---
title: "ATI Radeon"
date: 2008-03-29
forum: General Help
---

### Post by RandomRitz on 2008-03-29
Hey everyone , i know there is alot of posts about ATI graphics cards, i have went through alot of them and have not found an answer yet , i am new to linux and i have ATI Radeon 9000 graphics. I am trying to get compiz fusion to work when i found another post about it telling me to download a driver. i downloaded this driver but i am not able to install it, its a .run and the drivers name is ati-driver-installer-8.28.8.run , when i go to run this i click on run in a terminal, this open up in a text editor and starting writing out a bunch of stuff, it write this out.

Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.................................................................................................................................

Plus alot more dots, and then a little more writing then it closes.

Other than this problem i have gone to application/Add remove , and installed the desktop effects. i went to system , appearance and visual effects, went to enable extra visual effects and it said the desktop effects cannot be enabled.

Comp Specs:
Dell Latitude D600 Laptop
Processor: Intel Celeron M 1.4 Ghz
Harddrive: 35 GB (Currently dual botting windows xp and ubuntu 8 beta)
Ram: 512 Mb
Graphics: Ati Radeon 9000

Ubuntu was installed with Wubi

Does anyone know how i can get compiz fusion to work with ATI Radeon 9000 graphics. ?

**
GLXINFO
**
--------------------------
ryan@ryan-laptop:~$ glxinfo
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 4x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.3-rc2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_histogram, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_ATI_fragment_shader, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_window_pos, GL_NV_blend_square, 
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
0x56 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

---

### Post by dstew on 2008-03-29
I think what you did was successfully run an installer script for an ATI driver. What you are calling a text editor was actually the Terminal window, which uses text to get commands, or show you what is happening behind the scenes.

To get your new driver to run the display, you might have to reconfigure the xserver, the operating system software that runs the display, and tell it to use the new driver. I think you installed the driver named fgrlx. To reconfigure the xserver, open a terminal window (Applications --> Accessories --> Terminal) and on the command line enter```
sudo dpkg-reconfigure xserver-xorg
```Answer the questions the best you can (read the explanations). When you get to the display configuration, first note the current driver (likely to be ati) and resolution. See if you can select the fglrx driver. Choose as a highest resolution the resolution you actually use. When you are done, restart the xserver by pressing ctrl-alt-backspace.

If the display now is not working, you can get a command line by pressing ctrl-alt-F1. Then, reconfigure the xserver again but choose the ati driver and original resolution to get a working dislplay. Post back to tell us what happened. If it did not work we might try something else.

---

### Post by pointone on 2008-03-29
I think the more correct way is to run "aticonfig --initial" to configure the X server to use the driver.

The even more correct way would be to install the latest version of fglrx (8.28.8 is quite old) by following [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide") (method 2).

The still more correct way would be to use Ubuntu's Restricted Drivers Manager to automatically install and configure fglrx. This will install version 8.37.6, I believe.

The best solution for you, though, would probably be to use the open source ATI driver since it supports your card fully and is generally nicer than the proprietary driver which has a number of issues.

Note that if you use the proprietary fglrx driver, only versions higher than 8.42.x support AIGLX. If you want to enable desktop effects/Compiz on older versions, you will need to install Xgl ("sudo apt-get install xserver-xgl"). If you use the latest version of fglrx or the open source driver, this is not necessary.

Were desktop effects not working out of the box? They should have been...

---

### Post by Zimmer on 2008-03-29
I am almost certain there is no 3d support for a 9000 with proprietary drivers

See
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
The 9xxx series supported is 9500 and above... but don't stop looking on my account..

---

