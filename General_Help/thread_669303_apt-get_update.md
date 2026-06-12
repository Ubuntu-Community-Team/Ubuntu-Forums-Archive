---
title: "apt-get update"
date: 2008-01-16
forum: General Help
---

### Post by expatCM on 2008-01-16
I have four clients running gutsy.  They are all connected to the same server.  My Internet connection is often challenged.

Is there any way to use the server so that each client shares any common files needed for keeping the client systems up to date (much in the same way that squid minimizes browser traffic)?

---

### Post by tehet on 2008-01-16
Maybe you could try one of the apt proxies:
```
apt-cache search apt-proxy
approx - caching proxy server for Debian archive files
apt-cacher - caching proxy system for Debian package and source files
apt-proxy - Debian archive proxy and partial mirror builder
```
I do not have experience with any of them so I can't make recommendations.

---

### Post by expatCM on 2008-01-17
Thank you for posting your suggestions.  I had looked round before but it seems I made the mistake of looking at the apt-get commands which apparently do not present the solution.

Looking at the linked pages, the apt-cacher / proxy / ....  seem to be in a bit of a mess at present in that they are all getting dated and there are many suggestions that bugs may surface.  There are no assurances that this will work with Ubuntu.

I just managed to find AptProxy and this appears to fit the need.  
[https://help.ubuntu.com/community/AptProxy](https://help.ubuntu.com/community/AptProxy)
Since the article was published a year ago I wonder if anyone has experience using this ....  especially with Gutsy, I would really like to know if this works...

---

