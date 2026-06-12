---
title: "no direct rendering"
date: 2008-05-11
forum: General Help
---

### Post by Eviltelm on 2008-05-11
HI,

I'm using hardy here, and compiz seem to work pretty good, but when i try running 3d games like glchess (Yes, i've done sudo apt-get install python-opengl python-gtkglext1)
I installed fglrx using the hardware controller (bad translation maybe . . ., but i thing u get the idea)

```
tiago@tiago-laptop:/etc/gamin$ glchess 
Using OpenGL:
VENDOR=ATI Technologies Inc.
RENDERER=ATI Mobility Radeon X1400
VERSION=1.4 (2.1.7412 Release)
EXTENSIONS=GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_ATI_draw_buffers GL_ATI_texture_env_combine3 GL_ATIX_texture_env_combine3 GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_NV_blend_square GL_NV_texgen_reflection GL_NV_texture_rectangle GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_shadow_ambient GL_SUN_multi_draw_arrays 
```

doesn't seem to give back any error but the game looks really ugly when it gives 3D image, when it does not it swaps between 3d and 2g with horizontal lines . . .

```
tiago@tiago-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 1.4 (2.1.7412 Release)

tiago@tiago-laptop:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
Falha de segmentção (translated : segmentation fault)

tiago@tiago-laptop:~$ glxgears
17117 frames in 5.0 seconds = 3421.996 FPS
17273 frames in 5.0 seconds = 3453.559 FPS
(again crappy image with horizontal lines)

tiago@tiago-laptop:~$ glxinfo | grep direct --color
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)

```

I haven't used ubuntu in a long time, so a few questions, this time i just installed the compiz manager, no xgl to my ati, should i install it?? how is it running without it?
When starting ubuntu a strange noise comes from the mic I think, any ideas about that??


Sorry for big text, thanks for any help ;)

cya

---

### Post by Eviltelm on 2008-05-12
**bump**

---

### Post by FuturePilot on 2008-05-12
I think there's no direct rendering because of
```
(LIBGL_ALWAYS_INDIRECT set)
```
I'm not sure how you would change that though.

---

### Post by Eviltelm on 2008-05-12
hmm
[look at alexei colin post]("https://bugs.launchpad.net/ubuntu/+source/desktop-effects/+bug/137388")
I will try to change that

thanks

---

### Post by Eviltelm on 2008-05-14
Games work with compiz off, any more ideas?

---

### Post by phoenix5002 on 2008-05-14
it might help to post the contents of your xorg.conf file.  just open it with gedit with:
**sudo gedit /etc/X11/xorg.conf**

and paste it into code tags on this thread.


Also, I get "no direct rendering" when I install the fglrx driver on my ati card.  However, when I use the open source driver then I get "Direct Rendering: Yes".

---

