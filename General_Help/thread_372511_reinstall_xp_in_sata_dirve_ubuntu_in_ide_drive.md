---
title: "reinstall xp in sata dirve ubuntu in ide drive"
date: 2007-02-28
forum: General Help
---

### Post by emanuel79 on 2007-02-28
Hi i have ubuntu installed on an ide drive and xp on a sata drive. I have to reinstall xp in the sata drive when i try to do so i tells me that it have to write something in the ide drive but the partition is unknown and i should delete it or make freespace (no partition) to install. Do i have to resize the partition and let it write it and afterwards reinstall grub? Is it safe? Is there something else that can be done?

---

### Post by chewearn on 2007-02-28
Windows setup is notorious in wrecking havoc on ubuntu dual boot setup.  Do not let Windows setup write anything onto your harddisk where you have ubuntu installed.  Can you post the way you have setup your dual boot?
1. Which is your primary boot disk, where you have GRUB installed?
2. output of: cat /boot/grub/menu.lst
3. output of: cat /etc/fstab

---

### Post by emanuel79 on 2007-02-28
This is the output of cat /boot/grub/menu.lst (comments excluded)

default         0
timeout         10

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hdb1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hdb1 ro single
initrd          /boot/initrd.img-2.6.17-11-generic
boot

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet
boot

title           Other operating systems:
root

title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault

makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

the output of cat /etc/fstab is this

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=126a91ab-baf6-4a66-adde-96134171f974 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=235b7dfb-3401-4615-9c4e-f2c3d97fc1d7 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/sda5       /home   ext3    nodev,nosuid    0       2

windows is installed in sda1. It isn't in fstab.
Also I checked the bios setup and my ide disk is in the primary slave slot, the secondary master and slave are 1 dvd recorder and a cd recorder don't know if this helps.

---

### Post by chewearn on 2007-03-01
Ok, it helps a lot.  Here is my suggestion:
You should temporarily remove the ubuntu HDD from your PC, then run Windows setup.
After setup is done, you can put back the ubuntu HDD, and it should be able to work without any reconfiguration required.

---

### Post by emanuel79 on 2007-03-01
I thought the same but i wanted to be sure if it was ok
Thanks a lot!!

---

### Post by mahiyar on 2007-03-02
Only thing that when you reinsert your ide do not forget to change your bios settings to boot from ide, btw did it work?

---

