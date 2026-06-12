---
title: "synaptic + usb mouse *at the same time*?"
date: 2007-01-25
forum: General Help
---

### Post by Choad on 2007-01-25
at the moment, i have to edit xorg.conf and restart xorg every time i want to swap between the synaptic touchpad and the usb mouse.

its quite ridiculous to be having to do this, anyone know of a more permanent fix?

heres the relevent bits of my xorg.conf

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		**"mouse"**
	Option		"CorePointer
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
	**#Option**		"HorizScrollDelta"	"0"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

```

---

### Post by Choad on 2007-01-25
bump

c'mon it cant be that rare to want this setup? pretty much everyone with a laptop must require this

---

