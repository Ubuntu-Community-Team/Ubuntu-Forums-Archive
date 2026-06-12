---
title: "Kernel panic - not synching: VFS: Unable to mount root fs on unkown-block(0,0)"
date: 2013-05-05
forum: General Help
---

### Post by Riothamus on 2013-05-05
I'm using an HP Mini with a 160GB hard drive partitioned with Windows XP and Ubuntu. (I know, a lot to do with a netbook, but I wanted to do it for fun.) It's always worked well, but a couple of weeks ago, after switching over from Windows, I started getting this error whenever I try to start the Ubuntu partition and I can't get into the system at all. This is what it says whenever I try to start it up:

```

[   6.868427] Kernel panic - not synching: VFS: Unable to mount root fs on unkown-block(0,0)
[   6.868489] Pid: 1, comm: swapper/0 Not tainted 3.2.0-39 generic #62-Ubuntu
[   6.868541] Call Trace:
[   6.868590] [<c1561988>] ? printk+0x2d/0x2f
[   6.868639] [<c1561856>] panic+0x5c/0x161
[   6.868690] [<c1834bd1>] mount_block_root+0x12c/0x14c
[   6.868740] [<c155f3e2>] ? create_dev.constprop.0+0x29/0x2f
[   6.868794] [<c18356df>] handle_initrd+0x48/0x2ee
[   6.868843] [<c18359c7>] initrd_load+0x42/0x59
[   6.868892] [<c1834e32>] prepare_namespace+0xc3/0x192
[   6.868944] [<c1131eb5>] ? sys_access+0x25/0x30
[   6.868993] [<c18348d2>] kernel_init+0x156/0x15b
[   6.869044] [<c183477c>] ? start_kernel+0x358/0x358
[   6.869095] [<c157e07e>] kernel_thread_helper+0x6/0x10

```

Googling "Kernel panic - not synching: VFS: Unable to mount root fs on unkown-block" I find that this is a known problem, but there's usually no exact known cause or solution, and you basically have to play around with Linux in order to get it fixed. Unfortunately, I'm not enough of a whiz at Linux to be able to do that. I've tried making an installation disk and booting with that, but I can't get into the hard drive to look at things, and even if I could, I wouldn't know what to do. I'm wondering if someone here can walk me through getting this fixed.

---

### Post by Riothamus on 2013-05-13
*bump*

---

