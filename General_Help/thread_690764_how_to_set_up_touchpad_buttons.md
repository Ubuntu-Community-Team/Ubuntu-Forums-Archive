---
title: "how to set up touchpad buttons"
date: 2008-02-07
forum: General Help
---

### Post by verby on 2008-02-07
I have acer 5520 and did clean installation. Everything works, except touchpad buttons, actually the middle one (scroll) is really messed up. ie when I press scroll up it does scroll but down, when I press down it throws cursor somewhere else or even locks the screen and have to reboot. I did play with xorg.conf but with no success. Any ideas how to set it up?
Here is section from my xorg.conf:


Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"synaptics"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

---

### Post by verby on 2008-02-07
bump... any ideas/solutions?

---

### Post by slayer04 on 2008-02-07
try a different mouse, that will tell you if its Ubuntu's or mouse's fault or try the same mouse on a different computer. if its ubuntu's fault I can't help you more than saying play around with the control center

---

### Post by jijin on 2008-02-11
I am getting the same thing... anybody figure out the solution?

---

