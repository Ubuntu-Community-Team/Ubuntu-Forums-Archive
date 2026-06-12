---
title: "Kodi: Segmentation fault (core dumped)"
date: 2016-01-11
forum: General Help
---

### Post by Connor_Varney on 2016-01-11
Hello all,

Having a problem with my rooted Acer C720 Chromebook with Ubuntu precise installed alongside chromeos.


I recently installed XBMC, which ran perfectly with no problems. Today, I attempted to update to Kodi using [these]("http://www.htpcbeginner.com/upgrade-xbmc-to-kodi-media-center/") instructions, and I found Kodi will no longer start. When I try, I get the following error:


```
Segmentation fault (core dumped)
Crash report available at /home/connor/kodi_crashlog-20160112_100844.log
```
[FONT=arial]The full crash report:
[/FONT]```
[FONT=Verdana]############## Kodi CRASH LOG ###############[/FONT]
################ SYSTEM INFO ################
 Date: Tue Jan 12 09:59:50 NZDT 2016
 Kodi Options: 
 Arch: x86_64
 Kernel: Linux 3.8.11 #1 SMP Fri Dec 11 17:23:12 PST 2015
 Release: Ubuntu 12.04.5 LTS, Precise Pangolin
############## END SYSTEM INFO ##############

############### STACK TRACE #################
gdb not installed, can't get stack trace.
############# END STACK TRACE ###############

################# LOG FILE ##################

ï»¿09:59:49 T:140702035683200  NOTICE: special://profile/ is mapped to: special://masterprofile/
09:59:49 T:140702035683200  NOTICE: -----------------------------------------------------------------------
09:59:49 T:140702035683200  NOTICE: Starting Kodi (14.2 Git:7cc53a9). Platform: Linux x86 64-bit
09:59:49 T:140702035683200  NOTICE: Using Release Kodi x64 build
09:59:49 T:140702035683200  NOTICE: Kodi compiled Mar 27 2015 by GCC 4.6.3 for Linux x86 64-bit version 3.2.67 (197187)
09:59:49 T:140702035683200  NOTICE: Running on Ubuntu precise (12.04.5 LTS), kernel: Linux x86 64-bit version 3.8.11
09:59:49 T:140702035683200  NOTICE: FFmpeg statically linked, version: 2.4.6-xbmc-2.4.6-Helix
09:59:49 T:140702035683200  NOTICE: Host CPU: Intel(R) Celeron(R) 2955U @ 1.40GHz, 2 cores available
09:59:49 T:140702035683200  NOTICE: special://xbmc/ is mapped to: /usr/share/kodi
09:59:49 T:140702035683200  NOTICE: special://xbmcbin/ is mapped to: /usr/lib/kodi
09:59:49 T:140702035683200  NOTICE: special://masterprofile/ is mapped to: /home/connor/.kodi/userdata
09:59:49 T:140702035683200  NOTICE: special://home/ is mapped to: /home/connor/.kodi
09:59:49 T:140702035683200  NOTICE: special://temp/ is mapped to: /home/connor/.kodi/temp
09:59:49 T:140702035683200  NOTICE: The executable running is: /usr/lib/kodi/kodi.bin
09:59:49 T:140702035683200  NOTICE: Local hostname: chromebook
09:59:49 T:140702035683200  NOTICE: Log File is located: /home/connor/.kodi/temp/kodi.log
09:59:49 T:140702035683200  NOTICE: -----------------------------------------------------------------------
09:59:49 T:140702035683200  NOTICE: load settings...
09:59:49 T:140702035683200  NOTICE: Found 1 Lists of Devices
09:59:49 T:140702035683200  NOTICE: Enumerated PULSE devices:
09:59:49 T:140702035683200  NOTICE:     Device 1
09:59:49 T:140702035683200  NOTICE:         m_deviceName      : Default
09:59:49 T:140702035683200  NOTICE:         m_displayName     : Default
09:59:49 T:140702035683200  NOTICE:         m_displayNameExtra: Default Output Device (PULSEAUDIO)
09:59:49 T:140702035683200  NOTICE:         m_deviceType      : AE_DEVTYPE_PCM
09:59:49 T:140702035683200  NOTICE:         m_channels        : FL,FR
09:59:49 T:140702035683200  NOTICE:         m_sampleRates     : 5512,8000,11025,16000,22050,32000,44100,48000,64000,88200,96000,176400,192000,384000
09:59:49 T:140702035683200  NOTICE:         m_dataFormats     : AE_FMT_U8,AE_FMT_S16NE,AE_FMT_S24NE3,AE_FMT_S24NE4,AE_FMT_S32NE,AE_FMT_FLOAT
09:59:49 T:140702035683200  NOTICE:     Device 2
09:59:49 T:140702035683200  NOTICE:         m_deviceName      : cras-sink
09:59:49 T:140702035683200  NOTICE:         m_displayName     : cras
09:59:49 T:140702035683200  NOTICE:         m_displayNameExtra: cras (PULSEAUDIO)
09:59:49 T:140702035683200  NOTICE:         m_deviceType      : AE_DEVTYPE_PCM
09:59:49 T:140702035683200  NOTICE:         m_channels        : FL,FR
09:59:49 T:140702035683200  NOTICE:         m_sampleRates     : 5512,8000,11025,16000,22050,32000,44100,48000,64000,88200,96000,176400,192000,384000
09:59:49 T:140702035683200  NOTICE:         m_dataFormats     : AE_FMT_U8,AE_FMT_S16NE,AE_FMT_S24NE3,AE_FMT_S24NE4,AE_FMT_S32NE,AE_FMT_FLOAT
09:59:49 T:140702035683200  NOTICE: No settings file to load (special://xbmc/system/advancedsettings.xml)
09:59:49 T:140702035683200  NOTICE: No settings file to load (special://masterprofile/advancedsettings.xml)
09:59:49 T:140702035683200  NOTICE: Default DVD Player: dvdplayer
09:59:49 T:140702035683200  NOTICE: Default Video Player: dvdplayer
09:59:49 T:140702035683200  NOTICE: Default Audio Player: paplayer
09:59:49 T:140702035683200  NOTICE: Disabled debug logging due to GUI setting. Level 0.
09:59:49 T:140702035683200  NOTICE: Log level changed to "LOG_LEVEL_NORMAL"
09:59:49 T:140702035683200  NOTICE: CMediaSourceSettings: loading media sources from special://masterprofile/sources.xml
09:59:49 T:140702035683200  NOTICE: Loading player core factory settings from special://xbmc/system/playercorefactory.xml.
09:59:49 T:140702035683200  NOTICE: Loaded playercorefactory configuration
09:59:49 T:140702035683200  NOTICE: Loading player core factory settings from special://masterprofile/playercorefactory.xml.
09:59:49 T:140702035683200  NOTICE: special://masterprofile/playercorefactory.xml does not exist. Skipping.
09:59:49 T:140701704607488  NOTICE: Thread ActiveAE start, auto delete: false
09:59:49 T:140701771720448  NOTICE: Thread AESink start, auto delete: false
09:59:49 T:140701771720448  NOTICE: PulseAudio: Opened device Default in pcm mode with Buffersize 180 ms
09:59:49 T:140702035683200  NOTICE: Running database version Addons16
09:59:49 T:140702035683200  NOTICE: ADDONS: Using repository repository.xbmc.org
09:59:49 T:140702035683200  NOTICE: ADDONS: Using repository repository.dextertv
09:59:49 T:140701745731328  NOTICE: Thread PeripBusCEC start, auto delete: false
09:59:49 T:140701737338624  NOTICE: Thread PeripBusUSBUdev start, auto delete: false
09:59:49 T:140702035683200  NOTICE: Setup SDL
09:59:49 T:140702035683200  NOTICE: Checking resolution 16
09:59:49 T:140702035683200  NOTICE: Using visual 0x148
09:59:49 T:140702035683200  NOTICE: GL_VENDOR = VMware, Inc.
09:59:49 T:140702035683200  NOTICE: GL_RENDERER = Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits)
09:59:49 T:140702035683200  NOTICE: GL_VERSION = 2.1 Mesa 10.1.3
09:59:49 T:140702035683200  NOTICE: GL_SHADING_LANGUAGE_VERSION = 1.30
09:59:49 T:140702035683200  NOTICE: GL_EXTENSIONS = GL_ARB_multisample GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_copy_texture GL_EXT_polygon_offset GL_EXT_subtexture GL_EXT_texture_object GL_EXT_vertex_array GL_EXT_compiled_vertex_array GL_EXT_texture GL_EXT_texture3D GL_IBM_rasterpos_clip GL_ARB_point_parameters GL_EXT_draw_range_elements GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_separate_specular_color GL_EXT_texture_edge_clamp GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_ARB_framebuffer_sRGB GL_ARB_multitexture GL_EXT_framebuffer_sRGB GL_IBM_multimode_draw_arrays GL_IBM_texture_mirrored_repeat GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_transpose_matrix GL_EXT_blend_func_separate GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_secondary_color GL_EXT_texture_env_add GL_EXT_texture_lod_bias GL_INGR_blend_func_separate GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_SUN_multi_draw_arrays GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_EXT_framebuffer_object GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_MESA_window_pos GL_NV_packed_depth_stencil GL_NV_texture_rectangle GL_ARB_depth_texture GL_ARB_occlusion_query GL_ARB_shadow GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_EXT_stencil_two_side GL_EXT_texture_cube_map GL_NV_depth_clamp GL_NV_fog_distance GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_shader GL_ARB_shader_objects GL_ARB_vertex_program GL_ARB_vertex_shader GL_ATI_draw_buffers GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_NV_primitive_restart GL_ARB_depth_clamp GL_ARB_fragment_program_shadow GL_ARB_half_float_pixel GL_ARB_occlusion_query2 GL_ARB_point_sprite GL_ARB_shading_language_100 GL_ARB_sync GL_ARB_texture_non_power_of_two GL_ARB_vertex_buffer_object GL_ATI_blend_equation_separate GL_EXT_blend_equation_separate GL_OES_read_format GL_ARB_color_buffer_float GL_ARB_pixel_buffer_object GL_ARB_texture_compression_rgtc GL_ARB_texture_float GL_ARB_texture_rectangle GL_ATI_texture_compression_3dc GL_EXT_packed_float GL_EXT_pixel_buffer_object GL_EXT_texture_compression_rgtc GL_EXT_texture_mirror_clamp GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_texture_shared_exponent GL_ARB_framebuffer_object GL_EXT_framebuffer_blit GL_EXT_packed_depth_stencil GL_ARB_vertex_array_object GL_ATI_separate_stencil GL_ATI_texture_mirror_once GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_gpu_program_parameters GL_EXT_texture_array GL_EXT_texture_compression_latc GL_EXT_texture_integer GL_EXT_texture_sRGB_decode GL_EXT_timer_query GL_OES_EGL_image GL_ARB_copy_buffer GL_ARB_depth_buffer_float GL_ARB_draw_instanced GL_ARB_half_float_vertex GL_ARB_instanced_arrays GL_ARB_map_buffer_range GL_ARB_texture_rg GL_ARB_texture_swizzle GL_ARB_vertex_array_bgra GL_EXT_texture_swizzle GL_EXT_vertex_array_bgra GL_NV_conditional_render GL_AMD_conservative_depth GL_AMD_draw_buffers_blend GL_AMD_seamless_cubemap_per_texture GL_ARB_ES2_compatibility GL_ARB_blend_func_extended GL_ARB_debug_output GL_ARB_draw_buffers_blend GL_ARB_draw_elements_base_vertex GL_ARB_explicit_attrib_location GL_ARB_fragment_coord_conventions GL_ARB_provoking_vertex GL_ARB_sampler_objects GL_ARB_seamless_cube_map GL_ARB_shader_texture_lod GL_ARB_texture_rgb10_a2ui GL_ARB_uniform_buffer_object GL_ARB_vertex_type_2_10_10_10_rev GL_EXT_provoking_vertex GL_EXT_texture_snorm GL_MESA_texture_signed_rgba GL_ARB_get_program_binary GL_ARB_robustness GL_ARB_shader_bit_encoding GL_ARB_timer_query GL_ARB_transform_feedback2 GL_ARB_transform_feedback3 GL_NV_vdpau_interop GL_ARB_conservative_depth GL_ARB_internalformat_query GL_ARB_map_buffer_alignment GL_ARB_shading_language_420pack GL_ARB_shading_language_packing GL_ARB_texture_storage GL_ARB_transform_feedback_instanced GL_EXT_transform_feedback GL_AMD_shader_trinary_minmax GL_ARB_clear_buffer_object GL_ARB_invalidate_subdata GL_ARB_vertex_attrib_binding GL_KHR_debug GL_ARB_texture_mirror_clamp_to_edge GL_ARB_vertex_type_10f_11f_11f_rev
09:59:49 T:140702035683200  NOTICE: Running database version Addons16
09:59:49 T:140702035683200  NOTICE: Running database version ViewModes6
09:59:49 T:140702035683200  NOTICE: Running database version Textures13
09:59:49 T:140702035683200  NOTICE: Running database version MyMusic48
09:59:49 T:140702035683200  NOTICE: Running database version MyVideos90
09:59:49 T:140702035683200  NOTICE: Running database version TV26
09:59:49 T:140702035683200  NOTICE: Running database version Epg8
09:59:49 T:140702035683200  NOTICE: start dvd mediatype detection
09:59:49 T:140702034065152  NOTICE: Thread DetectDVDMedia start, auto delete: false
09:59:49 T:140702035683200 WARNING: JSONRPC: Could not parse type "PVR.Details.Channel"
09:59:49 T:140702035683200 WARNING: JSONRPC: Could not parse type "PVR.Details.ChannelGroup.Extended"
09:59:49 T:140702035683200 WARNING: JSONRPC: Could not parse type "GUI.Property.Value"
09:59:49 T:140702035683200 WARNING: JSONRPC: Could not parse type "Setting.Details.SettingList"
09:59:49 T:140702035683200  NOTICE: initialize done
09:59:49 T:140701350926080  NOTICE: Thread LanguageInvoker start, auto delete: false
09:59:49 T:140701350926080  NOTICE: -->Python Interpreter Initialized<--
09:59:50 T:140701325936384  NOTICE: Thread JobWorker start, auto delete: true
09:59:50 T:140702035683200  NOTICE: starting zeroconf publishing
09:59:50 T:140702035683200  NOTICE: ES: Starting event server
09:59:50 T:140700955952896  NOTICE: Thread TCPServer start, auto delete: false
09:59:50 T:140700964345600  NOTICE: Thread EventServer start, auto delete: false
09:59:50 T:140700964345600  NOTICE: ES: Starting UDP Event server on 0.0.0.0:9777
09:59:50 T:140700964345600  NOTICE: UDP: Listening on port 9777
09:59:50 T:140702034065152  NOTICE: Thread RSSReader start, auto delete: false
09:59:50 T:140700972738304  NOTICE: Thread JobWorker start, auto delete: true


############### END LOG FILE ################

[FONT=arial][FONT=Verdana]############ END Kodi CRASH LOG #############[/FONT][/FONT]
```[FONT=arial]
[/FONT][FONT=arial]
[/FONT][FONT=arial]Thanks for any help,[/FONT][FONT=arial]
[/FONT][FONT=arial]Connor[/FONT][FONT=arial]
[/FONT]

---

