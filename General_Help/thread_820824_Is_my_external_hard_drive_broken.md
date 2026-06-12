---
title: "Is my external hard drive broken?"
date: 2008-06-06
forum: General Help
---

### Post by spadewarrior on 2008-06-06
I'm not sure but it think it's fried. It's making a weird beeping noise every few seconds and xubuntu won't detect it. Is there any terminal command I can do to see if it's there/fix it?

Also, who actually makes reliable usb hard drives that work properly with linux? Mine is a Seagate FreeAgent.

Thanks.

---

### Post by ctrlER on 2008-06-06
It's probably dead.
See if it shows up in dmesg when you connect it.
You can paste the output here for us to take a look.
Open a terminal and type
```
dmesg
```

---

### Post by spadewarrior on 2008-06-06
Hi, 

I just decided 'what the hell' and opened the thing up, took it out of its case and plugged it directly into the motherboard via SATA lead. It now actually shows up in gparted but I can't seem to access it (although I don't really know what I'm doing!).

Here's the output:

```
dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-18-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed May 28 20:27:26 UTC 2008 (Ubuntu 2.6.24-18.32-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ff40000 (usable)
[    0.000000]  BIOS-e820: 000000003ff40000 - 000000003ff50000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ff50000 - 0000000040000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff380000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 261952) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   261952
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   261952
[    0.000000] On node 0 totalpages: 261952
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 254 pages used for memmap
[    0.000000]   HighMem zone: 32322 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FA570 checksum 0
[    0.000000] ACPI: RSDP 000FA570, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 3FF40000, 0030 (r1 A M I  OEMRSDT   7000731 MSFT       97)
[    0.000000] ACPI: FACP 3FF40200, 0081 (r2 A M I  OEMFACP   7000731 MSFT       97)
[    0.000000] ACPI: DSDT 3FF40370, 3B3B (r1  P4i6G P4i6G133      133 INTL  2002026)
[    0.000000] ACPI: FACS 3FF50000, 0040
[    0.000000] ACPI: APIC 3FF40300, 006C (r1 A M I  OEMAPIC   7000731 MSFT       97)
[    0.000000] ACPI: OEMB 3FF50040, 003F (r1 A M I  OEMBIOS   7000731 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bee00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259906
[    0.000000] Kernel command line: root=UUID=4e1ffc91-c5bf-4a77-b171-eec830bd47ba ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2659.959 MHz processor.
[   16.351422] Console: colour VGA+ 80x25
[   16.351426] console [tty0] enabled
[   16.352048] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   16.352639] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   16.386503] Memory: 1026276k/1047808k available (2176k kernel code, 20788k reserved, 1006k data, 368k init, 130304k highmem)
[   16.386514] virtual kernel memory layout:
[   16.386515]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   16.386517]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   16.386518]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   16.386519]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   16.386520]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   16.386521]       .data : 0xc03201f4 - 0xc041bdc4   (1006 kB)
[   16.386522]       .text : 0xc0100000 - 0xc03201f4   (2176 kB)
[   16.386525] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   16.386582] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   16.466409] Calibrating delay using timer specific routine.. 5324.81 BogoMIPS (lpj=10649626)
[   16.466444] Security Framework initialized
[   16.466455] SELinux:  Disabled at boot.
[   16.466473] AppArmor: AppArmor initialized
[   16.466479] Failure registering capabilities with primary security module.
[   16.466489] Mount-cache hash table entries: 512
[   16.466663] Initializing cgroup subsys ns
[   16.466670] Initializing cgroup subsys cpuacct
[   16.466684] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000 00000000
[   16.466699] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   16.466702] CPU: L2 cache: 512K
[   16.466705] CPU: Hyper-Threading is disabled
[   16.466707] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000 00000000
[   16.466722] Compat vDSO mapped to ffffe000.
[   16.466739] Checking 'hlt' instruction... OK.
[   16.482834] SMP alternatives: switching to UP code
[   16.484596] Freeing SMP alternatives: 11k freed
[   16.484746] Early unpacking initramfs... done
[   16.805533] ACPI: Core revision 20070126
[   16.805604] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   16.807574] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 09
[   16.807618] Total of 1 processors activated (5324.81 BogoMIPS).
[   16.807762] ENABLING IO-APIC IRQs
[   16.807950] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   16.953263] Brought up 1 CPUs
[   16.953289] CPU0 attaching sched-domain:
[   16.953292]  domain 0: span 01
[   16.953294]   groups: 01
[   16.953525] net_namespace: 64 bytes
[   16.953534] Booting paravirtualized kernel on bare hardware
[   16.954112] Time: 21:28:07  Date: 06/06/08
[   16.954144] NET: Registered protocol family 16
[   16.954384] EISA bus registered
[   16.954412] ACPI: bus type pci registered
[   16.954599] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[   16.954602] PCI: Using configuration type 1
[   16.954603] Setting up standard PCI resources
[   16.968938] ACPI: EC: Look up EC in DSDT
[   16.972842] ACPI: Interpreter enabled
[   16.972847] ACPI: (supports S0 S1 S3 S4 S5)
[   16.972864] ACPI: Using IOAPIC for interrupt routing
[   16.979723] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   16.980299] Force enabled HPET at base address 0xfed00000
[   16.980307] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[   16.980311] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[   16.980833] PCI: Transparent bridge - 0000:00:1e.0
[   16.980862] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   16.980973] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[   16.983004] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   16.983112] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   16.983218] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   16.983322] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   16.983429] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   16.983535] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   16.983641] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   16.983745] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   16.983878] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  ED, should be DE [20070126]
[   16.983884] Linux Plug and Play Support v0.97 (c) Adam Belay
[   16.983922] pnp: PnP ACPI init
[   16.983932] ACPI: bus type pnp registered
[   16.988735] pnp: PnP ACPI: found 15 devices
[   16.988739] ACPI: ACPI bus type pnp unregistered
[   16.988744] PnPBIOS: Disabled by ACPI PNP
[   16.989026] PCI: Using ACPI for IRQ routing
[   16.989029] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   17.005089] NET: Registered protocol family 8
[   17.005092] NET: Registered protocol family 20
[   17.005220] hpet clockevent registered
[   17.005227] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   17.005232] hpet0: 3 64-bit timers, 14318180 Hz
[   17.006285] AppArmor: AppArmor Filesystem Enabled
[   17.009069] Time: tsc clocksource has been installed.
[   17.017106] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   17.017110] system 00:08: ioport range 0x800-0x87f has been reserved
[   17.017112] system 00:08: ioport range 0x480-0x4bf has been reserved
[   17.017116] system 00:08: iomem range 0xfed20000-0xfed8ffff has been reserved
[   17.017119] system 00:08: iomem range 0xff380000-0xffefffff could not be reserved
[   17.017126] system 00:09: iomem range 0xfec00000-0xfec00fff has been reserved
[   17.017129] system 00:09: iomem range 0xfee00000-0xfee00fff could not be reserved
[   17.017137] system 00:0d: ioport range 0x680-0x6ff has been reserved
[   17.017140] system 00:0d: ioport range 0x295-0x296 has been reserved
[   17.017147] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[   17.017150] system 00:0e: iomem range 0xc0000-0xdffff could not be reserved
[   17.017152] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[   17.017155] system 00:0e: iomem range 0x100000-0x3fffffff could not be reserved
[   17.017158] system 00:0e: iomem range 0xfff00000-0xffffffff could not be reserved
[   17.047590] PCI: Bridge: 0000:00:01.0
[   17.047593]   IO window: disabled.
[   17.047599]   MEM window: f3d00000-f7dfffff
[   17.047604]   PREFETCH window: d3c00000-f3bfffff
[   17.047609] PCI: Bridge: 0000:00:1e.0
[   17.047613]   IO window: b000-bfff
[   17.047619]   MEM window: f7e00000-f7efffff
[   17.047623]   PREFETCH window: disabled.
[   17.047643] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   17.047657] NET: Registered protocol family 2
[   17.084978] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   17.085361] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   17.086150] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   17.086965] TCP: Hash tables configured (established 131072 bind 65536)
[   17.086970] TCP reno registered
[   17.097071] checking if image is initramfs... it is
[   17.507835] Switched to high resolution mode on CPU 0
[   17.727188] Freeing initrd memory: 7656k freed
[   17.727881] audit: initializing netlink socket (disabled)
[   17.727900] audit(1212787687.240:1): initialized
[   17.728123] highmem bounce pool size: 64 pages
[   17.730279] VFS: Disk quotas dquot_6.5.1
[   17.730368] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   17.730525] io scheduler noop registered
[   17.730528] io scheduler anticipatory registered
[   17.730530] io scheduler deadline registered
[   17.730543] io scheduler cfq registered (default)
[   17.730634] Boot video device is 0000:01:00.0
[   17.730959] isapnp: Scanning for PnP cards...
[   18.084169] isapnp: No Plug & Play device found
[   18.118631] Real Time Clock Driver v1.12ac
[   18.118746] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   18.118876] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   18.119043] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   18.119910] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   18.120786] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   18.120867] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   18.120996] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   18.123850] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.123855] serio: i8042 AUX port at 0x60,0x64 irq 12
[   18.126427] mice: PS/2 mouse device common for all mice
[   18.126569] EISA: Probing bus 0 at eisa.0
[   18.126606] EISA: Detected 0 cards.
[   18.126610] cpuidle: using governor ladder
[   18.126612] cpuidle: using governor menu
[   18.126720] NET: Registered protocol family 1
[   18.126760] Using IPI No-Shortcut mode
[   18.126797] registered taskstats version 1
[   18.126909]   Magic number: 12:603:499
[   18.127044] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   18.127046] EDD information not available.
[   18.127465] Freeing unused kernel memory: 368k freed
[   18.150852] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   19.392096] fuse init (API version 7.9)
[   19.417909] ACPI: Processor [CPU1] (supports 8 throttling states)
[   19.417931] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   19.417945] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   19.417957] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   20.060446] usbcore: registered new interface driver usbfs
[   20.060476] usbcore: registered new interface driver hub
[   20.068093] usbcore: registered new device driver usb
[   20.085200] USB Universal Host Controller Interface driver v3.0
[   20.085289] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   20.085303] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   20.085308] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   20.085708] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   20.085742] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000e000
[   20.085908] usb usb1: configuration #1 chosen from 1 choice
[   20.085936] hub 1-0:1.0: USB hub found
[   20.085944] hub 1-0:1.0: 2 ports detected
[   20.149270] SCSI subsystem initialized
[   20.189036] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   20.189053] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   20.189058] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   20.189086] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   20.189116] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000e400
[   20.189245] usb usb2: configuration #1 chosen from 1 choice
[   20.189273] hub 2-0:1.0: USB hub found
[   20.189280] hub 2-0:1.0: 2 ports detected
[   20.206053] 8139too Fast Ethernet driver 0.9.28
[   20.216435] libata version 3.00 loaded.
[   20.292753] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   20.292769] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   20.292774] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   20.292802] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   20.292832] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e800
[   20.292958] usb usb3: configuration #1 chosen from 1 choice
[   20.292988] hub 3-0:1.0: USB hub found
[   20.292995] hub 3-0:1.0: 2 ports detected
[   20.320419] FDC 0 is a post-1991 82077
[   20.396505] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
[   20.396522] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   20.396527] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   20.396556] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   20.396583] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ec00
[   20.396722] usb usb4: configuration #1 chosen from 1 choice
[   20.396750] hub 4-0:1.0: USB hub found
[   20.396757] hub 4-0:1.0: 2 ports detected
[   20.500406] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[   20.500426] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   20.500430] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   20.500465] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   20.504387] ehci_hcd 0000:00:1d.7: debug port 1
[   20.504394] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   20.504407] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xf7fffc00
[   20.520043] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   20.520189] usb usb5: configuration #1 chosen from 1 choice
[   20.520219] hub 5-0:1.0: USB hub found
[   20.520228] hub 5-0:1.0: 8 ports detected
[   20.624157] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 22 (level, low) -> IRQ 20
[   20.624858] eth0: RealTek RTL8139 at 0xb800, 00:19:66:51:8a:c5, IRQ 20
[   20.624861] eth0:  Identified 8139 chip type 'RTL-8101'
[   20.628734] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   20.634074] ata_piix 0000:00:1f.1: version 2.12
[   20.634097] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   20.634147] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   20.636923] scsi0 : ata_piix
[   20.638021] scsi1 : ata_piix
[   20.639484] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[   20.639487] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[   20.855760] ata1.00: ATA-6: ST3160022A, 4.04, max UDMA/100
[   20.855765] ata1.00: 312581808 sectors, multi 16: LBA48 
[   20.871598] ata1.00: configured for UDMA/100
[   21.346324] ata2.00: ATAPI: JLMS XJ-HD166S, DTS6, max UDMA/33
[   21.346351] ata2.01: ATAPI: _NEC DVD_RW ND-2500A, 1.0B, max UDMA/33
[   21.501858] ata2.00: configured for UDMA/33
[   21.673365] ata2.01: configured for UDMA/33
[   21.673514] scsi 0:0:0:0: Direct-Access     ATA      ST3160022A       4.04 PQ: 0 ANSI: 5
[   21.674216] scsi 1:0:0:0: CD-ROM            JLMS     XJ-HD166S        DTS6 PQ: 0 ANSI: 5
[   21.675263] scsi 1:0:1:0: CD-ROM            _NEC     DVD_RW ND-2500A  1.0B PQ: 0 ANSI: 5
[   21.675344] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[   21.675366] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 18
[   21.675420] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   21.675783] scsi2 : ata_piix
[   21.675963] scsi3 : ata_piix
[   21.676005] ata3: SATA max UDMA/133 cmd 0xd400 ctl 0xd000 bmdma 0xc400 irq 18
[   21.676008] ata4: SATA max UDMA/133 cmd 0xcc00 ctl 0xc800 bmdma 0xc408 irq 18
[   22.043112] ata4.00: ATA-7: ST3320820AS, 3.AFE, max UDMA/133
[   22.043118] ata4.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   22.109586] ata4.00: configured for UDMA/133
[   22.109745] scsi 3:0:0:0: Direct-Access     ATA      ST3320820AS      3.AF PQ: 0 ANSI: 5
[   22.127221] Driver 'sd' needs updating - please use bus_type methods
[   22.127332] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   22.127348] sd 0:0:0:0: [sda] Write Protect is off
[   22.127351] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.127374] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.127434] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   22.127446] sd 0:0:0:0: [sda] Write Protect is off
[   22.127449] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.127470] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.127474]  sda: sda1 sda2 sda3
[   22.135530] sd 0:0:0:0: [sda] Attached SCSI disk
[   22.135619] sd 3:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[   22.135634] sd 3:0:0:0: [sdb] Write Protect is off
[   22.135637] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   22.135660] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.135710] sd 3:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[   22.135722] sd 3:0:0:0: [sdb] Write Protect is off
[   22.135725] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   22.135746] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.135749]  sdb:<4>Driver 'sr' needs updating - please use bus_type methods
[   22.138249] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[   22.138255] Uniform CD-ROM driver Revision: 3.20
[   22.138324] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   22.141786] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   22.141861] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   22.165788]  sdb1
[   22.165872] sd 3:0:0:0: [sdb] Attached SCSI disk
[   22.180444] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   22.180470] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   22.180491] sr 1:0:1:0: Attached scsi generic sg2 type 5
[   22.180513] sd 3:0:0:0: Attached scsi generic sg3 type 0
[   22.767978] Attempting manual resume
[   22.767983] swsusp: Resume From Partition 8:1
[   22.767985] PM: Checking swsusp image.
[   22.775091] PM: Resume from disk failed.
[   22.814982] kjournald starting.  Commit interval 5 seconds
[   22.814998] EXT3-fs: mounted filesystem with ordered data mode.
[   31.758840] ip_tables: (C) 2000-2006 Netfilter Core Team
[   31.798417] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   32.620858] Linux agpgart interface v0.102
[   32.678283] agpgart: Detected an Intel 865 Chipset.
[   32.682623] agpgart: AGP aperture is 64M @ 0xf8000000
[   32.725857] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   32.776934] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   33.099625] intel_rng: FWH not detected
[   33.207355] iTCO_vendor_support: vendor-support=0
[   33.238514] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   33.238689] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0860)
[   33.238742] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   33.323207] input: Power Button (FF) as /devices/virtual/input/input2
[   33.342978] ACPI: Power Button (FF) [PWRF]
[   33.343158] input: Power Button (CM) as /devices/virtual/input/input3
[   33.354938] ACPI: Power Button (CM) [PWRB]
[   35.230261] nvidia: module license 'NVIDIA' taints kernel.
[   35.737336] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   35.836577] irda_init()
[   35.836604] NET: Registered protocol family 23
[   36.172830] parport_pc 00:07: reported by Plug and Play ACPI
[   36.172938] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   36.719263] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   36.719565] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   36.836998] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 21
[   36.837032] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   37.041575] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   37.157287] intel8x0_measure_ac97_clock: measured 55848 usecs
[   37.157292] intel8x0: clocking to 48000
[   38.637357] lp0: using parport0 (interrupt-driven).
[   38.700916] Adding 1461872k swap on /dev/sda1.  Priority:-1 extents:1 across:1461872k
[   39.089766] EXT3 FS on sda2, internal journal
[   39.223991] device-mapper: uevent: version 1.0.3
[   39.224029] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[   39.746634] kjournald starting.  Commit interval 5 seconds
[   39.746911] EXT3 FS on sda3, internal journal
[   39.746917] EXT3-fs: mounted filesystem with ordered data mode.
[   40.852959] No dock devices found.
[   42.173658] apm: BIOS version 1.2 Flags 0x02 (Driver version 1.16ac)
[   42.173665] apm: overridden by ACPI.
[   42.294977] ppdev: user-space parallel port driver
[   42.399468] audit(1212787711.883:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5040 profile="/usr/sbin/cupsd" namespace="default"
[   44.987016] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   45.109955] Bluetooth: Core ver 2.11
[   45.110798] NET: Registered protocol family 31
[   45.110804] Bluetooth: HCI device and connection manager initialized
[   45.110809] Bluetooth: HCI socket layer initialized
[   45.150794] Bluetooth: L2CAP ver 2.9
[   45.150800] Bluetooth: L2CAP socket layer initialized
[   45.244541] Bluetooth: RFCOMM socket layer initialized
[   45.244562] Bluetooth: RFCOMM TTY layer initialized
[   45.244565] Bluetooth: RFCOMM ver 1.8
[   47.693973] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   47.693996] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   47.694036] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   49.325766] NET: Registered protocol family 17
[   54.238177] NET: Registered protocol family 10
[   54.238840] lo: Disabled Privacy Extensions
[   64.969397] eth0: no IPv6 routers present
[   89.468679] Inbound IN=eth0 OUT= MAC=00:19:66:51:8a:c5:00:d0:2b:74:e5:8d:08:00 SRC=67.18.229.146 DST=77.100.101.128 LEN=60 TOS=0x00 PREC=0x00 TTL=49 ID=62831 DF PROTO=TCP SPT=51289 DPT=21 WINDOW=5840 RES=0x00 SYN URGP=0 
[   92.461156] Inbound IN=eth0 OUT= MAC=00:19:66:51:8a:c5:00:d0:2b:74:e5:8d:08:00 SRC=67.18.229.146 DST=77.100.101.128 LEN=60 TOS=0x00 PREC=0x00 TTL=49 ID=62833 DF PROTO=TCP SPT=51289 DPT=21 WINDOW=5840 RES=0x00 SYN URGP=0 
[  482.305829] Inbound IN=eth0 OUT= MAC=00:19:66:51:8a:c5:00:d0:2b:74:e5:8d:08:00 SRC=219.159.198.145 DST=77.100.101.128 LEN=404 TOS=0x00 PREC=0x00 TTL=114 ID=30534 PROTO=UDP SPT=3503 DPT=1434 LEN=384 
[  565.508182] Inbound IN=eth0 OUT= MAC=00:19:66:51:8a:c5:00:d0:2b:74:e5:8d:08:00 SRC=125.211.198.24 DST=77.100.101.128 LEN=485 TOS=0x00 PREC=0x00 TTL=45 ID=0 DF PROTO=UDP SPT=39179 DPT=1026 LEN=465 
[  565.508527] Inbound IN=eth0 OUT= MAC=00:19:66:51:8a:c5:00:d0:2b:74:e5:8d:08:00 SRC=125.211.198.24 DST=77.100.101.128 LEN=485 TOS=0x00 PREC=0x00 TTL=45 ID=0 DF PROTO=UDP SPT=39181 DPT=1027 LEN=465 

```

In case this info helps:

I have a separate /home partition on my regular hard drive.

The external is formatted to FAT32.

Thanks for your help. :)

---

### Post by ctrlER on 2008-06-06
It seems the drive is recognized as sdb and the partition as sdb1.
Try doing

```
sudo mkdir /media/newdisk
sudo mount /dev/sdb1 /media/newdisk
```

Then the contents of your drive should be accessible in the directory /media/newdisk.

---

### Post by spadewarrior on 2008-06-06
Nice one, that works. Will it stay there next time I boot up?

edit: apparently not. Is there anyway to get it to stick?

---

### Post by ctrlER on 2008-06-06
Yes. You have to add it to /etc/fstab.
```
sudo gedit /etc/fstab
```

and add the following line:

```
/dev/sdb1 /media/newdisk vfat defaults      0    0
```

---

### Post by spadewarrior on 2008-06-06
Thanks!

---

### Post by spadewarrior on 2008-06-06
There's just one problem. It's mounted as read-only. 

I've been looking at some fstab info but don't really understand it. What should I add to the command to allow me to write to it?

---

### Post by ctrlER on 2008-06-06
```
/dev/sdb1 /media/newdisk vfat umask=0000     0    0
```

Though is not really that safe.

---

### Post by spadewarrior on 2008-06-06
In what way? Could it crash? 

It's odd that it was writable when it was a usb drive.

---

### Post by ctrlER on 2008-06-06
It will not crash but it can be read/write by any user.
I think that when it was a usb drive it was automaticly mounted by udev and assigned to the running user.

---

### Post by redonwhite on 2008-06-06
> **spadewarrior said:**
> I'm not sure but it think it's fried. It's making a weird beeping noise every few seconds and xubuntu won't detect it. Is there any terminal command I can do to see if it's there/fix it?

[COLOR="SeaGreen"]Also, who actually makes reliable usb hard drives that work properly with linux?[/COLOR] Mine is a Seagate FreeAgent.

Thanks.

Hello.  Im using a WD passport 160gb usb HD.  Works Great with Ubuntu so far.

---

