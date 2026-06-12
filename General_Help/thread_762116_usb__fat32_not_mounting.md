---
title: "usb  fat32 not mounting"
date: 2008-04-21
forum: General Help
---

### Post by mrsudo on 2008-04-21
I just installed Hardy with no problems.  I tried  to change the mount point of a usb hd fat32 partition /media/fat32  in the gui options menu.  rebooted and now it wont mount.

The unmounting partition is /dev/sdb1 which doesnt even seem to be in fstab

i even tried doing a fresh install to since it was relatively new anyways.... and it still wont mount.

error:  
mount_point cannot contain the following characters:
newline, G_DIR_SEPERATOR (usually /)

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=9ade6e00-f037-4eac-9168-4bc6b53b20c7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb2
UUID=0682a1f2-6616-4b9f-82f2-73efc0936545 /home           ext3    relatime        0       2
# /dev/sda4
UUID=a4730631-c81d-4c49-97ab-39176ad37ee7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by mrsudo on 2008-04-22
Update:  I booted into XP last night to find that not only does it not mount in linux but windows as well.  what could i have possibly done? :(

---

### Post by mrsudo on 2008-04-23
SOLVED!!!

added a line to my fstab:

```
/dev/sdb1	/media/fat32	vfat	defaults	0	0
```

then a simple ... 
sudo mkdir /media/fat32
sudo mount /dev/sdb1

---

