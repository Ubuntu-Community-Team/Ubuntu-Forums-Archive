---
title: "No Sound at Startup - Gutsy Gibbon"
date: 2008-01-19
forum: General Help
---

### Post by makepeace2000 on 2008-01-19
Greetings,

I am a new forum member, but have been using Ubuntu since Dapper Drake ( currently running Gutsy Gibbon).  I have an intermittent problem that I cannot seem to resolve. My sound (from boot) will work (or not) completely intermittently. If no sound at start up , then a reboot is usually all that's required. The sound card is known to be good, as I am dual-booting with XP and card works fine on that side. If I restart Linux install I get sound back...no rhyme or reason.

The sound is available (or not) on about a 50/50 basis in Ubuntu, but 100% in XP...

I have read that there is a history of sound related issues in Linux in general and that 08.04 (Hardy Heron) is slated to fix some of them, but does anyone have any notion of what might be causing my issue?

I have seen a couple of commands ( aplay -l and  lspci -v  ) to run in terminal , but do not have the experience to interpret the output.

Thanks in Advance 

John

-No Sound 

john@k-ubuntu-desktop:~$ aplay -l 
**** List of PLAYBACK Hardware Devices **** 
card 0: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235] 
  Subdevices: 4/4 
  Subdevice #0: subdevice #0 
  Subdevice #1: subdevice #1 
  Subdevice #2: subdevice #2 
  Subdevice #3: subdevice #3 
card 0: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0 
card 1: CA0106 [CA0106], device 0: ca0106 [CA0106] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0 
card 1: CA0106 [CA0106], device 1: ca0106 [CA0106] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0 
card 1: CA0106 [CA0106], device 2: ca0106 [CA0106] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0 
card 1: CA0106 [CA0106], device 3: ca0106 [CA0106] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0 
john@k-ubuntu-desktop:~$ 

And  

john@k-ubuntu-desktop:~$ lspci -v 
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge 
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Unknown device 0240 
        Flags: bus master, 66MHz, medium devsel, latency 8 
        Memory at e0000000 (32-bit, prefetchable) [size=256M] 
        Capabilities: <access denied> 

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal decode]) 
        Flags: bus master, 66MHz, medium devsel, latency 0 
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0 
        Memory behind bridge: dbe00000-dfefffff 
        Prefetchable memory behind bridge: bbd00000-dbcfffff 
        Capabilities: <access denied> 

00:09.0 Multimedia audio controller: Creative Labs SB Audigy LS 
        Subsystem: Creative Labs Unknown device 100a 
        Flags: bus master, medium devsel, latency 32, IRQ 20 
        I/O ports at ec00 [size=32] 
        Capabilities: <access denied> 

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI]) 
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Unknown device 0240 
        Flags: bus master, medium devsel, latency 32, IRQ 16 
        I/O ports at e000 [size=32] 
        Capabilities: <access denied> 

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI]) 
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Unknown device 0240 
        Flags: bus master, medium devsel, latency 32, IRQ 16 
        I/O ports at e400 [size=32] 
        Capabilities: <access denied> 

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI]) 
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Unknown device 0240 
        Flags: bus master, medium devsel, latency 32, IRQ 16 
        I/O ports at e800 [size=32] 
        Capabilities: <access denied> 

00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82) (prog-if 20 [EHCI]) 
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Unknown device 0240 
        Flags: bus master, medium devsel, latency 32, IRQ 16 
        Memory at dfffff00 (32-bit, non-prefetchable) [size=256] 
        Capabilities: <access denied> 

00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge 
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Unknown device 0240 
        Flags: bus master, stepping, medium devsel, latency 0 
        Capabilities: <access denied> 

00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP]) 
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Unknown device 0240 
        Flags: bus master, medium devsel, latency 32, IRQ 255 
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8] 
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1] 
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8] 
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1] 
        I/O ports at fc00 [size=16] 
        Capabilities: <access denied> 

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50) 
        Subsystem: VIA Technologies, Inc. K7VT2 motherboard 
        Flags: medium devsel, IRQ 19 
        I/O ports at dc00 [size=256] 
        Capabilities: <access denied> 

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74) 
        Subsystem: VIA Technologies, Inc. VT6102 [Rhine II] Embeded Ethernet Controller on VT8235 
        Flags: bus master, medium devsel, latency 32, IRQ 17 
        I/O ports at d800 [size=256] 
        Memory at dffffe00 (32-bit, non-prefetchable) [size=256] 
        Capabilities: <access denied> 

01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1) (prog-if 00 [VGA]) 
        Subsystem: eVga.com. Corp. 256A8N341DX 
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 18 
        Memory at de000000 (32-bit, non-prefetchable) [size=16M] 
        Memory at c0000000 (32-bit, prefetchable) [size=256M] 
        Memory at dd000000 (32-bit, non-prefetchable) [size=16M] 
        [virtual] Expansion ROM at dfee0000 [disabled] [size=128K] 
        Capabilities: <access denied> 

john@k-ubuntu-desktop:~$ 
john@k-ubuntu-desktop:~$ aplay -l 
**** List of PLAYBACK Hardware Devices **** 
card 0: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235] 
  Subdevices: 4/4 
  Subdevice #0: subdevice #0 
  Subdevice #1: subdevice #1 
  Subdevice #2: subdevice #2 
  Subdevice #3: subdevice #3 
card 0: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0 
card 1: CA0106 [CA0106], device 0: ca0106 [CA0106] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0 
card 1: CA0106 [CA0106], device 1: ca0106 [CA0106] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0 
card 1: CA0106 [CA0106], device 2: ca0106 [CA0106] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0 
card 1: CA0106 [CA0106], device 3: ca0106 [CA0106] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0 





After restart with no changes -Sound working again-

john@k-ubuntu-desktop:~$ aplay -l 

**** List of PLAYBACK Hardware Devices ****

card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]

  Subdevices: 1/1

  Subdevice #0: subdevice #0

card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]

  Subdevices: 1/1

  Subdevice #0: subdevice #0

card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]

  Subdevices: 1/1

  Subdevice #0: subdevice #0

card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]

  Subdevices: 1/1

  Subdevice #0: subdevice #0

card 1: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]

  Subdevices: 4/4

  Subdevice #0: subdevice #0

  Subdevice #1: subdevice #1

  Subdevice #2: subdevice #2

  Subdevice #3: subdevice #3

card 1: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235]

  Subdevices: 1/1

  Subdevice #0: subdevice #0

john@k-ubuntu-desktop:~$ 



AND


john@k-ubuntu-desktop:~$ lspci -v 

00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge

        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Unknown device 0240

        Flags: bus master, 66MHz, medium devsel, latency 8

        Memory at e0000000 (32-bit, prefetchable) [size=256M]

        Capabilities: <access denied>



00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal decode])

        Flags: bus master, 66MHz, medium devsel, latency 0

        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0

        Memory behind bridge: dbe00000-dfefffff

        Prefetchable memory behind bridge: bbd00000-dbcfffff

        Capabilities: <access denied>



00:09.0 Multimedia audio controller: Creative Labs SB Audigy LS

        Subsystem: Creative Labs Unknown device 100a

        Flags: bus master, medium devsel, latency 32, IRQ 19

        I/O ports at ec00 [size=32]

        Capabilities: <access denied>



00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])

        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Unknown device 0240

        Flags: bus master, medium devsel, latency 32, IRQ 16

        I/O ports at e000 [size=32]

        Capabilities: <access denied>



00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])

        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Unknown device 0240

        Flags: bus master, medium devsel, latency 32, IRQ 16

        I/O ports at e400 [size=32]

        Capabilities: <access denied>



00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])

        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Unknown device 0240

        Flags: bus master, medium devsel, latency 32, IRQ 16

        I/O ports at e800 [size=32]

        Capabilities: <access denied>



00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82) (prog-if 20 [EHCI])

        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Unknown device 0240

        Flags: bus master, medium devsel, latency 32, IRQ 16

        Memory at dfffff00 (32-bit, non-prefetchable) [size=256]

        Capabilities: <access denied>



00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge

        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Unknown device 0240

        Flags: bus master, stepping, medium devsel, latency 0

        Capabilities: <access denied>



00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])

        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Unknown device 0240

        Flags: bus master, medium devsel, latency 32, IRQ 255

        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]

        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]

        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]

        [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]

        I/O ports at fc00 [size=16]

        Capabilities: <access denied>



00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)

        Subsystem: VIA Technologies, Inc. K7VT2 motherboard

        Flags: medium devsel, IRQ 20

        I/O ports at dc00 [size=256]

        Capabilities: <access denied>



00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)

        Subsystem: VIA Technologies, Inc. VT6102 [Rhine II] Embeded Ethernet Controller on VT8235

        Flags: bus master, medium devsel, latency 32, IRQ 17

        I/O ports at d800 [size=256]

        Memory at dffffe00 (32-bit, non-prefetchable) [size=256]

        Capabilities: <access denied>



01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1) (prog-if 00 [VGA])

        Subsystem: eVga.com. Corp. 256A8N341DX

        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 18

        Memory at de000000 (32-bit, non-prefetchable) [size=16M]

        Memory at c0000000 (32-bit, prefetchable) [size=256M]

        Memory at dd000000 (32-bit, non-prefetchable) [size=16M]

        [virtual] Expansion ROM at dfee0000 [disabled] [size=128K]

        Capabilities: <access denied>



john@k-ubuntu-desktop:~$

---

### Post by makepeace2000 on 2008-01-19
BTW- the only difference I note is that the soundcard got a different IRQ after the restart 20 instead of 19...

---

