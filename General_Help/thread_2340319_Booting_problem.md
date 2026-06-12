---
title: "Booting problem"
date: 2016-10-17
forum: General Help
---

### Post by Alxl on 2016-10-17
Laptop with dual boot :  win 10 (upgraded free fr Win 8)  and Ubuntu 16.04 lts.

I don't use windows much . But after an update months ago, booting became erratic : it always boots into Windows  but once in 2-3 or 4 tries does it boot into Ubuntu.

I tried Boot Repair but something went wrong and I had to reinstall Ubuntu.
Here is the latest boot repair report:

[http://paste2.org/eJMmbwdd](http://paste2.org/eJMmbwdd)

---

### Post by oldfred on 2016-10-17
What brand/model system?
Can you directly boot ubuntu entry in UEFI boot menu?

It looks like you left Windows fast start up on, which can cause issues.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)

---

### Post by Alxl on 2016-10-20
[I]What brand/model system?
[/I]Samtssung 3 NP305ESA-AO4US Laptop -AMD Dual-Core A4-3300M 1.9GHz 4GB DDR3 320GB HDD DVDRW 15.6 windows7 Home Premium 64-bit(upgraded to Win 10)[I]

Can you directly boot ubuntu entry in UEFI boot menu?
[/I]The boot menu only shows 1. Ubuntu 2.Ubuntu advanced (or something like that), and 3.Windows.
But in BIOS I can boot into UEFI boot menu[I]

It looks like you left Windows fast start up on, which can cause issues.
[/I]I cannot find "fast start" in bios

---

### Post by oldfred on 2016-10-20
UEFI has fast boot settings.
Windows has fast start up settings. They are different.

If originally Windows 7 probably system is BIOS, but a few Windows 7 systems were UEFI. Do you know?
Post this from live installer's terminal:
sudo parted -l

        SAMSUNG Series 3 NP365E5C-XXXXX laptops 
[http://ubuntuforums.org/showthread.php?t=2120763](http://ubuntuforums.org/showthread.php?t=2120763)

---

### Post by oldos2er on 2016-10-22
Thread moved to General Help.

---

