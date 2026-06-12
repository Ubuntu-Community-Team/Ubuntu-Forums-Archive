---
title: "Restart om power failure"
date: 2013-04-14
forum: General Help
---

### Post by patdundee on 2013-04-14
Hi Guys

UBUNTU 12.10 Server

My servers are set to restart on a power failure. When this happens some of them restart without any issue, but others load with the Linux version screen and do not start until I put a monitor on them and select the version to load. 

My questions is, How can i tell Ubuntu to always restart with the latest install Linux version. Thus ensuring they always start back up.

Many thanks

---

### Post by Impavidus on 2013-04-14
Sounds like all machines are powered up, in all cases the bios loads the boot loader, but on some machines the boot loader doesn't load the OS. Have you compared the grub configuration on those machines? Should be in /etc/default/grub. Make sure it is set to boot a kernel automatically, not wait an infinite time.

---

