---
title: "External Hard Drive not detected"
date: 2007-01-18
forum: General Help
---

### Post by garlito on 2007-01-18
Hi,
I've just bought an Airis usb external hard drive. It is supposed to be plug-and-play but when I connect it nothing happens and fdisk -l don't show the device. I think it comes without formating.

What could I do? Thanks in advance.

---

### Post by allwin on 2007-01-18
Check out your system log while you are connecting it.  You could also go into a terminal and type "dmesg", but you can display the system log under the menu that says PREFERENCES and ADMINISTRATIVE.  Maybe, reboot, then go into the system log display.  Make sure VIEW...MONITOR is checked;  go to the end.  Now plug the thing in and watch what messages are added to the bottom.  Perhaps they will indicate further things to look for.

BTW...I have posted here about my own USB problems several times and got NO RESPONSE...I have the feeling that USB issues are a "black hole of support" in UBUNTU...eg, when they say "it just works"  there is a little asterisk that says *Not USB right next to *Not wireless and *Not laptops...hehe

---

### Post by john_spiral on 2007-01-18
Try booting from Knoppix or Kanotix CDs both have very good abilities in detecting hardware.

Is any operating system seeing the drive?

---

### Post by garlito on 2007-01-18
Thanks for your help. I only use Ubuntu Dapper, no other operating system. I haven't got a knoppix here but this is what I've found in dmesg:

```
[17180108.452000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[17180108.720000] SCSI subsystem initialized
[17180108.752000] Initializing USB Mass Storage driver...
[17180108.756000] scsi0 : SCSI emulation for USB Mass Storage devices
[17180108.756000] usb-storage: device found at 2
[17180108.756000] usb-storage: waiting for device to settle before scanning
[17180108.756000] usbcore: registered new driver usb-storage
[17180108.756000] USB Mass Storage support registered.
[17180113.760000]   Vendor: SigmaTel  Model: MSCN              Rev: 0100
[17180113.760000]   Type:   Direct-Access                      ANSI SCSI revision: 04
[17180113.772000] usb-storage: device scan complete
[17180113.804000] Driver 'sd' needs updating - please use bus_type methods
[17180113.812000] SCSI device sda: 250624 512-byte hdwr sectors (128 MB)
[17180113.812000] sda: Write Protect is off
[17180113.812000] sda: Mode Sense: 03 00 00 00
[17180113.812000] sda: assuming drive cache: write through
[17180113.828000] SCSI device sda: 250624 512-byte hdwr sectors (128 MB)
[17180113.832000] sda: Write Protect is off
[17180113.832000] sda: Mode Sense: 03 00 00 00
[17180113.832000] sda: assuming drive cache: write through
[17180113.832000]  sda: sda1
[17180113.840000] sd 0:0:0:0: Attached scsi removable disk sda
[17180113.856000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17180114.476000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17180331.236000] usb 2-1: USB disconnect, address 2

```

---

### Post by allwin on 2007-01-18
While you are waiting for a GOOD answer, you could try this.  Boot.  Go into a terminal and type "sudo rmmod uhci_hcd".  Then plug the device in...PERHAPS...the faster driver ehci_hcd will kick in and render a different verdict.  I've tried about a half dozen things to get my external HD in a can to work...without much success, but removing the older driver looked like it got a little further into the process.  This looks like the kind of cruft that I have been getting trying to hook up my enclosed HD.  Hope your luck is better.  Reboot after you do the "rmmod" command and decide to try something else (if it didn't work).

Oh another thing you can shake your fist at...try booting with that drive connected and see if it mounts then...also, plug in another USB device into that port...if you have one...that you KNOW will work (camera, card reader, whatever).  Dismount it, and then plug your drive right back in...maybe it will "catch" after the USB pipes have been cleared by a working device.

I've been at mine for days.  Best I could do was get my drive to work on the USB 1.1 ports on my old clunker experimental box.  But that meant SLOWWWW SPEEDS (980kbs).

Even if you get the thing connected, you may be faced with a speed problem.  Hope not.  Good luck.

---

### Post by garlito on 2007-01-18
Thanks again, I'm very sorry because I've just noticed that these messages are from my mp3 player, which work fine. Unfortunatly it's all quiet when I plug the hard drive.

I think I will give it back tomorrow. If anyone knows a portable model (without power supply) that worked in Ubuntu I will be very grateful :)

---

### Post by allwin on 2007-01-18
Oh, it's worth fooling around another hour or two before you return it.  Keep trying and keep searching (GOOGLE) as the error messages change...you never know, you may find the majic thing you need to do to get it to work.  BTW, I think if you do manage to get it connected, you may be faced with having to format the drive, which is pretty easy.  You didn't mention if you are going to share it with another OS, which would affect how you format it possibly.  Windows programs exist out there to read EXT3 partitions just fine if that's the case and you decide to format it entirely with EXT3.  Furthermore, google for GPARTED and you will find somewhere a link to a live CD which you can boot the machine into and has one specific purpose...to make it easy to reformat drives.  PERHAPS you will luck out and GPARTED might recognize the drive (a good sign) but then I don't know how you would coax UBUNTU into seeing it.  But if GPARTED can't even recognize it, yeah, maybe return the thing and try again.  Mind the speed you see if you ever get it connected, it might be too slow after all that effort, too.

---

### Post by Zimmer on 2007-01-18
I have my old 3.5 40gig drive in an enclosure, that ,of course ,has an external supply, but there are enclosures available for 2.5 drives that run from the USB direct.

DOes your USB drive register at System>Disks  ??

When connected ( as the only USB device and file systems UN mounted ) my disk still registers an entry in the Systems>Disk  manager. the 2 partitions are allocated automatic mount points of sda1 and sda2.  I think I remember using GPARTED to format it and create the partitions (old age killing off the memory brain cells !)   
Have you run Gparted and seen if it recognises the unit?

---

