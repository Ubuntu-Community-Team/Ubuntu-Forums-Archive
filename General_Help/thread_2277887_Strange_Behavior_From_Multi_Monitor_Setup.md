---
title: "Strange Behavior From Multi Monitor Setup"
date: 2015-05-12
forum: General Help
---

### Post by scienceman91 on 2015-05-12
Ok so I haven't used Ubuntu in years (pre Unity days) and I switched back to it recently, didn't care for Unity so I installed XFCE. 
It's typical that I get odd behavior from my setup seeing as I have 4 monitors in such an odd layout
[IMG]http://imgur.com/LTpiCL5[/IMG]

The problem that I am having is every time I reboot (or the X server restarts) all my monitor configuration is reset to something horribly unusable (overlapping regions 2 of them are mirrored, all of them are out of order). And I have to start nvidia-settings and fix it every single time. For some reason the changes made by nvidia settings don't stick even when I set it as a startup command to load the configuration.

Furthermore it is impossible to use the display settings from the xfce settings panel, every time I change the position of one monitor all of them change at once, and a random one becomes mirrored, it looks like it either can't handle 4 monitors, or it gets confused because 2 monitors have the same name.

Also can we please avoid non-productive discussion, telling me to use unity, get 4 of the same monitors, or go back to OpenSuse is not a solution.

Ubuntu 14.04.2 LTS, everything up to date.

---

### Post by dino99 on 2015-05-12
you probably should get less troubles with gnome-shell

---

