---
title: "usb mouse not working"
date: 2007-01-02
forum: General Help
---

### Post by Choad on 2007-01-02
says it all in the title really. got a new laptop, earlier on today it (the usb mouse) worked no effort, and now it doesnt work at all. i have been setting the laptop up all day so i couldnt say what caused it to stop working

---

### Post by Choad on 2007-01-03
> **Choad said:**
> says it all in the title really. got a new laptop, earlier on today it (the usb mouse) worked no effort, and now it doesnt work at all. i have been setting the laptop up all day so i couldnt say what caused it to stop working

ok i now know it has something to do with the fact that i am using the synaptics driver

i just took the vanilla xorg.conf and changed the driver to synaptics, and the usb mouse goes.

```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"synaptics"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
	Option		"HorizScrollDelta"	"0"
EndSection
```

thats the only mouse device i have in xorg. do i need to add another one for the usb?

---

### Post by komaroveli on 2007-01-03
hi,
nothing wrong with trying so backup your xorg.conf first, and then add following
```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection
```

retart...see if it works...

---

### Post by Choad on 2007-01-03
> **komaroveli said:**
> hi,
nothing wrong with trying so backup your xorg.conf first, and then add following
```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection
```

retart...see if it works...
thanks :D it now looks like

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"synaptics"
	Option		"CorePointer
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection
```

same result. :(

---

### Post by komaroveli on 2007-01-03
ok..change it back as it was and let's try this.
1. is it powered when you plug it in? (if it's a optical mouse red light will be on)
2. does computer recognizes it? run ```
lsusb
``` command ant post the output here.

---

### Post by Choad on 2007-01-03
richard@richard-laptop:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
richard@richard-laptop:~$ 

and yeah, it powers up....

---

