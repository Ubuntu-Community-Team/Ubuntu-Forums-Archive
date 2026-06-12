---
title: "Broadcom Help!"
date: 2008-06-08
forum: General Help
---

### Post by Exsecrabilus on 2008-06-08
I want to try to use my Broadcom B4318 wireless card using something other than System >> Administration >> Hardware Drivers.
I found the following quote about my wireless card from [here](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/) but now I don't know what to do.
There are four tests about my wireless card, which one do I follow and how?

> Card: Broadcom Corporation BCM4318 AirForce One 54g 802.11g Wireless LAN Controller (rev 02)
* Ndiswrapper version: 1.1-4
* Chipset name: Broadcom BCM4318
* PCIID: 02:03.0 (rev 02)
* Windows driver location: [http://biginoz.free.fr/linux/bcmwl5a.inf](http://biginoz.free.fr/linux/bcmwl5a.inf). Also need .sys file [http://biginoz.free.fr/linux/bcmwl5.sys](http://biginoz.free.fr/linux/bcmwl5.sys)
* Using Ubuntu 5.10 on Dell Inspiron 1300

Card: Broadcom Corporation BCM4318 AirForce One 54g 802.11g Wireless LAN Controller (rev 02)
* Ndiswrapper version: 1.11
* Chipset name: Broadcom BCM4318
* PCIID: 30:02.0 (rev 02)
* Windows driver location: [ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/winxp64bit/80211g.zip](ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/winxp64bit/80211g.zip) Driver: WL_Broadcom,XP64
* Using Fedora Core 5 x86_64 on HP Pavilion zv6000 with AMD64.
* Worked after adding &#8220;noapic nolapic acpi=off&#8221; to kernel command line obtained from
* [http://www.linuxquestions.org/questions/showthread.php?p=2132310#post2132310](http://www.linuxquestions.org/questions/showthread.php?p=2132310#post2132310)

Card: Broadcom Corporation BCM4318 AirForce One 54g 802.11g Wireless LAN Controller (rev 02)
* Ndiswrapper version: 1.21
* Chipset name: Broadcom BCM4318
* PCIID: 03:02.0 0280: 14e4:4318 (rev 02)
* Windows driver location (v6.00 rev. a): [ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe) This file can be extracted with cabextract and contains both 32 bits and 64 bits files. Also explanations are available here: [ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.html](ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.html)
* Works with boot noapic nolapic
* You may need to blacklist the default bcm43xx kernel module by adding it to the listing in /etc/modprobe.d/blacklist
* Using Mandriva Cooker x86_64 on HP ZV 6000 Sempron 3200+
* Tested using Sidux 2007-01 on Compaq V5105US

Card: Broadcom Corporation BCM4318 AirForce One 54g 802.11g Wireless LAN Controller (rev 02)
* Ndiswrapper version: 1.11
* Chipset name: Broadcom BCM4318
* PCIID: 00:0b.0 (rev 02)
* Windows driver location: [ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/winxp64bit/80211g.zip](ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/winxp64bit/80211g.zip) Driver: WL_Broadcom,XP64
* Other: Needs *.sys *.inf files in same directory but use BCMWL5A.INF for ndiswrapper driver install. Load ndiswrapper at boot up thanks to /etc/rc5.d file. [email]Antho.martin@gmail.com[/email] for more informations or questions.
* Using Fedora Core 5 x86_64 on Acer Aspire 5002 WLMI with AMD Turion 64.

Card: Broadcom Corporation BCM4318 AirForce One 54g 802.11g Wireless LAN Controller (rev 02)
* Ndiswrapper version: 1.22 and 1.23
* Chipset name: Broadcom BCM4318
* PCIID: 02:03.0 (rev 02)
* Windows driver location: [http://biginoz.free.fr/linux/bcmwl5a.inf](http://biginoz.free.fr/linux/bcmwl5a.inf). Also need .sys file [http://biginoz.free.fr/linux/bcmwl5.sys](http://biginoz.free.fr/linux/bcmwl5.sys)
* Using SuSE 10.1 on Dell Inspiron 1300

---

