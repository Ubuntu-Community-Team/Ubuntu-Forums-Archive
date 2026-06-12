---
title: "Can't load GRUB without external HD"
date: 2007-06-03
forum: General Help
---

### Post by Scooter7 on 2007-06-03
Hi, I installed Linux to my external hard drive, and this weekend I booted up my laptop, only to get an error from GRUB, saying it couldn't load.

It then occurred to me that the boot loader is installed on my external drive, which, at the time, wasn't connected.   And thus my problem: If I'm somewhere that I cannot use my hard drive (say, maybe, on a flight), and I need to work on something quickly, or maybe check my email, I won't be able to.

And so I ask: Is there a way to bypass GRUB and boot directly to either Linux or Windows?

As far as I know, I can't specify where I want GRUB to be installed during Ubuntu installation - it simply assumes I want to install it to 'hd0'.   If I could do this, that would likely be the best solution.

---

### Post by JulianRoot on 2007-06-03
You must create a new partition for the /boot directory which is on the internal harddisk. Then the menu.lst is on the internal harddrive and GRUB can load it.

---

### Post by Scooter7 on 2007-06-04
Thanks, but now I fear I've screwed things up even worse.   I hadn't checked back here until now, and decided to simply remove my Linux partitions and continue using Windows for now.   Bad idea.   Now I can't boot, even with my external hard drive plugged in, as GRUB still gives an error.   Is there a way to remove GRUB?

---

