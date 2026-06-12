---
title: "Help!!"
date: 2006-11-23
forum: General Help
---

### Post by akshaysrinivasan on 2006-11-23
Well internet was working fine ,until i meddled around with the system.Now though ,except the web browsers every other application fails to connect to the internet.Evolution cannot access the POP server.Wget cannot download things....

---

### Post by NotJustANewbie on 2006-11-23
Check your firewall settings. iptables is the default in linux or check your router too.
Google iptables to find out what to do seeing as your web browsing is still fine ;)

---

### Post by jallain on 2006-11-23
You may also want to verify that /etc/resolv.conf has the proper nameserver listed in it.

---

