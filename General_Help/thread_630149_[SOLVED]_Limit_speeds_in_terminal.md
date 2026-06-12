---
title: "[SOLVED] Limit speeds in terminal?"
date: 2007-12-03
forum: General Help
---

### Post by TidusBlade on 2007-12-03
Well I know i will be doing alot of downloading using the terminal ver soon, so anybody knows how to limit the download speed in the terminal or is it possible?
Thanks! :)

---

### Post by rich.bradshaw on 2007-12-03
curl --limit-rate 10K [www.thesite.com/thefile](www.thesite.com/thefile)

would download thefile with a limit of 10KB per second

        curl --limit-rate 10240 [www.thesite.com/thefile](www.thesite.com/thefile)

would get it at 1MB per second

---

### Post by TidusBlade on 2007-12-03
thanks so much :D 
But what if the file is hosted on a server? 
I used to use this command to download
```
scp username@server:path_on_server/file path_to_download_to
```
It wasent really a site, a dedibox to be precise.

---

### Post by TidusBlade on 2007-12-03
Never mind, figured it out, just added a a limit ( -l ) to scp and it worked.

---

