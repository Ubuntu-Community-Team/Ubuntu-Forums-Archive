---
title: "ATI Hybrid graphics (Radeon HD 7730M) - Very slow boot in powersaving mode"
date: 2014-01-27
forum: General Help
---

### Post by M@dinko12 on 2014-01-27
Hi !

I'm facing an issue with FGLRX drivers on my Dell Inspiron 7520. In Power Saving Mode (Intel Chip), after installing fglrx or fglrx-updates and fglrx-pxpress, boot is really slow (~3 minutes I guess). The issue does not occur using discrete GPU (~30 seconds).

Manual installation of FGLRX doesn't help and I had the same issue with 13.04 and 12.10.

Here is the result of lscpi command :

```
~$ lspci|grep VGA
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Chelsea LP [Radeon HD 7730M] (rev ff)
```

And here dmesg :

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.11.0-15-generic (buildd@batsu) (gcc version 4.8.1 (Ubuntu/Linaro 4.8.1-10ubuntu8) ) #23-Ubuntu SMP Mon Dec 9 18:17:04 UTC 2013 (Ubuntu 3.11.0-15.23-generic 3.11.10)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-15-generic.efi.signed root=UUID=de8aa5d2-2d79-42c4-af04-2f817a2e2f06 ro quiet splash acpi_osi=Linux acpi_backlight=vendor vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x0000000000087fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000088000-0x00000000000bffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000020200000-0x0000000040003fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000040004000-0x0000000040004fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000040005000-0x000000008ffaffff] usable
[    0.000000] BIOS-e820: [mem 0x000000008ffb0000-0x00000000913affff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000913b0000-0x0000000099dbefff] usable
[    0.000000] BIOS-e820: [mem 0x0000000099dbf000-0x000000009aebefff] reserved
[    0.000000] BIOS-e820: [mem 0x000000009aebf000-0x000000009afbefff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000009afbf000-0x000000009affefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000009afff000-0x000000009affffff] usable
[    0.000000] BIOS-e820: [mem 0x000000009b000000-0x000000009f9fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000feb00000-0x00000000feb03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffb80000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000025f5fffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] efi: EFI v2.31 by INSYDE Corp.
[    0.000000] efi:  ACPI=0x9affe000  ACPI 2.0=0x9affe014  SMBIOS=0x9aebef98 
[    0.000000] efi: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000001000) (0MB)
[    0.000000] efi: mem01: type=7, attr=0xf, range=[0x0000000000001000-0x000000000006f000) (0MB)
[    0.000000] efi: mem02: type=4, attr=0xf, range=[0x000000000006f000-0x0000000000070000) (0MB)
[    0.000000] efi: mem03: type=7, attr=0xf, range=[0x0000000000070000-0x0000000000088000) (0MB)
[    0.000000] efi: mem04: type=6, attr=0x800000000000000f, range=[0x0000000000088000-0x00000000000a0000) (0MB)
[    0.000000] efi: mem05: type=2, attr=0xf, range=[0x0000000000100000-0x00000000014f3000) (19MB)
[    0.000000] efi: mem06: type=7, attr=0xf, range=[0x00000000014f3000-0x0000000002000000) (11MB)
[    0.000000] efi: mem07: type=2, attr=0xf, range=[0x0000000002000000-0x00000000033f3000) (19MB)
[    0.000000] efi: mem08: type=7, attr=0xf, range=[0x00000000033f3000-0x0000000020000000) (460MB)
[    0.000000] efi: mem09: type=0, attr=0xf, range=[0x0000000020000000-0x0000000020200000) (2MB)
[    0.000000] efi: mem10: type=7, attr=0xf, range=[0x0000000020200000-0x0000000035eb2000) (348MB)
[    0.000000] efi: mem11: type=2, attr=0xf, range=[0x0000000035eb2000-0x0000000036f51000) (16MB)
[    0.000000] efi: mem12: type=7, attr=0xf, range=[0x0000000036f51000-0x0000000040004000) (144MB)
[    0.000000] efi: mem13: type=0, attr=0xf, range=[0x0000000040004000-0x0000000040005000) (0MB)
[    0.000000] efi: mem14: type=7, attr=0xf, range=[0x0000000040005000-0x000000006939d000) (659MB)
[    0.000000] efi: mem15: type=2, attr=0xf, range=[0x000000006939d000-0x000000008e3c0000) (592MB)
[    0.000000] efi: mem16: type=4, attr=0xf, range=[0x000000008e3c0000-0x000000008e3e0000) (0MB)
[    0.000000] efi: mem17: type=7, attr=0xf, range=[0x000000008e3e0000-0x000000008efcc000) (11MB)
[    0.000000] efi: mem18: type=4, attr=0xf, range=[0x000000008efcc000-0x000000008ffb0000) (15MB)
[    0.000000] efi: mem19: type=0, attr=0xf, range=[0x000000008ffb0000-0x00000000913b0000) (20MB)
[    0.000000] efi: mem20: type=7, attr=0xf, range=[0x00000000913b0000-0x00000000915a1000) (1MB)
[    0.000000] efi: mem21: type=1, attr=0xf, range=[0x00000000915a1000-0x00000000915bf000) (0MB)
[    0.000000] efi: mem22: type=7, attr=0xf, range=[0x00000000915bf000-0x000000009638e000) (77MB)
[    0.000000] efi: mem23: type=4, attr=0xf, range=[0x000000009638e000-0x00000000963e6000) (0MB)
[    0.000000] efi: mem24: type=7, attr=0xf, range=[0x00000000963e6000-0x00000000963fa000) (0MB)
[    0.000000] efi: mem25: type=4, attr=0xf, range=[0x00000000963fa000-0x00000000972ee000) (14MB)
[    0.000000] efi: mem26: type=7, attr=0xf, range=[0x00000000972ee000-0x00000000972f4000) (0MB)
[    0.000000] efi: mem27: type=4, attr=0xf, range=[0x00000000972f4000-0x0000000097428000) (1MB)
[    0.000000] efi: mem28: type=7, attr=0xf, range=[0x0000000097428000-0x0000000097429000) (0MB)
[    0.000000] efi: mem29: type=4, attr=0xf, range=[0x0000000097429000-0x000000009742b000) (0MB)
[    0.000000] efi: mem30: type=7, attr=0xf, range=[0x000000009742b000-0x000000009742c000) (0MB)
[    0.000000] efi: mem31: type=4, attr=0xf, range=[0x000000009742c000-0x0000000097467000) (0MB)
[    0.000000] efi: mem32: type=7, attr=0xf, range=[0x0000000097467000-0x000000009746c000) (0MB)
[    0.000000] efi: mem33: type=4, attr=0xf, range=[0x000000009746c000-0x0000000097661000) (1MB)
[    0.000000] efi: mem34: type=7, attr=0xf, range=[0x0000000097661000-0x0000000097662000) (0MB)
[    0.000000] efi: mem35: type=4, attr=0xf, range=[0x0000000097662000-0x00000000978c3000) (2MB)
[    0.000000] efi: mem36: type=7, attr=0xf, range=[0x00000000978c3000-0x00000000978c6000) (0MB)
[    0.000000] efi: mem37: type=4, attr=0xf, range=[0x00000000978c6000-0x0000000097dca000) (5MB)
[    0.000000] efi: mem38: type=7, attr=0xf, range=[0x0000000097dca000-0x0000000097dd2000) (0MB)
[    0.000000] efi: mem39: type=4, attr=0xf, range=[0x0000000097dd2000-0x0000000097dd3000) (0MB)
[    0.000000] efi: mem40: type=7, attr=0xf, range=[0x0000000097dd3000-0x0000000097dd4000) (0MB)
[    0.000000] efi: mem41: type=4, attr=0xf, range=[0x0000000097dd4000-0x00000000995bf000) (23MB)
[    0.000000] efi: mem42: type=7, attr=0xf, range=[0x00000000995bf000-0x00000000999b1000) (3MB)
[    0.000000] efi: mem43: type=2, attr=0xf, range=[0x00000000999b1000-0x00000000999bb000) (0MB)
[    0.000000] efi: mem44: type=3, attr=0xf, range=[0x00000000999bb000-0x0000000099dbf000) (4MB)
[    0.000000] efi: mem45: type=5, attr=0x800000000000000f, range=[0x0000000099dbf000-0x0000000099f2e000) (1MB)
[    0.000000] efi: mem46: type=5, attr=0x800000000000000f, range=[0x0000000099f2e000-0x0000000099f31000) (0MB)
[    0.000000] efi: mem47: type=6, attr=0x800000000000000f, range=[0x0000000099f31000-0x000000009a0b7000) (1MB)
[    0.000000] efi: mem48: type=5, attr=0x800000000000000f, range=[0x000000009a0b7000-0x000000009a1bf000) (1MB)
[    0.000000] efi: mem49: type=6, attr=0x800000000000000f, range=[0x000000009a1bf000-0x000000009a2af000) (0MB)
[    0.000000] efi: mem50: type=6, attr=0x800000000000000f, range=[0x000000009a2af000-0x000000009a3bf000) (1MB)
[    0.000000] efi: mem51: type=0, attr=0xf, range=[0x000000009a3bf000-0x000000009add3000) (10MB)
[    0.000000] efi: mem52: type=0, attr=0xf, range=[0x000000009add3000-0x000000009aebf000) (0MB)
[    0.000000] efi: mem53: type=10, attr=0xf, range=[0x000000009aebf000-0x000000009af91000) (0MB)
[    0.000000] efi: mem54: type=10, attr=0xf, range=[0x000000009af91000-0x000000009afbf000) (0MB)
[    0.000000] efi: mem55: type=9, attr=0xf, range=[0x000000009afbf000-0x000000009afdf000) (0MB)
[    0.000000] efi: mem56: type=9, attr=0xf, range=[0x000000009afdf000-0x000000009afff000) (0MB)
[    0.000000] efi: mem57: type=4, attr=0xf, range=[0x000000009afff000-0x000000009b000000) (0MB)
[    0.000000] efi: mem58: type=7, attr=0xf, range=[0x0000000100000000-0x000000025f600000) (5622MB)
[    0.000000] efi: mem59: type=0, attr=0x0, range=[0x00000000000a0000-0x00000000000c0000) (0MB)
[    0.000000] efi: mem60: type=0, attr=0x0, range=[0x000000009b000000-0x000000009fa00000) (74MB)
[    0.000000] efi: mem61: type=11, attr=0x8000000000000001, range=[0x00000000e0000000-0x00000000f0000000) (256MB)
[    0.000000] efi: mem62: type=11, attr=0x8000000000000001, range=[0x00000000feb00000-0x00000000feb04000) (0MB)
[    0.000000] efi: mem63: type=11, attr=0x8000000000000001, range=[0x00000000fec00000-0x00000000fec01000) (0MB)
[    0.000000] efi: mem64: type=11, attr=0x8000000000000001, range=[0x00000000fed10000-0x00000000fed1a000) (0MB)
[    0.000000] efi: mem65: type=11, attr=0x8000000000000001, range=[0x00000000fed1c000-0x00000000fed20000) (0MB)
[    0.000000] efi: mem66: type=11, attr=0x8000000000000001, range=[0x00000000fee00000-0x00000000fee01000) (0MB)
[    0.000000] efi: mem67: type=11, attr=0x8000000000000000, range=[0x00000000ffb80000-0x00000000fff00000) (3MB)
[    0.000000] efi: mem68: type=11, attr=0x8000000000000000, range=[0x00000000fff00000-0x00000000fff40000) (0MB)
[    0.000000] efi: mem69: type=11, attr=0x8000000000000000, range=[0x00000000fff40000-0x0000000100000000) (0MB)
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: Dell Inc. Inspiron 7520/0PXH02, BIOS A10 05/13/2013
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x25f600 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-E7FFF write-protect
[    0.000000]   E8000-EFFFF write-combining
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FE0000000 write-back
[    0.000000]   2 base 09B000000 mask FFF000000 uncachable
[    0.000000]   3 base 09C000000 mask FFC000000 uncachable
[    0.000000]   4 base 0FFA00000 mask FFFE00000 write-protect
[    0.000000]   5 base 0FFC00000 mask FFFC00000 write-protect
[    0.000000]   6 base 100000000 mask F00000000 write-back
[    0.000000]   7 base 200000000 mask F80000000 write-back
[    0.000000]   8 base 25F600000 mask FFFE00000 uncachable
[    0.000000]   9 base 25F800000 mask FFF800000 uncachable
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: last_pfn = 0x9b000 max_arch_pfn = 0x400000000
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff88000007e000] 7e000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x02fd1000, 0x02fd1fff] PGTABLE
[    0.000000] BRK [0x02fd2000, 0x02fd2fff] PGTABLE
[    0.000000] BRK [0x02fd3000, 0x02fd3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x25f400000-0x25f5fffff]
[    0.000000]  [mem 0x25f400000-0x25f5fffff] page 2M
[    0.000000] BRK [0x02fd4000, 0x02fd4fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x25c000000-0x25f3fffff]
[    0.000000]  [mem 0x25c000000-0x25f3fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x200000000-0x25bffffff]
[    0.000000]  [mem 0x200000000-0x25bffffff] page 2M
[    0.000000] BRK [0x02fd5000, 0x02fd5fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x00100000-0x1fffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x1fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x20200000-0x40003fff]
[    0.000000]  [mem 0x20200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0x40003fff] page 4k
[    0.000000] BRK [0x02fd6000, 0x02fd6fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x40005000-0x8ffaffff]
[    0.000000]  [mem 0x40005000-0x401fffff] page 4k
[    0.000000]  [mem 0x40200000-0x8fdfffff] page 2M
[    0.000000]  [mem 0x8fe00000-0x8ffaffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x913b0000-0x99dbefff]
[    0.000000]  [mem 0x913b0000-0x913fffff] page 4k
[    0.000000]  [mem 0x91400000-0x99bfffff] page 2M
[    0.000000]  [mem 0x99c00000-0x99dbefff] page 4k
[    0.000000] init_memory_mapping: [mem 0x9afff000-0x9affffff]
[    0.000000]  [mem 0x9afff000-0x9affffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x1ffffffff]
[    0.000000]  [mem 0x100000000-0x1ffffffff] page 2M
[    0.000000] RAMDISK: [mem 0x35eb2000-0x36f50fff]
[    0.000000] ACPI: RSDP 000000009affe014 00024 (v02 DELL  )
[    0.000000] ACPI: XSDT 000000009affe210 000B4 (v01 DELL    CL09    00000001      01000013)
[    0.000000] ACPI: FACP 000000009affa000 0010C (v05 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: DSDT 000000009afee000 08F61 (v01 DELL    CL09    00000000 ASL  00040000)
[    0.000000] ACPI: FACS 000000009afb9000 00040
[    0.000000] ACPI: SLIC 000000009affd000 00176 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: UEFI 000000009affc000 00236 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: ASF! 000000009affb000 000A5 (v32 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: HPET 000000009aff9000 00038 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: APIC 000000009aff8000 0008C (v03 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: MCFG 000000009aff7000 0003C (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: SLIC 000000009afed000 00176 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: SSDT 000000009afec000 006FE (v01 COMPAL CRV ORB  00001000 ACPI 00040000)
[    0.000000] ACPI: BOOT 000000009afea000 00028 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: ASPT 000000009afe8000 00034 (v07 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: DBGP 000000009afe7000 00034 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: FPDT 000000009afe5000 00044 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: MSDM 000000009afe4000 00055 (v03 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: SSDT 000000009afe3000 008A2 (v01 COMPAL CRV ORB  00003000 ACPI 00040000)
[    0.000000] ACPI: SSDT 000000009afe2000 00A92 (v01 COMPAL CRV ORB  00003000 ACPI 00040000)
[    0.000000] ACPI: SSDT 000000009afdf000 01EED (v01 COMPAL CRV ORB  00001000 ACPI 00040000)
[    0.000000] ACPI: BGRT 000000009afe1000 00038 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000025f5fffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x25f5fffff]
[    0.000000]   NODE_DATA [mem 0x25f5f1000-0x25f5f5fff]
[    0.000000]  [ffffea0000000000-ffffea00097fffff] PMD -> [ffff880256c00000-ffff88025ebfffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x25f5fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x00087fff]
[    0.000000]   node   0: [mem 0x00100000-0x1fffffff]
[    0.000000]   node   0: [mem 0x20200000-0x40003fff]
[    0.000000]   node   0: [mem 0x40005000-0x8ffaffff]
[    0.000000]   node   0: [mem 0x913b0000-0x99dbefff]
[    0.000000]   node   0: [mem 0x9afff000-0x9affffff]
[    0.000000]   node   0: [mem 0x100000000-0x25f5fffff]
[    0.000000] On node 0 totalpages: 2063686
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 23 pages reserved
[    0.000000]   DMA zone: 3975 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 9695 pages used for memmap
[    0.000000]   DMA32 zone: 620479 pages, LIFO batch:31
[    0.000000]   Normal zone: 22488 pages used for memmap
[    0.000000]   Normal zone: 1439232 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x00088000-0x000bffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000c0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x20000000-0x201fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x40004000-0x40004fff]
[    0.000000] PM: Registered nosave memory: [mem 0x8ffb0000-0x913affff]
[    0.000000] PM: Registered nosave memory: [mem 0x99dbf000-0x9aebefff]
[    0.000000] PM: Registered nosave memory: [mem 0x9aebf000-0x9afbefff]
[    0.000000] PM: Registered nosave memory: [mem 0x9afbf000-0x9affefff]
[    0.000000] PM: Registered nosave memory: [mem 0x9b000000-0x9f9fffff]
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
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffb7ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffb80000-0xffffffff]
[    0.000000] e820: [mem 0x9fa00000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88025f200000 s86720 r8192 d23872 u262144
[    0.000000] pcpu-alloc: s86720 r8192 d23872 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2031416
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-15-generic.efi.signed root=UUID=de8aa5d2-2d79-42c4-af04-2f817a2e2f06 ro quiet splash acpi_osi=Linux acpi_backlight=vendor vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 7951320K/8254744K available (7149K kernel code, 1082K rwdata, 3312K rodata, 1364K init, 1420K bss, 303424K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] 	Offload RCU callbacks from all CPUs
[    0.000000] 	Offload RCU callbacks from CPUs: 0-255.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 2195.082 MHz processor
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 4390.16 BogoMIPS (lpj=8780328)
[    0.000005] pid_max: default: 32768 minimum: 301
[    0.000019] init_memory_mapping: [mem 0x99dbf000-0x99f30fff]
[    0.000021]  [mem 0x99dbf000-0x99f30fff] page 4k
[    0.000037] init_memory_mapping: [mem 0x99f31000-0x9a0b6fff]
[    0.000038]  [mem 0x99f31000-0x9a0b6fff] page 4k
[    0.000051] init_memory_mapping: [mem 0x9a0b7000-0x9a1befff]
[    0.000052]  [mem 0x9a0b7000-0x9a1befff] page 4k
[    0.000062] init_memory_mapping: [mem 0x9a1bf000-0x9a3befff]
[    0.000063]  [mem 0x9a1bf000-0x9a3befff] page 4k
[    0.040868] Security Framework initialized
[    0.040889] AppArmor: AppArmor initialized
[    0.040890] Yama: becoming mindful.
[    0.041399] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.043569] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.044550] Mount-cache hash table entries: 256
[    0.044719] Initializing cgroup subsys memory
[    0.044728] Initializing cgroup subsys devices
[    0.044729] Initializing cgroup subsys freezer
[    0.044731] Initializing cgroup subsys blkio
[    0.044732] Initializing cgroup subsys perf_event
[    0.044734] Initializing cgroup subsys hugetlb
[    0.044756] CPU: Physical Processor ID: 0
[    0.044757] CPU: Processor Core ID: 0
[    0.044761] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.044761] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.045168] mce: CPU supports 9 MCE banks
[    0.045181] CPU0: Thermal monitoring enabled (TM1)
[    0.045193] Last level iTLB entries: 4KB 512, 2MB 0, 4MB 0
[    0.045193] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32
[    0.045193] tlb_flushall_shift: 1
[    0.045323] Freeing SMP alternatives memory: 28K (ffffffff81e65000 - ffffffff81e6c000)
[    0.047586] ACPI: Core revision 20130517
[    0.053390] ACPI: All ACPI Tables successfully acquired
[    0.068525] ftrace: allocating 27844 entries in 109 pages
[    0.083213] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.122856] smpboot: CPU0: Intel(R) Core(TM) i7-3632QM CPU @ 2.20GHz (fam: 06, model: 3a, stepping: 09)
[    0.122863] TSC deadline timer enabled
[    0.122872] Performance Events: PEBS fmt1+, 16-deep LBR, IvyBridge events, full-width counters, Intel PMU driver.
[    0.122879] ... version:                3
[    0.122880] ... bit width:              48
[    0.122881] ... generic registers:      4
[    0.122882] ... value mask:             0000ffffffffffff
[    0.122883] ... max period:             0000ffffffffffff
[    0.122884] ... fixed-purpose events:   3
[    0.122885] ... event mask:             000000070000000f
[    0.138069] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.124470] smpboot: Booting Node   0, Processors  #1 #2 #3 #4 #5 #6 #7 OK
[    0.219614] Brought up 8 CPUs
[    0.219619] smpboot: Total of 8 processors activated (35121.31 BogoMIPS)
[    0.227226] devtmpfs: initialized
[    0.228313] EVM: security.selinux
[    0.228314] EVM: security.SMACK64
[    0.228315] EVM: security.capability
[    0.228368] PM: Registering ACPI NVS region [mem 0x9aebf000-0x9afbefff] (1048576 bytes)
[    0.229183] regulator-dummy: no parameters
[    0.229214] RTC time: 10:17:58, date: 01/27/14
[    0.229247] NET: Registered protocol family 16
[    0.229394] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.229396] ACPI: bus type PCI registered
[    0.229398] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.229454] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.229456] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.254764] PCI: Using configuration type 1 for base access
[    0.254880] dmi type 0xB1 record - unknown flag
[    0.255822] bio: create slab <bio-0> at 0
[    0.255969] ACPI: Added _OSI(Module Device)
[    0.255971] ACPI: Added _OSI(Processor Device)
[    0.255972] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.255974] ACPI: Added _OSI(Processor Aggregator Device)
[    0.255975] ACPI: Added _OSI(Linux)
[    0.257377] ACPI: EC: Look up EC in DSDT
[    0.258773] ACPI: Executed 1 blocks of module-level executable AML code
[    0.271448] ACPI: SSDT 000000009adf7018 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20121220)
[    0.271811] ACPI: Dynamic OEM Table Load:
[    0.271814] ACPI: SSDT           (null) 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20121220)
[    0.279181] ACPI: SSDT 000000009adf8a98 00303 (v01  PmRef    ApIst 00003000 INTL 20121220)
[    0.279570] ACPI: Dynamic OEM Table Load:
[    0.279572] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20121220)
[    0.283049] ACPI: SSDT 000000009adf6d98 00119 (v01  PmRef    ApCst 00003000 INTL 20121220)
[    0.283407] ACPI: Dynamic OEM Table Load:
[    0.283408] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20121220)
[    0.288183] ACPI: Interpreter enabled
[    0.288190] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20130517/hwxface-571)
[    0.288194] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20130517/hwxface-571)
[    0.288208] ACPI: (supports S0 S3 S4 S5)
[    0.288209] ACPI: Using IOAPIC for interrupt routing
[    0.288236] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.288343] ACPI: No dock devices found.
[    0.473830] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.473951] \_SB_.PCI0:_OSC invalid UUID
[    0.473953] _OSC request data:1 8 0 
[    0.473999] \_SB_.PCI0:_OSC invalid UUID
[    0.474000] _OSC request data:1 1f 0 
[    0.474003] acpi PNP0A08:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.474005] acpi PNP0A08:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.474347] PCI host bridge to bus 0000:00
[    0.474350] pci_bus 0000:00: root bus resource [bus 00-fe]
[    0.474352] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.474354] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.474356] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.474357] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff]
[    0.474359] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff]
[    0.474361] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff]
[    0.474362] pci_bus 0000:00: root bus resource [mem 0x000cc000-0x000cffff]
[    0.474364] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.474365] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.474367] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.474368] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.474370] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    0.474372] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    0.474373] pci_bus 0000:00: root bus resource [mem 0x000e8000-0x000ebfff]
[    0.474375] pci_bus 0000:00: root bus resource [mem 0x000ec000-0x000effff]
[    0.474376] pci_bus 0000:00: root bus resource [mem 0x000f0000-0x000fffff]
[    0.474378] pci_bus 0000:00: root bus resource [mem 0x9fa00000-0xfeafffff]
[    0.474386] pci 0000:00:00.0: [8086:0154] type 00 class 0x060000
[    0.474462] pci 0000:00:01.0: [8086:0151] type 01 class 0x060400
[    0.474495] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.474528] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.474562] pci 0000:00:02.0: [8086:0166] type 00 class 0x030000
[    0.474574] pci 0000:00:02.0: reg 0x10: [mem 0xc1000000-0xc13fffff 64bit]
[    0.474581] pci 0000:00:02.0: reg 0x18: [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.474586] pci 0000:00:02.0: reg 0x20: [io  0x4000-0x403f]
[    0.474679] pci 0000:00:14.0: [8086:1e31] type 00 class 0x0c0330
[    0.474703] pci 0000:00:14.0: reg 0x10: [mem 0xc1600000-0xc160ffff 64bit]
[    0.474778] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.474820] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.474856] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
[    0.474885] pci 0000:00:16.0: reg 0x10: [mem 0xc1614000-0xc161400f 64bit]
[    0.474965] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.475041] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
[    0.475065] pci 0000:00:1a.0: reg 0x10: [mem 0xc1619000-0xc16193ff]
[    0.475159] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.475228] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
[    0.475244] pci 0000:00:1b.0: reg 0x10: [mem 0xc1610000-0xc1613fff 64bit]
[    0.475315] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.475377] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
[    0.475458] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.475507] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.475538] pci 0000:00:1c.1: [8086:1e12] type 01 class 0x060400
[    0.475620] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.475659] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.475701] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
[    0.475724] pci 0000:00:1d.0: reg 0x10: [mem 0xc1618000-0xc16183ff]
[    0.475818] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.475865] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.475902] pci 0000:00:1f.0: [8086:1e57] type 00 class 0x060100
[    0.476066] pci 0000:00:1f.2: [8086:1e03] type 00 class 0x010601
[    0.476085] pci 0000:00:1f.2: reg 0x10: [io  0x4088-0x408f]
[    0.476094] pci 0000:00:1f.2: reg 0x14: [io  0x4094-0x4097]
[    0.476102] pci 0000:00:1f.2: reg 0x18: [io  0x4080-0x4087]
[    0.476111] pci 0000:00:1f.2: reg 0x1c: [io  0x4090-0x4093]
[    0.476119] pci 0000:00:1f.2: reg 0x20: [io  0x4060-0x407f]
[    0.476129] pci 0000:00:1f.2: reg 0x24: [mem 0xc1617000-0xc16177ff]
[    0.476177] pci 0000:00:1f.2: PME# supported from D3hot
[    0.476236] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
[    0.476252] pci 0000:00:1f.3: reg 0x10: [mem 0xc1615000-0xc16150ff 64bit]
[    0.476274] pci 0000:00:1f.3: reg 0x20: [io  0x4040-0x405f]
[    0.476392] pci 0000:01:00.0: [1002:682f] type 00 class 0x030000
[    0.476403] pci 0000:01:00.0: reg 0x10: [mem 0xa0000000-0xafffffff 64bit pref]
[    0.476411] pci 0000:01:00.0: reg 0x18: [mem 0xc0000000-0xc003ffff 64bit]
[    0.476417] pci 0000:01:00.0: reg 0x20: [io  0x3000-0x30ff]
[    0.476428] pci 0000:01:00.0: reg 0x30: [mem 0xfffe0000-0xffffffff pref]
[    0.476452] pci 0000:01:00.0: supports D1 D2
[    0.476454] pci 0000:01:00.0: PME# supported from D1 D2 D3hot
[    0.476520] pci 0000:01:00.0: System wakeup disabled by ACPI
[    0.482887] pci 0000:00:01.0: PCI bridge to [bus 01-06]
[    0.482892] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
[    0.482909] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xc0ffffff]
[    0.482913] pci 0000:00:01.0:   bridge window [mem 0xa0000000-0xafffffff 64bit pref]
[    0.483057] pci 0000:07:00.0: [10ec:8168] type 00 class 0x020000
[    0.483128] pci 0000:07:00.0: reg 0x10: [io  0x2000-0x20ff]
[    0.483253] pci 0000:07:00.0: reg 0x18: [mem 0xc1404000-0xc1404fff 64bit pref]
[    0.483328] pci 0000:07:00.0: reg 0x20: [mem 0xc1400000-0xc1403fff 64bit pref]
[    0.483668] pci 0000:07:00.0: supports D1 D2
[    0.483670] pci 0000:07:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.490938] pci 0000:00:1c.0: PCI bridge to [bus 07]
[    0.490943] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.490952] pci 0000:00:1c.0:   bridge window [mem 0xc1400000-0xc14fffff 64bit pref]
[    0.491076] pci 0000:08:00.0: [8086:0887] type 00 class 0x028000
[    0.491125] pci 0000:08:00.0: reg 0x10: [mem 0xc1500000-0xc1501fff 64bit]
[    0.491357] pci 0000:08:00.0: PME# supported from D0 D3hot D3cold
[    0.498949] pci 0000:00:1c.1: PCI bridge to [bus 08]
[    0.498956] pci 0000:00:1c.1:   bridge window [mem 0xc1500000-0xc15fffff]
[    0.559203] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.559256] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.559306] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.559356] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.559407] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.559459] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.559508] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.559556] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.559795] ACPI: Enabled 5 GPEs in block 00 to 3F
[    0.559801] ACPI: \_SB_.PCI0: notify handler is installed
[    0.559852] Found 1 acpi root devices
[    0.559884] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.559968] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.559973] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=none,locks=none
[    0.559974] vgaarb: loaded
[    0.559975] vgaarb: bridge control possible 0000:01:00.0
[    0.559976] vgaarb: no bridge control possible 0000:00:02.0
[    0.560117] SCSI subsystem initialized
[    0.560120] ACPI: bus type ATA registered
[    0.560161] libata version 3.00 loaded.
[    0.560174] ACPI: bus type USB registered
[    0.560188] usbcore: registered new interface driver usbfs
[    0.560195] usbcore: registered new interface driver hub
[    0.560216] usbcore: registered new device driver usb
[    0.560329] PCI: Using ACPI for IRQ routing
[    0.567092] PCI: pci_cache_line_size set to 64 bytes
[    0.567190] e820: reserve RAM buffer [mem 0x00088000-0x0008ffff]
[    0.567192] e820: reserve RAM buffer [mem 0x40004000-0x43ffffff]
[    0.567194] e820: reserve RAM buffer [mem 0x8ffb0000-0x8fffffff]
[    0.567195] e820: reserve RAM buffer [mem 0x99dbf000-0x9bffffff]
[    0.567197] e820: reserve RAM buffer [mem 0x9b000000-0x9bffffff]
[    0.567198] e820: reserve RAM buffer [mem 0x25f600000-0x25fffffff]
[    0.567270] NetLabel: Initializing
[    0.567272] NetLabel:  domain hash size = 128
[    0.567272] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.567281] NetLabel:  unlabeled traffic allowed by default
[    0.567340] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.567345] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.569366] Switched to clocksource hpet
[    0.573611] AppArmor: AppArmor Filesystem Enabled
[    0.573629] pnp: PnP ACPI init
[    0.573638] ACPI: bus type PNP registered
[    0.573662] pnp 00:00: [dma 4]
[    0.573677] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.573696] pnp 00:01: Plug and Play ACPI device, IDs INT0800 (active)
[    0.573779] pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.573806] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.573842] system 00:04: [io  0x0680-0x069f] has been reserved
[    0.573844] system 00:04: [io  0x1000-0x100f] has been reserved
[    0.573846] system 00:04: [io  0xffff] has been reserved
[    0.573848] system 00:04: [io  0xffff] has been reserved
[    0.573850] system 00:04: [io  0x0400-0x0453] could not be reserved
[    0.573852] system 00:04: [io  0x0458-0x047f] has been reserved
[    0.573854] system 00:04: [io  0x0500-0x057f] has been reserved
[    0.573855] system 00:04: [io  0x164e-0x164f] has been reserved
[    0.573857] system 00:04: [io  0xfd60-0xfd63] has been reserved
[    0.573860] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.573880] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.573923] system 00:06: [io  0x0454-0x0457] has been reserved
[    0.573926] system 00:06: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.573958] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.573984] pnp 00:08: Plug and Play ACPI device, IDs DLL0572 PNP0f13 (active)
[    0.633443] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.633445] system 00:09: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.633447] system 00:09: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.633449] system 00:09: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.633451] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
[    0.633453] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.633455] system 00:09: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.633456] system 00:09: [mem 0xff000000-0xff000fff] has been reserved
[    0.633459] system 00:09: [mem 0xff010000-0xffffffff] could not be reserved
[    0.633460] system 00:09: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.633462] system 00:09: [mem 0x9fa00000-0x9fa00fff] has been reserved
[    0.633465] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.633762] system 00:0a: [mem 0x20000000-0x201fffff] has been reserved
[    0.633764] system 00:0a: [mem 0x40004000-0x40004fff] has been reserved
[    0.633766] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.633782] pnp: PnP ACPI: found 11 devices
[    0.633783] ACPI: bus type PNP unregistered
[    0.639956] pci 0000:01:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
[    0.639984] pci 0000:01:00.0: BAR 6: assigned [mem 0xc0040000-0xc005ffff pref]
[    0.639987] pci 0000:00:01.0: PCI bridge to [bus 01-06]
[    0.639989] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
[    0.639992] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xc0ffffff]
[    0.639995] pci 0000:00:01.0:   bridge window [mem 0xa0000000-0xafffffff 64bit pref]
[    0.639998] pci 0000:00:1c.0: PCI bridge to [bus 07]
[    0.640002] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.640010] pci 0000:00:1c.0:   bridge window [mem 0xc1400000-0xc14fffff 64bit pref]
[    0.640017] pci 0000:00:1c.1: PCI bridge to [bus 08]
[    0.640022] pci 0000:00:1c.1:   bridge window [mem 0xc1500000-0xc15fffff]
[    0.640240] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.640242] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.640244] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.640245] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.640247] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.640249] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.640250] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff]
[    0.640252] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff]
[    0.640254] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff]
[    0.640255] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff]
[    0.640257] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff]
[    0.640259] pci_bus 0000:00: resource 15 [mem 0x000e0000-0x000e3fff]
[    0.640260] pci_bus 0000:00: resource 16 [mem 0x000e4000-0x000e7fff]
[    0.640262] pci_bus 0000:00: resource 17 [mem 0x000e8000-0x000ebfff]
[    0.640263] pci_bus 0000:00: resource 18 [mem 0x000ec000-0x000effff]
[    0.640265] pci_bus 0000:00: resource 19 [mem 0x000f0000-0x000fffff]
[    0.640267] pci_bus 0000:00: resource 20 [mem 0x9fa00000-0xfeafffff]
[    0.640269] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
[    0.640270] pci_bus 0000:01: resource 1 [mem 0xc0000000-0xc0ffffff]
[    0.640272] pci_bus 0000:01: resource 2 [mem 0xa0000000-0xafffffff 64bit pref]
[    0.640274] pci_bus 0000:07: resource 0 [io  0x2000-0x2fff]
[    0.640276] pci_bus 0000:07: resource 2 [mem 0xc1400000-0xc14fffff 64bit pref]
[    0.640277] pci_bus 0000:08: resource 1 [mem 0xc1500000-0xc15fffff]
[    0.640304] NET: Registered protocol family 2
[    0.640479] TCP established hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.640662] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.640774] TCP: Hash tables configured (established 65536 bind 65536)
[    0.640790] TCP: reno registered
[    0.640802] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.640830] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.640898] NET: Registered protocol family 1
[    0.640909] pci 0000:00:02.0: Boot video device
[    1.732231] PCI: CLS 64 bytes, default 64
[    1.732265] Trying to unpack rootfs image as initramfs...
[    2.015599] Freeing initrd memory: 17020K (ffff880035eb2000 - ffff880036f51000)
[    2.015603] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    2.015605] software IO TLB [mem 0x9238e000-0x9638e000] (64MB) mapped at [ffff88009238e000-ffff88009638dfff]
[    2.015654] Simple Boot Flag at 0x44 set to 0x1
[    2.015928] Scanning for low memory corruption every 60 seconds
[    2.016181] Initialise module verification
[    2.016217] audit: initializing netlink socket (disabled)
[    2.016226] type=2000 audit(1390817879.984:1): initialized
[    2.044063] bounce pool size: 64 pages
[    2.044072] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    2.045158] zbud: loaded
[    2.045283] VFS: Disk quotas dquot_6.5.2
[    2.045318] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    2.045738] fuse init (API version 7.22)
[    2.045802] msgmni has been set to 15703
[    2.046259] Key type asymmetric registered
[    2.046260] Asymmetric key parser 'x509' registered
[    2.046286] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    2.046327] io scheduler noop registered
[    2.046329] io scheduler deadline registered (default)
[    2.046349] io scheduler cfq registered
[    2.046422] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    2.046548] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.046560] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.046619] efifb: probing for efifb
[    2.047501] efifb: framebuffer at 0xb0000000, mapped to 0xffffc90021480000, using 8128k, total 8128k
[    2.047502] efifb: mode is 1920x1080x32, linelength=7680, pages=1
[    2.047503] efifb: scrolling: redraw
[    2.047505] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    2.052368] Console: switching to colour frame buffer device 240x67
[    2.057271] fb0: EFI VGA frame buffer device
[    2.057276] intel_idle: MWAIT substates: 0x21120
[    2.057277] intel_idle: v0.4 model 0x3A
[    2.057279] intel_idle: lapic_timer_reliable_states 0xffffffff
[    2.057379] ACPI: AC Adapter [ACAD] (on-line)
[    2.057459] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0C0C:00/input/input0
[    2.057463] ACPI: Power Button [PWRB]
[    2.057498] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    2.057519] ACPI: Lid Switch [LID0]
[    2.057545] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    2.057547] ACPI: Power Button [PWRF]
[    2.057607] ACPI: Requesting acpi_cpufreq
[    2.058702] GHES: HEST is not enabled!
[    2.058763] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    2.259551] ACPI: Battery Slot [BAT1] (battery present)
[    2.259646] Linux agpgart interface v0.103
[    2.260704] brd: module loaded
[    2.261296] loop: module loaded
[    2.261571] libphy: Fixed MDIO Bus: probed
[    2.261636] tun: Universal TUN/TAP device driver, 1.6
[    2.261637] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.261677] PPP generic driver version 2.4.2
[    2.261712] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.261714] ehci-pci: EHCI PCI platform driver
[    2.261812] ehci-pci 0000:00:1a.0: setting latency timer to 64
[    2.261819] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    2.261824] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.261837] ehci-pci 0000:00:1a.0: debug port 2
[    2.265726] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    2.265743] ehci-pci 0000:00:1a.0: irq 16, io mem 0xc1619000
[    2.275504] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    2.275521] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    2.275523] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.275525] usb usb1: Product: EHCI Host Controller
[    2.275526] usb usb1: Manufacturer: Linux 3.11.0-15-generic ehci_hcd
[    2.275528] usb usb1: SerialNumber: 0000:00:1a.0
[    2.275614] hub 1-0:1.0: USB hub found
[    2.275617] hub 1-0:1.0: 2 ports detected
[    2.275766] ehci-pci 0000:00:1d.0: setting latency timer to 64
[    2.275772] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    2.275776] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.275788] ehci-pci 0000:00:1d.0: debug port 2
[    2.279687] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    2.279700] ehci-pci 0000:00:1d.0: irq 23, io mem 0xc1618000
[    2.291487] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    2.291499] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    2.291501] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.291502] usb usb2: Product: EHCI Host Controller
[    2.291504] usb usb2: Manufacturer: Linux 3.11.0-15-generic ehci_hcd
[    2.291505] usb usb2: SerialNumber: 0000:00:1d.0
[    2.291581] hub 2-0:1.0: USB hub found
[    2.291584] hub 2-0:1.0: 2 ports detected
[    2.291651] ehci-platform: EHCI generic platform driver
[    2.291656] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.291658] ohci-pci: OHCI PCI platform driver
[    2.291664] ohci-platform: OHCI generic platform driver
[    2.291669] uhci_hcd: USB Universal Host Controller Interface driver
[    2.291770] xhci_hcd 0000:00:14.0: setting latency timer to 64
[    2.291774] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    2.291778] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    2.291867] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    2.291887] xhci_hcd 0000:00:14.0: irq 41 for MSI/MSI-X
[    2.291931] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    2.291933] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.291934] usb usb3: Product: xHCI Host Controller
[    2.291936] usb usb3: Manufacturer: Linux 3.11.0-15-generic xhci_hcd
[    2.291937] usb usb3: SerialNumber: 0000:00:14.0
[    2.291993] xHCI xhci_add_endpoint called for root hub
[    2.291995] xHCI xhci_check_bandwidth called for root hub
[    2.292010] hub 3-0:1.0: USB hub found
[    2.292017] hub 3-0:1.0: 4 ports detected
[    2.292295] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    2.292299] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    2.292319] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    2.292321] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.292322] usb usb4: Product: xHCI Host Controller
[    2.292324] usb usb4: Manufacturer: Linux 3.11.0-15-generic xhci_hcd
[    2.292325] usb usb4: SerialNumber: 0000:00:14.0
[    2.292380] xHCI xhci_add_endpoint called for root hub
[    2.292382] xHCI xhci_check_bandwidth called for root hub
[    2.292398] hub 4-0:1.0: USB hub found
[    2.292404] hub 4-0:1.0: 4 ports detected
[    2.299518] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.319777] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.319781] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.319870] mousedev: PS/2 mouse device common for all mice
[    2.322185] rtc_cmos 00:05: RTC can wake from S4
[    2.322301] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.322329] rtc_cmos 00:05: alarms up to one month, 242 bytes nvram, hpet irqs
[    2.322378] device-mapper: uevent: version 1.0.3
[    2.322426] device-mapper: ioctl: 4.25.0-ioctl (2013-06-26) initialised: dm-devel@redhat.com
[    2.322568] cpuidle: using governor ladder
[    2.322768] cpuidle: using governor menu
[    2.322777] ledtrig-cpu: registered to indicate activity on CPUs
[    2.322779] EFI Variables Facility v0.08 2004-May-17
[    2.330900] TCP: cubic registered
[    2.330977] NET: Registered protocol family 10
[    2.331143] NET: Registered protocol family 17
[    2.331150] Key type dns_resolver registered
[    2.331409] PM: Hibernation image not present or could not be loaded.
[    2.331412] Loading module verification certificates
[    2.332312] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 9da89dd2daeca3a3cb171fe18502208f132adef8'
[    2.332320] registered taskstats version 1
[    2.334369] Key type trusted registered
[    2.336367] Key type encrypted registered
[    2.338673] AppArmor: AppArmor sha1 policy hashing enabled
[    2.339138]   Magic number: 14:775:275
[    2.339157] tty tty12: hash matches
[    2.339262] rtc_cmos 00:05: setting system clock to 2014-01-27 10:18:00 UTC (1390817880)
[    2.340639] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.340640] EDD information not available.
[    2.341406] Freeing unused kernel memory: 1364K (ffffffff81d10000 - ffffffff81e65000)
[    2.341408] Write protecting the kernel read-only data: 12288k
[    2.343307] Freeing unused kernel memory: 1032K (ffff8800026fe000 - ffff880002800000)
[    2.344621] Freeing unused kernel memory: 784K (ffff880002b3c000 - ffff880002c00000)
[    2.347697] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.353374] systemd-udevd[145]: starting version 204
[    2.370609] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.370619] r8169 0000:07:00.0: can't disable ASPM; OS doesn't have ASPM control
[    2.370874] r8169 0000:07:00.0: irq 42 for MSI/MSI-X
[    2.370889] ahci 0000:00:1f.2: version 3.0
[    2.371020] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
[    2.371061] r8169 0000:07:00.0 eth0: RTL8168evl/8111evl at 0xffffc90000040000, e0:db:55:d0:88:47, XID 0c900880 IRQ 42
[    2.371063] r8169 0000:07:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    2.371074] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x5 impl SATA mode
[    2.371078] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst 
[    2.371083] ahci 0000:00:1f.2: setting latency timer to 64
[    2.376198] scsi0 : ahci
[    2.376276] scsi1 : ahci
[    2.376355] scsi2 : ahci
[    2.376430] scsi3 : ahci
[    2.376492] scsi4 : ahci
[    2.376555] scsi5 : ahci
[    2.376615] ata1: SATA max UDMA/133 abar m2048@0xc1617000 port 0xc1617100 irq 43
[    2.376618] ata2: DUMMY
[    2.376621] ata3: SATA max UDMA/133 abar m2048@0xc1617000 port 0xc1617200 irq 43
[    2.376623] ata4: DUMMY
[    2.376624] ata5: DUMMY
[    2.376625] ata6: DUMMY
[    2.587201] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    2.695089] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.695129] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.697893] ata3.00: ATAPI: HL-DT-ST DVDRW/BDROM CT40N, A102, max UDMA/133
[    2.700028] ata3.00: configured for UDMA/133
[    2.719454] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    2.719460] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.719859] hub 1-1:1.0: USB hub found
[    2.719923] hub 1-1:1.0: 6 ports detected
[    2.741171] ata1.00: ATA-8: WDC WD10JPVT-75A1YT0, 01.01A01, max UDMA/133
[    2.741177] ata1.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.742597] ata1.00: configured for UDMA/133
[    2.742791] scsi 0:0:0:0: Direct-Access     ATA      WDC WD10JPVT-75A 01.0 PQ: 0 ANSI: 5
[    2.742930] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.742933] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    2.743002] sd 0:0:0:0: [sda] Write Protect is off
[    2.743004] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.743011] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.743016] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.744943] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRWBD CT40N    A102 PQ: 0 ANSI: 5
[    2.749422] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.749427] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.749611] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.749667] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    2.793946]  sda: sda1 sda2 sda3 sda4 sda5 sda6 sda7
[    2.794329] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.834902] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    2.967144] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    2.967150] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.967418] hub 2-1:1.0: USB hub found
[    2.967520] hub 2-1:1.0: 8 ports detected
[    3.010707] tsc: Refined TSC clocksource calibration: 2195.014 MHz
[    3.190534] usb 3-3: new full-speed USB device number 3 using xhci_hcd
[    3.208983] usb 3-3: New USB device found, idVendor=041e, idProduct=30df
[    3.208985] usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    3.208987] usb 3-3: Product: SB X-Fi Surround 5.1 Pro
[    3.208988] usb 3-3: Manufacturer: Creative Technology Ltd
[    3.208989] usb 3-3: SerialNumber: 00000INF
[    3.209051] usb 3-3: ep 0x83 - rounding interval to 64 microframes, ep desc says 80 microframes
[    3.374301] usb 3-4: new low-speed USB device number 4 using xhci_hcd
[    3.396733] usb 3-4: New USB device found, idVendor=046d, idProduct=c043
[    3.396735] usb 3-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.396736] usb 3-4: Product: USB-PS/2 Optical Mouse
[    3.396737] usb 3-4: Manufacturer: Logitech
[    3.396789] usb 3-4: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    3.399514] hidraw: raw HID events driver (C) Jiri Kosina
[    3.404135] usbcore: registered new interface driver usbhid
[    3.404136] usbhid: USB HID core driver
[    3.405268] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.0/input/input4
[    3.405374] hid-generic 0003:046D:C043.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:14.0-4/input0
[    3.466382] usb 1-1.3: new high-speed USB device number 3 using ehci-pci
[    3.558978] usb 1-1.3: New USB device found, idVendor=0bda, idProduct=0129
[    3.558981] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    3.558982] usb 1-1.3: Product: USB2.0-CRW
[    3.558983] usb 1-1.3: Manufacturer: Generic
[    3.558984] usb 1-1.3: SerialNumber: 20100201396000000
[    3.630201] usb 1-1.5: new high-speed USB device number 4 using ehci-pci
[    3.791150] usb 1-1.5: New USB device found, idVendor=064e, idProduct=8126
[    3.791156] usb 1-1.5: New USB device strings: Mfr=2, Product=1, SerialNumber=0
[    3.791160] usb 1-1.5: Product: Laptop_Integrated_Webcam_HD
[    3.791163] usb 1-1.5: Manufacturer: SuYin
[    3.924858] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    4.005751] hub 2-1:1.0: over-current condition on port 5
[    4.009751] Switched to clocksource tsc
[    4.213503] hub 2-1:1.0: over-current condition on port 6
[    4.325288] usb 4-2: new SuperSpeed USB device number 2 using xhci_hcd
[    4.342140] usb 4-2: New USB device found, idVendor=067b, idProduct=2773
[    4.342147] usb 4-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    4.342150] usb 4-2: Product: USB-SATA Bridge
[    4.342154] usb 4-2: Manufacturer: Prolific Technology Inc.
[    4.342156] usb 4-2: SerialNumber: PROLIFICMP000000004
[    4.342429] usb 4-2: Set SEL for device-initiated U1 failed.
[    4.342547] usb 4-2: Set SEL for device-initiated U2 failed.
[    9.133281] Adding 1999868k swap on /dev/sda3.  Priority:-1 extents:1 across:1999868k FS
[    9.187199] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.269503] systemd-udevd[338]: starting version 204
[    9.385870] lp: driver loaded but no devices found
[    9.388493] i8k: unable to get SMM BIOS version
[    9.388726] Dell laptop SMM driver v1.14 21/02/2005 Massimo Dal Zotto (dz@debian.org)
[    9.404172] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20130517/utaddress-251)
[    9.404179] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.404183] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20130517/utaddress-251)
[    9.404188] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20130517/utaddress-251)
[    9.404191] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.404192] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20130517/utaddress-251)
[    9.404196] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20130517/utaddress-251)
[    9.404199] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.404201] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    9.407441] [drm] Initialized drm 1.1.0 20060810
[    9.409899] mei_me 0000:00:16.0: setting latency timer to 64
[    9.409945] mei_me 0000:00:16.0: irq 44 for MSI/MSI-X
[    9.417241] cfg80211: Calling CRDA to update world regulatory domain
[    9.420528] Intel(R) Wireless WiFi driver for Linux, in-tree:
[    9.420531] Copyright(c) 2003-2013 Intel Corporation
[    9.420611] iwlwifi 0000:08:00.0: can't disable ASPM; OS doesn't have ASPM control
[    9.420740] iwlwifi 0000:08:00.0: irq 45 for MSI/MSI-X
[    9.422469] [drm] Memory usable by graphics device = 2048M
[    9.422473] checking generic (b0000000 7f0000) vs hw (b0000000 10000000)
[    9.422475] fb: conflicting fb hw usage inteldrmfb vs EFI VGA - removing generic driver
[    9.422492] Console: switching to colour dummy device 80x25
[    9.422577] i915 0000:00:02.0: setting latency timer to 64
[    9.422944] AMD IOMMUv2 driver by Joerg Roedel <joerg.roedel@amd.com>
[    9.422946] AMD IOMMUv2 functionality not available on this system
[    9.423196] wmi: Mapper loaded
[    9.426410] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[    9.426413] Disabling lock debugging due to kernel taint
[    9.429942] fglrx: module verification failed: signature and/or required key missing - tainting kernel
[    9.439382] <6>[fglrx] Maximum main memory to use for locked dma buffers: 7623 MBytes.
[    9.439509] <6>[fglrx]   vendor: 1002 device: 682f count: 1
[    9.439677] <6>[fglrx] ioport: bar 4, base 0x3000, size: 0x100
[    9.439683] pci 0000:01:00.0: enabling device (0000 -> 0003)
[    9.439775] <6>[fglrx] Kernel PAT support is enabled
[    9.439789] <6>[fglrx] module loaded - fglrx 13.10.10 [May 23 2013] with 1 minors
[    9.445019] microcode: CPU0 sig=0x306a9, pf=0x10, revision=0x15
[    9.450565] i915 0000:00:02.0: irq 46 for MSI/MSI-X
[    9.450576] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    9.450577] [drm] Driver supports precise vblank timestamp query.
[    9.450595] ACPI Warning: \_SB_.PCI0.GFX0._DSM: Argument #4 type mismatch - Found [Integer], ACPI requires [Package] (20130517/nsarguments-95)
[    9.450634] ACPI Warning: \_SB_.PCI0.GFX0._DSM: Argument #4 type mismatch - Found [Integer], ACPI requires [Package] (20130517/nsarguments-95)
[    9.450698] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    9.450700] vgaarb: transferring owner from PCI:0000:00:02.0 to PCI:0000:01:00.0
[    9.497948] fbcon: inteldrmfb (fb0) is primary device
[    9.513643] type=1400 audit(1390814287.679:2): apparmor="STATUS" operation="profile_load" parent=427 profile="unconfined" name="/sbin/dhclient" pid=457 comm="apparmor_parser"
[    9.513646] type=1400 audit(1390814287.679:3): apparmor="STATUS" operation="profile_load" parent=427 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=457 comm="apparmor_parser"
[    9.513649] type=1400 audit(1390814287.679:4): apparmor="STATUS" operation="profile_load" parent=427 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=457 comm="apparmor_parser"
[    9.514031] type=1400 audit(1390814287.679:5): apparmor="STATUS" operation="profile_replace" parent=427 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=457 comm="apparmor_parser"
[    9.514034] type=1400 audit(1390814287.679:6): apparmor="STATUS" operation="profile_replace" parent=427 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=457 comm="apparmor_parser"
[    9.514243] type=1400 audit(1390814287.679:7): apparmor="STATUS" operation="profile_replace" parent=427 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=457 comm="apparmor_parser"
[    9.563699] iwlwifi 0000:08:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[    9.576356] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    9.576357] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    9.576358] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    9.576359] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_P2P disabled
[    9.576361] iwlwifi 0000:08:00.0: Detected Intel(R) Centrino(R) Wireless-N 2230 BGN, REV=0xC8
[    9.576462] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[    9.598241] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    9.599645] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    9.729200] rts5139: module is from the staging directory, the quality is unknown, you have been warned.
[    9.730471] Linux video capture interface: v2.00
[    9.732291] scsi6 : SCSI emulation for RTS5139 USB card reader
[    9.732380] usbcore: registered new interface driver rts5139
[    9.732400] scsi 6:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
[    9.732730] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    9.738125] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_HD (064e:8126)
[    9.738272] usbcore: registered new interface driver snd-usb-audio
[    9.738367] input: Dell WMI hotkeys as /devices/virtual/input/input5
[    9.740393] microcode: CPU1 sig=0x306a9, pf=0x10, revision=0x15
[    9.743024] cfg80211: World regulatory domain updated:
[    9.743025] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    9.743026] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.743027] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.743027] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    9.743028] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.743028] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.745566] microcode: CPU2 sig=0x306a9, pf=0x10, revision=0x15
[    9.745858] microcode: CPU3 sig=0x306a9, pf=0x10, revision=0x15
[    9.746158] microcode: CPU4 sig=0x306a9, pf=0x10, revision=0x15
[    9.746455] microcode: CPU5 sig=0x306a9, pf=0x10, revision=0x15
[    9.746747] microcode: CPU6 sig=0x306a9, pf=0x10, revision=0x15
[    9.747038] microcode: CPU7 sig=0x306a9, pf=0x10, revision=0x15
[    9.747353] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    9.761682] usb-storage 4-2:1.0: USB Mass Storage device detected
[    9.762461] input: Laptop_Integrated_Webcam_HD as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input6
[    9.762518] usbcore: registered new interface driver uvcvideo
[    9.762519] USB Video Class driver (1.1.1)
[    9.763276] scsi7 : usb-storage 4-2:1.0
[    9.763361] usb 4-2: Set SEL for device-initiated U1 failed.
[    9.763437] usb 4-2: Set SEL for device-initiated U2 failed.
[    9.763461] usbcore: registered new interface driver usb-storage
[    9.811596] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   10.138980] Console: switching to colour frame buffer device 240x67
[   10.142427] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   10.142428] i915 0000:00:02.0: registered panic notifier
[   10.142669] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[   10.143314] ACPI: Video Device [PEGP] (multi-head: yes  rom: no  post: no)
[   10.143349] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2c/LNXVIDEO:00/input/input7
[   10.143392] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   10.143849] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   10.143874] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:02/input/input8
[   10.143917] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   10.144067] snd_hda_intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   10.155667] hda_codec: CX20590: BIOS auto-probing.
[   10.156092] autoconfig: line_outs=1 (0x1f/0x0/0x0/0x0/0x0) type:speaker
[   10.156094]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   10.156095]    hp_outs=1 (0x19/0x0/0x0/0x0/0x0)
[   10.156096]    mono: mono_out=0x0
[   10.156096]    inputs:
[   10.156098]      Internal Mic=0x23
[   10.156099]      Mic=0x1a
[   10.156960] hda_codec: Enable sync_write for stable communication
[   10.162149] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   10.162204] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   10.162249] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   10.659561] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x450f02)
[   10.690021] psmouse serio1: elantech: Synaptics capabilities query result 0x79, 0x17, 0x0c.
[   10.798537] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off
[   10.849869] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input12
[   11.688585] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   11.765292] scsi 7:0:0:0: Direct-Access     ST2000DM 001-1CH164       CC24 PQ: 0 ANSI: 0
[   11.765609] sd 7:0:0:0: Attached scsi generic sg3 type 0
[   11.765787] sd 7:0:0:0: [sdc] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[   11.766053] sd 7:0:0:0: [sdc] Write Protect is off
[   11.766056] sd 7:0:0:0: [sdc] Mode Sense: 03 00 00 00
[   11.766333] sd 7:0:0:0: [sdc] No Caching mode page found
[   11.766358] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[   11.767219] sd 7:0:0:0: [sdc] No Caching mode page found
[   11.767242] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[   11.792318]  sdc: sdc1 sdc2
[   11.793257] sd 7:0:0:0: [sdc] No Caching mode page found
[   11.793278] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[   11.793299] sd 7:0:0:0: [sdc] Attached SCSI disk
[   12.335169] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[   14.683548] init: failsafe main process (809) killed by TERM signal
[   14.879906] Bluetooth: Core ver 2.16
[   14.879923] NET: Registered protocol family 31
[   14.879925] Bluetooth: HCI device and connection manager initialized
[   14.879932] Bluetooth: HCI socket layer initialized
[   14.879935] Bluetooth: L2CAP socket layer initialized
[   14.879940] Bluetooth: SCO socket layer initialized
[   14.884028] Bluetooth: RFCOMM TTY layer initialized
[   14.884037] Bluetooth: RFCOMM socket layer initialized
[   14.884038] Bluetooth: RFCOMM ver 1.11
[   14.885937] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.885939] Bluetooth: BNEP filters: protocol multicast
[   14.885946] Bluetooth: BNEP socket layer initialized
[   14.934441] type=1400 audit(1390814293.107:8): apparmor="STATUS" operation="profile_replace" parent=943 profile="unconfined" name="/sbin/dhclient" pid=948 comm="apparmor_parser"
[   14.934451] type=1400 audit(1390814293.107:9): apparmor="STATUS" operation="profile_replace" parent=943 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=948 comm="apparmor_parser"
[   14.934457] type=1400 audit(1390814293.107:10): apparmor="STATUS" operation="profile_replace" parent=943 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=948 comm="apparmor_parser"
[   14.935034] type=1400 audit(1390814293.107:11): apparmor="STATUS" operation="profile_replace" parent=943 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=948 comm="apparmor_parser"
[   14.935040] type=1400 audit(1390814293.107:12): apparmor="STATUS" operation="profile_replace" parent=943 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=948 comm="apparmor_parser"
[   14.935174] type=1400 audit(1390814293.107:13): apparmor="STATUS" operation="profile_load" parent=943 profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=952 comm="apparmor_parser"
[   14.935181] type=1400 audit(1390814293.107:14): apparmor="STATUS" operation="profile_load" parent=943 profile="unconfined" name="/usr/sbin/cupsd" pid=952 comm="apparmor_parser"
[   14.935339] type=1400 audit(1390814293.107:15): apparmor="STATUS" operation="profile_replace" parent=943 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=948 comm="apparmor_parser"
[   14.935791] type=1400 audit(1390814293.107:16): apparmor="STATUS" operation="profile_replace" parent=943 profile="unconfined" name="/usr/sbin/cupsd" pid=952 comm="apparmor_parser"
[   14.936980] type=1400 audit(1390814293.107:17): apparmor="STATUS" operation="profile_load" parent=943 profile="unconfined" name="/usr/sbin/mysqld" pid=953 comm="apparmor_parser"
[   15.048266] ppdev: user-space parallel port driver
[   15.059520] init: avahi-cups-reload main process (965) terminated with status 1
[   15.914644] r8169 0000:07:00.0 eth0: link down
[   15.914684] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.914930] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.916442] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[   15.923916] iwlwifi 0000:08:00.0: Radio type=0x2-0x0-0x0
[   16.167391] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[   16.174883] iwlwifi 0000:08:00.0: Radio type=0x2-0x0-0x0
[   16.232148] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.232425] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.013445] postgres (1236): /proc/1236/oom_adj is deprecated, please use /proc/1236/oom_score_adj instead.
[   18.305628] fglrx_pci 0000:01:00.0: irq 48 for MSI/MSI-X
[   18.306043] <6>[fglrx] Firegl kernel thread PID: 1241
[   18.306176] <6>[fglrx] Firegl kernel thread PID: 1242
[   18.306294] <6>[fglrx] Firegl kernel thread PID: 1243
[   18.306363] <6>[fglrx] IRQ 48 Enabled
[   18.314964] <6>[fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   18.314966] <6>[fglrx] Reserved FB block: Unshared offset:f87c000, size:484000 
[   18.314967] <6>[fglrx] Reserved FB block: Unshared offset:7fff4000, size:c000 
[   18.446437] <6>[fglrx] IRQ 48 Disabled
[   18.446876] <6>[fglrx] module unloaded - fglrx 13.10.10 [May 23 2013]
[   18.464194] AMD IOMMUv2 driver by Joerg Roedel <joerg.roedel@amd.com>
[   18.464197] AMD IOMMUv2 functionality not available on this system
[   18.473582] <6>[fglrx] Maximum main memory to use for locked dma buffers: 7623 MBytes.
[   18.473729] <6>[fglrx]   vendor: 1002 device: 682f count: 1
[   18.473908] <6>[fglrx] ioport: bar 4, base 0x3000, size: 0x100
[   18.473995] <6>[fglrx] Kernel PAT support is enabled
[   18.474006] <6>[fglrx] module loaded - fglrx 13.10.10 [May 23 2013] with 1 minors
[   19.827016] fglrx_pci 0000:01:00.0: irq 48 for MSI/MSI-X
[   19.827479] <6>[fglrx] Firegl kernel thread PID: 1346
[   19.827597] <6>[fglrx] Firegl kernel thread PID: 1347
[   19.827707] <6>[fglrx] Firegl kernel thread PID: 1348
[   19.827794] <6>[fglrx] IRQ 48 Enabled
[   19.835971] <6>[fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   19.835973] <6>[fglrx] Reserved FB block: Unshared offset:f87c000, size:484000 
[   19.835974] <6>[fglrx] Reserved FB block: Unshared offset:7fff4000, size:c000 
[   20.444192] vboxdrv: Found 8 processor cores.
[   20.444553] vboxdrv: fAsync=0 offMin=0xcb offMax=0x26f7
[   20.444617] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   20.444619] vboxdrv: Successfully loaded version 4.3.6 (interface 0x001a0007).
[   20.651150] vboxpci: IOMMU not found (not registered)
[   21.474736] <6>[fglrx] IRQ 48 Disabled
[   41.987924] iwlwifi 0000:08:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[   41.987927] iwlwifi 0000:08:00.0: Current CMD queue read_ptr 33 write_ptr 34
[   48.149104] BUG: soft lockup - CPU#5 stuck for 22s! [modprobe:1554]
[   48.149106] Modules linked in: pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) fglrx(POF-) amd_iommu_v2 parport_pc ppdev bnep rfcomm bluetooth binfmt_misc nls_iso8859_1 joydev snd_hda_codec_hdmi snd_hda_codec_conexant x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel usb_storage aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd dell_wmi uvcvideo sparse_keymap videobuf2_vmalloc videobuf2_memops videobuf2_core snd_usb_audio videodev rts5139(C) snd_usbmidi_lib dcdbas arc4 iwldvm mac80211 snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_page_alloc microcode snd_seq_midi snd_seq_midi_event snd_rawmidi psmouse serio_raw snd_seq snd_seq_device wmi snd_timer iwlwifi i915 cfg80211 snd mei_me drm_kms_helper mei drm video lpc_ich soundcore mac_hid i2c_algo_bit i8k lp parport hid_generic usbhid hid ahci r8169 libahci mii [last unloaded: amd_iommu_v2]
[   48.149154] CPU: 5 PID: 1554 Comm: modprobe Tainted: PF        C O 3.11.0-15-generic #23-Ubuntu
[   48.149155] Hardware name: Dell Inc. Inspiron 7520/0PXH02, BIOS A10 05/13/2013
[   48.149156] task: ffff88023de3ddc0 ti: ffff88023b25c000 task.ti: ffff88023b25c000
[   48.149157] RIP: 0010:[<ffffffff81019e60>]  [<ffffffff81019e60>] hw_breakpoint_pmu_read+0x10/0x10
[   48.149162] RSP: 0018:ffff88023b25dc30  EFLAGS: 00000246
[   48.149163] RAX: 0000000000000005 RBX: 0000000000000001 RCX: 00000000010bf450
[   48.149164] RDX: 00000000138048d2 RSI: 000000000000311a RDI: 0000000000000882
[   48.149165] RBP: ffff88023b25dc50 R08: 0000000000000001 R09: ffff88023b25dcd8
[   48.149166] R10: ffff880244c6a000 R11: ffff8802518f5000 R12: ffff880244c6a000
[   48.149166] R13: ffff8802518f5000 R14: 0000000000000001 R15: ffff88023b25dd88
[   48.149168] FS:  00007f7d0e124740(0000) GS:ffff88025f340000(0000) knlGS:0000000000000000
[   48.149169] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[   48.149170] CR2: 00007f7d0e14ff30 CR3: 000000024f444000 CR4: 00000000001407e0
[   48.149170] Stack:
[   48.149171]  ffffffff813696fa 00000000002c982c 0000000000000bb8 000000000000000a
[   48.149173]  ffff88023b25dc60 ffffffff81369660 ffff88023b25dc88 ffffffffa10121bc
[   48.149175]  0000000000000bb8 000000000000000a 00000000002c982c ffff88023b25dcd8
[   48.149177] Call Trace:
[   48.149181]  [<ffffffff813696fa>] ? delay_tsc+0x4a/0x80
[   48.149184]  [<ffffffff81369660>] __udelay+0x30/0x40
[   48.149218]  [<ffffffffa10121bc>] KCL_DelayInMicroSeconds+0x1c/0x80 [fglrx]
[   48.149251]  [<ffffffffa1032086>] MCIL_WaitFor+0x46/0x70 [fglrx]
[   48.149292]  [<ffffffffa1065668>] ? Cail_MCILWaitFor+0xe8/0x160 [fglrx]
[   48.149331]  [<ffffffffa10656e0>] Cail_MCILWaitFor+0x160/0x160 [fglrx]
[   48.149375]  [<ffffffffa1083552>] ? update_medium_grain_clock_gating+0x302/0x320 [fglrx]
[   48.149417]  [<ffffffffa10845da>] ? Cail_CapeVerde_SetVcePowerGating+0x12a/0x1c0 [fglrx]
[   48.149459]  [<ffffffffa1084874>] ? Cail_CapeVerde_ClockGatingControl+0x204/0x220 [fglrx]
[   48.149501]  [<ffffffffa10862f7>] ? perform_disable_clock_gating+0x87/0xc0 [fglrx]
[   48.149543]  [<ffffffffa1086220>] ? perform_power_control+0x50/0xa0 [fglrx]
[   48.149585]  [<ffffffffa1086be5>] ? Cail_DisablePowerGatingClockGating+0x25/0x40 [fglrx]
[   48.149621]  [<ffffffffa1057e28>] ? CAILExit+0x68/0x180 [fglrx]
[   48.149652]  [<ffffffffa102d135>] ? firegl_cail_free+0x45/0x80 [fglrx]
[   48.149680]  [<ffffffffa1020275>] ? cleanup_device+0x35/0x2a0 [fglrx]
[   48.149683]  [<ffffffff816ee5be>] ? _raw_spin_lock+0xe/0x20
[   48.149712]  [<ffffffffa10231d5>] ? firegl_cleanup_device_heads+0x65/0xa0 [fglrx]
[   48.149765]  [<ffffffffa11d788d>] ? firegl_cleanup_module+0x99/0x16c [fglrx]
[   48.149768]  [<ffffffff810c9c1b>] ? SyS_delete_module+0x16b/0x2d0
[   48.149771]  [<ffffffff816f2a2c>] ? do_page_fault+0x2c/0x50
[   48.149773]  [<ffffffff816f721d>] ? system_call_fastpath+0x1a/0x1f
[   48.149774] Code: 00 49 c7 85 38 05 00 00 00 00 00 00 41 5d 5d c3 66 66 2e 0f 1f 84 00 00 00 00 00 0f 1f 44 00 00 55 48 89 e5 5d c3 0f 1f 44 00 00 <55> 48 89 e5 0f 31 89 c0 48 c1 e2 20 48 09 c2 48 89 d0 5d c3 66 
[   63.890719] iwlwifi 0000:08:00.0: HCMD_ACTIVE already clear for command REPLY_SCAN_CMD
[   63.890820] <6>[fglrx] module unloaded - fglrx 13.10.10 [May 23 2013]
[   69.289688] xhci_queue_isoc_tx_prepare: 123 callbacks suppressed
[   73.893687] wlan0: authenticate with xx:xx:xx:xx:xx:xx
[   73.899601] wlan0: send auth to xx:xx:xx:xx:xx:xx (try 1/3)
[   73.902856] wlan0: authenticated
[   73.904837] wlan0: associate with xx:xx:xx:xx:xx:xx (try 1/3)
[   73.908398] wlan0: RX AssocResp from xx:xx:xx:xx:xx:xx (capab=0x411 status=0 aid=1)
[   73.911097] wlan0: associated
[   73.911138] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   73.911206] cfg80211: Calling CRDA for country: FR
[   73.913121] cfg80211: Regulatory domain changed to country: FR
[   73.913123] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   73.913125] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   73.913126] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   73.913127] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   73.913128] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[   73.913129] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
[   73.993659] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by 02:1a:11:f1:a4:9a
[   77.870000] EXT4-fs (sdc1): mounted filesystem with ordered data mode. Opts: (null)
[  119.760323] xhci_queue_isoc_tx_prepare: 14 callbacks suppressed
[  124.538666] delay: estimated 192, actual 0
[  126.536435] delay: estimated 240, actual 0
[  132.529808] delay: estimated 144, actual 0
[  144.508582] delay: estimated 192, actual 0
[  150.501959] delay: estimated 192, actual 0
[  166.475302] delay: estimated 240, actual 48
[  168.473082] delay: estimated 193, actual 48
[  183.584398] delay: estimated 192, actual 48

```

If you need any other log or information, please, do not hesitate to ask :) .

Thanks for help !
M@d

---

### Post by Bashing-om on 2014-01-30
M@dinko12; Hi !

I do not run integrated graphics thus have no direct experience, however;
Version 13.10 with Open soource drivers ? A lot has been done in this department with the latest releases.
see:
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)
[http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10/](http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10/)

Please let us know how it goes .

[INDENT][INDENT]You have come a long way, baby
[/INDENT][/INDENT]

---

