---
title: "Wacom Graphire4 in Hardy"
date: 2008-05-05
forum: General Help
---

### Post by mishathegoat on 2008-05-05
Hey all! Got an issue maybe someone can help..
I'm no Linux expert so I'm gonna explain my problem as best as I can.

I used a Graphire4 Tablet to draw in Gimp when I used Gutsy. To get the tablet to function properly I had to open xorg.conf and there was a commented line that said something like:
```
## Uncomment the following if you are using a Wacom Tablet
```
So I'd do that and it'd work just fine.

A little while ago I downloaded and installed hardy and those lines in xorg.conf aren't there anymore and my tablet isn't functioning properly anymore.. Any ideas?

---

### Post by jessika-kaos on 2008-05-05
I had to add them manually to get my Wacom to work with Hardy (other than in mouse mode).

Here's the relevant section from my xorg.conf


```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    Inputdevice     "stylus"        "SendCoreEvents"
    Inputdevice     "cursor"        "SendCoreEvents"
    Inputdevice     "eraser"        "SendCoreEvents"
    InputDevice     "pad"
EndSection

...

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
	Option		"USB"	"on"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
	Option		"USB"	"on"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
	Option		"USB"	"on"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "pad"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "pad"
	Option		"USB"	"on"
EndSection 
```

---

### Post by mishathegoat on 2008-05-05
I'm Googling now.. but would you happen to have those lines of code? Thanks...

---

### Post by mishathegoat on 2008-05-05
Hmm still doesn't work.. I even followed this guide ([http://wiki.archlinux.org/index.php/Wacom_Tablet](http://wiki.archlinux.org/index.php/Wacom_Tablet)) which tells me how to add those lines of code.. Only problem I had with it was installing Linuxwacom .. which may already be installed anywho

Any other ideas anyone?

---

### Post by jessika-kaos on 2008-05-06
did you install wacom-tools also? that changes the device from /dev/input/event-whatever to /dev/input/wacom. I remember I had a lot of problems getting mine sorted out.

---

### Post by mishathegoat on 2008-05-06
Yep yep did that and it didn't do anything.. I mean my Tablet is in fact "working" it's just functioning as a mouse instead of a tablet for some reason..

---

### Post by fragos on 2008-05-06
My Graphire4 works fine with 8.04. I copied the xorg.conf Wacom specific lines I'd used in 7.04 and 7.10 and placed them in the 8.04 xoeg.conf.

---

### Post by jessika-kaos on 2008-05-06
Hmm, I don't know what else you could do. Maybe someone else has an idea?

---

### Post by mishathegoat on 2008-05-06
@fragos - Hmm could you post those lines if yeh still have them? Thanks

@jessika - Well I'm still lookin' around, I've found a few posts but still haven't gotten it workin'..

---

### Post by fragos on 2008-05-06
Here's my xorg.conf. I added the (4) InputDevice sections for driver Wacom. I also added 4 lines to the ServerLayout section that relate to the 4 InputDevice sections.

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Stylus2" 	"3"  # set button to right click
	Option		"Type"		"stylus"
	Option		"USB"           "on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"USB"           "on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"USB"           "on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"        "/dev/input/wacom"
	Option		"Type"          "pad"
	Option		"USB"           "on"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice     "pad"
EndSection

Section "Module"
	Load		"glx"
EndSection

---

### Post by gwi on 2008-05-06
I have a Wacom Graphire 1, which worked perfectly well with Dapper, Edgy, Feisty and Gutsy. And now with Hardy it doesn't anymore. After every time I log in, or switch to tty1-tty6 and back to tty7, the mouse pointer is frozen. I then have to unplug and reconnect the tablet (USB connected). The pen however loses it absolute positioning mode, and whenever the pen is out of reach of the tablet, the mouse pointer moves to the upper left corner of the screen. This makes things like photo editing impossible.
My Wacom settings in xorg.conf are still there after the upgrade, so I have no idea what is wrong.

I reported [this bug]("https://bugs.launchpad.net/ubuntu/+bug/227424").

I had four issues after upgrading. Three I have solved in the past days, but if this one isn't solved within a week, I'm going back to Gutsy. IMO Hardy does not deserve the "LTS" suffix (unless it stands for something else than "stability").

---

### Post by mishathegoat on 2008-05-06
> **fragos said:**
> Here's my xorg.conf. I added the (4) InputDevice sections for driver Wacom. I also added 4 lines to the ServerLayout section that relate to the 4 InputDevice sections.

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Stylus2" 	"3"  # set button to right click
	Option		"Type"		"stylus"
	Option		"USB"           "on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"USB"           "on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"USB"           "on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"        "/dev/input/wacom"
	Option		"Type"          "pad"
	Option		"USB"           "on"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice     "pad"
EndSection

Section "Module"
	Load		"glx"
EndSection

Dang, didn't work.. I might have to go back to Gutsy.. that sucks

---

### Post by storm99999 on 2008-05-06
I recently installed an Intuos3, and I remember a key point that the section that states that its type is pad is only for the Intuos3 and Cintiq.  A good guide I found is here: [http://ubuntuforums.org/showthread.php?t=25151](http://ubuntuforums.org/showthread.php?t=25151)

---

### Post by fragos on 2008-05-06
> **storm99999 said:**
> I recently installed an Intuos3, and I remember a key point that the section that states that its type is pad is only for the Intuos3 and Cintiq.  A good guide I found is here: [http://ubuntuforums.org/showthread.php?t=25151](http://ubuntuforums.org/showthread.php?t=25151)

Pad is how the express keys and scroll wheel on Wacoms, including Graphire4, are processed for input.

---

### Post by storm99999 on 2008-05-06
> **fragos said:**
> Pad is how the express keys and scroll wheel on Wacoms, including Graphire4, are processed for input.

That guide mentions the Graphire4 using pad in one part but not the other.  Sorry about that.

---

