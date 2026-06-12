---
title: "Primary screen not showing up in Gnome Color"
date: 2015-11-10
forum: General Help
---

### Post by bach on 2015-11-10
I am running Ubuntu Gnome 15.10 64 bit, kernel 4.2.0-18 (fresh install). My computer's primary screen is not listed in the Gnome color manager. It only lists my printers. colormgr get-devices only return a list of my printers as well. A screenshot can be viewed at 

[https://dl.dropboxusercontent.com/u/2171814/gnome-color-manager.png](https://dl.dropboxusercontent.com/u/2171814/gnome-color-manager.png)

Hardware: DELL XPS 13 (2013 model) notebook, Intel GPU. 

Suggestions are welcome.

---

### Post by bach on 2015-11-10
cribari@darwin3:~$ colormgr get-devices
Object Path:   /org/freedesktop/ColorManager/devices/cups_HP_LaserJet_P3010_Series
Owner:         root
Created:       novembro 10 2015, 06:24:46 
Modified:      novembro 10 2015, 06:24:46 
Type:          printer
Enabled:       Yes
Embedded:      No
Model:         HP LaserJet P3010 Series
Vendor:        Hewlett Packard
Serial:        BRBHB6F720
Format:        ColorSpace.MediaType.Resolution
Scope:         temp
Colorspace:    gray
Device ID:     cups-HP-LaserJet-P3010-Series
Profile 1:     HP-LaserJet-P3010-Series-Gray..
Metadata:      OwnerCmdline=/usr/sbin/cupsd -l 

Object Path:   /org/freedesktop/ColorManager/devices/cups_HP_LaserJet_Professional_P1606dn
Owner:         root
Created:       novembro 10 2015, 06:24:46 
Modified:      novembro 10 2015, 06:24:46 
Type:          printer
Enabled:       Yes
Embedded:      No
Model:         HP LaserJet Pro P1606dn
Vendor:        Hewlett Packard
Serial:        000000000RL136FTPR1a
Format:        ColorSpace.MediaType.Resolution
Scope:         temp
Colorspace:    gray
Device ID:     cups-HP-LaserJet-Professional-P1606dn
Profile 1:     HP-LaserJet-Professional-P1606dn-Gray..
Metadata:      OwnerCmdline=/usr/sbin/cupsd -l 
cribari@darwin3:~$ colormgr get-devices-by-kind display
cribari@darwin3:~$

---

### Post by kryten35 on 2015-11-10
As i understand it to calibrate a monitor you need to buy a monitor calibration tool like Pantone Huey Pro or Spyder 3 to create an ICC /ICM profile for it.That profile can then be used to get your video card to output color in the way specified by it.  Monitor doesnt show as you need to generate a profile for it.

---

### Post by bach on 2015-11-10
I do have a calibration tool (ColorHug) and I do calibrate my monitors. Regardless of that, however, my primary screen should be listed in the Gnome color manager. I have a second notebook that runs Fedora 22 and Gnome 3.16. The two computers are DELL XPS 13 notebooks (2013 and 2015 editions, respectively). Screenshots: 

Ubuntu Gnome 15.10: [https://dl.dropboxusercontent.com/u/2171814/gnome-color-manager.png](https://dl.dropboxusercontent.com/u/2171814/gnome-color-manager.png)

Fedora 22: [https://dl.dropboxusercontent.com/u/2171814/gnome-color-manager-2.png](https://dl.dropboxusercontent.com/u/2171814/gnome-color-manager-2.png)

Notice the difference. The Gnome color manager in Ubuntu Gnome should include the "Laptop Screen" entry (as does the Fedora 22 Gnome color manager).

---

