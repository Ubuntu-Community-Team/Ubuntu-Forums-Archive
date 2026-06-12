---
title: "[SOLVED] Mounting SATA Drive with USB Adapter"
date: 2008-04-27
forum: General Help
---

### Post by TygerFish on 2008-04-27
My desktop is out of commission for repairs (dead motherboard) but I badly need to get a file off of one of my hard drives for work.  I bought a USB adapter (an enclosure minus the enclosure) and hooked the drive up to it but am having trouble figuring out how to mount the drive.  I'm using Kubuntu Hardy on a Dell D610.

One time, Kubuntu brought up the "new removable device" dialog for all of the partitions on the drive, but only that once.  The adapter has a power button that turns the attached drive(s) on/off.  I've tried different combinations of turning the drive on before and after plugging in the USB cable, but haven't been able to get the auto-mount to happen again.

Relevant dmesg output after plugging in the USB cable with the hard drive already turned on:
```
[  213.331707] usb 5-7: new high speed USB device using ehci_hcd and address 4
[  213.465862] usb 5-7: configuration #1 chosen from 1 choice
[  106.754094] usbcore: registered new interface driver libusual
[  106.803178] Initializing USB Mass Storage driver...
[  106.804019] scsi2 : SCSI emulation for USB Mass Storage devices
[  106.806100] usbcore: registered new interface driver usb-storage
[  106.806105] USB Mass Storage support registered.
[  106.806198] usb-storage: device found at 4
[  106.806200] usb-storage: waiting for device to settle before scanning
[  219.172644] usb-storage: device scan complete
[  219.173365] scsi 2:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
[  219.184572] sd 2:0:0:0: [sdb] Attached SCSI disk
[  219.184645] sd 2:0:0:0: Attached scsi generic sg2 type 0
```

This is the only thing I could think to do manually to mount the drive, but it didn't work:
```
$ sudo mount -t ext3 -o rw /dev/sdb5 /mnt/usb
mount: special device /dev/sdb5 does not exist
```

---

### Post by TygerFish on 2008-05-20
Much to my chagrin, everything works very nicely if I activate the external power source and then wait at least 15 seconds before plugging in the USB cable.  Silly undocumented products!

The device I'm using appears to be a JMicron JM20337.  It lists like this:
```
$ lsusb
Bus 005 Device 005: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
```
Hope this helps somebody else!

---

### Post by parovelb on 2011-09-30
Same issue here. WD800 drive from notebook attached to STLab USB to PATA + SATA adapter on gnome. Below is my otput.

```
:/$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bajtov
255 heads, 63 sectors/track, 19457 cylinders
Units = steze of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a76f9

Naprava   Zagon    Za&#269;etek       Konec     Bloki    Id  Sistem
/dev/sda1   *           1       19272   154798080   83  Linux
/dev/sda2           19272       19458     1489921    5  Raz&#353;irjen
/dev/sda5           19272       19458     1489920   82  Linux izmenjalni / Solaris

:/$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

How can I get to my data on the disk?

---

