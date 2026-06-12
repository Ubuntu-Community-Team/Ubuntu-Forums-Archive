---
title: "Galaxy S4 (Android 4.2.2.) not recognized"
date: 2013-11-01
forum: General Help
---

### Post by Inoki on 2013-11-01
Hey everyone,

I'm having issues with my Galaxy S4 on Xubuntu 12.04.3 x64, I plug the phone in, but it isn't recognized. On Ubuntu 13.04 this worked, even though with a few glitches here and there, but most of the time. When I plug it in, on the phone it says it's plugged as a media device (MTP), but it simply won't show up on the computer and I can't browse my files. The phone is brand new.

Output of lsusb:
```
inoki@innerdistance-Satellite-L650:~$ lsusbBus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 10f1:1a2a Importek 
Bus 002 Device 008: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 011: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 002 Device 012: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 014: ID 04e8:6860 Samsung Electronics Co., Ltd GT-I9100 Phone [Galaxy S II]



```

---

### Post by Mark Phelps on 2013-11-01
Sorry, but you are unlikely to get it working with that Ubuntu version.  

The latest version (3.10) can recognize the phone -- at least, it does with my S3.

---

### Post by ajgreeny on 2013-11-01
I'm sure it is possible to get this working as Xubuntu 12.04 connects to my android 4.1 Acer Iconia with no problem.

Perhaps you need to follow the info at [http://www.acertabletforum.com/forum/acer-iconia-tab-a500-general-discussions/129-connecting-via-usb-linux-ubuntu.html](http://www.acertabletforum.com/forum/acer-iconia-tab-a500-general-discussions/129-connecting-via-usb-linux-ubuntu.html) which is what was needed before I had any success.  I made minor changes to the name of the mountpoint to suit my tablet name, but otherwise all was the same.

---

### Post by Inoki on 2013-11-01
That's odd, my GF's netbook has the same installed and her iPhone 4 was recognized, so I don't understand why Android is not. Thanks anyway.

---

### Post by Inoki on 2013-11-01
> **ajgreeny said:**
> I'm sure it is possible to get this working as Xubuntu 12.04 connects to my android 4.1 Acer Iconia with no problem.

Perhaps you need to follow the info at [http://www.acertabletforum.com/forum/acer-iconia-tab-a500-general-discussions/129-connecting-via-usb-linux-ubuntu.html](http://www.acertabletforum.com/forum/acer-iconia-tab-a500-general-discussions/129-connecting-via-usb-linux-ubuntu.html) which is what was needed before I had any success.  I made minor changes to the name of the mountpoint to suit my tablet name, but otherwise all was the same.
Thank you! This worked with gMTP!

---

### Post by ajgreeny on 2013-11-01
Wonderful !

---

