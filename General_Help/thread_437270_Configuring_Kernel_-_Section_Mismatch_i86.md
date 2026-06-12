---
title: "Configuring Kernel - Section Mismatch i86"
date: 2007-05-08
forum: General Help
---

### Post by jjmatt on 2007-05-08
I've compiled a custom kernel before, namely on edgy (and in gentoo) without a problem, however following the instructions here: [https://wiki.ubuntu.com/KernelCustomBuild]("https://wiki.ubuntu.com/KernelCustomBuild") I ran into this error:

```
WARNING: vmlinux - Section mismatch: reference to .init.data:boot_params from .text between '_text' (at offset 0xc0100036) and 'startup_32_smp'
WARNING: vmlinux - Section mismatch: reference to .init.data:boot_params from .text between '_text' (at offset 0xc0100044) and 'startup_32_smp'
WARNING: vmlinux - Section mismatch: reference to .init.data:init_pg_tables_end from .text between '_text' (at offset 0xc01000a6) and 'startup_32_smp'
WARNING: vmlinux - Section mismatch: reference to .init.data:new_cpu_data from .text between 'checkCPUtype' (at offset 0xc0100132) and 'is486'
WARNING: vmlinux - Section mismatch: reference to .init.data:new_cpu_data from .text between 'checkCPUtype' (at offset 0xc010013c) and 'is486'
WARNING: vmlinux - Section mismatch: reference to .init.data:new_cpu_data from .text between 'checkCPUtype' (at offset 0xc010015b) and 'is486'
WARNING: vmlinux - Section mismatch: reference to .init.data:new_cpu_data from .text between 'checkCPUtype' (at offset 0xc010016c) and 'is486'
WARNING: vmlinux - Section mismatch: reference to .init.data:new_cpu_data from .text between 'checkCPUtype' (at offset 0xc0100172) and 'is486'
WARNING: vmlinux - Section mismatch: reference to .init.data:new_cpu_data from .text between 'checkCPUtype' (at offset 0xc0100178) and 'is486'
WARNING: vmlinux - Section mismatch: reference to .init.data:new_cpu_data from .text between 'checkCPUtype' (at offset 0xc010017e) and 'is486'
WARNING: vmlinux - Section mismatch: reference to .init.data:new_cpu_data from .text between 'checkCPUtype' (at offset 0xc0100194) and 'is486'
WARNING: vmlinux - Section mismatch: reference to .init.data:new_cpu_data from .text between 'checkCPUtype' (at offset 0xc010019e) and 'is486'
WARNING: vmlinux - Section mismatch: reference to .init.data:new_cpu_data from .text between 'checkCPUtype' (at offset 0xc01001a7) and 'is486'
WARNING: vmlinux - Section mismatch: reference to .init.data:new_cpu_data from .text between 'checkCPUtype' (at offset 0xc01001ad) and 'is486'
WARNING: vmlinux - Section mismatch: reference to .init.data:new_cpu_data from .text between 'check_x87' (at offset 0xc0100227) and 'setup_pda'
WARNING: vmlinux - Section mismatch: reference to .init.data:new_cpu_data from .text between 'check_x87' (at offset 0xc0100246) and 'setup_pda'
WARNING: vmlinux - Section mismatch: reference to .init.text:start_kernel from .text between 'is386' (at offset 0xc0100221) and 'check_x87'
WARNING: vmlinux - Section mismatch: reference to .init.text:smp_prepare_cpus from .text between 'init' (at offset 0xc0100427) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:migration_init from .text between 'init' (at offset 0xc010042c) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:spawn_ksoftirqd from .text between 'init' (at offset 0xc0100431) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:spawn_softlockup_task from .text between 'init' (at offset 0xc0100436) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:cpu_up from .text between 'init' (at offset 0xc0100488) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:smp_cpus_done from .text between 'init' (at offset 0xc01004b3) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:sched_init_smp from .text between 'init' (at offset 0xc01004b8) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:usermodehelper_init from .text between 'init' (at offset 0xc01004c2) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:driver_init from .text between 'init' (at offset 0xc01004c7) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:sysctl_init from .text between 'init' (at offset 0xc01004d1) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.data: from .text between 'init' (at offset 0xc01004f3) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.data: from .text between 'init' (at offset 0xc010050c) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:prepare_namespace from .text between 'init' (at offset 0xc01006ff) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:cpu_set_gdt from .text between 'initialize_secondary' (at offset 0xc010d1bb) and 'mp_find_ioapic'
WARNING: vmlinux - Section mismatch: reference to .init.data:initkmem_list3 from .text between 'set_up_list3s' (at offset 0xc016242f) and 's_start'
WARNING: vmlinux - Section mismatch: reference to .init.text:eisa_root_register from .text between 'pci_eisa_init' (at offset 0xc025c2db) and 'virtual_eisa_release'
WARNING: vmlinux - Section mismatch: reference to .init.text:eisa_root_register from .text between 'virtual_eisa_root_init' (at offset 0xc025c33f) and 'cpufreq_unregister_driver'
WARNING: vmlinux - Section mismatch: reference to .init.text: from .text between 'iret_exc' (at offset 0xc02eb7a0) and '_etext'
WARNING: vmlinux - Section mismatch: reference to .init.text:start_kernel from .paravirtprobe between '__start_paravirtprobe' (at offset 0xc03b8270) and '__stop_paravirtprobe'
WARNING: "register_cpu_notifier" [drivers/kvm/kvm.ko] undefined!
make[2]: *** [__modpost] Error 1
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/j0hn/.src/linux-source-2.6.20'
make: *** [debian/stamp-build-kernel] Error 2

```

I need to compile a new kernel in order to get optimum efficiency out of my dual core machine. Unless anyone knows of any other ideas...

Thanks

---

### Post by jjmatt on 2007-05-09
bump

---

### Post by ikonia on 2007-05-09
please could you define what optimum effetiency options your using, the edgy and fesity kernel are both intel dual core aware and even the 6.06 build is smp aware.

---

### Post by jjmatt on 2007-05-09
I'm running a Dell XPS 400, I want to say its a pentium D processor (NOT core 2 duo). The second core works fine in windows, but isn't seen in feisty (nor was it in egdy until i compiled the kernel). The kernel option I enabled was SMP.

Looking at the config file that came with the current kernel SMP is not effective by default.

---

### Post by ikonia on 2007-05-10
you do not have to compile a kernel for this, there is an smp kernel available for every ubuntu release I've seen.

do not build your own kernel to enable smp, just check the repos.

I was perhaps wrongly under the impression that all the ubuntu kernels where smp by default.

---

### Post by jjmatt on 2007-05-10
Ah word, thanks.

In case anyone else is wondering, to get SMP working you must: 
```
sudo apt-get install linux-generic
```

and i'm assuming
```
sudo apt-get install linux-image-generic
```

This kernel is built with SMP vs, the 386 kernel which is not.

---

### Post by ikonia on 2007-05-10
glad to help

---

### Post by lwtbenben on 2007-07-25
[COLOR="Blue"]I got the same warning messages when I was compiling my Ubuntu kernel.[/COLOR]

IWARNING: vmlinux - Section mismatch: reference to .init.data:boot_params from .text between '_text' (at offset 0xc0100036) and 'startup_32_smp'
WARNING: vmlinux - Section mismatch: reference to .init.data:boot_params from .text between '_text' (at offset 0xc0100044) and 'startup_32_smp'
WARNING: vmlinux - Section mismatch: reference to .init.data:init_pg_tables_end from .text between '_text' (at offset 0xc01000a6) and 'startup_32_smp'

What can I do to prevent this warning???

---

