---
title: "automount storage drive"
date: 2006-11-12
forum: General Help
---

### Post by jrsteffes on 2006-11-12
Need help to automount sdb1 on boot and to access it in /media/storage!
Please Help!

jason@jason-desktop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18666   149934613+  83  Linux
/dev/sda2           18667       19457     6353707+   5  Extended
/dev/sda5           18667       19457     6353676   82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401   83  Linux
jason@jason-desktop:~$

---

### Post by aysiu on 2006-11-12
This should help:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

