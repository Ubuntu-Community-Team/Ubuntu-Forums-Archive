---
title: "Display size during Boot"
date: 2007-03-31
forum: General Help
---

### Post by Tintinnabulation on 2007-03-31
When I boot the display only uses a part of the screen making my grub boot screen hard to read.  

It looks fine once i get to the login screen.  I tried enabling screen expansion in the bios and saving and that worked initially but on the next boot the problem was back again.

Maybe grub is overwriting the bios setting in some way? 

I'm dual booting xp and 6.10 by the way.
Thanks in advance for any help.

---

### Post by Sef on 2007-03-31
I have the same problem and there was post about it.  If I remember correctly, the boot screen is set for 800 x 600.   That post did give  way to fix it.   Will post it if i find it.

---

### Post by Tintinnabulation on 2007-04-02
I haven't been able to find a solution.  I've tried adding vga then some number to the grub menu.lst but that didn't work.

---

### Post by Zeroedout on 2007-04-04
> **Tintinnabulation said:**
> I haven't been able to find a solution.  I've tried adding vga then some number to the grub menu.lst but that didn't work.
Hey, I have had the EXACT same problem. I am using a Latitude D400 though. The number you used, was it 791 or 792, cause when I tried those, it told me I was using an unrecognized number or something to that effect. I think this might be a bug as 791 worked on an older version, though I may be wrong. However to fix this, I used vga=773, I  can't remember what the screen res is, but it does work on my laptop's lcd. If it does not work for you, I'de just google grub vga and look for a chart with the numbers. A few questions though,  What laptops are you guys using? Did this happen on a previous version of ubuntu?

---

### Post by Tintinnabulation on 2007-04-04
I'm using a dell inspiron 6400 and still on my 1st ubuntu version.  Tried various vga numbers using this link: 
[http://ubuntuforums.org/showthread.php?t=258484]("http://ubuntuforums.org/showthread.php?t=258484")
But that didn't seem to change anything.  Probably is some obscure setting somewhere
I think I'll live with it.

---

### Post by shotgunefx on 2007-04-04
I'm using vga=788 on my Inspiron 8600. Not a dual boot though.

---

