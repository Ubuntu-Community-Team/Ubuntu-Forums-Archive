---
title: "Kernel Boot Delay - Feisty"
date: 2007-07-20
forum: General Help
---

### Post by bench on 2007-07-20
Hi

I've had this issue since Dapper on my Acer Travelmate 2500 ...

[B][COLOR="Red"][   41.278169] checking if image is initramfs... it is
[  105.948785] Freeing initrd memory: 6770k freed[/COLOR][/B]

Can anyone explain the massive delay - the full dmesg output is below (highlighted in red, sorry, quite far down):

[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000002ee70000 end: 000000002ef70000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000002ef70000 size: 0000000000007000 end: 000000002ef77000 type: 3
[    0.000000] copy_e820_map() start: 000000002ef77000 size: 0000000000009000 end: 000000002ef80000 type: 4
[    0.000000] copy_e820_map() start: 000000002ef80000 size: 0000000000080000 end: 000000002f000000 type: 2
[    0.000000] copy_e820_map() start: 000000003ef80000 size: 0000000000080000 end: 000000003f000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fff80000 size: 0000000000080000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002ef70000 (usable)
[    0.000000]  BIOS-e820: 000000002ef70000 - 000000002ef77000 (ACPI data)
[    0.000000]  BIOS-e820: 000000002ef77000 - 000000002ef80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000002ef80000 - 000000002f000000 (reserved)
[    0.000000]  BIOS-e820: 000000003ef80000 - 000000003f000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 751MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f60e0
[    0.000000] Entering add_active_range(0, 0, 192368) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   192368
[    0.000000]   HighMem    192368 ->   192368
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   192368
[    0.000000] On node 0 totalpages: 192368
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1470 pages used for memmap
[    0.000000]   Normal zone: 186802 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f61e0
[    0.000000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x2ef72564
[    0.000000] ACPI: FADT (v001 ATI    Wistron  0x06040000 ATI  0x000f4240) @ 0x2ef76f32
[    0.000000] ACPI: MADT (v001 PTLTD    APIC   0x06040000  LTP 0x00000000) @ 0x2ef76fa6
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20030224) @ 0x2ef7279a
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20030224) @ 0x2ef72598
[    0.000000] ACPI: DSDT (v001    ATI    SB200 0x06040000 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3f000000:bfc00000)
[    0.000000] Detected 2800.183 MHz processor.
[   27.475794] Built 1 zonelists.  Total pages: 190866
[   27.475801] Kernel command line: root=UUID=e476a5f3-baa4-4201-8b93-8c418e814871 ro debug=on
[   27.475965] mapped APIC to ffffd000 (fee00000)
[   27.475968] mapped IOAPIC to ffffc000 (fec00000)
[   27.475972] Enabling fast FPU save and restore... done.
[   27.475976] Enabling unmasked SIMD FPU exception support... done.
[   27.475990] Initializing CPU#0
[   27.476097] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   27.477209] Console: colour VGA+ 80x25
[   27.480225] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   27.481250] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   27.502476] Memory: 751544k/769472k available (1992k kernel code, 17284k reserved, 900k data, 328k init, 0k highmem)
[   27.502540] virtual kernel memory layout:
[   27.502541]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   27.502542]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   27.502543]     vmalloc : 0xef800000 - 0xff7fe000   ( 255 MB)
[   27.502544]     lowmem  : 0xc0000000 - 0xeef70000   ( 751 MB)
[   27.502545]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   27.502546]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   27.502547]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   27.502832] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   27.583900] Calibrating delay using timer specific routine.. 5603.67 BogoMIPS (lpj=11207353)
[   27.584897] Security Framework v1.0.0 initialized
[   27.584940] SELinux:  Disabled at boot.
[   27.585359] Mount-cache hash table entries: 512
[   27.586090] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[   27.586102] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   27.586164] CPU: L2 cache: 512K
[   27.586199] CPU: Hyper-Threading is disabled
[   27.586235] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003080 00004400 00000000 00000000
[   27.586247] Compat vDSO mapped to ffffe000.
[   27.586285] Remapping vsyscall page to ffffe000
[   27.586336] Checking 'hlt' instruction... OK.
[   27.600010] SMP alternatives: switching to UP code
[   27.600282] Freeing SMP alternatives: 11k freed
[   27.601270] Early unpacking initramfs... done
[   40.348883] ACPI: Core revision 20060707
[   40.349724] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   40.361548] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 09
[   40.362284] Total of 1 processors activated (5603.67 BogoMIPS).
[   40.362918] ENABLING IO-APIC IRQs
[   40.364278] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   40.404287] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   40.404594] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[   40.404991] ...trying to set up timer as Virtual Wire IRQ... works.
[   40.552635] Brought up 1 CPUs
[   40.562425] Booting paravirtualized kernel on bare hardware
[   40.563880] Time:  3:59:45  Date: 06/21/107
[   40.565049] NET: Registered protocol family 16
[   40.567075] EISA bus registered
[   40.567352] ACPI: bus type pci registered
[   40.573621] PCI: PCI BIOS revision 2.10 entry at 0xfd778, last bus=4
[   40.573949] PCI: Using configuration type 1
[   40.574203] Setting up standard PCI resources
[   40.695317] ACPI: Interpreter enabled
[   40.695624] ACPI: Using IOAPIC for interrupt routing
[   40.722808] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   40.723104] PCI: Probing PCI hardware (bus 00)
[   40.773782] Boot video device is 0000:01:05.0
[   40.776606] PCI: Transparent bridge - 0000:00:14.4
[   40.778364] PCI: Bus #04 (-#07) is hidden behind transparent bridge #02 (-#04) (try 'pci=assign-busses')
[   40.778797] Please report the result to linux-kernel to fix this permanently
[   40.779445] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   40.900786] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 10 11) *0, disabled.
[   40.912889] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 10 11) *0, disabled.
[   40.925023] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 7 10 11) *0, disabled.
[   40.937073] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 7 10 11) *0, disabled.
[   40.993004] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   41.039160] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   41.055565] Linux Plug and Play Support v0.97 (c) Adam Belay
[   41.056085] pnp: PnP ACPI init
[   41.161388] pnp: PnP ACPI: found 9 devices
[   41.161647] PnPBIOS: Disabled by ACPI PNP
[   41.163136] PCI: Using ACPI for IRQ routing
[   41.163410] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   41.184196] NET: Registered protocol family 8
[   41.184470] NET: Registered protocol family 20
[   41.194904] pnp: 00:07: ioport range 0x1080-0x1080 has been reserved
[   41.195277] pnp: 00:07: ioport range 0x220-0x22f has been reserved
[   41.195641] pnp: 00:07: ioport range 0x40b-0x40b has been reserved
[   41.196003] pnp: 00:07: ioport range 0x4d0-0x4d1 has been reserved
[   41.203555] PCI: Bridge: 0000:00:01.0
[   41.203829]   IO window: 9000-9fff
[   41.204122]   MEM window: e0100000-e01fffff
[   41.204428]   PREFETCH window: e4000000-e7ffffff
[   41.205182] PCI: Bus 3, cardbus bridge: 0000:02:04.0
[   41.205481]   IO window: 0000a400-0000a4ff
[   41.205773]   IO window: 0000a800-0000a8ff
[   41.206075]   PREFETCH window: 40000000-43ffffff
[   41.206392]   MEM window: 4c000000-4fffffff
[   41.206828] PCI: Bus 4, cardbus bridge: 0000:02:04.1
[   41.207119]   IO window: 0000ac00-0000acff
[   41.207404]   IO window: 00001400-000014ff
[   41.207704]   PREFETCH window: 44000000-47ffffff
[   41.208021]   MEM window: 50000000-53ffffff
[   41.208290] PCI: Bridge: 0000:00:14.4
[   41.208561]   IO window: a000-afff
[   41.208851]   MEM window: e0200000-e02fffff
[   41.209157]   PREFETCH window: 40000000-49ffffff
[   41.209666] PCI: Enabling device 0000:02:04.0 (0000 -> 0003)
[   41.210010] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 16 (level, low) -> IRQ 16
[   41.210678] PCI: Enabling device 0000:02:04.1 (0000 -> 0003)
[   41.210998] ACPI: PCI Interrupt 0000:02:04.1[A] -> GSI 16 (level, low) -> IRQ 16
[   41.212410] NET: Registered protocol family 2
[   41.252399] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   41.256038] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   41.257881] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   41.259419] TCP: Hash tables configured (established 131072 bind 65536)
[   41.259747] TCP reno registered
[B][COLOR="Red"][   41.278169] checking if image is initramfs... it is
[  105.948785] Freeing initrd memory: 6770k freed[/COLOR][/B]
[  105.958510] audit: initializing netlink socket (disabled)
[  105.959273] audit(1184990450.676:1): initialized
[  105.967119] VFS: Disk quotas dquot_6.5.1
[  105.968615] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[  105.972518] io scheduler noop registered
[  105.973073] io scheduler anticipatory registered
[  105.973670] io scheduler deadline registered
[  105.975746] io scheduler cfq registered (default)
[  106.595221] isapnp: Scanning for PnP cards...
[  106.955852] isapnp: No Plug & Play device found
[  107.869758] Real Time Clock Driver v1.12ac
[  107.871804] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[  107.888997] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[  107.889904] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[  107.893227] mice: PS/2 mouse device common for all mice
[  107.920868] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
etc etc
etc

Searched everywhere and can find no info on this, any insight would be much appreciated.

Regards.

---

