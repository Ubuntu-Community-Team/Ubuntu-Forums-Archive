---
title: "display problem need help asap"
date: 2008-03-25
forum: General Help
---

### Post by ai3gtmc on 2008-03-25
Hi I mistakenly clicked the box that say's "Widescreen monitor" in the monitor preferences or something like that when i restarted my pc it loads but when it comes to the login screen it's so blurry(i duno what's it's called but it's impossibly readable).

how can i revert it back?

can i revert it using the recovery mode? the command line?..

im using the livecd atm..and need to finish some work...

thanks in advance!

---

### Post by banewman on 2008-03-25
boot into the recovery kernel and at the prompt type - 
dpkg-reconfigure xserver-xorg
and select the defaults except for the vid card driver - make sure it is the one you need - and the resolution.
:)

---

### Post by ai3gtmc on 2008-03-25
that worked! thanks!

---

### Post by Takido on 2008-03-25
i did the same thing but when i select my screen bit (24 bit) it gives me the warning of the overwrite or somthing and then goes to a new command line.

---

