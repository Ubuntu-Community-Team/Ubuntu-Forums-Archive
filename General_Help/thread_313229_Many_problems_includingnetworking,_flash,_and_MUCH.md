---
title: "Many problems including:networking, flash, and MUCH MORE!!!!!"
date: 2006-12-05
forum: General Help
---

### Post by jmon366 on 2006-12-05
I need help mith my dual booting dell deminsion 3000

I am not a newb who has no idea, but a newb who spends all night trying to fix something that is UN FIXABLE] (*,) 

Ok, first problem. My wireless usb network adapter.  I have done my homework before coming here to waste people's time, and get help, but I guess that is why you will be reading this. I have a Linksys WUSB54G V.2 adapter, and found a utility called Ndiswrapper, I have used the drivers from the cd for version 1, and 2, I have also used the drivers made for the chipset of the card, and of like modles. NONE WORK. I dont know if ubuntu plug-n-plays unknown device by saying "unknown usb device", or "Usb device" but It has not even thought of accepting it. the power light is on, on the device.... Im trying to stay saine about this 8) 

no.2 (combining of flash and java) They wont work. Period.  I have used add/remove programs, downloading from the adobe site, and a program called automatix. NONE WORK
Java I havent had time to fix, flash is screwed up.
:evil: 
no.3 
Rythembox wont play mp3's, the codecs arent there, I downloaded the lesser program, banshee,
works like a charm ;) 
no.4
(not a big one)
My ONLY other complaint about linux
IT TAKES FOREVER TO INSTALL SOMETHING
(and also, when it asks you to use terminal to extract something, what do you do?)




I hope I dont ditch linux before someone helps me, I LOVE IT, but the cons outweigh the pro's

Here is me until I get it fixed
](*,) ](*,) ](*,) ](*,)

---

### Post by IMELucky on 2006-12-05
Okay!

Lets get started here...
First, Flash, Java, and Mp3 are really easy to fix, but I imagine your internet would be the highest priority.

try typing this command:

iwconfig

and post the output. This will tell me if ubuntu can even detect your wireless adapter

Installing Java and Flash will depend on whether you are using Dapper Drake or Edgy Eft. Once I know what your using I'll walk you through installing these.

---

### Post by jmon366 on 2006-12-05
Edgey, and here is the output-
***@***-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

---

### Post by jmon366 on 2006-12-05
Im running a 50ft cable to my other room from my networking closet (it is a closet in another room :) ) and want poeple to stop triping on it!

---

### Post by IMELucky on 2006-12-05
Haha! Naturally. I hate running wires too!

First I'm following this guide which you can find here:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

The guide says that you can't use the drivers on your CD. I would use synaptic to do a complete removal of ndiswrapper and reinstall it. Then we'll work on configuring it.

The guide says to use the output from lspci to determine which driver you need to download.

type lspci from the terminal and post the output...then we'll go from there

---

### Post by jmon366 on 2006-12-05
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:01.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)



I dont think my adapter is from intel...

---

### Post by strabes on 2006-12-05
about the mp3 problem, see [this page](https://help.ubuntu.com/community/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29). Automatix will also install these things. 

For flash, download it [here](http://labs.adobe.com/downloads/flashplayer9.html) and just extract libflashplayer.so & throw it in ~/.mozilla/firefox/plugins/ to install for only yourself, or as root, extract it to /usr/lib/firefox/plugins/ to install systemwide.

---

### Post by jmon366 on 2006-12-05
I use oprea (with firefox) and that is my problem, I tried the installer for flash.....

---

### Post by adamkane on 2006-12-05
The first time using Ubuntu is always a little overwhelming/confusing. Every new Ubuntu install requires a little configuration to get things working. You get used to it after a while.

(To get amarok going, I have to install libxine, uninstall gstreamer, disable arts sound, install mysql, move audio files that amarok can't read to an alternate location, etc...)

---

### Post by jmon366 on 2006-12-05
amarokma is kde? I think it is, Im running gnome....

---

