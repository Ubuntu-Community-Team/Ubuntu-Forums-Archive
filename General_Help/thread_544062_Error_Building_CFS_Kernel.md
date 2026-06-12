---
title: "Error Building CFS Kernel"
date: 2007-09-05
forum: General Help
---

### Post by toallpointswest on 2007-09-05
I'm building kernel 2.6.20  with the CFS patch applied [http://ubuntuforums.org/showthread.php?t=538068](http://ubuntuforums.org/showthread.php?t=538068) and I just recieved this error. Does anyone know how to resolve it? Thanks

```
 Building modules, stage 2.
  MODPOST 1188 modules
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
WARNING: vmlinux - Section mismatch: reference to .init.text:smp_prepare_cpus from .text between 'init' (at offset 0xc0100428) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:migration_init from .text between 'init' (at offset 0xc010042d) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:spawn_ksoftirqd from .text between 'init' (at offset 0xc0100432) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:spawn_softlockup_task from .text between 'init' (at offset 0xc0100437) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:cpu_up from .text between 'init' (at offset 0xc0100487) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:smp_cpus_done from .text between 'init' (at offset 0xc01004b2) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:sched_init_smp from .text between 'init' (at offset 0xc01004b7) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:cpuset_init_smp from .text between 'init' (at offset 0xc01004bc) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:usermodehelper_init from .text between 'init' (at offset 0xc01004c6) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:driver_init from .text between 'init' (at offset 0xc01004cb) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:sysctl_init from .text between 'init' (at offset 0xc01004d1) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.data: from .text between 'init' (at offset 0xc01004f7) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.data: from .text between 'init' (at offset 0xc0100514) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:prepare_namespace from .text between 'init' (at offset 0xc01006ff) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:init_idle_bootup_task from .text between 'rest_init' (at offset 0xc010073d) and 'try_name'
WARNING: vmlinux - Section mismatch: reference to .init.text:cpu_set_gdt from .text between 'initialize_secondary' (at offset 0xc010ccab) and 'mp_find_ioapic'
WARNING: vmlinux - Section mismatch: reference to .init.data:initkmem_list3 from .text between 'set_up_list3s' (at offset 0xc0165fdf) and 's_start'
WARNING: vmlinux - Section mismatch: reference to .init.data:logo_linux_mono from .text between 'fb_find_logo' (at offset 0xc01ff43a) and 'acpi_table_compute_checksum'
WARNING: vmlinux - Section mismatch: reference to .init.data:logo_linux_clut224 from .text between 'fb_find_logo' (at offset 0xc01ff447) and 'acpi_table_compute_checksum'
WARNING: vmlinux - Section mismatch: reference to .init.data:logo_linux_vga16 from .text between 'fb_find_logo' (at offset 0xc01ff44c) and 'acpi_table_compute_checksum'
WARNING: vmlinux - Section mismatch: reference to .init.text: from .text between 'iret_exc' (at offset 0xc02dacc6) and '_etext'
WARNING: vmlinux - Section mismatch: reference to .init.text:start_kernel from .paravirtprobe between '__start_paravirtprobe' (at offset 0xc03a2a10) and '__stop_paravirtprobe'
WARNING: "register_cpu_notifier" [drivers/kvm/kvm.ko] undefined!
make[2]: *** [__modpost] Error 1
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.20'
make: *** [debian/stamp-build-kernel] Error 2

```

---

