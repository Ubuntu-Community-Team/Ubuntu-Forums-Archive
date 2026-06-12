---
title: "Qemu Problem"
date: 2007-09-13
forum: General Help
---

### Post by mfreeze on 2007-09-13
Can anyone tell me why I am having this problem? (Over and over and over...)

Thanks,
Mark.

root@laptop:/xp# qemu -cdrom /dev/scd0 -hda /xp/windowsxp.img -boot d -net nic -net user -m 384 -localtime

       ---------------------- DirectFB v0.9.25 ---------------------
             (c) 2000-2002  convergence integrated media GmbH
             (c) 2002-2004  convergence GmbH
        -----------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2006-12-20 21:25)
(*) Direct/Memcpy: Using SSE optimized memcpy()
(!) Direct/Util: opening '/dev/fb0' and '/dev/fb/0' failed
    --> No such file or directory
(!) DirectFB/FBDev: Error opening framebuffer device!
(!) DirectFB/FBDev: Use 'fbdev' option or set FRAMEBUFFER environment variable.
(!) DirectFB/Core: Could not initialize 'system' core!
    --> Initialization error!
Could not initialize SDL - exiting

---

