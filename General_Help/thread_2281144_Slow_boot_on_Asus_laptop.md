---
title: "Slow boot on Asus laptop"
date: 2015-06-04
forum: General Help
---

### Post by nbunya on 2015-06-04
Hi all
I'm new in ubuntu and I have a problem with a boot time.
If someone will help me will be nice.


My configuration ([COLOR=#333333][FONT=franklingothicdemicondcRg]ASUS U32VJ-RO003H[/FONT][/COLOR])

Ubuntu 14.10
i5 3210M
GeForce GT 635M
16 GB of RAM

I see long delays dmesq, but cannot understand out what was going on...

Thank You!

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.16.0-33-generic (buildd@toyol) (gcc version 4.9.1 (Ubuntu 4.9.1-16ubuntu6) ) #44-Ubuntu SMP Thu Mar 12 12:19:35 UTC 2015 (Ubuntu 3.16.0-33.44-generic 3.16.7-ckt7)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.16.0-33-generic.efi.signed root=/dev/mapper/ubuntu--vg-root ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009dfff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009e000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000020200000-0x0000000040003fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000040004000-0x0000000040004fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000040005000-0x00000000c971bfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000c971c000-0x00000000c9d1cfff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000c9d1d000-0x00000000c9d1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000c9d20000-0x00000000c9d36fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000c9d37000-0x00000000c9d3cfff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000c9d3d000-0x00000000c9d3efff] usable
[    0.000000] BIOS-e820: [mem 0x00000000c9d3f000-0x00000000c9d48fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000c9d49000-0x00000000c9edafff] usable
[    0.000000] BIOS-e820: [mem 0x00000000c9edb000-0x00000000c9edefff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000c9edf000-0x00000000c9f27fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000c9f28000-0x00000000c9f4efff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000c9f4f000-0x00000000c9f65fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000c9f66000-0x00000000c9f6bfff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000c9f6c000-0x00000000c9f73fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000c9f74000-0x00000000c9f74fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000c9f75000-0x00000000c9f83fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000c9f84000-0x00000000c9f84fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000c9f85000-0x00000000c9f8ffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000c9f90000-0x00000000c9f94fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000c9f95000-0x00000000c9fc8fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000c9fc9000-0x00000000c9fc9fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000c9fca000-0x00000000c9fd9fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000c9fda000-0x00000000ca000fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ca001000-0x00000000ca015fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000ca016000-0x00000000ca016fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ca017000-0x00000000ca017fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000ca018000-0x00000000ca019fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ca01a000-0x00000000ca01afff] usable
[    0.000000] BIOS-e820: [mem 0x00000000ca01b000-0x00000000ca01ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ca020000-0x00000000ca036fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000ca037000-0x00000000ca5fbfff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ca5fc000-0x00000000ca87bfff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000ca87c000-0x00000000ca880fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000ca881000-0x00000000ca881fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000ca882000-0x00000000ca8c4fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000ca8c5000-0x00000000cacd7fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cacd8000-0x00000000caff3fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000caff4000-0x00000000caffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cbc00000-0x00000000cfdfffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000032f1fffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] e820: update [mem 0xc8119018-0xc8128657] usable ==> usable
[    0.000000] extended physical RAM map:
[    0.000000] reserve setup_data: [mem 0x0000000000000000-0x000000000009dfff] usable
[    0.000000] reserve setup_data: [mem 0x000000000009e000-0x000000000009ffff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000000100000-0x000000001fffffff] usable
[    0.000000] reserve setup_data: [mem 0x0000000020000000-0x00000000201fffff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000020200000-0x0000000040003fff] usable
[    0.000000] reserve setup_data: [mem 0x0000000040004000-0x0000000040004fff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000040005000-0x00000000c8119017] usable
[    0.000000] reserve setup_data: [mem 0x00000000c8119018-0x00000000c8128657] usable
[    0.000000] reserve setup_data: [mem 0x00000000c8128658-0x00000000c971bfff] usable
[    0.000000] reserve setup_data: [mem 0x00000000c971c000-0x00000000c9d1cfff] ACPI NVS
[    0.000000] reserve setup_data: [mem 0x00000000c9d1d000-0x00000000c9d1ffff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000c9d20000-0x00000000c9d36fff] usable
[    0.000000] reserve setup_data: [mem 0x00000000c9d37000-0x00000000c9d3cfff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000c9d3d000-0x00000000c9d3efff] usable
[    0.000000] reserve setup_data: [mem 0x00000000c9d3f000-0x00000000c9d48fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000c9d49000-0x00000000c9edafff] usable
[    0.000000] reserve setup_data: [mem 0x00000000c9edb000-0x00000000c9edefff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000c9edf000-0x00000000c9f27fff] usable
[    0.000000] reserve setup_data: [mem 0x00000000c9f28000-0x00000000c9f4efff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000c9f4f000-0x00000000c9f65fff] usable
[    0.000000] reserve setup_data: [mem 0x00000000c9f66000-0x00000000c9f6bfff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000c9f6c000-0x00000000c9f73fff] usable
[    0.000000] reserve setup_data: [mem 0x00000000c9f74000-0x00000000c9f74fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000c9f75000-0x00000000c9f83fff] usable
[    0.000000] reserve setup_data: [mem 0x00000000c9f84000-0x00000000c9f84fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000c9f85000-0x00000000c9f8ffff] usable
[    0.000000] reserve setup_data: [mem 0x00000000c9f90000-0x00000000c9f94fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000c9f95000-0x00000000c9fc8fff] usable
[    0.000000] reserve setup_data: [mem 0x00000000c9fc9000-0x00000000c9fc9fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000c9fca000-0x00000000c9fd9fff] usable
[    0.000000] reserve setup_data: [mem 0x00000000c9fda000-0x00000000ca000fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000ca001000-0x00000000ca015fff] usable
[    0.000000] reserve setup_data: [mem 0x00000000ca016000-0x00000000ca016fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000ca017000-0x00000000ca017fff] usable
[    0.000000] reserve setup_data: [mem 0x00000000ca018000-0x00000000ca019fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000ca01a000-0x00000000ca01afff] usable
[    0.000000] reserve setup_data: [mem 0x00000000ca01b000-0x00000000ca01ffff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000ca020000-0x00000000ca036fff] usable
[    0.000000] reserve setup_data: [mem 0x00000000ca037000-0x00000000ca5fbfff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000ca5fc000-0x00000000ca87bfff] ACPI NVS
[    0.000000] reserve setup_data: [mem 0x00000000ca87c000-0x00000000ca880fff] ACPI data
[    0.000000] reserve setup_data: [mem 0x00000000ca881000-0x00000000ca881fff] usable
[    0.000000] reserve setup_data: [mem 0x00000000ca882000-0x00000000ca8c4fff] ACPI NVS
[    0.000000] reserve setup_data: [mem 0x00000000ca8c5000-0x00000000cacd7fff] usable
[    0.000000] reserve setup_data: [mem 0x00000000cacd8000-0x00000000caff3fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000caff4000-0x00000000caffffff] usable
[    0.000000] reserve setup_data: [mem 0x00000000cbc00000-0x00000000cfdfffff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000100000000-0x000000032f1fffff] usable
[    0.000000] efi: EFI v2.31 by American Megatrends
[    0.000000] efi:  ACPI=0xca84e000  ACPI 2.0=0xca84e000  SMBIOS=0xca0fa398 
[    0.000000] efi: mem00: type=7, attr=0xf, range=[0x0000000000000000-0x0000000000001000) (0MB)
[    0.000000] efi: mem01: type=2, attr=0xf, range=[0x0000000000001000-0x0000000000002000) (0MB)
[    0.000000] efi: mem02: type=7, attr=0xf, range=[0x0000000000002000-0x000000000005f000) (0MB)
[    0.000000] efi: mem03: type=4, attr=0xf, range=[0x000000000005f000-0x0000000000060000) (0MB)
[    0.000000] efi: mem04: type=7, attr=0xf, range=[0x0000000000060000-0x000000000009e000) (0MB)
[    0.000000] efi: mem05: type=0, attr=0xf, range=[0x000000000009e000-0x00000000000a0000) (0MB)
[    0.000000] efi: mem06: type=7, attr=0xf, range=[0x0000000000100000-0x0000000001000000) (15MB)
[    0.000000] efi: mem07: type=2, attr=0xf, range=[0x0000000001000000-0x0000000001100000) (1MB)
[    0.000000] efi: mem08: type=7, attr=0xf, range=[0x0000000001100000-0x0000000002000000) (15MB)
[    0.000000] efi: mem09: type=2, attr=0xf, range=[0x0000000002000000-0x00000000033f6000) (19MB)
[    0.000000] efi: mem10: type=7, attr=0xf, range=[0x00000000033f6000-0x0000000020000000) (460MB)
[    0.000000] efi: mem11: type=0, attr=0xf, range=[0x0000000020000000-0x0000000020200000) (2MB)
[    0.000000] efi: mem12: type=7, attr=0xf, range=[0x0000000020200000-0x000000003d7c9000) (469MB)
[    0.000000] efi: mem13: type=2, attr=0xf, range=[0x000000003d7c9000-0x0000000040000000) (40MB)
[    0.000000] efi: mem14: type=7, attr=0xf, range=[0x0000000040000000-0x0000000040004000) (0MB)
[    0.000000] efi: mem15: type=0, attr=0xf, range=[0x0000000040004000-0x0000000040005000) (0MB)
[    0.000000] efi: mem16: type=7, attr=0xf, range=[0x0000000040005000-0x0000000095e91000) (1374MB)
[    0.000000] efi: mem17: type=2, attr=0xf, range=[0x0000000095e91000-0x00000000c7fe1000) (801MB)
[    0.000000] efi: mem18: type=1, attr=0xf, range=[0x00000000c7fe1000-0x00000000c8104000) (1MB)
[    0.000000] efi: mem19: type=7, attr=0xf, range=[0x00000000c8104000-0x00000000c8119000) (0MB)
[    0.000000] efi: mem20: type=2, attr=0xf, range=[0x00000000c8119000-0x00000000c812a000) (0MB)
[    0.000000] efi: mem21: type=7, attr=0xf, range=[0x00000000c812a000-0x00000000c812d000) (0MB)
[    0.000000] efi: mem22: type=2, attr=0xf, range=[0x00000000c812d000-0x00000000c8132000) (0MB)
[    0.000000] efi: mem23: type=7, attr=0xf, range=[0x00000000c8132000-0x00000000c8133000) (0MB)
[    0.000000] efi: mem24: type=2, attr=0xf, range=[0x00000000c8133000-0x00000000c8134000) (0MB)
[    0.000000] efi: mem25: type=7, attr=0xf, range=[0x00000000c8134000-0x00000000c8139000) (0MB)
[    0.000000] efi: mem26: type=2, attr=0xf, range=[0x00000000c8139000-0x00000000c8223000) (0MB)
[    0.000000] efi: mem27: type=4, attr=0xf, range=[0x00000000c8223000-0x00000000c8296000) (0MB)
[    0.000000] efi: mem28: type=7, attr=0xf, range=[0x00000000c8296000-0x00000000c8297000) (0MB)
[    0.000000] efi: mem29: type=2, attr=0xf, range=[0x00000000c8297000-0x00000000c8299000) (0MB)
[    0.000000] efi: mem30: type=7, attr=0xf, range=[0x00000000c8299000-0x00000000c829a000) (0MB)
[    0.000000] efi: mem31: type=2, attr=0xf, range=[0x00000000c829a000-0x00000000c829f000) (0MB)
[    0.000000] efi: mem32: type=4, attr=0xf, range=[0x00000000c829f000-0x00000000c82b9000) (0MB)
[    0.000000] efi: mem33: type=2, attr=0xf, range=[0x00000000c82b9000-0x00000000c82bb000) (0MB)
[    0.000000] efi: mem34: type=7, attr=0xf, range=[0x00000000c82bb000-0x00000000c82bc000) (0MB)
[    0.000000] efi: mem35: type=4, attr=0xf, range=[0x00000000c82bc000-0x00000000c8398000) (0MB)
[    0.000000] efi: mem36: type=2, attr=0xf, range=[0x00000000c8398000-0x00000000c839a000) (0MB)
[    0.000000] efi: mem37: type=4, attr=0xf, range=[0x00000000c839a000-0x00000000c9098000) (12MB)
[    0.000000] efi: mem38: type=7, attr=0xf, range=[0x00000000c9098000-0x00000000c970f000) (6MB)
[    0.000000] efi: mem39: type=3, attr=0xf, range=[0x00000000c970f000-0x00000000c971c000) (0MB)
[    0.000000] efi: mem40: type=10, attr=0xf, range=[0x00000000c971c000-0x00000000c9d1d000) (6MB)
[    0.000000] efi: mem41: type=5, attr=0x800000000000000f, range=[0x00000000c9d1d000-0x00000000c9d20000) (0MB)
[    0.000000] efi: mem42: type=3, attr=0xf, range=[0x00000000c9d20000-0x00000000c9d37000) (0MB)
[    0.000000] efi: mem43: type=5, attr=0x800000000000000f, range=[0x00000000c9d37000-0x00000000c9d3d000) (0MB)
[    0.000000] efi: mem44: type=3, attr=0xf, range=[0x00000000c9d3d000-0x00000000c9d3f000) (0MB)
[    0.000000] efi: mem45: type=5, attr=0x800000000000000f, range=[0x00000000c9d3f000-0x00000000c9d49000) (0MB)
[    0.000000] efi: mem46: type=3, attr=0xf, range=[0x00000000c9d49000-0x00000000c9edb000) (1MB)
[    0.000000] efi: mem47: type=5, attr=0x800000000000000f, range=[0x00000000c9edb000-0x00000000c9edf000) (0MB)
[    0.000000] efi: mem48: type=3, attr=0xf, range=[0x00000000c9edf000-0x00000000c9f28000) (0MB)
[    0.000000] efi: mem49: type=5, attr=0x800000000000000f, range=[0x00000000c9f28000-0x00000000c9f2f000) (0MB)
[    0.000000] efi: mem50: type=6, attr=0x800000000000000f, range=[0x00000000c9f2f000-0x00000000c9f3c000) (0MB)
[    0.000000] efi: mem51: type=5, attr=0x800000000000000f, range=[0x00000000c9f3c000-0x00000000c9f4f000) (0MB)
[    0.000000] efi: mem52: type=3, attr=0xf, range=[0x00000000c9f4f000-0x00000000c9f66000) (0MB)
[    0.000000] efi: mem53: type=5, attr=0x800000000000000f, range=[0x00000000c9f66000-0x00000000c9f6c000) (0MB)
[    0.000000] efi: mem54: type=3, attr=0xf, range=[0x00000000c9f6c000-0x00000000c9f74000) (0MB)
[    0.000000] efi: mem55: type=5, attr=0x800000000000000f, range=[0x00000000c9f74000-0x00000000c9f75000) (0MB)
[    0.000000] efi: mem56: type=3, attr=0xf, range=[0x00000000c9f75000-0x00000000c9f84000) (0MB)
[    0.000000] efi: mem57: type=5, attr=0x800000000000000f, range=[0x00000000c9f84000-0x00000000c9f85000) (0MB)
[    0.000000] efi: mem58: type=3, attr=0xf, range=[0x00000000c9f85000-0x00000000c9f90000) (0MB)
[    0.000000] efi: mem59: type=5, attr=0x800000000000000f, range=[0x00000000c9f90000-0x00000000c9f95000) (0MB)
[    0.000000] efi: mem60: type=3, attr=0xf, range=[0x00000000c9f95000-0x00000000c9fc9000) (0MB)
[    0.000000] efi: mem61: type=5, attr=0x800000000000000f, range=[0x00000000c9fc9000-0x00000000c9fca000) (0MB)
[    0.000000] efi: mem62: type=3, attr=0xf, range=[0x00000000c9fca000-0x00000000c9fda000) (0MB)
[    0.000000] efi: mem63: type=5, attr=0x800000000000000f, range=[0x00000000c9fda000-0x00000000ca001000) (0MB)
[    0.000000] efi: mem64: type=3, attr=0xf, range=[0x00000000ca001000-0x00000000ca016000) (0MB)
[    0.000000] efi: mem65: type=5, attr=0x800000000000000f, range=[0x00000000ca016000-0x00000000ca017000) (0MB)
[    0.000000] efi: mem66: type=3, attr=0xf, range=[0x00000000ca017000-0x00000000ca018000) (0MB)
[    0.000000] efi: mem67: type=5, attr=0x800000000000000f, range=[0x00000000ca018000-0x00000000ca01a000) (0MB)
[    0.000000] efi: mem68: type=3, attr=0xf, range=[0x00000000ca01a000-0x00000000ca01b000) (0MB)
[    0.000000] efi: mem69: type=5, attr=0x800000000000000f, range=[0x00000000ca01b000-0x00000000ca020000) (0MB)
[    0.000000] efi: mem70: type=3, attr=0xf, range=[0x00000000ca020000-0x00000000ca037000) (0MB)
[    0.000000] efi: mem71: type=6, attr=0x800000000000000f, range=[0x00000000ca037000-0x00000000ca0b8000) (0MB)
[    0.000000] efi: mem72: type=5, attr=0x800000000000000f, range=[0x00000000ca0b8000-0x00000000ca0d2000) (0MB)
[    0.000000] efi: mem73: type=6, attr=0x800000000000000f, range=[0x00000000ca0d2000-0x00000000ca0d8000) (0MB)
[    0.000000] efi: mem74: type=6, attr=0x800000000000000f, range=[0x00000000ca0d8000-0x00000000ca0fc000) (0MB)
[    0.000000] efi: mem75: type=0, attr=0xf, range=[0x00000000ca0fc000-0x00000000ca573000) (4MB)
[    0.000000] efi: mem76: type=0, attr=0xf, range=[0x00000000ca573000-0x00000000ca591000) (0MB)
[    0.000000] efi: mem77: type=0, attr=0xf, range=[0x00000000ca591000-0x00000000ca5a0000) (0MB)
[    0.000000] efi: mem78: type=0, attr=0xf, range=[0x00000000ca5a0000-0x00000000ca5a2000) (0MB)
[    0.000000] efi: mem79: type=0, attr=0xf, range=[0x00000000ca5a2000-0x00000000ca5ac000) (0MB)
[    0.000000] efi: mem80: type=0, attr=0xf, range=[0x00000000ca5ac000-0x00000000ca5fc000) (0MB)
[    0.000000] efi: mem81: type=10, attr=0xf, range=[0x00000000ca5fc000-0x00000000ca6b9000) (0MB)
[    0.000000] efi: mem82: type=10, attr=0xf, range=[0x00000000ca6b9000-0x00000000ca865000) (1MB)
[    0.000000] efi: mem83: type=10, attr=0xf, range=[0x00000000ca865000-0x00000000ca866000) (0MB)
[    0.000000] efi: mem84: type=10, attr=0xf, range=[0x00000000ca866000-0x00000000ca87c000) (0MB)
[    0.000000] efi: mem85: type=9, attr=0xf, range=[0x00000000ca87c000-0x00000000ca881000) (0MB)
[    0.000000] efi: mem86: type=4, attr=0xf, range=[0x00000000ca881000-0x00000000ca882000) (0MB)
[    0.000000] efi: mem87: type=10, attr=0xf, range=[0x00000000ca882000-0x00000000ca8c5000) (0MB)
[    0.000000] efi: mem88: type=4, attr=0xf, range=[0x00000000ca8c5000-0x00000000caa11000) (1MB)
[    0.000000] efi: mem89: type=3, attr=0xf, range=[0x00000000caa11000-0x00000000caca9000) (2MB)
[    0.000000] efi: mem90: type=4, attr=0xf, range=[0x00000000caca9000-0x00000000cacae000) (0MB)
[    0.000000] efi: mem91: type=3, attr=0xf, range=[0x00000000cacae000-0x00000000cacb2000) (0MB)
[    0.000000] efi: mem92: type=4, attr=0xf, range=[0x00000000cacb2000-0x00000000cacbf000) (0MB)
[    0.000000] efi: mem93: type=3, attr=0xf, range=[0x00000000cacbf000-0x00000000cacd1000) (0MB)
[    0.000000] efi: mem94: type=4, attr=0xf, range=[0x00000000cacd1000-0x00000000cacd8000) (0MB)
[    0.000000] efi: mem95: type=6, attr=0x800000000000000f, range=[0x00000000cacd8000-0x00000000caff4000) (3MB)
[    0.000000] efi: mem96: type=4, attr=0xf, range=[0x00000000caff4000-0x00000000cb000000) (0MB)
[    0.000000] efi: mem97: type=7, attr=0xf, range=[0x0000000100000000-0x000000032f200000) (8946MB)
[    0.000000] efi: mem98: type=0, attr=0x8000000000000000, range=[0x00000000cbc00000-0x00000000cfe00000) (66MB)
[    0.000000] efi: mem99: type=11, attr=0x8000000000000001, range=[0x00000000f8000000-0x00000000fc000000) (64MB)
[    0.000000] efi: mem100: type=11, attr=0x8000000000000001, range=[0x00000000fec00000-0x00000000fec01000) (0MB)
[    0.000000] efi: mem101: type=11, attr=0x8000000000000001, range=[0x00000000fed00000-0x00000000fed04000) (0MB)
[    0.000000] efi: mem102: type=11, attr=0x8000000000000001, range=[0x00000000fed1c000-0x00000000fed20000) (0MB)
[    0.000000] efi: mem103: type=11, attr=0x8000000000000001, range=[0x00000000fee00000-0x00000000fee01000) (0MB)
[    0.000000] efi: mem104: type=11, attr=0x8000000000000001, range=[0x00000000ff000000-0x0000000100000000) (16MB)
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: ASUSTeK COMPUTER INC. U32VJ/U32VJ, BIOS U32VJ.202 09/27/2012
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] AGP: No AGP bridge found
[    0.000000] e820: last_pfn = 0x32f200 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask E00000000 write-back
[    0.000000]   1 base 200000000 mask F00000000 write-back
[    0.000000]   2 base 300000000 mask FC0000000 write-back
[    0.000000]   3 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   4 base 0D0000000 mask FF0000000 uncachable
[    0.000000]   5 base 0CC000000 mask FFC000000 uncachable
[    0.000000]   6 base 0CBC00000 mask FFFC00000 uncachable
[    0.000000]   7 base 330000000 mask FF0000000 uncachable
[    0.000000]   8 base 32F800000 mask FFF800000 uncachable
[    0.000000]   9 base 32F400000 mask FFFC00000 uncachable
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 8GB, type WB
[    0.000000] reg 1, base: 8GB, range: 4GB, type WB
[    0.000000] reg 2, base: 12GB, range: 1GB, type WB
[    0.000000] reg 3, base: 3584MB, range: 512MB, type UC
[    0.000000] reg 4, base: 3328MB, range: 256MB, type UC
[    0.000000] reg 5, base: 3264MB, range: 64MB, type UC
[    0.000000] reg 6, base: 3260MB, range: 4MB, type UC
[    0.000000] reg 7, base: 13056MB, range: 256MB, type UC
[    0.000000] reg 8, base: 13048MB, range: 8MB, type UC
[    0.000000] reg 9, base: 13044MB, range: 4MB, type UC
[    0.000000] total RAM covered: 12208M
[    0.000000]  gran_size: 64K     chunk_size: 64K     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 64K     chunk_size: 128K     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 64K     chunk_size: 256K     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 64K     chunk_size: 512K     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 64K     chunk_size: 1M     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 64K     chunk_size: 2M     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 64K     chunk_size: 4M     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 64K     chunk_size: 8M     num_reg: 10      lose cover RAM: 52M
[    0.000000] *BAD*gran_size: 64K     chunk_size: 16M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 64K     chunk_size: 32M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 64K     chunk_size: 64M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 64K     chunk_size: 128M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 64K     chunk_size: 256M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 64K     chunk_size: 512M     num_reg: 10      lose cover RAM: -264M
[    0.000000] *BAD*gran_size: 64K     chunk_size: 1G     num_reg: 10      lose cover RAM: -256M
[    0.000000] *BAD*gran_size: 64K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1280M
[    0.000000]  gran_size: 128K     chunk_size: 128K     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 128K     chunk_size: 256K     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 128K     chunk_size: 512K     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 128K     chunk_size: 1M     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 128K     chunk_size: 2M     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 128K     chunk_size: 4M     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 128K     chunk_size: 8M     num_reg: 10      lose cover RAM: 52M
[    0.000000] *BAD*gran_size: 128K     chunk_size: 16M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 128K     chunk_size: 32M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 128K     chunk_size: 64M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 128K     chunk_size: 128M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 128K     chunk_size: 256M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 128K     chunk_size: 512M     num_reg: 10      lose cover RAM: -264M
[    0.000000] *BAD*gran_size: 128K     chunk_size: 1G     num_reg: 10      lose cover RAM: -256M
[    0.000000] *BAD*gran_size: 128K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1280M
[    0.000000]  gran_size: 256K     chunk_size: 256K     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 256K     chunk_size: 512K     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 256K     chunk_size: 1M     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 256K     chunk_size: 2M     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 256K     chunk_size: 4M     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 256K     chunk_size: 8M     num_reg: 10      lose cover RAM: 52M
[    0.000000] *BAD*gran_size: 256K     chunk_size: 16M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 256K     chunk_size: 32M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 256K     chunk_size: 64M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 256K     chunk_size: 128M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 256K     chunk_size: 256M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 256K     chunk_size: 512M     num_reg: 10      lose cover RAM: -264M
[    0.000000] *BAD*gran_size: 256K     chunk_size: 1G     num_reg: 10      lose cover RAM: -256M
[    0.000000] *BAD*gran_size: 256K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1280M
[    0.000000]  gran_size: 512K     chunk_size: 512K     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 512K     chunk_size: 1M     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 512K     chunk_size: 2M     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 512K     chunk_size: 4M     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 512K     chunk_size: 8M     num_reg: 10      lose cover RAM: 52M
[    0.000000] *BAD*gran_size: 512K     chunk_size: 16M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 512K     chunk_size: 32M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 512K     chunk_size: 64M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 512K     chunk_size: 128M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 512K     chunk_size: 256M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 512K     chunk_size: 512M     num_reg: 10      lose cover RAM: -264M
[    0.000000] *BAD*gran_size: 512K     chunk_size: 1G     num_reg: 10      lose cover RAM: -256M
[    0.000000] *BAD*gran_size: 512K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1280M
[    0.000000]  gran_size: 1M     chunk_size: 1M     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 1M     chunk_size: 2M     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 1M     chunk_size: 4M     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 1M     chunk_size: 8M     num_reg: 10      lose cover RAM: 52M
[    0.000000] *BAD*gran_size: 1M     chunk_size: 16M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 1M     chunk_size: 32M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 1M     chunk_size: 64M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 1M     chunk_size: 128M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 1M     chunk_size: 256M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 1M     chunk_size: 512M     num_reg: 10      lose cover RAM: -264M
[    0.000000] *BAD*gran_size: 1M     chunk_size: 1G     num_reg: 10      lose cover RAM: -256M
[    0.000000] *BAD*gran_size: 1M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1280M
[    0.000000]  gran_size: 2M     chunk_size: 2M     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 2M     chunk_size: 4M     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 2M     chunk_size: 8M     num_reg: 10      lose cover RAM: 52M
[    0.000000] *BAD*gran_size: 2M     chunk_size: 16M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 2M     chunk_size: 32M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 2M     chunk_size: 64M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 2M     chunk_size: 128M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 2M     chunk_size: 256M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 2M     chunk_size: 512M     num_reg: 10      lose cover RAM: -264M
[    0.000000] *BAD*gran_size: 2M     chunk_size: 1G     num_reg: 10      lose cover RAM: -256M
[    0.000000] *BAD*gran_size: 2M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1280M
[    0.000000]  gran_size: 4M     chunk_size: 4M     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 4M     chunk_size: 8M     num_reg: 10      lose cover RAM: 52M
[    0.000000] *BAD*gran_size: 4M     chunk_size: 16M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 4M     chunk_size: 32M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 4M     chunk_size: 64M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 4M     chunk_size: 128M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 4M     chunk_size: 256M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 4M     chunk_size: 512M     num_reg: 10      lose cover RAM: -264M
[    0.000000] *BAD*gran_size: 4M     chunk_size: 1G     num_reg: 10      lose cover RAM: -256M
[    0.000000] *BAD*gran_size: 4M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1280M
[    0.000000]  gran_size: 8M     chunk_size: 8M     num_reg: 10      lose cover RAM: 120M
[    0.000000]  gran_size: 8M     chunk_size: 16M     num_reg: 10      lose cover RAM: 56M
[    0.000000]  gran_size: 8M     chunk_size: 32M     num_reg: 10      lose cover RAM: 8M
[    0.000000]  gran_size: 8M     chunk_size: 64M     num_reg: 10      lose cover RAM: 8M
[    0.000000]  gran_size: 8M     chunk_size: 128M     num_reg: 10      lose cover RAM: 8M
[    0.000000]  gran_size: 8M     chunk_size: 256M     num_reg: 10      lose cover RAM: 8M
[    0.000000] *BAD*gran_size: 8M     chunk_size: 512M     num_reg: 10      lose cover RAM: -248M
[    0.000000]  gran_size: 8M     chunk_size: 1G     num_reg: 10      lose cover RAM: 8M
[    0.000000] *BAD*gran_size: 8M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1016M
[    0.000000]  gran_size: 16M     chunk_size: 16M     num_reg: 10      lose cover RAM: 64M
[    0.000000]  gran_size: 16M     chunk_size: 32M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 16M     chunk_size: 64M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 16M     chunk_size: 128M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 16M     chunk_size: 256M     num_reg: 10      lose cover RAM: 16M
[    0.000000] *BAD*gran_size: 16M     chunk_size: 512M     num_reg: 10      lose cover RAM: -240M
[    0.000000]  gran_size: 16M     chunk_size: 1G     num_reg: 10      lose cover RAM: 16M
[    0.000000] *BAD*gran_size: 16M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1008M
[    0.000000]  gran_size: 32M     chunk_size: 32M     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 32M     chunk_size: 64M     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 32M     chunk_size: 128M     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 32M     chunk_size: 256M     num_reg: 10      lose cover RAM: 48M
[    0.000000] *BAD*gran_size: 32M     chunk_size: 512M     num_reg: 10      lose cover RAM: -208M
[    0.000000]  gran_size: 32M     chunk_size: 1G     num_reg: 10      lose cover RAM: 48M
[    0.000000] *BAD*gran_size: 32M     chunk_size: 2G     num_reg: 10      lose cover RAM: -976M
[    0.000000]  gran_size: 64M     chunk_size: 64M     num_reg: 8      lose cover RAM: 112M
[    0.000000]  gran_size: 64M     chunk_size: 128M     num_reg: 8      lose cover RAM: 112M
[    0.000000]  gran_size: 64M     chunk_size: 256M     num_reg: 9      lose cover RAM: 112M
[    0.000000]  gran_size: 64M     chunk_size: 512M     num_reg: 10      lose cover RAM: 112M
[    0.000000]  gran_size: 64M     chunk_size: 1G     num_reg: 9      lose cover RAM: 112M
[    0.000000]  gran_size: 64M     chunk_size: 2G     num_reg: 10      lose cover RAM: 112M
[    0.000000]  gran_size: 128M     chunk_size: 128M     num_reg: 7      lose cover RAM: 176M
[    0.000000]  gran_size: 128M     chunk_size: 256M     num_reg: 9      lose cover RAM: 176M
[    0.000000]  gran_size: 128M     chunk_size: 512M     num_reg: 10      lose cover RAM: 176M
[    0.000000]  gran_size: 128M     chunk_size: 1G     num_reg: 9      lose cover RAM: 176M
[    0.000000]  gran_size: 128M     chunk_size: 2G     num_reg: 10      lose cover RAM: 176M
[    0.000000]  gran_size: 256M     chunk_size: 256M     num_reg: 5      lose cover RAM: 432M
[    0.000000]  gran_size: 256M     chunk_size: 512M     num_reg: 5      lose cover RAM: 432M
[    0.000000]  gran_size: 256M     chunk_size: 1G     num_reg: 6      lose cover RAM: 432M
[    0.000000]  gran_size: 256M     chunk_size: 2G     num_reg: 7      lose cover RAM: 432M
[    0.000000]  gran_size: 512M     chunk_size: 512M     num_reg: 5      lose cover RAM: 432M
[    0.000000]  gran_size: 512M     chunk_size: 1G     num_reg: 6      lose cover RAM: 432M
[    0.000000]  gran_size: 512M     chunk_size: 2G     num_reg: 7      lose cover RAM: 432M
[    0.000000]  gran_size: 1G     chunk_size: 1G     num_reg: 4      lose cover RAM: 944M
[    0.000000]  gran_size: 1G     chunk_size: 2G     num_reg: 4      lose cover RAM: 944M
[    0.000000]  gran_size: 2G     chunk_size: 2G     num_reg: 3      lose cover RAM: 1968M
[    0.000000] mtrr_cleanup: can not find optimal value
[    0.000000] please specify mtrr_gran_size/mtrr_chunk_size
[    0.000000] e820: update [mem 0xcbc00000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xcb000 max_arch_pfn = 0x400000000
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x02fd2000, 0x02fd2fff] PGTABLE
[    0.000000] BRK [0x02fd3000, 0x02fd3fff] PGTABLE
[    0.000000] BRK [0x02fd4000, 0x02fd4fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x32f000000-0x32f1fffff]
[    0.000000]  [mem 0x32f000000-0x32f1fffff] page 2M
[    0.000000] BRK [0x02fd5000, 0x02fd5fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x32c000000-0x32effffff]
[    0.000000]  [mem 0x32c000000-0x32effffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x300000000-0x32bffffff]
[    0.000000]  [mem 0x300000000-0x32bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x1fffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x1fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x20200000-0x40003fff]
[    0.000000]  [mem 0x20200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0x40003fff] page 4k
[    0.000000] BRK [0x02fd6000, 0x02fd6fff] PGTABLE
[    0.000000] BRK [0x02fd7000, 0x02fd7fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x40005000-0xc971bfff]
[    0.000000]  [mem 0x40005000-0x401fffff] page 4k
[    0.000000]  [mem 0x40200000-0xc95fffff] page 2M
[    0.000000]  [mem 0xc9600000-0xc971bfff] page 4k
[    0.000000] init_memory_mapping: [mem 0xc9d20000-0xc9d36fff]
[    0.000000]  [mem 0xc9d20000-0xc9d36fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xc9d3d000-0xc9d3efff]
[    0.000000]  [mem 0xc9d3d000-0xc9d3efff] page 4k
[    0.000000] init_memory_mapping: [mem 0xc9d49000-0xc9edafff]
[    0.000000]  [mem 0xc9d49000-0xc9edafff] page 4k
[    0.000000] init_memory_mapping: [mem 0xc9edf000-0xc9f27fff]
[    0.000000]  [mem 0xc9edf000-0xc9f27fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xc9f4f000-0xc9f65fff]
[    0.000000]  [mem 0xc9f4f000-0xc9f65fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xc9f6c000-0xc9f73fff]
[    0.000000]  [mem 0xc9f6c000-0xc9f73fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xc9f75000-0xc9f83fff]
[    0.000000]  [mem 0xc9f75000-0xc9f83fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xc9f85000-0xc9f8ffff]
[    0.000000]  [mem 0xc9f85000-0xc9f8ffff] page 4k
[    0.000000] init_memory_mapping: [mem 0xc9f95000-0xc9fc8fff]
[    0.000000]  [mem 0xc9f95000-0xc9fc8fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xc9fca000-0xc9fd9fff]
[    0.000000]  [mem 0xc9fca000-0xc9fd9fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xca001000-0xca015fff]
[    0.000000]  [mem 0xca001000-0xca015fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xca017000-0xca017fff]
[    0.000000]  [mem 0xca017000-0xca017fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xca01a000-0xca01afff]
[    0.000000]  [mem 0xca01a000-0xca01afff] page 4k
[    0.000000] init_memory_mapping: [mem 0xca020000-0xca036fff]
[    0.000000]  [mem 0xca020000-0xca036fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xca881000-0xca881fff]
[    0.000000]  [mem 0xca881000-0xca881fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xca8c5000-0xcacd7fff]
[    0.000000]  [mem 0xca8c5000-0xca9fffff] page 4k
[    0.000000]  [mem 0xcaa00000-0xcabfffff] page 2M
[    0.000000]  [mem 0xcac00000-0xcacd7fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xcaff4000-0xcaffffff]
[    0.000000]  [mem 0xcaff4000-0xcaffffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x2ffffffff]
[    0.000000]  [mem 0x100000000-0x2ffffffff] page 2M
[    0.000000] RAMDISK: [mem 0x3d7c9000-0x3ec04fff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000CA84E000 000024 (v02 _ASUS_)
[    0.000000] ACPI: XSDT 0x00000000CA84E080 000084 (v01 _ASUS_ Notebook 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 0x00000000CA861A20 00010C (v05 _ASUS_ Notebook 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 0x00000000CA84E190 01388E (v02 _ASUS_ Notebook 00000013 INTL 20091112)
[    0.000000] ACPI: FACS 0x00000000CA879080 000040
[    0.000000] ACPI: APIC 0x00000000CA861B30 000072 (v03 _ASUS_ Notebook 01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 0x00000000CA861BA8 000044 (v01 _ASUS_ Notebook 01072009 AMI  00010013)
[    0.000000] ACPI: ECDT 0x00000000CA861BF0 0000C1 (v01 _ASUS_ Notebook 01072009 AMI. 00000005)
[    0.000000] ACPI: MCFG 0x00000000CA861CB8 00003C (v01 _ASUS_ Notebook 01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 0x00000000CA861CF8 000038 (v01 _ASUS_ Notebook 01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT 0x00000000CA861D30 0004EE (v01 IdeRe1 IdeTabl1 00001000 INTL 20091112)
[    0.000000] ACPI: SSDT 0x00000000CA862220 00052E (v01 IdeRe2 IdeTabl2 00001000 INTL 20091112)
[    0.000000] ACPI: SSDT 0x00000000CA862750 00098E (v01 PmRef  Cpu0Ist  00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 0x00000000CA8630E0 000B18 (v01 PmRef  CpuPm    00003000 INTL 20051117)
[    0.000000] ACPI: BGRT 0x00000000CA863BF8 000038 (v00 _ASUS_ Notebook 01072009 ASUS 00010013)
[    0.000000] ACPI: MSDM 0x00000000CA5FBE18 000055 (v03 _ASUS_ Notebook 00000000 ASUS 00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000032f1fffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x32f1fffff]
[    0.000000]   NODE_DATA [mem 0x32f1ea000-0x32f1eefff]
[    0.000000]  [ffffea0000000000-ffffea000cbfffff] PMD -> [ffff880322800000-ffff88032e7fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x32f1fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009dfff]
[    0.000000]   node   0: [mem 0x00100000-0x1fffffff]
[    0.000000]   node   0: [mem 0x20200000-0x40003fff]
[    0.000000]   node   0: [mem 0x40005000-0xc971bfff]
[    0.000000]   node   0: [mem 0xc9d20000-0xc9d36fff]
[    0.000000]   node   0: [mem 0xc9d3d000-0xc9d3efff]
[    0.000000]   node   0: [mem 0xc9d49000-0xc9edafff]
[    0.000000]   node   0: [mem 0xc9edf000-0xc9f27fff]
[    0.000000]   node   0: [mem 0xc9f4f000-0xc9f65fff]
[    0.000000]   node   0: [mem 0xc9f6c000-0xc9f73fff]
[    0.000000]   node   0: [mem 0xc9f75000-0xc9f83fff]
[    0.000000]   node   0: [mem 0xc9f85000-0xc9f8ffff]
[    0.000000]   node   0: [mem 0xc9f95000-0xc9fc8fff]
[    0.000000]   node   0: [mem 0xc9fca000-0xc9fd9fff]
[    0.000000]   node   0: [mem 0xca001000-0xca015fff]
[    0.000000]   node   0: [mem 0xca017000-0xca017fff]
[    0.000000]   node   0: [mem 0xca01a000-0xca01afff]
[    0.000000]   node   0: [mem 0xca020000-0xca036fff]
[    0.000000]   node   0: [mem 0xca881000-0xca881fff]
[    0.000000]   node   0: [mem 0xca8c5000-0xcacd7fff]
[    0.000000]   node   0: [mem 0xcaff4000-0xcaffffff]
[    0.000000]   node   0: [mem 0x100000000-0x32f1fffff]
[    0.000000] On node 0 totalpages: 3116407
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 22 pages reserved
[    0.000000]   DMA zone: 3997 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 12848 pages used for memmap
[    0.000000]   DMA32 zone: 822234 pages, LIFO batch:31
[    0.000000]   Normal zone: 35784 pages used for memmap
[    0.000000]   Normal zone: 2290176 pages, LIFO batch:31
[    0.000000] tboot: non-0 tboot_addr but it is not of type E820_RESERVED
[    0.000000] Reserving Intel graphics stolen memory at 0xcbe00000-0xcfdfffff
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
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
[    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x20000000-0x201fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x40004000-0x40004fff]
[    0.000000] PM: Registered nosave memory: [mem 0xc8119000-0xc8119fff]
[    0.000000] PM: Registered nosave memory: [mem 0xc8128000-0xc8128fff]
[    0.000000] PM: Registered nosave memory: [mem 0xc971c000-0xc9d1cfff]
[    0.000000] PM: Registered nosave memory: [mem 0xc9d1d000-0xc9d1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xc9d37000-0xc9d3cfff]
[    0.000000] PM: Registered nosave memory: [mem 0xc9d3f000-0xc9d48fff]
[    0.000000] PM: Registered nosave memory: [mem 0xc9edb000-0xc9edefff]
[    0.000000] PM: Registered nosave memory: [mem 0xc9f28000-0xc9f4efff]
[    0.000000] PM: Registered nosave memory: [mem 0xc9f66000-0xc9f6bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xc9f74000-0xc9f74fff]
[    0.000000] PM: Registered nosave memory: [mem 0xc9f84000-0xc9f84fff]
[    0.000000] PM: Registered nosave memory: [mem 0xc9f90000-0xc9f94fff]
[    0.000000] PM: Registered nosave memory: [mem 0xc9fc9000-0xc9fc9fff]
[    0.000000] PM: Registered nosave memory: [mem 0xc9fda000-0xca000fff]
[    0.000000] PM: Registered nosave memory: [mem 0xca016000-0xca016fff]
[    0.000000] PM: Registered nosave memory: [mem 0xca018000-0xca019fff]
[    0.000000] PM: Registered nosave memory: [mem 0xca01b000-0xca01ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xca037000-0xca5fbfff]
[    0.000000] PM: Registered nosave memory: [mem 0xca5fc000-0xca87bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xca87c000-0xca880fff]
[    0.000000] PM: Registered nosave memory: [mem 0xca882000-0xca8c4fff]
[    0.000000] PM: Registered nosave memory: [mem 0xcacd8000-0xcaff3fff]
[    0.000000] PM: Registered nosave memory: [mem 0xcb000000-0xcbbfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xcbc00000-0xcfdfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xcfe00000-0xf7ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfecfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed03fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed04000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0xcfe00000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88032ee00000 s82432 r8192 d24064 u524288
[    0.000000] pcpu-alloc: s82432 r8192 d24064 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 3067689
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.16.0-33-generic.efi.signed root=/dev/mapper/ubuntu--vg-root ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] AGP: Checking aperture...
[    0.000000] AGP: No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 12143356K/12465628K available (7745K kernel code, 1197K rwdata, 3612K rodata, 1360K init, 1308K bss, 322272K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-3.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=4
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 50331648 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 2494.463 MHz processor
[    0.000033] Calibrating delay loop (skipped), value calculated using timer frequency.. 4988.92 BogoMIPS (lpj=9977852)
[    0.000036] pid_max: default: 32768 minimum: 301
[    0.000042] ACPI: Core revision 20140424
[    0.013883] ACPI: All ACPI Tables successfully acquired
[    0.015484] Security Framework initialized
[    0.015498] AppArmor: AppArmor initialized
[    0.015499] Yama: becoming mindful.
[    0.016448] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.020348] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.022118] Mount-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.022136] Mountpoint-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.022366] Initializing cgroup subsys memory
[    0.022387] Initializing cgroup subsys devices
[    0.022393] Initializing cgroup subsys freezer
[    0.022395] Initializing cgroup subsys net_cls
[    0.022398] Initializing cgroup subsys blkio
[    0.022401] Initializing cgroup subsys perf_event
[    0.022403] Initializing cgroup subsys net_prio
[    0.022409] Initializing cgroup subsys hugetlb
[    0.022430] CPU: Physical Processor ID: 0
[    0.022430] CPU: Processor Core ID: 0
[    0.022435] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.022791] mce: CPU supports 7 MCE banks
[    0.022801] CPU0: Thermal monitoring enabled (TM1)
[    0.022810] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 8
Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32, 1GB 0
tlb_flushall_shift: 2
[    0.022929] Freeing SMP alternatives memory: 32K (ffffffff81e81000 - ffffffff81e89000)
[    0.024735] ftrace: allocating 29327 entries in 115 pages
[    0.038309] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.078041] smpboot: CPU0: Intel(R) Core(TM) i5-3210M CPU @ 2.50GHz (fam: 06, model: 3a, stepping: 09)
[    0.078049] TSC deadline timer enabled
[    0.078071] Performance Events: PEBS fmt1+, 16-deep LBR, IvyBridge events, full-width counters, Intel PMU driver.
[    0.078090] ... version:                3
[    0.078091] ... bit width:              48
[    0.078092] ... generic registers:      4
[    0.078093] ... value mask:             0000ffffffffffff
[    0.078094] ... max period:             0000ffffffffffff
[    0.078094] ... fixed-purpose events:   3
[    0.078095] ... event mask:             000000070000000f
[    0.079749] x86: Booting SMP configuration:
[    0.079751] .... node  #0, CPUs:      #1
[    0.093243] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.093321]  #2 #3
[    0.120325] x86: Booted up 1 node, 4 CPUs
[    0.120328] smpboot: Total of 4 processors activated (19955.70 BogoMIPS)
[    0.123487] devtmpfs: initialized
[    0.126278] evm: security.selinux
[    0.126279] evm: security.SMACK64
[    0.126280] evm: security.SMACK64EXEC
[    0.126281] evm: security.SMACK64TRANSMUTE
[    0.126281] evm: security.SMACK64MMAP
[    0.126282] evm: security.ima
[    0.126283] evm: security.capability
[    0.126335] PM: Registering ACPI NVS region [mem 0xc971c000-0xc9d1cfff] (6295552 bytes)
[    0.126407] PM: Registering ACPI NVS region [mem 0xca5fc000-0xca87bfff] (2621440 bytes)
[    0.126438] PM: Registering ACPI NVS region [mem 0xca882000-0xca8c4fff] (274432 bytes)
[    0.127210] pinctrl core: initialized pinctrl subsystem
[    0.127272] regulator-dummy: no parameters
[    0.127305] RTC time: 18:52:39, date: 06/04/15
[    0.127353] NET: Registered protocol family 16
[    0.127490] cpuidle: using governor ladder
[    0.127493] cpuidle: using governor menu
[    0.127553] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.127555] ACPI: bus type PCI registered
[    0.127556] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.127618] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.127621] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.127702] PCI: Using configuration type 1 for base access
[    0.132732] ACPI: Added _OSI(Module Device)
[    0.132734] ACPI: Added _OSI(Processor Device)
[    0.132735] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.132736] ACPI: Added _OSI(Processor Aggregator Device)
[    0.134655] ACPI : EC: EC description table is found, configuring boot EC
[    0.136617] ACPI: Executed 1 blocks of module-level executable AML code
[    0.252633] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.253085] ACPI: Dynamic OEM Table Load:
[    0.253092] ACPI: SSDT 0xFFFF88031D5DA000 000853 (v01 PmRef  Cpu0Cst  00003001 INTL 20051117)
[    0.256784] ACPI: Dynamic OEM Table Load:
[    0.256788] ACPI: SSDT 0xFFFF88031D5B6400 000303 (v01 PmRef  ApIst    00003000 INTL 20051117)
[    0.260676] ACPI: Dynamic OEM Table Load:
[    0.260680] ACPI: SSDT 0xFFFF88031D5C1800 000119 (v01 PmRef  ApCst    00003000 INTL 20051117)
[    0.265151] ACPI: Interpreter enabled
[    0.265158] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20140424/hwxface-580)
[    0.265163] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20140424/hwxface-580)
[    0.265177] ACPI: (supports S0 S3 S4 S5)
[    0.265178] ACPI: Using IOAPIC for interrupt routing
[    0.265200] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.386112] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.386118] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.386273] acpi PNP0A08:00: _OSC: platform does not support [PCIeHotplug PME]
[    0.386397] acpi PNP0A08:00: _OSC: OS now controls [AER PCIeCapability]
[    0.386917] PCI host bridge to bus 0000:00
[    0.386919] pci_bus 0000:00: root bus resource [bus 00-3e]
[    0.386921] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.386922] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.386924] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.386925] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff]
[    0.386927] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff]
[    0.386928] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff]
[    0.386929] pci_bus 0000:00: root bus resource [mem 0x000cc000-0x000cffff]
[    0.386931] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.386932] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.386934] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.386935] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.386936] pci_bus 0000:00: root bus resource [mem 0xcfe00000-0xfeafffff]
[    0.386943] pci 0000:00:00.0: [8086:0154] type 00 class 0x060000
[    0.387031] pci 0000:00:01.0: [8086:0151] type 01 class 0x060400
[    0.387062] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.387103] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.387141] pci 0000:00:02.0: [8086:0166] type 00 class 0x030000
[    0.387151] pci 0000:00:02.0: reg 0x10: [mem 0xf7400000-0xf77fffff 64bit]
[    0.387158] pci 0000:00:02.0: reg 0x18: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.387162] pci 0000:00:02.0: reg 0x20: [io  0xf000-0xf03f]
[    0.387265] pci 0000:00:14.0: [8086:1e31] type 00 class 0x0c0330
[    0.387289] pci 0000:00:14.0: reg 0x10: [mem 0xf7a00000-0xf7a0ffff 64bit]
[    0.387362] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.387407] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.387447] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
[    0.387471] pci 0000:00:16.0: reg 0x10: [mem 0xf7a19000-0xf7a1900f 64bit]
[    0.387548] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.387635] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
[    0.387657] pci 0000:00:1a.0: reg 0x10: [mem 0xf7a17000-0xf7a173ff]
[    0.387749] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.387795] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.387834] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
[    0.387851] pci 0000:00:1b.0: reg 0x10: [mem 0xf7a10000-0xf7a13fff 64bit]
[    0.387926] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.387972] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.388008] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
[    0.388093] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.388171] pci 0000:00:1c.1: [8086:1e12] type 01 class 0x060400
[    0.388255] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.388335] pci 0000:00:1c.3: [8086:1e16] type 01 class 0x060400
[    0.388420] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.388468] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    0.388510] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
[    0.388532] pci 0000:00:1d.0: reg 0x10: [mem 0xf7a16000-0xf7a163ff]
[    0.388623] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.388670] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.388707] pci 0000:00:1f.0: [8086:1e59] type 00 class 0x060100
[    0.388885] pci 0000:00:1f.2: [8086:1e01] type 00 class 0x01018f
[    0.388902] pci 0000:00:1f.2: reg 0x10: [io  0xf110-0xf117]
[    0.388909] pci 0000:00:1f.2: reg 0x14: [io  0xf100-0xf103]
[    0.388917] pci 0000:00:1f.2: reg 0x18: [io  0xf0f0-0xf0f7]
[    0.388926] pci 0000:00:1f.2: reg 0x1c: [io  0xf0e0-0xf0e3]
[    0.388934] pci 0000:00:1f.2: reg 0x20: [io  0xf0d0-0xf0df]
[    0.388942] pci 0000:00:1f.2: reg 0x24: [io  0xf0c0-0xf0cf]
[    0.389041] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
[    0.389057] pci 0000:00:1f.3: reg 0x10: [mem 0xf7a15000-0xf7a150ff 64bit]
[    0.389079] pci 0000:00:1f.3: reg 0x20: [io  0xf040-0xf05f]
[    0.389165] pci 0000:00:1f.5: [8086:1e09] type 00 class 0x010185
[    0.389178] pci 0000:00:1f.5: reg 0x10: [io  0xf0b0-0xf0b7]
[    0.389185] pci 0000:00:1f.5: reg 0x14: [io  0xf0a0-0xf0a3]
[    0.389191] pci 0000:00:1f.5: reg 0x18: [io  0xf090-0xf097]
[    0.389197] pci 0000:00:1f.5: reg 0x1c: [io  0xf080-0xf083]
[    0.389204] pci 0000:00:1f.5: reg 0x20: [io  0xf070-0xf07f]
[    0.389210] pci 0000:00:1f.5: reg 0x24: [io  0xf060-0xf06f]
[    0.389352] pci 0000:01:00.0: [10de:0de3] type 00 class 0x030000
[    0.389362] pci 0000:01:00.0: reg 0x10: [mem 0xf6000000-0xf6ffffff]
[    0.389371] pci 0000:01:00.0: reg 0x14: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.389380] pci 0000:01:00.0: reg 0x1c: [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.389386] pci 0000:01:00.0: reg 0x24: [io  0xe000-0xe07f]
[    0.389392] pci 0000:01:00.0: reg 0x30: [mem 0xf7000000-0xf707ffff pref]
[    0.396823] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.396828] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.396832] pci 0000:00:01.0:   bridge window [mem 0xf6000000-0xf70fffff]
[    0.396838] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xf1ffffff 64bit pref]
[    0.396919] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.397058] pci 0000:03:00.0: [8086:0887] type 00 class 0x028000
[    0.397112] pci 0000:03:00.0: reg 0x10: [mem 0xf7900000-0xf7901fff 64bit]
[    0.397360] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.397410] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.404906] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.404913] pci 0000:00:1c.1:   bridge window [mem 0xf7900000-0xf79fffff]
[    0.405005] pci 0000:04:00.0: [1969:1083] type 00 class 0x020000
[    0.405037] pci 0000:04:00.0: reg 0x10: [mem 0xf7800000-0xf783ffff 64bit]
[    0.405052] pci 0000:04:00.0: reg 0x18: [io  0xd000-0xd07f]
[    0.405192] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.405227] pci 0000:04:00.0: System wakeup disabled by ACPI
[    0.412860] pci 0000:00:1c.3: PCI bridge to [bus 04]
[    0.412867] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    0.412874] pci 0000:00:1c.3:   bridge window [mem 0xf7800000-0xf78fffff]
[    0.412943] acpi PNP0A08:00: Disabling ASPM (FADT indicates it is unsupported)
[    0.469447] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11 12) *0, disabled.
[    0.469491] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 12) *0, disabled.
[    0.469534] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 12) *0, disabled.
[    0.469577] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 12) *0, disabled.
[    0.469620] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 12) *0, disabled.
[    0.469661] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 12) *0, disabled.
[    0.469702] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 12) *0, disabled.
[    0.469742] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 12) *0, disabled.
[    0.469880] ACPI: Enabled 3 GPEs in block 00 to 3F
[    0.469942] ACPI : EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[    0.470028] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.470030] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.470034] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=none,locks=none
[    0.470035] vgaarb: loaded
[    0.470036] vgaarb: bridge control possible 0000:01:00.0
[    0.470037] vgaarb: no bridge control possible 0000:00:02.0
[    0.470248] SCSI subsystem initialized
[    0.470293] libata version 3.00 loaded.
[    0.470316] ACPI: bus type USB registered
[    0.470333] usbcore: registered new interface driver usbfs
[    0.470341] usbcore: registered new interface driver hub
[    0.470372] usbcore: registered new device driver usb
[    0.470583] PCI: Using ACPI for IRQ routing
[    0.472145] PCI: pci_cache_line_size set to 64 bytes
[    0.472204] e820: reserve RAM buffer [mem 0x0009e000-0x0009ffff]
[    0.472206] e820: reserve RAM buffer [mem 0x40004000-0x43ffffff]
[    0.472207] e820: reserve RAM buffer [mem 0xc8119018-0xcbffffff]
[    0.472212] e820: reserve RAM buffer [mem 0xc971c000-0xcbffffff]
[    0.472218] e820: reserve RAM buffer [mem 0xc9d37000-0xcbffffff]
[    0.472222] e820: reserve RAM buffer [mem 0xc9d3f000-0xcbffffff]
[    0.472227] e820: reserve RAM buffer [mem 0xc9edb000-0xcbffffff]
[    0.472232] e820: reserve RAM buffer [mem 0xc9f28000-0xcbffffff]
[    0.472236] e820: reserve RAM buffer [mem 0xc9f66000-0xcbffffff]
[    0.472241] e820: reserve RAM buffer [mem 0xc9f74000-0xcbffffff]
[    0.472245] e820: reserve RAM buffer [mem 0xc9f84000-0xcbffffff]
[    0.472249] e820: reserve RAM buffer [mem 0xc9f90000-0xcbffffff]
[    0.472253] e820: reserve RAM buffer [mem 0xc9fc9000-0xcbffffff]
[    0.472256] e820: reserve RAM buffer [mem 0xc9fda000-0xcbffffff]
[    0.472260] e820: reserve RAM buffer [mem 0xca016000-0xcbffffff]
[    0.472263] e820: reserve RAM buffer [mem 0xca018000-0xcbffffff]
[    0.472266] e820: reserve RAM buffer [mem 0xca01b000-0xcbffffff]
[    0.472268] e820: reserve RAM buffer [mem 0xca037000-0xcbffffff]
[    0.472271] e820: reserve RAM buffer [mem 0xca882000-0xcbffffff]
[    0.472273] e820: reserve RAM buffer [mem 0xcacd8000-0xcbffffff]
[    0.472274] e820: reserve RAM buffer [mem 0xcb000000-0xcbffffff]
[    0.472276] e820: reserve RAM buffer [mem 0x32f200000-0x32fffffff]
[    0.472381] NetLabel: Initializing
[    0.472382] NetLabel:  domain hash size = 128
[    0.472383] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.472395] NetLabel:  unlabeled traffic allowed by default
[    0.472455] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.472459] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.474504] Switched to clocksource hpet
[    0.479529] AppArmor: AppArmor Filesystem Enabled
[    0.479560] pnp: PnP ACPI init
[    0.479574] ACPI: bus type PNP registered
[    0.479660] system 00:00: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.479664] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.534748] system 00:01: [io  0x0680-0x069f] has been reserved
[    0.534750] system 00:01: [io  0x1000-0x100f] has been reserved
[    0.534752] system 00:01: [io  0xffff] has been reserved
[    0.534753] system 00:01: [io  0xffff] has been reserved
[    0.534755] system 00:01: [io  0x0400-0x0453] could not be reserved
[    0.534757] system 00:01: [io  0x0458-0x047f] has been reserved
[    0.534758] system 00:01: [io  0x0500-0x057f] has been reserved
[    0.534760] system 00:01: [io  0x164e-0x164f] has been reserved
[    0.534762] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.534792] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.534839] system 00:03: [io  0x0454-0x0457] has been reserved
[    0.534841] system 00:03: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.534889] system 00:04: [io  0x04d0-0x04d1] has been reserved
[    0.534891] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.534948] pnp 00:05: Plug and Play ACPI device, IDs ETD0108 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)
[    0.534988] pnp 00:06: Plug and Play ACPI device, IDs ATK3001 PNP030b (active)
[    0.535172] system 00:07: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.535174] system 00:07: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.535176] system 00:07: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.535177] system 00:07: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.535179] system 00:07: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.535181] system 00:07: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.535183] system 00:07: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.535184] system 00:07: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.535186] system 00:07: [mem 0xff000000-0xffffffff] has been reserved
[    0.535188] system 00:07: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.535190] system 00:07: [mem 0xcfe00000-0xcfe00fff] has been reserved
[    0.535192] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.535268] system 00:08: [mem 0xcfe00000-0xcfe00fff] has been reserved
[    0.535271] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.535396] system 00:09: [mem 0x20000000-0x201fffff] has been reserved
[    0.535398] system 00:09: [mem 0x40004000-0x40004fff] has been reserved
[    0.535400] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.535426] pnp: PnP ACPI: found 10 devices
[    0.535427] ACPI: bus type PNP unregistered
[    0.541792] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.541795] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.541798] pci 0000:00:01.0:   bridge window [mem 0xf6000000-0xf70fffff]
[    0.541801] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xf1ffffff 64bit pref]
[    0.541804] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.541816] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.541821] pci 0000:00:1c.1:   bridge window [mem 0xf7900000-0xf79fffff]
[    0.541829] pci 0000:00:1c.3: PCI bridge to [bus 04]
[    0.541832] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    0.541837] pci 0000:00:1c.3:   bridge window [mem 0xf7800000-0xf78fffff]
[    0.541847] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.541848] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.541850] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.541851] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.541852] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.541854] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.541855] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff]
[    0.541857] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff]
[    0.541858] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff]
[    0.541860] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff]
[    0.541861] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff]
[    0.541863] pci_bus 0000:00: resource 15 [mem 0xcfe00000-0xfeafffff]
[    0.541864] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.541866] pci_bus 0000:01: resource 1 [mem 0xf6000000-0xf70fffff]
[    0.541867] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xf1ffffff 64bit pref]
[    0.541869] pci_bus 0000:03: resource 1 [mem 0xf7900000-0xf79fffff]
[    0.541871] pci_bus 0000:04: resource 0 [io  0xd000-0xdfff]
[    0.541872] pci_bus 0000:04: resource 1 [mem 0xf7800000-0xf78fffff]
[    0.541897] NET: Registered protocol family 2
[    0.542088] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.542304] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.542418] TCP: Hash tables configured (established 131072 bind 65536)
[    0.542436] TCP: reno registered
[    0.542452] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    0.542502] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    0.542574] NET: Registered protocol family 1
[    0.542600] pci 0000:00:02.0: Video device with shadowed ROM
[    0.543076] PCI: CLS 64 bytes, default 64
[    0.543131] Trying to unpack rootfs image as initramfs...
[    0.848952] Freeing initrd memory: 20720K (ffff88003d7c9000 - ffff88003ec05000)
[    0.848983] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.848986] software IO TLB [mem 0xc4119000-0xc8119000] (64MB) mapped at [ffff8800c4119000-ffff8800c8118fff]
[    0.849231] RAPL PMU detected, hw unit 2^-16 Joules, API unit is 2^-32 Joules, 3 fixed counters 163840 ms ovfl timer
[    0.849271] microcode: CPU0 sig=0x306a9, pf=0x10, revision=0x15
[    0.849278] microcode: CPU1 sig=0x306a9, pf=0x10, revision=0x15
[    0.849286] microcode: CPU2 sig=0x306a9, pf=0x10, revision=0x15
[    0.849295] microcode: CPU3 sig=0x306a9, pf=0x10, revision=0x15
[    0.849341] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.849365] Scanning for low memory corruption every 60 seconds
[    0.849638] futex hash table entries: 1024 (order: 4, 65536 bytes)
[    0.849652] Initialise system trusted keyring
[    0.849677] audit: initializing netlink subsys (disabled)
[    0.849688] audit: type=2000 audit(1433443959.844:1): initialized
[    0.850023] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.851333] zpool: loaded
[    0.851337] zbud: loaded
[    0.851485] VFS: Disk quotas dquot_6.5.2
[    0.851515] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.851918] fuse init (API version 7.23)
[    0.851995] msgmni has been set to 23800
[    0.852045] Key type big_key registered
[    0.852406] Key type asymmetric registered
[    0.852409] Asymmetric key parser 'x509' registered
[    0.852441] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.852487] io scheduler noop registered
[    0.852490] io scheduler deadline registered (default)
[    0.852531] io scheduler cfq registered
[    0.852709] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.853084] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.853098] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.853147] efifb: probing for efifb
[    0.853164] efifb: framebuffer at 0xd0000000, mapped to 0xffffc90005c00000, using 4128k, total 4128k
[    0.853166] efifb: mode is 1366x768x32, linelength=5504, pages=1
[    0.853166] efifb: scrolling: redraw
[    0.853168] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.853240] Console: switching to colour frame buffer device 170x48
[    0.853256] fb0: EFI VGA frame buffer device
[    0.853270] intel_idle: MWAIT substates: 0x21120
[    0.853272] intel_idle: v0.4 model 0x3A
[    0.853272] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.859023] ACPI: AC Adapter [AC0] (off-line)
[    0.859120] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.895069] ACPI: Lid Switch [LID]
[    0.895114] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.895117] ACPI: Sleep Button [SLPB]
[    0.895151] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.895153] ACPI: Power Button [PWRF]
[    0.895795] thermal LNXTHERM:00: registered as thermal_zone0
[    0.895797] ACPI: Thermal Zone [THRM] (37 C)
[    0.895831] GHES: HEST is not enabled!
[    0.895917] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.898157] Linux agpgart interface v0.103
[    0.899626] brd: module loaded
[    0.900376] loop: module loaded
[    0.900528] ata_piix 0000:00:1f.2: version 2.13
[    0.900608] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.931238] ACPI: Battery Slot [BAT0] (battery present)
[    1.055655] scsi0 : ata_piix
[    1.055857] scsi1 : ata_piix
[    1.055905] ata1: SATA max UDMA/133 cmd 0xf110 ctl 0xf100 bmdma 0xf0d0 irq 19
[    1.055910] ata2: SATA max UDMA/133 cmd 0xf0f0 ctl 0xf0e0 bmdma 0xf0d8 irq 19
[    1.055926] ata_piix 0000:00:1f.5: enabling device (0000 -> 0001)
[    1.056015] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    1.211370] ata_piix 0000:00:1f.5: SCR access via SIDPR is available but doesn't work
[    1.211657] scsi2 : ata_piix
[    1.211840] scsi3 : ata_piix
[    1.211875] ata3: SATA max UDMA/133 cmd 0xf0b0 ctl 0xf0a0 bmdma 0xf070 irq 19
[    1.211876] ata4: SATA max UDMA/133 cmd 0xf090 ctl 0xf080 bmdma 0xf078 irq 19
[    1.211950] libphy: Fixed MDIO Bus: probed
[    1.211953] tun: Universal TUN/TAP device driver, 1.6
[    1.211954] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.212027] PPP generic driver version 2.4.2
[    1.212084] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.212094] ehci-pci: EHCI PCI platform driver
[    1.212203] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    1.212208] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.212221] ehci-pci 0000:00:1a.0: debug port 2
[    1.216136] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    1.216149] ehci-pci 0000:00:1a.0: irq 16, io mem 0xf7a17000
[    1.227382] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.227419] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.227421] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.227423] usb usb1: Product: EHCI Host Controller
[    1.227424] usb usb1: Manufacturer: Linux 3.16.0-33-generic ehci_hcd
[    1.227425] usb usb1: SerialNumber: 0000:00:1a.0
[    1.227531] hub 1-0:1.0: USB hub found
[    1.227537] hub 1-0:1.0: 2 ports detected
[    1.227721] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    1.227727] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.227738] ehci-pci 0000:00:1d.0: debug port 2
[    1.231654] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    1.231666] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf7a16000
[    1.243398] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.243432] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.243434] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.243435] usb usb2: Product: EHCI Host Controller
[    1.243437] usb usb2: Manufacturer: Linux 3.16.0-33-generic ehci_hcd
[    1.243438] usb usb2: SerialNumber: 0000:00:1d.0
[    1.243537] hub 2-0:1.0: USB hub found
[    1.243542] hub 2-0:1.0: 2 ports detected
[    1.243619] ehci-platform: EHCI generic platform driver
[    1.243630] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.243634] ohci-pci: OHCI PCI platform driver
[    1.243644] ohci-platform: OHCI generic platform driver
[    1.243652] uhci_hcd: USB Universal Host Controller Interface driver
[    1.243758] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.243762] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    1.243852] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    1.243870] xhci_hcd 0000:00:14.0: irq 41 for MSI/MSI-X
[    1.243925] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    1.243926] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.243928] usb usb3: Product: xHCI Host Controller
[    1.243929] usb usb3: Manufacturer: Linux 3.16.0-33-generic xhci_hcd
[    1.243930] usb usb3: SerialNumber: 0000:00:14.0
[    1.244023] hub 3-0:1.0: USB hub found
[    1.244031] hub 3-0:1.0: 4 ports detected
[    1.244124] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.244127] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    1.244156] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    1.244157] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.244158] usb usb4: Product: xHCI Host Controller
[    1.244160] usb usb4: Manufacturer: Linux 3.16.0-33-generic xhci_hcd
[    1.244161] usb usb4: SerialNumber: 0000:00:14.0
[    1.244247] hub 4-0:1.0: USB hub found
[    1.244255] hub 4-0:1.0: 4 ports detected
[    1.244400] i8042: PNP: PS/2 Controller [PNP030b:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.246668] i8042: Detected active multiplexing controller, rev 1.1
[    1.247602] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.247606] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.247629] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.247648] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.247666] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.247779] mousedev: PS/2 mouse device common for all mice
[    1.247957] rtc_cmos 00:02: RTC can wake from S4
[    1.248085] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.248113] rtc_cmos 00:02: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.248170] device-mapper: uevent: version 1.0.3
[    1.248236] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    1.248249] Intel P-state driver initializing.
[    1.248285] Intel pstate controlling: cpu 0
[    1.248308] Intel pstate controlling: cpu 1
[    1.248349] Intel pstate controlling: cpu 2
[    1.248362] Intel pstate controlling: cpu 3
[    1.248381] Consider also installing thermald for improved thermal control.
[    1.248386] ledtrig-cpu: registered to indicate activity on CPUs
[    1.248403] EFI Variables Facility v0.08 2004-May-17
[    1.251481] TCP: cubic registered
[    1.251567] NET: Registered protocol family 10
[    1.251728] NET: Registered protocol family 17
[    1.251737] Key type dns_resolver registered
[    1.252000] Loading compiled-in X.509 certificates
[    1.252748] Loaded X.509 cert 'Magrathea: Glacier signing key: 27437300f8ee183c8811434feb7fd95fc68782ec'
[    1.252768] registered taskstats version 1
[    1.254550] Key type trusted registered
[    1.257359] Key type encrypted registered
[    1.257366] AppArmor: AppArmor sha1 policy hashing enabled
[    1.257370] ima: No TPM chip found, activating TPM-bypass!
[    1.257382] evm: HMAC attrs: 0x1
[    1.257744]   Magic number: 3:548:897
[    1.257778] acpi INT340E:00: hash matches
[    1.257846] rtc_cmos 00:02: setting system clock to 2015-06-04 18:52:40 UTC (1433443960)
[    1.257919] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.257920] EDD information not available.
[    1.258036] PM: Hibernation image not present or could not be loaded.
[    1.285427] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.539821] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.672576] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.672579] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.672969] hub 1-1:1.0: USB hub found
[    1.673185] hub 1-1:1.0: 6 ports detected
[    1.784030] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.848129] tsc: Refined TSC clocksource calibration: 2494.333 MHz
[    1.916532] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.916538] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.916848] hub 2-1:1.0: USB hub found
[    1.917034] hub 2-1:1.0: 6 ports detected
[    1.988344] usb 1-1.1: new full-speed USB device number 3 using ehci-pci
[    2.084377] ata2.00: failed to resume link (SControl 30)
[    2.085068] usb 1-1.1: New USB device found, idVendor=8087, idProduct=07da
[    2.085073] usb 1-1.1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.156533] usb 1-1.3: new high-speed USB device number 4 using ehci-pci
[    2.352281] usb 1-1.3: New USB device found, idVendor=13d3, idProduct=5165
[    2.352287] usb 1-1.3: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[    2.352291] usb 1-1.3: Product: USB Camera
[    2.352294] usb 1-1.3: Manufacturer: Azurewave
[    2.352296] usb 1-1.3: SerialNumber: NULL
[    2.404759] ata1.01: failed to resume link (SControl 0)
[    2.561010] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 330)
[    2.561023] ata1.01: SATA link down (SStatus 0 SControl 0)
[    2.569436] ata1.00: ATA-8: Hitachi HTS547575A9E384, JE4OA60A, max UDMA/133
[    2.569442] ata1.00: 1465149168 sectors, multi 0: LBA48 NCQ (depth 0/32)
[    2.585457] ata1.00: configured for UDMA/133
[    2.585709] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54757 A60A PQ: 0 ANSI: 5
[    2.586056] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.586080] sd 0:0:0:0: [sda] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[    2.586083] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    2.586249] sd 0:0:0:0: [sda] Write Protect is off
[    2.586252] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.586302] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.667217]  sda: sda1 sda2 sda3
[    2.667585] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.849353] Switched to clocksource tsc
[    3.113564] ata2.01: failed to resume link (SControl 0)
[    3.125088] ata2.00: SATA link down (SStatus 4 SControl 30)
[    3.125102] ata2.01: SATA link down (SStatus 0 SControl 0)
[    3.125902] Freeing unused kernel memory: 1360K (ffffffff81d2d000 - ffffffff81e81000)
[    3.125904] Write protecting the kernel read-only data: 12288k
[    3.126806] Freeing unused kernel memory: 436K (ffff880002793000 - ffff880002800000)
[    3.127643] Freeing unused kernel memory: 484K (ffff880002b87000 - ffff880002c00000)
[    3.135962] systemd-udevd[130]: starting version 208
[    3.136341] random: systemd-udevd urandom read with 26 bits of entropy available
[    3.206986] atl1c 0000:04:00.0: version 1.0.1.1-NAPI
[    3.610487] psmouse serio4: alps: Unknown ALPS touchpad: E7=10 00 64, EC=10 00 64
[    4.105434] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x361f01)
[    4.119017] psmouse serio4: elantech: Synaptics capabilities query result 0x00, 0x15, 0x0c.
[    4.187332] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input11
[    4.356336] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[    5.081237] random: nonblocking pool is initialized
[   15.837963] Adding 12468220k swap on /dev/mapper/ubuntu--vg-swap_1.  Priority:-1 extents:1 across:12468220k FS
[   16.192925] EXT4-fs (dm-0): re-mounted. Opts: discard,errors=remount-ro
[   17.264754] systemd-udevd[377]: starting version 208
[   17.678501] lp: driver loaded but no devices found
[   17.681029] ppdev: user-space parallel port driver
[   17.704192] wmi: Mapper loaded
[   17.721654] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.724106] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042f conflicts with OpRegion 0x0000000000000400-0x000000000000044f (\GPIS) (20140424/utaddress-258)
[   17.724111] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042f conflicts with OpRegion 0x0000000000000400-0x000000000000047f (\PMIO) (20140424/utaddress-258)
[   17.724114] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   17.724117] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054f conflicts with OpRegion 0x0000000000000500-0x000000000000057f (\GPIO) (20140424/utaddress-258)
[   17.724119] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GP01) (20140424/utaddress-258)
[   17.724121] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   17.724122] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053f conflicts with OpRegion 0x0000000000000500-0x000000000000057f (\GPIO) (20140424/utaddress-258)
[   17.724124] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GP01) (20140424/utaddress-258)
[   17.724126] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   17.724127] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052f conflicts with OpRegion 0x0000000000000500-0x000000000000057f (\GPIO) (20140424/utaddress-258)
[   17.724128] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GP01) (20140424/utaddress-258)
[   17.724131] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   17.724131] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   17.735845] [drm] Initialized drm 1.1.0 20060810
[   17.738728] mei_me 0000:00:16.0: irq 42 for MSI/MSI-X
[   17.752564] cfg80211: Calling CRDA to update world regulatory domain
[   17.761605] Intel(R) Wireless WiFi driver for Linux, in-tree:
[   17.761608] Copyright(c) 2003- 2014 Intel Corporation
[   17.761730] iwlwifi 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   17.761830] iwlwifi 0000:03:00.0: irq 43 for MSI/MSI-X
[   17.771101] [drm] Memory usable by graphics device = 2048M
[   17.771106] checking generic (d0000000 408000) vs hw (d0000000 10000000)
[   17.771108] fb: switching to inteldrmfb from EFI VGA
[   17.771131] Console: switching to colour dummy device 80x25
[   17.771201] [drm] Replacing VGA console driver
[   17.790193] AVX version of gcm_enc/dec engaged.
[   17.819556] Bluetooth: Core ver 2.19
[   17.819594] NET: Registered protocol family 31
[   17.819596] Bluetooth: HCI device and connection manager initialized
[   17.819604] Bluetooth: HCI socket layer initialized
[   17.819607] Bluetooth: L2CAP socket layer initialized
[   17.819616] Bluetooth: SCO socket layer initialized
[   17.828142] usbcore: registered new interface driver btusb
[   17.852094] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[   17.852103] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   17.852104] [drm] Driver supports precise vblank timestamp query.
[   17.855769] intel_rapl: Found RAPL domain package
[   17.855772] intel_rapl: Found RAPL domain core
[   17.855774] intel_rapl: Found RAPL domain uncore
[   17.856892] EXT4-fs (sda2): mounting ext2 file system using the ext4 subsystem
[   17.870728] asus_wmi: ASUS WMI generic driver loaded
[   17.879030] asus_wmi: Initialization: 0x1
[   17.879101] asus_wmi: BIOS WMI version: 7.9
[   17.879174] asus_wmi: SFUN value: 0x4a0877
[   17.879354] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=none
[   17.880231] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input12
[   17.919705] fbcon: inteldrmfb (fb0) is primary device
[   17.919748] Console: switching to colour frame buffer device 170x48
[   17.919765] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   17.919766] i915 0000:00:02.0: registered panic notifier
[   17.930710] ACPI: Video Device [PEGP] (multi-head: yes  rom: yes  post: no)
[   17.930762] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:02/LNXVIDEO:00/input/input13
[   17.934941] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   17.938563] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input14
[   17.938620] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   17.938774] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   17.960941] sound hdaudioC0D0: autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   17.960945] sound hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   17.960946] sound hdaudioC0D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[   17.960947] sound hdaudioC0D0:    mono: mono_out=0x0
[   17.960949] sound hdaudioC0D0:    dig-out=0x1e/0x0
[   17.960950] sound hdaudioC0D0:    inputs:
[   17.960951] sound hdaudioC0D0:      Internal Mic=0x19
[   17.960953] sound hdaudioC0D0:      Mic=0x18
[   17.970439] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   17.970543] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
[   17.970611] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input17
[   17.980123] asus_wmi: Backlight controlled by ACPI video driver
[   18.132522] usb 1-1.1: USB disconnect, device number 3
[   18.296569] EXT4-fs (sda2): mounted filesystem without journal. Opts: (null)
[   18.833815] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[   18.845824] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   18.845828] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   18.845830] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   18.845832] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 2230 BGN, REV=0xC8
[   18.845887] iwlwifi 0000:03:00.0: L1 Disabled - LTR Disabled
[   18.867545] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   18.887444] cfg80211: World regulatory domain updated:
[   18.887448] cfg80211:  DFS Master region: unset
[   18.887450] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   18.887452] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   18.887454] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   18.887456] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[   18.887458] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   18.887459] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   19.513741] media: Linux media interface: v0.10
[   19.516740] Linux video capture interface: v2.00
[   19.523381] uvcvideo: Found UVC 1.00 device USB Camera (13d3:5165)
[   19.534503] input: USB Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input18
[   19.534579] usbcore: registered new interface driver uvcvideo
[   19.534581] USB Video Class driver (1.1.1)
[   19.637954] audit: type=1400 audit(1433443978.853:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=575 comm="apparmor_parser"
[   19.637960] audit: type=1400 audit(1433443978.853:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=575 comm="apparmor_parser"
[   19.637963] audit: type=1400 audit(1433443978.853:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=575 comm="apparmor_parser"
[   19.638440] audit: type=1400 audit(1433443978.853:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=519 comm="apparmor_parser"
[   19.638448] audit: type=1400 audit(1433443978.853:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=519 comm="apparmor_parser"
[   19.638454] audit: type=1400 audit(1433443978.853:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=519 comm="apparmor_parser"
[   19.638594] audit: type=1400 audit(1433443978.853:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=520 comm="apparmor_parser"
[   19.638599] audit: type=1400 audit(1433443978.853:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=520 comm="apparmor_parser"
[   19.638603] audit: type=1400 audit(1433443978.853:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=520 comm="apparmor_parser"
[   19.816683] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off
[   21.238427] init: failsafe main process (660) killed by TERM signal
[   22.689456] audit: type=1400 audit(1433443981.901:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=868 comm="apparmor_parser"
[   23.675598] Bluetooth: RFCOMM TTY layer initialized
[   23.675608] Bluetooth: RFCOMM socket layer initialized
[   23.675612] Bluetooth: RFCOMM ver 1.11
[   23.725604] init: cups main process (877) killed by HUP signal
[   23.725612] init: cups main process ended, respawning
[   23.923539] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.923543] Bluetooth: BNEP filters: protocol multicast
[   23.923549] Bluetooth: BNEP socket layer initialized
[   23.985137] nvidia: module license 'NVIDIA' taints kernel.
[   23.985140] Disabling lock debugging due to kernel taint
[   23.987649] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[   23.991130] nvidia 0000:01:00.0: enabling device (0000 -> 0003)
[   23.991202] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
[   23.991512] [drm] Initialized nvidia-drm 0.0.0 20130102 for 0000:01:00.0 on minor 1
[   23.991518] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  331.113  Mon Dec  1 21:08:13 PST 2014
[   27.554641] systemd-logind[999]: New seat seat0.
[   27.595514] systemd-logind[999]: Watching system buttons on /dev/input/event2 (Power Button)
[   27.595561] systemd-logind[999]: Watching system buttons on /dev/input/event7 (Video Bus)
[   27.595603] systemd-logind[999]: Watching system buttons on /dev/input/event6 (Video Bus)
[   27.595642] systemd-logind[999]: Watching system buttons on /dev/input/event0 (Lid Switch)
[   27.595681] systemd-logind[999]: Watching system buttons on /dev/input/event1 (Sleep Button)
[   27.828521] iwlwifi 0000:03:00.0: L1 Disabled - LTR Disabled
[   27.835928] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[   28.077696] iwlwifi 0000:03:00.0: L1 Disabled - LTR Disabled
[   28.085102] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[   28.142650] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.153593] atl1c 0000:04:00.0: irq 46 for MSI/MSI-X
[   28.171383] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.671117] wlan0: authenticate with c0:4a:00:fb:25:07
[   29.676165] wlan0: send auth to c0:4a:00:fb:25:07 (try 1/3)
[   29.678138] wlan0: authenticated
[   29.679891] wlan0: associate with c0:4a:00:fb:25:07 (try 1/3)
[   29.683819] wlan0: RX AssocResp from c0:4a:00:fb:25:07 (capab=0x431 status=0 aid=2)
[   29.704852] wlan0: associated
[   29.704902] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   31.682424] audit_printk_skb: 72 callbacks suppressed
[   31.682427] audit: type=1400 audit(1433443990.885:36): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cups-browsed" pid=1273 comm="apparmor_parser"
[   31.701662] init: anacron main process (1218) terminated with status 1
[   32.333609] audit: type=1400 audit(1433443991.533:37): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/mysqld" pid=1317 comm="apparmor_parser"
[   33.059832] Non-volatile memory driver v1.3
[   48.749391] bbswitch: version 0.7
[   48.749398] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
[   48.749404] bbswitch: Found discrete VGA device 0000:01:00.0: \_SB_.PCI0.PEG0.PEGP
[   48.749414] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20140424/nsarguments-95)
[   48.749488] bbswitch: detected an Optimus _DSM function
[   48.749494] bbswitch: Succesfully loaded. Discrete card 0000:01:00.0 is on
[   48.753375] [drm] Module unloaded
[   48.754327] bbswitch: disabling discrete graphics
[   48.754336] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20140424/nsarguments-95)
[   48.769687] pci 0000:01:00.0: Refused to change power state, currently in D0
[   51.628754] init: plymouth-upstart-bridge main process ended, respawning
[   51.650356] init: plymouth-upstart-bridge main process ended, respawning
[   51.750923] systemd-logind[999]: Failed to start unit user@112.service: Unknown unit: user@112.service
[   51.750929] systemd-logind[999]: Failed to start user service: Unknown unit: user@112.service
[   51.753845] systemd-logind[999]: New session c1 of user lightdm.
[   51.753868] systemd-logind[999]: Linked /tmp/.X11-unix/X0 to /run/user/112/X11-display.
[   53.127120] audit: type=1400 audit(1433444012.305:38): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2153 comm="apparmor_parser"
[   53.127128] audit: type=1400 audit(1433444012.305:39): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2153 comm="apparmor_parser"
[   53.142854] audit: type=1400 audit(1433444012.321:40): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="third_party" pid=2153 comm="apparmor_parser"
[   65.639327] systemd-logind[999]: Failed to start unit user@1000.service: Unknown unit: user@1000.service
[   65.639332] systemd-logind[999]: Failed to start user service: Unknown unit: user@1000.service
[   65.642289] systemd-logind[999]: New session c2 of user nick.
[   65.642312] systemd-logind[999]: Linked /tmp/.X11-unix/X0 to /run/user/1000/X11-display.
[ 2249.467377] cfg80211: Calling CRDA to update world regulatory domain
[ 2249.478883] cfg80211: World regulatory domain updated:
[ 2249.478887] cfg80211:  DFS Master region: unset
[ 2249.478888] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[ 2249.478890] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[ 2249.478891] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[ 2249.478892] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[ 2249.478894] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[ 2249.478895] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[ 2249.962115] wlan0: authenticate with c0:4a:00:fb:25:07
[ 2249.967769] wlan0: send auth to c0:4a:00:fb:25:07 (try 1/3)
[ 2249.970267] wlan0: authenticated
[ 2249.971802] wlan0: associate with c0:4a:00:fb:25:07 (try 1/3)
[ 2249.975651] wlan0: RX AssocResp from c0:4a:00:fb:25:07 (capab=0x431 status=0 aid=2)
[ 2249.978141] wlan0: associated
[ 4354.658428] systemd-hostnamed[4827]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!

```

---

### Post by oscar-tiderman on 2015-06-05
Do you have the same slow boot time if you boot a live image, like a DVD or USB stick?

---

### Post by nbunya on 2015-06-05
No, with live image (USB) this problem has not been.


I cannot understand this lines

[   65.642312] systemd-logind[999]: Linked /tmp/.X11-unix/X0 to /run/user/1000/X11-display.
[ 2249.467377] cfg80211: Calling CRDA to update world regulatory domain

Why delay so long?

---

### Post by mörgæs on 2015-06-07
I don't think it's worth the while to troubleshoot a 14.10 installation which is soon running out of support anyway.
If the live boot works there is a good chance that a fresh install (not upgrade) of 15.04 also will.

---

### Post by nbunya on 2015-06-08
Thanks!
I'll try install 15.04 and see what will happens

---

