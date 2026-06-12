---
title: "setting default DNS address"
date: 2007-05-16
forum: General Help
---

### Post by soonwah leong on 2007-05-16
Hi,
how do I set the default DNS value after I have set the IP under DHCP mode.
Appreciate if somebodt can give me some direction where to look.

---

### Post by ikonia on 2007-05-16
can you define what you mean by default dns address ?

if you mean what dns domain name does this machine belong to you can set that in the same gnome gui as the ip address, is in the next tab along, or in the /etc/resolv.conf in the domain parameter

eg:

domain mydns.com
nameserver 127.0.0.1
nameserver 127.0.1.1

---

