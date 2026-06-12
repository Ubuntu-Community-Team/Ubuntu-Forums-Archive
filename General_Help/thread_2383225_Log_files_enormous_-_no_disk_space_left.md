---
title: "Log files enormous - no disk space left"
date: 2018-01-22
forum: General Help
---

### Post by hans12345 on 2018-01-22
I ran out of disk space. On checking I found my logs were using 154 GB.

I deleted 2 files, kern.log.1 and syslog.1, since these (kern and syslog) were the biggest
( using sudo rm /var/log/syslog.1)

Now I have (only!) 47 GB in my logs.

What is happening to my log files? It is a recent development.

I'm using a fully up to date Ubuntu 16.04 LTS

Any ideas?

---

### Post by Impavidus on 2018-01-22
Can you find any repeating messages in the log files?

You may not be able to open the log files with gedit or whatever your favourite text editer is. Try in a terminal:```
# To print the first 100 lines
head -n 100 /var/log/whatever

# To print the last 100 lines
tail -n 100 /var/log/whatever
```

---

### Post by hans12345 on 2018-01-22
Syslog head
```

family@Arctic:/var/log$ head -n 100 /var/log/syslog
Jan 22 07:14:06 Arctic kernel: [  665.517834] ------------[ cut here ]------------
Jan 22 07:14:06 Arctic kernel: [  665.517849] WARNING: CPU: 2 PID: 154 at /build/linux-8wXrCB/linux-4.4.0/drivers/usb/core/urb.c:449 usb_submit_urb.part.6+0x142/0x560()
Jan 22 07:14:06 Arctic kernel: [  665.517854] usb 1-5.2: BOGUS urb xfer, pipe 1 != type 3
Jan 22 07:14:06 Arctic kernel: [  665.517857] Modules linked in: drbg ansi_cprng ctr ccm bnep snd_hrtimer binfmt_misc arc4 ath9k_htc ath9k_common ath9k_hw eeepc_wmi ath mac80211 cfg80211 asus_wmi sparse_keymap intel_rapl snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic x86_pkg_temp_thermal intel_powerclamp coretemp kvm irqbypass crct10dif_pclmul crc32_pclmul snd_hda_intel snd_hda_codec ghash_clmulni_intel snd_hda_core input_leds serio_raw snd_hwdep snd_pcm aesni_intel hci_uart snd_seq_midi snd_seq_midi_event snd_rawmidi btbcm btqca acpi_als btintel aes_x86_64 lrw gf128mul glue_helper bluetooth snd_seq ablk_helper kfifo_buf 8250_fintek cryptd snd_seq_device snd_timer snd soundcore mei_me industrialio mei shpchp intel_lpss_acpi mac_hid intel_lpss acpi_pad parport_pc ppdev lp parport autofs4 uas usb_storage mxm_wmi i915_bpo intel_ips psmouse i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops r8169 mii drm ahci libahci wmi video pinctrl_sunrisepoint pinctrl_intel i2c_hid hid fjes
Jan 22 07:14:06 Arctic kernel: [  665.517971] CPU: 2 PID: 154 Comm: kworker/u8:5 Tainted: G        W       4.4.0-109-generic #132-Ubuntu
Jan 22 07:14:06 Arctic kernel: [  665.517975] Hardware name: System manufacturer System Product Name/PRIME B250M-A, BIOS 0614 04/18/2017
Jan 22 07:14:06 Arctic kernel: [  665.517987] Workqueue: phy0 ath9k_htc_ani_work [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  665.517991]  0000000000000286 449f8593b1cd3726 ffff880227e37b58 ffffffff813fbb03
Jan 22 07:14:06 Arctic kernel: [  665.517997]  ffff880227e37ba0 ffffffff81d52c80 ffff880227e37b90 ffffffff81081e52
Jan 22 07:14:06 Arctic kernel: [  665.518002]  ffff880227d30480 0000000000000002 ffff88022cd2f800 0000000000000001
Jan 22 07:14:06 Arctic kernel: [  665.518008] Call Trace:
Jan 22 07:14:06 Arctic kernel: [  665.518017]  [<ffffffff813fbb03>] dump_stack+0x63/0x90
Jan 22 07:14:06 Arctic kernel: [  665.518025]  [<ffffffff81081e52>] warn_slowpath_common+0x82/0xc0
Jan 22 07:14:06 Arctic kernel: [  665.518031]  [<ffffffff81081eec>] warn_slowpath_fmt+0x5c/0x80
Jan 22 07:14:06 Arctic kernel: [  665.518037]  [<ffffffff81629092>] usb_submit_urb.part.6+0x142/0x560
Jan 22 07:14:06 Arctic kernel: [  665.518042]  [<ffffffff81629512>] usb_submit_urb+0x62/0x70
Jan 22 07:14:06 Arctic kernel: [  665.518051]  [<ffffffffc07e3d8b>] hif_usb_send+0xeb/0x340 [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  665.518058]  [<ffffffffc07e2058>] htc_issue_send.constprop.2+0x58/0x70 [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  665.518065]  [<ffffffffc07e2428>] htc_send_epid+0x18/0x20 [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  665.518073]  [<ffffffffc07e5201>] ath9k_wmi_cmd+0x111/0x1a0 [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  665.518082]  [<ffffffffc07eacc0>] ath9k_regwrite+0x70/0x100 [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  665.518090]  [<ffffffffc068db73>] ath_hw_cycle_counters_update+0x33/0x130 [ath]
Jan 22 07:14:06 Arctic kernel: [  665.518097]  [<ffffffff8102d66c>] ? __switch_to+0x1dc/0x5c0
Jan 22 07:14:06 Arctic kernel: [  665.518118]  [<ffffffffc078b9b9>] ath9k_hw_ani_monitor+0x29/0x1c0 [ath9k_hw]
Jan 22 07:14:06 Arctic kernel: [  665.518126]  [<ffffffffc07e9b5d>] ath9k_htc_ani_work+0xcd/0x1a0 [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  665.518134]  [<ffffffff8109b1a5>] process_one_work+0x165/0x480
Jan 22 07:14:06 Arctic kernel: [  665.518140]  [<ffffffff8109b50b>] worker_thread+0x4b/0x4d0
Jan 22 07:14:06 Arctic kernel: [  665.518146]  [<ffffffff8109b4c0>] ? process_one_work+0x480/0x480
Jan 22 07:14:06 Arctic kernel: [  665.518151]  [<ffffffff810a1845>] kthread+0xe5/0x100
Jan 22 07:14:06 Arctic kernel: [  665.518156]  [<ffffffff810a1760>] ? kthread_create_on_node+0x1e0/0x1e0
Jan 22 07:14:06 Arctic kernel: [  665.518165]  [<ffffffff81844a0f>] ret_from_fork+0x3f/0x70
Jan 22 07:14:06 Arctic kernel: [  665.518169]  [<ffffffff810a1760>] ? kthread_create_on_node+0x1e0/0x1e0
Jan 22 07:14:06 Arctic kernel: [  665.518173] ---[ end trace 0ae99387ad275f9d ]---
Jan 22 07:14:06 Arctic kernel: [  665.519037] ------------[ cut here ]------------
Jan 22 07:14:06 Arctic kernel: [  665.519050] WARNING: CPU: 2 PID: 154 at /build/linux-8wXrCB/linux-4.4.0/drivers/usb/core/urb.c:449 usb_submit_urb.part.6+0x142/0x560()
Jan 22 07:14:06 Arctic kernel: [  665.519054] usb 1-5.2: BOGUS urb xfer, pipe 1 != type 3
Jan 22 07:14:06 Arctic kernel: [  665.519056] Modules linked in: drbg ansi_cprng ctr ccm bnep snd_hrtimer binfmt_misc arc4 ath9k_htc ath9k_common ath9k_hw eeepc_wmi ath mac80211 cfg80211 asus_wmi sparse_keymap intel_rapl snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic x86_pkg_temp_thermal intel_powerclamp coretemp kvm irqbypass crct10dif_pclmul crc32_pclmul snd_hda_intel snd_hda_codec ghash_clmulni_intel snd_hda_core input_leds serio_raw snd_hwdep snd_pcm aesni_intel hci_uart snd_seq_midi snd_seq_midi_event snd_rawmidi btbcm btqca acpi_als btintel aes_x86_64 lrw gf128mul glue_helper bluetooth snd_seq ablk_helper kfifo_buf 8250_fintek cryptd snd_seq_device snd_timer snd soundcore mei_me industrialio mei shpchp intel_lpss_acpi mac_hid intel_lpss acpi_pad parport_pc ppdev lp parport autofs4 uas usb_storage mxm_wmi i915_bpo intel_ips psmouse i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops r8169 mii drm ahci libahci wmi video pinctrl_sunrisepoint pinctrl_intel i2c_hid hid fjes
Jan 22 07:14:06 Arctic kernel: [  665.519158] CPU: 2 PID: 154 Comm: kworker/u8:5 Tainted: G        W       4.4.0-109-generic #132-Ubuntu
Jan 22 07:14:06 Arctic kernel: [  665.519162] Hardware name: System manufacturer System Product Name/PRIME B250M-A, BIOS 0614 04/18/2017
Jan 22 07:14:06 Arctic kernel: [  665.519173] Workqueue: phy0 ath9k_htc_ani_work [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  665.519176]  0000000000000286 449f8593b1cd3726 ffff880227e37b80 ffffffff813fbb03
Jan 22 07:14:06 Arctic kernel: [  665.519182]  ffff880227e37bc8 ffffffff81d52c80 ffff880227e37bb8 ffffffff81081e52
Jan 22 07:14:06 Arctic kernel: [  665.519187]  ffff880227d30480 0000000000000002 ffff88022cd2f800 0000000000000001
Jan 22 07:14:06 Arctic kernel: [  665.519193] Call Trace:
Jan 22 07:14:06 Arctic kernel: [  665.519201]  [<ffffffff813fbb03>] dump_stack+0x63/0x90
Jan 22 07:14:06 Arctic kernel: [  665.519208]  [<ffffffff81081e52>] warn_slowpath_common+0x82/0xc0
Jan 22 07:14:06 Arctic kernel: [  665.519213]  [<ffffffff81081eec>] warn_slowpath_fmt+0x5c/0x80
Jan 22 07:14:06 Arctic kernel: [  665.519219]  [<ffffffff81629092>] usb_submit_urb.part.6+0x142/0x560
Jan 22 07:14:06 Arctic kernel: [  665.519224]  [<ffffffff81629512>] usb_submit_urb+0x62/0x70
Jan 22 07:14:06 Arctic kernel: [  665.519233]  [<ffffffffc07e3d8b>] hif_usb_send+0xeb/0x340 [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  665.519240]  [<ffffffffc07e2058>] htc_issue_send.constprop.2+0x58/0x70 [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  665.519247]  [<ffffffffc07e2428>] htc_send_epid+0x18/0x20 [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  665.519255]  [<ffffffffc07e5201>] ath9k_wmi_cmd+0x111/0x1a0 [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  665.519264]  [<ffffffffc07eaacd>] ath9k_regread+0x4d/0x80 [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  665.519270]  [<ffffffffc068db84>] ath_hw_cycle_counters_update+0x44/0x130 [ath]
Jan 22 07:14:06 Arctic kernel: [  665.519276]  [<ffffffff8102d66c>] ? __switch_to+0x1dc/0x5c0
Jan 22 07:14:06 Arctic kernel: [  665.519297]  [<ffffffffc078b9b9>] ath9k_hw_ani_monitor+0x29/0x1c0 [ath9k_hw]
Jan 22 07:14:06 Arctic kernel: [  665.519305]  [<ffffffffc07e9b5d>] ath9k_htc_ani_work+0xcd/0x1a0 [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  665.519312]  [<ffffffff8109b1a5>] process_one_work+0x165/0x480
Jan 22 07:14:06 Arctic kernel: [  665.519318]  [<ffffffff8109b50b>] worker_thread+0x4b/0x4d0
Jan 22 07:14:06 Arctic kernel: [  665.519324]  [<ffffffff8109b4c0>] ? process_one_work+0x480/0x480
Jan 22 07:14:06 Arctic kernel: [  665.519329]  [<ffffffff810a1845>] kthread+0xe5/0x100
Jan 22 07:14:06 Arctic kernel: [  665.519334]  [<ffffffff810a1760>] ? kthread_create_on_node+0x1e0/0x1e0
Jan 22 07:14:06 Arctic kernel: [  665.519342]  [<ffffffff81844a0f>] ret_from_fork+0x3f/0x70
Jan 22 07:14:06 Arctic kernel: [  665.519347]  [<ffffffff810a1760>] ? kthread_create_on_node+0x1e0/0x1e0
Jan 22 07:14:06 Arctic kernel: [  665.519351] ---[ end trace 0ae99387ad275f9e ]---
Jan 22 07:14:06 Arctic kernel: [  665.521042] ------------[ cut here ]------------
Jan 22 07:14:06 Arctic kernel: [  665.521055] WARNING: CPU: 2 PID: 154 at /build/linux-8wXrCB/linux-4.4.0/drivers/usb/core/urb.c:449 usb_submit_urb.part.6+0x142/0x560()
Jan 22 07:14:06 Arctic kernel: [  665.521060] usb 1-5.2: BOGUS urb xfer, pipe 1 != type 3
Jan 22 07:14:06 Arctic kernel: [  665.521062] Modules linked in: drbg ansi_cprng ctr ccm bnep snd_hrtimer binfmt_misc arc4 ath9k_htc ath9k_common ath9k_hw eeepc_wmi ath mac80211 cfg80211 asus_wmi sparse_keymap intel_rapl snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic x86_pkg_temp_thermal intel_powerclamp coretemp kvm irqbypass crct10dif_pclmul crc32_pclmul snd_hda_intel snd_hda_codec ghash_clmulni_intel snd_hda_core input_leds serio_raw snd_hwdep snd_pcm aesni_intel hci_uart snd_seq_midi snd_seq_midi_event snd_rawmidi btbcm btqca acpi_als btintel aes_x86_64 lrw gf128mul glue_helper bluetooth snd_seq ablk_helper kfifo_buf 8250_fintek cryptd snd_seq_device snd_timer snd soundcore mei_me industrialio mei shpchp intel_lpss_acpi mac_hid intel_lpss acpi_pad parport_pc ppdev lp parport autofs4 uas usb_storage mxm_wmi i915_bpo intel_ips psmouse i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops r8169 mii drm ahci libahci wmi video pinctrl_sunrisepoint pinctrl_intel i2c_hid hid fjes
Jan 22 07:14:06 Arctic kernel: [  665.521163] CPU: 2 PID: 154 Comm: kworker/u8:5 Tainted: G        W       4.4.0-109-generic #132-Ubuntu
Jan 22 07:14:06 Arctic kernel: [  665.521167] Hardware name: System manufacturer System Product Name/PRIME B250M-A, BIOS 0614 04/18/2017
Jan 22 07:14:06 Arctic kernel: [  665.521178] Workqueue: phy0 ath9k_htc_ani_work [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  665.521181]  0000000000000286 449f8593b1cd3726 ffff880227e37b80 ffffffff813fbb03
Jan 22 07:14:06 Arctic kernel: [  665.521187]  ffff880227e37bc8 ffffffff81d52c80 ffff880227e37bb8 ffffffff81081e52
Jan 22 07:14:06 Arctic kernel: [  665.521193]  ffff880227d30480 0000000000000002 ffff88022cd2f800 0000000000000001
Jan 22 07:14:06 Arctic kernel: [  665.521198] Call Trace:
Jan 22 07:14:06 Arctic kernel: [  665.521206]  [<ffffffff813fbb03>] dump_stack+0x63/0x90
Jan 22 07:14:06 Arctic kernel: [  665.521213]  [<ffffffff81081e52>] warn_slowpath_common+0x82/0xc0
Jan 22 07:14:06 Arctic kernel: [  665.521219]  [<ffffffff81081eec>] warn_slowpath_fmt+0x5c/0x80
Jan 22 07:14:06 Arctic kernel: [  665.521224]  [<ffffffff810edd28>] ? del_timer_sync+0x48/0x50
Jan 22 07:14:06 Arctic kernel: [  665.521229]  [<ffffffff81629092>] usb_submit_urb.part.6+0x142/0x560
Jan 22 07:14:06 Arctic kernel: [  665.521234]  [<ffffffff81629512>] usb_submit_urb+0x62/0x70
Jan 22 07:14:06 Arctic kernel: [  665.521242]  [<ffffffffc07e3d8b>] hif_usb_send+0xeb/0x340 [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  665.521250]  [<ffffffffc07e2058>] htc_issue_send.constprop.2+0x58/0x70 [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  665.521257]  [<ffffffffc07e2428>] htc_send_epid+0x18/0x20 [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  665.521264]  [<ffffffffc07e5201>] ath9k_wmi_cmd+0x111/0x1a0 [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  665.521273]  [<ffffffffc07eaacd>] ath9k_regread+0x4d/0x80 [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  665.521280]  [<ffffffffc068db98>] ath_hw_cycle_counters_update+0x58/0x130 [ath]
Jan 22 07:14:06 Arctic kernel: [  665.521301]  [<ffffffffc078b9b9>] ath9k_hw_ani_monitor+0x29/0x1c0 [ath9k_hw]
Jan 22 07:14:06 Arctic kernel: [  665.521310]  [<ffffffffc07e9b5d>] ath9k_htc_ani_work+0xcd/0x1a0 [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  665.521316]  [<ffffffff8109b1a5>] process_one_work+0x165/0x480
Jan 22 07:14:06 Arctic kernel: [  665.521322]  [<ffffffff8109b50b>] worker_thread+0x4b/0x4d0
Jan 22 07:14:06 Arctic kernel: [  665.521328]  [<ffffffff8109b4c0>] ? process_one_work+0x480/0x480
Jan 22 07:14:06 Arctic kernel: [  665.521333]  [<ffffffff810a1845>] kthread+0xe5/0x100
Jan 22 07:14:06 Arctic kernel: [  665.521338]  [<ffffffff810a1760>] ? kthread_create_on_node+0x1e0/0x1e0
Jan 22 07:14:06 Arctic kernel: [  665.521346]  [<ffffffff81844a0f>] ret_from_fork+0x3f/0x70
Jan 22 07:14:06 Arctic kernel: [  665.521351]  [<ffffffff810a1760>] ? kthread_create_on_node+0x1e0/0x1e0
Jan 22 07:14:06 Arctic kernel: [  665.521355] ---[ end trace 0ae99387ad275f9f ]---
Jan 22 07:14:06 Arctic kernel: [  665.523015] ------------[ cut here ]------------
family@Arctic:/var/log$ 

```

Syslog Tail:
```
/var/log$ tail -n 100 /var/log/syslog
Jan 22 19:37:34 Arctic kernel: [45274.790582] Modules linked in: drbg ansi_cprng ctr ccm bnep snd_hrtimer binfmt_misc arc4 ath9k_htc ath9k_common ath9k_hw eeepc_wmi ath mac80211 cfg80211 asus_wmi sparse_keymap intel_rapl snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic x86_pkg_temp_thermal intel_powerclamp coretemp kvm irqbypass crct10dif_pclmul crc32_pclmul snd_hda_intel snd_hda_codec ghash_clmulni_intel snd_hda_core input_leds serio_raw snd_hwdep snd_pcm aesni_intel hci_uart snd_seq_midi snd_seq_midi_event snd_rawmidi btbcm btqca acpi_als btintel aes_x86_64 lrw gf128mul glue_helper bluetooth snd_seq ablk_helper kfifo_buf 8250_fintek cryptd snd_seq_device snd_timer snd soundcore mei_me industrialio mei shpchp intel_lpss_acpi mac_hid intel_lpss acpi_pad parport_pc ppdev lp parport autofs4 uas usb_storage mxm_wmi i915_bpo intel_ips psmouse i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops r8169 mii drm ahci libahci wmi video pinctrl_sunrisepoint pinctrl_intel i2c_hid hid fjes
Jan 22 19:37:34 Arctic kernel: [45274.790681] CPU: 2 PID: 10072 Comm: kworker/u8:2 Tainted: G        W       4.4.0-109-generic #132-Ubuntu
Jan 22 19:37:34 Arctic kernel: [45274.790684] Hardware name: System manufacturer System Product Name/PRIME B250M-A, BIOS 0614 04/18/2017
Jan 22 19:37:34 Arctic kernel: [45274.790693] Workqueue: phy1 ath9k_htc_ani_work [ath9k_htc]
Jan 22 19:37:34 Arctic kernel: [45274.790697]  0000000000000286 7dc096b668284c4a ffff88022a213b08 ffffffff813fbb03
Jan 22 19:37:34 Arctic kernel: [45274.790703]  ffff88022a213b50 ffffffff81d52c80 ffff88022a213b40 ffffffff81081e52
Jan 22 19:37:34 Arctic kernel: [45274.790708]  ffff88022bd2e000 0000000000000002 ffff8801ef11e800 0000000000000001
Jan 22 19:37:34 Arctic kernel: [45274.790713] Call Trace:
Jan 22 19:37:34 Arctic kernel: [45274.790720]  [<ffffffff813fbb03>] dump_stack+0x63/0x90
Jan 22 19:37:34 Arctic kernel: [45274.790726]  [<ffffffff81081e52>] warn_slowpath_common+0x82/0xc0
Jan 22 19:37:34 Arctic kernel: [45274.790732]  [<ffffffff81081eec>] warn_slowpath_fmt+0x5c/0x80
Jan 22 19:37:34 Arctic kernel: [45274.790737]  [<ffffffff810edd28>] ? del_timer_sync+0x48/0x50
Jan 22 19:37:34 Arctic kernel: [45274.790742]  [<ffffffff81629092>] usb_submit_urb.part.6+0x142/0x560
Jan 22 19:37:34 Arctic kernel: [45274.790746]  [<ffffffff81629512>] usb_submit_urb+0x62/0x70
Jan 22 19:37:34 Arctic kernel: [45274.790754]  [<ffffffffc07e3d8b>] hif_usb_send+0xeb/0x340 [ath9k_htc]
Jan 22 19:37:34 Arctic kernel: [45274.790762]  [<ffffffffc07e2058>] htc_issue_send.constprop.2+0x58/0x70 [ath9k_htc]
Jan 22 19:37:34 Arctic kernel: [45274.790769]  [<ffffffffc07e2428>] htc_send_epid+0x18/0x20 [ath9k_htc]
Jan 22 19:37:34 Arctic kernel: [45274.790776]  [<ffffffffc07e5201>] ath9k_wmi_cmd+0x111/0x1a0 [ath9k_htc]
Jan 22 19:37:34 Arctic kernel: [45274.790785]  [<ffffffffc07eadd3>] ath9k_reg_rmw+0x83/0x190 [ath9k_htc]
Jan 22 19:37:34 Arctic kernel: [45274.790802]  [<ffffffffc077c089>] ar5008_hw_ani_control_new+0x99/0x3c0 [ath9k_hw]
Jan 22 19:37:34 Arctic kernel: [45274.790810]  [<ffffffffc07e5262>] ? ath9k_wmi_cmd+0x172/0x1a0 [ath9k_htc]
Jan 22 19:37:34 Arctic kernel: [45274.790827]  [<ffffffffc078b707>] ath9k_hw_set_ofdm_nil+0x67/0x190 [ath9k_hw]
Jan 22 19:37:34 Arctic kernel: [45274.790842]  [<ffffffffc078bb2b>] ath9k_hw_ani_monitor+0x19b/0x1c0 [ath9k_hw]
Jan 22 19:37:34 Arctic kernel: [45274.790849]  [<ffffffffc07e9b5d>] ath9k_htc_ani_work+0xcd/0x1a0 [ath9k_htc]
Jan 22 19:37:34 Arctic kernel: [45274.790856]  [<ffffffff8109b1a5>] process_one_work+0x165/0x480
Jan 22 19:37:34 Arctic kernel: [45274.790862]  [<ffffffff8109b50b>] worker_thread+0x4b/0x4d0
Jan 22 19:37:34 Arctic kernel: [45274.790868]  [<ffffffff8109b4c0>] ? process_one_work+0x480/0x480
Jan 22 19:37:34 Arctic kernel: [45274.790873]  [<ffffffff810a1845>] kthread+0xe5/0x100
Jan 22 19:37:34 Arctic kernel: [45274.790878]  [<ffffffff810a1760>] ? kthread_create_on_node+0x1e0/0x1e0
Jan 22 19:37:34 Arctic kernel: [45274.790885]  [<ffffffff81844a0f>] ret_from_fork+0x3f/0x70
Jan 22 19:37:34 Arctic kernel: [45274.790889]  [<ffffffff810a1760>] ? kthread_create_on_node+0x1e0/0x1e0
Jan 22 19:37:34 Arctic kernel: [45274.790893] ---[ end trace 0ae99387ad8b9908 ]---
Jan 22 19:37:34 Arctic kernel: [45274.792576] ------------[ cut here ]------------
Jan 22 19:37:34 Arctic kernel: [45274.792591] WARNING: CPU: 2 PID: 10072 at /build/linux-8wXrCB/linux-4.4.0/drivers/usb/core/urb.c:449 usb_submit_urb.part.6+0x142/0x560()
Jan 22 19:37:34 Arctic kernel: [45274.792596] usb 1-5.2: BOGUS urb xfer, pipe 1 != type 3
Jan 22 19:37:34 Arctic kernel: [45274.792601] Modules linked in: drbg ansi_cprng ctr ccm bnep snd_hrtimer binfmt_misc arc4 ath9k_htc ath9k_common ath9k_hw eeepc_wmi ath mac80211 cfg80211 asus_wmi sparse_keymap intel_rapl snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic x86_pkg_temp_thermal intel_powerclamp coretemp kvm irqbypass crct10dif_pclmul crc32_pclmul snd_hda_intel snd_hda_codec ghash_clmulni_intel snd_hda_core input_leds serio_raw snd_hwdep snd_pcm aesni_intel hci_uart snd_seq_midi snd_seq_midi_event snd_rawmidi btbcm btqca acpi_als btintel aes_x86_64 lrw gf128mul glue_helper bluetooth snd_seq ablk_helper kfifo_buf 8250_fintek cryptd snd_seq_device snd_timer snd soundcore mei_me industrialio mei shpchp intel_lpss_acpi mac_hid intel_lpss acpi_pad parport_pc ppdev lp parport autofs4 uas usb_storage mxm_wmi i915_bpo intel_ips psmouse i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops r8169 mii drm ahci libahci wmi video pinctrl_sunrisepoint pinctrl_intel i2c_hid hid fjes
Jan 22 19:37:34 Arctic kernel: [45274.792754] CPU: 2 PID: 10072 Comm: kworker/u8:2 Tainted: G        W       4.4.0-109-generic #132-Ubuntu
Jan 22 19:37:34 Arctic kernel: [45274.792759] Hardware name: System manufacturer System Product Name/PRIME B250M-A, BIOS 0614 04/18/2017
Jan 22 19:37:34 Arctic kernel: [45274.792774] Workqueue: phy1 ath9k_htc_ani_work [ath9k_htc]
Jan 22 19:37:34 Arctic kernel: [45274.792779]  0000000000000286 7dc096b668284c4a ffff88022a213b80 ffffffff813fbb03
Jan 22 19:37:34 Arctic kernel: [45274.792790]  ffff88022a213bc8 ffffffff81d52c80 ffff88022a213bb8 ffffffff81081e52
Jan 22 19:37:34 Arctic kernel: [45274.792799]  ffff88022bd2e000 0000000000000002 ffff8801ef11e800 0000000000000001
Jan 22 19:37:34 Arctic kernel: [45274.792807] Call Trace:
Jan 22 19:37:34 Arctic kernel: [45274.792817]  [<ffffffff813fbb03>] dump_stack+0x63/0x90
Jan 22 19:37:34 Arctic kernel: [45274.792826]  [<ffffffff81081e52>] warn_slowpath_common+0x82/0xc0
Jan 22 19:37:34 Arctic kernel: [45274.792836]  [<ffffffff81081eec>] warn_slowpath_fmt+0x5c/0x80
Jan 22 19:37:34 Arctic kernel: [45274.792845]  [<ffffffff81629092>] usb_submit_urb.part.6+0x142/0x560
Jan 22 19:37:34 Arctic kernel: [45274.792853]  [<ffffffff81629512>] usb_submit_urb+0x62/0x70
Jan 22 19:37:34 Arctic kernel: [45274.792865]  [<ffffffffc07e3d8b>] hif_usb_send+0xeb/0x340 [ath9k_htc]
Jan 22 19:37:34 Arctic kernel: [45274.792876]  [<ffffffffc07e2058>] htc_issue_send.constprop.2+0x58/0x70 [ath9k_htc]
Jan 22 19:37:34 Arctic kernel: [45274.792889]  [<ffffffffc07e2428>] htc_send_epid+0x18/0x20 [ath9k_htc]
Jan 22 19:37:34 Arctic kernel: [45274.792901]  [<ffffffffc07e5201>] ath9k_wmi_cmd+0x111/0x1a0 [ath9k_htc]
Jan 22 19:37:34 Arctic kernel: [45274.792914]  [<ffffffffc07eabc3>] ath9k_regwrite_multi.isra.6+0x53/0x80 [ath9k_htc]
Jan 22 19:37:34 Arctic kernel: [45274.792924]  [<ffffffffc07eac36>] ath9k_regwrite_flush+0x46/0x60 [ath9k_htc]
Jan 22 19:37:34 Arctic kernel: [45274.792955]  [<ffffffffc078b678>] ath9k_ani_restart+0x78/0xa0 [ath9k_hw]
Jan 22 19:37:34 Arctic kernel: [45274.792978]  [<ffffffffc078ba75>] ath9k_hw_ani_monitor+0xe5/0x1c0 [ath9k_hw]
Jan 22 19:37:34 Arctic kernel: [45274.792988]  [<ffffffffc07e9b5d>] ath9k_htc_ani_work+0xcd/0x1a0 [ath9k_htc]
Jan 22 19:37:34 Arctic kernel: [45274.793000]  [<ffffffff8109b1a5>] process_one_work+0x165/0x480
Jan 22 19:37:34 Arctic kernel: [45274.793009]  [<ffffffff8109b50b>] worker_thread+0x4b/0x4d0
Jan 22 19:37:34 Arctic kernel: [45274.793017]  [<ffffffff8109b4c0>] ? process_one_work+0x480/0x480
Jan 22 19:37:34 Arctic kernel: [45274.793024]  [<ffffffff810a1845>] kthread+0xe5/0x100
Jan 22 19:37:34 Arctic kernel: [45274.793032]  [<ffffffff810a1760>] ? kthread_create_on_node+0x1e0/0x1e0
Jan 22 19:37:34 Arctic kernel: [45274.793043]  [<ffffffff81844a0f>] ret_from_fork+0x3f/0x70
Jan 22 19:37:34 Arctic kernel: [45274.793051]  [<ffffffff810a1760>] ? kthread_create_on_node+0x1e0/0x1e0
Jan 22 19:37:34 Arctic kernel: [45274.793057] ---[ end trace 0ae99387ad8b9909 ]---
Jan 22 19:37:34 Arctic kernel: [45274.794566] ------------[ cut here ]------------
Jan 22 19:37:34 Arctic kernel: [45274.794578] WARNING: CPU: 2 PID: 10072 at /build/linux-8wXrCB/linux-4.4.0/drivers/usb/core/urb.c:449 usb_submit_urb.part.6+0x142/0x560()
Jan 22 19:37:34 Arctic kernel: [45274.794584] usb 1-5.2: BOGUS urb xfer, pipe 1 != type 3
Jan 22 19:37:34 Arctic kernel: [45274.794587] Modules linked in: drbg ansi_cprng ctr ccm bnep snd_hrtimer binfmt_misc arc4 ath9k_htc ath9k_common ath9k_hw eeepc_wmi ath mac80211 cfg80211 asus_wmi sparse_keymap intel_rapl snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic x86_pkg_temp_thermal intel_powerclamp coretemp kvm irqbypass crct10dif_pclmul crc32_pclmul snd_hda_intel snd_hda_codec ghash_clmulni_intel snd_hda_core input_leds serio_raw snd_hwdep snd_pcm aesni_intel hci_uart snd_seq_midi snd_seq_midi_event snd_rawmidi btbcm btqca acpi_als btintel aes_x86_64 lrw gf128mul glue_helper bluetooth snd_seq ablk_helper kfifo_buf 8250_fintek cryptd snd_seq_device snd_timer snd soundcore mei_me industrialio mei shpchp intel_lpss_acpi mac_hid intel_lpss acpi_pad parport_pc ppdev lp parport autofs4 uas usb_storage mxm_wmi i915_bpo intel_ips psmouse i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops r8169 mii drm ahci libahci wmi video pinctrl_sunrisepoint pinctrl_intel i2c_hid hid fjes
Jan 22 19:37:34 Arctic kernel: [45274.794740] CPU: 2 PID: 10072 Comm: kworker/u8:2 Tainted: G        W       4.4.0-109-generic #132-Ubuntu
Jan 22 19:37:34 Arctic kernel: [45274.794745] Hardware name: System manufacturer System Product Name/PRIME B250M-A, BIOS 0614 04/18/2017
Jan 22 19:37:34 Arctic kernel: [45274.794759] Workqueue: phy1 ath9k_htc_ani_work [ath9k_htc]
Jan 22 19:37:34 Arctic kernel: [45274.794764]  0000000000000286 7dc096b668284c4a ffff88022a213b18 ffffffff813fbb03
Jan 22 19:37:34 Arctic kernel: [45274.794773]  ffff88022a213b60 ffffffff81d52c80 ffff88022a213b50 ffffffff81081e52
Jan 22 19:37:34 Arctic kernel: [45274.794782]  ffff88022bd2e000 0000000000000002 ffff8801ef11e800 0000000000000001
Jan 22 19:37:34 Arctic kernel: [45274.794790] Call Trace:
Jan 22 19:37:34 Arctic kernel: [45274.794799]  [<ffffffff813fbb03>] dump_stack+0x63/0x90
Jan 22 19:37:34 Arctic kernel: [45274.794808]  [<ffffffff81081e52>] warn_slowpath_common+0x82/0xc0
Jan 22 19:37:34 Arctic kernel: [45274.794816]  [<ffffffff81081eec>] warn_slowpath_fmt+0x5c/0x80
Jan 22 19:37:34 Arctic kernel: [45274.794825]  [<ffffffff810edba4>] ? lock_timer_base.isra.22+0x54/0x70
Jan 22 19:37:34 Arctic kernel: [45274.794839]  [<ffffffff81629092>] usb_submit_urb.part.6+0x142/0x560
Jan 22 19:37:34 Arctic kernel: [45274.794846]  [<ffffffff81629512>] usb_submit_urb+0x62/0x70
Jan 22 19:37:34 Arctic kernel: [45274.794859]  [<ffffffffc07e3d8b>] hif_usb_send+0xeb/0x340 [ath9k_htc]
Jan 22 19:37:34 Arctic kernel: [45274.794870]  [<ffffffffc07e2058>] htc_issue_send.constprop.2+0x58/0x70 [ath9k_htc]
Jan 22 19:37:34 Arctic kernel: [45274.794881]  [<ffffffffc07e2428>] htc_send_epid+0x18/0x20 [ath9k_htc]
Jan 22 19:37:34 Arctic kernel: [45274.794893]  [<ffffffffc07e5201>] ath9k_wmi_cmd+0x111/0x1a0 [ath9k_htc]
Jan 22 19:37:34 Arctic kernel: [45274.794905]  [<ffffffffc07eaa25>] ath9k_multi_regread+0x65/0xc0 [ath9k_htc]
Jan 22 19:37:34 Arctic kernel: [45274.794932]  [<ffffffffc078b5c3>] ath9k_hw_update_mibstats+0x53/0x90 [ath9k_hw]
Jan 22 19:37:34 Arctic kernel: [45274.794944]  [<ffffffffc07eac46>] ? ath9k_regwrite_flush+0x56/0x60 [ath9k_htc]
Jan 22 19:37:34 Arctic kernel: [45274.794968]  [<ffffffffc078b687>] ath9k_ani_restart+0x87/0xa0 [ath9k_hw]
Jan 22 19:37:34 Arctic kernel: [45274.794992]  [<ffffffffc078ba75>] ath9k_hw_ani_monitor+0xe5/0x1c0 [ath9k_hw]
Jan 22 19:37:34 Arctic kernel: [45274.795005]  [<ffffffffc07e9b5d>] ath9k_htc_ani_work+0xcd/0x1a0 [ath9k_htc]
Jan 22 19:37:34 Arctic kernel: [45274.795015]  [<ffffffff8109b1a5>] process_one_work+0x165/0x480
Jan 22 19:37:34 Arctic kernel: [45274.795023]  [<ffffffff8109b50b>] worker_thread+0x4b/0x4d0
Jan 22 19:37:34 Arctic kernel: [45274.795032]  [<ffffffff8109b4c0>] ? process_one_work+0x480/0x480
Jan 22 19:37:34 Arctic kernel: [45274.795039]  [<ffffffff810a1845>] kthread+0xe5/0x100
Jan 22 19:37:34 Arctic kernel: [45274.795047]  [<ffffffff810a1760>] ? kthread_create_on_node+0x1e0/0x1e0
Jan 22 19:37:34 Arctic kernel: [45274.795057]  [<ffffffff81844a0f>] ret_from_fork+0x3f/0x70
Jan 22 19:37:34 Arctic kernel: [45274.795065]  [<ffffffff810a1760>] ? kthread_create_on_node+0x1e0/0x1e0
Jan 22 19:37:34 Arctic kernel: [45274.795071] ---[ end trace 0ae99387ad8b990a ]---

```

---

### Post by Habitual on 2018-01-22
Were there any syslog.*N*.gz files present in /var/log?
It sounds like logrotate isn't working. Maybe you didn't allocate enough disk space on that partition? 

```
df -hT 
``` output may be needed, if it disk space.

```
ls -1 /var//log/syslog.*.gz

```will show you.

Here's what one looks like. You should have some of these as well.

```
/var/log/syslog
/var/log/syslog.1
/var/log/syslog.2.gz
/var/log/syslog.3.gz
/var/log/syslog.4.gz
/var/log/syslog.5.gz
/var/log/syslog.6.gz
/var/log/syslog.7.gz
```
*N*.gz is evidence of logrotate, and so  is .1 for that matter.

the contents of ```
/etc/logrotate.d/rsyslog
``` would be helpful says [https://askubuntu.com/questions/932049/has-etc-logrotate-d-rsyslog-moved](https://askubuntu.com/questions/932049/has-etc-logrotate-d-rsyslog-moved)

In an emergency situation, I usually issue _as root_
```
> /path/to/file
```to empty out the target but leave the perms etc as is. ;)

Some steps from  [https://fabianlee.org/2017/04/17/ubuntu-logrotate-for-retention-policy-of-logs/](https://fabianlee.org/2017/04/17/ubuntu-logrotate-for-retention-policy-of-logs/) may help you determine if logrotate is doing what is expected.

I wouldn't advise making any changes, just a recon for info.

Artic kernel. Void everything I said. :(
IDK a thing about that. But I have "suspicions" That "new" or did it come stock with the OS?

---

### Post by Yellow Pasque on 2018-01-22
It looks like an issue with the wireless adapter (ath9k_htc driver). 
[https://github.com/qca/open-ath9k-htc-firmware/wiki/usb-related-issues#bogus-urb-xfer-pipe-1--type-3](https://github.com/qca/open-ath9k-htc-firmware/wiki/usb-related-issues#bogus-urb-xfer-pipe-1--type-3)
Look at lsusb to make sure the USB controller is >= 2.0
```
lsusb
```

> **Habitual said:**
> Artic kernel. Void everything I said. :(
IDK a thing about that. But I have "suspicions" That "new" or did it come stock with the OS?

You're reading it wrong. Arctic is just the hostname. It looks like the stock Ubuntu kernel.

---

### Post by hans12345 on 2018-01-22
Here are are the logs BEFORE I started the deletions of kern and syslog. See how big the kern log is! I'll do a head/tail of kern in the next post.

```

/var/log$ dir -l
total 153030892
-rw-r--r-- 1 root              root            3628 janv. 19 07:43 alternatives.log
-rw-r--r-- 1 root              root             242 déc.   2 09:47 alternatives.log.1
-rw-r--r-- 1 root              root             377 nov.  28 07:40 alternatives.log.2.gz
-rw-r--r-- 1 root              root             532 oct.  28 08:58 alternatives.log.3.gz
-rw-r--r-- 1 root              root            1019 sept. 26 06:52 alternatives.log.4.gz
-rw-r--r-- 1 root              root            5002 août  19 21:42 alternatives.log.5.gz
drwxr-x--- 2 root              adm             4096 janv. 22 07:08 apache2
-rw-r----- 1 root              adm                0 janv. 22 07:08 apport.log
-rw-r----- 1 root              adm              979 janv. 22 07:04 apport.log.1
-rw-r----- 1 root              adm              226 janv. 21 06:41 apport.log.2.gz
-rw-r----- 1 root              adm              439 janv. 20 08:07 apport.log.3.gz
-rw-r----- 1 root              adm              301 janv. 19 07:20 apport.log.4.gz
-rw-r----- 1 root              adm              235 janv. 18 07:18 apport.log.5.gz
-rw-r----- 1 root              adm              226 janv. 17 07:35 apport.log.6.gz
-rw-r----- 1 root              adm              237 janv. 16 07:49 apport.log.7.gz
drwxr-xr-x 2 root              root            4096 janv.  8 15:19 apt
-rw-r----- 1 syslog            adm            18010 janv. 22 18:25 auth.log
-rw-r----- 1 syslog            adm           234555 janv. 22 07:07 auth.log.1
-rw-r----- 1 syslog            adm            15816 janv. 14 07:25 auth.log.2.gz
-rw-r----- 1 syslog            adm            10624 janv.  8 15:18 auth.log.3.gz
-rw-r----- 1 syslog            adm             9879 déc.   3 07:47 auth.log.4.gz
-rw-r--r-- 1 root              root            4303 janv. 22 07:03 boot.log
-rw-r--r-- 1 root              root           57457 avril 21  2016 bootstrap.log
-rw------- 1 root              utmp               0 janv.  8 15:19 btmp
-rw------- 1 root              utmp               0 déc.   1 07:14 btmp.1
drwxr-xr-x 2 root              root            4096 janv. 22 07:08 cups
drwxr-xr-x 2 root              root            4096 avril 16  2016 dist-upgrade
-rw-r----- 1 root              adm               31 avril 21  2016 dmesg
-rw-r--r-- 1 root              root          187840 janv. 19 07:44 dpkg.log
-rw-r--r-- 1 root              root           46359 déc.   8 17:33 dpkg.log.1
-rw-r--r-- 1 root              root           14312 nov.  30 16:49 dpkg.log.2.gz
-rw-r--r-- 1 root              root           12050 oct.  31 08:31 dpkg.log.3.gz
-rw-r--r-- 1 root              root           38811 sept. 26 06:53 dpkg.log.4.gz
-rw-r--r-- 1 root              root          156809 août  19 21:42 dpkg.log.5.gz
-rw-r--r-- 1 root              root           32032 nov.  26 11:51 faillog
-rw-r--r-- 1 root              root            4475 sept.  3 21:32 fontconfig.log
drwxr-xr-x 2 root              root            4096 avril 21  2016 fsck
-rw-r--r-- 1 root              root            1949 janv. 22 07:03 gpu-manager.log
drwxr-xr-x 3 root              root            4096 avril 21  2016 hp
drwxrwxr-x 2 root              root            4096 août  18 18:32 installer
-rw-r----- 1 syslog            adm      21504609326 janv. 22 18:26 kern.log
-rw-r----- 1 syslog            adm      82834691644 janv. 22 07:14 kern.log.1
-rw-r----- 1 syslog            adm           205286 janv. 14 07:21 kern.log.2.gz
-rw-r----- 1 syslog            adm           148566 janv.  8 15:14 kern.log.3.gz
-rw-r----- 1 syslog            adm           244907 déc.   3 07:47 kern.log.4.gz
-rw-rw-r-- 1 root              utmp          292292 nov.  26 11:51 lastlog
drwxr-xr-x 2 root              root            4096 janv. 22 07:08 lightdm
-rw-r--r-- 1 minidlna          minidlna           0 janv. 22 07:08 minidlna.log
-rw-r--r-- 1 minidlna          minidlna        2091 janv. 22 07:08 minidlna.log.1
-rw-r--r-- 1 minidlna          minidlna         403 janv. 14 07:25 minidlna.log.2.gz
-rw-r--r-- 1 minidlna          minidlna         325 janv.  8 15:19 minidlna.log.3.gz
-rw-r--r-- 1 minidlna          minidlna         563 déc.   3 07:52 minidlna.log.4.gz
drwxr-x--- 3 root              adm             4096 janv. 22 07:14 samba
drwx------ 2 speech-dispatcher root            4096 févr. 18  2016 speech-dispatcher
-rw-r----- 1 syslog            adm      21504944907 janv. 22 18:26 syslog
-rw-r----- 1 syslog            adm      27967886211 janv. 22 07:14 syslog.1
-rw-r----- 1 syslog            adm       1830915380 janv. 21 06:49 syslog.2.gz
-rw-r----- 1 syslog            adm       1058447722 janv. 20 08:11 syslog.3.gz
-rw-r----- 1 syslog            adm            70267 janv. 19 07:24 syslog.4.gz
-rw-r----- 1 syslog            adm            40741 janv. 18 07:22 syslog.5.gz
-rw-r----- 1 syslog            adm            38140 janv. 17 07:39 syslog.6.gz
-rw-r----- 1 syslog            adm            38782 janv. 16 07:53 syslog.7.gz
drwxr-xr-x 2 root              root            4096 mai   12  2016 sysstat
drwxr-x--- 2 root              adm             4096 août  18 19:30 unattended-upgrades
drwxr-xr-x 2 root              root            4096 févr. 29  2016 upstart
-rw-rw-r-- 1 root              utmp           49920 janv. 22 07:03 wtmp
-rw-rw-r-- 1 root              utmp           33792 janv.  8 15:14 wtmp.1
-rw-r--r-- 1 root              root           19707 janv. 22 07:03 Xorg.0.log
-rw-r--r-- 1 root              root           19707 janv. 21 06:40 Xorg.0.log.old

```

---

### Post by hans12345 on 2018-01-22
The current head and tail of kern.log:

```
/var/log$ head -n 100 /var/log/kern.log
Jan 22 07:14:06 Arctic kernel: [  665.981856] ------------[ cut here ]------------
Jan 22 07:14:06 Arctic kernel: [  665.981876] WARNING: CPU: 1 PID: 154 at /build/linux-8wXrCB/linux-4.4.0/drivers/usb/core/urb.c:449 usb_submit_urb.part.6+0x142/0x560()
Jan 22 07:14:06 Arctic kernel: [  665.981883] usb 1-5.2: BOGUS urb xfer, pipe 1 != type 3
Jan 22 07:14:06 Arctic kernel: [  665.981887] Modules linked in: drbg ansi_cprng ctr ccm bnep snd_hrtimer binfmt_misc arc4 ath9k_htc ath9k_common ath9k_hw eeepc_wmi ath mac80211 cfg80211 asus_wmi sparse_keymap intel_rapl snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic x86_pkg_temp_thermal intel_powerclamp coretemp kvm irqbypass crct10dif_pclmul crc32_pclmul snd_hda_intel snd_hda_codec ghash_clmulni_intel snd_hda_core input_leds serio_raw snd_hwdep snd_pcm aesni_intel hci_uart snd_seq_midi snd_seq_midi_event snd_rawmidi btbcm btqca acpi_als btintel aes_x86_64 lrw gf128mul glue_helper bluetooth snd_seq ablk_helper kfifo_buf 8250_fintek cryptd snd_seq_device snd_timer snd soundcore mei_me industrialio mei shpchp intel_lpss_acpi mac_hid intel_lpss acpi_pad parport_pc ppdev lp parport autofs4 uas usb_storage mxm_wmi i915_bpo intel_ips psmouse i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops r8169 mii drm ahci libahci wmi video pinctrl_sunrisepoint pinctrl_intel i2c_hid hid fjes
Jan 22 07:14:06 Arctic kernel: [  665.982046] CPU: 1 PID: 154 Comm: kworker/u8:5 Tainted: G        W       4.4.0-109-generic #132-Ubuntu
Jan 22 07:14:06 Arctic kernel: [  665.982052] Hardware name: System manufacturer System Product Name/PRIME B250M-A, BIOS 0614 04/18/2017
Jan 22 07:14:06 Arctic kernel: [  665.982067] Workqueue: phy0 ath9k_led_work [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  665.982073]  0000000000000286 449f8593b1cd3726 ffff880227e37bb8 ffffffff813fbb03
Jan 22 07:14:06 Arctic kernel: [  665.982082]  ffff880227e37c00 ffffffff81d52c80 ffff880227e37bf0 ffffffff81081e52
Jan 22 07:14:06 Arctic kernel: [  665.982091]  ffff8802026cb0c0 0000000000000002 ffff88022cd2f800 0000000000000001
Jan 22 07:14:06 Arctic kernel: [  665.982098] Call Trace:
Jan 22 07:14:06 Arctic kernel: [  665.982111]  [<ffffffff813fbb03>] dump_stack+0x63/0x90
Jan 22 07:14:06 Arctic kernel: [  665.982122]  [<ffffffff81081e52>] warn_slowpath_common+0x82/0xc0
Jan 22 07:14:06 Arctic kernel: [  665.982130]  [<ffffffff81081eec>] warn_slowpath_fmt+0x5c/0x80
Jan 22 07:14:06 Arctic kernel: [  665.982199]  [<ffffffffc070d2d9>] ? ieee80211_sta_rx_queued_mgmt+0xf9/0x670 [mac80211]
Jan 22 07:14:06 Arctic kernel: [  665.982208]  [<ffffffff81629092>] usb_submit_urb.part.6+0x142/0x560
Jan 22 07:14:06 Arctic kernel: [  665.982215]  [<ffffffff81629512>] usb_submit_urb+0x62/0x70
Jan 22 07:14:06 Arctic kernel: [  665.982228]  [<ffffffffc07e3d8b>] hif_usb_send+0xeb/0x340 [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  665.982240]  [<ffffffffc07e2058>] htc_issue_send.constprop.2+0x58/0x70 [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  665.982251]  [<ffffffffc07e2428>] htc_send_epid+0x18/0x20 [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  665.982263]  [<ffffffffc07e5201>] ath9k_wmi_cmd+0x111/0x1a0 [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  665.982277]  [<ffffffffc07eadd3>] ath9k_reg_rmw+0x83/0x190 [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  665.982303]  [<ffffffffc0775004>] ath9k_hw_set_gpio+0xd4/0xe0 [ath9k_hw]
Jan 22 07:14:06 Arctic kernel: [  665.982315]  [<ffffffffc07ebe2b>] ath9k_led_work+0x2b/0x30 [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  665.982326]  [<ffffffff8109b1a5>] process_one_work+0x165/0x480
Jan 22 07:14:06 Arctic kernel: [  665.982335]  [<ffffffff8109b50b>] worker_thread+0x4b/0x4d0
Jan 22 07:14:06 Arctic kernel: [  665.982344]  [<ffffffff8109b4c0>] ? process_one_work+0x480/0x480
Jan 22 07:14:06 Arctic kernel: [  665.982352]  [<ffffffff810a1845>] kthread+0xe5/0x100
Jan 22 07:14:06 Arctic kernel: [  665.982360]  [<ffffffff810a1760>] ? kthread_create_on_node+0x1e0/0x1e0
Jan 22 07:14:06 Arctic kernel: [  665.982371]  [<ffffffff81844a0f>] ret_from_fork+0x3f/0x70
Jan 22 07:14:06 Arctic kernel: [  665.982378]  [<ffffffff810a1760>] ? kthread_create_on_node+0x1e0/0x1e0
Jan 22 07:14:06 Arctic kernel: [  665.982385] ---[ end trace 0ae99387ad275fd6 ]---
Jan 22 07:14:06 Arctic kernel: [  666.021851] ------------[ cut here ]------------
Jan 22 07:14:06 Arctic kernel: [  666.021871] WARNING: CPU: 0 PID: 154 at /build/linux-8wXrCB/linux-4.4.0/drivers/usb/core/urb.c:449 usb_submit_urb.part.6+0x142/0x560()
Jan 22 07:14:06 Arctic kernel: [  666.021878] usb 1-5.2: BOGUS urb xfer, pipe 1 != type 3
Jan 22 07:14:06 Arctic kernel: [  666.021882] Modules linked in: drbg ansi_cprng ctr ccm bnep snd_hrtimer binfmt_misc arc4 ath9k_htc ath9k_common ath9k_hw eeepc_wmi ath mac80211 cfg80211 asus_wmi sparse_keymap intel_rapl snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic x86_pkg_temp_thermal intel_powerclamp coretemp kvm irqbypass crct10dif_pclmul crc32_pclmul snd_hda_intel snd_hda_codec ghash_clmulni_intel snd_hda_core input_leds serio_raw snd_hwdep snd_pcm aesni_intel hci_uart snd_seq_midi snd_seq_midi_event snd_rawmidi btbcm btqca acpi_als btintel aes_x86_64 lrw gf128mul glue_helper bluetooth snd_seq ablk_helper kfifo_buf 8250_fintek cryptd snd_seq_device snd_timer snd soundcore mei_me industrialio mei shpchp intel_lpss_acpi mac_hid intel_lpss acpi_pad parport_pc ppdev lp parport autofs4 uas usb_storage mxm_wmi i915_bpo intel_ips psmouse i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops r8169 mii drm ahci libahci wmi video pinctrl_sunrisepoint pinctrl_intel i2c_hid hid fjes
Jan 22 07:14:06 Arctic kernel: [  666.022047] CPU: 0 PID: 154 Comm: kworker/u8:5 Tainted: G        W       4.4.0-109-generic #132-Ubuntu
Jan 22 07:14:06 Arctic kernel: [  666.022052] Hardware name: System manufacturer System Product Name/PRIME B250M-A, BIOS 0614 04/18/2017
Jan 22 07:14:06 Arctic kernel: [  666.022068] Workqueue: phy0 ath9k_htc_ani_work [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  666.022074]  0000000000000286 449f8593b1cd3726 ffff880227e37b58 ffffffff813fbb03
Jan 22 07:14:06 Arctic kernel: [  666.022084]  ffff880227e37ba0 ffffffff81d52c80 ffff880227e37b90 ffffffff81081e52
Jan 22 07:14:06 Arctic kernel: [  666.022093]  ffff88020416ab40 0000000000000002 ffff88022cd2f800 0000000000000001
Jan 22 07:14:06 Arctic kernel: [  666.022101] Call Trace:
Jan 22 07:14:06 Arctic kernel: [  666.022114]  [<ffffffff813fbb03>] dump_stack+0x63/0x90
Jan 22 07:14:06 Arctic kernel: [  666.022124]  [<ffffffff81081e52>] warn_slowpath_common+0x82/0xc0
Jan 22 07:14:06 Arctic kernel: [  666.022133]  [<ffffffff81081eec>] warn_slowpath_fmt+0x5c/0x80
Jan 22 07:14:06 Arctic kernel: [  666.022142]  [<ffffffff810b423d>] ? attach_task_cfs_rq+0x3d/0x80
Jan 22 07:14:06 Arctic kernel: [  666.022150]  [<ffffffff81629092>] usb_submit_urb.part.6+0x142/0x560
Jan 22 07:14:06 Arctic kernel: [  666.022158]  [<ffffffff81629512>] usb_submit_urb+0x62/0x70
Jan 22 07:14:06 Arctic kernel: [  666.022171]  [<ffffffffc07e3d8b>] hif_usb_send+0xeb/0x340 [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  666.022183]  [<ffffffffc07e2058>] htc_issue_send.constprop.2+0x58/0x70 [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  666.022195]  [<ffffffffc07e2428>] htc_send_epid+0x18/0x20 [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  666.022208]  [<ffffffffc07e5201>] ath9k_wmi_cmd+0x111/0x1a0 [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  666.022221]  [<ffffffffc07eacc0>] ath9k_regwrite+0x70/0x100 [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  666.022232]  [<ffffffffc068db73>] ath_hw_cycle_counters_update+0x33/0x130 [ath]
Jan 22 07:14:06 Arctic kernel: [  666.022242]  [<ffffffff8102d66c>] ? __switch_to+0x1dc/0x5c0
Jan 22 07:14:06 Arctic kernel: [  666.022272]  [<ffffffffc078b9b9>] ath9k_hw_ani_monitor+0x29/0x1c0 [ath9k_hw]
Jan 22 07:14:06 Arctic kernel: [  666.022285]  [<ffffffffc07e9b5d>] ath9k_htc_ani_work+0xcd/0x1a0 [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  666.022295]  [<ffffffff8109b1a5>] process_one_work+0x165/0x480
Jan 22 07:14:06 Arctic kernel: [  666.022304]  [<ffffffff8109b50b>] worker_thread+0x4b/0x4d0
Jan 22 07:14:06 Arctic kernel: [  666.022313]  [<ffffffff8109b4c0>] ? process_one_work+0x480/0x480
Jan 22 07:14:06 Arctic kernel: [  666.022321]  [<ffffffff810a1845>] kthread+0xe5/0x100
Jan 22 07:14:06 Arctic kernel: [  666.022329]  [<ffffffff810a1760>] ? kthread_create_on_node+0x1e0/0x1e0
Jan 22 07:14:06 Arctic kernel: [  666.022341]  [<ffffffff81844a0f>] ret_from_fork+0x3f/0x70
Jan 22 07:14:06 Arctic kernel: [  666.022348]  [<ffffffff810a1760>] ? kthread_create_on_node+0x1e0/0x1e0
Jan 22 07:14:06 Arctic kernel: [  666.022354] ---[ end trace 0ae99387ad275fd7 ]---
Jan 22 07:14:06 Arctic kernel: [  666.023002] ------------[ cut here ]------------
Jan 22 07:14:06 Arctic kernel: [  666.023013] WARNING: CPU: 0 PID: 154 at /build/linux-8wXrCB/linux-4.4.0/drivers/usb/core/urb.c:449 usb_submit_urb.part.6+0x142/0x560()
Jan 22 07:14:06 Arctic kernel: [  666.023019] usb 1-5.2: BOGUS urb xfer, pipe 1 != type 3
Jan 22 07:14:06 Arctic kernel: [  666.023022] Modules linked in: drbg ansi_cprng ctr ccm bnep snd_hrtimer binfmt_misc arc4 ath9k_htc ath9k_common ath9k_hw eeepc_wmi ath mac80211 cfg80211 asus_wmi sparse_keymap intel_rapl snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic x86_pkg_temp_thermal intel_powerclamp coretemp kvm irqbypass crct10dif_pclmul crc32_pclmul snd_hda_intel snd_hda_codec ghash_clmulni_intel snd_hda_core input_leds serio_raw snd_hwdep snd_pcm aesni_intel hci_uart snd_seq_midi snd_seq_midi_event snd_rawmidi btbcm btqca acpi_als btintel aes_x86_64 lrw gf128mul glue_helper bluetooth snd_seq ablk_helper kfifo_buf 8250_fintek cryptd snd_seq_device snd_timer snd soundcore mei_me industrialio mei shpchp intel_lpss_acpi mac_hid intel_lpss acpi_pad parport_pc ppdev lp parport autofs4 uas usb_storage mxm_wmi i915_bpo intel_ips psmouse i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops r8169 mii drm ahci libahci wmi video pinctrl_sunrisepoint pinctrl_intel i2c_hid hid fjes
Jan 22 07:14:06 Arctic kernel: [  666.023172] CPU: 0 PID: 154 Comm: kworker/u8:5 Tainted: G        W       4.4.0-109-generic #132-Ubuntu
Jan 22 07:14:06 Arctic kernel: [  666.023177] Hardware name: System manufacturer System Product Name/PRIME B250M-A, BIOS 0614 04/18/2017
Jan 22 07:14:06 Arctic kernel: [  666.023190] Workqueue: phy0 ath9k_htc_ani_work [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  666.023195]  0000000000000286 449f8593b1cd3726 ffff880227e37b80 ffffffff813fbb03
Jan 22 07:14:06 Arctic kernel: [  666.023205]  ffff880227e37bc8 ffffffff81d52c80 ffff880227e37bb8 ffffffff81081e52
Jan 22 07:14:06 Arctic kernel: [  666.023213]  ffff88020416ae40 0000000000000002 ffff88022cd2f800 0000000000000001
Jan 22 07:14:06 Arctic kernel: [  666.023221] Call Trace:
Jan 22 07:14:06 Arctic kernel: [  666.023230]  [<ffffffff813fbb03>] dump_stack+0x63/0x90
Jan 22 07:14:06 Arctic kernel: [  666.023240]  [<ffffffff81081e52>] warn_slowpath_common+0x82/0xc0
Jan 22 07:14:06 Arctic kernel: [  666.023248]  [<ffffffff81081eec>] warn_slowpath_fmt+0x5c/0x80
Jan 22 07:14:06 Arctic kernel: [  666.023257]  [<ffffffff81629092>] usb_submit_urb.part.6+0x142/0x560
Jan 22 07:14:06 Arctic kernel: [  666.023265]  [<ffffffff81629512>] usb_submit_urb+0x62/0x70
Jan 22 07:14:06 Arctic kernel: [  666.023277]  [<ffffffffc07e3d8b>] hif_usb_send+0xeb/0x340 [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  666.023289]  [<ffffffffc07e2058>] htc_issue_send.constprop.2+0x58/0x70 [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  666.023301]  [<ffffffffc07e2428>] htc_send_epid+0x18/0x20 [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  666.023313]  [<ffffffffc07e5201>] ath9k_wmi_cmd+0x111/0x1a0 [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  666.023325]  [<ffffffffc07eaacd>] ath9k_regread+0x4d/0x80 [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  666.023337]  [<ffffffffc068db84>] ath_hw_cycle_counters_update+0x44/0x130 [ath]
Jan 22 07:14:06 Arctic kernel: [  666.023345]  [<ffffffff8102d66c>] ? __switch_to+0x1dc/0x5c0
Jan 22 07:14:06 Arctic kernel: [  666.023375]  [<ffffffffc078b9b9>] ath9k_hw_ani_monitor+0x29/0x1c0 [ath9k_hw]
Jan 22 07:14:06 Arctic kernel: [  666.023387]  [<ffffffffc07e9b5d>] ath9k_htc_ani_work+0xcd/0x1a0 [ath9k_htc]
Jan 22 07:14:06 Arctic kernel: [  666.023397]  [<ffffffff8109b1a5>] process_one_work+0x165/0x480
Jan 22 07:14:06 Arctic kernel: [  666.023405]  [<ffffffff8109b50b>] worker_thread+0x4b/0x4d0
Jan 22 07:14:06 Arctic kernel: [  666.023413]  [<ffffffff8109b4c0>] ? process_one_work+0x480/0x480
Jan 22 07:14:06 Arctic kernel: [  666.023420]  [<ffffffff810a1845>] kthread+0xe5/0x100
Jan 22 07:14:06 Arctic kernel: [  666.023427]  [<ffffffff810a1760>] ? kthread_create_on_node+0x1e0/0x1e0
Jan 22 07:14:06 Arctic kernel: [  666.023437]  [<ffffffff81844a0f>] ret_from_fork+0x3f/0x70
Jan 22 07:14:06 Arctic kernel: [  666.023444]  [<ffffffff810a1760>] ? kthread_create_on_node+0x1e0/0x1e0
Jan 22 07:14:06 Arctic kernel: [  666.023449] ---[ end trace 0ae99387ad275fd8 ]---
Jan 22 07:14:06 Arctic kernel: [  666.025011] ------------[ cut here ]------------


```

Tail:

```

/var/log$ tail -n 100 /var/log/kern.log
Jan 22 22:58:39 Arctic kernel: [57339.631598]  [<ffffffff81844a0f>] ret_from_fork+0x3f/0x70
Jan 22 22:58:39 Arctic kernel: [57339.631603]  [<ffffffff810a1760>] ? kthread_create_on_node+0x1e0/0x1e0
Jan 22 22:58:39 Arctic kernel: [57339.631607] ---[ end trace 0ae99387ada64f54 ]---
Jan 22 22:58:39 Arctic kernel: [57339.633298] ------------[ cut here ]------------
Jan 22 22:58:39 Arctic kernel: [57339.633311] WARNING: CPU: 3 PID: 10930 at /build/linux-8wXrCB/linux-4.4.0/drivers/usb/core/urb.c:449 usb_submit_urb.part.6+0x142/0x560()
Jan 22 22:58:39 Arctic kernel: [57339.633316] usb 1-5.2: BOGUS urb xfer, pipe 1 != type 3
Jan 22 22:58:39 Arctic kernel: [57339.633318] Modules linked in: drbg ansi_cprng ctr ccm bnep snd_hrtimer binfmt_misc arc4 ath9k_htc ath9k_common ath9k_hw eeepc_wmi ath mac80211 cfg80211 asus_wmi sparse_keymap intel_rapl snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic x86_pkg_temp_thermal intel_powerclamp coretemp kvm irqbypass crct10dif_pclmul crc32_pclmul snd_hda_intel snd_hda_codec ghash_clmulni_intel snd_hda_core input_leds serio_raw snd_hwdep snd_pcm aesni_intel hci_uart snd_seq_midi snd_seq_midi_event snd_rawmidi btbcm btqca acpi_als btintel aes_x86_64 lrw gf128mul glue_helper bluetooth snd_seq ablk_helper kfifo_buf 8250_fintek cryptd snd_seq_device snd_timer snd soundcore mei_me industrialio mei shpchp intel_lpss_acpi mac_hid intel_lpss acpi_pad parport_pc ppdev lp parport autofs4 uas usb_storage mxm_wmi i915_bpo intel_ips psmouse i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops r8169 mii drm ahci libahci wmi video pinctrl_sunrisepoint pinctrl_intel i2c_hid hid fjes
Jan 22 22:58:39 Arctic kernel: [57339.633420] CPU: 3 PID: 10930 Comm: kworker/u8:3 Tainted: G        W       4.4.0-109-generic #132-Ubuntu
Jan 22 22:58:39 Arctic kernel: [57339.633423] Hardware name: System manufacturer System Product Name/PRIME B250M-A, BIOS 0614 04/18/2017
Jan 22 22:58:39 Arctic kernel: [57339.633434] Workqueue: phy1 ath9k_htc_ani_work [ath9k_htc]
Jan 22 22:58:39 Arctic kernel: [57339.633438]  0000000000000286 9a8209db5a7f35de ffff88022a213b30 ffffffff813fbb03
Jan 22 22:58:39 Arctic kernel: [57339.633444]  ffff88022a213b78 ffffffff81d52c80 ffff88022a213b68 ffffffff81081e52
Jan 22 22:58:39 Arctic kernel: [57339.633450]  ffff8802026cd240 0000000000000002 ffff8801ef11e800 0000000000000001
Jan 22 22:58:39 Arctic kernel: [57339.633455] Call Trace:
Jan 22 22:58:39 Arctic kernel: [57339.633463]  [<ffffffff813fbb03>] dump_stack+0x63/0x90
Jan 22 22:58:39 Arctic kernel: [57339.633470]  [<ffffffff81081e52>] warn_slowpath_common+0x82/0xc0
Jan 22 22:58:39 Arctic kernel: [57339.633475]  [<ffffffff81081eec>] warn_slowpath_fmt+0x5c/0x80
Jan 22 22:58:39 Arctic kernel: [57339.633480]  [<ffffffff810edcae>] ? try_to_del_timer_sync+0x5e/0x90
Jan 22 22:58:39 Arctic kernel: [57339.633486]  [<ffffffff81629092>] usb_submit_urb.part.6+0x142/0x560
Jan 22 22:58:39 Arctic kernel: [57339.633491]  [<ffffffff81629512>] usb_submit_urb+0x62/0x70
Jan 22 22:58:39 Arctic kernel: [57339.633499]  [<ffffffffc07e3d8b>] hif_usb_send+0xeb/0x340 [ath9k_htc]
Jan 22 22:58:39 Arctic kernel: [57339.633507]  [<ffffffffc07e2058>] htc_issue_send.constprop.2+0x58/0x70 [ath9k_htc]
Jan 22 22:58:39 Arctic kernel: [57339.633514]  [<ffffffffc07e2428>] htc_send_epid+0x18/0x20 [ath9k_htc]
Jan 22 22:58:39 Arctic kernel: [57339.633522]  [<ffffffffc07e5201>] ath9k_wmi_cmd+0x111/0x1a0 [ath9k_htc]
Jan 22 22:58:39 Arctic kernel: [57339.633531]  [<ffffffffc07eaa25>] ath9k_multi_regread+0x65/0xc0 [ath9k_htc]
Jan 22 22:58:39 Arctic kernel: [57339.633538]  [<ffffffffc07eacc0>] ? ath9k_regwrite+0x70/0x100 [ath9k_htc]
Jan 22 22:58:39 Arctic kernel: [57339.633559]  [<ffffffffc078b5c3>] ath9k_hw_update_mibstats+0x53/0x90 [ath9k_hw]
Jan 22 22:58:39 Arctic kernel: [57339.633577]  [<ffffffffc078b9de>] ath9k_hw_ani_monitor+0x4e/0x1c0 [ath9k_hw]
Jan 22 22:58:39 Arctic kernel: [57339.633585]  [<ffffffffc07e9b5d>] ath9k_htc_ani_work+0xcd/0x1a0 [ath9k_htc]
Jan 22 22:58:39 Arctic kernel: [57339.633592]  [<ffffffff8109b1a5>] process_one_work+0x165/0x480
Jan 22 22:58:39 Arctic kernel: [57339.633598]  [<ffffffff8109b50b>] worker_thread+0x4b/0x4d0
Jan 22 22:58:39 Arctic kernel: [57339.633604]  [<ffffffff8109b4c0>] ? process_one_work+0x480/0x480
Jan 22 22:58:39 Arctic kernel: [57339.633609]  [<ffffffff810a1845>] kthread+0xe5/0x100
Jan 22 22:58:39 Arctic kernel: [57339.633614]  [<ffffffff810a1760>] ? kthread_create_on_node+0x1e0/0x1e0
Jan 22 22:58:39 Arctic kernel: [57339.633621]  [<ffffffff81844a0f>] ret_from_fork+0x3f/0x70
Jan 22 22:58:39 Arctic kernel: [57339.633626]  [<ffffffff810a1760>] ? kthread_create_on_node+0x1e0/0x1e0
Jan 22 22:58:39 Arctic kernel: [57339.633630] ---[ end trace 0ae99387ada64f55 ]---
Jan 22 22:58:39 Arctic kernel: [57339.635292] ------------[ cut here ]------------
Jan 22 22:58:39 Arctic kernel: [57339.635305] WARNING: CPU: 3 PID: 10930 at /build/linux-8wXrCB/linux-4.4.0/drivers/usb/core/urb.c:449 usb_submit_urb.part.6+0x142/0x560()
Jan 22 22:58:39 Arctic kernel: [57339.635310] usb 1-5.2: BOGUS urb xfer, pipe 1 != type 3
Jan 22 22:58:39 Arctic kernel: [57339.635314] Modules linked in: drbg ansi_cprng ctr ccm bnep snd_hrtimer binfmt_misc arc4 ath9k_htc ath9k_common ath9k_hw eeepc_wmi ath mac80211 cfg80211 asus_wmi sparse_keymap intel_rapl snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic x86_pkg_temp_thermal intel_powerclamp coretemp kvm irqbypass crct10dif_pclmul crc32_pclmul snd_hda_intel snd_hda_codec ghash_clmulni_intel snd_hda_core input_leds serio_raw snd_hwdep snd_pcm aesni_intel hci_uart snd_seq_midi snd_seq_midi_event snd_rawmidi btbcm btqca acpi_als btintel aes_x86_64 lrw gf128mul glue_helper bluetooth snd_seq ablk_helper kfifo_buf 8250_fintek cryptd snd_seq_device snd_timer snd soundcore mei_me industrialio mei shpchp intel_lpss_acpi mac_hid intel_lpss acpi_pad parport_pc ppdev lp parport autofs4 uas usb_storage mxm_wmi i915_bpo intel_ips psmouse i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops r8169 mii drm ahci libahci wmi video pinctrl_sunrisepoint pinctrl_intel i2c_hid hid fjes
Jan 22 22:58:39 Arctic kernel: [57339.635424] CPU: 3 PID: 10930 Comm: kworker/u8:3 Tainted: G        W       4.4.0-109-generic #132-Ubuntu
Jan 22 22:58:39 Arctic kernel: [57339.635428] Hardware name: System manufacturer System Product Name/PRIME B250M-A, BIOS 0614 04/18/2017
Jan 22 22:58:39 Arctic kernel: [57339.635442] Workqueue: phy1 ath9k_htc_ani_work [ath9k_htc]
Jan 22 22:58:39 Arctic kernel: [57339.635446]  0000000000000286 9a8209db5a7f35de ffff88022a213bc0 ffffffff813fbb03
Jan 22 22:58:39 Arctic kernel: [57339.635452]  ffff88022a213c08 ffffffff81d52c80 ffff88022a213bf8 ffffffff81081e52
Jan 22 22:58:39 Arctic kernel: [57339.635459]  ffff8802026cda80 0000000000000002 ffff8801ef11e800 0000000000000001
Jan 22 22:58:39 Arctic kernel: [57339.635465] Call Trace:
Jan 22 22:58:39 Arctic kernel: [57339.635473]  [<ffffffff813fbb03>] dump_stack+0x63/0x90
Jan 22 22:58:39 Arctic kernel: [57339.635480]  [<ffffffff81081e52>] warn_slowpath_common+0x82/0xc0
Jan 22 22:58:39 Arctic kernel: [57339.635486]  [<ffffffff81081eec>] warn_slowpath_fmt+0x5c/0x80
Jan 22 22:58:39 Arctic kernel: [57339.635494]  [<ffffffff81629092>] usb_submit_urb.part.6+0x142/0x560
Jan 22 22:58:39 Arctic kernel: [57339.635499]  [<ffffffff81629512>] usb_submit_urb+0x62/0x70
Jan 22 22:58:39 Arctic kernel: [57339.635507]  [<ffffffffc07e3d8b>] hif_usb_send+0xeb/0x340 [ath9k_htc]
Jan 22 22:58:39 Arctic kernel: [57339.635514]  [<ffffffffc07e2058>] htc_issue_send.constprop.2+0x58/0x70 [ath9k_htc]
Jan 22 22:58:39 Arctic kernel: [57339.635522]  [<ffffffffc07e2428>] htc_send_epid+0x18/0x20 [ath9k_htc]
Jan 22 22:58:39 Arctic kernel: [57339.635532]  [<ffffffffc07e5201>] ath9k_wmi_cmd+0x111/0x1a0 [ath9k_htc]
Jan 22 22:58:39 Arctic kernel: [57339.635541]  [<ffffffffc07eaacd>] ath9k_regread+0x4d/0x80 [ath9k_htc]
Jan 22 22:58:39 Arctic kernel: [57339.635562]  [<ffffffffc078b9e8>] ath9k_hw_ani_monitor+0x58/0x1c0 [ath9k_hw]
Jan 22 22:58:39 Arctic kernel: [57339.635571]  [<ffffffffc07e9b5d>] ath9k_htc_ani_work+0xcd/0x1a0 [ath9k_htc]
Jan 22 22:58:39 Arctic kernel: [57339.635580]  [<ffffffff8109b1a5>] process_one_work+0x165/0x480
Jan 22 22:58:39 Arctic kernel: [57339.635586]  [<ffffffff8109b50b>] worker_thread+0x4b/0x4d0
Jan 22 22:58:39 Arctic kernel: [57339.635592]  [<ffffffff8109b4c0>] ? process_one_work+0x480/0x480
Jan 22 22:58:39 Arctic kernel: [57339.635597]  [<ffffffff810a1845>] kthread+0xe5/0x100
Jan 22 22:58:39 Arctic kernel: [57339.635603]  [<ffffffff810a1760>] ? kthread_create_on_node+0x1e0/0x1e0
Jan 22 22:58:39 Arctic kernel: [57339.635612]  [<ffffffff81844a0f>] ret_from_fork+0x3f/0x70
Jan 22 22:58:39 Arctic kernel: [57339.635617]  [<ffffffff810a1760>] ? kthread_create_on_node+0x1e0/0x1e0
Jan 22 22:58:39 Arctic kernel: [57339.635621] ---[ end trace 0ae99387ada64f56 ]---
Jan 22 22:58:39 Arctic kernel: [57339.637304] ------------[ cut here ]------------
Jan 22 22:58:39 Arctic kernel: [57339.637316] WARNING: CPU: 3 PID: 10930 at /build/linux-8wXrCB/linux-4.4.0/drivers/usb/core/urb.c:449 usb_submit_urb.part.6+0x142/0x560()
Jan 22 22:58:39 Arctic kernel: [57339.637321] usb 1-5.2: BOGUS urb xfer, pipe 1 != type 3
Jan 22 22:58:39 Arctic kernel: [57339.637324] Modules linked in: drbg ansi_cprng ctr ccm bnep snd_hrtimer binfmt_misc arc4 ath9k_htc ath9k_common ath9k_hw eeepc_wmi ath mac80211 cfg80211 asus_wmi sparse_keymap intel_rapl snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic x86_pkg_temp_thermal intel_powerclamp coretemp kvm irqbypass crct10dif_pclmul crc32_pclmul snd_hda_intel snd_hda_codec ghash_clmulni_intel snd_hda_core input_leds serio_raw snd_hwdep snd_pcm aesni_intel hci_uart snd_seq_midi snd_seq_midi_event snd_rawmidi btbcm btqca acpi_als btintel aes_x86_64 lrw gf128mul glue_helper bluetooth snd_seq ablk_helper kfifo_buf 8250_fintek cryptd snd_seq_device snd_timer snd soundcore mei_me industrialio mei shpchp intel_lpss_acpi mac_hid intel_lpss acpi_pad parport_pc ppdev lp parport autofs4 uas usb_storage mxm_wmi i915_bpo intel_ips psmouse i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops r8169 mii drm ahci libahci wmi video pinctrl_sunrisepoint pinctrl_intel i2c_hid hid fjes
Jan 22 22:58:39 Arctic kernel: [57339.637426] CPU: 3 PID: 10930 Comm: kworker/u8:3 Tainted: G        W       4.4.0-109-generic #132-Ubuntu
Jan 22 22:58:39 Arctic kernel: [57339.637429] Hardware name: System manufacturer System Product Name/PRIME B250M-A, BIOS 0614 04/18/2017
Jan 22 22:58:39 Arctic kernel: [57339.637440] Workqueue: phy1 ath9k_htc_ani_work [ath9k_htc]
Jan 22 22:58:39 Arctic kernel: [57339.637444]  0000000000000286 9a8209db5a7f35de ffff88022a213bc0 ffffffff813fbb03
Jan 22 22:58:39 Arctic kernel: [57339.637450]  ffff88022a213c08 ffffffff81d52c80 ffff88022a213bf8 ffffffff81081e52
Jan 22 22:58:39 Arctic kernel: [57339.637455]  ffff8802026cdd80 0000000000000002 ffff8801ef11e800 0000000000000001
Jan 22 22:58:39 Arctic kernel: [57339.637461] Call Trace:
Jan 22 22:58:39 Arctic kernel: [57339.637469]  [<ffffffff813fbb03>] dump_stack+0x63/0x90
Jan 22 22:58:39 Arctic kernel: [57339.637476]  [<ffffffff81081e52>] warn_slowpath_common+0x82/0xc0
Jan 22 22:58:39 Arctic kernel: [57339.637481]  [<ffffffff81081eec>] warn_slowpath_fmt+0x5c/0x80
Jan 22 22:58:39 Arctic kernel: [57339.637486]  [<ffffffff810edd28>] ? del_timer_sync+0x48/0x50
Jan 22 22:58:39 Arctic kernel: [57339.637492]  [<ffffffff81629092>] usb_submit_urb.part.6+0x142/0x560
Jan 22 22:58:39 Arctic kernel: [57339.637497]  [<ffffffff81629512>] usb_submit_urb+0x62/0x70
Jan 22 22:58:39 Arctic kernel: [57339.637505]  [<ffffffffc07e3d8b>] hif_usb_send+0xeb/0x340 [ath9k_htc]
Jan 22 22:58:39 Arctic kernel: [57339.637513]  [<ffffffffc07e2058>] htc_issue_send.constprop.2+0x58/0x70 [ath9k_htc]
Jan 22 22:58:39 Arctic kernel: [57339.637520]  [<ffffffffc07e2428>] htc_send_epid+0x18/0x20 [ath9k_htc]
Jan 22 22:58:39 Arctic kernel: [57339.637528]  [<ffffffffc07e5201>] ath9k_wmi_cmd+0x111/0x1a0 [ath9k_htc]
Jan 22 22:58:39 Arctic kernel: [57339.637536]  [<ffffffffc07eaacd>] ath9k_regread+0x4d/0x80 [ath9k_htc]
Jan 22 22:58:39 Arctic kernel: [57339.637558]  [<ffffffffc078b9f5>] ath9k_hw_ani_monitor+0x65/0x1c0 [ath9k_hw]
Jan 22 22:58:39 Arctic kernel: [57339.637567]  [<ffffffffc07e9b5d>] ath9k_htc_ani_work+0xcd/0x1a0 [ath9k_htc]
Jan 22 22:58:39 Arctic kernel: [57339.637573]  [<ffffffff8109b1a5>] process_one_work+0x165/0x480
Jan 22 22:58:39 Arctic kernel: [57339.637579]  [<ffffffff8109b50b>] worker_thread+0x4b/0x4d0
Jan 22 22:58:39 Arctic kernel: [57339.637586]  [<ffffffff8109b4c0>] ? process_one_work+0x480/0x480
Jan 22 22:58:39 Arctic kernel: [57339.637592]  [<ffffffff810a1845>] kthread+0xe5/0x100
Jan 22 22:58:39 Arctic kernel: [57339.637597]  [<ffffffff810a1760>] ? kthread_create_on_node+0x1e0/0x1e0
Jan 22 22:58:39 Arctic kernel: [57339.637605]  [<ffffffff81844a0f>] ret_from_fork+0x3f/0x70
Jan 22 22:58:39 Arctic kernel: [57339.637609]  [<ffffffff810a1760>] ? kthread_create_on_node+0x1e0/0x1e0
Jan 22 22:58:39 Arctic kernel: [57339.637613] ---[ end trace 0ae99387ada64f57 ]---



```

---

### Post by hans12345 on 2018-01-22
Thanks  Habitual for your tips.

I think logrotate is OK. See my post 2 or 3 back.

---

### Post by hans12345 on 2018-01-22
> **Temüjin said:**
> It looks like an issue with the wireless adapter (ath9k_htc driver). 
[https://github.com/qca/open-ath9k-htc-firmware/wiki/usb-related-issues#bogus-urb-xfer-pipe-1--type-3](https://github.com/qca/open-ath9k-htc-firmware/wiki/usb-related-issues#bogus-urb-xfer-pipe-1--type-3)
Look at lsusb to make sure the USB controller is >= 2.0
```
lsusb
```

...

```

/var/log$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0cf3:7015 Atheros Communications, Inc. TP-Link TL-WN821N v3 / TL-WN822N v2 802.11n [Atheros AR7010+AR9287]
Bus 001 Device 002: ID 03eb:3301 Atmel Corp. at43301 4-Port Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Can this be the problem? I did change the adaptor a few days ago!

---

### Post by Yellow Pasque on 2018-01-22
A little more info (no solution though): [http://lists.infradead.org/pipermail/linux-snps-arc/2016-July/001310.html](http://lists.infradead.org/pipermail/linux-snps-arc/2016-July/001310.html)

> **hans12345 said:**
> Can this be the problem? I did change the adaptor a few days ago!

Yes, the adapter is causing the flood of errors. The adapter is plugged into USB 2.0 controller, so that part is okay.

---

### Post by hans12345 on 2018-01-23
> **Temüjin said:**
> A little more info (no solution though): [http://lists.infradead.org/pipermail/linux-snps-arc/2016-July/001310.html](http://lists.infradead.org/pipermail/linux-snps-arc/2016-July/001310.html)



Yes, the adapter is causing the flood of errors. The adapter is plugged into USB 2.0 controller, so that part is okay.

Thanks Temüjin

I have just switched to a powerline connection (I was meaning to do that anyway) and removed the dongle.

Let's see if the logs go back to normal.

---

### Post by hans12345 on 2018-01-24
The status today:

```


-rw-r----- 1 syslog            adm      40573732907 janv. 24 19:10 kern.log
-rw-r----- 1 syslog            adm           205286 janv. 14 07:21 kern.log.2.gz
-rw-r----- 1 syslog            adm           148566 janv.  8 15:14 kern.log.3.gz
-rw-r----- 1 syslog            adm           244907 déc.   3 07:47 kern.log.4.gz
-rw-rw-r-- 1 root              utmp          292292 nov.  26 11:51 lastlog
drwxr-xr-x 2 root              root            4096 janv. 24 07:21 lightdm
-rw-r--r-- 1 minidlna          minidlna        1292 janv. 24 13:21 minidlna.log
-rw-r--r-- 1 minidlna          minidlna        2091 janv. 22 07:08 minidlna.log.1
-rw-r--r-- 1 minidlna          minidlna         403 janv. 14 07:25 minidlna.log.2.gz
-rw-r--r-- 1 minidlna          minidlna         325 janv.  8 15:19 minidlna.log.3.gz
-rw-r--r-- 1 minidlna          minidlna         563 déc.   3 07:52 minidlna.log.4.gz
drwxr-x--- 3 root              adm             4096 janv. 22 07:14 samba
drwx------ 2 speech-dispatcher root            4096 févr. 18  2016 speech-dispatcher
-rw-r----- 1 syslog            adm           295339 janv. 24 22:25 syslog
-rw-r----- 1 syslog            adm       7276515870 janv. 24 07:27 syslog.1
-rw-r----- 1 syslog            adm       1746684315 janv. 23 07:07 syslog.2.gz
-rw-r----- 1 syslog            adm       1830915380 janv. 21 06:49 syslog.4.gz
-rw-r----- 1 syslog            adm       1058447722 janv. 20 08:11 syslog.5.gz
-rw-r----- 1 syslog            adm            70267 janv. 19 07:24 syslog.6.gz
-rw-r----- 1 syslog            adm            40741 janv. 18 07:22 syslog.7.gz


```

syslog looking better, kern.log very big

---

### Post by Yellow Pasque on 2018-01-24
Okay. But the is the kern.log growing at the same rate? i.e. Are there a bunch of entries from the current boot like the ones you quoted?

---

### Post by Impavidus on 2018-01-25
Logrotate rotates syslog daily, kern.log weekly. So by next week kern.log should be renamed kern.log.1. Then you can safely remove it to get your disk space back, or you can wait 4 weeks before it gets removed automatically. The old big syslogs should be gone in a week.

---

### Post by hans12345 on 2018-01-29
It looks like things are good now, just as you have predicted:

```
                                     96 kern.log
       0 apport.log		39623200 kern.log.1
       4 apport.log.1		     204 kern.log.3.gz
       4 apport.log.2.gz	     148 kern.log.4.gz
       4 apport.log.3.gz	      40 lastlog
       4 apport.log.4.gz	       4 lightdm
       4 apport.log.5.gz	       4 minidlna.log
       4 apport.log.6.gz	       4 minidlna.log.1
       4 apport.log.7.gz	       4 minidlna.log.2.gz
       4 apt			       4 minidlna.log.3.gz
      32 auth.log		       4 minidlna.log.4.gz
     144 auth.log.1		       4 samba
      20 auth.log.2.gz		       4 speech-dispatcher
      16 auth.log.3.gz		       4 syslog
      12 auth.log.4.gz		     312 syslog.1
       8 boot.log		      40 syslog.2.gz
      60 bootstrap.log		      36 syslog.3.gz
       0 btmp			      36 syslog.4.gz
       0 btmp.1			      64 syslog.5.gz
       4 cups			  372344 syslog.6.gz
       4 dist-upgrade		 1705752 syslog.7.gz

```

Thanks everyone for your help and guidance.

---

