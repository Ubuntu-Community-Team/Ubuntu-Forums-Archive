---
title: "wierd mount request"
date: 2008-05-18
forum: General Help
---

### Post by itix on 2008-05-18
I was uuhhh... wondering if you can tell Ubuntu in some way NOT to mount a partition. I have installed openSUSE on my external drive (quite pleased with it to be honest), and it created separate root and user partitions. I don't want Ubuntu to mount the openSUSE root partition.

Is that possible??

---

### Post by meanerelk on 2008-05-18
Do you mean these partitions are getting mounted when you boot? If so, just edit fstab:

```
sudo nano /etc/fstab
```

and remove the lines referring to those partitions. Then run

```
sudo mount -a
```

to reload your fstab, which should unmount the partitions that are no longer listed there. Or just

```
sudo umount /media/xxx
```

where /media/xxx is the path to the mount point.

---

### Post by itix on 2008-05-18
Great, thanx...
I've tried a bunch of operatios with fstab befor but I'm a bit afraid of it since I don't get the language at all. Thought I'd wreck the system or something...

**EDIT**: And if it's not listed in the fstab? (neither is the other partition on sdb...)

---

### Post by strabes on 2008-05-18
Ok, just paste the output of the following commands and we'll tell you what to do:```
cat /etc/fstab
sudo fdisk -l
```

---

### Post by itix on 2008-05-18
fstab:

```
/etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3c4339ad-f940-4fae-9eb6-7afe84712567 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=a4c2da49-2825-4286-8a49-6d98ed5392de none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
itix@acer:~$
```

(said it wasn't there :p just sda-partitions and cd-drive)

fdisk list:
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x34fe34fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9355    75144006   83  Linux
/dev/sda2            9356        9729     3004155    5  Extended
/dev/sda5            9356        9729     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       13066   104952613+  83  Linux
/dev/sdb2           13067       14593    12265627+  83  Linux

```

As you can see, here be sdb with openSUSE (and no pirates).


**EDIT:** Oh right... you might wan't to know that sdb is an external drive. Would that be the source of the problem here?

---

### Post by danwood76 on 2008-05-22
You can add it to the fstab with noauto option and it wont mount it upon boot.
So you could do something like:

```

/dev/sdb1       /media/drive1   ext3 defaults,noauto     0       0
/dev/sdb2       /media/drive2   ext3 defaults,noauto     0       0

```
This will then not automount that partition on boot. (and also not mount when mount -a is used)

---

### Post by itix on 2008-05-22
Worked wonders... thanx.

---

