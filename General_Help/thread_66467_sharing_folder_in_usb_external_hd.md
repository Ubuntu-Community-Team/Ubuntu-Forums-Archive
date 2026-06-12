---
title: "sharing folder in usb external hd"
date: 2005-09-17
forum: General Help
---

### Post by giopas on 2005-09-17
Hi!

I've got a problem, but I'm sure I can fix it with your help.

I've created a privatenetwork at home, just for sharing some folders between 2 computers both linked to the same router.

Obviously I've installed Samba in both computer and correctely done all permissions  and modified the fstab in order to mount at boot the shared folders.

The problem is that I would automatically share even a folder placed in an usb external hd that is on the first computer. The problem is that even if I shared it with the same procedure of the already shared folders, this folder is not automatically (and non automatically too) mounted at boot.

The usb external is not statically mounted in the firs computer0s fstab, but is without problem detected at boot.

My question is:
if I want to share a folder of that external hd, have I to statically mount at boot that hd on the first computer's fstab or there is no way to do it?


thnx to every one,
giopas

**EDIT:** I've tryed to modify the fstab, adding the line for the external hd:
```
/dev/sda5	/media/EXTERNAL	vfat		iocharset=utf8,umask=000   	0       0
```
but, at boot I can't find the external hd.
As you can see, this is my external, as Ubuntu rightly has detected typing "fdisk" and then "p":
```
Disk /dev/sda: 203.9 GB, 203928109568 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cilindri of 16065 * 512 = 8225280 bytes

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1               2       24792   199133707+   f  W95 Ext'd (LBA)
/dev/sda5               2       24792   199133676    b  W95 FAT32
```

What can I do?  :neutral:

---

### Post by giopas on 2005-10-21
UP!

the same problem seems happen with [ftp](http://www.ubuntuforums.org/showthread.php?p=433290&posted=1#post433290) sharing way...

could someone tell me if I can do something to share folders placed in my external usb archive? :( 

enjoy, ;)
giopas

---

### Post by giopas on 2005-10-23
I know that is not fair to bump (twice) a post, but... anyone knows a workaround to fix this problem? :???: 

enjoy, ;)
giopas

---

