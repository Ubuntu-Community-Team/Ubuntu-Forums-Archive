---
title: "Stock ATI Drivers"
date: 2006-12-18
forum: General Help
---

### Post by seelk on 2006-12-18
Is there a way to compile/install the stock ATI drivers with new custom kernels?  I currently built a 2.6.19.1 kernel as well as the latest ATI drivers but I'm having problems with GL apps.  For example, GL screensavers are very choppy as if I did not have any drivers installed.  Moreover, glxinfo and fglrxinfo both state that I do have 3D enabled.  I also tried compiling the 8.32.5 against the stock kernel (2.6.17-10-generic) and I get the same effect.  I didn't have this problem with the stock ATI drivers.  Can someone please help me?

---

### Post by pay on 2006-12-18
Read my post here [http://forums.gentoo.org/viewtopic-t-521199-highlight-.html](http://forums.gentoo.org/viewtopic-t-521199-highlight-.html)

---

### Post by seelk on 2006-12-18
> **pay said:**
> Read my post here [http://forums.gentoo.org/viewtopic-t-521199-highlight-.html](http://forums.gentoo.org/viewtopic-t-521199-highlight-.html)

I was able to compile fine because I touched config.h...  Any other ideas?

```
# glxinfo | grep direct
direct rendering: Yes
# fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.6234 (8.32.5)
```

The problem is that the performance with the latest 8.32.5 drivers is terrible no matter which kernel I use.

---

### Post by seelk on 2006-12-27
Does anyone know how do I compile the stock 8.28.8 ATI drivers against custom kernel (2.6.19.1)??  I installed the fglrx-kernel-source package but I don't know how to proceed...

---

