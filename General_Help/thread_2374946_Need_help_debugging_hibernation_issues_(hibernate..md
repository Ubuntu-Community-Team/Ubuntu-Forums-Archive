---
title: "Need help debugging hibernation issues (hibernate.target: Job hibernate.target/start)"
date: 2017-10-20
forum: General Help
---

### Post by chaoslord2 on 2017-10-20
As stated above, I am unable to hibernate when using a large amount of ram (over 4GB) even though my swap partition is over 12 GB for a machine with 8 GB of RAM, the computer fails to power off and leaves itself on the lock screen. Suspension works fine, swapon reports that the swap partition is nowhere close to full. Suspend-log is blank, however syslog has some (vague to the point of useless) errors. Reducing RAM usage immediately allows it to work as normal. I have done my googling and found that my error does not fall into any of the common hibernation issue categories while at the same time I have no idea how to get more information on the problem. Help would be much appreciated.

Here are the errors from syslog:  
```
Oct 20 14:23:58 user-B85M-HD3 systemd[1]: Reached target Sleep.
Oct 20 14:23:58 user-B85M-HD3 systemd[1]: Starting Hibernate...
Oct 20 14:23:58 user-B85M-HD3 kernel: [   38.303196] PM: Hibernation mode set to 'platform'
Oct 20 14:23:58 user-B85M-HD3 systemd-sleep[3005]: Suspending system...
Oct 20 14:24:02 user-B85M-HD3 kernel: [   38.503663] PM: Syncing filesystems ... 
Oct 20 14:24:02 user-B85M-HD3 kernel: [   38.600657] done.
Oct 20 14:24:02 user-B85M-HD3 kernel: [   38.600686] Freezing user space processes ... (elapsed 0.001 seconds) done.
Oct 20 14:24:02 user-B85M-HD3 kernel: [   38.602117] PM: Marking nosave pages: [mem 0x00000000-0x00000fff]
Oct 20 14:24:02 user-B85M-HD3 kernel: [   38.602134] PM: Marking nosave pages: [mem 0x00058000-0x00058fff]
Oct 20 14:24:02 user-B85M-HD3 kernel: [   38.602151] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Oct 20 14:24:02 user-B85M-HD3 kernel: [   38.602169] PM: Marking nosave pages: [mem 0xa930d000-0xa9313fff]
Oct 20 14:24:02 user-B85M-HD3 kernel: [   38.602186] PM: Marking nosave pages: [mem 0xa9bf6000-0xa9e65fff]
Oct 20 14:24:02 user-B85M-HD3 kernel: [   38.602209] PM: Marking nosave pages: [mem 0xba0a8000-0xbaffefff]
Oct 20 14:24:02 user-B85M-HD3 kernel: [   38.602264] PM: Marking nosave pages: [mem 0xbb000000-0xffffffff]
Oct 20 14:24:02 user-B85M-HD3 kernel: [   38.602800] PM: Basic memory bitmaps created
Oct 20 14:24:02 user-B85M-HD3 kernel: [   38.602857] PM: Preallocating image memory... 
Oct 20 14:24:02 user-B85M-HD3 kernel: [   41.526695] PM: Basic memory bitmaps freed
Oct 20 14:24:02 user-B85M-HD3 kernel: [   41.526714] Restarting tasks ... done.
Oct 20 14:24:02 user-B85M-HD3 kernel: [   41.527185] video LNXVIDEO:00: Restoring backlight state
Oct 20 14:24:02 user-B85M-HD3 systemd[1]: systemd-hibernate.service: Main process exited, code=exited, status=1/FAILURE
Oct 20 14:24:02 user-B85M-HD3 systemd[1]: Failed to start Hibernate.
Oct 20 14:24:02 user-B85M-HD3 systemd[1]: Dependency failed for Hibernate.
Oct 20 14:24:02 user-B85M-HD3 systemd[1]: hibernate.target: Job hibernate.target/start failed with result 'dependency'.
Oct 20 14:24:02 user-B85M-HD3 systemd[1]: sleep.target: Unit not needed anymore. Stopping.
Oct 20 14:24:02 user-B85M-HD3 systemd[1]: systemd-hibernate.service: Unit entered failed state.
Oct 20 14:24:02 user-B85M-HD3 systemd[1]: systemd-hibernate.service: Failed with result 'exit-code'.
Oct 20 14:24:03 user-B85M-HD3 systemd[1]: Stopped target Sleep.
```

---

### Post by chaoslord2 on 2017-10-20
some more info as a friend pointed out I was missing some important  stuff. I'm on lubuntu 17.04 and this is my responce to lspci -vvv: 

```
00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd 4th Gen Core Processor DRAM Controller
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: <access denied>
    Kernel driver in use: hsw_uncore

00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core  Processor PCI Express x16 Controller (rev 06) (prog-if 00 [Normal  decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 26
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: d0000000-db0fffff
    Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th  Gen Core Processor Integrated Graphics Controller (rev 06) (prog-if 00  [VGA controller])
    Subsystem: Gigabyte Technology Co., Ltd Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 30
    Region 0: Memory at db400000 (64-bit, non-prefetchable) [size=4M]
    Region 2: Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Region 4: I/O ports at f000 [size=64]
    [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
    Subsystem: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 31
    Region 0: Memory at db914000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05) (prog-if 30 [XHCI])
    Subsystem: Gigabyte Technology Co., Ltd 8 Series/C220 Series Chipset Family USB xHCI
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 27
    Region 0: Memory at db900000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: Gigabyte Technology Co., Ltd 8 Series/C220 Series Chipset Family MEI Controller
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 32
    Region 0: Memory at db91f000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: mei_me
    Kernel modules: mei_me

00:16.3 Serial controller: Intel Corporation 8 Series/C220 Series Chipset Family KT Controller (rev 04) (prog-if 02 [16550])
    Subsystem: Gigabyte Technology Co., Ltd 8 Series/C220 Series Chipset Family KT Controller
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin B routed to IRQ 19
    Region 0: I/O ports at f0c0 [size=8]
    Region 1: Memory at db91d000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: serial

00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05) (prog-if 20 [EHCI])
    Subsystem: Gigabyte Technology Co., Ltd 8 Series/C220 Series Chipset Family USB EHCI
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at db91c000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
    Subsystem: Gigabyte Technology Co., Ltd 8 Series/C220 Series Chipset High Definition Audio Controller
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 33
    Region 0: Memory at db910000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset  Family PCI Express Root Port #1 (rev d5) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 16
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000f000-00000fff
    Memory behind bridge: fff00000-000fffff
    Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset  Family PCI Express Root Port #3 (rev d5) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin C routed to IRQ 18
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: db800000-db8fffff
    Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d5) (prog-if 01 [Subtractive decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin D routed to IRQ 3
    Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
    I/O behind bridge: 0000f000-00000fff
    Memory behind bridge: fff00000-000fffff
    Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>

00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05) (prog-if 20 [EHCI])
    Subsystem: Gigabyte Technology Co., Ltd 8 Series/C220 Series Chipset Family USB EHCI
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 23
    Region 0: Memory at db91b000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1f.0 ISA bridge: Intel Corporation B85 Express LPC Controller (rev 05)
    Subsystem: Gigabyte Technology Co., Ltd B85 Express LPC Controller
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: <access denied>
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich

00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset  Family 6-port SATA Controller 1 [AHCI mode] (rev 05) (prog-if 01 [AHCI  1.0])
    Subsystem: Gigabyte Technology Co., Ltd 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 29
    Region 0: I/O ports at f0b0 [size=8]
    Region 1: I/O ports at f0a0 [size=4]
    Region 2: I/O ports at f090 [size=8]
    Region 3: I/O ports at f080 [size=4]
    Region 4: I/O ports at f060 [size=32]
    Region 5: Memory at db91a000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
    Subsystem: Gigabyte Technology Co., Ltd 8 Series/C220 Series Chipset Family SMBus Controller
    Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin C routed to IRQ 10
    Region 0: Memory at db919000 (64-bit, non-prefetchable) [disabled] [size=256]
    Region 4: I/O ports at f040 [size=32]
    Kernel modules: i2c_i801

01:00.0 VGA compatible controller: NVIDIA Corporation GK104 [GeForce GTX 760] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: ZOTAC International (MCO) Ltd. GK104 [GeForce GTX 760]
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 11
    Region 0: Memory at da000000 (32-bit, non-prefetchable) [disabled] [size=16M]
    Region 1: Memory at d0000000 (64-bit, prefetchable) [disabled] [size=128M]
    Region 3: Memory at d8000000 (64-bit, prefetchable) [disabled] [size=32M]
    Region 5: I/O ports at e000 [disabled] [size=128]
    Expansion ROM at db000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel modules: nvidiafb, nouveau

01:00.1 Audio device: NVIDIA Corporation GK104 HDMI Audio Controller (rev a1)
    Subsystem: ZOTAC International (MCO) Ltd. GK104 HDMI Audio Controller
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin B routed to IRQ 17
    Region 0: Memory at db080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd Onboard Ethernet
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 28
    Region 0: I/O ports at d000 [size=256]
    Region 2: Memory at db804000 (64-bit, non-prefetchable) [size=4K]
    Region 4: Memory at db800000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

04:00.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 41) (prog-if 01 [Subtractive decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 3
    Bus: primary=04, secondary=05, subordinate=05, sec-latency=32
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: bfa00000-bfbfffff
    Prefetchable memory behind bridge: 00000000bfc00000-00000000bfdfffff
    Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr+ DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>


```

Lastly, I was able to retrieve a single suspend log of a recent hibernate, but it gave me a generic "sh: echo: I/O error" as the apparent cause of the issue.

---

