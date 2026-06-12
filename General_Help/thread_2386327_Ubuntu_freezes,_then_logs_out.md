---
title: "Ubuntu freezes, then logs out"
date: 2018-03-04
forum: General Help
---

### Post by kapad on 2018-03-04
I've recently done a fresh install of Ubuntu and upgraded to Artful (17.10) and am using Wayland (which is the default, I guess). 

There's a weird problem that I keep seeing (I think it only occurs when I'm using two monitors, and not when I'm using only my laptop monitor, but I'm not a 100% sure of this still). 

What happens is this: The entire desktop will freeze for a minute or two, then I will be taken to a black screen (this screen has some '@' characters printed on the first line). After this I get logged out of Gnome. I can log back in and continue using the system without further issues (for some time - a day or two) until the issue occurs again. Each time I get logged out, all applications that I am working on also close, and this is a major issue for me. 

I've run dmesg, and can see some lines in red that I've pasted below. 
There are a number of lines with the same messages and highlighted in red.

```
[   51.854739] pcieport 0000:00:1c.0: PCIe Bus Error: severity=Corrected, type=Data Link Layer, id=00e0(Transmitter ID)
[   51.854747] pcieport 0000:00:1c.0:   device [8086:9d14] error status/mask=00001000/00002000
[   51.854752] pcieport 0000:00:1c.0:    [12] Replay Timer Timeout  

```

The following trace was also in the dmesg output after those lines in red.

```
[19296.462083] WARNING: CPU: 2 PID: 0 at /home/kernel/COD/linux/net/core/dev.c:5630 net_rx_action+0x2b3/0x380
[19296.462085] Modules linked in: uhid algif_hash hid_logitech_hidpp hid_logitech_dj hid_generic usbhid hid btrfs zstd_compress xor raid6_pq ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) rfcomm ipt_MASQUERADE nf_nat_masquerade_ipv4 nf_conntrack_netlink nfnetlink xfrm_user xfrm_algo iptable_nat nf_conntrack_ipv4 nf_defrag_ipv4 nf_nat_ipv4 xt_addrtype iptable_filter xt_conntrack nf_nat nf_conntrack libcrc32c br_netfilter bridge stp llc overlay ccm pci_stub cmac bnep arc4 nls_iso8859_1 snd_hda_codec_hdmi snd_soc_skl snd_soc_skl_ipc snd_hda_codec_realtek snd_hda_ext_core snd_hda_codec_generic snd_soc_sst_dsp snd_soc_sst_ipc snd_soc_acpi snd_soc_core snd_compress ac97_bus snd_pcm_dmaengine snd_hda_intel snd_hda_codec snd_hda_core dell_laptop uvcvideo
[19296.462145]  dell_smbios_smm dcdbas videobuf2_vmalloc dell_smm_hwmon snd_hwdep videobuf2_memops intel_rapl videobuf2_v4l2 videobuf2_core x86_pkg_temp_thermal intel_powerclamp coretemp snd_pcm videodev media kvm_intel snd_seq_midi snd_seq_midi_event kvm snd_rawmidi irqbypass ath10k_pci btusb btrtl ath10k_core btbcm btintel ath intel_cstate intel_rapl_perf bluetooth snd_seq mac80211 snd_seq_device snd_timer dell_wmi ecdh_generic dell_smbios_wmi dell_smbios input_leds sparse_keymap joydev wmi_bmof snd serio_raw dell_wmi_descriptor rtsx_pci_ms memstick soundcore cfg80211 mei_me processor_thermal_device shpchp mei intel_pch_thermal intel_soc_dts_iosf mac_hid dell_rbtn int3403_thermal acpi_pad int340x_thermal_zone int3400_thermal acpi_thermal_rel parport_pc ppdev lp parport ip_tables x_tables autofs4 algif_skcipher
[19296.462186]  af_alg mmc_block dm_crypt i915 crct10dif_pclmul crc32_pclmul ghash_clmulni_intel pcbc i2c_algo_bit rtsx_pci_sdmmc drm_kms_helper syscopyarea sysfillrect aesni_intel sysimgblt fb_sys_fops e1000e aes_x86_64 crypto_simd glue_helper ptp cryptd psmouse pps_core drm rtsx_pci ahci libahci wmi video [last unloaded: vboxdrv]
[19296.462208] CPU: 2 PID: 0 Comm: swapper/2 Tainted: G           OE    4.15.2-041502-generic #201802072230
[19296.462209] Hardware name: Dell Inc. Latitude E7470/0DGYY5, BIOS 1.17.5 07/11/2017
[19296.462213] RIP: 0010:net_rx_action+0x2b3/0x380
[19296.462214] RSP: 0018:ffff881c8dd03ec8 EFLAGS: 00010293
[19296.462216] RAX: 0000000000000042 RBX: 0000000000000040 RCX: ffff881c72cf1e80
[19296.462217] RDX: ffff881874425000 RSI: 00000000fffffe01 RDI: ffffffffc08b71d0
[19296.462218] RBP: ffff881c8dd03f38 R08: 0000000000000002 R09: 0000000000000000
[19296.462219] R10: 00000000000065a1 R11: 0000000000000001 R12: 0000000000000000
[19296.462220] R13: 00000000ffffffff R14: 0000000000000003 R15: ffff881c72cf7b60
[19296.462222] FS:  0000000000000000(0000) GS:ffff881c8dd00000(0000) knlGS:0000000000000000
[19296.462223] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[19296.462225] CR2: 00000551d2e4cb10 CR3: 00000002bba0a002 CR4: 00000000003606e0
[19296.462226] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[19296.462227] DR3: 0000000000000000 DR6: 00000000fffe0ff0 DR7: 0000000000000400
[19296.462228] Call Trace:
[19296.462230]  <IRQ>
[19296.462235]  __do_softirq+0xdf/0x2b2
[19296.462238]  irq_exit+0xb6/0xc0
[19296.462241]  do_IRQ+0x82/0xd0
[19296.462243]  common_interrupt+0x9f/0x9f
[19296.462244]  </IRQ>
[19296.462247] RIP: 0010:cpuidle_enter_state+0xa7/0x2f0
[19296.462248] RSP: 0018:ffff976dc193fe68 EFLAGS: 00000246 ORIG_RAX: ffffffffffffffde
[19296.462250] RAX: ffff881c8dd22840 RBX: 0000118ccebf78d1 RCX: 000000000000001f
[19296.462252] RDX: 0000118ccebf78d1 RSI: 00001089a10b0d8f RDI: 0000000000000000
[19296.462253] RBP: ffff976dc193fea8 R08: 000000000000041e R09: 0000000000000018
[19296.462254] R10: ffff976dc193fe38 R11: 00000000000003de R12: ffff881c8dd2c858
[19296.462255] R13: 0000000000000004 R14: ffffffffbd971578 R15: 0000000000000000
[19296.462258]  ? cpuidle_enter_state+0x97/0x2f0
[19296.462260]  cpuidle_enter+0x17/0x20
[19296.462262]  call_cpuidle+0x23/0x40
[19296.462264]  do_idle+0x18c/0x1f0
[19296.462265]  cpu_startup_entry+0x73/0x80
[19296.462268]  start_secondary+0x1a6/0x200
[19296.462271]  secondary_startup_64+0xa5/0xb0
[19296.462272] Code: 24 08 49 83 c4 18 89 d9 44 89 f2 4c 89 fe e8 f5 ae 3b 00 4d 8b 14 24 4d 85 d2 75 e1 4c 8b 65 90 44 89 f0 39 c3 0f 8d 9d fe ff ff <0f> ff 39 c3 0f 8f 9b fe ff ff 49 8b 47 10 a8 04 75 68 49 83 7f 
[19296.462307] ---[ end trace 02904c832151e1c9 ]---

```

I've uploaded the entire dmesg output to [this gist]("https://gist.github.com/kapad/e2ca95650618b15c5ad9e9f36fd0e449")

---

### Post by cruzer001 on 2018-03-04
Are you saying that you have not tried xorg?

[https://itsfoss.com/switch-xorg-wayland/](https://itsfoss.com/switch-xorg-wayland/)

---

### Post by kapad on 2018-03-04
> **cruzer001 said:**
> Are you saying that you have not tried xorg?

[https://itsfoss.com/switch-xorg-wayland/](https://itsfoss.com/switch-xorg-wayland/)

I know it's an option, but since Wayland is the default now and going forward, I want to try and find workarounds to the issues. 
And no, I haven't yet tried X.org on artful as of yet.

---

### Post by kapad on 2018-03-04
This issue happened again, and I found a stack trace in syslog that I thought was relevant. Any ideas if this stack trace is the root cause? Any known workarounds to this problem? 

```
Mar  4 22:14:45 rocket gnome-shell[7471]: ../../../../glib/gmem.c:130: failed to allocate 18446744072098939136 bytes
Mar  4 22:14:45 rocket org.gnome.Shell.desktop[7471]: == Stack trace for context 0x561d31c1d000 ==
Mar  4 22:14:45 rocket org.gnome.Shell.desktop[7471]: #0 0x7ffe1fdbfb70 b   resource:///org/gnome/shell/ui/panel.js:199 (0x7f39e35091a8 @ 88)
Mar  4 22:14:45 rocket org.gnome.Shell.desktop[7471]: #1 0x7ffe1fdbfbd0 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7f3a004c2c48 @ 71)
Mar  4 22:14:45 rocket org.gnome.Shell.desktop[7471]: #2 0x7ffe1fdbfc80 b   resource:///org/gnome/shell/ui/panel.js:330 (0x7f39e3509670 @ 804)
Mar  4 22:14:45 rocket org.gnome.Shell.desktop[7471]: #3 0x7ffe1fdbfce0 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7f3a004c2c48 @ 71)
Mar  4 22:14:45 rocket org.gnome.Shell.desktop[7471]: #4 0x561d31e80920 i   resource:///org/gnome/shell/ui/panel.js:254 (0x7f39e3509450 @ 156)
Mar  4 22:14:45 rocket org.gnome.Shell.desktop[7471]: #5 0x7ffe1fdc08f0 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7f3a004c2c48 @ 71)
```

---

