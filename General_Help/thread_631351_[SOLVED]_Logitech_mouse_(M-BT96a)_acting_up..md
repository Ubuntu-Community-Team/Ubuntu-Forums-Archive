---
title: "[SOLVED] Logitech mouse (M-BT96a) acting up."
date: 2007-12-04
forum: General Help
---

### Post by paydaydaddy on 2007-12-04
Running Gutsy 7.10. I have a Logitech M-BT96a mouse that was working fine until yesterday (problem caused by updates?). The problem is that the scroll wheel will let me scroll down a page, but when I try to scroll back up, I get a drop down menu the same as if I had right clicked on the page. I have been searching the forums and have not found anything that I thought really addressed my particular problem. I did find some info about a different driver (evdev) for some logitech mice, but no reference to my specific model. Here is the output of xorg.conf for my mouse which I am running as PS/2:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"

Any help would be appreciated.

---

### Post by paydaydaddy on 2007-12-04
Bump

---

### Post by paydaydaddy on 2007-12-04
double bump

---

### Post by paydaydaddy on 2007-12-07
With todays software update the problem fixed itself. Odd that I didn't see anybody else talking about this, but I guess that doesn't matter as long as it works for me.

---

