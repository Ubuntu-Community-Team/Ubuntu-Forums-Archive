---
title: "System crash Ubuntu 14.04 detected hard LOCKUP"
date: 2016-06-15
forum: General Help
---

### Post by shota2 on 2016-06-15
Hi all
plz help I have problem My system have crashed several times when played games
Here is part of kern.log at exact time when last time OS was crashed
can someone help me to detect where is the problem, is it in the hardware and if so which part of hard is broken, maybe video card or snd card? or is it some kernel BUG?
Thank you 
```

Jun 15 22:33:39 shotalinux kernel: [ 7904.858877] ------------[ cut here ]------------
Jun 15 22:33:39 shotalinux kernel: [ 7904.858887] WARNING: CPU: 4 PID: 0 at /build/linux-lts-wily-an0LDU/linux-lts-wily-4.2.0/kernel/watchdog.c:311 watchdog_overflow_callback+0x8b/0xb0()
Jun 15 22:33:39 shotalinux kernel: [ 7904.858889] Watchdog detected hard LOCKUP on cpu 4
Jun 15 22:33:39 shotalinux kernel: [ 7904.858890] Modules linked in: rfcomm bnep bluetooth nvidia_modeset(POE) snd_hda_codec_hdmi nvidia(POE) snd_hda_codec_realtek snd_hda_codec_generic snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep gspca_zc3xx gspca_main kvm_intel videodev media kvm snd_pcm parport_pc snd_seq_midi snd_seq_midi_event drm snd_rawmidi snd_seq snd_seq_device snd_timer ppdev snd f71882fg soundcore coretemp gpio_ich input_leds i7core_edac shpchp serio_raw lp i5500_temp edac_core mac_hid lpc_ich parport pata_acpi uas usb_storage hid_generic usbhid hid e1000e firewire_ohci ahci firewire_core ptp libahci crc_itu_t pata_jmicron pps_core
Jun 15 22:33:39 shotalinux kernel: [ 7904.858928] CPU: 4 PID: 0 Comm: swapper/4 Tainted: P           OE   4.2.0-38-generic #45~14.04.1-Ubuntu
Jun 15 22:33:39 shotalinux kernel: [ 7904.858930] Hardware name: HP-Pavilion NJ062AA-ABA m9650f/TRUCKEE, BIOS 5.28    04/09/2010
Jun 15 22:33:39 shotalinux kernel: [ 7904.858932]  0000000000000000 ffff8801a9305b00 ffffffff817bb69b ffff8801a9305b50
Jun 15 22:33:39 shotalinux kernel: [ 7904.858935]  ffffffff81aa31b0 ffff8801a9305b40 ffffffff8107992a 0000000000000000
Jun 15 22:33:39 shotalinux kernel: [ 7904.858938]  ffff8801a79a0000 0000000000000000 0000000000000000 ffff8801a9305c40
Jun 15 22:33:39 shotalinux kernel: [ 7904.858940] Call Trace:
Jun 15 22:33:39 shotalinux kernel: [ 7904.858942]  <NMI>  [<ffffffff817bb69b>] dump_stack+0x63/0x81
Jun 15 22:33:39 shotalinux kernel: [ 7904.858950]  [<ffffffff8107992a>] warn_slowpath_common+0x8a/0xc0
Jun 15 22:33:39 shotalinux kernel: [ 7904.858953]  [<ffffffff810799a6>] warn_slowpath_fmt+0x46/0x50
Jun 15 22:33:39 shotalinux kernel: [ 7904.858956]  [<ffffffff8112c00b>] watchdog_overflow_callback+0x8b/0xb0
Jun 15 22:33:39 shotalinux kernel: [ 7904.858959]  [<ffffffff8116f1bc>] __perf_event_overflow+0x8c/0x1c0
Jun 15 22:33:39 shotalinux kernel: [ 7904.858961]  [<ffffffff8116fcc4>] perf_event_overflow+0x14/0x20
Jun 15 22:33:39 shotalinux kernel: [ 7904.858965]  [<ffffffff8103442e>] intel_pmu_handle_irq+0x1ce/0x450
Jun 15 22:33:39 shotalinux kernel: [ 7904.858969]  [<ffffffff8102b006>] perf_event_nmi_handler+0x26/0x40
Jun 15 22:33:39 shotalinux kernel: [ 7904.858973]  [<ffffffff810195dd>] nmi_handle+0x7d/0x120
Jun 15 22:33:39 shotalinux kernel: [ 7904.858975]  [<ffffffff81019b32>] default_do_nmi+0x42/0x110
Jun 15 22:33:39 shotalinux kernel: [ 7904.858977]  [<ffffffff81019ce5>] do_nmi+0xe5/0x160
Jun 15 22:33:39 shotalinux kernel: [ 7904.858981]  [<ffffffff817c4e11>] end_repeat_nmi+0x1a/0x1e
Jun 15 22:33:39 shotalinux kernel: [ 7904.858985]  [<ffffffff810ba372>] ? cpu_startup_entry+0x132/0x360
Jun 15 22:33:39 shotalinux kernel: [ 7904.858987]  [<ffffffff810ba372>] ? cpu_startup_entry+0x132/0x360
Jun 15 22:33:39 shotalinux kernel: [ 7904.858989]  [<ffffffff810ba372>] ? cpu_startup_entry+0x132/0x360
Jun 15 22:33:39 shotalinux kernel: [ 7904.858991]  <<EOE>>  [<ffffffff8104c455>] start_secondary+0x175/0x1a0
Jun 15 22:33:39 shotalinux kernel: [ 7904.858996] ---[ end trace 08db66c8a85db157 ]---
Jun 15 22:33:39 shotalinux kernel: [ 7906.180397] ------------[ cut here ]------------
Jun 15 22:33:39 shotalinux kernel: [ 7906.180404] WARNING: CPU: 2 PID: 0 at /build/linux-lts-wily-an0LDU/linux-lts-wily-4.2.0/kernel/watchdog.c:311 watchdog_overflow_callback+0x8b/0xb0()
Jun 15 22:33:39 shotalinux kernel: [ 7906.180406] Watchdog detected hard LOCKUP on cpu 2
Jun 15 22:33:39 shotalinux kernel: [ 7906.180407] Modules linked in: rfcomm bnep bluetooth nvidia_modeset(POE) snd_hda_codec_hdmi nvidia(POE) snd_hda_codec_realtek snd_hda_codec_generic snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep gspca_zc3xx gspca_main kvm_intel videodev media kvm snd_pcm parport_pc snd_seq_midi snd_seq_midi_event drm snd_rawmidi snd_seq snd_seq_device snd_timer ppdev snd f71882fg soundcore coretemp gpio_ich input_leds i7core_edac shpchp serio_raw lp i5500_temp edac_core mac_hid lpc_ich parport pata_acpi uas usb_storage hid_generic usbhid hid e1000e firewire_ohci ahci firewire_core ptp libahci crc_itu_t pata_jmicron pps_core
Jun 15 22:33:39 shotalinux kernel: [ 7906.180443] CPU: 2 PID: 0 Comm: swapper/2 Tainted: P        W  OE   4.2.0-38-generic #45~14.04.1-Ubuntu
Jun 15 22:33:39 shotalinux kernel: [ 7906.180445] Hardware name: HP-Pavilion NJ062AA-ABA m9650f/TRUCKEE, BIOS 5.28    04/09/2010
Jun 15 22:33:39 shotalinux kernel: [ 7906.180446]  0000000000000000 ffff8801a9285b00 ffffffff817bb69b ffff8801a9285b50
Jun 15 22:33:39 shotalinux kernel: [ 7906.180449]  ffffffff81aa31b0 ffff8801a9285b40 ffffffff8107992a 0000000000000000
Jun 15 22:33:39 shotalinux kernel: [ 7906.180452]  ffff8801a78c0000 0000000000000000 0000000000000000 ffff8801a9285c40
Jun 15 22:33:39 shotalinux kernel: [ 7906.180454] Call Trace:
Jun 15 22:33:39 shotalinux kernel: [ 7906.180456]  <NMI>  [<ffffffff817bb69b>] dump_stack+0x63/0x81
Jun 15 22:33:39 shotalinux kernel: [ 7906.180463]  [<ffffffff8107992a>] warn_slowpath_common+0x8a/0xc0
Jun 15 22:33:39 shotalinux kernel: [ 7906.180465]  [<ffffffff810799a6>] warn_slowpath_fmt+0x46/0x50
Jun 15 22:33:39 shotalinux kernel: [ 7906.180468]  [<ffffffff8112c00b>] watchdog_overflow_callback+0x8b/0xb0
Jun 15 22:33:39 shotalinux kernel: [ 7906.180471]  [<ffffffff8116f1bc>] __perf_event_overflow+0x8c/0x1c0
Jun 15 22:33:39 shotalinux kernel: [ 7906.180473]  [<ffffffff8116fcc4>] perf_event_overflow+0x14/0x20
Jun 15 22:33:39 shotalinux kernel: [ 7906.180477]  [<ffffffff8103442e>] intel_pmu_handle_irq+0x1ce/0x450
Jun 15 22:33:39 shotalinux kernel: [ 7906.180481]  [<ffffffff8102b006>] perf_event_nmi_handler+0x26/0x40
Jun 15 22:33:39 shotalinux kernel: [ 7906.180484]  [<ffffffff810195dd>] nmi_handle+0x7d/0x120
Jun 15 22:33:39 shotalinux kernel: [ 7906.180487]  [<ffffffff81019b32>] default_do_nmi+0x42/0x110
Jun 15 22:33:39 shotalinux kernel: [ 7906.180489]  [<ffffffff81019ce5>] do_nmi+0xe5/0x160
Jun 15 22:33:39 shotalinux kernel: [ 7906.180492]  [<ffffffff817c4e11>] end_repeat_nmi+0x1a/0x1e
Jun 15 22:33:39 shotalinux kernel: [ 7906.180497]  [<ffffffff810f17ba>] ? tick_check_broadcast_expired+0x1a/0x20
Jun 15 22:33:39 shotalinux kernel: [ 7906.180499]  [<ffffffff810f17ba>] ? tick_check_broadcast_expired+0x1a/0x20
Jun 15 22:33:39 shotalinux kernel: [ 7906.180502]  [<ffffffff810f17ba>] ? tick_check_broadcast_expired+0x1a/0x20
Jun 15 22:33:39 shotalinux kernel: [ 7906.180503]  <<EOE>>  [<ffffffff810ba372>] cpu_startup_entry+0x132/0x360
Jun 15 22:33:39 shotalinux kernel: [ 7906.180509]  [<ffffffff8104c455>] start_secondary+0x175/0x1a0
Jun 15 22:33:39 shotalinux kernel: [ 7906.180511] ---[ end trace 08db66c8a85db158 ]---
Jun 15 22:33:39 shotalinux kernel: [ 7907.262969] sysrq: SysRq : This sysrq operation is disabled.
Jun 15 22:33:39 shotalinux kernel: [ 7907.328629] ------------[ cut here ]------------
Jun 15 22:33:39 shotalinux kernel: [ 7907.328636] WARNING: CPU: 6 PID: 0 at /build/linux-lts-wily-an0LDU/linux-lts-wily-4.2.0/kernel/watchdog.c:311 watchdog_overflow_callback+0x8b/0xb0()
Jun 15 22:33:39 shotalinux kernel: [ 7907.328638] Watchdog detected hard LOCKUP on cpu 6
Jun 15 22:33:39 shotalinux kernel: [ 7907.328639] Modules linked in: rfcomm bnep bluetooth nvidia_modeset(POE) snd_hda_codec_hdmi nvidia(POE) snd_hda_codec_realtek snd_hda_codec_generic snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep gspca_zc3xx gspca_main kvm_intel videodev media kvm snd_pcm parport_pc snd_seq_midi snd_seq_midi_event drm snd_rawmidi snd_seq snd_seq_device snd_timer ppdev snd f71882fg soundcore coretemp gpio_ich input_leds i7core_edac shpchp serio_raw lp i5500_temp edac_core mac_hid lpc_ich parport pata_acpi uas usb_storage hid_generic usbhid hid e1000e firewire_ohci ahci firewire_core ptp libahci crc_itu_t pata_jmicron pps_core
Jun 15 22:33:39 shotalinux kernel: [ 7907.328675] CPU: 6 PID: 0 Comm: swapper/6 Tainted: P        W  OE   4.2.0-38-generic #45~14.04.1-Ubuntu
Jun 15 22:33:39 shotalinux kernel: [ 7907.328676] Hardware name: HP-Pavilion NJ062AA-ABA m9650f/TRUCKEE, BIOS 5.28    04/09/2010
Jun 15 22:33:39 shotalinux kernel: [ 7907.328678]  0000000000000000 ffff8801a9385b00 ffffffff817bb69b ffff8801a9385b50
Jun 15 22:33:39 shotalinux kernel: [ 7907.328681]  ffffffff81aa31b0 ffff8801a9385b40 ffffffff8107992a 0000000000000000
Jun 15 22:33:39 shotalinux kernel: [ 7907.328684]  ffff8801a7a78000 0000000000000000 0000000000000000 ffff8801a9385c40
Jun 15 22:33:39 shotalinux kernel: [ 7907.328687] Call Trace:
Jun 15 22:33:39 shotalinux kernel: [ 7907.328688]  <NMI>  [<ffffffff817bb69b>] dump_stack+0x63/0x81
Jun 15 22:33:39 shotalinux kernel: [ 7907.328695]  [<ffffffff8107992a>] warn_slowpath_common+0x8a/0xc0
Jun 15 22:33:39 shotalinux kernel: [ 7907.328697]  [<ffffffff810799a6>] warn_slowpath_fmt+0x46/0x50
Jun 15 22:33:39 shotalinux kernel: [ 7907.328700]  [<ffffffff8112c00b>] watchdog_overflow_callback+0x8b/0xb0
Jun 15 22:33:39 shotalinux kernel: [ 7907.328703]  [<ffffffff8116f1bc>] __perf_event_overflow+0x8c/0x1c0
Jun 15 22:33:39 shotalinux kernel: [ 7907.328705]  [<ffffffff8116fcc4>] perf_event_overflow+0x14/0x20
Jun 15 22:33:39 shotalinux kernel: [ 7907.328708]  [<ffffffff8103442e>] intel_pmu_handle_irq+0x1ce/0x450
Jun 15 22:33:39 shotalinux kernel: [ 7907.328713]  [<ffffffff8102b006>] perf_event_nmi_handler+0x26/0x40
Jun 15 22:33:39 shotalinux kernel: [ 7907.328715]  [<ffffffff810195dd>] nmi_handle+0x7d/0x120
Jun 15 22:33:39 shotalinux kernel: [ 7907.328718]  [<ffffffff81019b32>] default_do_nmi+0x42/0x110
Jun 15 22:33:39 shotalinux kernel: [ 7907.328720]  [<ffffffff81019ce5>] do_nmi+0xe5/0x160
Jun 15 22:33:39 shotalinux kernel: [ 7907.328723]  [<ffffffff817c4e11>] end_repeat_nmi+0x1a/0x1e
Jun 15 22:33:39 shotalinux kernel: [ 7907.328727]  [<ffffffff810f17ba>] ? tick_check_broadcast_expired+0x1a/0x20
Jun 15 22:33:39 shotalinux kernel: [ 7907.328730]  [<ffffffff810f17ba>] ? tick_check_broadcast_expired+0x1a/0x20
Jun 15 22:33:39 shotalinux kernel: [ 7907.328732]  [<ffffffff810f17ba>] ? tick_check_broadcast_expired+0x1a/0x20
Jun 15 22:33:39 shotalinux kernel: [ 7907.328734]  <<EOE>>  [<ffffffff810ba372>] cpu_startup_entry+0x132/0x360
Jun 15 22:33:39 shotalinux kernel: [ 7907.328739]  [<ffffffff8104c455>] start_secondary+0x175/0x1a0
Jun 15 22:33:39 shotalinux kernel: [ 7907.328741] ---[ end trace 08db66c8a85db159 ]---
Jun 15 22:33:39 shotalinux kernel: [ 7907.390981] sysrq: SysRq : This sysrq operation is disabled.
Jun 15 22:33:39 shotalinux kernel: [ 7907.911030] sysrq: SysRq : This sysrq operation is disabled.
Jun 15 22:33:39 shotalinux kernel: [ 7908.071046] sysrq: SysRq : Emergency Sync
Jun 15 22:33:39 shotalinux kernel: [ 7908.082374] Emergency Sync complete

```

---

### Post by KenUBF on 2016-06-15
Hi Shota2,

My recommendation would be for you to try a different version of the kernel. It looks like you are using version 4.2? If you have an earlier version of the kernel have you tried reverting back to the older one? You could also try the newest version of the kernel, which is 4.4 (for the long term support version). Here is a tutorial on how to do that: [https://www.linux.com/blog/how-installupgrade-linux-kernel-434-ubuntulinux-mint-systems](https://www.linux.com/blog/how-installupgrade-linux-kernel-434-ubuntulinux-mint-systems)     Just change the kernel version numbers for the one you want to download. Good luck! By the way, it is good practice to keep at least one extra kernel on your system just in case any new one you upgrade to becomes unstable on your system for any reason.

---

### Post by gordintoronto on 2016-06-16
What CPU? What motherboard?

---

### Post by shota2 on 2016-06-17
Hi thank you for reply
I tryed install new 4.4.0-24 kernel, hardware info is: Intel(R) Core(TM) i7 CPU 920, HP-Pavilion NJ062AA-ABA m9650f, NVIDIA GeForce GTX 560 SE
the system crash occures when I am playing video games I think it is video adapter problem, maybe its broken and need change, and your opinion is very interesting for me, here is last part of kern logs, I have done alt+sysrq REISUB after crash
```

Jun 17 21:39:22 shotalinux kernel: [  447.597650] audit: type=1400 audit(1466185162.104:72): apparmor="STATUS" operation="profile_replace" pro
file="unconfined" name="/usr/sbin/cupsd" pid=3474 comm="apparmor_parser"
Jun 17 21:39:22 shotalinux kernel: [  447.598575] audit: type=1400 audit(1466185162.104:73): apparmor="STATUS" operation="profile_replace" pro
file="unconfined" name="/usr/sbin/cupsd" pid=3474 comm="apparmor_parser"
Jun 17 21:51:17 shotalinux kernel: [ 1163.235461] perf interrupt took too long (2501 > 2500), lowering kernel.perf_event_max_sample_rate to 50
000
Jun 17 22:24:50 shotalinux kernel: [ 3176.206473] NVRM: GPU at PCI:0000:06:00: GPU-925100e7-2fc0-2073-6f6c-4a75f0a37d9f
Jun 17 22:24:50 shotalinux kernel: [ 3176.206478] NVRM: Xid (PCI:0000:06:00): 56, CMDre 00000001 000000c0 00010045 00000007 00000000
Jun 17 22:27:28 shotalinux kernel: [ 3334.008683] NVRM: Xid (PCI:0000:06:00): 56, CMDre 00000001 00000094 00010042 00000004 00000084
Jun 17 22:28:01 shotalinux kernel: [ 3367.132184] NVRM: Xid (PCI:0000:06:00): 56, CMDre 00000001 00000094 00010042 00000007 00000000
Jun 17 22:28:44 shotalinux kernel: [ 3409.735621] NVRM: Xid (PCI:0000:06:00): 56, CMDre 00000001 000000c0 00010045 00000007 00000000
Jun 17 22:28:47 shotalinux kernel: [ 3413.331293] NVRM: Xid (PCI:0000:06:00): 56, CMDre 00000001 00000094 00010042 00000007 00000000
Jun 17 22:28:49 shotalinux kernel: [ 3414.876415] NVRM: Xid (PCI:0000:06:00): 56, CMDre 00000001 000000c0 00010048 00000007 00000000
Jun 17 22:29:54 shotalinux kernel: [ 3479.683019] NVRM: Xid (PCI:0000:06:00): 56, CMDre 00000001 00000094 00010042 00000004 00000084
Jun 17 22:30:31 shotalinux kernel: [ 3516.644774] NVRM: Xid (PCI:0000:06:00): 56, CMDre 00000001 00000094 00010042 00000004 00000084
Jun 17 22:30:42 shotalinux kernel: [ 3528.276332] NVRM: Xid (PCI:0000:06:00): 56, CMDre 00000001 000000c0 00010045 00000007 00000000
Jun 17 22:31:07 shotalinux kernel: [ 3553.287856] NVRM: Xid (PCI:0000:06:00): 56, CMDre 00000001 00000094 00010042 00000004 00000084
Jun 17 22:31:23 shotalinux kernel: [ 3568.639914] NVRM: Xid (PCI:0000:06:00): 56, CMDre 00000001 000000c0 00010048 00000007 00000000
Jun 17 22:32:13 shotalinux kernel: [ 3618.785145] NVRM: Xid (PCI:0000:06:00): 56, CMDre 00000001 000000c0 00010048 00000007 00000000
Jun 17 22:32:30 shotalinux kernel: [ 3635.905952] NVRM: Xid (PCI:0000:06:00): 56, CMDre 00000001 000000c0 00010045 00000007 00000000
Jun 17 22:32:38 shotalinux kernel: [ 3644.195952] NVRM: Xid (PCI:0000:06:00): 56, CMDre 00000001 00000094 00010042 00000007 00000000
Jun 17 22:34:12 shotalinux kernel: [ 3737.854565] NVRM: Xid (PCI:0000:06:00): 56, CMDre 00000001 00000094 00010042 00000007 00000000
Jun 17 22:35:03 shotalinux kernel: [ 3789.023940] NVRM: Xid (PCI:0000:06:00): 56, CMDre 00000001 00000094 00010042 00000004 00000084
Jun 17 22:35:33 shotalinux kernel: [ 3819.357591] NVRM: Xid (PCI:0000:06:00): 56, CMDre 00000001 000000c0 00010045 00000007 00000000
Jun 17 22:35:50 shotalinux kernel: [ 3836.131288] NVRM: Xid (PCI:0000:06:00): 56, CMDre 00000001 000000c0 00010045 00000007 00000000
Jun 17 22:36:41 shotalinux kernel: [ 3886.654351] NVRM: Xid (PCI:0000:06:00): 56, CMDre 00000001 00000094 00010042 00000007 00000000
Jun 17 22:36:41 shotalinux kernel: [ 3886.792424] NVRM: Xid (PCI:0000:06:00): 56, CMDre 00000001 00000094 00010042 00000007 00000000
Jun 17 22:37:01 shotalinux kernel: [ 3907.244845] NVRM: Xid (PCI:0000:06:00): 56, CMDre 00000001 00000094 00010042 00000007 00000000
Jun 17 22:37:13 shotalinux kernel: [ 3918.408423] NVRM: Xid (PCI:0000:06:00): 56, CMDre 00000001 000000c0 00010048 00000007 00000000
Jun 17 22:37:16 shotalinux kernel: [ 3922.144467] NVRM: Xid (PCI:0000:06:00): 56, CMDre 00000001 000000c0 00010048 00000007 00000000
Jun 17 22:37:54 shotalinux kernel: [ 3959.798019] NVRM: Xid (PCI:0000:06:00): 56, CMDre 00000001 00000094 00010042 00000007 00000000
Jun 17 22:38:03 shotalinux kernel: [ 3969.133342] NVRM: Xid (PCI:0000:06:00): 56, CMDre 00000001 00000094 00010042 00000007 00000000
Jun 17 22:38:36 shotalinux kernel: [ 4002.038802] NVRM: Xid (PCI:0000:06:00): 56, CMDre 00000001 000000c0 00010045 00000007 00000000
Jun 17 22:39:17 shotalinux kernel: [ 4042.650352] NVRM: Xid (PCI:0000:06:00): 56, CMDre 00000001 000000c0 00010045 00000007 00000000
Jun 17 22:39:31 shotalinux kernel: [ 4057.197700] NVRM: Xid (PCI:0000:06:00): 56, CMDre 00000001 00000094 00010042 00000004 00000084
Jun 17 22:39:34 shotalinux kernel: [ 4059.897066] NVRM: Xid (PCI:0000:06:00): 56, CMDre 00000001 00000094 00010042 00000004 00000084
Jun 17 22:39:37 shotalinux kernel: [ 4063.216427] NVRM: Xid (PCI:0000:06:00): 56, CMDre 00000001 00000094 00010042 00000004 00000084
Jun 17 22:41:30 shotalinux kernel: [ 4175.512810] NVRM: Xid (PCI:0000:06:00): 56, CMDre 00000001 00000094 00010042 00000007 00000000
Jun 17 22:41:36 shotalinux kernel: [ 4181.822048] NVRM: Xid (PCI:0000:06:00): 56, CMDre 00000001 00000094 00010042 00000004 00000084
Jun 17 22:41:43 shotalinux kernel: [ 4189.347350] NVRM: Xid (PCI:0000:06:00): 56, CMDre 00000001 00000094 00010042 00000004 00000084
Jun 17 22:41:50 shotalinux kernel: [ 4196.073892] NVRM: Xid (PCI:0000:06:00): 56, CMDre 00000001 000000c0 00010045 00000007 00000000
Jun 17 22:53:31 shotalinux kernel: [ 4896.482637] NVRM: Xid (PCI:0000:06:00): 56, CMDre 00000001 00000094 00010042 00000007 00000000
Jun 17 22:56:55 shotalinux kernel: [ 5100.605068] NVRM: Xid (PCI:0000:06:00): 56, CMDre 00000001 00000094 00010042 00000004 00000084
Jun 17 22:58:29 shotalinux kernel: [ 5194.747304] NVRM: Xid (PCI:0000:06:00): 56, CMDre 00000001 00000094 00010042 00000004 00000084
Jun 17 23:02:20 shotalinux kernel: [ 5426.063143] NVRM: Xid (PCI:0000:06:00): 56, CMDre 00000001 00000094 00010042 00000004 00000084
Jun 17 23:07:10 shotalinux kernel: [ 5716.245692] sysrq: SysRq : This sysrq operation is disabled.
Jun 17 23:07:10 shotalinux kernel: [ 5716.357696] sysrq: SysRq : This sysrq operation is disabled.
Jun 17 23:07:11 shotalinux kernel: [ 5716.669703] sysrq: SysRq : This sysrq operation is disabled.
Jun 17 23:07:11 shotalinux kernel: [ 5716.813706] sysrq: SysRq : Emergency Sync
Jun 17 23:07:11 shotalinux kernel: [ 5716.819281] Emergency Sync complete
Jun 17 23:07:11 shotalinux kernel: [ 5717.021712] sysrq: SysRq : Emergency Remount R/O
Jun 17 23:07:47 shotalinux kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun 17 23:07:47 shotalinux kernel: [    0.000000] Initializing cgroup subsys cpu
Jun 17 23:07:47 shotalinux kernel: [    0.000000] Initializing cgroup subsys cpuacct

```

---

### Post by shota2 on 2016-06-18
Can someone help or move this topic in the hardware section? thank you ;)

---

