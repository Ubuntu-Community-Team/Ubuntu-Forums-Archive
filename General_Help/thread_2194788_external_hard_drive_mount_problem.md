---
title: "external hard drive mount problem"
date: 2013-12-20
forum: General Help
---

### Post by vaskark2 on 2013-12-20
I have a 1 TB external hard drive on my system and several symlinks in my home folder pointing to it. However, I've noticed that when I log in my symlinks are sometimes broken (and sometimes not). I've discovered this happens depending on the desktop environment I'm currently using:

In unity, the drive gets mounted at /media/user/Elements
In E17, the drive gets mounted at /media/Elements

Can anyone offer some assistance? Here is my output from *sudo fdisk -l* :

```
$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x87b802bb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   115330634    57665286    7  HPFS/NTFS/exFAT
/dev/sda2       115331070   156301311    20485121    5  Extended
/dev/sda5       115331072   154208255    19438592   83  Linux
/dev/sda6       154210304   156301311     1045504   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000202043392 bytes
255 heads, 63 sectors/track, 121600 cylinders, total 1953519616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00056154

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1953520064   976759008+   7  HPFS/NTFS/exFAT
```

Thanks :)

---

### Post by Erik1984 on 2013-12-20
Is that external drive always connected to your computer? In that case you could add a line in /etc/fstab for that particular partition to be always mounted on the same location. Each time you start Ubuntu (regardless of the desktop session) the drive will then be mounted on the same point. [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by vaskark2 on 2013-12-20
Thanks, Euroman! I made a permanent entry in fstab and it works great now.

---

