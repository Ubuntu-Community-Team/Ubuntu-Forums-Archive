---
title: "Section mismatch error when compiling kernel"
date: 2007-07-03
forum: General Help
---

### Post by rianquinn on 2007-07-03
I have tryed many ways to compile a kernel and all have failed to get ride of the following warnings:

```

WARNING: vmlinux - Section mismatch: reference to .init.data:boot_params from .text between '_text' (at offset 0xc0100036) and 'startup_32_smp'
WARNING: vmlinux - Section mismatch: reference to .init.data:boot_params from .text between '_text' (at offset 0xc0100044) and 'startup_32_smp'
WARNING: vmlinux - Section mismatch: reference to .init.data:init_pg_tables_end from .text between '_text' (at offset 0xc01000a6) and 'startup_32_smp'
WARNING: vmlinux - Section mismatch: reference to .init.text:start_kernel from .text between 'is386' (at offset 0xc0100221) and 'check_x87'
WARNING: vmlinux - Section mismatch: reference to .init.text:smp_prepare_cpus from .text between 'init' (at offset 0xc0100437) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:migration_init from .text between 'init' (at offset 0xc010043c) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:spawn_ksoftirqd from .text between 'init' (at offset 0xc0100441) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:spawn_softlockup_task from .text between 'init' (at offset 0xc0100446) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:smp_cpus_done from .text between 'init' (at offset 0xc01004c2) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:sched_init_smp from .text between 'init' (at offset 0xc01004c7) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:cpuset_init_smp from .text between 'init' (at offset 0xc01004cc) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:usermodehelper_init from .text between 'init' (at offset 0xc01004d6) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:driver_init from .text between 'init' (at offset 0xc01004db) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:sysctl_init from .text between 'init' (at offset 0xc01004e1) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.data: from .text between 'init' (at offset 0xc0100503) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.data: from .text between 'init' (at offset 0xc010051c) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:prepare_namespace from .text between 'init' (at offset 0xc01006ff) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:__alloc_bootmem from .text between 'init_gdt' (at offset 0xc010a0cb) and 'cpu_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:__alloc_bootmem from .text between 'init_gdt' (at offset 0xc010a0e1) and 'cpu_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:sysenter_setup from .text between 'identify_cpu' (at offset 0xc010a73b) and 'display_cacheinfo'
WARNING: vmlinux - Section mismatch: reference to .init.text:mtrr_bp_init from .text between 'identify_cpu' (at offset 0xc010a745) and 'display_cacheinfo'
WARNING: vmlinux - Section mismatch: reference to .init.text:trap_init_f00f_bug from .text between 'init_intel' (at offset 0xc010c796) and 'cpuid4_cache_lookup'
WARNING: vmlinux - Section mismatch: reference to .init.data:initkmem_list3 from .text between 'set_up_list3s' (at offset 0xc017238f) and 's_start'
WARNING: vmlinux - Section mismatch: reference to .init.text:eisa_root_register from .text between 'pci_eisa_init' (at offset 0xc026f71b) and 'virtual_eisa_release'
WARNING: vmlinux - Section mismatch: reference to .init.text:eisa_root_register from .text between 'virtual_eisa_root_init' (at offset 0xc026f77f) and 'cpufreq_unregister_driver'
WARNING: vmlinux - Section mismatch: reference to .init.text: from .text between 'iret_exc' (at offset 0xc02f2330) and '_etext'
WARNING: vmlinux - Section mismatch: reference to .init.text:start_kernel from .paravirtprobe between '__start_paravirtprobe' (at offset 0xc03c4790) and '__stop_paravirtprobe'

```

I need a kernel to compile so that I can write and test some kernel drivers I am writing. Here is my make script

```

#!/bin/sh
echo
echo "************************ Compiling Kernel Modules ************************"
export LINUX_SOURCES="linux-source-2.6.20"
make -C /usr/src/${LINUX_SOURCES} M=${PWD} modules
echo "**************************************************************************"
echo "DONE"
echo

```

When I run this make script I also get the warning messages above. How should I compile a kernel to prevent the messages?

---

