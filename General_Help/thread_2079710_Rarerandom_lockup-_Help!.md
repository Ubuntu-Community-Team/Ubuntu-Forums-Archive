---
title: "Rare/random lockup- Help!"
date: 2012-11-02
forum: General Help
---

### Post by faroutliving on 2012-11-02
I have a (very) remote server that has randomly hung for 2-6 hours for as long as I can remember. Usually, nothing gets written to the log during this time. It is like it just gets put in a time field. I can usually still ping the server, but that is it. I had surmised that it was some kind of disk issue, but yesterday I actually got a useful log entry. Then again this morning.

Linux 2.6.38-11-generic on x86_64
12 3TB drives in a raid 5 (Areca card)
24Gb ram
Dual Xeon

Help much appreciated!! Any ideas?

Thanks, Deron

```
Nov  2 06:32:35 lisn-mia kernel: [54124.550144] INFO: task jbd2/sda2-8:349 blocked for more than 120 seconds.
Nov  2 06:32:35 lisn-mia kernel: [54124.550150] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Nov  2 06:32:35 lisn-mia kernel: [54124.550161] jbd2/sda2-8     D 0000000000000010     0   349      2 0x00000000
Nov  2 06:32:35 lisn-mia kernel: [54124.550167]  ffff8803241f9af0 0000000000000046 ffff8803241f9fd8 ffff8803241f8000
Nov  2 06:32:35 lisn-mia kernel: [54124.550172]  0000000000013d00 ffff880323ee4858 ffff8803241f9fd8 0000000000013d00
Nov  2 06:32:35 lisn-mia kernel: [54124.550175]  ffff880323518000 ffff880323ee44a0 ffff88063ffe4868 ffff8800bf553d00
Nov  2 06:32:35 lisn-mia kernel: [54124.550179] Call Trace:
Nov  2 06:32:35 lisn-mia kernel: [54124.550190]  [<ffffffff8110c110>] ? sync_page+0x0/0x50
Nov  2 06:32:35 lisn-mia kernel: [54124.550201]  [<ffffffff815c1040>] io_schedule+0x70/0xc0
Nov  2 06:32:35 lisn-mia kernel: [54124.550204]  [<ffffffff8110c150>] sync_page+0x40/0x50
Nov  2 06:32:35 lisn-mia kernel: [54124.550208]  [<ffffffff815c19bf>] __wait_on_bit+0x5f/0x90
Nov  2 06:32:35 lisn-mia kernel: [54124.550212]  [<ffffffff8110c318>] wait_on_page_bit+0x78/0x80
Nov  2 06:32:35 lisn-mia kernel: [54124.550219]  [<ffffffff81087ff0>] ? wake_bit_function+0x0/0x50
Nov  2 06:32:35 lisn-mia kernel: [54124.550223]  [<ffffffff8110c4bd>] filemap_fdatawait_range+0xfd/0x190
Nov  2 06:32:35 lisn-mia kernel: [54124.550227]  [<ffffffff8110e7c5>] ? mempool_alloc_slab+0x15/0x20
Nov  2 06:32:35 lisn-mia kernel: [54124.550231]  [<ffffffff8110eb09>] ? mempool_alloc+0x59/0x140
Nov  2 06:32:35 lisn-mia kernel: [54124.550235]  [<ffffffff8110c57b>] filemap_fdatawait+0x2b/0x30
Nov  2 06:32:35 lisn-mia kernel: [54124.550240]  [<ffffffff81242b53>] journal_finish_inode_data_buffers+0x63/0x170
Nov  2 06:32:35 lisn-mia kernel: [54124.550244]  [<ffffffff81243344>] jbd2_journal_commit_transaction+0x6e4/0x1190
Nov  2 06:32:35 lisn-mia kernel: [54124.550251]  [<ffffffff810761d5>] ? try_to_del_timer_sync+0x85/0xe0
Nov  2 06:32:35 lisn-mia kernel: [54124.550257]  [<ffffffff81247f5b>] kjournald2+0xbb/0x220
Nov  2 06:32:35 lisn-mia kernel: [54124.550261]  [<ffffffff81087fb0>] ? autoremove_wake_function+0x0/0x40
Nov  2 06:32:35 lisn-mia kernel: [54124.550264]  [<ffffffff81247ea0>] ? kjournald2+0x0/0x220
Nov  2 06:32:35 lisn-mia kernel: [54124.550268]  [<ffffffff81087866>] kthread+0x96/0xa0
Nov  2 06:32:35 lisn-mia kernel: [54124.550274]  [<ffffffff8100ce24>] kernel_thread_helper+0x4/0x10
Nov  2 06:32:35 lisn-mia kernel: [54124.550278]  [<ffffffff810877d0>] ? kthread+0x0/0xa0
Nov  2 06:32:35 lisn-mia kernel: [54124.550281]  [<ffffffff8100ce20>] ? kernel_thread_helper+0x0/0x10
Nov  2 06:32:35 lisn-mia kernel: [54124.550284] INFO: task flush-8:0:367 blocked for more than 120 seconds.
Nov  2 06:32:35 lisn-mia kernel: [54124.550286] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Nov  2 06:32:35 lisn-mia kernel: [54124.550289] flush-8:0       D 0000000000000013     0   367      2 0x00000000
Nov  2 06:32:35 lisn-mia kernel: [54124.550293]  ffff880326a636b0 0000000000000046 ffff880326a63fd8 ffff880326a62000
Nov  2 06:32:35 lisn-mia kernel: [54124.550297]  0000000000013d00 ffff880323ccc858 ffff880326a63fd8 0000000000013d00
Nov  2 06:32:35 lisn-mia kernel: [54124.550301]  ffff880327292dc0 ffff880323ccc4a0 ffff880326a636a0 ffff880326a63700
Nov  2 06:32:35 lisn-mia kernel: [54124.550305] Call Trace:
Nov  2 06:32:35 lisn-mia kernel: [54124.550311]  [<ffffffff81241e85>] do_get_write_access+0x255/0x490
Nov  2 06:32:35 lisn-mia kernel: [54124.550315]  [<ffffffff81087ff0>] ? wake_bit_function+0x0/0x50
Nov  2 06:32:35 lisn-mia kernel: [54124.550321]  [<ffffffff81209fbd>] ? ext4_dirty_inode+0x3d/0x60
Nov  2 06:32:35 lisn-mia kernel: [54124.550325]  [<ffffffff81242201>] jbd2_journal_get_write_access+0x31/0x50
Nov  2 06:32:35 lisn-mia kernel: [54124.550331]  [<ffffffff8122900e>] __ext4_journal_get_write_access+0x3e/0x80
Nov  2 06:32:35 lisn-mia kernel: [54124.550336]  [<ffffffff812053f8>] ext4_reserve_inode_write+0x78/0xa0
Nov  2 06:32:35 lisn-mia kernel: [54124.550340]  [<ffffffff81241404>] ? __jbd2_journal_file_buffer+0xd4/0x210
Nov  2 06:32:35 lisn-mia kernel: [54124.550344]  [<ffffffff8120546f>] ext4_mark_inode_dirty+0x4f/0x220
Nov  2 06:32:35 lisn-mia kernel: [54124.550348]  [<ffffffff8121dc53>] ? ext4_journal_start_sb+0xb3/0x140
Nov  2 06:32:35 lisn-mia kernel: [54124.550352]  [<ffffffff81209fbd>] ext4_dirty_inode+0x3d/0x60
Nov  2 06:32:35 lisn-mia kernel: [54124.550358]  [<ffffffff8118b39f>] __mark_inode_dirty+0x3f/0x260
Nov  2 06:32:35 lisn-mia kernel: [54124.550362]  [<ffffffff812037bd>] ext4_da_update_reserve_space+0x1bd/0x220
Nov  2 06:32:35 lisn-mia kernel: [54124.550366]  [<ffffffff81228803>] ext4_ext_map_blocks+0x703/0x770
Nov  2 06:32:35 lisn-mia kernel: [54124.550370]  [<ffffffff81206a1a>] ext4_map_blocks+0x1ea/0x280
Nov  2 06:32:35 lisn-mia kernel: [54124.550374]  [<ffffffff81208d2b>] mpage_da_map_and_submit+0xbb/0x440
Nov  2 06:32:35 lisn-mia kernel: [54124.550378]  [<ffffffff81240923>] ? jbd2_journal_start+0x13/0x20
Nov  2 06:32:35 lisn-mia kernel: [54124.550382]  [<ffffffff8121dc53>] ? ext4_journal_start_sb+0xb3/0x140
Nov  2 06:32:35 lisn-mia kernel: [54124.550386]  [<ffffffff81209936>] ext4_da_writepages+0x336/0x630
Nov  2 06:32:35 lisn-mia kernel: [54124.550393]  [<ffffffff81117191>] do_writepages+0x21/0x40
Nov  2 06:32:35 lisn-mia kernel: [54124.550396]  [<ffffffff8118b65f>] writeback_single_inode+0x9f/0x240
Nov  2 06:32:35 lisn-mia kernel: [54124.550400]  [<ffffffff8118ba4b>] writeback_sb_inodes+0xcb/0x160
Nov  2 06:32:35 lisn-mia kernel: [54124.550405]  [<ffffffff81104461>] ? __perf_event_task_sched_out+0x31/0x40
Nov  2 06:32:35 lisn-mia kernel: [54124.550409]  [<ffffffff8118bc9b>] writeback_inodes_wb+0x10b/0x1c0
Nov  2 06:32:35 lisn-mia kernel: [54124.550413]  [<ffffffff8118c0ce>] wb_writeback+0x37e/0x490
Nov  2 06:32:35 lisn-mia kernel: [54124.550417]  [<ffffffff815c352f>] ? _raw_spin_lock_irqsave+0x2f/0x40
Nov  2 06:32:35 lisn-mia kernel: [54124.550421]  [<ffffffff8107502b>] ? lock_timer_base.clone.20+0x3b/0x70
Nov  2 06:32:35 lisn-mia kernel: [54124.550425]  [<ffffffff8118c401>] wb_do_writeback+0x221/0x230
Nov  2 06:32:35 lisn-mia kernel: [54124.550430]  [<ffffffff8118c492>] bdi_writeback_thread+0x82/0x260
Nov  2 06:32:35 lisn-mia kernel: [54124.550433]  [<ffffffff8118c410>] ? bdi_writeback_thread+0x0/0x260
Nov  2 06:32:35 lisn-mia kernel: [54124.550437]  [<ffffffff81087866>] kthread+0x96/0xa0
Nov  2 06:32:35 lisn-mia kernel: [54124.550441]  [<ffffffff8100ce24>] kernel_thread_helper+0x4/0x10
Nov  2 06:32:35 lisn-mia kernel: [54124.550444]  [<ffffffff810877d0>] ? kthread+0x0/0xa0
Nov  2 06:32:35 lisn-mia kernel: [54124.550448]  [<ffffffff8100ce20>] ? kernel_thread_helper+0x0/0x10
Nov  2 06:32:35 lisn-mia kernel: [54124.550452] INFO: task rs:main Q:Reg:3729 blocked for more than 120 seconds.
Nov  2 06:32:35 lisn-mia kernel: [54124.550454] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Nov  2 06:32:35 lisn-mia kernel: [54124.550456] rs:main Q:Reg   D 000000000000000e     0  3729      1 0x00000000
Nov  2 06:32:35 lisn-mia kernel: [54124.550461]  ffff8801882c79e8 0000000000000086 ffff8801882c7fd8 ffff8801882c6000
Nov  2 06:32:35 lisn-mia kernel: [54124.550465]  0000000000013d00 ffff88031cce5f38 ffff8801882c7fd8 0000000000013d00
Nov  2 06:32:35 lisn-mia kernel: [54124.550469]  ffff8803271fadc0 ffff88031cce5b80 ffff8801882c79d8 ffff8801882c7a38
Nov  2 06:32:35 lisn-mia kernel: [54124.550473] Call Trace:
Nov  2 06:32:35 lisn-mia kernel: [54124.550478]  [<ffffffff81241e85>] do_get_write_access+0x255/0x490
Nov  2 06:32:35 lisn-mia kernel: [54124.550481]  [<ffffffff81087ff0>] ? wake_bit_function+0x0/0x50
Nov  2 06:32:35 lisn-mia kernel: [54124.550485]  [<ffffffff81209fbd>] ? ext4_dirty_inode+0x3d/0x60
Nov  2 06:32:35 lisn-mia kernel: [54124.550490]  [<ffffffff81242201>] jbd2_journal_get_write_access+0x31/0x50
Nov  2 06:32:35 lisn-mia kernel: [54124.550494]  [<ffffffff8122900e>] __ext4_journal_get_write_access+0x3e/0x80
Nov  2 06:32:35 lisn-mia kernel: [54124.550498]  [<ffffffff812053f8>] ext4_reserve_inode_write+0x78/0xa0
Nov  2 06:32:35 lisn-mia kernel: [54124.550502]  [<ffffffff8120546f>] ext4_mark_inode_dirty+0x4f/0x220
Nov  2 06:32:35 lisn-mia kernel: [54124.550505]  [<ffffffff8121dc53>] ? ext4_journal_start_sb+0xb3/0x140
Nov  2 06:32:35 lisn-mia kernel: [54124.550509]  [<ffffffff81209fbd>] ext4_dirty_inode+0x3d/0x60
Nov  2 06:32:35 lisn-mia kernel: [54124.550513]  [<ffffffff8118b39f>] __mark_inode_dirty+0x3f/0x260
Nov  2 06:32:35 lisn-mia kernel: [54124.550518]  [<ffffffff8117f135>] file_update_time+0xf5/0x170
Nov  2 06:32:35 lisn-mia kernel: [54124.550523]  [<ffffffff8110d9c8>] __generic_file_aio_write+0x1f8/0x440
Nov  2 06:32:35 lisn-mia kernel: [54124.550528]  [<ffffffff8110dc76>] generic_file_aio_write+0x66/0xd0
Nov  2 06:32:35 lisn-mia kernel: [54124.550532]  [<ffffffff811fe439>] ext4_file_write+0x69/0x280
Nov  2 06:32:35 lisn-mia kernel: [54124.550538]  [<ffffffff811555cf>] ? kmem_cache_alloc_trace+0xff/0x120
Nov  2 06:32:35 lisn-mia kernel: [54124.550544]  [<ffffffff811646d2>] do_sync_write+0xd2/0x110
Nov  2 06:32:35 lisn-mia kernel: [54124.550549]  [<ffffffff810d8f45>] ? call_rcu_sched+0x15/0x20
Nov  2 06:32:35 lisn-mia kernel: [54124.550555]  [<ffffffff8108ed5c>] ? __put_cred+0x3c/0x50
Nov  2 06:32:35 lisn-mia kernel: [54124.550562]  [<ffffffff812ae958>] ? apparmor_file_permission+0x18/0x20
Nov  2 06:32:35 lisn-mia kernel: [54124.550568]  [<ffffffff81279c8c>] ? security_file_permission+0x2c/0xb0
Nov  2 06:32:35 lisn-mia kernel: [54124.550572]  [<ffffffff81164b01>] ? rw_verify_area+0x61/0xf0
Nov  2 06:32:35 lisn-mia kernel: [54124.550576]  [<ffffffff81164e46>] vfs_write+0xc6/0x180
Nov  2 06:32:35 lisn-mia kernel: [54124.550579]  [<ffffffff81165161>] sys_write+0x51/0x90
Nov  2 06:32:35 lisn-mia kernel: [54124.550583]  [<ffffffff8100c002>] system_call_fastpath+0x16/0x1b
Nov  2 06:32:35 lisn-mia kernel: [54124.550590] INFO: task miniserv.pl:1553 blocked for more than 120 seconds.
Nov  2 06:32:35 lisn-mia kernel: [54124.550592] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Nov  2 06:32:35 lisn-mia kernel: [54124.550594] miniserv.pl     D 0000000000000001     0  1553      1 0x00000000
Nov  2 06:32:35 lisn-mia kernel: [54124.550598]  ffff880623979a48 0000000000000086 ffff880623979fd8 ffff880623978000
Nov  2 06:32:35 lisn-mia kernel: [54124.550603]  0000000000013d00 ffff8806232d4858 ffff880623979fd8 0000000000013d00
Nov  2 06:32:35 lisn-mia kernel: [54124.550607]  ffff88032375c4a0 ffff8806232d44a0 ffff880623979a38 ffff880623979a98
Nov  2 06:32:35 lisn-mia kernel: [54124.550611] Call Trace:
Nov  2 06:32:35 lisn-mia kernel: [54124.550615]  [<ffffffff81241e85>] do_get_write_access+0x255/0x490
Nov  2 06:32:35 lisn-mia kernel: [54124.550619]  [<ffffffff81087ff0>] ? wake_bit_function+0x0/0x50
Nov  2 06:32:35 lisn-mia kernel: [54124.550624]  [<ffffffff81242201>] jbd2_journal_get_write_access+0x31/0x50
Nov  2 06:32:35 lisn-mia kernel: [54124.550628]  [<ffffffff8122900e>] __ext4_journal_get_write_access+0x3e/0x80
Nov  2 06:32:35 lisn-mia kernel: [54124.550633]  [<ffffffff8120f23b>] ext4_orphan_add+0xbb/0x200
Nov  2 06:32:35 lisn-mia kernel: [54124.550637]  [<ffffffff8120855a>] ext4_setattr+0x39a/0x540
Nov  2 06:32:35 lisn-mia kernel: [54124.550641]  [<ffffffff8117fc99>] notify_change+0x189/0x370
Nov  2 06:32:35 lisn-mia kernel: [54124.550644]  [<ffffffff811fe1a0>] ? ext4_file_open+0x0/0x1d0
Nov  2 06:32:35 lisn-mia kernel: [54124.550648]  [<ffffffff81163131>] do_truncate+0x61/0x90
Nov  2 06:32:35 lisn-mia kernel: [54124.550653]  [<ffffffff811734b5>] finish_open+0x145/0x1b0
Nov  2 06:32:35 lisn-mia kernel: [54124.550657]  [<ffffffff815c337e>] ? _raw_spin_lock+0xe/0x20
Nov  2 06:32:35 lisn-mia kernel: [54124.550660]  [<ffffffff811735a3>] do_last+0x83/0x410
Nov  2 06:32:35 lisn-mia kernel: [54124.550664]  [<ffffffff81173cc2>] do_filp_open+0x392/0x7c0
Nov  2 06:32:35 lisn-mia kernel: [54124.550671]  [<ffffffff812e6c77>] ? __strncpy_from_user+0x27/0x60
Nov  2 06:32:35 lisn-mia kernel: [54124.550676]  [<ffffffff81180f27>] ? alloc_fd+0xf7/0x150
Nov  2 06:32:35 lisn-mia kernel: [54124.550679]  [<ffffffff811642aa>] do_sys_open+0x6a/0x150
Nov  2 06:32:35 lisn-mia kernel: [54124.550683]  [<ffffffff811643b0>] sys_open+0x20/0x30
Nov  2 06:32:35 lisn-mia kernel: [54124.550686]  [<ffffffff8100c002>] system_call_fastpath+0x16/0x1b
Nov  2 06:32:35 lisn-mia kernel: [54124.550691] INFO: task FileManager:1901 blocked for more than 120 seconds.
Nov  2 06:32:35 lisn-mia kernel: [54124.550693] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Nov  2 06:32:35 lisn-mia kernel: [54124.550695] FileManager     D 0000000000000007     0  1901      1 0x00000004
Nov  2 06:32:35 lisn-mia kernel: [54124.550699]  ffff880325953a78 0000000000000082 ffff880325953fd8 ffff880325952000
Nov  2 06:32:35 lisn-mia kernel: [54124.550704]  0000000000013d00 ffff880326705f38 ffff880325953fd8 0000000000013d00
Nov  2 06:32:35 lisn-mia kernel: [54124.550708]  ffff880327145b80 ffff880326705b80 ffff880325953a68 ffff880325953ac8
Nov  2 06:32:35 lisn-mia kernel: [54124.550712] Call Trace:
Nov  2 06:32:35 lisn-mia kernel: [54124.550716]  [<ffffffff81241e85>] do_get_write_access+0x255/0x490
Nov  2 06:32:35 lisn-mia kernel: [54124.550720]  [<ffffffff81087ff0>] ? wake_bit_function+0x0/0x50
Nov  2 06:32:35 lisn-mia kernel: [54124.550724]  [<ffffffff81209fbd>] ? ext4_dirty_inode+0x3d/0x60
Nov  2 06:32:35 lisn-mia kernel: [54124.550728]  [<ffffffff81242201>] jbd2_journal_get_write_access+0x31/0x50
Nov  2 06:32:35 lisn-mia kernel: [54124.550733]  [<ffffffff8122900e>] __ext4_journal_get_write_access+0x3e/0x80
Nov  2 06:32:35 lisn-mia kernel: [54124.550737]  [<ffffffff812053f8>] ext4_reserve_inode_write+0x78/0xa0
Nov  2 06:32:35 lisn-mia kernel: [54124.550741]  [<ffffffff8120546f>] ext4_mark_inode_dirty+0x4f/0x220
Nov  2 06:32:35 lisn-mia kernel: [54124.550744]  [<ffffffff8121dc53>] ? ext4_journal_start_sb+0xb3/0x140
Nov  2 06:32:35 lisn-mia kernel: [54124.550748]  [<ffffffff81209fbd>] ext4_dirty_inode+0x3d/0x60
Nov  2 06:32:35 lisn-mia kernel: [54124.550752]  [<ffffffff8118b39f>] __mark_inode_dirty+0x3f/0x260
Nov  2 06:32:35 lisn-mia kernel: [54124.550756]  [<ffffffff8117d6fb>] touch_atime+0x12b/0x180
Nov  2 06:32:35 lisn-mia kernel: [54124.550760]  [<ffffffff8110d318>] do_generic_file_read.clone.23+0x378/0x450
Nov  2 06:32:35 lisn-mia kernel: [54124.550765]  [<ffffffff8110deaa>] generic_file_aio_read+0x1ca/0x240
Nov  2 06:32:35 lisn-mia kernel: [54124.550769]  [<ffffffff811647e2>] do_sync_read+0xd2/0x110
Nov  2 06:32:35 lisn-mia kernel: [54124.550773]  [<ffffffff81279cf3>] ? security_file_permission+0x93/0xb0
Nov  2 06:32:35 lisn-mia kernel: [54124.550777]  [<ffffffff81164b01>] ? rw_verify_area+0x61/0xf0
Nov  2 06:32:35 lisn-mia kernel: [54124.550781]  [<ffffffff81164fc3>] vfs_read+0xc3/0x180
Nov  2 06:32:35 lisn-mia kernel: [54124.550784]  [<ffffffff811650d1>] sys_read+0x51/0x90
Nov  2 06:32:35 lisn-mia kernel: [54124.550788]  [<ffffffff8100c002>] system_call_fastpath+0x16/0x1b
Nov  2 06:32:35 lisn-mia kernel: [54124.550793] INFO: task collectinfo.pl:3681 blocked for more than 120 seconds.
Nov  2 06:32:35 lisn-mia kernel: [54124.550795] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Nov  2 06:32:35 lisn-mia kernel: [54124.550797] collectinfo.pl  D 000000000000000d     0  3681   3680 0x00000000
Nov  2 06:32:35 lisn-mia kernel: [54124.550801]  ffff8802ea7f79e8 0000000000000086 ffff8802ea7f7fd8 ffff8802ea7f6000
Nov  2 06:32:35 lisn-mia kernel: [54124.550806]  0000000000013d00 ffff8803237c03b8 ffff8802ea7f7fd8 0000000000013d00
Nov  2 06:32:35 lisn-mia kernel: [54124.550810]  ffff8803271e44a0 ffff8803237c0000 ffff8800bf774c30 ffff8800bf4f3d00
Nov  2 06:32:35 lisn-mia kernel: [54124.550814] Call Trace:
Nov  2 06:32:35 lisn-mia kernel: [54124.550818]  [<ffffffff81191e30>] ? sync_buffer+0x0/0x50
Nov  2 06:32:35 lisn-mia kernel: [54124.550822]  [<ffffffff815c1040>] io_schedule+0x70/0xc0
Nov  2 06:32:35 lisn-mia kernel: [54124.550825]  [<ffffffff81191e70>] sync_buffer+0x40/0x50
Nov  2 06:32:35 lisn-mia kernel: [54124.550828]  [<ffffffff815c19bf>] __wait_on_bit+0x5f/0x90
Nov  2 06:32:35 lisn-mia kernel: [54124.550834]  [<ffffffff8119777b>] ? bio_alloc_bioset+0x5b/0xf0
Nov  2 06:32:35 lisn-mia kernel: [54124.550837]  [<ffffffff81191e30>] ? sync_buffer+0x0/0x50
Nov  2 06:32:35 lisn-mia kernel: [54124.550841]  [<ffffffff815c1a6c>] out_of_line_wait_on_bit+0x7c/0x90
Nov  2 06:32:35 lisn-mia kernel: [54124.550845]  [<ffffffff81087ff0>] ? wake_bit_function+0x0/0x50
Nov  2 06:32:35 lisn-mia kernel: [54124.550848]  [<ffffffff81191e2e>] __wait_on_buffer+0x2e/0x30
Nov  2 06:32:35 lisn-mia kernel: [54124.550852]  [<ffffffff8120c5b8>] ext4_find_entry+0x388/0x490
Nov  2 06:32:35 lisn-mia kernel: [54124.550855]  [<ffffffff8117f207>] ? ifind_fast+0x57/0xa0
Nov  2 06:32:35 lisn-mia kernel: [54124.550859]  [<ffffffff815c337e>] ? _raw_spin_lock+0xe/0x20
Nov  2 06:32:35 lisn-mia kernel: [54124.550863]  [<ffffffff81179059>] ? _d_rehash+0x49/0x50
Nov  2 06:32:35 lisn-mia kernel: [54124.550866]  [<ffffffff81179545>] ? d_rehash+0x35/0x50
Nov  2 06:32:35 lisn-mia kernel: [54124.550870]  [<ffffffff8120c70d>] ext4_lookup+0x4d/0x130
Nov  2 06:32:35 lisn-mia kernel: [54124.550874]  [<ffffffff8116f155>] d_alloc_and_lookup+0x45/0x90
Nov  2 06:32:35 lisn-mia kernel: [54124.550878]  [<ffffffff8117c675>] ? d_lookup+0x35/0x60
Nov  2 06:32:35 lisn-mia kernel: [54124.550881]  [<ffffffff81171562>] do_lookup+0x182/0x2e0
Nov  2 06:32:35 lisn-mia kernel: [54124.550885]  [<ffffffff815c337e>] ? _raw_spin_lock+0xe/0x20
Nov  2 06:32:35 lisn-mia kernel: [54124.550888]  [<ffffffff81171d16>] link_path_walk+0x656/0xc40
Nov  2 06:32:35 lisn-mia kernel: [54124.550893]  [<ffffffff811725fb>] do_path_lookup+0x5b/0x160
Nov  2 06:32:35 lisn-mia kernel: [54124.550896]  [<ffffffff81173a6c>] do_filp_open+0x13c/0x7c0
Nov  2 06:32:35 lisn-mia kernel: [54124.550901]  [<ffffffff812e6c77>] ? __strncpy_from_user+0x27/0x60
Nov  2 06:32:35 lisn-mia kernel: [54124.550905]  [<ffffffff81180f27>] ? alloc_fd+0xf7/0x150
Nov  2 06:32:35 lisn-mia kernel: [54124.550908]  [<ffffffff811642aa>] do_sys_open+0x6a/0x150
Nov  2 06:32:35 lisn-mia kernel: [54124.550912]  [<ffffffff811643b0>] sys_open+0x20/0x30
Nov  2 06:32:35 lisn-mia kernel: [54124.550915]  [<ffffffff8100c002>] system_call_fastpath+0x16/0x1b
Nov  2 06:32:35 lisn-mia kernel: [54124.550919] INFO: task miniserv.pl:3727 blocked for more than 120 seconds.
Nov  2 06:32:35 lisn-mia kernel: [54124.550921] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Nov  2 06:32:35 lisn-mia kernel: [54124.550923] miniserv.pl     D 0000000000000013     0  3727   1553 0x00000000
Nov  2 06:32:35 lisn-mia kernel: [54124.550927]  ffff88028686fad8 0000000000000082 ffff88028686ffd8 ffff88028686e000
Nov  2 06:32:35 lisn-mia kernel: [54124.550932]  0000000000013d00 ffff88031cce1a98 ffff88028686ffd8 0000000000013d00
Nov  2 06:32:35 lisn-mia kernel: [54124.550936]  ffff880327292dc0 ffff88031cce16e0 ffff88028686fac8 ffff88028686fb28
Nov  2 06:32:35 lisn-mia kernel: [54124.550940] Call Trace:
Nov  2 06:32:35 lisn-mia kernel: [54124.550944]  [<ffffffff81241e85>] do_get_write_access+0x255/0x490
Nov  2 06:32:35 lisn-mia kernel: [54124.550948]  [<ffffffff81087ff0>] ? wake_bit_function+0x0/0x50
Nov  2 06:32:35 lisn-mia kernel: [54124.550952]  [<ffffffff811933d7>] ? __find_get_block+0x87/0xe0
Nov  2 06:32:35 lisn-mia kernel: [54124.550956]  [<ffffffff81242201>] jbd2_journal_get_write_access+0x31/0x50
Nov  2 06:32:35 lisn-mia kernel: [54124.550961]  [<ffffffff8122900e>] __ext4_journal_get_write_access+0x3e/0x80
Nov  2 06:32:35 lisn-mia kernel: [54124.550964]  [<ffffffff812006d3>] ext4_new_inode+0x5c3/0xbe0
Nov  2 06:32:35 lisn-mia kernel: [54124.550968]  [<ffffffff812408ca>] ? jbd2__journal_start+0xca/0x110
Nov  2 06:32:35 lisn-mia kernel: [54124.550973]  [<ffffffff8121dc53>] ? ext4_journal_start_sb+0xb3/0x140
Nov  2 06:32:35 lisn-mia kernel: [54124.550977]  [<ffffffff8120e657>] ext4_create+0xb7/0x140
Nov  2 06:32:35 lisn-mia kernel: [54124.550980]  [<ffffffff8116ef83>] ? generic_permission+0x23/0xc0
Nov  2 06:32:35 lisn-mia kernel: [54124.550984]  [<ffffffff81173191>] vfs_create+0xb1/0x110
Nov  2 06:32:35 lisn-mia kernel: [54124.550988]  [<ffffffff81173866>] do_last+0x346/0x410
Nov  2 06:32:35 lisn-mia kernel: [54124.550991]  [<ffffffff81173cc2>] do_filp_open+0x392/0x7c0
Nov  2 06:32:35 lisn-mia kernel: [54124.550996]  [<ffffffff812e6c77>] ? __strncpy_from_user+0x27/0x60
Nov  2 06:32:35 lisn-mia kernel: [54124.551000]  [<ffffffff81180f27>] ? alloc_fd+0xf7/0x150
Nov  2 06:32:35 lisn-mia kernel: [54124.551003]  [<ffffffff811642aa>] do_sys_open+0x6a/0x150
Nov  2 06:32:35 lisn-mia kernel: [54124.551007]  [<ffffffff811643b0>] sys_open+0x20/0x30
Nov  2 06:32:35 lisn-mia kernel: [54124.551010]  [<ffffffff8100c002>] system_call_fastpath+0x16/0x1b
Nov  2 06:32:35 lisn-mia kernel: [54124.551013] INFO: task cron:3728 blocked for more than 120 seconds.
Nov  2 06:32:35 lisn-mia kernel: [54124.551015] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Nov  2 06:32:35 lisn-mia kernel: [54124.551018] cron            D 000000000000000d     0  3728    986 0x00000000
Nov  2 06:32:35 lisn-mia kernel: [54124.551022]  ffff880626b9dad8 0000000000000086 ffff880626b9dfd8 ffff880626b9c000
Nov  2 06:32:35 lisn-mia kernel: [54124.551026]  0000000000013d00 ffff88062517b178 ffff880626b9dfd8 0000000000013d00
Nov  2 06:32:35 lisn-mia kernel: [54124.551030]  ffff8803271e44a0 ffff88062517adc0 ffff880626b9dac8 ffff880626b9db28
Nov  2 06:32:35 lisn-mia kernel: [54124.551034] Call Trace:
Nov  2 06:32:35 lisn-mia kernel: [54124.551039]  [<ffffffff81241e85>] do_get_write_access+0x255/0x490
Nov  2 06:32:35 lisn-mia kernel: [54124.551042]  [<ffffffff81087ff0>] ? wake_bit_function+0x0/0x50
Nov  2 06:32:35 lisn-mia kernel: [54124.551046]  [<ffffffff811933d7>] ? __find_get_block+0x87/0xe0
Nov  2 06:32:35 lisn-mia kernel: [54124.551050]  [<ffffffff81242201>] jbd2_journal_get_write_access+0x31/0x50
Nov  2 06:32:35 lisn-mia kernel: [54124.551055]  [<ffffffff8122900e>] __ext4_journal_get_write_access+0x3e/0x80
Nov  2 06:32:35 lisn-mia kernel: [54124.551058]  [<ffffffff812006d3>] ext4_new_inode+0x5c3/0xbe0
Nov  2 06:32:35 lisn-mia kernel: [54124.551062]  [<ffffffff812408ca>] ? jbd2__journal_start+0xca/0x110
Nov  2 06:32:35 lisn-mia kernel: [54124.551066]  [<ffffffff8121dc53>] ? ext4_journal_start_sb+0xb3/0x140
Nov  2 06:32:35 lisn-mia kernel: [54124.551070]  [<ffffffff8120e657>] ext4_create+0xb7/0x140
Nov  2 06:32:35 lisn-mia kernel: [54124.551074]  [<ffffffff8116ef83>] ? generic_permission+0x23/0xc0
Nov  2 06:32:35 lisn-mia kernel: [54124.551077]  [<ffffffff81173191>] vfs_create+0xb1/0x110
Nov  2 06:32:35 lisn-mia kernel: [54124.551081]  [<ffffffff81173866>] do_last+0x346/0x410
Nov  2 06:32:35 lisn-mia kernel: [54124.551085]  [<ffffffff81173cc2>] do_filp_open+0x392/0x7c0
Nov  2 06:32:35 lisn-mia kernel: [54124.551089]  [<ffffffff812e6c77>] ? __strncpy_from_user+0x27/0x60
Nov  2 06:32:35 lisn-mia kernel: [54124.551093]  [<ffffffff81180f27>] ? alloc_fd+0xf7/0x150
Nov  2 06:32:35 lisn-mia kernel: [54124.551097]  [<ffffffff811642aa>] do_sys_open+0x6a/0x150
Nov  2 06:32:35 lisn-mia kernel: [54124.551100]  [<ffffffff811643b0>] sys_open+0x20/0x30
Nov  2 06:32:35 lisn-mia kernel: [54124.551104]  [<ffffffff8100c002>] system_call_fastpath+0x16/0x1b
Nov  2 06:32:35 lisn-mia kernel: [54124.551107] INFO: task dhclient-script:3730 blocked for more than 120 seconds.
Nov  2 06:32:35 lisn-mia kernel: [54124.551109] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Nov  2 06:32:35 lisn-mia kernel: [54124.551111] dhclient-script D 0000000000000001     0  3730   1361 0x00000000
Nov  2 06:32:35 lisn-mia kernel: [54124.551115]  ffff880323e15ad8 0000000000000086 ffff880323e15fd8 ffff880323e14000
Nov  2 06:32:35 lisn-mia kernel: [54124.551120]  0000000000013d00 ffff880323da5f38 ffff880323e15fd8 0000000000013d00
Nov  2 06:32:35 lisn-mia kernel: [54124.551124]  ffff8803270d8000 ffff880323da5b80 ffff880323e15ac8 ffff880323e15b28
Nov  2 06:32:35 lisn-mia kernel: [54124.551128] Call Trace:
Nov  2 06:32:35 lisn-mia kernel: [54124.551132]  [<ffffffff81241e85>] do_get_write_access+0x255/0x490
Nov  2 06:32:35 lisn-mia kernel: [54124.551136]  [<ffffffff81087ff0>] ? wake_bit_function+0x0/0x50
Nov  2 06:32:35 lisn-mia kernel: [54124.551140]  [<ffffffff811933d7>] ? __find_get_block+0x87/0xe0
Nov  2 06:32:35 lisn-mia kernel: [54124.551144]  [<ffffffff81242201>] jbd2_journal_get_write_access+0x31/0x50
Nov  2 06:32:35 lisn-mia kernel: [54124.551149]  [<ffffffff8122900e>] __ext4_journal_get_write_access+0x3e/0x80
Nov  2 06:32:35 lisn-mia kernel: [54124.551152]  [<ffffffff812006d3>] ext4_new_inode+0x5c3/0xbe0
Nov  2 06:32:35 lisn-mia kernel: [54124.551156]  [<ffffffff812408ca>] ? jbd2__journal_start+0xca/0x110
Nov  2 06:32:35 lisn-mia kernel: [54124.551160]  [<ffffffff8121dc53>] ? ext4_journal_start_sb+0xb3/0x140
Nov  2 06:32:35 lisn-mia kernel: [54124.551164]  [<ffffffff8120e657>] ext4_create+0xb7/0x140
Nov  2 06:32:35 lisn-mia kernel: [54124.551168]  [<ffffffff8116ef83>] ? generic_permission+0x23/0xc0
Nov  2 06:32:35 lisn-mia kernel: [54124.551172]  [<ffffffff81173191>] vfs_create+0xb1/0x110
Nov  2 06:32:35 lisn-mia kernel: [54124.551175]  [<ffffffff81173866>] do_last+0x346/0x410
Nov  2 06:32:35 lisn-mia kernel: [54124.551179]  [<ffffffff81173cc2>] do_filp_open+0x392/0x7c0
Nov  2 06:32:35 lisn-mia kernel: [54124.551184]  [<ffffffff812e6c77>] ? __strncpy_from_user+0x27/0x60
Nov  2 06:32:35 lisn-mia kernel: [54124.551187]  [<ffffffff81180f27>] ? alloc_fd+0xf7/0x150
Nov  2 06:32:35 lisn-mia kernel: [54124.551191]  [<ffffffff811642aa>] do_sys_open+0x6a/0x150
Nov  2 06:32:35 lisn-mia kernel: [54124.551195]  [<ffffffff811643b0>] sys_open+0x20/0x30
Nov  2 06:32:35 lisn-mia kernel: [54124.551198]  [<ffffffff8100c002>] system_call_fastpath+0x16/0x1b
Nov  2 06:32:35 lisn-mia kernel: [54244.550068] INFO: task jbd2/sda2-8:349 blocked for more than 120 seconds.
Nov  2 06:32:35 lisn-mia kernel: [54244.550072] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Nov  2 06:32:35 lisn-mia kernel: [54244.550076] jbd2/sda2-8     D 0000000000000010     0   349      2 0x00000000
Nov  2 06:32:35 lisn-mia kernel: [54244.550081]  ffff8803241f9af0 0000000000000046 ffff8803241f9fd8 ffff8803241f8000
Nov  2 06:32:35 lisn-mia kernel: [54244.550086]  0000000000013d00 ffff880323ee4858 ffff8803241f9fd8 0000000000013d00
Nov  2 06:32:35 lisn-mia kernel: [54244.550090]  ffff880323518000 ffff880323ee44a0 ffff88063ffe4868 ffff8800bf553d00
Nov  2 06:32:35 lisn-mia kernel: [54244.550095] Call Trace:
Nov  2 06:32:35 lisn-mia kernel: [54244.550101]  [<ffffffff8110c110>] ? sync_page+0x0/0x50
Nov  2 06:32:35 lisn-mia kernel: [54244.550106]  [<ffffffff815c1040>] io_schedule+0x70/0xc0
Nov  2 06:32:35 lisn-mia kernel: [54244.550110]  [<ffffffff8110c150>] sync_page+0x40/0x50
Nov  2 06:32:35 lisn-mia kernel: [54244.550114]  [<ffffffff815c19bf>] __wait_on_bit+0x5f/0x90
Nov  2 06:32:35 lisn-mia kernel: [54244.550121]  [<ffffffff8110c318>] wait_on_page_bit+0x78/0x80
Nov  2 06:32:35 lisn-mia kernel: [54244.550125]  [<ffffffff81087ff0>] ? wake_bit_function+0x0/0x50
Nov  2 06:32:35 lisn-mia kernel: [54244.550129]  [<ffffffff8110c4bd>] filemap_fdatawait_range+0xfd/0x190
Nov  2 06:32:35 lisn-mia kernel: [54244.550132]  [<ffffffff8110e7c5>] ? mempool_alloc_slab+0x15/0x20
Nov  2 06:32:35 lisn-mia kernel: [54244.550135]  [<ffffffff8110eb09>] ? mempool_alloc+0x59/0x140
Nov  2 06:32:35 lisn-mia kernel: [54244.550138]  [<ffffffff8110c57b>] filemap_fdatawait+0x2b/0x30
Nov  2 06:32:35 lisn-mia kernel: [54244.550142]  [<ffffffff81242b53>] journal_finish_inode_data_buffers+0x63/0x170
Nov  2 06:32:35 lisn-mia kernel: [54244.550145]  [<ffffffff81243344>] jbd2_journal_commit_transaction+0x6e4/0x1190
Nov  2 06:32:35 lisn-mia kernel: [54244.550150]  [<ffffffff810761d5>] ? try_to_del_timer_sync+0x85/0xe0
Nov  2 06:32:35 lisn-mia kernel: [54244.550154]  [<ffffffff81247f5b>] kjournald2+0xbb/0x220
Nov  2 06:32:35 lisn-mia kernel: [54244.550157]  [<ffffffff81087fb0>] ? autoremove_wake_function+0x0/0x40
Nov  2 06:32:35 lisn-mia kernel: [54244.550160]  [<ffffffff81247ea0>] ? kjournald2+0x0/0x220
Nov  2 06:32:35 lisn-mia kernel: [54244.550163]  [<ffffffff81087866>] kthread+0x96/0xa0
Nov  2 06:32:35 lisn-mia kernel: [54244.550167]  [<ffffffff8100ce24>] kernel_thread_helper+0x4/0x10
Nov  2 06:32:35 lisn-mia kernel: [54244.550170]  [<ffffffff810877d0>] ? kthread+0x0/0xa0
Nov  2 06:32:35 lisn-mia kernel: [54244.550173]  [<ffffffff8100ce20>] ? kernel_thread_helper+0x0/0x10

```

---

### Post by faroutliving on 2012-11-03
No one? Am I posting to the wrong place?

My own research indicates this might be some kind of kernel bug when flushing cache to disk. Does anyone have any solid leads on this, or way to know if that is what I am looking at here?

Thanks,
Deron

---

### Post by 2F4U on 2012-11-04
My quick research revealed this bug report:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=595927](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=595927)

Initially, it was thought that it is only a problem in dpkg, but later it seems to be confirmed to be a kernel problem with writeback.

---

### Post by faroutliving on 2012-11-07
Thanks for the pointer. I'm not 100% sure they are talking about the same thing, but the easy solutions didn't work for me so I am trying to remotely upgrade the server to 12.04 (got it to 11.10 but now dns doesn't resolve..., soon as that gets resolved I'll update to 12.04 at least).

Anyway, when I get updated I'll try some stress tests and see if it fixed the problem...

---

