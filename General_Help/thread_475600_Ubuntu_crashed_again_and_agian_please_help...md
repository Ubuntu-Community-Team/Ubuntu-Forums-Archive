---
title: "Ubuntu crashed again and agian please help.."
date: 2007-06-16
forum: General Help
---

### Post by sunshine12 on 2007-06-16
I have installed Ubuntu 7.04. But it is giving me a hard time since then. It crashed 3 times in last 10 days and I have formatted and installed Ubuntu, today is the 4th one.

The actual problem is :  After sudden powercut when I restarted system it is giving me error...... " There is error in root file system, forced fsck performed.... then automatic fsck failed and you have to run fsck manually..... then I ran fsck and given "yes" answer to all questions, and it seems that everything would be fine, but when pc restarted the same error repeats again and again. and I have to format the harddisk with fresh Ubuntu.
The error is something like.... "ta 126976 in ,  there is error in block 358 to block 367" and after correcting, it repeats again...

every 3rd or 4th day I have to reinstall Ubuntu afresh...!!!! This is really painful. Please someone here can help me out. Please anybody sugget what would be the problem?

compare it to Windows XP whenever this kind of unusual shutdown occur, the system automatically check and correct errors, what is the solution in Ubuntu.

If this repeats again then I have to switch back to windows XP or Vista, cause installing OS and other softwares every 4th day is practically impossible for me.:(

Detail of my system is : Intel Pentium III  933 MHz, 256 MB RAM, 20GB HDD, only one OS right now Ubuntu 7.04.... I will provide any other details if you want...

Thanks in advance..... Waiting for reply before another crash occur.....:p

---

### Post by llamakc on 2007-06-16
Sounds like a bad hard drive or data cable. Try a new data cable or IDE/SATA port to see if that helps first. If not, try a second hard drive.

You can look at the output of the command `dmesg` in the Terminal and cut/paste that here for others to look for any errors logged.

---

### Post by tgalati4 on 2007-06-16
Try Dapper 6.06.1 LTS.  Boot it as a Live CD and see how long it stays up.  If you get 3 days of uptime, then try installing it.

How well does Vista run on your hardware?

---

### Post by sunshine12 on 2007-06-16
**Output of dmesg.. hope this will be helpful**



[  158.545148] irq event 11: bogus return value e0000061
[  158.545157]  [<c0154394>] __report_bad_irq+0x24/0x80
[  158.545172]  [<c0154461>] note_interrupt+0x71/0x290
[  158.545180]  [<c0284f29>] net_rx_action+0xc9/0x220
[  158.545201]  [<c01538c0>] handle_IRQ_event+0x30/0x60
[  158.545215]  [<c01551cb>] handle_level_irq+0xeb/0x120
[  158.545229]  [<c0105b70>] do_IRQ+0x40/0x80
[  158.545244]  [<c0104233>] common_interrupt+0x23/0x30
[  158.545278]  =======================
[  158.545281] handlers:
[  158.545285] [<c88eef10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  158.545315] [<c89b5800>] (silan_interrupt+0x0/0xa80 [sc92031])
[  158.550749] irq event 11: bogus return value e0000061
[  158.550787]  [<c0154394>] __report_bad_irq+0x24/0x80
[  158.550813]  [<c0154461>] note_interrupt+0x71/0x290
[  158.550832]  [<c01538c0>] handle_IRQ_event+0x30/0x60
[  158.550846]  [<c01551cb>] handle_level_irq+0xeb/0x120
[  158.550862]  [<c0105b70>] do_IRQ+0x40/0x80
[  158.550883]  [<c0104233>] common_interrupt+0x23/0x30
[  158.550919]  =======================
[  158.550922] handlers:
[  158.550926] [<c88eef10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  158.550997] [<c89b5800>] (silan_interrupt+0x0/0xa80 [sc92031])
[  158.551128] irq event 11: bogus return value e0000061
[  158.551138]  [<c0154394>] __report_bad_irq+0x24/0x80
[  158.551153]  [<c0154461>] note_interrupt+0x71/0x290
[  158.551172]  [<c01538c0>] handle_IRQ_event+0x30/0x60
[  158.551186]  [<c01551cb>] handle_level_irq+0xeb/0x120
[  158.551200]  [<c0105b70>] do_IRQ+0x40/0x80
[  158.551216]  [<c0104233>] common_interrupt+0x23/0x30
[  158.551237]  [<c01300d8>] do_timer+0x7b8/0x820
[  158.551250]  [<c02ee85d>] _spin_unlock_irqrestore+0xd/0x20
[  158.551270]  [<c01324d2>] group_send_sig_info+0x72/0x80
[  158.551289]  [<c0132c79>] send_group_sig_info+0x29/0x40
[  158.551303]  [<c012a946>] it_real_fn+0x26/0x70
[  158.551324]  [<c012a920>] it_real_fn+0x0/0x70
[  158.551335]  [<c013dd13>] hrtimer_run_queues+0x123/0x150
[  158.551357]  [<c0284cb3>] process_backlog+0x93/0x130
[  158.551375]  [<c012f632>] run_timer_softirq+0x22/0x1a0
[  158.551386]  [<c0284f29>] net_rx_action+0xc9/0x220
[  158.551405]  [<c012b422>] __do_softirq+0x82/0x100
[  158.551424]  [<c012b4f5>] do_softirq+0x55/0x60
[  158.551434]  [<c0105b75>] do_IRQ+0x45/0x80
[  158.551449]  [<c0104233>] common_interrupt+0x23/0x30
[  158.551483]  =======================
[  158.551487] handlers:
[  158.551490] [<c88eef10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  158.551521] [<c89b5800>] (silan_interrupt+0x0/0xa80 [sc92031])
[  158.556741] irq event 11: bogus return value e0000061
[  158.556754]  [<c0154394>] __report_bad_irq+0x24/0x80
[  158.556771]  [<c0154461>] note_interrupt+0x71/0x290
[  158.556790]  [<c01538c0>] handle_IRQ_event+0x30/0x60
[  158.556804]  [<c01551cb>] handle_level_irq+0xeb/0x120
[  158.556818]  [<c0105b70>] do_IRQ+0x40/0x80
[  158.556835]  [<c0104233>] common_interrupt+0x23/0x30
[  158.556859]  [<c01270a8>] do_syslog+0x338/0x410
[  158.556891]  [<c0176e2c>] vfs_read+0xbc/0x190
[  158.556903]  [<c01b16f0>] kmsg_read+0x0/0x50
[  158.556923]  [<c01773b1>] sys_read+0x41/0x70
[  158.556939]  [<c01031f0>] sysenter_past_esp+0x69/0xa9
[  158.556973]  =======================
[  158.556976] handlers:
[  158.556980] [<c88eef10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  158.557019] [<c89b5800>] (silan_interrupt+0x0/0xa80 [sc92031])
[  158.557113] irq event 11: bogus return value e0000061
[  158.557123]  [<c0154394>] __report_bad_irq+0x24/0x80
[  158.557139]  [<c0154461>] note_interrupt+0x71/0x290
[  158.557157]  [<c01538c0>] handle_IRQ_event+0x30/0x60
[  158.557171]  [<c01551cb>] handle_level_irq+0xeb/0x120
[  158.557185]  [<c0105b70>] do_IRQ+0x40/0x80
[  158.557200]  [<c0104233>] common_interrupt+0x23/0x30
[  158.557224]  [<c01c6502>] dummy_file_permission+0x2/0x10
[  158.557239]  [<c0176c77>] vfs_write+0x97/0x190
[  158.557249]  [<c01b16f0>] kmsg_read+0x0/0x50
[  158.557262]  [<c0177421>] sys_write+0x41/0x70
[  158.557278]  [<c01031f0>] sysenter_past_esp+0x69/0xa9
[  158.557312]  =======================
[  158.557315] handlers:
[  158.557319] [<c88eef10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  158.557349] [<c89b5800>] (silan_interrupt+0x0/0xa80 [sc92031])
[  158.560652] irq event 11: bogus return value e0000061
[  158.560686]  [<c0154394>] __report_bad_irq+0x24/0x80
[  158.560710]  [<c0154461>] note_interrupt+0x71/0x290
[  158.560729]  [<c01538c0>] handle_IRQ_event+0x30/0x60
[  158.560744]  [<c01551cb>] handle_level_irq+0xeb/0x120
[  158.560758]  [<c0105b70>] do_IRQ+0x40/0x80
[  158.560778]  [<c0104233>] common_interrupt+0x23/0x30
[  158.560813]  =======================
[  158.560817] handlers:
[  158.560821] [<c88eef10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  158.560889] [<c89b5800>] (silan_interrupt+0x0/0xa80 [sc92031])
[  158.560986] irq event 11: bogus return value e0000061
[  158.560996]  [<c0154394>] __report_bad_irq+0x24/0x80
[  158.561011]  [<c0154461>] note_interrupt+0x71/0x290
[  158.561019]  [<c0284f29>] net_rx_action+0xc9/0x220
[  158.561039]  [<c01538c0>] handle_IRQ_event+0x30/0x60
[  158.561053]  [<c01551cb>] handle_level_irq+0xeb/0x120
[  158.561067]  [<c0105b70>] do_IRQ+0x40/0x80
[  158.561083]  [<c0104233>] common_interrupt+0x23/0x30
[  158.561117]  =======================
[  158.561120] handlers:
[  158.561124] [<c88eef10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  158.561153] [<c89b5800>] (silan_interrupt+0x0/0xa80 [sc92031])
[  158.566723] irq event 11: bogus return value e0000061
[  158.566767]  [<c0154394>] __report_bad_irq+0x24/0x80
[  158.566794]  [<c0154461>] note_interrupt+0x71/0x290
[  158.566814]  [<c01538c0>] handle_IRQ_event+0x30/0x60
[  158.566829]  [<c01551cb>] handle_level_irq+0xeb/0x120
[  158.566844]  [<c0105b70>] do_IRQ+0x40/0x80
[  158.566867]  [<c0104233>] common_interrupt+0x23/0x30
[  158.566902]  =======================
[  158.566906] handlers:
[  158.566910] [<c88eef10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  158.566987] [<c89b5800>] (silan_interrupt+0x0/0xa80 [sc92031])
[  158.567131] irq event 11: bogus return value e0000061
[  158.567140]  [<c0154394>] __report_bad_irq+0x24/0x80
[  158.567157]  [<c0154461>] note_interrupt+0x71/0x290
[  158.567164]  [<c028484c>] net_tx_action+0x5c/0x110
[  158.567184]  [<c01538c0>] handle_IRQ_event+0x30/0x60
[  158.567198]  [<c01551cb>] handle_level_irq+0xeb/0x120
[  158.567212]  [<c0105b70>] do_IRQ+0x40/0x80
[  158.567227]  [<c0104233>] common_interrupt+0x23/0x30
[  158.567252]  [<c02ec66c>] __sched_text_start+0x32c/0xa90
[  158.567313]  [<c02ed618>] schedule_timeout+0x78/0xd0
[  158.567324]  [<c013b0ad>] add_wait_queue+0x1d/0x50
[  158.567343]  [<c017c2ce>] pipe_poll+0x2e/0x90
[  158.567362]  [<c0183297>] do_sys_poll+0x277/0x3e0
[  158.567386]  [<c0183ec0>] __pollwait+0x0/0xf0
[  158.567403]  [<c0120b40>] default_wake_function+0x0/0x10
[  158.567421]  [<c0120b40>] default_wake_function+0x0/0x10
[  158.567438]  [<c0120b40>] default_wake_function+0x0/0x10
[  158.567455]  [<c0120b40>] default_wake_function+0x0/0x10
[  158.567471]  [<c0120b40>] default_wake_function+0x0/0x10
[  158.567488]  [<c0120b40>] default_wake_function+0x0/0x10
[  158.567505]  [<c0120b40>] default_wake_function+0x0/0x10
[  158.567520]  [<c011e341>] __activate_task+0x21/0x40
[  158.567544]  [<c0120706>] try_to_wake_up+0x46/0x480
[  158.567555]  [<c0120706>] try_to_wake_up+0x46/0x480
[  158.567573]  [<c011e0d9>] __wake_up_common+0x39/0x60
[  158.567581]  [<c01f17d8>] delay_tsc+0x18/0x30
[  158.567594]  [<c01f17d8>] delay_tsc+0x18/0x30
[  158.567604]  [<c01f17d8>] delay_tsc+0x18/0x30
[  158.567615]  [<c01f1836>] __delay+0x6/0x10
[  158.567623]  [<c88aca93>] ata_exec_command+0x23/0x30 [libata]
[  158.567718]  [<c88acbc3>] ata_bmdma_setup+0x53/0x70 [libata]
[  158.567750]  [<c88ac9ab>] ata_bmdma_start+0xb/0x20 [libata]
[  158.567782]  [<c88a85a7>] ata_qc_issue_prot+0x187/0x290 [libata]
[  158.567823]  [<c88a3b3e>] ata_qc_issue+0xae/0x4c0 [libata]
[  158.567878]  [<c015a012>] mempool_free+0x42/0x90
[  158.567892]  [<c019a412>] bio_put+0x22/0x30
[  158.567901]  [<c019f015>] mpage_end_io_read+0x75/0x80
[  158.567914]  [<c02328ee>] __add_entropy_words+0x5e/0x1d0
[  158.567927]  [<c01e9c11>] cfq_arm_slice_timer+0x91/0x110
[  158.567954]  [<c01eb32d>] cfq_completed_request+0xbd/0x170
[  158.567965]  [<c011e678>] __wake_up+0x38/0x50
[  158.567981]  [<c8881ce3>] scsi_run_queue+0xd3/0x1a0 [scsi_mod]
[  158.568070]  [<c01de9fd>] elv_queue_empty+0x1d/0x20
[  158.568084]  [<c01e2a2f>] blk_run_queue+0x1f/0x70
[  158.568104]  [<c8882190>] scsi_next_command+0x30/0x50 [scsi_mod]
[  158.568173]  [<c8859975>] sd_rw_intr+0x75/0x2e0 [sd_mod]
[  158.568221]  [<c887d491>] scsi_finish_command+0x51/0xa0 [scsi_mod]
[  158.568262]  [<c01e32f8>] blk_done_softirq+0x68/0x80
[  158.568275]  [<c012b422>] __do_softirq+0x82/0x100
[  158.568308]  [<c018342b>] sys_poll+0x2b/0x40
[  158.568319]  [<c01031f0>] sysenter_past_esp+0x69/0xa9
[  158.568353]  =======================
[  158.568357] handlers:
[  158.568360] [<c88eef10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  158.568398] [<c89b5800>] (silan_interrupt+0x0/0xa80 [sc92031])
[  165.923555] irq event 11: bogus return value e0000061
[  165.923601]  [<c0154394>] __report_bad_irq+0x24/0x80
[  165.923629]  [<c0154461>] note_interrupt+0x71/0x290
[  165.923649]  [<c01538c0>] handle_IRQ_event+0x30/0x60
[  165.923663]  [<c01551cb>] handle_level_irq+0xeb/0x120
[  165.923679]  [<c0105b70>] do_IRQ+0x40/0x80
[  165.923700]  [<c0104233>] common_interrupt+0x23/0x30
[  165.923710]  [<c0101e00>] default_idle+0x0/0x60
[  165.923731]  [<c011c092>] native_safe_halt+0x2/0x10
[  165.923750]  [<c0101e3d>] default_idle+0x3d/0x60
[  165.923757]  [<c0101409>] cpu_idle+0x49/0xd0
[  165.923769]  [<c03d77f5>] start_kernel+0x365/0x420
[  165.923788]  [<c03d7230>] unknown_bootoption+0x0/0x260
[  165.923812]  =======================
[  165.923815] handlers:
[  165.923819] [<c88eef10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  165.923905] [<c89b5800>] (silan_interrupt+0x0/0xa80 [sc92031])
[  165.962718] irq event 11: bogus return value e0000061
[  165.962763]  [<c0154394>] __report_bad_irq+0x24/0x80
[  165.962789]  [<c0154461>] note_interrupt+0x71/0x290
[  165.962809]  [<c01538c0>] handle_IRQ_event+0x30/0x60
[  165.962823]  [<c01551cb>] handle_level_irq+0xeb/0x120
[  165.962838]  [<c0105b70>] do_IRQ+0x40/0x80
[  165.962860]  [<c0104233>] common_interrupt+0x23/0x30
[  165.962870]  [<c0101e00>] default_idle+0x0/0x60
[  165.962890]  [<c011c092>] native_safe_halt+0x2/0x10
[  165.962909]  [<c0101e3d>] default_idle+0x3d/0x60
[  165.962916]  [<c0101409>] cpu_idle+0x49/0xd0
[  165.962928]  [<c03d77f5>] start_kernel+0x365/0x420
[  165.962946]  [<c03d7230>] unknown_bootoption+0x0/0x260
[  165.962969]  =======================
[  165.962973] handlers:
[  165.962977] [<c88eef10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  165.963057] [<c89b5800>] (silan_interrupt+0x0/0xa80 [sc92031])
[  172.442814] irq event 11: bogus return value e0000061
[  172.442860]  [<c0154394>] __report_bad_irq+0x24/0x80
[  172.442888]  [<c0154461>] note_interrupt+0x71/0x290
[  172.442907]  [<c01538c0>] handle_IRQ_event+0x30/0x60
[  172.442922]  [<c01551cb>] handle_level_irq+0xeb/0x120
[  172.442937]  [<c0105b70>] do_IRQ+0x40/0x80
[  172.442960]  [<c0104233>] common_interrupt+0x23/0x30
[  172.442979]  [<c02c007b>] tcp_get_available_congestion_control+0x3b/0x90
[  172.443000]  [<c01f5fb2>] percpu_counter_mod+0x22/0x70
[  172.443027]  [<c01777b0>] __fput+0x110/0x190
[  172.443049]  [<c0174ae7>] filp_close+0x47/0x80
[  172.443073]  [<c0175e4b>] sys_close+0x6b/0xd0
[  172.443085]  [<c01031f0>] sysenter_past_esp+0x69/0xa9
[  172.443106]  [<c02e0033>] xfrm_state_find+0x4e3/0x570
[  172.443131]  =======================
[  172.443135] handlers:
[  172.443139] [<c88eef10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  172.443224] [<c89b5800>] (silan_interrupt+0x0/0xa80 [sc92031])
[  172.632967] irq event 11: bogus return value e0000061
[  172.633015]  [<c0154394>] __report_bad_irq+0x24/0x80
[  172.633042]  [<c0154461>] note_interrupt+0x71/0x290
[  172.633062]  [<c01538c0>] handle_IRQ_event+0x30/0x60
[  172.633076]  [<c01551cb>] handle_level_irq+0xeb/0x120
[  172.633091]  [<c0105b70>] do_IRQ+0x40/0x80
[  172.633113]  [<c0104233>] common_interrupt+0x23/0x30
[  172.633123]  [<c0101e00>] default_idle+0x0/0x60
[  172.633143]  [<c011c092>] native_safe_halt+0x2/0x10
[  172.633162]  [<c0101e3d>] default_idle+0x3d/0x60
[  172.633170]  [<c0101409>] cpu_idle+0x49/0xd0
[  172.633181]  [<c03d77f5>] start_kernel+0x365/0x420
[  172.633201]  [<c03d7230>] unknown_bootoption+0x0/0x260
[  172.633225]  =======================
[  172.633229] handlers:
[  172.633233] [<c88eef10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  172.633317] [<c89b5800>] (silan_interrupt+0x0/0xa80 [sc92031])
[  179.162459] irq event 11: bogus return value e0000061
[  179.162506]  [<c0154394>] __report_bad_irq+0x24/0x80
[  179.162534]  [<c0154461>] note_interrupt+0x71/0x290
[  179.162553]  [<c01538c0>] handle_IRQ_event+0x30/0x60
[  179.162567]  [<c01551cb>] handle_level_irq+0xeb/0x120
[  179.162582]  [<c0105b70>] do_IRQ+0x40/0x80
[  179.162596]  [<c0105b75>] do_IRQ+0x45/0x80
[  179.162609]  [<c0104233>] common_interrupt+0x23/0x30
[  179.162634]  [<c02ec6b8>] __sched_text_start+0x378/0xa90
[  179.162653]  [<c010144d>] cpu_idle+0x8d/0xd0
[  179.162664]  [<c03d77f5>] start_kernel+0x365/0x420
[  179.162684]  [<c03d7230>] unknown_bootoption+0x0/0x260
[  179.162708]  =======================
[  179.162711] handlers:
[  179.162715] [<c88eef10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  179.162801] [<c89b5800>] (silan_interrupt+0x0/0xa80 [sc92031])
[  179.182790] irq event 11: bogus return value e0000061
[  179.182835]  [<c0154394>] __report_bad_irq+0x24/0x80
[  179.182861]  [<c0154461>] note_interrupt+0x71/0x290
[  179.182880]  [<c01538c0>] handle_IRQ_event+0x30/0x60
[  179.182894]  [<c01551cb>] handle_level_irq+0xeb/0x120
[  179.182909]  [<c0105b70>] do_IRQ+0x40/0x80
[  179.182931]  [<c0104233>] common_interrupt+0x23/0x30
[  179.182941]  [<c0101e00>] default_idle+0x0/0x60
[  179.182961]  [<c011c092>] native_safe_halt+0x2/0x10
[  179.182981]  [<c0101e3d>] default_idle+0x3d/0x60
[  179.182988]  [<c0101409>] cpu_idle+0x49/0xd0
[  179.182999]  [<c03d77f5>] start_kernel+0x365/0x420
[  179.183018]  [<c03d7230>] unknown_bootoption+0x0/0x260
[  179.183042]  =======================
[  179.183045] handlers:
[  179.183049] [<c88eef10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  179.183133] [<c89b5800>] (silan_interrupt+0x0/0xa80 [sc92031])
[  179.186652] irq event 11: bogus return value e0000061
[  179.186697]  [<c0154394>] __report_bad_irq+0x24/0x80
[  179.186723]  [<c0154461>] note_interrupt+0x71/0x290
[  179.186731]  [<c027926c>] sock_map_fd+0x3c/0x60
[  179.186753]  [<c01538c0>] handle_IRQ_event+0x30/0x60
[  179.186767]  [<c01551cb>] handle_level_irq+0xeb/0x120
[  179.186782]  [<c0105b70>] do_IRQ+0x40/0x80
[  179.186804]  [<c0104233>] common_interrupt+0x23/0x30
[  179.186825]  [<c02e0033>] xfrm_state_find+0x4e3/0x570
[  179.186850]  =======================
[  179.186854] handlers:
[  179.186858] [<c88eef10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  179.186942] [<c89b5800>] (silan_interrupt+0x0/0xa80 [sc92031])
[  179.480313] irq event 11: bogus return value e0000061
[  179.480355]  [<c0154394>] __report_bad_irq+0x24/0x80
[  179.480381]  [<c0154461>] note_interrupt+0x71/0x290
[  179.480400]  [<c01538c0>] handle_IRQ_event+0x30/0x60
[  179.480415]  [<c01551cb>] handle_level_irq+0xeb/0x120
[  179.480430]  [<c0105b70>] do_IRQ+0x40/0x80
[  179.480451]  [<c0104233>] common_interrupt+0x23/0x30
[  179.480460]  [<c0101e00>] default_idle+0x0/0x60
[  179.480481]  [<c011c092>] native_safe_halt+0x2/0x10
[  179.480500]  [<c0101e3d>] default_idle+0x3d/0x60
[  179.480507]  [<c0101409>] cpu_idle+0x49/0xd0
[  179.480519]  [<c03d77f5>] start_kernel+0x365/0x420
[  179.480538]  [<c03d7230>] unknown_bootoption+0x0/0x260
[  179.480561]  =======================
[  179.480565] handlers:
[  179.480569] [<c88eef10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  179.480653] [<c89b5800>] (silan_interrupt+0x0/0xa80 [sc92031])
[  179.480791] irq event 11: bogus return value e0000061
[  179.480801]  [<c0154394>] __report_bad_irq+0x24/0x80
[  179.480817]  [<c0154461>] note_interrupt+0x71/0x290
[  179.480836]  [<c01538c0>] handle_IRQ_event+0x30/0x60
[  179.480850]  [<c01551cb>] handle_level_irq+0xeb/0x120
[  179.480864]  [<c0105b70>] do_IRQ+0x40/0x80
[  179.480872]  [<c018ac49>] file_update_time+0x39/0xa0
[  179.480894]  [<c0104233>] common_interrupt+0x23/0x30
[  179.480918]  [<c02ec66c>] __sched_text_start+0x32c/0xa90
[  179.480939]  [<c0176355>] do_sync_write+0xd5/0x120
[  179.480972]  [<c013adf0>] autoremove_wake_function+0x0/0x50
[  179.480993]  [<c013afa0>] prepare_to_wait+0x20/0x70
[  179.481007]  [<c012712d>] do_syslog+0x3bd/0x410
[  179.481032]  [<c013adf0>] autoremove_wake_function+0x0/0x50
[  179.481049]  [<c0176e2c>] vfs_read+0xbc/0x190
[  179.481060]  [<c01b16f0>] kmsg_read+0x0/0x50
[  179.481080]  [<c01773b1>] sys_read+0x41/0x70
[  179.481096]  [<c01031f0>] sysenter_past_esp+0x69/0xa9
[  179.481131]  =======================
[  179.481134] handlers:
[  179.481138] [<c88eef10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  179.481168] [<c89b5800>] (silan_interrupt+0x0/0xa80 [sc92031])
[  179.483019] irq event 11: bogus return value e0000061
[  179.483035]  [<c0154394>] __report_bad_irq+0x24/0x80
[  179.483051]  [<c0154461>] note_interrupt+0x71/0x290
[  179.483069]  [<c01538c0>] handle_IRQ_event+0x30/0x60
[  179.483083]  [<c01551cb>] handle_level_irq+0xeb/0x120
[  179.483097]  [<c0105b70>] do_IRQ+0x40/0x80
[  179.483113]  [<c0104233>] common_interrupt+0x23/0x30
[  179.483133]  [<c017007b>] shmem_getpage+0xab/0x630
[  179.483150]  [<c01779f1>] fget_light+0x21/0x90
[  179.483163]  [<c01773f7>] sys_write+0x17/0x70
[  179.483179]  [<c01031f0>] sysenter_past_esp+0x69/0xa9
[  179.483213]  =======================
[  179.483216] handlers:
[  179.483220] [<c88eef10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  179.483256] [<c89b5800>] (silan_interrupt+0x0/0xa80 [sc92031])
[  179.800060] irq event 11: bogus return value e0000061
[  179.800107]  [<c0154394>] __report_bad_irq+0x24/0x80
[  179.800135]  [<c0154461>] note_interrupt+0x71/0x290
[  179.800154]  [<c01538c0>] handle_IRQ_event+0x30/0x60
[  179.800169]  [<c01551cb>] handle_level_irq+0xeb/0x120
[  179.800184]  [<c0105b70>] do_IRQ+0x40/0x80
[  179.800206]  [<c0104233>] common_interrupt+0x23/0x30
[  179.800216]  [<c0101e00>] default_idle+0x0/0x60
[  179.800236]  [<c011c092>] native_safe_halt+0x2/0x10
[  179.800255]  [<c0101e3d>] default_idle+0x3d/0x60
[  179.800263]  [<c0101409>] cpu_idle+0x49/0xd0
[  179.800274]  [<c03d77f5>] start_kernel+0x365/0x420
[  179.800294]  [<c03d7230>] unknown_bootoption+0x0/0x260
[  179.800317]  =======================
[  179.800321] handlers:
[  179.800325] [<c88eef10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  179.800410] [<c89b5800>] (silan_interrupt+0x0/0xa80 [sc92031])
[  179.926127] irq event 11: bogus return value e0000061
[  179.926175]  [<c0154394>] __report_bad_irq+0x24/0x80
[  179.926203]  [<c0154461>] note_interrupt+0x71/0x290
[  179.926222]  [<c01538c0>] handle_IRQ_event+0x30/0x60
[  179.926237]  [<c01551cb>] handle_level_irq+0xeb/0x120
[  179.926252]  [<c0105b70>] do_IRQ+0x40/0x80
[  179.926274]  [<c0104233>] common_interrupt+0x23/0x30
[  179.926284]  [<c0101e00>] default_idle+0x0/0x60
[  179.926304]  [<c011c092>] native_safe_halt+0x2/0x10
[  179.926323]  [<c0101e3d>] default_idle+0x3d/0x60
[  179.926330]  [<c0101409>] cpu_idle+0x49/0xd0
[  179.926342]  [<c03d77f5>] start_kernel+0x365/0x420
[  179.926361]  [<c03d7230>] unknown_bootoption+0x0/0x260
[  179.926385]  =======================
[  179.926388] handlers:
[  179.926392] [<c88eef10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  179.926479] [<c89b5800>] (silan_interrupt+0x0/0xa80 [sc92031])
[  179.926594] irq event 11: bogus return value e0000061
[  179.926604]  [<c0154394>] __report_bad_irq+0x24/0x80
[  179.926620]  [<c0154461>] note_interrupt+0x71/0x290
[  179.926639]  [<c01538c0>] handle_IRQ_event+0x30/0x60
[  179.926653]  [<c01551cb>] handle_level_irq+0xeb/0x120
[  179.926667]  [<c0105b70>] do_IRQ+0x40/0x80
[  179.926675]  [<c018ac49>] file_update_time+0x39/0xa0
[  179.926697]  [<c0104233>] common_interrupt+0x23/0x30
[  179.926721]  [<c02ec66c>] __sched_text_start+0x32c/0xa90
[  179.926742]  [<c0176355>] do_sync_write+0xd5/0x120
[  179.926776]  [<c013adf0>] autoremove_wake_function+0x0/0x50
[  179.926795]  [<c013afa0>] prepare_to_wait+0x20/0x70
[  179.926809]  [<c012712d>] do_syslog+0x3bd/0x410
[  179.926834]  [<c013adf0>] autoremove_wake_function+0x0/0x50
[  179.926851]  [<c0176e2c>] vfs_read+0xbc/0x190
[  179.926862]  [<c01b16f0>] kmsg_read+0x0/0x50
[  179.926882]  [<c01773b1>] sys_read+0x41/0x70
[  179.926898]  [<c01031f0>] sysenter_past_esp+0x69/0xa9
[  179.926932]  =======================
[  179.926936] handlers:
[  179.926940] [<c88eef10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  179.926971] [<c89b5800>] (silan_interrupt+0x0/0xa80 [sc92031])
[  179.934081] irq event 11: bogus return value e0000061
[  179.934128]  [<c0154394>] __report_bad_irq+0x24/0x80
[  179.934154]  [<c0154461>] note_interrupt+0x71/0x290
[  179.934173]  [<c01538c0>] handle_IRQ_event+0x30/0x60
[  179.934188]  [<c01551cb>] handle_level_irq+0xeb/0x120
[  179.934200]  [<c03d7230>] unknown_bootoption+0x0/0x260
[  179.934220]  [<c0105b70>] do_IRQ+0x40/0x80
[  179.934241]  [<c0104233>] common_interrupt+0x23/0x30
[  179.934252]  [<c02bfe20>] tcp_set_allowed_congestion_control+0x0/0x110
[  179.934269]  [<c03d7230>] unknown_bootoption+0x0/0x260
[  179.934297]  =======================
[  179.934301] handlers:
[  179.934304] [<c88eef10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  179.934387] [<c89b5800>] (silan_interrupt+0x0/0xa80 [sc92031])
[  179.934497] irq event 11: bogus return value e0000061
[  179.934506]  [<c0154394>] __report_bad_irq+0x24/0x80
[  179.934522]  [<c0154461>] note_interrupt+0x71/0x290
[  179.934540]  [<c01538c0>] handle_IRQ_event+0x30/0x60
[  179.934554]  [<c01551cb>] handle_level_irq+0xeb/0x120
[  179.934568]  [<c0105b70>] do_IRQ+0x40/0x80
[  179.934575]  [<c013aecd>] finish_wait+0x2d/0x70
[  179.934594]  [<c0104233>] common_interrupt+0x23/0x30
[  179.934618]  [<c0176e35>] vfs_read+0xc5/0x190
[  179.934633]  [<c01b16f0>] kmsg_read+0x0/0x50
[  179.934653]  [<c01773b1>] sys_read+0x41/0x70
[  179.934669]  [<c01031f0>] sysenter_past_esp+0x69/0xa9
[  179.934704]  =======================
[  179.934707] handlers:
[  179.934711] [<c88eef10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  179.934741] [<c89b5800>] (silan_interrupt+0x0/0xa80 [sc92031])
[  180.020022] irq event 11: bogus return value e0000061
[  180.020068]  [<c0154394>] __report_bad_irq+0x24/0x80
[  180.020095]  [<c0154461>] note_interrupt+0x71/0x290
[  180.020104]  [<c027926c>] sock_map_fd+0x3c/0x60
[  180.020124]  [<c01538c0>] handle_IRQ_event+0x30/0x60
[  180.020139]  [<c01551cb>] handle_level_irq+0xeb/0x120
[  180.020154]  [<c0105b70>] do_IRQ+0x40/0x80
[  180.020175]  [<c0104233>] common_interrupt+0x23/0x30
[  180.020197]  [<c02e0033>] xfrm_state_find+0x4e3/0x570
[  180.020222]  =======================
[  180.020226] handlers:
[  180.020229] [<c88eef10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  180.020313] [<c89b5800>] (silan_interrupt+0x0/0xa80 [sc92031])
[  180.225917] irq event 11: bogus return value e0000061
[  180.225964]  [<c0154394>] __report_bad_irq+0x24/0x80
[  180.225991]  [<c0154461>] note_interrupt+0x71/0x290
[  180.226010]  [<c01538c0>] handle_IRQ_event+0x30/0x60
[  180.226025]  [<c01551cb>] handle_level_irq+0xeb/0x120
[  180.226040]  [<c0105b70>] do_IRQ+0x40/0x80
[  180.226062]  [<c0104233>] common_interrupt+0x23/0x30
[  180.226072]  [<c0101e00>] default_idle+0x0/0x60
[  180.226093]  [<c011c092>] native_safe_halt+0x2/0x10
[  180.226111]  [<c0101e3d>] default_idle+0x3d/0x60
[  180.226118]  [<c0101409>] cpu_idle+0x49/0xd0
[  180.226130]  [<c03d77f5>] start_kernel+0x365/0x420
[  180.226148]  [<c03d7230>] unknown_bootoption+0x0/0x260
[  180.226172]  =======================
[  180.226176] handlers:
[  180.226179] [<c88eef10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  180.226261] [<c89b5800>] (silan_interrupt+0x0/0xa80 [sc92031])
[  180.226371] irq event 11: bogus return value e0000061
[  180.226381]  [<c0154394>] __report_bad_irq+0x24/0x80
[  180.226396]  [<c0154461>] note_interrupt+0x71/0x290
[  180.226414]  [<c01538c0>] handle_IRQ_event+0x30/0x60
[  180.226428]  [<c01551cb>] handle_level_irq+0xeb/0x120
[  180.226442]  [<c0105b70>] do_IRQ+0x40/0x80
[  180.226450]  [<c018ac49>] file_update_time+0x39/0xa0
[  180.226471]  [<c0104233>] common_interrupt+0x23/0x30
[  180.226495]  [<c02ec66c>] __sched_text_start+0x32c/0xa90
[  180.226515]  [<c0176355>] do_sync_write+0xd5/0x120
[  180.226549]  [<c013adf0>] autoremove_wake_function+0x0/0x50
[  180.226568]  [<c013afa0>] prepare_to_wait+0x20/0x70
[  180.226582]  [<c012712d>] do_syslog+0x3bd/0x410
[  180.226606]  [<c013adf0>] autoremove_wake_function+0x0/0x50
[  180.226624]  [<c0176e2c>] vfs_read+0xbc/0x190
[  180.226634]  [<c01b16f0>] kmsg_read+0x0/0x50
[  180.226654]  [<c01773b1>] sys_read+0x41/0x70
[  180.226670]  [<c01031f0>] sysenter_past_esp+0x69/0xa9
[  180.226704]  =======================
[  180.226708] handlers:
[  180.226712] [<c88eef10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  180.226743] [<c89b5800>] (silan_interrupt+0x0/0xa80 [sc92031])
[  180.231944] irq event 11: bogus return value e0000061
[  180.231990]  [<c0154394>] __report_bad_irq+0x24/0x80
[  180.232016]  [<c0154461>] note_interrupt+0x71/0x290
[  180.232036]  [<c01538c0>] handle_IRQ_event+0x30/0x60
[  180.232050]  [<c01551cb>] handle_level_irq+0xeb/0x120
[  180.232065]  [<c0105b70>] do_IRQ+0x40/0x80
[  180.232087]  [<c0104233>] common_interrupt+0x23/0x30
[  180.232122]  =======================
[  180.232126] handlers:
[  180.232130] [<c88eef10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  180.232207] [<c89b5800>] (silan_interrupt+0x0/0xa80 [sc92031])
[  600.992900] EXT3-fs error (device sda1): ext3_free_blocks_sb: bit already cleared for block 2037833
[  600.992925] Aborting journal on device sda1.
[  600.993556] ext3_abort called.
[  600.993565] EXT3-fs error (device sda1): ext3_journal_start_sb: Detected aborted journal
[  600.993597] Remounting filesystem read-only
[  600.994522] Remounting filesystem read-only
[  600.998624] EXT3-fs error (device sda1) in ext3_reserve_inode_write: Journal has aborted
[  600.998646] EXT3-fs error (device sda1) in ext3_truncate: Journal has aborted
[  600.998655] EXT3-fs error (device sda1) in ext3_reserve_inode_write: Journal has aborted
[  600.998662] EXT3-fs error (device sda1) in ext3_orphan_del: Journal has aborted
[  600.998668] EXT3-fs error (device sda1) in ext3_reserve_inode_write: Journal has aborted
[  601.002466] __journal_remove_journal_head: freeing b_committed_data

---

### Post by sunshine12 on 2007-06-16
thanks llamakc and tgalati4 for reply..
didn't tried Vista yet, was on XP.. 

There is some problem in the internet connection also.. my ethernet connection working fine if I am browsing sites(no disconnections), but whenever I try to download big files then it freezes after almost 50-60mb download about every 8-10 minutes and then I have to restart my computer to start downloading.
ethernet card is new,  hangzhou silan microelectronics ltd, sc92031 from intex
router is UT-300R2U, 2mbps connection

Waiting for your reply... Thanks

---

### Post by sunshine12 on 2007-06-16
here we go.... it crashed again and reinstalled it.......
anybody please help or should i switch back to xp??

please reply as soon as possible.... Thanks for your support....

---

### Post by sunshine12 on 2007-06-17
should I scan hard disk with Manufacturer's diagnostic software to check if harddisk is ok or not?

---

### Post by tgalati4 on 2007-06-17
Dear Sunshine12,

The dmesg output is not helpful in this case because the machine appears to be having problems with the hardware and that causes the kernel to have fits.

Pentium III's tend to run hot.  Have you cleaned out the machine lately?  You need to blow out the dust, especially the CPU fan and the heat sink on the processor.  The power supply also needs cleaning as the PIII draws a lot of power.  Have you reseated the memory and all of the cables to make sure that they are tight?  Try moving the memory by swapping the slots.

Since your machine is probably 7 years old, hardware problems are likely.  We need to isolate what is wrong with the hardware.  The harddisk could be going bad, and under certain circumstances that could cause what appears to be a freeze.  Although Ubuntu can usually recover from a bad disk and give you warnings that it can't read from the disk.

Be patient, these things take time.  If you have a Live Feisty disk, boot from that, don't boot from the harddisk.  If it freezes while running the Live Disk, then we can be pretty sure that the harddisk is NOT involved.

Don't bother testing the drive with the Manufacturer's disk utility, because your system could freeze in the middle of a low-level format, then you're back to square 1.

We need to determine how long your system will stay up running the Live Disk.  Don't forget to clean the insides and reseat your cards, memory, ribbon cables, and power cables.

---

### Post by sunshine12 on 2007-06-17
> **tgalati4 said:**
> Dear Sunshine12,

The dmesg output is not helpful in this case because the machine appears to be having problems with the hardware and that causes the kernel to have fits.

Pentium III's tend to run hot.  Have you cleaned out the machine lately?  You need to blow out the dust, especially the CPU fan and the heat sink on the processor.  The power supply also needs cleaning as the PIII draws a lot of power.  Have you reseated the memory and all of the cables to make sure that they are tight?  Try moving the memory by swapping the slots.

Since your machine is probably 7 years old, hardware problems are likely.  We need to isolate what is wrong with the hardware.  The harddisk could be going bad, and under certain circumstances that could cause what appears to be a freeze.  Although Ubuntu can usually recover from a bad disk and give you warnings that it can't read from the disk.

Be patient, these things take time.  If you have a Live Feisty disk, boot from that, don't boot from the harddisk.  If it freezes while running the Live Disk, then we can be pretty sure that the harddisk is NOT involved.

Don't bother testing the drive with the Manufacturer's disk utility, because your system could freeze in the middle of a low-level format, then you're back to square 1.

We need to determine how long your system will stay up running the Live Disk.  Don't forget to clean the insides and reseat your cards, memory, ribbon cables, and power cables.

thanks tgalati4 for detailed answer, and please can you tell me what could be the reason for frequent ethernet disconnections while downloading big files(torrents)??
thanks in advance

---

### Post by llamakc on 2007-06-17
Possible hardware failure, which is why you've been counseled to test how long the system can stay running without failure using the livecd.

---

### Post by sunshine12 on 2007-06-17
> **llamakc said:**
> Possible hardware failure, which is why you've been counseled to test how long the system can stay running without failure using the livecd.

Sorry, but I am confused!!!! 
what exactly to do after running live cd??
leave it to see how long it runs without failure or what?? please guide me..
thanks

---

### Post by zigx on 2007-06-18
> **sunshine12 said:**
> Sorry, but I am confused!!!! 
what exactly to do after running live cd??
leave it to see how long it runs without failure or what?? please guide me..
thanks

just let it run for a few days... see if it freezes or something like that.

This test will indicate if the HD is the problem or not.  if its fine then u know the HD is OK and can move on to troubleshoot the next element of your system.

---

### Post by sunshine12 on 2007-06-18
Thanks to all who have replied. and will do whatever you all have said... let's see what will happen, thanks once again.

---

### Post by sunshine12 on 2007-06-20
everything seems stable now, but only one problem remains, and that is frequent disconnection with wired ethernet connection while downloading stuff... 

NIC was not detected and I have installed drivers manually, may be this be a problem.
how to check if there is conflicts in the hardware devices?

---

### Post by sunshine12 on 2007-06-20
I have found the patch file for silan ethernet drivers for linux version 2.6.x, but how to apply that patch, please guide, and if this will solve the problem?

thanks

---

### Post by sunshine12 on 2007-06-20
how to apply a "patch" for the ethernet driver... I have the patch file but don't know how to apply it..
any kind of help is highly appreciated

---

### Post by llamakc on 2007-06-20
Provide a link to this patch you found. Typically, you're going to use the program from the terminal called "patch," but you have to be patching the correct thing and you'll need the kernel headers.

To get started open a Terminal and type:

```

sudo apt-get install linux-headers-`uname -r` build-essential patch

```

Do you have any experience compiling software or recompiling the kernel? You realize this would all be done on the system AFTER you have installed Ubuntu, and not while actively using the LiveCD, right?

---

### Post by sunshine12 on 2007-06-28
Problem Solved...

No more crashing, stable now.

The problem is due to Hardware conflict. The driver for sc92031 NIC was not compatible and that given me a hard time. But Ndiswrapper solved my problem.

Now my system is stable and also not having frequent disconnections from internet.

Thanks to everyone for helping me...

---

### Post by sunshine12 on 2007-07-02
May be not...

The same problem occurred after 15days. There is problem in some block 358 to block 368!!! 
The problem had occured before but fsck solved the problem. But sometime after performing fsck everything seems perfect but it repeats the error again and again..

I think my hard disk is having bad sectors. Is there any way to solve this problem without purchasing a new hard disk or have to replace it with newer one??

thanks

---

### Post by sunshine12 on 2007-07-03
One new thing...

When I fsck from the live cd then this corrects the errors..(like..error reading block 358 while doing inode scan), after I booted from the hard disk and it is working now..

what is the difference doing fsck from live cd and from hard disk with read-only mode??

fsck from hard disk with read only mode corrects errors but it repeates again and again while fsck from live cd solved the problem(temporarily)..

thanks

---

