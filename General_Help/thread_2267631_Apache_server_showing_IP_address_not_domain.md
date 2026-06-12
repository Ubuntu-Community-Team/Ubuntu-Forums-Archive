---
title: "Apache server showing IP address not domain"
date: 2015-03-03
forum: General Help
---

### Post by fzaman2 on 2015-03-03
Hi,

I'm sure there is an easy fix, but haven't been able to get it to work yet.  I have apache server running on my ubuntu box...can get to the website from inside and outside my LAN, but when I go to it, the address bar shows the IP address instead of the domain.  I found some articles about wordpress doing this, but can't find one to show how I need to configure apache to make it work.  Any help is appreciated.

Thanks

---

### Post by efflandt on 2015-03-03
See: [http://httpd.apache.org/docs/current/mod/core.html#usecanonicalname](http://httpd.apache.org/docs/current/mod/core.html#usecanonicalname)

Try setting:
UseCanonicalName off

---

