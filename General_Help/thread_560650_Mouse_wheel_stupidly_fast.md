---
title: "Mouse wheel stupidly fast"
date: 2007-09-26
forum: General Help
---

### Post by MobiusNZ on 2007-09-26
I have a usb wireless desktop, and i previously had it plugged into a ps/2 kvm via an adapter. Now I have a usb kvm, and have the wireless desktop plugged straight into that. Things work fine, except the mouse wheel is waaaaaaaaaaaay to sensitive. How can I change this??

---

### Post by Skerit on 2007-09-26
Well, it *can* be changed, I can tell you this..

Are you familiar with the xorg.conf file? (In /etc/X11/xorg.conf )

I think I'm going to hell if I should point a new user to such a file :P 

Anyway, 

find a region that has information about the mouse, it should look like this (the region before that would be called "generic keyboard")

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Now, to adjust the speed, try adding these settings (just after the "emulate"buttons" line, before the "endSection" line)

        Option          "MinSpeed"              "0.06"
        Option          "MaxSpeed"              "0.12"
        Option          "AccelFactor"           "0.0010"

I don't know what these paramters should be, though, that'll be a bit of a hunt for you. and, unfortunately, you'll have to restart X to try them out (Ctrl-alt-backspace)

---

### Post by strabes on 2007-09-26
Make sure you save the file before you restart X.

---

### Post by MobiusNZ on 2007-09-29
I am reasonably familiar with xorg.conf, but you may be mis-understanding what I'm after. The normal mouse speed is fine, its just the wheel. Its one of those smooth-rolling ones that doesn't have fixed scroll steps... kinda hard to explain... there's no resistance when scrolling like there is on most mice... 
anyway, its way too sensitive... I need to somehow increase the distance between each scroll point... or something? ](*,)

---

