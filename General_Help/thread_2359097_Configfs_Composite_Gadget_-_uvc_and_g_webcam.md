---
title: "Configfs Composite Gadget - uvc and g_webcam"
date: 2017-04-20
forum: General Help
---

### Post by e.u.mikhailov on 2017-04-20
Hi! 

I'm trying to implement g_webcam ([https://wiki.tizen.org/wiki/USB/Linux_USB_Layers/Configfs_Composite_Gadget/Usage_eq._to_g_webcam.ko](https://wiki.tizen.org/wiki/USB/Linux_USB_Layers/Configfs_Composite_Gadget/Usage_eq._to_g_webcam.ko)) using Configfs Composite Gadget on Ubuntu 17.04 (kernel 4.10.0). 

But system freezes after 

modprobe dummy_hcd
modprobe g_webcam

I'd tried to comment line f_uvc.c ([http://lxr.free-electrons.com/source/drivers/usb/gadget/function/f_uvc.c#L440](http://lxr.free-electrons.com/source/drivers/usb/gadget/function/f_uvc.c#L440)) and freeze stopped, but lsusb returns only udc hub, no webcam device. 

Can anybody help?

---

