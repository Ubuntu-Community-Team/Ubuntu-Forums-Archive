---
title: "Ubuntu wants to perform a disk recovery on detached volumes every time it boots"
date: 2012-12-20
forum: General Help
---

### Post by LMDevlin on 2012-12-20
Hi all.

I used to have a 1TB USB hard drive constantly attached to my PC, predominantly to do backups to for my Windows installation. I have Ubuntu on a second hard drive, and when I first installed it it mounted all the drives present.

However, that USB drive is no longer connected, but every time I fire up Ubuntu and it goes to the boot screen, it tries to perform a disk recovery on the two missing volumes that were on the now detached USB drive (the main storage volume and the System Reserved volume). I have to press the S key to skip every time, which isn't so much  of a problem as it is an annoyance- and I would like to know the best way to get rid of that.

This links to another question I had about how to best permanently remove any partitions that I do not want Ubuntu to mount. My Ubuntu drive is a 160GB SATA drive (dev sdb if I recall correctly), and I also have a 1TB SATA drive which Windows and all of my data is stored on (dev sda). The 1TB SATA drive mounts two partitions- the main Windows/data partition and System Reserved. System Reserved is constantly mounted but I have no need for it, so I would like Ubuntu to stop mounting it.

I'm pretty sure when I first installed Ubuntu 12.04 I was able to choose which drives to mount through a GUI of some sort but I don't recall exactly how I did this and don't know how to undo it.

I tried to do this in fstab by removing what I thought were the lines which corresponded with the partitions I no longer want mounted, but it didn't seem to work. I don't think I quite understand the syntax of fstab.

If anyone could help me that would be great.

---

### Post by ajgreeny on 2012-12-20
Can you show us the output of ```
sudo fdisk -l && cat /etc/fstab
``` please

---

### Post by LMDevlin on 2012-12-20
As requested:

> Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x363ac879

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  1953521663   976657408    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc68581cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   312180735   156089344   83  Linux
/dev/sdb2       312182782   320172031     3994625    5  Extended
/dev/sdb5       312182784   320172031     3994624   82  Linux swap / Solaris
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sdb1 :
UUID=7844bb66-1560-4d9d-b59e-da3d3878e203	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda2 :
UUID=306AEE676AEE2974	/media/306AEE676AEE2974	ntfs-3g	defaults,nosuid,nodev,locale=en_GB.UTF-8	0	0
#Entry for /dev/sdc2 :
UUID=DEC432D9C432B39D	/media/Luke_s_External_HDD	ntfs	defaults,nls=utf8,umask=0222	0	0
/dev/sda1	/media/System_Reserved	ntfs	defaults,nls=utf8,umask=0222	00
/dev/sdc1	/media/System_Reserved_	ntfs	defaults,nls=utf8,umask=0222	00
#Entry for /dev/sdb5 :
UUID=c54cc4cb-52d5-44f7-ab68-92e5155cb9f3	none	swap	sw	0	0


---

### Post by ajgreeny on 2012-12-21
You need to firstly backup fstab with ```
sudo cp /etc/fstab /etc/fstabbackup
``` then open the file fstab as root with ```
gksudo gedit /etc/fstab
``` and edit so that the line third from the bottom looks like ```
# /dev/sdc1    /media/System_Reserved_    ntfs    defaults,nls=utf8,umask=0222    00
``` ie, add the # at the start of the line, or even delete the line completely.  After doing that run command ```
sudo mount -a
``` in terminal and if no errors appear all is well.

The reason for the problem is that the system is trying to automount sdc1 at boot, but it no longer exists on your computer.

---

### Post by LMDevlin on 2012-12-24
Thank you for your reply.

This seemed to remove one of the entries at boot, but it was still trying to boot the System Reserved partition on the missing USB drive. In the end I deleted the entire entry for the USB drive which seemed to fix it.

---

