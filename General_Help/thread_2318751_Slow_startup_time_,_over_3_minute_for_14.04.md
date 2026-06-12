---
title: "Slow startup time , over 3 minute for 14.04"
date: 2016-03-29
forum: General Help
---

### Post by ubuserone on 2016-03-29
Startup time is over 3 minute for 14.04 and suspect of low disc space left.Do I need to defrag my ubuntu for my hard disk to get faster startup time ? I allocated 40GB and use up almost 80%.Using normal 3.5 hard disk and it stated it run on 7200rpm.

---

### Post by oldfred on 2016-03-29
There is no defrag with Linux.

If at 80% drive is getting full and you either need to houseclean or buy larger drive.

To check for boot issues get logs.
If systemd:
 systemd-analyze blame 

 Older systems with Upstart
gksudo gedit /var/log/dmesg
sudo grep -E -i "error|warning" /var/log/dmesg  

The dmesg is long, and most is not important. Look only at entry(s) before & after a long gap in timestamp.

---

