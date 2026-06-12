---
title: "Slow cardreader MMC mount"
date: 2013-09-25
forum: General Help
---

### Post by Jonor on 2013-09-25
(ETA: Problem has now disappeared)

I have two almost identical boxes both running Ubuntu 13.04 with Gnome Classic,
the first box mounts my multi media card immediately as desired whereas the second box typically takes 4 minutes.
This is a setback because the card normally needs to be shuttled frequently between the reader on the second box and
a camera to check the quality of some photography done with the card.

Here are log files of the first box for reference starting with plugging in the reader 
```
Sep 25 21:22:57 lj3 kernel: [  178.728056] usb 1-1: new high-speed USB device number 2 using ehci-pci
Sep 25 21:22:57 lj3 kernel: [  178.929489] usb 1-1: New USB device found, idVendor=090c, idProduct=6000
Sep 25 21:22:57 lj3 kernel: [  178.929503] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Sep 25 21:22:57 lj3 kernel: [  178.929510] usb 1-1: Product: USB2.0 Card Reader  
Sep 25 21:22:57 lj3 kernel: [  178.929516] usb 1-1: Manufacturer: Generic       ,   . 
Sep 25 21:22:57 lj3 kernel: [  178.929521] usb 1-1: SerialNumber: 12345678901234567890
Sep 25 21:22:57 lj3 mtp-probe: checking bus 1, device 2: "/sys/devices/pci0000:00/0000:00:12.2/usb1/1-1"
Sep 25 21:22:57 lj3 mtp-probe: bus: 1, device: 2 was not an MTP device
[COLOR="#800000"]Sep 25 21:22:57 lj3 kernel: [  178.953440] Initializing USB Mass Storage driver...[/COLOR]
Sep 25 21:22:57 lj3 kernel: [  178.953874] usb-storage 1-1:1.0: Quirks match for vid 090c pid 6000: 100000
Sep 25 21:22:57 lj3 kernel: [  178.955324] scsi6 : usb-storage 1-1:1.0
[COLOR="#800000"]Sep 25 21:22:57 lj3 kernel: [  178.955562] usbcore: registered new interface driver usb-storage
Sep 25 21:22:57 lj3 kernel: [  178.955567] USB Mass Storage support registered.[/COLOR]
Sep 25 21:22:58 lj3 kernel: [  179.953816] scsi 6:0:0:0: Direct-Access     Generic                   6000 PQ: 0 ANSI: 0 CCS
Sep 25 21:22:58 lj3 kernel: [  179.955548] sd 6:0:0:0: Attached scsi generic sg2 type 0
Sep 25 21:22:58 lj3 kernel: [  179.962446] sd 6:0:0:0: [sdb] Attached SCSI removable disk
```


First box slotting in the card
```
Sep 25 21:25:28 lj3 kernel: [  330.393433] sd 6:0:0:0: [sdb] 16152576 512-byte logical blocks: (8.27 GB/7.70 GiB)
Sep 25 21:25:28 lj3 kernel: [  330.394913] sd 6:0:0:0: [sdb] No Caching mode page present
Sep 25 21:25:28 lj3 kernel: [  330.394921] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep 25 21:25:28 lj3 kernel: [  330.398661] sd 6:0:0:0: [sdb] No Caching mode page present
Sep 25 21:25:28 lj3 kernel: [  330.398668] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep 25 21:25:28 lj3 kernel: [  330.409949]  sdb: sdb1
Sep 25 21:25:29 lj3 udisksd[1665]: Mounted /dev/sdb1 at /media/j3/C891-BD65 on behalf of uid 1000
```




Now for the slow second box

Second box plugging in the reader 
```
Sep 25 22:03:45 lj2 kernel: [133884.756299] usb 1-3.1.3: new high-speed USB device number 99 using ehci-pci
Sep 25 22:03:45 lj2 kernel: [133884.967148] usb 1-3.1.3: New USB device found, idVendor=090c, idProduct=6000
Sep 25 22:03:45 lj2 kernel: [133884.967161] usb 1-3.1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Sep 25 22:03:45 lj2 kernel: [133884.967167] usb 1-3.1.3: Product: USB2.0 Card Reader  
Sep 25 22:03:45 lj2 kernel: [133884.967173] usb 1-3.1.3: Manufacturer: Generic       ,   . 
Sep 25 22:03:45 lj2 kernel: [133884.967178] usb 1-3.1.3: SerialNumber: 12345678901234567890
Sep 25 22:03:45 lj2 kernel: [133884.967829] usb-storage 1-3.1.3:1.0: Quirks match for vid 090c pid 6000: 100000
Sep 25 22:03:45 lj2 kernel: [133884.968357] scsi44 : usb-storage 1-3.1.3:1.0
Sep 25 22:03:45 lj2 mtp-probe: checking bus 1, device 99: "/sys/devices/pci0000:00/0000:00:12.2/usb1/1-3/1-3.1/1-3.1.3"
Sep 25 22:03:45 lj2 mtp-probe: bus: 1, device: 99 was not an MTP device
Sep 25 22:03:46 lj2 kernel: [133885.969731] scsi 44:0:0:0: Direct-Access     Generic                   6000 PQ: 0 ANSI: 0 CCS
Sep 25 22:03:46 lj2 kernel: [133885.973449] sd 44:0:0:0: Attached scsi generic sg6 type 0
Sep 25 22:03:46 lj2 kernel: [133885.978610] sd 44:0:0:0: [sdf] Attached SCSI removable disk
```


Second box slotting in the card 
```
Sep 25 22:04:53 lj2 kernel: [133952.666241] sd 44:0:0:0: [sdf] 16152576 512-byte logical blocks: (8.27 GB/7.70 GiB)
Sep 25 22:04:53 lj2 kernel: [133952.667851] sd 44:0:0:0: [sdf] No Caching mode page present
Sep 25 22:04:53 lj2 kernel: [133952.667859] sd 44:0:0:0: [sdf] Assuming drive cache: write through
Sep 25 22:05:23 lj2 kernel: [133982.920236] usb 1-3.1.3: reset high-speed USB device number 99 using ehci-pci
Sep 25 22:05:54 lj2 udevd[11347]: timeout '/sbin/blkid -o udev -p /dev/sdf'
Sep 25 22:05:54 lj2 kernel: [134013.992288] usb 1-3.1.3: reset high-speed USB device number 99 using ehci-pci
Sep 25 22:05:55 lj2 udevd[11347]: timeout: killing '/sbin/blkid -o udev -p /dev/sdf' [11364]
Sep 25 22:06:25  udevd[11347]: last message repeated 30 times
Sep 25 22:06:25 lj2 kernel: [134044.968224] usb 1-3.1.3: reset high-speed USB device number 99 using ehci-pci
Sep 25 22:06:26 lj2 udevd[11347]: timeout: killing '/sbin/blkid -o udev -p /dev/sdf' [11364]
Sep 25 22:06:56  udevd[11347]: last message repeated 30 times
Sep 25 22:06:56 lj2 kernel: [134075.944285] usb 1-3.1.3: reset high-speed USB device number 99 using ehci-pci
Sep 25 22:06:57 lj2 udevd[11347]: timeout: killing '/sbin/blkid -o udev -p /dev/sdf' [11364]
Sep 25 22:06:57 lj2 kernel: [134076.761723] sd 44:0:0:0: [sdf] No Caching mode page present
Sep 25 22:06:57 lj2 kernel: [134076.761736] sd 44:0:0:0: [sdf] Assuming drive cache: write through
Sep 25 22:06:58 lj2 udevd[11347]: timeout: killing '/sbin/blkid -o udev -p /dev/sdf' [11364]
Sep 25 22:07:27  udevd[11347]: last message repeated 29 times
Sep 25 22:07:27 lj2 kernel: [134106.920370] usb 1-3.1.3: reset high-speed USB device number 99 using ehci-pci
Sep 25 22:07:28 lj2 udevd[11347]: timeout: killing '/sbin/blkid -o udev -p /dev/sdf' [11364]
Sep 25 22:07:58  udevd[11347]: last message repeated 30 times
Sep 25 22:07:58 lj2 kernel: [134137.896302] usb 1-3.1.3: reset high-speed USB device number 99 using ehci-pci
Sep 25 22:07:59 lj2 udevd[11347]: timeout: killing '/sbin/blkid -o udev -p /dev/sdf' [11364]
Sep 25 22:08:29  udevd[11347]: last message repeated 30 times
Sep 25 22:08:29 lj2 kernel: [134169.000345] usb 1-3.1.3: reset high-speed USB device number 99 using ehci-pci
Sep 25 22:08:30 lj2 udevd[11347]: timeout: killing '/sbin/blkid -o udev -p /dev/sdf' [11364]
Sep 25 22:09:01  udevd[11347]: last message repeated 31 times
Sep 25 22:09:01 lj2 kernel: [134201.000315] usb 1-3.1.3: reset high-speed USB device number 99 using ehci-pci
Sep 25 22:09:02 lj2 udevd[11347]: '/sbin/blkid -o udev -p /dev/sdf' [11364] terminated by signal 9 (Killed)
Sep 25 22:09:02 lj2 udevd[11347]: timeout 'udisks-part-id /dev/sdf'
Sep 25 22:09:02 lj2 kernel: [134201.821298]  sdf: sdf1
Sep 25 22:09:02 lj2 udisksd[1814]: Mounted /dev/sdf1 at /media/j2/C891-BD65 on behalf of uid 1000
```

It seems that a process has to be killed before some other step is more successful. The coloured code is missing from the second box.
The package usbmount has been tried which changes the last few lines of the second lot of log files but there is still a similar delay.
Any ideas how it could be speeded up ?

Thanks for reading.

---------------------------------------

ETA : Problem has disappeared, i have no clue why.

Plugging in cardreader log
```
Oct  1 19:05:56 lj2 kernel: [ 4377.140291] usb 1-3.1.3: new high-speed USB device number 11 using ehci-pci
Oct  1 19:05:56 lj2 kernel: [ 4377.333252] usb 1-3.1.3: New USB device found, idVendor=090c, idProduct=6000
Oct  1 19:05:56 lj2 kernel: [ 4377.333263] usb 1-3.1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Oct  1 19:05:56 lj2 kernel: [ 4377.333271] usb 1-3.1.3: Product: USB2.0 Card Reader  
Oct  1 19:05:56 lj2 kernel: [ 4377.333278] usb 1-3.1.3: Manufacturer: Generic       ,   . 
Oct  1 19:05:56 lj2 kernel: [ 4377.333284] usb 1-3.1.3: SerialNumber: 12345678901234567890
Oct  1 19:05:56 lj2 kernel: [ 4377.334965] usb-storage 1-3.1.3:1.0: Quirks match for vid 090c pid 6000: 100000
Oct  1 19:05:56 lj2 kernel: [ 4377.335035] scsi8 : usb-storage 1-3.1.3:1.0
Oct  1 19:05:56 lj2 mtp-probe: checking bus 1, device 11: "/sys/devices/pci0000:00/0000:00:12.2/usb1/1-3/1-3.1/1-3.1.3"
Oct  1 19:05:56 lj2 mtp-probe: bus: 1, device: 11 was not an MTP device
Oct  1 19:05:57 lj2 kernel: [ 4378.333700] scsi 8:0:0:0: Direct-Access     Generic                   6000 PQ: 0 ANSI: 0 CCS
Oct  1 19:05:57 lj2 kernel: [ 4378.335257] sd 8:0:0:0: Attached scsi generic sg6 type 0
Oct  1 19:05:57 lj2 kernel: [ 4378.340431] sd 8:0:0:0: [sdf] Attached SCSI removable disk
```

Slotting in the card
```
Oct  1 19:06:49 lj2 kernel: [ 4430.482654] sd 8:0:0:0: [sdf] 16152576 512-byte logical blocks: (8.27 GB/7.70 GiB)
Oct  1 19:06:49 lj2 kernel: [ 4430.484163] sd 8:0:0:0: [sdf] No Caching mode page present
Oct  1 19:06:49 lj2 kernel: [ 4430.484181] sd 8:0:0:0: [sdf] Assuming drive cache: write through
Oct  1 19:06:49 lj2 kernel: [ 4430.486871] sd 8:0:0:0: [sdf] No Caching mode page present
Oct  1 19:06:49 lj2 kernel: [ 4430.486878] sd 8:0:0:0: [sdf] Assuming drive cache: write through
Oct  1 19:06:49 lj2 kernel: [ 4430.497327]  sdf: sdf1
Oct  1 19:06:50 lj2 udisksd[1798]: Mounted /dev/sdf1 at /media/j2/C891-BD65 on behalf of uid 1000
```

---

