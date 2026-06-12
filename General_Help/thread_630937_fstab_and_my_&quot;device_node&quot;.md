---
title: "fstab and my &quot;device node&quot;"
date: 2007-12-03
forum: General Help
---

### Post by d0nuts on 2007-12-03
TRying to install a game with wine and I need a symlink to my cd drive. The guide I'm following says this:

It helps to add a device node symlink, so do the following. If your cd-rom drive letter in winecfg is d: and the corresponding device node to your mount point is /dev/hdc then run the following command:
$ ln -s /dev/hdc ~/.wine/dosdevices/d\:\:
Note, you *must* have two colons! You can tell what your device node is in /etc/fstab or viewing your boot-log.

My drive letter in wine is D and I opened fstab but I don't know what I'm looking for. here is my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=741f7f78-d183-4d5a-9561-222e3df40763 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=ed604c2b-e206-4a21-9710-973a9fac6cd7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

What should I be looking at?

---

### Post by geraldm on 2007-12-04
You should be looking for the mount point of your CD drive:
It is /media/cdrom0, so "/media/cdrom0" should be used in place of "/dev/hdc" in the link.
The third line in fstab contains the commented help line, and <mount point> is the second element in the line.

Gerald

---

