---
title: "System fails to start and goes to maintenance mode"
date: 2024-05-28
forum: General Help
---

### Post by rogerdv2 on 2024-05-28
A couple of days ago, suddenly my system started to put the filesystem in read only mode. The file browser displayed some error on top saying there was a problem with miniature cache, and I couldnt do anything. I was using Ubuntu Cinnamon, which worked without any significant problems for the last 8-9 months. After a few restarts, the system no longer started anymore, it went to maintenance mode. Running journalctl -xb like the prompt says gives me a long, long log, where the only thing relatively similar to an error was somethe lines saying File System check on Root Device was skipped because an unmet condition. Thre is another line saying Plataform Persistent Storage was skipped for the same reason, and another saying Repartition Root Disk was skipped because no trigger condition checks were met.
I booted with SysRescueCD and confirmed my home partition was there and the info seems to be safe. Decided to install Ubuntu 24.04 and found that installation wizard crashes 9 of 10 times. At any random step. Could be after choosing language, before repartition, or while installing. Booted again with SysRescueCD, removed my old boot and root partitions, and created a single one. Told the installer to use that already created partition for / and I managed to install, but again, it sends me directly to maintenance mode.
Any idea about what can be happening here and how to solve it? My boot device is an M2 disk, which already contains Windows (working fine), and 2 hard drives, one of them containing my home partition.

---

