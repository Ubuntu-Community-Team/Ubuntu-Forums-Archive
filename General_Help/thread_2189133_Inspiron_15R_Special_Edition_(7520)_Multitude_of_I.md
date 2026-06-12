---
title: "Inspiron 15R Special Edition (7520): Multitude of Issues"
date: 2013-11-20
forum: General Help
---

### Post by Donner87 on 2013-11-20
*EDIT:  Removed conflating issues.*

I have random, hard locks running Ubuntu 13.10 on this particular laptop (Inspiron 15R Special Edition).  I am hoping that a helpful soul can assist.  System information is at the bottom of the post.


This happens during two events, but will occur only sporadically during those events.  Either A) when the laptop powers down the screen after a period of inactivity;  or B) while attempting to put the laptop to sleep.  In either case, the laptop is hard locked; no response on screen, no activity LEDs, no SSH, no REISUB, and no error messages.  If it happens during A, the screen will be black, but with the backlight on.  If it happens during B, the screen will be frozen at whatever was on the screen prior to putting it to sleep.

For the most part this only occurs during those two events.  Once or twice it has happened while I'm actively using the laptop, but that's quite rare.

No error messages appear to be logged anywhere (dmesg, kern.log, on screen, etc).  I have tried to use the netconsole kernel module, but it requires ethernet, and despite trying for three days tethered to a wall, the problem never occurred.  It wasn't until I disconnected from ethernet and went back on wifi that the issue then (randomly) happened again.

I have no idea how to solve this.  I can't get any error messages, and have been unable to find any relevant bugs through my searches.  The problem is also difficult to reproduce.  Sleeping and unsleeping repeatedly doesn't do it, nor suspending repeatedly.  It just sort of happens out of the blue, usually when I'm in the middle of working on something important and decide I need a 10 minute break ... just long enough for the system to suspend and die a horrible death.

I tried an older kernel, 3.8.  Problem persisted, though symptoms were changed slightly.  It hard locked when powering the display back on, after displaying the desktop wallpaper, but before displaying the login box.


I hope someone can shed some light in my dark hell down here.


**System Info:**
Ubuntu 13.10

lspci
```
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Chelsea LP [Radeon HD 7730M] (rev ff)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 07)
08:00.0 Network controller: Intel Corporation Centrino Wireless-N 2230 (rev c4)
```

uname -a
```
Linux 3.11.0-13-generic #20-Ubuntu SMP Wed Oct 23 07:38:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

dmesg
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.11.0-13-generic (buildd@roseapple) (gcc version 4.8.1 (Ubuntu/Linaro 4.8.1-10ubuntu8) ) #20-Ubuntu SMP Wed Oct 23 07:38:26 UTC 2013 (Ubuntu 3.11.0-13.20-generic 3.11.6)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.11.0-13-generic root=/dev/mapper/ubuntu-root ro acpi_backlight=vendor dell_laptop.backlight=0 quiet splash vt.handoff=7
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
[    0.000000] BIOS-e820: [mem 0x0000000040005000-0x000000008f1e4fff] usable
[    0.000000] BIOS-e820: [mem 0x000000008f1e5000-0x000000008ff65fff] reserved
[    0.000000] BIOS-e820: [mem 0x000000008ff66000-0x000000008ffaffff] usable
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
[    0.000000] efi: mem10: type=7, attr=0xf, range=[0x0000000020200000-0x0000000034cc0000) (330MB)
[    0.000000] efi: mem11: type=2, attr=0xf, range=[0x0000000034cc0000-0x0000000036658000) (25MB)
[    0.000000] efi: mem12: type=7, attr=0xf, range=[0x0000000036658000-0x0000000040004000) (153MB)
[    0.000000] efi: mem13: type=0, attr=0xf, range=[0x0000000040004000-0x0000000040005000) (0MB)
[    0.000000] efi: mem14: type=7, attr=0xf, range=[0x0000000040005000-0x0000000069389000) (659MB)
[    0.000000] efi: mem15: type=2, attr=0xf, range=[0x0000000069389000-0x000000008e3c0000) (592MB)
[    0.000000] efi: mem16: type=4, attr=0xf, range=[0x000000008e3c0000-0x000000008e3e0000) (0MB)
[    0.000000] efi: mem17: type=7, attr=0xf, range=[0x000000008e3e0000-0x000000008efcb000) (11MB)
[    0.000000] efi: mem18: type=4, attr=0xf, range=[0x000000008efcb000-0x000000008f1e5000) (2MB)
[    0.000000] efi: mem19: type=0, attr=0xf, range=[0x000000008f1e5000-0x000000008ff66000) (13MB)
[    0.000000] efi: mem20: type=4, attr=0xf, range=[0x000000008ff66000-0x000000008ffb0000) (0MB)
[    0.000000] efi: mem21: type=0, attr=0xf, range=[0x000000008ffb0000-0x00000000913b0000) (20MB)
[    0.000000] efi: mem22: type=7, attr=0xf, range=[0x00000000913b0000-0x000000009159f000) (1MB)
[    0.000000] efi: mem23: type=1, attr=0xf, range=[0x000000009159f000-0x00000000915bf000) (0MB)
[    0.000000] efi: mem24: type=7, attr=0xf, range=[0x00000000915bf000-0x00000000963d3000) (78MB)
[    0.000000] efi: mem25: type=4, attr=0xf, range=[0x00000000963d3000-0x000000009642b000) (0MB)
[    0.000000] efi: mem26: type=7, attr=0xf, range=[0x000000009642b000-0x000000009643f000) (0MB)
[    0.000000] efi: mem27: type=4, attr=0xf, range=[0x000000009643f000-0x000000009731c000) (14MB)
[    0.000000] efi: mem28: type=7, attr=0xf, range=[0x000000009731c000-0x0000000097322000) (0MB)
[    0.000000] efi: mem29: type=4, attr=0xf, range=[0x0000000097322000-0x000000009732a000) (0MB)
[    0.000000] efi: mem30: type=7, attr=0xf, range=[0x000000009732a000-0x000000009732b000) (0MB)
[    0.000000] efi: mem31: type=4, attr=0xf, range=[0x000000009732b000-0x0000000097350000) (0MB)
[    0.000000] efi: mem32: type=7, attr=0xf, range=[0x0000000097350000-0x0000000097351000) (0MB)
[    0.000000] efi: mem33: type=4, attr=0xf, range=[0x0000000097351000-0x000000009747b000) (1MB)
[    0.000000] efi: mem34: type=7, attr=0xf, range=[0x000000009747b000-0x0000000097480000) (0MB)
[    0.000000] efi: mem35: type=4, attr=0xf, range=[0x0000000097480000-0x0000000097483000) (0MB)
[    0.000000] efi: mem36: type=7, attr=0xf, range=[0x0000000097483000-0x0000000097484000) (0MB)
[    0.000000] efi: mem37: type=4, attr=0xf, range=[0x0000000097484000-0x0000000097678000) (1MB)
[    0.000000] efi: mem38: type=7, attr=0xf, range=[0x0000000097678000-0x0000000097679000) (0MB)
[    0.000000] efi: mem39: type=4, attr=0xf, range=[0x0000000097679000-0x00000000978d7000) (2MB)
[    0.000000] efi: mem40: type=7, attr=0xf, range=[0x00000000978d7000-0x00000000978e2000) (0MB)
[    0.000000] efi: mem41: type=4, attr=0xf, range=[0x00000000978e2000-0x00000000978e3000) (0MB)
[    0.000000] efi: mem42: type=7, attr=0xf, range=[0x00000000978e3000-0x00000000978e5000) (0MB)
[    0.000000] efi: mem43: type=4, attr=0xf, range=[0x00000000978e5000-0x00000000995bf000) (28MB)
[    0.000000] efi: mem44: type=7, attr=0xf, range=[0x00000000995bf000-0x00000000999bb000) (3MB)
[    0.000000] efi: mem45: type=2, attr=0xf, range=[0x00000000999bb000-0x00000000999c5000) (0MB)
[    0.000000] efi: mem46: type=3, attr=0xf, range=[0x00000000999c5000-0x0000000099dbf000) (3MB)
[    0.000000] efi: mem47: type=5, attr=0x800000000000000f, range=[0x0000000099dbf000-0x0000000099f2b000) (1MB)
[    0.000000] efi: mem48: type=5, attr=0x800000000000000f, range=[0x0000000099f2b000-0x0000000099f2e000) (0MB)
[    0.000000] efi: mem49: type=6, attr=0x800000000000000f, range=[0x0000000099f2e000-0x000000009a0b4000) (1MB)
[    0.000000] efi: mem50: type=5, attr=0x800000000000000f, range=[0x000000009a0b4000-0x000000009a1bf000) (1MB)
[    0.000000] efi: mem51: type=6, attr=0x800000000000000f, range=[0x000000009a1bf000-0x000000009a2af000) (0MB)
[    0.000000] efi: mem52: type=6, attr=0x800000000000000f, range=[0x000000009a2af000-0x000000009a3bf000) (1MB)
[    0.000000] efi: mem53: type=0, attr=0xf, range=[0x000000009a3bf000-0x000000009ab86000) (7MB)
[    0.000000] efi: mem54: type=0, attr=0xf, range=[0x000000009ab86000-0x000000009aebf000) (3MB)
[    0.000000] efi: mem55: type=10, attr=0xf, range=[0x000000009aebf000-0x000000009af91000) (0MB)
[    0.000000] efi: mem56: type=10, attr=0xf, range=[0x000000009af91000-0x000000009afbf000) (0MB)
[    0.000000] efi: mem57: type=9, attr=0xf, range=[0x000000009afbf000-0x000000009afdf000) (0MB)
[    0.000000] efi: mem58: type=9, attr=0xf, range=[0x000000009afdf000-0x000000009afff000) (0MB)
[    0.000000] efi: mem59: type=4, attr=0xf, range=[0x000000009afff000-0x000000009b000000) (0MB)
[    0.000000] efi: mem60: type=7, attr=0xf, range=[0x0000000100000000-0x000000025f600000) (5622MB)
[    0.000000] efi: mem61: type=0, attr=0x0, range=[0x00000000000a0000-0x00000000000c0000) (0MB)
[    0.000000] efi: mem62: type=0, attr=0x0, range=[0x000000009b000000-0x000000009fa00000) (74MB)
[    0.000000] efi: mem63: type=11, attr=0x8000000000000001, range=[0x00000000e0000000-0x00000000f0000000) (256MB)
[    0.000000] efi: mem64: type=11, attr=0x8000000000000001, range=[0x00000000feb00000-0x00000000feb04000) (0MB)
[    0.000000] efi: mem65: type=11, attr=0x8000000000000001, range=[0x00000000fec00000-0x00000000fec01000) (0MB)
[    0.000000] efi: mem66: type=11, attr=0x8000000000000001, range=[0x00000000fed10000-0x00000000fed1a000) (0MB)
[    0.000000] efi: mem67: type=11, attr=0x8000000000000001, range=[0x00000000fed1c000-0x00000000fed20000) (0MB)
[    0.000000] efi: mem68: type=11, attr=0x8000000000000001, range=[0x00000000fee00000-0x00000000fee01000) (0MB)
[    0.000000] efi: mem69: type=11, attr=0x8000000000000000, range=[0x00000000ffb80000-0x00000000fff00000) (3MB)
[    0.000000] efi: mem70: type=11, attr=0x8000000000000000, range=[0x00000000fff00000-0x00000000fff40000) (0MB)
[    0.000000] efi: mem71: type=11, attr=0x8000000000000000, range=[0x00000000fff40000-0x0000000100000000) (0MB)
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: Dell Inc. Inspiron 7520/0PXH02, BIOS A05 08/13/2012
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
[    0.000000] init_memory_mapping: [mem 0x40005000-0x8f1e4fff]
[    0.000000]  [mem 0x40005000-0x401fffff] page 4k
[    0.000000]  [mem 0x40200000-0x8effffff] page 2M
[    0.000000]  [mem 0x8f000000-0x8f1e4fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x8ff66000-0x8ffaffff]
[    0.000000]  [mem 0x8ff66000-0x8ffaffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x913b0000-0x99dbefff]
[    0.000000]  [mem 0x913b0000-0x913fffff] page 4k
[    0.000000]  [mem 0x91400000-0x99bfffff] page 2M
[    0.000000]  [mem 0x99c00000-0x99dbefff] page 4k
[    0.000000] init_memory_mapping: [mem 0x9afff000-0x9affffff]
[    0.000000]  [mem 0x9afff000-0x9affffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x1ffffffff]
[    0.000000]  [mem 0x100000000-0x1ffffffff] page 2M
[    0.000000] RAMDISK: [mem 0x34cc0000-0x36657fff]
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
[    0.000000]   NODE_DATA [mem 0x25f5f0000-0x25f5f4fff]
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
[    0.000000]   node   0: [mem 0x40005000-0x8f1e4fff]
[    0.000000]   node   0: [mem 0x8ff66000-0x8ffaffff]
[    0.000000]   node   0: [mem 0x913b0000-0x99dbefff]
[    0.000000]   node   0: [mem 0x9afff000-0x9affffff]
[    0.000000]   node   0: [mem 0x100000000-0x25f5fffff]
[    0.000000] On node 0 totalpages: 2060229
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 23 pages reserved
[    0.000000]   DMA zone: 3975 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 9641 pages used for memmap
[    0.000000]   DMA32 zone: 617022 pages, LIFO batch:31
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
[    0.000000] PM: Registered nosave memory: [mem 0x8f1e5000-0x8ff65fff]
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
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2028013
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.11.0-13-generic root=/dev/mapper/ubuntu-root ro acpi_backlight=vendor dell_laptop.backlight=0 quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 7942448K/8240916K available (7141K kernel code, 1081K rwdata, 3260K rodata, 1364K init, 1420K bss, 298468K reserved)
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
[    0.004000] tsc: Detected 2195.003 MHz processor
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 4390.00 BogoMIPS (lpj=8780012)
[    0.000005] pid_max: default: 32768 minimum: 301
[    0.000018] init_memory_mapping: [mem 0x99dbf000-0x99f2dfff]
[    0.000020]  [mem 0x99dbf000-0x99f2dfff] page 4k
[    0.000037] init_memory_mapping: [mem 0x99f2e000-0x9a0b3fff]
[    0.000038]  [mem 0x99f2e000-0x9a0b3fff] page 4k
[    0.000051] init_memory_mapping: [mem 0x9a0b4000-0x9a1befff]
[    0.000053]  [mem 0x9a0b4000-0x9a1befff] page 4k
[    0.000062] init_memory_mapping: [mem 0x9a1bf000-0x9a3befff]
[    0.000064]  [mem 0x9a1bf000-0x9a3befff] page 4k
[    0.043369] Security Framework initialized
[    0.043392] AppArmor: AppArmor initialized
[    0.043393] Yama: becoming mindful.
[    0.043907] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.046090] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.047061] Mount-cache hash table entries: 256
[    0.047231] Initializing cgroup subsys memory
[    0.047239] Initializing cgroup subsys devices
[    0.047240] Initializing cgroup subsys freezer
[    0.047242] Initializing cgroup subsys blkio
[    0.047243] Initializing cgroup subsys perf_event
[    0.047245] Initializing cgroup subsys hugetlb
[    0.047266] CPU: Physical Processor ID: 0
[    0.047267] CPU: Processor Core ID: 0
[    0.047272] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.047272] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.047677] mce: CPU supports 9 MCE banks
[    0.047690] CPU0: Thermal monitoring enabled (TM1)
[    0.047702] Last level iTLB entries: 4KB 512, 2MB 0, 4MB 0
[    0.047702] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32
[    0.047702] tlb_flushall_shift: 1
[    0.047835] Freeing SMP alternatives memory: 28K (ffffffff81e65000 - ffffffff81e6c000)
[    0.050143] ACPI: Core revision 20130517
[    0.055940] ACPI: All ACPI Tables successfully acquired
[    0.070356] ftrace: allocating 27803 entries in 109 pages
[    0.084859] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.124585] smpboot: CPU0: Intel(R) Core(TM) i7-3632QM CPU @ 2.20GHz (fam: 06, model: 3a, stepping: 09)
[    0.124592] TSC deadline timer enabled
[    0.124602] Performance Events: PEBS fmt1+, 16-deep LBR, IvyBridge events, full-width counters, Intel PMU driver.
[    0.124609] ... version:                3
[    0.124610] ... bit width:              48
[    0.124611] ... generic registers:      4
[    0.124612] ... value mask:             0000ffffffffffff
[    0.124613] ... max period:             0000ffffffffffff
[    0.124614] ... fixed-purpose events:   3
[    0.124615] ... event mask:             000000070000000f
[    0.139817] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.126191] smpboot: Booting Node   0, Processors  #1 #2 #3 #4 #5 #6 #7 OK
[    0.221641] Brought up 8 CPUs
[    0.221644] smpboot: Total of 8 processors activated (35120.04 BogoMIPS)
[    0.229324] devtmpfs: initialized
[    0.230408] EVM: security.selinux
[    0.230410] EVM: security.SMACK64
[    0.230411] EVM: security.capability
[    0.230467] PM: Registering ACPI NVS region [mem 0x9aebf000-0x9afbefff] (1048576 bytes)
[    0.231321] regulator-dummy: no parameters
[    0.231352] RTC time: 18:55:57, date: 11/20/13
[    0.231385] NET: Registered protocol family 16
[    0.231539] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.231541] ACPI: bus type PCI registered
[    0.231543] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.231598] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.231601] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.259200] PCI: Using configuration type 1 for base access
[    0.259317] dmi type 0xB1 record - unknown flag
[    0.260239] bio: create slab <bio-0> at 0
[    0.260403] ACPI: Added _OSI(Module Device)
[    0.260404] ACPI: Added _OSI(Processor Device)
[    0.260406] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.260407] ACPI: Added _OSI(Processor Aggregator Device)
[    0.261828] ACPI: EC: Look up EC in DSDT
[    0.263236] ACPI: Executed 1 blocks of module-level executable AML code
[    0.269667] ACPI: SSDT 000000009abaa018 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20111123)
[    0.270034] ACPI: Dynamic OEM Table Load:
[    0.270037] ACPI: SSDT           (null) 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20111123)
[    0.273860] ACPI: SSDT 000000009ababa98 00303 (v01  PmRef    ApIst 00003000 INTL 20111123)
[    0.274251] ACPI: Dynamic OEM Table Load:
[    0.274253] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20111123)
[    0.277741] ACPI: SSDT 000000009aba9d98 00119 (v01  PmRef    ApCst 00003000 INTL 20111123)
[    0.278098] ACPI: Dynamic OEM Table Load:
[    0.278100] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20111123)
[    0.282895] ACPI: Interpreter enabled
[    0.282902] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20130517/hwxface-571)
[    0.282907] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20130517/hwxface-571)
[    0.282921] ACPI: (supports S0 S3 S4 S5)
[    0.282922] ACPI: Using IOAPIC for interrupt routing
[    0.282949] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.283059] ACPI: No dock devices found.
[    0.504972] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.505093] \_SB_.PCI0:_OSC invalid UUID
[    0.505094] _OSC request data:1 8 0 
[    0.505141] \_SB_.PCI0:_OSC invalid UUID
[    0.505142] _OSC request data:1 1f 0 
[    0.505145] acpi PNP0A08:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.505147] acpi PNP0A08:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.505496] PCI host bridge to bus 0000:00
[    0.505499] pci_bus 0000:00: root bus resource [bus 00-fe]
[    0.505501] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.505504] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.505506] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.505509] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff]
[    0.505511] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff]
[    0.505512] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff]
[    0.505514] pci_bus 0000:00: root bus resource [mem 0x000cc000-0x000cffff]
[    0.505516] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.505517] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.505519] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.505520] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.505522] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    0.505523] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    0.505525] pci_bus 0000:00: root bus resource [mem 0x000e8000-0x000ebfff]
[    0.505527] pci_bus 0000:00: root bus resource [mem 0x000ec000-0x000effff]
[    0.505528] pci_bus 0000:00: root bus resource [mem 0x000f0000-0x000fffff]
[    0.505530] pci_bus 0000:00: root bus resource [mem 0x9fa00000-0xfeafffff]
[    0.505539] pci 0000:00:00.0: [8086:0154] type 00 class 0x060000
[    0.505615] pci 0000:00:01.0: [8086:0151] type 01 class 0x060400
[    0.505648] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.505681] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.505714] pci 0000:00:02.0: [8086:0166] type 00 class 0x030000
[    0.505726] pci 0000:00:02.0: reg 0x10: [mem 0xc1000000-0xc13fffff 64bit]
[    0.505733] pci 0000:00:02.0: reg 0x18: [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.505739] pci 0000:00:02.0: reg 0x20: [io  0x4000-0x403f]
[    0.505830] pci 0000:00:14.0: [8086:1e31] type 00 class 0x0c0330
[    0.505854] pci 0000:00:14.0: reg 0x10: [mem 0xc1600000-0xc160ffff 64bit]
[    0.505930] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.505973] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.506007] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
[    0.506033] pci 0000:00:16.0: reg 0x10: [mem 0xc1614000-0xc161400f 64bit]
[    0.506113] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.506186] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
[    0.506209] pci 0000:00:1a.0: reg 0x10: [mem 0xc1619000-0xc16193ff]
[    0.506304] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.506372] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
[    0.506390] pci 0000:00:1b.0: reg 0x10: [mem 0xc1610000-0xc1613fff 64bit]
[    0.506461] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.506525] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
[    0.506608] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.506657] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.506688] pci 0000:00:1c.1: [8086:1e12] type 01 class 0x060400
[    0.506770] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.506810] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.506851] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
[    0.506874] pci 0000:00:1d.0: reg 0x10: [mem 0xc1618000-0xc16183ff]
[    0.506969] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.507017] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.507050] pci 0000:00:1f.0: [8086:1e57] type 00 class 0x060100
[    0.507217] pci 0000:00:1f.2: [8086:1e03] type 00 class 0x010601
[    0.507237] pci 0000:00:1f.2: reg 0x10: [io  0x4088-0x408f]
[    0.507246] pci 0000:00:1f.2: reg 0x14: [io  0x4094-0x4097]
[    0.507254] pci 0000:00:1f.2: reg 0x18: [io  0x4080-0x4087]
[    0.507263] pci 0000:00:1f.2: reg 0x1c: [io  0x4090-0x4093]
[    0.507272] pci 0000:00:1f.2: reg 0x20: [io  0x4060-0x407f]
[    0.507281] pci 0000:00:1f.2: reg 0x24: [mem 0xc1617000-0xc16177ff]
[    0.507330] pci 0000:00:1f.2: PME# supported from D3hot
[    0.507390] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
[    0.507408] pci 0000:00:1f.3: reg 0x10: [mem 0xc1615000-0xc16150ff 64bit]
[    0.507430] pci 0000:00:1f.3: reg 0x20: [io  0x4040-0x405f]
[    0.507546] pci 0000:01:00.0: [1002:682f] type 00 class 0x030000
[    0.507557] pci 0000:01:00.0: reg 0x10: [mem 0xa0000000-0xafffffff 64bit pref]
[    0.507565] pci 0000:01:00.0: reg 0x18: [mem 0xc0000000-0xc003ffff 64bit]
[    0.507571] pci 0000:01:00.0: reg 0x20: [io  0x3000-0x30ff]
[    0.507581] pci 0000:01:00.0: reg 0x30: [mem 0xfffe0000-0xffffffff pref]
[    0.507606] pci 0000:01:00.0: supports D1 D2
[    0.507608] pci 0000:01:00.0: PME# supported from D1 D2 D3hot
[    0.507674] pci 0000:01:00.0: System wakeup disabled by ACPI
[    0.513527] pci 0000:00:01.0: PCI bridge to [bus 01-06]
[    0.513532] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
[    0.513537] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xc0ffffff]
[    0.513543] pci 0000:00:01.0:   bridge window [mem 0xa0000000-0xafffffff 64bit pref]
[    0.513705] pci 0000:07:00.0: [10ec:8168] type 00 class 0x020000
[    0.513775] pci 0000:07:00.0: reg 0x10: [io  0x2000-0x20ff]
[    0.513899] pci 0000:07:00.0: reg 0x18: [mem 0xc1404000-0xc1404fff 64bit pref]
[    0.513976] pci 0000:07:00.0: reg 0x20: [mem 0xc1400000-0xc1403fff 64bit pref]
[    0.514312] pci 0000:07:00.0: supports D1 D2
[    0.514314] pci 0000:07:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.521600] pci 0000:00:1c.0: PCI bridge to [bus 07]
[    0.521605] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.521614] pci 0000:00:1c.0:   bridge window [mem 0xc1400000-0xc14fffff 64bit pref]
[    0.521738] pci 0000:08:00.0: [8086:0887] type 00 class 0x028000
[    0.521787] pci 0000:08:00.0: reg 0x10: [mem 0xc1500000-0xc1501fff 64bit]
[    0.522019] pci 0000:08:00.0: PME# supported from D0 D3hot D3cold
[    0.529626] pci 0000:00:1c.1: PCI bridge to [bus 08]
[    0.529633] pci 0000:00:1c.1:   bridge window [mem 0xc1500000-0xc15fffff]
[    0.590022] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.590075] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.590125] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.590178] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.590230] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.590284] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.590333] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.590383] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.590623] ACPI: Enabled 5 GPEs in block 00 to 3F
[    0.590629] ACPI: \_SB_.PCI0: notify handler is installed
[    0.590681] Found 1 acpi root devices
[    0.590715] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.590798] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.590803] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=none,locks=none
[    0.590805] vgaarb: loaded
[    0.590806] vgaarb: bridge control possible 0000:01:00.0
[    0.590807] vgaarb: no bridge control possible 0000:00:02.0
[    0.590944] SCSI subsystem initialized
[    0.590946] ACPI: bus type ATA registered
[    0.590987] libata version 3.00 loaded.
[    0.591000] ACPI: bus type USB registered
[    0.591014] usbcore: registered new interface driver usbfs
[    0.591020] usbcore: registered new interface driver hub
[    0.591041] usbcore: registered new device driver usb
[    0.591155] PCI: Using ACPI for IRQ routing
[    0.597935] PCI: pci_cache_line_size set to 64 bytes
[    0.598037] e820: reserve RAM buffer [mem 0x00088000-0x0008ffff]
[    0.598038] e820: reserve RAM buffer [mem 0x40004000-0x43ffffff]
[    0.598040] e820: reserve RAM buffer [mem 0x8f1e5000-0x8fffffff]
[    0.598041] e820: reserve RAM buffer [mem 0x8ffb0000-0x8fffffff]
[    0.598042] e820: reserve RAM buffer [mem 0x99dbf000-0x9bffffff]
[    0.598044] e820: reserve RAM buffer [mem 0x9b000000-0x9bffffff]
[    0.598046] e820: reserve RAM buffer [mem 0x25f600000-0x25fffffff]
[    0.598118] NetLabel: Initializing
[    0.598119] NetLabel:  domain hash size = 128
[    0.598120] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.598128] NetLabel:  unlabeled traffic allowed by default
[    0.598190] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.598196] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.600220] Switched to clocksource hpet
[    0.604522] AppArmor: AppArmor Filesystem Enabled
[    0.604542] pnp: PnP ACPI init
[    0.604552] ACPI: bus type PNP registered
[    0.604578] pnp 00:00: [dma 4]
[    0.604595] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.604613] pnp 00:01: Plug and Play ACPI device, IDs INT0800 (active)
[    0.604701] pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.604729] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.604765] system 00:04: [io  0x0680-0x069f] has been reserved
[    0.604769] system 00:04: [io  0x1100-0x110f] has been reserved
[    0.604771] system 00:04: [io  0xffff] has been reserved
[    0.604772] system 00:04: [io  0xffff] has been reserved
[    0.604775] system 00:04: [io  0x0400-0x0453] could not be reserved
[    0.604776] system 00:04: [io  0x0458-0x047f] has been reserved
[    0.604778] system 00:04: [io  0x0500-0x057f] has been reserved
[    0.604780] system 00:04: [io  0x164e-0x164f] has been reserved
[    0.604782] system 00:04: [io  0xfd60-0xfd63] has been reserved
[    0.604784] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.604807] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.604848] system 00:06: [io  0x0454-0x0457] has been reserved
[    0.604851] system 00:06: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.604884] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.604911] pnp 00:08: Plug and Play ACPI device, IDs DLL0572 PNP0f13 (active)
[    0.664443] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.664446] system 00:09: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.664448] system 00:09: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.664449] system 00:09: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.664451] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
[    0.664453] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.664455] system 00:09: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.664457] system 00:09: [mem 0xff000000-0xff000fff] has been reserved
[    0.664459] system 00:09: [mem 0xff010000-0xffffffff] could not be reserved
[    0.664461] system 00:09: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.664463] system 00:09: [mem 0x9fa00000-0x9fa00fff] has been reserved
[    0.664465] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.664770] system 00:0a: [mem 0x20000000-0x201fffff] has been reserved
[    0.664772] system 00:0a: [mem 0x40004000-0x40004fff] has been reserved
[    0.664775] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.664792] pnp: PnP ACPI: found 11 devices
[    0.664793] ACPI: bus type PNP unregistered
[    0.670970] pci 0000:01:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
[    0.670999] pci 0000:01:00.0: BAR 6: assigned [mem 0xc0040000-0xc005ffff pref]
[    0.671001] pci 0000:00:01.0: PCI bridge to [bus 01-06]
[    0.671004] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
[    0.671007] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xc0ffffff]
[    0.671009] pci 0000:00:01.0:   bridge window [mem 0xa0000000-0xafffffff 64bit pref]
[    0.671013] pci 0000:00:1c.0: PCI bridge to [bus 07]
[    0.671016] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.671024] pci 0000:00:1c.0:   bridge window [mem 0xc1400000-0xc14fffff 64bit pref]
[    0.671031] pci 0000:00:1c.1: PCI bridge to [bus 08]
[    0.671036] pci 0000:00:1c.1:   bridge window [mem 0xc1500000-0xc15fffff]
[    0.671253] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.671255] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.671257] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.671259] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.671260] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.671262] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.671264] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff]
[    0.671265] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff]
[    0.671267] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff]
[    0.671269] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff]
[    0.671270] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff]
[    0.671272] pci_bus 0000:00: resource 15 [mem 0x000e0000-0x000e3fff]
[    0.671274] pci_bus 0000:00: resource 16 [mem 0x000e4000-0x000e7fff]
[    0.671275] pci_bus 0000:00: resource 17 [mem 0x000e8000-0x000ebfff]
[    0.671277] pci_bus 0000:00: resource 18 [mem 0x000ec000-0x000effff]
[    0.671279] pci_bus 0000:00: resource 19 [mem 0x000f0000-0x000fffff]
[    0.671280] pci_bus 0000:00: resource 20 [mem 0x9fa00000-0xfeafffff]
[    0.671282] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
[    0.671284] pci_bus 0000:01: resource 1 [mem 0xc0000000-0xc0ffffff]
[    0.671286] pci_bus 0000:01: resource 2 [mem 0xa0000000-0xafffffff 64bit pref]
[    0.671288] pci_bus 0000:07: resource 0 [io  0x2000-0x2fff]
[    0.671289] pci_bus 0000:07: resource 2 [mem 0xc1400000-0xc14fffff 64bit pref]
[    0.671291] pci_bus 0000:08: resource 1 [mem 0xc1500000-0xc15fffff]
[    0.671318] NET: Registered protocol family 2
[    0.671494] TCP established hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.671677] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.671789] TCP: Hash tables configured (established 65536 bind 65536)
[    0.671804] TCP: reno registered
[    0.671815] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.671843] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.671909] NET: Registered protocol family 1
[    0.671920] pci 0000:00:02.0: Boot video device
[    0.704477] PCI: CLS 64 bytes, default 64
[    0.704514] Trying to unpack rootfs image as initramfs...
[    1.147493] Freeing initrd memory: 26208K (ffff880034cc0000 - ffff880036658000)
[    1.147499] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.147501] software IO TLB [mem 0x923d3000-0x963d3000] (64MB) mapped at [ffff8800923d3000-ffff8800963d2fff]
[    1.147553] Simple Boot Flag at 0x44 set to 0x1
[    1.147810] Scanning for low memory corruption every 60 seconds
[    1.148064] Initialise module verification
[    1.148105] audit: initializing netlink socket (disabled)
[    1.148114] type=2000 audit(1384973758.120:1): initialized
[    1.175728] bounce pool size: 64 pages
[    1.175736] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.176790] zbud: loaded
[    1.176923] VFS: Disk quotas dquot_6.5.2
[    1.176956] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.177356] fuse init (API version 7.22)
[    1.177419] msgmni has been set to 15676
[    1.177887] Key type asymmetric registered
[    1.177888] Asymmetric key parser 'x509' registered
[    1.177913] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.177958] io scheduler noop registered
[    1.177959] io scheduler deadline registered (default)
[    1.177978] io scheduler cfq registered
[    1.178047] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    1.178172] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.178183] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.178241] efifb: probing for efifb
[    1.179194] efifb: framebuffer at 0xb0000000, mapped to 0xffffc90021480000, using 8128k, total 8128k
[    1.179196] efifb: mode is 1920x1080x32, linelength=7680, pages=1
[    1.179197] efifb: scrolling: redraw
[    1.179198] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    1.184181] Console: switching to colour frame buffer device 240x67
[    1.189094] fb0: EFI VGA frame buffer device
[    1.189099] intel_idle: MWAIT substates: 0x21120
[    1.189100] intel_idle: v0.4 model 0x3A
[    1.189101] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.189201] ACPI: AC Adapter [ACAD] (on-line)
[    1.189280] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0C0C:00/input/input0
[    1.189284] ACPI: Power Button [PWRB]
[    1.189319] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.189339] ACPI: Lid Switch [LID0]
[    1.189365] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.189367] ACPI: Power Button [PWRF]
[    1.189427] ACPI: Requesting acpi_cpufreq
[    1.190512] GHES: HEST is not enabled!
[    1.190572] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.393090] ACPI: Battery Slot [BAT1] (battery present)
[    1.393182] Linux agpgart interface v0.103
[    1.394219] brd: module loaded
[    1.394708] loop: module loaded
[    1.394976] libphy: Fixed MDIO Bus: probed
[    1.395041] tun: Universal TUN/TAP device driver, 1.6
[    1.395042] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.395078] PPP generic driver version 2.4.2
[    1.395113] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.395115] ehci-pci: EHCI PCI platform driver
[    1.395211] ehci-pci 0000:00:1a.0: setting latency timer to 64
[    1.395218] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    1.395223] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.395236] ehci-pci 0000:00:1a.0: debug port 2
[    1.399142] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    1.399158] ehci-pci 0000:00:1a.0: irq 16, io mem 0xc1619000
[    1.409078] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.409094] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.409096] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.409097] usb usb1: Product: EHCI Host Controller
[    1.409099] usb usb1: Manufacturer: Linux 3.11.0-13-generic ehci_hcd
[    1.409100] usb usb1: SerialNumber: 0000:00:1a.0
[    1.409185] hub 1-0:1.0: USB hub found
[    1.409192] hub 1-0:1.0: 2 ports detected
[    1.409341] ehci-pci 0000:00:1d.0: setting latency timer to 64
[    1.409347] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    1.409352] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.409364] ehci-pci 0000:00:1d.0: debug port 2
[    1.413256] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    1.413270] ehci-pci 0000:00:1d.0: irq 23, io mem 0xc1618000
[    1.425095] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.425106] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.425108] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.425109] usb usb2: Product: EHCI Host Controller
[    1.425111] usb usb2: Manufacturer: Linux 3.11.0-13-generic ehci_hcd
[    1.425112] usb usb2: SerialNumber: 0000:00:1d.0
[    1.425189] hub 2-0:1.0: USB hub found
[    1.425192] hub 2-0:1.0: 2 ports detected
[    1.425258] ehci-platform: EHCI generic platform driver
[    1.425263] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.425265] ohci-platform: OHCI generic platform driver
[    1.425269] uhci_hcd: USB Universal Host Controller Interface driver
[    1.425370] xhci_hcd 0000:00:14.0: setting latency timer to 64
[    1.425374] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.425377] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    1.425468] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    1.425489] xhci_hcd 0000:00:14.0: irq 41 for MSI/MSI-X
[    1.425535] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    1.425537] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.425538] usb usb3: Product: xHCI Host Controller
[    1.425540] usb usb3: Manufacturer: Linux 3.11.0-13-generic xhci_hcd
[    1.425541] usb usb3: SerialNumber: 0000:00:14.0
[    1.425595] xHCI xhci_add_endpoint called for root hub
[    1.425597] xHCI xhci_check_bandwidth called for root hub
[    1.425614] hub 3-0:1.0: USB hub found
[    1.425620] hub 3-0:1.0: 4 ports detected
[    1.425898] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.425902] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    1.425921] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    1.425923] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.425924] usb usb4: Product: xHCI Host Controller
[    1.425926] usb usb4: Manufacturer: Linux 3.11.0-13-generic xhci_hcd
[    1.425927] usb usb4: SerialNumber: 0000:00:14.0
[    1.425982] xHCI xhci_add_endpoint called for root hub
[    1.425983] xHCI xhci_check_bandwidth called for root hub
[    1.425999] hub 4-0:1.0: USB hub found
[    1.426008] hub 4-0:1.0: 4 ports detected
[    1.433142] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.458838] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.458843] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.458931] mousedev: PS/2 mouse device common for all mice
[    1.459319] rtc_cmos 00:05: RTC can wake from S4
[    1.459435] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.459463] rtc_cmos 00:05: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.459512] device-mapper: uevent: version 1.0.3
[    1.459561] device-mapper: ioctl: 4.25.0-ioctl (2013-06-26) initialised: dm-devel@redhat.com
[    1.459699] cpuidle: using governor ladder
[    1.459893] cpuidle: using governor menu
[    1.459903] ledtrig-cpu: registered to indicate activity on CPUs
[    1.459905] EFI Variables Facility v0.08 2004-May-17
[    1.479829] TCP: cubic registered
[    1.479907] NET: Registered protocol family 10
[    1.480068] NET: Registered protocol family 17
[    1.480077] Key type dns_resolver registered
[    1.480432] PM: Hibernation image not present or could not be loaded.
[    1.480438] Loading module verification certificates
[    1.481364] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 0d2f067ae81edbe7efb6ee2c61c63d9bdcf0659d'
[    1.481373] registered taskstats version 1
[    1.483565] Key type trusted registered
[    1.485678] Key type encrypted registered
[    1.488027] AppArmor: AppArmor sha1 policy hashing enabled
[    1.488504]   Magic number: 5:335:949
[    1.488512] mdio_bus fixed-0: hash matches
[    1.488527] tty tty6: hash matches
[    1.488546] processor cpu4: hash matches
[    1.488554] memory memory2: hash matches
[    1.488625] rtc_cmos 00:05: setting system clock to 2013-11-20 18:55:58 UTC (1384973758)
[    1.490003] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.490005] EDD information not available.
[    1.490657] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.490784] Freeing unused kernel memory: 1364K (ffffffff81d10000 - ffffffff81e65000)
[    1.490785] Write protecting the kernel read-only data: 12288k
[    1.493139] Freeing unused kernel memory: 1040K (ffff8800026fc000 - ffff880002800000)
[    1.494518] Freeing unused kernel memory: 836K (ffff880002b2f000 - ffff880002c00000)
[    1.504331] systemd-udevd[147]: starting version 204
[    1.512299] video: module verification failed: signature and/or required key missing - tainting kernel
[    1.514205] wmi: Mapper loaded
[    1.518435] ahci 0000:00:1f.2: version 3.0
[    1.518588] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    1.518641] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x1 impl SATA mode
[    1.518645] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst 
[    1.518651] ahci 0000:00:1f.2: setting latency timer to 64
[    1.519479] [drm] Initialized drm 1.1.0 20060810
[    1.519545] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.519559] r8169 0000:07:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.519560] scsi0 : ahci
[    1.519788] r8169 0000:07:00.0: irq 43 for MSI/MSI-X
[    1.519956] r8169 0000:07:00.0 eth0: RTL8168evl/8111evl at 0xffffc90000062000, d4:be:d9:56:2e:35, XID 0c900880 IRQ 43
[    1.519960] r8169 0000:07:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.520265] scsi1 : ahci
[    1.520346] scsi2 : ahci
[    1.520410] scsi3 : ahci
[    1.520477] scsi4 : ahci
[    1.520548] scsi5 : ahci
[    1.520611] ata1: SATA max UDMA/133 abar m2048@0xc1617000 port 0xc1617100 irq 42
[    1.520613] ata2: DUMMY
[    1.520614] ata3: DUMMY
[    1.520615] ata4: DUMMY
[    1.520617] ata5: DUMMY
[    1.520618] ata6: DUMMY
[    1.538914] [drm] Memory usable by graphics device = 2048M
[    1.538919] checking generic (b0000000 7f0000) vs hw (b0000000 10000000)
[    1.538920] fb: conflicting fb hw usage inteldrmfb vs EFI VGA - removing generic driver
[    1.538933] Console: switching to colour dummy device 80x25
[    1.539021] i915 0000:00:02.0: setting latency timer to 64
[    1.549438] [drm] radeon kernel modesetting enabled.
[    1.549450] VGA switcheroo: detected switching method \_SB_.PCI0.GFX0.ATPX handle
[    1.549484] radeon 0000:01:00.0: enabling device (0000 -> 0003)
[    1.571672] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[    1.571679] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    1.571680] [drm] Driver supports precise vblank timestamp query.
[    1.571691] ACPI Warning: \_SB_.PCI0.GFX0._DSM: Argument #4 type mismatch - Found [Integer], ACPI requires [Package] (20130517/nsarguments-95)
[    1.571715] ACPI Warning: \_SB_.PCI0.GFX0._DSM: Argument #4 type mismatch - Found [Integer], ACPI requires [Package] (20130517/nsarguments-95)
[    1.571762] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    1.571763] vgaarb: transferring owner from PCI:0000:00:02.0 to PCI:0000:01:00.0
[    1.619840] fbcon: inteldrmfb (fb0) is primary device
[    1.721413] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.837554] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.838137] ata1.00: ATA-9: Samsung SSD 840 Series, DXT06B0Q, max UDMA/133
[    1.838138] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.839484] ata1.00: configured for UDMA/133
[    1.839726] scsi 0:0:0:0: Direct-Access     ATA      Samsung SSD 840  DXT0 PQ: 0 ANSI: 5
[    1.839936] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    1.839953] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.840244] sd 0:0:0:0: [sda] Write Protect is off
[    1.840246] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.840367] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.843172]  sda: sda1 sda2 sda3
[    1.843950] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.853929] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.853930] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.854066] hub 1-1:1.0: USB hub found
[    1.854171] hub 1-1:1.0: 6 ports detected
[    1.965679] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    2.098224] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    2.098227] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.098610] hub 2-1:1.0: USB hub found
[    2.098687] hub 2-1:1.0: 8 ports detected
[    2.145926] tsc: Refined TSC clocksource calibration: 2195.013 MHz
[    2.170071] usb 1-1.3: new high-speed USB device number 3 using ehci-pci
[    2.262862] usb 1-1.3: New USB device found, idVendor=0bda, idProduct=0129
[    2.262865] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.262867] usb 1-1.3: Product: USB2.0-CRW
[    2.262869] usb 1-1.3: Manufacturer: Generic
[    2.262871] usb 1-1.3: SerialNumber: 20100201396000000
[    2.286126] Console: switching to colour frame buffer device 240x67
[    2.289494] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    2.289495] i915 0000:00:02.0: registered panic notifier
[    2.289633] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[    2.290168] ACPI: Video Device [PEGP] (multi-head: yes  rom: no  post: no)
[    2.290209] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2c/LNXVIDEO:00/input/input4
[    2.290368] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[    2.290962] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    2.290999] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:02/input/input5
[    2.291108] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.291337] [drm] initializing kernel modesetting (VERDE 0x1002:0x682F 0x1028:0x0572).
[    2.291376] [drm] register mmio base: 0xC0000000
[    2.291378] [drm] register mmio size: 262144
[    2.291379] vga_switcheroo: enabled
[    2.291444] ATPX version 1
[    2.334187] usb 1-1.5: new high-speed USB device number 4 using ehci-pci
[    2.501942] usb 1-1.5: New USB device found, idVendor=0c45, idProduct=644a
[    2.501950] usb 1-1.5: New USB device strings: Mfr=2, Product=1, SerialNumber=0
[    2.501954] usb 1-1.5: Product: Laptop_Integrated_Webcam_HD
[    2.501957] usb 1-1.5: Manufacturer: CN00YCD6724872951JRTA02
[    2.578463] usb 2-1.5: new full-speed USB device number 3 using ehci-pci
[    2.675393] usb 2-1.5: New USB device found, idVendor=8087, idProduct=07da
[    2.675400] usb 2-1.5: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.842952] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off
[    3.047528] ATOM BIOS: Dell/Compal
[    3.047551] [drm] GPU not posted. posting now...
[    3.050972] radeon 0000:01:00.0: VRAM: 2048M 0x0000000000000000 - 0x000000007FFFFFFF (2048M used)
[    3.050974] radeon 0000:01:00.0: GTT: 512M 0x0000000080000000 - 0x000000009FFFFFFF
[    3.050975] [drm] Detected VRAM RAM=2048M, BAR=256M
[    3.050976] [drm] RAM width 128bits DDR
[    3.051100] [TTM] Zone  kernel: Available graphics memory: 4014754 kiB
[    3.051101] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[    3.051102] [TTM] Initializing pool allocator
[    3.051104] [TTM] Initializing DMA pool allocator
[    3.051130] [drm] radeon: 2048M of VRAM memory ready
[    3.051131] [drm] radeon: 512M of GTT memory ready.
[    3.051424] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    3.051674] [drm] probing gen 2 caps for device 8086:151 = 261ac83/e
[    3.051676] [drm] enabling PCIE gen 3 link speeds, disable with radeon.pcie_gen2=0
[    4.280670] Switched to clocksource tsc
[    4.281798] [drm] Loading VERDE Microcode
[    4.602159] [drm] PCIE GART of 512M enabled (table at 0x0000000000276000).
[    4.602253] radeon 0000:01:00.0: WB enabled
[    4.602255] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00 and cpu addr 0xffff88024cae0c00
[    4.602257] radeon 0000:01:00.0: fence driver on ring 1 use gpu addr 0x0000000080000c04 and cpu addr 0xffff88024cae0c04
[    4.602258] radeon 0000:01:00.0: fence driver on ring 2 use gpu addr 0x0000000080000c08 and cpu addr 0xffff88024cae0c08
[    4.602259] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c and cpu addr 0xffff88024cae0c0c
[    4.602260] radeon 0000:01:00.0: fence driver on ring 4 use gpu addr 0x0000000080000c10 and cpu addr 0xffff88024cae0c10
[    4.603035] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000075a18 and cpu addr 0xffffc90021db5a18
[    4.603037] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    4.603037] [drm] Driver supports precise vblank timestamp query.
[    4.603051] radeon 0000:01:00.0: irq 45 for MSI/MSI-X
[    4.603059] radeon 0000:01:00.0: radeon: using MSI.
[    4.603081] [drm] radeon: irq initialized.
[    4.622083] [drm] ring test on 0 succeeded in 1 usecs
[    4.622086] [drm] ring test on 1 succeeded in 1 usecs
[    4.622090] [drm] ring test on 2 succeeded in 1 usecs
[    4.622149] [drm] ring test on 3 succeeded in 2 usecs
[    4.622155] [drm] ring test on 4 succeeded in 1 usecs
[    4.807933] [drm] ring test on 5 succeeded in 1 usecs
[    4.807935] [drm] UVD initialized successfully.
[    4.809486] [drm] ib test on ring 0 succeeded in 0 usecs
[    4.809517] [drm] ib test on ring 1 succeeded in 0 usecs
[    4.809537] [drm] ib test on ring 2 succeeded in 0 usecs
[    4.809557] [drm] ib test on ring 3 succeeded in 0 usecs
[    4.809579] [drm] ib test on ring 4 succeeded in 1 usecs
[    4.960824] [drm] ib test on ring 5 succeeded
[    4.961038] [drm] Radeon Display Connectors
[    4.969059] [drm] Internal thermal controller with fan control
[    4.969131] [drm] radeon: power management initialized
[    4.969267] radeon 0000:01:00.0: No connectors reported connected with modes
[    4.969270] [drm] Cannot find any crtc or sizes - going 1024x768
[    4.970615] [drm] fb mappable at 0xA1388000
[    4.970616] [drm] vram apper at 0xA0000000
[    4.970616] [drm] size 3145728
[    4.970617] [drm] fb depth is 24
[    4.970618] [drm]    pitch is 4096
[    4.970746] radeon 0000:01:00.0: fb1: radeondrmfb frame buffer device
[    4.970767] [drm] Initialized radeon 2.34.0 20080528 for 0000:01:00.0 on minor 1
[   11.117501] bio: create slab <bio-1> at 1
[   11.279849] bio: create slab <bio-1> at 1
[   11.406955] EXT4-fs (dm-1): INFO: recovery required on readonly filesystem
[   11.406958] EXT4-fs (dm-1): write access will be enabled during recovery
[   12.024910] EXT4-fs (dm-1): orphan cleanup on readonly fs
[   12.028860] EXT4-fs (dm-1): 13 orphan inodes deleted
[   12.028862] EXT4-fs (dm-1): recovery complete
[   12.067472] EXT4-fs (dm-1): mounted filesystem with ordered data mode. Opts: (null)
[   12.996621] Adding 8241148k swap on /dev/mapper/ubuntu-swap_1.  Priority:-1 extents:1 across:8241148k SSFS
[   13.055555] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.089066] systemd-udevd[459]: starting version 204
[   13.103665] lp: driver loaded but no devices found
[   13.206283] cfg80211: Calling CRDA to update world regulatory domain
[   13.208411] Bluetooth: Core ver 2.16
[   13.208433] NET: Registered protocol family 31
[   13.208435] Bluetooth: HCI device and connection manager initialized
[   13.208444] Bluetooth: HCI socket layer initialized
[   13.208446] Bluetooth: L2CAP socket layer initialized
[   13.208451] Bluetooth: SCO socket layer initialized
[   13.208554] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20130517/utaddress-251)
[   13.208559] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   13.208563] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20130517/utaddress-251)
[   13.208565] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20130517/utaddress-251)
[   13.208567] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   13.208568] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20130517/utaddress-251)
[   13.208570] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20130517/utaddress-251)
[   13.208572] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   13.208573] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   13.213003] Intel(R) Wireless WiFi driver for Linux, in-tree:
[   13.213007] Copyright(c) 2003-2013 Intel Corporation
[   13.213108] iwlwifi 0000:08:00.0: can't disable ASPM; OS doesn't have ASPM control
[   13.213173] usbcore: registered new interface driver btusb
[   13.213238] iwlwifi 0000:08:00.0: irq 46 for MSI/MSI-X
[   13.219422] microcode: CPU0 sig=0x306a9, pf=0x10, revision=0x12
[   13.228613] snd_hda_intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   13.239055] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   13.239417] hda_codec: CX20590: BIOS auto-probing.
[   13.239834] autoconfig: line_outs=1 (0x1f/0x0/0x0/0x0/0x0) type:speaker
[   13.239835]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   13.239836]    hp_outs=1 (0x19/0x0/0x0/0x0/0x0)
[   13.239837]    mono: mono_out=0x0
[   13.239837]    inputs:
[   13.239839]      Internal Mic=0x23
[   13.239840]      Mic=0x1a
[   13.240433] dell_laptop: unknown parameter 'backlight' ignored
[   13.240768] hda_codec: Enable sync_write for stable communication
[   13.246870] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   13.247076] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   13.247155] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   13.257515] type=1400 audit(1384973770.254:2): apparmor="STATUS" operation="profile_load" parent=522 profile="unconfined" name="/sbin/dhclient" pid=561 comm="apparmor_parser"
[   13.257520] type=1400 audit(1384973770.254:3): apparmor="STATUS" operation="profile_load" parent=522 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=561 comm="apparmor_parser"
[   13.257524] type=1400 audit(1384973770.254:4): apparmor="STATUS" operation="profile_load" parent=522 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=561 comm="apparmor_parser"
[   13.257935] type=1400 audit(1384973770.254:5): apparmor="STATUS" operation="profile_replace" parent=522 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=561 comm="apparmor_parser"
[   13.257940] type=1400 audit(1384973770.254:6): apparmor="STATUS" operation="profile_replace" parent=522 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=561 comm="apparmor_parser"
[   13.258164] type=1400 audit(1384973770.254:7): apparmor="STATUS" operation="profile_replace" parent=522 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=561 comm="apparmor_parser"
[   13.258739] type=1400 audit(1384973770.254:8): apparmor="STATUS" operation="profile_replace" parent=559 profile="unconfined" name="/sbin/dhclient" pid=562 comm="apparmor_parser"
[   13.258747] type=1400 audit(1384973770.254:9): apparmor="STATUS" operation="profile_replace" parent=559 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=562 comm="apparmor_parser"
[   13.258752] type=1400 audit(1384973770.254:10): apparmor="STATUS" operation="profile_replace" parent=559 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=562 comm="apparmor_parser"
[   13.259309] type=1400 audit(1384973770.254:11): apparmor="STATUS" operation="profile_replace" parent=559 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=562 comm="apparmor_parser"
[   13.262509] mei_me 0000:00:16.0: setting latency timer to 64
[   13.262551] mei_me 0000:00:16.0: irq 48 for MSI/MSI-X
[   13.269201] iwlwifi 0000:08:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[   13.274845] input: Dell WMI hotkeys as /devices/virtual/input/input9
[   13.289442] rts5139: module is from the staging directory, the quality is unknown, you have been warned.
[   13.289914] Linux video capture interface: v2.00
[   13.290865] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   13.290868] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   13.290871] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   13.290872] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_P2P disabled
[   13.290875] iwlwifi 0000:08:00.0: Detected Intel(R) Centrino(R) Wireless-N 2230 BGN, REV=0xC8
[   13.290973] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[   13.292684] scsi6 : SCSI emulation for RTS5139 USB card reader
[   13.292790] usbcore: registered new interface driver rts5139
[   13.292796] scsi 6:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
[   13.293152] sd 6:0:0:0: Attached scsi generic sg1 type 0
[   13.295659] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_HD (0c45:644a)
[   13.295969] microcode: CPU1 sig=0x306a9, pf=0x10, revision=0x12
[   13.297869] microcode: CPU2 sig=0x306a9, pf=0x10, revision=0x12
[   13.298209] microcode: CPU3 sig=0x306a9, pf=0x10, revision=0x12
[   13.298529] microcode: CPU4 sig=0x306a9, pf=0x10, revision=0x12
[   13.298927] microcode: CPU5 sig=0x306a9, pf=0x10, revision=0x12
[   13.299311] microcode: CPU6 sig=0x306a9, pf=0x10, revision=0x12
[   13.299656] microcode: CPU7 sig=0x306a9, pf=0x10, revision=0x12
[   13.300074] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   13.305168] cfg80211: World regulatory domain updated:
[   13.305173] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.305175] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.305177] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.305179] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.305181] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.305183] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.312696] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   13.321549] input: Laptop_Integrated_Webcam_HD as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input10
[   13.321615] usbcore: registered new interface driver uvcvideo
[   13.321617] USB Video Class driver (1.1.1)
[   13.377581] EXT4-fs (dm-1): re-mounted. Opts: errors=remount-ro
[   13.381779] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   14.138703] init: failsafe main process (817) killed by TERM signal
[   14.196678] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.196681] Bluetooth: BNEP filters: protocol multicast
[   14.196690] Bluetooth: BNEP socket layer initialized
[   14.197003] Bluetooth: RFCOMM TTY layer initialized
[   14.197010] Bluetooth: RFCOMM socket layer initialized
[   14.197012] Bluetooth: RFCOMM ver 1.11
[   14.233491] ppdev: user-space parallel port driver
[   14.234501] init: avahi-cups-reload main process (924) terminated with status 1
[   14.402534] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x450f02)
[   14.412807] r8169 0000:07:00.0 eth0: link down
[   14.412847] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.413067] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.414124] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[   14.421734] iwlwifi 0000:08:00.0: Radio type=0x2-0x0-0x0
[   14.431884] psmouse serio1: elantech: Synaptics capabilities query result 0x79, 0x17, 0x0c.
[   14.597002] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input11
[   14.666411] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[   14.674029] iwlwifi 0000:08:00.0: Radio type=0x2-0x0-0x0
[   14.730728] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.731020] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.097098] ip_tables: (C) 2000-2006 Netfilter Core Team
[   15.109055] radeon: switched off
[   15.343812] init: plymouth-stop pre-start process (1463) terminated with status 1
[   15.892384] wlan0: authenticate with 10:bf:48:3c:f4:a1
[   15.897512] wlan0: send auth to 10:bf:48:3c:f4:a1 (try 1/3)
[   15.939528] wlan0: authenticated
[   15.939746] wlan0: waiting for beacon from 10:bf:48:3c:f4:a1
[   15.968318] wlan0: associate with 10:bf:48:3c:f4:a1 (try 1/3)
[   15.973028] wlan0: RX AssocResp from 10:bf:48:3c:f4:a1 (capab=0xc11 status=0 aid=4)
[   15.992688] wlan0: associated
[   15.992719] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   15.992801] cfg80211: Calling CRDA for country: US
[   15.994954] cfg80211: Regulatory domain changed to country: US
[   15.994957] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   15.994959] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   15.994960] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   15.994961] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.994962] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.994963] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.994964] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   15.994965] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
[   97.839393] psmouse serio1: Touchpad at isa0060/serio1/input0 lost sync at byte 6
[   97.872398] psmouse serio1: Touchpad at isa0060/serio1/input0 - driver resynced.
[  248.140096] psmouse serio1: Touchpad at isa0060/serio1/input0 lost sync at byte 6
[  248.154923] psmouse serio1: Touchpad at isa0060/serio1/input0 lost sync at byte 6
[  248.169726] psmouse serio1: Touchpad at isa0060/serio1/input0 lost sync at byte 6
[  248.184510] psmouse serio1: Touchpad at isa0060/serio1/input0 lost sync at byte 6
[  248.202839] psmouse serio1: Touchpad at isa0060/serio1/input0 lost sync at byte 6
[  248.202848] psmouse serio1: issuing reconnect request
[  248.411745] ACPI: \_SB_.PCI0: ACPI_NOTIFY_BUS_CHECK event: unsupported
[  248.411759] ACPI: \_SB_.PCI0: Bus check notify on _handle_hotplug_event_root
[  248.652228] wlan0: deauthenticating from 10:bf:48:3c:f4:a1 by local choice (reason=3)
[  248.689021] cfg80211: Calling CRDA to update world regulatory domain
[  248.693801] cfg80211: World regulatory domain updated:
[  248.693807] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  248.693811] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  248.693814] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  248.693817] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  248.693819] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  248.693821] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  249.212280] radeon: switched on
[  249.232508] [drm] probing gen 2 caps for device 8086:151 = 261ac83/e
[  249.232512] [drm] enabling PCIE gen 3 link speeds, disable with radeon.pcie_gen2=0
[  250.571341] [drm] PCIE GART of 512M enabled (table at 0x0000000000379000).
[  250.571469] radeon 0000:01:00.0: WB enabled
[  250.571474] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00 and cpu addr 0xffff88024cae0c00
[  250.571476] radeon 0000:01:00.0: fence driver on ring 1 use gpu addr 0x0000000080000c04 and cpu addr 0xffff88024cae0c04
[  250.571478] radeon 0000:01:00.0: fence driver on ring 2 use gpu addr 0x0000000080000c08 and cpu addr 0xffff88024cae0c08
[  250.571480] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c and cpu addr 0xffff88024cae0c0c
[  250.571482] radeon 0000:01:00.0: fence driver on ring 4 use gpu addr 0x0000000080000c10 and cpu addr 0xffff88024cae0c10
[  250.572256] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000075a18 and cpu addr 0xffffc90021db5a18
[  250.591568] [drm] ring test on 0 succeeded in 1 usecs
[  250.591573] [drm] ring test on 1 succeeded in 1 usecs
[  250.591577] [drm] ring test on 2 succeeded in 1 usecs
[  250.591637] [drm] ring test on 3 succeeded in 2 usecs
[  250.591645] [drm] ring test on 4 succeeded in 1 usecs
[  250.777511] [drm] ring test on 5 succeeded in 1 usecs
[  250.777515] [drm] UVD initialized successfully.
[  250.781290] [drm] ib test on ring 0 succeeded in 0 usecs
[  250.781314] [drm] ib test on ring 1 succeeded in 0 usecs
[  250.781338] [drm] ib test on ring 2 succeeded in 0 usecs
[  250.781364] [drm] ib test on ring 3 succeeded in 0 usecs
[  250.781388] [drm] ib test on ring 4 succeeded in 0 usecs
[  250.933914] [drm] ib test on ring 5 succeeded
[  251.032622] PM: Syncing filesystems ... done.
[  251.043287] PM: Preparing system for mem sleep
[  251.158750] Freezing user space processes ... (elapsed 0.001 seconds) done.
[  251.160004] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
[  251.161094] PM: Entering mem sleep
[  251.161132] Suspending console(s) (use no_console_suspend to debug)
[  251.161715] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[  251.162647] sd 0:0:0:0: [sda] Stopping disk
[  251.198967] mei_me 0000:00:16.0: suspend
[  251.742766] PM: suspend of devices complete after 580.921 msecs
[  251.742904] PM: late suspend of devices complete after 0.136 msecs
[  251.758784] pcieport 0000:00:1c.0: System wakeup enabled by ACPI
[  251.774786] ehci-pci 0000:00:1d.0: System wakeup enabled by ACPI
[  251.822767] xhci_hcd 0000:00:14.0: System wakeup enabled by ACPI
[  251.838787] PM: noirq suspend of devices complete after 95.781 msecs
[  251.839008] ACPI: Preparing to enter system sleep state S3
[  251.842875] PM: Saving platform NVS memory
[  251.843459] Disabling non-boot CPUs ...
[  251.844776] smpboot: CPU 1 is now offline
[  251.845272] Broke affinity for irq 46
[  251.946864] smpboot: CPU 2 is now offline
[  252.050973] smpboot: CPU 3 is now offline
[  252.155085] smpboot: CPU 4 is now offline
[  252.155529] Broke affinity for irq 42
[  252.259187] smpboot: CPU 5 is now offline
[  252.363295] smpboot: CPU 6 is now offline
[  252.467403] smpboot: CPU 7 is now offline
[  252.468677] ACPI: Low-level resume complete
[  252.468718] PM: Restoring platform NVS memory
[  252.469181] Enabling non-boot CPUs ...
[  252.469219] smpboot: Booting Node 0 Processor 1 APIC 0x1
[  252.483213] CPU1 is up
[  252.483230] smpboot: Booting Node 0 Processor 2 APIC 0x2
[  252.497074] CPU2 is up
[  252.497092] smpboot: Booting Node 0 Processor 3 APIC 0x3
[  252.510942] CPU3 is up
[  252.510959] smpboot: Booting Node 0 Processor 4 APIC 0x4
[  252.524699] CPU4 is up
[  252.524715] smpboot: Booting Node 0 Processor 5 APIC 0x5
[  252.538471] CPU5 is up
[  252.538488] smpboot: Booting Node 0 Processor 6 APIC 0x6
[  252.552340] CPU6 is up
[  252.552357] smpboot: Booting Node 0 Processor 7 APIC 0x7
[  252.566231] CPU7 is up
[  252.573336] ACPI: Waking up from system sleep state S3
[  252.609157] xhci_hcd 0000:00:14.0: System wakeup disabled by ACPI
[  252.673215] ehci-pci 0000:00:1d.0: System wakeup disabled by ACPI
[  252.737443] PM: noirq resume of devices complete after 160.131 msecs
[  252.737556] PM: early resume of devices complete after 0.091 msecs
[  252.737578] i915 0000:00:02.0: setting latency timer to 64
[  252.737598] xhci_hcd 0000:00:14.0: setting latency timer to 64
[  252.737611] mei_me 0000:00:16.0: irq 47 for MSI/MSI-X
[  252.737683] ahci 0000:00:1f.2: setting latency timer to 64
[  252.737735] ehci-pci 0000:00:1a.0: setting latency timer to 64
[  252.737970] pcieport 0000:00:1c.0: System wakeup disabled by ACPI
[  252.737976] snd_hda_intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[  252.737994] ehci-pci 0000:00:1d.0: setting latency timer to 64
[  252.741404] [drm] probing gen 2 caps for device 8086:151 = 261ac83/e
[  252.741406] [drm] enabling PCIE gen 3 link speeds, disable with radeon.pcie_gen2=0
[  252.937506] dpm_run_callback(): pnp_bus_resume+0x0/0x80 returns -19
[  252.937507] PM: Device 00:07 failed to resume: error -19
[  252.949521] usb 1-1.5: reset high-speed USB device number 4 using ehci-pci
[  253.057554] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[  253.112718] ata1.00: configured for UDMA/133
[  253.117725] usb 2-1.5: reset full-speed USB device number 3 using ehci-pci
[  253.125706] sd 0:0:0:0: [sda] Starting disk
[  253.281869] usb 1-1.3: reset high-speed USB device number 3 using ehci-pci
[  254.082919] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off
[  254.296161] [drm] PCIE GART of 512M enabled (table at 0x0000000000379000).
[  254.296260] radeon 0000:01:00.0: WB enabled
[  254.296261] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00 and cpu addr 0xffff88024cae0c00
[  254.296262] radeon 0000:01:00.0: fence driver on ring 1 use gpu addr 0x0000000080000c04 and cpu addr 0xffff88024cae0c04
[  254.296263] radeon 0000:01:00.0: fence driver on ring 2 use gpu addr 0x0000000080000c08 and cpu addr 0xffff88024cae0c08
[  254.296264] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c and cpu addr 0xffff88024cae0c0c
[  254.296265] radeon 0000:01:00.0: fence driver on ring 4 use gpu addr 0x0000000080000c10 and cpu addr 0xffff88024cae0c10
[  254.297043] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000075a18 and cpu addr 0xffffc90021db5a18
[  254.315702] [drm] ring test on 0 succeeded in 1 usecs
[  254.315705] [drm] ring test on 1 succeeded in 1 usecs
[  254.315708] [drm] ring test on 2 succeeded in 1 usecs
[  254.315766] [drm] ring test on 3 succeeded in 2 usecs
[  254.315772] [drm] ring test on 4 succeeded in 1 usecs
[  254.501543] [drm] ring test on 5 succeeded in 1 usecs
[  254.501545] [drm] UVD initialized successfully.
[  254.502972] [drm] ib test on ring 0 succeeded in 0 usecs
[  254.502991] [drm] ib test on ring 1 succeeded in 0 usecs
[  254.503010] [drm] ib test on ring 2 succeeded in 0 usecs
[  254.503030] [drm] ib test on ring 3 succeeded in 0 usecs
[  254.503051] [drm] ib test on ring 4 succeeded in 0 usecs
[  254.655236] [drm] ib test on ring 5 succeeded
[  254.668006] PM: resume of devices complete after 1928.427 msecs
[  254.668278] PM: Finishing wakeup.
[  254.668279] Restarting tasks ... done.
[  254.747536] video LNXVIDEO:00: Restoring backlight state
[  254.747540] video LNXVIDEO:02: Restoring backlight state
[  255.004826] radeon: switched off
[  255.522274] r8169 0000:07:00.0 eth0: link down
[  255.522335] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  255.523067] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[  255.530672] iwlwifi 0000:08:00.0: Radio type=0x2-0x0-0x0
[  255.605049] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  256.878133] wlan0: authenticate with 10:bf:48:3c:f4:a1
[  256.883368] wlan0: send auth to 10:bf:48:3c:f4:a1 (try 1/3)
[  256.885925] wlan0: authenticated
[  256.889589] wlan0: associate with 10:bf:48:3c:f4:a1 (try 1/3)
[  256.893393] wlan0: RX AssocResp from 10:bf:48:3c:f4:a1 (capab=0xc11 status=0 aid=2)
[  256.913102] wlan0: associated
[  256.913159] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  256.913345] cfg80211: Calling CRDA for country: US
[  256.917655] cfg80211: Regulatory domain changed to country: US
[  256.917661] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  256.917665] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  256.917668] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  256.917670] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  256.917672] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  256.917675] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  256.917677] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[  256.917680] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
[  260.137620] psmouse serio1: Touchpad at isa0060/serio1/input0 lost sync at byte 6
[  260.152434] psmouse serio1: Touchpad at isa0060/serio1/input0 lost sync at byte 6
[  260.170730] psmouse serio1: Touchpad at isa0060/serio1/input0 lost sync at byte 6
[  260.339361] ACPI: \_SB_.PCI0: ACPI_NOTIFY_BUS_CHECK event: unsupported
[  260.339376] ACPI: \_SB_.PCI0: Bus check notify on _handle_hotplug_event_root
[  260.523245] psmouse serio1: Touchpad at isa0060/serio1/input0 - driver resynced.
[  260.558062] wlan0: deauthenticating from 10:bf:48:3c:f4:a1 by local choice (reason=3)
[  260.587383] cfg80211: Calling CRDA to update world regulatory domain
[  260.591332] cfg80211: World regulatory domain updated:
[  260.591337] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  260.591341] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  260.591344] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  260.591346] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  260.591349] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  260.591351] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  261.086090] radeon: switched on
[  261.106502] [drm] probing gen 2 caps for device 8086:151 = 261ac83/e
[  261.106505] [drm] enabling PCIE gen 3 link speeds, disable with radeon.pcie_gen2=0
[  262.443950] [drm] PCIE GART of 512M enabled (table at 0x0000000000379000).
[  262.444109] radeon 0000:01:00.0: WB enabled
[  262.444113] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00 and cpu addr 0xffff88024cae0c00
[  262.444115] radeon 0000:01:00.0: fence driver on ring 1 use gpu addr 0x0000000080000c04 and cpu addr 0xffff88024cae0c04
[  262.444117] radeon 0000:01:00.0: fence driver on ring 2 use gpu addr 0x0000000080000c08 and cpu addr 0xffff88024cae0c08
[  262.444119] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c and cpu addr 0xffff88024cae0c0c
[  262.444121] radeon 0000:01:00.0: fence driver on ring 4 use gpu addr 0x0000000080000c10 and cpu addr 0xffff88024cae0c10
[  262.444895] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000075a18 and cpu addr 0xffffc90021db5a18
[  262.464247] [drm] ring test on 0 succeeded in 1 usecs
[  262.464251] [drm] ring test on 1 succeeded in 1 usecs
[  262.464255] [drm] ring test on 2 succeeded in 1 usecs
[  262.464315] [drm] ring test on 3 succeeded in 2 usecs
[  262.464323] [drm] ring test on 4 succeeded in 1 usecs
[  262.650191] [drm] ring test on 5 succeeded in 1 usecs
[  262.650195] [drm] UVD initialized successfully.
[  262.653910] [drm] ib test on ring 0 succeeded in 0 usecs
[  262.653934] [drm] ib test on ring 1 succeeded in 0 usecs
[  262.653958] [drm] ib test on ring 2 succeeded in 0 usecs
[  262.653984] [drm] ib test on ring 3 succeeded in 0 usecs
[  262.654008] [drm] ib test on ring 4 succeeded in 0 usecs
[  262.807774] [drm] ib test on ring 5 succeeded
[  262.915320] PM: Syncing filesystems ... done.
[  262.934428] PM: Preparing system for mem sleep
[  263.052335] Freezing user space processes ... (elapsed 0.001 seconds) done.
[  263.053773] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
[  263.055096] PM: Entering mem sleep
[  263.055143] Suspending console(s) (use no_console_suspend to debug)
[  263.056179] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[  263.060503] sd 0:0:0:0: [sda] Stopping disk
[  263.090788] mei_me 0000:00:16.0: suspend
[  263.600671] PM: suspend of devices complete after 544.844 msecs
[  263.600811] PM: late suspend of devices complete after 0.137 msecs
[  263.616729] pcieport 0000:00:1c.0: System wakeup enabled by ACPI
[  263.632744] ehci-pci 0000:00:1d.0: System wakeup enabled by ACPI
[  263.680714] xhci_hcd 0000:00:14.0: System wakeup enabled by ACPI
[  263.696750] PM: noirq suspend of devices complete after 95.837 msecs
[  263.696972] ACPI: Preparing to enter system sleep state S3
[  263.697175] PM: Saving platform NVS memory
[  263.697807] Disabling non-boot CPUs ...
[  263.800774] smpboot: CPU 1 is now offline
[  263.904886] smpboot: CPU 2 is now offline
[  263.905347] Broke affinity for irq 23
[  264.008985] smpboot: CPU 3 is now offline
[  264.113103] smpboot: CPU 4 is now offline
[  264.217204] smpboot: CPU 5 is now offline
[  264.321315] smpboot: CPU 6 is now offline
[  264.425417] smpboot: CPU 7 is now offline
[  264.426769] ACPI: Low-level resume complete
[  264.426811] PM: Restoring platform NVS memory
[  264.427292] Enabling non-boot CPUs ...
[  264.427341] smpboot: Booting Node 0 Processor 1 APIC 0x1
[  264.441278] CPU1 is up
[  264.441296] smpboot: Booting Node 0 Processor 2 APIC 0x2
[  264.455141] CPU2 is up
[  264.455158] smpboot: Booting Node 0 Processor 3 APIC 0x3
[  264.468908] CPU3 is up
[  264.468926] smpboot: Booting Node 0 Processor 4 APIC 0x4
[  264.482671] CPU4 is up
[  264.482688] smpboot: Booting Node 0 Processor 5 APIC 0x5
[  264.496445] CPU5 is up
[  264.496462] smpboot: Booting Node 0 Processor 6 APIC 0x6
[  264.510318] CPU6 is up
[  264.510334] smpboot: Booting Node 0 Processor 7 APIC 0x7
[  264.524107] CPU7 is up
[  264.531264] ACPI: Waking up from system sleep state S3
[  264.567173] xhci_hcd 0000:00:14.0: System wakeup disabled by ACPI
[  264.631229] ehci-pci 0000:00:1d.0: System wakeup disabled by ACPI
[  264.695461] PM: noirq resume of devices complete after 160.130 msecs
[  264.695575] PM: early resume of devices complete after 0.093 msecs
[  264.695597] i915 0000:00:02.0: setting latency timer to 64
[  264.695619] xhci_hcd 0000:00:14.0: setting latency timer to 64
[  264.695643] mei_me 0000:00:16.0: irq 47 for MSI/MSI-X
[  264.695652] ahci 0000:00:1f.2: setting latency timer to 64
[  264.695736] ehci-pci 0000:00:1a.0: setting latency timer to 64
[  264.695869] snd_hda_intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[  264.695994] ehci-pci 0000:00:1d.0: setting latency timer to 64
[  264.696067] pcieport 0000:00:1c.0: System wakeup disabled by ACPI
[  264.699529] [drm] probing gen 2 caps for device 8086:151 = 261ac83/e
[  264.699531] [drm] enabling PCIE gen 3 link speeds, disable with radeon.pcie_gen2=0
[  264.895523] dpm_run_callback(): pnp_bus_resume+0x0/0x80 returns -19
[  264.895524] PM: Device 00:07 failed to resume: error -19
[  264.907526] usb 1-1.5: reset high-speed USB device number 4 using ehci-pci
[  265.015566] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[  265.069445] ata1.00: configured for UDMA/133
[  265.075705] usb 2-1.5: reset full-speed USB device number 3 using ehci-pci
[  265.083703] sd 0:0:0:0: [sda] Starting disk
[  265.239874] usb 1-1.3: reset high-speed USB device number 3 using ehci-pci
[  266.072965] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off
[  266.254148] [drm] PCIE GART of 512M enabled (table at 0x0000000000379000).
[  266.254263] radeon 0000:01:00.0: WB enabled
[  266.254265] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00 and cpu addr 0xffff88024cae0c00
[  266.254265] radeon 0000:01:00.0: fence driver on ring 1 use gpu addr 0x0000000080000c04 and cpu addr 0xffff88024cae0c04
[  266.254266] radeon 0000:01:00.0: fence driver on ring 2 use gpu addr 0x0000000080000c08 and cpu addr 0xffff88024cae0c08
[  266.254267] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c and cpu addr 0xffff88024cae0c0c
[  266.254268] radeon 0000:01:00.0: fence driver on ring 4 use gpu addr 0x0000000080000c10 and cpu addr 0xffff88024cae0c10
[  266.255038] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000075a18 and cpu addr 0xffffc90021db5a18
[  266.273697] [drm] ring test on 0 succeeded in 1 usecs
[  266.273700] [drm] ring test on 1 succeeded in 1 usecs
[  266.273703] [drm] ring test on 2 succeeded in 1 usecs
[  266.273761] [drm] ring test on 3 succeeded in 2 usecs
[  266.273767] [drm] ring test on 4 succeeded in 1 usecs
[  266.459538] [drm] ring test on 5 succeeded in 1 usecs
[  266.459539] [drm] UVD initialized successfully.
[  266.460966] [drm] ib test on ring 0 succeeded in 0 usecs
[  266.460985] [drm] ib test on ring 1 succeeded in 0 usecs
[  266.461004] [drm] ib test on ring 2 succeeded in 0 usecs
[  266.461024] [drm] ib test on ring 3 succeeded in 0 usecs
[  266.461043] [drm] ib test on ring 4 succeeded in 0 usecs
[  266.613300] [drm] ib test on ring 5 succeeded
[  266.628265] PM: resume of devices complete after 1930.665 msecs
[  266.628482] PM: Finishing wakeup.
[  266.628482] Restarting tasks ... done.
[  266.705563] video LNXVIDEO:00: Restoring backlight state
[  266.705567] video LNXVIDEO:02: Restoring backlight state
[  266.941940] radeon: switched off
[  267.460267] r8169 0000:07:00.0 eth0: link down
[  267.460351] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  267.461897] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[  267.469578] iwlwifi 0000:08:00.0: Radio type=0x2-0x0-0x0
[  267.541698] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  268.743426] wlan0: authenticate with 10:bf:48:3c:f4:a1
[  268.748166] wlan0: send auth to 10:bf:48:3c:f4:a1 (try 1/3)
[  268.753605] wlan0: authenticated
[  268.755522] wlan0: associate with 10:bf:48:3c:f4:a1 (try 1/3)
[  268.759457] wlan0: RX AssocResp from 10:bf:48:3c:f4:a1 (capab=0xc11 status=0 aid=2)
[  268.779691] wlan0: associated
[  268.779750] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  268.779953] cfg80211: Calling CRDA for country: US
[  268.784112] cfg80211: Regulatory domain changed to country: US
[  268.784117] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  268.784121] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  268.784123] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  268.784126] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  268.784128] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  268.784131] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  268.784133] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[  268.784136] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
[  272.643349] psmouse serio1: Touchpad at isa0060/serio1/input0 lost sync at byte 6
[  272.658127] psmouse serio1: Touchpad at isa0060/serio1/input0 lost sync at byte 6
[  272.672910] psmouse serio1: Touchpad at isa0060/serio1/input0 lost sync at byte 6
[  272.687699] psmouse serio1: Touchpad at isa0060/serio1/input0 lost sync at byte 6
[  272.702514] psmouse serio1: Touchpad at isa0060/serio1/input0 lost sync at byte 6
[  272.702522] psmouse serio1: issuing reconnect request
[  272.889549] ACPI: \_SB_.PCI0: ACPI_NOTIFY_BUS_CHECK event: unsupported
[  272.889563] ACPI: \_SB_.PCI0: Bus check notify on _handle_hotplug_event_root
[  273.108007] wlan0: deauthenticating from 10:bf:48:3c:f4:a1 by local choice (reason=3)
[  273.144909] cfg80211: Calling CRDA to update world regulatory domain
[  273.149038] cfg80211: World regulatory domain updated:
[  273.149044] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  273.149048] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  273.149050] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  273.149053] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  273.149055] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  273.149058] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  273.715711] radeon: switched on
[  273.736135] [drm] probing gen 2 caps for device 8086:151 = 261ac83/e
[  273.736139] [drm] enabling PCIE gen 3 link speeds, disable with radeon.pcie_gen2=0
[  275.074110] [drm] PCIE GART of 512M enabled (table at 0x0000000000379000).
[  275.074291] radeon 0000:01:00.0: WB enabled
[  275.074296] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00 and cpu addr 0xffff88024cae0c00
[  275.074298] radeon 0000:01:00.0: fence driver on ring 1 use gpu addr 0x0000000080000c04 and cpu addr 0xffff88024cae0c04
[  275.074300] radeon 0000:01:00.0: fence driver on ring 2 use gpu addr 0x0000000080000c08 and cpu addr 0xffff88024cae0c08
[  275.074302] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c and cpu addr 0xffff88024cae0c0c
[  275.074304] radeon 0000:01:00.0: fence driver on ring 4 use gpu addr 0x0000000080000c10 and cpu addr 0xffff88024cae0c10
[  275.075078] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000075a18 and cpu addr 0xffffc90021db5a18
[  275.094349] [drm] ring test on 0 succeeded in 1 usecs
[  275.094353] [drm] ring test on 1 succeeded in 1 usecs
[  275.094357] [drm] ring test on 2 succeeded in 1 usecs
[  275.094418] [drm] ring test on 3 succeeded in 2 usecs
[  275.094426] [drm] ring test on 4 succeeded in 1 usecs
[  275.280290] [drm] ring test on 5 succeeded in 1 usecs
[  275.280293] [drm] UVD initialized successfully.
[  275.284072] [drm] ib test on ring 0 succeeded in 0 usecs
[  275.284096] [drm] ib test on ring 1 succeeded in 0 usecs
[  275.284120] [drm] ib test on ring 2 succeeded in 0 usecs
[  275.284145] [drm] ib test on ring 3 succeeded in 0 usecs
[  275.284169] [drm] ib test on ring 4 succeeded in 0 usecs
[  275.436472] [drm] ib test on ring 5 succeeded
[  275.593898] PM: Syncing filesystems ... done.
[  275.615390] PM: Preparing system for mem sleep
[  275.732941] Freezing user space processes ... (elapsed 0.001 seconds) done.
[  275.734318] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
[  275.735488] PM: Entering mem sleep
[  275.735530] Suspending console(s) (use no_console_suspend to debug)
[  275.737492] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[  275.739535] sd 0:0:0:0: [sda] Stopping disk
[  275.769220] mei_me 0000:00:16.0: suspend
[  276.269071] PM: suspend of devices complete after 533.146 msecs
[  276.269211] PM: late suspend of devices complete after 0.138 msecs
[  276.285042] pcieport 0000:00:1c.0: System wakeup enabled by ACPI
[  276.301044] ehci-pci 0000:00:1d.0: System wakeup enabled by ACPI
[  276.348991] xhci_hcd 0000:00:14.0: System wakeup enabled by ACPI
[  276.365023] PM: noirq suspend of devices complete after 95.758 msecs
[  276.365246] ACPI: Preparing to enter system sleep state S3
[  276.365450] PM: Saving platform NVS memory
[  276.366092] Disabling non-boot CPUs ...
[  276.468996] smpboot: CPU 1 is now offline
[  276.573058] smpboot: CPU 2 is now offline
[  276.677111] smpboot: CPU 3 is now offline
[  276.781180] smpboot: CPU 4 is now offline
[  276.885246] smpboot: CPU 5 is now offline
[  276.989275] smpboot: CPU 6 is now offline
[  277.093335] smpboot: CPU 7 is now offline
[  277.094730] ACPI: Low-level resume complete
[  277.094772] PM: Restoring platform NVS memory
[  277.095257] Enabling non-boot CPUs ...
[  277.095306] smpboot: Booting Node 0 Processor 1 APIC 0x1
[  277.109239] CPU1 is up
[  277.109257] smpboot: Booting Node 0 Processor 2 APIC 0x2
[  277.123100] CPU2 is up
[  277.123118] smpboot: Booting Node 0 Processor 3 APIC 0x3
[  277.136978] CPU3 is up
[  277.136996] smpboot: Booting Node 0 Processor 4 APIC 0x4
[  277.150839] CPU4 is up
[  277.150856] smpboot: Booting Node 0 Processor 5 APIC 0x5
[  277.164616] CPU5 is up
[  277.164634] smpboot: Booting Node 0 Processor 6 APIC 0x6
[  277.178498] CPU6 is up
[  277.178515] smpboot: Booting Node 0 Processor 7 APIC 0x7
[  277.192287] CPU7 is up
[  277.199400] ACPI: Waking up from system sleep state S3
[  277.235044] xhci_hcd 0000:00:14.0: System wakeup disabled by ACPI
[  277.299067] ehci-pci 0000:00:1d.0: System wakeup disabled by ACPI
[  277.363270] PM: noirq resume of devices complete after 160.142 msecs
[  277.363383] PM: early resume of devices complete after 0.091 msecs
[  277.363409] i915 0000:00:02.0: setting latency timer to 64
[  277.363430] xhci_hcd 0000:00:14.0: setting latency timer to 64
[  277.363453] mei_me 0000:00:16.0: irq 47 for MSI/MSI-X
[  277.363464] ahci 0000:00:1f.2: setting latency timer to 64
[  277.363548] ehci-pci 0000:00:1a.0: setting latency timer to 64
[  277.363627] snd_hda_intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[  277.363735] ehci-pci 0000:00:1d.0: setting latency timer to 64
[  277.363779] pcieport 0000:00:1c.0: System wakeup disabled by ACPI
[  277.367151] [drm] probing gen 2 caps for device 8086:151 = 261ac83/e
[  277.367153] [drm] enabling PCIE gen 3 link speeds, disable with radeon.pcie_gen2=0
[  277.563228] dpm_run_callback(): pnp_bus_resume+0x0/0x80 returns -19
[  277.563229] PM: Device 00:07 failed to resume: error -19
[  277.575237] usb 1-1.3: reset high-speed USB device number 3 using ehci-pci
[  277.691209] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[  277.739400] usb 1-1.5: reset high-speed USB device number 4 using ehci-pci
[  277.745466] ata1.00: configured for UDMA/133
[  277.759292] sd 0:0:0:0: [sda] Starting disk
[  277.907453] usb 2-1.5: reset full-speed USB device number 3 using ehci-pci
[  278.916045] [drm] PCIE GART of 512M enabled (table at 0x0000000000379000).
[  278.916170] radeon 0000:01:00.0: WB enabled
[  278.916172] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00 and cpu addr 0xffff88024cae0c00
[  278.916173] radeon 0000:01:00.0: fence driver on ring 1 use gpu addr 0x0000000080000c04 and cpu addr 0xffff88024cae0c04
[  278.916174] radeon 0000:01:00.0: fence driver on ring 2 use gpu addr 0x0000000080000c08 and cpu addr 0xffff88024cae0c08
[  278.916174] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c and cpu addr 0xffff88024cae0c0c
[  278.916175] radeon 0000:01:00.0: fence driver on ring 4 use gpu addr 0x0000000080000c10 and cpu addr 0xffff88024cae0c10
[  278.916959] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000075a18 and cpu addr 0xffffc90021db5a18
[  278.935622] [drm] ring test on 0 succeeded in 1 usecs
[  278.935625] [drm] ring test on 1 succeeded in 1 usecs
[  278.935628] [drm] ring test on 2 succeeded in 1 usecs
[  278.935686] [drm] ring test on 3 succeeded in 2 usecs
[  278.935693] [drm] ring test on 4 succeeded in 1 usecs
[  279.084340] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off
[  279.121469] [drm] ring test on 5 succeeded in 1 usecs
[  279.121471] [drm] UVD initialized successfully.
[  279.122926] [drm] ib test on ring 0 succeeded in 0 usecs
[  279.122947] [drm] ib test on ring 1 succeeded in 0 usecs
[  279.122965] [drm] ib test on ring 2 succeeded in 0 usecs
[  279.122985] [drm] ib test on ring 3 succeeded in 0 usecs
[  279.123005] [drm] ib test on ring 4 succeeded in 0 usecs
[  279.276226] [drm] ib test on ring 5 succeeded
[  279.285821] PM: resume of devices complete after 1921.384 msecs
[  279.286038] PM: Finishing wakeup.
[  279.286039] Restarting tasks ... done.
[  279.364346] video LNXVIDEO:00: Restoring backlight state
[  279.364350] video LNXVIDEO:02: Restoring backlight state
[  279.623751] radeon: switched off
[  280.158694] r8169 0000:07:00.0 eth0: link down
[  280.158782] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  280.160171] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[  280.167813] iwlwifi 0000:08:00.0: Radio type=0x2-0x0-0x0
[  280.236058] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  281.428140] wlan0: authenticate with 10:bf:48:3c:f4:a1
[  281.433348] wlan0: send auth to 10:bf:48:3c:f4:a1 (try 1/3)
[  281.435809] wlan0: authenticated
[  281.437269] wlan0: associate with 10:bf:48:3c:f4:a1 (try 1/3)
[  281.442883] wlan0: RX AssocResp from 10:bf:48:3c:f4:a1 (capab=0xc11 status=0 aid=2)
[  281.464219] wlan0: associated
[  281.464277] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  281.464456] cfg80211: Calling CRDA for country: US
[  281.468547] cfg80211: Regulatory domain changed to country: US
[  281.468553] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  281.468557] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  281.468560] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  281.468562] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  281.468564] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  281.468567] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  281.468569] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[  281.468572] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
[  282.234603] psmouse serio1: Touchpad at isa0060/serio1/input0 lost sync at byte 6
[  282.249418] psmouse serio1: Touchpad at isa0060/serio1/input0 lost sync at byte 6
[  282.264715] psmouse serio1: Touchpad at isa0060/serio1/input0 lost sync at byte 6
[  282.279499] psmouse serio1: Touchpad at isa0060/serio1/input0 lost sync at byte 6
[  282.294293] psmouse serio1: Touchpad at isa0060/serio1/input0 lost sync at byte 6
[  282.294302] psmouse serio1: issuing reconnect request
[  282.679102] ACPI: \_SB_.PCI0: ACPI_NOTIFY_BUS_CHECK event: unsupported
[  282.679116] ACPI: \_SB_.PCI0: Bus check notify on _handle_hotplug_event_root
[  282.946869] wlan0: deauthenticating from 10:bf:48:3c:f4:a1 by local choice (reason=3)
[  282.975066] cfg80211: Calling CRDA to update world regulatory domain
[  283.030479] cfg80211: World regulatory domain updated:
[  283.030489] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  283.030494] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  283.030499] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  283.030503] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  283.030507] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  283.030510] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  283.466551] radeon: switched on
[  283.486952] [drm] probing gen 2 caps for device 8086:151 = 261ac83/e
[  283.486955] [drm] enabling PCIE gen 3 link speeds, disable with radeon.pcie_gen2=0
[  284.808013] [drm] PCIE GART of 512M enabled (table at 0x0000000000379000).
[  284.808145] radeon 0000:01:00.0: WB enabled
[  284.808150] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00 and cpu addr 0xffff88024cae0c00
[  284.808152] radeon 0000:01:00.0: fence driver on ring 1 use gpu addr 0x0000000080000c04 and cpu addr 0xffff88024cae0c04
[  284.808154] radeon 0000:01:00.0: fence driver on ring 2 use gpu addr 0x0000000080000c08 and cpu addr 0xffff88024cae0c08
[  284.808156] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c and cpu addr 0xffff88024cae0c0c
[  284.808158] radeon 0000:01:00.0: fence driver on ring 4 use gpu addr 0x0000000080000c10 and cpu addr 0xffff88024cae0c10
[  284.808932] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000075a18 and cpu addr 0xffffc90021db5a18
[  284.828187] [drm] ring test on 0 succeeded in 1 usecs
[  284.828191] [drm] ring test on 1 succeeded in 1 usecs
[  284.828195] [drm] ring test on 2 succeeded in 1 usecs
[  284.828254] [drm] ring test on 3 succeeded in 2 usecs
[  284.828260] [drm] ring test on 4 succeeded in 1 usecs
[  285.014044] [drm] ring test on 5 succeeded in 1 usecs
[  285.014046] [drm] UVD initialized successfully.
[  285.015489] [drm] ib test on ring 0 succeeded in 0 usecs
[  285.015509] [drm] ib test on ring 1 succeeded in 0 usecs
[  285.015528] [drm] ib test on ring 2 succeeded in 0 usecs
[  285.015548] [drm] ib test on ring 3 succeeded in 0 usecs
[  285.015567] [drm] ib test on ring 4 succeeded in 0 usecs
[  285.168006] [drm] ib test on ring 5 succeeded
[  285.274598] PM: Syncing filesystems ... done.
[  285.291503] PM: Preparing system for mem sleep
[  285.424537] Freezing user space processes ... (elapsed 0.001 seconds) done.
[  285.425883] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
[  285.427059] PM: Entering mem sleep
[  285.427103] Suspending console(s) (use no_console_suspend to debug)
[  285.428672] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[  285.433181] sd 0:0:0:0: [sda] Stopping disk
[  285.468262] mei_me 0000:00:16.0: suspend
[  285.932820] PM: suspend of devices complete after 505.085 msecs
[  285.932930] PM: late suspend of devices complete after 0.108 msecs
[  285.948855] pcieport 0000:00:1c.0: System wakeup enabled by ACPI
[  285.964885] ehci-pci 0000:00:1d.0: System wakeup enabled by ACPI
[  286.012870] xhci_hcd 0000:00:14.0: System wakeup enabled by ACPI
[  286.028892] PM: noirq suspend of devices complete after 95.861 msecs
[  286.029138] ACPI: Preparing to enter system sleep state S3
[  286.029338] PM: Saving platform NVS memory
[  286.029948] Disabling non-boot CPUs ...
[  286.132908] smpboot: CPU 1 is now offline
[  286.237016] smpboot: CPU 2 is now offline
[  286.341126] smpboot: CPU 3 is now offline
[  286.445234] smpboot: CPU 4 is now offline
[  286.549340] smpboot: CPU 5 is now offline
[  286.653450] smpboot: CPU 6 is now offline
[  286.757559] smpboot: CPU 7 is now offline
[  286.758899] ACPI: Low-level resume complete
[  286.758941] PM: Restoring platform NVS memory
[  286.759473] Enabling non-boot CPUs ...
[  286.759509] smpboot: Booting Node 0 Processor 1 APIC 0x1
[  286.773353] CPU1 is up
[  286.773371] smpboot: Booting Node 0 Processor 2 APIC 0x2
[  286.787217] CPU2 is up
[  286.787235] smpboot: Booting Node 0 Processor 3 APIC 0x3
[  286.801082] CPU3 is up
[  286.801100] smpboot: Booting Node 0 Processor 4 APIC 0x4
[  286.814947] CPU4 is up
[  286.814963] smpboot: Booting Node 0 Processor 5 APIC 0x5
[  286.828820] CPU5 is up
[  286.828838] smpboot: Booting Node 0 Processor 6 APIC 0x6
[  286.842691] CPU6 is up
[  286.842707] smpboot: Booting Node 0 Processor 7 APIC 0x7
[  286.856576] CPU7 is up
[  286.863695] ACPI: Waking up from system sleep state S3
[  286.899308] xhci_hcd 0000:00:14.0: System wakeup disabled by ACPI
[  286.963368] ehci-pci 0000:00:1d.0: System wakeup disabled by ACPI
[  287.027599] PM: noirq resume of devices complete after 160.147 msecs
[  287.027713] PM: early resume of devices complete after 0.091 msecs
[  287.027737] i915 0000:00:02.0: setting latency timer to 64
[  287.027759] xhci_hcd 0000:00:14.0: setting latency timer to 64
[  287.027772] mei_me 0000:00:16.0: irq 47 for MSI/MSI-X
[  287.027849] ehci-pci 0000:00:1a.0: setting latency timer to 64
[  287.027882] ahci 0000:00:1f.2: setting latency timer to 64
[  287.028009] snd_hda_intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[  287.028118] pcieport 0000:00:1c.0: System wakeup disabled by ACPI
[  287.028135] ehci-pci 0000:00:1d.0: setting latency timer to 64
[  287.031570] [drm] probing gen 2 caps for device 8086:151 = 261ac83/e
[  287.031572] [drm] enabling PCIE gen 3 link speeds, disable with radeon.pcie_gen2=0
[  287.227655] dpm_run_callback(): pnp_bus_resume+0x0/0x80 returns -19
[  287.227656] PM: Device 00:07 failed to resume: error -19
[  287.239713] usb 2-1.5: reset full-speed USB device number 3 using ehci-pci
[  287.347705] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[  287.402621] ata1.00: configured for UDMA/133
[  287.403880] usb 1-1.3: reset high-speed USB device number 3 using ehci-pci
[  287.415820] sd 0:0:0:0: [sda] Starting disk
[  287.568045] usb 1-1.5: reset high-speed USB device number 4 using ehci-pci
[  288.092796] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off
[  288.582283] [drm] PCIE GART of 512M enabled (table at 0x0000000000379000).
[  288.582384] radeon 0000:01:00.0: WB enabled
[  288.582386] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00 and cpu addr 0xffff88024cae0c00
[  288.582387] radeon 0000:01:00.0: fence driver on ring 1 use gpu addr 0x0000000080000c04 and cpu addr 0xffff88024cae0c04
[  288.582388] radeon 0000:01:00.0: fence driver on ring 2 use gpu addr 0x0000000080000c08 and cpu addr 0xffff88024cae0c08
[  288.582388] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c and cpu addr 0xffff88024cae0c0c
[  288.582389] radeon 0000:01:00.0: fence driver on ring 4 use gpu addr 0x0000000080000c10 and cpu addr 0xffff88024cae0c10
[  288.583164] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000075a18 and cpu addr 0xffffc90021db5a18
[  288.601827] [drm] ring test on 0 succeeded in 1 usecs
[  288.601831] [drm] ring test on 1 succeeded in 1 usecs
[  288.601834] [drm] ring test on 2 succeeded in 1 usecs
[  288.601892] [drm] ring test on 3 succeeded in 2 usecs
[  288.601898] [drm] ring test on 4 succeeded in 1 usecs
[  288.787669] [drm] ring test on 5 succeeded in 1 usecs
[  288.787671] [drm] UVD initialized successfully.
[  288.789108] [drm] ib test on ring 0 succeeded in 0 usecs
[  288.789127] [drm] ib test on ring 1 succeeded in 0 usecs
[  288.789145] [drm] ib test on ring 2 succeeded in 0 usecs
[  288.789165] [drm] ib test on ring 3 succeeded in 0 usecs
[  288.789185] [drm] ib test on ring 4 succeeded in 0 usecs
[  288.941441] [drm] ib test on ring 5 succeeded
[  288.951434] PM: resume of devices complete after 1921.707 msecs
[  288.951650] PM: Finishing wakeup.
[  288.951651] Restarting tasks ... done.
[  289.029626] video LNXVIDEO:00: Restoring backlight state
[  289.029630] video LNXVIDEO:02: Restoring backlight state
[  289.237503] radeon: switched off
[  289.752415] r8169 0000:07:00.0 eth0: link down
[  289.752503] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  289.754038] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[  289.761710] iwlwifi 0000:08:00.0: Radio type=0x2-0x0-0x0
[  289.833040] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  291.075891] wlan0: authenticate with 10:bf:48:3c:f4:a1
[  291.079406] wlan0: send auth to 10:bf:48:3c:f4:a1 (try 1/3)
[  291.081304] wlan0: authenticated
[  291.083603] wlan0: associate with 10:bf:48:3c:f4:a1 (try 1/3)
[  291.088040] wlan0: RX AssocResp from 10:bf:48:3c:f4:a1 (capab=0xc11 status=0 aid=2)
[  291.107466] wlan0: associated
[  291.107520] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  291.107684] cfg80211: Calling CRDA for country: US
[  291.111469] cfg80211: Regulatory domain changed to country: US
[  291.111474] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  291.111478] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  291.111480] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  291.111483] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  291.111485] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  291.111488] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  291.111490] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[  291.111493] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm)

```

---

### Post by AngelGenchev on 2013-11-24
Did you use switcheroo to turn off DGPU, prior to suspend/switch off graphic mode ?
If you did, then your problem is the same as mine, so my answer should shed some light:
Somebody had tinkered with the code so now you need to turn on the DGPU prior to suspend/switch off graphic mode to prevent lock-up in the ATI atombios. If you don't want to, you can just sit and wait about 1 .. 2 minutes and see if it will "fix" itself. For me it does so with the following output in dmesg:
```
[ 1087.139892] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 5secs aborting
[ 1087.139906] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CCFC (len 62, WS 0, PS 0) @ 0xCD18
.......
[ 1162.176051] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 5secs aborting
[ 1162.176063] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CCFC (len 62, WS 0, PS 0) @ 0xCD18
```
To turn discrete GPU on, but have video output from integrated card, I do as root:
```
echo ON > /sys/kernel/debug/vgaswitcheroo/switch
```

---

### Post by Donner87 on 2013-11-25
Thank you for the response AngelGenchev.  Well, this happened before I started mucking around with the DGPU.  Plus, I believe for the problem you describe the system will *always* lockup.  Mine only locks up randomly when the screen goes off/on.

But yeah, I do turn off the DGPU these days, and have a script that turns it back on and off at the appropriate times.

As an update to my original post, I re-installed the old 13.04 kernel (3.8) and tried that.  Under that kernel, it locked up when waking the screen up, as opposed to when the screen turns off.  I previously mentioned that this problem was not occurring back in 13.04.  So either my recollection is bad (possible), something else is different and causing the problem, or the script I have to turn the DGPU back off may be the culprit under 3.8 (thanks for reminding me about that script, AngelGenchev).  I'll try disabling the script and running 3.8 again.

---

### Post by Bucky Ball on 2013-11-25
Just a tip: Please stick to one support question a thread or it gets confusing. This will also increase your chances of getting help. (Multiple questions could be why you are not getting a lot of responses).

You should edit out the Cinnamon issue and post a new thread regarding that in Desktop Environments (it doesn't belong here). The other two could be related, though.

---

### Post by Donner87 on 2013-11-25
Thank you for the tip Bucky Ball.  I edited out the other two issues.  Couldn't find a way to update the thread title, though.

---

### Post by AngelGenchev on 2013-11-25
We need to narrow the problem - whether it's software or hardware and which subsystem is responsible. 
Yes, the problem I describe is always reproducible. And your system does lock-up randomly ?
Hard locks mean:
1) it's impossible to signal it to shut down when "locked-up" by pressing the power button for a short time.
2) it's not ping-able on the LAN in this state. 3) your caps-lock LED doesn't switch on/off when you press the key.
Does it lock-up with the both GPUs enabled ? Did you try installing the fglrx driver ? It can bring you another issues, but may fix these.
Does the memcheck86 pass the tests #6,#7,#8 without reporting a problem ?
If you run out of options, you may want to try if in the Porteus distro (unobtrusive, can be run off a removable HDD or usb key) your system locks up the same way....

---

### Post by Donner87 on 2013-11-25
> And your system does lock-up randomly ?
Yes.  To describe it precisely:  I walk away from the computer.  10 minutes later, the screen dims and powers down as it should.  I come back at some point.  Most of the time, the screen is off as it should be, and I wake it up by wiggling mouse/tapping key.  Some of the time, I come back and see that the screen is black but the backlight is on, and the machine is hard locked.  Sometimes it happens 2+ times a day.  Sometimes it'll go a day or two with no problem.

> 1) it's impossible to signal it to shut down when "locked-up" by pressing the power button for a short time.
2) it's not ping-able on the LAN in this state. 3) your caps-lock LED doesn't switch on/off when you press the key.
#1 & #2 are correct.  I haven't checked #3.  No ping.  No SSH.  No activity LEDs.  All I can do is hold the power button down for a few seconds to get it to power off.

> Does it lock-up with the both GPUs enabled ? Did you try installing the fglrx driver ? It can bring you another issues, but may fix these.
It can lock up with both on, and with only integrated on.  I never use the DGPU, only the integrated Intel GPU, so fglrx doesn't seem like it would help.

> Does the memcheck86 pass the tests #6,#7,#8 without reporting a problem ?
I will check and report back.  I didn't check before, because I recall a period of time where this wasn't occurring (12.10 - 13.04).  That would lead me to believe RAM isn't the issue, but rather a kernel issue.  But it's worth a check; thanks for reminding me.  (Currently retesting 3.8 kernel with DGPU scripts turned off)

---

### Post by AngelGenchev on 2013-11-26
I wrote about fglrx, because it does strange enough things to be mentioned, for example - switcheroo kernel interface disappears and the DGPU can be powered down with DRI enabled on iGPU while xorg.conf contains only fglrx driver (entries generated by aticonfig)... 
But sometimes (xubuntu 12.10, kernel 3.5.0-43) it brings worse problem with the iGPU - when on, it "soft" locks-up when xsession is terminated (log-off). For ubuntu 13.x it may behave different way...
 In the kernel 2.6.x days, there were modules that had to be blacklisted in order software suspend to work. This issue could be related.
What does the Dell`s support think about this (beside their congratulations on buying it) ?
Btw, here's another thread for this model: [http://ubuntuforums.org/showthread.php?t=2186540. ]("http://ubuntuforums.org/showthread.php?t=2186540")

---

### Post by Donner87 on 2013-12-11
After two weeks of running the older 3.8.0-33 kernel, I have not had a single hard lock.  One time X died, but that was easy to recover from and never has the kernel just up and died like under 3.11.0.

So this appears to be an issue with the 3.11.0 kernel.  I guess I should file a kernel bug report.  Not sure if it matters that these are Ubuntu specific kernels.  I'm not sure if my system depends on any of the Ubuntu specific kernel tweaks.

---

