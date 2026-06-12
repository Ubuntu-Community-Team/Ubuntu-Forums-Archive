---
title: "Problem mounting"
date: 2013-02-05
forum: General Help
---

### Post by lobo115 on 2013-02-05
hello, i am using kubuntu and dolphin and i want mount disk with specific permisión like 777 or in umask 022 something liike that, thery are examples, but i need it mount trought dolphin, becouse a newbie user power on my pc, and he yet doesn't use terminal.
i try with 
```
/dev/sda1                                  /media/sda1     ntfs  nls=iso8859-1,ro,noauto,umask=722,user,owner  0  0 
```
but it appear a error message:

```
org.freedesktop.UDisks.Error.Failed: Error mounting: mount exited with exit code 1: helper failed with:
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
http://ntfs-3g.org/support.html#unprivileged
```

It is becouse my user it isn't root, so there is a eay that i edit udsiks default permissions to 755 or 022, so when dolphin mount disk folder take that permisions, THZ
PS. i dont want automount.

---

### Post by collisionystm on 2013-02-05
First of all, Ubuntu cannot dictate permissions on an NTFS file system.

Secondly, You should be editing the fstab with sudo, which would give you root permissions.

gksudo gedit /etc/fstab

when finished, save it

open terminal

sudo mount -a to mount all drives or

sudo mount <your mount> to mount the specific.

---

### Post by lobo115 on 2013-02-05
hello thz for your answer, think i dont explain it very well.
Ntfs system doesn't have permision, but folder when i mount it yes, like:
```
drwx------ 1 xxx xxxx  24576 2013-02-05 20:05 Info
```

```
drwxrwxrwx 2 root        root          4096 2012-07-14 14:30 info
```

both of them are mountpoints to /dev/sda1 only that Info is when i used dolphin to mount, and my other user can't read it. And other is the one that i create, and i mount using:
```
 sudo mount -t ntfs /dev/sda1 /media/info
```
that is only a example, i wont use 777 attribute for mountpoint. My friend mount it throught dolphin so when i am going to look at, my files that are in that disk, i cant't read it, until i umount that disk and mount it again using console, but sometimes he is written in disk large amount of files, so i need wait until he finish, and then umount it. So i was looking for a way, that when dolphin mount it, folder takes permision that i need for example 755. THZ

---

### Post by Abu Retaj on 2013-02-05
[FONT="Georgia"][SIZE="4"][COLOR="Blue"][CENTER]I want to Trying Kubuntu To Ubuntu?????????????[/CENTER][/COLOR][/SIZE][/FONT]

---

