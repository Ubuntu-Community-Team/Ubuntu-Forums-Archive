---
title: "installing live cd help please!"
date: 2007-06-20
forum: General Help
---

### Post by simo1234 on 2007-06-20
I have partitioned the disk (with gparted) I have the 3 partitions

dev/hda type mount point format? size used

/dev/hda1/ ntfs /media/hda1 63gb 55gb

/dev/hda2/ swap 1118mb 0mb

/dev/hda3 ext3 / 15841mb 421mb (why some used here

in the format column there is a checkbox to format , i know i dont format the windows hda1 partition but the other two?

also when I right click on either the swap or the / partition and go edit they either appear with 15841mb or the swap part 1118mb (which even one i first change (is this meant to be the same size as in the [size] column

I just went ahead with what i have


ok just went and did it as above

next screen looks like this

[http://img395.imageshack.us/my.php?image=screenshottl3.png](http://img395.imageshack.us/my.php?image=screenshottl3.png)

should i change the boot loader so it dosnt touch the windows mbr like this

[http://ubuntuforums.org/showthread.php?t=426895&highlight=dual+booting+super+easy](http://ubuntuforums.org/showthread.php?t=426895&highlight=dual+booting+super+easy)
does all this look ok


thanks alot

---

### Post by atria on 2007-06-20
You have to format the ext3 partition (hda3) if you want a clean installation. It was most probably left by a previous installation.

As for the mbr, you will need to let the installer install grub to your hard disk's mbr so that ubuntu can be booted too.

---

### Post by orb9220 on 2007-06-20
Looks good and yes the mbr has to be installed on that hd. The mbr does not install on the partitions but on the first track of the hardrive so grub will be loaded on startup and give you the option to boot into ubuntu or xp.

---

