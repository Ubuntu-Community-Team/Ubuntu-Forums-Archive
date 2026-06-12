---
title: "Please remind how to edit screen settings"
date: 2007-11-03
forum: General Help
---

### Post by martal on 2007-11-03
I've just installed Gutsy Gibbon.

Strangely, first time through the Live CD I had a normal screen, at 1280x1024. I made (too many) changes to try and get the resolution reporting correctly.

I reinstalled, this time on the Live CD I had 640x480 res, and this is how the installed version shows.

In Administration | Screen & Graphics I have:

Screen:
Model: Custom1
Resolution: 640x480 at 60Mhz

Graphics:
Driver: ati-Mach8, Mach32 etc. Can't see the rest.

My monitor is a Samsung SyncMaster 957DF. Screen & Graphics has close but not exact.

My Graphics card is an ATI  Radeon 8500 series. Screen & Graphics has a number of options for 8500. Not sure which one to choose.

Please advise on how I should proceed.

Manually edit the hmm... which file? And how?

---

### Post by taurus on 2007-11-03
Applications -> Accessories -> Terminal
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by #Reistlehr- on 2007-11-03
File: /etc/X11/xorg.conf

How: Carefully


:D


Yeah, but you wanna go down to the screens section where you see a bunch of resolutions. You should be able to just add "1280x1024" or somethign along the lines near the "640x480" entry.

If the changes you make break soemthing run:

sudo dpkg-reconfigure -phigh xserver-xorg

from a terminal after xserver fails, and it will rebuild it by default..

hmm, actually.. 

Run this first:
sudo dpkg-reconfigure -phigh xserver-xorg

And select the resolutions you want when it prompts you. If you don't know an answer, leave it at default.

Don't forget, just incase, to backup the current file (even though you don't want it lol)
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-back

---

### Post by martal on 2007-11-04
I've installed again.

Screens and Graphics is still showing as in my original post. Plug 'n Play, 640x480, 60Mhz

xorg.conf shows this:

Section "Device"
	Identifier	"ATI Technologies Inc Radeon R200 QL [Radeon 8500 LE]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R200 QL [Radeon 8500 LE]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Modes		"2048x1536" "1920x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

This appears contradictory.

I have issues with the top panel not expanded, as though it were 640px wide. I can't get down to the bottom of the Firefox window to resize it.

Still not sure how to proceed. :confused:

---

