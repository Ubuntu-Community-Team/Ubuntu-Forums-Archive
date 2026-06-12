---
title: "Ubuntu 14.04 Hard Kernel Lockup"
date: 2015-12-01
forum: General Help
---

### Post by John_Dempsey on 2015-12-01
Hello, this is my first forum post so I'll get straight to the point.  

I am running Ubuntu 14.04 on a [COLOR=#000000][FONT=arial]Sager NP8652 / Clevo P650SG with a Nvidia 980M graphics card.  Occassionally (about once a day) my screen will lock up and I can't move the mouse.  I try switching to a different TTY with ctrl+alt+F2, but that does not work.  Also, alt+PrtSc(SysRq)+REISUB does **not** work, leading me to believe this is a hard kernel lockup.  I have tried [/FONT][/COLOR][COLOR=#000000][FONT=arial]alt+PrtSc(SysRq)+REISUB before while my laptop was in a stable state and it did reboot, so I have the right key combination.  
[/FONT][/COLOR]
[SIZE=2]"uname -a" reveals:
[/SIZE]
> Linux consequence 3.16.0-55-generic #74~14.04.1-Ubuntu SMP Tue Nov 17 10:15:59 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


I had this problem before and I noticed that it would occur most often when I tried to access files on a second HDD that I had (formatted ntfs).  I had been automatically mounting the HDD with an /etc/fstab entry and when I removed the entry, it solved the problem.  Or so it seemed.  After a few weeks of being really stable, the kernel lockups are happening again, but I have not been accessing the HDD.  I am accessing and auto-mounting an SSD that I have, but I'm not sure if that's the real culprit anymore.  Here is my /etc/fstab:

```

jonah@consequence:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdd1 during installation
UUID=a8b4df8d-5fce-4c12-b5a6-0be2aa6b6637 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdc2 during installation
UUID=4E21-040F  /boot/efi       vfat    defaults        0       1
# /home was on /dev/sdd2 during installation
UUID=f1c3878f-5a71-4cd6-b16a-a2f93c3cd9c9 /home           ext4    defaults        0       2
# 1tb hdd storage
#UUID=DC9E23D79E23A94A    /media/jonah/tesla    ntfs    defaults    0    0
# 500 gb ssd misc
UUID=097C469769587A8A    /media/jonah/subterfuge    ntfs    defaults    0    0

```

How can I get more info about what caused this crash and/or file a bug report?

EDIT: I did check my ram with memtest and my ram passed all tests.

UPDATE: I have been trying to recreate the crash by mounting my HDD, booting back and forth between Ubuntu and Windows 10, etc. in order to post what "dmesg" would say, but I have not been able to recreate the crash, even when accessing my other HDDs/SSDs.  This leads me to believe that whatever is causing the freezing is more random than I initially thought.  The next time it crashes, I will post the output of "dmesg" as well as try to turn on the NumLock and CapsLock keys on and off (to see if the corresponding LEDs light up as they should).

UPDATE: I have experienced the crash again, and trying NumLock and CapsLock did **not **turn on/off the corresponding LEDs on my laptop.  After a reboot, I immediately saved the output of dmesg to a text file.  Here is the output:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.16.0-55-generic (buildd@lgw01-42) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #74~14.04.1-Ubuntu SMP Tue Nov 17 10:15:59 UTC 2015 (Ubuntu 3.16.0-55.74~14.04.1-generic 3.16.7-ckt19)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-55-generic.efi.signed root=UUID=a8b4df8d-5fce-4c12-b5a6-0be2aa6b6637 ro crashkernel=384M-:128M
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x0000000000057fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000058000-0x0000000000058fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000059000-0x000000000009dfff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009e000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000008efacfff] usable
[    0.000000] BIOS-e820: [mem 0x000000008efad000-0x000000008f2aafff] reserved
[    0.000000] BIOS-e820: [mem 0x000000008f2ab000-0x000000009222afff] usable
[    0.000000] BIOS-e820: [mem 0x000000009222b000-0x0000000092315fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000092316000-0x0000000092343fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x0000000092344000-0x0000000092cd2fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x0000000092cd3000-0x0000000092faefff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000092faf000-0x0000000092ffefff] type 20
[    0.000000] BIOS-e820: [mem 0x0000000092fff000-0x0000000092ffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000093800000-0x0000000097ffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x0000000466ffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] efi: EFI v2.40 by American Megatrends
[    0.000000] efi:  ACPI=0x9231f000  ACPI 2.0=0x9231f000  SMBIOS=0x92ef5f18 
[    0.000000] efi: mem00: type=7, attr=0xf, range=[0x0000000000000000-0x0000000000058000) (0MB)
[    0.000000] efi: mem01: type=0, attr=0xf, range=[0x0000000000058000-0x0000000000059000) (0MB)
[    0.000000] efi: mem02: type=7, attr=0xf, range=[0x0000000000059000-0x000000000009e000) (0MB)
[    0.000000] efi: mem03: type=0, attr=0xf, range=[0x000000000009e000-0x00000000000a0000) (0MB)
[    0.000000] efi: mem04: type=2, attr=0xf, range=[0x0000000000100000-0x00000000014e2000) (19MB)
[    0.000000] efi: mem05: type=7, attr=0xf, range=[0x00000000014e2000-0x0000000002000000) (11MB)
[    0.000000] efi: mem06: type=2, attr=0xf, range=[0x0000000002000000-0x00000000033e2000) (19MB)
[    0.000000] efi: mem07: type=7, attr=0xf, range=[0x00000000033e2000-0x0000000010000000) (204MB)
[    0.000000] efi: mem08: type=3, attr=0xf, range=[0x0000000010000000-0x000000001000b000) (0MB)
[    0.000000] efi: mem09: type=7, attr=0xf, range=[0x000000001000b000-0x0000000034a90000) (586MB)
[    0.000000] efi: mem10: type=2, attr=0xf, range=[0x0000000034a90000-0x0000000036540000) (26MB)
[    0.000000] efi: mem11: type=7, attr=0xf, range=[0x0000000036540000-0x0000000067a1d000) (788MB)
[    0.000000] efi: mem12: type=2, attr=0xf, range=[0x0000000067a1d000-0x000000008b2c1000) (568MB)
[    0.000000] efi: mem13: type=4, attr=0xf, range=[0x000000008b2c1000-0x000000008b301000) (0MB)
[    0.000000] efi: mem14: type=7, attr=0xf, range=[0x000000008b301000-0x000000008e128000) (46MB)
[    0.000000] efi: mem15: type=2, attr=0xf, range=[0x000000008e128000-0x000000008e2fc000) (1MB)
[    0.000000] efi: mem16: type=1, attr=0xf, range=[0x000000008e2fc000-0x000000008e422000) (1MB)
[    0.000000] efi: mem17: type=4, attr=0xf, range=[0x000000008e422000-0x000000008efad000) (11MB)
[    0.000000] efi: mem18: type=6, attr=0x800000000000000f, range=[0x000000008efad000-0x000000008f2ab000) (2MB)
[    0.000000] efi: mem19: type=4, attr=0xf, range=[0x000000008f2ab000-0x000000008f2b1000) (0MB)
[    0.000000] efi: mem20: type=7, attr=0xf, range=[0x000000008f2b1000-0x000000008f2be000) (0MB)
[    0.000000] efi: mem21: type=2, attr=0xf, range=[0x000000008f2be000-0x000000008f2c0000) (0MB)
[    0.000000] efi: mem22: type=4, attr=0xf, range=[0x000000008f2c0000-0x0000000091c2b000) (41MB)
[    0.000000] efi: mem23: type=7, attr=0xf, range=[0x0000000091c2b000-0x0000000091ece000) (2MB)
[    0.000000] efi: mem24: type=2, attr=0xf, range=[0x0000000091ece000-0x0000000091ed8000) (0MB)
[    0.000000] efi: mem25: type=3, attr=0xf, range=[0x0000000091ed8000-0x000000009222b000) (3MB)
[    0.000000] efi: mem26: type=0, attr=0xf, range=[0x000000009222b000-0x0000000092316000) (0MB)
[    0.000000] efi: mem27: type=9, attr=0xf, range=[0x0000000092316000-0x0000000092344000) (0MB)
[    0.000000] efi: mem28: type=10, attr=0xf, range=[0x0000000092344000-0x0000000092cd3000) (9MB)
[    0.000000] efi: mem29: type=6, attr=0x800000000000000f, range=[0x0000000092cd3000-0x0000000092faf000) (2MB)
[    0.000000] efi: mem30: type=5, attr=0x800000000000000f, range=[0x0000000092faf000-0x0000000092fff000) (0MB)
[    0.000000] efi: mem31: type=4, attr=0xf, range=[0x0000000092fff000-0x0000000093000000) (0MB)
[    0.000000] efi: mem32: type=7, attr=0xf, range=[0x0000000100000000-0x0000000467000000) (13936MB)
[    0.000000] efi: mem33: type=0, attr=0x0, range=[0x0000000093800000-0x0000000098000000) (72MB)
[    0.000000] efi: mem34: type=11, attr=0x8000000000000001, range=[0x00000000f8000000-0x00000000fc000000) (64MB)
[    0.000000] efi: mem35: type=11, attr=0x8000000000000001, range=[0x00000000fec00000-0x00000000fec01000) (0MB)
[    0.000000] efi: mem36: type=11, attr=0x8000000000000001, range=[0x00000000fed00000-0x00000000fed04000) (0MB)
[    0.000000] efi: mem37: type=11, attr=0x8000000000000001, range=[0x00000000fed1c000-0x00000000fed20000) (0MB)
[    0.000000] efi: mem38: type=11, attr=0x8000000000000001, range=[0x00000000fee00000-0x00000000fee01000) (0MB)
[    0.000000] efi: mem39: type=11, attr=0x8000000000000001, range=[0x00000000ff000000-0x0000000100000000) (16MB)
[    0.000000] SMBIOS 2.8 present.
[    0.000000] DMI: Notebook                         P65xSG-A/P65xSG-A, BIOS 5.011 09/10/2015
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] AGP: No AGP bridge found
[    0.000000] e820: last_pfn = 0x467000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask 7F80000000 write-back
[    0.000000]   1 base 0080000000 mask 7FF0000000 write-back
[    0.000000]   2 base 0090000000 mask 7FFE000000 write-back
[    0.000000]   3 base 0092000000 mask 7FFF000000 write-back
[    0.000000]   4 base 0100000000 mask 7F00000000 write-back
[    0.000000]   5 base 0200000000 mask 7E00000000 write-back
[    0.000000]   6 base 0400000000 mask 7F80000000 write-back
[    0.000000]   7 base 0470000000 mask 7FF0000000 uncachable
[    0.000000]   8 base 0468000000 mask 7FF8000000 uncachable
[    0.000000]   9 base 0467000000 mask 7FFF000000 uncachable
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 256MB, type WB
[    0.000000] reg 2, base: 2304MB, range: 32MB, type WB
[    0.000000] reg 3, base: 2336MB, range: 16MB, type WB
[    0.000000] reg 4, base: 4GB, range: 4GB, type WB
[    0.000000] reg 5, base: 8GB, range: 8GB, type WB
[    0.000000] reg 6, base: 16GB, range: 2GB, type WB
[    0.000000] reg 7, base: 18176MB, range: 256MB, type UC
[    0.000000] reg 8, base: 18048MB, range: 128MB, type UC
[    0.000000] reg 9, base: 18032MB, range: 16MB, type UC
[    0.000000] total RAM covered: 16288M
[    0.000000]  gran_size: 64K     chunk_size: 64K     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 64K     chunk_size: 128K     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 64K     chunk_size: 256K     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 64K     chunk_size: 512K     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 64K     chunk_size: 1M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 64K     chunk_size: 2M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 64K     chunk_size: 4M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 64K     chunk_size: 8M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 64K     chunk_size: 16M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 64K     chunk_size: 32M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 64K     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 64K     chunk_size: 128M     num_reg: 10      lose cover RAM: -16M
[    0.000000] *BAD*gran_size: 64K     chunk_size: 256M     num_reg: 10      lose cover RAM: -144M
[    0.000000] *BAD*gran_size: 64K     chunk_size: 512M     num_reg: 10      lose cover RAM: -256M
[    0.000000] *BAD*gran_size: 64K     chunk_size: 1G     num_reg: 10      lose cover RAM: -384M
[    0.000000] *BAD*gran_size: 64K     chunk_size: 2G     num_reg: 10      lose cover RAM: -384M
[    0.000000]  gran_size: 128K     chunk_size: 128K     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 128K     chunk_size: 256K     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 128K     chunk_size: 512K     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 128K     chunk_size: 1M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 128K     chunk_size: 2M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 128K     chunk_size: 4M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 128K     chunk_size: 8M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 128K     chunk_size: 16M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 128K     chunk_size: 32M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 128K     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 128K     chunk_size: 128M     num_reg: 10      lose cover RAM: -16M
[    0.000000] *BAD*gran_size: 128K     chunk_size: 256M     num_reg: 10      lose cover RAM: -144M
[    0.000000] *BAD*gran_size: 128K     chunk_size: 512M     num_reg: 10      lose cover RAM: -256M
[    0.000000] *BAD*gran_size: 128K     chunk_size: 1G     num_reg: 10      lose cover RAM: -384M
[    0.000000] *BAD*gran_size: 128K     chunk_size: 2G     num_reg: 10      lose cover RAM: -384M
[    0.000000]  gran_size: 256K     chunk_size: 256K     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 256K     chunk_size: 512K     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 256K     chunk_size: 1M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 256K     chunk_size: 2M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 256K     chunk_size: 4M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 256K     chunk_size: 8M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 256K     chunk_size: 16M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 256K     chunk_size: 32M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 256K     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 256K     chunk_size: 128M     num_reg: 10      lose cover RAM: -16M
[    0.000000] *BAD*gran_size: 256K     chunk_size: 256M     num_reg: 10      lose cover RAM: -144M
[    0.000000] *BAD*gran_size: 256K     chunk_size: 512M     num_reg: 10      lose cover RAM: -256M
[    0.000000] *BAD*gran_size: 256K     chunk_size: 1G     num_reg: 10      lose cover RAM: -384M
[    0.000000] *BAD*gran_size: 256K     chunk_size: 2G     num_reg: 10      lose cover RAM: -384M
[    0.000000]  gran_size: 512K     chunk_size: 512K     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 512K     chunk_size: 1M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 512K     chunk_size: 2M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 512K     chunk_size: 4M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 512K     chunk_size: 8M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 512K     chunk_size: 16M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 512K     chunk_size: 32M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 512K     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 512K     chunk_size: 128M     num_reg: 10      lose cover RAM: -16M
[    0.000000] *BAD*gran_size: 512K     chunk_size: 256M     num_reg: 10      lose cover RAM: -144M
[    0.000000] *BAD*gran_size: 512K     chunk_size: 512M     num_reg: 10      lose cover RAM: -256M
[    0.000000] *BAD*gran_size: 512K     chunk_size: 1G     num_reg: 10      lose cover RAM: -384M
[    0.000000] *BAD*gran_size: 512K     chunk_size: 2G     num_reg: 10      lose cover RAM: -384M
[    0.000000]  gran_size: 1M     chunk_size: 1M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 1M     chunk_size: 2M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 1M     chunk_size: 4M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 1M     chunk_size: 8M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 1M     chunk_size: 16M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 1M     chunk_size: 32M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 1M     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 1M     chunk_size: 128M     num_reg: 10      lose cover RAM: -16M
[    0.000000] *BAD*gran_size: 1M     chunk_size: 256M     num_reg: 10      lose cover RAM: -144M
[    0.000000] *BAD*gran_size: 1M     chunk_size: 512M     num_reg: 10      lose cover RAM: -256M
[    0.000000] *BAD*gran_size: 1M     chunk_size: 1G     num_reg: 10      lose cover RAM: -384M
[    0.000000] *BAD*gran_size: 1M     chunk_size: 2G     num_reg: 10      lose cover RAM: -384M
[    0.000000]  gran_size: 2M     chunk_size: 2M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 2M     chunk_size: 4M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 2M     chunk_size: 8M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 2M     chunk_size: 16M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 2M     chunk_size: 32M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 2M     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 2M     chunk_size: 128M     num_reg: 10      lose cover RAM: -16M
[    0.000000] *BAD*gran_size: 2M     chunk_size: 256M     num_reg: 10      lose cover RAM: -144M
[    0.000000] *BAD*gran_size: 2M     chunk_size: 512M     num_reg: 10      lose cover RAM: -256M
[    0.000000] *BAD*gran_size: 2M     chunk_size: 1G     num_reg: 10      lose cover RAM: -384M
[    0.000000] *BAD*gran_size: 2M     chunk_size: 2G     num_reg: 10      lose cover RAM: -384M
[    0.000000]  gran_size: 4M     chunk_size: 4M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 4M     chunk_size: 8M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 4M     chunk_size: 16M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 4M     chunk_size: 32M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 4M     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 4M     chunk_size: 128M     num_reg: 10      lose cover RAM: -16M
[    0.000000] *BAD*gran_size: 4M     chunk_size: 256M     num_reg: 10      lose cover RAM: -144M
[    0.000000] *BAD*gran_size: 4M     chunk_size: 512M     num_reg: 10      lose cover RAM: -256M
[    0.000000] *BAD*gran_size: 4M     chunk_size: 1G     num_reg: 10      lose cover RAM: -384M
[    0.000000] *BAD*gran_size: 4M     chunk_size: 2G     num_reg: 10      lose cover RAM: -384M
[    0.000000]  gran_size: 8M     chunk_size: 8M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 8M     chunk_size: 16M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 8M     chunk_size: 32M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 8M     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 8M     chunk_size: 128M     num_reg: 10      lose cover RAM: -16M
[    0.000000] *BAD*gran_size: 8M     chunk_size: 256M     num_reg: 10      lose cover RAM: -144M
[    0.000000] *BAD*gran_size: 8M     chunk_size: 512M     num_reg: 10      lose cover RAM: -256M
[    0.000000] *BAD*gran_size: 8M     chunk_size: 1G     num_reg: 10      lose cover RAM: -384M
[    0.000000] *BAD*gran_size: 8M     chunk_size: 2G     num_reg: 10      lose cover RAM: -384M
[    0.000000]  gran_size: 16M     chunk_size: 16M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 16M     chunk_size: 32M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 16M     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 16M     chunk_size: 128M     num_reg: 10      lose cover RAM: -16M
[    0.000000] *BAD*gran_size: 16M     chunk_size: 256M     num_reg: 10      lose cover RAM: -144M
[    0.000000] *BAD*gran_size: 16M     chunk_size: 512M     num_reg: 10      lose cover RAM: -256M
[    0.000000] *BAD*gran_size: 16M     chunk_size: 1G     num_reg: 10      lose cover RAM: -384M
[    0.000000] *BAD*gran_size: 16M     chunk_size: 2G     num_reg: 10      lose cover RAM: -384M
[    0.000000]  gran_size: 32M     chunk_size: 32M     num_reg: 9      lose cover RAM: 32M
[    0.000000]  gran_size: 32M     chunk_size: 64M     num_reg: 10      lose cover RAM: 32M
[    0.000000] *BAD*gran_size: 32M     chunk_size: 128M     num_reg: 10      lose cover RAM: -0G
[    0.000000] *BAD*gran_size: 32M     chunk_size: 256M     num_reg: 10      lose cover RAM: -128M
[    0.000000] *BAD*gran_size: 32M     chunk_size: 512M     num_reg: 10      lose cover RAM: -224M
[    0.000000] *BAD*gran_size: 32M     chunk_size: 1G     num_reg: 10      lose cover RAM: -352M
[    0.000000] *BAD*gran_size: 32M     chunk_size: 2G     num_reg: 10      lose cover RAM: -352M
[    0.000000]  gran_size: 64M     chunk_size: 64M     num_reg: 7      lose cover RAM: 96M
[    0.000000]  gran_size: 64M     chunk_size: 128M     num_reg: 8      lose cover RAM: 96M
[    0.000000]  gran_size: 64M     chunk_size: 256M     num_reg: 9      lose cover RAM: 96M
[    0.000000]  gran_size: 64M     chunk_size: 512M     num_reg: 9      lose cover RAM: 96M
[    0.000000]  gran_size: 64M     chunk_size: 1G     num_reg: 10      lose cover RAM: 96M
[    0.000000]  gran_size: 64M     chunk_size: 2G     num_reg: 10      lose cover RAM: 96M
[    0.000000]  gran_size: 128M     chunk_size: 128M     num_reg: 6      lose cover RAM: 160M
[    0.000000]  gran_size: 128M     chunk_size: 256M     num_reg: 6      lose cover RAM: 160M
[    0.000000]  gran_size: 128M     chunk_size: 512M     num_reg: 7      lose cover RAM: 160M
[    0.000000]  gran_size: 128M     chunk_size: 1G     num_reg: 8      lose cover RAM: 160M
[    0.000000]  gran_size: 128M     chunk_size: 2G     num_reg: 8      lose cover RAM: 160M
[    0.000000]  gran_size: 256M     chunk_size: 256M     num_reg: 6      lose cover RAM: 160M
[    0.000000]  gran_size: 256M     chunk_size: 512M     num_reg: 7      lose cover RAM: 160M
[    0.000000]  gran_size: 256M     chunk_size: 1G     num_reg: 8      lose cover RAM: 160M
[    0.000000]  gran_size: 256M     chunk_size: 2G     num_reg: 8      lose cover RAM: 160M
[    0.000000]  gran_size: 512M     chunk_size: 512M     num_reg: 5      lose cover RAM: 416M
[    0.000000]  gran_size: 512M     chunk_size: 1G     num_reg: 5      lose cover RAM: 416M
[    0.000000]  gran_size: 512M     chunk_size: 2G     num_reg: 5      lose cover RAM: 416M
[    0.000000]  gran_size: 1G     chunk_size: 1G     num_reg: 4      lose cover RAM: 928M
[    0.000000]  gran_size: 1G     chunk_size: 2G     num_reg: 5      lose cover RAM: 928M
[    0.000000]  gran_size: 2G     chunk_size: 2G     num_reg: 3      lose cover RAM: 1952M
[    0.000000] mtrr_cleanup: can not find optimal value
[    0.000000] please specify mtrr_gran_size/mtrr_chunk_size
[    0.000000] e820: update [mem 0x93000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0x93000 max_arch_pfn = 0x400000000
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x02fbe000, 0x02fbefff] PGTABLE
[    0.000000] BRK [0x02fbf000, 0x02fbffff] PGTABLE
[    0.000000] BRK [0x02fc0000, 0x02fc0fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x466e00000-0x466ffffff]
[    0.000000]  [mem 0x466e00000-0x466ffffff] page 2M
[    0.000000] BRK [0x02fc1000, 0x02fc1fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x464000000-0x466dfffff]
[    0.000000]  [mem 0x464000000-0x466dfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x400000000-0x463ffffff]
[    0.000000]  [mem 0x400000000-0x43fffffff] page 1G
[    0.000000]  [mem 0x440000000-0x463ffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x8efacfff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0x7fffffff] page 1G
[    0.000000]  [mem 0x80000000-0x8edfffff] page 2M
[    0.000000]  [mem 0x8ee00000-0x8efacfff] page 4k
[    0.000000] init_memory_mapping: [mem 0x8f2ab000-0x9222afff]
[    0.000000]  [mem 0x8f2ab000-0x8f3fffff] page 4k
[    0.000000]  [mem 0x8f400000-0x921fffff] page 2M
[    0.000000]  [mem 0x92200000-0x9222afff] page 4k
[    0.000000] BRK [0x02fc2000, 0x02fc2fff] PGTABLE
[    0.000000] BRK [0x02fc3000, 0x02fc3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x92fff000-0x92ffffff]
[    0.000000]  [mem 0x92fff000-0x92ffffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x3ffffffff]
[    0.000000]  [mem 0x100000000-0x3ffffffff] page 1G
[    0.000000] RAMDISK: [mem 0x34a90000-0x3653ffff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x000000009231F000 000024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 0x000000009231F0A0 0000C4 (v01 MIDERN MIDERN   01072009 AMI  00010013)
[    0.000000] ACPI: FACP 0x0000000092338CF8 00010C (v05 MIDERN MIDERN   01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 0x000000009231F1F8 019AFF (v02 MIDERN MIDERN   01072009 INTL 20120913)
[    0.000000] ACPI: FACS 0x0000000092CD1F80 000040
[    0.000000] ACPI: APIC 0x0000000092338E08 0000BC (v03 MIDERN MIDERN   01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 0x0000000092338EC8 000044 (v01 MIDERN MIDERN   01072009 AMI  00010013)
[    0.000000] ACPI: FIDT 0x0000000092338F10 00009C (v01 MIDERN MIDERN   01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 0x0000000092338FB0 00003C (v01 MIDERN MIDERN   01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 0x0000000092338FF0 000038 (v01 MIDERN MIDERN   01072009 AMI. 0005000B)
[    0.000000] ACPI: SSDT 0x0000000092339028 000315 (v01 MIDERN MIDERN   00001000 INTL 20120913)
[    0.000000] ACPI: UEFI 0x0000000092339340 000042 (v01 MIDERN MIDERN   00000000      00000000)
[    0.000000] ACPI: LPIT 0x0000000092339388 000094 (v01 MIDERN MIDERN   00000000      00000000)
[    0.000000] ACPI: SSDT 0x0000000092339420 000C7D (v02 MIDERN MIDERN   00001000 INTL 20120913)
[    0.000000] ACPI: SSDT 0x000000009233A0A0 000FD1 (v02 MIDERN MIDERN   00001000 INTL 20120913)
[    0.000000] ACPI: ASF! 0x000000009233B078 0000A0 (v32 MIDERN MIDERN   00000001 TFSM 000F4240)
[    0.000000] ACPI: MSDM 0x000000009233B118 000055 (v03 MIDERN MIDERN   01072009 AMI  00010013)
[    0.000000] ACPI: SSDT 0x000000009233B170 000539 (v02 MIDERN MIDERN   00003000 INTL 20120913)
[    0.000000] ACPI: SSDT 0x000000009233B6B0 000B74 (v02 MIDERN MIDERN   00003000 INTL 20120913)
[    0.000000] ACPI: SSDT 0x000000009233C228 005E39 (v02 MIDERN MIDERN   00003000 INTL 20120913)
[    0.000000] ACPI: SSDT 0x0000000092342068 000297 (v02 MIDERN MIDERN   00001000 INTL 20120913)
[    0.000000] ACPI: DMAR 0x0000000092342300 0000B8 (v01 MIDERN MIDERN   00000001 INTL 00000001)
[    0.000000] ACPI: SSDT 0x00000000923423B8 000E6D (v01 MIDERN MIDERN   00001000 INTL 20120913)
[    0.000000] ACPI: BGRT 0x0000000092343228 000038 (v00 MIDERN MIDERN   01072009 AMI  00010013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x0000000466ffffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x466ffffff]
[    0.000000]   NODE_DATA [mem 0x466ff8000-0x466ffcfff]
[    0.000000] Reserving 128MB of memory at 704MB for crashkernel (System RAM: 16270MB)
[    0.000000]  [ffffea0000000000-ffffea00119fffff] PMD -> [ffff880456600000-ffff8804665fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x466ffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x00057fff]
[    0.000000]   node   0: [mem 0x00059000-0x0009dfff]
[    0.000000]   node   0: [mem 0x00100000-0x8efacfff]
[    0.000000]   node   0: [mem 0x8f2ab000-0x9222afff]
[    0.000000]   node   0: [mem 0x92fff000-0x92ffffff]
[    0.000000]   node   0: [mem 0x100000000-0x466ffffff]
[    0.000000] On node 0 totalpages: 4165322
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 22 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 9277 pages used for memmap
[    0.000000]   DMA32 zone: 593710 pages, LIFO batch:31
[    0.000000]   Normal zone: 55744 pages used for memmap
[    0.000000]   Normal zone: 3567616 pages, LIFO batch:31
[    0.000000] Reserving Intel graphics stolen memory at 0x94000000-0x97ffffff
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high res lint[0x7e])
[    0.000000] ACPI: NMI not connected to LINT 1!
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] res dfl lint[0x6c])
[    0.000000] ACPI: NMI not connected to LINT 1!
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] res res lint[0x8])
[    0.000000] ACPI: NMI not connected to LINT 1!
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x57])
[    0.000000] ACPI: NMI not connected to LINT 1!
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] high level lint[0xda])
[    0.000000] ACPI: NMI not connected to LINT 1!
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] dfl res lint[0x2a])
[    0.000000] ACPI: NMI not connected to LINT 1!
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] high dfl lint[0x3c])
[    0.000000] ACPI: NMI not connected to LINT 1!
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x08] high res lint[0x2d])
[    0.000000] ACPI: NMI not connected to LINT 1!
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
[    0.000000] PM: Registered nosave memory: [mem 0x00058000-0x00058fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x8efad000-0x8f2aafff]
[    0.000000] PM: Registered nosave memory: [mem 0x9222b000-0x92315fff]
[    0.000000] PM: Registered nosave memory: [mem 0x92316000-0x92343fff]
[    0.000000] PM: Registered nosave memory: [mem 0x92344000-0x92cd2fff]
[    0.000000] PM: Registered nosave memory: [mem 0x92cd3000-0x92faefff]
[    0.000000] PM: Registered nosave memory: [mem 0x92faf000-0x92ffefff]
[    0.000000] PM: Registered nosave memory: [mem 0x93000000-0x937fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x93800000-0x97ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0x98000000-0xf7ffffff]
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
[    0.000000] e820: [mem 0x98000000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff880466c00000 s81408 r8192 d20992 u262144
[    0.000000] pcpu-alloc: s81408 r8192 d20992 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 4100215
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-55-generic.efi.signed root=UUID=a8b4df8d-5fce-4c12-b5a6-0be2aa6b6637 ro crashkernel=384M-:128M
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] AGP: Checking aperture...
[    0.000000] AGP: No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 16099344K/16661288K available (7635K kernel code, 1131K rwdata, 3616K rodata, 1356K init, 1300K bss, 561944K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-7.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=8
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 67108864 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 2693.827 MHz processor
[    0.000022] Calibrating delay loop (skipped), value calculated using timer frequency.. 5387.65 BogoMIPS (lpj=10775308)
[    0.000025] pid_max: default: 32768 minimum: 301
[    0.000031] ACPI: Core revision 20140424
[    0.013362] ACPI: All ACPI Tables successfully acquired
[    0.013944] Security Framework initialized
[    0.013955] AppArmor: AppArmor initialized
[    0.013957] Yama: becoming mindful.
[    0.014628] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.016807] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.017755] Mount-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.017768] Mountpoint-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.017954] Initializing cgroup subsys memory
[    0.017969] Initializing cgroup subsys devices
[    0.017974] Initializing cgroup subsys freezer
[    0.017976] Initializing cgroup subsys net_cls
[    0.017979] Initializing cgroup subsys blkio
[    0.017982] Initializing cgroup subsys perf_event
[    0.017984] Initializing cgroup subsys net_prio
[    0.017988] Initializing cgroup subsys hugetlb
[    0.018005] CPU: Physical Processor ID: 0
[    0.018007] CPU: Processor Core ID: 0
[    0.018010] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.018010] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.018811] mce: CPU supports 9 MCE banks
[    0.018822] CPU0: Thermal monitoring enabled (TM1)
[    0.018830] process: using mwait in idle threads
[    0.018832] Last level iTLB entries: 4KB 64, 2MB 8, 4MB 8
[    0.018832] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0, 1GB 4
[    0.018832] tlb_flushall_shift: 6
[    0.019103] Freeing SMP alternatives memory: 32K (ffffffff81e6f000 - ffffffff81e77000)
[    0.022268] ftrace: allocating 29286 entries in 115 pages
[    0.030780] dmar: Host address width 39
[    0.030782] dmar: DRHD base: 0x000000fed90000 flags: 0x0
[    0.030788] dmar: IOMMU 0: reg_base_addr fed90000 ver 1:0 cap 1c0000c40660462 ecap 7e1ff0505e
[    0.030790] dmar: DRHD base: 0x000000fed91000 flags: 0x1
[    0.030794] dmar: IOMMU 1: reg_base_addr fed91000 ver 1:0 cap d2008c20660462 ecap f010da
[    0.030795] dmar: RMRR base: 0x00000092f05000 end: 0x00000092f14fff
[    0.030797] dmar: RMRR base: 0x00000093800000 end: 0x00000097ffffff
[    0.030863] IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
[    0.030865] HPET id 0 under DRHD base 0xfed91000
[    0.030866] Queued invalidation will be enabled to support x2apic and Intr-remapping.
[    0.030867] Your BIOS is broken and requested that x2apic be disabled.
[    0.030867] This will slightly decrease performance.
[    0.030867] Use 'intremap=no_x2apic_optout' to override BIOS request.
[    0.031028] Enabled IRQ remapping in xapic mode
[    0.031030] x2apic not enabled, IRQ remapping is in xapic mode
[    0.031440] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.071110] smpboot: CPU0: Intel(R) Core(TM) i7-5700HQ CPU @ 2.70GHz (fam: 06, model: 47, stepping: 01)
[    0.071116] TSC deadline timer enabled
[    0.071131] Performance Events: PEBS fmt2+, 16-deep LBR, Haswell events, full-width counters, Intel PMU driver.
[    0.071146] ... version:                3
[    0.071147] ... bit width:              48
[    0.071148] ... generic registers:      4
[    0.071149] ... value mask:             0000ffffffffffff
[    0.071150] ... max period:             0000ffffffffffff
[    0.071151] ... fixed-purpose events:   3
[    0.071152] ... event mask:             000000070000000f
[    0.072350] x86: Booting SMP configuration:
[    0.072352] .... node  #0, CPUs:      #1
[    0.086325] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.086375]  #2 #3 #4 #5 #6 #7
[    0.170166] x86: Booted up 1 node, 8 CPUs
[    0.170170] smpboot: Total of 8 processors activated (43101.23 BogoMIPS)
[    0.175840] devtmpfs: initialized
[    0.177657] evm: security.selinux
[    0.177658] evm: security.SMACK64
[    0.177659] evm: security.SMACK64EXEC
[    0.177660] evm: security.SMACK64TRANSMUTE
[    0.177661] evm: security.SMACK64MMAP
[    0.177662] evm: security.ima
[    0.177663] evm: security.capability
[    0.177691] PM: Registering ACPI NVS region [mem 0x92344000-0x92cd2fff] (10022912 bytes)
[    0.178268] pinctrl core: initialized pinctrl subsystem
[    0.178312] regulator-dummy: no parameters
[    0.178340] RTC time:  9:52:07, date: 12/02/15
[    0.178371] NET: Registered protocol family 16
[    0.178464] cpuidle: using governor ladder
[    0.178466] cpuidle: using governor menu
[    0.178496] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.178498] ACPI: bus type PCI registered
[    0.178499] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.178545] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.178547] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.178597] PCI: Using configuration type 1 for base access
[    0.179927] ACPI: Added _OSI(Module Device)
[    0.179929] ACPI: Added _OSI(Processor Device)
[    0.179930] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.179931] ACPI: Added _OSI(Processor Aggregator Device)
[    0.183669] ACPI: Executed 17 blocks of module-level executable AML code
[    0.211766] ACPI: Dynamic OEM Table Load:
[    0.211773] ACPI: SSDT 0xFFFF880450261400 0003D3 (v02 PmRef  Cpu0Cst  00003001 INTL 20120913)
[    0.215863] ACPI: Dynamic OEM Table Load:
[    0.215868] ACPI: SSDT 0xFFFF88044FE68000 0005AA (v02 PmRef  ApIst    00003000 INTL 20120913)
[    0.219757] ACPI: Dynamic OEM Table Load:
[    0.219761] ACPI: SSDT 0xFFFF88044FE40C00 000119 (v02 PmRef  ApCst    00003000 INTL 20120913)
[    0.229199] ACPI: Interpreter enabled
[    0.229205] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20140424/hwxface-580)
[    0.229211] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20140424/hwxface-580)
[    0.229221] ACPI: (supports S0 S3 S4 S5)
[    0.229222] ACPI: Using IOAPIC for interrupt routing
[    0.229242] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.230284] ACPI: Power Resource [PG00] (on)
[    0.748709] ACPI: Power Resource [PG01] (on)
[    1.268802] ACPI: Power Resource [PG02] (on)
[    1.789168] ACPI: Power Resource [WRST] (off)
[    1.789351] ACPI: Power Resource [WRST] (off)
[    1.789532] ACPI: Power Resource [WRST] (off)
[    1.789733] ACPI: Power Resource [WRST] (off)
[    1.789927] ACPI: Power Resource [WRST] (off)
[    1.790180] ACPI: Power Resource [WRST] (off)
[    1.790352] ACPI: Power Resource [WRST] (off)
[    1.790525] ACPI: Power Resource [WRST] (off)
[    1.794976] ACPI: Power Resource [FN00] (off)
[    1.795019] ACPI: Power Resource [FN01] (off)
[    1.795060] ACPI: Power Resource [FN02] (off)
[    1.795102] ACPI: Power Resource [FN03] (off)
[    1.795144] ACPI: Power Resource [FN04] (off)
[    1.795649] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    1.795654] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    1.796075] acpi PNP0A08:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability]
[    1.796077] acpi PNP0A08:00: FADT indicates ASPM is unsupported, using BIOS configuration
[    1.796388] PCI host bridge to bus 0000:00
[    1.796390] pci_bus 0000:00: root bus resource [bus 00-3e]
[    1.796391] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    1.796393] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    1.796394] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    1.796396] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff]
[    1.796397] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff]
[    1.796398] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff]
[    1.796400] pci_bus 0000:00: root bus resource [mem 0x000cc000-0x000cffff]
[    1.796401] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    1.796402] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    1.796404] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    1.796405] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    1.796407] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    1.796408] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    1.796409] pci_bus 0000:00: root bus resource [mem 0x000e8000-0x000ebfff]
[    1.796411] pci_bus 0000:00: root bus resource [mem 0x000ec000-0x000effff]
[    1.796412] pci_bus 0000:00: root bus resource [mem 0x98000000-0xdfffffff]
[    1.796413] pci_bus 0000:00: root bus resource [mem 0xfe101000-0xfe113fff]
[    1.796419] pci 0000:00:00.0: [8086:1614] type 00 class 0x060000
[    1.796478] pci 0000:00:01.0: [8086:1601] type 01 class 0x060400
[    1.796505] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    1.796537] pci 0000:00:01.0: System wakeup disabled by ACPI
[    1.796564] pci 0000:00:02.0: [8086:1612] type 00 class 0x030000
[    1.796571] pci 0000:00:02.0: reg 0x10: [mem 0x99000000-0x99ffffff 64bit]
[    1.796576] pci 0000:00:02.0: reg 0x18: [mem 0xa0000000-0xafffffff 64bit pref]
[    1.796579] pci 0000:00:02.0: reg 0x20: [io  0x5000-0x503f]
[    1.796632] pci 0000:00:03.0: [8086:160c] type 00 class 0x040300
[    1.796637] pci 0000:00:03.0: reg 0x10: [mem 0x9b314000-0x9b317fff 64bit]
[    1.796711] pci 0000:00:14.0: [8086:8c31] type 00 class 0x0c0330
[    1.796729] pci 0000:00:14.0: reg 0x10: [mem 0x9b300000-0x9b30ffff 64bit]
[    1.796785] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    1.796821] pci 0000:00:14.0: System wakeup disabled by ACPI
[    1.796846] pci 0000:00:16.0: [8086:8c3a] type 00 class 0x078000
[    1.796863] pci 0000:00:16.0: reg 0x10: [mem 0x9b31d000-0x9b31d00f 64bit]
[    1.796920] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    1.796979] pci 0000:00:1a.0: [8086:8c2d] type 00 class 0x0c0320
[    1.796997] pci 0000:00:1a.0: reg 0x10: [mem 0x9b31b000-0x9b31b3ff]
[    1.797076] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    1.797112] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    1.797141] pci 0000:00:1b.0: [8086:8c20] type 00 class 0x040300
[    1.797153] pci 0000:00:1b.0: reg 0x10: [mem 0x9b310000-0x9b313fff 64bit]
[    1.797207] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.797242] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    1.797268] pci 0000:00:1c.0: [8086:8c10] type 01 class 0x060400
[    1.797335] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.797367] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    1.797393] pci 0000:00:1c.4: [8086:8c18] type 01 class 0x060400
[    1.797454] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    1.797485] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    1.797508] pci 0000:00:1c.5: [8086:8c1a] type 01 class 0x060400
[    1.797571] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    1.797602] pci 0000:00:1c.5: System wakeup disabled by ACPI
[    1.797631] pci 0000:00:1d.0: [8086:8c26] type 00 class 0x0c0320
[    1.797650] pci 0000:00:1d.0: reg 0x10: [mem 0x9b31a000-0x9b31a3ff]
[    1.797730] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    1.797766] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    1.797792] pci 0000:00:1f.0: [8086:8c4b] type 00 class 0x060100
[    1.797932] pci 0000:00:1f.2: [8086:8c03] type 00 class 0x010601
[    1.797945] pci 0000:00:1f.2: reg 0x10: [io  0x50b0-0x50b7]
[    1.797951] pci 0000:00:1f.2: reg 0x14: [io  0x50a0-0x50a3]
[    1.797959] pci 0000:00:1f.2: reg 0x18: [io  0x5090-0x5097]
[    1.797965] pci 0000:00:1f.2: reg 0x1c: [io  0x5080-0x5083]
[    1.797971] pci 0000:00:1f.2: reg 0x20: [io  0x5060-0x507f]
[    1.797978] pci 0000:00:1f.2: reg 0x24: [mem 0x9b319000-0x9b3197ff]
[    1.798011] pci 0000:00:1f.2: PME# supported from D3hot
[    1.798058] pci 0000:00:1f.3: [8086:8c22] type 00 class 0x0c0500
[    1.798070] pci 0000:00:1f.3: reg 0x10: [mem 0x9b318000-0x9b3180ff 64bit]
[    1.798087] pci 0000:00:1f.3: reg 0x20: [io  0x5040-0x505f]
[    1.798180] pci 0000:01:00.0: [10de:13d7] type 00 class 0x030200
[    1.798194] pci 0000:01:00.0: reg 0x10: [mem 0x00000000-0x00ffffff]
[    1.798207] pci 0000:01:00.0: reg 0x14: [mem 0x00000000-0x0fffffff 64bit pref]
[    1.798221] pci 0000:01:00.0: reg 0x1c: [mem 0x00000000-0x01ffffff 64bit pref]
[    1.798229] pci 0000:01:00.0: reg 0x24: [io  0x0000-0x007f]
[    1.798236] pci 0000:01:00.0: reg 0x30: [mem 0x00000000-0x0007ffff pref]
[    1.798317] pci 0000:01:00.0: System wakeup disabled by ACPI
[    1.804759] pci 0000:00:01.0: PCI bridge to [bus 01]
[    1.804762] pci 0000:00:01.0:   bridge window [io  0x4000-0x4fff]
[    1.804764] pci 0000:00:01.0:   bridge window [mem 0x9a000000-0x9b0fffff]
[    1.804767] pci 0000:00:01.0:   bridge window [mem 0xb0000000-0xc1ffffff 64bit pref]
[    1.804830] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    1.804917] pci 0000:03:00.0: [10ec:5287] type 00 class 0xff0000
[    1.804933] pci 0000:03:00.0: reg 0x10: [mem 0x9b215000-0x9b215fff]
[    1.804979] pci 0000:03:00.0: reg 0x30: [mem 0x9b200000-0x9b20ffff pref]
[    1.805062] pci 0000:03:00.0: supports D1 D2
[    1.805064] pci 0000:03:00.0: PME# supported from D1 D2 D3hot D3cold
[    1.805097] pci 0000:03:00.0: System wakeup disabled by ACPI
[    1.805137] pci 0000:03:00.1: [10ec:8168] type 00 class 0x020000
[    1.805158] pci 0000:03:00.1: reg 0x10: [io  0x3000-0x30ff]
[    1.805186] pci 0000:03:00.1: reg 0x18: [mem 0x9b214000-0x9b214fff 64bit]
[    1.805205] pci 0000:03:00.1: reg 0x20: [mem 0x9b210000-0x9b213fff 64bit]
[    1.805294] pci 0000:03:00.1: supports D1 D2
[    1.805295] pci 0000:03:00.1: PME# supported from D0 D1 D2 D3hot D3cold
[    1.812769] pci 0000:00:1c.4: PCI bridge to [bus 03]
[    1.812773] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
[    1.812776] pci 0000:00:1c.4:   bridge window [mem 0x9b200000-0x9b2fffff]
[    1.812892] pci 0000:04:00.0: [8086:095a] type 00 class 0x028000
[    1.812948] pci 0000:04:00.0: reg 0x10: [mem 0x9b100000-0x9b101fff 64bit]
[    1.813174] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    1.813226] pci 0000:04:00.0: System wakeup disabled by ACPI
[    1.820783] pci 0000:00:1c.5: PCI bridge to [bus 04]
[    1.820789] pci 0000:00:1c.5:   bridge window [mem 0x9b100000-0x9b1fffff]
[    1.820812] pci 0000:01:00.0: Max Payload Size 128, but upstream 0000:00:01.0 set to 256; if necessary, use "pci=pcie_bus_safe" and report a bug
[    1.821522] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.821563] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.821601] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.821639] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.821677] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.821713] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.821750] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.821787] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.822088] ACPI: Enabled 4 GPEs in block 00 to 3F
[    1.822117] ACPI : EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    1.822198] vgaarb: setting as boot device: PCI:0000:00:02.0
[    1.822200] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    1.822203] vgaarb: loaded
[    1.822204] vgaarb: bridge control possible 0000:00:02.0
[    1.822356] SCSI subsystem initialized
[    1.822384] libata version 3.00 loaded.
[    1.822398] ACPI: bus type USB registered
[    1.822407] usbcore: registered new interface driver usbfs
[    1.822412] usbcore: registered new interface driver hub
[    1.822434] usbcore: registered new device driver usb
[    1.822536] PCI: Using ACPI for IRQ routing
[    1.823800] PCI: pci_cache_line_size set to 64 bytes
[    1.823868] e820: reserve RAM buffer [mem 0x00058000-0x0005ffff]
[    1.823869] e820: reserve RAM buffer [mem 0x0009e000-0x0009ffff]
[    1.823870] e820: reserve RAM buffer [mem 0x8efad000-0x8fffffff]
[    1.823871] e820: reserve RAM buffer [mem 0x9222b000-0x93ffffff]
[    1.823872] e820: reserve RAM buffer [mem 0x93000000-0x93ffffff]
[    1.823873] e820: reserve RAM buffer [mem 0x467000000-0x467ffffff]
[    1.823938] NetLabel: Initializing
[    1.823940] NetLabel:  domain hash size = 128
[    1.823940] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.823948] NetLabel:  unlabeled traffic allowed by default
[    1.823986] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    1.823990] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    1.826020] Switched to clocksource hpet
[    1.829958] AppArmor: AppArmor Filesystem Enabled
[    1.829979] pnp: PnP ACPI init
[    1.829987] ACPI: bus type PNP registered
[    1.830102] pnp 00:00: Plug and Play ACPI device, IDs PNP0303 (active)
[    1.830173] pnp 00:01: Plug and Play ACPI device, IDs SYN1214 PNP0f13 (active)
[    1.830216] pnp 00:02: disabling [io  0x002e-0x002f] because it overlaps 0000:01:00.0 BAR 5 [io  0x0000-0x007f]
[    1.830219] pnp 00:02: disabling [io  0x004e-0x004f] because it overlaps 0000:01:00.0 BAR 5 [io  0x0000-0x007f]
[    1.830222] pnp 00:02: disabling [io  0x0061] because it overlaps 0000:01:00.0 BAR 5 [io  0x0000-0x007f]
[    1.830224] pnp 00:02: disabling [io  0x0063] because it overlaps 0000:01:00.0 BAR 5 [io  0x0000-0x007f]
[    1.830226] pnp 00:02: disabling [io  0x0065] because it overlaps 0000:01:00.0 BAR 5 [io  0x0000-0x007f]
[    1.830228] pnp 00:02: disabling [io  0x0067] because it overlaps 0000:01:00.0 BAR 5 [io  0x0000-0x007f]
[    1.830230] pnp 00:02: disabling [io  0x0070] because it overlaps 0000:01:00.0 BAR 5 [io  0x0000-0x007f]
[    1.830253] system 00:02: [io  0x0680-0x069f] has been reserved
[    1.830255] system 00:02: [io  0xffff] has been reserved
[    1.830257] system 00:02: [io  0xffff] has been reserved
[    1.830259] system 00:02: [io  0xffff] has been reserved
[    1.830261] system 00:02: [io  0x1800-0x18fe] could not be reserved
[    1.830262] system 00:02: [io  0x164e-0x164f] has been reserved
[    1.830265] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.830301] system 00:03: [io  0x0800-0x087f] has been reserved
[    1.830304] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.830325] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.830361] system 00:05: [io  0x1854-0x1857] has been reserved
[    1.830363] system 00:05: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    1.830459] system 00:06: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    1.830461] system 00:06: [mem 0xfed10000-0xfed17fff] has been reserved
[    1.830463] system 00:06: [mem 0xfed18000-0xfed18fff] has been reserved
[    1.830464] system 00:06: [mem 0xfed19000-0xfed19fff] has been reserved
[    1.830466] system 00:06: [mem 0xf8000000-0xfbffffff] has been reserved
[    1.830467] system 00:06: [mem 0xfed20000-0xfed3ffff] has been reserved
[    1.830469] system 00:06: [mem 0xfed90000-0xfed93fff] could not be reserved
[    1.830470] system 00:06: [mem 0xfed45000-0xfed8ffff] has been reserved
[    1.830472] system 00:06: [mem 0xff000000-0xffffffff] has been reserved
[    1.830474] system 00:06: [mem 0xfee00000-0xfeefffff] could not be reserved
[    1.830475] system 00:06: [mem 0x98010000-0x9801ffff] has been reserved
[    1.830477] system 00:06: [mem 0x98000000-0x9800ffff] has been reserved
[    1.830478] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.830745] pnp: PnP ACPI: found 7 devices
[    1.830747] ACPI: bus type PNP unregistered
[    1.836508] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 02] add_size 1000
[    1.836510] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02] add_size 200000
[    1.836511] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 02] add_size 200000
[    1.836525] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    1.836526] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    1.836527] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    1.836531] pci 0000:00:1c.0: BAR 14: assigned [mem 0x98100000-0x982fffff]
[    1.836537] pci 0000:00:1c.0: BAR 15: assigned [mem 0x98300000-0x984fffff 64bit pref]
[    1.836540] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    1.836542] pci 0000:01:00.0: BAR 1: assigned [mem 0xb0000000-0xbfffffff 64bit pref]
[    1.836553] pci 0000:01:00.0: BAR 3: assigned [mem 0xc0000000-0xc1ffffff 64bit pref]
[    1.836565] pci 0000:01:00.0: BAR 0: assigned [mem 0x9a000000-0x9affffff]
[    1.836569] pci 0000:01:00.0: BAR 6: assigned [mem 0x9b000000-0x9b07ffff pref]
[    1.836571] pci 0000:01:00.0: BAR 5: assigned [io  0x4000-0x407f]
[    1.836576] pci 0000:00:01.0: PCI bridge to [bus 01]
[    1.836577] pci 0000:00:01.0:   bridge window [io  0x4000-0x4fff]
[    1.836580] pci 0000:00:01.0:   bridge window [mem 0x9a000000-0x9b0fffff]
[    1.836582] pci 0000:00:01.0:   bridge window [mem 0xb0000000-0xc1ffffff 64bit pref]
[    1.836585] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    1.836587] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    1.836592] pci 0000:00:1c.0:   bridge window [mem 0x98100000-0x982fffff]
[    1.836595] pci 0000:00:1c.0:   bridge window [mem 0x98300000-0x984fffff 64bit pref]
[    1.836601] pci 0000:00:1c.4: PCI bridge to [bus 03]
[    1.836603] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
[    1.836608] pci 0000:00:1c.4:   bridge window [mem 0x9b200000-0x9b2fffff]
[    1.836614] pci 0000:00:1c.5: PCI bridge to [bus 04]
[    1.836619] pci 0000:00:1c.5:   bridge window [mem 0x9b100000-0x9b1fffff]
[    1.836626] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.836627] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.836628] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.836628] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    1.836629] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    1.836630] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    1.836631] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff]
[    1.836632] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff]
[    1.836633] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff]
[    1.836634] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff]
[    1.836635] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff]
[    1.836635] pci_bus 0000:00: resource 15 [mem 0x000e0000-0x000e3fff]
[    1.836636] pci_bus 0000:00: resource 16 [mem 0x000e4000-0x000e7fff]
[    1.836637] pci_bus 0000:00: resource 17 [mem 0x000e8000-0x000ebfff]
[    1.836638] pci_bus 0000:00: resource 18 [mem 0x000ec000-0x000effff]
[    1.836639] pci_bus 0000:00: resource 19 [mem 0x98000000-0xdfffffff]
[    1.836640] pci_bus 0000:00: resource 20 [mem 0xfe101000-0xfe113fff]
[    1.836641] pci_bus 0000:01: resource 0 [io  0x4000-0x4fff]
[    1.836641] pci_bus 0000:01: resource 1 [mem 0x9a000000-0x9b0fffff]
[    1.836642] pci_bus 0000:01: resource 2 [mem 0xb0000000-0xc1ffffff 64bit pref]
[    1.836643] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    1.836644] pci_bus 0000:02: resource 1 [mem 0x98100000-0x982fffff]
[    1.836645] pci_bus 0000:02: resource 2 [mem 0x98300000-0x984fffff 64bit pref]
[    1.836646] pci_bus 0000:03: resource 0 [io  0x3000-0x3fff]
[    1.836647] pci_bus 0000:03: resource 1 [mem 0x9b200000-0x9b2fffff]
[    1.836648] pci_bus 0000:04: resource 1 [mem 0x9b100000-0x9b1fffff]
[    1.836665] NET: Registered protocol family 2
[    1.836808] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.836956] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.837070] TCP: Hash tables configured (established 131072 bind 65536)
[    1.837084] TCP: reno registered
[    1.837095] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    1.837132] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    1.837189] NET: Registered protocol family 1
[    1.837199] pci 0000:00:02.0: Video device with shadowed ROM
[    1.874113] PCI: CLS 0 bytes, default 64
[    1.874150] Trying to unpack rootfs image as initramfs...
[    2.149357] Freeing initrd memory: 27328K (ffff880034a90000 - ffff880036540000)
[    2.149377] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    2.149380] software IO TLB [mem 0x872c1000-0x8b2c1000] (64MB) mapped at [ffff8800872c1000-ffff88008b2c0fff]
[    2.149621] microcode: CPU0 sig=0x40671, pf=0x20, revision=0xd
[    2.149628] microcode: CPU1 sig=0x40671, pf=0x20, revision=0xd
[    2.149633] microcode: CPU2 sig=0x40671, pf=0x20, revision=0xd
[    2.149641] microcode: CPU3 sig=0x40671, pf=0x20, revision=0xd
[    2.149648] microcode: CPU4 sig=0x40671, pf=0x20, revision=0xd
[    2.149654] microcode: CPU5 sig=0x40671, pf=0x20, revision=0xd
[    2.149660] microcode: CPU6 sig=0x40671, pf=0x20, revision=0xd
[    2.149667] microcode: CPU7 sig=0x40671, pf=0x20, revision=0xd
[    2.149699] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    2.149716] Scanning for low memory corruption every 60 seconds
[    2.149955] futex hash table entries: 2048 (order: 5, 131072 bytes)
[    2.149968] Initialise system trusted keyring
[    2.149981] audit: initializing netlink subsys (disabled)
[    2.149989] audit: type=2000 audit(1449049929.136:1): initialized
[    2.150176] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    2.151072] zpool: loaded
[    2.151074] zbud: loaded
[    2.151194] VFS: Disk quotas dquot_6.5.2
[    2.151218] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    2.151535] fuse init (API version 7.23)
[    2.151593] msgmni has been set to 31610
[    2.151633] Key type big_key registered
[    2.151927] Key type asymmetric registered
[    2.151930] Asymmetric key parser 'x509' registered
[    2.151956] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    2.152003] io scheduler noop registered
[    2.152006] io scheduler deadline registered (default)
[    2.152040] io scheduler cfq registered
[    2.152191] pcieport 0000:00:01.0: irq 42 for MSI/MSI-X
[    2.152301] pcieport 0000:00:1c.0: irq 43 for MSI/MSI-X
[    2.152418] pcieport 0000:00:1c.4: irq 44 for MSI/MSI-X
[    2.152524] pcieport 0000:00:1c.5: irq 45 for MSI/MSI-X
[    2.152589] pcieport 0000:00:01.0: Signaling PME through PCIe PME interrupt
[    2.152591] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    2.152593] pcie_pme 0000:00:01.0:pcie01: service driver pcie_pme loaded
[    2.152603] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    2.152608] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    2.152618] pcieport 0000:00:1c.4: Signaling PME through PCIe PME interrupt
[    2.152619] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    2.152621] pci 0000:03:00.1: Signaling PME through PCIe PME interrupt
[    2.152626] pcie_pme 0000:00:1c.4:pcie01: service driver pcie_pme loaded
[    2.152636] pcieport 0000:00:1c.5: Signaling PME through PCIe PME interrupt
[    2.152638] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt
[    2.152642] pcie_pme 0000:00:1c.5:pcie01: service driver pcie_pme loaded
[    2.152655] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.152691] pciehp 0000:00:1c.0:pcie04: Slot #0 AttnBtn- AttnInd- PwrInd- PwrCtrl- MRL- Interlock- NoCompl+ LLActRep+
[    2.152723] pciehp 0000:00:1c.0:pcie04: service driver pciehp loaded
[    2.152726] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.152765] efifb: probing for efifb
[    2.152782] efifb: framebuffer at 0xa0000000, mapped to 0xffffc90005c00000, using 8128k, total 8128k
[    2.152784] efifb: mode is 1920x1080x32, linelength=7680, pages=1
[    2.152785] efifb: scrolling: redraw
[    2.152786] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    2.155789] Console: switching to colour frame buffer device 240x67
[    2.158882] fb0: EFI VGA frame buffer device
[    2.158906] intel_idle: does not run on family 6 model 71
[    2.159442] ACPI: AC Adapter [AC] (on-line)
[    2.159654] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    2.159678] ACPI: Power Button [PWRB]
[    2.159708] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    2.159731] ACPI: Sleep Button [SLPB]
[    2.159762] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
[    2.159799] ACPI: Lid Switch [LID0]
[    2.159832] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    2.159852] ACPI: Power Button [PWRF]
[    2.159901] ACPI: Fan [FAN0] (off)
[    2.159927] ACPI: Fan [FAN1] (off)
[    2.159952] ACPI: Fan [FAN2] (off)
[    2.159977] ACPI: Fan [FAN3] (off)
[    2.160009] ACPI: Fan [FAN4] (off)
[    2.160191] Monitor-Mwait will be used to enter C-1 state
[    2.160199] Monitor-Mwait will be used to enter C-2 state
[    2.160205] ACPI: acpi_idle registered with cpuidle
[    2.161186] thermal LNXTHERM:00: registered as thermal_zone0
[    2.161201] ACPI: Thermal Zone [TZ0] (25 C)
[    2.161392] thermal LNXTHERM:01: registered as thermal_zone1
[    2.161407] ACPI: Thermal Zone [TZ00] (28 C)
[    2.161535] thermal LNXTHERM:02: registered as thermal_zone2
[    2.161550] ACPI: Thermal Zone [TZ01] (30 C)
[    2.161588] GHES: HEST is not enabled!
[    2.161663] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    2.161880] ACPI: Battery Slot [BAT0] (battery present)
[    2.162681] Linux agpgart interface v0.103
[    2.163452] brd: module loaded
[    2.163819] loop: module loaded
[    2.163953] libphy: Fixed MDIO Bus: probed
[    2.163966] tun: Universal TUN/TAP device driver, 1.6
[    2.163980] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.164019] PPP generic driver version 2.4.2
[    2.164055] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.164075] ehci-pci: EHCI PCI platform driver
[    2.164150] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    2.164169] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.164198] ehci-pci 0000:00:1a.0: debug port 2
[    2.168117] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    2.168128] ehci-pci 0000:00:1a.0: irq 16, io mem 0x9b31b000
[    2.177917] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    2.177963] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    2.177986] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.178010] usb usb1: Product: EHCI Host Controller
[    2.178027] usb usb1: Manufacturer: Linux 3.16.0-55-generic ehci_hcd
[    2.178945] usb usb1: SerialNumber: 0000:00:1a.0
[    2.179769] hub 1-0:1.0: USB hub found
[    2.180464] hub 1-0:1.0: 2 ports detected
[    2.181271] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    2.181977] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.182717] ehci-pci 0000:00:1d.0: debug port 2
[    2.187305] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    2.187313] ehci-pci 0000:00:1d.0: irq 23, io mem 0x9b31a000
[    2.197913] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    2.198822] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    2.198828] random: nonblocking pool is initialized
[    2.200379] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.201090] usb usb2: Product: EHCI Host Controller
[    2.201795] usb usb2: Manufacturer: Linux 3.16.0-55-generic ehci_hcd
[    2.202508] usb usb2: SerialNumber: 0000:00:1d.0
[    2.203272] hub 2-0:1.0: USB hub found
[    2.203971] hub 2-0:1.0: 2 ports detected
[    2.204746] ehci-platform: EHCI generic platform driver
[    2.205451] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.206144] ohci-pci: OHCI PCI platform driver
[    2.206829] ohci-platform: OHCI generic platform driver
[    2.207476] uhci_hcd: USB Universal Host Controller Interface driver
[    2.208249] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    2.208923] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    2.209689] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    2.209705] xhci_hcd 0000:00:14.0: irq 46 for MSI/MSI-X
[    2.209740] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    2.210427] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.211106] usb usb3: Product: xHCI Host Controller
[    2.211785] usb usb3: Manufacturer: Linux 3.16.0-55-generic xhci_hcd
[    2.212461] usb usb3: SerialNumber: 0000:00:14.0
[    2.213187] hub 3-0:1.0: USB hub found
[    2.213858] hub 3-0:1.0: 14 ports detected
[    2.216864] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    2.217506] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    2.218102] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    2.218741] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.219374] usb usb4: Product: xHCI Host Controller
[    2.220009] usb usb4: Manufacturer: Linux 3.16.0-55-generic xhci_hcd
[    2.220656] usb usb4: SerialNumber: 0000:00:14.0
[    2.221365] hub 4-0:1.0: USB hub found
[    2.222039] hub 4-0:1.0: 6 ports detected
[    2.223681] usb: failed to peer usb4-port5 and usb3-port2 by location (usb4-port5:none) (usb3-port2:usb4-port2)
[    2.224366] usb usb4-port5: failed to peer to usb3-port2 (-16)
[    2.225047] usb: port power management may be unreliable
[    2.225923] usb: failed to peer usb4-port6 and usb3-port2 by location (usb4-port6:none) (usb3-port2:usb4-port2)
[    2.226624] usb usb4-port6: failed to peer to usb3-port2 (-16)
[    2.227399] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:SYNM] at 0x60,0x64 irq 1,12
[    2.750819] i8042: Detected active multiplexing controller, rev 1.1
[    2.753626] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.754345] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.755065] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.755776] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.756480] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.757254] mousedev: PS/2 mouse device common for all mice
[    2.758155] rtc_cmos 00:04: RTC can wake from S4
[    2.759094] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    2.759938] rtc_cmos 00:04: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    2.760681] device-mapper: uevent: version 1.0.3
[    2.761186] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    2.762202] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    2.762936] ledtrig-cpu: registered to indicate activity on CPUs
[    2.763659] EFI Variables Facility v0.08 2004-May-17
[    2.765815] TCP: cubic registered
[    2.766679] NET: Registered protocol family 10
[    2.767615] NET: Registered protocol family 17
[    2.768253] Key type dns_resolver registered
[    2.769436] Loading compiled-in X.509 certificates
[    2.770655] Loaded X.509 cert 'Magrathea: Glacier signing key: c0e79120a193454330069fccfa63e661c83064f8'
[    2.771396] registered taskstats version 1
[    2.773411] Key type trusted registered
[    2.777180] Key type encrypted registered
[    2.778014] AppArmor: AppArmor sha1 policy hashing enabled
[    2.778822] ima: No TPM chip found, activating TPM-bypass!
[    2.779587] evm: HMAC attrs: 0x1
[    2.780784]   Magic number: 11:478:878
[    2.781617] rtc_cmos 00:04: setting system clock to 2015-12-02 09:52:10 UTC (1449049930)
[    2.783333] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.784000] EDD information not available.
[    2.784796] PM: Hibernation image not present or could not be loaded.
[    2.785360] Freeing unused kernel memory: 1356K (ffffffff81d1c000 - ffffffff81e6f000)
[    2.786127] Write protecting the kernel read-only data: 12288k
[    2.787129] Freeing unused kernel memory: 544K (ffff880002778000 - ffff880002800000)
[    2.788590] Freeing unused kernel memory: 480K (ffff880002b88000 - ffff880002c00000)
[    2.800516] systemd-udevd[152]: starting version 204
[    2.809323] sdhci: Secure Digital Host Controller Interface driver
[    2.810100] sdhci: Copyright(c) Pierre Ossman
[    2.812372] wmi: Mapper loaded
[    2.818773] rtsx_pci 0000:03:00.0: enabling device (0000 -> 0002)
[    2.819747] rtsx_pci 0000:03:00.0: irq 47 for MSI/MSI-X
[    2.819758] rtsx_pci 0000:03:00.0: rtsx_pci_acquire_irq: pcr->msi_en = 1, pci->irq = 47
[    2.820924] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.822410] r8169 0000:03:00.1: can't disable ASPM; OS doesn't have ASPM control
[    2.823970] ahci 0000:00:1f.2: version 3.0
[    2.824076] ahci 0000:00:1f.2: irq 48 for MSI/MSI-X
[    2.824101] ahci 0000:00:1f.2: SSS flag set, parallel bus scan disabled
[    2.825134] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x37 impl SATA mode
[    2.826129] ahci 0000:00:1f.2: flags: 64bit ncq stag pm led clo pio slum part ems sxs apst 
[    2.826219] [drm] Initialized drm 1.1.0 20060810
[    2.830083] r8169 0000:03:00.1: irq 49 for MSI/MSI-X
[    2.830266] r8169 0000:03:00.1 eth0: RTL8411 at 0xffffc900018fa000, 80:fa:5b:1e:9c:e7, XID 1c800800 IRQ 49
[    2.831207] r8169 0000:03:00.1 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    2.847788] MXM: GUID detected in BIOS
[    2.848536] ACPI Warning: \_SB_.PCI0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20140424/nsarguments-95)
[    2.849412] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20140424/nsarguments-95)
[    2.850304] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20140424/nsarguments-95)
[    2.851268] pci 0000:01:00.0: optimus capabilities: enabled, status dynamic power, hda bios codec supported
[    2.852113] VGA switcheroo: detected Optimus DSM method \_SB_.PCI0.PEG0.PEGP handle
[    2.852969] checking generic (a0000000 7f0000) vs hw (b0000000 10000000)
[    2.852970] checking generic (a0000000 7f0000) vs hw (c0000000 2000000)
[    2.852992] nouveau 0000:01:00.0: enabling device (0004 -> 0007)
[    2.854021] nouveau E[  DEVICE][0000:01:00.0] unknown chipset, 0x124170a1
[    2.854874] nouveau E[     DRM] failed to create 0x80000080, -22
[    2.855823] nouveau: probe of 0000:01:00.0 failed with error -22
[    2.858162] scsi0 : ahci
[    2.859284] scsi1 : ahci
[    2.860188] scsi2 : ahci
[    2.861079] scsi3 : ahci
[    2.861967] scsi4 : ahci
[    2.862828] scsi5 : ahci
[    2.863619] ata1: SATA max UDMA/133 abar m2048@0x9b319000 port 0x9b319100 irq 48
[    2.864393] ata2: SATA max UDMA/133 abar m2048@0x9b319000 port 0x9b319180 irq 48
[    2.865157] ata3: SATA max UDMA/133 abar m2048@0x9b319000 port 0x9b319200 irq 48
[    2.865921] ata4: DUMMY
[    2.866682] ata5: SATA max UDMA/133 abar m2048@0x9b319000 port 0x9b319300 irq 48
[    2.867466] ata6: SATA max UDMA/133 abar m2048@0x9b319000 port 0x9b319380 irq 48
[    2.868588] [drm] Memory usable by graphics device = 4096M
[    2.870074] checking generic (a0000000 7f0000) vs hw (a0000000 10000000)
[    2.870075] fb: switching to inteldrmfb from EFI VGA
[    2.870824] Console: switching to colour dummy device 80x25
[    2.870914] [drm] Replacing VGA console driver
[    2.893707] i915 0000:00:02.0: irq 50 for MSI/MSI-X
[    2.893715] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    2.893717] [drm] Driver supports precise vblank timestamp query.
[    2.893760] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    2.930298] [drm] VBT doesn't support DRRS
[    2.957625] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    3.145571] tsc: Refined TSC clocksource calibration: 2693.762 MHz
[    3.169945] usb 1-1: New USB device found, idVendor=8087, idProduct=8008
[    3.169948] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    3.170101] hub 1-1:1.0: USB hub found
[    3.170196] hub 1-1:1.0: 6 ports detected
[    3.185552] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    3.186698] ata1.00: ATA-8: HGST HTS721010A9E630, JB0OA3J0, max UDMA/133
[    3.186701] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    3.187925] ata1.00: configured for UDMA/133
[    3.188015] scsi 0:0:0:0: Direct-Access     ATA      HGST HTS721010A9 A3J0 PQ: 0 ANSI: 5
[    3.188170] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    3.188174] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    3.188193] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.188194] sd 0:0:0:0: [sda] Write Protect is off
[    3.188196] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.188203] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.249949]  sda: sda1
[    3.250082] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.281499] [drm] GMBUS [i915 gmbus vga] timed out, falling back to bit banging on pin 2
[    3.337499] usb 3-1: new full-speed USB device number 2 using xhci_hcd
[    3.348491] fbcon: inteldrmfb (fb0) is primary device
[    3.466560] usb 3-1: New USB device found, idVendor=1d50, idProduct=607d
[    3.466561] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    3.466562] usb 3-1: Product: Spark Core with WiFi    
[    3.466563] usb 3-1: Manufacturer: Particle          
[    3.466563] usb 3-1: SerialNumber: 6D821F664852
[    3.466631] usb 3-1: ep 0x82 - rounding interval to 1024 microframes, ep desc says 2040 microframes
[    3.505433] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    3.505805] ata2.00: ATA-9: M4-CT512M4SSD2, 070H, max UDMA/100
[    3.505807] ata2.00: 1000215216 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    3.506219] ata2.00: configured for UDMA/100
[    3.506291] scsi 1:0:0:0: Direct-Access     ATA      M4-CT512M4SSD2   070H PQ: 0 ANSI: 5
[    3.506443] sd 1:0:0:0: [sdb] 1000215216 512-byte logical blocks: (512 GB/476 GiB)
[    3.506466] sd 1:0:0:0: [sdb] Write Protect is off
[    3.506467] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.506468] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    3.506475] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.506775]  sdb: sdb1
[    3.506864] sd 1:0:0:0: [sdb] Attached SCSI disk
[    3.664580] usb 3-2: new full-speed USB device number 3 using xhci_hcd
[    3.825346] ata3: SATA link down (SStatus 0 SControl 300)
[    3.850276] usb 3-2: New USB device found, idVendor=1532, idProduct=0040
[    3.850277] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.850278] usb 3-2: Product: Razer Naga 2014
[    3.850278] usb 3-2: Manufacturer: Razer
[    3.892564] hidraw: raw HID events driver (C) Jiri Kosina
[    3.894901] usbcore: registered new interface driver usbhid
[    3.894902] usbhid: USB HID core driver
[    3.896161] input: Razer Razer Naga 2014 as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.0/0003:1532:0040.0001/input/input11
[    3.896274] hid-generic 0003:1532:0040.0001: input,hidraw0: USB HID v1.11 Mouse [Razer Razer Naga 2014] on usb-0000:00:14.0-2/input0
[    3.897054] input: Razer Razer Naga 2014 as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.1/0003:1532:0040.0002/input/input12
[    3.897109] hid-generic 0003:1532:0040.0002: input,hidraw1: USB HID v1.11 Keyboard [Razer Razer Naga 2014] on usb-0000:00:14.0-2/input1
[    3.897255] input: Razer Razer Naga 2014 as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.2/0003:1532:0040.0003/input/input13
[    3.897350] hid-generic 0003:1532:0040.0003: input,hidraw2: USB HID v1.11 Keyboard [Razer Razer Naga 2014] on usb-0000:00:14.0-2/input2
[    3.965274] usb 3-3: new full-speed USB device number 4 using xhci_hcd
[    4.035972] psmouse serio2: synaptics: queried max coordinates: x [..5706], y [..4800]
[    4.094803] usb 3-3: New USB device found, idVendor=1c7a, idProduct=0603
[    4.094804] usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    4.094805] usb 3-3: Product: EgisTec_ES603
[    4.094806] usb 3-3: Manufacturer: EgisTec
[    4.145256] ata5: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    4.145406] Switched to clocksource tsc
[    4.145484] ata5.00: supports DRM functions and may not be fully accessible
[    4.145879] ata5.00: disabling queued TRIM support
[    4.145880] ata5.00: ATA-9: Samsung SSD 850 EVO M.2 250GB, EMT21B6Q, max UDMA/133
[    4.145881] ata5.00: 488397168 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    4.146427] ata5.00: supports DRM functions and may not be fully accessible
[    4.146660] ata5.00: disabling queued TRIM support
[    4.146852] ata5.00: configured for UDMA/133
[    4.147003] scsi 4:0:0:0: Direct-Access     ATA      Samsung SSD 850  1B6Q PQ: 0 ANSI: 5
[    4.147222] sd 4:0:0:0: [sdc] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    4.147223] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    4.147298] sd 4:0:0:0: [sdc] Write Protect is off
[    4.147299] sd 4:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    4.147343] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.149237]  sdc: sdc1 sdc2 sdc3 sdc4
[    4.149531] sd 4:0:0:0: [sdc] Attached SCSI disk
[    4.178757] psmouse serio2: synaptics: Touchpad model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xd00033/0x240000/0xa0400, board id: 1474, fw id: 793787
[    4.214940] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input10
[    4.261143] usb 3-4: new full-speed USB device number 5 using xhci_hcd
[    4.321154] Console: switching to colour frame buffer device 240x67
[    4.337725] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    4.338637] i915 0000:00:02.0: registered panic notifier
[    4.346280] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    4.347254] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input16
[    4.348260] ACPI Exception: AE_NOT_FOUND, Evaluating _DOD (20140424/video-1419)
[    4.349206] ACPI: Video Device [PEGP] (multi-head: no  rom: yes  post: no)
[    4.350177] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:12/LNXVIDEO:01/input/input17
[    4.351203] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    4.389671] usb 3-4: No LPM exit latency info found, disabling LPM.
[    4.391694] usb 3-4: New USB device found, idVendor=8087, idProduct=0a2a
[    4.392905] usb 3-4: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    4.465111] ata6: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    4.466549] ata6.00: supports DRM functions and may not be fully accessible
[    4.468011] ata6.00: disabling queued TRIM support
[    4.468013] ata6.00: ATA-9: Samsung SSD 850 EVO M.2 250GB, EMT21B6Q, max UDMA/133
[    4.469260] ata6.00: 488397168 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    4.470695] ata6.00: supports DRM functions and may not be fully accessible
[    4.471957] ata6.00: disabling queued TRIM support
[    4.472155] ata6.00: configured for UDMA/133
[    4.473461] scsi 5:0:0:0: Direct-Access     ATA      Samsung SSD 850  1B6Q PQ: 0 ANSI: 5
[    4.474467] sd 5:0:0:0: Attached scsi generic sg3 type 0
[    4.474484] sd 5:0:0:0: [sdd] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    4.474678] sd 5:0:0:0: [sdd] Write Protect is off
[    4.474680] sd 5:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    4.474737] sd 5:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.476018]  sdd: sdd1 sdd2
[    4.476252] sd 5:0:0:0: [sdd] Attached SCSI disk
[    4.561073] usb 3-10: new high-speed USB device number 6 using xhci_hcd
[    4.793278] usb 3-10: New USB device found, idVendor=5986, idProduct=066d
[    4.795126] usb 3-10: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[    4.796976] usb 3-10: Product: BisonCam, NB Pro
[    4.798808] usb 3-10: Manufacturer: Generic
[    4.800627] usb 3-10: SerialNumber: 200901010001
[    4.829035] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
[    4.838275] EXT4-fs (sdd1): INFO: recovery required on readonly filesystem
[    4.838298] EXT4-fs (sdd1): write access will be enabled during recovery
[    4.853860] EXT4-fs (sdd1): recovery complete
[    4.854545] EXT4-fs (sdd1): mounted filesystem with ordered data mode. Opts: (null)
[    4.924909] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    5.025952] EXT4-fs (sdd1): re-mounted. Opts: errors=remount-ro
[    5.030511] systemd-udevd[395]: starting version 204
[    5.057280] usb 2-1: New USB device found, idVendor=8087, idProduct=8000
[    5.057283] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    5.057540] hub 2-1:1.0: USB hub found
[    5.057638] hub 2-1:1.0: 8 ports detected
[    5.060827] lp: driver loaded but no devices found
[    5.066574] ppdev: user-space parallel port driver
[    5.102665] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    5.149798] snd_hda_intel 0000:00:03.0: enabling device (0000 -> 0002)
[    5.149933] snd_hda_intel 0000:00:03.0: irq 51 for MSI/MSI-X
[    5.149974] snd_hda_intel 0000:00:1b.0: enabling device (0000 -> 0002)
[    5.150082] snd_hda_intel 0000:00:1b.0: irq 52 for MSI/MSI-X
[    5.152138] mei_me 0000:00:16.0: irq 53 for MSI/MSI-X
[    5.157188] cfg80211: Calling CRDA to update world regulatory domain
[    5.164699] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input18
[    5.167163] sound hdaudioC1D0: ignore pin 0x1b with mismatching assoc# 0x3 vs 0x2
[    5.167230] sound hdaudioC1D0: autoconfig: line_outs=1 (0x17/0x0/0x0/0x0/0x0) type:line
[    5.167232] sound hdaudioC1D0:    speaker_outs=1 (0x14/0x0/0x0/0x0/0x0)
[    5.167233] sound hdaudioC1D0:    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    5.167234] sound hdaudioC1D0:    mono: mono_out=0x0
[    5.167235] sound hdaudioC1D0:    dig-out=0x1e/0x0
[    5.167235] sound hdaudioC1D0:    inputs:
[    5.167237] sound hdaudioC1D0:      Mic=0x18
[    5.167238] sound hdaudioC1D0:      Internal Mic=0x12
[    5.173752] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input19
[    5.173818] input: HDA Intel PCH Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card1/input20
[    5.175635] Intel(R) Wireless WiFi driver for Linux, in-tree:
[    5.175641] Copyright(c) 2003- 2014 Intel Corporation
[    5.175744] iwlwifi 0000:04:00.0: enabling device (0000 -> 0002)
[    5.175984] iwlwifi 0000:04:00.0: irq 54 for MSI/MSI-X
[    5.184272] iwlwifi 0000:04:00.0: loaded firmware version 25.228.9.0 op_mode iwlmvm
[    5.186122] iwlwifi 0000:04:00.0: Unsupported splx structure
[    5.188139] AVX2 version of gcm_enc/dec engaged.
[    5.189567] audit: type=1400 audit(1449078732.904:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=581 comm="apparmor_parser"
[    5.189572] audit: type=1400 audit(1449078732.904:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=581 comm="apparmor_parser"
[    5.189576] audit: type=1400 audit(1449078732.904:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=581 comm="apparmor_parser"
[    5.189923] audit: type=1400 audit(1449078732.904:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=581 comm="apparmor_parser"
[    5.189928] audit: type=1400 audit(1449078732.904:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=581 comm="apparmor_parser"
[    5.190108] audit: type=1400 audit(1449078732.904:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=581 comm="apparmor_parser"
[    5.206643] iwlwifi 0000:04:00.0: Detected Intel(R) Dual Band Wireless AC 7265, REV=0x210
[    5.206714] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled
[    5.206897] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled
[    5.232929] cdc_acm 3-1:1.0: This device cannot do calls on its own. It is not a modem.
[    5.232971] cdc_acm 3-1:1.0: ttyACM0: USB ACM device
[    5.233161] usbcore: registered new interface driver cdc_acm
[    5.233162] cdc_acm: USB Abstract Control Model driver for USB modems and ISDN adapters
[    5.242846] media: Linux media interface: v0.10
[    5.247028] Bluetooth: Core ver 2.19
[    5.247040] NET: Registered protocol family 31
[    5.247041] Bluetooth: HCI device and connection manager initialized
[    5.247048] Bluetooth: HCI socket layer initialized
[    5.247050] Bluetooth: L2CAP socket layer initialized
[    5.247056] Bluetooth: SCO socket layer initialized
[    5.248591] Linux video capture interface: v2.00
[    5.254485] usbcore: registered new interface driver btusb
[    5.260499] uvcvideo: Found UVC 1.00 device BisonCam, NB Pro (5986:066d)
[    5.262978] input: BisonCam, NB Pro as /devices/pci0000:00/0000:00:14.0/usb3/3-10/3-10:1.0/input/input21
[    5.263113] usbcore: registered new interface driver uvcvideo
[    5.263114] USB Video Class driver (1.1.1)
[    5.264439] cfg80211: World regulatory domain updated:
[    5.264441] cfg80211:  DFS Master region: unset
[    5.264441] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[    5.264443] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[    5.264444] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[    5.264445] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[    5.264446] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[    5.264447] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[    5.269523] Bluetooth: hci0: read Intel version: 370810011003110e00
[    5.271900] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.8.10-fw-1.10.3.11.e.bseq
[    5.277914] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    5.304204] EXT4-fs (sdd2): mounted filesystem with ordered data mode. Opts: (null)
[    5.329384] init: failsafe main process (892) killed by TERM signal
[    5.338481] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[    5.343781] init: rsyslog main process (932) terminated with status 127
[    5.343787] init: rsyslog main process ended, respawning
[    5.388347] Bluetooth: RFCOMM TTY layer initialized
[    5.388355] Bluetooth: RFCOMM socket layer initialized
[    5.388359] Bluetooth: RFCOMM ver 1.11
[    5.388632] audit: type=1400 audit(1449078733.100:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=960 comm="apparmor_parser"
[    5.388637] audit: type=1400 audit(1449078733.100:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=960 comm="apparmor_parser"
[    5.388887] audit: type=1400 audit(1449078733.104:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=960 comm="apparmor_parser"
[    5.393317] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    5.393318] Bluetooth: BNEP filters: protocol multicast
[    5.393324] Bluetooth: BNEP socket layer initialized
[    5.400639] init: cups main process (981) killed by HUP signal
[    5.400644] init: cups main process ended, respawning
[    5.554837] r8169 0000:03:00.1 eth0: link down
[    5.554876] r8169 0000:03:00.1 eth0: link down
[    5.554884] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.556014] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled
[    5.556196] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled
[    5.565771] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    5.927900] init: alsa-restore main process (1177) terminated with status 99
[    6.098207] vboxdrv: module verification failed: signature and/or  required key missing - tainting kernel
[    6.100774] vboxdrv: Found 8 processor cores.
[    6.100939] vboxdrv: fAsync=0 offMin=0x159 offMax=0x10ec
[    6.101025] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[    6.101026] vboxdrv: Successfully loaded version 4.3.34_Ubuntu (interface 0x001a000b).
[    6.111493] vboxpci: IOMMU not found (not registered)
[    6.380936] init: plymouth-upstart-bridge main process ended, respawning
[    8.504559] r8169 0000:03:00.1 eth0: link up
[    8.504565] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[    9.123460] wlan0: authenticate with e0:3f:49:99:ee:b8
[    9.126653] wlan0: send auth to e0:3f:49:99:ee:b8 (try 1/3)
[    9.130720] wlan0: authenticated
[    9.131398] wlan0: associate with e0:3f:49:99:ee:b8 (try 1/3)
[    9.135122] wlan0: RX AssocResp from e0:3f:49:99:ee:b8 (capab=0x411 status=0 aid=13)
[    9.137309] wlan0: associated
[    9.137325] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   11.420140] Valid eCryptfs headers not found in file header region or xattr region, inode 9437227
[   11.893681] Valid eCryptfs headers not found in file header region or xattr region, inode 9437682

```

---

### Post by ian-weisser on 2015-12-02
The log is post-reboot, sorry.
That kind of ultimate-super-kernel-crash doesn't usually leave a log trace.
If the kernel identified an error for logging, it generally wouldn't have clobbered your system.

I think you are right to discount /etc/fstab as coincidental and to keep looking for more subtle clues.

---

### Post by John_Dempsey on 2015-12-03
Thanks.  I've been looking into logging into the laptop while in the lockup state with a serial cable and a second machine somehow, but the lockup is rare (once or twice a day) so I don't know if it would be worth pursuing in an in-depth effort.  Also, I'm not sure exactly on how to go about a serial connection because my laptop doesn't have a RS-232 jack.  I think I could use a USB-to-RS232, but I'm sure I would also have to configure something.

---

### Post by ricpeterson1 on 2016-05-03
Just curious if you resolved your issue with the lockup.  I am having the same issue and thought it was tied to running multiple VMs through VM Ware, but now have had it happen when not starting a VM.  I had also suspected a memory issue, but the memtest did not find any issue after more than three passes.

---

### Post by kolibri on 2016-06-17
> **ricpeterson1 said:**
> Just curious if you resolved your issue with the lockup.  I am having the same issue and thought it was tied to running multiple VMs through VM Ware, but now have had it happen when not starting a VM.  I had also suspected a memory issue, but the memtest did not find any issue after more than three passes.

ditto (minus the VM, running processes don't seem to be relevant)

---

