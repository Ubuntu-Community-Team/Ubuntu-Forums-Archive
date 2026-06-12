---
title: "Ubuntu 14.04 can't boot when I boot with an older Linux kernel"
date: 2015-05-20
forum: General Help
---

### Post by icoming on 2015-05-20
Hello,

I install Ubuntu 14.04 server version in my machine. It boots fine when I use the default kernel. I would like to try kernel v3.13.0, so I installed the kernel image from the Ubuntu repository. When the machine boots, it complains that it can't find /dev/mapper/fg1--vg-root and falls into a very simple shell.
The original kernel (v3.16.0) uses /dev/mapper/fg1--vg-root to boot and it works fine.
The root filesystem is EXT4. I checked the config of the kernel v3.13.0 and EXT4 is compiled into the kernel, instead of being built as a module.
I'm not familiar with the root filesystem setup. Could any one tell what are the possible reasons that the kernel v3.13.0 can't find /dev/mapper/fg1--vg-root?

Thanks,
Da

---

