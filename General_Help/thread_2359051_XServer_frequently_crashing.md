---
title: "XServer frequently crashing"
date: 2017-04-20
forum: General Help
---

### Post by inte2 on 2017-04-20
Hi,

I just installed Ubuntu (16.04 LTS neon flavor) on my X200 laptop and the xserver is frequently crashing (freezing):

That's from the logs:

Apr 20 08:18:30 cintema-ThinkPad-X200 kernel: [58362.844087] INFO: task Xorg:1025 blocked for more than 120 seconds.
Apr 20 08:18:30 cintema-ThinkPad-X200 kernel: [58362.844100]       Tainted: G           OE   4.8.0-46-generic #49~16.04.1-Ubuntu
Apr 20 08:18:30 cintema-ThinkPad-X200 kernel: [58362.844104] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Apr 20 08:18:30 cintema-ThinkPad-X200 kernel: [58362.844109] Xorg            D ffff94b8ef543b78     0  1025    987 0x00400004
Apr 20 08:18:30 cintema-ThinkPad-X200 kernel: [58362.844121]  ffff94b8ef543b78 ffff94b8effb6a00 ffff94b86ccb0dc0 ffff94b8f20244c0
Apr 20 08:18:30 cintema-ThinkPad-X200 kernel: [58362.844128]  ffff94b8f20244c0 ffff94b8ef544000 7fffffffffffffff ffff94b8ef543cc8
Apr 20 08:18:30 cintema-ThinkPad-X200 kernel: [58362.844135]  ffff94b8f20244c0 ffff94b8ee971e00 ffff94b8ef543b90 ffffffff95895fd5
Apr 20 08:18:30 cintema-ThinkPad-X200 kernel: [58362.844142] Call Trace:
Apr 20 08:18:30 cintema-ThinkPad-X200 kernel: [58362.844157]  [<ffffffff95895fd5>] schedule+0x35/0x80
Apr 20 08:18:30 cintema-ThinkPad-X200 kernel: [58362.844164]  [<ffffffff95899805>] schedule_timeout+0x235/0x3f0
Apr 20 08:18:30 cintema-ThinkPad-X200 kernel: [58362.844173]  [<ffffffff950adf80>] ? check_preempt_curr+0x80/0x90
Apr 20 08:18:30 cintema-ThinkPad-X200 kernel: [58362.844177]  [<ffffffff950adfa9>] ? ttwu_do_wakeup+0x19/0xe0
Apr 20 08:18:30 cintema-ThinkPad-X200 kernel: [58362.844182]  [<ffffffff950aebd8>] ? try_to_wake_up+0x58/0x3e0
Apr 20 08:18:30 cintema-ThinkPad-X200 kernel: [58362.844188]  [<ffffffff95896a33>] wait_for_completion+0xb3/0x140
Apr 20 08:18:30 cintema-ThinkPad-X200 kernel: [58362.844192]  [<ffffffff950aeff0>] ? wake_up_q+0x70/0x70
Apr 20 08:18:30 cintema-ThinkPad-X200 kernel: [58362.844197]  [<ffffffff9509e856>] flush_work+0x116/0x1c0
Apr 20 08:18:30 cintema-ThinkPad-X200 kernel: [58362.844204]  [<ffffffff9509abe0>] ? destroy_worker+0x90/0x90
Apr 20 08:18:30 cintema-ThinkPad-X200 kernel: [58362.844261]  [<ffffffffc03ed140>] drm_mode_rmfb+0x170/0x1c0 [drm]
Apr 20 08:18:30 cintema-ThinkPad-X200 kernel: [58362.844303]  [<ffffffffc03e81c0>] ? drm_framebuffer_remove+0x150/0x150 [drm]
Apr 20 08:18:30 cintema-ThinkPad-X200 kernel: [58362.844337]  [<ffffffffc03ded67>] drm_ioctl+0x1e7/0x4c0 [drm]
Apr 20 08:18:30 cintema-ThinkPad-X200 kernel: [58362.844380]  [<ffffffffc03ecfd0>] ? drm_mode_addfb+0xb0/0xb0 [drm]
Apr 20 08:18:30 cintema-ThinkPad-X200 kernel: [58362.844387]  [<ffffffff952330d9>] ? do_readv_writev+0x149/0x240
Apr 20 08:18:30 cintema-ThinkPad-X200 kernel: [58362.844394]  [<ffffffff952478c1>] do_vfs_ioctl+0xa1/0x5f0
Apr 20 08:18:30 cintema-ThinkPad-X200 kernel: [58362.844399]  [<ffffffff95247e89>] SyS_ioctl+0x79/0x90
Apr 20 08:18:30 cintema-ThinkPad-X200 kernel: [58362.844406]  [<ffffffff9589a7f6>] entry_SYSCALL_64_fastpath+0x1e/0xa8

No idea what to do next.
Thank you in advance!

---

