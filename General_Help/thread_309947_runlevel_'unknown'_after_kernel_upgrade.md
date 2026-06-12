---
title: "runlevel 'unknown' after kernel upgrade"
date: 2006-11-30
forum: General Help
---

### Post by kerm1t on 2006-11-30
Hi,

I've recently upgraded my kernel to 2.6.17.9 (needed a few features). When my machine boots, the network interface comes up, but none of the network services start. When I try to see which runlevel it's in:

# runlevel
unknown

If I 'telinit 3', network services start, and runlevel returns:

S 3

..indicating that it was previously in single user mode, right?

Looking in the process list (before I 'telinit 3'), I see

init [S]

Any thoughts on what's going on?

Here's the output of dmesg:


```
# dmesg
[4294667.296000] Linux version 2.6.17.9pete (root@aj3) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP Thu Nov 9 20:43:05 GMT 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[4294667.296000]  BIOS-e820: 0000000000100000 - 00000000dffc0000 (usable)
[4294667.296000]  BIOS-e820: 00000000dffc0000 - 00000000dffcfc00 (ACPI data)
[4294667.296000]  BIOS-e820: 00000000dffcfc00 - 00000000dffff000 (reserved)
[4294667.296000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fec00000 - 00000000fec90000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[4294667.296000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[4294667.296000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[4294667.296000]  BIOS-e820: 0000000100000000 - 00000001a0000000 (usable)
[4294667.296000] Warning only 4GB will be used.
[4294667.296000] Use a PAE enabled kernel.
[4294667.296000] 3200MB HIGHMEM available.
[4294667.296000] 896MB LOWMEM available.
[4294667.296000] found SMP MP-table at 000fe710
[4294667.296000] On node 0 totalpages: 1048576
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   Normal zone: 225280 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 819200 pages, LIFO batch:31
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fd5b0
[4294667.296000] ACPI: RSDT (v001 DELL   PE BKC   0x00000001 MSFT 0x0100000a) @ 0x000fd5c4
[4294667.296000] ACPI: FADT (v001 DELL   PE BKC   0x00000001 MSFT 0x0100000a) @ 0x000fd620
[4294667.296000] ACPI: MADT (v001 DELL   PE BKC   0x00000001 MSFT 0x0100000a) @ 0x000fd694
[4294667.296000] ACPI: SPCR (v001 DELL   PE BKC   0x00000001 MSFT 0x0100000a) @ 0x000fd774
[4294667.296000] ACPI: HPET (v001 DELL   PE BKC   0x00000001 MSFT 0x0100000a) @ 0x000fd7c4
[4294667.296000] ACPI: MCFG (v001 DELL   PE BKC   0x00000001 MSFT 0x0100000a) @ 0x000fd7fc
[4294667.296000] ACPI: DSDT (v001 DELL   PE BKC   0x00000001 MSFT 0x0100000e) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x808
[4294667.296000] ACPI: Local APIC address 0xfee00000
[4294667.296000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[4294667.296000] Processor #0 15:4 APIC version 20
[4294667.296000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x06] enabled)
[4294667.296000] Processor #6 15:4 APIC version 20
[4294667.296000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[4294667.296000] Processor #1 15:4 APIC version 20
[4294667.296000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x07] enabled)
[4294667.296000] Processor #7 15:4 APIC version 20
[4294667.296000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x02] disabled)
[4294667.296000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x04] disabled)
[4294667.296000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x03] disabled)
[4294667.296000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x05] disabled)
[4294667.296000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[4294667.296000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[4294667.296000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[4294667.296000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
[4294667.296000] ACPI: LAPIC_NMI (acpi_id[0x05] high edge lint[0x1])
[4294667.296000] ACPI: LAPIC_NMI (acpi_id[0x06] high edge lint[0x1])
[4294667.296000] ACPI: LAPIC_NMI (acpi_id[0x07] high edge lint[0x1])
[4294667.296000] ACPI: LAPIC_NMI (acpi_id[0x08] high edge lint[0x1])
[4294667.296000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[4294667.296000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[4294667.296000] ACPI: IOAPIC (id[0x09] address[0xfec80000] gsi_base[32])
[4294667.296000] IOAPIC[1]: apic_id 9, version 32, address 0xfec80000, GSI 32-55
[4294667.296000] ACPI: IOAPIC (id[0x0a] address[0xfec83000] gsi_base[64])
[4294667.296000] IOAPIC[2]: apic_id 10, version 32, address 0xfec83000, GSI 64-87
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[4294667.296000] ACPI: IRQ0 used by override.
[4294667.296000] ACPI: IRQ2 used by override.
[4294667.296000] ACPI: IRQ9 used by override.
[4294667.296000] Enabling APIC mode:  Flat.  Using 3 I/O APICs
[4294667.296000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[4294667.296000] Using ACPI (MADT) for SMP configuration information
[4294667.296000] Allocating PCI resources starting at f1000000 (gap: f0000000:0ec00000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/md0 ro single
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] mapped IOAPIC to ffffc000 (fec00000)
[4294667.296000] mapped IOAPIC to ffffb000 (fec80000)
[4294667.296000] mapped IOAPIC to ffffa000 (fec83000)
[4294667.296000] Enabling fast FPU save and restore... done.
[4294667.296000] Enabling unmasked SIMD FPU exception support... done.
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[4294667.296000] Console: colour VGA+ 80x25
[4294667.296000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[4294667.296000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294667.296000] Memory: 3625224k/4194304k available (2162k kernel code, 43352k reserved, 608k data, 320k init, 2752256k highmem)
[4294667.296000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294667.296000] hpet0: at MMIO 0xfed00000 (virtual 0xf8800000), IRQs 2, 8, 0
[4294667.296000] hpet0: 3 64-bit timers, 14318180 Hz
[4294667.296000] Using HPET for base-timer
[4294667.296000] Using HPET for gettimeofday
[4294667.296000] Detected 2993.212 MHz processor.
[4294667.296000] Using hpet for high-res timesource
[4294667.357000] Calibrating delay using timer specific routine.. 5988.91 BogoMIPS (lpj=2994459)
[4294667.357000] Security Framework v1.0.0 initialized
[4294667.357000] SELinux:  Disabled at boot.
[4294667.357000] Mount-cache hash table entries: 512
[4294667.357000] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000641d 00000000 00000000
[4294667.357000] CPU: After vendor identify, caps: bfebfbff 20100000 00000000 00000000 0000641d 00000000 00000000
[4294667.357000] monitor/mwait feature present.
[4294667.357000] using mwait in idle threads.
[4294667.357000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[4294667.357000] CPU: L2 cache: 1024K
[4294667.357000] CPU: Physical Processor ID: 0
[4294667.357000] CPU: After all inits, caps: bfebfbff 20100000 00000000 00000180 0000641d 00000000 00000000
[4294667.357000] Intel machine check architecture supported.
[4294667.357000] Intel machine check reporting enabled on CPU#0.
[4294667.357000] CPU0: Intel P4/Xeon Extended MCE MSRs (24) available
[4294667.358000] Checking 'hlt' instruction... OK.
[4294667.362000] SMP alternatives: switching to UP code
[4294667.368000] CPU0: Intel(R) Xeon(TM) CPU 3.00GHz stepping 01
[4294667.368000] SMP alternatives: switching to SMP code
[4294667.368000] Booting processor 1/1 eip 3000
[4294667.379000] Initializing CPU#1
[4294667.440000] Calibrating delay using timer specific routine.. 5985.39 BogoMIPS (lpj=2992697)
[4294667.440000] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000641d 00000000 00000000
[4294667.440000] CPU: After vendor identify, caps: bfebfbff 20100000 00000000 00000000 0000641d 00000000 00000000
[4294667.440000] monitor/mwait feature present.
[4294667.440000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[4294667.440000] CPU: L2 cache: 1024K
[4294667.440000] CPU: Physical Processor ID: 0
[4294667.440000] CPU: After all inits, caps: bfebfbff 20100000 00000000 00000180 0000641d 00000000 00000000
[4294667.440000] Intel machine check architecture supported.
[4294667.440000] Intel machine check reporting enabled on CPU#1.
[4294667.440000] CPU1: Intel P4/Xeon Extended MCE MSRs (24) available
[4294667.440000] CPU1: Intel(R) Xeon(TM) CPU 3.00GHz stepping 01
[4294667.440000] SMP alternatives: switching to SMP code
[4294667.441000] Booting processor 2/6 eip 3000
[4294667.451000] Initializing CPU#2
[4294667.512000] Calibrating delay using timer specific routine.. 5985.44 BogoMIPS (lpj=2992722)
[4294667.512000] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000641d 00000000 00000000
[4294667.512000] CPU: After vendor identify, caps: bfebfbff 20100000 00000000 00000000 0000641d 00000000 00000000
[4294667.512000] monitor/mwait feature present.
[4294667.512000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[4294667.512000] CPU: L2 cache: 1024K
[4294667.512000] CPU: Physical Processor ID: 3
[4294667.512000] CPU: After all inits, caps: bfebfbff 20100000 00000000 00000180 0000641d 00000000 00000000
[4294667.512000] Intel machine check architecture supported.
[4294667.512000] Intel machine check reporting enabled on CPU#2.
[4294667.512000] CPU2: Intel P4/Xeon Extended MCE MSRs (24) available
[4294667.512000] CPU2: Intel(R) Xeon(TM) CPU 3.00GHz stepping 01
[4294667.512000] SMP alternatives: switching to SMP code
[4294667.513000] Booting processor 3/7 eip 3000
[4294667.523000] Initializing CPU#3
[4294667.584000] Calibrating delay using timer specific routine.. 5985.50 BogoMIPS (lpj=2992754)
[4294667.584000] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000641d 00000000 00000000
[4294667.584000] CPU: After vendor identify, caps: bfebfbff 20100000 00000000 00000000 0000641d 00000000 00000000
[4294667.584000] monitor/mwait feature present.
[4294667.584000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[4294667.584000] CPU: L2 cache: 1024K
[4294667.584000] CPU: Physical Processor ID: 3
[4294667.584000] CPU: After all inits, caps: bfebfbff 20100000 00000000 00000180 0000641d 00000000 00000000
[4294667.584000] Intel machine check architecture supported.
[4294667.584000] Intel machine check reporting enabled on CPU#3.
[4294667.584000] CPU3: Intel P4/Xeon Extended MCE MSRs (24) available
[4294667.584000] CPU3: Intel(R) Xeon(TM) CPU 3.00GHz stepping 01
[4294667.584000] Total of 4 processors activated (23945.26 BogoMIPS).
[4294667.585000] ENABLING IO-APIC IRQs
[4294667.585000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[4294667.698000] checking TSC synchronization across 4 CPUs: passed.
[4294667.701000] Brought up 4 CPUs
[4294667.760000] migration_cost=1000,2000
[4294667.760000] checking if image is initramfs... it is
[4294668.251000] Freeing initrd memory: 6073k freed
[4294668.252000] NET: Registered protocol family 16
[4294668.252000] EISA bus registered
[4294668.252000] ACPI: bus type pci registered
[4294668.252000] PCI: Using MMCONFIG
[4294668.253000] Setting up standard PCI resources
[4294668.253000] ACPI: Subsystem revision 20060127
[4294668.261000] ACPI: Interpreter enabled
[4294668.261000] ACPI: Using IOAPIC for interrupt routing
[4294668.262000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294668.262000] PCI: Probing PCI hardware (bus 00)
[4294668.267000] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[4294668.267000] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[4294668.267000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[4294668.267000] PCI: PXH quirk detected, disabling MSI for SHPC device
[4294668.267000] PCI: PXH quirk detected, disabling MSI for SHPC device
[4294668.268000] Boot video device is 0000:09:0d.0
[4294668.268000] PCI: Transparent bridge - 0000:00:1e.0
[4294668.268000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294668.273000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PALO._PRT]
[4294668.273000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PALO.DOBA._PRT]
[4294668.274000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PALO.DOBB._PRT]
[4294668.274000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PBLO._PRT]
[4294668.275000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.VPR0._PRT]
[4294668.275000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PBHI._PRT]
[4294668.276000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PBHI.PXB1._PRT]
[4294668.276000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PBHI.PXB2._PRT]
[4294668.276000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PICH._PRT]
[4294668.277000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12)
[4294668.277000] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 10 11 12)
[4294668.278000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *7 10 11 12)
[4294668.279000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12)
[4294668.279000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12) *0, disabled.
[4294668.280000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12) *0, disabled.
[4294668.281000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12) *0, disabled.
[4294668.282000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12)
[4294668.282000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294668.282000] pnp: PnP ACPI init
[4294668.287000] pnp: PnP ACPI: found 10 devices
[4294668.287000] PnPBIOS: Disabled by ACPI PNP
[4294668.287000] PCI: Using ACPI for IRQ routing
[4294668.287000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294668.288000] pnp: 00:07: ioport range 0x800-0x87f could not be reserved
[4294668.288000] pnp: 00:07: ioport range 0x880-0x8bf has been reserved
[4294668.288000] pnp: 00:07: ioport range 0x8c0-0x8df has been reserved
[4294668.288000] pnp: 00:07: ioport range 0x8e0-0x8e3 has been reserved
[4294668.288000] pnp: 00:07: ioport range 0xc00-0xc0f has been reserved
[4294668.288000] pnp: 00:07: ioport range 0xc10-0xc1f has been reserved
[4294668.288000] pnp: 00:07: ioport range 0xca0-0xcaf has been reserved
[4294668.288000] pnp: 00:07: ioport range 0xc20-0xc3f has been reserved
[4294668.288000] PCI: Bridge: 0000:01:00.0
[4294668.288000]   IO window: e000-efff
[4294668.288000]   MEM window: fe900000-feafffff
[4294668.289000]   PREFETCH window: f9000000-f9ffffff
[4294668.289000] PCI: Bridge: 0000:01:00.2
[4294668.289000]   IO window: disabled.
[4294668.289000]   MEM window: fe800000-fe8fffff
[4294668.289000]   PREFETCH window: f8f00000-f8ffffff
[4294668.289000] PCI: Bridge: 0000:00:02.0
[4294668.289000]   IO window: e000-efff
[4294668.289000]   MEM window: fe700000-feafffff
[4294668.289000]   PREFETCH window: f8000000-f9ffffff
[4294668.289000] PCI: Bridge: 0000:00:04.0
[4294668.289000]   IO window: disabled.
[4294668.289000]   MEM window: disabled.
[4294668.289000]   PREFETCH window: disabled.
[4294668.291000] PCI: Bridge: 0000:05:00.0
[4294668.291000]   IO window: d000-dfff
[4294668.291000]   MEM window: fe500000-fe6fffff
[4294668.291000]   PREFETCH window: disabled.
[4294668.291000] PCI: Bridge: 0000:05:00.2
[4294668.291000]   IO window: c000-cfff
[4294668.291000]   MEM window: fe300000-fe4fffff
[4294668.291000]   PREFETCH window: disabled.
[4294668.292000] PCI: Bridge: 0000:00:05.0
[4294668.292000]   IO window: c000-dfff
[4294668.292000]   MEM window: fe200000-fe6fffff
[4294668.292000]   PREFETCH window: disabled.
[4294668.292000] PCI: Bridge: 0000:00:06.0
[4294668.292000]   IO window: disabled.
[4294668.292000]   MEM window: disabled.
[4294668.292000]   PREFETCH window: disabled.
[4294668.292000] PCI: Bridge: 0000:00:1e.0
[4294668.292000]   IO window: b000-bfff
[4294668.292000]   MEM window: fe000000-fe1fffff
[4294668.292000]   PREFETCH window: f0000000-f7ffffff
[4294668.292000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294668.292000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[4294668.292000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[4294668.292000] PCI: Setting latency timer of device 0000:01:00.2 to 64
[4294668.292000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294668.293000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[4294668.293000] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294668.293000] PCI: Setting latency timer of device 0000:00:05.0 to 64
[4294668.293000] PCI: Setting latency timer of device 0000:05:00.0 to 64
[4294668.293000] PCI: Setting latency timer of device 0000:05:00.2 to 64
[4294668.293000] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294668.293000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[4294668.293000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[4294668.293000] NET: Registered protocol family 2
[4294668.307000] IP route cache hash table entries: 131072 (order: 7, 524288 bytes)
[4294668.308000] TCP established hash table entries: 524288 (order: 10, 4194304 bytes)
[4294668.312000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[4294668.313000] TCP: Hash tables configured (established 524288 bind 65536)
[4294668.313000] TCP reno registered
[4294668.315000] audit: initializing netlink socket (disabled)
[4294668.315000] audit(1164828076.314:1): initialized
[4294668.315000] highmem bounce pool size: 64 pages
[4294668.316000] VFS: Disk quotas dquot_6.5.1
[4294668.316000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294668.316000] Initializing Cryptographic API
[4294668.316000] io scheduler noop registered
[4294668.316000] io scheduler anticipatory registered (default)
[4294668.316000] io scheduler deadline registered
[4294668.316000] io scheduler cfq registered
[4294668.317000] Intel E7520/7320/7525 detected.<6>ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294668.317000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[4294668.317000] Allocate Port Service[0000:00:02.0:pcie00]
[4294668.317000] Allocate Port Service[0000:00:02.0:pcie01]
[4294668.317000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294668.317000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[4294668.317000] Allocate Port Service[0000:00:04.0:pcie00]
[4294668.317000] Allocate Port Service[0000:00:04.0:pcie01]
[4294668.317000] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294668.318000] PCI: Setting latency timer of device 0000:00:05.0 to 64
[4294668.318000] Allocate Port Service[0000:00:05.0:pcie00]
[4294668.318000] Allocate Port Service[0000:00:05.0:pcie01]
[4294668.318000] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294668.318000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[4294668.318000] Allocate Port Service[0000:00:06.0:pcie00]
[4294668.318000] Allocate Port Service[0000:00:06.0:pcie01]
[4294668.318000] isapnp: Scanning for PnP cards...
[4294668.676000] isapnp: No Plug & Play device found
[4294668.711000] Real Time Clock Driver v1.12ac
[4294668.711000] hpet_resources: 0xfed00000 is busy
[4294668.711000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[4294668.712000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[4294668.712000] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[4294668.713000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294668.714000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294668.714000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294668.714000] PNP: No PS/2 controller found. Probing ports directly.
[4294668.716000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294668.717000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294668.717000] mice: PS/2 mouse device common for all mice
[4294668.717000] EISA: Probing bus 0 at eisa.0
[4294668.717000] EISA: Detected 0 cards.
[4294668.717000] TCP bic registered
[4294668.717000] NET: Registered protocol family 1
[4294668.717000] NET: Registered protocol family 8
[4294668.717000] NET: Registered protocol family 20
[4294668.718000] Starting balanced_irq
[4294668.718000] Using IPI No-Shortcut mode
[4294668.718000] ACPI wakeup devices:
[4294668.718000] PCI0 PALO PBLO VPR0 PBHI PICH
[4294668.718000] ACPI: (supports S0 S4 S5)
[4294668.719000] Freeing unused kernel memory: 320k freed
[4294669.210000] SCSI subsystem initialized
[4294669.213000] Fusion MPT base driver 3.03.09
[4294669.213000] Copyright (c) 1999-2005 LSI Logic Corporation
[4294669.216000] Fusion MPT SPI Host driver 3.03.09
[4294669.216000] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 34 (level, low) -> IRQ 177
[4294669.216000] mptbase: Initiating ioc0 bringup
[4294669.335000] ioc0: 53C1030: Capabilities={Initiator,Target}
[4294669.475000] scsi0 : ioc0: LSI53C1030, FwRev=01032300h, Ports=1, MaxQ=255, IRQ=177
[4294670.260000]   Vendor: MAXTOR    Model: ATLAS10K5_146SCA  Rev: JNZM
[4294670.261000]   Type:   Direct-Access                      ANSI SCSI revision: 03
[4294670.261000]  target0:0:0: Beginning Domain Validation
[4294670.275000]  target0:0:0: Ending Domain Validation
[4294670.275000]  target0:0:0: FAST-160 WIDE SCSI 320.0 MB/s DT IU RTI (6.25 ns, offset 127)
[4294670.278000]   Vendor: MAXTOR    Model: ATLAS10K5_146SCA  Rev: JNZM
[4294670.279000]   Type:   Direct-Access                      ANSI SCSI revision: 03
[4294670.279000]  target0:0:1: Beginning Domain Validation
[4294670.292000]  target0:0:1: Ending Domain Validation
[4294670.293000]  target0:0:1: FAST-160 WIDE SCSI 320.0 MB/s DT IU RTI (6.25 ns, offset 127)
[4294671.304000]   Vendor: PE/PV     Model: 1x2 SCSI BP       Rev: 1.0
[4294671.306000]   Type:   Processor                          ANSI SCSI revision: 02
[4294671.306000]  target0:0:6: Beginning Domain Validation
[4294671.325000]  target0:0:6: Ending Domain Validation
[4294671.325000]  target0:0:6: asynchronous
[4294673.350000] SCSI device sda: 286749480 512-byte hdwr sectors (146816 MB)
[4294673.351000] sda: Write Protect is off
[4294673.351000] sda: Mode Sense: bf 00 10 08
[4294673.352000] SCSI device sda: drive cache: write through w/ FUA
[4294673.352000] SCSI device sda: 286749480 512-byte hdwr sectors (146816 MB)
[4294673.353000] sda: Write Protect is off
[4294673.354000] sda: Mode Sense: bf 00 10 08
[4294673.354000] SCSI device sda: drive cache: write through w/ FUA
[4294673.355000]  sda: sda1 sda2 < sda5 >
[4294673.375000] sd 0:0:0:0: Attached scsi disk sda
[4294673.375000] SCSI device sdb: 286749480 512-byte hdwr sectors (146816 MB)
[4294673.376000] sdb: Write Protect is off
[4294673.377000] sdb: Mode Sense: bf 00 10 08
[4294673.377000] SCSI device sdb: drive cache: write through w/ FUA
[4294673.378000] SCSI device sdb: 286749480 512-byte hdwr sectors (146816 MB)
[4294673.379000] sdb: Write Protect is off
[4294673.379000] sdb: Mode Sense: bf 00 10 08
[4294673.380000] SCSI device sdb: drive cache: write through w/ FUA
[4294673.380000]  sdb: sdb1 sdb2 < sdb5 >
[4294673.387000] sd 0:0:1:0: Attached scsi disk sdb
[4294673.550000] ICH5: IDE controller at PCI slot 0000:00:1f.1
[4294673.550000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[4294673.550000] ACPI: PCI Interrupt 0000:00:1f.1[A]: no GSI
[4294673.550000] ICH5: chipset revision 2
[4294673.550000] ICH5: not 100% native mode: will probe irqs later
[4294673.550000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
[4294673.550000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:pio, hdd:pio
[4294673.550000] Probing IDE interface ide0...
[4294674.222000] hda: HL-DT-STDVD-ROM GDR8082N, ATAPI CD/DVD-ROM drive
[4294674.529000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294674.530000] Probing IDE interface ide1...
[4294675.059000] hda: ATAPI 24X DVD-ROM drive, 256kB Cache, UDMA(33)
[4294675.059000] Uniform CD-ROM driver Revision: 3.20
[4294675.154000] usbcore: registered new driver usbfs
[4294675.154000] usbcore: registered new driver hub
[4294675.158000] USB Universal Host Controller Interface driver v3.0
[4294675.158000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294675.158000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294675.158000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[4294675.159000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294675.159000] uhci_hcd 0000:00:1d.0: irq 169, io base 0x0000ace0
[4294675.159000] usb usb1: configuration #1 chosen from 1 choice
[4294675.159000] hub 1-0:1.0: USB hub found
[4294675.159000] hub 1-0:1.0: 2 ports detected
[4294675.260000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 185
[4294675.261000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294675.261000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[4294675.261000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294675.261000] uhci_hcd 0000:00:1d.1: irq 185, io base 0x0000acc0
[4294675.261000] usb usb2: configuration #1 chosen from 1 choice
[4294675.261000] hub 2-0:1.0: USB hub found
[4294675.261000] hub 2-0:1.0: 2 ports detected
[4294675.362000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 193
[4294675.362000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294675.362000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[4294675.362000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294675.362000] uhci_hcd 0000:00:1d.2: irq 193, io base 0x0000aca0
[4294675.362000] usb usb3: configuration #1 chosen from 1 choice
[4294675.363000] hub 3-0:1.0: USB hub found
[4294675.363000] hub 3-0:1.0: 2 ports detected
[4294675.465000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 201
[4294675.465000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294675.465000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[4294675.467000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[4294675.467000] ehci_hcd 0000:00:1d.7: debug port 1
[4294675.467000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[4294675.467000] ehci_hcd 0000:00:1d.7: irq 201, io mem 0xfeb00000
[4294675.471000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[4294675.471000] usb usb4: configuration #1 chosen from 1 choice
[4294675.471000] hub 4-0:1.0: USB hub found
[4294675.471000] hub 4-0:1.0: 6 ports detected
[4294675.587000] Probing IDE interface ide1...
[4294675.778000] usb 4-3: new high speed USB device using ehci_hcd and address 2
[4294675.892000] usb 4-3: configuration #1 chosen from 1 choice
[4294675.892000] hub 4-3:1.0: USB hub found
[4294675.892000] hub 4-3:1.0: 2 ports detected
[4294676.120000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294676.120000] md: bitmap version 4.39
[4294676.121000] md: raid1 personality registered for level 1
[4294676.201000] md: md0 stopped.
[4294676.202000] md: bind<sdb1>
[4294676.202000] md: bind<sda1>
[4294676.209000] raid1: raid set md0 active with 2 out of 2 mirrors
[4294676.227000] Attempting manual resume
[4294676.251000] kjournald starting.  Commit interval 5 seconds
[4294676.251000] EXT3-fs: mounted filesystem with ordered data mode.
[4294678.157000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[4294678.157000] sd 0:0:1:0: Attached scsi generic sg1 type 0
[4294678.157000]  0:0:6:0: Attached scsi generic sg2 type 3
[4294678.529000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294678.545000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294678.584000] Floppy drive(s): fd0 is 1.44M
[4294678.604000] FDC 0 is a National Semiconductor PC87306
[4294678.646000] input: PC Speaker as /class/input/input0
[4294678.650000] hw_random hardware driver 1.0.0 loaded
[4294678.819000] Intel(R) PRO/1000 Network Driver - version 7.0.33-k2
[4294678.819000] Copyright (c) 1999-2005 Intel Corporation.
[4294678.819000] ACPI: PCI Interrupt 0000:06:07.0[A] -> GSI 64 (level, low) -> IRQ 209
[4294678.879000] e1000: 0000:06:07.0: e1000_probe: (PCI:66MHz:32-bit) 00:14:22:22:64:28
[4294679.023000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[4294679.023000] ACPI: PCI Interrupt 0000:07:08.0[A] -> GSI 65 (level, low) -> IRQ 217
[4294679.083000] e1000: 0000:07:08.0: e1000_probe: (PCI:66MHz:32-bit) 00:14:22:22:64:29
[4294679.224000] e1000: eth1: e1000_probe: Intel(R) PRO/1000 Network Connection
[4294679.496000] lp: driver loaded but no devices found
[4294679.583000] Adding 5831552k swap on /dev/sda5.  Priority:-1 extents:1 across:5831552k
[4294679.593000] Adding 5831552k swap on /dev/sdb5.  Priority:-2 extents:1 across:5831552k
[4294679.683000] EXT3 FS on md0, internal journal
[4294679.927000] device-mapper: 4.6.0-ioctl (2006-02-17) initialised: [email]dm-devel@redhat.com[/email]
[4294680.513000] device-mapper: dm-linear: Device lookup failed
[4294680.513000] device-mapper: error adding target to table
[4294680.513000] device-mapper: dm-linear: Device lookup failed
[4294680.513000] device-mapper: error adding target to table
[4294680.513000] device-mapper: dm-linear: Device lookup failed
[4294680.513000] device-mapper: error adding target to table
[4294680.514000] device-mapper: dm-linear: Device lookup failed
[4294680.514000] device-mapper: error adding target to table
[4294680.514000] device-mapper: dm-linear: Device lookup failed
[4294680.514000] device-mapper: error adding target to table
[4294680.515000] device-mapper: dm-linear: Device lookup failed
[4294680.515000] device-mapper: error adding target to table
[4294680.515000] device-mapper: dm-linear: Device lookup failed
[4294680.515000] device-mapper: error adding target to table
[4294680.515000] device-mapper: dm-linear: Device lookup failed
[4294680.515000] device-mapper: error adding target to table
[4294680.516000] device-mapper: dm-linear: Device lookup failed
[4294680.516000] device-mapper: error adding target to table
[4294680.516000] device-mapper: dm-linear: Device lookup failed
[4294680.516000] device-mapper: error adding target to table
[4294680.516000] device-mapper: dm-linear: Device lookup failed
[4294680.516000] device-mapper: error adding target to table
[4294680.517000] device-mapper: dm-linear: Device lookup failed
[4294680.517000] device-mapper: error adding target to table
[4294680.578000] e1000: eth0: e1000_watchdog_task: NIC Link is Up 100 Mbps Full Duplex
[4294680.664000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[4294681.474000] NET: Registered protocol family 10
[4294681.474000] lo: Disabled Privacy Extensions
[4294681.475000] IPv6 over IPv4 tunneling driver
[4294692.052000] eth0: no IPv6 routers present
[4369761.504000] usb 3-2: new low speed USB device using uhci_hcd and address 2
[4369761.667000] usb 3-2: configuration #1 chosen from 1 choice
[4369761.717000] usbcore: registered new driver hiddev
[4369761.742000] input: Dell Dell USB Mouse as /class/input/input1
[4369761.742000] input: USB HID v1.10 Mouse [Dell Dell USB Mouse] on usb-0000:00:1d.2-2
[4369761.742000] usbcore: registered new driver usbhid
[4369761.742000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[4369761.770000] ts: Compaq touchscreen protocol output
[4369771.504000] usb 3-1: new low speed USB device using uhci_hcd and address 3
[4369771.667000] usb 3-1: configuration #1 chosen from 1 choice
[4369771.689000] input: Dell Dell USB Keyboard as /class/input/input2
[4369771.689000] input: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.2-1
[4370406.037000] usb 3-1: USB disconnect, address 3
[4370406.141000] usb 3-2: USB disconnect, address 2
```

---

### Post by tapferesschneiderlein on 2007-08-16
Hello.

I just upgraded from Ubuntu Edgy (which was a fresh install with upstart) to Feisty (default kernel 2.6.20).

Now the system only boots to runlevel "unknown". I always have to login and run `telinit 3` (sic!) to start all the daemons listed in /etc/rc{2,3}.d/.

`telinit 2` results in `runlevel` => "unknown", too.

There's no /etc/inittab file and no "single" or similar argument in /proc/cmdline.

What could be wrong here? Did you solve it?

---

