---
title: "Lubuntu PC turns off cold randomly"
date: 2015-01-09
forum: General Help
---

### Post by secuono on 2015-01-09
https://m.facebook.com/phoneacquire/?source=m_mobile_mirror_interstitial&refsrc=http%3A%2F%2Fwww.google.com%2F&refid=8&_rdr


Pic of my pc above.
 PC I use is old, compaq for gaming basic factory stuff from 2005.
I have an older Lubuntu on it, only OS I use and have on it. 
This week, I started noticing that the PC is off when I leave it for a few hours or for the night.
It took a day the first couple times, then less and less time before it shuts off on its own. I was using it earlier today and it turned off cold turkey on me, as if the power went out or someone unplugged it. It was off 30min before this latest failure.
I'm not using anything that needs a lot of recourses, just one forum I was typing in when it died. 
There is no warning, no pop up, no noise from the machine, nothing. There is no lag in loading pages either. 
Haven't installed anything or downloaded anything for a long time. 
How do I check the hardware to see if that's the issue? What else could be the problem?

---

### Post by Yellow Pasque on 2015-01-09
It could be overheating (monitor the CPU temp). When's the last time you cleaned it out? It wouldn't hurt to open it up and use some compressed air to blow it out (especially the CPU heatsink). Before you close the case, turn the system on and make sure the fans are running (including the PSU fan).

---

### Post by secuono on 2015-01-09
I keep the side off. With any linux on it, it always tells me 1 fan has failed, but all spin, could never get the error to be fixed, gave up a long time ago. =/
I'll clean out any dust and report back. 
Thanks.

---

### Post by mörgæs on 2015-01-10
Overheating is a possible cause but you could also see if a newer BIOS is available.

---

### Post by Yellow Pasque on 2015-01-10
> **mörgæs said:**
> Overheating is a possible cause but you could also see if a newer BIOS is available.

I'm not sure if I would be comfortable running a BIOS update on a machine that randomly shuts off. From the description of "less and less time before it shuts off on its own" it made me think overheating or dying PSU. 

It might be helpful if we knew the model of machine (a pic is not a substitute for good information and the OP gave some broken, weird facebook link asking for a phone number anyway).
```
sudo dmidecode -t bios
sudo dmidecode -t system
```

---

### Post by secuono on 2015-01-10
Don't know why the picture link isn't working. I'm using my phone, so that's why it's a weird link, but don't know why it asks for a number. =/

Everything was fairly clean. Removed what dust there was.
PC stayed on for a day and a half, then turned off. 
I don't know how much more clean I could get it. 

What info about the PC do you need?
It's a 2005 compaq presario. 
HD 250GB
1024MB memory
AMD Athlon 64 processor 3800+
integrated NVIDIA GeForce 6150 LE

---

### Post by secuono on 2015-01-10
[PHP]dmidecode 2.11
SMBIOS 2.4 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: Phoenix Technologies, LTD
	Version:  3.11
	Release Date: 09/19/2006
	Address: 0xE0000
	Runtime Size: 128 kB
	ROM Size: 512 kB
	Characteristics:
		PCI is supported
		PNP is supported
		APM is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		5.25"/360 kB floppy services are supported (int 13h)
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 kB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		LS-120 boot is supported
		ATAPI Zip drive boot is supported
		BIOS boot specification is supported
		Function key-initiated network boot is supported
		Targeted content distribution is supported
	BIOS Revision: 3.11

Handle 0x0034, DMI type 13, 22 bytes
BIOS Language Information
	Language Description Format: Long
	Installable Languages: 3
		n|US|iso8859-1
		n|US|iso8859-1
		r|CA|iso8859-1
	Currently Installed Language: n|US|iso8859-1
[/PHP]


[PHP]dmidecode 2.11
SMBIOS 2.4 present.

Handle 0x0001, DMI type 1, 27 bytes
System Information
	Manufacturer: Compaq Presario 061
	Product Name: EX325AA-ABA SR1950NX NA670
	Version: 0nx1411RE101NAGA200
	Serial Number: CNX62208KS
	UUID: 805C544B-835D-1110-A387-D7114F3AE6C3
	Wake-up Type: Power Switch
	SKU Number: EX325AA#ABA
	Family: 103C_53316J

Handle 0x003F, DMI type 32, 11 bytes
System Boot Information
	Status: No errors detected

Handle 0x0041, DMI type 12, 5 bytes
System Configuration Options
	Option 1: 0011D80000B0445F
[/PHP]

---

### Post by mörgæs on 2015-01-11
Which older Lubuntu are you using? 
There are only two supported versions, 14.04 and 14.10. If you don't have one of these then you should begin with a fresh install.

---

### Post by secuono on 2015-01-11
Old, 10 or something. 
Can't upsate while having shut off issues.
Millions of reasons as to why I  haven't kept up with updates. Not going to get into that, though.

---

### Post by mörgæs on 2015-01-11
Thanks for not posting. We wouldn't like to see a post with a million lines of text.

Few people would bother giving advice for obsolete software. Your best option is trying 14.* in a live boot and install if it's stable.

---

### Post by Yellow Pasque on 2015-01-11
Compaq/HP doesn't have any BIOS updates for your model, assuming this is it: [http://h10025.www1.hp.com/ewfrf/wc/product?cc=us&lc=en&dlc=en&product=3184153](http://h10025.www1.hp.com/ewfrf/wc/product?cc=us&lc=en&dlc=en&product=3184153)

Other than swapping hardware, there's not much you can do here. Perhaps you could run memtest to check the RAM, or if you're sure the CPU is adequately cooled, you could let the machine sit at the BIOS screen overnight and see if it shuts off (ruling out any problems with OS/software).

---

