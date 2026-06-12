---
title: "Nvidia overwritten at boot"
date: 2007-03-28
forum: General Help
---

### Post by phoebus_ on 2007-03-28
Hi guys,

EX debian user gere, I like ubuntu, bit this is driving me crazy- I installed "ubuntu" nvidia-glx drivers and they didn't work well so I downloaded Nvidia drivers from [www.nvidia.com](www.nvidia.com), installed them and it works perfectly OK.
BUT! When I reboot, something overwrites / deletes nvidia.ko from modules directory so X doesn't load. I have to run nVidia installer again to write the module once more.

I removed nvidia* from /etc/init.d but it doesn't help. So; how can I make it NOT overwrite nvidia's module from kernel modules?

---

### Post by Magnes on 2007-03-28
It should not do that. Maybe you didn't uninstall nvidia-glx first? Before instaling the ones from nvidia.com?

---

