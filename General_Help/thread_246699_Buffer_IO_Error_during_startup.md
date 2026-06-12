---
title: "Buffer I/O Error during startup"
date: 2006-08-29
forum: General Help
---

### Post by chrisccoulson on 2006-08-29
I've noticed that when I start up my machine, I get several 'Buffer I/O Error on device sd**, logical block ****' messages

The contents of dmesg are:

```
[    0.000000] Bootdata ok (command line is root=/dev/mapper/nvidia_dgcadeeg3 ro quiet)
[    0.000000] Linux version 2.6.15-26-amd64-k8 (buildd@king) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Thu Aug 3 03:11:38 UTC 2006
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d000 (usable)
[    0.000000]  BIOS-e820: 000000000009d000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fff0000 (usable)
[    0.000000]  BIOS-e820: 000000007fff0000 - 000000007fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff3000 - 0000000080000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] ACPI: RSDP (v000 Nvidia                                ) @ 0x00000000000f7560
[    0.000000] ACPI: RSDT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000007fff3040
[    0.000000] ACPI: FADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000007fff30c0
[    0.000000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x00000001  LTP 0x00000001) @ 0x000000007fff9880
[    0.000000] ACPI: MCFG (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000007fff99c0
[    0.000000] ACPI: MADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000007fff97c0
[    0.000000] ACPI: DSDT (v001 NVIDIA AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x0000000000000000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] Number of nodes 1
[    0.000000] Node 0 MemBase 0000000000000000 Limit 000000007fff0000
[    0.000000] Using 63 for the hash shift.
[    0.000000] Using node hash shift of 63
[    0.000000] Bootmem setup node 0 0000000000000000-000000007fff0000
[    0.000000] On node 0 totalpages: 516081
[    0.000000]   DMA zone: 3016 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 513065 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages, LIFO batch:0
[    0.000000]   HighMem zone: 0 pages, LIFO batch:0
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:15 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] Checking aperture...
[    0.000000] CPU 0: aperture @ e26c000000 size 32 MB
[    0.000000] Aperture from northbridge cpu 0 too small (32 MB)
[    0.000000] No AGP bridge found
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] Built 1 zonelists
[    0.000000] Kernel command line: root=/dev/mapper/nvidia_dgcadeeg3 ro quiet
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 131072 bytes)
[    0.000000] time.c: Using 3.579545 MHz PM timer.
[    0.000000] time.c: Detected 2211.382 MHz processor.
[   23.963338] Console: colour VGA+ 80x25
[   23.964239] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   23.965551] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   23.980738] Memory: 2053820k/2097088k available (2150k kernel code, 42872k reserved, 754k data, 180k init)
[   24.059513] Calibrating delay using timer specific routine.. 4427.39 BogoMIPS (lpj=8854782)
[   24.059556] Security Framework v1.0.0 initialized
[   24.059561] SELinux:  Disabled at boot.
[   24.059578] Mount-cache hash table entries: 256
[   24.059670] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   24.059673] CPU: L2 Cache: 512K (64 bytes/line)
[   24.059675] CPU 0(1) -> Node 0 -> Core 0
[   24.059681] mtrr: v2.0 (20020519)
[   24.059686] SMP alternatives: switching to UP code
[   24.059884] checking if image is initramfs... it is
[   24.551588] Freeing initrd memory: 7157k freed
[   24.557162] ACPI: Looking for DSDT ... not found!
[   24.601134] Using local APIC timer interrupts.
[   24.646351] Detected 12.564 MHz APIC timer.
[   24.646395] Brought up 1 CPUs
[   24.646423] time.c: Using PIT/TSC based timekeeping.
[   24.646424] testing NMI watchdog ... OK.
[   24.686673] NET: Registered protocol family 16
[   24.686691] ACPI: bus type pci registered
[   24.686926] PCI: Using configuration type 1
[   24.689892] PCI: Using MMCONFIG at e0000000
[   24.690324] ACPI: Subsystem revision 20051216
[   24.696811] ACPI: Interpreter enabled
[   24.696814] ACPI: Using IOAPIC for interrupt routing
[   24.697263] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   24.697265] PCI: Probing PCI hardware (bus 00)
[   24.700910] PCI: Transparent bridge - 0000:00:09.0
[   24.701070] Boot video device is 0000:01:00.0
[   24.701122] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   24.773132] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   24.774776] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   24.775062] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   24.775348] ACPI: PCI Interrupt Link [LNK3] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   24.775635] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   24.775919] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   24.776201] ACPI: PCI Interrupt Link [LUBA] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   24.776484] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   24.776768] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   24.777050] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   24.777334] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   24.777620] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   24.777902] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   24.778184] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   24.778479] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   24.778772] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   24.779064] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   24.779390] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[   24.779714] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   24.780033] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[   24.780351] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[   24.780596] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[   24.780929] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
[   24.781263] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[   24.781593] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
[   24.781923] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[   24.782252] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[   24.782589] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
[   24.782918] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
[   24.783248] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   24.783591] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.
[   24.783931] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[   24.784272] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
[   24.787570] Linux Plug and Play Support v0.97 (c) Adam Belay
[   24.787579] pnp: PnP ACPI init
[   24.793206] pnp: PnP ACPI: found 16 devices
[   24.793221] PCI: Using ACPI for IRQ routing
[   24.793224] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   24.793294] PCI-DMA: Disabling IOMMU.
[   24.793665] pnp: 00:00: ioport range 0x4000-0x407f could not be reserved
[   24.793667] pnp: 00:00: ioport range 0x4080-0x40ff has been reserved
[   24.793670] pnp: 00:00: ioport range 0x4400-0x447f has been reserved
[   24.793673] pnp: 00:00: ioport range 0x4480-0x44ff could not be reserved
[   24.793675] pnp: 00:00: ioport range 0x4800-0x487f has been reserved
[   24.793678] pnp: 00:00: ioport range 0x4880-0x48ff has been reserved
[   24.793817] PCI: Bridge: 0000:00:09.0
[   24.793818]   IO window: disabled.
[   24.793821]   MEM window: disabled.
[   24.793822]   PREFETCH window: disabled.
[   24.793824] PCI: Bridge: 0000:00:0b.0
[   24.793826]   IO window: disabled.
[   24.793827]   MEM window: disabled.
[   24.793829]   PREFETCH window: disabled.
[   24.793831] PCI: Bridge: 0000:00:0c.0
[   24.793832]   IO window: disabled.
[   24.793834]   MEM window: disabled.
[   24.793835]   PREFETCH window: disabled.
[   24.793837] PCI: Bridge: 0000:00:0d.0
[   24.793838]   IO window: disabled.
[   24.793840]   MEM window: disabled.
[   24.793841]   PREFETCH window: disabled.
[   24.793843] PCI: Bridge: 0000:00:0e.0
[   24.793845]   IO window: disabled.
[   24.793847]   MEM window: d0000000-d7ffffff
[   24.793849]   PREFETCH window: c0000000-cfffffff
[   24.793855] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   24.793860] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   24.793864] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   24.793868] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   24.793872] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   24.794054] IA32 emulation $Id: sys_ia32.c,v 1.32 2002/03/24 13:02:28 ak Exp $
[   24.794290] audit: initializing netlink socket (disabled)
[   24.794298] audit(1156887733.836:1): initialized
[   24.794404] VFS: Disk quotas dquot_6.5.1
[   24.794419] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   24.794455] Initializing Cryptographic API
[   24.794458] io scheduler noop registered
[   24.794464] io scheduler anticipatory registered
[   24.794469] io scheduler deadline registered
[   24.794482] io scheduler cfq registered
[   24.794744] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   24.794748] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[   24.794760] assign_interrupt_mode Found MSI capability
[   24.794784] Allocate Port Service[pcie00]
[   24.794812] Allocate Port Service[pcie03]
[   24.794836] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   24.794839] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[   24.794850] assign_interrupt_mode Found MSI capability
[   24.794863] Allocate Port Service[pcie00]
[   24.794886] Allocate Port Service[pcie03]
[   24.794909] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   24.794911] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[   24.794922] assign_interrupt_mode Found MSI capability
[   24.794935] Allocate Port Service[pcie00]
[   24.794956] Allocate Port Service[pcie03]
[   24.794980] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   24.794982] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[   24.794992] assign_interrupt_mode Found MSI capability
[   24.795005] Allocate Port Service[pcie00]
[   24.795026] Allocate Port Service[pcie03]
[   24.805646] Real Time Clock Driver v1.12
[   24.805676] Linux agpgart interface v0.101 (c) Dave Jones
[   24.805749] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   25.338426] serio: i8042 AUX port at 0x60,0x64 irq 12
[   25.339518] serio: i8042 KBD port at 0x60,0x64 irq 1
[   25.339554] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[   25.339642] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.341013] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.341348] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   25.341383] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   25.341386] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   25.341500] mice: PS/2 mouse device common for all mice
[   25.348533] NET: Registered protocol family 2
[   25.372408] input: AT Translated Set 2 keyboard as /class/input/input0
[   25.394299] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   25.394609] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[   25.396781] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   25.397322] TCP: Hash tables configured (established 262144 bind 65536)
[   25.397325] TCP reno registered
[   25.397395] TCP bic registered
[   25.397400] NET: Registered protocol family 1
[   25.397406] NET: Registered protocol family 8
[   25.397407] NET: Registered protocol family 20
[   25.397511] ACPI wakeup devices: 
[   25.397512] HUB0 XVR0 XVR1 XVR2 XVR3 USB0 USB2 MMAC MMCI UAR1 PS2M PS2K 
[   25.397518] ACPI: (supports S0 S1 S3 S4 S5)
[   25.397578] Freeing unused kernel memory: 180k freed
[   25.428726] Capability LSM initialized
[   25.450124] ACPI: Fan [FAN] (on)
[   25.453612] ACPI: Thermal Zone [THRM] (40 C)
[   25.801034] SCSI subsystem initialized
[   25.802434] ACPI: bus type scsi registered
[   25.802436] libata version 1.20 loaded.
[   25.803719] sata_nv 0000:00:07.0: version 0.8
[   25.804168] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[   25.804172] GSI 16 sharing vector 0xD9 and IRQ 16
[   25.804176] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] -> GSI 23 (level, low) -> IRQ 217
[   25.804254] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   25.804310] ata1: SATA max UDMA/133 cmd 0x9F0 ctl 0xBF2 bmdma 0xD800 irq 217
[   25.804326] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xB72 bmdma 0xD808 irq 217
[   26.010168] ata1: no device found (phy stat 00000000)
[   26.010171] scsi0 : sata_nv
[   26.214139] ata2: no device found (phy stat 00000000)
[   26.214142] scsi1 : sata_nv
[   26.214812] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
[   26.214816] GSI 17 sharing vector 0xE1 and IRQ 17
[   26.214821] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 22 (level, low) -> IRQ 225
[   26.214892] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   26.214932] ata3: SATA max UDMA/133 cmd 0x9E0 ctl 0xBE2 bmdma 0xC400 irq 225
[   26.214948] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xB62 bmdma 0xC408 irq 225
[   26.582175] ata3: dev 0 cfg 00:427a 49:2f00 82:746b 83:7f01 84:4023 85:7468 86:3c01 87:4023 88:407f 93:0000
[   26.582179] ata3: dev 0 ATA-7, max UDMA/133, 488397168 sectors: LBA48
[   26.585851] sata_get_dev_handle: SATA dev addr=0x80000, handle=0xffff810037fe2480
[   26.592428] nv_sata: Primary device added
[   26.592430] nv_sata: Primary device removed
[   26.592431] nv_sata: Secondary device added
[   26.592433] nv_sata: Secondary device removed
[   26.592436] ata3: dev 0 configured for UDMA/133
[   26.596120] sata_get_dev_handle: SATA dev addr=0x80000, handle=0xffff810037fe2480
[   26.602620] scsi2 : sata_nv
[   26.970122] ata4: dev 0 cfg 00:427a 49:2f00 82:746b 83:7f01 84:4023 85:7468 86:3c01 87:4023 88:407f 93:0000
[   26.970126] ata4: dev 0 ATA-7, max UDMA/133, 488397168 sectors: LBA48
[   26.973796] sata_get_dev_handle: SATA dev addr=0x80000, handle=0xffff810037fe2480
[   26.980393] nv_sata: Primary device added
[   26.980395] nv_sata: Primary device removed
[   26.980396] nv_sata: Secondary device added
[   26.980398] nv_sata: Secondary device removed
[   26.980400] ata4: dev 0 configured for UDMA/133
[   26.984079] sata_get_dev_handle: SATA dev addr=0x80000, handle=0xffff810037fe2480
[   26.990578] scsi3 : sata_nv
[   26.991157]   Vendor: ATA       Model: WDC WD2500KS-00M  Rev: 02.0
[   26.991164]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   26.994717] Driver 'sd' needs updating - please use bus_type methods
[   26.995259]   Vendor: ATA       Model: WDC WD2500KS-00M  Rev: 02.0
[   26.995266]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   26.996689] NFORCE-CK804: IDE controller at PCI slot 0000:00:06.0
[   26.996703] NFORCE-CK804: chipset revision 242
[   26.996705] NFORCE-CK804: not 100% native mode: will probe irqs later
[   26.996709] NFORCE-CK804: 0000:00:06.0 (rev f2) UDMA133 controller
[   26.996716]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[   26.996723]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
[   26.996729] Probing IDE interface ide0...
[   27.006743] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[   27.008550] SCSI device sda: drive cache: write back
[   27.010930] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[   27.010943] SCSI device sda: drive cache: write back
[   27.010947]  sda: unknown partition table
[   27.024487] sd 2:0:0:0: Attached scsi disk sda
[   27.024530] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[   27.027246] SCSI device sdb: drive cache: write back
[   27.031247] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[   27.033685] SCSI device sdb: drive cache: write back
[   27.033689]  sdb: sdb1 sdb2 < > sdb3 sdb4
[   27.053861] sd 3:0:0:0: Attached scsi disk sdb
[   27.119406] Buffer I/O error on device sdb3, logical block 15727584
[   27.119440] Buffer I/O error on device sdb3, logical block 15727585
[   27.119888] Buffer I/O error on device sdb3, logical block 15727584
[   27.119922] Buffer I/O error on device sdb4, logical block 48128
[   27.119952] Buffer I/O error on device sdb4, logical block 48129
[   27.119982] Buffer I/O error on device sdb4, logical block 48130
[   27.120012] Buffer I/O error on device sdb4, logical block 48131
[   27.120051] Buffer I/O error on device sdb4, logical block 48128
[   27.120082] Buffer I/O error on device sdb3, logical block 15727585
[   27.120125] Buffer I/O error on device sdb3, logical block 15727634
[   27.734001] hda: LITE-ON DVDRW SHM-165P6S, ATAPI CD/DVD-ROM drive
[   28.406377] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   28.419005] Probing IDE interface ide1...
[   29.157801] hdc: LITE-ON DVD SHD-16P1S, ATAPI CD/DVD-ROM drive
[   29.829781] ide1 at 0x170-0x177,0x376 on irq 15
[   29.839867] hda: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)
[   29.839875] Uniform CD-ROM driver Revision: 3.20
[   29.842823] hdc: ATAPI 48X DVD-ROM drive, 1725kB Cache, UDMA(33)
[   29.925428] usbcore: registered new driver usbfs
[   29.925443] usbcore: registered new driver hub
[   29.926082] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   29.926452] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[   29.926457] GSI 18 sharing vector 0xE9 and IRQ 18
[   29.926461] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 21 (level, low) -> IRQ 233
[   29.926525] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   29.926530] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   29.939245] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   29.939253] ohci_hcd 0000:00:02.0: irq 233, io mem 0xd8004000
[   29.986762] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.54.
[   29.999697] hub 1-0:1.0: USB hub found
[   29.999706] hub 1-0:1.0: 10 ports detected
[   30.106567] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
[   30.106572] GSI 19 sharing vector 0x32 and IRQ 19
[   30.106577] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 20 (level, low) -> IRQ 50
[   30.106654] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   30.106659] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   30.106685] ehci_hcd 0000:00:02.1: debug port 1
[   30.106687] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   30.106842] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   30.106851] ehci_hcd 0000:00:02.1: irq 50, io mem 0xfeb00000
[   30.106858] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   30.107040] hub 2-0:1.0: USB hub found
[   30.107046] hub 2-0:1.0: 10 ports detected
[   30.214581] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[   30.214586] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APCH] -> GSI 23 (level, low) -> IRQ 217
[   30.214591] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   30.214597] forcedeth: using HIGHDMA
[   30.737744] eth0: forcedeth.c: subsystem: 01043:8141 bound to 0000:00:0a.0
[   30.764890] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[   30.959897] cdrom: open failed.
[   30.961979] cdrom: open failed.
[   31.073479] ohci_hcd 0000:00:02.0: wakeup
[   31.161225] kjournald starting.  Commit interval 5 seconds
[   31.161234] EXT3-fs: mounted filesystem with ordered data mode.
[   31.457414] usb 1-2: new low speed USB device using ohci_hcd and address 2
[   31.993347] usb 1-3: new full speed USB device using ohci_hcd and address 3
[   32.629264] usb 1-4: new low speed USB device using ohci_hcd and address 4
[   36.378759] printk: 404 messages suppressed.
[   36.378764] Buffer I/O error on device sdb3, logical block 15727584
[   36.502208] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   36.502231] sd 3:0:0:0: Attached scsi generic sg1 type 0
[   38.057649] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[   38.057675] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x4c40
[   38.170583] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
[   38.170587] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCJ] -> GSI 22 (level, low) -> IRQ 225
[   38.170665] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   38.243719] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   38.422019] logips2pp: Detected unknown logitech mouse model 127
[   38.492474] intel8x0_measure_ac97_clock: measured 54727 usecs
[   38.492478] intel8x0: clocking to 46909
[   38.492935] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   38.688673] usbcore: registered new driver hiddev
[   38.693977] Bluetooth: Core ver 2.8
[   38.693981] NET: Registered protocol family 31
[   38.693982] Bluetooth: HCI device and connection manager initialized
[   38.693990] Bluetooth: HCI socket layer initialized
[   38.710236] NET: Registered protocol family 17
[   38.725783] parport: PnPBIOS parport detected.
[   38.725829] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   38.748801] input: PC Speaker as /class/input/input1
[   38.750359] Bluetooth: HCI USB driver ver 2.9
[   38.764899] input: Saitek PLC Saitek P2600 Rumble Force Pad as /class/input/input2
[   38.764924] input: USB HID v1.10 Joystick [Saitek PLC Saitek P2600 Rumble Force Pad] on usb-0000:00:02.0-2
[   38.781496] Floppy drive(s): fd0 is 1.44M
[   38.790431] input: Saitek Cyborg USB Stick as /class/input/input3
[   38.790471] input: USB HID v1.00 Joystick [Saitek Cyborg USB Stick] on usb-0000:00:02.0-4
[   38.790507] usbcore: registered new driver usbhid
[   38.790510] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   38.791448] usbcore: registered new driver hci_usb
[   38.804409] FDC 0 is a post-1991 82077
[   38.868818] input: ImExPS/2 Logitech Explorer Mouse as /class/input/input4
[   38.917830] nvidia: module license 'NVIDIA' taints kernel.
[   38.925492] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   38.925498] GSI 20 sharing vector 0x3A and IRQ 20
[   38.925502] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 58
[   38.925509] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   38.925616] NVRM: loading NVIDIA Linux x86_64 Kernel Module  1.0-8762  Mon May 15 13:58:14 PDT 2006
[   39.042016] ts: Compaq touchscreen protocol output
[   39.516338] fuse init (API version 7.3)
[   39.560650] NET: Registered protocol family 10
[   39.560737] lo: Disabled Privacy Extensions
[   39.561061] IPv6 over IPv4 tunneling driver
[   39.860307] it87: Found IT8712F chip at 0x290, revision 7
[   39.947194] EXT3 FS on dm-2, internal journal
[   40.053263] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   40.053266] md: bitmap version 4.39
[   40.131840] printk: 401 messages suppressed.
[   40.131844] Buffer I/O error on device sdb3, logical block 15727584
[   40.261641] cdrom: open failed.
[   40.783255] kjournald starting.  Commit interval 5 seconds
[   40.783365] EXT3 FS on dm-6, internal journal
[   40.783369] EXT3-fs: mounted filesystem with ordered data mode.
[   40.784083] kjournald starting.  Commit interval 5 seconds
[   40.786397] EXT3 FS on dm-3, internal journal
[   40.786402] EXT3-fs: mounted filesystem with ordered data mode.
[   40.838566] kjournald starting.  Commit interval 5 seconds
[   40.838700] EXT3 FS on dm-7, internal journal
[   40.838703] EXT3-fs: mounted filesystem with ordered data mode.
[   40.878736] NTFS driver 2.1.25 [Flags: R/O MODULE].
[   40.948659] NTFS volume version 3.1.
[   40.988136] NTFS volume version 3.1.
```

I'm not sure what these errors mean. They don't seem to be causing any real problems, but I'm just curious. I'm running 2 SATA drives as RAID 0 using NVIDIA software RAID on my ASUS A8N-E motherboard if that helps (so sda and sdb aren't really mounted disks. My root partition is mounted on /dev/mapper/nvidia_dgcadeeg3)

Cheers

---

