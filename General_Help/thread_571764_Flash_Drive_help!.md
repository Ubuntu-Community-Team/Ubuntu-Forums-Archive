---
title: "Flash Drive help!"
date: 2007-10-09
forum: General Help
---

### Post by IllegalCharacter on 2007-10-09
Hi, I'm trying to get my USB drive to work under Ubuntu, however I'm having difficulties. It used to work, but one day decided to stop working. I tried it on a Windows PC and it is recognized fine, chkdsk gives no errors and I can read/write easily.

When I plug it in, dmesg pops out a bunch of junk like this:

...
[56695.855815] usb 2-3: reset high speed USB device using ehci_hcd and address 8
[56710.960291] usb 2-3: reset high speed USB device using ehci_hcd and address 8
[56716.075681] usb 2-3: reset high speed USB device using ehci_hcd and address 8
[56719.138007] sd 6:0:0:0: SCSI error: return code = 0x00050000
[56719.138012] end_request: I/O error, dev sdb, sector 4095807
[56719.138018] Buffer I/O error on device sdb1, logical block 4095744
[56719.138025] Buffer I/O error on device sdb1, logical block 4095745
...

and the light on the USB drive goes crazy. Eventually it will stop flashing and lsusb tells me this:

Bus 002 Device 008: ID 0457:0151 Silicon Integrated Systems Corp. Super Flash 1GB Flash Drive

which unfortunately is not the correct brand or size (mine is an OCZ 2GB drive).

I've checked the fstab, I don't have anything for the USB drive in there and when I try to manually mount the drive, it just hangs. I've tried with all the USB ports on my system, including the ones that work with my other hardware (like keyboard, mouse, etc.). Any suggestions?

---

### Post by Phearicle on 2007-10-10
I just wanna say that It may be a faulty usb port.

---

### Post by tgalati4 on 2007-10-10
What is the physical condition and age of the flash drive.  If it was worn as part of a keychain, then pocket wear can cause the USB dongle to become loose and develop small cracks in the solder junctions that connect it to the USB jack.

Flash does go bad sometimes.  Try to recover your data and reformat.  It it's within warranty, then send it in for replacement.  If it's out of warranty, then do a google search for ways to revive a flash stick.  Then summarize the more amusing techniques.

Find your oldest computer with USB.  Boot with Damn Small Linux.  Try to mount your USB stick to read the data.  Older computers have USB 1.1 which is slower and sometimes reduces errors when a flash drive is acting wonky.

---

### Post by IllegalCharacter on 2007-10-10
> **Phearicle]I just wanna say that It may be a faulty usb port.[/QUOTE]
As I mentioned before, I tried with several USB ports and ruled out that as the problem  said:**
> What is the physical condition and age of the flash drive.
You're probably right, it is a bit old and I used to carry it around in my pocket. I do find it strange that it works in Windows and not Ubuntu though - fortunate that it does, since now I can copy all my data off it. Thanks.

---

