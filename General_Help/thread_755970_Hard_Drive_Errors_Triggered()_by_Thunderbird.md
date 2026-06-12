---
title: "Hard Drive Errors Triggered(?) by Thunderbird"
date: 2008-04-15
forum: General Help
---

### Post by schmutt on 2008-04-15
I'm new to Ubuntu (and loving it so far!). I just installed 7.10 on a new hard drive on my Dell Latitude D620 in a dual-boot setup with WinXP home. Things have been going great, but I started to have some very annoying problems affecting my hard drive. The problem happens as follows:

1. System boots fine
2. Every application is ok
3. Open Thunderbird and try to open an email
4. Hard drive goes into a death spiral; Thunderbird screen turns gray and cannot be closed.

Nothing else seems to be affected. I can even continue to run other applications as long as they do not need to access the hard drive. However, I cannot completely shutdown the system because it continues to get errors.

I am not 100% sure that this is entirely related to Thunderbird, because I was having some other related problems last night. But right now, the problem is only produced with Thunderbird, and as long as I don't run Thunderbird, the system seems fine (I am using it right now).

Also, I am using a completely vanilla installation of Thunderbird. No skins; only using the Enigmail plugin.

I searched long and hard, but haven't found a solution that applies to this specific problem

Here are the error messages I get in  kern.log (skip to bottom to see disk errors)
```

Apr 15 10:46:38 ian-latitude kernel: Inspecting /boot/System.map-2.6.22-14-generic
Apr 15 10:46:38 ian-latitude kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Apr 15 10:46:38 ian-latitude kernel: Symbols match kernel version 2.6.22.
Apr 15 10:46:38 ian-latitude kernel: No module symbols loaded - kernel modules not enabled. 
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 15 10:46:38 ian-latitude kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Apr 15 10:46:38 ian-latitude kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Apr 15 10:46:38 ian-latitude kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fe81400 (usable)
Apr 15 10:46:38 ian-latitude kernel: [    0.000000]  BIOS-e820: 000000007fe81400 - 0000000080000000 (reserved)
Apr 15 10:46:38 ian-latitude kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4007000 (reserved)
Apr 15 10:46:38 ian-latitude kernel: [    0.000000]  BIOS-e820: 00000000f4008000 - 00000000f400c000 (reserved)
Apr 15 10:46:38 ian-latitude kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Apr 15 10:46:38 ian-latitude kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
Apr 15 10:46:38 ian-latitude kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
Apr 15 10:46:38 ian-latitude kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] 1150MB HIGHMEM available.
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] 896MB LOWMEM available.
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] Entering add_active_range(0, 0, 523905) 0 entries of 256 used
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] Zone PFN ranges:
Apr 15 10:46:38 ian-latitude kernel: [    0.000000]   DMA             0 ->     4096
Apr 15 10:46:38 ian-latitude kernel: [    0.000000]   Normal       4096 ->   229376
Apr 15 10:46:38 ian-latitude kernel: [    0.000000]   HighMem    229376 ->   523905
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr 15 10:46:38 ian-latitude kernel: [    0.000000]     0:        0 ->   523905
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] On node 0 totalpages: 523905
Apr 15 10:46:38 ian-latitude kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Apr 15 10:46:38 ian-latitude kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr 15 10:46:38 ian-latitude kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Apr 15 10:46:38 ian-latitude kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Apr 15 10:46:38 ian-latitude kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Apr 15 10:46:38 ian-latitude kernel: [    0.000000]   HighMem zone: 2301 pages used for memmap
Apr 15 10:46:38 ian-latitude kernel: [    0.000000]   HighMem zone: 292228 pages, LIFO batch:31
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] DMI 2.4 present.
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FC0C0 checksum 0
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] ACPI: RSDP 000FC0C0, 0014 (r0 DELL  )
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] ACPI: RSDT 7FE8198A, 0044 (r1 DELL    M07     27D8010B ASL        61)
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] ACPI: FACP 7FE82800, 0074 (r1 DELL    M07     27D8010B ASL        61)
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] ACPI: DSDT 7FE83400, 519E (r1 INT430 SYSFexxx     1001 INTL 20050624)
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] ACPI: FACS 7FE91C00, 0040
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] ACPI: HPET 7FE82F00, 0038 (r1 DELL    M07            1 ASL        61)
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] ACPI: APIC 7FE83000, 0068 (r1 DELL    M07     27D8010B ASL        47)
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] ACPI: ASF! 7FE82C00, 005B (r16 DELL    M07     27D8010B ASL        61)
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] ACPI: MCFG 7FE82FC0, 003E (r16 DELL    M07     27D8010B ASL        61)
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] ACPI: TCPA 7FE83300, 0032 (r1 DELL    M07     27D8010B ASL        61)
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] ACPI: SLIC 7FE8309C, 0176 (r1 DELL    M07     27D8010B ASL        61)
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] ACPI: SSDT 7FE81A11, 04DC (r1  PmRef    CpuPm     3000 INTL 20050624)
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] Processor #0 6:14 APIC version 20
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] Processor #1 6:14 APIC version 20
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] ACPI: IRQ0 used by override.
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] ACPI: IRQ2 used by override.
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] ACPI: IRQ9 used by override.
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:70000000)
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] Built 1 zonelists.  Total pages: 519812
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] Kernel command line: root=UUID=9e22ffd6-2683-4dd8-8aa1-00c6cffa2e95 ro quiet splash
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] mapped APIC to ffffd000 (fee00000)
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] mapped IOAPIC to ffffc000 (fec00000)
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] Enabling fast FPU save and restore... done.
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] Initializing CPU#0
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Apr 15 10:46:38 ian-latitude kernel: [    0.000000] Detected 1995.119 MHz processor.
Apr 15 10:46:38 ian-latitude kernel: [    6.093831] Console: colour VGA+ 80x25
Apr 15 10:46:38 ian-latitude kernel: [    6.094081] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Apr 15 10:46:38 ian-latitude kernel: [    6.094405] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 15 10:46:38 ian-latitude kernel: [    6.187379] Memory: 2066096k/2095620k available (2015k kernel code, 28176k reserved, 915k data, 364k init, 1178116k highmem)
Apr 15 10:46:38 ian-latitude kernel: [    6.187388] virtual kernel memory layout:
Apr 15 10:46:38 ian-latitude kernel: [    6.187389]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Apr 15 10:46:38 ian-latitude kernel: [    6.187391]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Apr 15 10:46:38 ian-latitude kernel: [    6.187392]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Apr 15 10:46:38 ian-latitude kernel: [    6.187393]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Apr 15 10:46:38 ian-latitude kernel: [    6.187394]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Apr 15 10:46:38 ian-latitude kernel: [    6.187395]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
Apr 15 10:46:38 ian-latitude kernel: [    6.187396]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
Apr 15 10:46:38 ian-latitude kernel: [    6.187399] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr 15 10:46:38 ian-latitude kernel: [    6.187433] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Apr 15 10:46:38 ian-latitude kernel: [    6.187558] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Apr 15 10:46:38 ian-latitude kernel: [    6.187562] hpet0: 3 64-bit timers, 14318180 Hz
Apr 15 10:46:38 ian-latitude kernel: [    6.268533] Calibrating delay using timer specific routine.. 3993.23 BogoMIPS (lpj=7986470)
Apr 15 10:46:38 ian-latitude kernel: [    6.268555] Security Framework v1.0.0 initialized
Apr 15 10:46:38 ian-latitude kernel: [    6.268562] SELinux:  Disabled at boot.
Apr 15 10:46:38 ian-latitude kernel: [    6.268574] Mount-cache hash table entries: 512
Apr 15 10:46:38 ian-latitude kernel: [    6.268689] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c1a9 00000000 00000000
Apr 15 10:46:38 ian-latitude kernel: [    6.268697] monitor/mwait feature present.
Apr 15 10:46:38 ian-latitude kernel: [    6.268699] using mwait in idle threads.
Apr 15 10:46:38 ian-latitude kernel: [    6.268703] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 15 10:46:38 ian-latitude kernel: [    6.268705] CPU: L2 cache: 2048K
Apr 15 10:46:38 ian-latitude kernel: [    6.268708] CPU: Physical Processor ID: 0
Apr 15 10:46:38 ian-latitude kernel: [    6.268709] CPU: Processor Core ID: 0
Apr 15 10:46:38 ian-latitude kernel: [    6.268711] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c1a9 00000000 00000000
Apr 15 10:46:38 ian-latitude kernel: [    6.268719] Compat vDSO mapped to ffffe000.
Apr 15 10:46:38 ian-latitude kernel: [    6.268731] Checking 'hlt' instruction... OK.
Apr 15 10:46:38 ian-latitude kernel: [    6.284639] SMP alternatives: switching to UP code
Apr 15 10:46:38 ian-latitude kernel: [    6.285055] Early unpacking initramfs... done
Apr 15 10:46:38 ian-latitude kernel: [    6.574691] ACPI: Core revision 20070126
Apr 15 10:46:38 ian-latitude kernel: [    6.574744] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Apr 15 10:46:38 ian-latitude kernel: [    6.577399] CPU0: Intel Genuine Intel(R) CPU           T2500  @ 2.00GHz stepping 08
Apr 15 10:46:38 ian-latitude kernel: [    6.577415] SMP alternatives: switching to SMP code
Apr 15 10:46:38 ian-latitude kernel: [    6.577516] Booting processor 1/1 eip 3000
Apr 15 10:46:38 ian-latitude kernel: [    8.740787] Initializing CPU#1
Apr 15 10:46:38 ian-latitude kernel: [    8.818592] Calibrating delay using timer specific routine.. 3990.04 BogoMIPS (lpj=7980098)
Apr 15 10:46:38 ian-latitude kernel: [    8.818598] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c1a9 00000000 00000000
Apr 15 10:46:38 ian-latitude kernel: [    8.818603] monitor/mwait feature present.
Apr 15 10:46:38 ian-latitude kernel: [    8.818606] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 15 10:46:38 ian-latitude kernel: [    8.818608] CPU: L2 cache: 2048K
Apr 15 10:46:38 ian-latitude kernel: [    8.818610] CPU: Physical Processor ID: 0
Apr 15 10:46:38 ian-latitude kernel: [    8.818611] CPU: Processor Core ID: 1
Apr 15 10:46:38 ian-latitude kernel: [    8.818613] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c1a9 00000000 00000000
Apr 15 10:46:38 ian-latitude kernel: [    6.668786] CPU1: Intel Genuine Intel(R) CPU           T2500  @ 2.00GHz stepping 08
Apr 15 10:46:38 ian-latitude kernel: [    6.668805] Total of 2 processors activated (7983.28 BogoMIPS).
Apr 15 10:46:38 ian-latitude kernel: [    6.668952] ENABLING IO-APIC IRQs
Apr 15 10:46:38 ian-latitude kernel: [    6.669130] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 15 10:46:38 ian-latitude kernel: [    6.816306] checking TSC synchronization [CPU#0 -> CPU#1]:
Apr 15 10:46:38 ian-latitude kernel: [    6.836304] Measured 4292190132 cycles TSC warp between CPUs, turning off TSC clock.
Apr 15 10:46:38 ian-latitude kernel: [    0.520000] Marking TSC unstable due to: check_tsc_sync_source failed.
Apr 15 10:46:38 ian-latitude kernel: [    0.524000] Brought up 2 CPUs
Apr 15 10:46:38 ian-latitude kernel: [    0.624000] migration_cost=4000
Apr 15 10:46:38 ian-latitude kernel: [    0.624000] Booting paravirtualized kernel on bare hardware
Apr 15 10:46:38 ian-latitude kernel: [    0.624000] Time: 10:46:24  Date: 03/15/108
Apr 15 10:46:38 ian-latitude kernel: [    0.624000] NET: Registered protocol family 16
Apr 15 10:46:38 ian-latitude kernel: [    0.624000] EISA bus registered
Apr 15 10:46:38 ian-latitude kernel: [    0.624000] ACPI: bus type pci registered
Apr 15 10:46:38 ian-latitude kernel: [    0.648000] PCI: PCI BIOS revision 2.10 entry at 0xfacc6, last bus=12
Apr 15 10:46:38 ian-latitude kernel: [    0.648000] PCI: Using configuration type 1
Apr 15 10:46:38 ian-latitude kernel: [    0.648000] Setting up standard PCI resources
Apr 15 10:46:38 ian-latitude kernel: [    0.652000] ACPI: EC: Look up EC in DSDT
Apr 15 10:46:38 ian-latitude kernel: [    0.668000] ACPI Warning (tbutils-0217): Incorrect checksum in table [TCPA] -  00, should be A3 [20070126]
Apr 15 10:46:38 ian-latitude kernel: [    0.668000] ACPI: SSDT 7FE819CE, 0043 (r1  LMPWR  DELLLOM     1001 INTL 20050624)
Apr 15 10:46:38 ian-latitude kernel: [    0.668000] ACPI: Interpreter enabled
Apr 15 10:46:38 ian-latitude kernel: [    0.668000] ACPI: (supports S0 S3 S4 S5)
Apr 15 10:46:38 ian-latitude kernel: [    0.668000] ACPI: Using IOAPIC for interrupt routing
Apr 15 10:46:38 ian-latitude kernel: [    0.704000] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 15 10:46:38 ian-latitude kernel: [    0.704000] PCI: Probing PCI hardware (bus 00)
Apr 15 10:46:38 ian-latitude kernel: [    0.704000] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Apr 15 10:46:38 ian-latitude kernel: [    0.704000] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
Apr 15 10:46:38 ian-latitude kernel: [    0.704000] PCI: Transparent bridge - 0000:00:1e.0
Apr 15 10:46:38 ian-latitude kernel: [    0.704000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr 15 10:46:38 ian-latitude kernel: [    0.704000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
Apr 15 10:46:38 ian-latitude kernel: [    0.704000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
Apr 15 10:46:38 ian-latitude kernel: [    0.704000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Apr 15 10:46:38 ian-latitude kernel: [    0.704000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
Apr 15 10:46:38 ian-latitude kernel: [    0.704000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PXP0._PRT]
Apr 15 10:46:38 ian-latitude kernel: [    0.716000] ACPI: PCI Interrupt Link [LNKA] (IRQs *9 10 11)
Apr 15 10:46:38 ian-latitude kernel: [    0.716000] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *3
Apr 15 10:46:38 ian-latitude kernel: [    0.716000] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *5
Apr 15 10:46:38 ian-latitude kernel: [    0.716000] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *0, disabled.
Apr 15 10:46:38 ian-latitude kernel: [    0.716000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Apr 15 10:46:38 ian-latitude kernel: [    0.716000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Apr 15 10:46:38 ian-latitude kernel: [    0.716000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Apr 15 10:46:38 ian-latitude kernel: [    0.716000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Apr 15 10:46:38 ian-latitude kernel: [    0.716000] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr 15 10:46:38 ian-latitude kernel: [    0.716000] pnp: PnP ACPI init
Apr 15 10:46:38 ian-latitude kernel: [    0.716000] ACPI: bus type pnp registered
Apr 15 10:46:38 ian-latitude kernel: [    0.764000] pnp: PnP ACPI: found 14 devices
Apr 15 10:46:38 ian-latitude kernel: [    0.764000] ACPI: ACPI bus type pnp unregistered
Apr 15 10:46:38 ian-latitude kernel: [    0.764000] PnPBIOS: Disabled by ACPI PNP
Apr 15 10:46:38 ian-latitude kernel: [    0.764000] PCI: Using ACPI for IRQ routing
Apr 15 10:46:38 ian-latitude kernel: [    0.764000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr 15 10:46:38 ian-latitude kernel: [    0.788000] NET: Registered protocol family 8
Apr 15 10:46:38 ian-latitude kernel: [    0.788000] NET: Registered protocol family 20
Apr 15 10:46:38 ian-latitude kernel: [    0.788000] pnp: 00:00: iomem range 0x0-0x9fbff could not be reserved
Apr 15 10:46:38 ian-latitude kernel: [    0.788000] pnp: 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
Apr 15 10:46:38 ian-latitude kernel: [    0.788000] pnp: 00:00: iomem range 0xc0000-0xcffff could not be reserved
Apr 15 10:46:38 ian-latitude kernel: [    0.788000] pnp: 00:00: iomem range 0xe0000-0xfffff could not be reserved
Apr 15 10:46:38 ian-latitude kernel: [    0.788000] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
Apr 15 10:46:38 ian-latitude kernel: [    0.788000] pnp: 00:02: ioport range 0x1000-0x1005 has been reserved
Apr 15 10:46:38 ian-latitude kernel: [    0.788000] pnp: 00:02: ioport range 0x1008-0x100f has been reserved
Apr 15 10:46:38 ian-latitude kernel: [    0.788000] pnp: 00:03: ioport range 0xf400-0xf4fe has been reserved
Apr 15 10:46:38 ian-latitude kernel: [    0.788000] pnp: 00:03: ioport range 0x1006-0x1007 has been reserved
Apr 15 10:46:38 ian-latitude kernel: [    0.788000] pnp: 00:03: ioport range 0x100a-0x1059 could not be reserved
Apr 15 10:46:38 ian-latitude kernel: [    0.788000] pnp: 00:03: ioport range 0x1060-0x107f has been reserved
Apr 15 10:46:38 ian-latitude kernel: [    0.788000] pnp: 00:03: ioport range 0x1080-0x10bf has been reserved
Apr 15 10:46:38 ian-latitude kernel: [    0.788000] pnp: 00:03: ioport range 0x10c0-0x10df has been reserved
Apr 15 10:46:38 ian-latitude kernel: [    0.788000] pnp: 00:08: ioport range 0xc80-0xcaf has been reserved
Apr 15 10:46:38 ian-latitude kernel: [    0.788000] pnp: 00:08: ioport range 0xcc0-0xcff could not be reserved
Apr 15 10:46:38 ian-latitude kernel: [    0.788000] pnp: 00:08: ioport range 0x910-0x91f has been reserved
Apr 15 10:46:38 ian-latitude kernel: [    0.788000] pnp: 00:08: ioport range 0x920-0x92f has been reserved
Apr 15 10:46:38 ian-latitude kernel: [    0.788000] pnp: 00:08: ioport range 0xcbc-0xcbf has been reserved
Apr 15 10:46:38 ian-latitude kernel: [    0.788000] pnp: 00:08: ioport range 0x930-0x97f has been reserved
Apr 15 10:46:38 ian-latitude kernel: [    0.788000] pnp: 00:0b: iomem range 0xfed00000-0xfed003ff has been reserved
Apr 15 10:46:38 ian-latitude kernel: [    0.788000] pnp: 00:0d: ioport range 0xcb0-0xcbb has been reserved
Apr 15 10:46:38 ian-latitude kernel: [    0.788000] pnp: 00:0d: iomem range 0xfed40000-0xfed44fff could not be reserved
Apr 15 10:46:38 ian-latitude kernel: [    0.792000] Time: hpet clocksource has been installed.
Apr 15 10:46:38 ian-latitude kernel: [    0.792000] Switched to high resolution mode on CPU 0
Apr 15 10:46:38 ian-latitude kernel: [    0.792000] Switched to high resolution mode on CPU 1
Apr 15 10:46:38 ian-latitude kernel: [    0.820000] PCI: Bridge: 0000:00:01.0
Apr 15 10:46:38 ian-latitude kernel: [    0.820000]   IO window: disabled.
Apr 15 10:46:38 ian-latitude kernel: [    0.820000]   MEM window: ed000000-efefffff
Apr 15 10:46:38 ian-latitude kernel: [    0.820000]   PREFETCH window: d0000000-dfffffff
Apr 15 10:46:38 ian-latitude kernel: [    0.820000] PCI: Bridge: 0000:00:1c.0
Apr 15 10:46:38 ian-latitude kernel: [    0.820000]   IO window: disabled.
Apr 15 10:46:38 ian-latitude kernel: [    0.820000]   MEM window: disabled.
Apr 15 10:46:38 ian-latitude kernel: [    0.820000]   PREFETCH window: disabled.
Apr 15 10:46:38 ian-latitude kernel: [    0.820000] PCI: Bridge: 0000:00:1c.1
Apr 15 10:46:38 ian-latitude kernel: [    0.820000]   IO window: disabled.
Apr 15 10:46:38 ian-latitude kernel: [    0.820000]   MEM window: ecf00000-ecffffff
Apr 15 10:46:38 ian-latitude kernel: [    0.820000]   PREFETCH window: disabled.
Apr 15 10:46:38 ian-latitude kernel: [    0.820000] PCI: Bridge: 0000:00:1c.2
Apr 15 10:46:38 ian-latitude kernel: [    0.820000]   IO window: disabled.
Apr 15 10:46:38 ian-latitude kernel: [    0.820000]   MEM window: ece00000-ecefffff
Apr 15 10:46:38 ian-latitude kernel: [    0.820000]   PREFETCH window: disabled.
Apr 15 10:46:38 ian-latitude kernel: [    0.820000] PCI: Bus 4, cardbus bridge: 0000:03:01.0
Apr 15 10:46:38 ian-latitude kernel: [    0.820000]   IO window: 00002000-000020ff
Apr 15 10:46:38 ian-latitude kernel: [    0.820000]   IO window: 00002400-000024ff
Apr 15 10:46:38 ian-latitude kernel: [    0.820000]   PREFETCH window: 88000000-8bffffff
Apr 15 10:46:38 ian-latitude kernel: [    0.820000]   MEM window: 8c000000-8fffffff
Apr 15 10:46:38 ian-latitude kernel: [    0.820000] PCI: Bridge: 0000:00:1e.0
Apr 15 10:46:38 ian-latitude kernel: [    0.820000]   IO window: 2000-2fff
Apr 15 10:46:38 ian-latitude kernel: [    0.820000]   MEM window: 8c000000-91ffffff
Apr 15 10:46:38 ian-latitude kernel: [    0.820000]   PREFETCH window: 88000000-8bffffff
Apr 15 10:46:38 ian-latitude kernel: [    0.820000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 15 10:46:38 ian-latitude kernel: [    0.820000] PCI: Setting latency timer of device 0000:00:01.0 to 64
Apr 15 10:46:38 ian-latitude kernel: [    0.820000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 15 10:46:38 ian-latitude kernel: [    0.820000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Apr 15 10:46:38 ian-latitude kernel: [    0.820000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
Apr 15 10:46:38 ian-latitude kernel: [    0.820000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
Apr 15 10:46:38 ian-latitude kernel: [    0.820000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
Apr 15 10:46:38 ian-latitude kernel: [    0.820000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
Apr 15 10:46:38 ian-latitude kernel: [    0.820000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Apr 15 10:46:38 ian-latitude kernel: [    0.820000] PCI: Enabling device 0000:03:01.0 (0000 -> 0003)
Apr 15 10:46:38 ian-latitude kernel: [    0.820000] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 18 (level, low) -> IRQ 18
Apr 15 10:46:38 ian-latitude kernel: [    0.820000] NET: Registered protocol family 2
Apr 15 10:46:38 ian-latitude kernel: [    0.860000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 15 10:46:38 ian-latitude kernel: [    0.860000] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
Apr 15 10:46:38 ian-latitude kernel: [    0.860000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Apr 15 10:46:38 ian-latitude kernel: [    0.860000] TCP: Hash tables configured (established 131072 bind 65536)
Apr 15 10:46:38 ian-latitude kernel: [    0.860000] TCP reno registered
Apr 15 10:46:38 ian-latitude kernel: [    0.876000] checking if image is initramfs... it is
Apr 15 10:46:38 ian-latitude kernel: [    1.452000] Freeing initrd memory: 7052k freed
Apr 15 10:46:38 ian-latitude kernel: [    1.452000] audit: initializing netlink socket (disabled)
Apr 15 10:46:38 ian-latitude kernel: [    1.452000] audit(1208256384.292:1): initialized
Apr 15 10:46:38 ian-latitude kernel: [    1.452000] highmem bounce pool size: 64 pages
Apr 15 10:46:38 ian-latitude kernel: [    1.456000] VFS: Disk quotas dquot_6.5.1
Apr 15 10:46:38 ian-latitude kernel: [    1.456000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 15 10:46:38 ian-latitude kernel: [    1.456000] io scheduler noop registered
Apr 15 10:46:38 ian-latitude kernel: [    1.456000] io scheduler anticipatory registered
Apr 15 10:46:38 ian-latitude kernel: [    1.456000] io scheduler deadline registered
Apr 15 10:46:38 ian-latitude kernel: [    1.456000] io scheduler cfq registered (default)
Apr 15 10:46:38 ian-latitude kernel: [    1.456000] Boot video device is 0000:01:00.0
Apr 15 10:46:38 ian-latitude kernel: [    1.456000] PCI: Setting latency timer of device 0000:00:01.0 to 64
Apr 15 10:46:38 ian-latitude kernel: [    1.456000] assign_interrupt_mode Found MSI capability
Apr 15 10:46:38 ian-latitude kernel: [    1.456000] Allocate Port Service[0000:00:01.0:pcie00]
Apr 15 10:46:38 ian-latitude kernel: [    1.456000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Apr 15 10:46:38 ian-latitude kernel: [    1.456000] assign_interrupt_mode Found MSI capability
Apr 15 10:46:38 ian-latitude kernel: [    1.456000] Allocate Port Service[0000:00:1c.0:pcie00]
Apr 15 10:46:38 ian-latitude kernel: [    1.456000] Allocate Port Service[0000:00:1c.0:pcie02]
Apr 15 10:46:38 ian-latitude kernel: [    1.456000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
Apr 15 10:46:38 ian-latitude kernel: [    1.456000] assign_interrupt_mode Found MSI capability
Apr 15 10:46:38 ian-latitude kernel: [    1.456000] Allocate Port Service[0000:00:1c.1:pcie00]
Apr 15 10:46:38 ian-latitude kernel: [    1.456000] Allocate Port Service[0000:00:1c.1:pcie02]
Apr 15 10:46:38 ian-latitude kernel: [    1.456000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
Apr 15 10:46:38 ian-latitude kernel: [    1.456000] assign_interrupt_mode Found MSI capability
Apr 15 10:46:38 ian-latitude kernel: [    1.456000] Allocate Port Service[0000:00:1c.2:pcie00]
Apr 15 10:46:38 ian-latitude kernel: [    1.456000] Allocate Port Service[0000:00:1c.2:pcie02]
Apr 15 10:46:38 ian-latitude kernel: [    1.456000] isapnp: Scanning for PnP cards...
Apr 15 10:46:38 ian-latitude kernel: [    1.808000] isapnp: No Plug & Play device found
Apr 15 10:46:38 ian-latitude kernel: [    1.828000] Real Time Clock Driver v1.12ac
Apr 15 10:46:38 ian-latitude kernel: [    1.828000] hpet_resources: 0xfed00000 is busy
Apr 15 10:46:38 ian-latitude kernel: [    1.828000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr 15 10:46:38 ian-latitude kernel: [    1.828000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 15 10:46:38 ian-latitude kernel: [    1.828000] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 15 10:46:38 ian-latitude kernel: [    1.832000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr 15 10:46:38 ian-latitude kernel: [    1.832000] input: Macintosh mouse button emulation as /class/input/input0
Apr 15 10:46:38 ian-latitude kernel: [    1.832000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Apr 15 10:46:38 ian-latitude kernel: [    1.832000] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 15 10:46:38 ian-latitude kernel: [    1.832000] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 15 10:46:38 ian-latitude kernel: [    1.836000] mice: PS/2 mouse device common for all mice
Apr 15 10:46:38 ian-latitude kernel: [    1.836000] EISA: Probing bus 0 at eisa.0
Apr 15 10:46:38 ian-latitude kernel: [    1.836000] EISA: Cannot allocate resource for mainboard
Apr 15 10:46:38 ian-latitude kernel: [    1.836000] Cannot allocate resource for EISA slot 1
Apr 15 10:46:38 ian-latitude kernel: [    1.836000] Cannot allocate resource for EISA slot 2
Apr 15 10:46:38 ian-latitude kernel: [    1.836000] EISA: Detected 0 cards.
Apr 15 10:46:38 ian-latitude kernel: [    1.836000] TCP cubic registered
Apr 15 10:46:38 ian-latitude kernel: [    1.836000] NET: Registered protocol family 1
Apr 15 10:46:38 ian-latitude kernel: [    1.836000] Using IPI No-Shortcut mode
Apr 15 10:46:38 ian-latitude kernel: [    1.836000]   Magic number: 4:409:780
Apr 15 10:46:38 ian-latitude kernel: [    1.836000]   hash matches device ptyq2
Apr 15 10:46:38 ian-latitude kernel: [    1.836000] Freeing unused kernel memory: 364k freed
Apr 15 10:46:38 ian-latitude kernel: [    1.836000] input: AT Translated Set 2 keyboard as /class/input/input1
Apr 15 10:46:38 ian-latitude kernel: [    3.008000] AppArmor: AppArmor initialized<5>audit(1208256385.792:2):  type=1505 info="AppArmor initialized" pid=1262
Apr 15 10:46:38 ian-latitude kernel: [    3.016000] fuse init (API version 7.8)
Apr 15 10:46:38 ian-latitude kernel: [    3.020000] Failure registering capabilities with primary security module.
Apr 15 10:46:38 ian-latitude kernel: [    3.052000] ACPI: SSDT 7FE82138, 0244 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
Apr 15 10:46:38 ian-latitude kernel: [    3.052000] ACPI: SSDT 7FE81EED, 01C6 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
Apr 15 10:46:38 ian-latitude kernel: [    3.052000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Apr 15 10:46:38 ian-latitude kernel: [    3.052000] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr 15 10:46:38 ian-latitude kernel: [    3.052000] ACPI: SSDT 7FE8237C, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
Apr 15 10:46:38 ian-latitude kernel: [    3.052000] ACPI: SSDT 7FE820B3, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
Apr 15 10:46:38 ian-latitude kernel: [    3.052000] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Apr 15 10:46:38 ian-latitude kernel: [    3.052000] ACPI: Processor [CPU1] (supports 8 throttling states)
Apr 15 10:46:38 ian-latitude kernel: [    3.056000] ACPI: Thermal Zone [THM] (49 C)
Apr 15 10:46:38 ian-latitude kernel: [    3.420000] usbcore: registered new interface driver usbfs
Apr 15 10:46:38 ian-latitude kernel: [    3.420000] usbcore: registered new interface driver hub
Apr 15 10:46:38 ian-latitude kernel: [    3.420000] usbcore: registered new device driver usb
Apr 15 10:46:38 ian-latitude kernel: [    3.420000] USB Universal Host Controller Interface driver v3.0
Apr 15 10:46:38 ian-latitude kernel: [    3.420000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 19
Apr 15 10:46:38 ian-latitude kernel: [    3.420000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Apr 15 10:46:38 ian-latitude kernel: [    3.420000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Apr 15 10:46:38 ian-latitude kernel: [    3.420000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Apr 15 10:46:38 ian-latitude kernel: [    3.420000] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000bf80
Apr 15 10:46:38 ian-latitude kernel: [    3.420000] usb usb1: configuration #1 chosen from 1 choice
Apr 15 10:46:38 ian-latitude kernel: [    3.420000] hub 1-0:1.0: USB hub found
Apr 15 10:46:38 ian-latitude kernel: [    3.420000] hub 1-0:1.0: 2 ports detected
Apr 15 10:46:38 ian-latitude kernel: [    3.432000] SCSI subsystem initialized
Apr 15 10:46:38 ian-latitude kernel: [    3.436000] libata version 2.21 loaded.
Apr 15 10:46:38 ian-latitude kernel: [    3.524000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 20
Apr 15 10:46:38 ian-latitude kernel: [    3.524000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Apr 15 10:46:38 ian-latitude kernel: [    3.524000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Apr 15 10:46:38 ian-latitude kernel: [    3.524000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Apr 15 10:46:38 ian-latitude kernel: [    3.524000] uhci_hcd 0000:00:1d.1: irq 20, io base 0x0000bf60
Apr 15 10:46:38 ian-latitude kernel: [    3.524000] usb usb2: configuration #1 chosen from 1 choice
Apr 15 10:46:38 ian-latitude kernel: [    3.524000] hub 2-0:1.0: USB hub found
Apr 15 10:46:38 ian-latitude kernel: [    3.524000] hub 2-0:1.0: 2 ports detected
Apr 15 10:46:38 ian-latitude kernel: [    3.628000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 21
Apr 15 10:46:38 ian-latitude kernel: [    3.628000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Apr 15 10:46:38 ian-latitude kernel: [    3.628000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Apr 15 10:46:38 ian-latitude kernel: [    3.628000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Apr 15 10:46:38 ian-latitude kernel: [    3.628000] uhci_hcd 0000:00:1d.2: irq 21, io base 0x0000bf40
Apr 15 10:46:38 ian-latitude kernel: [    3.628000] usb usb3: configuration #1 chosen from 1 choice
Apr 15 10:46:38 ian-latitude kernel: [    3.628000] hub 3-0:1.0: USB hub found
Apr 15 10:46:38 ian-latitude kernel: [    3.628000] hub 3-0:1.0: 2 ports detected
Apr 15 10:46:38 ian-latitude kernel: [    3.732000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 22
Apr 15 10:46:38 ian-latitude kernel: [    3.732000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
Apr 15 10:46:38 ian-latitude kernel: [    3.732000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Apr 15 10:46:38 ian-latitude kernel: [    3.732000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Apr 15 10:46:38 ian-latitude kernel: [    3.732000] uhci_hcd 0000:00:1d.3: irq 22, io base 0x0000bf20
Apr 15 10:46:38 ian-latitude kernel: [    3.732000] usb usb4: configuration #1 chosen from 1 choice
Apr 15 10:46:38 ian-latitude kernel: [    3.732000] hub 4-0:1.0: USB hub found
Apr 15 10:46:38 ian-latitude kernel: [    3.732000] hub 4-0:1.0: 2 ports detected
Apr 15 10:46:38 ian-latitude kernel: [    3.768000] usb 1-2: new full speed USB device using uhci_hcd and address 2
Apr 15 10:46:38 ian-latitude kernel: [    3.836000] tg3.c:v3.77 (May 31, 2007)
Apr 15 10:46:38 ian-latitude kernel: [    3.836000] ACPI: PCI Interrupt 0000:09:00.0[A] -> GSI 18 (level, low) -> IRQ 18
Apr 15 10:46:38 ian-latitude kernel: [    3.836000] PCI: Setting latency timer of device 0000:09:00.0 to 64
Apr 15 10:46:38 ian-latitude kernel: [    3.852000] eth0: Tigon3 [partno(BCM5752KFBG) rev 6002 PHY(5752)] (PCI Express) 10/100/1000Base-T Ethernet 00:15:c5:46:59:1b
Apr 15 10:46:38 ian-latitude kernel: [    3.852000] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
Apr 15 10:46:38 ian-latitude kernel: [    3.852000] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Apr 15 10:46:38 ian-latitude kernel: [    3.852000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 19
Apr 15 10:46:38 ian-latitude kernel: [    3.852000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Apr 15 10:46:38 ian-latitude kernel: [    3.852000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Apr 15 10:46:38 ian-latitude kernel: [    3.852000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Apr 15 10:46:38 ian-latitude kernel: [    3.852000] ehci_hcd 0000:00:1d.7: debug port 1
Apr 15 10:46:38 ian-latitude kernel: [    3.852000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Apr 15 10:46:38 ian-latitude kernel: [    3.852000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xffa80000
Apr 15 10:46:38 ian-latitude kernel: [    3.884000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Apr 15 10:46:38 ian-latitude kernel: [    3.884000] usb usb5: configuration #1 chosen from 1 choice
Apr 15 10:46:38 ian-latitude kernel: [    3.884000] hub 5-0:1.0: USB hub found
Apr 15 10:46:38 ian-latitude kernel: [    3.884000] hub 5-0:1.0: 8 ports detected
Apr 15 10:46:38 ian-latitude kernel: [    3.988000] ata_piix 0000:00:1f.2: version 2.11
Apr 15 10:46:38 ian-latitude kernel: [    3.988000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
Apr 15 10:46:38 ian-latitude kernel: [    3.988000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
Apr 15 10:46:38 ian-latitude kernel: [    3.988000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Apr 15 10:46:38 ian-latitude kernel: [    3.988000] scsi0 : ata_piix
Apr 15 10:46:38 ian-latitude kernel: [    3.988000] scsi1 : ata_piix
Apr 15 10:46:38 ian-latitude kernel: [    3.988000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
Apr 15 10:46:38 ian-latitude kernel: [    3.988000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
Apr 15 10:46:38 ian-latitude kernel: [    4.152000] ata1.00: ATA-8: FUJITSU MHY2080BH, 0085000B, max UDMA/100
Apr 15 10:46:38 ian-latitude kernel: [    4.152000] ata1.00: 156301488 sectors, multi 8: LBA48 NCQ (depth 0/32)
Apr 15 10:46:38 ian-latitude kernel: [    4.168000] ata1.00: configured for UDMA/100
Apr 15 10:46:38 ian-latitude kernel: [    4.292000] usb 1-2: device not accepting address 2, error -71
Apr 15 10:46:38 ian-latitude kernel: [    4.488000] ata2.00: ATAPI: HL-DT-ST  GCR-8240N, 1.10, max UDMA/33
Apr 15 10:46:38 ian-latitude kernel: [    4.660000] ata2.00: configured for UDMA/33
Apr 15 10:46:38 ian-latitude kernel: [    4.660000] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHY2080B 0085 PQ: 0 ANSI: 5
Apr 15 10:46:38 ian-latitude kernel: [    4.660000] scsi 1:0:0:0: CD-ROM            HL-DT-ST CD-ROM GCR-8240N 1.10 PQ: 0 ANSI: 5
Apr 15 10:46:38 ian-latitude kernel: [    4.668000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 10:46:38 ian-latitude kernel: [    4.668000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 10:46:38 ian-latitude kernel: [    4.668000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 10:46:38 ian-latitude kernel: [    4.668000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 10:46:38 ian-latitude kernel: [    4.668000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 10:46:38 ian-latitude kernel: [    4.668000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 10:46:38 ian-latitude kernel: [    4.668000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 10:46:38 ian-latitude kernel: [    4.668000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 10:46:38 ian-latitude kernel: [    4.668000]  sda: sda1 sda2 sda3 sda4
Apr 15 10:46:38 ian-latitude kernel: [    4.688000] sd 0:0:0:0: [sda] Attached SCSI disk
Apr 15 10:46:38 ian-latitude kernel: [    4.692000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 15 10:46:38 ian-latitude kernel: [    4.692000] sr 1:0:0:0: Attached scsi generic sg1 type 5
Apr 15 10:46:38 ian-latitude kernel: [    4.696000] sr0: scsi3-mmc drive: 24x/24x cd/rw xa/form2 cdda tray
Apr 15 10:46:38 ian-latitude kernel: [    4.696000] Uniform CD-ROM driver Revision: 3.20
Apr 15 10:46:38 ian-latitude kernel: [    4.696000] sr 1:0:0:0: Attached scsi CD-ROM sr0
Apr 15 10:46:38 ian-latitude kernel: [    5.024000] usb 1-2: new full speed USB device using uhci_hcd and address 4
Apr 15 10:46:38 ian-latitude kernel: [    5.052000] Attempting manual resume
Apr 15 10:46:38 ian-latitude kernel: [    5.052000] swsusp: Resume From Partition 8:2
Apr 15 10:46:38 ian-latitude kernel: [    5.052000] PM: Checking swsusp image.
Apr 15 10:46:38 ian-latitude kernel: [    5.052000] PM: Resume from disk failed.
Apr 15 10:46:38 ian-latitude kernel: [    5.084000] kjournald starting.  Commit interval 5 seconds
Apr 15 10:46:38 ian-latitude kernel: [    5.084000] EXT3-fs: mounted filesystem with ordered data mode.
Apr 15 10:46:38 ian-latitude kernel: [    5.180000] usb 1-2: configuration #1 chosen from 1 choice
Apr 15 10:46:38 ian-latitude kernel: [    5.184000] hub 1-2:1.0: USB hub found
Apr 15 10:46:38 ian-latitude kernel: [    5.184000] hub 1-2:1.0: 4 ports detected
Apr 15 10:46:38 ian-latitude kernel: [    5.516000] usb 1-2.3: new full speed USB device using uhci_hcd and address 5
Apr 15 10:46:38 ian-latitude kernel: [    5.644000] usb 1-2.3: configuration #1 chosen from 1 choice
Apr 15 10:46:38 ian-latitude kernel: [    5.648000] hub 1-2.3:1.0: USB hub found
Apr 15 10:46:38 ian-latitude kernel: [    5.648000] hub 1-2.3:1.0: 3 ports detected
Apr 15 10:46:38 ian-latitude kernel: [    5.976000] usb 1-2.4: new full speed USB device using uhci_hcd and address 6
Apr 15 10:46:38 ian-latitude kernel: [    6.144000] usb 1-2.4: configuration #1 chosen from 1 choice
Apr 15 10:46:38 ian-latitude kernel: [    6.352000] usb 1-2.3.2: new full speed USB device using uhci_hcd and address 7
Apr 15 10:46:38 ian-latitude kernel: [    6.472000] usb 1-2.3.2: configuration #1 chosen from 1 choice
Apr 15 10:46:38 ian-latitude kernel: [   11.136000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr 15 10:46:38 ian-latitude kernel: [   11.184000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr 15 10:46:38 ian-latitude kernel: [   11.200000] Linux agpgart interface v0.102 (c) Dave Jones
Apr 15 10:46:38 ian-latitude kernel: [   11.208000] intel_rng: FWH not detected
Apr 15 10:46:38 ian-latitude kernel: [   11.416000] Yenta: CardBus bridge found at 0000:03:01.0 [1028:01c2]
Apr 15 10:46:38 ian-latitude kernel: [   11.416000] Yenta O2: res at 0x94/0xD4: 00/ea
Apr 15 10:46:38 ian-latitude kernel: [   11.416000] Yenta O2: enabling read prefetch/write burst
Apr 15 10:46:38 ian-latitude kernel: [   11.436000] iTCO_vendor_support: vendor-support=0
Apr 15 10:46:38 ian-latitude kernel: [   11.436000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
Apr 15 10:46:38 ian-latitude kernel: [   11.544000] Yenta: ISA IRQ mask 0x0cb8, PCI irq 18
Apr 15 10:46:38 ian-latitude kernel: [   11.544000] Socket status: 30000006
Apr 15 10:46:38 ian-latitude kernel: [   11.544000] Yenta: Raising subordinate bus# of parent bus (#03) from #04 to #07
Apr 15 10:46:38 ian-latitude kernel: [   11.544000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
Apr 15 10:46:38 ian-latitude kernel: [   11.544000] cs: IO port probe 0x2000-0x2fff: clean.
Apr 15 10:46:38 ian-latitude kernel: [   11.544000] pcmcia: parent PCI bridge Memory window: 0x8c000000 - 0x91ffffff
Apr 15 10:46:38 ian-latitude kernel: [   11.544000] pcmcia: parent PCI bridge Memory window: 0x88000000 - 0x8bffffff
Apr 15 10:46:38 ian-latitude kernel: [   11.604000] Bluetooth: Core ver 2.11
Apr 15 10:46:38 ian-latitude kernel: [   11.604000] NET: Registered protocol family 31
Apr 15 10:46:38 ian-latitude kernel: [   11.604000] Bluetooth: HCI device and connection manager initialized
Apr 15 10:46:38 ian-latitude kernel: [   11.604000] Bluetooth: HCI socket layer initialized
Apr 15 10:46:38 ian-latitude kernel: [   11.660000] Bluetooth: HCI USB driver ver 2.9
Apr 15 10:46:38 ian-latitude kernel: [   11.664000] usbcore: registered new interface driver hci_usb
Apr 15 10:46:38 ian-latitude kernel: [   11.688000] ieee80211_crypt: registered algorithm 'NULL'
Apr 15 10:46:38 ian-latitude kernel: [   11.692000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Apr 15 10:46:38 ian-latitude kernel: [   11.692000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Apr 15 10:46:38 ian-latitude kernel: [   11.708000] nvidia: module license 'NVIDIA' taints kernel.
Apr 15 10:46:38 ian-latitude kernel: [   11.960000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 15 10:46:38 ian-latitude kernel: [   11.960000] PCI: Setting latency timer of device 0000:01:00.0 to 64
Apr 15 10:46:38 ian-latitude kernel: [   11.960000] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
Apr 15 10:46:38 ian-latitude kernel: [   12.040000] cs: IO port probe 0x100-0x3af: clean.
Apr 15 10:46:38 ian-latitude kernel: [   12.040000] cs: IO port probe 0x3e0-0x4ff: clean.
Apr 15 10:46:38 ian-latitude kernel: [   12.044000] cs: IO port probe 0x820-0x8ff: clean.
Apr 15 10:46:38 ian-latitude kernel: [   12.044000] cs: IO port probe 0xc00-0xcf7: clean.
Apr 15 10:46:38 ian-latitude kernel: [   12.044000] cs: IO port probe 0xa00-0xaff: clean.
Apr 15 10:46:38 ian-latitude kernel: [   12.120000] bcm43xx driver
Apr 15 10:46:38 ian-latitude kernel: [   12.120000] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Apr 15 10:46:38 ian-latitude kernel: [   12.120000] PCI: Setting latency timer of device 0000:0c:00.0 to 64
Apr 15 10:46:38 ian-latitude kernel: [   12.152000] input: PS/2 Mouse as /class/input/input2
Apr 15 10:46:38 ian-latitude kernel: [   12.172000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input3
Apr 15 10:46:38 ian-latitude kernel: [   12.176000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
Apr 15 10:46:38 ian-latitude kernel: [   12.176000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Apr 15 10:46:38 ian-latitude kernel: [   12.176000] input: PC Speaker as /class/input/input4
Apr 15 10:46:38 ian-latitude kernel: [   12.316000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 20
Apr 15 10:46:38 ian-latitude kernel: [   12.316000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Apr 15 10:46:38 ian-latitude kernel: [   12.928000] lp: driver loaded but no devices found
Apr 15 10:46:38 ian-latitude kernel: [   12.960000] Adding 1951888k swap on /dev/sda2.  Priority:-1 extents:1 across:1951888k
Apr 15 10:46:38 ian-latitude kernel: [   13.312000] EXT3 FS on sda3, internal journal
Apr 15 10:46:38 ian-latitude kernel: [   14.476000] ACPI: ACPI Dock Station Driver 
Apr 15 10:46:38 ian-latitude kernel: [   14.496000] ACPI: \_SB_.PCI0.IDE0.SEC0.MAST: found ejectable bay
Apr 15 10:46:38 ian-latitude kernel: [   14.496000] ACPI: \_SB_.PCI0.IDE0.SEC0.MAST: Adding notify handler
Apr 15 10:46:38 ian-latitude kernel: [   14.496000] ACPI: Error installing bay notify handler
Apr 15 10:46:38 ian-latitude kernel: [   14.496000] ACPI: Bay [\_SB_.PCI0.IDE0.SEC0.MAST] Added
Apr 15 10:46:38 ian-latitude kernel: [   14.512000] input: Lid Switch as /class/input/input5
Apr 15 10:46:38 ian-latitude kernel: [   14.512000] ACPI: Lid Switch [LID]
Apr 15 10:46:38 ian-latitude kernel: [   14.512000] input: Power Button (CM) as /class/input/input6
Apr 15 10:46:38 ian-latitude kernel: [   14.512000] ACPI: Power Button (CM) [PBTN]
Apr 15 10:46:38 ian-latitude kernel: [   14.512000] input: Sleep Button (CM) as /class/input/input7
Apr 15 10:46:38 ian-latitude kernel: [   14.512000] ACPI: Sleep Button (CM) [SBTN]
Apr 15 10:46:38 ian-latitude kernel: [   14.600000] ACPI: AC Adapter [AC] (on-line)
Apr 15 10:46:38 ian-latitude kernel: [   14.636000] ACPI: Battery Slot [BAT0] (battery present)
Apr 15 10:46:38 ian-latitude kernel: [   14.636000] ACPI: Battery Slot [BAT1] (battery absent)
Apr 15 10:46:38 ian-latitude kernel: [   14.712000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Apr 15 10:46:38 ian-latitude kernel: [   14.716000] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
Apr 15 10:46:38 ian-latitude kernel: [   14.716000] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
Apr 15 10:46:39 ian-latitude kernel: [   15.908000] ppdev: user-space parallel port driver
Apr 15 10:46:39 ian-latitude kernel: [   16.272000] audit(1208270799.021:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5074 profile="/usr/sbin/cupsd"
Apr 15 10:46:39 ian-latitude kernel: [   16.352000] apm: BIOS not found.
Apr 15 10:46:41 ian-latitude kernel: [   17.824000] /dev/vmmon[5459]: Module vmmon: registered with major=10 minor=165
Apr 15 10:46:41 ian-latitude kernel: [   17.824000] /dev/vmmon[5459]: Module vmmon: initialized
Apr 15 10:46:41 ian-latitude kernel: [   17.912000] /dev/vmnet: open called by PID 5486 (vmnet-bridge)
Apr 15 10:46:41 ian-latitude kernel: [   17.912000] /dev/vmnet: hub 0 does not exist, allocating memory.
Apr 15 10:46:41 ian-latitude kernel: [   17.912000] /dev/vmnet: port on hub 0 successfully opened
Apr 15 10:46:41 ian-latitude kernel: [   17.912000] bridge-eth0: enabling the bridge
Apr 15 10:46:41 ian-latitude kernel: [   17.912000] bridge-eth0: up
Apr 15 10:46:41 ian-latitude kernel: [   17.912000] bridge-eth0: already up
Apr 15 10:46:41 ian-latitude kernel: [   17.912000] bridge-eth0: attached
Apr 15 10:46:41 ian-latitude kernel: [   17.984000] /dev/vmnet: open called by PID 5500 (vmnet-natd)
Apr 15 10:46:41 ian-latitude kernel: [   17.984000] /dev/vmnet: hub 8 does not exist, allocating memory.
Apr 15 10:46:41 ian-latitude kernel: [   17.984000] /dev/vmnet: port on hub 8 successfully opened
Apr 15 10:46:41 ian-latitude kernel: [   17.984000] /dev/vmnet: open called by PID 5501 (vmnet-netifup)
Apr 15 10:46:41 ian-latitude kernel: [   17.984000] /dev/vmnet: hub 1 does not exist, allocating memory.
Apr 15 10:46:41 ian-latitude kernel: [   17.984000] /dev/vmnet: port on hub 1 successfully opened
Apr 15 10:46:41 ian-latitude kernel: [   17.984000] /dev/vmnet: open called by PID 5502 (vmnet-netifup)
Apr 15 10:46:41 ian-latitude kernel: [   17.988000] /dev/vmnet: port on hub 8 successfully opened
Apr 15 10:46:41 ian-latitude kernel: [   18.432000] tg3: eth0: Link is up at 100 Mbps, full duplex.
Apr 15 10:46:41 ian-latitude kernel: [   18.432000] tg3: eth0: Flow control is on for TX and on for RX.
Apr 15 10:46:41 ian-latitude kernel: [   18.644000] /dev/vmnet: open called by PID 5528 (vmnet-dhcpd)
Apr 15 10:46:41 ian-latitude kernel: [   18.644000] /dev/vmnet: port on hub 1 successfully opened
Apr 15 10:46:41 ian-latitude kernel: [   18.724000] /dev/vmnet: open called by PID 5529 (vmnet-dhcpd)
Apr 15 10:46:41 ian-latitude kernel: [   18.724000] /dev/vmnet: port on hub 8 successfully opened
Apr 15 10:46:42 ian-latitude kernel: [   18.840000] Failure registering capabilities with primary security module.
Apr 15 10:46:42 ian-latitude kernel: [   19.296000] Bluetooth: L2CAP ver 2.8
Apr 15 10:46:42 ian-latitude kernel: [   19.296000] Bluetooth: L2CAP socket layer initialized
Apr 15 10:46:42 ian-latitude kernel: [   19.480000] Bluetooth: RFCOMM socket layer initialized
Apr 15 10:46:42 ian-latitude kernel: [   19.480000] Bluetooth: RFCOMM TTY layer initialized
Apr 15 10:46:42 ian-latitude kernel: [   19.480000] Bluetooth: RFCOMM ver 1.8
Apr 15 10:46:47 ian-latitude kernel: [   24.432000] NET: Registered protocol family 17
Apr 15 10:46:49 ian-latitude kernel: [   26.360000] NET: Registered protocol family 10
Apr 15 10:46:49 ian-latitude kernel: [   26.360000] lo: Disabled Privacy Extensions
Apr 15 10:46:49 ian-latitude kernel: [   26.360000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 15 10:47:00 ian-latitude kernel: [   36.744000] vmnet1: no IPv6 routers present
Apr 15 10:47:01 ian-latitude kernel: [   36.888000] eth0: no IPv6 routers present
Apr 15 10:47:01 ian-latitude kernel: [   37.196000] vmnet8: no IPv6 routers present
Apr 15 10:48:05 ian-latitude kernel: [  100.932000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:48:05 ian-latitude kernel: [  100.932000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:48:05 ian-latitude kernel: [  100.932000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:48:05 ian-latitude kernel: [  100.932000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:48:05 ian-latitude kernel: [  100.956000] ata1.00: configured for UDMA/100
Apr 15 10:48:05 ian-latitude kernel: [  100.956000] ata1: EH complete
Apr 15 10:48:09 ian-latitude kernel: [  105.500000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:48:09 ian-latitude kernel: [  105.500000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:48:09 ian-latitude kernel: [  105.500000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:48:09 ian-latitude kernel: [  105.500000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:48:09 ian-latitude kernel: [  105.524000] ata1.00: configured for UDMA/100
Apr 15 10:48:09 ian-latitude kernel: [  105.524000] ata1: EH complete
Apr 15 10:48:14 ian-latitude kernel: [  109.956000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:48:14 ian-latitude kernel: [  109.956000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:48:14 ian-latitude kernel: [  109.956000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:48:14 ian-latitude kernel: [  109.956000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:48:14 ian-latitude kernel: [  109.980000] ata1.00: configured for UDMA/100
Apr 15 10:48:14 ian-latitude kernel: [  109.980000] ata1: EH complete
Apr 15 10:48:18 ian-latitude kernel: [  114.188000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:48:18 ian-latitude kernel: [  114.188000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:48:18 ian-latitude kernel: [  114.188000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:48:18 ian-latitude kernel: [  114.188000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:48:18 ian-latitude kernel: [  114.212000] ata1.00: configured for UDMA/100
Apr 15 10:48:18 ian-latitude kernel: [  114.212000] ata1: EH complete
Apr 15 10:48:22 ian-latitude kernel: [  118.644000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:48:22 ian-latitude kernel: [  118.644000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:48:22 ian-latitude kernel: [  118.644000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:48:22 ian-latitude kernel: [  118.644000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:48:22 ian-latitude kernel: [  118.672000] ata1.00: configured for UDMA/100
Apr 15 10:48:22 ian-latitude kernel: [  118.672000] ata1: EH complete
Apr 15 10:48:27 ian-latitude kernel: [  123.112000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:48:27 ian-latitude kernel: [  123.112000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:48:27 ian-latitude kernel: [  123.112000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:48:27 ian-latitude kernel: [  123.112000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:48:27 ian-latitude kernel: [  123.140000] ata1.00: configured for UDMA/100
Apr 15 10:48:27 ian-latitude kernel: [  123.140000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Apr 15 10:48:27 ian-latitude kernel: [  123.140000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Apr 15 10:48:27 ian-latitude kernel: [  123.140000] Descriptor sense data with sense descriptors (in hex):
Apr 15 10:48:27 ian-latitude kernel: [  123.140000]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr 15 10:48:27 ian-latitude kernel: [  123.140000]         02 57 e2 83 
Apr 15 10:48:27 ian-latitude kernel: [  123.140000] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
Apr 15 10:48:27 ian-latitude kernel: [  123.140000] end_request: I/O error, dev sda, sector 39314051
Apr 15 10:48:27 ian-latitude kernel: [  123.140000] ata1: EH complete
Apr 15 10:48:27 ian-latitude kernel: [  123.160000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 10:48:27 ian-latitude kernel: [  123.160000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 10:48:27 ian-latitude kernel: [  123.160000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 10:48:27 ian-latitude kernel: [  123.160000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 10:48:27 ian-latitude kernel: [  123.160000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 10:48:27 ian-latitude kernel: [  123.160000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 10:48:27 ian-latitude kernel: [  123.160000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 10:48:27 ian-latitude kernel: [  123.160000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 10:48:31 ian-latitude kernel: [  127.724000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:48:31 ian-latitude kernel: [  127.724000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:48:31 ian-latitude kernel: [  127.724000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:48:31 ian-latitude kernel: [  127.724000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:48:32 ian-latitude kernel: [  128.036000] ata1.00: configured for UDMA/100
Apr 15 10:48:32 ian-latitude kernel: [  128.036000] ata1: EH complete
Apr 15 10:48:36 ian-latitude kernel: [  132.480000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:48:36 ian-latitude kernel: [  132.480000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:48:36 ian-latitude kernel: [  132.480000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:48:36 ian-latitude kernel: [  132.480000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:48:36 ian-latitude kernel: [  132.508000] ata1.00: configured for UDMA/100
Apr 15 10:48:36 ian-latitude kernel: [  132.508000] ata1: EH complete
Apr 15 10:48:41 ian-latitude kernel: [  136.940000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:48:41 ian-latitude kernel: [  136.940000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:48:41 ian-latitude kernel: [  136.940000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:48:41 ian-latitude kernel: [  136.940000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:48:41 ian-latitude kernel: [  136.964000] ata1.00: configured for UDMA/100
Apr 15 10:48:41 ian-latitude kernel: [  136.964000] ata1: EH complete
Apr 15 10:48:45 ian-latitude kernel: [  141.196000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:48:45 ian-latitude kernel: [  141.196000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:48:45 ian-latitude kernel: [  141.196000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:48:45 ian-latitude kernel: [  141.196000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:48:45 ian-latitude kernel: [  141.220000] ata1.00: configured for UDMA/100
Apr 15 10:48:45 ian-latitude kernel: [  141.220000] ata1: EH complete
Apr 15 10:48:50 ian-latitude kernel: [  146.028000] ata1.00: limiting speed to UDMA/66:PIO4
Apr 15 10:48:50 ian-latitude kernel: [  146.028000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
Apr 15 10:48:50 ian-latitude kernel: [  146.028000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:48:50 ian-latitude kernel: [  146.028000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:48:50 ian-latitude kernel: [  146.028000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:48:50 ian-latitude kernel: [  146.028000] ata1: soft resetting port
Apr 15 10:48:50 ian-latitude kernel: [  146.224000] ata1.00: configured for UDMA/66
Apr 15 10:48:50 ian-latitude kernel: [  146.224000] ata1: EH complete
Apr 15 10:48:54 ian-latitude kernel: [  150.520000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:48:54 ian-latitude kernel: [  150.520000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:48:54 ian-latitude kernel: [  150.520000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:48:54 ian-latitude kernel: [  150.520000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:48:54 ian-latitude kernel: [  150.544000] ata1.00: configured for UDMA/66
Apr 15 10:48:54 ian-latitude kernel: [  150.544000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Apr 15 10:48:54 ian-latitude kernel: [  150.544000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Apr 15 10:48:54 ian-latitude kernel: [  150.544000] Descriptor sense data with sense descriptors (in hex):
Apr 15 10:48:54 ian-latitude kernel: [  150.544000]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr 15 10:48:54 ian-latitude kernel: [  150.544000]         02 57 e2 83 
Apr 15 10:48:54 ian-latitude kernel: [  150.544000] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
Apr 15 10:48:54 ian-latitude kernel: [  150.544000] end_request: I/O error, dev sda, sector 39314051
Apr 15 10:48:54 ian-latitude kernel: [  150.544000] ata1: EH complete
Apr 15 10:48:54 ian-latitude kernel: [  150.560000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 10:48:54 ian-latitude kernel: [  150.560000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 10:48:54 ian-latitude kernel: [  150.560000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 10:48:54 ian-latitude kernel: [  150.572000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 10:48:54 ian-latitude kernel: [  150.584000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 10:48:54 ian-latitude kernel: [  150.592000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 10:48:54 ian-latitude kernel: [  150.592000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 10:48:54 ian-latitude kernel: [  150.608000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 10:48:59 ian-latitude kernel: [  155.064000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:48:59 ian-latitude kernel: [  155.064000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:48:59 ian-latitude kernel: [  155.064000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:48:59 ian-latitude kernel: [  155.064000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:48:59 ian-latitude kernel: [  155.152000] ata1.00: configured for UDMA/66
Apr 15 10:48:59 ian-latitude kernel: [  155.152000] ata1: EH complete
Apr 15 10:49:03 ian-latitude kernel: [  159.588000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:49:03 ian-latitude kernel: [  159.588000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:49:03 ian-latitude kernel: [  159.588000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:49:03 ian-latitude kernel: [  159.588000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:49:03 ian-latitude kernel: [  159.612000] ata1.00: configured for UDMA/66
Apr 15 10:49:03 ian-latitude kernel: [  159.612000] ata1: EH complete
Apr 15 10:49:08 ian-latitude kernel: [  164.032000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:49:08 ian-latitude kernel: [  164.032000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:49:08 ian-latitude kernel: [  164.032000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:49:08 ian-latitude kernel: [  164.032000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:49:08 ian-latitude kernel: [  164.056000] ata1.00: configured for UDMA/66
Apr 15 10:49:08 ian-latitude kernel: [  164.056000] ata1: EH complete
Apr 15 10:49:12 ian-latitude kernel: [  168.488000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:49:12 ian-latitude kernel: [  168.488000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:49:12 ian-latitude kernel: [  168.488000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:49:12 ian-latitude kernel: [  168.488000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:49:12 ian-latitude kernel: [  168.512000] ata1.00: configured for UDMA/66
Apr 15 10:49:12 ian-latitude kernel: [  168.512000] ata1: EH complete
Apr 15 10:49:17 ian-latitude kernel: [  173.056000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:49:17 ian-latitude kernel: [  173.056000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:49:17 ian-latitude kernel: [  173.056000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:49:17 ian-latitude kernel: [  173.056000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:49:17 ian-latitude kernel: [  173.080000] ata1.00: configured for UDMA/66
Apr 15 10:49:17 ian-latitude kernel: [  173.080000] ata1: EH complete
Apr 15 10:49:21 ian-latitude kernel: [  177.536000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:49:21 ian-latitude kernel: [  177.536000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:49:21 ian-latitude kernel: [  177.536000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:49:21 ian-latitude kernel: [  177.536000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:49:21 ian-latitude kernel: [  177.564000] ata1.00: configured for UDMA/66
Apr 15 10:49:21 ian-latitude kernel: [  177.564000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Apr 15 10:49:21 ian-latitude kernel: [  177.564000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Apr 15 10:49:21 ian-latitude kernel: [  177.564000] Descriptor sense data with sense descriptors (in hex):
Apr 15 10:49:21 ian-latitude kernel: [  177.564000]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr 15 10:49:21 ian-latitude kernel: [  177.564000]         02 57 e2 83 
Apr 15 10:49:21 ian-latitude kernel: [  177.564000] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
Apr 15 10:49:21 ian-latitude kernel: [  177.564000] end_request: I/O error, dev sda, sector 39314051
Apr 15 10:49:21 ian-latitude kernel: [  177.564000] ata1: EH complete
Apr 15 10:49:21 ian-latitude kernel: [  177.564000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 10:49:21 ian-latitude kernel: [  177.564000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 10:49:21 ian-latitude kernel: [  177.564000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 10:49:21 ian-latitude kernel: [  177.564000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 10:49:21 ian-latitude kernel: [  177.564000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 10:49:21 ian-latitude kernel: [  177.580000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 10:49:21 ian-latitude kernel: [  177.580000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 10:49:21 ian-latitude kernel: [  177.580000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 10:49:26 ian-latitude kernel: [  182.080000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:49:26 ian-latitude kernel: [  182.080000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:49:26 ian-latitude kernel: [  182.080000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:49:26 ian-latitude kernel: [  182.080000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:49:26 ian-latitude kernel: [  182.144000] ata1.00: configured for UDMA/66
Apr 15 10:49:26 ian-latitude kernel: [  182.144000] ata1: EH complete
Apr 15 10:49:30 ian-latitude kernel: [  186.592000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:49:30 ian-latitude kernel: [  186.592000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:49:30 ian-latitude kernel: [  186.592000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:49:30 ian-latitude kernel: [  186.592000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:49:30 ian-latitude kernel: [  186.616000] ata1.00: configured for UDMA/66
Apr 15 10:49:30 ian-latitude kernel: [  186.616000] ata1: EH complete
Apr 15 10:49:35 ian-latitude kernel: [  191.084000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:49:35 ian-latitude kernel: [  191.084000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:49:35 ian-latitude kernel: [  191.084000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:49:35 ian-latitude kernel: [  191.084000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:49:35 ian-latitude kernel: [  191.108000] ata1.00: configured for UDMA/66
Apr 15 10:49:35 ian-latitude kernel: [  191.108000] ata1: EH complete
Apr 15 10:49:39 ian-latitude kernel: [  195.640000] ata1.00: limiting speed to UDMA/33:PIO4
Apr 15 10:49:39 ian-latitude kernel: [  195.640000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
Apr 15 10:49:39 ian-latitude kernel: [  195.640000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:49:39 ian-latitude kernel: [  195.640000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:49:39 ian-latitude kernel: [  195.640000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:49:39 ian-latitude kernel: [  195.640000] ata1: soft resetting port
Apr 15 10:49:39 ian-latitude kernel: [  195.836000] ata1.00: configured for UDMA/33
Apr 15 10:49:39 ian-latitude kernel: [  195.836000] ata1: EH complete
Apr 15 10:49:44 ian-latitude kernel: [  200.272000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:49:44 ian-latitude kernel: [  200.272000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:49:44 ian-latitude kernel: [  200.272000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:49:44 ian-latitude kernel: [  200.272000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:49:44 ian-latitude kernel: [  200.296000] ata1.00: configured for UDMA/33
Apr 15 10:49:44 ian-latitude kernel: [  200.296000] ata1: EH complete
Apr 15 10:49:48 ian-latitude kernel: [  204.752000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:49:48 ian-latitude kernel: [  204.752000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:49:48 ian-latitude kernel: [  204.752000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:49:48 ian-latitude kernel: [  204.752000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:49:48 ian-latitude kernel: [  204.776000] ata1.00: configured for UDMA/33
Apr 15 10:49:48 ian-latitude kernel: [  204.776000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Apr 15 10:49:48 ian-latitude kernel: [  204.776000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Apr 15 10:49:48 ian-latitude kernel: [  204.776000] Descriptor sense data with sense descriptors (in hex):
Apr 15 10:49:48 ian-latitude kernel: [  204.776000]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr 15 10:49:48 ian-latitude kernel: [  204.776000]         02 57 e2 83 
Apr 15 10:49:48 ian-latitude kernel: [  204.776000] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
Apr 15 10:49:48 ian-latitude kernel: [  204.776000] end_request: I/O error, dev sda, sector 39314051
Apr 15 10:49:48 ian-latitude kernel: [  204.776000] ata1: EH complete
Apr 15 10:49:48 ian-latitude kernel: [  204.792000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 10:49:48 ian-latitude kernel: [  204.792000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 10:49:48 ian-latitude kernel: [  204.792000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 10:49:48 ian-latitude kernel: [  204.796000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 10:49:53 ian-latitude kernel: [  209.240000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:49:53 ian-latitude kernel: [  209.240000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:49:53 ian-latitude kernel: [  209.240000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:49:53 ian-latitude kernel: [  209.240000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:49:53 ian-latitude kernel: [  209.288000] ata1.00: configured for UDMA/33
Apr 15 10:49:53 ian-latitude kernel: [  209.288000] ata1: EH complete
Apr 15 10:49:57 ian-latitude kernel: [  213.744000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:49:57 ian-latitude kernel: [  213.744000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:49:57 ian-latitude kernel: [  213.744000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:49:57 ian-latitude kernel: [  213.744000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:49:57 ian-latitude kernel: [  213.768000] ata1.00: configured for UDMA/33
Apr 15 10:49:57 ian-latitude kernel: [  213.768000] ata1: EH complete
Apr 15 10:50:02 ian-latitude kernel: [  218.276000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:50:02 ian-latitude kernel: [  218.276000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:50:02 ian-latitude kernel: [  218.276000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:50:02 ian-latitude kernel: [  218.276000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:50:02 ian-latitude kernel: [  218.300000] ata1.00: configured for UDMA/33
Apr 15 10:50:02 ian-latitude kernel: [  218.300000] ata1: EH complete
Apr 15 10:50:06 ian-latitude kernel: [  222.732000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:50:06 ian-latitude kernel: [  222.732000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:50:06 ian-latitude kernel: [  222.732000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:50:06 ian-latitude kernel: [  222.732000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:50:06 ian-latitude kernel: [  222.756000] ata1.00: configured for UDMA/33
Apr 15 10:50:06 ian-latitude kernel: [  222.756000] ata1: EH complete
Apr 15 10:50:11 ian-latitude kernel: [  227.556000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:50:11 ian-latitude kernel: [  227.556000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:50:11 ian-latitude kernel: [  227.556000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:50:11 ian-latitude kernel: [  227.556000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:50:11 ian-latitude kernel: [  227.580000] ata1.00: configured for UDMA/33
Apr 15 10:50:11 ian-latitude kernel: [  227.580000] ata1: EH complete
Apr 15 10:50:16 ian-latitude kernel: [  232.000000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:50:16 ian-latitude kernel: [  232.000000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:50:16 ian-latitude kernel: [  232.000000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:50:16 ian-latitude kernel: [  232.000000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:50:16 ian-latitude kernel: [  232.024000] ata1.00: configured for UDMA/33
Apr 15 10:50:16 ian-latitude kernel: [  232.024000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Apr 15 10:50:16 ian-latitude kernel: [  232.024000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Apr 15 10:50:16 ian-latitude kernel: [  232.024000] Descriptor sense data with sense descriptors (in hex):
Apr 15 10:50:16 ian-latitude kernel: [  232.024000]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr 15 10:50:16 ian-latitude kernel: [  232.024000]         02 57 e2 83 
Apr 15 10:50:16 ian-latitude kernel: [  232.024000] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
Apr 15 10:50:16 ian-latitude kernel: [  232.024000] end_request: I/O error, dev sda, sector 39314051
Apr 15 10:50:16 ian-latitude kernel: [  232.024000] ata1: EH complete
Apr 15 10:50:20 ian-latitude kernel: [  236.480000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:50:20 ian-latitude kernel: [  236.480000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:50:20 ian-latitude kernel: [  236.480000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:50:20 ian-latitude kernel: [  236.480000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:50:20 ian-latitude kernel: [  236.504000] ata1.00: configured for UDMA/33
Apr 15 10:50:20 ian-latitude kernel: [  236.504000] ata1: EH complete
Apr 15 10:50:25 ian-latitude kernel: [  241.024000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:50:25 ian-latitude kernel: [  241.024000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:50:25 ian-latitude kernel: [  241.024000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:50:25 ian-latitude kernel: [  241.024000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:50:25 ian-latitude kernel: [  241.048000] ata1.00: configured for UDMA/33
Apr 15 10:50:25 ian-latitude kernel: [  241.048000] ata1: EH complete
Apr 15 10:50:29 ian-latitude kernel: [  245.536000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:50:29 ian-latitude kernel: [  245.536000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:50:29 ian-latitude kernel: [  245.536000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:50:29 ian-latitude kernel: [  245.536000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:50:29 ian-latitude kernel: [  245.560000] ata1.00: configured for UDMA/33
Apr 15 10:50:29 ian-latitude kernel: [  245.560000] ata1: EH complete
Apr 15 10:50:34 ian-latitude kernel: [  250.016000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:50:34 ian-latitude kernel: [  250.016000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:50:34 ian-latitude kernel: [  250.016000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:50:34 ian-latitude kernel: [  250.016000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:50:34 ian-latitude kernel: [  250.040000] ata1.00: configured for UDMA/33
Apr 15 10:50:34 ian-latitude kernel: [  250.040000] ata1: EH complete
Apr 15 10:50:38 ian-latitude kernel: [  254.508000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:50:38 ian-latitude kernel: [  254.508000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:50:38 ian-latitude kernel: [  254.508000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:50:38 ian-latitude kernel: [  254.508000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:50:38 ian-latitude kernel: [  254.532000] ata1.00: configured for UDMA/33
Apr 15 10:50:38 ian-latitude kernel: [  254.532000] ata1: EH complete
Apr 15 10:50:43 ian-latitude kernel: [  258.940000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:50:43 ian-latitude kernel: [  258.940000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:50:43 ian-latitude kernel: [  258.940000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:50:43 ian-latitude kernel: [  258.940000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:50:43 ian-latitude kernel: [  258.964000] ata1.00: configured for UDMA/33
Apr 15 10:50:43 ian-latitude kernel: [  258.964000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Apr 15 10:50:43 ian-latitude kernel: [  258.964000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Apr 15 10:50:43 ian-latitude kernel: [  258.964000] Descriptor sense data with sense descriptors (in hex):
Apr 15 10:50:43 ian-latitude kernel: [  258.964000]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr 15 10:50:43 ian-latitude kernel: [  258.964000]         02 57 e2 83 
Apr 15 10:50:43 ian-latitude kernel: [  258.964000] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
Apr 15 10:50:43 ian-latitude kernel: [  258.964000] end_request: I/O error, dev sda, sector 39314051
Apr 15 10:50:43 ian-latitude kernel: [  258.964000] ata1: EH complete
Apr 15 10:50:43 ian-latitude kernel: [  258.964000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 10:50:43 ian-latitude kernel: [  258.980000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 10:50:43 ian-latitude kernel: [  258.980000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 10:50:43 ian-latitude kernel: [  258.984000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 10:51:36 ian-latitude kernel: [  258.984000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 10:51:36 ian-latitude kernel: [  258.984000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 10:51:36 ian-latitude kernel: [  258.984000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 10:51:36 ian-latitude kernel: [  258.984000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 10:51:36 ian-latitude kernel: [  263.540000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:51:36 ian-latitude kernel: [  263.540000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:51:36 ian-latitude kernel: [  263.540000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:51:36 ian-latitude kernel: [  263.540000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:51:36 ian-latitude kernel: [  263.680000] ata1.00: configured for UDMA/33
Apr 15 10:51:36 ian-latitude kernel: [  263.680000] ata1: EH complete
Apr 15 10:51:36 ian-latitude kernel: [  268.108000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:51:36 ian-latitude kernel: [  268.108000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:51:36 ian-latitude kernel: [  268.108000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:51:36 ian-latitude kernel: [  268.108000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:52:30 ian-latitude kernel: [  268.132000] ata1.00: configured for UDMA/33
Apr 15 10:52:30 ian-latitude kernel: [  268.132000] ata1: EH complete
Apr 15 10:52:30 ian-latitude kernel: [  272.532000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:52:30 ian-latitude kernel: [  272.532000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:52:30 ian-latitude kernel: [  272.532000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:52:30 ian-latitude kernel: [  272.532000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:52:30 ian-latitude kernel: [  272.556000] ata1.00: configured for UDMA/33
Apr 15 10:52:30 ian-latitude kernel: [  272.556000] ata1: EH complete
Apr 15 10:52:30 ian-latitude kernel: [  277.000000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:52:30 ian-latitude kernel: [  277.000000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:52:30 ian-latitude kernel: [  277.000000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:52:30 ian-latitude kernel: [  277.000000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:52:30 ian-latitude kernel: [  277.024000] ata1.00: configured for UDMA/33
Apr 15 10:52:30 ian-latitude kernel: [  277.024000] ata1: EH complete
Apr 15 10:52:30 ian-latitude kernel: [  281.456000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:52:30 ian-latitude kernel: [  281.456000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:52:30 ian-latitude kernel: [  281.456000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:52:30 ian-latitude kernel: [  281.456000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:52:30 ian-latitude kernel: [  281.480000] ata1.00: configured for UDMA/33
Apr 15 10:52:30 ian-latitude kernel: [  281.480000] ata1: EH complete
Apr 15 10:52:30 ian-latitude kernel: [  286.024000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:52:30 ian-latitude kernel: [  286.024000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:52:30 ian-latitude kernel: [  286.024000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:52:30 ian-latitude kernel: [  286.024000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:52:30 ian-latitude kernel: [  286.048000] ata1.00: configured for UDMA/33
Apr 15 10:52:30 ian-latitude kernel: [  286.048000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Apr 15 10:52:30 ian-latitude kernel: [  286.048000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Apr 15 10:52:30 ian-latitude kernel: [  286.048000] Descriptor sense data with sense descriptors (in hex):
Apr 15 10:52:30 ian-latitude kernel: [  286.048000]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr 15 10:52:30 ian-latitude kernel: [  286.048000]         02 57 e2 83 
Apr 15 10:52:30 ian-latitude kernel: [  286.048000] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
Apr 15 10:52:30 ian-latitude kernel: [  286.048000] end_request: I/O error, dev sda, sector 39314051
Apr 15 10:52:30 ian-latitude kernel: [  286.048000] ata1: EH complete
Apr 15 10:52:30 ian-latitude kernel: [  290.392000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:52:30 ian-latitude kernel: [  290.392000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:52:30 ian-latitude kernel: [  290.392000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:52:30 ian-latitude kernel: [  290.392000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:52:30 ian-latitude kernel: [  290.416000] ata1.00: configured for UDMA/33
Apr 15 10:52:30 ian-latitude kernel: [  290.416000] ata1: EH complete
Apr 15 10:52:30 ian-latitude kernel: [  294.880000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:52:30 ian-latitude kernel: [  294.880000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:52:30 ian-latitude kernel: [  294.880000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:52:30 ian-latitude kernel: [  294.880000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:52:30 ian-latitude kernel: [  294.904000] ata1.00: configured for UDMA/33
Apr 15 10:52:30 ian-latitude kernel: [  294.904000] ata1: EH complete
Apr 15 10:52:30 ian-latitude kernel: [  299.348000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:52:30 ian-latitude kernel: [  299.348000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:52:30 ian-latitude kernel: [  299.348000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:52:30 ian-latitude kernel: [  299.348000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:52:30 ian-latitude kernel: [  299.372000] ata1.00: configured for UDMA/33
Apr 15 10:52:30 ian-latitude kernel: [  299.372000] ata1: EH complete
Apr 15 10:52:30 ian-latitude kernel: [  303.804000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:52:30 ian-latitude kernel: [  303.804000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:52:30 ian-latitude kernel: [  303.804000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:52:30 ian-latitude kernel: [  303.804000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:52:30 ian-latitude kernel: [  303.828000] ata1.00: configured for UDMA/33
Apr 15 10:52:30 ian-latitude kernel: [  303.828000] ata1: EH complete
Apr 15 10:52:30 ian-latitude kernel: [  308.352000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:52:30 ian-latitude kernel: [  308.352000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:52:30 ian-latitude kernel: [  308.352000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:52:30 ian-latitude kernel: [  308.352000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:52:30 ian-latitude kernel: [  308.376000] ata1.00: configured for UDMA/33
Apr 15 10:52:30 ian-latitude kernel: [  308.376000] ata1: EH complete
Apr 15 10:52:30 ian-latitude kernel: [  312.696000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:52:30 ian-latitude kernel: [  312.696000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:52:30 ian-latitude kernel: [  312.696000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:52:30 ian-latitude kernel: [  312.696000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:52:30 ian-latitude kernel: [  312.720000] ata1.00: configured for UDMA/33
Apr 15 10:52:30 ian-latitude kernel: [  312.720000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Apr 15 10:52:30 ian-latitude kernel: [  312.720000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Apr 15 10:52:30 ian-latitude kernel: [  312.720000] Descriptor sense data with sense descriptors (in hex):
Apr 15 10:52:30 ian-latitude kernel: [  312.720000]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr 15 10:52:30 ian-latitude kernel: [  312.720000]         02 57 e2 83 
Apr 15 10:52:30 ian-latitude kernel: [  312.720000] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
Apr 15 10:52:30 ian-latitude kernel: [  312.720000] end_request: I/O error, dev sda, sector 39314051
Apr 15 10:52:30 ian-latitude kernel: [  312.720000] ata1: EH complete
Apr 15 10:52:30 ian-latitude kernel: [  312.720000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 10:52:30 ian-latitude kernel: [  312.740000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 10:52:30 ian-latitude kernel: [  312.740000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 10:52:30 ian-latitude kernel: [  312.740000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 10:52:30 ian-latitude kernel: [  312.740000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 10:52:30 ian-latitude kernel: [  312.740000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 10:52:30 ian-latitude kernel: [  312.740000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 10:52:30 ian-latitude kernel: [  312.744000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 10:52:30 ian-latitude kernel: [  317.196000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:52:30 ian-latitude kernel: [  317.196000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:52:30 ian-latitude kernel: [  317.196000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:52:30 ian-latitude kernel: [  317.196000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:52:30 ian-latitude kernel: [  317.260000] ata1.00: configured for UDMA/33
Apr 15 10:52:30 ian-latitude kernel: [  317.260000] ata1: EH complete
Apr 15 10:52:30 ian-latitude kernel: [  321.696000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:52:30 ian-latitude kernel: [  321.696000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:52:30 ian-latitude kernel: [  321.696000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:52:30 ian-latitude kernel: [  321.696000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:52:30 ian-latitude kernel: [  321.720000] ata1.00: configured for UDMA/33
Apr 15 10:52:30 ian-latitude kernel: [  321.720000] ata1: EH complete
Apr 15 10:52:30 ian-latitude kernel: [  326.144000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:52:30 ian-latitude kernel: [  326.144000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:52:30 ian-latitude kernel: [  326.144000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:52:30 ian-latitude kernel: [  326.144000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:52:30 ian-latitude kernel: [  326.168000] ata1.00: configured for UDMA/33
Apr 15 10:52:30 ian-latitude kernel: [  326.168000] ata1: EH complete
Apr 15 10:52:30 ian-latitude kernel: [  330.676000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:52:30 ian-latitude kernel: [  330.676000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:52:30 ian-latitude kernel: [  330.676000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:52:30 ian-latitude kernel: [  330.676000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:52:30 ian-latitude kernel: [  330.700000] ata1.00: configured for UDMA/33
Apr 15 10:52:30 ian-latitude kernel: [  330.700000] ata1: EH complete
Apr 15 10:52:30 ian-latitude kernel: [  335.132000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:52:30 ian-latitude kernel: [  335.132000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:52:30 ian-latitude kernel: [  335.132000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:52:30 ian-latitude kernel: [  335.132000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:52:30 ian-latitude kernel: [  335.156000] ata1.00: configured for UDMA/33
Apr 15 10:52:30 ian-latitude kernel: [  335.156000] ata1: EH complete
Apr 15 10:52:30 ian-latitude kernel: [  339.600000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:52:30 ian-latitude kernel: [  339.600000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:52:30 ian-latitude kernel: [  339.600000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:52:30 ian-latitude kernel: [  339.600000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:52:30 ian-latitude kernel: [  339.628000] ata1.00: configured for UDMA/33
Apr 15 10:52:30 ian-latitude kernel: [  339.628000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Apr 15 10:52:30 ian-latitude kernel: [  339.628000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Apr 15 10:52:30 ian-latitude kernel: [  339.628000] Descriptor sense data with sense descriptors (in hex):
Apr 15 10:52:30 ian-latitude kernel: [  339.628000]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr 15 10:52:30 ian-latitude kernel: [  339.628000]         02 57 e2 83 
Apr 15 10:52:30 ian-latitude kernel: [  339.628000] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
Apr 15 10:52:30 ian-latitude kernel: [  339.628000] end_request: I/O error, dev sda, sector 39314051
Apr 15 10:52:30 ian-latitude kernel: [  339.628000] ata1: EH complete
Apr 15 10:52:30 ian-latitude kernel: [  344.068000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:52:30 ian-latitude kernel: [  344.068000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:52:30 ian-latitude kernel: [  344.068000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:52:30 ian-latitude kernel: [  344.068000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:52:30 ian-latitude kernel: [  344.092000] ata1.00: configured for UDMA/33
Apr 15 10:52:30 ian-latitude kernel: [  344.092000] ata1: EH complete
Apr 15 10:52:30 ian-latitude kernel: [  348.536000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:52:30 ian-latitude kernel: [  348.536000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:52:30 ian-latitude kernel: [  348.536000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:52:30 ian-latitude kernel: [  348.536000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:52:30 ian-latitude kernel: [  348.560000] ata1.00: configured for UDMA/33
Apr 15 10:52:30 ian-latitude kernel: [  348.560000] ata1: EH complete
Apr 15 10:52:30 ian-latitude kernel: [  353.080000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:52:30 ian-latitude kernel: [  353.080000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:52:30 ian-latitude kernel: [  353.080000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:52:30 ian-latitude kernel: [  353.080000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:52:30 ian-latitude kernel: [  353.104000] ata1.00: configured for UDMA/33
Apr 15 10:52:30 ian-latitude kernel: [  353.104000] ata1: EH complete
Apr 15 10:52:30 ian-latitude kernel: [  357.548000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:52:30 ian-latitude kernel: [  357.548000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:52:30 ian-latitude kernel: [  357.548000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:52:30 ian-latitude kernel: [  357.548000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:52:30 ian-latitude kernel: [  357.572000] ata1.00: configured for UDMA/33
Apr 15 10:52:30 ian-latitude kernel: [  357.572000] ata1: EH complete
Apr 15 10:52:30 ian-latitude kernel: [  362.028000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:52:30 ian-latitude kernel: [  362.028000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:52:30 ian-latitude kernel: [  362.028000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:52:30 ian-latitude kernel: [  362.028000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:52:30 ian-latitude kernel: [  362.052000] ata1.00: configured for UDMA/33
Apr 15 10:52:30 ian-latitude kernel: [  362.052000] ata1: EH complete
Apr 15 10:52:30 ian-latitude kernel: [  366.484000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:52:30 ian-latitude kernel: [  366.484000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:52:30 ian-latitude kernel: [  366.484000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:52:30 ian-latitude kernel: [  366.484000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:52:30 ian-latitude kernel: [  366.508000] ata1.00: configured for UDMA/33
Apr 15 10:52:30 ian-latitude kernel: [  366.508000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Apr 15 10:52:30 ian-latitude kernel: [  366.508000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Apr 15 10:52:30 ian-latitude kernel: [  366.508000] Descriptor sense data with sense descriptors (in hex):
Apr 15 10:52:30 ian-latitude kernel: [  366.508000]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr 15 10:52:30 ian-latitude kernel: [  366.508000]         02 57 e2 83 
Apr 15 10:52:30 ian-latitude kernel: [  366.508000] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
Apr 15 10:52:30 ian-latitude kernel: [  366.508000] end_request: I/O error, dev sda, sector 39314051
Apr 15 10:52:30 ian-latitude kernel: [  366.508000] ata1: EH complete
Apr 15 10:52:30 ian-latitude kernel: [  366.508000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 10:52:30 ian-latitude kernel: [  366.508000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 10:52:30 ian-latitude kernel: [  366.508000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 10:52:30 ian-latitude kernel: [  366.508000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 10:52:30 ian-latitude kernel: [  366.508000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 10:52:30 ian-latitude kernel: [  366.508000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 10:52:30 ian-latitude kernel: [  366.508000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 10:52:30 ian-latitude kernel: [  366.512000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 10:52:35 ian-latitude kernel: [  370.972000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:52:35 ian-latitude kernel: [  370.972000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:52:35 ian-latitude kernel: [  370.972000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:52:35 ian-latitude kernel: [  370.972000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:52:35 ian-latitude kernel: [  371.108000] ata1.00: configured for UDMA/33
Apr 15 10:52:35 ian-latitude kernel: [  371.108000] ata1: EH complete
Apr 15 10:52:39 ian-latitude kernel: [  375.632000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:52:39 ian-latitude kernel: [  375.632000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:52:39 ian-latitude kernel: [  375.632000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:52:39 ian-latitude kernel: [  375.632000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:52:39 ian-latitude kernel: [  375.656000] ata1.00: configured for UDMA/33
Apr 15 10:52:39 ian-latitude kernel: [  375.656000] ata1: EH complete
Apr 15 10:52:44 ian-latitude kernel: [  380.096000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:52:44 ian-latitude kernel: [  380.096000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:52:44 ian-latitude kernel: [  380.096000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:52:44 ian-latitude kernel: [  380.096000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:52:44 ian-latitude kernel: [  380.120000] ata1.00: configured for UDMA/33
Apr 15 10:52:44 ian-latitude kernel: [  380.120000] ata1: EH complete
Apr 15 10:52:48 ian-latitude kernel: [  384.564000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:52:48 ian-latitude kernel: [  384.564000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:52:48 ian-latitude kernel: [  384.564000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:52:48 ian-latitude kernel: [  384.564000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:52:48 ian-latitude kernel: [  384.588000] ata1.00: configured for UDMA/33
Apr 15 10:52:48 ian-latitude kernel: [  384.588000] ata1: EH complete
Apr 15 10:52:53 ian-latitude kernel: [  388.876000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:52:53 ian-latitude kernel: [  388.876000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:52:53 ian-latitude kernel: [  388.876000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:52:53 ian-latitude kernel: [  388.876000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:52:53 ian-latitude kernel: [  388.900000] ata1.00: configured for UDMA/33
Apr 15 10:52:53 ian-latitude kernel: [  388.900000] ata1: EH complete
Apr 15 10:52:57 ian-latitude kernel: [  393.300000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:52:57 ian-latitude kernel: [  393.300000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:52:57 ian-latitude kernel: [  393.300000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:52:57 ian-latitude kernel: [  393.300000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:52:57 ian-latitude kernel: [  393.324000] ata1.00: configured for UDMA/33
Apr 15 10:52:57 ian-latitude kernel: [  393.324000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Apr 15 10:52:57 ian-latitude kernel: [  393.324000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Apr 15 10:52:57 ian-latitude kernel: [  393.324000] Descriptor sense data with sense descriptors (in hex):
Apr 15 10:52:57 ian-latitude kernel: [  393.324000]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr 15 10:52:57 ian-latitude kernel: [  393.324000]         02 57 e2 83 
Apr 15 10:52:57 ian-latitude kernel: [  393.324000] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
Apr 15 10:52:57 ian-latitude kernel: [  393.324000] end_request: I/O error, dev sda, sector 39314051
Apr 15 10:52:57 ian-latitude kernel: [  393.324000] ata1: EH complete
Apr 15 10:52:57 ian-latitude kernel: [  393.344000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 10:52:57 ian-latitude kernel: [  393.344000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 10:52:57 ian-latitude kernel: [  393.344000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 10:52:57 ian-latitude kernel: [  393.352000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 10:52:57 ian-latitude kernel: [  393.368000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 10:52:57 ian-latitude kernel: [  393.368000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 10:52:57 ian-latitude kernel: [  393.368000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 10:52:57 ian-latitude kernel: [  393.368000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 10:53:02 ian-latitude kernel: [  397.900000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:53:02 ian-latitude kernel: [  397.900000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:53:02 ian-latitude kernel: [  397.900000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:53:02 ian-latitude kernel: [  397.900000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:53:02 ian-latitude kernel: [  397.964000] ata1.00: configured for UDMA/33
Apr 15 10:53:02 ian-latitude kernel: [  397.964000] ata1: EH complete
Apr 15 10:53:06 ian-latitude kernel: [  402.412000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:53:06 ian-latitude kernel: [  402.412000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:53:06 ian-latitude kernel: [  402.412000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:53:06 ian-latitude kernel: [  402.412000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:53:06 ian-latitude kernel: [  402.436000] ata1.00: configured for UDMA/33
Apr 15 10:53:06 ian-latitude kernel: [  402.436000] ata1: EH complete
Apr 15 10:53:11 ian-latitude kernel: [  406.868000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:53:11 ian-latitude kernel: [  406.868000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:53:11 ian-latitude kernel: [  406.868000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:53:11 ian-latitude kernel: [  406.868000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:53:11 ian-latitude kernel: [  406.892000] ata1.00: configured for UDMA/33
Apr 15 10:53:11 ian-latitude kernel: [  406.892000] ata1: EH complete
Apr 15 10:53:15 ian-latitude kernel: [  411.336000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:53:15 ian-latitude kernel: [  411.336000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:53:15 ian-latitude kernel: [  411.336000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:53:15 ian-latitude kernel: [  411.336000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:53:15 ian-latitude kernel: [  411.364000] ata1.00: configured for UDMA/33
Apr 15 10:53:15 ian-latitude kernel: [  411.364000] ata1: EH complete
Apr 15 10:53:19 ian-latitude kernel: [  415.804000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:53:19 ian-latitude kernel: [  415.804000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:53:19 ian-latitude kernel: [  415.804000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:53:19 ian-latitude kernel: [  415.804000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:53:19 ian-latitude kernel: [  415.828000] ata1.00: configured for UDMA/33
Apr 15 10:53:19 ian-latitude kernel: [  415.828000] ata1: EH complete
Apr 15 10:53:24 ian-latitude kernel: [  420.352000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:53:24 ian-latitude kernel: [  420.352000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:53:24 ian-latitude kernel: [  420.352000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:53:24 ian-latitude kernel: [  420.352000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:53:24 ian-latitude kernel: [  420.376000] ata1.00: configured for UDMA/33
Apr 15 10:53:24 ian-latitude kernel: [  420.376000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Apr 15 10:53:24 ian-latitude kernel: [  420.376000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Apr 15 10:53:24 ian-latitude kernel: [  420.376000] Descriptor sense data with sense descriptors (in hex):
Apr 15 10:53:24 ian-latitude kernel: [  420.376000]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr 15 10:53:24 ian-latitude kernel: [  420.376000]         02 57 e2 83 
Apr 15 10:53:24 ian-latitude kernel: [  420.376000] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
Apr 15 10:53:24 ian-latitude kernel: [  420.376000] end_request: I/O error, dev sda, sector 39314051
Apr 15 10:53:24 ian-latitude kernel: [  420.376000] ata1: EH complete
Apr 15 10:53:28 ian-latitude kernel: [  424.816000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:53:28 ian-latitude kernel: [  424.816000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:53:28 ian-latitude kernel: [  424.816000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:53:28 ian-latitude kernel: [  424.816000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:53:28 ian-latitude kernel: [  424.840000] ata1.00: configured for UDMA/33
Apr 15 10:53:28 ian-latitude kernel: [  424.840000] ata1: EH complete
Apr 15 10:53:33 ian-latitude kernel: [  429.264000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:53:33 ian-latitude kernel: [  429.264000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:53:33 ian-latitude kernel: [  429.264000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:53:33 ian-latitude kernel: [  429.264000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:53:33 ian-latitude kernel: [  429.288000] ata1.00: configured for UDMA/33
Apr 15 10:53:33 ian-latitude kernel: [  429.288000] ata1: EH complete
Apr 15 10:53:37 ian-latitude kernel: [  433.708000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:53:37 ian-latitude kernel: [  433.708000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:53:37 ian-latitude kernel: [  433.708000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:53:37 ian-latitude kernel: [  433.708000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:53:37 ian-latitude kernel: [  433.732000] ata1.00: configured for UDMA/33
Apr 15 10:53:37 ian-latitude kernel: [  433.732000] ata1: EH complete
Apr 15 10:53:42 ian-latitude kernel: [  438.188000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:53:42 ian-latitude kernel: [  438.188000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:53:42 ian-latitude kernel: [  438.188000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:53:42 ian-latitude kernel: [  438.188000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:53:42 ian-latitude kernel: [  438.212000] ata1.00: configured for UDMA/33
Apr 15 10:53:42 ian-latitude kernel: [  438.212000] ata1: EH complete
Apr 15 10:53:46 ian-latitude kernel: [  442.564000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:53:46 ian-latitude kernel: [  442.564000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:53:46 ian-latitude kernel: [  442.564000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:53:46 ian-latitude kernel: [  442.564000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:53:46 ian-latitude kernel: [  442.588000] ata1.00: configured for UDMA/33
Apr 15 10:53:46 ian-latitude kernel: [  442.588000] ata1: EH complete
Apr 15 10:53:51 ian-latitude kernel: [  446.924000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:53:51 ian-latitude kernel: [  446.924000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:53:51 ian-latitude kernel: [  446.924000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:53:51 ian-latitude kernel: [  446.924000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:53:51 ian-latitude kernel: [  446.948000] ata1.00: configured for UDMA/33
Apr 15 10:53:51 ian-latitude kernel: [  446.948000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Apr 15 10:53:51 ian-latitude kernel: [  446.948000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Apr 15 10:53:51 ian-latitude kernel: [  446.948000] Descriptor sense data with sense descriptors (in hex):
Apr 15 10:53:51 ian-latitude kernel: [  446.948000]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr 15 10:53:51 ian-latitude kernel: [  446.948000]         02 57 e2 83 
Apr 15 10:53:51 ian-latitude kernel: [  446.948000] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
Apr 15 10:53:51 ian-latitude kernel: [  446.948000] end_request: I/O error, dev sda, sector 39314051
Apr 15 10:53:51 ian-latitude kernel: [  446.948000] ata1: EH complete
Apr 15 10:53:51 ian-latitude kernel: [  446.948000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 10:53:51 ian-latitude kernel: [  446.948000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 10:53:51 ian-latitude kernel: [  446.948000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 10:53:51 ian-latitude kernel: [  446.948000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 10:53:55 ian-latitude kernel: [  451.400000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:53:55 ian-latitude kernel: [  451.400000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:53:55 ian-latitude kernel: [  451.400000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:53:55 ian-latitude kernel: [  451.400000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:53:55 ian-latitude kernel: [  451.448000] ata1.00: configured for UDMA/33
Apr 15 10:53:55 ian-latitude kernel: [  451.448000] ata1: EH complete
Apr 15 10:54:00 ian-latitude kernel: [  455.880000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:54:00 ian-latitude kernel: [  455.880000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:54:00 ian-latitude kernel: [  455.880000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:54:00 ian-latitude kernel: [  455.880000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:54:00 ian-latitude kernel: [  455.904000] ata1.00: configured for UDMA/33
Apr 15 10:54:00 ian-latitude kernel: [  455.904000] ata1: EH complete
Apr 15 10:54:04 ian-latitude kernel: [  460.368000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:54:04 ian-latitude kernel: [  460.368000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:54:04 ian-latitude kernel: [  460.368000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:54:04 ian-latitude kernel: [  460.368000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:54:04 ian-latitude kernel: [  460.392000] ata1.00: configured for UDMA/33
Apr 15 10:54:04 ian-latitude kernel: [  460.392000] ata1: EH complete
Apr 15 10:54:09 ian-latitude kernel: [  464.892000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:54:09 ian-latitude kernel: [  464.892000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:54:09 ian-latitude kernel: [  464.892000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:54:09 ian-latitude kernel: [  464.892000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:54:09 ian-latitude kernel: [  464.916000] ata1.00: configured for UDMA/33
Apr 15 10:54:09 ian-latitude kernel: [  464.916000] ata1: EH complete
Apr 15 10:54:13 ian-latitude kernel: [  469.372000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:54:13 ian-latitude kernel: [  469.372000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:54:13 ian-latitude kernel: [  469.372000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:54:13 ian-latitude kernel: [  469.372000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:54:13 ian-latitude kernel: [  469.396000] ata1.00: configured for UDMA/33
Apr 15 10:54:13 ian-latitude kernel: [  469.396000] ata1: EH complete
Apr 15 10:54:17 ian-latitude kernel: [  473.828000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:54:17 ian-latitude kernel: [  473.828000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:54:17 ian-latitude kernel: [  473.828000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:54:17 ian-latitude kernel: [  473.828000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:54:18 ian-latitude kernel: [  473.852000] ata1.00: configured for UDMA/33
Apr 15 10:54:18 ian-latitude kernel: [  473.852000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Apr 15 10:54:18 ian-latitude kernel: [  473.852000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Apr 15 10:54:18 ian-latitude kernel: [  473.852000] Descriptor sense data with sense descriptors (in hex):
Apr 15 10:54:18 ian-latitude kernel: [  473.852000]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr 15 10:54:18 ian-latitude kernel: [  473.852000]         02 57 e2 83 
Apr 15 10:54:18 ian-latitude kernel: [  473.852000] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
Apr 15 10:54:18 ian-latitude kernel: [  473.852000] end_request: I/O error, dev sda, sector 39314051
Apr 15 10:54:18 ian-latitude kernel: [  473.852000] ata1: EH complete
Apr 15 10:54:18 ian-latitude kernel: [  473.852000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 10:54:22 ian-latitude kernel: [  478.284000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:54:22 ian-latitude kernel: [  478.284000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:54:22 ian-latitude kernel: [  478.284000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:54:22 ian-latitude kernel: [  478.284000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:54:22 ian-latitude kernel: [  478.308000] ata1.00: configured for UDMA/33
Apr 15 10:54:22 ian-latitude kernel: [  478.308000] ata1: EH complete
Apr 15 10:54:26 ian-latitude kernel: [  482.740000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:54:26 ian-latitude kernel: [  482.740000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:54:26 ian-latitude kernel: [  482.740000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:54:26 ian-latitude kernel: [  482.740000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:54:26 ian-latitude kernel: [  482.764000] ata1.00: configured for UDMA/33
Apr 15 10:54:26 ian-latitude kernel: [  482.764000] ata1: EH complete
Apr 15 10:54:31 ian-latitude kernel: [  487.284000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:54:31 ian-latitude kernel: [  487.284000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:54:31 ian-latitude kernel: [  487.284000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:54:31 ian-latitude kernel: [  487.284000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:54:31 ian-latitude kernel: [  487.312000] ata1.00: configured for UDMA/33
Apr 15 10:54:31 ian-latitude kernel: [  487.312000] ata1: EH complete
Apr 15 10:54:36 ian-latitude kernel: [  492.120000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:54:36 ian-latitude kernel: [  492.120000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:54:36 ian-latitude kernel: [  492.120000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:54:36 ian-latitude kernel: [  492.120000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:54:36 ian-latitude kernel: [  492.148000] ata1.00: configured for UDMA/33
Apr 15 10:54:36 ian-latitude kernel: [  492.148000] ata1: EH complete
Apr 15 10:54:40 ian-latitude kernel: [  496.600000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:54:40 ian-latitude kernel: [  496.600000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:54:40 ian-latitude kernel: [  496.600000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:54:40 ian-latitude kernel: [  496.600000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:54:40 ian-latitude kernel: [  496.624000] ata1.00: configured for UDMA/33
Apr 15 10:54:40 ian-latitude kernel: [  496.624000] ata1: EH complete
Apr 15 10:54:45 ian-latitude kernel: [  501.044000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:54:45 ian-latitude kernel: [  501.044000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:54:45 ian-latitude kernel: [  501.044000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:54:45 ian-latitude kernel: [  501.044000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:54:45 ian-latitude kernel: [  501.068000] ata1.00: configured for UDMA/33
Apr 15 10:54:45 ian-latitude kernel: [  501.068000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Apr 15 10:54:45 ian-latitude kernel: [  501.068000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Apr 15 10:54:45 ian-latitude kernel: [  501.068000] Descriptor sense data with sense descriptors (in hex):
Apr 15 10:54:45 ian-latitude kernel: [  501.068000]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr 15 10:54:45 ian-latitude kernel: [  501.068000]         02 57 e2 83 
Apr 15 10:54:45 ian-latitude kernel: [  501.068000] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
Apr 15 10:54:45 ian-latitude kernel: [  501.068000] end_request: I/O error, dev sda, sector 39314051
Apr 15 10:54:45 ian-latitude kernel: [  501.068000] ata1: EH complete
Apr 15 10:54:45 ian-latitude kernel: [  501.068000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 10:54:45 ian-latitude kernel: [  501.068000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 10:54:45 ian-latitude kernel: [  501.080000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 10:54:45 ian-latitude kernel: [  501.080000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 10:54:45 ian-latitude kernel: [  501.080000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 10:54:45 ian-latitude kernel: [  501.080000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 10:54:45 ian-latitude kernel: [  501.080000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 10:54:50 ian-latitude kernel: [  506.044000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:54:50 ian-latitude kernel: [  506.044000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:54:50 ian-latitude kernel: [  506.044000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:54:50 ian-latitude kernel: [  506.044000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:54:50 ian-latitude kernel: [  506.212000] ata1.00: configured for UDMA/33
Apr 15 10:54:50 ian-latitude kernel: [  506.212000] ata1: EH complete
Apr 15 10:54:54 ian-latitude kernel: [  510.624000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:54:54 ian-latitude kernel: [  510.624000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:54:54 ian-latitude kernel: [  510.624000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:54:54 ian-latitude kernel: [  510.624000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:54:54 ian-latitude kernel: [  510.648000] ata1.00: configured for UDMA/33
Apr 15 10:54:54 ian-latitude kernel: [  510.648000] ata1: EH complete
Apr 15 10:54:59 ian-latitude kernel: [  515.092000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:54:59 ian-latitude kernel: [  515.092000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:54:59 ian-latitude kernel: [  515.092000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:54:59 ian-latitude kernel: [  515.092000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:54:59 ian-latitude kernel: [  515.116000] ata1.00: configured for UDMA/33
Apr 15 10:54:59 ian-latitude kernel: [  515.116000] ata1: EH complete
Apr 15 10:55:03 ian-latitude kernel: [  519.568000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:55:03 ian-latitude kernel: [  519.568000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:55:03 ian-latitude kernel: [  519.568000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:55:03 ian-latitude kernel: [  519.568000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:55:03 ian-latitude kernel: [  519.596000] ata1.00: configured for UDMA/33
Apr 15 10:55:03 ian-latitude kernel: [  519.596000] ata1: EH complete
Apr 15 10:55:08 ian-latitude kernel: [  524.028000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:55:08 ian-latitude kernel: [  524.028000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:55:08 ian-latitude kernel: [  524.028000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:55:08 ian-latitude kernel: [  524.028000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:55:08 ian-latitude kernel: [  524.052000] ata1.00: configured for UDMA/33
Apr 15 10:55:08 ian-latitude kernel: [  524.052000] ata1: EH complete
Apr 15 10:55:12 ian-latitude kernel: [  528.504000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:55:12 ian-latitude kernel: [  528.504000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:55:12 ian-latitude kernel: [  528.504000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:55:12 ian-latitude kernel: [  528.504000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:55:12 ian-latitude kernel: [  528.528000] ata1.00: configured for UDMA/33
Apr 15 10:55:12 ian-latitude kernel: [  528.528000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Apr 15 10:55:12 ian-latitude kernel: [  528.528000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Apr 15 10:55:12 ian-latitude kernel: [  528.528000] Descriptor sense data with sense descriptors (in hex):
Apr 15 10:55:12 ian-latitude kernel: [  528.528000]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr 15 10:55:12 ian-latitude kernel: [  528.528000]         02 57 e2 83 
Apr 15 10:55:12 ian-latitude kernel: [  528.528000] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
Apr 15 10:55:12 ian-latitude kernel: [  528.528000] end_request: I/O error, dev sda, sector 39314051
Apr 15 10:55:12 ian-latitude kernel: [  528.528000] ata1: EH complete
Apr 15 10:55:12 ian-latitude kernel: [  528.540000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 10:55:12 ian-latitude kernel: [  528.540000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 10:55:12 ian-latitude kernel: [  528.540000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 10:55:12 ian-latitude kernel: [  528.540000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 10:55:12 ian-latitude kernel: [  528.540000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 10:55:12 ian-latitude kernel: [  528.540000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 10:55:12 ian-latitude kernel: [  528.540000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 10:55:12 ian-latitude kernel: [  528.540000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 10:55:17 ian-latitude kernel: [  533.116000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:55:17 ian-latitude kernel: [  533.116000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:55:17 ian-latitude kernel: [  533.116000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:55:17 ian-latitude kernel: [  533.116000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:55:17 ian-latitude kernel: [  533.180000] ata1.00: configured for UDMA/33
Apr 15 10:55:17 ian-latitude kernel: [  533.180000] ata1: EH complete
Apr 15 10:55:21 ian-latitude kernel: [  537.616000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:55:21 ian-latitude kernel: [  537.616000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:55:21 ian-latitude kernel: [  537.616000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:55:21 ian-latitude kernel: [  537.616000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:55:21 ian-latitude kernel: [  537.644000] ata1.00: configured for UDMA/33
Apr 15 10:55:21 ian-latitude kernel: [  537.644000] ata1: EH complete
Apr 15 10:55:26 ian-latitude kernel: [  542.064000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:55:26 ian-latitude kernel: [  542.064000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:55:26 ian-latitude kernel: [  542.064000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:55:26 ian-latitude kernel: [  542.064000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:55:26 ian-latitude kernel: [  542.088000] ata1.00: configured for UDMA/33
Apr 15 10:55:26 ian-latitude kernel: [  542.088000] ata1: EH complete
Apr 15 10:55:30 ian-latitude kernel: [  546.520000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:55:30 ian-latitude kernel: [  546.520000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:55:30 ian-latitude kernel: [  546.520000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:55:30 ian-latitude kernel: [  546.520000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:55:30 ian-latitude kernel: [  546.544000] ata1.00: configured for UDMA/33
Apr 15 10:55:30 ian-latitude kernel: [  546.544000] ata1: EH complete
Apr 15 10:55:35 ian-latitude kernel: [  550.988000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:55:35 ian-latitude kernel: [  550.988000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:55:35 ian-latitude kernel: [  550.988000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:55:35 ian-latitude kernel: [  550.988000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:55:35 ian-latitude kernel: [  551.012000] ata1.00: configured for UDMA/33
Apr 15 10:55:35 ian-latitude kernel: [  551.012000] ata1: EH complete
Apr 15 10:55:39 ian-latitude kernel: [  555.532000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:55:39 ian-latitude kernel: [  555.532000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:55:39 ian-latitude kernel: [  555.532000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:55:39 ian-latitude kernel: [  555.532000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:55:39 ian-latitude kernel: [  555.556000] ata1.00: configured for UDMA/33
Apr 15 10:55:39 ian-latitude kernel: [  555.556000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Apr 15 10:55:39 ian-latitude kernel: [  555.556000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Apr 15 10:55:39 ian-latitude kernel: [  555.556000] Descriptor sense data with sense descriptors (in hex):
Apr 15 10:55:39 ian-latitude kernel: [  555.556000]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr 15 10:55:39 ian-latitude kernel: [  555.556000]         02 57 e2 83 
Apr 15 10:55:39 ian-latitude kernel: [  555.556000] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
Apr 15 10:55:39 ian-latitude kernel: [  555.556000] end_request: I/O error, dev sda, sector 39314051
Apr 15 10:55:39 ian-latitude kernel: [  555.556000] ata1: EH complete
Apr 15 10:55:44 ian-latitude kernel: [  560.000000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:55:44 ian-latitude kernel: [  560.000000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:55:44 ian-latitude kernel: [  560.000000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:55:44 ian-latitude kernel: [  560.000000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:55:44 ian-latitude kernel: [  560.024000] ata1.00: configured for UDMA/33
Apr 15 10:55:44 ian-latitude kernel: [  560.024000] ata1: EH complete
Apr 15 10:55:48 ian-latitude kernel: [  564.444000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:55:48 ian-latitude kernel: [  564.444000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:55:48 ian-latitude kernel: [  564.444000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:55:48 ian-latitude kernel: [  564.444000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:55:48 ian-latitude kernel: [  564.468000] ata1.00: configured for UDMA/33
Apr 15 10:55:48 ian-latitude kernel: [  564.468000] ata1: EH complete
Apr 15 10:55:53 ian-latitude kernel: [  568.924000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:55:53 ian-latitude kernel: [  568.924000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:55:53 ian-latitude kernel: [  568.924000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:55:53 ian-latitude kernel: [  568.924000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:55:53 ian-latitude kernel: [  568.948000] ata1.00: configured for UDMA/33
Apr 15 10:55:53 ian-latitude kernel: [  568.948000] ata1: EH complete
Apr 15 10:55:57 ian-latitude kernel: [  573.392000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:55:57 ian-latitude kernel: [  573.392000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:55:57 ian-latitude kernel: [  573.392000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:55:57 ian-latitude kernel: [  573.392000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:55:57 ian-latitude kernel: [  573.416000] ata1.00: configured for UDMA/33
Apr 15 10:55:57 ian-latitude kernel: [  573.416000] ata1: EH complete
Apr 15 10:56:02 ian-latitude kernel: [  577.948000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:56:02 ian-latitude kernel: [  577.948000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:56:02 ian-latitude kernel: [  577.948000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:56:02 ian-latitude kernel: [  577.948000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:56:02 ian-latitude kernel: [  577.972000] ata1.00: configured for UDMA/33
Apr 15 10:56:02 ian-latitude kernel: [  577.972000] ata1: EH complete
Apr 15 10:56:06 ian-latitude kernel: [  582.384000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:56:06 ian-latitude kernel: [  582.384000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:56:06 ian-latitude kernel: [  582.384000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:56:06 ian-latitude kernel: [  582.384000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:56:06 ian-latitude kernel: [  582.408000] ata1.00: configured for UDMA/33
Apr 15 10:56:06 ian-latitude kernel: [  582.408000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Apr 15 10:56:06 ian-latitude kernel: [  582.408000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Apr 15 10:56:06 ian-latitude kernel: [  582.408000] Descriptor sense data with sense descriptors (in hex):
Apr 15 10:56:06 ian-latitude kernel: [  582.408000]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr 15 10:56:06 ian-latitude kernel: [  582.408000]         02 57 e2 83 
Apr 15 10:56:06 ian-latitude kernel: [  582.408000] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
Apr 15 10:56:06 ian-latitude kernel: [  582.408000] end_request: I/O error, dev sda, sector 39314051
Apr 15 10:56:06 ian-latitude kernel: [  582.408000] ata1: EH complete
Apr 15 10:56:06 ian-latitude kernel: [  582.408000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 10:56:06 ian-latitude kernel: [  582.420000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 10:56:06 ian-latitude kernel: [  582.420000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 10:56:06 ian-latitude kernel: [  582.424000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 10:56:11 ian-latitude kernel: [  586.896000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:56:11 ian-latitude kernel: [  586.896000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:56:11 ian-latitude kernel: [  586.896000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:56:11 ian-latitude kernel: [  586.896000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:56:11 ian-latitude kernel: [  586.960000] ata1.00: configured for UDMA/33
Apr 15 10:56:11 ian-latitude kernel: [  586.960000] ata1: EH complete
Apr 15 10:56:15 ian-latitude kernel: [  591.328000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:56:15 ian-latitude kernel: [  591.328000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:56:15 ian-latitude kernel: [  591.328000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:56:15 ian-latitude kernel: [  591.328000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:56:15 ian-latitude kernel: [  591.352000] ata1.00: configured for UDMA/33
Apr 15 10:56:15 ian-latitude kernel: [  591.352000] ata1: EH complete
Apr 15 10:56:19 ian-latitude kernel: [  595.796000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:56:19 ian-latitude kernel: [  595.796000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:56:19 ian-latitude kernel: [  595.796000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:56:19 ian-latitude kernel: [  595.796000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:56:19 ian-latitude kernel: [  595.820000] ata1.00: configured for UDMA/33
Apr 15 10:56:19 ian-latitude kernel: [  595.820000] ata1: EH complete
Apr 15 10:56:24 ian-latitude kernel: [  600.340000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:56:24 ian-latitude kernel: [  600.340000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:56:24 ian-latitude kernel: [  600.340000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:56:24 ian-latitude kernel: [  600.340000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:56:24 ian-latitude kernel: [  600.364000] ata1.00: configured for UDMA/33
Apr 15 10:56:24 ian-latitude kernel: [  600.364000] ata1: EH complete
Apr 15 10:56:28 ian-latitude kernel: [  604.796000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:56:28 ian-latitude kernel: [  604.796000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:56:28 ian-latitude kernel: [  604.796000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:56:28 ian-latitude kernel: [  604.796000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:56:28 ian-latitude kernel: [  604.824000] ata1.00: configured for UDMA/33
Apr 15 10:56:28 ian-latitude kernel: [  604.824000] ata1: EH complete
Apr 15 10:56:33 ian-latitude kernel: [  609.264000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:56:33 ian-latitude kernel: [  609.264000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:56:33 ian-latitude kernel: [  609.264000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:56:33 ian-latitude kernel: [  609.264000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:56:33 ian-latitude kernel: [  609.288000] ata1.00: configured for UDMA/33
Apr 15 10:56:33 ian-latitude kernel: [  609.288000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Apr 15 10:56:33 ian-latitude kernel: [  609.288000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Apr 15 10:56:33 ian-latitude kernel: [  609.288000] Descriptor sense data with sense descriptors (in hex):
Apr 15 10:56:33 ian-latitude kernel: [  609.288000]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr 15 10:56:33 ian-latitude kernel: [  609.288000]         02 57 e2 83 
Apr 15 10:56:33 ian-latitude kernel: [  609.288000] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
Apr 15 10:56:33 ian-latitude kernel: [  609.288000] end_request: I/O error, dev sda, sector 39314051
Apr 15 10:56:33 ian-latitude kernel: [  609.288000] ata1: EH complete
Apr 15 10:56:33 ian-latitude kernel: [  609.288000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 10:56:37 ian-latitude kernel: [  613.732000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:56:37 ian-latitude kernel: [  613.732000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:56:37 ian-latitude kernel: [  613.732000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:56:37 ian-latitude kernel: [  613.732000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:56:37 ian-latitude kernel: [  613.756000] ata1.00: configured for UDMA/33
Apr 15 10:56:37 ian-latitude kernel: [  613.756000] ata1: EH complete
Apr 15 10:56:42 ian-latitude kernel: [  618.200000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:56:42 ian-latitude kernel: [  618.200000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:56:42 ian-latitude kernel: [  618.200000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:56:42 ian-latitude kernel: [  618.200000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:56:42 ian-latitude kernel: [  618.224000] ata1.00: configured for UDMA/33
Apr 15 10:56:42 ian-latitude kernel: [  618.224000] ata1: EH complete
Apr 15 10:56:46 ian-latitude kernel: [  622.736000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:56:46 ian-latitude kernel: [  622.736000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:56:46 ian-latitude kernel: [  622.736000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:56:46 ian-latitude kernel: [  622.736000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:56:46 ian-latitude kernel: [  622.760000] ata1.00: configured for UDMA/33
Apr 15 10:56:46 ian-latitude kernel: [  622.760000] ata1: EH complete
Apr 15 10:56:51 ian-latitude kernel: [  627.180000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:56:51 ian-latitude kernel: [  627.180000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:56:51 ian-latitude kernel: [  627.180000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:56:51 ian-latitude kernel: [  627.180000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:56:51 ian-latitude kernel: [  627.204000] ata1.00: configured for UDMA/33
Apr 15 10:56:51 ian-latitude kernel: [  627.204000] ata1: EH complete
Apr 15 10:56:55 ian-latitude kernel: [  631.624000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:56:55 ian-latitude kernel: [  631.624000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:56:55 ian-latitude kernel: [  631.624000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:56:55 ian-latitude kernel: [  631.624000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:56:55 ian-latitude kernel: [  631.652000] ata1.00: configured for UDMA/33
Apr 15 10:56:55 ian-latitude kernel: [  631.652000] ata1: EH complete
Apr 15 10:57:00 ian-latitude kernel: [  636.092000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 10:57:00 ian-latitude kernel: [  636.092000] ata1.00: (BMDMA stat 0x24)
Apr 15 10:57:00 ian-latitude kernel: [  636.092000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 10:57:00 ian-latitude kernel: [  636.092000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 10:57:00 ian-latitude kernel: [  636.116000] ata1.00: configured for UDMA/33
Apr 15 10:57:00 ian-latitude kernel: [  636.116000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Apr 15 10:57:00 ian-latitude kernel: [  636.116000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Apr 15 10:57:00 ian-latitude kernel: [  636.116000] Descriptor sense data with sense descriptors (in hex):
Apr 15 10:59:42 ian-latitude kernel: [  636.116000]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr 15 10:59:42 ian-latitude kernel: [  636.116000]         02 57 e2 83 
Apr 15 10:59:42 ian-latitude kernel: [  636.116000] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
Apr 15 10:59:42 ian-latitude kernel: [  636.116000] end_request: I/O error, dev sda, sector 39314051
Apr 15 10:59:42 ian-latitude kernel: [  636.116000] ata1: EH complete
Apr 15 10:59:42 ian-latitude kernel: [  636.116000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 10:59:42 ian-latitude kernel: [  636.116000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 10:59:42 ian-latitude kernel: [  636.116000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 10:59:42 ian-latitude kernel: [  636.116000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 11:00:09 ian-latitude kernel: [  640.560000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  640.560000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  640.560000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  640.560000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  640.624000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  640.624000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  645.128000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  645.128000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  645.128000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  645.128000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  645.152000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  645.152000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  649.608000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  649.608000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  649.608000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  649.608000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  649.632000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  649.632000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  654.084000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  654.084000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  654.084000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  654.084000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  654.108000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  654.108000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  658.552000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  658.552000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  658.552000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  658.552000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  658.576000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  658.576000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  663.008000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  663.008000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  663.008000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  663.008000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  663.032000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  663.032000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Apr 15 11:00:09 ian-latitude kernel: [  663.032000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Apr 15 11:00:09 ian-latitude kernel: [  663.032000] Descriptor sense data with sense descriptors (in hex):
Apr 15 11:00:09 ian-latitude kernel: [  663.032000]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr 15 11:00:09 ian-latitude kernel: [  663.032000]         02 57 e2 83 
Apr 15 11:00:09 ian-latitude kernel: [  663.032000] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
Apr 15 11:00:09 ian-latitude kernel: [  663.032000] end_request: I/O error, dev sda, sector 39314051
Apr 15 11:00:09 ian-latitude kernel: [  663.032000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  663.032000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 11:00:09 ian-latitude kernel: [  663.032000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 11:00:09 ian-latitude kernel: [  667.564000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  667.564000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  667.564000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  667.564000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  667.592000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  667.592000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  672.024000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  672.024000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  672.024000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  672.024000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  672.048000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  672.048000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  676.480000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  676.480000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  676.480000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  676.480000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  676.504000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  676.504000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  680.948000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  680.948000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  680.948000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  680.948000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  680.972000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  680.972000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  685.412000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  685.412000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  685.412000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  685.412000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  685.440000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  685.440000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  689.972000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  689.972000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  689.972000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  689.972000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  689.996000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  689.996000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Apr 15 11:00:09 ian-latitude kernel: [  689.996000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Apr 15 11:00:09 ian-latitude kernel: [  689.996000] Descriptor sense data with sense descriptors (in hex):
Apr 15 11:00:09 ian-latitude kernel: [  689.996000]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr 15 11:00:09 ian-latitude kernel: [  689.996000]         02 57 e2 83 
Apr 15 11:00:09 ian-latitude kernel: [  689.996000] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
Apr 15 11:00:09 ian-latitude kernel: [  689.996000] end_request: I/O error, dev sda, sector 39314051
Apr 15 11:00:09 ian-latitude kernel: [  689.996000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  689.996000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 11:00:09 ian-latitude kernel: [  690.016000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 11:00:09 ian-latitude kernel: [  690.016000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 11:00:09 ian-latitude kernel: [  690.016000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 11:00:09 ian-latitude kernel: [  690.016000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 11:00:09 ian-latitude kernel: [  694.684000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  694.684000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  694.684000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  694.684000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  694.748000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  694.748000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  699.172000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  699.172000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  699.172000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  699.172000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  699.196000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  699.196000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  703.616000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  703.616000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  703.616000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  703.616000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  703.640000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  703.640000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  708.076000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  708.076000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  708.076000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  708.076000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  708.100000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  708.100000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  712.608000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  712.608000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  712.608000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  712.608000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  712.632000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  712.632000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  716.908000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  716.908000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  716.908000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  716.908000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  716.932000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  716.932000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Apr 15 11:00:09 ian-latitude kernel: [  716.932000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Apr 15 11:00:09 ian-latitude kernel: [  716.932000] Descriptor sense data with sense descriptors (in hex):
Apr 15 11:00:09 ian-latitude kernel: [  716.932000]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr 15 11:00:09 ian-latitude kernel: [  716.932000]         02 57 e2 83 
Apr 15 11:00:09 ian-latitude kernel: [  716.932000] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
Apr 15 11:00:09 ian-latitude kernel: [  716.932000] end_request: I/O error, dev sda, sector 39314051
Apr 15 11:00:09 ian-latitude kernel: [  716.932000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  716.952000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 11:00:09 ian-latitude kernel: [  716.952000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 11:00:09 ian-latitude kernel: [  716.952000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 11:00:09 ian-latitude kernel: [  716.964000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 11:00:09 ian-latitude kernel: [  716.976000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 11:00:09 ian-latitude kernel: [  716.980000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 11:00:09 ian-latitude kernel: [  716.980000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 11:00:09 ian-latitude kernel: [  716.992000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 11:00:09 ian-latitude kernel: [  721.488000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  721.488000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  721.488000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  721.488000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  721.560000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  721.560000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  725.968000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  725.968000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  725.968000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  725.968000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  725.992000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  725.992000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  730.436000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  730.436000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  730.436000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  730.436000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  730.460000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  730.460000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  734.968000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  734.968000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  734.968000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  734.968000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  734.992000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  734.992000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  739.436000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  739.436000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  739.436000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  739.436000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  739.460000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  739.460000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  743.916000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  743.916000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  743.916000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  743.916000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  743.940000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  743.940000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Apr 15 11:00:09 ian-latitude kernel: [  743.940000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Apr 15 11:00:09 ian-latitude kernel: [  743.940000] Descriptor sense data with sense descriptors (in hex):
Apr 15 11:00:09 ian-latitude kernel: [  743.940000]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr 15 11:00:09 ian-latitude kernel: [  743.940000]         02 57 e2 83 
Apr 15 11:00:09 ian-latitude kernel: [  743.940000] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
Apr 15 11:00:09 ian-latitude kernel: [  743.940000] end_request: I/O error, dev sda, sector 39314051
Apr 15 11:00:09 ian-latitude kernel: [  743.940000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  748.372000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  748.372000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  748.372000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  748.372000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  748.396000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  748.396000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  752.848000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  752.848000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  752.848000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  752.848000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  752.872000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  752.872000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  757.396000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  757.396000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  757.396000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  757.396000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  757.420000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  757.420000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  761.852000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  761.852000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  761.852000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  761.852000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  761.876000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  761.876000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  766.676000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  766.676000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  766.676000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  766.676000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  766.700000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  766.700000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  771.132000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  771.132000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  771.132000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  771.132000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  771.156000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  771.156000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Apr 15 11:00:09 ian-latitude kernel: [  771.156000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Apr 15 11:00:09 ian-latitude kernel: [  771.156000] Descriptor sense data with sense descriptors (in hex):
Apr 15 11:00:09 ian-latitude kernel: [  771.156000]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr 15 11:00:09 ian-latitude kernel: [  771.156000]         02 57 e2 83 
Apr 15 11:00:09 ian-latitude kernel: [  771.156000] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
Apr 15 11:00:09 ian-latitude kernel: [  771.156000] end_request: I/O error, dev sda, sector 39314051
Apr 15 11:00:09 ian-latitude kernel: [  771.156000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  771.156000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 11:00:09 ian-latitude kernel: [  771.180000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 11:00:09 ian-latitude kernel: [  771.180000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 11:00:09 ian-latitude kernel: [  771.180000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 11:00:09 ian-latitude kernel: [  771.180000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 11:00:09 ian-latitude kernel: [  771.180000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 11:00:09 ian-latitude kernel: [  771.180000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 11:00:09 ian-latitude kernel: [  771.184000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 11:00:09 ian-latitude kernel: [  775.664000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  775.664000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  775.664000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  775.664000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  775.712000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  775.712000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  780.220000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  780.220000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  780.220000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  780.220000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  780.244000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  780.244000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  784.700000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  784.700000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  784.700000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  784.700000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  784.724000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  784.724000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  789.156000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  789.156000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  789.156000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  789.156000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  789.180000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  789.180000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  793.612000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  793.612000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  793.612000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  793.612000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  793.636000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  793.636000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  798.092000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  798.092000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  798.092000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  798.092000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  798.116000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  798.116000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Apr 15 11:00:09 ian-latitude kernel: [  798.116000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Apr 15 11:00:09 ian-latitude kernel: [  798.116000] Descriptor sense data with sense descriptors (in hex):
Apr 15 11:00:09 ian-latitude kernel: [  798.116000]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr 15 11:00:09 ian-latitude kernel: [  798.116000]         02 57 e2 83 
Apr 15 11:00:09 ian-latitude kernel: [  798.116000] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
Apr 15 11:00:09 ian-latitude kernel: [  798.116000] end_request: I/O error, dev sda, sector 39314051
Apr 15 11:00:09 ian-latitude kernel: [  798.116000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  798.116000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 11:00:09 ian-latitude kernel: [  798.116000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 11:00:09 ian-latitude kernel: [  798.116000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 11:00:09 ian-latitude kernel: [  798.116000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 11:00:09 ian-latitude kernel: [  798.132000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 11:00:09 ian-latitude kernel: [  798.144000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 11:00:09 ian-latitude kernel: [  798.144000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 11:00:09 ian-latitude kernel: [  798.144000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 11:00:09 ian-latitude kernel: [  802.692000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  802.692000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  802.692000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  802.692000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  802.732000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  802.732000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  806.992000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  806.992000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  806.992000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  806.992000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  807.016000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  807.016000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  811.396000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  811.396000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  811.396000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  811.396000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  811.420000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  811.420000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  815.872000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  815.872000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  815.872000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  815.872000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  815.896000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  815.896000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  820.276000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  820.276000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  820.276000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  820.276000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  820.300000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  820.300000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  824.820000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:09 ian-latitude kernel: [  824.820000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:09 ian-latitude kernel: [  824.820000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:09 ian-latitude kernel: [  824.820000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:09 ian-latitude kernel: [  824.844000] ata1.00: configured for UDMA/33
Apr 15 11:00:09 ian-latitude kernel: [  824.844000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Apr 15 11:00:09 ian-latitude kernel: [  824.844000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Apr 15 11:00:09 ian-latitude kernel: [  824.844000] Descriptor sense data with sense descriptors (in hex):
Apr 15 11:00:09 ian-latitude kernel: [  824.844000]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr 15 11:00:09 ian-latitude kernel: [  824.844000]         02 57 e2 83 
Apr 15 11:00:09 ian-latitude kernel: [  824.844000] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
Apr 15 11:00:09 ian-latitude kernel: [  824.844000] end_request: I/O error, dev sda, sector 39314051
Apr 15 11:00:09 ian-latitude kernel: [  824.844000] ata1: EH complete
Apr 15 11:00:09 ian-latitude kernel: [  824.860000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 11:00:09 ian-latitude kernel: [  824.860000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 11:00:09 ian-latitude kernel: [  824.860000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 11:00:09 ian-latitude kernel: [  824.880000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 11:00:09 ian-latitude kernel: [  824.880000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 11:00:09 ian-latitude kernel: [  824.884000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 11:00:09 ian-latitude kernel: [  824.884000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 11:00:09 ian-latitude kernel: [  824.884000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 11:00:13 ian-latitude kernel: [  829.432000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:13 ian-latitude kernel: [  829.432000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:13 ian-latitude kernel: [  829.432000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:13 ian-latitude kernel: [  829.432000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:13 ian-latitude kernel: [  829.504000] ata1.00: configured for UDMA/33
Apr 15 11:00:13 ian-latitude kernel: [  829.504000] ata1: EH complete
Apr 15 11:00:18 ian-latitude kernel: [  833.944000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:18 ian-latitude kernel: [  833.944000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:18 ian-latitude kernel: [  833.944000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:18 ian-latitude kernel: [  833.944000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:18 ian-latitude kernel: [  833.968000] ata1.00: configured for UDMA/33
Apr 15 11:00:18 ian-latitude kernel: [  833.968000] ata1: EH complete
Apr 15 11:00:22 ian-latitude kernel: [  838.424000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:22 ian-latitude kernel: [  838.424000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:22 ian-latitude kernel: [  838.424000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:22 ian-latitude kernel: [  838.424000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:22 ian-latitude kernel: [  838.448000] ata1.00: configured for UDMA/33
Apr 15 11:00:22 ian-latitude kernel: [  838.448000] ata1: EH complete
Apr 15 11:00:27 ian-latitude kernel: [  842.888000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:27 ian-latitude kernel: [  842.888000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:27 ian-latitude kernel: [  842.888000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:27 ian-latitude kernel: [  842.888000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:27 ian-latitude kernel: [  842.912000] ata1.00: configured for UDMA/33
Apr 15 11:00:27 ian-latitude kernel: [  842.912000] ata1: EH complete
Apr 15 11:00:31 ian-latitude kernel: [  847.212000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:31 ian-latitude kernel: [  847.212000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:31 ian-latitude kernel: [  847.212000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:31 ian-latitude kernel: [  847.212000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:31 ian-latitude kernel: [  847.236000] ata1.00: configured for UDMA/33
Apr 15 11:00:31 ian-latitude kernel: [  847.236000] ata1: EH complete
Apr 15 11:00:35 ian-latitude kernel: [  851.680000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:35 ian-latitude kernel: [  851.680000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:35 ian-latitude kernel: [  851.680000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:35 ian-latitude kernel: [  851.680000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:35 ian-latitude kernel: [  851.704000] ata1.00: configured for UDMA/33
Apr 15 11:00:35 ian-latitude kernel: [  851.704000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Apr 15 11:00:35 ian-latitude kernel: [  851.704000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Apr 15 11:00:35 ian-latitude kernel: [  851.704000] Descriptor sense data with sense descriptors (in hex):
Apr 15 11:00:35 ian-latitude kernel: [  851.704000]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr 15 11:00:35 ian-latitude kernel: [  851.704000]         02 57 e2 83 
Apr 15 11:00:35 ian-latitude kernel: [  851.704000] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
Apr 15 11:00:35 ian-latitude kernel: [  851.704000] end_request: I/O error, dev sda, sector 39314051
Apr 15 11:00:35 ian-latitude kernel: [  851.704000] ata1: EH complete
Apr 15 11:00:35 ian-latitude kernel: [  851.704000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 11:00:40 ian-latitude kernel: [  856.136000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:40 ian-latitude kernel: [  856.136000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:40 ian-latitude kernel: [  856.136000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:40 ian-latitude kernel: [  856.136000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:40 ian-latitude kernel: [  856.160000] ata1.00: configured for UDMA/33
Apr 15 11:00:40 ian-latitude kernel: [  856.160000] ata1: EH complete
Apr 15 11:00:45 ian-latitude kernel: [  860.992000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:45 ian-latitude kernel: [  860.992000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:45 ian-latitude kernel: [  860.992000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:45 ian-latitude kernel: [  860.992000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:45 ian-latitude kernel: [  861.016000] ata1.00: configured for UDMA/33
Apr 15 11:00:45 ian-latitude kernel: [  861.016000] ata1: EH complete
Apr 15 11:00:49 ian-latitude kernel: [  865.460000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:49 ian-latitude kernel: [  865.460000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:49 ian-latitude kernel: [  865.460000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:49 ian-latitude kernel: [  865.460000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:49 ian-latitude kernel: [  865.484000] ata1.00: configured for UDMA/33
Apr 15 11:00:49 ian-latitude kernel: [  865.484000] ata1: EH complete
Apr 15 11:00:54 ian-latitude kernel: [  870.016000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:54 ian-latitude kernel: [  870.016000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:54 ian-latitude kernel: [  870.016000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:54 ian-latitude kernel: [  870.016000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:54 ian-latitude kernel: [  870.040000] ata1.00: configured for UDMA/33
Apr 15 11:00:54 ian-latitude kernel: [  870.040000] ata1: EH complete
Apr 15 11:00:58 ian-latitude kernel: [  874.496000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:00:58 ian-latitude kernel: [  874.496000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:00:58 ian-latitude kernel: [  874.496000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:00:58 ian-latitude kernel: [  874.496000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:00:58 ian-latitude kernel: [  874.520000] ata1.00: configured for UDMA/33
Apr 15 11:00:58 ian-latitude kernel: [  874.520000] ata1: EH complete
Apr 15 11:01:03 ian-latitude kernel: [  878.976000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:01:03 ian-latitude kernel: [  878.976000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:01:03 ian-latitude kernel: [  878.976000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:01:03 ian-latitude kernel: [  878.976000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:01:03 ian-latitude kernel: [  879.000000] ata1.00: configured for UDMA/33
Apr 15 11:01:03 ian-latitude kernel: [  879.000000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Apr 15 11:01:03 ian-latitude kernel: [  879.000000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Apr 15 11:01:03 ian-latitude kernel: [  879.000000] Descriptor sense data with sense descriptors (in hex):
Apr 15 11:01:03 ian-latitude kernel: [  879.000000]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr 15 11:01:03 ian-latitude kernel: [  879.000000]         02 57 e2 83 
Apr 15 11:01:03 ian-latitude kernel: [  879.000000] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
Apr 15 11:01:03 ian-latitude kernel: [  879.000000] end_request: I/O error, dev sda, sector 39314051
Apr 15 11:01:03 ian-latitude kernel: [  879.000000] ata1: EH complete
Apr 15 11:01:03 ian-latitude kernel: [  879.000000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 11:01:03 ian-latitude kernel: [  879.000000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 11:01:03 ian-latitude kernel: [  879.020000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 11:01:03 ian-latitude kernel: [  879.020000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 11:01:03 ian-latitude kernel: [  879.020000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 11:01:03 ian-latitude kernel: [  879.020000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 11:01:03 ian-latitude kernel: [  879.020000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 11:01:07 ian-latitude kernel: [  883.620000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:01:30 ian-latitude kernel: [  883.620000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:01:30 ian-latitude kernel: [  883.620000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:01:30 ian-latitude kernel: [  883.620000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:01:30 ian-latitude kernel: [  883.888000] ata1.00: configured for UDMA/33
Apr 15 11:01:30 ian-latitude kernel: [  883.888000] ata1: EH complete
Apr 15 11:01:30 ian-latitude kernel: [  888.332000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:01:30 ian-latitude kernel: [  888.332000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:01:30 ian-latitude kernel: [  888.332000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:01:30 ian-latitude kernel: [  888.332000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:01:30 ian-latitude kernel: [  888.356000] ata1.00: configured for UDMA/33
Apr 15 11:01:30 ian-latitude kernel: [  888.356000] ata1: EH complete
Apr 15 11:01:30 ian-latitude kernel: [  892.832000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:01:30 ian-latitude kernel: [  892.832000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:01:30 ian-latitude kernel: [  892.832000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:01:30 ian-latitude kernel: [  892.832000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:01:30 ian-latitude kernel: [  892.856000] ata1.00: configured for UDMA/33
Apr 15 11:01:30 ian-latitude kernel: [  892.856000] ata1: EH complete
Apr 15 11:01:30 ian-latitude kernel: [  897.312000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:01:30 ian-latitude kernel: [  897.312000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:01:30 ian-latitude kernel: [  897.312000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:01:30 ian-latitude kernel: [  897.312000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:01:30 ian-latitude kernel: [  897.336000] ata1.00: configured for UDMA/33
Apr 15 11:01:30 ian-latitude kernel: [  897.336000] ata1: EH complete
Apr 15 11:01:30 ian-latitude kernel: [  901.780000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:01:30 ian-latitude kernel: [  901.780000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:01:30 ian-latitude kernel: [  901.780000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:01:30 ian-latitude kernel: [  901.780000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:01:30 ian-latitude kernel: [  901.804000] ata1.00: configured for UDMA/33
Apr 15 11:01:30 ian-latitude kernel: [  901.804000] ata1: EH complete
Apr 15 11:01:30 ian-latitude kernel: [  906.248000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:01:30 ian-latitude kernel: [  906.248000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:01:30 ian-latitude kernel: [  906.248000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:01:30 ian-latitude kernel: [  906.248000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:01:30 ian-latitude kernel: [  906.272000] ata1.00: configured for UDMA/33
Apr 15 11:01:30 ian-latitude kernel: [  906.272000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Apr 15 11:01:30 ian-latitude kernel: [  906.272000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Apr 15 11:01:30 ian-latitude kernel: [  906.272000] Descriptor sense data with sense descriptors (in hex):
Apr 15 11:01:30 ian-latitude kernel: [  906.272000]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr 15 11:01:30 ian-latitude kernel: [  906.272000]         02 57 e2 83 
Apr 15 11:01:30 ian-latitude kernel: [  906.272000] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
Apr 15 11:01:30 ian-latitude kernel: [  906.272000] end_request: I/O error, dev sda, sector 39314051
Apr 15 11:01:30 ian-latitude kernel: [  906.272000] ata1: EH complete
Apr 15 11:01:30 ian-latitude kernel: [  906.272000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 11:01:30 ian-latitude kernel: [  906.272000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 11:01:30 ian-latitude kernel: [  906.272000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 11:01:30 ian-latitude kernel: [  906.272000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 11:01:30 ian-latitude kernel: [  906.272000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 11:01:30 ian-latitude kernel: [  906.272000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 11:01:30 ian-latitude kernel: [  906.272000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 11:01:30 ian-latitude kernel: [  906.272000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 11:01:34 ian-latitude kernel: [  910.804000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:01:34 ian-latitude kernel: [  910.804000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:01:34 ian-latitude kernel: [  910.804000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:01:34 ian-latitude kernel: [  910.804000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:01:35 ian-latitude kernel: [  910.844000] ata1.00: configured for UDMA/33
Apr 15 11:01:35 ian-latitude kernel: [  910.844000] ata1: EH complete
Apr 15 11:01:39 ian-latitude kernel: [  915.336000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:01:39 ian-latitude kernel: [  915.336000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:01:39 ian-latitude kernel: [  915.336000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:01:39 ian-latitude kernel: [  915.336000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:01:57 ian-latitude kernel: [  915.360000] ata1.00: configured for UDMA/33
Apr 15 11:01:57 ian-latitude kernel: [  915.360000] ata1: EH complete
Apr 15 11:01:57 ian-latitude kernel: [  919.792000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:01:57 ian-latitude kernel: [  919.792000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:01:57 ian-latitude kernel: [  919.792000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:01:57 ian-latitude kernel: [  919.792000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:01:57 ian-latitude kernel: [  919.820000] ata1.00: configured for UDMA/33
Apr 15 11:01:57 ian-latitude kernel: [  919.820000] ata1: EH complete
Apr 15 11:01:57 ian-latitude kernel: [  924.216000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:01:57 ian-latitude kernel: [  924.216000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:01:57 ian-latitude kernel: [  924.216000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:01:57 ian-latitude kernel: [  924.216000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:01:57 ian-latitude kernel: [  924.244000] ata1.00: configured for UDMA/33
Apr 15 11:01:57 ian-latitude kernel: [  924.244000] ata1: EH complete
Apr 15 11:01:57 ian-latitude kernel: [  928.664000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:01:57 ian-latitude kernel: [  928.664000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:01:57 ian-latitude kernel: [  928.664000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:01:57 ian-latitude kernel: [  928.664000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:01:57 ian-latitude kernel: [  928.688000] ata1.00: configured for UDMA/33
Apr 15 11:01:57 ian-latitude kernel: [  928.688000] ata1: EH complete
Apr 15 11:01:57 ian-latitude kernel: [  933.108000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:01:57 ian-latitude kernel: [  933.108000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:01:57 ian-latitude kernel: [  933.108000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:01:57 ian-latitude kernel: [  933.108000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:01:57 ian-latitude kernel: [  933.132000] ata1.00: configured for UDMA/33
Apr 15 11:01:57 ian-latitude kernel: [  933.132000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Apr 15 11:01:57 ian-latitude kernel: [  933.132000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Apr 15 11:01:57 ian-latitude kernel: [  933.132000] Descriptor sense data with sense descriptors (in hex):
Apr 15 11:01:57 ian-latitude kernel: [  933.132000]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr 15 11:01:57 ian-latitude kernel: [  933.132000]         02 57 e2 83 
Apr 15 11:01:57 ian-latitude kernel: [  933.132000] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
Apr 15 11:01:57 ian-latitude kernel: [  933.132000] end_request: I/O error, dev sda, sector 39314051
Apr 15 11:01:57 ian-latitude kernel: [  933.132000] ata1: EH complete
Apr 15 11:01:57 ian-latitude kernel: [  933.148000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 11:01:57 ian-latitude kernel: [  933.148000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 11:01:57 ian-latitude kernel: [  933.148000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 11:01:57 ian-latitude kernel: [  933.148000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 11:01:57 ian-latitude kernel: [  933.164000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 11:01:57 ian-latitude kernel: [  933.176000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 11:01:57 ian-latitude kernel: [  933.176000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 11:01:57 ian-latitude kernel: [  933.176000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 11:02:02 ian-latitude kernel: [  938.064000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:02:02 ian-latitude kernel: [  938.064000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:02:02 ian-latitude kernel: [  938.064000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:02:02 ian-latitude kernel: [  938.064000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:02:02 ian-latitude kernel: [  938.088000] ata1.00: configured for UDMA/33
Apr 15 11:02:02 ian-latitude kernel: [  938.088000] ata1: EH complete
Apr 15 11:02:06 ian-latitude kernel: [  942.532000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:02:06 ian-latitude kernel: [  942.532000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:02:06 ian-latitude kernel: [  942.532000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:02:06 ian-latitude kernel: [  942.532000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:02:06 ian-latitude kernel: [  942.556000] ata1.00: configured for UDMA/33
Apr 15 11:02:06 ian-latitude kernel: [  942.556000] ata1: EH complete
Apr 15 11:02:10 ian-latitude kernel: [  946.764000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:02:10 ian-latitude kernel: [  946.764000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:02:10 ian-latitude kernel: [  946.764000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:02:10 ian-latitude kernel: [  946.764000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:02:10 ian-latitude kernel: [  946.792000] ata1.00: configured for UDMA/33
Apr 15 11:02:10 ian-latitude kernel: [  946.792000] ata1: EH complete
Apr 15 11:02:15 ian-latitude kernel: [  951.012000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:02:15 ian-latitude kernel: [  951.012000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:02:15 ian-latitude kernel: [  951.012000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:02:15 ian-latitude kernel: [  951.012000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:02:15 ian-latitude kernel: [  951.036000] ata1.00: configured for UDMA/33
Apr 15 11:02:15 ian-latitude kernel: [  951.036000] ata1: EH complete
Apr 15 11:02:19 ian-latitude kernel: [  955.488000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:02:19 ian-latitude kernel: [  955.488000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:02:19 ian-latitude kernel: [  955.488000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:02:19 ian-latitude kernel: [  955.488000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:02:19 ian-latitude kernel: [  955.516000] ata1.00: configured for UDMA/33
Apr 15 11:02:19 ian-latitude kernel: [  955.516000] ata1: EH complete
Apr 15 11:02:24 ian-latitude kernel: [  960.436000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:02:24 ian-latitude kernel: [  960.436000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:02:24 ian-latitude kernel: [  960.436000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:02:24 ian-latitude kernel: [  960.436000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:02:24 ian-latitude kernel: [  960.460000] ata1.00: configured for UDMA/33
Apr 15 11:02:24 ian-latitude kernel: [  960.460000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Apr 15 11:02:24 ian-latitude kernel: [  960.460000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Apr 15 11:02:24 ian-latitude kernel: [  960.460000] Descriptor sense data with sense descriptors (in hex):
Apr 15 11:02:24 ian-latitude kernel: [  960.460000]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr 15 11:02:24 ian-latitude kernel: [  960.460000]         02 57 e2 83 
Apr 15 11:02:24 ian-latitude kernel: [  960.460000] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
Apr 15 11:02:24 ian-latitude kernel: [  960.460000] end_request: I/O error, dev sda, sector 39314051
Apr 15 11:02:24 ian-latitude kernel: [  960.460000] ata1: EH complete
Apr 15 11:02:29 ian-latitude kernel: [  964.904000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:02:29 ian-latitude kernel: [  964.904000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:02:29 ian-latitude kernel: [  964.904000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:02:29 ian-latitude kernel: [  964.904000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:02:29 ian-latitude kernel: [  964.928000] ata1.00: configured for UDMA/33
Apr 15 11:02:29 ian-latitude kernel: [  964.928000] ata1: EH complete
Apr 15 11:02:33 ian-latitude kernel: [  969.380000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:02:33 ian-latitude kernel: [  969.380000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:02:33 ian-latitude kernel: [  969.380000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:02:33 ian-latitude kernel: [  969.380000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:02:33 ian-latitude kernel: [  969.404000] ata1.00: configured for UDMA/33
Apr 15 11:02:33 ian-latitude kernel: [  969.404000] ata1: EH complete
Apr 15 11:02:37 ian-latitude kernel: [  973.704000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:02:37 ian-latitude kernel: [  973.704000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:02:37 ian-latitude kernel: [  973.704000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:02:37 ian-latitude kernel: [  973.704000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:02:37 ian-latitude kernel: [  973.728000] ata1.00: configured for UDMA/33
Apr 15 11:02:37 ian-latitude kernel: [  973.728000] ata1: EH complete
Apr 15 11:02:42 ian-latitude kernel: [  978.172000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:02:42 ian-latitude kernel: [  978.172000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:02:42 ian-latitude kernel: [  978.172000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:02:42 ian-latitude kernel: [  978.172000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:02:42 ian-latitude kernel: [  978.196000] ata1.00: configured for UDMA/33
Apr 15 11:02:42 ian-latitude kernel: [  978.196000] ata1: EH complete
Apr 15 11:02:46 ian-latitude kernel: [  982.552000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:02:46 ian-latitude kernel: [  982.552000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:02:46 ian-latitude kernel: [  982.552000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:02:46 ian-latitude kernel: [  982.552000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:02:46 ian-latitude kernel: [  982.576000] ata1.00: configured for UDMA/33
Apr 15 11:02:46 ian-latitude kernel: [  982.576000] ata1: EH complete
Apr 15 11:02:51 ian-latitude kernel: [  987.020000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:02:51 ian-latitude kernel: [  987.020000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:02:51 ian-latitude kernel: [  987.020000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:02:51 ian-latitude kernel: [  987.020000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:02:51 ian-latitude kernel: [  987.044000] ata1.00: configured for UDMA/33
Apr 15 11:02:51 ian-latitude kernel: [  987.044000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Apr 15 11:02:51 ian-latitude kernel: [  987.044000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Apr 15 11:02:51 ian-latitude kernel: [  987.044000] Descriptor sense data with sense descriptors (in hex):
Apr 15 11:02:51 ian-latitude kernel: [  987.044000]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr 15 11:02:51 ian-latitude kernel: [  987.044000]         02 57 e2 83 
Apr 15 11:02:51 ian-latitude kernel: [  987.044000] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
Apr 15 11:02:51 ian-latitude kernel: [  987.044000] end_request: I/O error, dev sda, sector 39314051
Apr 15 11:02:51 ian-latitude kernel: [  987.044000] ata1: EH complete
Apr 15 11:02:51 ian-latitude kernel: [  987.044000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 11:02:51 ian-latitude kernel: [  987.044000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 11:02:51 ian-latitude kernel: [  987.044000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 11:02:51 ian-latitude kernel: [  987.044000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 11:02:51 ian-latitude kernel: [  987.044000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 11:02:51 ian-latitude kernel: [  987.044000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 11:02:51 ian-latitude kernel: [  987.044000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 11:02:51 ian-latitude kernel: [  987.048000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 11:02:55 ian-latitude kernel: [  991.464000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:02:55 ian-latitude kernel: [  991.464000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:02:55 ian-latitude kernel: [  991.464000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:02:55 ian-latitude kernel: [  991.464000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:02:55 ian-latitude kernel: [  991.552000] ata1.00: configured for UDMA/33
Apr 15 11:02:55 ian-latitude kernel: [  991.552000] ata1: EH complete
Apr 15 11:03:00 ian-latitude kernel: [  995.996000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:03:00 ian-latitude kernel: [  995.996000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:03:00 ian-latitude kernel: [  995.996000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:03:00 ian-latitude kernel: [  995.996000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:03:00 ian-latitude kernel: [  996.024000] ata1.00: configured for UDMA/33
Apr 15 11:03:00 ian-latitude kernel: [  996.024000] ata1: EH complete
Apr 15 11:03:04 ian-latitude kernel: [ 1000.456000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:03:04 ian-latitude kernel: [ 1000.456000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:03:04 ian-latitude kernel: [ 1000.456000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:03:04 ian-latitude kernel: [ 1000.456000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:03:04 ian-latitude kernel: [ 1000.480000] ata1.00: configured for UDMA/33
Apr 15 11:03:04 ian-latitude kernel: [ 1000.480000] ata1: EH complete
Apr 15 11:03:08 ian-latitude kernel: [ 1004.788000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:03:08 ian-latitude kernel: [ 1004.788000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:03:08 ian-latitude kernel: [ 1004.788000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:03:08 ian-latitude kernel: [ 1004.788000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:03:08 ian-latitude kernel: [ 1004.812000] ata1.00: configured for UDMA/33
Apr 15 11:03:08 ian-latitude kernel: [ 1004.812000] ata1: EH complete
Apr 15 11:03:13 ian-latitude kernel: [ 1009.224000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:03:13 ian-latitude kernel: [ 1009.224000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:03:13 ian-latitude kernel: [ 1009.224000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:03:13 ian-latitude kernel: [ 1009.224000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:03:13 ian-latitude kernel: [ 1009.248000] ata1.00: configured for UDMA/33
Apr 15 11:03:13 ian-latitude kernel: [ 1009.248000] ata1: EH complete
Apr 15 11:03:17 ian-latitude kernel: [ 1013.692000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:03:17 ian-latitude kernel: [ 1013.692000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:03:17 ian-latitude kernel: [ 1013.692000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:03:17 ian-latitude kernel: [ 1013.692000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:03:17 ian-latitude kernel: [ 1013.716000] ata1.00: configured for UDMA/33
Apr 15 11:03:17 ian-latitude kernel: [ 1013.716000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Apr 15 11:03:17 ian-latitude kernel: [ 1013.716000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Apr 15 11:03:17 ian-latitude kernel: [ 1013.716000] Descriptor sense data with sense descriptors (in hex):
Apr 15 11:03:17 ian-latitude kernel: [ 1013.716000]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr 15 11:03:17 ian-latitude kernel: [ 1013.716000]         02 57 e2 83 
Apr 15 11:03:17 ian-latitude kernel: [ 1013.716000] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
Apr 15 11:03:17 ian-latitude kernel: [ 1013.716000] end_request: I/O error, dev sda, sector 39314051
Apr 15 11:03:17 ian-latitude kernel: [ 1013.716000] ata1: EH complete
Apr 15 11:03:17 ian-latitude kernel: [ 1013.716000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 11:03:17 ian-latitude kernel: [ 1013.716000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 11:03:17 ian-latitude kernel: [ 1013.716000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 11:03:17 ian-latitude kernel: [ 1013.720000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 11:03:22 ian-latitude kernel: [ 1018.180000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:03:22 ian-latitude kernel: [ 1018.180000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:03:22 ian-latitude kernel: [ 1018.180000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:03:22 ian-latitude kernel: [ 1018.180000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:03:22 ian-latitude kernel: [ 1018.228000] ata1.00: configured for UDMA/33
Apr 15 11:03:22 ian-latitude kernel: [ 1018.228000] ata1: EH complete
Apr 15 11:03:26 ian-latitude kernel: [ 1022.616000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:03:26 ian-latitude kernel: [ 1022.616000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:03:26 ian-latitude kernel: [ 1022.616000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:03:26 ian-latitude kernel: [ 1022.616000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:03:26 ian-latitude kernel: [ 1022.640000] ata1.00: configured for UDMA/33
Apr 15 11:03:26 ian-latitude kernel: [ 1022.640000] ata1: EH complete
Apr 15 11:03:31 ian-latitude kernel: [ 1027.148000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:03:31 ian-latitude kernel: [ 1027.148000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:03:31 ian-latitude kernel: [ 1027.148000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:03:31 ian-latitude kernel: [ 1027.148000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:03:31 ian-latitude kernel: [ 1027.172000] ata1.00: configured for UDMA/33
Apr 15 11:03:31 ian-latitude kernel: [ 1027.172000] ata1: EH complete
Apr 15 11:03:35 ian-latitude kernel: [ 1031.604000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:03:35 ian-latitude kernel: [ 1031.604000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:03:35 ian-latitude kernel: [ 1031.604000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:03:35 ian-latitude kernel: [ 1031.604000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:03:35 ian-latitude kernel: [ 1031.628000] ata1.00: configured for UDMA/33
Apr 15 11:03:35 ian-latitude kernel: [ 1031.628000] ata1: EH complete
Apr 15 11:03:40 ian-latitude kernel: [ 1035.960000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:03:40 ian-latitude kernel: [ 1035.960000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:03:40 ian-latitude kernel: [ 1035.960000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:03:40 ian-latitude kernel: [ 1035.960000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:03:40 ian-latitude kernel: [ 1035.984000] ata1.00: configured for UDMA/33
Apr 15 11:03:40 ian-latitude kernel: [ 1035.984000] ata1: EH complete
Apr 15 11:03:44 ian-latitude kernel: [ 1040.440000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:03:44 ian-latitude kernel: [ 1040.440000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:03:44 ian-latitude kernel: [ 1040.440000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:03:44 ian-latitude kernel: [ 1040.440000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:03:44 ian-latitude kernel: [ 1040.464000] ata1.00: configured for UDMA/33
Apr 15 11:03:44 ian-latitude kernel: [ 1040.464000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Apr 15 11:03:44 ian-latitude kernel: [ 1040.464000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Apr 15 11:03:44 ian-latitude kernel: [ 1040.464000] Descriptor sense data with sense descriptors (in hex):
Apr 15 11:03:44 ian-latitude kernel: [ 1040.464000]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr 15 11:03:44 ian-latitude kernel: [ 1040.464000]         02 57 e2 83 
Apr 15 11:03:44 ian-latitude kernel: [ 1040.464000] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
Apr 15 11:03:44 ian-latitude kernel: [ 1040.464000] end_request: I/O error, dev sda, sector 39314051
Apr 15 11:03:44 ian-latitude kernel: [ 1040.464000] ata1: EH complete
Apr 15 11:03:49 ian-latitude kernel: [ 1044.896000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:03:49 ian-latitude kernel: [ 1044.896000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:03:49 ian-latitude kernel: [ 1044.896000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:03:49 ian-latitude kernel: [ 1044.896000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:03:49 ian-latitude kernel: [ 1044.920000] ata1.00: configured for UDMA/33
Apr 15 11:03:49 ian-latitude kernel: [ 1044.920000] ata1: EH complete
Apr 15 11:03:53 ian-latitude kernel: [ 1049.432000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:03:53 ian-latitude kernel: [ 1049.432000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:03:53 ian-latitude kernel: [ 1049.432000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:03:53 ian-latitude kernel: [ 1049.432000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:03:53 ian-latitude kernel: [ 1049.456000] ata1.00: configured for UDMA/33
Apr 15 11:03:53 ian-latitude kernel: [ 1049.456000] ata1: EH complete
Apr 15 11:03:58 ian-latitude kernel: [ 1053.908000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:03:58 ian-latitude kernel: [ 1053.908000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:03:58 ian-latitude kernel: [ 1053.908000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:03:58 ian-latitude kernel: [ 1053.908000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:03:58 ian-latitude kernel: [ 1053.932000] ata1.00: configured for UDMA/33
Apr 15 11:03:58 ian-latitude kernel: [ 1053.932000] ata1: EH complete
Apr 15 11:04:02 ian-latitude kernel: [ 1058.768000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:04:02 ian-latitude kernel: [ 1058.768000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:04:02 ian-latitude kernel: [ 1058.768000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:04:02 ian-latitude kernel: [ 1058.768000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:04:02 ian-latitude kernel: [ 1058.792000] ata1.00: configured for UDMA/33
Apr 15 11:04:02 ian-latitude kernel: [ 1058.792000] ata1: EH complete
Apr 15 11:04:07 ian-latitude kernel: [ 1063.232000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:04:07 ian-latitude kernel: [ 1063.232000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:04:07 ian-latitude kernel: [ 1063.232000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:04:07 ian-latitude kernel: [ 1063.232000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:04:07 ian-latitude kernel: [ 1063.260000] ata1.00: configured for UDMA/33
Apr 15 11:04:07 ian-latitude kernel: [ 1063.260000] ata1: EH complete
Apr 15 11:04:11 ian-latitude kernel: [ 1067.644000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:04:11 ian-latitude kernel: [ 1067.644000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:04:11 ian-latitude kernel: [ 1067.644000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:04:11 ian-latitude kernel: [ 1067.644000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:04:11 ian-latitude kernel: [ 1067.668000] ata1.00: configured for UDMA/33
Apr 15 11:04:11 ian-latitude kernel: [ 1067.668000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Apr 15 11:04:11 ian-latitude kernel: [ 1067.668000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Apr 15 11:04:11 ian-latitude kernel: [ 1067.668000] Descriptor sense data with sense descriptors (in hex):
Apr 15 11:04:11 ian-latitude kernel: [ 1067.668000]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr 15 11:04:11 ian-latitude kernel: [ 1067.668000]         02 57 e2 83 
Apr 15 11:04:11 ian-latitude kernel: [ 1067.668000] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
Apr 15 11:04:11 ian-latitude kernel: [ 1067.668000] end_request: I/O error, dev sda, sector 39314051
Apr 15 11:04:11 ian-latitude kernel: [ 1067.668000] ata1: EH complete
Apr 15 11:04:11 ian-latitude kernel: [ 1067.668000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 11:04:11 ian-latitude kernel: [ 1067.684000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 11:04:11 ian-latitude kernel: [ 1067.684000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 11:04:11 ian-latitude kernel: [ 1067.688000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 11:04:11 ian-latitude kernel: [ 1067.696000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 11:04:11 ian-latitude kernel: [ 1067.696000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 11:04:11 ian-latitude kernel: [ 1067.696000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 11:04:11 ian-latitude kernel: [ 1067.708000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 11:04:16 ian-latitude kernel: [ 1072.304000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:04:39 ian-latitude kernel: [ 1072.304000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:04:39 ian-latitude kernel: [ 1072.304000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:04:39 ian-latitude kernel: [ 1072.304000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:04:39 ian-latitude kernel: [ 1072.416000] ata1.00: configured for UDMA/33
Apr 15 11:04:39 ian-latitude kernel: [ 1072.416000] ata1: EH complete
Apr 15 11:04:39 ian-latitude kernel: [ 1076.868000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:04:39 ian-latitude kernel: [ 1076.868000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:04:39 ian-latitude kernel: [ 1076.868000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:04:39 ian-latitude kernel: [ 1076.868000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:04:39 ian-latitude kernel: [ 1076.892000] ata1.00: configured for UDMA/33
Apr 15 11:04:39 ian-latitude kernel: [ 1076.892000] ata1: EH complete
Apr 15 11:04:39 ian-latitude kernel: [ 1081.348000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:04:39 ian-latitude kernel: [ 1081.348000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:04:39 ian-latitude kernel: [ 1081.348000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:04:39 ian-latitude kernel: [ 1081.348000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:04:39 ian-latitude kernel: [ 1081.372000] ata1.00: configured for UDMA/33
Apr 15 11:04:39 ian-latitude kernel: [ 1081.372000] ata1: EH complete
Apr 15 11:04:39 ian-latitude kernel: [ 1085.816000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:04:39 ian-latitude kernel: [ 1085.816000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:04:39 ian-latitude kernel: [ 1085.816000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:04:39 ian-latitude kernel: [ 1085.816000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:04:39 ian-latitude kernel: [ 1085.840000] ata1.00: configured for UDMA/33
Apr 15 11:04:39 ian-latitude kernel: [ 1085.840000] ata1: EH complete
Apr 15 11:04:39 ian-latitude kernel: [ 1090.272000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:04:39 ian-latitude kernel: [ 1090.272000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:04:39 ian-latitude kernel: [ 1090.272000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:04:39 ian-latitude kernel: [ 1090.272000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:04:39 ian-latitude kernel: [ 1090.296000] ata1.00: configured for UDMA/33
Apr 15 11:04:39 ian-latitude kernel: [ 1090.296000] ata1: EH complete
Apr 15 11:04:39 ian-latitude kernel: [ 1094.808000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 15 11:04:39 ian-latitude kernel: [ 1094.808000] ata1.00: (BMDMA stat 0x24)
Apr 15 11:04:39 ian-latitude kernel: [ 1094.808000] ata1.00: cmd c8/00:08:7f:e2:57/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
Apr 15 11:04:39 ian-latitude kernel: [ 1094.808000]          res 51/01:04:83:e2:57/00:00:00:00:00/e2 Emask 0x1 (device error)
Apr 15 11:04:39 ian-latitude kernel: [ 1094.832000] ata1.00: configured for UDMA/33
Apr 15 11:04:39 ian-latitude kernel: [ 1094.832000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Apr 15 11:04:39 ian-latitude kernel: [ 1094.832000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Apr 15 11:04:39 ian-latitude kernel: [ 1094.832000] Descriptor sense data with sense descriptors (in hex):
Apr 15 11:04:39 ian-latitude kernel: [ 1094.832000]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr 15 11:04:39 ian-latitude kernel: [ 1094.832000]         02 57 e2 83 
Apr 15 11:04:39 ian-latitude kernel: [ 1094.832000] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
Apr 15 11:04:39 ian-latitude kernel: [ 1094.832000] end_request: I/O error, dev sda, sector 39314051
Apr 15 11:04:39 ian-latitude kernel: [ 1094.832000] ata1: EH complete
Apr 15 11:04:39 ian-latitude kernel: [ 1094.848000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 11:04:39 ian-latitude kernel: [ 1094.848000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 11:04:39 ian-latitude kernel: [ 1094.848000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 11:04:39 ian-latitude kernel: [ 1094.852000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 15 11:04:39 ian-latitude kernel: [ 1094.868000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 15 11:04:39 ian-latitude kernel: [ 1094.868000] sd 0:0:0:0: [sda] Write Protect is off
Apr 15 11:04:39 ian-latitude kernel: [ 1094.868000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 15 11:04:39 ian-latitude kernel: [ 1094.868000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```

Other system information:
```

ian@ian-latitude:/var/log$ uname -a
Linux ian-latitude 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

```

```

ian@ian-latitude:/var/log$ fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfd0efd0e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1020     8193118+   7  HPFS/NTFS
/dev/sda2            1021        1263     1951897+  82  Linux swap / Solaris
/dev/sda3            1264        2479     9767520   83  Linux
/dev/sda4            2480        9729    58235625    7  HPFS/NTFS
ian@ian-latitude:/var/log$ 

```

```

ian@ian-latitude:/var/log$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
03:01.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller (rev 40)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

```

Thanks to anyone who can help!

---

### Post by schmutt on 2008-04-15
Update:

This is working for now:
1. move .mozilla-thunderbird to .mozilla-thunderbird.old
2. uninstall then reinstall Thunderbird
3. After moving abook.mab to the new .mozilla-thunderbird folder, same problems repeat. Looks like my old addressbook (from a previous install under winXP) is corrupt
4. Upon deleting abook.mab, performance seems normal.

Maybe this was a newbie post, but I'd still be interested to know what would cause this to happen.

---

### Post by schmutt on 2008-04-16
Still having problems with this, now related to Firefox.

 Using a different user account, loading any page in firefox that involves looking up password information crashed firefox. Deleted the .mozilla profile, and performance for that user account returned to normal.

I don't think I have a bad disk, as it is brand new. Am I wrong? Is this a known mozilla problem? I would appreciate any advice.

---

