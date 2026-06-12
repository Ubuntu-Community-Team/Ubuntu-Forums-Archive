---
title: "graphics card doesn work"
date: 2008-06-01
forum: General Help
---

### Post by crazyfuturamanoob on 2008-06-01
I got VIA K8M800 graphics card.
For some reason almost every time 
I try to run something that needs 
opengl, or to draw something in 3d,
I get either hard freeze or then I'll
get back to login screen with no error
messages, instantly. How to fix it?
This stupid problem prevents me from
doing anything with my computer, but
browsing internet with firefox or
using the default apps & games that
came along with ubuntu cd. 
Battle for Wesnoth seems to work anyway.
And finally, *I Like Apple Pie!*

Edit: Here is the output of *glxinfo*:
```
arho@timo-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: VIA Technology
OpenGL renderer string: Mesa DRI UniChrome (K8M800) 20060710
OpenGL version string: 1.2 Mesa 7.0.3-rc2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_histogram, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array, 
    GL_APPLE_packed_pixels, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texgen_reflection, GL_OES_read_format, 
    GL_SGI_color_matrix, GL_SGI_color_table, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x23 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x2b 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x47 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
arho@timo-desktop:~$ 

```

---

### Post by Kevbert on 2008-06-01
I assume you want to run Compiz.  You may be out of luck, but you could try running: [Compiz-Check]("http://forlong.blogage.de/article/pages/Compiz-Check") which will give you a clue to your openGL problems.  You also need to run
```
glxinfo
```
in terminal and post the text on here.

---

### Post by crazyfuturamanoob on 2008-06-01
> **Kevbert said:**
> I assume you want to run Compiz.  You may be out of luck, but you could try running: [Compiz-Check]("http://forlong.blogage.de/article/pages/Compiz-Check") which will give you a clue to your openGL problems.  You also need to run
```
glxinfo
```
in terminal and post the text on here.

I tried to run compiz-check but it went to login screen
when I tried to run the script. I saw "Gathering information about your
system" and some other text then it suddenly went to login screen.
Doesn't work. But I added glxinfo to my first post.

---

### Post by Kevbert on 2008-06-01
One thing I didn't notice before is that you don't have much RAM memory.  It's possible that this is your problem.

---

### Post by crazyfuturamanoob on 2008-06-02
Oh yeah?? 1gb not enough????
Some things like baboviolent run perfectly with
my 2nd computer, which has 256mb RAM, so why they
wouldn't run on this computer, which has 1024 mb RAM?
256mb RAM is just enough. Or why would a c&c3 installer
make hard freeze?

---

### Post by crazyfuturamanoob on 2008-06-02
Even if I try to run *pivot* with wine I get either 
hard freeze or I get back to login screen.

---

### Post by Forlong on 2008-06-02
Kevbert was assuming you are on that 256 MB RAM machine, because of your signature.

Please post the output of
```
grep drivers /var/log/Xorg.0.log
```


P.S. Please don't add line breaks manually to your postings. The forum supports automatic word wrapping.

---

