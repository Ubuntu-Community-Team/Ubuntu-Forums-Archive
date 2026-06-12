---
title: "Fiesty Beta Live CD Won't Boot"
date: 2007-03-30
forum: General Help
---

### Post by blazercist on 2007-03-30
Ok I have a MS-1039 laptop with hardware as follows:

Single Core Turion 64 mt-40 @ 2.2Ghz
2 Gigs DDR RAM
ATI x1600 mobility GPU
100 GB IDE HDD @ 5400 RPM
RT61 WIFI card (with hard on/off button)

So I downloaded and burned Fiesty Beta BOTH AMD64 and i386 versions.

Both versions give the following error: "soft lockup detected on CPU#0"

This occurs 97% of the time just after cupsd is loaded during boot, 2% of the time after gnome is loaded at boot and 1% of the time at the splash screen when nautilus loads up.

The CD works fine in my Desktop.  Also Edgy Eft 6.10 live cd works fine on the laptop.

---

### Post by blazercist on 2007-04-01
BUMP?

I've tried all the cheat codes, pci=acpioff noapic 

I've tried with the wifi card on/off, enabled/disabled usb in bios, with each cd, same thing, someone please tell me this is normal or there is a fix.  Just say something.

---

### Post by blazercist on 2007-04-05
Last time I'm gonna try to bump this thread.

I was greatly dissapointed today to find out that Herd 6 was cancelled and with it my chance to possibly get Feisty working.

I will have to wait 2 more weeks to burn the final release and gamble that my problem was inadvertantly fixed and it will boot and install properly.

UNLESS someone can actually maybe reply to this thread with a helpful suggestion.

---

### Post by mpadams on 2007-04-05
[http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/) Trying a nightly is usually for the bold, but considering how most of the bugs have been in individual programs vs Ubuntu itself, I'd give it a shot. In fact, I've been making a hybridized scripted install of Edgy with some Feisty packages for the last several months at my company. We use rdesktop, tinc, and CUPS extensively, and the older versions don't cut it.

---

### Post by blazercist on 2007-04-06
Thanks I'll try this when I get home from work.

---

### Post by blazercist on 2007-04-18
Upgrading from Edgy, booting into recovery mode and removing network-manager did the trick.  The daily had the same problem.

---

