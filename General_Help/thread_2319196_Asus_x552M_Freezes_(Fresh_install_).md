---
title: "Asus x552M Freezes (Fresh install )"
date: 2016-04-01
forum: General Help
---

### Post by gabriel69 on 2016-04-01
Hi,

After a while, my ubuntu ( 14.04 or the latest 15 ) freezes on Asus x552MJ. I can't do anything. No keyboard, no mouse.. disk stops working. No sound. I think it is a kernel panic. I tried disable the touchpad and work with a mouse, disable wireless and work with a cable, install Nvidia drivers ( result: black screen ), revert to nouveau driver, reinstall the system 3 times... I can not figure out what the problem is, it happens sometimes.

Is someone with the same problem or know what it is ?
I'm exhausted :/

Page specifications ( my configuration ) -> [https://www.asus.com/Notebooks/X552MJ/specifications/](https://www.asus.com/Notebooks/X552MJ/specifications/)

Thank you.

---

### Post by gabriel69 on 2016-04-01
I forgot to say that in all fresh instalations, I installed Google Chrome stable to navigate. I'm testing a new fresh install without Google Chrome to see if is really the browser.

---

### Post by gabriel69 on 2016-04-02
It's not the browser... the kernel log file before the crash (  14:27:39 )

> 
Apr  2 13:23:23 gabriel-X550MJ kernel: [   87.878958] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] Initializing cgroup subsys cpuset
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] Initializing cgroup subsys cpu
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] Initializing cgroup subsys cpuacct
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] Linux version 4.2.0-34-generic (buildd@lgw01-54) (gcc version 5.2.1 20151010 (Ubuntu 5.2.1-22ubuntu2) ) #39-Ubuntu SMP Thu Mar 10 22:13:01 UTC 2016 (Ubuntu 4.2.0-34.39-generic 4.2.8-ckt4)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-34-generic.efi.signed root=UUID=cf328262-98b6-4044-ad1e-3e3d89b8d6f9 ro quiet splash vt.handoff=7
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] KERNEL supported cpus:
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]   Intel GenuineIntel
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]   AMD AuthenticAMD
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]   Centaur CentaurHauls
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] x86/fpu: Legacy x87 FPU detected.
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] x86/fpu: Using 'lazy' FPU context switches.
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000008efff] usable
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] BIOS-e820: [mem 0x000000000008f000-0x000000000008ffff] ACPI NVS
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] BIOS-e820: [mem 0x0000000000090000-0x000000000009dfff] usable
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] BIOS-e820: [mem 0x000000000009e000-0x000000000009ffff] reserved
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000200fffff] reserved
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] BIOS-e820: [mem 0x0000000020100000-0x0000000098cf1fff] usable
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] BIOS-e820: [mem 0x0000000098cf2000-0x0000000098d21fff] reserved
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] BIOS-e820: [mem 0x0000000098d22000-0x0000000098e5ffff] usable
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] BIOS-e820: [mem 0x0000000098e60000-0x00000000993a0fff] ACPI NVS
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] BIOS-e820: [mem 0x00000000993a1000-0x0000000099b8efff] reserved
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] BIOS-e820: [mem 0x0000000099b8f000-0x0000000099b8ffff] usable
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] BIOS-e820: [mem 0x0000000099b90000-0x0000000099bd1fff] reserved
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] BIOS-e820: [mem 0x0000000099bd2000-0x0000000099d47fff] usable
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] BIOS-e820: [mem 0x0000000099d48000-0x0000000099ff9fff] reserved
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] BIOS-e820: [mem 0x0000000099ffa000-0x0000000099ffffff] usable
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] BIOS-e820: [mem 0x00000000e00f8000-0x00000000e00f8fff] reserved
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed01000-0x00000000fed01fff] reserved
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] BIOS-e820: [mem 0x00000000ffc00000-0x00000000ffffffff] reserved
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000015fffffff] usable
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] NX (Execute Disable) protection: active
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] e820: update [mem 0x8a62a018-0x8a63a057] usable ==> usable
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] e820: update [mem 0x8a612018-0x8a629c57] usable ==> usable
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] extended physical RAM map:
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x0000000000000000-0x000000000008efff] usable
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x000000000008f000-0x000000000008ffff] ACPI NVS
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x0000000000090000-0x000000000009dfff] usable
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x000000000009e000-0x000000000009ffff] reserved
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x0000000000100000-0x000000001fffffff] usable
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x0000000020000000-0x00000000200fffff] reserved
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x0000000020100000-0x000000008a612017] usable
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x000000008a612018-0x000000008a629c57] usable
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x000000008a629c58-0x000000008a62a017] usable
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x000000008a62a018-0x000000008a63a057] usable
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x000000008a63a058-0x0000000098cf1fff] usable
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x0000000098cf2000-0x0000000098d21fff] reserved
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x0000000098d22000-0x0000000098e5ffff] usable
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x0000000098e60000-0x00000000993a0fff] ACPI NVS
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x00000000993a1000-0x0000000099b8efff] reserved
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x0000000099b8f000-0x0000000099b8ffff] usable
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x0000000099b90000-0x0000000099bd1fff] reserved
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x0000000099bd2000-0x0000000099d47fff] usable
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x0000000099d48000-0x0000000099ff9fff] reserved
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x0000000099ffa000-0x0000000099ffffff] usable
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x00000000e00f8000-0x00000000e00f8fff] reserved
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x00000000fed01000-0x00000000fed01fff] reserved
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x00000000ffc00000-0x00000000ffffffff] reserved
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x0000000100000000-0x000000015fffffff] usable
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] efi: EFI v2.31 by American Megatrends
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] efi:  ESRT=0x99b2a198  ACPI=0x98ee6000  ACPI 2.0=0x98ee6000  SMBIOS=0x99a78d98 
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] esrt: Reserving ESRT space from 0x0000000099b2a198 to 0x0000000099b2a1d0.
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] SMBIOS 2.8 present.
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] DMI: ASUSTeK COMPUTER INC. X550MJ/X550MJ, BIOS X550MJ.300 08/17/2015
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] e820: last_pfn = 0x160000 max_arch_pfn = 0x400000000
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] MTRR default type: uncachable
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] MTRR fixed ranges enabled:
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]   00000-9FFFF write-back
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]   A0000-FFFFF uncachable
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] MTRR variable ranges enabled:
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]   0 base 000000000 mask F80000000 write-back
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]   1 base 080000000 mask FE0000000 write-back
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]   2 base 09A000000 mask FFE000000 uncachable
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]   3 base 09C000000 mask FFC000000 uncachable
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]   4 base 100000000 mask F80000000 write-back
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]   5 disabled
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]   6 disabled
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]   7 disabled
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] original variable MTRRs
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] reg 1, base: 2GB, range: 512MB, type WB
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] reg 2, base: 2464MB, range: 32MB, type UC
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] reg 3, base: 2496MB, range: 64MB, type UC
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] reg 4, base: 4GB, range: 2GB, type WB
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] total RAM covered: 4512M
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] Found optimal setting for mtrr clean up
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]  gran_size: 64K     chunk_size: 64K     num_reg: 5      lose cover RAM: 0G
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] New variable MTRRs
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] reg 1, base: 2GB, range: 256MB, type WB
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] reg 2, base: 2304MB, range: 128MB, type WB
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] reg 3, base: 2432MB, range: 32MB, type WB
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] reg 4, base: 4GB, range: 2GB, type WB
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] e820: update [mem 0x9a000000-0xffffffff] usable ==> reserved
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] e820: last_pfn = 0x9a000 max_arch_pfn = 0x400000000
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] Scanning 1 areas for low memory corruption
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]  [mem 0x00000000-0x000fffff] page 4k
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] BRK [0x01ff1000, 0x01ff1fff] PGTABLE
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] BRK [0x01ff2000, 0x01ff2fff] PGTABLE
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] BRK [0x01ff3000, 0x01ff3fff] PGTABLE
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] init_memory_mapping: [mem 0x15fe00000-0x15fffffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]  [mem 0x15fe00000-0x15fffffff] page 2M
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] BRK [0x01ff4000, 0x01ff4fff] PGTABLE
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] init_memory_mapping: [mem 0x140000000-0x15fdfffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]  [mem 0x140000000-0x15fdfffff] page 2M
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] init_memory_mapping: [mem 0x00100000-0x1fffffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]  [mem 0x00100000-0x001fffff] page 4k
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]  [mem 0x00200000-0x1fffffff] page 2M
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] init_memory_mapping: [mem 0x20100000-0x98cf1fff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]  [mem 0x20100000-0x201fffff] page 4k
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]  [mem 0x20200000-0x98bfffff] page 2M
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]  [mem 0x98c00000-0x98cf1fff] page 4k
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] BRK [0x01ff5000, 0x01ff5fff] PGTABLE
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] BRK [0x01ff6000, 0x01ff6fff] PGTABLE
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] init_memory_mapping: [mem 0x98d22000-0x98e5ffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]  [mem 0x98d22000-0x98e5ffff] page 4k
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] init_memory_mapping: [mem 0x99b8f000-0x99b8ffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]  [mem 0x99b8f000-0x99b8ffff] page 4k
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] init_memory_mapping: [mem 0x99bd2000-0x99d47fff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]  [mem 0x99bd2000-0x99d47fff] page 4k
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] init_memory_mapping: [mem 0x99ffa000-0x99ffffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]  [mem 0x99ffa000-0x99ffffff] page 4k
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] init_memory_mapping: [mem 0x100000000-0x13fffffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]  [mem 0x100000000-0x13fffffff] page 2M
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] RAMDISK: [mem 0x3dff5000-0x3fffafff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] ACPI: Early table checksum verification disabled
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] ACPI: RSDP 0x0000000098EE6000 000024 (v02 _ASUS_)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] ACPI: XSDT 0x0000000098EE6088 00009C (v01 _ASUS_ Notebook 01072009 AMI  00010013)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] ACPI: FACP 0x0000000098EF7ED0 00010C (v05 _ASUS_ Notebook 01072009 AMI  00010013)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] ACPI BIOS Warning (bug): 32/64X length mismatch in FADT/Gpe0Block: 128/32 (20150619/tbfadt-623)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] ACPI: DSDT 0x0000000098EE61B8 011D11 (v02 _ASUS_ Notebook 01072009 INTL 20120913)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] ACPI: FACS 0x00000000993A0F80 000040
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] ACPI: APIC 0x0000000098EF7FE0 000084 (v03 _ASUS_ Notebook 01072009 AMI  00010013)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] ACPI: FPDT 0x0000000098EF8068 000044 (v01 _ASUS_ Notebook 01072009 AMI  00010013)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] ACPI: MCFG 0x0000000098EF80B0 00003C (v01 _ASUS_ Notebook 01072009 MSFT 00000097)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] ACPI: LPIT 0x0000000098EF80F0 000104 (v01 _ASUS_ Notebook 00000003 VLV2 0100000D)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] ACPI: ECDT 0x0000000098EF81F8 0000C1 (v01 _ASUS_ Notebook 01072009 AMI. 00000005)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] ACPI: HPET 0x0000000098EF82C0 000038 (v01 _ASUS_ Notebook 01072009 AMI. 00000005)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] ACPI: SSDT 0x0000000098EF82F8 000763 (v01 PmRef  CpuPm    00003000 INTL 20061109)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] ACPI: SSDT 0x0000000098EF8A60 000290 (v01 PmRef  Cpu0Tst  00003000 INTL 20061109)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] ACPI: SSDT 0x0000000098EF8CF0 00017A (v01 PmRef  ApTst    00003000 INTL 20061109)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] ACPI: UEFI 0x0000000098EF8E70 000042 (v01 _ASUS_ Notebook 00000000      00000000)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] ACPI: SSDT 0x0000000098EF8EB8 000915 (v01 SgRef  SgPch    00001000 INTL 20061109)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] ACPI: SSDT 0x0000000098EF97D0 0013E4 (v01 OptRef NvdPch   00001000 INTL 20061109)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] ACPI: BGRT 0x0000000098EFABB8 000038 (v00 _ASUS_ Notebook 01072009 AMI  00010013)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] ACPI: MSDM 0x0000000098D1FF98 000055 (v03 _ASUS_ Notebook 00000000 ASUS 00000001)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] No NUMA configuration found
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x000000015fffffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] NODE_DATA(0) allocated [mem 0x15fff4000-0x15fff8fff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]  [ffffea0000000000-ffffea00057fffff] PMD -> [ffff88015b600000-ffff88015f5fffff] on node 0
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] Zone ranges:
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]   Normal   [mem 0x0000000100000000-0x000000015fffffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] Movable zone start for each node
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] Early memory node ranges
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]   node   0: [mem 0x0000000000001000-0x000000000008efff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]   node   0: [mem 0x0000000000090000-0x000000000009dfff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]   node   0: [mem 0x0000000000100000-0x000000001fffffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]   node   0: [mem 0x0000000020100000-0x0000000098cf1fff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]   node   0: [mem 0x0000000098d22000-0x0000000098e5ffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]   node   0: [mem 0x0000000099b8f000-0x0000000099b8ffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]   node   0: [mem 0x0000000099bd2000-0x0000000099d47fff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]   node   0: [mem 0x0000000099ffa000-0x0000000099ffffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]   node   0: [mem 0x0000000100000000-0x000000015fffffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000015fffffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] On node 0 totalpages: 1019465
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]   DMA zone: 21 pages reserved
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]   DMA zone: 3996 pages, LIFO batch:0
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]   DMA32 zone: 9723 pages used for memmap
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]   DMA32 zone: 622253 pages, LIFO batch:31
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]   Normal zone: 6144 pages used for memmap
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]   Normal zone: 393216 pages, LIFO batch:31
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] tboot: non-0 tboot_addr but it is not of type E820_RESERVED
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] x86/hpet: Will disable the HPET for this platform because it's not reliable
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] Reserving Intel graphics stolen memory at 0x9b000000-0x9effffff
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-86
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] ACPI: IRQ0 used by override.
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] ACPI: IRQ9 used by override.
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0008f000-0x0008ffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0x20000000-0x200fffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0x8a612000-0x8a612fff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0x8a629000-0x8a629fff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0x8a62a000-0x8a62afff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0x8a63a000-0x8a63afff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0x98cf2000-0x98d21fff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0x98e60000-0x993a0fff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0x993a1000-0x99b8efff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0x99b90000-0x99bd1fff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0x99d48000-0x99ff9fff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9a000000-0x9affffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9b000000-0x9effffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f000000-0xe00f7fff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe00f8000-0xe00f8fff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe00f9000-0xfed00fff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed01000-0xfed01fff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed02000-0xffbfffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffc00000-0xffffffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] e820: [mem 0x9f000000-0xe00f7fff] available for PCI devices
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] PERCPU: Embedded 33 pages/cpu @ffff88015fc00000 s96728 r8192 d30248 u524288
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] pcpu-alloc: s96728 r8192 d30248 u524288 alloc=1*2097152
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1003513
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] Policy zone: Normal
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-34-generic.efi.signed root=UUID=cf328262-98b6-4044-ad1e-3e3d89b8d6f9 ro quiet splash vt.handoff=7
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] Memory: 3665116K/4077860K available (8158K kernel code, 1238K rwdata, 3804K rodata, 1464K init, 1292K bss, 412744K reserved, 0K cma-reserved)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] Hierarchical RCU implementation.
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]     Build-time adjustment of leaf fanout to 64.
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=4
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] NR_IRQS:16640 nr_irqs:1024 16
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]     Offload RCU callbacks from all CPUs
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000]     Offload RCU callbacks from CPUs: 0-3.
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] vt handoff: transparent VT on vt#7
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] Console: colour dummy device 80x25
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] console [tty0] enabled
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] Maximum core-clock to bus-clock ratio: 0x1a
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] Resolved frequency ID: 0, frequency: 83200 KHz
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] TSC runs at 2163200 KHz
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] lapic_timer_frequency = 332800
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000000] tsc: Detected 2163.200 MHz processor
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000038] Calibrating delay loop (skipped), value calculated using timer frequency.. 4326.40 BogoMIPS (lpj=8652800)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000043] pid_max: default: 32768 minimum: 301
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.000055] ACPI: Core revision 20150619
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.034885] ACPI: All ACPI Tables successfully acquired
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.037099] Security Framework initialized
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.037126] AppArmor: AppArmor initialized
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.037129] Yama: becoming mindful.
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.037619] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.039377] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.040207] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.040223] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.040581] Initializing cgroup subsys blkio
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.040590] Initializing cgroup subsys memory
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.040605] Initializing cgroup subsys devices
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.040611] Initializing cgroup subsys freezer
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.040616] Initializing cgroup subsys net_cls
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.040621] Initializing cgroup subsys perf_event
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.040626] Initializing cgroup subsys net_prio
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.040631] Initializing cgroup subsys hugetlb
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.040658] CPU: Physical Processor ID: 0
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.040661] CPU: Processor Core ID: 0
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.040666] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.040669] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.045433] mce: CPU supports 6 MCE banks
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.045442] CPU0: Thermal monitoring handled by SMI
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.045447] process: using mwait in idle threads
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.045454] Last level iTLB entries: 4KB 48, 2MB 0, 4MB 0
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.045457] Last level dTLB entries: 4KB 128, 2MB 16, 4MB 16, 1GB 0
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.045779] Freeing SMP alternatives memory: 28K (ffffffff81ea5000 - ffffffff81eac000)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.047545] Ignoring BGRT: invalid status 0 (expected 1)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.064764] ftrace: allocating 30940 entries in 121 pages
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.082133] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.121811] TSC deadline timer enabled
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.121816] smpboot: CPU0: Intel(R) Pentium(R) CPU  N3540  @ 2.16GHz (fam: 06, model: 37, stepping: 08)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.121854] Performance Events: PEBS fmt2+, 8-deep LBR, Silvermont events, full-width counters, Intel PMU driver.
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.121868] ... version:                3
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.121871] ... bit width:              40
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.121873] ... generic registers:      2
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.121875] ... value mask:             000000ffffffffff
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.121877] ... max period:             000000ffffffffff
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.121879] ... fixed-purpose events:   3
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.121880] ... event mask:             0000000700000003
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.123354] x86: Booting SMP configuration:
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.123359] .... node  #0, CPUs:      #1
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.129128] CPU1: Thermal monitoring handled by SMI
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.131319] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.131567]  #2
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.137335] CPU2: Thermal monitoring handled by SMI
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.139689]  #3<7>[    0.145458] CPU3: Thermal monitoring handled by SMI
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.147591] x86: Booted up 1 node, 4 CPUs
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.147597] smpboot: Total of 4 processors activated (17305.60 BogoMIPS)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.148741] devtmpfs: initialized
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.155431] evm: security.selinux
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.155434] evm: security.SMACK64
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.155436] evm: security.SMACK64EXEC
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.155438] evm: security.SMACK64TRANSMUTE
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.155440] evm: security.SMACK64MMAP
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.155442] evm: security.ima
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.155443] evm: security.capability
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.155594] PM: Registering ACPI NVS region [mem 0x0008f000-0x0008ffff] (4096 bytes)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.155598] PM: Registering ACPI NVS region [mem 0x98e60000-0x993a0fff] (5509120 bytes)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.156025] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.156206] pinctrl core: initialized pinctrl subsystem
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.156574] RTC time: 13:35:06, date: 04/02/16
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.156850] NET: Registered protocol family 16
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.167283] cpuidle: using governor ladder
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.171310] cpuidle: using governor menu
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.171605] ACPI: bus type PCI registered
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.171610] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.171753] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.171758] PCI: not using MMCONFIG
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.171761] PCI: Using configuration type 1 for base access
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.176993] ACPI: Added _OSI(Module Device)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.176998] ACPI: Added _OSI(Processor Device)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.177000] ACPI: Added _OSI(3.0 _SCP Extensions)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.177003] ACPI: Added _OSI(Processor Aggregator Device)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.181501] ACPI : EC: EC description table is found, configuring boot EC
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.181523] ACPI : EC: EC started
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.196012] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.200274] ACPI: Dynamic OEM Table Load:
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.200286] ACPI: SSDT 0xFFFF88015A6BA000 00045B (v01 PmRef  Cpu0Ist  00003000 INTL 20061109)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.201598] ACPI: Dynamic OEM Table Load:
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.201608] ACPI: SSDT 0xFFFF88015A6BA800 000433 (v01 PmRef  Cpu0Cst  00003001 INTL 20061109)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.203309] ACPI: Dynamic OEM Table Load:
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.203319] ACPI: SSDT 0xFFFF88015A746400 00015F (v01 PmRef  ApIst    00003000 INTL 20061109)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.204586] ACPI: Dynamic OEM Table Load:
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.204595] ACPI: SSDT 0xFFFF88015A730240 00008D (v01 PmRef  ApCst    00003000 INTL 20061109)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.207144] ACPI: Interpreter enabled
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.207158] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20150619/hwxface-580)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.207168] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150619/hwxface-580)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.207195] ACPI: (supports S0 S3 S4 S5)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.207198] ACPI: Using IOAPIC for interrupt routing
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.207241] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.208218] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.208270] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.217650] ACPI: Power Resource [PC05] (on)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.220406] ACPI: Power Resource [USBC] (on)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.222384] ACPI: Power Resource [PLPE] (on)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.222754] ACPI: Power Resource [PLPE] (on)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.227833] ACPI: Power Resource [CLK0] (on)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.227916] ACPI: Power Resource [CLK1] (on)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.231955] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.231967] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.232049] \_SB_.PCI0:_OSC invalid UUID
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.232052] _OSC request data:1 1f 0 
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.232060] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.232707] PCI host bridge to bus 0000:00
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.232713] pci_bus 0000:00: root bus resource [bus 00-ff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.232718] pci_bus 0000:00: root bus resource [io  0x0070-0x0077]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.232722] pci_bus 0000:00: root bus resource [io  0x0000-0x006f window]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.232725] pci_bus 0000:00: root bus resource [io  0x0078-0x0cf7 window]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.232729] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.232733] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.232737] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff window]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.232740] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000fffff window]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.232744] pci_bus 0000:00: root bus resource [mem 0xa0000000-0xc3c15ffe window]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.232756] pci 0000:00:00.0: [8086:0f00] type 00 class 0x060000
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.232963] pci 0000:00:02.0: [8086:0f31] type 00 class 0x030000
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.232978] pci 0000:00:02.0: reg 0x10: [mem 0xc3400000-0xc37fffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.232991] pci 0000:00:02.0: reg 0x18: [mem 0xa0000000-0xafffffff pref]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.233003] pci 0000:00:02.0: reg 0x20: [io  0xf080-0xf087]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.233205] pci 0000:00:13.0: [8086:0f23] type 00 class 0x010601
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.233225] pci 0000:00:13.0: reg 0x10: [io  0xf070-0xf077]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.233236] pci 0000:00:13.0: reg 0x14: [io  0xf060-0xf063]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.233247] pci 0000:00:13.0: reg 0x18: [io  0xf050-0xf057]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.233257] pci 0000:00:13.0: reg 0x1c: [io  0xf040-0xf043]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.233268] pci 0000:00:13.0: reg 0x20: [io  0xf020-0xf03f]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.233279] pci 0000:00:13.0: reg 0x24: [mem 0xc3c15000-0xc3c157ff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.233323] pci 0000:00:13.0: PME# supported from D3hot
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.233492] pci 0000:00:14.0: [8086:0f35] type 00 class 0x0c0330
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.233513] pci 0000:00:14.0: reg 0x10: [mem 0xc3c00000-0xc3c0ffff 64bit]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.233573] pci 0000:00:14.0: PME# supported from D3hot D3cold
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.233704] pci 0000:00:14.0: System wakeup disabled by ACPI
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.233785] pci 0000:00:1a.0: [8086:0f18] type 00 class 0x108000
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.233810] pci 0000:00:1a.0: reg 0x10: [mem 0xc3900000-0xc39fffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.233825] pci 0000:00:1a.0: reg 0x14: [mem 0xc3800000-0xc38fffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.233924] pci 0000:00:1a.0: PME# supported from D0 D3hot
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.234099] pci 0000:00:1b.0: [8086:0f04] type 00 class 0x040300
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.234123] pci 0000:00:1b.0: reg 0x10: [mem 0xc3c10000-0xc3c13fff 64bit]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.234194] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.234363] pci 0000:00:1c.0: [8086:0f48] type 01 class 0x060400
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.234424] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.234593] pci 0000:00:1c.2: [8086:0f4c] type 01 class 0x060400
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.234652] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.234763] pci 0000:00:1c.2: System wakeup disabled by ACPI
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.234834] pci 0000:00:1c.3: [8086:0f4e] type 01 class 0x060400
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.234894] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.235001] pci 0000:00:1c.3: System wakeup disabled by ACPI
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.235077] pci 0000:00:1f.0: [8086:0f1c] type 00 class 0x060100
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.235314] pci 0000:00:1f.3: [8086:0f12] type 00 class 0x0c0500
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.235350] pci 0000:00:1f.3: reg 0x10: [mem 0xc3c14000-0xc3c1401f]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.235422] pci 0000:00:1f.3: reg 0x20: [io  0xf000-0xf01f]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.235773] pci 0000:01:00.0: [10de:1299] type 00 class 0x030200
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.235793] pci 0000:01:00.0: reg 0x10: [mem 0xc2000000-0xc2ffffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.235810] pci 0000:01:00.0: reg 0x14: [mem 0xb0000000-0xbfffffff 64bit pref]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.235827] pci 0000:01:00.0: reg 0x1c: [mem 0xc0000000-0xc1ffffff 64bit pref]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.235839] pci 0000:01:00.0: reg 0x24: [io  0xe000-0xe07f]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.235851] pci 0000:01:00.0: reg 0x30: [mem 0xc3000000-0xc307ffff pref]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.236040] pci 0000:01:00.0: System wakeup disabled by ACPI
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.243736] pci 0000:00:1c.0: PCI bridge to [bus 01]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.243743] pci 0000:00:1c.0:   bridge window [io  0xe000-0xefff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.243748] pci 0000:00:1c.0:   bridge window [mem 0xb0000000-0xc30fffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.244043] pci 0000:02:00.0: [10ec:5286] type 00 class 0xff0000
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.244065] pci 0000:02:00.0: reg 0x10: [mem 0xc3b00000-0xc3b0ffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.244194] pci 0000:02:00.0: supports D1 D2
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.244198] pci 0000:02:00.0: PME# supported from D1 D2 D3hot D3cold
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.244259] pci 0000:02:00.0: System wakeup disabled by ACPI
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.244340] pci 0000:02:00.2: [10ec:8136] type 00 class 0x020000
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.244362] pci 0000:02:00.2: reg 0x10: [io  0xd000-0xd0ff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.244392] pci 0000:02:00.2: reg 0x18: [mem 0xc3b14000-0xc3b14fff 64bit]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.244411] pci 0000:02:00.2: reg 0x20: [mem 0xc3b10000-0xc3b13fff 64bit pref]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.244484] pci 0000:02:00.2: supports D1 D2
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.244489] pci 0000:02:00.2: PME# supported from D0 D1 D2 D3hot D3cold
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.251732] pci 0000:00:1c.2: PCI bridge to [bus 02]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.251738] pci 0000:00:1c.2:   bridge window [io  0xd000-0xdfff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.251743] pci 0000:00:1c.2:   bridge window [mem 0xc3b00000-0xc3bfffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.251990] pci 0000:03:00.0: [168c:0036] type 00 class 0x028000
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.252050] pci 0000:03:00.0: reg 0x10: [mem 0xc3a00000-0xc3a7ffff 64bit]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.252102] pci 0000:03:00.0: reg 0x30: [mem 0xc3a80000-0xc3a8ffff pref]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.252166] pci 0000:03:00.0: supports D1 D2
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.252170] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.252227] pci 0000:03:00.0: System wakeup disabled by ACPI
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.259728] pci 0000:00:1c.3: PCI bridge to [bus 03]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.259736] pci 0000:00:1c.3:   bridge window [mem 0xc3a00000-0xc3afffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.261011] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11 12) *0, disabled.
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.261137] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 12) *0, disabled.
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.261256] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 12) *0, disabled.
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.261378] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 12) *0, disabled.
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.261495] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 12) *0, disabled.
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.261614] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 12) *0, disabled.
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.261733] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 12) *0, disabled.
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.261851] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 12) *0, disabled.
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.263701] ACPI: Enabled 4 GPEs in block 00 to 3F
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.263880] ACPI : EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.264135] vgaarb: setting as boot device: PCI:0000:00:02.0
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.264140] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.264146] vgaarb: loaded
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.264149] vgaarb: bridge control possible 0000:00:02.0
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.264749] SCSI subsystem initialized
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.264861] libata version 3.00 loaded.
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.264913] ACPI: bus type USB registered
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.265000] usbcore: registered new interface driver usbfs
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.265080] usbcore: registered new interface driver hub
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.265161] usbcore: registered new device driver usb
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.265794] PCI: Using ACPI for IRQ routing
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.271671] PCI: pci_cache_line_size set to 64 bytes
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.271738] e820: reserve RAM buffer [mem 0x0008f000-0x0008ffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.271742] e820: reserve RAM buffer [mem 0x0009e000-0x0009ffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.271745] e820: reserve RAM buffer [mem 0x8a612018-0x8bffffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.271748] e820: reserve RAM buffer [mem 0x8a62a018-0x8bffffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.271750] e820: reserve RAM buffer [mem 0x98cf2000-0x9bffffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.271754] e820: reserve RAM buffer [mem 0x98e60000-0x9bffffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.271757] e820: reserve RAM buffer [mem 0x99b90000-0x9bffffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.271760] e820: reserve RAM buffer [mem 0x99d48000-0x9bffffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.271763] e820: reserve RAM buffer [mem 0x9a000000-0x9bffffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.271973] NetLabel: Initializing
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.271976] NetLabel:  domain hash size = 128
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.271978] NetLabel:  protocols = UNLABELED CIPSOv4
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.271997] NetLabel:  unlabeled traffic allowed by default
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.272246] clocksource: Switched to clocksource refined-jiffies
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.283897] AppArmor: AppArmor Filesystem Enabled
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.284030] pnp: PnP ACPI init
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.284143] pnp 00:00: Plug and Play ACPI device, IDs PNP0b00 (active)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.284407] system 00:01: [io  0x0680-0x069f] has been reserved
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.284412] system 00:01: [io  0x0400-0x047f] has been reserved
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.284416] system 00:01: [io  0x0500-0x05fe] has been reserved
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.284420] system 00:01: [io  0x0600-0x061f] has been reserved
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.284427] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.284543] system 00:02: [io  0x03f8-0x0411] could not be reserved
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.284550] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.284685] pnp 00:03: Plug and Play ACPI device, IDs FLT0101 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.284775] pnp 00:04: Plug and Play ACPI device, IDs ATK3001 PNP030b (active)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.285232] system 00:05: [mem 0xe0000000-0xefffffff] could not be reserved
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.285238] system 00:05: [mem 0xfed01000-0xfed01fff] has been reserved
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.285242] system 00:05: [mem 0xfed03000-0xfed03fff] has been reserved
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.285247] system 00:05: [mem 0xfed04000-0xfed04fff] has been reserved
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.285251] system 00:05: [mem 0xfed0c000-0xfed0ffff] has been reserved
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.285255] system 00:05: [mem 0xfed08000-0xfed08fff] has been reserved
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.285259] system 00:05: [mem 0xfed1c000-0xfed1cfff] has been reserved
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.285263] system 00:05: [mem 0xfee00000-0xfeefffff] has been reserved
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.285267] system 00:05: [mem 0xfef00000-0xfeffffff] has been reserved
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.285274] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.286769] pnp: PnP ACPI: found 6 devices
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.299271] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.299309] clocksource: Switched to clocksource acpi_pm
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.299354] pci 0000:00:1c.0: PCI bridge to [bus 01]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.299360] pci 0000:00:1c.0:   bridge window [io  0xe000-0xefff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.299366] pci 0000:00:1c.0:   bridge window [mem 0xb0000000-0xc30fffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.299375] pci 0000:00:1c.2: PCI bridge to [bus 02]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.299380] pci 0000:00:1c.2:   bridge window [io  0xd000-0xdfff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.299385] pci 0000:00:1c.2:   bridge window [mem 0xc3b00000-0xc3bfffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.299394] pci 0000:00:1c.3: PCI bridge to [bus 03]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.299400] pci 0000:00:1c.3:   bridge window [mem 0xc3a00000-0xc3afffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.299408] pci_bus 0000:00: resource 4 [io  0x0070-0x0077]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.299415] pci_bus 0000:00: resource 5 [io  0x0000-0x006f window]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.299419] pci_bus 0000:00: resource 6 [io  0x0078-0x0cf7 window]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.299423] pci_bus 0000:00: resource 7 [io  0x0d00-0xffff window]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.299426] pci_bus 0000:00: resource 8 [mem 0x000a0000-0x000bffff window]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.299430] pci_bus 0000:00: resource 9 [mem 0x000c0000-0x000dffff window]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.299434] pci_bus 0000:00: resource 10 [mem 0x000e0000-0x000fffff window]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.299438] pci_bus 0000:00: resource 11 [mem 0xa0000000-0xc3c15ffe window]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.299442] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.299445] pci_bus 0000:01: resource 1 [mem 0xb0000000-0xc30fffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.299449] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.299452] pci_bus 0000:02: resource 1 [mem 0xc3b00000-0xc3bfffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.299456] pci_bus 0000:03: resource 1 [mem 0xc3a00000-0xc3afffff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.299520] NET: Registered protocol family 2
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.299852] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.299997] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.300142] TCP: Hash tables configured (established 32768 bind 32768)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.300203] UDP hash table entries: 2048 (order: 4, 65536 bytes)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.300241] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.300374] NET: Registered protocol family 1
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.300408] pci 0000:00:02.0: Video device with shadowed ROM
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.300736] PCI: CLS 64 bytes, default 64
Apr  2 14:27:39 gabriel-X550MJ kernel: [    0.300884] Trying to unpack rootfs image as initramfs...
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.113354] Freeing initrd memory: 32792K (ffff88003dff5000 - ffff88003fffb000)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.113373] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.113377] software IO TLB [mem 0x86612000-0x8a612000] (64MB) mapped at [ffff880086612000-ffff88008a611fff]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.113617] microcode: CPU0 sig=0x30678, pf=0x8, revision=0x815
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.113632] microcode: CPU1 sig=0x30678, pf=0x8, revision=0x815
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.113662] microcode: CPU2 sig=0x30678, pf=0x8, revision=0x815
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.113694] microcode: CPU3 sig=0x30678, pf=0x8, revision=0x815
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.113807] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.114202] Scanning for low memory corruption every 60 seconds
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.115169] futex hash table entries: 1024 (order: 4, 65536 bytes)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.115197] Initialise system trusted keyring
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.115238] audit: initializing netlink subsys (disabled)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.115271] audit: type=2000 audit(1459604106.099:1): initialized
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.116231] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.119298] zpool: loaded
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.119303] zbud: loaded
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.119857] VFS: Disk quotas dquot_6.6.0
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.119928] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.121192] fuse init (API version 7.23)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.121515] Key type big_key registered
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.123359] Key type asymmetric registered
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.123383] Asymmetric key parser 'x509' registered
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.123455] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.123626] io scheduler noop registered
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.123632] io scheduler deadline registered (default)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.123744] io scheduler cfq registered
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.124548] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.124566] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.124638] efifb: probing for efifb
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.124665] efifb: framebuffer at 0xa0000000, mapped to 0xffffc90000800000, using 1876k, total 1875k
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.124668] efifb: mode is 800x600x32, linelength=3200, pages=1
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.124670] efifb: scrolling: redraw
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.124673] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.124873] Console: switching to colour frame buffer device 100x37
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.124894] fb0: EFI VGA frame buffer device
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.124911] intel_idle: MWAIT substates: 0x33000020
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.124915] intel_idle: v0.4 model 0x37
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.124917] intel_idle: lapic_timer_reliable_states 0xffffffff
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.125390] ACPI: AC Adapter [AC0] (off-line)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.125516] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.125523] ACPI: Power Button [PWRB]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.125604] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.126664] ACPI: Lid Switch [LID]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.126741] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.126747] ACPI: Sleep Button [SLPB]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.126823] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.126829] ACPI: Power Button [PWRF]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.131606] thermal LNXTHERM:00: registered as thermal_zone0
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.131611] ACPI: Thermal Zone [THRM] (45 C)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.131675] GHES: HEST is not enabled!
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.132236] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.152434] serial8250: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.161715] hpet: number irqs doesn't agree with number of timers
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.162197] Linux agpgart interface v0.103
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.169119] ACPI: Battery Slot [BAT0] (battery present)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.173422] brd: module loaded
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.175736] loop: module loaded
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.176198] libphy: Fixed MDIO Bus: probed
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.176204] tun: Universal TUN/TAP device driver, 1.6
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.176207] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.176334] PPP generic driver version 2.4.2
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.176695] xhci_hcd 0000:00:14.0: xHCI Host Controller
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.176707] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.177799] xhci_hcd 0000:00:14.0: hcc params 0x200077c1 hci version 0x100 quirks 0x00009810
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.177808] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.177948] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.177952] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.177956] usb usb1: Product: xHCI Host Controller
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.177959] usb usb1: Manufacturer: Linux 4.2.0-34-generic xhci-hcd
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.177962] usb usb1: SerialNumber: 0000:00:14.0
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.178232] hub 1-0:1.0: USB hub found
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.178251] hub 1-0:1.0: 6 ports detected
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.179933] xhci_hcd 0000:00:14.0: xHCI Host Controller
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.179940] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.180012] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.180055] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.180059] usb usb2: Product: xHCI Host Controller
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.180063] usb usb2: Manufacturer: Linux 4.2.0-34-generic xhci-hcd
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.180066] usb usb2: SerialNumber: 0000:00:14.0
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.180541] hub 2-0:1.0: USB hub found
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.180556] hub 2-0:1.0: 1 port detected
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.180790] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.180801] ehci-pci: EHCI PCI platform driver
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.180826] ehci-platform: EHCI generic platform driver
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.180853] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.180861] ohci-pci: OHCI PCI platform driver
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.180882] ohci-platform: OHCI generic platform driver
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.180903] uhci_hcd: USB Universal Host Controller Interface driver
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.181011] i8042: PNP: PS/2 Controller [PNP030b:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.183893] i8042: Detected active multiplexing controller, rev 1.1
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.185620] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.185631] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.185695] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.185754] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.185813] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.186300] mousedev: PS/2 mouse device common for all mice
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.187312] rtc_cmos 00:00: RTC can wake from S4
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.187512] rtc_cmos 00:00: rtc core: registered rtc_cmos as rtc0
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.187539] rtc_cmos 00:00: alarms up to one month, y3k, 242 bytes nvram
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.187560] i2c /dev entries driver
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.187710] device-mapper: uevent: version 1.0.3
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.188347] device-mapper: ioctl: 4.33.0-ioctl (2015-8-18) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.188373] Intel P-state driver initializing.
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.188707] ledtrig-cpu: registered to indicate activity on CPUs
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.188715] EFI Variables Facility v0.08 2004-May-17
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.190296] efivars: duplicate variable: AcpiGlobalVariable-c020489e-6db2-4ef2-9aa5-ca06fc11d36a
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.194174] PCCT header not found.
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.195713] NET: Registered protocol family 10
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.197281] NET: Registered protocol family 17
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.197308] Key type dns_resolver registered
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.198898] Loading compiled-in X.509 certificates
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.200343] Loaded X.509 cert 'Build time autogenerated kernel key: 544e45c0bde6f784077abca3de58e48fb525ee14'
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.200374] registered taskstats version 1
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.200400] zswap: loading zswap
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.200404] zswap: using zbud pool
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.200412] zswap: using lzo compressor
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.209148] Key type trusted registered
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.227001] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.227547] Key type encrypted registered
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.227559] AppArmor: AppArmor sha1 policy hashing enabled
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.227565] ima: No TPM chip found, activating TPM-bypass!
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.227610] evm: HMAC attrs: 0x1
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.229180]   Magic number: 12:543:583
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.229908] rtc_cmos 00:00: setting system clock to 2016-04-02 13:35:07 UTC (1459604107)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.230684] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.230689] EDD information not available.
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.230875] PM: Hibernation image not present or could not be loaded.
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.232285] Freeing unused kernel memory: 1464K (ffffffff81d37000 - ffffffff81ea5000)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.232291] Write protecting the kernel read-only data: 12288k
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.233731] Freeing unused kernel memory: 20K (ffff8800017fb000 - ffff880001800000)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.234529] Freeing unused kernel memory: 292K (ffff880001bb7000 - ffff880001c00000)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.271765] random: systemd-udevd urandom read with 11 bits of entropy available
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.337142] sdhci: Secure Digital Host Controller Interface driver
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.337147] sdhci: Copyright(c) Pierre Ossman
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.346130] hidraw: raw HID events driver (C) Jiri Kosina
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.357191] wmi: Mapper loaded
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.383218] ahci 0000:00:13.0: version 3.0
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.387887] [drm] Initialized drm 1.1.0 20060810
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.388781] rtsx_pci 0000:02:00.0: rtsx_pci_acquire_irq: pcr->msi_en = 1, pci->irq = 89
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.395564] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.395596] r8169 0000:02:00.2: can't disable ASPM; OS doesn't have ASPM control
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.396715] r8169 0000:02:00.2 eth0: RTL8402 at 0xffffc900006a6000, f8:32:e4:fb:c6:06, XID 04000800 IRQ 90
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.396767] ahci 0000:00:13.0: AHCI 0001.0300 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.396772] ahci 0000:00:13.0: flags: 64bit ncq pm led clo pio slum part deso sadm apst 
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.397760] scsi host0: ahci
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.398014] scsi host1: ahci
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.398098] ata1: SATA max UDMA/133 abar m2048@0xc3c15000 port 0xc3c15100 irq 88
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.398102] ata2: SATA max UDMA/133 abar m2048@0xc3c15000 port 0xc3c15180 irq 88
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.424986] [drm] Memory usable by graphics device = 2048M
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.424993] checking generic (a0000000 1d5000) vs hw (a0000000 10000000)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.424996] fb: switching to inteldrmfb from EFI VGA
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.425036] Console: switching to colour dummy device 80x25
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.425169] [drm] Replacing VGA console driver
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.427066] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.427072] [drm] Driver supports precise vblank timestamp query.
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.439185] MXM: GUID detected in BIOS
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.439311] ACPI Warning: \_SB_.PCI0.RP01.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.439417] ACPI Warning: \_SB_.PCI0.RP01.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.439744] pci 0000:01:00.0: optimus capabilities: enabled, status dynamic power, 
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.439749] VGA switcheroo: detected Optimus DSM method \_SB_.PCI0.RP01.PEGP handle
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.464820] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.487759] r8169 0000:02:00.2 enp2s0f2: renamed from eth0
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.488337] usb 1-3: new full-speed USB device number 2 using xhci_hcd
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.521457] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.527245] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input13
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.529562] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.529970] fbcon: inteldrmfb (fb0) is primary device
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.530065] Console: switching to colour frame buffer device 170x48
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.530109] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.530112] i915 0000:00:02.0: registered panic notifier
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.530741] ACPI: Video Device [PEGP] (multi-head: yes  rom: yes  post: no)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.530750] ACPI Error: [\_SB_.PCI0.GFX0.DD02._BCL] Namespace lookup failure, AE_NOT_FOUND (20150619/psargs-359)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.530758] ACPI Error: Method parse/execution failed [\_SB_.PCI0.RP01.PEGP.DD02._BCL] (Node ffff88015b0e7960), AE_NOT_FOUND (20150619/psparse-536)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.532460] input: FocalTechPS/2 FocalTech FocalTech Touchpad as /devices/platform/i8042/serio4/input/input12
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.536041] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:44/LNXVIDEO:01/input/input14
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.536597] [drm] Initialized i915 1.6.0 20150522 for 0000:00:02.0 on minor 0
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.537529] nouveau  [  DEVICE][0000:01:00.0] BOOT0  : 0xb06190b1
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.537534] nouveau  [  DEVICE][0000:01:00.0] Chipset: GK208B (NV106)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.537536] nouveau  [  DEVICE][0000:01:00.0] Family : NVE0
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.571405] nouveau  [   VBIOS][0000:01:00.0] using image from ACPI
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.571634] nouveau  [   VBIOS][0000:01:00.0] BIT signature found
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.571639] nouveau  [   VBIOS][0000:01:00.0] version 80.28.88.00.10
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.580541] nouveau  [   VBIOS][0000:01:00.0] running init tables
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.603549] nouveau  [     PMC][0000:01:00.0] MSI interrupts enabled
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.603631] nouveau  [     PFB][0000:01:00.0] RAM type: DDR3
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.603635] nouveau  [     PFB][0000:01:00.0] RAM size: 1024 MiB
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.603637] nouveau  [     PFB][0000:01:00.0]    ZCOMP: 0 tags
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.603681] nouveau E[   PIBUS][0000:01:00.0] HUB0: 0x6013d4 0x00005700 (0x1e708200)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.603714] nouveau E[   PIBUS][0000:01:00.0] HUB0: 0x10ecc0 0xffffffff (0x1c70822c)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.606201] nouveau  [    VOLT][0000:01:00.0] GPU voltage: 600000uv
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.617842] usb 1-3: New USB device found, idVendor=13d3, idProduct=3408
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.617847] usb 1-3: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.724960] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.725028] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.727062] ata2.00: ATAPI: HL-DT-ST DVDRAM GUC0N, AS01, max UDMA/133
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.729980] ata2.00: configured for UDMA/133
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.731241] ata1.00: ATA-8: ST1000LM024 HN-M101MBB, 2BA30001, max UDMA/133
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.731245] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.737510] ata1.00: configured for UDMA/133
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.737653] scsi 0:0:0:0: Direct-Access     ATA      ST1000LM024 HN-M 0001 PQ: 0 ANSI: 5
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.738407] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.738448] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.738455] sd 0:0:0:0: [sda] 4096-byte physical blocks
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.738638] sd 0:0:0:0: [sda] Write Protect is off
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.738643] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.738860] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.740165] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GUC0N     AS01 PQ: 0 ANSI: 5
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.763497] sr 1:0:0:0: [sr0] scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.763501] cdrom: Uniform CD-ROM driver Revision: 3.20
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.763857] sr 1:0:0:0: Attached scsi CD-ROM sr0
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.764009] sr 1:0:0:0: Attached scsi generic sg1 type 5
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.784678] usb 1-4: new high-speed USB device number 3 using xhci_hcd
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.797386]  sda: sda1 sda2 sda3 sda4 sda5 sda6
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.799081] sd 0:0:0:0: [sda] Attached SCSI disk
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.963766] usb 1-4: New USB device found, idVendor=04f2, idProduct=b48c
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.963773] usb 1-4: New USB device strings: Mfr=0, Product=1, SerialNumber=0
Apr  2 14:27:39 gabriel-X550MJ kernel: [    1.963776] usb 1-4: Product: USB2.0 VGA UVC WebCam
Apr  2 14:27:39 gabriel-X550MJ kernel: [    2.112833] tsc: Refined TSC clocksource calibration: 2166.669 MHz
Apr  2 14:27:39 gabriel-X550MJ kernel: [    2.112840] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x1f3b344e7d5, max_idle_ns: 440795250529 ns
Apr  2 14:27:39 gabriel-X550MJ kernel: [    2.905461] nouveau  [  PTHERM][0000:01:00.0] FAN control: none / external
Apr  2 14:27:39 gabriel-X550MJ kernel: [    2.905484] nouveau  [  PTHERM][0000:01:00.0] fan management: automatic
Apr  2 14:27:39 gabriel-X550MJ kernel: [    2.905507] nouveau  [  PTHERM][0000:01:00.0] internal sensor: yes
Apr  2 14:27:39 gabriel-X550MJ kernel: [    2.905568] nouveau  [     CLK][0000:01:00.0] 07: core 405 MHz memory 648 MHz 
Apr  2 14:27:39 gabriel-X550MJ kernel: [    2.905726] nouveau  [     CLK][0000:01:00.0] 0a: core 405-954 MHz memory 1620 MHz 
Apr  2 14:27:39 gabriel-X550MJ kernel: [    2.905923] nouveau  [     CLK][0000:01:00.0] 0f: core 405-954 MHz memory 1800 MHz 
Apr  2 14:27:39 gabriel-X550MJ kernel: [    2.906009] nouveau  [     CLK][0000:01:00.0] --: core 405 MHz memory 648 MHz 
Apr  2 14:27:39 gabriel-X550MJ kernel: [    2.978544] vga_switcheroo: enabled
Apr  2 14:27:39 gabriel-X550MJ kernel: [    2.979281] [TTM] Zone  kernel: Available graphics memory: 1965324 kiB
Apr  2 14:27:39 gabriel-X550MJ kernel: [    2.979284] [TTM] Initializing pool allocator
Apr  2 14:27:39 gabriel-X550MJ kernel: [    2.979294] [TTM] Initializing DMA pool allocator
Apr  2 14:27:39 gabriel-X550MJ kernel: [    2.979316] nouveau  [     DRM] VRAM: 1024 MiB
Apr  2 14:27:39 gabriel-X550MJ kernel: [    2.979320] nouveau  [     DRM] GART: 1048576 MiB
Apr  2 14:27:39 gabriel-X550MJ kernel: [    2.979326] nouveau W[     DRM] Pointer to TMDS table invalid
Apr  2 14:27:39 gabriel-X550MJ kernel: [    2.979329] nouveau  [     DRM] DCB version 4.0
Apr  2 14:27:39 gabriel-X550MJ kernel: [    2.979333] nouveau W[     DRM] Pointer to flat panel table invalid
Apr  2 14:27:39 gabriel-X550MJ kernel: [    2.988819] nouveau  [     DRM] MM: using COPY for buffer copies
Apr  2 14:27:39 gabriel-X550MJ kernel: [    2.988832] [drm] Initialized nouveau 1.2.2 20120801 for 0000:01:00.0 on minor 1
Apr  2 14:27:39 gabriel-X550MJ kernel: [    3.114672] clocksource: Switched to clocksource tsc
Apr  2 14:27:39 gabriel-X550MJ kernel: [    4.650051] random: nonblocking pool is initialized
Apr  2 14:27:39 gabriel-X550MJ kernel: [    7.989752] ACPI Warning: \_SB_.PCI0.RP01.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
Apr  2 14:27:39 gabriel-X550MJ kernel: [    7.990059] ACPI: \_SB_.PCI0.RP01.PEGP: failed to evaluate _DSM
Apr  2 14:27:39 gabriel-X550MJ kernel: [    7.990068] ACPI Warning: \_SB_.PCI0.RP01.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
Apr  2 14:27:39 gabriel-X550MJ kernel: [   14.198567] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
Apr  2 14:27:39 gabriel-X550MJ kernel: [   15.197945] efivars: duplicate variable: AcpiGlobalVariable-c020489e-6db2-4ef2-9aa5-ca06fc11d36a
Apr  2 14:27:39 gabriel-X550MJ kernel: [   17.820968] lp: driver loaded but no devices found
Apr  2 14:27:39 gabriel-X550MJ kernel: [   17.858309] ppdev: user-space parallel port driver
Apr  2 14:27:39 gabriel-X550MJ kernel: [   20.080557] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
Apr  2 14:27:39 gabriel-X550MJ kernel: [   20.437507] mei_txe 0000:00:1a.0: can't derive routing for PCI INT A
Apr  2 14:27:39 gabriel-X550MJ kernel: [   20.437513] mei_txe 0000:00:1a.0: PCI INT A: no GSI
Apr  2 14:27:39 gabriel-X550MJ kernel: [   20.533837] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr  2 14:27:39 gabriel-X550MJ kernel: [   21.143291] Bluetooth: Core ver 2.20
Apr  2 14:27:39 gabriel-X550MJ kernel: [   21.143318] NET: Registered protocol family 31
Apr  2 14:27:39 gabriel-X550MJ kernel: [   21.143320] Bluetooth: HCI device and connection manager initialized
Apr  2 14:27:39 gabriel-X550MJ kernel: [   21.143326] Bluetooth: HCI socket layer initialized
Apr  2 14:27:39 gabriel-X550MJ kernel: [   21.143331] Bluetooth: L2CAP socket layer initialized
Apr  2 14:27:39 gabriel-X550MJ kernel: [   21.143342] Bluetooth: SCO socket layer initialized
Apr  2 14:27:39 gabriel-X550MJ kernel: [   21.428997] usbcore: registered new interface driver btusb
Apr  2 14:27:39 gabriel-X550MJ kernel: [   21.492705] nouveau E[   PIBUS][0000:01:00.0] HUB0: 0x6013d4 0x00005700 (0x1c708200)
Apr  2 14:27:39 gabriel-X550MJ kernel: [   21.492741] nouveau E[   PIBUS][0000:01:00.0] HUB0: 0x10ecc0 0xffffffff (0x1c70822c)
Apr  2 14:27:39 gabriel-X550MJ kernel: [   21.528227] snd_hda_intel 0000:00:1b.0: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
Apr  2 14:27:39 gabriel-X550MJ kernel: [   21.837358] ath: phy0: WB335 2-ANT card detected
Apr  2 14:27:39 gabriel-X550MJ kernel: [   21.837363] ath: phy0: Set BT/WLAN RX diversity capability
Apr  2 14:27:39 gabriel-X550MJ kernel: [   21.843847] ath: phy0: Enable LNA combining
Apr  2 14:27:39 gabriel-X550MJ kernel: [   21.844954] ath: phy0: ASPM enabled: 0x42
Apr  2 14:27:39 gabriel-X550MJ kernel: [   21.844959] ath: EEPROM regdomain: 0x6a
Apr  2 14:27:39 gabriel-X550MJ kernel: [   21.844961] ath: EEPROM indicates we should expect a direct regpair map
Apr  2 14:27:39 gabriel-X550MJ kernel: [   21.844964] ath: Country alpha2 being used: 00
Apr  2 14:27:39 gabriel-X550MJ kernel: [   21.844966] ath: Regpair used: 0x6a
Apr  2 14:27:39 gabriel-X550MJ kernel: [   21.878854] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
Apr  2 14:27:39 gabriel-X550MJ kernel: [   21.879384] ieee80211 phy0: Atheros AR9565 Rev:1 mem=0xffffc90001300000, irq=19
Apr  2 14:27:39 gabriel-X550MJ kernel: [   21.902490] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC270: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
Apr  2 14:27:39 gabriel-X550MJ kernel: [   21.902496] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
Apr  2 14:27:39 gabriel-X550MJ kernel: [   21.902500] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
Apr  2 14:27:39 gabriel-X550MJ kernel: [   21.902502] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
Apr  2 14:27:39 gabriel-X550MJ kernel: [   21.902505] snd_hda_codec_realtek hdaudioC0D0:    inputs:
Apr  2 14:27:39 gabriel-X550MJ kernel: [   21.902508] snd_hda_codec_realtek hdaudioC0D0:      Mic=0x19
Apr  2 14:27:39 gabriel-X550MJ kernel: [   21.924945] usb 1-3: USB disconnect, device number 2
Apr  2 14:27:39 gabriel-X550MJ kernel: [   21.925075] usbcore: registered new interface driver ath3k
Apr  2 14:27:39 gabriel-X550MJ kernel: [   21.966928] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
Apr  2 14:27:39 gabriel-X550MJ kernel: [   21.967045] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
Apr  2 14:27:39 gabriel-X550MJ kernel: [   22.046557] media: Linux media interface: v0.10
Apr  2 14:27:39 gabriel-X550MJ kernel: [   22.106698] ath9k 0000:03:00.0 wlp3s0: renamed from wlan0
Apr  2 14:27:39 gabriel-X550MJ kernel: [   22.145254] Linux video capture interface: v2.00
Apr  2 14:27:39 gabriel-X550MJ kernel: [   22.197164] usb 1-3: new full-speed USB device number 4 using xhci_hcd
Apr  2 14:27:39 gabriel-X550MJ kernel: [   22.237819] asus_wmi: ASUS WMI generic driver loaded
Apr  2 14:27:39 gabriel-X550MJ kernel: [   22.337378] asus_wmi: Initialization: 0x1
Apr  2 14:27:39 gabriel-X550MJ kernel: [   22.337443] asus_wmi: BIOS WMI version: 7.9
Apr  2 14:27:39 gabriel-X550MJ kernel: [   22.337518] asus_wmi: SFUN value: 0x4a0877
Apr  2 14:27:39 gabriel-X550MJ kernel: [   22.339131] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input17
Apr  2 14:27:39 gabriel-X550MJ kernel: [   22.341648] asus_wmi: Number of fans: 1
Apr  2 14:27:39 gabriel-X550MJ kernel: [   22.503067] intel_soc_dts_thermal: request_threaded_irq ret -22
Apr  2 14:27:39 gabriel-X550MJ kernel: [   22.531042] intel_soc_dts_thermal: request_threaded_irq ret -22
Apr  2 14:27:39 gabriel-X550MJ kernel: [   22.554001] intel_soc_dts_thermal: request_threaded_irq ret -22
Apr  2 14:27:39 gabriel-X550MJ kernel: [   22.578192] intel_soc_dts_thermal: request_threaded_irq ret -22
Apr  2 14:27:39 gabriel-X550MJ kernel: [   22.580255] intel_rapl: Found RAPL domain package
Apr  2 14:27:39 gabriel-X550MJ kernel: [   22.580262] intel_rapl: Found RAPL domain core
Apr  2 14:27:39 gabriel-X550MJ kernel: [   22.966611] uvcvideo: Found UVC 1.00 device USB2.0 VGA UVC WebCam (04f2:b48c)
Apr  2 14:27:39 gabriel-X550MJ kernel: [   23.009629] input: USB2.0 VGA UVC WebCam as /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.0/input/input18
Apr  2 14:27:39 gabriel-X550MJ kernel: [   23.009746] usbcore: registered new interface driver uvcvideo
Apr  2 14:27:39 gabriel-X550MJ kernel: [   23.009749] USB Video Class driver (1.1.1)
Apr  2 14:27:39 gabriel-X550MJ kernel: [   23.527543] cfg80211: World regulatory domain updated:
Apr  2 14:27:39 gabriel-X550MJ kernel: [   23.527550] cfg80211:  DFS Master region: unset
Apr  2 14:27:39 gabriel-X550MJ kernel: [   23.527552] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Apr  2 14:27:39 gabriel-X550MJ kernel: [   23.527556] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Apr  2 14:27:39 gabriel-X550MJ kernel: [   23.527558] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Apr  2 14:27:39 gabriel-X550MJ kernel: [   23.527561] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
Apr  2 14:27:39 gabriel-X550MJ kernel: [   23.527564] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
Apr  2 14:27:39 gabriel-X550MJ kernel: [   23.527567] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
Apr  2 14:27:39 gabriel-X550MJ kernel: [   23.527570] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
Apr  2 14:27:39 gabriel-X550MJ kernel: [   23.527573] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
Apr  2 14:27:39 gabriel-X550MJ kernel: [   23.527575] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
Apr  2 14:27:39 gabriel-X550MJ kernel: [   25.019236] Adding 4077564k swap on /dev/sda6.  Priority:-1 extents:1 across:4077564k FS
Apr  2 14:27:39 gabriel-X550MJ kernel: [   26.845072] ACPI Warning: \_SB_.PCI0.RP01.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
Apr  2 14:27:39 gabriel-X550MJ kernel: [   26.845322] ACPI: \_SB_.PCI0.RP01.PEGP: failed to evaluate _DSM
Apr  2 14:27:39 gabriel-X550MJ kernel: [   26.845331] ACPI Warning: \_SB_.PCI0.RP01.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
Apr  2 14:27:39 gabriel-X550MJ kernel: [   30.791365] audit: type=1400 audit(1459603653.889:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=506 comm="apparmor_parser"
Apr  2 14:27:39 gabriel-X550MJ kernel: [   30.791381] audit: type=1400 audit(1459603653.889:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=506 comm="apparmor_parser"
Apr  2 14:27:39 gabriel-X550MJ kernel: [   30.957740] audit: type=1400 audit(1459603654.057:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=506 comm="apparmor_parser"
Apr  2 14:27:39 gabriel-X550MJ kernel: [   30.957758] audit: type=1400 audit(1459603654.057:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=506 comm="apparmor_parser"
Apr  2 14:27:39 gabriel-X550MJ kernel: [   30.957770] audit: type=1400 audit(1459603654.057:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=506 comm="apparmor_parser"
Apr  2 14:27:39 gabriel-X550MJ kernel: [   30.957782] audit: type=1400 audit(1459603654.057:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=506 comm="apparmor_parser"
Apr  2 14:27:39 gabriel-X550MJ kernel: [   31.384868] audit: type=1400 audit(1459603654.485:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=506 comm="apparmor_parser"
Apr  2 14:27:39 gabriel-X550MJ kernel: [   31.384885] audit: type=1400 audit(1459603654.485:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=506 comm="apparmor_parser"
Apr  2 14:27:39 gabriel-X550MJ kernel: [   31.384895] audit: type=1400 audit(1459603654.485:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=506 comm="apparmor_parser"
Apr  2 14:27:39 gabriel-X550MJ kernel: [   31.384905] audit: type=1400 audit(1459603654.485:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=506 comm="apparmor_parser"
Apr  2 14:27:39 gabriel-X550MJ kernel: [   32.906187] nouveau E[   PIBUS][0000:01:00.0] HUB0: 0x6013d4 0x00005700 (0x1c708200)
Apr  2 14:27:39 gabriel-X550MJ kernel: [   32.906260] nouveau E[   PIBUS][0000:01:00.0] HUB0: 0x10ecc0 0xffffffff (0x1d70822c)
Apr  2 14:27:39 gabriel-X550MJ kernel: [   35.409626] cgroup: new mount options do not match the existing superblock, will be ignored
Apr  2 14:27:41 gabriel-X550MJ kernel: [   37.970013] ACPI Warning: \_SB_.PCI0.RP01.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
Apr  2 14:27:41 gabriel-X550MJ kernel: [   37.970264] ACPI: \_SB_.PCI0.RP01.PEGP: failed to evaluate _DSM
Apr  2 14:27:41 gabriel-X550MJ kernel: [   37.970272] ACPI Warning: \_SB_.PCI0.RP01.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
Apr  2 14:27:41 gabriel-X550MJ kernel: [   38.571692] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
Apr  2 14:27:41 gabriel-X550MJ kernel: [   38.584089] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
Apr  2 14:27:41 gabriel-X550MJ kernel: [   38.606916] IPv6: ADDRCONF(NETDEV_UP): enp2s0f2: link is not ready
Apr  2 14:27:41 gabriel-X550MJ kernel: [   38.716949] r8169 0000:02:00.2 enp2s0f2: link down
Apr  2 14:27:41 gabriel-X550MJ kernel: [   38.717003] IPv6: ADDRCONF(NETDEV_UP): enp2s0f2: link is not ready
Apr  2 14:27:41 gabriel-X550MJ kernel: [   38.835826] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
Apr  2 14:27:42 gabriel-X550MJ kernel: [   39.171114] nouveau E[   PIBUS][0000:01:00.0] HUB0: 0x10ecc0 0xffffffff (0x1970822c)
Apr  2 14:27:42 gabriel-X550MJ kernel: [   39.719360] wlp3s0: authenticate with 78:8d:f7:05:8a:18
Apr  2 14:27:42 gabriel-X550MJ kernel: [   39.731685] wlp3s0: send auth to 78:8d:f7:05:8a:18 (try 1/3)
Apr  2 14:27:42 gabriel-X550MJ kernel: [   39.734771] wlp3s0: authenticated
Apr  2 14:27:42 gabriel-X550MJ kernel: [   39.740580] wlp3s0: associate with 78:8d:f7:05:8a:18 (try 1/3)
Apr  2 14:27:42 gabriel-X550MJ kernel: [   39.755923] wlp3s0: RX AssocResp from 78:8d:f7:05:8a:18 (capab=0xc31 status=0 aid=12)
Apr  2 14:27:42 gabriel-X550MJ kernel: [   39.756023] wlp3s0: associated
Apr  2 14:27:42 gabriel-X550MJ kernel: [   39.756072] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
Apr  2 14:27:46 gabriel-X550MJ kernel: [   43.268694] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Apr  2 14:27:46 gabriel-X550MJ kernel: [   43.268701] Bluetooth: BNEP filters: protocol multicast
Apr  2 14:27:46 gabriel-X550MJ kernel: [   43.268711] Bluetooth: BNEP socket layer initialized
Apr  2 14:27:48 gabriel-X550MJ kernel: [   45.836597] ACPI Warning: \_SB_.PCI0.RP01.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
Apr  2 14:27:48 gabriel-X550MJ kernel: [   45.836855] ACPI: \_SB_.PCI0.RP01.PEGP: failed to evaluate _DSM
Apr  2 14:27:48 gabriel-X550MJ kernel: [   45.836863] ACPI Warning: \_SB_.PCI0.RP01.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
Apr  2 14:27:55 gabriel-X550MJ gnome-session[1390]: Entering running state




Another crash.... kernel log file before the crash (  14:49 )

> 
Apr  2 14:27:46 gabriel-X550MJ kernel: [   43.268701] Bluetooth: BNEP filters: protocol multicast
Apr  2 14:27:46 gabriel-X550MJ kernel: [   43.268711] Bluetooth: BNEP socket layer initialized
Apr  2 14:27:48 gabriel-X550MJ kernel: [   45.836597] ACPI Warning: \_SB_.PCI0.RP01.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
Apr  2 14:27:48 gabriel-X550MJ kernel: [   45.836855] ACPI: \_SB_.PCI0.RP01.PEGP: failed to evaluate _DSM
Apr  2 14:27:48 gabriel-X550MJ kernel: [   45.836863] ACPI Warning: \_SB_.PCI0.RP01.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
Apr  2 14:27:55 gabriel-X550MJ gnome-session[1390]: Entering running state
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] Initializing cgroup subsys cpuset
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] Initializing cgroup subsys cpu
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] Initializing cgroup subsys cpuacct
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] Linux version 4.2.0-34-generic (buildd@lgw01-54) (gcc version 5.2.1 20151010 (Ubuntu 5.2.1-22ubuntu2) ) #39-Ubuntu SMP Thu Mar 10 22:13:01 UTC 2016 (Ubuntu 4.2.0-34.39-generic 4.2.8-ckt4)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-34-generic.efi.signed root=UUID=cf328262-98b6-4044-ad1e-3e3d89b8d6f9 ro quiet splash vt.handoff=7
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] KERNEL supported cpus:
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]   Intel GenuineIntel
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]   AMD AuthenticAMD
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]   Centaur CentaurHauls
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] x86/fpu: Legacy x87 FPU detected.
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] x86/fpu: Using 'lazy' FPU context switches.
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000008efff] usable
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] BIOS-e820: [mem 0x000000000008f000-0x000000000008ffff] ACPI NVS
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] BIOS-e820: [mem 0x0000000000090000-0x000000000009dfff] usable
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] BIOS-e820: [mem 0x000000000009e000-0x000000000009ffff] reserved
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000200fffff] reserved
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] BIOS-e820: [mem 0x0000000020100000-0x0000000098cf1fff] usable
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] BIOS-e820: [mem 0x0000000098cf2000-0x0000000098d21fff] reserved
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] BIOS-e820: [mem 0x0000000098d22000-0x0000000098e5ffff] usable
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] BIOS-e820: [mem 0x0000000098e60000-0x00000000993a0fff] ACPI NVS
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] BIOS-e820: [mem 0x00000000993a1000-0x0000000099b8efff] reserved
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] BIOS-e820: [mem 0x0000000099b8f000-0x0000000099b8ffff] usable
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] BIOS-e820: [mem 0x0000000099b90000-0x0000000099bd1fff] reserved
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] BIOS-e820: [mem 0x0000000099bd2000-0x0000000099d47fff] usable
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] BIOS-e820: [mem 0x0000000099d48000-0x0000000099ff9fff] reserved
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] BIOS-e820: [mem 0x0000000099ffa000-0x0000000099ffffff] usable
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] BIOS-e820: [mem 0x00000000e00f8000-0x00000000e00f8fff] reserved
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed01000-0x00000000fed01fff] reserved
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] BIOS-e820: [mem 0x00000000ffc00000-0x00000000ffffffff] reserved
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000015fffffff] usable
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] NX (Execute Disable) protection: active
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] e820: update [mem 0x8a62a018-0x8a63a057] usable ==> usable
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] e820: update [mem 0x8a612018-0x8a629c57] usable ==> usable
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] extended physical RAM map:
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x0000000000000000-0x000000000008efff] usable
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x000000000008f000-0x000000000008ffff] ACPI NVS
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x0000000000090000-0x000000000009dfff] usable
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x000000000009e000-0x000000000009ffff] reserved
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x0000000000100000-0x000000001fffffff] usable
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x0000000020000000-0x00000000200fffff] reserved
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x0000000020100000-0x000000008a612017] usable
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x000000008a612018-0x000000008a629c57] usable
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x000000008a629c58-0x000000008a62a017] usable
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x000000008a62a018-0x000000008a63a057] usable
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x000000008a63a058-0x0000000098cf1fff] usable
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x0000000098cf2000-0x0000000098d21fff] reserved
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x0000000098d22000-0x0000000098e5ffff] usable
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x0000000098e60000-0x00000000993a0fff] ACPI NVS
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x00000000993a1000-0x0000000099b8efff] reserved
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x0000000099b8f000-0x0000000099b8ffff] usable
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x0000000099b90000-0x0000000099bd1fff] reserved
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x0000000099bd2000-0x0000000099d47fff] usable
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x0000000099d48000-0x0000000099ff9fff] reserved
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x0000000099ffa000-0x0000000099ffffff] usable
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x00000000e00f8000-0x00000000e00f8fff] reserved
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x00000000fed01000-0x00000000fed01fff] reserved
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x00000000ffc00000-0x00000000ffffffff] reserved
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] reserve setup_data: [mem 0x0000000100000000-0x000000015fffffff] usable
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] efi: EFI v2.31 by American Megatrends
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] efi:  ESRT=0x99b2a198  ACPI=0x98ee6000  ACPI 2.0=0x98ee6000  SMBIOS=0x99a78d98 
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] esrt: Reserving ESRT space from 0x0000000099b2a198 to 0x0000000099b2a1d0.
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] SMBIOS 2.8 present.
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] DMI: ASUSTeK COMPUTER INC. X550MJ/X550MJ, BIOS X550MJ.300 08/17/2015
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] e820: last_pfn = 0x160000 max_arch_pfn = 0x400000000
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] MTRR default type: uncachable
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] MTRR fixed ranges enabled:
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]   00000-9FFFF write-back
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]   A0000-FFFFF uncachable
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] MTRR variable ranges enabled:
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]   0 base 000000000 mask F80000000 write-back
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]   1 base 080000000 mask FE0000000 write-back
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]   2 base 09A000000 mask FFE000000 uncachable
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]   3 base 09C000000 mask FFC000000 uncachable
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]   4 base 100000000 mask F80000000 write-back
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]   5 disabled
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]   6 disabled
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]   7 disabled
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] original variable MTRRs
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] reg 1, base: 2GB, range: 512MB, type WB
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] reg 2, base: 2464MB, range: 32MB, type UC
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] reg 3, base: 2496MB, range: 64MB, type UC
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] reg 4, base: 4GB, range: 2GB, type WB
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] total RAM covered: 4512M
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] Found optimal setting for mtrr clean up
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]  gran_size: 64K     chunk_size: 64K     num_reg: 5      lose cover RAM: 0G
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] New variable MTRRs
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] reg 1, base: 2GB, range: 256MB, type WB
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] reg 2, base: 2304MB, range: 128MB, type WB
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] reg 3, base: 2432MB, range: 32MB, type WB
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] reg 4, base: 4GB, range: 2GB, type WB
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] e820: update [mem 0x9a000000-0xffffffff] usable ==> reserved
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] e820: last_pfn = 0x9a000 max_arch_pfn = 0x400000000
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] Scanning 1 areas for low memory corruption
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]  [mem 0x00000000-0x000fffff] page 4k
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] BRK [0x01ff1000, 0x01ff1fff] PGTABLE
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] BRK [0x01ff2000, 0x01ff2fff] PGTABLE
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] BRK [0x01ff3000, 0x01ff3fff] PGTABLE
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] init_memory_mapping: [mem 0x15fe00000-0x15fffffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]  [mem 0x15fe00000-0x15fffffff] page 2M
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] BRK [0x01ff4000, 0x01ff4fff] PGTABLE
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] init_memory_mapping: [mem 0x140000000-0x15fdfffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]  [mem 0x140000000-0x15fdfffff] page 2M
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] init_memory_mapping: [mem 0x00100000-0x1fffffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]  [mem 0x00100000-0x001fffff] page 4k
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]  [mem 0x00200000-0x1fffffff] page 2M
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] init_memory_mapping: [mem 0x20100000-0x98cf1fff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]  [mem 0x20100000-0x201fffff] page 4k
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]  [mem 0x20200000-0x98bfffff] page 2M
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]  [mem 0x98c00000-0x98cf1fff] page 4k
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] BRK [0x01ff5000, 0x01ff5fff] PGTABLE
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] BRK [0x01ff6000, 0x01ff6fff] PGTABLE
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] init_memory_mapping: [mem 0x98d22000-0x98e5ffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]  [mem 0x98d22000-0x98e5ffff] page 4k
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] init_memory_mapping: [mem 0x99b8f000-0x99b8ffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]  [mem 0x99b8f000-0x99b8ffff] page 4k
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] init_memory_mapping: [mem 0x99bd2000-0x99d47fff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]  [mem 0x99bd2000-0x99d47fff] page 4k
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] init_memory_mapping: [mem 0x99ffa000-0x99ffffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]  [mem 0x99ffa000-0x99ffffff] page 4k
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] init_memory_mapping: [mem 0x100000000-0x13fffffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]  [mem 0x100000000-0x13fffffff] page 2M
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] RAMDISK: [mem 0x3dff5000-0x3fffafff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] ACPI: Early table checksum verification disabled
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] ACPI: RSDP 0x0000000098EE6000 000024 (v02 _ASUS_)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] ACPI: XSDT 0x0000000098EE6088 00009C (v01 _ASUS_ Notebook 01072009 AMI  00010013)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] ACPI: FACP 0x0000000098EF7ED0 00010C (v05 _ASUS_ Notebook 01072009 AMI  00010013)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] ACPI BIOS Warning (bug): 32/64X length mismatch in FADT/Gpe0Block: 128/32 (20150619/tbfadt-623)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] ACPI: DSDT 0x0000000098EE61B8 011D11 (v02 _ASUS_ Notebook 01072009 INTL 20120913)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] ACPI: FACS 0x00000000993A0F80 000040
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] ACPI: APIC 0x0000000098EF7FE0 000084 (v03 _ASUS_ Notebook 01072009 AMI  00010013)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] ACPI: FPDT 0x0000000098EF8068 000044 (v01 _ASUS_ Notebook 01072009 AMI  00010013)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] ACPI: MCFG 0x0000000098EF80B0 00003C (v01 _ASUS_ Notebook 01072009 MSFT 00000097)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] ACPI: LPIT 0x0000000098EF80F0 000104 (v01 _ASUS_ Notebook 00000003 VLV2 0100000D)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] ACPI: ECDT 0x0000000098EF81F8 0000C1 (v01 _ASUS_ Notebook 01072009 AMI. 00000005)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] ACPI: HPET 0x0000000098EF82C0 000038 (v01 _ASUS_ Notebook 01072009 AMI. 00000005)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] ACPI: SSDT 0x0000000098EF82F8 000763 (v01 PmRef  CpuPm    00003000 INTL 20061109)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] ACPI: SSDT 0x0000000098EF8A60 000290 (v01 PmRef  Cpu0Tst  00003000 INTL 20061109)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] ACPI: SSDT 0x0000000098EF8CF0 00017A (v01 PmRef  ApTst    00003000 INTL 20061109)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] ACPI: UEFI 0x0000000098EF8E70 000042 (v01 _ASUS_ Notebook 00000000      00000000)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] ACPI: SSDT 0x0000000098EF8EB8 000915 (v01 SgRef  SgPch    00001000 INTL 20061109)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] ACPI: SSDT 0x0000000098EF97D0 0013E4 (v01 OptRef NvdPch   00001000 INTL 20061109)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] ACPI: BGRT 0x0000000098EFABB8 000038 (v00 _ASUS_ Notebook 01072009 AMI  00010013)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] ACPI: MSDM 0x0000000098D1FF98 000055 (v03 _ASUS_ Notebook 00000000 ASUS 00000001)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] No NUMA configuration found
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x000000015fffffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] NODE_DATA(0) allocated [mem 0x15fff4000-0x15fff8fff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]  [ffffea0000000000-ffffea00057fffff] PMD -> [ffff88015b600000-ffff88015f5fffff] on node 0
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] Zone ranges:
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]   Normal   [mem 0x0000000100000000-0x000000015fffffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] Movable zone start for each node
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] Early memory node ranges
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]   node   0: [mem 0x0000000000001000-0x000000000008efff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]   node   0: [mem 0x0000000000090000-0x000000000009dfff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]   node   0: [mem 0x0000000000100000-0x000000001fffffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]   node   0: [mem 0x0000000020100000-0x0000000098cf1fff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]   node   0: [mem 0x0000000098d22000-0x0000000098e5ffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]   node   0: [mem 0x0000000099b8f000-0x0000000099b8ffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]   node   0: [mem 0x0000000099bd2000-0x0000000099d47fff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]   node   0: [mem 0x0000000099ffa000-0x0000000099ffffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]   node   0: [mem 0x0000000100000000-0x000000015fffffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000015fffffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] On node 0 totalpages: 1019465
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]   DMA zone: 21 pages reserved
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]   DMA zone: 3996 pages, LIFO batch:0
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]   DMA32 zone: 9723 pages used for memmap
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]   DMA32 zone: 622253 pages, LIFO batch:31
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]   Normal zone: 6144 pages used for memmap
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]   Normal zone: 393216 pages, LIFO batch:31
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] tboot: non-0 tboot_addr but it is not of type E820_RESERVED
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] x86/hpet: Will disable the HPET for this platform because it's not reliable
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] Reserving Intel graphics stolen memory at 0x9b000000-0x9effffff
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-86
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] ACPI: IRQ0 used by override.
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] ACPI: IRQ9 used by override.
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0008f000-0x0008ffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0x20000000-0x200fffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0x8a612000-0x8a612fff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0x8a629000-0x8a629fff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0x8a62a000-0x8a62afff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0x8a63a000-0x8a63afff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0x98cf2000-0x98d21fff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0x98e60000-0x993a0fff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0x993a1000-0x99b8efff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0x99b90000-0x99bd1fff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0x99d48000-0x99ff9fff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9a000000-0x9affffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9b000000-0x9effffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f000000-0xe00f7fff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe00f8000-0xe00f8fff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe00f9000-0xfed00fff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed01000-0xfed01fff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed02000-0xffbfffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffc00000-0xffffffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] e820: [mem 0x9f000000-0xe00f7fff] available for PCI devices
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] PERCPU: Embedded 33 pages/cpu @ffff88015fc00000 s96728 r8192 d30248 u524288
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] pcpu-alloc: s96728 r8192 d30248 u524288 alloc=1*2097152
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1003513
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] Policy zone: Normal
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-34-generic.efi.signed root=UUID=cf328262-98b6-4044-ad1e-3e3d89b8d6f9 ro quiet splash vt.handoff=7
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] Memory: 3665116K/4077860K available (8158K kernel code, 1238K rwdata, 3804K rodata, 1464K init, 1292K bss, 412744K reserved, 0K cma-reserved)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] Hierarchical RCU implementation.
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]     Build-time adjustment of leaf fanout to 64.
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=4
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] NR_IRQS:16640 nr_irqs:1024 16
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]     Offload RCU callbacks from all CPUs
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000]     Offload RCU callbacks from CPUs: 0-3.
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] vt handoff: transparent VT on vt#7
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] Console: colour dummy device 80x25
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] console [tty0] enabled
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] Maximum core-clock to bus-clock ratio: 0x1a
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] Resolved frequency ID: 0, frequency: 83200 KHz
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] TSC runs at 2163200 KHz
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] lapic_timer_frequency = 332800
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000000] tsc: Detected 2163.200 MHz processor
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000038] Calibrating delay loop (skipped), value calculated using timer frequency.. 4326.40 BogoMIPS (lpj=8652800)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000043] pid_max: default: 32768 minimum: 301
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.000055] ACPI: Core revision 20150619
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.034892] ACPI: All ACPI Tables successfully acquired
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.036763] Security Framework initialized
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.036783] AppArmor: AppArmor initialized
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.036786] Yama: becoming mindful.
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.037282] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.039038] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.039836] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.039852] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.040246] Initializing cgroup subsys blkio
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.040256] Initializing cgroup subsys memory
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.040272] Initializing cgroup subsys devices
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.040278] Initializing cgroup subsys freezer
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.040283] Initializing cgroup subsys net_cls
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.040288] Initializing cgroup subsys perf_event
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.040293] Initializing cgroup subsys net_prio
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.040298] Initializing cgroup subsys hugetlb
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.040325] CPU: Physical Processor ID: 0
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.040328] CPU: Processor Core ID: 0
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.040334] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.040336] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.045089] mce: CPU supports 6 MCE banks
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.045098] CPU0: Thermal monitoring handled by SMI
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.045103] process: using mwait in idle threads
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.045109] Last level iTLB entries: 4KB 48, 2MB 0, 4MB 0
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.045112] Last level dTLB entries: 4KB 128, 2MB 16, 4MB 16, 1GB 0
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.045434] Freeing SMP alternatives memory: 28K (ffffffff81ea5000 - ffffffff81eac000)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.047204] Ignoring BGRT: invalid status 0 (expected 1)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.064424] ftrace: allocating 30940 entries in 121 pages
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.081789] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.121467] TSC deadline timer enabled
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.121472] smpboot: CPU0: Intel(R) Pentium(R) CPU  N3540  @ 2.16GHz (fam: 06, model: 37, stepping: 08)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.121509] Performance Events: PEBS fmt2+, 8-deep LBR, Silvermont events, full-width counters, Intel PMU driver.
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.121524] ... version:                3
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.121526] ... bit width:              40
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.121528] ... generic registers:      2
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.121530] ... value mask:             000000ffffffffff
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.121532] ... max period:             000000ffffffffff
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.121534] ... fixed-purpose events:   3
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.121536] ... event mask:             0000000700000003
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.123008] x86: Booting SMP configuration:
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.123013] .... node  #0, CPUs:      #1
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.128782] CPU1: Thermal monitoring handled by SMI
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.130973] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.131221]  #2
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.136989] CPU2: Thermal monitoring handled by SMI
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.139334]  #3<7>[    0.145103] CPU3: Thermal monitoring handled by SMI
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.147237] x86: Booted up 1 node, 4 CPUs
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.147243] smpboot: Total of 4 processors activated (17305.60 BogoMIPS)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.148394] devtmpfs: initialized
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.155078] evm: security.selinux
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.155081] evm: security.SMACK64
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.155083] evm: security.SMACK64EXEC
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.155085] evm: security.SMACK64TRANSMUTE
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.155087] evm: security.SMACK64MMAP
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.155089] evm: security.ima
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.155091] evm: security.capability
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.155239] PM: Registering ACPI NVS region [mem 0x0008f000-0x0008ffff] (4096 bytes)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.155243] PM: Registering ACPI NVS region [mem 0x98e60000-0x993a0fff] (5509120 bytes)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.155670] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.155827] pinctrl core: initialized pinctrl subsystem
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.156191] RTC time: 13:50:21, date: 04/02/16
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.156460] NET: Registered protocol family 16
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.166938] cpuidle: using governor ladder
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.170966] cpuidle: using governor menu
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.171273] ACPI: bus type PCI registered
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.171278] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.171415] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.171420] PCI: not using MMCONFIG
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.171423] PCI: Using configuration type 1 for base access
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.176631] ACPI: Added _OSI(Module Device)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.176648] ACPI: Added _OSI(Processor Device)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.176660] ACPI: Added _OSI(3.0 _SCP Extensions)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.176670] ACPI: Added _OSI(Processor Aggregator Device)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.181142] ACPI : EC: EC description table is found, configuring boot EC
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.181164] ACPI : EC: EC started
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.195668] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.199975] ACPI: Dynamic OEM Table Load:
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.199987] ACPI: SSDT 0xFFFF88015A6BA000 00045B (v01 PmRef  Cpu0Ist  00003000 INTL 20061109)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.201299] ACPI: Dynamic OEM Table Load:
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.201310] ACPI: SSDT 0xFFFF88015A6BA800 000433 (v01 PmRef  Cpu0Cst  00003001 INTL 20061109)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.203013] ACPI: Dynamic OEM Table Load:
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.203022] ACPI: SSDT 0xFFFF88015A746400 00015F (v01 PmRef  ApIst    00003000 INTL 20061109)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.204286] ACPI: Dynamic OEM Table Load:
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.204295] ACPI: SSDT 0xFFFF88015A730240 00008D (v01 PmRef  ApCst    00003000 INTL 20061109)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.206847] ACPI: Interpreter enabled
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.206861] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20150619/hwxface-580)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.206871] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150619/hwxface-580)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.206897] ACPI: (supports S0 S3 S4 S5)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.206901] ACPI: Using IOAPIC for interrupt routing
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.206942] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.207925] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.207976] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.217349] ACPI: Power Resource [PC05] (on)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.220104] ACPI: Power Resource [USBC] (on)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.222079] ACPI: Power Resource [PLPE] (on)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.222450] ACPI: Power Resource [PLPE] (on)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.227508] ACPI: Power Resource [CLK0] (on)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.227591] ACPI: Power Resource [CLK1] (on)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.231637] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.231648] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.231730] \_SB_.PCI0:_OSC invalid UUID
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.231733] _OSC request data:1 1f 0 
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.231741] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.232387] PCI host bridge to bus 0000:00
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.232393] pci_bus 0000:00: root bus resource [bus 00-ff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.232398] pci_bus 0000:00: root bus resource [io  0x0070-0x0077]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.232401] pci_bus 0000:00: root bus resource [io  0x0000-0x006f window]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.232405] pci_bus 0000:00: root bus resource [io  0x0078-0x0cf7 window]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.232409] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.232413] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.232417] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff window]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.232420] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000fffff window]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.232424] pci_bus 0000:00: root bus resource [mem 0xa0000000-0xc3c15ffe window]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.232436] pci 0000:00:00.0: [8086:0f00] type 00 class 0x060000
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.232644] pci 0000:00:02.0: [8086:0f31] type 00 class 0x030000
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.232658] pci 0000:00:02.0: reg 0x10: [mem 0xc3400000-0xc37fffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.232671] pci 0000:00:02.0: reg 0x18: [mem 0xa0000000-0xafffffff pref]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.232683] pci 0000:00:02.0: reg 0x20: [io  0xf080-0xf087]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.232886] pci 0000:00:13.0: [8086:0f23] type 00 class 0x010601
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.232906] pci 0000:00:13.0: reg 0x10: [io  0xf070-0xf077]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.232917] pci 0000:00:13.0: reg 0x14: [io  0xf060-0xf063]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.232927] pci 0000:00:13.0: reg 0x18: [io  0xf050-0xf057]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.232938] pci 0000:00:13.0: reg 0x1c: [io  0xf040-0xf043]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.232948] pci 0000:00:13.0: reg 0x20: [io  0xf020-0xf03f]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.232959] pci 0000:00:13.0: reg 0x24: [mem 0xc3c15000-0xc3c157ff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.233003] pci 0000:00:13.0: PME# supported from D3hot
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.233172] pci 0000:00:14.0: [8086:0f35] type 00 class 0x0c0330
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.233192] pci 0000:00:14.0: reg 0x10: [mem 0xc3c00000-0xc3c0ffff 64bit]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.233252] pci 0000:00:14.0: PME# supported from D3hot D3cold
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.233384] pci 0000:00:14.0: System wakeup disabled by ACPI
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.233464] pci 0000:00:1a.0: [8086:0f18] type 00 class 0x108000
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.233490] pci 0000:00:1a.0: reg 0x10: [mem 0xc3900000-0xc39fffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.233505] pci 0000:00:1a.0: reg 0x14: [mem 0xc3800000-0xc38fffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.233604] pci 0000:00:1a.0: PME# supported from D0 D3hot
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.233779] pci 0000:00:1b.0: [8086:0f04] type 00 class 0x040300
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.233803] pci 0000:00:1b.0: reg 0x10: [mem 0xc3c10000-0xc3c13fff 64bit]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.233873] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.234044] pci 0000:00:1c.0: [8086:0f48] type 01 class 0x060400
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.234104] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.234274] pci 0000:00:1c.2: [8086:0f4c] type 01 class 0x060400
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.234333] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.234445] pci 0000:00:1c.2: System wakeup disabled by ACPI
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.234516] pci 0000:00:1c.3: [8086:0f4e] type 01 class 0x060400
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.234575] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.234682] pci 0000:00:1c.3: System wakeup disabled by ACPI
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.234759] pci 0000:00:1f.0: [8086:0f1c] type 00 class 0x060100
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.234995] pci 0000:00:1f.3: [8086:0f12] type 00 class 0x0c0500
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.235031] pci 0000:00:1f.3: reg 0x10: [mem 0xc3c14000-0xc3c1401f]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.235104] pci 0000:00:1f.3: reg 0x20: [io  0xf000-0xf01f]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.235459] pci 0000:01:00.0: [10de:1299] type 00 class 0x030200
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.235479] pci 0000:01:00.0: reg 0x10: [mem 0xc2000000-0xc2ffffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.235496] pci 0000:01:00.0: reg 0x14: [mem 0xb0000000-0xbfffffff 64bit pref]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.235513] pci 0000:01:00.0: reg 0x1c: [mem 0xc0000000-0xc1ffffff 64bit pref]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.235525] pci 0000:01:00.0: reg 0x24: [io  0xe000-0xe07f]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.235537] pci 0000:01:00.0: reg 0x30: [mem 0xc3000000-0xc307ffff pref]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.235727] pci 0000:01:00.0: System wakeup disabled by ACPI
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.243458] pci 0000:00:1c.0: PCI bridge to [bus 01]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.243482] pci 0000:00:1c.0:   bridge window [io  0xe000-0xefff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.243503] pci 0000:00:1c.0:   bridge window [mem 0xb0000000-0xc30fffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.243733] pci 0000:02:00.0: [10ec:5286] type 00 class 0xff0000
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.243759] pci 0000:02:00.0: reg 0x10: [mem 0xc3b00000-0xc3b0ffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.243888] pci 0000:02:00.0: supports D1 D2
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.243892] pci 0000:02:00.0: PME# supported from D1 D2 D3hot D3cold
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.243953] pci 0000:02:00.0: System wakeup disabled by ACPI
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.244034] pci 0000:02:00.2: [10ec:8136] type 00 class 0x020000
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.244056] pci 0000:02:00.2: reg 0x10: [io  0xd000-0xd0ff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.244086] pci 0000:02:00.2: reg 0x18: [mem 0xc3b14000-0xc3b14fff 64bit]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.244105] pci 0000:02:00.2: reg 0x20: [mem 0xc3b10000-0xc3b13fff 64bit pref]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.244178] pci 0000:02:00.2: supports D1 D2
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.244182] pci 0000:02:00.2: PME# supported from D0 D1 D2 D3hot D3cold
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.251483] pci 0000:00:1c.2: PCI bridge to [bus 02]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.251508] pci 0000:00:1c.2:   bridge window [io  0xd000-0xdfff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.251528] pci 0000:00:1c.2:   bridge window [mem 0xc3b00000-0xc3bfffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.251685] pci 0000:03:00.0: [168c:0036] type 00 class 0x028000
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.251713] pci 0000:03:00.0: reg 0x10: [mem 0xc3a00000-0xc3a7ffff 64bit]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.251766] pci 0000:03:00.0: reg 0x30: [mem 0xc3a80000-0xc3a8ffff pref]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.251829] pci 0000:03:00.0: supports D1 D2
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.251833] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.251890] pci 0000:03:00.0: System wakeup disabled by ACPI
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.259495] pci 0000:00:1c.3: PCI bridge to [bus 03]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.259524] pci 0000:00:1c.3:   bridge window [mem 0xc3a00000-0xc3afffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.260680] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11 12) *0, disabled.
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.260805] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 12) *0, disabled.
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.260924] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 12) *0, disabled.
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.261046] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 12) *0, disabled.
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.261163] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 12) *0, disabled.
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.261282] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 12) *0, disabled.
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.261400] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 12) *0, disabled.
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.261518] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 12) *0, disabled.
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.263374] ACPI: Enabled 4 GPEs in block 00 to 3F
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.263551] ACPI : EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.263807] vgaarb: setting as boot device: PCI:0000:00:02.0
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.263811] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.263818] vgaarb: loaded
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.263820] vgaarb: bridge control possible 0000:00:02.0
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.264455] SCSI subsystem initialized
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.264567] libata version 3.00 loaded.
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.264620] ACPI: bus type USB registered
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.264656] usbcore: registered new interface driver usbfs
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.264675] usbcore: registered new interface driver hub
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.264813] usbcore: registered new device driver usb
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.265426] PCI: Using ACPI for IRQ routing
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.271481] PCI: pci_cache_line_size set to 64 bytes
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.271537] e820: reserve RAM buffer [mem 0x0008f000-0x0008ffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.271541] e820: reserve RAM buffer [mem 0x0009e000-0x0009ffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.271543] e820: reserve RAM buffer [mem 0x8a612018-0x8bffffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.271546] e820: reserve RAM buffer [mem 0x8a62a018-0x8bffffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.271549] e820: reserve RAM buffer [mem 0x98cf2000-0x9bffffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.271552] e820: reserve RAM buffer [mem 0x98e60000-0x9bffffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.271555] e820: reserve RAM buffer [mem 0x99b90000-0x9bffffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.271558] e820: reserve RAM buffer [mem 0x99d48000-0x9bffffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.271561] e820: reserve RAM buffer [mem 0x9a000000-0x9bffffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.271766] NetLabel: Initializing
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.271769] NetLabel:  domain hash size = 128
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.271771] NetLabel:  protocols = UNLABELED CIPSOv4
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.271791] NetLabel:  unlabeled traffic allowed by default
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.272067] clocksource: Switched to clocksource refined-jiffies
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.283705] AppArmor: AppArmor Filesystem Enabled
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.283838] pnp: PnP ACPI init
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.283949] pnp 00:00: Plug and Play ACPI device, IDs PNP0b00 (active)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.284212] system 00:01: [io  0x0680-0x069f] has been reserved
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.284218] system 00:01: [io  0x0400-0x047f] has been reserved
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.284222] system 00:01: [io  0x0500-0x05fe] has been reserved
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.284226] system 00:01: [io  0x0600-0x061f] has been reserved
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.284233] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.284349] system 00:02: [io  0x03f8-0x0411] could not be reserved
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.284356] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.284492] pnp 00:03: Plug and Play ACPI device, IDs FLT0101 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.284581] pnp 00:04: Plug and Play ACPI device, IDs ATK3001 PNP030b (active)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.285039] system 00:05: [mem 0xe0000000-0xefffffff] could not be reserved
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.285044] system 00:05: [mem 0xfed01000-0xfed01fff] has been reserved
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.285049] system 00:05: [mem 0xfed03000-0xfed03fff] has been reserved
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.285053] system 00:05: [mem 0xfed04000-0xfed04fff] has been reserved
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.285057] system 00:05: [mem 0xfed0c000-0xfed0ffff] has been reserved
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.285061] system 00:05: [mem 0xfed08000-0xfed08fff] has been reserved
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.285065] system 00:05: [mem 0xfed1c000-0xfed1cfff] has been reserved
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.285069] system 00:05: [mem 0xfee00000-0xfeefffff] has been reserved
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.285074] system 00:05: [mem 0xfef00000-0xfeffffff] has been reserved
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.285080] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.286570] pnp: PnP ACPI: found 6 devices
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.299088] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.299126] clocksource: Switched to clocksource acpi_pm
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.299172] pci 0000:00:1c.0: PCI bridge to [bus 01]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.299178] pci 0000:00:1c.0:   bridge window [io  0xe000-0xefff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.299184] pci 0000:00:1c.0:   bridge window [mem 0xb0000000-0xc30fffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.299193] pci 0000:00:1c.2: PCI bridge to [bus 02]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.299198] pci 0000:00:1c.2:   bridge window [io  0xd000-0xdfff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.299203] pci 0000:00:1c.2:   bridge window [mem 0xc3b00000-0xc3bfffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.299212] pci 0000:00:1c.3: PCI bridge to [bus 03]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.299218] pci 0000:00:1c.3:   bridge window [mem 0xc3a00000-0xc3afffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.299232] pci_bus 0000:00: resource 4 [io  0x0070-0x0077]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.299236] pci_bus 0000:00: resource 5 [io  0x0000-0x006f window]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.299240] pci_bus 0000:00: resource 6 [io  0x0078-0x0cf7 window]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.299244] pci_bus 0000:00: resource 7 [io  0x0d00-0xffff window]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.299248] pci_bus 0000:00: resource 8 [mem 0x000a0000-0x000bffff window]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.299251] pci_bus 0000:00: resource 9 [mem 0x000c0000-0x000dffff window]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.299255] pci_bus 0000:00: resource 10 [mem 0x000e0000-0x000fffff window]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.299259] pci_bus 0000:00: resource 11 [mem 0xa0000000-0xc3c15ffe window]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.299263] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.299266] pci_bus 0000:01: resource 1 [mem 0xb0000000-0xc30fffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.299270] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.299273] pci_bus 0000:02: resource 1 [mem 0xc3b00000-0xc3bfffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.299283] pci_bus 0000:03: resource 1 [mem 0xc3a00000-0xc3afffff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.299343] NET: Registered protocol family 2
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.299675] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.299819] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.299963] TCP: Hash tables configured (established 32768 bind 32768)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.300026] UDP hash table entries: 2048 (order: 4, 65536 bytes)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.300065] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.300199] NET: Registered protocol family 1
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.300234] pci 0000:00:02.0: Video device with shadowed ROM
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.300560] PCI: CLS 64 bytes, default 64
Apr  2 14:39:58 gabriel-X550MJ kernel: [    0.300697] Trying to unpack rootfs image as initramfs...
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.113226] Freeing initrd memory: 32792K (ffff88003dff5000 - ffff88003fffb000)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.113245] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.113250] software IO TLB [mem 0x86612000-0x8a612000] (64MB) mapped at [ffff880086612000-ffff88008a611fff]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.113489] microcode: CPU0 sig=0x30678, pf=0x8, revision=0x815
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.113509] microcode: CPU1 sig=0x30678, pf=0x8, revision=0x815
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.113526] microcode: CPU2 sig=0x30678, pf=0x8, revision=0x815
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.113543] microcode: CPU3 sig=0x30678, pf=0x8, revision=0x815
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.113818] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.114110] Scanning for low memory corruption every 60 seconds
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.115059] futex hash table entries: 1024 (order: 4, 65536 bytes)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.115086] Initialise system trusted keyring
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.115127] audit: initializing netlink subsys (disabled)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.115162] audit: type=2000 audit(1459605021.103:1): initialized
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.116091] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.119141] zpool: loaded
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.119146] zbud: loaded
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.119686] VFS: Disk quotas dquot_6.6.0
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.119755] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.121034] fuse init (API version 7.23)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.121332] Key type big_key registered
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.123193] Key type asymmetric registered
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.123199] Asymmetric key parser 'x509' registered
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.123231] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.123381] io scheduler noop registered
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.123387] io scheduler deadline registered (default)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.123465] io scheduler cfq registered
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.124303] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.124318] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.124386] efifb: probing for efifb
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.124413] efifb: framebuffer at 0xa0000000, mapped to 0xffffc90000800000, using 1876k, total 1875k
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.124416] efifb: mode is 800x600x32, linelength=3200, pages=1
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.124418] efifb: scrolling: redraw
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.124422] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.124613] Console: switching to colour frame buffer device 100x37
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.124633] fb0: EFI VGA frame buffer device
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.124651] intel_idle: MWAIT substates: 0x33000020
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.124654] intel_idle: v0.4 model 0x37
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.124656] intel_idle: lapic_timer_reliable_states 0xffffffff
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.125124] ACPI: AC Adapter [AC0] (off-line)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.125248] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.125256] ACPI: Power Button [PWRB]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.125342] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.126341] ACPI: Lid Switch [LID]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.126419] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.126424] ACPI: Sleep Button [SLPB]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.126498] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.126503] ACPI: Power Button [PWRF]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.130843] thermal LNXTHERM:00: registered as thermal_zone0
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.130847] ACPI: Thermal Zone [THRM] (45 C)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.130908] GHES: HEST is not enabled!
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.131395] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.151625] serial8250: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.161574] hpet: number irqs doesn't agree with number of timers
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.161846] Linux agpgart interface v0.103
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.169659] ACPI: Battery Slot [BAT0] (battery present)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.173211] brd: module loaded
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.175829] loop: module loaded
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.176281] libphy: Fixed MDIO Bus: probed
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.176288] tun: Universal TUN/TAP device driver, 1.6
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.176290] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.176610] PPP generic driver version 2.4.2
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.177049] xhci_hcd 0000:00:14.0: xHCI Host Controller
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.177062] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.178157] xhci_hcd 0000:00:14.0: hcc params 0x200077c1 hci version 0x100 quirks 0x00009810
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.178165] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.178296] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.178301] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.178304] usb usb1: Product: xHCI Host Controller
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.178308] usb usb1: Manufacturer: Linux 4.2.0-34-generic xhci-hcd
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.178311] usb usb1: SerialNumber: 0000:00:14.0
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.178731] hub 1-0:1.0: USB hub found
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.178750] hub 1-0:1.0: 6 ports detected
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.180513] xhci_hcd 0000:00:14.0: xHCI Host Controller
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.180521] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.180593] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.180598] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.180601] usb usb2: Product: xHCI Host Controller
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.180605] usb usb2: Manufacturer: Linux 4.2.0-34-generic xhci-hcd
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.180608] usb usb2: SerialNumber: 0000:00:14.0
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.181046] hub 2-0:1.0: USB hub found
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.181062] hub 2-0:1.0: 1 port detected
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.181287] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.181298] ehci-pci: EHCI PCI platform driver
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.181326] ehci-platform: EHCI generic platform driver
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.181354] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.181362] ohci-pci: OHCI PCI platform driver
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.181383] ohci-platform: OHCI generic platform driver
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.181401] uhci_hcd: USB Universal Host Controller Interface driver
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.181516] i8042: PNP: PS/2 Controller [PNP030b:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.183761] i8042: Detected active multiplexing controller, rev 1.1
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.185289] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.185299] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.185363] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.185422] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.185481] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.186076] mousedev: PS/2 mouse device common for all mice
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.186890] rtc_cmos 00:00: RTC can wake from S4
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.187079] rtc_cmos 00:00: rtc core: registered rtc_cmos as rtc0
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.187107] rtc_cmos 00:00: alarms up to one month, y3k, 242 bytes nvram
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.187125] i2c /dev entries driver
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.187277] device-mapper: uevent: version 1.0.3
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.187986] device-mapper: ioctl: 4.33.0-ioctl (2015-8-18) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.188012] Intel P-state driver initializing.
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.188659] ledtrig-cpu: registered to indicate activity on CPUs
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.188686] EFI Variables Facility v0.08 2004-May-17
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.190341] efivars: duplicate variable: AcpiGlobalVariable-c020489e-6db2-4ef2-9aa5-ca06fc11d36a
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.194702] PCCT header not found.
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.196427] NET: Registered protocol family 10
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.197052] NET: Registered protocol family 17
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.197075] Key type dns_resolver registered
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.197946] Loading compiled-in X.509 certificates
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.199353] Loaded X.509 cert 'Build time autogenerated kernel key: 544e45c0bde6f784077abca3de58e48fb525ee14'
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.199374] registered taskstats version 1
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.199399] zswap: loading zswap
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.199403] zswap: using zbud pool
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.199411] zswap: using lzo compressor
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.207236] Key type trusted registered
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.221476] Key type encrypted registered
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.221490] AppArmor: AppArmor sha1 policy hashing enabled
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.221495] ima: No TPM chip found, activating TPM-bypass!
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.221532] evm: HMAC attrs: 0x1
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.223039]   Magic number: 12:302:836
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.223440] rtc_cmos 00:00: setting system clock to 2016-04-02 13:50:22 UTC (1459605022)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.223926] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.223929] EDD information not available.
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.224067] PM: Hibernation image not present or could not be loaded.
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.225388] Freeing unused kernel memory: 1464K (ffffffff81d37000 - ffffffff81ea5000)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.225393] Write protecting the kernel read-only data: 12288k
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.226552] Freeing unused kernel memory: 20K (ffff8800017fb000 - ffff880001800000)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.226934] Freeing unused kernel memory: 292K (ffff880001bb7000 - ffff880001c00000)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.227051] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.267369] random: systemd-udevd urandom read with 11 bits of entropy available
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.333749] sdhci: Secure Digital Host Controller Interface driver
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.333755] sdhci: Copyright(c) Pierre Ossman
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.341223] hidraw: raw HID events driver (C) Jiri Kosina
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.352187] wmi: Mapper loaded
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.375109] ahci 0000:00:13.0: version 3.0
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.378249] rtsx_pci 0000:02:00.0: rtsx_pci_acquire_irq: pcr->msi_en = 1, pci->irq = 89
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.380338] [drm] Initialized drm 1.1.0 20060810
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.385726] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.385741] r8169 0000:02:00.2: can't disable ASPM; OS doesn't have ASPM control
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.387261] r8169 0000:02:00.2 eth0: RTL8402 at 0xffffc90000798000, f8:32:e4:fb:c6:06, XID 04000800 IRQ 90
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.388195] ahci 0000:00:13.0: AHCI 0001.0300 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.388201] ahci 0000:00:13.0: flags: 64bit ncq pm led clo pio slum part deso sadm apst 
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.389365] scsi host0: ahci
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.389659] scsi host1: ahci
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.389740] ata1: SATA max UDMA/133 abar m2048@0xc3c15000 port 0xc3c15100 irq 88
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.389744] ata2: SATA max UDMA/133 abar m2048@0xc3c15000 port 0xc3c15180 irq 88
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.417513] [drm] Memory usable by graphics device = 2048M
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.417520] checking generic (a0000000 1d5000) vs hw (a0000000 10000000)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.417523] fb: switching to inteldrmfb from EFI VGA
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.417567] Console: switching to colour dummy device 80x25
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.417718] [drm] Replacing VGA console driver
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.419673] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.419679] [drm] Driver supports precise vblank timestamp query.
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.423671] MXM: GUID detected in BIOS
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.423798] ACPI Warning: \_SB_.PCI0.RP01.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.423903] ACPI Warning: \_SB_.PCI0.RP01.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.424293] pci 0000:01:00.0: optimus capabilities: enabled, status dynamic power, 
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.424300] VGA switcheroo: detected Optimus DSM method \_SB_.PCI0.RP01.PEGP handle
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.466874] r8169 0000:02:00.2 enp2s0f2: renamed from eth0
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.466996] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.492127] usb 1-3: new full-speed USB device number 2 using xhci_hcd
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.522828] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.524525] input: FocalTechPS/2 FocalTech FocalTech Touchpad as /devices/platform/i8042/serio4/input/input12
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.528827] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input13
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.529360] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.530549] ACPI: Video Device [PEGP] (multi-head: yes  rom: yes  post: no)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.530562] ACPI Error: [\_SB_.PCI0.GFX0.DD02._BCL] Namespace lookup failure, AE_NOT_FOUND (20150619/psargs-359)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.530570] ACPI Error: Method parse/execution failed [\_SB_.PCI0.RP01.PEGP.DD02._BCL] (Node ffff88015b0e7960), AE_NOT_FOUND (20150619/psparse-536)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.531097] fbcon: inteldrmfb (fb0) is primary device
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.531191] Console: switching to colour frame buffer device 170x48
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.531224] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.531226] i915 0000:00:02.0: registered panic notifier
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.535905] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:44/LNXVIDEO:01/input/input14
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.536205] [drm] Initialized i915 1.6.0 20150522 for 0000:00:02.0 on minor 0
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.536678] nouveau  [  DEVICE][0000:01:00.0] BOOT0  : 0xb06190b1
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.536682] nouveau  [  DEVICE][0000:01:00.0] Chipset: GK208B (NV106)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.536685] nouveau  [  DEVICE][0000:01:00.0] Family : NVE0
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.570925] nouveau  [   VBIOS][0000:01:00.0] using image from ACPI
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.571155] nouveau  [   VBIOS][0000:01:00.0] BIT signature found
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.571160] nouveau  [   VBIOS][0000:01:00.0] version 80.28.88.00.10
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.577353] nouveau  [   VBIOS][0000:01:00.0] running init tables
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.621724] usb 1-3: New USB device found, idVendor=13d3, idProduct=3408
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.621729] usb 1-3: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.639986] nouveau  [     PMC][0000:01:00.0] MSI interrupts enabled
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.640039] nouveau E[   PIBUS][0000:01:00.0] HUB0: 0x6013d4 0x00005700 (0x1e708200)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.640098] nouveau  [     PFB][0000:01:00.0] RAM type: DDR3
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.640101] nouveau  [     PFB][0000:01:00.0] RAM size: 1024 MiB
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.640103] nouveau  [     PFB][0000:01:00.0]    ZCOMP: 0 tags
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.640167] nouveau E[   PIBUS][0000:01:00.0] HUB0: 0x10ecc0 0xffffffff (0x1f70822c)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.642841] nouveau  [    VOLT][0000:01:00.0] GPU voltage: 600000uv
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.716869] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.720866] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.723336] ata2.00: ATAPI: HL-DT-ST DVDRAM GUC0N, AS01, max UDMA/133
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.723391] ata1.00: ATA-8: ST1000LM024 HN-M101MBB, 2BA30001, max UDMA/133
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.723396] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.728254] ata2.00: configured for UDMA/133
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.729991] ata1.00: configured for UDMA/133
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.730409] scsi 0:0:0:0: Direct-Access     ATA      ST1000LM024 HN-M 0001 PQ: 0 ANSI: 5
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.731088] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.731093] sd 0:0:0:0: [sda] 4096-byte physical blocks
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.731140] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.731291] sd 0:0:0:0: [sda] Write Protect is off
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.731297] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.731369] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.735907] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GUC0N     AS01 PQ: 0 ANSI: 5
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.762573] sr 1:0:0:0: [sr0] scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.762580] cdrom: Uniform CD-ROM driver Revision: 3.20
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.763061] sr 1:0:0:0: Attached scsi CD-ROM sr0
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.763196] sr 1:0:0:0: Attached scsi generic sg1 type 5
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.788494] usb 1-4: new high-speed USB device number 3 using xhci_hcd
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.807266]  sda: sda1 sda2 sda3 sda4 sda5 sda6
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.809757] sd 0:0:0:0: [sda] Attached SCSI disk
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.967768] usb 1-4: New USB device found, idVendor=04f2, idProduct=b48c
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.967774] usb 1-4: New USB device strings: Mfr=0, Product=1, SerialNumber=0
Apr  2 14:39:58 gabriel-X550MJ kernel: [    1.967777] usb 1-4: Product: USB2.0 VGA UVC WebCam
Apr  2 14:39:58 gabriel-X550MJ kernel: [    2.124665] tsc: Refined TSC clocksource calibration: 2166.666 MHz
Apr  2 14:39:58 gabriel-X550MJ kernel: [    2.124672] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x1f3b3172f25, max_idle_ns: 440795274731 ns
Apr  2 14:39:58 gabriel-X550MJ kernel: [    2.941307] nouveau  [  PTHERM][0000:01:00.0] FAN control: none / external
Apr  2 14:39:58 gabriel-X550MJ kernel: [    2.941330] nouveau  [  PTHERM][0000:01:00.0] fan management: automatic
Apr  2 14:39:58 gabriel-X550MJ kernel: [    2.941352] nouveau  [  PTHERM][0000:01:00.0] internal sensor: yes
Apr  2 14:39:58 gabriel-X550MJ kernel: [    2.941415] nouveau  [     CLK][0000:01:00.0] 07: core 405 MHz memory 648 MHz 
Apr  2 14:39:58 gabriel-X550MJ kernel: [    2.941575] nouveau  [     CLK][0000:01:00.0] 0a: core 405-954 MHz memory 1620 MHz 
Apr  2 14:39:58 gabriel-X550MJ kernel: [    2.941776] nouveau  [     CLK][0000:01:00.0] 0f: core 405-954 MHz memory 1800 MHz 
Apr  2 14:39:58 gabriel-X550MJ kernel: [    2.941862] nouveau  [     CLK][0000:01:00.0] --: core 405 MHz memory 648 MHz 
Apr  2 14:39:58 gabriel-X550MJ kernel: [    3.014388] vga_switcheroo: enabled
Apr  2 14:39:58 gabriel-X550MJ kernel: [    3.015813] [TTM] Zone  kernel: Available graphics memory: 1965324 kiB
Apr  2 14:39:58 gabriel-X550MJ kernel: [    3.015835] [TTM] Initializing pool allocator
Apr  2 14:39:58 gabriel-X550MJ kernel: [    3.015846] [TTM] Initializing DMA pool allocator
Apr  2 14:39:58 gabriel-X550MJ kernel: [    3.015870] nouveau  [     DRM] VRAM: 1024 MiB
Apr  2 14:39:58 gabriel-X550MJ kernel: [    3.015874] nouveau  [     DRM] GART: 1048576 MiB
Apr  2 14:39:58 gabriel-X550MJ kernel: [    3.015880] nouveau W[     DRM] Pointer to TMDS table invalid
Apr  2 14:39:58 gabriel-X550MJ kernel: [    3.015883] nouveau  [     DRM] DCB version 4.0
Apr  2 14:39:58 gabriel-X550MJ kernel: [    3.015888] nouveau W[     DRM] Pointer to flat panel table invalid
Apr  2 14:39:58 gabriel-X550MJ kernel: [    3.025845] nouveau  [     DRM] MM: using COPY for buffer copies
Apr  2 14:39:58 gabriel-X550MJ kernel: [    3.025858] [drm] Initialized nouveau 1.2.2 20120801 for 0000:01:00.0 on minor 1
Apr  2 14:39:58 gabriel-X550MJ kernel: [    3.126285] clocksource: Switched to clocksource tsc
Apr  2 14:39:58 gabriel-X550MJ kernel: [    4.370550] random: nonblocking pool is initialized
Apr  2 14:39:58 gabriel-X550MJ kernel: [    8.029442] ACPI Warning: \_SB_.PCI0.RP01.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
Apr  2 14:39:58 gabriel-X550MJ kernel: [    8.029701] ACPI: \_SB_.PCI0.RP01.PEGP: failed to evaluate _DSM
Apr  2 14:39:58 gabriel-X550MJ kernel: [    8.029709] ACPI Warning: \_SB_.PCI0.RP01.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
Apr  2 14:39:58 gabriel-X550MJ kernel: [   13.809306] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
Apr  2 14:39:58 gabriel-X550MJ kernel: [   14.798097] efivars: duplicate variable: AcpiGlobalVariable-c020489e-6db2-4ef2-9aa5-ca06fc11d36a
Apr  2 14:39:58 gabriel-X550MJ kernel: [   17.077218] lp: driver loaded but no devices found
Apr  2 14:39:58 gabriel-X550MJ kernel: [   17.120203] ppdev: user-space parallel port driver
Apr  2 14:39:58 gabriel-X550MJ kernel: [   19.330918] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
Apr  2 14:39:58 gabriel-X550MJ kernel: [   19.637423] mei_txe 0000:00:1a.0: can't derive routing for PCI INT A
Apr  2 14:39:58 gabriel-X550MJ kernel: [   19.637428] mei_txe 0000:00:1a.0: PCI INT A: no GSI
Apr  2 14:39:58 gabriel-X550MJ kernel: [   19.756472] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr  2 14:39:58 gabriel-X550MJ kernel: [   20.140187] Bluetooth: Core ver 2.20
Apr  2 14:39:58 gabriel-X550MJ kernel: [   20.140214] NET: Registered protocol family 31
Apr  2 14:39:58 gabriel-X550MJ kernel: [   20.140217] Bluetooth: HCI device and connection manager initialized
Apr  2 14:39:58 gabriel-X550MJ kernel: [   20.140224] Bluetooth: HCI socket layer initialized
Apr  2 14:39:58 gabriel-X550MJ kernel: [   20.140228] Bluetooth: L2CAP socket layer initialized
Apr  2 14:39:58 gabriel-X550MJ kernel: [   20.140238] Bluetooth: SCO socket layer initialized
Apr  2 14:39:58 gabriel-X550MJ kernel: [   20.238778] snd_hda_intel 0000:00:1b.0: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
Apr  2 14:39:58 gabriel-X550MJ kernel: [   20.400878] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC270: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
Apr  2 14:39:58 gabriel-X550MJ kernel: [   20.400885] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
Apr  2 14:39:58 gabriel-X550MJ kernel: [   20.400888] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
Apr  2 14:39:58 gabriel-X550MJ kernel: [   20.400891] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
Apr  2 14:39:58 gabriel-X550MJ kernel: [   20.400894] snd_hda_codec_realtek hdaudioC0D0:    inputs:
Apr  2 14:39:58 gabriel-X550MJ kernel: [   20.400897] snd_hda_codec_realtek hdaudioC0D0:      Mic=0x19
Apr  2 14:39:58 gabriel-X550MJ kernel: [   20.474802] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
Apr  2 14:39:58 gabriel-X550MJ kernel: [   20.474913] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
Apr  2 14:39:58 gabriel-X550MJ kernel: [   20.672798] usbcore: registered new interface driver btusb
Apr  2 14:39:58 gabriel-X550MJ kernel: [   21.038386] asus_wmi: ASUS WMI generic driver loaded
Apr  2 14:39:58 gabriel-X550MJ kernel: [   21.044671] asus_wmi: Initialization: 0x1
Apr  2 14:39:58 gabriel-X550MJ kernel: [   21.044736] asus_wmi: BIOS WMI version: 7.9
Apr  2 14:39:58 gabriel-X550MJ kernel: [   21.044811] asus_wmi: SFUN value: 0x4a0877
Apr  2 14:39:58 gabriel-X550MJ kernel: [   21.046430] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input17
Apr  2 14:39:58 gabriel-X550MJ kernel: [   21.047017] usb 1-3: USB disconnect, device number 2
Apr  2 14:39:58 gabriel-X550MJ kernel: [   21.047526] usbcore: registered new interface driver ath3k
Apr  2 14:39:58 gabriel-X550MJ kernel: [   21.050109] asus_wmi: Number of fans: 1
Apr  2 14:39:58 gabriel-X550MJ kernel: [   21.074117] ath: phy0: WB335 2-ANT card detected
Apr  2 14:39:58 gabriel-X550MJ kernel: [   21.074122] ath: phy0: Set BT/WLAN RX diversity capability
Apr  2 14:39:58 gabriel-X550MJ kernel: [   21.080563] ath: phy0: Enable LNA combining
Apr  2 14:39:58 gabriel-X550MJ kernel: [   21.081663] ath: phy0: ASPM enabled: 0x42
Apr  2 14:39:58 gabriel-X550MJ kernel: [   21.081666] ath: EEPROM regdomain: 0x6a
Apr  2 14:39:58 gabriel-X550MJ kernel: [   21.081668] ath: EEPROM indicates we should expect a direct regpair map
Apr  2 14:39:58 gabriel-X550MJ kernel: [   21.081671] ath: Country alpha2 being used: 00
Apr  2 14:39:58 gabriel-X550MJ kernel: [   21.081673] ath: Regpair used: 0x6a
Apr  2 14:39:58 gabriel-X550MJ kernel: [   21.235399] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
Apr  2 14:39:58 gabriel-X550MJ kernel: [   21.235948] ieee80211 phy0: Atheros AR9565 Rev:1 mem=0xffffc90001700000, irq=19
Apr  2 14:39:58 gabriel-X550MJ kernel: [   21.358383] media: Linux media interface: v0.10
Apr  2 14:39:58 gabriel-X550MJ kernel: [   21.374238] ath9k 0000:03:00.0 wlp3s0: renamed from wlan0
Apr  2 14:39:58 gabriel-X550MJ kernel: [   21.546149] Linux video capture interface: v2.00
Apr  2 14:39:58 gabriel-X550MJ kernel: [   21.891746] intel_soc_dts_thermal: request_threaded_irq ret -22
Apr  2 14:39:58 gabriel-X550MJ kernel: [   21.914126] intel_soc_dts_thermal: request_threaded_irq ret -22
Apr  2 14:39:58 gabriel-X550MJ kernel: [   21.941670] intel_soc_dts_thermal: request_threaded_irq ret -22
Apr  2 14:39:58 gabriel-X550MJ kernel: [   22.168759] intel_rapl: Found RAPL domain package
Apr  2 14:39:58 gabriel-X550MJ kernel: [   22.168764] intel_rapl: Found RAPL domain core
Apr  2 14:39:58 gabriel-X550MJ kernel: [   22.367012] uvcvideo: Found UVC 1.00 device USB2.0 VGA UVC WebCam (04f2:b48c)
Apr  2 14:39:58 gabriel-X550MJ kernel: [   22.410030] input: USB2.0 VGA UVC WebCam as /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.0/input/input18
Apr  2 14:39:58 gabriel-X550MJ kernel: [   22.410150] usbcore: registered new interface driver uvcvideo
Apr  2 14:39:58 gabriel-X550MJ kernel: [   22.410152] USB Video Class driver (1.1.1)
Apr  2 14:39:58 gabriel-X550MJ kernel: [   22.906095] cfg80211: World regulatory domain updated:
Apr  2 14:39:58 gabriel-X550MJ kernel: [   22.906102] cfg80211:  DFS Master region: unset
Apr  2 14:39:58 gabriel-X550MJ kernel: [   22.906104] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Apr  2 14:39:58 gabriel-X550MJ kernel: [   22.906108] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Apr  2 14:39:58 gabriel-X550MJ kernel: [   22.906111] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Apr  2 14:39:58 gabriel-X550MJ kernel: [   22.906113] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
Apr  2 14:39:58 gabriel-X550MJ kernel: [   22.906116] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
Apr  2 14:39:58 gabriel-X550MJ kernel: [   22.906119] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
Apr  2 14:39:58 gabriel-X550MJ kernel: [   22.906122] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
Apr  2 14:39:58 gabriel-X550MJ kernel: [   22.906125] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
Apr  2 14:39:58 gabriel-X550MJ kernel: [   22.906127] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
Apr  2 14:39:58 gabriel-X550MJ kernel: [   24.838174] Adding 4077564k swap on /dev/sda6.  Priority:-1 extents:1 across:4077564k FS
Apr  2 14:39:58 gabriel-X550MJ kernel: [   31.157577] audit: type=1400 audit(1459604393.575:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=535 comm="apparmor_parser"
Apr  2 14:39:58 gabriel-X550MJ kernel: [   31.157591] audit: type=1400 audit(1459604393.575:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=535 comm="apparmor_parser"
Apr  2 14:39:58 gabriel-X550MJ kernel: [   31.358387] audit: type=1400 audit(1459604393.775:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=535 comm="apparmor_parser"
Apr  2 14:39:58 gabriel-X550MJ kernel: [   31.358404] audit: type=1400 audit(1459604393.775:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=535 comm="apparmor_parser"
Apr  2 14:39:58 gabriel-X550MJ kernel: [   31.358416] audit: type=1400 audit(1459604393.775:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=535 comm="apparmor_parser"
Apr  2 14:39:58 gabriel-X550MJ kernel: [   31.358427] audit: type=1400 audit(1459604393.775:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=535 comm="apparmor_parser"
Apr  2 14:39:58 gabriel-X550MJ kernel: [   31.716597] audit: type=1400 audit(1459604394.131:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=535 comm="apparmor_parser"
Apr  2 14:39:58 gabriel-X550MJ kernel: [   31.716614] audit: type=1400 audit(1459604394.131:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=535 comm="apparmor_parser"
Apr  2 14:39:58 gabriel-X550MJ kernel: [   31.716624] audit: type=1400 audit(1459604394.131:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=535 comm="apparmor_parser"
Apr  2 14:39:58 gabriel-X550MJ kernel: [   31.716633] audit: type=1400 audit(1459604394.131:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=535 comm="apparmor_parser"
Apr  2 14:39:58 gabriel-X550MJ kernel: [   32.979261] nouveau E[   PIBUS][0000:01:00.0] HUB0: 0x10ecc0 0xffffffff (0x1970822c)
Apr  2 14:39:58 gabriel-X550MJ kernel: [   35.986647] cgroup: new mount options do not match the existing superblock, will be ignored
Apr  2 14:40:00 gabriel-X550MJ kernel: [   38.046147] ACPI Warning: \_SB_.PCI0.RP01.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
Apr  2 14:40:00 gabriel-X550MJ kernel: [   38.046447] ACPI: \_SB_.PCI0.RP01.PEGP: failed to evaluate _DSM
Apr  2 14:40:00 gabriel-X550MJ kernel: [   38.046456] ACPI Warning: \_SB_.PCI0.RP01.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
Apr  2 14:40:01 gabriel-X550MJ kernel: [   38.814591] IPv6: ADDRCONF(NETDEV_UP): enp2s0f2: link is not ready
Apr  2 14:40:01 gabriel-X550MJ kernel: [   38.949122] r8169 0000:02:00.2 enp2s0f2: link down
Apr  2 14:40:01 gabriel-X550MJ kernel: [   38.949180] IPv6: ADDRCONF(NETDEV_UP): enp2s0f2: link is not ready
Apr  2 14:40:01 gabriel-X550MJ kernel: [   38.954080] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
Apr  2 14:40:01 gabriel-X550MJ kernel: [   38.965958] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
Apr  2 14:40:01 gabriel-X550MJ kernel: [   39.132107] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
Apr  2 14:40:02 gabriel-X550MJ kernel: [   39.691432] nouveau E[   PIBUS][0000:01:00.0] HUB0: 0x10ecc0 0xffffffff (0x1970822c)
Apr  2 14:40:02 gabriel-X550MJ kernel: [   40.003682] wlp3s0: authenticate with 78:8d:f7:05:8a:18
Apr  2 14:40:02 gabriel-X550MJ kernel: [   40.015481] wlp3s0: send auth to 78:8d:f7:05:8a:18 (try 1/3)
Apr  2 14:40:02 gabriel-X550MJ kernel: [   40.017702] wlp3s0: authenticated
Apr  2 14:40:02 gabriel-X550MJ kernel: [   40.019701] wlp3s0: associate with 78:8d:f7:05:8a:18 (try 1/3)
Apr  2 14:40:02 gabriel-X550MJ kernel: [   40.035652] wlp3s0: RX AssocResp from 78:8d:f7:05:8a:18 (capab=0xc31 status=0 aid=12)
Apr  2 14:40:02 gabriel-X550MJ kernel: [   40.035751] wlp3s0: associated
Apr  2 14:40:02 gabriel-X550MJ kernel: [   40.035799] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
Apr  2 14:40:06 gabriel-X550MJ kernel: [   44.197464] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Apr  2 14:40:06 gabriel-X550MJ kernel: [   44.197470] Bluetooth: BNEP filters: protocol multicast
Apr  2 14:40:06 gabriel-X550MJ kernel: [   44.197477] Bluetooth: BNEP socket layer initialized
Apr  2 14:40:08 gabriel-X550MJ kernel: [   45.848436] ACPI Warning: \_SB_.PCI0.RP01.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
Apr  2 14:40:08 gabriel-X550MJ kernel: [   45.848687] ACPI: \_SB_.PCI0.RP01.PEGP: failed to evaluate _DSM
Apr  2 14:40:08 gabriel-X550MJ kernel: [   45.848695] ACPI Warning: \_SB_.PCI0.RP01.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
Apr  2 14:40:15 gabriel-X550MJ gnome-session[1412]: Entering running state


After this, I turned off the bluetooth driver with blacklist.conf. Testing..

---

### Post by gabriel69 on 2016-04-02
Not works. 
I changed the keyboard input method to none ( Remove iBus ) and now seems perfect!! No crashes. kern.log only have one entry after the normal system start up.

> 
Apr  2 22:41:48 gabriel-X550MJ kernel: [ 6270.958067] perf interrupt  took too long (6309 > 5000), lowering  kernel.perf_event_max_sample_rate to 25000.


I searched about this entry and seems secure.

Let's see if I found really the problem.

EDIT:
Not works, I gave up, go back to the windows, unfortunately :/

---

### Post by gabriel69 on 2016-04-14
I tried again because windows 10 is very slow and I love Ubuntu. I googled about similar problems and I am testing a solution that seems to be working.

[B]PROBLEM:
[/B]CPU Performance States - Freezes randomly ( idle related ) - kernel bug in intel driver ( **[https://git.kernel.org/cgit/linux/kernel/git/stable/linux-stable.git/tree/drivers/acpi/processor_idle.c?id=v4.1.21](https://git.kernel.org/cgit/linux/kernel/git/stable/linux-stable.git/tree/drivers/acpi/processor_idle.c?id=v4.1.21)** processor_idle.c )

**SOLUTION ( workaround ):**
[B][https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1511019/comments/8](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1511019/comments/8)

[/B][COLOR=#333333][FONT=Ubuntu][TABLE]
[TR]
[TD][Stasia (scani)]("https://launchpad.net/~scani") wrote on 2016-02-06:[/TD]
[TD="class: bug-comment-index"][#8]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1511019/comments/8")[/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]> 
[COLOR=#333333][FONT=Ubuntu][FONT=monospace]There is a workaround that worked for me:
You should use the kernel parameter: "intel_idle.max_cstate=1"
do these steps:
1. sudo nano /etc/default/grub
2. There is a line in that: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" (like this), replace with: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_idle.max_cstate=1"
Save it (CTRL+O)
3. sudo update-grub
4. sudo reboot
Your CPU will be a little warmer.[/FONT][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][FONT=monospace]
[/FONT][/FONT][/COLOR]
More references:
**[https://bugs.freedesktop.org/show_bug.cgi?id=93214](https://bugs.freedesktop.org/show_bug.cgi?id=93214)**

> 
[COLOR=#000000][FONT=Verdana]Dave Hindle 2016-02-05 14:52:06 UTC[/FONT][/COLOR]
Thanks everyone - save me my sanity - max_cstate=1 solved it. Lets hope the kernel fix comes around soon.


I leave here the solution to help someone in the same situation.

---

