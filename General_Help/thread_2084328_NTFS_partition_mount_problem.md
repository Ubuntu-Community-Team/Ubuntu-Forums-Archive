---
title: "NTFS partition mount problem"
date: 2012-11-15
forum: General Help
---

### Post by miro71 on 2012-11-15
Hi, I want to mount one of my windows ntfs partitions on ubuntu 12.04, but I can't.

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1e1a1e19

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   102398309    51199123+   7  HPFS/NTFS/exFAT
/dev/sda2       102398310   976751999   437176845    f  W95 Ext'd (LBA)
/dev/sda5       102398373   976751999   437176813+   7  HPFS/NTFS/exFAT
Note: sector size is 2048 (not 512)
``````
miroelo82@ubuntu:~$ sudo umount /media/sda5
umount: /media/sda5: not mounted
miroelo82@ubuntu:~$ sudo mount /media/sda5
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
``````
miroelo82@ubuntu:~$ df -th
df: no file systems processed

``````
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

/dev/sda5    /media/sda5    ntfs-3g    defaults,nosuid,nodev,locale=en_GB.UTF-8    0    0
#Entry for /dev/sda1 :
UUID=9EDC7AFDDC7ACF51    /media/sda1    ntfs-3g    defaults,locale=en_GB.UTF-8    0    0
UUID=D88C93338C930AE0    /media/sda5    ntfs-3g    defaults,locale=en_GB.UTF-8    0    0
/host/ubuntu/disks/swap.disk    none    swap    sw    0    0

```

---

### Post by NikTh on 2012-11-15
Hi , 

is that a Wubi installation ? (Ubuntu installed from within Windows)

Thanks

---

### Post by miro71 on 2012-11-15
yes

---

### Post by NikTh on 2012-11-15
Hi , 
read this please => [https://wiki.ubuntu.com/WubiGuide#How_do_I_access_the_Windows_drives.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_access_the_Windows_drives.3F)

Windows partition is already mounted . Wubi uses a virtual disk and install Ubuntu , so Windows has to be mounted for Ubuntu to load. 

You can find you Windows partition under /hosts .

Thanks

---

