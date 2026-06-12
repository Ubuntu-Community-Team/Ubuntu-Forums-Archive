---
title: "Kubuntu 6.10 - sloppy window change"
date: 2006-11-01
forum: General Help
---

### Post by mvarga on 2006-11-01
Hi all.

I've just installed Kubuntu 6.10. It replaced Ubuntu Dapper.

The problem is, that though the appearance of the UI got extremely beautiful, it seems to be slow and unresponsive in many cases, especially when changing windows with Alt+Tab.

Any ideas?

My machine is a Lenovo T60 w/ Core Duo, 2 GBs or RAM and an Ati X1400. FGLRX drivers are installed, DRI is working.

---

### Post by kkinder on 2006-11-01
Are you using translucent windows or anything like that? You might try toning down kind of thing in System Settings, although given the beefyness of your system, it also sounds like perhaps hardware GUI acceleration isn't working...

---

### Post by mvarga on 2006-11-01
No, nothing. No transparent panels, terminals. Hardware acceleration works, for sure.

mvarga@mv-t60:~$ glxinfo | grep render
direct rendering: Yes
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: ATI Mobility Radeon X1400 Generic


Cpu(s):  3.0%us,  0.5%sy,  0.0%ni, 96.0%id,  0.0%wa,  0.5%hi,  0.0%si,  0.0%st
Mem:   2074840k total,  1492404k used,   582436k free,   116188k buffers

(most of the 1.5 GB used is cache.)

---

