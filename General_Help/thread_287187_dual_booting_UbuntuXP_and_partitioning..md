---
title: "dual booting Ubuntu/XP and partitioning."
date: 2006-10-28
forum: General Help
---

### Post by soccertwin03 on 2006-10-28
This is the first time I am attempting to dual boot.  I have only used XP in the past.  

I have to drives, C and D.  Drive C has Windows XP.  Drive D is a 120 GB seagate harddrive.  I have some files in Drive D which I don't want to lose.  

Here is my problem.

I downloaded the ubuntu 6.10 desktop iso and burned it onto a cd.  Then i booted ubuntu from the cd and attempted to create my partitions in drive D.  However, in GParted it tells me that drive D is unallocated and that the DiskLabelType is unrecognized.

This is the output of fdisk -l:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40060403712 bytes
240 heads, 63 sectors/track, 5174 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         611     4619128+  12  Compaq diagnostics
/dev/hda2   *         612        5173    34488720    7  HPFS/NTFS

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       15506   117225328+   7  HPFS/NTFS

```

the output of GParted is:

```
ubuntu@ubuntu:~$ sudo gparted
======================
libparted : 1.7.1
automounting disabled
======================
Can't have a partition outside the disk!
```

Any ideas on how I should proceed?  Thank you in advance.

---

