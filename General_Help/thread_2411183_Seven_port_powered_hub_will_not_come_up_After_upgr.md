---
title: "Seven port powered hub will not come up After upgrade to 18.04"
date: 2019-01-26
forum: General Help
---

### Post by pouldney on 2019-01-26
I have a generic seven port powered USB hub 
   After upgrade to 18.04 it will no longer come up after boot
   If I unplug from USB port and Re plug the first half (4 ports) will come up
   Also if I unplug the power to the hub and boot the first half will come up
   
   I Tried
    /etc/defaults/grub
    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbcore.autosuspend=-1"
   
   
   Acer Aspire XC-605
   
-XC-605:~$ sudo lsusb -vs 04:7
Bus 004 Device 007: ID 05e3:0612 Genesys Logic, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               3.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         3 
  bMaxPacketSize0         9
  idVendor           0x05e3 Genesys Logic, Inc.
  idProduct          0x0612 
  bcdDevice           92.26
  iManufacturer           1 GenesysLogic
  iProduct                2 USB3.1 Hub

---

### Post by jdeca57 on 2019-01-26
An upgrade from what? My first impression would be that it is a hardware problem because well, generic devices just work unless you came from Windows and there was a driver. (but then it isn't generic of course)

---

