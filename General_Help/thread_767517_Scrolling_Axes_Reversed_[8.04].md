---
title: "Scrolling Axes Reversed [8.04]"
date: 2008-04-25
forum: General Help
---

### Post by thesalus on 2008-04-25
I just upgraded to Hardy Heron, and much to my delight, found that the Side buttons on my Logitech Mx518 mouse work as they should. The only problem being that the scrollwheel on the mouse as well as the two scrolling strips on my touchpad (Inspiron 640m) are confused. The scrollwheel/vertical strip now scroll horizontally and the horizontal strip scrolls vertically. And I simply can't normalize it.

As it stands, my xorg.conf says:
> Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Tampering with InvX, InvY, HorizEdgeScroll and VertEdgeScroll doesn't seem to change any of it. (nor playing with the ZAxisMapping)

Could anyone offer up any suggestions?

Edit: What a simple solution it turned out to be.
I edited a line in /home/login/mouse which was initially:
> exec xmodmap -e "pointer = 1 2 3 6 7 4 5" &
into:
> exec xmodmap -e "pointer = 1 2 3 4 5 6 7" &

---

