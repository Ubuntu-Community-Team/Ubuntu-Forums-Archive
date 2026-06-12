---
title: "Laptop lid close behavior changes after kernel update"
date: 2019-04-04
forum: General Help
---

### Post by cbraxton on 2019-04-04
I'm running Lubuntu 18.04 on an old Acer TravelMate 4670, a Centrino-based laptop of about 2005 vintage. The CPU is 32-bit only. With 2GB memory and a small SSD Lubuntu actually runs quite well on it.

Power management is configured so that when the laptop is plugged into the mains the screen just turns off when the lid is closed. (No suspend.) This has worked fine with kernels up to 4.15.0-46.

However, today the kernel was updated to 4.15.0-47 after which when the lid was closed the laptop appeared to suspend rather than merely blank the screen, and the display did not come back upon waking up. (The backlight would turn on but no image. Sometimes just the mouse pointer would display, sometimes nothing.) It was necessary to force the laptop off to regain control.

I double-checked power management settings and they have not changed. The desired lid-closing action returns when booting up on the previous kernel, 4.15.0-46. So for now I've uninstalled the new kernel and locked it to version 4.15.0-46 in Synaptic. Is this a bug or a feature? Any workarounds other than sticking with the earlier kernel?

---

### Post by fliewatuet on 2019-04-14
I think this version of the kernel is buggy. I noticed also strange behavior with this version.

For me the suspend does not work correctly. My 18.04 (mate flavor) wakes up on its own,
after I suspended it. Sometimes after some minutes, sometimes after some hours.

When booting 4.15.0-46 it works like expected.

---

