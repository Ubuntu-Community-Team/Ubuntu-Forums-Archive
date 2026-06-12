---
title: "Strange X server crashes after upgrade to raring"
date: 2013-05-08
forum: General Help
---

### Post by marianoa on 2013-05-08
Hi everybody,

I've upgraded my ubuntu installation to raring a few days ago and I've experienced some
abrupt crashes of the X server, the screen goes black and then I'm shown the login screen where
I can log in again and everything works fine until the next crash which usually happens after a few hours. 
Digging in the X server logs I've found these lines that could help solve the problem

```
[ 20937.790] (II) intel(0): switch to mode 1366x768 on crtc 3 (pipe 0)
[ 22122.563] (EE) 
[ 22122.563] (EE) Backtrace:
[ 22122.563] (EE) 0: /usr/bin/X (xorg_backtrace+0x49) [0xb7742f49]
[ 22122.563] (EE) 1: /usr/bin/X (0xb7595000+0x1b1e86) [0xb7746e86]
[ 22122.563] (EE) 2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb757240c]
[ 22122.563] (EE) 3: /usr/lib/xorg/modules/drivers/intel_drv.so (0xb6e85000+0x68418) [0xb6eed418]
[ 22122.563] (EE) 4: /usr/lib/xorg/modules/drivers/intel_drv.so (0xb6e85000+0x69942) [0xb6eee942]
[ 22122.563] (EE) 5: /usr/lib/xorg/modules/drivers/intel_drv.so (0xb6e85000+0x4c685) [0xb6ed1685]
[ 22122.563] (EE) 6: /usr/lib/xorg/modules/drivers/intel_drv.so (0xb6e85000+0x7d288) [0xb6f02288]
[ 22122.564] (EE) 7: /usr/lib/xorg/modules/drivers/intel_drv.so (0xb6e85000+0x6369b) [0xb6ee869b]
[ 22122.564] (EE) 8: /usr/lib/xorg/modules/drivers/intel_drv.so (0xb6e85000+0xccd0c) [0xb6f51d0c]
[ 22122.564] (EE) 9: /usr/lib/xorg/modules/drivers/intel_drv.so (0xb6e85000+0x670c5) [0xb6eec0c5]
[ 22122.564] (EE) 10: /usr/bin/X (0xb7595000+0x12e041) [0xb76c3041]
[ 22122.564] (EE) 11: /usr/bin/X (CompositePicture+0x319) [0xb76b74a9]
[ 22122.564] (EE) 12: /usr/bin/X (0xb7595000+0x126bfd) [0xb76bbbfd]
[ 22122.564] (EE) 13: /usr/bin/X (0xb7595000+0x122bae) [0xb76b7bae]
[ 22122.564] (EE) 14: /usr/bin/X (0xb7595000+0x3e035) [0xb75d3035]
[ 22122.564] (EE) 15: /usr/bin/X (0xb7595000+0x2b525) [0xb75c0525]
[ 22122.564] (EE) 16: /lib/i386-linux-gnu/libc.so.6 (__libc_start_main+0xf5) [0xb7183935]
[ 22122.564] (EE) 17: /usr/bin/X (0xb7595000+0x2b8f9) [0xb75c08f9]
[ 22122.564] (EE) 
[ 22122.564] (EE) Segmentation fault at address 0xffc5e4c0
[ 22122.564] 
Fatal server error:
[ 22122.564] Caught signal 11 (Segmentation fault). Server aborting
[ 22122.564] 
[ 22122.564] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[ 22122.564] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[ 22122.564] (EE) 
[ 22122.576] (II) evdev: Video Bus: Close
[ 22122.576] (II) UnloadModule: "evdev"
[ 22122.588] (II) evdev: Sony Vaio Keys: Close
[ 22122.588] (II) UnloadModule: "evdev"
[ 22122.600] (II) evdev: Power Button: Close
[ 22122.600] (II) UnloadModule: "evdev"
[ 22122.612] (II) evdev: USB 2.0 Camera: Close
[ 22122.612] (II) UnloadModule: "evdev"
[ 22122.614] (II) evdev: AT Translated Set 2 keyboard: Close
[ 22122.614] (II) UnloadModule: "evdev"
[ 22122.621] (II) evdev: PS/2 Mouse: Close
[ 22122.621] (II) UnloadModule: "evdev"
[ 22122.623] (II) UnloadModule: "synaptics"
[ 22122.624] (II) AIGLX: Suspending AIGLX clients for VT switch
[ 22122.642] Server terminated with error (1). Closing log file.
```

The problem  has shown up 3/4 times so far and it happened while I was browsing the web,
when trying to open some webpages even if I can't remember which pages I was going to visit to
check if I can reproduce the problem, they were completely "harmless" pages anyway.

Any idea? Thanks!

---

### Post by marianoa on 2013-05-13
I've got some news on the problem I'm experiencing, maybe it can help anyone help me. It's happened a few more times, the last one a few minutes ago and I've noted down a webpage where this happens 

[http://boutique.orange.fr/ESHOP_mx_ft/?tp=php&donnee_appel=FTASN&IDCible=1&type=4&code_rubrique=5-504008](http://boutique.orange.fr/ESHOP_mx_ft/?tp=php&donnee_appel=FTASN&IDCible=1&type=4&code_rubrique=5-504008)

the strange thing is that the problem appears again again if I try to open the webpage with firefox but I can open the same page just fine if I use Chrome/Chromium.
Any idea apart from stopping using firefox? (I would really like to avoid doing that)

---

