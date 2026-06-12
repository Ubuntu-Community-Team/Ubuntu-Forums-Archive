---
title: "Hardy Freezes When Unplugged and Idle"
date: 2008-06-08
forum: General Help
---

### Post by tholmesm on 2008-06-08
I'm finding that whenever I unplug my laptop Ubuntu freezes for a few seconds. My music gets stuck on the same part of the song, the keyboard/mouse don't respond for a few seconds wifi drops. In my system logs it shows the adapter being reset. 

Once the freeze passes, the same thing will happen if the mouse is idle for a period of time (about 30 seconds). It will freeze up again, until I start moving the mouse. If the laptop is plugged in there is no freezing. If it is unplugged and the lid is closed, there is no freezing.

I am running 8.04, Dell Inspiron 6000, 1GB ram, 1.73 Centrino, Intel 2300 wireless card, ATI x300 radeon (binary drivers).

Any thoughts? Thanks in advance!

---

### Post by tom66 on 2008-06-08
Try disabling the dimming of the display, it sounds like Ubuntu is trying to dim the display but the hardware is getting confused (maybe it doesn't support it)

In System > Preferences > Power Mananagement
 * Uncheck all 'Dim display when idle checkboxes'
 * Uncheck 'Reduce backlight brightness'

Also, see if dimming the display using the keyboard (Fn + Down Arrow, Fn + Up Arrow on my computer) does the same thing.

---

### Post by tholmesm on 2008-06-08
Awesome that's exactly what it was!

Now the obvious question, any idea how to fix it? Every time I adjust the brightness its obvious that that is the problem ...

---

