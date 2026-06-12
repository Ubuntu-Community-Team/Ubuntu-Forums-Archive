---
title: "Suspect that PepperFlash is triggering Kernel Oops 2"
date: 2016-08-07
forum: General Help
---

### Post by bcschmerker on 2016-08-07
I have run into intermittent lockups of chromium-browser under Ubuntu 16.04.1-LTS; when such lockups occur, Firefox also locks up.  The following typical trace is excerpted from /var/log/kern.log, which I noticed following varying numbers of "trap" reports for libpepflashplayer.so:

```
Aug  7 00:54:52 hotrodgpc-desktop kernel: [23437.320348] BUG: unable to handle kernel paging request at 0000000044de8955
Aug  7 00:54:52 hotrodgpc-desktop kernel: [23437.320407] IP: [<ffffffff8121c0be>] path_openat+0xc1e/0x1330
Aug  7 00:54:52 hotrodgpc-desktop kernel: [23437.320449] PGD 0 
Aug  7 00:54:52 hotrodgpc-desktop kernel: [23437.320465] Oops: 0002 [#1] SMP 
Aug  7 00:54:52 hotrodgpc-desktop kernel: [23437.320489] Modules linked in: rfcomm 8021q garp mrp stp llc bnep drbg ansi_cprng xts gf128mul dm_crypt kvm_amd kvm irqbypass uvcvideo input_leds videobuf2_vmalloc videobuf2_memops serio_raw videobuf2_v4l2 edac_mce_amd videobuf2_core k8temp edac_core v4l2_common videodev media btusb btrtl btbcm btintel bluetooth snd_hda_codec_hdmi snd_hda_intel i2c_piix4 snd_hda_codec snd_virtuoso snd_hda_core snd_oxygen_lib snd_hwdep snd_mpu401_uart snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq snd_seq_device snd_timer snd soundcore 8250_fintek mac_hid shpchp it87 hwmon_vid parport_pc ppdev lp parport autofs4 btrfs xor raid6_pq pata_acpi uas usb_storage psmouse firewire_ohci firewire_core crc_itu_t pata_atiixp amdkfd amd_iommu_v2 radeon i2c_algo_bit ttm drm_kms_helper syscopyarea sysfillrect floppy fjes sysimgblt fb_sys_fops drm r8169 mii wmi ahci libahci
Aug  7 00:54:52 hotrodgpc-desktop kernel: [23437.321069] CPU: 1 PID: 7789 Comm: Chrome_FileUser Not tainted 4.4.0-31-generic #50-Ubuntu
Aug  7 00:54:52 hotrodgpc-desktop kernel: [23437.321119] Hardware name: Gigabyte Technology Co., Ltd. GA-MA78GM-S2HP/GA-MA78GM-S2HP, BIOS F3 12/16/2008
Aug  7 00:54:52 hotrodgpc-desktop kernel: [23437.321176] task: ffff88007e2b2580 ti: ffff880006188000 task.ti: ffff880006188000
Aug  7 00:54:52 hotrodgpc-desktop kernel: [23437.321220] RIP: 0010:[<ffffffff8121c0be>]  [<ffffffff8121c0be>] path_openat+0xc1e/0x1330
Aug  7 00:54:52 hotrodgpc-desktop kernel: [23437.321270] RSP: 0018:ffff88000618bd10  EFLAGS: 00010202
Aug  7 00:54:52 hotrodgpc-desktop kernel: [23437.321302] RAX: ffff880129bf9800 RBX: ffff8800a97ea840 RCX: 000000000000000d
Aug  7 00:54:52 hotrodgpc-desktop kernel: [23437.321345] RDX: 0000000000008180 RSI: ffffc9000025d740 RDI: ffff8800a97ea840
Aug  7 00:54:52 hotrodgpc-desktop kernel: [23437.321387] RBP: ffff88000618bdc0 R08: 0000000000008180 R09: 0000000000000001
Aug  7 00:54:52 hotrodgpc-desktop kernel: [23437.321428] R10: 000000008fa5c33e R11: 0000000000000000 R12: 00000000000080c2
Aug  7 00:54:52 hotrodgpc-desktop kernel: [23437.321471] R13: ffff88000618bef4 R14: ffff88000618bdd0 R15: ffff8800abb15540
Aug  7 00:54:52 hotrodgpc-desktop kernel: [23437.321513] FS:  00007f726ce0c700(0000) GS:ffff88012fc80000(0000) knlGS:0000000000000000
Aug  7 00:54:52 hotrodgpc-desktop kernel: [23437.321561] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Aug  7 00:54:52 hotrodgpc-desktop kernel: [23437.321595] CR2: 0000000044de8955 CR3: 0000000110ce6000 CR4: 00000000000006e0
Aug  7 00:54:52 hotrodgpc-desktop kernel: [23437.321637] Stack:
Aug  7 00:54:52 hotrodgpc-desktop kernel: [23437.323990]  ffff88000618bd78 0000000000000001 ffff8800ae985c88 ffff88007e2b2580
Aug  7 00:54:52 hotrodgpc-desktop kernel: [23437.324008]  ffff88007e2b2580 ffff88007e2b2580 ffff88007e2b2580 ffff8800117e7d00
Aug  7 00:54:52 hotrodgpc-desktop kernel: [23437.324008]  000000260001bd48 00000041002b2580 ffff8800abb15540 01ffffff810fffe9
Aug  7 00:54:52 hotrodgpc-desktop kernel: [23437.324008] Call Trace:
Aug  7 00:54:52 hotrodgpc-desktop kernel: [23437.324008]  [<ffffffff8121d9c1>] do_filp_open+0x91/0x100
Aug  7 00:54:52 hotrodgpc-desktop kernel: [23437.324008]  [<ffffffff8122b256>] ? __alloc_fd+0x46/0x190
Aug  7 00:54:52 hotrodgpc-desktop kernel: [23437.324008]  [<ffffffff8120c248>] do_sys_open+0x138/0x2a0
Aug  7 00:54:52 hotrodgpc-desktop kernel: [23437.324008]  [<ffffffff81103441>] ? SyS_futex+0x81/0x180
Aug  7 00:54:52 hotrodgpc-desktop kernel: [23437.324008]  [<ffffffff810f4a5a>] ? ktime_get_ts64+0x4a/0xf0
Aug  7 00:54:52 hotrodgpc-desktop kernel: [23437.324008]  [<ffffffff8120c3ce>] SyS_open+0x1e/0x20
Aug  7 00:54:52 hotrodgpc-desktop kernel: [23437.324008]  [<ffffffff8182db32>] entry_SYSCALL_64_fastpath+0x16/0x71
Aug  7 00:54:52 hotrodgpc-desktop kernel: [23437.324008] Code: 0f 84 12 f9 ff ff 49 8b 47 30 41 0f b7 55 04 48 8b 40 28 f6 40 52 01 0f 84 1c 05 00 00 80 7d 92 00 0f 84 43 03 00 00 44 0f b7 c2 <31> c9 48 89 de 44 89 c2 4c 89 f7 83 4d b0 01 44 89 85 60 ff ff 
Aug  7 00:54:52 hotrodgpc-desktop kernel: [23437.324008] RIP  [<ffffffff8121c0be>] path_openat+0xc1e/0x1330
Aug  7 00:54:52 hotrodgpc-desktop kernel: [23437.324008]  RSP <ffff88000618bd10>
Aug  7 00:54:52 hotrodgpc-desktop kernel: [23437.324008] CR2: 0000000044de8955
Aug  7 00:54:52 hotrodgpc-desktop kernel: [23437.370973] ---[ end trace 9cd135f3efabd7cf ]---
```
Suspect an existing issue with libpepflashplayer.so (Package: **pepperflashplugin-nonfree**) but have some trouble locating the correct Bug at Launchpad. How do I proceed?

---

### Post by ajgreeny on 2016-08-07
You do not need **pepperflashplugin-nonfree** any more to get the latest version of flash in chromium, (nor firefox) so I suggest you remove it, enable the canonical partner repos if not already available in your software-sources, and then install **adobe-flashplugin** which is all that is now needed.  Hopefully that might solve your problem.

If you want flash version 22.0.0.209 for firefox also install the **browser-plugin-freshplayer-pepperflash** package otherwise you will only get flash version 11.

---

### Post by bcschmerker on 2016-08-08
Plug-in's in place after removing the installer package, but chromium-browser still hangs.  Updated excerpt from kern.log:

```
Aug  7 21:41:29 hotrodgpc-desktop kernel: [ 4242.101405] BUG: unable to handle kernel paging request at 0000000044de8955
Aug  7 21:41:29 hotrodgpc-desktop kernel: [ 4242.101471] IP: [<ffffffff8121c0be>] path_openat+0xc1e/0x1330
Aug  7 21:41:29 hotrodgpc-desktop kernel: [ 4242.101512] PGD 0 
Aug  7 21:41:29 hotrodgpc-desktop kernel: [ 4242.101528] Oops: 0002 [#1] SMP 
Aug  7 21:41:29 hotrodgpc-desktop kernel: [ 4242.101552] Modules linked in: rfcomm 8021q garp mrp stp llc bnep drbg ansi_cprng xts gf128mul dm_crypt kvm_amd kvm irqbypass uvcvideo videobuf2_vmalloc input_leds videobuf2_memops videobuf2_v4l2 serio_raw edac_mce_amd videobuf2_core edac_core k8temp v4l2_common videodev media btusb btrtl btbcm btintel bluetooth snd_hda_codec_hdmi snd_hda_intel i2c_piix4 snd_hda_codec snd_virtuoso snd_hda_core snd_oxygen_lib snd_hwdep snd_mpu401_uart snd_seq_midi snd_seq_midi_event snd_pcm snd_rawmidi snd_seq snd_seq_device snd_timer snd soundcore 8250_fintek shpchp mac_hid it87 hwmon_vid parport_pc ppdev lp parport autofs4 btrfs xor raid6_pq pata_acpi uas usb_storage psmouse firewire_ohci firewire_core crc_itu_t pata_atiixp amdkfd amd_iommu_v2 radeon i2c_algo_bit ttm fjes drm_kms_helper floppy syscopyarea ahci sysfillrect libahci sysimgblt r8169 mii wmi fb_sys_fops drm
Aug  7 21:41:29 hotrodgpc-desktop kernel: [ 4242.102137] CPU: 1 PID: 5656 Comm: Chrome_IOThread Not tainted 4.4.0-31-generic #50-Ubuntu
Aug  7 21:41:29 hotrodgpc-desktop kernel: [ 4242.102188] Hardware name: Gigabyte Technology Co., Ltd. GA-MA78GM-S2HP/GA-MA78GM-S2HP, BIOS F3 12/16/2008
Aug  7 21:41:29 hotrodgpc-desktop kernel: [ 4242.102244] task: ffff88011eea7080 ti: ffff88004cc40000 task.ti: ffff88004cc40000
Aug  7 21:41:29 hotrodgpc-desktop kernel: [ 4242.102288] RIP: 0010:[<ffffffff8121c0be>]  [<ffffffff8121c0be>] path_openat+0xc1e/0x1330
Aug  7 21:41:29 hotrodgpc-desktop kernel: [ 4242.102340] RSP: 0018:ffff88004cc43d10  EFLAGS: 00010202
Aug  7 21:41:29 hotrodgpc-desktop kernel: [ 4242.102372] RAX: ffff8800aed8c000 RBX: ffff88001ea4b3c0 RCX: 000000000000000d
Aug  7 21:41:29 hotrodgpc-desktop kernel: [ 4242.102414] RDX: 0000000000008180 RSI: ffffc90000199248 RDI: ffff88001ea4b3c0
Aug  7 21:41:29 hotrodgpc-desktop kernel: [ 4242.102455] RBP: ffff88004cc43dc0 R08: 0000000000008180 R09: 0000000000000001
Aug  7 21:41:29 hotrodgpc-desktop kernel: [ 4242.102498] R10: 000000008fa5c33e R11: 0000000000000000 R12: 00000000000080c2
Aug  7 21:41:29 hotrodgpc-desktop kernel: [ 4242.102541] R13: ffff88004cc43ef4 R14: ffff88004cc43dd0 R15: ffff8800aba8f840
Aug  7 21:41:29 hotrodgpc-desktop kernel: [ 4242.102584] FS:  00007f4a699b7700(0000) GS:ffff88012fc80000(0000) knlGS:0000000000000000
Aug  7 21:41:29 hotrodgpc-desktop kernel: [ 4242.102632] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Aug  7 21:41:29 hotrodgpc-desktop kernel: [ 4242.102666] CR2: 0000000044de8955 CR3: 000000002c11e000 CR4: 00000000000006e0
Aug  7 21:41:29 hotrodgpc-desktop kernel: [ 4242.102708] Stack:
Aug  7 21:41:29 hotrodgpc-desktop kernel: [ 4242.102721]  ffff880101643480 0000000000000000 ffff880129bca1a8 ffff88011eea7080
Aug  7 21:41:29 hotrodgpc-desktop kernel: [ 4242.104030]  ffff88011eea7080 ffff88011eea7080 ffff88011eea7080 ffff880029b59600
Aug  7 21:41:29 hotrodgpc-desktop kernel: [ 4242.104030]  000000260001bb40 000000410000014c ffff8800aba8f840 01ff88012b2f4c20
Aug  7 21:41:29 hotrodgpc-desktop kernel: [ 4242.104030] Call Trace:
Aug  7 21:41:29 hotrodgpc-desktop kernel: [ 4242.104030]  [<ffffffff8121d9c1>] do_filp_open+0x91/0x100
Aug  7 21:41:29 hotrodgpc-desktop kernel: [ 4242.113874]  [<ffffffff8122b256>] ? __alloc_fd+0x46/0x190
Aug  7 21:41:29 hotrodgpc-desktop kernel: [ 4242.114365]  [<ffffffff8120c248>] do_sys_open+0x138/0x2a0
Aug  7 21:41:29 hotrodgpc-desktop kernel: [ 4242.114365]  [<ffffffff810f4a5a>] ? ktime_get_ts64+0x4a/0xf0
Aug  7 21:41:29 hotrodgpc-desktop kernel: [ 4242.114365]  [<ffffffff8120c3ce>] SyS_open+0x1e/0x20
Aug  7 21:41:29 hotrodgpc-desktop kernel: [ 4242.122254]  [<ffffffff8182db32>] entry_SYSCALL_64_fastpath+0x16/0x71
Aug  7 21:41:29 hotrodgpc-desktop kernel: [ 4242.122254] Code: 0f 84 12 f9 ff ff 49 8b 47 30 41 0f b7 55 04 48 8b 40 28 f6 40 52 01 0f 84 1c 05 00 00 80 7d 92 00 0f 84 43 03 00 00 44 0f b7 c2 <31> c9 48 89 de 44 89 c2 4c 89 f7 83 4d b0 01 44 89 85 60 ff ff 
Aug  7 21:41:29 hotrodgpc-desktop kernel: [ 4242.122254] RIP  [<ffffffff8121c0be>] path_openat+0xc1e/0x1330
Aug  7 21:41:29 hotrodgpc-desktop kernel: [ 4242.122254]  RSP <ffff88004cc43d10>
Aug  7 21:41:29 hotrodgpc-desktop kernel: [ 4242.122254] CR2: 0000000044de8955
Aug  7 21:41:29 hotrodgpc-desktop kernel: [ 4242.147168] ---[ end trace 225757e611f0fda5 ]---

```

---

### Post by bcschmerker on 2016-08-13
**Update:**  It appears that the Kernel Oops 2 was not so much the fault of pepperflashplugin-nonfree as of LinUX Kernel 4.4.0-31; the problem went away with Kernel 4.4.0-34.  Considering the issue RESOLVED INVALID for adobe-flashplugin and peppeflashplugin-nonfree, RESOLVED FIXED for linux-image-generic.

---

