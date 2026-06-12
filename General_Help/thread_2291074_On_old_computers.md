---
title: "On old computers"
date: 2015-08-17
forum: General Help
---

### Post by Jack the R on 2015-08-17
I've got an Asus R1E laptop with 4 gigs of ram.  A few years ago it was running Ubuntu 8.04 like a champ.  Unfortunately the internet moved on and some sites would no longer work with that era of Firefox.  Newer versions of FireFox wouldn't install on 8.04 because of dependency issues.  Currently I have it running a recent version of Lubuntu and it is barely functional, to non-functional.  The Lubuntu desktop is very slow, despite having less functionality than Ubuntu 8.04.  Firefox can't always load web pages.  It's not a problem with my internet connection.  My desktop machine loads pages fine, although after a few more years of "improvements" to Linux and the web, I suspect this 16 gig machine won't be able to run a desktop or browse the internet either.

Am I missing something?  What is going on in Lubuntu that makes it slower than Ubuntu 8.04?  Is there anything I can put on my R1E that will run as well as 8.04 did, and be able to surf the internet smoothly?

---

### Post by tgalati4 on 2015-08-17
Try the MATE desktop either in Linux Mint MATE or Ubuntu MATE.  I run Linux Mint MATE 17 (based on 14.04 LTS) on several older laptops and it runs well.  Understand that the browsers are doing more work and sandboxing/jailing tabs to protect the rest of the system and that apparently takes up a lot of RAM.

---

### Post by Bucky Ball on 2015-08-17
Hold on a minute. You are saying it has 4Gb of RAM or 16? Either would run Ubuntu fine, let alone Lubuntu or Mate, so the Firefox issue is separate if this is the case. Is it happening system wide of isolated to Firefox webpages loading?

PS: I just found [this]("http://www.tabletpcreview.com/tabletreview/asus-r1e-tablet-pc-user-review/") and these specs:

> The specifications of the reviewed machine (R1E-B1) are:

    Intel Core 2 Duo T7700 (2.4GHz, 4MB Cache, 800MHz bus)
    2GB DDR2 (2 x 1GB) Memory
    160GB 5400RPM SATA Hard Drive

That would run Lubuntu fine.

---

### Post by Jack the R on 2015-08-17
I used to be able to run Firefox, GIMP, Blender, and a few other things simultaneously on the R1E; and they all ran great together.  Is 2015 Firefox doing that much work?

---

### Post by Jack the R on 2015-08-17
> **Bucky Ball said:**
> Hold on a minute. You are saying it has 4Gb of RAM or 16? Either would run Ubuntu fine, let alone Lubuntu or Mate, so the Firefox issue is separate if this is the case. Is it happening system wide of isolated to Firefox webpages loading?

The R1E has 4 gigs, the desktop has 16 gigs.

The basic Lubuntu desktop is abysmally slow on the R1E, with 4 gigs of RAM.  

This seems totally wrong to me as well.

---

### Post by Bucky Ball on 2015-08-17
Yep, it is. That should be running fine, unless I'm overlooking something. Processor looks up to it. Perhaps a graphics issue? Run this and let's see what's there:

```
sudo lshw -C video
```

Have you tried Xubuntu or Ubuntu or Kubuntu and is it the same? Is it like this when you boot from the install media and 'Try Lubuntu'?

PS: The 16Gb machine would run anything *buntu you could throw at it. Or should.

---

### Post by Jack the R on 2015-08-17
> **Bucky Ball said:**
> Yep, it is. That should be running fine, unless I'm overlooking something. Processor looks up to it. Perhaps a graphics issue? Run this and let's see what's there:

```
sudo lshw -C video
```

```
 *-display:0             
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:48 memory:feb00000-febfffff memory:d0000000-dfffffff ioport:ec00(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:fe900000-fe9fffff
```


> **Bucky Ball said:**
> 
Have you tried Xubuntu or Ubuntu or Kubuntu and is it the same? Is it like this when you boot from the install media and 'Try Lubuntu'?

PS: The 16Gb machine would run anything *buntu you could throw at it. Or should.

I had Kubuntu 12.04 or 14.04 on it before switching to Lubuntu.  The speed was about the same.

Performance running off the DVD is pretty good.

---

### Post by Vladlenin5000 on 2015-08-17
Graphics is also more than enough so the problem is somewhere else.
I assume the HDD, albeit old, is still good otherwise you would have felt it before with 8.04. Nevertheless checking it is in order.

---

### Post by Jack the R on 2015-08-17
The hard drive is a barely used 5400 rpm unit.  It shouldn't be a problem, but I'll look at it.  What command do you want me to run?

Is that you in your sig or Christopher Hitchens?

---

### Post by kerry_s on 2015-08-17
with 4gig ram you should be able to run any ubuntu version.
i only have 2gb which is the max on my netbook & i'm running full ubuntu.

did you check the installer ?
what version did you install ? 14lts is the recommended

---

### Post by Jack the R on 2015-08-17
It has Lubuntu 14.04 LTS.

I ran it off the install disk earlier and it ran the way it was supposed to.

---

### Post by Bucky Ball on 2015-08-18
As I thought. I'm still looking at the driver or something to do with graphics. I notice you have two monitors. Shutdown, unplug one, reboot, same issue?

As it is running fine from the install media we can safely rule out faulty hardware, HDDs, RAM, screens, vid cards, etc. 

Just a hunch: tried unplugging one of the monitors then booting? Same? Doesn't fix anything but might shake out a clue ... or two. :)

Also, not sure if I've asked this, but have you checked in 'Additional Drivers'? I'm not sure if the driver you have installed is correct for the card.

---

### Post by Yellow Pasque on 2015-08-18
> **Bucky Ball said:**
> I notice you have two monitors. 
If you're referring to lshw output, it does not indicate two monitors connected.

> As it is running fine from the install media we can safely rule out faulty hardware
The install media isn't using the hard disk (except maybe if it uses its swap partition). I would at least check the SMART info.
Assuming drive is /dev/sda:
```
sudo apt-get install smartmontools
sudo smartctl -s on /dev/sda    #it may already be on
sudo smartctl -a -q noserial /dev/sda
```

> but have you checked in 'Additional Drivers'? I'm not sure if the driver you have installed is correct for the card. 
Ubuntu doesn't list the open-source Intel driver in that dialog IIRC. I really doubt the wrong GPU driver is used, but glxinfo should tell quickly:
```
glxinfo
```

---

### Post by Jack the R on 2015-08-18
There is a second monitor, but I don't think it's causing the problem.  It was plugged in when I ran from the install CD, and got good performance.  I will check all this stuff tomorrow.

---

### Post by Jack the R on 2015-08-18
Results from running SmartMonTools - 

```
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.16.0-37-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     SAMSUNG SpinPoint MP5
Device Model:     SAMSUNG HM500JJ
Firmware Version: 2AK10001
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    7200 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 6
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Tue Aug 18 14:36:45 2015 CDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		( 6420) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 ( 107) minutes.
SCT capabilities: 	       (0x003f)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   100   051    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0026   252   252   000    Old_age   Always       -       0
  3 Spin_Up_Time            0x0023   090   086   025    Pre-fail  Always       -       3235
  4 Start_Stop_Count        0x0032   096   096   000    Old_age   Always       -       4067
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   252   252   051    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0024   252   252   015    Old_age   Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       4821
 10 Spin_Retry_Count        0x0032   252   252   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       12
 12 Power_Cycle_Count       0x0032   096   096   000    Old_age   Always       -       4083
191 G-Sense_Error_Rate      0x0022   100   100   000    Old_age   Always       -       227
192 Power-Off_Retract_Count 0x0022   252   252   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0002   054   044   000    Old_age   Always       -       46 (Min/Max 16/59)
195 Hardware_ECC_Recovered  0x003a   100   100   000    Old_age   Always       -       0
196 Reallocated_Event_Count 0x0032   252   252   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   252   252   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   252   252   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0036   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x002a   100   100   000    Old_age   Always       -       0
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       12
225 Load_Cycle_Count        0x0032   099   099   000    Old_age   Always       -       12180

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


SMART Selective self-test log data structure revision number 0
Note: revision number not 1 implies that no selective self-test has ever been run
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Completed [00% left] (0-65535)
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
```


Results from glxinfo - 

```

name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_fbconfig_float, GLX_ARB_framebuffer_sRGB, GLX_ARB_multisample, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, GLX_SGI_swap_control
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_fbconfig_float, 
    GLX_ARB_framebuffer_sRGB, GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_buffer_age, GLX_EXT_create_context_es2_profile, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync
GLX version: 1.4
GLX extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_fbconfig_float, GLX_ARB_framebuffer_sRGB, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) 965GM 
OpenGL version string: 2.1 Mesa 10.3.2
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_3DFX_texture_compression_FXT1, GL_AMD_seamless_cubemap_per_texture, 
    GL_AMD_shader_trinary_minmax, GL_ANGLE_texture_compression_dxt3, 
    GL_ANGLE_texture_compression_dxt5, GL_APPLE_object_purgeable, 
    GL_APPLE_packed_pixels, GL_APPLE_vertex_array_object, 
    GL_ARB_ES2_compatibility, GL_ARB_buffer_storage, 
    GL_ARB_clear_buffer_object, GL_ARB_clear_texture, 
    GL_ARB_color_buffer_float, GL_ARB_compressed_texture_pixel_storage, 
    GL_ARB_copy_buffer, GL_ARB_copy_image, GL_ARB_debug_output, 
    GL_ARB_depth_buffer_float, GL_ARB_depth_clamp, GL_ARB_depth_texture, 
    GL_ARB_draw_buffers, GL_ARB_draw_elements_base_vertex, 
    GL_ARB_draw_instanced, GL_ARB_explicit_attrib_location, 
    GL_ARB_explicit_uniform_location, GL_ARB_fragment_coord_conventions, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_framebuffer_object, 
    GL_ARB_framebuffer_sRGB, GL_ARB_get_program_binary, 
    GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, 
    GL_ARB_instanced_arrays, GL_ARB_internalformat_query, 
    GL_ARB_invalidate_subdata, GL_ARB_map_buffer_alignment, 
    GL_ARB_map_buffer_range, GL_ARB_multi_bind, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_occlusion_query2, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_provoking_vertex, GL_ARB_robustness, GL_ARB_sampler_objects, 
    GL_ARB_seamless_cube_map, GL_ARB_seamless_cubemap_per_texture, 
    GL_ARB_separate_shader_objects, GL_ARB_shader_bit_encoding, 
    GL_ARB_shader_objects, GL_ARB_shader_texture_lod, 
    GL_ARB_shading_language_100, GL_ARB_shadow, GL_ARB_sync, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_mirror_clamp_to_edge, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_texture_rg, GL_ARB_texture_rgb10_a2ui, 
    GL_ARB_texture_storage, GL_ARB_texture_swizzle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_array_bgra, GL_ARB_vertex_array_object, 
    GL_ARB_vertex_attrib_binding, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_vertex_type_10f_11f_11f_rev, GL_ARB_vertex_type_2_10_10_10_rev, 
    GL_ARB_window_pos, GL_ATI_blend_equation_separate, GL_ATI_draw_buffers, 
    GL_ATI_separate_stencil, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_float, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_copy_texture, GL_EXT_draw_buffers2, GL_EXT_draw_instanced, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_object, GL_EXT_framebuffer_sRGB, 
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_float, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_provoking_vertex, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_array, GL_EXT_texture_compression_dxt1, 
    GL_EXT_texture_compression_rgtc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_integer, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_texture_sRGB, GL_EXT_texture_sRGB_decode, 
    GL_EXT_texture_shared_exponent, GL_EXT_texture_snorm, 
    GL_EXT_texture_swizzle, GL_EXT_vertex_array, GL_EXT_vertex_array_bgra, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, GL_KHR_debug, 
    GL_MESA_pack_invert, GL_MESA_texture_signed_rgba, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_conditional_render, GL_NV_depth_clamp, 
    GL_NV_light_max_exponent, GL_NV_packed_depth_stencil, 
    GL_NV_primitive_restart, GL_NV_texgen_reflection, 
    GL_NV_texture_env_combine4, GL_NV_texture_rectangle, GL_OES_EGL_image, 
    GL_OES_read_format, GL_S3_s3tc, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

12 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x020 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x021 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x074 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x075 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x076 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x077 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x078 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x079 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x07a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x07b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x07c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x05b 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None

24 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x05c  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x05d  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x05e  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x05f  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x060 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x061 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x062 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x063 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x064  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x065  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x066 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x067 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x068  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x069  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x06a  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x06b  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x06c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06d 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x06f 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x070  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x071  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x072 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x073 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
```

Unplugging the 2nd monitor and rebooting made no difference.

What is the command for viewing cpu resources used?  I'm assuming Lubuntu doesn't have Nepomuk, but could there be a similar buggy process slowing down the cpu?

---

### Post by Jack the R on 2015-08-19
Any ideas?

---

### Post by kurja on 2015-08-19
Maybe there's just something (!?) running that's eating up your cpu time. Do you see anything with high cpu% in ```
top
```? What does ```
uptime
``` this return?

---

### Post by Jack the R on 2015-08-19
Top isn't showing anything unusual.  With nothing else running, top takes up the most CPU resources, at 1%.  There are a few other things using .3%.  So much for the idea that it was a buggy process using up the CPU.

Here are the results for uptime - 

```
16:14:11 up  2:56,  3 users,  load average: 0.01, 0.03, 0.05
```

Why would there be 3 users?  Only one person has logged in.

Oddly enough, the R1E is running better since I booted it up from the install CD.  It's faster, and it boots up different.  I haven't replaced the cmos battery, so usually I have to hit f1 to get it to boot.  I don't have to do that now, it boots right up.  I did change the boot order in the BIOS so it could boot from the install CD.  Would that make a difference?

---

### Post by Jack the R on 2015-08-19
Here's something.  Weather.com pushes Firefox and xorg to a combination of 140% CPU usage.

---

### Post by kurja on 2015-08-20
> **Jack the R said:**
> 
Here are the results for uptime - 

```
16:14:11 up  2:56,  3 users,  load average: 0.01, 0.03, 0.05
```

Why would there be 3 users?  Only one person has logged in.


Here, your graphical desktop session is a 'user', and each terminal window is also a 'user'.

---

### Post by Jack the R on 2015-08-20
O.K., that makes sense.

---

### Post by Topsiho on 2015-08-20
what does

df -h

say? I mean, how much space do you have on your / partition for Lubuntu? I agree with the other posters that Lubuntu should run very well on your computer, so the problem must be the hardware, or lack of space (ever seen a (healthy) whale swimming in a bathtub?). Ubuntu 8.04 should not be used anymore, as it is now not maintained (no (security) updates).
[
Example, on my own desktop:

/dev/sda1           20G     6,8G   13G  36% /

which says that I have plenty of room on my / partition :), as only 36% of the available space is used

]

Topsiho

---

### Post by Jack the R on 2015-08-22
FWIW I've seen pcmnfm and udisk surge up to 90% cpu, temporarily. I recently saw a couple inits hit 20%, momentarily, but at the same time.

> **Topsiho said:**
> what does

df -h

say? 


Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       455G  3.3G  429G   1% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           389M  1.3M  387M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.9G     0  1.9G   0% /run/shm
none            100M   16K  100M   1% /run/user

---

### Post by claydoh on 2015-08-30
I would look at that hard drive a little more. I run two old Dell laptops, D630 and D830, with 2.0 core2duos, 4 gb ram, and the same Intel graphics you have. The 830 is my daily driver, and has an ssd, which makes a **huge** difference. I had an old 5400 rpm drive in the 630, and before I got the ram to 4gb, it would have a tendency to hit the swap very soon, making the slow drive churn and slow everything down. Even after the ram boost, it would still hit the swap all the time.

 [https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F](https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F)

Modifying the swappiness might help a bit, if you are accessing swap a lot - browsers and flash usually do it for me.

---

### Post by Jack the R on 2015-09-02
I changed the swappiness from 60 to 10.  I haven't noticed a big change.  I keep seeing cpu usage over 100% from Firefox, or combinations of Firefox/x.org,pcmanfm.

---

### Post by Jack the R on 2015-09-07
Any more ideas?

---

### Post by chemist931 on 2015-09-07
The poster above me is correct, that machine should be able to run any Ubuntu version out there.  I have a desktop that shipped in 2005, CPU with cache 8 times smaller than today's standard, 1 GB DDR2 RAM, gag-triggering video card, and it runs Ubuntu (slow, but it runs it faster than my 2015 laptop that runs Windows 10).

---

### Post by chemist931 on 2015-09-07
A solution for your Firefox problem: Wait for it...
(Beethoven's Fifth Symphony starts playing)
Chrome/Chromium.

---

### Post by Jack the R on 2015-09-08
Chromium does appear to be running faster than FireFox, although I'm seeing 140% cpu usage on startup.

---

### Post by sgage on 2015-09-08
> **Jack the R said:**
> Any more ideas?

If I were in your shoes, I would try a clean reinstall.

I am running Ubuntu Gnome on a 2008 vintage dual-core-Pentium 2 GHz with 4 GB RAM, no SSD, and it works just fine - quite snappy, in fact. I'd just start fresh, if I were you.

---

### Post by sgage on 2015-09-08
> **chemist931 said:**
> A solution for your Firefox problem: Wait for it...
(Beethoven's Fifth Symphony starts playing)
Chrome/Chromium.

Firefox works fine for me, and I see no benefit from Chrome/Chromium. The problem here isn't Firefox.

---

### Post by Jack the R on 2015-09-10
Chromium has been much faster than Firefox.

Lubuntu was the fresh install, after having the same problem with Kubuntu.  I'm hesitant to put time into another reinstall, unless it's not a version of Ubuntu.

---

### Post by @Tornado on 2015-09-10
I always put Lubuntu 14.04 LTS on those older computers that don't have any hope. Especially the laptops that the screen is about to fall off and the disk drive won't stay shut. :D

---

### Post by Jack the R on 2015-09-10
Well it's a tablet but how did you know the screen was falling off?  

This thing cost me $2000 new, hard to believe the hinge isn't serviceable.  It's not a front line soldier anymore, but other than the hinge it could still pull duty in the reserves.

---

