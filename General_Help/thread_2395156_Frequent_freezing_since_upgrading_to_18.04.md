---
title: "Frequent freezing since upgrading to 18.04"
date: 2018-06-27
forum: General Help
---

### Post by llamallord on 2018-06-27
My laptop always seemed to work fine until sometime around when I upgraded to 18.04. Since then, it freezes every few hours or so. The screen just stays as it was just not updating, and sysrq+ctrl+b doesn't do anything visible, nor does ctrl+alt+f1.

I got this laptop second hand not that long ago and ran a full memory check without errors. I am seeing many of these in the kern.log though:

```
Jun 24 05:28:54 Merovingian kernel: [ 2907.388060] Bluetooth: hci0: last event is not cmd complete (0x0f)
```

...and also sonetimes this:

```
Jun 24 05:10:16 Merovingian kernel: [ 1789.505176] Corrupted low memory at 000000007297e50b (12d8 phys) = 909000000000000
Jun 24 05:10:16 Merovingian kernel: [ 1789.505190] Corrupted low memory at 00000000b1af975e (12e0 phys) = 00003600
Jun 24 05:10:16 Merovingian kernel: [ 1789.505223] ------------[ cut here ]------------
Jun 24 05:10:16 Merovingian kernel: [ 1789.505226] Memory corruption detected in low memory
Jun 24 05:10:16 Merovingian kernel: [ 1789.505251] WARNING: CPU: 1 PID: 1672 at /build/linux-uT8zSN/linux-4.15.0/arch/x86/kernel/check.c:142 check_for_bios_corruption+0xab/0x100
Jun 24 05:10:16 Merovingian kernel: [ 1789.505254] Modules linked in: rfcomm cmac bnep nls_iso8859_1 intel_rapl intel_soc_dts_thermal intel_soc_dts_iosf intel_powerclamp coretemp uvcvideo snd_hda_codec_hdmi videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 snd_hda_codec_realtek snd_hda_codec_generic videobuf2_core videodev media btusb btrtl kvm snd_hda_intel snd_hda_codec irqbypass snd_hda_core snd_hwdep punit_atom_debug snd_pcm snd_seq_midi snd_seq_midi_event crct10dif_pclmul crc32_pclmul hci_uart ghash_clmulni_intel btbcm snd_rawmidi wl(POE) snd_seq snd_seq_device snd_timer snd rtsx_pci_ms memstick hp_wmi input_leds sparse_keymap wmi_bmof joydev btqca cryptd btintel intel_cstate soundcore bluetooth cfg80211 serio_raw shpchp lpc_ich hp_accel lis3lv02d ecdh_generic mei_txe mac_hid input_polldev pwm_lpss_platform mei pwm_lpss hp_wireless
Jun 24 05:10:16 Merovingian kernel: [ 1789.505417]  rfkill_gpio sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_generic usbhid i915 rtsx_pci_sdmmc i2c_algo_bit drm_kms_helper syscopyarea sysfillrect r8169 psmouse mii sysimgblt fb_sys_fops ahci drm rtsx_pci libahci wmi i2c_hid video hid
Jun 24 05:10:16 Merovingian kernel: [ 1789.505497] CPU: 1 PID: 1672 Comm: kworker/1:0 Tainted: P           OE    4.15.0-23-generic #25-Ubuntu
Jun 24 05:10:16 Merovingian kernel: [ 1789.505501] Hardware name: Hewlett-Packard HP Pavilion 14 Notebook PC /227A, BIOS F.42 03/18/2015
Jun 24 05:10:16 Merovingian kernel: [ 1789.505511] Workqueue: events check_corruption
Jun 24 05:10:16 Merovingian kernel: [ 1789.505523] RIP: 0010:check_for_bios_corruption+0xab/0x100
Jun 24 05:10:16 Merovingian kernel: [ 1789.505527] RSP: 0018:ffffa8a1810e7e38 EFLAGS: 00010282
Jun 24 05:10:16 Merovingian kernel: [ 1789.505534] RAX: 0000000000000000 RBX: ffff9c4c0000e000 RCX: 0000000000000006
Jun 24 05:10:16 Merovingian kernel: [ 1789.505539] RDX: 0000000000000007 RSI: 0000000000000092 RDI: ffff9c4e7fc96490
Jun 24 05:10:16 Merovingian kernel: [ 1789.505543] RBP: ffffa8a1810e7e68 R08: 0000000000000000 R09: 00000000000005b6
Jun 24 05:10:16 Merovingian kernel: [ 1789.505547] R10: 0000000000000000 R11: ffffffff8e55380d R12: 0000000000000000
Jun 24 05:10:16 Merovingian kernel: [ 1789.505551] R13: ffffffff8e52d4d0 R14: 0000000000000001 R15: 0000000080000000
Jun 24 05:10:16 Merovingian kernel: [ 1789.505557] FS:  0000000000000000(0000) GS:ffff9c4e7fc80000(0000) knlGS:0000000000000000
Jun 24 05:10:16 Merovingian kernel: [ 1789.505562] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Jun 24 05:10:16 Merovingian kernel: [ 1789.505567] CR2: 00007f210e7af7c0 CR3: 00000001d221a000 CR4: 00000000001006e0
Jun 24 05:10:16 Merovingian kernel: [ 1789.505571] Call Trace:
Jun 24 05:10:16 Merovingian kernel: [ 1789.505588]  check_corruption+0xe/0x40
Jun 24 05:10:16 Merovingian kernel: [ 1789.505598]  process_one_work+0x1de/0x410
Jun 24 05:10:16 Merovingian kernel: [ 1789.505607]  worker_thread+0x32/0x410
Jun 24 05:10:16 Merovingian kernel: [ 1789.505616]  kthread+0x121/0x140
Jun 24 05:10:16 Merovingian kernel: [ 1789.505624]  ? process_one_work+0x410/0x410
Jun 24 05:10:16 Merovingian kernel: [ 1789.505632]  ? kthread_create_worker_on_cpu+0x70/0x70
Jun 24 05:10:16 Merovingian kernel: [ 1789.505640]  ? kthread_create_worker_on_cpu+0x70/0x70
Jun 24 05:10:16 Merovingian kernel: [ 1789.505649]  ret_from_fork+0x35/0x40
Jun 24 05:10:16 Merovingian kernel: [ 1789.505655] Code: c4 08 5b 41 5c 41 5d 41 5e 41 5f 5d c3 f3 c3 80 3d 50 31 5a 01 00 75 e6 48 c7 c7 10 35 cc 8d c6 05 40 31 5a 01 01 e8 35 f0 01 00 <0f> 0b eb cf 48 89 da 4c 01 fa 72 35 4c 89 c0 48 2b 05 f7 d5 3d 
Jun 24 05:10:16 Merovingian kernel: [ 1789.505804] ---[ end trace dae745b31118a478 ]---
```

It's using an Intel graphic card, and it doesn't feel very hot when it crashes, so I don't think it's a proprietary driver blob or overheating.

Output of lspci:
```
00:00.0 Host bridge: Intel Corporation Atom Processor Z36xxx/Z37xxx Series SoC Transaction Register (rev 0e)
00:02.0 VGA compatible controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Graphics & Display (rev 0e)
00:13.0 SATA controller: Intel Corporation Atom Processor E3800 Series SATA AHCI Controller (rev 0e)
00:14.0 USB controller: Intel Corporation Atom Processor Z36xxx/Z37xxx, Celeron N2000 Series USB xHCI (rev 0e)
00:1a.0 Encryption controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Trusted Execution Engine (rev 0e)
00:1b.0 Audio device: Intel Corporation Atom Processor Z36xxx/Z37xxx Series High Definition Audio Controller (rev 0e)
00:1c.0 PCI bridge: Intel Corporation Atom Processor E3800 Series PCI Express Root Port 1 (rev 0e)
00:1c.1 PCI bridge: Intel Corporation Atom Processor E3800 Series PCI Express Root Port 2 (rev 0e)
00:1c.2 PCI bridge: Intel Corporation Atom Processor E3800 Series PCI Express Root Port 3 (rev 0e)
00:1c.3 PCI bridge: Intel Corporation Atom Processor E3800 Series PCI Express Root Port 4 (rev 0e)
00:1f.0 ISA bridge: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Power Control Unit (rev 0e)
00:1f.3 SMBus: Intel Corporation Atom Processor E3800 Series SMBus Controller (rev 0e)
02:00.0 Network controller: Broadcom Limited BCM43142 802.11b/g/n (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller (rev 07)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)

```

Output of lsusb:
```
Bus 002 Device 002: ID 0bda:0401 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 04f2:b40e Chicony Electronics Co., Ltd HP Truevision HD camera
Bus 001 Device 003: ID 0a5c:216c Broadcom Corp. BCM43142A0 Bluetooth Device
Bus 001 Device 004: ID 045e:00d1 Microsoft Corp. Optical Mouse with Tilt Wheel
Bus 001 Device 002: ID 0bda:5401 Realtek Semiconductor Corp. RTL 8153 USB 3.0 hub with gigabit ethernet
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by bodhin2 on 2018-06-27
might try a clean fresh install and do all updates/upgrades immediately

---

### Post by llamallord on 2018-07-13
I tried a live USB of 18.04 and it still hangs using that, which to me suggests that it's not a corrupted upgrade. I'm just not sure where to look for further clues. I look in kern.log.[1-4] and I see errors, but nothing consistent every time it hangs. For example, in kern.log.1 at the moment, it ends with:

> Jul  7 12:09:28 Merovingian kernel: [  240.630807] Could not find key with description: [d4628bf1c812c861]
Jul  7 12:09:28 Merovingian kernel: [  240.630816] process_request_key_err: No key
Jul  7 12:09:28 Merovingian kernel: [  240.630818] Could not find valid key in user session keyring for sig specified in mount option: [d4628bf1c812c861]
Jul  7 12:09:28 Merovingian kernel: [  240.630823] One or more global auth toks could not properly register; rc = [-2]
Jul  7 12:09:28 Merovingian kernel: [  240.630826] Error parsing options; rc = [-2]
Jul  7 12:09:50 Merovingian kernel: [  263.344863] Bluetooth: RFCOMM TTY layer initialized
Jul  7 12:09:50 Merovingian kernel: [  263.344884] Bluetooth: RFCOMM socket layer initialized
Jul  7 12:09:50 Merovingian kernel: [  263.344910] Bluetooth: RFCOMM ver 1.11
Jul  7 12:09:58 Merovingian kernel: [  271.011755] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
Jul  7 12:10:18 Merovingian kernel: [  290.840289] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
Jul  7 14:10:03 Merovingian kernel: [ 7479.040837] perf: interrupt took too long (2503 > 2500), lowering kernel.perf_event_max_sample_rate to 79750
Jul  7 14:47:30 Merovingian kernel: [ 9726.085836] perf: interrupt took too long (3136 > 3128), lowering kernel.perf_event_max_sample_rate to 63750
Jul  7 15:46:18 Merovingian kernel: [13255.819992] perf: interrupt took too long (3929 > 3920), lowering kernel.perf_event_max_sample_rate to 50750
Jul  7 16:56:17 Merovingian kernel: [17456.421031] perf: interrupt took too long (4934 > 4911), lowering kernel.perf_event_max_sample_rate to 40500
Jul  7 18:36:32 Merovingian kernel: [23473.938322] perf: interrupt took too long (6632 > 6167), lowering kernel.perf_event_max_sample_rate to 30000
Jul  8 00:00:41 Merovingian kernel: [42930.938038] perf: interrupt took too long (8358 > 8290), lowering kernel.perf_event_max_sample_rate to 23750
Jul  8 03:53:03 Merovingian kernel: [56878.324671] perf: interrupt took too long (11347 > 10447), lowering kernel.perf_event_max_sample_rate to 17500
Jul  8 21:19:46 Merovingian kernel: [119706.010537] [drm:intel_pipe_update_end [i915]] *ERROR* Atomic update failure on pipe A (start=96545 end=96546) time 394 us, min 763, max 767, scanline start 760, end 778

That last error makes it look like it may be related to [this bug]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1660619") however due to a launchpad error, I can't log in to add my info to it (such as that this is still happening on a Bionic / 18.04 system).

---

