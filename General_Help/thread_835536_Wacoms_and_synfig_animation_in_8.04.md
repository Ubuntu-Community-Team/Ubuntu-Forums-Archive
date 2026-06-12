---
title: "Wacoms and synfig animation in 8.04?"
date: 2008-06-20
forum: General Help
---

### Post by transkinetic on 2008-06-20
*update*
I fixed the issue by removing references to pad in the xorg.conf file. These references included an input device block and something about send core events at the end. i kept the stylus, cursor, eraser input events as well as the send core events entry for each of them. I will attache my xorg.conf for clarification incase anyone with similar issues wants to try copying it verbatim.

I just installed Xubuntu 8.04 hardy on my laptop. I want to make some animations in Synfig using my Wacom tablet. According to the [wiki]("https://help.ubuntu.com/community/Wacom"), my Graphire should work automatically. It works poorly by default. The size is seen as smaller than the tablet area and the pointer 'chatters' around where I'm pointing. The wiki links to a procedure for getting bamboo tablets working. That's not what i have but i'll try it anyhow and post back here. Any thoughts? In 7.04, running sudo apt-get install xserver-xorg-input-wacom wacom-tools worked for me.

---

### Post by transkinetic on 2008-06-20
After following [howto: Wacom on 8.04 hardy]("http://ubuntuforums.org/showthread.php?t=765915"), there is no change in function. My tablets event number is now linked to /dev/input/wacom each time i boot. Running cat /dev/input/wacom spews gibberish onto the screen when i move my stylus. i think xorg.conf is setup correctly. I've tried both using /dev/input/event"#" and /dev/input/wacom...

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
#	Option		"Device"	"/dev/input/event8"
	Option		"Type"		"stylus"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Maybe it's broken. I'm going to go test it on a windoze computer...back to windows, oh noes!

---

### Post by fragos on 2008-06-20
My Graphire4 works welll with 8.04. Here's my Wacom related xorg sections:

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
	Option		"USB"           "on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"        "/dev/input/wacom"
	Option		"Type"          "pad"
	Option		"USB"           "on"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice     "pad"
EndSection

---

