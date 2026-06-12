---
title: "Squid problem (restart everytime)"
date: 2005-05-10
forum: General Help
---

### Post by zer on 2005-05-10
Hi,

When i boot my PC and want to use Squid as accelerator for my dialup Connection, i have to do
```
/etc/init.d/squid restart
```
before any site can be reached with Firefox.
the restart progress of squid takes a _loong_ time, but only the stopping of the service. If i do a
```
killall squid
```
before, i can restart the service fast.
IIRC, i only changed one line in /etc/squid/squid.conf when i set it up.
So, **any** ideas why i have to restart squid everytime, before i can surf?

PS: Sorry for the bad english

---

