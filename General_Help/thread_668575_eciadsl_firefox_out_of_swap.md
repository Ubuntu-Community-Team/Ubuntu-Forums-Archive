---
title: "eciadsl firefox out of swap?"
date: 2008-01-15
forum: General Help
---

### Post by sully101 on 2008-01-15
Heres my output from dmesg. what does it all mean and how do i fix it?

[635211.707938] gpg-agent invoked oom-killer: gfp_mask=0x201d2, order=0, oomkilladj=0
[635211.707993]  [<c0161f65>] out_of_memory+0x185/0x1c0
[635211.708020]  [<c0163934>] __alloc_pages+0x2e4/0x340
[635211.708039]  [<c01653d9>] __do_page_cache_readahead+0x109/0x250
[635211.708045]  [<f098bce0>] reiserfs_get_block+0x0/0x1400 [reiserfs]
[635211.708082]  [<c02f2c8d>] io_schedule+0x1d/0x30
[635211.708092]  [<c02f2f3b>] __wait_on_bit_lock+0x5b/0x70
[635211.708096]  [<c015e800>] sync_page+0x0/0x50
[635211.708104]  [<c015e7e3>] __lock_page+0x73/0x80
[635211.708116]  [<c01610a5>] filemap_nopage+0x155/0x340
[635211.708133]  [<c016ccd8>] __handle_mm_fault+0x148/0xb00
[635211.708143]  [<f0857719>] dl_done_list+0xc9/0x1f0 [ohci_hcd]
[635211.708153]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[635211.708177]  [<c02f5bf6>] do_page_fault+0x126/0x690
[635211.708185]  [<c01fefa0>] copy_to_user+0x30/0x60
[635211.708206]  [<c02f5ad0>] do_page_fault+0x0/0x690
[635211.708211]  [<c02f4352>] error_code+0x72/0x80
[635211.708230]  =======================
[635211.708232] Mem-info:
[635211.708235] DMA per-cpu:
[635211.708238] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
[635211.708241] Normal per-cpu:
[635211.708244] CPU    0: Hot: hi:  186, btch:  31 usd: 176   Cold: hi:   62, btch:  15 usd:  14
[635211.708250] Active:90336 inactive:90156 dirty:0 writeback:0 unstable:0
[635211.708252]  free:1623 slab:4216 mapped:6 pagetables:1409 bounce:0
[635211.708256] DMA free:3048kB min:72kB low:88kB high:108kB active:4632kB inactive:4508kB present:16256kB pages_scanned:15602 all_unreclaimable? yes
[635211.708260] lowmem_reserve[]: 0 746 746
[635211.708266] Normal free:3444kB min:3456kB low:4320kB high:5184kB active:356712kB inactive:356116kB present:763956kB pages_scanned:1131305 all_unreclaimable? yes
[635211.708270] lowmem_reserve[]: 0 0 0
[635211.708273] DMA: 0*4kB 1*8kB 2*16kB 0*32kB 1*64kB 1*128kB 1*256kB 1*512kB 0*1024kB 1*2048kB 0*4096kB = 3048kB
[635211.708282] Normal: 1*4kB 3*8kB 2*16kB 1*32kB 2*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 1*2048kB 0*4096kB = 3420kB
[635211.708293] Swap cache: add 612260, delete 612260, find 146681/222739, race 0+0
[635211.708296] Free swap  = 0kB
[635211.708298] Total swap = 610428kB
[635211.708300] Free swap:            0kB
[635211.718778] 196588 pages of RAM
[635211.718781] 0 pages of HIGHMEM
[635211.718783] 2754 reserved pages
[635211.718785] 7208 pages shared
[635211.718787] 0 pages swap cached
[635211.718789] 0 pages dirty
[635211.718790] 0 pages writeback
[635211.718792] 6 pages mapped
[635211.718794] 4216 pages slab
[635211.718796] 1409 pages pagetables
[635211.718830] dd invoked oom-killer: gfp_mask=0x201d2, order=0, oomkilladj=0
[635211.718868]  [<c0161f65>] out_of_memory+0x185/0x1c0
[635211.718891]  [<c0163934>] __alloc_pages+0x2e4/0x340
[635211.718910]  [<c01653d9>] __do_page_cache_readahead+0x109/0x250
[635211.718941]  [<c01610a5>] filemap_nopage+0x155/0x340
[635211.718947]  [<c02f204a>] schedule+0x2ca/0x890
[635211.718963]  [<c016ccd8>] __handle_mm_fault+0x148/0xb00
[635211.718991]  [<c02f5bf6>] do_page_fault+0x126/0x690
[635211.719002]  [<c0180e25>] vfs_read+0x125/0x160
[635211.719017]  [<c02f5ad0>] do_page_fault+0x0/0x690
[635211.719022]  [<c02f4352>] error_code+0x72/0x80
[635211.719042]  =======================
[635211.719044] Mem-info:
[635211.719046] DMA per-cpu:
[635211.719049] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
[635211.719052] Normal per-cpu:
[635211.719055] CPU    0: Hot: hi:  186, btch:  31 usd: 176   Cold: hi:   62, btch:  15 usd:  14
[635211.719060] Active:90336 inactive:90156 dirty:0 writeback:0 unstable:0
[635211.719061]  free:1623 slab:4216 mapped:6 pagetables:1409 bounce:0
[635211.719066] DMA free:3048kB min:72kB low:88kB high:108kB active:4632kB inactive:4508kB present:16256kB pages_scanned:15602 all_unreclaimable? yes
[635211.719070] lowmem_reserve[]: 0 746 746
[635211.719076] Normal free:3444kB min:3456kB low:4320kB high:5184kB active:356712kB inactive:356116kB present:763956kB pages_scanned:1131305 all_unreclaimable? yes
[635211.719080] lowmem_reserve[]: 0 0 0
[635211.719082] DMA: 0*4kB 1*8kB 2*16kB 0*32kB 1*64kB 1*128kB 1*256kB 1*512kB 0*1024kB 1*2048kB 0*4096kB = 3048kB
[635211.719092] Normal: 1*4kB 3*8kB 2*16kB 1*32kB 2*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 1*2048kB 0*4096kB = 3420kB
[635211.719102] Swap cache: add 612260, delete 612260, find 146681/222739, race 0+0
[635211.719105] Free swap  = 0kB
[635211.719107] Total swap = 610428kB
[635211.719109] Free swap:            0kB
[635211.729567] 196588 pages of RAM
[635211.729570] 0 pages of HIGHMEM
[635211.729572] 2754 reserved pages
[635211.729574] 7208 pages shared
[635211.729575] 0 pages swap cached
[635211.729577] 0 pages dirty
[635211.729579] 0 pages writeback
[635211.729580] 6 pages mapped
[635211.729582] 4216 pages slab
[635211.729584] 1409 pages pagetables
[635211.729735] bash invoked oom-killer: gfp_mask=0x201d2, order=0, oomkilladj=0
[635211.729772]  [<c0161f65>] out_of_memory+0x185/0x1c0
[635211.729794]  [<c0163934>] __alloc_pages+0x2e4/0x340
[635211.729812]  [<c01653d9>] __do_page_cache_readahead+0x109/0x250
[635211.729818]  [<f098bce0>] reiserfs_get_block+0x0/0x1400 [reiserfs]
[635211.729851]  [<c02f2c8d>] io_schedule+0x1d/0x30
[635211.729860]  [<c02f2f3b>] __wait_on_bit_lock+0x5b/0x70
[635211.729865]  [<c015e800>] sync_page+0x0/0x50
[635211.729872]  [<c015e7e3>] __lock_page+0x73/0x80
[635211.729884]  [<c01610a5>] filemap_nopage+0x155/0x340
[635211.729900]  [<c016ccd8>] __handle_mm_fault+0x148/0xb00
[635211.729908]  [<c01f76b3>] cfq_idle_slice_timer+0x73/0x80
[635211.729915]  [<c01312ab>] run_timer_softirq+0x15b/0x1c0
[635211.729924]  [<c010320a>] __switch_to+0xaa/0x1d0
[635211.729942]  [<c02f5bf6>] do_page_fault+0x126/0x690
[635211.729963]  [<c02f5ad0>] do_page_fault+0x0/0x690
[635211.729968]  [<c02f4352>] error_code+0x72/0x80
[635211.729987]  =======================
[635211.729989] Mem-info:
[635211.729991] DMA per-cpu:
[635211.729993] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
[635211.729996] Normal per-cpu:
[635211.729999] CPU    0: Hot: hi:  186, btch:  31 usd: 176   Cold: hi:   62, btch:  15 usd:  14
[635211.730004] Active:90355 inactive:90136 dirty:0 writeback:0 unstable:0
[635211.730006]  free:1623 slab:4216 mapped:6 pagetables:1409 bounce:0
[635211.730011] DMA free:3048kB min:72kB low:88kB high:108kB active:4632kB inactive:4508kB present:16256kB pages_scanned:15602 all_unreclaimable? yes
[635211.730014] lowmem_reserve[]: 0 746 746
[635211.730020] Normal free:3444kB min:3456kB low:4320kB high:5184kB active:356788kB inactive:356036kB present:763956kB pages_scanned:1131413 all_unreclaimable? yes
[635211.730024] lowmem_reserve[]: 0 0 0
[635211.730027] DMA: 0*4kB 1*8kB 2*16kB 0*32kB 1*64kB 1*128kB 1*256kB 1*512kB 0*1024kB 1*2048kB 0*4096kB = 3048kB
[635211.730036] Normal: 1*4kB 3*8kB 2*16kB 1*32kB 2*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 1*2048kB 0*4096kB = 3420kB
[635211.730047] Swap cache: add 612260, delete 612260, find 146681/222739, race 0+0
[635211.730049] Free swap  = 0kB
[635211.730051] Total swap = 610428kB
[635211.730053] Free swap:            0kB
[635211.740511] 196588 pages of RAM
[635211.740515] 0 pages of HIGHMEM
[635211.740517] 2754 reserved pages
[635211.740519] 7208 pages shared
[635211.740520] 0 pages swap cached
[635211.740522] 0 pages dirty
[635211.740524] 0 pages writeback
[635211.740525] 6 pages mapped
[635211.740527] 4216 pages slab
[635211.740529] 1409 pages pagetables
[635211.740772] Out of memory: kill process 9837 (run-mozilla.sh) score 70967 or a child
[635211.740784] Killed process 9846 (firefox-bin)
[635211.741973] akregator invoked oom-killer: gfp_mask=0x201d2, order=0, oomkilladj=0
[635211.742017]  [<c0161f65>] out_of_memory+0x185/0x1c0
[635211.742041]  [<c0163934>] __alloc_pages+0x2e4/0x340
[635211.742061]  [<c01653d9>] __do_page_cache_readahead+0x109/0x250
[635211.742068]  [<f098bce0>] reiserfs_get_block+0x0/0x1400 [reiserfs]
[635211.742103]  [<c02f2c8d>] io_schedule+0x1d/0x30
[635211.742112]  [<c02f2f3b>] __wait_on_bit_lock+0x5b/0x70
[635211.742116]  [<c015e800>] sync_page+0x0/0x50
[635211.742124]  [<c015e7e3>] __lock_page+0x73/0x80
[635211.742137]  [<c01610a5>] filemap_nopage+0x155/0x340
[635211.742153]  [<c016ccd8>] __handle_mm_fault+0x148/0xb00
[635211.742162]  [<c012da61>] irq_exit+0x51/0x80
[635211.742167]  [<c0118735>] smp_apic_timer_interrupt+0x55/0x80
[635211.742181]  [<c010320a>] __switch_to+0xaa/0x1d0
[635211.742200]  [<c02f5bf6>] do_page_fault+0x126/0x690
[635211.742221]  [<c02f5ad0>] do_page_fault+0x0/0x690
[635211.742227]  [<c02f4352>] error_code+0x72/0x80
[635211.742246]  =======================
[635211.742248] Mem-info:
[635211.742250] DMA per-cpu:
[635211.742253] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
[635211.742256] Normal per-cpu:
[635211.742259] CPU    0: Hot: hi:  186, btch:  31 usd: 176   Cold: hi:   62, btch:  15 usd:  14
[635211.742264] Active:90381 inactive:90136 dirty:0 writeback:0 unstable:0
[635211.742266]  free:1623 slab:4216 mapped:6 pagetables:1409 bounce:0
[635211.742271] DMA free:3048kB min:72kB low:88kB high:108kB active:4632kB inactive:4508kB present:16256kB pages_scanned:15602 all_unreclaimable? yes
[635211.742274] lowmem_reserve[]: 0 746 746
[635211.742280] Normal free:3444kB min:3456kB low:4320kB high:5184kB active:356892kB inactive:356036kB present:763956kB pages_scanned:1132855 all_unreclaimable? yes
[635211.742284] lowmem_reserve[]: 0 0 0
[635211.742287] DMA: 0*4kB 1*8kB 2*16kB 0*32kB 1*64kB 1*128kB 1*256kB 1*512kB 0*1024kB 1*2048kB 0*4096kB = 3048kB
[635211.742296] Normal: 1*4kB 3*8kB 2*16kB 1*32kB 2*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 1*2048kB 0*4096kB = 3420kB
[635211.742307] Swap cache: add 612260, delete 612260, find 146681/222739, race 0+0
[635211.742309] Free swap  = 0kB
[635211.742311] Total swap = 610428kB
[635211.742313] Free swap:            0kB
[635211.752810] 196588 pages of RAM
[635211.752813] 0 pages of HIGHMEM
[635211.752815] 2754 reserved pages
[635211.752817] 7176 pages shared
[635211.752819] 0 pages swap cached
[635211.752821] 0 pages dirty
[635211.752822] 0 pages writeback
[635211.752824] 6 pages mapped
[635211.752826] 4216 pages slab
[635211.752827] 1409 pages pagetables
[635211.752945] bash invoked oom-killer: gfp_mask=0x201d2, order=0, oomkilladj=0
[635211.752983]  [<c0161f65>] out_of_memory+0x185/0x1c0
[635211.753005]  [<c0163934>] __alloc_pages+0x2e4/0x340
[635211.753024]  [<c01653d9>] __do_page_cache_readahead+0x109/0x250
[635211.753030]  [<f098bce0>] reiserfs_get_block+0x0/0x1400 [reiserfs]
[635211.753063]  [<c02f2c8d>] io_schedule+0x1d/0x30
[635211.753072]  [<c02f2f3b>] __wait_on_bit_lock+0x5b/0x70
[635211.753076]  [<c015e800>] sync_page+0x0/0x50
[635211.753084]  [<c015e7e3>] __lock_page+0x73/0x80
[635211.753096]  [<c01610a5>] filemap_nopage+0x155/0x340
[635211.753113]  [<c016ccd8>] __handle_mm_fault+0x148/0xb00
[635211.753120]  [<c01f76b3>] cfq_idle_slice_timer+0x73/0x80
[635211.753128]  [<c01312ab>] run_timer_softirq+0x15b/0x1c0
[635211.753137]  [<c010320a>] __switch_to+0xaa/0x1d0
[635211.753156]  [<c02f5bf6>] do_page_fault+0x126/0x690
[635211.753178]  [<c02f5ad0>] do_page_fault+0x0/0x690
[635211.753183]  [<c02f4352>] error_code+0x72/0x80
[635211.753203]  =======================
[635211.753205] Mem-info:
[635211.753206] DMA per-cpu:
[635211.753209] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
[635211.753212] Normal per-cpu:
[635211.753215] CPU    0: Hot: hi:  186, btch:  31 usd: 176   Cold: hi:   62, btch:  15 usd:  14
[635211.753220] Active:90405 inactive:90118 dirty:0 writeback:0 unstable:0
[635211.753222]  free:1623 slab:4216 mapped:6 pagetables:1409 bounce:0
[635211.753227] DMA free:3048kB min:72kB low:88kB high:108kB active:4632kB inactive:4508kB present:16256kB pages_scanned:15602 all_unreclaimable? yes
[635211.753230] lowmem_reserve[]: 0 746 746
[635211.753236] Normal free:3444kB min:3456kB low:4320kB high:5184kB active:356988kB inactive:355964kB present:763956kB pages_scanned:1132963 all_unreclaimable? yes
[635211.753240] lowmem_reserve[]: 0 0 0
[635211.753243] DMA: 0*4kB 1*8kB 2*16kB 0*32kB 1*64kB 1*128kB 1*256kB 1*512kB 0*1024kB 1*2048kB 0*4096kB = 3048kB
[635211.753252] Normal: 1*4kB 3*8kB 2*16kB 1*32kB 2*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 1*2048kB 0*4096kB = 3420kB
[635211.753262] Swap cache: add 612260, delete 612260, find 146681/222739, race 0+0
[635211.753265] Free swap  = 0kB
[635211.753267] Total swap = 610428kB
[635211.753269] Free swap:            0kB
[635211.763727] 196588 pages of RAM
[635211.763731] 0 pages of HIGHMEM
[635211.763733] 2754 reserved pages
[635211.763741] 7176 pages shared
[635211.763743] 0 pages swap cached
[635211.763744] 0 pages dirty
[635211.763746] 0 pages writeback
[635211.763748] 6 pages mapped
[635211.763750] 4216 pages slab
[635211.763751] 1409 pages pagetables
[635211.763916] dd invoked oom-killer: gfp_mask=0x201d2, order=0, oomkilladj=0
[635211.763954]  [<c0161f65>] out_of_memory+0x185/0x1c0
[635211.763975]  [<c0163934>] __alloc_pages+0x2e4/0x340
[635211.763994]  [<c01653d9>] __do_page_cache_readahead+0x109/0x250
[635211.764024]  [<c01610a5>] filemap_nopage+0x155/0x340
[635211.764029]  [<c02f204a>] schedule+0x2ca/0x890
[635211.764045]  [<c016ccd8>] __handle_mm_fault+0x148/0xb00
[635211.764073]  [<c02f5bf6>] do_page_fault+0x126/0x690
[635211.764083]  [<c0180e25>] vfs_read+0x125/0x160
[635211.764098]  [<c02f5ad0>] do_page_fault+0x0/0x690
[635211.764103]  [<c02f4352>] error_code+0x72/0x80
[635211.764122]  =======================
[635211.764124] Mem-info:
[635211.764126] DMA per-cpu:
[635211.764128] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
[635211.764131] Normal per-cpu:
[635211.764134] CPU    0: Hot: hi:  186, btch:  31 usd: 176   Cold: hi:   62, btch:  15 usd:  14
[635211.764139] Active:90405 inactive:90118 dirty:0 writeback:0 unstable:0
[635211.764141]  free:1623 slab:4216 mapped:6 pagetables:1409 bounce:0
[635211.764146] DMA free:3048kB min:72kB low:88kB high:108kB active:4632kB inactive:4508kB present:16256kB pages_scanned:15602 all_unreclaimable? yes
[635211.764150] lowmem_reserve[]: 0 746 746
[635211.764155] Normal free:3444kB min:3456kB low:4320kB high:5184kB active:356988kB inactive:355964kB present:763956kB pages_scanned:1132963 all_unreclaimable? yes
[635211.764159] lowmem_reserve[]: 0 0 0
[635211.764162] DMA: 0*4kB 1*8kB 2*16kB 0*32kB 1*64kB 1*128kB 1*256kB 1*512kB 0*1024kB 1*2048kB 0*4096kB = 3048kB
[635211.764171] Normal: 1*4kB 3*8kB 2*16kB 1*32kB 2*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 1*2048kB 0*4096kB = 3420kB
[635211.764182] Swap cache: add 612260, delete 612260, find 146681/222739, race 0+0
[635211.764185] Free swap  = 0kB
[635211.764186] Total swap = 610428kB
[635211.764188] Free swap:            0kB
[635211.774678] 196588 pages of RAM
[635211.774682] 0 pages of HIGHMEM
[635211.774684] 2754 reserved pages
[635211.774686] 7176 pages shared
[635211.774688] 0 pages swap cached
[635211.774690] 0 pages dirty
[635211.774691] 0 pages writeback
[635211.774693] 6 pages mapped
[635211.774695] 4216 pages slab
[635211.774696] 1409 pages pagetables
[635211.774810] bash invoked oom-killer: gfp_mask=0x201d2, order=0, oomkilladj=0
[635211.774848]  [<c0161f65>] out_of_memory+0x185/0x1c0
[635211.774870]  [<c0163934>] __alloc_pages+0x2e4/0x340
[635211.774890]  [<c01653d9>] __do_page_cache_readahead+0x109/0x250
[635211.774896]  [<f098bce0>] reiserfs_get_block+0x0/0x1400 [reiserfs]
[635211.774929]  [<c02f2c8d>] io_schedule+0x1d/0x30
[635211.774938]  [<c02f2f3b>] __wait_on_bit_lock+0x5b/0x70
[635211.774942]  [<c015e800>] sync_page+0x0/0x50
[635211.774950]  [<c015e7e3>] __lock_page+0x73/0x80
[635211.774962]  [<c01610a5>] filemap_nopage+0x155/0x340
[635211.774979]  [<c016ccd8>] __handle_mm_fault+0x148/0xb00
[635211.774987]  [<c01f76b3>] cfq_idle_slice_timer+0x73/0x80
[635211.774994]  [<c01312ab>] run_timer_softirq+0x15b/0x1c0
[635211.775004]  [<c010320a>] __switch_to+0xaa/0x1d0
[635211.775023]  [<c02f5bf6>] do_page_fault+0x126/0x690
[635211.775045]  [<c02f5ad0>] do_page_fault+0x0/0x690
[635211.775050]  [<c02f4352>] error_code+0x72/0x80
[635211.775070]  =======================
[635211.775071] Mem-info:
[635211.775073] DMA per-cpu:
[635211.775076] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
[635211.775079] Normal per-cpu:
[635211.775082] CPU    0: Hot: hi:  186, btch:  31 usd: 176   Cold: hi:   62, btch:  15 usd:  14
[635211.775087] Active:90425 inactive:90098 dirty:0 writeback:0 unstable:0
[635211.775089]  free:1623 slab:4216 mapped:6 pagetables:1409 bounce:0
[635211.775094] DMA free:3048kB min:72kB low:88kB high:108kB active:4632kB inactive:4508kB present:16256kB pages_scanned:15602 all_unreclaimable? yes
[635211.775097] lowmem_reserve[]: 0 746 746
[635211.775103] Normal free:3444kB min:3456kB low:4320kB high:5184kB active:357068kB inactive:355884kB present:763956kB pages_scanned:1133071 all_unreclaimable? yes
[635211.775107] lowmem_reserve[]: 0 0 0
[635211.775110] DMA: 0*4kB 1*8kB 2*16kB 0*32kB 1*64kB 1*128kB 1*256kB 1*512kB 0*1024kB 1*2048kB 0*4096kB = 3048kB
[635211.775119] Normal: 1*4kB 3*8kB 2*16kB 1*32kB 2*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 1*2048kB 0*4096kB = 3420kB
[635211.775130] Swap cache: add 612260, delete 612260, find 146681/222739, race 0+0
[635211.775132] Free swap  = 0kB
[635211.775134] Total swap = 610428kB
[635211.775136] Free swap:            0kB
[635211.785623] 196588 pages of RAM
[635211.785627] 0 pages of HIGHMEM
[635211.785629] 2754 reserved pages
[635211.785631] 7176 pages shared
[635211.785632] 0 pages swap cached
[635211.785634] 0 pages dirty
[635211.785636] 0 pages writeback
[635211.785638] 6 pages mapped
[635211.785640] 4216 pages slab
[635211.785641] 1409 pages pagetables
[635211.785812] gpg-agent invoked oom-killer: gfp_mask=0x201d2, order=0, oomkilladj=0
[635211.785849]  [<c0161f65>] out_of_memory+0x185/0x1c0
[635211.785871]  [<c0163934>] __alloc_pages+0x2e4/0x340
[635211.785890]  [<c01653d9>] __do_page_cache_readahead+0x109/0x250
[635211.785896]  [<f098bce0>] reiserfs_get_block+0x0/0x1400 [reiserfs]
[635211.785929]  [<c02f2c8d>] io_schedule+0x1d/0x30
[635211.785938]  [<c02f2f3b>] __wait_on_bit_lock+0x5b/0x70
[635211.785942]  [<c015e800>] sync_page+0x0/0x50
[635211.785950]  [<c015e7e3>] __lock_page+0x73/0x80
[635211.785963]  [<c01610a5>] filemap_nopage+0x155/0x340
[635211.785979]  [<c016ccd8>] __handle_mm_fault+0x148/0xb00
[635211.785990]  [<f0857719>] dl_done_list+0xc9/0x1f0 [ohci_hcd]
[635211.785999]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[635211.786023]  [<c02f5bf6>] do_page_fault+0x126/0x690
[635211.786031]  [<c01fefa0>] copy_to_user+0x30/0x60
[635211.786052]  [<c02f5ad0>] do_page_fault+0x0/0x690
[635211.786057]  [<c02f4352>] error_code+0x72/0x80
[635211.786077]  =======================
[635211.786079] Mem-info:
[635211.786081] DMA per-cpu:
[635211.786084] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
[635211.786087] Normal per-cpu:
[635211.786090] CPU    0: Hot: hi:  186, btch:  31 usd: 176   Cold: hi:   62, btch:  15 usd:  14
[635211.786095] Active:90425 inactive:90098 dirty:0 writeback:0 unstable:0
[635211.786097]  free:1623 slab:4216 mapped:6 pagetables:1409 bounce:0
[635211.786102] DMA free:3048kB min:72kB low:88kB high:108kB active:4632kB inactive:4508kB present:16256kB pages_scanned:15602 all_unreclaimable? yes
[635211.786105] lowmem_reserve[]: 0 746 746
[635211.786111] Normal free:3444kB min:3456kB low:4320kB high:5184kB active:357068kB inactive:355884kB present:763956kB pages_scanned:1133071 all_unreclaimable? yes
[635211.786115] lowmem_reserve[]: 0 0 0
[635211.786118] DMA: 0*4kB 1*8kB 2*16kB 0*32kB 1*64kB 1*128kB 1*256kB 1*512kB 0*1024kB 1*2048kB 0*4096kB = 3048kB
[635211.786127] Normal: 1*4kB 3*8kB 2*16kB 1*32kB 2*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 1*2048kB 0*4096kB = 3420kB
[635211.786138] Swap cache: add 612260, delete 612260, find 146681/222739, race 0+0
[635211.786140] Free swap  = 0kB
[635211.786142] Total swap = 610428kB
[635211.786144] Free swap:            0kB
[635211.796651] 196588 pages of RAM
[635211.796654] 0 pages of HIGHMEM
[635211.796656] 2754 reserved pages
[635211.796658] 7176 pages shared
[635211.796660] 0 pages swap cached
[635211.796662] 0 pages dirty
[635211.796663] 0 pages writeback
[635211.796665] 6 pages mapped
[635211.796666] 4216 pages slab
[635211.796668] 1409 pages pagetables
[635211.796685] eciadsl-pppoeci invoked oom-killer: gfp_mask=0x40d0, order=1, oomkilladj=0
[635211.796723]  [<c0161f65>] out_of_memory+0x185/0x1c0
[635211.796745]  [<c0163934>] __alloc_pages+0x2e4/0x340
[635211.796752]  [<c01a5c97>] bio_add_page+0x37/0x50
[635211.796769]  [<c017c475>] __slab_alloc+0x125/0x4f0
[635211.796788]  [<c017cfd5>] __kmalloc+0x95/0xa0
[635211.796793]  [<f0885646>] proc_submiturb+0x1e6/0x910 [usbcore]
[635211.796834]  [<f0885646>] proc_submiturb+0x1e6/0x910 [usbcore]
[635211.796858]  [<f087ecb0>] urb_destroy+0x0/0x10 [usbcore]
[635211.796874]  [<c01faf9b>] kref_put+0x2b/0xa0
[635211.796888]  [<f088529a>] processcompl+0x10a/0x120 [usbcore]
[635211.796920]  [<f08866ad>] usbdev_ioctl+0x21d/0x1400 [usbcore]
[635211.796963]  [<c02f2c8d>] io_schedule+0x1d/0x30
[635211.796972]  [<c02f2f3b>] __wait_on_bit_lock+0x5b/0x70
[635211.796977]  [<c015e800>] sync_page+0x0/0x50
[635211.796985]  [<c015e7e3>] __lock_page+0x73/0x80
[635211.796993]  [<c013be20>] wake_bit_function+0x0/0x60
[635211.797003]  [<c0161237>] filemap_nopage+0x2e7/0x340
[635211.797019]  [<c016ce18>] __handle_mm_fault+0x288/0xb00
[635211.797031]  [<c0140e36>] getnstimeofday+0x36/0xd0
[635211.797048]  [<f0886490>] usbdev_ioctl+0x0/0x1400 [usbcore]
[635211.797066]  [<c018ca74>] do_ioctl+0x84/0xc0
[635211.797072]  [<c02f5e59>] do_page_fault+0x389/0x690
[635211.797080]  [<f0886490>] usbdev_ioctl+0x0/0x1400 [usbcore]
[635211.797099]  [<c018cb0c>] vfs_ioctl+0x5c/0x290
[635211.797109]  [<c018cdb2>] sys_ioctl+0x72/0x90
[635211.797117]  [<c01041d2>] sysenter_past_esp+0x6b/0xa9
[635211.797138]  =======================
[635211.797140] Mem-info:
[635211.797142] DMA per-cpu:
[635211.797145] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
[635211.797148] Normal per-cpu:
[635211.797151] CPU    0: Hot: hi:  186, btch:  31 usd: 176   Cold: hi:   62, btch:  15 usd:  14
[635211.797155] Active:90425 inactive:90098 dirty:0 writeback:0 unstable:0
[635211.797157]  free:1623 slab:4216 mapped:6 pagetables:1409 bounce:0
[635211.797162] DMA free:3048kB min:72kB low:88kB high:108kB active:4632kB inactive:4508kB present:16256kB pages_scanned:15602 all_unreclaimable? yes
[635211.797166] lowmem_reserve[]: 0 746 746
[635211.797172] Normal free:3444kB min:3456kB low:4320kB high:5184kB active:357068kB inactive:355884kB present:763956kB pages_scanned:1133071 all_unreclaimable? yes
[635211.797176] lowmem_reserve[]: 0 0 0
[635211.797179] DMA: 0*4kB 1*8kB 2*16kB 0*32kB 1*64kB 1*128kB 1*256kB 1*512kB 0*1024kB 1*2048kB 0*4096kB = 3048kB
[635211.797188] Normal: 1*4kB 3*8kB 2*16kB 1*32kB 2*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 1*2048kB 0*4096kB = 3420kB
[635211.797198] Swap cache: add 612260, delete 612260, find 146681/222739, race 0+0
[635211.797201] Free swap  = 0kB
[635211.797203] Total swap = 610428kB
[635211.797205] Free swap:            0kB
[635211.807647] 196588 pages of RAM
[635211.807650] 0 pages of HIGHMEM
[635211.807652] 2754 reserved pages
[635211.807654] 7176 pages shared
[635211.807656] 0 pages swap cached
[635211.807657] 0 pages dirty
[635211.807659] 0 pages writeback
[635211.807673] 6 pages mapped
[635211.807675] 4216 pages slab
[635211.807677] 1409 pages pagetables
[635211.807838] eciadsl-pppoeci invoked oom-killer: gfp_mask=0x201d2, order=0, oomkilladj=0
[635211.807876]  [<c0161f65>] out_of_memory+0x185/0x1c0
[635211.807899]  [<c0163934>] __alloc_pages+0x2e4/0x340
[635211.807908]  [<c0145607>] unqueue_me+0x47/0x90
[635211.807926]  [<c01653d9>] __do_page_cache_readahead+0x109/0x250
[635211.807932]  [<f098bce0>] reiserfs_get_block+0x0/0x1400 [reiserfs]
[635211.807966]  [<c02f2c8d>] io_schedule+0x1d/0x30
[635211.807975]  [<c02f2f3b>] __wait_on_bit_lock+0x5b/0x70
[635211.807979]  [<c015e800>] sync_page+0x0/0x50
[635211.807987]  [<c015e7e3>] __lock_page+0x73/0x80
[635211.808000]  [<c01610a5>] filemap_nopage+0x155/0x340
[635211.808018]  [<c016ccd8>] __handle_mm_fault+0x148/0xb00
[635211.808047]  [<c02f5bf6>] do_page_fault+0x126/0x690
[635211.808055]  [<c0140326>] do_gettimeofday+0x36/0x100
[635211.808072]  [<c02f5ad0>] do_page_fault+0x0/0x690
[635211.808077]  [<c02f4352>] error_code+0x72/0x80
[635211.808097]  =======================
[635211.808099] Mem-info:
[635211.808101] DMA per-cpu:
[635211.808104] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
[635211.808107] Normal per-cpu:
[635211.808110] CPU    0: Hot: hi:  186, btch:  31 usd: 176   Cold: hi:   62, btch:  15 usd:  14
[635211.808115] Active:90425 inactive:90098 dirty:0 writeback:0 unstable:0
[635211.808117]  free:1623 slab:4216 mapped:6 pagetables:1409 bounce:0
[635211.808122] DMA free:3048kB min:72kB low:88kB high:108kB active:4632kB inactive:4508kB present:16256kB pages_scanned:15602 all_unreclaimable? yes
[635211.808125] lowmem_reserve[]: 0 746 746
[635211.808131] Normal free:3444kB min:3456kB low:4320kB high:5184kB active:357068kB inactive:355884kB present:763956kB pages_scanned:1133071 all_unreclaimable? yes
[635211.808135] lowmem_reserve[]: 0 0 0
[635211.808138] DMA: 0*4kB 1*8kB 2*16kB 0*32kB 1*64kB 1*128kB 1*256kB 1*512kB 0*1024kB 1*2048kB 0*4096kB = 3048kB
[635211.808147] Normal: 1*4kB 3*8kB 2*16kB 1*32kB 2*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 1*2048kB 0*4096kB = 3420kB
[635211.808158] Swap cache: add 612260, delete 612260, find 146681/222739, race 0+0
[635211.808160] Free swap  = 0kB
[635211.808162] Total swap = 610428kB
[635211.808164] Free swap:            0kB
[635211.818610] 196588 pages of RAM
[635211.818613] 0 pages of HIGHMEM
[635211.818615] 2754 reserved pages
[635211.818616] 7176 pages shared
[635211.818618] 0 pages swap cached
[635211.818620] 0 pages dirty
[635211.818622] 0 pages writeback
[635211.818623] 6 pages mapped
[635211.818625] 4216 pages slab
[635211.818627] 1409 pages pagetables

---

