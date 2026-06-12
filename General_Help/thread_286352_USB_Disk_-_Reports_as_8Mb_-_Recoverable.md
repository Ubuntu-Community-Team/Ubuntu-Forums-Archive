---
title: "USB Disk - Reports as 8Mb - Recoverable?"
date: 2006-10-27
forum: General Help
---

### Post by victorhooi on 2006-10-27
heya,

I'm not sure if this is exactly the right category, but here goes...

Basically, I have a friend's 1Gb usb disk with important data that always reports itself as 8Mb now, with a b0rked partition table, and I need to get some important data off it (think latest copy of thesis, she has old copies but from back).

I originally made a post an gentoo forums, I suppose it's ok if I make a post here as well? ([http://forums.gentoo.org/viewtopic-t-510968.html]("http://forums.gentoo.org/viewtopic-t-510968.html"))

fdisk -l output
```

victorhooi@riv-cheron:/datastore$ fdisk -l /dev/sda

Disk /dev/sda: 8 MB, 8388608 bytes
1 heads, 16 sectors/track, 1024 cylinders
Units = cylinders of 16 * 512 = 8192 bytes

Disk /dev/sda doesn't contain a valid partition table
victorhooi@riv-cheron:/datastore$ 

```

dmesg output (Ubuntu 6.06 Live)
```

[4295784.710000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[4295787.073000] SCSI subsystem initialized
[4295787.184000] Initializing USB Mass Storage driver...
[4295787.186000] scsi0 : SCSI emulation for USB Mass Storage devices
[4295787.186000] usb-storage: device found at 2
[4295787.186000] usb-storage: waiting for device to settle before scanning
[4295787.187000] usbcore: registered new driver usb-storage
[4295787.187000] USB Mass Storage support registered.
[4295792.191000]   Vendor: ChipsBnk  Model: Flash Disk        Rev: 2.00
[4295792.191000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[4295792.199000] usb-storage: device scan complete
[4295792.279000] Driver 'sd' needs updating - please use bus_type methods
[4295792.286000] SCSI device sda: 16384 512-byte hdwr sectors (8 MB)
[4295792.290000] sda: Write Protect is off
[4295792.290000] sda: Mode Sense: 0b 00 00 08
[4295792.290000] sda: assuming drive cache: write through
[4295792.300000] SCSI device sda: 16384 512-byte hdwr sectors (8 MB)
[4295792.303000] sda: Write Protect is off
[4295792.303000] sda: Mode Sense: 0b 00 00 08
[4295792.303000] sda: assuming drive cache: write through
[4295792.303000]  sda: unknown partition table
[4295792.326000] sd 0:0:0:0: Attached scsi removable disk sda
[4295792.362000] sd 0:0:0:0: Attached scsi generic sg0 type 0 

```

No matter how I kick and scream at dd, it always spits out a 8Mb image file. Is there any way to force Linux to see geometry beyond 8Mb for a USB disk?

Thanks,
Victor

PS: As an aside, I managed to hose my ubuntu install, forced an uninstall of libc6 (don't ask...*sigh*), so I'm posting from the liveCD. Any suggestions for that? I suppose just downloading 6.10 and upgrading will work?

---

