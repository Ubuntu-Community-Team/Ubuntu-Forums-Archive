---
title: "XGL works perfectly with my Intel 945GM (i810 driver) but AIGX does not."
date: 2006-08-15
forum: General Help
---

### Post by Rinnan on 2006-08-15
The purpose of this post is such that it pops up during searches for those trying to get AIGLX or XGL to work on their i810 systems. 

There are *many* posts out there which say or imply that GLX does not work well on the Intel video chipsets, but that AIGLX does.  

In my specific case, with my specific hardware, I've had the opposite experience.  If you have an i810-driven chipset, this might also be true for you.  Don't give up with AIGLX doesn't work well.

Just the standard installation instructions for GLX worked fine.

lspci
```
0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
0000:02:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)
0000:0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:0a:09.0 CardBus bridge: Texas Instruments: Unknown device 8039
0000:0a:09.2 Mass storage controller: Texas Instruments: Unknown device 803b
0000:0a:09.3 0805: Texas Instruments: Unknown device 803c
```

---

### Post by reacocard on 2006-08-15
I had the exact opposite of what you had. AIGLX worked perfectly, but XGL not at all. i have intel i915 graphics, also i810 driver.

---

### Post by Rinnan on 2006-08-16
Yes, your case (where AIGLX works but XGL does not) seems the most common.  I encourage Intel owners to try both, perhaps we can compile our exact chipsets and report which one worked with what.

My card is reported as a "945GM" chipset by 915resolution -l.

How about yours?

---

### Post by reacocard on 2006-08-16
915GM chipset.

---

### Post by n0yd on 2006-08-19
I have the 945GM, I tried a bunch of different tweaks and quirks to get AIGLX to run, no go ](*,)   XGL works though :)

---

### Post by miseryshining on 2006-08-25
aiglx worked without any problems on my 945GM after following the tutorial found on these forums.

LSPCI:

```

0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
0000:03:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)
0000:0a:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705_2 Gigabit Ethernet (rev 03)
0000:0a:09.0 CardBus bridge: Texas Instruments: Unknown device 8039
0000:0a:09.1 FireWire (IEEE 1394): Texas Instruments: Unknown device 803a
0000:0a:09.2 Mass storage controller: Texas Instruments: Unknown device 803b

```

---

