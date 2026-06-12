---
title: "Help with Mounting USB &amp; Internal Hard Drives"
date: 2008-07-01
forum: General Help
---

### Post by gingermark on 2008-07-01
After a fresh install of Kubuntu Hardy I have found that my hardrives don't automount (which I appreciate is a problem mentioned elsewhere).

I can get my internal harddrives to mount by accessing them in the file browser - I have to enter my password, and then they are mounted as /media/disk, /media/disk-1 and so on, in the order that I access them.

My USB hardrive cannot be accessed this way - it is not visible unmounted in the filebrowser, despite the fact it used to automount in Dapper.

Oddly enough though my 6th Generation 160GB iPod Classic automounts fine.

My questions are:

1) How do I edit fstab (or whatever I need to edit) to automatically mount my internal hardrives at the same mount point each time I turn my computer on, without having to enter my password each time?

and

2) Can anybody help me access my USB portable hard drive?

Many thanks.

---

### Post by soccerboy on 2008-07-01
first lets see the contents of fdisk -l and fstab file

---

### Post by gingermark on 2008-07-01
My /etc/fstab file:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=70b45dfa-4cc0-4020-8514-91d17c6eb282 /               xfs     relatime        0       1
# /dev/sda1
UUID=27c6ecef-557c-48f4-9017-756ccce2c14b /boot           ext3    relatime        0       2
# /dev/sda4
UUID=0a2274ae-42bc-4d4c-8c89-c2072dfb10fd /home           xfs     relatime        0       2
# /dev/sda2
UUID=14ca7308-ac61-4fda-a2c0-85341d78a323 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

/tmp/app/1/image /tmp/app/1 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/2/image /tmp/app/2 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/3/image /tmp/app/3 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/4/image /tmp/app/4 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/5/image /tmp/app/5 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/6/image /tmp/app/6 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/7/image /tmp/app/7 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
```

When I type "fdisk -l" into a terminal I get no output.

---

### Post by soccerboy on 2008-07-01
sorry ```
sudo fdisk -l
```

---

### Post by gingermark on 2008-07-01
sudo fdisk -l gives:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00050005

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         108      867478+  83  Linux
/dev/sda2             109         315     1662727+  82  Linux swap / Solaris
/dev/sda3             316        5022    37808977+  83  Linux
/dev/sda4            5023        9729    37808977+  83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0641ae0b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00057dd4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        5393    43319241   83  Linux
/dev/sdc2            5599       30401   199230097+  83  Linux
/dev/sdc4            5394        5598     1646662+   5  Extended
/dev/sdc5            5394        5598     1646631   83  Linux

Partition table entries are not in disk order

Disk /dev/sdd: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x39c791b3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       48641   390708801    c  W95 FAT32 (LBA)

```

Edit: It looks like  /dev/sdd is my portable hardrive, but I cannot mount it through the filebrowser.

---

### Post by soccerboy on 2008-07-01
and finally ```
ls -l /dev/disk/by-uuid
```

---

### Post by gingermark on 2008-07-01
That command (without sudo) gives:

```
total 0
lrwxrwxrwx 1 root root 10 2008-07-01 17:56 0a2274ae-42bc-4d4c-8c89-c2072dfb10fd -> ../../sda4
lrwxrwxrwx 1 root root 10 2008-07-01 17:56 14ca7308-ac61-4fda-a2c0-85341d78a323 -> ../../sda2
lrwxrwxrwx 1 root root 10 2008-07-01 17:56 27c6ecef-557c-48f4-9017-756ccce2c14b -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-07-01 17:56 39430b00-afd7-41c6-a658-c1568f6ba385 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2008-07-01 17:56 3da09741-7b9a-4b54-ba52-b6809649d33e -> ../../sdc5
lrwxrwxrwx 1 root root 10 2008-07-01 17:56 70b45dfa-4cc0-4020-8514-91d17c6eb282 -> ../../sda3
lrwxrwxrwx 1 root root 10 2008-07-01 17:56 7ed17421-c0a3-48af-8b5a-d439ed17dfd1 -> ../../sdc2
lrwxrwxrwx 1 root root 10 2008-07-01 17:56 98c6d872-19c7-4dac-968f-8b3f00ed78b2 -> ../../sdc1
```

---

### Post by soccerboy on 2008-07-01
if you add these lines to fstab
```
# /dev/sdb1
UUID=39430b00-afd7-41c6-a658-c1568f6ba385 /media/sdb1           ext3     relatime        0       2
```

that should automatically mount sdb1 on reboot.  The UUID is from the ls -l /dev/disk/by-uuid output.  I am assuming your drives are ext3 filesystem.

---

### Post by gingermark on 2008-07-01
Thank you, I will give that a go shortly (I have to leave my computer now).

Do you by chance have any idea about auto-mounting my 400GB USB Hard Drive? Thanks again.

---

### Post by soccerboy on 2008-07-01
not positive on usb drives.  I think they mount under userspace so not sure.

---

