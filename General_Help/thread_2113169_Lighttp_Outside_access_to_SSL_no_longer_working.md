---
title: "Lighttp: Outside access to SSL no longer working"
date: 2013-02-06
forum: General Help
---

### Post by Apathia on 2013-02-06
Using lighttpd/1.4.28 on Ubuntu Linux 12.04.1

I'm not sure when this happened, but I attempted to access my domain but I just get "Page is not available" in all browsers (networked PC, android phone).

It works fine over the network (LAN IP), but both domain and WAN IP don't work. I've got it setup to redirect to SSL, so when I just use the domain, it redirects to https but still doesn't load anything.
I've not made any changes to lighttpd itself, but last night I did attempt to install zNC IRC bouncer but I ended up just removing it after I noticed lighttpd no longer worked, thinking maybe it had something to do with it.
The access log just shows this when I attempt to access it via domain name:
10.10.10.1 my.domain - [06/Feb/2013:15:38:28 - 0500] "GET / HTTP/1.1" 301 0 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.17 (KHTML, like Gecko) Chrome/24.0.1312.57 Safari/537.17" 
10.10.10.1 my.domain - [06/Feb/2013:15:39:07 - 0500] "GET /rutorrent HTTP/1.1" 301 0 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.17 (KHTML, like Gecko) Chrome/24.0.1312.57 Safari/537.17".

No errors in error.log

Here's my lighttpd conf: [http://paste.lighttpd.net/5d#p5mdxpnLUvNlwzunRDSHqZq9](http://paste.lighttpd.net/5d#p5mdxpnLUvNlwzunRDSHqZq9)

---

