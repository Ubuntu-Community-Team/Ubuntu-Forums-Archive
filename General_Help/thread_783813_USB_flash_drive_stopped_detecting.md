---
title: "USB flash drive stopped detecting"
date: 2008-05-06
forum: General Help
---

### Post by aulismedia on 2008-05-06
I've got 16GB AData flash drive with some orchestral music that I played earlier today -- the only existing copy in the world. The problem is that I cannot read the flash drive in Ubuntu (in Windows either, it just hangs up, on all the PCs I tried). Would you be able to tell me how to force-mount the drive? It doesn't automatically mount when I plug it in. 

>>> lsusb
Bus 006 Device 001: ID 0000:0000  
Bus 007 Device 003: ID 064e:a110 Suyin Corp. 
Bus 007 Device 002: ID 067b:2528 Prolific Technology, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0000:0000 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  

Here, Profilic one is the drive I need. 

"fdisk -l" cannot see the device at all.

I know it it formatted as Fat 32.

Anyone? I will be happy to share the music with the one who can help. It is actually Stravinsky's symphony...

---

### Post by niteshifter on 2008-05-06
Hi,

What does running 

```
sudo fdisk -l
```

do? And if that returns nothing, post the output of:

```
ls -l /dev/sd*
```

---

### Post by vanadium on 2008-05-06
If it is not listed in "sudo fdisk -l", then it probably means the USB is defect. You won't be able to mount the partition on it because the drive is not anymore recognized.

Someone (not me!) might have a hint if you post the kernel messages that are generated when you plugged in the drive. Thus, connect the drive, wait a few seconds, then issue the command

dmesg | tail -n 30

to display the last 30 lines of the kernel messages.

---

### Post by aulismedia on 2008-05-06
As I said, "fdisk -l" doesn't show any sign of the drive. But, what keeps up my hope, is that the drive is playable on a standalone player called MediaGate-350, it's fully operational there. Not on PC though.

In dmesg I see the following:

[21237.644000] usb 7-2: new high speed USB device using ehci_hcd and address 4
[21237.776000] usb 7-2: configuration #1 chosen from 1 choice
[21237.776000] scsi6 : SCSI emulation for USB Mass Storage devices
[21237.776000] usb-storage: device found at 4
[21237.776000] usb-storage: waiting for device to settle before scanning
[21242.776000] usb-storage: device scan complete
[21248.388000] usb 7-2: reset high speed USB device using ehci_hcd and address 4
[21258.632000] usb 7-2: reset high speed USB device using ehci_hcd and address 4
[21274.876000] usb 7-2: reset high speed USB device using ehci_hcd and address 4
[21275.124000] usb 7-2: reset high speed USB device using ehci_hcd and address 4
[21285.368000] usb 7-2: reset high speed USB device using ehci_hcd and address 4
[21285.500000] scsi 6:0:0:0: scsi: Device offlined - not ready after error recovery

Any hints here?

---

### Post by Damanther on 2008-05-06
I have actually had this happen to me when plugging in a drive on a USB hub that was either faulty or just plain cheap.

Try a different port? Preferably one on the computer itself and not an external hub.

---

### Post by aulismedia on 2008-05-06
I'm using PC ports directly, no hubs. Doesn't change anything.

---

