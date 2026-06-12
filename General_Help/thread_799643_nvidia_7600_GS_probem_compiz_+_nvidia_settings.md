---
title: "nvidia 7600 GS probem: compiz + nvidia settings"
date: 2008-05-19
forum: General Help
---

### Post by epidemiks on 2008-05-19
Hi,
I'm having a problem getting compiz running while also having nvidia xserver controls..
using envyNG, i can get compiz up and everything running sweet, but I can't change any monitor settings other than the preferences/screen resolution, which is pretty lax in terms of options. 
envy put the nvidia xserver settings tool in the admin toolbar, but won't let it run because its missing nvidia-xsettings, yet installing that package still doesn't allow me to open them.

back in 7.10, I had compiz and full nvidia controls, gamma/colour/dual screen options etc..

why won't 8.04 let me do this?

---

### Post by epidemiks on 2008-05-23
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
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"NVIDIA GeForce 7 Series"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
	Vendorname	"NVIDIA"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1680x1050"
	Horizsync	31.5-65.5
	Vertrefresh	56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1680x1050@60"	"1600x1024@60"	"1440x900@60"	"1280x800@60"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@56"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection

---

### Post by epidemiks on 2008-05-23
also, gutsy let me set the actual monitor.. 
i'm in the process of trying to purge all nvidia stuff to start from scratch..

---

### Post by iaculallad on 2008-05-23
Try replacing the "Screen" and "Monitor" Section. Copy and Paste it to overwrite the existing one in your xorg.conf file, Save it then restart.
[B]
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak[/B]
**sudo gedit /etc/X11/xorg.conf**

Hope this will work your case.


Section "Screen"
Identifier	"Default Screen"
Device		"Configured Video Device"
Monitor		"Configured Monitor"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1680x1050"
EndSubSection
EndSection

Section "Monitor"
Identifier "Configured Monitor"
Vendorname "Generic LCD Display"
Modelname "LCD Panel 1680x1050"
HorizSync 30-110
VertRefresh 50-160
EndSection

---

