---
title: "Forward and Back Buttons on a 4 button Trackball"
date: 2008-06-21
forum: General Help
---

### Post by rizlmilk on 2008-06-21
If you'd like to skip my long winded explanation, I have a four button trackball, and the back and forward buttons don't work properly...I would like to fix this. If you would like the back story, read on.

I'm currently introducing Ubuntu and Linux to my family. I've temporarily replaced the family computer with another computer with a fresh install of Hardy. The whole family likes using trackballs over mouses, but the "forward" and "back" buttons on our trackball don't function the way they should. The "back" button doesn't do anything, while the "forward" button acts like a right click.

I know I will most likely have to edit the xorg.conf file, but I can't find a decent explanation of the different options of the Input Device section. Every tutorial just tells you what to do, not what is being done, not to mention the majority of tutorials are for 5 buttons.

As I said earlier, it is a four button mouse. There is no scroll wheel, just four buttons and the trackball.

If it helps, here is the current mouse section of my xorg.conf file:
> Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Any help is appreciated, as this is the first time I am attempting to convert anyone to Linux (or at least letting them experience it).

---

