---
title: "&quot;usb 1-1.4: string descriptor 0 read error: -22&quot;"
date: 2014-10-06
forum: General Help
---

### Post by Logan_Hartman on 2014-10-06
When I start Ubuntu, before the login screen, I get an error that says "usb 1-1.4: string descriptor 0 read error: -22". What is this, and how do I fix it? Or is it just a benign complication?

Ubuntu 14.04 x64 on Acer Aspire V5-571P

---

### Post by matt_symes on 2014-10-08
Hi

It would be useful to know what device it is.

Open a terminal and type 

```
lsusb -t
```

Post the output into your next post and we can see.

Kind regards

---

### Post by Logan_Hartman on 2014-10-08
lsusb -t

/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 5000M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 480M
    |__ Port 1: Dev 4, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
    |__ Port 3: Dev 2, If 0, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 4: Dev 3, If 0, Class=Video, Driver=uvcvideo, 480M
    |__ Port 4: Dev 3, If 1, Class=Video, Driver=uvcvideo, 480M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/8p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/6p, 480M
        |__ Port 4: Dev 4, If 0, Class=Wireless, Driver=btusb, 12M
        |__ Port 4: Dev 4, If 1, Class=Wireless, Driver=btusb, 12M

---

### Post by Logan_Hartman on 2014-10-14
If anyone else needs me to run a command I'm happy to if it'll give them information to help...

---

### Post by matt_symes on 2014-10-17
Hi

Sorry for the delay in replying. I have been very busy.

> /:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    |__ Port 4: Dev 4, If 0, Class=Wireless, Driver=btusb, 12M
        |__ Port 4: Dev 4, If 1, Class=Wireless, Driver=btusb, 12M

It looks to be an error reading a descriptor from your USB Bluetooth device.

Do you use Bluetooth and, if so, has it given you any problems ?

Kind regards

---

### Post by Logan_Hartman on 2014-10-17
That's alright I just didn't know if anyone needed more information.

My Bluetooth seems to work fine, but I don't use it often enough to know truthfully.

---

### Post by matt_symes on 2014-10-18
Hi

> **Logan_Hartman said:**
> That's alright I just didn't know if anyone needed more information.

My Bluetooth seems to work fine, but I don't use it often enough to know truthfully.

If it does not seem to be causing you a problem then i would not worry about it. 

It could be caused by a number of things including firmware bugs in the hardware itself as well as problems with the USB subsystem and drivers.

Linux has a habit of telling you most things it finds unusual if they cause problems or not. Other operating systems are not so verbose. It's one of the things i like about Linux.

Kind regards

---

### Post by Logan_Hartman on 2014-10-18
Okay, thank you.

---

