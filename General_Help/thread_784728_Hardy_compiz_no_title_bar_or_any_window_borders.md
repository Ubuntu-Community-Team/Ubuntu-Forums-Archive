---
title: "Hardy compiz no title bar or any window borders"
date: 2008-05-06
forum: General Help
---

### Post by nealio1000 on 2008-05-06
i recently upgraded from gutsy to the hardy. in gutsy i had functioning desktop effects with no issues. this is an hp dv6000 laptop with integrated intel graphics. When i go to appearance>visual effects and enable normal or extra the screen refreshes and every opened window loses its window border and titlebar. not only that but the window is frozen in place even with alt+click and drag. It will do the same thing for any window opened after the effects are enabled as well. the only way i can get the window borders is to use metacity but then i get no effects. the effects werent essential but i did like having them. here is a copy of my xorg

```
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
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
```

Lastly if i open terminal and run "compiz" this is my error

```
compiz (core) - Error: Screen 0 on display ":1.0" already has a window manager; try using the --replace option to replace the current window manager.
compiz (core) - Fatal: No manageable screens found on display :1.0

```

---

### Post by ephro on 2008-05-06
Try these commands and see if it works:

```
sudo apt-get install emerald
emerald --replace
```

---

### Post by ubuntwinkel on 2008-05-06
I had a similar prob in Hardy; whenever I enabled 'Extra Visual Effects' the window decorations (title bar and frames) disappeared.  The only fix I found that worked for me was to install xserver-xgl.  Have no idea why it worked.  Have no idea why it wasn't already installed.  It may be worth a try.
```
sudo apt-get install xserver-xgl
```
Then do ctrl-alt-backspace to restart the xserver (Caution: close all open apps first--the xserver shutdown remorselessly kills any apps that are open)

---

### Post by tommyhakinen on 2008-05-06
I was having this problem with Gutsy before. I had compiz-fusion and emerald installed. That happened every time I switch the visual effects. Later, I removed emerald and everything just worked well. But I am not sure in Hardy. 

But if you have Compiz-Fusion installed and need a toggling switch that can switch between Metacity(Normal) and Compiz(Extra), I recommend you to use Fusion-Icon. Here how to install it:

> sudo apt-get install fusion-icon

good luck

Regards,

tommy

---

