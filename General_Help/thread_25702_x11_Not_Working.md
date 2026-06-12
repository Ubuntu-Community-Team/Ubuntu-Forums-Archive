---
title: "x11 Not Working"
date: 2005-04-10
forum: General Help
---

### Post by dem01 on 2005-04-10
Recently received my new disks from Shipit.  Wanted to try the Live CD first to see (1) how Ubuntu worked with my hardware, and (2) how it looked.  Booted up the CD.   Got the message "Undefined video mode."  This has not been a problem when I got it on Knoppix or PCLinux (Just hit "space Bar" and go on.)  Went on through bootup.  Hardware recognition messages were very positive. It even found SCSI and Firewire that I didn't know I had!   :-)   But then when it got to starting X11 message,  the best I have accomplished was that it went about 4 more messages, then through up about 1/2 of a screen of what I assume were error messages (came and went too fast to know), and went black.  No cursor, no nothing.  Tried several times with only minor variations in the outcome - no success.

Does this mean that I would be unable to use Ubuntu if I went ahead with the Install?  Am running an AthlonXP 1800, 256mb RAM, on an MSI mobo with a VIA chipset (don't remember the number). Video is an old S3Virge card (nothing fancy.)  I want to switch from Win98SE to Linux, and I had heard some very good things on Ubuntu, but I am a disabled person trying to supplement my pension check with some web site work, so I cannot afford (1) to buy other hardware, or (2) to have my computer down for an extended period while I figure this out.  Please advise. ](*,) 

TIA,
dem01

---

### Post by nad on 2005-04-10
At the boot prompt screen with the ubuntu splash, hit the F1 key for a menu of booting options. Try the noacpi option. ' live pci=noacpi ' This will ignore VIA pci mapping.

If that doesn't work try : ' live noapic ' (advanced power interface) , If still no go, there is expert mode, F3, which will prompt you for module install options.

Dan M

---

### Post by dem01 on 2005-04-20
None of the above settings worked so far.  I will keep playing with the "Expert" mode to see if something works out.  :???: .

dem01

---

