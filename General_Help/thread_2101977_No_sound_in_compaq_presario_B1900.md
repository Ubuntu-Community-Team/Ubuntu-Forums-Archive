---
title: "No sound in compaq presario B1900"
date: 2013-01-05
forum: General Help
---

### Post by somrita on 2013-01-05
I am getting no sound in ubuntu.I use compaq presario B1900.All hardwares are ok(I use dual operating systems...ubuntu and windows).Please tell me step by step how to solve the problem.I am using Rhythmbox.Inform if you need any other information.



Thanks in advance

---

### Post by iMurshaq on 2013-01-05
please show:

lsusb

lspci

---

### Post by somrita on 2013-01-05
> **iMurshaq said:**
> please show:

lsusb

lspci


Sorry,I did not understand.Please explain in another way


Thanks

---

### Post by somrita on 2013-01-05
I am new to ubuntu.So please tell me step by step

---

### Post by iMurshaq on 2013-01-06
open terminal, type in those commands and paste the output here in CODE brackets

---

### Post by somrita on 2013-01-06
after lspci,here is what i get...
[ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI Device 5a31 (rev 01)
00:01.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI Bridge
00:04.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI Bridge
00:05.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI Bridge
00:12.0 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller (rev 80)
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller (rev 80)
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RC410 [Radeon Xpress 200M]
02:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
08:07.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
08:07.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:07.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
08:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
]
and after lusb,i get
[
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 19d2:2003 ZTE WCDMA Technologies MSM 
]


any more information??thanks in advance.

---

### Post by fdrake on 2013-01-06
check that alsamixer is not muted
```

alsmaixer

```

also, if still no luck, can you post the output of
```

sudo lspci  -vvv -s 00:14.2 

```
```
aplay -l
```
```
aplay -L
```

---

### Post by somrita on 2013-01-06
after i ran "sudo lspci  -vvv -s 00:14.2".......i get..................
[
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI IXP SB4x0 High Definition Audio Controller (rev 01)
    Subsystem: Hewlett-Packard Company Device 30ba
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 40
    Region 0: Memory at c0500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Address: 00000000fee0300c  Data: 4169
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
]

---

### Post by somrita on 2013-01-06
aplay-L gives this...................
[
default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=SB
    HDA ATI SB, ALC260 Analog
    Default Audio Device
front:CARD=SB,DEV=0
    HDA ATI SB, ALC260 Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, ALC260 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, ALC260 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, ALC260 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, ALC260 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, ALC260 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=SB,DEV=0
    HDA ATI SB, ALC260 Analog
    Direct sample mixing device
dsnoop:CARD=SB,DEV=0
    HDA ATI SB, ALC260 Analog
    Direct sample snooping device
hw:CARD=SB,DEV=0
    HDA ATI SB, ALC260 Analog
    Direct hardware device without any conversions
plughw:CARD=SB,DEV=0
    HDA ATI SB, ALC260 Analog
    Hardware device with all software conversions
]

---

### Post by somrita on 2013-01-06
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



Found out I  have realtek alc260

---

### Post by somrita on 2013-01-06
My alsamixer is not muted also
@fdrake

---

### Post by fdrake on 2013-01-06
> **somrita said:**
> My alsamixer is not muted also
@fdrake

could you please run the alsa scritp
```

wget -O alsa-info.sh http://www.alsa-project.org/alsa-info.sh && chmod +x ./alsa-info.sh && ./alsa-info.sh

```

post here the link to your results please.

---

### Post by somrita on 2013-01-06
[http://www.alsa-project.org/db/?f=195f4dd7d6f03a366a3df1fb8b0a9616fb6c42dc](http://www.alsa-project.org/db/?f=195f4dd7d6f03a366a3df1fb8b0a9616fb6c42dc)


Thanks

---

### Post by gordintoronto on 2013-01-06
What operating system are you using? For example, it might be Ubuntu 12.04 32-bit.

When there is no sound, usually it is muted somewhere. Please run sound settings and check that the appropriate device is selected, and not muted. Run the speaker test.

---

### Post by somrita on 2013-01-06
I am using ubuntu 12.04 32 bit.I am giving you a brief of sound settings........Output is analog output(built-in audio).Volume is 100.Sound effects default.I did the speaker test.Left and right speakers looked like fine but no audio was audible.Also,during booting time,there is no music.

Thanks.

---

### Post by gordintoronto on 2013-01-07
In sound settings, what device? What "connector"? Where are the speakers plugged in, front or back?

---

### Post by somrita on 2013-01-08
I typed aplay-l in  terminal and here is what I get....
```

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```.
I use a notebook.The speakers are not plugged externally.Pardon,I did nt understand what you mean by 'connector'.Here is what I got by lspci-v
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI Device 5a31 (rev 01)
    Subsystem: Hewlett-Packard Company Device 30ba
    Flags: bus master, 66MHz, medium devsel, latency 64
    Kernel modules: ati-agp

00:01.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI Bridge (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: c0000000-c00fffff
    Prefetchable memory behind bridge: d0000000-dfffffff
    Capabilities: <access denied>
    Kernel modules: shpchp

00:04.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI Bridge (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=04, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: 38600000-388fffff
    Prefetchable memory behind bridge: 0000000038900000-0000000038afffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:05.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI Bridge (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=07, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: 38200000-383fffff
    Prefetchable memory behind bridge: 0000000038400000-00000000385fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:12.0 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Hewlett-Packard Company Device 30ba
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
    I/O ports at 8440 [size=8]
    I/O ports at 8430 [size=4]
    I/O ports at 8420 [size=8]
    I/O ports at 8410 [size=4]
    I/O ports at 8400 [size=16]
    Memory at c0507000 (32-bit, non-prefetchable) [size=512]
    [virtual] Expansion ROM at 38100000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: sata_sil
    Kernel modules: sata_sil

00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Device 30ba
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at c0504000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Device 30ba
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at c0505000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device 30ba
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at c0506000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI IXP SB400 SMBus Controller (rev 83)
    Subsystem: Hewlett-Packard Company Device 30ba
    Flags: 66MHz, medium devsel
    I/O ports at 8450 [size=16]
    Memory at c0507400 (32-bit, non-prefetchable) [size=1K]
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4

00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 IDE Controller (rev 80) (prog-if 82 [Master PriP])
    Subsystem: Hewlett-Packard Company Device 30ba
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 8460 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp

00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI IXP SB4x0 High Definition Audio Controller (rev 01)
    Subsystem: Hewlett-Packard Company Device 30ba
    Flags: bus master, slow devsel, latency 64, IRQ 40
    Memory at c0500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-ISA Bridge (rev 80)
    Subsystem: Hewlett-Packard Company Device 30ba
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=08, subordinate=0a, sec-latency=64
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: f0200000-f02fffff
    Prefetchable memory behind bridge: f0300000-f03fffff

01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RC410 [Radeon Xpress 200M] (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device 30ba
    Flags: bus master, 66MHz, medium devsel, latency 66, IRQ 17
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 9000 [size=256]
    Memory at c0000000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at c0020000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon, radeonfb

02:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
    Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at 38600000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

08:07.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Device 30ba
    Flags: bus master, medium devsel, latency 64, IRQ 22
    Memory at c0200000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci

08:07.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
    Subsystem: Hewlett-Packard Company Device 30ba
    Flags: bus master, medium devsel, latency 64, IRQ 23
    Memory at c0200800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

08:07.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
    Subsystem: Hewlett-Packard Company Device 30ba
    Flags: medium devsel, IRQ 23
    Memory at c0201000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: r592
    Kernel modules: r592

08:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Hewlett-Packard Company Device 30ba
    Flags: bus master, medium devsel, latency 64, IRQ 21
    I/O ports at a000 [size=256]
    Memory at c0201400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp

```.
Any other information?thank you

---

### Post by somrita on 2013-01-08
> **somrita said:**
> I am using ubuntu 12.04 32 bit.I am giving you a brief of sound settings........Output is analog output(built-in audio).Volume is 100.Sound effects default.I did the speaker test.Left and right speakers looked like fine but no audio was audible.Also,during booting time,there is no music.

Thanks.

I got this ,by going to System Settings>Sound

---

### Post by somrita on 2013-01-13
Sorry could not solve the problem yet.Please help.


Thanks.

---

