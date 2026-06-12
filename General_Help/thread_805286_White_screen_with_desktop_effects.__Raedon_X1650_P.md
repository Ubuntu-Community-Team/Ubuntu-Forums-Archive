---
title: "White screen with desktop effects.  Raedon X1650 Pro"
date: 2008-05-23
forum: General Help
---

### Post by MORDOCtheGREAT on 2008-05-23
I have Hardy and am using a Raedon X1650 Pro and when I try to use the proprietary driver and I turn on visual effects I just get a white screen.  I then have to click around randomly on my screen to find the "none" button.  Any help would be awesome.

---

### Post by Donkinator on 2008-05-24
Sounds like the usual ATI driver issue. Try getting your hands on a copy of EnvyNG, [http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A) 
Use that to install the drivers. It may do the trick, otherwise you can just blame ATI for their lack of support to the Linux community, and buy NVidia next time.

---

### Post by Forlong on 2008-05-24
How did you install the driver for your card and what is the output of ```
grep -v ^# /etc/X11/xorg.conf
``` use the forum's [noparse][CODE][/noparse] tag when posting that here please (# button)

---

### Post by MORDOCtheGREAT on 2008-05-24
When I did the code in the terminal this is what I got.
```
mordoc@mordoc-linux:~$ grep -v ^# /ect/x11/xorg.conf
grep: /ect/x11/xorg.conf: No such file or directory

```
I'm guessing thats not a good thing.
Also I downloaded Envy and no money. It still does the same thing.

---

### Post by Forlong on 2008-05-24
Please just compy & paste the command over to your terminal.
Capital letters do matter in the filesystem.

---

### Post by SplasHmdfc on 2008-05-24
i had the same problem go to [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)   and follow the instruction very cearfuly i was gettin crazy and then i do the Method 1: Install the Driver the Ubuntu Way and it worked i have ati X1200 on 64x AMD  dont worry u can fix. ive tryed the EnvyNG and it didnt work with me so idk if u what try my way

---

### Post by MORDOCtheGREAT on 2008-05-25
Okay, copy and pasted and it gave me this
```
mordoc@mordoc-linux:~$ grep -v ^# /etc/X11/xorg.conf


Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection


```
Oh yeah,  I Tried doing it SplasHmdfc's way to no avail.

---

