# Find_Sensitive_Data

1. chaos.projectdiscovery.io
2. Download Public Bounty File
3. Unzip filename
4. Find alive subdomain: httpx -l file_name -o alive.txt
5. Make two alive files : https and without https,http
6. Without https,http: cat alive.txt | sed 's|https\?://||' > clean_alive_withouthttp.txt
7. Check Waybackurls: cat clean_alive_withouthttp.txt | waybackurls > urls.txt
8. Filter url:

   cat urls.txt | grep ".js" | tee js.txt
   httpx -l js.txt -fc 404 -o alive.js.txt
   sort -u alivejs.txt | uniq > js.txt { For sure }

Active :
1. Using katana:  katana -list alive_domains_httpx_without.txt -jc -silent | grep "\.js$" | tee katanajsofiles.txt
