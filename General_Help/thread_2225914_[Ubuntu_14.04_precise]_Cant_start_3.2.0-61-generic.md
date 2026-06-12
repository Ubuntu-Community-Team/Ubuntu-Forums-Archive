---
title: "[Ubuntu 14.04 precise] Cant start 3.2.0-61-generic kernel"
date: 2014-05-24
forum: General Help
---

### Post by mrvic2 on 2014-05-24
[h=2][SIZE=2]good title : [Ubuntu[SIZE=4] _12.04_[/SIZE] precise] Cant start 3.2.0-61-generic kernel 		[/SIZE][/h]

Hi,

I use Ubuntu 12.04 precise 64bits.
Probably after upgrade I cant start 3.2.0-61-generic kernel. To start my PC I must select older kernel like 3.2.0.60-generic kernel in "previous Linux version" menu of GRUB.

When I try to start 3.2.0-61-generic kernel manualy with GRUB I get this echo :
```
[2.144099] kernel panic - not syneing : VFS unable to mount root fs on unkonow -  block (0,0)
pid : 1, comm : swapper /0 Not tainted 3.2.0-61-generic # 93-Ubuntu
call trace
panic+0x91/0x1a4
mount-block_root+0x163/0x18e
handle-initrd+0x4c/0x295
initlrd-load+0x46/0x5d
prepare-namespace+0xdf/0x106
kernel_thread_helper+Ox4/0x10
? start kernel+0x3C2/0x3c2
.gs-change+0x13/0x13
```

one body know Where is my problem ?
Best regards

---

