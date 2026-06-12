---
title: "Dual boot Edgy and Win XP"
date: 2006-12-08
forum: General Help
---

### Post by PiEp on 2006-12-08
Hi all,

I have searched this and many other forums for the answer to my question, but I just can't seem to puzzle it together. Here's my problem:

I have a PC with Ubuntu Edgy installed and added a SATA disk (sda1) on which I have installed Windows. I did this by disconnecting all other harddisks and installing Windows.

I now want to reconnect everything and multi-boot from GRUB, setting my BIOS to boot from the Ubuntu drive first. I just can't figure out what entry to add to my menu.lst to make Windows XP boot.

Here's my drive layout:

hda1 ext3 Linux
hda2 swap Linux swap
hdb1 ext3 Data
hdc1 ext3 Music
sda1 ntfs Windows XP

Can someone please help me? Thanks in advance!

---

### Post by rsambuca on 2006-12-08
Do you have 4 hard drives?  hda, hdb, hdc, and sda?

---

### Post by PiEp on 2006-12-09
Yes I do. But I seem to have found the solution by some more trial-and-error. Here is the relevant part of my new /boot/grub/menu.lst for interested people:

### 

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Windows XP Home
map (hd0,0) (hd3,0)
map (hd3,0) (hd0,0)
rootnoverify	(hd3,0)
makeactive
chainloader +1

###

Thanks for the intentions to help!

---

