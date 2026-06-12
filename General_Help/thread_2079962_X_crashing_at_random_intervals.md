---
title: "X crashing at random intervals"
date: 2012-11-02
forum: General Help
---

### Post by lilo346 on 2012-11-02
X crashes when lightdm loads, and after login repeatedy.

[ 24874.794] (EE) Backtrace:
[ 24874.831] (EE) 0: /usr/bin/X (xorg_backtrace+0x49) [0xb7706c79]
[ 24874.831] (EE) 1: /usr/bin/X (0xb755f000+0x1abb66) [0xb770ab66]
[ 24874.831] (EE) 2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb753c40c]
[ 24874.831] (EE) 3: /usr/lib/xorg/modules/drivers/r128_drv.so (0xb6fdb000+0x47a8) [0xb6fdf7a8]
[ 24874.831] (EE) 4: /usr/bin/X (0xb755f000+0xc98e8) [0xb76288e8]
[ 24874.831] (EE) 5: /usr/bin/X (0xb755f000+0xc8156) [0xb7627156]
[ 24874.831] (EE) 6: /usr/bin/X (miPointerUpdateSprite+0x2aa) [0xb76f0bda]
[ 24874.832] (EE) 7: /usr/bin/X (0xb755f000+0x191e6a) [0xb76f0e6a]
[ 24874.832] (EE) 8: /usr/bin/X (0xb755f000+0xd753b) [0xb763653b]
[ 24874.832] (EE) 9: /usr/bin/X (0xb755f000+0x123b06) [0xb7682b06]
[ 24874.832] (EE) 10: /usr/bin/X (0xb755f000+0x45aeb) [0xb75a4aeb]
[ 24874.832] (EE) 11: /usr/bin/X (WindowHasNewCursor+0x3b) [0xb75a5eeb]
[ 24874.832] (EE) 12: /usr/bin/X (ChangeWindowDeviceCursor+0x1d8) [0xb75ceb08]
[ 24874.832] (EE) 13: /usr/bin/X (0xb755f000+0x137858) [0xb7696858]
[ 24874.832] (EE) 14: /usr/bin/X (0xb755f000+0x131194) [0xb7690194]
[ 24874.832] (EE) 15: /usr/bin/X (0xb755f000+0x3cba5) [0xb759bba5]
[ 24874.833] (EE) 16: /usr/bin/X (0xb755f000+0x2a10a) [0xb758910a]
[ 24874.833] (EE) 17: /lib/i386-linux-gnu/libc.so.6 (__libc_start_main+0xf3) [0xb71b14d3]
[ 24874.833] (EE) 18: /usr/bin/X (0xb755f000+0x2a4e9) [0xb75894e9]
[ 24874.833] (EE) 
[ 24874.833] (EE) Segmentation fault at address 0xb6df8000
[ 24874.833] 
Fatal server error:
[ 24874.833] Caught signal 11 (Segmentation fault). Server aborting
[ 24874.833] 
[ 24874.833] (EE) 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[ 24874.833] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[ 24874.833] (EE) 
[ 24874.838] (II) evdev: Power Button: Close
[ 24874.838] (II) UnloadModule: "evdev"
[ 24874.839] (II) evdev: Power Button: Close
[ 24874.840] (II) UnloadModule: "evdev"
[ 24874.841] (II) evdev: AT Translated Set 2 keyboard: Close
[ 24874.841] (II) UnloadModule: "evdev"
[ 24874.843] (II) evdev: PS/2 Generic Mouse: Close
[ 24874.843] (II) UnloadModule: "evdev"
[ 24874.917] Server terminated with error (1). Closing log file.

---

