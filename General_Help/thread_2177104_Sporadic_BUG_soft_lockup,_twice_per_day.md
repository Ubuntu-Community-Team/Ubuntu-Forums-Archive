---
title: "Sporadic BUG: soft lockup, twice per day"
date: 2013-09-27
forum: General Help
---

### Post by fconcha on 2013-09-27
Hello, I have been using linux for some years, but since approximately one year or more, my PC started to lock completely one per day and sometimes when I shutdown it.

The kernel messages couldn't get to /var/log, but recently I could get the netconsole running and I can receive the messages which are always of the form:
```

[ 1876.164015] BUG: soft lockup - CPU#0 stuck for 23s! [nautilus:3754]
[ 1876.164024] Modules linked in: vesafb netconsole configfs pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) bnep rfcomm bluetooth parport_pc zram(C) ppdev nfsd nfs lockd fscache auth_rpcgss binfmt_misc nfs_acl sunrpc nvidia(PO) snd_hda_codec_hdmi snd_hda_codec_idt snd_hda_intel coretemp snd_ctxfi kvm_intel kvm snd_hda_codec snd_hwdep snd_seq_midi snd_pcm snd_rawmidi snd_seq_midi_event snd_seq snd_seq_device gpio_ich snd_timer snd dcdbas psmouse soundcore microcode mac_hid serio_raw snd_page_alloc lpc_ich hwmon_vid lp parport ahci libahci e1000e
[ 1876.164128] CPU 0 
[ 1876.164130] Modules linked in:[ 1876.164134]  vesafb netconsole configfs pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) bnep rfcomm bluetooth parport_pc zram(C) ppdev nfsd nfs lockd fscache auth_rpcgss binfmt_misc nfs_acl sunrpc nvidia(PO) snd_hda_codec_hdmi snd_hda_codec_idt snd_hda_intel coretemp snd_ctxfi kvm_intel kvm snd_hda_codec snd_hwdep snd_seq_midi snd_pcm snd_rawmidi snd_seq_midi_event snd_seq snd_seq_device gpio_ich snd_timer snd dcdbas psmouse soundcore microcode mac_hid serio_raw snd_page_alloc lpc_ich hwmon_vid lp parport ahci libahci e1000e


[ 1876.164230] Pid: 3754, comm: nautilus Tainted: P         C O 3.5.0-40-generic #62~precise1-Ubuntu Dell Inc.                 Dell DXP061                  /0CT017
[ 1876.164238] RIP: 0010:[<ffffffff81040a50>]  [<ffffffff81040a50>] __ticket_spin_lock+0x20/0x30
[ 1876.164251] RSP: 0000:ffff88012cbd3b68  EFLAGS: 00000293
[ 1876.164254] RAX: 000000000000452a RBX: ffff88005fd0e600 RCX: 0000000000000000
[ 1876.164257] RDX: 000000000000452c RSI: 0000000000000040 RDI: ffffffff81ef6698
[ 1876.164260] RBP: ffff88012cbd3b68 R08: dead000000100100 R09: dead000000200200
[ 1876.164263] R10: ffffea00049a2b40 R11: 00007ffff56576f0 R12: 0000001000000003
[ 1876.164266] R13: 0000004000000050 R14: ffff880133ffda08 R15: ffff8801291d9700
[ 1876.164270] FS:  00007fec52a17980(0000) GS:ffff880133c00000(0000) knlGS:0000000000000000
[ 1876.164273] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[ 1876.164276] CR2: 00000000013270f0 CR3: 000000012af16000 CR4: 00000000000007f0
[ 1876.164280] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[ 1876.164283] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[ 1876.164286] Process nautilus (pid: 3754, threadinfo ffff88012cbd2000, task ffff8801291d9700)
[ 1876.164289] Stack:
[ 1876.164291]  ffff88012cbd3b78 ffffffff8169e21e ffff88012cbd3bc8 ffffffff81162269
[ 1876.164300]  ffff8801291d9700 0000000001327040 ffff88012cfc0580 02000000000330f8
[ 1876.164309]  0000000000000000 00000000000000d0 00000000000200da ffff88012cfc0580
[ 1876.164317] Call Trace:
[ 1876.164326]  [<ffffffff8169e21e>] _raw_spin_lock+0xe/0x20
[ 1876.164333]  [<ffffffff81162269>] __swap_duplicate+0x69/0x170
[ 1876.164338]  [<ffffffff81164fd3>] swapcache_prepare+0x13/0x20
[ 1876.164343]  [<ffffffff811614ea>] read_swap_cache_async+0x7a/0x180
[ 1876.164348]  [<ffffffff8116167e>] swapin_readahead+0x8e/0xd0
[ 1876.164354]  [<ffffffff8114eb5c>] do_swap_page.isra.51+0x10c/0x620
[ 1876.164360]  [<ffffffff81568ebd>] ? sock_recvmsg+0x11d/0x140
[ 1876.164365]  [<ffffffff81150791>] handle_pte_fault+0x1a1/0x200
[ 1876.164370]  [<ffffffff8119b510>] ? __pollwait+0xf0/0xf0
[ 1876.164375]  [<ffffffff811519b9>] handle_mm_fault+0x269/0x340
[ 1876.164379]  [<ffffffff8119b510>] ? __pollwait+0xf0/0xf0
[ 1876.164384]  [<ffffffff816a201e>] do_page_fault+0x17e/0x540
[ 1876.164390]  [<ffffffff81188cb0>] ? vfs_read+0xb0/0x180
[ 1876.164394]  [<ffffffff8169e965>] page_fault+0x25/0x30
[ 1876.164397] Code: 90 90 90 90 90 90 90 90 90 90 90 55 b8 00 00 01 00 48 89 e5 f0 0f c1 07 89 c2 c1 ea 10 66 39 c2 74 13 66 0f 1f 84 00 00 00 00 00 <f3> 90 0f b7 07 66 39 d0 75 f6 5d c3 0f 1f 40 00 8b 17 55 31 c0 
[ 1876.176013] BUG: soft lockup - CPU#1 stuck for 23s! [gnome-fallback-:3745]
[ 1876.176018] Modules linked in: vesafb netconsole configfs pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) bnep rfcomm bluetooth parport_pc zram(C) ppdev nfsd nfs lockd fscache auth_rpcgss binfmt_misc nfs_acl sunrpc nvidia(PO) snd_hda_codec_hdmi snd_hda_codec_idt snd_hda_intel coretemp snd_ctxfi kvm_intel kvm snd_hda_codec snd_hwdep snd_seq_midi snd_pcm snd_rawmidi snd_seq_midi_event snd_seq snd_seq_device gpio_ich snd_timer snd dcdbas psmouse soundcore microcode mac_hid serio_raw snd_page_alloc lpc_ich hwmon_vid lp parport ahci libahci e1000e
[ 1876.176100] CPU 1 
[ 1876.176102] Modules linked in:[ 1876.176105]  vesafb netconsole configfs pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) bnep rfcomm bluetooth parport_pc zram(C) ppdev nfsd nfs lockd fscache auth_rpcgss binfmt_misc nfs_acl sunrpc nvidia(PO) snd_hda_codec_hdmi snd_hda_codec_idt snd_hda_intel coretemp snd_ctxfi kvm_intel kvm snd_hda_codec snd_hwdep snd_seq_midi snd_pcm snd_rawmidi snd_seq_midi_event snd_seq snd_seq_device gpio_ich snd_timer snd dcdbas psmouse soundcore microcode mac_hid serio_raw snd_page_alloc lpc_ich hwmon_vid lp parport ahci libahci e1000e


[ 1876.176282] Pid: 3745, comm: gnome-fallback- Tainted: P         C O 3.5.0-40-generic #62~precise1-Ubuntu Dell Inc.                 Dell DXP061                  /0CT017
[ 1876.176289] RIP: 0010:[<ffffffff81040a58>]  [<ffffffff81040a58>] __ticket_spin_lock+0x28/0x30
[ 1876.176296] RSP: 0000:ffff880110697b68  EFLAGS: 00000297
[ 1876.176299] RAX: 000000000000452a RBX: ffff880116d64500 RCX: 0000000000000000
[ 1876.176302] RDX: 000000000000452b RSI: 0000000000000040 RDI: ffffffff81ef6698
[ 1876.176305] RBP: ffff880110697b68 R08: dead000000100100 R09: dead000000200200
[ 1876.176308] R10: ffffea0004122c80 R11: ffff880128482000 R12: 0000001000000003
[ 1876.176310] R13: 0000004000000050 R14: ffff880133ffda08 R15: ffff880116d64500
[ 1876.176314] FS:  00007fde8047c940(0000) GS:ffff880133c40000(0000) knlGS:0000000000000000
[ 1876.176317] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[ 1876.176320] CR2: 0000000002717f24 CR3: 000000011069f000 CR4: 00000000000007e0
[ 1876.176323] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[ 1876.176325] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[ 1876.176329] Process gnome-fallback- (pid: 3745, threadinfo ffff880110696000, task ffff880116d64500)
[ 1876.176331] Stack:
[ 1876.176334]  ffff880110697b78 ffffffff8169e21e ffff880110697bc8 ffffffff81162269
[ 1876.176342]  ffff880116d64500 0000000002717f40 ffff88012d76b4d0 0200000000032de1
[ 1876.176350]  0000000000000000 00000000000000d0 00000000000200da ffff88012d76b4d0
[ 1876.176358] Call Trace:
[ 1876.176364]  [<ffffffff8169e21e>] _raw_spin_lock+0xe/0x20
[ 1876.176369]  [<ffffffff81162269>] __swap_duplicate+0x69/0x170
[ 1876.176374]  [<ffffffff81164fd3>] swapcache_prepare+0x13/0x20
[ 1876.176379]  [<ffffffff811614ea>] read_swap_cache_async+0x7a/0x180
[ 1876.176384]  [<ffffffff8116167e>] swapin_readahead+0x8e/0xd0
[ 1876.176389]  [<ffffffff8114eb5c>] do_swap_page.isra.51+0x10c/0x620
[ 1876.176393]  [<ffffffff8119b510>] ? __pollwait+0xf0/0xf0
[ 1876.176398]  [<ffffffff81150791>] handle_pte_fault+0x1a1/0x200
[ 1876.176402]  [<ffffffff811519b9>] handle_mm_fault+0x269/0x340
[ 1876.176407]  [<ffffffff816a201e>] do_page_fault+0x17e/0x540
[ 1876.176412]  [<ffffffff8108a8c0>] ? try_to_wake_up+0x200/0x200
[ 1876.176417]  [<ffffffff811d076c>] ? eventfd_read+0x3c/0x70
[ 1876.176421]  [<ffffffff81188cb0>] ? vfs_read+0xb0/0x180
[ 1876.176426]  [<ffffffff8169e965>] page_fault+0x25/0x30
[ 1876.176429] Code: 90 90 90 55 b8 00 00 01 00 48 89 e5 f0 0f c1 07 89 c2 c1 ea 10 66 39 c2 74 13 66 0f 1f 84 00 00 00 00 00 f3 90 0f b7 07 66 39 d0 <75> f6 5d c3 0f 1f 40 00 8b 17 55 31 c0 48 89 e5 89 d1 c1 e9 10 

```

And always with different processes, for example 
[LIST]
[*]CPU#0 nautilus, CPU#1 gnome-fallback-,
[*]CPU#0 gnome-settings-, CPU#1 gvfs-gphoto2-vo
[/LIST]

I suspected for and hardware problem so I changed the hard disk for my computer (with an AMD Athlon(tm) 64 X2 Dual Core Processor 5400+) to an compute with (Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz) and the problem keep repeating.

I'm using Ubuntu 12.04 with the kernel:[INDENT]Linux version 3.5.0-40-generic (buildd@panlong) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #62~precise1-Ubuntu SMP Fri Aug 23 17:38:26 UTC 2013 (Ubuntu 3.5.0-40.62~precise1-generic 3.5.7.20)


[/INDENT]
But with the normal kernel 3.2 I still face the Issue.

Any Idea how to debug the problem ideally without the need of reinstall everything, thanks

---

### Post by tgalati4 on 2013-09-27
vesafb is the VESA framebuffer driver and the soft lockup could be the CPU waiting for the GPU to do something.  Have you opened up your machine and cleaned it and reseated all RAM can cables?

You also mentioned changing the hard disk, but then you reference two different motherboards (from AMD to Intel), so I am just as confused.

---

### Post by fconcha on 2013-09-27
The first thing's that I did was change the RAM, work only with one slot of ram, take out the majority of PCI cards (a lot of ethernet interfaces) and since the bug still continued I changed my computer, maintaining only the hard disk, so i didn't change my ubuntu installation.

I'm using the NVIDIA driver with an PCI-Express card in the both computer that I have tried, I'm guessing it could be something with the ubuntu [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack), so I downgrade the kernel to the 3.2.0-54-generic, I guess in the next week I will see if the bug continues, it's very random but the past monts it has been happening almost one time daily

---

