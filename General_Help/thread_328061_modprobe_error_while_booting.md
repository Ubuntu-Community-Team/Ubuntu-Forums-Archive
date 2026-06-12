---
title: "modprobe error while booting"
date: 2006-12-30
forum: General Help
---

### Post by flapane on 2006-12-30
I successfully compiled my slim 2.6.15 kernel and my box is reallllly fast comparing to ubuntu prepackaged kernel.
I used stock ubuntu kernel in the last 2months because I had a problem with my new x2 3800+ (powernowk8 not supported by PSB bios structure). However I have a strange issue while booting:
modprobe: FATAL: Could not load /lib/modules/2.6.15.7-nv/modules.dep: No such file or directory

but the file EXISTS, the modules are loaded without problems and everything works wonderfully.
So what does this error mean?

```

Linux a64 2.6.15.7-nv #1 SMP Fri Dec 29 17:17:00 CET 2006 x86_64 GNU/Linux
flapane@a64:~$ lsmod
Module                  Size  Used by
ipv6                  266048  10
ipt_state               2368  1
ip_conntrack           50088  1 ipt_state
nfnetlink               6280  1 ip_conntrack
iptable_filter          3328  1
ip_tables              20288  2 ipt_state,iptable_filter
powernow_k8            10752  1
cpufreq_userspace       7392  0
cpufreq_stats           6148  0
freq_table              4608  2 powernow_k8,cpufreq_stats
cpufreq_powersave       2368  0
cpufreq_ondemand        7784  1
cpufreq_conservative     9000  0
video                  16072  0
container               4288  0
ac                      4680  0
button                  6496  0
vfat                   12864  1
af_packet              19916  2
md_mod                 64056  0
nvidia               5652576  32
sg                     33328  0
hci_usb                13076  6
sk98lin               163816  0
serio_raw               7300  0
pcspkr                  2504  0
floppy                 67528  0
psmouse                36484  0
ide_generic             1792  0 [permanent]
generic                 5764  0 [permanent]
sd_mod                 15936  7
usbhid                 37792  0
thermal                13068  0
processor              22888  2 powernow_k8,thermal
fan                     4424  0
vga16fb                12752  0
vgastate                8896  1 vga16fb
flapane@a64:~$

flapane@a64:~$ dmesg
[    0.000000] Bootdata ok (command line is root=UUID=8d54a918-79ab-44e5-afec-22b399bd1732 ro quiet splash)
[    0.000000] Linux version 2.6.15.7-nv (root@a64) (gcc version 4.0.4 20060630 (prerelease) (Ubuntu 4.0.3-4)) #1 SMP Fri Dec 29 17:17:00 CET 2006
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fee0000 (usable)
[    0.000000]  BIOS-e820: 000000003fee0000 - 000000003fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fee3000 - 000000003fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003fef0000 - 000000003ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] ACPI: RSDP (v000 Nvidia                                ) @ 0x00000000000f8160
[    0.000000] ACPI: RSDT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003fee3040
[    0.000000] ACPI: FADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003fee30c0
[    0.000000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x00000001  LTP 0x00000001) @ 0x000000003fee92c0
[    0.000000] ACPI: MCFG (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003fee9480
[    0.000000] ACPI: MADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003fee9200
[    0.000000] ACPI: DSDT (v001 NVIDIA AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x0000000000000000
[    0.000000] On node 0 totalpages: 256954
[    0.000000]   DMA zone: 2718 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 254236 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages, LIFO batch:0
[    0.000000]   HighMem zone: 0 pages, LIFO batch:0
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:11 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:11 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:a0100000)
[    0.000000] Checking aperture...
[    0.000000] CPU 0: aperture @ f810000000 size 32 MB
[    0.000000] Aperture from northbridge cpu 0 too small (32 MB)
[    0.000000] No AGP bridge found
[    0.000000] SMP: Allowing 3 CPUs, 1 hotplug CPUs
[    0.000000] Built 1 zonelists
[    0.000000] Kernel command line: root=UUID=8d54a918-79ab-44e5-afec-22b399bd1732 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 131072 bytes)
[    0.000000] time.c: Using 3.579545 MHz PM timer.
[    0.000000] time.c: Detected 2565.563 MHz processor.
[   24.157384] Console: colour VGA+ 80x25
[   24.157745] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   24.158241] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   24.164065] Memory: 1022300k/1047424k available (3059k kernel code, 24388k reserved, 1147k data, 184k init)
[   24.223177] Calibrating delay using timer specific routine.. 5134.31 BogoMIPS (lpj=2567155)
[   24.223198] Security Framework v1.0.0 initialized
[   24.223203] Capability LSM initialized
[   24.223216] Mount-cache hash table entries: 256
[   24.223279] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   24.223281] CPU: L2 Cache: 512K (64 bytes/line)
[   24.223287] mtrr: v2.0 (20020519)
[   24.250322] Using local APIC timer interrupts.
[   24.289290] Detected 17.816 MHz APIC timer.
[   24.289355] Booting processor 1/2 APIC 0x1
[   24.300116] Initializing CPU#1
[   24.360624] Calibrating delay using timer specific routine.. 5130.19 BogoMIPS (lpj=2565098)
[   24.360628] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   24.360630] CPU: L2 Cache: 512K (64 bytes/line)
[   24.360687] AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ stepping 01
[   24.360692] CPU 1: Syncing TSC to CPU 0.
[   24.360246] CPU 1: synchronized TSC with CPU 0 (last diff 0 cycles, maxerr 532 cycles)
[   24.360249] Brought up 2 CPUs
[   24.360279] Disabling vsyscall due to use of PM timer
[   24.360280] time.c: Using PM based timekeeping.
[   24.360282] testing NMI watchdog ... OK.
[   24.370345] checking if image is initramfs... it is
[   24.560148] NET: Registered protocol family 16
[   24.560164] ACPI: bus type pci registered
[   24.560396] PCI: Using configuration type 1
[   24.563057] PCI: Using MMCONFIG at e0000000
[   24.563446] ACPI: Subsystem revision 20050902
[   24.571360] ACPI: Interpreter enabled
[   24.571361] ACPI: Using IOAPIC for interrupt routing
[   24.571742] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   24.571744] PCI: Probing PCI hardware (bus 00)
[   24.575668] PCI: Transparent bridge - 0000:00:09.0
[   24.575823] Boot video device is 0000:05:00.0
[   24.575862] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   24.624990] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   24.626466] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   24.626714] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   24.626962] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   24.627216] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   24.627464] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   24.627710] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   24.627959] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   24.628218] ACPI: PCI Interrupt Link [LMAC] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   24.628468] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   24.628714] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   24.628963] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   24.629221] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   24.629470] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   24.629726] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   24.629989] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   24.630246] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   24.630528] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[   24.630807] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   24.631091] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[   24.631371] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[   24.631582] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[   24.631867] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
[   24.632158] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[   24.632444] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
[   24.632726] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[   24.633014] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[   24.633298] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
[   24.633583] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
[   24.633864] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   24.634161] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.
[   24.634454] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[   24.634747] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
[   24.636718] Linux Plug and Play Support v0.97 (c) Adam Belay
[   24.636726] pnp: PnP ACPI init
[   24.640398] pnp: PnP ACPI: found 13 devices
[   24.640482] SCSI subsystem initialized
[   24.640510] usbcore: registered new driver usbfs
[   24.640529] usbcore: registered new driver hub
[   24.640588] PCI: Using ACPI for IRQ routing
[   24.640591] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   24.640635] Bluetooth: Core ver 2.8
[   24.640637] NET: Registered protocol family 31
[   24.640638] Bluetooth: HCI device and connection manager initialized
[   24.640641] Bluetooth: HCI socket layer initialized
[   24.640664] PCI-DMA: Disabling IOMMU.
[   24.640990] pnp: 00:00: ioport range 0x1000-0x107f could not be reserved
[   24.640993] pnp: 00:00: ioport range 0x1080-0x10ff has been reserved
[   24.640995] pnp: 00:00: ioport range 0x1400-0x147f has been reserved
[   24.640997] pnp: 00:00: ioport range 0x1480-0x14ff could not be reserved
[   24.641000] pnp: 00:00: ioport range 0x1800-0x187f has been reserved
[   24.641002] pnp: 00:00: ioport range 0x1880-0x18ff has been reserved
[   24.641146] PCI: Bridge: 0000:00:09.0
[   24.641147]   IO window: c000-cfff
[   24.641150]   MEM window: fde00000-fdefffff
[   24.641152]   PREFETCH window: fdf00000-fdffffff
[   24.641154] PCI: Bridge: 0000:00:0b.0
[   24.641156]   IO window: b000-bfff
[   24.641158]   MEM window: fdd00000-fddfffff
[   24.641160]   PREFETCH window: fdc00000-fdcfffff
[   24.641162] PCI: Bridge: 0000:00:0c.0
[   24.641163]   IO window: a000-afff
[   24.641166]   MEM window: fdb00000-fdbfffff
[   24.641168]   PREFETCH window: fda00000-fdafffff
[   24.641173] PCI: Bridge: 0000:00:0d.0
[   24.641174]   IO window: 9000-9fff
[   24.641176]   MEM window: fd900000-fd9fffff
[   24.641178]   PREFETCH window: fd800000-fd8fffff
[   24.641181] PCI: Bridge: 0000:00:0e.0
[   24.641182]   IO window: 8000-8fff
[   24.641185]   MEM window: fa000000-fcffffff
[   24.641187]   PREFETCH window: d0000000-dfffffff
[   24.641192] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   24.641197] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   24.641201] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   24.641205] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   24.641208] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   24.641370] IA32 emulation $Id: sys_ia32.c,v 1.32 2002/03/24 13:02:28 ak Exp $
[   24.642408] audit: initializing netlink socket (disabled)
[   24.642415] audit(1167491542.348:1): initialized
[   24.642522] VFS: Disk quotas dquot_6.5.1
[   24.642534] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   24.642581] NTFS driver 2.1.25 [Flags: R/O DEBUG].
[   24.642605] Initializing Cryptographic API
[   24.642608] io scheduler noop registered
[   24.642612] io scheduler anticipatory registered
[   24.642617] io scheduler deadline registered
[   24.642628] io scheduler cfq registered
[   25.204973] 0000:00:02.1 EHCI: early BIOS handoff failed (BIOS bug ?)
[   25.205172] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   25.205175] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[   25.205187] assign_interrupt_mode Found MSI capability
[   25.205189] Allocate Port Service[pcie00]
[   25.205211] Allocate Port Service[pcie03]
[   25.205235] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   25.205237] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[   25.205248] assign_interrupt_mode Found MSI capability
[   25.205249] Allocate Port Service[pcie00]
[   25.205267] Allocate Port Service[pcie03]
[   25.205289] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   25.205291] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[   25.205302] assign_interrupt_mode Found MSI capability
[   25.205303] Allocate Port Service[pcie00]
[   25.205323] Allocate Port Service[pcie03]
[   25.205343] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   25.205345] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[   25.205355] assign_interrupt_mode Found MSI capability
[   25.205357] Allocate Port Service[pcie00]
[   25.205374] Allocate Port Service[pcie03]
[   25.215112] Real Time Clock Driver v1.12
[   25.215139] Linux agpgart interface v0.101 (c) Dave Jones
[   25.215214] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   25.217050] serio: i8042 AUX port at 0x60,0x64 irq 12
[   25.217162] serio: i8042 KBD port at 0x60,0x64 irq 1
[   25.217166] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing disabled
[   25.217269] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.217361] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   25.218595] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.218902] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   25.219060] loop: loaded (max 8 devices)
[   25.219082] pktcdvd: v0.2.0a 2004-07-14 Jens Axboe (axboe@suse.de) and petero2@telia.com
[   25.219339] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   25.219343] GSI 16 sharing vector 0xB1 and IRQ 16
[   25.219347] ACPI: PCI Interrupt 0000:01:0a.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 16
[   25.219490] skge 1.3 addr 0xfdefc000 irq 16 chip Yukon-Lite rev 9
[   25.219591] skge eth0: addr 00:01:29:16:27:c6
[   25.219621] tun: Universal TUN/TAP device driver, 1.6
[   25.219623] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[   25.219640] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   25.219642] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   25.219663] NFORCE-CK804: IDE controller at PCI slot 0000:00:06.0
[   25.219681] NFORCE-CK804: chipset revision 162
[   25.219683] NFORCE-CK804: not 100% native mode: will probe irqs later
[   25.219686] NFORCE-CK804: 0000:00:06.0 (rev a2) UDMA133 controller
[   25.219690]     ide0: BM-DMA at 0xe800-0xe807, BIOS settings: hda:DMA, hdb:DMA
[   25.219696]     ide1: BM-DMA at 0xe808-0xe80f, BIOS settings: hdc:DMA, hdd:DMA
[   25.219700] Probing IDE interface ide0...
[   25.738785] Probing IDE interface ide1...
[   26.410623] hdc: Pioneer DVD-ROM ATAPIModel DVD-105S 012, ATAPI CD/DVD-ROM drive
[   27.124372] hdd: _NEC DVD_RW ND-4550A, ATAPI CD/DVD-ROM drive
[   27.175856] ide1 at 0x170-0x177,0x376 on irq 15
[   27.176379] hdc: ATAPI 40X DVD-ROM drive, 512kB Cache, UDMA(33)
[   27.176383] Uniform CD-ROM driver Revision: 3.20
[   27.178872] hdd: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   27.180617] libata version 1.20 loaded.
[   27.180635] sata_nv 0000:00:07.0: version 0.8
[   27.181005] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[   27.181009] GSI 17 sharing vector 0xB9 and IRQ 17
[   27.181012] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] -> GSI 23 (level, low) -> IRQ 17
[   27.181115] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   27.181170] ata1: SATA max UDMA/133 cmd 0x9F0 ctl 0xBF2 bmdma 0xD400 irq 17
[   27.181190] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xB72 bmdma 0xD408 irq 17
[   27.536244] ata1: dev 0 cfg 49:2f00 82:346b 83:7fe9 84:4773 85:3469 86:3c01 87:4763 88:407f
[   27.536247] ata1: dev 0 ATA-7, max UDMA/133, 160836480 sectors: LBA48
[   27.536403] nv_sata: Primary device added
[   27.536405] nv_sata: Primary device removed
[   27.536406] nv_sata: Secondary device added
[   27.536407] nv_sata: Secondary device removed
[   27.536409] ata1: dev 0 configured for UDMA/133
[   27.536411] scsi0 : sata_nv
[   27.891117] ata2: dev 0 cfg 49:2f00 82:346b 83:7fe9 84:4773 85:3469 86:3c01 87:4763 88:407f
[   27.891120] ata2: dev 0 ATA-7, max UDMA/133, 488397168 sectors: LBA48
[   27.891282] nv_sata: Primary device added
[   27.891283] nv_sata: Primary device removed
[   27.891284] nv_sata: Secondary device added
[   27.891285] nv_sata: Secondary device removed
[   27.891287] ata2: dev 0 configured for UDMA/133
[   27.891289] scsi1 : sata_nv
[   27.891355]   Vendor: ATA       Model: HDS728080PLA380   Rev: PF2O
[   27.891361]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   27.891429]   Vendor: ATA       Model: HDT722525DLA380   Rev: V44O
[   27.891434]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   27.891799] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[   27.891803] GSI 18 sharing vector 0xC1 and IRQ 18
[   27.891806] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 22 (level, low) -> IRQ 18
[   27.891906] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   27.891910] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   27.891935] ehci_hcd 0000:00:02.1: debug port 1
[   27.891939] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   27.892011] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[   27.892019] ehci_hcd 0000:00:02.1: irq 18, io mem 0xfeb00000
[   27.892025] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   27.892097] hub 1-0:1.0: USB hub found
[   27.892102] hub 1-0:1.0: 10 ports detected
[   27.993029] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   27.993337] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[   27.993340] GSI 19 sharing vector 0xC9 and IRQ 19
[   27.993344] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 21 (level, low) -> IRQ 19
[   27.993437] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   27.993440] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   27.993513] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[   27.993521] ohci_hcd 0000:00:02.0: irq 19, io mem 0xfe02f000
[   28.047045] hub 2-0:1.0: USB hub found
[   28.047051] hub 2-0:1.0: 10 ports detected
[   28.147969] USB Universal Host Controller Interface driver v2.3
[   28.302815] usbcore: registered new driver usblp
[   28.302817] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   28.302819] Initializing USB Mass Storage driver...
[   28.563699] usb 2-3: new low speed USB device using ohci_hcd and address 2
[   29.027629] usb 2-6: new full speed USB device using ohci_hcd and address 3
[   29.384638] usbcore: registered new driver usb-storage
[   29.384639] USB Mass Storage support registered.
[   29.384673] mice: PS/2 mouse device common for all mice
[   29.384676] I2O subsystem v1.288
[   29.384681] i2o: max drivers = 8
[   29.385228] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   29.385249] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x1c40
[   29.409023] input: AT Translated Set 2 keyboard as /class/input/input0
[   29.865392]  : Chip was made by neither Winbond nor Asus?
[   29.865394] hdaps: supported laptop not found!
[   29.865395] hdaps: driver init failed (ret=-6)!
[   29.888365] it87: Found IT8712F chip at 0x290, revision 7
[   30.934965] i2c_adapter i2c-1: LM83 detection failed at 0x4e.
[   31.220891] Advanced Linux Sound Architecture Driver Version 1.0.10rc3 (Mon Nov 07 13:30:21 2005 UTC).
[   31.271905] request_module: runaway loop modprobe net-pf-1
[   31.285610] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 20
[   31.285615] GSI 20 sharing vector 0xD1 and IRQ 20
[   31.285619] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCJ] -> GSI 20 (level, low) -> IRQ 20
[   31.285809] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   31.597733] intel8x0_measure_ac97_clock: measured 50782 usecs
[   31.597735] intel8x0: clocking to 46875
[   31.598141] ALSA device list:
[   31.598142]   #0: Dummy 1
[   31.598144]   #1: Virtual MIDI Card 1
[   31.598145]   #2: NVidia CK804 with ALC850 at 0xfe02d000, irq 20
[   31.598184] NET: Registered protocol family 2
[   31.606768] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   31.606941] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   31.607686] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   31.608055] TCP: Hash tables configured (established 131072 bind 65536)
[   31.608057] TCP reno registered
[   31.608116] TCP bic registered
[   31.608122] NET: Registered protocol family 1
[   31.608128] Bluetooth: L2CAP ver 2.8
[   31.608129] Bluetooth: L2CAP socket layer initialized
[   31.608131] Bluetooth: SCO (Voice Link) ver 0.5
[   31.608132] Bluetooth: SCO socket layer initialized
[   31.608146] Bluetooth: RFCOMM socket layer initialized
[   31.608155] Bluetooth: RFCOMM TTY layer initialized
[   31.608156] Bluetooth: RFCOMM ver 1.6
[   31.608157] NET: Registered protocol family 8
[   31.608159] NET: Registered protocol family 20
[   31.608173] ieee80211: 802.11 data/management/control stack, git-1.1.7
[   31.608174] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   31.608176] ieee80211_crypt: registered algorithm 'NULL'
[   31.608178] ieee80211_crypt: registered algorithm 'WEP'
[   31.608252] ACPI wakeup devices:
[   31.608254] HUB0 XVR0 XVR1 XVR2 XVR3 USB0 USB2 MMAC MMCI UAR1 PS2M PS2K
[   31.608258] ACPI: (supports S0 S1 S3 S4 S5)
[   31.608395] Freeing unused kernel memory: 184k freed
[   31.624218] vga16fb: initializing
[   31.624221] vga16fb: mapped to 0xffff8100000a0000
[   31.624249] fb0: VGA16 VGA frame buffer device
[   31.636808] ACPI: Fan [FAN] (on)
[   31.639613] ACPI: Thermal Zone [THRM] (22 C)
[   31.920708] usbcore: registered new driver hiddev
[   31.930604] SCSI device sda: 160836480 512-byte hdwr sectors (82348 MB)
[   31.930618] SCSI device sda: drive cache: write back
[   31.930660] SCSI device sda: 160836480 512-byte hdwr sectors (82348 MB)
[   31.930667] SCSI device sda: drive cache: write back
[   31.930671]  sda:<6>input: Microsoft Microsoft Wireless Optical Mouse 1.0A as /class/input/input1
[   31.946672] input: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse 1.0A] on usb-0000:00:02.0-3
[   31.946681] usbcore: registered new driver usbhid
[   31.946683] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   31.956887]  sda1 sda2 < sda5 > sda3 sda4
[   31.969723] sd 0:0:0:0: Attached scsi disk sda
[   31.969771] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[   31.969883] SCSI device sdb: drive cache: write back
[   31.969911] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[   31.969925] SCSI device sdb: drive cache: write back
[   31.969926]  sdb: sdb1
[   31.984203] sd 1:0:0:0: Attached scsi disk sdb
[   32.305985] Probing IDE interface ide0...
[   32.849885] kjournald starting.  Commit interval 5 seconds
[   32.849900] EXT3-fs: mounted filesystem with ordered data mode.
[   41.520777] Floppy drive(s): fd0 is 1.44M
[   41.524035] input: PC Speaker as /class/input/input2
[   41.536976] FDC 0 is a post-1991 82077
[   41.563061] Bluetooth: HCI USB driver ver 2.9
[   41.563095] usbcore: registered new driver hci_usb
[   41.589435] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   41.589456] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   41.822462] input: ImPS/2 Logitech Wheel Mouse as /class/input/input3
[   42.180751] skge eth0: enabling interface
[   42.246936] nvidia: module license 'NVIDIA' taints kernel.
[   42.500147] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 16
[   42.500155] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   42.500255] NVRM: loading NVIDIA Linux x86_64 Kernel Module  1.0-9629  Wed Nov  1 19:27:33 PST 2006
[   42.623080] Adding 939792k swap on /dev/disk/by-uuid/da16d779-f525-4060-b2ec-8a8e2789a108.  Priority:-1 extents:1 across:939792k
[   42.720407] EXT3 FS on sda3, internal journal
[   42.831265] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   42.831269] md: bitmap version 4.39
[   43.273136] NET: Registered protocol family 17
[   43.277757] NTFS volume version 3.1.
[   43.334652] NTFS volume version 3.1.
[   44.447108] skge eth0: Link is up at 10 Mbps, half duplex, flow control none
[   46.352384] ACPI: Power Button (FF) [PWRF]
[   46.352393] ACPI: Power Button (CM) [PWRB]
[   46.372881] Using specific hotkey driver
[   46.523150] powernow-k8: Found 2 AMD Athlon 64 / Opteron processors (version 1.50.4)
[   46.523169] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x8 (1350 mV)
[   46.523172] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12 (1100 mV)
[   46.523176] cpu_init done, current fid 0xa, vid 0x8
[   51.096261] ip_tables: (C) 2000-2002 Netfilter core team
[   51.149081] Netfilter messages via NETLINK v0.30.
[   51.150793] ip_conntrack version 2.4 (4091 buckets, 32728 max) - 312 bytes per conntrack
[   59.699030] NET: Registered protocol family 10
[   59.699105] lo: Disabled Privacy Extensions
[   59.699193] IPv6 over IPv4 tunneling driver
[   66.570568] eth0: no IPv6 routers present
flapane@a64:~$                                                          

```

---

### Post by flapane on 2006-12-31
bump

---

