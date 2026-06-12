---
title: "Odd suspend issue"
date: 2013-02-26
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2013-02-26
i am using a Asus M4A78LT-M which is powered by a Cooler Master GX 430w PSU

it likes to come out of suspend by it self a lot i traced a the wireless mouse to waking it up when it is moved, well i unpluged it and turned the other wireless mouse off, leaving only 1 usb wired keyboard plugged in, i put it in suspend and left the room, and this is the weired part, when i came back and tured the ceiling light on, it magically waked up from suspend, this is the second time i noticed it did that

How on earth does turning a light on wake a computer from suspend? it is not like i installed a light sensor to this system

i do have wake on lan 
in the BIOS have these enabled:

```
Power on From S5 By PME# [Disabled]
Enables or disables PME wake from sleep states. Configuration options: [Disabled] [Enabled]

Power on From S5 By Ring [Disabled]
Enables or disables ring to generate a wake event. Configuration options: [Disabled][Enabled]

```

edit: now it happened when picking an empty bag up in the room

---

### Post by Toz on 2013-02-26
That really is very odd. 

What devices are enabled as wakeup devices?
```
cat /proc/acpi/wakeup
```

You can use "lspci" to give you some info about the devices that are listed in the "Sysfs node" column.

You can also trouble-shoot by disabling some of those enabled devices by:
```
echo DEV | sudo tee /proc/acpi/wakeup
```
...where DEV is the Device name (the echo command will act like a toggle).

Maybe movement is triggering one of the wakeup devices ???

---

### Post by pqwoerituytrueiwoq on 2013-02-26
i disabled wake on lan and it still booted up at seemingly random
and i was unable to make it boot with all usb devices unplugged (printer, wireless mouse, and keyboard)
from lsusb, i assume supertop is the internal card reader
```
Bus 002 Device 002: ID 14cd:8168 Super Top 
Bus 003 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 005: ID 1c4f:0002 SiGma Micro Keyboard TRACER Gamma Ivory
```

```
susan@desktop:~$ cat /proc/acpi/wakeup
Device    S-state      Status   Sysfs node
PCE2      S4    *disabled  pci:0000:00:02.0
PCE3      S4    *disabled
PCE4      S4    *disabled
PCE5      S4    *disabled
PCE6      S4    *disabled
PCE7      S4    *disabled
PCE9      S4    *disabled
PCEA      S4    *disabled
PCEB      S4    *disabled
PCEC      S4    *disabled
SBAZ      S4    *disabled  pci:0000:00:14.2
UAR1      S4    *disabled  pnp:00:08
P0PC      S4    *disabled  pci:0000:00:14.4
UHC1      S4    *enabled   pci:0000:00:12.0
UHC2      S4    *enabled   pci:0000:00:12.1
UHC3      S4    *enabled   pci:0000:00:12.2
USB4      S4    *enabled   pci:0000:00:13.0
UHC5      S4    *enabled   pci:0000:00:13.1
UHC6      S4    *enabled   pci:0000:00:13.2
UHC7      S4    *enabled   pci:0000:00:14.5
susan@desktop:~$ lspci -vv
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
    Subsystem: ASUSTeK Computer Inc. Device 8388
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: <access denied>

00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fd000000-feafffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000fbffffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity+ SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. Device 8389
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 22
    Region 0: I/O ports at c000 [size=8]
    Region 1: I/O ports at b000 [size=4]
    Region 2: I/O ports at a000 [size=8]
    Region 3: I/O ports at 9000 [size=4]
    Region 4: I/O ports at 8000 [size=16]
    Region 5: Memory at fcfffc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Device 8389
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at fcffe000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Device 8389
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at fcffd000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 8389
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin B routed to IRQ 17
    Region 0: Memory at fcfff800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Device 8389
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 18
    Region 0: Memory at fcffc000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Device 8389
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 18
    Region 0: Memory at fcffb000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 8389
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin B routed to IRQ 19
    Region 0: Memory at fcfff400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 3c)
    Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort+ <MAbort- >SERR- <PERR- INTx-
    Capabilities: <access denied>
    Kernel modules: sp5100_tco, i2c-piix4

00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller (prog-if 8a [Master SecP PriP])
    Subsystem: ASUSTeK Computer Inc. Device 8389
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Interrupt: pin A routed to IRQ 16
    Region 0: I/O ports at 01f0 [size=8]
    Region 1: I/O ports at 03f4 [size=1]
    Region 2: I/O ports at 0170 [size=8]
    Region 3: I/O ports at 0374 [size=1]
    Region 4: I/O ports at ff00 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_acpi
    Kernel modules: pata_atiixp

00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
    Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at fcff4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller
    Subsystem: ASUSTeK Computer Inc. Device 8389
    Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0

00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: feb00000-febfffff
    Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity+ SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-

00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Device 8389
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin C routed to IRQ 18
    Region 0: Memory at fcffa000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Capabilities: <access denied>
    Kernel driver in use: k10temp
    Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 430] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: NVIDIA Corporation Device 0000
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 18
    Region 0: Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Region 1: Memory at f0000000 (64-bit, prefetchable) [size=128M]
    Region 3: Memory at fa000000 (64-bit, prefetchable) [size=32M]
    Region 5: I/O ports at dc00 [size=128]
    [virtual] Expansion ROM at fea80000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia_current, nouveau, nvidiafb

01:00.1 Audio device: NVIDIA Corporation GF108 High Definition Audio Controller (rev a1)
    Subsystem: NVIDIA Corporation Device 0000
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin B routed to IRQ 19
    Region 0: Memory at fea7c000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

02:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8169 PCI Gigabit Ethernet Controller (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8169/8110 Family PCI Gigabit Ethernet NIC
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (8000ns min, 16000ns max), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 21
    Region 0: I/O ports at e800 [size=256]
    Region 1: Memory at febffc00 (32-bit, non-prefetchable) [size=256]
    Expansion ROM at febc0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

```

---

### Post by jwbrase on 2013-02-26
> **pqwoerituytrueiwoq said:**
> i am using a Asus M4A78LT-M which is powered by a Cooler Master GX 430w PSU

it likes to come out of suspend by it self a lot i traced a the wireless mouse to waking it up when it is moved, well i unpluged it and turned the other wireless mouse off, leaving only 1 usb wired keyboard plugged in, i put it in suspend and left the room, and this is the weired part, when i came back and tured the ceiling light on, it magically waked up from suspend, this is the second time i noticed it did that

How on earth does turning a light on wake a computer from suspend?

My guess would be that flipping the switch is causing radio interference that's causing a wakeup.

> 
edit: now it happened when picking an empty bag up in the room

This, on the other hand, is just weird...

---

### Post by pqwoerituytrueiwoq on 2013-02-27
> **jwbrase said:**
> My guess would be that flipping the switch is causing radio interference that's causing a wakeup.
will try it without the usb wireless mouse dongle connected

---

### Post by sandyd on 2013-02-27
electrical main spike interference as well, when you turn on the light
I had a problem with that in my old house until I got a UPS with filtering

---

### Post by pqwoerituytrueiwoq on 2013-02-27
> **sandyd said:**
> electrical main spike interference as well, when you turn on the light
I had a problem with that in my old house until I got a UPS with filtering
This is a new house was built in 2011 (or late 2010)
a UPS is expensive

---

### Post by mörgæs on 2013-02-27
But a filter for the mains power isn't. You can easily build one yourself.

---

### Post by pqwoerituytrueiwoq on 2013-02-27
> **mörgæs said:**
> But a filter for the mains power isn't. You can easily build one yourself.
are you refing to something that goes in the circuit breaker panel?

---

### Post by dino99 on 2013-02-27
> **pqwoerituytrueiwoq said:**
> are you refing to something that goes in the circuit breaker panel?

looks like that new house is a huge micro-waves box  :confused: interfering with magnetic fields

---

### Post by mörgæs on 2013-02-27
> **pqwoerituytrueiwoq said:**
> are you refing to something that goes in the circuit breaker panel?

No, I was thinking of a filter that sits on the power cable to the computer.

If you look at item 38 (Pi filter) in the list
[http://www.victorpower.com/knowledge_base.php](http://www.victorpower.com/knowledge_base.php)

you will see the diagram. In the explanation, swap 'high frequency' (=noise signal) for 'AC' and 'low frequency' (the power current itself) for 'DC'.

Let me know if you need more details.

---

### Post by pqwoerituytrueiwoq on 2013-02-27
managed to get a higher reproduction rate
turn light on when entering room then open the closet doors
computer wakes up 

this is without any wireless devices connected
there is nothing electrical involving the closet doors

---

