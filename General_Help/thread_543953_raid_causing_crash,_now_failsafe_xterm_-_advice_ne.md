---
title: "raid causing crash, now failsafe xterm - advice needed"
date: 2007-09-05
forum: General Help
---

### Post by cambie on 2007-09-05
Here's my situation. I built an AMD 64bit Athlon based system recently and installed Ubuntu 64bit on it. Here's the hardware involved.

Gigabyte GA-M61P-S2
4 x 1GB OCZ Platinum Rev2 DDR2 800 
AMD Athlon 64 x2 4600+
3 400GB Seagate 7200.10 in a software RAID 5 array for storage
1 40GB older Seagate drive for my OS drive.

The latest updates for Feisty 64bit are installed on the machine, and it's been updated on a regular basis. Last week sometime, the machine began randomly freezing hard. I could find nothing in my logs that indicated a problem. I kept rebooting and the machine would boot up fine, but it would freeze again within a few minutes. Finally, I realized that it was resyncing my array when booting up, and decided to pull one of my disks out of the RAID 5. This prevented it from doing any syncing, and the machine was again stable. But anytime I tried to add this disk back into my RAID array, the machine would crash when it got around 20 or 30% done. 

I had to leave this alone while out of town this weekend, turned the machine off while out, and came home to give it a shot again. I decided I was going to try rebuilding the array in single user mode. This was looking good, I got all the way to about 50% of a rebuild, and then froze hard. But this time, on reboot, Ubuntu didn't load all the way. It seemed to be missing binaries it needed in startup. I power cycled again and got a grub 17 error. 

At this point, I stuck the Ubuntu installer disk in and used it to run an fsck on my os disk. This found lots of errors, I let it fix them all, and rebooted as normal. All looked good until I tried to log into gnome. I am now getting stuck into a failsafe xterm because gnome-session is failing to load. 

I'm lost. Does anyone have advice? i want to first get my desktop back, and then try to get this raid array rebuilt in this box. I should note that I've already got it online in a Fedora Core 7 box, fully synched back up and running great.

---

### Post by cambie on 2007-09-05
I am going to go ahead and add that I think the crash on rebuild is due to heat in the drives. I've run smartctl -H on the drives from the RAID array while in the other Fedora box, and see that the the Temperature_celsuius thresheled seems to have been met in the past. I see one of the drives actually failing now. I guess I've got a heat problem. Perhaps I shouldn't have thrown the entire 400GB into one chunk.

---

### Post by cambie on 2007-09-06
Alright, since no one else wants to help, I am doing my best on my own. This has to be a heat issue. I want to get smart monitoring working properly now, but cannot. This is what I see on my 400GB sata drives.

$ sudo smartctl -i -d ata /dev/sdd
Password:
smartctl version 5.36 [x86_64-unknown-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     ST3400620AS
Serial Number:    5QH0J52B
Firmware Version: 3.AAK
User Capacity:    400,088,457,216 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Thu Sep  6 09:57:10 2007 CDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

Error SMART Status command failed
Please get assistance from [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)
Register values returned from SMART Status command are:
CMD=0x50
FR =0x00
NS =0x00
SC =0x00
CL =0x00
CH =0x00
SEL=0x00
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.


But my other 40GB drive works fine and gives no errors. I'm guessing because it IS in the smartmon database. But  my newer 7200.10 drives aren't. Any help with this one? or getting gnome back up? I've noticed that I can start gnome just fine from my failsafe xterm session but executing gnome-session. But that's less than ideal. How do I fix my login session?

---

