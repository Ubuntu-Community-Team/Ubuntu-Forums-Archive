---
title: "Problem with accessing partitions with custom kernel"
date: 2006-07-20
forum: General Help
---

### Post by abc1987 on 2006-07-20
Hi there,

I have built a new kernel for my 32-bit Athlon 64 Dapper box using the Linux 2.6.17.6 vanilla kernel with the realtime-lsm patch (I intend to use the machine for music composition with Rosegarden4 et al). Unfortunately, with the new kernel running I am finding that I cannot read anything on several of the mounted partitions on my two SATA drives, namely /dev/sdb1, a 200MB EXT3 file system and /dev/sdb3 a 182GB EXT3 file system. Strangely I have no problem accessing my NTFS Windows partiton /dev/sda1. I had a similar issue when I built a 2.6.17-ck1 kernel, that time I couldn't access either the EXT3 partitions or my NTFS partition. The partitions that do work are /dev/sda2 (/boot EXT2), and /dev/sda4 (/ XFS). There don't appear to be any problems accessing the swap partition. Also the partitions I can't see anything on come up as busy, but when I do ls I don't see anything - there definitely are files there from an old Dapper installation and I can see them when I boot with the stock kernel.

The kernel was configured by exporting the settings from the 2.6.15-26-k7 Ubuntu kernel using make oldconfig and I did not knowingly make any changes to the filesystem configuration, accepting all the defaults for any new options. The only changes I made were to change the CPU optimisation from AMD Athlon to AMD K8, disable SMP support and set the timer frequency to 1000Hz.

Here is my /etc/fstab:

#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda4       /               xfs     defaults        0       1
/dev/sda2       /boot           ext2    defaults        0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/sdb1       /media/sdb1     ext3    defaults        0       1
/dev/sdb3       /media/sdb3     ext3    defaults        0       1
/dev/sda3       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

Thanks in advance for your help,

Alastair

---

