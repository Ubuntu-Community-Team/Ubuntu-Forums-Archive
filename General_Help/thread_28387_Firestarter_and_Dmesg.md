---
title: "Firestarter and Dmesg"
date: 2005-04-20
forum: General Help
---

### Post by drspin on 2005-04-20
OK -- I have done a ton of googling on this topic and I'm not able to find a solution. Firestarter logs stuff using syslog... is there a way to keep it from polluting my dmesg but still be able to access the log in say /var/log/firewall ??

Thanks in advance - Cole

---

### Post by spacedoubtman on 2007-12-29
Hi,

I know this was posted a while ago but it annoyed me that the first result when I searched for firestarter and dmesg on google was someone telling me that they couldn't find how to turn it off.

So heres how:
In /etc/firestarter/configuration change the line
LOG_LEVEL=info
to be
 LOG_LEVEL=none

Adam

---

### Post by spacedoubtman on 2008-02-01
This may not be the best solution - I'm now getting errors like this when I start firestarter:

iptables v1.3.6: log-level `none' unknown
Try `iptables -h' or 'iptables --help' for more information.

From looking at /etc/firestarter/firewall it seems like the firewall will still start up but there must be a better solution.

---

