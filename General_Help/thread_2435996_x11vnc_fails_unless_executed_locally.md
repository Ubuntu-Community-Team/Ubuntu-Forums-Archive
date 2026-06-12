---
title: "x11vnc fails unless executed locally"
date: 2020-01-29
forum: General Help
---

### Post by nwsaia on 2020-01-29
OS: Ubuntu 18.04.3 LTS x86_64
Host: Precision WorkStation T3500
Kernel: 5.3.0-28-generic
Uptime: 2 hours, 49 mins
Packages: 1604
Shell: bash 4.4.20
Terminal: /dev/pts/0
CPU: Intel Xeon X5650 (12) @ 2.661GH
GPU: NVIDIA Quadro K600
Memory: 1082MiB / 11973MiB

If I sit down at the physical machine, open Terminal and run x11vnc, it works.

If I launch x11vnc via ssh session or as a systemd service, it fails with [B]XOpenDisplay(":0") failed.
[/B]
I tried the nouveau driver with identical results.

**Edit** I needed to specify display 1, not display 0.

---

### Post by nwsaia on 2020-01-29
I believe it could be the same bug as this: [https://ubuntuforums.org/showthread.php?t=2428787&p=13895331#post13895331](https://ubuntuforums.org/showthread.php?t=2428787&p=13895331#post13895331)

---

