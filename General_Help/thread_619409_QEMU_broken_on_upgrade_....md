---
title: "QEMU broken on upgrade ..."
date: 2007-11-21
forum: General Help
---

### Post by dbee on 2007-11-21
So the last time I tried to use QEMU, it worked fine. This time however it's giving me an error and telling me that it can't initialize SDL and that there's no framebuffer...

```

babo@eire:/home/babo/qemu_dir# qemu -localtime -cdrom /dev/cdrom -m 384 -boot d c.img
Warning: No DNS servers found

       ---------------------- DirectFB v0.9.25 ---------------------
             (c) 2000-2002  convergence integrated media GmbH  
             (c) 2002-2004  convergence GmbH                   
        -----------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2007-08-07 19:21) 
(*) Direct/Memcpy: Using MMX optimized memcpy()
(!) Direct/Util: opening '/dev/fb0' and '/dev/fb/0' failed
    --> No such file or directory
(!) DirectFB/FBDev: Error opening framebuffer device!
(!) DirectFB/FBDev: Use 'fbdev' option or set FRAMEBUFFER environment variable.
(!) DirectFB/Core: Could not initialize 'system' core!
    --> Initialization error!
Could not initialize SDL - exiting

```

Does anyone have any ideas about resolving this issue ?

Thanks,

---

### Post by dbee on 2008-01-17
QEMU looks for framebuffer for graphics. Ubuntu doesn't have a framebuffer anymore and nowadays most apps use SDL with the directfb drivers for graphic display. Since the driver won't handle QEMU graphics, the alternative is to use vnc ...
 
    qemu -vnc display c.img

Then connect to the vnc display with another terminal ...

    vncviewer localhost:1

As it happens, my DISPLAY env variable was also empty - I had to set the terminal to use the first X display ...

    set DISPLAY=:0

---

