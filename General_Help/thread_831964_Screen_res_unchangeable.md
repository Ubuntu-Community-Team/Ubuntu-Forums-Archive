---
title: "Screen res unchangeable"
date: 2008-06-17
forum: General Help
---

### Post by Nightglade on 2008-06-17
Hi there. Sorry if this is in wrong forum

(Firstly I'd like to add I've looked through the forums at other solutions, to no avail) 

This is my first real time at using Linux, and I chose Ubuntu. But my screen resolution is stuck to a minimum of 1024 x 768. 

I've tried changing the xorg.conf file, but that didn't work (so i reset it) and I did the xorg configuring thing in the terminal, but that just kept focusing on my keyboard for some reason.

Here is my xorg.conf file


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
Firstly I'd like to add I've looked through the 
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
EndSection


I'm running an nVidia GeForce 7300GT 512mb. with a hp v72 monitor

I'd really appreciate any help you can give, and sorry if it seems like a silly question.

---

### Post by nikgare on 2008-06-17
Try running this to see if you can manually configure your monitor:

sudo displayconfig-gtk

Nik

---

### Post by Pjotr123 on 2008-06-17
> **nikgare said:**
> Try running this to see if you can manually configure your monitor:

sudo displayconfig-gtk

Nik

I think so, too. For this you have to open a terminal:
Applications - Accessories - Terminal.

If you have an nvidia card, nvidia-settings may prove useful if the above fails:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)
(number 2 )

---

### Post by argail1980 on 2008-06-17
did you install the restricted drivers?

---

### Post by Nightglade on 2008-06-17
Hi there, yes I tried the restricted drivers but it wont let me past 1024x768 with 51hz. 

Am going to try the displayconfig thing quickly now

EDIT: oh the displayconfig thing was *that*

Yes. It shows a plug and play monitor (I tried to change that previously, though my monitor isn't listed and a standard CRT 17" @ 1280x1024 50hz screws the screen up to the point i have to use xfix.  I also tried the nVidia 7 series driver in the graphics thing, and that wouldnt let me get past 640x480 so had to reset it back to the VESA driver.

---

### Post by Pjotr123 on 2008-06-17
> **Nightglade said:**
> Hi there, yes I tried the restricted drivers but it wont let me past 1024x768 with 51hz. 

Am going to try the displayconfig thing quickly now

The 51 hz aren't really 51 hz. The restricted Nvidia driver uses fake Hz numbers to uniquely distinguish a screen. In reality it's probably 60 or 75 Hz (check the BIOS of your screen for that, if you're curious).

You definitely want the restricted driver for optimal performance. You can correct the resolution by means of the how-to in my earlier post.

---

### Post by Nightglade on 2008-06-17
Thankyou very much everyone for the help, but nvidia-settings thing worked like an absolute charm! Thankyou :D *big hugs*

---

### Post by mempman on 2008-06-17
> **Nightglade said:**
> 
Section "Device"
	Identifier	"Configured Video Device"
EndSection


For what its worth, typically, nvidia opensource driver reads "nv," and the proprietary drivers reads "nvidia" in the Device-Identifier section.

---

