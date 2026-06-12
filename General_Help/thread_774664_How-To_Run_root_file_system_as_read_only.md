---
title: "How-To: Run root file system as read only"
date: 2008-04-29
forum: General Help
---

### Post by zmarano on 2008-04-29
I am looking for the best way to go about mounting the root file system read only and still keep everything working. If anyone has gone about this I would appreciate the feedback you have. Here's what I have found out about this so far.

Lets consider you have a second partition that you are mounting read/write at /volatile and you want to use this partition for anything that needs to be read/write by the system.
1) Relink /etc/mtab to /proc/mounts
2) Relink /var/log /volatile/log

Here's what I haven't quite figured out yet:
1) Relink or move /etc/resolv.conf to /volatile/resolv.conf so everything including PPP and DNS works. I have tried linking it elsewhere but it is overwritten at boot. Any ideas?
2) The best way to remount the root file system ro, doing this with fstab seems to break a lot of things including Xorg. Perhaps remounting it later on- after boot is better (maybe through rc.local).
3) Any other vital directories or files that need to always be read/write.

---

