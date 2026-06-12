---
title: "Plymouth startup display problem"
date: 2017-06-22
forum: General Help
---

### Post by CatKiller on 2017-06-22
I've recently updated from 14.04 to 16.04, and Plymouth no longer displays the splash screen properly.

The splash screen displays briefly, but then is replaced by a black screen with red dots. It seems like the background gets flushed and only the parts of the screen that are updated are displayed.

The shutdown splash screen displays normally.

The consoles are at 1920x1200 as they should be.

Using uvesafb with the proprietary driver on a GTX 960, which worked with 14.04 and almost works now.

I've done significant searching already, but all the information seems to be about making it work at all, not about it almost working as in my case.

Further pointers would be appreciated.

---

### Post by CatKiller on 2017-06-23
bump.

---

### Post by CatKiller on 2017-06-25
bump :(

---

### Post by CatKiller on 2017-06-25
This may be significant:

dmesg | grep vesa

```
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.8.0-56-lowlatency root=UUID=4b613ba0-160e-46d1-be47-048918998f52 ro nmi_watchdog=0 quiet splash intel_pstate=enable video=uvesafb:mode_option=1920x1200-32,mtrr:0,scroll:ywrap vt.handoff=7
[    0.786048] vesafb: mode is 1920x1200x32, linelength=7680, pages=0
[    0.786049] vesafb: scrolling: redraw
[    0.786050] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.786058] vesafb: framebuffer at 0xf1000000, mapped to 0xffffa457c2000000, using 9024k, total 9024k
[    1.937778] uvesafb: NVIDIA Corporation, GM206 Board, Chip Rev   , OEM: NVIDIA, VBE v3.0
[    2.051013] uvesafb: VBIOS/hardware doesn't support DDC transfers
[    2.051013] uvesafb: no monitor limits have been set, default refresh rate will be used
[    2.051557] uvesafb: scrolling: redraw
[    2.051559] uvesafb: request region 0x3c0-0x3e0 failed
[    2.051565] uvesafb: probe of uvesafb.0 failed with error -5

```

Nothing I've tried has made it not use redraw as the scrolling method.

---

