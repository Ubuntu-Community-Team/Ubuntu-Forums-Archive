---
title: "Hardy - System frozen after locking screen"
date: 2008-05-23
forum: General Help
---

### Post by dbrummer on 2008-05-23
Hello,
I have Hardy Heron running on a Dell GX620 (3.4GHz Intel, 2.75GB RAM).  When I leave for the day I lock my screen.  When I come back the next morning to log in to my desktop the computer is completely frozen.  I try key presses and moving the mouse but both monitors show no signal from the desktop.  This has happened multiple times the past week.  My PC doesn't respond to network requests so I have to hard boot it.  Sometimes during the week when I go to lunch and come back and try to unlock my machine, only one monitor returns.

All hardware connections have been verified so it's not a connection issue.  I'm not sure what I can look at for in the logs or what troubleshooting techniques I should try.

Any help is greatly appreciated.

Thank you,
Dan

---

### Post by dbrummer on 2008-05-23
I'm not sure if this is the cause of the problem, but I have this entry in my /var/log/messages file every 10-15 seconds:

May 22 18:36:01 danb kernel: [16899.272290] Pid: 5593, comm: Xorg Tainted: P        (2.6.24-17-generic #1)
May 22 18:36:01 danb kernel: [16899.272294] EIP: 0060:[<f8cd2600>] EFLAGS: 00203293 CPU: 1
May 22 18:36:01 danb kernel: [16899.272417] EIP is at _ZN4Asic16Is_WPTR_equ_RPTR19ConditionSuccessfulEv+0x0/0x50 [fglrx]
May 22 18:36:01 danb kernel: [16899.272423] EAX: f8d35430 EBX: 007ffff9 ECX: 00000000 EDX: f8d35430
May 22 18:36:01 danb kernel: [16899.272427] ESI: 00000000 EDI: df8c3d98 EBP: df8c3d20 ESP: df8c3d04
May 22 18:36:01 danb kernel: [16899.272433]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
May 22 18:36:01 danb kernel: [16899.272437] CR0: 80050033 CR2: a3625000 CR3: 37fde000 CR4: 00000690
May 22 18:36:01 danb kernel: [16899.272441] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
May 22 18:36:01 danb kernel: [16899.272446] DR6: ffff0ff0 DR7: 00000400
May 22 18:36:01 danb kernel: [16899.272451]  [<f8cd16e8>] _ZN4Asic9WaitUntil15WaitForCompleteEv+0x38/0xf0 [fglrx]
May 22 18:36:01 danb kernel: [16899.272599]  [<f8cd5786>] _ZN6AsicR616ASICIdleInternalEN4Asic15idle_WaitMethodE+0x96/0x1f0 [fglrx]
May 22 18:36:01 danb kernel: [16899.272741]  [enqueue_entity+0x2b/0x60] enqueue_entity+0x2b/0x60
May 22 18:36:01 danb kernel: [16899.272858]  [<f8cb34b6>] QSSubmitList+0x146/0x150 [fglrx]
May 22 18:36:01 danb kernel: [16899.272975]  [<f8ccff9c>] _ZN4Asic7PM4idleENS_15idle_WaitMethodE+0x4c/0x80 [fglrx]
May 22 18:36:01 danb kernel: [16899.273118]  [<f8cca645>] _ZN15QS_PRIVATE_CORE7PM4idleEN4Asic15idle_WaitMethodE+0x35/0x70 [fglrx]
May 22 18:36:01 danb kernel: [16899.273256]  [<f8cba321>] _ZN10QS_PRIVATE11synchronizeEv+0x31/0x40 [fglrx]
May 22 18:36:01 danb kernel: [16899.273379]  [<f8cb34d7>] QSSynchronize+0x17/0x20 [fglrx]
May 22 18:36:01 danb kernel: [16899.273497]  [<f8cbae69>] _Z14uQSSynchronizej+0x19/0x20 [fglrx]
May 22 18:36:01 danb kernel: [16899.273621]  [<f8cc249f>] _Z8uCWDDEQCjjjPvjS_+0x33f/0x11a0 [fglrx]
May 22 18:36:01 danb kernel: [16899.273775]  [<f8cb2df4>] CMMQS_uCWDDEQC+0x34/0x40 [fglrx]
May 22 18:36:01 danb kernel: [16899.273906]  [<f8c79e48>] firegl_cmmqs_CWDDE_32+0x238/0x340 [fglrx]
May 22 18:36:01 danb kernel: [16899.274032]  [sys_quotactl+0x5a6/0x680] sys_quotactl+0x5a6/0x680
May 22 18:36:01 danb kernel: [16899.274043]  [<f8c78e06>] firegl_cmmqs_CWDDE32+0x76/0x110 [fglrx]
May 22 18:36:01 danb kernel: [16899.274194]  [<f8c78d90>] firegl_cmmqs_CWDDE32+0x0/0x110 [fglrx]
May 22 18:36:01 danb kernel: [16899.274292]  [<f8c6b4be>] firegl_ioctl+0x19e/0x220 [fglrx]
May 22 18:36:01 danb kernel: [16899.274381]  [sys_quotactl+0x5a6/0x680] sys_quotactl+0x5a6/0x680
May 22 18:36:01 danb kernel: [16899.274407]  [run_timer_softirq+0x30/0x1e0] run_timer_softirq+0x30/0x1e0
May 22 18:36:01 danb kernel: [16899.274434]  [sys_quotactl+0x5a6/0x680] sys_quotactl+0x5a6/0x680
May 22 18:36:01 danb kernel: [16899.274444]  [<f8c6085c>] ip_firegl_ioctl+0x1c/0x30 [fglrx]
May 22 18:36:01 danb kernel: [16899.274532]  [sys_quotactl+0x5a6/0x680] sys_quotactl+0x5a6/0x680
May 22 18:36:01 danb kernel: [16899.274547]  [do_ioctl+0x78/0x90] do_ioctl+0x78/0x90
May 22 18:36:01 danb kernel: [16899.274573]  [vfs_ioctl+0x22e/0x2b0] vfs_ioctl+0x22e/0x2b0
May 22 18:36:01 danb kernel: [16899.274602]  [sys_ioctl+0x56/0x70] sys_ioctl+0x56/0x70
May 22 18:36:01 danb kernel: [16899.274625]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
May 22 18:36:01 danb kernel: [16899.274637]  [sys_quotactl+0x5a6/0x680] sys_quotactl+0x5a6/0x680
May 22 18:36:01 danb kernel: [16899.274668]  [unix_dgram_recvmsg+0x110/0x2d0] unix_dgram_recvmsg+0x110/0x2d0
May 22 18:36:01 danb kernel: [16899.274704]  =======================

---

