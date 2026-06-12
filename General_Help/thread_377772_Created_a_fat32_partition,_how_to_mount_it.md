---
title: "Created a fat32 partition, how to mount it?"
date: 2007-03-06
forum: General Help
---

### Post by bg1256 on 2007-03-06
I'm running Ubuntu Edgy, and I created a fat32 partition in hopes of sharing data between Linux and Windows.

The question is, how do I mount it?  And I'd like to be able to mount it on startup.

Thanks!

---

### Post by bg1256 on 2007-03-06
I did some searching and found I would most likely need to post the outcome of fdisk -l and cat /etc/fstab

So,

> benjamin@BG-Desktop:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100       17143    96743430   83  Linux
/dev/sda3           29892       30401     4096575   82  Linux swap / Solaris
/dev/sda4           17144       29874   102261757+   b  W95 FAT32


And

> benjamin@BG-Desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=ca5fdd28-ec44-4e79-aa4c-60fff5cc307f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=3C384026383FDD98 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=50b62eda-1161-48d4-8473-0ab455d3576f none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0



---

### Post by bg1256 on 2007-03-06
I think I have it solved after some extensive searching.

The only thing I'm not sure of yet is wheter or not Windows will be able to read/write to it.

---

### Post by theblackandblue on 2007-03-08
Same problem here. How did you solve!?

---

### Post by indytim on 2007-03-08
It should auto-mount when you fire up Windows.  Boot to Windows and check the My Computer thinger.  

IndyTim

---

### Post by Azakus on 2007-03-08
Windows will automount it (like it does every disk).
And the /etc/fstab entry should look like this exactly:
```
/dev/hdX /media/share vfat iocharset=utf8,umask=000 0 0
```
replace /dev/hdX with your FAT32 partition's exact /dev/ name in sudo fdisk -l.

---

