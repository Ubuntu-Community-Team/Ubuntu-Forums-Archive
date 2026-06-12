---
title: "Command line (or otherwise) to display my monitor color depth in use"
date: 2014-12-02
forum: General Help
---

### Post by mladen.adamovic@gmail.com on 2014-12-02
Any idea?

---

### Post by phidia on 2014-12-02
What GPU are you running? You can try > xrandr --help and > xrandr man

---

### Post by tgalati4 on 2014-12-02
You can also look through the log file to see what color depth was selected:

> tgalati4@Mint14-Extensa ~ $ grep -i -3 Color /var/log/Xorg.0.log
	"Default Screen Section" for depth/fbbpp 24/32
[    32.772] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    32.772] (==) intel(0): RGB weight 888
[    32.772] (==) intel(0): Default visual is TrueColor
[    32.772] (--) intel(0): Integrated Graphics Chipset: Intel(R) 965GM
[    32.772] (**) intel(0): Relaxed fencing enabled
[    32.772] (**) intel(0): Wait on SwapBuffers? enabled
--
[    33.170] (II) intel(0): Max Image Size [cm]: horiz.: 30  vert.: 19
[    33.170] (II) intel(0): Gamma: 2.20
[    33.170] (II) intel(0): No DPMS capabilities specified
[    33.170] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    33.170] (II) intel(0): First detailed timing is preferred mode
[    33.170] (II) intel(0): redX: 0.575 redY: 0.335   greenX: 0.315 greenY: 0.550
[    33.170] (II) intel(0): blueX: 0.155 blueY: 0.135   whiteX: 0.313 whiteY: 0.329


Welcome to the forums.  You should change your username otherwise you will get a lot of junk mail.

---

### Post by slickymaster on 2014-12-02
> **tgalati4 said:**
> 
Welcome to the forums.  You should change your username otherwise you will get a lot of junk mail.

A big +1 on ^^^.

If you want to change your username just start a new thread in the [Resolution Center sub-forum]("http://ubuntuforums.org/forumdisplay.php?f=123") and name the thread "Username change".

When you'll do it, please take in consideration the following:
[LIST]
[*]Make sure that any change you request is what you want - we will only change it ONCE.
[*]Make sure to give us 3 alternatives, we will not look without there being 3.
[/LIST]

---

