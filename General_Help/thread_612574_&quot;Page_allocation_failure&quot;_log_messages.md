---
title: "&quot;Page allocation failure&quot; log messages"
date: 2007-11-14
forum: General Help
---

### Post by dmalinovsky on 2007-11-14
Recently following weird message began to appear in my logs:

```
Nov 14 13:07:00 localhost kernel: [19625.248000] Xorg: page allocation failure. order:1, mode:0x4020
Nov 14 13:07:00 localhost kernel: [19625.268000] nautilus: page allocation failure. order:1, mode:0x4020
```

I also have following in the logs:

```
Nov 14 13:06:58 localhost kernel: [19625.084000]  [__alloc_pages+769/800] __alloc_pages+0x301/0x320
Nov 14 13:06:58 localhost kernel: [19625.084000]  [__slab_alloc+362/976] __slab_alloc+0x16a/0x3d0
Nov 14 13:06:58 localhost kernel: [19625.084000]  [ip_rcv+685/1296] ip_rcv+0x2ad/0x510
Nov 14 13:06:58 localhost kernel: [19625.084000]  [<e08d7057>] rhine_interrupt+0x647/0xb00 [via_rhine]
Nov 14 13:06:58 localhost kernel: [19625.084000]  [__kmalloc_track_caller+149/160] __kmalloc_track_caller+0x95/0xa0
Nov 14 13:06:58 localhost kernel: [19625.084000]  [<e08d7057>] rhine_interrupt+0x647/0xb00 [via_rhine]
Nov 14 13:06:58 localhost kernel: [19625.084000]  [__alloc_skb+87/288] __alloc_skb+0x57/0x120
Nov 14 13:06:58 localhost kernel: [19625.084000]  [<e08d7057>] rhine_interrupt+0x647/0xb00 [via_rhine]
Nov 14 13:06:58 localhost kernel: [19625.084000]  [handle_IRQ_event+48/96] handle_IRQ_event+0x30/0x60
Nov 14 13:06:58 localhost kernel: [19625.084000]  [handle_level_irq+75/176] handle_level_irq+0x4b/0xb0
Nov 14 13:06:58 localhost kernel: [19625.084000]  [do_IRQ+55/112] do_IRQ+0x37/0x70
Nov 14 13:06:58 localhost kernel: [19625.084000]  [common_interrupt+35/48] common_interrupt+0x23/0x30
Nov 14 13:06:58 localhost kernel: [19625.084000]  =======================
Nov 14 13:06:58 localhost kernel: [19625.084000] Mem-info:
Nov 14 13:06:58 localhost kernel: [19625.084000] DMA per-cpu:
Nov 14 13:06:58 localhost kernel: [19625.084000] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Nov 14 13:06:58 localhost kernel: [19625.084000] Normal per-cpu:
Nov 14 13:06:58 localhost kernel: [19625.084000] CPU    0: Hot: hi:  186, btch:  31 usd:  29   Cold: hi:   62, btch:  15 usd:  58
Nov 14 13:06:58 localhost kernel: [19625.084000] Active:110163 inactive:7778 dirty:6106 writeback:0 unstable:0
Nov 14 13:06:58 localhost kernel: [19625.084000]  free:4113 slab:4639 mapped:16956 pagetables:515 bounce:0
Nov 14 13:06:58 localhost kernel: [19625.084000] DMA free:2008kB min:88kB low:108kB high:132kB active:8144kB inactive:1528kB present:16256kB pages_scanned:0 all_unreclaimable? no
Nov 14 13:06:58 localhost kernel: [19625.084000] lowmem_reserve[]: 0 492 492
Nov 14 13:06:58 localhost kernel: [19625.084000] Normal free:14444kB min:2792kB low:3488kB high:4188kB active:432508kB inactive:29584kB present:503876kB pages_scanned:757 all_unreclaimable? no
Nov 14 13:06:58 localhost kernel: [19625.084000] lowmem_reserve[]: 0 0 0
Nov 14 13:06:58 localhost kernel: [19625.084000] DMA: 190*4kB 0*8kB 0*16kB 1*32kB 1*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 0*4096kB = 2008kB
Nov 14 13:06:58 localhost kernel: [19625.084000] Normal: 3479*4kB 0*8kB 1*16kB 0*32kB 0*64kB 0*128kB 0*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 14444kB
Nov 14 13:06:58 localhost kernel: [19625.084000] Swap cache: add 8868, delete 8864, find 11/15, race 0+0
Nov 14 13:06:58 localhost kernel: [19625.084000] Free swap  = 1474716kB
Nov 14 13:06:58 localhost kernel: [19625.084000] Total swap = 1510068kB
Nov 14 13:06:58 localhost kernel: [19625.084000] Free swap:       1474716kB
Nov 14 13:06:58 localhost kernel: [19625.084000] 131056 pages of RAM
Nov 14 13:06:58 localhost kernel: [19625.084000] 0 pages of HIGHMEM
Nov 14 13:06:58 localhost kernel: [19625.084000] 2043 reserved pages
Nov 14 13:06:58 localhost kernel: [19625.084000] 107470 pages shared
Nov 14 13:06:58 localhost kernel: [19625.084000] 4 pages swap cached
Nov 14 13:06:58 localhost kernel: [19625.084000] 6106 pages dirty
Nov 14 13:06:58 localhost kernel: [19625.084000] 0 pages writeback
Nov 14 13:06:58 localhost kernel: [19625.084000] 16956 pages mapped
Nov 14 13:06:58 localhost kernel: [19625.084000] 4639 pages slab
Nov 14 13:06:58 localhost kernel: [19625.084000] 515 pages pagetables
Nov 14 13:07:00 localhost kernel: [19625.104000] eth0: Inconsistent Rx descriptor chain.
```

Does anyone have slightest idea what's happening?  I'm afraid something may be wrong with hardware—my PC is rather old already.

I also found something similar in [this thread]("http://ubuntuforums.org/showthread.php?t=457290"), but I have nothing about ext3 file system in the logs.

---

### Post by tageiru on 2007-12-03
I am seeing this on my system as well. It is the interrupt handler for incoming network packets for via rhine cards that cause the message. When it is processing packets it needs to make a GFP_ATOMIC allocation that (for some reason) fails. The good news is that this isn't dangerous. It will just cause dropped packets (and thus lowering network transmission speed).

I have quite a few dropped packets according to ifconfig.

```
RX packets:77586188 errors:0 dropped:404 overruns:0 frame:0
```

There is also a bug in the kernels memory allocation system that was recently fixed in the kernel (2.6.23.4) that caused some priority allocations to be down prioritised, which might cause priority allocations to fail.

---

### Post by dmalinovsky on 2007-12-06
Thanks!

---

### Post by RaZoR1394 on 2008-03-09
I'm having the same problem on Hardy and it happens when I download with hellanzb. The harddrive is working very hard it seems and I'm maxing my 100Mbit connection so that may be one of the causes.

---

