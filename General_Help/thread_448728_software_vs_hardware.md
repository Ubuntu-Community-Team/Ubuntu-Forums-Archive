---
title: "software vs hardware"
date: 2007-05-19
forum: General Help
---

### Post by SnowLinux on 2007-05-19
I've installed Edubuntu 7.04 on my PC
which is  750mhz Barton CPU,  512mb SDRam, onboard LAN & 32MB graphics
and I've given / partition 6.5Gig of space.
I'm getting very slow boots, the progress bar starts then stops at the LHS for a few minutes before continuing to boot. When booted everything seems good, even the speed for the spec of my PC.

I pressed CTRL+ALT+F1 on booting and the screen is displaying stuff like

ata1.00: exception ........ a load of zeros and numbers then comments that its frozen
then the very next line is
ata1.00: cmd

anyone got an idea on this please?

By the way, is there a GUI type app for HDD partition admin available for the Ubuntu familiy  ?

---

### Post by earobinson on 2007-05-19
the program is gparted ```
sudo apt-get install gparted
``` to install it.

---

