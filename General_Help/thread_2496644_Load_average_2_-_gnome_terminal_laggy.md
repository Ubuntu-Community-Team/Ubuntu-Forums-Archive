---
title: "Load average 2 - gnome terminal laggy"
date: 2024-04-06
forum: General Help
---

### Post by elfejoyeux2 on 2024-04-06
Hello,

I recently saw my computer always has a minimal load average of 2. Also, when using gnome terminal, everything seems laggy: when typing on my keyboard, the letters appear sometimes a second after. I'm not talking about network problems: the lag appears locally. I just open a gnome terminal and type some letters. When executing things, they are as fast as usual, it's just the display in gnome terminal that is slow. Every other application is as fast as always: firefox, evolution, Steam games…

Here is the config:
- Gigabyte Technology Co., Ltd. B550 GAMING X V2/B550 GAMING X V2 (BIOS F18)
- AMD Ryzen 5 5600X 6-Core Processor
- 32GB ram
- Samsung SSD 980 1TB NVME
- NVIDIA GeForce RTX 3060 Ti (Driver Version: 545.29.06)

Ubuntu 20.04, up to date, with ubuntu pro activated.
Kernel: 6.5.0-26-generic

Everything has worked like a charm for about 2 years.

Here is what I tested:
- glmark2 Score: 18049
- no error in smartctl
- md5sum of big files (>80GB) is consistent
- I just updated the bios to the latest available version
- no process is using a lot of CPU, no process is using a lot of RAM
- I tried an other terminal: xterm is not lagging at all
- I tried rebooting and not logging graphically. I went to the second tty (ctrl-alt-F2) and logged in CLI: it's not laggy at all, but the load average is at 2.

There are some red lines in dmesg:
[    7.056360] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  545.29.06  Thu Nov 16 01:59:08 UTC 2023
[    7.708123] sd 6:0:0:0: [sda] Asking for cache data failed
[   18.608374] kvm_amd: SVM disabled (by BIOS) in MSR_VM_CR on CPU 3
[   20.978868] usb 3-2.4.2: clock source 41 is not valid, cannot use
[   21.875131] [drm:nv_drm_master_set [nvidia_drm]] *ERROR* [nvidia-drm] [GPU ID 0x00000500] Failed to grab modeset ownership

I welcome any ideas :)

---

### Post by elfejoyeux2 on 2024-04-09
I resolved the 2 issues, which happen to be 2 completely different bugs.

1 - I de-activated autotrim on my 2 zfs pools. Bug fixed here : [https://github.com/openzfs/zfs/pull/15781](https://github.com/openzfs/zfs/pull/15781)

2 - there is a bug in mutter, which makes gnome terminal laggy. Explanation : [https://askubuntu.com/questions/1509058/input-delay-on-terminal-ubuntu-22-04-4/1509474#1509474](https://askubuntu.com/questions/1509058/input-delay-on-terminal-ubuntu-22-04-4/1509474#1509474)

---

### Post by racingronnie on 2024-04-12
Ubuntu 23.10; 32GB RAM;  i5-12600K
Thanks for the link to fix the lagging terminal!  The bug in mutter was my problem!

---

