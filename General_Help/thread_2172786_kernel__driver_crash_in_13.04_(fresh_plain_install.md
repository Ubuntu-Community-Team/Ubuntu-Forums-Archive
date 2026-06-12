---
title: "kernel / driver crash in 13.04 (fresh plain install, fully updated)"
date: 2013-09-06
forum: General Help
---

### Post by sanderj on 2013-09-06
Anything I can do about this kernel / driver crash in 13.04 (fresh plain install, fully updated)?

I think it is related to my eth driver; afterwards eth was not working anymore. After rebooting the router (!) it worked again ... :(

dmesg output:

```
[ 2152.143054] ------------[ cut here ]------------
[ 2152.143073] WARNING: at /build/buildd/linux-3.8.0/net/sched/sch_generic.c:254 dev_watchdog+0x242/0x250()
[ 2152.143077] Hardware name: R530/R730/R540              
[ 2152.143081] NETDEV WATCHDOG: eth0 (sky2): transmit queue 0 timed out
[ 2152.143083] Modules linked in: hid_generic usbhid hid vesafb(F) parport_pc(F) snd_hda_codec_hdmi ppdev(F) snd_hda_codec_realtek joydev(F) coretemp kvm_intel(F) kvm(F) rfcomm bnep bluetooth arc4(F) samsung_laptop snd_hda_intel ath9k snd_hda_codec ath9k_common microcode(F) snd_hwdep(F) snd_pcm(F) ath9k_hw snd_page_alloc(F) snd_seq_midi(F) snd_seq_midi_event(F) ath snd_rawmidi(F) uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev mac80211 snd_seq(F) cfg80211 i915 psmouse(F) mac_hid serio_raw(F) snd_seq_device(F) video(F) snd_timer(F) drm_kms_helper drm intel_ips snd(F) lpc_ich i2c_algo_bit soundcore(F) lp(F) parport(F) ahci(F) libahci(F) sky2
[ 2152.143174] Pid: 0, comm: swapper/2 Tainted: GF            3.8.0-30-generic #44-Ubuntu
[ 2152.143177] Call Trace:
[ 2152.143180]  <IRQ>  [<ffffffff810589bf>] warn_slowpath_common+0x7f/0xc0
[ 2152.143195]  [<ffffffff81058abc>] warn_slowpath_fmt+0x4c/0x50
[ 2152.143204]  [<ffffffff81074e84>] ? insert_work+0x94/0xb0
[ 2152.143213]  [<ffffffff815e8a32>] dev_watchdog+0x242/0x250
[ 2152.143220]  [<ffffffff815e87f0>] ? dev_graft_qdisc+0x90/0x90
[ 2152.143227]  [<ffffffff810682a6>] call_timer_fn+0x36/0x110
[ 2152.143233]  [<ffffffff815e87f0>] ? dev_graft_qdisc+0x90/0x90
[ 2152.143239]  [<ffffffff81069ed6>] run_timer_softirq+0x1f6/0x2a0
[ 2152.143248]  [<ffffffff8106110f>] __do_softirq+0xcf/0x200
[ 2152.143256]  [<ffffffff81574100>] ? centrino_target+0x370/0x370
[ 2152.143264]  [<ffffffff816d6bdc>] call_softirq+0x1c/0x30
[ 2152.143274]  [<ffffffff81016555>] do_softirq+0x75/0xb0
[ 2152.143280]  [<ffffffff810613a5>] irq_exit+0xa5/0xb0
[ 2152.143286]  [<ffffffff816d755e>] smp_apic_timer_interrupt+0x6e/0x99
[ 2152.143292]  [<ffffffff816d649d>] apic_timer_interrupt+0x6d/0x80
[ 2152.143295]  <EOI>  [<ffffffff81574b48>] ? cpuidle_wrap_enter+0x58/0xa0
[ 2152.143307]  [<ffffffff81574ba0>] cpuidle_enter_tk+0x10/0x20
[ 2152.143312]  [<ffffffff81574795>] cpuidle_idle_call+0xa5/0x260
[ 2152.143319]  [<ffffffff8101d5af>] cpu_idle+0xaf/0x120
[ 2152.143326]  [<ffffffff816b6bf3>] start_secondary+0x1e0/0x1e5
[ 2152.143330] ---[ end trace 2b405393b6e846ae ]---
[ 2152.143338] sky2 0000:06:00.0 eth0: tx timeout
[ 2152.143350] sky2 0000:06:00.0 eth0: transmit ring 86 .. 100 report=86 done=86
```

```
sander@flappie:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 13.04
Release:	13.04
Codename:	raring
sander@flappie:~$ uname -a
Linux flappie 3.8.0-30-generic #44-Ubuntu SMP Thu Aug 22 20:52:24 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
sander@flappie:~$ 
```

---

