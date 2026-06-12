---
title: "Dual-Boot Problem"
date: 2007-08-18
forum: General Help
---

### Post by LiteDrive on 2007-08-18
I've searched, and found similar threads relating to this problem. The only thing is, I barely understand any of it at all. I dual-booted XP Media Center on my primary hard drive, and made 4 partitions. I then installed Ubuntu on my secondary, a SATA 160gb. I remember installing a few programs: Envy (although I can't remember whether or not I actually installed the drivers..); Compiz Fuzion, and Pidgin. 

I then restarted my PC. For some reason, it immediately loaded up Ubuntu, without a boot menu. So I decided to restart again. I pressed the "ESC" key, when prompted to do so. Upon loading up the boot menu, Windows was gone. I've tried a few things, mostly relating to commands such as "root (hd0,1)", through Grub, in the terminal. Everything I've tried hasn't worked, so far. Any help would be great. Thanks. 


Note: My friend actually helped me a bit with Ubuntu; he knows more about Linux than I do, but we're both still learning. All I really did was initiate installation of Ubuntu, and I followed a specific guide to install the 3 programs, which I listed above.

---

### Post by confused57 on 2007-08-18
Open a terminal(Applications---Accessories---Terminal), post the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"

also post your Ubuntu entries in your /boot/grub/menu.lst:
```
gedit /boot/grub/menu.lst
```
menu.lst is short for menu.list

---

