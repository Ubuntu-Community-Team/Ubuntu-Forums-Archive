---
title: "Where did my menu.lst go?"
date: 2008-01-15
forum: General Help
---

### Post by sunfish on 2008-01-15
A few days ago I noticed on bootup that my Grub menu had a duplicate entry so I wanted to edit menu.lst. I've done this before, so it's no big deal for me, but when I looked in /boot/grub, there was NOTHING there! No menu.lst, nothing. I did a 'locate -u' to update my file database and then 'locate menu.lst' and all that came up was a couple example files in /usr/share/doc. WTF? This laptop has only one hd, /dev/hda. It still boots into one of three kernel versions I have installed, plus the memtest, and not the one that is in /boot. (What are those files in /boot anyway?) Where is this stuff hiding?

~$ uname -a
Linux Guppy 2.6.17-11-generic #2 SMP Fri May 18 23:39:08 UTC 2007 i586 GNU/Linux

~$ ll /boot
total 8928
-rw-r--r-- 1 root root  285573 2007-12-17 21:32 abi-2.6.17-12-generic
-rw-r--r-- 1 root root   74688 2007-12-17 19:49 config-2.6.17-12-generic
drwxr-xr-x 2 root root    4096 2008-01-15 16:36 grub
-rw-r--r-- 1 root root 6373251 2008-01-01 15:33 initrd.img-2.6.17-12-generic
-rw-r--r-- 1 root root  730033 2007-12-17 21:32 System.map-2.6.17-12-generic
-rw-r--r-- 1 root root 1636038 2007-12-17 21:32 vmlinuz-2.6.17-12-generic

~$ sudo fdisk -l /dev/hda
Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          31      248976   83  Linux
/dev/hda2              32        4864    38821072+  85  Linux extended
/dev/hda5              32         216     1485981   82  Linux swap / Solaris
/dev/hda6             217        4864    37335028+  8e  Linux LVM

/dev/hda1 is where /boot is located since this laptop has an old BIOS that won't see a drive bigger than 8 gb.

I can do 'update-grub' and get a menu.lst in /boot/grub, but it only shows the kernel files in /boot, ie. 2.6.17-12. Rebooting the machine gives me a completely different menu showing many more bootable options.

Color me flummoxed.

---

### Post by bodhi.zazen on 2008-01-15
You need root permissions, try :

```
gksu gedit /boot/grub/menu.lst
```

---

### Post by sunfish on 2008-01-17
SOLVED!

Something I did must have changed my /etc/fstab to delete any reference to my boot partition which is /boot. Duh! Adding a mount command in /etc/fstab fixed the bugger and now I have my menu.lst back.

---

### Post by kellemes on 2008-01-17
Just out of curiosity..
"locate -u" updates the db? Just like "updatedb"?

"man locate" shows me no -u option.. or am I misunderstanding something?

---

### Post by sunfish on 2008-01-19
locate -u actually creates the database. It's more brute force than updatedb. Must be done as root.

---

