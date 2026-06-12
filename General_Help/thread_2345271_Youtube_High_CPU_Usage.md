---
title: "Youtube High CPU Usage"
date: 2016-12-02
forum: General Help
---

### Post by gingabyte on 2016-12-02
I'm running Ubuntu 16.04 on the follow spec machine:

Intel i5 6500 CPU
8GB DDR4
1050ti - running nvidia drivers

The CPU usage when any youtube video is played in both chrome and opera hits 40 - 50% most of the time
Is this normal as it seems rather high for a newish machine?
Thanks

---

### Post by ajgreeny on 2016-12-02
Are you using flash or html5 to view the videos?

Both are fairly CPU intensive but flash is usually higher than html5, so go to [https://www.youtube.com/html5](https://www.youtube.com/html5) to check your settings and change them if necessary.

---

### Post by Yellow Pasque on 2016-12-02
First, make sure video accel works on your system in general:
```
sudo apt-get install vdpauinfo vainfo
vdpauinfo
vainfo
```

Also, can you look at chrome://gpu (within Chrome obviously)?

---

### Post by gingabyte on 2016-12-05
Youtube is running in HTML5

```
chris@chris-desktop:~$ vdpauinfo
display: :0   screen: 0
API version: 1
Information string: NVIDIA VDPAU Driver Shared Library  375.20  Tue Nov 15 16:42:40 PST 2016


Video surface:


name   width height types
-------------------------------------------
420     8192  8192  NV12 YV12 
422     8192  8192  UYVY YUYV 


Decoder capabilities:


name                        level macbs width height
----------------------------------------------------
MPEG1                           0 65536  4096  4096
MPEG2_SIMPLE                    3 65536  4096  4096
MPEG2_MAIN                      3 65536  4096  4096
H264_BASELINE                  41 65536  4096  4096
H264_MAIN                      41 65536  4096  4096
H264_HIGH                      41 65536  4096  4096
VC1_SIMPLE                      1  8190  2048  2048
VC1_MAIN                        2  8190  2048  2048
VC1_ADVANCED                    4  8190  2048  2048
MPEG4_PART2_SP                  3  8192  2048  2048
MPEG4_PART2_ASP                 5  8192  2048  2048
DIVX4_QMOBILE                   0  8192  2048  2048
DIVX4_MOBILE                    0  8192  2048  2048
DIVX4_HOME_THEATER              0  8192  2048  2048
DIVX4_HD_1080P                  0  8192  2048  2048
DIVX5_QMOBILE                   0  8192  2048  2048
DIVX5_MOBILE                    0  8192  2048  2048
DIVX5_HOME_THEATER              0  8192  2048  2048
DIVX5_HD_1080P                  0  8192  2048  2048
H264_CONSTRAINED_BASELINE      41 65536  4096  4096
H264_EXTENDED                  41 65536  4096  4096
H264_PROGRESSIVE_HIGH          41 65536  4096  4096
H264_CONSTRAINED_HIGH          41 65536  4096  4096
H264_HIGH_444_PREDICTIVE       41 65536  4096  4096
HEVC_MAIN                      153 262144  8192  8192
HEVC_MAIN_10                   --- not supported ---
HEVC_MAIN_STILL                --- not supported ---
HEVC_MAIN_12                   --- not supported ---
HEVC_MAIN_444                  --- not supported ---


Output surface:


name              width height nat types
----------------------------------------------------
B8G8R8A8         32768 32768    y  Y8U8V8A8 V8U8Y8A8 A4I4 I4A4 A8I8 I8A8 
R10G10B10A2      32768 32768    y  Y8U8V8A8 V8U8Y8A8 A4I4 I4A4 A8I8 I8A8 


Bitmap surface:


name              width height
------------------------------
B8G8R8A8         32768 32768
R8G8B8A8         32768 32768
R10G10B10A2      32768 32768
B10G10R10A2      32768 32768
A8               32768 32768


Video mixer:


feature name                    sup
------------------------------------
DEINTERLACE_TEMPORAL             y
DEINTERLACE_TEMPORAL_SPATIAL     y
INVERSE_TELECINE                 y
NOISE_REDUCTION                  y
SHARPNESS                        y
LUMA_KEY                         y
HIGH QUALITY SCALING - L1        y
HIGH QUALITY SCALING - L2        -
HIGH QUALITY SCALING - L3        -
HIGH QUALITY SCALING - L4        -
HIGH QUALITY SCALING - L5        -
HIGH QUALITY SCALING - L6        -
HIGH QUALITY SCALING - L7        -
HIGH QUALITY SCALING - L8        -
HIGH QUALITY SCALING - L9        -


parameter name                  sup      min      max
-----------------------------------------------------
VIDEO_SURFACE_WIDTH              y         1     8192
VIDEO_SURFACE_HEIGHT             y         1     8192
CHROMA_TYPE                      y  
LAYERS                           y         0        4


attribute name                  sup      min      max
-----------------------------------------------------
BACKGROUND_COLOR                 y  
CSC_MATRIX                       y  
NOISE_REDUCTION_LEVEL            y      0.00     1.00
SHARPNESS_LEVEL                  y     -1.00     1.00
LUMA_KEY_MIN_LUMA                y  
LUMA_KEY_MAX_LUMA                y  

```



```
chris@chris-desktop:~$ 

libva info: VA-API version 0.39.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/nvidia_drv_video.so
libva info: Found init function __vaDriverInit_0_39
libva info: va_openDriver() returns 0
vainfo: VA-API version: 0.39 (libva 1.7.0)
vainfo: Driver version: Splitted-Desktop Systems VDPAU backend for VA-API - 0.7.4
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :	VAEntrypointVLD
      VAProfileMPEG2Main              :	VAEntrypointVLD
      VAProfileMPEG4Simple            :	VAEntrypointVLD
      VAProfileMPEG4AdvancedSimple    :	VAEntrypointVLD
      VAProfileH264Baseline           :	VAEntrypointVLD
      VAProfileH264Main               :	VAEntrypointVLD
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileVC1Simple              :	VAEntrypointVLD
      VAProfileVC1Main                :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD

```
Thanks for your responses so far!

---

### Post by Yellow Pasque on 2016-12-05
The output in your previous post looks good as far as video decode accel being available on the system.

Can you give the output from chrome://gpu ?
Also, have you tried a different browser like Firefox? I know you said you used Opera, but it uses same Blink engine as Chrome.

---

### Post by gingabyte on 2016-12-05
```
Graphics Feature Status
Canvas: Hardware accelerated
Flash: Hardware accelerated
Flash Stage3D: Hardware accelerated
Flash Stage3D Baseline profile: Hardware accelerated
Compositing: Hardware accelerated
Multiple Raster Threads: Enabled
Native GpuMemoryBuffers: Software only. Hardware acceleration disabled
Rasterization: Software only. Hardware acceleration disabled
Video Decode: Software only, hardware acceleration unavailable
Video Encode: Hardware accelerated
VPx Video Decode: Software only, hardware acceleration unavailable
WebGL: Hardware accelerated
Driver Bug Workarounds
clear_uniforms_before_first_program_use
disable_discard_framebuffer
disable_framebuffer_cmaa
disable_transparent_visuals
force_cube_complete
init_gl_position_in_vertex_shader
init_vertex_attributes
pack_parameters_workaround_with_pack_buffer
scalarize_vec_and_mat_constructor_args
unpack_alignment_workaround_with_unpack_buffer
unpack_overlapping_rows_separately_unpack_buffer
use_current_program_after_successful_link
use_virtualized_gl_contexts
Problems Detected
Accelerated video decode is unavailable on Linux: 137247
Disabled Features: accelerated_video_decode
Always call glUseProgram after a successful link to avoid a driver bug: 349137
Applied Workarounds: use_current_program_after_successful_link
Program link fails in NVIDIA Linux if gl_Position is not set: 286468
Applied Workarounds: init_gl_position_in_vertex_shader
Clear uniforms before first program use on all platforms: 124764, 349137
Applied Workarounds: clear_uniforms_before_first_program_use
Linux NVIDIA drivers don't have the correct defaults for vertex attributes: 351528
Applied Workarounds: init_vertex_attributes
Always rewrite vec/mat constructors to be consistent: 398694
Applied Workarounds: scalarize_vec_and_mat_constructor_args
MakeCurrent is slow on Linux with NVIDIA drivers: 449150, 514510
Applied Workarounds: use_virtualized_gl_contexts
NVIDIA fails glReadPixels from incomplete cube map texture: 518889
Applied Workarounds: force_cube_complete
Pack parameters work incorrectly with pack buffer bound: 563714
Applied Workarounds: pack_parameters_workaround_with_pack_buffer
Alignment works incorrectly with unpack buffer bound: 563714
Applied Workarounds: unpack_alignment_workaround_with_unpack_buffer
Framebuffer discarding can hurt performance on non-tilers: 570897
Applied Workarounds: disable_discard_framebuffer
Unpacking overlapping rows from unpack buffers is unstable on NVIDIA GL driver: 596774
Applied Workarounds: unpack_overlapping_rows_separately_unpack_buffer
Limited enabling of Chromium GL_INTEL_framebuffer_CMAA: 535198
Applied Workarounds: disable_framebuffer_cmaa
Limit transparent visuals to drivers known to work: 369209
Applied Workarounds: disable_transparent_visuals
Accelerated rasterization has been disabled, either via blacklist, about:flags or the command line.
Disabled Features: rasterization
Native GpuMemoryBuffers have been disabled, either via about:flags or command line.
Disabled Features: native_gpu_memory_buffers
Version Information
Data exported	05/12/2016, 10:29:46
Chrome version	Chrome/54.0.2840.100
Operating system	Linux 4.4.0-51-generic
Software rendering list version	11.12
Driver bug list version	9.02
ANGLE commit id	905fbdea9ef0
2D graphics backend	Skia/54 a21f10dd8b19c6cb47d07d94d0a0525c16461969
Command Line Args	--wm-user-time-ms=55133204 --flag-switches-begin --flag-switches-end --disable_transparent_visuals --window-depth=24 --x11-visual-id=33
Driver Information
Initialization time	170
In-process GPU	false
Sandboxed	true
GPU0	VENDOR = 0x10de, DEVICE= 0x1c82
Optimus	false
AMD switchable	false
Driver vendor	NVIDIA
Driver version	375.20
Driver date	
Pixel shader version	4.50
Vertex shader version	4.50
Max. MSAA samples	32
Machine model name	
Machine model version	
GL_VENDOR	NVIDIA Corporation
GL_RENDERER	GeForce GTX 1050 Ti/PCIe/SSE2
GL_VERSION	4.5.0 NVIDIA 375.20
GL_EXTENSIONS	GL_AMD_multi_draw_indirect GL_AMD_seamless_cubemap_per_texture GL_AMD_vertex_shader_viewport_index GL_AMD_vertex_shader_layer GL_ARB_arrays_of_arrays GL_ARB_base_instance GL_ARB_bindless_texture GL_ARB_blend_func_extended GL_ARB_buffer_storage GL_ARB_clear_buffer_object GL_ARB_clear_texture GL_ARB_clip_control GL_ARB_color_buffer_float GL_ARB_compatibility GL_ARB_compressed_texture_pixel_storage GL_ARB_conservative_depth GL_ARB_compute_shader GL_ARB_compute_variable_group_size GL_ARB_conditional_render_inverted GL_ARB_copy_buffer GL_ARB_copy_image GL_ARB_cull_distance GL_ARB_debug_output GL_ARB_depth_buffer_float GL_ARB_depth_clamp GL_ARB_depth_texture GL_ARB_derivative_control GL_ARB_direct_state_access GL_ARB_draw_buffers GL_ARB_draw_buffers_blend GL_ARB_draw_indirect GL_ARB_draw_elements_base_vertex GL_ARB_draw_instanced GL_ARB_enhanced_layouts GL_ARB_ES2_compatibility GL_ARB_ES3_compatibility GL_ARB_ES3_1_compatibility GL_ARB_ES3_2_compatibility GL_ARB_explicit_attrib_location GL_ARB_explicit_uniform_location GL_ARB_fragment_coord_conventions GL_ARB_fragment_layer_viewport GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_fragment_shader_interlock GL_ARB_framebuffer_no_attachments GL_ARB_framebuffer_object GL_ARB_framebuffer_sRGB GL_ARB_geometry_shader4 GL_ARB_get_program_binary GL_ARB_get_texture_sub_image GL_ARB_gl_spirv GL_ARB_gpu_shader5 GL_ARB_gpu_shader_fp64 GL_ARB_gpu_shader_int64 GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_imaging GL_ARB_indirect_parameters GL_ARB_instanced_arrays GL_ARB_internalformat_query GL_ARB_internalformat_query2 GL_ARB_invalidate_subdata GL_ARB_map_buffer_alignment GL_ARB_map_buffer_range GL_ARB_multi_bind GL_ARB_multi_draw_indirect GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_occlusion_query2 GL_ARB_parallel_shader_compile GL_ARB_pipeline_statistics_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_post_depth_coverage GL_ARB_program_interface_query GL_ARB_provoking_vertex GL_ARB_query_buffer_object GL_ARB_robust_buffer_access_behavior GL_ARB_robustness GL_ARB_sample_locations GL_ARB_sample_shading GL_ARB_sampler_objects GL_ARB_seamless_cube_map GL_ARB_seamless_cubemap_per_texture GL_ARB_separate_shader_objects GL_ARB_shader_atomic_counter_ops GL_ARB_shader_atomic_counters GL_ARB_shader_ballot GL_ARB_shader_bit_encoding GL_ARB_shader_clock GL_ARB_shader_draw_parameters GL_ARB_shader_group_vote GL_ARB_shader_image_load_store GL_ARB_shader_image_size GL_ARB_shader_objects GL_ARB_shader_precision GL_ARB_shader_storage_buffer_object GL_ARB_shader_subroutine GL_ARB_shader_texture_image_samples GL_ARB_shader_texture_lod GL_ARB_shading_language_100 GL_ARB_shader_viewport_layer_array GL_ARB_shading_language_420pack GL_ARB_shading_language_include GL_ARB_shading_language_packing GL_ARB_shadow GL_ARB_sparse_buffer GL_ARB_sparse_texture GL_ARB_sparse_texture2 GL_ARB_sparse_texture_clamp GL_ARB_stencil_texturing GL_ARB_sync GL_ARB_tessellation_shader GL_ARB_texture_barrier GL_ARB_texture_border_clamp GL_ARB_texture_buffer_object GL_ARB_texture_buffer_object_rgb32 GL_ARB_texture_buffer_range GL_ARB_texture_compression GL_ARB_texture_compression_bptc GL_ARB_texture_compression_rgtc GL_ARB_texture_cube_map GL_ARB_texture_cube_map_array GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_filter_minmax GL_ARB_texture_float GL_ARB_texture_gather GL_ARB_texture_mirror_clamp_to_edge GL_ARB_texture_mirrored_repeat GL_ARB_texture_multisample GL_ARB_texture_non_power_of_two GL_ARB_texture_query_levels GL_ARB_texture_query_lod GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_texture_rgb10_a2ui GL_ARB_texture_stencil8 GL_ARB_texture_storage GL_ARB_texture_storage_multisample GL_ARB_texture_swizzle GL_ARB_texture_view GL_ARB_timer_query GL_ARB_transform_feedback2 GL_ARB_transform_feedback3 GL_ARB_transform_feedback_instanced GL_ARB_transform_feedback_overflow_query GL_ARB_transpose_matrix GL_ARB_uniform_buffer_object GL_ARB_vertex_array_bgra GL_ARB_vertex_array_object GL_ARB_vertex_attrib_64bit GL_ARB_vertex_attrib_binding GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_vertex_type_10f_11f_11f_rev GL_ARB_vertex_type_2_10_10_10_rev GL_ARB_viewport_array GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_bindable_uniform GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_direct_state_access GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXTX_framebuffer_mixed_formats GL_EXT_framebuffer_multisample_blit_scaled GL_EXT_framebuffer_object GL_EXT_framebuffer_sRGB GL_EXT_geometry_shader4 GL_EXT_gpu_program_parameters GL_EXT_gpu_shader4 GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_polygon_offset_clamp GL_EXT_post_depth_coverage GL_EXT_provoking_vertex GL_EXT_raster_multisample GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_shader_objects GL_EXT_separate_specular_color GL_EXT_shader_image_load_formatted GL_EXT_shader_image_load_store GL_EXT_shader_integer_mix GL_EXT_shadow_funcs GL_EXT_sparse_texture2 GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_array GL_EXT_texture_buffer_object GL_EXT_texture_compression_dxt1 GL_EXT_texture_compression_latc GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_filter_minmax GL_EXT_texture_integer GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_shared_exponent GL_EXT_texture_sRGB GL_EXT_texture_sRGB_decode GL_EXT_texture_storage GL_EXT_texture_swizzle GL_EXT_timer_query GL_EXT_transform_feedback2 GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_EXT_vertex_attrib_64bit GL_EXT_x11_sync_object GL_EXT_import_sync_object GL_NV_robustness_video_memory_purge GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KHR_context_flush_control GL_KHR_debug GL_KHR_no_error GL_KHR_robust_buffer_access_behavior GL_KHR_robustness GL_KTX_buffer_region GL_NV_alpha_to_coverage_dither_control GL_NV_bindless_multi_draw_indirect GL_NV_bindless_multi_draw_indirect_count GL_NV_bindless_texture GL_NV_blend_equation_advanced GL_NV_blend_equation_advanced_coherent GL_NVX_blend_equation_advanced_multi_draw_buffers GL_NV_blend_square GL_NV_clip_space_w_scaling GL_NV_command_list GL_NV_compute_program5 GL_NV_conditional_render GL_NV_conservative_raster GL_NV_conservative_raster_dilate GL_NV_conservative_raster_pre_snap_triangles GL_NV_copy_depth_to_color GL_NV_copy_image GL_NV_depth_buffer_float GL_NV_depth_clamp GL_NV_draw_texture GL_NV_draw_vulkan_image GL_NV_ES1_1_compatibility GL_NV_ES3_1_compatibility GL_NV_explicit_multisample GL_NV_fence GL_NV_fill_rectangle GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_coverage_to_color GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_fragment_shader_interlock GL_NV_framebuffer_mixed_samples GL_NV_framebuffer_multisample_coverage GL_NV_geometry_shader4 GL_NV_geometry_shader_passthrough GL_NV_gpu_program4 GL_NV_internalformat_sample_query GL_NV_gpu_program4_1 GL_NV_gpu_program5 GL_NV_gpu_program5_mem_extended GL_NV_gpu_program_fp64 GL_NV_gpu_shader5 GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_coverage GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_parameter_buffer_object GL_NV_parameter_buffer_object2 GL_NV_path_rendering GL_NV_path_rendering_shared_edge GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_sample_locations GL_NV_sample_mask_override_coverage GL_NV_shader_atomic_counters GL_NV_shader_atomic_float GL_NV_shader_atomic_float64 GL_NV_shader_atomic_fp16_vector GL_NV_shader_atomic_int64 GL_NV_shader_buffer_load GL_NV_shader_storage_buffer_object GL_NV_stereo_view_rendering GL_NV_texgen_reflection GL_NV_texture_barrier GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_multisample GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_transform_feedback GL_NV_transform_feedback2 GL_NV_uniform_buffer_unified_memory GL_NV_vdpau_interop GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_attrib_integer_64bit GL_NV_vertex_buffer_unified_memory GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NV_viewport_array2 GL_NV_viewport_swizzle GL_NVX_conditional_render GL_NVX_gpu_memory_info GL_NVX_nvenc_interop GL_NV_shader_thread_group GL_NV_shader_thread_shuffle GL_KHR_blend_equation_advanced GL_KHR_blend_equation_advanced_coherent GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum
Disabled Extensions	
Window system binding vendor	NVIDIA Corporation
Window system binding version	1.4
Window system binding extensions	GLX_EXT_visual_info GLX_EXT_visual_rating GLX_EXT_import_context GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGI_video_sync GLX_SGI_swap_control GLX_EXT_swap_control GLX_EXT_swap_control_tear GLX_EXT_texture_from_pixmap GLX_EXT_buffer_age GLX_ARB_create_context GLX_ARB_create_context_profile GLX_EXT_create_context_es_profile GLX_EXT_create_context_es2_profile GLX_ARB_create_context_robustness GLX_NV_delay_before_swap GLX_EXT_stereo_tree GLX_EXT_libglvnd GLX_ARB_context_flush_control GLX_NV_robustness_video_memory_purge GLX_ARB_multisample GLX_NV_float_buffer GLX_ARB_fbconfig_float GLX_EXT_framebuffer_sRGB GLX_NV_copy_image
Window manager	Compiz
XDG_CURRENT_DESKTOP	Unity
GDMSESSION	ubuntu
Compositing manager	Yes
Direct rendering	Yes
Reset notification strategy	0x8252
GPU process crash count	0
Compositor Information
Tile Update Mode	One-copy
Partial Raster	Enabled
GpuMemoryBuffers Status
ATC	Software only
ATCIA	Software only
DXT1	Software only
DXT5	Software only
ETC1	Software only
R_8	Software only
BGR_565	Software only
RGBA_4444	Software only
RGBX_8888	Software only
RGBA_8888	Software only
BGRX_8888	Software only
BGRA_8888	Software only
YVU_420	Software only
YUV_420_BIPLANAR	Software only
UYVY_422	Software only
```

---

### Post by Yellow Pasque on 2016-12-05
```
Video Decode: Software only, hardware acceleration unavailable
```

[http://www.phoronix.com/scan.php?page=news_item&px=MTYyMDk](http://www.phoronix.com/scan.php?page=news_item&px=MTYyMDk)

---

