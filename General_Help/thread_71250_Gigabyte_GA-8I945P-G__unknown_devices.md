---
title: "Gigabyte GA-8I945P-G / unknown devices"
date: 2005-10-02
forum: General Help
---

### Post by feicht on 2005-10-02
hi @ll,

i joined the ubuntu-community just a few days ago and i'm already battling it ( very badly ) ;-)

no, look :

feicht@fubuntu:~$ lspci
0000:00:00.0 Host bridge: Intel Corp.: Unknown device 2770 (rev 81)
0000:00:01.0 PCI bridge: Intel Corp.: Unknown device 2771 (rev 81)
0000:00:1b.0 0403: Intel Corp.: Unknown device 27d8 (rev 01)
0000:00:1c.0 PCI bridge: Intel Corp.: Unknown device 27d0 (rev 01)
0000:00:1c.2 PCI bridge: Intel Corp.: Unknown device 27d4 (rev 01)
0000:00:1d.0 USB Controller: Intel Corp.: Unknown device 27c8 (rev 01)
0000:00:1d.1 USB Controller: Intel Corp.: Unknown device 27c9 (rev 01)
0000:00:1d.2 USB Controller: Intel Corp.: Unknown device 27ca (rev 01)
0000:00:1d.3 USB Controller: Intel Corp.: Unknown device 27cb (rev 01)
0000:00:1d.7 USB Controller: Intel Corp.: Unknown device 27cc (rev 01)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corp.: Unknown device 27b8 (rev 01)
0000:00:1f.2 IDE interface: Intel Corp.: Unknown device 27c0 (rev 01)
0000:00:1f.3 SMBus: Intel Corp.: Unknown device 27da (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 554b
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 556b
0000:03:00.0 Ethernet controller: Broadcom Corporation: Unknown device 169d (rev 11)


the system doesn't recognize anything. as you can see all intel-devices are marked as "unknown" / most important is my missing onboard-sound-device. except the display-controller is fine ( 2 dvi-connectors with 2 screens ).


does anyone have an idea what's wrong ?

thx,
gerald

---

