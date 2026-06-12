---
title: "Problem with freezing and kernel errors"
date: 2007-08-16
forum: General Help
---

### Post by anebi on 2007-08-16
Hi, 

i have a some questions, because i can not find out some solution for this, maybe here you will can help me.

We have problems with servers , they are freezing and we can't understand where is the problem. sometimes in the logs we get messages like this:

> 
Aug 15 08:29:53 odin kernel: ntpd invoked oom-killer: gfp_mask=0x201d2, order=0, oomkilladj=0
Aug 15 08:29:53 odin kernel: 
Aug 15 08:29:53 odin kernel: Call Trace:
Aug 15 08:29:54 odin kernel:  [<ffffffff8106e2d6>] out_of_memory+0x70/0x2ea
Aug 15 08:29:54 odin kernel:  [<ffffffff8106ffc9>] __alloc_pages+0x24b/0x2d4
Aug 15 08:29:54 odin kernel:  [<ffffffff8102d141>] default_wake_function+0x0/0xe
Aug 15 08:29:54 odin kernel:  [<ffffffff81071873>] __do_page_cache_readahead+0xa1/0x1df
Aug 15 08:29:54 odin kernel:  [<ffffffff8126be74>] __wait_on_bit_lock+0x5b/0x66
Aug 15 08:29:54 odin kernel:  [<ffffffff880cabf1>] :dm_mod:dm_any_congested+0x38/0x3f
Aug 15 08:29:54 odin kernel:  [<ffffffff8106d71b>] filemap_nopage+0x13f/0x2c1
Aug 15 08:29:54 odin kernel:  [<ffffffff8107965f>] __handle_mm_fault+0x1fa/0xcfa
Aug 15 08:29:54 odin kernel:  [<ffffffff8126ef8b>] do_page_fault+0x443/0x7b4
Aug 15 08:29:54 odin kernel:  [<ffffffff81009972>] sys_rt_sigreturn+0x281/0x34f
Aug 15 08:29:55 odin kernel:  [<ffffffff81009a08>] sys_rt_sigreturn+0x317/0x34f
Aug 15 08:29:55 odin kernel:  [<ffffffff8126d4dd>] error_exit+0x0/0x84
Aug 15 08:29:55 odin kernel: 
Aug 15 08:29:55 odin kernel: Mem-info:
Aug 15 08:29:55 odin kernel: Node 0 DMA per-cpu:
Aug 15 08:29:56 odin kernel: CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Aug 15 08:29:56 odin kernel: CPU    1: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Aug 15 08:29:56 odin kernel: Node 0 DMA32 per-cpu:
Aug 15 08:29:56 odin kernel: CPU    0: Hot: hi:  186, btch:  31 usd:  25   Cold: hi:   62, btch:  15 usd:  44
Aug 15 08:29:56 odin kernel: CPU    1: Hot: hi:  186, btch:  31 usd: 114   Cold: hi:   62, btch:  15 usd:  50
Aug 15 08:29:56 odin kernel: Node 0 Normal per-cpu:
Aug 15 08:29:56 odin kernel: CPU    0: Hot: hi:  186, btch:  31 usd:  19   Cold: hi:   62, btch:  15 usd:  61
Aug 15 08:29:57 odin kernel: CPU    1: Hot: hi:  186, btch:  31 usd:  50   Cold: hi:   62, btch:  15 usd:  59
Aug 15 08:29:57 odin kernel: Active:453307 inactive:501457 dirty:0 writeback:0 unstable:0
Aug 15 08:29:57 odin kernel:  free:5206 slab:10533 mapped:19 pagetables:30217 bounce:0
Aug 15 08:29:59 odin kernel: Node 0 DMA free:10780kB min:20kB low:24kB high:28kB active:0kB inactive:0kB present:10260kB pages_scanned:0 all_unreclaimable? yes
Aug 15 08:29:59 odin kernel: lowmem_reserve[]: 0 3511 4016
Aug 15 08:29:59 odin kernel: Node 0 DMA32 free:9080kB min:7080kB low:8848kB high:10620kB active:1538828kB inactive:1901380kB present:3595360kB pages_scanned:15126949 all_unrecla
imable? yes
Aug 15 08:29:59 odin kernel: lowmem_reserve[]: 0 0 505
Aug 15 08:29:59 odin kernel: Node 0 Normal free:964kB min:1016kB low:1268kB high:1524kB active:274400kB inactive:104448kB present:517120kB pages_scanned:2637130 all_unreclaimable? yes


We get this kind of messages. we tested for bad rams and rootkis, everything is ok. And the main problem is that when the server is frozen, it doesn't logged what is happening after restart, we can't see what is wrong. 

What can we do in this situation, how to understand which aplication make the problems with out-of-memory?

There writes killed mysql or irqbalance, but sometimes i suppose this is not right, or maybe i'm wrong...

I hope that you will help me to solve these problems

Thanks in advanced!

---

