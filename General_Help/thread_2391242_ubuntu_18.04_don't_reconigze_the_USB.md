---
title: "ubuntu 18.04 don't reconigze the USB"
date: 2018-05-07
forum: General Help
---

### Post by gedas07 on 2018-05-07
After update  ubuntu 18.04 my PC don't recognize the External usb , but if I write in terminal lsusb , i see the USB , but in Nautilus don't see

---

### Post by deadflowr on 2018-05-07
So I assume not showing in nautilus you means not showing in Other Locations, yes?
Does it get listed in the parted or fdisk list commands:
```
sudo parted -l 
sudo fdisk -l
```

---

### Post by gedas07 on 2018-05-07
No with this command doesn't see
but with sudo lsusb i see
> Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 8087:07dc Intel Corp. 
Bus 002 Device 005: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 002 Device 004: ID 05ac:0250 Apple, Inc. Aluminium Keyboard (ISO)
Bus 002 Device 002: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 002 Device 011: ID 0951:1603 Kingston Technology DataTraveler 1GB/2GB Pen Drive
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

IS the kingston data traveler

---

### Post by deadflowr on 2018-05-07
What shows in Disks?

---

### Post by gedas07 on 2018-05-08
in disks only see my 2 internal disks, but not my usb disk

---

### Post by aederson on 2018-12-09
I'm having the same problem. 

Ubuntu 18.04 or 18.10 is not recognizing any usb flash drive at all. In any USB at the computer. 

If i plug a usb headset at the same port or mouse/keyboard it works. Also, the flash drivers works on other computers.

Also, nothing happens on dmesg when i plug/unplug the flash driver.

To clarify:
* The flash usb stick is working
* The usb port works for other devices
* dmesg does NOT show anything when plugging a flash driver
* happens with all flash drivers

My computer is a asus zephyrus m.

Did you solved your problem?

---

