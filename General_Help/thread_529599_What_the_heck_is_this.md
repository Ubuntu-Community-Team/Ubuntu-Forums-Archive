---
title: "What the heck is this?"
date: 2007-08-19
forum: General Help
---

### Post by herbster on 2007-08-19
I have Simple Backup set to do a backup at 10am every Sunday, so I just got home and see this in my desktop terminal:
```
bobby:~$ 
Message from syslogd@feistybox at Sun Aug 19 10:11:44 2007 ...
feistybox kernel: [1182500.199839] Oops: 0002 [#1]

Message from syslogd@feistybox at Sun Aug 19 10:11:44 2007 ...
feistybox kernel: [1182500.199841] SMP 

Message from syslogd@feistybox at Sun Aug 19 10:11:44 2007 ...
feistybox kernel: [1182500.199992] CPU:    0

Message from syslogd@feistybox at Sun Aug 19 10:11:44 2007 ...
feistybox kernel: [1182500.199993] EIP:    0060:[shrink_active_list+227/1056]    Tainted: P      VLI

Message from syslogd@feistybox at Sun Aug 19 10:11:44 2007 ...
feistybox kernel: [1182500.200013] EIP is at shrink_active_list+0xe3/0x420

Message from syslogd@feistybox at Sun Aug 19 10:11:44 2007 ...
feistybox kernel: [1182500.200017] eax: e0613821   ebx: c1fff9f8   ecx: c1fff9e0   edx: 0003a020

Message from syslogd@feistybox at Sun Aug 19 10:11:44 2007 ...
feistybox kernel: [1182500.200022] esi: c03aa900   edi: c1bebef8   ebp: c1bebf00   esp: c1bebe90

Message from syslogd@feistybox at Sun Aug 19 10:11:44 2007 ...
feistybox kernel: [1182500.200028] ds: 007b   es: 007b   ss: 0068

Message from syslogd@feistybox at Sun Aug 19 10:11:44 2007 ...
feistybox kernel: [1182500.199995] EFLAGS: 00010282   (2.6.20-16-generic #2)

Message from syslogd@feistybox at Sun Aug 19 10:11:44 2007 ...
feistybox kernel: [1182500.200033] Process kswapd0 (pid: 149, ti=c1bea000 task=c1b98a90 task.ti=c1bea000)

Message from syslogd@feistybox at Sun Aug 19 10:11:44 2007 ...
feistybox kernel: [1182500.200037] Stack: c1bebf08 c1bebef0 c03aae84 c03aae80 00000020 0000003c 00000000 00000000 

Message from syslogd@feistybox at Sun Aug 19 10:11:44 2007 ...
feistybox kernel: [1182500.200051]        00000000 00000001 c1430da0 c1685fc0 c165a720 c1430d80 c11c93e0 c1691100 

Message from syslogd@feistybox at Sun Aug 19 10:11:44 2007 ...
feistybox kernel: [1182500.200061]        c1691120 c15c05c0 c15c05e0 c115e580 c115e5a0 c10fce40 c10fce60 f8f3344e 

Message from syslogd@feistybox at Sun Aug 19 10:11:44 2007 ...
feistybox kernel: [1182500.200071] Call Trace:

Message from syslogd@feistybox at Sun Aug 19 10:11:44 2007 ...
feistybox kernel: [1182500.200129]  [<f8f3344e>] mb_cache_shrink_fn+0x1e/0x100 [mbcache]

Message from syslogd@feistybox at Sun Aug 19 10:11:44 2007 ...
feistybox kernel: [1182500.200167]  [shrink_zone+222/256] shrink_zone+0xde/0x100

Message from syslogd@feistybox at Sun Aug 19 10:11:44 2007 ...
feistybox kernel: [1182500.200193]  [kswapd+808/1072] kswapd+0x328/0x430

Message from syslogd@feistybox at Sun Aug 19 10:11:44 2007 ...
feistybox kernel: [1182500.200255]  [autoremove_wake_function+0/80] autoremove_wake_function+0x0/0x50

Message from syslogd@feistybox at Sun Aug 19 10:11:44 2007 ...
feistybox kernel: [1182500.200286]  [kswapd+0/1072] kswapd+0x0/0x430

Message from syslogd@feistybox at Sun Aug 19 10:11:44 2007 ...
feistybox kernel: [1182500.200290]  [kthread+186/240] kthread+0xba/0xf0

Message from syslogd@feistybox at Sun Aug 19 10:11:44 2007 ...
feistybox kernel: [1182500.200301]  [kthread+0/240] kthread+0x0/0xf0

Message from syslogd@feistybox at Sun Aug 19 10:11:44 2007 ...
feistybox kernel: [1182500.200313]  [kernel_thread_helper+7/16] kernel_thread_helper+0x7/0x10

Message from syslogd@feistybox at Sun Aug 19 10:11:44 2007 ...
feistybox kernel: [1182500.200336]  =======================

Message from syslogd@feistybox at Sun Aug 19 10:11:44 2007 ...
feistybox kernel: [1182500.200338] Code: 86 86 80 05 00 00 fb 90 8d b4 26 00 00 00 00 90 3b 6c 24 70 74 7c e8 6d d9 18 00 8b 4c 24 74 83 e9 18 8d 59 18 8b 51 18 8b 43 04 <89> 42 04 89 10 c7 43 04 00 02 20 00 8b 41 08 c7 41 18 00 01 10 

Message from syslogd@feistybox at Sun Aug 19 10:11:44 2007 ...
feistybox kernel: [1182500.200401] EIP: [shrink_active_list+227/1056] shrink_active_list+0xe3/0x420 SS:ESP 0068:c1bebe90
```

The time is 10:11 so it was during or at the end of the backup. I have never seen this before.

And the backup went fine, and my box is running just fine as well.

:? :?

---

