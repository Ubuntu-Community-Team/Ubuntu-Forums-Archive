---
title: "[SOLVED] compiz ati radeon 340M"
date: 2008-06-01
forum: General Help
---

### Post by dmizer on 2008-06-01
as far as i can see, 3D desktop effects should work.  i do not know why they are not.  i DID have it working with beryl back in feisty.

lspci:
```
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M
```

lsmod:
```
ati_agp                 9996  1 
agpgart                34760  2 drm,ati_agp
```

relevant xorg.conf section:
```
Section "Device"
	Identifier	"Ati Technologies Inc Radeon IGP 330M/340M/350M"
	Driver		"ati"
	BusID		"PCI:1:5"
	Option		"AGPMode"		"4"
	Option		"AGPFastWrite"		"true"
	Option		"EnablePageFlip"	"true"
	Option		"DCCMode"
	Option		"ColorTiling"		"false
	Option		"SubPixelOrder"		"NONE"

EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Option		"DPMS"
	Option		"LVDSBiosNativeMode"	"false"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon IGP 330M/340M/350M"
	Monitor		"Configured Monitor"
	DefaultDepth	24
EndSection
```

glxinfo:
```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
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
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20061018 AGP 4x x86/MMX/SSE2 NO-TCL
OpenGL version string: 1.3 Mesa 7.0.3-rc2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_logic_op, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_histogram, 
    GL_EXT_packed_pixels, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_stencil_wrap, GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_MESA_ycbcr_texture, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x55 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
```

glxgears output:
```
1476 frames in 5.0 seconds = 295.090 FPS
1514 frames in 5.0 seconds = 302.692 FPS
1512 frames in 5.0 seconds = 302.371 FPS
1513 frames in 5.0 seconds = 302.453 FPS
1512 frames in 5.0 seconds = 302.306 FPS
1512 frames in 5.0 seconds = 302.236 FPS
1514 frames in 5.0 seconds = 302.721 FPS
1513 frames in 5.0 seconds = 302.586 FPS
1513 frames in 5.0 seconds = 302.454 FPS
1462 frames in 5.0 seconds = 291.580 FPS
```

mesa is installed:
```
$ dpkg -l | grep mesa
ii  libgl1-mesa-dri   7.0.3~rc2-1ubuntu3   A free implementation of the OpenGL API -- D
ii  libgl1-mesa-glx   7.0.3~rc2-1ubuntu3   A free implementation of the OpenGL API -- G
ii  libglu1-mesa      7.0.3~rc2-1ubuntu3   The OpenGL utility library (GLU)
ii  mesa-utils        7.0.3~rc2-1ubuntu3   Miscellaneous Mesa GL utilities
```

but when i attempt to enable desktop effects through the gnome-appearance-properties script, i get this:
```
Checking for Xgl: not present. 
Found laptop using ati driver. 
aborting and using fallback: /usr/bin/metacity
```

what's missing, and how can i enable 3D?

---

### Post by dmizer on 2008-06-01
found [this](http://forlong.blogage.de/article/pages/Compiz-Check):

```
$ ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon IGP 330M/340M/350M
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Your current resolution is too high to run Compiz. 

Would you like to know more? (Y/n) y

 Your resolution is 1024x768 but the maximum 3D texture size that your
 graphics card is capable of is 512x512. Thus Compiz won't be able to run
 on this setup. You have to decrease the resolution first (in case you are
 using a dual-head setup, try disabling one monitor and run the script again).
```
i am not using a dual-head setup.

but again, i know this is not true because i had this working at 1024x768 in feisty.

---

### Post by kingkookie on 2008-06-01
I have the same problem on Hardy.  It worked perfectly with Gutsy, but for some reason, something has changed either in the driver or the configuration.

It would be nice to get this resolved, among other issues.

---

### Post by kingkookie on 2008-06-01
Update:  It seems I had a bit more luck that yourself.

I ran the compiz-check script that you found and it provided output saying that because of some nasty bug in the ati driver causing lockups on some machines, the driver had been blacklisted on Hardy.  Then it kindly asked me if I wanted to skip blacklist check and after saying yes, I was able to apply the the compiz desktop effects.  

So, your issue seems to be a variant from mine.  I have compared our xorg.conf files and they are identical, so that is not the problem.  Hopefully someone smarter than I can provide suggestions...

```
frodo@Gondor:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon IGP 330M/340M/350M
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Laptop using radeon driver. 

Would you like to know more? (Y/n) y

 It has been detected, that you are running a laptop with an ATI chip.
 The radeon driver supports Compiz out-of-the-box but because of a nasty bug
 in the driver that causes X to freeze on some cards, this particular
 combination had to be blacklisted in Ubuntu "Hardy Heron".

 In case you already used Compiz successfully on Ubuntu 7.10 (Gutsy), it is
 safe to skip the blacklist. 

Do you want to skip blacklist checks by Compiz? (y/N) y
frodo@Gondor:~$ 

```

---

### Post by Forlong on 2008-06-01
> **dmizer said:**
> but again, i know this is not true because i had this working at 1024x768 in feisty.
Try skipping the blacklist then (but don't complain afterwards):
```
mkdir -p $HOME/.config/compiz && echo SKIP_CHECKS=yes >> $HOME/.config/compiz/compiz-manager
```

---

### Post by Rocket2DMn on 2008-06-01
The workaround is like Forlong said, you can read more here: [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

### Post by dmizer on 2008-06-02
> **Forlong said:**
> Try skipping the blacklist then (but don't complain afterwards):
```
mkdir -p $HOME/.config/compiz && echo SKIP_CHECKS=yes >> $HOME/.config/compiz/compiz-manager
```

works like a champ.  thank you very much.

---

