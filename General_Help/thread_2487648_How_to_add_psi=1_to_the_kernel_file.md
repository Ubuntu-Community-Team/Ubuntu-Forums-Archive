---
title: "How to add psi=1 to the kernel file"
date: 2023-06-11
forum: General Help
---

### Post by tianyifox8 on 2023-06-11
I installed waydroid in ubuntu.

But there was an error on startup:
```
[22:23:33] Failed to get service waydroidplatform, trying again...
[22:23:34] Failed to get service waydroidplatform, trying again...
[22:23:35] Failed to get service waydroidplatform, trying again...
[22:23:36] Failed to get service waydroidplatform, trying again...
[22:23:37] Failed to get service waydroidplatform, trying again...
[22:23:38] Failed to get service waydroidplatform, trying again...
[22:23:39] Failed to get service waydroidplatform, trying again...
[22:23:40] Failed to get service waydroidplatform, trying again...
[22:23:41] Failed to get service waydroidplatform, trying again...
[22:23:42] Failed to get service waydroidplatform, trying again...
[22:23:43] Failed to get service waydroidplatform, trying again...

```

After a long search online, there was a post on github that read:

[HTML]/etc/gbinder.d/anbox.conf


[Protocol]
/dev/anbox-binder = aidl2
/dev/anbox-vndbinder = aidl2
/dev/anbox-hwbinder = hidl

[ServiceManager]
/dev/anbox-binder = aidl2
/dev/anbox-vndbinder = aidl2
/dev/anbox-hwbinder = hidl

then try to remove the waydroid-sensors package , on the kernel the psi must be enabled, you must add to grub psi=1[/HTML]


But I don't know where to put psi=1.


According to the directory he gave me, this file is not on my system.

thanks.


system:ubuntu 22.04.2 lts

uname -a:  Linux orangepi5plus 5.10.110-rockchip-rk3588 #1.0.6 SMP Thu Jun 1 11:43:16 CST 2023 aarch64 aarch64 aarch64 GNU/Linux

---

### Post by MAFoElffen on 2023-06-12
Add the boot parameter to file '/boot/firmware/cmdline.txt'.

---

