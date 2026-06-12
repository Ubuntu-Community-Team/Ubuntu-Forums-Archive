---
title: "Ubuntu 12.04 Stuck in Unity 2D with OpenGL and GLX Errors"
date: 2015-01-29
forum: General Help
---

### Post by lelouch2 on 2015-01-29
For the past few months, my Ubuntu 12.04 LTS desktop computer has been stuck in Unity 2D. Also, several programs I regularly use don't work due to errors that seem related to OpenGL and GLX. I have no idea what else to try at this point. This originally happened when some people on IRC had me mess with my graphics drivers to try and get Unity to start up again, but I don't know exactly what I was doing before this issue started up.

I'm not really sure how much of this information is relevant, so I'm just including all of it. Thanks in advance for anyone who looks into this!

Here are the errors from various program:

```
STEAM

openGL GLX extension not supported by display

PYTHON PYGAME

>>> pygame.display.set_mode((640, 480), pygame.HWSURFACE|pygame.OPENGL|pygame.DOUBLEBUF)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
pygame.error: Couldn't find matching GLX visual

MEDNAFEN

Couldn't find matching GLX visual

NETFLIX-DESKTOP

Compositing is not available, please enable compositing support and relaunch Netflix Desktop.

ADDITIONAL DRIVERS

No proprietary drivers are in use on this system.

> Realtek Wireless Lan Driver
   Tested by the Ubuntu developers
   License: Free

FCEUX

Plays for a few seconds, then Segmentation fault
(This didn't happen in Unity 3D)

VIRTUAL BOX

Failed to open a session for the virtual machine Windowcat.
This VM was configured to use 3D acceleration. However, the 3D support of the host is not working properly and the VM cannot be started. To fix this problem, either fix the host 3D support (update the host graphics driver?) or disable 3D acceleration in the VM settings (VERR_NOT_AVAILABLE).

DROPBOX

When computer starts up, Dropbox icon is in the top-left of the screen, on top of the top panel.
Running 'killall dropbox' and then 'dropbox start' puts it with the other notification icons.
```

Here's what the tty says when I log in, in case that's relevant:
```
Your current hardware enablement stack (HWE) is no longer supported since 2014-08-07. Security updates for critical parts (kernel and graphics stack) of your system are no longer available.

For more information, please see:
http://wiki.ubuntu.com/1204_HWE_EOL

There is a graphics stack installed on this system. An upgrade to a supported (or no longer supported) configuration will become available on 2014-07-16 and can be invoked by running 'update-manager' in the Dash.
```

I haven't been keeping logs of what I've been doing for very long, but here's what I tried on January 6th:
```
Uninstalled mesa-utils
Reinstalled mesa-utils (only effect is to make Nautilus folders stop stacking properly in launcher)
Installed Bumblebee https://wiki.ubuntu.com/Bumblebee
Rebooted - Unity wouldn't load after logging in.
Uninstalled Bumblebee.
Rebooted - Unity loads again.

```

(Nautilus folders eventually started stacking again, but I don't know why)

And here's what I tried today:
```
Install netflix-desktop ("compositing is not available")
Download: https://01.org/linuxgraphics/sites/default/files/downloads/u12.04-downgrade.tar
Extract to Downloads/Intel Downgrade
Mark the file as executable
sudo ./downgrade.sh
sudo apt-get autoremove

reboot - nothing happens (netflix-desktop has the same error)

http://ubuntuhandbook.org/index.php/2013/08/install-update-intel-graphics-driver-from-official-repository/

sudo sh -c 'echo "deb https://download.01.org/gfx/ubuntu/12.04/main Ubuntu 12.04" >> /etc/apt/sources.list.d/intel-graphics.list' (nothing happens)

sudo update-pciids
  > Downloaded daily snapshot dated 2015-01-28 03:15:02

E: Unable to locate package mesa-libgl

http://ubuntuforums.org/showthread.php?t=345177

sudo apt-get update (no problems)
sudo apt-get install build-essential (already the newest version)
sudo apt-get install freeglut3-dev (unable to fetch some archives)
sudo apt-get install freeglut3-dev --fix-missing (success!)
Reboot - still Unity 2D, no apparent changes
```

lspci -v
```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 7788
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 7788
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at f7800000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 7788
    Flags: bus master, fast devsel, latency 0, IRQ 41
    Memory at f7c09000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: mei
    Kernel modules: mei

00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05) (prog-if 20 [EHCI])
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 7788
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f7c07000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device d788
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at f7c00000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f00fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05) (prog-if 20 [EHCI])
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 7788
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f7c06000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1f.0 ISA bridge: Intel Corporation H61 Express Chipset Family LPC Controller (rev 05)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 7788
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich

00:1f.2 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller (rev 05) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 7788
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at f110 [size=8]
    I/O ports at f100 [size=4]
    I/O ports at f0f0 [size=8]
    I/O ports at f0e0 [size=4]
    I/O ports at f0d0 [size=16]
    I/O ports at f0c0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 7788
    Flags: medium devsel, IRQ 10
    Memory at f7c05000 (64-bit, non-prefetchable) [size=256]
    I/O ports at f040 [size=32]
    Kernel modules: i2c-i801

00:1f.5 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller (rev 05) (prog-if 85 [Master SecO PriO])
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 7788
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at f0b0 [size=8]
    I/O ports at f0a0 [size=4]
    I/O ports at f090 [size=8]
    I/O ports at f080 [size=4]
    I/O ports at f070 [size=16]
    I/O ports at f060 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 7788
    Flags: bus master, fast devsel, latency 0, IRQ 40
    I/O ports at e000 [size=256]
    Memory at f0004000 (64-bit, prefetchable) [size=4K]
    Memory at f0000000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

```

dmesg
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.8.0-44-generic (buildd@brownie) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #66~precise1-Ubuntu SMP Tue Jul 15 04:04:23 UTC 2014 (Ubuntu 3.8.0-44.66~precise1-generic 3.8.13.25)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009ebff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009ec00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000020200000-0x000000003fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000040000000-0x00000000401fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000040200000-0x00000000d9b22fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000d9b23000-0x00000000da0c5fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000da0c6000-0x00000000da1dafff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000da1db000-0x00000000da935fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000da936000-0x00000000da936fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000da937000-0x00000000da979fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000da97a000-0x00000000dad90fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000dad91000-0x00000000daff1fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000daff2000-0x00000000daffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000db800000-0x00000000df9fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000011f5fffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: MSI MS-7788/H61M-P31 (G3) (MS-7788), BIOS V2.5 07/14/2012
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x11f600 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 100000000 mask FE0000000 write-back
[    0.000000]   2 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   3 base 0DC000000 mask FFC000000 uncachable
[    0.000000]   4 base 0DB800000 mask FFF800000 uncachable
[    0.000000]   5 base 11F800000 mask FFF800000 uncachable
[    0.000000]   6 base 11F600000 mask FFFE00000 uncachable
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 4GB, type WB
[    0.000000] reg 1, base: 4GB, range: 512MB, type WB
[    0.000000] reg 2, base: 3584MB, range: 512MB, type UC
[    0.000000] reg 3, base: 3520MB, range: 64MB, type UC
[    0.000000] reg 4, base: 3512MB, range: 8MB, type UC
[    0.000000] reg 5, base: 4600MB, range: 8MB, type UC
[    0.000000] reg 6, base: 4598MB, range: 2MB, type UC
[    0.000000] total RAM covered: 4014M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 128M     num_reg: 8      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 512MB, type WB
[    0.000000] reg 3, base: 3512MB, range: 8MB, type UC
[    0.000000] reg 4, base: 3520MB, range: 64MB, type UC
[    0.000000] reg 5, base: 4GB, range: 512MB, type WB
[    0.000000] reg 6, base: 4598MB, range: 2MB, type UC
[    0.000000] reg 7, base: 4600MB, range: 8MB, type UC
[    0.000000] e820: update [mem 0xdb800000-0xffffffff] usable ==> reserved
[    0.000000] found SMP MP-table at [mem 0x000fd720-0x000fd72f] mapped at [c00fd720]
[    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
[    0.000000] Base memory trampoline at [c009a000] 9a000 size 16384
[    0.000000] reserving inaccessible SNB gfx pages
[    0.000000] init_memory_mapping: [mem 0x00000000-0x37bfdfff]
[    0.000000]  [mem 0x00000000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x379fffff] page 2M
[    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
[    0.000000] kernel direct mapping tables up to 0x37bfdfff @ [mem 0x01ffa000-0x01ffffff]
[    0.000000] RAMDISK: [mem 0x36096000-0x37042fff]
[    0.000000] ACPI: RSDP 000f0490 00024 (v02 ALASKA)
[    0.000000] ACPI: XSDT da1cc070 00064 (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FACP da1d5d78 0010C (v05 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT da1cc170 09C03 (v02 ALASKA    A M I 00000021 INTL 20051117)
[    0.000000] ACPI: FACS da1d9080 00040
[    0.000000] ACPI: APIC da1d5e88 00062 (v03 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FPDT da1d5ef0 00044 (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: MCFG da1d5f38 0003C (v01 ALASKA    A M I 01072009 MSFT 00000097)
[    0.000000] ACPI: HPET da1d5f78 00038 (v01 ALASKA    A M I 01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT da1d5fb0 004E9 (v01 IdeRef IdeTable 00001000 INTL 20091112)
[    0.000000] ACPI: SSDT da1d64a0 00926 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT da1d6dc8 00A92 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 3706MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
[    0.000000]   HighMem  [mem 0x37bfe000-0x1f5fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009dfff]
[    0.000000]   node   0: [mem 0x00100000-0x1fffffff]
[    0.000000]   node   0: [mem 0x20200000-0x3fffffff]
[    0.000000]   node   0: [mem 0x40200000-0xd9b22fff]
[    0.000000]   node   0: [mem 0xda936000-0xda936fff]
[    0.000000]   node   0: [mem 0xda97a000-0xdad90fff]
[    0.000000]   node   0: [mem 0xdaff2000-0xdaffffff]
[    0.000000]   node   0: [mem 0x00000000-0x1f5fffff]
[    0.000000] On node 0 totalpages: 1020119
[    0.000000] free_area_init_node: node 0, pgdat c1934280, node_mem_map f3ca6200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3950 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 221990 pages, LIFO batch:31
[    0.000000]   HighMem zone: 7413 pages used for memmap
[    0.000000]   HighMem zone: 784982 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
[    0.000000] e820: [mem 0xdfa00000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7bce000 s34880 r0 d22464 u57344
[    0.000000] pcpu-alloc: s34880 r0 d22464 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1010922
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-44-generic root=UUID=23f334cb-51f2-4274-b680-8a5d612f366e ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] Initializing CPU#0
[    0.000000] xsave: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] allocated 9416576 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0011f600)
[    0.000000] Memory: 4005636k/4708352k available (6375k kernel code, 74840k reserved, 3097k data, 800k init, 3169580k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff14000 - 0xfffff000   ( 940 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1941000 - 0xc1a09000   ( 800 kB)
[    0.000000]       .data : 0xc1639fad - 0xc1940580   (3097 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1639fad   (6375 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=2.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f3808000 soft=f380a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 2899.935 MHz processor
[    0.000001] Calibrating delay loop (skipped), value calculated using timer frequency.. 5799.87 BogoMIPS (lpj=11599740)
[    0.000003] pid_max: default: 32768 minimum: 301
[    0.000021] Security Framework initialized
[    0.000028] AppArmor: AppArmor initialized
[    0.000029] Yama: becoming mindful.
[    0.000061] Mount-cache hash table entries: 512
[    0.000195] Initializing cgroup subsys cpuacct
[    0.000197] Initializing cgroup subsys memory
[    0.000202] Initializing cgroup subsys devices
[    0.000203] Initializing cgroup subsys freezer
[    0.000204] Initializing cgroup subsys blkio
[    0.000205] Initializing cgroup subsys perf_event
[    0.000207] Initializing cgroup subsys hugetlb
[    0.000228] CPU: Physical Processor ID: 0
[    0.000229] CPU: Processor Core ID: 0
[    0.000232] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.000232] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.000235] mce: CPU supports 7 MCE banks
[    0.000244] CPU0: Thermal monitoring enabled (TM1)
[    0.000249] process: using mwait in idle threads
[    0.000253] Last level iTLB entries: 4KB 512, 2MB 0, 4MB 0
[    0.000253] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32
[    0.000253] tlb_flushall_shift: 5
[    0.000517] Freeing SMP alternatives: 24k freed
[    0.002171] ACPI: Core revision 20121018
[    0.016637] ftrace: allocating 28914 entries in 57 pages
[    0.028127] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.028520] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.068191] smpboot: CPU0: Intel(R) Pentium(R) CPU G850 @ 2.90GHz (fam: 06, model: 2a, stepping: 07)
[    0.068198] TSC deadline timer enabled
[    0.068201] Performance Events: PEBS fmt1+, 16-deep LBR, SandyBridge events, Intel PMU driver.
[    0.068207] perf_event_intel: PEBS disabled due to CPU errata, please upgrade microcode
[    0.068208] ... version:                3
[    0.068209] ... bit width:              48
[    0.068210] ... generic registers:      8
[    0.068211] ... value mask:             0000ffffffffffff
[    0.068212] ... max period:             000000007fffffff
[    0.068213] ... fixed-purpose events:   3
[    0.068213] ... event mask:             00000007000000ff
[    0.069022] CPU 1 irqstacks, hard=f38fe000 soft=f3900000
[    0.069024] smpboot: Booting Node   0, Processors  #1 OK
[    0.079233] Initializing CPU#1
[    0.082168] Brought up 2 CPUs
[    0.082171] smpboot: Total of 2 processors activated (11599.74 BogoMIPS)
[    0.082239] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.083682] devtmpfs: initialized
[    0.083831] EVM: security.selinux
[    0.083832] EVM: security.SMACK64
[    0.083833] EVM: security.capability
[    0.083901] PM: Registering ACPI NVS region [mem 0xda0c6000-0xda1dafff] (1134592 bytes)
[    0.083921] PM: Registering ACPI NVS region [mem 0xda937000-0xda979fff] (274432 bytes)
[    0.084494] regulator-dummy: no parameters
[    0.084532] NET: Registered protocol family 16
[    0.084628] EISA bus registered
[    0.084694] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.084696] ACPI: bus type pci registered
[    0.084733] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.084736] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.084737] PCI: Using MMCONFIG for extended config space
[    0.084738] PCI: Using configuration type 1 for base access
[    0.085428] bio: create slab <bio-0> at 0
[    0.085495] ACPI: Added _OSI(Module Device)
[    0.085496] ACPI: Added _OSI(Processor Device)
[    0.085497] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.085499] ACPI: Added _OSI(Processor Aggregator Device)
[    0.086951] ACPI: EC: Look up EC in DSDT
[    0.088569] ACPI: Executed 1 blocks of module-level executable AML code
[    0.091319] ACPI: SSDT da077018 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.091690] ACPI: Dynamic OEM Table Load:
[    0.091692] ACPI: SSDT   (null) 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.091906] ACPI: SSDT da078a98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.092305] ACPI: Dynamic OEM Table Load:
[    0.092306] ACPI: SSDT   (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.092397] ACPI: SSDT da076d98 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.092763] ACPI: Dynamic OEM Table Load:
[    0.092765] ACPI: SSDT   (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.093026] ACPI: Interpreter enabled
[    0.093030] ACPI: (supports S0 S3 S4 S5)
[    0.093045] ACPI: Using IOAPIC for interrupt routing
[    0.097902] ACPI: Power Resource [FN00] (off)
[    0.097960] ACPI: Power Resource [FN01] (off)
[    0.098015] ACPI: Power Resource [FN02] (off)
[    0.098071] ACPI: Power Resource [FN03] (off)
[    0.098126] ACPI: Power Resource [FN04] (off)
[    0.098476] ACPI: No dock devices found.
[    0.098479] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.098682] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.098684] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.099282] PCI host bridge to bus 0000:00
[    0.099285] pci_bus 0000:00: root bus resource [bus 00-3e]
[    0.099286] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.099288] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.099290] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.099291] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.099293] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.099294] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.099296] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.099297] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    0.099298] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    0.099300] pci_bus 0000:00: root bus resource [mem 0xdfa00000-0xfeafffff]
[    0.099307] pci 0000:00:00.0: [8086:0100] type 00 class 0x060000
[    0.099339] pci 0000:00:02.0: [8086:0102] type 00 class 0x030000
[    0.099349] pci 0000:00:02.0: reg 10: [mem 0xf7800000-0xf7bfffff 64bit]
[    0.099355] pci 0000:00:02.0: reg 18: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.099359] pci 0000:00:02.0: reg 20: [io  0xf000-0xf03f]
[    0.099408] pci 0000:00:16.0: [8086:1c3a] type 00 class 0x078000
[    0.099430] pci 0000:00:16.0: reg 10: [mem 0xf7c09000-0xf7c0900f 64bit]
[    0.099505] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.099537] pci 0000:00:1a.0: [8086:1c2d] type 00 class 0x0c0320
[    0.099557] pci 0000:00:1a.0: reg 10: [mem 0xf7c07000-0xf7c073ff]
[    0.099646] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.099670] pci 0000:00:1b.0: [8086:1c20] type 00 class 0x040300
[    0.099684] pci 0000:00:1b.0: reg 10: [mem 0xf7c00000-0xf7c03fff 64bit]
[    0.099749] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.099775] pci 0000:00:1c.0: [8086:1c10] type 01 class 0x060400
[    0.099903] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.099938] pci 0000:00:1c.4: [8086:1c18] type 01 class 0x060400
[    0.100014] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.100043] pci 0000:00:1d.0: [8086:1c26] type 00 class 0x0c0320
[    0.100063] pci 0000:00:1d.0: reg 10: [mem 0xf7c06000-0xf7c063ff]
[    0.100151] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.100174] pci 0000:00:1f.0: [8086:1c5c] type 00 class 0x060100
[    0.100291] pci 0000:00:1f.2: [8086:1c00] type 00 class 0x01018f
[    0.100305] pci 0000:00:1f.2: reg 10: [io  0xf110-0xf117]
[    0.100312] pci 0000:00:1f.2: reg 14: [io  0xf100-0xf103]
[    0.100319] pci 0000:00:1f.2: reg 18: [io  0xf0f0-0xf0f7]
[    0.100327] pci 0000:00:1f.2: reg 1c: [io  0xf0e0-0xf0e3]
[    0.100334] pci 0000:00:1f.2: reg 20: [io  0xf0d0-0xf0df]
[    0.100341] pci 0000:00:1f.2: reg 24: [io  0xf0c0-0xf0cf]
[    0.100383] pci 0000:00:1f.3: [8086:1c22] type 00 class 0x0c0500
[    0.100397] pci 0000:00:1f.3: reg 10: [mem 0xf7c05000-0xf7c050ff 64bit]
[    0.100417] pci 0000:00:1f.3: reg 20: [io  0xf040-0xf05f]
[    0.100448] pci 0000:00:1f.5: [8086:1c08] type 00 class 0x010185
[    0.100462] pci 0000:00:1f.5: reg 10: [io  0xf0b0-0xf0b7]
[    0.100469] pci 0000:00:1f.5: reg 14: [io  0xf0a0-0xf0a3]
[    0.100476] pci 0000:00:1f.5: reg 18: [io  0xf090-0xf097]
[    0.100483] pci 0000:00:1f.5: reg 1c: [io  0xf080-0xf083]
[    0.100490] pci 0000:00:1f.5: reg 20: [io  0xf070-0xf07f]
[    0.100497] pci 0000:00:1f.5: reg 24: [io  0xf060-0xf06f]
[    0.100605] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.100682] pci 0000:02:00.0: [10ec:8168] type 00 class 0x020000
[    0.100701] pci 0000:02:00.0: reg 10: [io  0xe000-0xe0ff]
[    0.100734] pci 0000:02:00.0: reg 18: [mem 0xf0004000-0xf0004fff 64bit pref]
[    0.100755] pci 0000:02:00.0: reg 20: [mem 0xf0000000-0xf0003fff 64bit pref]
[    0.100844] pci 0000:02:00.0: supports D1 D2
[    0.100846] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.106175] pci 0000:00:1c.4: PCI bridge to [bus 02]
[    0.106179] pci 0000:00:1c.4:   bridge window [io  0xe000-0xefff]
[    0.106186] pci 0000:00:1c.4:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.106200] pci_bus 0000:00: on NUMA node 0
[    0.106221] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.106255] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.106375]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.106548]  pci0000:00: ACPI _OSC control (0x18) granted
[    0.107130] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.107168] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.107204] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.107240] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.107276] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.107313] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.107351] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.107388] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.107461] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.107463] vgaarb: loaded
[    0.107464] vgaarb: bridge control possible 0000:00:02.0
[    0.107606] SCSI subsystem initialized
[    0.107607] ACPI: bus type scsi registered
[    0.107632] libata version 3.00 loaded.
[    0.107647] ACPI: bus type usb registered
[    0.107659] usbcore: registered new interface driver usbfs
[    0.107666] usbcore: registered new interface driver hub
[    0.107683] usbcore: registered new device driver usb
[    0.107751] PCI: Using ACPI for IRQ routing
[    0.109264] PCI: pci_cache_line_size set to 64 bytes
[    0.109302] e820: reserve RAM buffer [mem 0x0009ec00-0x0009ffff]
[    0.109304] e820: reserve RAM buffer [mem 0xd9b23000-0xdbffffff]
[    0.109306] e820: reserve RAM buffer [mem 0xda937000-0xdbffffff]
[    0.109308] e820: reserve RAM buffer [mem 0xdad91000-0xdbffffff]
[    0.109309] e820: reserve RAM buffer [mem 0xdb000000-0xdbffffff]
[    0.109310] e820: reserve RAM buffer [mem 0x11f600000-0x11fffffff]
[    0.109373] NetLabel: Initializing
[    0.109374] NetLabel:  domain hash size = 128
[    0.109375] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.109382] NetLabel:  unlabeled traffic allowed by default
[    0.109452] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.109457] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.111468] Switching to clocksource hpet
[    0.116304] AppArmor: AppArmor Filesystem Enabled
[    0.116325] pnp: PnP ACPI init
[    0.116335] ACPI: bus type pnp registered
[    0.116401] system 00:00: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.116404] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.116415] pnp 00:01: [dma 4]
[    0.116426] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.116442] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.116513] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.116545] system 00:04: [io  0x0680-0x069f] has been reserved
[    0.116546] system 00:04: [io  0x1000-0x100f] has been reserved
[    0.116548] system 00:04: [io  0xffff] has been reserved
[    0.116550] system 00:04: [io  0xffff] has been reserved
[    0.116551] system 00:04: [io  0x0400-0x0453] has been reserved
[    0.116553] system 00:04: [io  0x0458-0x047f] has been reserved
[    0.116555] system 00:04: [io  0x0500-0x057f] has been reserved
[    0.116556] system 00:04: [io  0x164e-0x164f] has been reserved
[    0.116558] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.116582] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.116616] system 00:06: [io  0x0454-0x0457] has been reserved
[    0.116618] system 00:06: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.116696] pnp 00:07: unknown resource type 4 in _CRS
[    0.116698] pnp 00:07: can't evaluate _CRS: 1
[    0.116713] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.116907] pnp 00:08: [dma 0 disabled]
[    0.116944] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.116980] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.116982] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.117002] pnp 00:0a: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.117226] pnp 00:0b: [dma 3]
[    0.117313] pnp 00:0b: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.117528] system 00:0c: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.117531] system 00:0c: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.117533] system 00:0c: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.117535] system 00:0c: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.117536] system 00:0c: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.117538] system 00:0c: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.117540] system 00:0c: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.117541] system 00:0c: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.117543] system 00:0c: [mem 0xff000000-0xffffffff] has been reserved
[    0.117545] system 00:0c: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.117547] system 00:0c: [mem 0xdfa00000-0xdfa00fff] has been reserved
[    0.117549] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.117686] system 00:0d: [mem 0x20000000-0x201fffff] has been reserved
[    0.117688] system 00:0d: [mem 0x40000000-0x401fffff] has been reserved
[    0.117690] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.117707] pnp: PnP ACPI: found 14 devices
[    0.117708] ACPI: ACPI bus type pnp unregistered
[    0.117710] PnPBIOS: Disabled by ACPI PNP
[    0.153464] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.153482] pci 0000:00:1c.4: PCI bridge to [bus 02]
[    0.153485] pci 0000:00:1c.4:   bridge window [io  0xe000-0xefff]
[    0.153492] pci 0000:00:1c.4:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.153518] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.153520] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.153521] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.153523] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.153524] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.153526] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.153527] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.153529] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.153530] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.153532] pci_bus 0000:00: resource 13 [mem 0xdfa00000-0xfeafffff]
[    0.153533] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.153535] pci_bus 0000:02: resource 2 [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.153559] NET: Registered protocol family 2
[    0.153656] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.153669] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.153679] TCP: Hash tables configured (established 8192 bind 8192)
[    0.153688] TCP: reno registered
[    0.153690] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.153694] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.153725] NET: Registered protocol family 1
[    0.153972] pci 0000:00:02.0: BIOS left Intel GPU interrupts enabled; disabling
[    0.153987] pci 0000:00:02.0: Boot video device
[    0.154043] PCI: CLS 64 bytes, default 64
[    0.154071] Trying to unpack rootfs image as initramfs...
[    0.391980] Freeing initrd memory: 16052k freed
[    0.393972] Initialise module verification
[    0.394002] audit: initializing netlink socket (disabled)
[    0.394010] type=2000 audit(1422526210.388:1): initialized
[    0.413900] bounce pool size: 64 pages
[    0.413907] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.415016] VFS: Disk quotas dquot_6.5.2
[    0.415047] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.415399] fuse init (API version 7.20)
[    0.415462] msgmni has been set to 1664
[    0.415714] Key type asymmetric registered
[    0.415715] Asymmetric key parser 'x509' registered
[    0.415739] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.415756] io scheduler noop registered
[    0.415757] io scheduler deadline registered (default)
[    0.415762] io scheduler cfq registered
[    0.415930] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.415940] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.415988] intel_idle: MWAIT substates: 0x1120
[    0.415989] intel_idle: v0.4 model 0x2A
[    0.415990] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.416053] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.416057] ACPI: Power Button [PWRB]
[    0.416084] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.416086] ACPI: Power Button [PWRF]
[    0.416139] ACPI: Fan [FAN0] (off)
[    0.416158] ACPI: Fan [FAN1] (off)
[    0.416176] ACPI: Fan [FAN2] (off)
[    0.416193] ACPI: Fan [FAN3] (off)
[    0.416213] ACPI: Fan [FAN4] (off)
[    0.416255] ACPI: Requesting acpi_cpufreq
[    0.423659] thermal LNXTHERM:00: registered as thermal_zone0
[    0.423661] ACPI: Thermal Zone [TZ00] (28 C)
[    0.423828] thermal LNXTHERM:01: registered as thermal_zone1
[    0.423830] ACPI: Thermal Zone [TZ01] (30 C)
[    0.423855] GHES: HEST is not enabled!
[    0.423868] isapnp: Scanning for PnP cards...
[    0.423904] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.444334] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.445139] Linux agpgart interface v0.103
[    0.445972] brd: module loaded
[    0.446391] loop: module loaded
[    0.446461] ata_piix 0000:00:1f.2: version 2.13
[    0.446477] ata_piix 0000:00:1f.2: MAP [
[    0.446478]  P0 P2 P1 P3 ]
[    0.599356] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.599504] scsi0 : ata_piix
[    0.599568] scsi1 : ata_piix
[    0.599621] ata1: SATA max UDMA/133 cmd 0xf110 ctl 0xf100 bmdma 0xf0d0 irq 19
[    0.599626] ata2: SATA max UDMA/133 cmd 0xf0f0 ctl 0xf0e0 bmdma 0xf0d8 irq 19
[    0.599639] ata_piix 0000:00:1f.5: MAP [
[    0.599640]  P0 -- P1 -- ]
[    0.755304] ata_piix 0000:00:1f.5: SCR access via SIDPR is available but doesn't work
[    0.755310] ata_piix 0000:00:1f.5: setting latency timer to 64
[    0.755407] scsi2 : ata_piix
[    0.755460] scsi3 : ata_piix
[    0.755501] ata3: SATA max UDMA/133 cmd 0xf0b0 ctl 0xf0a0 bmdma 0xf070 irq 19
[    0.755502] ata4: SATA max UDMA/133 cmd 0xf090 ctl 0xf080 bmdma 0xf078 irq 19
[    0.755682] libphy: Fixed MDIO Bus: probed
[    0.755725] tun: Universal TUN/TAP device driver, 1.6
[    0.755726] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.755758] PPP generic driver version 2.4.2
[    0.755782] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.755783] ehci-pci: EHCI PCI platform driver
[    0.755804] ehci-pci 0000:00:1a.0: setting latency timer to 64
[    0.755806] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.755810] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.755822] ehci-pci 0000:00:1a.0: debug port 2
[    0.759722] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    0.759736] ehci-pci 0000:00:1a.0: irq 16, io mem 0xf7c07000
[    0.771298] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.771314] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.771315] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.771317] usb usb1: Product: EHCI Host Controller
[    0.771318] usb usb1: Manufacturer: Linux 3.8.0-44-generic ehci_hcd
[    0.771320] usb usb1: SerialNumber: 0000:00:1a.0
[    0.771391] hub 1-0:1.0: USB hub found
[    0.771394] hub 1-0:1.0: 2 ports detected
[    0.771485] ehci-pci 0000:00:1d.0: setting latency timer to 64
[    0.771488] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.771491] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.771503] ehci-pci 0000:00:1d.0: debug port 2
[    0.775404] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.775414] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf7c06000
[    0.777564] isapnp: No Plug & Play device found
[    0.787293] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.787303] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.787304] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.787306] usb usb2: Product: EHCI Host Controller
[    0.787307] usb usb2: Manufacturer: Linux 3.8.0-44-generic ehci_hcd
[    0.787308] usb usb2: SerialNumber: 0000:00:1d.0
[    0.787371] hub 2-0:1.0: USB hub found
[    0.787373] hub 2-0:1.0: 2 ports detected
[    0.787446] ehci-platform: EHCI generic platform driver
[    0.787451] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.787460] uhci_hcd: USB Universal Host Controller Interface driver
[    0.787511] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.787858] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.787863] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.787944] mousedev: PS/2 mouse device common for all mice
[    0.788019] rtc_cmos 00:05: RTC can wake from S4
[    0.788123] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.788147] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.788209] device-mapper: uevent: version 1.0.3
[    0.788247] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
[    0.788257] EISA: Probing bus 0 at eisa.0
[    0.788259] EISA: Cannot allocate resource for mainboard
[    0.788260] Cannot allocate resource for EISA slot 1
[    0.788261] Cannot allocate resource for EISA slot 2
[    0.788262] Cannot allocate resource for EISA slot 3
[    0.788263] Cannot allocate resource for EISA slot 4
[    0.788264] Cannot allocate resource for EISA slot 5
[    0.788265] Cannot allocate resource for EISA slot 6
[    0.788266] Cannot allocate resource for EISA slot 7
[    0.788267] Cannot allocate resource for EISA slot 8
[    0.788268] EISA: Detected 0 cards.
[    0.788273] cpufreq-nforce2: No nForce2 chipset.
[    0.788300] cpuidle: using governor ladder
[    0.788335] cpuidle: using governor menu
[    0.788337] ledtrig-cpu: registered to indicate activity on CPUs
[    0.788338] EFI Variables Facility v0.08 2004-May-17
[    0.788449] ashmem: initialized
[    0.788538] TCP: cubic registered
[    0.788611] NET: Registered protocol family 10
[    0.788735] NET: Registered protocol family 17
[    0.788744] Key type dns_resolver registered
[    0.788851] Using IPI No-Shortcut mode
[    0.788906] Loading module verification certificates
[    0.791983] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 2efbf4ad9582ee6e0ed6b7f07aeecd58f97a9eb0'
[    0.791993] registered taskstats version 1
[    0.793752] Key type trusted registered
[    0.795126] Key type encrypted registered
[    0.796753] rtc_cmos 00:05: setting system clock to 2015-01-29 10:10:11 UTC (1422526211)
[    0.797043] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.797045] EDD information not available.
[    1.083255] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.215522] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.215525] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.215859] hub 1-1:1.0: USB hub found
[    1.215932] hub 1-1:1.0: 4 ports detected
[    1.327177] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.391153] tsc: Refined TSC clocksource calibration: 2900.020 MHz
[    1.391167] Switching to clocksource tsc
[    1.459480] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.459485] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.459798] hub 2-1:1.0: USB hub found
[    1.460001] hub 2-1:1.0: 6 ports detected
[    1.731147] usb 2-1.1: new full-speed USB device number 3 using ehci-pci
[    1.826754] usb 2-1.1: New USB device found, idVendor=046d, idProduct=c52b
[    1.826759] usb 2-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.826762] usb 2-1.1: Product: USB Receiver
[    1.826765] usb 2-1.1: Manufacturer: Logitech
[    1.899097] usb 2-1.2: new low-speed USB device number 4 using ehci-pci
[    1.955027] ata1.01: failed to resume link (SControl 0)
[    1.962986] ata2.01: failed to resume link (SControl 0)
[    2.010717] usb 2-1.2: New USB device found, idVendor=04d9, idProduct=1702
[    2.010722] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.010725] usb 2-1.2: Product: USB Keyboard
[    2.010727] usb 2-1.2: Manufacturer:  
[    2.083043] usb 2-1.3: new high-speed USB device number 5 using ehci-pci
[    2.111010] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 330)
[    2.111021] ata1.01: SATA link down (SStatus 0 SControl 0)
[    2.118999] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 330)
[    2.119012] ata2.01: SATA link down (SStatus 0 SControl 0)
[    2.119021] ata2.01: link offline, clearing class 3 to NONE
[    2.119608] ata1.00: ATA-8: ST31000524AS, JC4B, max UDMA/133
[    2.119611] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.127214] ata2.00: ATAPI: HL-DT-ST DVDRAM GH24NS90, IN00, max UDMA/100
[    2.135520] ata1.00: configured for UDMA/133
[    2.135689] scsi 0:0:0:0: Direct-Access     ATA      ST31000524AS     JC4B PQ: 0 ANSI: 5
[    2.135787] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.135834] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.135957] sd 0:0:0:0: [sda] Write Protect is off
[    2.135960] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.136045] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.143107] ata2.00: configured for UDMA/100
[    2.152935] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH24NS90  IN00 PQ: 0 ANSI: 5
[    2.166973] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.166983] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.167111] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.167210] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.176807]  sda: sda1 sda2 < sda5 >
[    2.176860] usb 2-1.3: New USB device found, idVendor=7392, idProduct=7811
[    2.176862] usb 2-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.176863] usb 2-1.3: Product: 802.11n WLAN Adapter
[    2.176865] usb 2-1.3: Manufacturer: Realtek
[    2.176866] usb 2-1.3: SerialNumber: 00e04c000001
[    2.177175] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.177221] Freeing unused kernel memory: 800k freed
[    2.177329] Write protecting the kernel text: 6376k
[    2.177368] Write protecting the kernel read-only data: 2556k
[    2.177369] NX-protecting the kernel data: 5912k
[    2.188335] udevd[106]: starting version 175
[    2.244703] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.244921] r8169 0000:02:00.0: irq 40 for MSI/MSI-X
[    2.245067] r8169 0000:02:00.0 eth0: RTL8168evl/8111evl at 0xf841c000, d4:3d:7e:28:f7:05, XID 0c900800 IRQ 40
[    2.245069] r8169 0000:02:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    2.274539] usbcore: registered new interface driver usbhid
[    2.274542] usbhid: USB HID core driver
[    2.287960] input:   USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input2
[    2.288120] hid-generic 0003:04D9:1702.0004: input,hidraw0: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:1d.0-1.2/input0
[    2.291283] input:   USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/input/input3
[    2.291341] hid-generic 0003:04D9:1702.0005: input,hidraw1: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:1d.0-1.2/input1
[    2.350299] logitech-djreceiver 0003:046D:C52B.0003: hiddev0,hidraw2: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-1.1/input2
[    2.353676] input: Logitech Unifying Device. Wireless PID:1028 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.2/0003:046D:C52B.0003/input/input4
[    2.353750] logitech-djdevice 0003:046D:C52B.0006: input,hidraw3: USB HID v1.11 Mouse [Logitech Unifying Device. Wireless PID:1028] on usb-0000:00:1d.0-1.1:1
[    2.528937] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    3.724479] init: ureadahead main process (283) terminated with status 5
[    4.829616] Adding 4079612k swap on /dev/sda5.  Priority:-1 extents:1 across:4079612k 
[    5.634997] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.866215] udevd[358]: starting version 175
[    6.939409] lp: driver loaded but no devices found
[    7.100030] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    7.909736] parport_pc 00:0b: reported by Plug and Play ACPI
[    7.909784] parport0: PC-style at 0x378, irq 5 [PCSPP]
[    8.005275] lp0: using parport0 (interrupt-driven).
[    8.097413] ppdev: user-space parallel port driver
[    8.478809] ACPI Warning: 0x00000428-0x0000042f SystemIO conflicts with Region \PMIO 1 (20121018/utaddress-251)
[    8.478815] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.478818] ACPI Warning: 0x00000540-0x0000054f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[    8.478821] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.478822] ACPI Warning: 0x00000530-0x0000053f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[    8.478824] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.478825] ACPI Warning: 0x00000500-0x0000052f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[    8.478827] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.478828] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    8.490868] microcode: CPU0 sig=0x206a7, pf=0x2, revision=0x26
[    8.491550] mei 0000:00:16.0: setting latency timer to 64
[    8.491597] mei 0000:00:16.0: irq 41 for MSI/MSI-X
[    8.895922] [drm] Initialized drm 1.1.0 20060810
[    9.106162] microcode: CPU1 sig=0x206a7, pf=0x2, revision=0x26
[    9.107213] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    9.509179] [drm] Memory usable by graphics device = 2048M
[    9.509185] i915 0000:00:02.0: setting latency timer to 64
[    9.509541] i915 0000:00:02.0: irq 42 for MSI/MSI-X
[    9.509548] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    9.509549] [drm] Driver supports precise vblank timestamp query.
[    9.509609] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    9.722547] fbcon: inteldrmfb (fb0) is primary device
[    9.952725] Console: switching to colour frame buffer device 160x64
[    9.956048] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    9.956049] i915 0000:00:02.0: registered panic notifier
[    9.956859] acpi device:4e: registered as cooling_device7
[    9.956979] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    9.957086] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5
[    9.957529] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    9.957609] snd_hda_intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   10.043298] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   10.043399] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   10.043485] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   10.043573] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   10.043655] input: HDA Intel PCH Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   10.461479] Disabling lock debugging due to kernel taint
[   10.462474] rtl8192cu driver version=v4.0.2_9000.20130911
[   10.462475] build time: Nov  9 2014 23:24:44
[   10.462494] 
[   10.462494] usb_endpoint_descriptor(0):
[   10.462495] bLength=7
[   10.462496] bDescriptorType=5
[   10.462497] bEndpointAddress=81
[   10.462498] wMaxPacketSize=200
[   10.462499] bInterval=0
[   10.462500] RT_usb_endpoint_is_bulk_in = 1
[   10.462501] 
[   10.462501] usb_endpoint_descriptor(1):
[   10.462502] bLength=7
[   10.462502] bDescriptorType=5
[   10.462503] bEndpointAddress=2
[   10.462504] wMaxPacketSize=200
[   10.462505] bInterval=0
[   10.462506] RT_usb_endpoint_is_bulk_out = 2
[   10.462507] 
[   10.462507] usb_endpoint_descriptor(2):
[   10.462508] bLength=7
[   10.462509] bDescriptorType=5
[   10.462509] bEndpointAddress=3
[   10.462510] wMaxPacketSize=200
[   10.462511] bInterval=0
[   10.462512] RT_usb_endpoint_is_bulk_out = 3
[   10.462512] 
[   10.462512] usb_endpoint_descriptor(3):
[   10.462514] bLength=7
[   10.462514] bDescriptorType=5
[   10.462515] bEndpointAddress=84
[   10.462516] wMaxPacketSize=40
[   10.462517] bInterval=1
[   10.462518] RT_usb_endpoint_is_int_in = 4, Interval = 1
[   10.462519] nr_endpoint=4, in_num=2, out_num=2
[   10.462519] 
[   10.462520] USB_SPEED_HIGH
[   10.462524] CHIP TYPE: RTL8188C_8192C
[   10.462530] register rtw_netdev_ops to netdev_ops
[   10.462682] Chip Version ID: VERSION_NORMAL_TSMC_CHIP_88C.
[   10.462683] RF_Type is 3!!
[   10.463052] EEPROM type is E-FUSE
[   10.463053] ====> ReadAdapterInfo8192C
[   10.463177] Boot from EFUSE, Autoload OK !
[   10.615885] EEPROMVID = 0x7392
[   10.615888] EEPROMPID = 0x7811
[   10.615889] EEPROMCustomerID : 0x00
[   10.615890] EEPROMSubCustomerID: 0x00
[   10.615891] RT_CustomerID: 0x00
[   10.615892] _ReadMACAddress MAC Address from EFUSE = 80:1f:02:be:ec:1d
[   10.615894] EEPROMRegulatory = 0x0
[   10.615895] _ReadBoardType(0)
[   10.615896] BT Coexistance = disable
[   10.615897] mlmepriv.ChannelPlan = 0x00
[   10.615898] _ReadPSSetting...bHWPwrPindetect(0)-bHWPowerdown(0) ,bSupportRemoteWakeup(0)
[   10.615899] ### PS params=>  power_mgnt(0),usbss_enable(0) ###
[   10.615900] ### AntDivCfg(0)
[   10.615901] readAdapterInfo_8192CU(): REPLACEMENT = 1
[   10.615903] <==== ReadAdapterInfo8192C in 152 ms
[   10.616009] rtw_macaddr_cfg MAC Address  = 80:1f:02:be:ec:1d
[   10.616010] bDriverStopped:1, bSurpriseRemoved:0, bup:0, hw_init_completed:0
[   10.616338] _rtw_drv_register_netdev, MAC Address (if1) = 80:1f:02:be:ec:1d
[   10.616394] usbcore: registered new interface driver rtl8192cu
[   10.820612] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
[   11.188040] type=1400 audit(1422526221.886:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=944 comm="apparmor_parser"
[   11.188107] type=1400 audit(1422526221.886:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=783 comm="apparmor_parser"
[   11.188380] type=1400 audit(1422526221.890:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=944 comm="apparmor_parser"
[   11.188445] type=1400 audit(1422526221.890:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=783 comm="apparmor_parser"
[   11.188563] type=1400 audit(1422526221.890:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=944 comm="apparmor_parser"
[   11.188629] type=1400 audit(1422526221.890:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=783 comm="apparmor_parser"
[   11.189004] type=1400 audit(1422526221.890:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=774 comm="apparmor_parser"
[   11.189330] type=1400 audit(1422526221.890:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=774 comm="apparmor_parser"
[   11.189513] type=1400 audit(1422526221.890:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=774 comm="apparmor_parser"
[   12.179338] init: failsafe main process (968) killed by TERM signal
[   16.344002] Bluetooth: Core ver 2.16
[   16.344016] NET: Registered protocol family 31
[   16.344017] Bluetooth: HCI device and connection manager initialized
[   16.344023] Bluetooth: HCI socket layer initialized
[   16.344025] Bluetooth: L2CAP socket layer initialized
[   16.344029] Bluetooth: SCO socket layer initialized
[   16.351956] type=1400 audit(1422526227.054:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1077 comm="apparmor_parser"
[   16.352471] type=1400 audit(1422526227.054:12): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1077 comm="apparmor_parser"
[   16.453848] Bluetooth: RFCOMM TTY layer initialized
[   16.453858] Bluetooth: RFCOMM socket layer initialized
[   16.453859] Bluetooth: RFCOMM ver 1.11
[   16.578536] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.578539] Bluetooth: BNEP filters: protocol multicast
[   16.578546] Bluetooth: BNEP socket layer initialized
[   18.741931] type=1400 audit(1422526229.446:13): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1126 comm="apparmor_parser"
[   18.742282] type=1400 audit(1422526229.446:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1126 comm="apparmor_parser"
[   18.742468] type=1400 audit(1422526229.446:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1126 comm="apparmor_parser"
[   18.939876] type=1400 audit(1422526229.646:16): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1125 comm="apparmor_parser"
[   18.940144] type=1400 audit(1422526229.646:17): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=1125 comm="apparmor_parser"
[   19.102245] type=1400 audit(1422526229.806:18): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1131 comm="apparmor_parser"
[   19.102627] type=1400 audit(1422526229.806:19): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1131 comm="apparmor_parser"
[   19.105384] type=1400 audit(1422526229.806:20): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1133 comm="apparmor_parser"
[   19.711923] r8169 0000:02:00.0 eth0: link down
[   19.711964] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.712207] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.712995] rtw_wx_set_scan: bDriverStopped=1, bup=0, hw_init_completed=0
[   19.713245] +871x_drv - drv_open, bup=0
[   19.717347]  ===> FirmwareDownload91C() fw:Rtl819XFwImageArray_TSMC
[   19.717348] FirmwareDownload92C accquire FW from embedded image
[   19.717350] fw_ver=v88, fw_subver=2, sig=0x88c0
[   19.745463] fw download ok!
[   19.745466] Set RF Chip ID to RF_6052 and RF type to 1T1R.
[   20.124222] IQK:Start!!!
[   20.135092] Path A IQK Success!!
[   20.142716] Path A IQK Success!!
[   20.147339] IQK: final_candidate is 0
[   20.147341] IQK: RegE94=102 RegE9C=f RegEA4=fd RegEAC=3fd RegEB4=0 RegEBC=0 RegEC4=0 RegECC=0
[   20.147341]  Path A IQ Calibration Success !
[   20.257434] pdmpriv->TxPowerTrackControl = 1
[   20.262056] rtl8192cu_hal_init in 552ms
[   20.275761] MAC Address = 80:1f:02:be:ec:1d
[   20.275825] -871x_drv - drv_open, bup=1
[   20.275849] IPv6: ADDRCONF(NETDEV_UP): wlan4: link is not ready
[   20.276022] IPv6: ADDRCONF(NETDEV_UP): wlan4: link is not ready
[   20.276036] set_mode = IW_MODE_INFRA
[   20.279177] hw_var_set_opmode()-4234 mode = 2
[   20.651346] [rtw_wx_set_pmkid] IW_PMKSA_FLUSH!
[   20.651352] set_mode = IW_MODE_INFRA
[   20.651941] hw_var_set_opmode()-4234 mode = 2
[   20.657690] [rtw_wx_set_pmkid] IW_PMKSA_FLUSH!
[   21.021262] vboxdrv: Found 2 processor cores.
[   21.021530] vboxdrv: fAsync=0 offMin=0x1af offMax=0x9d9
[   21.021576] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   21.021577] vboxdrv: Successfully loaded version 4.3.4 (interface 0x001a0005).
[   21.390198] vboxpci: IOMMU not found (not registered)
[   21.771116] survey done event(13) band:0 for wlan4
[   21.803429] IW_SCAN_THIS_ESSID, ssid=Snowflake, len=9
[   22.914781] survey done event(1c) band:0 for wlan4
[   22.915142] wpa_set_auth_algs, AUTH_ALG_OPEN_SYSTEM
[   22.915146] set_mode = IW_MODE_INFRA
[   22.915154] 
[   22.915154]  wpa_ie(length:22):
[   22.915157] 0x30 0x14 0x01 0x00 0x00 0x0f 0xac 0x04 
[   22.915158] 0x01 0x00 0x00 0x0f 0xac 0x04 0x01 0x00 
[   22.915159] 0x00 0x0f 0xac 0x02 0x00 0x00 0x00 0x00 
[   22.915621] SetHwReg8192CU, 5130, RCR= 700060ca 
[   22.915631] =>rtw_wx_set_essid
[   22.915632] ssid=Snowflake, len=9
[   22.915635] Set SSID under fw_state=0x00000008
[   22.915638] [by_bssid:0][assoc_ssid:Snowflake][to_roaming:0] new candidate: Snowflake(ec:1a:59:b0:49:b0, ch1) rssi:-52
[   22.915640] rtw_select_and_join_from_scanned_queue: candidate: Snowflake(ec:1a:59:b0:49:b0, ch:1)
[   22.915644] link to Broadcom AP
[   22.915646] <=rtw_wx_set_essid, ret 0
[   22.915649] Set BSSID under fw_state=0x00000088
[   22.916403] hw_var_set_opmode()-4234 mode = 2
[   22.916778] start_join_set_ch_bw: ch=1, bwmode=0, ch_offset=0
[   22.951525] link to Broadcom AP
[   22.955893] OnAuthClient
[   22.955897] network.SupportedRates[0]=82
[   22.955898] network.SupportedRates[1]=84
[   22.955899] network.SupportedRates[2]=0B
[   22.955900] network.SupportedRates[3]=0C
[   22.955901] network.SupportedRates[4]=12
[   22.955902] network.SupportedRates[5]=16
[   22.955903] network.SupportedRates[6]=18
[   22.955903] network.SupportedRates[7]=24
[   22.955904] network.SupportedRates[8]=30
[   22.955905] network.SupportedRates[9]=48
[   22.955906] network.SupportedRates[10]=60
[   22.955907] network.SupportedRates[11]=6C
[   22.955908] bssrate_len = 12
[   22.960304] OnAssocRsp
[   22.960311] report_join_res(6)
[   22.960313] rtw_joinbss_update_network
[   22.960316] +rtw_update_ht_cap()
[   22.960321] rtw_joinbss_update_stainfo
[   22.960360] IPv6: ADDRCONF(NETDEV_CHANGE): wlan4: link becomes ready
[   22.960602] HW_VAR_BASIC_RATE: BrateCfg(0x15d)
[   22.961515] WMM(0): 0, a42b
[   22.961639] WMM(1): 0, a44f
[   22.961764] WMM(2): 0, 5e4322
[   22.961889] WMM(3): 0, 2f3222
[   22.961890] HTOnAssocRsp
[   22.964641] OnAction_back
[   22.964642] OnAction_back, action=0
[   22.964644] issue_action_BA, category=3, action=1, status=0
[   22.967265] update raid entry, mask=0xfffff, arg=0xa0
[   22.968762] rtl8192c_set_FwJoinBssReport_cmd mstatus(1)
[   22.969637] SetFwRsvdPagePkt
[   22.969641] Set RSVD page location to Fw.
[   22.970761] =>mlmeext_joinbss_event_callback
[   22.990737] 
[   22.990737]  ~~~~stastakey:unicastkey
[   22.990774]  ~~~~set sta key:groupkey
[   22.990776] ==> rtw_set_key algorithm(4),keyid(1),key_mask(0)
[   22.994221] SetHwReg8192CU, 5126, RCR= 700060ce 
[   24.285627] rtl8192c_dm_RF_Saving(): RF_Normal
[   24.755983] init: bumblebeed main process (1621) terminated with status 127
[   24.756003] init: bumblebeed main process ended, respawning
[   24.761596] init: bumblebeed main process (1661) terminated with status 127
[   24.761615] init: bumblebeed main process ended, respawning
[   24.767239] init: bumblebeed main process (1669) terminated with status 127
[   24.767257] init: bumblebeed main process ended, respawning
[   24.773286] init: bumblebeed main process (1677) terminated with status 127
[   24.773304] init: bumblebeed main process ended, respawning
[   24.779341] init: bumblebeed main process (1689) terminated with status 127
[   24.779360] init: bumblebeed main process ended, respawning
[   24.784916] init: bumblebeed main process (1697) terminated with status 127
[   24.784935] init: bumblebeed main process ended, respawning
[   24.790729] init: bumblebeed main process (1705) terminated with status 127
[   24.790747] init: bumblebeed main process ended, respawning
[   24.796835] init: bumblebeed main process (1713) terminated with status 127
[   24.796853] init: bumblebeed main process ended, respawning
[   24.802852] init: bumblebeed main process (1721) terminated with status 127
[   24.802871] init: bumblebeed main process ended, respawning
[   24.809060] init: bumblebeed main process (1729) terminated with status 127
[   24.809079] init: bumblebeed main process ended, respawning
[   24.815450] init: bumblebeed main process (1737) terminated with status 127
[   24.815468] init: bumblebeed respawning too fast, stopped
[   25.203588] FS-Cache: Loaded
[   25.362440] FS-Cache: Netfs 'cifs' registered for caching
[   25.362498] Key type cifs.spnego registered
[   25.362503] Key type cifs.idmap registered
[   25.532666] init: plymouth-stop pre-start process (1797) terminated with status 1
[   26.289664] rtl8192c_dm_RF_Saving(): RF_Save
[   37.316178] init: bumblebeed main process (2130) terminated with status 127
[   37.316196] init: bumblebeed main process ended, respawning
[   37.321747] init: bumblebeed main process (2138) terminated with status 127
[   37.321765] init: bumblebeed main process ended, respawning
[   37.327451] init: bumblebeed main process (2146) terminated with status 127
[   37.327472] init: bumblebeed main process ended, respawning
[   37.333015] init: bumblebeed main process (2154) terminated with status 127
[   37.333033] init: bumblebeed main process ended, respawning
[   37.338525] init: bumblebeed main process (2162) terminated with status 127
[   37.338543] init: bumblebeed main process ended, respawning
[   37.344226] init: bumblebeed main process (2170) terminated with status 127
[   37.344244] init: bumblebeed main process ended, respawning
[   37.350390] init: bumblebeed main process (2178) terminated with status 127
[   37.350409] init: bumblebeed main process ended, respawning
[   37.356142] init: bumblebeed main process (2186) terminated with status 127
[   37.356160] init: bumblebeed main process ended, respawning
[   37.361845] init: bumblebeed main process (2194) terminated with status 127
[   37.361863] init: bumblebeed main process ended, respawning
[   37.367646] init: bumblebeed main process (2202) terminated with status 127
[   37.367665] init: bumblebeed main process ended, respawning
[   37.373384] init: bumblebeed main process (2210) terminated with status 127
[   37.373402] init: bumblebeed respawning too fast, stopped
[   41.176065] Drop duplicate management frame with seq_num = 4090.
[   42.177011] survey done event(c) band:0 for wlan4
[   45.405635] CIFS VFS: Autodisabling the use of server inode numbers on \\Router\Snowman(A1). This server doesn't seem to support them properly. Hardlinks will not be recognized on this mount. Consider mounting with the "noserverino" option to silence this message.
[   82.145548] survey done event(14) band:0 for wlan4
[  142.102522] survey done event(1a) band:0 for wlan4
[  196.200068] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
[  222.035592] survey done event(13) band:0 for wlan4
[  321.957022] survey done event(f) band:0 for wlan4
[  359.161879] OnAction_back
[  359.161883] OnAction_back, action=0
[  359.161885] issue_action_BA, category=3, action=1, status=0
[  360.888517] rtw_issue_addbareq_cmd, p=0
[  360.888568] issue_action_BA, category=3, action=0, status=0
[  360.888571] BA_starting_seqctrl = 1157 for TID=0
[  360.892862] OnAction_back
[  360.892864] OnAction_back, action=1
[  360.892865] agg_enable for TID=0
[  441.866839] survey done event(16) band:0 for wlan4
[  560.830956] Drop duplicate management frame with seq_num = 2393.
[  561.830102] survey done event(10) band:0 for wlan4
[  681.795739] survey done event(1a) band:0 for wlan4
[  801.761590] survey done event(14) band:0 for wlan4
[  921.723201] survey done event(14) band:0 for wlan4
[ 1041.692768] survey done event(17) band:0 for wlan4
[ 1161.658487] survey done event(19) band:0 for wlan4
[ 1280.633343] Drop duplicate management frame with seq_num = 2554.
[ 1281.620074] survey done event(16) band:0 for wlan4

```

/var/log/Xorg.0.log
```
[    21.070] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    21.070] X Protocol Version 11, Revision 0
[    21.070] Build Operating System: Linux 2.6.42-37-generic i686 Ubuntu
[    21.070] Current Operating System: Linux Stardust 3.8.0-44-generic #66~precise1-Ubuntu SMP Tue Jul 15 04:04:23 UTC 2014 i686
[    21.070] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-44-generic root=UUID=23f334cb-51f2-4274-b680-8a5d612f366e ro quiet splash vt.handoff=7
[    21.070] Build Date: 09 December 2014  11:11:05PM
[    21.070] xorg-server 2:1.11.4-0ubuntu10.16 (For technical support please see http://www.ubuntu.com/support) 
[    21.070] Current version of pixman: 0.30.2
[    21.070]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    21.070] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    21.070] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Jan 29 03:10:31 2015
[    21.178] (==) Using config file: "/etc/X11/xorg.conf"
[    21.178] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    21.361] (==) ServerLayout "Layout0"
[    21.361] (**) |-->Screen "Screen0" (0)
[    21.361] (**) |   |-->Monitor "Monitor0"
[    21.362] (==) No device specified for screen "Screen0".
    Using the first device section listed.
[    21.362] (**) |   |-->Device "Card0"
[    21.380] (**) |-->Input Device "Keyboard0"
[    21.380] (**) |-->Input Device "Mouse0"
[    21.380] (==) Automatically adding devices
[    21.380] (==) Automatically enabling devices
[    21.410] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    21.410]     Entry deleted from font path.
[    21.410] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    21.410]     Entry deleted from font path.
[    21.410] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    21.410]     Entry deleted from font path.
[    21.410] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    21.410]     Entry deleted from font path.
[    21.410] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    21.410]     Entry deleted from font path.
[    21.410] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    21.410]     Entry deleted from font path.
[    21.410] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    21.410] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    21.410] (**) Extension "Composite" is enabled
[    21.410] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    21.410] (WW) Disabling Keyboard0
[    21.410] (WW) Disabling Mouse0
[    21.411] (II) Loader magic: 0xb77d15a0
[    21.411] (II) Module ABI versions:
[    21.411]     X.Org ANSI C Emulation: 0.4
[    21.411]     X.Org Video Driver: 11.0
[    21.411]     X.Org XInput driver : 16.0
[    21.411]     X.Org Server Extension : 6.0
[    21.411] (--) PCI:*(0:0:2:0) 8086:0102:1462:7788 rev 9, Mem @ 0xf7800000/4194304, 0xe0000000/268435456, I/O @ 0x0000f000/64
[    21.411] (II) Open ACPI successful (/var/run/acpid.socket)
[    21.411] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    21.411] (II) "extmod" will be loaded by default.
[    21.411] (II) "dbe" will be loaded by default.
[    21.411] (II) "glx" will be loaded by default.
[    21.411] (II) "record" will be loaded by default.
[    21.411] (II) "dri" will be loaded by default.
[    21.411] (II) "dri2" will be loaded by default.
[    21.411] (II) LoadModule: "extmod"
[    21.456] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    21.477] (II) Module extmod: vendor="X.Org Foundation"
[    21.477]     compiled for 1.11.3, module version = 1.0.0
[    21.477]     Module class: X.Org Server Extension
[    21.477]     ABI class: X.Org Server Extension, version 6.0
[    21.477] (II) Loading extension MIT-SCREEN-SAVER
[    21.477] (II) Loading extension XFree86-VidModeExtension
[    21.477] (II) Loading extension XFree86-DGA
[    21.516] (II) Loading extension DPMS
[    21.516] (II) Loading extension XVideo
[    21.516] (II) Loading extension XVideo-MotionCompensation
[    21.516] (II) Loading extension X-Resource
[    21.516] (II) LoadModule: "dbe"
[    21.516] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    21.544] (II) Module dbe: vendor="X.Org Foundation"
[    21.544]     compiled for 1.11.3, module version = 1.0.0
[    21.544]     Module class: X.Org Server Extension
[    21.544]     ABI class: X.Org Server Extension, version 6.0
[    21.544] (II) Loading extension DOUBLE-BUFFER
[    21.544] (II) LoadModule: "glx"
[    21.544] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[    23.661] (II) Module glx: vendor="NVIDIA Corporation"
[    23.661]     compiled for 4.0.2, module version = 1.0.0
[    23.661]     Module class: X.Org Server Extension
[    23.661] (II) NVIDIA GLX Module  304.125  Mon Dec  1 20:21:57 PST 2014
[    23.661] (II) Loading extension GLX
[    23.661] (II) LoadModule: "record"
[    23.661] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    23.710] (II) Module record: vendor="X.Org Foundation"
[    23.710]     compiled for 1.11.3, module version = 1.13.0
[    23.710]     Module class: X.Org Server Extension
[    23.710]     ABI class: X.Org Server Extension, version 6.0
[    23.710] (II) Loading extension RECORD
[    23.710] (II) LoadModule: "dri"
[    23.711] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    23.727] (II) Module dri: vendor="X.Org Foundation"
[    23.727]     compiled for 1.11.3, module version = 1.0.0
[    23.727]     ABI class: X.Org Server Extension, version 6.0
[    23.727] (II) Loading extension XFree86-DRI
[    23.727] (II) LoadModule: "dri2"
[    23.727] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    23.736] (II) Module dri2: vendor="X.Org Foundation"
[    23.736]     compiled for 1.11.3, module version = 1.2.0
[    23.736]     ABI class: X.Org Server Extension, version 6.0
[    23.736] (II) Loading extension DRI2
[    23.736] (II) LoadModule: "intel"
[    23.785] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    23.853] (II) Module intel: vendor="X.Org Foundation"
[    23.853]     compiled for 1.11.3, module version = 2.21.15
[    23.853]     Module class: X.Org Video Driver
[    23.853]     ABI class: X.Org Video Driver, version 11.0
[    23.853] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43, HD Graphics,
    HD Graphics 2000, HD Graphics 3000, HD Graphics 2500,
    HD Graphics 4000, HD Graphics P4000, HD Graphics 4600,
    HD Graphics 5000, HD Graphics P4600/P4700, Iris(TM) Graphics 5100,
    HD Graphics 4400, HD Graphics 4200, Iris(TM) Pro Graphics 5200
[    23.853] (++) using VT number 7

[    23.853] drmOpenDevice: node name is /dev/dri/card0
[    23.853] drmOpenDevice: open result is 8, (OK)
[    23.853] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    23.853] drmOpenDevice: node name is /dev/dri/card0
[    23.853] drmOpenDevice: open result is 8, (OK)
[    23.853] drmOpenByBusid: drmOpenMinor returns 8
[    23.853] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    23.853] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    23.854] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.21.15-makson1~ppa1 (Tomasz Makarewicz <makson96@gmail.com>)
[    23.867] (**) intel(0): Depth 24, (--) framebuffer bpp 32
[    23.867] (==) intel(0): RGB weight 888
[    23.867] (==) intel(0): Default visual is TrueColor
[    23.867] (**) intel(0): Option "AccelMethod" "sna"
[    23.867] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 2000
[    23.867] (--) intel(0): CPU: x86, sse2, sse3, ssse3, sse4.1, sse4.2
[    23.867] (**) intel(0): Framebuffer tiled
[    23.867] (**) intel(0): Pixmaps tiled
[    23.867] (**) intel(0): "Tear free" disabled
[    23.867] (**) intel(0): Forcing per-crtc-pixmaps? no
[    23.867] (II) intel(0): Output VGA1 using monitor section Monitor0
[    23.867] (II) intel(0): Output HDMI1 has no monitor section
[    23.867] (II) intel(0): Output DP1 has no monitor section
[    23.867] (--) intel(0): Output VGA1 using initial mode 1280x1024 on pipe 0
[    23.867] (==) intel(0): DPI set to (96, 96)
[    23.867] (II) Loading sub module "dri2"
[    23.867] (II) LoadModule: "dri2"
[    23.867] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    23.867] (II) Module dri2: vendor="X.Org Foundation"
[    23.867]     compiled for 1.11.3, module version = 1.2.0
[    23.867]     ABI class: X.Org Server Extension, version 6.0
[    23.867] (==) Depth 24 pixmap format is 32 bpp
[    23.962] (II) intel(0): SNA initialized with Sandybridge (gen6, gt1) backend
[    23.962] (==) intel(0): Backing store disabled
[    23.962] (==) intel(0): Silken mouse enabled
[    23.962] (II) intel(0): HW Cursor enabled
[    23.962] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    23.962] (==) intel(0): DPMS enabled
[    23.963] (II) intel(0): [DRI2] Setup complete
[    23.963] (II) intel(0): [DRI2]   DRI driver: i965
[    23.963] (II) intel(0): direct rendering: DRI2 Enabled
[    23.963] (==) intel(0): hotplug detection: "enabled"
[    23.963] (--) RandR disabled
[    23.963] (II) Initializing built-in extension Generic Event Extension
[    23.963] (II) Initializing built-in extension SHAPE
[    23.963] (II) Initializing built-in extension MIT-SHM
[    23.963] (II) Initializing built-in extension XInputExtension
[    23.963] (II) Initializing built-in extension XTEST
[    23.963] (II) Initializing built-in extension BIG-REQUESTS
[    23.963] (II) Initializing built-in extension SYNC
[    23.963] (II) Initializing built-in extension XKEYBOARD
[    23.963] (II) Initializing built-in extension XC-MISC
[    23.963] (II) Initializing built-in extension SECURITY
[    23.963] (II) Initializing built-in extension XINERAMA
[    23.963] (II) Initializing built-in extension XFIXES
[    23.963] (II) Initializing built-in extension RENDER
[    23.963] (II) Initializing built-in extension RANDR
[    23.963] (II) Initializing built-in extension COMPOSITE
[    23.963] (II) Initializing built-in extension DAMAGE
[    23.993] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    24.024] (II) intel(0): switch to mode 1280x1024@60.0 on pipe 0 using VGA1, position (0, 0), rotation normal
[    24.048] (II) intel(0): Setting screen physical size to 338 x 270
[    24.289] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    24.335] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    24.335] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    24.335] (II) LoadModule: "evdev"
[    24.335] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.417] (II) Module evdev: vendor="X.Org Foundation"
[    24.418]     compiled for 1.11.3, module version = 2.7.0
[    24.418]     Module class: X.Org XInput Driver
[    24.418]     ABI class: X.Org XInput driver, version 16.0
[    24.418] (II) Using input driver 'evdev' for 'Power Button'
[    24.418] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.418] (**) Power Button: always reports core events
[    24.418] (**) evdev: Power Button: Device: "/dev/input/event1"
[    24.418] (--) evdev: Power Button: Vendor 0 Product 0x1
[    24.418] (--) evdev: Power Button: Found keys
[    24.418] (II) evdev: Power Button: Configuring as keyboard
[    24.418] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    24.418] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    24.418] (**) Option "xkb_rules" "evdev"
[    24.418] (**) Option "xkb_model" "pc105"
[    24.418] (**) Option "xkb_layout" "us"
[    24.418] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    24.418] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    24.418] (II) Using input driver 'evdev' for 'Video Bus'
[    24.418] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.418] (**) Video Bus: always reports core events
[    24.418] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    24.418] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    24.418] (--) evdev: Video Bus: Found keys
[    24.418] (II) evdev: Video Bus: Configuring as keyboard
[    24.418] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5/event5"
[    24.418] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    24.418] (**) Option "xkb_rules" "evdev"
[    24.418] (**) Option "xkb_model" "pc105"
[    24.418] (**) Option "xkb_layout" "us"
[    24.419] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    24.419] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    24.419] (II) Using input driver 'evdev' for 'Power Button'
[    24.419] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.419] (**) Power Button: always reports core events
[    24.419] (**) evdev: Power Button: Device: "/dev/input/event0"
[    24.419] (--) evdev: Power Button: Vendor 0 Product 0x1
[    24.419] (--) evdev: Power Button: Found keys
[    24.419] (II) evdev: Power Button: Configuring as keyboard
[    24.419] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    24.419] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    24.419] (**) Option "xkb_rules" "evdev"
[    24.419] (**) Option "xkb_model" "pc105"
[    24.419] (**) Option "xkb_layout" "us"
[    24.419] (II) config/udev: Adding input device HDA Intel PCH Line Out (/dev/input/event10)
[    24.419] (II) No input driver specified, ignoring this device.
[    24.419] (II) This device may have been added with another device file.
[    24.420] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event6)
[    24.420] (II) No input driver specified, ignoring this device.
[    24.420] (II) This device may have been added with another device file.
[    24.420] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event7)
[    24.420] (II) No input driver specified, ignoring this device.
[    24.420] (II) This device may have been added with another device file.
[    24.420] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event8)
[    24.420] (II) No input driver specified, ignoring this device.
[    24.420] (II) This device may have been added with another device file.
[    24.420] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event9)
[    24.420] (II) No input driver specified, ignoring this device.
[    24.420] (II) This device may have been added with another device file.
[    24.420] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:1028 (/dev/input/event4)
[    24.420] (**) Logitech Unifying Device. Wireless PID:1028: Applying InputClass "evdev pointer catchall"
[    24.420] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:1028'
[    24.420] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.420] (**) Logitech Unifying Device. Wireless PID:1028: always reports core events
[    24.420] (**) evdev: Logitech Unifying Device. Wireless PID:1028: Device: "/dev/input/event4"
[    24.420] (--) evdev: Logitech Unifying Device. Wireless PID:1028: Vendor 0x46d Product 0xc52b
[    24.420] (--) evdev: Logitech Unifying Device. Wireless PID:1028: Found 20 mouse buttons
[    24.420] (--) evdev: Logitech Unifying Device. Wireless PID:1028: Found scroll wheel(s)
[    24.420] (--) evdev: Logitech Unifying Device. Wireless PID:1028: Found relative axes
[    24.420] (--) evdev: Logitech Unifying Device. Wireless PID:1028: Found x and y relative axes
[    24.420] (II) evdev: Logitech Unifying Device. Wireless PID:1028: Configuring as mouse
[    24.420] (II) evdev: Logitech Unifying Device. Wireless PID:1028: Adding scrollwheel support
[    24.420] (**) evdev: Logitech Unifying Device. Wireless PID:1028: YAxisMapping: buttons 4 and 5
[    24.420] (**) evdev: Logitech Unifying Device. Wireless PID:1028: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    24.420] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.2/0003:046D:C52B.0003/input/input4/event4"
[    24.420] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:1028" (type: MOUSE, id 9)
[    24.420] (II) evdev: Logitech Unifying Device. Wireless PID:1028: initialized for relative axes.
[    24.421] (**) Logitech Unifying Device. Wireless PID:1028: (accel) keeping acceleration scheme 1
[    24.421] (**) Logitech Unifying Device. Wireless PID:1028: (accel) acceleration profile 0
[    24.421] (**) Logitech Unifying Device. Wireless PID:1028: (accel) acceleration factor: 2.000
[    24.421] (**) Logitech Unifying Device. Wireless PID:1028: (accel) acceleration threshold: 4
[    24.421] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:1028 (/dev/input/mouse0)
[    24.421] (II) No input driver specified, ignoring this device.
[    24.421] (II) This device may have been added with another device file.
[    24.421] (II) config/udev: Adding input device   USB Keyboard (/dev/input/event2)
[    24.421] (**)   USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    24.421] (II) Using input driver 'evdev' for '  USB Keyboard'
[    24.421] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.421] (**)   USB Keyboard: always reports core events
[    24.421] (**) evdev:   USB Keyboard: Device: "/dev/input/event2"
[    24.421] (--) evdev:   USB Keyboard: Vendor 0x4d9 Product 0x1702
[    24.421] (--) evdev:   USB Keyboard: Found keys
[    24.421] (II) evdev:   USB Keyboard: Configuring as keyboard
[    24.421] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input2/event2"
[    24.421] (II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD, id 10)
[    24.421] (**) Option "xkb_rules" "evdev"
[    24.421] (**) Option "xkb_model" "pc105"
[    24.421] (**) Option "xkb_layout" "us"
[    24.422] (II) config/udev: Adding input device   USB Keyboard (/dev/input/event3)
[    24.422] (**)   USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    24.422] (II) Using input driver 'evdev' for '  USB Keyboard'
[    24.422] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.422] (**)   USB Keyboard: always reports core events
[    24.422] (**) evdev:   USB Keyboard: Device: "/dev/input/event3"
[    24.422] (--) evdev:   USB Keyboard: Vendor 0x4d9 Product 0x1702
[    24.422] (--) evdev:   USB Keyboard: Found keys
[    24.422] (II) evdev:   USB Keyboard: Configuring as keyboard
[    24.422] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/input/input3/event3"
[    24.422] (II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD, id 11)
[    24.422] (**) Option "xkb_rules" "evdev"
[    24.422] (**) Option "xkb_model" "pc105"
[    24.422] (**) Option "xkb_layout" "us"
[    29.488] (II) intel(0): EDID vendor "HWP", prod id 10326
[    29.488] (II) intel(0): Using EDID range info for horizontal sync
[    29.488] (II) intel(0): Using EDID range info for vertical refresh
[    29.488] (II) intel(0): Printing DDC gathered Modelines:
[    29.488] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    29.488] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    29.488] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    29.488] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    29.488] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    29.488] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    43.180] (II) XKB: reuse xkmfile /var/lib/xkb/server-06D88AAF5356C6CF875D73CED515513D3FEA00ED.xkm
[   101.447] (II) Open ACPI successful (/var/run/acpid.socket)
[   101.447] (II) intel(0): switch to mode 1280x1024@60.0 on pipe 0 using VGA1, position (0, 0), rotation normal
[   101.971] (II) XKB: reuse xkmfile /var/lib/xkb/server-06D88AAF5356C6CF875D73CED515513D3FEA00ED.xkm
[   203.549] (II) XKB: reuse xkmfile /var/lib/xkb/server-06D88AAF5356C6CF875D73CED515513D3FEA00ED.xkm
[   474.841] (II) Open ACPI successful (/var/run/acpid.socket)
[   474.841] (II) intel(0): switch to mode 1280x1024@60.0 on pipe 0 using VGA1, position (0, 0), rotation normal
[   475.149] (II) XKB: reuse xkmfile /var/lib/xkb/server-06D88AAF5356C6CF875D73CED515513D3FEA00ED.xkm
[   501.089] (II) Open ACPI successful (/var/run/acpid.socket)
[   501.089] (II) intel(0): switch to mode 1280x1024@60.0 on pipe 0 using VGA1, position (0, 0), rotation normal
[   501.373] (II) XKB: reuse xkmfile /var/lib/xkb/server-06D88AAF5356C6CF875D73CED515513D3FEA00ED.xkm
```

/etc/X11/xorg.conf
```
Section "Device" Identifier "Card0" Driver "intel" Option "AccelMethod" "sna" EndSection

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 304.123  (buildmeister@swio-display-x86-rhel47-07)  Wed Jul  2 12:15:30 PDT 2014


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection


```

---

### Post by Yellow Pasque on 2015-01-29
So you have an Intel GPU and you installed drivers for an Nvidia GPU? That's... interesting.

The first thing you should do is get rid of the nvidia drivers and delete the /etc/X11/xorg.conf

---

### Post by lelouch2 on 2015-02-02
> **Temüjin said:**
> So you have an Intel GPU and you installed drivers for an Nvidia GPU? That's... interesting.

The first thing you should do is get rid of the nvidia drivers and delete the /etc/X11/xorg.conf

Sorry about the delay in replying!

I have no idea what drivers I started with, but at various points I've looked up issues to other problems and read that I was supposed to upgrade to new nvidia drivers, so that's why I have them if I'm not supposed to.

Doing that made Unity unable to load at all. I replaced xorg.conf and reinstalled the nvidia-304 drivers to get it to load again. Here are my steps:

```
http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely

sudo apt-get remove nvidia-304
sudo apt-get remove nvidia-cg-toolkit (this removed dolphin-emu)
sudo apt-get remove nvidia-settings
sudo apt-get install ubuntu-desktop
Backed up xorg.conf in Documents/Ubuntu + computer/xconf backup 2015-feb-11
sudo rm /etc/X11/xorg.conf
Reboot - Unity doesn't start up.
Put the backup of xorg.conf back in /etc/X11.
Reboot - no change.
sudo apt-get install nvidia-304
Reboot - Unity loads again.
```

This also reminded me to check if dolphin-emu could run games. It says this then I try to open a game: "Failed to initialize video backend!" And this in the terminal: Xlib:  extension "GLX" missing on display ":0".

**Edit:** I tried a couple of other nvidia removal guides. Same thing.

```
http://ubuntuforums.org/showthread.php?t=1741783

ldd /usr/bin/glxinfo
sudo ldconfig
ldd /usr/bin/glxinfo

Previously: libGL.so.1 => /usr/lib/nvidia-304/libGL.so.1 (0xb75ec000)
Afterward:  libGL.so.1 => /usr/lib/nvidia-304/libGL.so.1 (0xb7674000)

Backed up xorg.conf to Documents/Ubuntu + computer/Feb 2 xorg conf/xorg.conf

sudo apt-get purge nvidia* (The following packages will be REMOVED:
  bumblebee-nvidia* dolphin-emu* nvidia-304* nvidia-cg-toolkit*
  nvidia-common* nvidia-settings* ubuntu-desktop* )

[At this point, the Internet icon froze and became unclickable, and IRC and Firefox couldn't connect, but for some reason I could still install things. So I decided to reinstall and then reboot.]

sudo apt-get install ubuntu-desktop
sudo apt-get install nvidia-304
Reboot - everything seems fine, and the Internet works properly. In tty, a message appeared, but disappeared before I types the whole thing: "CIFS VFS: Autodisabling the user of server inode numbers on \\Router\Snowman(A1). This server doesn't seem to support them properly."

sudo apt-get purge nvidia* (The following packages will be REMOVED:
  nvidia-304* nvidia-common* nvidia-settings* ubuntu-desktop* )
sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo update-alternatives --remove gl_conf /usr/lib/nvidia-current/ld.so.conf
Reboot - Unity doesn't load.
sudo apt-get install nvidia-304
Reboot - Unity loads.
```

---

### Post by Yellow Pasque on 2015-02-02
> It says this then I try to open a game: "Failed to initialize video backend!" And this in the terminal: Xlib: extension "GLX" missing on display ":0".
Installing the nvdia drivers may make your system less broken in the sense that X starts, but obviously, your 3D is still borked, which is to be expected since you have proprietary Nvidia 3D modules installed and you don't have an Nvidia GPU. It looks like you've got a lot of modifications/issues going on here (PPA's, outdated LTS kernels, proprietary video drivers for components you don't have, etc.). Quite frankly, there's no telling what other inapplicable advice you've followed to get your system in the state it is now.

I would try and remove the makson ppa like so:
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:makson96/mesa
```
Maybe then, you can successfully the nvidia drivers as you did above. If it still does not boot, then reinstall the nvidia drivers, boot the system and share the Xorg**.1**.log, which will be the log from the failed boot. It should show why exactly x/Unity will not start.

---

### Post by efflandt on 2015-02-02
What Nvidia card or chip do you think you have? Boot logs and **lspci -v** do not show any sign of any Nvidia device, only your integrated Intel video. So if you do have any nvidia video device, it is not working at all.

Your nvidia based xorg.conf is loading nvidia GL stuff that is incompatible with Intel and is the reason your graphics is not working properly. You should totally purge anything nvidia related and NOT reinstall it unless or until your computer has an nvidia graphics card. And rename or remove any /etc/X11/xorg.conf, so you have no file at all specifically called "xorg.conf". With default drivers, like for Intel graphics, X usually figures everything out automatically without xorg.conf.

---

### Post by lelouch2 on 2015-02-04
@Temüjin

Steps, just in case they're relevant:

```
sudo apt-get install ppa-purge (already the newest version)
sudo ppa-purge ppa:makson96/mesa

The following extra packages will be installed:
  libllvm3.1
Suggested packages:
  libglide3 libvdpau-doc nvidia-vdpau-driver vdpau-driver
The following NEW packages will be installed:
  libllvm3.1
The following packages will be DOWNGRADED:
  i965-va-driver libegl1-mesa libegl1-mesa-drivers libgbm1 libgl1-mesa-dev
  libgl1-mesa-dri libgl1-mesa-dri-experimental libgl1-mesa-glx libglapi-mesa
  libgles1-mesa libgles2-mesa libglu1-mesa libglu1-mesa-dev libkms1
  libopenvg1-mesa libosmesa6 libva-dev libva-glx1 libva-intel-vaapi-driver
  libva-tpi1 libva-x11-1 libva1 libvdpau-dev libvdpau1 libxatracker1
  linux-firmware mesa-common-dev mesa-utils vainfo xserver-xorg-video-ati
  xserver-xorg-video-fbdev xserver-xorg-video-intel
  xserver-xorg-video-nouveau xserver-xorg-video-radeon
  xserver-xorg-video-vesa

WARNING: The following packages cannot be authenticated!
  libllvm3.1

PPA purged successfully.

sudo apt-get purge nvidia*
Reboot - Unity doesn't load.
sudo apt-get install nvidia-304
Reboot - Unity loads.
```

So Unity didn't load and I had to reinstall nvidia-304 again, but here's the Xorg.1.log!

```
[377821.716] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[377821.716] X Protocol Version 11, Revision 0
[377821.716] Build Operating System: Linux 2.6.42-37-generic i686 Ubuntu
[377821.716] Current Operating System: Linux Stardust 3.8.0-44-generic #66~precise1-Ubuntu SMP Tue Jul 15 04:04:23 UTC 2014 i686
[377821.716] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-44-generic root=UUID=23f334cb-51f2-4274-b680-8a5d612f366e ro quiet splash vt.handoff=7
[377821.716] Build Date: 16 October 2013  04:45:22PM
[377821.716] xorg-server 2:1.11.4-0ubuntu10.14 (For technical support please see http://www.ubuntu.com/support) 
[377821.716] Current version of pixman: 0.30.2
[377821.716]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[377821.716] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[377821.717] (==) Log file: "/var/log/Xorg.1.log", Time: Mon Dec  1 20:24:12 2014
[377821.734] (==) Using config file: "/etc/X11/xorg.conf"
[377821.734] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[377821.815] (==) ServerLayout "Layout0"
[377821.815] (**) |-->Screen "Screen0" (0)
[377821.815] (**) |   |-->Monitor "Monitor0"
[377821.815] (==) No device specified for screen "Screen0".
    Using the first device section listed.
[377821.815] (**) |   |-->Device "Device0"
[377821.816] (**) |-->Input Device "Keyboard0"
[377821.816] (**) |-->Input Device "Mouse0"
[377821.816] (==) Automatically adding devices
[377821.816] (==) Automatically enabling devices
[377821.844] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[377821.844]     Entry deleted from font path.
[377821.844] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[377821.844]     Entry deleted from font path.
[377821.844] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[377821.844]     Entry deleted from font path.
[377821.845] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[377821.845]     Entry deleted from font path.
[377821.845] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[377821.845]     Entry deleted from font path.
[377821.845] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[377821.845]     Entry deleted from font path.
[377821.845] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[377821.845] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[377821.845] (**) Extension "Composite" is enabled
[377821.845] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[377821.845] (WW) Disabling Keyboard0
[377821.845] (WW) Disabling Mouse0
[377821.845] (II) Loader magic: 0xb77d25a0
[377821.845] (II) Module ABI versions:
[377821.845]     X.Org ANSI C Emulation: 0.4
[377821.845]     X.Org Video Driver: 11.0
[377821.845]     X.Org XInput driver : 16.0
[377821.845]     X.Org Server Extension : 6.0
[377821.846] (--) PCI:*(0:0:2:0) 8086:0102:1462:7788 rev 9, Mem @ 0xf7800000/4194304, 0xe0000000/268435456, I/O @ 0x0000f000/64
[377821.846] (II) Open ACPI successful (/var/run/acpid.socket)
[377821.846] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[377821.846] (II) "extmod" will be loaded by default.
[377821.846] (II) "dbe" will be loaded by default.
[377821.846] (II) "glx" will be loaded by default.
[377821.846] (II) "record" will be loaded by default.
[377821.846] (II) "dri" will be loaded by default.
[377821.846] (II) "dri2" will be loaded by default.
[377821.846] (II) LoadModule: "extmod"
[377821.867] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[377821.887] (II) Module extmod: vendor="X.Org Foundation"
[377821.887]     compiled for 1.11.3, module version = 1.0.0
[377821.887]     Module class: X.Org Server Extension
[377821.887]     ABI class: X.Org Server Extension, version 6.0
[377821.887] (II) Loading extension MIT-SCREEN-SAVER
[377821.887] (II) Loading extension XFree86-VidModeExtension
[377821.887] (II) Loading extension XFree86-DGA
[377821.887] (II) Loading extension DPMS
[377821.887] (II) Loading extension XVideo
[377821.887] (II) Loading extension XVideo-MotionCompensation
[377821.887] (II) Loading extension X-Resource
[377821.887] (II) LoadModule: "dbe"
[377821.887] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[377821.888] (II) Module dbe: vendor="X.Org Foundation"
[377821.888]     compiled for 1.11.3, module version = 1.0.0
[377821.888]     Module class: X.Org Server Extension
[377821.888]     ABI class: X.Org Server Extension, version 6.0
[377821.888] (II) Loading extension DOUBLE-BUFFER
[377821.888] (II) LoadModule: "glx"
[377821.888] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[377822.381] (II) Module glx: vendor="NVIDIA Corporation"
[377822.381]     compiled for 4.0.2, module version = 1.0.0
[377822.381]     Module class: X.Org Server Extension
[377822.381] (II) NVIDIA GLX Module  304.123  Wed Jul  2 11:29:39 PDT 2014
[377822.381] (II) Loading extension GLX
[377822.381] (II) LoadModule: "record"
[377822.381] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[377822.403] (II) Module record: vendor="X.Org Foundation"
[377822.403]     compiled for 1.11.3, module version = 1.13.0
[377822.403]     Module class: X.Org Server Extension
[377822.403]     ABI class: X.Org Server Extension, version 6.0
[377822.403] (II) Loading extension RECORD
[377822.403] (II) LoadModule: "dri"
[377822.403] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[377822.407] (II) Module dri: vendor="X.Org Foundation"
[377822.407]     compiled for 1.11.3, module version = 1.0.0
[377822.407]     ABI class: X.Org Server Extension, version 6.0
[377822.407] (II) Loading extension XFree86-DRI
[377822.407] (II) LoadModule: "dri2"
[377822.407] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[377822.408] (II) Module dri2: vendor="X.Org Foundation"
[377822.408]     compiled for 1.11.3, module version = 1.2.0
[377822.408]     ABI class: X.Org Server Extension, version 6.0
[377822.408] (II) Loading extension DRI2
[377822.408] (II) LoadModule: "nvidia"
[377822.408] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[377822.514] (II) Module nvidia: vendor="NVIDIA Corporation"
[377822.514]     compiled for 4.0.2, module version = 1.0.0
[377822.514]     Module class: X.Org Video Driver
[377822.935] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[377822.935] (EE) NVIDIA:     system's kernel log for additional error messages.
[377822.935] (II) UnloadModule: "nvidia"
[377822.935] (II) Unloading nvidia
[377822.935] (EE) Failed to load module "nvidia" (module-specific error, 0)
[377822.935] (==) Matched intel as autoconfigured driver 0
[377822.935] (==) Matched vesa as autoconfigured driver 1
[377822.935] (==) Matched fbdev as autoconfigured driver 2
[377822.935] (==) Assigned the driver to the xf86ConfigLayout
[377822.935] (II) LoadModule: "intel"
[377823.018] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[377823.053] (II) Module intel: vendor="X.Org Foundation"
[377823.053]     compiled for 1.11.3, module version = 2.21.15
[377823.053]     Module class: X.Org Video Driver
[377823.053]     ABI class: X.Org Video Driver, version 11.0
[377823.053] (II) LoadModule: "vesa"
[377823.053] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[377823.065] (II) Module vesa: vendor="X.Org Foundation"
[377823.065]     compiled for 1.11.3, module version = 2.3.3
[377823.065]     Module class: X.Org Video Driver
[377823.065]     ABI class: X.Org Video Driver, version 11.0
[377823.065] (II) LoadModule: "fbdev"
[377823.065] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[377823.083] (II) Module fbdev: vendor="X.Org Foundation"
[377823.083]     compiled for 1.11.3, module version = 0.4.4
[377823.083]     Module class: X.Org Video Driver
[377823.083]     ABI class: X.Org Video Driver, version 11.0
[377823.083] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43, HD Graphics,
    HD Graphics 2000, HD Graphics 3000, HD Graphics 2500,
    HD Graphics 4000, HD Graphics P4000, HD Graphics 4600,
    HD Graphics 5000, HD Graphics P4600/P4700, Iris(TM) Graphics 5100,
    HD Graphics 4400, HD Graphics 4200, Iris(TM) Pro Graphics 5200
[377823.083] (II) VESA: driver for VESA chipsets: vesa
[377823.083] (II) FBDEV: driver for framebuffer: fbdev
[377823.083] (++) using VT number 8

[377823.083] drmOpenDevice: node name is /dev/dri/card0
[377823.083] drmOpenDevice: open result is 8, (OK)
[377823.083] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[377823.083] drmOpenDevice: node name is /dev/dri/card0
[377823.083] drmOpenDevice: open result is 8, (OK)
[377823.084] drmOpenByBusid: drmOpenMinor returns 8
[377823.084] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[377823.084] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[377823.084] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.21.15-makson1~ppa1 (Tomasz Makarewicz <makson96@gmail.com>)
[377823.084] (WW) Falling back to old probe method for vesa
[377823.084] (WW) Falling back to old probe method for fbdev
[377823.084] (II) Loading sub module "fbdevhw"
[377823.084] (II) LoadModule: "fbdevhw"
[377823.084] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[377823.100] (II) Module fbdevhw: vendor="X.Org Foundation"
[377823.101]     compiled for 1.11.3, module version = 0.0.2
[377823.101]     ABI class: X.Org Video Driver, version 11.0
[377823.101] (**) intel(0): Depth 24, (--) framebuffer bpp 32
[377823.101] (==) intel(0): RGB weight 888
[377823.101] (==) intel(0): Default visual is TrueColor
[377823.101] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 2000
[377823.101] (--) intel(0): CPU: x86, sse2, sse3, ssse3, sse4.1, sse4.2
[377823.101] (**) intel(0): Framebuffer tiled
[377823.101] (**) intel(0): Pixmaps tiled
[377823.101] (**) intel(0): "Tear free" disabled
[377823.101] (**) intel(0): Forcing per-crtc-pixmaps? no
[377823.101] (II) intel(0): Output VGA1 using monitor section Monitor0
[377823.102] (II) intel(0): Output HDMI1 has no monitor section
[377823.102] (II) intel(0): Output DP1 has no monitor section
[377823.102] (--) intel(0): Output VGA1 using initial mode 1280x1024 on pipe 0
[377823.102] (==) intel(0): DPI set to (96, 96)
[377823.102] (II) Loading sub module "dri2"
[377823.102] (II) LoadModule: "dri2"
[377823.102] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[377823.102] (II) Module dri2: vendor="X.Org Foundation"
[377823.102]     compiled for 1.11.3, module version = 1.2.0
[377823.102]     ABI class: X.Org Server Extension, version 6.0
[377823.102] (II) UnloadModule: "vesa"
[377823.102] (II) Unloading vesa
[377823.102] (II) UnloadModule: "fbdev"
[377823.102] (II) Unloading fbdev
[377823.102] (II) UnloadModule: "fbdevhw"
[377823.102] (II) Unloading fbdevhw
[377823.102] (==) Depth 24 pixmap format is 32 bpp
[377823.120] (II) intel(0): SNA initialized with Sandybridge (gen6, gt1) backend
[377823.120] (==) intel(0): Backing store disabled
[377823.120] (==) intel(0): Silken mouse enabled
[377823.120] (II) intel(0): HW Cursor enabled
[377823.120] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[377823.121] (==) intel(0): DPMS enabled
[377823.144] (II) intel(0): [DRI2] Setup complete
[377823.144] (II) intel(0): [DRI2]   DRI driver: i965
[377823.144] (II) intel(0): direct rendering: DRI2 Enabled
[377823.144] (==) intel(0): hotplug detection: "enabled"
[377823.144] (--) RandR disabled
[377823.144] (II) Initializing built-in extension Generic Event Extension
[377823.144] (II) Initializing built-in extension SHAPE
[377823.144] (II) Initializing built-in extension MIT-SHM
[377823.144] (II) Initializing built-in extension XInputExtension
[377823.144] (II) Initializing built-in extension XTEST
[377823.144] (II) Initializing built-in extension BIG-REQUESTS
[377823.144] (II) Initializing built-in extension SYNC
[377823.144] (II) Initializing built-in extension XKEYBOARD
[377823.144] (II) Initializing built-in extension XC-MISC
[377823.144] (II) Initializing built-in extension SECURITY
[377823.144] (II) Initializing built-in extension XINERAMA
[377823.144] (II) Initializing built-in extension XFIXES
[377823.144] (II) Initializing built-in extension RENDER
[377823.144] (II) Initializing built-in extension RANDR
[377823.144] (II) Initializing built-in extension COMPOSITE
[377823.144] (II) Initializing built-in extension DAMAGE
[377823.156] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[377823.163] (II) intel(0): switch to mode 1280x1024@60.0 on pipe 0 using VGA1, position (0, 0), rotation normal
[377823.188] (II) intel(0): Setting screen physical size to 338 x 270
[377823.268] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[377823.279] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[377823.279] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[377823.279] (II) LoadModule: "evdev"
[377823.279] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[377823.280] (II) Module evdev: vendor="X.Org Foundation"
[377823.280]     compiled for 1.11.3, module version = 2.7.0
[377823.280]     Module class: X.Org XInput Driver
[377823.280]     ABI class: X.Org XInput driver, version 16.0
[377823.280] (II) Using input driver 'evdev' for 'Power Button'
[377823.280] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[377823.280] (**) Power Button: always reports core events
[377823.280] (**) evdev: Power Button: Device: "/dev/input/event1"
[377823.280] (--) evdev: Power Button: Vendor 0 Product 0x1
[377823.280] (--) evdev: Power Button: Found keys
[377823.280] (II) evdev: Power Button: Configuring as keyboard
[377823.280] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[377823.280] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[377823.280] (**) Option "xkb_rules" "evdev"
[377823.280] (**) Option "xkb_model" "pc105"
[377823.280] (**) Option "xkb_layout" "us"
[377823.281] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[377823.281] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[377823.281] (II) Using input driver 'evdev' for 'Video Bus'
[377823.281] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[377823.281] (**) Video Bus: always reports core events
[377823.281] (**) evdev: Video Bus: Device: "/dev/input/event5"
[377823.281] (--) evdev: Video Bus: Vendor 0 Product 0x6
[377823.281] (--) evdev: Video Bus: Found keys
[377823.281] (II) evdev: Video Bus: Configuring as keyboard
[377823.281] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5/event5"
[377823.281] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[377823.281] (**) Option "xkb_rules" "evdev"
[377823.281] (**) Option "xkb_model" "pc105"
[377823.281] (**) Option "xkb_layout" "us"
[377823.281] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[377823.281] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[377823.281] (II) Using input driver 'evdev' for 'Power Button'
[377823.281] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[377823.281] (**) Power Button: always reports core events
[377823.281] (**) evdev: Power Button: Device: "/dev/input/event0"
[377823.281] (--) evdev: Power Button: Vendor 0 Product 0x1
[377823.281] (--) evdev: Power Button: Found keys
[377823.281] (II) evdev: Power Button: Configuring as keyboard
[377823.281] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[377823.281] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[377823.281] (**) Option "xkb_rules" "evdev"
[377823.281] (**) Option "xkb_model" "pc105"
[377823.281] (**) Option "xkb_layout" "us"
[377823.282] (II) config/udev: Adding input device   USB Keyboard (/dev/input/event2)
[377823.282] (**)   USB Keyboard: Applying InputClass "evdev keyboard catchall"
[377823.282] (II) Using input driver 'evdev' for '  USB Keyboard'
[377823.282] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[377823.282] (**)   USB Keyboard: always reports core events
[377823.282] (**) evdev:   USB Keyboard: Device: "/dev/input/event2"
[377823.282] (--) evdev:   USB Keyboard: Vendor 0x4d9 Product 0x1702
[377823.282] (--) evdev:   USB Keyboard: Found keys
[377823.282] (II) evdev:   USB Keyboard: Configuring as keyboard
[377823.282] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input22/event2"
[377823.282] (II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD, id 9)
[377823.282] (**) Option "xkb_rules" "evdev"
[377823.282] (**) Option "xkb_model" "pc105"
[377823.282] (**) Option "xkb_layout" "us"
[377823.283] (II) config/udev: Adding input device   USB Keyboard (/dev/input/event3)
[377823.283] (**)   USB Keyboard: Applying InputClass "evdev keyboard catchall"
[377823.283] (II) Using input driver 'evdev' for '  USB Keyboard'
[377823.283] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[377823.283] (**)   USB Keyboard: always reports core events
[377823.283] (**) evdev:   USB Keyboard: Device: "/dev/input/event3"
[377823.283] (--) evdev:   USB Keyboard: Vendor 0x4d9 Product 0x1702
[377823.283] (--) evdev:   USB Keyboard: Found keys
[377823.283] (II) evdev:   USB Keyboard: Configuring as keyboard
[377823.283] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.1/input/input23/event3"
[377823.283] (II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD, id 10)
[377823.283] (**) Option "xkb_rules" "evdev"
[377823.283] (**) Option "xkb_model" "pc105"
[377823.283] (**) Option "xkb_layout" "us"
[377823.283] (II) config/udev: Adding input device HDA Intel PCH Line Out (/dev/input/event10)
[377823.283] (II) No input driver specified, ignoring this device.
[377823.283] (II) This device may have been added with another device file.
[377823.283] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event6)
[377823.283] (II) No input driver specified, ignoring this device.
[377823.283] (II) This device may have been added with another device file.
[377823.283] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event7)
[377823.283] (II) No input driver specified, ignoring this device.
[377823.283] (II) This device may have been added with another device file.
[377823.284] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event8)
[377823.284] (II) No input driver specified, ignoring this device.
[377823.284] (II) This device may have been added with another device file.
[377823.284] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event9)
[377823.284] (II) No input driver specified, ignoring this device.
[377823.284] (II) This device may have been added with another device file.
[377823.284] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:1028 (/dev/input/event4)
[377823.284] (**) Logitech Unifying Device. Wireless PID:1028: Applying InputClass "evdev pointer catchall"
[377823.284] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:1028'
[377823.284] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[377823.284] (**) Logitech Unifying Device. Wireless PID:1028: always reports core events
[377823.284] (**) evdev: Logitech Unifying Device. Wireless PID:1028: Device: "/dev/input/event4"
[377823.284] (--) evdev: Logitech Unifying Device. Wireless PID:1028: Vendor 0x46d Product 0xc52b
[377823.284] (--) evdev: Logitech Unifying Device. Wireless PID:1028: Found 20 mouse buttons
[377823.284] (--) evdev: Logitech Unifying Device. Wireless PID:1028: Found scroll wheel(s)
[377823.284] (--) evdev: Logitech Unifying Device. Wireless PID:1028: Found relative axes
[377823.284] (--) evdev: Logitech Unifying Device. Wireless PID:1028: Found x and y relative axes
[377823.284] (II) evdev: Logitech Unifying Device. Wireless PID:1028: Configuring as mouse
[377823.284] (II) evdev: Logitech Unifying Device. Wireless PID:1028: Adding scrollwheel support
[377823.284] (**) evdev: Logitech Unifying Device. Wireless PID:1028: YAxisMapping: buttons 4 and 5
[377823.284] (**) evdev: Logitech Unifying Device. Wireless PID:1028: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[377823.284] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.2/0003:046D:C52B.0019/input/input15/event4"
[377823.284] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:1028" (type: MOUSE, id 11)
[377823.284] (II) evdev: Logitech Unifying Device. Wireless PID:1028: initialized for relative axes.
[377823.284] (**) Logitech Unifying Device. Wireless PID:1028: (accel) keeping acceleration scheme 1
[377823.284] (**) Logitech Unifying Device. Wireless PID:1028: (accel) acceleration profile 0
[377823.284] (**) Logitech Unifying Device. Wireless PID:1028: (accel) acceleration factor: 2.000
[377823.284] (**) Logitech Unifying Device. Wireless PID:1028: (accel) acceleration threshold: 4
[377823.284] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:1028 (/dev/input/mouse0)
[377823.284] (II) No input driver specified, ignoring this device.
[377823.284] (II) This device may have been added with another device file.
[377825.660] (II) intel(0): EDID vendor "HWP", prod id 10326
[377825.660] (II) intel(0): Using EDID range info for horizontal sync
[377825.660] (II) intel(0): Using EDID range info for vertical refresh
[377825.660] (II) intel(0): Printing DDC gathered Modelines:
[377825.660] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[377825.660] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[377825.660] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[377825.660] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[377825.660] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[377825.660] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[377832.187] (II) evdev: Logitech Unifying Device. Wireless PID:1028: Close
[377832.187] (II) UnloadModule: "evdev"
[377832.187] (II) Unloading evdev
[377832.187] (II) evdev:   USB Keyboard: Close
[377832.187] (II) UnloadModule: "evdev"
[377832.187] (II) Unloading evdev
[377832.187] (II) evdev:   USB Keyboard: Close
[377832.187] (II) UnloadModule: "evdev"
[377832.187] (II) Unloading evdev
[377832.187] (II) evdev: Power Button: Close
[377832.187] (II) UnloadModule: "evdev"
[377832.187] (II) Unloading evdev
[377832.187] (II) evdev: Video Bus: Close
[377832.187] (II) UnloadModule: "evdev"
[377832.187] (II) Unloading evdev
[377832.187] (II) evdev: Power Button: Close
[377832.187] (II) UnloadModule: "evdev"
[377832.187] (II) Unloading evdev
[377832.192]  ddxSigGiveUp: Closing log
[377832.192] Server terminated successfully (0). Closing log file.
```

@efflandt

> What Nvidia card or chip do you think you have? Boot logs and **lspci -v**  do not show any sign of any Nvidia device, only your integrated Intel  video. So if you do have any nvidia video device, it is not working at  all.

Your nvidia based xorg.conf is loading nvidia GL stuff that is  incompatible with Intel and is the reason your graphics is not working  properly. You should totally purge anything nvidia related and NOT  reinstall it unless or until your computer has an nvidia graphics card.  And rename or remove any /etc/X11/xorg.conf, so you have no file at all  specifically called "xorg.conf". With default drivers, like for Intel  graphics, X usually figures everything out automatically without  xorg.conf.

I don't think I have a Nvidia device. I just ended up with Nvidia drivers at some point, and they finally broke things.

I posted that I tried purging Nvidia completely and getting rid of xorg.conf on February 1. But I had to bring them back so that I could use the computer. If there's something I should do after purging it, then I'll purge it again.

```

**February 1**

sudo apt-get remove nvidia-304
sudo apt-get remove nvidia-cg-toolkit (this removed dolphin-emu)
sudo apt-get remove nvidia-settings
sudo apt-get install ubuntu-desktop
Backed up xorg.conf in Documents/Ubuntu + computer/xconf backup 2015-feb-11
sudo rm /etc/X11/xorg.conf
Reboot - Unity doesn't start up.
Put the backup of xorg.conf back in /etc/X11.
Reboot - no change.
sudo apt-get install nvidia-304
Reboot - Unity loads again.
```

---

### Post by Yellow Pasque on 2015-02-07
Sorry, the file that might help is **Xorg.0.log.old**. (that's not the first time I confused it with Xorg.1.log...) Repeat the experiment and then post that file.

---

### Post by lelouch2 on 2015-02-09
> **Temüjin said:**
> Sorry, the file that might help is **Xorg.0.log.old**. (that's not the first time I confused it with Xorg.1.log...) Repeat the experiment and then post that file.

Okay, here's that.

```
[    21.837] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    21.837] X Protocol Version 11, Revision 0
[    21.837] Build Operating System: Linux 2.6.42-37-generic i686 Ubuntu
[    21.837] Current Operating System: Linux Stardust 3.8.0-44-generic #66~precise1-Ubuntu SMP Tue Jul 15 04:04:23 UTC 2014 i686
[    21.837] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-44-generic root=UUID=23f334cb-51f2-4274-b680-8a5d612f366e ro quiet splash vt.handoff=7
[    21.837] Build Date: 09 December 2014  11:11:05PM
[    21.837] xorg-server 2:1.11.4-0ubuntu10.16 (For technical support please see http://www.ubuntu.com/support) 
[    21.837] Current version of pixman: 0.30.2
[    21.837]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    21.837] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    21.837] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Feb  3 22:54:32 2015
[    21.985] (==) Using config file: "/etc/X11/xorg.conf"
[    21.985] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    22.192] (==) ServerLayout "Layout0"
[    22.192] (**) |-->Screen "Screen0" (0)
[    22.192] (**) |   |-->Monitor "Monitor0"
[    22.192] (==) No device specified for screen "Screen0".
    Using the first device section listed.
[    22.192] (**) |   |-->Device "Card0"
[    22.204] (**) |-->Input Device "Keyboard0"
[    22.204] (**) |-->Input Device "Mouse0"
[    22.204] (==) Automatically adding devices
[    22.204] (==) Automatically enabling devices
[    22.225] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    22.225]     Entry deleted from font path.
[    22.225] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    22.225]     Entry deleted from font path.
[    22.225] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    22.225]     Entry deleted from font path.
[    22.231] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    22.231]     Entry deleted from font path.
[    22.231] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    22.231]     Entry deleted from font path.
[    22.231] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    22.231]     Entry deleted from font path.
[    22.231] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    22.231] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    22.231] (**) Extension "Composite" is enabled
[    22.231] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    22.231] (WW) Disabling Keyboard0
[    22.231] (WW) Disabling Mouse0
[    22.244] (II) Loader magic: 0xb77f65a0
[    22.244] (II) Module ABI versions:
[    22.244]     X.Org ANSI C Emulation: 0.4
[    22.244]     X.Org Video Driver: 11.0
[    22.244]     X.Org XInput driver : 16.0
[    22.244]     X.Org Server Extension : 6.0
[    22.244] (--) PCI:*(0:0:2:0) 8086:0102:1462:7788 rev 9, Mem @ 0xf7800000/4194304, 0xe0000000/268435456, I/O @ 0x0000f000/64
[    22.244] (II) Open ACPI successful (/var/run/acpid.socket)
[    22.244] (II) LoadModule: "extmod"
[    22.321] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    22.345] (II) Module extmod: vendor="X.Org Foundation"
[    22.345]     compiled for 1.11.3, module version = 1.0.0
[    22.345]     Module class: X.Org Server Extension
[    22.345]     ABI class: X.Org Server Extension, version 6.0
[    22.345] (II) Loading extension MIT-SCREEN-SAVER
[    22.345] (II) Loading extension XFree86-VidModeExtension
[    22.345] (II) Loading extension XFree86-DGA
[    22.362] (II) Loading extension DPMS
[    22.362] (II) Loading extension XVideo
[    22.362] (II) Loading extension XVideo-MotionCompensation
[    22.362] (II) Loading extension X-Resource
[    22.362] (II) LoadModule: "dbe"
[    22.362] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    22.375] (II) Module dbe: vendor="X.Org Foundation"
[    22.375]     compiled for 1.11.3, module version = 1.0.0
[    22.375]     Module class: X.Org Server Extension
[    22.375]     ABI class: X.Org Server Extension, version 6.0
[    22.375] (II) Loading extension DOUBLE-BUFFER
[    22.375] (II) LoadModule: "glx"
[    22.376] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    22.436] (II) Module glx: vendor="X.Org Foundation"
[    22.436]     compiled for 1.11.3, module version = 1.0.0
[    22.436]     ABI class: X.Org Server Extension, version 6.0
[    22.436] (==) AIGLX enabled
[    22.436] (II) Loading extension GLX
[    22.436] (II) LoadModule: "record"
[    22.436] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    22.447] (II) Module record: vendor="X.Org Foundation"
[    22.447]     compiled for 1.11.3, module version = 1.13.0
[    22.447]     Module class: X.Org Server Extension
[    22.447]     ABI class: X.Org Server Extension, version 6.0
[    22.447] (II) Loading extension RECORD
[    22.447] (II) LoadModule: "dri"
[    22.447] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    22.465] (II) Module dri: vendor="X.Org Foundation"
[    22.465]     compiled for 1.11.3, module version = 1.0.0
[    22.465]     ABI class: X.Org Server Extension, version 6.0
[    22.465] (II) Loading extension XFree86-DRI
[    22.465] (II) LoadModule: "dri2"
[    22.465] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    22.480] (II) Module dri2: vendor="X.Org Foundation"
[    22.480]     compiled for 1.11.3, module version = 1.2.0
[    22.480]     ABI class: X.Org Server Extension, version 6.0
[    22.480] (II) Loading extension DRI2
[    22.480] (II) LoadModule: "intel"
[    22.498] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    22.579] (II) Module intel: vendor="X.Org Foundation"
[    22.579]     compiled for 1.11.3, module version = 2.19.0
[    22.579]     Module class: X.Org Video Driver
[    22.579]     ABI class: X.Org Video Driver, version 11.0
[    22.579] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
    Ivybridge Server (GT2)
[    22.579] (++) using VT number 7

[    22.580] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    22.580] drmOpenDevice: node name is /dev/dri/card0
[    22.580] drmOpenDevice: open result is 9, (OK)
[    22.580] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    22.580] drmOpenDevice: node name is /dev/dri/card0
[    22.580] drmOpenDevice: open result is 9, (OK)
[    22.580] drmOpenByBusid: drmOpenMinor returns 9
[    22.580] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    22.580] (**) intel(0): Depth 24, (--) framebuffer bpp 32
[    22.580] (==) intel(0): RGB weight 888
[    22.580] (==) intel(0): Default visual is TrueColor
[    22.581] (II) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge Desktop (GT1)
[    22.581] (--) intel(0): Chipset: "Sandybridge Desktop (GT1)"
[    22.581] (**) intel(0): Relaxed fencing enabled
[    22.581] (**) intel(0): Wait on SwapBuffers? enabled
[    22.581] (**) intel(0): Triple buffering? enabled
[    22.581] (**) intel(0): Framebuffer tiled
[    22.581] (**) intel(0): Pixmaps tiled
[    22.581] (**) intel(0): 3D buffers tiled
[    22.581] (**) intel(0): SwapBuffers wait enabled
[    22.581] (==) intel(0): video overlay key set to 0x101fe
[    22.732] (II) intel(0): Output VGA1 using monitor section Monitor0
[    22.748] (II) intel(0): Output HDMI1 has no monitor section
[    22.796] (II) intel(0): Output DP1 has no monitor section
[    22.948] (II) intel(0): EDID for output VGA1
[    22.948] (II) intel(0): Manufacturer: HWP  Model: 2856  Serial#: 16843009
[    22.948] (II) intel(0): Year: 2010  Week: 28
[    22.948] (II) intel(0): EDID Version: 1.3
[    22.948] (II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    22.948] (II) intel(0): Sync:  Separate
[    22.948] (II) intel(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[    22.948] (II) intel(0): Gamma: 2.40
[    22.948] (II) intel(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    22.948] (II) intel(0): Default color space is primary color space
[    22.948] (II) intel(0): First detailed timing is preferred mode
[    22.948] (II) intel(0): redX: 0.640 redY: 0.335   greenX: 0.298 greenY: 0.608
[    22.948] (II) intel(0): blueX: 0.147 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
[    22.948] (II) intel(0): Supported established timings:
[    22.948] (II) intel(0): 720x400@70Hz
[    22.948] (II) intel(0): 640x480@60Hz
[    22.948] (II) intel(0): 800x600@60Hz
[    22.948] (II) intel(0): 1024x768@60Hz
[    22.948] (II) intel(0): Manufacturer's mask: 0
[    22.948] (II) intel(0): Supported standard timings:
[    22.948] (II) intel(0): #0: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    22.948] (II) intel(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    22.948] (II) intel(0): Supported detailed timing:
[    22.948] (II) intel(0): clock: 108.0 MHz   Image Size:  340 x 270 mm
[    22.948] (II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    22.948] (II) intel(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    22.948] (II) intel(0): Ranges: V min: 50 V max: 76 Hz, H min: 24 H max: 83 kHz, PixClock max 145 MHz
[    22.948] (II) intel(0): Monitor name: LE1711
[    22.948] (II) intel(0): Serial No: 3CQ028B7CZ
[    22.948] (II) intel(0): EDID (in hex):
[    22.948] (II) intel(0):     00ffffffffffff0022f0562801010101
[    22.948] (II) intel(0):     1c14010368221b8ceef7c5a3554c9b25
[    22.948] (II) intel(0):     125054a1080081408180010101010101
[    22.948] (II) intel(0):     010101010101302a009851002a403070
[    22.948] (II) intel(0):     1300540e1100001e000000fd00324c18
[    22.948] (II) intel(0):     530e000a202020202020000000fc004c
[    22.948] (II) intel(0):     45313731310a202020202020000000ff
[    22.948] (II) intel(0):     003343513032384237435a0a202000a2
[    22.948] (II) intel(0): EDID vendor "HWP", prod id 10326
[    22.948] (II) intel(0): Using EDID range info for horizontal sync
[    22.948] (II) intel(0): Using EDID range info for vertical refresh
[    22.948] (II) intel(0): Printing DDC gathered Modelines:
[    22.948] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    22.948] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    22.948] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    22.948] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    22.948] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    22.948] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    22.948] (II) intel(0): Printing probed modes for output VGA1
[    22.948] (II) intel(0): Modeline "1280p"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    22.948] (II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    22.948] (II) intel(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    22.948] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    22.948] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    22.948] (II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    22.948] (II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    22.964] (II) intel(0): EDID for output HDMI1
[    23.012] (II) intel(0): EDID for output DP1
[    23.012] (II) intel(0): Output VGA1 connected
[    23.012] (II) intel(0): Output HDMI1 disconnected
[    23.012] (II) intel(0): Output DP1 disconnected
[    23.012] (II) intel(0): Using user preference for initial modes
[    23.012] (II) intel(0): Output VGA1 using initial mode 1280p
[    23.012] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    23.012] (II) intel(0): Kernel page flipping support detected, enabling
[    23.012] (**) intel(0): Display dimensions: (340, 270) mm
[    23.012] (**) intel(0): DPI set to (95, 96)
[    23.012] (II) Loading sub module "fb"
[    23.012] (II) LoadModule: "fb"
[    23.051] (II) Loading /usr/lib/xorg/modules/libfb.so
[    23.091] (II) Module fb: vendor="X.Org Foundation"
[    23.091]     compiled for 1.11.3, module version = 1.0.0
[    23.091]     ABI class: X.Org ANSI C Emulation, version 0.4
[    23.091] (II) Loading sub module "dri2"
[    23.091] (II) LoadModule: "dri2"
[    23.091] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    23.091] (II) Module dri2: vendor="X.Org Foundation"
[    23.091]     compiled for 1.11.3, module version = 1.2.0
[    23.091]     ABI class: X.Org Server Extension, version 6.0
[    23.091] (==) Depth 24 pixmap format is 32 bpp
[    23.092] (II) intel(0): [DRI2] Setup complete
[    23.092] (II) intel(0): [DRI2]   DRI driver: i965
[    23.092] (II) intel(0): Allocated new frame buffer 1280x1024 stride 5120, tiled
[    23.165] (II) UXA(0): Driver registered support for the following operations:
[    23.165] (II)         solid
[    23.165] (II)         copy
[    23.165] (II)         composite (RENDER acceleration)
[    23.165] (II)         put_image
[    23.165] (II)         get_image
[    23.165] (==) intel(0): Backing store disabled
[    23.165] (==) intel(0): Silken mouse enabled
[    23.165] (II) intel(0): Initializing HW Cursor
[    23.165] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    23.166] (==) intel(0): DPMS enabled
[    23.166] (==) intel(0): Intel XvMC decoder enabled
[    23.166] (II) intel(0): Set up textured video
[    23.166] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    23.166] (II) intel(0): direct rendering: DRI2 Enabled
[    23.166] (WW) intel(0): Option "AccelMethod" is not used
[    23.166] (==) intel(0): hotplug detection: "enabled"
[    23.176] (--) RandR disabled
[    23.176] (II) Initializing built-in extension Generic Event Extension
[    23.176] (II) Initializing built-in extension SHAPE
[    23.176] (II) Initializing built-in extension MIT-SHM
[    23.176] (II) Initializing built-in extension XInputExtension
[    23.176] (II) Initializing built-in extension XTEST
[    23.176] (II) Initializing built-in extension BIG-REQUESTS
[    23.176] (II) Initializing built-in extension SYNC
[    23.176] (II) Initializing built-in extension XKEYBOARD
[    23.176] (II) Initializing built-in extension XC-MISC
[    23.176] (II) Initializing built-in extension SECURITY
[    23.176] (II) Initializing built-in extension XINERAMA
[    23.176] (II) Initializing built-in extension XFIXES
[    23.176] (II) Initializing built-in extension RENDER
[    23.176] (II) Initializing built-in extension RANDR
[    23.176] (II) Initializing built-in extension COMPOSITE
[    23.176] (II) Initializing built-in extension DAMAGE
[    23.313] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    23.313] (II) AIGLX: enabled GLX_INTEL_swap_event
[    23.313] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    23.313] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    23.314] (II) AIGLX: Loaded and initialized i965
[    23.314] (II) GLX: Initialized DRI2 GL provider for screen 0
[    23.314] (II) intel(0): Setting screen physical size to 338 x 270
[    23.569] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    23.610] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    23.610] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.610] (II) LoadModule: "evdev"
[    23.610] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.653] (II) Module evdev: vendor="X.Org Foundation"
[    23.653]     compiled for 1.11.3, module version = 2.7.0
[    23.653]     Module class: X.Org XInput Driver
[    23.653]     ABI class: X.Org XInput driver, version 16.0
[    23.653] (II) Using input driver 'evdev' for 'Power Button'
[    23.653] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.653] (**) Power Button: always reports core events
[    23.653] (**) evdev: Power Button: Device: "/dev/input/event1"
[    23.653] (--) evdev: Power Button: Vendor 0 Product 0x1
[    23.653] (--) evdev: Power Button: Found keys
[    23.653] (II) evdev: Power Button: Configuring as keyboard
[    23.653] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    23.653] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    23.653] (**) Option "xkb_rules" "evdev"
[    23.653] (**) Option "xkb_model" "pc105"
[    23.653] (**) Option "xkb_layout" "us"
[    23.654] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    23.654] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    23.654] (II) Using input driver 'evdev' for 'Video Bus'
[    23.654] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.654] (**) Video Bus: always reports core events
[    23.654] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    23.654] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    23.654] (--) evdev: Video Bus: Found keys
[    23.654] (II) evdev: Video Bus: Configuring as keyboard
[    23.654] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5/event5"
[    23.654] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    23.654] (**) Option "xkb_rules" "evdev"
[    23.654] (**) Option "xkb_model" "pc105"
[    23.654] (**) Option "xkb_layout" "us"
[    23.654] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    23.654] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.654] (II) Using input driver 'evdev' for 'Power Button'
[    23.654] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.654] (**) Power Button: always reports core events
[    23.654] (**) evdev: Power Button: Device: "/dev/input/event0"
[    23.654] (--) evdev: Power Button: Vendor 0 Product 0x1
[    23.654] (--) evdev: Power Button: Found keys
[    23.654] (II) evdev: Power Button: Configuring as keyboard
[    23.654] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    23.654] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    23.654] (**) Option "xkb_rules" "evdev"
[    23.654] (**) Option "xkb_model" "pc105"
[    23.654] (**) Option "xkb_layout" "us"
[    23.655] (II) config/udev: Adding input device HDA Intel PCH Line Out (/dev/input/event10)
[    23.655] (II) No input driver specified, ignoring this device.
[    23.655] (II) This device may have been added with another device file.
[    23.655] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event6)
[    23.655] (II) No input driver specified, ignoring this device.
[    23.655] (II) This device may have been added with another device file.
[    23.655] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event7)
[    23.655] (II) No input driver specified, ignoring this device.
[    23.655] (II) This device may have been added with another device file.
[    23.655] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event8)
[    23.655] (II) No input driver specified, ignoring this device.
[    23.655] (II) This device may have been added with another device file.
[    23.655] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event9)
[    23.655] (II) No input driver specified, ignoring this device.
[    23.655] (II) This device may have been added with another device file.
[    23.655] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:1028 (/dev/input/event4)
[    23.655] (**) Logitech Unifying Device. Wireless PID:1028: Applying InputClass "evdev pointer catchall"
[    23.655] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:1028'
[    23.655] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.656] (**) Logitech Unifying Device. Wireless PID:1028: always reports core events
[    23.656] (**) evdev: Logitech Unifying Device. Wireless PID:1028: Device: "/dev/input/event4"
[    23.656] (--) evdev: Logitech Unifying Device. Wireless PID:1028: Vendor 0x46d Product 0xc52b
[    23.656] (--) evdev: Logitech Unifying Device. Wireless PID:1028: Found 20 mouse buttons
[    23.656] (--) evdev: Logitech Unifying Device. Wireless PID:1028: Found scroll wheel(s)
[    23.656] (--) evdev: Logitech Unifying Device. Wireless PID:1028: Found relative axes
[    23.656] (--) evdev: Logitech Unifying Device. Wireless PID:1028: Found x and y relative axes
[    23.656] (II) evdev: Logitech Unifying Device. Wireless PID:1028: Configuring as mouse
[    23.656] (II) evdev: Logitech Unifying Device. Wireless PID:1028: Adding scrollwheel support
[    23.656] (**) evdev: Logitech Unifying Device. Wireless PID:1028: YAxisMapping: buttons 4 and 5
[    23.656] (**) evdev: Logitech Unifying Device. Wireless PID:1028: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    23.656] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.2/0003:046D:C52B.0003/input/input4/event4"
[    23.656] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:1028" (type: MOUSE, id 9)
[    23.656] (II) evdev: Logitech Unifying Device. Wireless PID:1028: initialized for relative axes.
[    23.656] (**) Logitech Unifying Device. Wireless PID:1028: (accel) keeping acceleration scheme 1
[    23.656] (**) Logitech Unifying Device. Wireless PID:1028: (accel) acceleration profile 0
[    23.656] (**) Logitech Unifying Device. Wireless PID:1028: (accel) acceleration factor: 2.000
[    23.656] (**) Logitech Unifying Device. Wireless PID:1028: (accel) acceleration threshold: 4
[    23.656] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:1028 (/dev/input/mouse0)
[    23.656] (II) No input driver specified, ignoring this device.
[    23.656] (II) This device may have been added with another device file.
[    23.656] (II) config/udev: Adding input device   USB Keyboard (/dev/input/event2)
[    23.656] (**)   USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    23.656] (II) Using input driver 'evdev' for '  USB Keyboard'
[    23.656] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.656] (**)   USB Keyboard: always reports core events
[    23.656] (**) evdev:   USB Keyboard: Device: "/dev/input/event2"
[    23.656] (--) evdev:   USB Keyboard: Vendor 0x4d9 Product 0x1702
[    23.656] (--) evdev:   USB Keyboard: Found keys
[    23.656] (II) evdev:   USB Keyboard: Configuring as keyboard
[    23.656] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input2/event2"
[    23.656] (II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD, id 10)
[    23.656] (**) Option "xkb_rules" "evdev"
[    23.656] (**) Option "xkb_model" "pc105"
[    23.656] (**) Option "xkb_layout" "us"
[    23.657] (II) config/udev: Adding input device   USB Keyboard (/dev/input/event3)
[    23.657] (**)   USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    23.657] (II) Using input driver 'evdev' for '  USB Keyboard'
[    23.657] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.657] (**)   USB Keyboard: always reports core events
[    23.657] (**) evdev:   USB Keyboard: Device: "/dev/input/event3"
[    23.657] (--) evdev:   USB Keyboard: Vendor 0x4d9 Product 0x1702
[    23.657] (--) evdev:   USB Keyboard: Found keys
[    23.657] (II) evdev:   USB Keyboard: Configuring as keyboard
[    23.657] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/input/input3/event3"
[    23.657] (II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD, id 11)
[    23.657] (**) Option "xkb_rules" "evdev"
[    23.657] (**) Option "xkb_model" "pc105"
[    23.657] (**) Option "xkb_layout" "us"
[    29.360] (II) intel(0): EDID vendor "HWP", prod id 10326
[    29.360] (II) intel(0): Using hsync ranges from config file
[    29.360] (II) intel(0): Using vrefresh ranges from config file
[    29.360] (II) intel(0): Printing DDC gathered Modelines:
[    29.360] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    29.360] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    29.360] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    29.360] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    29.360] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    29.360] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    41.308] (II) intel(0): EDID vendor "HWP", prod id 10326
[    41.308] (II) intel(0): Using hsync ranges from config file
[    41.308] (II) intel(0): Using vrefresh ranges from config file
[    41.308] (II) intel(0): Printing DDC gathered Modelines:
[    41.308] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    41.308] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    41.308] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    41.308] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    41.308] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    41.308] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    42.168] (II) intel(0): EDID vendor "HWP", prod id 10326
[    42.168] (II) intel(0): Using hsync ranges from config file
[    42.168] (II) intel(0): Using vrefresh ranges from config file
[    42.168] (II) intel(0): Printing DDC gathered Modelines:
[    42.168] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    42.168] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    42.168] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    42.168] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    42.168] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    42.168] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    52.060] (II) intel(0): EDID vendor "HWP", prod id 10326
[    52.060] (II) intel(0): Using hsync ranges from config file
[    52.060] (II) intel(0): Using vrefresh ranges from config file
[    52.060] (II) intel(0): Printing DDC gathered Modelines:
[    52.060] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    52.060] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    52.060] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    52.060] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    52.060] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    52.060] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    52.276] (II) intel(0): EDID vendor "HWP", prod id 10326
[    52.276] (II) intel(0): Using hsync ranges from config file
[    52.276] (II) intel(0): Using vrefresh ranges from config file
[    52.276] (II) intel(0): Printing DDC gathered Modelines:
[    52.276] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    52.276] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    52.276] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    52.276] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    52.276] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    52.276] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    64.120] (II) intel(0): EDID vendor "HWP", prod id 10326
[    64.120] (II) intel(0): Using hsync ranges from config file
[    64.120] (II) intel(0): Using vrefresh ranges from config file
[    64.120] (II) intel(0): Printing DDC gathered Modelines:
[    64.120] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    64.120] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    64.120] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    64.120] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    64.120] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    64.120] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    66.766] (II) AIGLX: Suspending AIGLX clients for VT switch
[    71.182] (II) Open ACPI successful (/var/run/acpid.socket)
[    71.182] (II) AIGLX: Resuming AIGLX clients after VT switch
[    71.182] (EE) intel(0): Couldn't create pixmap for fbcon
[    71.348] (II) intel(0): EDID vendor "HWP", prod id 10326
[    71.348] (II) intel(0): Using hsync ranges from config file
[    71.348] (II) intel(0): Using vrefresh ranges from config file
[    71.348] (II) intel(0): Printing DDC gathered Modelines:
[    71.348] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    71.348] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    71.348] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    71.348] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    71.348] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    71.348] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   109.996] (II) AIGLX: Suspending AIGLX clients for VT switch
[   121.542] (II) Open ACPI successful (/var/run/acpid.socket)
[   121.542] (II) AIGLX: Resuming AIGLX clients after VT switch
[   121.542] (EE) intel(0): Couldn't create pixmap for fbcon
[   121.708] (II) intel(0): EDID vendor "HWP", prod id 10326
[   121.708] (II) intel(0): Using hsync ranges from config file
[   121.708] (II) intel(0): Using vrefresh ranges from config file
[   121.708] (II) intel(0): Printing DDC gathered Modelines:
[   121.708] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   121.708] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   121.708] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   121.708] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   121.708] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   121.708] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   124.056] (II) AIGLX: Suspending AIGLX clients for VT switch
[   143.885] (II) Open ACPI successful (/var/run/acpid.socket)
[   143.885] (II) AIGLX: Resuming AIGLX clients after VT switch
[   143.886] (EE) intel(0): Couldn't create pixmap for fbcon
[   144.052] (II) intel(0): EDID vendor "HWP", prod id 10326
[   144.052] (II) intel(0): Using hsync ranges from config file
[   144.052] (II) intel(0): Using vrefresh ranges from config file
[   144.052] (II) intel(0): Printing DDC gathered Modelines:
[   144.052] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   144.052] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   144.052] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   144.052] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   144.052] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   144.052] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   145.680] (II) AIGLX: Suspending AIGLX clients for VT switch
[   235.917] (II) Open ACPI successful (/var/run/acpid.socket)
[   235.917] (II) AIGLX: Resuming AIGLX clients after VT switch
[   235.917] (EE) intel(0): Couldn't create pixmap for fbcon
[   236.092] (II) intel(0): EDID vendor "HWP", prod id 10326
[   236.092] (II) intel(0): Using hsync ranges from config file
[   236.092] (II) intel(0): Using vrefresh ranges from config file
[   236.092] (II) intel(0): Printing DDC gathered Modelines:
[   236.092] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   236.092] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   236.092] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   236.092] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   236.092] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   236.092] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   237.204] (II) AIGLX: Suspending AIGLX clients for VT switch
[   245.499] (II) evdev:   USB Keyboard: Close
[   245.499] (II) UnloadModule: "evdev"
[   245.499] (II) Unloading evdev
[   245.499] (II) evdev:   USB Keyboard: Close
[   245.499] (II) UnloadModule: "evdev"
[   245.499] (II) Unloading evdev
[   245.499] (II) evdev: Logitech Unifying Device. Wireless PID:1028: Close
[   245.499] (II) UnloadModule: "evdev"
[   245.499] (II) Unloading evdev
[   245.499] (II) evdev: Power Button: Close
[   245.499] (II) UnloadModule: "evdev"
[   245.499] (II) Unloading evdev
[   245.499] (II) evdev: Video Bus: Close
[   245.499] (II) UnloadModule: "evdev"
[   245.499] (II) Unloading evdev
[   245.499] (II) evdev: Power Button: Close
[   245.499] (II) UnloadModule: "evdev"
[   245.499] (II) Unloading evdev
[   245.506]  ddxSigGiveUp: Closing log
[   245.506] Server terminated successfully (0). Closing log file.
```

---

### Post by Yellow Pasque on 2015-02-10
I don't see any clues other than "Couldn't create pixmap for fbcon" error, which doesn't look serious from googling. It looks like the Xserver just closes without giving a reason. :/

---

