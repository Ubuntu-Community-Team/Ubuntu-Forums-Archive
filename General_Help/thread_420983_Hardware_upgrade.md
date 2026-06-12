---
title: "Hardware upgrade"
date: 2007-04-24
forum: General Help
---

### Post by calagan on 2007-04-24
I just got a second-hand PC (a P4 1.7) from the office that's slightly more powerful than my current PIII 866, which runs Dapper for LAMP and Squid. I was wondering if there's an easy way to migrate to the new machine by moving the HDD to the new machine and launch some kind of hardware detection to adapt to the new machine, so that I wouldn't have to reinstall everything from scratch.

Thank you in advance.

Calagan

---

### Post by kscott121 on 2007-08-29
I just did this exercise (moving an "installed" harddrive to a different machine).  Since the graphics cards differed the new system booted but the graphics was horrible and unusable. I did CTRL+ALT+ F4 to go to a login prompt , ran Xorg -reconfigure [this forces an Xorg redetection], copied the resultantly newly generated xorg.conf from my home directory to /etc/X11/xorg.conf [so it wouls be used] and rebooted (now with ok graphics). Yeah@!!

Anyways, sound and networking were detected automatically.
May your luck be both good and frequent.
Ken

---

