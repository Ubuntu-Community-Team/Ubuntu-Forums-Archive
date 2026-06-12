---
title: "No Audio"
date: 2007-09-09
forum: General Help
---

### Post by galtsgomjabbar on 2007-09-09
I have no audio at all 
i have tried the newest alsa mixer

here is the result of "lspci -v"

00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
        Subsystem: ABIT Computer Corp. Unknown device 1c0e
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
        Subsystem: ABIT Computer Corp. Unknown device 1c0e
        Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
        Subsystem: ABIT Computer Corp. Unknown device 1c0e
        Flags: 66MHz, fast devsel, IRQ 5
        I/O ports at fc00 [size=32]
        I/O ports at 1c00 [size=64]
        I/O ports at 1c40 [size=64]
        Capabilities: <access denied>

00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (prog-if 10 [OHCI])
        Subsystem: ABIT Computer Corp. Unknown device 1c0e
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
        Memory at febff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3) (prog-if 20 [EHCI])
        Subsystem: ABIT Computer Corp. Unknown device 1c0e
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at febfe000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
        Subsystem: ABIT Computer Corp. Unknown device 1c0e
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        I/O ports at f000 [size=256]
        I/O ports at ec00 [size=256]
        Memory at febfd000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2) (prog-if 8a [Master SecP PriP])
        Subsystem: ABIT Computer Corp. Unknown device 1c0e
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at e000 [size=16]
        Capabilities: <access denied>

00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
        Subsystem: ABIT Computer Corp. Unknown device 1c0e
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        I/O ports at 09f0 [size=8]
        I/O ports at 0bf0 [size=4]
        I/O ports at 0970 [size=8]
        I/O ports at 0b70 [size=4]
        I/O ports at cc00 [size=16]
        Memory at febfb000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
        Subsystem: ABIT Computer Corp. Unknown device 1c0e
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        I/O ports at 09e0 [size=8]
        I/O ports at 0be0 [size=4]
        I/O ports at 0960 [size=8]
        I/O ports at 0b60 [size=4]
        I/O ports at b800 [size=16]
        Memory at febfa000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: fe900000-fe9fffff
        Prefetchable memory behind bridge: fea00000-feafffff

00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
        Subsystem: ABIT Computer Corp. Unknown device 1c0e
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
        Memory at febf9000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at b400 [size=8]
        Capabilities: <access denied>

00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: fe800000-fe8fffff
        Prefetchable memory behind bridge: 00000000fe700000-00000000fe7fffff
        Capabilities: <access denied>

00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 00008000-00008fff
        Memory behind bridge: fe600000-fe6fffff
        Prefetchable memory behind bridge: 00000000fe500000-00000000fe5fffff
        Capabilities: <access denied>

00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 00007000-00007fff
        Memory behind bridge: fe400000-fe4fffff
        Prefetchable memory behind bridge: 00000000fe300000-00000000fe3fffff
        Capabilities: <access denied>

00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        I/O behind bridge: 00006000-00006fff
        Memory behind bridge: fe200000-fe2fffff
        Prefetchable memory behind bridge: 00000000b0000000-00000000cfffffff
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

01:08.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
        Subsystem: C-Media Electronics Inc CMI8738/C3DX PCI Audio Device
        Flags: bus master, stepping, medium devsel, latency 32, IRQ 20
        I/O ports at ac00 [size=256]
        Capabilities: <access denied>

05:00.0 VGA compatible controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)] (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc. Unknown device 0058
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at b0000000 (64-bit, prefetchable) [size=256M]
        Memory at fe200000 (64-bit, non-prefetchable) [size=64K]
        I/O ports at 6c00 [size=256]
        [virtual] Expansion ROM at c0000000 [disabled] [size=128K]
        Capabilities: <access denied>

05:00.1 Display controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)] Secondary
        Subsystem: ASUSTeK Computer Inc. Unknown device 0059
        Flags: fast devsel
        Memory at fe210000 (64-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <access denied>

---

### Post by linuxwizard on 2007-09-09
look through these see if anything will help
[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)


Also if you have installed the latest updates for Feisty you might want to look at Launchpad and see if a bug has been reported on your issue/sound card

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20)

---

### Post by galtsgomjabbar on 2007-09-11
unfortunalty, that didn't work, 
I've noticed though that my sound works if I boot up into XP and then restart my system into ubuntu

---

