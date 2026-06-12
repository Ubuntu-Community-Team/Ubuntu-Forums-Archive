---
title: "Right Mouse Button and Middle Click Swapped Functions"
date: 2006-10-27
forum: General Help
---

### Post by Jolly Roger on 2006-10-27
After I upgraded to Edgy during the RC phase I noticed that the clicking action of my scroll wheel and the right mouse button on my Logitech mx518 have switched functions. Middle clicking now brings up what is usually the right click menu. Right clicking now starts the autoscroll function in apps that support it. I thought this would be fixed by release time but it is still broken. Does anyone have a solution for this?

---

### Post by mssever on 2006-10-27
You can configure that in /etc/X11/xorg.conf. I don't remember the configuration option, but it must be documented somewhere. I did that years ago on my first Debian install, and have since forgotten how it's done.

---

### Post by Jolly Roger on 2006-10-27
I searched google for a way to configure the buttons but didn't come up with anything that worked. Has anyone else found a way to remap the buttons?

---

### Post by Jolly Roger on 2006-10-27
After getting XGL and Beryl up and running on my computer it seems that my swapped mouse button problem is now fixed. I have no idea why XGL or Beryl would fix the issue but I'm happy now.

---

### Post by JackandJohn on 2006-10-29
Jolly Roger: Can you post the contents of your /etc/X11/xorg.conf please?
I am sure the issue is there, but I'm not sure how to tackle it (and it's atrting to drive me mental)

the one that may be different on mine:


```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"false"
EndSection
```

Thanks, and I'll post the fix when I figure it out

---

### Post by Quite Interesting on 2006-10-29
I think I found a fix for this, it seems to work for me at any rate.

Try adding the lines:

```

	Option	    "Buttons" "9"
	Option	    "ButtonMapping" "1 3 2 8 9"

```

To your xorg.conf file in the input section. Of course if you don't have 9 buttons on your mouse you'll need to change that but the key thing is that the second and third buttons need to be swapped in the button mapping section.

It should make that section look a little bit like this
```

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "Buttons" "9"
	Option	    "ButtonMapping" "1 3 2 8 9"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "false"
EndSection

```

Hope this clears it up for you.

---

### Post by Jolly Roger on 2006-10-30
Thanks Quite Interesting! All my buttons are working perfectly now.

---

### Post by Quite Interesting on 2006-10-30
No problem, glad I could help.

---

### Post by JackandJohn on 2006-11-01
A quick note to anyone reading this in future:

Make sure that when you count the buttons on your mouse, you count any actual buttons, pluss 3 for the mouse wheel (one for press, and one each for up and down scroll)

The documentation for the "ButtonMapping" command is here:
[http://ftp.x.org/pub/X11R7.0/doc/html/mouse.4.html](http://ftp.x.org/pub/X11R7.0/doc/html/mouse.4.html)

Though; I would like to see what these numbers actually mean. 
(Are they mapped to specific functions in xorg? 
or are they application specific, and xorg just says "button X was pressed"? 
And, if there is a standard: What is it)

---

