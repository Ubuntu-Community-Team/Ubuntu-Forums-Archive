---
title: "Installing new HD on a machine that already has ubuntu installed"
date: 2007-05-11
forum: General Help
---

### Post by ieldib on 2007-05-11
Hi, I have a 250GB HD  that is nearly completely full of data (NTFS formatted), It does not have any OS installed on it, yet everytime  i  install it into my machine  I get a GRUB error 17.  I  checked my menu.lst and it lists  a weird fstab setting for my root partition and their is no seperate boot partition (I guess because LVM is setup).  I have  3 drives total in this machine the one i'am trying to add  so i can  get the data off of it and  format the drive with ext3 so i can move all of it onto a *nix friendly filesystem (but the machine won't boot if i have this hd plugged in their). Anyone have any suggestions ?  

Thanks in advance.

---

### Post by pizzutz on 2007-05-11
I suspect he problem is when you install that hard drive, It is rearranging the order of your other drives.  When Grub looks to 'hd(0,0)'  or wherever to find your linux root, it is finding that new drive instead, which is ntfs, which is giving you the error 17.

try manually editing the grub boot instructions to read at hd(1,0) or hd(2,0)  till you find the actual linux partition, when you find it , you can edit menu.lst to reflect the change permanantly.

Someone here may know an easier way to fix it, but that's what I would try.

---

