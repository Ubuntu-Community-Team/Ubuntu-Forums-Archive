---
title: "Problem mounting USB flash drive"
date: 2006-12-23
forum: General Help
---

### Post by BrendanM on 2006-12-23
Ok, so I have a Kingston Data Traveler 256 MB USB flash drive. When I plug it in at boot time, it mounts in the media directory as KINGSTON, and appears on the desktop. It also hotplugs/automounts fine when I'm using the live CD version of Xubuntu. However, if I try to hotplug it on my hard drive installation of Xubuntu, for a long time nothing happens. If I look at dmesg | tail, I get something like the following:

```
[17181650.988000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[17181651.744000] usb 1-1: new full speed USB device using uhci_hcd and address 4
[17181652.752000] usb 1-1: new full speed USB device using uhci_hcd and address 7
[17181653.508000] usb 1-1: new full speed USB device using uhci_hcd and address 9
[17181655.020000] usb 1-1: new full speed USB device using uhci_hcd and address 14
[17181655.776000] usb 1-1: new full speed USB device using uhci_hcd and address 16
[17181656.532000] usb 1-1: new full speed USB device using uhci_hcd and address 18
[17181657.792000] usb 1-1: new full speed USB device using uhci_hcd and address 22
[17181659.808000] usb 1-1: new full speed USB device using uhci_hcd and address 29
[17181661.068000] usb 1-1: new full speed USB device using uhci_hcd and address 33
[17181661.824000] usb 1-1: new full speed USB device using uhci_hcd and address 35
[17181662.580000] usb 1-1: new full speed USB device using uhci_hcd and address 37
[17181664.092000] usb 1-1: new full speed USB device using uhci_hcd and address 42
[17181664.848000] usb 1-1: new full speed USB device using uhci_hcd and address 44
[17181665.604000] usb 1-1: new full speed USB device using uhci_hcd and address 46
[17181666.612000] usb 1-1: new full speed USB device using uhci_hcd and address 49
[17181668.880000] usb 1-1: new full speed USB device using uhci_hcd and address 57
[17181669.636000] usb 1-1: new full speed USB device using uhci_hcd and address 59
[17181670.392000] usb 1-1: new full speed USB device using uhci_hcd and address 61
[17181671.148000] usb 1-1: new full speed USB device using uhci_hcd and address 63

```

And it continues cycling through USB addresses all the way up to 124 or so before starting over at the bottom and doing this again. Sometimes, it eventually stops doing this (for reasons which are unclear to me) and I get:

```
[17181670.392000] usb 1-1: new full speed USB device using uhci_hcd and address 61
[17181671.148000] usb 1-1: new full speed USB device using uhci_hcd and address 63
[17181673.164000] usb 1-1: new full speed USB device using uhci_hcd and address 70
[17181673.328000] usb 1-1: configuration #1 chosen from 1 choice
[17181673.332000] scsi1 : SCSI emulation for USB Mass Storage devices
[17181673.332000] usb-storage: device found at 70
[17181673.332000] usb-storage: waiting for device to settle before scanning
[17181678.332000] usb-storage: device scan complete
[17181678.336000]   Vendor: Kingston  Model: DataTraveler 2.0  Rev: 6.16
[17181678.336000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17181678.348000] SCSI device sda: 498687 512-byte hdwr sectors (255 MB)
[17181678.352000] sda: Write Protect is off
[17181678.352000] sda: Mode Sense: 45 00 00 08
[17181678.352000] sda: assuming drive cache: write through
[17181678.360000] SCSI device sda: 498687 512-byte hdwr sectors (255 MB)
[17181678.364000] sda: Write Protect is off
[17181678.364000] sda: Mode Sense: 45 00 00 08
[17181678.364000] sda: assuming drive cache: write through
[17181678.364000]  sda: sda1
[17181678.376000] sd 1:0:0:0: Attached scsi removable disk sda
[17181678.376000] sd 1:0:0:0: Attached scsi generic sg0 type 0

```

And the drive finally automounts correctly. This whole process can sometimes take as long as 10 or 15 minutes. Does anyone know what's going on here? Or how I can make it hurry up and pick an address sooner?

---

### Post by BrendanM on 2006-12-23
I found another post that seems to be describing the same issue I'm having: [http://ubuntuforums.org/showthread.php?t=188288](http://ubuntuforums.org/showthread.php?t=188288)
but there was no solution for the USB issue posted there. Is there anybody here who's good with USB stuff? Is this a problem with udev?

---

### Post by dcstar on 2006-12-23
> **BrendanM said:**
> I found another post that seems to be describing the same issue I'm having: [http://ubuntuforums.org/showthread.php?t=188288](http://ubuntuforums.org/showthread.php?t=188288)
but there was no solution for the USB issue posted there. Is there anybody here who's good with USB stuff? Is this a problem with udev?

Just make sure you have all the current updates installed, some USB problems were fixed in the recent updates.

---

### Post by BrendanM on 2006-12-24
Thanks, I ran apt-get upgrade to bring everything up to date, and I'm still getting the same behavior from the USB key.

Following that other forum, I borrowed a little (unpowered) 4-port USB hub from a friend of mine and tried it with that. IT WORKS PERFECTLY WITH THE USB HUB. Does anyone know why it would work with the hub, but not without it? If not, I guess I'll be buying a little USB hub.

---

### Post by sageb1 on 2007-12-02
My guess is the USB ports on the computer are USB 1.1 but the usb flash drive is USB 2.0.

---

