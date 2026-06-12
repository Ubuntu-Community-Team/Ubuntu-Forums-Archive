---
title: "Nvidia driver problem/crash..."
date: 2008-07-05
forum: General Help
---

### Post by babylon2233 on 2008-07-05
I'm using Ubuntu 8.04. The problem is sometimes the vga output gone just like that. I mean no input for my monitor. I believe it cause by my Nvidia graphic card driver. 

This is where it happen.. Just after I start Super Tuxcart.. Before, it happens when I'm using Firefox but i believe non of this apps is the cause.

```


Jul  5 22:50:04 Deep-Red kernel: [16189.833510] BUG: soft lockup - CPU#1 stuck for 11s! [supertuxkart:11076]
Jul  5 22:50:04 Deep-Red kernel: [16189.833514] 
Jul  5 22:50:04 Deep-Red kernel: [16189.833516] Pid: 11076, comm: supertuxkart Tainted: P        (2.6.24-19-generic #1)
Jul  5 22:50:04 Deep-Red kernel: [16189.833518] EIP: 0060:[<f97739c8>] EFLAGS: 00000202 CPU: 1
Jul  5 22:50:04 Deep-Red kernel: [16189.833678] EIP is at _nv003992rm+0x23/0x24 [nvidia]
Jul  5 22:50:04 Deep-Red kernel: [16189.833680] EAX: 00000000 EBX: dfb4c000 ECX: 00009410 EDX: f9b80000
Jul  5 22:50:04 Deep-Red kernel: [16189.833682] ESI: df9ce800 EDI: 00000000 EBP: e70af9a8 ESP: dfa67c1c
Jul  5 22:50:04 Deep-Red kernel: [16189.833683]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
Jul  5 22:50:04 Deep-Red kernel: [16189.833685] CR0: 80050033 CR2: b7a34000 CR3: 26da9000 CR4: 00000690
Jul  5 22:50:04 Deep-Red kernel: [16189.833687] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
Jul  5 22:50:04 Deep-Red kernel: [16189.833688] DR6: ffff0ff0 DR7: 00000400
Jul  5 22:50:04 Deep-Red kernel: [16189.833696]  [<f966c609>] _nv008240rm+0x1c/0x9c [nvidia]
Jul  5 22:50:04 Deep-Red kernel: [16189.833851]  [<f97e16d1>] _nv001587rm+0x1b/0xf9 [nvidia]
Jul  5 22:50:04 Deep-Red kernel: [16189.833983]  [<f97e00ca>] _nv001607rm+0xc0/0x102 [nvidia]
Jul  5 22:50:04 Deep-Red kernel: [16189.834116]  [<f973603a>] _nv008726rm+0xdf/0x1a4 [nvidia]
Jul  5 22:50:04 Deep-Red kernel: [16189.834261]  [<f949d261>] _nv015640rm+0xa5/0x17e [nvidia]
Jul  5 22:50:04 Deep-Red kernel: [16189.834354]  [<f949d43a>] _nv015642rm+0x100/0x10a [nvidia]
Jul  5 22:50:04 Deep-Red kernel: [16189.834448]  [<f94a4b34>] _nv015506rm+0x805/0x82e [nvidia]
Jul  5 22:50:04 Deep-Red kernel: [16189.834546]  [<f94a5242>] _nv015509rm+0xb3/0x3a4 [nvidia]
Jul  5 22:50:04 Deep-Red kernel: [16189.834641]  [<f9621d7b>] _nv009280rm+0x3fa/0x4b5 [nvidia]
Jul  5 22:50:04 Deep-Red kernel: [16189.834788]  [<f963ed16>] _nv009451rm+0x224/0x2f4 [nvidia]
Jul  5 22:50:04 Deep-Red kernel: [16189.834962]  [<f963d51a>] _nv009671rm+0x7f/0x20b [nvidia]
Jul  5 22:50:04 Deep-Red kernel: [16189.835119]  [<f97a1c9f>] _nv003318rm+0x144/0x23e [nvidia]
Jul  5 22:50:04 Deep-Red kernel: [16189.835261]  [<f97a1a71>] _nv003317rm+0x42d/0x517 [nvidia]
Jul  5 22:50:04 Deep-Red kernel: [16189.835402]  [<f963facf>] _nv009354rm+0x3df/0xcf5 [nvidia]
Jul  5 22:50:04 Deep-Red kernel: [16189.835558]  [<f9624694>] _nv009360rm+0x39/0x3f [nvidia]
Jul  5 22:50:04 Deep-Red kernel: [16189.835708]  [<f9640483>] _nv009348rm+0x9e/0x887 [nvidia]
Jul  5 22:50:04 Deep-Red kernel: [16189.835856]  [<f96f2c30>] _nv005862rm+0x439/0x5df [nvidia]
Jul  5 22:50:04 Deep-Red kernel: [16189.836006]  [<f9646103>] _nv009284rm+0x12f/0x188 [nvidia]
Jul  5 22:50:04 Deep-Red kernel: [16189.836153]  [<f97145da>] _nv003038rm+0x184/0x449 [nvidia]
Jul  5 22:50:04 Deep-Red kernel: [16189.836297]  [<f9713a72>] _nv003039rm+0x12f/0x2e1 [nvidia]
Jul  5 22:50:04 Deep-Red kernel: [16189.836440]  [<f970ff60>] _nv005240rm+0x4e/0x75 [nvidia]
Jul  5 22:50:04 Deep-Red kernel: [16189.836585]  [<f95d588d>] _nv002985rm+0x195/0x5fd [nvidia]
Jul  5 22:50:04 Deep-Red kernel: [16189.836720]  [<f9778fed>] rm_ioctl+0x3e/0x6d [nvidia]
Jul  5 22:50:04 Deep-Red kernel: [16189.836871]  [<f981df07>] nv_kern_ioctl+0x117/0x3b0 [nvidia]
Jul  5 22:50:04 Deep-Red kernel: [16189.837002]  [set_next_entity+0x1c/0x50] set_next_entity+0x1c/0x50
Jul  5 22:50:04 Deep-Red kernel: [16189.837009]  [irq_entries_start+0x39/0xe00] irq_entries_start+0x39/0xe00
Jul  5 22:50:04 Deep-Red kernel: [16189.837012]  [<f981e1d8>] nv_kern_unlocked_ioctl+0x18/0x20 [nvidia]
Jul  5 22:50:04 Deep-Red kernel: [16189.837140]  [<f981e1c0>] nv_kern_unlocked_ioctl+0x0/0x20 [nvidia]
Jul  5 22:50:04 Deep-Red kernel: [16189.837254]  [do_ioctl+0x2b/0x90] do_ioctl+0x2b/0x90
Jul  5 22:50:04 Deep-Red kernel: [16189.837266]  [vfs_ioctl+0x22e/0x2b0] vfs_ioctl+0x22e/0x2b0
Jul  5 22:50:04 Deep-Red kernel: [16189.837272]  [sys_ioctl+0x56/0x70] sys_ioctl+0x56/0x70
Jul  5 22:50:04 Deep-Red kernel: [16189.837277]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
Jul  5 22:50:04 Deep-Red kernel: [16189.837280]  [irq_entries_start+0x39/0xe00] irq_entries_start+0x39/0xe00


```

Thanks in advance.

---

