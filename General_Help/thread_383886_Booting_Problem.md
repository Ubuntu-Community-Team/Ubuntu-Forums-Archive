---
title: "Booting Problem"
date: 2007-03-13
forum: General Help
---

### Post by nick_533 on 2007-03-13
Disk /dev/hda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              63     1044224      522081   82  Linux swap / Solaris
/dev/hda2        20482875    58589054    19053090    7  HPFS/NTFS
/dev/hda3         1044225    20482874     9719325   83  Linux

Partition table entries are not in disk order


This is my partition info  when i start ubuntu with live cd to select  boot from hard disk option then only it boots

if no cd is there it doesnt boot from harddisk do i need to make any changes?

---

### Post by rsambuca on 2007-03-13
What exactly happens when you try to boot without the CD?  Ie, what error messages are you getting, if any.

---

### Post by Duggeek on 2007-03-13
> **nick_533 said:**
> Partition table entries are not in disk order

Is that the message you get from Grub? Strange that the partitioning utility picked for ubuntu doesn't always play nice with the preferred bootloader.

It is *always* best to have a logical partition-order, the partition table has four entries, and they should always go from first-to-last. Unfortunately, gParted is not the best at doing that when there are pre-existing partitions. (it can't dance around Windows that easily... I presume that's what the HPFS/NTFS partition is for)

If it's a spankin-new dual-boot (meaning you *just* installed Windows, too) then you really should do it over from scratch. (sorry!) :( 

You can make your planned Linux partitions as FAT to make Windows happy for the moment, then convert them with gParted later. Don't worry about exact sizes, let the partitioning software figure the exact size. (I always just use rough thousands-of-megs)

**Don't** try gParted first... there's something about the FAT format that Windows Setup doesn't like. Even if you re-write the MBR and all that, Setup will just barf all over it and ask to set-up the whole drive anyway. :mad: 

TIPS:
[LIST=1]
[*]Let Windows have the first-occuring partition; it's happier that way. (read: Windows is whiny) :rolleyes:
[*]Make the Linux partitions as FAT32 with Windows Setup, you can just re-format them later in gParted.
[*]The Linux-swap doesn't have to be a Primary Partition (one of the four table entries) but can also be in an Extended Partition and should always be the last partition on the drive.
[/LIST]
Fire up the ubuntu CD after Windows is done and everything else should be a snap!\\:D/

---

### Post by nick_533 on 2007-03-13
when computr starts it shiws cant boot frm HD

---

