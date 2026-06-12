---
title: "glxgears not functioning"
date: 2006-12-27
forum: General Help
---

### Post by malathia on 2006-12-27
I'm having a strange problem with glxgears.
I had initiated a fresh netboot install of ubuntu last night and had to go through the familiar
process of getting my savage video card up and running properly again. When I was going through some of the newest steps available, glxgears died right at the end.

Let me list some pertinent information

**Symptom:**

```
 :~$ glxgears
Killed

```

```
 :~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group,
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: S3 Graphics Inc.
OpenGL renderer string: Mesa DRI Savage/MX/IX 20050829 AGP 2x x86/MMX/SSE
OpenGL version string: 1.2 Mesa 6.5
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture,
    GL_ARB_texture_compression, GL_ARB_transpose_matrix, GL_ARB_window_pos,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_minmax,
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture,
    GL_EXT_draw_range_elements, GL_EXT_histogram, GL_EXT_packed_pixels,
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture,
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array,
    GL_APPLE_packed_pixels, GL_IBM_rasterpos_clip, GL_MESA_window_pos,
    GL_NV_light_max_exponent, GL_NV_texgen_reflection, GL_OES_read_format,
    GL_SGI_color_matrix, GL_SGI_color_table, GL_SGIS_texture_edge_clamp,
    GL_SGIS_texture_lod
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x23 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x24 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x25 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x26 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x27 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x28 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x29 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow

```

uname -r
2.6.15-27-686

Anyone have any ideas? 

I've tried rolling back savage drivers. I had newest when it happened, Tried rolling back to previous release, didn't change anything. Tried rolling back to 2.6.15-26, and that, with the rolled back drivers, but while booted into 2.6.15-26, found it to work, but only until I rebooted. Now, mind you, I thought I had fixed the issue by rolling back the savage drivers, Any attempts after the fact to make some sort of magic potion of rolled back this, new that, ad nauseum have not resulted in even a returned glimpse of an operational glxgears.

---

### Post by Shutdownrunner on 2006-12-27
Maybe you should check which drivers are being loaded at runtime and in what order.

Are you loading your chipset driver and so on?

---

### Post by malathia on 2006-12-30
Yeah, as far as I can tell, everything in that respect is fine.


```
(II) SAVAGE: driver (version 2.0.2) for S3 Savage chipsets: Savage4,
(**) SAVAGE(0): Depth 16, (--) framebuffer bpp 16
(==) SAVAGE(0): RGB weight 565
(==) SAVAGE(0): Default visual is TrueColor
(II) SAVAGE(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(**) SAVAGE(0): Option "AGPMode" "2"
(==) SAVAGE(0): Using HW cursor
(==) SAVAGE(0): Using video BIOS to set modes
(II) SAVAGE(0): initializing int10
(II) SAVAGE(0): Primary V_BIOS segment is: 0xc000
(II) SAVAGE(0): VESA BIOS detected
(II) SAVAGE(0): VESA VBE Version 2.0
(II) SAVAGE(0): VESA VBE Total Mem: 8192 kB
(II) SAVAGE(0): VESA VBE OEM: S3 Incorporated. M7 BIOS
(II) SAVAGE(0): VESA VBE OEM Software Rev: 1.0
(II) SAVAGE(0): VESA VBE OEM Vendor: S3 Incorporated.
(II) SAVAGE(0): VESA VBE OEM Product: VBE 2.0
(II) SAVAGE(0): VESA VBE OEM Product Rev: Rev 1.1
(--) SAVAGE(0): Chip: id 8c12, "Savage/IX-MV"
(--) SAVAGE(0): Engine: "MobileSavage"
(--) SAVAGE(0): AGP card detected
(==) SAVAGE(0): Using AGP DMA
(II) SAVAGE(0): Savage3D/MX/IX does not support command DMA.
(==) SAVAGE(0): Will try only vertex DMA mode
(**) SAVAGE(0): Using AGP 2x mode

```

What I've noticed is that when DRI enables, GLX breaks. So when I run in 1400x1050, glx works, I assume because it's using software rendering, as a result of DRI not being enabled. When I lower my resolution to 1280x1024, DRI enables, and glx auto kills.


still investigating.


*****************************SOLVED****************************

Solution to my personal problem was the addition of one thing to my xorg.conf
under my device section for my Savage vid card:

Option          "BusType"               "PCI"

After a reboot, everything worked as usual.

Quite pleased now.

---

