---
title: "Ubuntu 16.04 Fails to shutdown"
date: 2018-07-10
forum: General Help
---

### Post by lopezem on 2018-07-10
I am using an amd64 based PC, I am attempting to do a reboot with ubuntu 16.04 (core and server) and I get the same message at shutdown:
[IMG]https://snapforum.s3.amazonaws.com/optimized/2X/b/b10f008295748507516fae49fe4f1959f46d2972_1_374x500.jpg[/IMG]

I also get this stack trace from the kernel during boot (not sure if this is related)
```

[   12.641287] BUG: unable to handle kernel paging request at ffffffffffffffed
[   12.643467] IP: [<ffffffff81573c3e>] __fwnode_property_present+0xe/0x40
[   12.645647] PGD 1e0f067 PUD 1e11067 PMD 0
[   12.647751] Oops: 0000 [#1] SMP
[   12.649777] Modules linked in: 8250_dw(+) intel_telemetry_pltdrv intel_pmc_ipc intel_punit_ipc intel_telemetry_core x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm irqbypass crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic glue_helper ablk_helper cryptd snd_hda_intel usbhid snd_hda_codec igb snd_hda_core snd_hwdep ptp pps_core idma64 virt_dma snd_pcm intel_lpss_pci dca intel_lpss i2c_hid hid mei_me snd_timer mei mac_hid snd fjes pinctrl_broxton pinctrl_intel soundcore shpchp autofs4 sdhci_acpi virtio_scsi usb_storage mmc_block i915_bpo intel_ips i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops drm ahci sdhci_pci libahci sdhci video
[   12.654999] CPU: 0 PID: 573 Comm: systemd-udevd Not tainted 4.4.0-130-generic #156-Ubuntu
[   12.655000] Hardware name: Compulab fitlet2/fitlet2, BIOS FLT2.0.38.01.00 11/19/2017
[   12.655003] task: ffff8800722de900 ti: ffff880071e4c000 task.ti: ffff880071e4c000
[   12.655005] RIP: 0010:[<ffffffff81573c3e>]
[   12.655008]  [<ffffffff81573c3e>] __fwnode_property_present+0xe/0x40
[   12.655011] RSP: 0018:ffff880071e4f8b8  EFLAGS: 00010286
[   12.655012] RAX: 0000000000000000 RBX: ffff880071b64f60 RCX: 0000000000000000
[   12.655014] RDX: 0000000000000004 RSI: ffffffffc053f084 RDI: ffffffffffffffed
[   12.655016] RBP: ffff880071e4f8b8 R08: ffff880075e1a620 R09: ffff880075801600
[   12.655017] R10: ffff880075801600 R11: ffff88006fbc4a00 R12: ffffffffc053f084
[   12.655019] R13: ffff8800716a6800 R14: ffff8800716a6810 R15: ffff880071e4f908
[   12.655022] FS:  00007f141d7ce8c0(0000) GS:ffff880075e00000(0000) knlGS:0000000000000000
[   12.655024] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[   12.655026] CR2: ffffffffffffffed CR3: 0000000071e54000 CR4: 0000000000340670
[   12.655027] Stack:
[   12.655028]  ffff880071e4f8d8
[   12.655029]  ffffffff81573c9c
[   12.655030]  ffff88006fbc4a18
[   12.655031]  ffffffffc0540028


[   12.655032]  ffff880071e4f8e8
[   12.655033]  ffffffff81573cc5
[   12.655034]  ffff880071e4fb48
[   12.655035]  ffffffffc053e778


[   12.655036]  0000000000000246
[   12.655037]  0000000471e4f9cc
[   12.655038]  0000000000000000
[   12.655038]  0000000000000000


[   12.655040] Call Trace:
[   12.655046]  [<ffffffff81573c9c>] fwnode_property_present+0x2c/0x40
[   12.655051]  [<ffffffff81573cc5>] device_property_present+0x15/0x20
[   12.655058]  [<ffffffffc053e778>] dw8250_probe+0x1c8/0x703 [8250_dw]
[   12.655064]  [<ffffffffc053e040>] ? dw8250_serial_in+0x40/0x40 [8250_dw]
[   12.655068]  [<ffffffffc053e230>] ? dw8250_remove+0xe0/0xe0 [8250_dw]
[   12.655073]  [<ffffffffc053e350>] ? dw8250_serial_out+0x90/0x90 [8250_dw]
[   12.655077]  [<ffffffffc053e3d0>] ? dw8250_handle_irq+0x80/0x80 [8250_dw]
[   12.655084]  [<ffffffff8157050e>] platform_drv_probe+0x3e/0xa0
[   12.655087]  [<ffffffff8156e2db>] driver_probe_device+0x22b/0x4b0
[   12.655091]  [<ffffffff8156e5e7>] __driver_attach+0x87/0x90
[   12.655094]  [<ffffffff8156e560>] ? driver_probe_device+0x4b0/0x4b0
[   12.655097]  [<ffffffff8156bee2>] bus_for_each_dev+0x72/0xc0
[   12.655100]  [<ffffffff8156da8e>] driver_attach+0x1e/0x20
[   12.655103]  [<ffffffff8156d5c2>] bus_add_driver+0x1e2/0x280
[   12.655106]  [<ffffffffc0555000>] ? 0xffffffffc0555000
[   12.655109]  [<ffffffff8156ef00>] driver_register+0x60/0xe0
[   12.655113]  [<ffffffff81570436>] __platform_driver_register+0x36/0x40
[   12.655118]  [<ffffffffc0555017>] dw8250_platform_driver_init+0x17/0x1000 [8250_dw]
[   12.655122]  [<ffffffff81002135>] do_one_initcall+0xb5/0x200
[   12.655129]  [<ffffffff811f38d5>] ? kmem_cache_alloc_trace+0x185/0x1f0
[   12.655134]  [<ffffffff81192fa5>] do_init_module+0x5f/0x1cf
[   12.655138]  [<ffffffff8110f0ce>] load_module+0x16ae/0x1c50
[   12.655142]  [<ffffffff8110b5d0>] ? __symbol_put+0x60/0x60
[   12.655148]  [<ffffffff8121b6f0>] ? kernel_read+0x50/0x80
[   12.655152]  [<ffffffff8110f8b4>] SYSC_finit_module+0xb4/0xe0
[   12.655156]  [<ffffffff8110f8fe>] SyS_finit_module+0xe/0x10
[   12.655161]  [<ffffffff8185328e>] entry_SYSCALL_64_fastpath+0x22/0xc1
[   12.655163] Code:
[   12.655164] 44
[   12.655165] f8
[   12.655166] e8
[   12.655166] e6
[   12.655167] 97
[   12.655168] f2
[   12.655169] ff
[   12.655169] 5d
[   12.655170] c3
[   12.655171] 31
[   12.655172] ff
[   12.655172] e8
[   12.655173] dd
[   12.655174] 97
[   12.655174] f2
[   12.655175] ff
[   12.655176] 5d
[   12.655177] c3
[   12.655177] 90
[   12.655178] 66
[   12.655179] 2e
[   12.655180] 0f
[   12.655180] 1f
[   12.655181] 84
[   12.655182] 00
[   12.655182] 00
[   12.655183] 00
[   12.655184] 00
[   12.655185] 00
[   12.655185] 0f
[   12.655186] 1f
[   12.655187] 44
[   12.655188] 00
[   12.655188] 00
[   12.655189] 55
[   12.655190] 48
[   12.655190] 85
[   12.655191] ff
[   12.655192] 48
[   12.655193] 89
[   12.655193] e5
[   12.655194] 74
[   12.655195] 2e
[   12.655196] <8b>
[   12.655197] 17
[   12.655197] 8d
[   12.655198] 42
[   12.655199] fe
[   12.655199] 83
[   12.655200] f8
[   12.655201] 01
[   12.655202] 76
[   12.655202] 16
[   12.655203] 31
[   12.655204] c0
[   12.655204] 83
[   12.655205] fa
[   12.655206] 04
[   12.655207] 74
[   12.655207] 02
[   12.655208] 5d
[   12.655209] c3
[   12.655210] e8
[   12.655210] 0a


[   12.655212] RIP
[   12.655214]  [<ffffffff81573c3e>] __fwnode_property_present+0xe/0x40
[   12.655215]  RSP <ffff880071e4f8b8>
[   12.655216] CR2: ffffffffffffffed
[   12.655220] ---[ end trace d02949f8ba377891 ]---

```

I have changed multiple BIOS settings but have not found any setting that resolves the shut down issue.
Going back to the default BIOS settings, I tried a couple of different installations;

[LIST=1]
[*]I am able to successfully reboot using the same SD Card with Linux Mint 19 (which has a newer Kernel version (4.15.0-20).
[*]I go back to Linux Mint 18 (Kernel version 4.4.0, same as Ubuntu core) and I cannot shut down.
[*]I install a version of Ubuntu Server 16.04.4 (Kernel version 4.4.0 ), and it fails to shutdown as well.
[*]I install a version of Ubuntu Server 18.04 (kernel 4.15.0) and I can successfully reboot on the same HW. I also do no get any kernel stack traces either
[/LIST]

To me this sounds like more of a kernel problem.

Furthermore I have attempted the following, but with no luck


[LIST]
[*]Updating the grub parameters with: ```
GRUB_CMDLINE_LINUX_DEFAULT="acpi=force" #I also set acpi=off as well
```
[*]Updating the timeouts in /etc/systemd/system.con with:```
DefaultTimeoutStopSec=5s DefaultTimeoutStopSec=5s
```
[/LIST]

---

