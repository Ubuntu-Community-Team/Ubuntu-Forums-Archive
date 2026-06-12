---
title: "Kernel lockup, what should I be looking for?"
date: 2019-08-09
forum: General Help
---

### Post by dbarron on 2019-08-09
Ok, I've been experiencing some randomish lockups, here's journalctl log of the last incident.  Any suggestion of what to look for?
```
Aug 09 06:54:11 desktop kernel: watchdog: BUG: soft lockup - CPU#7 stuck for 22s! [(md-udevd):4845]
Aug 09 06:54:11 desktop kernel: Modules linked in: xt_tcpudp ip6t_REJECT nf_reject_ipv6 ipt_REJECT nf_reject_ipv4 xt_multiport xt_owner ip6table_filter ip6_tables iptable_filter bpfilter zfs(PO) zunicode(PO) zavl(PO) icp(PO) zcommon(PO) znvpair(PO) spl(O) nls_iso8859_1 input_leds joydev edac_mce_amd kvm ccp irqbypass snd_hda_codec_realtek snd_hda_codec_generic ledtrig_audio snd_hda_codec_hdmi snd_hda_intel snd_hda_codec crct10dif_pclmul snd_hda_core snd_hwdep crc32_pclmul snd_pcm ghash_clmulni_intel snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq snd_seq_device snd_timer aesni_intel eeepc_wmi aes_x86_64 asus_wmi crypto_simd sparse_keymap cryptd glue_helper wmi_bmof video k10temp snd soundcore mac_hid sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_generic usbhid hid amdgpu mxm_wmi chash amd_iommu_v2 gpu_sched ttm drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops igb drm i2c_piix4 dca nvme ahci i2c_algo_bit libahci nvme_core wmi gpio_amdpt gpio_generic
Aug 09 06:54:11 desktop kernel: CPU: 7 PID: 4845 Comm: (md-udevd) Tainted: P           O L    5.0.0-23-generic #24~18.04.1-Ubuntu
Aug 09 06:54:11 desktop kernel: Hardware name: System manufacturer System Product Name/PRIME X370-PRO, BIOS 5008 06/24/2019
Aug 09 06:54:11 desktop kernel: RIP: 0010:smp_call_function_many+0x229/0x250
Aug 09 06:54:11 desktop kernel: Code: c7 e8 4b 73 8d 00 3b 05 49 2a 70 01 0f 83 5c fe ff ff 48 63 c8 48 8b 13 48 03 14 cd 20 78 7b bd 8b 4a 18 83 e1 01 74 0a f3 90 <8b> 4a 18 83 e1 01 75 f6 eb c7 48 c7 c2 20 b6 c3 bd 4c 89 e6 89 c7
Aug 09 06:54:11 desktop kernel: RSP: 0018:ffff9c1ec3de3b90 EFLAGS: 00000202 ORIG_RAX: ffffffffffffff13
Aug 09 06:54:11 desktop kernel: RAX: 0000000000000000 RBX: ffff9097467e3c00 RCX: 0000000000000001
Aug 09 06:54:11 desktop kernel: RDX: ffff909746628ea0 RSI: 0000000000000000 RDI: ffff909746027458
Aug 09 06:54:11 desktop kernel: RBP: ffff9c1ec3de3bc8 R08: 0000000000027040 R09: ffffffffbce10ad9
Aug 09 06:54:11 desktop kernel: R10: ffffc4a9d8083280 R11: 0000000000000000 R12: 0000000000000020
Aug 09 06:54:11 desktop kernel: R13: 0000000000023bc0 R14: ffffffffbc483c00 R15: 0000000000000000
Aug 09 06:54:11 desktop kernel: FS:  00007f20f9a20e00(0000) GS:ffff9097467c0000(0000) knlGS:0000000000000000
Aug 09 06:54:11 desktop kernel: CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Aug 09 06:54:11 desktop kernel: CR2: 000056410bf033f8 CR3: 0000000602b48000 CR4: 00000000003406e0
Aug 09 06:54:11 desktop kernel: Call Trace:
Aug 09 06:54:11 desktop kernel:  ? load_new_mm_cr3+0xf0/0xf0
Aug 09 06:54:11 desktop kernel:  on_each_cpu+0x2d/0x60
Aug 09 06:54:11 desktop kernel:  flush_tlb_kernel_range+0x4b/0x80
Aug 09 06:54:11 desktop kernel:  ? sync_global_pgds+0xe/0x10
Aug 09 06:54:11 desktop kernel:  __purge_vmap_area_lazy+0x77/0x160
Aug 09 06:54:11 desktop kernel:  vm_unmap_aliases+0xf9/0x130
Aug 09 06:54:11 desktop kernel:  change_page_attr_set_clr+0xc7/0x1f0
Aug 09 06:54:11 desktop kernel:  set_memory_ro+0x29/0x30
Aug 09 06:54:11 desktop kernel:  bpf_int_jit_compile+0x14a/0x3c0
Aug 09 06:54:11 desktop kernel:  bpf_prog_select_runtime+0xdf/0x140
Aug 09 06:54:11 desktop kernel:  bpf_prepare_filter+0x480/0x5c0
Aug 09 06:54:11 desktop kernel:  ? kmemdup+0x31/0x40
Aug 09 06:54:11 desktop kernel:  bpf_prog_create_from_user+0xb3/0x120
Aug 09 06:54:11 desktop kernel:  ? hardlockup_detector_perf_cleanup+0xa0/0xa0
Aug 09 06:54:11 desktop kernel:  do_seccomp+0x263/0x8e0
Aug 09 06:54:11 desktop kernel: watchdog: BUG: soft lockup - CPU#7 stuck for 22s! [(md-udevd):4845]
Aug 09 06:54:11 desktop kernel: Modules linked in: xt_tcpudp ip6t_REJECT nf_reject_ipv6 ipt_REJECT nf_reject_ipv4 xt_multiport xt_owner ip6table_filter ip6_tables iptable_filter bpfilter zfs(PO) zunicode(PO) zavl(PO) icp(PO) zcommon(PO) znvpair(PO) spl(O) nls_iso8859_1 input_leds joydev edac_mce_amd kvm ccp irqbypass snd_hda_codec_realtek snd_hda_codec_generic ledtrig_audio snd_hda_codec_hdmi snd_hda_intel snd_hda_codec crct10dif_pclmul snd_hda_core snd_hwdep crc32_pclmul snd_pcm ghash_clmulni_intel snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq snd_seq_device snd_timer aesni_intel eeepc_wmi aes_x86_64 asus_wmi crypto_simd sparse_keymap cryptd glue_helper wmi_bmof video k10temp snd soundcore mac_hid sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_generic usbhid hid amdgpu mxm_wmi chash amd_iommu_v2 gpu_sched ttm drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops igb drm i2c_piix4 dca nvme ahci i2c_algo_bit libahci nvme_core wmi gpio_amdpt gpio_generic
Aug 09 06:54:11 desktop kernel: CPU: 7 PID: 4845 Comm: (md-udevd) Tainted: P           O L    5.0.0-23-generic #24~18.04.1-Ubuntu
Aug 09 06:54:11 desktop kernel: Hardware name: System manufacturer System Product Name/PRIME X370-PRO, BIOS 5008 06/24/2019
Aug 09 06:54:11 desktop kernel: RIP: 0010:smp_call_function_many+0x229/0x250
Aug 09 06:54:11 desktop kernel: Code: c7 e8 4b 73 8d 00 3b 05 49 2a 70 01 0f 83 5c fe ff ff 48 63 c8 48 8b 13 48 03 14 cd 20 78 7b bd 8b 4a 18 83 e1 01 74 0a f3 90 <8b> 4a 18 83 e1 01 75 f6 eb c7 48 c7 c2 20 b6 c3 bd 4c 89 e6 89 c7
Aug 09 06:54:11 desktop kernel: RSP: 0018:ffff9c1ec3de3b90 EFLAGS: 00000202 ORIG_RAX: ffffffffffffff13
Aug 09 06:54:11 desktop kernel: RAX: 0000000000000000 RBX: ffff9097467e3c00 RCX: 0000000000000001
Aug 09 06:54:11 desktop kernel: RDX: ffff909746628ea0 RSI: 0000000000000000 RDI: ffff909746027458
Aug 09 06:54:11 desktop kernel: RBP: ffff9c1ec3de3bc8 R08: 0000000000027040 R09: ffffffffbce10ad9
Aug 09 06:54:11 desktop kernel: R10: ffffc4a9d8083280 R11: 0000000000000000 R12: 0000000000000020
Aug 09 06:54:11 desktop kernel: R13: 0000000000023bc0 R14: ffffffffbc483c00 R15: 0000000000000000
Aug 09 06:54:11 desktop kernel: FS:  00007f20f9a20e00(0000) GS:ffff9097467c0000(0000) knlGS:0000000000000000
Aug 09 06:54:11 desktop kernel: CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Aug 09 06:54:11 desktop kernel: CR2: 000056410bf033f8 CR3: 0000000602b48000 CR4: 00000000003406e0
Aug 09 06:54:11 desktop kernel: Call Trace:
Aug 09 06:54:11 desktop kernel:  ? load_new_mm_cr3+0xf0/0xf0
Aug 09 06:54:11 desktop kernel:  on_each_cpu+0x2d/0x60
Aug 09 06:54:11 desktop kernel:  flush_tlb_kernel_range+0x4b/0x80
Aug 09 06:54:11 desktop kernel:  ? sync_global_pgds+0xe/0x10
Aug 09 06:54:11 desktop kernel:  __purge_vmap_area_lazy+0x77/0x160
Aug 09 06:54:11 desktop kernel:  vm_unmap_aliases+0xf9/0x130
Aug 09 06:54:11 desktop kernel:  change_page_attr_set_clr+0xc7/0x1f0
Aug 09 06:54:11 desktop kernel:  set_memory_ro+0x29/0x30
Aug 09 06:54:11 desktop kernel:  bpf_int_jit_compile+0x14a/0x3c0
Aug 09 06:54:11 desktop kernel:  bpf_prog_select_runtime+0xdf/0x140
Aug 09 06:54:11 desktop kernel:  bpf_prepare_filter+0x480/0x5c0
Aug 09 06:54:11 desktop kernel:  ? kmemdup+0x31/0x40
Aug 09 06:54:11 desktop kernel:  bpf_prog_create_from_user+0xb3/0x120
Aug 09 06:54:11 desktop kernel:  ? hardlockup_detector_perf_cleanup+0xa0/0xa0
Aug 09 06:54:11 desktop kernel:  do_seccomp+0x263/0x8e0


```

---

### Post by cruzer001 on 2019-08-09
I don't see any mention of what kernel this is.  Have you tried other kernels?

---

### Post by Autodave on 2019-08-09
Can you give us some info on your system?  Are you sure that you aren't having an overheat problem?  Have you ran a memory test yet?

---

### Post by dbarron on 2019-08-09
That's a 5.0 kernel, it appears to be kernel and maybe distro agnostic, so hardware is most likely...I think.   I don't think I'm having an overheating issue.  I haven't ran a full memory test but will do that when I logoff in a short while.

---

### Post by dbarron on 2019-08-10
Ok, ran memtest+ for about 4 hours, no overheating and no errors.

---

### Post by cruzer001 on 2019-08-10
Like Autodave suggested, more info please.
```
inxi -b
```
may have to install it

---

