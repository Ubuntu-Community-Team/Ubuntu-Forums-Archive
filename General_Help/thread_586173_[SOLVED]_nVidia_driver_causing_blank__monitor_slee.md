---
title: "[SOLVED] nVidia driver causing blank / monitor sleep on login, HELP!"
date: 2007-10-22
forum: General Help
---

### Post by mfarley on 2007-10-22
After browsing through the forums for the past two hours I have seen multiple posts describing my problem:

nv driver / initial setup works great, you're in!

Then once you enable the restricted nVidia drivers, either through the manager, or installing them yourself, you get:

GDM loads, but your monitor goes to sleep!  You can hear the sound effects.  You can even type your user name and password, and hear the sound of your desktop loading, but alas, your monitor is still asleep.

Many users are experiencing this and trying everything from changing refresh rates to changing monitors.  We've all reinstalled the drivers several times.

I'm beginning to think it's an issue with Gusty's kernel.

Has anyone made headway on this??

Thanks!

---

### Post by svasie on 2007-10-22
Put this line in "Device" section in "/etc/X11/xorg.conf":

[FONT="Courier New"]Option          "UseDisplayDevice"      "CRT"[/FONT]

---

### Post by mfarley on 2007-10-22
> **svasie said:**
> Put this line in "Device" section in "/etc/X11/xorg.conf":

[FONT="Courier New"]Option          "UseDisplayDevice"      "CRT"[/FONT]


Even if I have an LCD?  (2405fpw) ?

---

### Post by mfarley on 2007-10-23
> **mfarley said:**
> Even if I have an LCD?  (2405fpw) ?

Ha, it worked using "DFP" instead of "CRT"

Thanks!!

---

