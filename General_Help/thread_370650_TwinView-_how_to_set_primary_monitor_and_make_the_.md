---
title: "TwinView- how to set primary monitor and make the background image not stretch??"
date: 2007-02-26
forum: General Help
---

### Post by billdotson on 2007-02-26
I put the text in my xorg.conf to configure the TwinView setup.  I have an LCD on my right hooked up through DVI and a CRT on my left hooked with through DVI (an adapter for VGA) When I boot up everything is stretched out like it sees both monitors as one screen.. the panels+ the desktop background.  I changed some stuff and got it to where my right monitor was default but the Ubuntu login screen still shows up on the left, the top panel is on the left (where the applications menu and other icons are) and the background+panels are still stretched out.  Also, I have to move the mouse right to get to the monitor on the left.. annoying.  

Anyways here is my xorg.conf section for my videocard:

Section "Device"
	Identifier	"nVidia 7800GT"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
Option "TwinView" "True"
Option "TwinViewOrientation" "LeftOf"   
Option "UseEdidFreqs" "True"
Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
Option "UseDisplayDevice" "string" #replace 'DFP,DFP' with either 'DFP' (Digital flat panel connected via DVI port), 'CRT' (any monitor that is connected via VGA ports), or 'TV'
Option "ConnectedMonitor" "LCD,LCD"
EndSection

Thanks alot.

---

### Post by NewOldTimer on 2007-02-26
maybe in here?....[http://www.ubuntuforums.org/showthread.php?t=301946&highlight=twin+view](http://www.ubuntuforums.org/showthread.php?t=301946&highlight=twin+view)

---

### Post by billdotson on 2007-02-26
not everything is answered in that one post.. it would be nice if someone would just tell me how instead of hey read a 10 page topic to try and find it.

---

