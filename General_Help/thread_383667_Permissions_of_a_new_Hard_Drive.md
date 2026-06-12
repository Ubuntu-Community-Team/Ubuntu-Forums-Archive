---
title: "Permissions of a new Hard Drive"
date: 2007-03-13
forum: General Help
---

### Post by L2wis on 2007-03-13
Hey all, i've just mounted my new HDD and also thought that i'd set the permissions of it to '777 All for everyone' But really what it's done is 750 or some crap i can write or execute on it. I've  sudo nautilus on the folder and tried to use the GUI but that just gives errors even thou i'm root?

Anyone know?

---

### Post by taurus on 2007-03-13
What is the filesystem on that new harddrive?

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by L2wis on 2007-03-15
```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        4469    35897211   83  Linux
/dev/hda2   *        4470        7146    21503002+   7  HPFS/NTFS
/dev/hda3            9352        9729     3036285    5  Extended
/dev/hda4            7147        9351    17711662+   b  W95 FAT32
/dev/hda5            9352        9729     3036253+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        9729    78148161    b  W95 FAT32

```
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd1 /media/music vfat defaults 0 0

```

The hard drive i'm trying to set permissions for is  hdd1 and it's fat32.

Thanks for the reply

---

### Post by taurus on 2007-03-15
Edit your /etc/fstab

```
gksudo gedit /etc/fstab
```
and make the last line to look like this instead.

```
/dev/hdd1   /media/music   vfat   iocharset=utf8,umask=000   0   0
```
Reboot and you should be able to write to it now.

---

### Post by L2wis on 2007-03-16
I've just changed it over, i'm gonna give it a reboot hopefully it'll work! Many thanks for your help!

---

