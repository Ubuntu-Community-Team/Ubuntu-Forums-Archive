---
title: "How to stop auto-reboot after power outage?"
date: 2007-07-01
forum: General Help
---

### Post by Zill on 2007-07-01
IBM 6339 Netvista desktop PC:
Any ideas about the best way to stop this PC automatically rebooting after a power outage?  ie. simply staying off until Power button is pressed.
Haven't found a BIOS option for this (yet!) so can it be done by Ubuntu?

---

### Post by scooper on 2007-07-01
If the BIOS and the hardware doesn't help you can at least prevent the GRUB boot loader from starting the default menu item after a certain amount of elapsed time.  Your computer will be on, but not booted into the operating system.  The "timeout" option in /boot/grub/menu.lst controls the automatic default bootup.  I don't know whether you'd have to set that to a really big number or something else, like zero.

If you really want it to power off there may be a tricky GRUB way to do this after a timeout that I'm not familiar with.  I'd poke around.  E.g. set up a special default GRUB menu item that powers down.  Sounds ugly, but I can't think of a better way.  Are  you positive there's no BIOS setting about what to do in case of power failure?

Good luck,
steve

---

### Post by Zill on 2007-07-03
Thanks for the advice Scooper.  As this seems to be a BIOS problem, I checked out the support(!) at

[http://http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-59754]("www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-59754")

and found that this is a known bug with older BIOS's:
> The system powers on and boots to the operating system after the AC power has been restored from a power outage. This happens regardless of whether the system had been powered on or off when the AC power was lost.

IBM kindly provide a self-extracting .exe file to flash the BIOS.  All I have to do now is figure out how to extract a bootable floppy using my Linux-only system :-(

Anyway,  thanks again for the info - I may need to try the GRUB route if I can't flash the BIOS!

---

