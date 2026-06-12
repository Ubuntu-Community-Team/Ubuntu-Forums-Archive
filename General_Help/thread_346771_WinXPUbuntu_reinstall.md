---
title: "WinXP/Ubuntu reinstall"
date: 2007-01-26
forum: General Help
---

### Post by sNNooPY on 2007-01-26
Hello everyone!

First of all, this is my configuration:

ASUS P5B Deluxe WiFi-AP
Intel Core 2 Duo E6600@2.4GHz
Crucial 2x512MB Kit (CT2KIT6464AA667) DDR2@667MHz
Leadtek WinFast PX7900 GS TDH, 256MB GDDR3
Seagate 320GB(SATA-II)+160GB(SATA)

I've got WinXP on the first drive and I've installed Ubuntu later on the second drive.
Out of 160GB I gave Ubuntu 5+5GB (5 for / and 5 for swap). Since I'm a total Linux newbie, I obviously gave too much space to swap. Here's what I wanna do:

1. I want to REMOVE the current Ubuntu installation (and GRUB along with it...) and then reinstall it.
2. I want to setup GRUB to load into WinXP by default. HOW do I do that?

Should I consider using 64bit Ubuntu? Mind that I want to LEARN Linux with Ubuntu.

---

### Post by Jimmey on 2007-01-26
If you put in the install CD, which nowadays is the liveCD aswell, then you should be able to delete the partitions that you want to delete using the "Gparted" program that's selectable from the menu, once the CD's loaded.

Then, you can just install Ubuntu again, how you want. 

To make Windows boot as default, AFTER the installation, you'll need to edit GRUB's menu.lst. You can do this by typing
> gksudo gedit /boot/grub/menu.lst
into a terminal. Somewhere down in that textfile is a description of how to change the default OS.

---

### Post by sNNooPY on 2007-01-26
> **Jimmey said:**
> If you put in the install CD, which nowadays is the liveCD aswell, then you should be able to delete the partitions that you want to delete using the "Gparted" program that's selectable from the menu, once the CD's loaded.

Then, you can just install Ubuntu again, how you want. 

To make Windows boot as default, AFTER the installation, you'll need to edit GRUB's menu.lst. You can do this by typing

into a terminal. Somewhere down in that textfile is a description of how to change the default OS.
thnx!
I'll try it!

---

