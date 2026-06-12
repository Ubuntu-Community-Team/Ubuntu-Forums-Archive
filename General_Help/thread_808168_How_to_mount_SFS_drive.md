---
title: "How to mount SFS drive?"
date: 2008-05-26
forum: General Help
---

### Post by ziptnf on 2008-05-26
Hey guys,
I am dual booting Vista and Ubuntu (first time user... normal Fedora user, but decided to try Ubuntu).  I have two 500 gig storage drives that I merged together in Vista using the Dynamic Disk Drive Manager.  Vista lists them as NTFS drives, but Linux lists them as SFS.
```
ziptnf@omega:~$ sudo fdisk -l
Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe576a858

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6488    52111356    7  HPFS/NTFS
/dev/sda2            6489        6513      200812+  82  Linux swap / Solaris
/dev/sda3            6514        9026    20185672+  8e  Linux LVM
/dev/sda4            9027        9039      104422+  83  Linux

[B]Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1a6a534f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60802   488385528+  42  SFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1a6a534e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60802   488385528+  42  SFS[/B]

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c74ae42

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       30401   244196001    c  W95 FAT32 (LBA)

```

When I try to mount them as NTFS drives, it obviously fails.

```
ziptnf@omega:/mnt$ sudo mount -t ntfs /dev/sdb1 /mnt/disk1
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

```

Does anyone have any suggestions as to how I can mount these drives?

---

### Post by ziptnf on 2008-05-28
Bump, no suggestions?

---

### Post by prshah on 2008-05-29
> **ziptnf said:**
> ```
ziptnf@omega:/mnt$ sudo mount -t ntfs /dev/sdb1 /mnt/disk1
NTFS signature is missing.

```
Does anyone have any suggestions as to how I can mount these drives?

Take a look at [http://forum.linux-ntfs.org/viewtopic.php?t=555](http://forum.linux-ntfs.org/viewtopic.php?t=555) , especially the last post; any joy?

---

### Post by ziptnf on 2008-06-02
> **prshah said:**
> Take a look at [http://forum.linux-ntfs.org/viewtopic.php?t=555](http://forum.linux-ntfs.org/viewtopic.php?t=555) , especially the last post; any joy?

That would work if I only had one disk that was dynamic... mounting it like that gave me an NTFS error.  I'm beginning to think this might be impossible.

---

