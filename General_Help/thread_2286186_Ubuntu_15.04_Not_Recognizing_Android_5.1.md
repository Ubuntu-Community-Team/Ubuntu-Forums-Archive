---
title: "Ubuntu 15.04 Not Recognizing Android 5.1"
date: 2015-07-10
forum: General Help
---

### Post by branau on 2015-07-10
So, here's my situation: I have a Google Nexus 4 that I installed Ubuntu touch onto. Everything worked great, except that I was missing some key apps that I needed so I reverted my phone back to Android. I then upgraded from Android 4.2 to Android 5.1, and shortly later I learned about dual booting on the phone. However, now that I'm trying to run though the process again, my phone is no longer recognized by Ubuntu (I'm running 15.04 as my desktop.) When I plug it in, it starts charging, but I never get a message to allow this computer for debugging nor does Ubuntu respond at all. The phone has debugging enabled. I've tried various cables and all of my USB ports, and nothing seems to make a difference. Here are the results of running lsusb:
```

    Bus 004 Device 004: ID 5986:014c Acer, Inc 
    Bus 004 Device 003: ID 8087:07da Intel Corp. 
    Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
    Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
    Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
And I also ran this:
```

    dmesg | grep -i usb

```
Which gave me this output:

```

    [    0.609268] ACPI: bus type USB registered
    [    0.609285] usbcore: registered new interface driver usbfs
    [    0.609292] usbcore: registered new interface driver hub
    [    0.609309] usbcore: registered new device driver usb
    [    0.994120] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
    [    0.994290] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
    [    0.994292] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
    [    0.994294] usb usb1: Product: xHCI Host Controller
    [    0.994295] usb usb1: Manufacturer: Linux 3.19.0-22-generic xhci-hcd
    [    0.994296] usb usb1: SerialNumber: 0000:00:14.0
    [    0.994392] hub 1-0:1.0: USB hub found
    [    0.994692] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
    [    0.994721] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
    [    0.994723] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
    [    0.994724] usb usb2: Product: xHCI Host Controller
    [    0.994725] usb usb2: Manufacturer: Linux 3.19.0-22-generic xhci-hcd
    [    0.994726] usb usb2: SerialNumber: 0000:00:14.0
    [    0.994809] hub 2-0:1.0: USB hub found
    [    0.995089] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
    [    0.995180] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 3
    [    1.009545] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
    [    1.009581] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
    [    1.009582] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
    [    1.009584] usb usb3: Product: EHCI Host Controller
    [    1.009585] usb usb3: Manufacturer: Linux 3.19.0-22-generic ehci_hcd
    [    1.009586] usb usb3: SerialNumber: 0000:00:1a.0
    [    1.009682] hub 3-0:1.0: USB hub found
    [    1.009877] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 4
    [    1.025561] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
    [    1.025602] usb usb4: New USB device found, idVendor=1d6b, idProduct=0002
    [    1.025603] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
    [    1.025605] usb usb4: Product: EHCI Host Controller
    [    1.025606] usb usb4: Manufacturer: Linux 3.19.0-22-generic ehci_hcd
    [    1.025607] usb usb4: SerialNumber: 0000:00:1d.0
    [    1.025713] hub 4-0:1.0: USB hub found
    [    1.025841] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
    [    1.025862] uhci_hcd: USB Universal Host Controller Interface driver
    [    1.321785] usb 3-1: new high-speed USB device number 2 using ehci-pci
    [    1.337793] usb 4-1: new high-speed USB device number 2 using ehci-pci
    [    1.454254] usb 3-1: New USB device found, idVendor=8087, idProduct=0024
    [    1.454260] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
    [    1.454520] hub 3-1:1.0: USB hub found
    [    1.470268] usb 4-1: New USB device found, idVendor=8087, idProduct=0024
    [    1.470274] usb 4-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
    [    1.470538] hub 4-1:1.0: USB hub found
    [    1.726182] usb 3-1.1: new high-speed USB device number 3 using ehci-pci
    [    1.742164] usb 4-1.5: new full-speed USB device number 3 using ehci-pci
    [    1.838466] usb 4-1.5: New USB device found, idVendor=8087, idProduct=07da
    [    1.838469] usb 4-1.5: New USB device strings: Mfr=0, Product=0, SerialNumber=0
    [    1.910295] usb 4-1.6: new high-speed USB device number 4 using ehci-pci
    [    2.039594] usb 4-1.6: New USB device found, idVendor=5986, idProduct=014c
    [    2.039600] usb 4-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
    [    2.039604] usb 4-1.6: Product: BisonCam, NB Pro
    [    2.039607] usb 4-1.6: Manufacturer: Bison
    [    2.074992] usb 3-1.1: New USB device found, idVendor=0bda, idProduct=0138
    [    2.074998] usb 3-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
    [    2.075002] usb 3-1.1: Product: USB2.0-CRW
    [    2.075005] usb 3-1.1: Manufacturer: Generic
    [    2.075008] usb 3-1.1: SerialNumber: 20090516388200000
    [    2.082878] usbcore: registered new interface driver usb-storage
    [    2.083948] usbcore: registered new interface driver uas
    [    2.084936] ums-realtek 3-1.1:1.0: USB Mass Storage device detected
    [    2.103812] scsi host6: usb-storage 3-1.1:1.0
    [    2.103907] usbcore: registered new interface driver ums-realtek
    [    2.281248] usb 3-1.1: USB disconnect, device number 3
    [   14.874499] usbcore: registered new interface driver btusb
    [   15.974432] input: BisonCam, NB Pro as /devices/pci0000:00/0000:00:1d.0/usb4/4-1/4-1.6/4-1.6:1.0/input/input13
    [   15.974539] usbcore: registered new interface driver uvcvideo
    [   15.974540] USB Video Class driver (1.1.1)

```

Any ideas anyone?

---

### Post by branau on 2015-07-10
Turns out it's either a problem with the device's hardware or it could be Android 5.1.1, since two other android devices that I have (a phone and a tablet) appear when connected and can be interacted with no problem. I tested multiple USB cables, multiple USB ports, Ubuntu 15.04 and Windows 8.1 (on a couple of different systems) and nothing worked. I even called LG Customer Service and they recommended I send it in for a technical diagnosis.

---

