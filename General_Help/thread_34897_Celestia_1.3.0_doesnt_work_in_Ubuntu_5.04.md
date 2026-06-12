---
title: "Celestia 1.3.0 doesnt work in Ubuntu 5.04"
date: 2005-05-16
forum: General Help
---

### Post by Peter Alien on 2005-05-16
I installed Celestia in Ubuntu 5.04, but that doesnt work :(

Did someone installed it too ?

Can anyone tell me why it doesnt work ?


Thanks

---

### Post by kleeman on 2005-05-16
Works fine here in hoary (version 1.3.0). You need to provide more info to get hrlp....
eg

graphics card
error symptom
is graphical acceleration enabled?

etc

---

### Post by Peter Alien on 2005-05-17
My graphics card is a Matrox Millenium G400 Max.

The prog starts to load in the toolbar and waits a minute and then disapear :(

I have the same prog in WinXP Pro, and it works fine, so there isnt no problem with the graphics card.

---

### Post by kleeman on 2005-05-17
execute the program in a terminal window and see what error it produces....

---

### Post by Peter Alien on 2005-05-17
The Terminal gives the error:

libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x30
Unable to resolve Xmu symbols - please check your Xmu library installation.
celestia: ERROR: Communication problem with celestia, it probably crashed.

I'm still a n00bie in Linux, what does that mean ?

---

### Post by kleeman on 2005-05-17
Sounds like 3d graphics isn't working properly. Use synaptic to look for something like libxmu and install it. What does glxinfo show?

---

### Post by Peter Alien on 2005-05-17
Well... it shows:

name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x30
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_control,
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_visual_select_group
OpenGL vendor string: VA Linux Systems Inc.
OpenGL renderer string: Mesa DRI G400 20030328 AGP 1x x86/MMX/SSE
OpenGL version string: 1.2 Mesa 6.2.1
OpenGL extensions:
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_texture_compression,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_crossbar, GL_ARB_texture_rectangle,
    GL_ARB_transpose_matrix, GL_ARB_vertex_program, GL_ARB_window_pos,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_logic_op, GL_EXT_clip_volume_hint,
    GL_EXT_compiled_vertex_array, GL_EXT_copy_texture,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_polygon_offset, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_stencil_wrap, GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_object,
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels,
    GL_ATI_texture_env_combine3, GL_IBM_rasterpos_clip, GL_MESA_ycbcr_texture,
    GL_MESA_window_pos, GL_NV_light_max_exponent, GL_NV_texture_rectangle,
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_NV_vertex_program1_1,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod,
    GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x28 24 tc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x29 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x2a 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x2b 24 dc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x30 24 dc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x31 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x32 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow

---

### Post by Peter Alien on 2005-05-17
I installed the rest of the libxmu files, and i re-installed Celestia 1.3.0,.. and it keeps in the same error :(

---

### Post by kleeman on 2005-05-17
Interesting (but not hopeful ;-)) I did a google on your error message and someone else has noticed it with Fedora Core 3 and with something like your  graphics card apparently

[http://www.devolution.com/pipermail/sdl/2004-November/065806.html](http://www.devolution.com/pipermail/sdl/2004-November/065806.html)

The upshot of this thread (I am no graphics card expert) seems to be that certain 3d graphics operations are not working with the driver. I suspect that Celestia is doing such operations (as is glxinfo btw) so you may be out of luck with your graphics card. Does glxgears work btw?

---

### Post by Peter Alien on 2005-05-17
glxgears worked, and gave me:

libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x30
504 frames in 5.0 seconds = 100.800 FPS
660 frames in 5.0 seconds = 132.000 FPS
399 frames in 5.0 seconds = 79.800 FPS

---

### Post by kleeman on 2005-05-17
Hmmm that seems very slow for a dri enabled graphics card. I suspect strongly a graphics driver issue. You should research it using google. The dri project is one place to look (that is the group who did the 3d).

---

### Post by kiddyfurby on 2005-05-17
I have intel graphics card, I get the Xmu problem as well

I did this:

$ sudo ln -s /usr/X11R6/lib/libGL.so.1 /usr/lib/libGL.so
$ sudo ln -s /usr/X11R6/lib/libXmu.so.6 /usr/lib/libXmu.so

and it worked, hope it helps

solution from: [https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=126422](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=126422)

---

### Post by Peter Alien on 2005-05-18
IT WORKED.... urrrraaiiiiii  :)  \\:D/ 

Many thanks kiddyfurby, and for kleeman too... who tried to resolve the problem.

---

