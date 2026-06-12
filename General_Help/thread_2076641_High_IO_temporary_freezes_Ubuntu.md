---
title: "High IO temporary freezes Ubuntu"
date: 2012-10-26
forum: General Help
---

### Post by private54321 on 2012-10-26
I have this two processes which when appear every minute or so use up 99% of the
io in HDD when im doing activities.

jbd2/sda1-8
flush-8:0

[IMG]http://i.imgur.com/DZ1Wi.png[/IMG]

[IMG]http://i.imgur.com/5yGuQ.png[/IMG]

When they appear everything in my screen freezes, i can't move nothing, it usually goes away in 10 seconds and continues appearing when i'm using the os. (installing stuff, browsing, downloading, etc)

What's going on? This is a fresh 12.04 installation.

---

### Post by funicorn on 2012-10-26
should be a kernel thing. You should check errors in kern.log

---

### Post by private54321 on 2012-10-27
> **funicorn said:**
> should be a kernel thing. You should check errors in kern.log

im new to ubuntu.

here's what my kernel.log contains.

pastebin link as it's too long to paste here.

[http://pastebin.com/jXk3K5LN](http://pastebin.com/jXk3K5LN)

can someone tell me what's wrong

---

### Post by private54321 on 2012-10-27
bump up my post.

---

### Post by funicorn on 2012-10-27
I see something there. Google the issue on 'task ext4lazyinit blocked'
> 
Oct 24 22:04:26 i2071 kernel: [   87.592753]  xfce4-settings-[1428]: segfault at 1 ip 00007f3c698b7ff8 sp  00007fffb8430f30 error 4 in xfce4-settings-helper[7f3c698ae000+10000]
[COLOR=Red] Oct 26 00:43:06 i2071 kernel: [95949.205732] INFO: task ext4lazyinit:522 blocked for more than 120 seconds.[/COLOR]
Oct 26 00:43:06 i2071 kernel: [95949.205737] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Oct 26 00:43:06 i2071 kernel: [95949.205740] ext4lazyinit    D ffffffff81806240     0   522      2 0x00000000
Oct 26 00:43:06 i2071 kernel: [95949.205746]  ffff8808081a9c60 0000000000000046 0000000000000000 0000000000000000
Oct 26 00:43:06 i2071 kernel: [95949.205752]  ffff8808081a9fd8 ffff8808081a9fd8 ffff8808081a9fd8 0000000000013780
Oct 26 00:43:06 i2071 kernel: [95949.205757]  ffff88080bde16f0 ffff8808077016f0 ffff8808081a9c70 ffff8808081a9cd0
Oct 26 00:43:06 i2071 kernel: [95949.205762] Call Trace:
Oct 26 00:43:06 i2071 kernel: [95949.205770]  [<ffffffff8165a55f>] schedule+0x3f/0x60
Oct 26 00:43:06 i2071 kernel: [95949.205777]  [<ffffffff8125f53d>] do_get_write_access+0x27d/0x4f0
Oct 26 00:43:06 i2071 kernel: [95949.205783]  [<ffffffff811642fd>] ? kmem_cache_alloc+0x11d/0x140
Oct 26 00:43:06 i2071 kernel: [95949.205788]  [<ffffffff8108af00>] ? autoremove_wake_function+0x40/0x40
Oct 26 00:43:06 i2071 kernel: [95949.205794]  [<ffffffff8125f8f0>] jbd2_journal_get_write_access+0x30/0x50
Oct 26 00:43:06 i2071 kernel: [95949.205799]  [<ffffffff8124187e>] __ext4_journal_get_write_access+0x3e/0x80
Oct 26 00:43:06 i2071 kernel: [95949.205804]  [<ffffffff81213628>] ext4_init_inode_table+0x118/0x370
Oct 26 00:43:06 i2071 kernel: [95949.205808]  [<ffffffff8165aa75>] ? schedule_timeout+0x175/0x320
Oct 26 00:43:06 i2071 kernel: [95949.205812]  [<ffffffff81226f65>] ext4_run_li_request+0x85/0xe0
Oct 26 00:43:06 i2071 kernel: [95949.205816]  [<ffffffff8122705c>] ext4_lazyinit_thread+0x9c/0x1c0
Oct 26 00:43:06 i2071 kernel: [95949.205820]  [<ffffffff81226fc0>] ? ext4_run_li_request+0xe0/0xe0
Oct 26 00:43:06 i2071 kernel: [95949.205823]  [<ffffffff8108a42c>] kthread+0x8c/0xa0
Oct 26 00:43:06 i2071 kernel: [95949.205828]  [<ffffffff81666bf4>] kernel_thread_helper+0x4/0x10
Oct 26 00:43:06 i2071 kernel: [95949.205832]  [<ffffffff8108a3a0>] ? flush_kthread_worker+0xa0/0xa0
Oct 26 00:43:06 i2071 kernel: [95949.205836]  [<ffffffff81666bf0>] ? gs_change+0x13/0x13
Oct 26 00:43:06 i2071 kernel: [95949.205853] INFO: task firefox:7418 blocked for more than 120 seconds.
Oct 26 00:43:06 i2071 kernel: [95949.205855] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Oct 26 00:43:06 i2071 kernel: [95949.205857] firefox         D ffffffff81806240     0  7418   1415 0x00000000
Oct 26 00:43:06 i2071 kernel: [95949.205862]  ffff8807fb21de48 0000000000000082 ffff8807fb21de28 0000000300000001
Oct 26 00:43:06 i2071 kernel: [95949.205867]  ffff8807fb21dfd8 ffff8807fb21dfd8 ffff8807fb21dfd8 0000000000013780
Oct 26 00:43:06 i2071 kernel: [95949.205872]  ffff88080bde16f0 ffff880807700000 ffff8807fb21de58 ffff880807f99000
Oct 26 00:43:06 i2071 kernel: [95949.205876] Call Trace:
Oct 26 00:43:06 i2071 kernel: [95949.205880]  [<ffffffff8165a55f>] schedule+0x3f/0x60
Oct 26 00:43:06 i2071 kernel: [95949.205884]  [<ffffffff81265085>] jbd2_log_wait_commit+0xb5/0x130
Oct 26 00:43:06 i2071 kernel: [95949.205888]  [<ffffffff8108aec0>] ? add_wait_queue+0x60/0x60
Oct 26 00:43:06 i2071 kernel: [95949.205891]  [<ffffffff812111b8>] ext4_sync_file+0x208/0x2d0
Oct 26 00:43:06 i2071 kernel: [95949.205896]  [<ffffffff81177c90>] ? vfs_write+0x110/0x180
Oct 26 00:43:06 i2071 kernel: [95949.205901]  [<ffffffff811a6406>] do_fsync+0x56/0x80
Oct 26 00:43:06 i2071 kernel: [95949.205906]  [<ffffffff811a6730>] sys_fsync+0x10/0x20
Oct 26 00:43:06 i2071 kernel: [95949.205910]  [<ffffffff81664a82>] system_call_fastpath+0x16/0x1b



---

