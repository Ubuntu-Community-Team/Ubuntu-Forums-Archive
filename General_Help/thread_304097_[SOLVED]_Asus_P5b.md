---
title: "[SOLVED] Asus P5b"
date: 2006-11-21
forum: General Help
---

### Post by gerases on 2006-11-21
Hello,

I have an ASUS P5B and running 2.6.15-27-686. I can't get Ubuntu to recognize the FireWire subsystem. I'm attaching the output of lspci. 

Also, the board has 4 SATA connections and 1 IDE connector. When I connect an IDE drive the BIOS detects it correctly but I can't find it in Ubuntu. I've never mixed SATA and IDE drives before, so I don't know if there are any gotchas here. Would appreciate any ideas.

0000:00:00.0 Host bridge: Intel Corporation: Unknown device 29a0 (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation: Unknown device 29a1 (rev 02)
0000:00:1a.0 USB Controller: Intel Corporation: Unknown device 2834 (rev 02)
0000:00:1a.1 USB Controller: Intel Corporation: Unknown device 2835 (rev 02)
0000:00:1a.7 USB Controller: Intel Corporation: Unknown device 283a (rev 02)
0000:00:1b.0 0403: Intel Corporation: Unknown device 284b (rev 02)
0000:00:1c.0 PCI bridge: Intel Corporation: Unknown device 283f (rev 02)
0000:00:1c.3 PCI bridge: Intel Corporation: Unknown device 2845 (rev 02)
0000:00:1c.4 PCI bridge: Intel Corporation: Unknown device 2847 (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation: Unknown device 2830 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation: Unknown device 2831 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation: Unknown device 2832 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation: Unknown device 2836 (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
0000:00:1f.0 ISA bridge: Intel Corporation: Unknown device 2810 (rev 02)
0000:00:1f.2 IDE interface: Intel Corporation: Unknown device 2820 (rev 02)
0000:00:1f.3 SMBus: Intel Corporation: Unknown device 283e (rev 02)
0000:00:1f.5 IDE interface: Intel Corporation: Unknown device 2825 (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation GeForce 6200 TurboCache(TM) (rev a1)
0000:02:00.0 IDE interface: Unknown device 197b:2363 (rev 02)
0000:03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd.: Unknown device 8168 (rev 01)

---

### Post by nakko on 2006-12-30
I don't think the P5B has firewire. Just USB 2.0.
Which is a shame because I have a firewire port on the front of my case.
Does your motherboard have a firewire port on it somewhere?

---

### Post by sebi k on 2007-01-02
> **gerases said:**
> Also, the board has 4 SATA connections and 1 IDE connector. When I connect an IDE drive the BIOS detects it correctly but I can't find it in Ubuntu. I've never mixed SATA and IDE drives before, so I don't know if there are any gotchas here. Would appreciate any ideas.This is a well known issue, the jmicron controller isn't recognized by Kernels older than 2.6.18
There is some information over the net ( [gentoo-wiki]("http://gentoo-wiki.com/ASUS_P5B_Deluxe") ) and also in this forum exists [long thread]("http://www.ubuntuforums.org/showthread.php?t=234706&highlight=p5b")
I finally installed Feisty Fawn, now with 2.6.20 Kernel, and its pretty stable.
You can also try the boot option "all-generic-ide"

---

