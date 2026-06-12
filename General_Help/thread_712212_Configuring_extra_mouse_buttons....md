---
title: "Configuring extra mouse buttons..."
date: 2008-03-01
forum: General Help
---

### Post by Hoborg on 2008-03-01
Hey I am using Ubuntu 7.10 together with a mouse with some extra buttons, (next, previous) and Ubuntu doesn't recognize them. in the Ubuntu documentation I found that it could be solved by adding the extra number on buttons in this file: /etc/X11/xorg.conf 

The documentation says I should change Option "Buttons" "5" to Option "Buttons" "7"
this is the mouse section of the file: 

Section "InputDevice"

Identifier	"Configured Mouse"
Driver		"mouse"
Option		"CorePointer"
Option		"Device"	"/dev/input/mice"
Option		"Protocol"	"ImPS/2"
Option		"ZAxisMapping"	"4 5"
Option		"Emulate3Buttons"	"true"
EndSection


the Buttons option isn't there! what to do?

---

### Post by Distro Jockey on 2008-03-01
> **Hoborg said:**
> Hey I am using Ubuntu 7.10 together with a mouse with some extra buttons, (next, previous) and Ubuntu doesn't recognize them. in the Ubuntu documentation I found that it could be solved by adding the extra number on buttons in this file: /etc/X11/xorg.conf 

The documentation says I should change Option "Buttons" "5" to Option "Buttons" "7"
this is the mouse section of the file: 

Section "InputDevice"

Identifier	"Configured Mouse"
Driver		"mouse"
Option		"CorePointer"
Option		"Device"	"/dev/input/mice"
[B]Option		"Protocol"	"ImPS/2"
Option		"ZAxisMapping"	"4 5"
Option		"Emulate3Buttons"	"true"[/B]
EndSection


the Buttons option isn't there! what to do?

Make your section of /etc/X11/xorg.conf look like the following and then restart X and the back and forward buttons should work in Firefox.

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
[B]Option "Protocol" "ExplorerPS/2"
Option "Buttons" "7"
Option "ZAxisMapping" "4 5"
Option "ButtonMapping" "1 2 3 6 7"[/B]
EndSection

---

### Post by fjgaude on 2008-03-01
If that doesn't work correctly, try this:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"Emulate3Buttons"	"false"
	Option		"Buttons"	"7"
	Option		"ZAxisMapping"	"4 5"
	Option		"ButtonMapping"	"1 2 3 6 7 4 5"
EndSection
```

---

### Post by Semprini on 2008-03-11
> **Distro Jockey said:**
> Make your section of /etc/X11/xorg.conf look like the following and then restart X and the back and forward buttons should work in Firefox.

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
[B]Option "Protocol" "ExplorerPS/2"
Option "Buttons" "7"
Option "ZAxisMapping" "4 5"
Option "ButtonMapping" "1 2 3 6 7"[/B]
EndSection

Just to say that I was having a bit of trouble with this, but after some tweaking, I got it to work.

I'm using a Microsoft Intellimouse, and to get it work right, I had to change a couple of lines to the following:
> Option "ZAxisMapping" "6 7"
Option "ButtonMapping" "1 2 3 4 5"
So try that if you're having problems. Other than that, the advice above was a great help. Cheers!

---

### Post by agibby5 on 2008-04-24
Anyone having any issues with this in Hardy?

---

### Post by Naegling23 on 2008-04-25
hey guys, I had this working for some time now.  Just upgraded to Hardy, and my mouse is no longer working.  Some other posts suggest going back to the three button mouse to get it working....so, how do we get all the buttons working in Hardy?

---

### Post by jeremy on 2008-04-25
> **agibby5 said:**
> Anyone having any issues with this in Hardy?

I have issues, documented at [http://ubuntuforums.org/showthread.php?t=758387](http://ubuntuforums.org/showthread.php?t=758387)

---

### Post by soelk on 2008-04-25
I have a Logitech MX700. Works in Firefox with this modification. But it doesn't work in nautilus (or at least I don't know how to make it work).

Option "ButtonMapping" "1 2 3 8 9"

Basically, what happened is that the Firefox team did a design choice for FF3 to use buttons 8/9 for back/forward and 6/7 for side scrolling.

---

