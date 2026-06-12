---
title: "help with res higher than 800x600"
date: 2008-06-23
forum: General Help
---

### Post by toddo on 2008-06-23
Hi folks --

I just installed 08.04 this morning.  Things seem to have worked for the most part, other than not having a resolution higher than 800x600 for my laptop display.  I have run update manager.  A cursory search of the forums didn't help.

Here's my xorg.conf:

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

Any ideas?  I'm new.

---

### Post by prshah on 2008-06-23
> **toddo said:**
> 
I just installed 08.04 this morning.  Things seem to have worked for the most part, other than not having a resolution higher than 800x600 for my laptop display.  
Any ideas?  I'm new.

Press Alt+F2, then give the command ```
gksudo displayconfig-gtk
```, then click on the "Graphics Card" tab; what driver is in use? Is it the same as your card? If you don't know what card you have, Open a terminal (Applications-Accessories-Terminal), then give the following commands and post the output here. ```

lspci | grep -i -e vga||graphi

```

---

### Post by toddo on 2008-06-23
Thanks for the speedy reply.  

Here's the output from the lspci command:
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7000M (rev a2) (rev a2)

Under Screen and Gfx prefs, I saw that ubuntu had chosen a generic driver.  I saw "nvidia 7 series" as an option.  Should I chose that? 

Is there a significant difference between 7 series and 7xxxM?

---

### Post by prshah on 2008-06-23
> **toddo said:**
> 
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7000M (rev a2) (rev a2)
Under Screen and Gfx prefs, I saw that ubuntu had chosen a generic driver.  I saw "nvidia 7 series" as an option.  Should I chose that? 


Which generic driver? "Vesa"?

Yes go ahead and try "nvidia 7 series", let's see what happens.

I don't have nVidia so can't advise you properly on that. As a starting point, search the forums for "envy".

---

### Post by toddo on 2008-06-23
As a followup:  

Should I consider trying envy?  Some googling informed me that it can attempt to find the right driver for my hw.

Has anyone here had any luck with it?  I'm a very green linux user, so if it requires any advanced knowledge, I'd appreciate a headsup, so I know to avoid it.

---

### Post by gaspar on 2008-06-23
> **toddo said:**
> As a followup:  

Should I consider trying envy?  Some googling informed me that it can attempt to find the right driver for my hw.

Has anyone here had any luck with it?  I'm a very green linux user, so if it requires any advanced knowledge, I'd appreciate a headsup, so I know to avoid it.

I´m using Envy with no problems, it detected my Ti4200 and installed it.

---

