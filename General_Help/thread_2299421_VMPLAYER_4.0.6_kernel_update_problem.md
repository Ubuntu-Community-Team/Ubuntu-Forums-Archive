---
title: "VMPLAYER_4.0.6_kernel_update_problem"
date: 2015-10-18
forum: General Help
---

### Post by vladkac on 2015-10-18
H guys,

I have installed VMPlayer 4.0.6 and during kernel module update several errors occured. 
May somebody have a look and give me an advice ?
Thanks in advance.

```
2015-10-18T14:50:20.861+01:00| vthread-3| I120: Log for VMware Workstation pid=4645 version=8.0.6 build=build-1035888 option=Release
2015-10-18T14:50:20.861+01:00| vthread-3| I120: The process is 32-bit.
2015-10-18T14:50:20.861+01:00| vthread-3| I120: Host codepage=UTF-8 encoding=UTF-8
2015-10-18T14:50:20.861+01:00| vthread-3| I120: Host is Linux 3.19.0-30-generic Ubuntu 15.04
2015-10-18T14:50:20.860+01:00| vthread-3| I120: Msg_Reset:
2015-10-18T14:50:20.860+01:00| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/usr/lib/vmware/settings": No such file or directory.
2015-10-18T14:50:20.860+01:00| vthread-3| I120: ----------------------------------------
2015-10-18T14:50:20.860+01:00| vthread-3| I120: PREF Optional preferences file not found at /usr/lib/vmware/settings. Using default values.
2015-10-18T14:50:20.860+01:00| vthread-3| I120: Msg_Reset:
2015-10-18T14:50:20.860+01:00| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/root/.vmware/config": No such file or directory.
2015-10-18T14:50:20.860+01:00| vthread-3| I120: ----------------------------------------
2015-10-18T14:50:20.860+01:00| vthread-3| I120: PREF Optional preferences file not found at /root/.vmware/config. Using default values.
2015-10-18T14:50:20.860+01:00| vthread-3| I120: Msg_Reset:
2015-10-18T14:50:20.860+01:00| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/root/.vmware/preferences": No such file or directory.
2015-10-18T14:50:20.860+01:00| vthread-3| I120: ----------------------------------------
2015-10-18T14:50:20.860+01:00| vthread-3| I120: PREF Failed to load user preferences.
2015-10-18T14:50:20.861+01:00| vthread-3| W110: Logging to /tmp/vmware-root-2231943548/modconfig-4645.log
2015-10-18T14:50:21.101+01:00| vthread-3| I120: modconf query interface initialized
2015-10-18T14:50:21.101+01:00| vthread-3| I120: modconf library initialized
2015-10-18T14:50:21.144+01:00| vthread-3| I120: Your GCC version: 4.9
2015-10-18T14:50:21.150+01:00| vthread-3| I120: Validating path /lib/modules/preferred/build/include for kernel release 3.19.0-30-generic
2015-10-18T14:50:21.150+01:00| vthread-3| I120: Failed to find /lib/modules/preferred/build/include/linux/version.h
2015-10-18T14:50:21.150+01:00| vthread-3| I120: Failed version test: /lib/modules/preferred/build/include/linux/version.h not found.
2015-10-18T14:50:21.150+01:00| vthread-3| I120: Validating path /lib/modules/3.19.0-30-generic/build/include for kernel release 3.19.0-30-generic
2015-10-18T14:50:21.153+01:00| vthread-3| I120: Your GCC version: 4.9
2015-10-18T14:50:21.167+01:00| vthread-3| I120: Your GCC version: 4.9
2015-10-18T14:50:21.189+01:00| vthread-3| I120: Header path /lib/modules/3.19.0-30-generic/build/include for kernel release 3.19.0-30-generic is valid.
2015-10-18T14:50:21.189+01:00| vthread-3| I120: Validating path /lib/modules/3.19.0-30-generic/build/include for kernel release 3.19.0-30-generic
2015-10-18T14:50:21.193+01:00| vthread-3| I120: Your GCC version: 4.9
2015-10-18T14:50:21.207+01:00| vthread-3| I120: Your GCC version: 4.9
2015-10-18T14:50:21.226+01:00| vthread-3| I120: Header path /lib/modules/3.19.0-30-generic/build/include for kernel release 3.19.0-30-generic is valid.
2015-10-18T14:50:21.253+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.19.0-30-generic.
2015-10-18T14:50:21.256+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.19.0-30-generic.
2015-10-18T14:50:21.260+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.19.0-30-generic.
2015-10-18T14:50:21.263+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.19.0-30-generic.
2015-10-18T14:50:21.266+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.19.0-30-generic.
2015-10-18T14:50:21.291+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.19.0-30-generic.
2015-10-18T14:50:21.295+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.19.0-30-generic.
2015-10-18T14:50:21.299+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.19.0-30-generic.
2015-10-18T14:50:21.303+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.19.0-30-generic.
2015-10-18T14:50:21.306+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.19.0-30-generic.
2015-10-18T14:50:21.310+01:00| vthread-3| I120: Validating path /lib/modules/preferred/build/include for kernel release 3.19.0-30-generic
2015-10-18T14:50:21.310+01:00| vthread-3| I120: Failed to find /lib/modules/preferred/build/include/linux/version.h
2015-10-18T14:50:21.310+01:00| vthread-3| I120: Failed version test: /lib/modules/preferred/build/include/linux/version.h not found.
2015-10-18T14:50:21.310+01:00| vthread-3| I120: Validating path /lib/modules/3.19.0-30-generic/build/include for kernel release 3.19.0-30-generic
2015-10-18T14:50:21.313+01:00| vthread-3| I120: Your GCC version: 4.9
2015-10-18T14:50:21.329+01:00| vthread-3| I120: Your GCC version: 4.9
2015-10-18T14:50:21.350+01:00| vthread-3| I120: Header path /lib/modules/3.19.0-30-generic/build/include for kernel release 3.19.0-30-generic is valid.
2015-10-18T14:50:21.379+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.19.0-30-generic.
2015-10-18T14:50:21.382+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.19.0-30-generic.
2015-10-18T14:50:21.386+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.19.0-30-generic.
2015-10-18T14:50:21.389+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.19.0-30-generic.
2015-10-18T14:50:21.393+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.19.0-30-generic.
2015-10-18T14:50:21.396+01:00| vthread-3| I120: Validating path /lib/modules/preferred/build/include for kernel release 3.19.0-30-generic
2015-10-18T14:50:21.396+01:00| vthread-3| I120: Failed to find /lib/modules/preferred/build/include/linux/version.h
2015-10-18T14:50:21.396+01:00| vthread-3| I120: Failed version test: /lib/modules/preferred/build/include/linux/version.h not found.
2015-10-18T14:50:21.396+01:00| vthread-3| I120: Validating path /lib/modules/3.19.0-30-generic/build/include for kernel release 3.19.0-30-generic
2015-10-18T14:50:21.400+01:00| vthread-3| I120: Your GCC version: 4.9
2015-10-18T14:50:21.416+01:00| vthread-3| I120: Your GCC version: 4.9
2015-10-18T14:50:21.436+01:00| vthread-3| I120: Header path /lib/modules/3.19.0-30-generic/build/include for kernel release 3.19.0-30-generic is valid.
2015-10-18T14:50:21.489+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.19.0-30-generic.
2015-10-18T14:50:21.493+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.19.0-30-generic.
2015-10-18T14:50:21.497+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.19.0-30-generic.
2015-10-18T14:50:21.501+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.19.0-30-generic.
2015-10-18T14:50:21.504+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.19.0-30-generic.
2015-10-18T14:50:21.807+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.19.0-30-generic.
2015-10-18T14:50:21.808+01:00| vthread-3| I120: Validating path /lib/modules/3.19.0-30-generic/build/include for kernel release 3.19.0-30-generic
2015-10-18T14:50:21.812+01:00| vthread-3| I120: Your GCC version: 4.9
2015-10-18T14:50:21.829+01:00| vthread-3| I120: Your GCC version: 4.9
2015-10-18T14:50:21.849+01:00| vthread-3| I120: Header path /lib/modules/3.19.0-30-generic/build/include for kernel release 3.19.0-30-generic is valid.
2015-10-18T14:50:21.849+01:00| vthread-3| I120: Building module vmmon.
2015-10-18T14:50:21.849+01:00| vthread-3| I120: Extracting the sources of the vmmon module.
2015-10-18T14:50:21.867+01:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root-2231943548/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.19.0-30-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.9.2
2015-10-18T14:50:41.045+01:00| vthread-3| I120: Installing module vmmon from /tmp/vmware-root-2231943548/modules/vmmon.o to /lib/modules/3.19.0-30-generic/misc.
2015-10-18T14:50:41.045+01:00| vthread-3| I120: Registering file: /usr/lib/vmware-installer/2.0/vmware-installer --register-file vmware-vmx regular /lib/modules/3.19.0-30-generic/misc/vmmon.ko
2015-10-18T14:50:42.395+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.19.0-30-generic.
2015-10-18T14:50:42.395+01:00| vthread-3| I120: Validating path /lib/modules/3.19.0-30-generic/build/include for kernel release 3.19.0-30-generic
2015-10-18T14:50:42.399+01:00| vthread-3| I120: Your GCC version: 4.9
2015-10-18T14:50:42.413+01:00| vthread-3| I120: Your GCC version: 4.9
2015-10-18T14:50:42.433+01:00| vthread-3| I120: Header path /lib/modules/3.19.0-30-generic/build/include for kernel release 3.19.0-30-generic is valid.
2015-10-18T14:50:42.433+01:00| vthread-3| I120: Building module vmnet.
2015-10-18T14:50:42.433+01:00| vthread-3| I120: Extracting the sources of the vmnet module.
2015-10-18T14:50:42.455+01:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root-2231943548/modules/vmnet-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.19.0-30-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.9.2
2015-10-18T14:51:25.558+01:00| vthread-3| I120: Failed to compile module vmnet!
2015-10-18T14:51:25.568+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.19.0-30-generic.
2015-10-18T14:51:25.568+01:00| vthread-3| I120: Validating path /lib/modules/3.19.0-30-generic/build/include for kernel release 3.19.0-30-generic
2015-10-18T14:51:25.572+01:00| vthread-3| I120: Your GCC version: 4.9
2015-10-18T14:51:25.590+01:00| vthread-3| I120: Your GCC version: 4.9
2015-10-18T14:51:25.610+01:00| vthread-3| I120: Header path /lib/modules/3.19.0-30-generic/build/include for kernel release 3.19.0-30-generic is valid.
2015-10-18T14:51:25.610+01:00| vthread-3| I120: Building module vmblock.
2015-10-18T14:51:25.610+01:00| vthread-3| I120: Extracting the sources of the vmblock module.
2015-10-18T14:51:25.625+01:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root-2231943548/modules/vmblock-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.19.0-30-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.9.2
2015-10-18T14:51:42.404+01:00| vthread-3| I120: Failed to compile module vmblock!
2015-10-18T14:51:42.413+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.19.0-30-generic.
2015-10-18T14:51:42.413+01:00| vthread-3| I120: Validating path /lib/modules/3.19.0-30-generic/build/include for kernel release 3.19.0-30-generic
2015-10-18T14:51:42.417+01:00| vthread-3| I120: Your GCC version: 4.9
2015-10-18T14:51:42.433+01:00| vthread-3| I120: Your GCC version: 4.9
2015-10-18T14:51:42.454+01:00| vthread-3| I120: Header path /lib/modules/3.19.0-30-generic/build/include for kernel release 3.19.0-30-generic is valid.
2015-10-18T14:51:42.454+01:00| vthread-3| I120: Building module vmci.
2015-10-18T14:51:42.454+01:00| vthread-3| I120: Extracting the sources of the vmci module.
2015-10-18T14:51:42.472+01:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root-2231943548/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.19.0-30-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.9.2
2015-10-18T14:52:26.813+01:00| vthread-3| I120: Failed to compile module vmci!
2015-10-18T14:52:26.821+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.19.0-30-generic.
2015-10-18T14:52:26.821+01:00| vthread-3| I120: Validating path /lib/modules/3.19.0-30-generic/build/include for kernel release 3.19.0-30-generic
2015-10-18T14:52:26.825+01:00| vthread-3| I120: Your GCC version: 4.9
2015-10-18T14:52:26.841+01:00| vthread-3| I120: Your GCC version: 4.9
2015-10-18T14:52:26.861+01:00| vthread-3| I120: Header path /lib/modules/3.19.0-30-generic/build/include for kernel release 3.19.0-30-generic is valid.
2015-10-18T14:52:26.861+01:00| vthread-3| I120: Building module vmci.
2015-10-18T14:52:26.861+01:00| vthread-3| I120: Extracting the sources of the vmci module.
2015-10-18T14:52:26.884+01:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root-2231943548/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.19.0-30-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.9.2
2015-10-18T14:52:44.456+01:00| vthread-3| I120: Failed to compile module vmci!
```

---

