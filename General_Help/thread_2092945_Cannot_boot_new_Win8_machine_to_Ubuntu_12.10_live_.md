---
title: "Cannot boot new Win8 machine to Ubuntu 12.10 live cd to install dual boot . . . help"
date: 2012-12-09
forum: General Help
---

### Post by carusoswi on 2012-12-09
My son purchased a Samsung 700Z5C laptop that came with Windows 8 preinstalled.  All we want to do is to install Ubuntu 12.10 as a dual boot.
I have a live CD, but cannot get the machine to boot to the CD to start the process.

My mind keeps telling me this should not be hard.  What am I missing?

Help and advice appreciated.

Caruso

---

### Post by carusoswi on 2012-12-09
So, the solution was to hit F2 while booting to go into the bios setup, disable secure boot, then select the correct OS option (sorry, I don't remember the exact terms, but when I next have a chance, will go into the boot menu and write those down so I can post them here.

Then, I set the boot priority so that the SATA CD is at the top of the list.

That did it for me.  Pressing f10 to exit saved those settings.

Sorry I am not more precise with my terminology, but hopefully, this will save someone else an afternoon of stabbing around looking for a solution.

Caruso

---

