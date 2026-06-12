---
title: "Dual booting with XP and Edgy"
date: 2006-11-25
forum: General Help
---

### Post by yojimbosteel on 2006-11-25
I was wondering what's the best was dual boot with Ubuntu (edgy) and Windows XP. I have already created my partitions and operating systems.

Part 1: Linux boot ext2
Part 2: Linux swap swap
Part 3: Linux root ext3

Part 4: Windows XP ntfs

Thanks

---

### Post by pay on 2006-11-25
It is easier to install Windows first and then Ubuntu will install grub for you and set it up.

---

### Post by syadnom on 2006-11-25
easy enough to install windows to the 4th partition.  then you can search to forums for the boot commands to put in grub.conf/menu.lst .  just pop the ubuntu livecd in and get to a console and do a 

grub
install dh0
setup hd0,0
quit

then add the windows chainloader lines to the /boot/grub/menu.lst which you may have to mount to a temporary folder on the livecd system

sudo mkdir /tempboot
mount /dev/hda1 /tempboot
nano -w /tempboot/grub/menu.lst

then reboot.

##make sure to put the windows stuff on the very bottom of menu.lst and also make sure you have a timeout line set in menu.lst so you actually get to choose!

__________________
and yes, the easiest way is to install windows first and let the ubuntu installer set everything up for you.


__________________

---

### Post by umanzor on 2006-11-25
Windows first, then Edgy, and it will install and set up GRUB correctly for you. I my personal opinio I prefer using an external partitioner to set up the hd before installing.

---

