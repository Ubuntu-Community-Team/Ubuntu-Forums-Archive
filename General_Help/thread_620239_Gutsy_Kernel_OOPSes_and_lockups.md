---
title: "Gutsy Kernel OOPSes and lockups"
date: 2007-11-22
forum: General Help
---

### Post by Hagbard on 2007-11-22
Yesterday I experienced two absolutely hard lockups, one during firefox browsing and one at the moment I clicked "shut down" from the gnome 'quit' menu. When I say 'hard', I mean hard -- not only was I unable to switch to a text terminal, but even the Magic SysRq key combinations had no effect. The second lockup actually caused the caps lock/scroll lock LEDs on the keyboard to start blinking rhythmically, so I wasn't too surprised. Digging around in my logs, I found several kernel OOPS. So far as I can tell, it is not a hardware problem, because I ran memtest for several passes to check my RAM, and the machine is still stable when running Feisty from another partition. Here is the log from one of the OOPSes:

Nov 21 23:53:54 gutsy kernel: [24841.348000] BUG: unable to handle kernel paging request at virtual address 0a5b31ac
Nov 21 23:53:54 gutsy kernel: [24841.348000]  printing eip:
Nov 21 23:53:54 gutsy kernel: [24841.348000] c016eb23
Nov 21 23:53:54 gutsy kernel: [24841.348000] *pde = 00000000
Nov 21 23:53:54 gutsy kernel: [24841.348000] Oops: 0000 [#4]
Nov 21 23:53:54 gutsy kernel: [24841.348000] SMP 
Nov 21 23:53:54 gutsy kernel: [24841.348000] Modules linked in: ipv6 af_packet powernow_k8 cpufreq_conservative cpufreq_userspace cpufreq_powersave cpufreq_ondemand cpufreq_stats freq_table ac video button container sbs dock battery sbp2 parport_pc lp parport loop snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi ide_cd cdrom snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore snd_page_alloc pcspkr k8temp i2c_nforce2 nvidia(P) agpgart shpchp i2c_core pci_hotplug evdev ext3 jbd mbcache sg sd_mod ata_generic usbhid hid floppy amd74xx ide_core ohci1394 ieee1394 forcedeth ehci_hcd sata_nv libata scsi_mod ohci_hcd usbcore thermal processor fan fuse apparmor commoncap
Nov 21 23:53:54 gutsy kernel: [24841.348000] CPU:    0
Nov 21 23:53:54 gutsy kernel: [24841.348000] EIP:    0060:[find_vma+51/112]    Tainted: P       VLI
Nov 21 23:53:54 gutsy kernel: [24841.348000] EFLAGS: 00010202   (2.6.22-14-generic #1)
Nov 21 23:53:54 gutsy kernel: [24841.348000] EIP is at find_vma+0x33/0x70
Nov 21 23:53:54 gutsy kernel: [24841.348000] eax: 0a5b31bc   ebx: 00000000   ecx: 0a5b31a4   edx: bfff3000
Nov 21 23:53:54 gutsy kernel: [24841.348000] esi: c94c3380   edi: 00000000   ebp: bfff3c64   esp: d031fea0
Nov 21 23:53:54 gutsy kernel: [24841.348000] ds: 007b   es: 007b   fs: 00d8  gs: 0033  ss: 0068
Nov 21 23:53:54 gutsy kernel: [24841.348000] Process ps (pid: 8339, ti=d031e000 task=c0c88f90 task.ti=d031e000)
Nov 21 23:53:54 gutsy kernel: [24841.348000] Stack: 00000000 bfff3000 c016f19d 00000000 00000025 00000000 c016d6d0 c03b5600 
Nov 21 23:53:54 gutsy kernel: [24841.348000]        c94c3380 cb134f90 00000030 00000011 00000001 00000001 00000000 00000000 
Nov 21 23:53:54 gutsy kernel: [24841.348000]        00000025 c5860000 c5860000 c016da32 00000001 00000000 00000001 d031ff1c 
Nov 21 23:53:54 gutsy kernel: [24841.348000] Call Trace:
Nov 21 23:53:54 gutsy kernel: [24841.348000]  [find_extend_vma+29/112] find_extend_vma+0x1d/0x70
Nov 21 23:53:54 gutsy kernel: [24841.348000]  [get_user_pages+64/736] get_user_pages+0x40/0x2e0
Nov 21 23:53:54 gutsy kernel: [24841.348000]  [access_process_vm+194/336] access_process_vm+0xc2/0x150
Nov 21 23:53:54 gutsy kernel: [24841.348000]  [proc_pid_cmdline+120/272] proc_pid_cmdline+0x78/0x110
Nov 21 23:53:54 gutsy kernel: [24841.348000]  [proc_info_read+135/192] proc_info_read+0x87/0xc0
Nov 21 23:53:54 gutsy kernel: [24841.348000]  [vfs_read+188/352] vfs_read+0xbc/0x160
Nov 21 23:53:54 gutsy kernel: [24841.348000]  [proc_info_read+0/192] proc_info_read+0x0/0xc0
Nov 21 23:53:54 gutsy kernel: [24841.348000]  [sys_read+65/112] sys_read+0x41/0x70
Nov 21 23:53:54 gutsy kernel: [24841.348000]  [sysenter_past_esp+107/169] sysenter_past_esp+0x6b/0xa9
Nov 21 23:53:54 gutsy kernel: [24841.348000]  =======================
Nov 21 23:53:54 gutsy kernel: [24841.348000] Code: 8b 40 08 85 c0 74 05 3b 50 08 72 39 8b 46 04 85 c0 74 3e 31 db 8d 76 00 eb 0e 3b 51 04 73 2e 8b 40 08 89 cb 85 c0 74 0f 8d 48 e8 <39> 51 08 77 ea 8b 40 04 85 c0 75 f1 85 db 89 d8 74 05 89 5e 08 
Nov 21 23:53:54 gutsy kernel: [24841.348000] EIP: [find_vma+51/112] find_vma+0x33/0x70 SS:ESP 0068:d031fea0

---

