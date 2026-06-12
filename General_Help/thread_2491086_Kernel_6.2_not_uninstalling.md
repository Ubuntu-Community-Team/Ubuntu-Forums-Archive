---
title: "Kernel 6.2 not uninstalling"
date: 2023-09-25
forum: General Help
---

### Post by binaryist.com on 2023-09-25
**Current kernel installs.**
# dpkg --list | egrep 'linux-image|linux-headers'
ii  linux-headers-5.15.0-84                    5.15.0-84.93                                all          Header files related to Linux kernel version 5.15.0
ii  linux-headers-5.15.0-84-generic            5.15.0-84.93                                amd64        Linux kernel headers for version 5.15.0 on 64 bit x86 SMP
ii  linux-headers-6.2.0-33-generic             6.2.0-33.33~22.04.1                         amd64        Linux kernel headers for version 6.2.0 on 64 bit x86 SMP
ii  linux-headers-generic                      5.15.0.84.81                                amd64        Generic Linux kernel headers
ii  linux-headers-generic-hwe-22.04            6.2.0.33.33~22.04.10                        amd64        Generic Linux kernel headers
ii  linux-image-5.15.0-84-generic              5.15.0-84.93                                amd64        Signed kernel image generic
ii  linux-image-6.2.0-33-generic               6.2.0-33.33~22.04.1                         amd64        Signed kernel image generic
ii  linux-image-generic                        5.15.0.84.81                                amd64        Generic Linux kernel image
ii  linux-image-generic-hwe-22.04              6.2.0.33.33~22.04.10                        amd64        Generic Linux kernel image

**Try to remove hwe kernel.**
apt purge linux-hwe-6.2-headers-6.2.0-33 
The following package was automatically installed and is no longer required:
  linux-image-generic-hwe-22.04
The following packages will be REMOVED:
  linux-generic-hwe-22.04* linux-headers-6.2.0-33-generic* linux-headers-generic-hwe-22.04* linux-hwe-6.2-headers-6.2.0-33*
Removing linux-generic-hwe-22.04 (6.2.0.33.33~22.04.10) ...
Removing linux-headers-generic-hwe-22.04 (6.2.0.33.33~22.04.10) ...
Removing linux-headers-6.2.0-33-generic (6.2.0-33.33~22.04.1) ...
Removing linux-hwe-6.2-headers-6.2.0-33 (6.2.0-33.33~22.04.1) ...

# apt autoremove --purge
Removing linux-image-generic-hwe-22.04 (6.2.0.33.33~22.04.10) ...

**However, linux-image-6.2.0-33-generic is not removed.**
# sudo dpkg --list | egrep 'linux-image|linux-headers'
ii  linux-headers-5.15.0-84                    5.15.0-84.93                                all          Header files related to Linux kernel version 5.15.0
ii  linux-headers-5.15.0-84-generic            5.15.0-84.93                                amd64        Linux kernel headers for version 5.15.0 on 64 bit x86 SMP
ii  linux-headers-generic                      5.15.0.84.81                                amd64        Generic Linux kernel headers
ii  linux-image-5.15.0-84-generic              5.15.0-84.93                                amd64        Signed kernel image generic
ii  linux-image-6.2.0-33-generic               6.2.0-33.33~22.04.1                         amd64        Signed kernel image generic
ii  linux-image-generic                        5.15.0.84.81                                amd64        Generic Linux kernel image

[B]And when I try to remove kernel manually it tries to load the unsigned version.
[/B]# apt purge linux-image-6.2.0-33-generic 
The following packages will be REMOVED:
  linux-image-6.2.0-33-generic* linux-modules-ivsc-6.2.0-33-generic* linux-modules-ivsc-generic-hwe-22.04*
The following NEW packages will be installed:
  linux-image-unsigned-6.2.0-33-generic
[B]
I have been down the dependency rabbit hole, except the remaining are all dependencies to 5.15 kernel. Boot still defaults to 6.2, except that it now crashes. I need to return to 5.15 as default kernel as the 6.2 freezes temporary random (CPU race?), in addition I would like to use my ubuntu pro subscription.

Thanks.[/B]

---

### Post by MAFoElffen on 2023-09-25
Try this first:

Ensure that you are booted from a 5 series kernel first, then do
```

sudo apt install --reinstall --install-recommends linux-generic
sudo apt remove --purge linux-generic-hwe-22.04 linux-image-6.2.0-3*-generic* linux-modules*-6.2.0-3*-generic* linux-headers-6.2.0-3*-generic linux-modules*-generic-hwe-22.04*

```

---

