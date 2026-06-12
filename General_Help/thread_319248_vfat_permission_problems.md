---
title: "vfat permission problems"
date: 2006-12-15
forum: General Help
---

### Post by rullx on 2006-12-15
hi. some problems with mounting and permissions. i mounted a 20 Gb fat32 formatted hard disk. i did that adding this line in /etc/fstab:

UUID=4582-990C        /media/hdb1     vfat    auto,rw,users     0       0

the volume is correctly mounted at boot time and all. when i log in as a user i don't have the permission to write anything. i should switch to root user. as the root user i can write and all. but i can in no way change the permission to my hdb1  volume. seems like nobody can.

here is the complete fstab file:

[COLOR="Blue"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=4bc8c874-2914-4cd8-b8b4-479ca9141f79 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=0084594E845946F6 /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=4582-990C        /media/hdb1     vfat    auto,rw,users     0       0
# /dev/hda4
UUID=c3785c19-f9f1-45b8-b12d-ecee06bc2769 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0[/COLOR]

and here is the mtab:

[COLOR="Blue"]/dev/hda3 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
/dev/hda5 /media/hda5 ntfs rw,nls=utf8,umask=007,gid=46 0 0
/dev/hdb1 /media/hdb1 vfat rw,noexec,nosuid,nodev 0 0[/COLOR]

i think the problem is in the last line, any idea how to fix it?

thanks

---

### Post by pingvin on 2006-12-15
Don't know if it's of any use to you, but I also have a vfat volume mounted. Permissions work  okay, however I noticed some differences in /etc/mtab:
/dev/hdb1 /media/windows vfat rw,noexec,nosuid,nodev,_uid=1000,gid=1000,umask=0,utf8=true_ 0 0

Mike

PS since when did /etc/fstab have all those crazy numbers at the beginning of the lines? Is that an Edgy thing?

---

### Post by rullx on 2006-12-15
if it helps? it's so ok i would have used this forum before.:D  there is something i have to understand better, but the good thing is i can use that volume now. i'm new to ubuntu and i like it. 

the new mbab now is:

[COLOR="Blue"]
/dev/hda3 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
/dev/hda5 /media/hda5 ntfs rw,nls=utf8,umask=007,gid=46 0 0
/dev/hdb1 /media/hdb1 vfat rw,noexec,nosuid,nodev,uid=1000,gid=1000,umask=0,utf8=true 0 0[/COLOR]


thank you very much. bye

---

### Post by pingvin on 2006-12-15
Just one little thing - and I know "if it's not broken, don't fix it!" but I couldn't help noticing there is a space in between the "u" and the "tf8" in "utf8=true". This shouldn't be there - perhaps it's a typo, but if you copied and pasted it perhaps you ought to alter it. But like I said, if it works...

As far as I know, mtab is just a list that's created by 'mount', based on /etc/fstab. So you would correct these mistakes in /etc/fstab, then check /etc/mtab to make sure it all worked okay. And when you get it working make a backup, /etc/fstab_old or something similar.
Good luck

Mike

---

### Post by rullx on 2006-12-16
thanks for the suggestion. i'll surely check that, very nice of u.


in the hurry of yesterday i forgot to anser your question:

[COLOR="YellowGreen"]PS since when did /etc/fstab have all those crazy numbers at the beginning of the lines? Is that an Edgy thing?[/COLOR]

i installed Ubuntu Edgy from 2 or 3 days, and i always saw that numbers in fstab, they are called uuid, and, as i discovered in my reserches, they are  Universal Unique Identifier, wich are used to uniquely identify a specified device. it must be a recent update in ubuntu to solve the problems depending on using many devices, including portables, usb and so on.

so there is an uuid in front of every mount device now in fstab. after formatting the folume to fat32 using gparted utility, i retrieved that number using:

sudo vol_id -u /dev/hdb1

then i put it in the fstab file. that number sounds a little strange to me because it's different from the other uuid numbers and much shorter, but it works, so, you know...

thanks again for your help

ruggero

---

