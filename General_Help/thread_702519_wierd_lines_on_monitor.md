---
title: "wierd lines on monitor"
date: 2008-02-20
forum: General Help
---

### Post by thebrandon on 2008-02-20
I am having trouble with what I assume is a conflict between my xorg and my monitor.  Basically what is happening is I have these wierd horizontal lines that run vertically down my screen and make my desktop look like an episode of Dr Katz.  I can reboot my x server and it will go away, also, if I change the resolution and then switch it back it goes away.  It always comes back when I leave my computer sitting.  I have tried changing my screensaver and this doesnt seem to work either.   Also, I have an svideo out to my tv and even when the lines are on the monitor the tv display is fine.  Finally, when I reboot I get the error msg "OUT OF SCAN RANGE (random number, approx. 76) Khz , (another random number, approx. 2) Hz.  

A screenshot wont show the lines so I had to video them with my camera as I intended to post on youtube and add a link but youtube upload failed so instead I took a screenshot of the video which shows around the edges of the letters what is happening.  Also, turning off the monitor and back on, as well as using the monitor reset function, does not work.  

My monitor is a SONY SDM - M51 LCD and here is my xorg and that screenshot

```

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
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
	Identifier	"nVidia Corporation NV18 [GeForce4 MX 4000]"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"SDM-M51"
	Vendorname	"Sony"
	Modelname	"Sony SDM-M51"
	Horizsync	28.0-61.0
	Vertrefresh	48.0-65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV18 [GeForce4 MX 4000]"
	Monitor		"SDM-M51"
	Defaultdepth	24
	Option		"AddARGBGLXVisuals"	"True"
	Option		"RenderAccel"	"True"
	Option		"AllowGLXWithComposite"	"True"
	Option		"backingstore"	"True"
	Option		"TripleBuffer"	"True"
	Option		"TwinView"	"true"
	Option		"TwinViewOrientation"	"Clone"
	Option		"TVOutFormat"	"S-VIDEO"
	Option		"TVStandard"	"NTSC-M"
	Option		"SecondMonitorHorizSync"	"30-50"
	Option		"SecondMonitorVertRefresh"	"60"
	Option		"MetaModes"	"1024x768,1024x768;800x600,800x600;640x480,640x480"
	SubSection "Display"
		Depth	24
		Virtual	1280	960
		Modes		"1024x768@60"	"1280x960@60"	"800x600@60"	"800x600@56"	"640x480@60"
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
Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

[IMG]http://i79.photobucket.com/albums/j151/brandonburgess/Screenshot-DSCN7372MOV.png[/IMG]

---

### Post by thebrandon on 2008-02-22
As a side note I rebooted the other day and the error msg thrown up by the monitor is "OUT OF SCAN RANGE 74.18 kHz / 01 Hz"  I dont know if that info will help any, but there it is.

---

### Post by pointone on 2008-02-22
The only thing I can suggest is to try running "sudo dpkg-reconfigure xserver-xorg -phigh" to try to regenerate your xorg.conf file.

---

### Post by thebrandon on 2008-02-22
If I did that wouldnt I have to reinstall my vid card from scratch?  I have had so much trouble just getting it to act properly in the past I am wary of that path.

---

### Post by soldats on 2008-02-22
try finding the correct refresh rates for your monitor and manually place them in your xorg.conf file and restart X. it sounds like a refresh rate problem. make sure you back it up just in case.

---

### Post by pointone on 2008-02-23
> **thebrandon said:**
> If I did that wouldnt I have to reinstall my vid card from scratch?  I have had so much trouble just getting it to act properly in the past I am wary of that path.

dpkg-reconfigure saves a backup of your old xorg.conf file before making any changes, so if it doesn't help, you can easily revert to the old settings. It's worth a shot.

---

### Post by thebrandon on 2008-02-23
Well I seem to have fixed the problem by simply changing my Vertrefresh	from "48.0-65.0"  to "60"

---

### Post by wolf4540 on 2008-02-26
I was having a similar issue, i may try this when i get off work, thanks!!

---

### Post by thebrandon on 2008-02-27
Well it seems that I spoke to soon, my "fix" only seems to have worked for a short while and just extended the time it takes the lines to show up!  Hopefully someone else has a suggestion!  Its driving me mad!

---

