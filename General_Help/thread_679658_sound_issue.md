---
title: "sound issue"
date: 2008-01-27
forum: General Help
---

### Post by linuxnoob40 on 2008-01-27
recently installed 7.10 64 bit amd  sound blaster audigy  i have sound but can barely hear it . its got a high static content the actual sound is just a squeek behind the noise i cannot adjust any sound settings i dont have acces to it  


]00:00.0 Host bridge: ALi Corporation M1689 K8 Northbridge [Super K8 Single Chip]
        Subsystem: Giga-byte Technology Unknown device 5000
        Flags: bus master, fast devsel, latency 0
        Memory at <ignored> (32-bit, prefetchable)
        Capabilities: <access denied>

00:01.0 PCI bridge: ALi Corporation AGP8X Controller (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        Memory behind bridge: f8000000-faffffff
        Prefetchable memory behind bridge: e0000000-efffffff

00:02.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fb000000-fb0fffff

00:03.0 ISA bridge: ALi Corporation M1563 HyperTransport South Bridge (rev 70)
        Subsystem: Giga-byte Technology Unknown device 5001
        Flags: bus master, medium devsel, latency 32

00:03.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
        Subsystem: Giga-byte Technology Unknown device 5003
        Flags: medium devsel

00:0e.0 IDE interface: ALi Corporation M5229 IDE (rev c7) (prog-if fa)
        Subsystem: Giga-byte Technology Unknown device 5002
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at f000 [size=16]

00:0e.1 IDE interface: ALi Corporation ULi 5289 SATA (rev 10) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Giga-byte Technology Unknown device b003
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19
        I/O ports at d000 [size=8]
        I/O ports at d400 [size=4]
        I/O ports at d800 [size=8]
        I/O ports at dc00 [size=4]
        I/O ports at e000 [size=16]

00:0f.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 20
        Memory at fb100000 (32-bit, non-prefetchable) [size=4K]

00:0f.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 21
        Memory at fb101000 (32-bit, non-prefetchable) [size=4K]

00:0f.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 22
        Memory at fb102000 (32-bit, non-prefetchable) [size=4K]

00:0f.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, 66MHz, medium devsel, latency 48, IRQ 23
        Memory at fb103000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel

01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GS] (rev a2) (prog-if 00 [VGA])
        Subsystem: Unknown device 19f1:1fa4
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 16
        Memory at f8000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (32-bit, prefetchable) [size=256M]
        Memory at f9000000 (32-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at fa000000 [disabled] [size=128K]
        Capabilities: <access denied>

02:07.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
        Subsystem: D-Link System Inc DFE-530TX+ 10/100 Ethernet Adapter
        Flags: bus master, medium devsel, latency 64, IRQ 19
        I/O ports at c000 [size=256]
        Memory at fb005000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

02:09.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
        Subsystem: Creative Labs SB0090 Audigy Player
        Flags: bus master, medium devsel, latency 32, IRQ 21
        I/O ports at c400 [size=32]
        Capabilities: <access denied>

02:09.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
        Subsystem: Creative Labs SB Audigy MIDI/Game Port
        Flags: bus master, medium devsel, latency 32
        I/O ports at c800 [size=8]
        Capabilities: <access denied>

02:09.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (prog-if 10 [OHCI])
        Subsystem: Creative Labs SB Audigy FireWire Port
        Flags: bus master, medium devsel, latency 32, IRQ 22
        Memory at fb004000 (32-bit, non-prefetchable) [size=2K]
        Memory at fb000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

02:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Giga-byte Technology GA-7VM400M/7VT600 Motherboard
        Flags: bus master, medium devsel, latency 64, IRQ 18
        I/O ports at cc00 [size=256]
        Memory at fb006000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

steve@steve-desktop:~$ l-smod
bash: l-smod: command not found
steve@steve-desktop:~$ lspci -v
00:00.0 Host bridge: ALi Corporation M1689 K8 Northbridge [Super K8 Single Chip]
        Subsystem: Giga-byte Technology Unknown device 5000
        Flags: bus master, fast devsel, latency 0
        Memory at <ignored> (32-bit, prefetchable)
        Capabilities: <access denied>

00:01.0 PCI bridge: ALi Corporation AGP8X Controller (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        Memory behind bridge: f8000000-faffffff
        Prefetchable memory behind bridge: e0000000-efffffff

00:02.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fb000000-fb0fffff

00:03.0 ISA bridge: ALi Corporation M1563 HyperTransport South Bridge (rev 70)
        Subsystem: Giga-byte Technology Unknown device 5001
        Flags: bus master, medium devsel, latency 32

00:03.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
        Subsystem: Giga-byte Technology Unknown device 5003
        Flags: medium devsel

00:0e.0 IDE interface: ALi Corporation M5229 IDE (rev c7) (prog-if fa)
        Subsystem: Giga-byte Technology Unknown device 5002
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at f000 [size=16]

00:0e.1 IDE interface: ALi Corporation ULi 5289 SATA (rev 10) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Giga-byte Technology Unknown device b003
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19
        I/O ports at d000 [size=8]
        I/O ports at d400 [size=4]
        I/O ports at d800 [size=8]
        I/O ports at dc00 [size=4]
        I/O ports at e000 [size=16]

00:0f.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 20
        Memory at fb100000 (32-bit, non-prefetchable) [size=4K]

00:0f.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 21
        Memory at fb101000 (32-bit, non-prefetchable) [size=4K]

00:0f.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 22
        Memory at fb102000 (32-bit, non-prefetchable) [size=4K]

00:0f.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, 66MHz, medium devsel, latency 48, IRQ 23
        Memory at fb103000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel

01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GS] (rev a2) (prog-if 00 [VGA])
        Subsystem: Unknown device 19f1:1fa4
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 16
        Memory at f8000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (32-bit, prefetchable) [size=256M]
        Memory at f9000000 (32-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at fa000000 [disabled] [size=128K]
        Capabilities: <access denied>

02:07.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
        Subsystem: D-Link System Inc DFE-530TX+ 10/100 Ethernet Adapter
        Flags: bus master, medium devsel, latency 64, IRQ 19
        I/O ports at c000 [size=256]
        Memory at fb005000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

02:09.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
        Subsystem: Creative Labs SB0090 Audigy Player
        Flags: bus master, medium devsel, latency 32, IRQ 21
        I/O ports at c400 [size=32]
        Capabilities: <access denied>

02:09.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
        Subsystem: Creative Labs SB Audigy MIDI/Game Port
        Flags: bus master, medium devsel, latency 32
        I/O ports at c800 [size=8]
        Capabilities: <access denied>

02:09.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (prog-if 10 [OHCI])
        Subsystem: Creative Labs SB Audigy FireWire Port
        Flags: bus master, medium devsel, latency 32, IRQ 22
        Memory at fb004000 (32-bit, non-prefetchable) [size=2K]
        Memory at fb000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

02:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Giga-byte Technology GA-7VM400M/7VT600 Motherboard
        Flags: bus master, medium devsel, latency 64, IRQ 18
        I/O ports at cc00 [size=256]
        Memory at fb006000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>




dont know if that info helps anyone any other info i can give let me know

---

### Post by BuffaloX on 2008-01-27
Try swapping your soundcard to another slot,
Creative sucks at shared resources.
It is also recomended you get something else than Creative, because creative won't work with Linux at all, neither provide drivers, nor open up specifications to the community.

I reccomend something like Maudio, but others may be fine also.

PS
Maudio indisputably has better sound too.
Look for Maudio revolution 7.1 or 5.1
Maudio Audiophile 24/96
Or something similar.

---

### Post by linuxnoob40 on 2008-01-27
ill try swapping the slots but i have had ubuntu installed before and never had a issue with the sound card i have been using ubuntu since dapper drake on and off really dont know much more about it but as i said its never been a n issue in the past

---

### Post by linuxnoob40 on 2008-01-27
swapping to another slot has not done the trick im open to more suggestions

---

