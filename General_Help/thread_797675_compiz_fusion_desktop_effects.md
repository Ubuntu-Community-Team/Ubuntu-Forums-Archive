---
title: "compiz fusion desktop effects"
date: 2008-05-17
forum: General Help
---

### Post by GOfree on 2008-05-17
Hi,

My desktop effects are not working again. I started installing the Looking Glass 3D desktop, then changed my mind. Now Compiz Fusion is not working.

I have been through this before, so I knew some of the common setup problems to look for. But checking over everything, everything looks to be okay. Still, when I try to enable desktop effects, I get the message "Desktop effects could not be enabled."

So, here is the situation:

- ATI radeon express 200M graphics card
- Graphics Driver: fglrx
- xlg rather than aiglx
- compiz fusion installed with ccsm
- composite line added to xorg.conf


> Section "InputDevice"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"ATI Radeon (fbdev)"
	Busid		"PCI:1:5:0"
	Driver		"fglrx"
	Screen	0
	Vendorname	"ATI"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	768
		Modes		"1280x768@60"	"1280x720@60"	"800x600@60"	"800x600@56"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"dbe"
	Load		"v4l"
EndSection
Section "device" #   
	Identifier	"device1"
	Boardname	"ATI Radeon (fbdev)"
	Busid		"PCI:1:5:0"
	Driver		"fglrx"
	Screen	1
	Vendorname	"ATI"
EndSection
Section "screen" #   
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"
	EndSubSection
EndSection
Section "monitor" #   
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
Section "Extensions"
	Option 		"Composite" 		"1"
EndSection


The line in xorg.conf under "device" for "Boardname" looks suspicious. Isn't "fbdev" another ati driver? Could this be conflicting with fglrx?

And what about the line under "module" that says "Load 'glx"? Should this be "glx"?

What should I try next? Any suggestions?

---

### Post by prshah on 2008-05-17
> **GOfree said:**
> Still, when I try to enable desktop effects, I get the message "Desktop effects could not be enabled."


Open a terminal, Applications-Accessories-Terminal, and give the command [code]compiz --replace]/code] The output error messages (if any) will give us a more detailed clue.

---

### Post by GOfree on 2008-05-17
Thanks prshah,

When I ran "compiz --replace", here's what I got:

> geoffrey@geoffrey-laptop:~$ compiz --replace
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":1.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0
Window manager warning: Log level 8: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed
Window manager warning: Log level 8: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed
Window manager warning: Log level 8: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed
Window manager warning: Log level 8: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed
Window manager warning: Log level 8: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed
Window manager warning: Log level 8: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed
Window manager warning: Log level 8: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed
Window manager warning: Log level 8: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed
Window manager warning: Log level 8: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed
Window manager warning: Log level 8: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed
Window manager warning: Log level 8: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed
Window manager warning: Log level 8: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed
Window manager warning: Log level 8: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed
Window manager warning: Log level 8: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed
Window manager warning: Log level 8: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed
Window manager warning: Log level 8: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed
Window manager warning: Log level 8: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed
Window manager warning: Log level 8: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed
Window manager warning: Log level 8: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed
Window manager warning: Log level 8: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed
Window manager warning: Log level 8: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed
Window manager warning: Log level 8: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed
Window manager warning: Log level 8: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed
Window manager warning: Log level 8: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed
Window manager warning: Log level 8: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed
Window manager warning: Log level 8: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed
Window manager warning: Log level 8: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed
Window manager warning: Log level 8: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed
Window manager warning: Log level 8: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed
Window manager warning: Log level 8: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed
Window manager warning: Log level 8: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed
Window manager warning: Log level 8: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed


That's bad, isn't it?

---

### Post by GOfree on 2008-05-17
Should I try switching from xgl to aiglx?

How would this be done?

---

### Post by GOfree on 2008-05-18
No suggestions?!

I guess I am on my own here.

(I realize that people must be sick of these questions. I read as much as I could before asking, and tried to figure it out on my own. Oh well...)

---

