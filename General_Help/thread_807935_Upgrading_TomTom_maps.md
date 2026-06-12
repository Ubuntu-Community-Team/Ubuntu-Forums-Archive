---
title: "Upgrading TomTom maps"
date: 2008-05-26
forum: General Help
---

### Post by bobblehat on 2008-05-26
I was wondering if anyone had come across a way of downloading and installing new TomTom satnav maps via Ubuntu (or other Linux variants). TomTom's supported mechanism is an application called TomTom Home which only runs under Windows or Mac and according to their official help that's the only way to download maps. I can use it if needed but would ideally just like to download my paid for maps via something simple and standard like FTP or HTTP  and copy them onto the device or it's SD card.

As I understand it, the device itself runs a linux kernel but my reply from TomTom support says they don't support Linux desktop users. Any TomTom users out there who've solved this?

If it comes to it, I'd rather change my SatNav than change my OS but ideally I'd keep both :)

---

### Post by Handssolow on 2008-05-27
This is just a quick and early reply. I've just got the latest TomTomHOME2winlatest.exe running partially under Wine. Incidentally everyone should keep encouraging them to produce a Linux version of TomTom Home.

From memory there were a couple runtime errors during install which unfortunately I didn't note down. However, it seems to run and I can login to their web site. Hardy doesn't detect my TomTom but Ubuntu does. You can specify where updates are downloaded so perhaps there's some hope using Wine.

---

### Post by Handssolow on 2008-05-27
I'm sorry to report I've made no progress, I've even been going backwards. After a re-install of TomTomHome2 in an attempt to get my TomTom device recognised, TTHome2 now wont run. There's a Visual C++ Runtime library R 6034 error as there were during install.

It's a pity because I suspect that even if TomTom don't release a Linux version, I suspect that there's not much else needed to get it to run under Wine.

---

### Post by Handssolow on 2008-05-27
After following the information on this [link ](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10219)I've been able to re-install TomTom Home 2 but as others also report, the satnav device isn't recognised.

---

### Post by Zill on 2008-05-27
Not much help to the op but I have had a similar response from Garmin re my StreetPilot i3 satnav i.e. No Linux support :-(

It seems that some satnav manufacturers are still living in the stone age and fail to appreciate just how many of us don't use MS software.

Out of interest, has anyone found a satnav that *does* have Linux support?

---

### Post by bobblehat on 2008-05-30
Thanks for the effort here folks. If anyone does come up with a satnav with good Linux support I'd be interested to hear about it.

---

### Post by ocalld on 2008-06-05
> **Handssolow said:**
> After following the information on this [link ](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10219)I've been able to re-install TomTom Home 2 but as others also report, the satnav device isn't recognised.


I'm not sure that this entirely down to ubuntu/wine installed tomtom home.
I've been trying to get tomtom home v2 running in windows and it wouldn't see either my Palm based Navigator sd card or TomTomn Go.
Spent hours trying to get it working.

In the end i installed tomtom home version 1x and everything worked OK.

Try installing the 1x version with WINE and see if that works.
I found a copy on Torrent sites as TomTom no longer offer this for download.

got to admit, i tried loading a tomtom Go in Virtualbox XP guest - Ubuntu host. Ubuntu just couldn't detect the tomtom.

Cheers

---

