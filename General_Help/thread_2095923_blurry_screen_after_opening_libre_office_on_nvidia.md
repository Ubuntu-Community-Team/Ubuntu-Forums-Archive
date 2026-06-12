---
title: "blurry screen after opening libre office on nvidia 6100"
date: 2012-12-18
forum: General Help
---

### Post by edcv on 2012-12-18
Hi all,

I have just installed ubuntu 12.10 on this machine and when working in libreoffice calc I get this fuzzy screen after a while. 

[http://imgur.com/BhBSL](http://imgur.com/BhBSL)

Sometimes immediately and sometimes after a while
when opening something in libreoffice.

I have tried the current propriatary drivers and now using the current-updates.
( The x-org drivers always crashed compiz ). The experimental drivers are maybe
the next ones to test but this is a very old grapic card so I expected no changes,
and I wanted to get something stable.

glxinfo gives (and alot more):
```
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_swap_control, GLX_EXT_swap_control_tear, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_EXT_create_context_es_profile, 
    GLX_EXT_create_context_es2_profile, GLX_ARB_create_context_robustness, 
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_EXT_swap_control, GLX_EXT_swap_control_tear, 
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB, GLX_NV_present_video, GLX_NV_copy_image, 
    GLX_NV_multisample_coverage, GLX_NV_video_capture, 
    GLX_EXT_create_context_es2_profile, GLX_ARB_create_context_robustness
GLX version: 1.4
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_swap_control, GLX_EXT_swap_control_tear, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_EXT_create_context_es2_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_multisample, 
    GLX_NV_float_buffer, GLX_ARB_fbconfig_float, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 6100 nForce 405/integrated/SSE2
OpenGL version string: 2.1.2 NVIDIA 304.51
OpenGL shading language version string: 1.20 NVIDIA via Cg compiler
```Hoping someone knows how to fix this  as I'm trying to sell my dad the idea of using ubuntu and it is not going well so far. . . .

---

### Post by edcv on 2012-12-18
I have tried turning off and on the screen (silly I know but saw that suggestion somewhere), doesn't help.

I'm able to navigate my way to the turn off computer button and then the screen
looks fine for a few seconds just before it exits unity and turns off.

I'm using 64bit . . . not sure if that matters

---

### Post by edcv on 2012-12-18
Ok this seems to be solved now. 
Have been able to use libre Office now for at least few minutes after I 
disabled hardware acceleration:
Preferences/LibreOffice/View/Use Hardware Acceleration

And voila!

---

### Post by wribeiro on 2013-03-17
I have the same problem and disable hardware acceleration has no effect for me.
This bug is related here [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/568492](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/568492)
Here is my plea for help: [http://ubuntuforums.org/showthread.php?t=2124833](http://ubuntuforums.org/showthread.php?t=2124833)

---

