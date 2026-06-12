---
title: "can't click with mouse wheel after feisty upgrade"
date: 2007-04-22
forum: General Help
---

### Post by patcito on 2007-04-22
Hey all,

I've just upgraded to feisty, my mouse used to work perfectly on edgy but now I can't use the wheel to open tabs on firefox or to paste text. I can still scroll though. I have a USB Genius Optical. 
This is my config:

```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection


```

I also tried with ExplorerPS/2  and several other options but it didn't improve the situation :/

Any idea how to fix this?

Thanx in advance

Pat

---

### Post by BoneKracker on 2007-04-22
That's what I have and mine's working.

For the ZAxisMapping, try "4 5 6 7"

---

### Post by BoneKracker on 2007-04-22
I think the wheel functions that you describe failing are the mouse button 3.

The scrolling, which seems to be working, is governed by the ZAxisMapping.  You have these set to 4 and 5 which is correct for a mouse with two regular buttons plus a wheel.

If your mouse has more buttons that two plus the wheel, you might want to research xmodmap

---

### Post by dvord on 2007-04-22
Well this is what mine has.  Now I don't get the scroll wheel click to work, but I do get two extra buttons on my mouse to work which conform automatically in Firefox to Forward and Back buttons in the browser:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"Buttons"	"7"
	Option		"ZAxisMapping"	"4 5"
	Option		"ButtonMapping"	"1 2 3 6 7"
	Option		"Emulate3Buttons"	"true"
EndSection

The mouse I'm using is a Logitech MX518 USB.

---

### Post by BoneKracker on 2007-04-22
Well, yeah.  The scroll doesn't work because you told it that buttons 4 5 are scroll but you also told it there are no buttons 4 5.

See what happens when you change 

```
Option "ButtonMapping" "1 2 3 6 7"

```
to 

```
Option "ButtonMapping" "1 2 3 6 7 4 5"
```

Hopefully that will give you all your buttons plus the scroll wheel.

---

### Post by kerry_s on 2007-04-22
It's the feisty kernel, i lost several older mice on several machines. I also have one that's doing the same as yours, i'm using the left+right click for the middle click but that sucks. I've been replacing the 1's that don't work with other mouses, but don't have enough to go around. :(  I'm picking up more mice from a friend later hopefully some of those will work. I'm even using shift+alt+num lock and using the number keys to move the mouse on 1 system that the mouse don't work at all, you can imagine how slow that is :)

---

### Post by kerry_s on 2007-04-22
Just in case someone else gets stuck with a non working mouse in the gui, i thought i would give a run down on the mouse control keys.

shift+alt+num lock <- to activate/disable keybord mouse control, you'll hear a beep when you activate/disable.
/ = actvate left click
* = actvate middle click
- = activate right click
5 = uses key you choose with /, *, -
7 = left up
8 = up
9 = right up
4 = left
6 = right
1 = left down
2 = down
3 = right down
0 = lock drag
. = release lock drag
+ = double click


Hope that helps someone when there mouse loses function or they just prefer to use the keyboard.

---

### Post by patcito on 2007-04-22
> **kerry_s said:**
> It's the feisty kernel, i lost several older mice on several machines. I also have one that's doing the same as yours, i'm using the left+right click for the middle click but that sucks. I've been replacing the 1's that don't work with other mouses, but don't have enough to go around. :(  I'm picking up more mice from a friend later hopefully some of those will work. I'm even using shift+alt+num lock and using the number keys to move the mouse on 1 system that the mouse don't work at all, you can imagine how slow that is :)


is there any chance to get my middle click back by compiling my own kernel? I don't have any other mouse here :/

---

### Post by patcito on 2007-04-22
> **BoneKracker said:**
> I think the wheel functions that you describe failing are the mouse button 3.

The scrolling, which seems to be working, is governed by the ZAxisMapping.  You have these set to 4 and 5 which is correct for a mouse with two regular buttons plus a wheel.

If your mouse has more buttons that two plus the wheel, you might want to research xmodmap

I only have two buttons and the wheel, I tried with 1 2 3 4 5 6  7 and 4 5 6 7 but it didn't change nothing which is normal  as I only have 2 buttons. Any idea how to fix this?

---

### Post by kerry_s on 2007-04-22
> **patcito said:**
> is there any chance to get my middle click back by compiling my own kernel? I don't have any other mouse here :/

I would suggest rather than compiling, try adding the edgy repos grab the edgy kernel and use that. 

```
deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted multiverse universe 
```

i didn't try it myself, like i said it was easy to just replace the mouse. If that don't work then you can try compiling your own, but i don't know what setting you need to set to get the mouse to work.

You can also just live with it for know, till you get another mouse, just turn the keyboard mouse control(shift+alt+mun lock) on and press the * button, then when you need middle click just press 5 and use the parts of the mouse that work for the rest or just use the old fashion 2 button mouse way press left+right click at the same time.

---

