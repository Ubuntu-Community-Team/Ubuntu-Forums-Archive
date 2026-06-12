---
title: "Mounting windows partition"
date: 2007-01-22
forum: General Help
---

### Post by fredster001 on 2007-01-22
Hi,

I want to be able to access my windows partition when using Kubuntu. But dont know how to do this. Could somebody talk me through the steps please. I've had a look at other threads but am still a bit unsure.

the windows partition is /dev/hda1 and is FAT32 format
the linux partition is /dev/hda2 and is ext3 format

Thanks alot

fredster001

---

### Post by Pobega on 2007-01-22
Can't you just do> mkdir /mnt/win32
sudo mount -t auto /dev/hda1 /mnt/win32I might be wrong with that though, you should check mount's man page for the right flag to use for the FS type.

---

### Post by fredster001 on 2007-01-22
> **Pobega said:**
> might be wrong with that though, you should check mount's man page for the right flag to use for the FS type.

??? could you explain that please. 

Thanks

---

### Post by bodhi.zazen on 2007-01-22
Mounting and permissions depends on the file system:

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://doc.gwos.org/index.php/NTFS-3g) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```[/list]

_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)
To set permissions, mount the partition, then chmod```
sudo chmod 777 /mount/point
```

To mount at boot you will need to edit /etc/fstab (as outlined in the links above).
For an overview of fstab see: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)

See also [man mount](http://www.die.net/doc/linux/man/man8/mount.8.html)

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by fredster001 on 2007-01-22
ok, i get to the bit in the first tutorial where i edit the file

 /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=f666c697-5470-403a-bad5-ba4df873fe5b /               ext3    defaults,erro$
# /dev/hda5
UUID=11ce90dc-c5f5-4a07-8295-f9ff7fc37757 none            swap    sw           $
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


It says whats above ^^.
I need /dev/hda1 but its not there. do i type it in?

Thanks again

---

### Post by bodhi.zazen on 2007-01-22
Yep, just add it in ...

---

