---
title: "hard drive changed from hda to sde"
date: 2007-06-01
forum: General Help
---

### Post by Jhereg on 2007-06-01
I have been using KUbuntu for quite awhile now and really like it. However, this last upgrade, 7.04, has caused a few problems for me.

My computer has a single IDE hard drive, which always in the past (and on other distributions) has shown up in Linux as "/dev/hda". With the newest update, this has somehow gotten changed to "/dev/sde" I HAVE NOT changed anything in terms of hardware, and I do not remember installing any new drivers. This is a mystery to me especially, because it was my understanding that IDE was always assigned to "/dev/hd*" and the other assignments were reserved for other hardware (which makes sense from a "and what did this hardware get assigned as?" standpoint) Now, the computer still runs, so I wouldn't have bothered posting except that some programs, especially Firefox and Amarok, now seem to freeze randomly. I don't even know if the problems are related, but they showed up at the same time. Besides that, my computer now hangs when booting. It does still boot, but booting takes about twice as long as it used to. dmesg seems to have the answer to why it takes so long, but i don't know how to fix it.

the problem seems to begin where it says [33.999884]
```

[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003f542000 end: 000000003f642000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003f642000 size: 00000000000a6000 end: 000000003f6e8000 type: 4
[    0.000000] copy_e820_map() start: 000000003f6e8000 size: 0000000000018000 end: 000000003f700000 type: 3
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f642000 (usable)
[    0.000000]  BIOS-e820: 000000003f642000 - 000000003f6e8000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f6e8000 - 000000003f700000 (ACPI data)
[    0.000000] 118MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fe650
[    0.000000] Entering add_active_range(0, 0, 259650) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   259650
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   259650
[    0.000000] On node 0 totalpages: 259650
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 236 pages used for memmap
[    0.000000]   HighMem zone: 30038 pages, LIFO batch:7
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 GATEWA                                ) @ 0x000fe020
[    0.000000] ACPI: RSDT (v001 GATEWA 04DT040  0x00000330 MSFT 0x01000013) @ 0x3f6fde48
[    0.000000] ACPI: FADT (v001 GATEWA 04DT040  0x00000330 MSFT 0x01000013) @ 0x3f6fcf10
[    0.000000] ACPI: MADT (v001 GATEWA 04DT040  0x00000330 MSFT 0x01000013) @ 0x3f6fce10
[    0.000000] ACPI: WDDT (v001 GATEWA 04DT040  0x00000330 MSFT 0x01000013) @ 0x3f6f7f90
[    0.000000] ACPI: MCFG (v001 GATEWA 04DT040  0x00000330 MSFT 0x01000013) @ 0x3f6f7f10
[    0.000000] ACPI: SSDT (v001 GATEWA    CpuPm 0x00000330 MSFT 0x01000013) @ 0x3f6f6d90
[    0.000000] ACPI: DSDT (v001 GATEWA 04DT040  0x00000330 MSFT 0x01000013) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3f700000:c0900000)
[    0.000000] Detected 2933.662 MHz processor.
[   23.493810] Built 1 zonelists.  Total pages: 257622
[   23.493814] Kernel command line: root=UUID=2c83a931-a530-4cab-86b3-f2522a19902c ro quiet splash
[   23.493970] mapped APIC to ffffd000 (fee00000)
[   23.493973] mapped IOAPIC to ffffc000 (fec00000)
[   23.493976] Enabling fast FPU save and restore... done.
[   23.493979] Enabling unmasked SIMD FPU exception support... done.
[   23.493988] Initializing CPU#0
[   23.494053] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   23.496206] Console: colour VGA+ 80x25
[   23.496554] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   23.497039] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   23.517529] Memory: 1018404k/1038600k available (1992k kernel code, 19368k reserved, 893k data, 328k init, 121096k highmem)
[   23.517540] virtual kernel memory layout:
[   23.517541]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   23.517542]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   23.517543]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   23.517544]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   23.517545]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   23.517547]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   23.517548]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   23.517551] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   23.594038] Calibrating delay using timer specific routine.. 5872.23 BogoMIPS (lpj=11744469)
[   23.594084] Security Framework v1.0.0 initialized
[   23.594092] SELinux:  Disabled at boot.
[   23.594107] Mount-cache hash table entries: 512
[   23.594253] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000651d 00000000 00000000
[   23.594263] monitor/mwait feature present.
[   23.594265] using mwait in idle threads.
[   23.594272] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   23.594274] CPU: L2 cache: 256K
[   23.594278] CPU: Hyper-Threading is disabled
[   23.594280] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003180 0000651d 00000000 00000000
[   23.594291] Compat vDSO mapped to ffffe000.
[   23.594295] Remapping vsyscall page to ffffe000
[   23.594312] Checking 'hlt' instruction... OK.
[   23.610127] SMP alternatives: switching to UP code
[   23.610310] Freeing SMP alternatives: 11k freed
[   23.610524] Early unpacking initramfs... done
[   23.892790] ACPI: Core revision 20060707
[   23.894342] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   23.896184] CPU0: Intel(R) Celeron(R) CPU 2.93GHz stepping 09
[   23.896224] Total of 1 processors activated (5872.23 BogoMIPS).
[   23.896380] ENABLING IO-APIC IRQs
[   23.896558] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   24.041990] Brought up 1 CPUs
[   24.042251] Booting paravirtualized kernel on bare hardware
[   24.042341] Time: 12:07:38  Date: 05/01/107
[   24.042368] NET: Registered protocol family 16
[   24.042473] EISA bus registered
[   24.042479] ACPI: bus type pci registered
[   24.045371] PCI: Using configuration type 1
[   24.045373] Setting up standard PCI resources
[   24.056447] ACPI: Interpreter enabled
[   24.056453] ACPI: Using IOAPIC for interrupt routing
[   24.056942] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   24.056954] PCI: Probing PCI hardware (bus 00)
[   24.056974] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   24.058523] Boot video device is 0000:00:02.0
[   24.059047] PCI quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[   24.059051] PCI quirk: region 0500-053f claimed by ICH6 GPIO
[   24.059845] PCI: Firmware left 0000:05:08.0 e100 interrupts enabled, disabling
[   24.059928] PCI: Transparent bridge - 0000:00:1e.0
[   24.060004] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   24.063201] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[   24.064179] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[   24.064440] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12)
[   24.064693] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[   24.064950] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 12)
[   24.065222] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11 12)
[   24.065476] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12)
[   24.065734] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 *11 12)
[   24.066043] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 *9 10 11 12)
[   24.067562] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[   24.067832] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[   24.068098] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[   24.068368] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[   24.069542] Linux Plug and Play Support v0.97 (c) Adam Belay
[   24.069555] pnp: PnP ACPI init
[   24.073185] pnp: PnP ACPI: found 13 devices
[   24.073191] PnPBIOS: Disabled by ACPI PNP
[   24.073254] PCI: Using ACPI for IRQ routing
[   24.073260] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   24.073364] NET: Registered protocol family 8
[   24.073366] NET: Registered protocol family 20
[   24.073494] pnp: 00:06: ioport range 0x500-0x53f has been reserved
[   24.073498] pnp: 00:06: ioport range 0x400-0x47f could not be reserved
[   24.073501] pnp: 00:06: ioport range 0x680-0x6ff has been reserved
[   24.073914] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[   24.073920] PCI: Bridge: 0000:00:1c.0
[   24.073922]   IO window: disabled.
[   24.073928]   MEM window: 50200000-502fffff
[   24.073974]   PREFETCH window: disabled.
[   24.073980] PCI: Bridge: 0000:00:1c.1
[   24.073981]   IO window: disabled.
[   24.073986]   MEM window: 50300000-503fffff
[   24.073990]   PREFETCH window: disabled.
[   24.073995] PCI: Bridge: 0000:00:1c.2
[   24.073996]   IO window: disabled.
[   24.074001]   MEM window: 50400000-504fffff
[   24.074005]   PREFETCH window: disabled.
[   24.074010] PCI: Bridge: 0000:00:1c.3
[   24.074011]   IO window: disabled.
[   24.074017]   MEM window: 50500000-505fffff
[   24.074020]   PREFETCH window: disabled.
[   24.074026] PCI: Bridge: 0000:00:1e.0
[   24.074029]   IO window: 1000-1fff
[   24.074034]   MEM window: 50000000-500fffff
[   24.074038]   PREFETCH window: disabled.
[   24.074069] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[   24.074077] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   24.074096] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[   24.074103] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   24.074123] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   24.074130] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   24.074152] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   24.074158] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   24.074170] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   24.074201] NET: Registered protocol family 2
[   24.106006] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   24.106162] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   24.106816] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   24.107148] TCP: Hash tables configured (established 131072 bind 65536)
[   24.107152] TCP reno registered
[   24.118093] checking if image is initramfs... it is
[   24.663336] Freeing initrd memory: 6748k freed
[   24.663867] audit: initializing netlink socket (disabled)
[   24.663881] audit(1180699658.248:1): initialized
[   24.663960] highmem bounce pool size: 64 pages
[   24.664030] VFS: Disk quotas dquot_6.5.1
[   24.664052] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   24.664101] io scheduler noop registered
[   24.664104] io scheduler anticipatory registered
[   24.664106] io scheduler deadline registered
[   24.664116] io scheduler cfq registered (default)
[   24.664481] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   24.664529] assign_interrupt_mode Found MSI capability
[   24.664532] Allocate Port Service[0000:00:1c.0:pcie00]
[   24.664580] Allocate Port Service[0000:00:1c.0:pcie02]
[   24.664699] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   24.664745] assign_interrupt_mode Found MSI capability
[   24.664747] Allocate Port Service[0000:00:1c.1:pcie00]
[   24.664789] Allocate Port Service[0000:00:1c.1:pcie02]
[   24.664904] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   24.664950] assign_interrupt_mode Found MSI capability
[   24.664952] Allocate Port Service[0000:00:1c.2:pcie00]
[   24.664995] Allocate Port Service[0000:00:1c.2:pcie02]
[   24.665111] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   24.665157] assign_interrupt_mode Found MSI capability
[   24.665160] Allocate Port Service[0000:00:1c.3:pcie00]
[   24.665207] Allocate Port Service[0000:00:1c.3:pcie02]
[   24.665416] isapnp: Scanning for PnP cards...
[   25.017340] isapnp: No Plug & Play device found
[   25.086477] Real Time Clock Driver v1.12ac
[   25.086534] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   25.086677] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.088133] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.088539] mice: PS/2 mouse device common for all mice
[   25.089236] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   25.089424] input: Macintosh mouse button emulation as /class/input/input0
[   25.089473] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   25.089477] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   25.089718] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   25.092729] serio: i8042 KBD port at 0x60,0x64 irq 1
[   25.092738] serio: i8042 AUX port at 0x60,0x64 irq 12
[   25.092915] EISA: Probing bus 0 at eisa.0
[   25.092925] Cannot allocate resource for EISA slot 1
[   25.092927] Cannot allocate resource for EISA slot 2
[   25.092947] EISA: Detected 0 cards.
[   25.123026] TCP cubic registered
[   25.123034] NET: Registered protocol family 1
[   25.123058] Using IPI No-Shortcut mode
[   25.123150] ACPI: (supports S0 S1 S3 S4 S5)
[   25.123198]   Magic number: 11:409:126
[   25.123537] Freeing unused kernel memory: 328k freed
[   25.125720] Time: tsc clocksource has been installed.
[   25.147342] input: AT Translated Set 2 keyboard as /class/input/input1
[   26.390329] Capability LSM initialized
[   26.439960] ACPI: Processor [CPU0] (supports 8 throttling states)
[   26.439976] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   27.061257] usbcore: registered new interface driver usbfs
[   27.061283] usbcore: registered new interface driver hub
[   27.061354] usbcore: registered new device driver usb
[   27.062314] USB Universal Host Controller Interface driver v3.0
[   27.062367] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[   27.062379] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   27.062383] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   27.062494] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   27.062527] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00002080
[   27.062645] usb usb1: configuration #1 chosen from 1 choice
[   27.062673] hub 1-0:1.0: USB hub found
[   27.062683] hub 1-0:1.0: 2 ports detected
[   27.124913] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   27.144310] ieee1394: Initialized config rom entry `ip1394'
[   27.154248] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI
[   27.154252] e100: Copyright(c) 1999-2006 Intel Corporation
[   27.165449] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   27.165461] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   27.165466] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   27.165499] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   27.165530] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00002060
[   27.165629] usb usb2: configuration #1 chosen from 1 choice
[   27.165660] hub 2-0:1.0: USB hub found
[   27.165668] hub 2-0:1.0: 2 ports detected
[   27.269455] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   27.269468] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   27.269473] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   27.269505] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   27.269536] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00002040
[   27.269633] usb usb3: configuration #1 chosen from 1 choice
[   27.269662] hub 3-0:1.0: USB hub found
[   27.269671] hub 3-0:1.0: 2 ports detected
[   27.330358] FDC 0 is a post-1991 82077
[   27.373392] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[   27.373404] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   27.373408] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   27.373436] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   27.373467] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00002020
[   27.373578] usb usb4: configuration #1 chosen from 1 choice
[   27.373607] hub 4-0:1.0: USB hub found
[   27.373616] hub 4-0:1.0: 2 ports detected
[   27.478624] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[   27.478641] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   27.478645] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   27.478685] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   27.478719] ehci_hcd 0000:00:1d.7: debug port 1
[   27.478726] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   27.478734] ehci_hcd 0000:00:1d.7: irq 20, io mem 0x501c4000
[   27.482634] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   27.482725] usb usb5: configuration #1 chosen from 1 choice
[   27.482757] hub 5-0:1.0: USB hub found
[   27.482766] hub 5-0:1.0: 8 ports detected
[   27.509257] usb 2-2: new full speed USB device using uhci_hcd and address 2
[   27.585417] 8139cp 0000:05:00.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   27.585421] 8139cp 0000:05:00.0: Try the "8139too" driver instead.
[   27.587151] 8139too Fast Ethernet driver 0.9.28
[   27.587213] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 21 (level, low) -> IRQ 21
[   27.587587] eth0: RealTek RTL8139 at 0xf8846000, 00:40:f4:74:0b:2e, IRQ 21
[   27.587590] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   27.588280] ACPI: PCI Interrupt 0000:05:05.0[A] -> GSI 17 (level, low) -> IRQ 16
[   27.657529] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[50011000-500117ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[   27.667851] ACPI: PCI Interrupt 0000:05:08.0[A] -> GSI 20 (level, low) -> IRQ 22
[   27.688291] e100: eth1: e100_probe: addr 0x50010000, irq 22, MAC addr 00:13:20:B9:76:4F
[   27.694999] SCSI subsystem initialized
[   27.701754] libata version 2.20 loaded.
[   27.711638] ata_piix 0000:00:1f.1: version 2.10ac1
[   27.711656] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   27.711678] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   27.711938] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000120b0 irq 14
[   27.711972] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x000120b8 irq 15
[   27.711994] scsi0 : ata_piix
[   28.205453] ata1.00: ata_hpa_resize 1: sectors = 156368016, hpa_sectors = 156368016
[   28.205458] ata1.00: ATA-7: SAMSUNG SP0802N, UR100-04, max UDMA/100
[   28.205461] ata1.00: 156368016 sectors, multi 16: LBA48 
[   28.205464] ata1.01: ATAPI, max UDMA/33
[   28.213475] ata1.00: ata_hpa_resize 1: sectors = 156368016, hpa_sectors = 156368016
[   28.213478] ata1.00: configured for UDMA/100
[   28.357054] usb 2-2: new full speed USB device using uhci_hcd and address 3
[   28.534285] usb 2-2: configuration #1 chosen from 1 choice
[   28.776966] usb 4-1: new full speed USB device using uhci_hcd and address 2
[   28.937080] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0013200000b9764f]
[   28.968160] usb 4-1: configuration #1 chosen from 1 choice
[   28.971340] usbcore: registered new interface driver libusual
[   28.975249] Initializing USB Mass Storage driver...
[   28.975324] scsi2 : SCSI emulation for USB Mass Storage devices
[   28.975384] usb-storage: device found at 3
[   28.975386] usb-storage: waiting for device to settle before scanning
[   28.975405] usbcore: registered new interface driver usb-storage
[   28.975407] USB Mass Storage support registered.
[   33.973772] usb-storage: device scan complete
[   33.976771] scsi 2:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   33.979769] scsi 2:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   33.982767] scsi 2:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   33.985766] scsi 2:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   33.999884] sd 2:0:0:0: Attached scsi removable disk sda
[   34.004830] sd 2:0:0:1: Attached scsi removable disk sdb
[   34.009801] sd 2:0:0:2: Attached scsi removable disk sdc
[   34.014821] sd 2:0:0:3: Attached scsi removable disk sdd
[   34.018999] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   34.019023] sd 2:0:0:1: Attached scsi generic sg1 type 0
[   34.019044] sd 2:0:0:2: Attached scsi generic sg2 type 0
[   34.019069] sd 2:0:0:3: Attached scsi generic sg3 type 0
[   58.210793] ata1.01: qc timeout (cmd 0xef)
[   58.210807] ata1.01: failed to set xfermode (err_mask=0x4)
[   58.210811] ata1: failed to recover some devices, retrying in 5 secs
[   63.741991] ata1.00: ata_hpa_resize 1: sectors = 156368016, hpa_sectors = 156368016
[   63.753961] ata1.00: ata_hpa_resize 1: sectors = 156368016, hpa_sectors = 156368016
[   63.753964] ata1.00: configured for UDMA/100
[   93.751304] ata1.01: qc timeout (cmd 0xef)
[   93.751314] ata1.01: failed to set xfermode (err_mask=0x4)
[   93.751320] ata1.01: limiting speed to UDMA/33:PIO3
[   93.751322] ata1: failed to recover some devices, retrying in 5 secs
[   99.270486] ata1.00: ata_hpa_resize 1: sectors = 156368016, hpa_sectors = 156368016
[   99.282482] ata1.00: ata_hpa_resize 1: sectors = 156368016, hpa_sectors = 156368016
[   99.282486] ata1.00: configured for UDMA/100
[  129.279827] ata1.01: qc timeout (cmd 0xef)
[  129.279836] ata1.01: failed to set xfermode (err_mask=0x4)
[  129.279841] ata1.01: disabled
[  129.279844] ata1: failed to recover some devices, retrying in 5 secs
[  134.282776] ata1.00: failed to set xfermode (err_mask=0x40)
[  134.282782] ata1: failed to recover some devices, retrying in 5 secs
[  139.629998] ata1.00: ata_hpa_resize 1: sectors = 156368016, hpa_sectors = 156368016
[  139.630008] ata1.00: limited to UDMA/33 due to 40-wire cable
[  139.641988] ata1.00: ata_hpa_resize 1: sectors = 156368016, hpa_sectors = 156368016
[  139.641992] ata1.00: configured for UDMA/33
[  139.642002] scsi1 : ata_piix
[  139.642257] ata2: port disabled. ignoring.
[  139.642400] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG SP0802N  UR10 PQ: 0 ANSI: 5
[  139.642778] SCSI device sde: 156368016 512-byte hdwr sectors (80060 MB)
[  139.642793] sde: Write Protect is off
[  139.642796] sde: Mode Sense: 00 3a 00 00
[  139.642815] SCSI device sde: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  139.642874] SCSI device sde: 156368016 512-byte hdwr sectors (80060 MB)
[  139.642886] sde: Write Protect is off
[  139.642889] sde: Mode Sense: 00 3a 00 00
[  139.642907] SCSI device sde: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  139.642911]  sde: sde1 sde2 sde3 < sde5 >
[  139.684535] sd 0:0:0:0: Attached scsi disk sde
[  139.684834] sd 0:0:0:0: Attached scsi generic sg4 type 0
[  139.684957] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[  139.684986] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[  139.685004] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[  139.685048] ata3: SATA max UDMA/133 cmd 0x000120c8 ctl 0x000120ee bmdma 0x000120a0 irq 19
[  139.685077] ata4: SATA max UDMA/133 cmd 0x000120c0 ctl 0x000120ea bmdma 0x000120a8 irq 19
[  139.685088] scsi3 : ata_piix
[  139.851723] ATA: abnormal status 0x7F on port 0x000120cf
[  139.851746] scsi4 : ata_piix
[  140.019687] ATA: abnormal status 0x7F on port 0x000120c7
[  140.294080] kjournald starting.  Commit interval 5 seconds
[  140.294092] EXT3-fs: mounted filesystem with ordered data mode.
[  152.403058] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  154.470524] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  154.496649] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  154.507958] Linux agpgart interface v0.102 (c) Dave Jones
[  154.515394] agpgart: Detected an Intel 915G Chipset.
[  154.515562] agpgart: Detected 7932K stolen memory.
[  154.531883] agpgart: AGP aperture is 256M @ 0x40000000
[  154.623130] iTCO_vendor_support: vendor-support=0
[  154.635888] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[  154.636005] iTCO_wdt: Found a ICH6 or ICH6R TCO device (Version=2, TCOBASE=0x0460)
[  154.636056] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[  154.661878] intel_rng: Firmware space is locked read-only. If you can't or
[  154.661881] intel_rng: don't want to disable this in firmware setup, and if
[  154.661883] intel_rng: you are certain that your system has a functional
[  154.661884] intel_rng: RNG, try using the 'no_fwh_detect' option.
[  155.368249] NET: Registered protocol family 10
[  155.368339] lo: Disabled Privacy Extensions
[  155.430477] input: PC Speaker as /class/input/input2
[  155.476632] parport: PnPBIOS parport detected.
[  155.476662] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[  155.679788] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 17
[  155.679814] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[  155.692519] usbcore: registered new interface driver snd-usb-audio
[  156.073876] lp0: using parport0 (interrupt-driven).
[  156.162182] Linux video capture interface: v2.00
[  156.208654] usbcore: registered new interface driver quickcam
[  156.384059] input: ImExPS/2 Generic Explorer Mouse as /class/input/input3
[  156.625832] EXT3 FS on sde1, internal journal
[  158.171196] NET: Registered protocol family 17
[  162.235849] input: Power Button (FF) as /class/input/input4
[  162.240486] ACPI: Power Button (FF) [PWRF]
[  162.274352] input: Sleep Button (CM) as /class/input/input5
[  162.278982] ACPI: Sleep Button (CM) [SLPB]
[  162.297136] Using specific hotkey driver
[  162.330036] No dock devices found.
[  162.406796] ibm_acpi: ec object not found
[  162.538679] pcc_acpi: loading...
[  164.451840] eth2: link down
[  164.451971] ADDRCONF(NETDEV_UP): eth2: link is not ready
[  165.320351] tun: Universal TUN/TAP device driver, 1.6
[  165.320357] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[  165.948810] [drm] Initialized drm 1.1.0 20060810
[  166.038425] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[  166.041339] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  166.132048] eth0: no IPv6 routers present
[  166.862894] ppdev: user-space parallel port driver
[  174.613382] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  174.613387] apm: overridden by ACPI.
[  179.323074] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[  179.670984] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[  179.693561] NFSD: starting 90-second grace period
[  182.832603] Bluetooth: Core ver 2.11
[  182.833282] NET: Registered protocol family 31
[  182.833288] Bluetooth: HCI device and connection manager initialized
[  182.833292] Bluetooth: HCI socket layer initialized
[  182.850368] Bluetooth: L2CAP ver 2.8
[  182.850374] Bluetooth: L2CAP socket layer initialized
[  183.028221] Bluetooth: RFCOMM socket layer initialized
[  183.028464] Bluetooth: RFCOMM TTY layer initialized
[  183.028469] Bluetooth: RFCOMM ver 1.8

```

I am sorry about the huge amount of info there, but I am still a bit of a newb to Linux, so I wasn't sure what could help and what couldn't.

---

### Post by merlinus on 2007-06-01
If you install the new kernel ( 2.6.20-16-generic), available as an update, it will go back to hd's.

-merlin

---

### Post by Jhereg on 2007-06-01
Thanks so much for help! I hadn't realized that I hadn't updated in awhile.

This computer is not used all that often, but i would like to keep it up to date. Is there a way that I can have it fetch updates automatically, without me having to input the password? perhaps some sort of credentials file like you would use for an automated samba script?

And as long as my questions are being answered, I added a line to my fstab to mount a samba share with all my music in it, but it doesn't automount like i thought it was supposed to. Also, rightclick->mount returns a "permission denied" error. In other words, I have to "sudo mount /media/music" to get the drive to mount, no a big problem, but a little annoying.

Thanks again for the help and quick reply.

EDIT: just finished the upgrade and all problems are solved! i had hoped the fix would be easy, but thats why I like K/Ubuntu

---

### Post by lrrr on 2007-06-08
I just started getting the same problems (hard drive partitions go from /dev/hda* to /dev/sda*, incredibly slow boot). However, I just upgraded to linux-image-generic version 2.6.20-16.29-generic. Does anybody know what is happening here?

```
Jun  9 00:48:01 localhost kernel: [    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #
2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
Jun  9 00:48:01 localhost kernel: [    0.000000] BIOS-provided physical RAM map:
Jun  9 00:48:01 localhost kernel: [    0.000000] sanitize start
Jun  9 00:48:01 localhost kernel: [    0.000000] sanitize end
Jun  9 00:48:01 localhost kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
Jun  9 00:48:01 localhost kernel: [    0.000000] copy_e820_map() type is E820_RAM
Jun  9 00:48:01 localhost kernel: [    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
Jun  9 00:48:01 localhost kernel: [    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
Jun  9 00:48:01 localhost kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001feec000 end: 000000001ffec000 type: 1
Jun  9 00:48:01 localhost kernel: [    0.000000] copy_e820_map() type is E820_RAM
Jun  9 00:48:01 localhost kernel: [    0.000000] copy_e820_map() start: 000000001ffec000 size: 0000000000003000 end: 000000001ffef000 type: 3
Jun  9 00:48:01 localhost kernel: [    0.000000] copy_e820_map() start: 000000001ffef000 size: 0000000000010000 end: 000000001ffff000 type: 2
Jun  9 00:48:01 localhost kernel: [    0.000000] copy_e820_map() start: 000000001ffff000 size: 0000000000001000 end: 0000000020000000 type: 4
Jun  9 00:48:01 localhost kernel: [    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000001000 end: 00000000fec01000 type: 2
Jun  9 00:48:01 localhost kernel: [    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
Jun  9 00:48:01 localhost kernel: [    0.000000] copy_e820_map() start: 00000000ffff0000 size: 0000000000010000 end: 0000000100000000 type: 2
Jun  9 00:48:01 localhost kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Jun  9 00:48:01 localhost kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Jun  9 00:48:01 localhost kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jun  9 00:48:01 localhost kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffec000 (usable)
Jun  9 00:48:01 localhost kernel: [    0.000000]  BIOS-e820: 000000001ffec000 - 000000001ffef000 (ACPI data)
Jun  9 00:48:01 localhost kernel: [    0.000000]  BIOS-e820: 000000001ffef000 - 000000001ffff000 (reserved)
Jun  9 00:48:01 localhost kernel: [    0.000000]  BIOS-e820: 000000001ffff000 - 0000000020000000 (ACPI NVS)
Jun  9 00:48:01 localhost kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Jun  9 00:48:01 localhost kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jun  9 00:48:01 localhost kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Jun  9 00:48:01 localhost kernel: [    0.000000] 0MB HIGHMEM available.
Jun  9 00:48:01 localhost kernel: [    0.000000] 511MB LOWMEM available.
Jun  9 00:48:01 localhost kernel: [    0.000000] Entering add_active_range(0, 0, 131052) 0 entries of 256 used
Jun  9 00:48:01 localhost kernel: [    0.000000] Zone PFN ranges:
Jun  9 00:48:01 localhost kernel: [    0.000000]   DMA             0 ->     4096
Jun  9 00:48:01 localhost kernel: [    0.000000]   Normal       4096 ->   131052
Jun  9 00:48:01 localhost kernel: [    0.000000]   HighMem    131052 ->   131052
Jun  9 00:48:01 localhost kernel: [    0.000000] early_node_map[1] active PFN ranges
Jun  9 00:48:01 localhost kernel: [    0.000000]     0:        0 ->   131052
Jun  9 00:48:01 localhost kernel: [    0.000000] On node 0 totalpages: 131052
Jun  9 00:48:01 localhost kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Jun  9 00:48:01 localhost kernel: [    0.000000]   DMA zone: 0 pages reserved
Jun  9 00:48:01 localhost kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Jun  9 00:48:01 localhost kernel: [    0.000000]   Normal zone: 991 pages used for memmap
Jun  9 00:48:01 localhost kernel: [    0.000000]   Normal zone: 125965 pages, LIFO batch:31
Jun  9 00:48:01 localhost kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
Jun  9 00:48:01 localhost kernel: [    0.000000] DMI 2.3 present.
Jun  9 00:48:01 localhost kernel: [    0.000000] ACPI: RSDP (v000 ASUS                                  ) @ 0x000f5310
Jun  9 00:48:01 localhost kernel: [    0.000000] ACPI: RSDT (v001 ASUS   P4PE     0x42302e31 MSFT 0x31313031) @ 0x1ffec000
Jun  9 00:48:01 localhost kernel: [    0.000000] ACPI: FADT (v001 ASUS   P4PE     0x42302e31 MSFT 0x31313031) @ 0x1ffec0c0
Jun  9 00:48:01 localhost kernel: [    0.000000] ACPI: BOOT (v001 ASUS   P4PE     0x42302e31 MSFT 0x31313031) @ 0x1ffec030
Jun  9 00:48:01 localhost kernel: [    0.000000] ACPI: MADT (v001 ASUS   P4PE     0x42302e31 MSFT 0x31313031) @ 0x1ffec058
Jun  9 00:48:01 localhost kernel: [    0.000000] ACPI: DSDT (v001   ASUS P4PE     0x00001000 MSFT 0x0100000b) @ 0x00000000
Jun  9 00:48:01 localhost kernel: [    0.000000] ACPI: PM-Timer IO Port: 0xe408
Jun  9 00:48:01 localhost kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun  9 00:48:01 localhost kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jun  9 00:48:01 localhost kernel: [    0.000000] Processor #0 15:2 APIC version 20
Jun  9 00:48:01 localhost kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jun  9 00:48:01 localhost kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jun  9 00:48:01 localhost kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Jun  9 00:48:01 localhost kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl edge)
Jun  9 00:48:01 localhost kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 22 low level)
Jun  9 00:48:01 localhost kernel: [    0.000000] ACPI: IRQ0 used by override.
Jun  9 00:48:01 localhost kernel: [    0.000000] ACPI: IRQ2 used by override.
Jun  9 00:48:01 localhost kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jun  9 00:48:01 localhost kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jun  9 00:48:01 localhost kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
Jun  9 00:48:01 localhost kernel: [    0.000000] Detected 2539.267 MHz processor.
Jun  9 00:48:01 localhost kernel: [   16.927909] Built 1 zonelists.  Total pages: 130029
Jun  9 00:48:01 localhost kernel: [   16.927915] Kernel command line: root=UUID=c0a27ba7-5990-4503-a096-abe65be4812f ro splash vga=775
Jun  9 00:48:01 localhost kernel: [   16.928092] mapped APIC to ffffd000 (fee00000)
Jun  9 00:48:01 localhost kernel: [   16.928095] mapped IOAPIC to ffffc000 (fec00000)
Jun  9 00:48:01 localhost kernel: [   16.928098] Enabling fast FPU save and restore... done.
Jun  9 00:48:01 localhost kernel: [   16.928102] Enabling unmasked SIMD FPU exception support... done.
Jun  9 00:48:01 localhost kernel: [   16.928117] Initializing CPU#0
Jun  9 00:48:01 localhost kernel: [   16.928213] PID hash table entries: 2048 (order: 11, 8192 bytes)
Jun  9 00:48:01 localhost kernel: [   16.928319] Console: colour dummy device 80x25
Jun  9 00:48:01 localhost kernel: [   16.928811] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Jun  9 00:48:01 localhost kernel: [   16.929165] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Jun  9 00:48:01 localhost kernel: [   16.940227] Memory: 507064k/524208k available (1992k kernel code, 16624k reserved, 900k data, 328k init, 0
k highmem)
Jun  9 00:48:01 localhost kernel: [   16.940243] virtual kernel memory layout:
Jun  9 00:48:01 localhost kernel: [   16.940244]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
Jun  9 00:48:01 localhost kernel: [   16.940245]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jun  9 00:48:01 localhost kernel: [   16.940246]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
Jun  9 00:48:01 localhost kernel: [   16.940247]     lowmem  : 0xc0000000 - 0xdffec000   ( 511 MB)
Jun  9 00:48:01 localhost kernel: [   16.940249]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
Jun  9 00:48:01 localhost kernel: [   16.940250]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
Jun  9 00:48:01 localhost kernel: [   16.940251]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
Jun  9 00:48:01 localhost kernel: [   16.940264] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Jun  9 00:48:01 localhost kernel: [   17.020157] Calibrating delay using timer specific routine.. 5082.50 BogoMIPS (lpj=10165015)
Jun  9 00:48:01 localhost kernel: [   17.020207] Security Framework v1.0.0 initialized
Jun  9 00:48:01 localhost kernel: [   17.020216] SELinux:  Disabled at boot.
Jun  9 00:48:01 localhost kernel: [   17.020236] Mount-cache hash table entries: 512
Jun  9 00:48:01 localhost kernel: [   17.020396] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00000400 00000000 00000
000
Jun  9 00:48:01 localhost kernel: [   17.020409] CPU: Trace cache: 12K uops, L1 D cache: 8K
Jun  9 00:48:01 localhost kernel: [   17.020414] CPU: L2 cache: 512K
Jun  9 00:48:01 localhost kernel: [   17.020418] CPU: Hyper-Threading is disabled
Jun  9 00:48:01 localhost kernel: [   17.020421] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003080 00000400 00000000 00000000
Jun  9 00:48:01 localhost kernel: [   17.020433] Compat vDSO mapped to ffffe000.
Jun  9 00:48:01 localhost kernel: [   17.020438] Remapping vsyscall page to ffffe000
Jun  9 00:48:01 localhost kernel: [   17.020453] Checking 'hlt' instruction... OK.
Jun  9 00:48:01 localhost kernel: [   17.036246] SMP alternatives: switching to UP code
Jun  9 00:48:01 localhost kernel: [   17.036446] Freeing SMP alternatives: 11k freed
Jun  9 00:48:01 localhost kernel: [   17.036668] Early unpacking initramfs... done
Jun  9 00:48:01 localhost kernel: [   17.395859] ACPI: Core revision 20060707
Jun  9 00:48:01 localhost kernel: [   17.396781] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Jun  9 00:48:01 localhost kernel: [   17.398002] CPU0: Intel(R) Pentium(R) 4 CPU 2.53GHz stepping 07
Jun  9 00:48:01 localhost kernel: [   17.398048] Total of 1 processors activated (5082.50 BogoMIPS).
Jun  9 00:48:01 localhost kernel: [   17.398185] ENABLING IO-APIC IRQs
Jun  9 00:48:01 localhost kernel: [   17.398378] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Jun  9 00:48:01 localhost kernel: [   17.543853] Brought up 1 CPUs
Jun  9 00:48:01 localhost kernel: [   17.544117] Booting paravirtualized kernel on bare hardware
Jun  9 00:48:01 localhost kernel: [   17.544198] Time:  0:44:02  Date: 05/09/107
Jun  9 00:48:01 localhost kernel: [   17.544231] NET: Registered protocol family 16
Jun  9 00:48:01 localhost kernel: [   17.544336] EISA bus registered
Jun  9 00:48:01 localhost kernel: [   17.544343] ACPI: bus type pci registered
Jun  9 00:48:01 localhost kernel: [   17.546004] PCI: PCI BIOS revision 2.10 entry at 0xf1e50, last bus=2
Jun  9 00:48:01 localhost kernel: [   17.546008] PCI: Using configuration type 1
Jun  9 00:48:01 localhost kernel: [   17.546011] Setting up standard PCI resources
Jun  9 00:48:01 localhost kernel: [   17.556062] ACPI: Interpreter enabled
Jun  9 00:48:01 localhost kernel: [   17.556071] ACPI: Using IOAPIC for interrupt routing
Jun  9 00:48:01 localhost kernel: [   17.556797] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Jun  9 00:48:01 localhost kernel: [   17.557025] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Jun  9 00:48:01 localhost kernel: [   17.557266] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Jun  9 00:48:01 localhost kernel: [   17.557500] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Jun  9 00:48:01 localhost kernel: [   17.557721] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Jun  9 00:48:01 localhost kernel: [   17.557945] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Jun  9 00:48:01 localhost kernel: [   17.558167] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Jun  9 00:48:01 localhost kernel: [   17.558391] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Jun  9 00:48:01 localhost kernel: [   17.559403] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jun  9 00:48:01 localhost kernel: [   17.559412] PCI: Probing PCI hardware (bus 00)
Jun  9 00:48:01 localhost kernel: [   17.559762] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
Jun  9 00:48:01 localhost kernel: [   17.560290] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
Jun  9 00:48:01 localhost kernel: [   17.560292] * this clock source is slow. If you are sure your timer does not have
Jun  9 00:48:01 localhost kernel: [   17.560293] * this bug, please use "acpi_pm_good" to disable the workaround
Jun  9 00:48:01 localhost kernel: [   17.560344] PCI: Enabled i801 SMBus device
Jun  9 00:48:01 localhost kernel: [   17.560352] PCI quirk: region e400-e47f claimed by ICH4 ACPI/GPIO/TCO
Jun  9 00:48:01 localhost kernel: [   17.560357] PCI quirk: region ec00-ec3f claimed by ICH4 GPIO
Jun  9 00:48:01 localhost kernel: [   17.560546] Boot video device is 0000:01:00.0
Jun  9 00:48:01 localhost kernel: [   17.560986] PCI: Transparent bridge - 0000:00:1e.0
Jun  9 00:48:01 localhost kernel: [   17.561016] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jun  9 00:48:01 localhost kernel: [   17.624700] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
Jun  9 00:48:01 localhost kernel: [   17.625710] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
Jun  9 00:48:01 localhost kernel: [   17.635606] Linux Plug and Play Support v0.97 (c) Adam Belay
Jun  9 00:48:01 localhost kernel: [   17.635623] pnp: PnP ACPI init
Jun  9 00:48:01 localhost kernel: [   17.640742] pnp: PnP ACPI: found 15 devices
Jun  9 00:48:01 localhost kernel: [   17.640753] PnPBIOS: Disabled by ACPI PNP
Jun  9 00:48:01 localhost kernel: [   17.640813] PCI: Using ACPI for IRQ routing
Jun  9 00:48:01 localhost kernel: [   17.640819] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jun  9 00:48:01 localhost kernel: [   17.650253] NET: Registered protocol family 8
Jun  9 00:48:01 localhost kernel: [   17.650257] NET: Registered protocol family 20
Jun  9 00:48:01 localhost kernel: [   17.650538] pnp: 00:02: ioport range 0xe400-0xe47f could not be reserved
Jun  9 00:48:01 localhost kernel: [   17.650544] pnp: 00:02: ioport range 0xe800-0xe81f has been reserved
Jun  9 00:48:01 localhost kernel: [   17.650548] pnp: 00:02: ioport range 0xec00-0xec3f has been reserved
Jun  9 00:48:01 localhost kernel: [   17.650552] pnp: 00:02: ioport range 0x4d6-0x4d6 has been reserved
Jun  9 00:48:01 localhost kernel: [   17.650568] pnp: 00:0e: ioport range 0x3f0-0x3f1 has been reserved
Jun  9 00:48:01 localhost kernel: [   17.650904] PCI: Bridge: 0000:00:01.0
Jun  9 00:48:01 localhost kernel: [   17.650908]   IO window: disabled.
Jun  9 00:48:01 localhost kernel: [   17.650915]   MEM window: f2000000-f3dfffff
Jun  9 00:48:01 localhost kernel: [   17.650921]   PREFETCH window: f3f00000-f7ffffff
Jun  9 00:48:01 localhost kernel: [   17.650930] PCI: Bridge: 0000:00:1e.0
Jun  9 00:48:01 localhost kernel: [   17.650935]   IO window: b000-bfff
Jun  9 00:48:01 localhost kernel: [   17.650942]   MEM window: ef000000-f17fffff
Jun  9 00:48:01 localhost kernel: [   17.650948]   PREFETCH window: f3e00000-f3efffff
Jun  9 00:48:01 localhost kernel: [   17.650968] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Jun  9 00:48:01 localhost kernel: [   17.651001] NET: Registered protocol family 2
Jun  9 00:48:01 localhost kernel: [   17.687810] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Jun  9 00:48:01 localhost kernel: [   17.687907] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
Jun  9 00:48:01 localhost kernel: [   17.688009] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
Jun  9 00:48:01 localhost kernel: [   17.688061] TCP: Hash tables configured (established 16384 bind 8192)
Jun  9 00:48:01 localhost kernel: [   17.688065] TCP reno registered
Jun  9 00:48:01 localhost kernel: [   17.699847] checking if image is initramfs... it is
Jun  9 00:48:01 localhost kernel: [   18.414092] Freeing initrd memory: 8431k freed
Jun  9 00:48:01 localhost kernel: [   18.414350] Simple Boot Flag at 0x3a set to 0x1
Jun  9 00:48:01 localhost kernel: [   18.414607] audit: initializing netlink socket (disabled)
Jun  9 00:48:01 localhost kernel: [   18.414627] audit(1181349842.564:1): initialized
Jun  9 00:48:01 localhost kernel: [   18.414785] VFS: Disk quotas dquot_6.5.1
Jun  9 00:48:01 localhost kernel: [   18.414809] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jun  9 00:48:01 localhost kernel: [   18.414866] io scheduler noop registered
Jun  9 00:48:01 localhost kernel: [   18.414872] io scheduler anticipatory registered
Jun  9 00:48:01 localhost kernel: [   18.414876] io scheduler deadline registered
Jun  9 00:48:01 localhost kernel: [   18.414887] io scheduler cfq registered (default)
Jun  9 00:48:01 localhost kernel: [   18.415191] isapnp: Scanning for PnP cards...
Jun  9 00:48:01 localhost kernel: [   18.768988] isapnp: No Plug & Play device found
Jun  9 00:48:01 localhost kernel: [   18.798084] Real Time Clock Driver v1.12ac
Jun  9 00:48:01 localhost kernel: [   18.798152] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jun  9 00:48:01 localhost kernel: [   18.798281] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun  9 00:48:01 localhost kernel: [   18.798493] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Jun  9 00:48:01 localhost kernel: [   18.799263] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun  9 00:48:01 localhost kernel: [   18.799606] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Jun  9 00:48:01 localhost kernel: [   18.799882] mice: PS/2 mouse device common for all mice
Jun  9 00:48:01 localhost kernel: [   18.800519] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jun  9 00:48:01 localhost kernel: [   18.800805] input: Macintosh mouse button emulation as /class/input/input0
Jun  9 00:48:01 localhost kernel: [   18.800847] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jun  9 00:48:01 localhost kernel: [   18.800853] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jun  9 00:48:01 localhost kernel: [   18.801111] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jun  9 00:48:01 localhost kernel: [   18.804104] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun  9 00:48:01 localhost kernel: [   18.804113] serio: i8042 AUX port at 0x60,0x64 irq 12
Jun  9 00:48:01 localhost kernel: [   18.804252] EISA: Probing bus 0 at eisa.0
Jun  9 00:48:01 localhost kernel: [   18.804292] EISA: Detected 0 cards.
Jun  9 00:48:01 localhost kernel: [   18.834383] TCP cubic registered
Jun  9 00:48:01 localhost kernel: [   18.834391] NET: Registered protocol family 1
Jun  9 00:48:01 localhost kernel: [   18.834417] Using IPI No-Shortcut mode
Jun  9 00:48:01 localhost kernel: [   18.834491] ACPI: (supports S0 S1 S3 S4 S5)
Jun  9 00:48:01 localhost kernel: [   18.834543]   Magic number: 11:355:708
Jun  9 00:48:01 localhost kernel: [   18.834938] Time: tsc clocksource has been installed.
Jun  9 00:48:01 localhost kernel: [   18.835146] Freeing unused kernel memory: 328k freed
Jun  9 00:48:01 localhost kernel: [   18.852858] input: AT Translated Set 2 keyboard as /class/input/input1
Jun  9 00:48:01 localhost kernel: [   18.932430] vesafb: framebuffer at 0xf4000000, mapped to 0xe0880000, using 2560k, total 65536k
Jun  9 00:48:01 localhost kernel: [   18.932443] vesafb: mode is 1280x1024x8, linelength=1280, pages=1
Jun  9 00:48:01 localhost kernel: [   18.932447] vesafb: protected mode interface info at c000:dd80
Jun  9 00:48:01 localhost kernel: [   18.932452] vesafb: pmi: set display start = c00cddc5, set palette = c00cde4a
Jun  9 00:48:01 localhost kernel: [   18.932455] vesafb: pmi: ports = b4c3 b503 ba03 c003 c103 c403 c503 c603 c703 c803 c903 cc03 ce03 cf03 d00
3 d103 d203 d303 d403 d503 da03 ff03 
Jun  9 00:48:01 localhost kernel: [   18.932480] vesafb: scrolling: redraw
Jun  9 00:48:01 localhost kernel: [   18.932484] vesafb: Pseudocolor: size=8:8:8:8, shift=0:0:0:0
Jun  9 00:48:01 localhost kernel: [   18.941533] Console: switching to colour frame buffer device 160x64
Jun  9 00:48:01 localhost kernel: [   18.950566] fb0: VESA VGA frame buffer device
Jun  9 00:48:01 localhost kernel: [   20.380604] Capability LSM initialized
Jun  9 00:48:01 localhost kernel: [   20.395761] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: dm-devel@redhat.com
Jun  9 00:48:01 localhost kernel: [   20.697121] ACPI: Invalid PBLK length [5]
Jun  9 00:48:01 localhost kernel: [   20.697158] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Jun  9 00:48:01 localhost kernel: [   21.222099] md: linear personality registered for level -1
Jun  9 00:48:01 localhost kernel: [   21.228567] md: multipath personality registered for level -4
Jun  9 00:48:01 localhost kernel: [   21.232970] md: raid0 personality registered for level 0
Jun  9 00:48:01 localhost kernel: [   21.237986] md: raid1 personality registered for level 1
Jun  9 00:48:01 localhost kernel: [   21.242284] raid5: automatically using best checksumming function: pIII_sse
Jun  9 00:48:01 localhost kernel: [   21.261306]    pIII_sse  :  3208.000 MB/sec
Jun  9 00:48:01 localhost kernel: [   21.261308] raid5: using function: pIII_sse (3208.000 MB/sec)
Jun  9 00:48:01 localhost kernel: [   22.124739] raid6: int32x1    686 MB/s
Jun  9 00:48:01 localhost kernel: [   22.192699] raid6: int32x2    695 MB/s
Jun  9 00:48:01 localhost kernel: [   22.260641] raid6: int32x4    700 MB/s
Jun  9 00:48:01 localhost kernel: [   22.328697] raid6: int32x8    475 MB/s
Jun  9 00:48:01 localhost kernel: [   22.396549] raid6: mmxx1     1949 MB/s
Jun  9 00:48:01 localhost kernel: [   22.464508] raid6: mmxx2     2602 MB/s
Jun  9 00:48:01 localhost kernel: [   22.532460] raid6: sse1x1    1224 MB/s
Jun  9 00:48:01 localhost kernel: [   22.600420] raid6: sse1x2    2294 MB/s
Jun  9 00:48:01 localhost kernel: [   22.668366] raid6: sse2x1    1845 MB/s
Jun  9 00:48:01 localhost kernel: [   22.736330] raid6: sse2x2    2874 MB/s
Jun  9 00:48:01 localhost kernel: [   22.736332] raid6: using algorithm sse2x2 (2874 MB/s)
Jun  9 00:48:01 localhost kernel: [   22.736336] md: raid6 personality registered for level 6
Jun  9 00:48:01 localhost kernel: [   22.736338] md: raid5 personality registered for level 5
Jun  9 00:48:01 localhost kernel: [   22.736340] md: raid4 personality registered for level 4
Jun  9 00:48:01 localhost kernel: [   22.764264] md: raid10 personality registered for level 10
Jun  9 00:48:01 localhost kernel: [   23.446721] usbcore: registered new interface driver usbfs
Jun  9 00:48:01 localhost kernel: [   23.446753] usbcore: registered new interface driver hub
Jun  9 00:48:01 localhost kernel: [   23.446777] usbcore: registered new device driver usb
Jun  9 00:48:01 localhost kernel: [   23.447798] USB Universal Host Controller Interface driver v3.0
Jun  9 00:48:01 localhost kernel: [   23.447868] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
Jun  9 00:48:01 localhost kernel: [   23.447882] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Jun  9 00:48:01 localhost kernel: [   23.447886] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jun  9 00:48:01 localhost kernel: [   23.448036] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Jun  9 00:48:01 localhost kernel: [   23.448064] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000d800
Jun  9 00:48:01 localhost kernel: [   23.448183] usb usb1: configuration #1 chosen from 1 choice
Jun  9 00:48:01 localhost kernel: [   23.448213] hub 1-0:1.0: USB hub found
Jun  9 00:48:01 localhost kernel: [   23.448223] hub 1-0:1.0: 2 ports detected
Jun  9 00:48:01 localhost kernel: [   23.519871] ieee1394: Initialized config rom entry `ip1394'
Jun  9 00:48:01 localhost kernel: [   23.552125] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
Jun  9 00:48:01 localhost kernel: [   23.552142] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Jun  9 00:48:01 localhost kernel: [   23.552146] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jun  9 00:48:01 localhost kernel: [   23.552170] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Jun  9 00:48:01 localhost kernel: [   23.552197] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000d400
Jun  9 00:48:01 localhost kernel: [   23.552302] usb usb2: configuration #1 chosen from 1 choice
Jun  9 00:48:01 localhost kernel: [   23.552335] hub 2-0:1.0: USB hub found
Jun  9 00:48:01 localhost kernel: [   23.552344] hub 2-0:1.0: 2 ports detected
Jun  9 00:48:01 localhost kernel: [   23.656043] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
Jun  9 00:48:01 localhost kernel: [   23.656059] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Jun  9 00:48:01 localhost kernel: [   23.656063] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jun  9 00:48:01 localhost kernel: [   23.656093] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Jun  9 00:48:01 localhost kernel: [   23.656122] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d000
Jun  9 00:48:01 localhost kernel: [   23.656221] usb usb3: configuration #1 chosen from 1 choice
Jun  9 00:48:01 localhost kernel: [   23.656249] hub 3-0:1.0: USB hub found
Jun  9 00:48:01 localhost kernel: [   23.656259] hub 3-0:1.0: 2 ports detected
Jun  9 00:48:01 localhost kernel: [   23.706164] Floppy drive(s): fd0 is 1.44M
Jun  9 00:48:01 localhost kernel: [   23.733690] FDC 0 is a post-1991 82077
Jun  9 00:48:01 localhost kernel: [   23.761900] PCI: Enabling device 0000:00:1d.7 (0004 -> 0006)
Jun  9 00:48:01 localhost kernel: [   23.761918] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
Jun  9 00:48:01 localhost kernel: [   23.761936] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Jun  9 00:48:01 localhost kernel: [   23.761940] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jun  9 00:48:01 localhost kernel: [   23.761988] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
Jun  9 00:48:01 localhost kernel: [   23.762033] ehci_hcd 0000:00:1d.7: debug port 1
Jun  9 00:48:01 localhost kernel: [   23.762040] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
Jun  9 00:48:01 localhost kernel: [   23.762053] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xf1800000
Jun  9 00:48:01 localhost kernel: [   23.765935] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jun  9 00:48:01 localhost kernel: [   23.766034] usb usb4: configuration #1 chosen from 1 choice
Jun  9 00:48:01 localhost kernel: [   23.766070] hub 4-0:1.0: USB hub found
Jun  9 00:48:01 localhost kernel: [   23.766080] hub 4-0:1.0: 6 ports detected
Jun  9 00:48:01 localhost kernel: [   23.791831] usb 1-1: new full speed USB device using uhci_hcd and address 2
Jun  9 00:48:01 localhost kernel: [   23.874528] SCSI subsystem initialized
Jun  9 00:48:01 localhost kernel: [   23.880684] libata version 2.20 loaded.
Jun  9 00:48:01 localhost kernel: [   23.884456] ata_piix 0000:00:1f.1: version 2.10ac1
Jun  9 00:48:01 localhost kernel: [   23.884477] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
Jun  9 00:48:01 localhost kernel: [   23.884500] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Jun  9 00:48:01 localhost kernel: [   23.884565] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001f000 irq 14
Jun  9 00:48:01 localhost kernel: [   23.888666] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001f008 irq 15
Jun  9 00:48:01 localhost kernel: [   23.888700] scsi0 : ata_piix
Jun  9 00:48:01 localhost kernel: [   24.093495] ata1.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168
Jun  9 00:48:01 localhost kernel: [   24.093501] ata1.00: ATA-7: ST3250820A, 3.AAC, max UDMA/100
Jun  9 00:48:01 localhost kernel: [   24.093504] ata1.00: 488397168 sectors, multi 16: LBA48 
Jun  9 00:48:01 localhost kernel: [   24.151540] ata1.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168
Jun  9 00:48:01 localhost kernel: [   24.151546] ata1.00: configured for UDMA/100
Jun  9 00:48:01 localhost kernel: [   24.151562] scsi1 : ata_piix
Jun  9 00:48:01 localhost kernel: [   24.295484] usb 1-1: new full speed USB device using uhci_hcd and address 3
Jun  9 00:48:01 localhost kernel: [   24.483260] usb 1-1: configuration #1 chosen from 1 choice
Jun  9 00:48:01 localhost kernel: [   24.795480] ata2.00: ATAPI, max UDMA/33
Jun  9 00:48:01 localhost kernel: [   24.795485] ata2.01: ATAPI, max UDMA/33
Jun  9 00:48:01 localhost kernel: [   24.951379] ata2.00: configured for UDMA/33
Jun  9 00:48:01 localhost kernel: [   54.931826] ata2.01: qc timeout (cmd 0xef)
Jun  9 00:48:01 localhost kernel: [   54.931837] ata2.01: failed to set xfermode (err_mask=0x4)
Jun  9 00:48:01 localhost kernel: [   54.931841] ata2: failed to recover some devices, retrying in 5 secs
Jun  9 00:48:01 localhost kernel: [   60.736399] ata2.00: configured for UDMA/33
Jun  9 00:48:01 localhost kernel: [   90.716841] ata2.01: qc timeout (cmd 0xef)
Jun  9 00:48:01 localhost kernel: [   90.716851] ata2.01: failed to set xfermode (err_mask=0x4)
Jun  9 00:48:01 localhost kernel: [   90.716856] ata2.01: limiting speed to UDMA/33:PIO3
Jun  9 00:48:01 localhost kernel: [   90.716859] ata2: failed to recover some devices, retrying in 5 secs
Jun  9 00:48:01 localhost kernel: [   96.521407] ata2.00: configured for UDMA/33
Jun  9 00:48:01 localhost kernel: [  126.501860] ata2.01: qc timeout (cmd 0xef)
Jun  9 00:48:01 localhost kernel: [  126.501870] ata2.01: failed to set xfermode (err_mask=0x4)
Jun  9 00:48:01 localhost kernel: [  126.501874] ata2.01: disabled
Jun  9 00:48:01 localhost kernel: [  126.501877] ata2: failed to recover some devices, retrying in 5 secs
Jun  9 00:48:01 localhost kernel: [  131.502648] ata2.00: failed to set xfermode (err_mask=0x40)
Jun  9 00:48:01 localhost kernel: [  131.502654] ata2: failed to recover some devices, retrying in 5 secs
Jun  9 00:48:01 localhost kernel: [  137.147314] ata2.00: configured for UDMA/33
Jun  9 00:48:01 localhost kernel: [  137.147462] scsi 0:0:0:0: Direct-Access     ATA      ST3250820A       3.AA PQ: 0 ANSI: 5
Jun  9 00:48:01 localhost kernel: [  137.150830] scsi 1:0:0:0: CD-ROM            JLMS     XJ-HD166S        DNS2 PQ: 0 ANSI: 5
Jun  9 00:48:01 localhost kernel: [  137.153954] PCI: Enabling device 0000:02:03.0 (0094 -> 0097)
Jun  9 00:48:01 localhost kernel: [  137.153963] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 22 (level, low) -> IRQ 22
Jun  9 00:48:01 localhost kernel: [  137.207060] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[22]  MMIO=[f1000000-f10007ff]  Max Packet=[2048]
  IR/IT contexts=[4/8]
Jun  9 00:48:01 localhost kernel: [  137.212125] PCI: Enabling device 0000:02:0d.2 (0014 -> 0016)
Jun  9 00:48:01 localhost kernel: [  137.212132] ACPI: PCI Interrupt 0000:02:0d.2[B] -> GSI 22 (level, low) -> IRQ 22
Jun  9 00:48:01 localhost kernel: [  137.263338] ohci1394: fw-host1: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[ef800000-ef8007ff]  Max Packet=[2048]
  IR/IT contexts=[4/8]
Jun  9 00:48:01 localhost kernel: [  137.263856] tg3.c:v3.72 (January 8, 2007)
Jun  9 00:48:01 localhost kernel: [  137.263879] PCI: Enabling device 0000:02:05.0 (0014 -> 0016)
Jun  9 00:48:01 localhost kernel: [  137.263893] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 20 (level, low) -> IRQ 20
Jun  9 00:48:01 localhost kernel: [  137.285036] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
Jun  9 00:48:01 localhost kernel: [  137.285066] sda: Write Protect is off
Jun  9 00:48:01 localhost kernel: [  137.285069] sda: Mode Sense: 00 3a 00 00
Jun  9 00:48:01 localhost kernel: [  137.285089] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun  9 00:48:01 localhost kernel: [  137.285162] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
Jun  9 00:48:01 localhost kernel: [  137.285173] sda: Write Protect is off
Jun  9 00:48:01 localhost kernel: [  137.285176] sda: Mode Sense: 00 3a 00 00
Jun  9 00:48:01 localhost kernel: [  137.285195] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun  9 00:48:01 localhost kernel: [  137.285200]  sda:<6>eth0: Tigon3 [partno(BCM95702A20) rev 1002 PHY(5703)] (PCI:33MHz:32-bit) 10/100/1000Ba
se-T Ethernet 00:0c:6e:34:0f:6f
Jun  9 00:48:01 localhost kernel: [  137.317789] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[1] TSOcap[1] 
Jun  9 00:48:01 localhost kernel: [  137.317793] eth0: dma_rwctrl[763f0000] dma_mask[64-bit]
Jun  9 00:48:01 localhost kernel: [  137.318527]  sda1 sda2 sda3 < sda5 sda6 sda7 >
Jun  9 00:48:01 localhost kernel: [  137.348529] sd 0:0:0:0: Attached scsi disk sda
Jun  9 00:48:01 localhost kernel: [  137.353177] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jun  9 00:48:01 localhost kernel: [  137.353205] scsi 1:0:0:0: Attached scsi generic sg1 type 5
Jun  9 00:48:01 localhost kernel: [  137.358032] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
Jun  9 00:48:01 localhost kernel: [  137.358041] Uniform CD-ROM driver Revision: 3.20
Jun  9 00:48:01 localhost kernel: [  137.358259] sr 1:0:0:0: Attached scsi CD-ROM sr0
Jun  9 00:48:01 localhost kernel: [  137.852896] kjournald starting.  Commit interval 5 seconds
Jun  9 00:48:01 localhost kernel: [  137.852911] EXT3-fs: mounted filesystem with ordered data mode.
Jun  9 00:48:01 localhost kernel: [  138.490349] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e01800001b008b]
Jun  9 00:48:01 localhost kernel: [  138.762128] ieee1394: Host added: ID:BUS[1-00:1023]  GUID[00023c009105d6ac]
Jun  9 00:48:01 localhost kernel: [  150.505101] iTCO_vendor_support: vendor-support=0
Jun  9 00:48:01 localhost kernel: [  150.506321] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
Jun  9 00:48:01 localhost kernel: [  150.506518] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x6460)
Jun  9 00:48:01 localhost kernel: [  150.506541] iTCO_wdt: heartbeat value must be 2<heartbeat<39 (TCO v1) or 613 (TCO v2), using 30
Jun  9 00:48:01 localhost kernel: [  150.506577] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Jun  9 00:48:01 localhost kernel: [  150.519050] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun  9 00:48:01 localhost kernel: [  150.571101] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jun  9 00:48:01 localhost kernel: [  150.573870] intel_rng: FWH not detected
Jun  9 00:48:01 localhost kernel: [  151.043785] ath_hal: module license 'Proprietary' taints kernel.
Jun  9 00:48:01 localhost kernel: [  151.044635] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
Jun  9 00:48:01 localhost kernel: [  151.132942] wlan: 0.8.4.2 (0.9.3)
Jun  9 00:48:01 localhost kernel: [  151.169265] ath_pci: 0.9.4.5 (0.9.3)
Jun  9 00:48:01 localhost kernel: [  151.170707] PCI: Enabling device 0000:02:0a.0 (0014 -> 0016)
Jun  9 00:48:01 localhost kernel: [  151.170716] ACPI: PCI Interrupt 0000:02:0a.0[A] -> GSI 22 (level, low) -> IRQ 22
Jun  9 00:48:01 localhost kernel: [  151.706376] input: PC Speaker as /class/input/input2
Jun  9 00:48:01 localhost kernel: [  151.765662] Linux agpgart interface v0.102 (c) Dave Jones
Jun  9 00:48:01 localhost kernel: [  151.833955] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x04
3D pid 0x001D
Jun  9 00:48:01 localhost kernel: [  151.833970] usbcore: registered new interface driver usblp
Jun  9 00:48:01 localhost kernel: [  151.833974] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
Jun  9 00:48:01 localhost kernel: [  152.018200] ath_rate_sample: 1.2 (0.9.3)
Jun  9 00:48:01 localhost kernel: [  152.019846] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
Jun  9 00:48:01 localhost kernel: [  152.019855] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54
Mbps
Jun  9 00:48:01 localhost kernel: [  152.019866] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Jun  9 00:48:01 localhost kernel: [  152.019874] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
Jun  9 00:48:01 localhost kernel: [  152.019879] wifi0: mac 7.9 phy 4.5 radio 5.6
Jun  9 00:48:01 localhost kernel: [  152.019885] wifi0: Use hw queue 1 for WME_AC_BE traffic
Jun  9 00:48:01 localhost kernel: [  152.019887] wifi0: Use hw queue 0 for WME_AC_BK traffic
Jun  9 00:48:01 localhost kernel: [  152.019889] wifi0: Use hw queue 2 for WME_AC_VI traffic
Jun  9 00:48:01 localhost kernel: [  152.019891] wifi0: Use hw queue 3 for WME_AC_VO traffic
Jun  9 00:48:01 localhost kernel: [  152.019893] wifi0: Use hw queue 8 for CAB traffic
Jun  9 00:48:01 localhost kernel: [  152.019895] wifi0: Use hw queue 9 for beacons
Jun  9 00:48:01 localhost kernel: [  152.049715] parport: PnPBIOS parport detected.
Jun  9 00:48:01 localhost kernel: [  152.049769] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Jun  9 00:48:01 localhost kernel: [  152.370096] wifi0: Atheros 5212: mem=0xf0000000, irq=22
Jun  9 00:48:01 localhost kernel: [  152.370133] PCI: Enabling device 0000:02:0d.1 (0004 -> 0005)
Jun  9 00:48:01 localhost kernel: [  152.385749] gameport: EMU10K1 is pci0000:02:0d.1/gameport0, io 0xb000, speed 1147kHz
Jun  9 00:48:01 localhost kernel: [  152.387743] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Jun  9 00:48:01 localhost kernel: [  152.388074] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
Jun  9 00:48:01 localhost kernel: [  152.808027] NET: Registered protocol family 17
Jun  9 00:48:01 localhost kernel: [  153.002309] PCI: Enabling device 0000:02:0d.0 (0004 -> 0005)
Jun  9 00:48:01 localhost kernel: [  153.002325] ACPI: PCI Interrupt 0000:02:0d.0[A] -> GSI 21 (level, low) -> IRQ 21
Jun  9 00:48:01 localhost kernel: [  153.005913] input: ImExPS/2 Logitech Wheel Mouse as /class/input/input3
Jun  9 00:48:01 localhost kernel: [  153.006164] Installing spdif_bug patch: Audigy 2 Platinum [SB0240P]
Jun  9 00:48:01 localhost kernel: [  153.035057] NET: Registered protocol family 10
Jun  9 00:48:01 localhost kernel: [  153.035162] lo: Disabled Privacy Extensions
Jun  9 00:48:01 localhost kernel: [  153.863471] lp0: using parport0 (interrupt-driven).
Jun  9 00:48:01 localhost kernel: [  153.964527] fuse init (API version 7.8)

```

The system holds at the 25 second mark and then goes into all those "qc timeout" messages.

**EDIT:** Solved problem by adding "irqpoll" to kernel boot options in /boot/grub/menu.lst as per [this here thread]("http://ubuntuforums.org/showthread.php?t=440122").

---

