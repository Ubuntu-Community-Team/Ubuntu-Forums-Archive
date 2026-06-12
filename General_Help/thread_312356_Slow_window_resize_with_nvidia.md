---
title: "Slow window resize with nvidia"
date: 2006-12-04
forum: General Help
---

### Post by Cloud79 on 2006-12-04
Window resizeing with nvidia binary driver i so slow. I dont seem to have this problem with my laptop (intel graphics)

It is slow with both metacity and emerald/beryl

Does every nvidiacard owner have this problem? 


I run edgy.
Here is my xorg.conf

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"se"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection


Section "Device"
	Identifier	"NVIDIA Corporation 7600GS"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"RenderAccel" "true"
	Option          "TripleBuffer" "true"
        Option     "TwinView"
   	Option     "MetaModes"  "1600x1200,1600x1200"
	Option     "TwinViewOrientation"      "RightOf"
	Option     "SecondMonitorHorizSync"   "UseEdidFreqs"
	Option     "SecondMonitorVertRefresh" "UseEdidFreqs"
	Option "AddARGBGLXVisuals" "True"
	Option "XAANoOffscreenPixmaps" "true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-80
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation 7600GS"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1600x1200"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by PriceChild on 2006-12-04
run
```
sudo nvidia-xconfig
```I don't think that both dri and glx should be enabled in modules... that command will fix things.

---

### Post by Cloud79 on 2006-12-04
I removed it and it is still slow.

With metacity it is ok though!

---

### Post by PriceChild on 2006-12-04
Don't remove anything... just run that command I gave you.

---

### Post by Cloud79 on 2006-12-05
Doesn't make a difference. It has to be driver related.

---

### Post by PriceChild on 2006-12-05
Have you restarted your computer since that command?

Restarting just X may not be good enough.

---

### Post by odix on 2007-02-13
it seems not be a display driver problem, more a mainboard chipset driver problem, I've checked various display driver versions, all with the same result, slow. It seems that the bottleneck is the pci-express interface driver, because my old pc running with an Amd XP1900 and AGP Geforce5200 outperforms my AMD64X2-3800 with pci-e Geforce 6600 on the desktop (2D, not tested 3D), any ideas ?

---

### Post by pppetter on 2007-02-13
> With metacity it is ok though!

Then it's fixed? Resizing windows is faster than before right? 

Emereald/Beryl is bloaty and bad for you :P That's just what I think. But if you want to resize windows faster in beryl you should look into what settings you have. But my big tip for you is to try Official Compiz, it's way faster and not that bloaty.

---

### Post by NoobieDoobieDo on 2007-06-26
Exactl same problem with Ti4200, tried many drivers - nothing seems to work.

[See here]("http://ubuntuforums.org/showthread.php?t=484680")

---

