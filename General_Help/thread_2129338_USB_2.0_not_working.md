---
title: "USB 2.0 not working"
date: 2013-03-25
forum: General Help
---

### Post by jj00 on 2013-03-25
I am currently running Xubuntu 12.10 on a GIGABYTE GA-990FXA-UD3 AM3+ AMD 990FX SATA 6Gb/s USB 3.0 ATX AMD Motherboard.


It has 2 x USB 3.0 ports which work perfectly fine, however it also has 8 x USB 2.0 ports which aren't working at all.  These ports worked fine in Windows and my old motherboard had USB 2.0 ports which worked fine in Xubuntu 12.10.


Linux enterprise 3.5.0-26-generic #42-Ubuntu SMP Fri Mar 8 23:18:20 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
Results of dmesg: [http://paste.ubuntu.com/5648355/](http://paste.ubuntu.com/5648355/)
Results of lsusb: [http://paste.ubuntu.com/5648348/](http://paste.ubuntu.com/5648348/)

Anyone know what's up?

---

### Post by JoeStIdes on 2013-04-07
I'm in the same boat as you with the same motherboard. Only two USB's seem to work but lsusb command lists them all

[HTML]Bus 008 Device 002: ID 046d:c051 Logitech, Inc. G3 (MX518) Optical Mouse
Bus 008 Device 003: ID 0846:6a00 NetGear, Inc. WG111v2 54 Mbps Wireless [RealTek RTL8187L]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
[/HTML]

 Is your wired network card working? Mine keeps on trying to connect but never does. PM me with your solution to this so I don't hijack your thread. As you can see I am running from an old usb wireless adapter on the port not used by my mouse. We should start a support group... lol

---

### Post by raduweiss on 2013-04-12
I have the exact same issue with the[FONT=arial] Gigabyte 990XA-UD3 Socket AM3 and Ubuntu 12.10. Only the two USB 3.0 ports work, and the network card keeps connecting and disconnecting. The lsusb is the same. Have you made any progress, or is the board just not compatible with Ubuntu 12.10?[/FONT]

---

### Post by JoeStIdes on 2013-04-17
well it seems I can get the front two usb's to work but it shuts off the ps2 keyboard when I plug something in them, nice

---

### Post by eddiebeck on 2013-04-20
> **JoeStIdes said:**
> well it seems I can get the front two usb's to work but it shuts off the ps2 keyboard when I plug something in them, nice

I'm also having the same problem. How did you get the front ports to work?

---

### Post by quattro_cs on 2013-04-23
Any updates? I am having the same issue with USB 2.0 ports and the NIC as well.

---

### Post by ed-arevalo-ruiz on 2013-09-19
Hello, I had the same problem with my computer, Motherboard Gigabyte GA-970A-D3, Processor AMD FX8120, In the BIOS there is an option IOMMU enable it, that fixed the problem in my computer

---

### Post by swblake on 2014-04-29
Thank you, ed! That worked as advertised on my Gigabyte GA-990FXA-UD3 M/B. I would have NEVER discovered that.

---

