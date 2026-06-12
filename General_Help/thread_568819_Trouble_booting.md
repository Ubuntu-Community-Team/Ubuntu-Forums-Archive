---
title: "Trouble booting"
date: 2007-10-06
forum: General Help
---

### Post by nawitus on 2007-10-06
About 50% of the time Ubuntu wont boot. When it does it seems to work correctly. I've had this problem with both 7.04 and 7.10. I use noapic nolapic boot parameters, and tried stuff like irqfixup and remove splash and quiet.. doesn't make a difference.

[[IMG]http://img257.imageshack.us/img257/5584/bugkh2.th.jpg[/IMG]](http://img257.imageshack.us/my.php?image=bugkh2.jpg)

I'm using HP pavilion dv6544eo laptop.

EDIT:
I changed fstab and grub/menu.lst files to use /dev/sda2 (my root) instead of UUID method, and I got the same error.. and the second boot it worked.

So, the problem is clearly that linux is having trouble detecting my root partition..

```

~ $ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc23d5aee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9740    78236518+   7  HPFS/NTFS
/dev/sda2           16164       19196    24362572+  83  Linux
/dev/sda3           19197       19457     2096482+  82  Linux swap / Solaris
/dev/sda4            9741       16163    51592747+  83  Linux

Partition table entries are not in disk order
~ $ ls /dev/disk/by-uuid -alh
total 0
drwxr-xr-x 2 root root 120 2007-10-06 21:43 .
drwxr-xr-x 5 root root 100 2007-10-06 21:43 ..
lrwxrwxrwx 1 root root  10 2007-10-06 21:43 1CC4ADDBC4ADB802 -> ../../sda1
lrwxrwxrwx 1 root root  10 2007-10-06 21:43 3439fb11-ee6f-443a-9635-73ee7268e31c -> ../../sda4
lrwxrwxrwx 1 root root  10 2007-10-06 21:43 7e7c0b1a-e1ac-4d89-adf0-f940111778af -> ../../sda3
lrwxrwxrwx 1 root root  10 2007-10-06 21:43 82e37328-095e-4fd8-87ca-a74c6decc746 -> ../../sda2

```

```

#/etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

/dev/sda2 / ext3 defaults,errors=remount-ro 0 1
UUID=1CC4ADDBC4ADB802 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda3 none swap sw 0 0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda4       /media/disk     ext3     defaults     0     0

```

---

### Post by nawitus on 2007-10-06
I updated grub but still having the same problem.. Sometimes the last lines I see are bunch of "SATA link down", but I see them when I boot succesfully too.. Here's some info after a succesful boot

dmesg
```

[    0.000000] Linux version 2.6.22-13-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Thu Oct 4 17:18:44 GMT 2007 (Ubuntu 2.6.22-13.40-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ff60000 (usable)
[    0.000000]  BIOS-e820: 000000007ff60000 - 000000007ff6e000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ff6e000 - 000000007ff6f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ff6f000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 1151MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f8650
[    0.000000] Entering add_active_range(0, 0, 524128) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   524128
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   524128
[    0.000000] On node 0 totalpages: 524128
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2302 pages used for memmap
[    0.000000]   HighMem zone: 292450 pages, LIFO batch:31
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F85A0 checksum 0
[    0.000000] ACPI: RSDP 000F85A0, 0024 (r2 PTLTD )
[    0.000000] ACPI: XSDT 7FF649A9, 006C (r1 HPQOEM SLIC-MPC  6040000  LTP        0)
[    0.000000] ACPI: FACP 7FF6D92A, 00F4 (r3 NVIDIA MCP65-E   6040000 PTL_    F4240)
[    0.000000] ACPI: DSDT 7FF64A15, 8EA1 (r1 NVIDIA    MCP65  6040000 MSFT  3000000)
[    0.000000] ACPI: FACS 7FF6EFC0, 0040
[    0.000000] ACPI: SRAT 7FF6DA1E, 00A0 (r1 AMD    HAMMER    6040000 AMD         1)
[    0.000000] ACPI: WDAT 7FF6DABE, 0104 (r1 PTLTD  WDATTBL   6040000  LTP        1)
[    0.000000] ACPI: SSDT 7FF6DBC2, 01C4 (r1 PTLTD  POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: MCFG 7FF6DD86, 003C (r1 HP       MCFG    6040000  LTP        0)
[    0.000000] ACPI: HPET 7FF6DDC2, 0038 (r1 PTLTD  HPETTBL   6040000  LTP        1)
[    0.000000] ACPI: APIC 7FF6DDFA, 0068 (r1 HP     	 APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT 7FF6DE62, 0028 (r1     HP $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SLIC 7FF6DE8A, 0176 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] OEM ID: nVIDIA   Product ID: MCP65-EMU    APIC at: 0xFEE00000
[    0.000000] Processor #0 15:8 APIC version 16
[    0.000000] Processor #1 15:8 APIC version 16
[    0.000000] I/O APIC #2 Version 17 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 2
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] Built 1 zonelists.  Total pages: 520034
[    0.000000] Kernel command line: root=/dev/sda2 ro noapic nolapic irqfixup nodma
[    0.000000] Misrouted IRQ fixup support enabled.
[    0.000000] This may impact system performance.
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1808.250 MHz processor.
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Memory: 2067080k/2096512k available (2015k kernel code, 28216k reserved, 916k data, 364k init, 1179008k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.000000]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[    0.000000]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[    0.000000]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    0.000000] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[    0.000000] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.000000] hpet0: 3 32-bit timers, 25000000 Hz
[    0.080000] Calibrating delay using timer specific routine.. 3620.06 BogoMIPS (lpj=7240122)
[    0.080000] Security Framework v1.0.0 initialized
[    0.080000] SELinux:  Disabled at boot.
[    0.080000] Mount-cache hash table entries: 512
[    0.080000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
[    0.080000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.080000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.080000] CPU 0(2) -> Core 0
[    0.080000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f
[    0.080000] Compat vDSO mapped to ffffe000.
[    0.080000] Checking 'hlt' instruction... OK.
[    0.096000] SMP alternatives: switching to UP code
[    0.096000] Early unpacking initramfs... done
[    0.416000] ACPI: Core revision 20070126
[    0.416000] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    0.420000] ACPI: setting ELCR to 0200 (from 8ca0)
[    0.424000] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-56 stepping 02
[    0.424000] SMP alternatives: switching to SMP code
[    0.424000] Booting processor 1/1 eip 3000
[    0.436000] Initializing CPU#1
[    0.516000] Calibrating delay using timer specific routine.. 3616.42 BogoMIPS (lpj=7232857)
[    0.516000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
[    0.516000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.516000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.516000] CPU 1(2) -> Core 1
[    0.516000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f
[    0.516000] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-56 stepping 02
[    0.516000] Total of 2 processors activated (7236.48 BogoMIPS).
[    0.516000] Brought up 2 CPUs
[    0.536000] migration_cost=4000
[    0.536000] Booting paravirtualized kernel on bare hardware
[    0.536000] Time: 21:26:22  Date: 09/06/107
[    0.536000] NET: Registered protocol family 16
[    0.536000] EISA bus registered
[    0.536000] ACPI: bus type pci registered
[    0.556000] PCI: PCI BIOS revision 3.00 entry at 0xfde1b, last bus=9
[    0.556000] PCI: Using configuration type 1
[    0.556000] Setting up standard PCI resources
[    0.560000] ACPI: EC: Look up EC in DSDT
[    0.560000] ACPI: EC: GPE=0x10, ports=0x66, 0x62
[    0.560000] ACPI: System BIOS is requesting _OSI(Linux)
[    0.560000] ACPI: Please test with "acpi_osi=!Linux"
[    0.560000] Please send dmidecode to linux-acpi@vger.kernel.org
[    0.560000] ACPI: Interpreter enabled
[    0.560000] ACPI: (supports S0 S3 S4 S5)
[    0.560000] ACPI: Using PIC for interrupt routing
[    0.568000] ACPI: EC: GPE=0x10, ports=0x66, 0x62
[    0.568000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.568000] PCI: Probing PCI hardware (bus 00)
[    0.572000] PCI: Transparent bridge - 0000:00:08.0
[    0.572000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.572000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.572000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR0._PRT]
[    0.572000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[    0.572000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[    0.572000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR3._PRT]
[    0.592000] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 *15)
[    0.596000] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 *10 11 14 15)
[    0.596000] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.596000] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.596000] ACPI: PCI Interrupt Link [LK1E] (IRQs 5 7 9 10 *11 14 15)
[    0.600000] ACPI: PCI Interrupt Link [LK2E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.600000] ACPI: PCI Interrupt Link [LK3E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.600000] ACPI: PCI Interrupt Link [LK4E] (IRQs 5 7 9 10 11 14 *15)
[    0.600000] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[    0.604000] ACPI: PCI Interrupt Link [LUS0] (IRQs 5 7 9 10 *11 14 15)
[    0.604000] ACPI: PCI Interrupt Link [LUS2] (IRQs 5 *7 9 10 11 14 15)
[    0.604000] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
[    0.604000] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
[    0.604000] ACPI: PCI Interrupt Link [LPID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.608000] ACPI: PCI Interrupt Link [LTID] (IRQs *5 7 9 10 11 14 15)
[    0.608000] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.608000] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.608000] pnp: PnP ACPI init
[    0.608000] ACPI: bus type pnp registered
[    0.608000] ACPI Error (dsopcode-0548): Field [I9MN] at 544 exceeds Buffer [IORT] size 464 (bits) [20070126]
[    0.608000] ACPI Error (psparse-0551): Method parse/execution failed [\_SB_.PCI0.LPC0.PMIO._CRS] (Node df85b7c8), AE_AML_BUFFER_LIMIT
[    0.612000] ACPI Error (uteval-0236): Method execution failed [\_SB_.PCI0.LPC0.PMIO._CRS] (Node df85b7c8), AE_AML_BUFFER_LIMIT
[    0.612000] pnp: PnPACPI: METHOD_NAME__CRS failure for PNP0c02
[    0.612000] pnp: PnP ACPI: found 11 devices
[    0.612000] ACPI: ACPI bus type pnp unregistered
[    0.612000] PnPBIOS: Disabled by ACPI PNP
[    0.612000] PCI: Using ACPI for IRQ routing
[    0.612000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.636000] NET: Registered protocol family 8
[    0.636000] NET: Registered protocol family 20
[    0.636000] pnp: 00:02: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.636000] pnp: 00:0a: iomem range 0xffc00000-0xffffffff could not be reserved
[    0.636000] pnp: 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.636000] pnp: 00:0a: iomem range 0xfed00000-0xfed00fff has been reserved
[    0.640000] Time: hpet clocksource has been installed.
[    0.640000] pnp: 00:0a: iomem range 0xfec80000-0xfec80fff has been reserved
[    0.668000] PCI: Bridge: 0000:00:08.0
[    0.668000]   IO window: disabled.
[    0.668000]   MEM window: b0100000-b01fffff
[    0.668000]   PREFETCH window: disabled.
[    0.668000] PCI: Bridge: 0000:00:0b.0
[    0.668000]   IO window: disabled.
[    0.668000]   MEM window: disabled.
[    0.668000]   PREFETCH window: disabled.
[    0.668000] PCI: Bridge: 0000:00:0c.0
[    0.668000]   IO window: disabled.
[    0.668000]   MEM window: b0200000-b02fffff
[    0.668000]   PREFETCH window: disabled.
[    0.668000] PCI: Failed to allocate mem resource #6:20000@d0000000 for 0000:05:00.0
[    0.668000] PCI: Bridge: 0000:00:0d.0
[    0.668000]   IO window: 4000-4fff
[    0.672000]   MEM window: b1000000-b3ffffff
[    0.672000]   PREFETCH window: c0000000-cfffffff
[    0.672000] PCI: Bridge: 0000:00:0e.0
[    0.672000]   IO window: 5000-5fff
[    0.672000]   MEM window: b4000000-b5ffffff
[    0.672000]   PREFETCH window: d0000000-d01fffff
[    0.672000] PCI: Setting latency timer of device 0000:00:08.0 to 64
[    0.672000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[    0.672000] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[    0.672000] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[    0.672000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[    0.672000] NET: Registered protocol family 2
[    0.720000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.720000] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[    0.720000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.720000] TCP: Hash tables configured (established 131072 bind 65536)
[    0.720000] TCP reno registered
[    0.736000] checking if image is initramfs... it is
[    1.364000] Freeing initrd memory: 7095k freed
[    1.364000] Simple Boot Flag at 0x36 set to 0x1
[    1.364000] audit: initializing netlink socket (disabled)
[    1.364000] audit(1191705982.140:1): initialized
[    1.368000] highmem bounce pool size: 64 pages
[    1.368000] VFS: Disk quotas dquot_6.5.1
[    1.368000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.368000] io scheduler noop registered
[    1.368000] io scheduler anticipatory registered
[    1.368000] io scheduler deadline registered
[    1.368000] io scheduler cfq registered (default)
[    1.368000] Boot video device is 0000:05:00.0
[    1.368000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[    1.368000] assign_interrupt_mode Found MSI capability
[    1.368000] Allocate Port Service[0000:00:0b.0:pcie00]
[    1.368000] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[    1.368000] assign_interrupt_mode Found MSI capability
[    1.368000] Allocate Port Service[0000:00:0c.0:pcie00]
[    1.368000] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[    1.368000] assign_interrupt_mode Found MSI capability
[    1.368000] Allocate Port Service[0000:00:0d.0:pcie00]
[    1.368000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[    1.368000] assign_interrupt_mode Found MSI capability
[    1.368000] Allocate Port Service[0000:00:0e.0:pcie00]
[    1.368000] isapnp: Scanning for PnP cards...
[    1.724000] isapnp: No Plug & Play device found
[    1.744000] Real Time Clock Driver v1.12ac
[    1.744000] hpet_resources: 0xfed00000 is busy
[    1.744000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.744000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.744000] input: Macintosh mouse button emulation as /class/input/input0
[    1.744000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.772000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.772000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.772000] mice: PS/2 mouse device common for all mice
[    1.776000] EISA: Probing bus 0 at eisa.0
[    1.776000] Cannot allocate resource for EISA slot 1
[    1.776000] Cannot allocate resource for EISA slot 3
[    1.776000] Cannot allocate resource for EISA slot 4
[    1.776000] Cannot allocate resource for EISA slot 5
[    1.776000] EISA: Detected 0 cards.
[    1.776000] TCP cubic registered
[    1.776000] NET: Registered protocol family 1
[    1.776000] Using IPI No-Shortcut mode
[    1.776000]   Magic number: 11:78:449
[    1.776000] Freeing unused kernel memory: 364k freed
[    1.792000] input: AT Translated Set 2 keyboard as /class/input/input1
[    1.992000] AppArmor: AppArmor initialized<5>audit(1191705982.640:2):  type=1505 info="AppArmor initialized" pid=1241
[    2.000000] fuse init (API version 7.8)
[    2.008000] Failure registering capabilities with primary security module.
[    2.040000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.040000] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.040000] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.040000] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.040000] ACPI Exception (thermal-0311): AE_BAD_DATA, No critical threshold [20070126]
[    2.628000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    2.628000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    2.628000] NFORCE-MCP65: IDE controller at PCI slot 0000:00:09.0
[    2.628000] NFORCE-MCP65: chipset revision 161
[    2.628000] NFORCE-MCP65: not 100% native mode: will probe irqs later
[    2.628000] NFORCE-MCP65: BIOS didn't set cable bits correctly. Enabling workaround.
[    2.628000] NFORCE-MCP65: 0000:00:09.0 (rev a1) UDMA133 controller
[    2.628000]     ide0: BM-DMA at 0x30c0-0x30c7, BIOS settings: hda:DMA, hdb:pio
[    2.628000] Probing IDE interface ide0...
[    2.640000] usbcore: registered new interface driver usbfs
[    2.640000] usbcore: registered new interface driver hub
[    2.640000] usbcore: registered new device driver usb
[    2.640000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.660000] SCSI subsystem initialized
[    2.664000] libata version 2.21 loaded.
[    2.744000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[    3.376000] hda: MATSHITADVD-RAM UJ-851S, ATAPI CD/DVD-ROM drive
[    3.712000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    3.712000] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 11
[    3.712000] PCI: setting IRQ 11 as level-triggered
[    3.712000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LUS0] -> GSI 11 (level, low) -> IRQ 11
[    3.712000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    3.712000] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    3.716000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[    3.716000] ohci_hcd 0000:00:02.0: irq 11, io mem 0xb0006000
[    3.772000] usb usb1: configuration #1 chosen from 1 choice
[    3.772000] hub 1-0:1.0: USB hub found
[    3.772000] hub 1-0:1.0: 10 ports detected
[    3.876000] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 7
[    3.876000] PCI: setting IRQ 7 as level-triggered
[    3.876000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LUS2] -> GSI 7 (level, low) -> IRQ 7
[    3.876000] PCI: Setting latency timer of device 0000:00:02.1 to 64
[    3.876000] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    3.876000] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[    3.876000] ehci_hcd 0000:00:02.1: debug port 1
[    3.876000] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[    3.876000] ehci_hcd 0000:00:02.1: irq 7, io mem 0xb0007000
[    3.876000] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.876000] usb usb2: configuration #1 chosen from 1 choice
[    3.876000] hub 2-0:1.0: USB hub found
[    3.876000] hub 2-0:1.0: 10 ports detected
[    3.980000] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 15
[    3.980000] PCI: setting IRQ 15 as level-triggered
[    3.980000] ACPI: PCI Interrupt 0000:07:05.0[A] -> Link [LNK1] -> GSI 15 (level, low) -> IRQ 15
[    3.980000] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 10
[    3.980000] PCI: setting IRQ 10 as level-triggered
[    3.980000] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LMAC] -> GSI 10 (level, low) -> IRQ 10
[    3.980000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[    3.980000] forcedeth: using HIGHDMA
[    3.980000] 0000:00:06.0: Invalid Mac address detected: 17:a0:73:24:1b:00
[    3.980000] Please complain to your hardware vendor. Switching to a random MAC.
[    4.032000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[15]  MMIO=[b0100000-b01007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.044000] hda: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, (U)DMA
[    4.048000] Uniform CD-ROM driver Revision: 3.20
[    4.504000] eth0: forcedeth.c: subsystem: 0103c:30cf bound to 0000:00:06.0
[    4.504000] ahci 0000:00:0a.0: version 2.2
[    4.504000] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 5
[    4.504000] PCI: setting IRQ 5 as level-triggered
[    4.504000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LTID] -> GSI 5 (level, low) -> IRQ 5
[    4.612000] usb 2-4: new high speed USB device using ehci_hcd and address 3
[    4.752000] usb 2-4: configuration #1 chosen from 1 choice
[    5.056000] usb 1-2: new low speed USB device using ohci_hcd and address 2
[    5.268000] usb 1-2: configuration #1 chosen from 1 choice
[    5.280000] usbcore: registered new interface driver hiddev
[    5.288000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
[    5.288000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:02.0-2
[    5.288000] usbcore: registered new interface driver usbhid
[    5.288000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[    5.308000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b0029f63b00]
[    5.508000] ahci 0000:00:0a.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[    5.508000] ahci 0000:00:0a.0: flags: 64bit ncq pm led clo pmp pio 
[    5.508000] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[    5.508000] scsi0 : ahci
[    5.508000] scsi1 : ahci
[    5.508000] scsi2 : ahci
[    5.508000] scsi3 : ahci
[    5.508000] ata1: SATA max UDMA/133 cmd 0xf8874100 ctl 0x00000000 bmdma 0x00000000 irq 5
[    5.508000] ata2: SATA max UDMA/133 cmd 0xf8874180 ctl 0x00000000 bmdma 0x00000000 irq 5
[    5.508000] ata3: SATA max UDMA/133 cmd 0xf8874200 ctl 0x00000000 bmdma 0x00000000 irq 5
[    5.508000] ata4: SATA max UDMA/133 cmd 0xf8874280 ctl 0x00000000 bmdma 0x00000000 irq 5
[   11.032000] ata1: port is slow to respond, please be patient (Status 0x80)
[   15.848000] ata1: softreset failed (device not ready)
[   16.324000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   16.324000] ata1.00: ATA-7: Hitachi HTS541616J9SA00, SB4OC7BP, max UDMA/100
[   16.324000] ata1.00: 312581808 sectors, multi 16: LBA48 
[   16.324000] ata1.00: configured for UDMA/100
[   16.636000] ata2: SATA link down (SStatus 0 SControl 300)
[   16.948000] ata3: SATA link down (SStatus 0 SControl 300)
[   17.260000] ata4: SATA link down (SStatus 0 SControl 300)
[   17.260000] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SB4O PQ: 0 ANSI: 5
[   17.268000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   17.268000] sd 0:0:0:0: [sda] Write Protect is off
[   17.268000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   17.268000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   17.268000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   17.268000] sd 0:0:0:0: [sda] Write Protect is off
[   17.268000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   17.268000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   17.268000]  sda: sda1 sda2 sda3 sda4
[   17.720000] sd 0:0:0:0: [sda] Attached SCSI disk
[   17.724000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   17.984000] Attempting manual resume
[   17.984000] swsusp: Resume From Partition 8:3
[   17.984000] PM: Checking swsusp image.
[   17.984000] PM: Resume from disk failed.
[   18.024000] kjournald starting.  Commit interval 5 seconds
[   18.024000] EXT3-fs: mounted filesystem with ordered data mode.
[   28.376000] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x3040
[   28.376000] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x3000
[   28.508000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   28.544000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   28.716000] input: PC Speaker as /class/input/input3
[   28.988000] Linux agpgart interface v0.102 (c) Dave Jones
[   29.012000] sdhci: Secure Digital Host Controller Interface driver
[   29.012000] sdhci: Copyright(c) Pierre Ossman
[   29.012000] sdhci: SDHCI controller found at 0000:07:05.1 [1180:0822] (rev 22)
[   29.012000] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 10
[   29.012000] ACPI: PCI Interrupt 0000:07:05.1[B] -> Link [LNK2] -> GSI 10 (level, low) -> IRQ 10
[   29.012000] mmc0: SDHCI at 0xb0100800 irq 10 DMA
[   29.032000] Linux video capture interface: v2.00
[   29.352000] nvidia: module license 'NVIDIA' taints kernel.
[   29.536000] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   29.608000] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 15
[   29.608000] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [LK4E] -> GSI 15 (level, low) -> IRQ 15
[   29.608000] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   29.608000] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   29.608000] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[   29.672000] uvcvideo: Found UVC 1.00 device HP Webcam (064e:a101)
[   29.672000] usbcore: registered new interface driver uvcvideo
[   29.672000] USB Video Class driver (v0.1.0)
[   29.956000] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 11
[   29.956000] ACPI: PCI Interrupt 0000:00:07.0[B] -> Link [LAZA] -> GSI 11 (level, low) -> IRQ 11
[   29.956000] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   30.360000] lp: driver loaded but no devices found
[   30.420000] ndiswrapper version 1.45 loaded (smp=yes)
[   30.536000] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[   30.536000] ACPI: PCI Interrupt Link [LK1E] enabled at IRQ 11
[   30.536000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LK1E] -> GSI 11 (level, low) -> IRQ 11
[   30.536000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   30.544000] ndiswrapper: using IRQ 11
[   30.892000] wlan0: ethernet device 00:1a:73:75:86:2e using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4312.5.conf
[   30.892000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   30.892000] usbcore: registered new interface driver ndiswrapper
[   30.932000] Adding 2096472k swap on /dev/sda3.  Priority:-1 extents:1 across:2096472k
[   31.536000] EXT3 FS on sda2, internal journal
[   32.032000] kjournald starting.  Commit interval 5 seconds
[   32.032000] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   32.032000] EXT3 FS on sda4, internal journal
[   32.032000] EXT3-fs: mounted filesystem with ordered data mode.
[   32.424000] NET: Registered protocol family 17
[   33.552000] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   33.552000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   33.568000] No dock devices found.
[   33.652000] ACPI: AC Adapter [ACAD] (on-line)
[   33.756000] ACPI: Battery Slot [BAT0] (battery present)
[   33.768000] input: Power Button (FF) as /class/input/input5
[   33.768000] ACPI: Power Button (FF) [PWRF]
[   33.768000] input: Power Button (CM) as /class/input/input6
[   33.768000] ACPI: Power Button (CM) [PWRB]
[   33.768000] input: Sleep Button (CM) as /class/input/input7
[   33.768000] ACPI: Sleep Button (CM) [SLPB]
[   34.048000] powernow-k8: Found 2 AMD Turion(tm) 64 X2 Mobile Technology TL-56 processors (version 2.00.00)
[   34.048000] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x13
[   34.048000] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x15
[   34.048000] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x1e
[   35.416000] eth18: no link during initialization.
[   35.532000] apm: BIOS not found.
[   36.232000] Failure registering capabilities with primary security module.
[   36.500000] Clocksource tsc unstable (delta = -277807664 ns)
[   38.568000] NET: Registered protocol family 10
[   38.568000] lo: Disabled Privacy Extensions
[   38.568000] ADDRCONF(NETDEV_UP): eth18: link is not ready
[   48.908000] wlan0: no IPv6 routers present

```

lspci
```

00:00.0 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation MCP65 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP65 SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP65 SMU (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:06.0 Ethernet controller: nVidia Corporation MCP65 Ethernet (rev a3)
00:07.0 Audio device: nVidia Corporation MCP65 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP65 PCI bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP65 IDE (rev a1)
00:0a.0 IDE interface: nVidia Corporation MCP65 SATA Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 045b (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0e.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)
05:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

```

Help, please :(

**EDIT:**
I found a solution that has worked 3 boots so far.. I will reply if I get the problem again. I just added "all_generic_ide" to boot parameter.
[https://answers.launchpad.net/ubuntu/+question/14023](https://answers.launchpad.net/ubuntu/+question/14023)

---

