---
title: "won't POST after uninstall"
date: 2007-11-08
forum: General Help
---

### Post by 800 on 2007-11-08
Hi, I'm running Vista home premium 32-bit, or was, until my computer stopped posting. I had installed kubuntu using wubi, and had gotten my computer to a state where it would boot up fine in either operating system. I then uninstalled kubuntu (via uninstalling wubi like a normal windows program). The computer worked fine until i turned it off for the night.. the next day, it would not even POST (no BIOS screen, no mobo splash, no beeps, nothing).

I'm not sure if it has anything to do with my uninstallation of my wubi-created kubuntu directory, because i built the comp myself a few weeks ago and i think my mobo is spotty (I'm using a crappy Asus M2N-E SLI, i order an MSI Platinum from newegg so we'll see if that's the problem). But I've been reading a lot of threads on here that hint that wubi might screw with boot loaders.

Some more info: the mobo is definitely getting power, the PSU is fine, RAM checks out, monitor works well with another comp, all of the peripherals work, HDD spins up, video card turns on, the cd tray even opens.

I'm thinking at this point it's either the HDD or the CPU (hopefully not), but if anyone has any suggestions they would be appreciated.

Thanks!

---

### Post by ago on 2007-11-08
Yeah we nuke the muchine if wubi is uninstalled...








..just kidding... 


Seriously, Wubi would not have anything to do with the BIOS, so your issues have probably to do with something else.

---

### Post by CrazyGuy123 on 2007-11-09
if you've got post problems unplug everything except these items:

PSU
Mobo
CPU
Memory
Gfx card
Screen

Ie. remove HDD, keyboard, mouse all other pci cards etc.  See if you now get a screen when booting.  If you do plug things in one at a time till it won't boot again to identify the dodgy component.  If it still doesn't work remove all except mobo and psu (ie. remove screen, gfx card, cpu, and memory) and see if you get a beep code (make sure the beepers plugged in if there isn't an onboard one).  if you still get nothing replace the PSU and\or mobo.

If after doing all that you find it magicly works again then it was a poor connection somewhere.

If you've only just built the system and it's failed sounds like you didn't do a burn in test...

---

