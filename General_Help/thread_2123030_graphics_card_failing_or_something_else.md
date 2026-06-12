---
title: "graphics card failing or something else?"
date: 2013-03-06
forum: General Help
---

### Post by mrbojangles86 on 2013-03-06
hello!

i apologize if this is the wrong format/place for posting this type of question. im just wondering if this problem (screenshot below) is due to my graphics card failing or something with ubuntu working with my old hardware in general. its a nvidia 7300 le on a fresh install of 12.10 updated. linux-headers are 3.5.0-25-generic. the nouveau drivers seem to cause less of a problem than any of the proprietary. overheating was my first thought, but facing a fan at the open case changed nothing. turning down/off settings in the dconf editor and the nvidia panel didn't alter the problems either. also the purple rectangles flash as i move the mouse around the screen, if that helps at all haha. thanks for any help :)


[ATTACH=CONFIG]239854[/ATTACH]

---

### Post by Hodevah on 2013-03-06
Interesting problem you face there mrbojangles86. I am sorry that I can offer no help but I know that on my other partition having Windows 7, I experience this very same problem. Except that I have black bars. Initially, when I mentioned this to the computer shop where I bought my custom-made machine, I was told it was software. Initially, I thought much the same as yourself. Thinking that it was maybe over-heating or the graphics card. I had the card examined and I was told nothing was wrong. Bear that in mind, it may not necessarily be your graphics card, though I wouldnt rule that out entirely. Keep an open mind as I was asked to. In this case, I was told its software-based. I dont experience this problem at all while on Ubuntu. Strange. Hence my strong desire to use this OS, instead. 

What I might suggest is to have a look at your graphics card and do some research into it with respect to over-heating. It might also be the HDD. This is another idea that came to mind when I was facing pretty much the same problem as you. Flashing rectangles as you move the browser up and down and so forth. 
Sorry, but if I knew the answer I would tell you. And I apologize if I cant offer you much help in resolving this other than to tell you that it could by a number of things. Software, hard-ware, or maybe your system just isn't made for it.

---

### Post by Frogs Hair on 2013-03-06
Your older system may be struggling with Unity, but may run well with Lubuntu or Xubuntu. What are the CPU and memory specs?

---

### Post by Hodevah on 2013-03-06
Also, I forgot to mention earlier. Open a terminal and 
> lspci -v
This gives you the specs on all the stuff connected to your motherboard.

---

### Post by c2tarun on 2013-03-06
Since you installed Ubuntu 12.10, I would have suggested you to try Ubuntu 2D. :) meanwhile try installing Ubuntu fallback session and see if that works. You can get some info about it [here]("http://ubuntuforums.org/showthread.php?t=1966370").

---

### Post by mrbojangles86 on 2013-03-06
hello! i've had ubuntu 12.10 for a couple of months working with no issues, i reinstalled because i was thinking i screwed something up when this started about a week ago. 


memory - 3 gigs
processor - pentium d 2.8 ghz
os type - 64 bit
disk - 250 gigs

00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
    Subsystem: Dell Device 01dd
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=09 <?>

00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Memory behind bridge: dd000000-dfefffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
    Capabilities: [88] Subsystem: Dell Device 01dd
    Capabilities: [80] Power Management version 3
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [a0] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [140] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:19.0 Ethernet controller: Intel Corporation 82562V 10/100 Network Connection (rev 02)
    Subsystem: Dell Device 01dd
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at dffe0000 (32-bit, non-prefetchable) [size=128K]
    Memory at dffdb000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at ecc0 [size=32]
    Capabilities: [c8] Power Management version 2
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Kernel driver in use: e1000e
    Kernel modules: e1000e

00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Device 01dd
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at ff20 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Device 01dd
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at ff00 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
    Subsystem: Dell Device 01dd
    Flags: bus master, medium devsel, latency 0, IRQ 22
    Memory at dffdac00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
    Subsystem: Dell Device 01dd
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at dffdc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: dcf00000-dcffffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000d01fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Dell Device 01dd
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel
    Capabilities: [180] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Device 01dd
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at ff80 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Device 01dd
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at ff60 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Device 01dd
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at ff40 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
    Subsystem: Dell Device 01dd
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at ff980800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: dcd00000-dcefffff
    Capabilities: [50] Subsystem: Dell Device 01dd

00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich

00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA Controller [IDE mode] (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Dell Device 01dd
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
    I/O ports at fe00 [size=8]
    I/O ports at fe10 [size=4]
    I/O ports at fe20 [size=8]
    I/O ports at fe30 [size=4]
    I/O ports at fec0 [size=16]
    I/O ports at eca0 [size=16]
    Capabilities: [70] Power Management version 3
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
    Subsystem: Dell Device 01dd
    Flags: medium devsel, IRQ 10
    Memory at dffdab00 (32-bit, non-prefetchable) [size=256]
    I/O ports at ece0 [size=32]
    Kernel modules: i2c-i801

00:1f.5 IDE interface: Intel Corporation 82801HR/HO/HH (ICH8R/DO/DH) 2 port SATA Controller [IDE mode] (rev 02) (prog-if 85 [Master SecO PriO])
    Subsystem: Dell Device 01dd
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
    I/O ports at fe40 [size=8]
    I/O ports at fe50 [size=4]
    I/O ports at fe60 [size=8]
    I/O ports at fe70 [size=4]
    I/O ports at fed0 [size=16]
    I/O ports at ecb0 [size=16]
    Capabilities: [70] Power Management version 3
    Kernel driver in use: ata_piix

01:00.0 VGA compatible controller: NVIDIA Corporation G72 [GeForce 7300 LE] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Dell Device 0405
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at dd000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at de000000 (64-bit, non-prefetchable) [size=16M]
    Expansion ROM at dfe00000 [disabled] [size=128K]
    Capabilities: [60] Power Management version 2
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
    Kernel driver in use: nouveau
    Kernel modules: nouveau, nvidiafb

03:02.0 USB controller: ULi Electronics Inc. USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
    Subsystem: IOGEAR, Inc. Device 5237
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at dcded000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [60] Power Management version 2
    Kernel driver in use: ohci_hcd

03:02.1 USB controller: ULi Electronics Inc. USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
    Subsystem: IOGEAR, Inc. Device 5237
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at dcdee000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [60] Power Management version 2
    Kernel driver in use: ohci_hcd

03:02.2 USB controller: ULi Electronics Inc. USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
    Subsystem: IOGEAR, Inc. Device 5237
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at dcdef000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [60] Power Management version 2
    Kernel driver in use: ohci_hcd

03:02.3 USB controller: ULi Electronics Inc. USB 2.0 Controller (rev 01) (prog-if 20 [EHCI])
    Subsystem: IOGEAR, Inc. Device 1688
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at dcdec700 (32-bit, non-prefetchable) [size=256]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=0090
    Kernel driver in use: ehci_hcd

03:02.4 FireWire (IEEE 1394): ULi Electronics Inc. M5253 P1394 OHCI 1.1 Controller (prog-if 10 [OHCI])
    Subsystem: IOGEAR, Inc. Device 5253
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at dcdec800 (32-bit, non-prefetchable) [size=2K]
    Expansion ROM at dce00000 [disabled] [size=64K]
    Capabilities: [80] Power Management version 2
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci

03:03.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
    Subsystem: Conexant Systems, Inc. Dimension 3000
    Flags: bus master, medium devsel, latency 64, IRQ 5
    Memory at dcdf0000 (32-bit, non-prefetchable) [size=64K]
    I/O ports at dcf8 [size=8]
    Capabilities: [40] Power Management version 2

---

### Post by Frogs Hair on 2013-03-07
Your processor and memory are more than enough for any Ubuntu flavor so l am leaning towards a graphics card problem. Perhaps you could burn a Lubuntu cd/dvd and try it live to see what happens.

---

### Post by mrbojangles86 on 2013-03-08
installed lubuntu, things work better. rectangles are gone, lines come and go, but it's manageable for the moment. found an older cd of ubuntu 12.04, fired that up, same issues as before. so based on that, its pretty much gotta be a hardware issue because it worked fine in the past. i'll replace the graphics card soon. thanks everyone for the input and help!

---

