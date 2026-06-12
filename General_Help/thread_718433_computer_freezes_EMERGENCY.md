---
title: "computer freezes *EMERGENCY*"
date: 2008-03-08
forum: General Help
---

### Post by crazyfuturamanoob on 2008-03-08
Most programs (scorched3d, c&c3 patch 1.09 installer) freeze the whole 
computer when trying to open them. All of those apps freezing the computer
use opengl. Even ctrl+alt+backslash doesn't work. I got this from xorg.conf:
> 
Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fi"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
	Boardname	"OpenChrome"
	Busid		"PCI:1:0:0"
	Driver		"via"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"SAMSUNG"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1360x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
	Monitor		"SAMSUNG"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection
I haven't installed or done anything to this yet.

I tried glxgears in console:
> 
arho@timo-desktop:~$ glxgears
1823 frames in 5.0 seconds = 364.454 FPS
2134 frames in 5.0 seconds = 426.615 FPS
2150 frames in 5.0 seconds = 429.811 FPS
2136 frames in 5.0 seconds = 427.143 FPS
2069 frames in 5.0 seconds = 413.737 FPS
2115 frames in 5.0 seconds = 422.816 FPS
1545 frames in 5.0 seconds = 308.897 FPS
2114 frames in 5.0 seconds = 422.716 FPS
2124 frames in 5.0 seconds = 424.678 FPS
2121 frames in 5.0 seconds = 424.071 FPS
2125 frames in 5.0 seconds = 424.877 FPS
2122 frames in 5.0 seconds = 424.328 FPS
XIO: fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
after 78367 requests (67861 known processed) with 0 events remaining.
arho@timo-desktop:~$ glxgears
1285 frames in 5.0 seconds = 256.814 FPS
1206 frames in 5.0 seconds = 241.194 FPS
1215 frames in 5.0 seconds = 242.853 FPS
1165 frames in 5.0 seconds = 232.925 FPS
1271 frames in 5.0 seconds = 254.074 FPS
1219 frames in 5.0 seconds = 243.785 FPS
1221 frames in 5.0 seconds = 244.124 FPS
XIO: fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
after 26443 requests (26358 known processed) with 0 events remaining.
arho@timo-desktop:~$


---

### Post by Jimmey on 2008-03-08
> **crazyfuturamanoob said:**
>  Even ctrl+alt+backslash doesn't work.


Did you try CTRL + ALT + **Backspace**?

What about CTRL + ALT + F1 - 9?

---

### Post by crazyfuturamanoob on 2008-03-08
> **Jimmey said:**
> Did you try CTRL + ALT + **Backspace**?

What about CTRL + ALT + F1 - 9?
I ment backspace. Im not very good at english.
Wine's notepad hard freezes my computer also.

---

### Post by Jimmey on 2008-03-08
Try launching some of these applications from the terminal, See if any error messages are output before the computer freezes.

---

### Post by crazyfuturamanoob on 2008-03-08
Doesn't work. The hard freeze happens before this.
And with wine apps, I tried winedebug. Hard freeze
came before error messages.
 
Btw, all the default games work. 
Even the 3d chess in 3d mode.
I tried glxgears too and it works 
without problems. Most games &
programs I have downloaded don't work.

Any clue what the problem could be?
This is really annoying. Thanks

---

### Post by crazyfuturamanoob on 2008-03-08
btw I just noticed mouse stops each 1 second when playing travian.
Its a java-based browser game. Posted this in case that has something
to do with hard freeze,

---

### Post by crazyfuturamanoob on 2008-04-11
[SIZE="7"]BUMP!!!![/SIZE]
Does hardy hero have this problem?

---

### Post by crazyfuturamanoob on 2008-04-18
I give up, this is the last bump. :(:(:(:(:(:(
EDIT:
I'll try those things and then I'll forget
this topic for forever.

---

### Post by andrewabc on 2008-04-18
Hardy release Candidate has been released. 
[http://www.ubuntu.com/testing/804rc](http://www.ubuntu.com/testing/804rc)

I would suggest downloading the live cd and seeing it it works. Or you can wait a week and download the final version.
Remember before installing (if you choose to install, I'd play with live cd for a while first) to backup any important data in case something goes wrong :)

---

### Post by KeyserSoze93 on 2008-04-18
does you log say anything?

"tail /var/log/messages"

I had a very similar problem and it said a load of stuff about soft resetting ata0.1,
turned out I needed a new power supply.

---

### Post by crazyfuturamanoob on 2008-04-19
>  does you log say anything?

"tail /var/log/messages"

I had a very similar problem and it said a load of stuff about soft resetting ata0.1,
turned out I needed a new power supply.

I can't check that until after a week or so,
because the other computer that doesn't 
work is in my summer cottage. I posted this
from my main computer (which works).
So please keep reading this topic once a week,
and don't loose track of this.

> Hardy release Candidate has been released.
[http://www.ubuntu.com/testing/804rc](http://www.ubuntu.com/testing/804rc)

I would suggest downloading the live cd and seeing it it works. Or you can wait a week and download the final version.
Remember before installing (if you choose to install, I'd play with live cd for a while first) to backup any important data in case something goes wrong 
I'll try the final release.

---

### Post by crazyfuturamanoob on 2008-06-17
I tried glxgears in console:
> arho@timo-desktop:~$ glxgears
1823 frames in 5.0 seconds = 364.454 FPS
2134 frames in 5.0 seconds = 426.615 FPS
2150 frames in 5.0 seconds = 429.811 FPS
2136 frames in 5.0 seconds = 427.143 FPS
2069 frames in 5.0 seconds = 413.737 FPS
2115 frames in 5.0 seconds = 422.816 FPS
1545 frames in 5.0 seconds = 308.897 FPS
2114 frames in 5.0 seconds = 422.716 FPS
2124 frames in 5.0 seconds = 424.678 FPS
2121 frames in 5.0 seconds = 424.071 FPS
2125 frames in 5.0 seconds = 424.877 FPS
2122 frames in 5.0 seconds = 424.328 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 78367 requests (67861 known processed) with 0 events remaining.
arho@timo-desktop:~$ glxgears
1285 frames in 5.0 seconds = 256.814 FPS
1206 frames in 5.0 seconds = 241.194 FPS
1215 frames in 5.0 seconds = 242.853 FPS
1165 frames in 5.0 seconds = 232.925 FPS
1271 frames in 5.0 seconds = 254.074 FPS
1219 frames in 5.0 seconds = 243.785 FPS
1221 frames in 5.0 seconds = 244.124 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 26443 requests (26358 known processed) with 0 events remaining.
arho@timo-desktop:~$ 

Looks like a fork bomb -like problem, right?
The framerate reduced A LOT in the second test.
Maybe this is the key of the problem?

Edit:
Btw I'm using Hardy Heron 8.04.
Here's another test:
> arho@timo-desktop:~$ glxgears
2133 frames in 5.0 seconds = 426.420 FPS
2148 frames in 5.0 seconds = 429.433 FPS
1741 frames in 5.0 seconds = 348.109 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 18613 requests (18565 known processed) with 0 events remaining.
arho@timo-desktop:~$ glxgears
2144 frames in 5.0 seconds = 428.622 FPS
2167 frames in 5.0 seconds = 433.266 FPS
1913 frames in 5.0 seconds = 382.508 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 19217 requests (18979 known processed) with 0 events remaining.
arho@timo-desktop:~$ glxgears
2178 frames in 5.0 seconds = 435.466 FPS
2169 frames in 5.0 seconds = 433.648 FPS
1760 frames in 5.0 seconds = 351.981 FPS
1200 frames in 5.0 seconds = 239.907 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 22669 requests (22597 known processed) with 0 events remaining.
arho@timo-desktop:~$ glxgears
2138 frames in 5.0 seconds = 427.580 FPS
2173 frames in 5.0 seconds = 434.547 FPS
2188 frames in 5.0 seconds = 437.596 FPS
2180 frames in 5.0 seconds = 435.872 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 27587 requests (35 known processed) with 0 events remaining.
arho@timo-desktop:~$ glxgears
2080 frames in 5.0 seconds = 415.981 FPS
2112 frames in 5.0 seconds = 422.280 FPS
1398 frames in 5.0 seconds = 279.543 FPS
1198 frames in 5.0 seconds = 239.411 FPS
1207 frames in 5.0 seconds = 241.352 FPS
1204 frames in 5.0 seconds = 240.734 FPS
1208 frames in 5.0 seconds = 241.465 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 31902 requests (31871 known processed) with 0 events remaining.
arho@timo-desktop:~$ glxgears
2167 frames in 5.0 seconds = 433.328 FPS
2175 frames in 5.0 seconds = 434.969 FPS
1442 frames in 5.0 seconds = 288.302 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 17813 requests (17764 known processed) with 0 events remaining.
arho@timo-desktop:~$ 


---

