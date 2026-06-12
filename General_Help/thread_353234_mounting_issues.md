---
title: "mounting issues"
date: 2007-02-04
forum: General Help
---

### Post by jessej on 2007-02-04
Hello everyone,

I just installed Ubuntu 6.10 this morning and I am having issues accessing my 3 CD-Rom drives.  The data DVD I put in Drive 1 doesn't even start and when I select it I get the error message: *Unable to mount the selected volume. mount: special device /dev/hdb does not exist*
I am brand new to Linux and know nothing about how the mounting process works.  If someone could help that would be great.
Thanks!

---

### Post by taurus on 2007-02-04
What's the output of this command from a terminal after you have inserted the CD/DVD into a drive?

```
dmesg | tail
```

---

### Post by jessej on 2007-02-04
Output:

[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 511MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f4770
[17179569.184000] On node 0 totalpages: 131056
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126960 pages, LIFO batch:31
[17179569.184000] DMI 2.2 present.
[17179569.184000] ACPI: RSDP (v000 AWARD                                 ) @ 0x000f61b0
[17179569.184000] ACPI: RSDT (v001 AWARD  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3000
[17179569.184000] ACPI: FADT (v001 AWARD  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3040
[17179569.184000] ACPI: MADT (v001 AWARD  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff6ec0
[17179569.184000] ACPI: DSDT (v001 AWARD  AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:2 APIC version 20
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 20, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 1593.785 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179571.468000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.468000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179571.488000] Memory: 509800k/524224k available (1910k kernel code, 13840k reserved, 1070k data, 308k init, 0k highmem)
[17179571.488000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179571.568000] Calibrating delay using timer specific routine.. 3191.20 BogoMIPS (lpj=6382409)
[17179571.568000] Security Framework v1.0.0 initialized
[17179571.568000] SELinux:  Disabled at boot.
[17179571.568000] Mount-cache hash table entries: 512
[17179571.568000] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
[17179571.568000] CPU: After vendor identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
[17179571.568000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[17179571.568000] CPU: L2 cache: 512K
[17179571.568000] CPU: Hyper-Threading is disabled
[17179571.568000] CPU: After all inits, caps: 3febfbff 00000000 00000000 00000080 00000000 00000000 00000000
[17179571.568000] Checking 'hlt' instruction... OK.
[17179571.584000] SMP alternatives: switching to UP code
[17179571.584000] Freeing SMP alternatives: 16k freed
[17179571.584000] checking if image is initramfs... it is
[17179572.432000] Freeing initrd memory: 5564k freed
[17179572.432000] ACPI: Core revision 20060707
[17179572.440000] ACPI: Looking for DSDT ... not found!
[17179572.444000] CPU0: Intel(R) Pentium(R) 4 CPU 1.60GHz stepping 04
[17179572.444000] Total of 1 processors activated (3191.20 BogoMIPS).
[17179572.444000] ENABLING IO-APIC IRQs
[17179572.444000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179572.588000] Brought up 1 CPUs
[17179572.588000] migration_cost=0
[17179572.588000] NET: Registered protocol family 16
[17179572.588000] EISA bus registered
[17179572.588000] ACPI: bus type pci registered
[17179572.608000] PCI: PCI BIOS revision 2.10 entry at 0xfb390, last bus=2
[17179572.608000] PCI: Using configuration type 1
[17179572.608000] Setting up standard PCI resources
[17179572.624000] ACPI: Interpreter enabled
[17179572.624000] ACPI: Using IOAPIC for interrupt routing
[17179572.624000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179572.624000] PCI: Probing PCI hardware (bus 00)
[17179572.624000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179572.628000] Uncovering SIS961 that hid as a SIS503 (compatible=1)
[17179572.628000] Enabling SiS 96x SMBus.
[17179572.628000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:02.5
[17179572.628000] Boot video device is 0000:01:00.0
[17179572.632000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179572.672000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179572.672000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179572.672000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179572.672000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
[17179572.672000] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 6 7 10 11 12 14 15)
[17179572.672000] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 6 7 10 11 12 14 15)
[17179572.672000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179572.672000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179572.680000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179572.680000] pnp: PnP ACPI init
[17179572.684000] pnp: PnP ACPI: found 14 devices
[17179572.684000] PnPBIOS: Disabled by ACPI PNP
[17179572.684000] PCI: Using ACPI for IRQ routing
[17179572.684000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179572.784000] PCI: Bridge: 0000:00:01.0
[17179572.784000]   IO window: disabled.
[17179572.784000]   MEM window: e6000000-e7ffffff
[17179572.784000]   PREFETCH window: e4000000-e5ffffff
[17179572.784000] PCI: Bridge: 0000:00:09.0
[17179572.784000]   IO window: disabled.
[17179572.784000]   MEM window: e9000000-e90fffff
[17179572.784000]   PREFETCH window: disabled.
[17179572.784000] NET: Registered protocol family 2
[17179572.820000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179572.820000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179572.820000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179572.820000] TCP: Hash tables configured (established 16384 bind 8192)
[17179572.820000] TCP reno registered
[17179572.820000] audit: initializing netlink socket (disabled)
[17179572.820000] audit(1170575442.820:1): initialized
[17179572.820000] VFS: Disk quotas dquot_6.5.1
[17179572.820000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.820000] Initializing Cryptographic API
[17179572.820000] io scheduler noop registered
[17179572.820000] io scheduler anticipatory registered
[17179572.820000] io scheduler deadline registered
[17179572.820000] io scheduler cfq registered (default)
[17179572.820000] isapnp: Scanning for PnP cards...
[17179573.176000] isapnp: No Plug & Play device found
[17179573.212000] Real Time Clock Driver v1.12ac
[17179573.212000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179573.212000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.212000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.216000] mice: PS/2 mouse device common for all mice
[17179573.216000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179573.216000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.216000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179573.216000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179573.216000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179573.216000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.216000] EISA: Probing bus 0 at eisa.0
[17179573.216000] Cannot allocate resource for EISA slot 1
[17179573.216000] Cannot allocate resource for EISA slot 4
[17179573.216000] EISA: Detected 0 cards.
[17179573.216000] TCP bic registered
[17179573.216000] NET: Registered protocol family 1
[17179573.216000] NET: Registered protocol family 8
[17179573.216000] NET: Registered protocol family 20
[17179573.216000] Using IPI No-Shortcut mode
[17179573.216000] ACPI: (supports S0 S1 S4 S5)
[17179573.216000] Freeing unused kernel memory: 308k freed
[17179573.244000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179574.368000] Capability LSM initialized
[17179574.424000] ACPI: Fan [FAN] (on)
[17179574.432000] ACPI: Thermal Zone [THRM] (21 C)
[17179575.160000] SIS5513: IDE controller at PCI slot 0000:00:02.5
[17179575.160000] SIS5513: chipset revision 208
[17179575.160000] SIS5513: not 100% native mode: will probe irqs later
[17179575.160000] SIS5513: SiS 961 MuTIOL IDE UDMA100 controller
[17179575.160000]     ide0: BM-DMA at 0x4000-0x4007, BIOS settings: hda:DMA, hdb:DMA
[17179575.160000]     ide1: BM-DMA at 0x4008-0x400f, BIOS settings: hdc:DMA, hdd:DMA
[17179575.160000] Probing IDE interface ide0...
[17179575.456000] hda: WDC WD400BB-00DEA0, ATA DISK drive
[17179575.908000] hdb: LITE-ON DVDRW SHM-165P6S, ATAPI CD/DVD-ROM drive
[17179575.968000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179576.000000] Probing IDE interface ide1...
[17179576.736000] hdc: LITEON DVD-ROM LTD163D, ATAPI CD/DVD-ROM drive
[17179577.524000] hdd: LITE-ON LTR-32123S, ATAPI CD/DVD-ROM drive
[17179577.584000] ide1 at 0x170-0x177,0x376 on irq 15
[17179577.596000] hda: max request size: 128KiB
[17179577.608000] BUG: unable to handle kernel paging request at virtual address 00002000
[17179577.608000]  printing eip:
[17179577.608000] e0852007
[17179577.608000] *pde = 00000000
[17179577.608000] Oops: 0002 [#1]
[17179577.608000] SMP 
[17179577.608000] Modules linked in: cdrom ide_disk sis5513 generic thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap
[17179577.608000] CPU:    0
[17179577.608000] EIP:    0060:[<e0852007>]    Not tainted VLI
[17179577.608000] EFLAGS: 00010206   (2.6.17-10-generic #2) 
[17179577.608000] EIP is at cdrom_init+0x7/0x8 [cdrom]
[17179577.608000] eax: 00002000   ebx: e0874e80   ecx: 00000000   edx: e0874e80
[17179577.608000] esi: e0874e80   edi: dfab0cd0   ebp: 00000500   esp: dfe29ed4
[17179577.608000] ds: 007b   es: 007b   ss: 0068
[17179577.608000] Process modprobe (pid: 1618, threadinfo=dfe28000 task=dfbf9a90)
[17179577.608000] Stack: c013cda8 e0874ec8 c02f1471 e0874e8c dfcdda3c 00007e82 0000009b e0874e8c 
[17179577.608000]        e0874e80 00000000 00000000 00000000 00000000 0000000e 00000000 00000000 
[17179577.608000]        00000010 00000000 0000000b 0000001e e0869f94 defcbd00 b7dd0000 e0867444 
[17179577.608000] Call Trace:
[17179577.608000]  <c013cda8> sys_init_module+0x148/0x19c0  <c01670e0> __kmalloc+0x0/0x90
[17179577.608000]  <c0103027> syscall_call+0x7/0xb 
[17179577.608000] Code:  Bad EIP value.
[17179577.608000] EIP: [<e0852007>] cdrom_init+0x7/0x8 [cdrom] SS:ESP 0068:dfe29ed4
[17179577.608000]  <6>hda: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[17179577.636000] hda: cache flushes not supported
[17179577.636000]  hda: hda1 hda2 < hda5 >
[17179757.748000] usbcore: registered new driver usbfs
[17179757.748000] usbcore: registered new driver hub
[17179757.752000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179757.752000] ACPI: PCI Interrupt 0000:00:02.2[D] -> GSI 20 (level, low) -> IRQ 169
[17179757.752000] ohci_hcd 0000:00:02.2: OHCI Host Controller
[17179757.756000] ohci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
[17179757.756000] ohci_hcd 0000:00:02.2: irq 169, io mem 0xe9101000
[17179757.780000] USB Universal Host Controller Interface driver v3.0
[17179757.816000] usb usb1: configuration #1 chosen from 1 choice
[17179757.816000] hub 1-0:1.0: USB hub found
[17179757.816000] hub 1-0:1.0: 3 ports detected
[17179757.884000] ieee1394: Initialized config rom entry `ip1394'
[17179757.920000] ACPI: PCI Interrupt 0000:00:02.3[A] -> GSI 23 (level, low) -> IRQ 177
[17179757.920000] ohci_hcd 0000:00:02.3: OHCI Host Controller
[17179757.920000] ohci_hcd 0000:00:02.3: new USB bus registered, assigned bus number 2
[17179757.920000] ohci_hcd 0000:00:02.3: irq 177, io mem 0xe9103000
[17179757.980000] usb usb2: configuration #1 chosen from 1 choice
[17179757.980000] hub 2-0:1.0: USB hub found
[17179757.980000] hub 2-0:1.0: 3 ports detected
[17179758.084000] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 18 (level, low) -> IRQ 185
[17179758.084000] ohci_hcd 0000:02:08.0: OHCI Host Controller
[17179758.084000] ohci_hcd 0000:02:08.0: new USB bus registered, assigned bus number 3
[17179758.084000] ohci_hcd 0000:02:08.0: irq 185, io mem 0xe9007000
[17179758.084000] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 17 (level, low) -> IRQ 193
[17179758.084000] PCI: Via IRQ fixup for 0000:00:08.0, from 11 to 1
[17179758.084000] uhci_hcd 0000:00:08.0: UHCI Host Controller
[17179758.084000] uhci_hcd 0000:00:08.0: new USB bus registered, assigned bus number 4
[17179758.084000] uhci_hcd 0000:00:08.0: irq 193, io base 0x0000d800
[17179758.084000] usb usb4: configuration #1 chosen from 1 choice
[17179758.084000] hub 4-0:1.0: USB hub found
[17179758.084000] hub 4-0:1.0: 2 ports detected
[17179758.188000] ACPI: PCI Interrupt 0000:00:08.1[B] -> GSI 18 (level, low) -> IRQ 185
[17179758.188000] PCI: Via IRQ fixup for 0000:00:08.1, from 11 to 9
[17179758.188000] uhci_hcd 0000:00:08.1: UHCI Host Controller
[17179758.188000] uhci_hcd 0000:00:08.1: new USB bus registered, assigned bus number 5
[17179758.188000] uhci_hcd 0000:00:08.1: irq 185, io base 0x0000dc00
[17179758.188000] usb usb5: configuration #1 chosen from 1 choice
[17179758.188000] hub 5-0:1.0: USB hub found
[17179758.188000] hub 5-0:1.0: 2 ports detected
[17179758.292000] usb usb3: configuration #1 chosen from 1 choice
[17179758.292000] hub 3-0:1.0: USB hub found
[17179758.292000] hub 3-0:1.0: 3 ports detected
[17179758.396000] ACPI: PCI Interrupt 0000:02:08.1[B] -> GSI 19 (level, low) -> IRQ 201
[17179758.396000] ohci_hcd 0000:02:08.1: OHCI Host Controller
[17179758.396000] ohci_hcd 0000:02:08.1: new USB bus registered, assigned bus number 6
[17179758.396000] ohci_hcd 0000:02:08.1: irq 201, io mem 0xe9004000
[17179758.484000] usb usb6: configuration #1 chosen from 1 choice
[17179758.484000] hub 6-0:1.0: USB hub found
[17179758.484000] hub 6-0:1.0: 2 ports detected
[17179758.596000] ACPI: PCI Interrupt 0000:00:08.2[C] -> GSI 19 (level, low) -> IRQ 201
[17179758.596000] ehci_hcd 0000:00:08.2: EHCI Host Controller
[17179758.596000] ehci_hcd 0000:00:08.2: new USB bus registered, assigned bus number 7
[17179758.596000] ehci_hcd 0000:00:08.2: irq 201, io mem 0xe9100000
[17179758.596000] ehci_hcd 0000:00:08.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179758.596000] usb usb7: configuration #1 chosen from 1 choice
[17179758.596000] hub 7-0:1.0: USB hub found
[17179758.596000] hub 7-0:1.0: 4 ports detected
[17179758.700000] ACPI: PCI Interrupt 0000:02:08.2[C] -> GSI 16 (level, low) -> IRQ 209
[17179758.700000] ehci_hcd 0000:02:08.2: EHCI Host Controller
[17179758.700000] ehci_hcd 0000:02:08.2: new USB bus registered, assigned bus number 8
[17179758.724000] ehci_hcd 0000:02:08.2: irq 209, io mem 0xe9005000
[17179758.724000] ehci_hcd 0000:02:08.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179758.724000] usb usb8: configuration #1 chosen from 1 choice
[17179758.724000] hub 8-0:1.0: USB hub found
[17179758.724000] hub 8-0:1.0: 5 ports detected
[17179758.832000] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 19 (level, low) -> IRQ 201
[17179758.880000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[201]  MMIO=[e9006000-e90067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[17179758.952000] Attempting manual resume
[17179758.992000] kjournald starting.  Commit interval 5 seconds
[17179758.992000] EXT3-fs: mounted filesystem with ordered data mode.
[17179759.108000] ide_cd: Unknown symbol register_cdrom
[17179759.108000] ide_cd: Unknown symbol cdrom_ioctl
[17179759.108000] ide_cd: Unknown symbol cdrom_mode_select
[17179759.108000] ide_cd: Unknown symbol cdrom_media_changed
[17179759.108000] ide_cd: Unknown symbol cdrom_get_last_written
[17179759.108000] ide_cd: Unknown symbol cdrom_mode_sense
[17179759.108000] ide_cd: Unknown symbol cdrom_get_media_event
[17179759.108000] ide_cd: Unknown symbol cdrom_release
[17179759.108000] ide_cd: Unknown symbol cdrom_open
[17179759.112000] ide_cd: Unknown symbol unregister_cdrom
[17179759.112000] ide_cd: Unknown symbol cdrom_number_of_slots
[17179759.112000] ide_cd: Unknown symbol init_cdrom_command
[17179759.112000] ide_cd: Unknown symbol register_cdrom
[17179759.112000] ide_cd: Unknown symbol cdrom_ioctl
[17179759.112000] ide_cd: Unknown symbol cdrom_mode_select
[17179759.112000] ide_cd: Unknown symbol cdrom_media_changed
[17179759.112000] ide_cd: Unknown symbol cdrom_get_last_written
[17179759.112000] ide_cd: Unknown symbol cdrom_mode_sense
[17179759.112000] ide_cd: Unknown symbol cdrom_get_media_event
[17179759.112000] ide_cd: Unknown symbol cdrom_release
[17179759.112000] ide_cd: Unknown symbol cdrom_open
[17179759.112000] ide_cd: Unknown symbol unregister_cdrom
[17179759.112000] ide_cd: Unknown symbol cdrom_number_of_slots
[17179759.112000] ide_cd: Unknown symbol init_cdrom_command
[17179759.112000] ide_cd: Unknown symbol register_cdrom
[17179759.112000] ide_cd: Unknown symbol cdrom_ioctl
[17179759.112000] ide_cd: Unknown symbol cdrom_mode_select
[17179759.112000] ide_cd: Unknown symbol cdrom_media_changed
[17179759.112000] ide_cd: Unknown symbol cdrom_get_last_written
[17179759.112000] ide_cd: Unknown symbol cdrom_mode_sense
[17179759.112000] ide_cd: Unknown symbol cdrom_get_media_event
[17179759.116000] ide_cd: Unknown symbol cdrom_release
[17179759.116000] ide_cd: Unknown symbol cdrom_open
[17179759.116000] ide_cd: Unknown symbol unregister_cdrom
[17179759.116000] ide_cd: Unknown symbol cdrom_number_of_slots
[17179759.116000] ide_cd: Unknown symbol init_cdrom_command
[17179760.152000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[700050c5000029b7]
[17179769.564000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179769.568000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179770.188000] Linux agpgart interface v0.101 (c) Dave Jones
[17179770.192000] agpgart: Detected SiS 650 chipset
[17179770.196000] agpgart: AGP aperture is 64M @ 0xe0000000
[17179770.220000] 8139too Fast Ethernet driver 0.9.27
[17179770.220000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> GSI 18 (level, low) -> IRQ 185
[17179770.220000] eth0: RealTek RTL8139 at 0xe09be000, 00:e0:4c:7c:85:be, IRQ 185
[17179770.220000] eth0:  Identified 8139 chip type 'RTL-8100'
[17179770.288000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179770.332000] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x1080
[17179771.148000] input: PC Speaker as /class/input/input1
[17179771.164000] Floppy drive(s): fd0 is 1.44M
[17179771.184000] FDC 0 is a post-1991 82077
[17179771.236000] parport: PnPBIOS parport detected.
[17179771.236000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[17179771.556000] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[17179771.616000] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 21 (level, low) -> IRQ 217
[17179771.932000] intel8x0_measure_ac97_clock: measured 55083 usecs
[17179771.932000] intel8x0: clocking to 48000
[17179772.172000] eth0: link down
[17179772.180000] ts: Compaq touchscreen protocol output
[17179773.312000] NET: Registered protocol family 17
[17179949.116000] lp0: using parport0 (interrupt-driven).
[17179949.184000] SCSI subsystem initialized
[17179949.192000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179949.192000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179949.244000] Adding 1502036k swap on /dev/disk/by-uuid/be5b9b29-bcbf-4a2f-8725-2361c5f84765.  Priority:-1 extents:1 across:1502036k
[17179949.304000] EXT3 FS on hda1, internal journal
[17179955.916000] ACPI: Power Button (FF) [PWRF]
[17179955.916000] ACPI: Power Button (CM) [PWRB]
[17179955.916000] ACPI: Sleep Button (CM) [FUTS]
[17179956.104000] ibm_acpi: ec object not found
[17179956.144000] pcc_acpi: loading...
[17179959.692000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179959.692000] apm: overridden by ACPI.
[17179965.632000] Bluetooth: Core ver 2.8
[17179965.632000] NET: Registered protocol family 31
[17179965.632000] Bluetooth: HCI device and connection manager initialized
[17179965.632000] Bluetooth: HCI socket layer initialized
[17179965.672000] Bluetooth: L2CAP ver 2.8
[17179965.672000] Bluetooth: L2CAP socket layer initialized
[17179965.700000] Bluetooth: RFCOMM socket layer initialized
[17179965.700000] Bluetooth: RFCOMM TTY layer initialized
[17179965.700000] Bluetooth: RFCOMM ver 1.7
[17180009.420000] NET: Registered protocol family 10
[17180009.420000] lo: Disabled Privacy Extensions
[17180009.420000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17180009.420000] IPv6 over IPv4 tunneling driver
[17180182.584000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[17180182.584000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[17180192.908000] eth0: no IPv6 routers present
[17181349.476000] ieee1394: Error parsing configrom for node 0-00:1023
[17181349.476000] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[17184103.644000] end_request: I/O error, dev fd0, sector 0
[17184103.676000] end_request: I/O error, dev fd0, sector 0
[17184103.708000] end_request: I/O error, dev fd0, sector 0
[17184103.740000] end_request: I/O error, dev fd0, sector 0
[17184103.824000] end_request: I/O error, dev fd0, sector 0
[17184103.856000] end_request: I/O error, dev fd0, sector 0
[17184103.888000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17184103.916000] end_request: I/O error, dev fd0, sector 0
[17184103.948000] end_request: I/O error, dev fd0, sector 0
[17184104.004000] end_request: I/O error, dev fd0, sector 0
[17184104.036000] end_request: I/O error, dev fd0, sector 0
[17184104.080000] end_request: I/O error, dev fd0, sector 0
[17184104.112000] end_request: I/O error, dev fd0, sector 0
[17184104.144000] end_request: I/O error, dev fd0, sector 0
[17184104.176000] end_request: I/O error, dev fd0, sector 0
[17184104.236000] end_request: I/O error, dev fd0, sector 0
[17184104.268000] end_request: I/O error, dev fd0, sector 0
[17184104.336000] end_request: I/O error, dev fd0, sector 0
[17184104.368000] end_request: I/O error, dev fd0, sector 0
[17184104.508000] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[17184104.508000] SGI XFS Quota Management subsystem
[17184104.536000] end_request: I/O error, dev fd0, sector 0
[17184104.568000] end_request: I/O error, dev fd0, sector 0
[17184104.608000] JFS: nTxBlock = 4030, nTxLock = 32243
[17184104.640000] end_request: I/O error, dev fd0, sector 0
[17184104.672000] end_request: I/O error, dev fd0, sector 0
[17189282.120000] usb 8-5: new high speed USB device using ehci_hcd and address 2
[17189282.256000] usb 8-5: configuration #1 chosen from 2 choices
[17189335.808000] usb 8-5: USB disconnect, address 2

---

### Post by taurus on 2007-02-04
And what about your /etc/fstab?

```
cat /etc/fstab
```

---

### Post by jessej on 2007-02-04
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=4b76b960-4208-4649-ab3b-fdc01eef3c6e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=be5b9b29-bcbf-4a2f-8725-2361c5f84765 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom2   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by taurus on 2007-02-04
What happens if you insert the DVD into the second drive, /dev/hdc?  Does it start or can you mount it?  What's the output of this command?

```
ls -la /dev/hdb
```

---

### Post by jessej on 2007-02-04
nothing happens.

bash: ls-la/dev/hdb: No such file or directory

---

### Post by taurus on 2007-02-04
So the DVD won't work in all three drives?

Well, it knows you have three DVD drives because it sees them here...

```

hdb: LITE-ON DVDRW SHM-165P6S, ATAPI CD/DVD-ROM drive
hdc: LITEON DVD-ROM LTD163D, ATAPI CD/DVD-ROM drive
hdd: LITE-ON LTR-32123S, ATAPI CD/DVD-ROM drive

```

What kind of DVD is it anyway?

---

### Post by jessej on 2007-02-04
it is a data DVD containing files from my old computer.

---

### Post by bronzefury on 2007-08-26
Hi,

I just like to report that I'm getting a similar problem when running Xubuntu on a Toshiba Satellite 2590CDT.  I get these kinds of messages in "dmesg"..

[ 4201.129714] ide_cd: Unknown symbol register_cdrom
[ 4201.130101] ide_cd: Unknown symbol cdrom_ioctl
[ 4201.131810] ide_cd: Unknown symbol cdrom_mode_select
[ 4201.132755] ide_cd: Unknown symbol cdrom_media_changed
[ 4201.133077] ide_cd: Unknown symbol cdrom_get_last_written
[ 4201.133780] ide_cd: Unknown symbol cdrom_mode_sense
[ 4201.134519] ide_cd: Unknown symbol cdrom_get_media_event
[ 4201.135464] ide_cd: Unknown symbol cdrom_release
[ 4201.136556] ide_cd: Unknown symbol cdrom_open
[ 4201.137782] ide_cd: Unknown symbol unregister_cdrom

My CD-ROM is recognized but I suspect that driver modules aren't getting loaded.

Help,
bronzefury

---

### Post by bronzefury on 2007-08-26
Btw, I'm running Xubuntu Feisty Fawn

[00:55:00]>uname -a
Linux xubuntulaptop 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux
[00:55:02]>

[ 4198.616682] PIIX4: not 100% native mode: will probe irqs later
[ 4198.616767]     ide0: BM-DMA at 0xfe60-0xfe67, BIOS settings: hda:DMA, hdb:pio
[ 4198.618021]     ide1: BM-DMA at 0xfe68-0xfe6f, BIOS settings: hdc:DMA, hdd:pio
[ 4198.618195] Probing IDE interface ide0...
[ 4198.863825] usbcore: registered new interface driver usbfs
[ 4198.864000] usbcore: registered new interface driver hub
[ 4198.864251] usbcore: registered new device driver usb
[ 4198.871931] USB Universal Host Controller Interface driver v3.0
[ 4198.972246] hda: TOSHIBA MK6411MAT, ATA DISK drive
[ 4199.644035] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[ 4199.644347] Probing IDE interface ide1...
**[ 4200.379734] hdc: CD-224E, ATAPI CD/DVD-ROM drive**
[ 4201.051802] ide1 at 0x170-0x177,0x376 on irq 15

Any help would be greatly appreciated...
bronzefury

P.s. my floppy drive can't be seen either,.. but I want to deal with the CD-ROM first.

---

