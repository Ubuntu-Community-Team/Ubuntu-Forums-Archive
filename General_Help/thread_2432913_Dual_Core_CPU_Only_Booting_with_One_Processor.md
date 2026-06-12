---
title: "Dual Core CPU Only Booting with One Processor"
date: 2019-12-10
forum: General Help
---

### Post by Infinitas on 2019-12-10
I have a dual core Intel E5200 system that is only booting with a single core. I have tried booting in grub with apci=off, but to no avail. I have also tried disabling apci in the bios, but that also did not work. Does anyone have any advice one how to remedy this situation? I'm not sure what information is pertinent to post here, and would be glad to post any additional information required.

$ uname -a
Linux wolfdale 4.4.0-170-generic #199-Ubuntu SMP Thu Nov 14 01:45:04 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

$  cat /proc/cpuinfo | grep processor | wc -l
1

$ cat /etc/issue
Ubuntu 16.04.6 LTS \n \l

$ dmesg | grep -i smp
[    0.000000] Linux version 4.4.0-170-generic (buildd@lcy01-amd64-019) (gcc version 5.4.0 20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.12) ) #199-Ubuntu SMP Thu Nov 14 01:45:04 UTC 2019 (Ubuntu 4.4.0-170.199-generic 4.4.200)
[    0.000000] smpboot: Allowing 1 CPUs, 0 hotplug CPUs
[    0.026591] Freeing SMP alternatives memory: 36K
[    0.048168] smpboot: Max logical packages: 1
[    0.048175] smpboot: weird, boot CPU (#0) not listed by the BIOS
[    0.048177] smpboot: SMP motherboard not detected
[    0.048178] smpboot: SMP disabled
[    0.265900] smpboot: Total of 1 processors activated (4999.45 BogoMIPS)

---

