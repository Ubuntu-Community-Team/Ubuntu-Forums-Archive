---
title: "Mount 2nd Hard disk automatically?"
date: 2008-03-23
forum: General Help
---

### Post by Hayesio on 2008-03-23
Hi guys.  I have a second hard drive in my system and i was wondering if somebody could tell me how to have it automatically mount when the system starts up.  At the moment i have to select it in the nautilus menu and enter the root password.

Thanx

---

### Post by Scorpuk on 2008-03-23
You will need to add it to the fstab file.

To do this you need to know which drive it is (sda1, sda2, sdb1, sb2, etc) and the format of the drive (ext3, fat32, ntfs, etc)


Can you post the following?

```
ls -l /dev/sd*
```

```
ls -l /dev/hd*
```

Those are lower case L's ;-)


and the contents of /etc/fstab.

---

### Post by Hayesio on 2008-03-23
This is the output:
```
lexi@lexi-desktop:~$ ls -l /dev/sd*
brw-rw---- 1 root plugdev 8, 0 2008-03-24 10:53 /dev/sda
lexi@lexi-desktop:~$ ls -l /dev/hd*
brw-rw---- 1 root disk   3,  0 2008-03-24 21:53 /dev/hda
brw-rw---- 1 root disk   3,  1 2008-03-24 21:53 /dev/hda1
brw-rw---- 1 root disk   3,  2 2008-03-24 21:53 /dev/hda2
brw-rw---- 1 root disk   3,  5 2008-03-24 21:53 /dev/hda5
brw-rw---- 1 root disk   3, 64 2008-03-24 21:52 /dev/hdb
brw-rw---- 1 root disk   3, 65 2008-03-24 10:53 /dev/hdb1
brw-rw---- 1 root disk   3, 66 2008-03-24 21:53 /dev/hdb2
brw-rw---- 1 root disk   3, 69 2008-03-24 21:53 /dev/hdb5
brw-rw---- 1 root cdrom 22,  0 2008-03-24 21:52 /dev/hdc
brw-rw---- 1 root cdrom 22, 64 2008-03-24 21:52 /dev/hdd
lexi@lexi-desktop:~$ 

```

The disk i want to mount is a windows (NTFS) partition on a separate hdd to the ubuntu installation.  It is an IDE hdd, not sata.  Its size is 100GB. 



fstab file:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=b23ac845-c6eb-4004-8e19-3c3955890038 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=f0961e40-2174-471b-a979-a0473d11b6b2 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
``` 

Thanx

---

