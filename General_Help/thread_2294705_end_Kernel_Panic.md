---
title: "end Kernel Panic"
date: 2015-09-12
forum: General Help
---

### Post by heroquestelf on 2015-09-12
I have a Toshiba laptop, Satellite p305 and I'm running Ubuntu 14.04.3 LTS.

I am having a login issue and I can't seem to figure out how to fix it. Every time I go to log in, I get the following error

```

[   2.1312017]   Call Trace:
[   2.1312017]  [<ffffffff81765ca1>]    dump_stack+0x45/0x56
[   2.1312017]  [<ffffffff8175e138>]    panic+0xc8/0x1fc
[   2.1312017]  [<ffffffff81d3162d>]    mount_block_root+0x2a1/0x2b0
[   2.1312017]  [<ffffffff81d32261>]    initrd_load+0xcd/2d8
[   2.1312017]  [<ffffffff81d318ba>]    prepare_namespace+0xde/0x1a4
[   2.1312017]  [<ffffffff81d312b5>]    kernel_init_freeable+0x1f3/0x200
[   2.1312017]  [<ffffffff81d3099f>]    ?  initcall_blacklist+0xba/0xba
[   2.1312017]  [<ffffffff817547c0>]    ?  rest_init+0x80/0x80
[   2.1312017]  [<ffffffff817547ce>]    kernel_init+0xe/0xf0
[   2.1312017]  [<ffffffff8176e298>]    ret_from_fork+0x58/0x90
[   2.1312017]  [<ffffffff817547c0>]    ?  rest_init+0x80/0x80
[   2.1312017]  Kenrel Offset: 0x0 from 0xffffffff81000000 (relocation range: 0xffffffff80000000-0xffffffffbfffffff)
[   2.1312017]  ---[ end Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

```

The oddest thing is that I **CAN** get the laptop to load. If I go into "Advanced options for Ubuntu" and chose "3.16.0-**43**-generic" it loads fine. It is only when I try to load it into 3.16.0-**45**-generic" do I have the issue.

Any suggestions would be welcome.

---

### Post by tgalati4 on 2015-09-12
Well, you have demonstrated the value of having a backup kernel.  Continue to use the older kernel.  Just wait for an update to the kernel and apply it.  It could be a regression--something that was working and is now no longer working.  You can file a bug against the kernel version 3.16.0-45, and as part of that filing you will see if others are having the same issue.

It could be a bad installation of the current kernel. It could also be bit-rot--a natural degradation of data over time--it happens.  You can attempt to reinstall it, but it is not worth the Agony Units in my opinion.  I would wait a few months for the next update and apply that.  Then delete 0-45 version using *synaptic*.

Check the SMART status of your disk drive.  If it is failing, you would want to know about it.  Open a terminal.

```
sudo smartctl -a /dev/sda
```

---

