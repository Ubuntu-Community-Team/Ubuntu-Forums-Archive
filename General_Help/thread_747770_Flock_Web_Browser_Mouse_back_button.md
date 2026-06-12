---
title: "Flock Web Browser Mouse back button"
date: 2008-04-06
forum: General Help
---

### Post by WholeMilkRules on 2008-04-06
So this is my second time attempting to use linux. The first time was with Ubuntu breezy badger, which went well until the upgrade to 6.06 which messed with my wireless drivers.
This re-introduction to Ubuntu through Hardy is working amazingly. The wireless network setup went <almost> flawlessly, and nothing seems to be crashing *yet*.

I have a Logitech G5 mouse and wanted to use the thumb back and forward buttons on firefox, so I installed logitech-applet and locomo through the package manager. After the installation and a reboot, the buttons did what they were supposed to.

I then installed my favorite web browser, Flock, using a .deb package  I found at [http://www.getdeb.net/app/Flock]("http://www.getdeb.net/app/Flock")

All seemed to be working well, except that the thumb buttons didn't work in Flock. After searching on Google, I decided to modify the xorg.conf file using this forum post
[http://ubuntuforums.org/showthread.php?t=371379]("http://ubuntuforums.org/showthread.php?t=371379")

So I modified the xorg.conf file from

Section "InputDevice"
Identifier "Configured Mouse"
Driver "vmmouse"

to

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ButtonMapping" "1 2 3 6 7"
Option "ZAxisMapping" "4 5"
EndSection

I then restarted xorg and the thumb buttons did work. . . only in Flock. Somehow it stopped working in Firefox. I ended up playing with the xorg.conf file and completely removing both logitech-applet and locomo, and somehow, the two thumb buttons work on Firefox, but not in Flock.

For reference, my xorg.conf now is:

Section "InputDevice"
    Identifier	"Configured Mouse"
    Driver	"vmmouse"
	Option	"CorePointer"
	Option	"Device"	"/dev/input/mice"
	Option	"Protocol"	"ExplorerPS/2"
	Option	"Buttons" "9"
	Option	"ZAxisMapping"	"4 5"
EndSection

I think the issue has something to do with the driver. Firefox works with vmmouse, and flock works with mouse.
I couldn't understand why Flock had to be so temperamental, because it has a Firefox base.

Also, in Flock, both of the thumb buttons work as a normal left click.

Thanks in advance, and I hope the information above helps!

---

