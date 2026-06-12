---
title: "My sound doesn't work. I don't even know where to start."
date: 2006-11-07
forum: General Help
---

### Post by thenetduck on 2006-11-07
Hi, 
  For the last day, for some odd reason, my sound for my computer doesn't work. I'm using Edgy. I don't know what happened to make it go away, I did install the stuff to watch dvd's from the wiki, but I didn't think that would make my sound go away. Does anyone know where to start? I'm confused on why it went away, but more so why it won't come back. Does anyone have a solution for this? Thank you , 

 The Net Duck

---

### Post by Kateikyoushi on 2006-11-07
I would check alsamixer first, if still no sound follow the steps in this guide to see what went wrong. [LINK]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide")

If you get stuck provide us with more information about your hardware the output of these commands will do.
```
lspci -v
aplay -l
```

---

### Post by ...acid on 2006-11-07
check out some of the other threads.  Pretty common issue or so it seems.  Do you have more than one sound card?  integrated and pci?

---

### Post by thenetduck on 2006-11-07
Ok I can't find a solution. Here are my files.

lspci -v

```

00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
        Subsystem: ASUSTeK Computer Inc. Unknown device 8118
        Flags: bus master, 66MHz, medium devsel, latency 8
        Memory at e0000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: e4000000-e5ffffff
        Prefetchable memory behind bridge: c0000000-dfffffff
        Capabilities: <access denied>

00:09.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
        Subsystem: Belkin Unknown device 7000
        Flags: bus master, fast devsel, latency 32, IRQ 217
        Memory at e6000000 (32-bit, non-prefetchable) [size=8K]

00:0a.0 Modem: Motorola Unknown device 3052 (rev 04) (prog-if 00 [Generic])
        Subsystem: Motorola Unknown device 3020
        Flags: bus master, stepping, medium devsel, latency 32, IRQ 169
        Memory at e6002000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at b000 [size=256]
        Capabilities: <access denied>

00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. A8V Deluxe
        Flags: bus master, medium devsel, latency 32, IRQ 185
        Memory at e6003000 (32-bit, non-prefetchable) [size=2K]
        I/O ports at b400 [size=128]
        Capabilities: <access denied>

00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V Deluxe/K8V-X/A8V Deluxe motherboard
        Flags: bus master, medium devsel, latency 32, IRQ 177
        I/O ports at b800 [size=8]
        I/O ports at bc00 [size=4]
        I/O ports at c000 [size=8]
        I/O ports at c400 [size=4]
        I/O ports at c800 [size=16]
        I/O ports at cc00 [size=256]
        Capabilities: <access denied>

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard
        Flags: bus master, medium devsel, latency 32, IRQ 177
        I/O ports at d000 [size=16]
        Capabilities: <access denied>

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard
        Flags: bus master, medium devsel, latency 32, IRQ 193
        I/O ports at d400 [size=32]
        Capabilities: <access denied>

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard
        Flags: bus master, medium devsel, latency 32, IRQ 193
        I/O ports at d800 [size=32]
        Capabilities: <access denied>

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard
        Flags: bus master, medium devsel, latency 32, IRQ 193
        I/O ports at dc00 [size=32]
        Capabilities: <access denied>

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard
        Flags: bus master, medium devsel, latency 32, IRQ 193
        I/O ports at e000 [size=32]
        Capabilities: <access denied>

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard
        Flags: bus master, medium devsel, latency 32, IRQ 193
        Memory at e6004000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: <access denied>

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
        Subsystem: ASUSTeK Computer Inc. Unknown device 810a
        Flags: medium devsel, IRQ 209
        I/O ports at e400 [size=256]
        Capabilities: <access denied>

00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
        Flags: medium devsel, IRQ 209
        I/O ports at e800 [size=256]
        Capabilities: <access denied>

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
        Subsystem: ASUSTeK Computer Inc. Unknown device 80ff
        Flags: bus master, medium devsel, latency 32, IRQ 201
        I/O ports at ec00 [size=256]
        Memory at e6005000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600] (prog-if 00 [VGA])
        Subsystem: Connect Components Ltd Radeon 9600 256Mb Primary
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 225
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at a000 [size=256]
        Memory at e5000000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at e4000000 [disabled] [size=128K]
        Capabilities: <access denied>

01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)
        Subsystem: Connect Components Ltd Radeon 9600 256Mb Secondary
        Flags: 66MHz, medium devsel
        Memory at d0000000 (32-bit, prefetchable) [disabled] [size=256M]
        Memory at e5010000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <access denied>


```


aplay -l

```

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


```


Just a little information about my machine. I am using the sound card on the mother board. It's compaq made computer. I have added my own video card (ati 9600) and ram (1.5 GB). That sound was working and now is not, not sure why. It's an AMD process Seperon. I don't have two sound cards, just the default one that should  be on the mother board. Sound was working so I'm assuming there is one on the mother board. Thanks,
 The Net Duck

---

