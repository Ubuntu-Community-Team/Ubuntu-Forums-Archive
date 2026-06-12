---
title: "Asus UX305FA crashes 2-4 times per day"
date: 2017-04-10
forum: General Help
---

### Post by guttersnipe on 2017-04-10
Hello, ever since I bought an Asus UX305FA, I've had the following issue a few times per day, when I have a lot of programs open:

 1. 4x processor cores spike, but not to 100%
 2. the mouse begins to move *very* slow and *extremely* delayed
 3. audio begins to break up
 4. then, after tens of seconds, audio stops, and the computer becomes entirely unresponsive, requiring a hard-reset.

Notes about evasive maneuvers:
 * sometimes the crash is worse than others, and I can hop into a virtual terminal, log-in, and run top. Some of these times, I've seen kswapd at the top of my cpu usage list
 * I've re-enabled the ctrl-alt-backspace shortcut to kill the desktop environment. Sometimes, if I do this early enough, the computer completely recovers as the misbehaving program is killed with the desktop environment
 * Sometimes, after a few minutes, the kernel kills VirtualBox or Firefox, and the crash stops entirely. This is annoying, but much preferred to a hard-reset.

This crash tends to happen when I am using applications with a lot of memory. I'm a bit of a memory power user: I frequently have 4-10 firefox windows with 10-20 tabs open each--one of which is streaming video, as well as virtualbox running another version of ubuntu.

Hardware Specs:

 * Asus UX305FA Ultrabook/Laptop
 * 8 G RAM
 * Intel Core M-5Y10 CPU

Software Specs:

 * 1 GB cryptswap
 * Xubuntu 16.04
 * Linux xyz 4.4.0-71-generic #92-Ubuntu SMP Fri Mar 24 12:59:01 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
 * Firefox 52.0.2 (64-bit)
 * Oracle VirtualBox v5.1.14 r112924 (Qt5.5.1)

This issue has been occurring for the past 5 months. Nearly every day this computer crashes; it's extremely frustrating.

What I've done so far (unsuccessfully): 

 * Verified that the memory is OK with memtest86
 * Upgraded kernels and many various packages
 * Installed latest intel graphics drivers with intel-graphics-update-tool
 * tried using the "drm-intel-next" mainline build of the kernel with Direct Rendering Manager support, but I couldn't install the virtualbox module with it, so I had to revert.

Here's some settings I've added to my /etc/sysctl.conf, which have helped reduce the number of outright crashes (instead the kernel OOMs and kills an app to save itself rather than just totally locking up):

[INDENT]vm.swappiness = 0
vm.vfs_cache_pressure = 0
vm.min_free_kbytes = 0[/INDENT]

Below is an example of all the logs that came to /var/log/syslog when it locked up earlier today. I delayed hard-reset a few minutes after the system became completely unresponsive, which was a few minutes after the last log entry, but it must have locked up to the point that it couldn't write anymore. Can someone please explain to me what this log file is indicating happened? Are there any other log files I can pull-up to learn more about what causes this issue? TIA!

```
Apr 10 12:32:09 anderson kernel: [16697.153009] firefox: page allocation failure: order:0, mode:0x2284020
Apr 10 12:32:09 anderson kernel: [16697.153020] CPU: 0 PID: 4348 Comm: firefox Tainted: G           OE   4.4.0-71-generic #92-Ubuntu
Apr 10 12:32:09 anderson kernel: [16697.153024] Hardware name: ASUSTeK COMPUTER INC. UX305FA/UX305FA, BIOS UX305FA.206 12/16/2014
Apr 10 12:32:09 anderson kernel: [16697.153028]  0000000000000086 000000002f9c34e3 ffff8801ba1e7680 ffffffff813f82b3
Apr 10 12:32:09 anderson kernel: [16697.153036]  0000000002284020 0000000000000000 ffff8801ba1e7710 ffffffff81194b8a
Apr 10 12:32:09 anderson kernel: [16697.153042]  ffff88021eff8500 ffff88021eff96f0 0000000000000000 ffff880100000030
Apr 10 12:32:09 anderson kernel: [16697.153047] Call Trace:
Apr 10 12:32:09 anderson kernel: [16697.153060]  [<ffffffff813f82b3>] dump_stack+0x63/0x90
Apr 10 12:32:09 anderson kernel: [16697.153068]  [<ffffffff81194b8a>] warn_alloc_failed+0xfa/0x150
Apr 10 12:32:09 anderson kernel: [16697.153075]  [<ffffffff811a40c2>] ? move_active_pages_to_lru+0x102/0x210
Apr 10 12:32:09 anderson kernel: [16697.153082]  [<ffffffff81198832>] __alloc_pages_slowpath.constprop.88+0x492/0xad0
Apr 10 12:32:09 anderson kernel: [16697.153089]  [<ffffffff811990f6>] __alloc_pages_nodemask+0x286/0x2a0
Apr 10 12:32:09 anderson kernel: [16697.153097]  [<ffffffff811e2b8c>] alloc_pages_current+0x8c/0x110
Apr 10 12:32:09 anderson kernel: [16697.153103]  [<ffffffff811ebc7f>] new_slab+0x28f/0x490
Apr 10 12:32:09 anderson kernel: [16697.153109]  [<ffffffff811ecccb>] ___slab_alloc+0x22b/0x470
Apr 10 12:32:09 anderson kernel: [16697.153118]  [<ffffffff815b6bad>] ? scsi_host_alloc_command+0x2d/0xc0
Apr 10 12:32:09 anderson kernel: [16697.153124]  [<ffffffff81037eb9>] ? sched_clock+0x9/0x10
Apr 10 12:32:09 anderson kernel: [16697.153132]  [<ffffffff813c7b48>] ? get_request+0x2e8/0x790
Apr 10 12:32:09 anderson kernel: [16697.153138]  [<ffffffff815b6bad>] ? scsi_host_alloc_command+0x2d/0xc0
Apr 10 12:32:09 anderson kernel: [16697.153144]  [<ffffffff811ecf30>] __slab_alloc+0x20/0x40
Apr 10 12:32:09 anderson kernel: [16697.153149]  [<ffffffff811ed4af>] kmem_cache_alloc+0x19f/0x1f0
Apr 10 12:32:09 anderson kernel: [16697.153157]  [<ffffffff815b6bad>] scsi_host_alloc_command+0x2d/0xc0
Apr 10 12:32:09 anderson kernel: [16697.153166]  [<ffffffff815b7cc0>] scsi_get_command+0x20/0x170
Apr 10 12:32:09 anderson kernel: [16697.153174]  [<ffffffff815bf79b>] scsi_prep_fn+0x15b/0x170
Apr 10 12:32:09 anderson kernel: [16697.153183]  [<ffffffff813c9dc8>] blk_peek_request+0x168/0x290
Apr 10 12:32:09 anderson kernel: [16697.153192]  [<ffffffff815c0ede>] scsi_request_fn+0x3e/0x610
Apr 10 12:32:09 anderson kernel: [16697.153204]  [<ffffffff813c3eb3>] __blk_run_queue+0x33/0x40
Apr 10 12:32:09 anderson kernel: [16697.153213]  [<ffffffff813c417a>] queue_unplugged+0x2a/0xb0
Apr 10 12:32:09 anderson kernel: [16697.153221]  [<ffffffff813ca1e6>] blk_flush_plug_list+0x1d6/0x240
Apr 10 12:32:09 anderson kernel: [16697.153228]  [<ffffffff813ca65c>] blk_finish_plug+0x2c/0x40
Apr 10 12:32:09 anderson kernel: [16697.153239]  [<ffffffff8119dd5a>] __do_page_cache_readahead+0x1aa/0x230
Apr 10 12:32:09 anderson kernel: [16697.153246]  [<ffffffff8118fa0d>] ? pagecache_get_page+0x2d/0x1c0
Apr 10 12:32:09 anderson kernel: [16697.153254]  [<ffffffff811915c5>] filemap_fault+0x375/0x3f0
Apr 10 12:32:09 anderson kernel: [16697.153264]  [<ffffffff811cd271>] ? page_add_file_rmap+0x51/0x60
Apr 10 12:32:09 anderson kernel: [16697.153275]  [<ffffffff812a2e16>] ext4_filemap_fault+0x36/0x50
Apr 10 12:32:09 anderson kernel: [16697.153285]  [<ffffffff811be230>] __do_fault+0x50/0xe0
Apr 10 12:32:09 anderson kernel: [16697.153296]  [<ffffffff811c1d3e>] handle_mm_fault+0xf8e/0x1820
Apr 10 12:32:09 anderson kernel: [16697.153307]  [<ffffffff8106b527>] __do_page_fault+0x197/0x400
Apr 10 12:32:09 anderson kernel: [16697.153315]  [<ffffffff8106b7b2>] do_page_fault+0x22/0x30
Apr 10 12:32:09 anderson kernel: [16697.153324]  [<ffffffff8183e7f8>] page_fault+0x28/0x30
Apr 10 12:32:09 anderson kernel: [16697.153329] Mem-Info:
Apr 10 12:32:09 anderson kernel: [16697.153345] active_anon:397585 inactive_anon:225142 isolated_anon:0
Apr 10 12:32:09 anderson kernel: [16697.153345]  active_file:1104 inactive_file:996 isolated_file:75
Apr 10 12:32:09 anderson kernel: [16697.153345]  unevictable:1448 dirty:0 writeback:0 unstable:0
Apr 10 12:32:09 anderson kernel: [16697.153345]  slab_reclaimable:23545 slab_unreclaimable:27199
Apr 10 12:32:09 anderson kernel: [16697.153345]  mapped:1343980 shmem:59761 pagetables:10031 bounce:0
Apr 10 12:32:09 anderson kernel: [16697.153345]  free:8450 free_pcp:662 free_cma:0
Apr 10 12:32:09 anderson kernel: [16697.153357] Node 0 DMA free:15708kB min:0kB low:0kB high:0kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15988kB managed:15892kB mlocked:0kB dirty:0kB writeback:0kB mapped:144kB shmem:0kB slab_reclaimable:0kB slab_unreclaimable:12kB kernel_stack:0kB pagetables:0kB unstable:0kB bounce:0kB free_pcp:0kB local_pcp:0kB free_cma:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
Apr 10 12:32:09 anderson kernel: [16697.153374] lowmem_reserve[]: 0 3365 7828 7828 7828
Apr 10 12:32:09 anderson kernel: [16697.153386] Node 0 DMA32 free:17784kB min:0kB low:0kB high:0kB active_anon:523628kB inactive_anon:528048kB active_file:476kB inactive_file:392kB unevictable:3364kB isolated(anon):0kB isolated(file):0kB present:3567700kB managed:3487044kB mlocked:3364kB dirty:0kB writeback:0kB mapped:2362520kB shmem:111380kB slab_reclaimable:40000kB slab_unreclaimable:46888kB kernel_stack:3344kB pagetables:17180kB unstable:0kB bounce:0kB free_pcp:2276kB local_pcp:688kB free_cma:0kB writeback_tmp:0kB pages_scanned:444 all_unreclaimable? no
Apr 10 12:32:09 anderson kernel: [16697.153405] lowmem_reserve[]: 0 0 4462 4462 4462
Apr 10 12:32:09 anderson kernel: [16697.153417] Node 0 Normal free:308kB min:0kB low:0kB high:0kB active_anon:1066712kB inactive_anon:372520kB active_file:3940kB inactive_file:3592kB unevictable:2428kB isolated(anon):0kB isolated(file):300kB present:4702208kB managed:4569836kB mlocked:2428kB dirty:0kB writeback:0kB mapped:3013256kB shmem:127664kB slab_reclaimable:54180kB slab_unreclaimable:61896kB kernel_stack:5008kB pagetables:22944kB unstable:0kB bounce:0kB free_pcp:440kB local_pcp:64kB free_cma:0kB writeback_tmp:0kB pages_scanned:272096 all_unreclaimable? no
Apr 10 12:32:09 anderson kernel: [16697.153434] lowmem_reserve[]: 0 0 0 0 0
Apr 10 12:32:09 anderson kernel: [16697.153445] Node 0 DMA: 1*4kB (U) 1*8kB (U) 1*16kB (U) 0*32kB 1*64kB (U) 2*128kB (U) 0*256kB 0*512kB 1*1024kB (U) 1*2048kB (M) 3*4096kB (M) = 15708kB
Apr 10 12:32:09 anderson kernel: [16697.153485] Node 0 DMA32: 2072*4kB (UME) 474*8kB (UME) 119*16kB (UME) 47*32kB (UM) 36*64kB (UME) 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 17792kB
Apr 10 12:32:09 anderson kernel: [16697.153517] Node 0 Normal: 0*4kB 0*8kB 0*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 0kB
Apr 10 12:32:09 anderson kernel: [16697.153544] Node 0 hugepages_total=0 hugepages_free=0 hugepages_surp=0 hugepages_size=1048576kB
Apr 10 12:32:09 anderson kernel: [16697.153550] Node 0 hugepages_total=0 hugepages_free=0 hugepages_surp=0 hugepages_size=2048kB
Apr 10 12:32:09 anderson kernel: [16697.153553] 62553 total pagecache pages
Apr 10 12:32:09 anderson kernel: [16697.153558] 0 pages in swap cache
Apr 10 12:32:09 anderson kernel: [16697.153563] Swap cache stats: add 0, delete 0, find 0/0
Apr 10 12:32:09 anderson kernel: [16697.153566] Free swap  = 1022972kB
Apr 10 12:32:09 anderson kernel: [16697.153570] Total swap = 1022972kB
Apr 10 12:32:09 anderson kernel: [16697.153574] 2071474 pages RAM
Apr 10 12:32:09 anderson kernel: [16697.153578] 0 pages HighMem/MovableOnly
Apr 10 12:32:09 anderson kernel: [16697.153581] 53281 pages reserved
Apr 10 12:32:09 anderson kernel: [16697.153584] 0 pages cma reserved
Apr 10 12:32:09 anderson kernel: [16697.153588] 0 pages hwpoisoned
Apr 10 12:32:09 anderson kernel: [16697.153594] SLUB: Unable to allocate memory on node -1 (gfp=0x2088020)
Apr 10 12:32:09 anderson kernel: [16697.153600]   cache: mnt_cache, object size: 384, buffer size: 384, default order: 1, min order: 0
Apr 10 12:32:09 anderson kernel: [16697.153605]   node 0: slabs: 27, objs: 556, free: 0
```

---

### Post by Futant on 2017-04-11
Sounds like you're over-taxing your hardware. With lots of heavy programs and that many tabs your computer is bound to struggle! If it's happening aside of very heavy use you should contact the supplier of the laptop.

---

### Post by guttersnipe on 2017-04-11
Today I got a good log record of a would-be crash, but the OS recovered by killing VirtualBox due to an Out of memory issue.

Can someone tell me what is happening here? Has all of my RAM been exhausted (and what was the quantity used by buffers/cache)? Why didn't it attempt to use swap at the last minute (swappiness is set to 0).

```
Apr 11 09:32:21 anderson kernel: [10699.260993] Xorg invoked oom-killer: gfp_mask=0x240c0d0, order=3, oom_score_adj=0
Apr 11 09:32:21 anderson kernel: [10699.260997] Xorg cpuset=/ mems_allowed=0
Apr 11 09:32:21 anderson kernel: [10699.261005] CPU: 1 PID: 1172 Comm: Xorg Tainted: G           OE   4.4.0-71-generic #92-Ubuntu
Apr 11 09:32:21 anderson kernel: [10699.261007] Hardware name: ASUSTeK COMPUTER INC. UX305FA/UX305FA, BIOS UX305FA.206 12/16/2014
Apr 11 09:32:21 anderson kernel: [10699.261010]  0000000000000286 00000000b50e0595 ffff8800d8ff3530 ffffffff813f82b3
Apr 11 09:32:21 anderson kernel: [10699.261014]  ffff8800d8ff36e8 ffff880034f1aa00 ffff8800d8ff35a0 ffffffff8120b24e
Apr 11 09:32:21 anderson kernel: [10699.261017]  0000000000000015 0000000000000000 ffff8802118efe40 ffff880211a2c600
Apr 11 09:32:21 anderson kernel: [10699.261020] Call Trace:
Apr 11 09:32:21 anderson kernel: [10699.261028]  [<ffffffff813f82b3>] dump_stack+0x63/0x90
Apr 11 09:32:21 anderson kernel: [10699.261032]  [<ffffffff8120b24e>] dump_header+0x5a/0x1c5
Apr 11 09:32:21 anderson kernel: [10699.261037]  [<ffffffff81391254>] ? apparmor_capable+0xc4/0x1b0
Apr 11 09:32:21 anderson kernel: [10699.261041]  [<ffffffff811928c2>] oom_kill_process+0x202/0x3c0
Apr 11 09:32:21 anderson kernel: [10699.261044]  [<ffffffff81192ce9>] out_of_memory+0x219/0x460
Apr 11 09:32:21 anderson kernel: [10699.261049]  [<ffffffff81198cd8>] __alloc_pages_slowpath.constprop.88+0x938/0xad0
Apr 11 09:32:21 anderson kernel: [10699.261053]  [<ffffffff811990f6>] __alloc_pages_nodemask+0x286/0x2a0
Apr 11 09:32:21 anderson kernel: [10699.261058]  [<ffffffff811e2b8c>] alloc_pages_current+0x8c/0x110
Apr 11 09:32:21 anderson kernel: [10699.261062]  [<ffffffff81196ce9>] alloc_kmem_pages+0x19/0x90
Apr 11 09:32:21 anderson kernel: [10699.261065]  [<ffffffff811b472e>] kmalloc_order_trace+0x2e/0xe0
Apr 11 09:32:21 anderson kernel: [10699.261069]  [<ffffffff811ee91e>] __kmalloc+0x22e/0x250
Apr 11 09:32:21 anderson kernel: [10699.261100]  [<ffffffffc019bb9f>] ? alloc_gen8_temp_bitmaps+0x2f/0x80 [i915]
Apr 11 09:32:21 anderson kernel: [10699.261128]  [<ffffffffc019bbb8>] alloc_gen8_temp_bitmaps+0x48/0x80 [i915]
Apr 11 09:32:21 anderson kernel: [10699.261155]  [<ffffffffc019f1b0>] gen8_alloc_va_range_3lvl+0xa0/0x9d0 [i915]
Apr 11 09:32:21 anderson kernel: [10699.261160]  [<ffffffff811aafba>] ? shmem_getpage_gfp+0xca/0x830
Apr 11 09:32:21 anderson kernel: [10699.261164]  [<ffffffff81421c5d>] ? swiotlb_map_sg_attrs+0x6d/0x130
Apr 11 09:32:21 anderson kernel: [10699.261190]  [<ffffffffc019fd1f>] gen8_alloc_va_range+0x23f/0x4a0 [i915]
Apr 11 09:32:21 anderson kernel: [10699.261217]  [<ffffffffc01a1dab>] i915_vma_bind+0x9b/0x180 [i915]
Apr 11 09:32:21 anderson kernel: [10699.261235]  [<ffffffffc01a8f6a>] i915_gem_object_do_pin+0x89a/0xb10 [i915]
Apr 11 09:32:21 anderson kernel: [10699.261252]  [<ffffffffc01a920d>] i915_gem_object_pin+0x2d/0x30 [i915]
Apr 11 09:32:21 anderson kernel: [10699.261267]  [<ffffffffc0196b99>] i915_gem_execbuffer_reserve_vma.isra.18+0x99/0x160 [i915]
Apr 11 09:32:21 anderson kernel: [10699.261285]  [<ffffffffc0196feb>] i915_gem_execbuffer_reserve.isra.19+0x38b/0x3c0 [i915]
Apr 11 09:32:21 anderson kernel: [10699.261304]  [<ffffffffc01983bd>] i915_gem_do_execbuffer.isra.22+0x6ed/0x1310 [i915]
Apr 11 09:32:21 anderson kernel: [10699.261308]  [<ffffffff813f9749>] ? idr_get_empty_slot+0x199/0x3b0
Apr 11 09:32:21 anderson kernel: [10699.261311]  [<ffffffff811ed213>] ? kmem_cache_alloc_trace+0x183/0x1f0
Apr 11 09:32:21 anderson kernel: [10699.261329]  [<ffffffffc00c3ed4>] ? drm_vma_node_allow+0xa4/0xc0 [drm]
Apr 11 09:32:21 anderson kernel: [10699.261339]  [<ffffffffc00a9d53>] ? drm_gem_handle_create_tail+0xc3/0x190 [drm]
Apr 11 09:32:21 anderson kernel: [10699.261359]  [<ffffffffc0199ca2>] i915_gem_execbuffer2+0xb2/0x250 [i915]
Apr 11 09:32:21 anderson kernel: [10699.261369]  [<ffffffffc00aa752>] drm_ioctl+0x152/0x540 [drm]
Apr 11 09:32:21 anderson kernel: [10699.261389]  [<ffffffffc0199bf0>] ? i915_gem_execbuffer+0x330/0x330 [i915]
Apr 11 09:32:21 anderson kernel: [10699.261392]  [<ffffffff81222caf>] do_vfs_ioctl+0x29f/0x490
Apr 11 09:32:21 anderson kernel: [10699.261395]  [<ffffffff81222f19>] SyS_ioctl+0x79/0x90
Apr 11 09:32:21 anderson kernel: [10699.261399]  [<ffffffff8183c672>] entry_SYSCALL_64_fastpath+0x16/0x71
Apr 11 09:32:21 anderson kernel: [10699.261400] Mem-Info:
Apr 11 09:32:21 anderson kernel: [10699.261405] active_anon:396111 inactive_anon:234417 isolated_anon:0
Apr 11 09:32:21 anderson kernel: [10699.261405]  active_file:1305 inactive_file:1265 isolated_file:0
Apr 11 09:32:21 anderson kernel: [10699.261405]  unevictable:1457 dirty:10 writeback:0 unstable:0
Apr 11 09:32:21 anderson kernel: [10699.261405]  slab_reclaimable:28428 slab_unreclaimable:22839
Apr 11 09:32:21 anderson kernel: [10699.261405]  mapped:1342270 shmem:68381 pagetables:11019 bounce:0
Apr 11 09:32:21 anderson kernel: [10699.261405]  free:8413 free_pcp:62 free_cma:0
Apr 11 09:32:21 anderson kernel: [10699.261408] Node 0 DMA free:15784kB min:0kB low:0kB high:0kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15988kB managed:15892kB mlocked:0kB dirty:0kB writeback:0kB mapped:80kB shmem:0kB slab_reclaimable:0kB slab_unreclaimable:8kB kernel_stack:0kB pagetables:0kB unstable:0kB bounce:0kB free_pcp:0kB local_pcp:0kB free_cma:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
Apr 11 09:32:21 anderson kernel: [10699.261413] lowmem_reserve[]: 0 3365 7828 7828 7828
Apr 11 09:32:21 anderson kernel: [10699.261417] Node 0 DMA32 free:17904kB min:0kB low:0kB high:0kB active_anon:551580kB inactive_anon:523520kB active_file:3560kB inactive_file:3464kB unevictable:2528kB isolated(anon):0kB isolated(file):0kB present:3567700kB managed:3487044kB mlocked:2528kB dirty:16kB writeback:0kB mapped:2328528kB shmem:106888kB slab_reclaimable:50480kB slab_unreclaimable:40408kB kernel_stack:3616kB pagetables:18056kB unstable:0kB bounce:0kB free_pcp:248kB local_pcp:0kB free_cma:0kB writeback_tmp:0kB pages_scanned:344 all_unreclaimable? no
Apr 11 09:32:21 anderson kernel: [10699.261422] lowmem_reserve[]: 0 0 4462 4462 4462
Apr 11 09:32:21 anderson kernel: [10699.261425] Node 0 Normal free:0kB min:0kB low:0kB high:0kB active_anon:1032864kB inactive_anon:414148kB active_file:1660kB inactive_file:1596kB unevictable:3300kB isolated(anon):0kB isolated(file):0kB present:4702208kB managed:4569836kB mlocked:3300kB dirty:24kB writeback:0kB mapped:3040472kB shmem:166636kB slab_reclaimable:63232kB slab_unreclaimable:50940kB kernel_stack:5136kB pagetables:26020kB unstable:0kB bounce:0kB free_pcp:0kB local_pcp:0kB free_cma:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
Apr 11 09:32:21 anderson kernel: [10699.261429] lowmem_reserve[]: 0 0 0 0 0
Apr 11 09:32:21 anderson kernel: [10699.261432] Node 0 DMA: 0*4kB 1*8kB (U) 0*16kB 1*32kB (U) 2*64kB (U) 2*128kB (U) 0*256kB 0*512kB 1*1024kB (U) 1*2048kB (M) 3*4096kB (M) = 15784kB
Apr 11 09:32:21 anderson kernel: [10699.261446] Node 0 DMA32: 266*4kB (UME) 1985*8kB (UME) 59*16kB (M) 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 17888kB
Apr 11 09:32:21 anderson kernel: [10699.261455] Node 0 Normal: 26*4kB (M) 0*8kB 0*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 104kB
Apr 11 09:32:21 anderson kernel: [10699.261464] Node 0 hugepages_total=0 hugepages_free=0 hugepages_surp=0 hugepages_size=1048576kB
Apr 11 09:32:21 anderson kernel: [10699.261467] Node 0 hugepages_total=0 hugepages_free=0 hugepages_surp=0 hugepages_size=2048kB
Apr 11 09:32:21 anderson kernel: [10699.261468] 72084 total pagecache pages
Apr 11 09:32:21 anderson kernel: [10699.261469] 0 pages in swap cache
Apr 11 09:32:21 anderson kernel: [10699.261470] Swap cache stats: add 0, delete 0, find 0/0
Apr 11 09:32:21 anderson kernel: [10699.261471] Free swap  = 1022972kB
Apr 11 09:32:21 anderson kernel: [10699.261472] Total swap = 1022972kB
Apr 11 09:32:21 anderson kernel: [10699.261474] 2071474 pages RAM
Apr 11 09:32:21 anderson kernel: [10699.261475] 0 pages HighMem/MovableOnly
Apr 11 09:32:21 anderson kernel: [10699.261477] 53281 pages reserved
Apr 11 09:32:21 anderson kernel: [10699.261478] 0 pages cma reserved
Apr 11 09:32:21 anderson kernel: [10699.261479] 0 pages hwpoisoned
Apr 11 09:32:21 anderson kernel: [10699.261480] [ pid ]   uid  tgid total_vm      rss nr_ptes nr_pmds swapents oom_score_adj name
Apr 11 09:32:21 anderson kernel: [10699.261490] [  266]     0   266    10993     1886      23       3        0             0 systemd-journal
Apr 11 09:32:21 anderson kernel: [10699.261492] [  344]     0   344    11227      678      22       4        0         -1000 systemd-udevd
Apr 11 09:32:21 anderson kernel: [10699.261496] [  860]     0   860     7252      481      20       3        0             0 cron
Apr 11 09:32:21 anderson kernel: [10699.261498] [  874]   109   874    91140      872      78       3        0             0 whoopsie
Apr 11 09:32:21 anderson kernel: [10699.261500] [  875]     0   875    84320      844      66       3        0             0 ModemManager
Apr 11 09:32:21 anderson kernel: [10699.261501] [  877]   104   877    64099      573      27       4        0             0 rsyslogd
Apr 11 09:32:21 anderson kernel: [10699.261503] [  887]   111   887    11360      624      27       3        0             0 avahi-daemon
Apr 11 09:32:21 anderson kernel: [10699.261505] [  893]     0   893    41603      539      39       3        0             0 thermald
Apr 11 09:32:21 anderson kernel: [10699.261507] [  899]     0   899     7989      399      21       3        0             0 bluetoothd
Apr 11 09:32:21 anderson kernel: [10699.261509] [  902]   111   902    11197       82      25       3        0             0 avahi-daemon
Apr 11 09:32:21 anderson kernel: [10699.261511] [  905]   106   905    11054      566      27       3        0          -900 dbus-daemon
Apr 11 09:32:21 anderson kernel: [10699.261513] [  930]     0   930   133181     1165      74       4        0             0 NetworkManager
Apr 11 09:32:21 anderson kernel: [10699.261515] [  934]     0   934    54411     1948      30       5        0             0 snapd
Apr 11 09:32:21 anderson kernel: [10699.261517] [  939]     0   939    69006      397      38       4        0             0 accounts-daemon
Apr 11 09:32:21 anderson kernel: [10699.261519] [  964]     0   964     7160      422      20       3        0             0 systemd-logind
Apr 11 09:32:21 anderson kernel: [10699.261522] [  983]     0   983     1100      217       8       3        0             0 acpid
Apr 11 09:32:21 anderson kernel: [10699.261524] [ 1037]     0  1037     4521     1399      14       3        0             0 atop
Apr 11 09:32:21 anderson kernel: [10699.261526] [ 1090]     0  1090     4868      379      13       3        0             0 irqbalance
Apr 11 09:32:21 anderson kernel: [10699.261528] [ 1120]     0  1120    70432     1032      41       4        0             0 polkitd
Apr 11 09:32:21 anderson kernel: [10699.261530] [ 1139]     0  1139    87602      652      40       4        0             0 lightdm
Apr 11 09:32:21 anderson kernel: [10699.261532] [ 1148]     0  1148    16380      448      36       3        0         -1000 sshd
Apr 11 09:32:21 anderson kernel: [10699.261534] [ 1172]     0  1172   130287    52988     241       3        0             0 Xorg
Apr 11 09:32:21 anderson kernel: [10699.261536] [ 1240]     0  1240    11034      201      26       3        0             0 wpa_supplicant
Apr 11 09:32:21 anderson kernel: [10699.261537] [ 1303]     0  1303     3985      375      14       3        0             0 agetty
Apr 11 09:32:21 anderson kernel: [10699.261539] [ 1309]   123  1309    28024      267      25       3        0             0 ntpd
Apr 11 09:32:21 anderson kernel: [10699.261541] [ 1340]   117  1340    45886      410      25       3        0             0 rtkit-daemon
Apr 11 09:32:21 anderson kernel: [10699.261543] [ 1355]     0  1355    62227      705      57       3        0             0 lightdm
Apr 11 09:32:21 anderson kernel: [10699.261545] [ 1422]  1000  1422    11312      524      25       3        0             0 systemd
Apr 11 09:32:21 anderson kernel: [10699.261547] [ 1432]  1000  1432    20442      561      41       3        0             0 (sd-pam)
Apr 11 09:32:21 anderson kernel: [10699.261549] [ 1439]  1000  1439    88171      472      35       4        0             0 gnome-keyring-d
Apr 11 09:32:21 anderson kernel: [10699.261551] [ 1475]  1000  1475    11555      573      28       3        0             0 upstart
Apr 11 09:32:21 anderson kernel: [10699.261553] [ 1537]  1000  1537    10900      438      25       3        0             0 dbus-launch
Apr 11 09:32:21 anderson kernel: [10699.261555] [ 1538]  1000  1538    10692      452      23       3        0             0 dbus-daemon
Apr 11 09:32:21 anderson kernel: [10699.261557] [ 1544]  1000  1544    11878      473      27       3        0             0 xfconfd
Apr 11 09:32:21 anderson kernel: [10699.261559] [ 1555]  1000  1555     8215       67      20       4        0             0 upstart-udev-br
Apr 11 09:32:21 anderson kernel: [10699.261561] [ 1560]  1000  1560    10954      353      24       3        0             0 dbus-daemon
Apr 11 09:32:21 anderson kernel: [10699.261563] [ 1622]  1000  1622     1127      375       8       3        0             0 sh
Apr 11 09:32:21 anderson kernel: [10699.261565] [ 1634]  1000  1634    79771      913      91       3        0             0 xfce4-session
Apr 11 09:32:21 anderson kernel: [10699.261567] [ 1635]  1000  1635    10322      381      22       3        0             0 upstart-file-br
Apr 11 09:32:21 anderson kernel: [10699.261569] [ 1637]  1000  1637     8224      101      19       3        0             0 upstart-dbus-br
Apr 11 09:32:21 anderson kernel: [10699.261571] [ 1639]  1000  1639     8199       86      18       3        0             0 upstart-dbus-br
Apr 11 09:32:21 anderson kernel: [10699.261573] [ 1643]  1000  1643    11911      517      28       3        0             0 xfconfd
Apr 11 09:32:21 anderson kernel: [10699.261574] [ 1649]  1000  1649    94400     2561     109       4        0             0 xfwm4
Apr 11 09:32:21 anderson kernel: [10699.261576] [ 1653]  1000  1653    86229     1809     103       3        0             0 xfce4-panel
Apr 11 09:32:21 anderson kernel: [10699.261578] [ 1655]  1000  1655   242193     2528     120       4        0             0 Thunar
Apr 11 09:32:21 anderson kernel: [10699.261580] [ 1657]  1000  1657   112817     5497     119       3        0             0 xfdesktop
Apr 11 09:32:21 anderson kernel: [10699.261583] [ 1658]  1000  1658   147948     2526     175       4        0             0 launchy
Apr 11 09:32:21 anderson kernel: [10699.261584] [ 1659]  1000  1659    91333      787      96       4        0             0 xfsettingsd
Apr 11 09:32:21 anderson kernel: [10699.261586] [ 1660]  1000  1660    74249     1131      80       3        0             0 xfce4-notes
Apr 11 09:32:21 anderson kernel: [10699.261588] [ 1662]  1000  1662   218361     2433     129       4        0             0 nm-applet
Apr 11 09:32:21 anderson kernel: [10699.261590] [ 1663]  1000  1663    81567     1363      90       4        0             0 polkit-gnome-au
Apr 11 09:32:21 anderson kernel: [10699.261592] [ 1672]  1000  1672    78145      766      87       3        0             0 xfce4-power-man
Apr 11 09:32:21 anderson kernel: [10699.261594] [ 1673]  1000  1673    16679      469      39       3        0             0 xscreensaver
Apr 11 09:32:21 anderson kernel: [10699.261596] [ 1675]  1000  1675   123556     1224     108       4        0             0 update-notifier
Apr 11 09:32:21 anderson kernel: [10699.261598] [ 1677]  1000  1677    84453      550      32       4        0             0 at-spi-bus-laun
Apr 11 09:32:21 anderson kernel: [10699.261600] [ 1682]  1000  1682    10724      336      26       3        0             0 dbus-daemon
Apr 11 09:32:21 anderson kernel: [10699.261602] [ 1686]  1000  1686    51717      184      37       4        0             0 at-spi2-registr
Apr 11 09:32:21 anderson kernel: [10699.261604] [ 1690]  1000  1690   111369      645      90       4        0             0 xfce4-volumed
Apr 11 09:32:21 anderson kernel: [10699.261606] [ 1693]  1000  1693    68630      588      36       4        0             0 gvfsd
Apr 11 09:32:21 anderson kernel: [10699.261608] [ 1698]     0  1698    86814     1354      53       3        0             0 upowerd
Apr 11 09:32:21 anderson kernel: [10699.261610] [ 1701]  1000  1701   101715      997      34       4        0             0 gvfsd-fuse
Apr 11 09:32:21 anderson kernel: [10699.261612] [ 1718]  1000  1718   141612     1939      91       4        0             0 pulseaudio
Apr 11 09:32:21 anderson kernel: [10699.261614] [ 1779]  1000  1779    83010     1408      95       3        0             0 panel-1-whisker
Apr 11 09:32:21 anderson kernel: [10699.261617] [ 1785]  1000  1785    38552      462      78       3        0             0 panel-11-cpugra
Apr 11 09:32:21 anderson kernel: [10699.261619] [ 1790]  1000  1790    15325      529      33       3        0             0 gconfd-2
Apr 11 09:32:21 anderson kernel: [10699.261620] [ 1791]  1000  1791    39679      620      82       3        0             0 panel-4-systray
Apr 11 09:32:21 anderson kernel: [10699.261623] [ 1792]  1000  1792    78938     1130      89       4        0             0 panel-5-power-m
Apr 11 09:32:21 anderson kernel: [10699.261624] [ 1794]  1000  1794    89793      509      43       3        0             0 gvfs-udisks2-vo
Apr 11 09:32:21 anderson kernel: [10699.261626] [ 1797]  1000  1797   109360     2178     114       4        0             0 panel-6-indicat
Apr 11 09:32:21 anderson kernel: [10699.261629] [ 1798]     0  1798   108193     1519      45       4        0             0 udisksd
Apr 11 09:32:21 anderson kernel: [10699.261631] [ 1824]  1000  1824    66015      496      32       3        0             0 gvfs-mtp-volume
Apr 11 09:32:21 anderson kernel: [10699.261633] [ 1834]     0  1834     4032      625      13       3        0             0 dhclient
Apr 11 09:32:21 anderson kernel: [10699.261635] [ 1836]  1000  1836    64383      412      29       3        0             0 gvfs-goa-volume
Apr 11 09:32:21 anderson kernel: [10699.261636] [ 1845]  1000  1845    67930      417      34       4        0             0 gvfs-gphoto2-vo
Apr 11 09:32:21 anderson kernel: [10699.261638] [ 1857]  1000  1857   100902     1210      52       4        0             0 gvfs-afc-volume
Apr 11 09:32:21 anderson kernel: [10699.261640] [ 1858] 65534  1858    13217      483      30       3        0             0 dnsmasq
Apr 11 09:32:21 anderson kernel: [10699.261643] [ 1878]  1000  1878    11484      574      28       4        0             0 upstart
Apr 11 09:32:21 anderson kernel: [10699.261645] [ 1883]  1000  1883    88776      858      40       3        0             0 indicator-messa
Apr 11 09:32:21 anderson kernel: [10699.261647] [ 1884]  1000  1884   184394     1594      68       4        0             0 indicator-sound
Apr 11 09:32:21 anderson kernel: [10699.261648] [ 1891]  1000  1891    98984      814      87       3        0             0 indicator-appli
Apr 11 09:32:21 anderson kernel: [10699.261650] [ 2038]  1000  2038    87637      582      39       4        0             0 gvfsd-trash
Apr 11 09:32:21 anderson kernel: [10699.261652] [ 2058]  1000  2058    46486      321      26       3        0             0 gvfsd-metadata
Apr 11 09:32:21 anderson kernel: [10699.261654] [ 2092]  1000  2092    97935     2566      95       3        0             0 xfce4-terminal
Apr 11 09:32:21 anderson kernel: [10699.261656] [ 2096]  1000  2096     3718      395      13       3        0             0 gnome-pty-helpe
Apr 11 09:32:21 anderson kernel: [10699.261658] [ 2097]  1000  2097     5679      947      17       3        0             0 bash
Apr 11 09:32:21 anderson kernel: [10699.261660] [ 2109]  1000  2109     3136      443      12       3        0             0 startWork.sh
Apr 11 09:32:21 anderson kernel: [10699.261663] [ 2195]     0  2195     1127      181       8       3        0             0 sh
Apr 11 09:32:21 anderson kernel: [10699.261665] [ 2196]     0  2196     1756      158       7       2        0             0 ncsvc
Apr 11 09:32:21 anderson kernel: [10699.261667] [ 2307]  1000  2307   326650    23757     395       6        0             0 pidgin
Apr 11 09:32:21 anderson kernel: [10699.261669] [ 2328]  1000  2328   932679   279086    1121       7        0             0 firefox
Apr 11 09:32:21 anderson kernel: [10699.261671] [ 2349]  1000  2349    20256     2372      43       3        0             0 python
Apr 11 09:32:21 anderson kernel: [10699.261673] [ 2854]     0  2854    68704      518      67       3        0             0 cups-browsed
Apr 11 09:32:21 anderson kernel: [10699.261675] [ 3054]  1000  3054     1127      176       8       3        0             0 sh
Apr 11 09:32:21 anderson kernel: [10699.261677] [ 3055]  1000  3055   336779     5260     241       5        0             0 VirtualBox
Apr 11 09:32:21 anderson kernel: [10699.261679] [ 3070]  1000  3070    41649      657      67       4        0             0 VBoxXPCOMIPCD
Apr 11 09:32:21 anderson kernel: [10699.261681] [ 3075]  1000  3075   189125     1217     102       4        0             0 VBoxSVC
Apr 11 09:32:21 anderson kernel: [10699.261683] [ 3110]  1000  3110  1963180  1329785    2883      10        0             0 VirtualBox
Apr 11 09:32:21 anderson kernel: [10699.261685] [ 3691]  1000  3691   106620      654      43       4        0             0 gvfsd-network
Apr 11 09:32:21 anderson kernel: [10699.261687] [ 3712]  1000  3712     1127      165       9       3        0             0 sh
Apr 11 09:32:21 anderson kernel: [10699.261690] [ 3713]  1000  3713   195617    16016     135       5        0             0 cli
Apr 11 09:32:21 anderson kernel: [10699.261693] [ 3728]  1000  3728    90430      525      43       3        0             0 gvfsd-dnssd
Apr 11 09:32:21 anderson kernel: [10699.261696] [ 4021]  1000  4021   167712     9843     220      16        0             0 plugin-containe
Apr 11 09:32:21 anderson kernel: [10699.261699] [ 4824]  1000  4824    78760     2695      90       3        0             0 xfce4-notifyd
Apr 11 09:32:21 anderson kernel: [10699.261702] [ 4881]  1000  4881     1127      143       7       3        0             0 sh
Apr 11 09:32:21 anderson kernel: [10699.261704] [ 4882]  1000  4882    35423     1868      73       3        0             0 putty
Apr 11 09:32:21 anderson kernel: [10699.261706] [ 4903]  1000  4903     1127      139       8       3        0             0 sh
Apr 11 09:32:21 anderson kernel: [10699.261708] [ 4905]  1000  4905   112590     3055     109       4        0             0 mousepad
Apr 11 09:32:21 anderson kernel: [10699.261710] [ 4910]  1000  4910    44666      559      23       3        0             0 dconf-service
Apr 11 09:32:21 anderson kernel: [10699.261712] [ 5241]  1000  5241     3519      422      13       3        0             0 firejail
Apr 11 09:32:21 anderson kernel: [10699.261714] [ 5242]  1000  5242     3519      327      11       3        0             0 firejail
Apr 11 09:32:21 anderson kernel: [10699.261716] [ 5246]  1000  5246   645334   129931     584       6        0             0 firefox
Apr 11 09:32:21 anderson kernel: [10699.261718] [ 5501]  1000  5501     1127      180       8       3        0             0 sh
Apr 11 09:32:21 anderson kernel: [10699.261720] [ 5503]  1000  5503    38810     1735      78       3        0             0 putty
Apr 11 09:32:21 anderson kernel: [10699.261722] [ 5775]  1000  5775     1127      142       8       3        0             0 sh
Apr 11 09:32:21 anderson kernel: [10699.261724] [ 5776]  1000  5776    34323     1812      70       3        0             0 putty
Apr 11 09:32:21 anderson kernel: [10699.261726] [ 5798]  1000  5798     1127      166       8       3        0             0 sh
Apr 11 09:32:21 anderson kernel: [10699.261728] [ 5799]  1000  5799    34346     1719      71       3        0             0 putty
Apr 11 09:32:21 anderson kernel: [10699.261730] [ 5838]  1000  5838     1127      143       8       3        0             0 sh
Apr 11 09:32:21 anderson kernel: [10699.261733] [ 5840]  1000  5840    38779     1634      78       3        0             0 putty
Apr 11 09:32:21 anderson kernel: [10699.261736] Out of memory: Kill process 3110 (VirtualBox) score 586 or sacrifice child
Apr 11 09:32:21 anderson kernel: [10699.261793] Killed process 3110 (VirtualBox) total-vm:7852720kB, anon-rss:125172kB, file-rss:5193968kB

```

---

