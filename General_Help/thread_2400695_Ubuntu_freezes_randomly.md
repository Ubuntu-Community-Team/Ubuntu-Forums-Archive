---
title: "Ubuntu freezes randomly"
date: 2018-09-09
forum: General Help
---

### Post by 700 on 2018-09-09
PROBLEM:
Ubuntu system freezes randomly. 
Everything (except mouse cursor) gets frozen, including clock and keyboard (Caps Lock frozen, Num Lock frozen, tty terminal not available).

CONDITIONS:
- System: Ubuntu 18.04.1 LTS
- Machine: Dell Optiplex 990
- Processor: Intel Core i5-2400 CPU @ 3.10GHz × 4 
- GPU: NV106
- GNOME: 3.28.2
- OS type: 32-bit
- CPU temperature: ~50C (OK)
- Syslog output:
> Sep  7 23:17:01 ... CRON[6732]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep  7 23:25:15 ... kernel: [19122.475008] nouveau 0000:01:00.0: gr: TRAP ch 12 [003f672000 systemd-logind[795]]
Sep  7 23:25:15 ... kernel: [19122.475016] nouveau 0000:01:00.0: gr: GPC0/TPC0/TEX: 80000049
Sep  7 23:25:15 ... kernel: [19122.475024] nouveau 0000:01:00.0: fifo: read fault at 0000240000 engine 00 [GR] client 01 [GPC0/T1_0] reason 02 [PTE] on channel 12 [003f672000 systemd-logind[795]]
Sep  7 23:25:15 ... kernel: [19122.475031] nouveau 0000:01:00.0: fifo: channel 12: killed
Sep  7 23:25:15 ... kernel: [19122.475033] nouveau 0000:01:00.0: fifo: runlist 0: scheduled for recovery
Sep  7 23:25:15 ... kernel: [19122.475037] nouveau 0000:01:00.0: fifo: engine 0: scheduled for recovery
Sep  7 23:25:15 ... kernel: [19122.475042] nouveau 0000:01:00.0: systemd-logind[795]: channel 12 killed!
Sep  8 07:16:43 ... systemd-modules-load[286]: Inserted module 'lp'
Sep  8 07:16:43 ... systemd-modules-load[286]: Inserted module 'ppdev'
Sep  8 07:16:43 ... systemd[1]: Starting Flush Journal to Persistent Storage...
How to fix it, plz?

---

### Post by ludapesi on 2018-10-07
I'm looking for that issue also, I found this thread in the forum:
[https://ubuntuforums.org/showthread.php?t=2376704&highlight=nouveau+gnome-shell+killed](https://ubuntuforums.org/showthread.php?t=2376704&highlight=nouveau+gnome-shell+killed)

Maybe it solve the issue.

---

### Post by 3togo on 2018-10-07
blacklist nouveau

[https://linuxconfig.org/how-to-disable-nouveau-nvidia-driver-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-disable-nouveau-nvidia-driver-on-ubuntu-18-04-bionic-beaver-linux)

---

