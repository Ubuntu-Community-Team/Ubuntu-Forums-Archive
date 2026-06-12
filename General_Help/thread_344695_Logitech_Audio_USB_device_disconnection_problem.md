---
title: "Logitech Audio USB device disconnection problem"
date: 2007-01-23
forum: General Help
---

### Post by yhan on 2007-01-23
Hi Experts !

I'm experiencing the following problem with all versions of Ubuntu. Using Edgy now

I have a USB Logitech USB headset which works fine, detected at connection, and so on. 
I usually use it with Skype. 
The problem is, when I disconnect the headset, the USB subsystem is not responding anymore... sometimes after a while it's coming back to life, sometime I need to reboot the box. 

It's like a process is still using the driver, and as the device is not there anymore, it's waiting for something... 

What can I do to prevent that problem happening ?

Thanks 

Yhan

---

### Post by yhan on 2007-01-31
I found something interesting, closing firefox free up the driver. So I supposed that FF or a process started from FF has open a lock on the driver, so closing FF flushes the lock, then the driver.

---

