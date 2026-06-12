---
title: "Ubuntu broke, about to cry"
date: 2007-12-28
forum: General Help
---

### Post by ketzerei on 2007-12-28
Okay, recently I installed a modified version of XP because I hated my windows boot, and I liked it and it worked seemlessly and it played will with my beloved Ubuntu. Now, just about maybe... 15 minutes ago, I go to boot into my Ubuntu to play some ut2k4. It does the normal grub boot, then it says something like "the bios cannot handle this many sectors" or something like that, or it gives me the error that says something along the lines of the partition table is corrupted, and I'm about to cry because I have to type this from my windows boot. I'll try to post the exact error message here in a few minutes. :'(

Here are the exact error messages I get:

"Error 16: Inconsistent file system structure."
and
"Error 18: Selected cylinder exceeds maximum supported by bios."

---

### Post by meierfra on 2007-12-28
Boot from the Ubuntu LifeCD.
Lets see whether you can access your files  on the Ubuntu partition. Go to Places->Computer and double click the icon for the Ubuntu partition.

You should now have an icon on the Desktop  name "disk"  

Next open a terminal (Applications->Accessories->Terminal) and  post the output of 
```
sudo fdisk -l
```

and 

```
cat /media/disk/boot/grub/menu.lst
```
(if the ubuntu desktop icon  was named "disk-1"  your need use "disk-1"  in place of "disk")

---

### Post by ketzerei on 2007-12-28
I can't explain exactly what happened, but I think my MBR became corrupted. What I did was I put my Super Grub Boot Disk in, and re-installed GRUB, and somehow it now works. Thanks anyway. :)

---

