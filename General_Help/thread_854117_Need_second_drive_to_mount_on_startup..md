---
title: "Need second drive to mount on startup."
date: 2008-07-09
forum: General Help
---

### Post by Jimbo13 on 2008-07-09
I am trying to make my second drive mount at startup because I use my ubuntu PC as a server and well all the good stuff is on my second drive.

From the poorly translated italian post i I found on this I think this is the info needed to figure this one out.

Disk /dev/sda: 60.0 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdad4f39a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         421     3381651    7  HPFS/NTFS
/dev/sda2             422        7301    55263600    5  Extended
/dev/sda5             422        7116    53777556   83  Linux
/dev/sda6            7117        7301     1485981   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcf1fcf1f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30400   244187968+   7  HPFS/NTFS




My 250GB is my second drive, I tried ntfs-config and that didn't seem to detect my second drive but I have no trouble mounting it manually from
/places And I'm actually just using regular ubuntu

Thanks.

---

### Post by cyclobs on 2008-07-09
[http://ubuntuforums.org/showthread.php?t=852842&highlight=automount](http://ubuntuforums.org/showthread.php?t=852842&highlight=automount)

thats a guide a mate gave to me that works well, it should apply to kubuntu as well...

---

