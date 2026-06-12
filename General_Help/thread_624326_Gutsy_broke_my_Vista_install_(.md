---
title: "Gutsy broke my Vista install :("
date: 2007-11-26
forum: General Help
---

### Post by Mono1ith on 2007-11-26
Hi all, I am n00b so be gentle . . .

So I installed Gutsy today on a HD I had lying around, hoping to be able to dual-boot between Gutsy and Vista (Vista is on a SATA drive, Gutsy's on IDE as master).  Ubuntu looks great, but the problem is I can no longer boot into Vista.  From the GRUB loader, I get the error message: Error 13: Invalid or unsupported executable format.

So I popped in my Vista disc and attempted to repair, but the install disc can't find the installation on my hard drive.  I did some googling, and one thread I found made it sound like something called a Super Grub Disk might fix my problem.  I downloaded and booted from the ISO, and ran "fix boot of windows", but it didn't fix my problem.

Ideas?

---

### Post by fedex1993 on 2007-11-26
know you probley didnt do a duaul boot so gutsy did not break your vista you broke your vista

---

### Post by Sef on 2007-11-27
Applications > Accessories > Terminal

```
sudo fdisk -l
```

do that command above.   It will give you your partitions.   Copy and paste the results in here.

---

### Post by Mono1ith on 2007-11-27
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2a137c2c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           1         992+  42  SFS
Partition 1 does not end on cylinder boundary.
/dev/sda2               1       60802   488384512   42  SFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           60802       60802          24   42  SFS
Partition 3 does not end on cylinder boundary.

Disk /dev/hda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e1e13

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       37973   305018091   83  Linux
/dev/hda2           37974       38913     7550550    5  Extended
/dev/hda5           37974       38913     7550518+  82  Linux swap / Solaris
cliff@cliffbuntu:~$

---

