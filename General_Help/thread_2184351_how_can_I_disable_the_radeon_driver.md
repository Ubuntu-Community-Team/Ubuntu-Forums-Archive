---
title: "how can I disable the radeon driver"
date: 2013-10-28
forum: General Help
---

### Post by spam2 on 2013-10-28
lspci -k:

02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti XT [Radeon HD 7970/R9 280X]
        Subsystem: Hightech Information System Ltd. Tahiti XT2 [Radeon HD 7970 GHz Edition]
        Kernel driver in use: radeon

I've added "blacklist radeon" to /etc/modprobe.d/blacklist.conf, and I've added "radeon.modeset=0" to grub, [FONT=arial][COLOR=#444444]neither works. I tried [/COLOR][/FONT]modprobe -r radeon and it tells me FATAL: Module radeon is in use.

edit: D'oh, I forgot to update grub. Problem solved.

---

