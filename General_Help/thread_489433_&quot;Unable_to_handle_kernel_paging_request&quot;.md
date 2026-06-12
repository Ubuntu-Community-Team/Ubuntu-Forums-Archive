---
title: "&quot;Unable to handle kernel paging request&quot;"
date: 2007-07-01
forum: General Help
---

### Post by jdaverin on 2007-07-01
I am fairly newbish when it comes to Linux sysadmin tasks and kernel troubleshooting, so I was hoping to get some pointers from some folks maybe more experienced than I. I've set up a dual-boot Ubuntu/WinXP system and am having a recurrent but not directly reproducible problem in the Ubuntu boot that doesn't happen in the Windows boot. Every so often, after between 1 and 72 hours of runtime, "something" will happen, after which the keyboard stops responding. Originally I had set up a PS/2 keyboard, so I tried a USB but no luck, detaching and reattaching the keyboard doesn't help. Whatever numlock/capslock options were lit stay lit. Throughout all this the mouse works perfectly fine. The only way I've found to get the keyboard to go active again is restart the computer.

The last time it happened I checked around in /var/log to see if there was anything suspicious and found this in /var/log/syslog at about the time the keyboard freeze and found what is below. If anyone had a spare moment to glance over it and maybe suggest something that might be a problem. It's just a home machine so it's not really critical if it has to be rebooted occaisionally, but it's certainly a pain in the neck.

-------------------------------------------------------------------------------------------------------------------

Jul  1 09:34:34 joe kernel: [17218779.904000] Unable to handle kernel paging request at virtual address bef3917c
Jul  1 09:34:34 joe kernel: [17218779.904000]  printing eip:
Jul  1 09:34:34 joe kernel: [17218779.904000] c01496d3
Jul  1 09:34:34 joe kernel: [17218779.904000] *pde = 00000000
Jul  1 09:34:34 joe kernel: [17218779.904000] Oops: 0000 [#1]
Jul  1 09:34:34 joe kernel: [17218779.904000] PREEMPT 
Jul  1 09:34:34 joe kernel: [17218779.904000] Modules linked in: rfcomm l2cap bluetooth ppdev powernow_k8 cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sony_acpi pcc_acpi hotkey dev_acpi container button acpi_sbs battery ac i2c_acpi_ec nls_utf8 ntfs nls_iso8859_1 nls_cp437 vfat fat ipv6 dm_mod af_packet md_mod sr_mod sbp2 lp snd_emu10k1_synth snd_emux_synth snd_seq_virmidi snd_seq_midi_emul snd_seq_dummy snd_seq_oss snd_seq_midi snd_seq_midi_event snd_seq ltmodem snd_emu10k1 snd_rawmidi snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_device snd_timer snd_page_alloc snd_util_mem snd_hwdep snd soundcore emu10k1_gp gameport usblp forcedeth rtc pcspkr nvidia parport_pc parport floppy shpchp pci_hotplug psmouse serio_raw i2c_nforce2 i2c_core amd64_agp agpgart sg sd_mod tsdev evdev usbhid usb_storage ext3 jbd ide_generic ohci1394 ieee1394 ehci_hcd ohci_hcd usbcore ide_cd cdrom ide_disk generic amd74xx sata_nv libata scsi_mo
Jul  1 09:34:34 joe kernel:  thermal processor fan capability commoncap vga16fb vgastate fbcon tileblit font bitblit softcursor
Jul  1 09:34:34 joe kernel: [17218779.904000] CPU:    0
Jul  1 09:34:34 joe kernel: [17218779.904000] EIP:    0060:[cache_reap+147/448]    Tainted: P      VLI
Jul  1 09:34:34 joe kernel: [17218779.904000] EFLAGS: 00010086   (2.6.15-28-386) 
Jul  1 09:34:34 joe kernel: [17218779.904000] EIP is at cache_reap+0x93/0x1c0
Jul  1 09:34:34 joe kernel: [17218779.904000] eax: 00946ec0   ebx: dfffdd50   ecx: 00000032   edx: 65636976
Jul  1 09:34:34 joe kernel: [17218779.904000] esi: c0fffdc0   edi: c0fffe0c   ebp: bef39160   esp: df97bf44
Jul  1 09:34:34 joe kernel: [17218779.904000] ds: 007b   es: 007b   ss: 0068
Jul  1 09:34:34 joe kernel: [17218779.904000] Process events/0 (pid: 4, threadinfo=df97a000 task=dffdea70)
Jul  1 09:34:34 joe kernel: [17218779.904000] Stack: df97a000 dfffdd50 00000002 df97a000 c04055e0 c04055e4 00000206 00000000 
Jul  1 09:34:34 joe kernel: [17218779.904000]        c012cb0a 00000000 df97a000 df9746d8 df9746c8 df9746d0 df97a000 c0149640 
Jul  1 09:34:34 joe kernel: [17218779.904000]        df97a000 00000001 00000000 02e7c400 00010000 00000000 00000000 dffdea70 
Jul  1 09:34:34 joe kernel: [17218779.904000] Call Trace:
Jul  1 09:34:34 joe kernel: [17218779.904000]  [worker_thread+442/656] worker_thread+0x1ba/0x290
Jul  1 09:34:34 joe kernel: [17218779.904000]  [cache_reap+0/448] cache_reap+0x0/0x1c0
Jul  1 09:34:34 joe kernel: [17218779.904000]  [default_wake_function+0/32] default_wake_function+0x0/0x20
Jul  1 09:34:34 joe kernel: [17218779.904000]  [worker_thread+0/656] worker_thread+0x0/0x290
Jul  1 09:34:34 joe kernel: [17218779.904000]  [kthread+147/160] kthread+0x93/0xa0
Jul  1 09:34:34 joe kernel: [17218779.904000]  [kthread+0/160] kthread+0x0/0xa0
Jul  1 09:34:34 joe kernel: [17218779.904000]  [kernel_thread_helper+5/16] kernel_thread_helper+0x5/0x10
Jul  1 09:34:34 joe kernel: [17218779.904000] Code: 00 8d 77 b4 f6 46 19 10 75 de 8b 6e 14 fa 8b 54 24 0c ff 42 14 6a 00 6a 00 8b 47 b4 50 56 e8 d5 fe ff ff a1 98 75 33 c0 83 c4 10 <3b> 45 1c 78 30 a1 98 75 33 c0 05 e8 03 00 00 89 45 1c 8b 45 28 
Jul  1 09:34:34 joe kernel: [17218779.904000]  <6>note: events/0[4] exited with preempt_count 1

---

