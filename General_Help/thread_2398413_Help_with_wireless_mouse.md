---
title: "Help with wireless mouse"
date: 2018-08-11
forum: General Help
---

### Post by raleigh3 on 2018-08-11
I can not get my wireless mouse going. 

    lsusb -vv  only shows my corded mouse.(Logitech)
  
I have tried 4 different dongles.

  
Solaar did not help, so I guess it was not made by Logitech.

Can someone help me?

---

### Post by jeremy31 on 2018-08-11
So is it a bluetooth mouse or one of those that comes with it's own dongle?  No new devices show in lsusb when you plug in a dongle?  Anything in ```
dmesg | tail
```
After plugging one in?

---

### Post by raleigh3 on 2018-08-11
It did not come with it's own dongle.

Maybe I should have bought one that did ?

```
andy7_~$ dmesg | tail
[21306.915558] usb 3-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[21306.915561] usb 3-5: Product: BCM20702A0
[21306.915564] usb 3-5: Manufacturer: Broadcom Corp
[21306.915566] usb 3-5: SerialNumber: 5CF37080FFDA
[21307.032552] Bluetooth: hci0: BCM: chip id 63
[21307.034542] Bluetooth: hci0: BCM: features 0x07
[21307.051542] Bluetooth: hci0: BCM20702A
[21307.053556] Bluetooth: hci0: BCM20702A1 (001.002.014) build 0000
[21307.053592] bluetooth hci0: Direct firmware load for brcm/BCM20702A1-0a5c-21e8.hcd failed with error -2
[21307.053595] Bluetooth: hci0: BCM: Patch brcm/BCM20702A1-0a5c-21e8.hcd not found


```

```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 04f9:0045 Brother Industries, Ltd 
Bus 002 Device 003: ID 04a9:1760 Canon, Inc. 
Bus 002 Device 002: ID 045e:076d Microsoft Corp. LifeCam HD-5000
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 0a5c:21e8 Broadcom Corp. BCM20702A0 Bluetooth 4.0
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 003: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 006 Device 002: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by jeremy31 on 2018-08-11
I have that same device ID for bluetooth chip, try
```
wget https://s3.amazonaws.com/plugable/bin/fw-0a5c_21e8.hcd
sudo cp fw-0a5c_21e8.hcd /lib/firmwarebrcm/BCM20702A1-0a5c-21e8.hcd
```
Shutdown and boot

---

### Post by raleigh3 on 2018-08-11
Thanks Jeremy.

It didn't work.

But I found a Logitech m325 mouse on sale that came with a dongle.

Worked right out of the box.

---

