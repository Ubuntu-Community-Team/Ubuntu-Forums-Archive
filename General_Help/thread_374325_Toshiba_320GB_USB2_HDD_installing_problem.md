---
title: "Toshiba 320GB USB2 HDD installing problem"
date: 2007-03-02
forum: General Help
---

### Post by reza81 on 2007-03-02
I just got a new external hdd (Toshiba 320GB USB2 HDD) so I can copy data from my another NTFS USB 2 HDD on this one and format it to ext3. 

```

reza@reza-desktop:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         272     2184808+  82  Linux swap / Solaris
/dev/hda2             273        2567    18434587+  83  Linux
/dev/hda3            2568        9729    57528765   83  Linux

Disk /dev/sdf: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       14946   120053713+   7  HPFS/NTFS


```

```

reza@reza-desktop:~$ lsusb
Bus 005 Device 009: ID 0930:0b05 Toshiba Corp. 
Bus 005 Device 007: ID 20c8:3574  
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 1025:0041 Hyper-Paltek 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 04f2:0200 Chicony Electronics Co., Ltd 
Bus 003 Device 003: ID 147a:e00d Formosa Industrial Computing, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

```

this is what i see... it allso has some kind of lame password protection on it.

how can I formate this ???

P.S. Gnome Partition manager doesn't see the new USB HDD

---

### Post by dcstar on 2007-03-02
> **reza81 said:**
> I just got a new external hdd (Toshiba 320GB USB2 HDD) so I can copy data from my another NTFS USB 2 HDD on this one and format it to ext3. 
........
P.S. Gnome Partition manager doesn't see the new USB HDD

Plug it in and run:
```
dmesg
``` and post the output here (last few lines)

---

### Post by reza81 on 2007-03-04
> **dcstar said:**
> Plug it in and run:
```
dmesg
``` and post the output here (last few lines)

lots of output :popcorn: 

```
[17179569.184000] Linux version 2.6.17-11-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Thu Feb 1 19:52:28 UTC 2007 (Ubuntu 2.6.17-11.35-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000002fff0000 - 000000002fff3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000002fff3000 - 0000000030000000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 767MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f5400
[17179569.184000] On node 0 totalpages: 196592
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 192496 pages, LIFO batch:31
[17179569.184000] DMI 2.2 present.
[17179569.184000] ACPI: RSDP (v000 IntelR                                ) @ 0x000f72b0
[17179569.184000] ACPI: RSDT (v001 IntelR AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x2fff3000
[17179569.184000] ACPI: FADT (v001 IntelR AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x2fff3040
[17179569.184000] ACPI: MADT (v001 IntelR AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x2fff6f80
[17179569.184000] ACPI: DSDT (v001 INTELR AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x408
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:2 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 15:2 APIC version 20
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] ACPI: IRQ14 used by override.
[17179569.184000] ACPI: IRQ15 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 40000000 (gap: 30000000:cec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda2 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 2800.936 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179571.636000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179571.636000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.652000] Memory: 769632k/786368k available (1911k kernel code, 16088k reserved, 1073k data, 308k init, 0k highmem)
[17179571.652000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179571.732000] Calibrating delay using timer specific routine.. 5606.82 BogoMIPS (lpj=11213652)
[17179571.732000] Security Framework v1.0.0 initialized
[17179571.732000] SELinux:  Disabled at boot.
[17179571.732000] Mount-cache hash table entries: 512
[17179571.732000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[17179571.732000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[17179571.732000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[17179571.732000] CPU: L2 cache: 512K
[17179571.732000] CPU: Hyper-Threading is disabled
[17179571.732000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00004400 00000000 00000000
[17179571.732000] Checking 'hlt' instruction... OK.
[17179571.748000] SMP alternatives: switching to UP code
[17179571.748000] checking if image is initramfs... it is
[17179572.184000] Freeing initrd memory: 5326k freed
[17179572.184000] ACPI: Core revision 20060707
[17179572.188000] ACPI: Looking for DSDT ... not found!
[17179572.208000] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 09
[17179572.208000] SMP alternatives: switching to SMP code
[17179572.208000] Booting processor 1/1 eip 3000
[17179572.220000] Initializing CPU#1
[17179572.300000] Calibrating delay using timer specific routine.. 5601.32 BogoMIPS (lpj=11202648)
[17179572.300000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[17179572.300000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[17179572.300000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[17179572.300000] CPU: L2 cache: 512K
[17179572.300000] CPU: Hyper-Threading is disabled
[17179572.300000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00004400 00000000 00000000
[17179572.300000] CPU1: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 09
[17179572.300000] Total of 2 processors activated (11208.15 BogoMIPS).
[17179572.300000] ENABLING IO-APIC IRQs
[17179572.300000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179572.444000] checking TSC synchronization across 2 CPUs: passed.
[17179572.448000] Brought up 2 CPUs
[17179572.472000] migration_cost=4000
[17179572.472000] NET: Registered protocol family 16
[17179572.472000] EISA bus registered
[17179572.472000] ACPI: bus type pci registered
[17179572.484000] PCI: PCI BIOS revision 2.10 entry at 0xfb0a0, last bus=2
[17179572.484000] PCI: Using configuration type 1
[17179572.484000] Setting up standard PCI resources
[17179572.508000] ACPI: Interpreter enabled
[17179572.508000] ACPI: Using IOAPIC for interrupt routing
[17179572.508000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179572.508000] PCI: Probing PCI hardware (bus 00)
[17179572.508000] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[17179572.508000] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[17179572.508000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179572.508000] Boot video device is 0000:01:00.0
[17179572.508000] PCI: Transparent bridge - 0000:00:1e.0
[17179572.508000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179572.520000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[17179572.524000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[17179572.524000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[17179572.524000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[17179572.524000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[17179572.524000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[17179572.524000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[17179572.524000] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[17179572.524000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[17179572.524000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179572.524000] pnp: PnP ACPI init
[17179572.528000] pnp: PnP ACPI: found 14 devices
[17179572.528000] PnPBIOS: Disabled by ACPI PNP
[17179572.528000] PCI: Using ACPI for IRQ routing
[17179572.528000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179572.544000] pnp: 00:0b: ioport range 0x400-0x4bf could not be reserved
[17179572.544000] PCI: Bridge: 0000:00:01.0
[17179572.544000]   IO window: disabled.
[17179572.544000]   MEM window: e8000000-e9ffffff
[17179572.544000]   PREFETCH window: d0000000-dfffffff
[17179572.544000] PCI: Bridge: 0000:00:1e.0
[17179572.544000]   IO window: 9000-9fff
[17179572.544000]   MEM window: ea000000-ea0fffff
[17179572.544000]   PREFETCH window: ea100000-ea1fffff
[17179572.544000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179572.544000] NET: Registered protocol family 2
[17179572.584000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179572.584000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[17179572.584000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179572.584000] TCP: Hash tables configured (established 131072 bind 65536)
[17179572.584000] TCP reno registered
[17179572.584000] audit: initializing netlink socket (disabled)
[17179572.584000] audit(1173014562.584:1): initialized
[17179572.584000] VFS: Disk quotas dquot_6.5.1
[17179572.584000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.584000] Initializing Cryptographic API
[17179572.584000] io scheduler noop registered
[17179572.584000] io scheduler anticipatory registered
[17179572.584000] io scheduler deadline registered
[17179572.584000] io scheduler cfq registered (default)
[17179572.584000] isapnp: Scanning for PnP cards...
[17179572.940000] isapnp: No Plug & Play device found
[17179572.964000] Real Time Clock Driver v1.12ac
[17179572.964000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179572.964000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.964000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179572.964000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.964000] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179572.964000] mice: PS/2 mouse device common for all mice
[17179572.968000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179572.968000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179572.968000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179572.968000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[17179572.968000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179572.976000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179572.976000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179572.980000] EISA: Probing bus 0 at eisa.0
[17179572.980000] EISA: Detected 0 cards.
[17179572.980000] TCP bic registered
[17179572.980000] NET: Registered protocol family 1
[17179572.980000] NET: Registered protocol family 8
[17179572.980000] NET: Registered protocol family 20
[17179572.980000] Starting balanced_irq
[17179572.980000] Using IPI No-Shortcut mode
[17179572.980000] ACPI: (supports S0 S3 S4 S5)
[17179572.980000] Freeing unused kernel memory: 308k freed
[17179575.040000] Capability LSM initialized
[17179575.076000] ACPI: Fan [FAN] (on)
[17179575.080000] ACPI: Thermal Zone [THRM] (21 C)
[17179575.528000] ICH5: IDE controller at PCI slot 0000:00:1f.1
[17179575.528000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 169
[17179575.528000] ICH5: chipset revision 2
[17179575.528000] ICH5: not 100% native mode: will probe irqs later
[17179575.528000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:pio
[17179575.528000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:pio
[17179575.528000] Probing IDE interface ide0...
[17179575.824000] hda: WDC WD800EB-00DJF0, ATA DISK drive
[17179576.500000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179576.516000] Probing IDE interface ide1...
[17179577.260000] hdc: HL-DT-ST DVDRAM GSA-4040B, ATAPI CD/DVD-ROM drive
[17179577.600000] ide1 at 0x170-0x177,0x376 on irq 15
[17179577.612000] hda: max request size: 512KiB
[17179577.616000] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[17179577.616000] hda: cache flushes supported
[17179577.616000]  hda: hda1 hda2 hda3
[17179577.628000] hdc: ATAPI 32X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179577.628000] Uniform CD-ROM driver Revision: 3.20
[17179577.960000] usbcore: registered new driver usbfs
[17179577.960000] usbcore: registered new driver hub
[17179577.960000] USB Universal Host Controller Interface driver v3.0
[17179577.960000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 177
[17179577.960000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179577.960000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179577.960000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179577.960000] uhci_hcd 0000:00:1d.0: irq 177, io base 0x0000ac00
[17179577.960000] usb usb1: configuration #1 chosen from 1 choice
[17179577.960000] hub 1-0:1.0: USB hub found
[17179577.960000] hub 1-0:1.0: 2 ports detected
[17179577.996000] ieee1394: Initialized config rom entry `ip1394'
[17179578.068000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 185
[17179578.068000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179578.068000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179578.068000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179578.068000] uhci_hcd 0000:00:1d.1: irq 185, io base 0x0000a000
[17179578.068000] usb usb2: configuration #1 chosen from 1 choice
[17179578.068000] hub 2-0:1.0: USB hub found
[17179578.068000] hub 2-0:1.0: 2 ports detected
[17179578.172000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 169
[17179578.172000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179578.172000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179578.172000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179578.176000] uhci_hcd 0000:00:1d.2: irq 169, io base 0x0000a400
[17179578.176000] usb usb3: configuration #1 chosen from 1 choice
[17179578.176000] hub 3-0:1.0: USB hub found
[17179578.176000] hub 3-0:1.0: 2 ports detected
[17179578.280000] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 177
[17179578.280000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179578.280000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179578.280000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179578.284000] uhci_hcd 0000:00:1d.3: irq 177, io base 0x0000a800
[17179578.284000] usb usb4: configuration #1 chosen from 1 choice
[17179578.284000] hub 4-0:1.0: USB hub found
[17179578.284000] hub 4-0:1.0: 2 ports detected
[17179578.304000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[17179578.388000] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 22 (level, low) -> IRQ 193
[17179578.388000] PCI: Via IRQ fixup for 0000:02:04.0, from 5 to 1
[17179578.392000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 201
[17179578.392000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179578.392000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179578.392000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179578.392000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[17179578.392000] ehci_hcd 0000:00:1d.7: irq 201, io mem 0xea200000
[17179578.396000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179578.396000] usb usb5: configuration #1 chosen from 1 choice
[17179578.396000] hub 5-0:1.0: USB hub found
[17179578.396000] hub 5-0:1.0: 8 ports detected
[17179578.444000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[193]  MMIO=[ea001000-ea0017ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[17179578.572000] Attempting manual resume
[17179578.608000] kjournald starting.  Commit interval 5 seconds
[17179578.608000] EXT3-fs: mounted filesystem with ordered data mode.
[17179578.852000] usb 1-1: device not accepting address 2, error -71
[17179579.728000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00016c200003ad90]
[17179579.848000] usb 5-4: new high speed USB device using ehci_hcd and address 3
[17179579.988000] usb 5-4: configuration #1 chosen from 1 choice
[17179580.784000] usb 3-1: new low speed USB device using uhci_hcd and address 2
[17179581.024000] usb 3-1: configuration #1 chosen from 1 choice
[17179581.268000] usb 3-2: new low speed USB device using uhci_hcd and address 3
[17179581.460000] usb 3-2: configuration #1 chosen from 1 choice
[17179581.712000] usb 1-1: new low speed USB device using uhci_hcd and address 4
[17179581.900000] usb 1-1: configuration #1 chosen from 1 choice
[17179582.140000] usb 4-2: new full speed USB device using uhci_hcd and address 2
[17179582.348000] usb 4-2: configuration #1 chosen from 1 choice
[17179588.600000] Floppy drive(s): fd0 is 1.44M
[17179588.636000] input: PC Speaker as /class/input/input0
[17179588.668000] FDC 0 is a post-1991 82077
[17179588.688000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179588.692000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179589.060000] Linux agpgart interface v0.101 (c) Dave Jones
[17179589.072000] agpgart: Detected an Intel 865 Chipset.
[17179589.076000] agpgart: AGP aperture is 128M @ 0xe0000000
[17179589.176000] parport: PnPBIOS parport detected.
[17179589.176000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[17179589.420000] hw_random hardware driver 1.0.0 loaded
[17179589.496000] usbcore: registered new driver hiddev
[17179589.528000] input: Chicony USB Wireless HID Receiver as /class/input/input1
[17179589.528000] input: USB HID v1.10 Keyboard [Chicony USB Wireless HID Receiver] on usb-0000:00:1d.2-1
[17179589.664000] input: Chicony USB Wireless HID Receiver as /class/input/input2
[17179589.664000] input,hiddev96: USB HID v1.10 Device [Chicony USB Wireless HID Receiver] on usb-0000:00:1d.2-1
[17179589.708000] input: Chicony USB Wireless HID Receiver as /class/input/input3
[17179589.708000] input: USB HID v1.10 Mouse [Chicony USB Wireless HID Receiver] on usb-0000:00:1d.2-1
[17179589.712000] nvidia: module license 'NVIDIA' taints kernel.
[17179589.720000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 177
[17179589.724000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
[17179589.816000] input: Cypress Semiconductor Cypress CY7C637xx USB Mouse v?.? as /class/input/input4
[17179589.816000] input: USB HID v1.10 Device [Cypress Semiconductor Cypress CY7C637xx USB Mouse v?.?] on usb-0000:00:1d.2-2
[17179589.832000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input5
[17179589.832000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-1
[17179589.832000] usbcore: registered new driver usbhid
[17179589.832000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179590.160000] usbcore: registered new driver libusual
[17179590.204000] SCSI subsystem initialized
[17179590.208000] Initializing USB Mass Storage driver...
[17179590.208000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179590.208000] usb-storage: device found at 3
[17179590.208000] usb-storage: waiting for device to settle before scanning
[17179590.208000] scsi1 : SCSI emulation for USB Mass Storage devices
[17179590.216000] usbcore: registered new driver usb-storage
[17179590.216000] USB Mass Storage support registered.
[17179590.216000] usb-storage: device found at 2
[17179590.216000] usb-storage: waiting for device to settle before scanning
[17179590.232000] ACPI: PCI Interrupt 0000:02:01.1[A] -> GSI 22 (level, low) -> IRQ 193
[17179590.276000] 8139too Fast Ethernet driver 0.9.27
[17179590.276000] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 23 (level, low) -> IRQ 201
[17179590.276000] eth0: RealTek RTL8139 at 0xf09fe000, 00:01:6c:26:27:6d, IRQ 201
[17179590.276000] eth0:  Identified 8139 chip type 'RTL-8101'
[17179590.288000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179590.300000] Linux video capture interface: v1.00
[17179590.380000] bttv: driver version 0.9.16 loaded
[17179590.380000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17179590.380000] bttv: Bt8xx card found (0).
[17179590.380000] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 22 (level, low) -> IRQ 193
[17179590.380000] bttv0: Bt878 (rev 17) at 0000:02:01.0, irq: 193, latency: 32, mmio: 0xea100000
[17179590.380000] bttv0: detected: Leadtek WinFast TV 2000 [card=34], PCI subsystem ID is 107d:6606
[17179590.380000] bttv0: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,autodetected]
[17179590.380000] bttv0: gpio: en=00000000, out=00000000 in=003ffffe [init]
[17179590.380000] bttv0: using tuner=5
[17179590.380000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[17179590.380000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[17179590.384000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[17179590.388000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[17179590.440000] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[17179590.440000] tuner 0-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[17179590.452000] ts: Compaq touchscreen protocol output
[17179590.472000] bttv0: registered device video0
[17179590.472000] bttv0: registered device vbi0
[17179590.472000] bttv0: registered device radio0
[17179590.472000] bttv0: PLL: 28636363 => 35468950 .. ok
[17179590.508000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179590.508000] input: bttv IR (card=34) as /class/input/input6
[17179590.508000] bttv-input: bttv IR (card=34) detected at pci-0000:02:01.0/ir0
[17179590.672000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 209
[17179590.672000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179590.736000] bt878: AUDIO driver version 0.0.0 loaded
[17179590.992000] intel8x0_measure_ac97_clock: measured 59129 usecs
[17179590.992000] intel8x0: clocking to 48000
[17179591.136000] lp0: using parport0 (interrupt-driven).
[17179591.156000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179591.156000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179591.184000] fuse init (API version 7.6)
[17179591.220000] Adding 2184800k swap on /dev/disk/by-uuid/428c2054-318c-4472-9a57-a852e264715b.  Priority:-1 extents:1 across:2184800k
[17179591.292000] EXT3 FS on hda2, internal journal
[17179591.528000] kjournald starting.  Commit interval 5 seconds
[17179591.536000] EXT3 FS on hda3, internal journal
[17179591.536000] EXT3-fs: mounted filesystem with ordered data mode.
[17179591.816000] NET: Registered protocol family 17
[17179595.208000] usb-storage: device scan complete
[17179595.212000]   Vendor:           Model:                   Rev:     
[17179595.212000]   Type:   CD-ROM                             ANSI SCSI revision: 00
[17179595.212000]   Vendor: Toshiba   Model: USB 2.0 Ext. HDD  Rev: 1.15
[17179595.212000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179595.220000] usb-storage: device scan complete
[17179595.224000]   Vendor:           Model: USB Card Reader   Rev: 1.1f
[17179595.224000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179595.228000]   Vendor:           Model: USB Card Reader   Rev: 1.1f
[17179595.228000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179595.232000]   Vendor:           Model: USB Card Reader   Rev: 1.1f
[17179595.232000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179595.236000]   Vendor:           Model: USB Card Reader   Rev: 1.1f
[17179595.236000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179595.248000] sr0: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
[17179595.248000] sr 0:0:0:0: Attached scsi CD-ROM sr0
[17179595.288000] sd 0:0:0:1: Attached scsi disk sda
[17179595.296000] sr 0:0:0:0: Attached scsi generic sg0 type 5
[17179595.296000] sd 0:0:0:1: Attached scsi generic sg1 type 0
[17179595.296000] sd 1:0:0:0: Attached scsi generic sg2 type 0
[17179595.296000]  1:0:0:1: Attached scsi generic sg3 type 0
[17179595.296000]  1:0:0:2: Attached scsi generic sg4 type 0
[17179595.296000]  1:0:0:3: Attached scsi generic sg5 type 0
[17179595.308000] sd 1:0:0:0: Attached scsi removable disk sdb
[17179595.324000] sd 1:0:0:1: Attached scsi removable disk sdc
[17179595.344000] sd 1:0:0:2: Attached scsi removable disk sdd
[17179595.356000] sd 1:0:0:3: Attached scsi removable disk sde
[17179595.448000] NET: Registered protocol family 10
[17179595.448000] lo: Disabled Privacy Extensions
[17179595.448000] IPv6 over IPv4 tunneling driver
[17179600.008000] ACPI: Power Button (FF) [PWRF]
[17179600.008000] ACPI: Power Button (CM) [PWRB]
[17179600.116000] ibm_acpi: ec object not found
[17179600.156000] pcc_acpi: loading...
[17179603.596000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[17179603.596000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17179603.596000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[17179604.572000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179604.572000] apm: disabled - APM is not SMP safe.
[17179606.288000] eth0: no IPv6 routers present
[17179609.436000] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[17179609.536000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[17179609.536000] NFSD: starting 90-second grace period
[17179623.488000] eth0: no IPv6 routers present
[17179644.632000] input: AT Translated Set 2 keyboard as /class/input/input7
[17179659.976000] UDF-fs: No VRS found
[17179660.008000] UDF-fs: No VRS found
[17179660.200000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17179660.200000] ISO 9660 Extensions: RRIP_1991A
[17187174.928000] usb 5-4: USB disconnect, address 3
[17187175.112000]  0:0:0:0: rejecting I/O to dead device
[17187175.112000]  0:0:0:0: rejecting I/O to dead device
[17187196.840000] usb 5-4: new high speed USB device using ehci_hcd and address 7
[17187196.972000] usb 5-4: configuration #1 chosen from 1 choice
[17187196.976000] scsi2 : SCSI emulation for USB Mass Storage devices
[17187196.976000] usb-storage: device found at 7
[17187196.976000] usb-storage: waiting for device to settle before scanning
[17187201.976000] usb-storage: device scan complete
[17187201.976000]   Vendor:           Model:                   Rev:     
[17187201.976000]   Type:   CD-ROM                             ANSI SCSI revision: 00
[17187201.980000]   Vendor: Toshiba   Model: USB 2.0 Ext. HDD  Rev: 1.15
[17187201.980000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17187201.992000] sr0: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
[17187201.992000] sr 2:0:0:0: Attached scsi CD-ROM sr0
[17187201.992000] sr 2:0:0:0: Attached scsi generic sg0 type 5
[17187201.996000] sd 2:0:0:1: Attached scsi disk sda
[17187201.996000] sd 2:0:0:1: Attached scsi generic sg1 type 0
[17187202.608000] UDF-fs: No VRS found
[17187202.624000] UDF-fs: No VRS found
[17187202.640000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17187202.640000] ISO 9660 Extensions: RRIP_1991A
[17187256.072000] usb 5-4: USB disconnect, address 7
[17187256.124000]  2:0:0:0: rejecting I/O to dead device
[17187256.124000]  2:0:0:0: rejecting I/O to dead device
[17187266.644000] usb 5-2: new high speed USB device using ehci_hcd and address 8
[17187266.788000] usb 5-2: configuration #1 chosen from 1 choice
[17187266.788000] scsi3 : SCSI emulation for USB Mass Storage devices
[17187266.788000] usb-storage: device found at 8
[17187266.788000] usb-storage: waiting for device to settle before scanning
[17187271.788000] usb-storage: device scan complete
[17187271.792000]   Vendor: Maxtor 6  Model: B120P0            Rev: 0811
[17187271.792000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17187271.792000] SCSI device sda: 240121728 512-byte hdwr sectors (122942 MB)
[17187271.796000] sda: test WP failed, assume Write Enabled
[17187271.796000] sda: assuming drive cache: write through
[17187271.796000] SCSI device sda: 240121728 512-byte hdwr sectors (122942 MB)
[17187271.796000] sda: test WP failed, assume Write Enabled
[17187271.796000] sda: assuming drive cache: write through
[17187271.796000]  sda: sda1
[17187271.820000] sd 3:0:0:0: Attached scsi disk sda
[17187271.820000] sd 3:0:0:0: Attached scsi generic sg0 type 0
[17187272.136000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17187272.136000] NTFS-fs warning (device sda1): parse_options(): Option iocharset is deprecated. Please use option nls=<charsetname> in the future.
[17187272.172000] NTFS volume version 3.1.
[17187307.216000] usb 5-4: new high speed USB device using ehci_hcd and address 9
[17187307.348000] usb 5-4: configuration #1 chosen from 1 choice
[17187307.348000] scsi4 : SCSI emulation for USB Mass Storage devices
[17187307.348000] usb-storage: device found at 9
[17187307.348000] usb-storage: waiting for device to settle before scanning
[17187312.348000] usb-storage: device scan complete
[17187312.348000]   Vendor:           Model:                   Rev:     
[17187312.348000]   Type:   CD-ROM                             ANSI SCSI revision: 00
[17187312.348000]   Vendor: Toshiba   Model: USB 2.0 Ext. HDD  Rev: 1.15
[17187312.348000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17187312.360000] sr0: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
[17187312.360000] sr 4:0:0:0: Attached scsi CD-ROM sr0
[17187312.360000] sr 4:0:0:0: Attached scsi generic sg1 type 5
[17187312.364000] sd 4:0:0:1: Attached scsi disk sdf
[17187312.364000] sd 4:0:0:1: Attached scsi generic sg6 type 0
[17187312.716000] UDF-fs: No VRS found
[17187312.744000] UDF-fs: No VRS found
[17187312.756000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17187312.760000] ISO 9660 Extensions: RRIP_1991A
[17187396.184000] usb 5-4: USB disconnect, address 9
[17187448.084000] usb 5-4: new high speed USB device using ehci_hcd and address 10
[17187448.216000] usb 5-4: configuration #1 chosen from 1 choice
[17187448.216000] scsi5 : SCSI emulation for USB Mass Storage devices
[17187448.216000] usb-storage: device found at 10
[17187448.216000] usb-storage: waiting for device to settle before scanning
[17187453.216000] usb-storage: device scan complete
[17187453.216000]   Vendor:           Model:                   Rev:     
[17187453.216000]   Type:   CD-ROM                             ANSI SCSI revision: 00
[17187453.216000]   Vendor: Toshiba   Model: USB 2.0 Ext. HDD  Rev: 1.15
[17187453.216000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17187453.228000] sr0: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
[17187453.232000] sr 5:0:0:0: Attached scsi CD-ROM sr0
[17187453.232000] sr 5:0:0:0: Attached scsi generic sg1 type 5
[17187453.232000] sd 5:0:0:1: Attached scsi disk sdf
[17187453.232000] sd 5:0:0:1: Attached scsi generic sg6 type 0
[17187453.568000] UDF-fs: No VRS found
[17187453.588000] UDF-fs: No VRS found
[17187453.600000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17187453.604000] ISO 9660 Extensions: RRIP_1991A

```

---

### Post by reza81 on 2007-03-04
Can't anyone help me with this ... how do i make this drive visible for fdisk & format it without a static mount point (becouse ubuntu does this automaticly [http://ubuntuforums.org/showthread.php?p=2014937](http://ubuntuforums.org/showthread.php?p=2014937))

---

### Post by reza81 on 2007-03-04
anyone???

it's kind of urgent

---

### Post by reza81 on 2007-03-04
done!!!

it was a password protected HDD. I logged in to a M$ system & got a popup screen to enter or disable pssw. when disabled it mounted on linux

... 

I still wonder how to fix this without the help of a M$ or a Apple system???

---

