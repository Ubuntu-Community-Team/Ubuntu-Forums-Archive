---
title: "soft lockup in kernel forces hard reboot"
date: 2023-05-04
forum: General Help
---

### Post by ssrothman on 2023-05-04
Problem description: very frequently (sometime instantly on boot, sometimes not for a few hours) a kernel task gets stuck in some sort unkillable infinite loop. Any and all open applications then become non-responsive one-by-one, I assume as they try to interact with this kernel process and get stuck waiting for it. The only way to break out of this is to force-restart the computer (ie by holding down the power button). 

The problematic process shows in top as taking 100% cpu and being named kworker/u32:26:561, which I understand to be a dummy name for kernel processes. Attempting to kill it has no effect. In the journalctl log there are messages like the following:

```
May 04 23:25:59 simon-XPS-15-9510 kernel: watchdog: BUG: soft lockup -
CPU#15 stuck for 82s! [kworker/u32:26:561]
May 04 23:25:59 simon-XPS-15-9510 kernel: Modules linked in: rfcomm ccm
cmac algif_hash algif_skcipher af_alg snd_hda_codec_hdmi snd_ctl_led
snd_hda_codec_realtek snd_hda_codec_generic nvid>
May 04 23:25:59 simon-XPS-15-9510 kernel:  crct10dif_pclmul
drm_kms_helper ghash_clmulni_intel hid_sensor_als hid_sensor_trigger
dell_smbios aesni_intel industrialio_triggered_buffer input_>
May 04 23:25:59 simon-XPS-15-9510 kernel:  parport_pc ppdev lp parport
drm ramoops pstore_blk reed_solomon pstore_zone efi_pstore ip_tables
x_tables autofs4 hid_sensor_hub intel_ishtp_loade>
May 04 23:25:59 simon-XPS-15-9510 kernel: CPU: 15 PID: 561 Comm:
kworker/u32:26 Tainted: P           O L    5.14.0-1052-oem #59-Ubuntu
May 04 23:25:59 simon-XPS-15-9510 kernel: Hardware name: Dell Inc. XPS
15 9510/01V4T3, BIOS 1.19.0 03/10/2023
May 04 23:25:59 simon-XPS-15-9510 kernel: Workqueue: netns cleanup_net
May 04 23:25:59 simon-XPS-15-9510 kernel: RIP:
0010:inet_twsk_purge+0xf3/0x150
May 04 23:25:59 simon-XPS-15-9510 kernel: Code: 35 08 8b e8 df 85 62 ff
e8 4a 69 19 00 49 8b 1c 24 f6 c3 01 75 14 0f b6 43 aa 3c 06 0f 84 4d ff
ff ff 48 8b 1b f6 c3 01 74 ec <48> d1 eb 49 3>
May 04 23:25:59 simon-XPS-15-9510 kernel: RSP: 0018:ffffab4f40f43d80
EFLAGS: 00000202
May 04 23:25:59 simon-XPS-15-9510 kernel: RAX: 0000000000000000 RBX:
000002000007d819 RCX: ffffffff8c734bc0
May 04 23:25:59 simon-XPS-15-9510 kernel: RDX: 0000000000000003 RSI:
000000000000000a RDI: ffffffff8c734bc0
May 04 23:25:59 simon-XPS-15-9510 kernel: RBP: ffffab4f40f43db8 R08:
ffffffff8bf58240 R09: ffffffff8afb3701
May 04 23:25:59 simon-XPS-15-9510 kernel: R10: 0000000000000001 R11:
000000000000021f R12: ffff961c83df6060
May 04 23:25:59 simon-XPS-15-9510 kernel: R13: 000000000003ec0c R14:
ffffffff8c1062a8 R15: 000000000000000a
May 04 23:25:59 simon-XPS-15-9510 kernel: FS: 0000000000000000(0000)
GS:ffff96240f5c0000(0000) knlGS:0000000000000000
May 04 23:25:59 simon-XPS-15-9510 kernel: CS:  0010 DS: 0000 ES: 0000
CR0: 0000000080050033
May 04 23:25:59 simon-XPS-15-9510 kernel: CR2: 000055ebd6faa108 CR3:
0000000876410005 CR4: 0000000000770ee0
May 04 23:25:59 simon-XPS-15-9510 kernel: PKRU: 55555554
May 04 23:25:59 simon-XPS-15-9510 kernel: Call Trace:
May 04 23:25:59 simon-XPS-15-9510 kernel:  <TASK>
May 04 23:25:59 simon-XPS-15-9510 kernel: tcpv6_net_exit_batch+0x1a/0x20
May 04 23:25:59 simon-XPS-15-9510 kernel: ops_exit_list.isra.0+0x5d/0x70
May 04 23:25:59 simon-XPS-15-9510 kernel:  cleanup_net+0x206/0x350
May 04 23:25:59 simon-XPS-15-9510 kernel: process_one_work+0x21d/0x3c0
May 04 23:25:59 simon-XPS-15-9510 kernel: worker_thread+0x4d/0x3f0
May 04 23:25:59 simon-XPS-15-9510 kernel:  ? process_one_work+0x3c0/0x3c0
May 04 23:25:59 simon-XPS-15-9510 kernel:  kthread+0x127/0x150
May 04 23:25:59 simon-XPS-15-9510 kernel:  ? set_kthread_struct+0x40/0x40
May 04 23:25:59 simon-XPS-15-9510 kernel:  ret_from_fork+0x1f/0x30
May 04 23:25:59 simon-XPS-15-9510 kernel:  </TASK>
```

Troubleshooting steps taken: I have purged and reinstalled all of my Nvidia drivers, and tried running with both the oem and non-oem kernels from the grub bootloader. The problem usually starts when I try to access a (any) webpage in Firefox. I removed the snap version of Firefox and installed the .deb package and the problem persists. Also although Firefox seems to catalyze it, this doesn't seem to be a network issue as I can still ping e.g. google.com while the kernel process is stuck. 

I'm at a total loss what else I could try, short of nuking everything and trying a fresh install. Please help! I'm hoping the journalctl log pasted above has enough information for you experts to diagnose the issue.

---

### Post by Doug S on 2023-05-05
Soft lockup can be difficult to debug.
Try reducing the maximum CPU frequency a little, or even go as far as disabling turbo boost frequencies entirely.
You could also try [the latest mainline kernel]("https://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D"), just as a test.

---

### Post by ssrothman on 2023-05-05
Thanks for the advice. I have upgraded to the latest mainline kernel (6.3.1) and my problems seem to be gone.

---

### Post by Doug S on 2023-05-06
> **ssrothman said:**
> Thanks for the advice. I have upgraded to the latest mainline kernel (6.3.1) and my problems seem to be gone.So, that means that it is a known problem that has been fixed. Eventually the fix should be backported to the normal Ubuntu kernel updates. Keep trying the new kernels that come as part of regular updates.

---

