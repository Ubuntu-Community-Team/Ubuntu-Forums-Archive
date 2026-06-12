---
title: "Two mouse sections in xorg.conf"
date: 2006-10-02
forum: General Help
---

### Post by munwin on 2006-10-02
Can anyone tell me why there are two sections in my xorg.conf for mice ?
I use a USB mouse.
Can I remove one, and if so, which one ?

```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Generic Mouse"
    Driver         "mouse"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
EndSection
```

---

### Post by munwin on 2006-10-03
Bump...

---

### Post by slimdog360 on 2006-10-03
Its probably one for the system to fall back on. Id image you could get rid of the generic mouse one but Im not really sure. You can always comment out one of them by putting #'s in front of the parts you dont want. And if your mouse stops working you know its the other which you should have commented out.
But if everything is going fine I personally wouldnt touch anything.

---

### Post by CatKiller on 2006-10-04
> **munwin said:**
> Can anyone tell me why there are two sections in my xorg.conf for mice ?
I use a USB mouse.
Can I remove one, and if so, which one ?

You can probably remove one. Make a backup of your xorg.conf before fiddling with it, since you can copy it back easily enough from a virtual console with just the keyboard.

I'm using a USB mouse, and mine comes in on /dev/input/mice, but my protocol is different, too. You'll need to change the InputDevice of your ServerLayout section if make any changes, and you might want to bear this section of **man xorg.conf** in mind:>        Option "CorePointer"
              When  this  is  set,  the  input device is installed as the core
              (primary) pointer  device.   There  must  be  exactly  one  core
              pointer. 

---

### Post by 3miel on 2006-10-20
how to configure two mouse in xorg.conf ?? 
```
"InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	
	##start 4 ps2 mouse##
	#Option		"Device"		"/dev/input/mice"
	#Option		"Protocol"		"ImPS/2"
	##end ps2##

	##start 4 com1 mouse##
	#Option		"Device"		"/dev/ttyS1"
	Option 	"Device" 		"/dev/ttyS0" 
    	Option 	"Protocol" 		"auto"
	##end 4 com#
	
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
```
U can see that i'm using mouse plugin to com1 port.
is any possibility to use two mouse at the same time? 
os : Breezy Badger (Ubuntu 5.10)
under win98se two mouse R working fine.

why i need it? mouse plugin to port com1 doesn't have scroll but it work fine.
mouse plugin to port ps2 have scrolls but moving cursor is not very correctly, when i wanna move up cursor sometimes it hang up.
i cleared mouse but it didn't help.

---

### Post by CatKiller on 2006-10-20
I think that you'd need to have two separate InputDevice sections, each configured to one mouse. And only one should be a CorePointer.

I don't really know much more than that, but **man xorg.conf** should tell you more. Good luck.

---

