---
title: "Broken Master Boot Record"
date: 2008-06-04
forum: General Help
---

### Post by jaggerlink on 2008-06-04
I have been preparing an old laptop to give to my dad, and have reinstalled Windows on it using a restore DVD with a Norton Ghost image on it supplied by the manufacturer. This image did not affect the MBR however, and I am now stuck at a GRUB prompt with an Error 17 message.  Is there any way to use a live boot Ubuntu disc to edit GRUB to boot my Windows partition or maybe some way to install the Windows bootloader?  Any help would be appreciated.

---

### Post by logos34 on 2008-06-04
If you restored windows to the entire disk, use **Super Grub Disk** to restore windows bootoader.

If you still have ubuntu partition in a dual boot with windows:

Reinstall grub to mbr using [this]("http://ubuntuforums.org/showthread.php?t=224351").

If you still have trouble, mount your root partition from the live cd and post your menu.lst file and fdisk:
[B]
sudo fdisk -l[/B]

and for menu.lst:
[B]
sudo mkdir /media/ubuntu

sudo mount -t ext3 /dev/sda2 /media/ubuntu[/B]

(replace 'sda2' with your actual root)
[B]
gksudo gedit /media/ubuntu/boot/grub/menu.lst[/B]

---

### Post by jaggerlink on 2008-06-04
Thank you so much! Super Grub Disk fixed the MBR, and now Windows boots properly.

---

