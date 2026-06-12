---
title: "Nvidia GPU hang when opening libreoffice apps"
date: 2016-07-05
forum: General Help
---

### Post by vertigo420 on 2016-07-05
Hi there. I was messing about with getting Arma 3 running on Ubuntu 16.04, and ended up installing the oibaf drivers for OpenGL 4.1 support, and a few other supporting libs that I now cant remember. Ever since, opening libreoffice results in a complete crash of the desktop environment and taking me back to lightdm.

Here are the relevant syslog entries.

```

Jul  6 10:01:39 camlinux kernel: [667904.231505] [drm] stuck on render ring
Jul  6 10:01:39 camlinux kernel: [667904.232297] [drm] GPU HANG: ecode 7:0:0x85df3c1c, in Xorg [19819], reason: Ring hung, action: reset
Jul  6 10:01:39 camlinux kernel: [667904.234413] drm/i915: Resetting chip after gpu hang
Jul  6 10:01:47 camlinux kernel: [667912.268472] [drm] stuck on render ring
Jul  6 10:01:47 camlinux kernel: [667912.269228] [drm] GPU HANG: ecode 7:0:0x86dffffd, in Xorg [19819], reason: Ring hung, action: reset
Jul  6 10:01:47 camlinux kernel: [667912.269259] ------------[ cut here ]------------
Jul  6 10:01:47 camlinux kernel: [667912.269290] WARNING: CPU: 4 PID: 30295 at /build/linux-UbQGH5/linux-4.4.0/drivers/gpu/drm/i915/intel_display.c:11287 intel_mmio_flip_work_func+0x38e/0x3d0 [i915]()
Jul  6 10:01:47 camlinux kernel: [667912.269293] WARN_ON(__i915_wait_request(mmio_flip->req, mmio_flip->crtc->reset_counter, false, NULL, &mmio_flip->i915->rps.mmioflips))
Jul  6 10:01:47 camlinux kernel: [667912.269294] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common videodev media arc4 btusb btrtl btbcm btintel intel_rapl bluetooth x86_pkg_temp_thermal iwlmvm intel_powerclamp kvm_intel mac80211 kvm snd_hda_codec_hdmi irqbypass crct10dif_pclmul sparse_keymap crc32_pclmul snd_hda_codec_realtek snd_hda_codec_generic aesni_intel mei_me snd_hda_intel aes_x86_64 snd_hda_codec lrw gf128mul snd_hda_core glue_helper ablk_helper cryptd snd_hwdep iwlwifi snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi cfg80211 snd_seq rtsx_pci_ms joydev input_leds acpi_als memstick snd_seq_device ie31200_edac snd_timer kfifo_buf lpc_ich mei snd industrialio edac_core soundcore serio_raw shpchp mac_hid cuse coretemp parport_pc ppdev lp parport autofs4 uas usb_storage hid_generic usbhid hid rtsx_pci_sdmmc i915 nouveau mxm_wmi ttm i2c_algo_bit psmouse drm_kms_helper syscopyarea sysfillrect ahci sysimgblt fb_sys_fops libahci drm r8169 rtsx_pci mii wmi video fjes
Jul  6 10:01:47 camlinux kernel: [667912.269369] CPU: 4 PID: 30295 Comm: kworker/4:2 Tainted: G        W  OE   4.4.0-22-generic #39-Ubuntu
Jul  6 10:01:47 camlinux kernel: [667912.269371] Hardware name: GIGABYTE P35V3/P35V3, BIOS P35V3.FB08 11/28/2014
Jul  6 10:01:47 camlinux kernel: [667912.269396] Workqueue: events intel_mmio_flip_work_func [i915]
Jul  6 10:01:47 camlinux kernel: [667912.269399]  0000000000000286 000000005be2177e ffff88014199fd20 ffffffff813e9c53
Jul  6 10:01:47 camlinux kernel: [667912.269402]  ffff88014199fd68 ffffffffc0421a50 ffff88014199fd58 ffffffff81080fb2
Jul  6 10:01:47 camlinux kernel: [667912.269405]  ffff8800caf1c680 ffff88042fb16500 ffff88042fb1ae00 0000000000000100
Jul  6 10:01:47 camlinux kernel: [667912.269407] Call Trace:
Jul  6 10:01:47 camlinux kernel: [667912.269414]  [<ffffffff813e9c53>] dump_stack+0x63/0x90
Jul  6 10:01:47 camlinux kernel: [667912.269419]  [<ffffffff81080fb2>] warn_slowpath_common+0x82/0xc0
Jul  6 10:01:47 camlinux kernel: [667912.269422]  [<ffffffff8108104c>] warn_slowpath_fmt+0x5c/0x80
Jul  6 10:01:47 camlinux kernel: [667912.269426]  [<ffffffff8102d66c>] ? __switch_to+0x1dc/0x5c0
Jul  6 10:01:47 camlinux kernel: [667912.269449]  [<ffffffffc03bac9e>] intel_mmio_flip_work_func+0x38e/0x3d0 [i915]
Jul  6 10:01:47 camlinux kernel: [667912.269452]  [<ffffffff8109a052>] process_one_work+0x162/0x480
Jul  6 10:01:47 camlinux kernel: [667912.269454]  [<ffffffff8109a3bb>] worker_thread+0x4b/0x4c0
Jul  6 10:01:47 camlinux kernel: [667912.269457]  [<ffffffff8109a370>] ? process_one_work+0x480/0x480
Jul  6 10:01:47 camlinux kernel: [667912.269459]  [<ffffffff8109a370>] ? process_one_work+0x480/0x480
Jul  6 10:01:47 camlinux kernel: [667912.269462]  [<ffffffff810a0588>] kthread+0xd8/0xf0
Jul  6 10:01:47 camlinux kernel: [667912.269464]  [<ffffffff810a04b0>] ? kthread_create_on_node+0x1e0/0x1e0
Jul  6 10:01:47 camlinux kernel: [667912.269467]  [<ffffffff8182568f>] ret_from_fork+0x3f/0x70
Jul  6 10:01:47 camlinux kernel: [667912.269469]  [<ffffffff810a04b0>] ? kthread_create_on_node+0x1e0/0x1e0
Jul  6 10:01:47 camlinux kernel: [667912.269471] ---[ end trace d59d4d94c9a21277 ]---
Jul  6 10:01:47 camlinux kernel: [667912.269480] ------------[ cut here ]------------
Jul  6 10:01:47 camlinux kernel: [667912.269501] WARNING: CPU: 4 PID: 17898 at /build/linux-UbQGH5/linux-4.4.0/drivers/gpu/drm/i915/intel_display.c:11287 intel_mmio_flip_work_func+0x38e/0x3d0 [i915]()
Jul  6 10:01:47 camlinux kernel: [667912.269503] WARN_ON(__i915_wait_request(mmio_flip->req, mmio_flip->crtc->reset_counter, false, NULL, &mmio_flip->i915->rps.mmioflips))
Jul  6 10:01:47 camlinux kernel: [667912.269503] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common videodev media arc4 btusb btrtl btbcm btintel intel_rapl bluetooth x86_pkg_temp_thermal iwlmvm intel_powerclamp kvm_intel mac80211 kvm snd_hda_codec_hdmi irqbypass crct10dif_pclmul sparse_keymap crc32_pclmul snd_hda_codec_realtek snd_hda_codec_generic aesni_intel mei_me snd_hda_intel aes_x86_64 snd_hda_codec lrw gf128mul snd_hda_core glue_helper ablk_helper cryptd snd_hwdep iwlwifi snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi cfg80211 snd_seq rtsx_pci_ms joydev input_leds acpi_als memstick snd_seq_device ie31200_edac snd_timer kfifo_buf lpc_ich mei snd industrialio edac_core soundcore serio_raw shpchp mac_hid cuse coretemp parport_pc ppdev lp parport autofs4 uas usb_storage hid_generic usbhid hid rtsx_pci_sdmmc i915 nouveau mxm_wmi ttm i2c_algo_bit psmouse drm_kms_helper syscopyarea sysfillrect ahci sysimgblt fb_sys_fops libahci drm r8169 rtsx_pci mii wmi video fjes
Jul  6 10:01:47 camlinux kernel: [667912.269562] CPU: 4 PID: 17898 Comm: kworker/4:3 Tainted: G        W  OE   4.4.0-22-generic #39-Ubuntu
Jul  6 10:01:47 camlinux kernel: [667912.269564] Hardware name: GIGABYTE P35V3/P35V3, BIOS P35V3.FB08 11/28/2014
Jul  6 10:01:47 camlinux kernel: [667912.269585] Workqueue: events intel_mmio_flip_work_func [i915]
Jul  6 10:01:47 camlinux kernel: [667912.269586]  0000000000000286 00000000bb8a570e ffff88011dc87d20 ffffffff813e9c53
Jul  6 10:01:47 camlinux kernel: [667912.269589]  ffff88011dc87d68 ffffffffc0421a50 ffff88011dc87d58 ffffffff81080fb2
Jul  6 10:01:47 camlinux kernel: [667912.269591]  ffff8800caf1c8c0 ffff88042fb16500 ffff88042fb1ae00 0000000000000100
Jul  6 10:01:47 camlinux kernel: [667912.269594] Call Trace:
Jul  6 10:01:47 camlinux kernel: [667912.269597]  [<ffffffff813e9c53>] dump_stack+0x63/0x90
Jul  6 10:01:47 camlinux kernel: [667912.269601]  [<ffffffff81080fb2>] warn_slowpath_common+0x82/0xc0
Jul  6 10:01:47 camlinux kernel: [667912.269603]  [<ffffffff8108104c>] warn_slowpath_fmt+0x5c/0x80
Jul  6 10:01:47 camlinux kernel: [667912.269607]  [<ffffffff8102d66c>] ? __switch_to+0x1dc/0x5c0
Jul  6 10:01:47 camlinux kernel: [667912.269626]  [<ffffffffc03bac9e>] intel_mmio_flip_work_func+0x38e/0x3d0 [i915]
Jul  6 10:01:47 camlinux kernel: [667912.269630]  [<ffffffff8109a052>] process_one_work+0x162/0x480
Jul  6 10:01:47 camlinux kernel: [667912.269633]  [<ffffffff8109a3bb>] worker_thread+0x4b/0x4c0
Jul  6 10:01:47 camlinux kernel: [667912.269635]  [<ffffffff8109a370>] ? process_one_work+0x480/0x480
Jul  6 10:01:47 camlinux kernel: [667912.269638]  [<ffffffff810a0588>] kthread+0xd8/0xf0
Jul  6 10:01:47 camlinux kernel: [667912.269640]  [<ffffffff810a04b0>] ? kthread_create_on_node+0x1e0/0x1e0
Jul  6 10:01:47 camlinux kernel: [667912.269642]  [<ffffffff8182568f>] ret_from_fork+0x3f/0x70
Jul  6 10:01:47 camlinux kernel: [667912.269645]  [<ffffffff810a04b0>] ? kthread_create_on_node+0x1e0/0x1e0
Jul  6 10:01:47 camlinux kernel: [667912.269646] ---[ end trace d59d4d94c9a21278 ]---
Jul  6 10:01:47 camlinux kernel: [667912.271357] drm/i915: Resetting chip after gpu hang

```

Ive already removed the oibaf drivers, and its now using the default nouveau libs, but there is obviously something else still running and messing with it.

What do now?

Can provide whatever else you might need to help resolve this.

---

### Post by vertigo420 on 2016-07-06
Anyone got any ideas?

---

### Post by ppattard on 2016-08-01
> **vertigo420 said:**
> Anyone got any ideas?

I don't have any idea on the origin of your problem as I'm not  expert. But at least I found someone else who reported a similar problem  with exactly same stack trace. Check the bug report here:  [https://bugs.freedesktop.org/show_bug.cgi?id=96891](https://bugs.freedesktop.org/show_bug.cgi?id=96891)

Unfortunately there is no reply either but it looks quite recent as well.


Both of you are using the oibaf drivers. I'm tempted by these as the support in Xenial for ATI is really bad. But if it's the price to pay I'm not that sure...

---

