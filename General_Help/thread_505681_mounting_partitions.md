---
title: "mounting partitions"
date: 2007-07-20
forum: General Help
---

### Post by skaspud on 2007-07-20
i have my windows harddrive also hooked up to my computer but, right now i can only access the C:/ partition. i have like 5 more that i ABSOLUTELY need to access.
i was wondering how to do this.

got this from command:
sudo fdisk -l
++++++++++++++++++++++++++++++++++

Disk /dev/hdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2327    18691596   83  Linux
/dev/hdb2            2328        2434      859477+   5  Extended
/dev/hdb5            2328        2434      859446   82  Linux swap / Solaris

Disk /dev/hdc: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       35187   282639546   44  Unknown

Disk /dev/sda: 1024 MB, 1024966656 bytes
32 heads, 63 sectors/track, 993 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         992      999813+   6  FAT16
+++++++++++++++++++++++
i know it's the 300g one.
thanks.

---

### Post by bodhi.zazen on 2007-07-20
See this link for details: [http://ubuntuforums.org/showpost.php?p=3053391&postcount=2](http://ubuntuforums.org/showpost.php?p=3053391&postcount=2)

---

### Post by skaspud on 2007-07-20
sorry i'm really newb, i couldn't understand that...

---

### Post by bodhi.zazen on 2007-07-20
You need to :

1. make a mount point.

2. You then mount with the mount command, but ownership and read-write access depend on the file system, so you set such things one way with FAT/NTFS partitions and another for ext2/3 (and other linux file systems).

3. You then add an entry in /etc/fstab if you want to mount the partitions at boot.

Example :

using the /dev/sda1 :

```
sudo mkdir /media/sda1
sudo mount /dev/sda1 /media/sda1 -o umask=000
```

And fstab :

> /dev/sda1 /media/sda1 vfat auto,users,uid=1000,gid=100,umask=000 0 2

And on ....

---

