---
title: "can i get synaptic touchpad to emulate OSX?"
date: 2007-01-28
forum: General Help
---

### Post by Choad on 2007-01-28
in osx if you double tap to drag a window, you can let go and then tap again quickly and it keeps on dragging.

i like this

:)

i have looked through google but cant find anything

---

### Post by Jussi01 on 2007-01-28
I'd like this too. anyone know?

---

### Post by Choad on 2007-01-29
bump....

---

### Post by Scheater5 on 2007-01-29
Sounds like something to do with the calibration and the sensitivity to me - that is, the touchpad on OSX is by default less sensitive than in Ubuntu.  I'm afraid I'm neither familiar with this feature in OSX nor how to emulate it with Ubuntu, but perhaps knowing that will aid your search.

---

### Post by fragos on 2007-01-29
If I'm not mistaken, you can adjust touch pad sensitivity with the mouse configuration settings.

---

### Post by Choad on 2007-01-30
im pretty sure its not sensitivity 

for example, to drag a window accros the length of the screen on to another workspace, you might end up running out of space on the touchpad.

by default, you just hold your finger at the edge and it (very) slowly carries on moving in that direction

in osX however, it doesnt do this. instead you can let go of the touchpad, then touch your finger back on it at the other end  of the touchpad and the window will still be grabbed. you have to leave the touchpad alone for about a second for the window to finally drop.

it takes a bit of getting used to but in just a day of using my friends mac it was the one thing i really liked about it.

---

### Post by fragos on 2007-01-30
Now I understand what you mean.  I haven't had a touch pad in a while.  Mine was an external one for use with a desktop.  If I told the system it was a conventional mouse I found the pad more comfortable to use.  As a mouse, the buttons are required to do anything other than move the cursor.  Never used OSX but its delay to allow additive strokes to move the cursor sounds interesting.

---

### Post by rsotam on 2008-02-04
Hi,

You can add and set the option "LockedDrags".
This is my section "InputDevice":

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option		"SHMConfig"	"on"
	Option		"LockedDrags"	"on"
EndSection

Good luck!

---

