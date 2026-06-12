---
title: "Problems mounting disk"
date: 2007-01-18
forum: General Help
---

### Post by wagga on 2007-01-18
for a few days ago i installed a new disk in my ubuntu 6.06.1 server. 
Got it up and running after som problems mounting the disk.
After a couple of days running i couldn`t write anything to the newest disk and wondered if i didn`t have the nessesary access. 
when i tried changing the access i got an error: 

d: changing permissions of `/home/samba/mp3/Saybia - These.Are.The.Days/Saybia - These Are The Days/Saybia - Brilliant Sky.mpg': Read-only file system

so i discussed the problem with one of my buddies.
he ment i had mounted read-only.

so i tried umount`ing it. the i got this error:
umount: /home/samba/filma: device is busy
umount: /home/samba/filma: device is busy
umount: /home/samba/mp3/: not mounted

so i checked fstab:

# <file system> <mount point> <type> <options> <d
ump> <pass>
proc /proc proc defaults 0 0
/dev/sda1 / ext3 defaults,errors=remount-ro 0 1
/dev/sda5 none swap sw 0 0
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/sda2 /home/samba/filma proc defaults 0 0

on the last line it should be /dev/sdb1 instead of /dev/sda2
so we figured i had mounted it manually the way it should be... without rebooting.
When i then tried reboot the system wouldn`t boot.

Target filesystem doesn`t have /sbin/init
BusyBox v1.01(Debian 1:1.0-4ubuntu3) built-in shell (ash)
Enter "help" for a list of built-in commands
/bin/sh: can`t access tty;job control turned off

so.. i ran an livecd to try to fix it. then i got this error:
unable to mount the selected volume
error: device /dev/sdb1 is not removable
error: could not execute pmount

Created a new folder and tried mounting againg with: 
sudo mount -t ext3 /dev/sda1 /tommy 
and got error: 
wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage or other error

And now i`m stuck.
Anybody been having this problem?

---

### Post by ben2talk on 2008-04-01
Yes, I'm pissed off - I plug in my camera or my telephone memory card and I have no rights to do anything because it's a READ ONLY disk...

---

