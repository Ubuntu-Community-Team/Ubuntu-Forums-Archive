---
title: "Problem recognizing memory with varnish"
date: 2015-05-02
forum: General Help
---

### Post by bachhaduy on 2015-05-02
First thanks for your time and comments :)

I have a problem with a varnish server. Some of the information from varnish is not going right, so I am a bit worried.

I have configured varnish to spend 5TB for caching using file, but varnish is recognizing wrong:

SMF.s0.g_bytes 2196952567808 . Bytes outstanding 
SMF.s0.g_space 62561628229632 . Bytes available

Which is in total 62 TB.

When I show from another command and check, the used space is freezed at about 1.3TB

/dev/mapper/cache-cache 6730009920 1377209736 5010935328 22% /cache

And here is the log:

Apr 30 12:05:42 hn-edge3 kernel: lowmem_reserve[]: 0 0 0 0 
Apr 30 12:05:42 hn-edge3 kernel: Node 0 DMA: 1*4kB 1*8kB 1*16kB 1*32kB 2*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 1*2048kB 3*4096kB = 15676kB 
Apr 30 12:05:42 hn-edge3 kernel: Node 0 DMA32: 6803*4kB 3704*8kB 542*16kB 163*32kB 53*64kB 6*128kB 1*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 75148kB 
Apr 30 12:05:42 hn-edge3 kernel: Node 0 Normal: 8410*4kB 645*8kB 575*16kB 55*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 49760kB 
Apr 30 12:05:42 hn-edge3 kernel: Node 1 Normal: 19248*4kB 3408*8kB 827*16kB 230*32kB 5*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 125168kB 
Apr 30 12:05:42 hn-edge3 kernel: 7529544 total pagecache pages 
Apr 30 12:05:42 hn-edge3 kernel: 20743 pages in swap cache 
Apr 30 12:05:42 hn-edge3 kernel: Swap cache stats: add 187508698, delete 187487955, find 45571328/71259675 
Apr 30 12:05:42 hn-edge3 kernel: Free swap = 974404kB 
Apr 30 12:05:42 hn-edge3 kernel: Total swap = 2097144kB 
Apr 30 12:05:42 hn-edge3 kernel: 8388592 pages RAM 
Apr 30 12:05:42 hn-edge3 kernel: 176808 pages reserved 
Apr 30 12:05:42 hn-edge3 kernel: 15851674 pages shared 
Apr 30 12:05:42 hn-edge3 kernel: 606626 pages non-shared 
Apr 30 14:29:01 hn-edge3 kernel: varnishd: page allocation failure. order:6, mode:0xd0 
Apr 30 14:29:01 hn-edge3 kernel: Pid: 11831, comm: varnishd Not tainted 2.6.32-431.el6.x86_64 #1 
Apr 30 14:29:01 hn-edge3 kernel: Call Trace: 
Apr 30 14:29:01 hn-edge3 kernel: [<ffffffff8112f9e7>] ? __alloc_pages_nodemask+0x757/0x8d0 
Apr 30 14:29:01 hn-edge3 kernel: [<ffffffff8116e482>] ? kmem_getpages+0x62/0x170 
Apr 30 14:29:01 hn-edge3 kernel: [<ffffffff8116f09a>] ? fallback_alloc+0x1ba/0x270 
Apr 30 14:29:01 hn-edge3 kernel: [<ffffffff8116eaef>] ? cache_grow+0x2cf/0x320 
Apr 30 14:29:01 hn-edge3 kernel: [<ffffffff8116ee19>] ? ____cache_alloc_node+0x99/0x160 
Apr 30 14:29:01 hn-edge3 kernel: [<ffffffff8142d4e5>] ? dma_pin_iovec_pages+0xb5/0x230 
Apr 30 14:29:01 hn-edge3 kernel: [<ffffffff8116fbe9>] ? __kmalloc+0x189/0x220 
Apr 30 14:29:01 hn-edge3 kernel: [<ffffffff8142d4e5>] ? dma_pin_iovec_pages+0xb5/0x230 
Apr 30 14:29:01 hn-edge3 kernel: [<ffffffff8144b38c>] ? lock_sock_nested+0xac/0xc0 
Apr 30 14:29:01 hn-edge3 kernel: [<ffffffff814a442a>] ? tcp_recvmsg+0x4ca/0xe80 
Apr 30 14:29:01 hn-edge3 kernel: [<ffffffff814c58ca>] ? inet_recvmsg+0x5a/0x90 
Apr 30 14:29:01 hn-edge3 kernel: [<ffffffff81446b91>] ? sock_aio_read+0x1a1/0x1b0 
Apr 30 14:29:01 hn-edge3 kernel: [<ffffffff81188dba>] ? do_sync_read+0xfa/0x140 
Apr 30 14:29:01 hn-edge3 kernel: [<ffffffff8109b2a0>] ? autoremove_wake_function+0x0/0x40 
Apr 30 14:29:01 hn-edge3 kernel: [<ffffffff8152a4eb>] ? _spin_unlock_bh+0x1b/0x20 
Apr 30 14:29:01 hn-edge3 kernel: [<ffffffff812263c6>] ? security_file_permission+0x16/0x20 
Apr 30 14:29:01 hn-edge3 kernel: [<ffffffff81189771>] ? vfs_read+0x181/0x1a0 
Apr 30 14:29:01 hn-edge3 kernel: [<ffffffff811897e1>] ? sys_read+0x51/0x90

I'm thinking that there's a problem with reserving RAM for varnish.

VARNISH_STORAGE_SIZE=99%
VARNISH_TTL=120

However I really cannot understand why varnish read the memory space wrong (62TB).

Any help is appreciated

---

