---
title: "Really need help"
date: 2008-06-10
forum: General Help
---

### Post by kayslay on 2008-06-10
****i still cant get my sound to work,what do i do please,im using ubuntu 7.10

---

### Post by TeoBigusGeekus on 2008-06-10
Is your card recognised by Ubuntu? Post us the output of 
```
lspci
```

---

### Post by kayslay on 2008-06-10
Yeah,here is the the output

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
        Subsystem: Lenovo Unknown device 383c
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c) (prog-if 00 [VGA])
        Subsystem: Lenovo Unknown device 383e
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at fc000000 (64-bit, non-prefetchable) [size=1M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 1800 [size=8]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
        Subsystem: Lenovo Unknown device 383e
        Flags: bus master, fast devsel, latency 0
        Memory at fc100000 (64-bit, non-prefetchable) [size=1M]
        Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Lenovo Unknown device 3846
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 1820 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Lenovo Unknown device 3847
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 1840 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
        Subsystem: Lenovo Unknown device 3849
        Flags: bus master, medium devsel, latency 0, IRQ 18
        Memory at fc504000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Lenovo Unknown device 384e
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at fc300000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: f6000000-f7ffffff
        Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: f8000000-f9ffffff
        Prefetchable memory behind bridge: 00000000f2000000-00000000f3ffffff
        Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: fa000000-fbffffff
        Prefetchable memory behind bridge: 00000000f4000000-00000000f5ffffff
        Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
        I/O behind bridge: 00005000-00005fff
        Memory behind bridge: c8000000-c9ffffff
        Prefetchable memory behind bridge: 00000000cc000000-00000000cdffffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Lenovo Unknown device 3843
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1860 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Lenovo Unknown device 3844
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1880 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Lenovo Unknown device 3845
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 18a0 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
        Subsystem: Lenovo Unknown device 3848
        Flags: bus master, medium devsel, latency 0, IRQ 20
        Memory at fc504400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=08, subordinate=08, sec-latency=32
        Memory behind bridge: fc200000-fc2fffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
        Subsystem: Lenovo Unknown device 3840
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Lenovo Unknown device 386d
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 1810 [size=16]

00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Lenovo Unknown device 3841
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at 1c00 [size=8]
        I/O ports at 18f4 [size=4]
        I/O ports at 18f8 [size=8]
        I/O ports at 18f0 [size=4]
        I/O ports at 18e0 [size=16]
        I/O ports at 18d0 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
        Subsystem: Lenovo Unknown device 3842
        Flags: medium devsel, IRQ 10
        Memory at 50000000 (32-bit, non-prefetchable) [size=256]
        I/O ports at 1c20 [size=32]

04:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
        Subsystem: Broadcom Corporation Unknown device 0465
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f8000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

06:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
        Subsystem: Lenovo Unknown device 3861
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at c8000000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

08:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (prog-if 10 [OHCI])
        Subsystem: Lenovo Unknown device 3829
        Flags: bus master, medium devsel, latency 32, IRQ 22
        Memory at fc200000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

08:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
        Subsystem: Lenovo Unknown device 382a
        Flags: bus master, medium devsel, latency 32, IRQ 20
        Memory at fc200800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

08:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
        Subsystem: Lenovo Unknown device 382b
        Flags: bus master, medium devsel, latency 0, IRQ 11
        Memory at fc200c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

08:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
        Subsystem: Lenovo Unknown device 382c
        Flags: medium devsel, IRQ 11
        Memory at fc201000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

08:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
        Subsystem: Lenovo Unknown device 382d
        Flags: medium devsel, IRQ 11
        Memory at fc201400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

---

### Post by TeoBigusGeekus on 2008-06-10
Look at this link, try it and post us what happened...
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/]("http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/")

---

### Post by kayslay on 2008-06-10
I followed what was the link u gave me and restarted my computer but still the sound is not working

---

### Post by xebian on 2008-06-10
> **kayslay said:**
> I followed what was the link u gave me and restarted my computer but still the sound is not working

Sound problem sometime is due to muted channels.  Try looking at your mixer.  Usually it's trial and error.  I have the front, center, and pcm enabled and raise the bar/volume up. Everything else disabled or muted- headphone, surround, line, lfe, cd.

---

### Post by kayslay on 2008-06-10
i have raised everything including the pcm,front,front mic and microphone but its still not working,

---

### Post by xebian on 2008-06-11
> **kayslay said:**
> i have raised everything including the pcm,front,front mic and microphone but its still not working,

The fact that you can see them is a good sign.  However, I'm not sure from your post if you did the other thing I wanted you to try.  To check if it's on 'mute'.  Sometimes, these laptops have a physical switch which you can try toggling on/off.

---

