---
title: "Retreiving files from old HDD with courupt widows 7 installed"
date: 2014-04-26
forum: General Help
---

### Post by Steven_McCutcheon on 2014-04-26
Greetings 

Long story short, my windows 7 machine mother board took a dump  I built a new machine and installed 14.4 (im very happy to be back, I havent used Ubuntu since around 2008)  My windows drive booted the first time on the new machine, now it wont boot, windows wont load.  How can I mount the drive and manually remove all my files.

Thank you.

---

### Post by TheFu on 2014-04-26
Welcome back.  You've missed some great times here. Since 10.04, Ubuntu really has been completely awesome!  The only things I do on MS-Windows are video editing, recording TV, and management of stocks. Everything else has been easier on Linux for many years.

Use the built-in file manager to access the drive (nautilus or pcmanfm).  The partition probably already shows up in the list on the left side when connected.  Might need to load samba-client packages.  In 2008, this stuff was much harder - these days, just connect up the USB drive and it should pop up a dialog asking if you'd like to mount it.

If the HDD is corrupted, using Windows disk tools really the best answer to get it back before connecting it with Linux.

Windows7 has DRM built into the OS. If the hardware changes much, then the DRM will likely prevent it from running. If the Win7 was pre-installed with a PC/laptop purchase, that license is tied to the specific hardware and will NOT run on hardware of a different model.  OTOH, moving a partition with Liunx on it will work provided the CPU is reasonably compatible with the installed OS - so of the new CPU is 64-bit, pretty much any old Linux will run, but if the new CPU is only 32-bit and the old install was a 64-bit version, that will fail to work.

---

### Post by whitesmith on 2014-04-26
If your issue was purely DRM, I think Windows would put up a notice requiring reactivation. Is this a dual-boot config with the Windows HDD as a second drive? If it is and if I understand your post you simply want to copy files and then remove everything on the old HDD, so start from a terminal with this:```
sudo blkid
``` This one-liner will tell you if Ubuntu recognizes the Windows HDD. If it does, you can try getting into safe mode or maybe the last known good configuration. No go? Then get into the recovery console and follow basic repair steps. At some point the thing should boot. Then, after you've copied your files with Ubuntu, just follow an old post at [http://ubuntuforums.org/showthread.php?t=267869](http://ubuntuforums.org/showthread.php?t=267869) to format the Win HDD as ext3/4 to wipe everything away. Cheers.

---

### Post by TheFu on 2014-04-26
He has swapped motherboards - MS-Windows doesn't like that at all - changing the south bridge does bad things for Windows compatibility.  I don't think it will ever boot that old OS installation, unless the exact same MB is the replacement.  At this point, he can either reinstall with a "retail copy" of Windows :( or move forward to Ubuntu. ;)

Or did I misread the OP?

---

