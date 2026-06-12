---
title: "usb 1-1: device v0424 p3fb7 is not supported"
date: 2015-04-08
forum: General Help
---

### Post by jeanvaljean2 on 2015-04-08
Hi,

I've installed ubuntu in a beaglebone black ([http://elinux.org/BeagleBoardUbuntu](http://elinux.org/BeagleBoardUbuntu)).
I'm trying to connect a audio interface through the usb port, but when i plug in, using dmesg i have the following message:

>  [  20.729985] IPv6: ADDRCONF(NETDEV_UP): usb0: link is not ready[   24.022617] init: plymouth-upstart-bridge main process ended, respawning
[   32.881763] musb-hdrc musb-hdrc.1.auto: VBUS_ERROR in a_wait_bcon (89, <AValid), retry #1, port1 00000104
[   33.517814] usb 1-1: new high-speed USB device number 2 using musb-hdrc
[   33.659037] usb 1-1: device v0424 p3fb7 is not supported
[   33.664662] usb 1-1: New USB device found, idVendor=0424, idProduct=3fb7
[   33.664702] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3




Do i need to update the kernel?

Regards

---

