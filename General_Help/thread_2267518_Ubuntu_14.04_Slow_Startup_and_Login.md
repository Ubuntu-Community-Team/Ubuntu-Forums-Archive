---
title: "Ubuntu 14.04 Slow Startup and Login"
date: 2015-03-02
forum: General Help
---

### Post by hcamelion on 2015-03-02
Hi,

I have a 14.04 System76 laptop that has a slow startup.  It is mostly slow after I login at the login screen.  It takes over 2 minutes to get to the login and over 2 minutes to login.  I guess getting to the login in 2 min is average but I remember logging in being much quicker in the past?  Can anyone tell me if they see anything unusual in my dmesg?

Thanks!

```
[    0.000000] Initializing cgroup subsys cpuset[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-46-generic (buildd@aatxe) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #76-Ubuntu SMP Thu Feb 26 18:52:13 UTC 2015 (Ubuntu 3.13.0-46.76-generic 3.13.11-ckt15)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-46-generic root=UUID=6fb59d06-ec00-44f4-abcc-0da0f018be93 ro quiet splash acpi_os_name=Linux acpi_osi= vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009d7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009d800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000020200000-0x0000000040003fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000040004000-0x0000000040004fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000040005000-0x00000000d99e3fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000d99e4000-0x00000000d9e62fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000d9e63000-0x00000000d9eeefff] usable
[    0.000000] BIOS-e820: [mem 0x00000000d9eef000-0x00000000d9f91fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000d9f92000-0x00000000da5f6fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000da5f7000-0x00000000da5f7fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000da5f8000-0x00000000da63afff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000da63b000-0x00000000dad80fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000dad81000-0x00000000daff2fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000daff3000-0x00000000daffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000db800000-0x00000000df9fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000041f5fffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: System76, Inc. Gazelle Professional/Gazelle Professional, BIOS 4.6.5 09/27/2012
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x41f600 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask C00000000 write-back
[    0.000000]   1 base 400000000 mask FE0000000 write-back
[    0.000000]   2 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   3 base 0DC000000 mask FFC000000 uncachable
[    0.000000]   4 base 0DB800000 mask FFF800000 uncachable
[    0.000000]   5 base 41F800000 mask FFF800000 uncachable
[    0.000000]   6 base 41F600000 mask FFFE00000 uncachable
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 16GB, type WB
[    0.000000] reg 1, base: 16GB, range: 512MB, type WB
[    0.000000] reg 2, base: 3584MB, range: 512MB, type UC
[    0.000000] reg 3, base: 3520MB, range: 64MB, type UC
[    0.000000] reg 4, base: 3512MB, range: 8MB, type UC
[    0.000000] reg 5, base: 16888MB, range: 8MB, type UC
[    0.000000] reg 6, base: 16886MB, range: 2MB, type UC
[    0.000000] total RAM covered: 16302M
[    0.000000]  gran_size: 64K     chunk_size: 64K     num_reg: 10      lose cover RAM: 246M
[    0.000000]  gran_size: 64K     chunk_size: 128K     num_reg: 10      lose cover RAM: 246M
[    0.000000]  gran_size: 64K     chunk_size: 256K     num_reg: 10      lose cover RAM: 246M
[    0.000000]  gran_size: 64K     chunk_size: 512K     num_reg: 10      lose cover RAM: 246M
[    0.000000]  gran_size: 64K     chunk_size: 1M     num_reg: 10      lose cover RAM: 246M
[    0.000000]  gran_size: 64K     chunk_size: 2M     num_reg: 10      lose cover RAM: 246M
[    0.000000]  gran_size: 64K     chunk_size: 4M     num_reg: 10      lose cover RAM: 246M
[    0.000000]  gran_size: 64K     chunk_size: 8M     num_reg: 10      lose cover RAM: 246M
[    0.000000] *BAD*gran_size: 64K     chunk_size: 16M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 64K     chunk_size: 32M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 64K     chunk_size: 64M     num_reg: 10      lose cover RAM: -8M
[    0.000000]  gran_size: 64K     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 64K     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 64K     chunk_size: 512M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 64K     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 64K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 128K     chunk_size: 128K     num_reg: 10      lose cover RAM: 246M
[    0.000000]  gran_size: 128K     chunk_size: 256K     num_reg: 10      lose cover RAM: 246M
[    0.000000]  gran_size: 128K     chunk_size: 512K     num_reg: 10      lose cover RAM: 246M
[    0.000000]  gran_size: 128K     chunk_size: 1M     num_reg: 10      lose cover RAM: 246M
[    0.000000]  gran_size: 128K     chunk_size: 2M     num_reg: 10      lose cover RAM: 246M
[    0.000000]  gran_size: 128K     chunk_size: 4M     num_reg: 10      lose cover RAM: 246M
[    0.000000]  gran_size: 128K     chunk_size: 8M     num_reg: 10      lose cover RAM: 246M
[    0.000000] *BAD*gran_size: 128K     chunk_size: 16M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 128K     chunk_size: 32M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 128K     chunk_size: 64M     num_reg: 10      lose cover RAM: -8M
[    0.000000]  gran_size: 128K     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 128K     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 128K     chunk_size: 512M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 128K     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 128K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 256K     chunk_size: 256K     num_reg: 10      lose cover RAM: 246M
[    0.000000]  gran_size: 256K     chunk_size: 512K     num_reg: 10      lose cover RAM: 246M
[    0.000000]  gran_size: 256K     chunk_size: 1M     num_reg: 10      lose cover RAM: 246M
[    0.000000]  gran_size: 256K     chunk_size: 2M     num_reg: 10      lose cover RAM: 246M
[    0.000000]  gran_size: 256K     chunk_size: 4M     num_reg: 10      lose cover RAM: 246M
[    0.000000]  gran_size: 256K     chunk_size: 8M     num_reg: 10      lose cover RAM: 246M
[    0.000000] *BAD*gran_size: 256K     chunk_size: 16M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 256K     chunk_size: 32M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 256K     chunk_size: 64M     num_reg: 10      lose cover RAM: -8M
[    0.000000]  gran_size: 256K     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 256K     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 256K     chunk_size: 512M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 256K     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 256K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 512K     chunk_size: 512K     num_reg: 10      lose cover RAM: 246M
[    0.000000]  gran_size: 512K     chunk_size: 1M     num_reg: 10      lose cover RAM: 246M
[    0.000000]  gran_size: 512K     chunk_size: 2M     num_reg: 10      lose cover RAM: 246M
[    0.000000]  gran_size: 512K     chunk_size: 4M     num_reg: 10      lose cover RAM: 246M
[    0.000000]  gran_size: 512K     chunk_size: 8M     num_reg: 10      lose cover RAM: 246M
[    0.000000] *BAD*gran_size: 512K     chunk_size: 16M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 512K     chunk_size: 32M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 512K     chunk_size: 64M     num_reg: 10      lose cover RAM: -8M
[    0.000000]  gran_size: 512K     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 512K     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 512K     chunk_size: 512M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 512K     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 512K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 1M     chunk_size: 1M     num_reg: 10      lose cover RAM: 246M
[    0.000000]  gran_size: 1M     chunk_size: 2M     num_reg: 10      lose cover RAM: 246M
[    0.000000]  gran_size: 1M     chunk_size: 4M     num_reg: 10      lose cover RAM: 246M
[    0.000000]  gran_size: 1M     chunk_size: 8M     num_reg: 10      lose cover RAM: 246M
[    0.000000] *BAD*gran_size: 1M     chunk_size: 16M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 1M     chunk_size: 32M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 1M     chunk_size: 64M     num_reg: 10      lose cover RAM: -8M
[    0.000000]  gran_size: 1M     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 1M     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 1M     chunk_size: 512M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 1M     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 1M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 2M     chunk_size: 2M     num_reg: 10      lose cover RAM: 246M
[    0.000000]  gran_size: 2M     chunk_size: 4M     num_reg: 10      lose cover RAM: 246M
[    0.000000]  gran_size: 2M     chunk_size: 8M     num_reg: 10      lose cover RAM: 246M
[    0.000000] *BAD*gran_size: 2M     chunk_size: 16M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 2M     chunk_size: 32M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 2M     chunk_size: 64M     num_reg: 10      lose cover RAM: -8M
[    0.000000]  gran_size: 2M     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 2M     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 2M     chunk_size: 512M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 2M     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 2M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 4M     chunk_size: 4M     num_reg: 10      lose cover RAM: 246M
[    0.000000]  gran_size: 4M     chunk_size: 8M     num_reg: 10      lose cover RAM: 246M
[    0.000000] *BAD*gran_size: 4M     chunk_size: 16M     num_reg: 10      lose cover RAM: -6M
[    0.000000] *BAD*gran_size: 4M     chunk_size: 32M     num_reg: 10      lose cover RAM: -6M
[    0.000000] *BAD*gran_size: 4M     chunk_size: 64M     num_reg: 10      lose cover RAM: -6M
[    0.000000]  gran_size: 4M     chunk_size: 128M     num_reg: 10      lose cover RAM: 2M
[    0.000000]  gran_size: 4M     chunk_size: 256M     num_reg: 10      lose cover RAM: 2M
[    0.000000]  gran_size: 4M     chunk_size: 512M     num_reg: 10      lose cover RAM: 2M
[    0.000000]  gran_size: 4M     chunk_size: 1G     num_reg: 10      lose cover RAM: 2M
[    0.000000] *BAD*gran_size: 4M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1022M
[    0.000000]  gran_size: 8M     chunk_size: 8M     num_reg: 10      lose cover RAM: 246M
[    0.000000]  gran_size: 8M     chunk_size: 16M     num_reg: 10      lose cover RAM: 118M
[    0.000000]  gran_size: 8M     chunk_size: 32M     num_reg: 10      lose cover RAM: 6M
[    0.000000]  gran_size: 8M     chunk_size: 64M     num_reg: 10      lose cover RAM: 6M
[    0.000000]  gran_size: 8M     chunk_size: 128M     num_reg: 9      lose cover RAM: 6M
[    0.000000]  gran_size: 8M     chunk_size: 256M     num_reg: 9      lose cover RAM: 6M
[    0.000000]  gran_size: 8M     chunk_size: 512M     num_reg: 9      lose cover RAM: 6M
[    0.000000]  gran_size: 8M     chunk_size: 1G     num_reg: 9      lose cover RAM: 6M
[    0.000000]  gran_size: 8M     chunk_size: 2G     num_reg: 10      lose cover RAM: 6M
[    0.000000]  gran_size: 16M     chunk_size: 16M     num_reg: 10      lose cover RAM: 126M
[    0.000000]  gran_size: 16M     chunk_size: 32M     num_reg: 10      lose cover RAM: 14M
[    0.000000]  gran_size: 16M     chunk_size: 64M     num_reg: 10      lose cover RAM: 14M
[    0.000000]  gran_size: 16M     chunk_size: 128M     num_reg: 9      lose cover RAM: 14M
[    0.000000]  gran_size: 16M     chunk_size: 256M     num_reg: 9      lose cover RAM: 14M
[    0.000000]  gran_size: 16M     chunk_size: 512M     num_reg: 9      lose cover RAM: 14M
[    0.000000]  gran_size: 16M     chunk_size: 1G     num_reg: 9      lose cover RAM: 14M
[    0.000000]  gran_size: 16M     chunk_size: 2G     num_reg: 10      lose cover RAM: 14M
[    0.000000]  gran_size: 32M     chunk_size: 32M     num_reg: 10      lose cover RAM: 78M
[    0.000000]  gran_size: 32M     chunk_size: 64M     num_reg: 10      lose cover RAM: 46M
[    0.000000]  gran_size: 32M     chunk_size: 128M     num_reg: 9      lose cover RAM: 46M
[    0.000000]  gran_size: 32M     chunk_size: 256M     num_reg: 9      lose cover RAM: 46M
[    0.000000]  gran_size: 32M     chunk_size: 512M     num_reg: 9      lose cover RAM: 46M
[    0.000000]  gran_size: 32M     chunk_size: 1G     num_reg: 9      lose cover RAM: 46M
[    0.000000]  gran_size: 32M     chunk_size: 2G     num_reg: 10      lose cover RAM: 46M
[    0.000000]  gran_size: 64M     chunk_size: 64M     num_reg: 9      lose cover RAM: 110M
[    0.000000]  gran_size: 64M     chunk_size: 128M     num_reg: 8      lose cover RAM: 110M
[    0.000000]  gran_size: 64M     chunk_size: 256M     num_reg: 8      lose cover RAM: 110M
[    0.000000]  gran_size: 64M     chunk_size: 512M     num_reg: 8      lose cover RAM: 110M
[    0.000000]  gran_size: 64M     chunk_size: 1G     num_reg: 8      lose cover RAM: 110M
[    0.000000]  gran_size: 64M     chunk_size: 2G     num_reg: 9      lose cover RAM: 110M
[    0.000000]  gran_size: 128M     chunk_size: 128M     num_reg: 8      lose cover RAM: 174M
[    0.000000]  gran_size: 128M     chunk_size: 256M     num_reg: 8      lose cover RAM: 174M
[    0.000000]  gran_size: 128M     chunk_size: 512M     num_reg: 8      lose cover RAM: 174M
[    0.000000]  gran_size: 128M     chunk_size: 1G     num_reg: 8      lose cover RAM: 174M
[    0.000000]  gran_size: 128M     chunk_size: 2G     num_reg: 9      lose cover RAM: 174M
[    0.000000]  gran_size: 256M     chunk_size: 256M     num_reg: 6      lose cover RAM: 430M
[    0.000000]  gran_size: 256M     chunk_size: 512M     num_reg: 8      lose cover RAM: 430M
[    0.000000]  gran_size: 256M     chunk_size: 1G     num_reg: 8      lose cover RAM: 430M
[    0.000000]  gran_size: 256M     chunk_size: 2G     num_reg: 9      lose cover RAM: 430M
[    0.000000]  gran_size: 512M     chunk_size: 512M     num_reg: 4      lose cover RAM: 942M
[    0.000000]  gran_size: 512M     chunk_size: 1G     num_reg: 4      lose cover RAM: 942M
[    0.000000]  gran_size: 512M     chunk_size: 2G     num_reg: 4      lose cover RAM: 942M
[    0.000000]  gran_size: 1G     chunk_size: 1G     num_reg: 4      lose cover RAM: 942M
[    0.000000]  gran_size: 1G     chunk_size: 2G     num_reg: 4      lose cover RAM: 942M
[    0.000000]  gran_size: 2G     chunk_size: 2G     num_reg: 3      lose cover RAM: 1966M
[    0.000000] mtrr_cleanup: can not find optimal value
[    0.000000] please specify mtrr_gran_size/mtrr_chunk_size
[    0.000000] e820: update [mem 0xdb800000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xdb000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fd7f0-0x000fd7ff] mapped at [ffff8800000fd7f0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fe1000, 0x01fe1fff] PGTABLE
[    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
[    0.000000] BRK [0x01fe3000, 0x01fe3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x41f400000-0x41f5fffff]
[    0.000000]  [mem 0x41f400000-0x41f5fffff] page 2M
[    0.000000] BRK [0x01fe4000, 0x01fe4fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x41c000000-0x41f3fffff]
[    0.000000]  [mem 0x41c000000-0x41f3fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x400000000-0x41bffffff]
[    0.000000]  [mem 0x400000000-0x41bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x1fffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x1fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x20200000-0x40003fff]
[    0.000000]  [mem 0x20200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0x40003fff] page 4k
[    0.000000] BRK [0x01fe5000, 0x01fe5fff] PGTABLE
[    0.000000] BRK [0x01fe6000, 0x01fe6fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x40005000-0xd99e3fff]
[    0.000000]  [mem 0x40005000-0x401fffff] page 4k
[    0.000000]  [mem 0x40200000-0xd97fffff] page 2M
[    0.000000]  [mem 0xd9800000-0xd99e3fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xd9e63000-0xd9eeefff]
[    0.000000]  [mem 0xd9e63000-0xd9eeefff] page 4k
[    0.000000] init_memory_mapping: [mem 0xda5f7000-0xda5f7fff]
[    0.000000]  [mem 0xda5f7000-0xda5f7fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xda63b000-0xdad80fff]
[    0.000000]  [mem 0xda63b000-0xda7fffff] page 4k
[    0.000000]  [mem 0xda800000-0xdabfffff] page 2M
[    0.000000]  [mem 0xdac00000-0xdad80fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xdaff3000-0xdaffffff]
[    0.000000]  [mem 0xdaff3000-0xdaffffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x3ffffffff]
[    0.000000]  [mem 0x100000000-0x3ffffffff] page 2M
[    0.000000] RAMDISK: [mem 0x35988000-0x36cbbfff]
[    0.000000] ACPI: RSDP 00000000000f0490 000024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 00000000d9f81078 00006C (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 00000000d9f8bc50 00010C (v05 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 00000000d9f81178 00AAD7 (v02 ALASKA    A M I 00000023 INTL 20051117)
[    0.000000] ACPI: FACS 00000000d9f90080 000040
[    0.000000] ACPI: APIC 00000000d9f8bd60 000092 (v03 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 00000000d9f8bdf8 000044 (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 00000000d9f8be40 00003C (v01 ALASKA    A M I 01072009 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000d9f8be80 000F92 (v01 TrmRef PtidDevc 00001000 INTL 20091112)
[    0.000000] ACPI: HPET 00000000d9f8ce18 000038 (v01 ALASKA    A M I 01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT 00000000d9f8ce50 000315 (v01 SataRe SataTabl 00001000 INTL 20091112)
[    0.000000] ACPI: SSDT 00000000d9f8d168 000926 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 00000000d9f8da90 000B22 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000041f5fffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x41f5fffff]
[    0.000000]   NODE_DATA [mem 0x41f5e7000-0x41f5ebfff]
[    0.000000]  [ffffea0000000000-ffffea00107fffff] PMD -> [ffff88040ec00000-ffff88041ebfffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x41f5fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009cfff]
[    0.000000]   node   0: [mem 0x00100000-0x1fffffff]
[    0.000000]   node   0: [mem 0x20200000-0x40003fff]
[    0.000000]   node   0: [mem 0x40005000-0xd99e3fff]
[    0.000000]   node   0: [mem 0xd9e63000-0xd9eeefff]
[    0.000000]   node   0: [mem 0xda5f7000-0xda5f7fff]
[    0.000000]   node   0: [mem 0xda63b000-0xdad80fff]
[    0.000000]   node   0: [mem 0xdaff3000-0xdaffffff]
[    0.000000]   node   0: [mem 0x100000000-0x41f5fffff]
[    0.000000] On node 0 totalpages: 4167007
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 13888 pages used for memmap
[    0.000000]   DMA32 zone: 888771 pages, LIFO batch:31
[    0.000000]   Normal zone: 51160 pages used for memmap
[    0.000000]   Normal zone: 3274240 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
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
[    0.000000] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x20000000-0x201fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x40004000-0x40004fff]
[    0.000000] PM: Registered nosave memory: [mem 0xd99e4000-0xd9e62fff]
[    0.000000] PM: Registered nosave memory: [mem 0xd9eef000-0xd9f91fff]
[    0.000000] PM: Registered nosave memory: [mem 0xd9f92000-0xda5f6fff]
[    0.000000] PM: Registered nosave memory: [mem 0xda5f8000-0xda63afff]
[    0.000000] PM: Registered nosave memory: [mem 0xdad81000-0xdaff2fff]
[    0.000000] PM: Registered nosave memory: [mem 0xdb000000-0xdb7fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xdb800000-0xdf9fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xdfa00000-0xf7ffffff]
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
[    0.000000] e820: [mem 0xdfa00000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88041f200000 s82368 r8192 d24128 u262144
[    0.000000] pcpu-alloc: s82368 r8192 d24128 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 4101874
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-46-generic root=UUID=6fb59d06-ec00-44f4-abcc-0da0f018be93 ro quiet splash acpi_os_name=Linux acpi_osi= vt.handoff=7
[    0.000000] ACPI: _OSI method disabled
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 16302548K/16668028K available (7384K kernel code, 1145K rwdata, 3408K rodata, 1336K init, 1444K bss, 365480K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-7.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 67108864 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 2394.685 MHz processor
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 4789.37 BogoMIPS (lpj=9578740)
[    0.000005] pid_max: default: 32768 minimum: 301
[    0.000029] Security Framework initialized
[    0.000045] AppArmor: AppArmor initialized
[    0.000046] Yama: becoming mindful.
[    0.001094] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.005222] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.007051] Mount-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.007069] Mountpoint-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.007290] Initializing cgroup subsys memory
[    0.007295] Initializing cgroup subsys devices
[    0.007297] Initializing cgroup subsys freezer
[    0.007298] Initializing cgroup subsys blkio
[    0.007299] Initializing cgroup subsys perf_event
[    0.007301] Initializing cgroup subsys hugetlb
[    0.007321] CPU: Physical Processor ID: 0
[    0.007322] CPU: Processor Core ID: 0
[    0.007327] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.007327] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.007700] mce: CPU supports 9 MCE banks
[    0.007713] CPU0: Thermal monitoring enabled (TM1)
[    0.007724] Last level iTLB entries: 4KB 512, 2MB 0, 4MB 0
[    0.007724] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32
[    0.007724] tlb_flushall_shift: 2
[    0.007847] Freeing SMP alternatives memory: 32K (ffffffff81e6e000 - ffffffff81e76000)
[    0.009028] ACPI: Core revision 20131115
[    0.009046] ACPI: Overriding _OS definition to 'Linux'
[    0.013942] ACPI: All ACPI Tables successfully acquired
[    0.026785] ftrace: allocating 28563 entries in 112 pages
[    0.040745] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.080466] smpboot: CPU0: Intel(R) Core(TM) i7-3630QM CPU @ 2.40GHz (fam: 06, model: 3a, stepping: 09)
[    0.080472] TSC deadline timer enabled
[    0.080480] Performance Events: PEBS fmt1+, 16-deep LBR, IvyBridge events, full-width counters, Intel PMU driver.
[    0.080486] ... version:                3
[    0.080486] ... bit width:              48
[    0.080487] ... generic registers:      4
[    0.080488] ... value mask:             0000ffffffffffff
[    0.080489] ... max period:             0000ffffffffffff
[    0.080490] ... fixed-purpose events:   3
[    0.080491] ... event mask:             000000070000000f
[    0.081996] x86: Booting SMP configuration:
[    0.095514] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.081998] .... node  #0, CPUs:      #1 #2 #3 #4 #5 #6 #7
[    0.177306] x86: Booted up 1 node, 8 CPUs
[    0.177310] smpboot: Total of 8 processors activated (38314.96 BogoMIPS)
[    0.184426] devtmpfs: initialized
[    0.187402] EVM: security.selinux
[    0.187403] EVM: security.SMACK64
[    0.187404] EVM: security.ima
[    0.187405] EVM: security.capability
[    0.187454] PM: Registering ACPI NVS region [mem 0xd9eef000-0xd9f91fff] (667648 bytes)
[    0.187463] PM: Registering ACPI NVS region [mem 0xda5f8000-0xda63afff] (274432 bytes)
[    0.188222] pinctrl core: initialized pinctrl subsystem
[    0.188274] regulator-dummy: no parameters
[    0.188304] RTC time:  8:39:46, date: 03/02/15
[    0.188333] NET: Registered protocol family 16
[    0.188434] cpuidle: using governor ladder
[    0.188435] cpuidle: using governor menu
[    0.188477] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.188479] ACPI: bus type PCI registered
[    0.188480] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.188530] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.188532] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.195828] PCI: Using configuration type 1 for base access
[    0.196761] bio: create slab <bio-0> at 0
[    0.196901] ACPI: Added _OSI(Module Device)
[    0.196903] ACPI: Added _OSI(Processor Device)
[    0.196904] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.196905] ACPI: Added _OSI(Processor Aggregator Device)
[    0.199336] ACPI: Executed 1 blocks of module-level executable AML code
[    0.204710] ACPI: SSDT 00000000d9e10018 00083B (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.205024] ACPI: Dynamic OEM Table Load:
[    0.205026] ACPI: SSDT           (null) 00083B (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.208452] ACPI: SSDT 00000000d9e11a98 000303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.208787] ACPI: Dynamic OEM Table Load:
[    0.208789] ACPI: SSDT           (null) 000303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.212343] ACPI: SSDT 00000000d9e12c18 000119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.212648] ACPI: Dynamic OEM Table Load:
[    0.212649] ACPI: SSDT           (null) 000119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    1.882643] ACPI: Interpreter enabled
[    1.882655] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    1.882663] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    1.882691] ACPI: (supports S0 S3 S4 S5)
[    1.882693] ACPI: Using IOAPIC for interrupt routing
[    1.882714] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.882857] ACPI: No dock devices found.
[    1.891095] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    1.891100] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    1.891152] ACPI Error: [_OSI] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
[    1.891156] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node ffff880408cedde8), AE_NOT_FOUND (20131115/psparse-536)
[    1.891163] acpi PNP0A08:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    1.891700] PCI host bridge to bus 0000:00
[    1.891702] pci_bus 0000:00: root bus resource [bus 00-3e]
[    1.891704] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    1.891706] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    1.891707] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    1.891709] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    1.891710] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    1.891712] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    1.891713] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    1.891715] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    1.891716] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    1.891718] pci_bus 0000:00: root bus resource [mem 0xdfa00000-0xfeafffff]
[    1.891725] pci 0000:00:00.0: [8086:0154] type 00 class 0x060000
[    1.891807] pci 0000:00:02.0: [8086:0166] type 00 class 0x030000
[    1.891817] pci 0000:00:02.0: reg 0x10: [mem 0xf7800000-0xf7bfffff 64bit]
[    1.891823] pci 0000:00:02.0: reg 0x18: [mem 0xe0000000-0xefffffff 64bit pref]
[    1.891827] pci 0000:00:02.0: reg 0x20: [io  0xf000-0xf03f]
[    1.891926] pci 0000:00:14.0: [8086:1e31] type 00 class 0x0c0330
[    1.891948] pci 0000:00:14.0: reg 0x10: [mem 0xf7e00000-0xf7e0ffff 64bit]
[    1.892020] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    1.892066] pci 0000:00:14.0: System wakeup disabled by ACPI
[    1.892095] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
[    1.892118] pci 0000:00:16.0: reg 0x10: [mem 0xf7e1a000-0xf7e1a00f 64bit]
[    1.892194] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    1.892274] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
[    1.892295] pci 0000:00:1a.0: reg 0x10: [mem 0xf7e18000-0xf7e183ff]
[    1.892385] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    1.892444] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    1.892474] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
[    1.892489] pci 0000:00:1b.0: reg 0x10: [mem 0xf7e10000-0xf7e13fff 64bit]
[    1.892557] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.892605] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    1.892632] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
[    1.892712] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.892762] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    1.892789] pci 0000:00:1c.2: [8086:1e14] type 01 class 0x060400
[    1.892868] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    1.892918] pci 0000:00:1c.2: System wakeup disabled by ACPI
[    1.892943] pci 0000:00:1c.3: [8086:1e16] type 01 class 0x060400
[    1.893022] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    1.893072] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    1.893104] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
[    1.893125] pci 0000:00:1d.0: reg 0x10: [mem 0xf7e17000-0xf7e173ff]
[    1.893216] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    1.893273] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    1.893302] pci 0000:00:1f.0: [8086:1e59] type 00 class 0x060100
[    1.893472] pci 0000:00:1f.2: [8086:1e03] type 00 class 0x010601
[    1.893490] pci 0000:00:1f.2: reg 0x10: [io  0xf0b0-0xf0b7]
[    1.893498] pci 0000:00:1f.2: reg 0x14: [io  0xf0a0-0xf0a3]
[    1.893505] pci 0000:00:1f.2: reg 0x18: [io  0xf090-0xf097]
[    1.893513] pci 0000:00:1f.2: reg 0x1c: [io  0xf080-0xf083]
[    1.893520] pci 0000:00:1f.2: reg 0x20: [io  0xf060-0xf07f]
[    1.893528] pci 0000:00:1f.2: reg 0x24: [mem 0xf7e16000-0xf7e167ff]
[    1.893573] pci 0000:00:1f.2: PME# supported from D3hot
[    1.893638] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
[    1.893653] pci 0000:00:1f.3: reg 0x10: [mem 0xf7e15000-0xf7e150ff 64bit]
[    1.893673] pci 0000:00:1f.3: reg 0x20: [io  0xf040-0xf05f]
[    1.893805] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    1.893913] pci 0000:02:00.0: [8086:08b1] type 00 class 0x028000
[    1.893961] pci 0000:02:00.0: reg 0x10: [mem 0xf7d00000-0xf7d01fff 64bit]
[    1.894162] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    1.894213] pci 0000:02:00.0: System wakeup disabled by ACPI
[    1.898700] pci 0000:00:1c.2: PCI bridge to [bus 02]
[    1.898717] pci 0000:00:1c.2:   bridge window [mem 0xf7d00000-0xf7dfffff]
[    1.898894] pci 0000:03:00.0: [10ec:5289] type 00 class 0xff0000
[    1.898953] pci 0000:03:00.0: reg 0x10: [mem 0xf7c00000-0xf7c0ffff]
[    1.899464] pci 0000:03:00.0: supports D1 D2
[    1.899465] pci 0000:03:00.0: PME# supported from D1 D2 D3hot D3cold
[    1.899565] pci 0000:03:00.0: System wakeup disabled by ACPI
[    1.899660] pci 0000:03:00.2: [10ec:8168] type 00 class 0x020000
[    1.899722] pci 0000:03:00.2: reg 0x10: [io  0xe000-0xe0ff]
[    1.899834] pci 0000:03:00.2: reg 0x18: [mem 0xf0004000-0xf0004fff 64bit pref]
[    1.899898] pci 0000:03:00.2: reg 0x20: [mem 0xf0000000-0xf0003fff 64bit pref]
[    1.900200] pci 0000:03:00.2: supports D1 D2
[    1.900201] pci 0000:03:00.2: PME# supported from D0 D1 D2 D3hot D3cold
[    1.900335] pci 0000:03:00.2: System wakeup disabled by ACPI
[    1.906741] pci 0000:00:1c.3: PCI bridge to [bus 03]
[    1.906745] pci 0000:00:1c.3:   bridge window [io  0xe000-0xefff]
[    1.906749] pci 0000:00:1c.3:   bridge window [mem 0xf7c00000-0xf7cfffff]
[    1.906755] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    1.907261] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    1.907306] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.907350] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 10 11 12 14 15)
[    1.907393] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *10 11 12 14 15)
[    1.907435] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.907477] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.907520] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 10 11 12 14 15)
[    1.907562] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 5 6 10 11 12 14 15)
[    1.908123] ACPI: Enabled 5 GPEs in block 00 to 3F
[    1.908130] ACPI: \_SB_.PCI0: notify handler is installed
[    1.908180] Found 1 acpi root devices
[    1.908210] ACPI : EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    1.908284] vgaarb: setting as boot device: PCI:0000:00:02.0
[    1.908285] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    1.908288] vgaarb: loaded
[    1.908289] vgaarb: bridge control possible 0000:00:02.0
[    1.908413] SCSI subsystem initialized
[    1.908451] libata version 3.00 loaded.
[    1.908466] ACPI: bus type USB registered
[    1.908479] usbcore: registered new interface driver usbfs
[    1.908486] usbcore: registered new interface driver hub
[    1.908502] usbcore: registered new device driver usb
[    1.908588] PCI: Using ACPI for IRQ routing
[    1.910175] PCI: pci_cache_line_size set to 64 bytes
[    1.910240] e820: reserve RAM buffer [mem 0x0009d800-0x0009ffff]
[    1.910242] e820: reserve RAM buffer [mem 0x40004000-0x43ffffff]
[    1.910243] e820: reserve RAM buffer [mem 0xd99e4000-0xdbffffff]
[    1.910245] e820: reserve RAM buffer [mem 0xd9eef000-0xdbffffff]
[    1.910247] e820: reserve RAM buffer [mem 0xda5f8000-0xdbffffff]
[    1.910248] e820: reserve RAM buffer [mem 0xdad81000-0xdbffffff]
[    1.910250] e820: reserve RAM buffer [mem 0xdb000000-0xdbffffff]
[    1.910251] e820: reserve RAM buffer [mem 0x41f600000-0x41fffffff]
[    1.910316] NetLabel: Initializing
[    1.910317] NetLabel:  domain hash size = 128
[    1.910318] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.910330] NetLabel:  unlabeled traffic allowed by default
[    1.910385] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    1.910389] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    1.912425] Switched to clocksource hpet
[    1.916233] AppArmor: AppArmor Filesystem Enabled
[    1.916252] pnp: PnP ACPI init
[    1.916263] ACPI: bus type PNP registered
[    1.916329] system 00:00: [mem 0xfed40000-0xfed44fff] has been reserved
[    1.916333] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    1.916356] pnp 00:01: [dma 4]
[    1.916370] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.916385] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    1.916469] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    1.916504] system 00:04: [io  0x0680-0x069f] has been reserved
[    1.916506] system 00:04: [io  0x1000-0x100f] has been reserved
[    1.916507] system 00:04: [io  0xffff] has been reserved
[    1.916509] system 00:04: [io  0xffff] has been reserved
[    1.916511] system 00:04: [io  0x0400-0x0453] could not be reserved
[    1.916512] system 00:04: [io  0x0458-0x047f] has been reserved
[    1.916514] system 00:04: [io  0x0500-0x057f] has been reserved
[    1.916516] system 00:04: [io  0x164e-0x164f] has been reserved
[    1.916517] system 00:04: [io  0x3322-0x3323] has been reserved
[    1.916519] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.916543] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.916580] system 00:06: [io  0x0454-0x0457] has been reserved
[    1.916582] system 00:06: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    1.916609] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    1.916666] pnp 00:08: Plug and Play ACPI device, IDs ETD0403 PNP0f13 (active)
[    1.916705] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    1.916708] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.916729] pnp 00:0a: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.916963] system 00:0b: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    1.916965] system 00:0b: [mem 0xfed10000-0xfed17fff] has been reserved
[    1.916967] system 00:0b: [mem 0xfed18000-0xfed18fff] has been reserved
[    1.916969] system 00:0b: [mem 0xfed19000-0xfed19fff] has been reserved
[    1.916971] system 00:0b: [mem 0xf8000000-0xfbffffff] has been reserved
[    1.916972] system 00:0b: [mem 0xfed20000-0xfed3ffff] has been reserved
[    1.916974] system 00:0b: [mem 0xfed90000-0xfed93fff] has been reserved
[    1.916976] system 00:0b: [mem 0xfed45000-0xfed8ffff] has been reserved
[    1.916978] system 00:0b: [mem 0xff000000-0xffffffff] has been reserved
[    1.916979] system 00:0b: [mem 0xfee00000-0xfeefffff] could not be reserved
[    1.916981] system 00:0b: [mem 0xdfa00000-0xdfa00fff] has been reserved
[    1.916983] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.917115] system 00:0c: [mem 0x20000000-0x201fffff] has been reserved
[    1.917117] system 00:0c: [mem 0x40004000-0x40004fff] has been reserved
[    1.917119] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    1.917540] pnp: PnP ACPI: found 13 devices
[    1.917541] ACPI: bus type PNP unregistered
[    1.923535] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    1.923547] pci 0000:00:1c.2: PCI bridge to [bus 02]
[    1.923552] pci 0000:00:1c.2:   bridge window [mem 0xf7d00000-0xf7dfffff]
[    1.923560] pci 0000:00:1c.3: PCI bridge to [bus 03]
[    1.923563] pci 0000:00:1c.3:   bridge window [io  0xe000-0xefff]
[    1.923567] pci 0000:00:1c.3:   bridge window [mem 0xf7c00000-0xf7cfffff]
[    1.923571] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    1.923577] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.923579] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.923581] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.923582] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    1.923584] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    1.923585] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    1.923587] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    1.923589] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
[    1.923590] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
[    1.923592] pci_bus 0000:00: resource 13 [mem 0xdfa00000-0xfeafffff]
[    1.923594] pci_bus 0000:02: resource 1 [mem 0xf7d00000-0xf7dfffff]
[    1.923596] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    1.923597] pci_bus 0000:03: resource 1 [mem 0xf7c00000-0xf7cfffff]
[    1.923599] pci_bus 0000:03: resource 2 [mem 0xf0000000-0xf00fffff 64bit pref]
[    1.923622] NET: Registered protocol family 2
[    1.923828] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.924057] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.924173] TCP: Hash tables configured (established 131072 bind 65536)
[    1.924187] TCP: reno registered
[    1.924204] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    1.924256] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    1.924334] NET: Registered protocol family 1
[    1.924343] pci 0000:00:02.0: Video device with shadowed ROM
[    1.924792] PCI: CLS 64 bytes, default 64
[    1.924836] Trying to unpack rootfs image as initramfs...
[    2.224245] Freeing initrd memory: 19664K (ffff880035988000 - ffff880036cbc000)
[    2.224249] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    2.224252] software IO TLB [mem 0xd59e4000-0xd99e4000] (64MB) mapped at [ffff8800d59e4000-ffff8800d99e3fff]
[    2.224541] microcode: CPU0 sig=0x306a9, pf=0x10, revision=0x15
[    2.224548] microcode: CPU1 sig=0x306a9, pf=0x10, revision=0x15
[    2.224556] microcode: CPU2 sig=0x306a9, pf=0x10, revision=0x15
[    2.224562] microcode: CPU3 sig=0x306a9, pf=0x10, revision=0x15
[    2.224568] microcode: CPU4 sig=0x306a9, pf=0x10, revision=0x15
[    2.224575] microcode: CPU5 sig=0x306a9, pf=0x10, revision=0x15
[    2.224580] microcode: CPU6 sig=0x306a9, pf=0x10, revision=0x15
[    2.224585] microcode: CPU7 sig=0x306a9, pf=0x10, revision=0x15
[    2.224629] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    2.224631] Scanning for low memory corruption every 60 seconds
[    2.224864] Initialise system trusted keyring
[    2.224904] audit: initializing netlink socket (disabled)
[    2.224913] type=2000 audit(1425285587.208:1): initialized
[    2.251281] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    2.252293] zbud: loaded
[    2.252423] VFS: Disk quotas dquot_6.5.2
[    2.252456] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    2.252797] fuse init (API version 7.22)
[    2.252854] msgmni has been set to 31879
[    2.252896] Key type big_key registered
[    2.253273] Key type asymmetric registered
[    2.253274] Asymmetric key parser 'x509' registered
[    2.253297] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    2.253339] io scheduler noop registered
[    2.253340] io scheduler deadline registered (default)
[    2.253360] io scheduler cfq registered
[    2.253751] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.253762] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.253791] vesafb: mode is 1920x1080x32, linelength=7680, pages=0
[    2.253792] vesafb: scrolling: redraw
[    2.253793] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    2.254803] vesafb: framebuffer at 0xe0000000, mapped to 0xffffc90005c00000, using 8128k, total 8128k
[    2.402493] Console: switching to colour frame buffer device 240x67
[    2.549582] fb0: VESA VGA frame buffer device
[    2.549595] intel_idle: MWAIT substates: 0x21120
[    2.549596] intel_idle: v0.4 model 0x3A
[    2.549597] intel_idle: lapic_timer_reliable_states 0xffffffff
[    2.549749] ipmi message handler version 39.2
[    2.549780] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    2.549811] ACPI: AC Adapter [AC] (on-line)
[    2.549886] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    2.549891] ACPI: Power Button [PWRB]
[    2.549914] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    2.549917] ACPI: Sleep Button [SLPB]
[    2.549941] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    2.550316] ACPI: Lid Switch [LID0]
[    2.550346] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    2.550348] ACPI: Power Button [PWRF]
[    2.553009] thermal LNXTHERM:00: registered as thermal_zone0
[    2.553010] ACPI: Thermal Zone [TZ0] (68 C)
[    2.553035] GHES: HEST is not enabled!
[    2.553127] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    2.557404] Linux agpgart interface v0.103
[    2.558722] brd: module loaded
[    2.559257] loop: module loaded
[    2.559527] libphy: Fixed MDIO Bus: probed
[    2.559592] tun: Universal TUN/TAP device driver, 1.6
[    2.559593] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.559630] PPP generic driver version 2.4.2
[    2.559666] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.559669] ehci-pci: EHCI PCI platform driver
[    2.559768] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    2.559775] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.559797] ehci-pci 0000:00:1a.0: debug port 2
[    2.561644] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    2.561650] ACPI: Battery Slot [BAT0] (battery present)
[    2.563709] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    2.563723] ehci-pci 0000:00:1a.0: irq 16, io mem 0xf7e18000
[    2.573000] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    2.573033] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    2.573035] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.573036] usb usb1: Product: EHCI Host Controller
[    2.573038] usb usb1: Manufacturer: Linux 3.13.0-46-generic ehci_hcd
[    2.573039] usb usb1: SerialNumber: 0000:00:1a.0
[    2.573152] hub 1-0:1.0: USB hub found
[    2.573158] hub 1-0:1.0: 2 ports detected
[    2.573310] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    2.573314] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.573325] ehci-pci 0000:00:1d.0: debug port 2
[    2.577209] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    2.577220] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf7e17000
[    2.589011] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    2.589046] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    2.589047] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.589049] usb usb2: Product: EHCI Host Controller
[    2.589050] usb usb2: Manufacturer: Linux 3.13.0-46-generic ehci_hcd
[    2.589052] usb usb2: SerialNumber: 0000:00:1d.0
[    2.589198] hub 2-0:1.0: USB hub found
[    2.589206] hub 2-0:1.0: 2 ports detected
[    2.589281] ehci-platform: EHCI generic platform driver
[    2.589287] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.589288] ohci-pci: OHCI PCI platform driver
[    2.589296] ohci-platform: OHCI generic platform driver
[    2.589300] uhci_hcd: USB Universal Host Controller Interface driver
[    2.589404] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    2.589408] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    2.589494] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    2.589514] xhci_hcd 0000:00:14.0: irq 40 for MSI/MSI-X
[    2.589570] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    2.589572] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.589573] usb usb3: Product: xHCI Host Controller
[    2.589575] usb usb3: Manufacturer: Linux 3.13.0-46-generic xhci_hcd
[    2.589576] usb usb3: SerialNumber: 0000:00:14.0
[    2.589720] hub 3-0:1.0: USB hub found
[    2.589733] hub 3-0:1.0: 4 ports detected
[    2.590008] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    2.590011] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    2.590043] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    2.590045] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.590047] usb usb4: Product: xHCI Host Controller
[    2.590048] usb usb4: Manufacturer: Linux 3.13.0-46-generic xhci_hcd
[    2.590049] usb usb4: SerialNumber: 0000:00:14.0
[    2.590195] hub 4-0:1.0: USB hub found
[    2.590206] hub 4-0:1.0: 4 ports detected
[    2.597230] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:ELNM] at 0x60,0x64 irq 1,12
[    2.600337] i8042: Detected active multiplexing controller, rev 1.1
[    2.602286] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.602293] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.602318] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.602331] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.602345] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.602568] mousedev: PS/2 mouse device common for all mice
[    2.603092] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.603120] rtc_cmos 00:05: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    2.603177] device-mapper: uevent: version 1.0.3
[    2.603227] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    2.603235] ledtrig-cpu: registered to indicate activity on CPUs
[    2.603327] TCP: cubic registered
[    2.603395] NET: Registered protocol family 10
[    2.603527] NET: Registered protocol family 17
[    2.603535] Key type dns_resolver registered
[    2.603855] Loading compiled-in X.509 certificates
[    2.604723] Loaded X.509 cert 'Magrathea: Glacier signing key: 61c15846aa32da28b9f1e3be36fac9172aa9622a'
[    2.604742] registered taskstats version 1
[    2.605782] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    2.607272] Key type trusted registered
[    2.611209] Key type encrypted registered
[    2.611213] AppArmor: AppArmor sha1 policy hashing enabled
[    2.611215] IMA: No TPM chip found, activating TPM-bypass!
[    2.611472] regulator-dummy: disabling
[    2.611603]   Magic number: 7:110:674
[    2.611733] rtc_cmos 00:05: setting system clock to 2015-03-02 08:39:48 UTC (1425285588)
[    2.612853] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.612854] EDD information not available.
[    2.612884] PM: Hibernation image not present or could not be loaded.
[    2.613577] Freeing unused kernel memory: 1336K (ffffffff81d20000 - ffffffff81e6e000)
[    2.613578] Write protecting the kernel read-only data: 12288k
[    2.615093] Freeing unused kernel memory: 796K (ffff880001739000 - ffff880001800000)
[    2.616354] Freeing unused kernel memory: 688K (ffff880001b54000 - ffff880001c00000)
[    2.624447] systemd-udevd[145]: starting version 204
[    2.640092] rtsx_pci 0000:03:00.0: irq 41 for MSI/MSI-X
[    2.640107] rtsx_pci 0000:03:00.0: rtsx_pci_acquire_irq: pcr->msi_en = 1, pci->irq = 41
[    2.641470] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.641479] r8169 0000:03:00.2: can't disable ASPM; OS doesn't have ASPM control
[    2.641707] r8169 0000:03:00.2: irq 42 for MSI/MSI-X
[    2.641881] r8169 0000:03:00.2 eth0: RTL8411 at 0xffffc900018ae000, 00:90:f5:d6:73:d1, XID 08800800 IRQ 42
[    2.641883] r8169 0000:03:00.2 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    2.643693] ahci 0000:00:1f.2: version 3.0
[    2.643788] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
[    2.643814] ahci 0000:00:1f.2: SSS flag set, parallel bus scan disabled
[    2.657102] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x15 impl SATA mode
[    2.657107] ahci 0000:00:1f.2: flags: 64bit ncq stag pm led clo pio slum part ems sxs apst 
[    2.673474] scsi0 : ahci
[    2.673600] scsi1 : ahci
[    2.673739] scsi2 : ahci
[    2.673808] scsi3 : ahci
[    2.673856] scsi4 : ahci
[    2.673932] scsi5 : ahci
[    2.673969] ata1: SATA max UDMA/133 abar m2048@0xf7e16000 port 0xf7e16100 irq 43
[    2.673970] ata2: DUMMY
[    2.673972] ata3: SATA max UDMA/133 abar m2048@0xf7e16000 port 0xf7e16200 irq 43
[    2.673973] ata4: DUMMY
[    2.673975] ata5: SATA max UDMA/133 abar m2048@0xf7e16000 port 0xf7e16300 irq 43
[    2.673975] ata6: DUMMY
[    2.885334] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    2.993436] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.014710] ata1.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    3.014719] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    3.014724] ata1.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    3.017819] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    3.017826] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    3.018214] hub 1-1:1.0: USB hub found
[    3.018286] hub 1-1:1.0: 6 ports detected
[    3.025026] ata1.00: ATA-8: ST9750420AS, 0001SDM5, max UDMA/133
[    3.025033] ata1.00: 1465149168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.048291] ata1.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    3.048300] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    3.048304] ata1.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    3.049271] ata1.00: configured for UDMA/133
[    3.049563] scsi 0:0:0:0: Direct-Access     ATA      ST9750420AS      0001 PQ: 0 ANSI: 5
[    3.049757] sd 0:0:0:0: [sda] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[    3.049759] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    3.049797] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.050068] sd 0:0:0:0: [sda] Write Protect is off
[    3.050071] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.050183] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.102290]  sda: sda1 sda2 < sda5 > sda3
[    3.103122] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.129604] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    3.221553] tsc: Refined TSC clocksource calibration: 2394.560 MHz
[    3.261980] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    3.261983] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    3.262278] hub 2-1:1.0: USB hub found
[    3.262363] hub 2-1:1.0: 6 ports detected
[    3.369693] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.373564] ata3.00: ATAPI: TSSTcorp CDDVDW SN-208DB, TC01, max UDMA/100
[    3.375976] ata3.00: configured for UDMA/100
[    3.380932] scsi 2:0:0:0: CD-ROM            TSSTcorp CDDVDW SN-208DB  TC01 PQ: 0 ANSI: 5
[    3.384649] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.384655] cdrom: Uniform CD-ROM driver Revision: 3.20
[    3.384867] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    3.384940] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    3.429794] usb 3-1: new high-speed USB device number 2 using xhci_hcd
[    3.449029] usb 3-1: New USB device found, idVendor=1bcf, idProduct=0c31
[    3.449031] usb 3-1: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[    3.449033] usb 3-1: Product: USB to Serial-ATA bridge
[    3.449035] usb 3-1: Manufacturer: Sunplus Innovation Technology.
[    3.449036] usb 3-1: SerialNumber: FDC0FD100200000FD0FCAFF1769131
[    3.506554] usb-storage 3-1:1.0: USB Mass Storage device detected
[    3.506723] scsi6 : usb-storage 3-1:1.0
[    3.506779] usbcore: registered new interface driver usb-storage
[    3.540690] psmouse serio2: elantech: assuming hardware version 3 (with firmware version 0x250f01)
[    3.617938] usb 3-2: new high-speed USB device number 3 using xhci_hcd
[    3.639878] psmouse serio2: elantech: Synaptics capabilities query result 0x18, 0x17, 0x0b.
[    3.701975] ata5: SATA link down (SStatus 0 SControl 300)
[    3.966789] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio2/input/input10
[    4.222727] Switched to clocksource tsc
[    4.511326] scsi 6:0:0:0: Direct-Access     WDC WD10 02FAEX-00Z3A0         PQ: 0 ANSI: 4
[    4.511729] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    4.512299] sd 6:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    4.518619] sd 6:0:0:0: [sdb] Write Protect is off
[    4.518623] sd 6:0:0:0: [sdb] Mode Sense: 38 00 00 00
[    4.524967] sd 6:0:0:0: [sdb] No Caching mode page found
[    4.524970] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    4.538378] sd 6:0:0:0: [sdb] No Caching mode page found
[    4.538380] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    4.745468] usb 3-2: New USB device found, idVendor=046d, idProduct=082d
[    4.745471] usb 3-2: New USB device strings: Mfr=0, Product=2, SerialNumber=1
[    4.745472] usb 3-2: Product: HD Pro Webcam C920
[    4.745473] usb 3-2: SerialNumber: 8929093F
[    4.911115] usb 3-4: new full-speed USB device number 4 using xhci_hcd
[    4.928321] usb 3-4: New USB device found, idVendor=8087, idProduct=07dc
[    4.928328] usb 3-4: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    4.999243] usb 1-1.2: new full-speed USB device number 3 using ehci-pci
[    5.094408] usb 1-1.2: New USB device found, idVendor=046d, idProduct=c52b
[    5.094415] usb 1-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    5.094419] usb 1-1.2: Product: USB Receiver
[    5.094422] usb 1-1.2: Manufacturer: Logitech
[    5.097434] hidraw: raw HID events driver (C) Jiri Kosina
[    5.102557] usbcore: registered new interface driver usbhid
[    5.102559] usbhid: USB HID core driver
[    5.104987] logitech-djreceiver 0003:046D:C52B.0003: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1a.0-1.2/input2
[    5.108254] input: Logitech Unifying Device. Wireless PID:1020 as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.2/0003:046D:C52B.0003/input/input14
[    5.108314] logitech-djdevice 0003:046D:C52B.0004: input,hidraw1: USB HID v1.11 Mouse [Logitech Unifying Device. Wireless PID:1020] on usb-0000:00:1a.0-1.2:1
[    5.110302] input: Logitech Unifying Device. Wireless PID:4004 as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.2/0003:046D:C52B.0003/input/input15
[    5.110345] logitech-djdevice 0003:046D:C52B.0005: input,hidraw2: USB HID v1.11 Keyboard [Logitech Unifying Device. Wireless PID:4004] on usb-0000:00:1a.0-1.2:2
[    5.167385] usb 2-1.6: new high-speed USB device number 3 using ehci-pci
[    5.337482] usb 2-1.6: New USB device found, idVendor=5986, idProduct=0401
[    5.337489] usb 2-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    5.337493] usb 2-1.6: Product: BisonCam, NB Pro
[    5.337496] usb 2-1.6: Manufacturer: Bison
[    5.347138] random: nonblocking pool is initialized
[    8.299496]  sdb: sdb1
[    8.344431] sd 6:0:0:0: [sdb] No Caching mode page found
[    8.344435] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    8.344438] sd 6:0:0:0: [sdb] Attached SCSI disk
[    8.777410] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   16.255632] Adding 15600944k swap on /dev/sda5.  Priority:-1 extents:1 across:15600944k FS
[   16.327046] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.629418] systemd-udevd[387]: starting version 204
[   17.636345] lp: driver loaded but no devices found
[   17.696387] ppdev: user-space parallel port driver
[   20.111962] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
[   20.111968] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   20.111971] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[   20.111972] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   20.111973] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[   20.111975] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   20.111976] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   20.432555] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   20.436848] mei_me 0000:00:16.0: irq 44 for MSI/MSI-X
[   20.603100] device-mapper: multipath: version 1.6.0 loaded
[   20.639003] Bluetooth: Core ver 2.17
[   20.639014] NET: Registered protocol family 31
[   20.639015] Bluetooth: HCI device and connection manager initialized
[   20.639021] Bluetooth: HCI socket layer initialized
[   20.639023] Bluetooth: L2CAP socket layer initialized
[   20.639025] Bluetooth: SCO socket layer initialized
[   20.775724] wmi: Mapper loaded
[   20.897547] usbcore: registered new interface driver btusb
[   20.910463] Bluetooth: hci0: read Intel version: 3707100180012d0d00
[   21.038876] [drm] Initialized drm 1.1.0 20060810
[   21.092359] cfg80211: Calling CRDA to update world regulatory domain
[   21.379077] Intel(R) Wireless WiFi driver for Linux, in-tree:
[   21.379079] Copyright(c) 2003-2013 Intel Corporation
[   21.379248] iwlwifi 0000:02:00.0: irq 45 for MSI/MSI-X
[   21.390365] Linux video capture interface: v2.00
[   21.452483] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   21.792042] autoconfig: line_outs=1 (0x24/0x0/0x0/0x0/0x0) type:speaker
[   21.792042]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   21.792043]    hp_outs=1 (0x25/0x0/0x0/0x0/0x0)
[   21.792043]    mono: mono_out=0x0
[   21.792043]    inputs:
[   21.792044]      Mic=0x2b
[   21.792045]      Internal Mic=0x29
[   21.922907] iwlwifi 0000:02:00.0: loaded firmware version 22.24.8.0 op_mode iwlmvm
[   21.964615] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input18
[   21.964664] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input17
[   21.964698] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
[   21.965489] intel_rapl: domain uncore energy ctr 44019:44019 not working, skip
[   21.966006] [drm] Memory usable by graphics device = 2048M
[   21.966010] checking generic (e0000000 7f0000) vs hw (e0000000 10000000)
[   21.966011] fb: conflicting fb hw usage inteldrmfb vs VESA VGA - removing generic driver
[   21.966045] Console: switching to colour dummy device 80x25
[   22.013567] i915 0000:00:02.0: irq 47 for MSI/MSI-X
[   22.013575] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   22.013576] [drm] Driver supports precise vblank timestamp query.
[   22.013619] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   22.068129] uvcvideo: Found UVC 1.00 device HD Pro Webcam C920 (046d:082d)
[   22.068493] input: HD Pro Webcam C920 as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.0/input/input19
[   22.068563] uvcvideo: Found UVC 1.00 device BisonCam, NB Pro (5986:0401)
[   22.072771] fbcon: inteldrmfb (fb0) is primary device
[   22.073529] input: BisonCam, NB Pro as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input20
[   22.073563] usbcore: registered new interface driver uvcvideo
[   22.073563] USB Video Class driver (1.1.1)
[   22.133028] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.1.2d.d.bseq
[   22.180653] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[   22.281157] usbcore: registered new interface driver snd-usb-audio
[   22.871273] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[   22.871343] iwlwifi 0000:02:00.0: L1 Enabled - LTR Disabled
[   22.871591] iwlwifi 0000:02:00.0: L1 Enabled - LTR Disabled
[   22.958525] Console: switching to colour frame buffer device 240x67
[   22.962017] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   22.962018] i915 0000:00:02.0: registered panic notifier
[   22.962116] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   22.967228] acpi device:4d: registered as cooling_device9
[   22.967283] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input21
[   22.967346] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   22.978092] cfg80211: World regulatory domain updated:
[   22.978094] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   22.978095] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.978097] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.978097] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   22.978098] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.978099] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.123659] type=1400 audit(1425285608.991:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=597 comm="apparmor_parser"
[   23.123664] type=1400 audit(1425285608.991:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=597 comm="apparmor_parser"
[   23.123667] type=1400 audit(1425285608.991:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=597 comm="apparmor_parser"
[   23.123691] type=1400 audit(1425285608.991:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=633 comm="apparmor_parser"
[   23.123696] type=1400 audit(1425285608.991:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=633 comm="apparmor_parser"
[   23.123699] type=1400 audit(1425285608.991:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=633 comm="apparmor_parser"
[   23.123949] type=1400 audit(1425285608.991:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=597 comm="apparmor_parser"
[   23.123952] type=1400 audit(1425285608.991:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=597 comm="apparmor_parser"
[   23.123979] type=1400 audit(1425285608.991:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=633 comm="apparmor_parser"
[   23.123981] type=1400 audit(1425285608.991:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=633 comm="apparmor_parser"
[   23.140636] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   23.851449] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off
[   27.117290] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   28.068996] init: failsafe main process (893) killed by TERM signal
[   29.072343] audit_printk_skb: 6 callbacks suppressed
[   29.072345] type=1400 audit(1425285614.935:14): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=1041 comm="apparmor_parser"
[   29.072350] type=1400 audit(1425285614.935:15): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1041 comm="apparmor_parser"
[   29.072353] type=1400 audit(1425285614.935:16): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1041 comm="apparmor_parser"
[   29.072643] type=1400 audit(1425285614.935:17): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1041 comm="apparmor_parser"
[   29.072646] type=1400 audit(1425285614.935:18): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1041 comm="apparmor_parser"
[   29.072796] type=1400 audit(1425285614.935:19): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1041 comm="apparmor_parser"
[   29.210063] type=1400 audit(1425285615.071:20): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1046 comm="apparmor_parser"
[   29.210069] type=1400 audit(1425285615.071:21): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=1046 comm="apparmor_parser"
[   29.210400] type=1400 audit(1425285615.071:22): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1046 comm="apparmor_parser"
[   29.239715] type=1400 audit(1425285615.103:23): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/mysqld" pid=1047 comm="apparmor_parser"
[   31.048836] Bluetooth: RFCOMM TTY layer initialized
[   31.048846] Bluetooth: RFCOMM socket layer initialized
[   31.048850] Bluetooth: RFCOMM ver 1.11
[   31.137902] init: cups main process (1100) killed by HUP signal
[   31.137909] init: cups main process ended, respawning
[   31.540819] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   31.540822] Bluetooth: BNEP filters: protocol multicast
[   31.540830] Bluetooth: BNEP socket layer initialized
[   34.952853] audit_printk_skb: 159 callbacks suppressed
[   34.952856] type=1400 audit(1425285620.811:77): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cups-browsed" pid=1328 comm="apparmor_parser"
[   34.953912] type=1400 audit(1425285620.811:78): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/mysqld" pid=1329 comm="apparmor_parser"
[   38.179020] iwlwifi 0000:02:00.0: L1 Enabled - LTR Disabled
[   38.179273] iwlwifi 0000:02:00.0: L1 Enabled - LTR Disabled
[   38.191133] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   38.191297] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   38.482424] r8169 0000:03:00.2 eth0: link down
[   38.482465] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   38.482844] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   39.282910] init: samba-ad-dc main process (1175) terminated with status 1
[   40.689767] vboxdrv: module verification failed: signature and/or  required key missing - tainting kernel
[   40.692196] vboxdrv: Found 8 processor cores.
[   40.692355] vboxdrv: fAsync=0 offMin=0x186 offMax=0x1143
[   40.692488] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   40.692490] vboxdrv: Successfully loaded version 4.3.10_Ubuntu (interface 0x001a0007).
[   40.953953] vboxpci: IOMMU not found (not registered)
[   42.429125] wlan0: authenticate with c8:a7:0a:9b:70:54
[   42.431701] wlan0: direct probe to c8:a7:0a:9b:70:54 (try 1/3)
[   42.636042] wlan0: send auth to c8:a7:0a:9b:70:54 (try 2/3)
[   42.636696] wlan0: authenticated
[   42.639103] wlan0: associate with c8:a7:0a:9b:70:54 (try 1/3)
[   42.640126] wlan0: RX AssocResp from c8:a7:0a:9b:70:54 (capab=0x11 status=0 aid=2)
[   42.641080] wlan0: associated
[   42.641109] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   42.641156] cfg80211: Calling CRDA for country: US
[   42.642977] cfg80211: Regulatory domain changed to country: US
[   42.642979] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   42.642980] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   42.642981] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   42.642982] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.642983] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.642984] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.642985] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   42.642986] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
[   42.885692] wlan0: Limiting TX power to 30 (30 - 0) dBm as advertised by c8:a7:0a:9b:70:54
[   61.367661] type=1400 audit(1425285647.202:79): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2096 comm="apparmor_parser"
[   61.367667] type=1400 audit(1425285647.202:80): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2096 comm="apparmor_parser"
[   61.367979] type=1400 audit(1425285647.206:81): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2096 comm="apparmor_parser"
[   79.196996] init: plymouth-upstart-bridge main process ended, respawning
[   79.344948] init: plymouth-upstart-bridge main process ended, respawning
[  142.982951] EXT4-fs (sdb1): warning: maximal mount count reached, running e2fsck is recommended
[  142.992807] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
```


Attached is my bootchart:  [https://dl.dropboxusercontent.com/u/89787730/henry-Gazelle-Professional-trusty-20150302-1.png](https://dl.dropboxusercontent.com/u/89787730/henry-Gazelle-Professional-trusty-20150302-1.png)

---

### Post by mattharris4 on 2015-03-02
What are the specs on your System 76 computer (CPU, amount of RAM, HDD or SDD capacity, graphics card model, etc.)?  I really cannot give more than general advice without that information.

I can say that unless your system is ancient (I don't know how long System 76 has been in business) four minutes from power-up to a working Ubuntu is not good.  Even Windows can boot up fastet than that on most computers.  On my Edubuntu computer (essentially Ubuntu with a GNOME option and educational suite) I can go from power-up to a working Edubuntu in less than a minute including selecting Edubuntu from my GRUB boot screen (I also have Win XP on that computer), since you don't have the log-on screen bypassed/disabled you could add 20 seconds or so for that process but four minutes is ridiculous for any relatively modern Linux system.  If your computer is still under warranty you need to contact System 76, if not please post the info I ask for in the first sentence.  You can get this info by clicking on the gear icon at the very top right of your screen (to the right of the clock) then select System Settings.  Next select Details.  You will then have a mini-window with the information in it.  You can also install updates from this mini-screen.

---

### Post by hcamelion on 2015-03-02
I uploaded a screenshot of my system properties to the original post.  Thanks for the help!  Here is is here too...


[ATTACH=CONFIG]260391[/ATTACH]

---

### Post by mattharris4 on 2015-03-03
> **hcamelion said:**
> I uploaded a screenshot of my system properties to the original post.  Thanks for the help!  Here is is here too...


[ATTACH=CONFIG]260391[/ATTACH]


Sorry I missed the specs screen you posted.  Certainly it should not take four minutes to boot up Ubuntu on this computer, you actually have pretty much the top of the line computer that anyone sells.  Maybe the newest i7s run a bit faster but something isn't right.  The X8 means your CPU has eight cores, most only have two or four.  You have almost 16GB of RAM, worst-case Ubuntu only really requires about three unless you are rendering professional videos or something just as exotic (although that number will increase as websites such as SF Gate get even more RAM hoggy).  For comparison I am typing this on a computer with 3.5GB RAM, a Pentium 4 3.0GHz 32-bit dual-core CPU and is about 7-8 years old.  I can boot up Edubuntu (essentially Ubuntu with a bunch more programs in it) in less than a minute from power-up to usable state, I have the login screen bypassed (this computer is in my office and only I use it) so that would likely add about 25-30 seconds to boot-up.  I can even boot up Windows XP in less than four minutes.  Your i7 CPU should be booting up in about 20 seconds or so plus whatever time it takes to type in your password.

I have some questions for you here.  The first one is probably obvious -- is this computer still under manufacturer's (in this case System 76) warranty?  The second one (and I apologize for having to ask, please don't take this as an accusation or insult) is did you alter the operating system with any scripts, programs from shifty sources (programs not from the Ubuntu Software Center or reliable sources such as Google, Microsoft, Apple, AVG, etc)?  If a poorly scripted program is running upon start-up that could be the issue.  You would know if this is the case.  If it is still under warranty and the answer to question two is negative I would contact the manufacturer.  System 76 has a good reputation from what I can find, I am sure they want to keep it that way.

If the computer is not under warranty, you probably need to back up your documents to a portable hard drive, then create a bootable DVD or USB and reinstall Ubuntu using the option to wipe/format the drive before installing.  Also, test the computer thoroughly before installing any scripts or programs not from reliable sources.  Before doing this, if the computer will cooperate enough to get this far you should install and use System Monitor to see if you are maxing out either the CPU or the RAM (this should also tell you if any of your RAM sticks are defective, the number will be a bit less than 15.6GB but if it is only 11-12 you know you have a defective RAM stick).  If it is the CPU that is defective (hardly likely but stranger things have happened) then I don't really know how to help you, I don't even know how to verify whether the CPU is working correctly or not other than that eight cores should show up on the System Monitor, if there are less than eight you probably have a bad CPU or motherboard.  I suspect something is maxing one of these out but if not and a reinstall doesn't take care of the issue you need to check the hard drive or SSD for defects.  Checking the hard drive for defects is something I haven't had to do but search this forum, I read a thread that told how to do it but I did not bookmark it so you will need to do a search for it.  If the hard drive is defective, they are usually quite easy to replace and even for a laptop cost less than $100.  Since you likely don't have a Windows installation to deal with on a System 76 computer just follow the Ubuntu installation process on the bootable DVD/USB and then reinstall the programs you need from the Ubuntu Software Center.  Of course it is your option whether to reinstall Ubuntu or install a lighter OS such as Lubuntu, Kubuntu or Xubuntu but with the computer you have and the specs it has I don't think it would make much of a difference once you figure out the problem and fix it.  Before replacing the CPU (if this ends up going that far) you really need to get a professional computer tech involved, it could be a motherboard issue as well and I would hate to see you spend $500 plus on another i7 CPU if the motherboard itself is defective.

---

### Post by westie457 on 2015-03-03
@hcamelion
This line from your dmesg > [COLOR=#000000][FONT=Ubuntu Mono][  142.982951] EXT4-fs (sdb1): warning: maximal mount count reached, running e2fsck is recommended[/FONT][/COLOR]shows the main hold-up.
Have you tried the suggestion to run 'e2fsck'?

---

### Post by mattharris4 on 2015-03-04
Here is some info on the e2fsck command from the Ubuntu site.  I think it would be a good idea to read it before using that command:  [http://manpages.ubuntu.com/manpages/hardy/man8/fsck.ext2.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/fsck.ext2.8.html) .  For example it is not safe to run this on mounted filesystems (an example would be when you attach an external hard drive or USB stick in computer parlance you are actually "mounting" it to the computer, that is why you are supposed to "dismount" them before removing them from the computer) .  I am not a Linux programmer so explaining this command goes way beyond my knowledge.  I don't think you will wreck a hard drive/RAM/CPU/motherboard physically by using it as long as ventilation in your computer is enough to prevent overheating but if even one question it asks is answered wrong (I suspect from what I read, it is unclear) you could have to reinstall Ubuntu anyway and lose your other files in the process.  Therefore I strongly recommend backing up your files before attempting to take Westie's advice if the computer will now boot up at all.  I am interested in seeing Westie's advice after reading this post and the attached link, as I say above I am unfamiliar with this command and am not a programmer so my advice is after reading the linked page and very conservative.

---

