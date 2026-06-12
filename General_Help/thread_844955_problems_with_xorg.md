---
title: "problems with xorg"
date: 2008-06-30
forum: General Help
---

### Post by Isomorphismus on 2008-06-30
Hi everybody,
basically, I want to enable xinerama on my system. I got two monitors, and I have a Matrox P750 graphics card. I followed the instructions in the archive concerning xinerama, which means, I modified my xorg.conf - file according the instructions there. 
Furthermore, I downloaded the (inofficial) driver for my graphics card, matroxdriver_mtx-x86_32-1.4.6.1-installer.run, which was recommended on many webpages. 
But restarting my ubuntu, it says "driver not found" and the resolution of my screen gets really low. 

I guess, that I put the BusID wrong, for the graphic card, I put 

BusID "PCI:1:0:0",

but how can I find out if this is true? 

well, I'm posting my xorg.conf as well, just in case.. 

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"0 Matrox Graphics, Inc. Millenium P650/P750 (rev 02)"
	Driver          "mtx"
	BusID		"PCI:1:0:0"
 	  Screen 0
	Option "THI" "True"
EndSection

Section "Device"
	Identifier	"1 Matrox Graphics, Inc. Millenium P650/P750 (rev 02)"
	Driver          "mtx"
	BusID		"PCI:1:0:0"
          Screen 1
	Option "THI" "True"
EndSection


Section "Monitor"
	Identifier	"Main Monitor"
	Option 		"DPMS"
EndSection

Section "Monitor"
        Identifier      "Second Monitor"
	Option 		"DPMS"
EndSection


Section "Screen"
	Identifier	"Main Screen"
	Monitor		"Main Monitor"
	Device		"0 Matrox Graphics, Inc. Millenium P650/P750 (rev 02)"
    SubSection "Display"
		Modes   "800x600"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Second Screen"
	Monitor		"Second Monitor"
	Device		"1 Matrox Graphics, Inc. Millenium P650/P750 (rev 02)"
	SubSection "Display"
		Modes   "800x600"
	EndSubSection
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
	Screen	     0	"Main Screen"
	Screen 	     1  "Second Screen" RightOf "MainScreen"
	Option   	"Xinerama" "true"
EndSection
```

thanks in advance for any help,
Iso

---

### Post by NT4usB on 2008-06-30
```
$lspci
```should show you the bus info for your card.

---

