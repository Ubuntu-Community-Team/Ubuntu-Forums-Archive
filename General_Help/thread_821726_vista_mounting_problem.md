---
title: "vista mounting problem"
date: 2008-06-07
forum: General Help
---

### Post by mastermatt63 on 2008-06-07
Hey guys, Every time I try and browse my vista drive its says:

Cannot mount volume

then it'll got to

opening VISTA

then it'll say

Unable to mount location
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

any ideas how i can access my stuff on my vista drive?

---

### Post by TeoBigusGeekus on 2008-06-07
Could you post us the output of 
```
sudo fdisk -l
```
(-L)
and tell us which one is your vista partition?

---

### Post by mastermatt63 on 2008-06-07
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2988b65f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         901     7232512   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         901       24127   186562776    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14677   117892971    c  W95 FAT32 (LBA)
/dev/sdb2           14678       38913   194675670    5  Extended
/dev/sdb5           14678       38159   188619133+  83  Linux
/dev/sdb6           38160       38913     6056473+  82  Linux swap / Solaris

The first one that is 200GB is the Vista one.

There is no vista partition since i am running ubuntu from an external drive, but i want to run ubuntu off my internal drive, that has vista on it. Right now I just want to browsw my data on my vista drive

---

