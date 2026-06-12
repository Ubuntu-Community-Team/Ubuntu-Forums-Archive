---
title: "XGL and BERYL working great on EDGY! But no DRI with i915! What this could be ?"
date: 2006-11-07
forum: General Help
---

### Post by nooneelse on 2006-11-07
I've installed xserver-xgl, beryl and emerald-theme from 

> deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) edgy main-edgyand launched it with the xgl

```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
exec gnome-session
```But when I see into 'glxinfo' is says: 

```
name of display: localhost:1.0
display: localhost:1  screen: 0
**[COLOR=Red]direct rendering: No[/COLOR]**
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: [www.mesa3d.org]("http://www.mesa3d.org")
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multitexture, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_point_sprite, GL_NV_texgen_reflection, GL_NV_texture_rectangle, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
```Beryl is running PERFECT but with no direct rendering its a lotta slow, and 3D and other stuff are slow too.

Below my modules:

```

bruno@bnogueira:~$ sudo lsmod | grep i915
i915                   21632  3 
drm                    74644  4 i915
```and the WW(warnings) on Xorg.0.log:

```
bruno@bnogueira:~$ cat /var/log/Xorg.0.log | grep WW
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
(WW) I810: No matching Device section for instance (BusID PCI:0:2:1) found
(WW) I810(0): Bad V_BIOS checksum
(WW) I810(0): Bad V_BIOS checksum
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(WW) I810(0): config file hsync range 28-64kHz not within DDC hsync range 30-70kHz
(WW) I810(0): config file vrefresh range 43-60Hz not within DDC vrefresh range 50-160Hz
*(WW) (1280x1024,Dell Monitor) mode clock 135MHz exceeds DDC maximum 110MHz
(WW) (1280x1024,Dell Monitor) mode clock 157.5MHz exceeds DDC maximum 110MHz
*(WW) (1600x1200,Dell Monitor) mode clock 162MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 175.5MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 189MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 202.5MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 229.5MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 204.326MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 204.326MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 204.326MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 204.326MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 204.326MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 204.326MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 204.326MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 204.326MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 204.326MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 204.326MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 195.84MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 195.84MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 195.84MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 190.247MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 190.247MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 160.833MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 160.833MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 160.833MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 160.833MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 160.833MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 160.833MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 160.833MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 160.833MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 160.833MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 160.833MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,Dell Monitor) mode clock 148.759MHz exceeds DDC maximum 110MHz
(WW) I810(0): Bad V_BIOS checksum
(WW) I810(0): xf86AllocateGARTMemory: allocation of 16 pages failed
(WW) I810(0): xf86AllocateGARTMemory: allocation of 8 pages failed
(WW) I810(0): xf86AllocateGARTMemory: allocation of 2048 pages failed
(WW) I810(0): xf86AllocateGARTMemory: allocation of 2048 pages failed
(WW) I810(0): xf86AllocateGARTMemory: allocation of 9152 pages failed
(WW) I810(0): xf86AllocateGARTMemory: allocation of 1121 pages failed
(WW) I810(0): Extended BIOS function 0x5f05 not supported.
(WW) I810(0): Extended BIOS function 0x5f05 not supported.
(WW) I810(0): Extended BIOS function 0x5f28 not supported.
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32

```and the DRM from DMESG:

```
bruno@bnogueira:~$ sudo dmesg | grep drm
[17179601.844000] [drm] Initialized drm 1.0.1 20051102
[17179601.848000] [drm] Initialized i915 1.5.0 20060119 on minor 0
```Someone knows how to fix ? I've tried to build from this thread [http://ubuntuforums.org/showthread.php?t=134069](http://ubuntuforums.org/showthread.php?t=134069) but returned lotta of errors.

I'm running "Ubuntu 6.10 - the Edgy Eft - released in October 2006"

Any ideas ?

---

### Post by Kateikyoushi on 2006-11-07
Why do you use XGL on edgy ? It comes with Aiglx built in which is faster than xgl on intel chips.

---

### Post by d3v1ant_0n3 on 2006-11-07
Indeed- I found it much faster, and with edgy, stupidly painless to install/ setup- Just install the beryland emerald packages, and reboot.

---

### Post by andresv on 2006-11-20
Does ubuntu edgy really come with AIGLX built in? I have an Intel Card running on i810, and it has been simply impossible to run beryl. I constantly get "Xlib:  extension "GLX" missing on display ":0.0"" when I run glxinfo.

AIGLX support seems very buggy on edgy - everything else has been extremely easy to configure, but beryl+AIGLX has been impossible so far!

---

### Post by Trance Gemini on 2006-11-21
> I have an Intel Card running on i810, and it has been simply impossible to run beryl. I constantly get "Xlib: extension "GLX" missing on display ":0.0"" when I run glxinfo.
The same here! I have A Fujitsu-Siemens P7010 laptop with Intel 835 card that runs in "i810" driver (in xorg.conf).
Any driver change cause blue screen (of death), and after that I need to restore my original xorg.conf.

I also get an "no direct rendering" stuff. That is strange, because some time ago (on 6.06) I ran XGL without any problem.

---

### Post by Ramses de Norre on 2006-11-21
Did you enable aiglx and compositing in xorg.conf?

---

### Post by Trance Gemini on 2006-11-21
> Did you enable aiglx and compositing in xorg.conf?
Composition - yes, but as I remember aiglx is already enabled in edgy, no?
Anyway how do I check it?

---

### Post by Ramses de Norre on 2006-11-21
I made this sections, I guess you need to revert the composite and aiglx options if you want them enabled.
(for clarity: I have both disabled)

```
Section "Extensions"
        Option  "Composite"     "0"
#       Option  "RENDER"        "Enable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection


```

---

### Post by Trance Gemini on 2006-11-21
I made it like you said, but when I try to execute "beryl" it sais
```

XGL Absent, checking for nVidia
nVidia Absent, assuming AIGLX
beryl: No composite extension

```

What is that?

---

### Post by andresv on 2006-11-21
> **Ramses de Norre said:**
> I made this sections, I guess you need to revert the composite and aiglx options if you want them enabled.
(for clarity: I have both disabled)

```
Section "Extensions"
        Option  "Composite"     "0"
#       Option  "RENDER"        "Enable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection


```

I made that (enabling Composite, RENDER and AIGLX). Same result:

```
Xlib:  extension "GLX" missing on display ":0.0".
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
Xlib:  extension "GLX" missing on display ":0.0".
```

Is it possible that AIGLX support is still incomplete on edgy?

---

### Post by ronmarley1 on 2006-11-21
To use Beryl on Edgy and Intel integrated graphics, follow this HowTo:
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)
Trevino's repo. is for the SVN updates, you may want to avoid that, as sometime daily updates mean daily breakages.  To get the official 0.1.2 release from 11/7/06, add this to your sources.list:
"deb [http://ubuntu2.beryl-project.org](http://ubuntu2.beryl-project.org) edgy main" (without the quotes)
You don't need XGL (AIGLX is built in, and runs fine for me, by the way) and you have an Intel card, not NVidia.
I have an Intel 855 using the same 810 driver on Edgy.  The setup should take 5 mins.

---

### Post by andresv on 2006-11-21
> **ronmarley1 said:**
> To use Beryl on Edgy and Intel integrated graphics, follow this HowTo:
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)
You don't need XGL (AIGLX is built in) and you have an Intel card, not NVidia.

Following that HowTo was my very first attempt, a few days ago. It didn't work, and gave me the message on "GLX missing". I wonder what I did wrong, but my Edgy seems to be expecting GLX for some odd reason.

At this point, I wonder if a system-wide reinstall is the only option. The failed install of Beryl has been frustrating. I wonder if there is a serious bug in the way AIGLX is built in for Intel cards (mine uses the i810 module).

---

### Post by andresv on 2006-11-21
> "deb [http://ubuntu2.beryl-project.org](http://ubuntu2.beryl-project.org) edgy main" (without the quotes)
You don't need XGL (AIGLX is built in, and runs fine for me, by the way) and you have an Intel card, not NVidia.
I have an Intel 855 using the same 810 driver on Edgy. The setup should take 5 mins.

I changed the repository from [http://ubuntu.beryl](http://ubuntu.beryl)... to [http://ubuntu2.beryl](http://ubuntu2.beryl)... and am trying again. It may be that the "2" makes the difference (on the howto, the "2" does not appear!)

---

### Post by ronmarley1 on 2006-11-21
> **andresv said:**
> Following that HowTo was my very first attempt, a few days ago. It didn't work, and gave me the message on "GLX missing". I wonder what I did wrong, but my Edgy seems to be expecting GLX for some odd reason.

At this point, I wonder if a system-wide reinstall is the only option. The failed install of Beryl has been frustrating. I wonder if there is a serious bug in the way AIGLX is built in for Intel cards (mine uses the i810 module).

I'm not sure why you're getting the "GLX missing" error.  Are you using Edgy or Dapper?  Did you make any changes to your Xorg.conf file before trying the HowTo I linked to?  To see if a reinstall would help, boot the live CD and the try the HowTo again and see if Beryl will work.  It did for me.

---

### Post by ronmarley1 on 2006-11-21
> **andresv said:**
> I changed the repository from [http://ubuntu.beryl](http://ubuntu.beryl)... to [http://ubuntu2.beryl](http://ubuntu2.beryl)... and am trying again. It may be that the "2" makes the difference (on the howto, the "2" does not appear!)
Good luck!  Let me know how it goes.  Maybe you got the SVN version from Trevino's repo?  The repo with the "2" has the "official" 0.1.2 release, which works for me.  
Maybe starting the Beryl install process from scratch will help?
1. Restore your original Xorg.conf file.  I can send you mine if you don't have a copy.
2.  Go into Synaptic and uninstall nything with Beryl in the name.
3.  If you did add Tevino's repo, comment it out in your sources list.
4.  Run the HowTo again
OR
4.  Reload your sources and search for Beryl again and add the 0.1.2 versions.

---

### Post by andresv on 2006-11-21
> I'm not sure why you're getting the "GLX missing" error. Are you using Edgy or Dapper? Did you make any changes to your Xorg.conf file before trying the HowTo I linked to? To see if a reinstall would help, boot the live CD and the try the HowTo again and see if Beryl will work. It did for me.


Using Edgy (fresh install, not an upgrade). At this point, after so many attempts, my Xorg.conf has been modified many times (I tried the HowTo you linked to a few days ago, but in between many other suggestions of people, etc. have made me change the Xorg.conf).

I would like to avoid the complete reinstall, and rather reinstall the X server part... but I have to figure that out.

This beryl install has been incredibly hard, even for someone who has installed many other distros before. It is very puzzling to me that it works easy for some other people, but in this case gives the strange "GLX missing" error...

---

### Post by andresv on 2006-11-21
> 1. Restore your original Xorg.conf file. I can send you mine if you don't have a copy.

I would be very thankful for that!

---

### Post by Ramses de Norre on 2006-11-21
Isn't trevino the guy who got packages in his repo that altered your fstab and sudoers files? Looks like I wouldn't trust him..

There are threads about it in the café.

---

### Post by ronmarley1 on 2006-11-21
> **Ramses de Norre said:**
> Isn't trevino the guy who got packages in his repo that altered your fstab and sudoers files? Looks like I wouldn't trust him..

There are threads about it in the café.
Yes.  I saw something where it one of the packages in his repo changed someone's desktop wallpaper and they could not change it!  I would stay away from that also!

---

### Post by ronmarley1 on 2006-11-21
> **andresv said:**
> I would be very thankful for that!
Here's mine.  I hope it helps.  I hear what you are saying about it working for some folks and not others.  It took me a couple of days to get Compiz working on Dapper.  Then, moving to Beryl was another project.  Beryl on Edgy was easy for me (sorry it's not been for you).  I just HAD to have the bells and whistles!  For some folks, it seems to be a snap, and others, it's trial-and-error.  Very frustrating!
My Xorg:
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection




```

---

### Post by andresv on 2006-11-21
Same output :-k after trying the xorg.conf file you sent me and following the HowTo ... I have to give up beryl for now.

---

### Post by ronmarley1 on 2006-11-21
> **andresv said:**
> Same output :-k after trying the xorg.conf file you sent me and following the HowTo ... I have to give up beryl for now.
With hindsight, considering the amount of time I spent on Conpiz and Beryl, I would not go through that again.  It's just that once I start something, I gotta finish it.  Maybe when Beryl moves out of the alpha stage, you can try again.  Sorry I could not help more.

---

### Post by andresv on 2006-11-21
ronmarley1: thanks a lot for your help! I am spending too much time on trying beryl - my other projects are suffering from that :( I think I will try Beryl in a couple months time again. I really wanted the bells and whistles, but I guess that will be for some other time...

---

### Post by andresv on 2006-11-21
> **ronmarley1 said:**
> With hindsight, considering the amount of time I spent on Conpiz and Beryl, I would not go through that again.  It's just that once I start something, I gotta finish it.  Maybe when Beryl moves out of the alpha stage, you can try again.  Sorry I could not help more.

Beryl NOW WORKING!

Although I had decided not to try anymore, I decided to trace the "history" of the problem. I realized I began (in BIG confusion) by installing nvidia-glx (I believed the i810 wouldn't work - misled by [this review]("http://lunapark6.com/?p=2501")). I tried uninstalling nvidia-glx - and beryl started working.

---

### Post by ronmarley1 on 2006-11-21
> **andresv said:**
> Beryl NOW WORKING!

Although I had decided not to try anymore, I decided to trace the "history" of the problem. I realized I began (in BIG confusion) by installing nvidia-glx (I believed the i810 wouldn't work - misled by [this review]("http://lunapark6.com/?p=2501")). I tried uninstalling nvidia-glx - and beryl started working.
Whoo-hoo!  Good for you!  As Ramses said in a previous post, I would stay away from Trevion's SVN repos for updating Beryl.  Wait until 0.1.3 is "officially" released, and it should be in the "2" repo I gave you a day or two after that (as soon as someone makes the packages).  Have fun spinning the cube!  Show it to your Window$ using colleagues; it'll make their teeth fall out.

---

### Post by Trance Gemini on 2006-11-22
Some of the last posts gave me hope to run beryl on my laptop, because, as I have posted before, I had the same problem.

I changed the repo to "ubuntu2...." and remembered, that my laptop isn't now connected to internet due to corporate security policy in company where I work. I will be able to get to internet only on weekends, but I managed to download all debs from ubuntu2.beryl-project.org and copy it to laptop via flash drive.

So I have a question - how do I install beryl when I have the packages in /home/vadim/debs folder (and not connected to internet)? Is it possible?

P.S. I am happy for you, andresv, that you can finally enjoy beryl at 100%! I am sure I will make it wor too!

---

### Post by ronmarley1 on 2006-11-22
> **Trance Gemini said:**
> So I have a question - how do I install beryl when I have the packages in /home/vadim/debs folder (and not connected to internet)? Is it possible?
Use a terminal window to navigate to the folder where the debs are then:
```
dpkg --install file.deb
--or--
dpkg -i file.deb
```
PS,this site may also be a good resource for you:
[http://forum.beryl-project.org/](http://forum.beryl-project.org/)

---

