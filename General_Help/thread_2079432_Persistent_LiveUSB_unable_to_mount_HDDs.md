---
title: "Persistent LiveUSB unable to mount HDDs"
date: 2012-11-01
forum: General Help
---

### Post by Sapphire Dragon on 2012-11-01
Hi, I've searched around for many possible solutions to this, to no avail. So I'm posting now for some direct help if possible.
I've installed Ubuntu 12.04 onto an 8GB flash drive with persistence as a LiveUSB. Whenever I try to access any other hard drive (both my computer's and my external) it always gives me the error message "Error mounting: mount exited with exit code 21: mount: according to mtab, /dev/* is already mountetd on /media/*". Whenever I try to access it through /media/, it tells me I don't have the necessary permissions to.

I've gone through Disk Utility with the same result, tried gksudo nautilus (navigating to the drive in /media/ just shows nothing), and tried shutting down/rebooting several times. Nothing works. I had also installed another Ubuntu 12.04 on my computer in Win7 through Wubi, and rebooted to that installation to unmount  the drive (which mounted/unmounted with no problems), but eventually uninstalled that one thinking that it might still passively be the problem. No good. I'm stumped.

Some various command line results, if you wanted them:

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x99fd87a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2          409600   935329791   467460096    7  HPFS/NTFS/exFAT
/dev/sda3       935329792   976560127    20615168    7  HPFS/NTFS/exFAT
/dev/sda4       976560128   976771119      105496   82  Linux swap / Solaris

Disk /dev/sdb: 8075 MB, 8075120640 bytes
255 heads, 63 sectors/track, 981 cylinders, total 15771720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0f482339

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    15771719     7885828+   c  W95 FAT32 (LBA)

Disk /dev/sdc: 1000.2 GB, 1000170586112 bytes
255 heads, 63 sectors/track, 121597 cylinders, total 1953458176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00042ada

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  1953458175   976728064    7  HPFS/NTFS/exFAT
ubuntu@ubuntu:~$ cat /etc/mtab
cat: /etc/mtab: Input/output error

```Thanks again! Long live Ubuntu. ~

---

