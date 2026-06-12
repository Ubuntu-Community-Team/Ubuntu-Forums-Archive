---
title: "The file 40_custom for grub does not exist"
date: 2017-06-14
forum: General Help
---

### Post by pixeled4life on 2017-06-14
So, I recently installed android-x86 on another partition on my PC, since now I was using grub-customizer for my grub entries but when I added android through that I couldn't make it work(I used a script I found for the 40_custom) so, I tried editing the 40_custom file but it does not exist on my computer. Instead I have a "40_custom_proxy" and a "49_custom" files, none of which work nor does it work creating the 40_custom and adding the script.

As of right now I have installed a win7, ubuntu 16.04 and android-x86 but I'm unable to make android-x86 boot

Sorry for my bad english, if I need to add any more information I will, I'm kinda new with these things

---

### Post by oldfred on 2017-06-14
Grub customizer deletes all the standard grub files and adds "proxy" files in their place.
You should have backups in a sub-directly. But if you want to remove customizer and manually edit grub configuration, it usually is best just to delete everything and do a total reinstall of grub2. Either the BIOS or UEFI version whichevery you have.

---

