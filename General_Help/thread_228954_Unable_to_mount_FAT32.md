---
title: "Unable to mount FAT32"
date: 2006-08-03
forum: General Help
---

### Post by metalsam on 2006-08-03
I have a FAT 32 slace hard drive on my comp that ubuntu cant mount. Before I switched from XP to ubuntu, i put all my music, videos etc onto this drive, because i thought linux could handle fat32.

Heres the error:

error: device /dev/hdb5 is not removable

error: could not execute pmount

All help greatly appreciated. Thanks :D

---

### Post by ciscosurfer on 2006-08-03
Please post your /etc/fstab```
cat /etc/fstab
```

---

### Post by metalsam on 2006-08-04
[fstab]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
[/fstab]

---

### Post by CameronCalver on 2006-08-04
to see if it is working just try
```
sudo mkdir /mnt/fat32
```
```
sudo mount /dev/hda5 /mnt/fat32
```
then go to /mnt/fat32 and see if it is all there

---

### Post by metalsam on 2006-08-04
I assume you meant hdc....
```

sam@sam-ubuntu:/mnt/fat32$ sudo mount -t vfat /dev/hdc /mnt/fat32
mount: No medium found

```

---

