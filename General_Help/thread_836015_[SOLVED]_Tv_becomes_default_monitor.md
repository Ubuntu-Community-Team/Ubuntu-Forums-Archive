---
title: "[SOLVED] Tv becomes default monitor"
date: 2008-06-21
forum: General Help
---

### Post by Joe Y-lee on 2008-06-21
My computer's monitor is an HP w2007 22" and I'm trying to setup up my new V1Z10 26" Flatscreen TV to be the second monitor. The TV has an rgb pc input so I hooked it up to my Nvidia card. Ubuntu 8.04 works fine, I can save my nvidia settings to operate smoothly with dual monitors. The only problem is that the bios and grub menu(needed for dual boot) loads up on the tv screen. 

**Edit**
     Everything works fine if you accept the fact that you can only access grub and bios through the tv.

---

### Post by hal8000 on 2008-06-21
> **Joe Y-lee said:**
> My computer's monitor is an HP w2007 and I'm trying to setup up my new V1Z10 26" Flatscreen TV to be the second monitor. The TV has an rgb pc input so I hooked it up to my Nvidia card. Upon restart, everything loaded up to the tv and the monitor stayed off. Ubuntu worked fine on the tv and I could make my monitor work by configuring my Nvidia X server settings, however the computer recognizes the tv as the default monitor for some reason.
Could anyone tell me how to change that? Thanks.

Only having a single monitor its difficult to answer. But you're in the right place with Nvidia X server settings.
Go to X server display configuration, you'll probably have two displays there, you may be able to drag them or swap positions, then make sure you save the X configuration file. Hopefully youll get a more exact answer but that should give you a start.
Another way is simply unplug the TV display at your computer until it is needed.

---

### Post by Joe Y-lee on 2008-06-21
Well I've tried that already and set ubuntu up recognize which is default. If I restart the computer though it resets itself and the tv is used as the main monitor(in other words bios and everything boots up on the tv). I think that the bios needs to recognize my hp monitor as the default but can't figure out how to do it.

---

### Post by tom66 on 2008-06-21
If you want to use the normal monitor, just ensure that the TV is not plugged in on BIOS startup, unplug it before rebooting.

---

### Post by Joe Y-lee on 2008-06-21
Although your advice is appreciated, I'm looking for a convenient way to put both my monitor and my tv to use with my computer. Plugging and unplugging cords works for the moment but it isn't the best possible outcome.

---

