---
title: "XP will not autodetect USB with VMPlayer"
date: 2007-07-31
forum: General Help
---

### Post by miatawnt2b on 2007-07-31
I am running VMPlayer 1.0.2 under Feisty and booting into my XP partition which works great.   If I plug in a USB device and let Feisty detect it, then run the VM, VMPlayer sees the USB device and everything works.  However, VMPlayer is already running, and I connect a USB device, VMPlayer never sees the device.  Do I need to config something other than the USB setting in the vmx file?

usb.present = "TRUE" 
usb.generic.autoconnect = "TRUE"
usb.startConnected = "TRUE"

Thanks,
-J

---

### Post by testube_babies on 2007-07-31
I think that's just how it works.  I've never been able to get VMware to see a device that has been plugged in after the program starts.

---

### Post by nitro_n2o on 2007-07-31
[http://www.vmware.com/support/ws45/doc/devices_usb_ws.html](http://www.vmware.com/support/ws45/doc/devices_usb_ws.html)
check out the section " Using USB with a Linux Host"

---

