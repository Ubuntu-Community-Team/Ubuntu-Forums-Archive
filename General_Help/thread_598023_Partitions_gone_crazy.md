---
title: "Partitions gone crazy"
date: 2007-10-30
forum: General Help
---

### Post by cold_fu5ion on 2007-10-30
Hi all,

I've got 2 identical segate 320gb sata drives, One with ubuntu approx 50 gig and an NTFS partition. The other with nothing no data, just a reiser partition.

Ok so here's the problem, I went to resize the blank drive to make it reiser and NTFS using gparted but it gave an error saying from memory "unknown flag". So I downloaded the gparted live cd, thinking I would partition it under there, would be safer.

Here's where the problem really starts, gparted messes up on boot, x fails to correctly load and forcing video drives doesnt work either. So I chuck my XP cd in (I know, there my problem right) because I think "well XP will be good for creating an NTFS partition" and just quit the install. When I get to the partition part of XP I realize I can't tell the two drives apart in XP.

So I take out the cd, reboot to go back to Ubuntu and .......... nothing. No grub, no missing OS message, the system posts then nothing happens.

Booting ubuntu live cd, my second drive (no data) shows up but the drive with my ubuntu  install and NTFS partition does not. fdisk -l shows this:

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e4abf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       16708   134206978+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
86 heads, 15 sectors/track, 484606 cylinders
Units = cylinders of 1290 * 512 = 660480 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      208090   134217727+   4  FAT16 <32M

Disk /dev/sdb1: 137.4 GB, 137438952960 bytes
86 heads, 15 sectors/track, 208089 cylinders
Units = cylinders of 1290 * 512 = 660480 bytes
Disk identifier: 0x00000001

     Device Boot      Start         End      Blocks   Id  System
/dev/sdb1p1   *           1      208090   134217727+   4  FAT16 <32M

```

Fat16? From what I can gather XP must put a MBR on the first drive before it even installs. But I have no idea why those partitions say fat16. I have no fat16 drives and didn't format or partition anything :confused:

Can anyone help me out?

---

### Post by cold_fu5ion on 2007-10-31
Ok I got Gparted loaded and checked out the drives,
It lists the fist one (file system drive) as having one parition of 120ish gb and the rest unused space (this should be an ntfs partiton!) and the other as all unused space.

I have no idea what when wrong or how to fix it.

---

### Post by cold_fu5ion on 2007-10-31
The mystery deepens.....

trying to use gparted to format the blank disk with a linux file system to do a complete copy of the first disk (just in case I screw it up an more) It gives a disk label error and cannot be formatted. This is the same error it gave when trying to format under ubuntu.

After booting up the live cd again and trying to figure out whats going on with fdisk -l it now displays:

```
sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e4abf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       16708   134206978+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System

```

whats going on here?

---

### Post by cold_fu5ion on 2007-10-31
For anyone interested here's what I did:

I downloaded systemrescue cd from [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

and used testdisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) on the cd to recover the partition table.

---

