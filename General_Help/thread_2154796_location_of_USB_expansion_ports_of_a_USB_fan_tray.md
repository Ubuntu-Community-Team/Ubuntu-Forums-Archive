---
title: "location of USB expansion ports of a USB fan tray"
date: 2013-06-15
forum: General Help
---

### Post by twinturbotom on 2013-06-15
My macbook air has 1 usb port.  Sometimes I hook up a usb powered fan tray which has 4 usb ports.  I'm looking to see where / how these ports are registered on my system but can't.  Specifically I'm plugging in an Arduino which is registered as /dev/ttyACM0 when plugged directly into the macbook air usb port.  I believe it is interpreted as a serial device.

When I plug the arudino into one of the expansion ports of the fan tray I can't find it!

I've attemped searching dmesg and lsusb in all configurations (nothing plugged in, fan plugged in, arduino in fan, arduino direct) by piping output to files and comparing with no luck in locating the arduino when plugged into the fan tray.

Next I'll probably start plugging in other devices and see if this is just and arduino specific thing.

Any thoughts? or direction?

Thanks.

---

