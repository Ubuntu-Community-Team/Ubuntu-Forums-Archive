---
title: "Unable to handle kernel paging request??"
date: 2007-02-20
forum: General Help
---

### Post by dannyboy79 on 2007-02-20
Hello,
I am curious as to why this message has appeared in my log files? I use logcheck daily, and it emails results of parsing my log files for any security or system relevance. On the 17th as well as a couple days later, I had this appear.
System Events
=-=-=-=-=-=-=
Feb 17 23:16:11 ubuntu kernel: [17194647.244000] Unable to handle kernel paging request at virtual address bbb20f77
Feb 17 23:16:11 ubuntu kernel: [17194647.244000]  printing eip:
Feb 17 23:16:11 ubuntu kernel: [17194647.244000] c0155508
Feb 17 23:16:11 ubuntu kernel: [17194647.244000] *pde = 00000000
Feb 17 23:16:11 ubuntu kernel: [17194647.244000] Oops: 0000 [#1]
Feb 17 23:16:11 ubuntu kernel: [17194647.244000] PREEMPT SMP
Feb 17 23:16:11 ubuntu kernel: [17194647.244000] Modules linked in: binfmt_misc rfcomm l2cap bluetooth ppdev speedstep_lib cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sony_acpi pcc_acpi hotkey dev_acpi container button acpi_sbs battery ac i2c_acpi_ec iptable_mangle ipt_state ipt_multiport iptable_filter iptable_nat ip_nat ip_conntrack nfnetlink ip_tables nls_cp437 vfat fat nls_utf8 ntfs dm_mod md_mod tsdev sr_mod sbp2 lp parport_pc parport floppy psmouse serio_raw pcspkr tda9887 msp3400 saa7127 saa7115 tuner tveeprom nvidia ivtv i2c_algo_bit sis900 i2c_core snd_intel8x0 snd_ac97_codec snd_ac97_bus mii snd_pcm_oss snd_mixer_oss videodev snd_pcm snd_timer snd soundcore snd_page_alloc shpchp pci_hotplug sis_agp agpgart sg evdev ipv6 ext3 jbd ide_generic ehci_hcd ohci_hcd ohci1394 ieee1394 usbcore sd_mod sata_sis libata scsi_mod ide_disk ide_cd cdrom sis5513 generic thermal processor fan fbcon tileblit font !
 bitblit softcursor capability commonc
Feb 17 23:16:11 ubuntu kernel: p
Feb 17 23:16:11 ubuntu kernel: [17194647.244000] CPU:    0
Feb 17 23:16:11 ubuntu kernel: [17194647.244000] EIP:    0060:[prep_new_page+8/128]    Tainted: P      VLI
Feb 17 23:16:11 ubuntu kernel: [17194647.244000] EFLAGS: 00010286   (2.6.15-27-686)
Feb 17 23:16:11 ubuntu kernel: [17194647.244000] EIP is at prep_new_page+0x8/0x80
Feb 17 23:16:11 ubuntu kernel: [17194647.244000] eax: 00000000   ebx: bbb20f6f   ecx: 0000002c   edx: c14b552c
Feb 17 23:16:11 ubuntu kernel: [17194647.244000] esi: 00000010   edi: c035a500   ebp: edd1e000   esp: edd1fe44
Feb 17 23:16:11 ubuntu kernel: [17194647.244000] ds: 007b   es: 007b   ss: 0068
Feb 17 23:16:11 ubuntu kernel: [17194647.244000] Process nautilus (pid: 26617, threadinfo=edd1e000 task=ee307560)
Feb 17 23:16:11 ubuntu kernel: [17194647.244000] Stack: c14b552c 00000246 c035a520 c0155be6 c14b552c 00000000 edd1fe94 c011fc1c
Feb 17 23:16:11 ubuntu kernel: [17194647.244000]        00000001 00000000 c14b552c 00000002 00000246 c035ad04 00000001 00000002
Feb 17 23:16:11 ubuntu kernel: [17194647.244000]        00000044 c0155ea5 c035a500 00000000 000200d0 00000002 00000044 00000000
Feb 17 23:16:11 ubuntu kernel: [17194647.244000] Call Trace:
Feb 17 23:16:11 ubuntu kernel: [17194647.244000]  [buffered_rmqueue+278/608] buffered_rmqueue+0x116/0x260
Feb 17 23:16:11 ubuntu kernel: [17194647.244000]  [load_balance_newidle+76/304] load_balance_newidle+0x4c/0x130
Feb 17 23:16:11 ubuntu kernel: [17194647.244000]  [get_page_from_freelist+133/240] get_page_from_freelist+0x85/0xf0
Feb 17 23:16:11 ubuntu kernel: [17194647.244000]  [__alloc_pages+94/800] __alloc_pages+0x5e/0x320
Feb 17 23:16:11 ubuntu kernel: [17194647.244000]  [__get_free_pages+33/80] __get_free_pages+0x21/0x50
Feb 17 23:16:11 ubuntu kernel: [17194647.244000]  [try_to_del_timer_sync+82/96] try_to_del_timer_sync+0x52/0x60
Feb 17 23:16:11 ubuntu kernel: [17194647.244000]  [__pollwait+140/208] __pollwait+0x8c/0xd0
Feb 17 23:16:11 ubuntu kernel: [17194647.244000]  [pipe_poll+60/208] pipe_poll+0x3c/0xd0
Feb 17 23:16:11 ubuntu kernel: [17194647.244000]  [do_pollfd+81/192] do_pollfd+0x51/0xc0
Feb 17 23:16:11 ubuntu kernel: [17194647.244000]  [do_poll+106/208] do_poll+0x6a/0xd0
Feb 17 23:16:11 ubuntu kernel: [17194647.244000]  [sys_poll+314/672] sys_poll+0x13a/0x2a0
Feb 17 23:16:11 ubuntu kernel: [17194647.244000]  [__pollwait+0/208] __pollwait+0x0/0xd0
Feb 17 23:16:11 ubuntu kernel: [17194647.244000]  [sysenter_past_esp+84/117] sysenter_past_esp+0x54/0x75
Feb 17 23:16:11 ubuntu kernel: [17194647.244000] Code: ff ff f7 03 e1 9c 02 00 0f 84 46 ff ff ff e9 31 ff ff ff 8b 44 24 04 c7 40 04 00 00 00 00 c3 8d 74 26 00 53 83 ec 08 8b 5c 2c 10 <8b> 43 08 40 74 42 26 5c 24 04 c7 04 24 2e 8b 31 c0 e8 82 fa ff

 Does this mean anything to anyone? I believe this is with kernel 2.6.15-26-686 (i am on Dapper). Just lat night I finally let my machine restart and it upgraded to -28 and it basically ruined everything. My nvidia driver failed as well as grub. FOr some reason when grub trys to be automatically updated it changed my root line within my menu.lst to (hd2,1) which is where grub is installed (drive hdc, partition 1 within ubuntu) but grub's device map file lists hdc as hd0, so obviously grub failed with error 17 I believe it was. Anyway, luckily I am smart enough to know what my menu.lst file should look like as I have dealt with the #groot line being changed as well in the past. So, I am wondering what I can do to have grub update work correctly in the future when I updrade my kernel. I am on my way to fixing my nvidia driver because at 1 point the guy who wrote envy didn't have the latest and greatest driver within his repo, so I downloaded the installer straight from Nvidia, needless to say, before I can do the update using his repo this time (since now he does have the latest in his repo) I have to use the installer and do an uninstall or else I get an error about the kernel module not matching the nvidia module or something like that. Anyway, any thoughts on the kernel error as well as somehow making grub update work correctly would be appreciated.

---

