---
title: "Volume control applet doesn't mute properly"
date: 2008-01-24
forum: General Help
---

### Post by kimangroo on 2008-01-24
Hi all, enjoying my first installation of Ubuntu, but I noticed that the volume control applet doesn't seem to mute when it should.

If I drag the volume control right down, the icon changes and it says muted, but it still plays sound, only very quietly.

If I double click on the icon and have the main volume controls showing at the same time, when I drag the volume control down on the applet it does mute the sound but then stops working/moving...

It's a little strange. I might not be particularly bothered but as my cruddy old laptop doesn't have an external volume control I'm very dependent on that little applet.

Can anyone help?

Thanks.

---

### Post by peabody on 2008-01-24
Could you tell us the make of your audio card and if you don't know that, could you try running 'lspci -vv' in a terminal app and pasting the output here?

---

### Post by kimangroo on 2008-01-25
Thanks for the reply, sorry for being late to respond. I've had a number of other problems recently with Firefox hanging/greying out and my mouse cursor skipping etc... :( Seems my ubuntu honeymoon period was very brief!

Anyway back on topic, I don't know my audio card but lspci -v (I figured -w was a typo) gave this output:

```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
        Subsystem: Hewlett-Packard Company NX6110/NC6120
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company NX6110/NC6120
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at d0400000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 7000 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at d0480000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
        Subsystem: Hewlett-Packard Company NX6110/NC6120
        Flags: bus master, fast devsel, latency 0
        Memory at d0500000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company NX6110/NC6120
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 2000 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company NX6110/NC6120
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 2020 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company NX6110/NC6120
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 2040 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company NX6110/NC6120
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 2060 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company NX6110/NC6120
        Flags: bus master, medium devsel, latency 0, IRQ 18
        Memory at d0580000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=06, sec-latency=32
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: d0000000-d03fffff
        Prefetchable memory behind bridge: 0000000030000000-0000000033ffffff
        Capabilities: <access denied>

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company NX6110/NC6120
        Flags: bus master, medium devsel, latency 0, IRQ 22
        I/O ports at 2100 [size=256]
        I/O ports at 2200 [size=64]
        Memory at d0581000 (32-bit, non-prefetchable) [size=512]
        Memory at d0582000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
        Subsystem: Hewlett-Packard Company NX6110/NC6120
        Flags: medium devsel, IRQ 17
        I/O ports at 2400 [size=256]
        I/O ports at 2500 [size=128]
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
        Subsystem: Hewlett-Packard Company NX6110/NC6120
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company NX6110/NC6120
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 2580 [size=16]

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
        Flags: medium devsel
        I/O ports at 1200 [size=32]

02:04.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
        Subsystem: Hewlett-Packard Company Presario R3000 802.11b/g
        Flags: bus master, fast devsel, latency 64, IRQ 22
        Memory at d0000000 (32-bit, non-prefetchable) [size=8K]

02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
        Subsystem: Hewlett-Packard Company NX6110/NC6120
        Flags: bus master, medium devsel, latency 168, IRQ 16
        Memory at d0002000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: 30000000-33fff000 (prefetchable)
        Memory window 1: 34000000-37fff000
        I/O window 0: 00003000-000030ff
        I/O window 1: 00003400-000034ff
        16-bit legacy interface ports at 0001

02:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company NX6110/NC6120
        Flags: bus master, medium devsel, latency 64, IRQ 17
        Memory at d0003000 (32-bit, non-prefetchable) [size=2K]
        Memory at d0004000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

02:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
        Subsystem: Hewlett-Packard Company NX6110/NC6120
        Flags: bus master, fast devsel, latency 64, IRQ 21
        Memory at d000e000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

```

Hope you can help!

---

