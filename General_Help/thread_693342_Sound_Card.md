---
title: "Sound Card?"
date: 2008-02-10
forum: General Help
---

### Post by u4m on 2008-02-10
Can anyone please tell me which is my sound card?:
I am using the instructions on sound trouble shooting here > [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) and in looking for my sound card I am stopped here >
blablabla-desktop:~$ lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev 44)
        Subsystem: Giga-byte Technology VT82C691 Apollo Pro System Controller
        Flags: bus master, medium devsel, latency 16
        Memory at d8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP] (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: dc000000-ddffffff
        Prefetchable memory behind bridge: de000000-dfffffff
        Capabilities: <access denied>

00:07.0 ISA bridge: VIA Technologies, Inc. VT82C596 ISA [Mobile South] (rev 23)
        Subsystem: Giga-byte Technology VT82C596/A/B PCI to ISA Bridge
        Flags: bus master, stepping, medium devsel, latency 0

00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10) (prog-if 8a [Master SecP PriP])
        Flags: bus master, medium devsel, latency 64
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
        I/O ports at e000 [size=16]
        Capabilities: <access denied>

00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 11) (prog-if 00 [UHCI])
        Subsystem: First International Computer, Inc. VA-502 Mainboard
        Flags: bus master, medium devsel, latency 64, IRQ 10
        I/O ports at e400 [size=32]
        Capabilities: <access denied>

00:07.3 Host bridge: VIA Technologies, Inc. VT82C596 Power Management (rev 30)
        Flags: medium devsel

00:0a.0 Ethernet controller: VIA Technologies, Inc. VT86C100A [Rhine] (rev 06)
        Subsystem: D-Link System Inc DFE-530TX rev A
        Flags: bus master, medium devsel, latency 64, IRQ 12
        I/O ports at e800 [size=128]
        Memory at e1000000 (32-bit, non-prefetchable) [size=128]
        Expansion ROM at e0000000 [disabled] [size=64K]

01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15) (prog-if 00 [VGA])
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
        Memory at dc000000 (32-bit, non-prefetchable) [size=16M]
        Memory at de000000 (32-bit, prefetchable) [size=32M]
        [virtual] Expansion ROM at dd000000 [disabled] [size=64K]
        Capabilities: <access denied>

---

### Post by Fernanernie on 2008-02-11
I may be blind, but I don't see one listed there

---

