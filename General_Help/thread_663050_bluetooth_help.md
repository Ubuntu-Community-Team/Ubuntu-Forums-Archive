---
title: "bluetooth help"
date: 2008-01-09
forum: General Help
---

### Post by malfist on 2008-01-09
I can't get kbluetooth to detect my bluetooth adapter.

lsusb says this:
```

Bus 002 Device 004: ID 0b7a:07d0 Zeevo, Inc. 

```
dmesg shows:
```

[   35.887993] usb 2-3: new full speed USB device using ohci_hcd and address 4
[   36.104287] usb 2-3: configuration #1 chosen from 1 choice
[   36.107422] usbcore: registered new interface driver hiddev
[   36.107620] usb-storage: device found at 4

```

is the bluetooth adapter. I have no idea how to proceed, any advice?

---

### Post by geraldm on 2008-01-10
module driver loaded?
```

sudo modprobe hci_usb

```

Gerald

---

### Post by malfist on 2008-01-10
Doesn't seem to make a difference, heres more output from dmesg (device location changed).

```

[   34.971644] usb 2-2: new low speed USB device using ohci_hcd and address 3
[   35.206936] usb 2-2: configuration #1 chosen from 1 choice
[   35.210833] usbcore: registered new interface driver hiddev
[   35.511044] usb 1-1: new full speed USB device using ohci_hcd and address 3
[   35.727482] usb 1-1: configuration #1 chosen from 1 choice
[   36.030472] usb 1-3: new low speed USB device using ohci_hcd and address 4
[   36.210279] usb 1-3: device descriptor read/64, error -62
[   36.493972] usb 1-3: device descriptor read/64, error -62
[   36.773646] usb 1-3: new low speed USB device using ohci_hcd and address 5
[   36.953449] usb 1-3: device descriptor read/64, error -62
[   37.237132] usb 1-3: device descriptor read/64, error -62
[   37.516815] usb 1-3: new low speed USB device using ohci_hcd and address 6
[   37.924357] usb 1-3: device not accepting address 6, error -62
[   38.100165] usb 1-3: new low speed USB device using ohci_hcd and address 7
[   38.507709] usb 1-3: device not accepting address 7, error -62

```

lsusb:```

Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 06a3:8020 Saitek PLC 
Bus 002 Device 002: ID 04b4:0033 Cypress Semiconductor Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0b7a:07d0 Zeevo, Inc. 
Bus 001 Device 001: ID 0000:0000  
```

---

### Post by malfist on 2008-01-10
worked with bluez and got device working, now I just can't connect. dmesg is giving:
```

[ 1948.317199] hci_scodata_packet: hci0 SCO packet for unknown connection handle 1

```

---

### Post by malfist on 2008-01-10
Headset was difficult to connect, I'm assuming it working now.

---

