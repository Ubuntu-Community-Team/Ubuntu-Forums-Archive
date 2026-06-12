---
title: "Simple scan problem"
date: 2015-02-15
forum: General Help
---

### Post by asb3 on 2015-02-15
I have simple scan 3.1.12 installed on a computer running Ubuntu 14.04.1 LTS. I have two scanners connected to the computer: an epson perfection 1640su and an hp photosmart c4280.  I used to be able to scan reliably on both scanners.  I can still scan on the hp, but the epson is erratic; sometime it scans, and other times the "moving dark circle" screen continues for a long time, even hours, without scanning starting.  I thought this might be a cable problem but the epson works fine with the same cable plugged into a windows machine.

Any ideas?

Alan

---

### Post by pdc on 2015-02-15
Hi; sorry to hear of your problems; probably hard to think of all the questions someone else might ask you but if you can help us with: 

how long have you been on 14.04; are you using 32bit?

what drivers did you install for the Epson? In what order did you install them?

___________________

there seem two ways of driving this scanner:

a) open-source software or b) Epson software;

the sane site (open-source) lists only the **1640XL** and says support there is good, and its ID as > 0x04b8/0x0109.............you could tell us what you get from ```
lsusb
```

______________________

my take on how to get a 1640SU from the Epson site would be: 

1) [COLOR="#008000"]iscan-data_1.35.0-1_all.deb[/COLOR] which must be installed first

2) [COLOR="#008000"]iscan_2.30.1-1~usb0.1.ltdl7_i386.deb[/COLOR] or [COLOR="#008000"]iscan_2.30.1-1~usb0.1.ltdl7_amd64.deb[/COLOR]

Epson provide their own programme Image Scan! for Linux and it drives their scanners well 

.......

---

### Post by dragonfly41 on 2015-02-15
> I thought this might be a cable problem but the epson works fine with the same cable plugged into a windows machine.

I have Simple Scan 3.12.1 installed on Ubuntu 14.04 .. but I've never been able to scan on my Canon LiDE snanner
.. which works fine on my Windows (dual boot) with same cable and USB port.

I've read that I should be using an externally powered USB expander.  I don't know if this is your problem.

---

