---
title: "Greek filenames do not display correct"
date: 2007-05-08
forum: General Help
---

### Post by gpsalt on 2007-05-08
I encountered the following problem with Feisty: Although initially the Greek filenames were displayed correct, at some point in time this was not happening any more. Both on root (ext3) as well as on a mounted vfat partition, greek filenames are not displayed correct. In vfat, I get weird characters, while in ext3 I get question marks. At the same time, German filenames display correctly for example. Upon installing Feisty these kind of problems dont exist as far as I noticed. Something messed up with the encoding afterwards. So, any ideas?

This is how my fstab looks like (I can hardly imagine that fstab was changed after installing Feisty):

[FONT="Courier New"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=2fb88a9a-7fe5-4a60-bf59-d4f00396891b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb3
UUID=4d0f807a-1333-485d-b799-370275f4eeef /home           ext3    defaults        0       2
# /dev/sda5
UUID=8D03-AFBA  /media/windata  vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=A4906FAC906F8420 /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb1
UUID=04724aab-5f9a-4275-90ab-811c2778c379 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0[/FONT]

---

### Post by gpsalt on 2007-05-10
Still no clue as to what is causing the problem. Everything else works fine (except firefox crashes from time to time). Only solution seems to be reinstalling feisty, so PLEASE HELP me avoid this overhead! Btw, is there a way to make a massive repair/reinstall of things like, e.g., KDE, without however reinstalling feisty itself?

---

