---
title: "Booting vista breaks GRUB, stuck in reboot @stage 1.5"
date: 2008-06-29
forum: General Help
---

### Post by NDJeff on 2008-06-29
My system is set up in a triple boot, with Vista Business x64, XP, and Hardy x64.  It worked fine for months, but recently something keeps destroying my GRUB entries.  After using Vista and powering down the PC, the next reboot my GRUB is messed up.  The system will get stuck in a constant reboot loop, flashing "GRUB stage 1.5" on the screen, then restarting.  
I have been using Super Grub to fix my bootloader, and it restores GRUB.  However the next cold boot after using Vista I am right back to where I started! :confused:  Is there something I can do to fix this, or am I stuck with either needing my Super Grub CD every morning; or getting rid of Ubuntu?

---

### Post by Aphoxema on 2009-05-06
I'm having the same problem, I'm surprised I can't find any other information on it.

> **NDJeff said:**
> Is there something I can do to fix this, or am I stuck with either needing my Super Grub CD every morning; or getting rid of Ubuntu?

I'm thinking similarly, except replace "Ubuntu" with "Vista".

---

### Post by Aphoxema on 2009-05-11
I ended up resorting to using EasyBCD to restore the Vista bootloader and I'm using that to boot grub which now goes straight to Ubuntu. Not the solution I would have preferred but it's elegant enough and solves the problem.

---

### Post by graekidd on 2010-01-28
Check this, it helped me.

[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)

---

