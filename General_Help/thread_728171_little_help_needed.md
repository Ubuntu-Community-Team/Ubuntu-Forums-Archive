---
title: "little help needed"
date: 2008-03-18
forum: General Help
---

### Post by Solid_dean on 2008-03-18
Hi im new to this forum and Ubuntu, I have been running this OS for about a week now with no problems but then for no reason at all a huge error happened. When I boot the system on the ram count/system check screen there is vertical white lines across the screen then it all just goes black and the scroll lock and the caps lock light on my keyboard start to flash.

I then ran the Live CD and when that loaded i could see most of the screen but there was a lot of green lines (cannot remember if they were vertical or horizontal.). 
I am now running the live CD on safe graphics mode which seems to work fine. 

I'm guessing that it is a graphics driver issue and i need to know how to install the drivers to the hard drive from the live CD.

---

### Post by deepclutch on 2008-03-18
keyboard LED's blinked?that means a kernel panic ,I suspect.
regarding ur graphics,which card do u use?

make sure ur ubuntu /boot/grub/menu.lst "kernel" line for Ubuntu is correct.like for example the "root=" line -be sure that the UUID points to the ubuntu partition. :)

---

### Post by Solid_dean on 2008-03-18
its just an old geforce mx440

---

### Post by Solid_dean on 2008-03-18
well it seems to be pointing towards the Ubuntu partition on the hard drive.

---

### Post by Solid_dean on 2008-03-18
Is there any way i can do a re-install to get the old settings back without losing all my data?

---

