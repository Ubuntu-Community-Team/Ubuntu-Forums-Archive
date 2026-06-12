---
title: "Ati Restricted driver &amp; Compiz Fusion (Gutsy)"
date: 2007-10-07
forum: General Help
---

### Post by Naatan on 2007-10-07
Hi,

Basically I have the same issue as here:

[http://ubuntuforums.org/showthread.php?t=567854&highlight=ati+restricted+drivers+compiz](http://ubuntuforums.org/showthread.php?t=567854&highlight=ati+restricted+drivers+compiz)

Currently I am using the ati driver gutsy ships with, but when I use the restricted driver compiz doesn't work..

So what's the problem? The driver it ships with is extremely slow, scrolling lags like hell and the animations are choppy.

Does anyone know if it's possible to enable compiz with the restricted drivers?

Or perhaps there's a simple way increase performance in compiz with the shipped driver..

I'm really liking Gutsy but this really puts a drain on it for me.

**Edit:** This might be handy.. I have a Mobility Radeon x600..

---

### Post by dredwerker on 2007-10-07
I cant help - sorry.
But I am having the same problem with an x1950 pro on Gutsy/dual core pentium/nvidia mobo.

**I have tried installing this driver from ATI**

```
ati-driver-installer-8.40.4-x86.x86_64.run
```

From here [HTML]https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.40.4-x86.x86_64.run[/HTML]

[HTML]http://ati.amd.com/support/drivers/linux/linux-radeon.html[/HTML]
[B]
I tried enabling the restricted driver and rebooting but all I end up with is screen glitches/tearing sort of issues.[/B]


I also edited my xorg.conf ```
sudo nano /etc/X11/xorg.conf
``` to add 1 to the composite bit but I dont appear to even have that section now I have turned off restricted driver. 


**I got this with GLXINFO (typing on the command line for newbies)**

```

name of display: :0.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x3d 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

```

arggghh help

---

### Post by KIAaze on 2007-10-07
You could always try the old Beryl with AiGLX. It's the only one that ever worked correctly for me. (ATI Radeon IGP 345M)
However, I currently don't have any desktop effects on my PC since I've also given up temporarily on the Compiz issue (and Beryl got removed quite some time ago). :/

---

### Post by dredwerker on 2007-10-07
For me the point is one of getting the drivers working as they should and then compiz should just follow on.

---

### Post by strabes on 2007-10-07
At the moment you cannot use fglrx (ATI's proprietary driver) and use AIGLX. You can, however, use XGL which is relatively unstable and basically all-around worse than AIGLX. Just install the ATI drivers using the process linked to in my signature and then install the xserver-xgl package.

---

### Post by nathansu on 2007-10-08
I'm having the same issue on a Thinkpad t43 with a Mobility x600.

---

### Post by the yawner on 2007-10-08
I'm currently running Compiz Fusion that's with Gutsy on a Thinkpad with an ATI. I just installed enabled the restricted driver, then installed the xserver-xgl package (which in Gutsy automatically creates a script to run xgl upon logging in.)

On my setup, I find it running much better than my previous Feisty+xgl+fglrx+Compiz Fusion.

---

### Post by Naatan on 2007-10-11
Exactly what videocard do you have?

The last time I tried installing the xgl package it screwed up my system

---

