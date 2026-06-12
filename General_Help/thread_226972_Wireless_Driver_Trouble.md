---
title: "Wireless Driver Trouble"
date: 2006-08-01
forum: General Help
---

### Post by Cath0de on 2006-08-01
K, so I've been trying to get my wireless internet working for the last few days. When I found out my wireless network wasn't been detected, I found out my wireless card wasn't been detected, then I found out it was being detected but it had no installed drivers, but then when I tried to install the necesarry ipw2100 drivers, I came across this:

```
root@ubuntulaptop1:/home/cath0de# modprobe ipw2100
WARNING: Could not open '/lib/modules/2.6.15-23-386/kernel/net/ieee80211/ieee80211_crypt.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-23-386/kernel/net/ieee80211/ieee80211.ko': No such file or directory
FATAL: Error inserting ipw2100 (/lib/modules/2.6.15-23-386/kernel/drivers/net/wireless/ipw2100.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

Anyone care to untangle this mess?

If you want more background info, look at this thread: [http://ubuntuforums.org/showthread.php?t=224411](http://ubuntuforums.org/showthread.php?t=224411)

---

### Post by Cath0de on 2006-08-01
Ok, I installed the kernel source headers, make and make installed ieee80211, but when I modprobe ipw2100, I still get this message:

```
root@ubuntulaptop1:/home/cath0de/Desktop/ieee80211-1.1.14# modprobe ipw2100
FATAL: Error inserting ipw2100 (/lib/modules/2.6.15-23-386/kernel/drivers/net/wireless/ipw2100.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

The output of dmesg is:
```
root@ubuntulaptop1:/home/cath0de/Desktop/ieee80211-1.1.14# dmesg
[4294667.296000] Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[4294667.296000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000000f6e0000 (usable)
[4294667.296000]  BIOS-e820: 000000000f6e0000 - 000000000f6f7000 (ACPI data)
[4294667.296000]  BIOS-e820: 000000000f6f7000 - 000000000f6f9000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 000000000f700000 - 0000000010000000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[4294667.296000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 246MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 63200
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 59104 pages, LIFO batch:15
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI present.
[4294667.296000] ACPI: RSDP (v002 IBM                                   ) @ 0x000f7010
[4294667.296000] ACPI: XSDT (v001 IBM    TP-1U    0x00001140  LTP 0x00000000) @ 0x0f6ea5bf
[4294667.296000] ACPI: FADT (v003 IBM    TP-1U    0x00001140 IBM  0x00000001) @ 0x0f6ea700
[4294667.296000] ACPI: SSDT (v001 IBM    TP-1U    0x00001140 MSFT 0x0100000e) @ 0x0f6ea8b4
[4294667.296000] ACPI: ECDT (v001 IBM    TP-1U    0x00001140 IBM  0x00000001) @ 0x0f6f6e68
[4294667.296000] ACPI: TCPA (v001 IBM    TP-1U    0x00001140 PTL  0x00000001) @ 0x0f6f6eba
[4294667.296000] ACPI: MADT (v001 IBM    TP-1U    0x00001140 IBM  0x00000001) @ 0x0f6f6eec
[4294667.296000] ACPI: BOOT (v001 IBM    TP-1U    0x00001140  LTP 0x00000001) @ 0x0f6f6fd8
[4294667.296000] ACPI: DSDT (v001 IBM    TP-1U    0x00001140 MSFT 0x0100000e) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x1008
[4294667.296000] ACPI: Local APIC address 0xfee00000
[4294667.296000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[4294667.296000] Processor #0 6:9 APIC version 20
[4294667.296000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[4294667.296000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[4294667.296000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[4294667.296000] ACPI: IRQ0 used by override.
[4294667.296000] ACPI: IRQ2 used by override.
[4294667.296000] ACPI: IRQ9 used by override.
[4294667.296000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[4294667.296000] Using ACPI (MADT) for SMP configuration information
[4294667.296000] Allocating PCI resources starting at 20000000 (gap: 10000000:eec00000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] mapped IOAPIC to ffffc000 (fec00000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[4294667.296000] Detected 1196.138 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294668.274000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294668.275000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[4294668.282000] Memory: 240052k/252800k available (1976k kernel code, 12080k reserved, 606k data, 288k init, 0k highmem)
[4294668.282000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294668.342000] Calibrating delay using timer specific routine.. 2393.45 BogoMIPS (lpj=1196729)
[4294668.342000] Security Framework v1.0.0 initialized
[4294668.342000] SELinux:  Disabled at boot.
[4294668.342000] Mount-cache hash table entries: 512
[4294668.342000] CPU: After generic identify, caps: a7e9fbbf 00000000 00000000 00000000 00000180 00000000 00000000
[4294668.342000] CPU: After vendor identify, caps: a7e9fbbf 00000000 00000000 00000000 00000180 00000000 00000000
[4294668.342000] CPU: L1 I cache: 32K, L1 D cache: 32K
[4294668.342000] CPU: L2 cache: 1024K
[4294668.342000] CPU: After all inits, caps: a7e9fbbf 00000000 00000000 00000040 00000180 00000000 00000000
[4294668.342000] mtrr: v2.0 (20020519)
[4294668.342000] CPU: Intel(R) Pentium(R) M processor 1200MHz stepping 05
[4294668.342000] Enabling fast FPU save and restore... done.
[4294668.342000] Enabling unmasked SIMD FPU exception support... done.
[4294668.342000] Checking 'hlt' instruction... OK.
[4294668.346000] checking if image is initramfs... it is
[4294669.578000] Freeing initrd memory: 6608k freed
[4294669.585000] ACPI: Looking for DSDT ... not found!
[4294669.602000] ENABLING IO-APIC IRQs
[4294669.602000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[4294669.713000] NET: Registered protocol family 16
[4294669.713000] EISA bus registered
[4294669.713000] ACPI: bus type pci registered
[4294669.713000] PCI: PCI BIOS revision 2.10 entry at 0xfd8c8, last bus=5
[4294669.713000] PCI: Using configuration type 1
[4294669.713000] ACPI: Subsystem revision 20051216
[4294669.715000] ACPI: Found ECDT
[4294669.847000] ACPI: Interpreter enabled
[4294669.847000] ACPI: Using IOAPIC for interrupt routing
[4294669.848000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[4294669.848000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[4294669.849000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[4294669.850000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[4294669.851000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[4294669.851000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
[4294669.852000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[4294669.853000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[4294669.853000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294669.853000] PCI: Probing PCI hardware (bus 00)
[4294669.859000] Boot video device is 0000:00:02.0
[4294669.859000] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[4294669.859000] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[4294669.859000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[4294669.860000] PCI: Transparent bridge - 0000:00:1e.0
[4294669.860000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294669.864000] ACPI: Embedded Controller [EC] (gpe 28) interrupt mode.
[4294669.864000] ACPI: Power Resource [PUBS] (on)
[4294669.866000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[4294669.869000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294669.869000] pnp: PnP ACPI init
[4294669.874000] pnp: PnP ACPI: found 10 devices
[4294669.874000] PnPBIOS: Disabled by ACPI PNP
[4294669.874000] PCI: Using ACPI for IRQ routing
[4294669.874000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294669.883000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[4294669.883000] PCI: Bus 3, cardbus bridge: 0000:02:00.0
[4294669.883000]   IO window: 00003000-000030ff
[4294669.883000]   IO window: 00003400-000034ff
[4294669.883000]   PREFETCH window: f0000000-f1ffffff
[4294669.883000]   MEM window: d2000000-d3ffffff
[4294669.883000] PCI: Bridge: 0000:00:1e.0
[4294669.883000]   IO window: 3000-7fff
[4294669.883000]   MEM window: d0200000-dfffffff
[4294669.883000]   PREFETCH window: f0000000-f7ffffff
[4294669.883000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[4294669.883000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294669.883000] Simple Boot Flag at 0x35 set to 0x1
[4294669.884000] audit: initializing netlink socket (disabled)
[4294669.884000] audit(1154445614.883:1): initialized
[4294669.884000] VFS: Disk quotas dquot_6.5.1
[4294669.884000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294669.884000] Initializing Cryptographic API
[4294669.884000] io scheduler noop registered
[4294669.884000] io scheduler anticipatory registered
[4294669.884000] io scheduler deadline registered
[4294669.884000] io scheduler cfq registered
[4294669.884000] isapnp: Scanning for PnP cards...
[4294670.240000] isapnp: No Plug & Play device found
[4294670.256000] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[4294670.262000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294670.262000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294670.262000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294670.265000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> GSI 17 (level, low) -> IRQ 177
[4294670.265000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[4294670.265000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294670.265000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294670.265000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294670.265000] mice: PS/2 mouse device common for all mice
[4294670.266000] EISA: Probing bus 0 at eisa.0
[4294670.266000] Cannot allocate resource for EISA slot 1
[4294670.266000] Cannot allocate resource for EISA slot 2
[4294670.266000] Cannot allocate resource for EISA slot 3
[4294670.266000] Cannot allocate resource for EISA slot 4
[4294670.266000] Cannot allocate resource for EISA slot 5
[4294670.266000] Cannot allocate resource for EISA slot 6
[4294670.266000] Cannot allocate resource for EISA slot 7
[4294670.266000] EISA: Detected 0 cards.
[4294670.266000] NET: Registered protocol family 2
[4294670.275000] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[4294670.275000] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[4294670.275000] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[4294670.275000] TCP: Hash tables configured (established 8192 bind 8192)
[4294670.275000] TCP reno registered
[4294670.275000] TCP bic registered
[4294670.275000] NET: Registered protocol family 1
[4294670.275000] NET: Registered protocol family 8
[4294670.275000] NET: Registered protocol family 20
[4294670.275000] Using IPI Shortcut mode
[4294670.275000] ACPI wakeup devices:
[4294670.275000]  LID SLPB PCI0 PCI1 DOCK USB0 USB1 USB2 AC9M
[4294670.275000] ACPI: (supports S0 S3 S4 S5)
[4294670.275000] Freeing unused kernel memory: 288k freed
[4294670.325000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294670.333000] vga16fb: initializing
[4294670.333000] vga16fb: mapped to 0xc00a0000
[4294670.444000] Console: switching to colour frame buffer device 80x25
[4294670.444000] fb0: VGA16 VGA frame buffer device
[4294671.529000] Capability LSM initialized
[4294671.568000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[4294671.568000] ACPI: Processor [CPU] (supports 8 throttling states)
[4294671.570000] ACPI: Thermal Zone [THM0] (31 C)
[4294671.996000] ICH4: IDE controller at PCI slot 0000:00:1f.1
[4294671.996000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[4294671.996000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 185
[4294671.996000] ICH4: chipset revision 1
[4294671.996000] ICH4: not 100% native mode: will probe irqs later
[4294671.996000]     ide0: BM-DMA at 0x1810-0x1817, BIOS settings: hda:DMA, hdb:pio
[4294671.996000]     ide1: BM-DMA at 0x1818-0x181f, BIOS settings: hdc:pio, hdd:pio
[4294671.996000] Probing IDE interface ide0...
[4294672.260000] hda: HITACHI_DK13FA-40B, ATA DISK drive
[4294672.872000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294672.971000] Probing IDE interface ide1...
[4294673.497000] hda: max request size: 128KiB
[4294673.497000] hda: 78140160 sectors (40007 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[4294673.497000] hda: cache flushes supported
[4294673.497000]  hda: hda1 hda2 < hda5 >
[4294673.863000] usbcore: registered new driver usbfs
[4294673.863000] usbcore: registered new driver hub
[4294673.915000] USB Universal Host Controller Interface driver v2.3
[4294673.915000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294673.915000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294673.915000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[4294673.915000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294673.915000] uhci_hcd 0000:00:1d.0: irq 169, io base 0x00001820
[4294673.916000] hub 1-0:1.0: USB hub found
[4294673.916000] hub 1-0:1.0: 2 ports detected
[4294674.017000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 193
[4294674.017000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294674.017000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[4294674.017000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294674.017000] uhci_hcd 0000:00:1d.1: irq 193, io base 0x00001840
[4294674.017000] hub 2-0:1.0: USB hub found
[4294674.017000] hub 2-0:1.0: 2 ports detected
[4294674.118000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 185
[4294674.118000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294674.118000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[4294674.118000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294674.118000] uhci_hcd 0000:00:1d.2: irq 185, io base 0x00001860
[4294674.118000] hub 3-0:1.0: USB hub found
[4294674.118000] hub 3-0:1.0: 2 ports detected
[4294674.220000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 201
[4294674.220000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294674.220000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[4294674.221000] ehci_hcd 0000:00:1d.7: debug port 1
[4294674.221000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[4294674.221000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[4294674.221000] ehci_hcd 0000:00:1d.7: irq 201, io mem 0xd0100000
[4294674.225000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[4294674.225000] hub 4-0:1.0: USB hub found
[4294674.225000] hub 4-0:1.0: 6 ports detected
[4294674.344000] Probing IDE interface ide1...
[4294674.977000] Attempting manual resume
[4294675.000000] EXT3-fs: mounted filesystem with ordered data mode.
[4294675.014000] kjournald starting.  Commit interval 5 seconds
[4294692.943000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294692.953000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294692.992000] Linux agpgart interface v0.101 (c) Dave Jones
[4294693.012000] hw_random hardware driver 1.0.0 loaded
[4294693.015000] agpgart: Detected an Intel 855 Chipset.
[4294693.015000] agpgart: Detected 8060K stolen memory.
[4294693.024000] agpgart: AGP aperture is 128M @ 0xe0000000
[4294693.108000] input: PC Speaker as /class/input/input1
[4294693.393000] Real Time Clock Driver v1.12
[4294693.628000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 177
[4294693.628000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[4294693.689000] sdhci: Secure Digital Host Controller Interface driver, 0.10
[4294693.689000] sdhci: Copyright(c) Pierre Ossman
[4294693.729000] Intel(R) PRO/1000 Network Driver - version 7.0.33-k2
[4294693.729000] Copyright (c) 1999-2005 Intel Corporation.
[4294693.866000] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[4294693.883000] input: TPPS/2 IBM TrackPoint as /class/input/input2
[4294693.925000] ipw2100: Unknown symbol ieee80211_wx_get_encodeext
[4294693.926000] ipw2100: Unknown symbol ieee80211_wx_set_encode
[4294693.926000] ipw2100: Unknown symbol ieee80211_wx_get_encode
[4294693.926000] ipw2100: Unknown symbol ieee80211_txb_free
[4294693.926000] ipw2100: Unknown symbol ieee80211_wx_set_encodeext
[4294693.926000] ipw2100: Unknown symbol ieee80211_wx_get_scan
[4294693.927000] ipw2100: Unknown symbol ieee80211_set_geo
[4294693.927000] ipw2100: Unknown symbol ieee80211_rx
[4294693.927000] ipw2100: Unknown symbol ieee80211_rx_mgt
[4294693.928000] ipw2100: Unknown symbol free_ieee80211
[4294693.928000] ipw2100: Unknown symbol alloc_ieee80211
[4294694.324000] ts: Compaq touchscreen protocol output
[4294694.390000] irda_init()
[4294694.390000] NET: Registered protocol family 23
[4294694.413000] **** SET: Misaligned resource pointer: cb91ea42 Type 00 Len 42
[4294694.413000] **** SET: Misaligned resource pointer: cb91eac6 Type 07 Len 0
[4294694.414000] pnp: Device 00:08 activated.
[4294694.414000] nsc_ircc_pnp_probe() : Found cfg_base 0x000 ; firbase 0x2F8 ; irq 3 ; dma 1.
[4294694.414000] nsc-ircc, Found chip at base=0x000
[4294694.414000] nsc-ircc, driver loaded (Dag Brattli)
[4294694.414000] IrDA: Registered device irda0
[4294694.414000] nsc-ircc, Found dongle: No dongle connected
[4294694.414000] nsc_ircc_init_dongle_interface(), No dongle connected
[4294694.414000] nsc-ircc, Found chip at base=0x164e
[4294694.414000] nsc-ircc, driver loaded (Dag Brattli)
[4294694.414000] nsc_ircc_open(), can't get iobase of 0x2f8
[4294694.440000] intel8x0_measure_ac97_clock: measured 50461 usecs
[4294694.440000] intel8x0: clocking to 48000
[4294694.445000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294694.445000] Yenta: CardBus bridge found at 0000:02:00.0 [1014:0555]
[4294694.567000] Yenta: ISA IRQ mask 0x04b0, PCI irq 169
[4294694.567000] Socket status: 30000006
[4294694.567000] Yenta: Raising subordinate bus# of parent bus (#02) from #05 to #06
[4294694.567000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x7fff
[4294694.567000] cs: IO port probe 0x3000-0x7fff: clean.
[4294694.569000] pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xdfffffff
[4294694.569000] pcmcia: parent PCI bridge Memory window: 0xf0000000 - 0xf7ffffff
[4294694.590000] ACPI: PCI Interrupt 0000:02:00.1[B] -> GSI 17 (level, low) -> IRQ 177
[4294694.621000] Unable to handle kernel NULL pointer dereference at virtual address 00000004
[4294694.621000]  printing eip:
[4294694.621000] c013112f
[4294694.621000] *pde = 00000000
[4294694.621000] Oops: 0002 [#1]
[4294694.621000] PREEMPT
[4294694.621000] Modules linked in: irtty_sir sir_dev nsc_ircc irda crc_ccitt tsdev e1000 sdhci mmc_core yenta_socket snd_intel8x0 snd_ac97_codec snd_ac97_bus rsrc_nonstatic snd_pcm_oss snd_mixer_oss pcmcia_core snd_pcm snd_timer snd soundcore psmouse snd_page_alloc serio_raw rtc pcspkr intel_agp hw_random agpgart shpchp pci_hotplug evdev ext3 jbd ide_generic ehci_hcd uhci_hcd usbcore ide_disk piix generic thermal processor fan capability commoncap vga16fb vgastate fbcon tileblit font bitblit softcursor
[4294694.621000] CPU:    0
[4294694.621000] EIP:    0060:[<c013112f>]    Not tainted VLI
[4294694.621000] EFLAGS: 00010002   (2.6.15-23-386)
[4294694.621000] EIP is at finish_wait+0x2f/0x70
[4294694.621000] eax: ca14e000   ebx: 00000286   ecx: 00000000   edx: 00000000
[4294694.621000] esi: ca14ffd8   edi: ca14ffcc   ebp: 00000000   esp: ca14ffbc
[4294694.621000] ds: 007b   es: 007b   ss: 0068
[4294694.621000] Process kIrDAd (pid: 3008, threadinfo=ca14e000 task=cf335030)
[4294694.621000] Stack: ca14e000 00000000 00000000 d028a840 00000000 cf335030 c0118940 00000000
[4294694.621000]        00000000 d028a790 00000000 c0101385 ca013f98 00000000 00000000 00000000
[4294694.621000]        00000000
[4294694.621000] Call Trace:
[4294694.621000]  [<d028a840>] irda_thread+0xb0/0xf0 [sir_dev]
[4294694.621000]  [<c0118940>] default_wake_function+0x0/0x20
[4294694.621000]  [<d028a790>] irda_thread+0x0/0xf0 [sir_dev]
[4294694.621000]  [<c0101385>] kernel_thread_helper+0x5/0x10
[4294694.621000] Code: d7 b8 00 e0 ff ff 21 e0 8b 00 c7 00 00 00 00 00 8d 72 0c 3b 72 0c 74 34 9c 5b fa b8 00 e0 ff ff 21 e0 ff 40 14 8b 4f 0c 8b 56 04 <89> 51 04 89 0a 89 77 0c 89 76 04 53 9d ff 48 14 8b 40 08 a8 08
[4294694.621000]  <6>note: kIrDAd[3008] exited with preempt_count 1
[4294694.640000] sdhci: ============== REGISTER DUMP ==============
[4294694.640000] sdhci: Sys addr: 0x00000000 | Version:  0x00000200
[4294694.640000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[4294694.640000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[4294694.640000] sdhci: Present:  0x01f20000 | Host ctl: 0x00000000
[4294694.640000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[4294694.640000] sdhci: Walk up:  0x00000000 | Clock:    0x00000000
[4294694.640000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[4294694.640000] sdhci: Int enab: 0xe1ff00cf | Sig enab: 0xe1ff00cf
[4294694.640000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[4294694.640000] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[4294694.640000] sdhci: ===========================================
[4294694.690000] mmc0: SDHCI at 0xd0221000 irq 177 DMA
[4294694.691000] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 20 (level, low) -> IRQ 209
[4294695.014000] e1000: 0000:02:01.0: e1000_probe: (PCI:33MHz:32-bit) 00:0a:e4:24:1e:ea
[4294695.083000] cs: IO port probe 0x100-0x4ff: excluding 0x170-0x177 0x370-0x377 0x4d0-0x4d7
[4294695.084000] cs: IO port probe 0xc00-0xcf7: clean.
[4294695.085000] cs: IO port probe 0xa00-0xaff: clean.
[4294695.179000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[4294695.546000] lp: driver loaded but no devices found
[4294695.643000] Adding 722884k swap on /dev/hda5.  Priority:-1 extents:1 across:722884k
[4294695.759000] EXT3 FS on hda1, internal journal
[4294695.968000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294695.968000] md: bitmap version 4.39
[4294696.832000] NET: Registered protocol family 17
[4294696.911000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294701.423000] ACPI: AC Adapter [AC] (on-line)
[4294701.435000] ACPI: Battery Slot [BAT0] (battery present)
[4294701.641000] ACPI: Power Button (FF) [PWRF]
[4294701.641000] ACPI: Lid Switch [LID]
[4294701.641000] ACPI: Sleep Button (CM) [SLPB]
[4294701.762000] ibm_acpi: IBM ThinkPad ACPI Extras v0.12a
[4294701.762000] ibm_acpi: http://ibm-acpi.sf.net/
[4294701.766000] ibm_acpi: dock device not present
[4294701.766000] ibm_acpi: bay device not present
[4294701.789000] pcc_acpi: loading...
[4294701.921000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[4294709.761000] ppdev: user-space parallel port driver
[4294711.449000] [drm] Initialized drm 1.0.1 20051102
[4294711.455000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294711.456000] [drm] Initialized i915 1.4.0 20060119 on minor 0
[4294711.456000] [drm] Initialized i915 1.4.0 20060119 on minor 1
[4294714.741000] IBM machine detected. Enabling interrupts during APM calls.
[4294714.742000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294714.742000] apm: overridden by ACPI.
[4294715.359000] Non-volatile memory driver v1.2
[4294715.408000] input: /usr/sbin/thinkpad-keys as /class/input/input3
[4294716.226000] Bluetooth: Core ver 2.8
[4294716.226000] NET: Registered protocol family 31
[4294716.226000] Bluetooth: HCI device and connection manager initialized
[4294716.226000] Bluetooth: HCI socket layer initialized
[4294716.392000] Bluetooth: L2CAP ver 2.8
[4294716.392000] Bluetooth: L2CAP socket layer initialized
[4294716.397000] Bluetooth: RFCOMM socket layer initialized
[4294716.397000] Bluetooth: RFCOMM TTY layer initialized
[4294716.397000] Bluetooth: RFCOMM ver 1.7
[4294735.361000] NET: Registered protocol family 10
[4294735.361000] lo: Disabled Privacy Extensions
[4294735.361000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[4294735.361000] IPv6 over IPv4 tunneling driver
[4296091.808000] e1000: eth0: e1000_watchdog_task: NIC Link is Up 100 Mbps Full Duplex
[4296091.809000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[4296111.728000] eth0: no IPv6 routers present
[4296463.430000] ipw2100: Unknown symbol ieee80211_wx_get_encodeext
[4296463.431000] ipw2100: Unknown symbol ieee80211_wx_set_encode
[4296463.431000] ipw2100: Unknown symbol ieee80211_wx_get_encode
[4296463.431000] ipw2100: Unknown symbol ieee80211_txb_free
[4296463.432000] ipw2100: Unknown symbol ieee80211_wx_set_encodeext
[4296463.432000] ipw2100: Unknown symbol ieee80211_wx_get_scan
[4296463.433000] ipw2100: Unknown symbol ieee80211_set_geo
[4296463.433000] ipw2100: Unknown symbol ieee80211_rx
[4296463.434000] ipw2100: Unknown symbol ieee80211_rx_mgt
[4296463.434000] ipw2100: Unknown symbol free_ieee80211
[4296463.435000] ipw2100: Unknown symbol alloc_ieee80211
[4296736.850000] ieee80211_crypt: registered algorithm 'NULL'
[4296736.915000] ieee80211: 802.11 data/management/control stack, 1.1.14
[4296736.915000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[4296736.941000] ipw2100: disagrees about version of symbol ieee80211_wx_get_encodeext
[4296736.941000] ipw2100: Unknown symbol ieee80211_wx_get_encodeext
[4296736.942000] ipw2100: disagrees about version of symbol ieee80211_wx_set_encode
[4296736.942000] ipw2100: Unknown symbol ieee80211_wx_set_encode
[4296736.942000] ipw2100: disagrees about version of symbol ieee80211_wx_get_encode
[4296736.943000] ipw2100: Unknown symbol ieee80211_wx_get_encode
[4296736.943000] ipw2100: disagrees about version of symbol ieee80211_txb_free
[4296736.943000] ipw2100: Unknown symbol ieee80211_txb_free
[4296736.944000] ipw2100: disagrees about version of symbol ieee80211_wx_set_encodeext
[4296736.944000] ipw2100: Unknown symbol ieee80211_wx_set_encodeext
[4296736.944000] ipw2100: disagrees about version of symbol ieee80211_wx_get_scan
[4296736.945000] ipw2100: Unknown symbol ieee80211_wx_get_scan
[4296736.945000] ipw2100: disagrees about version of symbol ieee80211_set_geo
[4296736.946000] ipw2100: Unknown symbol ieee80211_set_geo
[4296736.946000] ipw2100: disagrees about version of symbol ieee80211_rx
[4296736.946000] ipw2100: Unknown symbol ieee80211_rx
[4296736.947000] ipw2100: disagrees about version of symbol ieee80211_rx_mgt
[4296736.948000] ipw2100: Unknown symbol ieee80211_rx_mgt
[4296736.948000] ipw2100: disagrees about version of symbol free_ieee80211
[4296736.948000] ipw2100: Unknown symbol free_ieee80211
[4296736.949000] ipw2100: disagrees about version of symbol alloc_ieee80211
[4296736.949000] ipw2100: Unknown symbol alloc_ieee80211

```

Sorry, long, but I didn't want to miss anything.

---

### Post by Cath0de on 2006-08-01
A little sleuthing tracked this down:
[http://sourceforge.net/mailarchive/forum.php?thread_id=5469436&forum_id=38938](http://sourceforge.net/mailarchive/forum.php?thread_id=5469436&forum_id=38938)

Can anyone tell me how to apply the patch, if the patch is relevant for this kernel (since that is dated 2 years ago)?

---

### Post by Cath0de on 2006-08-01
bump, I think that patch is a really simple fix, I'm just relatively new to linux, so I don't know how to do it, so any help at all would be appreciated.

---

### Post by Cath0de on 2006-08-01
bump, new title

---

