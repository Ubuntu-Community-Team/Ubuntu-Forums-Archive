---
title: "[SOLVED] USB flash doesn't mount after kernel update"
date: 2008-02-08
forum: General Help
---

### Post by Tosa on 2008-02-08
I've finally updated to new (64) kernel. It seems that everything is OK now, except that when I insert USB flash it is not mounted. I can mount it manually, but it would be a pain to do it all the time.
I've browsed older threads, but didn't find anything on this problem.

Help would be appreciated.

---

### Post by dcstar on 2008-02-09
> **Tosa said:**
> I've finally updated to new (64) kernel. It seems that everything is OK now, except that when I insert USB flash it is not mounted. I can mount it manually, but it would be a pain to do it all the time.
I've browsed older threads, but didn't find anything on this problem.


As most of the threads on USB mounting say, open a terminal and post the output of **dmesg** when you plug in the device.

And clarify exactly what you mean by "updated", did you just use the Update Manager or do something else?

---

### Post by Tosa on 2008-02-09
I used Adept Manager.  If you asked weather I'd compiled kernel, no I didn't (wouldn't dare).

This is dmesg output after I manually mounted flash stick:

```
[    0.000000] Linux version 2.6.22-14-generic (buildd@king) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Thu Jan 31 23:33:13 UTC 2008 (Ubuntu 2.6.22-14.51-generic)
[    0.000000] Command line: root=UUID=a9529e2e-fe08-43b5-8ce9-2d6a8b0b424a ro quiet splash nosplash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
[    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 158) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524000) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F6AB0 checksum 0
[    0.000000] ACPI: RSDP 000F6AB0, 0014 (r0 GBT   )
[    0.000000] ACPI: RSDT 7FEE3040, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: FACP 7FEE30C0, 0074 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: DSDT 7FEE3180, 49E4 (r1 GBT    GBTUACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 7FEE0000, 0040
[    0.000000] ACPI: HPET 7FEE7CC0, 0038 (r1 GBT    GBTUACPI 42302E31 GBTU       98)
[    0.000000] ACPI: MCFG 7FEE7D40, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: APIC 7FEE7BC0, 0084 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: SSDT 7FEE7DC0, 015C (r1  PmRef  Cpu0Ist     3000 INTL 20040311)
[    0.000000] ACPI: SSDT 7FEE8250, 0275 (r1  PmRef    CpuPm     3000 INTL 20040311)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007fee0000
[    0.000000] Entering add_active_range(0, 0, 158) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524000) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000007fee0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      158
[    0.000000]     0:      256 ->   524000
[    0.000000] On node 0 totalpages: 523902
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1126 pages reserved
[    0.000000]   DMA zone: 2816 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7108 pages used for memmap
[    0.000000]   DMA32 zone: 512796 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:70100000)
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 515612
[    0.000000] Kernel command line: root=UUID=a9529e2e-fe08-43b5-8ce9-2d6a8b0b424a ro quiet splash nosplash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   28.044389] time.c: Detected 1804.235 MHz processor.
[   28.045490] Console: colour VGA+ 80x25
[   28.045508] Checking aperture...
[   28.045517] Calgary: detecting Calgary via BIOS EBDA area
[   28.045519] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   28.063397] Memory: 2054980k/2096000k available (2274k kernel code, 40628k reserved, 1181k data, 296k init)
[   28.063440] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
[   28.140869] Calibrating delay using timer specific routine.. 3611.22 BogoMIPS (lpj=7222440)
[   28.140897] Security Framework v1.0.0 initialized
[   28.140904] SELinux:  Disabled at boot.
[   28.141115] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   28.142182] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   28.142680] Mount-cache hash table entries: 256
[   28.142813] CPU: L1 I cache: 32K, L1 D cache: 32K
[   28.142816] CPU: L2 cache: 1024K
[   28.142819] CPU 0/0 -> Node 0
[   28.142821] using mwait in idle threads.
[   28.142823] CPU: Physical Processor ID: 0
[   28.142824] CPU: Processor Core ID: 0
[   28.142831] CPU0: Thermal monitoring enabled (TM2)
[   28.142842] SMP alternatives: switching to UP code
[   28.143079] Early unpacking initramfs... done
[   28.508614] ACPI: Core revision 20070126
[   28.508656] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   28.551179] Using local APIC timer interrupts.
[   28.606555] result 12529399
[   28.606557] Detected 12.529 MHz APIC timer.
[   28.608468] SMP alternatives: switching to SMP code
[   28.608542] Booting processor 1/2 APIC 0x1
[   28.618680] Initializing CPU#1
[   28.696325] Calibrating delay using timer specific routine.. 3608.51 BogoMIPS (lpj=7217024)
[   28.696332] CPU: L1 I cache: 32K, L1 D cache: 32K
[   28.696334] CPU: L2 cache: 1024K
[   28.696336] CPU 1/1 -> Node 0
[   28.696338] CPU: Physical Processor ID: 0
[   28.696340] CPU: Processor Core ID: 1
[   28.696346] CPU1: Thermal monitoring enabled (TM2)
[   28.696563] Genuine Intel(R) CPU            2160  @ 1.80GHz stepping 02
[   28.696579] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   28.720315] Brought up 2 CPUs
[   28.744906] migration_cost=17
[   28.745082] NET: Registered protocol family 16
[   28.745163] ACPI: bus type pci registered
[   28.745169] PCI: Using configuration type 1
[   28.745171] mtrr: your CPUs had inconsistent variable MTRR settings
[   28.745173] mtrr: probably your BIOS does not setup all CPUs.
[   28.745175] mtrr: corrected configuration.
[   28.746338] ACPI: EC: Look up EC in DSDT
[   28.750224] ACPI: Interpreter enabled
[   28.750229] ACPI: (supports S0 S3 S4 S5)
[   28.750250] ACPI: Using IOAPIC for interrupt routing
[   28.756312] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   28.756332] PCI: Probing PCI hardware (bus 00)
[   28.757673] PCI: Transparent bridge - 0000:00:1e.0
[   28.757735] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   28.757884] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[   28.757961] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[   28.758037] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[   28.758111] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   28.773029] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   28.773126] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   28.773222] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12 *14 15)
[   28.773317] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 14 *15)
[   28.773416] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   28.773511] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[   28.773607] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   28.773701] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   28.773800] Linux Plug and Play Support v0.97 (c) Adam Belay
[   28.773810] pnp: PnP ACPI init
[   28.773818] ACPI: bus type pnp registered
[   28.776414] pnp: PnP ACPI: found 13 devices
[   28.776417] ACPI: ACPI bus type pnp unregistered
[   28.776470] PCI: Using ACPI for IRQ routing
[   28.776472] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   28.776566] NET: Registered protocol family 8
[   28.776568] NET: Registered protocol family 20
[   28.776585] PCI-GART: No AMD northbridge found.
[   28.776590] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[   28.776594] hpet0: 4 64-bit timers, 14318180 Hz
[   28.777661] pnp: 00:09: ioport range 0x400-0x4bf has been reserved
[   28.777667] pnp: 00:0a: iomem range 0xf0000000-0xf3ffffff could not be reserved
[   28.777672] pnp: 00:0b: iomem range 0xd1e00-0xd3fff has been reserved
[   28.777675] pnp: 00:0b: iomem range 0xf0000-0xf7fff could not be reserved
[   28.777678] pnp: 00:0b: iomem range 0xf8000-0xfbfff could not be reserved
[   28.777681] pnp: 00:0b: iomem range 0xfc000-0xfffff could not be reserved
[   28.777982] PCI: Bridge: 0000:00:01.0
[   28.777985]   IO window: b000-bfff
[   28.777988]   MEM window: f4000000-f7ffffff
[   28.777992]   PREFETCH window: e0000000-efffffff
[   28.777995] PCI: Bridge: 0000:00:1c.0
[   28.777998]   IO window: a000-afff
[   28.778002]   MEM window: disabled.
[   28.778005]   PREFETCH window: disabled.
[   28.778009] PCI: Bridge: 0000:00:1c.3
[   28.778012]   IO window: c000-cfff
[   28.778017]   MEM window: f8000000-f8ffffff
[   28.778020]   PREFETCH window: disabled.
[   28.778024] PCI: Bridge: 0000:00:1c.4
[   28.778027]   IO window: d000-dfff
[   28.778032]   MEM window: f9000000-faffffff
[   28.778035]   PREFETCH window: 80000000-800fffff
[   28.778040] PCI: Bridge: 0000:00:1e.0
[   28.778041]   IO window: disabled.
[   28.778046]   MEM window: fb000000-fb0fffff
[   28.778049]   PREFETCH window: disabled.
[   28.778063] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   28.778069] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   28.778084] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   28.778089] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   28.778105] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   28.778110] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   28.778125] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
[   28.778130] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   28.778139] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   28.778150] NET: Registered protocol family 2
[   28.780245] Time: tsc clocksource has been installed.
[   28.820502] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   28.821254] TCP established hash table entries: 262144 (order: 10, 6291456 bytes)
[   28.824244] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   28.824736] TCP: Hash tables configured (established 262144 bind 65536)
[   28.824740] TCP reno registered
[   28.840702] checking if image is initramfs... it is
[   29.564199] Freeing initrd memory: 7203k freed
[   29.568059] audit: initializing netlink socket (disabled)
[   29.568076] audit(1202506323.464:1): initialized
[   29.570176] VFS: Disk quotas dquot_6.5.1
[   29.570228] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   29.570314] io scheduler noop registered
[   29.570316] io scheduler anticipatory registered
[   29.570318] io scheduler deadline registered
[   29.570413] io scheduler cfq registered (default)
[   29.571533] Boot video device is 0000:01:00.0
[   29.571650] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   29.571682] assign_interrupt_mode Found MSI capability
[   29.571685] Allocate Port Service[0000:00:01.0:pcie00]
[   29.571762] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   29.571802] assign_interrupt_mode Found MSI capability
[   29.571804] Allocate Port Service[0000:00:1c.0:pcie00]
[   29.571841] Allocate Port Service[0000:00:1c.0:pcie02]
[   29.571914] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   29.571950] assign_interrupt_mode Found MSI capability
[   29.571953] Allocate Port Service[0000:00:1c.3:pcie00]
[   29.571985] Allocate Port Service[0000:00:1c.3:pcie02]
[   29.572061] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   29.572097] assign_interrupt_mode Found MSI capability
[   29.572100] Allocate Port Service[0000:00:1c.4:pcie00]
[   29.572130] Allocate Port Service[0000:00:1c.4:pcie02]
[   29.595219] Real Time Clock Driver v1.12ac
[   29.595326] Linux agpgart interface v0.102 (c) Dave Jones
[   29.595329] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   29.595420] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   29.596604] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   29.597316] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   29.597439] input: Macintosh mouse button emulation as /class/input/input0
[   29.597557] PNP: No PS/2 controller found. Probing ports directly.
[   29.597888] serio: i8042 KBD port at 0x60,0x64 irq 1
[   29.597892] serio: i8042 AUX port at 0x60,0x64 irq 12
[   29.598021] mice: PS/2 mouse device common for all mice
[   29.598142] TCP cubic registered
[   29.598197] NET: Registered protocol family 1
[   29.598379] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   29.598387] Freeing unused kernel memory: 296k freed
[   30.763278] AppArmor: AppArmor initialized<5>audit(1202506324.660:2):  type=1505 info="AppArmor initialized" pid=1252
[   30.769568] fuse init (API version 7.8)
[   30.773635] Failure registering capabilities with primary security module.
[   30.800652] ACPI: Processor [CPU0] (supports 8 throttling states)
[   30.800768] ACPI: SSDT 7FEE81C0, 0087 (r1  PmRef  Cpu1Ist     3000 INTL 20040311)
[   30.800891] ACPI: Processor [CPU1] (supports 8 throttling states)
[   30.800903] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   30.800912] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   31.249102] usbcore: registered new interface driver usbfs
[   31.249124] usbcore: registered new interface driver hub
[   31.249146] usbcore: registered new device driver usb
[   31.249892] USB Universal Host Controller Interface driver v3.0
[   31.249972] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   31.249982] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   31.249985] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   31.250092] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   31.250119] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000e100
[   31.250230] usb usb1: configuration #1 chosen from 1 choice
[   31.250252] hub 1-0:1.0: USB hub found
[   31.250258] hub 1-0:1.0: 2 ports detected
[   31.298265] SCSI subsystem initialized
[   31.302510] libata version 2.21 loaded.
[   31.313256] Floppy drive(s): fd0 is 1.44M
[   31.349939] FDC 0 is a post-1991 82077
[   31.356713] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 21
[   31.356724] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   31.356728] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   31.356886] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   31.356915] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000e200
[   31.357283] usb usb2: configuration #1 chosen from 1 choice
[   31.357440] hub 2-0:1.0: USB hub found
[   31.357446] hub 2-0:1.0: 2 ports detected
[   31.461710] ACPI: PCI Interrupt 0000:00:1a.2[C] -> GSI 18 (level, low) -> IRQ 18
[   31.461721] PCI: Setting latency timer of device 0000:00:1a.2 to 64
[   31.461725] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[   31.461891] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[   31.461919] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000e000
[   31.462308] usb usb3: configuration #1 chosen from 1 choice
[   31.462477] hub 3-0:1.0: USB hub found
[   31.462484] hub 3-0:1.0: 2 ports detected
[   31.566100] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[   31.566110] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   31.566114] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   31.566288] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
[   31.566314] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e300
[   31.566725] usb usb4: configuration #1 chosen from 1 choice
[   31.566914] hub 4-0:1.0: USB hub found
[   31.566921] hub 4-0:1.0: 2 ports detected
[   31.670805] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   31.670815] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   31.670818] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   31.671012] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
[   31.671039] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e400
[   31.671484] usb usb5: configuration #1 chosen from 1 choice
[   31.671682] hub 5-0:1.0: USB hub found
[   31.671688] hub 5-0:1.0: 2 ports detected
[   31.702580] usb 2-1: new low speed USB device using uhci_hcd and address 2
[   31.775847] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   31.775858] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   31.775861] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   31.776075] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
[   31.776100] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e500
[   31.776588] usb usb6: configuration #1 chosen from 1 choice
[   31.776814] hub 6-0:1.0: USB hub found
[   31.776820] hub 6-0:1.0: 2 ports detected
[   31.877532] usb 2-1: configuration #1 chosen from 1 choice
[   31.881170] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[   31.881434] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   31.881440] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   31.881764] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 7
[   31.881796] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   31.881803] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfb105000
[   31.885696] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   31.885819] usb usb7: configuration #1 chosen from 1 choice
[   31.885850] hub 7-0:1.0: USB hub found
[   31.885858] hub 7-0:1.0: 6 ports detected
[   31.993002] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[   31.993332] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   31.993338] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   31.993389] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[   31.993421] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   31.993432] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfb104000
[   31.997314] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   31.997410] usb usb8: configuration #1 chosen from 1 choice
[   31.997437] hub 8-0:1.0: USB hub found
[   31.997443] hub 8-0:1.0: 6 ports detected
[   32.020971] usb 2-1: USB disconnect, address 2
[   32.101444] ahci 0000:00:1f.2: version 2.2
[   32.101471] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   32.520607] usbcore: registered new interface driver hiddev
[   32.758226] usb 2-1: new low speed USB device using uhci_hcd and address 3
[   32.937520] usb 2-1: configuration #1 chosen from 1 choice
[   33.105381] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[   33.105387] ahci 0000:00:1f.2: flags: 64bit ncq stag pm led clo pmp pio slum part
[   33.105393] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   33.105677] scsi0 : ahci
[   33.105739] scsi1 : ahci
[   33.105776] scsi2 : ahci
[   33.105810] scsi3 : ahci
[   33.105846] scsi4 : ahci
[   33.105880] scsi5 : ahci
[   33.105983] ata1: SATA max UDMA/133 cmd 0xffffc20000ab0100 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 19
[   33.105988] ata2: SATA max UDMA/133 cmd 0xffffc20000ab0180 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 19
[   33.105990] ata3: DUMMY
[   33.105992] ata4: DUMMY
[   33.105995] ata5: SATA max UDMA/133 cmd 0xffffc20000ab0300 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 19
[   33.105998] ata6: SATA max UDMA/133 cmd 0xffffc20000ab0380 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 19
[   33.190142] usb 2-2: new low speed USB device using uhci_hcd and address 4
[   33.377090] usb 2-2: configuration #1 chosen from 1 choice
[   33.398249] input: A4Tech PS/2+USB Mouse as /class/input/input1
[   33.398270] input: USB HID v1.10 Mouse [A4Tech PS/2+USB Mouse] on usb-0000:00:1a.1-1
[   33.413425] input: NOVATEK USB Keyboard as /class/input/input2
[   33.413435] input: USB HID v1.10 Keyboard [NOVATEK USB Keyboard] on usb-0000:00:1a.1-2
[   33.457966] input: NOVATEK USB Keyboard as /class/input/input3
[   33.458036] input,hiddev96: USB HID v1.10 Mouse [NOVATEK USB Keyboard] on usb-0000:00:1a.1-2
[   33.458051] usbcore: registered new interface driver usbhid
[   33.458056] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   33.593665] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   33.610805] ata1.00: ATA-7: WDC WD1600AAJS-00PSA0, 05.06H05, max UDMA/133
[   33.610810] ata1.00: 312581808 sectors, multi 0: LBA48 NCQ (depth 31/32)
[   33.611593] ata1.00: configured for UDMA/133
[   33.923841] ata2: SATA link down (SStatus 0 SControl 300)
[   34.407373] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   34.418016] ata5.00: ATA-7: WDC WD3200AAKS-00SBA0, 12.01B01, max UDMA/133
[   34.418022] ata5.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 31/32)
[   34.418765] ata5.00: configured for UDMA/133
[   34.734203] ata6: SATA link down (SStatus 0 SControl 300)
[   34.734340] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600AAJS-0 05.0 PQ: 0 ANSI: 5
[   34.734786] scsi 4:0:0:0: Direct-Access     ATA      WDC WD3200AAKS-0 12.0 PQ: 0 ANSI: 5
[   34.735479] r8169 Gigabit Ethernet driver 2.2LK loaded
[   34.735503] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   34.735520] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   34.735861] eth0: RTL8168b/8111b at 0xffffc20000ab2000, 00:1a:4d:4f:69:7b, XID 38000000 IRQ 16
[   34.738661] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 19 (level, low) -> IRQ 19
[   34.738700] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   34.738741] scsi6 : pata_jmicron
[   34.738800] scsi7 : pata_jmicron
[   34.738899] ata7: PATA max UDMA/100 cmd 0x000000000001c000 ctl 0x000000000001c102 bmdma 0x000000000001c400 irq 19
[   34.738902] ata8: PATA max UDMA/100 cmd 0x000000000001c200 ctl 0x000000000001c302 bmdma 0x000000000001c408 irq 19
[   34.746778] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   34.746790] sd 0:0:0:0: [sda] Write Protect is off
[   34.746792] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   34.746806] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.746866] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   34.746875] sd 0:0:0:0: [sda] Write Protect is off
[   34.746877] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   34.746890] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.746895]  sda: sda1
[   34.750300] sd 0:0:0:0: [sda] Attached SCSI disk
[   34.750374] sd 4:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[   34.750388] sd 4:0:0:0: [sdb] Write Protect is off
[   34.750391] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   34.750411] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.750469] sd 4:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[   34.750479] sd 4:0:0:0: [sdb] Write Protect is off
[   34.750481] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   34.750494] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.750497]  sdb: sdb1
[   34.756110] sd 4:0:0:0: [sdb] Attached SCSI disk
[   34.760424] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   34.760584] sd 4:0:0:0: Attached scsi generic sg1 type 0
[   35.070764] ata7.00: Host Protected Area detected:
[   35.070767]  current size: 234439535 sectors
[   35.070769]  native size: 234441648 sectors
[   35.072965] ata7.00: native size increased to 234441648 sectors
[   35.072970] ata7.00: ATA-6: WDC WD1200JB-00GVA0, 08.02D08, max UDMA/100
[   35.072974] ata7.00: 234441648 sectors, multi 16: LBA48
[   35.072981] ata7.01: ATAPI: _NEC DVD_RW ND-4550A, 1.06, max UDMA/33
[   35.090956] ata7.00: configured for UDMA/100
[   35.262631] ata7.01: configured for UDMA/33
[   35.419455] scsi 6:0:0:0: Direct-Access     ATA      WDC WD1200JB-00G 08.0 PQ: 0 ANSI: 5
[   35.419847] sd 6:0:0:0: [sdc] 234441648 512-byte hardware sectors (120034 MB)
[   35.419858] sd 6:0:0:0: [sdc] Write Protect is off
[   35.419860] sd 6:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   35.419874] sd 6:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   35.419919] sd 6:0:0:0: [sdc] 234441648 512-byte hardware sectors (120034 MB)
[   35.419927] sd 6:0:0:0: [sdc] Write Protect is off
[   35.419929] sd 6:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   35.419943] sd 6:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   35.419946]  sdc: sdc1 sdc2 < sdc5 sdc6 > sdc3
[   35.460136] sd 6:0:0:0: [sdc] Attached SCSI disk
[   35.460180] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   35.461469] scsi 6:0:1:0: CD-ROM            _NEC     DVD_RW ND-4550A  1.06 PQ: 0 ANSI: 5
[   35.461981] scsi 6:0:1:0: Attached scsi generic sg3 type 5
[   35.481099] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   35.481105] Uniform CD-ROM driver Revision: 3.20
[   35.481159] sr 6:0:1:0: Attached scsi CD-ROM sr0
[   35.803467] kjournald starting.  Commit interval 5 seconds
[   35.803480] EXT3-fs: mounted filesystem with ordered data mode.
[   41.324318] r8169: eth0: link up
[   41.324328] r8169: eth0: link up
[   42.962147] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   42.968297] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   43.083693] NET: Registered protocol family 17
[   43.219648] parport_pc 00:08: reported by Plug and Play ACPI
[   43.219712] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   43.308528] input: PC Speaker as /class/input/input4
[   43.346866] Linux video capture interface: v2.00
[   43.417253] saa7130/34: v4l2 driver version 0.2.14 loaded
[   43.417317] ACPI: PCI Interrupt 0000:05:02.0[A] -> GSI 18 (level, low) -> IRQ 18
[   43.417326] saa7134[0]: found at 0000:05:02.0, rev: 1, irq: 18, latency: 32, mmio: 0xfb000000
[   43.417333] saa7134[0]: subsystem: 11bd:002b, board: Pinnacle PCTV Stereo (saa7134) [card=26,autodetected]
[   43.417341] saa7134[0]: board init: gpio is 0
[   43.446159] usbcore: registered new interface driver xpad
[   43.446164] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   43.499085] nvidia: module license 'NVIDIA' taints kernel.
[   43.788528] saa7134[0]: i2c eeprom 00: bd 11 2b 00 f8 f8 1c 00 43 43 a9 1c 55 d2 b2 92
[   43.788542] saa7134[0]: i2c eeprom 10: 00 00 19 0e ff 20 ff ff ff ff ff ff ff ff ff ff
[   43.788553] saa7134[0]: i2c eeprom 20: 01 40 01 03 03 ff 03 01 08 ff 00 53 ff ff ff ff
[   43.788563] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   43.788574] saa7134[0]: i2c eeprom 40: ff 07 00 c0 86 ff 01 01 ff ff ff ff ff ff ff ff
[   43.788585] saa7134[0]: i2c eeprom 50: 0c 22 17 09 02 14 aa ac ff ff ff ff ff ff ff ff
[   43.788595] saa7134[0]: i2c eeprom 60: 03 03 19 71 fb ff ff ff ff ff ff ff ff ff ff ff
[   43.788606] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   43.868754] tuner 0-0043: chip found @ 0x86 (saa7134[0])
[   43.868787] tda9887 0-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   43.888835] tuner 0-0060: Chip ID is not zero. It is not a TEA5767
[   43.888841] tuner 0-0060: chip found @ 0xc0 (saa7134[0])
[   43.909002] tuner 0-0060: microtune: companycode=3cbf part=42 rev=21
[   43.945410] tuner 0-0060: microtune MT2050 found, OK
[   43.969483] tuner 0-0060: microtune: companycode=3cbf part=42 rev=21
[   44.001632] tuner 0-0060: microtune MT2050 found, OK
[   44.004326] saa7134[0]: registered device video0 [v4l2]
[   44.004344] saa7134[0]: registered device vbi0
[   44.004483] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   44.004492] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   44.004605] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  100.14.19  Wed Sep 12 14:08:38 PDT 2007
[   44.012812] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   44.013125] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   44.034482] saa7134 ALSA driver for DMA sound loaded
[   44.034510] saa7134[0]/alsa: saa7134[0] at 0xfb000000 irq 18 registered as card -2
[   45.143495] loop: module loaded
[   45.159385] lp0: using parport0 (interrupt-driven).
[   45.257927] Adding 1220900k swap on /dev/sdc6.  Priority:-1 extents:1 across:1220900k
[   48.663772] EXT3 FS on sdc3, internal journal
[   49.489012] NET: Registered protocol family 10
[   49.489110] lo: Disabled Privacy Extensions
[   60.319708] eth0: no IPv6 routers present
[   82.343200] No dock devices found.
[   82.435745] input: Power Button (FF) as /class/input/input5
[   82.435762] ACPI: Power Button (FF) [PWRF]
[   82.435806] input: Power Button (CM) as /class/input/input6
[   82.435820] ACPI: Power Button (CM) [PWRB]
[   83.210706] ppdev: user-space parallel port driver
[   83.802624] audit(1202502778.759:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5429 profile="/usr/sbin/cupsd"
[   86.409929] Failure registering capabilities with primary security module.
[   86.640191] Bluetooth: Core ver 2.11
[   86.640337] NET: Registered protocol family 31
[   86.640340] Bluetooth: HCI device and connection manager initialized
[   86.640343] Bluetooth: HCI socket layer initialized
[   86.749553] Bluetooth: L2CAP ver 2.8
[   86.749558] Bluetooth: L2CAP socket layer initialized
[   86.819444] Bluetooth: RFCOMM socket layer initialized
[   86.819525] Bluetooth: RFCOMM TTY layer initialized
[   86.819528] Bluetooth: RFCOMM ver 1.8
[  120.789937] usb 8-1: new high speed USB device using ehci_hcd and address 2
[  120.922739] usb 8-1: configuration #1 chosen from 1 choice
[  120.995177] usbcore: registered new interface driver libusual
[  121.025545] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[  121.025555] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[  121.031115] Initializing USB Mass Storage driver...
[  121.031206] scsi8 : SCSI emulation for USB Mass Storage devices
[  121.031272] usb-storage: device found at 2
[  121.031275] usb-storage: waiting for device to settle before scanning
[  121.031292] usbcore: registered new interface driver usb-storage
[  121.031296] USB Mass Storage support registered.
[  126.028899] usb-storage: device scan complete
[  126.029406] scsi 8:0:0:0: Direct-Access              USB Flash Memory 6.50 PQ: 0 ANSI: 0 CCS
[  126.031505] sd 8:0:0:0: [sdd] 3903487 512-byte hardware sectors (1999 MB)
[  126.032127] sd 8:0:0:0: [sdd] Write Protect is off
[  126.032132] sd 8:0:0:0: [sdd] Mode Sense: 45 00 00 08
[  126.032136] sd 8:0:0:0: [sdd] Assuming drive cache: write through
[  126.033874] sd 8:0:0:0: [sdd] 3903487 512-byte hardware sectors (1999 MB)
[  126.034499] sd 8:0:0:0: [sdd] Write Protect is off
[  126.034503] sd 8:0:0:0: [sdd] Mode Sense: 45 00 00 08
[  126.034507] sd 8:0:0:0: [sdd] Assuming drive cache: write through
[  126.034512]  sdd: sdd1
[  126.035540] sd 8:0:0:0: [sdd] Attached SCSI removable disk
[  126.035601] sd 8:0:0:0: Attached scsi generic sg4 type 0
```

---

### Post by Tosa on 2008-02-09
A thread that I've just read reminded me that I had changed
concurrency=none to concurrency=shell
in /etc/int.d/rc
before the kernel update. I've put it back to the original, and after reboot the USB flash stick is automounted again!?

---

