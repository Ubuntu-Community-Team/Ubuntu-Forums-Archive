---
title: "Trouble mounting ntfs drive."
date: 2008-04-25
forum: General Help
---

### Post by BluntBox on 2008-04-25
Hi all, I am having some trouble trying to mount one of my ntfs drives. My PC has 4 hard drives in it, 2 IDE and 2 SATA. All of which are working fine in XP, and were working fine in Gutsy.

IDE1 = Winxp (ntfs)
IDE2 = 200gb storage (ntfs)
SATA1 = Partions for Ubuntu
SATA2 = 160gb storage (ntfs)

Previously in Gutsy the 2 IDE drives would get the device names /dev/hdc1 /dev/hdd1 but now they are using /dev/sda1 /dev/sdb1.

I added the drives to fstab just like I had previously in Gutsy with:
```
/dev/sda1 /mnt/XP ntfs defaults 0 0
/dev/sdb1 /mnt/Storage ntfs defaults 0 0
```
sda1 works without a hitch, sdb1 refuses to mount (or be found)
```
ntfs-3g: Failed to access volume '/dev/sdb1': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.
```

Attempting to mount it with "ntfs-3g /dev/sdb1 /mnt/Storage -any combination of options" just returns the above error.

sudo fdisk -l :
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5a801662

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9fc62c7c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401    7  HPFS/NTFS

... 
other 2 drives that work fine (sdc sdd)
```

ls -l /dev/disk/by-uuid/ :
```
total 0
lrwxrwxrwx 1 root root 10 2008-04-26 09:51 2f2a6585-1c40-40df-bb16-37dc7b083027 -> ../../sdc1
lrwxrwxrwx 1 root root 10 2008-04-26 09:51 6830823930820DEE -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-04-26 09:51 6B7B43B41DD03CE9 -> ../../sdd1
lrwxrwxrwx 1 root root 10 2008-04-26 09:51 6d82c3c5-33b6-46f0-852e-44a169842ad9 -> ../../sdc2
lrwxrwxrwx 1 root root 10 2008-04-26 09:51 8f95cf07-6ffd-45e7-beac-f7186a03bf87 -> ../../sdc3
lrwxrwxrwx 1 root root 10 2008-04-26 09:51 b110cdcb-08c7-4a5d-aaa9-90ec04f01078 -> ../../sdc4
```

I was going to try and mount it using the UUID, but apparently it doesn't have one.

Any ideas?

---

### Post by hermes0710 on 2008-04-25
Any chance the device is "sdd1" and not "sdb1"?

---

### Post by BluntBox on 2008-04-25
Probably should have mentioned:
SATA1 contains sdc1(ext2), sdc2(ext3), sdc3(ext3), sdc4(swap)
SATA2 contains sdd1(ntfs) 

Which all mount correctly. Had just removed them from the fdisk output to save some space.

I've tried substituting different device names for sdb1, but then I get "mount: special device /dev/whatever does not exist" error (as expected).

---

### Post by hermes0710 on 2008-04-25
Can you post the output of ```
dmesg
```   and   ```
ls /dev/s*
```

?

---

### Post by BluntBox on 2008-04-25
```

[    0.000000] Linux version 2.6.24-16-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 12:47:45 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] Command line: root=UUID=6d82c3c5-33b6-46f0-852e-44a169842ad9 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fff0000 (usable)
[    0.000000]  BIOS-e820: 000000007fff0000 - 000000007fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff3000 - 0000000080000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fefffc00 - 00000000ff000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524272) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F7D50 checksum 0
[    0.000000] ACPI: RSDP 000F7D50, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 7FFF3040, 0030 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 7FFF30C0, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 7FFF3180, 6399 (r1 NVIDIA AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 7FFF0000, 0040
[    0.000000] ACPI: MCFG 7FFF9640, 003C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 7FFF9580, 006E (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] CPU has 1 num_cores
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007fff0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524272) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000007fff0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   524272
[    0.000000] On node 0 totalpages: 524175
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1208 pages reserved
[    0.000000]   DMA zone: 2735 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7111 pages used for memmap
[    0.000000]   DMA32 zone: 513065 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 515800
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=6d82c3c5-33b6-46f0-852e-44a169842ad9 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] TSC calibrated against PM_TIMER
[   16.101426] time.c: Detected 2211.329 MHz processor.
[   16.103663] Console: colour VGA+ 80x25
[   16.103666] console [tty0] enabled
[   16.103680] Checking aperture...
[   16.103683] CPU 0: aperture @ f9a2000000 size 32 MB
[   16.103684] Aperture too small (32 MB)
[   16.108343] No AGP bridge found
[   16.126490] Memory: 2054820k/2097088k available (2466k kernel code, 41880k reserved, 1309k data, 316k init)
[   16.126523] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   16.203404] Calibrating delay using timer specific routine.. 4425.40 BogoMIPS (lpj=8850811)
[   16.203433] Security Framework initialized
[   16.203441] SELinux:  Disabled at boot.
[   16.203454] AppArmor: AppArmor initialized
[   16.203458] Failure registering capabilities with primary security module.
[   16.203599] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   16.204843] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   16.205444] Mount-cache hash table entries: 256
[   16.205569] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   16.205571] CPU: L2 Cache: 512K (64 bytes/line)
[   16.205573] CPU 0/0 -> Node 0
[   16.205593] SMP alternatives: switching to UP code
[   16.206107] Freeing SMP alternatives: 24k freed
[   16.206413] Early unpacking initramfs... done
[   16.501848] ACPI: Core revision 20070126
[   16.501905] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   16.545233] Using local APIC timer interrupts.
[   16.590452] APIC timer calibration result 12564368
[   16.590453] Detected 12.564 MHz APIC timer.
[   16.590500] Brought up 1 CPUs
[   16.590559] CPU0 attaching sched-domain:
[   16.590561]  domain 0: span 01
[   16.590563]   groups: 01
[   16.590694] net_namespace: 120 bytes
[   16.591060] Time: 23:51:42  Date: 04/25/08
[   16.591086] NET: Registered protocol family 16
[   16.591230] ACPI: bus type pci registered
[   16.591286] PCI: Using configuration type 1
[   16.592296] ACPI: EC: Look up EC in DSDT
[   16.598230] ACPI: Interpreter enabled
[   16.598232] ACPI: (supports S0 S1 S3 S4 S5)
[   16.598246] ACPI: Using IOAPIC for interrupt routing
[   16.606196] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   16.606684] PCI: Transparent bridge - 0000:00:09.0
[   16.606903] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   16.607153] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   16.665355] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   16.665514] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   16.665674] ACPI: PCI Interrupt Link [LNK3] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   16.665830] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 7 9 10 11 *12 14 15)
[   16.665986] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   16.666144] ACPI: PCI Interrupt Link [LUBA] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   16.666302] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   16.666465] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   16.666622] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   16.666779] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   16.666936] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 7 9 10 11 *12 14 15)
[   16.667092] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   16.667249] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   16.667412] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 9 10 11 *12 14 15)
[   16.667579] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   16.667744] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   16.667859] ACPI: PCI Interrupt Link [APC1] (IRQs *16)
[   16.667971] ACPI: PCI Interrupt Link [APC2] (IRQs *17)
[   16.668086] ACPI: PCI Interrupt Link [APC3] (IRQs *18)
[   16.668197] ACPI: PCI Interrupt Link [APC4] (IRQs *19)
[   16.668308] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[   16.668485] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[   16.668661] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[   16.668834] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[   16.669005] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[   16.669177] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[   16.669348] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[   16.669520] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[   16.669691] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   16.669869] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   16.670047] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[   16.670224] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
[   16.670331] Linux Plug and Play Support v0.97 (c) Adam Belay
[   16.670353] pnp: PnP ACPI init
[   16.670360] ACPI: bus type pnp registered
[   16.674779] pnpacpi: exceeded the max number of mem resources: 12
[   16.674830] pnp: PnP ACPI: found 14 devices
[   16.674832] ACPI: ACPI bus type pnp unregistered
[   16.675007] PCI: Using ACPI for IRQ routing
[   16.675010] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   16.690467] NET: Registered protocol family 8
[   16.690469] NET: Registered protocol family 20
[   16.690565] AppArmor: AppArmor Filesystem Enabled
[   16.694452] Time: tsc clocksource has been installed.
[   16.702477] system 00:00: ioport range 0x4000-0x407f has been reserved
[   16.702479] system 00:00: ioport range 0x4080-0x40ff has been reserved
[   16.702481] system 00:00: ioport range 0x4400-0x447f has been reserved
[   16.702484] system 00:00: ioport range 0x4480-0x44ff has been reserved
[   16.702486] system 00:00: ioport range 0x4800-0x487f has been reserved
[   16.702488] system 00:00: ioport range 0x4880-0x48ff has been reserved
[   16.702493] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   16.702495] system 00:02: ioport range 0x800-0x87f has been reserved
[   16.702498] system 00:02: ioport range 0x290-0x297 has been reserved
[   16.702505] system 00:0c: iomem range 0xe0000000-0xefffffff could not be reserved
[   16.702510] system 00:0d: iomem range 0xf0000-0xf3fff could not be reserved
[   16.702512] system 00:0d: iomem range 0xf4000-0xf7fff could not be reserved
[   16.702514] system 00:0d: iomem range 0xf8000-0xfbfff could not be reserved
[   16.702517] system 00:0d: iomem range 0xfc000-0xfffff could not be reserved
[   16.702519] system 00:0d: iomem range 0x7fff0000-0x7fffffff could not be reserved
[   16.702521] system 00:0d: iomem range 0xffff0000-0xffffffff could not be reserved
[   16.702524] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[   16.702526] system 00:0d: iomem range 0x100000-0x7ffeffff could not be reserved
[   16.702528] system 00:0d: iomem range 0xfec00000-0xfec00fff could not be reserved
[   16.702530] system 00:0d: iomem range 0xfee00000-0xfeefffff could not be reserved
[   16.702532] system 00:0d: iomem range 0xfefff000-0xfeffffff could not be reserved
[   16.702535] system 00:0d: iomem range 0xfff80000-0xfff80fff has been reserved
[   16.702826] PCI: Bridge: 0000:00:09.0
[   16.702828]   IO window: a000-afff
[   16.702831]   MEM window: d3000000-d4ffffff
[   16.702832]   PREFETCH window: disabled.
[   16.702834] PCI: Bridge: 0000:00:0b.0
[   16.702835]   IO window: disabled.
[   16.702837]   MEM window: disabled.
[   16.702838]   PREFETCH window: disabled.
[   16.702840] PCI: Bridge: 0000:00:0c.0
[   16.702841]   IO window: disabled.
[   16.702843]   MEM window: disabled.
[   16.702844]   PREFETCH window: disabled.
[   16.702846] PCI: Bridge: 0000:00:0d.0
[   16.702847]   IO window: disabled.
[   16.702848]   MEM window: disabled.
[   16.702850]   PREFETCH window: disabled.
[   16.702852] PCI: Bridge: 0000:00:0e.0
[   16.702853]   IO window: disabled.
[   16.702855]   MEM window: d0000000-d2ffffff
[   16.702857]   PREFETCH window: c0000000-cfffffff
[   16.702863] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   16.702871] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   16.702876] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   16.702880] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   16.702885] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   16.702927] NET: Registered protocol family 2
[   16.738537] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   16.739178] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[   16.741628] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   16.742221] TCP: Hash tables configured (established 262144 bind 65536)
[   16.742224] TCP reno registered
[   16.750566] checking if image is initramfs... it is
[   17.206380] Switched to high resolution mode on CPU 0
[   17.328054] Freeing initrd memory: 8209k freed
[   17.333363] audit: initializing netlink socket (disabled)
[   17.333375] audit(1209167502.196:1): initialized
[   17.334925] VFS: Disk quotas dquot_6.5.1
[   17.334984] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   17.335088] io scheduler noop registered
[   17.335089] io scheduler anticipatory registered
[   17.335091] io scheduler deadline registered
[   17.335167] io scheduler cfq registered (default)
[   17.350501] PCI: Found disabled HT MSI Mapping on 0000:00:0b.0
[   17.350511] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   17.350516] PCI: Found disabled HT MSI Mapping on 0000:00:0c.0
[   17.350522] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   17.350526] PCI: Found disabled HT MSI Mapping on 0000:00:0d.0
[   17.350532] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   17.350536] PCI: Found disabled HT MSI Mapping on 0000:00:0e.0
[   17.350542] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   17.350550] Boot video device is 0000:01:00.0
[   17.350692] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   17.350708] assign_interrupt_mode Found MSI capability
[   17.350722] Allocate Port Service[0000:00:0b.0:pcie00]
[   17.350770] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   17.350785] assign_interrupt_mode Found MSI capability
[   17.350795] Allocate Port Service[0000:00:0c.0:pcie00]
[   17.350836] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   17.350850] assign_interrupt_mode Found MSI capability
[   17.350860] Allocate Port Service[0000:00:0d.0:pcie00]
[   17.350901] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   17.350914] assign_interrupt_mode Found MSI capability
[   17.350924] Allocate Port Service[0000:00:0e.0:pcie00]
[   17.372009] Real Time Clock Driver v1.12ac
[   17.372085] Linux agpgart interface v0.102
[   17.372087] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   17.372185] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   17.372624] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   17.373163] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   17.373217] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   17.373281] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   17.373283] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   17.373767] serio: i8042 KBD port at 0x60,0x64 irq 1
[   17.374683] mice: PS/2 mouse device common for all mice
[   17.374711] cpuidle: using governor ladder
[   17.374713] cpuidle: using governor menu
[   17.374832] NET: Registered protocol family 1
[   17.374880] registered taskstats version 1
[   17.374999]   Magic number: 4:646:909
[   17.375053]   hash matches device ptyz5
[   17.375110] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   17.375112] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   17.375114] EDD information not available.
[   17.375121] Freeing unused kernel memory: 316k freed
[   17.406324] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   18.548156] fuse init (API version 7.9)
[   18.559582] ACPI: Fan [FAN] (on)
[   18.563751] ACPI: Processor [CPU0] (supports 8 throttling states)
[   18.564935] ACPI: Thermal Zone [THRM] (40 C)
[   19.269977] usbcore: registered new interface driver usbfs
[   19.269996] usbcore: registered new interface driver hub
[   19.273978] usbcore: registered new device driver usb
[   19.289146] SCSI subsystem initialized
[   19.310479] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   19.310835] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[   19.310842] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 23
[   19.310944] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   19.310950] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   19.311123] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   19.311140] ohci_hcd 0000:00:02.0: irq 23, io mem 0xd5003000
[   19.347884] libata version 3.00 loaded.
[   19.368046] usb usb1: configuration #1 chosen from 1 choice
[   19.368069] hub 1-0:1.0: USB hub found
[   19.368078] hub 1-0:1.0: 10 ports detected
[   19.470392] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[   19.470400] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 22 (level, low) -> IRQ 22
[   19.470489] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   19.470495] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   19.470544] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   19.470568] ehci_hcd 0000:00:02.1: debug port 1
[   19.470571] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   19.470580] ehci_hcd 0000:00:02.1: irq 22, io mem 0xd5004000
[   19.481910] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   19.482031] usb usb2: configuration #1 chosen from 1 choice
[   19.482052] hub 2-0:1.0: USB hub found
[   19.482058] hub 2-0:1.0: 10 ports detected
[   19.586051] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   19.586374] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 21
[   19.586381] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APCH] -> GSI 21 (level, low) -> IRQ 21
[   19.586386] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   19.869817] usb 2-2: new high speed USB device using ehci_hcd and address 2
[   20.002965] usb 2-2: configuration #1 chosen from 1 choice
[   20.003036] hub 2-2:1.0: USB hub found
[   20.003140] hub 2-2:1.0: 2 ports detected
[   20.106155] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:11:d8:51:6c:0f
[   20.106159] forcedeth 0000:00:0a.0: highdma csum timirq gbit lnktim desc-v3
[   20.106270] pata_amd 0000:00:06.0: version 0.3.10
[   20.106316] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   20.107308] scsi0 : pata_amd
[   20.107898] scsi1 : pata_amd
[   20.108534] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   20.108537] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   20.305735] usb 2-2.1: new high speed USB device using ehci_hcd and address 3
[   20.414919] usb 2-2.1: configuration #1 chosen from 1 choice
[   20.415196] hub 2-2.1:1.0: USB hub found
[   20.415668] hub 2-2.1:1.0: 4 ports detected
[   20.434879] ata1.00: ATA-6: WDC WD800BB-00FRA0, 77.07W77, max UDMA/100
[   20.434883] ata1.00: 156301488 sectors, multi 1: LBA48 
[   20.434898] ata1.01: ATAPI: PIONEER DVD-RW  DVR-106D, 1.08, max UDMA/33
[   20.434907] ata1.00: limited to UDMA/33 due to 40-wire cable
[   20.450781] ata1.00: configured for UDMA/33
[   20.613826] ata1.01: configured for UDMA/33
[   20.717687] usb 2-2.2: new high speed USB device using ehci_hcd and address 4
[   20.779158] ata2.00: ATA-6: WDC WD2000JB-00GVA0, 08.02D08, max UDMA/100
[   20.779162] ata2.00: 390721968 sectors, multi 1: LBA48 
[   20.795089] ata2.00: configured for UDMA/100
[   20.795188] scsi 0:0:0:0: Direct-Access     ATA      WDC WD800BB-00FR 77.0 PQ: 0 ANSI: 5
[   20.801680] scsi 0:0:1:0: CD-ROM            PIONEER  DVD-RW  DVR-106D 1.08 PQ: 0 ANSI: 5
[   20.801987] scsi 1:0:0:0: Direct-Access     ATA      WDC WD2000JB-00G 08.0 PQ: 0 ANSI: 5
[   20.804724] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   20.804732] ACPI: PCI Interrupt 0000:05:0c.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 17
[   20.804829] skge 1.13 addr 0xd4004000 irq 17 chip Yukon-Lite rev 9
[   20.805070] skge eth1: addr 00:11:d8:51:71:c5
[   20.805274] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   20.805280] ACPI: PCI Interrupt 0000:05:08.2[B] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 19
[   20.855408] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[d400d000-d400d7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   20.858174] sata_nv 0000:00:07.0: version 3.5
[   20.858563] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
[   20.858570] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] -> GSI 20 (level, low) -> IRQ 20
[   20.858574] sata_nv 0000:00:07.0: Using ADMA mode
[   20.858701] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   20.862170] scsi2 : sata_nv
[   20.863859] scsi3 : sata_nv
[   20.864049] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 20
[   20.864052] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 20
[   20.865156] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   20.865164] ACPI: PCI Interrupt 0000:05:0b.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 16
[   20.915302] ohci1394: fw-host1: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[d400c000-d400c7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   20.970483] usb 2-2.2: configuration #1 chosen from 1 choice
[   21.169631] usb 2-2.1.2: new low speed USB device using ehci_hcd and address 5
[   21.173528] ata3: SATA link down (SStatus 0 SControl 300)
[   21.287190] usb 2-2.1.2: configuration #1 chosen from 1 choice
[   21.293542] usbcore: registered new interface driver libusual
[   21.301286] Initializing USB Mass Storage driver...
[   21.305227] scsi4 : SCSI emulation for USB Mass Storage devices
[   21.306484] usbcore: registered new interface driver usb-storage
[   21.306489] USB Mass Storage support registered.
[   21.306582] usbcore: registered new interface driver hiddev
[   21.306611] usb-storage: device found at 4
[   21.306613] usb-storage: waiting for device to settle before scanning
[   21.315540] input: Logitech USB RECEIVER as /devices/pci0000:00/0000:00:02.1/usb2/2-2/2-2.1/2-2.1.2/2-2.1.2:1.0/input/input2
[   21.325523] input,hidraw0: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:02.1-2.1.2
[   21.325537] usbcore: registered new interface driver usbhid
[   21.325540] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   21.485460] ata4: SATA link down (SStatus 0 SControl 300)
[   21.485871] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 23
[   21.485874] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 23 (level, low) -> IRQ 23
[   21.485878] sata_nv 0000:00:08.0: Using ADMA mode
[   21.486006] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   21.486110] scsi5 : sata_nv
[   21.486379] scsi6 : sata_nv
[   21.486534] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 23
[   21.486536] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 23
[   21.953368] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   21.961527] ata5.00: ATA-6: ST3160827AS, 3.42, max UDMA/133
[   21.961530] ata5.00: 312581808 sectors, multi 1: LBA48 NCQ (depth 31/32)
[   21.977538] ata5.00: configured for UDMA/133
[   22.133408] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023c01410229a6]
[   22.185395] ieee1394: Host added: ID:BUS[1-00:1023]  GUID[0011d8000000ee74]
[   22.445267] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   22.453437] ata6.00: ATA-6: ST3160827AS, 3.42, max UDMA/133
[   22.453439] ata6.00: 312581808 sectors, multi 1: LBA48 NCQ (depth 31/32)
[   22.469418] ata6.00: configured for UDMA/133
[   22.469514] scsi 5:0:0:0: Direct-Access     ATA      ST3160827AS      3.42 PQ: 0 ANSI: 5
[   22.469520] ata5: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
[   22.469915] scsi 6:0:0:0: Direct-Access     ATA      ST3160827AS      3.42 PQ: 0 ANSI: 5
[   22.469919] ata6: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
[   22.481404] Driver 'sd' needs updating - please use bus_type methods
[   22.481480] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   22.481490] sd 0:0:0:0: [sda] Write Protect is off
[   22.481493] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.481505] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.481539] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   22.481546] sd 0:0:0:0: [sda] Write Protect is off
[   22.481548] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.481558] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.481561]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   22.500743]  sda1
[   22.500801] sd 0:0:0:0: [sda] Attached SCSI disk
[   22.500984] sd 1:0:0:0: [sdb] 390721968 512-byte hardware sectors (200050 MB)
[   22.500994] sd 1:0:0:0: [sdb] Write Protect is off
[   22.500996] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   22.501009] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.501042] sd 1:0:0:0: [sdb] 390721968 512-byte hardware sectors (200050 MB)
[   22.501049] sd 1:0:0:0: [sdb] Write Protect is off
[   22.501051] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   22.501063] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.501065]  sdb:sr0: scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray
[   22.512941] Uniform CD-ROM driver Revision: 3.20
[   22.512985] sr 0:0:1:0: Attached scsi CD-ROM sr0
[   22.524002] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   22.524005] ata2.00: BMDMA stat 0x64
[   22.524010] ata2.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   22.524011]          res 51/84:00:07:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[   22.524014] ata2.00: status: { DRDY ERR }
[   22.524016] ata2.00: error: { ICRC ABRT }
[   22.524031] ata2: soft resetting link
[   22.702650] ata2.00: configured for UDMA/100
[   22.702663] ata2: EH complete
[   22.706803] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   22.706806] ata2.00: BMDMA stat 0x64
[   22.706811] ata2.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   22.706812]          res 51/84:00:07:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[   22.706814] ata2.00: status: { DRDY ERR }
[   22.706816] ata2.00: error: { ICRC ABRT }
[   22.706830] ata2: soft resetting link
[   22.886616] ata2.00: configured for UDMA/100
[   22.886629] ata2: EH complete
[   22.889569] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   22.889573] ata2.00: BMDMA stat 0x64
[   22.889578] ata2.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   22.889579]          res 51/84:00:07:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[   22.889581] ata2.00: status: { DRDY ERR }
[   22.889583] ata2.00: error: { ICRC ABRT }
[   22.889597] ata2: soft resetting link
[   23.070575] ata2.00: configured for UDMA/100
[   23.070590] ata2: EH complete
[   23.080643] ata2.00: limiting speed to UDMA/66:PIO4
[   23.080646] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   23.080649] ata2.00: BMDMA stat 0x64
[   23.080654] ata2.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   23.080655]          res 51/84:00:07:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[   23.080657] ata2.00: status: { DRDY ERR }
[   23.080659] ata2.00: error: { ICRC ABRT }
[   23.080670] ata2: soft resetting link
[   23.258512] ata2.00: configured for UDMA/66
[   23.258526] ata2: EH complete
[   23.263442] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   23.263445] ata2.00: BMDMA stat 0x64
[   23.263450] ata2.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   23.263451]          res 51/84:00:07:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[   23.263453] ata2.00: status: { DRDY ERR }
[   23.263455] ata2.00: error: { ICRC ABRT }
[   23.263466] ata2: soft resetting link
[   23.442481] ata2.00: configured for UDMA/66
[   23.442494] ata2: EH complete
[   23.446201] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   23.446203] ata2.00: BMDMA stat 0x64
[   23.446208] ata2.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   23.446209]          res 51/84:00:07:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[   23.446212] ata2.00: status: { DRDY ERR }
[   23.446213] ata2.00: error: { ICRC ABRT }
[   23.446224] ata2: soft resetting link
[   23.626436] ata2.00: configured for UDMA/66
[   23.626451] sd 1:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   23.626454] sd 1:0:0:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[   23.626458] Descriptor sense data with sense descriptors (in hex):
[   23.626459]         72 0b 47 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   23.626463]         00 00 00 07 
[   23.626465] sd 1:0:0:0: [sdb] Add. Sense: Scsi parity error
[   23.626471] end_request: I/O error, dev sdb, sector 0
[   23.626474] Buffer I/O error on device sdb, logical block 0
[   23.626490] ata2: EH complete
[   23.637243] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   23.637245] ata2.00: BMDMA stat 0x64
[   23.637250] ata2.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   23.637251]          res 51/84:00:07:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[   23.637253] ata2.00: status: { DRDY ERR }
[   23.637255] ata2.00: error: { ICRC ABRT }
[   23.637266] ata2: soft resetting link
[   23.818416] ata2.00: configured for UDMA/66
[   23.818431] ata2: EH complete
[   23.828313] ata2.00: limiting speed to UDMA/33:PIO4
[   23.828316] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   23.828319] ata2.00: BMDMA stat 0x64
[   23.828323] ata2.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   23.828325]          res 51/84:00:07:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[   23.828327] ata2.00: status: { DRDY ERR }
[   23.828329] ata2.00: error: { ICRC ABRT }
[   23.828341] ata2: soft resetting link
[   24.006363] ata2.00: configured for UDMA/33
[   24.006378] ata2: EH complete
[   24.009526] ldm_validate_partition_table(): Disk read failed.
[   24.009532] Dev sdb: unable to read RDB block 0
[   24.009603] sd 1:0:0:0: [sdb] 390721968 512-byte hardware sectors (200050 MB)
[   24.009746] sd 1:0:0:0: [sdb] Write Protect is off
[   24.009748] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   24.009763] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.009777] sd 1:0:0:0: [sdb] 390721968 512-byte hardware sectors (200050 MB)
[   24.009784] sd 1:0:0:0: [sdb] Write Protect is off
[   24.009786] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   24.009797] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.009802]  unable to read partition table
[   24.009848] sd 1:0:0:0: [sdb] Attached SCSI disk
[   24.010187] sd 5:0:0:0: [sdc] 312581808 512-byte hardware sectors (160042 MB)
[   24.010196] sd 5:0:0:0: [sdc] Write Protect is off
[   24.010198] sd 5:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   24.010209] sd 5:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.010241] sd 5:0:0:0: [sdc] 312581808 512-byte hardware sectors (160042 MB)
[   24.010249] sd 5:0:0:0: [sdc] Write Protect is off
[   24.010251] sd 5:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   24.010263] sd 5:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.010266]  sdc: sdc1 sdc2 sdc3 sdc4
[   24.036573] sd 5:0:0:0: [sdc] Attached SCSI disk
[   24.037197] sd 6:0:0:0: [sdd] 312581808 512-byte hardware sectors (160042 MB)
[   24.037206] sd 6:0:0:0: [sdd] Write Protect is off
[   24.037208] sd 6:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[   24.037219] sd 6:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.037245] sd 6:0:0:0: [sdd] 312581808 512-byte hardware sectors (160042 MB)
[   24.037252] sd 6:0:0:0: [sdd] Write Protect is off
[   24.037254] sd 6:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[   24.037265] sd 6:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.037269]  sdd: sdd1
[   24.046460] sd 6:0:0:0: [sdd] Attached SCSI disk
[   24.061322] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   24.061339] sr 0:0:1:0: Attached scsi generic sg1 type 5
[   24.061353] sd 1:0:0:0: Attached scsi generic sg2 type 0
[   24.061367] sd 5:0:0:0: Attached scsi generic sg3 type 0
[   24.061382] sd 6:0:0:0: Attached scsi generic sg4 type 0
[   24.458354] Attempting manual resume
[   24.458357] swsusp: Resume From Partition 8:36
[   24.458359] PM: Checking swsusp image.
[   24.458532] PM: Resume from disk failed.
[   24.484284] kjournald starting.  Commit interval 5 seconds
[   24.484298] EXT3-fs: mounted filesystem with ordered data mode.
[   26.310153] usb-storage: device scan complete
[   26.314007] scsi 4:0:0:0: Direct-Access     SMSC     223 U HS-CF      3.60 PQ: 0 ANSI: 0
[   26.317877] scsi 4:0:0:1: Direct-Access     SMSC     223 U HS-MS      3.60 PQ: 0 ANSI: 0
[   26.321625] scsi 4:0:0:2: Direct-Access     SMSC     223 U HS-SM      3.60 PQ: 0 ANSI: 0
[   26.325501] scsi 4:0:0:3: Direct-Access     SMSC     223 U HS-SD/MMC  3.60 PQ: 0 ANSI: 0
[   26.330402] sd 4:0:0:0: [sde] Attached SCSI removable disk
[   26.330426] sd 4:0:0:0: Attached scsi generic sg5 type 0
[   26.334514] sd 4:0:0:1: [sdf] Attached SCSI removable disk
[   26.334535] sd 4:0:0:1: Attached scsi generic sg6 type 0
[   26.339389] sd 4:0:0:2: [sdg] Attached SCSI removable disk
[   26.339407] sd 4:0:0:2: Attached scsi generic sg7 type 0
[   26.389388] sd 4:0:0:3: [sdh] Attached SCSI removable disk
[   26.389410] sd 4:0:0:3: Attached scsi generic sg8 type 0
[   30.679680] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[   30.679703] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4c40
[   30.731593] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   30.771598] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   30.995618] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   31.043631] input: Power Button (FF) as /devices/virtual/input/input4
[   31.055485] ACPI: Power Button (FF) [PWRF]
[   31.055574] input: Power Button (CM) as /devices/virtual/input/input5
[   31.071466] ACPI: Power Button (CM) [PWRB]
[   31.479287] gameport: EMU10K1 is pci0000:05:08.1/gameport0, io 0xa400, speed 1206kHz
[   32.571431] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   32.571439] ACPI: PCI Interrupt 0000:05:08.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
[   32.573718] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/emu10k1/../../alsa-kernel/pci/emu10k1/emufx.c:1544: Installing spdif_bug patch: Audigy 2 ZS [2001]
[   33.323080] nvidia: module license 'NVIDIA' taints kernel.
[   33.899086] usbcore: registered new interface driver lmpcm_usb
[   33.899091] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/misc/lmpcm_usb.c: v0.5.5:USB Logitech MediaPlay Cordless Mouse driver
[   34.435100] parport_pc 00:08: reported by Plug and Play ACPI
[   34.435149] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   34.579848] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
[   34.579856] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   34.579994] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
[   36.550862] lp0: using parport0 (interrupt-driven).
[   36.643636] Adding 3148732k swap on /dev/sdc4.  Priority:-1 extents:1 across:3148732k
[   37.183367] EXT3 FS on sdc2, internal journal
[   37.957523] kjournald starting.  Commit interval 5 seconds
[   37.957731] EXT3 FS on sdc3, internal journal
[   37.957735] EXT3-fs: mounted filesystem with ordered data mode.
[   38.852123] ip_tables: (C) 2000-2006 Netfilter Core Team
[   39.211749] No dock devices found.
[   39.508963] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3500+ processors (1 cpu cores) (version 2.20.00)
[   39.509001] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x6
[   39.509003] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x8
[   39.509005] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xa
[   39.509006] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[   40.585682] Marking TSC unstable due to cpufreq changes
[   40.589483] Time: acpi_pm clocksource has been installed.
[   41.545791] eth0: no link during initialization.
[   41.604692] skge eth1: enabling interface
[   42.017219] Clocksource tsc unstable (delta = -79269343 ns)
[   42.890787] skge eth1: Link is up at 100 Mbps, full duplex, flow control both
[   44.408867] NET: Registered protocol family 17
[   46.971427] NET: Registered protocol family 10
[   46.971874] lo: Disabled Privacy Extensions
[   46.972454] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   52.400439] eth1: no IPv6 routers present
[   72.470644] UDF-fs: No VRS found
[   72.482514] ISO 9660 Extensions: Microsoft Joliet Level 3
[   72.492902] ISO 9660 Extensions: RRIP_1991A

```

```

/dev/scd0  /dev/sdc2  /dev/sdf         /dev/sg1  /dev/sg7       /dev/stdin
/dev/sda   /dev/sdc3  /dev/sdg         /dev/sg2  /dev/sg8       /dev/stdout
/dev/sda1  /dev/sdc4  /dev/sdh         /dev/sg3  /dev/snapshot
/dev/sdb   /dev/sdd   /dev/sequencer   /dev/sg4  /dev/sndstat
/dev/sdc   /dev/sdd1  /dev/sequencer2  /dev/sg5  /dev/sr0
/dev/sdc1  /dev/sde   /dev/sg0         /dev/sg6  /dev/stderr


```

---

### Post by hermes0710 on 2008-04-25
> [   23.626465] sd 1:0:0:0: [sdb] Add. Sense: Scsi parity error
[   23.626471] end_request: I/O error, dev sdb, sector 0
[   23.626474] Buffer I/O error on device sdb, logical block 0

> [   24.009526] ldm_validate_partition_table(): Disk read failed.
[   24.009532] Dev sdb: unable to read RDB block 0

These are not good... I'll check them out and i will get back to you...

---

### Post by hermes0710 on 2008-04-25
Check this out:

[http://www.aoaforums.com/forum/os-software-firmware-and-bios/44695-a-problem-in-fedora-8-boot.html]("http://www.aoaforums.com/forum/os-software-firmware-and-bios/44695-a-problem-in-fedora-8-boot.html")

---

### Post by BluntBox on 2008-04-26
Decided to back up all my data and nuke the drive. Removed the partitions from it so it was just a blank disk and booted the live CD to see if it would recognise it. GParted knows the drive is there, but gives me this warning about it:

(liveCD seems to be starting my hard disks at sde, perhaps the 4 usb removable drives on my monitor are stealing the first 4 or something)
```

The device /dev/sdf1 doesn't exist.

ntfsresize v2.0.0 (libntfs 10:0:0)
ERROR(2): Failed to check '/dev/sdf1' mount state: no such file or directory.
Probably /etc/mtab is missing. It's too risky to continue. You might want to try another Linux disto.

Unable to read the contents of this file system!
Because of this some operations may be unavailable.

```

So I guess Hardy just hates this hard drive, despite it having no errors or bad sectors according to Windows.

Edit: Just booted 7.10 liveCD and the drive works perfectly. Really quite frustrating.

---

