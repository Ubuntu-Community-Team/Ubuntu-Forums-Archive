---
title: "saucy - mei kernel module  issue (3.9.0-2-generic)"
date: 2013-05-26
forum: General Help
---

### Post by FrUser on 2013-05-26
Hello,

I 've a problem with mei , I'm getting a lot of ```
 mei 0000:00:03.0: unexpected reset: dev_state = RESETING
``` in my dmesg.

  The laptop is running saucy (xubuntu 13.10) with 3.9.0-2-generic kernel, and here is my lspci ( after "modprobe -r mei" ;) )
```

lspci -kv
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
    Subsystem: Micro-Star International Co., Ltd. Device 401b
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03) (prog-if 00 [VGA controller])
    Subsystem: Micro-Star International Co., Ltd. Device 401b
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at feb00000 (64-bit, non-prefetchable) [size=1M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at ec00 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 03)
    Subsystem: Micro-Star International Co., Ltd. Device 401b
    Flags: bus master, fast devsel, latency 0
    Memory at fe900000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

00:03.0 Communication controller: Intel Corporation Mobile PM965/GM965 [COLOR=#ff0000]MEI [/COLOR]Controller (rev 03)
    Subsystem: Micro-Star International Co., Ltd. Device 401b
    Flags: fast devsel, IRQ 16
    Memory at feafe800 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>

00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
    Subsystem: Micro-Star International Co., Ltd. Device 401b
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at feac0000 (32-bit, non-prefetchable) [size=128K]
    Memory at feafd000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at d080 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: e1000e

00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 401b
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at d480 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 401b
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at d400 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 401b
    Flags: bus master, medium devsel, latency 0, IRQ 18
    Memory at feafec00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
    Subsystem: Micro-Star International Co., Ltd. Device 401b
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at feaf8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: fe600000-fe6fffff
    Prefetchable memory behind bridge: 000000007d800000-000000007d9fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: 7da00000-7dbfffff
    Prefetchable memory behind bridge: 000000007dc00000-000000007ddfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 401b
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at dc00 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 401b
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at d880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 401b
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at d800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 401b
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at feaff000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=02, sec-latency=32
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fdd00000-fe5fffff
    Prefetchable memory behind bridge: 00000000bdf00000-00000000bfefffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M-E) LPC Interface Controller (rev 03)
    Subsystem: Micro-Star International Co., Ltd. Device 401b
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: lpc_ich

00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
    Subsystem: Micro-Star International Co., Ltd. Device 401b
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at ffa0 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03) (prog-if 01 [AHCI 1.0])
    Subsystem: Micro-Star International Co., Ltd. Device 401b
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 43
    I/O ports at e880 [size=8]
    I/O ports at e800 [size=4]
    I/O ports at e480 [size=8]
    I/O ports at e400 [size=4]
    I/O ports at e080 [size=32]
    Memory at feaff800 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
    Subsystem: Micro-Star International Co., Ltd. Device 401b
    Flags: medium devsel, IRQ 10
    Memory at feaff400 (32-bit, non-prefetchable) [size=256]
    I/O ports at 0400 [size=32]

01:04.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
    Subsystem: Micro-Star International Co., Ltd. Device 401b
    Flags: bus master, medium devsel, latency 168, IRQ 16
    Memory at 80000000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=01, secondary=02, subordinate=02, sec-latency=176
    Memory window 0: 84000000-87ffffff (prefetchable)
    Memory window 1: 88000000-8bffffff
    I/O window 0: 0000c000-0000c0ff
    I/O window 1: 0000c400-0000c4ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus

01:04.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04) (prog-if 10 [OHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 401b
    Flags: bus master, medium devsel, latency 64, IRQ 17
    Memory at fe5ff800 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci

01:04.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
    Subsystem: Micro-Star International Co., Ltd. Device 401b
    Flags: bus master, medium devsel, latency 64, IRQ 18
    Memory at fe5ff400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci

01:04.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
    Subsystem: Micro-Star International Co., Ltd. Device 401b
    Flags: bus master, medium devsel, latency 64, IRQ 18
    Memory at fe5ff000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: r592

01:04.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)
    Subsystem: Micro-Star International Co., Ltd. Device 401b
    Flags: bus master, medium devsel, latency 64, IRQ 18
    Memory at fe5fec00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: r852

03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
    Subsystem: Intel Corporation Device 1001
    Flags: bus master, fast devsel, latency 0, IRQ 47
    Memory at fe6fe000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwl4965

```

I currently use "modprobe -r mei" to fix the ptoblem, but it is not a nice solution ;)
thx

---

