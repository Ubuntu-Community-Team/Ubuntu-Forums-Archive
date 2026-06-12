---
title: "bluetooth not recognized after upgrade to 14.04"
date: 2014-05-08
forum: General Help
---

### Post by ccerrillo on 2014-05-08
Hi,

I upgraded from 13.10 to 14.04 but now the bluetooth is not recognized, the tray icon dissapeared and if i go to bluetooth config there are no devices

What can i try?

Thanks!!

```
**$lsusb**
Bus 003 Device 002: ID 0930:0219 Toshiba Corp.
```

```
**$dmesd**
[    2.283509] usb 3-3: Product: Bluetooth USB Host Controller
[   14.359215] toshiba_bluetooth: Detected Toshiba ACPI Bluetooth device - installing RFKill handler
[   14.359240] toshiba_bluetooth: Re-enabling Toshiba Bluetooth
[   17.836397] Bluetooth: Core ver 2.17
[   17.836411] Bluetooth: HCI device and connection manager initialized
[   17.836417] Bluetooth: HCI socket layer initialized
[   17.836419] Bluetooth: L2CAP socket layer initialized
[   17.836421] Bluetooth: SCO socket layer initialized
[   21.309857] Bluetooth: Error in firmware loading err = -110,len = 448, size = 4096
[   21.309919] Bluetooth: Loading patch file failed
[   21.572675] Bluetooth: RFCOMM TTY layer initialized
[   21.572692] Bluetooth: RFCOMM socket layer initialized
[   21.572705] Bluetooth: RFCOMM ver 1.11
[   22.102303] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.102305] Bluetooth: BNEP filters: protocol multicast
[   22.102312] Bluetooth: BNEP socket layer initialized



```

---

### Post by ccerrillo on 2014-05-10
For those who have this problem, i solved it with those commands:

sudo modprobe -v ath3k
sudo modprobe -v btusb
sudo echo 0930 0219 > /sys/bus/usb/drivers/ath3k/new_id
sudo echo 0930 0219 > /sys/bus/usb/drivers/btusb/new_id 

Hope that this could help you guys! ;)

---

### Post by alessandro-grillini on 2014-08-04
> **ccerrillo said:**
> For those who have this problem, i solved it with those commands:

sudo modprobe -v ath3k
sudo modprobe -v btusb
sudo echo 0930 0219 > /sys/bus/usb/drivers/ath3k/new_id
sudo echo 0930 0219 > /sys/bus/usb/drivers/btusb/new_id 

Hope that this could help you guys! ;)


Great !!!!


I spent over a pair of days (and nights) with no success trying to make working the integrated Bluetooth on my Toshiba Saltellite L50d-B-12W when I found this post.
Thank you ccerrillo this solution is working fine on my laptop.


In my case "lsusb" told me the device is 0930 0225, so 
the commands I appended in the /etc/rc.local (so that they will be loaded at each startup) are :


modprobe -v ath3k
modprobe -v btusb
echo 0930 0225 > /sys/bus/usb/drivers/ath3k/new_id
echo 0930 0225 > /sys/bus/usb/drivers/btusb/new_id 


("sudo" is not necessary because the rc.local script is executed as root)


this made the trick.

Before I tried the other solution proposed in oldest posts : use "toshset" to enable the bluetooth
but it seems that the "toshset" is not more supported by the newest kernels ( I get the "required kernel Toshiba support not enabled").
Some people have recompiled the kernel, patching the toshiba_acpi module with an old script to make "toshset" working, but I luckily found this solution in the meantime and now I resolved definitively my last problem using Ubuntu on this laptop.

Thank you very much.

Sorry for my little english, I from Italy :-)


EDIT : 
I rejoiced too soon.
Ok the Bluetooth applet now is in the tray and I'm able to switch on-off  bluetooth end visibility, but the device is still not functioning.
It's not possible to add a new device (searched devices  list is empty, and at the other side the computer is not visible)

---

