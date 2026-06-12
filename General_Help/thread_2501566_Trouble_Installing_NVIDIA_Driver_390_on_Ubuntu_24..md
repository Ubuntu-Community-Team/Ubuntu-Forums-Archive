---
title: "Trouble Installing NVIDIA Driver 390 on Ubuntu 24.04.1 LTS for Quadro 2000"
date: 2024-10-13
forum: General Help
---

### Post by yousefosama on 2024-10-13
Hi everyone,
I'm currently running **Ubuntu 24.04.1 LTS**, and I'm having trouble installing the recommended NVIDIA driver for my _Quadro 2000_ graphics card (**nvidia-driver-390**). The driver doesn't show up in the Additional Drivers app by default.

I tried adding the **ppa:kelebek333/nvidia-legacy** repository, which listed both drivers 340 and 390 in the Additional Drivers section. After installing nvidia-driver-390 and restarting, I encountered a black screen with a blinking cursor after the Ubuntu logo.

Previously, on older Linux distros with older kernels (around version 5.x), nvidia-driver-390 worked fine, and the driver appeared as the recommended one without needing to add extra repositories.

Any advice on resolving this issue would be greatly appreciated. Should I provide any additional system information to help diagnose the problem?

---

### Post by Bashing-om on 2024-10-13
Hello yousefosama - Welcome to the Forums :D

I be that barer of ill news.

Nvidia version 390 is no longer supported: 
[http://nvidia.custhelp.com/app/answers/detail/a_id/3142/~/support-timeframes-for-unix-legacy-gpu-releases](http://nvidia.custhelp.com/app/answers/detail/a_id/3142/~/support-timeframes-for-unix-legacy-gpu-releases)
Our last release to support that driver was 22.04.

At this point the open source nouveau driver is what is available.
If you are not doing intensive gaming should workie fine.

[INDENT]nothing lasts forever
[/INDENT]

---

