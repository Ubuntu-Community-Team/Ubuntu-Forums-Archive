---
title: "[SOLVED] Reboot/Shutdown problem"
date: 2007-07-08
forum: General Help
---

### Post by MadMac on 2007-07-08
Howdy all!

I just did a new install (had a bad hard drive) and now, when I attempt to do a reboot or shutdown,  the process will hang at what seems to be the very last stage. The Ubuntu progress bar will move from the left to the right normally, but when the bar is completely empty, the system simply won't finish what it is supposed to do, which is to shutdown or reboot the system.  The second time this happened I left it for over an hour as I assumed that maybe it was just taking longer than usual, but it never did reboot.  At that point even the good-ol' ctrl-alt-del is non-functional and I have to manually power down the system by pressing the power button.

I did some searching and I did try adding "acpi force" in the menu.lst file, as was suggested in a thread I found, but that did not work.

Anyone have any ideas on this?

Thanks!

---

### Post by eggdeng on 2007-07-09
```
sudo gedit /etc/modules
```
Add the line
```
apm power_off=1
```
Save the file and reboot.

---

### Post by MadMac on 2007-07-09
> **eggdeng said:**
> ```
sudo gedit /etc/modules
```
Add the line
```
apm power_off=1
```
Save the file and reboot.

Howdy Eggdeng!

Sorry, no luck.  Even tried twice.  Still locks up instead of rebooting.

Thanks though!


Edit:  I have tried using different variations (where the code is placed, etc.), but still no luck.

---

### Post by MadMac on 2007-07-11
FIXED - Had two video cards in the system.  Took one out and, wa-la, it now reboots and shuts down, with no more lock-ups.

---

