---
title: "dmesg errors"
date: 2016-05-24
forum: General Help
---

### Post by davide3 on 2016-05-24
Here's my first time looking at dmesg, but bad news I can see here!
Could someone tell me what's happening?

```

[   13.979800] WARNING: CPU: 0 PID: 384 at /build/linux-xgbPFL/linux-4.4.0/drivers/gpu/drm/drm_atomic_helper.c:725 drm_atomic_helper_update_legacy_modeset_state+0x26a/0x280 [drm_kms_helper]()[   13.979807] Modules linked in: snd soundcore ideapad_laptop shpchp sparse_keymap mac_hid ip6t_REJECT nf_reject_ipv6 nf_log_ipv6 xt_hl ip6t_rt nf_conntrack_ipv6 nf_defrag_ipv6 ipt_REJECT nf_reject_ipv4 nf_log_ipv4 nf_log_common xt_LOG xt_limit xt_tcpudp xt_addrtype nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack ip6table_filter ip6_tables nf_conntrack_netbios_ns nf_conntrack_broadcast nf_nat_ftp nf_nat nf_conntrack_ftp nf_conntrack iptable_filter ip_tables x_tables coretemp parport_pc ppdev lp parport autofs4 hid_generic ums_realtek uas usbhid hid usb_storage i915 tg3 psmouse i2c_algo_bit drm_kms_helper ptp syscopyarea sysfillrect pata_acpi sysimgblt fb_sys_fops drm pps_core wmi video fjes
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

