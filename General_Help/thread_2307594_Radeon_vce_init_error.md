---
title: "Radeon vce init error"
date: 2015-12-26
forum: General Help
---

### Post by Afonso_Muralha on 2015-12-26
[COLOR=#111111][FONT=Ubuntu]Hello I finally decided to move to linux, and I chose the latest version of Ubuntu Gnome, after getting all of it installed the computer is working great, but the boot time (to the login screen) almost reaches 3min.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I tried to disable the splash screen on the grub config file so I can see what was happening, and it gets stuck on a Radeon VCE init error.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I'm using a thoshiba laptop with a core i3 and AMD Radeon GPU[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Any help would be much appreciated[/FONT][/COLOR]

---

### Post by DuckHook on 2015-12-26
Hi Alfonso and welcome to Ubuntu and the forums,

This seems to be a known issue with Linux and newer AMD cards. To get further info, please open a terminal, use the following commands, and post back results to this thread.```
sudo lspci -vnk | grep -iA20 vga
``````
dmesg | egrep -i 'vce|error'
``````
uname -a
```Linux is case-sensitive and these commands are rather obscure, so copy and paste into terminal rather than retype. Also, you can copy and paste results back to this thread but please wrap them in *CODE* tags to allow for proper formatting, especially as the output may be rather lengthy.

---

### Post by Afonso_Muralha on 2015-12-27
Thank you for the response, here are the results:

For [COLOR=#000000][FONT=Ubuntu Mono]sudo lspci -vnk | grep -iA20 vga:

[/FONT][/COLOR]```
00:02.0 0300: 8086:0a16 (rev 0b) (prog-if 00 [VGA controller])    Subsystem: 1179:f920
    Flags: bus master, fast devsel, latency 0, IRQ 48
    Memory at c2000000 (64-bit, non-prefetchable) [size=4M]
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 6000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915


00:03.0 0403: 8086:0a0c (rev 0b)
    Subsystem: 1179:f920
    Flags: bus master, fast devsel, latency 0, IRQ 52
    Memory at c2810000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Kernel driver in use: snd_hda_intel

```[COLOR=#000000][FONT=Ubuntu Mono]





For the [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]dmesg | egrep -i 'vce|error':

[/FONT][/COLOR]```
[   10.857396] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro[   12.277534] iwlwifi 0000:07:00.0: Direct firmware load for iwlwifi-3160-15.ucode failed with error -2
[   12.283250] iwlwifi 0000:07:00.0: Direct firmware load for iwlwifi-3160-14.ucode failed with error -2

```[COLOR=#000000][FONT=Ubuntu Mono]





And for [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]uname -a:

(please ignore my computer name :P )

[/FONT][/COLOR]```
Linux afonso-toshibapowered-noobpwner 4.2.0-22-generic #27-Ubuntu SMP Thu Dec 17 22:57:08 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```[COLOR=#000000][FONT=Ubuntu Mono]




I had searched a little about this error but still haven't found a way to fix it. It's a bit anoying have a slow boot time and some screen tearing when whatchig hd movies through HDMI.

I also changeg the gpu drivers for one of the proprietary ones (on additional drivers > Advanced Micro Devices Inc.[AMD/ATI]:Jet pro [Radeon R5 M230]). I also read somewhere that I should install bumblebee (whatever that is).

Thank you for your time.

[/FONT][/COLOR]

---

### Post by Afonso_Muralha on 2015-12-27
Ok little update:

I tried to run dmesg (I assume that is for the boot log or something) and it gave me this:  (sorry for the long post)

```
[    0.000000] Initializing cgroup subsys cpuset[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 4.2.0-22-generic (buildd@lcy01-22) (gcc version 5.2.1 20151010 (Ubuntu 5.2.1-22ubuntu2) ) #27-Ubuntu SMP Thu Dec 17 22:57:08 UTC 2015 (Ubuntu 4.2.0-22.27-generic 4.2.6)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-22-generic.efi.signed root=UUID=86fc55af-6d89-4b2f-b227-1311efb5c36d ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] x86/fpu: xstate_offset[2]: 0240, xstate_sizes[2]: 0100
[    0.000000] x86/fpu: Supporting XSAVE feature 0x01: 'x87 floating point registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x02: 'SSE registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x04: 'AVX registers'
[    0.000000] x86/fpu: Enabled xstate features 0x7, context size is 0x340 bytes, using 'standard' format.
[    0.000000] x86/fpu: Using 'eager' FPU context switches.
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x0000000000057fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000058000-0x0000000000058fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000059000-0x0000000000085fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000086000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x0000000094db9fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000094dba000-0x00000000956b9fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000956ba000-0x000000009c39efff] usable
[    0.000000] BIOS-e820: [mem 0x000000009c39f000-0x000000009c59efff] type 20
[    0.000000] BIOS-e820: [mem 0x000000009c59f000-0x000000009cd8efff] reserved
[    0.000000] BIOS-e820: [mem 0x000000009cd8f000-0x000000009ce8efff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000009ce8f000-0x000000009cefefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000009ceff000-0x000000009cefffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000feb00000-0x00000000feb03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffa00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000015f5fffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] efi: EFI v2.40 by INSYDE Corp.
[    0.000000] efi:  SMBIOS=0x9c613000  ESRT=0x9c71e118  ACPI 2.0=0x9cefe014 
[    0.000000] esrt: Reserving ESRT space from 0x000000009c71e118 to 0x000000009c71e150.
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: TOSHIBA SATELLITE L50-B/Type2 - Board Product Name1, BIOS 2.00 12/11/2014
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x15f600 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-E7FFF write-protect
[    0.000000]   E8000-EFFFF write-combining
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask 7E00000000 write-back
[    0.000000]   1 base 009CF00000 mask 7FFFF00000 uncachable
[    0.000000]   2 base 009D000000 mask 7FFF000000 uncachable
[    0.000000]   3 base 009E000000 mask 7FFE000000 uncachable
[    0.000000]   4 base 00A0000000 mask 7FE0000000 uncachable
[    0.000000]   5 base 00C0000000 mask 7FC0000000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 8GB, type WB
[    0.000000] reg 1, base: 2511MB, range: 1MB, type UC
[    0.000000] reg 2, base: 2512MB, range: 16MB, type UC
[    0.000000] reg 3, base: 2528MB, range: 32MB, type UC
[    0.000000] reg 4, base: 2560MB, range: 512MB, type UC
[    0.000000] reg 5, base: 3GB, range: 1GB, type UC
[    0.000000] total RAM covered: 6607M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 64M 	num_reg: 6  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 512MB, type WB
[    0.000000] reg 2, base: 2511MB, range: 1MB, type UC
[    0.000000] reg 3, base: 2512MB, range: 16MB, type UC
[    0.000000] reg 4, base: 2528MB, range: 32MB, type UC
[    0.000000] reg 5, base: 4GB, range: 4GB, type WB
[    0.000000] e820: update [mem 0x9cf00000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0x9cf00 max_arch_pfn = 0x400000000
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000080000] 80000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x02ff0000, 0x02ff0fff] PGTABLE
[    0.000000] BRK [0x02ff1000, 0x02ff1fff] PGTABLE
[    0.000000] BRK [0x02ff2000, 0x02ff2fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x15f400000-0x15f5fffff]
[    0.000000]  [mem 0x15f400000-0x15f5fffff] page 2M
[    0.000000] BRK [0x02ff3000, 0x02ff3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x140000000-0x15f3fffff]
[    0.000000]  [mem 0x140000000-0x15f3fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x120000000-0x13fffffff]
[    0.000000]  [mem 0x120000000-0x13fffffff] page 1G
[    0.000000] init_memory_mapping: [mem 0x00100000-0x94db9fff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0x7fffffff] page 1G
[    0.000000]  [mem 0x80000000-0x94bfffff] page 2M
[    0.000000]  [mem 0x94c00000-0x94db9fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x956ba000-0x9c39efff]
[    0.000000]  [mem 0x956ba000-0x957fffff] page 4k
[    0.000000]  [mem 0x95800000-0x9c1fffff] page 2M
[    0.000000]  [mem 0x9c200000-0x9c39efff] page 4k
[    0.000000] BRK [0x02ff4000, 0x02ff4fff] PGTABLE
[    0.000000] BRK [0x02ff5000, 0x02ff5fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x9ceff000-0x9cefffff]
[    0.000000]  [mem 0x9ceff000-0x9cefffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x11fffffff]
[    0.000000]  [mem 0x100000000-0x11fffffff] page 1G
[    0.000000] RAMDISK: [mem 0x3477c000-0x363b5fff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x000000009CEFE014 000024 (v02 TOSQCI)
[    0.000000] ACPI: XSDT 0x000000009CECA188 0000D4 (v01 TOSQCI TOSQCI00 00000001      01000013)
[    0.000000] ACPI: FACP 0x000000009CEF6000 00010C (v05 TOSQCI TOSQCI00 00000001 ACPI 00040000)
[    0.000000] ACPI: DSDT 0x000000009CEDA000 015AE4 (v02 TOSQCI TOSQCI00 00000000 ACPI 00040000)
[    0.000000] ACPI: FACS 0x000000009CE89000 000040
[    0.000000] ACPI: UEFI 0x000000009CEFD000 000236 (v01 TOSQCI TOSQCI00 00000001 ACPI 00040000)
[    0.000000] ACPI: UEFI 0x000000009CEFC000 000042 (v01 TOSQCI TOSQCI00 00000000 ACPI 00040000)
[    0.000000] ACPI: MSDM 0x000000009CEFB000 000055 (v03 TOSQCI TOSQCI00 00000001 ACPI 00040000)
[    0.000000] ACPI: ASF! 0x000000009CEFA000 0000A5 (v32 TOSQCI TOSQCI00 00000001 ACPI 00040000)
[    0.000000] ACPI: ASPT 0x000000009CEF9000 000034 (v07 TOSQCI TOSQCI00 00000001 ACPI 00040000)
[    0.000000] ACPI: BOOT 0x000000009CEF8000 000028 (v01 TOSQCI TOSQCI00 00000001 ACPI 00040000)
[    0.000000] ACPI: DBGP 0x000000009CEF7000 000034 (v01 TOSQCI TOSQCI00 00000001 ACPI 00040000)
[    0.000000] ACPI: HPET 0x000000009CEF5000 000038 (v01 TOSQCI TOSQCI00 00000001 ACPI 00040000)
[    0.000000] ACPI: LPIT 0x000000009CEF4000 000094 (v01 TOSQCI TOSQCI00 00000001 ACPI 00040000)
[    0.000000] ACPI: APIC 0x000000009CEF3000 00008C (v03 TOSQCI TOSQCI00 00000001 ACPI 00040000)
[    0.000000] ACPI: MCFG 0x000000009CEF2000 00003C (v01 TOSQCI TOSQCI00 00000001 ACPI 00040000)
[    0.000000] ACPI: SLIC 0x000000009CEF1000 000176 (v01 TOSQCI TOSQCI00 00000001 ACPI 00040000)
[    0.000000] ACPI: WDAT 0x000000009CEF0000 000224 (v01 TOSQCI TOSQCI00 00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 0x000000009CED7000 002E26 (v01 INSYDE HSW-LPT  00001000 ACPI 00040000)
[    0.000000] ACPI: SSDT 0x000000009CED6000 0004BF (v01 INSYDE HSW-LPT  00003000 ACPI 00040000)
[    0.000000] ACPI: SSDT 0x000000009CED5000 000B74 (v01 INSYDE HSW-LPT  00003000 ACPI 00040000)
[    0.000000] ACPI: SSDT 0x000000009CECF000 005C4C (v01 INSYDE HSW-LPT  00003000 ACPI 00040000)
[    0.000000] ACPI: SSDT 0x000000009CECD000 001B4B (v01 INSYDE HSW-LPT  00001000 ACPI 00040000)
[    0.000000] ACPI: CSRT 0x000000009CECC000 0000C4 (v01 TOSQCI TOSQCI00 00000001 ACPI 00040000)
[    0.000000] ACPI: FPDT 0x000000009CECB000 000044 (v01 TOSQCI TOSQCI00 00000002 ACPI 00040000)
[    0.000000] ACPI: BGRT 0x000000009CEC9000 000038 (v01 TOSQCI TOSQCI00 00000001 ACPI 00040000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000015f5fffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x15f5f8000-0x15f5fcfff]
[    0.000000]  [ffffea0000000000-ffffea00057fffff] PMD -> [ffff88015ac00000-ffff88015ebfffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.000000]   Normal   [mem 0x0000000100000000-0x000000015f5fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x0000000000057fff]
[    0.000000]   node   0: [mem 0x0000000000059000-0x0000000000085fff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x0000000094db9fff]
[    0.000000]   node   0: [mem 0x00000000956ba000-0x000000009c39efff]
[    0.000000]   node   0: [mem 0x000000009ceff000-0x000000009cefffff]
[    0.000000]   node   0: [mem 0x0000000100000000-0x000000015f5fffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000015f5fffff]
[    0.000000] On node 0 totalpages: 1028132
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 23 pages reserved
[    0.000000]   DMA zone: 3972 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 9899 pages used for memmap
[    0.000000]   DMA32 zone: 633504 pages, LIFO batch:31
[    0.000000]   Normal zone: 6104 pages used for memmap
[    0.000000]   Normal zone: 390656 pages, LIFO batch:31
[    0.000000] Reserving Intel graphics stolen memory at 0x9da00000-0x9f9fffff
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-39
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x00058000-0x00058fff]
[    0.000000] PM: Registered nosave memory: [mem 0x00086000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x94dba000-0x956b9fff]
[    0.000000] PM: Registered nosave memory: [mem 0x9c39f000-0x9c59efff]
[    0.000000] PM: Registered nosave memory: [mem 0x9c59f000-0x9cd8efff]
[    0.000000] PM: Registered nosave memory: [mem 0x9cd8f000-0x9ce8efff]
[    0.000000] PM: Registered nosave memory: [mem 0x9ce8f000-0x9cefefff]
[    0.000000] PM: Registered nosave memory: [mem 0x9cf00000-0x9d9fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x9da00000-0x9f9fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x9fa00000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfeafffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfeb00000-0xfeb03fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfeb04000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed19fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xff9fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffa00000-0xffffffff]
[    0.000000] e820: [mem 0x9fa00000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 33 pages/cpu @ffff88015f200000 s96728 r8192 d30248 u262144
[    0.000000] pcpu-alloc: s96728 r8192 d30248 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1012042
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-22-generic.efi.signed root=UUID=86fc55af-6d89-4b2f-b227-1311efb5c36d ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3864048K/4112528K available (8148K kernel code, 1237K rwdata, 3800K rodata, 1460K init, 1292K bss, 248480K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	Build-time adjustment of leaf fanout to 64.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=8
[    0.000000] NR_IRQS:16640 nr_irqs:760 16
[    0.000000] 	Offload RCU callbacks from all CPUs
[    0.000000] 	Offload RCU callbacks from CPUs: 0-7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 1695.993 MHz processor
[    0.000041] Calibrating delay loop (skipped), value calculated using timer frequency.. 3391.98 BogoMIPS (lpj=6783972)
[    0.000045] pid_max: default: 32768 minimum: 301
[    0.000052] ACPI: Core revision 20150619
[    0.027536] ACPI: All ACPI Tables successfully acquired
[    0.029456] Security Framework initialized
[    0.029473] AppArmor: AppArmor initialized
[    0.029474] Yama: becoming mindful.
[    0.029885] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.030963] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.031439] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.031449] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.031701] Initializing cgroup subsys blkio
[    0.031705] Initializing cgroup subsys memory
[    0.031714] Initializing cgroup subsys devices
[    0.031716] Initializing cgroup subsys freezer
[    0.031719] Initializing cgroup subsys net_cls
[    0.031722] Initializing cgroup subsys perf_event
[    0.031724] Initializing cgroup subsys net_prio
[    0.031727] Initializing cgroup subsys hugetlb
[    0.031756] CPU: Physical Processor ID: 0
[    0.031757] CPU: Processor Core ID: 0
[    0.031762] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.031764] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.032982] mce: CPU supports 7 MCE banks
[    0.032999] CPU0: Thermal monitoring enabled (TM1)
[    0.033010] process: using mwait in idle threads
[    0.033014] Last level iTLB entries: 4KB 1024, 2MB 1024, 4MB 1024
[    0.033015] Last level dTLB entries: 4KB 1024, 2MB 1024, 4MB 1024, 1GB 4
[    0.033464] Freeing SMP alternatives memory: 28K (ffffffff81ea4000 - ffffffff81eab000)
[    0.037072] Ignoring BGRT: invalid status 0 (expected 1)
[    0.039747] ftrace: allocating 30910 entries in 121 pages
[    0.057690] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.097397] TSC deadline timer enabled
[    0.097400] smpboot: CPU0: Intel(R) Core(TM) i3-4005U CPU @ 1.70GHz (fam: 06, model: 45, stepping: 01)
[    0.097437] Performance Events: PEBS fmt2+, 16-deep LBR, Haswell events, full-width counters, Intel PMU driver.
[    0.097464] ... version:                3
[    0.097466] ... bit width:              48
[    0.097467] ... generic registers:      4
[    0.097468] ... value mask:             0000ffffffffffff
[    0.097469] ... max period:             0000ffffffffffff
[    0.097470] ... fixed-purpose events:   3
[    0.097472] ... event mask:             000000070000000f
[    0.098554] x86: Booting SMP configuration:
[    0.098556] .... node  #0, CPUs:      #1
[    0.103245] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.103357]  #2 #3
[    0.112503] x86: Booted up 1 node, 4 CPUs
[    0.112507] smpboot: Total of 4 processors activated (13567.94 BogoMIPS)
[    0.117599] devtmpfs: initialized
[    0.120212] evm: security.selinux
[    0.120214] evm: security.SMACK64
[    0.120215] evm: security.SMACK64EXEC
[    0.120216] evm: security.SMACK64TRANSMUTE
[    0.120217] evm: security.SMACK64MMAP
[    0.120218] evm: security.ima
[    0.120219] evm: security.capability
[    0.120282] PM: Registering ACPI NVS region [mem 0x94dba000-0x956b9fff] (9437184 bytes)
[    0.120425] PM: Registering ACPI NVS region [mem 0x9cd8f000-0x9ce8efff] (1048576 bytes)
[    0.120535] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.120643] pinctrl core: initialized pinctrl subsystem
[    0.120768] RTC time: 10:12:48, date: 12/27/15
[    0.120909] NET: Registered protocol family 16
[    0.125418] cpuidle: using governor ladder
[    0.129433] cpuidle: using governor menu
[    0.129467] Simple Boot Flag at 0x44 set to 0x1
[    0.129529] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.129531] ACPI: bus type PCI registered
[    0.129533] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.129623] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.129625] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.129639] PCI: Using configuration type 1 for base access
[    0.129888] perf_event_intel: PMU erratum BJ122, BV98, HSD29 worked around, HT is on
[    0.133861] ACPI: Added _OSI(Module Device)
[    0.133863] ACPI: Added _OSI(Processor Device)
[    0.133865] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.133867] ACPI: Added _OSI(Processor Aggregator Device)
[    0.140920] ACPI: Executed 17 blocks of module-level executable AML code
[    0.147824] ACPI: Dynamic OEM Table Load:
[    0.147840] ACPI: SSDT 0xFFFF880159FCB400 0003D3 (v01 PmRef  Cpu0Cst  00003001 INTL 20130117)
[    0.148983] ACPI: Dynamic OEM Table Load:
[    0.148996] ACPI: SSDT 0xFFFF880159F92800 0005AA (v01 PmRef  ApIst    00003000 INTL 20130117)
[    0.150203] ACPI: Dynamic OEM Table Load:
[    0.150214] ACPI: SSDT 0xFFFF880159838C00 000119 (v01 PmRef  ApCst    00003000 INTL 20130117)
[    0.152355] ACPI : EC: EC started
[    0.152637] ACPI: Interpreter enabled
[    0.152649] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20150619/hwxface-580)
[    0.152659] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150619/hwxface-580)
[    0.152689] ACPI: (supports S0 S3 S4 S5)
[    0.152690] ACPI: Using IOAPIC for interrupt routing
[    0.152729] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.187150] ACPI: Power Resource [PC05] (on)
[    0.189715] acpi ABCD0000:00: ACPI dock station (docks/bays count: 1)
[    0.192444] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.192451] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    2.628022] acpi PNP0A08:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability]
[    2.628025] acpi PNP0A08:00: FADT indicates ASPM is unsupported, using BIOS configuration
[    2.628901] PCI host bridge to bus 0000:00
[    2.628905] pci_bus 0000:00: root bus resource [bus 00-fe]
[    2.628907] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    2.628910] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    2.628912] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    2.628914] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff window]
[    2.628916] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff window]
[    2.628918] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff window]
[    2.628920] pci_bus 0000:00: root bus resource [mem 0x000cc000-0x000cffff window]
[    2.628922] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff window]
[    2.628924] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff window]
[    2.628926] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff window]
[    2.628927] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff window]
[    2.628929] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff window]
[    2.628931] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff window]
[    2.628933] pci_bus 0000:00: root bus resource [mem 0x000e8000-0x000ebfff window]
[    2.628935] pci_bus 0000:00: root bus resource [mem 0x000ec000-0x000effff window]
[    2.628937] pci_bus 0000:00: root bus resource [mem 0x9fa00000-0xfeafffff window]
[    2.628947] pci 0000:00:00.0: [8086:0a04] type 00 class 0x060000
[    2.629279] pci 0000:00:02.0: [8086:0a16] type 00 class 0x030000
[    2.629298] pci 0000:00:02.0: reg 0x10: [mem 0xc2000000-0xc23fffff 64bit]
[    2.629307] pci 0000:00:02.0: reg 0x18: [mem 0xb0000000-0xbfffffff 64bit pref]
[    2.629313] pci 0000:00:02.0: reg 0x20: [io  0x6000-0x603f]
[    2.629633] pci 0000:00:03.0: [8086:0a0c] type 00 class 0x040300
[    2.629650] pci 0000:00:03.0: reg 0x10: [mem 0xc2810000-0xc2813fff 64bit]
[    2.629993] pci 0000:00:14.0: [8086:9c31] type 00 class 0x0c0330
[    2.630021] pci 0000:00:14.0: reg 0x10: [mem 0xc2800000-0xc280ffff 64bit]
[    2.630074] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    2.630345] pci 0000:00:14.0: System wakeup disabled by ACPI
[    2.630393] pci 0000:00:16.0: [8086:9c3a] type 00 class 0x078000
[    2.630425] pci 0000:00:16.0: reg 0x10: [mem 0xc281b000-0xc281b01f 64bit]
[    2.630486] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    2.630818] pci 0000:00:1b.0: [8086:9c20] type 00 class 0x040300
[    2.630846] pci 0000:00:1b.0: reg 0x10: [mem 0xc2814000-0xc2817fff 64bit]
[    2.630899] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    2.631170] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    2.631215] pci 0000:00:1c.0: [8086:9c10] type 01 class 0x060400
[    2.631281] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    2.631596] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    2.631643] pci 0000:00:1c.2: [8086:9c14] type 01 class 0x060400
[    2.631710] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    2.632053] pci 0000:00:1c.3: [8086:9c16] type 01 class 0x060400
[    2.632119] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    2.632430] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    2.632476] pci 0000:00:1c.4: [8086:9c18] type 01 class 0x060400
[    2.632542] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    2.632852] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    2.632903] pci 0000:00:1d.0: [8086:9c26] type 00 class 0x0c0320
[    2.633152] pci 0000:00:1d.0: reg 0x10: [mem 0xc2819000-0xc28193ff]
[    2.634514] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    2.634792] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    2.634842] pci 0000:00:1f.0: [8086:9c45] type 00 class 0x060100
[    2.635253] pci 0000:00:1f.2: [8086:9c03] type 00 class 0x010601
[    2.635276] pci 0000:00:1f.2: reg 0x10: [io  0x6088-0x608f]
[    2.635283] pci 0000:00:1f.2: reg 0x14: [io  0x6094-0x6097]
[    2.635291] pci 0000:00:1f.2: reg 0x18: [io  0x6080-0x6087]
[    2.635299] pci 0000:00:1f.2: reg 0x1c: [io  0x6090-0x6093]
[    2.635307] pci 0000:00:1f.2: reg 0x20: [io  0x6060-0x607f]
[    2.635316] pci 0000:00:1f.2: reg 0x24: [mem 0xc2818000-0xc28187ff]
[    2.635343] pci 0000:00:1f.2: PME# supported from D3hot
[    2.635651] pci 0000:00:1f.3: [8086:9c22] type 00 class 0x0c0500
[    2.635669] pci 0000:00:1f.3: reg 0x10: [mem 0xc281a000-0xc281a0ff 64bit]
[    2.635690] pci 0000:00:1f.3: reg 0x20: [io  0x6040-0x605f]
[    2.636126] pci 0000:01:00.0: [10ec:5229] type 00 class 0xff0000
[    2.636203] pci 0000:01:00.0: reg 0x10: [mem 0xc1000000-0xc1000fff]
[    2.636335] pci 0000:01:00.0: supports D1 D2
[    2.636337] pci 0000:01:00.0: PME# supported from D1 D2 D3hot
[    2.636377] pci 0000:01:00.0: System wakeup disabled by ACPI
[    2.643534] pci 0000:00:1c.0: PCI bridge to [bus 01-06]
[    2.643539] pci 0000:00:1c.0:   bridge window [io  0x5000-0x5fff]
[    2.643542] pci 0000:00:1c.0:   bridge window [mem 0xc1000000-0xc1ffffff]
[    2.643548] pci 0000:00:1c.0:   bridge window [mem 0xc0000000-0xc0ffffff 64bit pref]
[    2.643811] pci 0000:07:00.0: [8086:08b3] type 00 class 0x028000
[    2.643928] pci 0000:07:00.0: reg 0x10: [mem 0xc2700000-0xc2701fff 64bit]
[    2.644275] pci 0000:07:00.0: PME# supported from D0 D3hot D3cold
[    2.651650] pci 0000:00:1c.2: PCI bridge to [bus 07]
[    2.651656] pci 0000:00:1c.2:   bridge window [mem 0xc2700000-0xc27fffff]
[    2.651729] pci 0000:08:00.0: [10ec:8168] type 00 class 0x020000
[    2.651771] pci 0000:08:00.0: reg 0x10: [io  0x4000-0x40ff]
[    2.651802] pci 0000:08:00.0: reg 0x18: [mem 0xc2600000-0xc2600fff 64bit]
[    2.651821] pci 0000:08:00.0: reg 0x20: [mem 0xc2400000-0xc2403fff 64bit pref]
[    2.651886] pci 0000:08:00.0: supports D1 D2
[    2.651888] pci 0000:08:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    2.651920] pci 0000:08:00.0: System wakeup disabled by ACPI
[    2.659520] pci 0000:00:1c.3: PCI bridge to [bus 08]
[    2.659524] pci 0000:00:1c.3:   bridge window [io  0x4000-0x4fff]
[    2.659528] pci 0000:00:1c.3:   bridge window [mem 0xc2600000-0xc26fffff]
[    2.659534] pci 0000:00:1c.3:   bridge window [mem 0xc2400000-0xc24fffff 64bit pref]
[    2.659615] pci 0000:09:00.0: [1002:6665] type 00 class 0x038000
[    2.659663] pci 0000:09:00.0: reg 0x10: [mem 0xa0000000-0xafffffff 64bit pref]
[    2.659680] pci 0000:09:00.0: reg 0x18: [mem 0xc2500000-0xc253ffff 64bit]
[    2.659690] pci 0000:09:00.0: reg 0x20: [io  0x3000-0x30ff]
[    2.659709] pci 0000:09:00.0: reg 0x30: [mem 0xfffe0000-0xffffffff pref]
[    2.659755] pci 0000:09:00.0: supports D1 D2
[    2.659757] pci 0000:09:00.0: PME# supported from D1 D2 D3hot
[    2.659788] pci 0000:09:00.0: System wakeup disabled by ACPI
[    2.667527] pci 0000:00:1c.4: PCI bridge to [bus 09]
[    2.667531] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
[    2.667535] pci 0000:00:1c.4:   bridge window [mem 0xc2500000-0xc25fffff]
[    2.667540] pci 0000:00:1c.4:   bridge window [mem 0xa0000000-0xafffffff 64bit pref]
[    2.669054] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    2.669117] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    2.669178] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    2.669239] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    2.669296] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    2.669352] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    2.669408] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    2.669463] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    2.670013] ACPI: Enabled 5 GPEs in block 00 to 7F
[    2.670052] ACPI : EC: GPE = 0xa, I/O: command/status = 0x66, data = 0x62
[    2.670184] vgaarb: setting as boot device: PCI:0000:00:02.0
[    2.670186] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    2.670190] vgaarb: loaded
[    2.670192] vgaarb: bridge control possible 0000:00:02.0
[    2.670528] SCSI subsystem initialized
[    2.670583] libata version 3.00 loaded.
[    2.670615] ACPI: bus type USB registered
[    2.670637] usbcore: registered new interface driver usbfs
[    2.670648] usbcore: registered new interface driver hub
[    2.670671] usbcore: registered new device driver usb
[    2.670917] PCI: Using ACPI for IRQ routing
[    2.677722] PCI: pci_cache_line_size set to 64 bytes
[    2.678088] e820: reserve RAM buffer [mem 0x00058000-0x0005ffff]
[    2.678090] e820: reserve RAM buffer [mem 0x00086000-0x0008ffff]
[    2.678092] e820: reserve RAM buffer [mem 0x94dba000-0x97ffffff]
[    2.678093] e820: reserve RAM buffer [mem 0x9c39f000-0x9fffffff]
[    2.678096] e820: reserve RAM buffer [mem 0x9cf00000-0x9fffffff]
[    2.678098] e820: reserve RAM buffer [mem 0x15f600000-0x15fffffff]
[    2.678234] NetLabel: Initializing
[    2.678235] NetLabel:  domain hash size = 128
[    2.678236] NetLabel:  protocols = UNLABELED CIPSOv4
[    2.678250] NetLabel:  unlabeled traffic allowed by default
[    2.678338] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    2.678344] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    2.680377] clocksource: Switched to clocksource hpet
[    2.687595] AppArmor: AppArmor Filesystem Enabled
[    2.687676] pnp: PnP ACPI init
[    2.687915] system 00:00: [io  0x0680-0x069f] has been reserved
[    2.687919] system 00:00: [io  0xffff] has been reserved
[    2.687922] system 00:00: [io  0xffff] has been reserved
[    2.687924] system 00:00: [io  0xffff] has been reserved
[    2.687927] system 00:00: [io  0x1800-0x18fe] could not be reserved
[    2.687930] system 00:00: [io  0x164e-0x164f] has been reserved
[    2.687935] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    2.687997] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    2.688049] system 00:02: [io  0x1854-0x1857] has been reserved
[    2.688053] system 00:02: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    2.688087] pnp 00:03: Plug and Play ACPI device, IDs TOS1102 PNP0303 (active)
[    2.688189] pnp 00:04: Plug and Play ACPI device, IDs TOS1151 PNP0f03 (active)
[    2.688932] system 00:05: [mem 0xfe102000-0xfe102fff] has been reserved
[    2.688935] system 00:05: [mem 0xfe104000-0xfe104fff] has been reserved
[    2.688938] system 00:05: [mem 0xfe106000-0xfe106fff] has been reserved
[    2.688941] system 00:05: [mem 0xfe10e000-0xfe10efff] has been reserved
[    2.688944] system 00:05: [mem 0xfe112000-0xfe112fff] has been reserved
[    2.688947] system 00:05: [mem 0xfe111000-0xfe111007] has been reserved
[    2.688950] system 00:05: [mem 0xfe111014-0xfe111fff] has been reserved
[    2.688953] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    2.689508] system 00:06: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    2.689511] system 00:06: [mem 0xfed10000-0xfed17fff] has been reserved
[    2.689514] system 00:06: [mem 0xfed18000-0xfed18fff] has been reserved
[    2.689517] system 00:06: [mem 0xfed19000-0xfed19fff] has been reserved
[    2.689520] system 00:06: [mem 0xe0000000-0xefffffff] has been reserved
[    2.689522] system 00:06: [mem 0xfed20000-0xfed3ffff] has been reserved
[    2.689525] system 00:06: [mem 0xfed90000-0xfed93fff] has been reserved
[    2.689528] system 00:06: [mem 0xfed45000-0xfed8ffff] has been reserved
[    2.689531] system 00:06: [mem 0xff000000-0xffffffff] could not be reserved
[    2.689534] system 00:06: [mem 0xfee00000-0xfeefffff] could not be reserved
[    2.689536] system 00:06: [mem 0x9fa10000-0x9fa1ffff] has been reserved
[    2.689540] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    2.690078] pnp: PnP ACPI: found 7 devices
[    2.696565] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    2.696575] pci 0000:09:00.0: can't claim BAR 6 [mem 0xfffe0000-0xffffffff pref]: no compatible bridge window
[    2.696607] pci 0000:00:1c.0: PCI bridge to [bus 01-06]
[    2.696611] pci 0000:00:1c.0:   bridge window [io  0x5000-0x5fff]
[    2.696616] pci 0000:00:1c.0:   bridge window [mem 0xc1000000-0xc1ffffff]
[    2.696621] pci 0000:00:1c.0:   bridge window [mem 0xc0000000-0xc0ffffff 64bit pref]
[    2.696627] pci 0000:00:1c.2: PCI bridge to [bus 07]
[    2.696632] pci 0000:00:1c.2:   bridge window [mem 0xc2700000-0xc27fffff]
[    2.696640] pci 0000:00:1c.3: PCI bridge to [bus 08]
[    2.696642] pci 0000:00:1c.3:   bridge window [io  0x4000-0x4fff]
[    2.696647] pci 0000:00:1c.3:   bridge window [mem 0xc2600000-0xc26fffff]
[    2.696651] pci 0000:00:1c.3:   bridge window [mem 0xc2400000-0xc24fffff 64bit pref]
[    2.696660] pci 0000:09:00.0: BAR 6: assigned [mem 0xc2540000-0xc255ffff pref]
[    2.696662] pci 0000:00:1c.4: PCI bridge to [bus 09]
[    2.696665] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
[    2.696670] pci 0000:00:1c.4:   bridge window [mem 0xc2500000-0xc25fffff]
[    2.696674] pci 0000:00:1c.4:   bridge window [mem 0xa0000000-0xafffffff 64bit pref]
[    2.696681] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    2.696683] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    2.696685] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    2.696687] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff window]
[    2.696689] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff window]
[    2.696691] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff window]
[    2.696693] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff window]
[    2.696695] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff window]
[    2.696697] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff window]
[    2.696699] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff window]
[    2.696701] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff window]
[    2.696703] pci_bus 0000:00: resource 15 [mem 0x000e0000-0x000e3fff window]
[    2.696705] pci_bus 0000:00: resource 16 [mem 0x000e4000-0x000e7fff window]
[    2.696707] pci_bus 0000:00: resource 17 [mem 0x000e8000-0x000ebfff window]
[    2.696709] pci_bus 0000:00: resource 18 [mem 0x000ec000-0x000effff window]
[    2.696711] pci_bus 0000:00: resource 19 [mem 0x9fa00000-0xfeafffff window]
[    2.696713] pci_bus 0000:01: resource 0 [io  0x5000-0x5fff]
[    2.696715] pci_bus 0000:01: resource 1 [mem 0xc1000000-0xc1ffffff]
[    2.696717] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xc0ffffff 64bit pref]
[    2.696719] pci_bus 0000:07: resource 1 [mem 0xc2700000-0xc27fffff]
[    2.696721] pci_bus 0000:08: resource 0 [io  0x4000-0x4fff]
[    2.696723] pci_bus 0000:08: resource 1 [mem 0xc2600000-0xc26fffff]
[    2.696725] pci_bus 0000:08: resource 2 [mem 0xc2400000-0xc24fffff 64bit pref]
[    2.696727] pci_bus 0000:09: resource 0 [io  0x3000-0x3fff]
[    2.696729] pci_bus 0000:09: resource 1 [mem 0xc2500000-0xc25fffff]
[    2.696731] pci_bus 0000:09: resource 2 [mem 0xa0000000-0xafffffff 64bit pref]
[    2.696770] NET: Registered protocol family 2
[    2.696965] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[    2.697055] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    2.697147] TCP: Hash tables configured (established 32768 bind 32768)
[    2.697175] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    2.697195] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    2.697254] NET: Registered protocol family 1
[    2.697272] pci 0000:00:02.0: Video device with shadowed ROM
[    2.697372] pci 0000:00:14.0: can't derive routing for PCI INT A
[    2.697374] pci 0000:00:14.0: PCI INT A: no GSI
[    2.712677] PCI: CLS 64 bytes, default 64
[    2.712741] Trying to unpack rootfs image as initramfs...
[    3.335913] Freeing initrd memory: 28904K (ffff88003477c000 - ffff8800363b6000)
[    3.335937] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    3.335940] software IO TLB [mem 0x8e6d0000-0x926d0000] (64MB) mapped at [ffff88008e6d0000-ffff8800926cffff]
[    3.336018] RAPL PMU detected, API unit is 2^-32 Joules, 4 fixed counters 655360 ms ovfl timer
[    3.336020] hw unit of domain pp0-core 2^-14 Joules
[    3.336021] hw unit of domain package 2^-14 Joules
[    3.336022] hw unit of domain dram 2^-14 Joules
[    3.336023] hw unit of domain pp1-gpu 2^-14 Joules
[    3.336158] microcode: CPU0 sig=0x40651, pf=0x40, revision=0x1c
[    3.336167] microcode: CPU1 sig=0x40651, pf=0x40, revision=0x1c
[    3.336177] microcode: CPU2 sig=0x40651, pf=0x40, revision=0x1c
[    3.336186] microcode: CPU3 sig=0x40651, pf=0x40, revision=0x1c
[    3.336247] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    3.336343] Scanning for low memory corruption every 60 seconds
[    3.336769] futex hash table entries: 2048 (order: 5, 131072 bytes)
[    3.336807] Initialise system trusted keyring
[    3.336834] audit: initializing netlink subsys (disabled)
[    3.336851] audit: type=2000 audit(1451211168.892:1): initialized
[    3.337298] HugeTLB registered 1 GB page size, pre-allocated 0 pages
[    3.337300] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    3.339238] zpool: loaded
[    3.339243] zbud: loaded
[    3.339473] VFS: Disk quotas dquot_6.6.0
[    3.339515] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    3.340092] fuse init (API version 7.23)
[    3.340266] Key type big_key registered
[    3.340617] Key type asymmetric registered
[    3.340620] Asymmetric key parser 'x509' registered
[    3.340637] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    3.340687] io scheduler noop registered
[    3.340690] io scheduler deadline registered (default)
[    3.340732] io scheduler cfq registered
[    3.341530] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    3.341533] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    3.341537] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    3.341559] pcieport 0000:00:1c.2: Signaling PME through PCIe PME interrupt
[    3.341561] pci 0000:07:00.0: Signaling PME through PCIe PME interrupt
[    3.341565] pcie_pme 0000:00:1c.2:pcie01: service driver pcie_pme loaded
[    3.341586] pcieport 0000:00:1c.3: Signaling PME through PCIe PME interrupt
[    3.341588] pci 0000:08:00.0: Signaling PME through PCIe PME interrupt
[    3.341592] pcie_pme 0000:00:1c.3:pcie01: service driver pcie_pme loaded
[    3.341614] pcieport 0000:00:1c.4: Signaling PME through PCIe PME interrupt
[    3.341616] pci 0000:09:00.0: Signaling PME through PCIe PME interrupt
[    3.341620] pcie_pme 0000:00:1c.4:pcie01: service driver pcie_pme loaded
[    3.341628] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    3.341641] pciehp 0000:00:1c.0:pcie04: Slot #0 AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug+ Surprise+ Interlock- NoCompl+ LLActRep+
[    3.341674] pciehp 0000:00:1c.0:pcie04: service driver pciehp loaded
[    3.341680] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    3.341726] efifb: probing for efifb
[    3.341739] efifb: framebuffer at 0xb0000000, mapped to 0xffffc90000800000, using 4160k, total 4160k
[    3.341741] efifb: mode is 1366x768x32, linelength=5504, pages=1
[    3.341742] efifb: scrolling: redraw
[    3.341744] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    3.341847] Console: switching to colour frame buffer device 170x48
[    3.341865] fb0: EFI VGA frame buffer device
[    3.341877] intel_idle: MWAIT substates: 0x11142120
[    3.341878] intel_idle: v0.4 model 0x45
[    3.341880] intel_idle: lapic_timer_reliable_states 0xffffffff
[    3.342262] ACPI: AC Adapter [ACAD] (off-line)
[    3.342339] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    3.342343] ACPI: Power Button [PWRB]
[    3.342389] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    3.342416] ACPI: Lid Switch [LID]
[    3.342460] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    3.342463] ACPI: Power Button [PWRF]
[    3.342830] GHES: HEST is not enabled!
[    3.342954] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    3.344838] Linux agpgart interface v0.103
[    3.347455] brd: module loaded
[    3.348515] loop: module loaded
[    3.348772] libphy: Fixed MDIO Bus: probed
[    3.348776] tun: Universal TUN/TAP device driver, 1.6
[    3.348778] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    3.348831] PPP generic driver version 2.4.2
[    3.349007] xhci_hcd 0000:00:14.0: can't derive routing for PCI INT A
[    3.349010] xhci_hcd 0000:00:14.0: PCI INT A: no GSI
[    3.349033] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    3.349040] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    3.350110] xhci_hcd 0000:00:14.0: hcc params 0x200077c1 hci version 0x100 quirks 0x0004b810
[    3.350116] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    3.350203] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    3.350206] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.350208] usb usb1: Product: xHCI Host Controller
[    3.350210] usb usb1: Manufacturer: Linux 4.2.0-22-generic xhci-hcd
[    3.350211] usb usb1: SerialNumber: 0000:00:14.0
[    3.350353] hub 1-0:1.0: USB hub found
[    3.350364] hub 1-0:1.0: 8 ports detected
[    3.351387] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    3.351392] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    3.351427] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    3.351429] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.351431] usb usb2: Product: xHCI Host Controller
[    3.351433] usb usb2: Manufacturer: Linux 4.2.0-22-generic xhci-hcd
[    3.351434] usb usb2: SerialNumber: 0000:00:14.0
[    3.351563] hub 2-0:1.0: USB hub found
[    3.351571] hub 2-0:1.0: 4 ports detected
[    3.352052] usb: failed to peer usb2-port4 and usb1-port4 by location (usb2-port4:none) (usb1-port4:usb2-port3)
[    3.352055] usb usb2-port4: failed to peer to usb1-port4 (-16)
[    3.352056] usb: port power management may be unreliable
[    3.352129] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.352135] ehci-pci: EHCI PCI platform driver
[    3.352261] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    3.352267] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 3
[    3.352279] ehci-pci 0000:00:1d.0: debug port 2
[    3.356183] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    3.356199] ehci-pci 0000:00:1d.0: irq 23, io mem 0xc2819000
[    3.364676] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    3.364713] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    3.364715] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.364717] usb usb3: Product: EHCI Host Controller
[    3.364719] usb usb3: Manufacturer: Linux 4.2.0-22-generic ehci_hcd
[    3.364721] usb usb3: SerialNumber: 0000:00:1d.0
[    3.364851] hub 3-0:1.0: USB hub found
[    3.364857] hub 3-0:1.0: 2 ports detected
[    3.364993] ehci-platform: EHCI generic platform driver
[    3.365006] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.365012] ohci-pci: OHCI PCI platform driver
[    3.365024] ohci-platform: OHCI generic platform driver
[    3.365035] uhci_hcd: USB Universal Host Controller Interface driver
[    3.365100] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    3.366440] i8042: Detected active multiplexing controller, rev 1.1
[    3.367077] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.367082] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    3.367118] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    3.367148] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    3.367177] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    3.367330] mousedev: PS/2 mouse device common for all mice
[    3.367517] rtc_cmos 00:01: RTC can wake from S4
[    3.367654] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    3.367681] rtc_cmos 00:01: alarms up to one month, 242 bytes nvram, hpet irqs
[    3.367691] i2c /dev entries driver
[    3.367784] device-mapper: uevent: version 1.0.3
[    3.367867] device-mapper: ioctl: 4.33.0-ioctl (2015-8-18) initialised: dm-devel@redhat.com
[    3.367889] Intel P-state driver initializing.
[    3.368067] ledtrig-cpu: registered to indicate activity on CPUs
[    3.368076] EFI Variables Facility v0.08 2004-May-17
[    3.387568] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    3.399500] PCCT header not found.
[    3.399757] NET: Registered protocol family 10
[    3.399971] NET: Registered protocol family 17
[    3.399984] Key type dns_resolver registered
[    3.400357] Loading compiled-in X.509 certificates
[    3.401421] Loaded X.509 cert 'Build time autogenerated kernel key: 5ba1353109d27849ddd6fbd554a5534438beafab'
[    3.401440] registered taskstats version 1
[    3.401463] zswap: loading zswap
[    3.401465] zswap: using zbud pool
[    3.401471] zswap: using lzo compressor
[    3.403831] Key type trusted registered
[    3.408069] Key type encrypted registered
[    3.408080] AppArmor: AppArmor sha1 policy hashing enabled
[    3.408086] ima: No TPM chip found, activating TPM-bypass!
[    3.408109] evm: HMAC attrs: 0x1
[    3.408816]   Magic number: 11:294:225
[    3.408930] rtc_cmos 00:01: setting system clock to 2015-12-27 10:12:51 UTC (1451211171)
[    3.409016] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.409018] EDD information not available.
[    3.409127] PM: Hibernation image not present or could not be loaded.
[    3.660851] usb 1-3: new full-speed USB device number 2 using xhci_hcd
[    3.676858] usb 3-1: new high-speed USB device number 2 using ehci-pci
[    3.791167] usb 1-3: New USB device found, idVendor=046d, idProduct=c52f
[    3.791171] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.791173] usb 1-3: Product: USB Receiver
[    3.791175] usb 1-3: Manufacturer: Logitech
[    3.809367] usb 3-1: New USB device found, idVendor=8087, idProduct=8000
[    3.809371] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    3.809769] hub 3-1:1.0: USB hub found
[    3.809833] hub 3-1:1.0: 8 ports detected
[    3.845127] ACPI: Battery Slot [BAT1] (battery present)
[    3.845514] Freeing unused kernel memory: 1460K (ffffffff81d37000 - ffffffff81ea4000)
[    3.845516] Write protecting the kernel read-only data: 12288k
[    3.845720] Freeing unused kernel memory: 32K (ffff8800027f8000 - ffff880002800000)
[    3.845807] Freeing unused kernel memory: 296K (ffff880002bb6000 - ffff880002c00000)
[    3.865935] random: systemd-udevd urandom read with 7 bits of entropy available
[    3.902800] hidraw: raw HID events driver (C) Jiri Kosina
[    3.909430] sdhci: Secure Digital Host Controller Interface driver
[    3.909434] sdhci: Copyright(c) Pierre Ossman
[    3.923889] wmi: Mapper loaded
[    3.929203] rtsx_pci 0000:01:00.0: rtsx_pci_acquire_irq: pcr->msi_en = 1, pci->irq = 45
[    3.933424] [drm] Initialized drm 1.1.0 20060810
[    3.934428] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.934441] r8169 0000:08:00.0: can't disable ASPM; OS doesn't have ASPM control
[    3.940628] ahci 0000:00:1f.2: version 3.0
[    3.941870] r8169 0000:08:00.0 eth0: RTL8168g/8111g at 0xffffc900006be000, 2c:60:0c:63:94:9b, XID 0c000880 IRQ 47
[    3.941874] r8169 0000:08:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    3.953441] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 2 ports 6 Gbps 0x1 impl SATA mode
[    3.953448] ahci 0000:00:1f.2: flags: 64bit ncq led clo only pio slum part deso sadm sds apst 
[    3.954871] scsi host0: ahci
[    3.955799] scsi host1: ahci
[    3.955866] ata1: SATA max UDMA/133 abar m2048@0xc2818000 port 0xc2818100 irq 46
[    3.955869] ata2: DUMMY
[    3.960933] usb 1-5: new full-speed USB device number 3 using xhci_hcd
[    3.975025] [drm] Memory usable by graphics device = 2048M
[    3.975032] checking generic (b0000000 410000) vs hw (b0000000 10000000)
[    3.975035] fb: switching to inteldrmfb from EFI VGA
[    3.975077] Console: switching to colour dummy device 80x25
[    3.975174] [drm] Replacing VGA console driver
[    3.982328] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    3.982331] [drm] Driver supports precise vblank timestamp query.
[    3.982442] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    3.997076] r8169 0000:08:00.0 enp8s0: renamed from eth0
[    4.008898] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    4.009270] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input10
[    4.009421] [drm] Initialized i915 1.6.0 20150522 for 0000:00:02.0 on minor 0
[    4.009872] fbcon: inteldrmfb (fb0) is primary device
[    4.009983] Console: switching to colour frame buffer device 170x48
[    4.010017] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    4.010020] i915 0000:00:02.0: registered panic notifier
[    4.094238] usb 1-5: New USB device found, idVendor=8087, idProduct=07dc
[    4.094243] usb 1-5: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    4.261106] usb 1-6: new high-speed USB device number 4 using xhci_hcd
[    4.273115] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.325133] ata1.00: ATA-8: TOSHIBA MQ01ABD100, AX1P4M, max UDMA/100
[    4.325139] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    4.327059] ata1.00: configured for UDMA/100
[    4.327283] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MQ01ABD1 4M   PQ: 0 ANSI: 5
[    4.327656] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    4.327683] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.327737] sd 0:0:0:0: [sda] Write Protect is off
[    4.327742] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.327773] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.333103] tsc: Refined TSC clocksource calibration: 1696.073 MHz
[    4.333108] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x1872a9796f1, max_idle_ns: 440795212049 ns
[    4.423829] usb 1-6: New USB device found, idVendor=04ca, idProduct=7046
[    4.423833] usb 1-6: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[    4.423836] usb 1-6: Product: TOSHIBA Web Camera - HD
[    4.423838] usb 1-6: Manufacturer: LI3SF102N2A51D1PA
[    4.423840] usb 1-6: SerialNumber: 200901010001
[    4.432485] usbcore: registered new interface driver usbhid
[    4.432488] usbhid: USB HID core driver
[    4.434369] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/0003:046D:C52F.0001/input/input11
[    4.434507] hid-generic 0003:046D:C52F.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:14.0-3/input0
[    4.435282] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.1/0003:046D:C52F.0002/input/input12
[    4.437003]  sda: sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8
[    4.437652] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.489496] hid-generic 0003:046D:C52F.0002: input,hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-3/input1
[    4.615349] psmouse serio2: synaptics: queried max coordinates: x [..5660], y [..4690]
[    4.640377] psmouse serio2: synaptics: queried min coordinates: x [1366..], y [1298..]
[    4.688046] psmouse serio2: synaptics: Touchpad model: 1, fw: 8.1, id: 0x1e2b1, caps: 0xf00123/0x840300/0x12e800/0x0, board id: 2989, fw id: 1717119
[    4.718459] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input9
[    5.333570] clocksource: Switched to clocksource tsc
[    6.578149] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[    6.725327] random: nonblocking pool is initialized
[    7.381963] systemd[1]: RTC configured in localtime, applying delta of 0 minutes to system time.
[    7.818709] systemd[1]: Failed to insert module 'kdbus': Function not implemented
[    8.020407] systemd[1]: systemd 225 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID -ELFUTILS +KMOD -IDN)
[    8.020584] systemd[1]: Detected architecture x86-64.
[    8.037551] systemd[1]: Set hostname to <afonso-toshibapowered-noobpwner>.
[    9.073242] systemd[1]: Created slice Root Slice.
[    9.073402] systemd[1]: Created slice System Slice.
[    9.073424] systemd[1]: Reached target Encrypted Volumes.
[    9.073514] systemd[1]: Listening on Journal Audit Socket.
[    9.073556] systemd[1]: Listening on udev Control Socket.
[    9.073597] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[    9.073632] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[    9.073763] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[    9.073817] systemd[1]: Listening on Journal Socket.
[    9.074341] systemd[1]: Mounting Huge Pages File System...
[    9.136505] systemd[1]: Mounting Debug File System...
[    9.136593] systemd[1]: Listening on udev Kernel Socket.
[    9.137185] systemd[1]: Starting udev Coldplug all Devices...
[    9.138024] systemd[1]: Starting Uncomplicated firewall...
[    9.138149] systemd[1]: Created slice system-getty.slice.
[    9.138178] systemd[1]: Reached target User and Group Name Lookups.
[    9.138768] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[    9.139335] systemd[1]: Starting Increase datagram queue length...
[    9.139444] systemd[1]: Created slice system-systemd\x2dfsck.slice.
[    9.139991] systemd[1]: Starting Setup Virtual Console...
[    9.140096] systemd[1]: Created slice User and Session Slice.
[    9.140119] systemd[1]: Reached target Slices.
[    9.140146] systemd[1]: Reached target Remote File Systems (Pre).
[    9.140695] systemd[1]: Mounting POSIX Message Queue File System...
[    9.141339] systemd[1]: Started Braille Device Support.
[    9.296082] systemd[1]: Starting Load Kernel Modules...
[    9.296156] systemd[1]: Listening on Journal Socket (/dev/log).
[    9.296756] systemd[1]: Started Read required files in advance.
[    9.296871] systemd[1]: Listening on fsck to fsckd communication Socket.
[    9.298207] systemd[1]: Started Create list of required static device nodes for the current kernel.
[    9.298424] systemd[1]: Started Setup Virtual Console.
[    9.299066] systemd[1]: Starting Create Static Device Nodes in /dev...
[    9.381550] systemd[1]: Mounted Huge Pages File System.
[    9.381589] systemd[1]: Mounted POSIX Message Queue File System.
[    9.381607] systemd[1]: Mounted Debug File System.
[    9.381960] systemd[1]: Started Increase datagram queue length.
[    9.382168] systemd[1]: Listening on Syslog Socket.
[    9.382734] systemd[1]: Starting Journal Service...
[    9.564137] systemd[1]: Started Uncomplicated firewall.
[    9.997434] lp: driver loaded but no devices found
[   10.003476] systemd[1]: Started Journal Service.
[   10.017193] ppdev: user-space parallel port driver
[   10.857396] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro
[   11.221801] dw_dmac INTL9C60:00: DesignWare DMA Controller, 8 channels
[   11.311901] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.499435] toshiba_bluetooth: Toshiba ACPI Bluetooth device driver
[   11.500369] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.22
[   11.503890] input: Toshiba input device as /devices/virtual/input/input15
[   11.505668] toshiba_acpi: Illumination device not available
[   11.507297] toshiba_acpi: Keyboard illumination not available
[   11.508951] toshiba_acpi: Accelerometer not supported
[   11.513713] toshiba_acpi: Sleep and Music not supported
[   11.516372] toshiba_acpi: USB 3 not supported
[   11.893904] systemd-journald[244]: Received request to flush runtime journal from PID 1
[   12.103500] Intel(R) Wireless WiFi driver for Linux
[   12.103504] Copyright(c) 2003- 2015 Intel Corporation
[   12.249034] AMD IOMMUv2 driver by Joerg Roedel <jroedel@suse.de>
[   12.249039] AMD IOMMUv2 functionality not available on this system
[   12.277534] iwlwifi 0000:07:00.0: Direct firmware load for iwlwifi-3160-15.ucode failed with error -2
[   12.283250] iwlwifi 0000:07:00.0: Direct firmware load for iwlwifi-3160-14.ucode failed with error -2
[   12.322000] iwlwifi 0000:07:00.0: loaded firmware version 25.30.13.0 op_mode iwlmvm
[   12.673509] AVX2 version of gcm_enc/dec engaged.
[   12.673513] AES CTR mode by8 optimization enabled
[   12.773282] Bluetooth: Core ver 2.20
[   12.773299] NET: Registered protocol family 31
[   12.773300] Bluetooth: HCI device and connection manager initialized
[   12.773304] Bluetooth: HCI socket layer initialized
[   12.773307] Bluetooth: L2CAP socket layer initialized
[   12.773312] Bluetooth: SCO socket layer initialized
[   12.876253] iwlwifi 0000:07:00.0: Detected Intel(R) Dual Band Wireless AC 3160, REV=0x164
[   12.876577] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled
[   12.877073] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled
[   13.013068] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   13.076365] usbcore: registered new interface driver btusb
[   13.089248] Bluetooth: hci0: read Intel version: 370710010002030d00
[   13.143557] snd_hda_intel 0000:00:03.0: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[   13.230687] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.0.2.3.d.bseq
[   13.268799] snd_hda_codec_conexant hdaudioC1D0: CX20756: BIOS auto-probing.
[   13.269125] snd_hda_codec_conexant hdaudioC1D0: autoconfig for CX20756: line_outs=1 (0x17/0x0/0x0/0x0/0x0) type:speaker
[   13.269128] snd_hda_codec_conexant hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   13.269130] snd_hda_codec_conexant hdaudioC1D0:    hp_outs=1 (0x16/0x0/0x0/0x0/0x0)
[   13.269131] snd_hda_codec_conexant hdaudioC1D0:    mono: mono_out=0x0
[   13.269133] snd_hda_codec_conexant hdaudioC1D0:    inputs:
[   13.269135] snd_hda_codec_conexant hdaudioC1D0:      Internal Mic=0x1a
[   13.269137] snd_hda_codec_conexant hdaudioC1D0:      Mic=0x19
[   13.269896] snd_hda_codec_conexant hdaudioC1D0: Enable sync_write for stable communication
[   13.272434] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input16
[   13.272544] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input17
[   13.365043] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input18
[   13.365112] input: HDA Intel HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/sound/card0/input19
[   13.365172] input: HDA Intel HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/sound/card0/input20
[   13.370355] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[   13.552350] cfg80211: World regulatory domain updated:
[   13.552354] cfg80211:  DFS Master region: unset
[   13.552356] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   13.552358] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   13.552361] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   13.552362] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[   13.552364] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[   13.552367] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[   13.552369] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[   13.552370] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[   13.552372] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[   13.828987] iwlwifi 0000:07:00.0 wlp7s0: renamed from wlan0
[   13.865453] intel_rapl: Found RAPL domain package
[   13.865458] intel_rapl: Found RAPL domain core
[   13.865461] intel_rapl: Found RAPL domain uncore
[   13.865464] intel_rapl: Found RAPL domain dram
[   13.890593] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   13.890597] Disabling lock debugging due to kernel taint
[   13.896326] fglrx: module verification failed: signature and/or required key missing - tainting kernel
[   13.909122] <6>[fglrx] Maximum main memory to use for locked dma buffers: 3711 MBytes.
[   13.909377] <6>[fglrx]   vendor: 1002 device: 6665 revision: 0 count: 1
[   13.909758] <6>[fglrx] ioport: bar 4, base 0x3000, size: 0x100
[   13.909773] pci 0000:09:00.0: enabling device (0000 -> 0003)
[   13.910040] <6>[fglrx] Kernel PAT support is enabled
[   13.910065] <6>[fglrx] module loaded - fglrx 15.20.3 [Sep  8 2015] with 1 minors
[   14.430903] media: Linux media interface: v0.10
[   14.507678] Linux video capture interface: v2.00
[   14.585992] uvcvideo: Found UVC 1.00 device TOSHIBA Web Camera - HD (04ca:7046)
[   14.588760] input: TOSHIBA Web Camera - HD as /devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/input/input21
[   14.588834] usbcore: registered new interface driver uvcvideo
[   14.588836] USB Video Class driver (1.1.1)
[   15.222679] Adding 4112380k swap on /dev/sda8.  Priority:-1 extents:1 across:4112380k FS
[   19.832830] audit: type=1400 audit(1451211187.911:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=603 comm="apparmor_parser"
[   19.832839] audit: type=1400 audit(1451211187.911:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=603 comm="apparmor_parser"
[   19.832844] audit: type=1400 audit(1451211187.911:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=603 comm="apparmor_parser"
[   19.832849] audit: type=1400 audit(1451211187.911:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=603 comm="apparmor_parser"
[   19.866903] audit: type=1400 audit(1451211187.943:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=603 comm="apparmor_parser"
[   19.866913] audit: type=1400 audit(1451211187.943:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=603 comm="apparmor_parser"
[   19.866918] audit: type=1400 audit(1451211187.943:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=603 comm="apparmor_parser"
[   19.866923] audit: type=1400 audit(1451211187.943:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=603 comm="apparmor_parser"
[   19.866929] audit: type=1400 audit(1451211187.943:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-thumbnailer" pid=603 comm="apparmor_parser"
[   19.866934] audit: type=1400 audit(1451211187.943:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=603 comm="apparmor_parser"
[   25.329352] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.329356] Bluetooth: BNEP filters: protocol multicast
[   25.329361] Bluetooth: BNEP socket layer initialized
[   29.932915] vboxdrv: Found 4 processor cores
[   29.952011] vboxdrv: TSC mode is Invariant, tentative frequency 1696071607 Hz
[   29.952014] vboxdrv: Successfully loaded version 5.0.12 (interface 0x00240000)
[   30.778027] VBoxNetFlt: Successfully started.
[   30.813546] VBoxNetAdp: Successfully started.
[   30.820493] VBoxPciLinuxInit
[   30.897848] vboxpci: IOMMU not found (not registered)
[   31.255573] IPv6: ADDRCONF(NETDEV_UP): enp8s0: link is not ready
[   31.614979] r8169 0000:08:00.0 enp8s0: link down
[   31.615020] IPv6: ADDRCONF(NETDEV_UP): enp8s0: link is not ready
[   31.618551] IPv6: ADDRCONF(NETDEV_UP): wlp7s0: link is not ready
[   31.618952] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled
[   31.619544] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled
[   31.727258] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled
[   31.727847] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled
[   31.750402] IPv6: ADDRCONF(NETDEV_UP): wlp7s0: link is not ready
[   32.708766] IPv6: ADDRCONF(NETDEV_UP): wlp7s0: link is not ready
[   36.006016] wlp7s0: authenticate with 9c:97:26:43:29:91
[   36.014768] wlp7s0: send auth to 9c:97:26:43:29:91 (try 1/3)
[   36.052602] wlp7s0: authenticated
[   36.054354] wlp7s0: associate with 9c:97:26:43:29:91 (try 1/3)
[   36.059045] wlp7s0: RX AssocResp from 9c:97:26:43:29:91 (capab=0x411 status=0 aid=2)
[   36.059572] wlp7s0: associated
[   36.059603] IPv6: ADDRCONF(NETDEV_CHANGE): wlp7s0: link becomes ready
[   36.321580] iwlwifi 0000:07:00.0: No association and the time event is over already...
[   36.381042] wlp7s0: Connection to AP 9c:97:26:43:29:91 lost
[   36.394956] cfg80211: World regulatory domain updated:
[   36.394962] cfg80211:  DFS Master region: unset
[   36.394964] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   36.394968] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   36.394971] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   36.394973] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[   36.394976] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[   36.394980] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[   36.394982] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[   36.394985] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[   36.394987] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[  145.916985] <6>[fglrx] Firegl kernel thread PID: 2345
[  145.917154] <6>[fglrx] Firegl kernel thread PID: 2346
[  145.917320] <6>[fglrx] Firegl kernel thread PID: 2347
[  145.917491] <6>[fglrx] IRQ 53 Enabled
[  145.931409] <6>[fglrx] Reserved FB block: Shared offset:0, size:1000000 
[  145.931412] <6>[fglrx] Reserved FB block: Unshared offset:f7fa000, size:4000 
[  145.931414] <6>[fglrx] Reserved FB block: Unshared offset:f7fe000, size:502000 
[  145.931415] <6>[fglrx] Reserved FB block: Unshared offset:3fff3000, size:d000 
[  146.126950] vgaarb: this pci device is not a vga device
[  149.049668] vgaarb: this pci device is not a vga device
[  158.740379] Bluetooth: RFCOMM TTY layer initialized
[  158.740390] Bluetooth: RFCOMM socket layer initialized
[  158.740397] Bluetooth: RFCOMM ver 1.11
[  166.546124] audit_printk_skb: 33 callbacks suppressed
[  166.546128] audit: type=1400 audit(1451211334.563:23): apparmor="DENIED" operation="open" profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/dconf/profile/gdm" pid=2852 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=120 ouid=0
[  167.600082] vgaarb: this pci device is not a vga device
[  193.491512] vgaarb: this pci device is not a vga device
[  194.346167] vgaarb: this pci device is not a vga device
[  212.893103] vgaarb: this pci device is not a vga device
[  238.550375] IPv6: ADDRCONF(NETDEV_UP): wlp7s0: link is not ready
[  241.754488] wlp7s0: authenticate with 9c:97:26:43:29:91
[  241.761377] wlp7s0: send auth to 9c:97:26:43:29:91 (try 1/3)
[  241.763304] wlp7s0: authenticated
[  241.764309] wlp7s0: associate with 9c:97:26:43:29:91 (try 1/3)
[  241.767605] wlp7s0: RX AssocResp from 9c:97:26:43:29:91 (capab=0x411 status=0 aid=2)
[  241.770596] wlp7s0: associated
[  241.770634] IPv6: ADDRCONF(NETDEV_CHANGE): wlp7s0: link becomes ready
[  401.267988] vgaarb: this pci device is not a vga device
[  484.205242] vgaarb: this pci device is not a vga device
[  965.679303] vgaarb: this pci device is not a vga device
[ 1233.985990] vgaarb: this pci device is not a vga device

```

It seems that the VCI error is not here anymore...  If it helps when i changed grub to boot without showing the splashscreen (only text) it shows all the things being iniciated and after about 30s it shows a fully functional tty1 but after a bit it writes the vci error and (finnaly) boots the gnome login screen. 



Thanks for the help

---

### Post by DuckHook on 2015-12-29
No problem with long post if it is enclosed in *CODE* tags which makes it easier to read. In fact, the more info, the easier to solve. *dmesg* is most of your boot log but not everything, and also includes post boot stuff. Real boot log is actually called *boot.log* and can be seen with```
cat /var/log/boot.log
```> It seems that the VCI error is not here anymore...I am confused. Are you saying that the VCE error has been solved? Perhaps a recent kernel update has resolved the issue. 30 sec delay does not seem excessive, depending on your HDD. If problem no longer exists, please mark thread "solved" even though we don't really know what has changed.

---

### Post by Afonso_Muralha on 2015-12-29
Yes, it has been solved, the error is not there anymore (the screen tearing is still there though...) and the boot times are super fast!

But now i have another (maybe worst) on this therad: [http://ubuntuforums.org/showthread.php?t=2307885](http://ubuntuforums.org/showthread.php?t=2307885)
I'm not going on further detalis on this new problem, and if someone is willing to help, i'll be on that thread.


Thanks!
Afonso Muralha

---

