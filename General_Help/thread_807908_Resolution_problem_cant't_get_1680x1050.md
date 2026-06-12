---
title: "Resolution problem: cant't get 1680x1050"
date: 2008-05-26
forum: General Help
---

### Post by kabuchin on 2008-05-26
Hi all, i can't get 1680x1050 on my monitor. My settings are:
nvidia 8800gts, ViewSonic 2035wm (1680x1050 native).
On a fresh ubuntu 8.04 install, the first screen says my monitor couldn't be detected. I choose generic 1680x1050 flat panel, and on restart, a frequency problem is present (i can't see anything but lines, classic frequency error). The only way i can get to desktop is to do a 

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

and set a flat panel 1024x768 monitor.
I installed envy, same problem. I changed the xorg.conf settings, adding manually the native resolution, but nothing i do seems to work. 
I've searched for different modeline and screen settings, but no luck yet.
Any help? Thanks.

---

### Post by kabuchin on 2008-05-27
Update: i've been able to fix it, first I deleted the xorg.conf, shut down, connect the monitor through vga analog cable (was connected via dvi cable) and power on.
It booted up with native 1680x1050 resolution, I installed envy, restarted, and no screen was found again. I selected the default 1680x1050 lcd panel, restart and then the frequency problem. I restarted in recovery mode, edited the xorg.conf file (changed the settings for frequency to match my monitor's) restarted, and finally It worked.

---

