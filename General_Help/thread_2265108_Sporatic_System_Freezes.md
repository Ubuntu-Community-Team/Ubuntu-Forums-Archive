---
title: "Sporatic System Freezes"
date: 2015-02-12
forum: General Help
---

### Post by Bob_Pennington on 2015-02-12
Having problem with system freezes.  Does not occur when system is just running idle.....only when running apps.  Apps will be running just fine & then system freeze with keyboard "Num & Caps" lights flashing.  Only recourse is powering machine down.....waiting at least 10 min. & then reboot.  Reboot has to be SAFE Mode; which I tend to beleive is hardware related.  Problem is after reboot; checking all logs, does not reflect anything from the freeze.....just latest boot activity, etc.  Can anyone give me suggestions on how I might enhance logging to catch the freeze; or some other method to find out what's going on.  Sometimes it will flash info on fullscreenn text...but flies by so fast; cannot determine root cause.  It just sets there; no command line; nothing.  Thanks in advance for any help provided.

---

### Post by kerry_s on 2015-02-12
if the keyboard lights flash, that means it's a kernel crash.

check your memory(ram) using the live or rescue system.

(to enter rescue hold the shift key before grub load, just after system startup(bios loads) select rescue)

---

