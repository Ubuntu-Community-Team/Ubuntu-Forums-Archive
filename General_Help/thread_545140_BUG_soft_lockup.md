---
title: "BUG: soft lockup"
date: 2007-09-07
forum: General Help
---

### Post by sblanzio on 2007-09-07
when I got home this afternoon I found my screen blank (in standby monitor) and couldn't come back to gnome with any key or mouse movement.

I rebooted, looked in /var/log/syslog and I found this at the time it stopped.

```

Sep  7 11:38:40 enrico-desktop kernel: [51941.784000] BUG: soft lockup detected on CPU#0!
Sep  7 11:38:40 enrico-desktop kernel: [51941.784000]  [softlockup_tick+156/240] softlockup_tick+0x9c/0xf0
Sep  7 11:38:40 enrico-desktop kernel: [51941.784000]  [update_process_times+51/128] update_process_times+0x33/0x80
Sep  7 11:38:40 enrico-desktop kernel: [51941.784000]  [smp_apic_timer_interrupt+112/128] smp_apic_timer_interrupt+0x70/0x80
Sep  7 11:38:40 enrico-desktop kernel: [51941.784000]  [apic_timer_interrupt+40/48] apic_timer_interrupt+0x28/0x30
Sep  7 11:38:40 enrico-desktop kernel: [51941.784000]  [_spin_unlock_irqrestore+13/32] _spin_unlock_irqrestore+0xd/0x20
Sep  7 11:38:40 enrico-desktop kernel: [51941.784000]  [try_to_del_timer_sync+71/80] try_to_del_timer_sync+0x47/0x50
Sep  7 11:38:40 enrico-desktop kernel: [51941.784000]  [del_timer_sync+14/32] del_timer_sync+0xe/0x20
Sep  7 11:38:40 enrico-desktop kernel: [51941.784000]  [<f8b0026a>] MlmeJoinReqAction+0x2a/0xe0 [rt61]
Sep  7 11:38:40 enrico-desktop kernel: [51941.784000]  [<f8b00030>] BeaconTimeout+0x0/0x30 [rt61]
Sep  7 11:38:40 enrico-desktop kernel: [51941.784000]  [<f8af57de>] StateMachinePerformAction+0x1e/0x30 [rt61]
Sep  7 11:38:40 enrico-desktop kernel: [51941.784000]  [<f8afa43b>] MlmeHandler+0x10b/0x170 [rt61]
Sep  7 11:38:40 enrico-desktop kernel: [51941.784000]  [run_timer_softirq+303/416] run_timer_softirq+0x12f/0x1a0
Sep  7 11:38:40 enrico-desktop kernel: [51941.784000]  [timer_interrupt+89/176] timer_interrupt+0x59/0xb0
Sep  7 11:38:40 enrico-desktop kernel: [51941.784000]  [__do_softirq+130/256] __do_softirq+0x82/0x100
Sep  7 11:38:40 enrico-desktop kernel: [51941.784000]  [do_softirq+85/96] do_softirq+0x55/0x60
Sep  7 11:38:40 enrico-desktop kernel: [51941.784000]  [smp_apic_timer_interrupt+117/128] smp_apic_timer_interrupt+0x75/0x80
Sep  7 11:38:40 enrico-desktop kernel: [51941.784000]  [apic_timer_interrupt+40/48] apic_timer_interrupt+0x28/0x30
Sep  7 11:38:40 enrico-desktop kernel: [51941.784000]  [default_idle+0/96] default_idle+0x0/0x60
Sep  7 11:38:40 enrico-desktop kernel: [51941.784000]  [native_safe_halt+2/16] native_safe_halt+0x2/0x10
Sep  7 11:38:40 enrico-desktop kernel: [51941.784000]  [default_idle+61/96] default_idle+0x3d/0x60
Sep  7 11:38:40 enrico-desktop kernel: [51941.784000]  [cpu_idle+73/208] cpu_idle+0x49/0xd0
Sep  7 11:38:40 enrico-desktop kernel: [51941.784000]  [start_kernel+869/1056] start_kernel+0x365/0x420
Sep  7 11:38:40 enrico-desktop kernel: [51941.784000]  [unknown_bootoption+0/608] unknown_bootoption+0x0/0x260
Sep  7 11:38:40 enrico-desktop kernel: [51941.784000]  =======================

```

Should I worry?

I have kept my pc on for almost 3 days continuosly without any problem. Yesterday I started it on evening and it has worked untile 11am...

I found this could be realted to wifi troubles, but i have had this wifi card since a long time and never had this problem before (at least as much as I can remember).

I can't say if the wifi access point was down in that moment... could I in any way?

EDIT: this is my system
Linux enrico-desktop 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686 GNU/Linux
Athlond 64X2 +3800
1Gb Ram Kingstone
MB M2A-MVP ASUS
NVIDIA 6600GT 128Mb

any hint?
thanks

---

