---
title: "Hotplug/auto-mount not working?"
date: 2007-03-18
forum: General Help
---

### Post by graabein on 2007-03-18
Hi, I've been having this problem for some time now. When I insert a CD it don't show up on the desktop until I click it in Nautilus. Same goes for the iPod and external disk. 

This is somewhat annoying especially when I no longer can import photos with gTumb because it cannot detect a connected device. 

What service/module is missing? Maybe this is related to my GDM problem?

---

### Post by graabein on 2007-03-18
Error from gThumb:

> An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.



Solved with [https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250]("https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250")

---

