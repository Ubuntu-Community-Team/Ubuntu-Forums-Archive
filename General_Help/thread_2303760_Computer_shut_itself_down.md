---
title: "Computer shut itself down"
date: 2015-11-21
forum: General Help
---

### Post by mistcloud-misty on 2015-11-21
Ubuntu 14.04, 64-bit, Nvidia Geforce 940M

Battery was fully charged and temperature was not warm at all. It turned back on without any problems. 

The shut down was simple: I heard the usual 'click' as if someone had pushed the shut down button and it was off, without ever going to the logout/purple screen. 

This is what I have in dmesg: 
```
[   39.460814] WARNING: CPU: 0 PID: 1458 at /home/apw/COD/linux/drivers/gpu/drm/i915/intel_display.c:9310 check_crtc_state+0x275/0x330 [i915]()
[   39.460815] pipe state doesn't match!
[   39.460817] Modules linked in: bbswitch(OF) ctr ccm rfcomm bnep bluetooth binfmt_misc nls_iso8859_1 snd_hda_codec_realtek nvidia(POF) ip6t_REJECT xt_hl ip6t_rt nf_conntrack_ipv6 nf_defrag_ipv6 ipt_REJECT xt_LOG xt_limit xt_tcpudp xt_addrtype uvcvideo nf_conntrack_ipv4 nf_defrag_ipv4 videobuf2_vmalloc xt_conntrack videobuf2_memops videobuf2_core rts5139(C) videodev ip6table_filter ip6_tables nf_conntrack_netbios_ns nf_conntrack_broadcast nf_nat_ftp nf_nat nf_conntrack_ftp nf_conntrack iptable_filter ip_tables x_tables x86_pkg_temp_thermal coretemp i915 kvm_intel kvm crct10dif_pclmul crc32_pclmul asus_nb_wmi arc4 asus_wmi mt7630e(OF) ghash_clmulni_intel sparse_keymap mxm_wmi mac80211 snd_hda_intel snd_hda_codec snd_hwdep snd_pcm cfg80211 aesni_intel snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi drm_kms_helper snd_seq drm aes_x86_64 lrw snd_seq_device gf128mul snd_timer glue_helper eeprom_93cx6 snd crc_ccitt ablk_helper cryptd joydev serio_raw soundcore mei_me mei i2c_algo_bit lpc_ich wmi acpi_pad video shpchp mac_hid parport_pc ppdev lp parport psmouse ahci r8169 libahci mii
[   39.460877] CPU: 0 PID: 1458 Comm: Xorg Tainted: PF       WC O 3.13.11-03131107-generic #201409181736
[   39.460878] Hardware name: ASUSTeK COMPUTER INC. X555LB/X555LB, BIOS X555LB.408 07/07/2015
[   39.460880]  000000000000245e ffff88024e9118a8 ffffffff817471b4 0000000000000007
[   39.460884]  ffff88024e9118f8 ffff88024e9118e8 ffffffff81069acc ffff88024e911918
[   39.460887]  ffff880251a24000 ffff88024f5f0328 ffff88024f5f0000 ffff880251a246e0
[   39.460890] Call Trace:
[   39.460896]  [<ffffffff817471b4>] dump_stack+0x46/0x58
[   39.460901]  [<ffffffff81069acc>] warn_slowpath_common+0x8c/0xc0
[   39.460904]  [<ffffffff81069bb6>] warn_slowpath_fmt+0x46/0x50
[   39.460921]  [<ffffffffa051a5a2>] ? intel_ddi_get_config+0x102/0x190 [i915]
[   39.460935]  [<ffffffffa0504e55>] check_crtc_state+0x275/0x330 [i915]
[   39.460950]  [<ffffffffa0510e15>] intel_modeset_check_state+0x65/0xa0 [i915]
[   39.460963]  [<ffffffffa0510e75>] intel_set_mode+0x25/0x30 [i915]
[   39.460975]  [<ffffffffa051111d>] intel_crtc_set_config+0x29d/0x310 [i915]
[   39.460989]  [<ffffffffa01919fc>] drm_mode_set_config_internal+0x5c/0xe0 [drm]
[   39.461002]  [<ffffffffa0194f60>] drm_mode_setcrtc+0x310/0x4c0 [drm]
[   39.461011]  [<ffffffffa0184e3a>] drm_ioctl+0x4da/0x600 [drm]
[   39.461022]  [<ffffffffa0194c50>] ? drm_mode_setplane+0x3f0/0x3f0 [drm]
[   39.461026]  [<ffffffff811daab5>] do_vfs_ioctl+0x75/0x2c0
[   39.461028]  [<ffffffff811dad91>] SyS_ioctl+0x91/0xb0
[   39.461032]  [<ffffffff8175c86d>] system_call_fastpath+0x1a/0x1f
[   39.461034] ---[ end trace 16dd619d4986a79a ]---
[   40.487729] [UFW BLOCK] IN=wlan0 OUT= MAC=40:b8:9a:76:8a:17:48:5a:b6:f8:10:cd:08:00 SRC=74.125.141.189 DST=192.168.0.17 LEN=111 TOS=0x00 PREC=0x00 TTL=39 ID=50131 PROTO=TCP SPT=443 DPT=53001 WINDOW=641 RES=0x00 ACK PSH URGP=0 
[   41.122500] [UFW BLOCK] IN=wlan0 OUT= MAC=40:b8:9a:76:8a:17:48:5a:b6:f8:10:cd:08:00 SRC=173.194.123.117 DST=192.168.0.17 LEN=111 TOS=0x00 PREC=0x00 TTL=52 ID=40092 PROTO=TCP SPT=443 DPT=32869 WINDOW=1587 RES=0x00 ACK PSH URGP=0 
[   41.124337] [drm:intel_pipe_config_compare] *ERROR* mismatch in ips_enabled (expected 1, found 0)
[   41.124339] ------------[ cut here ]------------
[   41.124360] WARNING: CPU: 0 PID: 1458 at /home/apw/COD/linux/drivers/gpu/drm/i915/intel_display.c:9310 check_crtc_state+0x275/0x330 [i915]()
[   41.124361] pipe state doesn't match!
[   41.124363] Modules linked in: bbswitch(OF) ctr ccm rfcomm bnep bluetooth binfmt_misc nls_iso8859_1 snd_hda_codec_realtek nvidia(POF) ip6t_REJECT xt_hl ip6t_rt nf_conntrack_ipv6 nf_defrag_ipv6 ipt_REJECT xt_LOG xt_limit xt_tcpudp xt_addrtype uvcvideo nf_conntrack_ipv4 nf_defrag_ipv4 videobuf2_vmalloc xt_conntrack videobuf2_memops videobuf2_core rts5139(C) videodev ip6table_filter ip6_tables nf_conntrack_netbios_ns nf_conntrack_broadcast nf_nat_ftp nf_nat nf_conntrack_ftp nf_conntrack iptable_filter ip_tables x_tables x86_pkg_temp_thermal coretemp i915 kvm_intel kvm crct10dif_pclmul crc32_pclmul asus_nb_wmi arc4 asus_wmi mt7630e(OF) ghash_clmulni_intel sparse_keymap mxm_wmi mac80211 snd_hda_intel snd_hda_codec snd_hwdep snd_pcm cfg80211 aesni_intel snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi drm_kms_helper snd_seq drm aes_x86_64 lrw snd_seq_device gf128mul snd_timer glue_helper eeprom_93cx6 snd crc_ccitt ablk_helper cryptd joydev serio_raw soundcore mei_me mei i2c_algo_bit lpc_ich wmi acpi_pad video shpchp mac_hid parport_pc ppdev lp parport psmouse ahci r8169 libahci mii
[   41.124423] CPU: 0 PID: 1458 Comm: Xorg Tainted: PF       WC O 3.13.11-03131107-generic #201409181736
[   41.124425] Hardware name: ASUSTeK COMPUTER INC. X555LB/X555LB, BIOS X555LB.408 07/07/2015
[   41.124426]  000000000000245e ffff88024e9118a8 ffffffff817471b4 0000000000000007
[   41.124430]  ffff88024e9118f8 ffff88024e9118e8 ffffffff81069acc ffff88024e911918
[   41.124433]  ffff880251a24000 ffff88024f5f0328 ffff88024f5f0000 ffff880251a246e0
[   41.124436] Call Trace:
[   41.124442]  [<ffffffff817471b4>] dump_stack+0x46/0x58
[   41.124447]  [<ffffffff81069acc>] warn_slowpath_common+0x8c/0xc0
[   41.124450]  [<ffffffff81069bb6>] warn_slowpath_fmt+0x46/0x50
[   41.124467]  [<ffffffffa051a5a2>] ? intel_ddi_get_config+0x102/0x190 [i915]
[   41.124480]  [<ffffffffa0504e55>] check_crtc_state+0x275/0x330 [i915]
[   41.124495]  [<ffffffffa0510e15>] intel_modeset_check_state+0x65/0xa0 [i915]
[   41.124508]  [<ffffffffa0510e75>] intel_set_mode+0x25/0x30 [i915]
[   41.124520]  [<ffffffffa051111d>] intel_crtc_set_config+0x29d/0x310 [i915]
[   41.124535]  [<ffffffffa01919fc>] drm_mode_set_config_internal+0x5c/0xe0 [drm]
[   41.124548]  [<ffffffffa0194f60>] drm_mode_setcrtc+0x310/0x4c0 [drm]
[   41.124557]  [<ffffffffa0184e3a>] drm_ioctl+0x4da/0x600 [drm]
[   41.124569]  [<ffffffffa0194c50>] ? drm_mode_setplane+0x3f0/0x3f0 [drm]
[   41.124573]  [<ffffffff811daab5>] do_vfs_ioctl+0x75/0x2c0
[   41.124577]  [<ffffffff811c87de>] ? vfs_write+0x1ae/0x1f0
[   41.124580]  [<ffffffff811dad91>] SyS_ioctl+0x91/0xb0
[   41.124583]  [<ffffffff8175c86d>] system_call_fastpath+0x1a/0x1f
```

I am using an older kernel, 3.13 which is the only way I can get the wireless and the graphics card to work together.

---

### Post by ian-weisser on 2015-11-21
What about logs from before the shutdown?

---

### Post by mistcloud-misty on 2015-11-21
```
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293157] [drm:intel_pipe_config_compare] *ERROR* mismatch in ips_enabled (expected 1, found 0)
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293158] ------------[ cut here ]------------
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293180] WARNING: CPU: 0 PID: 1210 at /home/apw/COD/linux/drivers/gpu/drm/i915/intel_display.c:9310 check_crtc_state+0x275/0x330 [i915]()
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293180] pipe state doesn't match!
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293206] Modules linked in: xt_recent xt_hl ip6t_rt nf_conntrack_ipv6 nf_defrag_ipv6 ipt_REJECT xt_LOG xt_limit xt_tcpudp xt_addrtype nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack ip6table_filter ip6_tables nf_conntrack_netbios_ns nf_conntrack_broadcast nf_nat_ftp nf_nat nf_conntrack_ftp nf_conntrack iptable_filter ip_tables x_tables bbswitch(OF) ctr ccm bnep rfcomm bluetooth binfmt_misc nls_iso8859_1 nvidia(POF) snd_hda_codec_realtek uvcvideo videobuf2_vmalloc videobuf2_memops rts5139(C) videobuf2_core videodev x86_pkg_temp_thermal coretemp snd_hda_intel kvm_intel i915 snd_hda_codec kvm snd_hwdep snd_pcm arc4 mt7630e(OF) crct10dif_pclmul snd_page_alloc snd_seq_midi snd_seq_midi_event crc32_pclmul snd_rawmidi ghash_clmulni_intel mac80211 cfg80211 aesni_intel snd_seq drm_kms_helper aes_x86_64 asus_nb_wmi lrw asus_wmi mxm_wmi sparse_keymap gf128mul glue_helper snd_seq_device ablk_helper snd_timer cryptd eeprom_93cx6 drm snd crc_ccitt joydev serio_raw soundcore mei_me mei acpi_pad video wmi i2c_algo_bit mac_hid lpc_ich shpchp parport_pc ppdev lp parport psmouse ahci r8169 libahci mii
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293224] CPU: 0 PID: 1210 Comm: Xorg Tainted: PF       WC O 3.13.11-03131107-generic #201409181736
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293225] Hardware name: ASUSTeK COMPUTER INC. X555LB/X555LB, BIOS X555LB.408 07/07/2015
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293228]  000000000000245e ffff880251029638 ffffffff817471b4 0000000000000086
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293230]  ffff880251029688 ffff880251029678 ffffffff81069acc ffff8802510296a8
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293232]  ffff88024f2a9000 ffff880035ea9328 ffff880035ea9000 ffff88024f2a96e0
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293232] Call Trace:
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293237]  [<ffffffff817471b4>] dump_stack+0x46/0x58
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293241]  [<ffffffff81069acc>] warn_slowpath_common+0x8c/0xc0
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293243]  [<ffffffff81069bb6>] warn_slowpath_fmt+0x46/0x50
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293260]  [<ffffffffa04885a2>] ? intel_ddi_get_config+0x102/0x190 [i915]
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293273]  [<ffffffffa0472e55>] check_crtc_state+0x275/0x330 [i915]
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293287]  [<ffffffffa047ee15>] intel_modeset_check_state+0x65/0xa0 [i915]
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293299]  [<ffffffffa047ee75>] intel_set_mode+0x25/0x30 [i915]
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293311]  [<ffffffffa047f11d>] intel_crtc_set_config+0x29d/0x310 [i915]
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293324]  [<ffffffffa01259fc>] drm_mode_set_config_internal+0x5c/0xe0 [drm]
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293329]  [<ffffffffa01a7e46>] drm_fb_helper_set_par+0x66/0xe0 [drm_kms_helper]
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293332]  [<ffffffff813d78a3>] fb_set_var+0x283/0x3a0
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293335]  [<ffffffff810a809b>] ? check_preempt_wakeup+0x14b/0x260
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293337]  [<ffffffff813e5484>] fbcon_blank+0x1e4/0x2d0
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293341]  [<ffffffff8147115e>] do_unblank_screen.part.18+0x9e/0x180
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293343]  [<ffffffff81471288>] do_unblank_screen+0x48/0x80
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293346]  [<ffffffff814664c5>] complete_change_console+0x65/0xf0
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293347]  [<ffffffff8146767c>] vt_ioctl+0x112c/0x11d0
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293351]  [<ffffffff8145abb8>] tty_ioctl+0x298/0x8f0
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293354]  [<ffffffff814a21d8>] ? dev_attr_store+0x18/0x30
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293357]  [<ffffffff8123df1a>] ? flush_write_buffer+0x9a/0x100
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293359]  [<ffffffff811daab5>] do_vfs_ioctl+0x75/0x2c0
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293362]  [<ffffffff816293c5>] ? __sys_recvmsg+0x75/0x90
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293363]  [<ffffffff811dad91>] SyS_ioctl+0x91/0xb0
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293366]  [<ffffffff8175c86d>] system_call_fastpath+0x1a/0x1f
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293367] ---[ end trace aee9a8b1c8add4f6 ]---
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293524] Freezing user space processes ... (elapsed 0.001 seconds) done.
Nov 21 08:33:42 arcane-X555LB kernel: [388794.295120] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
Nov 21 08:33:42 arcane-X555LB kernel: [388794.296285] PM: Entering mem sleep
Nov 21 08:33:42 arcane-X555LB kernel: [388794.297018] Suspending console(s) (use no_console_suspend to debug)
Nov 21 08:33:42 arcane-X555LB kernel: [388794.297227] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Nov 21 08:33:42 arcane-X555LB kernel: [388794.297392] sd 0:0:0:0: [sda] Stopping disk
Nov 21 08:33:42 arcane-X555LB kernel: [388795.417751] PM: suspend of devices complete after 1120.925 msecs
Nov 21 08:33:42 arcane-X555LB kernel: [388795.432935] PM: late suspend of devices complete after 15.184 msecs
Nov 21 08:33:42 arcane-X555LB kernel: [388795.433113] pcieport 0000:00:1c.2: System wakeup enabled by ACPI
Nov 21 08:33:42 arcane-X555LB kernel: [388795.464887] xhci_hcd 0000:00:14.0: System wakeup enabled by ACPI
Nov 21 08:33:42 arcane-X555LB kernel: [388795.464945] PM: noirq suspend of devices complete after 32.017 msecs
Nov 21 08:33:42 arcane-X555LB kernel: [388795.465184] ACPI: Preparing to enter system sleep state S3
Nov 21 08:33:42 arcane-X555LB kernel: [388795.470626] PM: Saving platform NVS memory
Nov 21 08:33:42 arcane-X555LB kernel: [388795.483461] Disabling non-boot CPUs ...
Nov 21 08:33:42 arcane-X555LB kernel: [388795.484658] kvm: disabling virtualization on CPU1
Nov 21 08:33:42 arcane-X555LB kernel: [388795.584810] smpboot: CPU 1 is now offline
Nov 21 08:33:42 arcane-X555LB kernel: [388795.586198] kvm: disabling virtualization on CPU2
Nov 21 08:33:42 arcane-X555LB kernel: [388795.688774] smpboot: CPU 2 is now offline
Nov 21 08:33:42 arcane-X555LB kernel: [388795.689107] Broke affinity for irq 59
Nov 21 08:33:42 arcane-X555LB kernel: [388795.689108] Broke affinity for irq 60
Nov 21 08:33:42 arcane-X555LB kernel: [388795.689110] Broke affinity for irq 61
Nov 21 08:33:42 arcane-X555LB kernel: [388795.689112] Broke affinity for irq 62
Nov 21 08:33:42 arcane-X555LB kernel: [388795.689114] Broke affinity for irq 63
Nov 21 08:33:42 arcane-X555LB kernel: [388795.690119] kvm: disabling virtualization on CPU3
Nov 21 08:33:42 arcane-X555LB kernel: [388795.792746] smpboot: CPU 3 is now offline
Nov 21 08:33:42 arcane-X555LB kernel: [388795.795713] ACPI: Low-level resume complete
Nov 21 08:33:42 arcane-X555LB kernel: [388795.795785] PM: Restoring platform NVS memory
Nov 21 08:33:42 arcane-X555LB kernel: [388795.801624] Enabling non-boot CPUs ...
Nov 21 08:33:42 arcane-X555LB kernel: [388795.801674] x86: Booting SMP configuration:
Nov 21 08:33:42 arcane-X555LB kernel: [388795.801676] smpboot: Booting Node 0 Processor 1 APIC 0x2
Nov 21 08:33:42 arcane-X555LB kernel: [388795.814157] kvm: enabling virtualization on CPU1
Nov 21 08:33:42 arcane-X555LB kernel: [388795.816647] CPU1 is up
Nov 21 08:33:42 arcane-X555LB kernel: [388795.816667] smpboot: Booting Node 0 Processor 2 APIC 0x1
Nov 21 08:33:42 arcane-X555LB kernel: [388795.828817] kvm: enabling virtualization on CPU2
Nov 21 08:33:42 arcane-X555LB kernel: [388795.831168] CPU2 is up
Nov 21 08:33:42 arcane-X555LB kernel: [388795.831181] smpboot: Booting Node 0 Processor 3 APIC 0x3
Nov 21 08:33:42 arcane-X555LB kernel: [388795.843367] kvm: enabling virtualization on CPU3
Nov 21 08:33:42 arcane-X555LB kernel: [388795.845642] CPU3 is up
Nov 21 08:33:42 arcane-X555LB kernel: [388795.854877] ACPI: Waking up from system sleep state S3
Nov 21 08:33:42 arcane-X555LB kernel: [388795.913324] xhci_hcd 0000:00:14.0: System wakeup disabled by ACPI
Nov 21 08:33:42 arcane-X555LB kernel: [388795.993379] PM: noirq resume of devices complete after 95.883 msecs
Nov 21 08:33:42 arcane-X555LB kernel: [388795.993596] PM: early resume of devices complete after 0.197 msecs
Nov 21 08:33:42 arcane-X555LB kernel: [388795.993826] mei_me 0000:00:16.0: irq 65 for MSI/MSI-X
Nov 21 08:33:42 arcane-X555LB kernel: [388795.994028] pcieport 0000:00:1c.2: System wakeup disabled by ACPI
Nov 21 08:33:42 arcane-X555LB kernel: [388795.994236] snd_hda_intel 0000:00:1b.0: irq 67 for MSI/MSI-X
Nov 21 08:33:42 arcane-X555LB kernel: [388795.994399] ==>MT76x0_WLAN_ChipOnOff(): OnOff:1 pAd->WlanFunCtrl.word = 0xffff0103, Reg-WlanFunCtrl=0xff000202
Nov 21 08:33:42 arcane-X555LB kernel: [388795.994400] Reset(1) WlanFunCtrl.word = 0xffff020e
Nov 21 08:33:42 arcane-X555LB kernel: [388795.994451] Reset(2) WlanFunCtrl.word = 0xffff0202
Nov 21 08:33:42 arcane-X555LB kernel: [388795.994503] WlanFunCtrl.word = 0xffff0203
Nov 21 08:33:42 arcane-X555LB kernel: [388795.994563] MACVersion = 0x76502000
Nov 21 08:33:42 arcane-X555LB kernel: [388795.994569] <== MT76x0_WLAN_ChipOnOff():  pAd->WlanFunCtrl.word = 0xffff0203, Reg->WlanFunCtrl=0xffff0f03!
Nov 21 08:33:42 arcane-X555LB kernel: [388796.029191] [drm:__gen6_gt_force_wake_mt_get] *ERROR* Timed out waiting for forcewake old ack to clear.
Nov 21 08:33:42 arcane-X555LB kernel: [388796.317474] usb 1-6: reset high-speed USB device number 5 using xhci_hcd
Nov 21 08:33:42 arcane-X555LB kernel: [388796.329166] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Nov 21 08:33:42 arcane-X555LB kernel: [388796.338167] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88020e8bca80
Nov 21 08:33:42 arcane-X555LB kernel: [388796.338168] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88020e8bcac0
Nov 21 08:33:42 arcane-X555LB kernel: [388796.338169] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88020e8bcb00
Nov 21 08:33:42 arcane-X555LB kernel: [388796.338170] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff880041441980
Nov 21 08:33:42 arcane-X555LB kernel: [388796.338171] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800414419c0
Nov 21 08:33:42 arcane-X555LB kernel: [388796.339329] ata2.00: configured for UDMA/100
Nov 21 08:33:42 arcane-X555LB kernel: [388796.445509] usb 1-5: reset high-speed USB device number 2 using xhci_hcd
Nov 21 08:33:42 arcane-X555LB kernel: [388796.480347] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff880036a64940
Nov 21 08:33:42 arcane-X555LB kernel: [388796.573313] usb 1-8: reset high-speed USB device number 4 using xhci_hcd
Nov 21 08:33:42 arcane-X555LB kernel: [388796.589181] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88024edc9000
Nov 21 08:33:42 arcane-X555LB kernel: [388796.589183] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88024edc9040
Nov 21 08:33:42 arcane-X555LB kernel: [388796.589184] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88024edc9080
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613096] [drm:intel_pipe_config_compare] *ERROR* mismatch in ips_enabled (expected 1, found 0)
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613096] ------------[ cut here ]------------
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613117] WARNING: CPU: 1 PID: 22958 at /home/apw/COD/linux/drivers/gpu/drm/i915/intel_display.c:9310 check_crtc_state+0x275/0x330 [i915]()
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613117] pipe state doesn't match!
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613137] Modules linked in: xt_recent xt_hl ip6t_rt nf_conntrack_ipv6 nf_defrag_ipv6 ipt_REJECT xt_LOG xt_limit xt_tcpudp xt_addrtype nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack ip6table_filter ip6_tables nf_conntrack_netbios_ns nf_conntrack_broadcast nf_nat_ftp nf_nat nf_conntrack_ftp nf_conntrack iptable_filter ip_tables x_tables bbswitch(OF) ctr ccm bnep rfcomm bluetooth binfmt_misc nls_iso8859_1 nvidia(POF) snd_hda_codec_realtek uvcvideo videobuf2_vmalloc videobuf2_memops rts5139(C) videobuf2_core videodev x86_pkg_temp_thermal coretemp snd_hda_intel kvm_intel i915 snd_hda_codec kvm snd_hwdep snd_pcm arc4 mt7630e(OF) crct10dif_pclmul snd_page_alloc snd_seq_midi snd_seq_midi_event crc32_pclmul snd_rawmidi ghash_clmulni_intel mac80211 cfg80211 aesni_intel snd_seq drm_kms_helper aes_x86_64 asus_nb_wmi lrw asus_wmi mxm_wmi sparse_keymap gf128mul glue_helper snd_seq_device ablk_helper snd_timer cryptd eeprom_93cx6 drm snd crc_ccitt joydev serio_raw soundcore mei_me mei acpi_pad video wmi i2c_algo_bit mac_hid lpc_ich shpchp parport_pc ppdev lp parport psmouse ahci r8169 libahci mii
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613152] CPU: 1 PID: 22958 Comm: kworker/u8:12 Tainted: PF       WC O 3.13.11-03131107-generic #201409181736
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613153] Hardware name: ASUSTeK COMPUTER INC. X555LB/X555LB, BIOS X555LB.408 07/07/2015
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613157] Workqueue: events_unbound async_run_entry_fn
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613159]  000000000000245e ffff880056365868 ffffffff817471b4 ffffffff81c4b698
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613160]  ffff8800563658b8 ffff8800563658a8 ffffffff81069acc ffff8800563658d8
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613162]  ffff88024f2a9000 ffff880035ea9328 ffff880035ea9000 ffff88024f2a96e0
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613162] Call Trace:
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613168]  [<ffffffff817471b4>] dump_stack+0x46/0x58
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613170]  [<ffffffff81069acc>] warn_slowpath_common+0x8c/0xc0
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613172]  [<ffffffff81069bb6>] warn_slowpath_fmt+0x46/0x50
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613186]  [<ffffffffa04885a2>] ? intel_ddi_get_config+0x102/0x190 [i915]
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613198]  [<ffffffffa0472e55>] check_crtc_state+0x275/0x330 [i915]
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613210]  [<ffffffffa047ee15>] intel_modeset_check_state+0x65/0xa0 [i915]
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613223]  [<ffffffffa0480a3d>] intel_modeset_setup_hw_state+0x2cd/0x350 [i915]
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613229]  [<ffffffffa043c383>] __i915_drm_thaw+0x153/0x210 [i915]
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613232]  [<ffffffff813b4410>] ? pci_pm_thaw+0x90/0x90
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613237]  [<ffffffffa043cbeb>] i915_resume+0x2b/0x50 [i915]
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613240]  [<ffffffff813b4410>] ? pci_pm_thaw+0x90/0x90
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613245]  [<ffffffffa043cc26>] i915_pm_resume+0x16/0x20 [i915]
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613247]  [<ffffffff813b448e>] pci_pm_resume+0x7e/0xe0
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613249]  [<ffffffff814af996>] dpm_run_callback+0x56/0xa0
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613250]  [<ffffffff814b00de>] device_resume+0xde/0x210
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613251]  [<ffffffff814b0231>] async_resume+0x21/0x50
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613253]  [<ffffffff8109497b>] async_run_entry_fn+0x3b/0x140
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613255]  [<ffffffff8108647f>] process_one_work+0x17f/0x4c0
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613257]  [<ffffffff8108769b>] worker_thread+0x11b/0x3d0
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613259]  [<ffffffff81087580>] ? manage_workers.isra.21+0x190/0x190
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613260]  [<ffffffff8108e5e9>] kthread+0xc9/0xe0
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613261]  [<ffffffff8108e520>] ? flush_kthread_worker+0xb0/0xb0
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613263]  [<ffffffff8175c7bc>] ret_from_fork+0x7c/0xb0
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613265]  [<ffffffff8108e520>] ? flush_kthread_worker+0xb0/0xb0
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613266] ---[ end trace aee9a8b1c8add4f7 ]---
Nov 21 08:33:42 arcane-X555LB kernel: [388798.736506] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Nov 21 08:33:42 arcane-X555LB kernel: [388798.739059] ata1.00: configured for UDMA/133
Nov 21 08:33:42 arcane-X555LB kernel: [388798.752522] sd 0:0:0:0: [sda] Starting disk
Nov 21 08:33:42 arcane-X555LB kernel: [388798.776243] PM: resume of devices complete after 2783.409 msecs
Nov 21 08:33:42 arcane-X555LB kernel: [388798.776493] PM: Finishing wakeup.
Nov 21 08:33:42 arcane-X555LB kernel: [388798.776494] Restarting tasks ... done.
Nov 21 08:33:42 arcane-X555LB kernel: [388798.781493] video LNXVIDEO:00: Restoring backlight state
Nov 21 08:33:42 arcane-X555LB kernel: [388798.781498] video LNXVIDEO:01: Restoring backlight state
Nov 21 08:33:42 arcane-X555LB kernel: [388799.270396] r8169 0000:02:00.0 eth0: link down
Nov 21 08:33:42 arcane-X555LB kernel: [388799.270476] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov 21 08:33:42 arcane-X555LB kernel: [388799.271152] ===>rt2x00lib_start
Nov 21 08:33:42 arcane-X555LB kernel: [388799.271170] ==>MT76x0_WLAN_ChipOnOff(): OnOff:1 pAd->WlanFunCtrl.word = 0xffff0203, Reg-WlanFunCtrl=0xffff0103
Nov 21 08:33:42 arcane-X555LB kernel: [388799.271172] Reset(1) WlanFunCtrl.word = 0xffff010f
Nov 21 08:33:42 arcane-X555LB kernel: [388799.271223] Reset(2) WlanFunCtrl.word = 0xffff0103
Nov 21 08:33:42 arcane-X555LB kernel: [388799.271274] WlanFunCtrl.word = 0xffff0103
Nov 21 08:33:42 arcane-X555LB kernel: [388799.271326] MACVersion = 0x76502000
Nov 21 08:33:42 arcane-X555LB kernel: [388799.271333] <== MT76x0_WLAN_ChipOnOff():  pAd->WlanFunCtrl.word = 0xffff0103, Reg->WlanFunCtrl=0xffff0103!
Nov 21 08:33:42 arcane-X555LB kernel: [388799.271387] ASIC is ready
Nov 21 08:33:42 arcane-X555LB kernel: [388799.271399] FW Version:16.0.151 Build:370
Nov 21 08:33:42 arcane-X555LB kernel: [388799.271401] Build Time:201404211629____
Nov 21 08:33:42 arcane-X555LB kernel: [388799.271408] ILM Length = 334408(bytes)
Nov 21 08:33:42 arcane-X555LB kernel: [388799.271409] DLM Length = 47772(bytes)
Nov 21 08:33:42 arcane-X555LB kernel: [388799.343593] rt2800pci_write_firmware: COM_REG0(0x730) = 0x1
Nov 21 08:33:42 arcane-X555LB kernel: [388799.343600] rt2800_load_firmware: COM_REG0(0x730) = 0x1
Nov 21 08:33:42 arcane-X555LB kernel: [388799.350754] ===>rt2x00lib_enable_radio
Nov 21 08:33:42 arcane-X555LB kernel: [388799.350794] ===>rt2800_enable_radio: 
Nov 21 08:33:42 arcane-X555LB kernel: [388799.351116] reg FCE_PSE_CTRL =x0
Nov 21 08:33:42 arcane-X555LB kernel: [388799.351130] rt2800_init_bbp(): Init BBP Registers MT7630
Nov 21 08:33:42 arcane-X555LB kernel: [388799.352130] BBP version = f000f200
Nov 21 08:33:42 arcane-X555LB kernel: [388799.352132] rt2800_init_bbp(): Init BBP Registers MT7630
Nov 21 08:33:42 arcane-X555LB kernel: [388799.352171] rt2800_init_bbp(): Init BBP Registers MT7630 complete
Nov 21 08:33:42 arcane-X555LB kernel: [388799.352173] ==>rt2800lib_init_queues
Nov 21 08:33:42 arcane-X555LB kernel: [388799.352175] -->TX_RING: Base=0x0x000000000d160000, Cnt=64
Nov 21 08:33:42 arcane-X555LB kernel: [388799.352177] -->TX_RING: Base=0x0x00000000715ce000, Cnt=64
Nov 21 08:33:42 arcane-X555LB kernel: [388799.352179] -->TX_RING: Base=0x0x000000007ac03000, Cnt=64
Nov 21 08:33:42 arcane-X555LB kernel: [388799.352181] -->TX_RING: Base=0x0x000000008796a000, Cnt=64
Nov 21 08:33:42 arcane-X555LB kernel: [388799.352183] -->RX_RING: Base=0x0x0000000056326000, Cnt=128
Nov 21 08:33:42 arcane-X555LB kernel: [388799.352184] AsicInitTxRxRing
Nov 21 08:33:42 arcane-X555LB kernel: [388799.352186] -->TX_RING_CTRL: Base=0x35c9a000, Cnt=32!
Nov 21 08:33:42 arcane-X555LB kernel: [388799.352192] <===rt2800lib_init_queues
Nov 21 08:33:42 arcane-X555LB kernel: [388799.352193] MAC 40:b8:9a:76:8a:17 
Nov 21 08:33:42 arcane-X555LB kernel: [388799.352202] rt2800_enable_radio -7630 Dual antenna mode
Nov 21 08:33:42 arcane-X555LB kernel: [388799.364287] rt2800_init_rfcsr(): Init RF Registers MT7630
Nov 21 08:33:42 arcane-X555LB kernel: [388799.364686] rt2800_init_rfcsr: B0.R22 = 0x7d
Nov 21 08:33:42 arcane-X555LB kernel: [388799.364702] rt2800_init_rfcsr(): Init RF Registers MT7630 complete
Nov 21 08:33:42 arcane-X555LB kernel: [388799.384981] --> AsicCheckCommanFail2 Timeout Command = 2, CmdStatus= 0x0 
Nov 21 08:33:42 arcane-X555LB kernel: [388799.405229] --> AsicCheckCommanFail2 Timeout Command = 3, CmdStatus= 0x0 
Nov 21 08:33:42 arcane-X555LB kernel: [388799.405240] rtmp_bbp_set_rxpath(): rxpath=1, Set AGC1_R0=0x21400, agc_r0=0x21400
Nov 21 08:33:42 arcane-X555LB kernel: [388799.405244] rtmp_bbp_set_txdac(): txdac=0, Set txbe=0x0, txbe_r5=0x0
Nov 21 08:33:42 arcane-X555LB kernel: [388799.412277] set INT_MASK_CSR = 0xdff3ff3
Nov 21 08:33:42 arcane-X555LB kernel: [388799.412279] ==> RTMPEnableRxTx
Nov 21 08:33:42 arcane-X555LB kernel: [388799.412282] ==>  DMAIdle, GloCfg=0x50
Nov 21 08:33:42 arcane-X555LB kernel: [388799.412385] <== WRITE DMA offset 0x208 = 0x75
Nov 21 08:33:42 arcane-X555LB kernel: [388799.412386] <== RTMPEnableRxTx
Nov 21 08:33:42 arcane-X555LB kernel: [388799.412389] 0x1300 = 00064300
Nov 21 08:33:42 arcane-X555LB kernel: [388799.412391] rt2800pci_toggle_irq(1):Check if PDMA is idle!
Nov 21 08:33:42 arcane-X555LB kernel: [388799.412393] ==>  DMAIdle, GloCfg=0x75
Nov 21 08:33:42 arcane-X555LB kernel: [388799.412395] rt2800pci_toggle_irq(2):Check if PDMA is idle!
Nov 21 08:33:42 arcane-X555LB kernel: [388799.412397] ==>  DMAIdle, GloCfg=0x75
Nov 21 08:33:42 arcane-X555LB kernel: [388799.424354] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov 21 08:33:44 arcane-X555LB kernel: [388800.876759] wlan0: authenticate with 54:35:30:24:c5:ef
Nov 21 08:33:44 arcane-X555LB kernel: [388800.892171] wlan0: send auth to 54:35:30:24:c5:ef (try 1/3)
Nov 21 08:33:44 arcane-X555LB kernel: [388800.893656] wlan0: authenticated
Nov 21 08:33:44 arcane-X555LB kernel: [388800.895968] wlan0: associate with 54:35:30:24:c5:ef (try 1/3)
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899177] wlan0: RX AssocResp from 54:35:30:24:c5:ef (capab=0x411 status=0 aid=3)
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899194] ===>rt2800_sta_add:MT7630
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899210] ===>rt2800_sta_add:MT7630   wcid=33
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899213] Connect to AP MAC: 54:35:30:24:c5:ef WCID=33
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899221] BtAFHCtl: COEX AFH Start Ch = 0, AFH End Ch = 47, Channel = 1, CentralChannel = 1
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899223] SendAndesAFH: -->
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899226] SendAndesAFH: LinkStatus = 1, BW = 1, Channel = 1, BssHashID = 1, PktLength = 20
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899229] AsicSendCmdToAndes not need  Rsp!!!
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899232] CmdUnit->u.ANDES.CmdPayload: ffff88020a7476cc, len = 20
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899234] 0x0000 : 03 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899248] 0x0010 : 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899254] AsicSendCmdToAndes: ffff88022eae9f60, len = 24
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899256] 0x0000 : 14 00 10 51 03 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899269] 0x0010 : 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899277] Buf: ffff88022eae9f60, len = 24
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899279] 0x0000 : 14 00 10 51 03 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899292] 0x0010 : 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899301] pPacket->data: ffff880252296f80, len = 20
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899303] 0x0000 : 03 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899315] 0x0010 : 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899322] PCIKickOutCmd (TxCpuIdx = 1)
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899324] SendAndesAFH: <--
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899326] SendAndesWLANStatus: -->
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899330] SendAndesWLANStatus: CoexOperation = 4, WlanStatus = 15, PrivilegeTime = 0, BssHashID = 1, PktLength = 16
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899332] ==>INT_SOURCE_CSR_7630_HCCA_DMA_DONE
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899335] AsicSendCmdToAndes not need  Rsp!!!
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899338] CmdUnit->u.ANDES.CmdPayload: ffff88020a7476c0, len = 16
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899340] 0x0000 : 04 00 00 00 15 00 00 00 00 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899352] 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899355] AsicSendCmdToAndes: ffff88022eae9f60, len = 20
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899356] 0x0000 : 10 00 10 51 04 00 00 00 15 00 00 00 00 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899369] 0x0010 : 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899374] Buf: ffff88022eae9f60, len = 20
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899376] 0x0000 : 10 00 10 51 04 00 00 00 15 00 00 00 00 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899394] 0x0010 : 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899403] pPacket->data: ffff880252297140, len = 16
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899406] 0x0000 : 04 00 00 00 15 00 00 00 00 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899424] 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899428] PCIKickOutCmd (TxCpuIdx = 2)
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899437] ==>INT_SOURCE_CSR_7630_HCCA_DMA_DONE
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899666] ieee80211 phy0: rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840
Nov 21 08:33:44 arcane-X555LB kernel: [388800.904896] BtAFHCtl: COEX AFH Start Ch = 0, AFH End Ch = 47, Channel = 1, CentralChannel = 1
Nov 21 08:33:44 arcane-X555LB kernel: [388800.904902] SendAndesAFH: -->
Nov 21 08:33:44 arcane-X555LB kernel: [388800.904905] SendAndesAFH: LinkStatus = 1, BW = 1, Channel = 1, BssHashID = 1, PktLength = 20
Nov 21 08:33:44 arcane-X555LB kernel: [388800.904909] AsicSendCmdToAndes not need  Rsp!!!
Nov 21 08:33:44 arcane-X555LB kernel: [388800.904912] CmdUnit->u.ANDES.CmdPayload: ffff88020a7476cc, len = 20
Nov 21 08:33:44 arcane-X555LB kernel: [388800.904915] 0x0000 : 03 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.904929] 0x0010 : 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.904935] AsicSendCmdToAndes: ffff88022eae9f60, len = 24
Nov 21 08:33:44 arcane-X555LB kernel: [388800.904937] 0x0000 : 14 00 10 51 03 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.904950] 0x0010 : 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.904958] Buf: ffff88022eae9f60, len = 24
Nov 21 08:33:44 arcane-X555LB kernel: [388800.904960] 0x0000 : 14 00 10 51 03 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.904973] 0x0010 : 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.904982] pPacket->data: ffff880252297300, len = 20
Nov 21 08:33:44 arcane-X555LB kernel: [388800.904984] 0x0000 : 03 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.904996] 0x0010 : 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.905003] PCIKickOutCmd (TxCpuIdx = 3)
Nov 21 08:33:44 arcane-X555LB kernel: [388800.905006] SendAndesAFH: <--
Nov 21 08:33:44 arcane-X555LB kernel: [388800.905037] ==>INT_SOURCE_CSR_7630_HCCA_DMA_DONE
Nov 21 08:33:44 arcane-X555LB kernel: [388800.910045] wlan0: associated
Nov 21 08:33:44 arcane-X555LB kernel: [388800.910067] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Nov 21 08:33:44 arcane-X555LB kernel: [388800.957304] wlan0: deauthenticating from 54:35:30:24:c5:ef by local choice (reason=2)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.003935] ===>rt2800_sta_remove:MT7630
Nov 21 08:33:44 arcane-X555LB kernel: [388801.094121] BtAFHCtl: COEX AFH Start Ch = 0, AFH End Ch = 0, Channel = 1, CentralChannel = 1
Nov 21 08:33:44 arcane-X555LB kernel: [388801.094124] SendAndesAFH: -->
Nov 21 08:33:44 arcane-X555LB kernel: [388801.094125] SendAndesAFH: LinkStatus = 2, BW = 1, Channel = 1, BssHashID = 1, PktLength = 20
Nov 21 08:33:44 arcane-X555LB kernel: [388801.094127] AsicSendCmdToAndes not need  Rsp!!!
Nov 21 08:33:44 arcane-X555LB kernel: [388801.094128] CmdUnit->u.ANDES.CmdPayload: ffff88025218d6d4, len = 20
Nov 21 08:33:44 arcane-X555LB kernel: [388801.094129] 0x0000 : 03 00 00 00 02 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.094135] 0x0010 : 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.094137] AsicSendCmdToAndes: ffff880036a82f40, len = 24
Nov 21 08:33:44 arcane-X555LB kernel: [388801.094138] 0x0000 : 14 00 10 51 03 00 00 00 02 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.094142] 0x0010 : 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.094145] Buf: ffff880036a82f40, len = 24
Nov 21 08:33:44 arcane-X555LB kernel: [388801.094146] 0x0000 : 14 00 10 51 03 00 00 00 02 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.094151] 0x0010 : 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.094154] pPacket->data: ffff8801631d6700, len = 20
Nov 21 08:33:44 arcane-X555LB kernel: [388801.094155] 0x0000 : 03 00 00 00 02 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.094160] 0x0010 : 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.094162] PCIKickOutCmd (TxCpuIdx = 4)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.094163] SendAndesAFH: <--
Nov 21 08:33:44 arcane-X555LB kernel: [388801.094172] ==>INT_SOURCE_CSR_7630_HCCA_DMA_DONE
Nov 21 08:33:44 arcane-X555LB kernel: [388801.099126] ===>rt2800_sta_remove:MT7630   0x80100 = 0x0
Nov 21 08:33:44 arcane-X555LB kernel: [388801.099127] ===>rt2800_sta_remove:MT7630   0x80100 = 0x0
Nov 21 08:33:44 arcane-X555LB kernel: [388801.107918] cfg80211: Calling CRDA to update world regulatory domain
Nov 21 08:33:44 arcane-X555LB kernel: [388801.108071] wlan0: authenticate with 54:35:30:24:c5:ef
Nov 21 08:33:44 arcane-X555LB kernel: [388801.116026] wlan0: send auth to 54:35:30:24:c5:ef (try 1/3)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.116354] cfg80211: World regulatory domain updated:
Nov 21 08:33:44 arcane-X555LB kernel: [388801.116361] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.116366] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.116370] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.116374] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.116377] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.116380] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.116404] cfg80211: Calling CRDA for country: US
Nov 21 08:33:44 arcane-X555LB kernel: [388801.117603] wlan0: authenticated
Nov 21 08:33:44 arcane-X555LB kernel: [388801.120003] wlan0: associate with 54:35:30:24:c5:ef (try 1/3)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.122788] cfg80211: Regulatory domain changed to country: US
Nov 21 08:33:44 arcane-X555LB kernel: [388801.122796] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.122801] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.122805] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.122809] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.122812] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.122815] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.122819] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.122822] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123193] wlan0: RX AssocResp from 54:35:30:24:c5:ef (capab=0x411 status=0 aid=3)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123217] ===>rt2800_sta_add:MT7630
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123237] ===>rt2800_sta_add:MT7630   wcid=33
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123243] Connect to AP MAC: 54:35:30:24:c5:ef WCID=33
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123254] BtAFHCtl: COEX AFH Start Ch = 0, AFH End Ch = 47, Channel = 1, CentralChannel = 1
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123259] SendAndesAFH: -->
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123264] SendAndesAFH: LinkStatus = 1, BW = 1, Channel = 1, BssHashID = 1, PktLength = 20
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123269] AsicSendCmdToAndes not need  Rsp!!!
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123275] CmdUnit->u.ANDES.CmdPayload: ffff88020a7476cc, len = 20
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123279] 0x0000 : 03 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123306] 0x0010 : 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123314] AsicSendCmdToAndes: ffff880036a82500, len = 24
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123316] 0x0000 : 14 00 10 51 03 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123333] 0x0010 : 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123343] Buf: ffff880036a82500, len = 24
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123345] 0x0000 : 14 00 10 51 03 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123361] 0x0010 : 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123372] pPacket->data: ffff8801631d6a80, len = 20
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123375] 0x0000 : 03 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123390] 0x0010 : 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123398] PCIKickOutCmd (TxCpuIdx = 5)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123401] SendAndesAFH: <--
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123404] SendAndesWLANStatus: -->
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123410] SendAndesWLANStatus: CoexOperation = 4, WlanStatus = 15, PrivilegeTime = 0, BssHashID = 1, PktLength = 16
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123411] ==>INT_SOURCE_CSR_7630_HCCA_DMA_DONE
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123417] AsicSendCmdToAndes not need  Rsp!!!
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123421] CmdUnit->u.ANDES.CmdPayload: ffff88020a7476c0, len = 16
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123424] 0x0000 : 04 00 00 00 15 00 00 00 00 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123443] 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123446] AsicSendCmdToAndes: ffff880036a82500, len = 20
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123448] 0x0000 : 10 00 10 51 04 00 00 00 15 00 00 00 00 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123464] 0x0010 : 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123471] Buf: ffff880036a82500, len = 20
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123473] 0x0000 : 10 00 10 51 04 00 00 00 15 00 00 00 00 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123489] 0x0010 : 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123496] pPacket->data: ffff8801631d6c40, len = 16
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123498] 0x0000 : 04 00 00 00 15 00 00 00 00 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123514] 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123517] PCIKickOutCmd (TxCpuIdx = 6)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123527] ==>INT_SOURCE_CSR_7630_HCCA_DMA_DONE
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123708] ieee80211 phy0: rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840
Nov 21 08:33:44 arcane-X555LB kernel: [388801.128990] BtAFHCtl: COEX AFH Start Ch = 0, AFH End Ch = 47, Channel = 1, CentralChannel = 1
Nov 21 08:33:44 arcane-X555LB kernel: [388801.128993] SendAndesAFH: -->
Nov 21 08:33:44 arcane-X555LB kernel: [388801.128995] SendAndesAFH: LinkStatus = 1, BW = 1, Channel = 1, BssHashID = 1, PktLength = 20
Nov 21 08:33:44 arcane-X555LB kernel: [388801.128996] AsicSendCmdToAndes not need  Rsp!!!
Nov 21 08:33:44 arcane-X555LB kernel: [388801.128998] CmdUnit->u.ANDES.CmdPayload: ffff88020a7476cc, len = 20
Nov 21 08:33:44 arcane-X555LB kernel: [388801.128999] 0x0000 : 03 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.129006] 0x0010 : 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.129009] AsicSendCmdToAndes: ffff880036a82500, len = 24
Nov 21 08:33:44 arcane-X555LB kernel: [388801.129010] 0x0000 : 14 00 10 51 03 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.129016] 0x0010 : 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.129020] Buf: ffff880036a82500, len = 24
Nov 21 08:33:44 arcane-X555LB kernel: [388801.129021] 0x0000 : 14 00 10 51 03 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.129027] 0x0010 : 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.129032] pPacket->data: ffff8801631d6e00, len = 20
Nov 21 08:33:44 arcane-X555LB kernel: [388801.129033] 0x0000 : 03 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.129039] 0x0010 : 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.129042] PCIKickOutCmd (TxCpuIdx = 7)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.129044] SendAndesAFH: <--
Nov 21 08:33:44 arcane-X555LB kernel: [388801.129054] ==>INT_SOURCE_CSR_7630_HCCA_DMA_DONE
Nov 21 08:33:44 arcane-X555LB kernel: [388801.134069] wlan0: associated
Nov 21 08:33:57 arcane-X555LB kernel: [388814.346843] [UFW BLOCK] IN=wlan0 OUT= MAC=40:b8:9a:76:8a:17:6c:71:d9:70:19:23:08:00 SRC=192.168.0.2 DST=192.168.0.17 LEN=56 TOS=0x00 PREC=0x00 TTL=128 ID=13280 PROTO=UDP SPT=53949 DPT=2054 LEN=36 
Nov 21 08:33:57 arcane-X555LB kernel: [388815.163511] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:48:5a:b6:f8:10:cd:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
Nov 21 08:33:57 arcane-X555LB kernel: [388815.164523] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:48:5a:b6:f8:10:cd:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
Nov 21 08:33:57 arcane-X555LB kernel: [388815.165396] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:48:5a:b6:f8:10:cd:08:00 SRC=192.168.26.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
Nov 21 08:33:57 arcane-X555LB kernel: [388815.166471] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:48:5a:b6:f8:10:cd:08:00 SRC=192.168.26.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
Nov 21 08:33:57 arcane-X555LB kernel: [388815.167374] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:48:5a:b6:f8:10:cd:08:00 SRC=192.168.27.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
Nov 21 08:33:57 arcane-X555LB kernel: [388815.171923] [UFW BLOCK] IN=wlan0 OUT= MAC=33:33:00:00:00:01:48:5a:b6:f8:10:cd:86:dd SRC=fe80:0000:0000:0000:4a5a:b6ff:fef8:10cd DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=76 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
Nov 21 08:35:14 arcane-X555LB kernel: [388892.249469] [UFW BLOCK] IN=wlan0 OUT= MAC=40:b8:9a:76:8a:17:6c:71:d9:70:19:23:08:00 SRC=192.168.0.2 DST=192.168.0.17 LEN=56 TOS=0x00 PREC=0x00 TTL=128 ID=13310 PROTO=UDP SPT=61464 DPT=2054 LEN=36 
Nov 21 08:36:03 arcane-X555LB kernel: [388941.118241] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:48:5a:b6:f8:10:cd:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
Nov 21 08:36:03 arcane-X555LB kernel: [388941.119275] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:48:5a:b6:f8:10:cd:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
Nov 21 08:36:03 arcane-X555LB kernel: [388941.120221] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:48:5a:b6:f8:10:cd:08:00 SRC=192.168.26.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
Nov 21 08:36:03 arcane-X555LB kernel: [388941.121353] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:48:5a:b6:f8:10:cd:08:00 SRC=192.168.26.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
Nov 21 08:36:03 arcane-X555LB kernel: [388941.122370] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:48:5a:b6:f8:10:cd:08:00 SRC=192.168.27.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
Nov 21 08:36:03 arcane-X555LB kernel: [388941.126592] [UFW BLOCK] IN=wlan0 OUT= MAC=33:33:00:00:00:01:48:5a:b6:f8:10:cd:86:dd SRC=fe80:0000:0000:0000:4a5a:b6ff:fef8:10cd DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=76 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
Nov 21 08:37:15 arcane-X555LB kernel: [389012.234485] [UFW BLOCK] IN=wlan0 OUT= MAC=40:b8:9a:76:8a:17:6c:71:d9:70:19:23:08:00 SRC=192.168.0.2 DST=192.168.0.17 LEN=56 TOS=0x00 PREC=0x00 TTL=128 ID=13346 PROTO=UDP SPT=59166 DPT=2054 LEN=36 
Nov 21 08:38:09 arcane-X555LB kernel: [389067.103309] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:48:5a:b6:f8:10:cd:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
Nov 21 08:38:09 arcane-X555LB kernel: [389067.104283] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:48:5a:b6:f8:10:cd:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
Nov 21 08:38:09 arcane-X555LB kernel: [389067.105205] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:48:5a:b6:f8:10:cd:08:00 SRC=192.168.26.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
Nov 21 08:38:09 arcane-X555LB kernel: [389067.106247] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:48:5a:b6:f8:10:cd:08:00 SRC=192.168.26.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
Nov 21 08:38:09 arcane-X555LB kernel: [389067.107078] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:48:5a:b6:f8:10:cd:08:00 SRC=192.168.27.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
Nov 21 08:38:09 arcane-X555LB kernel: [389067.111337] [UFW BLOCK] IN=wlan0 OUT= MAC=33:33:00:00:00:01:48:5a:b6:f8:10:cd:86:dd SRC=fe80:0000:0000:0000:4a5a:b6ff:fef8:10cd DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=76 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
Nov 21 08:38:42 arcane-X555LB kernel: [389099.704277] type=1400 audit(1448113122.493:86): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=24159 comm="apparmor_parser"
Nov 21 08:38:42 arcane-X555LB kernel: [389099.704285] type=1400 audit(1448113122.493:87): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=24159 comm="apparmor_parser"
Nov 21 08:38:42 arcane-X555LB kernel: [389099.704749] type=1400 audit(1448113122.493:88): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=24159 comm="apparmor_parser"
Nov 21 08:38:59 arcane-X555LB kernel: [389116.925150] ===>rt2800_sta_remove:MT7630
Nov 21 08:38:59 arcane-X555LB kernel: [389117.018204] BtAFHCtl: COEX AFH Start Ch = 0, AFH End Ch = 0, Channel = 1, CentralChannel = 1
Nov 21 08:38:59 arcane-X555LB kernel: [389117.018207] SendAndesAFH: -->
Nov 21 08:38:59 arcane-X555LB kernel: [389117.018208] SendAndesAFH: LinkStatus = 2, BW = 1, Channel = 1, BssHashID = 1, PktLength = 20
Nov 21 08:38:59 arcane-X555LB kernel: [389117.018210] AsicSendCmdToAndes not need  Rsp!!!
Nov 21 08:38:59 arcane-X555LB kernel: [389117.018211] CmdUnit->u.ANDES.CmdPayload: ffff88022b3b9b04, len = 20
Nov 21 08:38:59 arcane-X555LB kernel: [389117.018212] 0x0000 : 03 00 00 00 02 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:38:59 arcane-X555LB kernel: [389117.018217] 0x0010 : 01 00 00 00 
Nov 21 08:38:59 arcane-X555LB kernel: [389117.018220] AsicSendCmdToAndes: ffff88005612eee0, len = 24
Nov 21 08:38:59 arcane-X555LB kernel: [389117.018220] 0x0000 : 14 00 10 51 03 00 00 00 02 00 00 00 01 00 00 00 
Nov 21 08:38:59 arcane-X555LB kernel: [389117.018225] 0x0010 : 01 00 00 00 01 00 00 00 
Nov 21 08:38:59 arcane-X555LB kernel: [389117.018228] Buf: ffff88005612eee0, len = 24
Nov 21 08:38:59 arcane-X555LB kernel: [389117.018229] 0x0000 : 14 00 10 51 03 00 00 00 02 00 00 00 01 00 00 00 
Nov 21 08:38:59 arcane-X555LB kernel: [389117.018234] 0x0010 : 01 00 00 00 01 00 00 00 
Nov 21 08:38:59 arcane-X555LB kernel: [389117.018237] pPacket->data: ffff880252291a40, len = 20
Nov 21 08:38:59 arcane-X555LB kernel: [389117.018238] 0x0000 : 03 00 00 00 02 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:38:59 arcane-X555LB kernel: [389117.018242] 0x0010 : 01 00 00 00 
Nov 21 08:38:59 arcane-X555LB kernel: [389117.018245] PCIKickOutCmd (TxCpuIdx = 8)
Nov 21 08:38:59 arcane-X555LB kernel: [389117.018246] SendAndesAFH: <--
Nov 21 08:38:59 arcane-X555LB kernel: [389117.018273] ==>INT_SOURCE_CSR_7630_HCCA_DMA_DONE
Nov 21 08:38:59 arcane-X555LB kernel: [389117.023210] ===>rt2800_sta_remove:MT7630   0x80100 = 0x0
Nov 21 08:38:59 arcane-X555LB kernel: [389117.023212] ===>rt2800_sta_remove:MT7630   0x80100 = 0x0
Nov 21 08:38:59 arcane-X555LB kernel: [389117.045273] cfg80211: Calling CRDA to update world regulatory domain
Nov 21 08:38:59 arcane-X555LB kernel: [389117.051072] cfg80211: World regulatory domain updated:
Nov 21 08:38:59 arcane-X555LB kernel: [389117.051080] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov 21 08:38:59 arcane-X555LB kernel: [389117.051086] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:38:59 arcane-X555LB kernel: [389117.051091] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:38:59 arcane-X555LB kernel: [389117.051095] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:38:59 arcane-X555LB kernel: [389117.051099] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:38:59 arcane-X555LB kernel: [389117.051103] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:38:59 arcane-X555LB kernel: [389117.051516] cfg80211: Calling CRDA for country: US
Nov 21 08:38:59 arcane-X555LB kernel: [389117.057210] cfg80211: Regulatory domain changed to country: US
Nov 21 08:38:59 arcane-X555LB kernel: [389117.057214] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov 21 08:38:59 arcane-X555LB kernel: [389117.057215] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Nov 21 08:38:59 arcane-X555LB kernel: [389117.057217] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
Nov 21 08:38:59 arcane-X555LB kernel: [389117.057219] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:38:59 arcane-X555LB kernel: [389117.057220] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:38:59 arcane-X555LB kernel: [389117.057222] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:38:59 arcane-X555LB kernel: [389117.057223] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
Nov 21 08:38:59 arcane-X555LB kernel: [389117.057225] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
Nov 21 08:39:00 arcane-X555LB kernel: [389117.833571] wlan0: authenticate with 54:35:30:24:c5:ef
Nov 21 08:39:00 arcane-X555LB kernel: [389117.848910] wlan0: send auth to 54:35:30:24:c5:ef (try 1/3)
Nov 21 08:39:00 arcane-X555LB kernel: [389117.868413] wlan0: send auth to 54:35:30:24:c5:ef (try 2/3)
Nov 21 08:39:00 arcane-X555LB kernel: [389117.903253] wlan0: authenticated
Nov 21 08:39:00 arcane-X555LB kernel: [389117.904787] wlan0: associate with 54:35:30:24:c5:ef (try 1/3)
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908015] wlan0: RX AssocResp from 54:35:30:24:c5:ef (capab=0x411 status=0 aid=3)
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908036] ===>rt2800_sta_add:MT7630
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908053] ===>rt2800_sta_add:MT7630   wcid=33
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908057] Connect to AP MAC: 54:35:30:24:c5:ef WCID=33
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908066] BtAFHCtl: COEX AFH Start Ch = 0, AFH End Ch = 47, Channel = 1, CentralChannel = 1
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908069] SendAndesAFH: -->
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908073] SendAndesAFH: LinkStatus = 1, BW = 1, Channel = 1, BssHashID = 1, PktLength = 20
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908076] AsicSendCmdToAndes not need  Rsp!!!
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908080] CmdUnit->u.ANDES.CmdPayload: ffff88022b3b96cc, len = 20
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908083] 0x0000 : 03 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908101] 0x0010 : 01 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908108] AsicSendCmdToAndes: ffff88005612e160, len = 24
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908111] 0x0000 : 14 00 10 51 03 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908127] 0x0010 : 01 00 00 00 01 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908138] Buf: ffff88005612e160, len = 24
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908140] 0x0000 : 14 00 10 51 03 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908156] 0x0010 : 01 00 00 00 01 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908168] pPacket->data: ffff880252292b40, len = 20
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908170] 0x0000 : 03 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908185] 0x0010 : 01 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908193] PCIKickOutCmd (TxCpuIdx = 9)
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908196] SendAndesAFH: <--
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908199] SendAndesWLANStatus: -->
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908203] SendAndesWLANStatus: CoexOperation = 4, WlanStatus = 15, PrivilegeTime = 0, BssHashID = 1, PktLength = 16
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908205] AsicSendCmdToAndes not need  Rsp!!!
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908208] CmdUnit->u.ANDES.CmdPayload: ffff88022b3b96c0, len = 16
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908210] 0x0000 : 04 00 00 00 15 00 00 00 00 00 00 00 01 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908226] 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908230] ==>INT_SOURCE_CSR_7630_HCCA_DMA_DONE
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908237] AsicSendCmdToAndes: ffff88005612e160, len = 20
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908240] 0x0000 : 10 00 10 51 04 00 00 00 15 00 00 00 00 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908258] 0x0010 : 01 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908265] Buf: ffff88005612e160, len = 20
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908267] 0x0000 : 10 00 10 51 04 00 00 00 15 00 00 00 00 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908336] 0x0010 : 01 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908359] pPacket->data: ffff880252292d00, len = 16
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908361] 0x0000 : 04 00 00 00 15 00 00 00 00 00 00 00 01 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908377] 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908380] PCIKickOutCmd (TxCpuIdx = 10)
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908390] ==>INT_SOURCE_CSR_7630_HCCA_DMA_DONE
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908590] ieee80211 phy0: rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840
Nov 21 08:39:00 arcane-X555LB kernel: [389117.913847] BtAFHCtl: COEX AFH Start Ch = 0, AFH End Ch = 47, Channel = 1, CentralChannel = 1
Nov 21 08:39:00 arcane-X555LB kernel: [389117.913854] SendAndesAFH: -->
Nov 21 08:39:00 arcane-X555LB kernel: [389117.913859] SendAndesAFH: LinkStatus = 1, BW = 1, Channel = 1, BssHashID = 1, PktLength = 20
Nov 21 08:39:00 arcane-X555LB kernel: [389117.913864] AsicSendCmdToAndes not need  Rsp!!!
Nov 21 08:39:00 arcane-X555LB kernel: [389117.913869] CmdUnit->u.ANDES.CmdPayload: ffff88022b3b96cc, len = 20
Nov 21 08:39:00 arcane-X555LB kernel: [389117.913872] 0x0000 : 03 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.913888] 0x0010 : 01 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.913895] AsicSendCmdToAndes: ffff88005612ee80, len = 24
Nov 21 08:39:00 arcane-X555LB kernel: [389117.913896] 0x0000 : 14 00 10 51 03 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.913911] 0x0010 : 01 00 00 00 01 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.913919] Buf: ffff88005612ee80, len = 24
Nov 21 08:39:00 arcane-X555LB kernel: [389117.913921] 0x0000 : 14 00 10 51 03 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.913936] 0x0010 : 01 00 00 00 01 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.913945] pPacket->data: ffff880252292ec0, len = 20
Nov 21 08:39:00 arcane-X555LB kernel: [389117.913947] 0x0000 : 03 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.913961] 0x0010 : 01 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.913968] PCIKickOutCmd (TxCpuIdx = 11)
Nov 21 08:39:00 arcane-X555LB kernel: [389117.913970] SendAndesAFH: <--
Nov 21 08:39:00 arcane-X555LB kernel: [389117.914003] ==>INT_SOURCE_CSR_7630_HCCA_DMA_DONE
Nov 21 08:39:00 arcane-X555LB kernel: [389117.919001] wlan0: associated
Nov 21 08:39:15 arcane-X555LB kernel: [389132.313424] [UFW BLOCK] IN=wlan0 OUT= MAC=40:b8:9a:76:8a:17:6c:71:d9:70:19:23:08:00 SRC=192.168.0.2 DST=192.168.0.17 LEN=56 TOS=0x00 PREC=0x00 TTL=128 ID=13377 PROTO=UDP SPT=58664 DPT=2054 LEN=36 
Nov 21 08:39:29 arcane-X555LB kernel: [389146.343019] [UFW BLOCK] IN=wlan0 OUT= MAC=40:b8:9a:76:8a:17:48:5a:b6:f8:10:cd:08:00 SRC=69.172.216.111 DST=192.168.0.17 LEN=83 TOS=0x00 PREC=0x00 TTL=50 ID=50629 DF PROTO=TCP SPT=443 DPT=57590 WINDOW=33 RES=0x00 ACK PSH URGP=0 
Nov 21 08:39:29 arcane-X555LB kernel: [389146.344252] [UFW BLOCK] IN=wlan0 OUT= MAC=40:b8:9a:76:8a:17:48:5a:b6:f8:10:cd:08:00 SRC=69.172.216.111 DST=192.168.0.17 LEN=83 TOS=0x00 PREC=0x00 TTL=51 ID=62466 DF PROTO=TCP SPT=443 DPT=57589 WINDOW=33 RES=0x00 ACK PSH URGP=0 
Nov 21 08:39:29 arcane-X555LB kernel: [389146.645913] [UFW BLOCK] IN=wlan0 OUT= MAC=40:b8:9a:76:8a:17:48:5a:b6:f8:10:cd:08:00 SRC=69.172.216.111 DST=192.168.0.17 LEN=83 TOS=0x00 PREC=0x00 TTL=50 ID=50631 DF PROTO=TCP SPT=443 DPT=57590 WINDOW=33 RES=0x00 ACK PSH URGP=0 
Nov 21 08:39:44 arcane-X555LB kernel: [389161.489754] [UFW BLOCK] IN=wlan0 OUT= MAC=40:b8:9a:76:8a:17:48:5a:b6:f8:10:cd:08:00 SRC=69.172.216.111 DST=192.168.0.17 LEN=83 TOS=0x00 PREC=0x00 TTL=51 ID=62473 DF PROTO=TCP SPT=443 DPT=57589 WINDOW=33 RES=0x00 ACK PSH URGP=0 
Nov 21 08:40:15 arcane-X555LB kernel: [389192.209108] [UFW BLOCK] IN=wlan0 OUT= MAC=40:b8:9a:76:8a:17:6c:71:d9:70:19:23:08:00 SRC=192.168.0.2 DST=192.168.0.17 LEN=56 TOS=0x00 PREC=0x00 TTL=128 ID=13391 PROTO=UDP SPT=63715 DPT=2054 LEN=36 
Nov 21 08:40:15 arcane-X555LB kernel: [389193.029666] [UFW BLOCK] IN=wlan0 OUT= MAC=33:33:00:00:00:01:48:5a:b6:f8:10:cd:86:dd SRC=fe80:0000:0000:0000:4a5a:b6ff:fef8:10cd DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=76 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
Nov 21 08:41:15 arcane-X555LB kernel: [389252.296364] [UFW BLOCK] IN=wlan0 OUT= MAC=40:b8:9a:76:8a:17:6c:71:d9:70:19:23:08:00 SRC=192.168.0.2 DST=192.168.0.17 LEN=56 TOS=0x00 PREC=0x00 TTL=128 ID=13405 PROTO=UDP SPT=62393 DPT=2054 LEN=36 
Nov 21 08:42:15 arcane-X555LB kernel: [389312.187907] [UFW BLOCK] IN=wlan0 OUT= MAC=40:b8:9a:76:8a:17:6c:71:d9:70:19:23:08:00 SRC=192.168.0.2 DST=192.168.0.17 LEN=56 TOS=0x00 PREC=0x00 TTL=128 ID=13419 PROTO=UDP SPT=57510 DPT=2054 LEN=36 
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Initializing cgroup subsys cpu
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Initializing cgroup subsys cpuacct
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Linux version 3.13.11-03131107-generic (apw@gomeisa) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #201409181736 SMP Thu Sep 18 21:37:41 UTC 2014
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.11-03131107-generic root=UUID=b320ac20-ec61-42ec-8900-f1b181a2d24e ro noprompt persistent quiet splash acpi_osi= vt.handoff=7
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] KERNEL supported cpus:
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   Intel GenuineIntel
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   AMD AuthenticAMD
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   Centaur CentaurHauls
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x0000000000057fff] usable
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x0000000000058000-0x0000000000058fff] reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x0000000000059000-0x000000000009dfff] usable
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x000000000009e000-0x000000000009ffff] reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x0000000097070fff] usable
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x0000000097071000-0x00000000973c5fff] reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x00000000973c6000-0x000000009aa36fff] usable
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x000000009aa37000-0x000000009aa96fff] reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x000000009aa97000-0x000000009b296fff] usable
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x000000009b297000-0x000000009c41dfff] ACPI NVS
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x000000009c41e000-0x000000009cee6fff] reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x000000009cee7000-0x000000009cffefff] type 20
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x000000009cfff000-0x000000009cffffff] usable
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x000000009d800000-0x000000009fffffff] reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000025effffff] usable
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] NX (Execute Disable) protection: active
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: EFI v2.40 by American Megatrends
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi:  ACPI=0x9b69b000  ACPI 2.0=0x9b69b000  SMBIOS=0x9ce30918 
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem00: type=7, attr=0xf, range=[0x0000000000000000-0x0000000000058000) (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem01: type=0, attr=0xf, range=[0x0000000000058000-0x0000000000059000) (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem02: type=7, attr=0xf, range=[0x0000000000059000-0x000000000009e000) (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem03: type=0, attr=0xf, range=[0x000000000009e000-0x00000000000a0000) (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem04: type=2, attr=0xf, range=[0x0000000000100000-0x0000000001502000) (20MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem05: type=7, attr=0xf, range=[0x0000000001502000-0x0000000002000000) (10MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem06: type=2, attr=0xf, range=[0x0000000002000000-0x0000000003402000) (20MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem07: type=7, attr=0xf, range=[0x0000000003402000-0x0000000010000000) (203MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem08: type=3, attr=0xf, range=[0x0000000010000000-0x000000001000b000) (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem09: type=7, attr=0xf, range=[0x000000001000b000-0x0000000035ccc000) (604MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem10: type=2, attr=0xf, range=[0x0000000035ccc000-0x0000000036e5e000) (17MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem11: type=7, attr=0xf, range=[0x0000000036e5e000-0x000000006999e000) (811MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem12: type=2, attr=0xf, range=[0x000000006999e000-0x000000008f3dc000) (602MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem13: type=4, attr=0xf, range=[0x000000008f3dc000-0x000000008f41c000) (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem14: type=7, attr=0xf, range=[0x000000008f41c000-0x0000000095ee2000) (106MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem15: type=2, attr=0xf, range=[0x0000000095ee2000-0x0000000095fce000) (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem16: type=7, attr=0xf, range=[0x0000000095fce000-0x0000000095fd0000) (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem17: type=2, attr=0xf, range=[0x0000000095fd0000-0x0000000095fd1000) (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem18: type=7, attr=0xf, range=[0x0000000095fd1000-0x0000000095fd2000) (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem19: type=2, attr=0xf, range=[0x0000000095fd2000-0x0000000095fd4000) (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem20: type=7, attr=0xf, range=[0x0000000095fd4000-0x0000000095fd5000) (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem21: type=2, attr=0xf, range=[0x0000000095fd5000-0x0000000095fd6000) (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem22: type=7, attr=0xf, range=[0x0000000095fd6000-0x0000000095fda000) (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem23: type=2, attr=0xf, range=[0x0000000095fda000-0x00000000960c4000) (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem24: type=1, attr=0xf, range=[0x00000000960c4000-0x00000000961ea000) (1MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem25: type=4, attr=0xf, range=[0x00000000961ea000-0x0000000097071000) (14MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem26: type=6, attr=0x800000000000000f, range=[0x0000000097071000-0x00000000973c6000) (3MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem27: type=4, attr=0xf, range=[0x00000000973c6000-0x00000000973cc000) (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem28: type=7, attr=0xf, range=[0x00000000973cc000-0x00000000973ce000) (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem29: type=2, attr=0xf, range=[0x00000000973ce000-0x00000000973d0000) (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem30: type=7, attr=0xf, range=[0x00000000973d0000-0x00000000973d1000) (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem31: type=2, attr=0xf, range=[0x00000000973d1000-0x00000000973d3000) (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem32: type=7, attr=0xf, range=[0x00000000973d3000-0x00000000973d6000) (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem33: type=2, attr=0xf, range=[0x00000000973d6000-0x00000000973d8000) (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem34: type=7, attr=0xf, range=[0x00000000973d8000-0x00000000973d9000) (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem35: type=2, attr=0xf, range=[0x00000000973d9000-0x00000000973db000) (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem36: type=4, attr=0xf, range=[0x00000000973db000-0x000000009a437000) (48MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem37: type=7, attr=0xf, range=[0x000000009a437000-0x000000009a78f000) (3MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem38: type=3, attr=0xf, range=[0x000000009a78f000-0x000000009aa37000) (2MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem39: type=0, attr=0xf, range=[0x000000009aa37000-0x000000009aa97000) (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem40: type=7, attr=0xf, range=[0x000000009aa97000-0x000000009b28d000) (7MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem41: type=2, attr=0xf, range=[0x000000009b28d000-0x000000009b297000) (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem42: type=10, attr=0xf, range=[0x000000009b297000-0x000000009c41e000) (17MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem43: type=6, attr=0x800000000000000f, range=[0x000000009c41e000-0x000000009cee7000) (10MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem44: type=5, attr=0x800000000000000f, range=[0x000000009cee7000-0x000000009cfff000) (1MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem45: type=4, attr=0xf, range=[0x000000009cfff000-0x000000009d000000) (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem46: type=7, attr=0xf, range=[0x0000000100000000-0x000000025f000000) (5616MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem47: type=0, attr=0x0, range=[0x000000009d800000-0x00000000a0000000) (40MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem48: type=11, attr=0x8000000000000001, range=[0x00000000f8000000-0x00000000fc000000) (64MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem49: type=11, attr=0x8000000000000001, range=[0x00000000fec00000-0x00000000fec01000) (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem50: type=11, attr=0x8000000000000001, range=[0x00000000fed00000-0x00000000fed04000) (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem51: type=11, attr=0x8000000000000001, range=[0x00000000fed1c000-0x00000000fed20000) (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem52: type=11, attr=0x8000000000000001, range=[0x00000000fee00000-0x00000000fee01000) (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem53: type=11, attr=0x8000000000000001, range=[0x00000000ff000000-0x0000000100000000) (16MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] SMBIOS 2.8 present.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] DMI: ASUSTeK COMPUTER INC. X555LB/X555LB, BIOS X555LB.408 07/07/2015
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] No AGP bridge found
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] e820: last_pfn = 0x25f000 max_arch_pfn = 0x400000000
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] MTRR default type: uncachable
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] MTRR fixed ranges enabled:
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   00000-9FFFF write-back
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   A0000-EFFFF uncachable
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   F0000-FFFFF write-protect
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] MTRR variable ranges enabled:
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   0 base 0000000000 mask 7F80000000 write-back
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   1 base 0080000000 mask 7FF0000000 write-back
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   2 base 0090000000 mask 7FF8000000 write-back
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   3 base 0098000000 mask 7FFC000000 write-back
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   4 base 009C000000 mask 7FFF000000 write-back
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   5 base 0100000000 mask 7F00000000 write-back
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   6 base 0200000000 mask 7F80000000 write-back
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   7 base 0260000000 mask 7FE0000000 uncachable
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   8 base 025F000000 mask 7FFF000000 uncachable
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   9 disabled
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] original variable MTRRs
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] reg 1, base: 2GB, range: 256MB, type WB
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] reg 2, base: 2304MB, range: 128MB, type WB
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] reg 3, base: 2432MB, range: 64MB, type WB
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] reg 4, base: 2496MB, range: 16MB, type WB
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] reg 5, base: 4GB, range: 4GB, type WB
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] reg 6, base: 8GB, range: 2GB, type WB
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] reg 7, base: 9728MB, range: 512MB, type UC
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] reg 8, base: 9712MB, range: 16MB, type UC
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] total RAM covered: 8128M
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Found optimal setting for mtrr clean up
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]  gran_size: 64K     chunk_size: 64M     num_reg: 8      lose cover RAM: 0G
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] New variable MTRRs
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] reg 1, base: 2GB, range: 512MB, type WB
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] reg 2, base: 2512MB, range: 16MB, type UC
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] reg 3, base: 2528MB, range: 32MB, type UC
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] reg 4, base: 4GB, range: 4GB, type WB
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] reg 5, base: 8GB, range: 1GB, type WB
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] reg 6, base: 9GB, range: 512MB, type WB
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] reg 7, base: 9712MB, range: 16MB, type UC
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] e820: update [mem 0x9d000000-0xffffffff] usable ==> reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] e820: last_pfn = 0x9d000 max_arch_pfn = 0x400000000
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Scanning 1 areas for low memory corruption
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Using GB pages for direct mapping
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]  [mem 0x00000000-0x000fffff] page 4k
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BRK [0x02fe0000, 0x02fe0fff] PGTABLE
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BRK [0x02fe1000, 0x02fe1fff] PGTABLE
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BRK [0x02fe2000, 0x02fe2fff] PGTABLE
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] init_memory_mapping: [mem 0x25ee00000-0x25effffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]  [mem 0x25ee00000-0x25effffff] page 2M
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BRK [0x02fe3000, 0x02fe3fff] PGTABLE
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] init_memory_mapping: [mem 0x25c000000-0x25edfffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]  [mem 0x25c000000-0x25edfffff] page 2M
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] init_memory_mapping: [mem 0x200000000-0x25bffffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]  [mem 0x200000000-0x23fffffff] page 1G
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]  [mem 0x240000000-0x25bffffff] page 2M
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] init_memory_mapping: [mem 0x00100000-0x97070fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]  [mem 0x00100000-0x001fffff] page 4k
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]  [mem 0x40000000-0x7fffffff] page 1G
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]  [mem 0x80000000-0x96ffffff] page 2M
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]  [mem 0x97000000-0x97070fff] page 4k
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] init_memory_mapping: [mem 0x973c6000-0x9aa36fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]  [mem 0x973c6000-0x973fffff] page 4k
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]  [mem 0x97400000-0x9a9fffff] page 2M
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]  [mem 0x9aa00000-0x9aa36fff] page 4k
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BRK [0x02fe4000, 0x02fe4fff] PGTABLE
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BRK [0x02fe5000, 0x02fe5fff] PGTABLE
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] init_memory_mapping: [mem 0x9aa97000-0x9b296fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]  [mem 0x9aa97000-0x9abfffff] page 4k
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]  [mem 0x9ac00000-0x9b1fffff] page 2M
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]  [mem 0x9b200000-0x9b296fff] page 4k
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] init_memory_mapping: [mem 0x9cfff000-0x9cffffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]  [mem 0x9cfff000-0x9cffffff] page 4k
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] init_memory_mapping: [mem 0x100000000-0x1ffffffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]  [mem 0x100000000-0x1ffffffff] page 1G
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] RAMDISK: [mem 0x35ccc000-0x36e5dfff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: RSDP 000000009b69b000 000024 (v02 _ASUS_)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: XSDT 000000009b69b0b0 0000DC (v01 _ASUS_ Notebook 01072009 AMI  00010013)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: FACP 000000009b6b4b58 00010C (v05 _ASUS_ Notebook 01072009 AMI  00010013)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI Error: Gpe0Block - 32-bit FADT register is too long (32 bytes, 256 bits) to convert to GAS struct - 255 bits max, truncating (20131115/tbfadt-202)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: DSDT 000000009b69b218 01993D (v02 _ASUS_ Notebook 01072009 INTL 20120913)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: FACS 000000009c41bf80 000040
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: APIC 000000009b6b4c68 000084 (v03 _ASUS_ Notebook 01072009 AMI  00010013)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: FPDT 000000009b6b4cf0 000044 (v01 _ASUS_ Notebook 01072009 AMI  00010013)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: FIDT 000000009b6b4d38 00009C (v01 _ASUS_ Notebook 01072009 AMI  00010013)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: ECDT 000000009b6b4dd8 0000C1 (v01 _ASUS_ Notebook 01072009 AMI. 00000005)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: MCFG 000000009b6b4ea0 00003C (v01 _ASUS_ Notebook 01072009 MSFT 00000097)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: HPET 000000009b6b4ee0 000038 (v01 _ASUS_ Notebook 01072009 AMI. 00000005)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: SSDT 000000009b6b4f18 000315 (v01 SataRe SataTabl 00001000 INTL 20120913)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: UEFI 000000009b6b5230 000042 (v01                 00000000      00000000)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: SSDT 000000009b6b5278 000194 (v01  Intel    zpodd 00001000 INTL 20120913)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: ASF! 000000009b6b5410 0000A0 (v32 INTEL       HCG 00000001 TFSM 000F4240)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: SSDT 000000009b6b54b0 000539 (v02  PmRef  Cpu0Ist 00003000 INTL 20120913)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: SSDT 000000009b6b59f0 000B74 (v02 CpuRef  CpuSsdt 00003000 INTL 20120913)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: SSDT 000000009b6b6568 003245 (v02 DptfTa DptfTabl 00001000 INTL 20120913)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: SSDT 000000009b6b97b0 000394 (v02 CppcTa CppcTabl 00001000 INTL 20120913)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: PCCT 000000009b6b9b48 00006E (v05 PcctTa PcctTabl 00001000 INTL 20120913)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: SSDT 000000009b6b9bb8 000AC4 (v02 Cpc_Ta Cpc_Tabl 00001000 INTL 20120913)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: SSDT 000000009b6ba680 006B80 (v02 SaSsdt  SaSsdt  00003000 INTL 20120913)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: SSDT 000000009b6c1200 00067C (v02  SgRef    SgPch 00001000 INTL 20120913)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: DMAR 000000009b6c1880 0000A8 (v01 INTEL      BDW  00000001 INTL 00000001)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: BGRT 000000009b6c1928 000038 (v01 _ASUS_ Notebook 01072009 AMI  00010013)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: SSDT 000000009b6c1960 000ED1 (v01 OptRef  OptTabl 00001000 INTL 20120913)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: MSDM 000000009aa95e18 000055 (v03 _ASUS_ Notebook 00000000 ASUS 00000001)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] No NUMA configuration found
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x000000025effffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Initmem setup node 0 [mem 0x00000000-0x25effffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   NODE_DATA [mem 0x25eff7000-0x25effbfff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]  [ffffea0000000000-ffffea00097fffff] PMD -> [ffff880256600000-ffff88025e5fffff] on node 0
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Zone ranges:
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   Normal   [mem 0x100000000-0x25effffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Movable zone start for each node
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Early memory node ranges
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   node   0: [mem 0x00001000-0x00057fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   node   0: [mem 0x00059000-0x0009dfff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   node   0: [mem 0x00100000-0x97070fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   node   0: [mem 0x973c6000-0x9aa36fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   node   0: [mem 0x9aa97000-0x9b296fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   node   0: [mem 0x9cfff000-0x9cffffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   node   0: [mem 0x100000000-0x25effffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] On node 0 totalpages: 2072191
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   DMA zone: 22 pages reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   DMA zone: 3996 pages, LIFO batch:0
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   DMA32 zone: 9852 pages used for memmap
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   DMA32 zone: 630499 pages, LIFO batch:31
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   Normal zone: 22464 pages used for memmap
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   Normal zone: 1437696 pages, LIFO batch:31
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1808
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl level lint[0x40])
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: NMI not connected to LINT 1!
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl res lint[0x8b])
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: NMI not connected to LINT 1!
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] low level lint[0xf])
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: NMI not connected to LINT 1!
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] dfl edge lint[0x83])
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: NMI not connected to LINT 1!
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-39
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: IRQ0 used by override.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: IRQ2 used by override.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: IRQ9 used by override.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] nr_irqs_gsi: 56
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0x00058000-0x00058fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0x97071000-0x973c5fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9aa37000-0x9aa96fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9b297000-0x9c41dfff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9c41e000-0x9cee6fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9cee7000-0x9cffefff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9d000000-0x9d7fffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9d800000-0x9fffffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xa0000000-0xf7ffffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfecfffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed03fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed04000-0xfed1bfff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] e820: [mem 0xa0000000-0xf7ffffff] available for PCI devices
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88025ec00000 s86400 r8192 d24192 u524288
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] pcpu-alloc: s86400 r8192 d24192 u524288 alloc=1*2097152
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2039789
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Policy zone: Normal
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.11-03131107-generic root=UUID=b320ac20-ec61-42ec-8900-f1b181a2d24e ro noprompt persistent quiet splash acpi_osi= vt.handoff=7
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: _OSI method disabled
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Checking aperture...
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] No AGP bridge found
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Memory: 7989084K/8288764K available (7555K kernel code, 1135K rwdata, 3528K rodata, 1348K init, 1444K bss, 299680K reserved)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Hierarchical RCU implementation.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]     Offload RCU callbacks from all CPUs
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]     Offload RCU callbacks from CPUs: 0-3.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] NR_IRQS:16640 nr_irqs:984 16
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Console: colour dummy device 80x25
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] console [tty0] enabled
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] allocated 33554432 bytes of page_cgroup
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] hpet clockevent registered
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] tsc: Fast TSC calibration using PIT
Nov 21 08:43:20 arcane-X555LB kernel: [    0.004000] tsc: Detected 2196.779 MHz processor
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 4393.55 BogoMIPS (lpj=8787116)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000005] pid_max: default: 32768 minimum: 301
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000015] init_memory_mapping: [mem 0x97071000-0x973c5fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000017]  [mem 0x97071000-0x973c5fff] page 4k
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000037] init_memory_mapping: [mem 0x9c41e000-0x9cee6fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000038]  [mem 0x9c41e000-0x9c5fffff] page 4k
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000039]  [mem 0x9c600000-0x9cdfffff] page 2M
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000040]  [mem 0x9ce00000-0x9cee6fff] page 4k
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000061] init_memory_mapping: [mem 0x9cee7000-0x9cffefff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000062]  [mem 0x9cee7000-0x9cffefff] page 4k
Nov 21 08:43:20 arcane-X555LB kernel: [    0.007892] Security Framework initialized
Nov 21 08:43:20 arcane-X555LB kernel: [    0.007900] AppArmor: AppArmor initialized
Nov 21 08:43:20 arcane-X555LB kernel: [    0.007901] Yama: becoming mindful.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.008392] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.009671] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.010189] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.010199] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.010376] Initializing cgroup subsys memory
Nov 21 08:43:20 arcane-X555LB kernel: [    0.010381] Initializing cgroup subsys devices
Nov 21 08:43:20 arcane-X555LB kernel: [    0.010383] Initializing cgroup subsys freezer
Nov 21 08:43:20 arcane-X555LB kernel: [    0.010384] Initializing cgroup subsys blkio
Nov 21 08:43:20 arcane-X555LB kernel: [    0.010385] Initializing cgroup subsys perf_event
Nov 21 08:43:20 arcane-X555LB kernel: [    0.010387] Initializing cgroup subsys hugetlb
Nov 21 08:43:20 arcane-X555LB kernel: [    0.010406] CPU: Physical Processor ID: 0
Nov 21 08:43:20 arcane-X555LB kernel: [    0.010407] CPU: Processor Core ID: 0
Nov 21 08:43:20 arcane-X555LB kernel: [    0.010411] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
Nov 21 08:43:20 arcane-X555LB kernel: [    0.010411] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.011398] mce: CPU supports 7 MCE banks
Nov 21 08:43:20 arcane-X555LB kernel: [    0.011409] CPU0: Thermal monitoring enabled (TM1)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.011418] Last level iTLB entries: 4KB 0, 2MB 0, 4MB 0
Nov 21 08:43:20 arcane-X555LB kernel: [    0.011418] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0
Nov 21 08:43:20 arcane-X555LB kernel: [    0.011418] tlb_flushall_shift: 6
Nov 21 08:43:20 arcane-X555LB kernel: [    0.011738] Freeing SMP alternatives memory: 28K (ffffffff81e6e000 - ffffffff81e75000)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.012577] ACPI: Core revision 20131115
Nov 21 08:43:20 arcane-X555LB kernel: [    0.031105] ACPI: All ACPI Tables successfully acquired
Nov 21 08:43:20 arcane-X555LB kernel: [    0.033850] ftrace: allocating 31300 entries in 123 pages
Nov 21 08:43:20 arcane-X555LB kernel: [    0.046290] dmar: Host address width 39
Nov 21 08:43:20 arcane-X555LB kernel: [    0.046292] dmar: DRHD base: 0x000000fed90000 flags: 0x0
Nov 21 08:43:20 arcane-X555LB kernel: [    0.046299] dmar: IOMMU 0: reg_base_addr fed90000 ver 1:0 cap 1c0000c40660462 ecap 7e1ff0505e
Nov 21 08:43:20 arcane-X555LB kernel: [    0.046301] dmar: DRHD base: 0x000000fed91000 flags: 0x1
Nov 21 08:43:20 arcane-X555LB kernel: [    0.046306] dmar: IOMMU 1: reg_base_addr fed91000 ver 1:0 cap d2008c20660462 ecap f010da
Nov 21 08:43:20 arcane-X555LB kernel: [    0.046308] dmar: RMRR base: 0x0000009ce40000 end: 0x0000009ce4efff
Nov 21 08:43:20 arcane-X555LB kernel: [    0.046309] dmar: RMRR base: 0x0000009d800000 end: 0x0000009fffffff
Nov 21 08:43:20 arcane-X555LB kernel: [    0.046431] IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
Nov 21 08:43:20 arcane-X555LB kernel: [    0.046432] HPET id 0 under DRHD base 0xfed91000
Nov 21 08:43:20 arcane-X555LB kernel: [    0.046433] Your BIOS is broken and requested that x2apic be disabled.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.046433] This will slightly decrease performance.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.046433] Use 'intremap=no_x2apic_optout' to override BIOS request.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.046631] Enabled IRQ remapping in xapic mode
Nov 21 08:43:20 arcane-X555LB kernel: [    0.046632] x2apic not enabled, IRQ remapping is in xapic mode
Nov 21 08:43:20 arcane-X555LB kernel: [    0.047245] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Nov 21 08:43:20 arcane-X555LB kernel: [    0.086917] smpboot: CPU0: Intel(R) Core(TM) i5-5200U CPU @ 2.20GHz (fam: 06, model: 3d, stepping: 04)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.086924] TSC deadline timer enabled
Nov 21 08:43:20 arcane-X555LB kernel: [    0.086932] Performance Events: PEBS fmt2+, generic architected perfmon, full-width counters, Intel PMU driver.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.086937] ... version:                3
Nov 21 08:43:20 arcane-X555LB kernel: [    0.086938] ... bit width:              48
Nov 21 08:43:20 arcane-X555LB kernel: [    0.086938] ... generic registers:      4
Nov 21 08:43:20 arcane-X555LB kernel: [    0.086939] ... value mask:             0000ffffffffffff
Nov 21 08:43:20 arcane-X555LB kernel: [    0.086940] ... max period:             0000ffffffffffff
Nov 21 08:43:20 arcane-X555LB kernel: [    0.086941] ... fixed-purpose events:   3
Nov 21 08:43:20 arcane-X555LB kernel: [    0.086942] ... event mask:             000000070000000f
Nov 21 08:43:20 arcane-X555LB kernel: [    0.088260] x86: Booting SMP configuration:
Nov 21 08:43:20 arcane-X555LB kernel: [    0.102427] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.088262] .... node  #0, CPUs:      #1 #2 #3
Nov 21 08:43:20 arcane-X555LB kernel: [    0.130811] x86: Booted up 1 node, 4 CPUs
Nov 21 08:43:20 arcane-X555LB kernel: [    0.130814] smpboot: Total of 4 processors activated (17574.23 BogoMIPS)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.134577] devtmpfs: initialized
Nov 21 08:43:20 arcane-X555LB kernel: [    0.137606] EVM: security.selinux
Nov 21 08:43:20 arcane-X555LB kernel: [    0.137607] EVM: security.SMACK64
Nov 21 08:43:20 arcane-X555LB kernel: [    0.137608] EVM: security.ima
Nov 21 08:43:20 arcane-X555LB kernel: [    0.137608] EVM: security.capability
Nov 21 08:43:20 arcane-X555LB kernel: [    0.137650] PM: Registering ACPI NVS region [mem 0x9b297000-0x9c41dfff] (18378752 bytes)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.138476] pinctrl core: initialized pinctrl subsystem
Nov 21 08:43:20 arcane-X555LB kernel: [    0.138520] regulator-dummy: no parameters
Nov 21 08:43:20 arcane-X555LB kernel: [    0.138549] RTC time:  8:43:04, date: 11/21/15
Nov 21 08:43:20 arcane-X555LB kernel: [    0.138574] NET: Registered protocol family 16
Nov 21 08:43:20 arcane-X555LB kernel: [    0.138664] cpuidle: using governor ladder
Nov 21 08:43:20 arcane-X555LB kernel: [    0.138666] cpuidle: using governor menu
Nov 21 08:43:20 arcane-X555LB kernel: [    0.138703] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
Nov 21 08:43:20 arcane-X555LB kernel: [    0.138705] ACPI: bus type PCI registered
Nov 21 08:43:20 arcane-X555LB kernel: [    0.138706] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
Nov 21 08:43:20 arcane-X555LB kernel: [    0.138745] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.138747] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
Nov 21 08:43:20 arcane-X555LB kernel: [    0.144452] PCI: Using configuration type 1 for base access
Nov 21 08:43:20 arcane-X555LB kernel: [    0.145195] bio: create slab <bio-0> at 0
Nov 21 08:43:20 arcane-X555LB kernel: [    0.145321] ACPI: Added _OSI(Module Device)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.145323] ACPI: Added _OSI(Processor Device)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.145324] ACPI: Added _OSI(3.0 _SCP Extensions)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.145325] ACPI: Added _OSI(Processor Aggregator Device)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.148076] ACPI : EC: EC description table is found, configuring boot EC
Nov 21 08:43:20 arcane-X555LB kernel: [    0.151028] ACPI: Executed 9 blocks of module-level executable AML code
Nov 21 08:43:20 arcane-X555LB kernel: [    0.182541] ACPI: SSDT 000000009aa57918 0003D3 (v02  PmRef  Cpu0Cst 00003001 INTL 20120913)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.183315] ACPI: Dynamic OEM Table Load:
Nov 21 08:43:20 arcane-X555LB kernel: [    0.183317] ACPI: SSDT           (null) 0003D3 (v02  PmRef  Cpu0Cst 00003001 INTL 20120913)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.186663] ACPI: SSDT 000000009aa58618 0005AA (v02  PmRef    ApIst 00003000 INTL 20120913)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.187505] ACPI: Dynamic OEM Table Load:
Nov 21 08:43:20 arcane-X555LB kernel: [    0.187507] ACPI: SSDT           (null) 0005AA (v02  PmRef    ApIst 00003000 INTL 20120913)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.190524] ACPI: SSDT 000000009aa59c18 000119 (v02  PmRef    ApCst 00003000 INTL 20120913)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.191296] ACPI: Dynamic OEM Table Load:
Nov 21 08:43:20 arcane-X555LB kernel: [    0.191298] ACPI: SSDT           (null) 000119 (v02  PmRef    ApCst 00003000 INTL 20120913)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.195264] ACPI: Interpreter enabled
Nov 21 08:43:20 arcane-X555LB kernel: [    0.195272] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.195279] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.195292] ACPI: (supports S0 S3 S4 S5)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.195293] ACPI: Using IOAPIC for interrupt routing
Nov 21 08:43:20 arcane-X555LB kernel: [    0.195319] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Nov 21 08:43:20 arcane-X555LB kernel: [    0.195545] ACPI: No dock devices found.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.197901] ACPI: Power Resource [PG00] (on)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.198140] ACPI: Power Resource [PG01] (on)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.198369] ACPI: Power Resource [PG02] (on)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.199124] ACPI: Power Resource [PC05] (on)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.214770] ACPI Error: [_OSI] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.214774] ACPI Error: Method parse/execution failed [\_SB_.PAGD._STA] (Node ffff8802530db938), AE_NOT_FOUND (20131115/psparse-536)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.214788] ACPI Error: [_OSI] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.214791] ACPI Error: Method parse/execution failed [\_SB_.PAGD._STA] (Node ffff8802530db938), AE_NOT_FOUND (20131115/psparse-536)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.214810] ACPI Error: [_OSI] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.214812] ACPI Error: Method parse/execution failed [\_SB_.PAGD._STA] (Node ffff8802530db938), AE_NOT_FOUND (20131115/psparse-536)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.216572] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
Nov 21 08:43:20 arcane-X555LB kernel: [    0.216577] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217013] acpi PNP0A08:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217464] PCI host bridge to bus 0000:00
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217466] pci_bus 0000:00: root bus resource [bus 00-3e]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217468] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217469] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217471] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217472] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217473] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217475] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217476] pci_bus 0000:00: root bus resource [mem 0x000cc000-0x000cffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217478] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217480] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217481] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217482] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217483] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217485] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217486] pci_bus 0000:00: root bus resource [mem 0x000e8000-0x000ebfff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217487] pci_bus 0000:00: root bus resource [mem 0x000ec000-0x000effff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217488] pci_bus 0000:00: root bus resource [mem 0xa0000000-0xfeafffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217495] pci 0000:00:00.0: [8086:1604] type 00 class 0x060000
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217581] pci 0000:00:02.0: [8086:1616] type 00 class 0x030000
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217591] pci 0000:00:02.0: reg 0x10: [mem 0xa1000000-0xa1ffffff 64bit]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217596] pci 0000:00:02.0: reg 0x18: [mem 0xb0000000-0xbfffffff 64bit pref]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217601] pci 0000:00:02.0: reg 0x20: [io  0x5000-0x503f]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217683] pci 0000:00:03.0: [8086:160c] type 00 class 0x040300
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217690] pci 0000:00:03.0: reg 0x10: [mem 0xa331c000-0xa331ffff 64bit]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217777] pci 0000:00:04.0: [8086:1603] type 00 class 0x118000
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217788] pci 0000:00:04.0: reg 0x10: [mem 0xa3310000-0xa3317fff 64bit]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217892] pci 0000:00:14.0: [8086:9cb1] type 00 class 0x0c0330
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217907] pci 0000:00:14.0: reg 0x10: [mem 0xa3300000-0xa330ffff 64bit]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217958] pci 0000:00:14.0: PME# supported from D3hot D3cold
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218013] pci 0000:00:14.0: System wakeup disabled by ACPI
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218039] pci 0000:00:16.0: [8086:9cba] type 00 class 0x078000
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218057] pci 0000:00:16.0: reg 0x10: [mem 0xa3324000-0xa332401f 64bit]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218119] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218196] pci 0000:00:1b.0: [8086:9ca0] type 00 class 0x040300
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218211] pci 0000:00:1b.0: reg 0x10: [mem 0xa3318000-0xa331bfff 64bit]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218261] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218315] pci 0000:00:1b.0: System wakeup disabled by ACPI
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218340] pci 0000:00:1c.0: [8086:9c90] type 01 class 0x060400
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218393] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218449] pci 0000:00:1c.0: System wakeup disabled by ACPI
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218471] pci 0000:00:1c.2: [8086:9c94] type 01 class 0x060400
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218525] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218578] pci 0000:00:1c.2: System wakeup disabled by ACPI
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218599] pci 0000:00:1c.3: [8086:9c96] type 01 class 0x060400
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218653] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218704] pci 0000:00:1c.3: System wakeup disabled by ACPI
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218726] pci 0000:00:1c.4: [8086:9c98] type 01 class 0x060400
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218780] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218831] pci 0000:00:1c.4: System wakeup disabled by ACPI
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218859] pci 0000:00:1f.0: [8086:9cc3] type 00 class 0x060100
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219029] pci 0000:00:1f.2: [8086:9c83] type 00 class 0x010601
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219042] pci 0000:00:1f.2: reg 0x10: [io  0x50b0-0x50b7]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219048] pci 0000:00:1f.2: reg 0x14: [io  0x50a0-0x50a3]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219054] pci 0000:00:1f.2: reg 0x18: [io  0x5090-0x5097]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219059] pci 0000:00:1f.2: reg 0x1c: [io  0x5080-0x5083]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219065] pci 0000:00:1f.2: reg 0x20: [io  0x5060-0x507f]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219072] pci 0000:00:1f.2: reg 0x24: [mem 0xa3322000-0xa33227ff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219102] pci 0000:00:1f.2: PME# supported from D3hot
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219165] pci 0000:00:1f.3: [8086:9ca2] type 00 class 0x0c0500
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219177] pci 0000:00:1f.3: reg 0x10: [mem 0xa3321000-0xa33210ff 64bit]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219194] pci 0000:00:1f.3: reg 0x20: [io  0x5040-0x505f]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219277] pci 0000:00:1f.6: [8086:9ca4] type 00 class 0x118000
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219306] pci 0000:00:1f.6: reg 0x10: [mem 0xa3320000-0xa3320fff 64bit]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219526] acpiphp: Slot [1] registered
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219530] pci 0000:00:1c.0: PCI bridge to [bus 01]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219605] pci 0000:02:00.0: [10ec:8168] type 00 class 0x020000
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219621] pci 0000:02:00.0: reg 0x10: [io  0x4000-0x40ff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219647] pci 0000:02:00.0: reg 0x18: [mem 0xa3204000-0xa3204fff 64bit]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219663] pci 0000:02:00.0: reg 0x20: [mem 0xa3200000-0xa3203fff 64bit]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219732] pci 0000:02:00.0: supports D1 D2
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219734] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Nov 21 08:43:20 arcane-X555LB kernel: [    0.226456] pci 0000:00:1c.2: PCI bridge to [bus 02]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.226460] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.226463] pci 0000:00:1c.2:   bridge window [mem 0xa3200000-0xa32fffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.226542] pci 0000:03:00.0: [14c3:7630] type 00 class 0x028000
Nov 21 08:43:20 arcane-X555LB kernel: [    0.226558] pci 0000:03:00.0: reg 0x10: [mem 0xa3100000-0xa31fffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.226669] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
Nov 21 08:43:20 arcane-X555LB kernel: [    0.234460] pci 0000:00:1c.3: PCI bridge to [bus 03]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.234465] pci 0000:00:1c.3:   bridge window [mem 0xa3100000-0xa31fffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.234533] pci 0000:04:00.0: [10de:1347] type 00 class 0x030200
Nov 21 08:43:20 arcane-X555LB kernel: [    0.234546] pci 0000:04:00.0: reg 0x10: [mem 0xa2000000-0xa2ffffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.234559] pci 0000:04:00.0: reg 0x14: [mem 0xc0000000-0xcfffffff 64bit pref]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.234572] pci 0000:04:00.0: reg 0x1c: [mem 0xd0000000-0xd1ffffff 64bit pref]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.234581] pci 0000:04:00.0: reg 0x24: [io  0x3000-0x307f]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.234591] pci 0000:04:00.0: reg 0x30: [mem 0xa3000000-0xa307ffff pref]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.234651] pci 0000:04:00.0: System wakeup disabled by ACPI
Nov 21 08:43:20 arcane-X555LB kernel: [    0.242464] pci 0000:00:1c.4: PCI bridge to [bus 04]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.242467] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.242470] pci 0000:00:1c.4:   bridge window [mem 0xa2000000-0xa30fffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.242474] pci 0000:00:1c.4:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.242496] acpi PNP0A08:00: Disabling ASPM (FADT indicates it is unsupported)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.246743] ACPI Error: [_OSI] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.246747] ACPI Error: Method parse/execution failed [\_SB_.PAGD._STA] (Node ffff8802530db938), AE_NOT_FOUND (20131115/psparse-536)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.246789] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.246835] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.246878] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.246921] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.246964] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.247008] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.247053] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.247096] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.247695] ACPI: Enabled 5 GPEs in block 00 to 7F
Nov 21 08:43:20 arcane-X555LB kernel: [    0.247701] ACPI: \_SB_.PCI0: notify handler is installed
Nov 21 08:43:20 arcane-X555LB kernel: [    0.247779] Found 1 acpi root devices
Nov 21 08:43:20 arcane-X555LB kernel: [    0.247842] ACPI : EC: GPE = 0xa, I/O: command/status = 0x66, data = 0x62
Nov 21 08:43:20 arcane-X555LB kernel: [    0.247916] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Nov 21 08:43:20 arcane-X555LB kernel: [    0.247919] vgaarb: loaded
Nov 21 08:43:20 arcane-X555LB kernel: [    0.247920] vgaarb: bridge control possible 0000:00:02.0
Nov 21 08:43:20 arcane-X555LB kernel: [    0.248037] SCSI subsystem initialized
Nov 21 08:43:20 arcane-X555LB kernel: [    0.248072] libata version 3.00 loaded.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.248085] ACPI: bus type USB registered
Nov 21 08:43:20 arcane-X555LB kernel: [    0.248096] usbcore: registered new interface driver usbfs
Nov 21 08:43:20 arcane-X555LB kernel: [    0.248101] usbcore: registered new interface driver hub
Nov 21 08:43:20 arcane-X555LB kernel: [    0.248118] usbcore: registered new device driver usb
Nov 21 08:43:20 arcane-X555LB kernel: [    0.248203] PCI: Using ACPI for IRQ routing
Nov 21 08:43:20 arcane-X555LB kernel: [    0.249349] PCI: pci_cache_line_size set to 64 bytes
Nov 21 08:43:20 arcane-X555LB kernel: [    0.249389] e820: reserve RAM buffer [mem 0x00058000-0x0005ffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.249390] e820: reserve RAM buffer [mem 0x0009e000-0x0009ffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.249391] e820: reserve RAM buffer [mem 0x97071000-0x97ffffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.249393] e820: reserve RAM buffer [mem 0x9aa37000-0x9bffffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.249394] e820: reserve RAM buffer [mem 0x9b297000-0x9bffffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.249395] e820: reserve RAM buffer [mem 0x9d000000-0x9fffffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.249396] e820: reserve RAM buffer [mem 0x25f000000-0x25fffffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.249457] NetLabel: Initializing
Nov 21 08:43:20 arcane-X555LB kernel: [    0.249458] NetLabel:  domain hash size = 128
Nov 21 08:43:20 arcane-X555LB kernel: [    0.249458] NetLabel:  protocols = UNLABELED CIPSOv4
Nov 21 08:43:20 arcane-X555LB kernel: [    0.249468] NetLabel:  unlabeled traffic allowed by default
Nov 21 08:43:20 arcane-X555LB kernel: [    0.249517] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
Nov 21 08:43:20 arcane-X555LB kernel: [    0.249522] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
Nov 21 08:43:20 arcane-X555LB kernel: [    0.251552] Switched to clocksource hpet
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255124] AppArmor: AppArmor Filesystem Enabled
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255141] pnp: PnP ACPI init
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255151] ACPI: bus type PNP registered
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255306] system 00:00: [io  0x0240-0x0259] has been reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255309] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255377] pnp 00:01: Plug and Play ACPI device, IDs ETD0108 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255412] pnp 00:02: Plug and Play ACPI device, IDs ATK3001 PNP030b (active)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255418] pnp 00:03: [dma 4]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255430] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255447] pnp 00:04: Plug and Play ACPI device, IDs INT0800 (active)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255535] pnp 00:05: Plug and Play ACPI device, IDs PNP0103 (active)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255590] system 00:06: [io  0x0680-0x069f] has been reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255592] system 00:06: [io  0xffff] has been reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255593] system 00:06: [io  0xffff] has been reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255595] system 00:06: [io  0xffff] has been reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255596] system 00:06: [io  0x1800-0x18fe] could not be reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255598] system 00:06: [io  0x164e-0x164f] has been reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255599] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255636] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255665] system 00:08: [io  0x1854-0x1857] has been reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255667] system 00:08: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255788] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255789] system 00:09: [mem 0xfed10000-0xfed17fff] has been reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255791] system 00:09: [mem 0xfed18000-0xfed18fff] has been reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255792] system 00:09: [mem 0xfed19000-0xfed19fff] has been reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255794] system 00:09: [mem 0xf8000000-0xfbffffff] has been reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255796] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255797] system 00:09: [mem 0xfed90000-0xfed93fff] could not be reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255799] system 00:09: [mem 0xfed45000-0xfed8ffff] has been reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255800] system 00:09: [mem 0xff000000-0xffffffff] has been reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255802] system 00:09: [mem 0xfee00000-0xfeefffff] could not be reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255803] system 00:09: [mem 0xa0010000-0xa001ffff] has been reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255805] system 00:09: [mem 0xa0000000-0xa000ffff] has been reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255806] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.259774] ACPI Error: [_OSI] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.259779] ACPI Error: Method parse/execution failed [\_SB_.PAGD._STA] (Node ffff8802530db938), AE_NOT_FOUND (20131115/psparse-536)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.260014] pnp: PnP ACPI: found 10 devices
Nov 21 08:43:20 arcane-X555LB kernel: [    0.260015] ACPI: bus type PNP unregistered
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265851] pci 0000:00:1c.0: PCI bridge to [bus 01]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265861] pci 0000:00:1c.2: PCI bridge to [bus 02]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265863] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265867] pci 0000:00:1c.2:   bridge window [mem 0xa3200000-0xa32fffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265873] pci 0000:00:1c.3: PCI bridge to [bus 03]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265876] pci 0000:00:1c.3:   bridge window [mem 0xa3100000-0xa31fffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265882] pci 0000:00:1c.4: PCI bridge to [bus 04]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265884] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265888] pci 0000:00:1c.4:   bridge window [mem 0xa2000000-0xa30fffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265891] pci 0000:00:1c.4:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265896] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265897] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265899] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265900] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265901] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265903] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265904] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265905] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265907] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265908] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265909] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265910] pci_bus 0000:00: resource 15 [mem 0x000e0000-0x000e3fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265912] pci_bus 0000:00: resource 16 [mem 0x000e4000-0x000e7fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265913] pci_bus 0000:00: resource 17 [mem 0x000e8000-0x000ebfff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265914] pci_bus 0000:00: resource 18 [mem 0x000ec000-0x000effff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265915] pci_bus 0000:00: resource 19 [mem 0xa0000000-0xfeafffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265917] pci_bus 0000:02: resource 0 [io  0x4000-0x4fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265918] pci_bus 0000:02: resource 1 [mem 0xa3200000-0xa32fffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265920] pci_bus 0000:03: resource 1 [mem 0xa3100000-0xa31fffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265921] pci_bus 0000:04: resource 0 [io  0x3000-0x3fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265923] pci_bus 0000:04: resource 1 [mem 0xa2000000-0xa30fffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265924] pci_bus 0000:04: resource 2 [mem 0xc0000000-0xd1ffffff 64bit pref]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265945] NET: Registered protocol family 2
Nov 21 08:43:20 arcane-X555LB kernel: [    0.266105] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.266221] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.266325] TCP: Hash tables configured (established 65536 bind 65536)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.266341] TCP: reno registered
Nov 21 08:43:20 arcane-X555LB kernel: [    0.266351] UDP hash table entries: 4096 (order: 5, 131072 bytes)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.266375] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.266424] NET: Registered protocol family 1
Nov 21 08:43:20 arcane-X555LB kernel: [    0.266433] pci 0000:00:02.0: Boot video device
Nov 21 08:43:20 arcane-X555LB kernel: [    0.266622] PCI: CLS 64 bytes, default 64
Nov 21 08:43:20 arcane-X555LB kernel: [    0.266662] Trying to unpack rootfs image as initramfs...
Nov 21 08:43:20 arcane-X555LB kernel: [    0.531203] Freeing initrd memory: 17992K (ffff880035ccc000 - ffff880036e5e000)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.531212] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.531214] software IO TLB [mem 0x921ea000-0x961ea000] (64MB) mapped at [ffff8800921ea000-ffff8800961e9fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.531368] microcode: CPU0 sig=0x306d4, pf=0x40, revision=0x1f
Nov 21 08:43:20 arcane-X555LB kernel: [    0.531374] microcode: CPU1 sig=0x306d4, pf=0x40, revision=0x1f
Nov 21 08:43:20 arcane-X555LB kernel: [    0.531381] microcode: CPU2 sig=0x306d4, pf=0x40, revision=0x1f
Nov 21 08:43:20 arcane-X555LB kernel: [    0.531387] microcode: CPU3 sig=0x306d4, pf=0x40, revision=0x1f
Nov 21 08:43:20 arcane-X555LB kernel: [    0.531423] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Nov 21 08:43:20 arcane-X555LB kernel: [    0.531424] Scanning for low memory corruption every 60 seconds
Nov 21 08:43:20 arcane-X555LB kernel: [    0.531623] Initialise system trusted keyring
Nov 21 08:43:20 arcane-X555LB kernel: [    0.531654] audit: initializing netlink socket (disabled)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.531661] type=2000 audit(1448095384.528:1): initialized
Nov 21 08:43:20 arcane-X555LB kernel: [    0.557256] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Nov 21 08:43:20 arcane-X555LB kernel: [    0.558211] zbud: loaded
Nov 21 08:43:20 arcane-X555LB kernel: [    0.558334] VFS: Disk quotas dquot_6.5.2
Nov 21 08:43:20 arcane-X555LB kernel: [    0.558368] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.558678] fuse init (API version 7.22)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.558730] msgmni has been set to 15770
Nov 21 08:43:20 arcane-X555LB kernel: [    0.558766] Key type big_key registered
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559073] Key type asymmetric registered
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559075] Asymmetric key parser 'x509' registered
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559095] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559122] io scheduler noop registered
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559123] io scheduler deadline registered (default)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559140] io scheduler cfq registered
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559300] pcieport 0000:00:1c.0: irq 58 for MSI/MSI-X
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559421] pcieport 0000:00:1c.2: irq 59 for MSI/MSI-X
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559543] pcieport 0000:00:1c.3: irq 60 for MSI/MSI-X
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559654] pcieport 0000:00:1c.4: irq 61 for MSI/MSI-X
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559709] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559713] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559723] pcieport 0000:00:1c.2: Signaling PME through PCIe PME interrupt
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559724] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559727] pcie_pme 0000:00:1c.2:pcie01: service driver pcie_pme loaded
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559741] pcieport 0000:00:1c.3: Signaling PME through PCIe PME interrupt
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559744] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559747] pcie_pme 0000:00:1c.3:pcie01: service driver pcie_pme loaded
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559756] pcieport 0000:00:1c.4: Signaling PME through PCIe PME interrupt
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559758] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559761] pcie_pme 0000:00:1c.4:pcie01: service driver pcie_pme loaded
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559769] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559779] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559809] efifb: probing for efifb
Nov 21 08:43:20 arcane-X555LB kernel: [    0.560008] efifb: framebuffer at 0xb0000000, mapped to 0xffffc90009f80000, using 1920k, total 1920k
Nov 21 08:43:20 arcane-X555LB kernel: [    0.560010] efifb: mode is 800x600x32, linelength=3200, pages=1
Nov 21 08:43:20 arcane-X555LB kernel: [    0.560010] efifb: scrolling: redraw
Nov 21 08:43:20 arcane-X555LB kernel: [    0.560012] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Nov 21 08:43:20 arcane-X555LB kernel: [    0.560889] Console: switching to colour frame buffer device 100x37
Nov 21 08:43:20 arcane-X555LB kernel: [    0.561711] fb0: EFI VGA frame buffer device
Nov 21 08:43:20 arcane-X555LB kernel: [    0.561719] intel_idle: does not run on family 6 model 61
Nov 21 08:43:20 arcane-X555LB kernel: [    0.561724] ipmi message handler version 39.2
Nov 21 08:43:20 arcane-X555LB kernel: [    0.567512] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Nov 21 08:43:20 arcane-X555LB kernel: [    0.567566] ACPI: AC Adapter [AC0] (off-line)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.567662] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
Nov 21 08:43:20 arcane-X555LB kernel: [    0.568312] ACPI: Lid Switch [LID]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.568340] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
Nov 21 08:43:20 arcane-X555LB kernel: [    0.568344] ACPI: Sleep Button [SLPB]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.568368] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Nov 21 08:43:20 arcane-X555LB kernel: [    0.568370] ACPI: Power Button [PWRF]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.568645] Monitor-Mwait will be used to enter C-1 state
Nov 21 08:43:20 arcane-X555LB kernel: [    0.568648] Monitor-Mwait will be used to enter C-2 state
Nov 21 08:43:20 arcane-X555LB kernel: [    0.568651] Monitor-Mwait will be used to enter C-3 state
Nov 21 08:43:20 arcane-X555LB kernel: [    0.568665] ACPI: acpi_idle registered with cpuidle
Nov 21 08:43:20 arcane-X555LB kernel: [    0.569600] thermal LNXTHERM:00: registered as thermal_zone0
Nov 21 08:43:20 arcane-X555LB kernel: [    0.569602] ACPI: Thermal Zone [THRM] (56 C)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.569634] GHES: HEST is not enabled!
Nov 21 08:43:20 arcane-X555LB kernel: [    0.569691] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Nov 21 08:43:20 arcane-X555LB kernel: [    0.571159] Linux agpgart interface v0.103
Nov 21 08:43:20 arcane-X555LB kernel: [    0.574633] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Nov 21 08:43:20 arcane-X555LB kernel: [    0.574638] ACPI: Battery Slot [BAT0] (battery present)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.574696] brd: module loaded
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575130] loop: module loaded
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575367] libphy: Fixed MDIO Bus: probed
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575425] tun: Universal TUN/TAP device driver, 1.6
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575426] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575457] PPP generic driver version 2.4.2
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575509] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575511] ehci-pci: EHCI PCI platform driver
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575518] ehci-platform: EHCI generic platform driver
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575523] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575524] ohci-pci: OHCI PCI platform driver
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575530] ohci-platform: OHCI generic platform driver
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575534] uhci_hcd: USB Universal Host Controller Interface driver
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575634] xhci_hcd 0000:00:14.0: xHCI Host Controller
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575638] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575713] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575729] xhci_hcd 0000:00:14.0: irq 62 for MSI/MSI-X
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575776] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575777] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575779] usb usb1: Product: xHCI Host Controller
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575780] usb usb1: Manufacturer: Linux 3.13.11-03131107-generic xhci_hcd
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575781] usb usb1: SerialNumber: 0000:00:14.0
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575855] hub 1-0:1.0: USB hub found
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575865] hub 1-0:1.0: 11 ports detected
Nov 21 08:43:20 arcane-X555LB kernel: [    0.578193] xhci_hcd 0000:00:14.0: xHCI Host Controller
Nov 21 08:43:20 arcane-X555LB kernel: [    0.578196] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
Nov 21 08:43:20 arcane-X555LB kernel: [    0.578221] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
Nov 21 08:43:20 arcane-X555LB kernel: [    0.578222] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Nov 21 08:43:20 arcane-X555LB kernel: [    0.578223] usb usb2: Product: xHCI Host Controller
Nov 21 08:43:20 arcane-X555LB kernel: [    0.578225] usb usb2: Manufacturer: Linux 3.13.11-03131107-generic xhci_hcd
Nov 21 08:43:20 arcane-X555LB kernel: [    0.578226] usb usb2: SerialNumber: 0000:00:14.0
Nov 21 08:43:20 arcane-X555LB kernel: [    0.578294] hub 2-0:1.0: USB hub found
Nov 21 08:43:20 arcane-X555LB kernel: [    0.578301] hub 2-0:1.0: 4 ports detected
Nov 21 08:43:20 arcane-X555LB kernel: [    0.583570] i8042: PNP: PS/2 Controller [PNP030b:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Nov 21 08:43:20 arcane-X555LB kernel: [    0.586589] i8042: Detected active multiplexing controller, rev 1.1
Nov 21 08:43:20 arcane-X555LB kernel: [    0.588498] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov 21 08:43:20 arcane-X555LB kernel: [    0.588502] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Nov 21 08:43:20 arcane-X555LB kernel: [    0.588529] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Nov 21 08:43:20 arcane-X555LB kernel: [    0.588538] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Nov 21 08:43:20 arcane-X555LB kernel: [    0.588548] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Nov 21 08:43:20 arcane-X555LB kernel: [    0.588779] mousedev: PS/2 mouse device common for all mice
Nov 21 08:43:20 arcane-X555LB kernel: [    0.589257] rtc_cmos 00:07: RTC can wake from S4
Nov 21 08:43:20 arcane-X555LB kernel: [    0.589452] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
Nov 21 08:43:20 arcane-X555LB kernel: [    0.589479] rtc_cmos 00:07: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
Nov 21 08:43:20 arcane-X555LB kernel: [    0.589529] device-mapper: uevent: version 1.0.3
Nov 21 08:43:20 arcane-X555LB kernel: [    0.589587] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
Nov 21 08:43:20 arcane-X555LB kernel: [    0.589592] ledtrig-cpu: registered to indicate activity on CPUs
Nov 21 08:43:20 arcane-X555LB kernel: [    0.589593] EFI Variables Facility v0.08 2004-May-17
Nov 21 08:43:20 arcane-X555LB kernel: [    0.591131] TCP: cubic registered
Nov 21 08:43:20 arcane-X555LB kernel: [    0.591188] NET: Registered protocol family 10
Nov 21 08:43:20 arcane-X555LB kernel: [    0.591300] NET: Registered protocol family 17
Nov 21 08:43:20 arcane-X555LB kernel: [    0.591310] Key type dns_resolver registered
Nov 21 08:43:20 arcane-X555LB kernel: [    0.591854] Loading compiled-in X.509 certificates
Nov 21 08:43:20 arcane-X555LB kernel: [    0.592524] Loaded X.509 cert 'Magrathea: Glacier signing key: 3ce7d6b7ac2aa04206fb669ece940cfebfb09e52'
Nov 21 08:43:20 arcane-X555LB kernel: [    0.592534] registered taskstats version 1
Nov 21 08:43:20 arcane-X555LB kernel: [    0.594831] Key type trusted registered
Nov 21 08:43:20 arcane-X555LB kernel: [    0.596657] Key type encrypted registered
Nov 21 08:43:20 arcane-X555LB kernel: [    0.598010] AppArmor: AppArmor sha1 policy hashing enabled
Nov 21 08:43:20 arcane-X555LB kernel: [    0.598013] IMA: No TPM chip found, activating TPM-bypass!
Nov 21 08:43:20 arcane-X555LB kernel: [    0.598401] regulator-dummy: disabling
Nov 21 08:43:20 arcane-X555LB kernel: [    0.598457]   Magic number: 7:141:726
Nov 21 08:43:20 arcane-X555LB kernel: [    0.598465] block loop6: hash matches
Nov 21 08:43:20 arcane-X555LB kernel: [    0.598564] rtc_cmos 00:07: setting system clock to 2015-11-21 08:43:04 UTC (1448095384)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.599139] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Nov 21 08:43:20 arcane-X555LB kernel: [    0.599141] EDD information not available.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.599176] PM: Hibernation image not present or could not be loaded.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.600076] Freeing unused kernel memory: 1348K (ffffffff81d1d000 - ffffffff81e6e000)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.600078] Write protecting the kernel read-only data: 12288k
Nov 21 08:43:20 arcane-X555LB kernel: [    0.601288] Freeing unused kernel memory: 624K (ffff880002764000 - ffff880002800000)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.602309] Freeing unused kernel memory: 568K (ffff880002b72000 - ffff880002c00000)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.627809] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Nov 21 08:43:20 arcane-X555LB kernel: [    0.635804] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Nov 21 08:43:20 arcane-X555LB kernel: [    0.635814] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
Nov 21 08:43:20 arcane-X555LB kernel: [    0.636142] ahci 0000:00:1f.2: version 3.0
Nov 21 08:43:20 arcane-X555LB kernel: [    0.636239] ahci 0000:00:1f.2: irq 63 for MSI/MSI-X
Nov 21 08:43:20 arcane-X555LB kernel: [    0.643874] r8169 0000:02:00.0: irq 64 for MSI/MSI-X
Nov 21 08:43:20 arcane-X555LB kernel: [    0.644038] r8169 0000:02:00.0 eth0: RTL8168g/8111g at 0xffffc900040a2000, 1c:b7:2c:a2:ad:f1, XID 10900800 IRQ 64
Nov 21 08:43:20 arcane-X555LB kernel: [    0.644041] r8169 0000:02:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.651479] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 6 Gbps 0x3 impl SATA mode
Nov 21 08:43:20 arcane-X555LB kernel: [    0.651485] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo only pio slum part deso sadm sds apst 
Nov 21 08:43:20 arcane-X555LB kernel: [    0.652035] scsi0 : ahci
Nov 21 08:43:20 arcane-X555LB kernel: [    0.652108] scsi1 : ahci
Nov 21 08:43:20 arcane-X555LB kernel: [    0.652162] scsi2 : ahci
Nov 21 08:43:20 arcane-X555LB kernel: [    0.652207] scsi3 : ahci
Nov 21 08:43:20 arcane-X555LB kernel: [    0.652251] ata1: SATA max UDMA/133 abar m2048@0xa3322000 port 0xa3322100 irq 63
Nov 21 08:43:20 arcane-X555LB kernel: [    0.652253] ata2: SATA max UDMA/133 abar m2048@0xa3322000 port 0xa3322180 irq 63
Nov 21 08:43:20 arcane-X555LB kernel: [    0.652255] ata3: DUMMY
Nov 21 08:43:20 arcane-X555LB kernel: [    0.652256] ata4: DUMMY
Nov 21 08:43:20 arcane-X555LB kernel: [    0.887463] usb 1-5: new high-speed USB device number 2 using xhci_hcd
Nov 21 08:43:20 arcane-X555LB kernel: [    0.925145] usb 1-5: New USB device found, idVendor=0bda, idProduct=57b5
Nov 21 08:43:20 arcane-X555LB kernel: [    0.925148] usb 1-5: New USB device strings: Mfr=3, Product=1, SerialNumber=2
Nov 21 08:43:20 arcane-X555LB kernel: [    0.925150] usb 1-5: Product: USB Camera
Nov 21 08:43:20 arcane-X555LB kernel: [    0.925152] usb 1-5: Manufacturer: 04081-00092400F6GL2R
Nov 21 08:43:20 arcane-X555LB kernel: [    0.925153] usb 1-5: SerialNumber: 200901010001
Nov 21 08:43:20 arcane-X555LB kernel: [    0.971423] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.971441] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.972782] ata1.00: ATA-8: HGST HTS721075A9E630, JB2OA3J0, max UDMA/133
Nov 21 08:43:20 arcane-X555LB kernel: [    0.972786] ata1.00: 1465149168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Nov 21 08:43:20 arcane-X555LB kernel: [    0.974277] ata1.00: configured for UDMA/133
Nov 21 08:43:20 arcane-X555LB kernel: [    0.974480] scsi 0:0:0:0: Direct-Access     ATA      HGST HTS721075A9 JB2O PQ: 0 ANSI: 5
Nov 21 08:43:20 arcane-X555LB kernel: [    0.974614] sd 0:0:0:0: [sda] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.974618] sd 0:0:0:0: [sda] 4096-byte physical blocks
Nov 21 08:43:20 arcane-X555LB kernel: [    0.974627] sd 0:0:0:0: Attached scsi generic sg0 type 0
Nov 21 08:43:20 arcane-X555LB kernel: [    0.974691] sd 0:0:0:0: [sda] Write Protect is off
Nov 21 08:43:20 arcane-X555LB kernel: [    0.974695] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov 21 08:43:20 arcane-X555LB kernel: [    0.974729] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 21 08:43:20 arcane-X555LB kernel: [    0.975571] ata2.00: ATAPI: TSSTcorp CDDVDW SU-228GB, AS00, max UDMA/100
Nov 21 08:43:20 arcane-X555LB kernel: [    0.978216] ata2.00: configured for UDMA/100
Nov 21 08:43:20 arcane-X555LB kernel: [    0.984618] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW SU-228GB  AS00 PQ: 0 ANSI: 5
Nov 21 08:43:20 arcane-X555LB kernel: [    0.990038] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Nov 21 08:43:20 arcane-X555LB kernel: [    0.990041] cdrom: Uniform CD-ROM driver Revision: 3.20
Nov 21 08:43:20 arcane-X555LB kernel: [    0.990165] sr 1:0:0:0: Attached scsi CD-ROM sr0
Nov 21 08:43:20 arcane-X555LB kernel: [    0.990328] sr 1:0:0:0: Attached scsi generic sg1 type 5
Nov 21 08:43:20 arcane-X555LB kernel: [    1.015292]  sda: sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8
Nov 21 08:43:20 arcane-X555LB kernel: [    1.015824] sd 0:0:0:0: [sda] Attached SCSI disk
Nov 21 08:43:20 arcane-X555LB kernel: [    1.091387] usb 1-6: new high-speed USB device number 3 using xhci_hcd
Nov 21 08:43:20 arcane-X555LB kernel: [    1.121481] usb 1-6: New USB device found, idVendor=0489, idProduct=e080
Nov 21 08:43:20 arcane-X555LB kernel: [    1.121484] usb 1-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Nov 21 08:43:20 arcane-X555LB kernel: [    1.121486] usb 1-6: Product: BT
Nov 21 08:43:20 arcane-X555LB kernel: [    1.121487] usb 1-6: Manufacturer: MediaTek
Nov 21 08:43:20 arcane-X555LB kernel: [    1.121489] usb 1-6: SerialNumber: 1.0
Nov 21 08:43:20 arcane-X555LB kernel: [    1.287325] usb 1-8: new high-speed USB device number 4 using xhci_hcd
Nov 21 08:43:20 arcane-X555LB kernel: [    1.303616] usb 1-8: New USB device found, idVendor=0bda, idProduct=0129
Nov 21 08:43:20 arcane-X555LB kernel: [    1.303619] usb 1-8: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Nov 21 08:43:20 arcane-X555LB kernel: [    1.303621] usb 1-8: Product: USB2.0-CRW
Nov 21 08:43:20 arcane-X555LB kernel: [    1.303622] usb 1-8: Manufacturer: Generic
Nov 21 08:43:20 arcane-X555LB kernel: [    1.303623] usb 1-8: SerialNumber: 20100201396000000
Nov 21 08:43:20 arcane-X555LB kernel: [    1.364376] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x381f00)
Nov 21 08:43:20 arcane-X555LB kernel: [    1.378951] psmouse serio4: elantech: Synaptics capabilities query result 0x10, 0x14, 0x0e.
Nov 21 08:43:20 arcane-X555LB kernel: [    1.446697] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input11
Nov 21 08:43:20 arcane-X555LB kernel: [    1.527246] tsc: Refined TSC clocksource calibration: 2196.821 MHz
Nov 21 08:43:20 arcane-X555LB kernel: [    1.745787] EXT4-fs (sda7): INFO: recovery required on readonly filesystem
Nov 21 08:43:20 arcane-X555LB kernel: [    1.745790] EXT4-fs (sda7): write access will be enabled during recovery
Nov 21 08:43:20 arcane-X555LB kernel: [    2.069157] random: nonblocking pool is initialized
Nov 21 08:43:20 arcane-X555LB kernel: [    2.527034] Switched to clocksource tsc
Nov 21 08:43:20 arcane-X555LB kernel: [    3.477366] EXT4-fs (sda7): orphan cleanup on readonly fs
Nov 21 08:43:20 arcane-X555LB kernel: [    3.651697] EXT4-fs (sda7): 494 orphan inodes deleted
Nov 21 08:43:20 arcane-X555LB kernel: [    3.651701] EXT4-fs (sda7): recovery complete
Nov 21 08:43:20 arcane-X555LB kernel: [    3.883061] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
Nov 21 08:43:20 arcane-X555LB kernel: [    6.171592] Adding 8288252k swap on /dev/sda8.  Priority:-1 extents:1 across:8288252k FS
Nov 21 08:43:20 arcane-X555LB kernel: [    7.441987] lp: driver loaded but no devices found
Nov 21 08:43:20 arcane-X555LB kernel: [    7.481817] ppdev: user-space parallel port driver
Nov 21 08:43:20 arcane-X555LB kernel: [    8.186182] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Nov 21 08:43:20 arcane-X555LB kernel: [    8.235841] wmi: Mapper loaded
Nov 21 08:43:20 arcane-X555LB kernel: [    8.238516] ACPI Warning: 0x0000000000001828-0x000000000000182f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
Nov 21 08:43:20 arcane-X555LB kernel: [    8.238523] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Nov 21 08:43:20 arcane-X555LB kernel: [    8.238541] ACPI Warning: 0x0000000000001c30-0x0000000000001c3f SystemIO conflicts with Region \GPRL 1 (20131115/utaddress-251)
Nov 21 08:43:20 arcane-X555LB kernel: [    8.238545] ACPI Warning: 0x0000000000001c30-0x0000000000001c3f SystemIO conflicts with Region \GPR_ 2 (20131115/utaddress-251)
Nov 21 08:43:20 arcane-X555LB kernel: [    8.238549] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Nov 21 08:43:20 arcane-X555LB kernel: [    8.238551] ACPI Warning: 0x0000000000001c00-0x0000000000001c2f SystemIO conflicts with Region \GPRL 1 (20131115/utaddress-251)
Nov 21 08:43:20 arcane-X555LB kernel: [    8.238554] ACPI Warning: 0x0000000000001c00-0x0000000000001c2f SystemIO conflicts with Region \GPR_ 2 (20131115/utaddress-251)
Nov 21 08:43:20 arcane-X555LB kernel: [    8.238558] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Nov 21 08:43:20 arcane-X555LB kernel: [    8.238559] lpc_ich: Resource conflict(s) found affecting gpio_ich
Nov 21 08:43:20 arcane-X555LB kernel: [    8.423103] mei_me 0000:00:16.0: irq 65 for MSI/MSI-X
Nov 21 08:43:20 arcane-X555LB kernel: [    8.832805] [drm] Initialized drm 1.1.0 20060810
Nov 21 08:43:20 arcane-X555LB kernel: [    8.879620] cfg80211: Calling CRDA to update world regulatory domain
Nov 21 08:43:20 arcane-X555LB kernel: [    8.984442] snd_hda_intel 0000:00:03.0: irq 66 for MSI/MSI-X
Nov 21 08:43:20 arcane-X555LB kernel: [    9.120383] mt7630e: module verification failed: signature and/or  required key missing - tainting kernel
Nov 21 08:43:20 arcane-X555LB kernel: [    9.121043] ==>MT76x0_WLAN_ChipOnOff(): OnOff:1 pAd->WlanFunCtrl.word = 0x0, Reg-WlanFunCtrl=0xff000202
Nov 21 08:43:20 arcane-X555LB kernel: [    9.121045] WlanFunCtrl.word = 0xffff0203
Nov 21 08:43:20 arcane-X555LB kernel: [    9.121097] MACVersion = 0x76502000
Nov 21 08:43:20 arcane-X555LB kernel: [    9.121104] <== MT76x0_WLAN_ChipOnOff():  pAd->WlanFunCtrl.word = 0xffff0203, Reg->WlanFunCtrl=0xffff0f03!
Nov 21 08:43:20 arcane-X555LB kernel: [    9.121112] MAC_version=0x76300002
Nov 21 08:43:20 arcane-X555LB kernel: [    9.121123] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 7630, rev 0002 detected
Nov 21 08:43:20 arcane-X555LB kernel: [    9.123012] MAC: 40:b8:9a:76:8a:17
Nov 21 08:43:20 arcane-X555LB kernel: [    9.123015] MAC_version=0x76300002
Nov 21 08:43:20 arcane-X555LB kernel: [    9.123016] RFIC =0x7630
Nov 21 08:43:20 arcane-X555LB kernel: [    9.123017] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 7630 detected
Nov 21 08:43:20 arcane-X555LB kernel: [    9.123018] rt2x00dev->chip.rt = 0x7630
Nov 21 08:43:20 arcane-X555LB kernel: [    9.123019] rt2x00dev->chip.rf = 0x7630
Nov 21 08:43:20 arcane-X555LB kernel: [    9.130269] asus_wmi: ASUS WMI generic driver loaded
Nov 21 08:43:20 arcane-X555LB kernel: [    9.133193] asus_wmi: Initialization: 0x1
Nov 21 08:43:20 arcane-X555LB kernel: [    9.133242] asus_wmi: BIOS WMI version: 7.9
Nov 21 08:43:20 arcane-X555LB kernel: [    9.133292] asus_wmi: SFUN value: 0xa0077
Nov 21 08:43:20 arcane-X555LB kernel: [    9.134512] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input12
Nov 21 08:43:20 arcane-X555LB kernel: [    9.134967] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
Nov 21 08:43:20 arcane-X555LB kernel: [    9.135796] -->RTMPAllocTxRxRingMemory
Nov 21 08:43:20 arcane-X555LB kernel: [    9.135800] CTRL Ring: total 512 bytes allocated
Nov 21 08:43:20 arcane-X555LB kernel: [    9.135802] <-- RTMPAllocTxRxRingMemory, Status=0
Nov 21 08:43:20 arcane-X555LB kernel: [    9.145478] asus_wmi: Backlight controlled by ACPI video driver
Nov 21 08:43:20 arcane-X555LB kernel: [    9.788990] ip_tables: (C) 2000-2006 Netfilter Core Team
Nov 21 08:43:20 arcane-X555LB kernel: [    9.992898] hda-intel 0000:00:03.0: Codec #0 probe error; disabling it...
Nov 21 08:43:20 arcane-X555LB kernel: [   10.006442] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Nov 21 08:43:20 arcane-X555LB kernel: [   10.269833] ip6_tables: (C) 2000-2006 Netfilter Core Team
Nov 21 08:43:20 arcane-X555LB kernel: [   10.374421] cfg80211: World regulatory domain updated:
Nov 21 08:43:20 arcane-X555LB kernel: [   10.374424] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov 21 08:43:20 arcane-X555LB kernel: [   10.374426] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:43:20 arcane-X555LB kernel: [   10.374428] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:43:20 arcane-X555LB kernel: [   10.374429] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:43:20 arcane-X555LB kernel: [   10.374430] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:43:20 arcane-X555LB kernel: [   10.374431] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:43:20 arcane-X555LB kernel: [   10.374571] cfg80211: Calling CRDA for country: US
Nov 21 08:43:20 arcane-X555LB kernel: [   10.376453] cfg80211: Regulatory domain changed to country: US
Nov 21 08:43:20 arcane-X555LB kernel: [   10.376456] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov 21 08:43:20 arcane-X555LB kernel: [   10.376457] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Nov 21 08:43:20 arcane-X555LB kernel: [   10.376459] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
Nov 21 08:43:20 arcane-X555LB kernel: [   10.376460] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:43:20 arcane-X555LB kernel: [   10.376461] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:43:20 arcane-X555LB kernel: [   10.376462] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:43:20 arcane-X555LB kernel: [   10.376463] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
Nov 21 08:43:20 arcane-X555LB kernel: [   10.376464] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
Nov 21 08:43:20 arcane-X555LB kernel: [   10.443310] Linux video capture interface: v2.00
Nov 21 08:43:20 arcane-X555LB kernel: [   10.482419] rts5139: module is from the staging directory, the quality is unknown, you have been warned.
Nov 21 08:43:20 arcane-X555LB kernel: [   10.483883] scsi4 : SCSI emulation for RTS5139 USB card reader
Nov 21 08:43:20 arcane-X555LB kernel: [   10.483962] usbcore: registered new interface driver rts5139
Nov 21 08:43:20 arcane-X555LB kernel: [   10.484000] scsi 4:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
Nov 21 08:43:20 arcane-X555LB kernel: [   10.484337] sd 4:0:0:0: Attached scsi generic sg2 type 0
Nov 21 08:43:20 arcane-X555LB kernel: [   10.564537] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Nov 21 08:43:20 arcane-X555LB kernel: [   10.701100] type=1400 audit(1448113394.603:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=468 comm="apparmor_parser"
Nov 21 08:43:20 arcane-X555LB kernel: [   10.701106] type=1400 audit(1448113394.603:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=468 comm="apparmor_parser"
Nov 21 08:43:20 arcane-X555LB kernel: [   10.701109] type=1400 audit(1448113394.603:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=468 comm="apparmor_parser"
Nov 21 08:43:20 arcane-X555LB kernel: [   10.701322] type=1400 audit(1448113394.603:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=393 comm="apparmor_parser"
Nov 21 08:43:20 arcane-X555LB kernel: [   10.701329] type=1400 audit(1448113394.603:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=393 comm="apparmor_parser"
Nov 21 08:43:20 arcane-X555LB kernel: [   10.701334] type=1400 audit(1448113394.603:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=393 comm="apparmor_parser"
Nov 21 08:43:20 arcane-X555LB kernel: [   10.701342] type=1400 audit(1448113394.603:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=394 comm="apparmor_parser"
Nov 21 08:43:20 arcane-X555LB kernel: [   10.701348] type=1400 audit(1448113394.603:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=394 comm="apparmor_parser"
Nov 21 08:43:20 arcane-X555LB kernel: [   10.701353] type=1400 audit(1448113394.603:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=394 comm="apparmor_parser"
Nov 21 08:43:20 arcane-X555LB kernel: [   10.701426] type=1400 audit(1448113394.603:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=468 comm="apparmor_parser"
Nov 21 08:43:20 arcane-X555LB kernel: [   10.781312] uvcvideo: Found UVC 1.00 device USB Camera (0bda:57b5)
Nov 21 08:43:20 arcane-X555LB kernel: [   10.787276] input: USB Camera as /devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5:1.0/input/input13
Nov 21 08:43:20 arcane-X555LB kernel: [   10.787349] usbcore: registered new interface driver uvcvideo
Nov 21 08:43:20 arcane-X555LB kernel: [   10.787351] USB Video Class driver (1.1.1)
Nov 21 08:43:20 arcane-X555LB kernel: [   11.809848] nvidia: module license 'NVIDIA' taints kernel.
Nov 21 08:43:20 arcane-X555LB kernel: [   11.809851] Disabling lock debugging due to kernel taint
Nov 21 08:43:20 arcane-X555LB kernel: [   11.815963] [drm] Initialized nvidia-drm 0.0.0 20150116 for 0000:04:00.0 on minor 0
Nov 21 08:43:20 arcane-X555LB kernel: [   11.815969] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  346.96  Sun Aug 23 22:29:21 PDT 2015
Nov 21 08:43:20 arcane-X555LB kernel: [   12.523199] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro
Nov 21 08:43:20 arcane-X555LB kernel: [   13.008109] hda-intel 0000:00:03.0: no codecs initialized
Nov 21 08:43:20 arcane-X555LB kernel: [   13.008381] snd_hda_intel 0000:00:1b.0: irq 66 for MSI/MSI-X
Nov 21 08:43:20 arcane-X555LB kernel: [   13.102365] asus_wmi: Unknown key cf pressed
Nov 21 08:43:20 arcane-X555LB kernel: [   13.483851] SKU: Nid=0x1d sku_cfg=0x40469b05
Nov 21 08:43:20 arcane-X555LB kernel: [   13.483854] SKU: port_connectivity=0x1
Nov 21 08:43:20 arcane-X555LB kernel: [   13.483855] SKU: enable_pcbeep=0x0
Nov 21 08:43:20 arcane-X555LB kernel: [   13.483856] SKU: check_sum=0x00000006
Nov 21 08:43:20 arcane-X555LB kernel: [   13.483857] SKU: customization=0x0000009b
Nov 21 08:43:20 arcane-X555LB kernel: [   13.483858] SKU: external_amp=0x0
Nov 21 08:43:20 arcane-X555LB kernel: [   13.483859] SKU: platform_type=0x1
Nov 21 08:43:20 arcane-X555LB kernel: [   13.483860] SKU: swap=0x0
Nov 21 08:43:20 arcane-X555LB kernel: [   13.483861] SKU: override=0x1
Nov 21 08:43:20 arcane-X555LB kernel: [   13.484036] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
Nov 21 08:43:20 arcane-X555LB kernel: [   13.484038]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
Nov 21 08:43:20 arcane-X555LB kernel: [   13.484040]    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
Nov 21 08:43:20 arcane-X555LB kernel: [   13.484041]    mono: mono_out=0x0
Nov 21 08:43:20 arcane-X555LB kernel: [   13.484042]    inputs:
Nov 21 08:43:20 arcane-X555LB kernel: [   13.484043]      Mic=0x1b
Nov 21 08:43:20 arcane-X555LB kernel: [   13.484045] realtek: No valid SSID, checking pincfg 0x40469b05 for NID 0x1d
Nov 21 08:43:20 arcane-X555LB kernel: [   13.484046] realtek: Enabling init ASM_ID=0x9b05 CODEC_ID=10ec0233
Nov 21 08:43:20 arcane-X555LB kernel: [   13.490670] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
Nov 21 08:43:20 arcane-X555LB kernel: [   13.492970] [drm] Memory usable by graphics device = 2048M
Nov 21 08:43:20 arcane-X555LB kernel: [   13.492975] checking generic (b0000000 1e0000) vs hw (b0000000 10000000)
Nov 21 08:43:20 arcane-X555LB kernel: [   13.492977] fb: conflicting fb hw usage inteldrmfb vs EFI VGA - removing generic driver
Nov 21 08:43:20 arcane-X555LB kernel: [   13.493003] Console: switching to colour dummy device 80x25
Nov 21 08:43:20 arcane-X555LB kernel: [   13.544209] i915 0000:00:02.0: irq 67 for MSI/MSI-X
Nov 21 08:43:20 arcane-X555LB kernel: [   13.544219] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
Nov 21 08:43:20 arcane-X555LB kernel: [   13.544220] [drm] Driver supports precise vblank timestamp query.
Nov 21 08:43:20 arcane-X555LB kernel: [   13.596444] [drm:__gen6_gt_force_wake_mt_get] *ERROR* Timed out waiting for forcewake old ack to clear.
Nov 21 08:43:20 arcane-X555LB kernel: [   13.606914] fbcon: inteldrmfb (fb0) is primary device
Nov 21 08:43:20 arcane-X555LB kernel: [   15.191479] [drm:intel_pipe_config_compare] *ERROR* mismatch in ips_enabled (expected 1, found 0)
Nov 21 08:43:20 arcane-X555LB kernel: [   15.191480] ------------[ cut here ]------------
```


This is what I got out of the kernel logs - I believe it was within that time frame where the shut down occurred. It happened a few minutes after waking it from suspend.

---

### Post by mistcloud-misty on 2015-11-21
```
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293157]  [drm:intel_pipe_config_compare] *ERROR* mismatch in ips_enabled  (expected 1, found 0)
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293158] ------------[ cut here ]------------
Nov  21 08:33:42 arcane-X555LB kernel: [388794.293180] WARNING: CPU: 0 PID:  1210 at /home/apw/COD/linux/drivers/gpu/drm/i915/intel_display.c:9310  check_crtc_state+0x275/0x330 [i915]()
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293180] pipe state doesn't match!
Nov  21 08:33:42 arcane-X555LB kernel: [388794.293206] Modules linked in:  xt_recent xt_hl ip6t_rt nf_conntrack_ipv6 nf_defrag_ipv6 ipt_REJECT  xt_LOG xt_limit xt_tcpudp xt_addrtype nf_conntrack_ipv4 nf_defrag_ipv4  xt_conntrack ip6table_filter ip6_tables nf_conntrack_netbios_ns  nf_conntrack_broadcast nf_nat_ftp nf_nat nf_conntrack_ftp nf_conntrack  iptable_filter ip_tables x_tables bbswitch(OF) ctr ccm bnep rfcomm  bluetooth binfmt_misc nls_iso8859_1 nvidia(POF) snd_hda_codec_realtek  uvcvideo videobuf2_vmalloc videobuf2_memops rts5139(C) videobuf2_core  videodev x86_pkg_temp_thermal coretemp snd_hda_intel kvm_intel i915  snd_hda_codec kvm snd_hwdep snd_pcm arc4 mt7630e(OF) crct10dif_pclmul  snd_page_alloc snd_seq_midi snd_seq_midi_event crc32_pclmul snd_rawmidi  ghash_clmulni_intel mac80211 cfg80211 aesni_intel snd_seq drm_kms_helper  aes_x86_64 asus_nb_wmi lrw asus_wmi mxm_wmi sparse_keymap gf128mul  glue_helper snd_seq_device ablk_helper snd_timer cryptd eeprom_93cx6 drm  snd crc_ccitt joydev serio_raw soundcore mei_me mei acpi_pad video wmi  i2c_algo_bit mac_hid lpc_ich shpchp parport_pc ppdev lp parport psmouse  ahci r8169 libahci mii
Nov 21 08:33:42 arcane-X555LB kernel:  [388794.293224] CPU: 0 PID: 1210 Comm: Xorg Tainted: PF       WC O  3.13.11-03131107-generic #201409181736
Nov 21 08:33:42 arcane-X555LB  kernel: [388794.293225] Hardware name: ASUSTeK COMPUTER INC.  X555LB/X555LB, BIOS X555LB.408 07/07/2015
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293228]  000000000000245e ffff880251029638 ffffffff817471b4 0000000000000086
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293230]  ffff880251029688 ffff880251029678 ffffffff81069acc ffff8802510296a8
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293232]  ffff88024f2a9000 ffff880035ea9328 ffff880035ea9000 ffff88024f2a96e0
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293232] Call Trace:
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293237]  [<ffffffff817471b4>] dump_stack+0x46/0x58
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293241]  [<ffffffff81069acc>] warn_slowpath_common+0x8c/0xc0
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293243]  [<ffffffff81069bb6>] warn_slowpath_fmt+0x46/0x50
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293260]  [<ffffffffa04885a2>] ? intel_ddi_get_config+0x102/0x190 [i915]
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293273]  [<ffffffffa0472e55>] check_crtc_state+0x275/0x330 [i915]
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293287]  [<ffffffffa047ee15>] intel_modeset_check_state+0x65/0xa0 [i915]
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293299]  [<ffffffffa047ee75>] intel_set_mode+0x25/0x30 [i915]
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293311]  [<ffffffffa047f11d>] intel_crtc_set_config+0x29d/0x310 [i915]
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293324]  [<ffffffffa01259fc>] drm_mode_set_config_internal+0x5c/0xe0 [drm]
Nov  21 08:33:42 arcane-X555LB kernel: [388794.293329]   [<ffffffffa01a7e46>] drm_fb_helper_set_par+0x66/0xe0  [drm_kms_helper]
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293332]  [<ffffffff813d78a3>] fb_set_var+0x283/0x3a0
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293335]  [<ffffffff810a809b>] ? check_preempt_wakeup+0x14b/0x260
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293337]  [<ffffffff813e5484>] fbcon_blank+0x1e4/0x2d0
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293341]  [<ffffffff8147115e>] do_unblank_screen.part.18+0x9e/0x180
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293343]  [<ffffffff81471288>] do_unblank_screen+0x48/0x80
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293346]  [<ffffffff814664c5>] complete_change_console+0x65/0xf0
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293347]  [<ffffffff8146767c>] vt_ioctl+0x112c/0x11d0
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293351]  [<ffffffff8145abb8>] tty_ioctl+0x298/0x8f0
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293354]  [<ffffffff814a21d8>] ? dev_attr_store+0x18/0x30
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293357]  [<ffffffff8123df1a>] ? flush_write_buffer+0x9a/0x100
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293359]  [<ffffffff811daab5>] do_vfs_ioctl+0x75/0x2c0
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293362]  [<ffffffff816293c5>] ? __sys_recvmsg+0x75/0x90
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293363]  [<ffffffff811dad91>] SyS_ioctl+0x91/0xb0
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293366]  [<ffffffff8175c86d>] system_call_fastpath+0x1a/0x1f
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293367] ---[ end trace aee9a8b1c8add4f6 ]---
Nov 21 08:33:42 arcane-X555LB kernel: [388794.293524] Freezing user space processes ... (elapsed 0.001 seconds) done.
Nov 21 08:33:42 arcane-X555LB kernel: [388794.295120] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
Nov 21 08:33:42 arcane-X555LB kernel: [388794.296285] PM: Entering mem sleep
Nov 21 08:33:42 arcane-X555LB kernel: [388794.297018] Suspending console(s) (use no_console_suspend to debug)
Nov 21 08:33:42 arcane-X555LB kernel: [388794.297227] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Nov 21 08:33:42 arcane-X555LB kernel: [388794.297392] sd 0:0:0:0: [sda] Stopping disk
Nov 21 08:33:42 arcane-X555LB kernel: [388795.417751] PM: suspend of devices complete after 1120.925 msecs
Nov 21 08:33:42 arcane-X555LB kernel: [388795.432935] PM: late suspend of devices complete after 15.184 msecs
Nov 21 08:33:42 arcane-X555LB kernel: [388795.433113] pcieport 0000:00:1c.2: System wakeup enabled by ACPI
Nov 21 08:33:42 arcane-X555LB kernel: [388795.464887] xhci_hcd 0000:00:14.0: System wakeup enabled by ACPI
Nov 21 08:33:42 arcane-X555LB kernel: [388795.464945] PM: noirq suspend of devices complete after 32.017 msecs
Nov 21 08:33:42 arcane-X555LB kernel: [388795.465184] ACPI: Preparing to enter system sleep state S3
Nov 21 08:33:42 arcane-X555LB kernel: [388795.470626] PM: Saving platform NVS memory
Nov 21 08:33:42 arcane-X555LB kernel: [388795.483461] Disabling non-boot CPUs ...
Nov 21 08:33:42 arcane-X555LB kernel: [388795.484658] kvm: disabling virtualization on CPU1
Nov 21 08:33:42 arcane-X555LB kernel: [388795.584810] smpboot: CPU 1 is now offline
Nov 21 08:33:42 arcane-X555LB kernel: [388795.586198] kvm: disabling virtualization on CPU2
Nov 21 08:33:42 arcane-X555LB kernel: [388795.688774] smpboot: CPU 2 is now offline
Nov 21 08:33:42 arcane-X555LB kernel: [388795.689107] Broke affinity for irq 59
Nov 21 08:33:42 arcane-X555LB kernel: [388795.689108] Broke affinity for irq 60
Nov 21 08:33:42 arcane-X555LB kernel: [388795.689110] Broke affinity for irq 61
Nov 21 08:33:42 arcane-X555LB kernel: [388795.689112] Broke affinity for irq 62
Nov 21 08:33:42 arcane-X555LB kernel: [388795.689114] Broke affinity for irq 63
Nov 21 08:33:42 arcane-X555LB kernel: [388795.690119] kvm: disabling virtualization on CPU3
Nov 21 08:33:42 arcane-X555LB kernel: [388795.792746] smpboot: CPU 3 is now offline
Nov 21 08:33:42 arcane-X555LB kernel: [388795.795713] ACPI: Low-level resume complete
Nov 21 08:33:42 arcane-X555LB kernel: [388795.795785] PM: Restoring platform NVS memory
Nov 21 08:33:42 arcane-X555LB kernel: [388795.801624] Enabling non-boot CPUs ...
Nov 21 08:33:42 arcane-X555LB kernel: [388795.801674] x86: Booting SMP configuration:
Nov 21 08:33:42 arcane-X555LB kernel: [388795.801676] smpboot: Booting Node 0 Processor 1 APIC 0x2
Nov 21 08:33:42 arcane-X555LB kernel: [388795.814157] kvm: enabling virtualization on CPU1
Nov 21 08:33:42 arcane-X555LB kernel: [388795.816647] CPU1 is up
Nov 21 08:33:42 arcane-X555LB kernel: [388795.816667] smpboot: Booting Node 0 Processor 2 APIC 0x1
Nov 21 08:33:42 arcane-X555LB kernel: [388795.828817] kvm: enabling virtualization on CPU2
Nov 21 08:33:42 arcane-X555LB kernel: [388795.831168] CPU2 is up
Nov 21 08:33:42 arcane-X555LB kernel: [388795.831181] smpboot: Booting Node 0 Processor 3 APIC 0x3
Nov 21 08:33:42 arcane-X555LB kernel: [388795.843367] kvm: enabling virtualization on CPU3
Nov 21 08:33:42 arcane-X555LB kernel: [388795.845642] CPU3 is up
Nov 21 08:33:42 arcane-X555LB kernel: [388795.854877] ACPI: Waking up from system sleep state S3
Nov 21 08:33:42 arcane-X555LB kernel: [388795.913324] xhci_hcd 0000:00:14.0: System wakeup disabled by ACPI
Nov 21 08:33:42 arcane-X555LB kernel: [388795.993379] PM: noirq resume of devices complete after 95.883 msecs
Nov 21 08:33:42 arcane-X555LB kernel: [388795.993596] PM: early resume of devices complete after 0.197 msecs
Nov 21 08:33:42 arcane-X555LB kernel: [388795.993826] mei_me 0000:00:16.0: irq 65 for MSI/MSI-X
Nov 21 08:33:42 arcane-X555LB kernel: [388795.994028] pcieport 0000:00:1c.2: System wakeup disabled by ACPI
Nov 21 08:33:42 arcane-X555LB kernel: [388795.994236] snd_hda_intel 0000:00:1b.0: irq 67 for MSI/MSI-X
Nov  21 08:33:42 arcane-X555LB kernel: [388795.994399]  ==>MT76x0_WLAN_ChipOnOff(): OnOff:1 pAd->WlanFunCtrl.word =  0xffff0103, Reg-WlanFunCtrl=0xff000202
Nov 21 08:33:42 arcane-X555LB kernel: [388795.994400] Reset(1) WlanFunCtrl.word = 0xffff020e
Nov 21 08:33:42 arcane-X555LB kernel: [388795.994451] Reset(2) WlanFunCtrl.word = 0xffff0202
Nov 21 08:33:42 arcane-X555LB kernel: [388795.994503] WlanFunCtrl.word = 0xffff0203
Nov 21 08:33:42 arcane-X555LB kernel: [388795.994563] MACVersion = 0x76502000
Nov  21 08:33:42 arcane-X555LB kernel: [388795.994569] <==  MT76x0_WLAN_ChipOnOff():  pAd->WlanFunCtrl.word = 0xffff0203,  Reg->WlanFunCtrl=0xffff0f03!
Nov 21 08:33:42 arcane-X555LB kernel:  [388796.029191] [drm:__gen6_gt_force_wake_mt_get] *ERROR* Timed out  waiting for forcewake old ack to clear.
Nov 21 08:33:42 arcane-X555LB kernel: [388796.317474] usb 1-6: reset high-speed USB device number 5 using xhci_hcd
Nov 21 08:33:42 arcane-X555LB kernel: [388796.329166] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Nov  21 08:33:42 arcane-X555LB kernel: [388796.338167] xhci_hcd  0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep  ffff88020e8bca80
Nov 21 08:33:42 arcane-X555LB kernel:  [388796.338168] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called  with disabled ep ffff88020e8bcac0
Nov 21 08:33:42 arcane-X555LB  kernel: [388796.338169] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint  called with disabled ep ffff88020e8bcb00
Nov 21 08:33:42  arcane-X555LB kernel: [388796.338170] xhci_hcd 0000:00:14.0: xHCI  xhci_drop_endpoint called with disabled ep ffff880041441980
Nov 21  08:33:42 arcane-X555LB kernel: [388796.338171] xhci_hcd 0000:00:14.0:  xHCI xhci_drop_endpoint called with disabled ep ffff8800414419c0
Nov 21 08:33:42 arcane-X555LB kernel: [388796.339329] ata2.00: configured for UDMA/100
Nov 21 08:33:42 arcane-X555LB kernel: [388796.445509] usb 1-5: reset high-speed USB device number 2 using xhci_hcd
Nov  21 08:33:42 arcane-X555LB kernel: [388796.480347] xhci_hcd  0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep  ffff880036a64940
Nov 21 08:33:42 arcane-X555LB kernel: [388796.573313] usb 1-8: reset high-speed USB device number 4 using xhci_hcd
Nov  21 08:33:42 arcane-X555LB kernel: [388796.589181] xhci_hcd  0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep  ffff88024edc9000
Nov 21 08:33:42 arcane-X555LB kernel:  [388796.589183] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called  with disabled ep ffff88024edc9040
Nov 21 08:33:42 arcane-X555LB  kernel: [388796.589184] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint  called with disabled ep ffff88024edc9080
Nov 21 08:33:42  arcane-X555LB kernel: [388796.613096] [drm:intel_pipe_config_compare]  *ERROR* mismatch in ips_enabled (expected 1, found 0)
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613096] ------------[ cut here ]------------
Nov  21 08:33:42 arcane-X555LB kernel: [388796.613117] WARNING: CPU: 1 PID:  22958 at /home/apw/COD/linux/drivers/gpu/drm/i915/intel_display.c:9310  check_crtc_state+0x275/0x330 [i915]()
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613117] pipe state doesn't match!
Nov  21 08:33:42 arcane-X555LB kernel: [388796.613137] Modules linked in:  xt_recent xt_hl ip6t_rt nf_conntrack_ipv6 nf_defrag_ipv6 ipt_REJECT  xt_LOG xt_limit xt_tcpudp xt_addrtype nf_conntrack_ipv4 nf_defrag_ipv4  xt_conntrack ip6table_filter ip6_tables nf_conntrack_netbios_ns  nf_conntrack_broadcast nf_nat_ftp nf_nat nf_conntrack_ftp nf_conntrack  iptable_filter ip_tables x_tables bbswitch(OF) ctr ccm bnep rfcomm  bluetooth binfmt_misc nls_iso8859_1 nvidia(POF) snd_hda_codec_realtek  uvcvideo videobuf2_vmalloc videobuf2_memops rts5139(C) videobuf2_core  videodev x86_pkg_temp_thermal coretemp snd_hda_intel kvm_intel i915  snd_hda_codec kvm snd_hwdep snd_pcm arc4 mt7630e(OF) crct10dif_pclmul  snd_page_alloc snd_seq_midi snd_seq_midi_event crc32_pclmul snd_rawmidi  ghash_clmulni_intel mac80211 cfg80211 aesni_intel snd_seq drm_kms_helper  aes_x86_64 asus_nb_wmi lrw asus_wmi mxm_wmi sparse_keymap gf128mul  glue_helper snd_seq_device ablk_helper snd_timer cryptd eeprom_93cx6 drm  snd crc_ccitt joydev serio_raw soundcore mei_me mei acpi_pad video wmi  i2c_algo_bit mac_hid lpc_ich shpchp parport_pc ppdev lp parport psmouse  ahci r8169 libahci mii
Nov 21 08:33:42 arcane-X555LB kernel:  [388796.613152] CPU: 1 PID: 22958 Comm: kworker/u8:12 Tainted: PF        WC O 3.13.11-03131107-generic #201409181736
Nov 21 08:33:42  arcane-X555LB kernel: [388796.613153] Hardware name: ASUSTeK COMPUTER  INC. X555LB/X555LB, BIOS X555LB.408 07/07/2015
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613157] Workqueue: events_unbound async_run_entry_fn
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613159]  000000000000245e ffff880056365868 ffffffff817471b4 ffffffff81c4b698
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613160]  ffff8800563658b8 ffff8800563658a8 ffffffff81069acc ffff8800563658d8
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613162]  ffff88024f2a9000 ffff880035ea9328 ffff880035ea9000 ffff88024f2a96e0
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613162] Call Trace:
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613168]  [<ffffffff817471b4>] dump_stack+0x46/0x58
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613170]  [<ffffffff81069acc>] warn_slowpath_common+0x8c/0xc0
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613172]  [<ffffffff81069bb6>] warn_slowpath_fmt+0x46/0x50
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613186]  [<ffffffffa04885a2>] ? intel_ddi_get_config+0x102/0x190 [i915]
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613198]  [<ffffffffa0472e55>] check_crtc_state+0x275/0x330 [i915]
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613210]  [<ffffffffa047ee15>] intel_modeset_check_state+0x65/0xa0 [i915]
Nov  21 08:33:42 arcane-X555LB kernel: [388796.613223]   [<ffffffffa0480a3d>] intel_modeset_setup_hw_state+0x2cd/0x350  [i915]
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613229]  [<ffffffffa043c383>] __i915_drm_thaw+0x153/0x210 [i915]
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613232]  [<ffffffff813b4410>] ? pci_pm_thaw+0x90/0x90
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613237]  [<ffffffffa043cbeb>] i915_resume+0x2b/0x50 [i915]
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613240]  [<ffffffff813b4410>] ? pci_pm_thaw+0x90/0x90
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613245]  [<ffffffffa043cc26>] i915_pm_resume+0x16/0x20 [i915]
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613247]  [<ffffffff813b448e>] pci_pm_resume+0x7e/0xe0
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613249]  [<ffffffff814af996>] dpm_run_callback+0x56/0xa0
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613250]  [<ffffffff814b00de>] device_resume+0xde/0x210
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613251]  [<ffffffff814b0231>] async_resume+0x21/0x50
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613253]  [<ffffffff8109497b>] async_run_entry_fn+0x3b/0x140
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613255]  [<ffffffff8108647f>] process_one_work+0x17f/0x4c0
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613257]  [<ffffffff8108769b>] worker_thread+0x11b/0x3d0
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613259]  [<ffffffff81087580>] ? manage_workers.isra.21+0x190/0x190
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613260]  [<ffffffff8108e5e9>] kthread+0xc9/0xe0
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613261]  [<ffffffff8108e520>] ? flush_kthread_worker+0xb0/0xb0
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613263]  [<ffffffff8175c7bc>] ret_from_fork+0x7c/0xb0
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613265]  [<ffffffff8108e520>] ? flush_kthread_worker+0xb0/0xb0
Nov 21 08:33:42 arcane-X555LB kernel: [388796.613266] ---[ end trace aee9a8b1c8add4f7 ]---
Nov 21 08:33:42 arcane-X555LB kernel: [388798.736506] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Nov 21 08:33:42 arcane-X555LB kernel: [388798.739059] ata1.00: configured for UDMA/133
Nov 21 08:33:42 arcane-X555LB kernel: [388798.752522] sd 0:0:0:0: [sda] Starting disk
Nov 21 08:33:42 arcane-X555LB kernel: [388798.776243] PM: resume of devices complete after 2783.409 msecs
Nov 21 08:33:42 arcane-X555LB kernel: [388798.776493] PM: Finishing wakeup.
Nov 21 08:33:42 arcane-X555LB kernel: [388798.776494] Restarting tasks ... done.
Nov 21 08:33:42 arcane-X555LB kernel: [388798.781493] video LNXVIDEO:00: Restoring backlight state
Nov 21 08:33:42 arcane-X555LB kernel: [388798.781498] video LNXVIDEO:01: Restoring backlight state
Nov 21 08:33:42 arcane-X555LB kernel: [388799.270396] r8169 0000:02:00.0 eth0: link down
Nov 21 08:33:42 arcane-X555LB kernel: [388799.270476] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov 21 08:33:42 arcane-X555LB kernel: [388799.271152] ===>rt2x00lib_start
Nov  21 08:33:42 arcane-X555LB kernel: [388799.271170]  ==>MT76x0_WLAN_ChipOnOff(): OnOff:1 pAd->WlanFunCtrl.word =  0xffff0203, Reg-WlanFunCtrl=0xffff0103
Nov 21 08:33:42 arcane-X555LB kernel: [388799.271172] Reset(1) WlanFunCtrl.word = 0xffff010f
Nov 21 08:33:42 arcane-X555LB kernel: [388799.271223] Reset(2) WlanFunCtrl.word = 0xffff0103
Nov 21 08:33:42 arcane-X555LB kernel: [388799.271274] WlanFunCtrl.word = 0xffff0103
Nov 21 08:33:42 arcane-X555LB kernel: [388799.271326] MACVersion = 0x76502000
Nov  21 08:33:42 arcane-X555LB kernel: [388799.271333] <==  MT76x0_WLAN_ChipOnOff():  pAd->WlanFunCtrl.word = 0xffff0103,  Reg->WlanFunCtrl=0xffff0103!
Nov 21 08:33:42 arcane-X555LB kernel: [388799.271387] ASIC is ready
Nov 21 08:33:42 arcane-X555LB kernel: [388799.271399] FW Version:16.0.151 Build:370
Nov 21 08:33:42 arcane-X555LB kernel: [388799.271401] Build Time:201404211629____
Nov 21 08:33:42 arcane-X555LB kernel: [388799.271408] ILM Length = 334408(bytes)
Nov 21 08:33:42 arcane-X555LB kernel: [388799.271409] DLM Length = 47772(bytes)
Nov 21 08:33:42 arcane-X555LB kernel: [388799.343593] rt2800pci_write_firmware: COM_REG0(0x730) = 0x1
Nov 21 08:33:42 arcane-X555LB kernel: [388799.343600] rt2800_load_firmware: COM_REG0(0x730) = 0x1
Nov 21 08:33:42 arcane-X555LB kernel: [388799.350754] ===>rt2x00lib_enable_radio
Nov 21 08:33:42 arcane-X555LB kernel: [388799.350794] ===>rt2800_enable_radio: 
Nov 21 08:33:42 arcane-X555LB kernel: [388799.351116] reg FCE_PSE_CTRL =x0
Nov 21 08:33:42 arcane-X555LB kernel: [388799.351130] rt2800_init_bbp(): Init BBP Registers MT7630
Nov 21 08:33:42 arcane-X555LB kernel: [388799.352130] BBP version = f000f200
Nov 21 08:33:42 arcane-X555LB kernel: [388799.352132] rt2800_init_bbp(): Init BBP Registers MT7630
Nov 21 08:33:42 arcane-X555LB kernel: [388799.352171] rt2800_init_bbp(): Init BBP Registers MT7630 complete
Nov 21 08:33:42 arcane-X555LB kernel: [388799.352173] ==>rt2800lib_init_queues
Nov 21 08:33:42 arcane-X555LB kernel: [388799.352175] -->TX_RING: Base=0x0x000000000d160000, Cnt=64
Nov 21 08:33:42 arcane-X555LB kernel: [388799.352177] -->TX_RING: Base=0x0x00000000715ce000, Cnt=64
Nov 21 08:33:42 arcane-X555LB kernel: [388799.352179] -->TX_RING: Base=0x0x000000007ac03000, Cnt=64
Nov 21 08:33:42 arcane-X555LB kernel: [388799.352181] -->TX_RING: Base=0x0x000000008796a000, Cnt=64
Nov 21 08:33:42 arcane-X555LB kernel: [388799.352183] -->RX_RING: Base=0x0x0000000056326000, Cnt=128
Nov 21 08:33:42 arcane-X555LB kernel: [388799.352184] AsicInitTxRxRing
Nov 21 08:33:42 arcane-X555LB kernel: [388799.352186] -->TX_RING_CTRL: Base=0x35c9a000, Cnt=32!
Nov 21 08:33:42 arcane-X555LB kernel: [388799.352192] <===rt2800lib_init_queues
Nov 21 08:33:42 arcane-X555LB kernel: [388799.352193] MAC 40:b8:9a:76:8a:17 
Nov 21 08:33:42 arcane-X555LB kernel: [388799.352202] rt2800_enable_radio -7630 Dual antenna mode
Nov 21 08:33:42 arcane-X555LB kernel: [388799.364287] rt2800_init_rfcsr(): Init RF Registers MT7630
Nov 21 08:33:42 arcane-X555LB kernel: [388799.364686] rt2800_init_rfcsr: B0.R22 = 0x7d
Nov 21 08:33:42 arcane-X555LB kernel: [388799.364702] rt2800_init_rfcsr(): Init RF Registers MT7630 complete
Nov 21 08:33:42 arcane-X555LB kernel: [388799.384981] --> AsicCheckCommanFail2 Timeout Command = 2, CmdStatus= 0x0 
Nov 21 08:33:42 arcane-X555LB kernel: [388799.405229] --> AsicCheckCommanFail2 Timeout Command = 3, CmdStatus= 0x0 
Nov 21 08:33:42 arcane-X555LB kernel: [388799.405240] rtmp_bbp_set_rxpath(): rxpath=1, Set AGC1_R0=0x21400, agc_r0=0x21400
Nov 21 08:33:42 arcane-X555LB kernel: [388799.405244] rtmp_bbp_set_txdac(): txdac=0, Set txbe=0x0, txbe_r5=0x0
Nov 21 08:33:42 arcane-X555LB kernel: [388799.412277] set INT_MASK_CSR = 0xdff3ff3
Nov 21 08:33:42 arcane-X555LB kernel: [388799.412279] ==> RTMPEnableRxTx
Nov 21 08:33:42 arcane-X555LB kernel: [388799.412282] ==>  DMAIdle, GloCfg=0x50
Nov 21 08:33:42 arcane-X555LB kernel: [388799.412385] <== WRITE DMA offset 0x208 = 0x75
Nov 21 08:33:42 arcane-X555LB kernel: [388799.412386] <== RTMPEnableRxTx
Nov 21 08:33:42 arcane-X555LB kernel: [388799.412389] 0x1300 = 00064300
Nov 21 08:33:42 arcane-X555LB kernel: [388799.412391] rt2800pci_toggle_irq(1):Check if PDMA is idle!
Nov 21 08:33:42 arcane-X555LB kernel: [388799.412393] ==>  DMAIdle, GloCfg=0x75
Nov 21 08:33:42 arcane-X555LB kernel: [388799.412395] rt2800pci_toggle_irq(2):Check if PDMA is idle!
Nov 21 08:33:42 arcane-X555LB kernel: [388799.412397] ==>  DMAIdle, GloCfg=0x75
Nov 21 08:33:42 arcane-X555LB kernel: [388799.424354] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov 21 08:33:44 arcane-X555LB kernel: [388800.876759] wlan0: authenticate with 54:35:30:24:c5:ef
Nov 21 08:33:44 arcane-X555LB kernel: [388800.892171] wlan0: send auth to 54:35:30:24:c5:ef (try 1/3)
Nov 21 08:33:44 arcane-X555LB kernel: [388800.893656] wlan0: authenticated
Nov 21 08:33:44 arcane-X555LB kernel: [388800.895968] wlan0: associate with 54:35:30:24:c5:ef (try 1/3)
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899177] wlan0: RX AssocResp from 54:35:30:24:c5:ef (capab=0x411 status=0 aid=3)
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899194] ===>rt2800_sta_add:MT7630
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899210] ===>rt2800_sta_add:MT7630   wcid=33
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899213] Connect to AP MAC: 54:35:30:24:c5:ef WCID=33
Nov  21 08:33:44 arcane-X555LB kernel: [388800.899221] BtAFHCtl: COEX AFH  Start Ch = 0, AFH End Ch = 47, Channel = 1, CentralChannel = 1
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899223] SendAndesAFH: -->
Nov  21 08:33:44 arcane-X555LB kernel: [388800.899226] SendAndesAFH:  LinkStatus = 1, BW = 1, Channel = 1, BssHashID = 1, PktLength = 20
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899229] AsicSendCmdToAndes not need  Rsp!!!
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899232] CmdUnit->u.ANDES.CmdPayload: ffff88020a7476cc, len = 20
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899234] 0x0000 : 03 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899248] 0x0010 : 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899254] AsicSendCmdToAndes: ffff88022eae9f60, len = 24
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899256] 0x0000 : 14 00 10 51 03 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899269] 0x0010 : 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899277] Buf: ffff88022eae9f60, len = 24
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899279] 0x0000 : 14 00 10 51 03 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899292] 0x0010 : 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899301] pPacket->data: ffff880252296f80, len = 20
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899303] 0x0000 : 03 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899315] 0x0010 : 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899322] PCIKickOutCmd (TxCpuIdx = 1)
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899324] SendAndesAFH: <--
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899326] SendAndesWLANStatus: -->
Nov  21 08:33:44 arcane-X555LB kernel: [388800.899330] SendAndesWLANStatus:  CoexOperation = 4, WlanStatus = 15, PrivilegeTime = 0, BssHashID = 1,  PktLength = 16
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899332] ==>INT_SOURCE_CSR_7630_HCCA_DMA_DONE
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899335] AsicSendCmdToAndes not need  Rsp!!!
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899338] CmdUnit->u.ANDES.CmdPayload: ffff88020a7476c0, len = 16
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899340] 0x0000 : 04 00 00 00 15 00 00 00 00 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899352] 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899355] AsicSendCmdToAndes: ffff88022eae9f60, len = 20
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899356] 0x0000 : 10 00 10 51 04 00 00 00 15 00 00 00 00 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899369] 0x0010 : 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899374] Buf: ffff88022eae9f60, len = 20
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899376] 0x0000 : 10 00 10 51 04 00 00 00 15 00 00 00 00 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899394] 0x0010 : 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899403] pPacket->data: ffff880252297140, len = 16
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899406] 0x0000 : 04 00 00 00 15 00 00 00 00 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899424] 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899428] PCIKickOutCmd (TxCpuIdx = 2)
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899437] ==>INT_SOURCE_CSR_7630_HCCA_DMA_DONE
Nov 21 08:33:44 arcane-X555LB kernel: [388800.899666] ieee80211 phy0: rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840
Nov  21 08:33:44 arcane-X555LB kernel: [388800.904896] BtAFHCtl: COEX AFH  Start Ch = 0, AFH End Ch = 47, Channel = 1, CentralChannel = 1
Nov 21 08:33:44 arcane-X555LB kernel: [388800.904902] SendAndesAFH: -->
Nov  21 08:33:44 arcane-X555LB kernel: [388800.904905] SendAndesAFH:  LinkStatus = 1, BW = 1, Channel = 1, BssHashID = 1, PktLength = 20
Nov 21 08:33:44 arcane-X555LB kernel: [388800.904909] AsicSendCmdToAndes not need  Rsp!!!
Nov 21 08:33:44 arcane-X555LB kernel: [388800.904912] CmdUnit->u.ANDES.CmdPayload: ffff88020a7476cc, len = 20
Nov 21 08:33:44 arcane-X555LB kernel: [388800.904915] 0x0000 : 03 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.904929] 0x0010 : 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.904935] AsicSendCmdToAndes: ffff88022eae9f60, len = 24
Nov 21 08:33:44 arcane-X555LB kernel: [388800.904937] 0x0000 : 14 00 10 51 03 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.904950] 0x0010 : 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.904958] Buf: ffff88022eae9f60, len = 24
Nov 21 08:33:44 arcane-X555LB kernel: [388800.904960] 0x0000 : 14 00 10 51 03 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.904973] 0x0010 : 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.904982] pPacket->data: ffff880252297300, len = 20
Nov 21 08:33:44 arcane-X555LB kernel: [388800.904984] 0x0000 : 03 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.904996] 0x0010 : 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388800.905003] PCIKickOutCmd (TxCpuIdx = 3)
Nov 21 08:33:44 arcane-X555LB kernel: [388800.905006] SendAndesAFH: <--
Nov 21 08:33:44 arcane-X555LB kernel: [388800.905037] ==>INT_SOURCE_CSR_7630_HCCA_DMA_DONE
Nov 21 08:33:44 arcane-X555LB kernel: [388800.910045] wlan0: associated
Nov 21 08:33:44 arcane-X555LB kernel: [388800.910067] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Nov 21 08:33:44 arcane-X555LB kernel: [388800.957304] wlan0: deauthenticating from 54:35:30:24:c5:ef by local choice (reason=2)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.003935] ===>rt2800_sta_remove:MT7630
Nov  21 08:33:44 arcane-X555LB kernel: [388801.094121] BtAFHCtl: COEX AFH  Start Ch = 0, AFH End Ch = 0, Channel = 1, CentralChannel = 1
Nov 21 08:33:44 arcane-X555LB kernel: [388801.094124] SendAndesAFH: -->
Nov  21 08:33:44 arcane-X555LB kernel: [388801.094125] SendAndesAFH:  LinkStatus = 2, BW = 1, Channel = 1, BssHashID = 1, PktLength = 20
Nov 21 08:33:44 arcane-X555LB kernel: [388801.094127] AsicSendCmdToAndes not need  Rsp!!!
Nov 21 08:33:44 arcane-X555LB kernel: [388801.094128] CmdUnit->u.ANDES.CmdPayload: ffff88025218d6d4, len = 20
Nov 21 08:33:44 arcane-X555LB kernel: [388801.094129] 0x0000 : 03 00 00 00 02 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.094135] 0x0010 : 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.094137] AsicSendCmdToAndes: ffff880036a82f40, len = 24
Nov 21 08:33:44 arcane-X555LB kernel: [388801.094138] 0x0000 : 14 00 10 51 03 00 00 00 02 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.094142] 0x0010 : 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.094145] Buf: ffff880036a82f40, len = 24
Nov 21 08:33:44 arcane-X555LB kernel: [388801.094146] 0x0000 : 14 00 10 51 03 00 00 00 02 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.094151] 0x0010 : 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.094154] pPacket->data: ffff8801631d6700, len = 20
Nov 21 08:33:44 arcane-X555LB kernel: [388801.094155] 0x0000 : 03 00 00 00 02 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.094160] 0x0010 : 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.094162] PCIKickOutCmd (TxCpuIdx = 4)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.094163] SendAndesAFH: <--
Nov 21 08:33:44 arcane-X555LB kernel: [388801.094172] ==>INT_SOURCE_CSR_7630_HCCA_DMA_DONE
Nov 21 08:33:44 arcane-X555LB kernel: [388801.099126] ===>rt2800_sta_remove:MT7630   0x80100 = 0x0
Nov 21 08:33:44 arcane-X555LB kernel: [388801.099127] ===>rt2800_sta_remove:MT7630   0x80100 = 0x0
Nov 21 08:33:44 arcane-X555LB kernel: [388801.107918] cfg80211: Calling CRDA to update world regulatory domain
Nov 21 08:33:44 arcane-X555LB kernel: [388801.108071] wlan0: authenticate with 54:35:30:24:c5:ef
Nov 21 08:33:44 arcane-X555LB kernel: [388801.116026] wlan0: send auth to 54:35:30:24:c5:ef (try 1/3)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.116354] cfg80211: World regulatory domain updated:
Nov  21 08:33:44 arcane-X555LB kernel: [388801.116361] cfg80211:    (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.116366] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.116370] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.116374] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.116377] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.116380] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.116404] cfg80211: Calling CRDA for country: US
Nov 21 08:33:44 arcane-X555LB kernel: [388801.117603] wlan0: authenticated
Nov 21 08:33:44 arcane-X555LB kernel: [388801.120003] wlan0: associate with 54:35:30:24:c5:ef (try 1/3)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.122788] cfg80211: Regulatory domain changed to country: US
Nov  21 08:33:44 arcane-X555LB kernel: [388801.122796] cfg80211:    (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.122801] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.122805] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.122809] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.122812] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.122815] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.122819] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.122822] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123193] wlan0: RX AssocResp from 54:35:30:24:c5:ef (capab=0x411 status=0 aid=3)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123217] ===>rt2800_sta_add:MT7630
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123237] ===>rt2800_sta_add:MT7630   wcid=33
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123243] Connect to AP MAC: 54:35:30:24:c5:ef WCID=33
Nov  21 08:33:44 arcane-X555LB kernel: [388801.123254] BtAFHCtl: COEX AFH  Start Ch = 0, AFH End Ch = 47, Channel = 1, CentralChannel = 1
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123259] SendAndesAFH: -->
Nov  21 08:33:44 arcane-X555LB kernel: [388801.123264] SendAndesAFH:  LinkStatus = 1, BW = 1, Channel = 1, BssHashID = 1, PktLength = 20
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123269] AsicSendCmdToAndes not need  Rsp!!!
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123275] CmdUnit->u.ANDES.CmdPayload: ffff88020a7476cc, len = 20
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123279] 0x0000 : 03 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123306] 0x0010 : 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123314] AsicSendCmdToAndes: ffff880036a82500, len = 24
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123316] 0x0000 : 14 00 10 51 03 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123333] 0x0010 : 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123343] Buf: ffff880036a82500, len = 24
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123345] 0x0000 : 14 00 10 51 03 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123361] 0x0010 : 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123372] pPacket->data: ffff8801631d6a80, len = 20
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123375] 0x0000 : 03 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123390] 0x0010 : 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123398] PCIKickOutCmd (TxCpuIdx = 5)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123401] SendAndesAFH: <--
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123404] SendAndesWLANStatus: -->
Nov  21 08:33:44 arcane-X555LB kernel: [388801.123410] SendAndesWLANStatus:  CoexOperation = 4, WlanStatus = 15, PrivilegeTime = 0, BssHashID = 1,  PktLength = 16
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123411] ==>INT_SOURCE_CSR_7630_HCCA_DMA_DONE
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123417] AsicSendCmdToAndes not need  Rsp!!!
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123421] CmdUnit->u.ANDES.CmdPayload: ffff88020a7476c0, len = 16
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123424] 0x0000 : 04 00 00 00 15 00 00 00 00 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123443] 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123446] AsicSendCmdToAndes: ffff880036a82500, len = 20
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123448] 0x0000 : 10 00 10 51 04 00 00 00 15 00 00 00 00 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123464] 0x0010 : 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123471] Buf: ffff880036a82500, len = 20
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123473] 0x0000 : 10 00 10 51 04 00 00 00 15 00 00 00 00 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123489] 0x0010 : 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123496] pPacket->data: ffff8801631d6c40, len = 16
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123498] 0x0000 : 04 00 00 00 15 00 00 00 00 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123514] 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123517] PCIKickOutCmd (TxCpuIdx = 6)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123527] ==>INT_SOURCE_CSR_7630_HCCA_DMA_DONE
Nov 21 08:33:44 arcane-X555LB kernel: [388801.123708] ieee80211 phy0: rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840
Nov  21 08:33:44 arcane-X555LB kernel: [388801.128990] BtAFHCtl: COEX AFH  Start Ch = 0, AFH End Ch = 47, Channel = 1, CentralChannel = 1
Nov 21 08:33:44 arcane-X555LB kernel: [388801.128993] SendAndesAFH: -->
Nov  21 08:33:44 arcane-X555LB kernel: [388801.128995] SendAndesAFH:  LinkStatus = 1, BW = 1, Channel = 1, BssHashID = 1, PktLength = 20
Nov 21 08:33:44 arcane-X555LB kernel: [388801.128996] AsicSendCmdToAndes not need  Rsp!!!
Nov 21 08:33:44 arcane-X555LB kernel: [388801.128998] CmdUnit->u.ANDES.CmdPayload: ffff88020a7476cc, len = 20
Nov 21 08:33:44 arcane-X555LB kernel: [388801.128999] 0x0000 : 03 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.129006] 0x0010 : 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.129009] AsicSendCmdToAndes: ffff880036a82500, len = 24
Nov 21 08:33:44 arcane-X555LB kernel: [388801.129010] 0x0000 : 14 00 10 51 03 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.129016] 0x0010 : 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.129020] Buf: ffff880036a82500, len = 24
Nov 21 08:33:44 arcane-X555LB kernel: [388801.129021] 0x0000 : 14 00 10 51 03 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.129027] 0x0010 : 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.129032] pPacket->data: ffff8801631d6e00, len = 20
Nov 21 08:33:44 arcane-X555LB kernel: [388801.129033] 0x0000 : 03 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.129039] 0x0010 : 01 00 00 00 
Nov 21 08:33:44 arcane-X555LB kernel: [388801.129042] PCIKickOutCmd (TxCpuIdx = 7)
Nov 21 08:33:44 arcane-X555LB kernel: [388801.129044] SendAndesAFH: <--
Nov 21 08:33:44 arcane-X555LB kernel: [388801.129054] ==>INT_SOURCE_CSR_7630_HCCA_DMA_DONE
Nov 21 08:33:44 arcane-X555LB kernel: [388801.134069] wlan0: associated
Nov  21 08:33:57 arcane-X555LB kernel: [388814.346843] [UFW BLOCK] IN=wlan0  OUT= MAC=40:b8:9a:76:8a:17:6c:71:d9:70:19:23:08:00 SRC=192.168.0.2  DST=192.168.0.17 LEN=56 TOS=0x00 PREC=0x00 TTL=128 ID=13280 PROTO=UDP  SPT=53949 DPT=2054 LEN=36 
Nov 21 08:33:57 arcane-X555LB kernel:  [388815.163511] [UFW BLOCK] IN=wlan0 OUT=  MAC=01:00:5e:00:00:01:48:5a:b6:f8:10:cd:08:00 SRC=192.168.0.1  DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
Nov 21  08:33:57 arcane-X555LB kernel: [388815.164523] [UFW BLOCK] IN=wlan0 OUT=  MAC=01:00:5e:00:00:01:48:5a:b6:f8:10:cd:08:00 SRC=192.168.0.1  DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
Nov 21  08:33:57 arcane-X555LB kernel: [388815.165396] [UFW BLOCK] IN=wlan0 OUT=  MAC=01:00:5e:00:00:01:48:5a:b6:f8:10:cd:08:00 SRC=192.168.26.1  DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
Nov 21  08:33:57 arcane-X555LB kernel: [388815.166471] [UFW BLOCK] IN=wlan0 OUT=  MAC=01:00:5e:00:00:01:48:5a:b6:f8:10:cd:08:00 SRC=192.168.26.1  DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
Nov 21  08:33:57 arcane-X555LB kernel: [388815.167374] [UFW BLOCK] IN=wlan0 OUT=  MAC=01:00:5e:00:00:01:48:5a:b6:f8:10:cd:08:00 SRC=192.168.27.1  DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
Nov 21  08:33:57 arcane-X555LB kernel: [388815.171923] [UFW BLOCK] IN=wlan0 OUT=  MAC=33:33:00:00:00:01:48:5a:b6:f8:10:cd:86:dd  SRC=fe80:0000:0000:0000:4a5a:b6ff:fef8:10cd  DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=76 TC=0 HOPLIMIT=1  FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
Nov 21 08:35:14 arcane-X555LB  kernel: [388892.249469] [UFW BLOCK] IN=wlan0 OUT=  MAC=40:b8:9a:76:8a:17:6c:71:d9:70:19:23:08:00 SRC=192.168.0.2  DST=192.168.0.17 LEN=56 TOS=0x00 PREC=0x00 TTL=128 ID=13310 PROTO=UDP  SPT=61464 DPT=2054 LEN=36 
Nov 21 08:36:03 arcane-X555LB kernel:  [388941.118241] [UFW BLOCK] IN=wlan0 OUT=  MAC=01:00:5e:00:00:01:48:5a:b6:f8:10:cd:08:00 SRC=192.168.0.1  DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
Nov 21  08:36:03 arcane-X555LB kernel: [388941.119275] [UFW BLOCK] IN=wlan0 OUT=  MAC=01:00:5e:00:00:01:48:5a:b6:f8:10:cd:08:00 SRC=192.168.0.1  DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
Nov 21  08:36:03 arcane-X555LB kernel: [388941.120221] [UFW BLOCK] IN=wlan0 OUT=  MAC=01:00:5e:00:00:01:48:5a:b6:f8:10:cd:08:00 SRC=192.168.26.1  DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
Nov 21  08:36:03 arcane-X555LB kernel: [388941.121353] [UFW BLOCK] IN=wlan0 OUT=  MAC=01:00:5e:00:00:01:48:5a:b6:f8:10:cd:08:00 SRC=192.168.26.1  DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
Nov 21  08:36:03 arcane-X555LB kernel: [388941.122370] [UFW BLOCK] IN=wlan0 OUT=  MAC=01:00:5e:00:00:01:48:5a:b6:f8:10:cd:08:00 SRC=192.168.27.1  DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
Nov 21  08:36:03 arcane-X555LB kernel: [388941.126592] [UFW BLOCK] IN=wlan0 OUT=  MAC=33:33:00:00:00:01:48:5a:b6:f8:10:cd:86:dd  SRC=fe80:0000:0000:0000:4a5a:b6ff:fef8:10cd  DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=76 TC=0 HOPLIMIT=1  FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
Nov 21 08:37:15 arcane-X555LB  kernel: [389012.234485] [UFW BLOCK] IN=wlan0 OUT=  MAC=40:b8:9a:76:8a:17:6c:71:d9:70:19:23:08:00 SRC=192.168.0.2  DST=192.168.0.17 LEN=56 TOS=0x00 PREC=0x00 TTL=128 ID=13346 PROTO=UDP  SPT=59166 DPT=2054 LEN=36 
Nov 21 08:38:09 arcane-X555LB kernel:  [389067.103309] [UFW BLOCK] IN=wlan0 OUT=  MAC=01:00:5e:00:00:01:48:5a:b6:f8:10:cd:08:00 SRC=192.168.0.1  DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
Nov 21  08:38:09 arcane-X555LB kernel: [389067.104283] [UFW BLOCK] IN=wlan0 OUT=  MAC=01:00:5e:00:00:01:48:5a:b6:f8:10:cd:08:00 SRC=192.168.0.1  DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
Nov 21  08:38:09 arcane-X555LB kernel: [389067.105205] [UFW BLOCK] IN=wlan0 OUT=  MAC=01:00:5e:00:00:01:48:5a:b6:f8:10:cd:08:00 SRC=192.168.26.1  DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
Nov 21  08:38:09 arcane-X555LB kernel: [389067.106247] [UFW BLOCK] IN=wlan0 OUT=  MAC=01:00:5e:00:00:01:48:5a:b6:f8:10:cd:08:00 SRC=192.168.26.1  DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
Nov 21  08:38:09 arcane-X555LB kernel: [389067.107078] [UFW BLOCK] IN=wlan0 OUT=  MAC=01:00:5e:00:00:01:48:5a:b6:f8:10:cd:08:00 SRC=192.168.27.1  DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
Nov 21  08:38:09 arcane-X555LB kernel: [389067.111337] [UFW BLOCK] IN=wlan0 OUT=  MAC=33:33:00:00:00:01:48:5a:b6:f8:10:cd:86:dd  SRC=fe80:0000:0000:0000:4a5a:b6ff:fef8:10cd  DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=76 TC=0 HOPLIMIT=1  FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
Nov 21 08:38:42 arcane-X555LB  kernel: [389099.704277] type=1400 audit(1448113122.493:86):  apparmor="STATUS" operation="profile_replace"  name="/usr/lib/cups/backend/cups-pdf" pid=24159 comm="apparmor_parser"
Nov  21 08:38:42 arcane-X555LB kernel: [389099.704285] type=1400  audit(1448113122.493:87): apparmor="STATUS" operation="profile_replace"  name="/usr/sbin/cupsd" pid=24159 comm="apparmor_parser"
Nov 21  08:38:42 arcane-X555LB kernel: [389099.704749] type=1400  audit(1448113122.493:88): apparmor="STATUS" operation="profile_replace"  name="/usr/sbin/cupsd" pid=24159 comm="apparmor_parser"
Nov 21 08:38:59 arcane-X555LB kernel: [389116.925150] ===>rt2800_sta_remove:MT7630
Nov  21 08:38:59 arcane-X555LB kernel: [389117.018204] BtAFHCtl: COEX AFH  Start Ch = 0, AFH End Ch = 0, Channel = 1, CentralChannel = 1
Nov 21 08:38:59 arcane-X555LB kernel: [389117.018207] SendAndesAFH: -->
Nov  21 08:38:59 arcane-X555LB kernel: [389117.018208] SendAndesAFH:  LinkStatus = 2, BW = 1, Channel = 1, BssHashID = 1, PktLength = 20
Nov 21 08:38:59 arcane-X555LB kernel: [389117.018210] AsicSendCmdToAndes not need  Rsp!!!
Nov 21 08:38:59 arcane-X555LB kernel: [389117.018211] CmdUnit->u.ANDES.CmdPayload: ffff88022b3b9b04, len = 20
Nov 21 08:38:59 arcane-X555LB kernel: [389117.018212] 0x0000 : 03 00 00 00 02 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:38:59 arcane-X555LB kernel: [389117.018217] 0x0010 : 01 00 00 00 
Nov 21 08:38:59 arcane-X555LB kernel: [389117.018220] AsicSendCmdToAndes: ffff88005612eee0, len = 24
Nov 21 08:38:59 arcane-X555LB kernel: [389117.018220] 0x0000 : 14 00 10 51 03 00 00 00 02 00 00 00 01 00 00 00 
Nov 21 08:38:59 arcane-X555LB kernel: [389117.018225] 0x0010 : 01 00 00 00 01 00 00 00 
Nov 21 08:38:59 arcane-X555LB kernel: [389117.018228] Buf: ffff88005612eee0, len = 24
Nov 21 08:38:59 arcane-X555LB kernel: [389117.018229] 0x0000 : 14 00 10 51 03 00 00 00 02 00 00 00 01 00 00 00 
Nov 21 08:38:59 arcane-X555LB kernel: [389117.018234] 0x0010 : 01 00 00 00 01 00 00 00 
Nov 21 08:38:59 arcane-X555LB kernel: [389117.018237] pPacket->data: ffff880252291a40, len = 20
Nov 21 08:38:59 arcane-X555LB kernel: [389117.018238] 0x0000 : 03 00 00 00 02 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:38:59 arcane-X555LB kernel: [389117.018242] 0x0010 : 01 00 00 00 
Nov 21 08:38:59 arcane-X555LB kernel: [389117.018245] PCIKickOutCmd (TxCpuIdx = 8)
Nov 21 08:38:59 arcane-X555LB kernel: [389117.018246] SendAndesAFH: <--
Nov 21 08:38:59 arcane-X555LB kernel: [389117.018273] ==>INT_SOURCE_CSR_7630_HCCA_DMA_DONE
Nov 21 08:38:59 arcane-X555LB kernel: [389117.023210] ===>rt2800_sta_remove:MT7630   0x80100 = 0x0
Nov 21 08:38:59 arcane-X555LB kernel: [389117.023212] ===>rt2800_sta_remove:MT7630   0x80100 = 0x0
Nov 21 08:38:59 arcane-X555LB kernel: [389117.045273] cfg80211: Calling CRDA to update world regulatory domain
Nov 21 08:38:59 arcane-X555LB kernel: [389117.051072] cfg80211: World regulatory domain updated:
Nov  21 08:38:59 arcane-X555LB kernel: [389117.051080] cfg80211:    (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov 21 08:38:59 arcane-X555LB kernel: [389117.051086] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:38:59 arcane-X555LB kernel: [389117.051091] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:38:59 arcane-X555LB kernel: [389117.051095] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:38:59 arcane-X555LB kernel: [389117.051099] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:38:59 arcane-X555LB kernel: [389117.051103] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:38:59 arcane-X555LB kernel: [389117.051516] cfg80211: Calling CRDA for country: US
Nov 21 08:38:59 arcane-X555LB kernel: [389117.057210] cfg80211: Regulatory domain changed to country: US
Nov  21 08:38:59 arcane-X555LB kernel: [389117.057214] cfg80211:    (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov 21 08:38:59 arcane-X555LB kernel: [389117.057215] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Nov 21 08:38:59 arcane-X555LB kernel: [389117.057217] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
Nov 21 08:38:59 arcane-X555LB kernel: [389117.057219] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:38:59 arcane-X555LB kernel: [389117.057220] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:38:59 arcane-X555LB kernel: [389117.057222] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:38:59 arcane-X555LB kernel: [389117.057223] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
Nov 21 08:38:59 arcane-X555LB kernel: [389117.057225] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
Nov 21 08:39:00 arcane-X555LB kernel: [389117.833571] wlan0: authenticate with 54:35:30:24:c5:ef
Nov 21 08:39:00 arcane-X555LB kernel: [389117.848910] wlan0: send auth to 54:35:30:24:c5:ef (try 1/3)
Nov 21 08:39:00 arcane-X555LB kernel: [389117.868413] wlan0: send auth to 54:35:30:24:c5:ef (try 2/3)
Nov 21 08:39:00 arcane-X555LB kernel: [389117.903253] wlan0: authenticated
Nov 21 08:39:00 arcane-X555LB kernel: [389117.904787] wlan0: associate with 54:35:30:24:c5:ef (try 1/3)
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908015] wlan0: RX AssocResp from 54:35:30:24:c5:ef (capab=0x411 status=0 aid=3)
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908036] ===>rt2800_sta_add:MT7630
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908053] ===>rt2800_sta_add:MT7630   wcid=33
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908057] Connect to AP MAC: 54:35:30:24:c5:ef WCID=33
Nov  21 08:39:00 arcane-X555LB kernel: [389117.908066] BtAFHCtl: COEX AFH  Start Ch = 0, AFH End Ch = 47, Channel = 1, CentralChannel = 1
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908069] SendAndesAFH: -->
Nov  21 08:39:00 arcane-X555LB kernel: [389117.908073] SendAndesAFH:  LinkStatus = 1, BW = 1, Channel = 1, BssHashID = 1, PktLength = 20
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908076] AsicSendCmdToAndes not need  Rsp!!!
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908080] CmdUnit->u.ANDES.CmdPayload: ffff88022b3b96cc, len = 20
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908083] 0x0000 : 03 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908101] 0x0010 : 01 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908108] AsicSendCmdToAndes: ffff88005612e160, len = 24
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908111] 0x0000 : 14 00 10 51 03 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908127] 0x0010 : 01 00 00 00 01 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908138] Buf: ffff88005612e160, len = 24
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908140] 0x0000 : 14 00 10 51 03 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908156] 0x0010 : 01 00 00 00 01 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908168] pPacket->data: ffff880252292b40, len = 20
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908170] 0x0000 : 03 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908185] 0x0010 : 01 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908193] PCIKickOutCmd (TxCpuIdx = 9)
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908196] SendAndesAFH: <--
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908199] SendAndesWLANStatus: -->
Nov  21 08:39:00 arcane-X555LB kernel: [389117.908203] SendAndesWLANStatus:  CoexOperation = 4, WlanStatus = 15, PrivilegeTime = 0, BssHashID = 1,  PktLength = 16
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908205] AsicSendCmdToAndes not need  Rsp!!!
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908208] CmdUnit->u.ANDES.CmdPayload: ffff88022b3b96c0, len = 16
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908210] 0x0000 : 04 00 00 00 15 00 00 00 00 00 00 00 01 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908226] 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908230] ==>INT_SOURCE_CSR_7630_HCCA_DMA_DONE
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908237] AsicSendCmdToAndes: ffff88005612e160, len = 20
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908240] 0x0000 : 10 00 10 51 04 00 00 00 15 00 00 00 00 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908258] 0x0010 : 01 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908265] Buf: ffff88005612e160, len = 20
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908267] 0x0000 : 10 00 10 51 04 00 00 00 15 00 00 00 00 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908336] 0x0010 : 01 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908359] pPacket->data: ffff880252292d00, len = 16
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908361] 0x0000 : 04 00 00 00 15 00 00 00 00 00 00 00 01 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908377] 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908380] PCIKickOutCmd (TxCpuIdx = 10)
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908390] ==>INT_SOURCE_CSR_7630_HCCA_DMA_DONE
Nov 21 08:39:00 arcane-X555LB kernel: [389117.908590] ieee80211 phy0: rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840
Nov  21 08:39:00 arcane-X555LB kernel: [389117.913847] BtAFHCtl: COEX AFH  Start Ch = 0, AFH End Ch = 47, Channel = 1, CentralChannel = 1
Nov 21 08:39:00 arcane-X555LB kernel: [389117.913854] SendAndesAFH: -->
Nov  21 08:39:00 arcane-X555LB kernel: [389117.913859] SendAndesAFH:  LinkStatus = 1, BW = 1, Channel = 1, BssHashID = 1, PktLength = 20
Nov 21 08:39:00 arcane-X555LB kernel: [389117.913864] AsicSendCmdToAndes not need  Rsp!!!
Nov 21 08:39:00 arcane-X555LB kernel: [389117.913869] CmdUnit->u.ANDES.CmdPayload: ffff88022b3b96cc, len = 20
Nov 21 08:39:00 arcane-X555LB kernel: [389117.913872] 0x0000 : 03 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.913888] 0x0010 : 01 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.913895] AsicSendCmdToAndes: ffff88005612ee80, len = 24
Nov 21 08:39:00 arcane-X555LB kernel: [389117.913896] 0x0000 : 14 00 10 51 03 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.913911] 0x0010 : 01 00 00 00 01 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.913919] Buf: ffff88005612ee80, len = 24
Nov 21 08:39:00 arcane-X555LB kernel: [389117.913921] 0x0000 : 14 00 10 51 03 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.913936] 0x0010 : 01 00 00 00 01 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.913945] pPacket->data: ffff880252292ec0, len = 20
Nov 21 08:39:00 arcane-X555LB kernel: [389117.913947] 0x0000 : 03 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.913961] 0x0010 : 01 00 00 00 
Nov 21 08:39:00 arcane-X555LB kernel: [389117.913968] PCIKickOutCmd (TxCpuIdx = 11)
Nov 21 08:39:00 arcane-X555LB kernel: [389117.913970] SendAndesAFH: <--
Nov 21 08:39:00 arcane-X555LB kernel: [389117.914003] ==>INT_SOURCE_CSR_7630_HCCA_DMA_DONE
Nov 21 08:39:00 arcane-X555LB kernel: [389117.919001] wlan0: associated
Nov  21 08:39:15 arcane-X555LB kernel: [389132.313424] [UFW BLOCK] IN=wlan0  OUT= MAC=40:b8:9a:76:8a:17:6c:71:d9:70:19:23:08:00 SRC=192.168.0.2  DST=192.168.0.17 LEN=56 TOS=0x00 PREC=0x00 TTL=128 ID=13377 PROTO=UDP  SPT=58664 DPT=2054 LEN=36 
Nov 21 08:39:29 arcane-X555LB kernel:  [389146.343019] [UFW BLOCK] IN=wlan0 OUT=  MAC=40:b8:9a:76:8a:17:48:5a:b6:f8:10:cd:08:00 SRC=69.172.216.111  DST=192.168.0.17 LEN=83 TOS=0x00 PREC=0x00 TTL=50 ID=50629 DF PROTO=TCP  SPT=443 DPT=57590 WINDOW=33 RES=0x00 ACK PSH URGP=0 
Nov 21 08:39:29  arcane-X555LB kernel: [389146.344252] [UFW BLOCK] IN=wlan0 OUT=  MAC=40:b8:9a:76:8a:17:48:5a:b6:f8:10:cd:08:00 SRC=69.172.216.111  DST=192.168.0.17 LEN=83 TOS=0x00 PREC=0x00 TTL=51 ID=62466 DF PROTO=TCP  SPT=443 DPT=57589 WINDOW=33 RES=0x00 ACK PSH URGP=0 
Nov 21 08:39:29  arcane-X555LB kernel: [389146.645913] [UFW BLOCK] IN=wlan0 OUT=  MAC=40:b8:9a:76:8a:17:48:5a:b6:f8:10:cd:08:00 SRC=69.172.216.111  DST=192.168.0.17 LEN=83 TOS=0x00 PREC=0x00 TTL=50 ID=50631 DF PROTO=TCP  SPT=443 DPT=57590 WINDOW=33 RES=0x00 ACK PSH URGP=0 
Nov 21 08:39:44  arcane-X555LB kernel: [389161.489754] [UFW BLOCK] IN=wlan0 OUT=  MAC=40:b8:9a:76:8a:17:48:5a:b6:f8:10:cd:08:00 SRC=69.172.216.111  DST=192.168.0.17 LEN=83 TOS=0x00 PREC=0x00 TTL=51 ID=62473 DF PROTO=TCP  SPT=443 DPT=57589 WINDOW=33 RES=0x00 ACK PSH URGP=0 
Nov 21 08:40:15  arcane-X555LB kernel: [389192.209108] [UFW BLOCK] IN=wlan0 OUT=  MAC=40:b8:9a:76:8a:17:6c:71:d9:70:19:23:08:00 SRC=192.168.0.2  DST=192.168.0.17 LEN=56 TOS=0x00 PREC=0x00 TTL=128 ID=13391 PROTO=UDP  SPT=63715 DPT=2054 LEN=36 
Nov 21 08:40:15 arcane-X555LB kernel:  [389193.029666] [UFW BLOCK] IN=wlan0 OUT=  MAC=33:33:00:00:00:01:48:5a:b6:f8:10:cd:86:dd  SRC=fe80:0000:0000:0000:4a5a:b6ff:fef8:10cd  DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=76 TC=0 HOPLIMIT=1  FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
Nov 21 08:41:15 arcane-X555LB  kernel: [389252.296364] [UFW BLOCK] IN=wlan0 OUT=  MAC=40:b8:9a:76:8a:17:6c:71:d9:70:19:23:08:00 SRC=192.168.0.2  DST=192.168.0.17 LEN=56 TOS=0x00 PREC=0x00 TTL=128 ID=13405 PROTO=UDP  SPT=62393 DPT=2054 LEN=36 
Nov 21 08:42:15 arcane-X555LB kernel:  [389312.187907] [UFW BLOCK] IN=wlan0 OUT=  MAC=40:b8:9a:76:8a:17:6c:71:d9:70:19:23:08:00 SRC=192.168.0.2  DST=192.168.0.17 LEN=56 TOS=0x00 PREC=0x00 TTL=128 ID=13419 PROTO=UDP  SPT=57510 DPT=2054 LEN=36 
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Initializing cgroup subsys cpu
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Initializing cgroup subsys cpuacct
Nov  21 08:43:20 arcane-X555LB kernel: [    0.000000] Linux version  3.13.11-03131107-generic (apw@gomeisa) (gcc version 4.6.3 (Ubuntu/Linaro  4.6.3-1ubuntu5) ) #201409181736 SMP Thu Sep 18 21:37:41 UTC 2014
Nov  21 08:43:20 arcane-X555LB kernel: [    0.000000] Command line:  BOOT_IMAGE=/boot/vmlinuz-3.13.11-03131107-generic  root=UUID=b320ac20-ec61-42ec-8900-f1b181a2d24e ro noprompt persistent  quiet splash acpi_osi= vt.handoff=7
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] KERNEL supported cpus:
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   Intel GenuineIntel
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   AMD AuthenticAMD
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   Centaur CentaurHauls
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x0000000000057fff] usable
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x0000000000058000-0x0000000000058fff] reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x0000000000059000-0x000000000009dfff] usable
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x000000000009e000-0x000000000009ffff] reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x0000000097070fff] usable
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x0000000097071000-0x00000000973c5fff] reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x00000000973c6000-0x000000009aa36fff] usable
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x000000009aa37000-0x000000009aa96fff] reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x000000009aa97000-0x000000009b296fff] usable
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x000000009b297000-0x000000009c41dfff] ACPI NVS
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x000000009c41e000-0x000000009cee6fff] reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x000000009cee7000-0x000000009cffefff] type 20
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x000000009cfff000-0x000000009cffffff] usable
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x000000009d800000-0x000000009fffffff] reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000025effffff] usable
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] NX (Execute Disable) protection: active
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: EFI v2.40 by American Megatrends
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi:  ACPI=0x9b69b000  ACPI 2.0=0x9b69b000  SMBIOS=0x9ce30918 
Nov  21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem00: type=7,  attr=0xf, range=[0x0000000000000000-0x0000000000058000) (0MB)
Nov 21  08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem01: type=0,  attr=0xf, range=[0x0000000000058000-0x0000000000059000) (0MB)
Nov 21  08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem02: type=7,  attr=0xf, range=[0x0000000000059000-0x000000000009e000) (0MB)
Nov 21  08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem03: type=0,  attr=0xf, range=[0x000000000009e000-0x00000000000a0000) (0MB)
Nov 21  08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem04: type=2,  attr=0xf, range=[0x0000000000100000-0x0000000001502000) (20MB)
Nov 21  08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem05: type=7,  attr=0xf, range=[0x0000000001502000-0x0000000002000000) (10MB)
Nov 21  08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem06: type=2,  attr=0xf, range=[0x0000000002000000-0x0000000003402000) (20MB)
Nov 21  08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem07: type=7,  attr=0xf, range=[0x0000000003402000-0x0000000010000000) (203MB)
Nov  21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem08: type=3,  attr=0xf, range=[0x0000000010000000-0x000000001000b000) (0MB)
Nov 21  08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem09: type=7,  attr=0xf, range=[0x000000001000b000-0x0000000035ccc000) (604MB)
Nov  21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem10: type=2,  attr=0xf, range=[0x0000000035ccc000-0x0000000036e5e000) (17MB)
Nov 21  08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem11: type=7,  attr=0xf, range=[0x0000000036e5e000-0x000000006999e000) (811MB)
Nov  21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem12: type=2,  attr=0xf, range=[0x000000006999e000-0x000000008f3dc000) (602MB)
Nov  21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem13: type=4,  attr=0xf, range=[0x000000008f3dc000-0x000000008f41c000) (0MB)
Nov 21  08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem14: type=7,  attr=0xf, range=[0x000000008f41c000-0x0000000095ee2000) (106MB)
Nov  21 08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem15: type=2,  attr=0xf, range=[0x0000000095ee2000-0x0000000095fce000) (0MB)
Nov 21  08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem16: type=7,  attr=0xf, range=[0x0000000095fce000-0x0000000095fd0000) (0MB)
Nov 21  08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem17: type=2,  attr=0xf, range=[0x0000000095fd0000-0x0000000095fd1000) (0MB)
Nov 21  08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem18: type=7,  attr=0xf, range=[0x0000000095fd1000-0x0000000095fd2000) (0MB)
Nov 21  08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem19: type=2,  attr=0xf, range=[0x0000000095fd2000-0x0000000095fd4000) (0MB)
Nov 21  08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem20: type=7,  attr=0xf, range=[0x0000000095fd4000-0x0000000095fd5000) (0MB)
Nov 21  08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem21: type=2,  attr=0xf, range=[0x0000000095fd5000-0x0000000095fd6000) (0MB)
Nov 21  08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem22: type=7,  attr=0xf, range=[0x0000000095fd6000-0x0000000095fda000) (0MB)
Nov 21  08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem23: type=2,  attr=0xf, range=[0x0000000095fda000-0x00000000960c4000) (0MB)
Nov 21  08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem24: type=1,  attr=0xf, range=[0x00000000960c4000-0x00000000961ea000) (1MB)
Nov 21  08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem25: type=4,  attr=0xf, range=[0x00000000961ea000-0x0000000097071000) (14MB)
Nov 21  08:43:20 arcane-X555LB kernel: [    0.000000] efi: mem26: type=6,  attr=0x800000000000000f, range=[0x0000000097071000-0x00000000973c6000)  (3MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi:  mem27: type=4, attr=0xf, range=[0x00000000973c6000-0x00000000973cc000)  (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi:  mem28: type=7, attr=0xf, range=[0x00000000973cc000-0x00000000973ce000)  (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi:  mem29: type=2, attr=0xf, range=[0x00000000973ce000-0x00000000973d0000)  (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi:  mem30: type=7, attr=0xf, range=[0x00000000973d0000-0x00000000973d1000)  (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi:  mem31: type=2, attr=0xf, range=[0x00000000973d1000-0x00000000973d3000)  (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi:  mem32: type=7, attr=0xf, range=[0x00000000973d3000-0x00000000973d6000)  (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi:  mem33: type=2, attr=0xf, range=[0x00000000973d6000-0x00000000973d8000)  (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi:  mem34: type=7, attr=0xf, range=[0x00000000973d8000-0x00000000973d9000)  (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi:  mem35: type=2, attr=0xf, range=[0x00000000973d9000-0x00000000973db000)  (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi:  mem36: type=4, attr=0xf, range=[0x00000000973db000-0x000000009a437000)  (48MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi:  mem37: type=7, attr=0xf, range=[0x000000009a437000-0x000000009a78f000)  (3MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi:  mem38: type=3, attr=0xf, range=[0x000000009a78f000-0x000000009aa37000)  (2MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi:  mem39: type=0, attr=0xf, range=[0x000000009aa37000-0x000000009aa97000)  (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi:  mem40: type=7, attr=0xf, range=[0x000000009aa97000-0x000000009b28d000)  (7MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi:  mem41: type=2, attr=0xf, range=[0x000000009b28d000-0x000000009b297000)  (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi:  mem42: type=10, attr=0xf, range=[0x000000009b297000-0x000000009c41e000)  (17MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi:  mem43: type=6, attr=0x800000000000000f,  range=[0x000000009c41e000-0x000000009cee7000) (10MB)
Nov 21 08:43:20  arcane-X555LB kernel: [    0.000000] efi: mem44: type=5,  attr=0x800000000000000f, range=[0x000000009cee7000-0x000000009cfff000)  (1MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi:  mem45: type=4, attr=0xf, range=[0x000000009cfff000-0x000000009d000000)  (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi:  mem46: type=7, attr=0xf, range=[0x0000000100000000-0x000000025f000000)  (5616MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi:  mem47: type=0, attr=0x0, range=[0x000000009d800000-0x00000000a0000000)  (40MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi:  mem48: type=11, attr=0x8000000000000001,  range=[0x00000000f8000000-0x00000000fc000000) (64MB)
Nov 21 08:43:20  arcane-X555LB kernel: [    0.000000] efi: mem49: type=11,  attr=0x8000000000000001, range=[0x00000000fec00000-0x00000000fec01000)  (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi:  mem50: type=11, attr=0x8000000000000001,  range=[0x00000000fed00000-0x00000000fed04000) (0MB)
Nov 21 08:43:20  arcane-X555LB kernel: [    0.000000] efi: mem51: type=11,  attr=0x8000000000000001, range=[0x00000000fed1c000-0x00000000fed20000)  (0MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] efi:  mem52: type=11, attr=0x8000000000000001,  range=[0x00000000fee00000-0x00000000fee01000) (0MB)
Nov 21 08:43:20  arcane-X555LB kernel: [    0.000000] efi: mem53: type=11,  attr=0x8000000000000001, range=[0x00000000ff000000-0x0000000100000000)  (16MB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] SMBIOS 2.8 present.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] DMI: ASUSTeK COMPUTER INC. X555LB/X555LB, BIOS X555LB.408 07/07/2015
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] No AGP bridge found
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] e820: last_pfn = 0x25f000 max_arch_pfn = 0x400000000
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] MTRR default type: uncachable
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] MTRR fixed ranges enabled:
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   00000-9FFFF write-back
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   A0000-EFFFF uncachable
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   F0000-FFFFF write-protect
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] MTRR variable ranges enabled:
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   0 base 0000000000 mask 7F80000000 write-back
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   1 base 0080000000 mask 7FF0000000 write-back
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   2 base 0090000000 mask 7FF8000000 write-back
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   3 base 0098000000 mask 7FFC000000 write-back
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   4 base 009C000000 mask 7FFF000000 write-back
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   5 base 0100000000 mask 7F00000000 write-back
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   6 base 0200000000 mask 7F80000000 write-back
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   7 base 0260000000 mask 7FE0000000 uncachable
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   8 base 025F000000 mask 7FFF000000 uncachable
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   9 disabled
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] original variable MTRRs
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] reg 1, base: 2GB, range: 256MB, type WB
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] reg 2, base: 2304MB, range: 128MB, type WB
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] reg 3, base: 2432MB, range: 64MB, type WB
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] reg 4, base: 2496MB, range: 16MB, type WB
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] reg 5, base: 4GB, range: 4GB, type WB
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] reg 6, base: 8GB, range: 2GB, type WB
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] reg 7, base: 9728MB, range: 512MB, type UC
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] reg 8, base: 9712MB, range: 16MB, type UC
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] total RAM covered: 8128M
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Found optimal setting for mtrr clean up
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]  gran_size: 64K     chunk_size: 64M     num_reg: 8      lose cover RAM: 0G
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] New variable MTRRs
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] reg 1, base: 2GB, range: 512MB, type WB
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] reg 2, base: 2512MB, range: 16MB, type UC
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] reg 3, base: 2528MB, range: 32MB, type UC
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] reg 4, base: 4GB, range: 4GB, type WB
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] reg 5, base: 8GB, range: 1GB, type WB
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] reg 6, base: 9GB, range: 512MB, type WB
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] reg 7, base: 9712MB, range: 16MB, type UC
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] e820: update [mem 0x9d000000-0xffffffff] usable ==> reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] e820: last_pfn = 0x9d000 max_arch_pfn = 0x400000000
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Scanning 1 areas for low memory corruption
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Using GB pages for direct mapping
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]  [mem 0x00000000-0x000fffff] page 4k
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BRK [0x02fe0000, 0x02fe0fff] PGTABLE
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BRK [0x02fe1000, 0x02fe1fff] PGTABLE
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BRK [0x02fe2000, 0x02fe2fff] PGTABLE
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] init_memory_mapping: [mem 0x25ee00000-0x25effffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]  [mem 0x25ee00000-0x25effffff] page 2M
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BRK [0x02fe3000, 0x02fe3fff] PGTABLE
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] init_memory_mapping: [mem 0x25c000000-0x25edfffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]  [mem 0x25c000000-0x25edfffff] page 2M
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] init_memory_mapping: [mem 0x200000000-0x25bffffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]  [mem 0x200000000-0x23fffffff] page 1G
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]  [mem 0x240000000-0x25bffffff] page 2M
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] init_memory_mapping: [mem 0x00100000-0x97070fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]  [mem 0x00100000-0x001fffff] page 4k
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]  [mem 0x40000000-0x7fffffff] page 1G
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]  [mem 0x80000000-0x96ffffff] page 2M
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]  [mem 0x97000000-0x97070fff] page 4k
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] init_memory_mapping: [mem 0x973c6000-0x9aa36fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]  [mem 0x973c6000-0x973fffff] page 4k
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]  [mem 0x97400000-0x9a9fffff] page 2M
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]  [mem 0x9aa00000-0x9aa36fff] page 4k
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BRK [0x02fe4000, 0x02fe4fff] PGTABLE
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] BRK [0x02fe5000, 0x02fe5fff] PGTABLE
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] init_memory_mapping: [mem 0x9aa97000-0x9b296fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]  [mem 0x9aa97000-0x9abfffff] page 4k
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]  [mem 0x9ac00000-0x9b1fffff] page 2M
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]  [mem 0x9b200000-0x9b296fff] page 4k
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] init_memory_mapping: [mem 0x9cfff000-0x9cffffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]  [mem 0x9cfff000-0x9cffffff] page 4k
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] init_memory_mapping: [mem 0x100000000-0x1ffffffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]  [mem 0x100000000-0x1ffffffff] page 1G
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] RAMDISK: [mem 0x35ccc000-0x36e5dfff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: RSDP 000000009b69b000 000024 (v02 _ASUS_)
Nov  21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: XSDT  000000009b69b0b0 0000DC (v01 _ASUS_ Notebook 01072009 AMI  00010013)
Nov  21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: FACP  000000009b6b4b58 00010C (v05 _ASUS_ Notebook 01072009 AMI  00010013)
Nov  21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI Error: Gpe0Block -  32-bit FADT register is too long (32 bytes, 256 bits) to convert to GAS  struct - 255 bits max, truncating (20131115/tbfadt-202)
Nov 21  08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: DSDT  000000009b69b218 01993D (v02 _ASUS_ Notebook 01072009 INTL 20120913)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: FACS 000000009c41bf80 000040
Nov  21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: APIC  000000009b6b4c68 000084 (v03 _ASUS_ Notebook 01072009 AMI  00010013)
Nov  21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: FPDT  000000009b6b4cf0 000044 (v01 _ASUS_ Notebook 01072009 AMI  00010013)
Nov  21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: FIDT  000000009b6b4d38 00009C (v01 _ASUS_ Notebook 01072009 AMI  00010013)
Nov  21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: ECDT  000000009b6b4dd8 0000C1 (v01 _ASUS_ Notebook 01072009 AMI. 00000005)
Nov  21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: MCFG  000000009b6b4ea0 00003C (v01 _ASUS_ Notebook 01072009 MSFT 00000097)
Nov  21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: HPET  000000009b6b4ee0 000038 (v01 _ASUS_ Notebook 01072009 AMI. 00000005)
Nov  21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: SSDT  000000009b6b4f18 000315 (v01 SataRe SataTabl 00001000 INTL 20120913)
Nov  21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: UEFI  000000009b6b5230 000042 (v01                 00000000      00000000)
Nov  21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: SSDT  000000009b6b5278 000194 (v01  Intel    zpodd 00001000 INTL 20120913)
Nov  21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: ASF!  000000009b6b5410 0000A0 (v32 INTEL       HCG 00000001 TFSM 000F4240)
Nov  21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: SSDT  000000009b6b54b0 000539 (v02  PmRef  Cpu0Ist 00003000 INTL 20120913)
Nov  21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: SSDT  000000009b6b59f0 000B74 (v02 CpuRef  CpuSsdt 00003000 INTL 20120913)
Nov  21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: SSDT  000000009b6b6568 003245 (v02 DptfTa DptfTabl 00001000 INTL 20120913)
Nov  21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: SSDT  000000009b6b97b0 000394 (v02 CppcTa CppcTabl 00001000 INTL 20120913)
Nov  21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: PCCT  000000009b6b9b48 00006E (v05 PcctTa PcctTabl 00001000 INTL 20120913)
Nov  21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: SSDT  000000009b6b9bb8 000AC4 (v02 Cpc_Ta Cpc_Tabl 00001000 INTL 20120913)
Nov  21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: SSDT  000000009b6ba680 006B80 (v02 SaSsdt  SaSsdt  00003000 INTL 20120913)
Nov  21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: SSDT  000000009b6c1200 00067C (v02  SgRef    SgPch 00001000 INTL 20120913)
Nov  21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: DMAR  000000009b6c1880 0000A8 (v01 INTEL      BDW  00000001 INTL 00000001)
Nov  21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: BGRT  000000009b6c1928 000038 (v01 _ASUS_ Notebook 01072009 AMI  00010013)
Nov  21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: SSDT  000000009b6c1960 000ED1 (v01 OptRef  OptTabl 00001000 INTL 20120913)
Nov  21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: MSDM  000000009aa95e18 000055 (v03 _ASUS_ Notebook 00000000 ASUS 00000001)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] No NUMA configuration found
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x000000025effffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Initmem setup node 0 [mem 0x00000000-0x25effffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   NODE_DATA [mem 0x25eff7000-0x25effbfff]
Nov  21 08:43:20 arcane-X555LB kernel: [    0.000000]   [ffffea0000000000-ffffea00097fffff] PMD ->  [ffff880256600000-ffff88025e5fffff] on node 0
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Zone ranges:
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   Normal   [mem 0x100000000-0x25effffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Movable zone start for each node
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Early memory node ranges
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   node   0: [mem 0x00001000-0x00057fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   node   0: [mem 0x00059000-0x0009dfff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   node   0: [mem 0x00100000-0x97070fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   node   0: [mem 0x973c6000-0x9aa36fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   node   0: [mem 0x9aa97000-0x9b296fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   node   0: [mem 0x9cfff000-0x9cffffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   node   0: [mem 0x100000000-0x25effffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] On node 0 totalpages: 2072191
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   DMA zone: 22 pages reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   DMA zone: 3996 pages, LIFO batch:0
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   DMA32 zone: 9852 pages used for memmap
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   DMA32 zone: 630499 pages, LIFO batch:31
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   Normal zone: 22464 pages used for memmap
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]   Normal zone: 1437696 pages, LIFO batch:31
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1808
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl level lint[0x40])
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: NMI not connected to LINT 1!
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl res lint[0x8b])
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: NMI not connected to LINT 1!
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] low level lint[0xf])
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: NMI not connected to LINT 1!
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] dfl edge lint[0x83])
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: NMI not connected to LINT 1!
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-39
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: IRQ0 used by override.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: IRQ2 used by override.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: IRQ9 used by override.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] nr_irqs_gsi: 56
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0x00058000-0x00058fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0x97071000-0x973c5fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9aa37000-0x9aa96fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9b297000-0x9c41dfff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9c41e000-0x9cee6fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9cee7000-0x9cffefff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9d000000-0x9d7fffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9d800000-0x9fffffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xa0000000-0xf7ffffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfecfffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed03fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed04000-0xfed1bfff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] e820: [mem 0xa0000000-0xf7ffffff] available for PCI devices
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88025ec00000 s86400 r8192 d24192 u524288
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] pcpu-alloc: s86400 r8192 d24192 u524288 alloc=1*2097152
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Nov  21 08:43:20 arcane-X555LB kernel: [    0.000000] Built 1 zonelists in  Zone order, mobility grouping on.  Total pages: 2039789
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Policy zone: Normal
Nov  21 08:43:20 arcane-X555LB kernel: [    0.000000] Kernel command line:  BOOT_IMAGE=/boot/vmlinuz-3.13.11-03131107-generic  root=UUID=b320ac20-ec61-42ec-8900-f1b181a2d24e ro noprompt persistent  quiet splash acpi_osi= vt.handoff=7
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] ACPI: _OSI method disabled
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Checking aperture...
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] No AGP bridge found
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Nov  21 08:43:20 arcane-X555LB kernel: [    0.000000] Memory:  7989084K/8288764K available (7555K kernel code, 1135K rwdata, 3528K  rodata, 1348K init, 1444K bss, 299680K reserved)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Hierarchical RCU implementation.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]     Offload RCU callbacks from all CPUs
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000]     Offload RCU callbacks from CPUs: 0-3.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] NR_IRQS:16640 nr_irqs:984 16
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Console: colour dummy device 80x25
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] console [tty0] enabled
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] allocated 33554432 bytes of page_cgroup
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] hpet clockevent registered
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] tsc: Fast TSC calibration using PIT
Nov 21 08:43:20 arcane-X555LB kernel: [    0.004000] tsc: Detected 2196.779 MHz processor
Nov  21 08:43:20 arcane-X555LB kernel: [    0.000003] Calibrating delay loop  (skipped), value calculated using timer frequency.. 4393.55 BogoMIPS  (lpj=8787116)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000005] pid_max: default: 32768 minimum: 301
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000015] init_memory_mapping: [mem 0x97071000-0x973c5fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000017]  [mem 0x97071000-0x973c5fff] page 4k
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000037] init_memory_mapping: [mem 0x9c41e000-0x9cee6fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000038]  [mem 0x9c41e000-0x9c5fffff] page 4k
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000039]  [mem 0x9c600000-0x9cdfffff] page 2M
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000040]  [mem 0x9ce00000-0x9cee6fff] page 4k
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000061] init_memory_mapping: [mem 0x9cee7000-0x9cffefff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000062]  [mem 0x9cee7000-0x9cffefff] page 4k
Nov 21 08:43:20 arcane-X555LB kernel: [    0.007892] Security Framework initialized
Nov 21 08:43:20 arcane-X555LB kernel: [    0.007900] AppArmor: AppArmor initialized
Nov 21 08:43:20 arcane-X555LB kernel: [    0.007901] Yama: becoming mindful.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.008392] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.009671] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.010189] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.010199] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.010376] Initializing cgroup subsys memory
Nov 21 08:43:20 arcane-X555LB kernel: [    0.010381] Initializing cgroup subsys devices
Nov 21 08:43:20 arcane-X555LB kernel: [    0.010383] Initializing cgroup subsys freezer
Nov 21 08:43:20 arcane-X555LB kernel: [    0.010384] Initializing cgroup subsys blkio
Nov 21 08:43:20 arcane-X555LB kernel: [    0.010385] Initializing cgroup subsys perf_event
Nov 21 08:43:20 arcane-X555LB kernel: [    0.010387] Initializing cgroup subsys hugetlb
Nov 21 08:43:20 arcane-X555LB kernel: [    0.010406] CPU: Physical Processor ID: 0
Nov 21 08:43:20 arcane-X555LB kernel: [    0.010407] CPU: Processor Core ID: 0
Nov 21 08:43:20 arcane-X555LB kernel: [    0.010411] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
Nov 21 08:43:20 arcane-X555LB kernel: [    0.010411] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.011398] mce: CPU supports 7 MCE banks
Nov 21 08:43:20 arcane-X555LB kernel: [    0.011409] CPU0: Thermal monitoring enabled (TM1)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.011418] Last level iTLB entries: 4KB 0, 2MB 0, 4MB 0
Nov 21 08:43:20 arcane-X555LB kernel: [    0.011418] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0
Nov 21 08:43:20 arcane-X555LB kernel: [    0.011418] tlb_flushall_shift: 6
Nov 21 08:43:20 arcane-X555LB kernel: [    0.011738] Freeing SMP alternatives memory: 28K (ffffffff81e6e000 - ffffffff81e75000)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.012577] ACPI: Core revision 20131115
Nov 21 08:43:20 arcane-X555LB kernel: [    0.031105] ACPI: All ACPI Tables successfully acquired
Nov 21 08:43:20 arcane-X555LB kernel: [    0.033850] ftrace: allocating 31300 entries in 123 pages
Nov 21 08:43:20 arcane-X555LB kernel: [    0.046290] dmar: Host address width 39
Nov 21 08:43:20 arcane-X555LB kernel: [    0.046292] dmar: DRHD base: 0x000000fed90000 flags: 0x0
Nov  21 08:43:20 arcane-X555LB kernel: [    0.046299] dmar: IOMMU 0:  reg_base_addr fed90000 ver 1:0 cap 1c0000c40660462 ecap 7e1ff0505e
Nov 21 08:43:20 arcane-X555LB kernel: [    0.046301] dmar: DRHD base: 0x000000fed91000 flags: 0x1
Nov  21 08:43:20 arcane-X555LB kernel: [    0.046306] dmar: IOMMU 1:  reg_base_addr fed91000 ver 1:0 cap d2008c20660462 ecap f010da
Nov 21 08:43:20 arcane-X555LB kernel: [    0.046308] dmar: RMRR base: 0x0000009ce40000 end: 0x0000009ce4efff
Nov 21 08:43:20 arcane-X555LB kernel: [    0.046309] dmar: RMRR base: 0x0000009d800000 end: 0x0000009fffffff
Nov 21 08:43:20 arcane-X555LB kernel: [    0.046431] IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
Nov 21 08:43:20 arcane-X555LB kernel: [    0.046432] HPET id 0 under DRHD base 0xfed91000
Nov 21 08:43:20 arcane-X555LB kernel: [    0.046433] Your BIOS is broken and requested that x2apic be disabled.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.046433] This will slightly decrease performance.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.046433] Use 'intremap=no_x2apic_optout' to override BIOS request.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.046631] Enabled IRQ remapping in xapic mode
Nov 21 08:43:20 arcane-X555LB kernel: [    0.046632] x2apic not enabled, IRQ remapping is in xapic mode
Nov 21 08:43:20 arcane-X555LB kernel: [    0.047245] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Nov  21 08:43:20 arcane-X555LB kernel: [    0.086917] smpboot: CPU0:  Intel(R) Core(TM) i5-5200U CPU @ 2.20GHz (fam: 06, model: 3d, stepping:  04)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.086924] TSC deadline timer enabled
Nov  21 08:43:20 arcane-X555LB kernel: [    0.086932] Performance Events:  PEBS fmt2+, generic architected perfmon, full-width counters, Intel PMU  driver.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.086937] ... version:                3
Nov 21 08:43:20 arcane-X555LB kernel: [    0.086938] ... bit width:              48
Nov 21 08:43:20 arcane-X555LB kernel: [    0.086938] ... generic registers:      4
Nov 21 08:43:20 arcane-X555LB kernel: [    0.086939] ... value mask:             0000ffffffffffff
Nov 21 08:43:20 arcane-X555LB kernel: [    0.086940] ... max period:             0000ffffffffffff
Nov 21 08:43:20 arcane-X555LB kernel: [    0.086941] ... fixed-purpose events:   3
Nov 21 08:43:20 arcane-X555LB kernel: [    0.086942] ... event mask:             000000070000000f
Nov 21 08:43:20 arcane-X555LB kernel: [    0.088260] x86: Booting SMP configuration:
Nov 21 08:43:20 arcane-X555LB kernel: [    0.102427] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.088262] .... node  #0, CPUs:      #1 #2 #3
Nov 21 08:43:20 arcane-X555LB kernel: [    0.130811] x86: Booted up 1 node, 4 CPUs
Nov 21 08:43:20 arcane-X555LB kernel: [    0.130814] smpboot: Total of 4 processors activated (17574.23 BogoMIPS)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.134577] devtmpfs: initialized
Nov 21 08:43:20 arcane-X555LB kernel: [    0.137606] EVM: security.selinux
Nov 21 08:43:20 arcane-X555LB kernel: [    0.137607] EVM: security.SMACK64
Nov 21 08:43:20 arcane-X555LB kernel: [    0.137608] EVM: security.ima
Nov 21 08:43:20 arcane-X555LB kernel: [    0.137608] EVM: security.capability
Nov  21 08:43:20 arcane-X555LB kernel: [    0.137650] PM: Registering ACPI  NVS region [mem 0x9b297000-0x9c41dfff] (18378752 bytes)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.138476] pinctrl core: initialized pinctrl subsystem
Nov 21 08:43:20 arcane-X555LB kernel: [    0.138520] regulator-dummy: no parameters
Nov 21 08:43:20 arcane-X555LB kernel: [    0.138549] RTC time:  8:43:04, date: 11/21/15
Nov 21 08:43:20 arcane-X555LB kernel: [    0.138574] NET: Registered protocol family 16
Nov 21 08:43:20 arcane-X555LB kernel: [    0.138664] cpuidle: using governor ladder
Nov 21 08:43:20 arcane-X555LB kernel: [    0.138666] cpuidle: using governor menu
Nov 21 08:43:20 arcane-X555LB kernel: [    0.138703] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
Nov 21 08:43:20 arcane-X555LB kernel: [    0.138705] ACPI: bus type PCI registered
Nov 21 08:43:20 arcane-X555LB kernel: [    0.138706] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
Nov  21 08:43:20 arcane-X555LB kernel: [    0.138745] PCI: MMCONFIG for  domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.138747] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
Nov 21 08:43:20 arcane-X555LB kernel: [    0.144452] PCI: Using configuration type 1 for base access
Nov 21 08:43:20 arcane-X555LB kernel: [    0.145195] bio: create slab <bio-0> at 0
Nov 21 08:43:20 arcane-X555LB kernel: [    0.145321] ACPI: Added _OSI(Module Device)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.145323] ACPI: Added _OSI(Processor Device)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.145324] ACPI: Added _OSI(3.0 _SCP Extensions)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.145325] ACPI: Added _OSI(Processor Aggregator Device)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.148076] ACPI : EC: EC description table is found, configuring boot EC
Nov 21 08:43:20 arcane-X555LB kernel: [    0.151028] ACPI: Executed 9 blocks of module-level executable AML code
Nov  21 08:43:20 arcane-X555LB kernel: [    0.182541] ACPI: SSDT  000000009aa57918 0003D3 (v02  PmRef  Cpu0Cst 00003001 INTL 20120913)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.183315] ACPI: Dynamic OEM Table Load:
Nov  21 08:43:20 arcane-X555LB kernel: [    0.183317] ACPI: SSDT            (null) 0003D3 (v02  PmRef  Cpu0Cst 00003001 INTL 20120913)
Nov 21  08:43:20 arcane-X555LB kernel: [    0.186663] ACPI: SSDT  000000009aa58618 0005AA (v02  PmRef    ApIst 00003000 INTL 20120913)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.187505] ACPI: Dynamic OEM Table Load:
Nov  21 08:43:20 arcane-X555LB kernel: [    0.187507] ACPI: SSDT            (null) 0005AA (v02  PmRef    ApIst 00003000 INTL 20120913)
Nov 21  08:43:20 arcane-X555LB kernel: [    0.190524] ACPI: SSDT  000000009aa59c18 000119 (v02  PmRef    ApCst 00003000 INTL 20120913)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.191296] ACPI: Dynamic OEM Table Load:
Nov  21 08:43:20 arcane-X555LB kernel: [    0.191298] ACPI: SSDT            (null) 000119 (v02  PmRef    ApCst 00003000 INTL 20120913)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.195264] ACPI: Interpreter enabled
Nov  21 08:43:20 arcane-X555LB kernel: [    0.195272] ACPI Exception:  AE_NOT_FOUND, While evaluating Sleep State [\_S1_]  (20131115/hwxface-580)
Nov 21 08:43:20 arcane-X555LB kernel: [     0.195279] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State  [\_S2_] (20131115/hwxface-580)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.195292] ACPI: (supports S0 S3 S4 S5)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.195293] ACPI: Using IOAPIC for interrupt routing
Nov  21 08:43:20 arcane-X555LB kernel: [    0.195319] PCI: Using host bridge  windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Nov 21 08:43:20 arcane-X555LB kernel: [    0.195545] ACPI: No dock devices found.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.197901] ACPI: Power Resource [PG00] (on)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.198140] ACPI: Power Resource [PG01] (on)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.198369] ACPI: Power Resource [PG02] (on)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.199124] ACPI: Power Resource [PC05] (on)
Nov  21 08:43:20 arcane-X555LB kernel: [    0.214770] ACPI Error: [_OSI]  Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
Nov 21  08:43:20 arcane-X555LB kernel: [    0.214774] ACPI Error: Method  parse/execution failed [\_SB_.PAGD._STA] (Node ffff8802530db938),  AE_NOT_FOUND (20131115/psparse-536)
Nov 21 08:43:20 arcane-X555LB  kernel: [    0.214788] ACPI Error: [_OSI] Namespace lookup failure,  AE_NOT_FOUND (20131115/psargs-359)
Nov 21 08:43:20 arcane-X555LB  kernel: [    0.214791] ACPI Error: Method parse/execution failed  [\_SB_.PAGD._STA] (Node ffff8802530db938), AE_NOT_FOUND  (20131115/psparse-536)
Nov 21 08:43:20 arcane-X555LB kernel: [     0.214810] ACPI Error: [_OSI] Namespace lookup failure, AE_NOT_FOUND  (20131115/psargs-359)
Nov 21 08:43:20 arcane-X555LB kernel: [     0.214812] ACPI Error: Method parse/execution failed [\_SB_.PAGD._STA]  (Node ffff8802530db938), AE_NOT_FOUND (20131115/psparse-536)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.216572] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
Nov  21 08:43:20 arcane-X555LB kernel: [    0.216577] acpi PNP0A08:00: _OSC:  OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217013] acpi PNP0A08:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217464] PCI host bridge to bus 0000:00
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217466] pci_bus 0000:00: root bus resource [bus 00-3e]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217468] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217469] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217471] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217472] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217473] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217475] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217476] pci_bus 0000:00: root bus resource [mem 0x000cc000-0x000cffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217478] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217480] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217481] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217482] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217483] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217485] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217486] pci_bus 0000:00: root bus resource [mem 0x000e8000-0x000ebfff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217487] pci_bus 0000:00: root bus resource [mem 0x000ec000-0x000effff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217488] pci_bus 0000:00: root bus resource [mem 0xa0000000-0xfeafffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217495] pci 0000:00:00.0: [8086:1604] type 00 class 0x060000
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217581] pci 0000:00:02.0: [8086:1616] type 00 class 0x030000
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217591] pci 0000:00:02.0: reg 0x10: [mem 0xa1000000-0xa1ffffff 64bit]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217596] pci 0000:00:02.0: reg 0x18: [mem 0xb0000000-0xbfffffff 64bit pref]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217601] pci 0000:00:02.0: reg 0x20: [io  0x5000-0x503f]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217683] pci 0000:00:03.0: [8086:160c] type 00 class 0x040300
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217690] pci 0000:00:03.0: reg 0x10: [mem 0xa331c000-0xa331ffff 64bit]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217777] pci 0000:00:04.0: [8086:1603] type 00 class 0x118000
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217788] pci 0000:00:04.0: reg 0x10: [mem 0xa3310000-0xa3317fff 64bit]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217892] pci 0000:00:14.0: [8086:9cb1] type 00 class 0x0c0330
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217907] pci 0000:00:14.0: reg 0x10: [mem 0xa3300000-0xa330ffff 64bit]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.217958] pci 0000:00:14.0: PME# supported from D3hot D3cold
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218013] pci 0000:00:14.0: System wakeup disabled by ACPI
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218039] pci 0000:00:16.0: [8086:9cba] type 00 class 0x078000
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218057] pci 0000:00:16.0: reg 0x10: [mem 0xa3324000-0xa332401f 64bit]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218119] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218196] pci 0000:00:1b.0: [8086:9ca0] type 00 class 0x040300
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218211] pci 0000:00:1b.0: reg 0x10: [mem 0xa3318000-0xa331bfff 64bit]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218261] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218315] pci 0000:00:1b.0: System wakeup disabled by ACPI
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218340] pci 0000:00:1c.0: [8086:9c90] type 01 class 0x060400
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218393] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218449] pci 0000:00:1c.0: System wakeup disabled by ACPI
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218471] pci 0000:00:1c.2: [8086:9c94] type 01 class 0x060400
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218525] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218578] pci 0000:00:1c.2: System wakeup disabled by ACPI
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218599] pci 0000:00:1c.3: [8086:9c96] type 01 class 0x060400
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218653] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218704] pci 0000:00:1c.3: System wakeup disabled by ACPI
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218726] pci 0000:00:1c.4: [8086:9c98] type 01 class 0x060400
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218780] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218831] pci 0000:00:1c.4: System wakeup disabled by ACPI
Nov 21 08:43:20 arcane-X555LB kernel: [    0.218859] pci 0000:00:1f.0: [8086:9cc3] type 00 class 0x060100
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219029] pci 0000:00:1f.2: [8086:9c83] type 00 class 0x010601
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219042] pci 0000:00:1f.2: reg 0x10: [io  0x50b0-0x50b7]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219048] pci 0000:00:1f.2: reg 0x14: [io  0x50a0-0x50a3]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219054] pci 0000:00:1f.2: reg 0x18: [io  0x5090-0x5097]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219059] pci 0000:00:1f.2: reg 0x1c: [io  0x5080-0x5083]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219065] pci 0000:00:1f.2: reg 0x20: [io  0x5060-0x507f]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219072] pci 0000:00:1f.2: reg 0x24: [mem 0xa3322000-0xa33227ff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219102] pci 0000:00:1f.2: PME# supported from D3hot
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219165] pci 0000:00:1f.3: [8086:9ca2] type 00 class 0x0c0500
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219177] pci 0000:00:1f.3: reg 0x10: [mem 0xa3321000-0xa33210ff 64bit]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219194] pci 0000:00:1f.3: reg 0x20: [io  0x5040-0x505f]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219277] pci 0000:00:1f.6: [8086:9ca4] type 00 class 0x118000
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219306] pci 0000:00:1f.6: reg 0x10: [mem 0xa3320000-0xa3320fff 64bit]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219526] acpiphp: Slot [1] registered
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219530] pci 0000:00:1c.0: PCI bridge to [bus 01]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219605] pci 0000:02:00.0: [10ec:8168] type 00 class 0x020000
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219621] pci 0000:02:00.0: reg 0x10: [io  0x4000-0x40ff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219647] pci 0000:02:00.0: reg 0x18: [mem 0xa3204000-0xa3204fff 64bit]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219663] pci 0000:02:00.0: reg 0x20: [mem 0xa3200000-0xa3203fff 64bit]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219732] pci 0000:02:00.0: supports D1 D2
Nov 21 08:43:20 arcane-X555LB kernel: [    0.219734] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Nov 21 08:43:20 arcane-X555LB kernel: [    0.226456] pci 0000:00:1c.2: PCI bridge to [bus 02]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.226460] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.226463] pci 0000:00:1c.2:   bridge window [mem 0xa3200000-0xa32fffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.226542] pci 0000:03:00.0: [14c3:7630] type 00 class 0x028000
Nov 21 08:43:20 arcane-X555LB kernel: [    0.226558] pci 0000:03:00.0: reg 0x10: [mem 0xa3100000-0xa31fffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.226669] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
Nov 21 08:43:20 arcane-X555LB kernel: [    0.234460] pci 0000:00:1c.3: PCI bridge to [bus 03]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.234465] pci 0000:00:1c.3:   bridge window [mem 0xa3100000-0xa31fffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.234533] pci 0000:04:00.0: [10de:1347] type 00 class 0x030200
Nov 21 08:43:20 arcane-X555LB kernel: [    0.234546] pci 0000:04:00.0: reg 0x10: [mem 0xa2000000-0xa2ffffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.234559] pci 0000:04:00.0: reg 0x14: [mem 0xc0000000-0xcfffffff 64bit pref]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.234572] pci 0000:04:00.0: reg 0x1c: [mem 0xd0000000-0xd1ffffff 64bit pref]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.234581] pci 0000:04:00.0: reg 0x24: [io  0x3000-0x307f]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.234591] pci 0000:04:00.0: reg 0x30: [mem 0xa3000000-0xa307ffff pref]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.234651] pci 0000:04:00.0: System wakeup disabled by ACPI
Nov 21 08:43:20 arcane-X555LB kernel: [    0.242464] pci 0000:00:1c.4: PCI bridge to [bus 04]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.242467] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.242470] pci 0000:00:1c.4:   bridge window [mem 0xa2000000-0xa30fffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.242474] pci 0000:00:1c.4:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.242496] acpi PNP0A08:00: Disabling ASPM (FADT indicates it is unsupported)
Nov  21 08:43:20 arcane-X555LB kernel: [    0.246743] ACPI Error: [_OSI]  Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
Nov 21  08:43:20 arcane-X555LB kernel: [    0.246747] ACPI Error: Method  parse/execution failed [\_SB_.PAGD._STA] (Node ffff8802530db938),  AE_NOT_FOUND (20131115/psparse-536)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.246789] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.246835] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.246878] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.246921] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.246964] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.247008] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.247053] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.247096] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.247695] ACPI: Enabled 5 GPEs in block 00 to 7F
Nov 21 08:43:20 arcane-X555LB kernel: [    0.247701] ACPI: \_SB_.PCI0: notify handler is installed
Nov 21 08:43:20 arcane-X555LB kernel: [    0.247779] Found 1 acpi root devices
Nov 21 08:43:20 arcane-X555LB kernel: [    0.247842] ACPI : EC: GPE = 0xa, I/O: command/status = 0x66, data = 0x62
Nov  21 08:43:20 arcane-X555LB kernel: [    0.247916] vgaarb: device added:  PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Nov 21 08:43:20 arcane-X555LB kernel: [    0.247919] vgaarb: loaded
Nov 21 08:43:20 arcane-X555LB kernel: [    0.247920] vgaarb: bridge control possible 0000:00:02.0
Nov 21 08:43:20 arcane-X555LB kernel: [    0.248037] SCSI subsystem initialized
Nov 21 08:43:20 arcane-X555LB kernel: [    0.248072] libata version 3.00 loaded.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.248085] ACPI: bus type USB registered
Nov 21 08:43:20 arcane-X555LB kernel: [    0.248096] usbcore: registered new interface driver usbfs
Nov 21 08:43:20 arcane-X555LB kernel: [    0.248101] usbcore: registered new interface driver hub
Nov 21 08:43:20 arcane-X555LB kernel: [    0.248118] usbcore: registered new device driver usb
Nov 21 08:43:20 arcane-X555LB kernel: [    0.248203] PCI: Using ACPI for IRQ routing
Nov 21 08:43:20 arcane-X555LB kernel: [    0.249349] PCI: pci_cache_line_size set to 64 bytes
Nov 21 08:43:20 arcane-X555LB kernel: [    0.249389] e820: reserve RAM buffer [mem 0x00058000-0x0005ffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.249390] e820: reserve RAM buffer [mem 0x0009e000-0x0009ffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.249391] e820: reserve RAM buffer [mem 0x97071000-0x97ffffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.249393] e820: reserve RAM buffer [mem 0x9aa37000-0x9bffffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.249394] e820: reserve RAM buffer [mem 0x9b297000-0x9bffffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.249395] e820: reserve RAM buffer [mem 0x9d000000-0x9fffffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.249396] e820: reserve RAM buffer [mem 0x25f000000-0x25fffffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.249457] NetLabel: Initializing
Nov 21 08:43:20 arcane-X555LB kernel: [    0.249458] NetLabel:  domain hash size = 128
Nov 21 08:43:20 arcane-X555LB kernel: [    0.249458] NetLabel:  protocols = UNLABELED CIPSOv4
Nov 21 08:43:20 arcane-X555LB kernel: [    0.249468] NetLabel:  unlabeled traffic allowed by default
Nov 21 08:43:20 arcane-X555LB kernel: [    0.249517] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
Nov 21 08:43:20 arcane-X555LB kernel: [    0.249522] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
Nov 21 08:43:20 arcane-X555LB kernel: [    0.251552] Switched to clocksource hpet
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255124] AppArmor: AppArmor Filesystem Enabled
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255141] pnp: PnP ACPI init
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255151] ACPI: bus type PNP registered
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255306] system 00:00: [io  0x0240-0x0259] has been reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255309] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
Nov  21 08:43:20 arcane-X555LB kernel: [    0.255377] pnp 00:01: Plug and  Play ACPI device, IDs ETD0108 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12  (active)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255412] pnp 00:02: Plug and Play ACPI device, IDs ATK3001 PNP030b (active)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255418] pnp 00:03: [dma 4]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255430] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255447] pnp 00:04: Plug and Play ACPI device, IDs INT0800 (active)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255535] pnp 00:05: Plug and Play ACPI device, IDs PNP0103 (active)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255590] system 00:06: [io  0x0680-0x069f] has been reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255592] system 00:06: [io  0xffff] has been reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255593] system 00:06: [io  0xffff] has been reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255595] system 00:06: [io  0xffff] has been reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255596] system 00:06: [io  0x1800-0x18fe] could not be reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255598] system 00:06: [io  0x164e-0x164f] has been reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255599] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255636] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255665] system 00:08: [io  0x1854-0x1857] has been reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255667] system 00:08: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255788] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255789] system 00:09: [mem 0xfed10000-0xfed17fff] has been reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255791] system 00:09: [mem 0xfed18000-0xfed18fff] has been reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255792] system 00:09: [mem 0xfed19000-0xfed19fff] has been reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255794] system 00:09: [mem 0xf8000000-0xfbffffff] has been reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255796] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255797] system 00:09: [mem 0xfed90000-0xfed93fff] could not be reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255799] system 00:09: [mem 0xfed45000-0xfed8ffff] has been reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255800] system 00:09: [mem 0xff000000-0xffffffff] has been reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255802] system 00:09: [mem 0xfee00000-0xfeefffff] could not be reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255803] system 00:09: [mem 0xa0010000-0xa001ffff] has been reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255805] system 00:09: [mem 0xa0000000-0xa000ffff] has been reserved
Nov 21 08:43:20 arcane-X555LB kernel: [    0.255806] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
Nov  21 08:43:20 arcane-X555LB kernel: [    0.259774] ACPI Error: [_OSI]  Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
Nov 21  08:43:20 arcane-X555LB kernel: [    0.259779] ACPI Error: Method  parse/execution failed [\_SB_.PAGD._STA] (Node ffff8802530db938),  AE_NOT_FOUND (20131115/psparse-536)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.260014] pnp: PnP ACPI: found 10 devices
Nov 21 08:43:20 arcane-X555LB kernel: [    0.260015] ACPI: bus type PNP unregistered
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265851] pci 0000:00:1c.0: PCI bridge to [bus 01]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265861] pci 0000:00:1c.2: PCI bridge to [bus 02]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265863] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265867] pci 0000:00:1c.2:   bridge window [mem 0xa3200000-0xa32fffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265873] pci 0000:00:1c.3: PCI bridge to [bus 03]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265876] pci 0000:00:1c.3:   bridge window [mem 0xa3100000-0xa31fffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265882] pci 0000:00:1c.4: PCI bridge to [bus 04]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265884] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265888] pci 0000:00:1c.4:   bridge window [mem 0xa2000000-0xa30fffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265891] pci 0000:00:1c.4:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265896] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265897] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265899] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265900] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265901] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265903] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265904] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265905] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265907] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265908] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265909] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265910] pci_bus 0000:00: resource 15 [mem 0x000e0000-0x000e3fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265912] pci_bus 0000:00: resource 16 [mem 0x000e4000-0x000e7fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265913] pci_bus 0000:00: resource 17 [mem 0x000e8000-0x000ebfff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265914] pci_bus 0000:00: resource 18 [mem 0x000ec000-0x000effff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265915] pci_bus 0000:00: resource 19 [mem 0xa0000000-0xfeafffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265917] pci_bus 0000:02: resource 0 [io  0x4000-0x4fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265918] pci_bus 0000:02: resource 1 [mem 0xa3200000-0xa32fffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265920] pci_bus 0000:03: resource 1 [mem 0xa3100000-0xa31fffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265921] pci_bus 0000:04: resource 0 [io  0x3000-0x3fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265923] pci_bus 0000:04: resource 1 [mem 0xa2000000-0xa30fffff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265924] pci_bus 0000:04: resource 2 [mem 0xc0000000-0xd1ffffff 64bit pref]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.265945] NET: Registered protocol family 2
Nov 21 08:43:20 arcane-X555LB kernel: [    0.266105] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.266221] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.266325] TCP: Hash tables configured (established 65536 bind 65536)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.266341] TCP: reno registered
Nov 21 08:43:20 arcane-X555LB kernel: [    0.266351] UDP hash table entries: 4096 (order: 5, 131072 bytes)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.266375] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.266424] NET: Registered protocol family 1
Nov 21 08:43:20 arcane-X555LB kernel: [    0.266433] pci 0000:00:02.0: Boot video device
Nov 21 08:43:20 arcane-X555LB kernel: [    0.266622] PCI: CLS 64 bytes, default 64
Nov 21 08:43:20 arcane-X555LB kernel: [    0.266662] Trying to unpack rootfs image as initramfs...
Nov 21 08:43:20 arcane-X555LB kernel: [    0.531203] Freeing initrd memory: 17992K (ffff880035ccc000 - ffff880036e5e000)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.531212] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Nov  21 08:43:20 arcane-X555LB kernel: [    0.531214] software IO TLB [mem  0x921ea000-0x961ea000] (64MB) mapped at  [ffff8800921ea000-ffff8800961e9fff]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.531368] microcode: CPU0 sig=0x306d4, pf=0x40, revision=0x1f
Nov 21 08:43:20 arcane-X555LB kernel: [    0.531374] microcode: CPU1 sig=0x306d4, pf=0x40, revision=0x1f
Nov 21 08:43:20 arcane-X555LB kernel: [    0.531381] microcode: CPU2 sig=0x306d4, pf=0x40, revision=0x1f
Nov 21 08:43:20 arcane-X555LB kernel: [    0.531387] microcode: CPU3 sig=0x306d4, pf=0x40, revision=0x1f
Nov  21 08:43:20 arcane-X555LB kernel: [    0.531423] microcode: Microcode  Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Nov 21 08:43:20 arcane-X555LB kernel: [    0.531424] Scanning for low memory corruption every 60 seconds
Nov 21 08:43:20 arcane-X555LB kernel: [    0.531623] Initialise system trusted keyring
Nov 21 08:43:20 arcane-X555LB kernel: [    0.531654] audit: initializing netlink socket (disabled)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.531661] type=2000 audit(1448095384.528:1): initialized
Nov 21 08:43:20 arcane-X555LB kernel: [    0.557256] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Nov 21 08:43:20 arcane-X555LB kernel: [    0.558211] zbud: loaded
Nov 21 08:43:20 arcane-X555LB kernel: [    0.558334] VFS: Disk quotas dquot_6.5.2
Nov 21 08:43:20 arcane-X555LB kernel: [    0.558368] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.558678] fuse init (API version 7.22)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.558730] msgmni has been set to 15770
Nov 21 08:43:20 arcane-X555LB kernel: [    0.558766] Key type big_key registered
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559073] Key type asymmetric registered
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559075] Asymmetric key parser 'x509' registered
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559095] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559122] io scheduler noop registered
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559123] io scheduler deadline registered (default)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559140] io scheduler cfq registered
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559300] pcieport 0000:00:1c.0: irq 58 for MSI/MSI-X
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559421] pcieport 0000:00:1c.2: irq 59 for MSI/MSI-X
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559543] pcieport 0000:00:1c.3: irq 60 for MSI/MSI-X
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559654] pcieport 0000:00:1c.4: irq 61 for MSI/MSI-X
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559709] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559713] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559723] pcieport 0000:00:1c.2: Signaling PME through PCIe PME interrupt
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559724] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559727] pcie_pme 0000:00:1c.2:pcie01: service driver pcie_pme loaded
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559741] pcieport 0000:00:1c.3: Signaling PME through PCIe PME interrupt
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559744] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559747] pcie_pme 0000:00:1c.3:pcie01: service driver pcie_pme loaded
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559756] pcieport 0000:00:1c.4: Signaling PME through PCIe PME interrupt
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559758] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559761] pcie_pme 0000:00:1c.4:pcie01: service driver pcie_pme loaded
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559769] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559779] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Nov 21 08:43:20 arcane-X555LB kernel: [    0.559809] efifb: probing for efifb
Nov  21 08:43:20 arcane-X555LB kernel: [    0.560008] efifb: framebuffer at  0xb0000000, mapped to 0xffffc90009f80000, using 1920k, total 1920k
Nov 21 08:43:20 arcane-X555LB kernel: [    0.560010] efifb: mode is 800x600x32, linelength=3200, pages=1
Nov 21 08:43:20 arcane-X555LB kernel: [    0.560010] efifb: scrolling: redraw
Nov 21 08:43:20 arcane-X555LB kernel: [    0.560012] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Nov 21 08:43:20 arcane-X555LB kernel: [    0.560889] Console: switching to colour frame buffer device 100x37
Nov 21 08:43:20 arcane-X555LB kernel: [    0.561711] fb0: EFI VGA frame buffer device
Nov 21 08:43:20 arcane-X555LB kernel: [    0.561719] intel_idle: does not run on family 6 model 61
Nov 21 08:43:20 arcane-X555LB kernel: [    0.561724] ipmi message handler version 39.2
Nov  21 08:43:20 arcane-X555LB kernel: [    0.567512] ACPI: Deprecated  procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER  cleared
Nov 21 08:43:20 arcane-X555LB kernel: [    0.567566] ACPI: AC Adapter [AC0] (off-line)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.567662] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
Nov 21 08:43:20 arcane-X555LB kernel: [    0.568312] ACPI: Lid Switch [LID]
Nov  21 08:43:20 arcane-X555LB kernel: [    0.568340] input: Sleep Button as  /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
Nov 21 08:43:20 arcane-X555LB kernel: [    0.568344] ACPI: Sleep Button [SLPB]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.568368] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Nov 21 08:43:20 arcane-X555LB kernel: [    0.568370] ACPI: Power Button [PWRF]
Nov 21 08:43:20 arcane-X555LB kernel: [    0.568645] Monitor-Mwait will be used to enter C-1 state
Nov 21 08:43:20 arcane-X555LB kernel: [    0.568648] Monitor-Mwait will be used to enter C-2 state
Nov 21 08:43:20 arcane-X555LB kernel: [    0.568651] Monitor-Mwait will be used to enter C-3 state
Nov 21 08:43:20 arcane-X555LB kernel: [    0.568665] ACPI: acpi_idle registered with cpuidle
Nov 21 08:43:20 arcane-X555LB kernel: [    0.569600] thermal LNXTHERM:00: registered as thermal_zone0
Nov 21 08:43:20 arcane-X555LB kernel: [    0.569602] ACPI: Thermal Zone [THRM] (56 C)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.569634] GHES: HEST is not enabled!
Nov 21 08:43:20 arcane-X555LB kernel: [    0.569691] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Nov 21 08:43:20 arcane-X555LB kernel: [    0.571159] Linux agpgart interface v0.103
Nov  21 08:43:20 arcane-X555LB kernel: [    0.574633] ACPI: Deprecated  procfs I/F for battery is loaded, please retry with  CONFIG_ACPI_PROCFS_POWER cleared
Nov 21 08:43:20 arcane-X555LB kernel: [    0.574638] ACPI: Battery Slot [BAT0] (battery present)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.574696] brd: module loaded
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575130] loop: module loaded
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575367] libphy: Fixed MDIO Bus: probed
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575425] tun: Universal TUN/TAP device driver, 1.6
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575426] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575457] PPP generic driver version 2.4.2
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575509] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575511] ehci-pci: EHCI PCI platform driver
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575518] ehci-platform: EHCI generic platform driver
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575523] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575524] ohci-pci: OHCI PCI platform driver
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575530] ohci-platform: OHCI generic platform driver
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575534] uhci_hcd: USB Universal Host Controller Interface driver
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575634] xhci_hcd 0000:00:14.0: xHCI Host Controller
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575638] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575713] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575729] xhci_hcd 0000:00:14.0: irq 62 for MSI/MSI-X
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575776] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575777] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575779] usb usb1: Product: xHCI Host Controller
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575780] usb usb1: Manufacturer: Linux 3.13.11-03131107-generic xhci_hcd
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575781] usb usb1: SerialNumber: 0000:00:14.0
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575855] hub 1-0:1.0: USB hub found
Nov 21 08:43:20 arcane-X555LB kernel: [    0.575865] hub 1-0:1.0: 11 ports detected
Nov 21 08:43:20 arcane-X555LB kernel: [    0.578193] xhci_hcd 0000:00:14.0: xHCI Host Controller
Nov 21 08:43:20 arcane-X555LB kernel: [    0.578196] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
Nov 21 08:43:20 arcane-X555LB kernel: [    0.578221] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
Nov 21 08:43:20 arcane-X555LB kernel: [    0.578222] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Nov 21 08:43:20 arcane-X555LB kernel: [    0.578223] usb usb2: Product: xHCI Host Controller
Nov 21 08:43:20 arcane-X555LB kernel: [    0.578225] usb usb2: Manufacturer: Linux 3.13.11-03131107-generic xhci_hcd
Nov 21 08:43:20 arcane-X555LB kernel: [    0.578226] usb usb2: SerialNumber: 0000:00:14.0
Nov 21 08:43:20 arcane-X555LB kernel: [    0.578294] hub 2-0:1.0: USB hub found
Nov 21 08:43:20 arcane-X555LB kernel: [    0.578301] hub 2-0:1.0: 4 ports detected
Nov  21 08:43:20 arcane-X555LB kernel: [    0.583570] i8042: PNP: PS/2  Controller [PNP030b:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Nov 21 08:43:20 arcane-X555LB kernel: [    0.586589] i8042: Detected active multiplexing controller, rev 1.1
Nov 21 08:43:20 arcane-X555LB kernel: [    0.588498] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov 21 08:43:20 arcane-X555LB kernel: [    0.588502] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Nov 21 08:43:20 arcane-X555LB kernel: [    0.588529] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Nov 21 08:43:20 arcane-X555LB kernel: [    0.588538] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Nov 21 08:43:20 arcane-X555LB kernel: [    0.588548] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Nov 21 08:43:20 arcane-X555LB kernel: [    0.588779] mousedev: PS/2 mouse device common for all mice
Nov 21 08:43:20 arcane-X555LB kernel: [    0.589257] rtc_cmos 00:07: RTC can wake from S4
Nov 21 08:43:20 arcane-X555LB kernel: [    0.589452] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
Nov 21 08:43:20 arcane-X555LB kernel: [    0.589479] rtc_cmos 00:07: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
Nov 21 08:43:20 arcane-X555LB kernel: [    0.589529] device-mapper: uevent: version 1.0.3
Nov  21 08:43:20 arcane-X555LB kernel: [    0.589587] device-mapper: ioctl:  4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
Nov 21 08:43:20 arcane-X555LB kernel: [    0.589592] ledtrig-cpu: registered to indicate activity on CPUs
Nov 21 08:43:20 arcane-X555LB kernel: [    0.589593] EFI Variables Facility v0.08 2004-May-17
Nov 21 08:43:20 arcane-X555LB kernel: [    0.591131] TCP: cubic registered
Nov 21 08:43:20 arcane-X555LB kernel: [    0.591188] NET: Registered protocol family 10
Nov 21 08:43:20 arcane-X555LB kernel: [    0.591300] NET: Registered protocol family 17
Nov 21 08:43:20 arcane-X555LB kernel: [    0.591310] Key type dns_resolver registered
Nov 21 08:43:20 arcane-X555LB kernel: [    0.591854] Loading compiled-in X.509 certificates
Nov  21 08:43:20 arcane-X555LB kernel: [    0.592524] Loaded X.509 cert  'Magrathea: Glacier signing key:  3ce7d6b7ac2aa04206fb669ece940cfebfb09e52'
Nov 21 08:43:20 arcane-X555LB kernel: [    0.592534] registered taskstats version 1
Nov 21 08:43:20 arcane-X555LB kernel: [    0.594831] Key type trusted registered
Nov 21 08:43:20 arcane-X555LB kernel: [    0.596657] Key type encrypted registered
Nov 21 08:43:20 arcane-X555LB kernel: [    0.598010] AppArmor: AppArmor sha1 policy hashing enabled
Nov 21 08:43:20 arcane-X555LB kernel: [    0.598013] IMA: No TPM chip found, activating TPM-bypass!
Nov 21 08:43:20 arcane-X555LB kernel: [    0.598401] regulator-dummy: disabling
Nov 21 08:43:20 arcane-X555LB kernel: [    0.598457]   Magic number: 7:141:726
Nov 21 08:43:20 arcane-X555LB kernel: [    0.598465] block loop6: hash matches
Nov  21 08:43:20 arcane-X555LB kernel: [    0.598564] rtc_cmos 00:07:  setting system clock to 2015-11-21 08:43:04 UTC (1448095384)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.599139] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Nov 21 08:43:20 arcane-X555LB kernel: [    0.599141] EDD information not available.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.599176] PM: Hibernation image not present or could not be loaded.
Nov 21 08:43:20 arcane-X555LB kernel: [    0.600076] Freeing unused kernel memory: 1348K (ffffffff81d1d000 - ffffffff81e6e000)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.600078] Write protecting the kernel read-only data: 12288k
Nov 21 08:43:20 arcane-X555LB kernel: [    0.601288] Freeing unused kernel memory: 624K (ffff880002764000 - ffff880002800000)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.602309] Freeing unused kernel memory: 568K (ffff880002b72000 - ffff880002c00000)
Nov  21 08:43:20 arcane-X555LB kernel: [    0.627809] input: AT Translated  Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Nov 21 08:43:20 arcane-X555LB kernel: [    0.635804] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Nov 21 08:43:20 arcane-X555LB kernel: [    0.635814] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
Nov 21 08:43:20 arcane-X555LB kernel: [    0.636142] ahci 0000:00:1f.2: version 3.0
Nov 21 08:43:20 arcane-X555LB kernel: [    0.636239] ahci 0000:00:1f.2: irq 63 for MSI/MSI-X
Nov 21 08:43:20 arcane-X555LB kernel: [    0.643874] r8169 0000:02:00.0: irq 64 for MSI/MSI-X
Nov  21 08:43:20 arcane-X555LB kernel: [    0.644038] r8169 0000:02:00.0  eth0: RTL8168g/8111g at 0xffffc900040a2000, 1c:b7:2c:a2:ad:f1, XID  10900800 IRQ 64
Nov 21 08:43:20 arcane-X555LB kernel: [    0.644041]  r8169 0000:02:00.0 eth0: jumbo features [frames: 9200 bytes, tx  checksumming: ko]
Nov 21 08:43:20 arcane-X555LB kernel: [     0.651479] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 6 Gbps 0x3  impl SATA mode
Nov 21 08:43:20 arcane-X555LB kernel: [    0.651485]  ahci 0000:00:1f.2: flags: 64bit ncq pm led clo only pio slum part deso  sadm sds apst 
Nov 21 08:43:20 arcane-X555LB kernel: [    0.652035] scsi0 : ahci
Nov 21 08:43:20 arcane-X555LB kernel: [    0.652108] scsi1 : ahci
Nov 21 08:43:20 arcane-X555LB kernel: [    0.652162] scsi2 : ahci
Nov 21 08:43:20 arcane-X555LB kernel: [    0.652207] scsi3 : ahci
Nov 21 08:43:20 arcane-X555LB kernel: [    0.652251] ata1: SATA max UDMA/133 abar m2048@0xa3322000 port 0xa3322100 irq 63
Nov 21 08:43:20 arcane-X555LB kernel: [    0.652253] ata2: SATA max UDMA/133 abar m2048@0xa3322000 port 0xa3322180 irq 63
Nov 21 08:43:20 arcane-X555LB kernel: [    0.652255] ata3: DUMMY
Nov 21 08:43:20 arcane-X555LB kernel: [    0.652256] ata4: DUMMY
Nov 21 08:43:20 arcane-X555LB kernel: [    0.887463] usb 1-5: new high-speed USB device number 2 using xhci_hcd
Nov 21 08:43:20 arcane-X555LB kernel: [    0.925145] usb 1-5: New USB device found, idVendor=0bda, idProduct=57b5
Nov 21 08:43:20 arcane-X555LB kernel: [    0.925148] usb 1-5: New USB device strings: Mfr=3, Product=1, SerialNumber=2
Nov 21 08:43:20 arcane-X555LB kernel: [    0.925150] usb 1-5: Product: USB Camera
Nov 21 08:43:20 arcane-X555LB kernel: [    0.925152] usb 1-5: Manufacturer: 04081-00092400F6GL2R
Nov 21 08:43:20 arcane-X555LB kernel: [    0.925153] usb 1-5: SerialNumber: 200901010001
Nov 21 08:43:20 arcane-X555LB kernel: [    0.971423] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.971441] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.972782] ata1.00: ATA-8: HGST HTS721075A9E630, JB2OA3J0, max UDMA/133
Nov 21 08:43:20 arcane-X555LB kernel: [    0.972786] ata1.00: 1465149168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Nov 21 08:43:20 arcane-X555LB kernel: [    0.974277] ata1.00: configured for UDMA/133
Nov  21 08:43:20 arcane-X555LB kernel: [    0.974480] scsi 0:0:0:0:  Direct-Access     ATA      HGST HTS721075A9 JB2O PQ: 0 ANSI: 5
Nov 21 08:43:20 arcane-X555LB kernel: [    0.974614] sd 0:0:0:0: [sda] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
Nov 21 08:43:20 arcane-X555LB kernel: [    0.974618] sd 0:0:0:0: [sda] 4096-byte physical blocks
Nov 21 08:43:20 arcane-X555LB kernel: [    0.974627] sd 0:0:0:0: Attached scsi generic sg0 type 0
Nov 21 08:43:20 arcane-X555LB kernel: [    0.974691] sd 0:0:0:0: [sda] Write Protect is off
Nov 21 08:43:20 arcane-X555LB kernel: [    0.974695] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  21 08:43:20 arcane-X555LB kernel: [    0.974729] sd 0:0:0:0: [sda]  Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 21 08:43:20 arcane-X555LB kernel: [    0.975571] ata2.00: ATAPI: TSSTcorp CDDVDW SU-228GB, AS00, max UDMA/100
Nov 21 08:43:20 arcane-X555LB kernel: [    0.978216] ata2.00: configured for UDMA/100
Nov  21 08:43:20 arcane-X555LB kernel: [    0.984618] scsi 1:0:0:0:  CD-ROM            TSSTcorp CDDVDW SU-228GB  AS00 PQ: 0 ANSI: 5
Nov 21 08:43:20 arcane-X555LB kernel: [    0.990038] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Nov 21 08:43:20 arcane-X555LB kernel: [    0.990041] cdrom: Uniform CD-ROM driver Revision: 3.20
Nov 21 08:43:20 arcane-X555LB kernel: [    0.990165] sr 1:0:0:0: Attached scsi CD-ROM sr0
Nov 21 08:43:20 arcane-X555LB kernel: [    0.990328] sr 1:0:0:0: Attached scsi generic sg1 type 5
Nov 21 08:43:20 arcane-X555LB kernel: [    1.015292]  sda: sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8
Nov 21 08:43:20 arcane-X555LB kernel: [    1.015824] sd 0:0:0:0: [sda] Attached SCSI disk
Nov 21 08:43:20 arcane-X555LB kernel: [    1.091387] usb 1-6: new high-speed USB device number 3 using xhci_hcd
Nov 21 08:43:20 arcane-X555LB kernel: [    1.121481] usb 1-6: New USB device found, idVendor=0489, idProduct=e080
Nov 21 08:43:20 arcane-X555LB kernel: [    1.121484] usb 1-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Nov 21 08:43:20 arcane-X555LB kernel: [    1.121486] usb 1-6: Product: BT
Nov 21 08:43:20 arcane-X555LB kernel: [    1.121487] usb 1-6: Manufacturer: MediaTek
Nov 21 08:43:20 arcane-X555LB kernel: [    1.121489] usb 1-6: SerialNumber: 1.0
Nov 21 08:43:20 arcane-X555LB kernel: [    1.287325] usb 1-8: new high-speed USB device number 4 using xhci_hcd
Nov 21 08:43:20 arcane-X555LB kernel: [    1.303616] usb 1-8: New USB device found, idVendor=0bda, idProduct=0129
Nov 21 08:43:20 arcane-X555LB kernel: [    1.303619] usb 1-8: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Nov 21 08:43:20 arcane-X555LB kernel: [    1.303621] usb 1-8: Product: USB2.0-CRW
Nov 21 08:43:20 arcane-X555LB kernel: [    1.303622] usb 1-8: Manufacturer: Generic
Nov 21 08:43:20 arcane-X555LB kernel: [    1.303623] usb 1-8: SerialNumber: 20100201396000000
Nov  21 08:43:20 arcane-X555LB kernel: [    1.364376] psmouse serio4:  elantech: assuming hardware version 4 (with firmware version 0x381f00)
Nov  21 08:43:20 arcane-X555LB kernel: [    1.378951] psmouse serio4:  elantech: Synaptics capabilities query result 0x10, 0x14, 0x0e.
Nov  21 08:43:20 arcane-X555LB kernel: [    1.446697] input: ETPS/2 Elantech  Touchpad as /devices/platform/i8042/serio4/input/input11
Nov 21 08:43:20 arcane-X555LB kernel: [    1.527246] tsc: Refined TSC clocksource calibration: 2196.821 MHz
Nov 21 08:43:20 arcane-X555LB kernel: [    1.745787] EXT4-fs (sda7): INFO: recovery required on readonly filesystem
Nov 21 08:43:20 arcane-X555LB kernel: [    1.745790] EXT4-fs (sda7): write access will be enabled during recovery
Nov 21 08:43:20 arcane-X555LB kernel: [    2.069157] random: nonblocking pool is initialized
Nov 21 08:43:20 arcane-X555LB kernel: [    2.527034] Switched to clocksource tsc
Nov 21 08:43:20 arcane-X555LB kernel: [    3.477366] EXT4-fs (sda7): orphan cleanup on readonly fs
Nov 21 08:43:20 arcane-X555LB kernel: [    3.651697] EXT4-fs (sda7): 494 orphan inodes deleted
Nov 21 08:43:20 arcane-X555LB kernel: [    3.651701] EXT4-fs (sda7): recovery complete
Nov 21 08:43:20 arcane-X555LB kernel: [    3.883061] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
Nov  21 08:43:20 arcane-X555LB kernel: [    6.171592] Adding 8288252k swap  on /dev/sda8.  Priority:-1 extents:1 across:8288252k FS
Nov 21 08:43:20 arcane-X555LB kernel: [    7.441987] lp: driver loaded but no devices found
Nov 21 08:43:20 arcane-X555LB kernel: [    7.481817] ppdev: user-space parallel port driver
Nov 21 08:43:20 arcane-X555LB kernel: [    8.186182] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Nov 21 08:43:20 arcane-X555LB kernel: [    8.235841] wmi: Mapper loaded
Nov  21 08:43:20 arcane-X555LB kernel: [    8.238516] ACPI Warning:  0x0000000000001828-0x000000000000182f SystemIO conflicts with Region  \PMIO 1 (20131115/utaddress-251)
Nov 21 08:43:20 arcane-X555LB  kernel: [    8.238523] ACPI: If an ACPI driver is available for this  device, you should use it instead of the native driver
Nov 21  08:43:20 arcane-X555LB kernel: [    8.238541] ACPI Warning:  0x0000000000001c30-0x0000000000001c3f SystemIO conflicts with Region  \GPRL 1 (20131115/utaddress-251)
Nov 21 08:43:20 arcane-X555LB  kernel: [    8.238545] ACPI Warning:  0x0000000000001c30-0x0000000000001c3f SystemIO conflicts with Region  \GPR_ 2 (20131115/utaddress-251)
Nov 21 08:43:20 arcane-X555LB  kernel: [    8.238549] ACPI: If an ACPI driver is available for this  device, you should use it instead of the native driver
Nov 21  08:43:20 arcane-X555LB kernel: [    8.238551] ACPI Warning:  0x0000000000001c00-0x0000000000001c2f SystemIO conflicts with Region  \GPRL 1 (20131115/utaddress-251)
Nov 21 08:43:20 arcane-X555LB  kernel: [    8.238554] ACPI Warning:  0x0000000000001c00-0x0000000000001c2f SystemIO conflicts with Region  \GPR_ 2 (20131115/utaddress-251)
Nov 21 08:43:20 arcane-X555LB  kernel: [    8.238558] ACPI: If an ACPI driver is available for this  device, you should use it instead of the native driver
Nov 21 08:43:20 arcane-X555LB kernel: [    8.238559] lpc_ich: Resource conflict(s) found affecting gpio_ich
Nov 21 08:43:20 arcane-X555LB kernel: [    8.423103] mei_me 0000:00:16.0: irq 65 for MSI/MSI-X
Nov 21 08:43:20 arcane-X555LB kernel: [    8.832805] [drm] Initialized drm 1.1.0 20060810
Nov 21 08:43:20 arcane-X555LB kernel: [    8.879620] cfg80211: Calling CRDA to update world regulatory domain
Nov 21 08:43:20 arcane-X555LB kernel: [    8.984442] snd_hda_intel 0000:00:03.0: irq 66 for MSI/MSI-X
Nov  21 08:43:20 arcane-X555LB kernel: [    9.120383] mt7630e: module  verification failed: signature and/or  required key missing - tainting  kernel
Nov 21 08:43:20 arcane-X555LB kernel: [    9.121043]  ==>MT76x0_WLAN_ChipOnOff(): OnOff:1 pAd->WlanFunCtrl.word = 0x0,  Reg-WlanFunCtrl=0xff000202
Nov 21 08:43:20 arcane-X555LB kernel: [    9.121045] WlanFunCtrl.word = 0xffff0203
Nov 21 08:43:20 arcane-X555LB kernel: [    9.121097] MACVersion = 0x76502000
Nov  21 08:43:20 arcane-X555LB kernel: [    9.121104] <==  MT76x0_WLAN_ChipOnOff():  pAd->WlanFunCtrl.word = 0xffff0203,  Reg->WlanFunCtrl=0xffff0f03!
Nov 21 08:43:20 arcane-X555LB kernel: [    9.121112] MAC_version=0x76300002
Nov 21 08:43:20 arcane-X555LB kernel: [    9.121123] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 7630, rev 0002 detected
Nov 21 08:43:20 arcane-X555LB kernel: [    9.123012] MAC: 40:b8:9a:76:8a:17
Nov 21 08:43:20 arcane-X555LB kernel: [    9.123015] MAC_version=0x76300002
Nov 21 08:43:20 arcane-X555LB kernel: [    9.123016] RFIC =0x7630
Nov 21 08:43:20 arcane-X555LB kernel: [    9.123017] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 7630 detected
Nov 21 08:43:20 arcane-X555LB kernel: [    9.123018] rt2x00dev->chip.rt = 0x7630
Nov 21 08:43:20 arcane-X555LB kernel: [    9.123019] rt2x00dev->chip.rf = 0x7630
Nov 21 08:43:20 arcane-X555LB kernel: [    9.130269] asus_wmi: ASUS WMI generic driver loaded
Nov 21 08:43:20 arcane-X555LB kernel: [    9.133193] asus_wmi: Initialization: 0x1
Nov 21 08:43:20 arcane-X555LB kernel: [    9.133242] asus_wmi: BIOS WMI version: 7.9
Nov 21 08:43:20 arcane-X555LB kernel: [    9.133292] asus_wmi: SFUN value: 0xa0077
Nov 21 08:43:20 arcane-X555LB kernel: [    9.134512] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input12
Nov 21 08:43:20 arcane-X555LB kernel: [    9.134967] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
Nov 21 08:43:20 arcane-X555LB kernel: [    9.135796] -->RTMPAllocTxRxRingMemory
Nov 21 08:43:20 arcane-X555LB kernel: [    9.135800] CTRL Ring: total 512 bytes allocated
Nov 21 08:43:20 arcane-X555LB kernel: [    9.135802] <-- RTMPAllocTxRxRingMemory, Status=0
Nov 21 08:43:20 arcane-X555LB kernel: [    9.145478] asus_wmi: Backlight controlled by ACPI video driver
Nov 21 08:43:20 arcane-X555LB kernel: [    9.788990] ip_tables: (C) 2000-2006 Netfilter Core Team
Nov 21 08:43:20 arcane-X555LB kernel: [    9.992898] hda-intel 0000:00:03.0: Codec #0 probe error; disabling it...
Nov 21 08:43:20 arcane-X555LB kernel: [   10.006442] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Nov 21 08:43:20 arcane-X555LB kernel: [   10.269833] ip6_tables: (C) 2000-2006 Netfilter Core Team
Nov 21 08:43:20 arcane-X555LB kernel: [   10.374421] cfg80211: World regulatory domain updated:
Nov  21 08:43:20 arcane-X555LB kernel: [   10.374424] cfg80211:    (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov 21 08:43:20 arcane-X555LB kernel: [   10.374426] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:43:20 arcane-X555LB kernel: [   10.374428] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:43:20 arcane-X555LB kernel: [   10.374429] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:43:20 arcane-X555LB kernel: [   10.374430] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:43:20 arcane-X555LB kernel: [   10.374431] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:43:20 arcane-X555LB kernel: [   10.374571] cfg80211: Calling CRDA for country: US
Nov 21 08:43:20 arcane-X555LB kernel: [   10.376453] cfg80211: Regulatory domain changed to country: US
Nov  21 08:43:20 arcane-X555LB kernel: [   10.376456] cfg80211:    (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov 21 08:43:20 arcane-X555LB kernel: [   10.376457] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Nov 21 08:43:20 arcane-X555LB kernel: [   10.376459] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
Nov 21 08:43:20 arcane-X555LB kernel: [   10.376460] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:43:20 arcane-X555LB kernel: [   10.376461] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:43:20 arcane-X555LB kernel: [   10.376462] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 21 08:43:20 arcane-X555LB kernel: [   10.376463] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
Nov 21 08:43:20 arcane-X555LB kernel: [   10.376464] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
Nov 21 08:43:20 arcane-X555LB kernel: [   10.443310] Linux video capture interface: v2.00
Nov  21 08:43:20 arcane-X555LB kernel: [   10.482419] rts5139: module is  from the staging directory, the quality is unknown, you have been  warned.
Nov 21 08:43:20 arcane-X555LB kernel: [   10.483883] scsi4 : SCSI emulation for RTS5139 USB card reader
Nov 21 08:43:20 arcane-X555LB kernel: [   10.483962] usbcore: registered new interface driver rts5139
Nov  21 08:43:20 arcane-X555LB kernel: [   10.484000] scsi 4:0:0:0:  Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
Nov 21 08:43:20 arcane-X555LB kernel: [   10.484337] sd 4:0:0:0: Attached scsi generic sg2 type 0
Nov 21 08:43:20 arcane-X555LB kernel: [   10.564537] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Nov  21 08:43:20 arcane-X555LB kernel: [   10.701100] type=1400  audit(1448113394.603:2): apparmor="STATUS" operation="profile_load"  name="/sbin/dhclient" pid=468 comm="apparmor_parser"
Nov 21 08:43:20  arcane-X555LB kernel: [   10.701106] type=1400 audit(1448113394.603:3):  apparmor="STATUS" operation="profile_load"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=468  comm="apparmor_parser"
Nov 21 08:43:20 arcane-X555LB kernel: [    10.701109] type=1400 audit(1448113394.603:4): apparmor="STATUS"  operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script"  pid=468 comm="apparmor_parser"
Nov 21 08:43:20 arcane-X555LB kernel:  [   10.701322] type=1400 audit(1448113394.603:5): apparmor="STATUS"  operation="profile_replace" name="/sbin/dhclient" pid=393  comm="apparmor_parser"
Nov 21 08:43:20 arcane-X555LB kernel: [    10.701329] type=1400 audit(1448113394.603:6): apparmor="STATUS"  operation="profile_replace"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=393  comm="apparmor_parser"
Nov 21 08:43:20 arcane-X555LB kernel: [    10.701334] type=1400 audit(1448113394.603:7): apparmor="STATUS"  operation="profile_replace"  name="/usr/lib/connman/scripts/dhclient-script" pid=393  comm="apparmor_parser"
Nov 21 08:43:20 arcane-X555LB kernel: [    10.701342] type=1400 audit(1448113394.603:8): apparmor="STATUS"  operation="profile_replace" name="/sbin/dhclient" pid=394  comm="apparmor_parser"
Nov 21 08:43:20 arcane-X555LB kernel: [    10.701348] type=1400 audit(1448113394.603:9): apparmor="STATUS"  operation="profile_replace"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=394  comm="apparmor_parser"
Nov 21 08:43:20 arcane-X555LB kernel: [    10.701353] type=1400 audit(1448113394.603:10): apparmor="STATUS"  operation="profile_replace"  name="/usr/lib/connman/scripts/dhclient-script" pid=394  comm="apparmor_parser"
Nov 21 08:43:20 arcane-X555LB kernel: [    10.701426] type=1400 audit(1448113394.603:11): apparmor="STATUS"  operation="profile_replace"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=468  comm="apparmor_parser"
Nov 21 08:43:20 arcane-X555LB kernel: [   10.781312] uvcvideo: Found UVC 1.00 device USB Camera (0bda:57b5)
Nov  21 08:43:20 arcane-X555LB kernel: [   10.787276] input: USB Camera as  /devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5:1.0/input/input13
Nov 21 08:43:20 arcane-X555LB kernel: [   10.787349] usbcore: registered new interface driver uvcvideo
Nov 21 08:43:20 arcane-X555LB kernel: [   10.787351] USB Video Class driver (1.1.1)
Nov 21 08:43:20 arcane-X555LB kernel: [   11.809848] nvidia: module license 'NVIDIA' taints kernel.
Nov 21 08:43:20 arcane-X555LB kernel: [   11.809851] Disabling lock debugging due to kernel taint
Nov 21 08:43:20 arcane-X555LB kernel: [   11.815963] [drm] Initialized nvidia-drm 0.0.0 20150116 for 0000:04:00.0 on minor 0
Nov  21 08:43:20 arcane-X555LB kernel: [   11.815969] NVRM: loading NVIDIA  UNIX x86_64 Kernel Module  346.96  Sun Aug 23 22:29:21 PDT 2015
Nov 21 08:43:20 arcane-X555LB kernel: [   12.523199] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro
Nov 21 08:43:20 arcane-X555LB kernel: [   13.008109] hda-intel 0000:00:03.0: no codecs initialized
Nov 21 08:43:20 arcane-X555LB kernel: [   13.008381] snd_hda_intel 0000:00:1b.0: irq 66 for MSI/MSI-X
Nov 21 08:43:20 arcane-X555LB kernel: [   13.102365] asus_wmi: Unknown key cf pressed
Nov 21 08:43:20 arcane-X555LB kernel: [   13.483851] SKU: Nid=0x1d sku_cfg=0x40469b05
Nov 21 08:43:20 arcane-X555LB kernel: [   13.483854] SKU: port_connectivity=0x1
Nov 21 08:43:20 arcane-X555LB kernel: [   13.483855] SKU: enable_pcbeep=0x0
Nov 21 08:43:20 arcane-X555LB kernel: [   13.483856] SKU: check_sum=0x00000006
Nov 21 08:43:20 arcane-X555LB kernel: [   13.483857] SKU: customization=0x0000009b
Nov 21 08:43:20 arcane-X555LB kernel: [   13.483858] SKU: external_amp=0x0
Nov 21 08:43:20 arcane-X555LB kernel: [   13.483859] SKU: platform_type=0x1
Nov 21 08:43:20 arcane-X555LB kernel: [   13.483860] SKU: swap=0x0
Nov 21 08:43:20 arcane-X555LB kernel: [   13.483861] SKU: override=0x1
Nov 21 08:43:20 arcane-X555LB kernel: [   13.484036] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
Nov 21 08:43:20 arcane-X555LB kernel: [   13.484038]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
Nov 21 08:43:20 arcane-X555LB kernel: [   13.484040]    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
Nov 21 08:43:20 arcane-X555LB kernel: [   13.484041]    mono: mono_out=0x0
Nov 21 08:43:20 arcane-X555LB kernel: [   13.484042]    inputs:
Nov 21 08:43:20 arcane-X555LB kernel: [   13.484043]      Mic=0x1b
Nov 21 08:43:20 arcane-X555LB kernel: [   13.484045] realtek: No valid SSID, checking pincfg 0x40469b05 for NID 0x1d
Nov 21 08:43:20 arcane-X555LB kernel: [   13.484046] realtek: Enabling init ASM_ID=0x9b05 CODEC_ID=10ec0233
Nov  21 08:43:20 arcane-X555LB kernel: [   13.490670] input: HDA Intel PCH  Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
Nov 21 08:43:20 arcane-X555LB kernel: [   13.492970] [drm] Memory usable by graphics device = 2048M
Nov 21 08:43:20 arcane-X555LB kernel: [   13.492975] checking generic (b0000000 1e0000) vs hw (b0000000 10000000)
Nov 21 08:43:20 arcane-X555LB kernel: [   13.492977] fb: conflicting fb hw usage inteldrmfb vs EFI VGA - removing generic driver
Nov 21 08:43:20 arcane-X555LB kernel: [   13.493003] Console: switching to colour dummy device 80x25
Nov 21 08:43:20 arcane-X555LB kernel: [   13.544209] i915 0000:00:02.0: irq 67 for MSI/MSI-X
Nov 21 08:43:20 arcane-X555LB kernel: [   13.544219] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
Nov 21 08:43:20 arcane-X555LB kernel: [   13.544220] [drm] Driver supports precise vblank timestamp query.
Nov  21 08:43:20 arcane-X555LB kernel: [   13.596444]  [drm:__gen6_gt_force_wake_mt_get] *ERROR* Timed out waiting for  forcewake old ack to clear.
Nov 21 08:43:20 arcane-X555LB kernel: [   13.606914] fbcon: inteldrmfb (fb0) is primary device
Nov  21 08:43:20 arcane-X555LB kernel: [   15.191479]  [drm:intel_pipe_config_compare] *ERROR* mismatch in ips_enabled  (expected 1, found 0)
Nov 21 08:43:20 arcane-X555LB kernel: [   15.191480] ------------[ cut here ]------------
```


This  is what I got out of the kernel logs - I believe it was within that  time frame where the shut down occurred. It happened a few minutes after  waking it from suspend.

---

### Post by ian-weisser on 2015-11-21
When you reboot, the uptime resets to zero.
That's the easy way to tell in the logs when the restart occurred.

> **mistcloud-misty said:**
> ```

Nov 21 08:40:15 arcane-X555LB kernel: [389192.209108] [UFW BLOCK] IN=wlan0 OUT= MAC=40:b8:9a:76:8a:17:6c:71:d9:70:19:23:08:00 SRC=192.168.0.2 DST=192.168.0.17 LEN=56 TOS=0x00 PREC=0x00 TTL=128 ID=13391 PROTO=UDP SPT=63715 DPT=2054 LEN=36 
Nov 21 08:40:15 arcane-X555LB kernel: [389193.029666] [UFW BLOCK] IN=wlan0 OUT= MAC=33:33:00:00:00:01:48:5a:b6:f8:10:cd:86:dd SRC=fe80:0000:0000:0000:4a5a:b6ff:fef8:10cd DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=76 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
Nov 21 08:41:15 arcane-X555LB kernel: [389252.296364] [UFW BLOCK] IN=wlan0 OUT= MAC=40:b8:9a:76:8a:17:6c:71:d9:70:19:23:08:00 SRC=192.168.0.2 DST=192.168.0.17 LEN=56 TOS=0x00 PREC=0x00 TTL=128 ID=13405 PROTO=UDP SPT=62393 DPT=2054 LEN=36 
Nov 21 08:42:15 arcane-X555LB kernel: [389312.187907] [UFW BLOCK] IN=wlan0 OUT= MAC=40:b8:9a:76:8a:17:6c:71:d9:70:19:23:08:00 SRC=192.168.0.2 DST=192.168.0.17 LEN=56 TOS=0x00 PREC=0x00 TTL=128 ID=13419 PROTO=UDP SPT=57510 DPT=2054 LEN=36 
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Initializing cgroup subsys cpu
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Initializing cgroup subsys cpuacct
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Linux version 3.13.11-03131107-generic (apw@gomeisa) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #201409181736 SMP Thu Sep 18 21:37:41 UTC 2014
Nov 21 08:43:20 arcane-X555LB kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.11-03131107-generic root=UUID=b320ac20-ec61-42ec-8900-f1b181a2d24e ro noprompt persistent quiet splash acpi_osi= vt.handoff=7
```


So before the shutdown, network activity.
No unusual kernel activity.
Then 65 seconds of nothing (also not unusual).
Then restart.

Check your /var/log/syslog at that time for any messages from Power Manager or shutdown warnings.
If you don't find any logged shutdown warnings in syslog, then Ubuntu didn't shut down your system - hardware cut power, and took your OS completely by surprise.

---

### Post by mistcloud-misty on 2015-11-22
I don't see anything about power manager or even any shut down warnings in syslogs. 

My computer has yet to shut down again. This is a relatively new computer, and has not 'shut down' without warning before. If the hardware cut power, what are the 'possibilities' as to why so I can try and figure out what caused the problem?

---

### Post by tgalati4 on 2015-11-22
Was this computer mailed or shipped to you?  Sometimes new computers need a burn-in period to improve reliability.  Sometimes you need to tear them down and reseat and tighten all connections.  This is not easy to do.  Try a Live USB of the latest Ubuntu and see if things work properly.

Your log files show a stack dump in the graphics routines, so something about the i915 (Intel) driver is not happy.  Try turning it off in BIOS/UEFI.  Are you using open or proprietary nVidia drivers?

---

### Post by mistcloud-misty on 2015-11-22
The computer was shipped to me. Purchased it from Newegg and it is under warranty (though not sure if the warranty covers anything to do with a different operating system). 

I am using the Nvidia proprietary driver, closed source, which runs best with this kernel - something about open source nouveau made it black screen at login.

I will try turning it off in BIOS and see what happens while getting a USB installed with 15.10.

---

### Post by mistcloud-misty on 2015-11-22
Okay, in my BIOS there was only one option for Intel, and it was some intel acceleration thing which I disabled. Rebooted as normal, still have same kernel dumps but they don't particularly seem to effect anything and occur only at boot or suspend. The change didn't have any effect good or bad that I can see.

Now, I initially believed the problem was not due to overheating, because the laptop did not feel hot and I was doing less activity than usual (two tabs in chrome, 3 in firefox, 1 of them flash element).

However, I noticed when using flash in chrome my CPU for pappi (flash in Chrome) uses over 50% of my CPU and the temperature goes up to around 70+ C. I did some updates today that involved Nvidia (upgraded to closed source proprietary 252) and chrome is no longer taking such a huge impact on my PC or causing such a temperature rise. I still don't know if it's related (critical heat is 105 C according to lm-sensors).

Regardless, the random shut down has not recurred so it may have been a one time thing.

---

### Post by tgalati4 on 2015-11-22
I have seen new laptops that have been shipped with broken heat sinks--the plastic screws get cracked and they don't provide the 7 lbs of force required to transfer the heat.  The chip overheats and shuts down quickly.  Was the packaging damaged at all?  Random shutdowns need to be treated before the warranty period, otherwise you will end up with a computer that will continue to be unreliable and one where you will lose work with sudden shutdowns.

Keep an eye on your log files.

---

