---
title: "no ethernet or wireless Ubuntu on Acer Aspire 5610"
date: 2015-06-27
forum: General Help
---

### Post by jj4 on 2015-06-27
I have a ethernet cable plugged in but there's no internet.
How can I install the drivers? I have no ethernet connection on the software so cannot run apt-get install commands

```
j@j-Aspire-5610:~$ lspci -vnn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
    Subsystem: Acer Incorporated [ALI] Device [1025:0090]
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03) (prog-if 00 [VGA controller])
    Subsystem: Acer Incorporated [ALI] Device [1025:0090]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d0200000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 5088 [size=8]
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    Memory at d0300000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: intelfb, i915

00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
    Subsystem: Acer Incorporated [ALI] Device [1025:0090]
    Flags: bus master, fast devsel, latency 0
    Memory at d0280000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1b.0 Audio device [0403]: Intel Corporation NM10/ICH7 Family High Definition Audio Controller [8086:27d8] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0090]
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at d0340000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 1 [8086:27d0] (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: d0600000-d07fffff
    Prefetchable memory behind bridge: 00000000d0800000-00000000d09fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 2 [8086:27d2] (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: d0a00000-d0bfffff
    Prefetchable memory behind bridge: 00000000d0c00000-00000000d0dfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 3 [8086:27d4] (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: d0e00000-d0ffffff
    Prefetchable memory behind bridge: 00000000d1000000-00000000d11fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 4 [8086:27d6] (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 00006000-00006fff
    Memory behind bridge: d0000000-d00fffff
    Prefetchable memory behind bridge: 00000000d1200000-00000000d13fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device [1025:0090]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 50a0 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 [8086:27c9] (rev 02) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device [1025:0090]
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 50c0 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 [8086:27ca] (rev 02) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device [1025:0090]
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 50e0 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 [8086:27cb] (rev 02) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device [1025:0090]
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 5400 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller [8086:27cc] (rev 02) (prog-if 20 [EHCI])
    Subsystem: Acer Incorporated [ALI] Device [1025:0090]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at d0544000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=0a, sec-latency=32
    I/O behind bridge: 00007000-00007fff
    Memory behind bridge: d0100000-d01fffff
    Prefetchable memory behind bridge: 00000000d4000000-00000000d7ffffff
    Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0090]
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: lpc_ich
    Kernel modules: leds-ss4200, lpc_ich, intel-rng

00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] [8086:27c4] (rev 02) (prog-if 80 [Master])
    Subsystem: Acer Incorporated [ALI] Device [1025:0090]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 5440 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus [0c05]: Intel Corporation NM10/ICH7 Family SMBus Controller [8086:27da] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0090]
    Flags: medium devsel, IRQ 10
    I/O ports at 5420 [size=32]
    Kernel modules: i2c-i801

05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: AMBIT Microsystem Corp. Device [1468:0422]
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at d0000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl
    Kernel modules: wl, ssb

06:01.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0090]
    Flags: fast devsel, IRQ 10
    Memory at d0100000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel modules: b44

06:04.0 CardBus bridge [0607]: ENE Technology Inc CB-712/4 Cardbus Controller [1524:1412] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0090]
    Flags: bus master, medium devsel, latency 168, IRQ 16
    Memory at d8000000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=06, secondary=07, subordinate=0a, sec-latency=176
    Memory window 0: d4000000-d7fff000 (prefetchable)
    Memory window 1: dc000000-dffff000
    I/O window 0: 00007000-000070ff
    I/O window 1: 00007400-000074ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

06:04.1 FLASH memory [0501]: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller [1524:0530] (rev 01)
    Subsystem: Acer Incorporated [ALI] Device [1025:0090]
    Flags: medium devsel, IRQ 11
    Memory at d0103000 (32-bit, non-prefetchable) [disabled] [size=128]
    Capabilities: <access denied>

06:04.2 SD Host controller [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller [1524:0550] (rev 01) (prog-if 01)
    Subsystem: Acer Incorporated [ALI] Device [1025:0090]
    Flags: medium devsel, IRQ 17
    Memory at d0103400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

06:04.3 FLASH memory [0501]: ENE Technology Inc FLASH memory: ENE Technology Inc: [1524:0520] (rev 01)
    Subsystem: Acer Incorporated [ALI] Device [1025:0090]
    Flags: medium devsel, IRQ 11
    Memory at d0103800 (32-bit, non-prefetchable) [disabled] [size=128]
    Capabilities: <access denied>

06:04.4 FLASH memory [0501]: ENE Technology Inc SD/MMC Card Reader Controller [1524:0551] (rev 01)
    Subsystem: Acer Incorporated [ALI] Device [1025:0090]
    Flags: medium devsel, IRQ 17
    Memory at d0102000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci


```

---

### Post by wildmanne39 on 2015-06-27
Please do:
```
sudo apt-get purge bcmwl-kernel-source
```
reboot and your ethernet should be working, then do:
```
sudo apt-get install firmware-b43-installer
```
Reboot and wireless should work.
Thanks

---

### Post by jj4 on 2015-06-27
Thanks. There is no sound either? Do I have to install drivers for that and how?

---

### Post by wildmanne39 on 2015-06-27
> **jj4 said:**
> Thanks. There is no sound either? Do I have to install drivers for that and how?
Probably not, you can check to make sure the sound is not muted because a lot of times it is when ubuntu is installed, if that is not the case please start a new thread for that issue.
Thanks

---

