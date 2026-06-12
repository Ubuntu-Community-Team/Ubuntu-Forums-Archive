---
title: "Need help tracking down problem, kernel i/o going oops."
date: 2006-09-02
forum: General Help
---

### Post by fubadubrub on 2006-09-02
My kernel i/o seems to be going oops.  I suspect my audio card.  Would like some opinions on possible causes and solutions.  Mostly happens with Flightgear CVS and once in a great while with Firefox stable release and I mean the Mozilla Firefox and not Ubuntu Firefox.  I have included the revelent sections from syslog, messages, kern below.

Kernel> Sep  1 00:34:21 localhost kernel: [17197075.796000] Unable to handle kernel NULL pointer dereference at virtual address 00000008
Sep  1 00:34:21 localhost kernel: [17197075.796000]  printing eip:
Sep  1 00:34:21 localhost kernel: [17197075.796000] f9d94648
Sep  1 00:34:21 localhost kernel: [17197075.796000] *pde = 00000000
Sep  1 00:34:21 localhost kernel: [17197075.796000] Oops: 0000 [#1]
Sep  1 00:34:21 localhost kernel: [17197075.796000] PREEMPT SMP 
Sep  1 00:34:21 localhost kernel: [17197075.796000] Modules linked in: nls_cp437 isofs udf rfcomm l2cap bluetooth ppdev speedstep_lib cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sony_acpi pcc_acpi hotkey dev_acpi container button acpi_sbs battery ac i2c_acpi_ec ext2 dm_mod md_mod sr_mod sbp2 parport_pc lp parport tsdev snd_emu10k1_synth snd_emux_synth snd_seq_virmidi snd_seq_midi_emul snd_seq_dummy snd_seq_oss snd_seq_midi snd_seq_midi_event snd_seq snd_emu10k1 ipv6 snd_rawmidi snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss cx88_blackbird snd_pcm snd_seq_device snd_timer tda9887 snd_page_alloc snd_util_mem psmouse snd_hwdep tuner cx88_dvb cx8802 mt352 or51132 video_buf_dvb dvb_core serio_raw snd nvidia nxt200x lgdt330x cx22702 dvb_pll cx8800 cx88xx i2c_algo_bit video_buf ir_common tveeprom i2c_core v4l1_compat v4l2_common soundcore btcx_risc pcspkr videodev usbhid emu10k1_gp gameport 8139too mii hw_random shpchp pci_hotplug intel_agp ag
Sep  1 00:34:21 localhost kernel: gart evdev sg ext3 jbd ide_generic ohci1394 ehci_hcd ieee1394 uhci_hcd usbcore sd_mod ata_piix libata scsi_mod ide_disk ide_cd cdrom piix generic thermal processor fan capability commoncap vga16fb vgastate fbcon tileblit font bitblit softcursor
Sep  1 00:34:21 localhost kernel: [17197075.796000] CPU:    0
Sep  1 00:34:21 localhost kernel: [17197075.796000] EIP:    0060:[pg0+965973576/1069167616]    Tainted: P      VLI
Sep  1 00:34:21 localhost kernel: [17197075.796000] EFLAGS: 00010286   (2.6.15-26-686) 
Sep  1 00:34:21 localhost kernel: [17197075.796000] EIP is at snd_emu10k1_pcm_init_voice+0x18/0x5f0 [snd_emu10k1]
Sep  1 00:34:21 localhost kernel: [17197075.796000] eax: 00000000   ebx: 00000000   ecx: 00001000   edx: f77029fc
Sep  1 00:34:21 localhost kernel: [17197075.796000] esi: cbd6bbc0   edi: 00000000   ebp: f7702000   esp: e06fbe44
Sep  1 00:34:21 localhost kernel: [17197075.796000] ds: 007b   es: 007b   ss: 0068
Sep  1 00:34:21 localhost kernel: [17197075.796000] Process fgfs (pid: 25510, threadinfo=e06fa000 task=c53b6560)
Sep  1 00:34:21 localhost kernel: [17197075.796000] Stack: c012ec84 e06fbe88 ffffffff 00000202 c012eed2 e06fbe88 e06fbe60 00000202 
Sep  1 00:34:21 localhost kernel: [17197075.796000]        e06fbe88 0041ad18 c012eef8 e06fbe88 e06fbe88 c030e135 00000001 cbd6bbc0 
Sep  1 00:34:21 localhost kernel: [17197075.796000]        f7702000 f7673780 f9d94ec0 f7702000 00000001 00000001 f77029fc 00001000 
Sep  1 00:34:21 localhost kernel: [17197075.796000] Call Trace:
Sep  1 00:34:21 localhost kernel: [17197075.796000]  [lock_timer_base+36/80] lock_timer_base+0x24/0x50
Sep  1 00:34:21 localhost kernel: [17197075.796000]  [try_to_del_timer_sync+82/96] try_to_del_timer_sync+0x52/0x60
Sep  1 00:34:21 localhost kernel: [17197075.796000]  [del_timer_sync+24/32] del_timer_sync+0x18/0x20
Sep  1 00:34:21 localhost kernel: [17197075.796000]  [schedule_timeout+85/192] schedule_timeout+0x55/0xc0
Sep  1 00:34:21 localhost kernel: [17197075.796000]  [pg0+965975744/1069167616] snd_emu10k1_playback_prepare+0x70/0x140 [snd_emu10k1]
Sep  1 00:34:21 localhost kernel: [17197075.796000]  [pg0+965336257/1069167616] snd_pcm_do_prepare+0x11/0x30 [snd_pcm]
Sep  1 00:34:21 localhost kernel: [17197075.796000]  [pg0+965332792/1069167616] snd_pcm_action_single+0x38/0x90 [snd_pcm]
Sep  1 00:34:21 localhost kernel: [17197075.796000]  [pg0+965333424/1069167616] snd_pcm_action_nonatomic+0x80/0x90 [snd_pcm]
Sep  1 00:34:21 localhost kernel: [17197075.796000]  [pg0+965336420/1069167616] snd_pcm_prepare+0x54/0x80 [snd_pcm]
Sep  1 00:34:21 localhost kernel: [17197075.796000]  [pg0+965346866/1069167616] snd_pcm_playback_ioctl1+0x52/0x300 [snd_pcm]
Sep  1 00:34:21 localhost kernel: [17197075.796000]  [do_ioctl+59/160] do_ioctl+0x3b/0xa0
Sep  1 00:34:21 localhost kernel: [17197075.796000]  [vfs_ioctl+107/560] vfs_ioctl+0x6b/0x230
Sep  1 00:34:21 localhost kernel: [17197075.796000]  [sys_ioctl+136/160] sys_ioctl+0x88/0xa0
Sep  1 00:34:21 localhost kernel: [17197075.796000]  [sysenter_past_esp+84/117] sysenter_past_esp+0x54/0x75
Sep  1 00:34:21 localhost kernel: [17197075.796000] Code: 8d 76 00 c3 eb 0d 90 90 90 90 90 90 90 90 90 90 90 90 90 55 57 56 53 31 db 83 ec 38 8b 54 24 58 8b 6c 24 4c 8b 7c 24 64 8b 42 10 <8b> 40 08 8b 40 5c 89 44 24 18 8b 4c 24 18 83 78 2c 02 8b 72 04messages> Sep  2 15:14:09 localhost kernel: [17180230.424000] f8c4e648
Sep  2 15:14:09 localhost kernel: [17180230.424000] PREEMPT SMP 
Sep  2 15:14:09 localhost kernel: [17180230.424000] Modules linked in: joydev rfcomm l2cap bluetooth ppdev speedstep_lib cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sony_acpi pcc_acpi hotkey dev_acpi container button acpi_sbs battery ac i2c_acpi_ec ext2 dm_mod md_mod sr_mod sbp2 parport_pc lp parport cx88_blackbird snd_emu10k1_synth snd_emux_synth snd_seq_virmidi snd_seq_midi_emul snd_seq_dummy snd_seq_oss snd_seq_midi snd_seq_midi_event snd_seq tda9887 tuner ipv6 snd_emu10k1 snd_rawmidi snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_device snd_timer snd_page_alloc snd_util_mem cx88_dvb cx8802 snd_hwdep snd cx8800 cx88xx emu10k1_gp mt352 or51132 video_buf_dvb dvb_core i2c_algo_bit gameport ir_common video_buf nxt200x tveeprom lgdt330x soundcore cx22702 dvb_pll v4l1_compat v4l2_common btcx_risc videodev 8139too mii tsdev hw_random pcspkr usbhid nvidia i2c_core shpchp pci_hotplug psmouse serio_raw intel_agp agpgart sg evde
Sep  2 15:14:09 localhost kernel:  ext3 jbd ide_generic ohci1394 ieee1394 ehci_hcd uhci_hcd usbcore sd_mod ata_piix libata scsi_mod ide_cd ide_disk cdrom piix generic thermal processor fan capability commoncap vga16fb vgastate fbcon tileblit font bitblit softcursor
Sep  2 15:14:09 localhost kernel: [17180230.424000] CPU:    0
Sep  2 15:14:09 localhost kernel: [17180230.424000] EIP:    0060:[pg0+947861064/1069167616]    Tainted: P      VLI
Sep  2 15:14:09 localhost kernel: [17180230.424000] EFLAGS: 00210286   (2.6.15-26-686) 
Sep  2 15:14:09 localhost kernel: [17180230.424000] EIP is at snd_emu10k1_pcm_init_voice+0x18/0x5f0 [snd_emu10k1]
Sep  2 15:14:09 localhost kernel: [17180230.424000] eax: 00000000   ebx: 00000000   ecx: 00001000   edx: dfb5a77c
Sep  2 15:14:09 localhost kernel: [17180230.424000] esi: f71f76c0   edi: 00000000   ebp: dfb5a000   esp: f543fe44
Sep  2 15:14:09 localhost kernel: [17180230.424000] ds: 007b   es: 007b   ss: 0068
Sep  2 15:14:09 localhost kernel: [17180230.424000] Process fgfs (pid: 6254, threadinfo=f543e000 task=f735ba90)
Sep  2 15:14:09 localhost kernel: [17180230.424000] Stack: c012ec84 f543fe88 ffffffff 00200202 c012eed2 f543fe88 f543fe60 00200202 
Sep  2 15:14:09 localhost kernel: [17180230.424000]        f543fe88 00016a87 c012eef8 f543fe88 f543fe88 c030e135 00000001 f71f76c0 
Sep  2 15:14:09 localhost kernel: [17180230.424000]        dfb5a000 f74e08c0 f8c4eec0 dfb5a000 00000001 00000001 dfb5a77c 00001000 
Sep  2 15:14:09 localhost kernel: [17180230.424000] Call Trace:
Sep  2 15:14:09 localhost kernel: [17180230.424000]  [lock_timer_base+36/80] lock_timer_base+0x24/0x50
Sep  2 15:14:09 localhost kernel: [17180230.424000]  [try_to_del_timer_sync+82/96] try_to_del_timer_sync+0x52/0x60
Sep  2 15:14:09 localhost kernel: [17180230.424000]  [del_timer_sync+24/32] del_timer_sync+0x18/0x20
Sep  2 15:14:09 localhost kernel: [17180230.424000]  [schedule_timeout+85/192] schedule_timeout+0x55/0xc0
Sep  2 15:14:09 localhost kernel: [17180230.424000]  [pg0+947863232/1069167616] snd_emu10k1_playback_prepare+0x70/0x140 [snd_emu10k1]
Sep  2 15:14:09 localhost kernel: [17180230.424000]  [pg0+947223745/1069167616] snd_pcm_do_prepare+0x11/0x30 [snd_pcm]
Sep  2 15:14:09 localhost kernel: [17180230.424000]  [pg0+947220280/1069167616] snd_pcm_action_single+0x38/0x90 [snd_pcm]
Sep  2 15:14:09 localhost kernel: [17180230.424000]  [pg0+947220912/1069167616] snd_pcm_action_nonatomic+0x80/0x90 [snd_pcm]
Sep  2 15:14:09 localhost kernel: [17180230.424000]  [pg0+947223908/1069167616] snd_pcm_prepare+0x54/0x80 [snd_pcm]
Sep  2 15:14:09 localhost kernel: [17180230.424000]  [pg0+947234354/1069167616] snd_pcm_playback_ioctl1+0x52/0x300 [snd_pcm]
Sep  2 15:14:09 localhost kernel: [17180230.424000]  [do_ioctl+59/160] do_ioctl+0x3b/0xa0
Sep  2 15:14:09 localhost kernel: [17180230.424000]  [vfs_ioctl+107/560] vfs_ioctl+0x6b/0x230
Sep  2 15:14:09 localhost kernel: [17180230.424000]  [sys_ioctl+136/160] sys_ioctl+0x88/0xa0
Sep  2 15:14:09 localhost kernel: [17180230.424000]  [sysenter_past_esp+84/117] sysenter_past_esp+0x54/0x75
Sep  2 15:14:09 localhost kernel: [17180230.424000] Code: 8d 76 00 c3 eb 0d 90 90 90 90 90 90 90 90 90 90 90 90 90 55 57 56 53 31 db 83 ec 38 8b 54 24 58 8b 6c 24 4c 8b 7c 24 64 8b 42 10 <8b> 40 08 8b 40 5c 89 44 24 18 8b 4c 24 18 83 78 2c 02 8b 72 04syslog> Sep  2 15:01:03 localhost kernel: [17261428.824000] Unable to handle kernel NULL pointer dereference at virtual address 00000008
Sep  2 15:01:03 localhost kernel: [17261428.824000]  printing eip:
Sep  2 15:01:03 localhost kernel: [17261428.824000] f8bb5648
Sep  2 15:01:03 localhost kernel: [17261428.824000] *pde = 00000000
Sep  2 15:01:03 localhost kernel: [17261428.824000] Oops: 0000 [#1]
Sep  2 15:01:03 localhost kernel: [17261428.824000] PREEMPT SMP 
Sep  2 15:01:03 localhost kernel: [17261428.824000] Modules linked in: joydev rfcomm l2cap bluetooth ppdev speedstep_lib cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sony_acpi pcc_acpi hotkey dev_acpi container button acpi_sbs battery ac i2c_acpi_ec ext2 dm_mod md_mod sr_mod sbp2 parport_pc lp parport cx88_blackbird ipv6 tda9887 tuner snd_emu10k1_synth snd_emux_synth snd_seq_virmidi snd_seq_midi_emul snd_seq_dummy snd_seq_oss cx8800 cx88_dvb cx8802 cx88xx snd_seq_midi snd_seq_midi_event i2c_algo_bit snd_seq ir_common tveeprom mt352 or51132 video_buf_dvb tsdev dvb_core v4l1_compat video_buf nxt200x 8139too emu10k1_gp lgdt330x cx22702 dvb_pll mii usbhid gameport snd_emu10k1 snd_rawmidi snd_ac97_codec snd_ac97_bus v4l2_common snd_pcm_oss snd_mixer_oss btcx_risc videodev snd_pcm snd_seq_device snd_timer snd_page_alloc snd_util_mem snd_hwdep snd soundcore pcspkr intel_agp hw_random nvidia agpgart i2c_core psmouse serio_raw shpchp pci_hotplug sg evde
Sep  2 15:01:03 localhost kernel:  ext3 jbd ide_generic ohci1394 ieee1394 uhci_hcd ehci_hcd usbcore sd_mod ata_piix libata scsi_mod ide_cd cdrom ide_disk piix generic thermal processor fan capability commoncap vga16fb vgastate fbcon tileblit font bitblit softcursor
Sep  2 15:01:03 localhost kernel: [17261428.824000] CPU:    0
Sep  2 15:01:03 localhost kernel: [17261428.824000] EIP:    0060:[pg0+947234376/1069167616]    Tainted: P      VLI
Sep  2 15:01:03 localhost kernel: [17261428.824000] EFLAGS: 00210286   (2.6.15-26-686) 
Sep  2 15:01:03 localhost kernel: [17261428.824000] EIP is at snd_emu10k1_pcm_init_voice+0x18/0x5f0 [snd_emu10k1]
Sep  2 15:01:03 localhost kernel: [17261428.824000] eax: 00000000   ebx: 00000000   ecx: 00001000   edx: f789c68c
Sep  2 15:01:03 localhost kernel: [17261428.824000] esi: f1a248c0   edi: 00000000   ebp: f789c000   esp: ce003e44
Sep  2 15:01:03 localhost kernel: [17261428.824000] ds: 007b   es: 007b   ss: 0068
Sep  2 15:01:03 localhost kernel: [17261428.824000] Process fgfs (pid: 8265, threadinfo=ce002000 task=f1901560)
Sep  2 15:01:03 localhost kernel: [17261428.824000] Stack: c012ec84 ce003e88 ffffffff 00200202 c012eed2 ce003e88 ce003e60 00200202 
Sep  2 15:01:03 localhost kernel: [17261428.824000]        ce003e88 013729d9 c012eef8 ce003e88 ce003e88 c030e135 00000001 f1a248c0 
Sep  2 15:01:03 localhost kernel: [17261428.824000]        f789c000 f781b180 f8bb5ec0 f789c000 00000001 00000001 f789c68c 00001000 
Sep  2 15:01:03 localhost kernel: [17261428.824000] Call Trace:
Sep  2 15:01:03 localhost kernel: [17261428.824000]  [lock_timer_base+36/80] lock_timer_base+0x24/0x50
Sep  2 15:01:03 localhost kernel: [17261428.824000]  [try_to_del_timer_sync+82/96] try_to_del_timer_sync+0x52/0x60
Sep  2 15:01:03 localhost kernel: [17261428.824000]  [del_timer_sync+24/32] del_timer_sync+0x18/0x20
Sep  2 15:01:03 localhost kernel: [17261428.824000]  [schedule_timeout+85/192] schedule_timeout+0x55/0xc0
Sep  2 15:01:03 localhost kernel: [17261428.824000]  [pg0+947236544/1069167616] snd_emu10k1_playback_prepare+0x70/0x140 [snd_emu10k1]
Sep  2 15:01:03 localhost kernel: [17261428.824000]  [pg0+946597057/1069167616] snd_pcm_do_prepare+0x11/0x30 [snd_pcm]
Sep  2 15:01:03 localhost kernel: [17261428.824000]  [pg0+946593592/1069167616] snd_pcm_action_single+0x38/0x90 [snd_pcm]
Sep  2 15:01:03 localhost kernel: [17261428.824000]  [pg0+946594224/1069167616] snd_pcm_action_nonatomic+0x80/0x90 [snd_pcm]
Sep  2 15:01:03 localhost kernel: [17261428.824000]  [pg0+946597220/1069167616] snd_pcm_prepare+0x54/0x80 [snd_pcm]
Sep  2 15:01:03 localhost kernel: [17261428.824000]  [pg0+946607666/1069167616] snd_pcm_playback_ioctl1+0x52/0x300 [snd_pcm]
Sep  2 15:01:03 localhost kernel: [17261428.824000]  [do_ioctl+59/160] do_ioctl+0x3b/0xa0
Sep  2 15:01:03 localhost kernel: [17261428.824000]  [vfs_ioctl+107/560] vfs_ioctl+0x6b/0x230
Sep  2 15:01:03 localhost kernel: [17261428.824000]  [sys_ioctl+136/160] sys_ioctl+0x88/0xa0
Sep  2 15:01:03 localhost kernel: [17261428.824000]  [sysenter_past_esp+84/117] sysenter_past_esp+0x54/0x75
Sep  2 15:01:03 localhost kernel: [17261428.824000] Code: 8d 76 00 c3 eb 0d 90 90 90 90 90 90 90 90 90 90 90 90 90 55 57 56 53 31 db 83 ec 38 8b 54 24 58 8b 6c 24 4c 8b 7c 24 64 8b 42 10 <8b> 40 08 8b 40 5c 89 44 24 18 8b 4c 24 18 83 78 2c 02 8b 72 04



Sep  2 15:14:09 localhost kernel: [17180230.424000] Unable to handle kernel NULL pointer dereference at virtual address 00000008
Sep  2 15:14:09 localhost kernel: [17180230.424000]  printing eip:
Sep  2 15:14:09 localhost kernel: [17180230.424000] f8c4e648
Sep  2 15:14:09 localhost kernel: [17180230.424000] *pde = 00000000
Sep  2 15:14:09 localhost kernel: [17180230.424000] Oops: 0000 [#1]
Sep  2 15:14:09 localhost kernel: [17180230.424000] PREEMPT SMP 
Sep  2 15:14:09 localhost kernel: [17180230.424000] Modules linked in: joydev rfcomm l2cap bluetooth ppdev speedstep_lib cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sony_acpi pcc_acpi hotkey dev_acpi container button acpi_sbs battery ac i2c_acpi_ec ext2 dm_mod md_mod sr_mod sbp2 parport_pc lp parport cx88_blackbird snd_emu10k1_synth snd_emux_synth snd_seq_virmidi snd_seq_midi_emul snd_seq_dummy snd_seq_oss snd_seq_midi snd_seq_midi_event snd_seq tda9887 tuner ipv6 snd_emu10k1 snd_rawmidi snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_device snd_timer snd_page_alloc snd_util_mem cx88_dvb cx8802 snd_hwdep snd cx8800 cx88xx emu10k1_gp mt352 or51132 video_buf_dvb dvb_core i2c_algo_bit gameport ir_common video_buf nxt200x tveeprom lgdt330x soundcore cx22702 dvb_pll v4l1_compat v4l2_common btcx_risc videodev 8139too mii tsdev hw_random pcspkr usbhid nvidia i2c_core shpchp pci_hotplug psmouse serio_raw intel_agp agpgart sg evde
Sep  2 15:14:09 localhost kernel:  ext3 jbd ide_generic ohci1394 ieee1394 ehci_hcd uhci_hcd usbcore sd_mod ata_piix libata scsi_mod ide_cd ide_disk cdrom piix generic thermal processor fan capability commoncap vga16fb vgastate fbcon tileblit font bitblit softcursor
Sep  2 15:14:09 localhost kernel: [17180230.424000] CPU:    0
Sep  2 15:14:09 localhost kernel: [17180230.424000] EIP:    0060:[pg0+947861064/1069167616]    Tainted: P      VLI
Sep  2 15:14:09 localhost kernel: [17180230.424000] EFLAGS: 00210286   (2.6.15-26-686) 
Sep  2 15:14:09 localhost kernel: [17180230.424000] EIP is at snd_emu10k1_pcm_init_voice+0x18/0x5f0 [snd_emu10k1]
Sep  2 15:14:09 localhost kernel: [17180230.424000] eax: 00000000   ebx: 00000000   ecx: 00001000   edx: dfb5a77c
Sep  2 15:14:09 localhost kernel: [17180230.424000] esi: f71f76c0   edi: 00000000   ebp: dfb5a000   esp: f543fe44
Sep  2 15:14:09 localhost kernel: [17180230.424000] ds: 007b   es: 007b   ss: 0068
Sep  2 15:14:09 localhost kernel: [17180230.424000] Process fgfs (pid: 6254, threadinfo=f543e000 task=f735ba90)
Sep  2 15:14:09 localhost kernel: [17180230.424000] Stack: c012ec84 f543fe88 ffffffff 00200202 c012eed2 f543fe88 f543fe60 00200202 
Sep  2 15:14:09 localhost kernel: [17180230.424000]        f543fe88 00016a87 c012eef8 f543fe88 f543fe88 c030e135 00000001 f71f76c0 
Sep  2 15:14:09 localhost kernel: [17180230.424000]        dfb5a000 f74e08c0 f8c4eec0 dfb5a000 00000001 00000001 dfb5a77c 00001000 
Sep  2 15:14:09 localhost kernel: [17180230.424000] Call Trace:
Sep  2 15:14:09 localhost kernel: [17180230.424000]  [lock_timer_base+36/80] lock_timer_base+0x24/0x50
Sep  2 15:14:09 localhost kernel: [17180230.424000]  [try_to_del_timer_sync+82/96] try_to_del_timer_sync+0x52/0x60
Sep  2 15:14:09 localhost kernel: [17180230.424000]  [del_timer_sync+24/32] del_timer_sync+0x18/0x20
Sep  2 15:14:09 localhost kernel: [17180230.424000]  [schedule_timeout+85/192] schedule_timeout+0x55/0xc0
Sep  2 15:14:09 localhost kernel: [17180230.424000]  [pg0+947863232/1069167616] snd_emu10k1_playback_prepare+0x70/0x140 [snd_emu10k1]
Sep  2 15:14:09 localhost kernel: [17180230.424000]  [pg0+947223745/1069167616] snd_pcm_do_prepare+0x11/0x30 [snd_pcm]
Sep  2 15:14:09 localhost kernel: [17180230.424000]  [pg0+947220280/1069167616] snd_pcm_action_single+0x38/0x90 [snd_pcm]
Sep  2 15:14:09 localhost kernel: [17180230.424000]  [pg0+947220912/1069167616] snd_pcm_action_nonatomic+0x80/0x90 [snd_pcm]
Sep  2 15:14:09 localhost kernel: [17180230.424000]  [pg0+947223908/1069167616] snd_pcm_prepare+0x54/0x80 [snd_pcm]
Sep  2 15:14:09 localhost kernel: [17180230.424000]  [pg0+947234354/1069167616] snd_pcm_playback_ioctl1+0x52/0x300 [snd_pcm]
Sep  2 15:14:09 localhost kernel: [17180230.424000]  [do_ioctl+59/160] do_ioctl+0x3b/0xa0
Sep  2 15:14:09 localhost kernel: [17180230.424000]  [vfs_ioctl+107/560] vfs_ioctl+0x6b/0x230
Sep  2 15:14:09 localhost kernel: [17180230.424000]  [sys_ioctl+136/160] sys_ioctl+0x88/0xa0
Sep  2 15:14:09 localhost kernel: [17180230.424000]  [sysenter_past_esp+84/117] sysenter_past_esp+0x54/0x75
Sep  2 15:14:09 localhost kernel: [17180230.424000] Code: 8d 76 00 c3 eb 0d 90 90 90 90 90 90 90 90 90 90 90 90 90 55 57 56 53 31 db 83 ec 38 8b 54 24 58 8b 6c 24 4c 8b 7c 24 64 8b 42 10 <8b> 40 08 8b 40 5c 89 44 24 18 8b 4c 24 18 83 78 2c 02 8b 72 04

---

### Post by orb9220 on 2006-09-03
I would have to agree with you on soundcard.

CPU: 0
Tainted: P VLI
localhost kernel: [17180230.424000] 
EFLAGS: 00210286 (2.6.15-26-686)
EIP is at snd_emu10k1_pcm_init_voice+0x18/0x5f0 [snd_emu10k1]
localhost kernel: [17180230.424000] eax: 00000000 ebx: 00000000 ecx: 00001000 edx: dfb5a77c
localhost kernel: [17180230.424000] esi: f71f76c0 edi: 00000000 ebp: dfb5a000 esp: f543fe44
localhost kernel: [17180230.424000] ds: 007b es: 007b ss: 0068

Tells me anyway to unistall sound card or if it is onboard disable it in the bios and see if you still get them.

---

### Post by fubadubrub on 2006-09-04
Sorry to take so long to get back to you.  Any way I disabled the esd and removed alsa from rc scripts, but that does nothing.  Removing my audio card would be a real pain and since I was going to be installing edgy, well I just left it in.  I got edgy up and running now and since edgy comes with flightgear 0.9.10, I can use the built in flightgear instead of cvs.  So no audio i/o problems as of now.  Thanks for the reply.> **orb9220 said:**
> I would have to agree with you on soundcard.

CPU: 0
Tainted: P VLI
localhost kernel: [17180230.424000] 
EFLAGS: 00210286 (2.6.15-26-686)
EIP is at snd_emu10k1_pcm_init_voice+0x18/0x5f0 [snd_emu10k1]
localhost kernel: [17180230.424000] eax: 00000000 ebx: 00000000 ecx: 00001000 edx: dfb5a77c
localhost kernel: [17180230.424000] esi: f71f76c0 edi: 00000000 ebp: dfb5a000 esp: f543fe44
localhost kernel: [17180230.424000] ds: 007b es: 007b ss: 0068

Tells me anyway to unistall sound card or if it is onboard disable it in the bios and see if you still get them.

---

