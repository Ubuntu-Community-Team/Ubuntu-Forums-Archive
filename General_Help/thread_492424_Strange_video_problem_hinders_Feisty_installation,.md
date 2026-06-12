---
title: "Strange video problem hinders Feisty installation, Fun with pen-drive Linux."
date: 2007-07-04
forum: General Help
---

### Post by MikeMLP on 2007-07-04
Edit: SOLVED

This was a problem with the bios of the computer.

----------------------------------------------------------------------------

This is a rather bizarre story:

While running on my  Windows partition (probably for a game or something), I did a force shutdown, something I've done many times before ;-).  Upon reboot, I immediately noticed something strange:  The Grub menu, as installed by Ubuntu normally is displayed at a low resolution - something like 640x480 or 800x600 - and fills up the entire screen.  

This time (and each subsequent time, despite a fresh install of Feisty), the Grub menu was displayed in the center of the screen, but the screen was at full 1440x1050.  Thus, the text was there, but small (picture running an NES game in an emulator in windowed mode).  I soon realized that this problem was not limited to Grub.  When selecting my Windows partition, the Windows XP splash screen, also a low-resolution, full-screen image, appeared in a "box" at the center of the screen in the same manner described above.  

Changing screen resolutions and normal use within both operating systems functions normally.  This seemed like more of an annoyance than anything else.  The real problem arose when I tried to reinstall Feisty (as I had done before) using the alternate installer.  The installer makes it to the title screen and then, when I select text install, the screen goes blank, and the machine appears to freeze.  I had to reinstall using the LiveCD.  I know that this wasn't a problem with the CD or the burn because I had used the exact same disc to install Feisty just two months prior.

Today I experimented with Puppy linux, with the goal of getting it onto a USB flash drive.  I had to use another machine to get Puppy to run - the LiveCD for Puppy spun up on boot, but never got past my BIOS splash.  When running on the other machine, I noticed that the first thing Puppy displays is a low-resolution text-only interface, somewhat similar to the text-based Ubuntu installer.  I believe the two issues are related.  To make matters worse, this machine is the only one in the house which has a BIOS capable of booting from a USB flash-drive, thus curtailing my Linux fun, even though I now have a Puppy USB flash drive.

Do these symptoms sound familiar to anyone?  Help me get my flash-drive fix!

---

