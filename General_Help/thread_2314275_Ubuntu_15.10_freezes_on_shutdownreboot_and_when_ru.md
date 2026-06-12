---
title: "Ubuntu 15.10 freezes on shutdown/reboot and when running lshw"
date: 2016-02-19
forum: General Help
---

### Post by dario10 on 2016-02-19
Hi everyone, this is my first post: nice to meet you!

I am writing here for an issue I have with Ubuntu 15.10: it **freezes** every time I run **lshw** or Steam and, most annoyingly, every time I **shutdown**/reboot or even logout. When it happens, hard reset seems to be the only option (no mouse, no keyboard, no virtual terminal switching, no ctrl+alt+del, no reisub, etc.). When the system is running I have no problems switching between virtual terminals, but the system freezes even if I try to shutdown from command line, with either `shutdown -H now` or Ctrl+Alt+Del.

I'm having this issue on a Santech C47 **laptop** (Clevo P671RE6) with Skylake CPU (Intel i7-6700HQ). I believe the problem has to do with the video card (**Nvidia 970m** + Intel integrated graphics), as I have experienced cross-distro issues (Arch, Mint 17.3, Fedora 23) with it: live media would only boot with '**nomodeset**', otherwise the system freezes right after login. This happens with the Nouveau driver. With the official Nvidia driver (352.63) everything works fine, but for the freeze problem I described. With 'nomodeset' I can use lshw and shutdown/reboot the system with no problem. I am running kernel 4.2.0-27.

I can't provide many more details: even when I set the 'debug' kernel parameter in grub, I don't see errors on screen on shutdown, before the freeze. When I run `lshw` the only output I get is `PCI (sysfs)`, and then everything is frozen. Kernel logs (/var/log/**kern.log**) don't show errors, and neither do Xorg logs (/var/log/**Xorg.0.log**):

```

...
Feb 16 11:20:13 santech kernel: [    0.000000] Initializing cgroup subsys cpuset
Feb 16 11:20:13 santech kernel: [    0.000000] Initializing cgroup subsys cpu
Feb 16 11:20:13 santech kernel: [    0.000000] Initializing cgroup subsys cpuacct
Feb 16 11:20:13 santech kernel: [    0.000000] Linux version 4.2.0-27-generic (buildd@lgw01-12) (gcc version 5.2.1 20151010 (Ubuntu 5.2.1-22ubuntu2) ) #32-Ubuntu SMP Fri Jan 22 04:49:08 UTC 2016 (Ubuntu 4.2.0-27.32-generic 4.2.8-ckt1)
Feb 16 11:20:13 santech kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-27-generic.efi.signed root=UUID=7b8f97f2-410e-4e94-bba2-4f633f7e1f9e ro quiet splash vt.handoff=7
Feb 16 11:20:13 santech kernel: [    0.000000] KERNEL supported cpus:
Feb 16 11:20:13 santech kernel: [    0.000000]   Intel GenuineIntel
Feb 16 11:20:13 santech kernel: [    0.000000]   AMD AuthenticAMD
Feb 16 11:20:13 santech kernel: [    0.000000]   Centaur CentaurHauls
Feb 16 11:20:13 santech kernel: [    0.000000] x86/fpu: xstate_offset[2]: 0240, xstate_sizes[2]: 0100
Feb 16 11:20:13 santech kernel: [    0.000000] x86/fpu: xstate_offset[3]: 03c0, xstate_sizes[3]: 0040
Feb 16 11:20:13 santech kernel: [    0.000000] x86/fpu: xstate_offset[4]: 0400, xstate_sizes[4]: 0040
Feb 16 11:20:13 santech kernel: [    0.000000] x86/fpu: Supporting XSAVE feature 0x01: 'x87 floating point registers'
Feb 16 11:20:13 santech kernel: [    0.000000] x86/fpu: Supporting XSAVE feature 0x02: 'SSE registers'
Feb 16 11:20:13 santech kernel: [    0.000000] x86/fpu: Supporting XSAVE feature 0x04: 'AVX registers'
Feb 16 11:20:13 santech kernel: [    0.000000] x86/fpu: Supporting XSAVE feature 0x08: 'MPX bounds registers'
Feb 16 11:20:13 santech kernel: [    0.000000] x86/fpu: Supporting XSAVE feature 0x10: 'MPX CSR'
Feb 16 11:20:13 santech kernel: [    0.000000] x86/fpu: Enabled xstate features 0x1f, context size is 0x440 bytes, using 'standard' format.
Feb 16 11:20:13 santech kernel: [    0.000000] x86/fpu: Using 'eager' FPU context switches.
Feb 16 11:20:13 santech kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Feb 16 11:20:13 santech kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x0000000000057fff] usable
Feb 16 11:20:13 santech kernel: [    0.000000] BIOS-e820: [mem 0x0000000000058000-0x0000000000058fff] reserved
Feb 16 11:20:13 santech kernel: [    0.000000] BIOS-e820: [mem 0x0000000000059000-0x000000000009dfff] usable
Feb 16 11:20:13 santech kernel: [    0.000000] BIOS-e820: [mem 0x000000000009e000-0x000000000009ffff] reserved
Feb 16 11:20:13 santech kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000005c3fdfff] usable
Feb 16 11:20:13 santech kernel: [    0.000000] BIOS-e820: [mem 0x000000005c3fe000-0x000000005c505fff] ACPI NVS
Feb 16 11:20:13 santech kernel: [    0.000000] BIOS-e820: [mem 0x000000005c506000-0x000000005c539fff] usable
Feb 16 11:20:13 santech kernel: [    0.000000] BIOS-e820: [mem 0x000000005c53a000-0x000000005c55dfff] ACPI NVS
Feb 16 11:20:13 santech kernel: [    0.000000] BIOS-e820: [mem 0x000000005c55e000-0x000000005c795fff] reserved
Feb 16 11:20:13 santech kernel: [    0.000000] BIOS-e820: [mem 0x000000005c796000-0x000000005c7b8fff] usable
Feb 16 11:20:13 santech kernel: [    0.000000] BIOS-e820: [mem 0x000000005c7b9000-0x000000005c9bafff] ACPI NVS
Feb 16 11:20:13 santech kernel: [    0.000000] BIOS-e820: [mem 0x000000005c9bb000-0x000000005cf11fff] reserved
Feb 16 11:20:13 santech kernel: [    0.000000] BIOS-e820: [mem 0x000000005cf12000-0x000000005cf13fff] type 20
Feb 16 11:20:13 santech kernel: [    0.000000] BIOS-e820: [mem 0x000000005cf14000-0x000000005cf15fff] reserved
Feb 16 11:20:13 santech kernel: [    0.000000] BIOS-e820: [mem 0x000000005cf16000-0x000000005cf18fff] type 20
Feb 16 11:20:13 santech kernel: [    0.000000] BIOS-e820: [mem 0x000000005cf19000-0x000000005cf5afff] reserved
Feb 16 11:20:13 santech kernel: [    0.000000] BIOS-e820: [mem 0x000000005cf5b000-0x000000005cf5efff] type 20
Feb 16 11:20:13 santech kernel: [    0.000000] BIOS-e820: [mem 0x000000005cf5f000-0x000000005d1fefff] reserved
Feb 16 11:20:13 santech kernel: [    0.000000] BIOS-e820: [mem 0x000000005d1ff000-0x000000005df49fff] usable
Feb 16 11:20:13 santech kernel: [    0.000000] BIOS-e820: [mem 0x000000005df4a000-0x000000005df4afff] ACPI NVS
Feb 16 11:20:13 santech kernel: [    0.000000] BIOS-e820: [mem 0x000000005df4b000-0x000000005df94fff] reserved
Feb 16 11:20:13 santech kernel: [    0.000000] BIOS-e820: [mem 0x000000005df95000-0x000000005dfe6fff] usable
Feb 16 11:20:13 santech kernel: [    0.000000] BIOS-e820: [mem 0x000000005dfe7000-0x000000005e3f7fff] reserved
Feb 16 11:20:13 santech kernel: [    0.000000] BIOS-e820: [mem 0x000000005e3f8000-0x000000005e3fffff] usable
Feb 16 11:20:13 santech kernel: [    0.000000] BIOS-e820: [mem 0x000000005e400000-0x000000005e40efff] type 20
Feb 16 11:20:13 santech kernel: [    0.000000] BIOS-e820: [mem 0x000000005e40f000-0x000000005ff0efff] usable
Feb 16 11:20:13 santech kernel: [    0.000000] BIOS-e820: [mem 0x000000005ff0f000-0x000000005ff3efff] reserved
Feb 16 11:20:13 santech kernel: [    0.000000] BIOS-e820: [mem 0x000000005ff3f000-0x000000005ff67fff] usable
Feb 16 11:20:13 santech kernel: [    0.000000] BIOS-e820: [mem 0x000000005ff68000-0x000000005ffaefff] ACPI NVS
Feb 16 11:20:13 santech kernel: [    0.000000] BIOS-e820: [mem 0x000000005ffaf000-0x000000005ffcefff] reserved
Feb 16 11:20:13 santech kernel: [    0.000000] BIOS-e820: [mem 0x000000005ffcf000-0x000000005fffefff] type 20
Feb 16 11:20:13 santech kernel: [    0.000000] BIOS-e820: [mem 0x000000005ffff000-0x000000005fffffff] usable
Feb 16 11:20:13 santech kernel: [    0.000000] BIOS-e820: [mem 0x0000000060000000-0x00000000600fffff] reserved
Feb 16 11:20:13 santech kernel: [    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
Feb 16 11:20:13 santech kernel: [    0.000000] BIOS-e820: [mem 0x00000000fe000000-0x00000000fe010fff] reserved
Feb 16 11:20:13 santech kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
Feb 16 11:20:13 santech kernel: [    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
Feb 16 11:20:13 santech kernel: [    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
Feb 16 11:20:13 santech kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x0000000295ffffff] usable
Feb 16 11:20:13 santech kernel: [    0.000000] NX (Execute Disable) protection: active
Feb 16 11:20:13 santech kernel: [    0.000000] efi: EFI v2.40 by American Megatrends
Feb 16 11:20:13 santech kernel: [    0.000000] efi:  ESRT=0x5ffb3f98  ACPI=0x5c53a000  ACPI 2.0=0x5c53a000  SMBIOS=0x5ffb2000  SMBIOS 3.0=0x5ffb1000 
Feb 16 11:20:13 santech kernel: [    0.000000] esrt: Reserving ESRT space from 0x000000005ffb3f98 to 0x000000005ffb3fd0.
Feb 16 11:20:13 santech kernel: [    0.000000] SMBIOS 3.0.0 present.
Feb 16 11:20:13 santech kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Feb 16 11:20:13 santech kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Feb 16 11:20:13 santech kernel: [    0.000000] e820: last_pfn = 0x296000 max_arch_pfn = 0x400000000
Feb 16 11:20:13 santech kernel: [    0.000000] MTRR default type: write-back
Feb 16 11:20:13 santech kernel: [    0.000000] MTRR fixed ranges enabled:
Feb 16 11:20:13 santech kernel: [    0.000000]   00000-9FFFF write-back
Feb 16 11:20:13 santech kernel: [    0.000000]   A0000-BFFFF uncachable
Feb 16 11:20:13 santech kernel: [    0.000000]   C0000-FFFFF write-protect
Feb 16 11:20:13 santech kernel: [    0.000000] MTRR variable ranges enabled:
Feb 16 11:20:13 santech kernel: [    0.000000]   0 base 0080000000 mask 7F80000000 uncachable
Feb 16 11:20:13 santech kernel: [    0.000000]   1 base 0070000000 mask 7FF0000000 uncachable
Feb 16 11:20:13 santech kernel: [    0.000000]   2 base 0068000000 mask 7FF8000000 uncachable
Feb 16 11:20:13 santech kernel: [    0.000000]   3 base 0064000000 mask 7FFC000000 uncachable
Feb 16 11:20:13 santech kernel: [    0.000000]   4 base 0062000000 mask 7FFE000000 uncachable
Feb 16 11:20:13 santech kernel: [    0.000000]   5 base 0061000000 mask 7FFF000000 uncachable
Feb 16 11:20:13 santech kernel: [    0.000000]   6 base 0060800000 mask 7FFF800000 uncachable
Feb 16 11:20:13 santech kernel: [    0.000000]   7 disabled
Feb 16 11:20:13 santech kernel: [    0.000000]   8 disabled
Feb 16 11:20:13 santech kernel: [    0.000000]   9 disabled
Feb 16 11:20:13 santech kernel: [    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
Feb 16 11:20:13 santech kernel: [    0.000000] e820: last_pfn = 0x60000 max_arch_pfn = 0x400000000
Feb 16 11:20:13 santech kernel: [    0.000000] Scanning 1 areas for low memory corruption
Feb 16 11:20:13 santech kernel: [    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
Feb 16 11:20:13 santech kernel: [    0.000000] Using GB pages for direct mapping
Feb 16 11:20:13 santech kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
Feb 16 11:20:13 santech kernel: [    0.000000]  [mem 0x00000000-0x000fffff] page 4k
Feb 16 11:20:13 santech kernel: [    0.000000] BRK [0x02ff0000, 0x02ff0fff] PGTABLE
Feb 16 11:20:13 santech kernel: [    0.000000] BRK [0x02ff1000, 0x02ff1fff] PGTABLE
Feb 16 11:20:13 santech kernel: [    0.000000] BRK [0x02ff2000, 0x02ff2fff] PGTABLE
Feb 16 11:20:13 santech kernel: [    0.000000] init_memory_mapping: [mem 0x295e00000-0x295ffffff]
Feb 16 11:20:13 santech kernel: [    0.000000]  [mem 0x295e00000-0x295ffffff] page 2M
Feb 16 11:20:13 santech kernel: [    0.000000] BRK [0x02ff3000, 0x02ff3fff] PGTABLE
Feb 16 11:20:13 santech kernel: [    0.000000] init_memory_mapping: [mem 0x280000000-0x295dfffff]
Feb 16 11:20:13 santech kernel: [    0.000000]  [mem 0x280000000-0x295dfffff] page 2M
Feb 16 11:20:13 santech kernel: [    0.000000] init_memory_mapping: [mem 0x260000000-0x27fffffff]
Feb 16 11:20:13 santech kernel: [    0.000000]  [mem 0x260000000-0x27fffffff] page 1G
Feb 16 11:20:13 santech kernel: [    0.000000] init_memory_mapping: [mem 0x00100000-0x5c3fdfff]
Feb 16 11:20:13 santech kernel: [    0.000000]  [mem 0x00100000-0x001fffff] page 4k
Feb 16 11:20:13 santech kernel: [    0.000000]  [mem 0x00200000-0x5c1fffff] page 2M
Feb 16 11:20:13 santech kernel: [    0.000000]  [mem 0x5c200000-0x5c3fdfff] page 4k
Feb 16 11:20:13 santech kernel: [    0.000000] init_memory_mapping: [mem 0x5c506000-0x5c539fff]
Feb 16 11:20:13 santech kernel: [    0.000000]  [mem 0x5c506000-0x5c539fff] page 4k
Feb 16 11:20:13 santech kernel: [    0.000000] BRK [0x02ff4000, 0x02ff4fff] PGTABLE
Feb 16 11:20:13 santech kernel: [    0.000000] init_memory_mapping: [mem 0x5c796000-0x5c7b8fff]
Feb 16 11:20:13 santech kernel: [    0.000000]  [mem 0x5c796000-0x5c7b8fff] page 4k
Feb 16 11:20:13 santech kernel: [    0.000000] BRK [0x02ff5000, 0x02ff5fff] PGTABLE
Feb 16 11:20:13 santech kernel: [    0.000000] init_memory_mapping: [mem 0x5d1ff000-0x5df49fff]
Feb 16 11:20:13 santech kernel: [    0.000000]  [mem 0x5d1ff000-0x5d1fffff] page 4k
Feb 16 11:20:13 santech kernel: [    0.000000]  [mem 0x5d200000-0x5ddfffff] page 2M
Feb 16 11:20:13 santech kernel: [    0.000000]  [mem 0x5de00000-0x5df49fff] page 4k
Feb 16 11:20:13 santech kernel: [    0.000000] init_memory_mapping: [mem 0x5df95000-0x5dfe6fff]
Feb 16 11:20:13 santech kernel: [    0.000000]  [mem 0x5df95000-0x5dfe6fff] page 4k
Feb 16 11:20:13 santech kernel: [    0.000000] init_memory_mapping: [mem 0x5e3f8000-0x5e3fffff]
Feb 16 11:20:13 santech kernel: [    0.000000]  [mem 0x5e3f8000-0x5e3fffff] page 4k
Feb 16 11:20:13 santech kernel: [    0.000000] init_memory_mapping: [mem 0x5e40f000-0x5ff0efff]
Feb 16 11:20:13 santech kernel: [    0.000000]  [mem 0x5e40f000-0x5e5fffff] page 4k
Feb 16 11:20:13 santech kernel: [    0.000000]  [mem 0x5e600000-0x5fdfffff] page 2M
Feb 16 11:20:13 santech kernel: [    0.000000]  [mem 0x5fe00000-0x5ff0efff] page 4k
Feb 16 11:20:13 santech kernel: [    0.000000] init_memory_mapping: [mem 0x5ff3f000-0x5ff67fff]
Feb 16 11:20:13 santech kernel: [    0.000000]  [mem 0x5ff3f000-0x5ff67fff] page 4k
Feb 16 11:20:13 santech kernel: [    0.000000] init_memory_mapping: [mem 0x5ffff000-0x5fffffff]
Feb 16 11:20:13 santech kernel: [    0.000000]  [mem 0x5ffff000-0x5fffffff] page 4k
Feb 16 11:20:13 santech kernel: [    0.000000] init_memory_mapping: [mem 0x100000000-0x25fffffff]
Feb 16 11:20:13 santech kernel: [    0.000000]  [mem 0x100000000-0x25fffffff] page 1G
Feb 16 11:20:13 santech kernel: [    0.000000] RAMDISK: [mem 0x340e6000-0x3606afff]
Feb 16 11:20:13 santech kernel: [    0.000000] ACPI: Early table checksum verification disabled
Feb 16 11:20:13 santech kernel: [    0.000000] ACPI: RSDP 0x000000005C53A000 000024 (v02 ALASKA)
Feb 16 11:20:13 santech kernel: [    0.000000] ACPI: XSDT 0x000000005C53A0A0 0000BC (v01 ALASKA A M I    01072009 AMI  00010013)
Feb 16 11:20:13 santech kernel: [    0.000000] ACPI: FACP 0x000000005C553A70 00010C (v05 ALASKA A M I    01072009 AMI  00010013)
Feb 16 11:20:13 santech kernel: [    0.000000] ACPI: DSDT 0x000000005C53A1F0 01987D (v02 ALASKA A M I    01072009 INTL 20120913)
Feb 16 11:20:13 santech kernel: [    0.000000] ACPI: FACS 0x000000005FFAEF80 000040
Feb 16 11:20:13 santech kernel: [    0.000000] ACPI: APIC 0x000000005C553B80 0000BC (v03 ALASKA A M I    01072009 AMI  00010013)
Feb 16 11:20:13 santech kernel: [    0.000000] ACPI: FPDT 0x000000005C553C40 000044 (v01 ALASKA A M I    01072009 AMI  00010013)
Feb 16 11:20:13 santech kernel: [    0.000000] ACPI: FIDT 0x000000005C553C88 00009C (v01 ALASKA A M I    01072009 AMI  00010013)
Feb 16 11:20:13 santech kernel: [    0.000000] ACPI: MCFG 0x000000005C553D28 00003C (v01 ALASKA A M I    01072009 MSFT 00000097)
Feb 16 11:20:13 santech kernel: [    0.000000] ACPI: HPET 0x000000005C553D68 000038 (v01 ALASKA A M I    01072009 AMI. 0005000B)
Feb 16 11:20:13 santech kernel: [    0.000000] ACPI: SSDT 0x000000005C553DA0 000315 (v01 SataRe SataTabl 00001000 INTL 20120913)
Feb 16 11:20:13 santech kernel: [    0.000000] ACPI: SSDT 0x000000005C5540B8 001100 (v01 INTEL  PtidDevc 00001000 INTL 20120913)
Feb 16 11:20:13 santech kernel: [    0.000000] ACPI: DBGP 0x000000005C5551B8 000034 (v01 INTEL           00000000 MSFT 0000005F)
Feb 16 11:20:13 santech kernel: [    0.000000] ACPI: DBG2 0x000000005C5551F0 000054 (v00 INTEL           00000000 MSFT 0000005F)
Feb 16 11:20:13 santech kernel: [    0.000000] ACPI: SSDT 0x000000005C555248 00573A (v02 SaSsdt SaSsdt   00003000 INTL 20120913)
Feb 16 11:20:13 santech kernel: [    0.000000] ACPI: UEFI 0x000000005C55A988 000042 (v01                 00000000      00000000)
Feb 16 11:20:13 santech kernel: [    0.000000] ACPI: SSDT 0x000000005C55A9D0 000E58 (v02 CpuRef CpuSsdt  00003000 INTL 20120913)
Feb 16 11:20:13 santech kernel: [    0.000000] ACPI: SSDT 0x000000005C55B828 000778 (v02 Intel  PerfTune 00001000 INTL 20120913)
Feb 16 11:20:13 santech kernel: [    0.000000] ACPI: BGRT 0x000000005C55BFA0 000038 (v01 ALASKA A M I    01072009 AMI  00010013)
Feb 16 11:20:13 santech kernel: [    0.000000] ACPI: SSDT 0x000000005C55BFD8 00009F (v02 SgRef  SgPeg    00001000 INTL 20120913)
Feb 16 11:20:13 santech kernel: [    0.000000] ACPI: DMAR 0x000000005C55C078 0000A8 (v01 INTEL  SKL      00000001 INTL 00000001)
Feb 16 11:20:13 santech kernel: [    0.000000] ACPI: SSDT 0x000000005C55C120 001AB3 (v01 OptRef OptTabl  00001000 INTL 20120913)
Feb 16 11:20:13 santech kernel: [    0.000000] ACPI: ASF! 0x000000005C55DBD8 0000A5 (v32 INTEL   HCG     00000001 TFSM 000F4240)
Feb 16 11:20:13 santech kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Feb 16 11:20:13 santech kernel: [    0.000000] No NUMA configuration found
Feb 16 11:20:13 santech kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x0000000295ffffff]
Feb 16 11:20:13 santech kernel: [    0.000000] NODE_DATA(0) allocated [mem 0x295ff4000-0x295ff8fff]
Feb 16 11:20:13 santech kernel: [    0.000000]  [ffffea0000000000-ffffea000a5fffff] PMD -> [ffff88028d800000-ffff8802955fffff] on node 0
Feb 16 11:20:13 santech kernel: [    0.000000] Zone ranges:
Feb 16 11:20:13 santech kernel: [    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
Feb 16 11:20:13 santech kernel: [    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
Feb 16 11:20:13 santech kernel: [    0.000000]   Normal   [mem 0x0000000100000000-0x0000000295ffffff]
Feb 16 11:20:13 santech kernel: [    0.000000] Movable zone start for each node
Feb 16 11:20:13 santech kernel: [    0.000000] Early memory node ranges
Feb 16 11:20:13 santech kernel: [    0.000000]   node   0: [mem 0x0000000000001000-0x0000000000057fff]
Feb 16 11:20:13 santech kernel: [    0.000000]   node   0: [mem 0x0000000000059000-0x000000000009dfff]
Feb 16 11:20:13 santech kernel: [    0.000000]   node   0: [mem 0x0000000000100000-0x000000005c3fdfff]
Feb 16 11:20:13 santech kernel: [    0.000000]   node   0: [mem 0x000000005c506000-0x000000005c539fff]
Feb 16 11:20:13 santech kernel: [    0.000000]   node   0: [mem 0x000000005c796000-0x000000005c7b8fff]
Feb 16 11:20:13 santech kernel: [    0.000000]   node   0: [mem 0x000000005d1ff000-0x000000005df49fff]
Feb 16 11:20:13 santech kernel: [    0.000000]   node   0: [mem 0x000000005df95000-0x000000005dfe6fff]
Feb 16 11:20:13 santech kernel: [    0.000000]   node   0: [mem 0x000000005e3f8000-0x000000005e3fffff]
Feb 16 11:20:13 santech kernel: [    0.000000]   node   0: [mem 0x000000005e40f000-0x000000005ff0efff]
Feb 16 11:20:13 santech kernel: [    0.000000]   node   0: [mem 0x000000005ff3f000-0x000000005ff67fff]
Feb 16 11:20:13 santech kernel: [    0.000000]   node   0: [mem 0x000000005ffff000-0x000000005fffffff]
Feb 16 11:20:13 santech kernel: [    0.000000]   node   0: [mem 0x0000000100000000-0x0000000295ffffff]
Feb 16 11:20:13 santech kernel: [    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x0000000295ffffff]
Feb 16 11:20:13 santech kernel: [    0.000000] On node 0 totalpages: 2051264
Feb 16 11:20:13 santech kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Feb 16 11:20:13 santech kernel: [    0.000000]   DMA zone: 22 pages reserved
Feb 16 11:20:13 santech kernel: [    0.000000]   DMA zone: 3996 pages, LIFO batch:0
Feb 16 11:20:13 santech kernel: [    0.000000]   DMA32 zone: 6005 pages used for memmap
Feb 16 11:20:13 santech kernel: [    0.000000]   DMA32 zone: 384292 pages, LIFO batch:31
Feb 16 11:20:13 santech kernel: [    0.000000]   Normal zone: 25984 pages used for memmap
Feb 16 11:20:13 santech kernel: [    0.000000]   Normal zone: 1662976 pages, LIFO batch:31
Feb 16 11:20:13 santech kernel: [    0.000000] Reserving Intel graphics stolen memory at 0x61000000-0x68ffffff
Feb 16 11:20:13 santech kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1808
Feb 16 11:20:13 santech kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Feb 16 11:20:13 santech kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Feb 16 11:20:13 santech kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Feb 16 11:20:13 santech kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Feb 16 11:20:13 santech kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
Feb 16 11:20:13 santech kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] high edge lint[0x1])
Feb 16 11:20:13 santech kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] high edge lint[0x1])
Feb 16 11:20:13 santech kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] high edge lint[0x1])
Feb 16 11:20:13 santech kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x08] high edge lint[0x1])
Feb 16 11:20:13 santech kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-119
Feb 16 11:20:13 santech kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Feb 16 11:20:13 santech kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Feb 16 11:20:13 santech kernel: [    0.000000] ACPI: IRQ0 used by override.
Feb 16 11:20:13 santech kernel: [    0.000000] ACPI: IRQ9 used by override.
Feb 16 11:20:13 santech kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Feb 16 11:20:13 santech kernel: [    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
Feb 16 11:20:13 santech kernel: [    0.000000] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
Feb 16 11:20:13 santech kernel: [    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
Feb 16 11:20:13 santech kernel: [    0.000000] PM: Registered nosave memory: [mem 0x00058000-0x00058fff]
Feb 16 11:20:13 santech kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
Feb 16 11:20:13 santech kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
Feb 16 11:20:13 santech kernel: [    0.000000] PM: Registered nosave memory: [mem 0x5c3fe000-0x5c505fff]
Feb 16 11:20:13 santech kernel: [    0.000000] PM: Registered nosave memory: [mem 0x5c53a000-0x5c55dfff]
Feb 16 11:20:13 santech kernel: [    0.000000] PM: Registered nosave memory: [mem 0x5c55e000-0x5c795fff]
Feb 16 11:20:13 santech kernel: [    0.000000] PM: Registered nosave memory: [mem 0x5c7b9000-0x5c9bafff]
Feb 16 11:20:13 santech kernel: [    0.000000] PM: Registered nosave memory: [mem 0x5c9bb000-0x5cf11fff]
Feb 16 11:20:13 santech kernel: [    0.000000] PM: Registered nosave memory: [mem 0x5cf12000-0x5cf13fff]
Feb 16 11:20:13 santech kernel: [    0.000000] PM: Registered nosave memory: [mem 0x5cf14000-0x5cf15fff]
Feb 16 11:20:13 santech kernel: [    0.000000] PM: Registered nosave memory: [mem 0x5cf16000-0x5cf18fff]
Feb 16 11:20:13 santech kernel: [    0.000000] PM: Registered nosave memory: [mem 0x5cf19000-0x5cf5afff]
Feb 16 11:20:13 santech kernel: [    0.000000] PM: Registered nosave memory: [mem 0x5cf5b000-0x5cf5efff]
Feb 16 11:20:13 santech kernel: [    0.000000] PM: Registered nosave memory: [mem 0x5cf5f000-0x5d1fefff]
Feb 16 11:20:13 santech kernel: [    0.000000] PM: Registered nosave memory: [mem 0x5df4a000-0x5df4afff]
Feb 16 11:20:13 santech kernel: [    0.000000] PM: Registered nosave memory: [mem 0x5df4b000-0x5df94fff]
Feb 16 11:20:13 santech kernel: [    0.000000] PM: Registered nosave memory: [mem 0x5dfe7000-0x5e3f7fff]
Feb 16 11:20:13 santech kernel: [    0.000000] PM: Registered nosave memory: [mem 0x5e400000-0x5e40efff]
Feb 16 11:20:13 santech kernel: [    0.000000] PM: Registered nosave memory: [mem 0x5ff0f000-0x5ff3efff]
Feb 16 11:20:13 santech kernel: [    0.000000] PM: Registered nosave memory: [mem 0x5ff68000-0x5ffaefff]
Feb 16 11:20:13 santech kernel: [    0.000000] PM: Registered nosave memory: [mem 0x5ffaf000-0x5ffcefff]
Feb 16 11:20:13 santech kernel: [    0.000000] PM: Registered nosave memory: [mem 0x5ffcf000-0x5fffefff]
Feb 16 11:20:13 santech kernel: [    0.000000] PM: Registered nosave memory: [mem 0x60000000-0x600fffff]
Feb 16 11:20:13 santech kernel: [    0.000000] PM: Registered nosave memory: [mem 0x60100000-0x60ffffff]
Feb 16 11:20:13 santech kernel: [    0.000000] PM: Registered nosave memory: [mem 0x61000000-0x68ffffff]
Feb 16 11:20:13 santech kernel: [    0.000000] PM: Registered nosave memory: [mem 0x69000000-0xdfffffff]
Feb 16 11:20:13 santech kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
Feb 16 11:20:13 santech kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfdffffff]
Feb 16 11:20:13 santech kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfe000000-0xfe010fff]
Feb 16 11:20:13 santech kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfe011000-0xfebfffff]
Feb 16 11:20:13 santech kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Feb 16 11:20:13 santech kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfedfffff]
Feb 16 11:20:13 santech kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Feb 16 11:20:13 santech kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
Feb 16 11:20:13 santech kernel: [    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
Feb 16 11:20:13 santech kernel: [    0.000000] e820: [mem 0x69000000-0xdfffffff] available for PCI devices
Feb 16 11:20:13 santech kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Feb 16 11:20:13 santech kernel: [    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
Feb 16 11:20:13 santech kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
Feb 16 11:20:13 santech kernel: [    0.000000] PERCPU: Embedded 33 pages/cpu @ffff880295c00000 s96728 r8192 d30248 u262144
Feb 16 11:20:13 santech kernel: [    0.000000] pcpu-alloc: s96728 r8192 d30248 u262144 alloc=1*2097152
Feb 16 11:20:13 santech kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
Feb 16 11:20:13 santech kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 2019189
Feb 16 11:20:13 santech kernel: [    0.000000] Policy zone: Normal
Feb 16 11:20:13 santech kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-27-generic.efi.signed root=UUID=7b8f97f2-410e-4e94-bba2-4f633f7e1f9e ro quiet splash vt.handoff=7
Feb 16 11:20:13 santech kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Feb 16 11:20:13 santech kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Feb 16 11:20:13 santech kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Feb 16 11:20:13 santech kernel: [    0.000000] Memory: 7920816K/8205056K available (8154K kernel code, 1238K rwdata, 3804K rodata, 1460K init, 1292K bss, 284240K reserved, 0K cma-reserved)
Feb 16 11:20:13 santech kernel: [    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
Feb 16 11:20:13 santech kernel: [    0.000000] Hierarchical RCU implementation.
Feb 16 11:20:13 santech kernel: [    0.000000]     Build-time adjustment of leaf fanout to 64.
Feb 16 11:20:13 santech kernel: [    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
Feb 16 11:20:13 santech kernel: [    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=8
Feb 16 11:20:13 santech kernel: [    0.000000] NR_IRQS:16640 nr_irqs:2048 16
Feb 16 11:20:13 santech kernel: [    0.000000]     Offload RCU callbacks from all CPUs
Feb 16 11:20:13 santech kernel: [    0.000000]     Offload RCU callbacks from CPUs: 0-7.
Feb 16 11:20:13 santech kernel: [    0.000000] vt handoff: transparent VT on vt#7
Feb 16 11:20:13 santech kernel: [    0.000000] Console: colour dummy device 80x25
Feb 16 11:20:13 santech kernel: [    0.000000] console [tty0] enabled
Feb 16 11:20:13 santech kernel: [    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 79635855245 ns
Feb 16 11:20:13 santech kernel: [    0.000000] hpet clockevent registered
Feb 16 11:20:13 santech kernel: [    0.000000] tsc: PIT calibration matches HPET. 1 loops
Feb 16 11:20:13 santech kernel: [    0.000000] tsc: Detected 2590.846 MHz processor
Feb 16 11:20:13 santech kernel: [    0.000023] Calibrating delay loop (skipped), value calculated using timer frequency.. 5181.69 BogoMIPS (lpj=10363384)
Feb 16 11:20:13 santech kernel: [    0.000025] pid_max: default: 32768 minimum: 301
Feb 16 11:20:13 santech kernel: [    0.000028] ACPI: Core revision 20150619
Feb 16 11:20:13 santech kernel: [    0.024221] ACPI: All ACPI Tables successfully acquired
Feb 16 11:20:13 santech kernel: [    0.025144] Security Framework initialized
Feb 16 11:20:13 santech kernel: [    0.025152] AppArmor: AppArmor initialized
Feb 16 11:20:13 santech kernel: [    0.025153] Yama: becoming mindful.
Feb 16 11:20:13 santech kernel: [    0.025553] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Feb 16 11:20:13 santech kernel: [    0.026678] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
Feb 16 11:20:13 santech kernel: [    0.027160] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
Feb 16 11:20:13 santech kernel: [    0.027167] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
Feb 16 11:20:13 santech kernel: [    0.027305] Initializing cgroup subsys blkio
Feb 16 11:20:13 santech kernel: [    0.027307] Initializing cgroup subsys memory
Feb 16 11:20:13 santech kernel: [    0.027312] Initializing cgroup subsys devices
Feb 16 11:20:13 santech kernel: [    0.027313] Initializing cgroup subsys freezer
Feb 16 11:20:13 santech kernel: [    0.027314] Initializing cgroup subsys net_cls
Feb 16 11:20:13 santech kernel: [    0.027316] Initializing cgroup subsys perf_event
Feb 16 11:20:13 santech kernel: [    0.027317] Initializing cgroup subsys net_prio
Feb 16 11:20:13 santech kernel: [    0.027318] Initializing cgroup subsys hugetlb
Feb 16 11:20:13 santech kernel: [    0.027337] CPU: Physical Processor ID: 0
Feb 16 11:20:13 santech kernel: [    0.027337] CPU: Processor Core ID: 0
Feb 16 11:20:13 santech kernel: [    0.027341] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
Feb 16 11:20:13 santech kernel: [    0.027341] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
Feb 16 11:20:13 santech kernel: [    0.028239] mce: CPU supports 10 MCE banks
Feb 16 11:20:13 santech kernel: [    0.028252] CPU0: Thermal monitoring enabled (TM1)
Feb 16 11:20:13 santech kernel: [    0.028260] process: using mwait in idle threads
Feb 16 11:20:13 santech kernel: [    0.028262] Last level iTLB entries: 4KB 64, 2MB 8, 4MB 8
Feb 16 11:20:13 santech kernel: [    0.028263] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0, 1GB 4
Feb 16 11:20:13 santech kernel: [    0.028527] Freeing SMP alternatives memory: 28K (ffffffff81ea4000 - ffffffff81eab000)
Feb 16 11:20:13 santech kernel: [    0.031487] ftrace: allocating 30933 entries in 121 pages
Feb 16 11:20:13 santech kernel: [    0.041038] DMAR: Host address width 39
Feb 16 11:20:13 santech kernel: [    0.041042] DMAR: DRHD base: 0x000000fed90000 flags: 0x0
Feb 16 11:20:13 santech kernel: [    0.041050] DMAR: dmar0: reg_base_addr fed90000 ver 1:0 cap 1c0000c40660462 ecap 7e3ff0501e
Feb 16 11:20:13 santech kernel: [    0.041051] DMAR: DRHD base: 0x000000fed91000 flags: 0x1
Feb 16 11:20:13 santech kernel: [    0.041055] DMAR: dmar1: reg_base_addr fed91000 ver 1:0 cap d2008c40660462 ecap f050da
Feb 16 11:20:13 santech kernel: [    0.041056] DMAR: RMRR base: 0x0000005cee0000 end: 0x0000005cefffff
Feb 16 11:20:13 santech kernel: [    0.041057] DMAR: RMRR base: 0x00000060800000 end: 0x00000068ffffff
Feb 16 11:20:13 santech kernel: [    0.041058] DMAR-IR: IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
Feb 16 11:20:13 santech kernel: [    0.041059] DMAR-IR: HPET id 0 under DRHD base 0xfed91000
Feb 16 11:20:13 santech kernel: [    0.041060] DMAR-IR: x2apic is disabled because BIOS sets x2apic opt out bit.
Feb 16 11:20:13 santech kernel: [    0.041060] DMAR-IR: Use 'intremap=no_x2apic_optout' to override the BIOS setting.
Feb 16 11:20:13 santech kernel: [    0.042467] DMAR-IR: Enabled IRQ remapping in xapic mode
Feb 16 11:20:13 santech kernel: [    0.042468] x2apic: IRQ remapping doesn't support X2APIC mode
Feb 16 11:20:13 santech kernel: [    0.046410] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Feb 16 11:20:13 santech kernel: [    0.086076] TSC deadline timer enabled
Feb 16 11:20:13 santech kernel: [    0.086081] smpboot: CPU0: Intel(R) Core(TM) i7-6700HQ CPU @ 2.60GHz (fam: 06, model: 5e, stepping: 03)
Feb 16 11:20:13 santech kernel: [    0.086098] Performance Events: PEBS fmt3+, 32-deep LBR, Skylake events, full-width counters, Intel PMU driver.
Feb 16 11:20:13 santech kernel: [    0.086119] ... version:                4
Feb 16 11:20:13 santech kernel: [    0.086119] ... bit width:              48
Feb 16 11:20:13 santech kernel: [    0.086120] ... generic registers:      4
Feb 16 11:20:13 santech kernel: [    0.086121] ... value mask:             0000ffffffffffff
Feb 16 11:20:13 santech kernel: [    0.086121] ... max period:             0000ffffffffffff
Feb 16 11:20:13 santech kernel: [    0.086122] ... fixed-purpose events:   3
Feb 16 11:20:13 santech kernel: [    0.086122] ... event mask:             000000070000000f
Feb 16 11:20:13 santech kernel: [    0.086708] x86: Booting SMP configuration:
Feb 16 11:20:13 santech kernel: [    0.086709] .... node  #0, CPUs:      #1
Feb 16 11:20:13 santech kernel: [    0.090922] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Feb 16 11:20:13 santech kernel: [    0.090976]  #2 #3 #4 #5 #6 #7
Feb 16 11:20:13 santech kernel: [    0.116375] x86: Booted up 1 node, 8 CPUs
Feb 16 11:20:13 santech kernel: [    0.116378] smpboot: Total of 8 processors activated (41453.53 BogoMIPS)
Feb 16 11:20:13 santech kernel: [    0.122627] devtmpfs: initialized
Feb 16 11:20:13 santech kernel: [    0.124223] evm: security.selinux
Feb 16 11:20:13 santech kernel: [    0.124224] evm: security.SMACK64
Feb 16 11:20:13 santech kernel: [    0.124225] evm: security.SMACK64EXEC
Feb 16 11:20:13 santech kernel: [    0.124225] evm: security.SMACK64TRANSMUTE
Feb 16 11:20:13 santech kernel: [    0.124226] evm: security.SMACK64MMAP
Feb 16 11:20:13 santech kernel: [    0.124227] evm: security.ima
Feb 16 11:20:13 santech kernel: [    0.124227] evm: security.capability
Feb 16 11:20:13 santech kernel: [    0.124283] PM: Registering ACPI NVS region [mem 0x5c3fe000-0x5c505fff] (1081344 bytes)
Feb 16 11:20:13 santech kernel: [    0.124292] PM: Registering ACPI NVS region [mem 0x5c53a000-0x5c55dfff] (147456 bytes)
Feb 16 11:20:13 santech kernel: [    0.124294] PM: Registering ACPI NVS region [mem 0x5c7b9000-0x5c9bafff] (2105344 bytes)
Feb 16 11:20:13 santech kernel: [    0.124326] PM: Registering ACPI NVS region [mem 0x5df4a000-0x5df4afff] (4096 bytes)
Feb 16 11:20:13 santech kernel: [    0.124327] PM: Registering ACPI NVS region [mem 0x5ff68000-0x5ffaefff] (290816 bytes)
Feb 16 11:20:13 santech kernel: [    0.124383] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
Feb 16 11:20:13 santech kernel: [    0.124442] pinctrl core: initialized pinctrl subsystem
Feb 16 11:20:13 santech kernel: [    0.124582] RTC time: 11:20:03, date: 02/16/16
Feb 16 11:20:13 santech kernel: [    0.124663] NET: Registered protocol family 16
Feb 16 11:20:13 santech kernel: [    0.134439] cpuidle: using governor ladder
Feb 16 11:20:13 santech kernel: [    0.138433] cpuidle: using governor menu
Feb 16 11:20:13 santech kernel: [    0.138495] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
Feb 16 11:20:13 santech kernel: [    0.138497] ACPI: bus type PCI registered
Feb 16 11:20:13 santech kernel: [    0.138498] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
Feb 16 11:20:13 santech kernel: [    0.138555] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Feb 16 11:20:13 santech kernel: [    0.138556] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
Feb 16 11:20:13 santech kernel: [    0.138567] PCI: Using configuration type 1 for base access
Feb 16 11:20:13 santech kernel: [    0.142699] ACPI: Added _OSI(Module Device)
Feb 16 11:20:13 santech kernel: [    0.142701] ACPI: Added _OSI(Processor Device)
Feb 16 11:20:13 santech kernel: [    0.142702] ACPI: Added _OSI(3.0 _SCP Extensions)
Feb 16 11:20:13 santech kernel: [    0.142703] ACPI: Added _OSI(Processor Aggregator Device)
Feb 16 11:20:13 santech kernel: [    0.148459] ACPI: Executed 20 blocks of module-level executable AML code
Feb 16 11:20:13 santech kernel: [    0.153110] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Feb 16 11:20:13 santech kernel: [    0.156253] ACPI: Dynamic OEM Table Load:
Feb 16 11:20:13 santech kernel: [    0.156258] ACPI: SSDT 0xFFFF88028BFC4C00 00037F (v02 PmRef  Cpu0Cst  00003001 INTL 20120913)
Feb 16 11:20:13 santech kernel: [    0.156910] ACPI: Dynamic OEM Table Load:
Feb 16 11:20:13 santech kernel: [    0.156914] ACPI: SSDT 0xFFFF88028C335800 0005DC (v02 PmRef  Cpu0Ist  00003000 INTL 20120913)
Feb 16 11:20:13 santech kernel: [    0.158344] ACPI: Dynamic OEM Table Load:
Feb 16 11:20:13 santech kernel: [    0.158348] ACPI: SSDT 0xFFFF88028C336000 0005AA (v02 PmRef  ApIst    00003000 INTL 20120913)
Feb 16 11:20:13 santech kernel: [    0.159159] ACPI: Dynamic OEM Table Load:
Feb 16 11:20:13 santech kernel: [    0.159163] ACPI: SSDT 0xFFFF88028BFF3200 000119 (v02 PmRef  ApCst    00003000 INTL 20120913)
Feb 16 11:20:13 santech kernel: [    0.162976] ACPI : EC: EC started
Feb 16 11:20:13 santech kernel: [    0.163399] ACPI: Interpreter enabled
Feb 16 11:20:13 santech kernel: [    0.163407] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20150619/hwxface-580)
Feb 16 11:20:13 santech kernel: [    0.163413] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150619/hwxface-580)
Feb 16 11:20:13 santech kernel: [    0.163429] ACPI: (supports S0 S3 S4 S5)
Feb 16 11:20:13 santech kernel: [    0.163430] ACPI: Using IOAPIC for interrupt routing
Feb 16 11:20:13 santech kernel: [    0.163454] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Feb 16 11:20:13 santech kernel: [    0.164905] ACPI: Power Resource [PG00] (on)
Feb 16 11:20:13 santech kernel: [    0.165214] ACPI: Power Resource [PG01] (on)
Feb 16 11:20:13 santech kernel: [    0.165474] ACPI: Power Resource [PG02] (on)
Feb 16 11:20:13 santech kernel: [    0.174913] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
Feb 16 11:20:13 santech kernel: [    0.174917] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
Feb 16 11:20:13 santech kernel: [    0.174938] \_SB_.PCI0:_OSC invalid UUID
Feb 16 11:20:13 santech kernel: [    0.174939] _OSC request data:1 1f 0 
Feb 16 11:20:13 santech kernel: [    0.174941] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
Feb 16 11:20:13 santech kernel: [    0.175276] PCI host bridge to bus 0000:00
Feb 16 11:20:13 santech kernel: [    0.175277] pci_bus 0000:00: root bus resource [bus 00-fe]
Feb 16 11:20:13 santech kernel: [    0.175279] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
Feb 16 11:20:13 santech kernel: [    0.175280] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
Feb 16 11:20:13 santech kernel: [    0.175281] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
Feb 16 11:20:13 santech kernel: [    0.175282] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff window]
Feb 16 11:20:13 santech kernel: [    0.175283] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff window]
Feb 16 11:20:13 santech kernel: [    0.175284] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff window]
Feb 16 11:20:13 santech kernel: [    0.175285] pci_bus 0000:00: root bus resource [mem 0x000cc000-0x000cffff window]
Feb 16 11:20:13 santech kernel: [    0.175286] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff window]
Feb 16 11:20:13 santech kernel: [    0.175287] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff window]
Feb 16 11:20:13 santech kernel: [    0.175288] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff window]
Feb 16 11:20:13 santech kernel: [    0.175289] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff window]
Feb 16 11:20:13 santech kernel: [    0.175289] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff window]
Feb 16 11:20:13 santech kernel: [    0.175290] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff window]
Feb 16 11:20:13 santech kernel: [    0.175291] pci_bus 0000:00: root bus resource [mem 0x000e8000-0x000ebfff window]
Feb 16 11:20:13 santech kernel: [    0.175292] pci_bus 0000:00: root bus resource [mem 0x000ec000-0x000effff window]
Feb 16 11:20:13 santech kernel: [    0.175293] pci_bus 0000:00: root bus resource [mem 0x000f0000-0x000fffff window]
Feb 16 11:20:13 santech kernel: [    0.175294] pci_bus 0000:00: root bus resource [mem 0x69000000-0xdfffffff window]
Feb 16 11:20:13 santech kernel: [    0.175295] pci_bus 0000:00: root bus resource [mem 0xfd000000-0xfe7fffff window]
Feb 16 11:20:13 santech kernel: [    0.175300] pci 0000:00:00.0: [8086:1910] type 00 class 0x060000
Feb 16 11:20:13 santech kernel: [    0.175372] pci 0000:00:01.0: [8086:1901] type 01 class 0x060400
Feb 16 11:20:13 santech kernel: [    0.175398] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Feb 16 11:20:13 santech kernel: [    0.175472] pci 0000:00:01.0: System wakeup disabled by ACPI
Feb 16 11:20:13 santech kernel: [    0.175519] pci 0000:00:02.0: [8086:191b] type 00 class 0x030000
Feb 16 11:20:13 santech kernel: [    0.175529] pci 0000:00:02.0: reg 0x10: [mem 0xdd000000-0xddffffff 64bit]
Feb 16 11:20:13 santech kernel: [    0.175533] pci 0000:00:02.0: reg 0x18: [mem 0xa0000000-0xbfffffff 64bit pref]
Feb 16 11:20:13 santech kernel: [    0.175536] pci 0000:00:02.0: reg 0x20: [io  0xf000-0xf03f]
Feb 16 11:20:13 santech kernel: [    0.175666] pci 0000:00:14.0: [8086:a12f] type 00 class 0x0c0330
Feb 16 11:20:13 santech kernel: [    0.175689] pci 0000:00:14.0: reg 0x10: [mem 0xdf310000-0xdf31ffff 64bit]
Feb 16 11:20:13 santech kernel: [    0.175733] pci 0000:00:14.0: PME# supported from D3hot D3cold
Feb 16 11:20:13 santech kernel: [    0.175793] pci 0000:00:14.0: System wakeup disabled by ACPI
Feb 16 11:20:13 santech kernel: [    0.175822] pci 0000:00:14.2: [8086:a131] type 00 class 0x118000
Feb 16 11:20:13 santech kernel: [    0.175844] pci 0000:00:14.2: reg 0x10: [mem 0xdf32e000-0xdf32efff 64bit]
Feb 16 11:20:13 santech kernel: [    0.175953] pci 0000:00:16.0: [8086:a13a] type 00 class 0x078000
Feb 16 11:20:13 santech kernel: [    0.175979] pci 0000:00:16.0: reg 0x10: [mem 0xdf32d000-0xdf32dfff 64bit]
Feb 16 11:20:13 santech kernel: [    0.176025] pci 0000:00:16.0: PME# supported from D3hot
Feb 16 11:20:13 santech kernel: [    0.176125] pci 0000:00:17.0: [8086:a103] type 00 class 0x010601
Feb 16 11:20:13 santech kernel: [    0.176143] pci 0000:00:17.0: reg 0x10: [mem 0xdf328000-0xdf329fff]
Feb 16 11:20:13 santech kernel: [    0.176150] pci 0000:00:17.0: reg 0x14: [mem 0xdf32c000-0xdf32c0ff]
Feb 16 11:20:13 santech kernel: [    0.176156] pci 0000:00:17.0: reg 0x18: [io  0xf090-0xf097]
Feb 16 11:20:13 santech kernel: [    0.176162] pci 0000:00:17.0: reg 0x1c: [io  0xf080-0xf083]
Feb 16 11:20:13 santech kernel: [    0.176168] pci 0000:00:17.0: reg 0x20: [io  0xf060-0xf07f]
Feb 16 11:20:13 santech kernel: [    0.176174] pci 0000:00:17.0: reg 0x24: [mem 0xdf32b000-0xdf32b7ff]
Feb 16 11:20:13 santech kernel: [    0.176195] pci 0000:00:17.0: PME# supported from D3hot
Feb 16 11:20:13 santech kernel: [    0.176282] pci 0000:00:1c.0: [8086:a114] type 01 class 0x060400
Feb 16 11:20:13 santech kernel: [    0.176325] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Feb 16 11:20:13 santech kernel: [    0.176393] pci 0000:00:1c.0: System wakeup disabled by ACPI
Feb 16 11:20:13 santech kernel: [    0.176429] pci 0000:00:1c.5: [8086:a115] type 01 class 0x060400
Feb 16 11:20:13 santech kernel: [    0.176474] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
Feb 16 11:20:13 santech kernel: [    0.176541] pci 0000:00:1c.5: System wakeup disabled by ACPI
Feb 16 11:20:13 santech kernel: [    0.176576] pci 0000:00:1f.0: [8086:a14e] type 00 class 0x060100
Feb 16 11:20:13 santech kernel: [    0.176737] pci 0000:00:1f.2: [8086:a121] type 00 class 0x058000
Feb 16 11:20:13 santech kernel: [    0.176747] pci 0000:00:1f.2: reg 0x10: [mem 0xdf324000-0xdf327fff]
Feb 16 11:20:13 santech kernel: [    0.176853] pci 0000:00:1f.3: [8086:a170] type 00 class 0x040300
Feb 16 11:20:13 santech kernel: [    0.176882] pci 0000:00:1f.3: reg 0x10: [mem 0xdf320000-0xdf323fff 64bit]
Feb 16 11:20:13 santech kernel: [    0.176903] pci 0000:00:1f.3: reg 0x20: [mem 0xdf300000-0xdf30ffff 64bit]
Feb 16 11:20:13 santech kernel: [    0.176928] pci 0000:00:1f.3: PME# supported from D3hot D3cold
Feb 16 11:20:13 santech kernel: [    0.177024] pci 0000:00:1f.3: System wakeup disabled by ACPI
Feb 16 11:20:13 santech kernel: [    0.177055] pci 0000:00:1f.4: [8086:a123] type 00 class 0x0c0500
Feb 16 11:20:13 santech kernel: [    0.177108] pci 0000:00:1f.4: reg 0x10: [mem 0xdf32a000-0xdf32a0ff 64bit]
Feb 16 11:20:13 santech kernel: [    0.177177] pci 0000:00:1f.4: reg 0x20: [io  0xf040-0xf05f]
Feb 16 11:20:13 santech kernel: [    0.177338] pci 0000:01:00.0: [10de:1618] type 00 class 0x030000
Feb 16 11:20:13 santech kernel: [    0.177350] pci 0000:01:00.0: reg 0x10: [mem 0xde000000-0xdeffffff]
Feb 16 11:20:13 santech kernel: [    0.177357] pci 0000:01:00.0: reg 0x14: [mem 0xc0000000-0xcfffffff 64bit pref]
Feb 16 11:20:13 santech kernel: [    0.177364] pci 0000:01:00.0: reg 0x1c: [mem 0xd0000000-0xd1ffffff 64bit pref]
Feb 16 11:20:13 santech kernel: [    0.177368] pci 0000:01:00.0: reg 0x24: [io  0xe000-0xe07f]
Feb 16 11:20:13 santech kernel: [    0.177373] pci 0000:01:00.0: reg 0x30: [mem 0xdf000000-0xdf07ffff pref]
Feb 16 11:20:13 santech kernel: [    0.177426] pci 0000:01:00.0: System wakeup disabled by ACPI
Feb 16 11:20:13 santech kernel: [    0.182541] pci 0000:00:01.0: PCI bridge to [bus 01]
Feb 16 11:20:13 santech kernel: [    0.182543] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
Feb 16 11:20:13 santech kernel: [    0.182545] pci 0000:00:01.0:   bridge window [mem 0xde000000-0xdf0fffff]
Feb 16 11:20:13 santech kernel: [    0.182548] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
Feb 16 11:20:13 santech kernel: [    0.182619] pci 0000:02:00.0: [10ec:5287] type 00 class 0xff0000
Feb 16 11:20:13 santech kernel: [    0.182651] pci 0000:02:00.0: reg 0x10: [mem 0xdf215000-0xdf215fff]
Feb 16 11:20:13 santech kernel: [    0.182691] pci 0000:02:00.0: reg 0x30: [mem 0xdf200000-0xdf20ffff pref]
Feb 16 11:20:13 santech kernel: [    0.182737] pci 0000:02:00.0: supports D1 D2
Feb 16 11:20:13 santech kernel: [    0.182738] pci 0000:02:00.0: PME# supported from D1 D2 D3hot D3cold
Feb 16 11:20:13 santech kernel: [    0.182770] pci 0000:02:00.0: System wakeup disabled by ACPI
Feb 16 11:20:13 santech kernel: [    0.182806] pci 0000:02:00.1: [10ec:8168] type 00 class 0x020000
Feb 16 11:20:13 santech kernel: [    0.182840] pci 0000:02:00.1: reg 0x10: [io  0xd000-0xd0ff]
Feb 16 11:20:13 santech kernel: [    0.182864] pci 0000:02:00.1: reg 0x18: [mem 0xdf214000-0xdf214fff 64bit]
Feb 16 11:20:13 santech kernel: [    0.182879] pci 0000:02:00.1: reg 0x20: [mem 0xdf210000-0xdf213fff 64bit]
Feb 16 11:20:13 santech kernel: [    0.182930] pci 0000:02:00.1: supports D1 D2
Feb 16 11:20:13 santech kernel: [    0.182931] pci 0000:02:00.1: PME# supported from D0 D1 D2 D3hot D3cold
Feb 16 11:20:13 santech kernel: [    0.190550] pci 0000:00:1c.0: PCI bridge to [bus 02]
Feb 16 11:20:13 santech kernel: [    0.190552] pci 0000:00:1c.0:   bridge window [io  0xd000-0xdfff]
Feb 16 11:20:13 santech kernel: [    0.190555] pci 0000:00:1c.0:   bridge window [mem 0xdf200000-0xdf2fffff]
Feb 16 11:20:13 santech kernel: [    0.190642] pci 0000:03:00.0: [8086:24f3] type 00 class 0x028000
Feb 16 11:20:13 santech kernel: [    0.190703] pci 0000:03:00.0: reg 0x10: [mem 0xdf100000-0xdf101fff 64bit]
Feb 16 11:20:13 santech kernel: [    0.190832] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
Feb 16 11:20:13 santech kernel: [    0.190884] pci 0000:03:00.0: System wakeup disabled by ACPI
Feb 16 11:20:13 santech kernel: [    0.198561] pci 0000:00:1c.5: PCI bridge to [bus 03]
Feb 16 11:20:13 santech kernel: [    0.198565] pci 0000:00:1c.5:   bridge window [mem 0xdf100000-0xdf1fffff]
Feb 16 11:20:13 santech kernel: [    0.199445] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
Feb 16 11:20:13 santech kernel: [    0.199486] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *10 11 12 14 15)
Feb 16 11:20:13 santech kernel: [    0.199525] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 *11 12 14 15)
Feb 16 11:20:13 santech kernel: [    0.199564] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 *11 12 14 15)
Feb 16 11:20:13 santech kernel: [    0.199602] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 *11 12 14 15)
Feb 16 11:20:13 santech kernel: [    0.199640] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 *11 12 14 15)
Feb 16 11:20:13 santech kernel: [    0.199678] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 *11 12 14 15)
Feb 16 11:20:13 santech kernel: [    0.199716] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 *11 12 14 15)
Feb 16 11:20:13 santech kernel: [    0.199962] ACPI: Enabled 5 GPEs in block 00 to 7F
Feb 16 11:20:13 santech kernel: [    0.200033] ACPI : EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
Feb 16 11:20:13 santech kernel: [    0.200114] vgaarb: setting as boot device: PCI:0000:00:02.0
Feb 16 11:20:13 santech kernel: [    0.200115] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Feb 16 11:20:13 santech kernel: [    0.200118] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=none,locks=none
Feb 16 11:20:13 santech kernel: [    0.200119] vgaarb: loaded
Feb 16 11:20:13 santech kernel: [    0.200120] vgaarb: bridge control possible 0000:01:00.0
Feb 16 11:20:13 santech kernel: [    0.200121] vgaarb: no bridge control possible 0000:00:02.0
Feb 16 11:20:13 santech kernel: [    0.200280] SCSI subsystem initialized
Feb 16 11:20:13 santech kernel: [    0.200306] libata version 3.00 loaded.
Feb 16 11:20:13 santech kernel: [    0.200324] ACPI: bus type USB registered
Feb 16 11:20:13 santech kernel: [    0.200336] usbcore: registered new interface driver usbfs
Feb 16 11:20:13 santech kernel: [    0.200342] usbcore: registered new interface driver hub
Feb 16 11:20:13 santech kernel: [    0.200357] usbcore: registered new device driver usb
Feb 16 11:20:13 santech kernel: [    0.200535] PCI: Using ACPI for IRQ routing
Feb 16 11:20:13 santech kernel: [    0.228599] PCI: pci_cache_line_size set to 64 bytes
Feb 16 11:20:13 santech kernel: [    0.228668] e820: reserve RAM buffer [mem 0x00058000-0x0005ffff]
Feb 16 11:20:13 santech kernel: [    0.228669] e820: reserve RAM buffer [mem 0x0009e000-0x0009ffff]
Feb 16 11:20:13 santech kernel: [    0.228670] e820: reserve RAM buffer [mem 0x5c3fe000-0x5fffffff]
Feb 16 11:20:13 santech kernel: [    0.228673] e820: reserve RAM buffer [mem 0x5c53a000-0x5fffffff]
Feb 16 11:20:13 santech kernel: [    0.228676] e820: reserve RAM buffer [mem 0x5c7b9000-0x5fffffff]
Feb 16 11:20:13 santech kernel: [    0.228678] e820: reserve RAM buffer [mem 0x5df4a000-0x5fffffff]
Feb 16 11:20:13 santech kernel: [    0.228680] e820: reserve RAM buffer [mem 0x5dfe7000-0x5fffffff]
Feb 16 11:20:13 santech kernel: [    0.228682] e820: reserve RAM buffer [mem 0x5e400000-0x5fffffff]
Feb 16 11:20:13 santech kernel: [    0.228683] e820: reserve RAM buffer [mem 0x5ff0f000-0x5fffffff]
Feb 16 11:20:13 santech kernel: [    0.228684] e820: reserve RAM buffer [mem 0x5ff68000-0x5fffffff]
Feb 16 11:20:13 santech kernel: [    0.228685] e820: reserve RAM buffer [mem 0x296000000-0x297ffffff]
Feb 16 11:20:13 santech kernel: [    0.228759] NetLabel: Initializing
Feb 16 11:20:13 santech kernel: [    0.228759] NetLabel:  domain hash size = 128
Feb 16 11:20:13 santech kernel: [    0.228760] NetLabel:  protocols = UNLABELED CIPSOv4
Feb 16 11:20:13 santech kernel: [    0.228767] NetLabel:  unlabeled traffic allowed by default
Feb 16 11:20:13 santech kernel: [    0.228844] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
Feb 16 11:20:13 santech kernel: [    0.228848] hpet0: 8 comparators, 64-bit 24.000000 MHz counter
Feb 16 11:20:13 santech kernel: [    0.230893] clocksource: Switched to clocksource hpet
Feb 16 11:20:13 santech kernel: [    0.235016] AppArmor: AppArmor Filesystem Enabled
Feb 16 11:20:13 santech kernel: [    0.235049] pnp: PnP ACPI init
Feb 16 11:20:13 santech kernel: [    0.235187] system 00:00: [io  0x0680-0x069f] has been reserved
Feb 16 11:20:13 santech kernel: [    0.235189] system 00:00: [io  0xffff] has been reserved
Feb 16 11:20:13 santech kernel: [    0.235190] system 00:00: [io  0xffff] has been reserved
Feb 16 11:20:13 santech kernel: [    0.235191] system 00:00: [io  0xffff] has been reserved
Feb 16 11:20:13 santech kernel: [    0.235192] system 00:00: [io  0x1800-0x18fe] could not be reserved
Feb 16 11:20:13 santech kernel: [    0.235193] system 00:00: [io  0x164e-0x164f] has been reserved
Feb 16 11:20:13 santech kernel: [    0.235194] system 00:00: [io  0x3322-0x3323] has been reserved
Feb 16 11:20:13 santech kernel: [    0.235196] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
Feb 16 11:20:13 santech kernel: [    0.235254] system 00:01: [io  0x0800-0x087f] has been reserved
Feb 16 11:20:13 santech kernel: [    0.235256] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Feb 16 11:20:13 santech kernel: [    0.235270] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
Feb 16 11:20:13 santech kernel: [    0.235293] system 00:03: [io  0x1854-0x1857] has been reserved
Feb 16 11:20:13 santech kernel: [    0.235295] system 00:03: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
Feb 16 11:20:13 santech kernel: [    0.235310] pnp 00:04: Plug and Play ACPI device, IDs PNP0303 (active)
Feb 16 11:20:13 santech kernel: [    0.235384] pnp 00:05: Plug and Play ACPI device, IDs SYN1219 PNP0f13 (active)
Feb 16 11:20:13 santech kernel: [    0.235519] system 00:06: [mem 0xfed10000-0xfed17fff] has been reserved
Feb 16 11:20:13 santech kernel: [    0.235520] system 00:06: [mem 0xfed18000-0xfed18fff] has been reserved
Feb 16 11:20:13 santech kernel: [    0.235522] system 00:06: [mem 0xfed19000-0xfed19fff] has been reserved
Feb 16 11:20:13 santech kernel: [    0.235523] system 00:06: [mem 0xe0000000-0xefffffff] has been reserved
Feb 16 11:20:13 santech kernel: [    0.235524] system 00:06: [mem 0xfed20000-0xfed3ffff] has been reserved
Feb 16 11:20:13 santech kernel: [    0.235525] system 00:06: [mem 0xfed90000-0xfed93fff] could not be reserved
Feb 16 11:20:13 santech kernel: [    0.235526] system 00:06: [mem 0xfed45000-0xfed8ffff] has been reserved
Feb 16 11:20:13 santech kernel: [    0.235528] system 00:06: [mem 0xff000000-0xffffffff] has been reserved
Feb 16 11:20:13 santech kernel: [    0.235529] system 00:06: [mem 0xfee00000-0xfeefffff] could not be reserved
Feb 16 11:20:13 santech kernel: [    0.235530] system 00:06: [mem 0xdffe0000-0xdfffffff] has been reserved
Feb 16 11:20:13 santech kernel: [    0.235532] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
Feb 16 11:20:13 santech kernel: [    0.235558] system 00:07: [mem 0xfd000000-0xfdabffff] has been reserved
Feb 16 11:20:13 santech kernel: [    0.235559] system 00:07: [mem 0xfdad0000-0xfdadffff] has been reserved
Feb 16 11:20:13 santech kernel: [    0.235560] system 00:07: [mem 0xfdb00000-0xfdffffff] has been reserved
Feb 16 11:20:13 santech kernel: [    0.235562] system 00:07: [mem 0xfe000000-0xfe01ffff] could not be reserved
Feb 16 11:20:13 santech kernel: [    0.235563] system 00:07: [mem 0xfe036000-0xfe03bfff] has been reserved
Feb 16 11:20:13 santech kernel: [    0.235564] system 00:07: [mem 0xfe03d000-0xfe3fffff] has been reserved
Feb 16 11:20:13 santech kernel: [    0.235565] system 00:07: [mem 0xfe410000-0xfe7fffff] has been reserved
Feb 16 11:20:13 santech kernel: [    0.235566] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
Feb 16 11:20:13 santech kernel: [    0.235754] system 00:08: [io  0xff00-0xfffe] has been reserved
Feb 16 11:20:13 santech kernel: [    0.235755] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
Feb 16 11:20:13 santech kernel: [    0.236438] system 00:09: [mem 0xfdaf0000-0xfdafffff] has been reserved
Feb 16 11:20:13 santech kernel: [    0.236439] system 00:09: [mem 0xfdae0000-0xfdaeffff] has been reserved
Feb 16 11:20:13 santech kernel: [    0.236440] system 00:09: [mem 0xfdac0000-0xfdacffff] has been reserved
Feb 16 11:20:13 santech kernel: [    0.236442] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
Feb 16 11:20:13 santech kernel: [    0.236816] pnp: PnP ACPI: found 10 devices
Feb 16 11:20:13 santech kernel: [    0.245495] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
Feb 16 11:20:13 santech kernel: [    0.245512] pci 0000:00:01.0: PCI bridge to [bus 01]
Feb 16 11:20:13 santech kernel: [    0.245513] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
Feb 16 11:20:13 santech kernel: [    0.245516] pci 0000:00:01.0:   bridge window [mem 0xde000000-0xdf0fffff]
Feb 16 11:20:13 santech kernel: [    0.245518] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
Feb 16 11:20:13 santech kernel: [    0.245520] pci 0000:00:1c.0: PCI bridge to [bus 02]
Feb 16 11:20:13 santech kernel: [    0.245522] pci 0000:00:1c.0:   bridge window [io  0xd000-0xdfff]
Feb 16 11:20:13 santech kernel: [    0.245524] pci 0000:00:1c.0:   bridge window [mem 0xdf200000-0xdf2fffff]
Feb 16 11:20:13 santech kernel: [    0.245529] pci 0000:00:1c.5: PCI bridge to [bus 03]
Feb 16 11:20:13 santech kernel: [    0.245532] pci 0000:00:1c.5:   bridge window [mem 0xdf100000-0xdf1fffff]
Feb 16 11:20:13 santech kernel: [    0.245537] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
Feb 16 11:20:13 santech kernel: [    0.245538] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
Feb 16 11:20:13 santech kernel: [    0.245539] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
Feb 16 11:20:13 santech kernel: [    0.245540] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff window]
Feb 16 11:20:13 santech kernel: [    0.245541] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff window]
Feb 16 11:20:13 santech kernel: [    0.245542] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff window]
Feb 16 11:20:13 santech kernel: [    0.245543] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff window]
Feb 16 11:20:13 santech kernel: [    0.245544] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff window]
Feb 16 11:20:13 santech kernel: [    0.245545] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff window]
Feb 16 11:20:13 santech kernel: [    0.245546] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff window]
Feb 16 11:20:13 santech kernel: [    0.245547] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff window]
Feb 16 11:20:13 santech kernel: [    0.245548] pci_bus 0000:00: resource 15 [mem 0x000e0000-0x000e3fff window]
Feb 16 11:20:13 santech kernel: [    0.245549] pci_bus 0000:00: resource 16 [mem 0x000e4000-0x000e7fff window]
Feb 16 11:20:13 santech kernel: [    0.245550] pci_bus 0000:00: resource 17 [mem 0x000e8000-0x000ebfff window]
Feb 16 11:20:13 santech kernel: [    0.245551] pci_bus 0000:00: resource 18 [mem 0x000ec000-0x000effff window]
Feb 16 11:20:13 santech kernel: [    0.245552] pci_bus 0000:00: resource 19 [mem 0x000f0000-0x000fffff window]
Feb 16 11:20:13 santech kernel: [    0.245553] pci_bus 0000:00: resource 20 [mem 0x69000000-0xdfffffff window]
Feb 16 11:20:13 santech kernel: [    0.245554] pci_bus 0000:00: resource 21 [mem 0xfd000000-0xfe7fffff window]
Feb 16 11:20:13 santech kernel: [    0.245555] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
Feb 16 11:20:13 santech kernel: [    0.245556] pci_bus 0000:01: resource 1 [mem 0xde000000-0xdf0fffff]
Feb 16 11:20:13 santech kernel: [    0.245557] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xd1ffffff 64bit pref]
Feb 16 11:20:13 santech kernel: [    0.245558] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
Feb 16 11:20:13 santech kernel: [    0.245559] pci_bus 0000:02: resource 1 [mem 0xdf200000-0xdf2fffff]
Feb 16 11:20:13 santech kernel: [    0.245560] pci_bus 0000:03: resource 1 [mem 0xdf100000-0xdf1fffff]
Feb 16 11:20:13 santech kernel: [    0.245578] NET: Registered protocol family 2
Feb 16 11:20:13 santech kernel: [    0.245736] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
Feb 16 11:20:13 santech kernel: [    0.245865] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Feb 16 11:20:13 santech kernel: [    0.245954] TCP: Hash tables configured (established 65536 bind 65536)
Feb 16 11:20:13 santech kernel: [    0.245973] UDP hash table entries: 4096 (order: 5, 131072 bytes)
Feb 16 11:20:13 santech kernel: [    0.245991] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
Feb 16 11:20:13 santech kernel: [    0.246026] NET: Registered protocol family 1
Feb 16 11:20:13 santech kernel: [    0.246037] pci 0000:00:02.0: Video device with shadowed ROM
Feb 16 11:20:13 santech kernel: [    0.246859] PCI: CLS 0 bytes, default 64
Feb 16 11:20:13 santech kernel: [    0.246949] Trying to unpack rootfs image as initramfs...
Feb 16 11:20:13 santech kernel: [    0.622701] Freeing initrd memory: 32276K (ffff8800340e6000 - ffff88003606b000)
Feb 16 11:20:13 santech kernel: [    0.622719] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Feb 16 11:20:13 santech kernel: [    0.622721] software IO TLB [mem 0x583e4000-0x5c3e4000] (64MB) mapped at [ffff8800583e4000-ffff88005c3e3fff]
Feb 16 11:20:13 santech kernel: [    0.622949] microcode: CPU0 sig=0x506e3, pf=0x20, revision=0x55
Feb 16 11:20:13 santech kernel: [    0.622953] microcode: CPU1 sig=0x506e3, pf=0x20, revision=0x55
Feb 16 11:20:13 santech kernel: [    0.622960] microcode: CPU2 sig=0x506e3, pf=0x20, revision=0x55
Feb 16 11:20:13 santech kernel: [    0.622983] microcode: CPU3 sig=0x506e3, pf=0x20, revision=0x55
Feb 16 11:20:13 santech kernel: [    0.622993] microcode: CPU4 sig=0x506e3, pf=0x20, revision=0x55
Feb 16 11:20:13 santech kernel: [    0.623003] microcode: CPU5 sig=0x506e3, pf=0x20, revision=0x55
Feb 16 11:20:13 santech kernel: [    0.623013] microcode: CPU6 sig=0x506e3, pf=0x20, revision=0x55
Feb 16 11:20:13 santech kernel: [    0.623022] microcode: CPU7 sig=0x506e3, pf=0x20, revision=0x55
Feb 16 11:20:13 santech kernel: [    0.623106] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Feb 16 11:20:13 santech kernel: [    0.623210] Scanning for low memory corruption every 60 seconds
Feb 16 11:20:13 santech kernel: [    0.623562] futex hash table entries: 2048 (order: 5, 131072 bytes)
Feb 16 11:20:13 santech kernel: [    0.623587] Initialise system trusted keyring
Feb 16 11:20:13 santech kernel: [    0.623603] audit: initializing netlink subsys (disabled)
Feb 16 11:20:13 santech kernel: [    0.623613] audit: type=2000 audit(1455621603.628:1): initialized
Feb 16 11:20:13 santech kernel: [    0.623881] HugeTLB registered 1 GB page size, pre-allocated 0 pages
Feb 16 11:20:13 santech kernel: [    0.623882] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Feb 16 11:20:13 santech kernel: [    0.624826] zpool: loaded
Feb 16 11:20:13 santech kernel: [    0.624828] zbud: loaded
Feb 16 11:20:13 santech kernel: [    0.625036] VFS: Disk quotas dquot_6.6.0
Feb 16 11:20:13 santech kernel: [    0.625057] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Feb 16 11:20:13 santech kernel: [    0.625413] fuse init (API version 7.23)
Feb 16 11:20:13 santech kernel: [    0.625543] Key type big_key registered
Feb 16 11:20:13 santech kernel: [    0.626747] Key type asymmetric registered
Feb 16 11:20:13 santech kernel: [    0.626748] Asymmetric key parser 'x509' registered
Feb 16 11:20:13 santech kernel: [    0.626757] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
Feb 16 11:20:13 santech kernel: [    0.627172] io scheduler noop registered
Feb 16 11:20:13 santech kernel: [    0.627198] io scheduler deadline registered (default)
Feb 16 11:20:13 santech kernel: [    0.627247] io scheduler cfq registered
Feb 16 11:20:13 santech kernel: [    0.627599] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb 16 11:20:13 santech kernel: [    0.627604] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Feb 16 11:20:13 santech kernel: [    0.627633] efifb: probing for efifb
Feb 16 11:20:13 santech kernel: [    0.627645] efifb: framebuffer at 0xa0000000, mapped to 0xffffc90001000000, using 8128k, total 8128k
Feb 16 11:20:13 santech kernel: [    0.627646] efifb: mode is 1920x1080x32, linelength=7680, pages=1
Feb 16 11:20:13 santech kernel: [    0.627647] efifb: scrolling: redraw
Feb 16 11:20:13 santech kernel: [    0.627648] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Feb 16 11:20:13 santech kernel: [    0.627738] Console: switching to colour frame buffer device 240x67
Feb 16 11:20:13 santech kernel: [    0.627755] fb0: EFI VGA frame buffer device
Feb 16 11:20:13 santech kernel: [    0.627761] intel_idle: MWAIT substates: 0x11142120
Feb 16 11:20:13 santech kernel: [    0.627762] intel_idle: v0.4 model 0x5E
Feb 16 11:20:13 santech kernel: [    0.627762] intel_idle: lapic_timer_reliable_states 0xffffffff
Feb 16 11:20:13 santech kernel: [    0.628724] ACPI: AC Adapter [AC] (off-line)
Feb 16 11:20:13 santech kernel: [    0.628768] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Feb 16 11:20:13 santech kernel: [    0.628770] ACPI: Power Button [PWRB]
Feb 16 11:20:13 santech kernel: [    0.628791] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
Feb 16 11:20:13 santech kernel: [    0.628793] ACPI: Sleep Button [SLPB]
Feb 16 11:20:13 santech kernel: [    0.628814] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
Feb 16 11:20:13 santech kernel: [    0.629142] ACPI: Lid Switch [LID0]
Feb 16 11:20:13 santech kernel: [    0.629164] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Feb 16 11:20:13 santech kernel: [    0.629166] ACPI: Power Button [PWRF]
Feb 16 11:20:13 santech kernel: [    0.629662] thermal LNXTHERM:00: registered as thermal_zone0
Feb 16 11:20:13 santech kernel: [    0.629663] ACPI: Thermal Zone [TZ0] (25 C)
Feb 16 11:20:13 santech kernel: [    0.629705] GHES: HEST is not enabled!
Feb 16 11:20:13 santech kernel: [    0.629838] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Feb 16 11:20:13 santech kernel: [    0.630087] ACPI: Battery Slot [BAT0] (battery present)
Feb 16 11:20:13 santech kernel: [    0.632892] Linux agpgart interface v0.103
Feb 16 11:20:13 santech kernel: [    0.635906] brd: module loaded
Feb 16 11:20:13 santech kernel: [    0.637003] loop: module loaded
Feb 16 11:20:13 santech kernel: [    0.637305] libphy: Fixed MDIO Bus: probed
Feb 16 11:20:13 santech kernel: [    0.637307] tun: Universal TUN/TAP device driver, 1.6
Feb 16 11:20:13 santech kernel: [    0.637308] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Feb 16 11:20:13 santech kernel: [    0.637365] PPP generic driver version 2.4.2
Feb 16 11:20:13 santech kernel: [    0.637539] xhci_hcd 0000:00:14.0: xHCI Host Controller
Feb 16 11:20:13 santech kernel: [    0.637543] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
Feb 16 11:20:13 santech kernel: [    0.638609] xhci_hcd 0000:00:14.0: hcc params 0x200077c1 hci version 0x100 quirks 0x00109810
Feb 16 11:20:13 santech kernel: [    0.638614] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
Feb 16 11:20:13 santech kernel: [    0.638665] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Feb 16 11:20:13 santech kernel: [    0.638666] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Feb 16 11:20:13 santech kernel: [    0.638667] usb usb1: Product: xHCI Host Controller
Feb 16 11:20:13 santech kernel: [    0.638668] usb usb1: Manufacturer: Linux 4.2.0-27-generic xhci-hcd
Feb 16 11:20:13 santech kernel: [    0.638669] usb usb1: SerialNumber: 0000:00:14.0
Feb 16 11:20:13 santech kernel: [    0.638790] hub 1-0:1.0: USB hub found
Feb 16 11:20:13 santech kernel: [    0.638804] hub 1-0:1.0: 16 ports detected
Feb 16 11:20:13 santech kernel: [    0.646451] xhci_hcd 0000:00:14.0: xHCI Host Controller
Feb 16 11:20:13 santech kernel: [    0.646452] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
Feb 16 11:20:13 santech kernel: [    0.646471] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
Feb 16 11:20:13 santech kernel: [    0.646472] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Feb 16 11:20:13 santech kernel: [    0.646473] usb usb2: Product: xHCI Host Controller
Feb 16 11:20:13 santech kernel: [    0.646474] usb usb2: Manufacturer: Linux 4.2.0-27-generic xhci-hcd
Feb 16 11:20:13 santech kernel: [    0.646474] usb usb2: SerialNumber: 0000:00:14.0
Feb 16 11:20:13 santech kernel: [    0.646621] hub 2-0:1.0: USB hub found
Feb 16 11:20:13 santech kernel: [    0.646630] hub 2-0:1.0: 8 ports detected
Feb 16 11:20:13 santech kernel: [    0.648502] usb: failed to peer usb2-port4 and usb1-port3 by location (usb2-port4:none) (usb1-port3:usb2-port3)
Feb 16 11:20:13 santech kernel: [    0.648503] usb usb2-port4: failed to peer to usb1-port3 (-16)
Feb 16 11:20:13 santech kernel: [    0.648504] usb: port power management may be unreliable
Feb 16 11:20:13 santech kernel: [    0.648924] usb: failed to peer usb2-port5 and usb1-port3 by location (usb2-port5:none) (usb1-port3:usb2-port3)
Feb 16 11:20:13 santech kernel: [    0.648925] usb usb2-port5: failed to peer to usb1-port3 (-16)
Feb 16 11:20:13 santech kernel: [    0.649763] usb: failed to peer usb2-port7 and usb1-port7 by location (usb2-port7:none) (usb1-port7:usb2-port6)
Feb 16 11:20:13 santech kernel: [    0.649764] usb usb2-port7: failed to peer to usb1-port7 (-16)
Feb 16 11:20:13 santech kernel: [    0.650182] usb: failed to peer usb2-port8 and usb1-port7 by location (usb2-port8:none) (usb1-port7:usb2-port6)
Feb 16 11:20:13 santech kernel: [    0.650183] usb usb2-port8: failed to peer to usb1-port7 (-16)
Feb 16 11:20:13 santech kernel: [    0.650260] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Feb 16 11:20:13 santech kernel: [    0.650263] ehci-pci: EHCI PCI platform driver
Feb 16 11:20:13 santech kernel: [    0.650270] ehci-platform: EHCI generic platform driver
Feb 16 11:20:13 santech kernel: [    0.650275] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Feb 16 11:20:13 santech kernel: [    0.650277] ohci-pci: OHCI PCI platform driver
Feb 16 11:20:13 santech kernel: [    0.650283] ohci-platform: OHCI generic platform driver
Feb 16 11:20:13 santech kernel: [    0.650288] uhci_hcd: USB Universal Host Controller Interface driver
Feb 16 11:20:13 santech kernel: [    0.650318] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:SYNM] at 0x60,0x64 irq 1,12
Feb 16 11:20:13 santech kernel: [    1.199324] i8042: Detected active multiplexing controller, rev 1.1
Feb 16 11:20:13 santech kernel: [    1.201836] serio: i8042 KBD port at 0x60,0x64 irq 1
Feb 16 11:20:13 santech kernel: [    1.201838] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Feb 16 11:20:13 santech kernel: [    1.201856] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Feb 16 11:20:13 santech kernel: [    1.201870] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Feb 16 11:20:13 santech kernel: [    1.201883] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Feb 16 11:20:13 santech kernel: [    1.202136] mousedev: PS/2 mouse device common for all mice
Feb 16 11:20:13 santech kernel: [    1.202662] rtc_cmos 00:02: RTC can wake from S4
Feb 16 11:20:13 santech kernel: [    1.203351] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
Feb 16 11:20:13 santech kernel: [    1.203429] rtc_cmos 00:02: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
Feb 16 11:20:13 santech kernel: [    1.203434] i2c /dev entries driver
Feb 16 11:20:13 santech kernel: [    1.203496] device-mapper: uevent: version 1.0.3
Feb 16 11:20:13 santech kernel: [    1.203687] device-mapper: ioctl: 4.33.0-ioctl (2015-8-18) initialised: dm-devel@redhat.com
Feb 16 11:20:13 santech kernel: [    1.203712] Intel P-state driver initializing.
Feb 16 11:20:13 santech kernel: [    1.204241] ledtrig-cpu: registered to indicate activity on CPUs
Feb 16 11:20:13 santech kernel: [    1.204249] EFI Variables Facility v0.08 2004-May-17
Feb 16 11:20:13 santech kernel: [    1.206495] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Feb 16 11:20:13 santech kernel: [    1.213189] PCCT header not found.
Feb 16 11:20:13 santech kernel: [    1.213395] NET: Registered protocol family 10
Feb 16 11:20:13 santech kernel: [    1.213792] NET: Registered protocol family 17
Feb 16 11:20:13 santech kernel: [    1.213803] Key type dns_resolver registered
Feb 16 11:20:13 santech kernel: [    1.214573] Loading compiled-in X.509 certificates
Feb 16 11:20:13 santech kernel: [    1.215202] Loaded X.509 cert 'Build time autogenerated kernel key: 9421ce78f7dd6932d7a71d3bab89bb036afa29eb'
Feb 16 11:20:13 santech kernel: [    1.215213] registered taskstats version 1
Feb 16 11:20:13 santech kernel: [    1.215230] zswap: loading zswap
Feb 16 11:20:13 santech kernel: [    1.215231] zswap: using zbud pool
Feb 16 11:20:13 santech kernel: [    1.215235] zswap: using lzo compressor
Feb 16 11:20:13 santech kernel: [    1.217259] Key type trusted registered
Feb 16 11:20:13 santech kernel: [    1.221420] Key type encrypted registered
Feb 16 11:20:13 santech kernel: [    1.221424] AppArmor: AppArmor sha1 policy hashing enabled
Feb 16 11:20:13 santech kernel: [    1.221426] ima: No TPM chip found, activating TPM-bypass!
Feb 16 11:20:13 santech kernel: [    1.221438] evm: HMAC attrs: 0x1
Feb 16 11:20:13 santech kernel: [    1.222315]   Magic number: 4:613:327
Feb 16 11:20:13 santech kernel: [    1.222672] rtc_cmos 00:02: setting system clock to 2016-02-16 11:20:04 UTC (1455621604)
Feb 16 11:20:13 santech kernel: [    1.222985] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Feb 16 11:20:13 santech kernel: [    1.222986] EDD information not available.
Feb 16 11:20:13 santech kernel: [    1.223159] PM: Hibernation image not present or could not be loaded.
Feb 16 11:20:13 santech kernel: [    1.223887] Freeing unused kernel memory: 1460K (ffffffff81d37000 - ffffffff81ea4000)
Feb 16 11:20:13 santech kernel: [    1.223888] Write protecting the kernel read-only data: 12288k
Feb 16 11:20:13 santech kernel: [    1.224607] Freeing unused kernel memory: 24K (ffff8800027fa000 - ffff880002800000)
Feb 16 11:20:13 santech kernel: [    1.224978] Freeing unused kernel memory: 292K (ffff880002bb7000 - ffff880002c00000)
Feb 16 11:20:13 santech kernel: [    1.234492] random: systemd-udevd urandom read with 9 bits of entropy available
Feb 16 11:20:13 santech kernel: [    1.257317] hidraw: raw HID events driver (C) Jiri Kosina
Feb 16 11:20:13 santech kernel: [    1.279810] rtsx_pci 0000:02:00.0: enabling device (0000 -> 0002)
Feb 16 11:20:13 santech kernel: [    1.280008] rtsx_pci 0000:02:00.0: rtsx_pci_acquire_irq: pcr->msi_en = 1, pci->irq = 124
Feb 16 11:20:13 santech kernel: [    1.280032] ahci 0000:00:17.0: version 3.0
Feb 16 11:20:13 santech kernel: [    1.280179] ahci 0000:00:17.0: SSS flag set, parallel bus scan disabled
Feb 16 11:20:13 santech kernel: [    1.281578] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Feb 16 11:20:13 santech kernel: [    1.281600] r8169 0000:02:00.1: can't disable ASPM; OS doesn't have ASPM control
Feb 16 11:20:13 santech kernel: [    1.283048] [drm] Initialized drm 1.1.0 20060810
Feb 16 11:20:13 santech kernel: [    1.287985] r8169 0000:02:00.1 eth0: RTL8411 at 0xffffc90000eac000, 80:fa:5b:22:50:5f, XID 1c800800 IRQ 126
Feb 16 11:20:13 santech kernel: [    1.287988] r8169 0000:02:00.1 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
Feb 16 11:20:13 santech kernel: [    1.294992] ahci 0000:00:17.0: AHCI 0001.0301 32 slots 2 ports 6 Gbps 0xc impl SATA mode
Feb 16 11:20:13 santech kernel: [    1.294995] ahci 0000:00:17.0: flags: 64bit ncq sntf stag pm led clo only pio slum part ems deso sadm sds apst 
Feb 16 11:20:13 santech kernel: [    1.303650] scsi host0: ahci
Feb 16 11:20:13 santech kernel: [    1.304075] scsi host1: ahci
Feb 16 11:20:13 santech kernel: [    1.304326] scsi host2: ahci
Feb 16 11:20:13 santech kernel: [    1.304959] scsi host3: ahci
Feb 16 11:20:13 santech kernel: [    1.304996] ata1: DUMMY
Feb 16 11:20:13 santech kernel: [    1.304997] ata2: DUMMY
Feb 16 11:20:13 santech kernel: [    1.304999] ata3: SATA max UDMA/133 abar m2048@0xdf32b000 port 0xdf32b200 irq 125
Feb 16 11:20:13 santech kernel: [    1.305003] ata4: SATA max UDMA/133 abar m2048@0xdf32b000 port 0xdf32b280 irq 125
Feb 16 11:20:13 santech kernel: [    1.306622] [drm] Memory usable by graphics device = 4096M
Feb 16 11:20:13 santech kernel: [    1.308126] checking generic (a0000000 7f0000) vs hw (a0000000 20000000)
Feb 16 11:20:13 santech kernel: [    1.308127] fb: switching to inteldrmfb from EFI VGA
Feb 16 11:20:13 santech kernel: [    1.308142] Console: switching to colour dummy device 80x25
Feb 16 11:20:13 santech kernel: [    1.308315] [drm] Replacing VGA console driver
Feb 16 11:20:13 santech kernel: [    1.315466] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
Feb 16 11:20:13 santech kernel: [    1.315468] [drm] Driver supports precise vblank timestamp query.
Feb 16 11:20:13 santech kernel: [    1.325348] r8169 0000:02:00.1 enp2s0f1: renamed from eth0
Feb 16 11:20:13 santech kernel: [    1.325765] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
Feb 16 11:20:13 santech kernel: [    1.337176] fbcon: inteldrmfb (fb0) is primary device
Feb 16 11:20:13 santech kernel: [    1.337222] Console: switching to colour frame buffer device 240x67
Feb 16 11:20:13 santech kernel: [    1.337241] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
Feb 16 11:20:13 santech kernel: [    1.337242] i915 0000:00:02.0: registered panic notifier
Feb 16 11:20:13 santech kernel: [    1.338517] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Feb 16 11:20:13 santech kernel: [    1.338770] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input10
Feb 16 11:20:13 santech kernel: [    1.339060] ACPI Exception: AE_NOT_FOUND, Evaluating _DOD (20150619/video-1157)
Feb 16 11:20:13 santech kernel: [    1.339063] ACPI: Video Device [PEGP] (multi-head: no  rom: yes  post: no)
Feb 16 11:20:13 santech kernel: [    1.339087] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:12/LNXVIDEO:01/input/input11
Feb 16 11:20:13 santech kernel: [    1.339338] [drm] Initialized i915 1.6.0 20150522 for 0000:00:02.0 on minor 0
Feb 16 11:20:13 santech kernel: [    1.406777] usb 1-4: new low-speed USB device number 2 using xhci_hcd
Feb 16 11:20:13 santech kernel: [    1.538497] usb 1-4: New USB device found, idVendor=046d, idProduct=c06c
Feb 16 11:20:13 santech kernel: [    1.538499] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Feb 16 11:20:13 santech kernel: [    1.538500] usb 1-4: Product: USB Optical Mouse
Feb 16 11:20:13 santech kernel: [    1.538501] usb 1-4: Manufacturer: Logitech
Feb 16 11:20:13 santech kernel: [    1.538766] usb 1-4: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
Feb 16 11:20:13 santech kernel: [    1.551477] usbcore: registered new interface driver usbhid
Feb 16 11:20:13 santech kernel: [    1.551478] usbhid: USB HID core driver
Feb 16 11:20:13 santech kernel: [    1.553535] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.0/0003:046D:C06C.0001/input/input13
Feb 16 11:20:13 santech kernel: [    1.553939] hid-generic 0003:046D:C06C.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:14.0-4/input0
Feb 16 11:20:13 santech kernel: [    1.618815] tsc: Refined TSC clocksource calibration: 2591.973 MHz
Feb 16 11:20:13 santech kernel: [    1.618817] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x255c9d3d01a, max_idle_ns: 440795269681 ns
Feb 16 11:20:13 santech kernel: [    1.650793] usb 1-7: new full-speed USB device number 3 using xhci_hcd
Feb 16 11:20:13 santech kernel: [    1.667568] ata3: SATA link down (SStatus 4 SControl 300)
Feb 16 11:20:13 santech kernel: [    1.780687] usb 1-7: New USB device found, idVendor=1c7a, idProduct=0603
Feb 16 11:20:13 santech kernel: [    1.780689] usb 1-7: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Feb 16 11:20:13 santech kernel: [    1.780690] usb 1-7: Product: EgisTec_ES603
Feb 16 11:20:13 santech kernel: [    1.780691] usb 1-7: Manufacturer: EgisTec
Feb 16 11:20:13 santech kernel: [    1.946705] usb 1-8: new full-speed USB device number 4 using xhci_hcd
Feb 16 11:20:13 santech kernel: [    1.986714] ata4: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Feb 16 11:20:13 santech kernel: [    1.986949] ata4.00: supports DRM functions and may not be fully accessible
Feb 16 11:20:13 santech kernel: [    1.987109] ata4.00: READ LOG DMA EXT failed, trying unqueued
Feb 16 11:20:13 santech kernel: [    1.987170] ata4.00: failed to get NCQ Send/Recv Log Emask 0x1
Feb 16 11:20:13 santech kernel: [    1.987171] ata4.00: ATA-9: Samsung SSD 850 EVO 500GB, EMT01B6Q, max UDMA/133
Feb 16 11:20:13 santech kernel: [    1.987172] ata4.00: 976773168 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
Feb 16 11:20:13 santech kernel: [    1.988759] ata4.00: supports DRM functions and may not be fully accessible
Feb 16 11:20:13 santech kernel: [    1.988873] ata4.00: failed to get NCQ Send/Recv Log Emask 0x1
Feb 16 11:20:13 santech kernel: [    1.988994] ata4.00: configured for UDMA/133
Feb 16 11:20:13 santech kernel: [    1.994997] scsi 3:0:0:0: Direct-Access     ATA      Samsung SSD 850  1B6Q PQ: 0 ANSI: 5
Feb 16 11:20:13 santech kernel: [    1.995624] sd 3:0:0:0: Attached scsi generic sg0 type 0
Feb 16 11:20:13 santech kernel: [    1.995744] sd 3:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Feb 16 11:20:13 santech kernel: [    1.996465] sd 3:0:0:0: [sda] Write Protect is off
Feb 16 11:20:13 santech kernel: [    1.996481] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
Feb 16 11:20:13 santech kernel: [    1.996682] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 16 11:20:13 santech kernel: [    1.999486]  sda: sda1 sda2 sda3 sda4 sda5 sda6
Feb 16 11:20:13 santech kernel: [    2.001150] sd 3:0:0:0: [sda] Attached SCSI disk
Feb 16 11:20:13 santech kernel: [    2.075743] usb 1-8: New USB device found, idVendor=8087, idProduct=0a2b
Feb 16 11:20:13 santech kernel: [    2.075745] usb 1-8: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Feb 16 11:20:13 santech kernel: [    2.242664] usb 1-9: new high-speed USB device number 5 using xhci_hcd
Feb 16 11:20:13 santech kernel: [    2.419402] usb 1-9: New USB device found, idVendor=5986, idProduct=066d
Feb 16 11:20:13 santech kernel: [    2.419404] usb 1-9: New USB device strings: Mfr=3, Product=1, SerialNumber=2
Feb 16 11:20:13 santech kernel: [    2.419405] usb 1-9: Product: BisonCam, NB Pro
Feb 16 11:20:13 santech kernel: [    2.419406] usb 1-9: Manufacturer: Generic
Feb 16 11:20:13 santech kernel: [    2.419407] usb 1-9: SerialNumber: 200901010001
Feb 16 11:20:13 santech kernel: [    2.520705] psmouse serio2: synaptics: queried max coordinates: x [..5654], y [..4716]
Feb 16 11:20:13 santech kernel: [    2.619144] clocksource: Switched to clocksource tsc
Feb 16 11:20:13 santech kernel: [    2.639575] psmouse serio2: synaptics: queried min coordinates: x [1326..], y [1228..]
Feb 16 11:20:13 santech kernel: [    2.787921] psmouse serio2: synaptics: Touchpad model: 1, fw: 8.2, id: 0x1e2b1, caps: 0xf00123/0x840300/0x26800/0x0, board id: 3163, fw id: 1924066
Feb 16 11:20:13 santech kernel: [    2.806765] [drm] RC6 on
Feb 16 11:20:13 santech kernel: [    2.829892] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input12
Feb 16 11:20:13 santech kernel: [    9.281626] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
Feb 16 11:20:13 santech kernel: [    9.379164] random: nonblocking pool is initialized
Feb 16 11:20:13 santech kernel: [    9.441613] lp: driver loaded but no devices found
Feb 16 11:20:13 santech kernel: [    9.443897] ppdev: user-space parallel port driver
Feb 16 11:20:13 santech kernel: [    9.480688] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
Feb 16 11:20:13 santech kernel: [    9.508915] wmi: Mapper loaded
Feb 16 11:20:13 santech kernel: [    9.543233] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Feb 16 11:20:13 santech kernel: [    9.545343] mei_me 0000:00:16.0: enabling device (0000 -> 0002)
Feb 16 11:20:13 santech kernel: [    9.567184] Intel(R) Wireless WiFi driver for Linux
Feb 16 11:20:13 santech kernel: [    9.567185] Copyright(c) 2003- 2015 Intel Corporation
Feb 16 11:20:13 santech kernel: [    9.567241] iwlwifi 0000:03:00.0: enabling device (0000 -> 0002)
Feb 16 11:20:13 santech kernel: [    9.567894] AVX2 version of gcm_enc/dec engaged.
Feb 16 11:20:13 santech kernel: [    9.567895] AES CTR mode by8 optimization enabled
Feb 16 11:20:13 santech kernel: [    9.568531] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-8000C-15.ucode failed with error -2
Feb 16 11:20:13 santech kernel: [    9.568676] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-8000C-14.ucode failed with error -2
Feb 16 11:20:13 santech kernel: [    9.579620] iwlwifi 0000:03:00.0: loaded firmware version 25.30.13.0 op_mode iwlmvm
Feb 16 11:20:13 santech kernel: [    9.589374] intel_rapl: Found RAPL domain package
Feb 16 11:20:13 santech kernel: [    9.589377] intel_rapl: Found RAPL domain core
Feb 16 11:20:13 santech kernel: [    9.589379] intel_rapl: Found RAPL domain uncore
Feb 16 11:20:13 santech kernel: [    9.589381] intel_rapl: Found RAPL domain dram
Feb 16 11:20:13 santech kernel: [    9.595816] snd_hda_intel 0000:00:1f.3: enabling device (0000 -> 0002)
Feb 16 11:20:13 santech kernel: [    9.595950] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
Feb 16 11:20:13 santech kernel: [    9.597207] nvidia: module license 'NVIDIA' taints kernel.
Feb 16 11:20:13 santech kernel: [    9.597208] Disabling lock debugging due to kernel taint
Feb 16 11:20:13 santech kernel: [    9.598653] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 8260, REV=0x208
Feb 16 11:20:13 santech kernel: [    9.598727] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
Feb 16 11:20:13 santech kernel: [    9.599024] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
Feb 16 11:20:13 santech kernel: [    9.599606] iwlwifi 0000:03:00.0: can't access the RSA semaphore it is write protected
Feb 16 11:20:13 santech kernel: [    9.599879] nvidia: module verification failed: signature and/or required key missing - tainting kernel
Feb 16 11:20:13 santech kernel: [    9.622230] cfg80211: World regulatory domain updated:
Feb 16 11:20:13 santech kernel: [    9.622232] cfg80211:  DFS Master region: unset
Feb 16 11:20:13 santech kernel: [    9.622233] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Feb 16 11:20:13 santech kernel: [    9.622235] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Feb 16 11:20:13 santech kernel: [    9.622236] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Feb 16 11:20:13 santech kernel: [    9.622236] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
Feb 16 11:20:13 santech kernel: [    9.622238] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
Feb 16 11:20:13 santech kernel: [    9.622239] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
Feb 16 11:20:13 santech kernel: [    9.622240] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
Feb 16 11:20:13 santech kernel: [    9.622241] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
Feb 16 11:20:13 santech kernel: [    9.622241] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
Feb 16 11:20:13 santech kernel: [    9.630434] nvidia 0000:01:00.0: enabling device (0006 -> 0007)
Feb 16 11:20:13 santech kernel: [    9.630500] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
Feb 16 11:20:13 santech kernel: [    9.630612] [drm] Initialized nvidia-drm 0.0.0 20150116 for 0000:01:00.0 on minor 1
Feb 16 11:20:13 santech kernel: [    9.630615] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  352.63  Sat Nov  7 21:25:42 PST 2015
Feb 16 11:20:13 santech kernel: [    9.632171] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC892: line_outs=1 (0x17/0x0/0x0/0x0/0x0) type:line
Feb 16 11:20:13 santech kernel: [    9.632173] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=1 (0x14/0x0/0x0/0x0/0x0)
Feb 16 11:20:13 santech kernel: [    9.632174] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
Feb 16 11:20:13 santech kernel: [    9.632175] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
Feb 16 11:20:13 santech kernel: [    9.632176] snd_hda_codec_realtek hdaudioC0D0:    dig-out=0x1e/0x0
Feb 16 11:20:13 santech kernel: [    9.632177] snd_hda_codec_realtek hdaudioC0D0:    inputs:
Feb 16 11:20:13 santech kernel: [    9.632178] snd_hda_codec_realtek hdaudioC0D0:      Mic=0x18
Feb 16 11:20:13 santech kernel: [    9.632179] snd_hda_codec_realtek hdaudioC0D0:      Internal Mic=0x12
Feb 16 11:20:13 santech kernel: [    9.645607] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1f.3/sound/card0/input16
Feb 16 11:20:13 santech kernel: [    9.645876] input: HDA Intel PCH Line Out as /devices/pci0000:00/0000:00:1f.3/sound/card0/input17
Feb 16 11:20:13 santech kernel: [    9.645941] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1f.3/sound/card0/input18
Feb 16 11:20:13 santech kernel: [    9.646020] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input19
Feb 16 11:20:13 santech kernel: [    9.646075] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input20
Feb 16 11:20:13 santech kernel: [    9.646137] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input21
Feb 16 11:20:13 santech kernel: [    9.744974] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
Feb 16 11:20:13 santech kernel: [    9.749923] iwlwifi 0000:03:00.0 wlp3s0: renamed from wlan0
Feb 16 11:20:13 santech kernel: [    9.823342] Adding 2928124k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:2928124k SSFS
Feb 16 11:20:13 santech kernel: [    9.832951] audit: type=1400 audit(1455618013.107:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=656 comm="apparmor_parser"
Feb 16 11:20:13 santech kernel: [    9.832956] audit: type=1400 audit(1455618013.107:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=656 comm="apparmor_parser"
Feb 16 11:20:13 santech kernel: [    9.834443] audit: type=1400 audit(1455618013.111:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=656 comm="apparmor_parser"
Feb 16 11:20:13 santech kernel: [    9.834447] audit: type=1400 audit(1455618013.111:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=656 comm="apparmor_parser"
Feb 16 11:20:13 santech kernel: [    9.834450] audit: type=1400 audit(1455618013.111:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=656 comm="apparmor_parser"
Feb 16 11:20:13 santech kernel: [    9.834453] audit: type=1400 audit(1455618013.111:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=656 comm="apparmor_parser"
Feb 16 11:20:13 santech kernel: [    9.840215] audit: type=1400 audit(1455618013.115:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=656 comm="apparmor_parser"
Feb 16 11:20:13 santech kernel: [    9.840220] audit: type=1400 audit(1455618013.115:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=656 comm="apparmor_parser"
Feb 16 11:20:13 santech kernel: [    9.840223] audit: type=1400 audit(1455618013.115:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=656 comm="apparmor_parser"
Feb 16 11:20:13 santech kernel: [    9.840225] audit: type=1400 audit(1455618013.115:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=656 comm="apparmor_parser"
Feb 16 11:20:13 santech kernel: [    9.959396] cgroup: new mount options do not match the existing superblock, will be ignored
Feb 16 11:20:13 santech kernel: [   10.098260] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
Feb 16 11:20:13 santech kernel: [   10.098356] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
Feb 16 11:20:13 santech kernel: [   10.098616] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
Feb 16 11:20:13 santech kernel: [   10.099108] iwlwifi 0000:03:00.0: can't access the RSA semaphore it is write protected
Feb 16 11:20:13 santech kernel: [   10.240567] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
Feb 16 11:20:13 santech kernel: [   10.240826] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
Feb 16 11:20:13 santech kernel: [   10.241243] iwlwifi 0000:03:00.0: can't access the RSA semaphore it is write protected
Feb 16 11:20:13 santech kernel: [   10.316760] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
Feb 16 11:20:13 santech kernel: [   10.318085] IPv6: ADDRCONF(NETDEV_UP): enp2s0f1: link is not ready
Feb 16 11:20:13 santech kernel: [   10.325283] bbswitch: version 0.7
Feb 16 11:20:13 santech kernel: [   10.325288] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
Feb 16 11:20:13 santech kernel: [   10.325312] bbswitch: Found discrete VGA device 0000:01:00.0: \_SB_.PCI0.PEG0.PEGP
Feb 16 11:20:13 santech kernel: [   10.325318] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
Feb 16 11:20:13 santech kernel: [   10.325401] bbswitch: detected an Optimus _DSM function
Feb 16 11:20:13 santech kernel: [   10.325405] bbswitch: Succesfully loaded. Discrete card 0000:01:00.0 is on
Feb 16 11:20:13 santech kernel: [   10.328890] [drm] Module unloaded
Feb 16 11:20:13 santech kernel: [   10.335382] r8169 0000:02:00.1 enp2s0f1: link down
Feb 16 11:20:13 santech kernel: [   10.335425] IPv6: ADDRCONF(NETDEV_UP): enp2s0f1: link is not ready
Feb 16 11:20:13 santech kernel: [   10.374046] bbswitch: disabling discrete graphics
Feb 16 11:20:13 santech kernel: [   10.374054] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
Feb 16 11:20:13 santech kernel: [   10.423507] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
Feb 16 11:20:14 santech kernel: [   11.629293] media: Linux media interface: v0.10
Feb 16 11:20:14 santech kernel: [   11.632327] Linux video capture interface: v2.00
Feb 16 11:20:14 santech kernel: [   11.632350] Bluetooth: Core ver 2.20
Feb 16 11:20:14 santech kernel: [   11.632365] NET: Registered protocol family 31
Feb 16 11:20:14 santech kernel: [   11.632366] Bluetooth: HCI device and connection manager initialized
Feb 16 11:20:14 santech kernel: [   11.632369] Bluetooth: HCI socket layer initialized
Feb 16 11:20:14 santech kernel: [   11.632371] Bluetooth: L2CAP socket layer initialized
Feb 16 11:20:14 santech kernel: [   11.632374] Bluetooth: SCO socket layer initialized
Feb 16 11:20:15 santech kernel: [   11.717603] usbcore: registered new interface driver btusb
Feb 16 11:20:15 santech kernel: [   11.718501] Bluetooth: hci0: Bootloader revision 0.0 build 2 week 52 2014
Feb 16 11:20:15 santech kernel: [   11.723503] Bluetooth: hci0: Device revision is 5
Feb 16 11:20:15 santech kernel: [   11.723504] Bluetooth: hci0: Secure boot is enabled
Feb 16 11:20:15 santech kernel: [   11.723505] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
Feb 16 11:20:15 santech kernel: [   11.725277] uvcvideo: Found UVC 1.00 device BisonCam, NB Pro (5986:066d)
Feb 16 11:20:15 santech kernel: [   11.725684] Bluetooth: hci0: Found device firmware: intel/ibt-11-5.sfi
Feb 16 11:20:15 santech kernel: [   11.727644] input: BisonCam, NB Pro as /devices/pci0000:00/0000:00:14.0/usb1/1-9/1-9:1.0/input/input22
Feb 16 11:20:15 santech kernel: [   11.727788] usbcore: registered new interface driver uvcvideo
Feb 16 11:20:15 santech kernel: [   11.727790] USB Video Class driver (1.1.1)
Feb 16 11:20:15 santech kernel: [   12.055173] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Feb 16 11:20:15 santech kernel: [   12.055176] Bluetooth: BNEP filters: protocol multicast
Feb 16 11:20:15 santech kernel: [   12.055179] Bluetooth: BNEP socket layer initialized
Feb 16 11:20:15 santech kernel: [   12.500996] Non-volatile memory driver v1.3
Feb 16 11:20:15 santech kernel: [   12.636887] ahci 0000:00:17.0: port does not support device sleep
Feb 16 11:20:15 santech kernel: [   12.668328] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
Feb 16 11:20:15 santech kernel: [   12.678492] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
Feb 16 11:20:16 santech kernel: [   13.104257] Bluetooth: hci0: Waiting for firmware download to complete
Feb 16 11:20:16 santech kernel: [   13.104278] Bluetooth: hci0: Firmware loaded in 1354204 usecs
Feb 16 11:20:16 santech kernel: [   13.104321] Bluetooth: hci0: Waiting for device to boot
Feb 16 11:20:16 santech kernel: [   13.116281] Bluetooth: hci0: Device booted in 11694 usecs
Feb 16 11:20:16 santech kernel: [   13.116430] Bluetooth: hci0: Found Intel DDC parameters: intel/ibt-11-5.ddc
Feb 16 11:20:16 santech kernel: [   13.118307] Bluetooth: hci0: Applying Intel DDC parameters completed
Feb 16 11:20:16 santech kernel: [   13.173905] Bluetooth: RFCOMM TTY layer initialized
Feb 16 11:20:16 santech kernel: [   13.173911] Bluetooth: RFCOMM socket layer initialized
Feb 16 11:20:16 santech kernel: [   13.173914] Bluetooth: RFCOMM ver 1.11
Feb 16 11:20:16 santech kernel: [   13.520800] wlp3s0: authenticate with 30:46:9a:83:e7:22
Feb 16 11:20:16 santech kernel: [   13.530539] wlp3s0: send auth to 30:46:9a:83:e7:22 (try 1/3)
Feb 16 11:20:16 santech kernel: [   13.687872] wlp3s0: send auth to 30:46:9a:83:e7:22 (try 2/3)
Feb 16 11:20:16 santech kernel: [   13.700421] wlp3s0: authenticated
Feb 16 11:20:16 santech kernel: [   13.700700] wlp3s0: associate with 30:46:9a:83:e7:22 (try 1/3)
Feb 16 11:20:16 santech kernel: [   13.705171] wlp3s0: RX AssocResp from 30:46:9a:83:e7:22 (capab=0x411 status=0 aid=3)
Feb 16 11:20:16 santech kernel: [   13.709135] wlp3s0: associated
Feb 16 11:20:16 santech kernel: [   13.709174] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
Feb 16 11:20:19 santech gnome-session[2009]: Entering running state
Feb 16 11:20:25 santech kernel: [   22.282184] Valid eCryptfs headers not found in file header region or xattr region, inode 4592922
Feb 16 11:20:25 santech kernel: [   22.282310] Valid eCryptfs headers not found in file header region or xattr region, inode 4592924
Feb 16 11:20:25 santech kernel: [   22.282398] Valid eCryptfs headers not found in file header region or xattr region, inode 4592925
Feb 16 11:20:25 santech kernel: [   22.283561] Valid eCryptfs headers not found in file header region or xattr region, inode 4592943
Feb 16 11:20:25 santech kernel: [   22.283645] Valid eCryptfs headers not found in file header region or xattr region, inode 4592932
Feb 16 11:20:25 santech kernel: [   22.283778] Valid eCryptfs headers not found in file header region or xattr region, inode 4592934
Feb 16 11:20:25 santech kernel: [   22.290948] Valid eCryptfs headers not found in file header region or xattr region, inode 4592923
Feb 16 11:20:25 santech kernel: [   22.301004] Valid eCryptfs headers not found in file header region or xattr region, inode 4592927
Feb 16 11:20:25 santech kernel: [   22.301067] Valid eCryptfs headers not found in file header region or xattr region, inode 4592948
Feb 16 11:20:25 santech kernel: [   22.301213] Valid eCryptfs headers not found in file header region or xattr region, inode 4592951
Feb 16 11:20:25 santech kernel: [   22.303753] Valid eCryptfs headers not found in file header region or xattr region, inode 4592936
Feb 16 11:20:25 santech kernel: [   22.394285] Valid eCryptfs headers not found in file header region or xattr region, inode 4592923
Feb 16 11:20:27 santech kernel: [   24.294207] Valid eCryptfs headers not found in file header region or xattr region, inode 4592923
Feb 16 11:20:27 santech kernel: [   24.294317] Valid eCryptfs headers not found in file header region or xattr region, inode 4592926
Feb 16 11:20:27 santech kernel: [   24.294439] Valid eCryptfs headers not found in file header region or xattr region, inode 4592927
Feb 16 11:20:27 santech kernel: [   24.294536] Valid eCryptfs headers not found in file header region or xattr region, inode 4592928
Feb 16 11:20:27 santech kernel: [   24.294650] Valid eCryptfs headers not found in file header region or xattr region, inode 4592929
Feb 16 11:20:27 santech kernel: [   24.294750] Valid eCryptfs headers not found in file header region or xattr region, inode 4592930
Feb 16 11:20:27 santech kernel: [   24.295164] Valid eCryptfs headers not found in file header region or xattr region, inode 4592935
Feb 16 11:20:27 santech kernel: [   24.295245] Valid eCryptfs headers not found in file header region or xattr region, inode 4592936
Feb 16 11:20:27 santech kernel: [   24.298450] Valid eCryptfs headers not found in file header region or xattr region, inode 4592938
Feb 16 11:20:27 santech kernel: [   24.303429] Valid eCryptfs headers not found in file header region or xattr region, inode 4592941
Feb 16 11:20:27 santech kernel: [   24.303536] Valid eCryptfs headers not found in file header region or xattr region, inode 4592942
Feb 16 11:20:27 santech kernel: [   24.303621] Valid eCryptfs headers not found in file header region or xattr region, inode 4592943
Feb 16 11:20:27 santech kernel: [   24.303757] Valid eCryptfs headers not found in file header region or xattr region, inode 4592945
Feb 16 11:20:27 santech kernel: [   24.303848] Valid eCryptfs headers not found in file header region or xattr region, inode 4592946
Feb 16 11:20:27 santech kernel: [   24.303936] Valid eCryptfs headers not found in file header region or xattr region, inode 4592947
Feb 16 11:20:27 santech kernel: [   24.304090] Valid eCryptfs headers not found in file header region or xattr region, inode 4592950
Feb 16 11:20:27 santech kernel: [   24.304936] Valid eCryptfs headers not found in file header region or xattr region, inode 4592953
Feb 16 11:20:27 santech kernel: [   24.305028] Valid eCryptfs headers not found in file header region or xattr region, inode 4592954
Feb 16 11:25:00 santech kernel: [  297.954407] Valid eCryptfs headers not found in file header region or xattr region, inode 3288067
Feb 16 11:25:57 santech kernel: [  354.949213] Valid eCryptfs headers not found in file header region or xattr region, inode 3149007
Feb 16 11:32:04 santech kernel: [  722.237098] wlp3s0: authenticate with 30:46:9a:83:e7:22
Feb 16 11:32:04 santech kernel: [  722.244356] wlp3s0: send auth to 30:46:9a:83:e7:22 (try 1/3)
Feb 16 11:32:04 santech kernel: [  722.248275] wlp3s0: authenticated
Feb 16 11:32:04 santech kernel: [  722.251135] wlp3s0: associate with 30:46:9a:83:e7:22 (try 1/3)
Feb 16 11:32:04 santech kernel: [  722.255120] wlp3s0: RX AssocResp from 30:46:9a:83:e7:22 (capab=0x411 status=0 aid=3)
Feb 16 11:32:04 santech kernel: [  722.257567] wlp3s0: associated
Feb 16 11:33:06 santech kernel: [  784.241597] wlp3s0: authenticate with 30:46:9a:83:e7:22
Feb 16 11:33:06 santech kernel: [  784.248869] wlp3s0: send auth to 30:46:9a:83:e7:22 (try 1/3)
Feb 16 11:33:06 santech kernel: [  784.252225] wlp3s0: authenticated
Feb 16 11:33:06 santech kernel: [  784.255275] wlp3s0: associate with 30:46:9a:83:e7:22 (try 1/3)
Feb 16 11:33:06 santech kernel: [  784.259522] wlp3s0: RX AssocResp from 30:46:9a:83:e7:22 (capab=0x411 status=0 aid=3)
Feb 16 11:33:06 santech kernel: [  784.261900] wlp3s0: associated
Feb 16 11:57:32 santech kernel: [ 2249.759505] wlp3s0: deauthenticated from 30:46:9a:83:e7:22 (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
Feb 16 11:57:32 santech kernel: [ 2249.771198] wlp3s0: authenticate with 30:46:9a:83:e7:22
Feb 16 11:57:32 santech kernel: [ 2249.777788] wlp3s0: send auth to 30:46:9a:83:e7:22 (try 1/3)
Feb 16 11:57:32 santech kernel: [ 2249.779597] wlp3s0: authenticated
Feb 16 11:57:32 santech kernel: [ 2249.783488] wlp3s0: associate with 30:46:9a:83:e7:22 (try 1/3)
Feb 16 11:57:32 santech kernel: [ 2249.787485] wlp3s0: RX AssocResp from 30:46:9a:83:e7:22 (capab=0x411 status=0 aid=3)
Feb 16 11:57:32 santech kernel: [ 2249.789677] wlp3s0: associated
Feb 16 11:58:31 santech kernel: [ 2308.774611] wlp3s0: deauthenticated from 30:46:9a:83:e7:22 (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
Feb 16 11:58:34 santech kernel: [ 2312.189609] wlp3s0: authenticate with 30:46:9a:83:e7:22
Feb 16 11:58:34 santech kernel: [ 2312.196946] wlp3s0: send auth to 30:46:9a:83:e7:22 (try 1/3)
Feb 16 11:58:34 santech kernel: [ 2312.300860] wlp3s0: send auth to 30:46:9a:83:e7:22 (try 2/3)
Feb 16 11:58:34 santech kernel: [ 2312.302915] wlp3s0: authenticated
Feb 16 11:58:34 santech kernel: [ 2312.307166] wlp3s0: associate with 30:46:9a:83:e7:22 (try 1/3)
Feb 16 11:58:34 santech kernel: [ 2312.313444] wlp3s0: RX AssocResp from 30:46:9a:83:e7:22 (capab=0x411 status=0 aid=3)
Feb 16 11:58:34 santech kernel: [ 2312.317679] wlp3s0: associated
Feb 16 12:07:06 santech kernel: [ 2823.987623] wlp3s0: authenticate with 30:46:9a:83:e7:22
Feb 16 12:07:06 santech kernel: [ 2823.995006] wlp3s0: send auth to 30:46:9a:83:e7:22 (try 1/3)
Feb 16 12:07:06 santech kernel: [ 2824.102618] wlp3s0: send auth to 30:46:9a:83:e7:22 (try 2/3)
Feb 16 12:07:06 santech kernel: [ 2824.105482] wlp3s0: authenticated
Feb 16 12:07:06 santech kernel: [ 2824.109012] wlp3s0: associate with 30:46:9a:83:e7:22 (try 1/3)
Feb 16 12:07:06 santech kernel: [ 2824.113235] wlp3s0: RX AssocResp from 30:46:9a:83:e7:22 (capab=0x411 status=0 aid=3)
Feb 16 12:07:06 santech kernel: [ 2824.115578] wlp3s0: associated
Feb 16 12:28:19 santech kernel: [ 4096.892422] wlp3s0: authenticate with 30:46:9a:83:e7:22
Feb 16 12:28:19 santech kernel: [ 4096.899724] wlp3s0: send auth to 30:46:9a:83:e7:22 (try 1/3)
Feb 16 12:28:19 santech kernel: [ 4097.004099] wlp3s0: send auth to 30:46:9a:83:e7:22 (try 2/3)
Feb 16 12:28:19 santech kernel: [ 4097.006112] wlp3s0: authenticated
Feb 16 12:28:19 santech kernel: [ 4097.006377] wlp3s0: associate with 30:46:9a:83:e7:22 (try 1/3)
Feb 16 12:28:19 santech kernel: [ 4097.011796] wlp3s0: RX AssocResp from 30:46:9a:83:e7:22 (capab=0x411 status=0 aid=3)
Feb 16 12:28:19 santech kernel: [ 4097.014205] wlp3s0: associated
Feb 17 09:15:46 santech kernel: [    0.000000] Initializing cgroup subsys cpuset
Feb 17 09:15:46 santech kernel: [    0.000000] Initializing cgroup subsys cpu
Feb 17 09:15:46 santech kernel: [    0.000000] Initializing cgroup subsys cpuacct
Feb 17 09:15:46 santech kernel: [    0.000000] Linux version 4.2.0-27-generic (buildd@lgw01-12) (gcc version 5.2.1 20151010 (Ubuntu 5.2.1-22ubuntu2) ) #32-Ubuntu SMP Fri Jan 22 04:49:08 UTC 2016 (Ubuntu 4.2.0-27.32-generic 4.2.8-ckt1)
...

```

```

[    10.357] 
X.Org X Server 1.17.2
Release Date: 2015-06-16
[    10.357] X Protocol Version 11, Revision 0
[    10.357] Build Operating System: Linux 3.13.0-68-generic x86_64 Ubuntu
[    10.357] Current Operating System: Linux santech 4.2.0-27-generic #32-Ubuntu SMP Fri Jan 22 04:49:08 UTC 2016 x86_64
[    10.357] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-27-generic.efi.signed root=UUID=7b8f97f2-410e-4e94-bba2-4f633f7e1f9e ro quiet splash vt.handoff=7
[    10.357] Build Date: 12 November 2015  05:33:29PM
[    10.357] xorg-server 2:1.17.2-1ubuntu9.1 (For technical support please see http://www.ubuntu.com/support) 
[    10.357] Current version of pixman: 0.32.6
[    10.357]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    10.357] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    10.357] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Feb 19 22:33:00 2016
[    10.358] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    10.358] (==) No Layout section.  Using the first Screen section.
[    10.358] (==) No screen section available. Using defaults.
[    10.358] (**) |-->Screen "Default Screen Section" (0)
[    10.358] (**) |   |-->Monitor "<default monitor>"
[    10.358] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    10.358] (==) Automatically adding devices
[    10.358] (==) Automatically enabling devices
[    10.358] (==) Automatically adding GPU devices
[    10.358] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    10.358]     Entry deleted from font path.
[    10.358] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    10.358]     Entry deleted from font path.
[    10.358] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    10.358]     Entry deleted from font path.
[    10.358] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    10.358]     Entry deleted from font path.
[    10.358] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    10.358]     Entry deleted from font path.
[    10.358] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    10.358] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    10.358] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    10.358] (II) Loader magic: 0x559f1c9d4d40
[    10.358] (II) Module ABI versions:
[    10.358]     X.Org ANSI C Emulation: 0.4
[    10.358]     X.Org Video Driver: 19.0
[    10.358]     X.Org XInput driver : 21.0
[    10.358]     X.Org Server Extension : 9.0
[    10.359] (II) xfree86: Adding drm device (/dev/dri/card0)
[    11.515] (--) PCI:*(0:0:2:0) 8086:191b:1558:6540 rev 6, Mem @ 0xdd000000/16777216, 0xa0000000/536870912, I/O @ 0x0000f000/64
[    11.515] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    11.515] (II) "glx" will be loaded by default.
[    11.515] (II) LoadModule: "glx"
[    11.515] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    11.522] (II) Module glx: vendor="X.Org Foundation"
[    11.522]     compiled for 1.17.2, module version = 1.0.0
[    11.522]     ABI class: X.Org Server Extension, version 9.0
[    11.522] (==) AIGLX enabled
[    11.522] (==) Matched intel as autoconfigured driver 0
[    11.522] (==) Matched intel as autoconfigured driver 1
[    11.522] (==) Matched modesetting as autoconfigured driver 2
[    11.522] (==) Matched fbdev as autoconfigured driver 3
[    11.522] (==) Matched vesa as autoconfigured driver 4
[    11.522] (==) Assigned the driver to the xf86ConfigLayout
[    11.522] (II) LoadModule: "intel"
[    11.522] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    11.523] (II) Module intel: vendor="X.Org Foundation"
[    11.523]     compiled for 1.17.2, module version = 2.99.917
[    11.523]     Module class: X.Org Video Driver
[    11.523]     ABI class: X.Org Video Driver, version 19.0
[    11.523] (II) LoadModule: "modesetting"
[    11.523] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    11.523] (II) Module modesetting: vendor="X.Org Foundation"
[    11.523]     compiled for 1.17.2, module version = 1.17.2
[    11.523]     Module class: X.Org Video Driver
[    11.523]     ABI class: X.Org Video Driver, version 19.0
[    11.523] (II) LoadModule: "fbdev"
[    11.523] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    11.523] (II) Module fbdev: vendor="X.Org Foundation"
[    11.523]     compiled for 1.17.1, module version = 0.4.4
[    11.523]     Module class: X.Org Video Driver
[    11.523]     ABI class: X.Org Video Driver, version 19.0
[    11.523] (II) LoadModule: "vesa"
[    11.523] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    11.523] (II) Module vesa: vendor="X.Org Foundation"
[    11.523]     compiled for 1.17.1, module version = 2.3.4
[    11.523]     Module class: X.Org Video Driver
[    11.523]     ABI class: X.Org Video Driver, version 19.0
[    11.523] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    11.523] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    11.523] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    11.523] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    11.523] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    11.523] (II) FBDEV: driver for framebuffer: fbdev
[    11.523] (II) VESA: driver for VESA chipsets: vesa
[    11.523] (++) using VT number 7

[    11.523] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20150522
[    11.524] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git20150808-0ubuntu4 (Robert Ancell <robert.ancell@canonical.com>)
[    11.524] (II) intel(0): SNA compiled for use with valgrind
[    11.524] (WW) Falling back to old probe method for modesetting
[    11.524] (WW) Falling back to old probe method for fbdev
[    11.524] (II) Loading sub module "fbdevhw"
[    11.524] (II) LoadModule: "fbdevhw"
[    11.524] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    11.524] (II) Module fbdevhw: vendor="X.Org Foundation"
[    11.524]     compiled for 1.17.2, module version = 0.0.2
[    11.524]     ABI class: X.Org Video Driver, version 19.0
[    11.524] (WW) Falling back to old probe method for vesa
[    11.524] (--) intel(0): gen9 engineering sample
[    11.524] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2; using a maximum of 4 threads
[    11.524] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    11.524] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    11.524] (==) intel(0): RGB weight 888
[    11.524] (==) intel(0): Default visual is TrueColor
[    11.524] (II) intel(0): Output eDP1 has no monitor section
[    11.536] (--) intel(0): Found backlight control interface intel_backlight (type 'raw') for output eDP1
[    11.536] (II) intel(0): Enabled output eDP1
[    11.536] (--) intel(0): Using a maximum size of 256x256 for hardware cursors
[    11.536] (II) intel(0): Output VIRTUAL1 has no monitor section
[    11.536] (II) intel(0): Enabled output VIRTUAL1
[    11.536] (--) intel(0): Output eDP1 using initial mode 1920x1080 on pipe 0
[    11.536] (==) intel(0): TearFree disabled
[    11.536] (==) intel(0): DPI set to (96, 96)
[    11.536] (II) Loading sub module "dri2"
[    11.536] (II) LoadModule: "dri2"
[    11.536] (II) Module "dri2" already built-in
[    11.536] (II) Loading sub module "present"
[    11.536] (II) LoadModule: "present"
[    11.536] (II) Module "present" already built-in
[    11.536] (II) UnloadModule: "modesetting"
[    11.536] (II) Unloading modesetting
[    11.536] (II) UnloadModule: "fbdev"
[    11.536] (II) Unloading fbdev
[    11.536] (II) UnloadSubModule: "fbdevhw"
[    11.536] (II) Unloading fbdevhw
[    11.536] (II) UnloadModule: "vesa"
[    11.536] (II) Unloading vesa
[    11.536] (==) Depth 24 pixmap format is 32 bpp
[    11.536] (II) intel(0): SNA initialized with generic backend
[    11.536] (==) intel(0): Backing store enabled
[    11.536] (==) intel(0): Silken mouse enabled
[    11.536] (II) intel(0): HW Cursor enabled
[    11.536] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    11.536] (==) intel(0): DPMS enabled
[    11.536] (==) intel(0): Display hotplug detection enabled
[    11.537] (II) intel(0): Textured video not supported on this hardware or backend
[    11.537] (II) intel(0): [DRI2] Setup complete
[    11.537] (II) intel(0): [DRI2]   DRI driver: i965
[    11.537] (II) intel(0): [DRI2]   VDPAU driver: va_gl
[    11.537] (II) intel(0): direct rendering: DRI2 enabled
[    11.537] (II) intel(0): hardware support for Present enabled
[    11.537] (--) RandR disabled
[    11.539] (II) SELinux: Disabled on system
[    11.546] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    11.546] (II) AIGLX: enabled GLX_ARB_create_context
[    11.546] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    11.546] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    11.546] (II) AIGLX: enabled GLX_INTEL_swap_event
[    11.546] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    11.546] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    11.546] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    11.546] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    11.546] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[    11.546] (II) AIGLX: Loaded and initialized i965
[    11.546] (II) GLX: Initialized DRI2 GL provider for screen 0
[    11.549] (II) intel(0): switch to mode 1920x1080@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[    11.549] (II) intel(0): Setting screen physical size to 508 x 285
[    11.553] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    11.559] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    11.559] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    11.559] (II) LoadModule: "evdev"
[    11.559] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.560] (II) Module evdev: vendor="X.Org Foundation"
[    11.560]     compiled for 1.17.1, module version = 2.9.2
[    11.560]     Module class: X.Org XInput Driver
[    11.560]     ABI class: X.Org XInput driver, version 21.0
[    11.560] (II) Using input driver 'evdev' for 'Power Button'
[    11.560] (**) Power Button: always reports core events
[    11.560] (**) evdev: Power Button: Device: "/dev/input/event3"
[    11.560] (--) evdev: Power Button: Vendor 0 Product 0x1
[    11.560] (--) evdev: Power Button: Found keys
[    11.560] (II) evdev: Power Button: Configuring as keyboard
[    11.560] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    11.560] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    11.560] (**) Option "xkb_rules" "evdev"
[    11.560] (**) Option "xkb_model" "pc105"
[    11.560] (**) Option "xkb_layout" "us"
[    11.560] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    11.560] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    11.560] (II) Using input driver 'evdev' for 'Video Bus'
[    11.560] (**) Video Bus: always reports core events
[    11.560] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    11.560] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    11.560] (--) evdev: Video Bus: Found keys
[    11.560] (II) evdev: Video Bus: Configuring as keyboard
[    11.560] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input10/event5"
[    11.560] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    11.560] (**) Option "xkb_rules" "evdev"
[    11.560] (**) Option "xkb_model" "pc105"
[    11.560] (**) Option "xkb_layout" "us"
[    11.560] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    11.560] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    11.560] (II) Using input driver 'evdev' for 'Video Bus'
[    11.560] (**) Video Bus: always reports core events
[    11.560] (**) evdev: Video Bus: Device: "/dev/input/event6"
[    11.561] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    11.561] (--) evdev: Video Bus: Found keys
[    11.561] (II) evdev: Video Bus: Configuring as keyboard
[    11.561] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:12/LNXVIDEO:01/input/input11/event6"
[    11.561] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    11.561] (**) Option "xkb_rules" "evdev"
[    11.561] (**) Option "xkb_model" "pc105"
[    11.561] (**) Option "xkb_layout" "us"
[    11.561] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    11.561] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    11.561] (II) Using input driver 'evdev' for 'Power Button'
[    11.561] (**) Power Button: always reports core events
[    11.561] (**) evdev: Power Button: Device: "/dev/input/event0"
[    11.561] (--) evdev: Power Button: Vendor 0 Product 0x1
[    11.561] (--) evdev: Power Button: Found keys
[    11.561] (II) evdev: Power Button: Configuring as keyboard
[    11.561] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    11.561] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[    11.561] (**) Option "xkb_rules" "evdev"
[    11.561] (**) Option "xkb_model" "pc105"
[    11.561] (**) Option "xkb_layout" "us"
[    11.561] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[    11.561] (II) No input driver specified, ignoring this device.
[    11.561] (II) This device may have been added with another device file.
[    11.561] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    11.561] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    11.561] (II) Using input driver 'evdev' for 'Sleep Button'
[    11.561] (**) Sleep Button: always reports core events
[    11.561] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    11.561] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    11.561] (--) evdev: Sleep Button: Found keys
[    11.561] (II) evdev: Sleep Button: Configuring as keyboard
[    11.561] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1"
[    11.561] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 10)
[    11.561] (**) Option "xkb_rules" "evdev"
[    11.561] (**) Option "xkb_model" "pc105"
[    11.561] (**) Option "xkb_layout" "us"
[    11.562] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/event7)
[    11.562] (**) Logitech USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    11.562] (II) Using input driver 'evdev' for 'Logitech USB Optical Mouse'
[    11.562] (**) Logitech USB Optical Mouse: always reports core events
[    11.562] (**) evdev: Logitech USB Optical Mouse: Device: "/dev/input/event7"
[    11.572] (--) evdev: Logitech USB Optical Mouse: Vendor 0x46d Product 0xc06c
[    11.572] (--) evdev: Logitech USB Optical Mouse: Found 3 mouse buttons
[    11.572] (--) evdev: Logitech USB Optical Mouse: Found scroll wheel(s)
[    11.572] (--) evdev: Logitech USB Optical Mouse: Found relative axes
[    11.572] (--) evdev: Logitech USB Optical Mouse: Found x and y relative axes
[    11.572] (II) evdev: Logitech USB Optical Mouse: Configuring as mouse
[    11.572] (II) evdev: Logitech USB Optical Mouse: Adding scrollwheel support
[    11.572] (**) evdev: Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    11.572] (**) evdev: Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    11.572] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.0/0003:046D:C06C.0001/input/input13/event7"
[    11.572] (II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE, id 11)
[    11.572] (II) evdev: Logitech USB Optical Mouse: initialized for relative axes.
[    11.572] (**) Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
[    11.572] (**) Logitech USB Optical Mouse: (accel) acceleration profile 0
[    11.572] (**) Logitech USB Optical Mouse: (accel) acceleration factor: 2.000
[    11.572] (**) Logitech USB Optical Mouse: (accel) acceleration threshold: 4
[    11.572] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/mouse0)
[    11.572] (II) No input driver specified, ignoring this device.
[    11.572] (II) This device may have been added with another device file.
[    11.572] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event9)
[    11.572] (II) No input driver specified, ignoring this device.
[    11.572] (II) This device may have been added with another device file.
[    11.573] (II) config/udev: Adding input device HDA Intel PCH Line Out (/dev/input/event10)
[    11.573] (II) No input driver specified, ignoring this device.
[    11.573] (II) This device may have been added with another device file.
[    11.573] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event11)
[    11.573] (II) No input driver specified, ignoring this device.
[    11.573] (II) This device may have been added with another device file.
[    11.573] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event12)
[    11.573] (II) No input driver specified, ignoring this device.
[    11.573] (II) This device may have been added with another device file.
[    11.573] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=7 (/dev/input/event13)
[    11.573] (II) No input driver specified, ignoring this device.
[    11.573] (II) This device may have been added with another device file.
[    11.573] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=8 (/dev/input/event14)
[    11.573] (II) No input driver specified, ignoring this device.
[    11.573] (II) This device may have been added with another device file.
[    11.573] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    11.573] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    11.573] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    11.573] (**) AT Translated Set 2 keyboard: always reports core events
[    11.573] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    11.573] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    11.573] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    11.573] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    11.573] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    11.573] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[    11.573] (**) Option "xkb_rules" "evdev"
[    11.573] (**) Option "xkb_model" "pc105"
[    11.573] (**) Option "xkb_layout" "us"
[    11.574] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event8)
[    11.574] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    11.574] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    11.574] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    11.574] (II) LoadModule: "synaptics"
[    11.574] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    11.574] (II) Module synaptics: vendor="X.Org Foundation"
[    11.574]     compiled for 1.17.1, module version = 1.8.2
[    11.574]     Module class: X.Org XInput Driver
[    11.574]     ABI class: X.Org XInput driver, version 21.0
[    11.574] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    11.574] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    11.574] (**) Option "Device" "/dev/input/event8"
[    11.608] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1326 - 5654 (res 40)
[    11.608] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1228 - 4716 (res 59)
[    11.608] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    11.608] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    11.608] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    11.608] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    11.608] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    11.608] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    11.648] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input12/event8"
[    11.648] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 13)
[    11.648] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    11.648] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    11.648] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.036
[    11.648] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    11.648] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    11.648] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    11.648] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    11.648] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    11.648] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    11.648] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    11.653] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/mouse0)
[    11.653] (II) No input driver specified, ignoring this device.
[    11.653] (II) This device may have been added with another device file.
[    11.653] (WW) config/udev: device Logitech USB Optical Mouse already added. Ignoring.
[    11.653] (II) config/udev: Adding input device BisonCam, NB Pro (/dev/input/event15)
[    11.653] (**) BisonCam, NB Pro: Applying InputClass "evdev keyboard catchall"
[    11.653] (II) Using input driver 'evdev' for 'BisonCam, NB Pro'
[    11.653] (**) BisonCam, NB Pro: always reports core events
[    11.653] (**) evdev: BisonCam, NB Pro: Device: "/dev/input/event15"
[    11.653] (--) evdev: BisonCam, NB Pro: Vendor 0x5986 Product 0x66d
[    11.653] (--) evdev: BisonCam, NB Pro: Found keys
[    11.653] (II) evdev: BisonCam, NB Pro: Configuring as keyboard
[    11.653] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-9/1-9:1.0/input/input22/event15"
[    11.653] (II) XINPUT: Adding extended input device "BisonCam, NB Pro" (type: KEYBOARD, id 14)
[    11.653] (**) Option "xkb_rules" "evdev"
[    11.653] (**) Option "xkb_model" "pc105"
[    11.653] (**) Option "xkb_layout" "us"
[    11.654] (WW) Option "xkb_variant" requires a string value
[    11.654] (WW) Option "xkb_options" requires a string value
[    11.968] (II) intel(0): EDID vendor "LGD", prod id 1132
[    11.968] (II) intel(0): Printing DDC gathered Modelines:
[    11.968] (II) intel(0): Modeline "1920x1080"x0.0  138.70  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.7 kHz eP)
[    17.447] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    17.871] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    17.880] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    18.106] (II) XKB: reuse xkmfile /var/lib/xkb/server-7C75F152E85183199599C3E0B919739C0EE668AA.xkm

```

This is the output of **lshw**, which I get when I run with 'nomodeset':

```

dario@santech:~$ sudo lshw
[sudo] password for dario: 
santech                   
    description: Computer
    width: 64 bits
    capabilities: smbios-3.0 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 7806MiB
     *-cpu
          product: Intel(R) Core(TM) i7-6700HQ CPU @ 2.60GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 3101MHz
          capacity: 3500MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch ida arat epb pln pts dtherm hwp hwp_noitfy hwp_act_window hwp_epp intel_pt tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 erms invpcid rtm mpx rdseed adx smap clflushopt xsaveopt xsavec xgetbv1 cpufreq
     *-pci
          description: Host bridge
          product: Sky Lake Host Bridge/DRAM Registers
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Sky Lake PCIe Controller (x16)
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:122 ioport:e000(size=4096) memory:de000000-df0fffff ioport:c0000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: GM204M [GeForce GTX 970M]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:de000000-deffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:df000000-df07ffff
        *-display UNCLAIMED
             description: VGA compatible controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pciexpress msi pm vga_controller bus_master cap_list
             configuration: latency=0
             resources: memory:dd000000-ddffffff memory:a0000000-bfffffff ioport:f000(size=64)
        *-usb
             description: USB controller
             product: Sunrise Point-H USB 3.0 xHCI Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 31
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:123 memory:df310000-df31ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.2.0-27-generic xhci-hcd
                physical id: 0
                bus info: usb@2
                logical name: usb2
                version: 4.02
                capabilities: usb-3.00
                configuration: driver=hub slots=8 speed=5000Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.2.0-27-generic xhci-hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.02
                capabilities: usb-2.00
                configuration: driver=hub slots=16 speed=480Mbit/s
              *-usb:0
                   description: Mouse
                   product: USB Optical Mouse
                   vendor: Logitech
                   physical id: 4
                   bus info: usb@1:4
                   version: 63.00
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=1Mbit/s
              *-usb:1 UNCLAIMED
                   description: Generic USB device
                   product: EgisTec_ES603
                   vendor: EgisTec
                   physical id: 7
                   bus info: usb@1:7
                   version: 2.00
                   capabilities: usb-1.10
                   configuration: maxpower=100mA speed=12Mbit/s
              *-usb:2
                   description: Bluetooth wireless interface
                   vendor: Intel Corp.
                   physical id: 8
                   bus info: usb@1:8
                   version: 0.01
                   capabilities: bluetooth usb-2.00
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
              *-usb:3
                   description: Video
                   product: BisonCam, NB Pro
                   vendor: Generic
                   physical id: 9
                   bus info: usb@1:9
                   version: 6.05
                   serial: 200901010001
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
        *-generic UNCLAIMED
             description: Signal processing controller
             product: Sunrise Point-H Thermal subsystem
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 31
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi cap_list
             configuration: latency=0
             resources: memory:df32e000-df32efff
        *-communication
             description: Communication controller
             product: Sunrise Point-H CSME HECI #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 31
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:127 memory:df32d000-df32dfff
        *-storage
             description: SATA controller
             product: Sunrise Point-H SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: 31
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:125 memory:df328000-df329fff memory:df32c000-df32c0ff ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memory:df32b000-df32b7ff
        *-pci:1
             description: PCI bridge
             product: Sunrise Point-H PCI Express Root Port #5
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:d000(size=4096) memory:df200000-df2fffff
           *-generic
                description: Unassigned class
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom
                configuration: driver=rtsx_pci latency=0
                resources: irq:124 memory:df215000-df215fff memory:df200000-df20ffff
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0.1
                bus info: pci@0000:02:00.1
                logical name: enp2s0f1
                version: 12
                serial: 80:fa:5b:22:50:5f
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8411-2_0.0.1 07/08/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:126 ioport:d000(size=256) memory:df214000-df214fff memory:df210000-df213fff
        *-pci:2
             description: PCI bridge
             product: Sunrise Point-H PCI Express Root Port #6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 memory:df100000-df1fffff
           *-network
                description: Wireless interface
                product: Wireless 8260
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlp3s0
                version: 3a
                serial: a4:34:d9:56:2d:81
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=4.2.0-27-generic firmware=25.30.13.0 ip=192.168.1.8 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
                resources: irq:128 memory:df100000-df101fff
        *-isa
             description: ISA bridge
             product: Sunrise Point-H LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 31
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-memory UNCLAIMED
             description: Memory controller
             product: Sunrise Point-H PMC
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 31
             width: 32 bits
             clock: 33MHz (30.3ns)
             configuration: latency=0
             resources: memory:df324000-df327fff
        *-multimedia
             description: Audio device
             product: Sunrise Point-H HD Audio
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 31
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:129 memory:df320000-df323fff memory:df300000-df30ffff
        *-serial UNCLAIMED
             description: SMBus
             product: Sunrise Point-H SMBus
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 31
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:df32a000-df32a0ff ioport:f040(size=32)
     *-scsi
          physical id: 2
          logical name: scsi3
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Samsung SSD 850
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sda
             version: 1B6Q
             serial: S21JNXAG731055Y
             size: 465GiB (500GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=9ff2c670-30a0-4b71-a88e-c17034bab62e logicalsectorsize=512 sectorsize=512
           *-volume:0
                description: Windows NTFS volume
                vendor: Windows
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: e033-dea0
                size: 448MiB
                capacity: 449MiB
                capabilities: boot precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2016-01-14 12:32:08 filesystem=ntfs label=Ripristino modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:1
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 2
                bus info: scsi@3:0.0.0,2
                logical name: /dev/sda2
                logical name: /boot/efi
                version: FAT32
                serial: b434-4ab1
                size: 92MiB
                capacity: 98MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro name=EFI System Partition state=mounted
           *-volume:2
                description: reserved partition
                vendor: Windows
                physical id: 3
                bus info: scsi@3:0.0.0,3
                logical name: /dev/sda3
                serial: 97befea0-dc48-4fd4-b6b6-911ae662e895
                capacity: 15MiB
                capabilities: nofs
                configuration: name=Microsoft reserved partition
           *-volume:3
                description: Windows NTFS volume
                vendor: Windows
                physical id: 4
                bus info: scsi@3:0.0.0,4
                logical name: /dev/sda4
                version: 3.1
                serial: f2ed3dbb-59d3-a341-814f-b618f98e5ea7
                size: 341GiB
                capacity: 341GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2016-01-14 12:32:36 filesystem=ntfs name=Basic data partition state=clean
           *-volume:4
                description: EXT4 volume
                vendor: Linux
                physical id: 5
                bus info: scsi@3:0.0.0,5
                logical name: /dev/sda5
                logical name: /
                version: 1.0
                serial: 7b8f97f2-410e-4e94-bba2-4f633f7e1f9e
                size: 121GiB
                capacity: 121GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2016-01-16 18:33:43 filesystem=ext4 lastmountpoint=/ modified=2016-02-19 23:24:10 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2016-02-19 22:24:20 state=mounted
           *-volume:5
                description: Linux swap volume
                vendor: Linux
                physical id: 6
                bus info: scsi@3:0.0.0,6
                logical name: /dev/sda6
                version: 1
                serial: ac9a5249-cf8c-4818-a0a9-e8df00602729
                size: 2859MiB
                capacity: 2859MiB
                capabilities: nofs precious readonly hidden nomount swap initialized
                configuration: filesystem=swap pagesize=4095
dario@santech:~$ 

```

I would be ok with **disabling** the discrete vieo card (I only need it on Windows), but not with making permanent use of 'nomodeset', because of the power consumption implications and worse desktop experience in general. Any help with getting Nouveau to work, or fixing this behavior with the proprietary driver, or even just thoughts on **how to debug** this issue will be greatly apreciated.

Thank you!
Dario

---

### Post by Scott Deagan on 2016-02-20
Hi Dario,

I have a machine that looks almost identical to yours, a "PC Specialist Defiance II" (which I believe is a re-branded Clevo), and am running Ubuntu 15.10. I have searched long and hard for a solution to the shutdown freezing problem (and lshw or lspci freezing problem), but haven't found anything yet. The best write up on the issue I've seen so far is this one on the PC Specialist forums: [https://www.pcspecialist.co.uk/forums/showthread.php?47727-Installing-Ubuntu-15-10-on-the-Defiance-II](https://www.pcspecialist.co.uk/forums/showthread.php?47727-Installing-Ubuntu-15-10-on-the-Defiance-II)

In short, if you go in to your BIOS, **set the graphics to DISCRETE**, boot up, then go in to **Additional Drivers** and **install the proprietary nVidia** driver, and then **install the 4.4.1 (or 4.4.2) kernel**, you should be able to use your laptop with everything working - but only when you're **nVidia PRIME mode is set to nVidia**.

If I set my laptop to Intel GPU mode and start up in console only mode, I can shutdown properly using shutdown -h now, and I can run lspci and lshw.

Sometimes, I still boot the unit in with the graphics mode (in the Advanced Chipset settings) set to MSHYBRID, and just live with the fact that I have to hard shutdown (sometimes it's worth it for the extra battery life - if I'm out on the road, for example). Using the Intel GPU mode, I still experience the same problems you have described above - the unit freezes on shutdown, lspci and lshw. I would love to know if there is a solution out there (other than switching to DISCRETE graphics mode), but after spending many hours on this, have only come up empty handed.

---

### Post by dario10 on 2016-02-24
Hi Scott,

Thank you for your reply, and sorry for my late one: it looks like I am not subscribed to my own thread and I don't get notifications.

I have been researching the issue on my own in these days, and I'm happy to say I just found a working setup! I have messed a lot with bleeding edge kernels and driver versions, so I hope the solutions I am posting will work for you as well. I tested them on kernel 4.4.2.

**tl;dr** update graphic drivers to the latest possible version

**Solution 1**: Installing the latest Nvidia drivers (v. 361) will keep the discrete GPU on all the time (even if you select the Intel powersave option in the Nvidia settings panel), resulting in a battery life of about 2h (battery reported power consumption ranging between 22W-30W). However, the system will shutdown/suspend properly, lspci/lshw will work, and Steam will run games with sweet 3D capabilities. The Nvidia installer didn't work for me, but you can get the latest proprietary drivers easily from this PPA: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

**Solution 2**: Removing proprietary drivers, blacklisting nouveau, setting up bbswitch, and upgrading the Intel drivers to the most recent (=yesterday's git commit) version will have your laptop run on the (properly accelerated) Intel video card, with the discrete card disabled. This way you will have good enough graphics for desktop task, and a battery life of around 4,5h (reported power consumption ranging between 11W-18W). lspci, lshw, restart/suspend/reboot are all working for me. Steam works as well, even though with graphic capabilities that are limited to the Intel card. I got the latest open source video drivers from this PPA: [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers). The only disadvantage I found is that setting bbswitch to disable the discrete card by default prevents X from starting; instead, I login with the discrete card enabled, and run `$ sudo tee /proc/acpi/bbswitch <<<OFF` to disable it as soon as I have the desktop ready. I will create a service to do this automatically, but for the moment I think is good enough.

Today I wrote a page on Linlap about this issue, where I go a bit deeper in these two solutions: [http://www.linlap.com/santech_c47_clevo_p671re6-g](http://www.linlap.com/santech_c47_clevo_p671re6-g).

Let me know if it works for you, if you try it (in case, backup your data: too many times in these days I found myself in that "oh s**t!" kind of situation :) )

Best,
Dario

---

### Post by Scott Deagan on 2016-02-25
Thanks for the reply Dario! I'm at work at the moment, so cannot try it out right now, but this will be the first thing I do when I get home :) I don't mind losing everything on the laptop, as it's a trivial matter for me to restore everything from my Ubuntu 15.10 desktop. I'll report back here and let you know how I get on.

---

### Post by Scott Deagan on 2016-02-25
Hi Dario,

I have tried the steps you mentioned, but unfortunately they do not work for me. Perhaps we have slightly different BIOSes. In your BIOS, do you have an option to switch the graphics mode between "MSHYBRID" and "DISCRETE"?

I got to the stage where there were no nVidia drivers installed, nouveau was blacklisted, bbswitch was added to my /etc/modules (and sudo update-initramfs -u -k all was run), and the latest Intel drivers were installed from ppa:oibaf/graphics-drivers. With all of this in place, whenever I started the laptop, I would be able to use it for a few minutes (at most), then it would freeze up. I did manage to check the value of the nVidia card using sudo cat /proc/acpi/bbswitch, and it was definitely OFF. If only it wasn't freezing up after a few minutes, it would have been "mission accomplished".

Thanks for your tip on installing the latest nVidia driver - that works  (as you have stated), but the power consumption is still high. When I  run powerstat, I can see around 22 to 30 watts in use when idle. The nVidia card remains powered on, and running sudo tee /proc/acpi/bbswitch <<<OFF doesn't turn it off :(

BTW - have you seen the System76 Oryx PPA? [https://launchpad.net/~system76-dev/+archive/ubuntu/stable](https://launchpad.net/~system76-dev/+archive/ubuntu/stable). I tried installing the "system76-driver" package, but is didn't seem to do anything or make a difference.

I'll try again over this weekend (with a fresh install of 15.10). This time, I won't install any nVidia drivers and will just go straight for the latest Intel drivers from oibaf.

Many thanks,
Scott.

---

### Post by dario10 on 2016-02-26
Hey Scott,

Yes, I have that setting in the BIOS, which is currently set to MSHYBRID. Thanks for the heads up on the System76 PPA, I didn't know the brand and they ship our same machine with Linux: there must be a way to get it to work...

Which kernel are you  using? I have 4.4.2 (040402) installed. I didn't try the default 4.2, but I remember 4.5 was showing some random black flashes and video glitches with the same video drivers configuration that I have now, so maybe it's the kernel causing the freeze. Also, it's strange that the discrete card is already off for you by default: afaik bbswitch  defaults to "ON", unless you specify a module option `load_state=0` in /etc/modprobe.d/bbswitch.conf, or have Bumblebee do it for you. Wild (and possibly wrong) guess: you have Bumblebee installed, which at some point activates the nouveau driver that causes the freeze. You can  try to remove that option and/or Bumblebee, and maybe unload the bbswitch module altogether; when you are on desktop you then enable it manually (`sudo modprobe bbswitch`); at this point /proc/acpi/bbswitch should show "ON", and you can now switch it off with `sudo tee /proc/acpi/bbswitch <<<OFF`. If it freezes before loading bbswitch than it's again a Intel drivers issue :(

Let me know how it goes,
Dario

---

### Post by Scott Deagan on 2016-02-26
Hi Dario,

Thank you so much! I am finally in the same place as you - using the Intel GPU and being able to completely cut power to the nVidia GPU :). Here's my power usage when idle:

```

-------- ----- ----- ----- ----- ----- ---- ------ ------ ---- ---- ---- ------
 Average   0.3   0.0   0.2  99.5   0.1  1.0  103.1   46.3  0.2  0.0  0.3  12.69
  StdDev   0.3   0.0   0.3   0.8   0.1  0.2  119.5   65.7  0.7  0.0  0.5   0.07
-------- ----- ----- ----- ----- ----- ---- ------ ------ ---- ---- ---- ------
 Minimum   0.1   0.0   0.0  95.7   0.0  1.0   41.9   19.6  0.0  0.0  0.0  12.63
 Maximum   1.9   0.0   1.8  99.9   0.6  2.0  708.5  388.7  3.0  0.0  2.0  12.99
-------- ----- ----- ----- ----- ----- ---- ------ ------ ---- ---- ---- ------
Summary:
 12.69 Watts on average with standard deviation 0.07
```

Not sure if it makes much of a difference, but I'm also turning off 6 of my CPU cores with:

```

$ echo 0 | sudo tee /sys/devices/system/cpu/cpu7/online
$ echo 0 | sudo tee /sys/devices/system/cpu/cpu6/online
$ echo 0 | sudo tee /sys/devices/system/cpu/cpu5/online
$ echo 0 | sudo tee /sys/devices/system/cpu/cpu4/online
$ echo 0 | sudo tee /sys/devices/system/cpu/cpu3/online
$ echo 0 | sudo tee /sys/devices/system/cpu/cpu2/online

```

Just to clarify the steps I took (in point form, in case I have to do this again at some point):


[LIST=1]
[*]Installed Ubuntu 15.10. 
[*]The instant I saw the Unity login screen, pressed CTRL + ALT + F1 to bring up a console (Unity will crash within minutes if you don't do this). 
[*]Installed the 4.4.2 kernel. 
[*]Blacklisted the nouveau driver (in /etc/modprobe.d/blacklist-nouveau.conf). 
[*]Installed the latest Intel graphics drivers from Oibaf's PPA. 
[*]Reboot, again pressing CTRL + ALT + F1 to bring up a console window the moment the login screen appears. 
[*]Installed bbswitch-dkms. 
[*]Added bbswitch to /etc/modules 
[*]Ran: sudo update-initramfs -u -k all 
[*]Rebooted - this time everything works, although (like you said), the nVidia GPU is still powered up. 
[*]Turned off the nVidia GPU with: sudo tee /proc/acpi/bbswitch <<<OFF 
[*]Wrote a small script to turn off all but two of my CPU cores, and placed it in /usr/local/bin 
[/LIST]

I haven't as yet experienced DNS failing as you mentioned in your write up, but will let you know if I do. Right now, I'm just so happy I'm running on the Intel GPU without the nVidia draining power.

Once again, thank you so much!!!

Regards,
Scott

---

### Post by Scott Deagan on 2016-02-26
I just noticed that turning off CPU cores doesn't make much of a difference to power consumption.

---

### Post by dario10 on 2016-02-27
Hey Scott,

I'm glad to hear the issue is solved for you as well, let's hope these new drivers will soon make it to the standard repos!

Best,
Dario

---

### Post by Scott Deagan on 2016-03-01
Hi Dario,

I performed an update last night, which included Intel GPU driver updates from Oibaf's PPA. Strangest thing: while **lshw** and **lspci** still work, **sudo lshw -C network** now freezes my machine. I'm not actually sure if something broke in the update or if that issue was already there. Can you successfully run **sudo lshw -C network** without your machine freezing up?

Thanks,
Scott

---

### Post by dario10 on 2016-03-01
Hey Scott,

That command is working ok for me:

```

dario@santech:~$ sudo lshw -C network
[sudo] password for dario: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.1
       bus info: pci@0000:02:00.1
       logical name: enp2s0f1
       version: 12
       serial: 80:fa:5b:22:50:5f
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8411-2_0.0.1 07/08/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:126 ioport:d000(size=256) memory:df214000-df214fff memory:df210000-df213fff
  *-network
       description: Wireless interface
       product: Wireless 8260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 3a
       serial: a4:34:d9:56:2d:81
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.4.2-040402-generic firmware=25.30.13.0 ip=192.168.1.4 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:129 memory:df100000-df101fff

```

We might have different wireless adapters though, mine is a Intel Dual Band Wireless-AC 8260.

Cheers,
Dario

---

### Post by Scott Deagan on 2016-03-02
Hi Dario,

It looks like my wireless adapter is identical to yours:

```

scott@d2-lin:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.1
       bus info: pci@0000:02:00.1
       logical name: enp2s0f1
       version: 12
       serial: 80:fa:5b:27:63:a7
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8411-2_0.0.1 07/08/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:126 ioport:d000(size=256) memory:df214000-df214fff memory:df210000-df213fff
  *-network
       description: Wireless interface
       product: Wireless 8260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 3a
       serial: a4:34:d9:80:63:76
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.4.2-040402-generic firmware=25.30.13.0 ip=192.168.1.112 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:129 memory:df100000-df101fff

```

Anyway, besides the freezing I get when running lchw -C network, I have managed to make some progress. With the nVidia 361 driver installed, I am now able to power on or off my nVidia card and use optirun.

The steps I used:


[LIST=1]
[*]Made sure GPU was set to "DISCRETE" in the BIOS. 
[*]Performed a clean install of Ubuntu 15.10 (had messed around too much, felt safer doing a clean install). 
[*]Updated the kernel to 4.4.2 (then rebooted). 
[*]Added the ppa:graphics-drivers/ppa repo and installed the nvidia-361 driver (then rebooted). 
[*]Installed bbswitch-dkms, added "bbswitch" to /etc/modules, ran sudo update-initramfs -u 
[*]Downloaded and installed the [latest Intel graphics drivers]("https://01.org/linuxgraphics/downloads") and rebooted (not sure if this step was necessary). 
[*][Installed Bumblebee]("https://wiki.ubuntu.com/Bumblebee") 
[*]Edited /etc/bumblebee/bumblebee.conf (Driver=nvidia on line 22, and changed all occurrences of "nvidia-current" to "nvidia-361"). 
[*]Restarted Bumblebee (sudo systemctl restart bumblebeed.service). 
[/LIST]

All of the above worked, but there was still the issue of turning off the nVidia card to reduce power consumption. I figured out that if I unloaded the nVidia modules, I could then use bbswitch to turn off the card. I wrote a small script (called it "nvidia" and placed it in /usr/local/bin) to do this:

```

#!/bin/bash

if [ "$#" -ne 1 ]; then
  echo "Usage: $0 [on|off]. Example: $0 on"
  exit
fi


if [ $1 = "on" ]
then
  tee /proc/acpi/bbswitch <<<ON > /dev/null
  modprobe nvidia_modeset nvidia_uvm nvidia
elif [ $1 = "off" ]
then
  rmmod nvidia_modeset nvidia_uvm nvidia
  tee /proc/acpi/bbswitch <<<OFF > /dev/null
fi

```

Now I can turn the nVidia card on or off using:

```

scott@d2-lin:~$ sudo nvidia off
scott@d2-lin:~$ sudo nvidia on

```

I read the bbswitch docs, and it specifically says that if you cannot turn off your card, it's probably because the drivers are still loaded (unloading nvidia_modeset, nvidia_uvm and nvidia did the trick).

Bumblebee also works fine:

```

scott@d2-lin:~$ optirun firefox

```

I'm very happy with this and will have to live with the lchw issue for now (I just have to remember to turn on my nVidia card before running those commands!).

Really appreciate all your help with this.

Many thanks,
Scott.

---

