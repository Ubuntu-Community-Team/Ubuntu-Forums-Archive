---
title: "Can't get hds to automount or mount at all (fstab included)"
date: 2008-05-30
forum: General Help
---

### Post by barlrol on 2008-05-30
first a little introduction:
Ubuntu 8.04 Hardy
64 bit

Problem: I'm new to linux and I can't get these nfts drives to automount on startup.  Here's what it shows when I enter sudo fdisk -l

Disk /dev/sda: 750.1 GB, 750156374016 bytes
16 heads, 63 sectors/track, 1453521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xff3278dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1     1453521   732574552+  42  SFS

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
16 heads, 63 sectors/track, 1453521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x064cfd6e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1     1453521   732574552+  42  SFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04533558

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       29649   238155561   83  Linux
/dev/sdc2           29650       30401     6040440    5  Extended
/dev/sdc5           29650       30401     6040408+  82  Linux swap / Solaris

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe068158e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/sde: 750.1 GB, 750156374016 bytes
16 heads, 63 sectors/track, 1453521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xff3278db

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1     1453517   732572536+   7  HPFS/NTFS

Disk /dev/sdf: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcdeecdee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       24792   199141708+   7  HPFS/NTFS

Disk /dev/sdg: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0515574d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       24792   199141708+   7  HPFS/NTFS


Heres my complete fstab file:


/dev/sda1 /mnt ntfs auto,0 0
/dev/sdb1 /mnt ntfs auto,0 0
/dev/sdc1 /mnt ntfs auto,0 0
/dev/sdd1 /mnt ntfs auto,0 0
/dev/sdf1 /mnt ntfs auto,0 0
/dev/sdg1 /mnt ntfs auto,0 0

When I go to places > Computer I see a drive called movies in addition to filesystem...Movies is one of my 750 GB sata drives but i dont know why that shoes and none of the others ones do.  It shows its mounted at /media for some reason.  I've been messing with this fstab for like 5 hours and nothing has worked.  So if I mount them to /mnt I should be able to go into the /mnt directory and see all my drives?  Also should these drives show up in Computer:///

Thanks in advance

---

### Post by fjgaude on 2008-05-30
I believe you need individual mountpoints for each drive, not just /mnt.

You mkdir as /mnt/sda /mnt/sdb etc...

Then in fstab use the mountpoints you have chosen for each drive.

---

