---
title: "bluetooth dongle help"
date: 2008-01-08
forum: General Help
---

### Post by malfist on 2008-01-08
I'm trying to hook up my bluetooth dongle to my computer, but I can't get kbluetooth to detect it. This is as far as I have gotten:
dmesg:
```

[ 1585.981846] usb 1-1: new full speed USB device using ohci_hcd and address 3
[ 1586.161666] usb 1-1: device descriptor read/64, error -62
[ 1586.445349] usb 1-1: device descriptor read/64, error -62
[ 1586.725051] usb 1-1: new full speed USB device using ohci_hcd and address 4
[ 1586.904858] usb 1-1: device descriptor read/64, error -62
[ 1587.224837] usb 1-1: configuration #1 chosen from 1 choice
[ 1587.498215] usbcore: registered new interface driver hci_usb

```

lsusb:
```

jerome@jerome-desktop:~$ lsusb 
Bus 003 Device 005: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)
Bus 003 Device 004: ID 05e3:0760 Genesys Logic, Inc. Card Reader
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 06a3:8020 Saitek PLC 
Bus 002 Device 002: ID 04b4:0033 Cypress Semiconductor Corp. 
Bus 002 Device 001: ID 0000:0000  

```

hciconfig returns nothing.

Can anyone help me out?

It's a GFM 4020 Bluetooth Audio/PC Adaptor

edit: Only trying to use it with a headset for skype.

---

### Post by malfist on 2008-01-08
error goes away on reboot if device is plugged in:
```

dmesg | grep usb
[   32.173280] usbcore: registered new interface driver usbfs
[   32.173311] usbcore: registered new interface driver hub
[   32.173334] usbcore: registered new device driver usb
[   32.249731] usb usb1: configuration #1 chosen from 1 choice
[   32.409496] usb usb2: configuration #1 chosen from 1 choice
[   32.655125] usb 1-3: new full speed USB device using ohci_hcd and address 2
[   32.655246] usb usb3: configuration #1 chosen from 1 choice
[   33.833837] usb 3-5: new high speed USB device using ehci_hcd and address 4
[   33.976444] usb 3-5: configuration #1 chosen from 1 choice
[   34.213423] usb 3-6: new high speed USB device using ehci_hcd and address 5
[   34.350461] usb 3-6: configuration #1 chosen from 1 choice
[   34.352428] usbcore: registered new interface driver libusual
[   34.652943] usb 2-1: new low speed USB device using ohci_hcd and address 2
[   34.857183] usb 2-1: configuration #1 chosen from 1 choice
[   35.160391] usb 2-2: new low speed USB device using ohci_hcd and address 3
[   35.391674] usb 2-2: configuration #1 chosen from 1 choice
[   35.395766] usb-storage: device found at 4
[   35.395768] usb-storage: waiting for device to settle before scanning
[   35.395796] usbcore: registered new interface driver usb-storage
[   35.395910] usbcore: registered new interface driver hiddev
[   35.401832] input: USB HID v1.10 Mouse [HID 04b4:0033] on usb-0000:00:02.1-1
[   35.417803] input: USB HID v1.11 Keyboard [Chicony Saitek Eclipse Keyboard] on usb-0000:00:02.1-2
[   35.447608] input,hiddev96: USB HID v1.11 Device [Chicony Saitek Eclipse Keyboard] on usb-0000:00:02.1-2
[   35.447620] usbcore: registered new interface driver usbhid
[   35.447624] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   40.387197] usb-storage: device scan complete
[   46.248337] usb 3-6: reset high speed USB device using ehci_hcd and address 5
[   49.373076] usbcore: registered new interface driver ndiswrapper
[   49.373475] usbcore: registered new interface driver xpad

```

lsusb:
```

lsusb
Bus 003 Device 005: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)
Bus 003 Device 004: ID 05e3:0760 Genesys Logic, Inc. Card Reader
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 06a3:8020 Saitek PLC 
Bus 002 Device 002: ID 04b4:0033 Cypress Semiconductor Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

Can't tell you which is the bluetooth device, but no -62 error.

KBluetooth still doesn't detect it.

edit: upon unplug and replug, dmesg gives:
```

[  436.091196] usb 1-1: new full speed USB device using ohci_hcd and address 3

```
But device 3 in lsusb is my saitek keyboard...

---

### Post by malfist on 2008-01-09
sorry to bump but I'd really like help on this...

---

