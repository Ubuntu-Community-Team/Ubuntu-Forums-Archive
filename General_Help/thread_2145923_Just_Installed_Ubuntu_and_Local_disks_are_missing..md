---
title: "Just Installed Ubuntu and Local disks are missing. Help"
date: 2013-05-16
forum: General Help
---

### Post by Guengineer on 2013-05-16
Hi there, I installed ubuntu replacing my windows 8. After successfully installing it. I don't know where my drives are now? In devices I can only see computer? 

Any idea. What's this?  Please help. I had stuff in other disks. 

Thankyou.

---

### Post by arpanaut on 2013-05-16
Please explain more clearly how you went about installing.
How many hard drives are in your computer?
Windows refers to Drives when they are actually just partitions.

open a terminal in ubuntu (ctrl+alt+t) and copy and paste this into it, 
```
sudo fdisk -lu
``` hit enter,
then enter your user password and post back the results of that command here.

---

### Post by Guengineer on 2013-05-16
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   312449023   155973633    5  Extended
/dev/sda5          501760   312449023   155973632   8e  Linux LVM

Disk /dev/mapper/ubuntu--vg-root: 157.6 GB, 157580001280 bytes
255 heads, 63 sectors/track, 19158 cylinders, total 307773440 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-swap_1: 2113 MB, 2113929216 bytes
255 heads, 63 sectors/track, 257 cylinders, total 4128768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table

This is the result i got. I Installed it through bootable usb and replaced windows with ubuntu. I had 4 drive C, D, E, & F. C is where the windows  were installed.

---

### Post by ammontgo on 2013-05-16
You have to mount your drives if you have more than just the installation disk.

---

### Post by arpanaut on 2013-05-17
Yup, you overwrote the entire disk, you certainly succeeded in replacing windows.
Windows is gone and with it all the partitions that were previously on the disk i.e. C,D,E & F
Did you backup your data before you began?
You may be able to recover your lost data with a program called testdisk.
If you need to recover that data STOP using your hard drive and only use the live session of Ubuntu
Otherwise you will have more difficulty recovering your data.

I will get back to you soon with some information on testdisk and data recovery.

Here's some info to get you started:
[http://ubuntuforums.org/showthread.php?t=2102472&p=12443356&viewfull=1#post12443356](http://ubuntuforums.org/showthread.php?t=2102472&p=12443356&viewfull=1#post12443356)

---

