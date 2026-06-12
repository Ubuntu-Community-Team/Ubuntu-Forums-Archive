---
title: "New Ubuntu install, system randomly rebooted"
date: 2014-11-09
forum: General Help
---

### Post by sam103 on 2014-11-09
I installed Ubuntu after several BSODs on Windows 7. Everything was going swimminly when, all of a sudden, my monitors went black and my computer restarted. After I entered my crypto key, it said something about verifying disk integrity or something. I rebooted and checked out some log files, and kern.log has a particularly terrifying block of red zeros. Not sure if that has anything to do with it. It seems like the reboot happened right after these red zeros (EDIT: It was minutes after, so likely irrelevant).

EDIT: It happened again, and the message on reboot is "checking disk drives for errors" and it only takes seconds. Both times it happened while either seconds into playing a youtube video or starting a game. This time around, all logs just show the normal startup procedure as before. How can I diagnose this problem? 


```
Nov  9 00:12:01 QUANTUM-PC kernel: [ 6595.847753] sd 7:0:0:0: [sdc] Assuming drive cache: write throughNov  9 00:12:01 QUANTUM-PC kernel: [ 6595.847761] sd 7:0:0:0: [sdc] Attached SCSI disk
Nov  9 00:12:02 QUANTUM-PC kernel: [ 6596.792680] EXT4-fs (sdc2): recovery complete
Nov  9 00:12:02 QUANTUM-PC kernel: [ 6596.793900] EXT4-fs (sdc2): mounted filesystem with ordered data mode. Opts: (null)
Nov  9 00:12:20 QUANTUM-PC kernel: [ 6614.728532] usb 1-2.4: USB disconnect, device number 5
Nov  9 00:12:20 QUANTUM-PC kernel: [ 6614.759867] Buffer I/O error on device sdc2, logical block 5799936
Nov  9 00:12:20 QUANTUM-PC kernel: [ 6614.759870] lost page write due to I/O error on sdc2
Nov  9 00:12:20 QUANTUM-PC kernel: [ 6614.759872] JBD2: Error -5 detected when updating journal superblock for sdc2-8.
\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00Nov  9 00:16:57 QUANTUM-PC kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov  9 00:16:57 QUANTUM-PC kernel: [    0.000000] Initializing cgroup subsys cpu
Nov  9 00:16:57 QUANTUM-PC kernel: [    0.000000] Initializing cgroup subsys cpuacct
Nov  9 00:16:57 QUANTUM-PC kernel: [    0.000000] Linux version 3.13.0-39-generic (buildd@toyol) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #66-Ubuntu SMP Tue Oct 28 13:30:27 UTC 2014 (Ubuntu 3.13.0-39.66-generic 3.13.11.8)
Nov  9 00:16:57 QUANTUM-PC kernel: [    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.13.0-39-generic root=/dev/mapper/ubuntu--vg-root ro quiet splash
Nov  9 00:16:57 QUANTUM-PC kernel: [    0.000000] KERNEL supported cpus:
Nov  9 00:16:57 QUANTUM-PC kernel: [    0.000000]   Intel GenuineIntel
Nov  9 00:16:57 QUANTUM-PC kernel: [    0.000000]   AMD AuthenticAMD
Nov  9 00:16:57 QUANTUM-PC kernel: [    0.000000]   Centaur CentaurHauls
Nov  9 00:16:57 QUANTUM-PC kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Nov  9 00:16:57 QUANTUM-PC kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
Nov  9 00:16:57 QUANTUM-PC kernel: [    0.000000] BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
Nov  9 00:16:57 QUANTUM-PC kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e6000-0x00000000000fffff] reserved
Nov  9 00:16:57 QUANTUM-PC kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000cff9ffff] usable
Nov  9 00:16:57 QUANTUM-PC kernel: [    0.000000] BIOS-e820: [mem 0x00000000cffa0000-0x00000000cffaffff] ACPI data
Nov  9 00:16:57 QUANTUM-PC kernel: [    0.000000] BIOS-e820: [mem 0x00000000cffb0000-0x00000000cffdffff] ACPI NVS
Nov  9 00:16:57 QUANTUM-PC kernel: [    0.000000] BIOS-e820: [mem 0x00000000cffe0000-0x00000000cfffffff] reserved
Nov  9 00:16:57 QUANTUM-PC kernel: [    0.000000] BIOS-e820: [mem 0x00000000fff00000-0x00000000ffffffff] reserved
Nov  9 00:16:57 QUANTUM-PC kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000022fffffff] usable
Nov  9 00:16:57 QUANTUM-PC kernel: [    0.000000] NX (Execute Disable) protection: active
Nov  9 00:16:57 QUANTUM-PC kernel: [    0.000000] SMBIOS 2.6 present.
Nov  9 00:16:57 QUANTUM-PC kernel: [    0.000000] DMI: To Be Filled By O.E.M. To Be Filled By O.E.M./880GM-LE, BIOS P1.40 02/18/2011
Nov  9 00:16:57 QUANTUM-PC kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Nov  9 00:16:57 QUANTUM-PC kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Nov  9 00:16:57 QUANTUM-PC kernel: [    0.000000] No AGP bridge found
Nov  9 00:16:57 QUANTUM-PC kernel: [    0.000000] e820: last_pfn = 0x230000 max_arch_pfn = 0x400000000
Nov  9 00:16:57 QUANTUM-PC kernel: [    0.000000] MTRR default type: uncachable
```

---

### Post by Ubi_one_2014 on 2014-11-09
looks like a hardware failure

my first idea is to replace the HD with a new one, however, maybe there are better answers from other users

---

