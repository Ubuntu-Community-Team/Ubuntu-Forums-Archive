---
title: "kernel  BUG: soft lockup - CPU stuck for 23s!"
date: 2014-02-12
forum: General Help
---

### Post by william16 on 2014-02-12
Hi, thanks for reading this.

Basically, my machine is sort of half crashing yielding error messages in the
kern.log, and I'm looking for advice on what to try next.  When there's a
crash, some of the applications are still working, but the machine is very
slow, and the crashed application is unresponsive; also the machine will not
shutdown properly necessitating application of the Reset button.

Here's the background:

I recently installed Xubuntu 13.10 from DVD (checksummed, downloaded
images I burned to DVD).

I'm getting a series of crashes all of the type "BUG: soft lockup - CPU stuck".
An interesting feature of my crashes is that the crash is not always associated
with the same user-space software (often firefox, sometimes "irqbalance",
sometimes samba).

The computer is lightly used for e-mail, websurfing, and sharing files through
samba, on a local home network.

I've done the usual things:
1 - I've googled extensively
2 - I've upgraded the BIOS
3 - I've run memtest
4 - I've tried running "untainted" by using the "Nouveau" Nvidia driver
(#4 made no difference to my problem, I still got the crashes, so I switched
back to the closed-source Nvidia drivers for performance reasons.)

Here are the log entries corresponding to some of these crashes:


```

Feb  9 09:49:00 shannon kernel: [ 5196.092002] BUG: soft lockup - CPU#1 stuck for 23s! [irqbalance:954]
Feb  9 09:49:00 shannon kernel: [ 5196.092002] Modules linked in: nvidia(POF) snd_hda_codec_analog bnep
rfcomm snd_hda_intel snd_hda_codec bluetooth snd_hwdep snd_pcm snd_page_alloc gpio_ich snd_seq_midi
snd_seq_midi_event snd_rawmidi ppdev snd_seq snd_seq_device snd_timer snd psmouse soundcore microcode
lpc_ich serio_raw asus_atk0110 parport_pc mac_hid lp parport raid10 raid456 async_raid6_recov
async_memcpy async_pq async_xor async_tx xor usb_storage raid6_pq raid1 raid0 multipath floppy
linear via_rhine mii
Feb  9 09:49:00 shannon kernel: [ 5196.092002] CPU: 1 PID: 954 Comm: irqbalance Tainted: PF          O 3.11.0-15-generic #25-Ubuntu
Feb  9 09:49:00 shannon kernel: [ 5196.092002] Hardware name: USTek Computer INC. P5L-MX/P5L-MX, BIOS 1103    12/12/2007
Feb  9 09:49:00 shannon kernel: [ 5196.092002] task: ffff880078cc2ee0 ti: ffff88007b144000 task.ti: ffff88007b144000
Feb  9 09:49:00 shannon kernel: [ 5196.092002] RIP: 0010:[<ffffffff8104de62>]  [<ffffffff8104de62>] __ticket_spin_lock+0x22/0x30
Feb  9 09:49:00 shannon kernel: [ 5196.092002] RSP: 0018:ffff88007b145b98  EFLAGS: 00000a16
Feb  9 09:49:00 shannon kernel: [ 5196.092002] RAX: 000000000000c600 RBX: 0000000000000000 RCX: 0000000000007d01
Feb  9 09:49:00 shannon kernel: [ 5196.092002] RDX: 0000000000007d01 RSI: 00003ffffffff000 RDI: ffffea0001e399b0
Feb  9 09:49:00 shannon kernel: [ 5196.092002] RBP: ffff88007b145b98 R08: ffffea00012d7080 R09: 0000000000046ed6
Feb  9 09:49:00 shannon kernel: [ 5196.092002] R10: 0000000000003692 R11: ffff880066cffd40 R12: ffff88007d013000
Feb  9 09:49:00 shannon kernel: [ 5196.092002] R13: ffffea00012d7080 R14: ffff88007c935c20 R15: ffff88007b145b78
Feb  9 09:49:00 shannon kernel: [ 5196.092002] FS:  00007fc0a6549780(0000) GS:ffff88007fc80000(0000) knlGS:0000000000000000
Feb  9 09:49:00 shannon kernel: [ 5196.092002] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Feb  9 09:49:00 shannon kernel: [ 5196.092002] CR2: 00007fc0a6564000 CR3: 000000007a80c000 CR4: 00000000000007e0
Feb  9 09:49:00 shannon kernel: [ 5196.092002] Stack:
Feb  9 09:49:00 shannon kernel: [ 5196.092002]  ffff88007b145ba8 ffffffff816ee5fe ffff88007b145c38 ffffffff811671c7
Feb  9 09:49:00 shannon kernel: [ 5196.092002]  ffff8800460047c0 ffff88007d00d800 ffffffff8118dbc8 ffffffff811c8abe
Feb  9 09:49:00 shannon kernel: [ 5196.092002]  0000000000000000 ffff880062a6a100 ffffea00012d7080 800000004b5c2867
Feb  9 09:49:00 shannon kernel: [ 5196.092002] Call Trace:
Feb  9 09:49:00 shannon kernel: [ 5196.092002]  [<ffffffff816ee5fe>] _raw_spin_lock+0xe/0x20
Feb  9 09:49:00 shannon kernel: [ 5196.092002]  [<ffffffff811671c7>] handle_pte_fault+0x827/0xab0
Feb  9 09:49:00 shannon kernel: [ 5196.092002]  [<ffffffff8118dbc8>] ? kmem_cache_alloc_trace+0x38/0x130
Feb  9 09:49:00 shannon kernel: [ 5196.092002]  [<ffffffff811c8abe>] ? seq_open+0xee/0x160
Feb  9 09:49:00 shannon kernel: [ 5196.092002]  [<ffffffff8118dbc8>] ? kmem_cache_alloc_trace+0x38/0x130
Feb  9 09:49:00 shannon kernel: [ 5196.092002]  [<ffffffff811681f9>] handle_mm_fault+0x299/0x670
Feb  9 09:49:00 shannon kernel: [ 5196.092002]  [<ffffffff811c8a4e>] ? seq_open+0x7e/0x160
Feb  9 09:49:00 shannon kernel: [ 5196.092002]  [<ffffffff81365b42>] ? put_dec+0x72/0x90
Feb  9 09:49:00 shannon kernel: [ 5196.092002]  [<ffffffff816f265d>] __do_page_fault+0x14d/0x530
Feb  9 09:49:00 shannon kernel: [ 5196.092002]  [<ffffffff813685f4>] ? vsnprintf+0x214/0x680
Feb  9 09:49:00 shannon kernel: [ 5196.092002]  [<ffffffff816f2a6c>] do_page_fault+0x2c/0x50
Feb  9 09:49:00 shannon kernel: [ 5196.092002]  [<ffffffff816eee98>] page_fault+0x28/0x30
Feb  9 09:49:00 shannon kernel: [ 5196.092002]  [<ffffffff81369231>] ? copy_user_generic_unrolled+0x41/0xc0
Feb  9 09:49:00 shannon kernel: [ 5196.092002]  [<ffffffff811c9b5b>] ? seq_read+0x27b/0x390
Feb  9 09:49:00 shannon kernel: [ 5196.092002]  [<ffffffff8120950d>] proc_reg_read+0x3d/0x80
Feb  9 09:49:00 shannon kernel: [ 5196.092002]  [<ffffffff811a6f9e>] vfs_read+0x9e/0x170
Feb  9 09:49:00 shannon kernel: [ 5196.092002]  [<ffffffff811a7ac9>] SyS_read+0x49/0xa0
Feb  9 09:49:00 shannon kernel: [ 5196.092002]  [<ffffffff816f725d>] system_call_fastpath+0x1a/0x1f
Feb  9 09:49:00 shannon kernel: [ 5196.092002] Code: 5d c3 0f 1f 80 00 00 00 00 55 b8 00 00 01 00
48 89 e5 f0 0f c1 07 89 c1 c1 e9 10 66 39 c1 89 ca 74 11 0f 1f 80 00 00 00 00 f3 90 <0f> b7 07 66
39 d0 75 f6 5d c3 0f 1f 40 00 8b 17 55 31 c0 48 89 
Feb  9 09:49:28 shannon kernel: [ 5224.092003] BUG: soft lockup - CPU#1 stuck for 23s! [irqbalance:954]
Feb  9 09:49:28 shannon kernel: [ 5224.092003] Modules linked in: nvidia(POF) snd_hda_codec_analog bnep
rfcomm snd_hda_intel snd_hda_codec bluetooth snd_hwdep snd_pcm snd_page_alloc gpio_ich snd_seq_midi
snd_seq_midi_event snd_rawmidi ppdev snd_seq snd_seq_device snd_timer snd psmouse soundcore microcode
lpc_ich serio_raw asus_atk0110 parport_pc mac_hid lp parport raid10 raid456 async_raid6_recov async_memcpy
async_pq async_xor async_tx xor usb_storage raid6_pq raid1 raid0 multipath floppy linear via_rhine mii
Feb  9 09:49:28 shannon kernel: [ 5224.092003] CPU: 1 PID: 954 Comm: irqbalance Tainted: PF          O 3.11.0-15-generic #25-Ubuntu
Feb  9 09:49:28 shannon kernel: [ 5224.092003] Hardware name: USTek Computer INC. P5L-MX/P5L-MX, BIOS 1103    12/12/2007
Feb  9 09:49:28 shannon kernel: [ 5224.092003] task: ffff880078cc2ee0 ti: ffff88007b144000 task.ti: ffff88007b144000
Feb  9 09:49:28 shannon kernel: [ 5224.092003] RIP: 0010:[<ffffffff8104de62>]  [<ffffffff8104de62>] __ticket_spin_lock+0x22/0x30
Feb  9 09:49:28 shannon kernel: [ 5224.092003] RSP: 0018:ffff88007b145b98  EFLAGS: 00000a16
Feb  9 09:49:28 shannon kernel: [ 5224.092003] RAX: 000000000000c600 RBX: 0000000000000000 RCX: 0000000000007d01
Feb  9 09:49:28 shannon kernel: [ 5224.092003] RDX: 0000000000007d01 RSI: 00003ffffffff000 RDI: ffffea0001e399b0
Feb  9 09:49:28 shannon kernel: [ 5224.092003] RBP: ffff88007b145b98 R08: ffffea00012d7080 R09: 0000000000046ed6
Feb  9 09:49:28 shannon kernel: [ 5224.092003] R10: 0000000000003692 R11: ffff880066cffd40 R12: ffff88007d013000
Feb  9 09:49:28 shannon kernel: [ 5224.092003] R13: ffffea00012d7080 R14: ffff88007c935c20 R15: ffff88007b145b78
Feb  9 09:49:28 shannon kernel: [ 5224.092003] FS:  00007fc0a6549780(0000) GS:ffff88007fc80000(0000) knlGS:0000000000000000
Feb  9 09:49:28 shannon kernel: [ 5224.092003] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Feb  9 09:49:28 shannon kernel: [ 5224.092003] CR2: 00007fc0a6564000 CR3: 000000007a80c000 CR4: 00000000000007e0
Feb  9 09:49:28 shannon kernel: [ 5224.092003] Stack:
Feb  9 09:49:28 shannon kernel: [ 5224.092003]  ffff88007b145ba8 ffffffff816ee5fe ffff88007b145c38 ffffffff811671c7
Feb  9 09:49:28 shannon kernel: [ 5224.092003]  ffff8800460047c0 ffff88007d00d800 ffffffff8118dbc8 ffffffff811c8abe
Feb  9 09:49:28 shannon kernel: [ 5224.092003]  0000000000000000 ffff880062a6a100 ffffea00012d7080 800000004b5c2867
Feb  9 09:49:28 shannon kernel: [ 5224.092003] Call Trace:
Feb  9 09:49:28 shannon kernel: [ 5224.092003]  [<ffffffff816ee5fe>] _raw_spin_lock+0xe/0x20
Feb  9 09:49:28 shannon kernel: [ 5224.092003]  [<ffffffff811671c7>] handle_pte_fault+0x827/0xab0
Feb  9 09:49:28 shannon kernel: [ 5224.092003]  [<ffffffff8118dbc8>] ? kmem_cache_alloc_trace+0x38/0x130
Feb  9 09:49:28 shannon kernel: [ 5224.092003]  [<ffffffff811c8abe>] ? seq_open+0xee/0x160
Feb  9 09:49:28 shannon kernel: [ 5224.092003]  [<ffffffff8118dbc8>] ? kmem_cache_alloc_trace+0x38/0x130
Feb  9 09:49:28 shannon kernel: [ 5224.092003]  [<ffffffff811681f9>] handle_mm_fault+0x299/0x670
Feb  9 09:49:28 shannon kernel: [ 5224.092003]  [<ffffffff811c8a4e>] ? seq_open+0x7e/0x160
Feb  9 09:49:28 shannon kernel: [ 5224.092003]  [<ffffffff81365b42>] ? put_dec+0x72/0x90
Feb  9 09:49:28 shannon kernel: [ 5224.092003]  [<ffffffff816f265d>] __do_page_fault+0x14d/0x530
Feb  9 09:49:28 shannon kernel: [ 5224.092003]  [<ffffffff813685f4>] ? vsnprintf+0x214/0x680
Feb  9 09:49:28 shannon kernel: [ 5224.092003]  [<ffffffff816f2a6c>] do_page_fault+0x2c/0x50
Feb  9 09:49:28 shannon kernel: [ 5224.092003]  [<ffffffff816eee98>] page_fault+0x28/0x30
Feb  9 09:49:28 shannon kernel: [ 5224.092003]  [<ffffffff81369231>] ? copy_user_generic_unrolled+0x41/0xc0
Feb  9 09:49:28 shannon kernel: [ 5224.092003]  [<ffffffff811c9b5b>] ? seq_read+0x27b/0x390
Feb  9 09:49:28 shannon kernel: [ 5224.092003]  [<ffffffff8120950d>] proc_reg_read+0x3d/0x80
Feb  9 09:49:28 shannon kernel: [ 5224.092003]  [<ffffffff811a6f9e>] vfs_read+0x9e/0x170
Feb  9 09:49:28 shannon kernel: [ 5224.092003]  [<ffffffff811a7ac9>] SyS_read+0x49/0xa0
Feb  9 09:49:28 shannon kernel: [ 5224.092003]  [<ffffffff816f725d>] system_call_fastpath+0x1a/0x1f
Feb  9 09:49:28 shannon kernel: [ 5224.092003] Code: 5d c3 0f 1f 80 00 00 00 00 55 b8 00 00 01 00
48 89 e5 f0 0f c1 07 89 c1 c1 e9 10 66 39 c1 89 ca 74 11 0f 1f 80 00 00 00 00 f3 90 <0f> b7 07 66
39 d0 75 f6 5d c3 0f 1f 40 00 8b 17 55 31 c0 48 89 
[... and many repetitions more]

```


```

Feb 10 02:58:09 shannon kernel: [44668.100003] BUG: soft lockup - CPU#1 stuck for 22s! [irqbalance:972]
Feb 10 02:58:09 shannon kernel: [44668.100003] Modules linked in: snd_hda_codec_analog gpio_ich
snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_page_alloc ppdev snd_seq_midi snd_seq_midi_event
snd_rawmidi microcode nvidia(POF) snd_seq psmouse rfcomm bnep bluetooth serio_raw lpc_ich snd_seq_device
snd_timer snd asus_atk0110 parport_pc mac_hid soundcore lp parport raid10 raid456 async_raid6_recov
async_memcpy async_pq async_xor async_tx xor usb_storage via_rhine mii raid6_pq raid1 raid0 multipath floppy linear
Feb 10 02:58:09 shannon kernel: [44668.100003] CPU: 1 PID: 972 Comm: irqbalance Tainted: PF          O 3.11.0-15-generic #25-Ubuntu
Feb 10 02:58:09 shannon kernel: [44668.100003] Hardware name: USTek Computer INC. P5L-MX/P5L-MX, BIOS 1103    12/12/2007
Feb 10 02:58:09 shannon kernel: [44668.100003] task: ffff880064b48000 ti: ffff880064b76000 task.ti: ffff880064b76000
Feb 10 02:58:09 shannon kernel: [44668.100003] RIP: 0010:[<ffffffff8104de62>]  [<ffffffff8104de62>] __ticket_spin_lock+0x22/0x30
Feb 10 02:58:09 shannon kernel: [44668.100003] RSP: 0018:ffff880064b77b98  EFLAGS: 00000a16
Feb 10 02:58:09 shannon kernel: [44668.100003] RAX: 000000000000c600 RBX: 0000000000000000 RCX: 0000000000007d01
Feb 10 02:58:09 shannon kernel: [44668.100003] RDX: 0000000000007d01 RSI: 00003ffffffff000 RDI: ffffea00019a8cf0
Feb 10 02:58:09 shannon kernel: [44668.100003] RBP: ffff880064b77b98 R08: ffffea0000980d80 R09: 000000000001e2f3
Feb 10 02:58:09 shannon kernel: [44668.100003] R10: 0000000000003692 R11: ffff880051634440 R12: ffff88007d013000
Feb 10 02:58:09 shannon kernel: [44668.100003] R13: ffffea0000980d80 R14: ffff88007d2e0360 R15: ffff880064b77b78
Feb 10 02:58:09 shannon kernel: [44668.100003] FS:  00007f02b4bfa780(0000) GS:ffff88007fc80000(0000) knlGS:0000000000000000
Feb 10 02:58:09 shannon kernel: [44668.100003] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Feb 10 02:58:09 shannon kernel: [44668.100003] CR2: 00007f02b4c15000 CR3: 0000000064b63000 CR4: 00000000000007e0
Feb 10 02:58:09 shannon kernel: [44668.100003] Stack:
Feb 10 02:58:09 shannon kernel: [44668.100003]  ffff880064b77ba8 ffffffff816ee5fe ffff880064b77c38 ffffffff811671c7
Feb 10 02:58:09 shannon kernel: [44668.100003]  ffff8800664287c0 ffff88007d00d800 ffffffff8118dbc8 ffffffff811c8abe
Feb 10 02:58:09 shannon kernel: [44668.100003]  0000000000000000 ffff880053963e00 ffffea0000980d80 8000000026036867
Feb 10 02:58:09 shannon kernel: [44668.100003] Call Trace:
Feb 10 02:58:09 shannon kernel: [44668.100003]  [<ffffffff816ee5fe>] _raw_spin_lock+0xe/0x20
Feb 10 02:58:09 shannon kernel: [44668.100003]  [<ffffffff811671c7>] handle_pte_fault+0x827/0xab0
Feb 10 02:58:09 shannon kernel: [44668.100003]  [<ffffffff8118dbc8>] ? kmem_cache_alloc_trace+0x38/0x130
Feb 10 02:58:09 shannon kernel: [44668.100003]  [<ffffffff811c8abe>] ? seq_open+0xee/0x160
Feb 10 02:58:09 shannon kernel: [44668.100003]  [<ffffffff8118dbc8>] ? kmem_cache_alloc_trace+0x38/0x130
Feb 10 02:58:09 shannon kernel: [44668.100003]  [<ffffffff811681f9>] handle_mm_fault+0x299/0x670
Feb 10 02:58:09 shannon kernel: [44668.100003]  [<ffffffff811c8a4e>] ? seq_open+0x7e/0x160
Feb 10 02:58:09 shannon kernel: [44668.100003]  [<ffffffff81365b42>] ? put_dec+0x72/0x90
Feb 10 02:58:09 shannon kernel: [44668.100003]  [<ffffffff816f265d>] __do_page_fault+0x14d/0x530
Feb 10 02:58:09 shannon kernel: [44668.100003]  [<ffffffff813685f4>] ? vsnprintf+0x214/0x680
Feb 10 02:58:09 shannon kernel: [44668.100003]  [<ffffffff816f2a6c>] do_page_fault+0x2c/0x50
Feb 10 02:58:09 shannon kernel: [44668.100003]  [<ffffffff816eee98>] page_fault+0x28/0x30
Feb 10 02:58:09 shannon kernel: [44668.100003]  [<ffffffff81369231>] ? copy_user_generic_unrolled+0x41/0xc0
Feb 10 02:58:09 shannon kernel: [44668.100003]  [<ffffffff811c9b5b>] ? seq_read+0x27b/0x390
Feb 10 02:58:09 shannon kernel: [44668.100003]  [<ffffffff8120950d>] proc_reg_read+0x3d/0x80
Feb 10 02:58:09 shannon kernel: [44668.100003]  [<ffffffff811a6f9e>] vfs_read+0x9e/0x170
Feb 10 02:58:09 shannon kernel: [44668.100003]  [<ffffffff811a7ac9>] SyS_read+0x49/0xa0
Feb 10 02:58:09 shannon kernel: [44668.100003]  [<ffffffff816f725d>] system_call_fastpath+0x1a/0x1f
Feb 10 02:58:09 shannon kernel: [44668.100003] Code: 5d c3 0f 1f 80 00 00 00 00 55 b8 00 00 01 00 48
89 e5 f0 0f c1 07 89 c1 c1 e9 10 66 39 c1 89 ca 74 11 0f 1f 80 00 00 00 00 f3 90 <0f> b7 07 66 39 d0
75 f6 5d c3 0f 1f 40 00 8b 17 55 31 c0 48 89 
Feb 10 02:58:37 shannon kernel: [44696.100002] BUG: soft lockup - CPU#1 stuck for 22s! [irqbalance:972]
Feb 10 02:58:37 shannon kernel: [44696.100002] Modules linked in: snd_hda_codec_analog gpio_ich snd_hda_intel
snd_hda_codec snd_hwdep snd_pcm snd_page_alloc ppdev snd_seq_midi snd_seq_midi_event snd_rawmidi microcode
nvidia(POF) snd_seq psmouse rfcomm bnep bluetooth serio_raw lpc_ich snd_seq_device snd_timer snd asus_atk0110
parport_pc mac_hid soundcore lp parport raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor
async_tx xor usb_storage via_rhine mii raid6_pq raid1 raid0 multipath floppy linear
Feb 10 02:58:37 shannon kernel: [44696.100002] CPU: 1 PID: 972 Comm: irqbalance Tainted: PF          O 3.11.0-15-generic #25-Ubuntu
Feb 10 02:58:37 shannon kernel: [44696.100002] Hardware name: USTek Computer INC. P5L-MX/P5L-MX, BIOS 1103    12/12/2007
Feb 10 02:58:37 shannon kernel: [44696.100002] task: ffff880064b48000 ti: ffff880064b76000 task.ti: ffff880064b76000
Feb 10 02:58:37 shannon kernel: [44696.100002] RIP: 0010:[<ffffffff8104de62>]  [<ffffffff8104de62>] __ticket_spin_lock+0x22/0x30
Feb 10 02:58:37 shannon kernel: [44696.100002] RSP: 0018:ffff880064b77b98  EFLAGS: 00000a16
Feb 10 02:58:37 shannon kernel: [44696.100002] RAX: 000000000000c600 RBX: 0000000000000000 RCX: 0000000000007d01
Feb 10 02:58:37 shannon kernel: [44696.100002] RDX: 0000000000007d01 RSI: 00003ffffffff000 RDI: ffffea00019a8cf0
Feb 10 02:58:37 shannon kernel: [44696.100002] RBP: ffff880064b77b98 R08: ffffea0000980d80 R09: 000000000001e2f3
Feb 10 02:58:37 shannon kernel: [44696.100002] R10: 0000000000003692 R11: ffff880051634440 R12: ffff88007d013000
Feb 10 02:58:37 shannon kernel: [44696.100002] R13: ffffea0000980d80 R14: ffff88007d2e0360 R15: ffff880064b77b78
Feb 10 02:58:37 shannon kernel: [44696.100002] FS:  00007f02b4bfa780(0000) GS:ffff88007fc80000(0000) knlGS:0000000000000000
Feb 10 02:58:37 shannon kernel: [44696.100002] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Feb 10 02:58:37 shannon kernel: [44696.100002] CR2: 00007f02b4c15000 CR3: 0000000064b63000 CR4: 00000000000007e0
Feb 10 02:58:37 shannon kernel: [44696.100002] Stack:
Feb 10 02:58:37 shannon kernel: [44696.100002]  ffff880064b77ba8 ffffffff816ee5fe ffff880064b77c38 ffffffff811671c7
Feb 10 02:58:37 shannon kernel: [44696.100002]  ffff8800664287c0 ffff88007d00d800 ffffffff8118dbc8 ffffffff811c8abe
Feb 10 02:58:37 shannon kernel: [44696.100002]  0000000000000000 ffff880053963e00 ffffea0000980d80 8000000026036867
Feb 10 02:58:37 shannon kernel: [44696.100002] Call Trace:
Feb 10 02:58:37 shannon kernel: [44696.100002]  [<ffffffff816ee5fe>] _raw_spin_lock+0xe/0x20
Feb 10 02:58:37 shannon kernel: [44696.100002]  [<ffffffff811671c7>] handle_pte_fault+0x827/0xab0
Feb 10 02:58:37 shannon kernel: [44696.100002]  [<ffffffff8118dbc8>] ? kmem_cache_alloc_trace+0x38/0x130
Feb 10 02:58:37 shannon kernel: [44696.100002]  [<ffffffff811c8abe>] ? seq_open+0xee/0x160
Feb 10 02:58:37 shannon kernel: [44696.100002]  [<ffffffff8118dbc8>] ? kmem_cache_alloc_trace+0x38/0x130
Feb 10 02:58:37 shannon kernel: [44696.100002]  [<ffffffff811681f9>] handle_mm_fault+0x299/0x670
Feb 10 02:58:37 shannon kernel: [44696.100002]  [<ffffffff811c8a4e>] ? seq_open+0x7e/0x160
Feb 10 02:58:37 shannon kernel: [44696.100002]  [<ffffffff81365b42>] ? put_dec+0x72/0x90
Feb 10 02:58:37 shannon kernel: [44696.100002]  [<ffffffff816f265d>] __do_page_fault+0x14d/0x530
Feb 10 02:58:37 shannon kernel: [44696.100002]  [<ffffffff813685f4>] ? vsnprintf+0x214/0x680
Feb 10 02:58:37 shannon kernel: [44696.100002]  [<ffffffff816f2a6c>] do_page_fault+0x2c/0x50
Feb 10 02:58:37 shannon kernel: [44696.100002]  [<ffffffff816eee98>] page_fault+0x28/0x30
Feb 10 02:58:37 shannon kernel: [44696.100002]  [<ffffffff81369231>] ? copy_user_generic_unrolled+0x41/0xc0
Feb 10 02:58:37 shannon kernel: [44696.100002]  [<ffffffff811c9b5b>] ? seq_read+0x27b/0x390
Feb 10 02:58:37 shannon kernel: [44696.100002]  [<ffffffff8120950d>] proc_reg_read+0x3d/0x80
Feb 10 02:58:37 shannon kernel: [44696.100002]  [<ffffffff811a6f9e>] vfs_read+0x9e/0x170
Feb 10 02:58:37 shannon kernel: [44696.100002]  [<ffffffff811a7ac9>] SyS_read+0x49/0xa0
Feb 10 02:58:37 shannon kernel: [44696.100002]  [<ffffffff816f725d>] system_call_fastpath+0x1a/0x1f
Feb 10 02:58:37 shannon kernel: [44696.100002] Code: 5d c3 0f 1f 80 00 00 00 00 55 b8 00 00 01 00 48
89 e5 f0 0f c1 07 89 c1 c1 e9 10 66 39 c1 89 ca 74 11 0f 1f 80 00 00 00 00 f3 90 <0f> b7 07 66 39 d0
75 f6 5d c3 0f 1f 40 00 8b 17 55 31 c0 48 89 

```


```

Feb 12 13:22:33 shannon kernel: [152580.100003] BUG: soft lockup - CPU#1 stuck for 23s! [firefox:7889]
Feb 12 13:22:33 shannon kernel: [152580.100003] Modules linked in: snd_hda_codec_analog gpio_ich
snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_page_alloc microcode snd_seq_midi ppdev nvidia(POF)
snd_seq_midi_event psmouse serio_raw snd_rawmidi lpc_ich rfcomm bnep bluetooth snd_seq parport_pc
asus_atk0110 snd_seq_device mac_hid snd_timer snd soundcore lp parport raid10 raid456 async_raid6_recov
async_memcpy async_pq async_xor async_tx xor usb_storage raid6_pq raid1 via_rhine mii raid0 multipath linear floppy
Feb 12 13:22:33 shannon kernel: [152580.100003] CPU: 1 PID: 7889 Comm: firefox Tainted: PF          O 3.11.0-15-generic #25-Ubuntu
Feb 12 13:22:33 shannon kernel: [152580.100003] Hardware name: USTek Computer INC. P5L-MX/P5L-MX, BIOS 1103    12/12/2007
Feb 12 13:22:33 shannon kernel: [152580.100003] task: ffff880052c34650 ti: ffff880036508000 task.ti: ffff880036508000
Feb 12 13:22:33 shannon kernel: [152580.100003] RIP: 0010:[<ffffffff8104de60>]  [<ffffffff8104de60>] __ticket_spin_lock+0x20/0x30
Feb 12 13:22:33 shannon kernel: [152580.100003] RSP: 0000:ffff880036509d18  EFLAGS: 00000a16
Feb 12 13:22:33 shannon kernel: [152580.100003] RAX: 000000000000c600 RBX: 0000000000000000 RCX: 0000000000007d01
Feb 12 13:22:33 shannon kernel: [152580.100003] RDX: 0000000000007d01 RSI: 00003ffffffff000 RDI: ffffea0001f0f1f0
Feb 12 13:22:33 shannon kernel: [152580.100003] RBP: ffff880036509d18 R08: ffffea00006b0480 R09: 000000000000e011
Feb 12 13:22:33 shannon kernel: [152580.100003] R10: 0000000000003692 R11: 00007f58540aa030 R12: ffff88007d013000
Feb 12 13:22:33 shannon kernel: [152580.100003] R13: ffffea00006b0480 R14: ffff88007d22c120 R15: ffff880036509cf8
Feb 12 13:22:33 shannon kernel: [152580.100003] FS:  00007f58871d7740(0000) GS:ffff88007fc80000(0000) knlGS:0000000000000000
Feb 12 13:22:33 shannon kernel: [152580.100003] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Feb 12 13:22:33 shannon kernel: [152580.100003] CR2: 00007f5847a0f019 CR3: 0000000052f50000 CR4: 00000000000007e0
Feb 12 13:22:33 shannon kernel: [152580.100003] Stack:
Feb 12 13:22:33 shannon kernel: [152580.100003]  ffff880036509d28 ffffffff816ee5fe ffff880036509db8 ffffffff811671c7
Feb 12 13:22:33 shannon kernel: [152580.100003]  ffff88007c11ec20 ffff880036509d58 ffffffff811a9651 ffff8800651f4b40
Feb 12 13:22:33 shannon kernel: [152580.100003]  ffff880036509d88 ffffffff811c0cdf ffffea00006b0480 800000001ac12867
Feb 12 13:22:33 shannon kernel: [152580.100003] Call Trace:
Feb 12 13:22:33 shannon kernel: [152580.100003]  [<ffffffff816ee5fe>] _raw_spin_lock+0xe/0x20
Feb 12 13:22:33 shannon kernel: [152580.100003]  [<ffffffff811671c7>] handle_pte_fault+0x827/0xab0
Feb 12 13:22:33 shannon kernel: [152580.100003]  [<ffffffff811a9651>] ? __sb_end_write+0x31/0x60
Feb 12 13:22:33 shannon kernel: [152580.100003]  [<ffffffff811c0cdf>] ? touch_atime+0x10f/0x140
Feb 12 13:22:33 shannon kernel: [152580.100003]  [<ffffffff811681f9>] handle_mm_fault+0x299/0x670
Feb 12 13:22:33 shannon kernel: [152580.100003]  [<ffffffff816f265d>] __do_page_fault+0x14d/0x530
Feb 12 13:22:33 shannon kernel: [152580.100003]  [<ffffffff811a6940>] ? do_sync_read+0x80/0xb0
Feb 12 13:22:33 shannon kernel: [152580.100003]  [<ffffffff816f2a6c>] do_page_fault+0x2c/0x50
Feb 12 13:22:33 shannon kernel: [152580.100003]  [<ffffffff816eee98>] page_fault+0x28/0x30
Feb 12 13:22:33 shannon kernel: [152580.100003] Code: ff ff 5d c3 0f 1f 80 00 00 00 00 55 b8 00 00 01 00 48 89 e5 f0 0f c1
07 89 c1 c1 e9 10 66 39 c1 89 ca 74 11 0f 1f 80 00 00 00 00 <f3> 90 0f b7 07 66 39 d0 75 f6 5d c3 0f 1f 40 00 8b 17 55 31 c0 
Feb 12 13:23:01 shannon kernel: [152608.100003] BUG: soft lockup - CPU#1 stuck for 22s! [firefox:7889]
Feb 12 13:23:01 shannon kernel: [152608.100003] Modules linked in: snd_hda_codec_analog gpio_ich snd_hda_intel
snd_hda_codec snd_hwdep snd_pcm snd_page_alloc microcode snd_seq_midi ppdev nvidia(POF) snd_seq_midi_event
psmouse serio_raw snd_rawmidi lpc_ich rfcomm bnep bluetooth snd_seq parport_pc asus_atk0110 snd_seq_device
mac_hid snd_timer snd soundcore lp parport raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor
async_tx xor usb_storage raid6_pq raid1 via_rhine mii raid0 multipath linear floppy
Feb 12 13:23:01 shannon kernel: [152608.100003] CPU: 1 PID: 7889 Comm: firefox Tainted: PF          O 3.11.0-15-generic #25-Ubuntu
Feb 12 13:23:01 shannon kernel: [152608.100003] Hardware name: USTek Computer INC. P5L-MX/P5L-MX, BIOS 1103    12/12/2007
Feb 12 13:23:01 shannon kernel: [152608.100003] task: ffff880052c34650 ti: ffff880036508000 task.ti: ffff880036508000
Feb 12 13:23:01 shannon kernel: [152608.100003] RIP: 0010:[<ffffffff8104de62>]  [<ffffffff8104de62>] __ticket_spin_lock+0x22/0x30
Feb 12 13:23:01 shannon kernel: [152608.100003] RSP: 0000:ffff880036509d18  EFLAGS: 00000a16
Feb 12 13:23:01 shannon kernel: [152608.100003] RAX: 000000000000c600 RBX: 0000000000000000 RCX: 0000000000007d01
Feb 12 13:23:01 shannon kernel: [152608.100003] RDX: 0000000000007d01 RSI: 00003ffffffff000 RDI: ffffea0001f0f1f0
Feb 12 13:23:01 shannon kernel: [152608.100003] RBP: ffff880036509d18 R08: ffffea00006b0480 R09: 000000000000e011
Feb 12 13:23:01 shannon kernel: [152608.100003] R10: 0000000000003692 R11: 00007f58540aa030 R12: ffff88007d013000
Feb 12 13:23:01 shannon kernel: [152608.100003] R13: ffffea00006b0480 R14: ffff88007d22c120 R15: ffff880036509cf8
Feb 12 13:23:01 shannon kernel: [152608.100003] FS:  00007f58871d7740(0000) GS:ffff88007fc80000(0000) knlGS:0000000000000000
Feb 12 13:23:01 shannon kernel: [152608.100003] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Feb 12 13:23:01 shannon kernel: [152608.100003] CR2: 00007f5847a0f019 CR3: 0000000052f50000 CR4: 00000000000007e0
Feb 12 13:23:01 shannon kernel: [152608.100003] Stack:
Feb 12 13:23:01 shannon kernel: [152608.100003]  ffff880036509d28 ffffffff816ee5fe ffff880036509db8 ffffffff811671c7
Feb 12 13:23:01 shannon kernel: [152608.100003]  ffff88007c11ec20 ffff880036509d58 ffffffff811a9651 ffff8800651f4b40
Feb 12 13:23:01 shannon kernel: [152608.100003]  ffff880036509d88 ffffffff811c0cdf ffffea00006b0480 800000001ac12867
Feb 12 13:23:01 shannon kernel: [152608.100003] Call Trace:
Feb 12 13:23:01 shannon kernel: [152608.100003]  [<ffffffff816ee5fe>] _raw_spin_lock+0xe/0x20
Feb 12 13:23:01 shannon kernel: [152608.100003]  [<ffffffff811671c7>] handle_pte_fault+0x827/0xab0
Feb 12 13:23:01 shannon kernel: [152608.100003]  [<ffffffff811a9651>] ? __sb_end_write+0x31/0x60
Feb 12 13:23:01 shannon kernel: [152608.100003]  [<ffffffff811c0cdf>] ? touch_atime+0x10f/0x140
Feb 12 13:23:01 shannon kernel: [152608.100003]  [<ffffffff811681f9>] handle_mm_fault+0x299/0x670
Feb 12 13:23:01 shannon kernel: [152608.100003]  [<ffffffff816f265d>] __do_page_fault+0x14d/0x530
Feb 12 13:23:01 shannon kernel: [152608.100003]  [<ffffffff811a6940>] ? do_sync_read+0x80/0xb0
Feb 12 13:23:01 shannon kernel: [152608.100003]  [<ffffffff816f2a6c>] do_page_fault+0x2c/0x50
Feb 12 13:23:01 shannon kernel: [152608.100003]  [<ffffffff816eee98>] page_fault+0x28/0x30
Feb 12 13:23:01 shannon kernel: [152608.100003] Code: 5d c3 0f 1f 80 00 00 00 00 55 b8 00 00 01 00 48 89 e5 f0 0f
c1 07 89 c1 c1 e9 10 66 39 c1 89 ca 74 11 0f 1f 80 00 00 00 00 f3 90 <0f> b7 07 66 39 d0 75 f6 5d c3 0f 1f 40 00
8b 17 55 31 c0 48 89 

```

Anyway, thanks for reading, any suggestions or advice would be greatly appreciated.

Thanks!

---

### Post by william16 on 2014-02-12
More information...
(I appologise for not having included this the first time)


uname -a
```

Linux shannon 3.11.0-15-generic #25-Ubuntu SMP Thu Jan 30 17:22:01 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```


cat /proc/version_signature
```

Ubuntu 3.11.0-15.25-generic 3.11.10

```


dmesg
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.11.0-15-generic (buildd@roseapple) (gcc version 4.8.1 (Ubuntu/Linaro 4.8.1-10ubuntu8) ) #25-Ubuntu SMP Thu Jan 30 17:22:01 UTC 2014 (Ubuntu 3.11.0-15.25-generic 3.11.10)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-15-generic root=UUID=7461fabb-0536-47e2-a52d-a92ac7c5895d ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e4000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000007ff8ffff] usable
[    0.000000] BIOS-e820: [mem 0x000000007ff90000-0x000000007ff9dfff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000007ff9e000-0x000000007ffdffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000007ffe0000-0x000000007fffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffb80000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI: USTek Computer INC. P5L-MX/P5L-MX, BIOS 1103    12/12/2007
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x7ff90 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-DFFFF write-protect
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [ffff8800000ff780]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fd1000, 0x01fd1fff] PGTABLE
[    0.000000] BRK [0x01fd2000, 0x01fd2fff] PGTABLE
[    0.000000] BRK [0x01fd3000, 0x01fd3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x7fc00000-0x7fdfffff]
[    0.000000]  [mem 0x7fc00000-0x7fdfffff] page 2M
[    0.000000] BRK [0x01fd4000, 0x01fd4fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x7c000000-0x7fbfffff]
[    0.000000]  [mem 0x7c000000-0x7fbfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x7bffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x7bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x7fe00000-0x7ff8ffff]
[    0.000000]  [mem 0x7fe00000-0x7ff8ffff] page 4k
[    0.000000] BRK [0x01fd5000, 0x01fd5fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x35db4000-0x36ed1fff]
[    0.000000] ACPI: RSDP 00000000000fafb0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 000000007ff90000 00038 (v01 ATComp TestAsus 12000712 MSFT 00000097)
[    0.000000] ACPI: FACP 000000007ff90200 00081 (v01 ATComp TestAsus 12000712 MSFT 00000097)
[    0.000000] ACPI: DSDT 000000007ff90590 063B6 (v01 ATComp TestAsus 00000000 INTL 20060113)
[    0.000000] ACPI: FACS 000000007ff9e000 00040
[    0.000000] ACPI: APIC 000000007ff90390 00080 (v01 ATComp TestAsus 12000712 MSFT 00000097)
[    0.000000] ACPI: OEMB 000000007ff9e040 00066 (v01 ATComp TestAsus 12000712 MSFT 00000097)
[    0.000000] ACPI: HPET 000000007ff96950 00038 (v01 ATComp OEMHPET  12000712 MSFT 00000097)
[    0.000000] ACPI: MCFG 000000007ff96990 0003C (v01 ATComp TestAsus 12000712 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000007ff8ffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x7ff8ffff]
[    0.000000]   NODE_DATA [mem 0x7ff8b000-0x7ff8ffff]
[    0.000000]  [ffffea0000000000-ffffea0001ffffff] PMD -> [ffff88007d600000-ffff88007f5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0x7ff8ffff]
[    0.000000] On node 0 totalpages: 524078
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 8127 pages used for memmap
[    0.000000]   DMA32 zone: 520080 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000e3fff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e4000-0x000fffff]
[    0.000000] e820: [mem 0x80000000-0xffb7ffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88007fc00000 s86720 r8192 d23872 u524288
[    0.000000] pcpu-alloc: s86720 r8192 d23872 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 515866
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-15-generic root=UUID=7461fabb-0536-47e2-a52d-a92ac7c5895d ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 2028976K/2096312K available (7149K kernel code, 1082K rwdata, 3312K rodata, 1364K init, 1420K bss, 67336K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-255.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 8388608 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 2800.079 MHz processor
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 5600.15 BogoMIPS (lpj=11200316)
[    0.004012] pid_max: default: 32768 minimum: 301
[    0.004057] Security Framework initialized
[    0.004091] AppArmor: AppArmor initialized
[    0.004094] Yama: becoming mindful.
[    0.004462] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.008108] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.008655] Mount-cache hash table entries: 256
[    0.009027] Initializing cgroup subsys memory
[    0.009051] Initializing cgroup subsys devices
[    0.009054] Initializing cgroup subsys freezer
[    0.009057] Initializing cgroup subsys blkio
[    0.009060] Initializing cgroup subsys perf_event
[    0.009065] Initializing cgroup subsys hugetlb
[    0.009107] CPU: Physical Processor ID: 0
[    0.009111] CPU: Processor Core ID: 0
[    0.009114] mce: CPU supports 4 MCE banks
[    0.009130] CPU0: Thermal monitoring enabled (TM1)
[    0.009142] Last level iTLB entries: 4KB 128, 2MB 128, 4MB 128
[    0.009142] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 64
[    0.009142] tlb_flushall_shift: 6
[    0.009248] Freeing SMP alternatives memory: 28K (ffffffff81e65000 - ffffffff81e6c000)
[    0.012340] ACPI: Core revision 20130517
[    0.016730] ACPI: All ACPI Tables successfully acquired
[    0.020019] ftrace: allocating 27844 entries in 109 pages
[    0.032538] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.078673] smpboot: CPU0: Intel(R) Pentium(R) D CPU 2.80GHz (fam: 0f, model: 04, stepping: 07)
[    0.080000] Performance Events: Netburst events, Netburst P4/Xeon PMU driver.
[    0.080000] ... version:                0
[    0.080000] ... bit width:              40
[    0.080000] ... generic registers:      18
[    0.080000] ... value mask:             000000ffffffffff
[    0.080000] ... max period:             0000007fffffffff
[    0.080000] ... fixed-purpose events:   0
[    0.080000] ... event mask:             000000000003ffff
[    0.080000] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.080000] smpboot: Booting Node   0, Processors  #1
[    0.091996] Brought up 2 CPUs
[    0.092000] smpboot: Total of 2 processors activated (11200.31 BogoMIPS)
[    0.093130] devtmpfs: initialized
[    0.093653] EVM: security.selinux
[    0.093656] EVM: security.SMACK64
[    0.093658] EVM: security.capability
[    0.093704] PM: Registering ACPI NVS region [mem 0x7ff9e000-0x7ffdffff] (270336 bytes)
[    0.096662] regulator-dummy: no parameters
[    0.096703] RTC time: 18:23:52, date: 02/12/14
[    0.096776] NET: Registered protocol family 16
[    0.097032] ACPI: bus type PCI registered
[    0.097037] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.097131] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
[    0.097136] PCI: not using MMCONFIG
[    0.097139] PCI: Using configuration type 1 for base access
[    0.097310] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.097313] mtrr: probably your BIOS does not setup all CPUs.
[    0.097315] mtrr: corrected configuration.
[    0.098748] bio: create slab <bio-0> at 0
[    0.098748] ACPI: Added _OSI(Module Device)
[    0.098748] ACPI: Added _OSI(Processor Device)
[    0.098748] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.098748] ACPI: Added _OSI(Processor Aggregator Device)
[    0.100839] ACPI: EC: Look up EC in DSDT
[    0.102878] ACPI: Executed 1 blocks of module-level executable AML code
[    0.106820] ACPI: Interpreter enabled
[    0.106839] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20130517/hwxface-571)
[    0.106863] ACPI: (supports S0 S1 S3 S4 S5)
[    0.106867] ACPI: Using IOAPIC for interrupt routing
[    0.106907] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
[    0.109448] PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] reserved in ACPI motherboard resources
[    0.115366] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.115512] ACPI: No dock devices found.
[    0.126068] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.126081] acpi PNP0A08:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.126086] acpi PNP0A08:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.126223] acpi PNP0A08:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.126229] acpi PNP0A08:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.126233] acpi PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.126237] acpi PNP0A08:00: host bridge window [mem 0x80010000-0xffffffff] (ignored)
[    0.126240] PCI: root bus 00: using default resources
[    0.126245] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    0.126428] PCI host bridge to bus 0000:00
[    0.126434] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.126438] pci_bus 0000:00: root bus resource [io  0x0000-0xffff]
[    0.126445] pci_bus 0000:00: root bus resource [mem 0x00000000-0xfffffffff]
[    0.126460] pci 0000:00:00.0: [8086:2770] type 00 class 0x060000
[    0.126612] pci 0000:00:01.0: [8086:2771] type 01 class 0x060400
[    0.126675] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.126751] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.126845] pci 0000:00:1b.0: [8086:27d8] type 00 class 0x040300
[    0.126866] pci 0000:00:1b.0: reg 0x10: [mem 0xdddf8000-0xdddfbfff 64bit]
[    0.126950] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.127075] pci 0000:00:1c.0: [8086:27d0] type 01 class 0x060400
[    0.127162] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.127239] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.127305] pci 0000:00:1d.0: [8086:27c8] type 00 class 0x0c0300
[    0.127354] pci 0000:00:1d.0: reg 0x20: [io  0x9000-0x901f]
[    0.127449] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.127507] pci 0000:00:1d.1: [8086:27c9] type 00 class 0x0c0300
[    0.127556] pci 0000:00:1d.1: reg 0x20: [io  0x9400-0x941f]
[    0.127646] pci 0000:00:1d.1: System wakeup disabled by ACPI
[    0.127703] pci 0000:00:1d.2: [8086:27ca] type 00 class 0x0c0300
[    0.127752] pci 0000:00:1d.2: reg 0x20: [io  0x9800-0x981f]
[    0.127842] pci 0000:00:1d.2: System wakeup disabled by ACPI
[    0.127898] pci 0000:00:1d.3: [8086:27cb] type 00 class 0x0c0300
[    0.127947] pci 0000:00:1d.3: reg 0x20: [io  0xa000-0xa01f]
[    0.128046] pci 0000:00:1d.3: System wakeup disabled by ACPI
[    0.128113] pci 0000:00:1d.7: [8086:27cc] type 00 class 0x0c0320
[    0.128138] pci 0000:00:1d.7: reg 0x10: [mem 0xdddffc00-0xdddfffff]
[    0.128236] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.128309] pci 0000:00:1d.7: System wakeup disabled by ACPI
[    0.128368] pci 0000:00:1e.0: [8086:244e] type 01 class 0x060401
[    0.128492] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.128553] pci 0000:00:1f.0: [8086:27b8] type 00 class 0x060100
[    0.128648] pci 0000:00:1f.0: address space collision: [io  0x0800-0x087f] conflicts with ACPI CPU throttle [??? 0x00000810-0x00000815 flags 0x80000000]
[    0.128657] pci 0000:00:1f.0: quirk: [io  0x0480-0x04bf] claimed by ICH6 GPIO
[    0.128664] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0290 (mask 0007)
[    0.128804] pci 0000:00:1f.1: [8086:27df] type 00 class 0x01018a
[    0.128822] pci 0000:00:1f.1: reg 0x10: [io  0x0000-0x0007]
[    0.128835] pci 0000:00:1f.1: reg 0x14: [io  0x0000-0x0003]
[    0.128846] pci 0000:00:1f.1: reg 0x18: [io  0x0000-0x0007]
[    0.128858] pci 0000:00:1f.1: reg 0x1c: [io  0x0000-0x0003]
[    0.128870] pci 0000:00:1f.1: reg 0x20: [io  0xffa0-0xffaf]
[    0.129008] pci 0000:00:1f.2: [8086:27c0] type 00 class 0x01018f
[    0.129027] pci 0000:00:1f.2: reg 0x10: [io  0xb800-0xb807]
[    0.129037] pci 0000:00:1f.2: reg 0x14: [io  0xb400-0xb403]
[    0.129048] pci 0000:00:1f.2: reg 0x18: [io  0xb000-0xb007]
[    0.129058] pci 0000:00:1f.2: reg 0x1c: [io  0xa800-0xa803]
[    0.129068] pci 0000:00:1f.2: reg 0x20: [io  0xa400-0xa40f]
[    0.129113] pci 0000:00:1f.2: PME# supported from D3hot
[    0.129228] pci 0000:00:1f.3: [8086:27da] type 00 class 0x0c0500
[    0.129288] pci 0000:00:1f.3: reg 0x20: [io  0x0400-0x041f]
[    0.129493] pci 0000:03:00.0: [10de:01df] type 00 class 0x030000
[    0.129509] pci 0000:03:00.0: reg 0x10: [mem 0xdf000000-0xdfffffff]
[    0.129524] pci 0000:03:00.0: reg 0x14: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.129538] pci 0000:03:00.0: reg 0x1c: [mem 0xde000000-0xdeffffff 64bit]
[    0.129554] pci 0000:03:00.0: reg 0x30: [mem 0xddfe0000-0xddffffff pref]
[    0.129643] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.129655] pci 0000:00:01.0: PCI bridge to [bus 03]
[    0.129660] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.129666] pci 0000:00:01.0:   bridge window [mem 0xddf00000-0xdfffffff]
[    0.129672] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.129746] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.129753] pci 0000:00:1c.0:   bridge window [io  0xd000-0xdfff]
[    0.129827] pci 0000:01:01.0: [1106:3106] type 00 class 0x020000
[    0.129850] pci 0000:01:01.0: reg 0x10: [io  0xc800-0xc8ff]
[    0.129863] pci 0000:01:01.0: reg 0x14: [mem 0xddeffc00-0xddeffcff]
[    0.129914] pci 0000:01:01.0: reg 0x30: [mem 0xddee0000-0xddeeffff pref]
[    0.129949] pci 0000:01:01.0: supports D1 D2
[    0.129953] pci 0000:01:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.130053] pci 0000:00:1e.0: PCI bridge to [bus 01] (subtractive decode)
[    0.130059] pci 0000:00:1e.0:   bridge window [io  0xc000-0xcfff]
[    0.130065] pci 0000:00:1e.0:   bridge window [mem 0xdde00000-0xddefffff]
[    0.130073] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.130077] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xfffffffff] (subtractive decode)
[    0.131335] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.131452] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.131567] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.131680] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.131792] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.131905] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.132024] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.132139] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.132331] ACPI: \_SB_.PCI0: notify handler is installed
[    0.132393] Found 1 acpi root devices
[    0.132545] vgaarb: device added: PCI:0000:03:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.132545] vgaarb: loaded
[    0.132545] vgaarb: bridge control possible 0000:03:00.0
[    0.132545] SCSI subsystem initialized
[    0.132545] ACPI: bus type ATA registered
[    0.132545] libata version 3.00 loaded.
[    0.132545] ACPI: bus type USB registered
[    0.132545] usbcore: registered new interface driver usbfs
[    0.132545] usbcore: registered new interface driver hub
[    0.132545] usbcore: registered new device driver usb
[    0.132545] PCI: Using ACPI for IRQ routing
[    0.133801] PCI: pci_cache_line_size set to 64 bytes
[    0.133858] e820: reserve RAM buffer [mem 0x0009fc00-0x0009ffff]
[    0.133862] e820: reserve RAM buffer [mem 0x7ff90000-0x7fffffff]
[    0.134018] NetLabel: Initializing
[    0.134022] NetLabel:  domain hash size = 128
[    0.134024] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.134043] NetLabel:  unlabeled traffic allowed by default
[    0.134064] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.134064] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.134064] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.137039] Switched to clocksource hpet
[    0.147112] AppArmor: AppArmor Filesystem Enabled
[    0.147160] pnp: PnP ACPI init
[    0.147188] ACPI: bus type PNP registered
[    0.147294] system 00:00: [mem 0xfed13000-0xfed19fff] has been reserved
[    0.147301] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.147348] pnp 00:01: [dma 4]
[    0.147383] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.147445] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.147492] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.147541] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.148030] pnp 00:05: [dma 2]
[    0.148113] pnp 00:05: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.148636] pnp 00:06: [dma 3]
[    0.148827] pnp 00:06: Plug and Play ACPI device, IDs PNP0401 (active)
[    0.148926] system 00:07: [io  0x0290-0x0297] has been reserved
[    0.148933] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.149201] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.149207] system 00:08: [io  0x0800-0x087f] could not be reserved
[    0.149212] system 00:08: [io  0x0480-0x04bf] has been reserved
[    0.149216] system 00:08: [io  0x0900-0x091f] has been reserved
[    0.149220] system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.149225] system 00:08: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.149229] system 00:08: [mem 0xffb00000-0xffbfffff] could not be reserved
[    0.149233] system 00:08: [mem 0xfff00000-0xffffffff] has been reserved
[    0.149238] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.149430] pnp 00:09: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.149555] pnp 00:0a: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.149676] pnp 00:0b: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
[    0.149797] system 00:0c: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.149802] system 00:0c: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.149807] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.150167] pnp 00:0d: [dma 0 disabled]
[    0.150268] pnp 00:0d: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.150388] pnp 00:0e: Plug and Play ACPI device, IDs INT0800 (active)
[    0.150504] system 00:0f: [mem 0xffc00000-0xfff7ffff] could not be reserved
[    0.150510] system 00:0f: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.150617] system 00:10: [mem 0xf0000000-0xf3ffffff] has been reserved
[    0.150623] system 00:10: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.150911] system 00:11: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.150917] system 00:11: [mem 0x000c0000-0x000dffff] could not be reserved
[    0.150922] system 00:11: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.150926] system 00:11: [mem 0x00100000-0x7fffffff] could not be reserved
[    0.150931] system 00:11: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.151173] pnp: PnP ACPI: found 18 devices
[    0.151176] ACPI: bus type PNP unregistered
[    0.159470] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02] add_size 200000
[    0.159476] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 02] add_size 200000
[    0.159492] pci 0000:00:1f.0: BAR 13: [io  0x0800-0x087f] has bogus alignment
[    0.159498] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.159502] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.159509] pci 0000:00:1c.0: BAR 14: assigned [mem 0x80000000-0x801fffff]
[    0.159514] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80200000-0x803fffff 64bit pref]
[    0.159520] pci 0000:00:01.0: PCI bridge to [bus 03]
[    0.159525] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.159531] pci 0000:00:01.0:   bridge window [mem 0xddf00000-0xdfffffff]
[    0.159536] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.159542] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.159547] pci 0000:00:1c.0:   bridge window [io  0xd000-0xdfff]
[    0.159553] pci 0000:00:1c.0:   bridge window [mem 0x80000000-0x801fffff]
[    0.159559] pci 0000:00:1c.0:   bridge window [mem 0x80200000-0x803fffff 64bit pref]
[    0.159567] pci 0000:00:1e.0: PCI bridge to [bus 01]
[    0.159572] pci 0000:00:1e.0:   bridge window [io  0xc000-0xcfff]
[    0.159579] pci 0000:00:1e.0:   bridge window [mem 0xdde00000-0xddefffff]
[    0.159807] pci 0000:00:1e.0: setting latency timer to 64
[    0.159815] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.159819] pci_bus 0000:00: resource 5 [mem 0x00000000-0xfffffffff]
[    0.159823] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    0.159827] pci_bus 0000:03: resource 1 [mem 0xddf00000-0xdfffffff]
[    0.159831] pci_bus 0000:03: resource 2 [mem 0xe0000000-0xefffffff 64bit pref]
[    0.159835] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
[    0.159839] pci_bus 0000:02: resource 1 [mem 0x80000000-0x801fffff]
[    0.159843] pci_bus 0000:02: resource 2 [mem 0x80200000-0x803fffff 64bit pref]
[    0.159847] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
[    0.159851] pci_bus 0000:01: resource 1 [mem 0xdde00000-0xddefffff]
[    0.159854] pci_bus 0000:01: resource 4 [io  0x0000-0xffff]
[    0.159858] pci_bus 0000:01: resource 5 [mem 0x00000000-0xfffffffff]
[    0.159915] NET: Registered protocol family 2
[    0.160182] TCP established hash table entries: 16384 (order: 6, 262144 bytes)
[    0.160310] TCP bind hash table entries: 16384 (order: 6, 262144 bytes)
[    0.160397] TCP: Hash tables configured (established 16384 bind 16384)
[    0.160455] TCP: reno registered
[    0.160465] UDP hash table entries: 1024 (order: 3, 32768 bytes)
[    0.160488] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
[    0.160603] NET: Registered protocol family 1
[    0.161662] pci 0000:03:00.0: Boot video device
[    0.161671] PCI: CLS 16 bytes, default 64
[    0.161784] Trying to unpack rootfs image as initramfs...
[    0.656574] Freeing initrd memory: 17528K (ffff880035db4000 - ffff880036ed2000)
[    0.656794] Scanning for low memory corruption every 60 seconds
[    0.657181] Initialise module verification
[    0.657252] audit: initializing netlink socket (disabled)
[    0.657280] type=2000 audit(1392229432.656:1): initialized
[    0.695712] bounce pool size: 64 pages
[    0.695733] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.697846] zbud: loaded
[    0.698052] VFS: Disk quotas dquot_6.5.2
[    0.698134] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.699002] fuse init (API version 7.22)
[    0.699129] msgmni has been set to 3997
[    0.699773] Key type asymmetric registered
[    0.699778] Asymmetric key parser 'x509' registered
[    0.699838] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.699887] io scheduler noop registered
[    0.699891] io scheduler deadline registered (default)
[    0.699939] io scheduler cfq registered
[    0.700127] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.700219] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.700326] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.700352] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.700569] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.700577] ACPI: Power Button [PWRB]
[    0.700647] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.700652] ACPI: Power Button [PWRF]
[    0.700904] GHES: HEST is not enabled!
[    0.701020] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.721492] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.723441] Linux agpgart interface v0.103
[    0.725667] brd: module loaded
[    0.726746] loop: module loaded
[    0.726936] ata_piix 0000:00:1f.1: version 2.13
[    0.727131] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.727545] scsi0 : ata_piix
[    0.728260] scsi1 : ata_piix
[    0.728873] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.728878] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.729002] ata_piix 0000:00:1f.2: MAP [
[    0.729006]  P0 P2 P1 P3 ]
[    0.729054] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.729531] scsi2 : ata_piix
[    0.730292] scsi3 : ata_piix
[    0.731012] ata3: SATA max UDMA/133 cmd 0xb800 ctl 0xb400 bmdma 0xa400 irq 23
[    0.731016] ata4: SATA max UDMA/133 cmd 0xb000 ctl 0xa800 bmdma 0xa408 irq 23
[    0.731466] libphy: Fixed MDIO Bus: probed
[    0.731618] tun: Universal TUN/TAP device driver, 1.6
[    0.731621] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.731708] PPP generic driver version 2.4.2
[    0.731783] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.731787] ehci-pci: EHCI PCI platform driver
[    0.731924] ehci-pci 0000:00:1d.7: setting latency timer to 64
[    0.731939] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    0.731950] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.731968] ehci-pci 0000:00:1d.7: debug port 1
[    0.735866] ehci-pci 0000:00:1d.7: cache line size of 16 is not supported
[    0.735898] ehci-pci 0000:00:1d.7: irq 20, io mem 0xdddffc00
[    0.744028] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.744063] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.744067] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.744071] usb usb1: Product: EHCI Host Controller
[    0.744074] usb usb1: Manufacturer: Linux 3.11.0-15-generic ehci_hcd
[    0.744077] usb usb1: SerialNumber: 0000:00:1d.7
[    0.744232] hub 1-0:1.0: USB hub found
[    0.744240] hub 1-0:1.0: 8 ports detected
[    0.744475] ehci-platform: EHCI generic platform driver
[    0.744489] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.744492] ohci-pci: OHCI PCI platform driver
[    0.744508] ohci-platform: OHCI generic platform driver
[    0.744519] uhci_hcd: USB Universal Host Controller Interface driver
[    0.744647] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.744653] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.744661] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.744716] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00009000
[    0.744766] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    0.744770] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.744774] usb usb2: Product: UHCI Host Controller
[    0.744777] usb usb2: Manufacturer: Linux 3.11.0-15-generic uhci_hcd
[    0.744780] usb usb2: SerialNumber: 0000:00:1d.0
[    0.744925] hub 2-0:1.0: USB hub found
[    0.744935] hub 2-0:1.0: 2 ports detected
[    0.745168] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.745174] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.745182] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.745225] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00009400
[    0.745273] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    0.745278] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.745281] usb usb3: Product: UHCI Host Controller
[    0.745284] usb usb3: Manufacturer: Linux 3.11.0-15-generic uhci_hcd
[    0.745287] usb usb3: SerialNumber: 0000:00:1d.1
[    0.745411] hub 3-0:1.0: USB hub found
[    0.745418] hub 3-0:1.0: 2 ports detected
[    0.745619] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.745625] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.745633] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.745676] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00009800
[    0.745722] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    0.745726] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.745729] usb usb4: Product: UHCI Host Controller
[    0.745732] usb usb4: Manufacturer: Linux 3.11.0-15-generic uhci_hcd
[    0.745735] usb usb4: SerialNumber: 0000:00:1d.2
[    0.745857] hub 4-0:1.0: USB hub found
[    0.745864] hub 4-0:1.0: 2 ports detected
[    0.746098] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.746104] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.746112] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.746151] uhci_hcd 0000:00:1d.3: irq 19, io base 0x0000a000
[    0.746201] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    0.746205] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.746209] usb usb5: Product: UHCI Host Controller
[    0.746212] usb usb5: Manufacturer: Linux 3.11.0-15-generic uhci_hcd
[    0.746215] usb usb5: SerialNumber: 0000:00:1d.3
[    0.746342] hub 5-0:1.0: USB hub found
[    0.746348] hub 5-0:1.0: 2 ports detected
[    0.746587] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.749288] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.749299] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.749512] mousedev: PS/2 mouse device common for all mice
[    0.749725] rtc_cmos 00:02: RTC can wake from S4
[    0.749883] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.749914] rtc_cmos 00:02: alarms up to one month, 114 bytes nvram, hpet irqs
[    0.750038] device-mapper: uevent: version 1.0.3
[    0.750146] device-mapper: ioctl: 4.25.0-ioctl (2013-06-26) initialised: dm-devel@redhat.com
[    0.750155] cpuidle: using governor ladder
[    0.750158] cpuidle: using governor menu
[    0.750179] ledtrig-cpu: registered to indicate activity on CPUs
[    0.750308] TCP: cubic registered
[    0.750509] NET: Registered protocol family 10
[    0.750829] NET: Registered protocol family 17
[    0.750847] Key type dns_resolver registered
[    0.751196] PM: Hibernation image not present or could not be loaded.
[    0.751202] Loading module verification certificates
[    0.752864] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 233c65a83836c14ba34eda83a0b805044bc3b448'
[    0.752885] registered taskstats version 1
[    0.756955] Key type trusted registered
[    0.760489] Key type encrypted registered
[    0.763982] AppArmor: AppArmor sha1 policy hashing enabled
[    0.764324]   Magic number: 2:608:392
[    0.764450] rtc_cmos 00:02: setting system clock to 2014-02-12 18:23:53 UTC (1392229433)
[    0.764556] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.764559] EDD information not available.
[    0.773421] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.907354] ata3.00: ATA-8: WDC WD2002FAEX-007BA0, 05.01D05, max UDMA/133
[    0.907360] ata3.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.912317] ata4.01: ATAPI: HL-DT-ST DVDRAM GH24NS90, IN01, max UDMA/100
[    0.912457] ata3.00: configured for UDMA/133
[    0.912612] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2002FAEX-0 05.0 PQ: 0 ANSI: 5
[    0.912865] sd 2:0:0:0: [sda] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    0.912954] sd 2:0:0:0: [sda] Write Protect is off
[    0.912959] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.912998] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.913116] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    0.928170] ata4.01: configured for UDMA/100
[    0.935787]  sda: sda1 sda2 < sda5 sda6 sda7 >
[    0.936435] sd 2:0:0:0: [sda] Attached SCSI disk
[    0.940062] scsi 3:0:1:0: CD-ROM            HL-DT-ST DVDRAM GH24NS90  IN01 PQ: 0 ANSI: 5
[    0.953731] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.953736] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.953887] sr 3:0:1:0: Attached scsi CD-ROM sr0
[    0.954035] sr 3:0:1:0: Attached scsi generic sg1 type 5
[    0.955992] Freeing unused kernel memory: 1364K (ffffffff81d10000 - ffffffff81e65000)
[    0.955996] Write protecting the kernel read-only data: 12288k
[    0.960431] Freeing unused kernel memory: 1032K (ffff8800016fe000 - ffff880001800000)
[    0.963429] Freeing unused kernel memory: 784K (ffff880001b3c000 - ffff880001c00000)
[    0.986615] systemd-udevd[110]: starting version 204
[    1.022374] via_rhine: v1.10-LK1.5.1 2010-10-09 Written by Donald Becker
[    1.029008] via-rhine 0000:01:01.0 eth0: VIA Rhine III at 0xddeffc00, 00:19:5b:82:9f:82, IRQ 21
[    1.029798] via-rhine 0000:01:01.0 eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1
[    1.034794] md: linear personality registered for level -1
[    1.039831] md: multipath personality registered for level -4
[    1.044709] md: raid0 personality registered for level 0
[    1.047569] Floppy drive(s): fd0 is 1.44M
[    1.050226] md: raid1 personality registered for level 1
[    1.056070] usb 1-8: new high-speed USB device number 2 using ehci-pci
[    1.067879] FDC 0 is a post-1991 82077
[    1.124021] raid6: sse2x1    2000 MB/s
[    1.192013] raid6: sse2x2    3039 MB/s
[    1.260025] raid6: sse2x4    2908 MB/s
[    1.260029] raid6: using algorithm sse2x2 (3039 MB/s)
[    1.260031] raid6: using intx1 recovery algorithm
[    1.262147] xor: measuring software checksum speed
[    1.300013]    prefetch64-sse:  3848.000 MB/sec
[    1.313340] usb 1-8: New USB device found, idVendor=0bc2, idProduct=50a5
[    1.313348] usb 1-8: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[    1.313352] usb 1-8: Product: GoFlex Desk
[    1.313355] usb 1-8: Manufacturer: Seagate
[    1.313358] usb 1-8: SerialNumber: NA0L8P5Q
[    1.319283] usb-storage 1-8:1.0: USB Mass Storage device detected
[    1.322430] scsi4 : usb-storage 1-8:1.0
[    1.322637] usbcore: registered new interface driver usb-storage
[    1.340012]    generic_sse:  3785.000 MB/sec
[    1.340016] xor: using function: prefetch64-sse (3848.000 MB/sec)
[    1.341938] async_tx: api initialized (async)
[    1.353409] md: raid6 personality registered for level 6
[    1.353414] md: raid5 personality registered for level 5
[    1.353417] md: raid4 personality registered for level 4
[    1.365341] md: raid10 personality registered for level 10
[    1.395057] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[    1.395063] EXT4-fs (sda5): write access will be enabled during recovery
[    1.656035] tsc: Refined TSC clocksource calibration: 2799.909 MHz
[    1.730297] EXT4-fs (sda5): orphan cleanup on readonly fs
[    1.733822] EXT4-fs (sda5): 3 orphan inodes deleted
[    1.733826] EXT4-fs (sda5): recovery complete
[    1.805061] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    2.320907] scsi 4:0:0:0: Direct-Access     Seagate  GoFlex Desk      0D16 PQ: 0 ANSI: 5
[    2.321288] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    2.321772] sd 4:0:0:0: [sdb] 732566645 4096-byte logical blocks: (3.00 TB/2.72 TiB)
[    2.322882] sd 4:0:0:0: [sdb] Write Protect is off
[    2.322888] sd 4:0:0:0: [sdb] Mode Sense: 4f 00 00 00
[    2.324532] sd 4:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    2.327762] sd 4:0:0:0: [sdb] 732566645 4096-byte logical blocks: (3.00 TB/2.72 TiB)
[    2.330543]  sdb: sdb1
[    2.331639] sd 4:0:0:0: [sdb] 732566645 4096-byte logical blocks: (3.00 TB/2.72 TiB)
[    2.333634] sd 4:0:0:0: [sdb] Attached SCSI disk
[    2.656107] Switched to clocksource tsc
[    9.328485] Adding 3998716k swap on /dev/sda1.  Priority:-1 extents:1 across:3998716k FS
[    9.652984] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   10.042112] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: errors=remount-ro
[   10.413402] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.520509] systemd-udevd[363]: starting version 204
[   10.630226] lp: driver loaded but no devices found
[   10.695702] parport_pc 00:06: reported by Plug and Play ACPI
[   10.695834] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   10.776436] lp0: using parport0 (interrupt-driven).
[   10.795655] Bluetooth: Core ver 2.16
[   10.795691] NET: Registered protocol family 31
[   10.795695] Bluetooth: HCI device and connection manager initialized
[   10.795709] Bluetooth: HCI socket layer initialized
[   10.795713] Bluetooth: L2CAP socket layer initialized
[   10.795724] Bluetooth: SCO socket layer initialized
[   10.814709] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   10.814716] Bluetooth: BNEP filters: protocol multicast
[   10.814730] Bluetooth: BNEP socket layer initialized
[   10.839053] intel_rng: FWH not detected
[   10.864063] Bluetooth: RFCOMM TTY layer initialized
[   10.864087] Bluetooth: RFCOMM socket layer initialized
[   10.864091] Bluetooth: RFCOMM ver 1.11
[   10.876460] leds_ss4200: no LED devices found
[   11.023259] nvidia: module license 'NVIDIA' taints kernel.
[   11.023268] Disabling lock debugging due to kernel taint
[   11.080980] type=1400 audit(1392229443.811:2): apparmor="STATUS" operation="profile_load" parent=457 profile="unconfined" name="/sbin/dhclient" pid=459 comm="apparmor_parser"
[   11.080996] type=1400 audit(1392229443.811:3): apparmor="STATUS" operation="profile_load" parent=457 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=459 comm="apparmor_parser"
[   11.081005] type=1400 audit(1392229443.811:4): apparmor="STATUS" operation="profile_load" parent=457 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=459 comm="apparmor_parser"
[   11.081689] type=1400 audit(1392229443.811:5): apparmor="STATUS" operation="profile_replace" parent=457 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=459 comm="apparmor_parser"
[   11.081703] type=1400 audit(1392229443.811:6): apparmor="STATUS" operation="profile_replace" parent=457 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=459 comm="apparmor_parser"
[   11.082034] type=1400 audit(1392229443.811:7): apparmor="STATUS" operation="profile_replace" parent=457 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=459 comm="apparmor_parser"
[   11.093613] nvidia: module verification failed: signature and/or required key missing - tainting kernel
[   11.107458] type=1400 audit(1392229443.835:8): apparmor="STATUS" operation="profile_load" parent=457 profile="unconfined" name="/usr/sbin/ntpd" pid=463 comm="apparmor_parser"
[   11.151322] vgaarb: device changed decodes: PCI:0000:03:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   11.153915] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  304.108  Wed Jul 31 19:35:17 PDT 2013
[   11.182318] ppdev: user-space parallel port driver
[   11.288608] init: avahi-cups-reload main process (465) terminated with status 1
[   11.293320] microcode: CPU0 sig=0xf47, pf=0x10, revision=0x3
[   11.334713] type=1400 audit(1392229444.063:9): apparmor="STATUS" operation="profile_load" parent=476 profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=497 comm="apparmor_parser"
[   11.334729] type=1400 audit(1392229444.063:10): apparmor="STATUS" operation="profile_load" parent=476 profile="unconfined" name="/usr/sbin/cupsd" pid=497 comm="apparmor_parser"
[   11.335453] type=1400 audit(1392229444.063:11): apparmor="STATUS" operation="profile_replace" parent=476 profile="unconfined" name="/usr/sbin/cupsd" pid=497 comm="apparmor_parser"
[   11.813294] snd_hda_intel 0000:00:1b.0: irq 42 for MSI/MSI-X
[   11.827238] init: failsafe main process (534) killed by TERM signal
[   11.916979] gpio_ich: GPIO from 206 to 255 on gpio_ich
[   11.950911] microcode: CPU1 sig=0xf47, pf=0x10, revision=0x3
[   11.959061] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   12.278753] input: ImExPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input3
[   12.433011] init: udev-fallback-graphics main process (715) terminated with status 1

```


sudo lspci -vvnn
```

00:00.0 Host bridge [0600]: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub [8086:2770] (rev 02)
    Subsystem: ASUSTeK Computer Inc. P5LD2-VM Mainboard [1043:817a]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: [e0] Vendor Specific Information: Len=09 <?>

00:01.0 PCI bridge [0604]: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port [8086:2771] (rev 02) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 16 bytes
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: ddf00000-dfffffff
    Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: [88] Subsystem: ASUSTeK Computer Inc. Device [1043:817a]
    Capabilities: [80] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Address: fee0300c  Data: 4191
    Capabilities: [a0] Express (v1) Root Port (Slot+), MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
            ExtTag- RBE- FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 128 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
        LnkCap:    Port #2, Speed 2.5GT/s, Width x16, ASPM L0s, Latency L0 <256ns, L1 <4us
            ClockPM- Surprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x16, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        SltCap:    AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surprise-
            Slot #0, PowerLimit 75.000W; Interlock- NoCompl-
        SltCtl:    Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
            Control: AttnInd Off, PwrInd On, Power- Interlock-
        SltSta:    Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-
            Changed: MRL- PresDet+ LinkState-
        RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
        RootCap: CRSVisible-
        RootSta: PME ReqID 0000, PMEStatus- PMEPending-
    Capabilities: [100 v1] Virtual Channel
        Caps:    LPEVC=0 RefClk=100ns PATEntryBits=1
        Arb:    Fixed+ WRR32- WRR64- WRR128-
        Ctrl:    ArbSelect=Fixed
        Status:    InProgress-
        VC0:    Caps:    PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
            Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
            Ctrl:    Enable+ ID=0 ArbSelect=Fixed TC/VC=01
            Status:    NegoPending- InProgress-
    Capabilities: [140 v1] Root Complex Link
        Desc:    PortNumber=02 ComponentID=01 EltType=Config
        Link0:    Desc:    TargetPort=00 TargetComponent=01 AssocRCRB- LinkType=MemMapped LinkValid+
            Addr:    00000000fed19000
    Kernel driver in use: pcieport

00:1b.0 Audio device [0403]: Intel Corporation NM10/ICH7 Family High Definition Audio Controller [8086:27d8] (rev 01)
    Subsystem: ASUSTeK Computer Inc. P5LD2-VM Mainboard (Realtek ALC 882 codec) [1043:817f]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 16 bytes
    Interrupt: pin A routed to IRQ 42
    Region 0: Memory at dddf8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Address: 00000000fee0300c  Data: 41e1
    Capabilities: [70] Express (v1) Root Complex Integrated Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
            ExtTag- RBE- FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
            MaxPayload 128 bytes, MaxReadReq 128 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
        LnkCap:    Port #0, Speed unknown, Width x0, ASPM unknown, Latency L0 <64ns, L1 <1us
            ClockPM- Surprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; Disabled- Retrain- CommClk-
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed unknown, Width x0, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
    Capabilities: [100 v1] Virtual Channel
        Caps:    LPEVC=0 RefClk=100ns PATEntryBits=1
        Arb:    Fixed- WRR32- WRR64- WRR128-
        Ctrl:    ArbSelect=Fixed
        Status:    InProgress-
        VC0:    Caps:    PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
            Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
            Ctrl:    Enable+ ID=0 ArbSelect=Fixed TC/VC=01
            Status:    NegoPending- InProgress-
        VC1:    Caps:    PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
            Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
            Ctrl:    Enable+ ID=1 ArbSelect=Fixed TC/VC=80
            Status:    NegoPending- InProgress-
    Capabilities: [130 v1] Root Complex Link
        Desc:    PortNumber=0f ComponentID=00 EltType=Config
        Link0:    Desc:    TargetPort=00 TargetComponent=00 AssocRCRB- LinkType=MemMapped LinkValid+
            Addr:    00000000fed1c000
    Kernel driver in use: snd_hda_intel

00:1c.0 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 1 [8086:27d0] (rev 01) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 16 bytes
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: 80000000-801fffff
    Prefetchable memory behind bridge: 0000000080200000-00000000803fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: [40] Express (v1) Root Port (Slot+), MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s unlimited, L1 unlimited
            ExtTag- RBE- FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 128 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
        LnkCap:    Port #1, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <256ns, L1 <4us
            ClockPM- Surprise- LLActRep+ BwNot-
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x0, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        SltCap:    AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug+ Surprise+
            Slot #1, PowerLimit 10.000W; Interlock- NoCompl-
        SltCtl:    Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
            Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
        SltSta:    Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet- Interlock-
            Changed: MRL- PresDet- LinkState-
        RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
        RootCap: CRSVisible-
        RootSta: PME ReqID 0000, PMEStatus- PMEPending-
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Address: fee0300c  Data: 41a1
    Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device [1043:8179]
    Capabilities: [a0] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [100 v1] Virtual Channel
        Caps:    LPEVC=0 RefClk=100ns PATEntryBits=1
        Arb:    Fixed+ WRR32- WRR64- WRR128-
        Ctrl:    ArbSelect=Fixed
        Status:    InProgress-
        VC0:    Caps:    PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
            Arb:    Fixed+ WRR32- WRR64- WRR128- TWRR128- WRR256-
            Ctrl:    Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
            Status:    NegoPending- InProgress-
        VC1:    Caps:    PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
            Arb:    Fixed+ WRR32- WRR64- WRR128- TWRR128- WRR256-
            Ctrl:    Enable- ID=0 ArbSelect=Fixed TC/VC=00
            Status:    NegoPending- InProgress-
    Capabilities: [180 v1] Root Complex Link
        Desc:    PortNumber=01 ComponentID=00 EltType=Config
        Link0:    Desc:    TargetPort=00 TargetComponent=00 AssocRCRB- LinkType=MemMapped LinkValid+
            Addr:    00000000fed1c001
    Kernel driver in use: pcieport

00:1d.0 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 01) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM,P5LD2-VM Mainboard [1043:8179]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 20
    Region 4: I/O ports at 9000 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 [8086:27c9] (rev 01) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM,P5LD2-VM Mainboard [1043:8179]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 17
    Region 4: I/O ports at 9400 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 [8086:27ca] (rev 01) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM,P5LD2-VM Mainboard [1043:8179]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin C routed to IRQ 18
    Region 4: I/O ports at 9800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 [8086:27cb] (rev 01) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM,P5LD2-VM Mainboard [1043:8179]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin D routed to IRQ 19
    Region 4: I/O ports at a000 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller [8086:27cc] (rev 01) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM,P5LD2-VM Mainboard [1043:8179]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 20
    Region 0: Memory at dddffc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Kernel driver in use: ehci-pci

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1) (prog-if 01 [Subtractive decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: dde00000-ddefffff
    Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: [50] Subsystem: ASUSTeK Computer Inc. Device [1043:8179]

00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM Motherboard [1043:8179]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel driver in use: lpc_ich

00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01) (prog-if 8a [Master SecP PriP])
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM Motherboard [1043:8179]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx+
    Latency: 0
    Interrupt: pin A routed to IRQ 22
    Region 0: I/O ports at 01f0 [size=8]
    Region 1: I/O ports at 03f4 [size=1]
    Region 2: I/O ports at 0170 [size=8]
    Region 3: I/O ports at 0374 [size=1]
    Region 4: I/O ports at ffa0 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 IDE interface [0101]: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] [8086:27c0] (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: ASUSTeK Computer Inc. Device [1043:2601]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 23
    Region 0: I/O ports at b800 [size=8]
    Region 1: I/O ports at b400 [size=4]
    Region 2: I/O ports at b000 [size=8]
    Region 3: I/O ports at a800 [size=4]
    Region 4: I/O ports at a400 [size=16]
    Capabilities: [70] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: ata_piix

00:1f.3 SMBus [0c05]: Intel Corporation NM10/ICH7 Family SMBus Controller [8086:27da] (rev 01)
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM Motherboard [1043:8179]
    Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin B routed to IRQ 11
    Region 4: I/O ports at 0400 [size=32]

01:01.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] [1106:3106] (rev 86)
    Subsystem: D-Link System Inc DFE-538TX [1186:1407]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (750ns min, 2000ns max), Cache Line Size: 16 bytes
    Interrupt: pin A routed to IRQ 21
    Region 0: I/O ports at c800 [size=256]
    Region 1: Memory at ddeffc00 (32-bit, non-prefetchable) [size=256]
    Expansion ROM at ddee0000 [disabled] [size=64K]
    Capabilities: [40] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: via-rhine

03:00.0 VGA compatible controller [0300]: NVIDIA Corporation G72 [GeForce 7300 GS] [10de:01df] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: XFX Pine Group Inc. Device [1682:2200]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at df000000 (32-bit, non-prefetchable) [size=16M]
    Region 1: Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Region 3: Memory at de000000 (64-bit, non-prefetchable) [size=16M]
    [virtual] Expansion ROM at ddfe0000 [disabled] [size=128K]
    Capabilities: [60] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
        Address: 0000000000000000  Data: 0000
    Capabilities: [78] Express (v1) Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <256ns, L1 <4us
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x16, ASPM L0s L1, Latency L0 <256ns, L1 <4us
            ClockPM- Surprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; RCB 128 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x16, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
    Capabilities: [100 v1] Virtual Channel
        Caps:    LPEVC=0 RefClk=100ns PATEntryBits=1
        Arb:    Fixed- WRR32- WRR64- WRR128-
        Ctrl:    ArbSelect=Fixed
        Status:    InProgress-
        VC0:    Caps:    PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
            Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
            Ctrl:    Enable+ ID=0 ArbSelect=Fixed TC/VC=01
            Status:    NegoPending- InProgress-
    Capabilities: [128 v1] Power Budgeting <?>
    Kernel driver in use: nvidia

```

---

### Post by william16 on 2014-03-08
Hi.
I haven't had any replies to my post.
Anybody got any ideas on what to try next?

I have experimented with adding "acpi=off noapic nolapic" to the kernel options, and these stop the crashes (suggesting to me that there's something wrong with the SPINLOCK code).  But when I boot this way these kernel options mean that I am running my dual-core CPU as a single core, so things are SSSLLLOOOWWW.

Anyway, here's another crash, this one while I was using the open-source "nouveau" nVidia drivers...

```
[11407.530057] perf samples too long (2517 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[56692.092003] BUG: soft lockup - CPU#1 stuck for 22s! [firefox:1912]
[56692.092003] Modules linked in: vesafb(F) snd_hda_codec_analog gpio_ich snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event nouveau snd_rawmidi mxm_wmi psmouse wmi serio_raw video ppdev ttm drm_kms_helper snd_seq snd_seq_device snd_timer lpc_ich drm rfcomm bnep snd bluetooth parport_pc asus_atk0110 i2c_algo_bit mac_hid soundcore lp parport raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor usb_storage raid6_pq via_rhine raid1 mii raid0 multipath linear microcode floppy
[56692.092003] CPU: 1 PID: 1912 Comm: firefox Tainted: GF            3.11.0-17-generic #31-Ubuntu
[56692.092003] Hardware name: USTek Computer INC. P5L-MX/P5L-MX, BIOS 1103    12/12/2007
[56692.092003] task: ffff8800621f0000 ti: ffff880058826000 task.ti: ffff880058826000
[56692.092003] RIP: 0010:[<ffffffff8104de62>]  [<ffffffff8104de62>] __ticket_spin_lock+0x22/0x30
[56692.092003] RSP: 0000:ffff880058827d18  EFLAGS: 00000212
[56692.092003] RAX: 0000000000006a28 RBX: 0000000000000000 RCX: 00000000000059ea
[56692.092003] RDX: 00000000000059ea RSI: 00003ffffffff000 RDI: ffffea0001633d30
[56692.092003] RBP: ffff880058827d18 R08: ffffea00003e2480 R09: 00000000fffffffc
[56692.092003] R10: 0000000000000001 R11: 0000000000000283 R12: ffff88007d00d800
[56692.092003] R13: ffffea00003e2480 R14: ffff88007d178920 R15: ffff880058827cf8
[56692.092003] FS:  00007fa08630f740(0000) GS:ffff88007fc80000(0000) knlGS:0000000000000000
[56692.092003] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[56692.092003] CR2: 00007fa045b70019 CR3: 0000000062044000 CR4: 00000000000007e0
[56692.092003] Stack:
[56692.092003]  ffff880058827d28 ffffffff816ee85e ffff880058827db8 ffffffff81167977
[56692.092003]  0000000000000246 ffff8800588e2ee0 ffff880058827d98 ffffffff810949da
[56692.092003]  ffff880058827d88 ffffffff00000001 ffffea00003e2480 800000000f892867
[56692.092003] Call Trace:
[56692.092003]  [<ffffffff816ee85e>] _raw_spin_lock+0xe/0x20
[56692.092003]  [<ffffffff81167977>] handle_pte_fault+0x827/0xab0
[56692.092003]  [<ffffffff810949da>] ? try_to_wake_up+0x20a/0x2b0
[56692.092003]  [<ffffffff811689a9>] handle_mm_fault+0x299/0x670
[56692.092003]  [<ffffffff810c3d70>] ? futex_requeue+0x400/0x990
[56692.092003]  [<ffffffff816f28dd>] __do_page_fault+0x14d/0x530
[56692.092003]  [<ffffffff810c48c9>] ? do_futex+0xa9/0x620
[56692.092003]  [<ffffffff816f2cec>] do_page_fault+0x2c/0x50
[56692.092003]  [<ffffffff816ef118>] page_fault+0x28/0x30
[56692.092003] Code: 5d c3 0f 1f 80 00 00 00 00 55 b8 00 00 01 00 48 89 e5 f0 0f c1 07 89 c1 c1 e9 10 66 39 c1 89 ca 74 11 0f 1f 80 00 00 00 00 f3 90 <0f> b7 07 66 39 d0 75 f6 5d c3 0f 1f 40 00 8b 17 55 31 c0 48 89 

```

---

### Post by pqwoerituytrueiwoq on 2014-03-08
I think i have seen that error before, are you overclocking? this can be caused by a unstable overclock

---

### Post by william16 on 2014-03-08
> **pqwoerituytrueiwoq said:**
> I think i have seen that error before, are you overclocking? this can be caused by a unstable overclock

Hi - thanks for your suggestion! :p

I have never over-clocked this machine, but I have experimented with the various clock modes in my attempts to make this machine more stable.  For example, in the BIOS I have tried "Spread Spectrum", "Auto" clocking, and "Manual" clocking (in manual mode I just used the BIOS default values).  I get crashes in all three modes.

---

### Post by pqwoerituytrueiwoq on 2014-03-08
i would suggest researching how to OC your CPU, possibly getting help on overclockers.com
i assume you computer is out of warranty
is is also possible your PSU is not giving the CPU enough power
it probably just needs a little more vcore, hopefully that will get the CPU stable, a CPU on stock settings should be stable, if not it is defective, but you may be able to compensate with a little above stock voltage

---

### Post by william16 on 2014-03-08
> **pqwoerituytrueiwoq said:**
> i would suggest researching how to OC your CPU...
it probably just needs a little more vcore...

I've been googling extensively and I think you might be on to something.  I'm going to experiment and I'll report back.  Thanks for the idea!

---

### Post by pqwoerituytrueiwoq on 2014-03-08
it is possible your motherboard is getting auto values wrong, look up the cpu on cpuworld for the specs you will need when using manual in your bios
[FONT=courier new]sensors[/FONT] is a very useful command
[FONT=courier new]cat /proc/cpuinfo[/FONT] will also help you out

---

### Post by william16 on 2014-04-21
In the end I slowly became suspicious of the power supply in this computer.  It is hard to quantify exactly why, but the suggestions from "[**[COLOR=#000000]pqwoerituytrueiwoq[/COLOR]**]("http://ubuntuforums.org/member.php?u=865458")" got me looking at the voltage levels provided by the "sensors" linux command-line program, and the voltages reported by the BIOS, and somehow I decided that it was worth replacing the power supply.

I bought a small (500W) new power supply made by what I feel is a reputable company and made the swap.

GREAT NEWS:  After replacing the power supply, the crashes completely stopped!  I wanted to wait a while just to be sure, but it is now a few weeks since the new powersupply went in, and I haven't had a single crash since.  The power supply is not something that I would normally worry about, but in this case it totally fixed my problem.

Thanks to those who read my post, and especially to those who responded.

---

### Post by tgalati4 on 2014-04-21
I'm glad you got it sorted out.  This proves once again that error messages in Linux are not helpful when you have a hardware problem.  Your lack of finding answers on google and lack of forum responses also point to a hardware problem because a kernel or software problem would be repeatable and probably fixed by now.  

There are many power supplies that are made of catfood.

---

### Post by wa6dzs on 2014-08-23
I have had the same problem, on an old Dell Precision 360 Workstation that I was working on to install Win-7Ultimate (to replace youngest daughter's XP) and had a bent pin on the DVI_DMS-59 Dual Monitor connector on the nVidia GeForce-5200 card.  Gently fixing that, I couldn't find a worthwhile driver for this eleven-year-old machine. Ordered a NEW video card from NewEgg. Then it become e.x.c.r.u.c.i.a.t.i.n.g.l.y slow. Time to see if any of the Linux tools would help. The Ubuntu 14.0.4.1 install DVD went in, the first logo (box=Vitruvian-man-in-circle) appeared, then this BUG display.
At first, I thought 'Oh-HO! Time to scrap it', but had to Google it, found this thread.  While pulling it carefully apart to find and get a power supply (the existing one is a measly 250W), I noticed that;
Next to the CPU chip heatsink, there is a row of little electrolytic capacitors.  Six of them, taller than the rest (about 20x8mm-dia) are 820uF 6.3V, and each of them is BULGING ON THE TOP. The X across them (there as a final safety valve if the electrolyte boils and it HAS to release the pressure) makes a nice pyramid, obvious in a strong light.
I recalled that <https://http://www.badcaps.net/> had an answer, having to do with bungled industrial espionage and second-and-third-tier electrolytic manufacturers willing to shave a nickel (show me a bean-counter who WON'T) off their cost.
If your power supply can't keep up, take a GOOD LOOK at your motherboard; the tops of all those caps should be FLAT, with perhaps a K or an X scribed into them.  BadCaps.net has lots of photos of ones that have just bulged, and some that have actually leaked gunk all over the board or blown their tops (messy, that).
If you are up for soldering, there may ba a $5US solution (plus shipping, depending on vendor; be sure you get the right PHYSICAL size too. A little over the uF or voltage is likely OK, but never UNDER.)
I'll let you all know how this turns out for me, but to bring up a DVR center/server, think I'll go for it (with the power supply too).

---

### Post by wgualla on 2015-04-15
Hi, it's not a hardware issue. I'm having this same bug message in a VMware virtual machine.

---

### Post by julesbowden on 2015-04-15
This might help someone: I had this same problem on an Asus desktop PC that of course came with windows pre-installed and worked perfectly well (well, you know what I mean) with windows 8. On Ubuntu 14.04, it would run for some period, and then lock up with the CPU Stuck for 23s message.

I tried the following:

Upgrade to 14.10
Try the nvidia proprietary drivers
replace the power supply with a premium 500W unit

All with no success. It would run for no more than about a day without crashing.

Eventually I took out the nvidia graphics card and fell back to the motherboard integrated Intel graphics. Works great, and is perfectly stable.

---

### Post by Fraidoon_Sarwary on 2015-09-22
to : William16: This was a perfect solution for a vague messages in the boot log....THANK YOU!!!!

---

### Post by Locane on 2015-09-22
In case someone else finds this, a kernel upgrade fixed a similar problem for me. I had a JBOD that was attached to the system through a SAS3 controller throwing these CPU Softlock errors on boot.

I had Ubuntu 14.04.2 kernel version 3.16.0-30, and doing a "apt -y upgrade" ended me up at kernel 3.16.0-49, and that solved the problem.

---

### Post by chartre on 2016-02-04
> **wgualla said:**
> Hi, it's not a hardware issue. I'm having this same bug message in a VMware virtual machine.

Actually is a kind of hardware issue. Im using VMware with the configuration set to use 2 cpu cores. Since my PC is a Core2Duo, I was leaving no cores for the Host SO. After change the option the error vanished.

---

### Post by giovanni.n on 2016-03-06
Same problem here. I have nvidia video card.

The pc was going very fine for a long time then i experimented some crashes as in the topic.

The crashes seems related to last distro update (i'm using elementary os freya, based on ubuntu 14.04). Or maybe it's related to some new hardware issue.

Until now i have tried some different kernels and some different nvidia drivers. No success at all.

What i have noticed is that the crash succeded when start working on my pc at beginning of the day ( at cold).
I have tried to leave the pc on for about three days and no crash at all.

So i think it's some hardware issue.  By now, i have removed the nvidia card and i'm testing the stability. If it not working i will change the power supply as suggested in this thread.

---

### Post by cytg on 2016-07-19
ubuntu_mate 16.04

Update, new kernel, boot stuck with "BUG: soft lockup"

I boot with the old kernel (-24) and I am good.
4.4.0-31-generic on virtualbox 5.16 t105871 is broken.

"NMI watchdog: BUG: soft lockup - CPU#0 stuck for 23s! ......"


(for some god forsaken reason i cannot post new threads, i get a 403 forbidden.. damn bus, theyre everywhere)

---

### Post by stormrage2 on 2016-07-20
Updated Ubuntu Linux 3.13.0-88-generic to Ubuntu Linux 3.13.0-92-generic only to be greeted with the dreaded "BUG: soft lockup - CPU#1 stuck for 23s!"

More specifically:

BUG: soft lockup - CPU#1 stuck for 23s! [khugepaged:46]
BUG: soft lockup - CPU#2 stuck for 23s! [ntpdate:593]
BUG: soft lockup - CPU#1 stuck for 22s! [khugepaged:46]
BUG: soft lockup - CPU#2 stuck for 22s! [ntpdate:593]

at which time the VM on ProxMox froze.

"Hard reset" VM and selecting the Ubuntu Linux 3.13.0-88-generic kernel had the VM startup again.

Retried the Ubuntu Linux 3.13.0-92-generic kernel thereafter which has worked without any further issues since ....

No proper idea as to why or how it resolved itself as yet, though need a proper technical explanation for the powers that be.

---

### Post by Dasgrooves on 2016-08-03
so after 2 years, is the problem still solved or has it come bback?

---

### Post by slowjack on 2016-08-09
I got the same error message during installation of ubuntu 16 (4.4.0-31-generic) on my virtualbox.
I needed to switch off "use Host I-O cache". After changing this setting I was able to install ubuntu 16 
on VirtualBox.

---

### Post by knighttechdev on 2016-08-09
I had the same error message in Virtual Box, and when I set the CPU amount to 4 and made sure the USB was set to USB 2.0 then the problem was solved.:KS

---

