---
title: "Another Sound problem"
date: 2007-05-01
forum: General Help
---

### Post by stinkypudding on 2007-05-01
I have a sound problem.    After I watched 24 last night on Myth, I fired up Amarok to listen to music, but there was no sound.    Now I'm not getting any sound at all.   I'm assuming there must be some sort of conflict between my HD5500 card and SiS SL7012 sound card, but I don't know how to fix it.    Can anyone help me get my sound back?

ryanr@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ryanr@ubuntu:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 761/M761 Host (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS966 [MuTIOL Media IO] (rev 59)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 190 Gigabit Ethernet Adapter (rev 01)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 02)
00:0f.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
00:0f.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
00:0f.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
00:0f.4 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)

ryanr@ubuntu:~$ lspci -v
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 761/M761 Host (rev 02)
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Unknown device 3047
        Flags: bus master, medium devsel, latency 0
        Memory at b0000000 (32-bit, non-prefetchable) [size=256M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: d4000000-dbffffff
        Prefetchable memory behind bridge: 00000000c8000000-00000000cfffffff
        Capabilities: <access denied>

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS966 [MuTIOL Media IO] (rev 59)
        Flags: bus master, medium devsel, latency 0

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01) (prog-if 80 [Master])
        Subsystem: Silicon Integrated Systems [SiS] SiS5513 EIDE Controller (A,B step)
        Flags: bus master, medium devsel, latency 128, IRQ 16
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 4000 [size=16]
        Capabilities: <access denied>

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Unknown device c5f1
        Flags: bus master, medium devsel, latency 52, IRQ 22
        I/O ports at f400 [size=256]
        I/O ports at fe00 [size=128]
        Capabilities: <access denied>

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Unknown device 3047
        Flags: bus master, medium devsel, latency 64, IRQ 18
        Memory at fbfff000 (32-bit, non-prefetchable) [size=4K]

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Unknown device 3047
        Flags: bus master, medium devsel, latency 64, IRQ 19
        Memory at fbffe000 (32-bit, non-prefetchable) [size=4K]

00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20 [EHCI])
        Subsystem: Silicon Integrated Systems [SiS] USB 2.0 Controller
        Flags: bus master, medium devsel, latency 64, IRQ 17
        Memory at fbffd000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 190 Gigabit Ethernet Adapter (rev 01)
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Unknown device 3047
        Flags: bus master, medium devsel, latency 0, IRQ 21
        Memory at fbffc000 (32-bit, non-prefetchable) [size=128]
        I/O ports at fd00 [size=128]
        Capabilities: <access denied>

00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 02) (prog-if 85 [Master SecO PriO])
        Subsystem: Silicon Integrated Systems [SiS] SATA Controller / IDE mode
        Flags: bus master, medium devsel, latency 64, IRQ 20
        I/O ports at fc00 [size=8]
        I/O ports at fb00 [size=4]
        I/O ports at fa00 [size=8]
        I/O ports at f900 [size=4]
        I/O ports at f800 [size=16]
        I/O ports at f700 [size=128]
        Capabilities: <access denied>

00:0f.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
        Subsystem: pcHDTV Unknown device 5500
        Flags: bus master, medium devsel, latency 20, IRQ 22
        Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <access denied>

00:0f.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
        Subsystem: pcHDTV Unknown device 5500
        Flags: bus master, medium devsel, latency 64, IRQ 22
        Memory at f9000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <access denied>

00:0f.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
        Subsystem: pcHDTV Unknown device 5500
        Flags: bus master, medium devsel, latency 64, IRQ 22
        Memory at f8000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <access denied>

00:0f.4 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
        Subsystem: pcHDTV Unknown device 5500
        Flags: bus master, medium devsel, latency 6, IRQ 9
        Memory at f7000000 (32-bit, non-prefetchable) [size=16M]
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
        Capabilities: <access denied>

01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2) (prog-if 00 [VGA])
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at d4000000 (32-bit, non-prefetchable) [size=64M]
        Memory at c8000000 (64-bit, prefetchable) [size=128M]
        Memory at da000000 (64-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at d8000000 [disabled] [size=128K]
        Capabilities: <access denied>

---

