---
title: "Gutsy: is there a way to read a camera connected through a usb hub?"
date: 2007-11-10
forum: General Help
---

### Post by mdurham on 2007-11-10
Cheers, Mike

---

### Post by geraldm on 2007-11-10
A working driver for the camera would work with and/or without the hub.
The only extra problem that a hub introduces is that there may be more devices on the bus
and some performance may be slower as a result.  For cameras that are not self-powered,
the hub might be required to provide the power through the USB cable, and that may mean
that the camera must be the only device at its connection port -- no peer devices at its level.

Gerald

---

### Post by mdurham on 2007-11-11
> A working driver for the camera would work with and/or without the hub.
Thanks for the reply geraldm but I can't agree with it. Using usbview, I can see a camera or memory stick if plugged into the hub but it's impossible to access them. If I plug these devices into a non-hub usb socket they work fine, no problems with drivers. In other words the drivers work fine when the devices are not plugged into a hub, so my reasoning is that it's a driver problem. My 'working drivers' don't always work!
Cheers, Mike

---

