---
title: "Latest update hosed my internet connection"
date: 2006-09-20
forum: General Help
---

### Post by bigaltx on 2006-09-20
Yesterday I installed updates to BIND and some related libraries. Everything seemed to work fine, until I rebooted today. Now I can't connect to the internet. anyone have any ideas? Runnig Dapper with a 686 kernel.

---

### Post by wieman01 on 2006-09-21
It helps if you showed us your "/etc/network/interfaces" file using this command:
> gedit /etc/network/interfaces

---

### Post by bigaltx on 2006-09-21
Found the problem, IP adresses for DNS servers had been erased in /etc/resolv.conf. :D

---

