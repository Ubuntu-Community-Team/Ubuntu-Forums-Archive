---
title: "ubuntu 15.04 not resuming after suspend"
date: 2015-09-12
forum: General Help
---

### Post by 123avi on 2015-09-12
I have a newly installed 15.04 on dell laptop. after suspend (using menu -> suspend) when I hit the power button (or any button) the computer is not waking up (I do see keyboard backlight and power button light), The only thing I am forced to do is force shutdown (long pres on the power button).
is there and fix for this issue ?

Please see below some info 
Thanks in advance for your help

> Manufacturer - Dell
Product name: xps 15 9530

avi@avi-XPS-15-9530:~$ uname -r
3.19.0-28-generic
avi@avi-XPS-15-9530:~$ lspci -vnn
00:00.0 Host bridge [0600]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller [8086:0c04] (rev 06)
    Subsystem: Dell Device [1028:05fe]
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>


00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller [8086:0c01] (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: f6000000-f70fffff
    Prefetchable memory behind bridge: 00000000e0000000-00000000f1ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport


00:02.0 VGA compatible controller [0300]: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller [8086:0416] (rev 06) (prog-if 00 [VGA controller])
    Subsystem: Dell Device [1028:05fe]
    Flags: bus master, fast devsel, latency 0, IRQ 34
    Memory at f7400000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915


00:03.0 Audio device [0403]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller [8086:0c0c] (rev 06)
    Subsystem: Intel Corporation Device [8086:2010]
    Flags: bus master, fast devsel, latency 0, IRQ 36
    Memory at f7c1c000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel


00:04.0 Signal processing controller [1180]: Intel Corporation Device [8086:0c03] (rev 06)
    Subsystem: Intel Corporation Device [8086:2010]
    Flags: fast devsel, IRQ 11
    Memory at f7c10000 (64-bit, non-prefetchable) [disabled] [size=32K]
    Capabilities: <access denied>


00:14.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI [8086:8c31] (rev 05) (prog-if 30 [XHCI])
    Subsystem: Dell Device [1028:05fe]
    Flags: bus master, medium devsel, latency 0, IRQ 30
    Memory at f7c00000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd


00:16.0 Communication controller [0780]: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 [8086:8c3a] (rev 04)
    Subsystem: Dell Device [1028:05fe]
    Flags: bus master, fast devsel, latency 0, IRQ 33
    Memory at f7c26000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: mei_me


00:1a.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 [8086:8c2d] (rev 05) (prog-if 20 [EHCI])
    Subsystem: Dell Device [1028:05fe]
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f7c24000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci


00:1b.0 Audio device [0403]: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller [8086:8c20] (rev 05)
    Subsystem: Dell Device [1028:05fe]
    Flags: bus master, fast devsel, latency 0, IRQ 35
    Memory at f7c18000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel


00:1c.0 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 [8086:8c10] (rev d5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: cf200000-cf3fffff
    Prefetchable memory behind bridge: 00000000cf400000-00000000cf5fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport


00:1c.2 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 [8086:8c14] (rev d5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    Memory behind bridge: f7800000-f7afffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport


00:1c.3 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 [8086:8c16] (rev d5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
    Memory behind bridge: f7b00000-f7bfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport


00:1d.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 [8086:8c26] (rev 05) (prog-if 20 [EHCI])
    Subsystem: Dell Device [1028:05fe]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f7c23000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci


00:1f.0 ISA bridge [0601]: Intel Corporation HM87 Express LPC Controller [8086:8c4b] (rev 05)
    Subsystem: Dell Device [1028:05fe]
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: lpc_ich


00:1f.2 SATA controller [0106]: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] [8086:8c03] (rev 05) (prog-if 01 [AHCI 1.0])
    Subsystem: Dell Device [1028:05fe]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 32
    I/O ports at f0b0 [size=8]
    I/O ports at f0a0 [size=4]
    I/O ports at f090 [size=8]
    I/O ports at f080 [size=4]
    I/O ports at f060 [size=32]
    Memory at f7c22000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci


00:1f.3 SMBus [0c05]: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller [8086:8c22] (rev 05)
    Subsystem: Dell Device [1028:05fe]
    Flags: medium devsel, IRQ 3
    Memory at f7c21000 (64-bit, non-prefetchable) [size=256]
    I/O ports at f040 [size=32]


00:1f.6 Signal processing controller [1180]: Intel Corporation 8 Series Chipset Family Thermal Management Controller [8086:8c24] (rev 05)
    Subsystem: Dell Device [1028:05fe]
    Flags: fast devsel, IRQ 3
    Memory at f7c20000 (64-bit, non-prefetchable) [disabled] [size=4K]
    Capabilities: <access denied>


02:00.0 3D controller [0302]: NVIDIA Corporation GK107M [GeForce GT 750M] [10de:0fe4] (rev a1)
    Subsystem: Dell Device [1028:05fe]
    Flags: bus master, fast devsel, latency 0, IRQ 37
    Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    Expansion ROM at f7000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nouveau


06:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
    Subsystem: Dell Device [1028:0019]
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at f7a00000 (64-bit, non-prefetchable) [size=32K]
    Memory at f7800000 (64-bit, non-prefetchable) [size=2M]
    Capabilities: <access denied>
    Kernel driver in use: wl


07:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5249 PCI Express Card Reader [10ec:5249] (rev 01)
    Subsystem: Dell Device [1028:05fe]
    Flags: bus master, fast devsel, latency 0, IRQ 31
    Memory at f7b00000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: rtsx_pci




---

### Post by Rob_Stevenson on 2016-03-02
I found this post from a Google search and would like to report that I am also suffering from this issue with a Dell XPS 15 9530. 

I am dual booting with Windows 10 which can go into and resume from suspend just fine, however Ubuntu Gnome 15.10 will not resume after a suspend. The power button light and keyboard back lights stay on and fans are going, but the machine will not resume and I have to hard shutdown by holding the power button as described above.

Any tips for how to resolve this problem or investigate it further would be appreciated.

---

### Post by abergo on 2016-04-17
> **Rob_Stevenson said:**
> I found this post from a Google search and would like to report that I am also suffering from this issue with a Dell XPS 15 9530. 

I am dual booting with Windows 10 which can go into and resume from suspend just fine, however Ubuntu Gnome 15.10 will not resume after a suspend. The power button light and keyboard back lights stay on and fans are going, but the machine will not resume and I have to hard shutdown by holding the power button as described above.

Any tips for how to resolve this problem or investigate it further would be appreciated.

I have the same. I found that the broadcom driver is creating issues. If you uninstall the driver the suspend / resume will work, but that is of course not acceptable. Did you figure out something?

---

