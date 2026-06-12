---
title: "USB 3.0 Host with XHCI driver runs with USB-2.00 capabilities"
date: 2017-07-19
forum: General Help
---

### Post by lammert-nijhof on 2017-07-19
My laptop HP Elitebook 8460p has two Super Speed USB connectors, one runs at USB 2.0 speed and the other at USB 3.0 speed. 
>   *-usb
                description: USB controller
                product: uPD720200 USB 3.0 Host Controller
                vendor: NEC Corporation
                physical id: 0
                bus info: pci@0000:25:00.0
                version: 04
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi msix pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:19 memory:d4400000-d4401fff
              *-usbhost:0
                   product: xHCI Host Controller
                   vendor: Linux 4.8.0-58-generic xhci-hcd
                   physical id: 0
                   bus info: usb@3
                   logical name: usb3
                   version: 4.08
------->          capabilities: usb-2.00
                   configuration: driver=hub slots=2 speed=480Mbit/s
              *-usbhost:1
                   product: xHCI Host Controller
                   vendor: Linux 4.8.0-58-generic xhci-hcd
                   physical id: 1
                   bus info: usb@4
                   logical name: usb4
                   version: 4.08
------->          capabilities: usb-3.00
                   configuration: driver=hub slots=2 speed=5000Mbit/s

I have tested both connections with an Ewent USB 3.1 to SATA HDD adaptor, at one connector it is reading at 80 MB/s (the max disk read speed of the 320GB Seagate) at the other it only reads at 31 MB/s.
I use Ubuntu 16.04 up-to-date with Linux 4.8.0-58 and the BIOS is at its latest version.
Two questions:

1. Why that difference?
2. How can I change those capabilities of the USB connector.

---

### Post by efflandt on 2017-07-19
I know that some devices may end up with different USB ID depending upon whether they are connected to USB 2.0 or 3.0. So it may have one as USB 2.0 port for compatibility with such devices. Although, the only device I specifically heard of that ends up with different USB IDs is a racing (steering) wheel for gaming, and some games may not recognize its USB 3.0 ID.

While I do not have anything with USB 3.0 other than a slow laptop, I have a Logitech G29 racing wheel, but that is not my problem. My problem is that the Linux version of a game does not recognize the G29 yet, so I have to pre-configure it in Linux (with a script) in an alternate mode as a G27 (which gives it the G27 USB ID). Then it works in the game.

---

### Post by lammert-nijhof on 2017-07-20
The laptop also has 2 USB 2.0 connectors and I can use USB 2.0 devices in both 3.0 connectors. I think they even run a little bit faster there. By design USB 3.0 is compatible with USB 2.0.

---

