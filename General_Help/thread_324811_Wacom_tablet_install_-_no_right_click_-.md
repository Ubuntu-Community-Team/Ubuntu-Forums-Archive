---
title: "Wacom tablet install - no right click -"
date: 2006-12-24
forum: General Help
---

### Post by booboo on 2006-12-24
Hi I'm a brand new Ubuntu user,
installed 2 days ago...
I had a hell of time to install my artpad II serial wacom tablet.
But a big issue is still around, there is no right click on the button.
Just the regular click on the pointer.
Not too bad but I'm not using mouse since a couple of years.
So a working tablet is quite important to me.
A little trick to bring the right click on, will be great.
Thanks.

Here is my xorg.conf 

> Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
    Identifier "stylus"
    Driver "wacom"
    Option "Device" "/dev/ttyS1"
    Option "Type" "stylus"
    Option "KeepShape" "on"
EndSection

Section "InputDevice"
    Identifier "eraser"
    Driver "wacom"
    Option "Device" "/dev/ttyS1"
    Option "Type" "eraser"
    Option "KeepShape" "on"
EndSection

Section "InputDevice"
    Identifier "cursor"
    Driver "wacom"
    Option "Device" "/dev/ttyS1"
    Option "Type" "cursor"
    Option "KeepShape" "on"
EndSection

---

### Post by dio525i on 2006-12-24
i'm not sure exactly...a friend of mine was using a tablet pc and had the same problem with a wacom touch screen....he said all he did was search synaptic for wacom and it came up with some package that said it would enable the screen he installed it and everything worked fine

sorry i don't know more...but maybe it could narrow your searches?

---

### Post by booboo on 2006-12-24
Thanks dio525i,
I tried to re-install with synaptic, but still the same situation.
An half working tablet,
and feeling like an antique single click Mac !!!

---

### Post by dio525i on 2006-12-24
sorry it didn't help much....if i get a hold of him in the next day or so i'll be sure to ask...but until then..good luck in finding a solution

---

### Post by fragos on 2006-12-24
The Ubuntu wacom package has a list of supported devices you can see with Synaptic.  Artpad isn't on that list.  Perhaps current support is more geared toward USB tablets.  Your artpad may be supported as a different device.  Synaptic also shows wacom tools which may be helpful.

---

### Post by booboo on 2006-12-25
Happy holidays 
I found the solution.....:p
Just needed to put

> Option 	"Button1"   "1"
Option 	"Button2"   "3"

into the stylus


Here is my Wacom section for records
Wacom serial ArtpadII KT-0405-R



> Section "InputDevice"
    Driver 	"wacom"    
    Identifier  "stylus"
    Option	"Device"    "/dev/ttyS1"
    Option 	"Type"      "stylus"
    Option 	"Mode"      "Absolute"
    Option 	"KeepShape" "on"
    Option 	"Button1"   "1"
    Option 	"Button2"   "3"
EndSection

Section "InputDevice"
    Driver      "wacom"    
    Identifier  "eraser"
    Option      "Device"    "/dev/ttyS1"
    Option      "Type"      "eraser"
    Option      "Mode"      "relative"
    Option      "KeepShape" "on"
EndSection

Section "InputDevice"
    Driver      "wacom"    
    Identifier  "cursor"
    Option      "Device"    "/dev/ttyS1"
    Option      "Type"      "cursor"
    Option      "KeepShape" "on"
EndSection

---

### Post by 0x29a on 2007-01-23
> **booboo said:**
> Happy holidays 
I found the solution.....:p
Just needed to put

> 
Option "Button1" "1"
Option "Button2" "3"


into the stylus


Here is my Wacom section for records
Wacom serial ArtpadII KT-0405-R


Hey booboo, this is great! I have both an artpadII and a graphire. I like the artpadII way better. Thanks for working this out!

Andrew

---

### Post by smitty5533 on 2007-01-23
i just put in :
"button 2" "3" 
and it works perfectly with the toshiba r15 tablet!

=D>  Thank you everybody!

---

### Post by Scunizi on 2007-01-28
I've got a Graphire 4 and would like to activate the roller wheel and two button's that are on the pad.  Any ideas?

---

### Post by galileon on 2007-02-01
that worked on my hp tc1100 tablet pc - it uses a wacom graphics tablet

---

### Post by Cityrider on 2007-09-14
Hi Guys -

Brand new here - just installed Feisty Fawn a couple of days ago after reading an article and it's looking good :)

It never occurred to me though that I might be able to get my old serial ArtpadII graphics pad working under Ubuntu as it belongs to a bygone age. However reading some of these posts got my attention and so I've tried to install it.

The pad seems to have been detected as the Wacom drivers appear in my xorg.conf file but with the settings for a tablet PC. I then edited the xorg.conf Wacom entries to the values described in this thread and rebooted ... nothing changed and pad doesn't work :(

Is there some additional set-up stage that I've missed here? Now I know it's possible I want to try and get the thing working as it's always given good service.

Thanks in advance for any guidance.

---

### Post by fragos on 2007-09-14
> **Scunizi said:**
> I've got a Graphire 4 and would like to activate the roller wheel and two button's that are on the pad.  Any ideas?

First you must add the wacom device "pad" to xorg.conf.  The default xorg is configured for older serial tablets that didn't have the pad buttons.  Bits from my xorg.conf are included for example.

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Stylus2" 	"3"  # set button to right click
	Option		"Type"		"stylus"
	Option		"USB"           "on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"USB"           "on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"Speed"         ".8"
	Option		"USB"           "on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"        "/dev/input/wacom"
	Option		"Type"          "pad"
	Option		"USB"           "on"
EndSection

Also in the "ServerLayout" Section you'll need the following

	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice     "pad"

If you wish to change the action of the buttons and wheel, check out "xsetwacom" in a terminal window.

---

### Post by Cityrider on 2007-09-15
Problem solved! Thanks go to Booboo for his (her?) original work.

I just had to stare hard at the xorg.conf in original post, have a hunch, Google around a bit and then alter ttyS1 to ttyS0 as my ArtpadII was effectively on "COM1".

So much to learn!

---

### Post by UofLSpeed on 2007-09-20
Just posting to say thanks for the help.  That saved me a lot of frustration.

---

### Post by ibbuntu on 2008-02-22
Thanks this worked for me on a Toshiba Portege R400. Now to the other problems!

---

