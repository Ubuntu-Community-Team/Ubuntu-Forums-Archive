---
title: "What Mouse and Keyboard do you use?"
date: 2007-05-19
forum: General Help
---

### Post by Papillonrus on 2007-05-19
I am using a M$ Trackball Explorer and a M$ Internet Keyboard.  I have had them for about 5years.  I fixed the issue with the Trackball today.  Now I'm looking for the keyboard fix to enable the web and the My Computer key.  Here is my xorg.conf files for the mouse and keyboard.   I've showed you mine now everyone show their Keyboard and Mouse models and their working xorg.conf sections.  perhaps this will help many Noobes trying to find fixes for their little quirks.  Maybe a post for other hardware like video cards, printers, joysticks and soundcards would help also.    Warning each fix posted may not work for your PC, so be very careful and research the posted fix before you use it.  No guarantees, no warranty, you are responsible for what you feed your PC.  Thanks to all who participates.

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Buttons"		"7"
	Option		"ZAxisMapping"		"4 5"
	Option		"ButtonMapping"		"1 2 3 6 7"
EndSection

---

### Post by Cene on 2007-05-19
Erm okay... I got Logitech MX518 and Prodige FlatX Ultra keyboard. Both have some issues. Not really ruining my life or anything, but would be fine to fix them:
In mouse, the back and forward buttons won't work. Everything else does.
In keyboard I can't get the multimedia keys to work. Especially volume + and - and the mute button would be cool to see working.

Here's my xorg.conf:
```

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "fi"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "Dev Name" "Logitech USB-PS/2 Optical Mouse"
    Option         "Dev Phys" "usb-0000:00:11.2-1/input0"
    Option         "Device" "/dev/input/mice"
    Option         "Buttons" "10"
    Option         "ZAxisMapping" "4 5"
    Option         "Resolution" "800"
EndSection

```

---

### Post by Papillonrus on 2007-05-19
Sweet, the fix for the keyboard was in system/preference/keyboard, just configure the keyboard to show what you are using.  I'm liking this more and more.

---

### Post by aks44 on 2007-05-20
Papillonrus,

Based on your example, I managed to make my 5 buttons / 2 wheels mouse (no brand) almost work. Only the second wheel does not work correctly (it behaves like the first one, but it should be scrolling horizontally, at least it did under M$ XP).

Anyway, I'm glad to have my Backward/Forward buttons working again, thank you !

FWIW here is the xorg.conf section :

```
Section "InputDevice"
  Identifier "Configured Mouse"
  Driver "mouse"
  option "CorePointer"
  option "Device" "/dev/input/mice"
  option "Protocol" "ExplorerPS/2"
  option "Buttons" "9"
  option "ZAxisMapping" "4 5"
  option "ButtonMapping" "1 2 3 6 7"
EndSection
```

Any idea how I could configure my second wheel to scroll horizontally ? I'm a Linux newbie (installed Kubuntu yesterday for the first time), and I don't really have an idea where to look for... Anyway I'll continue searching on the web, and will edit this post if I find a solution.

**Edit:** I forgot to mention that I already tried
```
option "ZAxisMapping" "4 5 8 9"
```with no luck :(

---

### Post by Papillonrus on 2007-09-12
have you tried 

option "xaxismapping"   "8 9"  seems reasonable that if you have a Z axis there also has to be an X axis.

---

