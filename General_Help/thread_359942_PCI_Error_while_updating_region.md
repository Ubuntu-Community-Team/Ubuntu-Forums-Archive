---
title: "PCI: Error while updating region"
date: 2007-02-12
forum: General Help
---

### Post by ykhun on 2007-02-12
I'm running a server with the P5B Mobo on Core2 Duo, with 4 SATA disks mouted as 2 RAID 1 volumes and a GEFORCE 7300 LE gfx card. There is also an additional DVD drive. No other additional hardware on any PCI slots.

One thing which i did and i'm not sure if that causes the problem is that i do not have a mouse, keyb or monitor attach to the box. All work on the server is done remotedly.

Whenever i reboot, kern.log shows the following error. The blue section shows the region not being allocate and later on, the red section shows the region not being updated. 

I suspected the gfx card and tried the fix in this [thread](http://ubuntuforums.org/showthread.php?t=2544&highlight=PCI%3A+Error+while+updating) but it didn't work.

Anyone knows what might be causing this kernel error? The server still works fine, but it just bothers me and i hope to prevent this from becoming a more serious problem in the future.

```
eb 12 12:56:45 ping kernel: [42949377.760000] Linux Plug and Play Support v0.97 (c) Adam Belay
Feb 12 12:56:45 ping kernel: [42949377.760000] pnp: PnP ACPI init
Feb 12 12:56:45 ping kernel: [42949377.760000] pnp: PnP ACPI: found 13 devices
Feb 12 12:56:45 ping kernel: [42949377.760000] PnPBIOS: Disabled by ACPI PNP
Feb 12 12:56:45 ping kernel: [42949377.760000] PCI: Using ACPI for IRQ routing
Feb 12 12:56:45 ping kernel: [42949377.760000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[COLOR="Blue"]Feb 12 12:56:45 ping kernel: [42949377.760000] PCI: Cannot allocate resource region 0 of device 0000:03:00.0
Feb 12 12:56:45 ping kernel: [42949377.760000] PCI: Cannot allocate resource region 1 of device 0000:03:00.0
Feb 12 12:56:45 ping kernel: [42949377.760000] PCI: Cannot allocate resource region 2 of device 0000:03:00.0
Feb 12 12:56:45 ping kernel: [42949377.760000] PCI: Cannot allocate resource region 3 of device 0000:03:00.0[/COLOR]
Feb 12 12:56:45 ping kernel: [42949377.780000] pnp: 00:08: ioport range 0x290-0x297 has been reserved
Feb 12 12:56:45 ping kernel: [42949377.780000] PCI: Bridge: 0000:00:01.0
Feb 12 12:56:45 ping kernel: [42949377.780000]   IO window: disabled.
Feb 12 12:56:45 ping kernel: [42949377.780000]   MEM window: fa700000-fe7fffff
Feb 12 12:56:45 ping kernel: [42949377.780000]   PREFETCH window: bfe00000-dfdfffff
Feb 12 12:56:45 ping kernel: [42949377.780000] PCI: Bridge: 0000:00:1c.0
Feb 12 12:56:45 ping kernel: [42949377.780000]   IO window: disabled.
Feb 12 12:56:45 ping kernel: [42949377.780000]   MEM window: disabled.
Feb 12 12:56:45 ping kernel: [42949377.780000]   PREFETCH window: dfe00000-dfefffff
Feb 12 12:56:45 ping kernel: [42949377.780000] PCI: Ignore bogus resource 1 [0:0] of 0000:03:00.0
Feb 12 12:56:45 ping kernel: [42949377.780000] PCI: Ignore bogus resource 3 [0:0] of 0000:03:00.0
[COLOR="Red"]Feb 12 12:56:45 ping kernel: [42949377.780000] PCI: Error while updating region 0000:03:00.0/0 (0000a000 != 00000000)
Feb 12 12:56:45 ping kernel: [42949377.780000] PCI: Error while updating region 0000:03:00.0/2 (0000a008 != 00000000)[/COLOR]
Feb 12 12:56:45 ping kernel: [42949377.780000] PCI: Bridge: 0000:00:1c.4
Feb 12 12:56:45 ping kernel: [42949377.780000]   IO window: a000-afff
Feb 12 12:56:45 ping kernel: [42949377.780000]   MEM window: fe900000-fe9fffff
Feb 12 12:56:45 ping kernel: [42949377.780000]   PREFETCH window: disabled.
Feb 12 12:56:45 ping kernel: [42949377.780000] PCI: Bridge: 0000:00:1c.5
Feb 12 12:56:45 ping kernel: [42949377.780000]   IO window: 9000-9fff
Feb 12 12:56:45 ping kernel: [42949377.780000]   MEM window: fe800000-fe8fffff
Feb 12 12:56:45 ping kernel: [42949377.780000]   PREFETCH window: disabled.
Feb 12 12:56:45 ping kernel: [42949377.780000] PCI: Bridge: 0000:00:1e.0
Feb 12 12:56:45 ping kernel: [42949377.780000]   IO window: b000-bfff
Feb 12 12:56:45 ping kernel: [42949377.780000]   MEM window: fea00000-feafffff
Feb 12 12:56:45 ping kernel: [42949377.780000]   PREFETCH window: 88000000-880fffff
Feb 12 12:56:45 ping kernel: [42949377.780000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
Feb 12 12:56:45 ping kernel: [42949377.780000] PCI: Setting latency timer of device 0000:00:01.0 to 64
Feb 12 12:56:45 ping kernel: [42949377.780000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
Feb 12 12:56:45 ping kernel: [42949377.780000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Feb 12 12:56:45 ping kernel: [42949377.780000] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 169
Feb 12 12:56:45 ping kernel: [42949377.780000] PCI: Setting latency timer of device 0000:00:1c.4 to 64
Feb 12 12:56:45 ping kernel: [42949377.780000] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 17 (level, low) -> IRQ 177
Feb 12 12:56:45 ping kernel: [42949377.780000] PCI: Setting latency timer of device 0000:00:1c.5 to 64
Feb 12 12:56:45 ping kernel: [42949377.780000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Feb 12 12:56:45 ping kernel: [42949377.780000] NET: Registered protocol family 2
```

---

### Post by seppo on 2007-02-12
You can debug this by looking up the PCI ID.

In your case 03:00.0 is causing the error:

sudo lspci

you can see which device is responsible for the errors. I'm not a hardware guru, but maybe it has something to do with an IRQ conflict? I've seen these types of errors also on my laptop. In my case it was the SD card reader, which caused the errors. The errors did not affect stability in my case.

---

### Post by ykhun on 2007-02-12
Thx for the headsup. I did lpsc -vvv and found that the problem matches to the following hardware.

```
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81e4
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 169
        Region 0: [virtual] Memory at 0000a000 (32-bit, non-prefetchable) [size=8]
        Region 2: [virtual] Memory at 0000a000 (32-bit, prefetchable) [size=8]
        Region 5: Memory at fe9fe000 (32-bit, non-prefetchable) [size=8K]
        Expansion ROM at fe9e0000 [disabled] [size=64K]
        Capabilities: [68] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [50] Express Legacy Endpoint IRQ 1
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
                Device: Latency L0s <64ns, L1 <1us
                Device: AtnBtn- AtnInd- PwrInd-
                Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
                Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
                Device: MaxPayload 128 bytes, MaxReadReq 512 bytes
                Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s, Port 1
                Link: Latency L0s <1us, L1 <16us
                Link: ASPM Disabled RCB 64 bytes CommClk+ ExtSynch-
                Link: Speed 2.5Gb/s, Width x1
```

I'm pretty certain i'm not using that SATA controller, but i'm not sure if i can disable that in the bios and still bootup the box... Any1 had taken the plunge on the P5B mobo before?

---

