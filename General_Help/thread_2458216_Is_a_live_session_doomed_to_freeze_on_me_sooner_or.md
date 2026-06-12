---
title: "Is a live session doomed to freeze on me sooner or later?"
date: 2021-02-19
forum: General Help
---

### Post by slaytanicprion on 2021-02-19
I've ran 18.04.5 and 20.04 on a 256gb usb 3.1 stick because I'm broke and all my 3 internal hard drives are either close to full, need partitions repaired and I already have 1 external SATA III hard drive on a hot swap dock and 2 typical external seagate drives. I only have 2 usb 3.0 ports on my desktop, the motherboard is a bit old, but it still can run my pretty powerful amd fx 8350 black edition (running at 4.2ghz x 8, it would be 4ghz normally but I have one huge cooling tower over it). So I boot from a usb 3.0/3.1 extension that has power on/off buttons (those Seagate externals with no power switches is just bad design, they should all have power switches, that's why I bother with SATA III and the dock, I can turn off, remove the 2TB WD blue drive there and put on another). But I think I might be giving my 500 watts power supply (high quality, but it's 4 years old now), I always wanted to buy the 660 watts they had in the store but the guy convinced me that 500 watts was enough.

Well back then I didn't add a floppy bay replacement for extra usb 2.0 ports (my mobo has 12 in the back but 8 others), it can work without plugging it in, relying on the power supply, but it also has a male molex power input, but I didn't have the wiring to give it extra power. So that's 8 total added usb ports, 3 which are used with drives, one is the ubuntu 20.04 usb stick, the others the seagate expansions and also another drive connected to the SATA III port I also added to my desktop tower.

All this to say, I used to be able to run off a 64gb usb stick (until it got not very stable) 18.04.5 ubuntu mate for months on end on a live session. But not so much anymore with 20.04, it'll tough out a week or two then the gui will freeze. I'll be able typically to do ctrl+shift F1 to see what's going on, sometimes seems like there was a memory problem (lots of ffffff8823 and such hexadecimal errors, I'm certainly no pro out on that deep of a subject), I'll be able to to do the same with F2, F3, and get myself obviously impossible to get in logins, root password is unknown and for good reason. I can get back to the frozen gui (often the mouse still works but everything else's gone) with ctrl+shift+F7 but there's nothing I can do.

Yes, I am lazy and should install it. I have to bring back a 1TB drive whose partition deleted itself once when I had a real hard freeze when the screen went to black and a frozen cursor was there and that was it. I had noticed ubuntu mate had trouble (it was lagging) when mounting that internal drive. But my computer sees it, but it's an NTFS partition, I took all of it that I could with Testdisk, almost lost nothing and what I lost I can get back from my XL Blu-Ray backups (yeah I still use an optical drive burner, definitely need it for my music collection, I'd go mad losing all of that. Once I get back the partition/disk, I don't have win7 anymore since it became useless so I'm stuck to using old tools like Hiren's Boot to get the mini winxp in there to do a chkdsk on the drive,but the utilities are old (2013 or such), and they don't help me like only testdisk seems able to, they just say Bad Disk. Gparted tells me to do chkdsk on it, well, nope, I can't do that. I don't know what's better, bringing back an empty partition from it with testdisk or gparted (Attempt Data Rescue fails but I already took care of that with testdisk).

tl;dr Used to be able to run 18.04.5 on a usb stick of lesser quality and smaller size (64gb) for months on end on a live session (record is 4 month, only interrupted by power failure in my town) last fall, now a high quality 256gb usb stick always ends up crashing sometime after a week or two, so, is a live session doomed to crash eventually? It's really frustrating to have to reinstall all my software and own tweaks.

---

### Post by TheFu on 2021-02-19
Use **mkusb** for flash drive installs that allow updates.  Eventually, the updates will lead to an unstable system, but Linux needs to be patched weekly if it is connected to any network.

As for flash drives.  I've found no repeatable method to determine what is and isn't a quality flash drive for any specific ports.

There is little need for lots of power, unless you have a powersucking GPU.  Most HDDs use 6W normally and perhaps 2x that at startup.  500W in a PSU should handle 350W of need.  Remember, power is RMS, so hooking up so many devices that you are above about 2/3rds of the peak rated power is asking for problems.  The USB on a motherboard will have a limited amount of power it can push out.  They certainly aren't designed to support 6W on every port, concurrently.  If external storage supports external power, USE IT!!!

The only way to fix Windows file systems is with a Windows OS.

If you don't want to lose data, have backups that you 100% know can be restored. I have very little compassion for people who lose data due to lack of backups.  People with multiple disks, yet no backups are the worst.  I know. I was one of them 20 yrs ago.  Then I lost 80% of my data. If you need testdisk or photorec, then you've failed.

How about less explaining and more facts?  
What does a full **inxi -Fxxxz** show?
What do the log files show?  

Facts.

---

### Post by slaytanicprion on 2021-02-19
would an inxi with the parameters you've given tell me anything about a flash drive session that's gone forever?

I agree with you, like I said, I had most of everything backed up and what I didn't, testdisk brought back easily. Just weird that I can't be that long on a live session. Especially since one time it resulted in an internal drive deleting its own partition when it *really* froze, with the black screen and frozen cursor of death. Maybe the usb 3.0 extension is getting defective (which adds 4 usb 3.0 port and is powered on its own, like my usb sata III/usb 3.0 dock) I rather use it with sata III, speed is a little slower but much more stable. The internal disk that was the destination for where I wanted to install 20.04 MATE, of course, it had to be that one, not the 200gb WD from 2006 first generation SATA I got that will just not die, shows how they reduced quality of drives for quantity, it had to be that Seagate ST1000DM003-1CH162 1TB I bought 3 or 4 years ago. Now that I got what I need from it with testdisk, I'm ready to format it to ext4, just not sure with what to do it, testdisk or gpart, either way that will demand a reboot.

I just noticed that booting sometimes just fails and I have to turn off the power supply, wait 10-20 seconds, then turn it back on. So I suspected I was nonetheless taking too much power from my PSU. My GPU is a Radeon HD 7870, getting borderline old. So I was wondering, is it me overusing the PSU, despite having my usb 3.1/3.0 extension ports having its own power cord, as well as for the SATA III dock or it's just unrealistic to think you can run a live session like you can with a real hard drive install. I was just about to do it when that drive's partition quit on me. I'll give you the results of that inxi nonetheless when I get back home...

Thanks.

---

### Post by Impavidus on 2021-02-19
On a live system with persistence you can install upgrades, but still no kernel upgrades. I don't think I ever used a live session longer than 2 hours, to change some partitions on my hard drive. They are really meant for testing, fixing things if broken, partitioning and installing. They also have some use as secure, portable systems.

---

### Post by TheFu on 2021-02-19
I used a live session for about 4 days after the OS disk crashed and I waited for a replacement to arrive last July.  It didn't have too much extra installed, just enough to provide access to the normal stuff that box did. It was a media and NFS server for the network.  There was some media on the OS drive, so I connected the backup drive read-only to the Live session to make the media available without risk of me doing dumb things.

I use a live session for online banking, but it gets run inside a virtual machine for about 20 minutes every 2 weeks. No persistence, since that would break the rules for online banking.  [https://krebsonsecurity.com/online-banking-best-practices-for-businesses/](https://krebsonsecurity.com/online-banking-best-practices-for-businesses/) explains more. When doing payroll for all the people in the business, I really don't want to take chances for having credentials stolen.  In the US, business bank accounts don't have bank insurance protections like accounts for individuals. If the money gets stolen, the business is out that money, period.

---

