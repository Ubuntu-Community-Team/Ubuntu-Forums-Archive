---
title: "Micro SD Card with Linux???"
date: 2008-02-12
forum: General Help
---

### Post by kelforn on 2008-02-12
I have a Nokia Cell Phone Model # 6126 in which I purchased a Kingston 2gb Micro SD Card for.

I want to be able to transfer photos and music to and from a Linux Computer. The Micro SD Card came with an SD size adapter. I also own a USB Card Reader (the ones that's about the size of a regular flash drive) so to do all this with.

Do I have to format this Micro SD Card?

If so, how do I do it and how do I get around Linux Kubuntu NOT even recognizing this card even though the card readers led light flashes then stays on steady without it being anywhere in Linux - even /Media.

If I can get an explanation or even get pointed in the right direction - I'd really appreciate it as googling hasn't helped me in the least.


Thanks for your anticipated responses.

---

### Post by danwood76 on 2008-02-12
You should be able to format the SD card in your phone, if you do this and it doesnt show up in ubuntu after this I would have thought your USB reader maybe isnt supported.

you can check to see if it knows your reader is in the slot by doing:
```

lsusb

```
in terminal, this will give you the make/model of the readers chipset which you can search the web for drivers.

I have a multi card reader that works perfectly with gutsy and automatically mounts newly installed cards to /media so they appear on the desktop.

hope this helps a bit,
Danny

---

### Post by kelforn on 2008-02-12
> **danwood76 said:**
> You should be able to format the SD card in your phone, if you do this and it doesnt show up in ubuntu after this I would have thought your USB reader maybe isnt supported.

you can check to see if it knows your reader is in the slot by doing:
```

lsusb

```
in terminal, this will give you the make/model of the readers chipset which you can search the web for drivers.

I have a multi card reader that works perfectly with gutsy and automatically mounts newly installed cards to /media so they appear on the desktop.

hope this helps a bit,
Danny


Hi Danny,
Thanks for your post.  I did go ahead and formatted the Micro SD card using my phone which went well, however now the reader doesn't even flash anymore - lol!

I'll see if there's drivers for this reader as shown.

This is what the "lsusb" command yielded:

us 004 Device 001: ID 0000:0000
Bus 002 Device 002: ID 0458:0007 KYE Systems Corp. (Mouse Systems)
Bus 002 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 003: ID 0aec:3050 Neodio Technologies Corp. ND3050 8-in-1 Card Reader
Bus 001 Device 001: ID 0000:0000


I also did the "dmesg" command and this is what showed:

[   81.156000] Bluetooth: RFCOMM ver 1.8
[   85.576000] NET: Registered protocol family 17
[ 2451.372000] usb 1-2: new full speed USB device using uhci_hcd and address 4
[ 2451.492000] usb 1-2: device descriptor read/64, error -71
[ 2451.716000] usb 1-2: device descriptor read/64, error -71
[ 2451.932000] usb 1-2: new full speed USB device using uhci_hcd and address 5
[ 2452.052000] usb 1-2: device descriptor read/64, error -71
[ 2452.276000] usb 1-2: device descriptor read/64, error -71
[ 2452.492000] usb 1-2: new full speed USB device using uhci_hcd and address 6
[ 2452.900000] usb 1-2: device not accepting address 6, error -71
[ 2453.012000] usb 1-2: new full speed USB device using uhci_hcd and address 7
[ 2453.420000] usb 1-2: device not accepting address 7, error -71
[ 2830.328000] usb 1-2: new full speed USB device using uhci_hcd and address 8
[ 2830.448000] usb 1-2: device descriptor read/64, error -71
[ 2830.672000] usb 1-2: device descriptor read/64, error -71
[ 2830.888000] usb 1-2: new full speed USB device using uhci_hcd and address 9
[ 2831.008000] usb 1-2: device descriptor read/64, error -71
[ 2831.232000] usb 1-2: device descriptor read/64, error -71
[ 2831.448000] usb 1-2: new full speed USB device using uhci_hcd and address 10
[ 2831.856000] usb 1-2: device not accepting address 10, error -71
[ 2831.968000] usb 1-2: new full speed USB device using uhci_hcd and address 11
[ 2832.384000] usb 1-2: device not accepting address 11, error -71
[ 3064.480000] usb 1-2: new full speed USB device using uhci_hcd and address 12
[ 3064.600000] usb 1-2: device descriptor read/64, error -71
[ 3064.824000] usb 1-2: device descriptor read/64, error -71
[ 3065.040000] usb 1-2: new full speed USB device using uhci_hcd and address 13
[ 3065.160000] usb 1-2: device descriptor read/64, error -71
[ 3065.384000] usb 1-2: device descriptor read/64, error -71
[ 3065.600000] usb 1-2: new full speed USB device using uhci_hcd and address 14
[ 3066.008000] usb 1-2: device not accepting address 14, error -71
[ 3066.120000] usb 1-2: new full speed USB device using uhci_hcd and address 15
[ 3066.528000] usb 1-2: device not accepting address 15, error -71

Thanks for putting me on the right road - if all fails I'll just have to try another card reader but to make sure it's compatible with Linux.

If anyone can recommend a USB portable SD card reader  - I'd be open and welcoming to those suggestions.

Thanks so much:)
Nick

---

### Post by danwood76 on 2008-02-12
Your reader is compatible:
[http://hardware4linux.info/component/12389/](http://hardware4linux.info/component/12389/)

have you tried it in another USB port, it sounds as if its connecting and disconnecting over and over.

---

### Post by kelforn on 2008-02-12
I don't know what's going on now the "dmesg" command comes back a bit differently.

 1540.292000] Buffer I/O error on device sde, logical block 0
[ 1540.300000] sd 2:0:0:0: SCSI error: return code = 0x08000002
[ 1540.300000] sde: Current: sense key: Medium Error
[ 1540.300000]     Additional sense: Unrecovered read error
[ 1540.300000] end_request: I/O error, dev sde, sector 0
[ 1540.300000] Buffer I/O error on device sde, logical block 0
[ 1540.300000] Dev sde: unable to read RDB block 0
[ 1540.308000] sd 2:0:0:0: SCSI error: return code = 0x08000002
[ 1540.308000] sde: Current: sense key: Medium Error
[ 1540.308000]     Additional sense: Unrecovered read error
[ 1540.308000] end_request: I/O error, dev sde, sector 0
[ 1540.308000] Buffer I/O error on device sde, logical block 0
[ 1540.316000] sd 2:0:0:0: SCSI error: return code = 0x08000002
[ 1540.316000] sde: Current: sense key: Medium Error
[ 1540.316000]     Additional sense: Unrecovered read error
[ 1540.316000] end_request: I/O error, dev sde, sector 0
[ 1543.988000] sd 2:0:0:0: SCSI error: return code = 0x08000002
[ 1543.988000] sde: Current: sense key: Medium Error
[ 1543.988000]     Additional sense: Unrecovered read error
[ 1543.988000] end_request: I/O error, dev sde, sector 24
[ 1547.660000] sd 2:0:0:0: SCSI error: return code = 0x08000002
[ 1547.660000] sde: Current: sense key: Medium Error
[ 1547.660000]     Additional sense: Unrecovered read error
[ 1547.660000] end_request: I/O error, dev sde, sector 24
[ 1547.660000] printk: 2 messages suppressed.
[ 1547.660000] Buffer I/O error on device sde, logical block 3
[ 1547.668000] sd 2:0:0:0: SCSI error: return code = 0x08000002
[ 1547.668000] sde: Current: sense key: Medium Error
[ 1547.668000]     Additional sense: Unrecovered read error
[ 1547.668000] end_request: I/O error, dev sde, sector 0
[ 1547.668000]  unknown partition table
[ 1547.668000] sd 2:0:0:0: Attached scsi removable disk sde
[ 1547.668000] sd 2:0:0:0: Attached scsi generic sg4 type 0
[ 1600.584000] usb 4-5: USB disconnect, address 5
[ 1686.828000] usb 4-3: new high speed USB device using ehci_hcd and address 6
[ 1686.964000] usb 4-3: configuration #1 chosen from 1 choice
[ 1686.964000] scsi3 : SCSI emulation for USB Mass Storage devices
[ 1686.964000] usb-storage: device found at 6
[ 1686.964000] usb-storage: waiting for device to settle before scanning
[ 1691.968000] usb-storage: device scan complete
[ 1691.968000] scsi 3:0:0:0: Direct-Access     USB 2.0  SD/MMC Reader         PQ: 0 ANSI: 0 CCS
[ 1691.968000] SCSI device sde: 903573504 512-byte hdwr sectors (462630 MB)
[ 1691.972000] sde: Write Protect is off
[ 1691.972000] sde: Mode Sense: 03 00 00 00
[ 1691.972000] sde: assuming drive cache: write through
[ 1691.972000] SCSI device sde: 903573504 512-byte hdwr sectors (462630 MB)
[ 1691.976000] sde: Write Protect is off
[ 1691.976000] sde: Mode Sense: 03 00 00 00
[ 1691.976000] sde: assuming drive cache: write through
[ 1691.976000]  sde:<6>sd 3:0:0:0: SCSI error: return code = 0x08000002
[ 1691.984000] sde: Current: sense key: Medium Error
[ 1691.984000]     Additional sense: Unrecovered read error
[ 1691.984000] end_request: I/O error, dev sde, sector 0
[ 1691.984000] printk: 1 messages suppressed.
[ 1691.984000] Buffer I/O error on device sde, logical block 0
[ 1691.988000] sd 3:0:0:0: SCSI error: return code = 0x08000002
[ 1691.988000] sde: Current: sense key: Medium Error
[ 1691.988000]     Additional sense: Unrecovered read error
[ 1691.988000] end_request: I/O error, dev sde, sector 0
[ 1691.988000] Buffer I/O error on device sde, logical block 0
[ 1691.996000] sd 3:0:0:0: SCSI error: return code = 0x08000002
[ 1691.996000] sde: Current: sense key: Medium Error
[ 1691.996000]     Additional sense: Unrecovered read error
[ 1691.996000] end_request: I/O error, dev sde, sector 0
[ 1691.996000] Buffer I/O error on device sde, logical block 0
[ 1692.004000] sd 3:0:0:0: SCSI error: return code = 0x08000002
[ 1692.004000] sde: Current: sense key: Medium Error
[ 1692.004000]     Additional sense: Unrecovered read error
[ 1692.004000] end_request: I/O error, dev sde, sector 0
[ 1692.004000] Buffer I/O error on device sde, logical block 0
[ 1692.012000] sd 3:0:0:0: SCSI error: return code = 0x08000002
[ 1692.012000] sde: Current: sense key: Medium Error
[ 1692.012000]     Additional sense: Unrecovered read error
[ 1692.012000] end_request: I/O error, dev sde, sector 0
[ 1692.012000] Buffer I/O error on device sde, logical block 0
[ 1692.012000] ldm_validate_partition_table(): Disk read failed.
[ 1692.020000] sd 3:0:0:0: SCSI error: return code = 0x08000002
[ 1692.020000] sde: Current: sense key: Medium Error
[ 1692.020000]     Additional sense: Unrecovered read error
[ 1692.020000] end_request: I/O error, dev sde, sector 0
[ 1692.020000] Buffer I/O error on device sde, logical block 0
[ 1692.028000] sd 3:0:0:0: SCSI error: return code = 0x08000002
[ 1692.028000] sde: Current: sense key: Medium Error
[ 1692.028000]     Additional sense: Unrecovered read error
[ 1692.028000] end_request: I/O error, dev sde, sector 0
[ 1692.028000] Buffer I/O error on device sde, logical block 0
[ 1692.036000] sd 3:0:0:0: SCSI error: return code = 0x08000002
[ 1692.036000] sde: Current: sense key: Medium Error
[ 1692.036000]     Additional sense: Unrecovered read error
[ 1692.036000] end_request: I/O error, dev sde, sector 0
[ 1692.036000] Buffer I/O error on device sde, logical block 0
[ 1692.044000] sd 3:0:0:0: SCSI error: return code = 0x08000002
[ 1692.044000] sde: Current: sense key: Medium Error
[ 1692.044000]     Additional sense: Unrecovered read error
[ 1692.044000] end_request: I/O error, dev sde, sector 0
[ 1692.044000] Buffer I/O error on device sde, logical block 0
[ 1692.044000] Dev sde: unable to read RDB block 0
[ 1692.048000] sd 3:0:0:0: SCSI error: return code = 0x08000002
[ 1692.048000] sde: Current: sense key: Medium Error
[ 1692.048000]     Additional sense: Unrecovered read error
[ 1692.048000] end_request: I/O error, dev sde, sector 0
[ 1692.048000] Buffer I/O error on device sde, logical block 0
[ 1692.056000] sd 3:0:0:0: SCSI error: return code = 0x08000002
[ 1692.056000] sde: Current: sense key: Medium Error
[ 1692.056000]     Additional sense: Unrecovered read error
[ 1692.056000] end_request: I/O error, dev sde, sector 0
[ 1695.732000] sd 3:0:0:0: SCSI error: return code = 0x08000002
[ 1695.732000] sde: Current: sense key: Medium Error
[ 1695.732000]     Additional sense: Unrecovered read error
[ 1695.732000] end_request: I/O error, dev sde, sector 24

The Micro SD card IS formatted via the Cell Phone and stored in the Micro SD card is a photo and a video - still doesn't want to show me it wants to cooperate.

I tried all 6 of the 2.0 USB connections too.

Any clue of what this is saying?

Thanks:)

---

### Post by danwood76 on 2008-02-13
well its coming up with /dev/sde which means its reading the disk by the sounds of it.
you could try repartitioning/reformatting it using gparted (available from synaptic).

But of course make sure you are reformatting the correct drive/partition, if you do the wrong one you will loose data.

It looks as if its having problems reading block 0.

---

### Post by kelforn on 2008-02-13
> **danwood76 said:**
> well its coming up with /dev/sde which means its reading the disk by the sounds of it.
you could try repartitioning/reformatting it using gparted (available from synaptic).

But of course make sure you are reformatting the correct drive/partition, if you do the wrong one you will loose data.

It looks as if its having problems reading block 0.

I tried something different this morning - I plugged that USB reader into a Windows XP machine.

It still doesn't even work there!

I tried opening it up and it won't instead asking me if I wanted to reformat it - I answered "yes" and it came back saying that it cannot be formatted.

I can't say there's anything wrong with the Micro SD card because it stores the one photo and one video fine and which is there safe and sound every time when I use my phone to access them.

It must be the reader problem which might be faulty - please feel free to disagree if you think I'm mistaken:)

When it doesn't work with Linux and Windows - somethings very wrong.  Not that Windows is all that but has its use in some things Linux cannot quite do yet and most of it not the fault of Linux.

---

### Post by notwen on 2008-02-13
If you decide to try and purchase a new mobile media reader, I personally own this [Sandisk MobileMate]("http://www.sandisk.com/Products/Item(1220)-SDDR-104-A11M-SanDisk_MobileMate_SD_Plus5in1_Reader.aspx") and it works great in both Linux/Windows.  I use it for the exact same reason(cell phone microsd) along w/ moving pictures from my digicam.  Good luck with your issue. =]

---

### Post by kelforn on 2008-02-13
> **notwen said:**
> If you decide to try and purchase a new mobile media reader, I personally own this [Sandisk MobileMate]("http://www.sandisk.com/Products/Item(1220)-SDDR-104-A11M-SanDisk_MobileMate_SD_Plus5in1_Reader.aspx") and it works great in both Linux/Windows.  I use it for the exact same reason(cell phone microsd) along w/ moving pictures from my digicam.  Good luck with your issue. =]

Thanks so much for the recommendation:)

---

