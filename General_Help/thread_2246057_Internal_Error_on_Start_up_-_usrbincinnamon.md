---
title: "Internal Error on Start up - usr/bin/cinnamon"
date: 2014-09-28
forum: General Help
---

### Post by The_Weaver on 2014-09-28
Hi,

I'm using LTS 14.04 with cinnamon. On start up I get a internal error warning, referencing usr/bin/cinnamon. It stops prior to reaching the destop. If I logout, then log back in everything is fine. Any ideas?

---

### Post by ibjsb4 on 2014-09-28
This sounds like Apport.

Try resetting it by removing the file in /var/log/apport.log.

[https://wiki.ubuntu.com/Apport#Why_is_it_disabled.3F](https://wiki.ubuntu.com/Apport#Why_is_it_disabled.3F)

---

### Post by The_Weaver on 2014-09-28
Solved it by disabling Apport by modifying the **&#8220;/etc/default/apport&#8221;** file. Thanks.

---

