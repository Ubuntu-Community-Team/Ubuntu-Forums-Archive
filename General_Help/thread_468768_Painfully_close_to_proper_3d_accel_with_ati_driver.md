---
title: "Painfully close to proper 3d accel with ati drivers (Resolution Problem)..."
date: 2007-06-09
forum: General Help
---

### Post by Tadhg on 2007-06-09
I've been trying to get everything working in feisty for the last few days, and like all my other installs, my main woe has been ati drivers. I've finally got them working now, and no longer have the mesa problem etc (using a x700). 

The problem I'm left with, is my resolution doesn't seem to be correct....even though it says it is correct. 

My laptop supports 1200x800 and is set at 1200x800 at the moment, yet the desktop is too big for the screen if you get what i mean. A portion of the desktop is off screen. If i move the cursor to the edges of my screen, everything moves over. I've tried

```
aticonfig --lcd-mode=center
```

which didn't help so obviously something is wrong in my xorg file so here it is:

```


Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"int10"
	Load		"vbe"
	Load		"glx"
	Load		"GLcore"
	Load		"dri"
	Load		"v4l"
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility X700 (PCIE)"
	Boardname	"ATI Radeon"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  **modeline  "1200x800@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync**
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility X700 (PCIE)"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		[B]Virtual	1200	800
		Modes		"1200x800@60"[/B]
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "ServerFlags"
EndSection


Section "Extensions"
	Option		"Composite"	"0"
EndSection
```

Any suggestions?

---

### Post by Tadhg on 2007-06-09
Right, all fixed, easy solution, I just had to comment out the lines in bold.

---

### Post by ratazana80 on 2007-06-14
Hi can U tell me how you were able to make the 3D acceleration work on mobility X700?

I also own a laptop with a X700 Ati radeon mobility - Asus A6va - and can't make the 3D accel work.

thanks.

---

