---
title: "Undo swapon NTFS partition"
date: 2013-12-20
forum: General Help
---

### Post by kwilde on 2013-12-20
I am dual booting Windows 7 and Ubuntu and I accidentally did swapon on my windows NTFS partition. What do I do to resolve this? Swapoff -a doesn't seem to work.



fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xec78060d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     1023999      510976    7  HPFS/NTFS/exFAT
/dev/sda2         1024000   512987135   255981568    7  HPFS/NTFS/exFAT
/dev/sda3       512989182   976771071   231890945    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda5       512989184   968642559   227826688   83  Linux
/dev/sda6       968644608   976771071     4063232   82  Linux swap / Solaris

---

### Post by Habitual on 2013-12-20
reboot?
clarify "doesn't seem to work" please.

---

### Post by kwilde on 2013-12-21
I mean that gparted still indicates that dev/sda2 is of the fily system type 'linux swap'. It was originally NTFS and where WIndows lived, which now refuses to boot.

---

