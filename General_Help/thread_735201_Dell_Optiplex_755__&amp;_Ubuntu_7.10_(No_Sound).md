---
title: "Dell Optiplex 755  &amp; Ubuntu 7.10 (No Sound)"
date: 2008-03-25
forum: General Help
---

### Post by SLK55_AMG on 2008-03-25
I have tried all the various methods, and I am never able to get sound working.


It's using the onboard audio, nothing comes out, not from the internal speakers, and not headsets when plugged into the jack in rear or front panel.



Frustrating, any type of commands or logs anyone would like me to type/paste here?


cat /proc/asound/card0/codec#* | grep Codec
Codec: Analog Devices AD1984
bleh@postgreeskwill:~$ 


does this help any where I need to go?


82801I (ICH9 Family) HD Audio Controller , is what is on this mobo/chipset.

---

### Post by SLK55_AMG on 2008-03-25
Dell OptiPlex 755 System BIOS
BIOS
Release Title:	BIOS: Dell OptiPlex 755 System BIOS, English, OptiPlex 755, A08
Release Date:	2/21/2008
Criticality:	Optional
Description:	OptiPlex 755 System BIOS

By downloading, you accept the terms of the Dell Software License Agreement.

File Name	File Size	Download Time (56K)	File Format
O755-A08.exe	2 MB	5 min	Windows/DOS
	
Download Now
	
	Add to My Downloads
	
	
FTP Download

	Other Versions

Criticality
Optional  Dell recommends the customer review specifics about the update to determine if it applies to your system. The update contains changes that impact only certain configurations, or provides new features that may/may not apply to your environment.

Additional Information
No information available.

Important Information
No information available.

Fixes and Enhancements
1. Added 848x480 video mode to onboard graphics
2. Improved AHCI support with small hard drive partitions
3. Add support for new CPUs
4. Improve Linux support
5. Restore TxT support
6. Update Imageserver to version 4.5
7. Improve CD boot attempt logic on some drive models
8. Improve OS licensing handling
9. Allow flash program to work in Windows PE
10.New Intel Processor Microcode Updates



Currently I am at A01, this is bios to A08

notice #4, "improve linux support"

will get back with you all if this addresses any soundcard related issues.

---

### Post by mcobit on 2008-04-28
Hello, i had the same problem.

When you open the alsamixer and add the output 'mono' and pull up the volume, you will get sound through the internal speaker, but I cant test this with headphones.

MfG
Martin

---

### Post by Tobbera on 2008-07-12
[SIZE="5"][COLOR="Red"]mcobit[/COLOR] [/SIZE]Thank You!

---

### Post by johnystevenson on 2008-07-12
hi there

i have a similar 755 and have found the sound works good with 7.10 and hardy, with the difference being i purchased a cheap hd radeon 2400 pro. The only other difference i can see is the bios revision is up to A010

---

