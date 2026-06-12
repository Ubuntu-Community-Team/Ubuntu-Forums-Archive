---
title: "/dev/ttyUSB0 not showing up for Garmin GPS on 14.04 LTS"
date: 2014-09-07
forum: General Help
---

### Post by bushidoka on 2014-09-07
[COLOR=#000000]Hi folks, I am having what appears to be a very similar issue to this one [/COLOR]http://ubuntuforums.org/showthread.php?t=2208751 but for me it is on LTS release of 14.04, not a pre-release.
[COLOR=#000000]
I am connecting a Garmin eTrex 20 - I'm expecting to get a /dev/ttyUSB0 device to show up, but am not getting it. I have been at this for hours and am certain I have everything set up correctly. I add the garmin_gps kernel module. I get all sorts of nice things showing up in dmesg - just not a ttyUSB device. lsusb shows my Garmin.[/COLOR]

[COLOR=#000000]usb-devices has it show up as using the usb-storage driver, and I wonder if that is the issue. Should it be using garmin-gps? And how do I tell the system to force that?[/COLOR]

[COLOR=#000000]T: Bus=04 Lev=01 Prnt=01 Port=03 Cnt=01 Dev#= 18 Spd=12 MxCh= 0[/COLOR]
[COLOR=#000000]D: Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs= 1[/COLOR]
[COLOR=#000000]P: Vendor=091e ProdID=2519 Rev=05.09[/COLOR]
[COLOR=#000000]S: SerialNumber=0000e61cc669[/COLOR]
[COLOR=#000000]C: #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA[/COLOR]
[COLOR=#000000]I: If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage[/COLOR]


[COLOR=#000000]amckay@ubuntu-gig:~$ lsusb [/COLOR]
[COLOR=#000000]Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR]
[COLOR=#000000]Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]
[COLOR=#000000]Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]
[COLOR=#000000]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR]
[COLOR=#000000]Bus 005 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard[/COLOR]
[COLOR=#000000]Bus 005 Device 002: ID 046d:c045 Logitech, Inc. Optical Mouse[/COLOR]
[COLOR=#000000]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]
[COLOR=#000000]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR]
[COLOR=#000000]Bus 004 Device 022: ID 091e:2519 Garmin International eTrex 30[/COLOR]
[COLOR=#000000]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Here is what dmesg shows when I plug it in

[/COLOR][45366.425270] sd 16:0:0:0: [sdb] Synchronizing SCSI cache
[45366.425363] sd 16:0:0:0: [sdb]  
[45366.425370] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[45366.430091] sd 16:0:0:1: [sdc] Synchronizing SCSI cache
[45366.430135] sd 16:0:0:1: [sdc]  
[45366.430137] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[45370.300617] usb 4-4: new full-speed USB device number 44 using ohci-pci
[45370.440788] usb 4-4: device descriptor read/64, error -62
[45377.969993] usb 4-4: new full-speed USB device number 45 using ohci-pci
[45378.513886] usb 4-4: device not accepting address 45, error -62
[45387.547505] usb 4-4: new full-speed USB device number 47 using ohci-pci
[45387.712049] usb 4-4: New USB device found, idVendor=091e, idProduct=2519
[45387.712058] usb 4-4: New USB device strings: Mfr=0, Product=0, SerialNumber=5
[45387.712063] usb 4-4: SerialNumber: 0000e61cc669
[45387.726097] usb-storage 4-4:1.0: USB Mass Storage device detected
[45387.726285] scsi17 : usb-storage 4-4:1.0
[45388.730088] scsi 17:0:0:0: Direct-Access     Garmin   GARMIN Flash     1.00 PQ: 0 ANSI: 5
[45388.736102] scsi 17:0:0:1: Direct-Access     Garmin   GARMIN Card      1.00 PQ: 0 ANSI: 5
[45388.736479] sd 17:0:0:0: Attached scsi generic sg2 type 0
[45388.736671] sd 17:0:0:1: Attached scsi generic sg3 type 0
[45388.770286] sd 17:0:0:0: [sdb] 3907584 512-byte logical blocks: (2.00 GB/1.86 GiB)
[45388.776287] sd 17:0:0:1: [sdc] 15605760 512-byte logical blocks: (7.99 GB/7.44 GiB)
[45388.782164] sd 17:0:0:0: [sdb] Write Protect is off
[45388.782175] sd 17:0:0:0: [sdb] Mode Sense: 23 00 00 00
[45388.788077] sd 17:0:0:1: [sdc] Write Protect is off
[45388.788090] sd 17:0:0:1: [sdc] Mode Sense: 23 00 00 00
[45388.794327] sd 17:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[45388.800277] sd 17:0:0:1: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[45388.871320]  sdb:
[45388.881214]  sdc: sdc1
[45388.959307] sd 17:0:0:0: [sdb] Attached SCSI removable disk
[45388.965311] sd 17:0:0:1: [sdc] Attached SCSI removable disk
[45391.324444] FAT-fs (sdb): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[45392.253704] FAT-fs (sdc1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.

---

### Post by bushidoka on 2014-09-13
Problem solved - installed Centos 7

---

