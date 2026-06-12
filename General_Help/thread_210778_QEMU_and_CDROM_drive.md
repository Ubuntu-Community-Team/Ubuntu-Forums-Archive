---
title: "QEMU and CDROM drive"
date: 2006-07-07
forum: General Help
---

### Post by DarkStarDeity on 2006-07-07
Following the instructions in [this thread]("http://www.ubuntuforums.org/showthread.php?t=187413&highlight=qemu"), I got QEMU working with the accelerator and installed Win XP in the disk image. It all runs nice and fast and I am happy except for one thing - I can't access my CDROM drive. The WinXP install has a D: drive, but if I put a CD into the physical drive, nothing happens. Clicking on the D: drive in Win give the "please insert a disk" message. This problem might be caused by the fact that I have two physical drives in the machine, and looking at teh QEMU doc it seems I can't use two drives at once, but that's fine, I just want one of them to show up. I tried specifying "-cdrom /dev/hdc" but I get the message "qemu: could not open hard disk image '/dev/hdc'". This was the same string I used with the "boot -d" option to install Windows in the first place, so I can't understand why it doesn't work now. Does anyone have any ideas?

---

### Post by 4ebees on 2006-07-25
Hi DarkStarDeity,

try:
 -cdrom /dev/cdrom

and see if that helps

---

### Post by DarkStarDeity on 2006-07-25
I meant to update this, I worked it out. There has to be a data CD in the drive when you invoke QEMU (or use the monitor to mount one). Music CDs (and I presume DVDs also) don't work.

---

