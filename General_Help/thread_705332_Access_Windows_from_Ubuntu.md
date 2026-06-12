---
title: "Access Windows from Ubuntu"
date: 2008-02-23
forum: General Help
---

### Post by msferoz85 on 2008-02-23
Ok, I am using dual boot: Ubuntu and Windows. I don't like windows, but my network configurations aren't made properly on Ubuntu as yet, so I HAVE to use Windows for the time being side by side. Some of my documents on Windows are tagged read-only, which prevents me from modifying them in Ubuntu. Is there a way I can change these settings directly from Ubuntu, or do i HAVE to log in to Windows?? (oh no, please!!)

The folder propeties say the the owner of the folder is "root", and i cannot change permissions. Can i change them by logging in as root?? If yes, how do i do so?? 

(Sorry for the noob question)

---

### Post by taurus on 2008-02-23
I bet it's ntfs filesystem which means you need to use ntfs-3g driver if you want to write to it.  Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by msferoz85 on 2008-02-23
fdisk -l

```
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3df63df5

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1275    10241406    c  W95 FAT32 (LBA)
/dev/hda2            1276        4864    28828642+   f  W95 Ext'd (LBA)
/dev/hda5            2551        3825    10241406    b  W95 FAT32
/dev/hda6            3826        4864     8345736    b  W95 FAT32
/dev/hda7            1276        2307     8289477   83  Linux
/dev/hda8            2308        2550     1951866   82  Linux swap / Solaris

Partition table entries are not in disk order

```

fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda7
UUID=565bf8a1-1342-4378-bf41-8bfb17bf8b5d /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=DC12-4453  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=9C83-08E0  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=D489-201F  /media/hda6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda8
UUID=c4ec8ebd-9cf0-47bb-8c91-1ee59e38cd20 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

df -h

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda7             7.8G  2.4G  5.1G  33% /
varrun                474M   84K  474M   1% /var/run
varlock               474M     0  474M   0% /var/lock
udev                  474M   80K  474M   1% /dev
devshm                474M     0  474M   0% /dev/shm
lrm                   474M   34M  440M   8% /lib/modules/2.6.22-14-generic/volatile
/dev/hda1             9.8G  7.9G  2.0G  81% /media/hda1
/dev/hda5             9.8G  6.7G  3.2G  68% /media/hda5
/dev/hda6             8.0G  5.3G  2.8G  66% /media/hda6

```

---

