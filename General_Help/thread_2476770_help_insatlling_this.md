---
title: "help insatlling this"
date: 2022-07-06
forum: General Help
---

### Post by natbrowne on 2022-07-06
Hi, 
Need a VPN for my work, this one worked great in 20 LTS, [https://hadler.me/linux/openfortigui/](https://hadler.me/linux/openfortigui/)

But when I try to install it, it tells me in the package manager, " Package : openfortigui, Status : Error cannot satisfy dependencies "

Can anyone help me install it?

---

### Post by #&amp;thj^% on 2022-07-06
It's minus the GUI, but otherwise it is in the repos:
```
apt search openfortivpn
Sorting... Done
Full Text Search... Done
openfortivpn/jammy,now 1.17.1-1build1 amd64 [installed]
  Fortinet client for PPP+SSL VPN tunnel services

```
I'm not sure if they will include the GUI in upcoming updates.
Jumping to newer LTS releases can be a challenge for our favorite/needed apps. ;)

---

