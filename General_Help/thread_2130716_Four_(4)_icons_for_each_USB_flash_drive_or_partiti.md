---
title: "Four (4) icons for each USB flash drive or partition inserted in GNOME panel"
date: 2013-03-30
forum: General Help
---

### Post by vezolmi on 2013-03-30
Hi. In a very recently installed Ubuntu 10.04 (Lucid Lynx) when I insert a USB flash memory drive 4 icons appear in the GNOME panel (only 1 in the desktop, as it should be in both places). If the device is divided into several partitions there are four icons for each one of them (1 per partition in desktop, as it should be in both locations). When I click on one of these icons and then on "Remove ..." (or the icon -or one of the several if more than 1 partition- of the desktop and then on "Safely Remove Drive") all of them dissapear.

Why do I have this problem? How can I solve it? Thank you

---

### Post by tgalati4 on 2013-03-30
Does it happen with one USB flash drive or all of them?  If you have an intermittent flash drive or bad USB port, it's possible that the drive is being mounted several times.  Also, drives that are bigger than 32GB may be an issue--since 10.04 is an old release.

Open a terminal and examine the output from:

```
dmesg | more
```

Spacebar to page forward, "q" to quit.  Look for messages regarding your USB drive.  Also:

```
sudo fdisk -l
```

---

### Post by vezolmi on 2013-03-31
Thanks. The strange phenomenon happens with all the USB flash drives I have tried, and in the 2 USB ports this P4 256MB RAM computer has. The drives are smaller than 32GB (I have installed 10.04 v -Lucid Lynx- because I had it downloaded from some time ago, to try it in this computer).

```
dmesg | grep -i usb
[    0.141870] usbcore: registered new interface driver usbfs
[    0.141896] usbcore: registered new interface driver hub
[    0.141961] usbcore: registered new device driver usb
[    0.315377] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.315421] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.315448] uhci_hcd: USB Universal Host Controller Interface driver
[    0.315996] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[    0.316577] usb usb1: configuration #1 chosen from 1 choice
[    0.316644] hub 1-0:1.0: USB hub found
[    0.317225] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[    0.317467] usb usb2: configuration #1 chosen from 1 choice
[    0.317528] hub 2-0:1.0: USB hub found
[ 3781.744072] usb 1-1: new full speed USB device using uhci_hcd and address 2
[ 3781.920715] usb 1-1: configuration #1 chosen from 1 choice
[ 3783.648302] Initializing USB Mass Storage driver...
[ 3783.656131] scsi2 : SCSI emulation for USB Mass Storage devices
[ 3783.657119] usbcore: registered new interface driver usb-storage
[ 3783.657128] USB Mass Storage support registered.
[ 3783.664684] usb-storage: device found at 2
[ 3783.664691] usb-storage: waiting for device to settle before scanning
[ 3788.666010] usb-storage: device scan complete
```

**sudo fdisk -l** returns what espected: info about the HDD and its partitions and info about the UFD and its partitions.

---

