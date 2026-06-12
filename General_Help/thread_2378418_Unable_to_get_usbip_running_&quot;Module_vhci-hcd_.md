---
title: "Unable to get usbip running &quot;Module vhci-hcd not found&quot;"
date: 2017-11-23
forum: General Help
---

### Post by abjorshammar on 2017-11-23
Hi,

I have a server running 16.04.3, 4.4.0-101-generic where I want to "mount" a remotely attached USB-device over usbip. 
The server part (raspbian stretch) is running fine, and on my Ubuntu machine I can list the remote device with no problem:

```
# usbip list -r 10.83.10.231
usbip: error: failed to open /usr/share/hwdata//usb.ids
Exportable USB devices
======================
 - 10.83.10.231
      1-1.5: unknown vendor : unknown product (0403:6001)
           : /sys/devices/platform/soc/3f980000.usb/usb1/1-1/1-1.5
           : (Defined at Interface level) (00/00/00)

```

However when I try to mount I get this error:

```
# usbip attach -r 10.83.10.231 -b 1-1.5
libusbip: error: udev_device_new_from_subsystem_sysname failed
usbip: error: open vhci_driver
usbip: error: query

```
Easy, just modprobe vhci-hcd, right? No.

```
# modprobe vhci-hcd
modprobe: FATAL: Module vhci-hcd not found in directory /lib/modules/4.4.0-101-generic

```

I've installed **linux-tools-generic**, but it doesn't help...

---

