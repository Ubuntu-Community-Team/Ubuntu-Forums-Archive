---
title: "graphics driver error ?"
date: 2020-05-10
forum: General Help
---

### Post by maketopsite on 2020-05-10
```
May 10 07:14:20 ntb-TN kernel: fbcon: inteldrmfb (fb0) is primary device
May 10 07:14:20 ntb-TN kernel: snd_hda_intel 0000:00:1b.0: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
May 10 07:14:20 ntb-TN kernel: input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input8
May 10 07:14:20 ntb-TN kernel: ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
May 10 07:14:20 ntb-TN kernel: [drm] Initialized i915 1.6.0 20171023 for 0000:00:02.0 on minor 0
May 10 07:14:20 ntb-TN kernel: ---[ end trace b9bc2be604c9581f ]---
May 10 07:14:20 ntb-TN kernel: Code: e9 46 fc ff ff 48 c7 c6 f7 2d 6b c0 48 c7 c7 4f 21 6b c0 e8 b4 98 e6 f7 0f 0b e9 73
May 10 07:14:20 ntb-TN kernel: R13: 0000564a4121a330 R14: 0000000000020000 R15: 0000564a4123b410
May 10 07:14:20 ntb-TN kernel: R10: 0000000000000015 R11: 0000000000000246 R12: 0000000000000000
May 10 07:14:20 ntb-TN kernel: RBP: 00007fb3d1745105 R08: 0000000000000000 R09: 00007ffc1f7110e0
May 10 07:14:20 ntb-TN kernel: RDX: 0000000000000000 RSI: 00007fb3d1745105 RDI: 0000000000000015
May 10 07:14:20 ntb-TN kernel: RAX: ffffffffffffffda RBX: 0000564a4123b410 RCX: 00007fb3d1a66839
May 10 07:14:20 ntb-TN kernel: RSP: 002b:00007ffc1f710fc8 EFLAGS: 00000246 ORIG_RAX: 0000000000000139
May 10 07:14:20 ntb-TN kernel: RIP: 0033:0x7fb3d1a66839
May 10 07:14:20 ntb-TN kernel:  entry_SYSCALL_64_after_hwframe+0x3d/0xa2
May 10 07:14:20 ntb-TN kernel:  do_syscall_64+0x73/0x130
May 10 07:14:20 ntb-TN kernel:  SyS_finit_module+0xe/0x10
May 10 07:14:20 ntb-TN kernel:  ? SYSC_finit_module+0xfc/0x120
May 10 07:14:20 ntb-TN kernel:  SYSC_finit_module+0xfc/0x120
May 10 07:14:20 ntb-TN kernel:  ? ima_post_read_file+0x96/0xa0
May 10 07:14:20 ntb-TN kernel:  load_module+0x16bd/0x1f20
May 10 07:14:20 ntb-TN kernel:  do_init_module+0x5f/0x213
May 10 07:14:20 ntb-TN kernel:  ? do_init_module+0x27/0x213
May 10 07:14:20 ntb-TN kernel:  ? kmem_cache_alloc_trace+0xa6/0x1b0
May 10 07:14:20 ntb-TN kernel:  ? _cond_resched+0x19/0x40
May 10 07:14:20 ntb-TN kernel:  ? __vunmap+0x8e/0xc0
May 10 07:14:20 ntb-TN kernel:  do_one_initcall+0x52/0x19f
May 10 07:14:20 ntb-TN kernel:  i915_init+0x5c/0x5f [i915]
May 10 07:14:20 ntb-TN kernel:  __pci_register_driver+0x5a/0x60
May 10 07:14:20 ntb-TN kernel:  ? 0xffffffffc0724000
May 10 07:14:20 ntb-TN kernel:  driver_register+0x60/0xe0
May 10 07:14:20 ntb-TN kernel:  ? 0xffffffffc0724000
May 10 07:14:20 ntb-TN kernel:  bus_add_driver+0x1c7/0x270
May 10 07:14:20 ntb-TN kernel:  driver_attach+0x1e/0x20
May 10 07:14:20 ntb-TN kernel:  bus_for_each_dev+0x70/0xc0
May 10 07:14:20 ntb-TN kernel:  ? driver_probe_device+0x4a0/0x4a0
May 10 07:14:20 ntb-TN kernel:  __driver_attach+0xcc/0xf0
May 10 07:14:20 ntb-TN kernel:  driver_probe_device+0x30c/0x4a0
May 10 07:14:20 ntb-TN kernel:  pci_device_probe+0x10e/0x1c0
May 10 07:14:20 ntb-TN kernel:  local_pci_probe+0x47/0xa0
May 10 07:14:20 ntb-TN kernel:  i915_pci_probe+0x42/0x70 [i915]
May 10 07:14:20 ntb-TN kernel:  i915_driver_load+0xa73/0xe60 [i915]
May 10 07:14:20 ntb-TN kernel: Call Trace:
May 10 07:14:20 ntb-TN kernel: CR2: 00007f367b57b008 CR3: 000000014780a001 CR4: 00000000001606f0
May 10 07:14:20 ntb-TN kernel: CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
May 10 07:14:20 ntb-TN kernel: FS:  00007fb3d1f38680(0000) GS:ffff9257cf200000(0000) knlGS:0000000000000000
May 10 07:14:20 ntb-TN kernel: R13: ffff9257c23ae400 R14: 00000000ffffffea R15: ffff9257c6d80358
May 10 07:14:20 ntb-TN kernel: R10: 0000000000000040 R11: 0000000000000001 R12: ffff9257c9a46800
May 10 07:14:20 ntb-TN kernel: RBP: ffffb914c0b03a40 R08: 0000000000000306 R09: 0000000000000004
May 10 07:14:20 ntb-TN kernel: RDX: 0000000000000007 RSI: 0000000000000096 RDI: ffff9257cf216490
May 10 07:14:20 ntb-TN kernel: RAX: 0000000000000000 RBX: ffff9257c6d80000 RCX: 0000000000000006
May 10 07:14:20 ntb-TN kernel: RSP: 0018:ffffb914c0b039b0 EFLAGS: 00010286
May 10 07:14:20 ntb-TN kernel: RIP: 0010:intel_modeset_init+0xfcf/0x1010 [i915]
May 10 07:14:20 ntb-TN kernel: Hardware name: Acer TravelMate P253/BA51_HC_CR, BIOS V2.15 03/11/2013
May 10 07:14:20 ntb-TN kernel: CPU: 0 PID: 279 Comm: systemd-udevd Not tainted 4.15.0-99-generic #100-Ubuntu
May 10 07:14:20 ntb-TN kernel: Modules linked in: snd_hda_intel(+) snd_hda_codec snd_hda_core snd_hwdep joydev snd_pcm i
May 10 07:14:20 ntb-TN kernel: WARNING: CPU: 0 PID: 279 at /build/linux-CbANGF/linux-4.15.0/drivers/gpu/drm/i915/intel_d
May 10 07:14:20 ntb-TN kernel: Could not determine valid watermarks for inherited state
May 10 07:14:20 ntb-TN kernel: ------------[ cut here ]------------
May 10 07:14:20 ntb-TN kernel: [drm] LVDS was detected, not registering eDP
May 10 07:14:20 ntb-TN kernel: i915 0000:00:02.0: vgaarb: changed VGA decodes: olddecodes=io+mem,decodes=io+mem:owns=io+
May 10 07:14:20 ntb-TN kernel: [drm] Driver supports precise vblank timestamp query.
May 10 07:14:20 ntb-TN kernel: [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
May 10 07:14:20 ntb-TN kernel: [drm] Replacing VGA console driver
May 10 07:14:20 ntb-TN kernel: Console: switching to colour dummy device 80x25
May 10 07:14:20 ntb-TN kernel: fb: switching to inteldrmfb from EFI VGA

```
Any action needed ?

---

