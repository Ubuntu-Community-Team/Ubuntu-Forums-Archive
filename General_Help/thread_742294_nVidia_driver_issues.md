---
title: "nVidia driver issues"
date: 2008-04-01
forum: General Help
---

### Post by zingbats on 2008-04-01
Hey Guys,

I've just upgraded to Hardy, and I like the changes I've noticed. However, my graphics have been playing up.

I've run the latest (169.12) .run file from nVidia. It tells me that the drivers are already installed, and asks me if I want to reinstall them. I say yes, and it takes me through a number of steps until I get to the "ERROR: Unable to find the kernel source tree for the currently running kernel" message.

Since the drivers are installed; I figure there should be away to stop me living in the ghastly 800*600  resolution, however, when I try and configure the drivers to "nv", the test fails. 

I've included the appropriate section of my xorg.conf file thus:

[quote=xorg]
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Vendorname	"NVIDIA"
	Boardname	"NVIDIA GeForce 8 Series"
	Screen	0
EndSection
[/quote]

I have no idea how to get the nvidia driver to be the one that loads.

I've installed the nvidia-settings package, but that tells me to restart the server, which has no effect.

Any help would be appreciated,
Thanks.

---

### Post by warp99 on 2008-04-01
You don't need the latest drivers from Nvidia since they are available in Ubuntu in the restricted-modules packages. This guide should help you:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29#head-7192e75555e2fa307b2ee7415a0367b58a9fe866](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29#head-7192e75555e2fa307b2ee7415a0367b58a9fe866)

This has been the method in Ubuntu since version 7.04. See also the troubleshooting sections on the same help page.

---

### Post by zingbats on 2008-04-01
I removed the downloaded nvidia drivers, downloaded nvidia-glx-new.

Now, when I start up, I get a blank screen after the initial CTRL+ALT+1 terminal.

Any ideas on what's causing this, or shall I just start with a fresh 8.04 install?

---

### Post by forrestcupp on 2008-04-01
So you can't even boot to the desktop?

Boot to your recovery console and type
```
apt-get --purge remove nvidia*
```
To remove everything to do with nvidia.  Then type
```
dpkg-reconfigure xserver-xorg
```
And choose the vesa drivers to ensure you will be able to boot to your desktop.  When that's done, type **exit** to exit that session and boot to the desktop.  When you are there, go to System->Administration->Restricted Drivers Manager and install your nvidia drivers with that.  You don't need to install the nvidia-settings package because that is for the legacy drivers and it will cause you problems because it depends on the old drivers.  Nvidia-settings is included in the nvidia-glx-new package that you will install with the RDM.

Once you have rebooted with your restricted drivers installed, you should be able to find your Nvidia settings app in Applications->System Tools.  If not, open a terminal and type
```
gksu nvidia-settings
```

---

### Post by zingbats on 2008-04-01
In the restricted drivers section (now Hardware Drivers)

It says:

"No proprietary drivers are in use on this system"

Also, let it be known that when using dpkg, I got errors about overwriting a custom xorg.conf file, and had to restore a backup.

---

### Post by Crafty Kisses on 2008-04-01
> **zingbats said:**
> In the restricted drivers section (now Hardware Drivers)

It says:

"No proprietary drivers are in use on this system"

Also, let it be known that when using dpkg, I got errors about overwriting a custom xorg.conf file, and had to restore a backup.

If they are enabled, then post the following output:
```
glxinfo
```

---

### Post by zingbats on 2008-04-01
```

name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
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
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_program, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_fragment_program, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texgen_reflection, GL_NV_texture_rectangle, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x23 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 None
0x24 16 tc  0 24  0 r  y  .  5  6  5  8  0 16  8 16 16 16 16  0 0 None
0x25 16 tc  0 24  0 r  .  .  5  6  5  8  0 16  8 16 16 16 16  0 0 None
0x3e 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

---

### Post by heavyt on 2008-04-01
I am also having the same problems with Nvidia GeFroce sense I did an update this morning. 8.04 was ok until this morning package update. Now I am stuck at 800x600. I have tried all the the tricks posted in this tread plus envy

---

### Post by zingbats on 2008-04-01
> **heavyt said:**
> I am also having the same problems with Nvidia GeFroce sense I did an update this morning. 8.04 was ok until this morning package update. Now I am stuck at 800x600. I have tried all the the tricks posted in this tread plus envy
dexconf ended up helping me get out of the rubbish 800*600

---

### Post by heavyt on 2008-04-01
> **zingbats said:**
> dexconf ended up helping me get out of the rubbish 800*600
thanks

---

### Post by zingbats on 2008-04-02
Bumping.

---

