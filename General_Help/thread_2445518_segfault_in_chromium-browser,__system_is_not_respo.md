---
title: "segfault in chromium-browser,  system is not responding in Kubuntu 18.04 LTS"
date: 2020-06-15
forum: General Help
---

### Post by anderbuntu on 2020-06-15
Hi



I just realized that during last week I got 3 system crashes, 
How it occurs: When I have opened multiple tabs in Chrome ( as always ) suddenly I have no response from KDE desktop, ( no response from keyboard and mouse pointer is only working but no window is responsive.
Any idea ? System also crashed today after new kernel update form yesterday.

current setup: Kubuntu 18.04 LTS
[FONT=monospace]
[COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ uname -a[/COLOR]
Linux host 5.3.0-59-generic #53~18.04.1-Ubuntu SMP Thu Jun 4 14:58:26 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux


[/FONT]
here is last logs from systemlog>

```

Jun 15 20:11:07 host PackageKit: get-updates transaction /16969_cebdddcd from uid 1000 finished with success after 838ms
Jun 15 20:11:07 host systemd-resolved[931]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Jun 15 20:14:13 host kernel: [ 2102.064620] Asynchronous wait on fence i915:kwin_x11[1749]:b358 timed out (hint:intel_atomic_commit_ready+0x0/0x54 [i915])
Jun 15 20:14:25 host kernel**: [COLOR=#ff0000][ 2113.735880] GpuWatchdog[2091]: segfault at 0 ip 00005577f1e87d09 sp 00007fb7dccd06b0 error 6 in chromium-browser[5577ec8c3000+98a3000][/COLOR]**
Jun 15 20:14:25 host kernel: [ 2113.735923] Code: 00 79 09 48 8b 7d c0 e8 e5 b0 5d fe c7 45 c0 aa aa aa aa 0f ae f0 41 8b 84 24 e0 00 00 00 89 45 c0 48 8d 7d c0 e8 67 52 a4 fe <c7> 04 25 00 00 00 00 37 13 00 00 48 83 c4 38 5b 41 5c 41 5d 41 5e
Jun 15 20:11:09 host systemd-resolved[931]: message repeated 5 times: [ Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.]
Jun 15 20:15:01 host CRON[9206]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Jun 15 20:16:12 host systemd-modules-load[451]: Inserted module 'lp'

```

[FONT=monospace]
[/FONT]

---

