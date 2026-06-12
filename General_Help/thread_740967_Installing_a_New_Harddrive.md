---
title: "Installing a New Harddrive"
date: 2008-03-31
forum: General Help
---

### Post by damonjablons on 2008-03-31
Hey,

I just bought a new ATA 500GB Maxtor drive for my Ubuntu machine.  I've installed it using "cable select" and I can't figure out how to get Ubuntu to recognize it.

Here's the output of "**$ fdisk -l**":

```
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9538    76613953+  83  Linux
/dev/sda2            9539        9726     1510110    5  Extended
/dev/sda5            9539        9726     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf993d974

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    c  W95 FAT32 (LBA)
```

and here's the output of "**$ cat /etc/fstab**":
 
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=133d828a-1dc1-41b5-b9c1-a2f2784192f1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=10a6e7d3-972d-4add-868f-1bf304e45440 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

Thanks in advance for the help, I appreciate it.

---

### Post by wolfen69 on 2008-03-31
in terminal:
```
sudo mkdir /media/storage
```
substitute storage with whatever you want.
then add a line to fstab
```
gksudo gedit /etc/fstab
```
add this line
```
/dev/sdb1    /media/storage  vfat  rw,user,auto,exec  0     0
```
then put your cursor at the end of the line you just entered in fstab, and hit enter. (it needs another line with nothing on it.)
save file.

reboot.

---

### Post by damonjablons on 2008-03-31
Thank you for your help!  The drive mounted fine, and all is working.

In order to make the drive faster for read and write access, **how can I format it to the ext system?**

Thanks again!

---

### Post by wolfen69 on 2008-03-31
```
sudo umount /dev/sdb1
```
```
sudo gparted
```
from pull down menu at top right choose sdb1
then just highlight it and choose reformat.
then
```
sudo mount /dev/sdb1
```
then you will have to change fstab entry from vfat to ext3

---

### Post by damonjablons on 2008-03-31
SOLVED!

I found this tutorial, and it was quite helpful:

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

---

