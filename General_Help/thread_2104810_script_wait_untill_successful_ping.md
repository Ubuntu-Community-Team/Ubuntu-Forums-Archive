---
title: "script wait untill successful ping"
date: 2013-01-14
forum: General Help
---

### Post by marchelloUA on 2013-01-14
Hi all, 

my need is to run particular command but only after ping google.com is successful. How do I perform it?

---

### Post by rnerwein on 2013-01-14
> **marchelloUA said:**
> Hi all, 

my need is to run particular command but only after ping google.com is successful. How do I perform it?
hi
you can use: ping -c 1 -W 5 [www.google.de](www.google.de)
check the return code of ping: $? = 0 success, $? = 1 fault.
for further information see: man ping
ciao

---

