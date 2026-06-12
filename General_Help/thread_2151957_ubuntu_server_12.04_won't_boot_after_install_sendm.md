---
title: "ubuntu server 12.04 won't boot after install sendmail"
date: 2013-06-06
forum: General Help
---

### Post by ScottWerkema on 2013-06-06
I have (had) a ubuntu server running as a virtual machine on a Xen server. It is configured as a LAMP stack to host several little php web apps for internal use. Yesterday I installed sendmail with apt-get. The install seemed to go fine, until I rebooted. The system never rebooted. It goes black right after the BIOS splash screen. The last thing displayed on the BIOS screen is "grub loading." Once the screen goes black Xen indicates the guest machine has consumed all RAM (1024MB) and is using 100% of the two CPU cores it has assigned.

I have tried searching forms high and low and have tried many suggestions. I have also deleted all entries to start sendmail during boot.

Any suggestions on what may have gone wrong would be appreciated.

---

