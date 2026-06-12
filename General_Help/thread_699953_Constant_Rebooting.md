---
title: "Constant Rebooting"
date: 2008-02-17
forum: General Help
---

### Post by TorchlightJay on 2008-02-17
Hello,

I am running the latest Ubuntu Hardy heron alpha. I have two problems that are kind of upsetting me. 

Just recently, my kdm keeps reloading itself. After about 5-10 minutes, my session will log out and go back to the kdm login menu. It'll keep doing it no matter how many times I log in. I am using 2.6.24-8-generic kernel and my software is up-to-date to the minute. Well I don't know why it does it. It may be power related but I don't know. 

Also, if I close the lid on my notebook or the screen saver comes on, or I keep clicking the screen dimmer, the screen goes black (backlight still on) and I can't get it back. The session is still running but not screen. I do not know what to do?

Any ideas?

---

### Post by Crafty Kisses on 2008-02-17
> **TorchlightJay said:**
> Hello,

I am running the latest Ubuntu Hardy heron alpha. I have two problems that are kind of upsetting me. 

Just recently, my kdm keeps reloading itself. After about 5-10 minutes, my session will log out and go back to the kdm login menu. It'll keep doing it no matter how many times I log in. I am using 2.6.24-8-generic kernel and my software is up-to-date to the minute. Well I don't know why it does it. It may be power related but I don't know. 

Also, if I close the lid on my notebook or the screen saver comes on, or I keep clicking the screen dimmer, the screen goes black (backlight still on) and I can't get it back. The session is still running but not screen. I do not know what to do?

Any ideas?
Sounds to me like either your X is crashing, or your laptop is overheating.

---

### Post by TorchlightJay on 2008-02-17
Hey,

I don't think the notebook is overheating, I am feeling the back and the vents, it's warm but not hot in the least bit. I must add, this has just recently starting too. It might be X crashing.

What seems to happen is it ends my session. The computer doesn't reboot or anything, I just seem to log out of session automatically and then I am at the kdm login screen and have to type my password and hit enter. 

I just checked my "Log Out.." screen under the K Menu and my only option is Log Off. Before I had all the options (Suspend, Hibernate, Reboot, log off, Shut Down.) This happened maybe 3 days ago when I recognized it. 

any help would be great. Thanks.

---

### Post by TorchlightJay on 2008-02-17
might I add, I installed Nvidia x86 linux drive 169.09 and used nvidia-xconfig on xorg.conf. Does that do anything? What do I need to do to fix it?

---

### Post by socceroos on 2008-02-20
> **TorchlightJay said:**
> might I add, I installed Nvidia x86 linux drive 169.09 and used nvidia-xconfig on xorg.conf. Does that do anything? What do I need to do to fix it?

It would seem to me that it is in fact your nvidia drivers that have caused the problem. I know in my own experience that X crashed with particular versions of the nvidia driver.

Here is what I would suggest doing (be aware - if you do this correctly, it will not be using the nvidia drivers you've previously installed - but your problem should go away):

Hit the keys CTRL->ALT->F1   This should take you to a black screen that is asking for your username and password. Enter your normal login details.

Once you've logged in you'll see some more text on the screen - if you've logged in correctly then you are successfully using the command line!

To reconfigure your X-server (the server that helps display the graphical user interface that you use), try typing this:

sudo dpkg-reconfigure xserver-xorg

You will be asked a list of questions, accept all the defaults. But when it comes to ask you what the resolutions of your monitor are - be sure to select the ones you know work (you select them by pressing the space-bar). Also, if it asks you for your monitor details - just select the simple setup instead of advanced (a lot easier).

To get back to your GUI press ALT->F7.

If you get stuck on this then let me know.

---

### Post by Crafty Kisses on 2008-02-21
> **TorchlightJay said:**
> might I add, I installed Nvidia x86 linux drive 169.09 and used nvidia-xconfig on xorg.conf. Does that do anything? What do I need to do to fix it?

Hmmm, post the following output: ```
glxinfo
```

---

### Post by TorchlightJay on 2008-02-22
```

name of display: :1.0
display: :1  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe,
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync,
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float,
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap,
    GLX_EXT_framebuffer_sRGB
GLX version: 1.2
GLX extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_SGIX_fbconfig,
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce Go 6150/PCI/SSE2/3DNOW!
OpenGL version string: 1.2 (2.1.2 NVIDIA 169.09)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_imaging, GL_ARB_multitexture,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow,
    GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_window_pos, GL_ARB_texture_non_power_of_two, GL_ARB_vertex_program,
    GL_ARB_fragment_program, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color,
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap,
    GL_EXT_texture3D, GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, GL_EXT_texture_lod,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array,
    GL_EXT_framebuffer_object, GL_ATI_texture_mirror_once,
    GL_IBM_texture_mirrored_repeat, GL_NV_blend_square,
    GL_NV_texgen_reflection, GL_NV_texture_rectangle,
    GL_NV_texture_env_combine4, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod,
    GL_SGIX_depth_texture, GL_SGIX_shadow

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

that's my glxinfo

---

