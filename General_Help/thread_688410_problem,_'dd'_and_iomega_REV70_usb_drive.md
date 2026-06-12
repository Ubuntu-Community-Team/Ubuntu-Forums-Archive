---
title: "problem, 'dd' and iomega REV70 usb drive"
date: 2008-02-05
forum: General Help
---

### Post by tspby on 2008-02-05
Trying to use 'dd' to copy a linux root partition on disk to a file on a REV drive, but having problems.

'dd' seems to never detect the end of the disk partition.

On an HP xw9300 w/sata disk, I also have a USB Iomega REV70 drive.
Ubuntu 7.10 mounts the REV's ufs volume fine, and tar to that filesystem works fine.
However dd appears to never detect end of volume and continues to try to write to the REV drive until it runs out of space.

Has anyone seen 'dd' fail to work on a partition?
Why does it work on sda3 but not sda1?

???


;example1, dd of sda3 (swap partition.... works as expected)

tiny@tiny-desktop:/media/REV 70$ sudo  dd if=/dev/sda5 of=sda5.dd
6458067+0 records in
6458067+0 records out
3306530304 bytes (3.3 GB) copied, 113.462 seconds, 29.1 MB/s

;----------------------------------------------
;example 2, dd of sda1. dd writes until out of space. (Same results w/o bs argument.)


tiny@tiny-desktop:/media/REV 70$ sudo  dd if=/dev/sda1 of=sda1.dd bs=64k
 
dd: writing `sda1.dd': No space left on device
969560+0 records in
969559+0 records out
63541080064 bytes (64 GB) copied, 3144.64 seconds, 20.2 MB/s

;-------------------------------------------
; disk partition info from fdisk

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f2709

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9324    74894998+  83  Linux
/dev/sda2            9325        9726     3229065    5  Extended
/dev/sda5            9325        9726     3229033+  82  Linux swap / Solaris

---

