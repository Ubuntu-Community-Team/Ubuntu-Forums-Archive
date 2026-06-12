---
title: "Cannot install VMware Workstation 7.1.0 on Ubuntu 12.04"
date: 2013-05-26
forum: General Help
---

### Post by astroids on 2013-05-26
Hi All,

I am newbie on Ubuntu. I upgrade Ubuntu 10.04 to 12.04 by using Update Manager and my VMware Workstation doesn't work anymore. I've got lots of errors and I try to follow direction from ubuntu forums for endless hours.
I even try to re-install VMware-Workstation-Full-7.1.0-261024.x86_64.bundle and I get now the following error " VMware installer-> "root access is required for the operation you have chosen". Also before that I've got during VMware Kernel Module Updater the following error "Unable to build kernel module"-> "See log file /tmp/vmware-root/setup-log25321.

I am wondering if anyone had this issue and can help.

Thanks a lot in advance.

Astroids

see bellow:

Setup-2532log:
============                                                                                                                                                                                                                                                                                                                                                                                                                   

May 26 10:53:22.697: app-140409689147136| Log for VMware Workstation pid=2532 version=7.1.0 build=build-261024 option=Release
May 26 10:53:22.697: app-140409689147136| The process is 64-bit.
May 26 10:53:22.697: app-140409689147136| Host codepage=UTF-8 encoding=UTF-8
May 26 10:53:22.697: app-140409689147136| Logging to /tmp/vmware-root/setup-2532.log
May 26 10:53:22.796: app-140409689147136| modconf query interface initialized
May 26 10:53:22.797: app-140409689147136| modconf library initialized
May 26 10:53:22.814: app-140409689147136| Your GCC version: 4.6
May 26 10:53:22.818: app-140409689147136| Your GCC version: 4.6
May 26 10:53:22.823: app-140409689147136| Your GCC version: 4.6
May 26 10:53:22.842: app-140409689147136| Your GCC version: 4.6
May 26 10:53:22.847: app-140409689147136| Your GCC version: 4.6
May 26 10:53:22.876: app-140409689147136| Trying to find a suitable PBM set for kernel 3.2.0-44-generic.
May 26 10:53:22.878: app-140409689147136| Trying to find a suitable PBM set for kernel 3.2.0-44-generic.
May 26 10:53:22.880: app-140409689147136| Trying to find a suitable PBM set for kernel 3.2.0-44-generic.
May 26 10:53:22.882: app-140409689147136| Trying to find a suitable PBM set for kernel 3.2.0-44-generic.
May 26 10:53:22.884: app-140409689147136| Trying to find a suitable PBM set for kernel 3.2.0-44-generic.
May 26 10:53:22.893: app-140409689147136| Trying to find a suitable PBM set for kernel 3.2.0-44-generic.
May 26 10:53:22.895: app-140409689147136| Trying to find a suitable PBM set for kernel 3.2.0-44-generic.
May 26 10:53:22.897: app-140409689147136| Trying to find a suitable PBM set for kernel 3.2.0-44-generic.
May 26 10:53:22.899: app-140409689147136| Trying to find a suitable PBM set for kernel 3.2.0-44-generic.
May 26 10:53:22.901: app-140409689147136| Trying to find a suitable PBM set for kernel 3.2.0-44-generic.
May 26 10:53:22.904: app-140409689147136| Your GCC version: 4.6
May 26 10:53:22.909: app-140409689147136| Your GCC version: 4.6
May 26 10:53:22.939: app-140409689147136| Trying to find a suitable PBM set for kernel 3.2.0-44-generic.
May 26 10:53:22.941: app-140409689147136| Trying to find a suitable PBM set for kernel 3.2.0-44-generic.
May 26 10:53:22.943: app-140409689147136| Trying to find a suitable PBM set for kernel 3.2.0-44-generic.
May 26 10:53:22.945: app-140409689147136| Trying to find a suitable PBM set for kernel 3.2.0-44-generic.
May 26 10:53:22.947: app-140409689147136| Trying to find a suitable PBM set for kernel 3.2.0-44-generic.
May 26 10:53:22.949: app-140409689147136| Your GCC version: 4.6
May 26 10:53:22.954: app-140409689147136| Your GCC version: 4.6
May 26 10:53:22.990: app-140409689147136| Trying to find a suitable PBM set for kernel 3.2.0-44-generic.
May 26 10:53:22.992: app-140409689147136| Trying to find a suitable PBM set for kernel 3.2.0-44-generic.
May 26 10:53:22.994: app-140409689147136| Trying to find a suitable PBM set for kernel 3.2.0-44-generic.
May 26 10:53:22.996: app-140409689147136| Trying to find a suitable PBM set for kernel 3.2.0-44-generic.
May 26 10:53:22.998: app-140409689147136| Trying to find a suitable PBM set for kernel 3.2.0-44-generic.
May 26 10:53:23.295: app-140409689147136| Trying to find a suitable PBM set for kernel 3.2.0-44-generic.
May 26 10:53:23.295: app-140409689147136| Building module vmmon.
May 26 10:53:23.314: app-140409689147136| Extracting the sources of the vmmon module.
May 26 10:53:23.366: app-140409689147136| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-44-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
May 26 10:53:26.681: app-140409689147136| Failed to compile module vmmon!

---

