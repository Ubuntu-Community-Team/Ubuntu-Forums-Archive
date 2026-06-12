---
title: "Tablet keeps on immediately sleeping (crashing?)"
date: 2022-03-02
forum: General Help
---

### Post by sshaikh on 2022-03-02
I've installed Ubuntu 20.04.4 on a baytrail tablet. It worked fine provided I pass nomodeset as a kernel parameter in grub, but that removes a lot of features including the ability to suspend.

If i remove nomodeset, then the tablet will suspend randomly at very frequent intervals (seconds). The tablet can be woken up immediately by pressing a key on an attached keyboard or pressing the power button.

I suspect this is a power management or display driver issue. The relevant dmesg output follows:

```

[   95.819408] PM: suspend entry (s2idle)
[   95.904838] Filesystems sync: 0.085 seconds
[   95.907196] Freezing user space processes ... (elapsed 0.544 seconds) done.
[   96.451594] OOM killer disabled.
[   96.451603] Freezing remaining freezable tasks ... (elapsed 0.002 seconds) done.
[   96.453912] printk: Suspending console(s) (use no_console_suspend to debug)
[   96.664138] ------------[ cut here ]------------
[   96.664146] WARNING: CPU: 0 PID: 1528 at drivers/mmc/core/sdio.c:1026 mmc_sdio_suspend+0xc8/0x130
[   96.664170] Modules linked in: rfcomm cmac algif_hash algif_skcipher af_alg bnep snd_soc_sst_bytcr_rt5640 gpio_keys snd_hdmi_lpe_audio intel_rapl_msr joydev mei_hdcp intel_soc_dts_thermal intel_powerclamp coretemp kvm_intel kvm punit_atom_debug crct10dif_pclmul ghash_clmulni_intel aesni_intel nls_iso8859_1 crypto_simd cryptd intel_cstate efi_pstore r8723bs(C) cfg80211 axp288_fuel_gauge extcon_axp288 axp288_charger axp20x_pek axp288_adc input_leds mac_hid snd_sof_acpi_intel_byt snd_sof_intel_ipc snd_sof_acpi snd_sof_xtensa_dsp snd_sof ledtrig_audio snd_intel_sst_acpi snd_soc_rt5670 snd_soc_acpi_intel_match snd_soc_rt5651 snd_soc_acpi snd_soc_rt5645 snd_intel_sst_core snd_soc_sst_atom_hifi2_platform snd_intel_dspcfg snd_intel_sdw_acpi snd_soc_rt5640 snd_soc_rl6231 snd_soc_core snd_compress ac97_bus snd_pcm_dmaengine snd_pcm soc_button_array dptf_power int3406_thermal snd_seq_midi snd_seq_midi_event processor_thermal_device processor_thermal_rfim snd_rawmidi processor_thermal_mbox
[   96.664374]  processor_thermal_rapl int3400_thermal int3403_thermal intel_rapl_common acpi_thermal_rel int340x_thermal_zone intel_soc_dts_iosf hci_uart kxcjk_1013 snd_seq btqca industrialio_triggered_buffer btrtl kfifo_buf btbcm intel_int0002_vgpio snd_seq_device btintel industrialio i915 snd_timer intel_cht_int33fe bluetooth goodix acpi_pad snd ecdh_generic soundcore ecc drm_kms_helper cec rc_core i2c_algo_bit fb_sys_fops syscopyarea 8250_dw mei_txe mei sysfillrect sysimgblt sch_fq_codel msr parport_pc ppdev lp parport drm ip_tables x_tables autofs4 hid_generic usbhid hid mmc_block crc32_pclmul xhci_pci xhci_pci_renesas lpc_ich video dw_dmac dw_dmac_core axp20x_i2c sdhci_acpi axp20x sdhci
[   96.664563] CPU: 0 PID: 1528 Comm: kworker/u8:12 Tainted: G        WC        5.13.0-30-generic #33~20.04.1-Ubuntu
[   96.664574] Hardware name: Exertis Linx8/Type2 - Board Product Name, BIOS LINX8.RL221.03.03_1 10/21/2014
[   96.664580] Workqueue: events_unbound async_run_entry_fn
[   96.664595] RIP: 0010:mmc_sdio_suspend+0xc8/0x130
[   96.664608] Code: 00 00 4c 89 e7 e8 b8 40 ff ff 31 c0 41 5c 41 5d 5d c3 4c 89 e7 e8 a8 6d ff ff 4c 89 e7 e8 a0 40 ff ff 31 c0 41 5c 41 5d 5d c3 <0f> 0b e9 58 ff ff ff 4d 8b ac 24 c0 03 00 00 41 83 bd f0 02 00 00
[   96.664616] RSP: 0018:ffffa5d80227bd60 EFLAGS: 00010246
[   96.664625] RAX: ffffffffa316e5c0 RBX: 0000000000000000 RCX: ffffffffa3e5a48a
[   96.664632] RDX: 0000000000000001 RSI: 0000000000000002 RDI: ffff8b35cde28000
[   96.664638] RBP: ffffa5d80227bd70 R08: 0000000000000000 R09: 8080808080808080
[   96.664644] R10: ffff8b35c837542c R11: 000000000000000f R12: ffff8b35cde28000
[   96.664650] R13: ffff8b35c2963008 R14: ffff8b35cde28000 R15: 0000000000000002
[   96.664656] FS:  0000000000000000(0000) GS:ffff8b35f5200000(0000) knlGS:0000000000000000
[   96.664664] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[   96.664671] CR2: 0000561c51bc8ad6 CR3: 000000002c410000 CR4: 00000000001006f0
[   96.664678] Call Trace:
[   96.664683]  <TASK>
[   96.664691]  mmc_bus_suspend+0x35/0x60
[   96.664705]  ? mmc_bus_resume+0x40/0x40
[   96.664717]  dpm_run_callback+0x51/0x120
[   96.664728]  __device_suspend+0x148/0x4a0
[   96.664739]  async_suspend+0x20/0x90
[   96.664749]  async_run_entry_fn+0x33/0x120
[   96.664760]  process_one_work+0x220/0x3c0
[   96.664773]  worker_thread+0x4d/0x3f0
[   96.664784]  ? process_one_work+0x3c0/0x3c0
[   96.664794]  kthread+0x12b/0x150
[   96.664803]  ? set_kthread_struct+0x40/0x40
[   96.664814]  ret_from_fork+0x22/0x30
[   96.664830]  </TASK>
[   96.664834] ---[ end trace 8a7bef3658f33887 ]---
[   96.664835] serial 00:02: disabled
[   98.326093] PM: dpm_run_callback(): rtw_sdio_resume+0x0/0x50 [r8723bs] returns -1
[   98.326321] rtl8723bs mmc0:0001:1: PM: failed to resume async: error -1
[   98.489047] OOM killer enabled.
[   98.489059] Restarting tasks ... done.
[   98.513771] ACPI Error: AE_ERROR, Returned by Handler for [UserDefinedRegion] (20210331/evregion-281)

[   98.513817] No Local Variables are initialized for Method [_TMP]

[   98.513824] No Arguments are initialized for method [_TMP]

[   98.513836] ACPI Error: Aborting method \_SB.SXP1._TMP due to previous error (AE_ERROR) (20210331/psparse-529)
[   98.513877] thermal thermal_zone2: failed to read out thermal zone (-5)
[   98.514673] PM: suspend exit
[   99.171163] Bluetooth: hci0: RTL: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[   99.176032] Bluetooth: hci0: RTL: rom_version status=0 version=1
[   99.176067] Bluetooth: hci0: RTL: loading rtl_bt/rtl8723bs_fw.bin
[   99.176160] Bluetooth: hci0: RTL: loading rtl_bt/rtl8723bs_config-OBDA8723.bin
[   99.200273] Bluetooth: hci0: RTL: cfg_sz 64, total sz 24508
[   99.980317] Bluetooth: hci0: RTL: fw version 0x365d462e

```

Although I am not clear on whether this appears on suspend or wakeup.

Are there any tips on how to diagnose this further?

---

### Post by sshaikh on 2022-03-03
Latest bios fixed these issues for me.

---

### Post by vic11con on 2022-03-04
Check for any recent updates or get the latest bios.

---

