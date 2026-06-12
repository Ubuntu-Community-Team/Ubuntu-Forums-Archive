---
title: "Mouse back&amp;forward in Nautilus"
date: 2008-03-26
forum: General Help
---

### Post by luceerose on 2008-03-26
Hey all,
I was wondering if anyone knows how to get mouse back & forward buttons working in Nautilus.

I have a Gigabyte 1600dpi Lasermouse.
I have back & forward working in Firefox by editing my xorg.conf to look like;

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"vmmouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"ButtonMapping"	"1 2 3"
	Option		"ZAxisMapping"	"4 5"
	Option		"YAxisMapping"	"6 7"
	Option		"Emulate3Buttons"	"false"
	Option		"Resolution"	"1600"
EndSection

Obviously, buttons 6 & 7 are my back & forward on YAxis.
This works perfectly in firefox, but I would really like to browse Nautilus using the same buttons for back & forward.
Anyone have any ideas ?

---

### Post by luceerose on 2008-03-27
bump

---

### Post by luceerose on 2008-03-28
anybody?

---

