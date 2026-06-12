---
title: "OpenGL Segmentation fault"
date: 2013-08-01
forum: General Help
---

### Post by MarshyTheKid on 2013-08-01
Noticed this after Compiz failed and threw a fit about OpenGL not loaded.
```
$ glxinfo
name of display: :1.0
display: :1  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_multisample, GLX_EXT_create_context_es2_profile, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, GLX_OML_swap_method, 
    GLX_SGI_swap_control, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_get_proc_address, 
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_create_context_es2_profile, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_create_context_es2_profile, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: (null)
OpenGL renderer string: (null)
OpenGL version string: (null)
Segmentation fault

```

Any suggestions? I'm not sure where to go from here.

---

### Post by startas on 2013-08-01
Try to reinstall your graphic drivers.

---

### Post by MarshyTheKid on 2013-08-01
Tried reinstalling them, also tried installing Intel Linux Graphic Drivers using the tool from [https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads) . No change

It's just gotten worse now...
```
$ glxinfo
name of display: :1
Segmentation fault

```

Computer: Lenovo Thinkpad SL410

---

### Post by MarshyTheKid on 2013-08-01
```
ldconfig deferred processing now taking place
/sbin/ldconfig.real: /usr/lib/x86_64-linux-gnu/libGL.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/x86_64-linux-gnu/libEGL.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/x86_64-linux-gnu/libdricore8.1.0.so.1 is not a symbolic link

``` Probably part of my problem. Should I just move those to another folder and create a symbolic link in /usr/lib/x86_64-linux-gnu/? I don't know and can't seem to find the proper way to fix this.

---

### Post by Corey Goettsch on 2013-09-12
Hey:

DId you ever figure this out?  I'm having the same problem.

---

### Post by MarshyTheKid on 2013-09-17
> **Corey Goettsch said:**
> Hey:

DId you ever figure this out?  I'm having the same problem.

Not yet.

```
$ glxgears -info
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
GL_RENDERER   = (null)
GL_VERSION    = (null)
GL_VENDOR     = (null)
GL_EXTENSIONS = (null)
Segmentation fault

```
I'm guessing something may be wonky with my video card driver. I've been having a hard time finding the right driver for my video card on my laptop. It should be an Intel GMA 4500M. I have i965-va-driver as well as libva-intel-vaapi-driver installed. If I search synaptic for graphic driver, I have about 30 things installed. Not sure which are needed and which aren't. :/ I'm planning on just wiping my machine clean, but I hate the woes that go with that. Figuring out what packages I want installed, getting all of my settings just so. *sigh* I wish Ubuntu had an easy backup system for doing that.

---

