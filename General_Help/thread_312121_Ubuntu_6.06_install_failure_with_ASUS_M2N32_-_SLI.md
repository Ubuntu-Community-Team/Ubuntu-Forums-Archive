---
title: "Ubuntu 6.06 install failure with ASUS M2N32 - SLI"
date: 2006-12-03
forum: General Help
---

### Post by Kurt_Alan on 2006-12-03
Just built an AM2 dual core 5200+ system with ASUS M2N32 - SLI Deluxe.  Ubuntu 6.06 and 6.10 fail repeated install with: " Kernal panic - not syncing; 10-APIC + timer doesn't work."

Google search confirms others with similar problems -- but no solution.  Damn! I wasn't expected problems installing Linux on my new system.

SUSE 10.1 installed with some difficulties.  Must install Failsafe: "apm off, acpi off, no resume, nosmp, no apic, maxcpu = 0, cdd = off 3"

I can only startx in runlevel 3, not default runlevel 5.  I'm up and running with full functionality, BUT if I reboot I lose a lot of my KDE configuration, for example, I run a lot of virtual desktops, and I lose these when I reboot.  So my workaround now is to never reboot.  I'm running Folding at Home 24/7 anyway. . . 

But I'm kind of bummed about this "state of the art" mb and Linux failure/ hiccups . . .

I'd appreciate your opinions, observations . . .

Kurt

---

### Post by SnoopDeVille on 2007-02-19
> **Kurt_Alan said:**
> Just built an AM2 dual core 5200+ system with ASUS M2N32 - SLI Deluxe.  Ubuntu 6.06 and 6.10 fail repeated install with: " Kernal panic - not syncing; 10-APIC + timer doesn't work."

Google search confirms others with similar problems -- but no solution.  Damn! I wasn't expected problems installing Linux on my new system.

SUSE 10.1 installed with some difficulties.  Must install Failsafe: "apm off, acpi off, no resume, nosmp, no apic, maxcpu = 0, cdd = off 3"

I can only startx in runlevel 3, not default runlevel 5.  I'm up and running with full functionality, BUT if I reboot I lose a lot of my KDE configuration, for example, I run a lot of virtual desktops, and I lose these when I reboot.  So my workaround now is to never reboot.  I'm running Folding at Home 24/7 anyway. . . 

But I'm kind of bummed about this "state of the art" mb and Linux failure/ hiccups . . .

I'd appreciate your opinions, observations . . .

Kurt

The solution was quite simple, when the install asked u to run in NO APIC mode u had to go back to the install screen when u booted and press F6 and add the command line  to disable the APIC on install

Problem is i have the same MoBo and no sound ! ... :) grrr

An advice...Flash your BIOS to 0903 (if u have m2n32 sli deluxe)

---

### Post by fructal_jabolcnik on 2008-03-03
0903? where can one find this version of bios for m2n32 sli deluxe...
Writing, becouse i have the same problem...still. will try to flash with  	0706 BIOS version(claims that solves the linux problem)...
I will report my success ASAP :) hope to succeed

---

