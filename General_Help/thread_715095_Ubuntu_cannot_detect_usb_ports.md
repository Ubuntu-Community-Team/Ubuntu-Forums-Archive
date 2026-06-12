---
title: "Ubuntu cannot detect usb ports"
date: 2008-03-04
forum: General Help
---

### Post by ripmillar on 2008-03-04
Dear all I'm a newbie with ubuntu

and I have a problem :( about my usb not detected by ubuntu 
anyone please help me

it's show nothing when I type lsusb

this what lshw show me

> ripmillar@iLLuSion:~$ lshw
WARNING: you should run this program as super-user.
illusion                  
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 511MB
     *-cpu
          product: AMD Athlon(tm) Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 6.4.2
          size: 1GHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr syscall mmxext 3dnowext 3dnow up
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KB
     *-pci
          description: Host bridge
          product: VT8363/8365 [KT133/KM133]
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via latency=8 module=via_agp
        *-pci
             description: PCI bridge
             product: VT8363/8365 [KT133/KM133 AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: Radeon R200 QL [Radeon 8500 LE]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: latency=64 mingnt=8
        *-isa
             description: ISA bridge
             product: VT82C686 [Apollo Super South]
             vendor: VIA Technologies, Inc.
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 40
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=parport_pc latency=0 module=parport_pc
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 4.1
             bus info: pci@0000:00:04.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=VIA_IDE latency=32 module=via82cxxx
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   product: ST320011A
                   vendor: Seagate
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 18GB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   product: LITE-ON DVDRW SHW-160P6S
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capabilities: packet
        *-usb:0 UNCLAIMED
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 4.2
             bus info: pci@0000:00:04.2
             version: 16
             width: 32 bits
             clock: 33MHz
             capabilities: uhci cap_list
             configuration: latency=32
        *-usb:1 UNCLAIMED
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 4.3
             bus info: pci@0000:00:04.3
             version: 16
             width: 32 bits
             clock: 33MHz
             capabilities: uhci cap_list
             configuration: latency=32
        *-bridge UNCLAIMED
             description: Bridge
             product: VT82C686 [Apollo Super ACPI]
             vendor: VIA Technologies, Inc.
             physical id: 4.4
             bus info: pci@0000:00:04.4
             version: 40
             width: 32 bits
             clock: 33MHz
             capabilities: bridge cap_list
             configuration: latency=0
        *-communication UNCLAIMED
             description: Communication controller
             product: HSF 56k HSFi Modem
             vendor: Conexant
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=32
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: b
             bus info: pci@0000:00:0b.0
             logical name: eth0
             version: 10
             serial: 00:a0:b0:02:cc:bb
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.101 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
        *-multimedia
             description: Multimedia audio controller
             product: YMF-744B [DS-1S Audio Controller]
             vendor: Yamaha Corporation
             physical id: c
             bus info: pci@0000:00:0c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Yamaha DS-1 PCI latency=32 maxlatency=25 mingnt=5 module=snd_ymfpci
ripmillar@iLLuSion:~$ clear

ripmillar@iLLuSion:~$ lshw
WARNING: you should run this program as super-user.
illusion                  
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 511MB
     *-cpu
          product: AMD Athlon(tm) Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 6.4.2
          size: 1GHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr syscall mmxext 3dnowext 3dnow up
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KB
     *-pci
          description: Host bridge
          product: VT8363/8365 [KT133/KM133]
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via latency=8 module=via_agp
        *-pci
             description: PCI bridge
             product: VT8363/8365 [KT133/KM133 AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: Radeon R200 QL [Radeon 8500 LE]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: latency=64 mingnt=8
        *-isa
             description: ISA bridge
             product: VT82C686 [Apollo Super South]
             vendor: VIA Technologies, Inc.
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 40
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=parport_pc latency=0 module=parport_pc
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 4.1
             bus info: pci@0000:00:04.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=VIA_IDE latency=32 module=via82cxxx
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   product: ST320011A
                   vendor: Seagate
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 18GB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   product: LITE-ON DVDRW SHW-160P6S
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capabilities: packet
        *-usb:0 UNCLAIMED
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 4.2
             bus info: pci@0000:00:04.2
             version: 16
             width: 32 bits
             clock: 33MHz
             capabilities: uhci cap_list
             configuration: latency=32
        *-usb:1 UNCLAIMED
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 4.3
             bus info: pci@0000:00:04.3
             version: 16
             width: 32 bits
             clock: 33MHz
             capabilities: uhci cap_list
             configuration: latency=32
        *-bridge UNCLAIMED
             description: Bridge
             product: VT82C686 [Apollo Super ACPI]
             vendor: VIA Technologies, Inc.
             physical id: 4.4
             bus info: pci@0000:00:04.4
             version: 40
             width: 32 bits
             clock: 33MHz
             capabilities: bridge cap_list
             configuration: latency=0
        *-communication UNCLAIMED
             description: Communication controller
             product: HSF 56k HSFi Modem
             vendor: Conexant
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=32
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: b
             bus info: pci@0000:00:0b.0
             logical name: eth0
             version: 10
             serial: 00:a0:b0:02:cc:bb
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.101 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
        *-multimedia
             description: Multimedia audio controller
             product: YMF-744B [DS-1S Audio Controller]
             vendor: Yamaha Corporation
             physical id: c
             bus info: pci@0000:00:0c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Yamaha DS-1 PCI latency=32 maxlatency=25 mingnt=5 module=snd_ymfpci


and this what dmesg show

> ripmillar@iLLuSion:~$ dmesg 
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffec000 (usable)
[    0.000000]  BIOS-e820: 000000001ffec000 - 000000001ffef000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ffef000 - 000000001ffff000 (reserved)
[    0.000000]  BIOS-e820: 000000001ffff000 - 0000000020000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 131052) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131052
[    0.000000]   HighMem    131052 ->   131052
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131052
[    0.000000] On node 0 totalpages: 131052
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125965 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6A80 checksum 0
[    0.000000] ACPI: RSDP 000F6A80, 0014 (r0 ASUS  )
[    0.000000] ACPI: RSDT 1FFEC000, 002C (r1 ASUS   A7V133-C 30303031 MSFT 31313031)
[    0.000000] ACPI: FACP 1FFEC080, 0074 (r1 ASUS   A7V133-C 30303031 MSFT 31313031)
[    0.000000] ACPI: DSDT 1FFEC100, 2CE1 (r1   ASUS A7V133-C     1000 MSFT  100000B)
[    0.000000] ACPI: FACS 1FFFF000, 0040
[    0.000000] ACPI: BOOT 1FFEC040, 0028 (r1 ASUS   A7V133-C 30303031 MSFT 31313031)
[    0.000000] ACPI: PM-Timer IO Port: 0xe408
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfff0000)
[    0.000000] Built 1 zonelists.  Total pages: 130029
[    0.000000] Kernel command line: root=UUID=8a3a32ba-66d0-4826-bc64-0a3e1fc76aa5 ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (0140d000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1007.303 MHz processor.
[   14.186689] Console: colour VGA+ 80x25
[   14.187495] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   14.188060] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   14.220095] Memory: 507916k/524208k available (2015k kernel code, 15720k reserved, 915k data, 364k init, 0k highmem)
[   14.220117] virtual kernel memory layout:
[   14.220119]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   14.220122]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   14.220125]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   14.220128]     lowmem  : 0xc0000000 - 0xdffec000   ( 511 MB)
[   14.220130]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   14.220133]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[   14.220136]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[   14.220143] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   14.220227] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   14.300216] Calibrating delay using timer specific routine.. 2016.91 BogoMIPS (lpj=4033839)
[   14.300272] Security Framework v1.0.0 initialized
[   14.300285] SELinux:  Disabled at boot.
[   14.300322] Mount-cache hash table entries: 512
[   14.300570] CPU: After generic identify, caps: 0183f9ff c1c7f9ff 00000000 00000000 00000000 00000000 00000000
[   14.300588] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   14.300593] CPU: L2 Cache: 256K (64 bytes/line)
[   14.300599] CPU: After all inits, caps: 0183f9ff c1c7f9ff 00000000 00000420 00000000 00000000 00000000
[   14.300619] Compat vDSO mapped to ffffe000.
[   14.300642] Checking 'hlt' instruction... OK.
[   14.316269] SMP alternatives: switching to UP code
[   14.316700] Freeing SMP alternatives: 11k freed
[   14.317346] Early unpacking initramfs... done
[   14.972602] ACPI: Core revision 20070126
[   14.972780] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   14.974721] ACPI: setting ELCR to 0200 (from 0c60)
[   14.974905] CPU0: AMD Athlon(tm) Processor stepping 02
[   14.974916] SMP motherboard not detected.
[   14.974921] Local APIC not detected. Using dummy APIC emulation.
[   14.975011] Brought up 1 CPUs
[   14.975287] Booting paravirtualized kernel on bare hardware
[   14.975405] Time:  6:07:06  Date: 02/04/108
[   14.975464] NET: Registered protocol family 16
[   14.975660] EISA bus registered
[   14.975684] ACPI: bus type pci registered
[   14.978151] PCI: PCI BIOS revision 2.10 entry at 0xf1180, last bus=1
[   14.978157] PCI: Using configuration type 1
[   14.978160] Setting up standard PCI resources
[   14.990141] ACPI: EC: Look up EC in DSDT
[   14.993867] ACPI: Interpreter enabled
[   14.993873] ACPI: (supports S0 S1 S4 S5)
[   14.993903] ACPI: Using PIC for interrupt routing
[   15.005044] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   15.005067] PCI: Probing PCI hardware (bus 00)
[   15.005202] Disabling VIA memory write queue (PCI ID 0305, rev 03): [55] 89 & 1f -> 09
[   15.005450] PCI quirk: region e200-e27f claimed by vt82c686 HW-mon
[   15.005456] PCI quirk: region e800-e80f claimed by vt82c686 SMB
[   15.005751] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   15.064389] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   15.064538] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   15.064680] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   15.064821] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 *6 7 9 10 11 12 14 15)
[   15.064963] Linux Plug and Play Support v0.97 (c) Adam Belay
[   15.064999] pnp: PnP ACPI init
[   15.065016] ACPI: bus type pnp registered
[   15.069137] pnp: PnP ACPI: found 14 devices
[   15.069142] ACPI: ACPI bus type pnp unregistered
[   15.069150] PnPBIOS: Disabled by ACPI PNP
[   15.069271] PCI: Using ACPI for IRQ routing
[   15.069277] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   15.076754] NET: Registered protocol family 8
[   15.076758] NET: Registered protocol family 20
[   15.076894] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
[   15.076901] pnp: 00:00: iomem range 0xf0000-0xfffff could not be reserved
[   15.076907] pnp: 00:00: iomem range 0x100000-0x1fffffff could not be reserved
[   15.076914] pnp: 00:00: iomem range 0xfffe0000-0xffffffff could not be reserved
[   15.076931] pnp: 00:03: ioport range 0xe400-0xe47f has been reserved
[   15.076937] pnp: 00:03: ioport range 0xe800-0xe80f has been reserved
[   15.079806] Time: tsc clocksource has been installed.
[   15.107549] PCI: Bridge: 0000:00:01.0
[   15.107554]   IO window: d000-dfff
[   15.107562]   MEM window: d7000000-d7efffff
[   15.107568]   PREFETCH window: d7f00000-e5ffffff
[   15.107590] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   15.107612] NET: Registered protocol family 2
[   15.143896] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   15.144009] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   15.144617] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   15.145161] TCP: Hash tables configured (established 16384 bind 16384)
[   15.145167] TCP reno registered
[   15.156079] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0
[   15.724178]  it is
[   16.407628] Freeing initrd memory: 7340k freed
[   16.407857] Simple Boot Flag at 0x3a set to 0x1
[   16.408435] audit: initializing netlink socket (disabled)
[   16.408463] audit(1204610826.864:1): initialized
[   16.412186] VFS: Disk quotas dquot_6.5.1
[   16.412301] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   16.412508] io scheduler noop registered
[   16.412513] io scheduler anticipatory registered
[   16.412517] io scheduler deadline registered
[   16.412545] io scheduler cfq registered (default)
[   16.412575] Applying VIA southbridge workaround.
[   16.412582] PCI: VIA PCI bridge detected. Disabling DAC.
[   16.412588] PCI: Disabling Via external APIC routing
[   16.412629] Boot video device is 0000:01:00.0
[   16.412932] isapnp: Scanning for PnP cards...
[   16.767248] isapnp: No Plug & Play device found
[   16.822945] Real Time Clock Driver v1.12ac
[   16.823141] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   16.823299] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   16.823708] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   16.824886] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   16.825447] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   16.827063] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   16.827520] input: Macintosh mouse button emulation as /class/input/input0
[   16.827684] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   16.828123] serio: i8042 KBD port at 0x60,0x64 irq 1
[   16.828134] serio: i8042 AUX port at 0x60,0x64 irq 12
[   16.828450] mice: PS/2 mouse device common for all mice
[   16.828676] EISA: Probing bus 0 at eisa.0
[   16.828731] Cannot allocate resource for EISA slot 8
[   16.828736] EISA: Detected 0 cards.
[   16.829118] TCP cubic registered
[   16.829138] NET: Registered protocol family 1
[   16.829177] Using IPI No-Shortcut mode
[   16.829482]   Magic number: 0:977:113
[   16.830643] Freeing unused kernel memory: 364k freed
[   16.870867] input: AT Translated Set 2 keyboard as /class/input/input1
[   18.243851] AppArmor: AppArmor initialized<5>audit(1204610828.864:2):  type=1505 info="AppArmor initialized" pid=1171
[   18.256522] fuse init (API version 7.8)
[   18.266032] Failure registering capabilities with primary security module.
[   18.291999] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   18.292011] ACPI: Processor [CPU0] (supports 16 throttling states)
[   19.371862] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   19.371876] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   19.373095] VP_IDE: IDE controller at PCI slot 0000:00:04.1
[   19.373177] VP_IDE: chipset revision 6
[   19.373182] VP_IDE: not 100% native mode: will probe irqs later
[   19.373200] VP_IDE: VIA vt82c686b (rev 40) IDE UDMA100 controller on pci0000:00:04.1
[   19.373213]     ide0: BM-DMA at 0xb800-0xb807, BIOS settings: hda:DMA, hdb:pio
[   19.373232]     ide1: BM-DMA at 0xb808-0xb80f, BIOS settings: hdc:DMA, hdd:pio
[   19.373245] Probing IDE interface ide0...
[   19.438480] usbcore: registered new interface driver usbfs
[   19.438533] usbcore: registered new interface driver hub
[   19.438589] usbcore: registered new device driver usb
[   19.440363] USB Universal Host Controller Interface driver v3.0
[   19.502345] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   19.805110] hda: ST320011A, ATA DISK drive
[    5.680000] Marking TSC unstable due to: possible TSC halt in C2.
[    5.684000] Time: acpi_pm clocksource has been installed.
[    6.264000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    6.268000] Probing IDE interface ide1...
[    7.132000] hdc: LITE-ON DVDRW SHW-160P6S, ATAPI CD/DVD-ROM drive
[    7.804000] ide1 at 0x170-0x177,0x376 on irq 15
[    7.832000] SCSI subsystem initialized
[    7.840000] libata version 2.21 loaded.
[    7.848000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 6
[    7.848000] PCI: setting IRQ 6 as level-triggered
[    9.608000] irq 6: nobody cared (try booting with the "irqpoll" option)
[    9.608000]  [<c015b5b4>] __report_bad_irq+0x24/0x80
[    9.608000]  [<c015b872>] note_interrupt+0x262/0x2a0
[    9.608000]  [<e08631f2>] floppy_interrupt+0xd2/0x1d0 [floppy]
[    9.608000]  [<c015aad0>] handle_IRQ_event+0x30/0x60
[    9.608000]  [<c015c48b>] handle_level_irq+0xdb/0x110
[    9.608000]  [<c0106b1b>] do_IRQ+0x3b/0x70
[    9.608000]  [<c0105223>] common_interrupt+0x23/0x30
[    9.608000]  [<c012d691>] __do_softirq+0x61/0x110
[    9.608000]  [<c012d795>] do_softirq+0x55/0x60
[    9.608000]  [<c012da7d>] irq_exit+0x6d/0x80
[    9.608000]  [<c0106b20>] do_IRQ+0x40/0x70
[    9.608000]  [<c0105223>] common_interrupt+0x23/0x30
[    9.608000]  [<c02765cf>] eisa_set_level_irq+0x7f/0x90
[    9.608000]  [<c01131b7>] acpi_register_gsi+0x47/0x60
[    9.608000]  [<c0236225>] acpi_pci_irq_enable+0x133/0x1da
[    9.608000]  [<c023601b>] acpi_pci_allocate_irq+0x0/0x4d
[    9.608000]  [<c0277278>] pcibios_enable_device+0x28/0x30
[    9.608000]  [<c0206fc2>] do_pci_enable_device+0x22/0x50
[    9.608000]  [<c0207017>] pci_enable_device_bars+0x27/0x40
[    9.608000]  [<e08c82e4>] usb_hcd_pci_probe+0x54/0x2c0 [usbcore]
[    9.608000]  [<c01c50b4>] sysfs_create_link+0xf4/0x140
[    9.608000]  [<c02099e3>] pci_match_device+0x13/0xc0
[    9.608000]  [<c0209b06>] pci_device_probe+0x56/0x80
[    9.608000]  [<c02611ae>] driver_probe_device+0x8e/0x190
[    9.608000]  [<c026141e>] __driver_attach+0x9e/0xa0
[    9.608000]  [<c026059b>] bus_for_each_dev+0x3b/0x60
[    9.608000]  [<c0261026>] driver_attach+0x16/0x20
[    9.608000]  [<c0261380>] __driver_attach+0x0/0xa0
[    9.608000]  [<c026096a>] bus_add_driver+0x8a/0x1b0
[    9.608000]  [<c0209cb3>] __pci_register_driver+0x53/0xa0
[    9.608000]  [<e083a087>] uhci_hcd_init+0x87/0xb2 [uhci_hcd]
[    9.608000]  [<c014a7f1>] sys_init_module+0x151/0x1a00
[    9.608000]  [<c01fb43f>] prio_tree_insert+0x1f/0x250
[    9.608000]  [<e0850000>] mii_ethtool_sset+0x0/0x1e0 [mii]
[    9.608000]  [<c0104252>] syscall_call+0x7/0xb
[    9.608000]  =======================
[    9.608000] handlers:
[    9.608000] [<e0866050>] (floppy_hardint+0x0/0x110 [floppy])
[    9.608000] Disabling IRQ #6
[    9.608000] ACPI: PCI Interrupt 0000:00:04.2[D] -> Link [LNKD] -> GSI 6 (level, low) -> IRQ 6
[    9.608000] uhci_hcd 0000:00:04.2: UHCI Host Controller
[    9.612000] uhci_hcd 0000:00:04.2: new USB bus registered, assigned bus number 1
[    9.612000] uhci_hcd 0000:00:04.2: request interrupt 6 failed
[    9.612000] uhci_hcd 0000:00:04.2: USB bus 1 deregistered
[    9.612000] ACPI: PCI interrupt for device 0000:00:04.2 disabled
[    9.612000] uhci_hcd 0000:00:04.2: init 0000:00:04.2 fail, -16
[    9.612000] uhci_hcd: probe of 0000:00:04.2 failed with error -16
[    9.612000] ACPI: PCI Interrupt 0000:00:04.3[D] -> Link [LNKD] -> GSI 6 (level, low) -> IRQ 6
[    9.612000] uhci_hcd 0000:00:04.3: UHCI Host Controller
[    9.616000] uhci_hcd 0000:00:04.3: new USB bus registered, assigned bus number 1
[    9.616000] uhci_hcd 0000:00:04.3: request interrupt 6 failed
[    9.616000] uhci_hcd 0000:00:04.3: USB bus 1 deregistered
[    9.616000] ACPI: PCI interrupt for device 0000:00:04.3 disabled
[    9.616000] uhci_hcd 0000:00:04.3: init 0000:00:04.3 fail, -16
[    9.616000] uhci_hcd: probe of 0000:00:04.3 failed with error -16
[    9.616000] floppy0: no floppy controllers found
[    9.616000] 8139cp 0000:00:0b.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    9.616000] 8139cp 0000:00:0b.0: Try the "8139too" driver instead.
[    9.620000] 8139too Fast Ethernet driver 0.9.28
[    9.620000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[    9.620000] PCI: setting IRQ 10 as level-triggered
[    9.620000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[    9.620000] eth0: RealTek RTL8139 at 0xe083c000, 00:a0:b0:02:cc:bb, IRQ 10
[    9.620000] eth0:  Identified 8139 chip type 'RTL-8139C'
[    9.640000] hda: max request size: 128KiB
[    9.664000] hda: 39102336 sectors (20020 MB) w/2048KiB Cache, CHS=38792/16/63, UDMA(100)
[    9.664000] hda: cache flushes not supported
[    9.664000]  hda: hda1 hda2 < hda5 >
[    9.700000] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[    9.700000] Uniform CD-ROM driver Revision: 3.20
[    9.924000] Attempting manual resume
[    9.924000] swsusp: Resume From Partition 3:5
[    9.924000] PM: Checking swsusp image.
[    9.924000] PM: Resume from disk failed.
[    9.968000] kjournald starting.  Commit interval 5 seconds
[    9.968000] EXT3-fs: mounted filesystem with ordered data mode.
[   19.824000] parport_pc: VIA 686A/8231 detected
[   19.824000] parport_pc: probing current configuration
[   19.824000] parport_pc: Current parallel port base: 0x378
[   19.824000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   19.856000] Linux agpgart interface v0.102 (c) Dave Jones
[   19.880000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   19.884000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.976000] agpgart: Detected VIA Twister-K/KT133x/KM133 chipset
[   19.980000] agpgart: AGP aperture is 32M @ 0xe6000000
[   20.008000] parport_pc: VIA parallel port: io=0x378, irq=7
[   20.644000] i2c-adapter i2c-9191: sensors disabled - enable with force_addr=0xe200
[   21.008000] input: PC Speaker as /class/input/input2
[   22.852000] irq 6: nobody cared (try booting with the "irqpoll" option)
[   22.852000]  [<c015b5b4>] __report_bad_irq+0x24/0x80
[   22.852000]  [<c015b872>] note_interrupt+0x262/0x2a0
[   22.852000]  [<e0a0b1f2>] floppy_interrupt+0xd2/0x1d0 [floppy]
[   22.852000]  [<c015aad0>] handle_IRQ_event+0x30/0x60
[   22.852000]  [<c015c48b>] handle_level_irq+0xdb/0x110
[   22.852000]  [<c0106b1b>] do_IRQ+0x3b/0x70
[   22.852000]  [<c0105223>] common_interrupt+0x23/0x30
[   22.852000]  [<c015aab6>] handle_IRQ_event+0x16/0x60
[   22.852000]  [<c015c433>] handle_level_irq+0x83/0x110
[   22.852000]  [<c0106b1b>] do_IRQ+0x3b/0x70
[   22.852000]  [<c01202c1>] __activate_task+0x21/0x40
[   22.852000]  [<c0105223>] common_interrupt+0x23/0x30
[   22.852000]  [<c015aab6>] handle_IRQ_event+0x16/0x60
[   22.852000]  [<c015c433>] handle_level_irq+0x83/0x110
[   22.852000]  [<c0106b1b>] do_IRQ+0x3b/0x70
[   22.852000]  [<c0105223>] common_interrupt+0x23/0x30
[   22.852000]  [<c02f410d>] _spin_unlock_irqrestore+0xd/0x20
[   22.852000]  [<c015b2d0>] setup_irq+0xe0/0x1b0
[   22.852000]  [<c0138509>] flush_cpu_workqueue+0x19/0x90
[   22.852000]  [<e0a0e050>] floppy_hardint+0x0/0x110 [floppy]
[   22.852000]  [<c015b443>] request_irq+0xa3/0xc0
[   22.852000]  [<e0973a62>] init_module+0x8f2/0xfb7 [floppy]
[   22.852000]  [<c01232a6>] __cond_resched+0x16/0x40
[   22.852000]  [<c02f272a>] cond_resched+0x2a/0x40
[   22.852000]  [<c02f2779>] wait_for_completion+0x19/0xe0
[   22.852000]  [<c014a7f1>] sys_init_module+0x151/0x1a00
[   22.852000]  [<c01041d2>] sysenter_past_esp+0x6b/0xa9
[   22.852000]  =======================
[   22.852000] handlers:
[   22.852000] [<e0a0e050>] (floppy_hardint+0x0/0x110 [floppy])
[   22.852000] Disabling IRQ #6
[   23.392000] input: ImExPS/2 Generic Explorer Mouse as /class/input/input3
[   23.528000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   23.528000] PCI: setting IRQ 11 as level-triggered
[   23.528000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   25.924000] floppy0: no floppy controllers found
[   26.420000] lp0: using parport0 (interrupt-driven).
[   26.500000] Adding 859436k swap on /dev/hda5.  Priority:-1 extents:1 across:859436k
[   26.916000] EXT3 FS on hda1, internal journal
[   28.716000] No dock devices found.
[   28.984000] input: Power Button (FF) as /class/input/input4
[   28.992000] ACPI: Power Button (FF) [PWRF]
[   29.060000] input: Power Button (CM) as /class/input/input5
[   29.060000] ACPI: Power Button (CM) [PWRB]
[   29.416000] powernow: No powernow capabilities detected
[   31.220000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   31.392000] ppdev: user-space parallel port driver
[   31.564000] audit(1204610856.939:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4445 profile="/usr/sbin/cupsd"
[   31.688000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   31.688000] apm: overridden by ACPI.
[   32.092000] Failure registering capabilities with primary security module.
[   32.412000] Bluetooth: Core ver 2.11
[   32.412000] NET: Registered protocol family 31
[   32.412000] Bluetooth: HCI device and connection manager initialized
[   32.412000] Bluetooth: HCI socket layer initialized
[   32.444000] Bluetooth: L2CAP ver 2.8
[   32.444000] Bluetooth: L2CAP socket layer initialized
[   32.460000] Bluetooth: RFCOMM socket layer initialized
[   32.460000] Bluetooth: RFCOMM TTY layer initialized
[   32.460000] Bluetooth: RFCOMM ver 1.8
[   33.764000] [drm] Initialized drm 1.1.0 20060810
[   33.776000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   33.784000] [drm] Initialized radeon 1.27.0 20060524 on minor 0
[   34.352000] NET: Registered protocol family 10
[   34.352000] lo: Disabled Privacy Extensions
[   36.028000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   36.028000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   36.028000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   36.292000] [drm] Setting GART location based on new memory map
[   36.292000] [drm] Loading R200 Microcode
[   36.292000] [drm] writeback test succeeded in 1 usecs
[   36.852000] NET: Registered protocol family 17
[   49.024000] eth0: no IPv6 routers present


that's all information that need for my solution?

---

### Post by Mark_in_Hollywood on 2008-03-04
Please turn off your computer. Unplug ALL usb devices, memory, usb harddrives, printer, scanner, ALL. Restart Ubuntu in Recovery mode. When it has finished loading, logout with:

shutdown -r now

restart normally. Shutdown, again, without restart. Plug in one (1) usb device. Restart. See if lsusb lists it. If yes, you are good to go. If no, post the output of lspci and lsusb here.

---

### Post by ripmillar on 2008-03-04
Wow... THANKS

I'm very appreciate for your help :):):)

after I try follow your suggestion..  lsusb show me this :)

> Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 067b:2528 Prolific Technology, Inc. 
Bus 001 Device 001: ID 0000:0000  

I really love this forum :lolflag:

---

### Post by Mark_in_Hollywood on 2008-03-06
If your devices are now found and working, please mark this thread as SOLVED by using the Thread Tools radio button at the top of this post.

---

### Post by ripmillar on 2008-03-06
T^T

since I show you what lsusb show.. I still can't find the way to make my usb work....

could you tell me how can I do =_=''


Thanks for future

---

### Post by Mark_in_Hollywood on 2008-03-08
Please give the name of the manufacturer of the usb device(s) and the model numbers or otherwise describe them so I know what we are looking at.

Prolific Technology, Inc.  seems to be the usb stuff on the motherboard.

---

### Post by ripmillar on 2008-03-09
it's A-data USB 2.0 flash drive 1Gb follow this link

[http://www.adata.com.tw/adata_en/product_show.php?ProductNo=AR19ZZZOR](http://www.adata.com.tw/adata_en/product_show.php?ProductNo=AR19ZZZOR)

sorry to reply late and thaks for your kindly. ^_^

---

### Post by Mark_in_Hollywood on 2008-03-11
Have you tried this device in another computer or any thing with a USB port? If you don't have any other device, try a friend's computer, a public library, or an internet cafe.

Let's make sure you have a known good working flash drive. As crazy as it seems, sometimes, things go bad "mechanically". If that's the case, I hope your device is under warranty.

If it's working on other computers/devices, you need to test 1 or more of your usb ports and double-check that they are working, too. Crazy as it seems . . .

If the device is good and the usb ports are good, then we need to see if it's found in /dev/disk/by-uuid. If the a-data is listed let me know. If it's not listed, start poking around your BIOS, carefully, noting settings. Post that info.

---

### Post by SmallFish on 2008-03-14
although this thread has been awhile, i  feel like this is still an issue.

I am having the same issue that my laptop not recognizing usb once awhile. I would not see my s510 keyboard and mouse with isusb or cat /proc/cat /proc/bus/input/devices
.  It usually got it resolves after a long shutdown like 15 minutes or so.  For quick reboot, it will not resolved it most of the time. I think something is cached .. in the /proc ? may be?

Here is my spec.
dell e1505
2 gig memory
s510 logitech wireless keyboard and mouse combo
ubuntu 7.04 up to date kernel

---

### Post by rusyear04 on 2008-03-15
hi there!

I tried to solve the "Isusb-problem" with the described shutdown procedure. unfortunatelly things did not chage.

all i get are "command not found" messages, for both "Isusb" and "Ispci"

```
user@home:~$ Isusb
bash: Isusb: command not found
user@home:~$ Ispci
bash: Ispci: command not found
```

do you have a clue what is wrong?
thanx!

---

### Post by Mark_in_Hollywood on 2008-03-19
substitute the letter

L

or in lower-case:

                    l

for the 

      I 

you used.

---

