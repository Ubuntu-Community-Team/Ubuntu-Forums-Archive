---
title: "Squid3 cannot get HTTPS traffic working"
date: 2013-04-15
forum: General Help
---

### Post by theHAAG on 2013-04-15
Hi All,

I have just installed a new server with squid and webmin following this guide. I have an upstream proxy that everything get directed to I have followed this guide: [http://ubuntuserverguide.com/2012/05/how-to-install-and-configure-proxy-server-with-squid3-on-ubuntu-server-12-04-lts.html](http://ubuntuserverguide.com/2012/05/how-to-install-and-configure-proxy-server-with-squid3-on-ubuntu-server-12-04-lts.html) and cannot get HTTPS to work for clients. I have tried adding exceptions into the firewall and editing ACL's. Any assistance with this would be great...

---

### Post by theHAAG on 2013-04-15
Solution: never_direct allow all

> **theHAAG said:**
> Hi All,

I have just installed a new server with squid and webmin following this guide. I have an upstream proxy that everything get directed to I have followed this guide: [http://ubuntuserverguide.com/2012/05/how-to-install-and-configure-proxy-server-with-squid3-on-ubuntu-server-12-04-lts.html](http://ubuntuserverguide.com/2012/05/how-to-install-and-configure-proxy-server-with-squid3-on-ubuntu-server-12-04-lts.html) and cannot get HTTPS to work for clients. I have tried adding exceptions into the firewall and editing ACL's. Any assistance with this would be great...

---

