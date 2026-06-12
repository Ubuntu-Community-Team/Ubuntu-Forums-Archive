---
title: "Very very slow boot"
date: 2008-03-18
forum: General Help
---

### Post by webit on 2008-03-18
At first - sorry for my english I'll do my best :-)

Since few days (about 2 weeks, I think) my Ubuntu 7.10 boots very slow. I had 6.04 and upgrading every release till currtent - 7.10.

I don't know what happened - nothing changed in hardware so no new debs were installed. I checked forum several times and saw there is debug log. I will print below only part of it

```
Mar 18 18:56:40 webit kernel: [    0.000000] Entering add_active_range(0, 0, 524272) 0 entries of 256 used
Mar 18 18:56:40 webit kernel: [    0.000000] On node 0 totalpages: 524272
Mar 18 18:56:40 webit kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Mar 18 18:56:40 webit kernel: [    0.000000]   DMA zone: 0 pages reserved
Mar 18 18:56:40 webit kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Mar 18 18:56:40 webit kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Mar 18 18:56:40 webit kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Mar 18 18:56:40 webit kernel: [    0.000000]   HighMem zone: 2303 pages used for memmap
Mar 18 18:56:40 webit kernel: [    0.000000]   HighMem zone: 292593 pages, LIFO batch:31
Mar 18 18:56:40 webit kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Mar 18 18:56:40 webit kernel: [    0.000000] ACPI: IRQ9 used by override.
Mar 18 18:56:40 webit kernel: [    0.000000] mapped APIC to ffffd000 (fee00000)
Mar 18 18:56:40 webit kernel: [    0.000000] mapped IOAPIC to ffffc000 (fec00000)
Mar 18 18:56:40 webit kernel: [   17.397279] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000

```

Please take a look on last line (it took 17 seconds, isn't it?) Why does it take so long?

---

### Post by webit on 2008-03-18
Let me add some additional informations about my system:

```

webit@webit:~$ uname -a
Linux webit 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux
webit@webit:~$ dmesg | grep ailed
[   26.137821] PM: Resume from disk failed.

```

Seems system started after 156 seconds (part from /var/log/debug):

```
Mar 18 18:58:05 webit kernel: [  156.450721] ra0: no IPv6 routers present
```

---

### Post by webit on 2008-03-19
Nobody can help me? :(
Maybe some ideas what is wrong?

---

