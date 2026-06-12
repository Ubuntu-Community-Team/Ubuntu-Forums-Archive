---
title: "Can't mount MTP device"
date: 2018-09-29
forum: General Help
---

### Post by fabioscheer on 2018-09-29
Hello,

Every now and then my PC running Ubuntu 16.04.5 is unable to connect to my phone and displays the message "MTP-Device [usb:004,002] can't be opened".

lsusb shows me
```

Bus 002 Device 003: ID 045e:028e Microsoft Corp. Xbox360 Controller
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 17e9:430c DisplayLink 
Bus 004 Device 002: ID 2109:0811 VIA Labs, Inc. Hub
Bus 004 Device 012: ID 18d1:4ee1 Google Inc. Nexus 4 / 10
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 004: ID 046a:0023 Cherry GmbH CyMotion Master Linux Keyboard G230
Bus 003 Device 003: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 003 Device 002: ID 2109:0811 VIA Labs, Inc. Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
Detecting my Google Pixel XL as it should. 

Output of dmesg however states
> 
[  447.604029] usb 4-1: USB disconnect, device number 10
[  456.571978] usb 4-1: new SuperSpeed USB device number 11 using xhci_hcd
[  456.596772] usb 4-1: New USB device found, idVendor=18d1, idProduct=4ee1
[  456.596774] usb 4-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  456.596783] usb 4-1: Product: Pixel XL
[  456.596784] usb 4-1: Manufacturer: Google
[  456.596785] usb 4-1: SerialNumber: HT69R0202693
[  456.597330] usb 4-1: Not enough bandwidth for new device state.
[  456.597347] usb 4-1: can't set config #1, error -28
[  456.644954] usb 4-1: Not enough bandwidth for new device state.


Which from my point of view doesn't look like what it's supposed to look like, but i may be wrong.


i have already gone through these entries on the forum but it did not help at all.
[https://ubuntuforums.org/showthread.php?t=2312327](https://ubuntuforums.org/showthread.php?t=2312327)
[https://ubuntuforums.org/showthread.php?t=2226702](https://ubuntuforums.org/showthread.php?t=2226702)


If any more information is needed please ask and i will try to provide it to the best of my abilty.
Thanks in advance.


Sincerely, 
Fabio Scheer

---

