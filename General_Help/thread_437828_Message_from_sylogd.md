---
title: "Message from sylogd"
date: 2007-05-09
forum: General Help
---

### Post by Toe Knee on 2007-05-09
Hi,
  Does anyone have any idea what is causing syslogd to dump the following into the terminal.
Is it a bug that I should file?

```
Message from syslogd@pepe at Wed May  9 04:48:47 2007 ...
pepe kernel: [117112.580000]  [generic_drop_inode+114/368] generic_drop_inode+0x72/0x170

Message from syslogd@pepe at Wed May  9 04:48:47 2007 ...
pepe kernel: [117112.580000] Process kswapd0 (pid: 137, ti=debc6000 task=deb4f560 task.ti=debc6000)

Message from syslogd@pepe at Wed May  9 04:48:47 2007 ...
pepe kernel: [117112.580000] Call Trace:

Message from syslogd@pepe at Wed May  9 04:48:47 2007 ...
pepe kernel: [117112.580000]        c01886e7 c016052d 000032cb 00000000 00000000 00000019 00000000 c0427e80 

Message from syslogd@pepe at Wed May  9 04:48:47 2007 ...
pepe kernel: [117112.580000]        c0188504 dca6c25c 00000021 c018865b 0000aa50 00000094 dffeeac0 000000d0 

Message from syslogd@pepe at Wed May  9 04:48:47 2007 ...
pepe kernel: [117112.580000] Stack: d7bf5400 d8c6226c d7bf5400 c018a412 d8c6226c 00000021 c0189906 dca6c25c 

Message from syslogd@pepe at Wed May  9 04:48:47 2007 ...
pepe kernel: [117112.580000] ds: 007b   es: 007b   ss: 0068

Message from syslogd@pepe at Wed May  9 04:48:47 2007 ...
pepe kernel: [117112.580000] esi: d8c623a0   edi: 00000000   ebp: d7bf563c   esp: debc7ec4

Message from syslogd@pepe at Wed May  9 04:48:47 2007 ...
pepe kernel: [117112.580000] eax: 00000000   ebx: d8c6226c   ecx: d8c62e30   edx: 00000000

Message from syslogd@pepe at Wed May  9 04:48:47 2007 ...
pepe kernel: [117112.580000] EIP is at clear_inode+0x94/0x150

Message from syslogd@pepe at Wed May  9 04:48:47 2007 ...
pepe kernel: [117112.580000] EIP:    0060:[clear_inode+148/336]    Tainted: P      VLI

Message from syslogd@pepe at Wed May  9 04:48:47 2007 ...
pepe kernel: [117112.580000] CPU:    0

Message from syslogd@pepe at Wed May  9 04:48:47 2007 ...
pepe kernel: [117112.580000] SMP 

Message from syslogd@pepe at Wed May  9 04:48:47 2007 ...
pepe kernel: [117112.580000] Oops: 0000 [#1]

Message from syslogd@pepe at Wed May  9 04:48:47 2007 ...
pepe kernel: [117112.580000] EFLAGS: 00010286   (2.6.20-15-generic #2)

Message from syslogd@pepe at Wed May  9 04:48:47 2007 ...
pepe kernel: [117112.580000]  [iput+86/112] iput+0x56/0x70

Message from syslogd@pepe at Wed May  9 04:48:47 2007 ...
pepe kernel: [117112.580000]  [prune_one_dentry+84/128] prune_one_dentry+0x54/0x80

Message from syslogd@pepe at Wed May  9 04:48:47 2007 ...
pepe kernel: [117112.580000]  [prune_dcache+299/384] prune_dcache+0x12b/0x180

Message from syslogd@pepe at Wed May  9 04:48:47 2007 ...
pepe kernel: [117112.580000]  [shrink_dcache_memory+55/64] shrink_dcache_memory+0x37/0x40

Message from syslogd@pepe at Wed May  9 04:48:47 2007 ...
pepe kernel: [117112.580000]  [shrink_slab+285/384] shrink_slab+0x11d/0x180

Message from syslogd@pepe at Wed May  9 04:48:47 2007 ...
pepe kernel: [117112.580000]  [kswapd+838/1072] kswapd+0x346/0x430

Message from syslogd@pepe at Wed May  9 04:48:47 2007 ...
pepe kernel: [117112.580000]  [autoremove_wake_function+0/80] autoremove_wake_function+0x0/0x50

Message from syslogd@pepe at Wed May  9 04:48:47 2007 ...
pepe kernel: [117112.580000]  [kswapd+0/1072] kswapd+0x0/0x430

Message from syslogd@pepe at Wed May  9 04:48:47 2007 ...
pepe kernel: [117112.580000]  [kthread+186/240] kthread+0xba/0xf0

Message from syslogd@pepe at Wed May  9 04:48:47 2007 ...
pepe kernel: [117112.580000]  [kthread+0/240] kthread+0x0/0xf0

Message from syslogd@pepe at Wed May  9 04:48:47 2007 ...
pepe kernel: [117112.580000]  [kernel_thread_helper+7/16] kernel_thread_helper+0x7/0x10

Message from syslogd@pepe at Wed May  9 04:48:47 2007 ...
pepe kernel: [117112.580000]  =======================

Message from syslogd@pepe at Wed May  9 04:48:47 2007 ...
pepe kernel: [117112.580000] Code: 23 8b 52 04 85 d2 74 1c 8b b3 f8 00 00 00 85 f6 0f 85 ad 00 00 00 8b 8b fc 00 00 00 85 c9 0f 85 9f 00 00 00 85 c0 74 0e 8b 40 20 <8b> 50 3c 85 d2 74 04 89 d8 ff d2 0f b7 53 6a 89 d0 25 00 f0 00 

Message from syslogd@pepe at Wed May  9 04:48:47 2007 ...
pepe kernel: [117112.580000] EIP: [clear_inode+148/336] clear_inode+0x94/0x150 SS:ESP 0068:debc7ec4

```

P.S. I'm not usually up at 5am, but leave my computer on over night.  It was running things like Beagled, eclipse, mysql browser, firefox, gaim, liferea.

Thanks in advance,

---

