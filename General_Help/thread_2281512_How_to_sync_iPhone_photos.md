---
title: "How to sync iPhone photos?"
date: 2015-06-07
forum: General Help
---

### Post by PenguinLust on 2015-06-07
My iPhone 4S is bloated w/20Gb of photos, so I'd like to start removing them. Apparently this can be done by sync'ing. What is the modern way of doing this? My searches so far have just turned up a bunch of out-of-date articles and instructions on how to sync music *to* the iPhone.
When I try plugging in the iPhone, I get a popup saying "Unhandled Lockdown error (-20)" and the dmesg has:
> [15105.604184] usb 1-1: new high-speed USB device number 2 using ehci-pci
[15105.740275] usb 1-1: New USB device found, idVendor=05ac, idProduct=12a0
[15105.740289] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[15105.740300] usb 1-1: Product: iPhone
[15105.740309] usb 1-1: Manufacturer: Apple Inc.
[15105.740319] usb 1-1: SerialNumber: b8dcb364b56d88f3f38fe587aaa69c149e96e84a
[15107.691515] ipheth 1-1:4.2: Apple iPhone USB Ethernet device attached
[15107.695108] usbcore: registered new interface driver ipheth
[15108.497295] IPv6: ADDRCONF(NETDEV_UP): eth2: link is not ready
[15108.499223] IPv6: ADDRCONF(NETDEV_UP): eth2: link is not ready
[15795.359260] usb 1-1: USB disconnect, device number 2
[15795.380117] ipheth 1-1:4.2: Apple iPhone USB Ethernet now disconnected
[15803.220098] usb 1-1: new high-speed USB device number 3 using ehci-pci
[15803.356011] usb 1-1: New USB device found, idVendor=05ac, idProduct=12a0
[15803.356063] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[15803.356074] usb 1-1: Product: iPhone
[15803.356083] usb 1-1: Manufacturer: Apple Inc.
[15803.356093] usb 1-1: SerialNumber: b8dcb364b56d88f3f38fe587aaa69c149e96e84a
[15803.503884] ipheth 1-1:4.2: Apple iPhone USB Ethernet device attached
[15803.699362] IPv6: ADDRCONF(NETDEV_UP): eth2: link is not ready
[15803.700658] IPv6: ADDRCONF(NETDEV_UP): eth2: link is not ready

I'm running Lubuntu 14.04.2.

---

### Post by tgalati4 on 2015-06-07
Install the google photo app then upload your photos.  You will probably need to give the google photo app permission to touch your photo library.  On the desktop, using Chrome you should be able to see your google photos.  Once you have verified that they are in the cloud, you can delete them from your phone and use the google photo app to search and retrieve them.

---

### Post by PenguinLust on 2015-06-07
I can't find the google photo app in the repository or by Googling it. Also, I'm not sure I want to use the cloud for this. 20Gb is rather a lot, even if there is a free cloud service that does that capacity.

---

