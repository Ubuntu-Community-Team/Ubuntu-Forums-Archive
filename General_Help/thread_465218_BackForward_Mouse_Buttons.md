---
title: "Back/Forward Mouse Buttons"
date: 2007-06-05
forum: General Help
---

### Post by Andrewz on 2007-06-05
Hi, was wondering if anyone knew how to get the back/forward side buttons on my mouse to work with firefox in ubuntu, they work okay for me with XP but for some reason they don't work in ubuntu, maybe they just need to be set up? Thanks in advance.:p

---

### Post by Irti on 2007-06-05
same prob here bro...cant figure out wuts wrong....am gonna try puttin the cd they gave me with the mouse...bt i doubt if it will run...coz the cd was meant for xp...i think     lets c

---

### Post by NT4usB on 2007-06-05
Been a bunch of posts here over the years on how to do it.
Search stuff like ButtonMapping and you'll find them.

---

### Post by Andrewz on 2007-06-05
Okay I searched and think I found what I need to do, they all talk about editing the xorg.conf, how do I access that, sorry if its a really dumb question I'm very new to this.

---

### Post by RedSquirrel on 2007-06-05
> **Andrewz said:**
> Okay I searched and think I found what I need to do, they all talk about editing the xorg.conf, how do I access that, sorry if its a really dumb question I'm very new to this.

Open a terminal. Applications -> Accessories -> Terminal

Make a backup copy of xorg.conf just to be on the safe side:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

Then, to edit the file:

```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by Andrewz on 2007-06-05
Thank you red.

So this is what I have right now,

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

I'm using a Logitech MX600 Mouse, just trying to make it so the side back/forward buttons work with firefox, any suggestions as to what needs to be changed?

---

### Post by dodgePT on 2007-06-05
Try this

> Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
	Option          "Buttons" "7" 
	Option          "ButtonMapping" "1 2 3 6 7"
EndSection

---

### Post by RedSquirrel on 2007-06-05
> **Andrewz said:**
> Thank you red.

So this is what I have right now,

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"    "/dev/input/mice"
    Option        "Protocol"    "ImPS/2"
    Option        "ZAxisMapping"    "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

I'm using a Logitech MX600 Mouse, just trying to make it so the side back/forward buttons work with firefox, any suggestions as to what needs to be changed?

I'm afraid you'll have to read through some guides for that. I don't have that mouse. There are a few HOWTOs on ubuntuforums though. If you do a search for "mx600", you'll see what I mean. Good luck. :)

---

