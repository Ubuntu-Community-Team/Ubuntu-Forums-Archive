---
title: "Stuck at boot up suddenly with Ubuntu studio"
date: 2015-04-19
forum: General Help
---

### Post by Christopher Newtoit on 2015-04-19
Help me out people.  I am stuck at boot up on Ubuntu studio after messing with one of the sound generators I got stuck in a guest login loop that would not work.  Seems to be problems with sound switching applications like from a media player to a sound generator. Anyway got the boot repair output of 
[Http://paste.ubuntu.com/10854202/](Http://paste.ubuntu.com/10854202/)

On another note I only use studio for music mixing and mastering and do my recording elsewhere.  I am strongly considering dropping studio and going back to normal old Ubuntu or kde and then installing ardour to mix on( after I backup all my wav files using the live disc of course) Would I be missing out on much?

---

### Post by oldfred on 2015-04-20
It looks like you booted Boot-Repair in UEFI mode, but your system is installed in CSM mode.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

Make sure your system is set to only boot in BIOS/CSM boot mode.

Can you boot recovery mode or second line in grub menu?

I do not see anything in Summary report that looks out of place so you may have a driver issue.

---

