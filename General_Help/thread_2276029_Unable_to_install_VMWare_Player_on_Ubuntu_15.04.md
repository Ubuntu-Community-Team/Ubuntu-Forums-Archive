---
title: "Unable to install VMWare Player on Ubuntu 15.04"
date: 2015-04-29
forum: General Help
---

### Post by brian62 on 2015-04-29
When I try to install VMWare Player, it asks to compile modules and fails at the step "Starting VMWare Services" with the following error:


2015-04-29T18:43:24.520-07:00| vthread-4| W110: Failed to build vmnet.  Failed to execute the build command.

---

### Post by matthias-minjauw on 2015-04-30
I'm experiencing the same problem with Vmware player 7.1.0 on Ubuntu 15.04, when compiling the vmware modules after an install of Vmware player.

There are actually multiple errors occurring.
The full log is:

2015-04-30T17:52:16.368+02:00| vthread-4| I120: Log for VMware Workstation pid=2524 version=11.1.0 build=build-2496824 option=Release
2015-04-30T17:52:16.368+02:00| vthread-4| I120: The process is 64-bit.
2015-04-30T17:52:16.368+02:00| vthread-4| I120: Host codepage=UTF-8 encoding=UTF-8
2015-04-30T17:52:16.368+02:00| vthread-4| I120: Host is Linux 3.19.0-15-generic Ubuntu 15.04
2015-04-30T17:52:16.368+02:00| vthread-4| I120: DictionaryLoad: Cannot open file "/usr/lib/vmware/settings": No such file or directory.
2015-04-30T17:52:16.368+02:00| vthread-4| I120: Msg_Reset:
2015-04-30T17:52:16.368+02:00| vthread-4| I120: [msg.dictionary.load.openFailed] Cannot open file "/usr/lib/vmware/settings": No such file or directory.
2015-04-30T17:52:16.368+02:00| vthread-4| I120: ----------------------------------------
2015-04-30T17:52:16.368+02:00| vthread-4| I120: PREF Optional preferences file not found at /usr/lib/vmware/settings. Using default values.
2015-04-30T17:52:16.368+02:00| vthread-4| I120: DictionaryLoad: Cannot open file "/root/.vmware/config": No such file or directory.
2015-04-30T17:52:16.368+02:00| vthread-4| I120: Msg_Reset:
2015-04-30T17:52:16.368+02:00| vthread-4| I120: [msg.dictionary.load.openFailed] Cannot open file "/root/.vmware/config": No such file or directory.
2015-04-30T17:52:16.368+02:00| vthread-4| I120: ----------------------------------------
2015-04-30T17:52:16.368+02:00| vthread-4| I120: PREF Optional preferences file not found at /root/.vmware/config. Using default values.
2015-04-30T17:52:16.368+02:00| vthread-4| I120: PREF Unable to check permissions for preferences file.
2015-04-30T17:52:16.368+02:00| vthread-4| I120: DictionaryLoad: Cannot open file "/root/.vmware/preferences": No such file or directory.
2015-04-30T17:52:16.368+02:00| vthread-4| I120: Msg_Reset:
2015-04-30T17:52:16.368+02:00| vthread-4| I120: [msg.dictionary.load.openFailed] Cannot open file "/root/.vmware/preferences": No such file or directory.
2015-04-30T17:52:16.368+02:00| vthread-4| I120: ----------------------------------------
2015-04-30T17:52:16.368+02:00| vthread-4| I120: PREF Failed to load user preferences.
2015-04-30T17:52:16.396+02:00| vthread-4| W110: Logging to /tmp/vmware-root/vmware-2524.log
2015-04-30T17:52:16.403+02:00| vthread-4| I120: Obtaining info using the running kernel.
2015-04-30T17:52:16.403+02:00| vthread-4| I120: Created new pathsHash.
2015-04-30T17:52:16.403+02:00| vthread-4| I120: Setting header path for 3.19.0-15-generic to "/lib/modules/3.19.0-15-generic/build/include".
2015-04-30T17:52:16.403+02:00| vthread-4| I120: Validating path "/lib/modules/3.19.0-15-generic/build/include" for kernel release "3.19.0-15-generic".
2015-04-30T17:52:16.403+02:00| vthread-4| I120: Failed to find /lib/modules/3.19.0-15-generic/build/include/linux/version.h
2015-04-30T17:52:16.403+02:00| vthread-4| I120: /lib/modules/3.19.0-15-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2015-04-30T17:52:16.403+02:00| vthread-4| I120: using /usr/bin/gcc-4.9 for preprocess check
2015-04-30T17:52:16.408+02:00| vthread-4| I120: Preprocessed UTS_RELEASE, got value "3.19.0-15-generic".
2015-04-30T17:52:16.408+02:00| vthread-4| I120: The header path "/lib/modules/3.19.0-15-generic/build/include" for the kernel "3.19.0-15-generic" is valid.  Whoohoo!
2015-04-30T17:52:16.515+02:00| vthread-4| I120: found symbol version file /lib/modules/3.19.0-15-generic/build/Module.symvers
2015-04-30T17:52:16.515+02:00| vthread-4| I120: Reading symbol versions from /lib/modules/3.19.0-15-generic/build/Module.symvers.
2015-04-30T17:52:16.530+02:00| vthread-4| I120: Read 18818 symbol versions
2015-04-30T17:52:16.530+02:00| vthread-4| I120: Reading in info for the vmmon module.
2015-04-30T17:52:16.530+02:00| vthread-4| I120: Reading in info for the vmnet module.
2015-04-30T17:52:16.530+02:00| vthread-4| I120: Reading in info for the vmblock module.
2015-04-30T17:52:16.530+02:00| vthread-4| I120: Reading in info for the vmci module.
2015-04-30T17:52:16.530+02:00| vthread-4| I120: Reading in info for the vsock module.
2015-04-30T17:52:16.530+02:00| vthread-4| I120: Setting vsock to depend on vmci.
2015-04-30T17:52:16.530+02:00| vthread-4| I120: Invoking modinfo on "vmmon".
2015-04-30T17:52:16.531+02:00| vthread-4| I120: "/sbin/modinfo" exited with status 0.
2015-04-30T17:52:16.531+02:00| vthread-4| I120: Invoking modinfo on "vmnet".
2015-04-30T17:52:16.532+02:00| vthread-4| I120: "/sbin/modinfo" exited with status 256.
2015-04-30T17:52:16.532+02:00| vthread-4| I120: Invoking modinfo on "vmblock".
2015-04-30T17:52:16.534+02:00| vthread-4| I120: "/sbin/modinfo" exited with status 256.
2015-04-30T17:52:16.534+02:00| vthread-4| I120: Invoking modinfo on "vmci".
2015-04-30T17:52:16.535+02:00| vthread-4| I120: "/sbin/modinfo" exited with status 256.
2015-04-30T17:52:16.535+02:00| vthread-4| I120: Invoking modinfo on "vsock".
2015-04-30T17:52:16.536+02:00| vthread-4| I120: "/sbin/modinfo" exited with status 0.
2015-04-30T17:52:16.545+02:00| vthread-4| I120: to be installed: vmnet status: 0
2015-04-30T17:52:16.552+02:00| vthread-4| I120: Obtaining info using the running kernel.
2015-04-30T17:52:16.552+02:00| vthread-4| I120: Setting header path for 3.19.0-15-generic to "/lib/modules/3.19.0-15-generic/build/include".
2015-04-30T17:52:16.552+02:00| vthread-4| I120: Validating path "/lib/modules/3.19.0-15-generic/build/include" for kernel release "3.19.0-15-generic".
2015-04-30T17:52:16.552+02:00| vthread-4| I120: Failed to find /lib/modules/3.19.0-15-generic/build/include/linux/version.h
2015-04-30T17:52:16.552+02:00| vthread-4| I120: /lib/modules/3.19.0-15-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2015-04-30T17:52:16.552+02:00| vthread-4| I120: using /usr/bin/gcc-4.9 for preprocess check
2015-04-30T17:52:16.557+02:00| vthread-4| I120: Preprocessed UTS_RELEASE, got value "3.19.0-15-generic".
2015-04-30T17:52:16.557+02:00| vthread-4| I120: The header path "/lib/modules/3.19.0-15-generic/build/include" for the kernel "3.19.0-15-generic" is valid.  Whoohoo!
2015-04-30T17:52:16.664+02:00| vthread-4| I120: found symbol version file /lib/modules/3.19.0-15-generic/build/Module.symvers
2015-04-30T17:52:16.664+02:00| vthread-4| I120: Reading symbol versions from /lib/modules/3.19.0-15-generic/build/Module.symvers.
2015-04-30T17:52:16.678+02:00| vthread-4| I120: Read 18818 symbol versions
2015-04-30T17:52:16.678+02:00| vthread-4| I120: Kernel header path retrieved from FileEntry: /lib/modules/3.19.0-15-generic/build/include
2015-04-30T17:52:16.678+02:00| vthread-4| I120: Update kernel header path to /lib/modules/3.19.0-15-generic/build/include
2015-04-30T17:52:16.678+02:00| vthread-4| I120: Validating path "/lib/modules/3.19.0-15-generic/build/include" for kernel release "3.19.0-15-generic".
2015-04-30T17:52:16.678+02:00| vthread-4| I120: Failed to find /lib/modules/3.19.0-15-generic/build/include/linux/version.h
2015-04-30T17:52:16.678+02:00| vthread-4| I120: /lib/modules/3.19.0-15-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2015-04-30T17:52:16.678+02:00| vthread-4| I120: using /usr/bin/gcc-4.9 for preprocess check
2015-04-30T17:52:16.683+02:00| vthread-4| I120: Preprocessed UTS_RELEASE, got value "3.19.0-15-generic".
2015-04-30T17:52:16.683+02:00| vthread-4| I120: The header path "/lib/modules/3.19.0-15-generic/build/include" for the kernel "3.19.0-15-generic" is valid.  Whoohoo!
2015-04-30T17:52:16.684+02:00| vthread-4| I120: Found compiler at "/usr/bin/gcc"
2015-04-30T17:52:16.685+02:00| vthread-4| I120: Got gcc version "4.9.2".
2015-04-30T17:52:16.685+02:00| vthread-4| I120: The GCC version matches the kernel GCC minor version like a glove.
2015-04-30T17:52:16.685+02:00| vthread-4| I120: Using user supplied compiler "/usr/bin/gcc".
2015-04-30T17:52:16.687+02:00| vthread-4| I120: Got gcc version "4.9.2".
2015-04-30T17:52:16.688+02:00| vthread-4| I120: The GCC version matches the kernel GCC minor version like a glove.
2015-04-30T17:52:16.690+02:00| vthread-4| I120: Trying to find a suitable PBM set for kernel "3.19.0-15-generic".
2015-04-30T17:52:16.690+02:00| vthread-4| I120: No matching PBM set was found for kernel "3.19.0-15-generic".
2015-04-30T17:52:16.690+02:00| vthread-4| I120: The GCC version matches the kernel GCC minor version like a glove.
2015-04-30T17:52:16.690+02:00| vthread-4| I120: Validating path "/lib/modules/3.19.0-15-generic/build/include" for kernel release "3.19.0-15-generic".
2015-04-30T17:52:16.690+02:00| vthread-4| I120: Failed to find /lib/modules/3.19.0-15-generic/build/include/linux/version.h
2015-04-30T17:52:16.690+02:00| vthread-4| I120: /lib/modules/3.19.0-15-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2015-04-30T17:52:16.690+02:00| vthread-4| I120: using /usr/bin/gcc-4.9 for preprocess check
2015-04-30T17:52:16.694+02:00| vthread-4| I120: Preprocessed UTS_RELEASE, got value "3.19.0-15-generic".
2015-04-30T17:52:16.694+02:00| vthread-4| I120: The header path "/lib/modules/3.19.0-15-generic/build/include" for the kernel "3.19.0-15-generic" is valid.  Whoohoo!
2015-04-30T17:52:16.713+02:00| vthread-4| I120: The GCC version matches the kernel GCC minor version like a glove.
2015-04-30T17:52:16.713+02:00| vthread-4| I120: Validating path "/lib/modules/3.19.0-15-generic/build/include" for kernel release "3.19.0-15-generic".
2015-04-30T17:52:16.713+02:00| vthread-4| I120: Failed to find /lib/modules/3.19.0-15-generic/build/include/linux/version.h
2015-04-30T17:52:16.713+02:00| vthread-4| I120: /lib/modules/3.19.0-15-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2015-04-30T17:52:16.713+02:00| vthread-4| I120: using /usr/bin/gcc-4.9 for preprocess check
2015-04-30T17:52:16.717+02:00| vthread-4| I120: Preprocessed UTS_RELEASE, got value "3.19.0-15-generic".
2015-04-30T17:52:16.717+02:00| vthread-4| I120: The header path "/lib/modules/3.19.0-15-generic/build/include" for the kernel "3.19.0-15-generic" is valid.  Whoohoo!
2015-04-30T17:52:16.717+02:00| vthread-4| I120: Using temp dir "/tmp".
2015-04-30T17:52:16.718+02:00| vthread-4| I120: Obtaining info using the running kernel.
2015-04-30T17:52:16.718+02:00| vthread-4| I120: Setting header path for 3.19.0-15-generic to "/lib/modules/3.19.0-15-generic/build/include".
2015-04-30T17:52:16.718+02:00| vthread-4| I120: Validating path "/lib/modules/3.19.0-15-generic/build/include" for kernel release "3.19.0-15-generic".
2015-04-30T17:52:16.718+02:00| vthread-4| I120: Failed to find /lib/modules/3.19.0-15-generic/build/include/linux/version.h
2015-04-30T17:52:16.718+02:00| vthread-4| I120: /lib/modules/3.19.0-15-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2015-04-30T17:52:16.718+02:00| vthread-4| I120: using /usr/bin/gcc-4.9 for preprocess check
2015-04-30T17:52:16.722+02:00| vthread-4| I120: Preprocessed UTS_RELEASE, got value "3.19.0-15-generic".
2015-04-30T17:52:16.722+02:00| vthread-4| I120: The header path "/lib/modules/3.19.0-15-generic/build/include" for the kernel "3.19.0-15-generic" is valid.  Whoohoo!
2015-04-30T17:52:16.828+02:00| vthread-4| I120: found symbol version file /lib/modules/3.19.0-15-generic/build/Module.symvers
2015-04-30T17:52:16.828+02:00| vthread-4| I120: Reading symbol versions from /lib/modules/3.19.0-15-generic/build/Module.symvers.
2015-04-30T17:52:16.843+02:00| vthread-4| I120: Read 18818 symbol versions
2015-04-30T17:52:16.844+02:00| vthread-4| I120: Invoking modinfo on "vmnet".
2015-04-30T17:52:16.846+02:00| vthread-4| I120: "/sbin/modinfo" exited with status 256.
2015-04-30T17:52:17.081+02:00| vthread-4| I120: Setting destination path for vmnet to "/lib/modules/3.19.0-15-generic/misc/vmnet.ko".
2015-04-30T17:52:17.082+02:00| vthread-4| I120: Extracting the vmnet source from "/usr/lib/vmware/modules/source/vmnet.tar".
2015-04-30T17:52:17.089+02:00| vthread-4| I120: Successfully extracted the vmnet source.
2015-04-30T17:52:17.089+02:00| vthread-4| I120: Building module with command "/usr/bin/make -j8 -C /tmp/modconfig-qIbF4g/vmnet-only auto-build HEADER_DIR=/lib/modules/3.19.0-15-generic/build/include CC=/usr/bin/gcc IS_GCC_3=no"
2015-04-30T17:52:18.309+02:00| vthread-4| W110: Failed to build vmnet.  Failed to execute the build command.

---

### Post by henpanta on 2015-05-10
same here

---

### Post by DanyalDenyo on 2015-06-03
Same here, can't install VMWare Player or VMWare Workstation on Ubuntu 15.04

**Edit: While installing (before compile) it gives this error multiple times in the Terminal:**

(vmware-installer.py:9453): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory


Here's my log file of compile attempt:

2015-06-03T20:50:39.894+03:00| vthread-4| I120: Log for VMware Workstation pid=4027 version=11.1.0 build=build-2496824 option=Release
2015-06-03T20:50:39.894+03:00| vthread-4| I120: The process is 64-bit.
2015-06-03T20:50:39.894+03:00| vthread-4| I120: Host codepage=UTF-8 encoding=UTF-8
2015-06-03T20:50:39.894+03:00| vthread-4| I120: Host is Linux 3.19.0-18-generic Ubuntu 15.04
2015-06-03T20:50:39.893+03:00| vthread-4| I120: DictionaryLoad: Cannot open file "/usr/lib/vmware/settings": No such file or directory.
2015-06-03T20:50:39.893+03:00| vthread-4| I120: Msg_Reset:
2015-06-03T20:50:39.893+03:00| vthread-4| I120: [msg.dictionary.load.openFailed] Cannot open file "/usr/lib/vmware/settings": No such file or directory.
2015-06-03T20:50:39.893+03:00| vthread-4| I120: ----------------------------------------
2015-06-03T20:50:39.893+03:00| vthread-4| I120: PREF Optional preferences file not found at /usr/lib/vmware/settings. Using default values.
2015-06-03T20:50:39.894+03:00| vthread-4| I120: DictionaryLoad: Cannot open file "/root/.vmware/config": No such file or directory.
2015-06-03T20:50:39.894+03:00| vthread-4| I120: Msg_Reset:
2015-06-03T20:50:39.894+03:00| vthread-4| I120: [msg.dictionary.load.openFailed] Cannot open file "/root/.vmware/config": No such file or directory.
2015-06-03T20:50:39.894+03:00| vthread-4| I120: ----------------------------------------
2015-06-03T20:50:39.894+03:00| vthread-4| I120: PREF Optional preferences file not found at /root/.vmware/config. Using default values.
2015-06-03T20:50:39.894+03:00| vthread-4| I120: PREF Unable to check permissions for preferences file.
2015-06-03T20:50:39.894+03:00| vthread-4| I120: DictionaryLoad: Cannot open file "/root/.vmware/preferences": No such file or directory.
2015-06-03T20:50:39.894+03:00| vthread-4| I120: Msg_Reset:
2015-06-03T20:50:39.894+03:00| vthread-4| I120: [msg.dictionary.load.openFailed] Cannot open file "/root/.vmware/preferences": No such file or directory.
2015-06-03T20:50:39.894+03:00| vthread-4| I120: ----------------------------------------
2015-06-03T20:50:39.894+03:00| vthread-4| I120: PREF Failed to load user preferences.
2015-06-03T20:50:39.934+03:00| vthread-4| W110: Logging to /tmp/vmware-root/vmware-4027.log
2015-06-03T20:50:39.947+03:00| vthread-4| I120: Obtaining info using the running kernel.
2015-06-03T20:50:39.948+03:00| vthread-4| I120: Created new pathsHash.
2015-06-03T20:50:39.948+03:00| vthread-4| I120: Setting header path for 3.19.0-18-generic to "/lib/modules/3.19.0-18-generic/build/include".
2015-06-03T20:50:39.948+03:00| vthread-4| I120: Validating path "/lib/modules/3.19.0-18-generic/build/include" for kernel release "3.19.0-18-generic".
2015-06-03T20:50:39.948+03:00| vthread-4| I120: Failed to find /lib/modules/3.19.0-18-generic/build/include/linux/version.h
2015-06-03T20:50:39.948+03:00| vthread-4| I120: /lib/modules/3.19.0-18-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2015-06-03T20:50:39.949+03:00| vthread-4| I120: using /usr/bin/gcc-4.9 for preprocess check
2015-06-03T20:50:39.955+03:00| vthread-4| I120: Preprocessed UTS_RELEASE, got value "3.19.0-18-generic".
2015-06-03T20:50:39.955+03:00| vthread-4| I120: The header path "/lib/modules/3.19.0-18-generic/build/include" for the kernel "3.19.0-18-generic" is valid.  Whoohoo!
2015-06-03T20:50:40.103+03:00| vthread-4| I120: found symbol version file /lib/modules/3.19.0-18-generic/build/Module.symvers
2015-06-03T20:50:40.103+03:00| vthread-4| I120: Reading symbol versions from /lib/modules/3.19.0-18-generic/build/Module.symvers.
2015-06-03T20:50:40.123+03:00| vthread-4| I120: Read 18826 symbol versions
2015-06-03T20:50:40.126+03:00| vthread-4| I120: Reading in info for the vmmon module.
2015-06-03T20:50:40.126+03:00| vthread-4| I120: Reading in info for the vmnet module.
2015-06-03T20:50:40.126+03:00| vthread-4| I120: Reading in info for the vmblock module.
2015-06-03T20:50:40.126+03:00| vthread-4| I120: Reading in info for the vmci module.
2015-06-03T20:50:40.126+03:00| vthread-4| I120: Reading in info for the vsock module.
2015-06-03T20:50:40.126+03:00| vthread-4| I120: Setting vsock to depend on vmci.
2015-06-03T20:50:40.126+03:00| vthread-4| I120: Invoking modinfo on "vmmon".
2015-06-03T20:50:40.128+03:00| vthread-4| I120: "/sbin/modinfo" exited with status 256.
2015-06-03T20:50:40.128+03:00| vthread-4| I120: Invoking modinfo on "vmnet".
2015-06-03T20:50:40.130+03:00| vthread-4| I120: "/sbin/modinfo" exited with status 256.
2015-06-03T20:50:40.130+03:00| vthread-4| I120: Invoking modinfo on "vmblock".
2015-06-03T20:50:40.131+03:00| vthread-4| I120: "/sbin/modinfo" exited with status 256.
2015-06-03T20:50:40.131+03:00| vthread-4| I120: Invoking modinfo on "vmci".
2015-06-03T20:50:40.133+03:00| vthread-4| I120: "/sbin/modinfo" exited with status 256.
2015-06-03T20:50:40.133+03:00| vthread-4| I120: Invoking modinfo on "vsock".
2015-06-03T20:50:40.134+03:00| vthread-4| I120: "/sbin/modinfo" exited with status 0.
2015-06-03T20:50:40.149+03:00| vthread-4| I120: to be installed: vmmon status: 0
2015-06-03T20:50:40.149+03:00| vthread-4| I120: to be installed: vmnet status: 0
2015-06-03T20:50:40.158+03:00| vthread-4| I120: Obtaining info using the running kernel.
2015-06-03T20:50:40.158+03:00| vthread-4| I120: Setting header path for 3.19.0-18-generic to "/lib/modules/3.19.0-18-generic/build/include".
2015-06-03T20:50:40.158+03:00| vthread-4| I120: Validating path "/lib/modules/3.19.0-18-generic/build/include" for kernel release "3.19.0-18-generic".
2015-06-03T20:50:40.158+03:00| vthread-4| I120: Failed to find /lib/modules/3.19.0-18-generic/build/include/linux/version.h
2015-06-03T20:50:40.158+03:00| vthread-4| I120: /lib/modules/3.19.0-18-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2015-06-03T20:50:40.159+03:00| vthread-4| I120: using /usr/bin/gcc-4.9 for preprocess check
2015-06-03T20:50:40.164+03:00| vthread-4| I120: Preprocessed UTS_RELEASE, got value "3.19.0-18-generic".
2015-06-03T20:50:40.164+03:00| vthread-4| I120: The header path "/lib/modules/3.19.0-18-generic/build/include" for the kernel "3.19.0-18-generic" is valid.  Whoohoo!
2015-06-03T20:50:40.355+03:00| vthread-4| I120: found symbol version file /lib/modules/3.19.0-18-generic/build/Module.symvers
2015-06-03T20:50:40.355+03:00| vthread-4| I120: Reading symbol versions from /lib/modules/3.19.0-18-generic/build/Module.symvers.
2015-06-03T20:50:40.377+03:00| vthread-4| I120: Read 18826 symbol versions
2015-06-03T20:50:40.378+03:00| vthread-4| I120: Kernel header path retrieved from FileEntry: /lib/modules/3.19.0-18-generic/build/include
2015-06-03T20:50:40.378+03:00| vthread-4| I120: Update kernel header path to /lib/modules/3.19.0-18-generic/build/include
2015-06-03T20:50:40.378+03:00| vthread-4| I120: Validating path "/lib/modules/3.19.0-18-generic/build/include" for kernel release "3.19.0-18-generic".
2015-06-03T20:50:40.378+03:00| vthread-4| I120: Failed to find /lib/modules/3.19.0-18-generic/build/include/linux/version.h
2015-06-03T20:50:40.378+03:00| vthread-4| I120: /lib/modules/3.19.0-18-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2015-06-03T20:50:40.378+03:00| vthread-4| I120: using /usr/bin/gcc-4.9 for preprocess check
2015-06-03T20:50:40.383+03:00| vthread-4| I120: Preprocessed UTS_RELEASE, got value "3.19.0-18-generic".
2015-06-03T20:50:40.383+03:00| vthread-4| I120: The header path "/lib/modules/3.19.0-18-generic/build/include" for the kernel "3.19.0-18-generic" is valid.  Whoohoo!
2015-06-03T20:50:40.384+03:00| vthread-4| I120: Found compiler at "/usr/bin/gcc"
2015-06-03T20:50:40.390+03:00| vthread-4| I120: Got gcc version "4.9.2".
2015-06-03T20:50:40.390+03:00| vthread-4| I120: The GCC version matches the kernel GCC minor version like a glove.
2015-06-03T20:50:40.390+03:00| vthread-4| I120: Using user supplied compiler "/usr/bin/gcc".
2015-06-03T20:50:40.393+03:00| vthread-4| I120: Got gcc version "4.9.2".
2015-06-03T20:50:40.393+03:00| vthread-4| I120: The GCC version matches the kernel GCC minor version like a glove.
2015-06-03T20:50:40.418+03:00| vthread-4| I120: Trying to find a suitable PBM set for kernel "3.19.0-18-generic".
2015-06-03T20:50:40.418+03:00| vthread-4| I120: No matching PBM set was found for kernel "3.19.0-18-generic".
2015-06-03T20:50:40.418+03:00| vthread-4| I120: The GCC version matches the kernel GCC minor version like a glove.
2015-06-03T20:50:40.418+03:00| vthread-4| I120: Validating path "/lib/modules/3.19.0-18-generic/build/include" for kernel release "3.19.0-18-generic".
2015-06-03T20:50:40.418+03:00| vthread-4| I120: Failed to find /lib/modules/3.19.0-18-generic/build/include/linux/version.h
2015-06-03T20:50:40.418+03:00| vthread-4| I120: /lib/modules/3.19.0-18-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2015-06-03T20:50:40.418+03:00| vthread-4| I120: using /usr/bin/gcc-4.9 for preprocess check
2015-06-03T20:50:40.424+03:00| vthread-4| I120: Preprocessed UTS_RELEASE, got value "3.19.0-18-generic".
2015-06-03T20:50:40.424+03:00| vthread-4| I120: The header path "/lib/modules/3.19.0-18-generic/build/include" for the kernel "3.19.0-18-generic" is valid.  Whoohoo!
2015-06-03T20:50:40.469+03:00| vthread-4| I120: The GCC version matches the kernel GCC minor version like a glove.
2015-06-03T20:50:40.469+03:00| vthread-4| I120: Validating path "/lib/modules/3.19.0-18-generic/build/include" for kernel release "3.19.0-18-generic".
2015-06-03T20:50:40.469+03:00| vthread-4| I120: Failed to find /lib/modules/3.19.0-18-generic/build/include/linux/version.h
2015-06-03T20:50:40.469+03:00| vthread-4| I120: /lib/modules/3.19.0-18-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2015-06-03T20:50:40.469+03:00| vthread-4| I120: using /usr/bin/gcc-4.9 for preprocess check
2015-06-03T20:50:40.478+03:00| vthread-4| I120: Preprocessed UTS_RELEASE, got value "3.19.0-18-generic".
2015-06-03T20:50:40.478+03:00| vthread-4| I120: The header path "/lib/modules/3.19.0-18-generic/build/include" for the kernel "3.19.0-18-generic" is valid.  Whoohoo!
2015-06-03T20:50:40.478+03:00| vthread-4| I120: Using temp dir "/tmp".
2015-06-03T20:50:40.478+03:00| vthread-4| I120: Obtaining info using the running kernel.
2015-06-03T20:50:40.478+03:00| vthread-4| I120: Setting header path for 3.19.0-18-generic to "/lib/modules/3.19.0-18-generic/build/include".
2015-06-03T20:50:40.478+03:00| vthread-4| I120: Validating path "/lib/modules/3.19.0-18-generic/build/include" for kernel release "3.19.0-18-generic".
2015-06-03T20:50:40.478+03:00| vthread-4| I120: Failed to find /lib/modules/3.19.0-18-generic/build/include/linux/version.h
2015-06-03T20:50:40.478+03:00| vthread-4| I120: /lib/modules/3.19.0-18-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2015-06-03T20:50:40.478+03:00| vthread-4| I120: using /usr/bin/gcc-4.9 for preprocess check
2015-06-03T20:50:40.483+03:00| vthread-4| I120: Preprocessed UTS_RELEASE, got value "3.19.0-18-generic".
2015-06-03T20:50:40.483+03:00| vthread-4| I120: The header path "/lib/modules/3.19.0-18-generic/build/include" for the kernel "3.19.0-18-generic" is valid.  Whoohoo!
2015-06-03T20:50:40.637+03:00| vthread-4| I120: found symbol version file /lib/modules/3.19.0-18-generic/build/Module.symvers
2015-06-03T20:50:40.637+03:00| vthread-4| I120: Reading symbol versions from /lib/modules/3.19.0-18-generic/build/Module.symvers.
2015-06-03T20:50:40.659+03:00| vthread-4| I120: Read 18826 symbol versions
2015-06-03T20:50:40.659+03:00| vthread-4| I120: Invoking modinfo on "vmmon".
2015-06-03T20:50:40.661+03:00| vthread-4| I120: "/sbin/modinfo" exited with status 256.
2015-06-03T20:50:40.661+03:00| vthread-4| I120: Invoking modinfo on "vmnet".
2015-06-03T20:50:40.663+03:00| vthread-4| I120: "/sbin/modinfo" exited with status 256.
2015-06-03T20:50:41.140+03:00| vthread-4| I120: Setting destination path for vmmon to "/lib/modules/3.19.0-18-generic/misc/vmmon.ko".
2015-06-03T20:50:41.141+03:00| vthread-4| I120: Extracting the vmmon source from "/usr/lib/vmware/modules/source/vmmon.tar".
2015-06-03T20:50:41.157+03:00| vthread-4| I120: Successfully extracted the vmmon source.
2015-06-03T20:50:41.157+03:00| vthread-4| I120: Building module with command "/usr/bin/make -j4 -C /tmp/modconfig-PomcIr/vmmon-only auto-build HEADER_DIR=/lib/modules/3.19.0-18-generic/build/include CC=/usr/bin/gcc IS_GCC_3=no"
2015-06-03T20:50:43.851+03:00| vthread-4| I120: Successfully built vmmon.  Module is currently at "/tmp/modconfig-PomcIr/vmmon.o".
2015-06-03T20:50:43.851+03:00| vthread-4| I120: Found the vmmon symvers file at "/tmp/modconfig-PomcIr/vmmon-only/Module.symvers".
2015-06-03T20:50:43.851+03:00| vthread-4| I120: Installing vmmon from /tmp/modconfig-PomcIr/vmmon.o to /lib/modules/3.19.0-18-generic/misc/vmmon.ko.
2015-06-03T20:50:43.852+03:00| vthread-4| I120: Registering file "/lib/modules/3.19.0-18-generic/misc/vmmon.ko".
2015-06-03T20:50:44.312+03:00| vthread-4| I120: "/usr/lib/vmware-installer/2.1.0/vmware-installer" exited with status 0.
2015-06-03T20:50:44.313+03:00| vthread-4| I120: Registering file "/usr/lib/vmware/symvers/vmmon-3.19.0-18-generic".
2015-06-03T20:50:44.636+03:00| vthread-4| I120: "/usr/lib/vmware-installer/2.1.0/vmware-installer" exited with status 0.
2015-06-03T20:50:44.638+03:00| vthread-4| I120: Setting destination path for vmnet to "/lib/modules/3.19.0-18-generic/misc/vmnet.ko".
2015-06-03T20:50:44.638+03:00| vthread-4| I120: Extracting the vmnet source from "/usr/lib/vmware/modules/source/vmnet.tar".
2015-06-03T20:50:44.649+03:00| vthread-4| I120: Successfully extracted the vmnet source.
2015-06-03T20:50:44.649+03:00| vthread-4| I120: Building module with command "/usr/bin/make -j4 -C /tmp/modconfig-PomcIr/vmnet-only auto-build HEADER_DIR=/lib/modules/3.19.0-18-generic/build/include CC=/usr/bin/gcc IS_GCC_3=no"
2015-06-03T20:50:46.266+03:00| vthread-4| W110: Failed to build vmnet.  Failed to execute the build command.
2015-06-03T20:58:08.300+03:00| vthread-4| I120: The GCC version matches the kernel GCC minor version like a glove.
2015-06-03T20:58:08.300+03:00| vthread-4| I120: Validating path "/lib/modules/3.19.0-18-generic/build/include" for kernel release "3.19.0-18-generic".
2015-06-03T20:58:08.302+03:00| vthread-4| I120: Failed to find /lib/modules/3.19.0-18-generic/build/include/linux/version.h
2015-06-03T20:58:08.302+03:00| vthread-4| I120: /lib/modules/3.19.0-18-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2015-06-03T20:58:08.302+03:00| vthread-4| I120: using /usr/bin/gcc-4.9 for preprocess check
2015-06-03T20:58:08.374+03:00| vthread-4| I120: Preprocessed UTS_RELEASE, got value "3.19.0-18-generic".
2015-06-03T20:58:08.375+03:00| vthread-4| I120: The header path "/lib/modules/3.19.0-18-generic/build/include" for the kernel "3.19.0-18-generic" is valid.  Whoohoo!
2015-06-03T20:58:08.375+03:00| vthread-4| I120: Using temp dir "/tmp".
2015-06-03T20:58:08.375+03:00| vthread-4| I120: Obtaining info using the running kernel.
2015-06-03T20:58:08.375+03:00| vthread-4| I120: Setting header path for 3.19.0-18-generic to "/lib/modules/3.19.0-18-generic/build/include".
2015-06-03T20:58:08.375+03:00| vthread-4| I120: Validating path "/lib/modules/3.19.0-18-generic/build/include" for kernel release "3.19.0-18-generic".
2015-06-03T20:58:08.375+03:00| vthread-4| I120: Failed to find /lib/modules/3.19.0-18-generic/build/include/linux/version.h
2015-06-03T20:58:08.375+03:00| vthread-4| I120: /lib/modules/3.19.0-18-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2015-06-03T20:58:08.375+03:00| vthread-4| I120: using /usr/bin/gcc-4.9 for preprocess check
2015-06-03T20:58:08.380+03:00| vthread-4| I120: Preprocessed UTS_RELEASE, got value "3.19.0-18-generic".
2015-06-03T20:58:08.380+03:00| vthread-4| I120: The header path "/lib/modules/3.19.0-18-generic/build/include" for the kernel "3.19.0-18-generic" is valid.  Whoohoo!
2015-06-03T20:58:08.501+03:00| vthread-4| I120: found symbol version file /lib/modules/3.19.0-18-generic/build/Module.symvers
2015-06-03T20:58:08.501+03:00| vthread-4| I120: Reading symbol versions from /lib/modules/3.19.0-18-generic/build/Module.symvers.
2015-06-03T20:58:08.520+03:00| vthread-4| I120: Read 18826 symbol versions
2015-06-03T20:58:08.520+03:00| vthread-4| I120: Invoking modinfo on "vmmon".
2015-06-03T20:58:08.523+03:00| vthread-4| I120: "/sbin/modinfo" exited with status 0.
2015-06-03T20:58:08.523+03:00| vthread-4| I120: Invoking modinfo on "vmnet".
2015-06-03T20:58:08.525+03:00| vthread-4| I120: "/sbin/modinfo" exited with status 256.
2015-06-03T20:58:08.862+03:00| vthread-4| I120: Setting destination path for vmnet to "/lib/modules/3.19.0-18-generic/misc/vmnet.ko".
2015-06-03T20:58:08.862+03:00| vthread-4| I120: Extracting the vmnet source from "/usr/lib/vmware/modules/source/vmnet.tar".
2015-06-03T20:58:08.869+03:00| vthread-4| I120: Successfully extracted the vmnet source.
2015-06-03T20:58:08.869+03:00| vthread-4| I120: Building module with command "/usr/bin/make -j4 -C /tmp/modconfig-oeE9Yq/vmnet-only auto-build HEADER_DIR=/lib/modules/3.19.0-18-generic/build/include CC=/usr/bin/gcc IS_GCC_3=no"
2015-06-03T20:58:10.140+03:00| vthread-4| W110: Failed to build vmnet.  Failed to execute the build command.

---

