---
title: "My system has slowed to a crawl and lost all internet connection"
date: 2006-11-27
forum: General Help
---

### Post by happy-and-lost on 2006-11-27
I'm currently suffering from a completely random slowdown on my relatively fresh install of Ubuntu 6.10 Edgy. I haven't installed or changed anything recently, but *somthing* has caused it to go into meltdown. Another random effect of this is that my internet connection has died. I can connect to my router and get an IP address, but I can't access the net or ping any sites.

Another weird thing, despite this slowdown, RAM useage is still at its usual 168mb and CPU is also how it ususally is :(

Any suggestions? :confused:

---

### Post by nixclusive on 2006-11-27
You might wanna check out the kernel messages with:
```
dmesg | less
```

or disable the splash screen by editing the kernel command line in grub:
1. Press ESC when the message appears: Grub Loading... Press Esc to access menu.
2. Press 'e' to edit the default option in the menu.
3. Edit the line 'kernel ...' by pressing 'e' on it again.
4. Remove the words 'quiet splash' and press enter.
5. Press 'b' to boot now.

You should see a lot of messages passing by. Check to see if something's wrong. You can press 'Scroll Lock' while the messages scroll by and press Ctrl+PgUP to see what scrolled up while you blinked.

---

### Post by happy-and-lost on 2006-11-27
Here's my dmesg...

```

jo@mithos:~$ dmesg
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[17179569.184000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003ffd3800 (usable)
[17179569.184000]  BIOS-e820: 000000003ffd3800 - 0000000040000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000e0000000 - 00000000f0007000 (reserved)
[17179569.184000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed20000 - 00000000fee10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[17179569.184000] 127MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 262099
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 32723 pages, LIFO batch:7
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fc9b0
[17179569.184000] ACPI: RSDT (v001 DELL    CPi R   0x27d5091c ASL  0x00000061) @ 0x3ffd3fd3
[17179569.184000] ACPI: FADT (v001 DELL    CPi R   0x27d5091c ASL  0x00000061) @ 0x3ffd4c00
[17179569.184000] ACPI: MADT (v001 DELL    CPi R   0x27d5091c ASL  0x00000047) @ 0x3ffd5400
[17179569.184000] ACPI: MCFG (v016 DELL    CPi R   0x27d5091c ASL  0x00000061) @ 0x3ffd53c0
[17179569.184000] ACPI: BOOT (v001 DELL    CPi R   0x27d5091c ASL  0x00000061) @ 0x3ffd4fc0
[17179569.184000] ACPI: SSDT (v001  PmRef  Cpu0Ist 0x00003000 INTL 0x20030522) @ 0x3ffd43e6
[17179569.184000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20030522) @ 0x3ffd420e
[17179569.184000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20030522) @ 0x3ffd4013
[17179569.184000] ACPI: DSDT (v001 INT430 SYSFexxx 0x00001001 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:13 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda3 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 1729.428 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.472000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179569.472000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.500000] Memory: 1029396k/1048396k available (1910k kernel code, 18336k reserved, 1070k data, 308k init, 130892k highmem)
[17179569.500000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.580000] Calibrating delay using timer specific routine.. 3463.40 BogoMIPS (lpj=6926813)
[17179569.580000] Security Framework v1.0.0 initialized
[17179569.580000] SELinux:  Disabled at boot.
[17179569.580000] Mount-cache hash table entries: 512
[17179569.580000] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000180 00000000 00000000
[17179569.580000] CPU: After vendor identify, caps: afe9fbff 00100000 00000000 00000000 00000180 00000000 00000000
[17179569.580000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179569.580000] CPU: L2 cache: 2048K
[17179569.580000] CPU: After all inits, caps: afe9fbff 00100000 00000000 00000040 00000180 00000000 00000000
[17179569.580000] Checking 'hlt' instruction... OK.
[17179569.596000] SMP alternatives: switching to UP code
[17179569.596000] Freeing SMP alternatives: 16k freed
[17179569.596000] checking if image is initramfs... it is
[17179570.128000] Freeing initrd memory: 5563k freed
[17179570.128000] ACPI: Core revision 20060707
[17179570.136000] ACPI: Looking for DSDT ... not found!
[17179570.140000] CPU0: Intel(R) Pentium(R) M processor 1.73GHz stepping 08
[17179570.140000] Total of 1 processors activated (3463.40 BogoMIPS).
[17179570.140000] ENABLING IO-APIC IRQs
[17179570.140000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.284000] Brought up 1 CPUs
[17179570.284000] migration_cost=0
[17179570.284000] NET: Registered protocol family 16
[17179570.284000] EISA bus registered
[17179570.284000] ACPI: bus type pci registered
[17179570.284000] PCI: Using MMCONFIG
[17179570.284000] Setting up standard PCI resources
[17179570.300000] ACPI: Interpreter enabled
[17179570.300000] ACPI: Using IOAPIC for interrupt routing
[17179570.300000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.300000] PCI: Probing PCI hardware (bus 00)
[17179570.300000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179570.316000] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[17179570.316000] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
[17179570.316000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.2
[17179570.316000] Boot video device is 0000:01:00.0
[17179570.316000] PCI: Transparent bridge - 0000:00:1e.0
[17179570.316000] PCI: Bus #04 (-#07) is hidden behind transparent bridge #03 (-#04) (try 'pci=assign-busses')
[17179570.316000] Please report the result to linux-kernel to fix this permanently
[17179570.316000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.332000] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[17179570.332000] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[17179570.332000] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
[17179570.332000] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 *7 9 10 11)
[17179570.336000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179570.336000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179570.336000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179570.336000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[17179570.336000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[17179570.336000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.336000] pnp: PnP ACPI init
[17179570.364000] pnp: PnP ACPI: found 11 devices
[17179570.364000] PnPBIOS: Disabled by ACPI PNP
[17179570.364000] PCI: Using ACPI for IRQ routing
[17179570.364000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.380000] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
[17179570.380000] pnp: 00:02: ioport range 0x1000-0x1005 could not be reserved
[17179570.380000] pnp: 00:02: ioport range 0x1008-0x100f could not be reserved
[17179570.380000] pnp: 00:03: ioport range 0xf400-0xf4fe has been reserved
[17179570.380000] pnp: 00:03: ioport range 0x1006-0x1007 has been reserved
[17179570.380000] pnp: 00:03: ioport range 0x100a-0x1059 could not be reserved
[17179570.380000] pnp: 00:03: ioport range 0x1060-0x107f has been reserved
[17179570.380000] pnp: 00:03: ioport range 0x1080-0x10bf has been reserved
[17179570.380000] pnp: 00:03: ioport range 0x10c0-0x10df has been reserved
[17179570.380000] pnp: 00:08: ioport range 0x900-0x90f has been reserved
[17179570.380000] pnp: 00:08: ioport range 0x910-0x91f has been reserved
[17179570.380000] pnp: 00:08: ioport range 0x920-0x92f has been reserved
[17179570.380000] pnp: 00:08: ioport range 0x930-0x93f has been reserved
[17179570.380000] pnp: 00:08: ioport range 0x940-0x97f has been reserved
[17179570.380000] PCI: Bridge: 0000:00:01.0
[17179570.380000]   IO window: d000-dfff
[17179570.380000]   MEM window: dfd00000-dfefffff
[17179570.380000]   PREFETCH window: d0000000-d7ffffff
[17179570.380000] PCI: Bus 4, cardbus bridge: 0000:03:01.0
[17179570.380000]   IO window: 00002000-000020ff
[17179570.380000]   IO window: 00002400-000024ff
[17179570.380000]   PREFETCH window: 50000000-51ffffff
[17179570.380000]   MEM window: 52000000-53ffffff
[17179570.380000] PCI: Bridge: 0000:00:1e.0
[17179570.380000]   IO window: 2000-2fff
[17179570.380000]   MEM window: dfc00000-dfcfffff
[17179570.380000]   PREFETCH window: 50000000-51ffffff
[17179570.380000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179570.380000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179570.380000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179570.380000] PCI: Enabling device 0000:03:01.0 (0000 -> 0003)
[17179570.380000] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 177
[17179570.380000] NET: Registered protocol family 2
[17179570.420000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179570.420000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[17179570.420000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179570.420000] TCP: Hash tables configured (established 131072 bind 65536)
[17179570.420000] TCP reno registered
[17179570.420000] Simple Boot Flag at 0x79 set to 0x1
[17179570.420000] audit: initializing netlink socket (disabled)
[17179570.420000] audit(1164653807.420:1): initialized
[17179570.420000] highmem bounce pool size: 64 pages
[17179570.420000] VFS: Disk quotas dquot_6.5.1
[17179570.420000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.420000] Initializing Cryptographic API
[17179570.420000] io scheduler noop registered
[17179570.420000] io scheduler anticipatory registered
[17179570.420000] io scheduler deadline registered
[17179570.420000] io scheduler cfq registered (default)
[17179570.420000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179570.420000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179570.420000] assign_interrupt_mode Found MSI capability
[17179570.420000] Allocate Port Service[0000:00:01.0:pcie00]
[17179570.420000] Allocate Port Service[0000:00:01.0:pcie03]
[17179570.420000] isapnp: Scanning for PnP cards...
[17179570.776000] isapnp: No Plug & Play device found
[17179570.796000] Real Time Clock Driver v1.12ac
[17179570.796000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179570.796000] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 17 (level, low) -> IRQ 201
[17179570.796000] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[17179570.796000] mice: PS/2 mouse device common for all mice
[17179570.796000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179570.796000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179570.796000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179570.796000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179570.804000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179570.804000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179570.808000] EISA: Probing bus 0 at eisa.0
[17179570.808000] Cannot allocate resource for EISA slot 1
[17179570.808000] Cannot allocate resource for EISA slot 2
[17179570.808000] EISA: Detected 0 cards.
[17179570.808000] TCP bic registered
[17179570.808000] NET: Registered protocol family 1
[17179570.808000] NET: Registered protocol family 8
[17179570.808000] NET: Registered protocol family 20
[17179570.808000] Using IPI No-Shortcut mode
[17179570.808000] ACPI: (supports S0 S3 S4 S5)
[17179570.808000] Freeing unused kernel memory: 308k freed
[17179570.816000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179571.984000] Capability LSM initialized
[17179572.012000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[17179572.012000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179572.012000] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[17179572.012000] ACPI: Getting cpuindex for acpiid 0x1
[17179572.016000] ACPI: Thermal Zone [THM] (39 C)
[17179572.296000] SCSI subsystem initialized
[17179572.296000] libata version 1.20 loaded.
[17179572.300000] ahci 0000:00:1f.2: version 1.2
[17179572.300000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 201
[17179572.300000] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[17179572.300000] ahci: probe of 0000:00:1f.2 failed with error -12
[17179572.300000] ata_piix 0000:00:1f.2: version 1.05
[17179572.300000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 201
[17179572.300000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179572.300000] ata1: SATA max UDMA/133 cmd 0x1F0 ctl 0x3F6 bmdma 0xBFA0 irq 14
[17179572.464000] ata1: dev 0 cfg 49:2b00 82:346b 83:5b29 84:6003 85:3469 86:9a09 87:6003 88:203f
[17179572.464000] ata1: dev 0 ATA-6, max UDMA/100, 117210240 sectors: LBA
[17179572.464000] ata1(0): applying bridge limits
[17179572.668000] ata1: dev 0 configured for UDMA/100
[17179572.668000] scsi0 : ata_piix
[17179572.668000]   Vendor: ATA       Model: FUJITSU MHV2060A  Rev: 0000
[17179572.668000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179572.668000] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xBFA8 irq 15
[17179572.988000] ata2: dev 0 cfg 49:0b00 82:0000 83:0000 84:0000 85:0000 86:0000 87:0000 88:0407
[17179572.988000] ata2: dev 0 ATAPI, max UDMA/33
[17179573.152000] ata2: dev 0 configured for UDMA/33
[17179573.152000] scsi1 : ata_piix
[17179573.152000]   Vendor: _NEC      Model: DVD+-RW ND-6650A  Rev: 102C
[17179573.152000]   Type:   CD-ROM                             ANSI SCSI revision: 05
[17179573.164000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[17179573.164000] sda: Write Protect is off
[17179573.164000] sda: Mode Sense: 00 3a 00 00
[17179573.164000] SCSI device sda: drive cache: write back
[17179573.164000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[17179573.164000] sda: Write Protect is off
[17179573.164000] sda: Mode Sense: 00 3a 00 00
[17179573.164000] SCSI device sda: drive cache: write back
[17179573.164000]  sda: sda1 sda2 sda3 sda4
[17179573.280000] sd 0:0:0:0: Attached scsi disk sda
[17179573.300000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[17179573.300000] Uniform CD-ROM driver Revision: 3.20
[17179573.300000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[17179574.856000] ide0: I/O resource 0x1F0-0x1F7 not free.
[17179574.856000] ide0: ports already in use, skipping probe
[17179574.856000] ide1: I/O resource 0x170-0x177 not free.
[17179574.856000] ide1: ports already in use, skipping probe
[17179574.880000] usbcore: registered new driver usbfs
[17179574.880000] usbcore: registered new driver hub
[17179574.880000] USB Universal Host Controller Interface driver v3.0
[17179574.880000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179574.880000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179574.880000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179574.880000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179574.880000] uhci_hcd 0000:00:1d.0: irq 169, io base 0x0000bf80
[17179574.884000] usb usb1: configuration #1 chosen from 1 choice
[17179574.884000] hub 1-0:1.0: USB hub found
[17179574.884000] hub 1-0:1.0: 2 ports detected
[17179574.940000] ieee1394: Initialized config rom entry `ip1394'
[17179574.988000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 201
[17179574.988000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179574.988000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179574.988000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179574.988000] uhci_hcd 0000:00:1d.1: irq 201, io base 0x0000bf60
[17179574.988000] usb usb2: configuration #1 chosen from 1 choice
[17179574.988000] hub 2-0:1.0: USB hub found
[17179574.988000] hub 2-0:1.0: 2 ports detected
[17179575.092000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 209
[17179575.092000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179575.092000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179575.092000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179575.092000] uhci_hcd 0000:00:1d.2: irq 209, io base 0x0000bf40
[17179575.092000] usb usb3: configuration #1 chosen from 1 choice
[17179575.092000] hub 3-0:1.0: USB hub found
[17179575.092000] hub 3-0:1.0: 2 ports detected
[17179575.196000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 177
[17179575.196000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179575.196000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179575.196000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179575.196000] uhci_hcd 0000:00:1d.3: irq 177, io base 0x0000bf20
[17179575.196000] usb usb4: configuration #1 chosen from 1 choice
[17179575.196000] hub 4-0:1.0: USB hub found
[17179575.196000] hub 4-0:1.0: 2 ports detected
[17179575.300000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 16 (level, low) -> IRQ 169
[17179575.300000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179575.300000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179575.300000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179575.300000] ehci_hcd 0000:00:1d.7: debug port 1
[17179575.300000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179575.300000] ehci_hcd 0000:00:1d.7: irq 169, io mem 0xffa80800
[17179575.304000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179575.304000] usb usb5: configuration #1 chosen from 1 choice
[17179575.304000] hub 5-0:1.0: USB hub found
[17179575.304000] hub 5-0:1.0: 8 ports detected
[17179575.408000] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 209
[17179575.460000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[209]  MMIO=[dfcfc800-dfcfcfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[17179575.548000] Attempting manual resume
[17179575.608000] kjournald starting.  Commit interval 5 seconds
[17179575.608000] EXT3-fs: mounted filesystem with ordered data mode.
[17179576.740000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[424fc0002543f030]
[17179586.784000] input: PC Speaker as /class/input/input1
[17179586.800000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179586.804000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179586.876000] Linux agpgart interface v0.101 (c) Dave Jones
[17179586.880000] agpgart: Detected an Intel 915GM Chipset.
[17179586.900000] agpgart: AGP aperture is 256M @ 0x0
[17179587.116000] hw_random: cannot enable RNG, aborting
[17179587.156000] input: PS/2 Mouse as /class/input/input2
[17179587.180000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input3
[17179587.528000] ts: Compaq touchscreen protocol output
[17179587.780000] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 177
[17179587.780000] Yenta: CardBus bridge found at 0000:03:01.0 [1028:0188]
[17179587.908000] Yenta: ISA IRQ mask 0x04b8, PCI irq 177
[17179587.908000] Socket status: 30000006
[17179587.908000] Yenta: Raising subordinate bus# of parent bus (#03) from #04 to #07
[17179587.908000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[17179587.908000] cs: IO port probe 0x2000-0x2fff: clean.
[17179587.908000] pcmcia: parent PCI bridge Memory window: 0xdfc00000 - 0xdfcfffff
[17179587.908000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x51ffffff
[17179588.052000] ieee80211_crypt: registered algorithm 'NULL'
[17179588.120000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[17179588.120000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179588.304000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 16 (level, low) -> IRQ 169
[17179588.304000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[17179588.364000] sdhci: Secure Digital Host Controller Interface driver, 0.12
[17179588.364000] sdhci: Copyright(c) Pierre Ossman
[17179588.512000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179588.512000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[17179588.704000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
[17179588.704000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179588.704000] Driver 'ipw2200' needs updating - please use bus_type methods
[17179589.124000] intel8x0_measure_ac97_clock: measured 55497 usecs
[17179589.124000] intel8x0: clocking to 48000
[17179589.124000] sdhci: SDHCI controller found at 0000:03:01.2 [1180:0822] (rev 17)
[17179589.124000] ACPI: PCI Interrupt 0000:03:01.2[C] -> GSI 17 (level, low) -> IRQ 201
[17179589.124000] mmc0: SDHCI at 0xdfcfc700 irq 201 DMA
[17179589.132000] b44.c:v1.00 (Apr 7, 2006)
[17179589.132000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 18 (level, low) -> IRQ 209
[17179589.132000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:12:3f:ec:47:d2
[17179589.132000] ACPI: PCI Interrupt 0000:03:03.0[A] -> GSI 17 (level, low) -> IRQ 201
[17179589.132000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[17179589.664000] cs: IO port probe 0x100-0x3af: excluding 0x370-0x377
[17179589.664000] cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7
[17179589.668000] cs: IO port probe 0x820-0x8ff: clean.
[17179589.668000] cs: IO port probe 0xc00-0xcf7: clean.
[17179589.668000] cs: IO port probe 0xa00-0xaff: clean.
[17179589.668000] ipw2200: Detected geography ZZD (13 802.11bg channels, 0 802.11a channels)
[17179590.416000] lp: driver loaded but no devices found
[17179590.436000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179590.436000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179590.480000] Adding 1261092k swap on /dev/disk/by-uuid/7af9803f-ea41-42e0-88bd-61149ef49981.  Priority:-1 extents:1 across:1261092k
[17179590.640000] EXT3 FS on sda3, internal journal
[17179603.792000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179603.860000] NTFS volume version 3.1.
[17179606.144000] ACPI: AC Adapter [AC] (on-line)
[17179606.452000] ACPI: Battery Slot [BAT0] (battery present)
[17179606.468000] ACPI: Lid Switch [LID]
[17179606.468000] ACPI: Power Button (CM) [PBTN]
[17179606.468000] ACPI: Sleep Button (CM) [SBTN]
[17179606.612000] ibm_acpi: ec object not found
[17179606.644000] pcc_acpi: loading...
[17179606.748000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[17179606.748000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[17179606.748000] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[17179609.632000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179609.632000] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
[17179609.632000] [fglrx] module loaded - fglrx 8.28.8 [Aug 17 2006] on minor 0
[17179609.664000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179612.348000] [fglrx] total      GART = 134217728
[17179612.348000] [fglrx] free       GART = 118226944
[17179612.348000] [fglrx] max single GART = 118226944
[17179612.348000] [fglrx] total      LFB  = 27226112
[17179612.348000] [fglrx] free       LFB  = 19034112
[17179612.348000] [fglrx] max single LFB  = 19034112
[17179612.348000] [fglrx] total      Inv  = 0
[17179612.348000] [fglrx] free       Inv  = 0
[17179612.348000] [fglrx] max single Inv  = 0
[17179612.348000] [fglrx] total      TIM  = 0
[17179612.416000] apm: BIOS not found.
[17179619.728000] cdrom: This disc doesn't have any tracks I recognize!
[17179621.196000] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[17179621.320000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[17179621.320000] NFSD: starting 90-second grace period
[17179621.320000] portmap: RPC call returned error 101
[17179621.320000] RPC: failed to contact portmap (errno -101).
[17179621.320000] portmap: RPC call returned error 101
[17179621.320000] RPC: failed to contact portmap (errno -101).
[17179621.320000] portmap: RPC call returned error 101
[17179621.320000] RPC: failed to contact portmap (errno -101).
[17179623.300000] Bluetooth: Core ver 2.8
[17179623.300000] NET: Registered protocol family 31
[17179623.300000] Bluetooth: HCI device and connection manager initialized
[17179623.300000] Bluetooth: HCI socket layer initialized
[17179623.376000] Bluetooth: L2CAP ver 2.8
[17179623.376000] Bluetooth: L2CAP socket layer initialized
[17179623.388000] Bluetooth: RFCOMM socket layer initialized
[17179623.388000] Bluetooth: RFCOMM TTY layer initialized
[17179623.388000] Bluetooth: RFCOMM ver 1.7
[17179623.456000] NET: Registered protocol family 10
[17179623.456000] lo: Disabled Privacy Extensions
[17179623.456000] IPv6 over IPv4 tunneling driver
[17179624.032000] /dev/vmmon[4491]: Module vmmon: registered with major=10 minor=165
[17179624.036000] /dev/vmmon[4491]: Module vmmon: initialized
[17179624.404000] /dev/vmnet: open called by PID 4522 (vmnet-bridge)
[17179624.404000] /dev/vmnet: hub 0 does not exist, allocating memory.
[17179624.404000] /dev/vmnet: port on hub 0 successfully opened
[17179624.404000] bridge-eth1: peer interface eth1 not found, will wait for it to come up
[17179624.404000] bridge-eth1: attached
[17179624.420000] /dev/vmnet: open called by PID 4532 (vmnet-bridge)
[17179624.420000] /dev/vmnet: hub 2 does not exist, allocating memory.
[17179624.420000] /dev/vmnet: port on hub 2 successfully opened
[17179624.420000] bridge-eth0: peer interface eth0 not found, will wait for it to come up
[17179624.420000] bridge-eth0: attached
[17179624.540000] /dev/vmnet: open called by PID 4542 (vmnet-netifup)
[17179624.544000] /dev/vmnet: hub 1 does not exist, allocating memory.
[17179624.544000] /dev/vmnet: port on hub 1 successfully opened
[17179624.552000] /dev/vmnet: open called by PID 4543 (vmnet-netifup)
[17179624.552000] /dev/vmnet: hub 8 does not exist, allocating memory.
[17179624.552000] /dev/vmnet: port on hub 8 successfully opened
[17179624.600000] /dev/vmnet: open called by PID 4541 (vmnet-natd)
[17179624.600000] /dev/vmnet: port on hub 8 successfully opened
[17179625.412000] /dev/vmnet: open called by PID 4565 (vmnet-dhcpd)
[17179625.412000] /dev/vmnet: port on hub 8 successfully opened
[17179627.328000] bridge-eth1: enabling the bridge
[17179627.328000] bridge-eth1: is a Wireless Adapter
[17179627.328000] bridge-eth1: up
[17179628.392000] NET: Registered protocol family 17
[17179634.808000] vmnet8: no IPv6 routers present
[17179635.396000] vmnet1: no IPv6 routers present
[17179637.668000] eth1: no IPv6 routers present

```

As far as the net problems go, when I type ifup eth1 it says "ifup eth1
ifup: couldn't read interfaces file "/etc/network/interfaces" :???:

---

