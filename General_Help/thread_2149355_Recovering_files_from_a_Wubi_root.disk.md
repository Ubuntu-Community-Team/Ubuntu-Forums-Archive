---
title: "Recovering files from a Wubi root.disk"
date: 2013-05-28
forum: General Help
---

### Post by AndyCinDallas on 2013-05-28
I had never used WUBI before to install Ubuntu and a few years ago I decided to try it out on a new Win 7 laptop.

I didn't really like it much as the partition was limited to 32 Gb or so but I was admittedly too lazy to backup my files and start again. Then my laptop's motherboard died last week and I was forced to pull the drive and connect it via a USB connector to my new laptop (which has Ubuntu 12.04 LTS installed *(without WUBI this time!)*

I hadn't realized that WUBI creates a single big root.disk file which is the Linux install within Windows, so I had to do some research on how to get all my files from within that disk image-file. Here's the results of my research and the technique that worked for me:


_**Step 1.**_ Once you've attached your old drive to the new PC, run the [COLOR="#FF0000"]sudo fdisk -l[/COLOR] command to find all the hard-disks:

> 
[I]andy@test-laptop:~$ [COLOR="#FF0000"]sudo fdisk -l[/COLOR]
[sudo] password for andy: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

Disk /dev/sda: 500.1 GB, 500107862016 bytes [COLOR="#0000FF"](sda is the new laptop’s hard-disk)[/COLOR]
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x01a8a7c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 320.1 GB, 320072933376 bytes [COLOR="#0000FF"](sbd is the external disk)[/COLOR]
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6029c818

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   596465663   298231808    7  HPFS/NTFS/exFAT
/dev/sdb2       596465664   625139711    14337024    7  HPFS/NTFS/exFAT
andy@test-laptop:~$ [/I]


_**Step 2.**_ Now to make directories to be used as mount-points and then mount the disks to those mount-points – the root.disk file I needed to access was in the sdb1 partition:

> 
andy@test-laptop:~$ [COLOR="#FF0000"]sudo mkdir /win[/COLOR]
andy@test-laptop:~$ [COLOR="#FF0000"]sudo mount /dev/sdb1 /win[/COLOR]
andy@test-laptop:~$ [COLOR="#FF0000"]sudo mkdir /vdisk[/COLOR]
andy@test-laptop:~$ [COLOR="#FF0000"]sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk[/COLOR]


The last command mounted the root.disk file and automatically opened up the nautilus explorer so that I could browse and copy files across from the big root.disk file (now seen as a drive) to my local drive.

I hope that this method helps somebody else some day.

---

