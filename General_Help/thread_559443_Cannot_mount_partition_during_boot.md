---
title: "Cannot mount partition during boot"
date: 2007-09-25
forum: General Help
---

### Post by larsdk on 2007-09-25
Hi,

After a system update this morning my Ubuntu won't start - it says that the partition cannot be mounted. Any suggestions?

Lars

---

### Post by larsdk on 2007-09-25
btw - i think it is the GRUB 17 error that comes to show on boot... If that's of any help to anyone :)

---

### Post by Mike-97470 on 2007-09-25
I'm having the same problem.....for me it seems to be happening every kernel update.  The last time I fixed the root disk in menu.lst to the correct hd(0,0).  This time menu.lst seems to be ok, but fstab had my sda1 and sda5 commented out.  I fixed that but still have the same "error xx can't mount partition" boot problem.

Here's what grub has to say:

grub> find /boot/grub/stage1

Error 15: File not found

grub> root (hd0,0) 

Error 21: Selected disk does not exist

grub> 

What's up with that???  GNOME Partition Editor shows my sda disk like I expect, and if fact the Live CD has it mounted right now.  I'm really baffled!

Oh yeah, my config is a high speed SATA as hd0 with Ubuntu and an IDE/ATA as hd1 with WinXP.  None of the Linux kernels (hd(0,0)) in menu.lst run, but WinXP runs fine.........................................I just noticed that it's root is hd(0,0)..........I going to change it to hd(0,0).....

---

### Post by Mike-97470 on 2007-09-25
..........switching WinXP in /boot/grub/menu.lst to hd(1,0) didn't work, but switching all of the linux kernels to hd(1,0) and leaving WinXP on hd(0,1) did...........this problem for this kernel update solved for me.  Hopefully this will be the last time this mixup occurs!!!

---

### Post by larsdk on 2007-09-27
no solutions to this (other than maybe re-installing linux in which case i will wait until the new release in october) ?

---

