---
title: "why is my fat32 read only"
date: 2006-11-18
forum: General Help
---

### Post by jms830 on 2006-11-18
How come my fat32 drive is read-only? This I think only happened after the edgy update.

**My fstab:**
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2 -- converted during upgrade to edgy
UUID=856b4f3b-85d2-4f75-bbae-4a71cb02f2ac / reiserfs notail 0 1
# /dev/hda1 -- converted during upgrade to edgy
UUID=7A18A62418A5DF7F /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda3 -- converted during upgrade to edgy
UUID=85CB-F1F0 /media/fat32 vfat iocharset=utf8,umask=000 0 0
# /dev/hdb1 -- converted during upgrade to edgy
UUID=206287b5-305e-4204-af8a-bba7865a4b1a /home/jordan/Desktop reiserfs user_xattr 0 2
# /dev/hda4 -- converted during upgrade to edgy
UUID=9dc0ae44-ba79-42b6-a949-9258d1edbd4b none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
usbfs 		/proc/bus/usb usbfs devgid=14,devmode=0660 0 0 

```

---

### Post by kartikya on 2006-11-21
I dont know but this happened with me too
create on any of your panels a "custom aplication launcher" 
 call it whatever you want but for command put: gksudo nautilus
 you can now acess your harddisk in root and can copy and edit whatever you want

---

### Post by 900i on 2006-11-21
To make disk Read/Write, "sudo chmod 777 /dev/hda3" in a terminal. This makes it Read/Writable by anyone not just root.

---

### Post by taurus on 2006-11-21
> **900i said:**
> To make disk Read/Write, "sudo chmod 777 /dev/hda3" in a terminal. This makes it Read/Writable by anyone not just root.
Actually, you cannot use the chmod command to set permissions with fat32/NTFS.  You need to use "umask=000" in /etc/fstab if you want to allow others to write to fat32...  And besides, "sudo chmod 777 /dev/hda3" is wrong!!!

---

### Post by 900i on 2006-11-21
Thanks for putting me on the right track

---

### Post by jms830 on 2006-11-23
thanks for the responses. for some reason it seems to have cleared itself up on its own... strange.

---

