---
title: "How to disable middle mouse button paste"
date: 2007-05-03
forum: General Help
---

### Post by fiestaforever on 2007-05-03
I know this is a standard in Linux, but I've always found the middle mouse button paste functionality (where you select some text and paste the selection by pressing the middle mouse button) confusing.

Plus, it interferes with the middle mouse button plus trackpoint scrolling on my thinkpad. 
Every so often when I want to scroll, I inadvertedly paste something.

Is there any way to get completely rid of middle mouse button paste?
*(Edit: I know that you can do that in Firefox; I want it system-wide, therefore I wrote "completely".)*

TIA
Alex

*Edit (2): Sorry, just noticed that this has already been asked before: [http://ubuntuforums.org/showthread.php?p=336190](http://ubuntuforums.org/showthread.php?p=336190). But no solution yet.*

---

### Post by 50words on 2007-05-03
Oh man, I want to know this! It drives me crazy every time I try to scroll with the pointing stick.

---

### Post by fiestaforever on 2007-05-03
Meanwhile, I came across [this page]("http://learn.clemsonlinux.org/wiki/Laptops:IBM_Thinkpad_R31#Mouse") which seems to indicate that you can use the middle button as "scroll toggle" instead of paste button (and use left and right mouse buttons together for paste). 
I couldn't, however, make much sense of the xorg.conf file there, and when I tried to paste it into mine, all I got was messed-up system.
No idea how this differs from the standard  method to enable scrolling w/ middle button and trackpoint, which leaves the paste functionality intact (unfortunately).

---

### Post by 50words on 2007-05-03
That was what I needed. Look for this section in your xorg.conf (line 50 in mine):

```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

```

Add these two lines to the section:

```

	Option		"EmulateWheelButton"	"2"
	Option		"EmulateWheel" "true"

```

I'm not sure which one of those moved my paste to pushing both buttons. I'm just happy to have my scrolling back. And since it is nearly impossible to push both buttons at the same time, I'm not likely to notice.

---

### Post by fiestaforever on 2007-05-03
This is exactly how my xorg.conf file looks. AFAIK the "Emulate3Buttons" options lets left and right button act together as middle button. 

But the middle button still acts as a paste button (and additionally lets you scroll w/ the trackpoint while you hold the middle button) 

The emphasis of the original post, however, was how to make the middle button stop working as a paste button, because mixing both functions of the button is too error-prone for me.

---

### Post by 50words on 2007-06-08
So now we know how to enable scrolling, but does anyone know how to disable the paste function on the middle button?

---

### Post by Rob_Frohne on 2007-08-12
Hi,

I have a three button Microsoft Intellimouse, and I kept accidently pasting things in the source code I was browsing, which is a major pain.  I had to get rid of the Emulate3Button stuff, and then remap the buttons with ButtonMapping.  

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"ZAxisMapping"	"4 5"
#	Option		"Emulate3Buttons"
#	Option 		"Emulate3Timeout" "50"
#	Option		"EmulateWheelButton"	"2"
	Option		"ButtonMapping" "1 9 3 4 5 6 7 8 2"
#	Option		"EmulateWheel" "true"
EndSection

I also found some useful reading here:

[http://hanzubon.jp/mirrors/xorg/sources/X11R6.9.0/doc/html/mouse.4.html#toc](http://hanzubon.jp/mirrors/xorg/sources/X11R6.9.0/doc/html/mouse.4.html#toc)

Hope this helps someone else!

Rob

---

### Post by tzulberti on 2007-08-20
Thanks, that worked for me...

---

### Post by esaym on 2008-03-08
> **Rob_Frohne said:**
> Hi,

I have a three button Microsoft Intellimouse, and I kept accidently pasting things in the source code I was browsing, which is a major pain.  I had to get rid of the Emulate3Button stuff, and then remap the buttons with ButtonMapping.  

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"ZAxisMapping"	"4 5"
#	Option		"Emulate3Buttons"
#	Option 		"Emulate3Timeout" "50"
#	Option		"EmulateWheelButton"	"2"
	Option		"ButtonMapping" "1 9 3 4 5 6 7 8 2"
#	Option		"EmulateWheel" "true"
EndSection

I also found some useful reading here:

[http://hanzubon.jp/mirrors/xorg/sources/X11R6.9.0/doc/html/mouse.4.html#toc](http://hanzubon.jp/mirrors/xorg/sources/X11R6.9.0/doc/html/mouse.4.html#toc)

Hope this helps someone else!

Rob


A quick way to disable the middle mouse button is to turn it into a regular left click button with:

	Option		"ZAxisMapping"	"4 5"
	Option		"ButtonMapping" "1 1 3 4 5"

Left button normally = #1, middle is 2, right is 3, scroll up and down are 4 and 5.

---

### Post by maniaq on 2008-04-10
HALLELUJAH!

remapping to left click! why didn't I think of that?

that just made my day....

:)

---

