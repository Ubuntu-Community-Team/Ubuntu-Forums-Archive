---
title: "Edit X11org.conf"
date: 2006-10-17
forum: General Help
---

### Post by squibT on 2006-10-17
I have an IBM T20 laptop with a known vidio card issue and I need to edit Edgy's X11org.conf but cant get in via safe mode (no safe option to select at boot for some reason)... gedit /etc/X11org.conf at boot cli will not work...is there a way to edit this file at boot using cli?

---

### Post by skwillz on 2006-10-17
are you doing this?

sudo gedit /etc/X11/xorg.conf

what you currently have is incorrect.

---

### Post by squibT on 2006-10-18
Yes from the command line at boot..not GUI...Is gedit a GUI?...error message is like it cant open a GUI.....

I got Edgy to boot into the Gnome GUI all the way after many tries...usually just got a black screen and no cursor. I then did this:

sudo gedit /etc/X11org.conf

gedit opens this file but is is blank...no entries at all. The posting I followed said to open this file and enter under the Device section:

Option "BusType" "PCI"
Option "DmaMode" "None"

Since the file was empty I added a [Device] section myself. No GUI problems now. Every reboot my video card works fine. Is this just a fluke??? Or did I really fix this problem? Got the info from ThinkWiki. Evidently the IBM T20 video card and Ubuntu has issues....](*,)

I think it was a fluke. Fresh install of Dapper and a search for X11org showed me /etc/X11/xorg.conf...
I added the Options below based on a HowToo...

Section "Device"
	Identifier	"S3 Inc. 86C270-294 Savage/IX-MV"
	Driver		"savage"
	BusID		"PCI:1:0:0"
 Option		"BusType"	"PCI"
 Option		"DmaMode"	"None"
EndSection

Seems to work...no more black screens when restarting Dapper....yet...

---

