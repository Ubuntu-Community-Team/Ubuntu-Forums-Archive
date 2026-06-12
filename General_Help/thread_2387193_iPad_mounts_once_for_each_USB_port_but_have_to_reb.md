---
title: "iPad mounts once for each USB port but have to reboot to mount again"
date: 2018-03-15
forum: General Help
---

### Post by marty-millercrispe on 2018-03-15
I'm on Ubuntu 17.10.  I connect my iPad and 'Trust this computer'.  It mounts fine and I can copy files onto my iPad.
I then unmount it (click the 'eject' button in Nemo) and if I try to connect again Ubuntu makes a sound but it does not mount.
If I then change to another USB port it connects but again after I disconnect it won't mount again in any of the USB ports used.  Once I'm out of USB ports I have to reboot Ubuntu to get it to work again.

I'm not sure where to look to troubleshoot but here is the last few lines of dmesg
```
[  123.396321] usb 1-2: new high-speed USB device number 4 using xhci_hcd[  123.541075] usb 1-2: New USB device found, idVendor=05ac, idProduct=12ab
[  123.541085] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  123.541091] usb 1-2: Product: iPad
[  123.541098] usb 1-2: Manufacturer: Apple Inc.
[  123.541104] usb 1-2: SerialNumber: f4502336fbe696c3d4e8571331f5e803c39037a6
[  124.964359] ipheth 1-2:4.2: Apple iPhone USB Ethernet device attached
[  124.964439] usbcore: registered new interface driver ipheth
[  124.972213] ipheth 1-2:4.2 enp0s20f0u2c4i2: renamed from eth0
[  124.991443] IPv6: ADDRCONF(NETDEV_UP): enp0s20f0u2c4i2: link is not ready
[  124.992044] IPv6: ADDRCONF(NETDEV_UP): enp0s20f0u2c4i2: link is not ready
[20569.516047] perf: interrupt took too long (2560 > 2500), lowering kernel.perf_event_max_sample_rate to 78000
[29842.636538] perf: interrupt took too long (3269 > 3200), lowering kernel.perf_event_max_sample_rate to 61000
[35579.994541] ipheth 1-2:4.2: ipheth_rcvbulk_callback: urb status: -71
[35579.995348] usb 1-2: USB disconnect, device number 4
[35580.035540] ipheth 1-2:4.2: Apple iPhone USB Ethernet now disconnected
[35870.631947] usb 1-2: new high-speed USB device number 5 using xhci_hcd
[35870.777588] usb 1-2: New USB device found, idVendor=05ac, idProduct=12ab
[35870.777598] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[35870.777605] usb 1-2: Product: iPad
[35870.777612] usb 1-2: Manufacturer: Apple Inc.
[35870.777617] usb 1-2: SerialNumber: f4502336fbe696c3d4e8571331f5e803c39037a6
[35876.099655] usb 1-2: USB disconnect, device number 5
[35881.111704] usb 1-1: new high-speed USB device number 6 using xhci_hcd
[35881.256954] usb 1-1: New USB device found, idVendor=05ac, idProduct=12ab
[35881.256965] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[35881.256972] usb 1-1: Product: iPad
[35881.256979] usb 1-1: Manufacturer: Apple Inc.
[35881.256984] usb 1-1: SerialNumber: f4502336fbe696c3d4e8571331f5e803c39037a6
[35881.339532] ipheth 1-1:4.2: Apple iPhone USB Ethernet device attached
[35881.359115] ipheth 1-1:4.2 enp0s20f0u1c4i2: renamed from eth0
[35881.611703] IPv6: ADDRCONF(NETDEV_UP): enp0s20f0u1c4i2: link is not ready
[35881.614659] IPv6: ADDRCONF(NETDEV_UP): enp0s20f0u1c4i2: link is not ready
[36101.825275] ipheth 1-1:4.2: ipheth_rcvbulk_callback: urb status: -71
[36101.825954] usb 1-1: USB disconnect, device number 6
[36101.859619] ipheth 1-1:4.2: Apple iPhone USB Ethernet now disconnected
[41730.499127] perf: interrupt took too long (4100 > 4086), lowering kernel.perf_event_max_sample_rate to 48750
[42929.614766] usb 1-1: new high-speed USB device number 7 using xhci_hcd
[42929.760395] usb 1-1: New USB device found, idVendor=05ac, idProduct=12ab
[42929.760405] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[42929.760412] usb 1-1: Product: iPad
[42929.760419] usb 1-1: Manufacturer: Apple Inc.
[42929.760424] usb 1-1: SerialNumber: f4502336fbe696c3d4e8571331f5e803c39037a6



```

Edit:  
I found if I manually invoke this:

```
 [COLOR=#333333][FONT=&quot]sudo /usr/sbin/usbmuxd -U usbmux [/FONT][/COLOR]
```

The iPad mounts so I don't have to reboot.  But why does it work on every USB only once before having to do this if I plug into a 'used' USB port?

---

