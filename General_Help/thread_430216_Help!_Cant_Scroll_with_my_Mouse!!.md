---
title: "Help! Cant Scroll with my Mouse!!"
date: 2007-05-01
forum: General Help
---

### Post by E87 on 2007-05-01
Hi guys! Im having trouble with my mouse scolling
I have a regular 3 button mouse a optical bluetooth Rocketfish Mouse&Keyboard 
and here is my info:


Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option

Any help is extremely appreciated! Thanks		"Protocol"		"IMPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

---

### Post by sandman55 on 2007-05-01
Hi [This](http://ubuntuforums.org/showthread.php?t=219894) did the trick with my logitec MX500 I dont know how it will go with your mouse so be sure to backup and document what you do so that you can back track what I did in my xorg.conf is not delete any thing just put a # infront of it then it is not treated as script just text

---

