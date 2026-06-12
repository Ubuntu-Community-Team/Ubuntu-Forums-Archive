---
title: "Can't Mount USB CD Drive"
date: 2008-05-30
forum: General Help
---

### Post by Bungo Pony on 2008-05-30
Having a rotten time with this one. 

```
 lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 001 Device 002: ID 059f:a602 LaCie, Ltd 
Bus 001 Device 001: ID 0000:0000  

```

So it find the drive (LaCie). But here's what happens when I try to mount it with a CD in the drive:

```
sudo mount -t iso9660 /dev/scd0 /media/extcd
mount: No medium found

```

I've searched Google, and apparently I'm not the only one having this problem, but there's never a solution.

Has anyone been able to overcome this?

---

### Post by Bungo Pony on 2008-05-30
Here's my dmesg if it helps:

```
[ 2122.203445] usb 1-7: new full speed USB device using ohci_hcd and address 4
[ 2122.393325] usb 1-7: configuration #1 chosen from 1 choice
[ 2122.409416] scsi6 : SCSI emulation for USB Mass Storage devices
[ 2122.415440] usb-storage: device found at 4
[ 2122.416533] usb-storage: waiting for device to settle before scanning
[ 2127.416143] usb-storage: device scan complete
[ 2133.071633] usb 1-7: reset full speed USB device using ohci_hcd and address 4
[ 2143.409963] usb 1-7: reset full speed USB device using ohci_hcd and address 4
[ 2159.752735] usb 1-7: reset full speed USB device using ohci_hcd and address 4
[ 2160.093682] usb 1-7: reset full speed USB device using ohci_hcd and address 4
[ 2170.430973] usb 1-7: reset full speed USB device using ohci_hcd and address 4
[ 2170.613357] scsi 6:0:0:0: Device offlined - not ready after error recovery


```

Go figure I can get a 1G Parallel HD working, but not a USB CD drive :(

---

