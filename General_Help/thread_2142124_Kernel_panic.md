---
title: "Kernel panic"
date: 2013-05-04
forum: General Help
---

### Post by Crisopa on 2013-05-04
Last year i installed Lubuntu in a very old computer with the minimum specs imaginable and it ran fine, especially after a memory upgrade (from 500MB to 2GB).
Lubuntu brought the machine back to life, but i thought it could use another little push, so i also upgraded the processor (from [this]("http://ark.intel.com/es/products/27424/Intel-Pentium-4-Processor-1_60-GHz-256K-Cache-400-MHz-FSB") to [this]("http://ark.intel.com/es/products/27453/Intel-Pentium-4-Processor-511-1M-Cache-2_80A-GHz-533-MHz-FSB")) and it did well throughout the year, but it took a little vacation from December to January, because nobody cared anymore.
Three months later, however, i tried to boot it up, but it would crash randomly, so i thought this was a chance to try out the new Lubuntu that just came out, but the Live CD would crash as well when "trying" Lubuntu before install (something i wanted to do to wipe the HDD). Anyway, i tried using Windows XP SP2 to wipe the drive (which it did), and then tried to install the OS, but it BSOD'd (IRQL_NOT_LESS_OR_EQUAL or something); after a while, i tried with SP3 and got another BSOD, after which i gave up with Windows and tried again with Lubuntu Live CD.

This is the message i got this time:

```
[    7.373085] Stack:
[    7.373131]  00000000 00000000 00000000 00000000 00000000 00000000 00000000 000000a
[    7.373888] Call Trace:
[    7.373944] [<c104ca80>] ? local_bh_enable_ip+0x90/0x90
[    7.373995] <IRQ>
[    7.374042] [<c104ce55>] ? irq_exit+0x95/0xa0
[    7.374185] [<c15d076e>] ? smp_apic_timer_interrupt+0x5e/0x8d
[    7.374240] [<c10699c7>] ? hrtimer_start+0x27/0x30
[    7.374300] [<c15c9815>] ? apic_timer_interrupt+0x31/0x38
[    7.374359] [<c14900e0>] ? __get_uuid_cell+0x50/0x80
[    7.374418] [<c1017e28>] ? mwait_idle+0x78/0x1b0
[    7.374475] [<c1018716>] ? cpu_idle+0xb6/0xe0
[    7.374534] [<c159f715>] ? rest_init+0x5d/0x68
[    7.374592] [<c18ae9be>] ? start_kernel+0x35d/0x363
[    7.374648] [<c18ae4ed>] ? do_early_param+0x80/0x80
[    7.374704] [<c18ae303>] ? i386_start_kernel+0xa6/0xad
[    7.374758] [<c18ae303>] Code: f0 01 74 f2 89 e0 89 fe 25 00 e0 ff ff 81 ee 00 6a 83 c1 8(number-offscreen) 8d 

40 14 c1 fe 02 64 ff 04 b5 c4 58 96 c1 89 45 ec 3e 8d 74 26 00 89 f8 <ff> 17 3(number-offscreen) 8d 74 26 00 89 e0 

25 00 e0 ff ff 8b 40 14 39 45 ec 0f
[    7.376003] EIP: [<c104cb05>] __do_softirq+0x85/0x180 SS:ESO 0068:f500bfc4
[    7.377827] ---[ end trace bc0269e4a278a1ab ]---
[    7.377882] Kernel panic - not syncing: Fatal exception in interrupt
```

My bet is this is hardware related, but what component exactly? Memory tests seem to be fine and this machine GPU is embedded, so what else could it be?
[I]
Help me, Obi-Wan Kenobi. You're my only hope. [/I]

---

### Post by Bashing-om on 2013-05-04
Crisopa; Hi !

Maybe just a maybe .... BIOS is not talking to the updated processor ?

Might try updating BIOS and play around with BIOS defaults ?
[INDENT=2]
just my thought

[/INDENT]

---

### Post by sanderj on 2013-05-05
> **Crisopa said:**
> Memory tests seem to be fine

Did you run memtest86 from the GRUB menu for a few hours?

---

