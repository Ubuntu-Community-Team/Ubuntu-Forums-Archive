---
title: "[SOLVED] merge partitions"
date: 2008-04-03
forum: General Help
---

### Post by StOoZ on 2008-04-03
I have a windows XP 20GB partition, which I would like to convert to ext3 and add it to my other 88GB linux partition , is it possible? 
I dont have any use for winxp whatsoever.
here is my filesystem:
> Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/hda2     ext3     88G   23G   61G  28% /
proc          proc       0     0     0   -  /proc
/sys         sysfs       0     0     0   -  /sys
varrun       tmpfs    506M  132K  506M   1% /var/run
varlock      tmpfs    506M     0  506M   0% /var/lock
udev         tmpfs    506M   84K  506M   1% /dev
devshm       tmpfs    506M     0  506M   0% /dev/shm
devpts      devpts       0     0     0   -  /dev/pts
lrm          tmpfs    506M   24M  483M   5% /lib/modules/2.6.22-14-generic/volatile
securityfs
        securityfs       0     0     0   -  /sys/kernel/security
/dev/scd0  iso9660    700M  700M     0 100% /media/cdrom0
/dev/hda1  fuseblk     20G   15G  4.6G  77% /media/Windows

---

### Post by bodhi.zazen on 2008-04-03
gparted will do this for you.

You will need to run it from a live CD. You can use the Ubuntu Desktop CD, the gparted live CD, or any live tool with gparted on it.

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

---

### Post by StOoZ on 2008-04-03
I have the ubuntu 7.10 CD , so I can put it in the drive , run it, make it load the ubuntu from the CD, and then use Gparted from there?

---

### Post by bodhi.zazen on 2008-04-03
That should work just fine.

Be careful though you may need to update /boot/grub/menu.lst and /etc/fstab (on the Ubuntu partition) manually afterwards.

Here is an overview of how to do that part (not exactly, but it will give advice on how to mount your ubuntu partition and edit the relevant files):

[http://ubuntuforums.org/showthread.php?t=316237](http://ubuntuforums.org/showthread.php?t=316237)

---

### Post by StOoZ on 2008-04-04
thanks.

---

