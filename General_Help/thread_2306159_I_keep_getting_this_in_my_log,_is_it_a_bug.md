---
title: "I keep getting this in my log, is it a bug?"
date: 2015-12-12
forum: General Help
---

### Post by MechaMechanism on 2015-12-12
Is this a bug I should report?  I keep getting this constantly in the log.  I don't notice it in my use of the computer.
System76 Wild Dog Pro.
Intel HD 530 graphics.

```
Dec 12 16:07:32 frontier kernel: [80936.949588] ------------[ cut here ]------------
Dec 12 16:07:32 frontier kernel: [80936.949598] WARNING: CPU: 0 PID: 1143 at /build/linux-26_gwp/linux-4.2.0/drivers/gpu/drm/i915/intel_pm.c:3404 skl_update_other_pipe_wm+0x1de/0x1f0 [i915]()
Dec 12 16:07:32 frontier kernel: [80936.949599] WARN_ON(!wm_changed)
Dec 12 16:07:32 frontier kernel: [80936.949600] Modules linked in: udp_diag tcp_diag inet_diag binfmt_misc drbg ansi_cprng ctr ccm hid_logitech_hidpp hid_generic hid_logitech_dj rfcomm bnep btusb btrtl btbcm btintel usbhid bluetooth uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core v4l2_common snd_usb_audio videodev snd_usbmidi_lib media pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) arc4 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic intel_rapl iosf_mbi snd_hda_intel x86_pkg_temp_thermal intel_powerclamp snd_hda_codec coretemp snd_hda_core snd_hwdep kvm_intel kvm crct10dif_pclmul snd_pcm crc32_pclmul iwlmvm snd_seq_midi snd_seq_midi_event snd_rawmidi mac80211 aesni_intel snd_seq snd_seq_device aes_x86_64 snd_timer lrw gf128mul glue_helper ablk_helper cryptd snd iwlwifi input_leds serio_raw soundcore cfg80211 shpchp mei_me mei 8250_fintek intel_lpss_acpi intel_lpss acpi_als tpm_infineon kfifo_buf acpi_pad industrialio mac_hid ip6t_REJECT nf_reject_ipv6 nf_log_ipv6 xt_hl ip6t_rt nf_conntrack_ipv6 nf_defrag_ipv6 ipt_REJECT nf_reject_ipv4 nf_log_ipv4 nf_log_common xt_LOG xt_limit xt_tcpudp xt_addrtype nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack ip6table_filter ip6_tables nf_conntrack_netbios_ns nf_conntrack_broadcast nf_nat_ftp nf_nat nf_conntrack_ftp nf_conntrack iptable_filter ip_tables parport_pc ppdev x_tables lp parport autofs4 btrfs xor raid6_pq dm_mirror dm_region_hash dm_log uas usb_storage i915 e1000e psmouse ptp pps_core i2c_algo_bit drm_kms_helper drm ahci libahci wmi video pinctrl_sunrisepoint pinctrl_intel i2c_hid hid
Dec 12 16:07:32 frontier kernel: [80936.949647] CPU: 0 PID: 1143 Comm: Xorg Tainted: G        W  OE   4.2.0-19-generic #23-Ubuntu
Dec 12 16:07:32 frontier kernel: [80936.949649] Hardware name: System76, Inc. Wild Dog Pro/H170-D3HP-CF, BIOS F2 10/19/2015
Dec 12 16:07:32 frontier kernel: [80936.949651]  0000000000000000 00000000d256a7c7 ffff8804593eb518 ffffffff817e93f9
Dec 12 16:07:32 frontier kernel: [80936.949652]  0000000000000000 ffff8804593eb570 ffff8804593eb558 ffffffff8107b3d6
Dec 12 16:07:32 frontier kernel: [80936.949654]  ffff8804593eb620 ffff8804593eb6c4 ffff88045dc2d000 ffff88045dc2c000
Dec 12 16:07:32 frontier kernel: [80936.949655] Call Trace:
Dec 12 16:07:32 frontier kernel: [80936.949659]  [<ffffffff817e93f9>] dump_stack+0x45/0x57
Dec 12 16:07:32 frontier kernel: [80936.949662]  [<ffffffff8107b3d6>] warn_slowpath_common+0x86/0xc0
Dec 12 16:07:32 frontier kernel: [80936.949663]  [<ffffffff8107b465>] warn_slowpath_fmt+0x55/0x70
Dec 12 16:07:32 frontier kernel: [80936.949668]  [<ffffffffc01abb9e>] skl_update_other_pipe_wm+0x1de/0x1f0 [i915]
Dec 12 16:07:32 frontier kernel: [80936.949674]  [<ffffffffc01abd6b>] skl_update_wm+0x1bb/0x740 [i915]
Dec 12 16:07:32 frontier kernel: [80936.949683]  [<ffffffffc01f7837>] ? gen9_read32+0xf7/0x2d0 [i915]
Dec 12 16:07:32 frontier kernel: [80936.949691]  [<ffffffffc01e02a2>] ? i915_get_vblank_timestamp+0x62/0xa0 [i915]
Dec 12 16:07:32 frontier kernel: [80936.949697]  [<ffffffffc01af4be>] intel_update_watermarks+0x1e/0x30 [i915]
Dec 12 16:07:32 frontier kernel: [80936.949706]  [<ffffffffc0212ad9>] intel_finish_crtc_commit+0x169/0x190 [i915]
Dec 12 16:07:32 frontier kernel: [80936.949710]  [<ffffffffc0100793>] drm_atomic_helper_commit_planes_on_crtc+0x143/0x260 [drm_kms_helper]
Dec 12 16:07:32 frontier kernel: [80936.949719]  [<ffffffffc022be3b>] intel_atomic_commit+0x6b/0x100 [i915]
Dec 12 16:07:32 frontier kernel: [80936.949728]  [<ffffffffc009bd47>] drm_atomic_commit+0x37/0x60 [drm]
Dec 12 16:07:32 frontier kernel: [80936.949732]  [<ffffffffc00ff0cf>] drm_atomic_helper_disable_plane+0xef/0x130 [drm_kms_helper]
Dec 12 16:07:32 frontier kernel: [80936.949734]  [<ffffffff81211700>] ? poll_select_copy_remaining+0x140/0x140
Dec 12 16:07:32 frontier kernel: [80936.949740]  [<ffffffffc008b93a>] __setplane_internal+0x23a/0x2f0 [drm]
Dec 12 16:07:32 frontier kernel: [80936.949741]  [<ffffffff81211700>] ? poll_select_copy_remaining+0x140/0x140
Dec 12 16:07:32 frontier kernel: [80936.949747]  [<ffffffffc008bb1b>] drm_mode_cursor_universal+0x12b/0x210 [drm]
Dec 12 16:07:32 frontier kernel: [80936.949748]  [<ffffffff817edf2f>] ? __ww_mutex_lock+0x5f/0xa0
Dec 12 16:07:32 frontier kernel: [80936.949753]  [<ffffffffc008bc81>] drm_mode_cursor_common+0x81/0x180 [drm]
Dec 12 16:07:32 frontier kernel: [80936.949759]  [<ffffffffc008fca0>] drm_mode_cursor_ioctl+0x50/0x70 [drm]
Dec 12 16:07:32 frontier kernel: [80936.949763]  [<ffffffffc0080495>] drm_ioctl+0x125/0x610 [drm]
Dec 12 16:07:32 frontier kernel: [80936.949769]  [<ffffffffc008fc50>] ? drm_mode_setcrtc+0x500/0x500 [drm]
Dec 12 16:07:32 frontier kernel: [80936.949771]  [<ffffffff81210a25>] do_vfs_ioctl+0x295/0x480
Dec 12 16:07:32 frontier kernel: [80936.949772]  [<ffffffff81087f71>] ? __set_task_blocked+0x41/0xa0
Dec 12 16:07:32 frontier kernel: [80936.949774]  [<ffffffff81210c89>] SyS_ioctl+0x79/0x90
Dec 12 16:07:32 frontier kernel: [80936.949775]  [<ffffffff8108ab9e>] ? SyS_rt_sigprocmask+0x8e/0xc0
Dec 12 16:07:32 frontier kernel: [80936.949777]  [<ffffffff817f01f2>] entry_SYSCALL_64_fastpath+0x16/0x75
Dec 12 16:07:32 frontier kernel: [80936.949778] ---[ end trace d3216d9b2aeab5a3 ]---
```

---

### Post by sandyd on 2015-12-12
See [https://bugs.freedesktop.org/show_bug.cgi?id=89055](https://bugs.freedesktop.org/show_bug.cgi?id=89055)

Seems to affect nothing other than have that message in the logs.
It has been fixed in the nightly builds for intel drm, and if you want to test it out, it may arrive in xorg-edgers

---

### Post by MechaMechanism on 2015-12-12
Good to know.  I'll just wait till 16.04 or .10.

---

