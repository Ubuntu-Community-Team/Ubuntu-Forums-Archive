---
title: "How to handle &quot;Kernel BUG&quot; line in log file?"
date: 2008-03-16
forum: General Help
---

### Post by kkinder on 2008-03-16
I've been trying to isolate a problem that's been plaguing me recently -- on my IBM Thinkpad T41, with Ubuntu 7.10 and kernel 2.6.22-14-386, my system seems to crash hard, often with a blinking caps lock. This seems to happen when I'm trying to connect or have recently connected with my wifi card, although I don't know if that's connected.

My wifi driver is a airo. That is using a AIRONET Wireless Communications Cisco Aironet Wireless 802.11b.

I was watching syslog in a window when it happened. There are a several of these lines:

```
Mar 16 00:03:28 kkinder-laptop kernel: [  306.664000] airo(eth1): Max tries exceeded when issueing command
Mar 16 00:03:29 kkinder-laptop kernel: [  307.688000] airo(eth1): Max tries exceeded when issueing command
Mar 16 00:03:30 kkinder-laptop kernel: [  308.704000] airo(eth1): Max tries exceeded when issueing command
```

That was all that was visible. But here's what it said after that after I rebooted and looked at syslog:

```
Mar 16 00:03:30 kkinder-laptop kernel: [  308.712000] BUG: unable to handle kernel NULL pointer dereference at virtual address 00000000
Mar 16 00:03:30 kkinder-laptop kernel: [  308.712000]  printing eip:
Mar 16 00:03:30 kkinder-laptop kernel: [  308.712000] 00000000
Mar 16 00:03:30 kkinder-laptop kernel: [  308.712000] *pde = 00000000
Mar 16 00:03:30 kkinder-laptop kernel: [  308.712000] Oops: 0000 [#1]
Mar 16 00:03:30 kkinder-laptop kernel: [  308.712000] SMP 
Mar 16 00:03:30 kkinder-laptop kernel: [  308.712000] Modules linked in: af_packet rfcomm l2cap bluetooth thinkpad_acpi ppdev radeon drm ipv6 speedstep_centrino cpufreq_userspace cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table cpufreq_conservative video sbs button bay dock battery container ac nls_iso8859_1 nls_cp437 vfat fat lp snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm joydev irtty_sir sir_dev snd_seq_dummy snd_seq_oss snd_seq_midi nsc_ircc snd_rawmidi irda snd_seq_midi_event snd_seq snd_timer snd_seq_device crc_ccitt parport_pc snd psmouse pcmcia parport serio_raw soundcore aes pcspkr snd_page_alloc airo iTCO_wdt yenta_socket rsrc_nonstatic pcmcia_core iTCO_vendor_support intel_agp agpgart shpchp pci_hotplug evdev ext3 jbd mbcache sg sr_mod cdrom sd_mod floppy ata_piix e1000 ata_generic libata scsi_mod ehci_hcd uhci_hcd usbcore thermal processor fan fuse apparmor commoncap
Mar 16 00:03:30 kkinder-laptop kernel: [  308.712000] CPU:    0
Mar 16 00:03:30 kkinder-laptop kernel: [  308.712000] EIP:    0060:[<00000000>]    Not tainted VLI
Mar 16 00:03:30 kkinder-laptop kernel: [  308.712000] EFLAGS: 00210256   (2.6.22-14-generic #1)
Mar 16 00:03:30 kkinder-laptop kernel: [  308.712000] EIP is at 0x0
Mar 16 00:03:30 kkinder-laptop kernel: [  308.712000] eax: f4865240   ebx: f5014874   ecx: 00000000   edx: f4f13c00
Mar 16 00:03:30 kkinder-laptop kernel: [  308.712000] esi: 00000020   edi: f4865240   ebp: 00000000   esp: f5017b80
Mar 16 00:03:30 kkinder-laptop kernel: [  308.712000] ds: 007b   es: 007b   fs: 00d8  gs: 0033  ss: 0068
Mar 16 00:03:30 kkinder-laptop kernel: [  308.712000] Process artsd (pid: 5733, ti=f5016000 task=f48099f0 task.ti=f5016000)
Mar 16 00:03:30 kkinder-laptop kernel: [  308.712000] Stack: c0277e0c 00000005 c018dabe f5017bec f4557cf0 00000020 f5017f9c f5017f54 
Mar 16 00:03:30 kkinder-laptop kernel: [  308.712000]        00000000 00000000 00000000 f5017e60 f5017e64 f5017e68 f5017e58 f5017e5c 
Mar 16 00:03:30 kkinder-laptop kernel: [  308.712000]        f5017e60 00000028 00000000 00000020 00000028 00000000 00000000 00000000 
Mar 16 00:03:30 kkinder-laptop kernel: [  308.712000] Call Trace:
Mar 16 00:03:30 kkinder-laptop kernel: [  308.712000]  [sock_poll+12/16] sock_poll+0xc/0x10
Mar 16 00:03:30 kkinder-laptop kernel: [  308.712000]  [do_select+606/1168] do_select+0x25e/0x490
Mar 16 00:03:30 kkinder-laptop kernel: [  308.712000]  [__pollwait+0/240] __pollwait+0x0/0xf0
Mar 16 00:03:30 kkinder-laptop kernel: [  308.712000]  [default_wake_function+0/16] default_wake_function+0x0/0x10
Mar 16 00:03:30 kkinder-laptop last message repeated 2 times
Mar 16 00:03:30 kkinder-laptop kernel: [  308.712000]  [<f88db9f9>] scsi_io_completion+0xa9/0x440 [scsi_mod]
Mar 16 00:03:30 kkinder-laptop kernel: [  308.712000]  [__activate_task+33/64] __activate_task+0x21/0x40
Mar 16 00:03:30 kkinder-laptop kernel: [  308.712000]  [try_to_wake_up+70/1152] try_to_wake_up+0x46/0x480
Mar 16 00:03:30 kkinder-laptop kernel: [  308.712000]  [<f8a61a0d>] airo_interrupt+0x5d/0x1160 [airo]
Mar 16 00:03:30 kkinder-laptop kernel: [  308.712000]  [<f88fd68e>] __ata_qc_complete+0x4e/0xa0 [libata]
Mar 16 00:03:30 kkinder-laptop kernel: [  308.712000]  [getnstimeofday+54/208] getnstimeofday+0x36/0xd0
Mar 16 00:03:30 kkinder-laptop kernel: [  308.712000]  [__sigqueue_alloc+45/128] __sigqueue_alloc+0x2d/0x80
Mar 16 00:03:30 kkinder-laptop kernel: [  308.712000]  [signal_wake_up+30/48] signal_wake_up+0x1e/0x30
Mar 16 00:03:30 kkinder-laptop kernel: [  308.712000]  [__group_send_sig_info+107/144] __group_send_sig_info+0x6b/0x90
Mar 16 00:03:30 kkinder-laptop kernel: [  308.712000]  [sys_semctl+252/2576] sys_semctl+0xfc/0xa10
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [handle_IRQ_event+48/96] handle_IRQ_event+0x30/0x60
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [__pagevec_free+31/48] __pagevec_free+0x1f/0x30
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [release_pages+325/384] release_pages+0x145/0x180
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [__activate_task+33/64] __activate_task+0x21/0x40
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [try_to_wake_up+70/1152] try_to_wake_up+0x46/0x480
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [__activate_task+33/64] __activate_task+0x21/0x40
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [try_to_wake_up+70/1152] try_to_wake_up+0x46/0x480
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [try_to_wake_up+70/1152] try_to_wake_up+0x46/0x480
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [__activate_task+33/64] __activate_task+0x21/0x40
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [core_sys_select+456/768] core_sys_select+0x1c8/0x300
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [save_i387+338/368] save_i387+0x152/0x170
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [setup_sigcontext+260/400] setup_sigcontext+0x104/0x190
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [autoremove_wake_function+27/80] autoremove_wake_function+0x1b/0x50
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [__wake_up_common+57/96] __wake_up_common+0x39/0x60
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [__wake_up+56/80] __wake_up+0x38/0x50
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [acpi_ec_gpe_handler+44/97] acpi_ec_gpe_handler+0x2c/0x61
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [acpi_ev_gpe_dispatch+87/342] acpi_ev_gpe_dispatch+0x57/0x156
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [acpi_ev_gpe_detect+205/216] acpi_ev_gpe_detect+0xcd/0xd8
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [sys_select+226/432] sys_select+0xe2/0x1b0
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [copy_to_user+48/96] copy_to_user+0x30/0x60
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [sysenter_past_esp+107/169] sysenter_past_esp+0x6b/0xa9
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  =======================
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000] Code:  Bad EIP value.
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000] EIP: [<00000000>] 0x0 SS:ESP 0068:f5017b80
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000] ------------[ cut here ]------------
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000] kernel BUG at /build/buildd/linux-source-2.6.22-2.6.22/mm/prio_tree.c:125!
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000] invalid opcode: 0000 [#2]
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000] SMP 
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000] Modules linked in: af_packet rfcomm l2cap bluetooth thinkpad_acpi ppdev radeon drm ipv6 speedstep_centrino cpufreq_userspace cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table cpufreq_conservative video sbs button bay dock battery container ac nls_iso8859_1 nls_cp437 vfat fat lp snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm joydev irtty_sir sir_dev snd_seq_dummy snd_seq_oss snd_seq_midi nsc_ircc snd_rawmidi irda snd_seq_midi_event snd_seq snd_timer snd_seq_device crc_ccitt parport_pc snd psmouse pcmcia parport serio_raw soundcore aes pcspkr snd_page_alloc airo iTCO_wdt yenta_socket rsrc_nonstatic pcmcia_core iTCO_vendor_support intel_agp agpgart shpchp pci_hotplug evdev ext3 jbd mbcache sg sr_mod cdrom sd_mod floppy ata_piix e1000 ata_generic libata scsi_mod ehci_hcd uhci_hcd usbcore thermal processor fan fuse apparmor commoncap
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000] CPU:    0
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000] EIP:    0060:[vma_prio_tree_remove+190/208]    Not tainted VLI
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000] EFLAGS: 00210286   (2.6.22-14-generic #1)
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000] EIP is at vma_prio_tree_remove+0xbe/0xd0
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000] eax: f4821c60   ebx: f4821c60   ecx: f485913c   edx: f4859154
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000] esi: f4f0e420   edi: f4821c60   ebp: f4859154   esp: f5017a18
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000] ds: 007b   es: 007b   fs: 00d8  gs: 0000  ss: 0068
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000] Process artsd (pid: 5733, ti=f5016000 task=f48099f0 task.ti=f5016000)
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000] Stack: f485913c f5001480 f4821c60 b732b000 c016f290 f4821c60 f4821cb8 f625f370 
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]        c016dd12 00000000 b7000000 00000000 f5017a70 f5017a70 f625f160 f482d540 
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]        00200206 c016f025 00000000 f5017a6c 00000000 000002bb c1c0c2c0 f482d540 
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000] Call Trace:
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [unlink_file_vma+48/80] unlink_file_vma+0x30/0x50
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [free_pgtables+98/176] free_pgtables+0x62/0xb0
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [exit_mmap+149/240] exit_mmap+0x95/0xf0
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [mmput+56/160] mmput+0x38/0xa0
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [do_exit+271/2064] do_exit+0x10f/0x810
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [__wake_up+56/80] __wake_up+0x38/0x50
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [die+607/608] die+0x25f/0x260
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [do_page_fault+827/1680] do_page_fault+0x33b/0x690
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [do_page_fault+0/1680] do_page_fault+0x0/0x690
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [error_code+114/128] error_code+0x72/0x80
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [clip_ioctl+1051/1296] clip_ioctl+0x41b/0x510
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [clip_ioctl+1144/1296] clip_ioctl+0x478/0x510
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [sock_poll+12/16] sock_poll+0xc/0x10
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [do_select+606/1168] do_select+0x25e/0x490
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [__pollwait+0/240] __pollwait+0x0/0xf0
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [default_wake_function+0/16] default_wake_function+0x0/0x10
Mar 16 00:03:31 kkinder-laptop last message repeated 2 times
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [<f88db9f9>] scsi_io_completion+0xa9/0x440 [scsi_mod]
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [__activate_task+33/64] __activate_task+0x21/0x40
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [try_to_wake_up+70/1152] try_to_wake_up+0x46/0x480
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [<f8a61a0d>] airo_interrupt+0x5d/0x1160 [airo]
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [<f88fd68e>] __ata_qc_complete+0x4e/0xa0 [libata]
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [getnstimeofday+54/208] getnstimeofday+0x36/0xd0
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [__sigqueue_alloc+45/128] __sigqueue_alloc+0x2d/0x80
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [signal_wake_up+30/48] signal_wake_up+0x1e/0x30
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [__group_send_sig_info+107/144] __group_send_sig_info+0x6b/0x90
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [sys_semctl+252/2576] sys_semctl+0xfc/0xa10
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [handle_IRQ_event+48/96] handle_IRQ_event+0x30/0x60
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [__pagevec_free+31/48] __pagevec_free+0x1f/0x30
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [release_pages+325/384] release_pages+0x145/0x180
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [__activate_task+33/64] __activate_task+0x21/0x40
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [try_to_wake_up+70/1152] try_to_wake_up+0x46/0x480
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [__activate_task+33/64] __activate_task+0x21/0x40
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [try_to_wake_up+70/1152] try_to_wake_up+0x46/0x480
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [try_to_wake_up+70/1152] try_to_wake_up+0x46/0x480
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [__activate_task+33/64] __activate_task+0x21/0x40
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [core_sys_select+456/768] core_sys_select+0x1c8/0x300
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [save_i387+338/368] save_i387+0x152/0x170
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [setup_sigcontext+260/400] setup_sigcontext+0x104/0x190
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [autoremove_wake_function+27/80] autoremove_wake_function+0x1b/0x50
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [__wake_up_common+57/96] __wake_up_common+0x39/0x60
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [__wake_up+56/80] __wake_up+0x38/0x50
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [acpi_ec_gpe_handler+44/97] acpi_ec_gpe_handler+0x2c/0x61
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [acpi_ev_gpe_dispatch+87/342] acpi_ev_gpe_dispatch+0x57/0x156
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [acpi_ev_gpe_detect+205/216] acpi_ev_gpe_detect+0xcd/0xd8
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [sys_select+226/432] sys_select+0xe2/0x1b0
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [copy_to_user+48/96] copy_to_user+0x30/0x60
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  [sysenter_past_esp+107/169] sysenter_past_esp+0x6b/0xa9
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000]  =======================
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000] Code: 24 5b 5e 5f 5d c3 8b 78 24 8d 48 24 39 f9 74 bc 8b 41 04 89 fa 83 ea 24 89 47 04 89 38 89 49 04 89 4b 24 89 56 30 89 72 30 eb 92 <0f> 0b eb fe 90 90 90 90 90 90 90 90 90 90 90 90 90 90 83 ec 10 
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000] EIP: [vma_prio_tree_remove+190/208] vma_prio_tree_remove+0xbe/0xd0 SS:ESP 0068:f5017a18
Mar 16 00:03:31 kkinder-laptop kernel: [  308.712000] Fixing recursive fault but reboot is needed!
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000] BUG: unable to handle kernel NULL pointer dereference at virtual address 00000045
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000]  printing eip:
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000] c0277e09
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000] *pde = 00000000
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000] Oops: 0000 [#3]
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000] SMP 
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000] Modules linked in: af_packet rfcomm l2cap bluetooth thinkpad_acpi ppdev radeon drm ipv6 speedstep_centrino cpufreq_userspace cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table cpufreq_conservative video sbs button bay dock battery container ac nls_iso8859_1 nls_cp437 vfat fat lp snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm joydev irtty_sir sir_dev snd_seq_dummy snd_seq_oss snd_seq_midi nsc_ircc snd_rawmidi irda snd_seq_midi_event snd_seq snd_timer snd_seq_device crc_ccitt parport_pc snd psmouse pcmcia parport serio_raw soundcore aes pcspkr snd_page_alloc airo iTCO_wdt yenta_socket rsrc_nonstatic pcmcia_core iTCO_vendor_support intel_agp agpgart shpchp pci_hotplug evdev ext3 jbd mbcache sg sr_mod cdrom sd_mod floppy ata_piix e1000 ata_generic libata scsi_mod ehci_hcd uhci_hcd usbcore thermal processor fan fuse apparmor commoncap
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000] CPU:    0
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000] EIP:    0060:[sock_poll+9/16]    Not tainted VLI
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000] EFLAGS: 00010256   (2.6.22-14-generic #1)
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000] EIP is at sock_poll+0x9/0x10
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000] eax: f49aac00   ebx: 00000025   ecx: 00000000   edx: f4f13600
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000] esi: 00000010   edi: f49aac00   ebp: 00000000   esp: f4a4fb84
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000] ds: 007b   es: 007b   fs: 00d8  gs: 0033  ss: 0068
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000] Process klipper (pid: 5770, ti=f4a4e000 task=f4808f90 task.ti=f4a4e000)
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000] Stack: 00000004 c018dabe f4a4fbec 0000003b 00000020 f4a4ff9c f4a4ff54 00000000 
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000]        00000000 00000000 f4a4fe60 f4a4fe64 f4a4fe68 f4a4fe58 f4a4fe5c f4a4fe60 
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000]        00000178 00000000 00000000 00000178 00000000 00000000 00000000 00000304 
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000] Call Trace:
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000]  [do_select+606/1168] do_select+0x25e/0x490
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000]  [__pollwait+0/240] __pollwait+0x0/0xf0
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000]  [default_wake_function+0/16] default_wake_function+0x0/0x10
Mar 16 00:03:31 kkinder-laptop last message repeated 4 times
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000]  [__delay+6/16] __delay+0x6/0x10
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000]  [<f8906d53>] ata_bmdma_setup+0x53/0x70 [libata]
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000]  [<f8906c2b>] ata_bmdma_start+0xb/0x20 [libata]
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000]  [<f89023d1>] ata_qc_issue_prot+0x1d1/0x250 [libata]
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000]  [task_rq_lock+74/128] task_rq_lock+0x4a/0x80
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000]  [try_to_wake_up+70/1152] try_to_wake_up+0x46/0x480
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000]  [mempool_free+66/144] mempool_free+0x42/0x90
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000]  [task_rq_lock+74/128] task_rq_lock+0x4a/0x80
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000]  [try_to_wake_up+70/1152] try_to_wake_up+0x46/0x480
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000]  [__wake_up_common+57/96] __wake_up_common+0x39/0x60
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000]  [__wake_up+56/80] __wake_up+0x38/0x50
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000]  [add_partial+19/64] add_partial+0x13/0x40
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000]  [add_partial+19/64] add_partial+0x13/0x40
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000]  [__slab_free+273/672] __slab_free+0x111/0x2a0
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000]  [unix_write_space+24/128] unix_write_space+0x18/0x80
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000]  [sock_wfree+56/64] sock_wfree+0x38/0x40
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000]  [unix_stream_recvmsg+582/1424] unix_stream_recvmsg+0x246/0x590
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000]  [sock_alloc_send_skb+363/448] sock_alloc_send_skb+0x16b/0x1c0
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000]  [core_sys_select+456/768] core_sys_select+0x1c8/0x300
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000]  [do_sync_read+213/288] do_sync_read+0xd5/0x120
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000]  [tick_program_event+68/112] tick_program_event+0x44/0x70
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000]  [autoremove_wake_function+0/80] autoremove_wake_function+0x0/0x50
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000]  [unix_ioctl+151/208] unix_ioctl+0x97/0xd0
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000]  [sock_ioctl+191/528] sock_ioctl+0xbf/0x210
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000]  [sock_ioctl+0/528] sock_ioctl+0x0/0x210
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000]  [sys_select+226/432] sys_select+0xe2/0x1b0
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000]  [copy_to_user+48/96] copy_to_user+0x30/0x60
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000]  [sysenter_past_esp+107/169] sysenter_past_esp+0x6b/0xa9
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000]  [clip_ioctl+928/1296] clip_ioctl+0x3a0/0x510
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000]  =======================
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000] Code: 85 db 74 03 80 cc 80 8b 5e 08 89 44 24 04 8b 44 24 14 89 04 24 89 f0 ff 53 50 83 c4 08 5b 5e c3 66 90 53 89 d1 8b 50 7c 8b 5a 08 <ff> 53 20 5b c3 66 90 53 89 d1 8b 50 7c 8b 5a 08 ff 53 4c 5b c3 
Mar 16 00:03:31 kkinder-laptop kernel: [  308.736000] EIP: [sock_poll+9/16] sock_poll+0x9/0x10 SS:ESP 0068:f4a4fb84
Mar 16 00:03:31 kkinder-laptop kernel: [  309.092000] BUG: unable to handle kernel NULL pointer dereference at virtual address 00000000
Mar 16 00:03:31 kkinder-laptop kernel: [  309.092000]  printing eip:
Mar 16 00:03:31 kkinder-laptop kernel: [  309.092000] c1d9ffff
Mar 16 00:03:31 kkinder-laptop kernel: [  309.092000] *pde = 00000000
Mar 16 00:03:31 kkinder-laptop kernel: [  309.092000] Oops: 0002 [#4]
Mar 16 00:03:31 kkinder-laptop kernel: [  309.092000] SMP 
Mar 16 00:03:31 kkinder-laptop kernel: [  309.092000] Modules linked in: af_packet rfcomm l2cap bluetooth thinkpad_acpi ppdev radeon drm ipv6 speedstep_centrino cpufreq_userspace cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table cpufreq_conservative video sbs button bay dock battery container ac nls_iso8859_1 nls_cp437 vfat fat lp snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm joydev irtty_sir sir_dev snd_seq_dummy snd_seq_oss snd_seq_midi nsc_ircc snd_rawmidi irda snd_seq_midi_event snd_seq snd_timer snd_seq_device crc_ccitt parport_pc snd psmouse pcmcia parport serio_raw soundcore aes pcspkr snd_page_alloc airo iTCO_wdt yenta_socket rsrc_nonstatic pcmcia_core iTCO_vendor_support intel_agp agpgart shpchp pci_hotplug evdev ext3 jbd mbcache sg sr_mod cdrom sd_mod floppy ata_piix e1000 ata_generic libata scsi_mod ehci_hcd uhci_hcd usbcore thermal processor fan fuse apparmor commoncap
Mar 16 00:03:31 kkinder-laptop kernel: [  309.092000] CPU:    0
Mar 16 00:03:31 kkinder-laptop kernel: [  309.092000] EIP:    0060:[<c1d9ffff>]    Not tainted VLI
Mar 16 00:03:31 kkinder-laptop kernel: [  309.092000] EFLAGS: 00213246   (2.6.22-14-generic #1)
Mar 16 00:03:31 kkinder-laptop kernel: [  309.092000] EIP is at 0xc1d9ffff
Mar 16 00:03:31 kkinder-laptop kernel: [  309.092000] eax: f4886480   ebx: b7ef9000   ecx: 00000000   edx: f4f13180
Mar 16 00:03:31 kkinder-laptop kernel: [  309.092000] esi: 00100000   edi: f4886480   ebp: 00000041   esp: f628db80
Mar 16 00:03:31 kkinder-laptop kernel: [  309.092000] ds: 007b   es: 007b   fs: 00d8  gs: 0033  ss: 0068
Mar 16 00:03:31 kkinder-laptop kernel: [  309.092000] Process Xorg (pid: 4683, ti=f628c000 task=df87f4c0 task.ti=f628c000)
Mar 16 00:03:31 kkinder-laptop kernel: [  309.092000] Stack: c0277e0c 00000014 c018dabe f628dbec f628de54 00000020 f628df9c f628df54 
Mar 16 00:03:31 kkinder-laptop kernel: [  309.092000]        00000000 00000001 00000000 f628deb4 f628ded4 f628def4 f628de58 f628de78 
Mar 16 00:03:31 kkinder-laptop kernel: [  309.092000]        f628de98 fffff81a 00000000 00000000 fffff81a 00080000 00000000 00000000 
Mar 16 00:03:31 kkinder-laptop kernel: [  309.092000] Call Trace:
Mar 16 00:03:31 kkinder-laptop kernel: [  309.092000]  [sock_poll+12/16] sock_poll+0xc/0x10
Mar 16 00:03:31 kkinder-laptop kernel: [  309.092000]  [do_select+606/1168] do_select+0x25e/0x490
Mar 16 00:03:31 kkinder-laptop kernel: [  309.092000]  [__pollwait+0/240] __pollwait+0x0/0xf0
Mar 16 00:03:31 kkinder-laptop kernel: [  309.092000]  [default_wake_function+0/16] default_wake_function+0x0/0x10
Mar 16 00:03:31 kkinder-laptop last message repeated 19 times
Mar 16 00:03:31 kkinder-laptop kernel: [  309.092000]  [core_sys_select+456/768] core_sys_select+0x1c8/0x300
Mar 16 00:03:31 kkinder-laptop kernel: [  309.092000]  [__remove_hrtimer+79/128] __remove_hrtimer+0x4f/0x80
Mar 16 00:03:31 kkinder-laptop kernel: [  309.092000]  [convert_fxsr_from_user+28/240] convert_fxsr_from_user+0x1c/0xf0
Mar 16 00:03:31 kkinder-laptop kernel: [  309.092000]  [sys_select+226/432] sys_select+0xe2/0x1b0
Mar 16 00:03:31 kkinder-laptop kernel: [  309.092000]  [copy_to_user+48/96] copy_to_user+0x30/0x60
Mar 16 00:03:31 kkinder-laptop kernel: [  309.092000]  [sysenter_past_esp+107/169] sysenter_past_esp+0x6b/0xa9
Mar 16 00:03:31 kkinder-laptop kernel: [  309.092000]  =======================
Mar 16 00:03:31 kkinder-laptop kernel: [  309.092000] Code: 00 00 00 00 01 00 00 00 00 00 00 00 01 00 00 00 00 00 00 00 01 00 00 00 00 00 00 00 01 00 00 00 00 00 00 00 01 00 00 00 00 00 00 <00> 01 00 00 00 00 00 00 00 01 00 00 00 00 00 00 00 01 00 00 00 
Mar 16 00:03:31 kkinder-laptop kernel: [  309.092000] EIP: [<c1d9ffff>] 0xc1d9ffff SS:ESP 0068:f628db80
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000] BUG: unable to handle kernel NULL pointer dereference at virtual address 000000fd
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000]  printing eip:
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000] c018fd08
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000] *pde = 00000000
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000] Oops: 0000 [#5]
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000] SMP 
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000] Modules linked in: af_packet rfcomm l2cap bluetooth thinkpad_acpi ppdev radeon drm ipv6 speedstep_centrino cpufreq_userspace cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table cpufreq_conservative video sbs button bay dock battery container ac nls_iso8859_1 nls_cp437 vfat fat lp snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm joydev irtty_sir sir_dev snd_seq_dummy snd_seq_oss snd_seq_midi nsc_ircc snd_rawmidi irda snd_seq_midi_event snd_seq snd_timer snd_seq_device crc_ccitt parport_pc snd psmouse pcmcia parport serio_raw soundcore aes pcspkr snd_page_alloc airo iTCO_wdt yenta_socket rsrc_nonstatic pcmcia_core iTCO_vendor_support intel_agp agpgart shpchp pci_hotplug evdev ext3 jbd mbcache sg sr_mod cdrom sd_mod floppy ata_piix e1000 ata_generic libata scsi_mod ehci_hcd uhci_hcd usbcore thermal processor fan fuse apparmor commoncap
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000] CPU:    0
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000] EIP:    0060:[__posix_lock_file+376/1360]    Not tainted VLI
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000] EFLAGS: 00213206   (2.6.22-14-generic #1)
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000] EIP is at __posix_lock_file+0x178/0x550
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000] eax: 00000000   ebx: 000000d1   ecx: 00000000   edx: f628c000
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000] esi: f4f13244   edi: f628d9f8   ebp: f4f131a8   esp: f628d98c
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000] ds: 007b   es: 007b   fs: 00d8  gs: 0000  ss: 0068
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000] Process Xorg (pid: 4683, ti=f628c000 task=df87f4c0 task.ti=f628c000)
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000] Stack: c0115c00 00000000 00000000 d0000000 c017b173 f6022000 00000000 00000000 
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000]        00000001 f62a6160 f6669ea0 f8d80000 c0115aeb c16c5e00 00203287 c03d9e90 
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000]        f672e400 00203287 00000001 00000001 f672e528 f4886480 f628d9f8 00000000 
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000] Call Trace:
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000]  [do_flush_tlb_all+0/80] do_flush_tlb_all+0x0/0x50
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000]  [add_partial+19/64] add_partial+0x13/0x40
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000]  [flush_tlb_all+27/32] flush_tlb_all+0x1b/0x20
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000]  [locks_remove_posix+130/160] locks_remove_posix+0x82/0xa0
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000]  [fasync_helper+161/224] fasync_helper+0xa1/0xe0
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000]  [mutex_lock+8/32] mutex_lock+0x8/0x20
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000]  [input_close_device+37/96] input_close_device+0x25/0x60
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000]  [__fput+299/416] __fput+0x12b/0x1a0
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000]  [filp_close+64/128] filp_close+0x40/0x80
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000]  [put_files_struct+143/176] put_files_struct+0x8f/0xb0
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000]  [do_exit+337/2064] do_exit+0x151/0x810
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000]  [__wake_up+56/80] __wake_up+0x38/0x50
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000]  [die+607/608] die+0x25f/0x260
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000]  [do_page_fault+827/1680] do_page_fault+0x33b/0x690
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000]  [do_page_fault+0/1680] do_page_fault+0x0/0x690
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000]  [error_code+114/128] error_code+0x72/0x80
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000]  [sock_poll+12/16] sock_poll+0xc/0x10
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000]  [do_select+606/1168] do_select+0x25e/0x490
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000]  [__pollwait+0/240] __pollwait+0x0/0xf0
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000]  [default_wake_function+0/16] default_wake_function+0x0/0x10
Mar 16 00:03:31 kkinder-laptop last message repeated 19 times
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000]  [core_sys_select+456/768] core_sys_select+0x1c8/0x300
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000]  [__remove_hrtimer+79/128] __remove_hrtimer+0x4f/0x80
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000]  [convert_fxsr_from_user+28/240] convert_fxsr_from_user+0x1c/0xf0
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000]  [sys_select+226/432] sys_select+0xe2/0x1b0
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000]  [copy_to_user+48/96] copy_to_user+0x30/0x60
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000]  [sysenter_past_esp+107/169] sysenter_past_esp+0x6b/0xa9
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000]  =======================
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000] Code: ff 85 c0 74 de 8b 73 fc eb ae 8b 9d 9c 00 00 00 8d b5 9c 00 00 00 85 db 75 11 eb 22 8d b4 26 00 00 00 00 89 de 8b 1b 85 db 74 13 <f6> 43 2c 01 74 f2 89 da 89 f8 e8 19 f2 ff ff 85 c0 74 e5 c7 44 
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000] EIP: [__posix_lock_file+376/1360] __posix_lock_file+0x178/0x550 SS:ESP 0068:f628d98c
Mar 16 00:03:31 kkinder-laptop kernel: [  309.096000] Fixing recursive fault but reboot is needed!
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000] BUG: unable to handle kernel paging request at virtual address 01c783da
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  printing eip:
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000] 01c783da
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000] *pde = 00000000
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000] Oops: 0000 [#6]
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000] SMP 
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000] Modules linked in: af_packet rfcomm l2cap bluetooth thinkpad_acpi ppdev radeon drm ipv6 speedstep_centrino cpufreq_userspace cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table cpufreq_conservative video sbs button bay dock battery container ac nls_iso8859_1 nls_cp437 vfat fat lp snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm joydev irtty_sir sir_dev snd_seq_dummy snd_seq_oss snd_seq_midi nsc_ircc snd_rawmidi irda snd_seq_midi_event snd_seq snd_timer snd_seq_device crc_ccitt parport_pc snd psmouse pcmcia parport serio_raw soundcore aes pcspkr snd_page_alloc airo iTCO_wdt yenta_socket rsrc_nonstatic pcmcia_core iTCO_vendor_support intel_agp agpgart shpchp pci_hotplug evdev ext3 jbd mbcache sg sr_mod cdrom sd_mod floppy ata_piix e1000 ata_generic libata scsi_mod ehci_hcd uhci_hcd usbcore thermal processor fan fuse apparmor commoncap
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000] CPU:    0
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000] EIP:    0060:[phys_startup_32+28804058/-1073741824]    Not tainted VLI
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000] EFLAGS: 00210256   (2.6.22-14-generic #1)
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000] EIP is at 0x1c783da
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000] eax: f4827480   ebx: c01f5980   ecx: 00000000   edx: f4f13900
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000] esi: 00000008   edi: f4827480   ebp: 7b000178   esp: f4939b80
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000] ds: 007b   es: 007b   fs: 00d8  gs: 0033  ss: 0068
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000] Process akregator (pid: 5751, ti=f4938000 task=f54a4000 task.ti=f4938000)
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000] Stack: c0277e0c 00000003 c018dabe f4939bec 0000003b 00000020 f4939f9c f4939f54 
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]        00000000 00000000 00000000 f4939e60 f4939e64 f4939e68 f4939e58 f4939e5c 
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]        f4939e60 7b000178 00000000 00000000 7b000178 00000000 00000000 00000000 
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000] Call Trace:
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [sock_poll+12/16] sock_poll+0xc/0x10
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [do_select+606/1168] do_select+0x25e/0x490
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [__pollwait+0/240] __pollwait+0x0/0xf0
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [default_wake_function+0/16] default_wake_function+0x0/0x10
Mar 16 00:03:31 kkinder-laptop last message repeated 11 times
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [__wake_up_common+57/96] __wake_up_common+0x39/0x60
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [__wake_up+56/80] __wake_up+0x38/0x50
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [add_partial+19/64] add_partial+0x13/0x40
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [__slab_free+273/672] __slab_free+0x111/0x2a0
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [unix_write_space+24/128] unix_write_space+0x18/0x80
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [sock_wfree+56/64] sock_wfree+0x38/0x40
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [unix_stream_recvmsg+582/1424] unix_stream_recvmsg+0x246/0x590
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [core_sys_select+456/768] core_sys_select+0x1c8/0x300
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [do_sync_read+213/288] do_sync_read+0xd5/0x120
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [unmap_vmas+954/1488] unmap_vmas+0x3ba/0x5d0
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [autoremove_wake_function+0/80] autoremove_wake_function+0x0/0x50
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [unix_ioctl+151/208] unix_ioctl+0x97/0xd0
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [sock_ioctl+191/528] sock_ioctl+0xbf/0x210
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [unmap_region+207/288] unmap_region+0xcf/0x120
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [sock_ioctl+0/528] sock_ioctl+0x0/0x210
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [sys_select+226/432] sys_select+0xe2/0x1b0
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [copy_to_user+48/96] copy_to_user+0x30/0x60
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [sysenter_past_esp+107/169] sysenter_past_esp+0x6b/0xa9
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  =======================
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000] Code:  Bad EIP value.
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000] EIP: [phys_startup_32+28804058/-1073741824] 0x1c783da SS:ESP 0068:f4939b80
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000] BUG: unable to handle kernel paging request at virtual address b7f0402c
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  printing eip:
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000] c018fd08
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000] *pde = 00000000
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000] Oops: 0000 [#7]
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000] SMP 
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000] Modules linked in: af_packet rfcomm l2cap bluetooth thinkpad_acpi ppdev radeon drm ipv6 speedstep_centrino cpufreq_userspace cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table cpufreq_conservative video sbs button bay dock battery container ac nls_iso8859_1 nls_cp437 vfat fat lp snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm joydev irtty_sir sir_dev snd_seq_dummy snd_seq_oss snd_seq_midi nsc_ircc snd_rawmidi irda snd_seq_midi_event snd_seq snd_timer snd_seq_device crc_ccitt parport_pc snd psmouse pcmcia parport serio_raw soundcore aes pcspkr snd_page_alloc airo iTCO_wdt yenta_socket rsrc_nonstatic pcmcia_core iTCO_vendor_support intel_agp agpgart shpchp pci_hotplug evdev ext3 jbd mbcache sg sr_mod cdrom sd_mod floppy ata_piix e1000 ata_generic libata scsi_mod ehci_hcd uhci_hcd usbcore thermal processor fan fuse apparmor commoncap
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000] CPU:    0
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000] EIP:    0060:[__posix_lock_file+376/1360]    Not tainted VLI
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000] EFLAGS: 00210286   (2.6.22-14-generic #1)
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000] EIP is at __posix_lock_file+0x178/0x550
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000] eax: 00000000   ebx: b7f04000   ecx: 00000000   edx: f4938000
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000] esi: f4f139c4   edi: f49399f8   ebp: f4f13928   esp: f493998c
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000] ds: 007b   es: 007b   fs: 00d8  gs: 0000  ss: 0068
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000] Process akregator (pid: 5751, ti=f4938000 task=f54a4000 task.ti=f4938000)
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000] Stack: 00000006 c1000000 00000000 c03b5d0c c0162a70 000000e4 00000000 00000000 
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]        c03b5c80 c1a21cc0 00000001 0000001f 00000002 c1a1c7a0 c03b5d00 c1a53b00 
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]        c03b5c80 00200246 c011fc6e c011fc7a c1a53b00 f4827480 f49399f8 00000000 
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000] Call Trace:
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [free_pages_bulk+160/608] free_pages_bulk+0xa0/0x260
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [kunmap_atomic+94/160] kunmap_atomic+0x5e/0xa0
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [kunmap_atomic+106/160] kunmap_atomic+0x6a/0xa0
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [locks_remove_posix+130/160] locks_remove_posix+0x82/0xa0
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [filp_close+64/128] filp_close+0x40/0x80
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [put_files_struct+143/176] put_files_struct+0x8f/0xb0
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [do_exit+337/2064] do_exit+0x151/0x810
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [die+607/608] die+0x25f/0x260
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [do_page_fault+827/1680] do_page_fault+0x33b/0x690
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [cfq_free_io_context+0/160] cfq_free_io_context+0x0/0xa0
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [do_page_fault+0/1680] do_page_fault+0x0/0x690
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [error_code+114/128] error_code+0x72/0x80
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [cfq_free_io_context+0/160] cfq_free_io_context+0x0/0xa0
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [clip_ioctl+1051/1296] clip_ioctl+0x41b/0x510
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [clip_ioctl+1144/1296] clip_ioctl+0x478/0x510
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [sock_poll+12/16] sock_poll+0xc/0x10
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [do_select+606/1168] do_select+0x25e/0x490
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [__pollwait+0/240] __pollwait+0x0/0xf0
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [default_wake_function+0/16] default_wake_function+0x0/0x10
Mar 16 00:03:31 kkinder-laptop last message repeated 11 times
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [__wake_up_common+57/96] __wake_up_common+0x39/0x60
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [__wake_up+56/80] __wake_up+0x38/0x50
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [add_partial+19/64] add_partial+0x13/0x40
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [__slab_free+273/672] __slab_free+0x111/0x2a0
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [unix_write_space+24/128] unix_write_space+0x18/0x80
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [sock_wfree+56/64] sock_wfree+0x38/0x40
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [unix_stream_recvmsg+582/1424] unix_stream_recvmsg+0x246/0x590
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [core_sys_select+456/768] core_sys_select+0x1c8/0x300
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [do_sync_read+213/288] do_sync_read+0xd5/0x120
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [unmap_vmas+954/1488] unmap_vmas+0x3ba/0x5d0
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [autoremove_wake_function+0/80] autoremove_wake_function+0x0/0x50
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [unix_ioctl+151/208] unix_ioctl+0x97/0xd0
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [sock_ioctl+191/528] sock_ioctl+0xbf/0x210
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [unmap_region+207/288] unmap_region+0xcf/0x120
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [sock_ioctl+0/528] sock_ioctl+0x0/0x210
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [sys_select+226/432] sys_select+0xe2/0x1b0
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [copy_to_user+48/96] copy_to_user+0x30/0x60
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  [sysenter_past_esp+107/169] sysenter_past_esp+0x6b/0xa9
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000]  =======================
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000] Code: ff 85 c0 74 de 8b 73 fc eb ae 8b 9d 9c 00 00 00 8d b5 9c 00 00 00 85 db 75 11 eb 22 8d b4 26 00 00 00 00 89 de 8b 1b 85 db 74 13 <f6> 43 2c 01 74 f2 89 da 89 f8 e8 19 f2 ff ff 85 c0 74 e5 c7 44 
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000] EIP: [__posix_lock_file+376/1360] __posix_lock_file+0x178/0x550 SS:ESP 0068:f493998c
Mar 16 00:03:31 kkinder-laptop kernel: [  309.108000] Fixing recursive fault but reboot is needed!
Mar 16 00:03:32 kkinder-laptop kernel: [  309.960000] airo(eth1): Max tries exceeded when issueing command
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000] airo(eth1): Max tries exceeded when issueing command
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000] BUG: unable to handle kernel NULL pointer dereference at virtual address 00000020
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  printing eip:
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000] c0277e09
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000] *pde = 00000000
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000] Oops: 0000 [#8]
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000] SMP 
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000] Modules linked in: af_packet rfcomm l2cap bluetooth thinkpad_acpi ppdev radeon drm ipv6 speedstep_centrino cpufreq_userspace cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table cpufreq_conservative video sbs button bay dock battery container ac nls_iso8859_1 nls_cp437 vfat fat lp snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm joydev irtty_sir sir_dev snd_seq_dummy snd_seq_oss snd_seq_midi nsc_ircc snd_rawmidi irda snd_seq_midi_event snd_seq snd_timer snd_seq_device crc_ccitt parport_pc snd psmouse pcmcia parport serio_raw soundcore aes pcspkr snd_page_alloc airo iTCO_wdt yenta_socket rsrc_nonstatic pcmcia_core iTCO_vendor_support intel_agp agpgart shpchp pci_hotplug evdev ext3 jbd mbcache sg sr_mod cdrom sd_mod floppy ata_piix e1000 ata_generic libata scsi_mod ehci_hcd uhci_hcd usbcore thermal processor fan fuse apparmor commoncap
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000] CPU:    0
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000] EIP:    0060:[sock_poll+9/16]    Not tainted VLI
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000] EFLAGS: 00010256   (2.6.22-14-generic #1)
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000] EIP is at sock_poll+0x9/0x10
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000] eax: f48279c0   ebx: 00000000   ecx: 00000000   edx: f4f13780
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000] esi: 00100000   edi: f48279c0   ebp: 00000000   esp: f5025b84
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000] ds: 007b   es: 007b   fs: 00d8  gs: 0033  ss: 0068
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000] Process dcopserver (pid: 5680, ti=f5024000 task=f543c000 task.ti=f5024000)
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000] Stack: 00000014 c018dabe f5025bec f5025e54 00000020 f5025f9c f5025f54 00000000 
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]        00000000 00000000 f5025e6c f5025e74 f5025e7c f5025e58 f5025e60 f5025e68 
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]        fffbfed8 00000000 00000000 fffbfed8 00000000 00000000 00000000 00000304 
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000] Call Trace:
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  [do_select+606/1168] do_select+0x25e/0x490
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  [__pollwait+0/240] __pollwait+0x0/0xf0
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  [default_wake_function+0/16] default_wake_function+0x0/0x10
Mar 16 00:03:33 kkinder-laptop last message repeated 19 times
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  [core_sys_select+456/768] core_sys_select+0x1c8/0x300
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  [sys_sendto+301/400] sys_sendto+0x12d/0x190
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  [do_sync_read+213/288] do_sync_read+0xd5/0x120
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  [invalidate_inode_buffers+14/192] invalidate_inode_buffers+0xe/0xc0
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  [autoremove_wake_function+0/80] autoremove_wake_function+0x0/0x50
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  [sys_select+75/432] sys_select+0x4b/0x1b0
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  [do_fcntl+639/752] do_fcntl+0x27f/0x2f0
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  [sysenter_past_esp+107/169] sysenter_past_esp+0x6b/0xa9
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  =======================
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000] Code: 85 db 74 03 80 cc 80 8b 5e 08 89 44 24 04 8b 44 24 14 89 04 24 89 f0 ff 53 50 83 c4 08 5b 5e c3 66 90 53 89 d1 8b 50 7c 8b 5a 08 <ff> 53 20 5b c3 66 90 53 89 d1 8b 50 7c 8b 5a 08 ff 53 4c 5b c3 
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000] EIP: [sock_poll+9/16] sock_poll+0x9/0x10 SS:ESP 0068:f5025b84
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000] BUG: unable to handle kernel NULL pointer dereference at virtual address 0000002d
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  printing eip:
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000] c018fd08
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000] *pde = 00000000
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000] Oops: 0000 [#9]
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000] SMP 
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000] Modules linked in: af_packet rfcomm l2cap bluetooth thinkpad_acpi ppdev radeon drm ipv6 speedstep_centrino cpufreq_userspace cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table cpufreq_conservative video sbs button bay dock battery container ac nls_iso8859_1 nls_cp437 vfat fat lp snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm joydev irtty_sir sir_dev snd_seq_dummy snd_seq_oss snd_seq_midi nsc_ircc snd_rawmidi irda snd_seq_midi_event snd_seq snd_timer snd_seq_device crc_ccitt parport_pc snd psmouse pcmcia parport serio_raw soundcore aes pcspkr snd_page_alloc airo iTCO_wdt yenta_socket rsrc_nonstatic pcmcia_core iTCO_vendor_support intel_agp agpgart shpchp pci_hotplug evdev ext3 jbd mbcache sg sr_mod cdrom sd_mod floppy ata_piix e1000 ata_generic libata scsi_mod ehci_hcd uhci_hcd usbcore thermal processor fan fuse apparmor commoncap
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000] CPU:    0
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000] EIP:    0060:[__posix_lock_file+376/1360]    Not tainted VLI
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000] EFLAGS: 00010202   (2.6.22-14-generic #1)
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000] EIP is at __posix_lock_file+0x178/0x550
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000] eax: 00000000   ebx: 00000001   ecx: 00000000   edx: f5024000
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000] esi: f55c8ba0   edi: f50259fc   ebp: f4f137a8   esp: f5025990
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000] ds: 007b   es: 007b   fs: 00d8  gs: 0000  ss: 0068
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000] Process dcopserver (pid: 5680, ti=f5024000 task=f543c000 task.ti=f5024000)
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000] Stack: 00000006 c1000000 00000000 c03b5d0c c0162a70 00000170 00000000 00000000 
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]        c03b5c80 c1a22e40 00000001 0000001f 00000002 00000086 f5025c54 f54f0e04 
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]        00000000 f50259f8 c011fff9 00000000 00000001 f48279c0 f50259fc 00000000 
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000] Call Trace:
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  [free_pages_bulk+160/608] free_pages_bulk+0xa0/0x260
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  [__wake_up_common+57/96] __wake_up_common+0x39/0x60
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  [locks_remove_posix+130/160] locks_remove_posix+0x82/0xa0
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  [__wake_up+56/80] __wake_up+0x38/0x50
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  [pipe_release+134/176] pipe_release+0x86/0xb0
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  [__fput+299/416] __fput+0x12b/0x1a0
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  [filp_close+64/128] filp_close+0x40/0x80
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  [put_files_struct+143/176] put_files_struct+0x8f/0xb0
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  [do_exit+337/2064] do_exit+0x151/0x810
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  [__wake_up+56/80] __wake_up+0x38/0x50
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  [die+607/608] die+0x25f/0x260
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  [do_page_fault+827/1680] do_page_fault+0x33b/0x690
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  [do_page_fault+0/1680] do_page_fault+0x0/0x690
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  [error_code+114/128] error_code+0x72/0x80
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  [sock_poll+9/16] sock_poll+0x9/0x10
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  [do_select+606/1168] do_select+0x25e/0x490
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  [__pollwait+0/240] __pollwait+0x0/0xf0
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  [default_wake_function+0/16] default_wake_function+0x0/0x10
Mar 16 00:03:33 kkinder-laptop last message repeated 19 times
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  [core_sys_select+456/768] core_sys_select+0x1c8/0x300
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  [sys_sendto+301/400] sys_sendto+0x12d/0x190
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  [do_sync_read+213/288] do_sync_read+0xd5/0x120
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  [invalidate_inode_buffers+14/192] invalidate_inode_buffers+0xe/0xc0
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  [autoremove_wake_function+0/80] autoremove_wake_function+0x0/0x50
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  [sys_select+75/432] sys_select+0x4b/0x1b0
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  [do_fcntl+639/752] do_fcntl+0x27f/0x2f0
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  [sysenter_past_esp+107/169] sysenter_past_esp+0x6b/0xa9
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000]  =======================
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000] Code: ff 85 c0 74 de 8b 73 fc eb ae 8b 9d 9c 00 00 00 8d b5 9c 00 00 00 85 db 75 11 eb 22 8d b4 26 00 00 00 00 89 de 8b 1b 85 db 74 13 <f6> 43 2c 01 74 f2 89 da 89 f8 e8 19 f2 ff ff 85 c0 74 e5 c7 44 
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000] EIP: [__posix_lock_file+376/1360] __posix_lock_file+0x178/0x550 SS:ESP 0068:f5025990
Mar 16 00:03:33 kkinder-laptop kernel: [  310.948000] Fixing recursive fault but reboot is needed!
Mar 16 00:03:34 kkinder-laptop kernel: [  312.004000] airo(eth1): Max tries exceeded when issueing command
Mar 16 00:03:35 kkinder-laptop kernel: [  312.992000] airo(eth1): Max tries exceeded when issueing command
Mar 16 00:03:36 kkinder-laptop kernel: [  313.980000] airo(eth1): Max tries exceeded when issueing command
Mar 16 00:03:37 kkinder-laptop kernel: [  314.968000] airo(eth1): Max tries exceeded when issueing command
Mar 16 00:03:38 kkinder-laptop kernel: [  315.964000] airo(eth1): Max tries exceeded when issueing command
Mar 16 00:03:39 kkinder-laptop kernel: [  316.952000] airo(eth1): Max tries exceeded when issueing command
Mar 16 00:04:38 kkinder-laptop syslogd 1.4.1#21ubuntu3: restart.

```

Sorry for the long paste. Although it says "reboot needed", I had to actually just force a powerdown.

Where should I take this issue?

---

### Post by kkinder on 2008-03-16
I submitted a bug here:

[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/202984](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/202984)

---

