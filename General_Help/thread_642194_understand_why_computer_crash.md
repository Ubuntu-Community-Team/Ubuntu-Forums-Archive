---
title: "understand why computer crash"
date: 2007-12-16
forum: General Help
---

### Post by Blinkiz on 2007-12-16
Hi
Am in need of help to understand why Ubuntu 7.10 server totally freezes when one of my programs doing something wrong.

When I download alot with rtorrent/libtorrent my ubuntu server can totally freeze and I have to restart it by pressing the power button. Changing tty and ctrl-alt-del does not work. Not even a text about the crash is put in /var/log/messages. Yes, it is because of rtorrent but ubuntu shouldn't crash because of a faulty program.

**Am in need of help to troubleshoot why ubuntu totally crashes at high load of rtorrent/libtorrent.** I have heard of a klog console but I can't find any information about this for ubuntu.

Specifications
Intel Pentium 3 800 Mhz processor
512 MB RAM 100 Mhz (using 40-70 MB when download with rtorrent)
1 GB SWAP space (all free, on old IDE drive)
10 GB sysdrive ext3 (Old IDE drive)
New Seagate Barracuda ES.2 500GB SATA/300 32MB, ext3
New Lycom SATA II Controller card PCI (SiliconImage SiI 3124-2 chipset)
No graphical gui is running.

Below is syslog from the same minute my computer freezes.
```
Dec 16 17:27:01 localhost kernel: [ 1188.623728] printk: 414349 messages suppressed.
Dec 16 17:27:03 localhost kernel: [ 1188.623745] swapper: page allocation failure. order:1, mode:0x4020
Dec 16 17:27:36 localhost kernel: [ 1188.623782]  [__alloc_pages+800/832] __alloc_pages+0x320/0x340
Dec 16 17:27:36 localhost kernel: [ 1188.623831]  [__slab_alloc+293/1264] __slab_alloc+0x125/0x4f0
Dec 16 17:27:36 localhost kernel: [ 1188.623856]  [<e0850a47>] rtl8169_rx_interrupt+0x567/0x590 [r8169]
Dec 16 17:27:36 localhost kernel: [ 1188.623891]  [__netdev_alloc_skb+34/80] __netdev_alloc_skb+0x22/0x50
Dec 16 17:27:36 localhost kernel: [ 1188.623909]  [__kmalloc_track_caller+153/160] __kmalloc_track_caller+0x99/0xa0
Dec 16 17:27:36 localhost kernel: [ 1188.623921]  [__netdev_alloc_skb+34/80] __netdev_alloc_skb+0x22/0x50
Dec 16 17:27:36 localhost kernel: [ 1188.623934]  [__alloc_skb+87/288] __alloc_skb+0x57/0x120
Dec 16 17:27:36 localhost kernel: [ 1188.623947]  [__netdev_alloc_skb+34/80] __netdev_alloc_skb+0x22/0x50
Dec 16 17:27:36 localhost kernel: [ 1188.623959]  [<e08503cd>] rtl8169_rx_fill+0xbd/0x1d0 [r8169]
Dec 16 17:27:36 localhost kernel: [ 1188.623973]  [handle_IRQ_event+48/96] handle_IRQ_event+0x30/0x60
Dec 16 17:27:36 localhost kernel: [ 1188.623995]  [<e0850a47>] rtl8169_rx_interrupt+0x567/0x590 [r8169]
Dec 16 17:27:36 localhost kernel: [ 1188.624019]  [<e08511ad>] rtl8169_interrupt+0x34d/0x410 [r8169]
Dec 16 17:27:36 localhost kernel: [ 1188.624044]  [handle_IRQ_event+48/96] handle_IRQ_event+0x30/0x60
Dec 16 17:27:36 localhost kernel: [ 1188.624055]  [handle_level_irq+131/272] handle_level_irq+0x83/0x110
Dec 16 17:27:36 localhost kernel: [ 1188.624067]  [do_IRQ+59/112] do_IRQ+0x3b/0x70
Dec 16 17:27:36 localhost kernel: [ 1188.624094]  [common_interrupt+35/48] common_interrupt+0x23/0x30
Dec 16 17:27:36 localhost kernel: [ 1188.624112]  [schedule+752/2192] schedule+0x2f0/0x890
Dec 16 17:27:36 localhost kernel: [ 1188.624140]  [tick_nohz_restart_sched_tick+250/320] tick_nohz_restart_sched_tick+0xfa/0x140
Dec 16 17:27:36 localhost kernel: [ 1188.624166]  [default_idle+0/96] default_idle+0x0/0x60
Dec 16 17:27:36 localhost kernel: [ 1188.624177]  [cpu_idle+157/224] cpu_idle+0x9d/0xe0
Dec 16 17:27:36 localhost kernel: [ 1188.624188]  [start_kernel+805/944] start_kernel+0x325/0x3b0
Dec 16 17:27:36 localhost kernel: [ 1188.624211]  [unknown_bootoption+0/608] unknown_bootoption+0x0/0x260
Dec 16 17:27:36 localhost kernel: [ 1188.624227]  =======================
Dec 16 17:27:36 localhost kernel: [ 1188.624232] Mem-info:
Dec 16 17:27:36 localhost kernel: [ 1188.624237] DMA per-cpu:
Dec 16 17:27:36 localhost kernel: [ 1188.624244] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Dec 16 17:27:36 localhost kernel: [ 1188.624251] Normal per-cpu:
Dec 16 17:27:36 localhost kernel: [ 1188.624258] CPU    0: Hot: hi:  186, btch:  31 usd:  20   Cold: hi:   62, btch:  15 usd:  57
Dec 16 17:27:36 localhost kernel: [ 1188.624270] Active:85648 inactive:35547 dirty:6239 writeback:0 unstable:0
Dec 16 17:27:36 localhost kernel: [ 1188.624274]  free:825 slab:5042 mapped:89788 pagetables:299 bounce:0
Dec 16 17:27:36 localhost kernel: [ 1188.624286] DMA free:1996kB min:88kB low:108kB high:132kB active:8924kB inactive:1204kB present:16256kB pages_scanned:0 all_unreclaimable? no
Dec 16 17:27:36 localhost kernel: [ 1188.624294] lowmem_reserve[]: 0 491 491
Dec 16 17:27:36 localhost kernel: [ 1188.624307] Normal free:1304kB min:2788kB low:3484kB high:4180kB active:333668kB inactive:140984kB present:502860kB pages_scanned:940 all_unreclaimable? no
Dec 16 17:27:36 localhost kernel: [ 1188.624316] lowmem_reserve[]: 0 0 0
Dec 16 17:27:36 localhost kernel: [ 1188.624323] DMA: 13*4kB 21*8kB 39*16kB 10*32kB 3*64kB 1*128kB 0*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1996kB
Dec 16 17:27:36 localhost kernel: [ 1188.624346] Normal: 197*4kB 2*8kB 2*16kB 1*32kB 1*64kB 1*128kB 1*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 1316kB
Dec 16 17:27:36 localhost kernel: [ 1188.624371] Swap cache: add 16837, delete 16483, find 1144/1532, race 0+0
Dec 16 17:27:36 localhost kernel: [ 1188.624378] Free swap  = 409648kB
Dec 16 17:27:36 localhost kernel: [ 1188.624382] Total swap = 465844kB
Dec 16 17:27:36 localhost kernel: [ 1188.624387] Free swap:       409648kB
Dec 16 17:27:36 localhost kernel: [ 1188.647311] 130800 pages of RAM
Dec 16 17:27:36 localhost kernel: [ 1188.647317] 0 pages of HIGHMEM
Dec 16 17:27:36 localhost kernel: [ 1188.647322] 2115 reserved pages
Dec 16 17:27:36 localhost kernel: [ 1188.647326] 188310 pages shared
Dec 16 17:27:36 localhost kernel: [ 1188.647331] 354 pages swap cached
Dec 16 17:27:36 localhost kernel: [ 1188.647335] 6239 pages dirty
Dec 16 17:27:36 localhost kernel: [ 1188.647339] 0 pages writeback
Dec 16 17:27:36 localhost kernel: [ 1188.647344] 89788 pages mapped
Dec 16 17:27:36 localhost kernel: [ 1188.647348] 5042 pages slab
Dec 16 17:27:36 localhost kernel: [ 1188.647352] 299 pages pagetables
Dec 16 17:27:36 localhost kernel: [ 1216.511448] printk: 10696059 messages suppressed.
Dec 16 17:27:36 localhost kernel: [ 1216.511468] swapper: page allocation failure. order:1, mode:0x4020
Dec 16 17:27:36 localhost kernel: [ 1216.511501]  [__alloc_pages+800/832] __alloc_pages+0x320/0x340
Dec 16 17:27:36 localhost kernel: [ 1216.511546]  [__slab_alloc+293/1264] __slab_alloc+0x125/0x4f0
Dec 16 17:27:36 localhost kernel: [ 1216.511578]  [__netdev_alloc_skb+34/80] __netdev_alloc_skb+0x22/0x50
Dec 16 17:27:36 localhost kernel: [ 1216.511596]  [__kmalloc_track_caller+153/160] __kmalloc_track_caller+0x99/0xa0
Dec 16 17:27:36 localhost kernel: [ 1216.511608]  [__netdev_alloc_skb+34/80] __netdev_alloc_skb+0x22/0x50
Dec 16 17:27:36 localhost kernel: [ 1216.511621]  [__alloc_skb+87/288] __alloc_skb+0x57/0x120
Dec 16 17:27:36 localhost kernel: [ 1216.511634]  [__netdev_alloc_skb+34/80] __netdev_alloc_skb+0x22/0x50
Dec 16 17:27:36 localhost kernel: [ 1216.511646]  [<e08503cd>] rtl8169_rx_fill+0xbd/0x1d0 [r8169]
Dec 16 17:27:36 localhost kernel: [ 1216.511688]  [<e0850a47>] rtl8169_rx_interrupt+0x567/0x590 [r8169]
Dec 16 17:27:36 localhost kernel: [ 1216.511712]  [<e08511ad>] rtl8169_interrupt+0x34d/0x410 [r8169]
Dec 16 17:27:36 localhost kernel: [ 1216.511738]  [handle_IRQ_event+48/96] handle_IRQ_event+0x30/0x60
Dec 16 17:27:36 localhost kernel: [ 1216.511751]  [handle_level_irq+131/272] handle_level_irq+0x83/0x110
Dec 16 17:27:36 localhost kernel: [ 1216.511764]  [do_IRQ+59/112] do_IRQ+0x3b/0x70
Dec 16 17:27:36 localhost kernel: [ 1216.511786]  [common_interrupt+35/48] common_interrupt+0x23/0x30
Dec 16 17:27:36 localhost kernel: [ 1216.511804]  [schedule+752/2192] schedule+0x2f0/0x890
Dec 16 17:27:36 localhost kernel: [ 1216.511833]  [tick_nohz_restart_sched_tick+250/320] tick_nohz_restart_sched_tick+0xfa/0x140
Dec 16 17:27:36 localhost kernel: [ 1216.511860]  [default_idle+0/96] default_idle+0x0/0x60
Dec 16 17:27:36 localhost kernel: [ 1216.511871]  [cpu_idle+157/224] cpu_idle+0x9d/0xe0
Dec 16 17:27:36 localhost kernel: [ 1216.511883]  [start_kernel+805/944] start_kernel+0x325/0x3b0
Dec 16 17:27:36 localhost kernel: [ 1216.511902]  [unknown_bootoption+0/608] unknown_bootoption+0x0/0x260
Dec 16 17:27:36 localhost kernel: [ 1216.511920]  =======================
Dec 16 17:27:36 localhost kernel: [ 1216.511924] Mem-info:
Dec 16 17:27:36 localhost kernel: [ 1216.511929] DMA per-cpu:
Dec 16 17:27:36 localhost kernel: [ 1216.511936] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Dec 16 17:27:36 localhost kernel: [ 1216.511943] Normal per-cpu:
Dec 16 17:27:36 localhost kernel: [ 1216.511950] CPU    0: Hot: hi:  186, btch:  31 usd:  20   Cold: hi:   62, btch:  15 usd:  60
Dec 16 17:27:36 localhost kernel: [ 1216.511962] Active:85623 inactive:35514 dirty:6239 writeback:0 unstable:0
Dec 16 17:27:36 localhost kernel: [ 1216.511967]  free:867 slab:5042 mapped:89788 pagetables:299 bounce:0
Dec 16 17:27:36 localhost kernel: [ 1216.511980] DMA free:1996kB min:88kB low:108kB high:132kB active:8928kB inactive:1204kB present:16256kB pages_scanned:68 all_unreclaimable? no
Dec 16 17:27:36 localhost kernel: [ 1216.511989] lowmem_reserve[]: 0 491 491
Dec 16 17:27:36 localhost kernel: [ 1216.512002] Normal free:1472kB min:2788kB low:3484kB high:4180kB active:333564kB inactive:140852kB present:502860kB pages_scanned:1171 all_unreclaimable? no
Dec 16 17:27:36 localhost kernel: [ 1216.512010] lowmem_reserve[]: 0 0 0
Dec 16 17:27:36 localhost kernel: [ 1216.512018] DMA: 13*4kB 21*8kB 39*16kB 10*32kB 3*64kB 1*128kB 0*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1996kB
Dec 16 17:27:36 localhost kernel: [ 1216.512040] Normal: 242*4kB 2*8kB 2*16kB 1*32kB 1*64kB 1*128kB 1*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 1496kB
Dec 16 17:27:36 localhost kernel: [ 1216.512066] Swap cache: add 16837, delete 16483, find 1144/1532, race 0+0
Dec 16 17:27:36 localhost kernel: [ 1216.512072] Free swap  = 409648kB
Dec 16 17:27:36 localhost kernel: [ 1216.512077] Total swap = 465844kB
Dec 16 17:27:36 localhost kernel: [ 1216.512081] Free swap:       409648kB
Dec 16 17:27:36 localhost kernel: [ 1216.534961] 130800 pages of RAM
Dec 16 17:27:36 localhost kernel: [ 1216.534969] 0 pages of HIGHMEM
Dec 16 17:27:36 localhost kernel: [ 1216.534974] 2115 reserved pages
Dec 16 17:27:36 localhost kernel: [ 1216.534978] 188310 pages shared
Dec 16 17:27:36 localhost kernel: [ 1216.534983] 354 pages swap cached
Dec 16 17:27:36 localhost kernel: [ 1216.534987] 6239 pages dirty
Dec 16 17:27:36 localhost kernel: [ 1216.534991] 0 pages writeback
Dec 16 17:27:36 localhost kernel: [ 1216.534996] 89788 pages mapped
Dec 16 17:27:36 localhost kernel: [ 1216.535001] 5042 pages slab
Dec 16 17:27:36 localhost kernel: [ 1216.535005] 299 pages pagetables
Dec 16 17:27:36 localhost kernel: [ 1216.535059] swapper: page allocation failure. order:1, mode:0x4020
Dec 16 17:27:36 localhost kernel: [ 1216.535084]  [__alloc_pages+800/832] __alloc_pages+0x320/0x340
Dec 16 17:27:36 localhost kernel: [ 1216.535142]  [__slab_alloc+293/1264] __slab_alloc+0x125/0x4f0
Dec 16 17:27:36 localhost kernel: [ 1216.535180]  [__netdev_alloc_skb+34/80] __netdev_alloc_skb+0x22/0x50
Dec 16 17:27:36 localhost kernel: [ 1216.535201]  [__kmalloc_track_caller+153/160] __kmalloc_track_caller+0x99/0xa0
Dec 16 17:27:36 localhost kernel: [ 1216.535212]  [__netdev_alloc_skb+34/80] __netdev_alloc_skb+0x22/0x50
Dec 16 17:27:36 localhost kernel: [ 1216.535230]  [__alloc_skb+87/288] __alloc_skb+0x57/0x120
Dec 16 17:27:36 localhost kernel: [ 1216.535247]  [__netdev_alloc_skb+34/80] __netdev_alloc_skb+0x22/0x50
Dec 16 17:27:36 localhost kernel: [ 1216.535262]  [<e08503cd>] rtl8169_rx_fill+0xbd/0x1d0 [r8169]
Dec 16 17:27:36 localhost kernel: [ 1216.535309]  [<e0850a47>] rtl8169_rx_interrupt+0x567/0x590 [r8169]
Dec 16 17:27:36 localhost kernel: [ 1216.535341]  [<e08511ad>] rtl8169_interrupt+0x34d/0x410 [r8169]
Dec 16 17:27:36 localhost kernel: [ 1216.535377]  [handle_IRQ_event+48/96] handle_IRQ_event+0x30/0x60
Dec 16 17:27:36 localhost kernel: [ 1216.535393]  [handle_level_irq+131/272] handle_level_irq+0x83/0x110
Dec 16 17:27:36 localhost kernel: [ 1216.535410]  [do_IRQ+59/112] do_IRQ+0x3b/0x70
Dec 16 17:27:36 localhost kernel: [ 1216.535438]  [common_interrupt+35/48] common_interrupt+0x23/0x30
Dec 16 17:27:36 localhost kernel: [ 1216.535463]  [schedule+752/2192] schedule+0x2f0/0x890
Dec 16 17:27:36 localhost kernel: [ 1216.535507]  [tick_nohz_restart_sched_tick+250/320] tick_nohz_restart_sched_tick+0xfa/0x140
Dec 16 17:27:36 localhost kernel: [ 1216.535534]  [default_idle+0/96] default_idle+0x0/0x60
Dec 16 17:27:36 localhost kernel: [ 1216.535548]  [cpu_idle+157/224] cpu_idle+0x9d/0xe0
Dec 16 17:27:36 localhost kernel: [ 1216.535563]  [start_kernel+805/944] start_kernel+0x325/0x3b0
Dec 16 17:27:36 localhost kernel: [ 1216.535585]  [unknown_bootoption+0/608] unknown_bootoption+0x0/0x260
Dec 16 17:27:36 localhost kernel: [ 1216.535610]  =======================
Dec 16 17:27:36 localhost kernel: [ 1216.535615] Mem-info:
Dec 16 17:27:36 localhost kernel: [ 1216.535619] DMA per-cpu:
Dec 16 17:27:36 localhost kernel: [ 1216.535626] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Dec 16 17:27:36 localhost kernel: [ 1216.535634] Normal per-cpu:
Dec 16 17:27:36 localhost kernel: [ 1216.535641] CPU    0: Hot: hi:  186, btch:  31 usd:  20   Cold: hi:   62, btch:  15 usd:  60
Dec 16 17:27:36 localhost kernel: [ 1216.535653] Active:85623 inactive:35514 dirty:6239 writeback:0 unstable:0
Dec 16 17:27:36 localhost kernel: [ 1216.535657]  free:867 slab:5042 mapped:89788 pagetables:299 bounce:0
Dec 16 17:27:36 localhost kernel: [ 1216.535669] DMA free:1996kB min:88kB low:108kB high:132kB active:8928kB inactive:1204kB present:16256kB pages_scanned:68 all_unreclaimable? no
Dec 16 17:27:36 localhost kernel: [ 1216.535677] lowmem_reserve[]: 0 491 491
Dec 16 17:27:36 localhost kernel: [ 1216.535690] Normal free:1472kB min:2788kB low:3484kB high:4180kB active:333564kB inactive:140852kB present:502860kB pages_scanned:1171 all_unreclaimable? no
Dec 16 17:27:36 localhost kernel: [ 1216.535699] lowmem_reserve[]: 0 0 0
Dec 16 17:27:36 localhost kernel: [ 1216.535706] DMA: 13*4kB 21*8kB 39*16kB 10*32kB 3*64kB 1*128kB 0*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1996kB
Dec 16 17:27:36 localhost kernel: [ 1216.535728] Normal: 242*4kB 2*8kB 2*16kB 1*32kB 1*64kB 1*128kB 1*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 1496kB
Dec 16 17:27:36 localhost kernel: [ 1216.535753] Swap cache: add 16837, delete 16483, find 1144/1532, race 0+0
Dec 16 17:27:36 localhost kernel: [ 1216.535760] Free swap  = 409648kB
Dec 16 17:27:36 localhost kernel: [ 1216.535764] Total swap = 465844kB
Dec 16 17:27:36 localhost kernel: [ 1216.535769] Free swap:       409648kB
Dec 16 17:27:36 localhost kernel: [ 1216.558819] 130800 pages of RAM
Dec 16 17:27:36 localhost kernel: [ 1216.558825] 0 pages of HIGHMEM
Dec 16 17:27:36 localhost kernel: [ 1216.558829] 2115 reserved pages
Dec 16 17:27:36 localhost kernel: [ 1216.558833] 188310 pages shared
Dec 16 17:27:36 localhost kernel: [ 1216.558838] 354 pages swap cached
Dec 16 17:27:36 localhost kernel: [ 1216.558843] 6239 pages dirty
Dec 16 17:27:36 localhost kernel: [ 1216.558847] 0 pages writeback
Dec 16 17:27:36 localhost kernel: [ 1216.558851] 89788 pages mapped
Dec 16 17:27:36 localhost kernel: [ 1216.558855] 5042 pages slab
Dec 16 17:27:36 localhost kernel: [ 1216.558859] 299 pages pagetables
Dec 16 17:27:36 localhost kernel: [ 1216.558880] swapper: page allocation failure. order:1, mode:0x4020
Dec 16 17:27:36 localhost kernel: [ 1216.558901]  [__alloc_pages+800/832] __alloc_pages+0x320/0x340
Dec 16 17:27:36 localhost kernel: [ 1216.558956]  [__slab_alloc+293/1264] __slab_alloc+0x125/0x4f0
Dec 16 17:27:36 localhost kernel: [ 1216.558993]  [__netdev_alloc_skb+34/80] __netdev_alloc_skb+0x22/0x50
Dec 16 17:27:36 localhost kernel: [ 1216.559011]  [__kmalloc_track_caller+153/160] __kmalloc_track_caller+0x99/0xa0
Dec 16 17:27:36 localhost kernel: [ 1216.559023]  [__netdev_alloc_skb+34/80] __netdev_alloc_skb+0x22/0x50
Dec 16 17:27:36 localhost kernel: [ 1216.559043]  [__alloc_skb+87/288] __alloc_skb+0x57/0x120
Dec 16 17:27:36 localhost kernel: [ 1216.559059]  [__netdev_alloc_skb+34/80] __netdev_alloc_skb+0x22/0x50
Dec 16 17:27:36 localhost kernel: [ 1216.559074]  [<e08503cd>] rtl8169_rx_fill+0xbd/0x1d0 [r8169]
Dec 16 17:27:36 localhost kernel: [ 1216.559120]  [<e0850a47>] rtl8169_rx_interrupt+0x567/0x590 [r8169]
Dec 16 17:27:36 localhost kernel: [ 1216.559152]  [<e08511ad>] rtl8169_interrupt+0x34d/0x410 [r8169]
Dec 16 17:27:36 localhost kernel: [ 1216.559186]  [handle_IRQ_event+48/96] handle_IRQ_event+0x30/0x60
Dec 16 17:27:36 localhost kernel: [ 1216.559202]  [handle_level_irq+131/272] handle_level_irq+0x83/0x110
Dec 16 17:27:36 localhost kernel: [ 1216.559217]  [do_IRQ+59/112] do_IRQ+0x3b/0x70
Dec 16 17:27:36 localhost kernel: [ 1216.559243]  [common_interrupt+35/48] common_interrupt+0x23/0x30
Dec 16 17:27:36 localhost kernel: [ 1216.559268]  [schedule+752/2192] schedule+0x2f0/0x890
Dec 16 17:27:36 localhost kernel: [ 1216.559306]  [tick_nohz_restart_sched_tick+250/320] tick_nohz_restart_sched_tick+0xfa/0x140
Dec 16 17:27:36 localhost kernel: [ 1216.559332]  [default_idle+0/96] default_idle+0x0/0x60
Dec 16 17:27:36 localhost kernel: [ 1216.559345]  [cpu_idle+157/224] cpu_idle+0x9d/0xe0
Dec 16 17:27:36 localhost kernel: [ 1216.559361]  [start_kernel+805/944] start_kernel+0x325/0x3b0
Dec 16 17:27:36 localhost kernel: [ 1216.559379]  [unknown_bootoption+0/608] unknown_bootoption+0x0/0x260
Dec 16 17:27:36 localhost kernel: [ 1216.559402]  =======================
Dec 16 17:27:36 localhost kernel: [ 1216.559406] Mem-info:
Dec 16 17:27:36 localhost kernel: [ 1216.559410] DMA per-cpu:
Dec 16 17:27:36 localhost kernel: [ 1216.559418] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Dec 16 17:27:36 localhost kernel: [ 1216.559425] Normal per-cpu:
Dec 16 17:27:36 localhost kernel: [ 1216.559432] CPU    0: Hot: hi:  186, btch:  31 usd:  20   Cold: hi:   62, btch:  15 usd:  60
Dec 16 17:27:36 localhost kernel: [ 1216.559444] Active:85623 inactive:35514 dirty:6239 writeback:0 unstable:0
Dec 16 17:27:36 localhost kernel: [ 1216.559448]  free:867 slab:5042 mapped:89788 pagetables:299 bounce:0
Dec 16 17:27:36 localhost kernel: [ 1216.559459] DMA free:1996kB min:88kB low:108kB high:132kB active:8928kB inactive:1204kB present:16256kB pages_scanned:68 all_unreclaimable? no
Dec 16 17:27:36 localhost kernel: [ 1216.559468] lowmem_reserve[]: 0 491 491
Dec 16 17:27:36 localhost kernel: [ 1216.559481] Normal free:1472kB min:2788kB low:3484kB high:4180kB active:333564kB inactive:140852kB present:502860kB pages_scanned:1171 all_unreclaimable? no
Dec 16 17:27:36 localhost kernel: [ 1216.559489] lowmem_reserve[]: 0 0 0
Dec 16 17:27:36 localhost kernel: [ 1216.559496] DMA: 13*4kB 21*8kB 39*16kB 10*32kB 3*64kB 1*128kB 0*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1996kB
Dec 16 17:27:36 localhost kernel: [ 1216.559519] Normal: 242*4kB 2*8kB 2*16kB 1*32kB 1*64kB 1*128kB 1*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 1496kB
Dec 16 17:27:36 localhost kernel: [ 1216.559544] Swap cache: add 16837, delete 16483, find 1144/1532, race 0+0
Dec 16 17:27:36 localhost kernel: [ 1216.559551] Free swap  = 409648kB
Dec 16 17:27:36 localhost kernel: [ 1216.559555] Total swap = 465844kB
Dec 16 17:27:36 localhost kernel: [ 1216.559560] Free swap:       409648kB
Dec 16 17:27:36 localhost kernel: [ 1216.582383] 130800 pages of RAM
Dec 16 17:27:36 localhost kernel: [ 1216.582388] 0 pages of HIGHMEM
Dec 16 17:27:36 localhost kernel: [ 1216.582393] 2115 reserved pages
Dec 16 17:27:36 localhost kernel: [ 1216.582397] 188310 pages shared
Dec 16 17:27:36 localhost kernel: [ 1216.582402] 354 pages swap cached
Dec 16 17:27:36 localhost kernel: [ 1216.582408] 6239 pages dirty
Dec 16 17:27:36 localhost kernel: [ 1216.582411] 0 pages writeback
Dec 16 17:27:36 localhost kernel: [ 1216.582416] 89788 pages mapped
Dec 16 17:27:36 localhost kernel: [ 1216.582420] 5042 pages slab
Dec 16 17:27:36 localhost kernel: [ 1216.582424] 299 pages pagetables
Dec 16 17:27:36 localhost kernel: [ 1216.582477] swapper: page allocation failure. order:1, mode:0x4020
Dec 16 17:27:36 localhost kernel: [ 1216.582500]  [__alloc_pages+800/832] __alloc_pages+0x320/0x340
Dec 16 17:27:36 localhost kernel: [ 1216.582554]  [__slab_alloc+293/1264] __slab_alloc+0x125/0x4f0
Dec 16 17:27:36 localhost kernel: [ 1216.582591]  [__netdev_alloc_skb+34/80] __netdev_alloc_skb+0x22/0x50
Dec 16 17:27:36 localhost kernel: [ 1216.582610]  [__kmalloc_track_caller+153/160] __kmalloc_track_caller+0x99/0xa0
Dec 16 17:27:36 localhost kernel: [ 1216.582621]  [__netdev_alloc_skb+34/80] __netdev_alloc_skb+0x22/0x50
Dec 16 17:27:36 localhost kernel: [ 1216.582639]  [__alloc_skb+87/288] __alloc_skb+0x57/0x120
Dec 16 17:27:36 localhost kernel: [ 1216.582655]  [__netdev_alloc_skb+34/80] __netdev_alloc_skb+0x22/0x50
Dec 16 17:27:36 localhost kernel: [ 1216.582671]  [<e08503cd>] rtl8169_rx_fill+0xbd/0x1d0 [r8169]
Dec 16 17:27:36 localhost kernel: [ 1216.582717]  [<e0850a47>] rtl8169_rx_interrupt+0x567/0x590 [r8169]
Dec 16 17:27:36 localhost kernel: [ 1216.582749]  [<e08511ad>] rtl8169_interrupt+0x34d/0x410 [r8169]
Dec 16 17:27:36 localhost kernel: [ 1216.582785]  [handle_IRQ_event+48/96] handle_IRQ_event+0x30/0x60
Dec 16 17:27:36 localhost kernel: [ 1216.582801]  [handle_level_irq+131/272] handle_level_irq+0x83/0x110
Dec 16 17:27:36 localhost kernel: [ 1216.582816]  [do_IRQ+59/112] do_IRQ+0x3b/0x70
Dec 16 17:27:36 localhost kernel: [ 1216.582845]  [common_interrupt+35/48] common_interrupt+0x23/0x30
Dec 16 17:27:36 localhost kernel: [ 1216.582871]  [schedule+752/2192] schedule+0x2f0/0x890
Dec 16 17:27:36 localhost kernel: [ 1216.582912]  [tick_nohz_restart_sched_tick+250/320] tick_nohz_restart_sched_tick+0xfa/0x140
Dec 16 17:27:36 localhost kernel: [ 1216.582939]  [default_idle+0/96] default_idle+0x0/0x60
Dec 16 17:27:36 localhost kernel: [ 1216.582953]  [cpu_idle+157/224] cpu_idle+0x9d/0xe0
Dec 16 17:27:36 localhost kernel: [ 1216.582968]  [start_kernel+805/944] start_kernel+0x325/0x3b0
Dec 16 17:27:36 localhost kernel: [ 1216.582989]  [unknown_bootoption+0/608] unknown_bootoption+0x0/0x260
Dec 16 17:27:36 localhost kernel: [ 1216.583013]  =======================
Dec 16 17:27:36 localhost kernel: [ 1216.583018] Mem-info:
Dec 16 17:27:36 localhost kernel: [ 1216.583023] DMA per-cpu:
Dec 16 17:27:36 localhost kernel: [ 1216.583030] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Dec 16 17:27:36 localhost kernel: [ 1216.583037] Normal per-cpu:
Dec 16 17:27:36 localhost kernel: [ 1216.583045] CPU    0: Hot: hi:  186, btch:  31 usd:  20   Cold: hi:   62, btch:  15 usd:  60
Dec 16 17:27:36 localhost kernel: [ 1216.583057] Active:85623 inactive:35514 dirty:6239 writeback:0 unstable:0
Dec 16 17:27:36 localhost kernel: [ 1216.583061]  free:867 slab:5042 mapped:89788 pagetables:299 bounce:0
Dec 16 17:27:36 localhost kernel: [ 1216.583074] DMA free:1996kB min:88kB low:108kB high:132kB active:8928kB inactive:1204kB present:16256kB pages_scanned:68 all_unreclaimable? no
Dec 16 17:27:36 localhost kernel: [ 1216.583082] lowmem_reserve[]: 0 491 491
Dec 16 17:27:36 localhost kernel: [ 1216.583095] Normal free:1472kB min:2788kB low:3484kB high:4180kB active:333564kB inactive:140852kB present:502860kB pages_scanned:1171 all_unreclaimable? no
Dec 16 17:27:36 localhost kernel: [ 1216.583104] lowmem_reserve[]: 0 0 0
Dec 16 17:27:36 localhost kernel: [ 1216.583111] DMA: 13*4kB 21*8kB 39*16kB 10*32kB 3*64kB 1*128kB 0*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1996kB
Dec 16 17:27:36 localhost kernel: [ 1216.583133] Normal: 242*4kB 2*8kB 2*16kB 1*32kB 1*64kB 1*128kB 1*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 1496kB
Dec 16 17:27:36 localhost kernel: [ 1216.583159] Swap cache: add 16837, delete 16483, find 1144/1532, race 0+0
Dec 16 17:27:36 localhost kernel: [ 1216.583166] Free swap  = 409648kB
Dec 16 17:27:36 localhost kernel: [ 1216.583171] Total swap = 465844kB
Dec 16 17:27:36 localhost kernel: [ 1216.583176] Free swap:       409648kB
Dec 16 17:27:36 localhost kernel: [ 1216.605927] 130800 pages of RAM
Dec 16 17:27:36 localhost kernel: [ 1216.605932] 0 pages of HIGHMEM
Dec 16 17:27:36 localhost kernel: [ 1216.605937] 2115 reserved pages
Dec 16 17:27:36 localhost kernel: [ 1216.605941] 188310 pages shared
Dec 16 17:27:36 localhost kernel: [ 1216.605946] 354 pages swap cached
Dec 16 17:27:36 localhost kernel: [ 1216.605950] 6239 pages dirty
Dec 16 17:27:36 localhost kernel: [ 1216.605954] 0 pages writeback
Dec 16 17:27:36 localhost kernel: [ 1216.605958] 89788 pages mapped
Dec 16 17:27:36 localhost kernel: [ 1216.605963] 5042 pages slab
Dec 16 17:27:36 localhost kernel: [ 1216.605967] 299 pages pagetables
Dec 16 17:27:36 localhost kernel: [ 1216.605988] swapper: page allocation failure. order:1, mode:0x4020
Dec 16 17:27:36 localhost kernel: [ 1216.606013]  [__alloc_pages+800/832] __alloc_pages+0x320/0x340
Dec 16 17:27:36 localhost kernel: [ 1216.606066]  [__slab_alloc+293/1264] __slab_alloc+0x125/0x4f0
Dec 16 17:27:36 localhost kernel: [ 1216.606105]  [__netdev_alloc_skb+34/80] __netdev_alloc_skb+0x22/0x50
Dec 16 17:27:36 localhost kernel: [ 1216.606122]  [__kmalloc_track_caller+153/160] __kmalloc_track_caller+0x99/0xa0
Dec 16 17:27:36 localhost kernel: [ 1216.606135]  [__netdev_alloc_skb+34/80] __netdev_alloc_skb+0x22/0x50
Dec 16 17:27:36 localhost kernel: [ 1216.606153]  [__alloc_skb+87/288] __alloc_skb+0x57/0x120
Dec 16 17:27:36 localhost kernel: [ 1216.606170]  [__netdev_alloc_skb+34/80] __netdev_alloc_skb+0x22/0x50
Dec 16 17:27:36 localhost kernel: [ 1216.606185]  [<e08503cd>] rtl8169_rx_fill+0xbd/0x1d0 [r8169]
Dec 16 17:27:36 localhost kernel: [ 1216.606237]  [<e0850a47>] rtl8169_rx_interrupt+0x567/0x590 [r8169]
Dec 16 17:27:36 localhost kernel: [ 1216.606270]  [<e08511ad>] rtl8169_interrupt+0x34d/0x410 [r8169]
Dec 16 17:27:36 localhost kernel: [ 1216.606307]  [handle_IRQ_event+48/96] handle_IRQ_event+0x30/0x60
Dec 16 17:27:36 localhost kernel: [ 1216.606324]  [handle_level_irq+131/272] handle_level_irq+0x83/0x110
Dec 16 17:27:36 localhost kernel: [ 1216.606340]  [do_IRQ+59/112] do_IRQ+0x3b/0x70
Dec 16 17:27:36 localhost kernel: [ 1216.606369]  [common_interrupt+35/48] common_interrupt+0x23/0x30
Dec 16 17:27:36 localhost kernel: [ 1216.606396]  [schedule+752/2192] schedule+0x2f0/0x890
Dec 16 17:27:36 localhost kernel: [ 1216.606437]  [tick_nohz_restart_sched_tick+250/320] tick_nohz_restart_sched_tick+0xfa/0x140
Dec 16 17:27:36 localhost kernel: [ 1216.606467]  [default_idle+0/96] default_idle+0x0/0x60
Dec 16 17:27:36 localhost kernel: [ 1216.606482]  [cpu_idle+157/224] cpu_idle+0x9d/0xe0
Dec 16 17:27:36 localhost kernel: [ 1216.606498]  [start_kernel+805/944] start_kernel+0x325/0x3b0
Dec 16 17:27:36 localhost kernel: [ 1216.606519]  [unknown_bootoption+0/608] unknown_bootoption+0x0/0x260
Dec 16 17:27:36 localhost kernel: [ 1216.606543]  =======================
Dec 16 17:27:36 localhost kernel: [ 1216.606547] Mem-info:
Dec 16 17:27:36 localhost kernel: [ 1216.606551] DMA per-cpu:
Dec 16 17:27:36 localhost kernel: [ 1216.606559] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Dec 16 17:27:36 localhost kernel: [ 1216.606566] Normal per-cpu:
Dec 16 17:27:36 localhost kernel: [ 1216.606573] CPU    0: Hot: hi:  186, btch:  31 usd:  20   Cold: hi:   62, btch:  15 usd:  60
Dec 16 17:27:36 localhost kernel: [ 1216.606585] Active:85623 inactive:35514 dirty:6239 writeback:0 unstable:0
Dec 16 17:27:36 localhost kernel: [ 1216.606590]  free:867 slab:5042 mapped:89788 pagetables:299 bounce:0
Dec 16 17:27:36 localhost kernel: [ 1216.606601] DMA free:1996kB min:88kB low:108kB high:132kB active:8928kB inactive:1204kB present:16256kB pages_scanned:68 all_unreclaimable? no
Dec 16 17:27:36 localhost kernel: [ 1216.606609] lowmem_reserve[]: 0 491 491
Dec 16 17:27:36 localhost kernel: [ 1216.606623] Normal free:1472kB min:2788kB low:3484kB high:4180kB active:333564kB inactive:140852kB present:502860kB pages_scanned:1171 all_unreclaimable? no
Dec 16 17:27:36 localhost kernel: [ 1216.606631] lowmem_reserve[]: 0 0 0
Dec 16 17:27:36 localhost kernel: [ 1216.606638] DMA: 13*4kB 21*8kB 39*16kB 10*32kB 3*64kB 1*128kB 0*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1996kB
Dec 16 17:27:36 localhost kernel: [ 1216.606661] Normal: 242*4kB 2*8kB 2*16kB 1*32kB 1*64kB 1*128kB 1*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 1496kB
Dec 16 17:27:36 localhost kernel: [ 1216.606686] Swap cache: add 16837, delete 16483, find 1144/1532, race 0+0
Dec 16 17:27:36 localhost kernel: [ 1216.606692] Free swap  = 409648kB
Dec 16 17:27:36 localhost kernel: [ 1216.606697] Total swap = 465844kB
Dec 16 17:27:36 localhost kernel: [ 1216.606701] Free swap:       409648kB
Dec 16 17:27:36 localhost kernel: [ 1216.629751] 130800 pages of RAM
Dec 16 17:27:36 localhost kernel: [ 1216.629758] 0 pages of HIGHMEM
Dec 16 17:27:36 localhost kernel: [ 1216.629762] 2115 reserved pages
Dec 16 17:27:36 localhost kernel: [ 1216.629767] 188310 pages shared
Dec 16 17:27:36 localhost kernel: [ 1216.629771] 354 pages swap cached
Dec 16 17:27:36 localhost kernel: [ 1216.629776] 6239 pages dirty
Dec 16 17:27:36 localhost kernel: [ 1216.629780] 0 pages writeback
Dec 16 17:27:36 localhost kernel: [ 1216.629784] 89788 pages mapped
Dec 16 17:27:36 localhost kernel: [ 1216.629789] 5042 pages slab
Dec 16 17:27:36 localhost kernel: [ 1216.629793] 299 pages pagetables
Dec 16 17:27:36 localhost kernel: [ 1247.638928] Clocksource tsc unstable (delta = 56243866411 ns)
Dec 16 17:27:36 localhost kernel: [ 1247.640788] Time: acpi_pm clocksource has been installed.
Dec 16 17:47:34 localhost syslogd 1.4.1#21ubuntu3: restart.
Dec 16 17:47:34 localhost kernel: Inspecting /boot/System.map-2.6.22-14-generic
Dec 16 17:47:34 localhost kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
```

---

### Post by jaakan on 2007-12-16
Whats in /var/log/kern.log and message at around the same time? 

and cat /proc/interrupts


is there a lot of harddrive activity right before it locks up?

---

### Post by Blinkiz on 2007-12-16
The /var/log/kern.log looks like the syslog files above.

cat /proc/interrupts maybe 1 minute before the crash:
```
           CPU0       
  0:     205200    XT-PIC-XT        timer
  1:          2    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  6:          3    XT-PIC-XT        floppy
  7:          0    XT-PIC-XT        parport0
  8:          3    XT-PIC-XT        rtc
  9:      96641    XT-PIC-XT        acpi, sata_sil24
 10:    2525120    XT-PIC-XT        eth0
 11:          0    XT-PIC-XT        uhci_hcd:usb1
 14:       5886    XT-PIC-XT        libata
 15:         88    XT-PIC-XT        libata
NMI:          0 
LOC:          0 
ERR:          0
MIS:          0
```

"htop" exacly when the crash happen:
```

  CPU[#######################***************************100.0%]     Tasks: 52 total, 2 running
  Mem[||||||#*****************************************53/502MB]     Load average: 2.94 2.55 1.50 
  Swp[||||||                                          45/454MB]     Uptime: 00:22:29

  PID USER     PRI  NI  VIRT   RES   SHR S CPU% MEM%   TIME+  Command                                                               
 5063 niklas    18   0  441M  333M  327M R 69.9 66.3  9:59.05 rtorrent
 5144 niklas    15   0  2556  1272   960 R  1.6  0.2  0:03.12 htop
 5162 niklas    16   0  2360  1136   864 S  0.8  0.2  0:01.16 top
 4197 syslog    18   0  1912   680   556 S  0.0  0.1  0:01.37 /sbin/syslogd -u syslog
 4254 klog      15   0  2508   860   408 S  0.0  0.2  0:01.06 /sbin/klogd -P /var/run/klogd/kmsg
 4252 root      18   0  1836   532   444 S  0.0  0.1  0:01.28 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
 4584 niklas    15   0  8188  1060   904 S  1.2  0.2  0:00.72 sshd: niklas@pts/0,pts/3,pts/4
 5039 niklas    15   0  4404  1380   700 S  0.0  0.3  0:00.26 SCREEN -fn -dm -S rtorrent
 4602 niklas    15   0 13240  5148  1888 S  0.0  1.0  0:01.00 python /home/niklas/rssdler/rssdler.py -d -c /home/niklas/rssdler/conf
 4660 root      15   0  6416  1096   816 S  0.0  0.2  0:00.09 /usr/sbin/nmbd -D
 5164 niklas    15   0  4004  1140   900 S  0.0  0.2  0:00.01 screen
 5066 niklas    16   0  5840  1688  1424 S  0.0  0.3  0:00.51 -bash
 5146 niklas    16   0  5844  2900  1408 S  0.0  0.6  0:00.52 -bash
    1 root      18   0  2948  1800   476 S  0.0  0.3  0:02.33 /sbin/init
 2433 root      16  -4  2956   512   408 S  0.0  0.1  0:00.91 /sbin/udevd --daemon
 3533 dhcp      19  -2  2420   316   220 S  0.0  0.1  0:00.00 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth0.pid -lf /var/lib
 3754 daemon    15   0  1812   492   408 S  0.0  0.1  0:00.00 /sbin/portmap
 3773 statd     25   0  1872   668   580 S  0.0  0.1  0:00.00 /sbin/rpc.statd --port 4000
 3982 root      18   0  1696   520   448 S  0.0  0.1  0:00.00 /sbin/getty 38400 tty4
 3983 root      18   0  1696   520   448 S  0.0  0.1  0:00.00 /sbin/getty 38400 tty5
 3985 root      18   0  1696   516   448 S  0.0  0.1  0:00.00 /sbin/getty 38400 tty2
 3993 root      18   0  1692   516   448 S  0.0  0.1  0:00.00 /sbin/getty 38400 tty3
 3996 root      18   0  1692   516   448 S  0.0  0.1  0:00.00 /sbin/getty 38400 tty1
 3997 root      18   0  1696   520   448 S  0.0  0.1  0:00.00 /sbin/getty 38400 tty6
 4163 root      18   0  2436  1252   668 S  0.0  0.2  0:00.01 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket          
 4275 messageb  15   0  2776   580   532 S  0.0  0.1  0:00.07 /usr/bin/dbus-daemon --system
 4291 root      15   0  4364   828   776 S  0.0  0.2  0:00.04 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkMan
 4305 root      25   0  3252   552   552 S  0.0  0.1  0:00.00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/
 4318 root      24   0  3084   444   444 S  0.0  0.1  0:00.00 /usr/bin/system-tools-backends
 4319 root      25   0  2772   796   796 S  0.0  0.2  0:00.00 dbus-daemon --session --print-address --nofork
 4338 haldaemo  18   0  5516  1156   888 S  0.0  0.2  0:00.45 /usr/sbin/hald
 4339 root      25   0  3096   572   572 S  0.0  0.1  0:00.01 hald-runner
 4393 root      18   0  5284   616   616 S  0.0  0.1  0:00.00 /usr/sbin/sshd
 4405 haldaemo  22   0  2156   624   624 S  0.0  0.1  0:00.00 hald-addon-keyboard: listening on /dev/input/event2
 4425 haldaemo  22   0  2160   624   624 S  0.0  0.1  0:00.00 hald-addon-keyboard: listening on /dev/input/event3
 4429 haldaemo  25   0  2156   612   612 S  0.0  0.1  0:00.01 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket      
 4458 root      18   0  5800   848   848 S  0.0  0.2  0:00.03 /usr/sbin/cupsd
 4557 root      25   0  2484   152   152 S  0.0  0.0  0:00.00 /usr/sbin/rpc.mountd --p 4002
 4582 root      16   0  8060  1532  1508 S  0.0  0.3  0:00.06 sshd: niklas [priv]
 4585 niklas    15   0  5840  3192  1424 S  0.0  0.6  0:00.71 -bash
 4662 root      18   0  9896  2032  1440 S  0.0  0.4  0:00.02 /usr/sbin/smbd -D
 4719 avahi     15   0  2732  1060   860 S  0.0  0.2  0:00.01 avahi-daemon: running [fileserver.local]
 4720 avahi     25   0  2732   444   272 S  0.0  0.1  0:00.00 avahi-daemon: chroot helper
 4734 root      18   0  9896   868   276 S  0.0  0.2  0:00.00 /usr/sbin/smbd -D
 4735 root      18   0  1992   608   516 S  0.0  0.1  0:00.42 /usr/sbin/dhcdbd --system
 4771 daemon    25   0  1960   428   308 S  0.0  0.1  0:00.00 /usr/sbin/atd
 4785 root      18   0  2332   908   728 S  0.0  0.2  0:00.01 /usr/sbin/cron
 4910 root      18   0 10260  2600  1876 S  0.0  0.5  0:00.19 /usr/sbin/smbd -D
 5040 niklas    15   0  5840  3168  1400 S  0.0  0.6  0:00.37 /bin/bash
 5061 root      19   0  3412  1024   808 S  0.0  0.2  0:00.01 sg users -c rtorrent
 5062 niklas    19   0  1752   476   412 S  0.0  0.1  0:00.00 sh -c rtorrent
 5128 niklas    17   0  5840  2636  1408 S  0.0  0.5  0:00.51 -bash                                                                 

```

"top" exacly when the crash happen:
```
top - 22:37:44 up 22 min,  5 users,  load average: 2.94, 2.55, 1.50
Tasks:  89 total,   2 running,  87 sleeping,   0 stopped,   0 zombie
Cpu(s): 41.9%us, 25.6%sy,  0.0%ni,  0.0%id, 12.3%wa,  8.0%hi, 12.3%si,  0.0%st
Mem:    514804k total,   509012k used,     5792k free,      760k buffers
Swap:   465844k total,    46276k used,   419568k free,   455788k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                
 5063 niklas    20   0  429m 318m 312m R 70.6 63.3   9:58.25 rtorrent                                                               
 5107 root      15   0     0    0    0 S  7.6  0.0   0:06.12 pdflush                                                                
 5144 niklas    15   0  2552 1272  960 S  2.0  0.2   0:03.12 htop                                                                   
  114 root      10  -5     0    0    0 D  1.7  0.0   0:26.11 kswapd0                                                                
 4584 niklas    15   0  8188 1060  904 S  1.7  0.2   0:00.72 sshd                                                                   
 5162 niklas    15   0  2360 1136  864 R  0.7  0.2   0:01.16 top                                                                    
 3627 root      10  -5     0    0    0 S  0.3  0.0   0:00.86 kjournald                                                              
    1 root      18   0  2948 1800  476 S  0.0  0.3   0:02.34 init                                                                   
    2 root      11  -5     0    0    0 S  0.0  0.0   0:01.86 kthreadd                                                               
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                            
    4 root      34  19     0    0    0 S  0.0  0.0   0:00.04 ksoftirqd/0                                                            
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                             
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.15 events/0                                                               
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 khelper                                                                
   26 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0                                                              
   27 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                 
   28 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                           
   95 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                                
  166 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                                  
 1821 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                          
 1822 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                                  
 1842 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0                                                                  
 1843 root      14  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                                
 1845 root      14  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                              
 1846 root      12  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1                                                              
 1935 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_2                                                              
 1936 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_3                                                              
 1937 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_4                                                              
 1938 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_5                                                              
 2205 root      10  -5     0    0    0 S  0.0  0.0   0:01.14 kjournald                                                              
 2433 root      16  -4  2956  512  408 S  0.0  0.1   0:00.91 udevd                                                                  
 3533 dhcp      19  -2  2420  316  220 S  0.0  0.1   0:00.00 dhclient3                                                              
 3754 daemon    15   0  1812  492  408 S  0.0  0.1   0:00.00 portmap                                                                
 3773 statd     25   0  1872  668  580 S  0.0  0.1   0:00.00 rpc.statd                                                              
 3982 root      18   0  1696  520  448 S  0.0  0.1   0:00.00 getty                                                                  
 3983 root      18   0  1696  520  448 S  0.0  0.1   0:00.00 getty                                                                  
 3985 root      18   0  1696  516  448 S  0.0  0.1   0:00.00 getty                                                                  
 3993 root      18   0  1692  516  448 S  0.0  0.1   0:00.00 getty                                                                  
 3996 root      18   0  1692  516  448 S  0.0  0.1   0:00.00 getty                                                                  
 3997 root      18   0  1696  520  448 S  0.0  0.1   0:00.00 getty                                                                  
 4163 root      18   0  2436 1252  668 S  0.0  0.2   0:00.01 acpid                                                                  
 4197 syslog    18   0  1912  680  556 S  0.0  0.1   0:01.37 syslogd                                                                
 4252 root      18   0  1836  532  444 S  0.0  0.1   0:01.29 dd                                                                     
 4254 klog      15   0  2508  860  408 S  0.0  0.2   0:01.07 klogd                                                                  
 4275 messageb  15   0  2776  580  532 S  0.0  0.1   0:00.07 dbus-daemon                                                            
 4291 root      15   0  4364  828  776 S  0.0  0.2   0:00.04 NetworkManager                                                         
 4305 root      25   0  3252  552  552 S  0.0  0.1   0:00.00 NetworkManagerD                                                        
 4318 root      24   0  3084  444  444 S  0.0  0.1   0:00.00 system-tools-ba                                                        
 4319 root      25   0  2772  796  796 S  0.0  0.2   0:00.00 dbus-daemon                                                            
 4338 haldaemo  18   0  5516 1156  888 S  0.0  0.2   0:00.46 hald                                                                   
 4339 root      25   0  3096  572  572 S  0.0  0.1   0:00.01 hald-runner                                                            
 4393 root      18   0  5284  616  616 S  0.0  0.1   0:00.00 sshd                                                                   
 4405 haldaemo  22   0  2156  624  624 S  0.0  0.1   0:00.00 hald-addon-keyb                                                        
 4425 haldaemo  22   0  2160  624  624 S  0.0  0.1   0:00.00 hald-addon-keyb                                                        
 4429 haldaemo  25   0  2156  612  612 S  0.0  0.1   0:00.01 hald-addon-acpi                                                        
```

"rtorrent" exacly when the crash happen:
```
                                          *** rTorrent 0.7.9/0.11.9 - fileserver:5063 ***
[View: main]
  Assxxxxxxxxx.xxxxxxx.x
            4175.8 / 6783.6 MB Rate:   0.8 / 4480.6 KB Uploaded:     0.5 MB [57%]  0d  0:09 [T  R: 0.00]

   Call.xxxxxxxxx.xxxxxxx.x
            2275.8 / 6521.7 MB Rate:   0.0 / 820.6 KB Uploaded:     0.0 MB [34%]  0d  1:28 [T  R: 0.00]

   The.xxxxxxxxx.xxxxxxx.x 
 [OPEN]      94.0 /  699.8 MB Rate:   0.0 /   0.0 KB Uploaded:     0.0 MB                 [T  R: 0.00]
  Hashing: Checking hash [93%]


[Throttle 9500/9500 KB] [Rate   8.2/5323.2 KB] [Port: 50501]             [U 1/1910] [D 128/1910] [H 0/32] [S 24/175/768] [F 128/128]
```

The "crash" is a totally freeze and I most reboot by pressing the reset button on the computer. Why is ubuntu crashing this hard?

---

### Post by assan on 2008-02-03
Hi,

I think that problem is with SATA driver. My computer was crashing when some torrent application was running. Another guess is connection between SATA and torrent. There is a lot of read/write action and disk is very slow and it crashes system.
Please check if system will crash if you will not start torrent up/download?
If it will be true please read about SATA disk problems. Developers now about this bug, it has something to do with kernel. But there is not fix at the moment.
Many user have similar problems with sata drives.

---

### Post by Blinkiz on 2008-02-04
I have changed my hardware totally so I don't have this problem anymore.

---

