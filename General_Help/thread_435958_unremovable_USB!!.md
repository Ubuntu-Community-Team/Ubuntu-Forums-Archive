---
title: "unremovable USB!!"
date: 2007-05-07
forum: General Help
---

### Post by mviroli on 2007-05-07
Hi,

I plugged a card reader on my usb port on a DELL D620...
After removing that, I found that the usb port was no longer working (with any usb device)
By the lsusb command I noticed that Ubuntu believes the card reader is still plugged!!
Is there any way to refresh the cache, or something similar?

---

### Post by Iarwain ben-adar on 2007-05-07
Can you try this ?
```
sudo umount /path/to/device
```


Iarwain

---

### Post by rai4shu2 on 2007-05-07
Is this a multi-card reader or just something like a PCMCIA device?

---

### Post by mviroli on 2007-05-08
> **Iarwain ben-adar said:**
> Can you try this ?
```
sudo umount /path/to/device
```


Iarwain

The problem is that it is not mounted!! Nothing appears on "/etc/mtab". The system just believes it is plugged.
lsusb gives:

Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 005: ID 04b4:8081 Cypress Semiconductor Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 007: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 001 Device 006: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 001 Device 005: ID 0b97:7761 O2 Micro, Inc. 
Bus 001 Device 004: ID 413c:a005 Dell Computer Corp. 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

Two lines are actually incorrect, those with O2 Micro..

In fact, even "ls /proc/bus/usb/001/" gives:

001  004  005  006  007

Should I just try to remove directories 005 and 007?

---

### Post by rai4shu2 on 2007-05-08
If you're using Feisty, it may be related to this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746/](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746/)

---

### Post by mviroli on 2007-05-08
I tried what they say but it didn't worked!
Should I file a bug or something?

---

### Post by rai4shu2 on 2007-05-08
I guess it's something different. Might be a good idea to file a bug report on that.

---

### Post by mviroli on 2007-05-08
Done, I'll let you know..
Thank you

---

### Post by aneas on 2007-05-13
> **mviroli said:**
> The problem is that it is not mounted!! Nothing appears on "/etc/mtab". The system just believes it is plugged.
lsusb gives:

Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 005: ID 04b4:8081 Cypress Semiconductor Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 007: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 001 Device 006: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 001 Device 005: ID 0b97:7761 O2 Micro, Inc. 
Bus 001 Device 004: ID 413c:a005 Dell Computer Corp. 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

Two lines are actually incorrect, those with O2 Micro..

In fact, even "ls /proc/bus/usb/001/" gives:

001  004  005  006  007

Should I just try to remove directories 005 and 007?

I have a brand new d620, I get the same O2 Micro devices from lsusb and I have never plugged in any card reader, I believe that is an internal chip not being used for anything or so. I remember something like that on windows too.

---

### Post by mviroli on 2007-05-14
Interesting, in fact I now see there is an integrated  smartcard reader in the laptop!!

So, why I do have a USB stick that is recognised (see by lsusb) from all USB ports except one???

---

