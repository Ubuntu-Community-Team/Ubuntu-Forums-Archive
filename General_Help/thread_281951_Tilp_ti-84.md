---
title: "Tilp ti-84"
date: 2006-10-21
forum: General Help
---

### Post by bkanuka on 2006-10-21
I cannot get tilp to work for the life of me.  I have a ti-84+.  I have tried tilp, tilp2, SilverLink, DirectLink, and nothing works.  
Tilp2 does not detect the calculator, and when I put in values I get a Segmentation fault.  
Tilp gives me the error:```
Msg: Error occurred while initializing the libusb.
Cause: Check that your cable is connected or not stalled. Check your libusb and usbfs, too.
System: Device or resource busy (errno = 16)
```
The last bit of output says:```
ticables: mapping I/O...
ticables: registering cable...
ticables: list of settings:
ticables:   cable: SilverLink
ticables:   port: USB port #1
ticables:   method: user mode (ioctl)
ticables:   device name: /dev/tiusb0
ticables:   delay value: 10
tifiles : settings:
tifiles :   calc type: TI84+
ticalcs : settings:
ticalcs :   calc type: TI84+
ticables: Found <SilverLink>.
ticables: err: usb_set_configuration (could not set config 1: Device or resource busy).
```
Has anyone gotten this working?

---

### Post by Keen101 on 2007-07-30
I have the same problem.

I get this message:

Msg: Unable to open/find a USB device.
Cause: Check that your cable is connected or not stalled. Check you rlibusb and usbfs, too.
System: Inappropriate ioctl for device (errno = 25)

---

### Post by splintercellguy on 2007-07-30
Bah, don't bump old threads :(. See [https://launchpad.net/ubuntu/+source/tilp/+bugs](https://launchpad.net/ubuntu/+source/tilp/+bugs)

---

