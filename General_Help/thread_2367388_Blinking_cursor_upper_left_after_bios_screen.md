---
title: "Blinking cursor upper left after bios screen"
date: 2017-07-29
forum: General Help
---

### Post by dmbomer on 2017-07-29
Hardware specs
8320FX
970A-DSP3
32GB mem
Kingston black 120 SSD
Sapphire R7-370 nitro video card
Evga 850 power
Deckink mini recorder
usb card VIA

Over the past 2 years with 3 different distro's Jessie, Arch, Ubuntu-Studio every blue moon the system would not boot after the BIOS screen.  Just a blinking cursor in the upper left corner.  

Before this event occurs on every shutdown the system would flash a black screen with writing in the upper left corner about orphan node.  This behavior happens a few times before the system stop booting the OS.  Than I would have to install a fresh copy of the OS on the system.  

Anyone out there have any ideas?

---

### Post by Autodave on 2017-07-29
Kinda sounds like a HD problem. If it were a spinning disc HD, I would go after that first. However, it is kinda rare to see a SSD act that way. Not impossible, just rare. Still sounds like a HD issue.

---

### Post by dmbomer on 2017-07-29
I narrowed it down to the motherboard and SSD.  I needed a second opinion.  Only reason why I was thinking the board is due to the fact I can't clear the cmos.  I removed the battery but all the settings remain.  Right now the system is working.  Thank you for the info Autodave.

---

### Post by dmbomer on 2017-08-05
System died again changed out SSD up and running again for now.

---

### Post by dmbomer on 2017-09-04
I'm now starting to think the motherboard is having issues.  The original hard drive is now in a macbook pro mid 2012 model and its been running fine for the past 3 weeks.  Performance is as it should be for a SSD.  Only time will tell.

---

### Post by Bashing-om on 2017-09-04
dmbomer; a thought ;

SSDs require AHCI - Advanced Host Controller Interface - .
Check in bios a that the SATA mode is set to AHCI .

[INDENT][INDENT]maybe this
[INDENT][INDENT]could be that
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by dmbomer on 2017-09-05
Thank you Bashing-om I will take a look.

---

### Post by dmbomer on 2018-04-06
It was me installing packages from different sources and performing update anytime they came out.  I have limited the updates and the system appears to be fine.  The HD I thought was a problem works fine in a MAC book pro no issues.

---

### Post by Bashing-om on 2018-04-06
dmbomer; :)

Good to hear

[INDENT][INDENT]good work done dirt cheap
[/INDENT][/INDENT]

---

