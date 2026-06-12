---
title: "Im new and have no sound"
date: 2008-04-03
forum: General Help
---

### Post by joecagle77 on 2008-04-03
I've been looking at lot of threads seeing if any other sound post can help but I've found none. 

Here is my info, can anyone tell me why my sound wont work. When I first did my install there where a few bleeps but after that nothing. When I try and open my sound controller it tries to open but just goes away. 

joe@j-pc:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:06.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
00:07.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 08)
00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)
joe@j-pc:~$ asoundconf list
Names of available sound cards:
V8237
AudioPCI
joe@j-pc:~$

---

### Post by joecagle77 on 2008-04-04
umm, please..

or should I take the hint that no one knows.

---

### Post by zvacet on 2008-04-04
Try with [this.](http://ubuntuforums.org/showthread.php?t=744497)That will just check and enable your sound.To play audio type in terminal

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by newhappyxuser on 2008-04-04
> **joecagle77 said:**
> umm, please..

or should I take the hint that no one knows.

What distribution you are using ?

---

### Post by joecagle77 on 2008-04-04
Some how I fixed it. But thanks to all.

---

### Post by joecagle77 on 2008-04-04
Well, I thought I had this fixed. I restarted and then no sound again. 
What info do I need to output to help someone assist me?

---

### Post by joecagle77 on 2008-04-04
Im running Ubuntu 7.10

I thought I had it fixed but after restarting no sound

Here is my aplay -1 output

**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
Subdevices: 4/4
Subdevice #0: subdevice #0
Subdevice #1: subdevice #1
Subdevice #2: subdevice #2
Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
Subdevices: 1/1
Subdevice #0: subdevice #0


and here is my lspci -v output

joe@j-pc:~$ lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
Subsystem: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
Flags: bus master, 66MHz, medium devsel, latency 8
Memory at e0000000 (32-bit, prefetchable) [size=128M]
Capabilities: <access denied>

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal decode])
Flags: bus master, 66MHz, medium devsel, latency 0
Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
Memory behind bridge: ec000000-edffffff
Prefetchable memory behind bridge: e8000000-ebffffff
Capabilities: <access denied>

00:06.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
Subsystem: Netgear Unknown device 5e00
Flags: bus master, medium devsel, latency 168, IRQ 18
Memory at ee000000 (32-bit, non-prefetchable) [size=64K]
Capabilities: <access denied>

00:07.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 0
Subsystem: Ensoniq Creative Sound Blaster AudioPCI64V, AudioPCI128
Flags: bus master, slow devsel, latency 32, IRQ 20
I/O ports at e000 [size=64]
Capabilities: <access denied>

00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
Subsystem: VIA Technologies, Inc. VT82C586/B/VT82C686/A/B/VT8233/A/C/VT8235 PIPC Bus Master IDE
Flags: bus master, medium devsel, latency 32, IRQ 16
[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
I/O ports at e100 [size=16]
Capabilities: <access denied>

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
Flags: bus master, medium devsel, latency 32, IRQ 17
I/O ports at e200 [size=32]
Capabilities: <access denied>

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
Flags: bus master, medium devsel, latency 32, IRQ 17
I/O ports at e300 [size=32]
Capabilities: <access denied>

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
Flags: bus master, medium devsel, latency 32, IRQ 17
I/O ports at e400 [size=32]
Capabilities: <access denied>

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
Flags: bus master, medium devsel, latency 32, IRQ 17
I/O ports at e500 [size=32]
Capabilities: <access denied>

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
Subsystem: VIA Technologies, Inc. USB 2.0
Flags: bus master, medium devsel, latency 32, IRQ 17
Memory at ee010000 (32-bit, non-prefetchable) [size=256]
Capabilities: <access denied>

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
Subsystem: VIA Technologies, Inc. DFI KT600-AL / Soltek SL-B9D-FGR Motherboard
Flags: bus master, stepping, medium devsel, latency 0
Capabilities: <access denied>

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
Subsystem: Micro-Star International Co., Ltd. Unknown device 7061
Flags: medium devsel, IRQ 19
I/O ports at e600 [size=256]
Capabilities: <access denied>

01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01) (prog-if 00 [VGA])
Subsystem: Micro-Star International Co., Ltd. MS-7061
Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 21
Memory at e8000000 (32-bit, prefetchable) [size=64M]
Memory at ec000000 (32-bit, non-prefetchable) [size=16M]
[virtual] Expansion ROM at ed000000 [disabled] [size=64K]
Capabilities: <access denied>
__________________

---

