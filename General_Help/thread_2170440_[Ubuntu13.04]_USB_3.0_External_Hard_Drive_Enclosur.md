---
title: "[Ubuntu13.04] USB 3.0 External Hard Drive Enclosure Recognized as USB2.0"
date: 2013-08-26
forum: General Help
---

### Post by boshkash1151 on 2013-08-26
I have the following configuration :4Bay external hard drive enclosure connected to a USB3.0 PCI-E card to my Ubuntu 13.04 box. 

Whenever I try to connect the enclosure, the lsusb -t command returns the device as a USB2.0 connected and consequently the speed drops from 5Gbps to 480Mbps. 

Sometimes the device gets recognized as a USB3.0 if i did the following : system is on & enclosure is connected -> power off the enclosure -> remove usb 3.0 cable-> turn it back on  ->plug in the usb3.0 cable -> the enclosure is not recognized -> reboot ->  enclosure recognized as USB3.0


Thanks

---

### Post by bkline on 2013-08-27
This thread might be helpful:

[http://ubuntuforums.org/showthread.php?t=2054604](http://ubuntuforums.org/showthread.php?t=2054604)

---

### Post by boshkash1151 on 2013-08-27
> **bkline said:**
> This thread might be helpful:

[http://ubuntuforums.org/showthread.php?t=2054604](http://ubuntuforums.org/showthread.php?t=2054604)

still nothing
I tried upgrading the firmware as that was the only solution i have not tried yet, but still the USB3.0 enclosure is recognized as USB2.0 and I would still need to do the same scenario explained earlier to get it working at USB 3 speeds

---

