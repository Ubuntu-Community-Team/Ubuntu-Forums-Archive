---
title: "[SOLVED] Xubuntu Touchpad"
date: 2008-02-19
forum: General Help
---

### Post by Segismundo on 2008-02-19
Hi,

I'm new to Linux, and have a Toshiba 2400 series laptop running Xubuntu. Its pretty snazzy, but there is a problem I am having with my touchpad. Originally it worked fine. Sometime on the 2nd day of use I couldn't move the cursor after starting up... I reinstalled the drivers and it is enabled it with gysnaptics.  Any ideas?
Here is how my xorg.conf looks:
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option		"SHMConfig"		"true"
EndSection

Thanks for checking it out.

---

### Post by Segismundo on 2008-02-20
Ok, what I posted above isn't such a big problem anymore. I decided to boot from the live cd and see if the touchpad worked (it did) and then view and configurations to see if I could change them to get it to work.  The live cd loaded the kernel, but Xubuntu (7.1 what I installed) was unable to completely load. I shut it off, and tried again and after the "Loading Linux Kernel" dialog box all I end up with is a blinking cursor in the upper left hand corner of the monitor. I tried loading Ubuntu (7.1), which ended up in the same place.  Next I am thinking of trying Puppy to see if it will load.

Does anyone know what happened? Need more info?

Thanks in advance.

---

### Post by Segismundo on 2008-02-26
Settled on bad hard disk, replaced and reinstalled. No problems.

---

