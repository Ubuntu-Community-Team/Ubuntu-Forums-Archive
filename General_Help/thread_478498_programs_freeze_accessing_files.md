---
title: "programs freeze accessing files"
date: 2007-06-19
forum: General Help
---

### Post by schekn on 2007-06-19
I use Kubuntu on a Dell Inspiron 1300 notebook, there is a Windows XP partition and a Linux partition on the computer. Half a year ago I have installed some little program that would allow me to work with files on the Linux partition under Windows. It worked fine until last week when I restarted in Kubuntu and the Konqueror window of my Home folder appeared empty, it said No files No folders. When I tried closing the window  sign "the application is not responding" came up. The same thing happens with any other application that _shows_ files, like Gwenview or Kaffeine. 
I tried reinstalling most of the programs, reinstalled KDE, but nothing helps. 
I don't even know where to start. Is there any way to fix this without formatting this partition?

---

### Post by kuja on 2007-06-19
Sounds like an ugly problem indeed, why not run fsck on the partition and see what it says?

---

### Post by schekn on 2007-06-19
Restarted in recovery mode and ran fsck, it says "clean", no problems there though it does look like a filesystem trouble. When I boot from Knoppix the same thing happens: it just freezes as soon as I open my /home/user folder. All other folders OK. 
Any other suggestions? I would really appreciate it :)

---

### Post by kuja on 2007-06-19
The best thing I can think of is to check the system log at /var/log/dmesg, or perhaps /var/log/syslog.

I recommend attatching them in their entirety too.

---

### Post by schekn on 2007-06-19
files on my desktop crash kate too :( I had to put it right here..

var/log$ dmesg
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f000 end: 000000000009f000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f000 size: 0000000000001000 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001f6d3800 end: 000000001f7d3800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001f7d3800 size: 000000000082c800 end: 0000000020000000 type: 2
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010007000 end: 00000000f0007000 type: 2
[    0.000000] copy_e820_map() start: 00000000f0008000 size: 0000000000004000 end: 00000000f000c000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fed20000 size: 00000000000f0000 end: 00000000fee10000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffb00000 size: 0000000000500000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001f7d3800 (usable)
[    0.000000]  BIOS-e820: 000000001f7d3800 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0007000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 503MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 128979) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   128979
[    0.000000]   HighMem    128979 ->   128979
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   128979
[    0.000000] On node 0 totalpages: 128979
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 975 pages used for memmap
[    0.000000]   Normal zone: 123908 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fc970
[    0.000000] ACPI: RSDT (v001 DELL    D05     0x27d6041b ASL  0x00000061) @ 0x1f7d4425
[    0.000000] ACPI: FADT (v001 DELL    D05     0x27d6041b ASL  0x00000061) @ 0x1f7d4c00
[    0.000000] ACPI: MADT (v001 DELL    D05     0x27d6041b ASL  0x00000047) @ 0x1f7d5400
[    0.000000] ACPI: MCFG (v016 DELL    D05     0x27d6041b ASL  0x00000061) @ 0x1f7d53c0
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20030522) @ 0x1f7d4658
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20030522) @ 0x1f7d445d
[    0.000000] ACPI: DSDT (v001 INT430 SYSFexxx 0x00001001 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:13 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[    0.000000] Detected 1596.162 MHz processor.
[    6.307065] Built 1 zonelists.  Total pages: 127972
[    6.307070] Kernel command line: root=UUID=dd3c6a25-cbdc-425b-a174-fa8aa45aba57 ro quiet splash
[    6.307247] mapped APIC to ffffd000 (fee00000)
[    6.307249] mapped IOAPIC to ffffc000 (fec00000)
[    6.307253] Enabling fast FPU save and restore... done.
[    6.307256] Enabling unmasked SIMD FPU exception support... done.
[    6.307264] Initializing CPU#0
[    6.307341] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    6.309291] Console: colour VGA+ 80x25
[    6.309534] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    6.309785] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    6.323491] Memory: 500536k/515916k available (1992k kernel code, 14908k reserved, 900k data, 328k init, 0k highmem)
[    6.323501] virtual kernel memory layout:
[    6.323502]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[    6.323504]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    6.323505]     vmalloc : 0xe0000000 - 0xff7fe000   ( 503 MB)
[    6.323507]     lowmem  : 0xc0000000 - 0xdf7d3000   ( 503 MB)
[    6.323508]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[    6.323509]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[    6.323511]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[    6.323514] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    6.403267] Calibrating delay using timer specific routine.. 3195.67 BogoMIPS (lpj=6391352)
[    6.403310] Security Framework v1.0.0 initialized
[    6.403318] SELinux:  Disabled at boot.
[    6.403339] Mount-cache hash table entries: 512
[    6.403483] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000000 00000000 00000000
[    6.403497] CPU: L1 I cache: 32K, L1 D cache: 32K
[    6.403500] CPU: L2 cache: 1024K
[    6.403503] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002040 00000000 00000000 00000000
[    6.403513] Compat vDSO mapped to ffffe000.
[    6.403517] Remapping vsyscall page to ffffe000
[    6.403528] Checking 'hlt' instruction... OK.
[    6.419350] SMP alternatives: switching to UP code
[    6.419550] Freeing SMP alternatives: 11k freed
[    6.419737] Early unpacking initramfs... done
[    6.770803] ACPI: Core revision 20060707
[    6.778521] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[    6.780915] CPU0: Intel(R) Celeron(R) M processor         1.60GHz stepping 08
[    6.780941] Total of 1 processors activated (3195.67 BogoMIPS).
[    6.781128] ENABLING IO-APIC IRQs
[    6.781332] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    6.926861] Brought up 1 CPUs
[    6.927122] Booting paravirtualized kernel on bare hardware
[    6.927205] Time:  8:35:56  Date: 05/20/107
[    6.927237] NET: Registered protocol family 16
[    6.927329] EISA bus registered
[    6.927333] ACPI: bus type pci registered
[    6.957984] PCI: PCI BIOS revision 2.10 entry at 0xfba7e, last bus=13
[    6.957987] PCI: Using configuration type 1
[    6.957989] Setting up standard PCI resources
[    6.974303] ACPI: Interpreter enabled
[    6.974306] ACPI: Using IOAPIC for interrupt routing
[    6.975557] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    6.975567] PCI: Probing PCI hardware (bus 00)
[    6.975660] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[    6.989670] Boot video device is 0000:00:02.0
[    6.990262] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    6.990266] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
[    6.990670] PCI: Transparent bridge - 0000:00:1e.0
[    6.990729] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    7.009612] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    7.009879] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[    7.010146] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
[    7.010417] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 *7 9 10 11)
[    7.010670] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    7.010949] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    7.011207] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    7.011950] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    7.012263] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    7.012667] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    7.013100] Linux Plug and Play Support v0.97 (c) Adam Belay
[    7.013110] pnp: PnP ACPI init
[    7.045134] pnp: PnP ACPI: found 11 devices
[    7.045138] PnPBIOS: Disabled by ACPI PNP
[    7.045188] PCI: Using ACPI for IRQ routing
[    7.045192] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    7.071781] NET: Registered protocol family 8
[    7.071784] NET: Registered protocol family 20
[    7.088831] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    7.088835] pnp: 00:02: ioport range 0x1000-0x1005 could not be reserved
[    7.088838] pnp: 00:02: ioport range 0x1008-0x100f could not be reserved
[    7.088843] pnp: 00:03: ioport range 0xf400-0xf4fe has been reserved
[    7.088846] pnp: 00:03: ioport range 0x1006-0x1007 has been reserved
[    7.088849] pnp: 00:03: ioport range 0x100a-0x1059 could not be reserved
[    7.088852] pnp: 00:03: ioport range 0x1060-0x107f has been reserved
[    7.088855] pnp: 00:03: ioport range 0x1080-0x10bf has been reserved
[    7.088858] pnp: 00:03: ioport range 0x10c0-0x10df has been reserved
[    7.088865] pnp: 00:08: ioport range 0x900-0x90f has been reserved
[    7.088868] pnp: 00:08: ioport range 0x910-0x91f has been reserved
[    7.088871] pnp: 00:08: ioport range 0x920-0x92f has been reserved
[    7.088874] pnp: 00:08: ioport range 0x930-0x93f has been reserved
[    7.088876] pnp: 00:08: ioport range 0x940-0x97f has been reserved
[    7.089138] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[    7.089142] PCI: Bridge: 0000:00:1c.0
[    7.089144]   IO window: disabled.
[    7.089150]   MEM window: disabled.
[    7.089154]   PREFETCH window: disabled.
[    7.089160] PCI: Bridge: 0000:00:1c.3
[    7.089164]   IO window: d000-dfff
[    7.089170]   MEM window: dfc00000-dfdfffff
[    7.089175]   PREFETCH window: d0000000-d01fffff
[    7.089181] PCI: Bridge: 0000:00:1e.0
[    7.089182]   IO window: disabled.
[    7.089189]   MEM window: dfb00000-dfbfffff
[    7.089193]   PREFETCH window: disabled.
[    7.089226] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[    7.089234] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    7.089258] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 17
[    7.089264] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    7.089277] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    7.089305] NET: Registered protocol family 2
[    7.126715] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    7.126800] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    7.126914] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    7.126974] TCP: Hash tables configured (established 16384 bind 8192)
[    7.126977] TCP reno registered
[    7.138761] checking if image is initramfs... it is
[    7.822629] Freeing initrd memory: 6774k freed
[    7.823123] audit: initializing netlink socket (disabled)
[    7.823140] audit(1182328556.596:1): initialized
[    7.823284] VFS: Disk quotas dquot_6.5.1
[    7.823304] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    7.823360] io scheduler noop registered
[    7.823363] io scheduler anticipatory registered
[    7.823365] io scheduler deadline registered
[    7.823376] io scheduler cfq registered (default)
[    7.823643] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    7.823701] assign_interrupt_mode Found MSI capability
[    7.823705] Allocate Port Service[0000:00:1c.0:pcie00]
[    7.823743] Allocate Port Service[0000:00:1c.0:pcie02]
[    7.823862] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    7.823917] assign_interrupt_mode Found MSI capability
[    7.823921] Allocate Port Service[0000:00:1c.3:pcie00]
[    7.823951] Allocate Port Service[0000:00:1c.3:pcie02]
[    7.824131] isapnp: Scanning for PnP cards...
[    8.178127] isapnp: No Plug & Play device found
[    8.212044] Real Time Clock Driver v1.12ac
[    8.212109] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    8.212981] mice: PS/2 mouse device common for all mice
[    8.213553] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    8.213863] input: Macintosh mouse button emulation as /class/input/input0
[    8.213899] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    8.213903] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    8.214145] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    8.214278] i8042.c: Warning: Keylock active.
[    8.216566] serio: i8042 KBD port at 0x60,0x64 irq 1
[    8.216572] serio: i8042 AUX port at 0x60,0x64 irq 12
[    8.216716] EISA: Probing bus 0 at eisa.0
[    8.216726] Cannot allocate resource for EISA slot 1
[    8.216755] EISA: Detected 0 cards.
[    8.246839] TCP cubic registered
[    8.246849] NET: Registered protocol family 1
[    8.246874] Using IPI No-Shortcut mode
[    8.246960] ACPI: (supports S0 S3 S4 S5)
[    8.247009]   Magic number: 11:378:574
[    8.247106]   hash matches device ptyb6
[    8.247382] Freeing unused kernel memory: 328k freed
[    8.247971] input: AT Translated Set 2 keyboard as /class/input/input1
[    8.249680] Time: tsc clocksource has been installed.
[    9.478043] Capability LSM initialized
[    9.511760] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    9.511767] ACPI: Processor [CPU0] (supports 8 throttling states)
[    9.511775] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    9.516741] ACPI: Thermal Zone [THM] (72 C)
[    9.900794] usbcore: registered new interface driver usbfs
[    9.900818] usbcore: registered new interface driver hub
[    9.900843] usbcore: registered new device driver usb
[    9.901716] USB Universal Host Controller Interface driver v3.0
[    9.901767] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[    9.901780] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    9.901784] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    9.901951] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    9.901985] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000bf80
[    9.902094] usb usb1: configuration #1 chosen from 1 choice
[    9.902117] hub 1-0:1.0: USB hub found
[    9.902123] hub 1-0:1.0: 2 ports detected
[   10.004336] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 18
[   10.004351] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   10.004356] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   10.004378] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   10.004412] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000bf60
[   10.004515] usb usb2: configuration #1 chosen from 1 choice
[   10.004541] hub 2-0:1.0: USB hub found
[   10.004547] hub 2-0:1.0: 2 ports detected
[   10.108252] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[   10.108268] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   10.108273] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   10.108296] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   10.108331] uhci_hcd 0000:00:1d.2: irq 19, io base 0x0000bf40
[   10.108425] usb usb3: configuration #1 chosen from 1 choice
[   10.108452] hub 3-0:1.0: USB hub found
[   10.108458] hub 3-0:1.0: 2 ports detected
[    3.736000] Time: acpi_pm clocksource has been installed.
[    3.804000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 17
[    3.804000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.804000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.804000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.804000] uhci_hcd 0000:00:1d.3: irq 17, io base 0x0000bf20
[    3.804000] usb usb4: configuration #1 chosen from 1 choice
[    3.804000] hub 4-0:1.0: USB hub found
[    3.804000] hub 4-0:1.0: 2 ports detected
[    3.908000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 16 (level, low) -> IRQ 16
[    3.908000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.908000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.908000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.908000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.908000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.908000] ehci_hcd 0000:00:1d.7: irq 16, io mem 0xb0000000
[    3.912000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.912000] usb usb5: configuration #1 chosen from 1 choice
[    3.912000] hub 5-0:1.0: USB hub found
[    3.912000] hub 5-0:1.0: 8 ports detected
[    3.940000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    4.020000] SCSI subsystem initialized
[    4.028000] b44.c:v1.01 (Jun 16, 2006)
[    4.028000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 19
[    4.028000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:14:22:ab:39:ec
[    4.032000] libata version 2.20 loaded.
[    4.032000] ata_piix 0000:00:1f.1: version 2.10ac1
[    4.032000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[    4.032000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    4.032000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
[    4.032000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
[    4.032000] scsi0 : ata_piix
[    4.360000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    4.360000] ata1.00: ATA-7: FUJITSU MHV2080AH, 000000A0, max UDMA/100
[    4.360000] ata1.00: 156301488 sectors, multi 8: LBA
[    4.360000] ata1.01: ATAPI, max UDMA/33
[    4.372000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    4.372000] ata1.00: configured for UDMA/100
[    4.444000] usb 2-1: new low speed USB device using uhci_hcd and address 3
[    4.536000] ata1.01: configured for UDMA/33
[    4.536000] scsi1 : ata_piix
[    4.536000] ata2: port disabled. ignoring.
[    4.536000] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2080A 0000 PQ: 0 ANSI: 5
[    4.536000] scsi 0:0:1:0: CD-ROM            _NEC     DVD+-RW ND-6650A 102C PQ: 0 ANSI: 5
[    4.552000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    4.552000] sda: Write Protect is off
[    4.552000] sda: Mode Sense: 00 3a 00 00
[    4.552000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.552000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    4.552000] sda: Write Protect is off
[    4.552000] sda: Mode Sense: 00 3a 00 00
[    4.552000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.552000]  sda: sda1 sda2 < sda5<6>usb 2-1: configuration #1 chosen from 1 choice
[    4.624000] usbcore: registered new interface driver hiddev
[    4.624000]  sda6 >
[    4.624000] sd 0:0:0:0: Attached scsi disk sda
[    4.632000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.632000] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    4.636000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.636000] Uniform CD-ROM driver Revision: 3.20
[    4.636000] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    4.644000] input: PS/2+USB Mouse as /class/input/input2
[    4.644000] input: USB HID v1.00 Mouse [PS/2+USB Mouse] on usb-0000:00:1d.1-1
[    4.644000] usbcore: registered new interface driver usbhid
[    4.644000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[    4.856000] Attempting manual resume
[    4.856000] swsusp: Resume From Partition 8:5
[    4.856000] PM: Checking swsusp image.
[    4.856000] PM: Resume from disk failed.
[    4.888000] kjournald starting.  Commit interval 5 seconds
[    4.888000] EXT3-fs: mounted filesystem with ordered data mode.
[   16.064000] NET: Registered protocol family 17
[   16.304000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.308000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.764000] Linux agpgart interface v0.102 (c) Dave Jones
[   17.012000] agpgart: Detected an Intel 915GM Chipset.
[   17.012000] agpgart: Detected 7932K stolen memory.
[   17.032000] agpgart: AGP aperture is 256M @ 0xc0000000
[   17.040000] iTCO_vendor_support: vendor-support=0
[   17.040000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   17.040000] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   17.040000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   17.080000] intel_rng: FWH not detected
[   17.180000] input: PC Speaker as /class/input/input3
[   17.704000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   17.704000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   17.808000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x200000
[   17.836000] b44: eth0: Link is up at 100 Mbps, full duplex.
[   17.836000] b44: eth0: Flow control is off for TX and off for RX.
[   17.848000] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[   19.028000] hda_intel: azx_get_response timeout, switching to polling mode...
[   19.324000] fuse init (API version 7.8)
[   19.388000] lp: driver loaded but no devices found
[   19.412000] Adding 2104472k swap on /dev/disk/by-uuid/08397b55-9be3-49f5-b4e5-74ee44dd729a.  Priority:-1 extents:1 across:2104472k
[   19.552000] EXT3 FS on sda6, internal journal
[   19.724000] NET: Registered protocol family 10
[   19.724000] lo: Disabled Privacy Extensions
[   19.836000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   19.896000] NTFS volume version 3.1.
[   25.336000] ibm_acpi: ec object not found
[   25.396000] No dock devices found.
[   25.408000] Using specific hotkey driver
[   25.580000] input: Lid Switch as /class/input/input5
[   25.584000] ACPI: Lid Switch [LID]
[   25.624000] input: Power Button (CM) as /class/input/input6
[   25.628000] ACPI: Power Button (CM) [PBTN]
[   25.664000] input: Sleep Button (CM) as /class/input/input7
[   25.668000] ACPI: Sleep Button (CM) [SBTN]
[   25.960000] ACPI: Battery Slot [BAT0] (battery present)
[   25.972000] ACPI: AC Adapter [AC] (on-line)
[   25.988000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   25.988000] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   26.036000] pcc_acpi: loading...
[   27.984000] ppdev: user-space parallel port driver
[   28.756000] apm: BIOS not found.
[   29.500000] Bluetooth: Core ver 2.11
[   29.500000] NET: Registered protocol family 31
[   29.500000] Bluetooth: HCI device and connection manager initialized
[   29.500000] Bluetooth: HCI socket layer initialized
[   29.516000] Bluetooth: L2CAP ver 2.8
[   29.516000] Bluetooth: L2CAP socket layer initialized
[   29.616000] Bluetooth: RFCOMM socket layer initialized
[   29.616000] Bluetooth: RFCOMM TTY layer initialized
[   29.616000] Bluetooth: RFCOMM ver 1.8
[   30.872000] [drm] Initialized drm 1.1.0 20060810
[   30.876000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   30.880000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   41.996000] eth0: no IPv6 routers present
[ 7462.480000] Assertion failure in dx_probe() at fs/ext3/namei.c:384: "dx_get_limit(entries) == dx_root_limit(dir, root->info.info_length)"
[ 7462.480000] ------------[ cut here ]------------
[ 7462.480000] kernel BUG at fs/ext3/namei.c:384!
[ 7462.480000] invalid opcode: 0000 [#1]
[ 7462.480000] SMP
[ 7462.480000] Modules linked in: i915 drm binfmt_misc rfcomm l2cap bluetooth ppdev cpufreq_stats cpufreq_powersave cpufreq_conservative cpufreq_userspace cpufreq_ondemand freq_table tc1100_wmi dev_acpi pcc_acpi sony_acpi video ac battery button container sbs i2c_ec i2c_core dock asus_acpi backlight nls_utf8 ntfs ipv6 parport_pc lp parport fuse joydev snd_hda_intel snd_hda_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device serio_raw pcspkr psmouse iTCO_wdt iTCO_vendor_support intel_agp snd soundcore snd_page_alloc agpgart shpchp pci_hotplug af_packet evdev tsdev ext3 jbd mbcache sg usbhid hid sr_mod cdrom sd_mod ata_generic ata_piix libata scsi_mod b44 mii generic ehci_hcd uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap
[ 7462.480000] CPU:    0
[ 7462.480000] EIP:    0060:[<e0188b51>]    Not tainted VLI
[ 7462.480000] EFLAGS: 00010282   (2.6.20-16-generic #2)
[ 7462.480000] EIP is at dx_probe+0x1e1/0x320 [ext3]
[ 7462.480000] eax: 00000090   ebx: d1cb8000   ecx: 00000082   edx: 00000000
[ 7462.480000] esi: d1cb8018   edi: d998bd30   ebp: cacc06c0   esp: d21d3ce0
[ 7462.480000] ds: 007b   es: 007b   ss: 0068
[ 7462.480000] Process kate (pid: 5631, ti=d21d2000 task=c0dcb030 task.ti=d21d2000)
[ 7462.480000] Stack: e0194f28 e019426b e0196d6d 00000180 e0195078 d21d3dcc 00000000 d1cd3fe4
[ 7462.480000]        b3aa3e4e df5fd800 d21d3ddc d21d3db4 d21d3e70 e018974b d21d3db4 d21d3ddc
[ 7462.480000]        00000000 b5bf9000 deb71ba8 ca5f8740 00000000 c59513ec 00000000 df5fda00
[ 7462.480000] Call Trace:
[ 7462.480000]  [<e018974b>] ext3_find_entry+0x28b/0x640 [ext3]
[ 7462.480000]  [<e0183f0e>] __ext3_get_inode_loc+0x11e/0x340 [ext3]
[ 7462.480000]  [<e0149734>] journal_stop+0x164/0x1f0 [jbd]
[ 7462.480000]  [<e0184202>] ext3_mark_inode_dirty+0x32/0x50 [ext3]
[ 7462.480000]  [<e018b20c>] ext3_lookup+0x3c/0x100 [ext3]
[ 7462.480000]  [<c0188217>] d_alloc+0x107/0x190
[ 7462.480000]  [<c017dd98>] do_lookup+0x148/0x190
[ 7462.480000]  [<c017fcf7>] __link_path_walk+0x867/0xe70
[ 7462.480000]  [<c0180345>] link_path_walk+0x45/0xc0
[ 7462.480000]  [<c02f07bf>] do_page_fault+0x33f/0x5f0
[ 7462.480000]  [<c01805a3>] do_path_lookup+0x83/0x1c0
[ 7462.480000]  [<c017f2b7>] getname+0xa7/0xd0
[ 7462.480000]  [<c0180fab>] __user_walk_fd+0x3b/0x60
[ 7462.480000]  [<c017558b>] sys_faccessat+0x9b/0x150
[ 7462.480000]  [<c02f07bf>] do_page_fault+0x33f/0x5f0
[ 7462.480000]  [<c017565f>] sys_access+0x1f/0x30
[ 7462.480000]  [<c01031f0>] sysenter_past_esp+0x69/0xa9
[ 7462.480000]  =======================
[ 7462.480000] Code: 44 24 10 78 50 19 e0 c7 44 24 0c 80 01 00 00 c7 44 24 08 6d 6d 19 e0 c7 44 24 04 6b 42 19 e0 c7 04 24 28 4f 19 e0 e8 bf e0 f9 df <0f> 0b eb fe 89 44 24 0c c7 44 24 08 50 50 19 e0 c7 44 24 04 6b
[ 7462.480000] EIP: [<e0188b51>] dx_probe+0x1e1/0x320 [ext3] SS:ESP 0068:d21d3ce0
[ 7462.480000]

---

