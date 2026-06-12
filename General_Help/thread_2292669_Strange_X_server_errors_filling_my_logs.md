---
title: "Strange X server errors filling my logs"
date: 2015-08-30
forum: General Help
---

### Post by georgesgiralt on 2015-08-30
Hello !
On my Lenovo laptop (7 month old) I suddenly get a lot of below errors. I do not know if they are software or hardware related ? 
The mainboard has an NVidia chip and, of course the Intel graphic card on the CPU. I think this is called Optimus Technology ? 
I'm running the Nouveau X server (which is I think the default on 14.04 installation with this graphic card configuration.
I would be very pleased to get your advice on these errors.
Thanks a lot in advance !
```

[ 3710.007359] ------------[ cut here ]------------
[ 3710.007367] WARNING: CPU: 2 PID: 3738 at /build/linux-lts-utopic-ZOOBEH/linux-lts-utopic-3.16.0/drivers/gpu/drm/i915/intel_pm.c:5940 intel_display_power_put+0x11d/0x160 [i915]()
[ 3710.007383] Modules linked in: msr acpi_call(OE) pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) autofs4 ctr ccm btusb uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core v4l2_common videodev media bnep rfcomm bluetooth 6lowpan_iphc nfsd auth_rpcgss nfs_acl nfs binfmt_misc lockd sunrpc fscache snd_hda_codec_conexant snd_hda_codec_generic nls_iso8859_1 snd_hda_codec_hdmi arc4 intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd iwlmvm mac80211 nouveau thinkpad_acpi joydev nvram snd_hda_intel iwlwifi snd_hda_controller serio_raw snd_hda_codec snd_hwdep snd_pcm mxm_wmi cfg80211 rtsx_pci_ms snd_seq_midi snd_seq_midi_event lpc_ich memstick ttm mei_me mei i915 wmi snd_rawmidi snd_seq snd_seq_device snd_timer drm_kms_helper drm mac_hid snd shpchp i2c_algo_bit soundcore video parport_pc ppdev lp parport hid_generic usbhid hid rtsx_pci_sdmmc psmouse ahci r8169 libahci rtsx_pci mii
[ 3710.007390] CPU: 2 PID: 3738 Comm: kworker/u16:6 Tainted: G        W  OE 3.16.0-46-generic #62~14.04.1-Ubuntu
[ 3710.007391] Hardware name: LENOVO 20C600JHFR/20C600JHFR, BIOS J9ET99WW (2.19 ) 05/05/2015
[ 3710.007392] Workqueue: events_unbound async_run_entry_fn
[ 3710.007394]  0000000000000009 ffff880099fb7bc0 ffffffff817663d1 0000000000000000
[ 3710.007395]  ffff880099fb7bf8 ffffffff8106de3d 0000000000000000 ffffffffc06087a0
[ 3710.007396]  0000000000008000 ffff880328fc8548 ffff880328fc0000 ffff880099fb7c08
[ 3710.007396] Call Trace:
[ 3710.007398]  [<ffffffff817663d1>] dump_stack+0x45/0x56
[ 3710.007400]  [<ffffffff8106de3d>] warn_slowpath_common+0x7d/0xa0
[ 3710.007402]  [<ffffffff8106df1a>] warn_slowpath_null+0x1a/0x20
[ 3710.007409]  [<ffffffffc055caad>] intel_display_power_put+0x11d/0x160 [i915]
[ 3710.007422]  [<ffffffffc05c0b6b>] intel_dp_detect+0xab/0x330 [i915]
[ 3710.007433]  [<ffffffffc05c78ca>] ? intel_hdmi_detect+0x9a/0x130 [i915]
[ 3710.007438]  [<ffffffffc0537c09>] drm_helper_hpd_irq_event+0x99/0x140 [drm_kms_helper]
[ 3710.007440]  [<ffffffff813d0e70>] ? pci_pm_thaw+0xa0/0xa0
[ 3710.007446]  [<ffffffffc054f3bf>] __i915_drm_thaw+0x14f/0x1b0 [i915]
[ 3710.007453]  [<ffffffffc054fc38>] i915_resume+0x28/0x50 [i915]
[ 3710.007460]  [<ffffffffc054fc75>] i915_pm_resume+0x15/0x20 [i915]
[ 3710.007462]  [<ffffffff813d0ed4>] pci_pm_resume+0x64/0xb0
[ 3710.007463]  [<ffffffff814c677e>] dpm_run_callback+0x4e/0x100
[ 3710.007464]  [<ffffffff814c6cf6>] device_resume+0xd6/0x200
[ 3710.007465]  [<ffffffff814c6e3d>] async_resume+0x1d/0x50
[ 3710.007467]  [<ffffffff81097767>] async_run_entry_fn+0x37/0x130
[ 3710.007468]  [<ffffffff8108a562>] process_one_work+0x182/0x450
[ 3710.007469]  [<ffffffff8108acd1>] worker_thread+0x121/0x570
[ 3710.007471]  [<ffffffff8108abb0>] ? rescuer_thread+0x380/0x380
[ 3710.007472]  [<ffffffff81091572>] kthread+0xd2/0xf0
[ 3710.007474]  [<ffffffff810914a0>] ? kthread_create_on_node+0x1c0/0x1c0
[ 3710.007476]  [<ffffffff8176e9d8>] ret_from_fork+0x58/0x90
[ 3710.007477]  [<ffffffff810914a0>] ? kthread_create_on_node+0x1c0/0x1c0
[ 3710.007478] ---[ end trace 2873e864b579abd2 ]---

```

---

### Post by dino99 on 2015-08-30
check if you get the same issue with older kernels
check if the fan(s) are running as expected (control temperature) (indeed the laptop needs some fresh air for cooling)
note that sometimes its a bios/uefi issue: when the setting is set to 'auto' for the ram voltage, some bios/uefi in fact set a too low voltage. In that case, to unhide the ram voltage setting, opt-in for 'manual' cpu settings first, then the ram voltage is unhide.
check your bios/uefi version is the last one (upgrade if necessary)

---

### Post by georgesgiralt on 2015-08-30
Hello Dino99,
As per the BIOS, it is the last one and the same since may. (I had to upgrade to correct a strange USB problem) There are no CPU setting in it, either concealed or showing ! 
I already monitor the fan and it is running, the temperature is around 50°C for both cores which I suppose is normal given the ambient room is at 26~27 °C... 
I will try the previous kernel as the error is very recent. 
Thank you for your help !

---

