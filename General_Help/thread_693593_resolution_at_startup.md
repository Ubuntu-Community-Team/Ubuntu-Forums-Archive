---
title: "resolution at startup"
date: 2008-02-11
forum: General Help
---

### Post by daboo_discovery on 2008-02-11
i have very recently installed ubuntu gusty gibbon on my computer.Although the operating system runs fine, however i was trying out commands and things; and one day i pressed 
ctrl+alt+backspace. The screen blanked out and when it came on again, the resolution was set to 640*480. 

Although i didn't have such a problem before this experiment :( , now every time i start the computer , the startup screen has big fonts and when the desktop appears , the resoultion is set to 640*480 . Even though i set it to 1024*768 each time and the resolution becomes fine, however every time i start the system, the resolution is again set to 640*480.

What is the way to solve this problem so that the resolution stays at 1024*768 every time and does not reset itself to 640*480.

---

### Post by hahahan on 2008-02-11
Daboo_discovery,

Maybe this helps:

sudo gedit /etc/X11/xorg.conf

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768"  <-- [COLOR="black"]**Your disired res.**[/COLOR]
	EndSubSection
EndSection

And

sudo gedit /boot/grub/menu.lst

kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=????  ro quiet splash vga=971

add **vga=791** to the kernel you are booting.

Goodluck.

---

### Post by daboo_discovery on 2008-02-11
but it is already there!

i am posting it here..



Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" #               
	Identifier	"device1"
	Boardname	"intel"
	Busid		"PCI:0:2:0"
	Driver		"intel"
	Screen	1
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

---

### Post by daboo_discovery on 2008-02-11
i have tried the second method too!
But it did not help.

---

### Post by hahahan on 2008-02-11
How about Menu>Preferences>screen resolution and set the desired resolution there?

regards

---

### Post by daboo_discovery on 2008-02-12
yes then the resolution does become fine, but when i restart the computer , it again becomes 640*480!

All this happened only after i did ctrl+alt+backspace, and it's not been cured yet:(

---

### Post by daboo_discovery on 2008-02-15
the problem has been solved...


Thanks

---

### Post by Takmadeus on 2008-02-15
> **daboo_discovery said:**
> the problem has been solved...


Thanks

Would you mind telling us how did you solve it?

---

