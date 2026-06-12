---
title: "ubuntu 16.04 mini mimimal install of XFCE4 sound issue"
date: 2018-01-29
forum: General Help
---

### Post by Chris1965 on 2018-01-29
I am using a Dell M6800 i7 workstation laptop and all is going fine with besides for one nagging problem. Every time the computer boots it makes a very disturbing loud crackling noise. I've read a crap load of other reports of so called fixes but none of them actually work. The OS installed is a minimal XFCE4 install of 16.04 x64.

 lspci -v showed:

00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
    Subsystem: Dell Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: ie31200_edac

00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 26
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: f4000000-f50fffff
    Prefetchable memory behind bridge: 00000000e0000000-00000000f1ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06) (prog-if 00 [VGA controller])
    DeviceName:  Onboard IGD
    Subsystem: Dell 4th Gen Core Processor Integrated Graphics Controller
    Flags: bus master, fast devsel, latency 0, IRQ 30
    Memory at f5400000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

[B]00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
    Subsystem: Dell Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
    Flags: bus master, fast devsel, latency 0, IRQ 33
    Memory at f7a34000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel[/B]

00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 04) (prog-if 30 [XHCI])
    Subsystem: Dell 8 Series/C220 Series Chipset Family USB xHCI
    Flags: bus master, medium devsel, latency 0, IRQ 27
    Memory at f7a20000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: Dell 8 Series/C220 Series Chipset Family MEI Controller
    Flags: bus master, fast devsel, latency 0, IRQ 31
    Memory at f7a40000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: mei_me
    Kernel modules: mei_me

00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I217-LM (rev 04)
    DeviceName:  Onboard LAN
    Subsystem: Dell Ethernet Connection I217-LM
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Memory at f7a00000 (32-bit, non-prefetchable) [size=128K]
    Memory at f7a3d000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at f080 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: e1000e
    Kernel modules: e1000e

00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Dell 8 Series/C220 Series Chipset Family USB EHCI
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f7a3c000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

[B]00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 04)
    Subsystem: Dell 8 Series/C220 Series Chipset High Definition Audio Controller
    Flags: bus master, fast devsel, latency 0, IRQ 32
    Memory at f7a30000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel[/B]

00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: f5800000-f5afffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Bus: primary=00, secondary=04, subordinate=07, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: f6f00000-f78fffff
    Prefetchable memory behind bridge: 00000000f3500000-00000000f3efffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5 (rev d4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: f6500000-f6efffff
    Prefetchable memory behind bridge: 00000000f2b00000-00000000f34fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.6 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #7 (rev d4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Bus: primary=00, secondary=09, subordinate=10, sec-latency=0
    I/O behind bridge: 0000a000-0000bfff
    Memory behind bridge: f5b00000-f64fffff
    Prefetchable memory behind bridge: 00000000f2100000-00000000f2afffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.7 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #8 (rev d4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Bus: primary=00, secondary=11, subordinate=11, sec-latency=0
    Memory behind bridge: f7900000-f79fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Dell 8 Series/C220 Series Chipset Family USB EHCI
    Flags: bus master, medium devsel, latency 0, IRQ 21
    Memory at f7a3b000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1f.0 ISA bridge: Intel Corporation QM87 Express LPC Controller (rev 04)
    Subsystem: Dell QM87 Express LPC Controller
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich

00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
    Subsystem: Dell 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 29
    I/O ports at f0d0 [size=8]
    I/O ports at f0c0 [size=4]
    I/O ports at f0b0 [size=8]
    I/O ports at f0a0 [size=4]
    I/O ports at f060 [size=32]
    Memory at f7a3a000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 04)
    Subsystem: Dell 8 Series/C220 Series Chipset Family SMBus Controller
    Flags: medium devsel, IRQ 10
    Memory at f7a39000 (64-bit, non-prefetchable) [size=256]
    I/O ports at f040 [size=32]
    Kernel modules: i2c_i801

01:00.0 VGA compatible controller: NVIDIA Corporation GK104GLM [Quadro K3100M] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Dell GK104GLM [Quadro K3100M]
    Flags: bus master, fast devsel, latency 0, IRQ 34
    Memory at f4000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    [virtual] Expansion ROM at f5000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_384_drm, nvidia_384

03:00.0 Network controller: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter (rev 03)
    Subsystem: Dell BCM4352 802.11ac Wireless Network Adapter
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at f5a00000 (64-bit, non-prefetchable) [size=32K]
    Memory at f5800000 (64-bit, non-prefetchable) [size=2M]
    Capabilities: <access denied>
    Kernel driver in use: wl
    Kernel modules: bcma, wl

11:00.0 SD Host controller: O2 Micro, Inc. SD/MMC Card Reader Controller (rev 01) (prog-if 01)
    Subsystem: Dell SD/MMC Card Reader Controller
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at f7901000 (32-bit, non-prefetchable) [size=4K]
    Memory at f7900000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci_pci

Any help with this issue would be greatly appreciated.

---

### Post by tinylagarto on 2018-01-30
I am not sure about the noise. I only know on my laptop I can hear a light plop sound when the system boots up and I suppose is recognizing my sound card.

---

