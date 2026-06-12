---
title: "Kubuntu won't boot"
date: 2008-06-10
forum: General Help
---

### Post by drinu21 on 2008-06-10
Hi all,

I have kubuntu 7.04 installed, all was working well and it's more than 8 months that i am using it, but now, all of a sudden would not boot.

it starts booting normally with the KUBUNTU title and the progress bar going up, but then it just stops, the progress bar goes all down again and it remain like that, with no sign that the hard disk is working,

thanks 

Adrian

---

### Post by cmnorton on 2008-06-10
The only thing that comes to mind is to boot with a rescue or live CD of some kind, and first see if that boots your hardware.

If you boot, mount your hard drive, and look through your logs in /var/log, kern.log, syslog, and messages would be good ones to view.

---

### Post by drinu21 on 2008-06-12
with the live CD it has booted, this is what i found from kern.log and syslog, 
```
Jun 12 11:53:20 Kubuntu kernel: Inspecting /boot/System.map-2.6.20-16-generic
Jun 12 11:53:20 Kubuntu kernel: Loaded 24980 symbols from /boot/System.map-2.6.20-16-generic.
Jun 12 11:53:20 Kubuntu kernel: Symbols match kernel version 2.6.20.
Jun 12 11:53:20 Kubuntu kernel: No module symbols loaded - kernel modules not enabled. 
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Sep 23 19:50:39 UTC 2007 (Ubuntu 2.6.20-16.32-generic)
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] sanitize start
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] sanitize end
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] copy_e820_map() type is E820_RAM
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003fed0000 end: 000000003ffd0000 type: 1
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] copy_e820_map() type is E820_RAM
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] copy_e820_map() start: 000000003ffd0000 size: 000000000000e000 end: 000000003ffde000 type: 3
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] copy_e820_map() start: 000000003ffde000 size: 0000000000022000 end: 0000000040000000 type: 4
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000001000 end: 00000000fec01000 type: 2
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000100000 end: 00000000fef00000 type: 2
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] copy_e820_map() start: 00000000fff80000 size: 0000000000080000 end: 0000000100000000 type: 2
Jun 12 11:53:20 Kubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Jun 12 11:53:20 Kubuntu kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Jun 12 11:53:20 Kubuntu kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Jun 12 11:53:20 Kubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffd0000 (usable)
Jun 12 11:53:20 Kubuntu kernel: [    0.000000]  BIOS-e820: 000000003ffd0000 - 000000003ffde000 (ACPI data)
Jun 12 11:53:20 Kubuntu kernel: [    0.000000]  BIOS-e820: 000000003ffde000 - 0000000040000000 (ACPI NVS)
Jun 12 11:53:20 Kubuntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Jun 12 11:53:20 Kubuntu kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
Jun 12 11:53:20 Kubuntu kernel: [    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] 127MB HIGHMEM available.
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] 896MB LOWMEM available.
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] found SMP MP-table at 000ff780
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] Entering add_active_range(0, 0, 262096) 0 entries of 256 used
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] Zone PFN ranges:
Jun 12 11:53:20 Kubuntu kernel: [    0.000000]   DMA             0 ->     4096
Jun 12 11:53:20 Kubuntu kernel: [    0.000000]   Normal       4096 ->   229376
Jun 12 11:53:20 Kubuntu kernel: [    0.000000]   HighMem    229376 ->   262096
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] early_node_map[1] active PFN ranges
Jun 12 11:53:20 Kubuntu kernel: [    0.000000]     0:        0 ->   262096
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] On node 0 totalpages: 262096
Jun 12 11:53:20 Kubuntu kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Jun 12 11:53:20 Kubuntu kernel: [    0.000000]   DMA zone: 0 pages reserved
Jun 12 11:53:20 Kubuntu kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Jun 12 11:53:20 Kubuntu kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Jun 12 11:53:20 Kubuntu kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Jun 12 11:53:20 Kubuntu kernel: [    0.000000]   HighMem zone: 255 pages used for memmap
Jun 12 11:53:20 Kubuntu kernel: [    0.000000]   HighMem zone: 32465 pages, LIFO batch:7
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] DMI present.
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: RSDP (v000 M S I                                 ) @ 0x000f8320
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: RSDT (v001 MSI_NB MEGABOOK 0x03000714 MSFT 0x00000097) @ 0x3ffd0000
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: FADT (v002 MSI_NB 1635X    0x03000714 MSFT 0x00000097) @ 0x3ffd0200
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: MADT (v001 MSI_NB OEMAPIC  0x03000714 MSFT 0x00000097) @ 0x3ffd0390
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: MCFG (v001 MSI_NB OEMMCFG  0x03000714 MSFT 0x00000097) @ 0x3ffd0400
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: SLIC (v001 MSI_NB MEGABOOK 0x03000714 MSFT 0x00000097) @ 0x3ffd0440
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: OEMB (v001 MSI_NB AMI_OEM  0x03000714 MSFT 0x00000097) @ 0x3ffde040
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: HPET (v001 MSI_NB OEMHPET0 0x03000714 MSFT 0x00000097) @ 0x3ffd5020
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: SSDT (v001 A M I  POWERNOW 0x00000001 AMD  0x00000001) @ 0x3ffd5060
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: DSDT (v001 M S I  1635X    0x04162004 INTL 0x20051117) @ 0x00000000
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] Processor #0 15:8 APIC version 16
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] Processor #1 15:8 APIC version 16
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: IRQ0 used by override.
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: IRQ2 used by override.
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: IRQ14 used by override.
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: IRQ15 used by override.
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] Detected 1607.404 MHz processor.
Jun 12 11:53:20 Kubuntu kernel: [   30.652752] Built 1 zonelists.  Total pages: 260049
Jun 12 11:53:20 Kubuntu kernel: [   30.652755] Kernel command line: root=UUID=3ab2cf20-76c0-45a3-b22a-9e1fdc5362b2 ro quiet splash
Jun 12 11:53:20 Kubuntu kernel: [   30.652909] mapped APIC to ffffd000 (fee00000)
Jun 12 11:53:20 Kubuntu kernel: [   30.652912] mapped IOAPIC to ffffc000 (fec00000)
Jun 12 11:53:20 Kubuntu kernel: [   30.652915] Enabling fast FPU save and restore... done.
Jun 12 11:53:20 Kubuntu kernel: [   30.652918] Enabling unmasked SIMD FPU exception support... done.
Jun 12 11:53:20 Kubuntu kernel: [   30.652926] Initializing CPU#0
Jun 12 11:53:20 Kubuntu kernel: [   30.652975] PID hash table entries: 4096 (order: 12, 16384 bytes)
Jun 12 11:53:20 Kubuntu kernel: [   30.653011] spurious 8259A interrupt: IRQ7.
Jun 12 11:53:20 Kubuntu kernel: [   30.655475] Console: colour VGA+ 80x25
Jun 12 11:53:20 Kubuntu kernel: [   30.655852] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jun 12 11:53:20 Kubuntu kernel: [   30.656305] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jun 12 11:53:20 Kubuntu kernel: [   30.679361] Memory: 1028196k/1048384k available (1993k kernel code, 19500k reserved, 900k data, 328k init, 130880k highmem)
Jun 12 11:53:20 Kubuntu kernel: [   30.679373] virtual kernel memory layout:
Jun 12 11:53:20 Kubuntu kernel: [   30.679374]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
Jun 12 11:53:20 Kubuntu kernel: [   30.679375]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jun 12 11:53:20 Kubuntu kernel: [   30.679377]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Jun 12 11:53:20 Kubuntu kernel: [   30.679378]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Jun 12 11:53:20 Kubuntu kernel: [   30.679380]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
Jun 12 11:53:20 Kubuntu kernel: [   30.679381]       .data : 0xc02f2429 - 0xc03d36d4   ( 900 kB)
Jun 12 11:53:20 Kubuntu kernel: [   30.679383]       .text : 0xc0100000 - 0xc02f2429   (1993 kB)
Jun 12 11:53:20 Kubuntu kernel: [   30.679387] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Jun 12 11:53:20 Kubuntu kernel: [   30.679531] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
Jun 12 11:53:20 Kubuntu kernel: [   30.679537] hpet0: 3 32-bit timers, 25000000 Hz
Jun 12 11:53:20 Kubuntu kernel: [   30.680545] Using HPET for base-timer
Jun 12 11:53:20 Kubuntu kernel: [   30.759523] Calibrating delay using timer specific routine.. 3217.49 BogoMIPS (lpj=6434996)
Jun 12 11:53:20 Kubuntu kernel: [   30.759566] Security Framework v1.0.0 initialized
Jun 12 11:53:20 Kubuntu kernel: [   30.759573] SELinux:  Disabled at boot.
Jun 12 11:53:20 Kubuntu kernel: [   30.759588] Mount-cache hash table entries: 512
Jun 12 11:53:20 Kubuntu kernel: [   30.759724] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
Jun 12 11:53:20 Kubuntu kernel: [   30.759734] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jun 12 11:53:20 Kubuntu kernel: [   30.759737] CPU: L2 Cache: 512K (64 bytes/line)
Jun 12 11:53:20 Kubuntu kernel: [   30.759740] CPU 0(2) -> Core 0
Jun 12 11:53:20 Kubuntu kernel: [   30.759742] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f
Jun 12 11:53:20 Kubuntu kernel: [   30.759753] Compat vDSO mapped to ffffe000.
Jun 12 11:53:20 Kubuntu kernel: [   30.759759] Remapping vsyscall page to ffffe000
Jun 12 11:53:20 Kubuntu kernel: [   30.759768] Checking 'hlt' instruction... OK.
Jun 12 11:53:20 Kubuntu kernel: [   30.775651] SMP alternatives: switching to UP code
Jun 12 11:53:20 Kubuntu kernel: [   30.776038] Early unpacking initramfs... done
Jun 12 11:53:20 Kubuntu kernel: [   31.122965] ACPI: Core revision 20060707
Jun 12 11:53:20 Kubuntu kernel: [   31.123423] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Jun 12 11:53:20 Kubuntu kernel: [   31.133494] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-52 stepping 02
Jun 12 11:53:20 Kubuntu kernel: [   31.133518] SMP alternatives: switching to SMP code
Jun 12 11:53:20 Kubuntu kernel: [   31.133817] Booting processor 1/1 eip 3000
Jun 12 11:53:20 Kubuntu kernel: [   31.144658] Initializing CPU#1
Jun 12 11:53:20 Kubuntu kernel: [   31.224104] Calibrating delay using timer specific routine.. 3214.68 BogoMIPS (lpj=6429361)
Jun 12 11:53:20 Kubuntu kernel: [   31.224112] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
Jun 12 11:53:20 Kubuntu kernel: [   31.224119] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jun 12 11:53:20 Kubuntu kernel: [   31.224122] CPU: L2 Cache: 512K (64 bytes/line)
Jun 12 11:53:20 Kubuntu kernel: [   31.224125] CPU 1(2) -> Core 1
Jun 12 11:53:20 Kubuntu kernel: [   31.224126] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f
Jun 12 11:53:20 Kubuntu kernel: [   31.223603] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-52 stepping 02
Jun 12 11:53:20 Kubuntu kernel: [   31.223616] Total of 2 processors activated (6432.17 BogoMIPS).
Jun 12 11:53:20 Kubuntu kernel: [   31.223921] ENABLING IO-APIC IRQs
Jun 12 11:53:20 Kubuntu kernel: [   31.224161] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Jun 12 11:53:20 Kubuntu kernel: [   31.371435] checking TSC synchronization across 2 CPUs: 
Jun 12 11:53:20 Kubuntu kernel: [    0.000001] CPU#0 had -323 usecs TSC skew, fixed it up.
Jun 12 11:53:20 Kubuntu kernel: [    0.000004] CPU#1 had 323 usecs TSC skew, fixed it up.
Jun 12 11:53:20 Kubuntu kernel: [    0.004000] Brought up 2 CPUs
Jun 12 11:53:20 Kubuntu kernel: [    0.079248] migration_cost=233
Jun 12 11:53:20 Kubuntu kernel: [    0.079499] Booting paravirtualized kernel on bare hardware
Jun 12 11:53:20 Kubuntu kernel: [    0.079573] Time: 11:52:51  Date: 05/12/108
Jun 12 11:53:20 Kubuntu kernel: [    0.079606] NET: Registered protocol family 16
Jun 12 11:53:20 Kubuntu kernel: [    0.079690] EISA bus registered
Jun 12 11:53:20 Kubuntu kernel: [    0.079694] ACPI: bus type pci registered
Jun 12 11:53:20 Kubuntu kernel: [    0.080417] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=6
Jun 12 11:53:20 Kubuntu kernel: [    0.080420] PCI: Using configuration type 1
Jun 12 11:53:20 Kubuntu kernel: [    0.080422] Setting up standard PCI resources
Jun 12 11:53:20 Kubuntu kernel: [    0.092046] ACPI: Interpreter enabled
Jun 12 11:53:20 Kubuntu kernel: [    0.092049] ACPI: Using IOAPIC for interrupt routing
Jun 12 11:53:20 Kubuntu kernel: [    0.092314] Error attaching device data
Jun 12 11:53:20 Kubuntu kernel: [    0.092321] Error attaching device data
Jun 12 11:53:20 Kubuntu kernel: [    0.092910] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jun 12 11:53:20 Kubuntu kernel: [    0.092917] PCI: Probing PCI hardware (bus 00)
Jun 12 11:53:20 Kubuntu kernel: [    0.094148] Boot video device is 0000:04:00.0
Jun 12 11:53:20 Kubuntu kernel: [    0.094433] PCI: Transparent bridge - 0000:00:10.0
Jun 12 11:53:20 Kubuntu kernel: [    0.094480] PCI: Bus #06 (-#09) is hidden behind transparent bridge #05 (-#06) (try 'pci=assign-busses')
Jun 12 11:53:20 Kubuntu kernel: [    0.094483] Please report the result to linux-kernel to fix this permanently
Jun 12 11:53:20 Kubuntu kernel: [    0.094517] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jun 12 11:53:20 Kubuntu kernel: [    0.112083] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PA._PRT]
Jun 12 11:53:20 Kubuntu kernel: [    0.116034] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Jun 12 11:53:20 Kubuntu kernel: [    0.116409] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
Jun 12 11:53:20 Kubuntu kernel: [    0.116743] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
Jun 12 11:53:20 Kubuntu kernel: [    0.118107] ACPI: PCI Interrupt Link [LNKA] (IRQs 16) *10
Jun 12 11:53:20 Kubuntu kernel: [    0.118618] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
Jun 12 11:53:20 Kubuntu kernel: [    0.119132] ACPI: PCI Interrupt Link [LNKC] (IRQs 17) *10
Jun 12 11:53:20 Kubuntu kernel: [    0.119643] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
Jun 12 11:53:20 Kubuntu kernel: [    0.120162] ACPI: PCI Interrupt Link [LNEA] (IRQs 18) *10
Jun 12 11:53:20 Kubuntu kernel: [    0.120680] ACPI: PCI Interrupt Link [LNEB] (IRQs 19) *5
Jun 12 11:53:20 Kubuntu kernel: [    0.121185] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.
Jun 12 11:53:20 Kubuntu kernel: [    0.121690] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
Jun 12 11:53:20 Kubuntu kernel: [    0.122198] ACPI: PCI Interrupt Link [LUB0] (IRQs 21) *7
Jun 12 11:53:20 Kubuntu kernel: [    0.122709] ACPI: PCI Interrupt Link [LUB2] (IRQs 21) *14
Jun 12 11:53:20 Kubuntu kernel: [    0.123217] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *0, disabled.
Jun 12 11:53:20 Kubuntu kernel: [    0.123728] ACPI: PCI Interrupt Link [LAZA] (IRQs 23) *11
Jun 12 11:53:20 Kubuntu kernel: [    0.124258] ACPI: PCI Interrupt Link [LACI] (IRQs 20 21 22 23) *0, disabled.
Jun 12 11:53:20 Kubuntu kernel: [    0.124760] ACPI: PCI Interrupt Link [LMC9] (IRQs 20 21 22 23) *0, disabled.
Jun 12 11:53:20 Kubuntu kernel: [    0.125261] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *5
Jun 12 11:53:20 Kubuntu kernel: [    0.125774] ACPI: PCI Interrupt Link [LPMU] (IRQs 20) *11
Jun 12 11:53:20 Kubuntu kernel: [    0.126290] ACPI: PCI Interrupt Link [LSA0] (IRQs 22) *10
Jun 12 11:53:20 Kubuntu kernel: [    0.126797] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *0, disabled.
Jun 12 11:53:20 Kubuntu kernel: [    0.127407] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
Jun 12 11:53:20 Kubuntu kernel: [    0.127540] Linux Plug and Play Support v0.97 (c) Adam Belay
Jun 12 11:53:20 Kubuntu kernel: [    0.127550] pnp: PnP ACPI init
Jun 12 11:53:20 Kubuntu kernel: [    0.132074] pnp: PnP ACPI: found 13 devices
Jun 12 11:53:20 Kubuntu kernel: [    0.132078] PnPBIOS: Disabled by ACPI PNP
Jun 12 11:53:20 Kubuntu kernel: [    0.132125] PCI: Using ACPI for IRQ routing
Jun 12 11:53:20 Kubuntu kernel: [    0.132129] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jun 12 11:53:20 Kubuntu kernel: [    0.149134] NET: Registered protocol family 8
Jun 12 11:53:20 Kubuntu kernel: [    0.149137] NET: Registered protocol family 20
Jun 12 11:53:20 Kubuntu kernel: [    0.150785] PCI: Bridge: 0000:00:02.0
Jun 12 11:53:20 Kubuntu kernel: [    0.150788]   IO window: b000-bfff
Jun 12 11:53:20 Kubuntu kernel: [    0.150792]   MEM window: f8c00000-f8cfffff
Jun 12 11:53:20 Kubuntu kernel: [    0.150795]   PREFETCH window: disabled.
Jun 12 11:53:20 Kubuntu kernel: [    0.150798] PCI: Bridge: 0000:00:03.0
Jun 12 11:53:20 Kubuntu kernel: [    0.150801]   IO window: c000-cfff
Jun 12 11:53:20 Kubuntu kernel: [    0.150804]   MEM window: f8d00000-f94fffff
Jun 12 11:53:20 Kubuntu kernel: [    0.150807]   PREFETCH window: bbf00000-bdefffff
Jun 12 11:53:20 Kubuntu kernel: [    0.150810] PCI: Bridge: 0000:00:04.0
Jun 12 11:53:20 Kubuntu kernel: [    0.150811]   IO window: disabled.
Jun 12 11:53:20 Kubuntu kernel: [    0.150814]   MEM window: f9500000-fd5fffff
Jun 12 11:53:20 Kubuntu kernel: [    0.150817]   PREFETCH window: bdf00000-ddefffff
Jun 12 11:53:20 Kubuntu kernel: [    0.150826] PCI: Bus 6, cardbus bridge: 0000:05:04.0
Jun 12 11:53:20 Kubuntu kernel: [    0.150828]   IO window: 0000d000-0000d0ff
Jun 12 11:53:20 Kubuntu kernel: [    0.150832]   IO window: 0000d400-0000d4ff
Jun 12 11:53:20 Kubuntu kernel: [    0.150837]   PREFETCH window: 50000000-53ffffff
Jun 12 11:53:20 Kubuntu kernel: [    0.150842]   MEM window: 54000000-57ffffff
Jun 12 11:53:20 Kubuntu kernel: [    0.150846] PCI: Bridge: 0000:00:10.0
Jun 12 11:53:20 Kubuntu kernel: [    0.150848]   IO window: d000-dfff
Jun 12 11:53:20 Kubuntu kernel: [    0.150853]   MEM window: fd600000-fdefffff
Jun 12 11:53:20 Kubuntu kernel: [    0.150856]   PREFETCH window: ddf00000-dfefffff
Jun 12 11:53:20 Kubuntu kernel: [    0.150870] PCI: Setting latency timer of device 0000:00:02.0 to 64
Jun 12 11:53:20 Kubuntu kernel: [    0.150878] PCI: Setting latency timer of device 0000:00:03.0 to 64
Jun 12 11:53:20 Kubuntu kernel: [    0.150885] PCI: Setting latency timer of device 0000:00:04.0 to 64
Jun 12 11:53:20 Kubuntu kernel: [    0.150893] PCI: Setting latency timer of device 0000:00:10.0 to 64
Jun 12 11:53:20 Kubuntu kernel: [    0.151385] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 17
Jun 12 11:53:20 Kubuntu kernel: [    0.151396] ACPI: PCI Interrupt 0000:05:04.0[A] -> Link [LNKC] -> GSI 17 (level, low) -> IRQ 16
Jun 12 11:53:20 Kubuntu kernel: [    0.151436] NET: Registered protocol family 2
Jun 12 11:53:20 Kubuntu kernel: [    0.184038] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jun 12 11:53:20 Kubuntu kernel: [    0.184180] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jun 12 11:53:20 Kubuntu kernel: [    0.185081] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jun 12 11:53:20 Kubuntu kernel: [    0.185561] TCP: Hash tables configured (established 131072 bind 65536)
Jun 12 11:53:20 Kubuntu kernel: [    0.185564] TCP reno registered
Jun 12 11:53:20 Kubuntu kernel: [    0.196115] checking if image is initramfs... it is
Jun 12 11:53:20 Kubuntu kernel: [    0.880483] Freeing initrd memory: 6778k freed
Jun 12 11:53:20 Kubuntu kernel: [    1.468000] audit: initializing netlink socket (disabled)
Jun 12 11:53:20 Kubuntu kernel: [    1.468000] audit(1213271572.652:1): initialized
Jun 12 11:53:20 Kubuntu kernel: [    1.468000] highmem bounce pool size: 64 pages
Jun 12 11:53:20 Kubuntu kernel: [    1.468000] VFS: Disk quotas dquot_6.5.1
Jun 12 11:53:20 Kubuntu kernel: [    1.468000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jun 12 11:53:20 Kubuntu kernel: [    1.468000] io scheduler noop registered
Jun 12 11:53:20 Kubuntu kernel: [    1.468000] io scheduler anticipatory registered
Jun 12 11:53:20 Kubuntu kernel: [    1.468000] io scheduler deadline registered
Jun 12 11:53:20 Kubuntu kernel: [    1.468000] io scheduler cfq registered (default)
Jun 12 11:53:20 Kubuntu kernel: [    1.488000] PCI: Setting latency timer of device 0000:00:02.0 to 64
Jun 12 11:53:20 Kubuntu kernel: [    1.488000] assign_interrupt_mode Found MSI capability
Jun 12 11:53:20 Kubuntu kernel: [    1.488000] Allocate Port Service[0000:00:02.0:pcie00]
Jun 12 11:53:20 Kubuntu kernel: [    1.488000] PCI: Setting latency timer of device 0000:00:03.0 to 64
Jun 12 11:53:20 Kubuntu kernel: [    1.488000] assign_interrupt_mode Found MSI capability
Jun 12 11:53:20 Kubuntu kernel: [    1.488000] Allocate Port Service[0000:00:03.0:pcie00]
Jun 12 11:53:20 Kubuntu kernel: [    1.488000] PCI: Setting latency timer of device 0000:00:04.0 to 64
Jun 12 11:53:20 Kubuntu kernel: [    1.488000] assign_interrupt_mode Found MSI capability
Jun 12 11:53:20 Kubuntu kernel: [    1.488000] Allocate Port Service[0000:00:04.0:pcie00]
Jun 12 11:53:20 Kubuntu kernel: [    1.488000] isapnp: Scanning for PnP cards...
Jun 12 11:53:20 Kubuntu kernel: [    1.840000] isapnp: No Plug & Play device found
Jun 12 11:53:20 Kubuntu kernel: [    1.864000] Real Time Clock Driver v1.12ac
Jun 12 11:53:20 Kubuntu kernel: [    1.864000] hpet_resources: 0xfed00000 is busy
Jun 12 11:53:20 Kubuntu kernel: [    1.864000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jun 12 11:53:20 Kubuntu kernel: [    1.864000] mice: PS/2 mouse device common for all mice
Jun 12 11:53:20 Kubuntu kernel: [    1.864000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jun 12 11:53:20 Kubuntu kernel: [    1.864000] input: Macintosh mouse button emulation as /class/input/input0
Jun 12 11:53:20 Kubuntu kernel: [    1.864000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jun 12 11:53:20 Kubuntu kernel: [    1.864000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jun 12 11:53:20 Kubuntu kernel: [    1.864000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Jun 12 11:53:20 Kubuntu kernel: [    1.868000] i8042.c: Detected active multiplexing controller, rev 1.1.
Jun 12 11:53:20 Kubuntu kernel: [    1.868000] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun 12 11:53:20 Kubuntu kernel: [    1.868000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Jun 12 11:53:20 Kubuntu kernel: [    1.868000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Jun 12 11:53:20 Kubuntu kernel: [    1.868000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Jun 12 11:53:20 Kubuntu kernel: [    1.868000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Jun 12 11:53:20 Kubuntu kernel: [    1.868000] EISA: Probing bus 0 at eisa.0
Jun 12 11:53:20 Kubuntu kernel: [    1.868000] Cannot allocate resource for EISA slot 2
Jun 12 11:53:20 Kubuntu kernel: [    1.868000] Cannot allocate resource for EISA slot 4
Jun 12 11:53:20 Kubuntu kernel: [    1.868000] Cannot allocate resource for EISA slot 5
Jun 12 11:53:20 Kubuntu kernel: [    1.868000] Cannot allocate resource for EISA slot 6
Jun 12 11:53:20 Kubuntu kernel: [    1.868000] EISA: Detected 0 cards.
Jun 12 11:53:20 Kubuntu kernel: [    1.896000] TCP cubic registered
Jun 12 11:53:20 Kubuntu kernel: [    1.896000] NET: Registered protocol family 1
Jun 12 11:53:20 Kubuntu kernel: [    1.896000] Starting balanced_irq
Jun 12 11:53:20 Kubuntu kernel: [    1.896000] Using IPI No-Shortcut mode
Jun 12 11:53:20 Kubuntu kernel: [    1.896000] input: AT Translated Set 2 keyboard as /class/input/input1
Jun 12 11:53:20 Kubuntu kernel: [    1.896000] ACPI: (supports S0 S1 S3 S4 S5)
Jun 12 11:53:20 Kubuntu kernel: [    1.896000]   Magic number: 12:405:883
Jun 12 11:53:20 Kubuntu kernel: [    1.896000]   hash matches device ptyx7
Jun 12 11:53:20 Kubuntu kernel: [    1.896000]   hash matches device ptyua
Jun 12 11:53:20 Kubuntu kernel: [    1.896000] Freeing unused kernel memory: 328k freed
Jun 12 11:53:20 Kubuntu kernel: [    1.900000] Time: hpet clocksource has been installed.
Jun 12 11:53:20 Kubuntu kernel: [    3.168000] Capability LSM initialized
Jun 12 11:53:20 Kubuntu kernel: [    3.224000] ACPI: Thermal Zone [THRM] (69 C)
Jun 12 11:53:20 Kubuntu kernel: [    3.764000] usbcore: registered new interface driver usbfs
Jun 12 11:53:20 Kubuntu kernel: [    3.764000] usbcore: registered new interface driver hub
Jun 12 11:53:20 Kubuntu kernel: [    3.764000] usbcore: registered new device driver usb
Jun 12 11:53:20 Kubuntu kernel: [    3.764000] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 21
Jun 12 11:53:20 Kubuntu kernel: [    3.764000] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUB2] -> GSI 21 (level, low) -> IRQ 17
Jun 12 11:53:20 Kubuntu kernel: [    3.764000] PCI: Setting latency timer of device 0000:00:0b.1 to 64
Jun 12 11:53:20 Kubuntu kernel: [    3.764000] ehci_hcd 0000:00:0b.1: EHCI Host Controller
Jun 12 11:53:20 Kubuntu kernel: [    3.764000] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
Jun 12 11:53:20 Kubuntu kernel: [    3.764000] ehci_hcd 0000:00:0b.1: debug port 1
Jun 12 11:53:20 Kubuntu kernel: [    3.764000] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
Jun 12 11:53:20 Kubuntu kernel: [    3.764000] ehci_hcd 0000:00:0b.1: irq 17, io mem 0xfdfbfc00
Jun 12 11:53:20 Kubuntu kernel: [    3.764000] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jun 12 11:53:20 Kubuntu kernel: [    3.764000] usb usb1: configuration #1 chosen from 1 choice
Jun 12 11:53:20 Kubuntu kernel: [    3.764000] hub 1-0:1.0: USB hub found
Jun 12 11:53:20 Kubuntu kernel: [    3.764000] hub 1-0:1.0: 8 ports detected
Jun 12 11:53:20 Kubuntu kernel: [    3.800000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Jun 12 11:53:20 Kubuntu kernel: [    3.872000] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 21
Jun 12 11:53:20 Kubuntu kernel: [    3.872000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUB0] -> GSI 21 (level, low) -> IRQ 17
Jun 12 11:53:20 Kubuntu kernel: [    3.872000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
Jun 12 11:53:20 Kubuntu kernel: [    3.872000] ohci_hcd 0000:00:0b.0: OHCI Host Controller
Jun 12 11:53:20 Kubuntu kernel: [    3.872000] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
Jun 12 11:53:20 Kubuntu kernel: [    3.872000] ohci_hcd 0000:00:0b.0: irq 17, io mem 0xfdfbe000
Jun 12 11:53:20 Kubuntu kernel: [    3.884000] ieee1394: Initialized config rom entry `ip1394'
Jun 12 11:53:20 Kubuntu kernel: [    3.932000] usb usb2: configuration #1 chosen from 1 choice
Jun 12 11:53:20 Kubuntu kernel: [    3.932000] hub 2-0:1.0: USB hub found
Jun 12 11:53:20 Kubuntu kernel: [    3.932000] hub 2-0:1.0: 8 ports detected
Jun 12 11:53:20 Kubuntu kernel: [    4.040000] r8169 Gigabit Ethernet driver 2.2LK loaded
Jun 12 11:53:20 Kubuntu kernel: [    4.040000] ACPI: PCI Interrupt Link [LNEB] enabled at IRQ 19
Jun 12 11:53:20 Kubuntu kernel: [    4.040000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNEB] -> GSI 19 (level, low) -> IRQ 18
Jun 12 11:53:20 Kubuntu kernel: [    4.040000] PCI: Setting latency timer of device 0000:01:00.0 to 64
Jun 12 11:53:20 Kubuntu kernel: [    4.040000] eth0: RTL8168b/8111b at 0xf8854000, 00:19:db:39:b9:16, IRQ 18
Jun 12 11:53:20 Kubuntu kernel: [    4.048000] NFORCE-MCP51: IDE controller at PCI slot 0000:00:0d.0
Jun 12 11:53:20 Kubuntu kernel: [    4.048000] NFORCE-MCP51: chipset revision 161
Jun 12 11:53:20 Kubuntu kernel: [    4.048000] NFORCE-MCP51: not 100%% native mode: will probe irqs later
Jun 12 11:53:20 Kubuntu kernel: [    4.048000] NFORCE-MCP51: 0000:00:0d.0 (rev a1) UDMA133 controller
Jun 12 11:53:20 Kubuntu kernel: [    4.048000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:pio
Jun 12 11:53:20 Kubuntu kernel: [    4.048000] Probing IDE interface ide1...
Jun 12 11:53:20 Kubuntu kernel: [    4.048000] SCSI subsystem initialized
Jun 12 11:53:20 Kubuntu kernel: [    4.056000] libata version 2.20 loaded.
Jun 12 11:53:20 Kubuntu kernel: [    4.116000] usb 1-1: new high speed USB device using ehci_hcd and address 2
Jun 12 11:53:20 Kubuntu kernel: [    4.264000] usb 1-1: configuration #1 chosen from 1 choice
Jun 12 11:53:20 Kubuntu kernel: [    4.752000] usb 2-2: new low speed USB device using ohci_hcd and address 2
Jun 12 11:53:20 Kubuntu kernel: [    4.788000] hdc: HL-DT-ST DVDRAM GSA-T20N, ATAPI CD/DVD-ROM drive
Jun 12 11:53:20 Kubuntu kernel: [    4.960000] usb 2-2: configuration #1 chosen from 1 choice
Jun 12 11:53:20 Kubuntu kernel: [    4.972000] usbcore: registered new interface driver hiddev
Jun 12 11:53:20 Kubuntu kernel: [    4.980000] input: MosArt Optical Mouse as /class/input/input2
Jun 12 11:53:20 Kubuntu kernel: [    4.980000] input: USB HID v1.10 Mouse [MosArt Optical Mouse] on usb-0000:00:0b.0-2
Jun 12 11:53:20 Kubuntu kernel: [    4.980000] usbcore: registered new interface driver usbhid
Jun 12 11:53:20 Kubuntu kernel: [    4.980000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Jun 12 11:53:20 Kubuntu kernel: [    5.128000] ide1 at 0x170-0x177,0x376 on irq 15
Jun 12 11:53:20 Kubuntu kernel: [    5.132000] ACPI: PCI Interrupt 0000:05:04.4[A] -> Link [LNKC] -> GSI 17 (level, low) -> IRQ 16
Jun 12 11:53:20 Kubuntu kernel: [    5.184000] sata_nv 0000:00:0e.0: version 3.3
Jun 12 11:53:20 Kubuntu kernel: [    5.184000] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 22
Jun 12 11:53:20 Kubuntu kernel: [    5.184000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LSA0] -> GSI 22 (level, low) -> IRQ 19
Jun 12 11:53:20 Kubuntu kernel: [    5.184000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
Jun 12 11:53:20 Kubuntu kernel: [    5.184000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[fdeff000-fdeff7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
Jun 12 11:53:20 Kubuntu kernel: [    5.184000] ata1: SATA max UDMA/133 cmd 0x0001e800 ctl 0x0001e482 bmdma 0x0001e000 irq 19
Jun 12 11:53:20 Kubuntu kernel: [    5.184000] ata2: SATA max UDMA/133 cmd 0x0001e400 ctl 0x0001e082 bmdma 0x0001e008 irq 19
Jun 12 11:53:20 Kubuntu kernel: [    5.184000] scsi0 : sata_nv
Jun 12 11:53:20 Kubuntu kernel: [    5.656000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun 12 11:53:20 Kubuntu kernel: [    6.056000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
Jun 12 11:53:20 Kubuntu kernel: [    6.056000] ata1.00: ATA-7: WDC WD1200BEVS-22LAT0, 01.06M01, max UDMA/133
Jun 12 11:53:20 Kubuntu kernel: [    6.056000] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/1)
Jun 12 11:53:20 Kubuntu kernel: [    6.068000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
Jun 12 11:53:20 Kubuntu kernel: [    6.068000] ata1.00: configured for UDMA/133
Jun 12 11:53:20 Kubuntu kernel: [    6.068000] scsi1 : sata_nv
Jun 12 11:53:20 Kubuntu kernel: [    6.380000] ata2: SATA link down (SStatus 0 SControl 300)
Jun 12 11:53:20 Kubuntu kernel: [    6.384000] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1200BEVS-2 01.0 PQ: 0 ANSI: 5
Jun 12 11:53:20 Kubuntu kernel: [    6.392000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
Jun 12 11:53:20 Kubuntu kernel: [    6.392000] sda: Write Protect is off
Jun 12 11:53:20 Kubuntu kernel: [    6.392000] sda: Mode Sense: 00 3a 00 00
Jun 12 11:53:20 Kubuntu kernel: [    6.392000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 12 11:53:20 Kubuntu kernel: [    6.392000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
Jun 12 11:53:20 Kubuntu kernel: [    6.392000] sda: Write Protect is off
Jun 12 11:53:20 Kubuntu kernel: [    6.392000] sda: Mode Sense: 00 3a 00 00
Jun 12 11:53:20 Kubuntu kernel: [    6.392000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 12 11:53:20 Kubuntu kernel: [    6.392000]  sda:<6>hdc: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
Jun 12 11:53:20 Kubuntu kernel: [    6.404000] Uniform CD-ROM driver Revision: 3.20
Jun 12 11:53:20 Kubuntu kernel: [    6.436000]  sda1 sda2 sda3 <<7>ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00dc100022321b01]
Jun 12 11:53:20 Kubuntu kernel: [    6.468000]  sda5 >
Jun 12 11:53:20 Kubuntu kernel: [    6.468000] sd 0:0:0:0: Attached scsi disk sda
Jun 12 11:53:20 Kubuntu kernel: [    6.472000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jun 12 11:53:20 Kubuntu kernel: [    6.784000] Attempting manual resume
Jun 12 11:53:20 Kubuntu kernel: [    6.784000] swsusp: Resume From Partition 8:5
Jun 12 11:53:20 Kubuntu kernel: [    6.784000] PM: Checking swsusp image.
Jun 12 11:53:20 Kubuntu kernel: [    6.784000] PM: Resume from disk failed.
Jun 12 11:53:20 Kubuntu kernel: [    6.820000] kjournald starting.  Commit interval 5 seconds
Jun 12 11:53:20 Kubuntu kernel: [    6.820000] EXT3-fs: mounted filesystem with ordered data mode.
Jun 12 11:53:20 Kubuntu kernel: [   18.888000] r8169: eth0: link up
Jun 12 11:53:20 Kubuntu kernel: [   18.888000] r8169: eth0: link up
Jun 12 11:53:20 Kubuntu kernel: [   19.532000] NET: Registered protocol family 10
Jun 12 11:53:20 Kubuntu kernel: [   19.532000] lo: Disabled Privacy Extensions
Jun 12 11:53:20 Kubuntu kernel: [   20.088000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun 12 11:53:20 Kubuntu kernel: [   20.132000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jun 12 11:53:20 Kubuntu kernel: [   20.724000] sdhci: Secure Digital Host Controller Interface driver
Jun 12 11:53:20 Kubuntu kernel: [   20.724000] sdhci: Copyright(c) Pierre Ossman
Jun 12 11:53:20 Kubuntu kernel: [   20.724000] sdhci: SDHCI controller found at 0000:05:04.2 [1217:7120] (rev 1)
Jun 12 11:53:20 Kubuntu kernel: [   20.724000] ACPI: PCI Interrupt 0000:05:04.2[A] -> Link [LNKC] -> GSI 17 (level, low) -> IRQ 16
Jun 12 11:53:20 Kubuntu kernel: [   20.724000] sdhci:slot0: Unknown controller version (16). You may experience problems.
Jun 12 11:53:20 Kubuntu kernel: [   20.724000] mmc0: SDHCI at 0xfdefe400 irq 16 PIO
Jun 12 11:53:20 Kubuntu kernel: [   20.732000] Yenta: CardBus bridge found at 0000:05:04.0 [1462:3fdf]
Jun 12 11:53:20 Kubuntu kernel: [   20.732000] Yenta O2: res at 0x94/0xD4: 00/ea
Jun 12 11:53:20 Kubuntu kernel: [   20.732000] Yenta O2: enabling read prefetch/write burst
Jun 12 11:53:20 Kubuntu kernel: [   20.744000] Linux agpgart interface v0.102 (c) Dave Jones
Jun 12 11:53:20 Kubuntu kernel: [   20.780000] input: PC Speaker as /class/input/input3
Jun 12 11:53:20 Kubuntu kernel: [   20.864000] Yenta: ISA IRQ mask 0x0cb8, PCI irq 16
Jun 12 11:53:20 Kubuntu kernel: [   20.864000] Socket status: 30000006
Jun 12 11:53:20 Kubuntu kernel: [   20.864000] Yenta: Raising subordinate bus# of parent bus (#05) from #06 to #09
Jun 12 11:53:20 Kubuntu kernel: [   20.864000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xdfff
Jun 12 11:53:20 Kubuntu kernel: [   20.864000] cs: IO port probe 0xd000-0xdfff: clean.
Jun 12 11:53:20 Kubuntu kernel: [   20.864000] pcmcia: parent PCI bridge Memory window: 0xfd600000 - 0xfdefffff
Jun 12 11:53:20 Kubuntu kernel: [   20.864000] pcmcia: parent PCI bridge Memory window: 0xddf00000 - 0xdfefffff
Jun 12 11:53:20 Kubuntu kernel: [   20.868000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x5000
Jun 12 11:53:20 Kubuntu kernel: [   20.868000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x6000
Jun 12 11:53:20 Kubuntu kernel: [   20.872000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 16
Jun 12 11:53:20 Kubuntu kernel: [   20.872000] ACPI: PCI Interrupt 0000:05:09.0[A] -> Link [LNKA] -> GSI 16 (level, low) -> IRQ 20
Jun 12 11:53:20 Kubuntu kernel: [   20.872000] rt2500 1.1.0 BETA4 2006/06/18 http://rt2x00.serialmonkey.com
Jun 12 11:53:20 Kubuntu kernel: [   20.916000] rt2500 EEPROM:  1  2  3  4  5  6  7  8  9 10 11 12 13 14  Channel
Jun 12 11:53:20 Kubuntu kernel: [   20.916000] rt2500 EEPROM:  6  6  6  6  6  6  6  6  6  6  6  6  7  7  dBm Maximum
Jun 12 11:53:20 Kubuntu kernel: [   21.376000] input: ImPS/2 Logitech Wheel Mouse as /class/input/input4
Jun 12 11:53:20 Kubuntu kernel: [   21.432000] cs: IO port probe 0x100-0x3af: clean.
Jun 12 11:53:20 Kubuntu kernel: [   21.432000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Jun 12 11:53:20 Kubuntu kernel: [   21.436000] cs: IO port probe 0x820-0x8ff: clean.
Jun 12 11:53:20 Kubuntu kernel: [   21.436000] cs: IO port probe 0xc00-0xcf7: clean.
Jun 12 11:53:20 Kubuntu kernel: [   21.436000] cs: IO port probe 0xa00-0xaff: clean.
Jun 12 11:53:20 Kubuntu kernel: [   21.676000] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 23
Jun 12 11:53:20 Kubuntu kernel: [   21.676000] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 23 (level, low) -> IRQ 21
Jun 12 11:53:20 Kubuntu kernel: [   21.676000] PCI: Setting latency timer of device 0000:00:10.1 to 64
Jun 12 11:53:20 Kubuntu kernel: [   22.168000] NET: Registered protocol family 17
Jun 12 11:53:20 Kubuntu kernel: [   22.400000] fuse init (API version 7.8)
Jun 12 11:53:20 Kubuntu kernel: [   22.480000] lp: driver loaded but no devices found
Jun 12 11:53:20 Kubuntu kernel: [   22.548000] Adding 1004020k swap on /dev/disk/by-uuid/0ac3f9ac-a8fd-4a72-bc4d-c0dd4f5299c7.  Priority:-1 extents:1 across:1004020k
Jun 12 11:53:20 Kubuntu kernel: [   22.732000] EXT3 FS on sda2, internal journal
Jun 12 11:53:20 Kubuntu kernel: [   28.236000] PPP generic driver version 2.4.2
Jun 12 11:53:20 Kubuntu kernel: [   28.792000] No dock devices found.
Jun 12 11:53:20 Kubuntu kernel: [   28.804000] Using specific hotkey driver
Jun 12 11:53:20 Kubuntu kernel: [   28.848000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Jun 12 11:53:20 Kubuntu kernel: [   28.872000] ACPI: Battery Slot [BAT1] (battery present)
Jun 12 11:53:20 Kubuntu kernel: [   28.972000] ibm_acpi: ec object not found
Jun 12 11:53:20 Kubuntu kernel: [   29.036000] ACPI: AC Adapter [ADP1] (on-line)
Jun 12 11:53:20 Kubuntu kernel: [   29.056000] input: Power Button (FF) as /class/input/input5
Jun 12 11:53:20 Kubuntu kernel: [   29.056000] ACPI: Power Button (FF) [PWRF]
Jun 12 11:53:20 Kubuntu kernel: [   29.060000] input: Lid Switch as /class/input/input6
Jun 12 11:53:20 Kubuntu kernel: [   29.060000] ACPI: Lid Switch [LID0]
Jun 12 11:53:20 Kubuntu kernel: [   29.084000] input: Sleep Button (CM) as /class/input/input7
Jun 12 11:53:20 Kubuntu kernel: [   29.084000] ACPI: Sleep Button (CM) [SLPB]
Jun 12 11:53:20 Kubuntu kernel: [   29.100000] input: Power Button (CM) as /class/input/input8
Jun 12 11:53:20 Kubuntu kernel: [   29.100000] ACPI: Power Button (CM) [PWRB]
Jun 12 11:53:20 Kubuntu kernel: [   29.164000] pcc_acpi: loading...
Jun 12 11:53:20 Kubuntu kernel: [   29.404000] powernow-k8: Found 2 AMD Turion(tm) 64 X2 Mobile Technology TL-52 processors (version 2.00.00)
Jun 12 11:53:20 Kubuntu kernel: [   29.404000] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x12
Jun 12 11:53:20 Kubuntu kernel: [   29.404000] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x1e
Jun 12 11:53:20 Kubuntu kernel: [   29.588000] eth0: no IPv6 routers present
Jun 12 11:53:21 Kubuntu kernel: [   30.976000] ra0: no IPv6 routers present
Jun 12 11:53:25 Kubuntu kernel: [   34.508000] ppdev: user-space parallel port driver
Jun 12 11:53:26 Kubuntu kernel: [   35.476000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Jun 12 11:53:26 Kubuntu kernel: [   35.476000] apm: disabled - APM is not SMP safe.
Jun 12 11:53:27 Kubuntu kernel: [   36.340000] Bluetooth: Core ver 2.11
Jun 12 11:53:27 Kubuntu kernel: [   36.340000] NET: Registered protocol family 31
Jun 12 11:53:27 Kubuntu kernel: [   36.340000] Bluetooth: HCI device and connection manager initialized
Jun 12 11:53:27 Kubuntu kernel: [   36.340000] Bluetooth: HCI socket layer initialized
Jun 12 11:53:27 Kubuntu kernel: [   36.364000] Bluetooth: L2CAP ver 2.8
Jun 12 11:53:27 Kubuntu kernel: [   36.364000] Bluetooth: L2CAP socket layer initialized
Jun 12 11:53:27 Kubuntu kernel: [   36.412000] Bluetooth: RFCOMM socket layer initialized
Jun 12 11:53:27 Kubuntu kernel: [   36.412000] Bluetooth: RFCOMM TTY layer initialized
Jun 12 11:53:27 Kubuntu kernel: [   36.412000] Bluetooth: RFCOMM ver 1.8
Jun 12 11:54:24 Kubuntu kernel: [   93.452000] NET: Registered protocol family 24
Jun 12 11:54:26 Kubuntu kernel: [   96.204000] ip_tables: (C) 2000-2006 Netfilter Core Team

```

```
Jun 12 11:53:20 Kubuntu syslogd 1.4.1#20ubuntu4: restart.
Jun 12 11:53:20 Kubuntu kernel: Inspecting /boot/System.map-2.6.20-16-generic
Jun 12 11:53:20 Kubuntu kernel: Loaded 24980 symbols from /boot/System.map-2.6.20-16-generic.
Jun 12 11:53:20 Kubuntu kernel: Symbols match kernel version 2.6.20.
Jun 12 11:53:20 Kubuntu kernel: No module symbols loaded - kernel modules not enabled. 
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Sep 23 19:50:39 UTC 2007 (Ubuntu 2.6.20-16.32-generic)
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] sanitize start
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] sanitize end
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] copy_e820_map() type is E820_RAM
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003fed0000 end: 000000003ffd0000 type: 1
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] copy_e820_map() type is E820_RAM
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] copy_e820_map() start: 000000003ffd0000 size: 000000000000e000 end: 000000003ffde000 type: 3
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] copy_e820_map() start: 000000003ffde000 size: 0000000000022000 end: 0000000040000000 type: 4
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000001000 end: 00000000fec01000 type: 2
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000100000 end: 00000000fef00000 type: 2
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] copy_e820_map() start: 00000000fff80000 size: 0000000000080000 end: 0000000100000000 type: 2
Jun 12 11:53:20 Kubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Jun 12 11:53:20 Kubuntu kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Jun 12 11:53:20 Kubuntu kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Jun 12 11:53:20 Kubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffd0000 (usable)
Jun 12 11:53:20 Kubuntu kernel: [    0.000000]  BIOS-e820: 000000003ffd0000 - 000000003ffde000 (ACPI data)
Jun 12 11:53:20 Kubuntu kernel: [    0.000000]  BIOS-e820: 000000003ffde000 - 0000000040000000 (ACPI NVS)
Jun 12 11:53:20 Kubuntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Jun 12 11:53:20 Kubuntu kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
Jun 12 11:53:20 Kubuntu kernel: [    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] 127MB HIGHMEM available.
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] 896MB LOWMEM available.
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] found SMP MP-table at 000ff780
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] Entering add_active_range(0, 0, 262096) 0 entries of 256 used
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] Zone PFN ranges:
Jun 12 11:53:20 Kubuntu kernel: [    0.000000]   DMA             0 ->     4096
Jun 12 11:53:20 Kubuntu kernel: [    0.000000]   Normal       4096 ->   229376
Jun 12 11:53:20 Kubuntu kernel: [    0.000000]   HighMem    229376 ->   262096
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] early_node_map[1] active PFN ranges
Jun 12 11:53:20 Kubuntu kernel: [    0.000000]     0:        0 ->   262096
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] On node 0 totalpages: 262096
Jun 12 11:53:20 Kubuntu kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Jun 12 11:53:20 Kubuntu kernel: [    0.000000]   DMA zone: 0 pages reserved
Jun 12 11:53:20 Kubuntu kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Jun 12 11:53:20 Kubuntu kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Jun 12 11:53:20 Kubuntu kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Jun 12 11:53:20 Kubuntu kernel: [    0.000000]   HighMem zone: 255 pages used for memmap
Jun 12 11:53:20 Kubuntu kernel: [    0.000000]   HighMem zone: 32465 pages, LIFO batch:7
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] DMI present.
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: RSDP (v000 M S I                                 ) @ 0x000f8320
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: RSDT (v001 MSI_NB MEGABOOK 0x03000714 MSFT 0x00000097) @ 0x3ffd0000
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: FADT (v002 MSI_NB 1635X    0x03000714 MSFT 0x00000097) @ 0x3ffd0200
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: MADT (v001 MSI_NB OEMAPIC  0x03000714 MSFT 0x00000097) @ 0x3ffd0390
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: MCFG (v001 MSI_NB OEMMCFG  0x03000714 MSFT 0x00000097) @ 0x3ffd0400
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: SLIC (v001 MSI_NB MEGABOOK 0x03000714 MSFT 0x00000097) @ 0x3ffd0440
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: OEMB (v001 MSI_NB AMI_OEM  0x03000714 MSFT 0x00000097) @ 0x3ffde040
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: HPET (v001 MSI_NB OEMHPET0 0x03000714 MSFT 0x00000097) @ 0x3ffd5020
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: SSDT (v001 A M I  POWERNOW 0x00000001 AMD  0x00000001) @ 0x3ffd5060
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: DSDT (v001 M S I  1635X    0x04162004 INTL 0x20051117) @ 0x00000000
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] Processor #0 15:8 APIC version 16
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] Processor #1 15:8 APIC version 16
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: IRQ0 used by override.
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: IRQ2 used by override.
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: IRQ14 used by override.
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: IRQ15 used by override.
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
Jun 12 11:53:20 Kubuntu kernel: [    0.000000] Detected 1607.404 MHz processor.
Jun 12 11:53:20 Kubuntu kernel: [   30.652752] Built 1 zonelists.  Total pages: 260049
Jun 12 11:53:20 Kubuntu kernel: [   30.652755] Kernel command line: root=UUID=3ab2cf20-76c0-45a3-b22a-9e1fdc5362b2 ro quiet splash
Jun 12 11:53:20 Kubuntu kernel: [   30.652909] mapped APIC to ffffd000 (fee00000)
Jun 12 11:53:20 Kubuntu kernel: [   30.652912] mapped IOAPIC to ffffc000 (fec00000)
Jun 12 11:53:20 Kubuntu kernel: [   30.652915] Enabling fast FPU save and restore... done.
Jun 12 11:53:20 Kubuntu kernel: [   30.652918] Enabling unmasked SIMD FPU exception support... done.
Jun 12 11:53:20 Kubuntu kernel: [   30.652926] Initializing CPU#0
Jun 12 11:53:20 Kubuntu kernel: [   30.652975] PID hash table entries: 4096 (order: 12, 16384 bytes)
Jun 12 11:53:20 Kubuntu kernel: [   30.653011] spurious 8259A interrupt: IRQ7.
Jun 12 11:53:20 Kubuntu kernel: [   30.655475] Console: colour VGA+ 80x25
Jun 12 11:53:20 Kubuntu kernel: [   30.655852] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jun 12 11:53:20 Kubuntu kernel: [   30.656305] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jun 12 11:53:20 Kubuntu kernel: [   30.679361] Memory: 1028196k/1048384k available (1993k kernel code, 19500k reserved, 900k data, 328k init, 130880k highmem)
Jun 12 11:53:20 Kubuntu kernel: [   30.679373] virtual kernel memory layout:
Jun 12 11:53:20 Kubuntu kernel: [   30.679374]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
Jun 12 11:53:20 Kubuntu kernel: [   30.679375]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jun 12 11:53:20 Kubuntu kernel: [   30.679377]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Jun 12 11:53:20 Kubuntu kernel: [   30.679378]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Jun 12 11:53:20 Kubuntu kernel: [   30.679380]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
Jun 12 11:53:20 Kubuntu kernel: [   30.679381]       .data : 0xc02f2429 - 0xc03d36d4   ( 900 kB)
Jun 12 11:53:20 Kubuntu kernel: [   30.679383]       .text : 0xc0100000 - 0xc02f2429   (1993 kB)
Jun 12 11:53:20 Kubuntu kernel: [   30.679387] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Jun 12 11:53:20 Kubuntu kernel: [   30.679531] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
Jun 12 11:53:20 Kubuntu kernel: [   30.679537] hpet0: 3 32-bit timers, 25000000 Hz
Jun 12 11:53:20 Kubuntu kernel: [   30.680545] Using HPET for base-timer
Jun 12 11:53:20 Kubuntu kernel: [   30.759523] Calibrating delay using timer specific routine.. 3217.49 BogoMIPS (lpj=6434996)
Jun 12 11:53:20 Kubuntu kernel: [   30.759566] Security Framework v1.0.0 initialized
Jun 12 11:53:20 Kubuntu kernel: [   30.759573] SELinux:  Disabled at boot.
Jun 12 11:53:20 Kubuntu kernel: [   30.759588] Mount-cache hash table entries: 512
Jun 12 11:53:20 Kubuntu kernel: [   30.759724] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
Jun 12 11:53:20 Kubuntu kernel: [   30.759734] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jun 12 11:53:20 Kubuntu kernel: [   30.759737] CPU: L2 Cache: 512K (64 bytes/line)
Jun 12 11:53:20 Kubuntu kernel: [   30.759740] CPU 0(2) -> Core 0
Jun 12 11:53:20 Kubuntu kernel: [   30.759742] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f
Jun 12 11:53:20 Kubuntu kernel: [   30.759753] Compat vDSO mapped to ffffe000.
Jun 12 11:53:20 Kubuntu kernel: [   30.759759] Remapping vsyscall page to ffffe000
Jun 12 11:53:20 Kubuntu kernel: [   30.759768] Checking 'hlt' instruction... OK.
Jun 12 11:53:20 Kubuntu kernel: [   30.775651] SMP alternatives: switching to UP code
Jun 12 11:53:20 Kubuntu kernel: [   30.776038] Early unpacking initramfs... done
Jun 12 11:53:20 Kubuntu kernel: [   31.122965] ACPI: Core revision 20060707
Jun 12 11:53:20 Kubuntu kernel: [   31.123423] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Jun 12 11:53:20 Kubuntu kernel: [   31.133494] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-52 stepping 02
Jun 12 11:53:20 Kubuntu kernel: [   31.133518] SMP alternatives: switching to SMP code
Jun 12 11:53:20 Kubuntu kernel: [   31.133817] Booting processor 1/1 eip 3000
Jun 12 11:53:20 Kubuntu kernel: [   31.144658] Initializing CPU#1
Jun 12 11:53:20 Kubuntu kernel: [   31.224104] Calibrating delay using timer specific routine.. 3214.68 BogoMIPS (lpj=6429361)
Jun 12 11:53:20 Kubuntu kernel: [   31.224112] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
Jun 12 11:53:20 Kubuntu kernel: [   31.224119] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jun 12 11:53:20 Kubuntu kernel: [   31.224122] CPU: L2 Cache: 512K (64 bytes/line)
Jun 12 11:53:20 Kubuntu kernel: [   31.224125] CPU 1(2) -> Core 1
Jun 12 11:53:20 Kubuntu kernel: [   31.224126] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f
Jun 12 11:53:20 Kubuntu kernel: [   31.223603] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-52 stepping 02
Jun 12 11:53:20 Kubuntu kernel: [   31.223616] Total of 2 processors activated (6432.17 BogoMIPS).
Jun 12 11:53:20 Kubuntu kernel: [   31.223921] ENABLING IO-APIC IRQs
Jun 12 11:53:20 Kubuntu kernel: [   31.224161] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Jun 12 11:53:20 Kubuntu kernel: [   31.371435] checking TSC synchronization across 2 CPUs: 
Jun 12 11:53:20 Kubuntu kernel: [    0.000001] CPU#0 had -323 usecs TSC skew, fixed it up.
Jun 12 11:53:20 Kubuntu kernel: [    0.000004] CPU#1 had 323 usecs TSC skew, fixed it up.
Jun 12 11:53:20 Kubuntu kernel: [    0.004000] Brought up 2 CPUs
Jun 12 11:53:20 Kubuntu kernel: [    0.079248] migration_cost=233
Jun 12 11:53:20 Kubuntu kernel: [    0.079499] Booting paravirtualized kernel on bare hardware
Jun 12 11:53:20 Kubuntu kernel: [    0.079573] Time: 11:52:51  Date: 05/12/108
Jun 12 11:53:20 Kubuntu kernel: [    0.079606] NET: Registered protocol family 16
Jun 12 11:53:20 Kubuntu kernel: [    0.079690] EISA bus registered
Jun 12 11:53:20 Kubuntu kernel: [    0.079694] ACPI: bus type pci registered
Jun 12 11:53:20 Kubuntu kernel: [    0.080417] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=6
Jun 12 11:53:20 Kubuntu kernel: [    0.080420] PCI: Using configuration type 1
Jun 12 11:53:20 Kubuntu kernel: [    0.080422] Setting up standard PCI resources
Jun 12 11:53:20 Kubuntu kernel: [    0.092046] ACPI: Interpreter enabled
Jun 12 11:53:20 Kubuntu kernel: [    0.092049] ACPI: Using IOAPIC for interrupt routing
Jun 12 11:53:20 Kubuntu kernel: [    0.092314] Error attaching device data
Jun 12 11:53:20 Kubuntu kernel: [    0.092321] Error attaching device data
Jun 12 11:53:20 Kubuntu kernel: [    0.092910] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jun 12 11:53:20 Kubuntu kernel: [    0.092917] PCI: Probing PCI hardware (bus 00)
Jun 12 11:53:20 Kubuntu kernel: [    0.094148] Boot video device is 0000:04:00.0
Jun 12 11:53:20 Kubuntu kernel: [    0.094433] PCI: Transparent bridge - 0000:00:10.0
Jun 12 11:53:20 Kubuntu kernel: [    0.094480] PCI: Bus #06 (-#09) is hidden behind transparent bridge #05 (-#06) (try 'pci=assign-busses')
Jun 12 11:53:20 Kubuntu kernel: [    0.094483] Please report the result to linux-kernel to fix this permanently
Jun 12 11:53:20 Kubuntu kernel: [    0.094517] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jun 12 11:53:20 Kubuntu kernel: [    0.112083] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PA._PRT]
Jun 12 11:53:20 Kubuntu kernel: [    0.116034] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Jun 12 11:53:20 Kubuntu kernel: [    0.116409] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
Jun 12 11:53:20 Kubuntu kernel: [    0.116743] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
Jun 12 11:53:20 Kubuntu kernel: [    0.118107] ACPI: PCI Interrupt Link [LNKA] (IRQs 16) *10
Jun 12 11:53:20 Kubuntu kernel: [    0.118618] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
Jun 12 11:53:20 Kubuntu kernel: [    0.119132] ACPI: PCI Interrupt Link [LNKC] (IRQs 17) *10
Jun 12 11:53:20 Kubuntu kernel: [    0.119643] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
Jun 12 11:53:20 Kubuntu kernel: [    0.120162] ACPI: PCI Interrupt Link [LNEA] (IRQs 18) *10
Jun 12 11:53:20 Kubuntu kernel: [    0.120680] ACPI: PCI Interrupt Link [LNEB] (IRQs 19) *5
Jun 12 11:53:20 Kubuntu kernel: [    0.121185] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.
Jun 12 11:53:20 Kubuntu kernel: [    0.121690] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
Jun 12 11:53:20 Kubuntu kernel: [    0.122198] ACPI: PCI Interrupt Link [LUB0] (IRQs 21) *7
Jun 12 11:53:20 Kubuntu kernel: [    0.122709] ACPI: PCI Interrupt Link [LUB2] (IRQs 21) *14
Jun 12 11:53:20 Kubuntu kernel: [    0.123217] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *0, disabled.
Jun 12 11:53:20 Kubuntu kernel: [    0.123728] ACPI: PCI Interrupt Link [LAZA] (IRQs 23) *11
Jun 12 11:53:20 Kubuntu kernel: [    0.124258] ACPI: PCI Interrupt Link [LACI] (IRQs 20 21 22 23) *0, disabled.
Jun 12 11:53:20 Kubuntu kernel: [    0.124760] ACPI: PCI Interrupt Link [LMC9] (IRQs 20 21 22 23) *0, disabled.
Jun 12 11:53:20 Kubuntu kernel: [    0.125261] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *5
Jun 12 11:53:20 Kubuntu kernel: [    0.125774] ACPI: PCI Interrupt Link [LPMU] (IRQs 20) *11
Jun 12 11:53:20 Kubuntu kernel: [    0.126290] ACPI: PCI Interrupt Link [LSA0] (IRQs 22) *10
Jun 12 11:53:20 Kubuntu kernel: [    0.126797] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *0, disabled.
Jun 12 11:53:20 Kubuntu kernel: [    0.127407] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
Jun 12 11:53:20 Kubuntu kernel: [    0.127540] Linux Plug and Play Support v0.97 (c) Adam Belay
Jun 12 11:53:20 Kubuntu kernel: [    0.127550] pnp: PnP ACPI init
Jun 12 11:53:20 Kubuntu kernel: [    0.132074] pnp: PnP ACPI: found 13 devices
Jun 12 11:53:20 Kubuntu kernel: [    0.132078] PnPBIOS: Disabled by ACPI PNP
Jun 12 11:53:20 Kubuntu kernel: [    0.132125] PCI: Using ACPI for IRQ routing
Jun 12 11:53:20 Kubuntu kernel: [    0.132129] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jun 12 11:53:20 Kubuntu kernel: [    0.149134] NET: Registered protocol family 8
Jun 12 11:53:20 Kubuntu kernel: [    0.149137] NET: Registered protocol family 20
Jun 12 11:53:20 Kubuntu kernel: [    0.150785] PCI: Bridge: 0000:00:02.0
Jun 12 11:53:20 Kubuntu kernel: [    0.150788]   IO window: b000-bfff
Jun 12 11:53:20 Kubuntu kernel: [    0.150792]   MEM window: f8c00000-f8cfffff
Jun 12 11:53:20 Kubuntu kernel: [    0.150795]   PREFETCH window: disabled.
Jun 12 11:53:20 Kubuntu kernel: [    0.150798] PCI: Bridge: 0000:00:03.0
Jun 12 11:53:20 Kubuntu kernel: [    0.150801]   IO window: c000-cfff
Jun 12 11:53:20 Kubuntu kernel: [    0.150804]   MEM window: f8d00000-f94fffff
Jun 12 11:53:20 Kubuntu kernel: [    0.150807]   PREFETCH window: bbf00000-bdefffff
Jun 12 11:53:20 Kubuntu kernel: [    0.150810] PCI: Bridge: 0000:00:04.0
Jun 12 11:53:20 Kubuntu kernel: [    0.150811]   IO window: disabled.
Jun 12 11:53:20 Kubuntu kernel: [    0.150814]   MEM window: f9500000-fd5fffff
Jun 12 11:53:20 Kubuntu kernel: [    0.150817]   PREFETCH window: bdf00000-ddefffff
Jun 12 11:53:20 Kubuntu kernel: [    0.150826] PCI: Bus 6, cardbus bridge: 0000:05:04.0
Jun 12 11:53:20 Kubuntu kernel: [    0.150828]   IO window: 0000d000-0000d0ff
Jun 12 11:53:20 Kubuntu kernel: [    0.150832]   IO window: 0000d400-0000d4ff
Jun 12 11:53:20 Kubuntu kernel: [    0.150837]   PREFETCH window: 50000000-53ffffff
Jun 12 11:53:20 Kubuntu kernel: [    0.150842]   MEM window: 54000000-57ffffff
Jun 12 11:53:20 Kubuntu kernel: [    0.150846] PCI: Bridge: 0000:00:10.0
Jun 12 11:53:20 Kubuntu kernel: [    0.150848]   IO window: d000-dfff
Jun 12 11:53:20 Kubuntu kernel: [    0.150853]   MEM window: fd600000-fdefffff
Jun 12 11:53:20 Kubuntu kernel: [    0.150856]   PREFETCH window: ddf00000-dfefffff
Jun 12 11:53:20 Kubuntu kernel: [    0.150870] PCI: Setting latency timer of device 0000:00:02.0 to 64
Jun 12 11:53:20 Kubuntu kernel: [    0.150878] PCI: Setting latency timer of device 0000:00:03.0 to 64
Jun 12 11:53:20 Kubuntu kernel: [    0.150885] PCI: Setting latency timer of device 0000:00:04.0 to 64
Jun 12 11:53:20 Kubuntu kernel: [    0.150893] PCI: Setting latency timer of device 0000:00:10.0 to 64
Jun 12 11:53:20 Kubuntu kernel: [    0.151385] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 17
Jun 12 11:53:20 Kubuntu kernel: [    0.151396] ACPI: PCI Interrupt 0000:05:04.0[A] -> Link [LNKC] -> GSI 17 (level, low) -> IRQ 16
Jun 12 11:53:20 Kubuntu kernel: [    0.151436] NET: Registered protocol family 2
Jun 12 11:53:20 Kubuntu kernel: [    0.184038] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jun 12 11:53:20 Kubuntu kernel: [    0.184180] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jun 12 11:53:20 Kubuntu kernel: [    0.185081] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jun 12 11:53:20 Kubuntu kernel: [    0.185561] TCP: Hash tables configured (established 131072 bind 65536)
Jun 12 11:53:20 Kubuntu kernel: [    0.185564] TCP reno registered
Jun 12 11:53:20 Kubuntu kernel: [    0.196115] checking if image is initramfs... it is
Jun 12 11:53:20 Kubuntu kernel: [    0.880483] Freeing initrd memory: 6778k freed
Jun 12 11:53:20 Kubuntu kernel: [    1.468000] audit: initializing netlink socket (disabled)
Jun 12 11:53:20 Kubuntu kernel: [    1.468000] audit(1213271572.652:1): initialized
Jun 12 11:53:20 Kubuntu kernel: [    1.468000] highmem bounce pool size: 64 pages
Jun 12 11:53:20 Kubuntu kernel: [    1.468000] VFS: Disk quotas dquot_6.5.1
Jun 12 11:53:20 Kubuntu kernel: [    1.468000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jun 12 11:53:20 Kubuntu kernel: [    1.468000] io scheduler noop registered
Jun 12 11:53:20 Kubuntu kernel: [    1.468000] io scheduler anticipatory registered
Jun 12 11:53:20 Kubuntu kernel: [    1.468000] io scheduler deadline registered
Jun 12 11:53:20 Kubuntu kernel: [    1.468000] io scheduler cfq registered (default)
Jun 12 11:53:20 Kubuntu kernel: [    1.488000] PCI: Setting latency timer of device 0000:00:02.0 to 64
Jun 12 11:53:20 Kubuntu kernel: [    1.488000] assign_interrupt_mode Found MSI capability
Jun 12 11:53:20 Kubuntu kernel: [    1.488000] Allocate Port Service[0000:00:02.0:pcie00]
Jun 12 11:53:20 Kubuntu kernel: [    1.488000] PCI: Setting latency timer of device 0000:00:03.0 to 64
Jun 12 11:53:20 Kubuntu kernel: [    1.488000] assign_interrupt_mode Found MSI capability
Jun 12 11:53:20 Kubuntu kernel: [    1.488000] Allocate Port Service[0000:00:03.0:pcie00]
Jun 12 11:53:20 Kubuntu kernel: [    1.488000] PCI: Setting latency timer of device 0000:00:04.0 to 64
Jun 12 11:53:20 Kubuntu kernel: [    1.488000] assign_interrupt_mode Found MSI capability
Jun 12 11:53:20 Kubuntu kernel: [    1.488000] Allocate Port Service[0000:00:04.0:pcie00]
Jun 12 11:53:20 Kubuntu kernel: [    1.488000] isapnp: Scanning for PnP cards...
Jun 12 11:53:20 Kubuntu kernel: [    1.840000] isapnp: No Plug & Play device found
Jun 12 11:53:20 Kubuntu kernel: [    1.864000] Real Time Clock Driver v1.12ac
Jun 12 11:53:20 Kubuntu kernel: [    1.864000] hpet_resources: 0xfed00000 is busy
Jun 12 11:53:20 Kubuntu kernel: [    1.864000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jun 12 11:53:20 Kubuntu kernel: [    1.864000] mice: PS/2 mouse device common for all mice
Jun 12 11:53:20 Kubuntu kernel: [    1.864000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jun 12 11:53:20 Kubuntu kernel: [    1.864000] input: Macintosh mouse button emulation as /class/input/input0
Jun 12 11:53:20 Kubuntu kernel: [    1.864000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jun 12 11:53:20 Kubuntu kernel: [    1.864000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jun 12 11:53:20 Kubuntu kernel: [    1.864000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Jun 12 11:53:20 Kubuntu kernel: [    1.868000] i8042.c: Detected active multiplexing controller, rev 1.1.
Jun 12 11:53:20 Kubuntu kernel: [    1.868000] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun 12 11:53:20 Kubuntu kernel: [    1.868000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Jun 12 11:53:20 Kubuntu kernel: [    1.868000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Jun 12 11:53:20 Kubuntu kernel: [    1.868000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Jun 12 11:53:20 Kubuntu kernel: [    1.868000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Jun 12 11:53:20 Kubuntu kernel: [    1.868000] EISA: Probing bus 0 at eisa.0
Jun 12 11:53:20 Kubuntu kernel: [    1.868000] Cannot allocate resource for EISA slot 2
Jun 12 11:53:20 Kubuntu kernel: [    1.868000] Cannot allocate resource for EISA slot 4
Jun 12 11:53:20 Kubuntu kernel: [    1.868000] Cannot allocate resource for EISA slot 5
Jun 12 11:53:20 Kubuntu kernel: [    1.868000] Cannot allocate resource for EISA slot 6
Jun 12 11:53:20 Kubuntu kernel: [    1.868000] EISA: Detected 0 cards.
Jun 12 11:53:20 Kubuntu kernel: [    1.896000] TCP cubic registered
Jun 12 11:53:20 Kubuntu kernel: [    1.896000] NET: Registered protocol family 1
Jun 12 11:53:20 Kubuntu kernel: [    1.896000] Starting balanced_irq
Jun 12 11:53:20 Kubuntu kernel: [    1.896000] Using IPI No-Shortcut mode
Jun 12 11:53:20 Kubuntu kernel: [    1.896000] input: AT Translated Set 2 keyboard as /class/input/input1
Jun 12 11:53:20 Kubuntu kernel: [    1.896000] ACPI: (supports S0 S1 S3 S4 S5)
Jun 12 11:53:20 Kubuntu kernel: [    1.896000]   Magic number: 12:405:883
Jun 12 11:53:20 Kubuntu kernel: [    1.896000]   hash matches device ptyx7
Jun 12 11:53:20 Kubuntu kernel: [    1.896000]   hash matches device ptyua
Jun 12 11:53:20 Kubuntu kernel: [    1.896000] Freeing unused kernel memory: 328k freed
Jun 12 11:53:20 Kubuntu kernel: [    1.900000] Time: hpet clocksource has been installed.
Jun 12 11:53:20 Kubuntu kernel: [    3.168000] Capability LSM initialized
Jun 12 11:53:20 Kubuntu kernel: [    3.224000] ACPI: Thermal Zone [THRM] (69 C)
Jun 12 11:53:20 Kubuntu kernel: [    3.764000] usbcore: registered new interface driver usbfs
Jun 12 11:53:20 Kubuntu kernel: [    3.764000] usbcore: registered new interface driver hub
Jun 12 11:53:20 Kubuntu kernel: [    3.764000] usbcore: registered new device driver usb
Jun 12 11:53:20 Kubuntu kernel: [    3.764000] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 21
Jun 12 11:53:20 Kubuntu kernel: [    3.764000] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUB2] -> GSI 21 (level, low) -> IRQ 17
Jun 12 11:53:20 Kubuntu kernel: [    3.764000] PCI: Setting latency timer of device 0000:00:0b.1 to 64
Jun 12 11:53:20 Kubuntu kernel: [    3.764000] ehci_hcd 0000:00:0b.1: EHCI Host Controller
Jun 12 11:53:20 Kubuntu kernel: [    3.764000] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
Jun 12 11:53:20 Kubuntu kernel: [    3.764000] ehci_hcd 0000:00:0b.1: debug port 1
Jun 12 11:53:20 Kubuntu kernel: [    3.764000] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
Jun 12 11:53:20 Kubuntu kernel: [    3.764000] ehci_hcd 0000:00:0b.1: irq 17, io mem 0xfdfbfc00
Jun 12 11:53:20 Kubuntu kernel: [    3.764000] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jun 12 11:53:20 Kubuntu kernel: [    3.764000] usb usb1: configuration #1 chosen from 1 choice
Jun 12 11:53:20 Kubuntu kernel: [    3.764000] hub 1-0:1.0: USB hub found
Jun 12 11:53:20 Kubuntu kernel: [    3.764000] hub 1-0:1.0: 8 ports detected
Jun 12 11:53:20 Kubuntu kernel: [    3.800000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Jun 12 11:53:20 Kubuntu kernel: [    3.872000] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 21
Jun 12 11:53:20 Kubuntu kernel: [    3.872000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUB0] -> GSI 21 (level, low) -> IRQ 17
Jun 12 11:53:20 Kubuntu kernel: [    3.872000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
Jun 12 11:53:20 Kubuntu kernel: [    3.872000] ohci_hcd 0000:00:0b.0: OHCI Host Controller
Jun 12 11:53:20 Kubuntu kernel: [    3.872000] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
Jun 12 11:53:20 Kubuntu kernel: [    3.872000] ohci_hcd 0000:00:0b.0: irq 17, io mem 0xfdfbe000
Jun 12 11:53:20 Kubuntu kernel: [    3.884000] ieee1394: Initialized config rom entry `ip1394'
Jun 12 11:53:20 Kubuntu kernel: [    3.932000] usb usb2: configuration #1 chosen from 1 choice
Jun 12 11:53:20 Kubuntu kernel: [    3.932000] hub 2-0:1.0: USB hub found
Jun 12 11:53:20 Kubuntu kernel: [    3.932000] hub 2-0:1.0: 8 ports detected
Jun 12 11:53:20 Kubuntu kernel: [    4.040000] r8169 Gigabit Ethernet driver 2.2LK loaded
Jun 12 11:53:20 Kubuntu kernel: [    4.040000] ACPI: PCI Interrupt Link [LNEB] enabled at IRQ 19
Jun 12 11:53:20 Kubuntu kernel: [    4.040000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNEB] -> GSI 19 (level, low) -> IRQ 18
Jun 12 11:53:20 Kubuntu kernel: [    4.040000] PCI: Setting latency timer of device 0000:01:00.0 to 64
Jun 12 11:53:20 Kubuntu kernel: [    4.040000] eth0: RTL8168b/8111b at 0xf8854000, 00:19:db:39:b9:16, IRQ 18
Jun 12 11:53:20 Kubuntu kernel: [    4.048000] NFORCE-MCP51: IDE controller at PCI slot 0000:00:0d.0
Jun 12 11:53:20 Kubuntu kernel: [    4.048000] NFORCE-MCP51: chipset revision 161
Jun 12 11:53:20 Kubuntu kernel: [    4.048000] NFORCE-MCP51: not 100%% native mode: will probe irqs later
Jun 12 11:53:20 Kubuntu kernel: [    4.048000] NFORCE-MCP51: 0000:00:0d.0 (rev a1) UDMA133 controller
Jun 12 11:53:20 Kubuntu kernel: [    4.048000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:pio
Jun 12 11:53:20 Kubuntu kernel: [    4.048000] Probing IDE interface ide1...
Jun 12 11:53:20 Kubuntu kernel: [    4.048000] SCSI subsystem initialized
Jun 12 11:53:20 Kubuntu kernel: [    4.056000] libata version 2.20 loaded.
Jun 12 11:53:20 Kubuntu kernel: [    4.116000] usb 1-1: new high speed USB device using ehci_hcd and address 2
Jun 12 11:53:20 Kubuntu kernel: [    4.264000] usb 1-1: configuration #1 chosen from 1 choice
Jun 12 11:53:20 Kubuntu kernel: [    4.752000] usb 2-2: new low speed USB device using ohci_hcd and address 2
Jun 12 11:53:20 Kubuntu kernel: [    4.788000] hdc: HL-DT-ST DVDRAM GSA-T20N, ATAPI CD/DVD-ROM drive
Jun 12 11:53:20 Kubuntu kernel: [    4.960000] usb 2-2: configuration #1 chosen from 1 choice
Jun 12 11:53:20 Kubuntu kernel: [    4.972000] usbcore: registered new interface driver hiddev
Jun 12 11:53:20 Kubuntu kernel: [    4.980000] input: MosArt Optical Mouse as /class/input/input2
Jun 12 11:53:20 Kubuntu kernel: [    4.980000] input: USB HID v1.10 Mouse [MosArt Optical Mouse] on usb-0000:00:0b.0-2
Jun 12 11:53:20 Kubuntu kernel: [    4.980000] usbcore: registered new interface driver usbhid
Jun 12 11:53:20 Kubuntu kernel: [    4.980000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Jun 12 11:53:20 Kubuntu kernel: [    5.128000] ide1 at 0x170-0x177,0x376 on irq 15
Jun 12 11:53:20 Kubuntu kernel: [    5.132000] ACPI: PCI Interrupt 0000:05:04.4[A] -> Link [LNKC] -> GSI 17 (level, low) -> IRQ 16
Jun 12 11:53:20 Kubuntu kernel: [    5.184000] sata_nv 0000:00:0e.0: version 3.3
Jun 12 11:53:20 Kubuntu kernel: [    5.184000] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 22
Jun 12 11:53:20 Kubuntu kernel: [    5.184000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LSA0] -> GSI 22 (level, low) -> IRQ 19
Jun 12 11:53:20 Kubuntu kernel: [    5.184000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
Jun 12 11:53:20 Kubuntu kernel: [    5.184000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[fdeff000-fdeff7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
Jun 12 11:53:20 Kubuntu kernel: [    5.184000] ata1: SATA max UDMA/133 cmd 0x0001e800 ctl 0x0001e482 bmdma 0x0001e000 irq 19
Jun 12 11:53:20 Kubuntu kernel: [    5.184000] ata2: SATA max UDMA/133 cmd 0x0001e400 ctl 0x0001e082 bmdma 0x0001e008 irq 19
Jun 12 11:53:20 Kubuntu kernel: [    5.184000] scsi0 : sata_nv
Jun 12 11:53:20 Kubuntu kernel: [    5.656000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun 12 11:53:20 Kubuntu kernel: [    6.056000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
Jun 12 11:53:20 Kubuntu kernel: [    6.056000] ata1.00: ATA-7: WDC WD1200BEVS-22LAT0, 01.06M01, max UDMA/133
Jun 12 11:53:20 Kubuntu kernel: [    6.056000] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/1)
Jun 12 11:53:20 Kubuntu kernel: [    6.068000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
Jun 12 11:53:20 Kubuntu kernel: [    6.068000] ata1.00: configured for UDMA/133
Jun 12 11:53:20 Kubuntu kernel: [    6.068000] scsi1 : sata_nv
Jun 12 11:53:20 Kubuntu kernel: [    6.380000] ata2: SATA link down (SStatus 0 SControl 300)
Jun 12 11:53:20 Kubuntu kernel: [    6.384000] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1200BEVS-2 01.0 PQ: 0 ANSI: 5
Jun 12 11:53:20 Kubuntu kernel: [    6.392000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
Jun 12 11:53:20 Kubuntu kernel: [    6.392000] sda: Write Protect is off
Jun 12 11:53:20 Kubuntu kernel: [    6.392000] sda: Mode Sense: 00 3a 00 00
Jun 12 11:53:20 Kubuntu kernel: [    6.392000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 12 11:53:20 Kubuntu kernel: [    6.392000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
Jun 12 11:53:20 Kubuntu kernel: [    6.392000] sda: Write Protect is off
Jun 12 11:53:20 Kubuntu kernel: [    6.392000] sda: Mode Sense: 00 3a 00 00
Jun 12 11:53:20 Kubuntu kernel: [    6.392000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 12 11:53:20 Kubuntu kernel: [    6.392000]  sda:<6>hdc: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
Jun 12 11:53:20 Kubuntu kernel: [    6.404000] Uniform CD-ROM driver Revision: 3.20
Jun 12 11:53:20 Kubuntu kernel: [    6.436000]  sda1 sda2 sda3 <<7>ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00dc100022321b01]
Jun 12 11:53:20 Kubuntu kernel: [    6.468000]  sda5 >
Jun 12 11:53:20 Kubuntu kernel: [    6.468000] sd 0:0:0:0: Attached scsi disk sda
Jun 12 11:53:20 Kubuntu kernel: [    6.472000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jun 12 11:53:20 Kubuntu kernel: [    6.784000] Attempting manual resume
Jun 12 11:53:20 Kubuntu kernel: [    6.784000] swsusp: Resume From Partition 8:5
Jun 12 11:53:20 Kubuntu kernel: [    6.784000] PM: Checking swsusp image.
Jun 12 11:53:20 Kubuntu kernel: [    6.784000] PM: Resume from disk failed.
Jun 12 11:53:20 Kubuntu kernel: [    6.820000] kjournald starting.  Commit interval 5 seconds
Jun 12 11:53:20 Kubuntu kernel: [    6.820000] EXT3-fs: mounted filesystem with ordered data mode.
Jun 12 11:53:20 Kubuntu kernel: [   18.888000] r8169: eth0: link up
Jun 12 11:53:20 Kubuntu kernel: [   18.888000] r8169: eth0: link up
Jun 12 11:53:20 Kubuntu kernel: [   19.532000] NET: Registered protocol family 10
Jun 12 11:53:20 Kubuntu kernel: [   19.532000] lo: Disabled Privacy Extensions
Jun 12 11:53:20 Kubuntu kernel: [   20.088000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun 12 11:53:20 Kubuntu kernel: [   20.132000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jun 12 11:53:20 Kubuntu kernel: [   20.724000] sdhci: Secure Digital Host Controller Interface driver
Jun 12 11:53:20 Kubuntu kernel: [   20.724000] sdhci: Copyright(c) Pierre Ossman
Jun 12 11:53:20 Kubuntu kernel: [   20.724000] sdhci: SDHCI controller found at 0000:05:04.2 [1217:7120] (rev 1)
Jun 12 11:53:20 Kubuntu kernel: [   20.724000] ACPI: PCI Interrupt 0000:05:04.2[A] -> Link [LNKC] -> GSI 17 (level, low) -> IRQ 16
Jun 12 11:53:20 Kubuntu kernel: [   20.724000] sdhci:slot0: Unknown controller version (16). You may experience problems.
Jun 12 11:53:20 Kubuntu kernel: [   20.724000] mmc0: SDHCI at 0xfdefe400 irq 16 PIO
Jun 12 11:53:20 Kubuntu kernel: [   20.732000] Yenta: CardBus bridge found at 0000:05:04.0 [1462:3fdf]
Jun 12 11:53:20 Kubuntu kernel: [   20.732000] Yenta O2: res at 0x94/0xD4: 00/ea
Jun 12 11:53:20 Kubuntu kernel: [   20.732000] Yenta O2: enabling read prefetch/write burst
Jun 12 11:53:20 Kubuntu kernel: [   20.744000] Linux agpgart interface v0.102 (c) Dave Jones
Jun 12 11:53:20 Kubuntu kernel: [   20.780000] input: PC Speaker as /class/input/input3
Jun 12 11:53:20 Kubuntu kernel: [   20.864000] Yenta: ISA IRQ mask 0x0cb8, PCI irq 16
Jun 12 11:53:20 Kubuntu kernel: [   20.864000] Socket status: 30000006
Jun 12 11:53:20 Kubuntu kernel: [   20.864000] Yenta: Raising subordinate bus# of parent bus (#05) from #06 to #09
Jun 12 11:53:20 Kubuntu kernel: [   20.864000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xdfff
Jun 12 11:53:20 Kubuntu kernel: [   20.864000] cs: IO port probe 0xd000-0xdfff: clean.
Jun 12 11:53:20 Kubuntu kernel: [   20.864000] pcmcia: parent PCI bridge Memory window: 0xfd600000 - 0xfdefffff
Jun 12 11:53:20 Kubuntu kernel: [   20.864000] pcmcia: parent PCI bridge Memory window: 0xddf00000 - 0xdfefffff
Jun 12 11:53:20 Kubuntu kernel: [   20.868000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x5000
Jun 12 11:53:20 Kubuntu kernel: [   20.868000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x6000
Jun 12 11:53:20 Kubuntu kernel: [   20.872000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 16
Jun 12 11:53:20 Kubuntu kernel: [   20.872000] ACPI: PCI Interrupt 0000:05:09.0[A] -> Link [LNKA] -> GSI 16 (level, low) -> IRQ 20
Jun 12 11:53:20 Kubuntu kernel: [   20.872000] rt2500 1.1.0 BETA4 2006/06/18 http://rt2x00.serialmonkey.com
Jun 12 11:53:20 Kubuntu kernel: [   20.916000] rt2500 EEPROM:  1  2  3  4  5  6  7  8  9 10 11 12 13 14  Channel
Jun 12 11:53:20 Kubuntu kernel: [   20.916000] rt2500 EEPROM:  6  6  6  6  6  6  6  6  6  6  6  6  7  7  dBm Maximum
Jun 12 11:53:20 Kubuntu kernel: [   21.376000] input: ImPS/2 Logitech Wheel Mouse as /class/input/input4
Jun 12 11:53:20 Kubuntu kernel: [   21.432000] cs: IO port probe 0x100-0x3af: clean.
Jun 12 11:53:20 Kubuntu kernel: [   21.432000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Jun 12 11:53:20 Kubuntu kernel: [   21.436000] cs: IO port probe 0x820-0x8ff: clean.
Jun 12 11:53:20 Kubuntu kernel: [   21.436000] cs: IO port probe 0xc00-0xcf7: clean.
Jun 12 11:53:20 Kubuntu kernel: [   21.436000] cs: IO port probe 0xa00-0xaff: clean.
Jun 12 11:53:20 Kubuntu kernel: [   21.676000] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 23
Jun 12 11:53:20 Kubuntu kernel: [   21.676000] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 23 (level, low) -> IRQ 21
Jun 12 11:53:20 Kubuntu kernel: [   21.676000] PCI: Setting latency timer of device 0000:00:10.1 to 64
Jun 12 11:53:20 Kubuntu kernel: [   22.168000] NET: Registered protocol family 17
Jun 12 11:53:20 Kubuntu kernel: [   22.400000] fuse init (API version 7.8)
Jun 12 11:53:20 Kubuntu kernel: [   22.480000] lp: driver loaded but no devices found
Jun 12 11:53:20 Kubuntu kernel: [   22.548000] Adding 1004020k swap on /dev/disk/by-uuid/0ac3f9ac-a8fd-4a72-bc4d-c0dd4f5299c7.  Priority:-1 extents:1 across:1004020k
Jun 12 11:53:20 Kubuntu kernel: [   22.732000] EXT3 FS on sda2, internal journal
Jun 12 11:53:20 Kubuntu kernel: [   28.236000] PPP generic driver version 2.4.2
Jun 12 11:53:20 Kubuntu kernel: [   28.792000] No dock devices found.
Jun 12 11:53:20 Kubuntu kernel: [   28.804000] Using specific hotkey driver
Jun 12 11:53:20 Kubuntu kernel: [   28.848000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Jun 12 11:53:20 Kubuntu kernel: [   28.872000] ACPI: Battery Slot [BAT1] (battery present)
Jun 12 11:53:20 Kubuntu kernel: [   28.972000] ibm_acpi: ec object not found
Jun 12 11:53:20 Kubuntu kernel: [   29.036000] ACPI: AC Adapter [ADP1] (on-line)
Jun 12 11:53:20 Kubuntu kernel: [   29.056000] input: Power Button (FF) as /class/input/input5
Jun 12 11:53:20 Kubuntu kernel: [   29.056000] ACPI: Power Button (FF) [PWRF]
Jun 12 11:53:20 Kubuntu kernel: [   29.060000] input: Lid Switch as /class/input/input6
Jun 12 11:53:20 Kubuntu kernel: [   29.060000] ACPI: Lid Switch [LID0]
Jun 12 11:53:20 Kubuntu kernel: [   29.084000] input: Sleep Button (CM) as /class/input/input7
Jun 12 11:53:20 Kubuntu kernel: [   29.084000] ACPI: Sleep Button (CM) [SLPB]
Jun 12 11:53:20 Kubuntu kernel: [   29.100000] input: Power Button (CM) as /class/input/input8
Jun 12 11:53:20 Kubuntu kernel: [   29.100000] ACPI: Power Button (CM) [PWRB]
Jun 12 11:53:20 Kubuntu kernel: [   29.164000] pcc_acpi: loading...
Jun 12 11:53:20 Kubuntu kernel: [   29.404000] powernow-k8: Found 2 AMD Turion(tm) 64 X2 Mobile Technology TL-52 processors (version 2.00.00)
Jun 12 11:53:20 Kubuntu kernel: [   29.404000] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x12
Jun 12 11:53:20 Kubuntu kernel: [   29.404000] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x1e
Jun 12 11:53:20 Kubuntu kernel: [   29.588000] eth0: no IPv6 routers present
Jun 12 11:53:21 Kubuntu kernel: [   30.976000] ra0: no IPv6 routers present
Jun 12 11:53:24 Kubuntu dhcdbd: Started up.
Jun 12 11:53:24 Kubuntu NetworkManager: <information>^Istarting... 
Jun 12 11:53:24 Kubuntu NetworkManager: <information>^Ira0: Device is fully-supported using driver 'rt2500'. 
Jun 12 11:53:24 Kubuntu NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
Jun 12 11:53:24 Kubuntu avahi-daemon[5121]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Jun 12 11:53:24 Kubuntu avahi-daemon[5121]: Successfully dropped root privileges.
Jun 12 11:53:24 Kubuntu avahi-daemon[5121]: avahi-daemon 0.6.17 starting up.
Jun 12 11:53:24 Kubuntu avahi-daemon[5121]: Successfully called chroot().
Jun 12 11:53:24 Kubuntu avahi-daemon[5121]: Successfully dropped remaining capabilities.
Jun 12 11:53:24 Kubuntu avahi-daemon[5121]: No service found in /etc/avahi/services.
Jun 12 11:53:24 Kubuntu avahi-daemon[5121]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.0.0.1.
Jun 12 11:53:24 Kubuntu avahi-daemon[5121]: New relevant interface eth0.IPv4 for mDNS.
Jun 12 11:53:24 Kubuntu avahi-daemon[5121]: Network interface enumeration completed.
Jun 12 11:53:24 Kubuntu avahi-daemon[5121]: Registering new address record for fe80::219:dbff:fe00:bf13 on ra0.*.
Jun 12 11:53:24 Kubuntu avahi-daemon[5121]: Registering new address record for fe80::219:dbff:fe39:b916 on eth0.*.
Jun 12 11:53:24 Kubuntu avahi-daemon[5121]: Registering new address record for 10.0.0.1 on eth0.IPv4.
Jun 12 11:53:24 Kubuntu avahi-daemon[5121]: Server startup complete. Host name is Kubuntu.local. Local service cookie is 3266307320.
Jun 12 11:53:24 Kubuntu avahi-daemon[5121]: Registering HINFO record with values 'I686'/'LINUX'.
Jun 12 11:53:24 Kubuntu NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
Jun 12 11:53:24 Kubuntu NetworkManager: <information>^INow managing wireless (802.11) device 'ra0'. 
Jun 12 11:53:24 Kubuntu NetworkManager: <information>^IDeactivating device ra0. 
Jun 12 11:53:24 Kubuntu avahi-daemon[5121]: Withdrawing address record for fe80::219:dbff:fe00:bf13 on ra0.
Jun 12 11:53:24 Kubuntu NetworkManager: <information>^IFound dial up configuration for dsl-provider via Modem: dsl-provider 
Jun 12 11:53:25 Kubuntu kernel: [   34.508000] ppdev: user-space parallel port driver
Jun 12 11:53:25 Kubuntu hpiod: 1.7.3 accepting connections at 2208... 
Jun 12 11:53:26 Kubuntu kernel: [   35.476000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Jun 12 11:53:26 Kubuntu kernel: [   35.476000] apm: disabled - APM is not SMP safe.
Jun 12 11:53:26 Kubuntu nas[5260]: Network Audio System Release 1.9 
Jun 12 11:53:26 Kubuntu nas[5261]: Init: Input open(/dev/dsp1) failed: No such file or directory, using output device 
Jun 12 11:53:26 Kubuntu nas[5261]: initMixer: could not open input mixer device /dev/mixer1: No such file or directory 
Jun 12 11:53:26 Kubuntu nas[5261]: initMixer: using output mixer /dev/mixer for input 
Jun 12 11:53:27 Kubuntu hcid[5323]: Bluetooth HCI daemon
Jun 12 11:53:27 Kubuntu kernel: [   36.340000] Bluetooth: Core ver 2.11
Jun 12 11:53:27 Kubuntu kernel: [   36.340000] NET: Registered protocol family 31
Jun 12 11:53:27 Kubuntu kernel: [   36.340000] Bluetooth: HCI device and connection manager initialized
Jun 12 11:53:27 Kubuntu kernel: [   36.340000] Bluetooth: HCI socket layer initialized
Jun 12 11:53:27 Kubuntu hcid[5323]: Starting SDP server
Jun 12 11:53:27 Kubuntu kernel: [   36.364000] Bluetooth: L2CAP ver 2.8
Jun 12 11:53:27 Kubuntu kernel: [   36.364000] Bluetooth: L2CAP socket layer initialized
Jun 12 11:53:27 Kubuntu NetworkManager: <debug info>^I[1213264407.071763] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Jun 12 11:53:27 Kubuntu kernel: [   36.412000] Bluetooth: RFCOMM socket layer initialized
Jun 12 11:53:27 Kubuntu kernel: [   36.412000] Bluetooth: RFCOMM TTY layer initialized
Jun 12 11:53:27 Kubuntu kernel: [   36.412000] Bluetooth: RFCOMM ver 1.8
Jun 12 11:53:27 Kubuntu anacron[5365]: Anacron 2.3 started on 2008-06-12
Jun 12 11:53:27 Kubuntu anacron[5365]: Will run job `cron.daily' in 5 min.
Jun 12 11:53:27 Kubuntu anacron[5365]: Will run job `cron.monthly' in 15 min.
Jun 12 11:53:27 Kubuntu anacron[5365]: Jobs will be executed sequentially
Jun 12 11:53:27 Kubuntu /usr/sbin/cron[5392]: (CRON) INFO (pidfile fd = 3)
Jun 12 11:53:27 Kubuntu /usr/sbin/cron[5393]: (CRON) STARTUP (fork ok)
Jun 12 11:53:27 Kubuntu /usr/sbin/cron[5393]: (CRON) INFO (Running @reboot jobs)
Jun 12 11:53:29 Kubuntu kdm: :0[5488]: IO Error in XOpenDisplay
Jun 12 11:53:29 Kubuntu kdm[5454]: X server for display :0 terminated unexpectedly
Jun 12 11:53:29 Kubuntu kdm[5454]: Display :0 cannot be opened
Jun 12 11:53:29 Kubuntu kdm[5454]: Unable to fire up local display :0; disabling.
Jun 12 11:53:31 Kubuntu dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 5
Jun 12 11:53:36 Kubuntu dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
Jun 12 11:53:44 Kubuntu dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 14
Jun 12 11:53:50 Kubuntu ntpdate[3069]: can't find host ntp.ubuntu.com 
Jun 12 11:53:50 Kubuntu ntpdate[3069]: no servers can be used, exiting
Jun 12 11:53:53 Kubuntu pppd[4393]: Timeout waiting for PADO packets
Jun 12 11:53:53 Kubuntu pppd[4393]: Unable to complete PPPoE Discovery
Jun 12 11:53:58 Kubuntu dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
Jun 12 11:53:58 Kubuntu ntpdate[4405]: can't find host ntp.ubuntu.com 
Jun 12 11:53:58 Kubuntu ntpdate[4405]: no servers can be used, exiting
Jun 12 11:54:02 Kubuntu dhclient: No DHCPOFFERS received.
Jun 12 11:54:02 Kubuntu dhclient: Trying recorded lease 192.168.0.230
Jun 12 11:54:02 Kubuntu avahi-daemon[5121]: Joining mDNS multicast group on interface ra0.IPv4 with address 192.168.0.230.
Jun 12 11:54:02 Kubuntu avahi-daemon[5121]: New relevant interface ra0.IPv4 for mDNS.
Jun 12 11:54:02 Kubuntu avahi-daemon[5121]: Registering new address record for 192.168.0.230 on ra0.IPv4.
Jun 12 11:54:05 Kubuntu avahi-daemon[5121]: Withdrawing address record for 192.168.0.230 on ra0.
Jun 12 11:54:05 Kubuntu avahi-daemon[5121]: Leaving mDNS multicast group on interface ra0.IPv4 with address 192.168.0.230.
Jun 12 11:54:05 Kubuntu avahi-daemon[5121]: Interface ra0.IPv4 no longer relevant for mDNS.
Jun 12 11:54:05 Kubuntu avahi-autoipd(ra0)[5509]: Found user 'avahi-autoipd' (UID 103) and group 'avahi-autoipd' (GID 109).
Jun 12 11:54:05 Kubuntu avahi-autoipd(ra0)[5509]: Successfully called chroot().
Jun 12 11:54:05 Kubuntu avahi-autoipd(ra0)[5509]: Successfully dropped root privileges.
Jun 12 11:54:05 Kubuntu avahi-autoipd(ra0)[5509]: fopen() failed: Permission denied
Jun 12 11:54:05 Kubuntu avahi-autoipd(ra0)[5509]: Starting with address 169.254.5.43
Jun 12 11:54:10 Kubuntu avahi-autoipd(ra0)[5509]: Callout BIND, address 169.254.5.43 on interface ra0
Jun 12 11:54:10 Kubuntu avahi-daemon[5121]: Joining mDNS multicast group on interface ra0.IPv4 with address 169.254.5.43.
Jun 12 11:54:10 Kubuntu avahi-daemon[5121]: New relevant interface ra0.IPv4 for mDNS.
Jun 12 11:54:10 Kubuntu avahi-daemon[5121]: Registering new address record for 169.254.5.43 on ra0.IPv4.
Jun 12 11:54:14 Kubuntu avahi-autoipd(ra0)[5509]: Successfully claimed IP address 169.254.5.43
Jun 12 11:54:14 Kubuntu avahi-autoipd(ra0)[5509]: fopen() failed: Permission denied
Jun 12 11:54:14 Kubuntu dhclient: No working leases in persistent database - sleeping.
Jun 12 11:54:24 Kubuntu pppd[4393]: PPP session is 53338
Jun 12 11:54:24 Kubuntu kernel: [   93.452000] NET: Registered protocol family 24
Jun 12 11:54:24 Kubuntu pppd[4393]: Using interface ppp0
Jun 12 11:54:24 Kubuntu pppd[4393]: Connect: ppp0 <--> eth0
Jun 12 11:54:26 Kubuntu pppd[4393]: PAP authentication succeeded
Jun 12 11:54:26 Kubuntu pppd[4393]: peer from calling number 00:04:4E:22:18:19 authorized
Jun 12 11:54:26 Kubuntu pppd[4393]: replacing old default route to eth0 [10.0.0.1]
Jun 12 11:54:26 Kubuntu pppd[4393]: Cannot determine ethernet address for proxy ARP
Jun 12 11:54:26 Kubuntu pppd[4393]: local  IP address 85.232.221.166
Jun 12 11:54:26 Kubuntu pppd[4393]: remote IP address 192.168.180.1
Jun 12 11:54:26 Kubuntu pppd[4393]: primary   DNS address 194.158.37.196
Jun 12 11:54:26 Kubuntu pppd[4393]: secondary DNS address 194.158.37.211
Jun 12 11:54:26 Kubuntu kernel: [   96.204000] ip_tables: (C) 2000-2006 Netfilter Core Team
Jun 12 11:54:36 Kubuntu ntpdate[5547]: step time server 91.189.94.4 offset 0.842484 sec
Jun 12 11:55:27 Kubuntu init: tty4 main process (4538) killed by TERM signal
Jun 12 11:55:27 Kubuntu init: tty5 main process (4539) killed by TERM signal
Jun 12 11:55:27 Kubuntu init: tty2 main process (4542) killed by TERM signal
Jun 12 11:55:27 Kubuntu init: tty3 main process (4544) killed by TERM signal
Jun 12 11:55:27 Kubuntu init: tty6 main process (4546) killed by TERM signal
Jun 12 11:55:27 Kubuntu init: tty1 main process (4545) killed by TERM signal
Jun 12 11:55:34 Kubuntu exiting on signal 15
```

Kubuntu exiting on signal 15?

thanks 
adrian

---

### Post by cmnorton on 2008-06-12
I have seen this error in a lot of places relating to power, heat, or packaging issues. I don't have a clue why you are getting this problem. I went back to re-read your original post. Given everything was running fine and you did not go through a release update, this sounds like a hardware problem.

Here are two links I found from Googling "Kubuntu exiting on signal 15". There is a launchpad bug regarding this error, 8.04 and CPU temperature, but you're on 7.04.

[http://ubuntuforums.org/showthread.php?t=438958](http://ubuntuforums.org/showthread.php?t=438958)
[http://ph.ubuntuforums.com/showthread.php?p=4838241](http://ph.ubuntuforums.com/showthread.php?p=4838241)

---

