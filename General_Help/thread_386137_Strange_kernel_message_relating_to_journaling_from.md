---
title: "Strange kernel message relating to journaling from syslogd"
date: 2007-03-16
forum: General Help
---

### Post by retiman on 2007-03-16
I get weird kernel messages sometimes when I'm playing a movie in mplayer or copying files.  After a while my computer freezes up and I have to do a physical reboot.  Could somebody please help?

```

crema kernel: [17198185.272000] Oops: 0002 [#1]

Message from syslogd@crema at Fri Mar 16 00:55:56 2007 ...
crema kernel: [17198185.272000] Oops: 0002 [#1]

Message from syslogd@crema at Fri Mar 16 00:55:56 2007 ...
crema kernel: [17198185.272000] SMP

Message from syslogd@crema at Fri Mar 16 00:55:56 2007 ...
crema kernel: [17198185.272000] SMP

Message from syslogd@crema at Fri Mar 16 00:55:56 2007 ...
crema kernel: [ 17198185.272000] CPU:    0

Message from syslogd@crema at Fri Mar 16 00:55:56 2007 ...
crema kernel: [17198185.272000] CPU:    0

Message from syslogd@crema at Fri Mar 16 00:55:56 2007 ...
crema kernel: [ 17198185.272000] EIP is at __journal_drop_transaction+0x22/0x310 [jbd]

Message from syslogd@crema at Fri Mar 16 00:55:56 2007 ...
crema kernel: [17198185.272000] EIP is at __journal_drop_transaction+0x22/0x310 [jbd]

Message from syslogd@crema at Fri Mar 16 00:55:56 2007 ...
crema kernel: [17198185.272000] eax: c436d840   ebx: c436d840   ecx: ea4e9a2c   edx: 0036d840

Message from syslogd@crema at Fri Mar 16 00:55:56 2007 ...
crema kernel: [17198185.272000] eax: c436d840   ebx: c436d840   ecx: ea4e9a2c   edx: 0036d840

Message from syslogd@crema at Fri Mar 16 00:55:56 2007 ...
crema kernel: [17198185.272000] esi: f7c91800   edi: ea4e9c00   ebp: c436dcc0   esp: c1bb7ee8

Message from syslogd@crema at Fri Mar 16 00:55:56 2007 ...
crema kernel: [17198185.272000] esi: f7c91800   edi: ea4e9c00   ebp: c436dcc0   esp: c1bb7ee8

Message from syslogd@crema at Fri Mar 16 00:55:56 2007 ...
crema kernel: [17198185.272000] ds: 007b   es: 007b   ss: 0068

Message from syslogd@crema at Fri Mar 16 00:55:56 2007 ...
crema kernel: [17198185.272000] ds: 007b   es: 007b   ss: 0068

Message from syslogd@crema at Fri Mar 16 00:55:56 2007 ...
crema kernel: [17198185.272000] Process kjournald (pid: 3336, threadinfo=c1bb6000 task=dff76580)

Message from syslogd@crema at Fri Mar 16 00:55:56 2007 ...
crema kernel: [17198185.272000 ] Process kjournald (pid: 3336, threadinfo=c1bb6000 task=dff76580)

Message from syslogd@crema at Fri Mar 16 00:55:56 2007 ...
crema kernel: [17198185.272000] Stack: d7437414 ea4e9c00 ea4e9c00 f8997b4b c016e1da c436d840 f7c91800 f8996463

Message from syslogd@crema at Fri Mar 16 00:55:56 2007 ...
crema kernel: [17198185.272000] Stack: d7437414 ea4e9c00 ea4e9c00 f8997b4b c016e1da c436d840 f7c91800 f8996463

Message from syslogd@crema at Fri Mar 16 00:55:56 2007 ...
crema kernel: [17198185.272000]        d7437448 d50c24b0 ea4e9a2c f8994f7b 000006f7 61e54c00 003d19a7 000a0280

Message from syslogd@crema at Fri Mar 16 00:55:56 2007 ...
crema kernel: [17198185.272000]        d7437448 d50c24b0 ea4e9a2c f8994f7b 000006f7 61e54c00 003d19a7 000a0280

Message from syslogd@crema at Fri Mar 16 00:55:56 2007 ...
crema kernel: [17198185.272000]        c1bb6000 f7c91814 c436dcf8 f7c918b8 f7c91800 00000000 f7901000 00000000

Message from syslogd@crema at Fri Mar 16 00:55:56 2007 ...
crema kernel: [17198185.272000]        c1bb6000 f7c91814 c436dcf8 f7c918b8 f7c91800 00000000 f7901000 00000000

Message from syslogd@crema at Fri Mar 16 00:55:56 2007 ...
crema kernel: [17198185.272000] Call Trace:

Message from syslogd@crema at Fri Mar 16 00:55:56 2007 ...
crema kernel: [17198185.272000] Call Trace:

Message from syslogd@crema at Fri Mar 16 00:55:56 2007 ...
crema kernel: [17198185.272000]  <f8997b4b> journal_put_journal_head+0x9b/0xb0 [jbd]  <c016e1da> sync_dirty_buffer+0x8a/0xe0

Message from syslogd@crema at Fri Mar 16 00:55:56 2007 ...
crema kernel: [17198185.272000]  <f8997b4b> journal_put_journal_head+0x9b/0xb0 [jbd]  <c016e1da> sync_dirty_buffer+0x8a/0xe0

Message from syslogd@crema at Fri Mar 16 00:55:56 2007 ...
crema kernel: [17198185.272000]  <f8996463> __journal_remove_checkpoint+0x63/0x90 [jbd]  <f8994f7b> journal_commit_transaction+0x81b/0x1180 [jbd]

Message from syslogd@crema at Fri Mar 16 00:55:56 2007 ...
crema kernel: [17198185.272000]  <f8996463> __journal_remove_checkpoint+0x63/0x90 [jbd]  <f8994f7b> journal_commit_transaction+0x81b/0x1180 [jbd]

Message from syslogd@crema at Fri Mar 16 00:55:56 2007 ...
crema kernel: [17198185.272000]  <c012bb70> lock_timer_base+0x20/0x50  <f8999209> kjournald+0xa9/0x210 [jbd]

Message from syslogd@crema at Fri Mar 16 00:55:56 2007 ...
crema kernel: [17198185.272000]  <c012bb70> lock_timer_base+0x20/0x50  <f8999209> kjournald+0xa9/0x210 [jbd]

Message from syslogd@crema at Fri Mar 16 00:55:56 2007 ...
crema kernel: [17198185.272000 ]  <c0136180> autoremove_wake_function+0x0/0x50  <f8999160> kjournald+0x0/0x210 [jbd]

Message from syslogd@crema at Fri Mar 16 00:55:56 2007 ...
crema kernel: [17198185.272000]  <c0136180> autoremove_wake_function+0x0/0x50  <f8999160> kjournald+0x0/0x210 [jbd]

Message from syslogd@crema at Fri Mar 16 00:55:56 2007 ...
crema kernel: [17198185.272000]  <c0135f8b> kthread+0xab/0xe0  <c0135ee0> kthread+0x0/0xe0

Message from syslogd@crema at Fri Mar 16 00:55:56 2007 ...
crema kernel: [17198185.272000]  <c0135f8b> kthread+0xab/0xe0  <c0135ee0> kthread+0x0/0xe0

Message from syslogd@crema at Fri Mar 16 00:55:56 2007 ...
crema kernel: [17198185.272000]  <c0101005> kernel_thread_helper+0x5/0x10

Message from syslogd@crema at Fri Mar 16 00:55:56 2007 ...
crema kernel: [17198185.272000]  <c0101005> kernel_thread_helper+0x5/0x10

Message from syslogd@crema at Fri Mar 16 00:55:56 2007 ...
crema kernel: [ 17198185.272000] Code: 90 90 90 90 90 90 90 90 90 56 89 c6 53 89 d3 83 ec 14 0f b6 80 b8 00 00 00 84 c0 0f 8f de 02 00 00 8b 53 44 85 d2 74 15 8b 43 48 <89> 42 48 8b 43 48 89 50 44 3b 5e 34 0f 84 72 02 00 00 83 7b 08

Message from syslogd@crema at Fri Mar 16 00:55:56 2007 ...
crema kernel: [17198185.272000] Code: 90 90 90 90 90 90 90 90 90 56 89 c6 53 89 d3 83 ec 14 0f b6 80 b8 00 00 00 84 c0 0f 8f de 02 00 00 8b 53 44 85 d2 74 15 8b 43 48 <89> 42 48 8b 43 48 89 50 44 3b 5e 34 0f 84 72 02 00 00 83 7b 08

Message from syslogd@crema at Fri Mar 16 00:55:56 2007 ...
crema kernel: [17198185.272000] EIP: [pg0+944734482/1068893184] __journal_drop_transaction+0x22/0x310 [jbd] SS:ESP 0068:c1bb7ee8

Message from syslogd@crema at Fri Mar 16 00:55:56 2007 ...
crema kernel: [17198185.272000] EIP: [pg0+944734482/1068893184] __journal_drop_transaction+0x22/0x310 [jbd] SS:ESP 0068:c1bb7ee8
A: 206.9 V: 206.9 A-V:  0.003 ct: -0.091 6207/6207  3%  0%  2.5% 0 0 

```

---

