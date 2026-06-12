---
title: "Ubuntu 22.04 only boots in lowlatency kernel"
date: 2023-07-26
forum: General Help
---

### Post by sharma-deepak83 on 2023-07-26
I think it is linked to NVIDIA drivers but I am not sure. I had nvidia drivers installed(not sure which one) and everything was working correctly. Since I started using zoom my system started rebooting randomly. After persistent reboots, Ubuntu decided to not use nvidia anymore which I am suspecting now may have been corrupted driver.

[LIST]
[*]I installed the driver again and after reboot got blank screen even on grub.
[*]Used live boot cd to fix the grub
[/LIST]
Now I am able to start Ubuntu only in low latency kernels, generic and regulars do not work
Any help will be appreciated on this:
Nvidia Card - GTX 1660 ti mobile Kernel: 6.2.0-1009 but only 6.2.0-1009-lowlatency works

---

### Post by DuckHook on 2023-07-26
Please use only standard styles and fonts when posting. Unusual styles and fonts make your posts hard to read on some monitors and portable devices.

---

