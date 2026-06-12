---
title: "Any one there to help me... Whole system locks up Ubuntu 7.10"
date: 2008-06-16
forum: General Help
---

### Post by MATHEWJOHN on 2008-06-16
I am New to Ubuntu..I tried 7.04, 7.10 & 8.04 in my system but all these giving me some difficulties... My system locks up completely with out giving any warning. I have to press the reset button to restart the system... since I am new to linux plse give me advice is this happens because of lacking proper installation or any other???????

************************************************


heby@Thekkadathu:~$ lspci -v
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
        Subsystem: Intel Corporation Unknown device d600
        Flags: bus master, 66MHz, medium devsel, latency 64
        Memory at <ignored> (64-bit, non-prefetchable)

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 99
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fde00000-fdefffff
        Prefetchable memory behind bridge: d0000000-dfffffff
        Capabilities: <access denied>

00:11.0 IDE interface: ATI Technologies Inc 437A Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Intel Corporation Unknown device d600
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        I/O ports at ff00 [size=8]
        I/O ports at fe00 [size=4]
        I/O ports at fd00 [size=8]
        I/O ports at fc00 [size=4]
        I/O ports at fb00 [size=16]
        Memory at fe02f000 (32-bit, non-prefetchable) [size=512]
        Expansion ROM at fdf80000 [disabled] [size=512K]
        Capabilities: <access denied>

00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Intel Corporation Unknown device d600
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
        I/O ports at fa00 [size=8]
        I/O ports at f900 [size=4]
        I/O ports at f800 [size=8]
        I/O ports at f700 [size=4]
        I/O ports at f600 [size=16]
        Memory at fe02e000 (32-bit, non-prefetchable) [size=512]
        Expansion ROM at 30000000 [disabled] [size=512K]
        Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Intel Corporation Unknown device d600
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Intel Corporation Unknown device d600
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
        Subsystem: Intel Corporation Unknown device d600
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
        Subsystem: Intel Corporation Unknown device d600
        Flags: 66MHz, medium devsel
        I/O ports at 0b00 [size=16]
        Memory at fe02a000 (32-bit, non-prefetchable) [size=1K]

00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80) (prog-if 8a [Master SecP PriP])
        Subsystem: Intel Corporation Unknown device d600
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at f400 [size=16]
        Capabilities: <access denied>

00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
        Subsystem: Intel Corporation Unknown device d600
        Flags: bus master, slow devsel, latency 64, IRQ 16
        Memory at fe024000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
        Subsystem: Intel Corporation Unknown device d600
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
        Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fdd00000-fddfffff
        Prefetchable memory behind bridge: fdc00000-fdcfffff

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200] (prog-if 00 [VGA])
        Subsystem: Intel Corporation Unknown device d600
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at ee00 [size=256]
        Memory at fdef0000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at fde00000 [disabled] [size=128K]
        Capabilities: <access denied>

02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Intel Corporation Unknown device d600
        Flags: bus master, medium devsel, latency 64, IRQ 20
        I/O ports at de00 [size=256]
        Memory at fddff000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

---

### Post by cmnorton on 2008-06-16
Is this a laptop or desktop/workstation?

When does the system lock up?

---

### Post by MATHEWJOHN on 2008-06-17
Desktop one... This happens on surfing... I installed opera instead of FF but no us... If I use more graphics based activities systems lock happens

---

