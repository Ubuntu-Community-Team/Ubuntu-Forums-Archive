---
title: "dns issue/server newbie"
date: 2007-10-24
forum: General Help
---

### Post by kinalas on 2007-10-24
greetings!

just installed ubuntu 7.10 server. the only added software is lamp.

on my eth0 - i entered my public ip/subnest mask, gateway, nameserver.

i can ping all. but if i ping yahoo.com it says unknown host. the result applies also if i ping using fqdn

do i need to install dns?

help

---

### Post by mrog on 2007-10-25
Unless you're actually trying to build an DNS server there should be no need to install DNS services.

Does /etc/resolv.conf contain an entry for your ISPs DNS server. i.e.
nameserver xxx.xxx.xxx.xxx

---

