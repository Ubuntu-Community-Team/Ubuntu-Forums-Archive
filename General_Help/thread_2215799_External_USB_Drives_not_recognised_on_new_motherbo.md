---
title: "External USB Drives not recognised on new motherboard"
date: 2014-04-08
forum: General Help
---

### Post by Davey_Burgess on 2014-04-08
I had had enough of my older, slower computer, so I bought some parts and threw a new one together!  Clean install of Ubuntu, 13.04 upgraded to 13.10 and all updates installed, then attached my old Ubuntu hard drive as a slave and copied over my files, email, firefox preferences, etc. All is good!

The problem has arisen that I have data saved on older IDE hard drives, and this new motherboard doesn't have an IDE interface! No problem, I have that little USB adapter that can connect an IDE drive .... hmm, no drive detected!   Rebooted the old computer, tried it on there, and it works perfectly!  Back to the new one again, no drive detected in either the USB2 or the USB3 ports!

I also, with the new computer parts, got a USB 3.0 SATA drive dock, so I wouldn't have to keep cracking the case to work with a SATA drive - this isn't detected either!  The old computer doesn't have USB 3.0 or a spare PCI Express port to install one, so I can't check it there.

Both my cell phone, camera and USB thumb drives all work quite happily, as does my USB Bluetooth adapter. The problem seems to be confined to hard drives!  Does anyone have any suggestions?

The new motherboard is an Asrock 970 Extreme3 r2.0 running 16gigs of DDR3 RAM, with a 700 watt power supply and an Nvidia GEForce GT 630 video card.

LSUSB Shows the adapter: Bus 001 Device 004: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
/media shows no new devices
/dev does show the addition of SDC
'Disks' shows SDC as being connected to the USB bridge, but lists it as no media and only offers to power it off.
Unplugging the USB cable and plugging it straight into the old computer, the disk is readable!  The disk in question is a 300 gig Seagate Barracuda 7200 IDE

Any suggestions would be appreciated!

---

### Post by Mark Phelps on 2014-04-08
I know this is NOT supposed to make a difference, but check each of the IDE drives and make sure it is jumpered to "Master".  I had similar problems with a newer motherboard that as not IDE ports and had to do this to get the IDE drives recognized using a SATA adapter.

---

### Post by Davey_Burgess on 2014-04-08
Darn it, you're right - it's not supposed to make a difference, and darn it, you're also right in that it does!

Thanks for the quick response - I'll crawl back to my seat in the corner now! :)

---

