---
title: "Debugging system crashes?"
date: 2015-02-19
forum: General Help
---

### Post by eezacque on 2015-02-19
Every week or so, my system crashes: mouse and keyboard usually dead, every now and then, I am able to ctrl-alt-F2 into a terminal, and I can ssh back into my machine.
There doesn't seem to be a process consuming a lot of resources. Memory test seems to be ok. Sometimes, not always, I can save a kernel trace. This week's trace:

Feb 19 14:25:39 behemoth kernel: [242133.861161] ------------[ cut here ]------------
Feb 19 14:25:39 behemoth kernel: [242133.861185] WARNING: CPU: 6 PID: 1908 at /build/buildd/linux-3.16.0/drivers/gpu/drm/i915/intel_display.c:3324 intel_crtc_wait_for_pending_flips+0x16c/0x180 [i915]()
Feb 19 14:25:39 behemoth kernel: [242133.861186] Modules linked in: joydev wacom bridge stp llc pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) ipt_MASQUERADE iptable_nat nf_nat_ipv4 xt_CHECKSUM iptable_mangle snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic ip6t_REJECT xt_hl ip6t_rt nf_conntrack_ipv6 nf_defrag_ipv6 ipt_REJECT xt_LOG xt_limit xt_tcpudp xt_addrtype nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack bnep wl(POE) rfcomm ip6table_filter ip6_tables nf_conntrack_netbios_ns nf_conntrack_broadcast nf_nat_ftp nf_nat nf_conntrack_ftp nf_conntrack iptable_filter btusb intel_rapl ip_tables hid_generic bluetooth x86_pkg_temp_thermal x_tables intel_powerclamp usbhid 6lowpan_iphc kvm_intel hid snd_hda_intel kvm snd_hda_controller snd_hda_codec snd_hwdep snd_pcm eeepc_wmi crct10dif_pclmul i915 crc32_pclmul asus_wmi snd_seq_midi sparse_keymap snd_seq_midi_event ghash_clmulni_intel mxm_wmi snd_rawmidi aesni_intel cfg80211 snd_seq aes_x86_64 snd_seq_device lrw snd_timer gf128mul drm_kms_helper glue_helper ablk_helper drm cryptd snd mei_me i2c_algo_bit mei soundcore shpchp serio_raw tpm_infineon video wmi acpi_pad mac_hid binfmt_misc parport_pc ppdev coretemp lp parport e1000e psmouse ahci ptp libahci pps_core
Feb 19 14:25:39 behemoth kernel: [242133.861219] CPU: 6 PID: 1908 Comm: Xorg Tainted: P           OE 3.16.0-30-generic #40-Ubuntu
Feb 19 14:25:39 behemoth kernel: [242133.861219] Hardware name: ASUS All Series/Z97-PRO(Wi-Fi ac), BIOS 2012 09/30/2014
Feb 19 14:25:39 behemoth kernel: [242133.861220]  0000000000000009 ffff8804267d7c18 ffffffff8178236b 0000000000000000
Feb 19 14:25:39 behemoth kernel: [242133.861221]  ffff8804267d7c50 ffffffff8106feed 0000000000000000 ffff8804285d3000
Feb 19 14:25:39 behemoth kernel: [242133.861223]  ffff880426148210 ffff880426215800 ffff880426215800 ffff8804267d7c60
Feb 19 14:25:39 behemoth kernel: [242133.861224] Call Trace:
Feb 19 14:25:39 behemoth kernel: [242133.861229]  [<ffffffff8178236b>] dump_stack+0x45/0x56
Feb 19 14:25:39 behemoth kernel: [242133.861232]  [<ffffffff8106feed>] warn_slowpath_common+0x7d/0xa0
Feb 19 14:25:39 behemoth kernel: [242133.861234]  [<ffffffff8106ffca>] warn_slowpath_null+0x1a/0x20
Feb 19 14:25:39 behemoth kernel: [242133.861242]  [<ffffffffc058f03c>] intel_crtc_wait_for_pending_flips+0x16c/0x180 [i915]
Feb 19 14:25:39 behemoth kernel: [242133.861245]  [<ffffffff810b9740>] ? prepare_to_wait_event+0x100/0x100
Feb 19 14:25:39 behemoth kernel: [242133.861253]  [<ffffffffc0591b03>] intel_crtc_disable_planes+0x33/0x1c0 [i915]
Feb 19 14:25:39 behemoth kernel: [242133.861255]  [<ffffffff817874fb>] ? __ww_mutex_lock+0x1b/0xb0
Feb 19 14:25:39 behemoth kernel: [242133.861262]  [<ffffffffc0592a47>] haswell_crtc_disable+0x57/0x2d0 [i915]
Feb 19 14:25:39 behemoth kernel: [242133.861264]  [<ffffffff81788152>] ? mutex_lock+0x12/0x30
Feb 19 14:25:39 behemoth kernel: [242133.861272]  [<ffffffffc0593477>] intel_crtc_update_dpms+0x67/0xa0 [i915]
Feb 19 14:25:39 behemoth kernel: [242133.861280]  [<ffffffffc0597b09>] intel_connector_dpms+0x59/0x70 [i915]
Feb 19 14:25:39 behemoth kernel: [242133.861289]  [<ffffffffc03cce19>] drm_mode_obj_set_property_ioctl+0x399/0x3a0 [drm]
Feb 19 14:25:39 behemoth kernel: [242133.861295]  [<ffffffffc03cce50>] drm_mode_connector_property_set_ioctl+0x30/0x40 [drm]
Feb 19 14:25:39 behemoth kernel: [242133.861299]  [<ffffffffc03bba4f>] drm_ioctl+0x1df/0x680 [drm]
Feb 19 14:25:39 behemoth kernel: [242133.861303]  [<ffffffff811f51f8>] do_vfs_ioctl+0x2c8/0x4a0
Feb 19 14:25:39 behemoth kernel: [242133.861305]  [<ffffffff811e36f1>] ? __sb_end_write+0x31/0x60
Feb 19 14:25:39 behemoth kernel: [242133.861307]  [<ffffffff811e1262>] ? vfs_write+0x1b2/0x1f0
Feb 19 14:25:39 behemoth kernel: [242133.861308]  [<ffffffff811f5451>] SyS_ioctl+0x81/0xa0
Feb 19 14:25:39 behemoth kernel: [242133.861311]  [<ffffffff8178a3ad>] system_call_fastpath+0x1a/0x1f
Feb 19 14:25:39 behemoth kernel: [242133.861311] ---[ end trace 7e2953dffb03ce07 ]---


Any clue on how to corner this issue is appreciated...

---

### Post by ian-weisser on 2015-02-20
Does a .crash file get created in /var/crash?

---

### Post by eezacque on 2015-02-20
> **ian-weisser said:**
> Does a .crash file get created in /var/crash?

No.

---

