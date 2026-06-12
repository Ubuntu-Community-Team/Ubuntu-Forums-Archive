---
title: "Only one DVD drive mounting"
date: 2008-04-30
forum: General Help
---

### Post by MangasColoradas on 2008-04-30
Yesterday neither would mount unless I did 'sudo mount', now scd1 mounts when a disk is put in but scd0  still needs ```
sudo mount /dev/scd0
```.

Even after it is mounted, Places->Computer looks like this...

[IMG]http://img241.imageshack.us/img241/1660/screenshotca8.png[/IMG]

It still shows one DVD drive as empty and I only have two not three.

My /etc/fstab looks like this.

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=10b7e5ec-a013-4747-acb3-703b3570f1d1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=842d5f56-c9da-47c6-9477-1af12059e8cc /home           ext3    relatime        0       2
# /dev/sda2
UUID=05DE-C6ED  /windows        vfat    utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=8cbba75e-91c2-4735-ab08-36490b034932 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by MangasColoradas on 2008-05-01
I discovered today that the first disc put into EITHER drive will automount but then the second disc put into the other drive will not.

I suppose its not a huge problem but it *is* bugging me! :confused:

---

### Post by MangasColoradas on 2008-05-02
Seems fine now, it's gone from neither disc drive auto-mounting to one auto-mounting to both auto-mounting.

:lolflag:

---

