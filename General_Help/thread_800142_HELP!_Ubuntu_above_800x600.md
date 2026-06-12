---
title: "HELP! Ubuntu above 800x600"
date: 2008-05-19
forum: General Help
---

### Post by SmartRoss on 2008-05-19
I am planning on tweaking some open source OpenGL Software and decided that Ubuntu Desktop 8.04LTS would be the best OS to run it on, as I require the use of Linux. When I run the program, I get an error that it cannot run in 1024x768; the minimum resolution. When I check in my settings, the highest available resolution is 800x600; my current one. Does anybody know how I can 'force' Ubuntu to run at 1024x768?

I'm emulating Ubuntu on innotek VirtualBox, which may be a problem...

---

### Post by jpeddicord on 2008-05-19
> **SmartRoss said:**
> I'm emulating Ubuntu on innotek VirtualBox, which may be a problem...

That's probably the problem... VirtualBox can't emulate real graphics drivers yet. If there is a setting to change the driver resolution in VB, use that, otherwise there isn't much of a way (I think).

Also, you will get anywhere from horrible to poor OpenGL performance in VirtualBox for the same reason above. :???:

---

### Post by SmartRoss on 2008-05-19
Do you know of any emulators which *can* emulate graphics drivers, or can at least provide a graphics emulation allowing a resolution of at least 1024x768?

---

### Post by jpeddicord on 2008-05-19
VMware Server seems to handle fair resolutions, but it's a beast of a download and even more to set up. As far as I know, only VMware Workstation properly emulates graphics drivers, but it isn't free.

---

### Post by SmartRoss on 2008-05-20
[I][COLOR="Silver"]Does VMWare Player emulate Graphics Drivers (or provide a decent resolution)?

If not, does Microsoft Virtual PC?[/COLOR][/I]

EDIT: I've managed to get VMWare Server to work perfectly! Thanks for all of the advice!

---

