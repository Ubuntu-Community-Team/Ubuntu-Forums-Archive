---
title: "Call traceback on every boot."
date: 2021-06-01
forum: General Help
---

### Post by georgesgiralt on 2021-06-01
Hello Guys,
I post this as I do not know where to put it. You can move it if need be.
The culprit is a Lenovo Thinkbook (20VE) with a 11th gen i5 and an MX450 Nvidia GPU. On it I've put Ubuntu 20.04 LTS and perfectly up to date. 
On every boot I've got this :
```
 
[    4.554116] ------------[ cut here ]------------
[    4.554118] Missing case (clock == 269720)
[    4.554194] WARNING: CPU: 1 PID: 501 at drivers/gpu/drm/i915/display/intel_dpll_mgr.c:2967 icl_calc_dpll_state.isra.0+0x21d/0x280 [i915]
[    4.554195] Modules linked in: snd_pcm libarc4 input_leds(+) serio_raw i915(+) efi_pstore wmi_bmof snd_timer ee1004 snd drm_kms_helper mei_me iwlwifi hid_multitouch(+) cec soundcore rc_core mei i2c_algo_bit fb_sys_fops syscopyarea sysfillrect cfg80211 sysimgblt processor_thermal_device mac_hid intel_rapl_common ucsi_acpi typec_ucsi intel_soc_dts_iosf typec ideapad_laptop sparse_keymap int3403_thermal int340x_thermal_zone int3400_thermal acpi_thermal_rel acpi_pad sch_fq_codel cuse parport_pc ppdev lp parport drm nfsd auth_rpcgss nfs_acl lockd grace sunrpc ip_tables x_tables autofs4 dm_mirror dm_region_hash dm_log hid_generic nvme sdhci_pci cqhci ahci intel_lpss_pci nvme_core libahci intel_lpss i2c_i801 r8169 crc32_pclmul i2c_smbus sdhci idma64 xhci_pci realtek i2c_hid thunderbolt virt_dma vmd xhci_pci_renesas hid wmi video pinctrl_tigerlake pinctrl_intel
[    4.554224] CPU: 1 PID: 501 Comm: systemd-udevd Not tainted 5.8.0-53-generic #60~20.04.1-Ubuntu
[    4.554225] Hardware name: LENOVO 20VE/LNVNB161216, BIOS F8CN38WW(V2.03) 04/09/2021
[    4.554262] RIP: 0010:icl_calc_dpll_state.isra.0+0x21d/0x280 [i915]
[    4.554264] Code: 4c 63 c2 39 cf 74 55 48 83 c2 01 48 83 fa 08 75 e5 48 63 d7 48 c7 c6 de 65 c1 c0 48 c7 c7 d3 64 c1 c0 88 45 bf e8 c9 52 5c e3 <0f> 0b 0f b6 45 bf e9 ea fe ff ff 31 d2 be 54 00 60 00 e9 9b fe ff
[    4.554265] RSP: 0000:ffffab03407db6c8 EFLAGS: 00010282
[    4.554266] RAX: 0000000000000000 RBX: ffff9aae96087490 RCX: 0000000000000027
[    4.554266] RDX: 0000000000000027 RSI: 0000000000000086 RDI: ffff9aae9fa58cd8
[    4.554267] RBP: ffffab03407db710 R08: ffff9aae9fa58cd0 R09: 0000000000000004
[    4.554267] R10: 0000000000000000 R11: 0000000000000001 R12: ffff9aae96087000
[    4.554268] R13: ffff9aae94280000 R14: ffff9aae96247800 R15: ffff9aae96f7e000
[    4.554269] FS:  00007fcb2d3fa880(0000) GS:ffff9aae9fa40000(0000) knlGS:0000000000000000
[    4.554269] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[    4.554270] CR2: 000056317bb1e708 CR3: 0000000496736002 CR4: 0000000000760ee0
[    4.554270] PKRU: 55555554
[    4.554271] Call Trace:
[    4.554307]  icl_get_dplls+0x34b/0x840 [i915]
[    4.554325]  ? drm_mode_object_get+0x2a/0x60 [drm]
[    4.554337]  ? drm_connector_list_iter_next+0x8e/0xb0 [drm]
[    4.554373]  intel_reserve_shared_dplls+0x24/0x60 [i915]
[    4.554409]  hsw_crtc_compute_clock+0x5a/0x90 [i915]
[    4.554443]  intel_atomic_check_crtcs+0x3ba/0x620 [i915]
[    4.554475]  ? icl_put_dplls+0x6c/0xb0 [i915]
[    4.554507]  intel_atomic_check+0xa22/0xb60 [i915]
[    4.554519]  ? drm_plane_check_pixel_format+0x4f/0xb0 [drm]
[    4.554531]  ? drm_atomic_plane_check+0x7a/0x3a0 [drm]
[    4.554542]  drm_atomic_check_only+0x2c7/0x450 [drm]
[    4.554553]  drm_atomic_commit+0x18/0x50 [drm]
[    4.554585]  intel_modeset_init+0x456/0xae0 [i915]
[    4.554614]  i915_driver_probe+0x275/0x500 [i915]
[    4.554617]  ? _cond_resched+0x19/0x30
[    4.554619]  ? mutex_lock+0x13/0x40
[    4.554648]  i915_pci_probe+0x5a/0x140 [i915]
[    4.554651]  local_pci_probe+0x48/0x80
[    4.554653]  pci_device_probe+0x10f/0x1b0
[    4.554656]  really_probe+0x159/0x3d0
[    4.554657]  driver_probe_device+0xe9/0x160
[    4.554659]  device_driver_attach+0x5d/0x70
[    4.554660]  __driver_attach+0x8f/0x150
[    4.554661]  ? device_driver_attach+0x70/0x70
[    4.554662]  bus_for_each_dev+0x7e/0xc0
[    4.554664]  driver_attach+0x1e/0x20
[    4.554665]  bus_add_driver+0x152/0x1f0
[    4.554666]  driver_register+0x74/0xd0
[    4.554667]  __pci_register_driver+0x54/0x60
[    4.554697]  i915_init+0x61/0x75 [i915]
[    4.554698]  ? 0xffffffffc0caa000
[    4.554700]  do_one_initcall+0x4a/0x200
[    4.554702]  ? kfree+0x231/0x250
[    4.554704]  ? _cond_resched+0x19/0x30
[    4.554705]  ? kmem_cache_alloc_trace+0x177/0x240
[    4.554708]  do_init_module+0x62/0x250
[    4.554709]  load_module+0x10f5/0x12a0
[    4.554711]  ? ima_post_read_file+0x108/0x120
[    4.554713]  __do_sys_finit_module+0xc9/0x130
[    4.554714]  ? __do_sys_finit_module+0xc9/0x130
[    4.554716]  __x64_sys_finit_module+0x1a/0x20
[    4.554718]  do_syscall_64+0x49/0xc0
[    4.554720]  entry_SYSCALL_64_after_hwframe+0x44/0xa9
[    4.554720] RIP: 0033:0x7fcb2d97c89d
[    4.554722] Code: 00 c3 66 2e 0f 1f 84 00 00 00 00 00 90 f3 0f 1e fa 48 89 f8 48 89 f7 48 89 d6 48 89 ca 4d 89 c2 4d 89 c8 4c 8b 4c 24 08 0f 05 <48> 3d 01 f0 ff ff 73 01 c3 48 8b 0d c3 f5 0c 00 f7 d8 64 89 01 48
[    4.554723] RSP: 002b:00007ffeeef3ca88 EFLAGS: 00000246 ORIG_RAX: 0000000000000139
[    4.554724] RAX: ffffffffffffffda RBX: 000055affe7c35e0 RCX: 00007fcb2d97c89d
[    4.554725] RDX: 0000000000000000 RSI: 00007fcb2d859ded RDI: 0000000000000016
[    4.554725] RBP: 0000000000020000 R08: 0000000000000000 R09: 0000000000000000
[    4.554726] R10: 0000000000000016 R11: 0000000000000246 R12: 00007fcb2d859ded
[    4.554726] R13: 0000000000000000 R14: 000055affe7d7c80 R15: 000055affe7c35e0
[    4.554728] ---[ end trace cffdc12aacbe8ff9 ]---


```
The machine runs fine otherwise but this annoys me a lot because I try to clear all potential problem on this new (to me ) machine. (and I've got a lot of ACPI red lines in dmesg.... )
So I' would be very glad and thankful to get your help and advice ! 
Have a nice and bright day !

---

### Post by InuY4sha on 2021-07-07
I'm having the exact same problem:
xubuntu 20.04 downloaded and freshinstalled today on a dell 5520

I'm upgrading the graphics drivers for i915 in hope it's that. I'm following the answer given here:

[https://askubuntu.com/questions/1082499/how-to-get-and-install-intel-i915-drivers-on-ubuntu-18-04](https://askubuntu.com/questions/1082499/how-to-get-and-install-intel-i915-drivers-on-ubuntu-18-04)

[EDIT] Nothing good this way

[2nd EDIT] I figured out what is causing this at least for me: I have an HDMI monitor attached to the laptop. On *EVERY* reboot I get the fault. subsequent additional reboot goes fine. Unplugging the HDMI cable and rebooting does not exhibit  the problem

I'm reading these:
[https://elementaryos.stackexchange.com/questions/12918/frequent-crashes-with-intel-i915-and-second-hdmi-monitor](https://elementaryos.stackexchange.com/questions/12918/frequent-crashes-with-intel-i915-and-second-hdmi-monitor)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1580272](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1580272)
[https://bbs.archlinux.org/viewtopic.php?id=262283](https://bbs.archlinux.org/viewtopic.php?id=262283)
[https://forums.unraid.net/topic/99958-intel-igpu-i915-driver-crashing-issues-on-various-linux-kernels/](https://forums.unraid.net/topic/99958-intel-igpu-i915-driver-crashing-issues-on-various-linux-kernels/)

---

