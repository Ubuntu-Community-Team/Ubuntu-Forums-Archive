---
title: "Ubuntu 21.04 kernel lock up early boot NVIDIA drivers"
date: 2021-06-02
forum: General Help
---

### Post by mongoosex on 2021-06-02
Ubuntu version:
Ubuntu 21.04

Board:
Gigabyte Technology Co., Ltd. AB350M-Gaming 3/AB350M-Gaming 3-CF, BIOS F42d 10/18/2019

GFX:
Nvidia 1060 6Gb

CPU:
AMD Ryzen 5 1600 Six-Core Processor (family: 0x17, model: 0x1, stepping: 0x1)

Form:
Desktop PC

I updated yesterday which appeared to add a new kernel and nvidia drivers.

Now when the system boots, it freezes before even leaving the Gigabyte BIOS screen after selecting "Ubuntu" on the grub screen.

It will boot into recovery mode and looking in /var/log/kern.log I find this:

Jun  2 10:17:51 mediapc kernel: [   12.968520] Hardware name: Gigabyte Technology Co., Ltd. AB350M-Gaming 3/AB350M-Gaming 3-CF, BIOS F42d 10/18/2019
Jun  2 10:17:51 mediapc kernel: [   12.968521] RIP: 0010:_nv015534rm+0x1b6/0x330 [nvidia]
Jun  2 10:17:51 mediapc kernel: [   12.968842] Code: 8b 87 68 05 00 00 ba 01 00 00 00 be 02 00 00 00 e8 bf 6b 0d f5 41 83 c5 01 41 83 fd 1f 0f 84 0b 01 00 00 48 8b 45 10 44 89 ee <48> 8b b8 70 01 00 00 48 8b 87 d8 04 00 00 e8 97 6b 0d f5 89 c3 48
Jun  2 10:17:51 mediapc kernel: [   12.968843] RSP: 0018:ffffb9cd8280f958 EFLAGS: 00010293
Jun  2 10:17:51 mediapc kernel: [   12.968845] RAX: 0000000000000000 RBX: 0000000000002000 RCX: 0000000000000002
Jun  2 10:17:51 mediapc kernel: [   12.968846] RDX: 0000000000000004 RSI: 0000000000000002 RDI: 0000000000000000
Jun  2 10:17:51 mediapc kernel: [   12.968847] RBP: ffff9dd5818e5dd0 R08: 0000000000000001 R09: ffff9dd5818e5cb8
Jun  2 10:17:51 mediapc kernel: [   12.968848] R10: ffff9dd580bac008 R11: 0000000010100000 R12: 0000000000002000
Jun  2 10:17:51 mediapc kernel: [   12.968849] R13: 0000000000000002 R14: ffff9dd57b8b4010 R15: 0000000000000400
Jun  2 10:17:51 mediapc kernel: [   12.968850] FS:  00007fc5135eca40(0000) GS:ffff9dd84e8c0000(0000) knlGS:0000000000000000
Jun  2 10:17:51 mediapc kernel: [   12.968851] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Jun  2 10:17:51 mediapc kernel: [   12.968852] CR2: 0000000000000170 CR3: 0000000109ac0000 CR4: 00000000003506e0
Jun  2 10:17:51 mediapc kernel: [   12.968853] Call Trace:
Jun  2 10:17:51 mediapc kernel: [   12.968856]  ? _nv015556rm+0x7fd/0x1020 [nvidia]
Jun  2 10:17:51 mediapc kernel: [   12.969170]  ? _nv027155rm+0x22c/0x4f0 [nvidia]
Jun  2 10:17:51 mediapc kernel: [   12.969507]  ? _nv017787rm+0x303/0x5e0 [nvidia]
Jun  2 10:17:51 mediapc kernel: [   12.969847]  ? _nv017789rm+0xe1/0x220 [nvidia]
Jun  2 10:17:51 mediapc kernel: [   12.970118]  ? _nv022829rm+0xed/0x220 [nvidia]
Jun  2 10:17:51 mediapc kernel: [   12.970475]  ? _nv023065rm+0x30/0x60 [nvidia]
Jun  2 10:17:51 mediapc kernel: [   12.970691]  ? _nv000704rm+0x16da/0x22b0 [nvidia]
Jun  2 10:17:51 mediapc kernel: [   12.970912]  ? rm_init_adapter+0xc5/0xe0 [nvidia]
Jun  2 10:17:51 mediapc kernel: [   12.971134]  ? nv_open_device+0x122/0x8e0 [nvidia]
Jun  2 10:17:51 mediapc kernel: [   12.971322]  ? nvidia_open+0x2b7/0x560 [nvidia]
Jun  2 10:17:51 mediapc kernel: [   12.971510]  ? nvidia_frontend_open+0x58/0xa0 [nvidia]
Jun  2 10:17:51 mediapc kernel: [   12.971698]  ? chrdev_open+0xf7/0x220
Jun  2 10:17:51 mediapc kernel: [   12.971702]  ? cdev_device_add+0x90/0x90
Jun  2 10:17:51 mediapc kernel: [   12.971704]  ? do_dentry_open+0x156/0x370
Jun  2 10:17:51 mediapc kernel: [   12.971706]  ? vfs_open+0x2d/0x30
Jun  2 10:17:51 mediapc kernel: [   12.971707]  ? do_open+0x1c3/0x340
Jun  2 10:17:51 mediapc kernel: [   12.971709]  ? path_openat+0x10a/0x1d0
Jun  2 10:17:51 mediapc kernel: [   12.971711]  ? do_filp_open+0x8c/0x130
Jun  2 10:17:51 mediapc kernel: [   12.971713]  ? __check_object_size+0x1c/0x20
Jun  2 10:17:51 mediapc kernel: [   12.971715]  ? do_sys_openat2+0x9b/0x150
Jun  2 10:17:51 mediapc kernel: [   12.971717]  ? __x64_sys_openat+0x56/0x90
Jun  2 10:17:51 mediapc kernel: [   12.971718]  ? do_syscall_64+0x38/0x90
Jun  2 10:17:51 mediapc kernel: [   12.971721]  ? entry_SYSCALL_64_after_hwframe+0x44/0xa9

Removing nvidia-driver-460 restores the ability to boot - but with the nouvea drivers.

nvidia-driver-465 displays the same behaviour.

Attempts to install any nvidia-driver-4** will try to pull in parts of 460 and the same problems occur.

I can install nvidia-driver-390 and this will install without any 4** components, and will boot and work normally using the proprietary driver, albeit the old 390 version.

I'm not able to investigate much further, but it looks like someone has messed something shared in 4** drivers.

---

### Post by Autodave on 2021-06-02
Some info on your hardware would be helpful.  Lap or desk top?  What nVidia card do you have?

---

### Post by mongoosex on 2021-06-02
I've added which card. It's a desktop with a Gigabyte motherboard. The CPU was included already.

---

### Post by mongoosex on 2021-06-02
> **mongoosex said:**
> I've added which card. It's a desktop with a Gigabyte motherboard. The CPU was included already.

Additional... after a bit of experimentation. It seems the BENQ 4K monitor via display port is 'causing' this.

I found it by accident by having the monitor off. I tested it with an old monitor and 465.27 worked fine. Eventually I figured out that the BENQ 4k specifically connected via DisplayPort causes the kernel crash when the Nvidia modules are loaded right at the start of the boot.

I replaced the DisplayPort cable with an HDMI and it's working ok.

Pretty crappy NVIDIA. You've clearly got an issue with DisplayPort and/or 4K - and it's a nasty one too. It locks out the user completely  almost as soon as they try to boot... leaving them with no errors, just a hard lock. Unless they are quite technical no way to even show you what the error is.

Anyway, if anyone reads this... try an HDMI cable. Not a fix, but a temp workaround that might get your system back up.

NOTE: just found some more info backing this up. The part NVIDIA  moderators: "We were able to reproduce issue locally and actively  debugging it. Will keep updated and let you know once fix is available."

[https://forums.developer.nvidia.com/t/465-24-02-page-fault/175782/64](https://forums.developer.nvidia.com/t/465-24-02-page-fault/175782/64)

---

### Post by Autodave on 2021-06-02
Good deal!  Thanks for the info!

---

