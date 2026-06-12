---
title: "Printers recommended and compatible with Ubuntu"
date: 2007-05-21
forum: General Help
---

### Post by stchman on 2007-05-21
Hello all, I would like to get a thread going to recommend what are the best printers with Ubuntu.  I can safely add the following printers as they work out of the box with no fuss for both Edgy and Feisty:

HP Laserjet 2605dn
HP Laserjet 4050tn
HP Laserjet 4L
HP Laserjet 5L
HP Laserjet 6L

Ok, I like HP laser printers.

I was really surprised that when I upgraded to Feisty (clean install) that Feisty detected my LAN printers.  WOW, windows I had to install a bunch of software and configure ports.

If there is another thread or some website with printers that Ubuntu are most compatible with please direct me to it.

Thanks.

---

### Post by ghell on 2007-05-21
There is probably a compatibility list for cups somewhere. My cheapo esys printer (its really a HP Something 3920) works fine on ubuntu.

On a sidenote, I have never had any problems with network printers in windows. I have used them out of the box with no problems ever on windows 95, 98, 98 SE, ME, NT4, 2000, XP and Vista :)

---

### Post by stchman on 2007-05-21
> **ghell said:**
> There is probably a compatibility list for cups somewhere. My cheapo esys printer (its really a HP Something 3920) works fine on ubuntu.

On a sidenote, I have never had any problems with network printers in windows. I have used them out of the box with no problems ever on windows 95, 98, 98 SE, ME, NT4, 2000, XP and Vista :)

I have had VERY few printers work out of the box with Windows.  Only my older laserjet 4L, 5L, 6L worked out of the box with XP.  The other printers required driver download and where applicable port creation/configuration.

I find printers to work with Ubuntu out of the box far better than 95/98/Me/2000/XP/Vista.

---

### Post by RedSquirrel on 2007-05-21
Here are some links to check for setting up a printer and checking compatibility:

[https://help.ubuntu.com/7.04/printing/C/printing.html](https://help.ubuntu.com/7.04/printing/C/printing.html)

[http://www.linuxprinting.org/](http://www.linuxprinting.org/)

[https://wiki.ubuntu.com/HardwareSupportComponentsPrinters](https://wiki.ubuntu.com/HardwareSupportComponentsPrinters)

---

### Post by snakedr on 2007-05-21
I purchased a HP OfficeJet 5610 in October 2006. The printer and scanner combo is very linux friendly. The main reason I purchased the printer was the scanner was linux compatible. 

Do a through online search once you decide on a printer model to see if there are any problems getting it to work on linux.

---

### Post by ghell on 2007-05-22
> **stchman said:**
> I find printers to work with Ubuntu out of the box far better than 95/98/Me/2000/XP/Vista.Well I obviously haven't tried every printer under the sun and as there are drivers for windows printers, obviously some printers can't just do with the generic drivers. Vista has gone leaps and bounds with this though and I have not found a single printer that I can't attach to vista and only be able to print after manual setup (again, I have not tried all of course, I have tried 6 or 7 from at least 3 manufacturers though). Networked printers should not be a problem either. Even if a printer needs manual installation on a machine it is physically connected to, networking generally abstracts away some of these problems and printers can generally be used on the network as soon as they are found (provided the print server is already set up, which now requires little to no effort)

Maybe there is a problem with HP Laserjets on Windows, since you seem to mainly use them. I have tried one on vista with no problems but I did have problems with an HP on 2003 (it wanted me to install their software, which didn't work on Windows Server 2003)

---

### Post by stchman on 2007-05-23
> **ghell said:**
> Well I obviously haven't tried every printer under the sun and as there are drivers for windows printers, obviously some printers can't just do with the generic drivers. Vista has gone leaps and bounds with this though and I have not found a single printer that I can't attach to vista and only be able to print after manual setup (again, I have not tried all of course, I have tried 6 or 7 from at least 3 manufacturers though). Networked printers should not be a problem either. Even if a printer needs manual installation on a machine it is physically connected to, networking generally abstracts away some of these problems and printers can generally be used on the network as soon as they are found (provided the print server is already set up, which now requires little to no effort)

Maybe there is a problem with HP Laserjets on Windows, since you seem to mainly use them. I have tried one on vista with no problems but I did have problems with an HP on 2003 (it wanted me to install their software, which didn't work on Windows Server 2003)

When I mean out of the box I mean that there is nothing to download.  All of the printers I use work with no downloads.  I have a laserjet1000 but it does not work out of the box with Ubuntu.  You have to compile drivers from foo2jz(sp?) and then the printer works.  I don't use the laserjet 1000 anymore.

I have not found a printer with Windows that does that for some time.  The older printers Windows will find and they work, the newer ones need drivers installed.  I have (2) network printers and Feisty found them.  Amazing.

---

### Post by seamuso on 2007-05-23
I have an HP C5180 (connected via its onboard print server only) that prints/scans  using the HPLIP (feisty) ..  All I really expected from the printer was to be able to print (was realy purchased for my wife to work with photos), the network scanning was an added bonus.

---

### Post by ghell on 2007-05-23
> **stchman said:**
> When I mean out of the box I mean that there is nothing to download.  All of the printers I use work with no downloads.  I have a laserjet1000 but it does not work out of the box with Ubuntu.  You have to compile drivers from foo2jz(sp?) and then the printer works.  I don't use the laserjet 1000 anymore.

I have not found a printer with Windows that does that for some time.  The older printers Windows will find and they work, the newer ones need drivers installed.  I have (2) network printers and Feisty found them.  Amazing.When *I* say out of the box, i mean not having to go and install a driver at all. My HP somethingjet 3920 was this simple to run on both vista and fedora (not tried using it in ubuntu yet, i assume it works as well as it did in fedora, when i turn my computer off it takes a while to disable HP services so I assume it is installed properly)

On XP:
- Plug it in to the USB
- get told that drivers could not be found
- find out that I have to install crappy HP printer software that only works on XP, not even windows server 2003

On vista, fedora and probably ubuntu:
- Plug it in to the USB
- Go to a file
- Press print
- Collect properly printed page

Asside from this HP rubbish about having to install their software (not just drivers) on XP (which is HP's fault a problem with windows), I have not had any problems getting printers to just work properly by plugging them in since Windows 95. This goes of course for parallel port as well as USB, I only have 1 USB printer (that cheapo £30 HP 3920)

---

### Post by stchman on 2007-05-23
> **ghell said:**
> When *I* say out of the box, i mean not having to go and install a driver at all. My HP somethingjet 3920 was this simple to run on both vista and fedora (not tried using it in ubuntu yet, i assume it works as well as it did in fedora, when i turn my computer off it takes a while to disable HP services so I assume it is installed properly)

On XP:
- Plug it in to the USB
- get told that drivers could not be found
- find out that I have to install crappy HP printer software that only works on XP, not even windows server 2003

On vista, fedora and probably ubuntu:
- Plug it in to the USB
- Go to a file
- Press print
- Collect properly printed page

Asside from this HP rubbish about having to install their software (not just drivers) on XP (which is HP's fault a problem with windows), I have not had any problems getting printers to just work properly by plugging them in since Windows 95. This goes of course for parallel port as well as USB, I only have 1 USB printer (that cheapo £30 HP 3920)

WOW, I just looked at HP's website and the DeskJet 3920 driver is a 45MB download.  There has to be an incredible amount of BS in that download.  Does the HP driver let you install JUST the driver for the printer in XP?  When I install the Creative software for Audigy cards in Windows there is an option to install just the drivers and not install the Creative control panel.

---

### Post by stchman on 2007-05-23
> **seamuso said:**
> I have an HP C5180 (connected via its onboard print server only) that prints/scans  using the HPLIP (feisty) ..  All I really expected from the printer was to be able to print (was realy purchased for my wife to work with photos), the network scanning was an added bonus.

What exactly does HPLIP do.  I have never investigated it.

Thanks.

---

### Post by ghell on 2007-05-24
As I said, on XP there was no option for just the driver. The software bundled was something to the extent of "HP Printing and Imaging Suite" and XP wouldn't let me just use a generic printer driver etc. Vista, however, let me plug the printer in, after a few seconds of "detecting new usb device" it was ready to use :)

---

### Post by seamuso on 2007-05-24
> **stchman said:**
> What exactly does HPLIP do.  I have never investigated it.

Thanks.

HPLIP is ...
[http://hplip.sourceforge.net/index.html](http://hplip.sourceforge.net/index.html)

> 
HPLIP is an HP developed solution for printing, scanning, and faxing with HP inkjet and laser based printers in Linux.
 The HPLIP project provides printing support for 1,151 printer models, including Deskjet, Officejet, Photosmart, PSC (Print Scan Copy), Business Inkjet, LaserJet, Edgeline MFP, and LaserJet MFP.



I celebrated when I saw it was included in feisty .. I had to build it for my LFS system and it was a b*tch and a half to get all of the dependencies sorted out.

has gui tools for setting up, interfaces with cups, works with sane/xsane.

here's a list of things ..

```
seamuso@bluebuntu:~$ hp
hp-align       hpijs          hplj1005       hp-print       hp-testpage
hp-clean       hp-info        hplj1018       hp-probe       hp-timedate
hp-colorcal    hpiod          hplj1020       hp-sendfax     hp-toolbox
hp-fab         hp-levels      hp-makecopies  hp-setup       hp-unload
hp-firmware    hplj1000       hp-makeuri     hpssd

```

and here's 6 images of the hp-toolbox ..
[http://info.bluefrogcs.com/images/hp-toolbox/](http://info.bluefrogcs.com/images/hp-toolbox/)

---

