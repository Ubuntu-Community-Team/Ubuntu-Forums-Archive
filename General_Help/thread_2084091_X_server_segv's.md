---
title: "X server segv's"
date: 2012-11-14
forum: General Help
---

### Post by defaria on 2012-11-14
I'm not sure if this is the right place to post this. If not then kindly point me in the right direction.

I just had my X server die! It happens when I'm running huludesktop, which I suspect uses an old version of flash. Everything freezes and then I get a fast flicker of the screen. A couple of seconds of freezing and another fast flicker. Usually it eventually recovers after about 4 of these. I sometime kill and restart huludesktop and it works just fine. Other times it doesn't. Sometimes X dies. This time X died.

The relevant part of /var/log/Xorg.0.log.old (also attached) shows:

```
Backtrace:
[606739.953] 0: /usr/bin/X (xorg_backtrace+0x26) [0x7fee6bc10876]
[606739.953] 1: /usr/bin/X (0x7fee6ba88000+0x18c71a) [0x7fee6bc1471a]
[606739.953] 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7fee6adae000+0xfcb0) [0x7fee6adbdcb0]
[606739.953] 3: /lib/x86_64-linux-gnu/libc.so.6 (0x7fee69c1e000+0x91da0) [0x7fee69cafda0]
[606739.953] 4: /lib/x86_64-linux-gnu/libc.so.6 (0x7fee69c1e000+0x8bba5) [0x7fee69ca9ba5]
[606739.953] 5: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so (0x7fee648a6000+0xf3e40) [0x7fee64999e40]
[606739.953] 6: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so (0x7fee648a6000+0x4a0952) [0x7fee64d46952]
[606739.953] 7: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so (0x7fee648a6000+0x4a0bcb) [0x7fee64d46bcb]
[606739.953] 8: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so (0x7fee648a6000+0x49d03a) [0x7fee64d4303a]
[606739.953] 9: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so (0x7fee648a6000+0x46a026) [0x7fee64d10026]
[606739.953] 10: /usr/bin/X (0x7fee6ba88000+0xa5ffe) [0x7fee6bb2dffe]
[606739.953] 11: /usr/bin/X (SigAbortDDX+0x8b) [0x7fee6bb1565b]
[606739.953] 12: /usr/bin/X (0x7fee6ba88000+0x1938f3) [0x7fee6bc1b8f3]
[606739.954] 13: /usr/bin/X (0x7fee6ba88000+0x19393b) [0x7fee6bc1b93b]
[606739.954] 14: /usr/bin/X (0x7fee6ba88000+0x193b15) [0x7fee6bc1bb15]
[606739.954] 15: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so (0x7fee648a6000+0xc98ae) [0x7fee6496f8ae]
[606739.954] 16: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so (0x7fee648a6000+0x7c2bb) [0x7fee649222bb]
[606739.954] 17: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so (0x7fee648a6000+0xf117b) [0x7fee6499717b]
[606739.954] 18: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so (0x7fee648a6000+0x499e46) [0x7fee64d3fe46]
[606739.954] 19: /usr/bin/X (0x7fee6ba88000+0x11971c) [0x7fee6bba171c]
[606739.954] 20: /usr/bin/X (0x7fee6ba88000+0x4a943) [0x7fee6bad2943]
[606739.954] 21: /usr/bin/X (0x7fee6ba88000+0x4e8a1) [0x7fee6bad68a1]
[606739.954] 22: /usr/bin/X (0x7fee6ba88000+0x3d7ba) [0x7fee6bac57ba]
[606739.954] 23: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xed) [0x7fee69c3f76d]
[606739.954] 24: /usr/bin/X (0x7fee6ba88000+0x3daad) [0x7fee6bac5aad]
[606739.954] Segmentation fault at address 0x7fee6b98f000
[606739.954] 
Caught signal 11 (Segmentation fault). Server aborting
[606739.954] 
Please consult the The X.Org Foundation support 
         at http://wiki.x.org
 for help. 

```

[http://wiki.x.org](http://wiki.x.org) just gives me a 503 service unavailable - thanks guys.

So what to do?

---

