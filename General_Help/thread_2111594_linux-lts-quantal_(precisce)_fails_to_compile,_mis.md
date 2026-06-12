---
title: "linux-lts-quantal (precisce) fails to compile, missing dependency?"
date: 2013-02-02
forum: General Help
---

### Post by quequotion on 2013-02-02
Trying to compile the lts kernel:```
arch/x86/built-in.o: In function `alternatives_smp_switch':
(.text+0x7974): undefined reference to `cpu_info'
arch/x86/built-in.o: In function `alternatives_smp_switch':
(.text+0x7a91): undefined reference to `cpu_info'
arch/x86/built-in.o: In function `time_cpufreq_notifier':
tsc.c:(.text+0x84d9): undefined reference to `cpu_info'
arch/x86/built-in.o: In function `mwait_idle':
process.c:(.text+0x93c9): undefined reference to `cpu_info'
arch/x86/built-in.o: In function `c_start':
proc.c:(.text+0xec11): undefined reference to `cpu_info'
arch/x86/built-in.o: In function `show_cpuinfo':
proc.c:(.text+0xed1b): undefined reference to `smp_num_siblings'
proc.c:(.text+0xed52): undefined reference to `cpu_core_map'
arch/x86/built-in.o: In function `amd_get_nb_id':
(.text+0xf576): undefined reference to `cpu_llc_id'
arch/x86/built-in.o: In function `cpu_has_amd_erratum':
(.text+0xf593): undefined reference to `cpu_info'
arch/x86/built-in.o: In function `p4_pmu_schedule_events':
perf_event_p4.c:(.text+0x126dc): undefined reference to `smp_num_siblings'
perf_event_p4.c:(.text+0x12702): undefined reference to `cpu_sibling_map'
perf_event_p4.c:(.text+0x12777): undefined reference to `smp_num_siblings'
perf_event_p4.c:(.text+0x12883): undefined reference to `smp_num_siblings'
perf_event_p4.c:(.text+0x128d3): undefined reference to `cpu_sibling_map'
perf_event_p4.c:(.text+0x12973): undefined reference to `smp_num_siblings'
perf_event_p4.c:(.text+0x129cc): undefined reference to `cpu_sibling_map'
perf_event_p4.c:(.text+0x12a13): undefined reference to `cpu_sibling_map'
arch/x86/built-in.o: In function `p4_hw_config':
perf_event_p4.c:(.text+0x12b17): undefined reference to `smp_num_siblings'
perf_event_p4.c:(.text+0x12c07): undefined reference to `smp_num_siblings'
perf_event_p4.c:(.text+0x12d23): undefined reference to `cpu_sibling_map'
perf_event_p4.c:(.text+0x12d58): undefined reference to `smp_num_siblings'
perf_event_p4.c:(.text+0x12da8): undefined reference to `smp_num_siblings'
perf_event_p4.c:(.text+0x12dbb): undefined reference to `cpu_sibling_map'
perf_event_p4.c:(.text+0x12e0f): undefined reference to `smp_num_siblings'
arch/x86/built-in.o: In function `intel_pmu_cpu_starting':
perf_event_intel.c:(.text+0x14aa5): undefined reference to `cpu_info'
perf_event_intel.c:(.text+0x14b05): undefined reference to `cpu_sibling_map'
arch/x86/built-in.o: In function `print_mce':
mce.c:(.text+0x165a5): undefined reference to `cpu_info'
arch/x86/built-in.o: In function `mce_setup':
(.text+0x16fdd): undefined reference to `cpu_info'
arch/x86/built-in.o: In function `mce_syscore_resume':
mce.c:(.text+0x17e3c): undefined reference to `cpu_info'
arch/x86/built-in.o: In function `mce_enable_ce':
mce.c:(.text+0x17ea7): undefined reference to `cpu_info'
arch/x86/built-in.o: In function `mce_timer_fn':
mce.c:(.text+0x17f0c): undefined reference to `cpu_info'
arch/x86/built-in.o:mce.c:(.text+0x17fe7): more undefined references to `cpu_info' follow
arch/x86/built-in.o: In function `default_inquire_remote_apic':
apic_flat_64.c:(.text+0x220ca): undefined reference to `__inquire_remote_apic'
arch/x86/built-in.o: In function `amd_get_subcaches':
(.text+0x23f09): undefined reference to `cpu_info'
arch/x86/built-in.o: In function `amd_set_subcaches':
(.text+0x23fd6): undefined reference to `cpu_info'
arch/x86/built-in.o: In function `setup_arch':
(.init.text+0x1005): undefined reference to `prefill_possible_map'
arch/x86/built-in.o: In function `alternative_instructions':
(.init.text+0x2fcd): undefined reference to `cpu_info'
arch/x86/built-in.o: In function `disable_x2apic':
apic.c:(.init.text+0x9f67): undefined reference to `cpu_info'
arch/x86/built-in.o: In function `loop_timeout':
tsc_sync.c:(.text.unlikely+0x3cc): undefined reference to `cpu_core_map'
arch/x86/built-in.o: In function `cpu_vsyscall_init':
vsyscall_64.c:(.cpuinit.text+0x46): undefined reference to `cpu_info'
arch/x86/built-in.o: In function `calibrate_delay_is_known':
(.cpuinit.text+0x13e): undefined reference to `cpu_info'
arch/x86/built-in.o: In function `calibrate_delay_is_known':
(.cpuinit.text+0x19b): undefined reference to `cpu_info'
arch/x86/built-in.o: In function `select_idle_routine':
(.cpuinit.text+0x1d5): undefined reference to `smp_num_siblings'
arch/x86/built-in.o: In function `cpuid4_cache_lookup_regs':
intel_cacheinfo.c:(.cpuinit.text+0xa69): undefined reference to `cpu_info'
intel_cacheinfo.c:(.cpuinit.text+0xaf3): undefined reference to `cpu_info'
arch/x86/built-in.o: In function `get_cpu_leaves':
intel_cacheinfo.c:(.cpuinit.text+0xd10): undefined reference to `cpu_info'
intel_cacheinfo.c:(.cpuinit.text+0xe3b): undefined reference to `cpu_llc_shared_map'
intel_cacheinfo.c:(.cpuinit.text+0xf28): undefined reference to `cpu_sibling_map'
arch/x86/built-in.o: In function `init_intel_cacheinfo':
(.cpuinit.text+0x13dd): undefined reference to `cpu_llc_id'
arch/x86/built-in.o: In function `init_intel_cacheinfo':
(.cpuinit.text+0x13fc): undefined reference to `cpu_llc_id'
arch/x86/built-in.o: In function `detect_extended_topology':
(.cpuinit.text+0x1502): undefined reference to `smp_num_siblings'
arch/x86/built-in.o: In function `detect_extended_topology':
(.cpuinit.text+0x15a8): undefined reference to `smp_num_siblings'
arch/x86/built-in.o: In function `detect_ht':
(.cpuinit.text+0x183b): undefined reference to `smp_num_siblings'
arch/x86/built-in.o: In function `detect_ht':
(.cpuinit.text+0x18a7): undefined reference to `smp_num_siblings'
arch/x86/built-in.o: In function `detect_ht':
(.cpuinit.text+0x18bc): undefined reference to `smp_num_siblings'
arch/x86/built-in.o:(.cpuinit.text+0x1911): more undefined references to `smp_num_siblings' follow
arch/x86/built-in.o: In function `init_amd':
amd.c:(.cpuinit.text+0x293a): undefined reference to `cpu_llc_id'
amd.c:(.cpuinit.text+0x298a): undefined reference to `smp_num_siblings'
amd.c:(.cpuinit.text+0x29f1): undefined reference to `cpu_llc_id'
amd.c:(.cpuinit.text+0x2a4e): undefined reference to `cpu_llc_id'
arch/x86/built-in.o: In function `mce_reenable_cpu':
mce.c:(.cpuinit.text+0x2e14): undefined reference to `cpu_info'
arch/x86/built-in.o: In function `mce_disable_cpu':
mce.c:(.cpuinit.text+0x2e72): undefined reference to `cpu_info'
arch/x86/built-in.o: In function `thermal_throttle_add_dev':
therm_throt.c:(.cpuinit.text+0x35a1): undefined reference to `cpu_info'
arch/x86/built-in.o: In function `setup_APIC_timer':
apic.c:(.cpuinit.text+0x399b): undefined reference to `cpu_info'
arch/x86/built-in.o: In function `saved_magic':
(.data+0x43a0): undefined reference to `native_smp_prepare_boot_cpu'
arch/x86/built-in.o: In function `saved_magic':
(.data+0x43a8): undefined reference to `native_smp_prepare_cpus'
arch/x86/built-in.o: In function `saved_magic':
(.data+0x43b0): undefined reference to `native_smp_cpus_done'
arch/x86/built-in.o: In function `saved_magic':
(.data+0x43c8): undefined reference to `native_cpu_up'
arch/x86/built-in.o: In function `saved_magic':
(.data+0x43d0): undefined reference to `native_cpu_disable'
arch/x86/built-in.o: In function `saved_magic':
(.data+0x43d8): undefined reference to `native_cpu_die'
arch/x86/built-in.o: In function `saved_magic':
(.data+0x43e0): undefined reference to `native_play_dead'
kernel/built-in.o: In function `cpu_smt_mask':
bfs.c:(.text+0x283d6): undefined reference to `cpu_sibling_map'
kernel/built-in.o:(.data+0x35f8): undefined reference to `cpu_coregroup_mask'
arch/x86/lib/lib.a(delay.o): In function `__const_udelay':
(.text+0x45): undefined reference to `cpu_info'
arch/x86/lib/lib.a(delay.o): In function `__udelay':
(.text+0x7c): undefined reference to `cpu_info'
arch/x86/lib/lib.a(delay.o): In function `__ndelay':
(.text+0xa9): undefined reference to `cpu_info'
lib/built-in.o: In function `cpu_rmap_update':
(.text+0x101e4): undefined reference to `cpu_sibling_map'
lib/built-in.o: In function `cpu_rmap_update':
(.text+0x101eb): undefined reference to `cpu_core_map'
drivers/built-in.o: In function `acpi_processor_set_throttling_ptc':
processor_throttling.c:(.text+0x5bc05): undefined reference to `cpu_info'
processor_throttling.c:(.text+0x5bc12): undefined reference to `cpu_info'
drivers/built-in.o: In function `acpi_processor_get_throttling_ptc':
processor_throttling.c:(.text+0x5c1d9): undefined reference to `cpu_info'
processor_throttling.c:(.text+0x5c1e6): undefined reference to `cpu_info'
drivers/built-in.o: In function `acpi_processor_get_power_info':
processor_idle.c:(.text+0x5cc4b): undefined reference to `cpu_info'
drivers/built-in.o:processor_thermal.c:(.text+0x5d89f): more undefined references to `cpu_info' follow
drivers/built-in.o: In function `cpu_release_store':
cpu.c:(.text+0xaac97): undefined reference to `arch_cpu_release'
drivers/built-in.o: In function `cpu_probe_store':
cpu.c:(.text+0xaaca7): undefined reference to `arch_cpu_probe'
drivers/built-in.o: In function `show_core_cpumask_list':
topology.c:(.text+0xac729): undefined reference to `cpu_core_map'
drivers/built-in.o: In function `show_core_cpumask':
topology.c:(.text+0xac749): undefined reference to `cpu_core_map'
drivers/built-in.o: In function `show_thread_cpumask_list':
topology.c:(.text+0xac769): undefined reference to `cpu_sibling_map'
drivers/built-in.o: In function `show_thread_cpumask':
topology.c:(.text+0xac789): undefined reference to `cpu_sibling_map'
drivers/built-in.o: In function `show_core_id':
topology.c:(.text+0xac7b0): undefined reference to `cpu_info'
drivers/built-in.o: In function `show_physical_package_id':
topology.c:(.text+0xac7f0): undefined reference to `cpu_info'
drivers/built-in.o: In function `acpi_cpufreq_cpu_init':
acpi-cpufreq.c:(.text+0x1a07ce): undefined reference to `cpu_info'
acpi-cpufreq.c:(.text+0x1a0963): undefined reference to `cpu_core_map'
drivers/built-in.o: In function `store_online':
cpu.c:(.ref.text+0x194d): undefined reference to `cpu_hotplug_driver_lock'
cpu.c:(.ref.text+0x195d): undefined reference to `cpu_hotplug_driver_unlock'
cpu.c:(.ref.text+0x1998): undefined reference to `cpu_hotplug_driver_unlock'
cpu.c:(.ref.text+0x19d1): undefined reference to `cpu_hotplug_driver_unlock'
drivers/built-in.o: In function `acpi_processor_set_pdc':
(.cpuinit.text+0xa): undefined reference to `cpu_info'
drivers/built-in.o: In function `acpi_processor_set_pdc':
(.cpuinit.text+0xdf): undefined reference to `cpu_info'
drivers/built-in.o: In function `coretemp_get_pdev':
coretemp.c:(.cpuinit.text+0x91b): undefined reference to `cpu_info'
drivers/built-in.o: In function `coretemp_add_core':
coretemp.c:(.cpuinit.text+0x9a7): undefined reference to `cpu_info'
coretemp.c:(.cpuinit.text+0xa52): undefined reference to `cpu_info'
drivers/built-in.o:coretemp.c:(.cpuinit.text+0xe50): more undefined references to `cpu_info' follow
drivers/built-in.o: In function `coretemp_cpu_callback':
coretemp.c:(.cpuinit.text+0x10cd): undefined reference to `cpu_sibling_map'
coretemp.c:(.cpuinit.text+0x1187): undefined reference to `cpu_info'
```Obviously, I'm missing a dependency. I can't find any clues as to what that dependency might be.

What dependency(ies) will provide:```
__inquire_remote_apic prefill_possible_map cpu_llc_shared_map smp_num_siblings cpu_llc_id native_smp_prepare_boot_cpu native_smp_prepare_cpus native_smp_cpus_done native_cpu_up native_cpu_disable native_cpu_die native_play_dead cpu_coregroup_mask __udelay __ndelay arch_cpu_release arch_cpu_probe cpu_core_map cpu_hotplug_driver_lock cpu_hotplug_driver_unlock cpu_sibling_map cpu_info
```

---

### Post by quequotion on 2013-02-03
Can someone at least tell me how to debug this myself?

I've gone over and over the source code; all the definitions are there and these "undefined references" aren't even in the files listed in the error.....
Kernel configuration checks out; not using any weird cflags.

Why is this compile failing to link arch/x86/built-in.o, kernel/built-in.o, and drivers/built-in.o?

---

