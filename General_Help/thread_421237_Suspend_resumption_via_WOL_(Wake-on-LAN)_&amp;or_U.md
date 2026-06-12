---
title: "Suspend resumption via WOL (Wake-on-LAN) &amp;/or USB keyboard/mouse"
date: 2007-04-24
forum: General Help
---

### Post by StewD on 2007-04-24
Hi

I have (finally)  achieved resumption of my Ubuntu PC from suspension and hibernation by pressing the power button on my PC. A great step forward.

I now want to be able to resume using WOL (Wake On LAN), but am unable to....I assume that clicking on a Windows XP drive that is mapped to my Ubuntu box should trigger a wake up event? Ping doesn't work either (Request Timed Out.).  

I have "PCI Devices Power On" and "Ring-In Power On" both enabled in the BIOS under ACPI settings.

Less of a priority, but on a related note:  I can currently resume by pressing a PS/2 mouse button, but not a USB wireless mouse button or USB keyboard button? Any ideas on how to make these work - I know I can do this on my XP box!

Any ideas?

My hardware is :

[LIST]
[*]Intel Celeron D351 3.2 Ghz 775

[*]Asrock 775i945GZ i945 socket 775
extracted from asrock website: 
[INDENT]LAN[/INDENT]  	
[INDENT][INDENT]- Realtek PCI LAN 8101L
- Speed: 10/100 Ethernet
- Supports Wake-On-LAN
[/INDENT][/INDENT]

[*]160GB Maxtor DMAZ+10 SATA2

[*]512MB PC4200 Elixir DDR2

[*]NEC AD-7170A-0B 18x DVDRW DL
[/LIST]

Thanks for any help!

Stewart

---

### Post by qhartman on 2007-05-23
There are a number of things that can influence this. Check out these recent discussions on the Portland LUG email list that might provide you some insights:

Original thread: [http://search.gmane.org/?query=e100+wake+on+lan&author=&group=gmane.org.user-groups.linux.portland&sort=relevance&DEFAULTOP=and&xP=e100%09wol&xFILTERS=Gorg.user-groups.linux.portland---A](http://search.gmane.org/?query=e100+wake+on+lan&author=&group=gmane.org.user-groups.linux.portland&sort=relevance&DEFAULTOP=and&xP=e100%09wol&xFILTERS=Gorg.user-groups.linux.portland---A)

Resolution:
[http://article.gmane.org/gmane.linux.drivers.e1000.devel/1677/match=e100+resolved](http://article.gmane.org/gmane.linux.drivers.e1000.devel/1677/match=e100+resolved)

---

