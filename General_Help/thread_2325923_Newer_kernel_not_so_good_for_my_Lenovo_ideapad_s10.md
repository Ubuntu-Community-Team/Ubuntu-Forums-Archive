---
title: "Newer kernel not so good for my Lenovo ideapad s10e"
date: 2016-05-26
forum: General Help
---

### Post by davide3 on 2016-05-26
That's what's happening at boot time:
Could you give me any advice?

Tnx

```

[    3.646422] WARNING: CPU: 0 PID: 6 at /build/linux-xgbPFL/linux-4.4.0/drivers/gpu/drm/i915/intel_fbdev.c:406 intel_fb_initial_config+0x2e4/0x5f0 [i915]()
[    3.646428] WARN_ON(!encoder->crtc)
[    3.646432] Modules linked in:
[    3.646437]  i915(+) tg3 psmouse i2c_algo_bit drm_kms_helper ptp syscopyarea sysfillrect pata_acpi sysimgblt fb_sys_fops drm pps_core wmi video fjes
[    3.646475] CPU: 0 PID: 6 Comm: kworker/u4:0 Not tainted 4.4.0-22-generic #40-Ubuntu
[    3.646482] Hardware name: LENOVO                           41875QG         /Kuril                           , BIOS 14CNA0WW   10/11/2010
[    3.646495] Workqueue: events_unbound async_run_entry_fn
[    3.646501]  c1abf967 3d26bd4c 00000286 f6323d0c c139dccf f6323d4c f8aef8e4 f6323d3c
[    3.646518]  c106e997 f8afa45c f6323d6c 00000006 f8aef8e4 00000196 f8a9f444 f8a9f444
[    3.646533]  00000000 00000001 00000001 f6323d58 c106ea0e 00000009 f6323d4c f8afa45c
[    3.646549] Call Trace:
[    3.646564]  [<c139dccf>] dump_stack+0x58/0x79
[    3.646575]  [<c106e997>] warn_slowpath_common+0x87/0xc0
[    3.646692]  [<f8a9f444>] ? intel_fb_initial_config+0x2e4/0x5f0 [i915]
[    3.646809]  [<f8a9f444>] ? intel_fb_initial_config+0x2e4/0x5f0 [i915]
[    3.646818]  [<c106ea0e>] warn_slowpath_fmt+0x3e/0x60
[    3.646935]  [<f8a9f444>] intel_fb_initial_config+0x2e4/0x5f0 [i915]
[    3.647054]  [<f8a9f160>] ? intel_crtc_fb_gamma_get+0x40/0x40 [i915]
[    3.647086]  [<f85e048f>] drm_setup_crtcs+0x21f/0xa90 [drm_kms_helper]
[    3.647099]  [<c1095d67>] ? ttwu_do_wakeup+0x17/0x110
[    3.647108]  [<c1096849>] ? try_to_wake_up+0x39/0x360
[    3.647118]  [<c1096b84>] ? wake_up_process+0x14/0x20
[    3.647147]  [<f85e0fac>] drm_fb_helper_initial_config+0xbc/0x400 [drm_kms_helper]
[    3.647161]  [<c10a8719>] ? pick_next_task_fair+0x459/0x520
[    3.647286]  [<f8aa0329>] intel_fbdev_initial_config+0x19/0x20 [i915]
[    3.647291] [drm] Initialized i915 1.6.0 20151010 for 0000:00:02.0 on minor 0
[    3.647306]  [<c108db3e>] async_run_entry_fn+0x4e/0x170
[    3.647317]  [<c1085cea>] process_one_work+0x12a/0x420
[    3.647328]  [<c1086017>] worker_thread+0x37/0x490
[    3.647337]  [<c1085fe0>] ? process_one_work+0x420/0x420
[    3.647346]  [<c108b4c6>] kthread+0xa6/0xc0
[    3.647358]  [<c17a7d49>] ret_from_kernel_thread+0x21/0x38
[    3.647367]  [<c108b420>] ? kthread_create_on_node+0x170/0x170
[   13.976487] WARNING: CPU: 0 PID: 384 at /build/linux-xgbPFL/linux-4.4.0/drivers/gpu/drm/i915/intel_display.c:11693 intel_plane_atomic_calc_changes+0x549/0x6b0 [i915]()
[   13.976495] WARN_ON(was_visible)
[   13.976500] Modules linked in:
[   13.976506]  snd soundcore ideapad_laptop shpchp sparse_keymap mac_hid ip6t_REJECT nf_reject_ipv6 nf_log_ipv6 xt_hl ip6t_rt nf_conntrack_ipv6 nf_defrag_ipv6 ipt_REJECT nf_reject_ipv4 nf_log_ipv4 nf_log_common xt_LOG xt_limit xt_tcpudp xt_addrtype nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack ip6table_filter ip6_tables nf_conntrack_netbios_ns nf_conntrack_broadcast nf_nat_ftp nf_nat nf_conntrack_ftp nf_conntrack iptable_filter ip_tables x_tables coretemp parport_pc ppdev lp parport autofs4 hid_generic ums_realtek uas usbhid hid usb_storage i915 tg3 psmouse i2c_algo_bit drm_kms_helper ptp syscopyarea sysfillrect pata_acpi sysimgblt fb_sys_fops drm pps_core wmi video fjes
[   13.976638] CPU: 0 PID: 384 Comm: plymouthd Tainted: G        W       4.4.0-22-generic #40-Ubuntu
[   13.976646] Hardware name: LENOVO                           41875QG         /Kuril                           , BIOS 14CNA0WW   10/11/2010
[   13.976654]  c1abf967 0ba32763 00000286 f1d09ca0 c139dccf f1d09ce0 f8aea834 f1d09cd0
[   13.976672]  c106e997 f8af8d3e f1d09d00 00000180 f8aea834 00002dad f8a91f19 f8a91f19
[   13.976689]  00000000 f2272540 f3466000 f1d09cec c106ea0e 00000009 f1d09ce0 f8af8d3e
[   13.976706] Call Trace:
[   13.976725]  [<c139dccf>] dump_stack+0x58/0x79
[   13.976739]  [<c106e997>] warn_slowpath_common+0x87/0xc0
[   13.976859]  [<f8a91f19>] ? intel_plane_atomic_calc_changes+0x549/0x6b0 [i915]
[   13.976970]  [<f8a91f19>] ? intel_plane_atomic_calc_changes+0x549/0x6b0 [i915]
[   13.976985]  [<c106ea0e>] warn_slowpath_fmt+0x3e/0x60
[   13.977093]  [<f8a91f19>] intel_plane_atomic_calc_changes+0x549/0x6b0 [i915]
[   13.977130]  [<f85d5195>] ? drm_plane_helper_check_update+0xc5/0x180 [drm_kms_helper]
[   13.977240]  [<f8a7fca0>] ? intel_check_primary_plane+0x80/0x100 [i915]
[   13.977348]  [<f8a71c65>] intel_plane_atomic_check+0xb5/0x1c0 [i915]
[   13.977384]  [<f85dc451>] drm_atomic_helper_check_planes+0xb1/0x1b0 [drm_kms_helper]
[   13.977497]  [<f8a8c65a>] intel_atomic_check+0x15a/0x6d0 [i915]
[   13.977602]  [<f8a8c500>] ? intel_modeset_pipe_config+0x950/0x950 [i915]
[   13.977677]  [<f886130e>] drm_atomic_check_only+0x1ae/0x600 [drm]
[   13.977744]  [<f885feb9>] ? drm_modeset_lock+0x49/0xd0 [drm]
[   13.977811]  [<f886082c>] ? drm_atomic_set_crtc_for_connector+0x5c/0xe0 [drm]
[   13.977877]  [<f8861776>] drm_atomic_commit+0x16/0x60 [drm]
[   13.977911]  [<f85dede3>] restore_fbdev_mode+0x253/0x290 [drm_kms_helper]
[   13.977976]  [<f885ffd4>] ? drm_modeset_lock_all_ctx+0x94/0xb0 [drm]
[   13.978009]  [<f85e0e47>] drm_fb_helper_restore_fbdev_mode_unlocked+0x27/0x70 [drm_kms_helper]
[   13.978126]  [<f8aa0500>] intel_fbdev_restore_mode+0x20/0x80 [i915]
[   13.978236]  [<f8a94567>] ? intel_modeset_preclose+0x37/0x90 [i915]
[   13.978339]  [<f8a4f621>] ? i915_gem_release+0x21/0xb0 [i915]
[   13.978451]  [<f8acc42d>] i915_driver_lastclose+0xd/0x20 [i915]
[   13.978515]  [<f884489a>] drm_lastclose+0x2a/0x140 [drm]
[   13.978577]  [<f8844c4f>] drm_release+0x29f/0x490 [drm]
[   13.978590]  [<c11dc63f>] __fput+0xcf/0x210
[   13.978599]  [<c11dc7bd>] ____fput+0xd/0x10
[   13.978609]  [<c1089a5f>] task_work_run+0x7f/0xa0
[   13.978620]  [<c1003115>] exit_to_usermode_loop+0xd5/0xe0
[   13.978631]  [<c10039f7>] do_fast_syscall_32+0x147/0x150
[   13.978643]  [<c17a7dd8>] sysenter_past_esp+0x3d/0x61
[   13.978652] ---[ end trace 3fb1c2bdf4a91395 ]---
[   13.979757] ------------[ cut here ]------------
[   13.979800] WARNING: CPU: 0 PID: 384 at /build/linux-xgbPFL/linux-4.4.0/drivers/gpu/drm/drm_atomic_helper.c:725 drm_atomic_helper_update_legacy_modeset_state+0x26a/0x280 [drm_kms_helper]()
[   13.979807] Modules linked in: snd soundcore ideapad_laptop shpchp sparse_keymap mac_hid ip6t_REJECT nf_reject_ipv6 nf_log_ipv6 xt_hl ip6t_rt nf_conntrack_ipv6 nf_defrag_ipv6 ipt_REJECT nf_reject_ipv4 nf_log_ipv4 nf_log_common xt_LOG xt_limit xt_tcpudp xt_addrtype nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack ip6table_filter ip6_tables nf_conntrack_netbios_ns nf_conntrack_broadcast nf_nat_ftp nf_nat nf_conntrack_ftp nf_conntrack iptable_filter ip_tables x_tables coretemp parport_pc ppdev lp parport autofs4 hid_generic ums_realtek uas usbhid hid usb_storage i915 tg3 psmouse i2c_algo_bit drm_kms_helper ptp syscopyarea sysfillrect pata_acpi sysimgblt fb_sys_fops drm pps_core wmi video fjes
[   13.979953] CPU: 0 PID: 384 Comm: plymouthd Tainted: G        W       4.4.0-22-generic #40-Ubuntu
[   13.979961] Hardware name: LENOVO                           41875QG         /Kuril                           , BIOS 14CNA0WW   10/11/2010
[   13.979968]  c1abf967 0ba32763 00000286 f1d09d7c c139dccf 00000000 f85e3f90 f1d09dac
[   13.979986]  c106e997 c19b52a8 00000000 00000180 f85e3f90 000002d5 f85db78a f85db78a
[   13.980002]  f5a3fc00 00000000 f3c3f600 f1d09dbc c106eaa2 00000009 00000000 f1d09de4
[   13.980017] Call Trace:
[   13.980024]  [<c139dccf>] dump_stack+0x58/0x79
[   13.980024]  [<c106e997>] warn_slowpath_common+0x87/0xc0
[   13.980024]  [<f85db78a>] ? drm_atomic_helper_update_legacy_modeset_state+0x26a/0x280 [drm_kms_helper]
[   13.980024]  [<f85db78a>] ? drm_atomic_helper_update_legacy_modeset_state+0x26a/0x280 [drm_kms_helper]
[   13.980024]  [<c106eaa2>] warn_slowpath_null+0x22/0x30
[   13.980024]  [<f85db78a>] drm_atomic_helper_update_legacy_modeset_state+0x26a/0x280 [drm_kms_helper]
[   13.980024]  [<f8a8a4e8>] ? intel_pre_plane_update+0xd8/0x130 [i915]
[   13.980024]  [<f8a8aeda>] intel_atomic_commit+0x52a/0x6a0 [i915]
[   13.980024]  [<f886130e>] ? drm_atomic_check_only+0x1ae/0x600 [drm]
[   13.980024]  [<f885feb9>] ? drm_modeset_lock+0x49/0xd0 [drm]
[   13.980024]  [<f886082c>] ? drm_atomic_set_crtc_for_connector+0x5c/0xe0 [drm]
[   13.980024]  [<f8861792>] drm_atomic_commit+0x32/0x60 [drm]
[   13.980024]  [<f85dede3>] restore_fbdev_mode+0x253/0x290 [drm_kms_helper]
[   13.980024]  [<f885ffd4>] ? drm_modeset_lock_all_ctx+0x94/0xb0 [drm]
[   13.980024]  [<f85e0e47>] drm_fb_helper_restore_fbdev_mode_unlocked+0x27/0x70 [drm_kms_helper]
[   13.980024]  [<f8aa0500>] intel_fbdev_restore_mode+0x20/0x80 [i915]
[   13.980024]  [<f8a94567>] ? intel_modeset_preclose+0x37/0x90 [i915]
[   13.980024]  [<f8a4f621>] ? i915_gem_release+0x21/0xb0 [i915]
[   13.980024]  [<f8acc42d>] i915_driver_lastclose+0xd/0x20 [i915]
[   13.980024]  [<f884489a>] drm_lastclose+0x2a/0x140 [drm]
[   13.980024]  [<f8844c4f>] drm_release+0x29f/0x490 [drm]
[   13.980024]  [<c11dc63f>] __fput+0xcf/0x210
[   13.980024]  [<c11dc7bd>] ____fput+0xd/0x10
[   13.980024]  [<c1089a5f>] task_work_run+0x7f/0xa0
[   13.980024]  [<c1003115>] exit_to_usermode_loop+0xd5/0xe0
[   13.980024]  [<c10039f7>] do_fast_syscall_32+0x147/0x150
[   13.980024]  [<c17a7dd8>] sysenter_past_esp+0x3d/0x61
[   13.981497] ---[ end trace 3fb1c2bdf4a91396 ]---
[   14.055634] intel_rng: FWH not detected
[   14.211228] ACPI Warning: SystemIO range 0x0000000000001028-0x000000000000102F conflicts with OpRegion 0x0000000000001000-0x000000000000107F (\PMIO) (20150930/utaddress-254)
[   14.211254] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.211264] ACPI Warning: SystemIO range 0x00000000000011B0-0x00000000000011BF conflicts with OpRegion 0x0000000000001180-0x00000000000011BB (\GPIO) (20150930/utaddress-254)
[   14.211281] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.211288] ACPI Warning: SystemIO range 0x0000000000001180-0x00000000000011AF conflicts with OpRegion 0x0000000000001180-0x00000000000011BB (\GPIO) (20150930/utaddress-254)
[   14.211303] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.211309] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   14.323179] leds_ss4200: no LED devices found

```

---

