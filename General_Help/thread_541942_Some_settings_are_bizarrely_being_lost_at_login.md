---
title: "Some settings are bizarrely being lost at login"
date: 2007-09-03
forum: General Help
---

### Post by darsu on 2007-09-03
System: 6.10, Openbox, KDM, Nvidia driver installed via Envy.

My mouse sensitivity settings and monitor refresh rate are reset at each login.

First, the refresh rate. I addressed this bit before a few months back, but only got incredulous remarks. I've set my monitor at 1280x1024x85Hz. At startup, up to the KDM login screen, everything is fine. When I log on, there's a mode switch (I can follow it in real time from the config menu of my monitor) and I end up at 60Hz. I have to manually change it back via nvidia-settings. While in that program, if I save the settings to xorg.conf, my keyboard layout resets to what I presume is US, and even then the next time I logon the refresh rate will *again* reset from 85 at the KDM login screen to 60 when I enter the desktop.

I had assumed it's some elusive thing with the nvidia suite, and bit the bullet and readjusted the settings after every logon. But now I just bought a new mouse, and something similar is happening. The new mouse is much more sensitive than my old one, and I had to set the mouse acceleration from x2.0 to x1.0 in kcontrol. That change *does not stick*. Every time I log on, the mouse acceleration jumps to what I believe is x2.0. When I go to kcontrol to fix it, it's erroneously still shown as x1.0; if I set it to 2.0, apply changes, then set it to 1.0 and apply changes *again*, the acceleration is right. This is exactly like what it takes to fix my keyboard layout if I save xorg.conf in nvidia-settings. 

What could *possibly* be wrong with my system? It seems like there are mismatches between actual configuration settings and what the configuration tools show, and changed configuration values somewhere are either being reset or not saved permanently in the first place.

---

