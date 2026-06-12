---
title: "random freeze in gutsy"
date: 2007-10-19
forum: General Help
---

### Post by smmalis on 2007-10-19
Every so often my computer will completely freeze.  There is nothing I can do but reboot with the button on the case.  The computer becomes almost completely unresponsive, but I can still move the mouse and switch to text-only modes.  Ctrl-Alt-F1 (and F2-6) work, but I can't log in once I get to them.  I can also hit Ctrl-Alt-Backspace to restart the X server, but it will shutdown and not start up again.  Please help!

Lspci:
```
00:00.0 Host bridge: VIA Technologies, Inc. VT3351 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. VT3351 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. VT3351 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. VT3351 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. VT3351 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. VT3351 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. Unknown device 6238
00:00.7 Host bridge: VIA Technologies, Inc. VT3351 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. [K8T890 North / VT8237 South] PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.1 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.2 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.3 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2)
07:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
80:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)

```

dmesg:
```
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cffb0000 (usable)
[    0.000000]  BIOS-e820: 00000000cffb0000 - 00000000cffbe000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cffbe000 - 00000000cffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cffe0000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fecc0000 - 00000000fecc1000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] Warning only 4GB will be used.
[    0.000000] Use a PAE enabled kernel.
[    0.000000] 3200MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 1048576) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->  1048576
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->  1048576
[    0.000000] On node 0 totalpages: 1048576
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 6400 pages used for memmap
[    0.000000]   HighMem zone: 812800 pages, LIFO batch:31
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00FA960 checksum 0
[    0.000000] ACPI: RSDP 000FA960, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT CFFB0000, 0038 (r1 A_M_I_ OEMRSDT   9000706 MSFT       97)
[    0.000000] ACPI: FACP CFFB0200, 0084 (r2 A_M_I_ OEMFACP   9000706 MSFT       97)
[    0.000000] ACPI: DSDT CFFB05C0, 4E3F (r1  A0498 A0498000        0 INTL 20060113)
[    0.000000] ACPI: FACS CFFBE000, 0040
[    0.000000] ACPI: APIC CFFB0390, 0068 (r1 A_M_I_ OEMAPIC   9000706 MSFT       97)
[    0.000000] ACPI: MCFG CFFB0400, 003C (r1 A_M_I_ OEMMCFG   9000706 MSFT       97)
[    0.000000] ACPI: OEMB CFFBE040, 0060 (r1 A_M_I_ AMI_OEM   9000706 MSFT       97)
[    0.000000] ACPI: HPET CFFB5400, 0038 (r1 A_M_I_ OEMHPET   9000706 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:3 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:3 APIC version 16
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x03] address[0xfecc0000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 3, version 3, address 0xfecc0000, GSI 24-47
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 2 I/O APICs
[    0.000000] ACPI: HPET id: 0x11068201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at d4000000 (gap: d0000000:2ec00000)
[    0.000000] Built 1 zonelists.  Total pages: 1040384
[    0.000000] Kernel command line: root=UUID=de2fdefe-1d93-4428-b34e-00f28d381130 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] mapped IOAPIC to ffffb000 (fecc0000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2799.959 MHz processor.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Memory: 3361500k/4194304k available (2015k kernel code, 44868k reserved, 916k data, 364k init, 2490048k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.000000]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[    0.000000]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[    0.000000]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    0.000000] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[    0.000000] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.000000] hpet0: 3 32-bit timers, 14318180 Hz
[    0.080000] Calibrating delay using timer specific routine.. 5602.19 BogoMIPS (lpj=11204399)
[    0.080000] Security Framework v1.0.0 initialized
[    0.080000] SELinux:  Disabled at boot.
[    0.080000] Mount-cache hash table entries: 512
[    0.080000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
[    0.080000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.080000] CPU: L2 Cache: 1024K (64 bytes/line)
[    0.080000] CPU 0(2) -> Core 0
[    0.080000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f
[    0.080000] Compat vDSO mapped to ffffe000.
[    0.080000] Checking 'hlt' instruction... OK.
[    0.096000] SMP alternatives: switching to UP code
[    0.096000] Early unpacking initramfs... done
[    0.308000] ACPI: Core revision 20070126
[    0.308000] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    0.308000] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 5600+ stepping 03
[    0.308000] SMP alternatives: switching to SMP code
[    0.308000] Booting processor 1/1 eip 3000
[    0.320000] Initializing CPU#1
[    0.400000] Calibrating delay using timer specific routine.. 5599.31 BogoMIPS (lpj=11198632)
[    0.400000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
[    0.400000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.400000] CPU: L2 Cache: 1024K (64 bytes/line)
[    0.400000] CPU 1(2) -> Core 1
[    0.400000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f
[    0.400000] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 5600+ stepping 03
[    0.400000] Total of 2 processors activated (11201.51 BogoMIPS).
[    0.400000] ENABLING IO-APIC IRQs
[    0.400000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[    0.440000] Brought up 2 CPUs
[    0.484000] migration_cost=4000
[    0.484000] Booting paravirtualized kernel on bare hardware
[    0.484000] Time: 15:01:40  Date: 09/19/107
[    0.484000] NET: Registered protocol family 16
[    0.484000] EISA bus registered
[    0.484000] ACPI: bus type pci registered
[    0.484000] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=128
[    0.484000] PCI: Using configuration type 1
[    0.484000] Setting up standard PCI resources
[    0.488000] ACPI: EC: Look up EC in DSDT
[    0.492000] ACPI: Interpreter enabled
[    0.492000] ACPI: (supports S0 S1 S3 S4 S5)
[    0.492000] ACPI: Using IOAPIC for interrupt routing
[    0.492000] Error attaching device data
[    0.492000] Error attaching device data
[    0.500000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.500000] PCI: Probing PCI hardware (bus 00)
[    0.500000] PCI: Transparent bridge - 0000:00:13.1
[    0.500000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.500000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.500000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBPG._PRT]
[    0.500000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBP0._PRT]
[    0.500000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBP1._PRT]
[    0.500000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBP2._PRT]
[    0.500000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBP3._PRT]
[    0.500000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.500000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PA._PRT]
[    0.512000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.512000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.512000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.512000] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.512000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.512000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.512000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.512000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.512000] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.512000] pnp: PnP ACPI init
[    0.512000] ACPI: bus type pnp registered
[    0.516000] pnp: PnP ACPI: found 17 devices
[    0.516000] ACPI: ACPI bus type pnp unregistered
[    0.516000] PnPBIOS: Disabled by ACPI PNP
[    0.516000] PCI: Using ACPI for IRQ routing
[    0.516000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.740000] NET: Registered protocol family 8
[    0.740000] NET: Registered protocol family 20
[    0.740000] pnp: 00:06: ioport range 0xc00-0xc0f has been reserved
[    0.740000] pnp: 00:06: ioport range 0xd00-0xd0f has been reserved
[    0.740000] pnp: 00:06: ioport range 0xa20-0xa2f has been reserved
[    0.740000] pnp: 00:06: ioport range 0xa30-0xa3f has been reserved
[    0.740000] pnp: 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.740000] pnp: 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.740000] pnp: 00:0f: iomem range 0xe0000000-0xefffffff has been reserved
[    0.740000] pnp: 00:10: iomem range 0x0-0x9ffff could not be reserved
[    0.740000] pnp: 00:10: iomem range 0xc0000-0xcffff could not be reserved
[    0.740000] pnp: 00:10: iomem range 0xe0000-0xfffff could not be reserved
[    0.740000] pnp: 00:10: iomem range 0x100000-0xcfffffff could not be reserved
[    0.744000] Time: hpet clocksource has been installed.
[    0.744000] Switched to high resolution mode on CPU 0
[    0.744000] Switched to high resolution mode on CPU 1
[    0.768000] PCI: Bridge: 0000:00:01.0
[    0.768000]   IO window: disabled.
[    0.768000]   MEM window: disabled.
[    0.768000]   PREFETCH window: disabled.
[    0.768000] PCI: Bridge: 0000:00:02.0
[    0.768000]   IO window: d000-dfff
[    0.768000]   MEM window: f8000000-fbdfffff
[    0.768000]   PREFETCH window: d0000000-dfffffff
[    0.768000] PCI: Bridge: 0000:00:03.0
[    0.768000]   IO window: disabled.
[    0.768000]   MEM window: disabled.
[    0.768000]   PREFETCH window: f6f00000-f6ffffff
[    0.768000] PCI: Bridge: 0000:00:03.1
[    0.768000]   IO window: disabled.
[    0.768000]   MEM window: disabled.
[    0.768000]   PREFETCH window: f6e00000-f6efffff
[    0.768000] PCI: Bridge: 0000:00:03.2
[    0.768000]   IO window: disabled.
[    0.768000]   MEM window: disabled.
[    0.768000]   PREFETCH window: f6d00000-f6dfffff
[    0.768000] PCI: Bridge: 0000:00:03.3
[    0.768000]   IO window: disabled.
[    0.768000]   MEM window: disabled.
[    0.768000]   PREFETCH window: f6c00000-f6cfffff
[    0.768000] PCI: Bridge: 0000:00:13.0
[    0.768000]   IO window: disabled.
[    0.768000]   MEM window: fbf00000-fbffffff
[    0.768000]   PREFETCH window: disabled.
[    0.768000] PCI: Bridge: 0000:00:13.1
[    0.768000]   IO window: e000-efff
[    0.768000]   MEM window: fbe00000-fbefffff
[    0.768000]   PREFETCH window: f0000000-f00fffff
[    0.768000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.768000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 27 (level, low) -> IRQ 16
[    0.768000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    0.768000] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 31 (level, low) -> IRQ 17
[    0.768000] PCI: Setting latency timer of device 0000:00:03.0 to 64
[    0.768000] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 35 (level, low) -> IRQ 18
[    0.768000] PCI: Setting latency timer of device 0000:00:03.1 to 64
[    0.768000] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 39 (level, low) -> IRQ 19
[    0.768000] PCI: Setting latency timer of device 0000:00:03.2 to 64
[    0.768000] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 43 (level, low) -> IRQ 20
[    0.768000] PCI: Setting latency timer of device 0000:00:03.3 to 64
[    0.768000] PCI: Setting latency timer of device 0000:00:13.0 to 64
[    0.768000] PCI: Setting latency timer of device 0000:00:13.1 to 64
[    0.768000] NET: Registered protocol family 2
[    0.808000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.808000] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[    0.808000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.808000] TCP: Hash tables configured (established 131072 bind 65536)
[    0.808000] TCP reno registered
[    0.824000] checking if image is initramfs... it is
[    1.240000] Freeing initrd memory: 7338k freed
[    1.244000] audit: initializing netlink socket (disabled)
[    1.244000] audit(1192806099.744:1): initialized
[    1.244000] highmem bounce pool size: 64 pages
[    1.244000] VFS: Disk quotas dquot_6.5.1
[    1.244000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.244000] io scheduler noop registered
[    1.244000] io scheduler anticipatory registered
[    1.244000] io scheduler deadline registered
[    1.244000] io scheduler cfq registered (default)
[    1.244000] PCI: MSI quirk detected. MSI deactivated.
[    1.244000] PCI: VIA PCI bridge detected. Disabling DAC.
[    1.244000] Boot video device is 0000:02:00.0
[    1.244000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    1.244000] assign_interrupt_mode Found MSI capability
[    1.244000] Allocate Port Service[0000:00:02.0:pcie00]
[    1.244000] Allocate Port Service[0000:00:02.0:pcie02]
[    1.244000] PCI: Setting latency timer of device 0000:00:03.0 to 64
[    1.244000] assign_interrupt_mode Found MSI capability
[    1.244000] Allocate Port Service[0000:00:03.0:pcie00]
[    1.244000] Allocate Port Service[0000:00:03.0:pcie02]
[    1.244000] PCI: Setting latency timer of device 0000:00:03.1 to 64
[    1.244000] assign_interrupt_mode Found MSI capability
[    1.244000] Allocate Port Service[0000:00:03.1:pcie00]
[    1.244000] Allocate Port Service[0000:00:03.1:pcie02]
[    1.244000] PCI: Setting latency timer of device 0000:00:03.2 to 64
[    1.244000] assign_interrupt_mode Found MSI capability
[    1.244000] Allocate Port Service[0000:00:03.2:pcie00]
[    1.244000] Allocate Port Service[0000:00:03.2:pcie02]
[    1.244000] PCI: Setting latency timer of device 0000:00:03.3 to 64
[    1.244000] assign_interrupt_mode Found MSI capability
[    1.244000] Allocate Port Service[0000:00:03.3:pcie00]
[    1.244000] Allocate Port Service[0000:00:03.3:pcie02]
[    1.244000] isapnp: Scanning for PnP cards...
[    1.596000] isapnp: No Plug & Play device found
[    1.612000] Real Time Clock Driver v1.12ac
[    1.612000] hpet_resources: 0xfed00000 is busy
[    1.612000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.612000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.612000] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.612000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.612000] input: Macintosh mouse button emulation as /class/input/input0
[    1.612000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.612000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.612000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.612000] mice: PS/2 mouse device common for all mice
[    1.612000] EISA: Probing bus 0 at eisa.0
[    1.612000] EISA: Detected 0 cards.
[    1.612000] TCP cubic registered
[    1.612000] NET: Registered protocol family 1
[    1.612000] Using IPI No-Shortcut mode
[    1.612000]   Magic number: 11:5:33
[    1.612000] Freeing unused kernel memory: 364k freed
[    1.640000] input: AT Translated Set 2 keyboard as /class/input/input1
[    2.820000] AppArmor: AppArmor initialized<5>audit(1192806101.744:2):  type=1505 info="AppArmor initialized" pid=1264
[    2.836000] fuse init (API version 7.8)
[    2.840000] Failure registering capabilities with primary security module.
[    2.860000] ACPI: Processor [P001] (supports 16 throttling states)
[    3.288000] usbcore: registered new interface driver usbfs
[    3.288000] usbcore: registered new interface driver hub
[    3.288000] usbcore: registered new device driver usb
[    3.288000] USB Universal Host Controller Interface driver v3.0
[    3.288000] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 20 (level, low) -> IRQ 21
[    3.288000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    3.288000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[    3.288000] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000b480
[    3.288000] usb usb1: configuration #1 chosen from 1 choice
[    3.288000] hub 1-0:1.0: USB hub found
[    3.288000] hub 1-0:1.0: 2 ports detected
[    3.304000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    3.304000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    3.308000] SCSI subsystem initialized
[    3.324000] libata version 2.21 loaded.
[    3.352000] Floppy drive(s): fd0 is 1.44M
[    3.368000] FDC 0 is a post-1991 82077
[    3.392000] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 22 (level, low) -> IRQ 22
[    3.392000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    3.392000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[    3.392000] uhci_hcd 0000:00:10.1: irq 22, io base 0x0000b800
[    3.392000] usb usb2: configuration #1 chosen from 1 choice
[    3.392000] hub 2-0:1.0: USB hub found
[    3.392000] hub 2-0:1.0: 2 ports detected
[    3.496000] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 23
[    3.496000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    3.496000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[    3.496000] uhci_hcd 0000:00:10.2: irq 23, io base 0x0000b880
[    3.496000] usb usb3: configuration #1 chosen from 1 choice
[    3.496000] hub 3-0:1.0: USB hub found
[    3.496000] hub 3-0:1.0: 2 ports detected
[    3.600000] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 23 (level, low) -> IRQ 24
[    3.600000] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    3.600000] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[    3.600000] uhci_hcd 0000:00:10.3: irq 24, io base 0x0000bc00
[    3.600000] usb usb4: configuration #1 chosen from 1 choice
[    3.600000] hub 4-0:1.0: USB hub found
[    3.600000] hub 4-0:1.0: 2 ports detected
[    3.704000] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 23
[    3.704000] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    3.704000] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[    3.704000] ehci_hcd 0000:00:10.4: irq 23, io mem 0xf7fffc00
[    3.704000] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.704000] usb usb5: configuration #1 chosen from 1 choice
[    3.704000] hub 5-0:1.0: USB hub found
[    3.704000] hub 5-0:1.0: 8 ports detected
[    3.808000] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[    3.808000] VP_IDE: chipset revision 7
[    3.808000] VP_IDE: not 100% native mode: will probe irqs later
[    3.808000] VP_IDE: VIA vt8237a (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[    3.808000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
[    3.808000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:pio, hdd:pio
[    3.808000] Probing IDE interface ide0...
[    4.672000] hda: TSSTcorpCD/DVDW SH-S182D, ATAPI CD/DVD-ROM drive
[    4.996000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    5.172000] usb 2-1: configuration #1 chosen from 1 choice
[    5.180000] usbcore: registered new interface driver hiddev
[    5.196000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
[    5.196000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:10.1-1
[    5.196000] usbcore: registered new interface driver usbhid
[    5.196000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[    5.344000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    5.344000] Probing IDE interface ide1...
[    5.916000] r8169 Gigabit Ethernet driver 2.2LK loaded
[    5.916000] ACPI: PCI Interrupt 0000:07:08.0[A] -> GSI 18 (level, low) -> IRQ 25
[    5.916000] eth0: RTL8110s at 0xf885cc00, 00:1b:2f:be:f6:64, XID 04000000 IRQ 25
[    5.920000] sata_via 0000:00:0f.0: version 2.2
[    5.920000] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 21 (level, low) -> IRQ 23
[    5.920000] sata_via 0000:00:0f.0: routed to hard irq line 10
[    5.920000] scsi0 : sata_via
[    5.920000] scsi1 : sata_via
[    5.920000] ata1: SATA max UDMA/133 cmd 0x0001cc00 ctl 0x0001c882 bmdma 0x0001c400 irq 23
[    5.920000] ata2: SATA max UDMA/133 cmd 0x0001c800 ctl 0x0001c482 bmdma 0x0001c408 irq 23
[    5.928000] hda: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[    5.928000] Uniform CD-ROM driver Revision: 3.20
[    6.124000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.328000] ata1.00: ATA-7: WDC WD1600YS-01SHB1, 20.06C06, max UDMA/133
[    6.328000] ata1.00: 321672960 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    6.344000] ata1.00: configured for UDMA/133
[    6.548000] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    6.556000] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600YS-01S 20.0 PQ: 0 ANSI: 5
[    6.560000] sd 0:0:0:0: [sda] 321672960 512-byte hardware sectors (164697 MB)
[    6.560000] sd 0:0:0:0: [sda] Write Protect is off
[    6.560000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.560000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.560000] sd 0:0:0:0: [sda] 321672960 512-byte hardware sectors (164697 MB)
[    6.560000] sd 0:0:0:0: [sda] Write Protect is off
[    6.560000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.560000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.560000]  sda: sda1 sda2 sda3
[    6.592000] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.596000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    6.812000] Attempting manual resume
[    6.812000] swsusp: Resume From Partition 8:3
[    6.812000] PM: Checking swsusp image.
[    6.812000] PM: Resume from disk failed.
[    6.816000] EXT3-fs: INFO: recovery required on readonly filesystem.
[    6.816000] EXT3-fs: write access will be enabled during recovery.
[    7.588000] kjournald starting.  Commit interval 5 seconds
[    7.588000] EXT3-fs: recovery complete.
[    7.588000] EXT3-fs: mounted filesystem with ordered data mode.
[   11.376000] input: PC Speaker as /class/input/input3
[   11.648000] parport_pc 00:05: reported by Plug and Play ACPI
[   11.648000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   11.712000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   11.716000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.048000] Linux agpgart interface v0.102 (c) Dave Jones
[   12.080000] nvidia: module license 'NVIDIA' taints kernel.
[   12.332000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 24 (level, low) -> IRQ 26
[   12.332000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   12.332000] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   12.476000] ACPI: PCI Interrupt 0000:80:01.0[A] -> GSI 17 (level, low) -> IRQ 27
[   12.476000] PCI: Setting latency timer of device 0000:80:01.0 to 64
[   12.852000] lp0: using parport0 (interrupt-driven).
[   12.900000] Adding 787176k swap on /dev/sda3.  Priority:-1 extents:1 across:787176k
[   13.132000] EXT3 FS on sda2, internal journal
[   13.872000] No dock devices found.
[   13.996000] input: Power Button (FF) as /class/input/input4
[   13.996000] ACPI: Power Button (FF) [PWRF]
[   13.996000] input: Sleep Button (CM) as /class/input/input5
[   13.996000] ACPI: Sleep Button (CM) [SLPB]
[   13.996000] input: Power Button (CM) as /class/input/input6
[   13.996000] ACPI: Power Button (CM) [PWRB]
[   14.188000] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 5600+ processors (version 2.00.00)
[   14.188000] powernow-k8: MP systems not supported by PSB BIOS structure
[   14.188000] powernow-k8: MP systems not supported by PSB BIOS structure
[   14.812000] ppdev: user-space parallel port driver
[   14.944000] audit(1192820517.656:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5058 profile="/usr/sbin/cupsd"
[   14.964000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   14.964000] apm: disabled - APM is not SMP safe.
[   15.080000] r8169: eth0: link up
[   15.124000] Failure registering capabilities with primary security module.
[   19.692000] NET: Registered protocol family 17
[   21.184000] hda-intel: Invalid position buffer, using LPIB read method instead.
[   22.316000] NET: Registered protocol family 10
[   22.316000] lo: Disabled Privacy Extensions
[   32.540000] eth0: no IPv6 routers present
[  685.556000] r8169: eth0: link up
[  696.340000] eth0: no IPv6 routers present

```

---

### Post by smah77 on 2007-10-27
Same exact problem here, running Xubuntu gutsy... But I can log in in safe mode - it seems like it might be an issue with Xorg or GDM.

---

### Post by smah77 on 2007-10-31
Turns out my issue is compiz.  After uninstalling it, everything works fine, though login is really slow (getting there is fast though!).  All in all, gutsy has been really disappointing for me.

---

