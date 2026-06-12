---
title: "mouse keyboard and video driver stopped working"
date: 2007-10-15
forum: General Help
---

### Post by JBull on 2007-10-15
My X Server/Gnome crashed yesterday back to command line.  I rebooted and my mouse, keyboard, and NVIDIA drivers won't work.  I went in to the xorg.conf file and changed to the generic "nv" driver so I can get back into gnome now.  I had to take my USB keyboard off and use one with the old ps/2 type plug and it is working.  No matter what I do my mouse won;t work.  I;ve tried a USB mouse, and two different ps/2 mice but no go. 

I also reconfigured with dpkg-reconfigure xserver-xorg several times and it still wont work.  I manually edited my xorg.conf file to correct settings and still no mouse function.  I'm using this in xorg.conf with a regular two-button ps/2 mouse.  It almost seems as if the mouse drivers are gone.

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
EndSection

$mdetect -x                     gives this output:

/dev/psaux
ImPS/2


Any help?  Its really hard to use Gnome and Firefox with no mouse!

---

### Post by JBull on 2007-10-15
Another odd thing I just discovered, I went to reinstall gnome and xserver-xorg.  I typed apt-get remove gnome and I got the reply "gnome is not installed", which is strange because I am using gnome right now.  Anyway, I installed gnome even though it was really already there, and also reinstalled xserver-xorg.  then reconfigured xserver-xorg.  Still the mouse is not working.

Anyone have advice on how to proceed?  

When the crash happened I was playing Unreal Tournament 2004 online, whichI have done hundreds of times.  Suddenly it crashed all the way out of gnome to a command prompt.  Seems now everything is screwed.  Problems I have discovered so far is the USB keyboard stopped working, no mouse will work, the NVIDIA driver (kernel module built from NVIDIA installer) will not work, and my apt-get said gnome was not installed when it actually was, and my sound seems to have stopped working.

I'm considering reinstalling the OS from scratch but ouch that would suck....

---

