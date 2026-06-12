---
title: "Slowness on my laptop"
date: 2007-05-29
forum: General Help
---

### Post by synthetic_fenix on 2007-05-29
The laptop i have is a Dell Latitude 100L
Specs:

CPU = 2.8Ghz Pentium4 Mobile
Memory = 1Gb of PC2700 DDR memory
Graphics = Intel Graphics Extreme 855 Series
Wireless = Intel A/B/G Wireless (native linux drivers)
Hard drive = 60Gb Hitachi 7200RPM pata drive
Version of ubuntu = 7.04 Feisty Fawn



Problems I am having, Things just seem to run a lot slower then they really should. Mozilla uses 100% CPU when doing almost anything. I can't run games like starcraft in Wine, just runs too slow and its really choppy. over all things are just really sluggish and I'm wondering if it has to do with the generic kernel or what.

---

### Post by Crafty Kisses on 2007-05-29
Go into terminal and type:
```
top
```
Copy and paste the log.

---

### Post by synthetic_fenix on 2007-05-30
From when do you want the top log? when sitting idle or when doing something?

---

### Post by Crafty Kisses on 2007-05-30
> **synthetic_fenix said:**
> From when do you want the top log? when sitting idle or when doing something?

When you're doing something. :p Usually there is always a process that uses a lot of resources, so just post the log and you should see the program that's eating up all the resources.

---

### Post by synthetic_fenix on 2007-05-31
attached i have top-idle.txt which is my laptop sitting idle and then the other is top-firefox.txt which is when firefox is just starting up but even when nothing is running my laptop just "feels" slow.

---

### Post by synthetic_fenix on 2007-06-01
Ok I compared my running install of Feisty on my laptop to an install on my friend's Acer that is running a Turon 64  x2 with only 512Mb of ram and a slower hard drive. Firefox opened twice as fast on his laptop then on mine and didnt hit full cpu utilization on the system monitor, where mine almost fills the graph up in full blue when i open up firefox or anything. Even when firefox is loaded and i got scroll a webpage it uses the CPU alot. Its also not just Firefox, Like I said above with my system specs I should be able to play starcraft with no problems in wine and its not playable. Evolution mail practically kill my system performance when its up and running. DVDs play really choppy in totem. I am almost at the end of my patience with this and am thinking of putting XP back on it and runing linux from VMware, atleast there I know whey my performance is a little degraded.

---

### Post by bmartin on 2007-06-01
Try disabling the power management. That caused a lot of problems w/ my laptop.

There's a service called **powernowd** that starts up with your computer. Try disabling it:
```
sudo /etc/rc5.d/S20powernowd stop
```

---

### Post by synthetic_fenix on 2007-06-01
I actually have that disabled from starting up.

---

### Post by synthetic_fenix on 2007-06-02
any other ideas? I went through and turned off all the powernowd stuff from starting up.

---

### Post by jjacobs2 on 2007-06-02
I think there might be something wrong with your graphics driver.  Xorg was taking up a quarter of the processor power while firefox was opening.  What kind of result do you get with glxgears?  Put glxgears -info into a terminal and see what you get.  I don't know that much about intel graphics but I think the drivers are supposed to be open source.

---

### Post by synthetic_fenix on 2007-06-02
ok here is the out put of glxgear -info and also what came up in Top when glxgears was running. Should I try the Intel drivers even though they are from 2004?

```
GL_RENDERER   = Mesa DRI Intel(R) 852GM/855GM 20061017 x86/MMX/SSE2
GL_VERSION    = 1.3 Mesa 6.5.2
GL_VENDOR     = Tungsten Graphics, Inc
GL_EXTENSIONS = GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_point_parameters
GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add
GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat
GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos
GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate
GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_cull_vertex GL_EXT_compiled_vertex_array
GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_histogram
GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal
GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture
GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3
GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle
GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_packed_pixels
GL_ATI_blend_equation_separate GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate
GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent
GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format
GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp
GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays
2519 frames in 5.0 seconds = 503.753 FPS
1761 frames in 5.0 seconds = 352.118 FPS
1975 frames in 5.0 seconds = 394.841 FP
```







```
top - 17:06:46 up 3 min,  3 users,  load average: 1.89, 1.43, 0.60
Tasks: 106 total,   2 running, 104 sleeping,   0 stopped,   0 zombie
Cpu(s): 33.3%us, 30.4%sy,  0.0%ni, 19.8%id,  0.0%wa, 16.2%hi,  0.3%si,  0.0%st
Mem:   1034592k total,   478664k used,   555928k free,    11208k buffers
Swap:  2441840k total,        0k used,  2441840k free,   274008k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 5654 crolves   16   0 90880 5532 1468 R 75.5  0.5   0:14.90 glxgears
 5504 crolves   15   0 19116 6612 5604 S  1.3  0.6   0:01.12 multiload-apple
 4806 root      15   0  210m  11m 6804 S  1.0  1.1   0:05.89 Xorg
 5655 crolves   15   0  2316 1092  848 R  1.0  0.1   0:00.20 top
 4903 cupsys    18   0  4688 1912 1416 S  0.3  0.2   0:00.20 cupsd
 5391 crolves   15   0 50812 9876 8164 S  0.3  1.0   0:00.53 nm-applet
    1 root      18   0  2908 1824  504 S  0.0  0.2   0:03.44 init
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 events/0
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 khelper
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 kthread
   30 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0
   31 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
   32 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify
  129 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod

```

---

### Post by synthetic_fenix on 2007-06-05
Ok so I ended up installing Windows back on the machine and I was still having problems with the system running really slow. I finally dug into it and found out that someone had disabled intel speedstep in the bios. Turned that back on and everything was nice and quick in windows. Will be re-installing feisty back on it to dualboot for a whiel tomorrow.

---

### Post by synthetic_fenix on 2007-06-06
OK great news! the intel speedstep being disabled was exactly the problem. My laptop is much more responsive now and doesn't have near the CPU load as it had before. now I must ask does 750 to 800 FPS in GLXgears sound about right for the video in my laptop?

---

