---
title: "OGRE EXCEPTION(7:InternalErrorException): Error decoding image in FreeImageCodec::dec"
date: 2013-07-16
forum: General Help
---

### Post by cwx133 on 2013-07-16
16:48:42: Creating resource group General
16:48:42: Creating resource group Internal
16:48:42: Creating resource group Autodetect
16:48:42: SceneManagerFactory for type 'DefaultSceneManager' registered.
16:48:42: Registering ResourceManager for type Material
16:48:42: Registering ResourceManager for type Mesh
16:48:42: Registering ResourceManager for type Skeleton
16:48:42: MovableObjectFactory for type 'ParticleSystem' registered.
16:48:42: OverlayElementFactory for type Panel registered.
16:48:42: OverlayElementFactory for type BorderPanel registered.
16:48:42: OverlayElementFactory for type TextArea registered.
16:48:42: Registering ResourceManager for type Font
16:48:42: ArchiveFactory for archive type FileSystem registered.
16:48:42: ArchiveFactory for archive type Zip registered.
16:48:42: DDS codec registering
16:48:42: FreeImage version: 3.15.1
16:48:42: This program uses FreeImage, a free, open source image library supporting all common bitmap formats. See [http://freeimage.sourceforge.net](http://freeimage.sourceforge.net) for details
16:48:42: Supported formats: bmp,ico,jpg,jif,jpeg,jpe,jng,koa,iff,lbm,mng,pbm,pbm,pcd,pcx,pgm,pgm,png,ppm,ppm,ras,tga,targa,tif,tiff,wap,wbmp,wbm,psd,cut,xbm,xpm,gif,hdr,g3,sgi,exr,j2k,j2c,jp2,pfm,pct,pict,pic,3fr,arw,bay,bmq,cap,cine,cr2,crw,cs1,dc2,dcr,drf,dsc,dng,erf,fff,ia,iiq,k25,kc2,kdc,mdc,mef,mos,mrw,nef,nrw,orf,pef,ptx,pxn,qtk,raf,raw,rdc,rw2,rwl,rwz,sr2,srf,sti
16:48:42: Registering ResourceManager for type HighLevelGpuProgram
16:48:42: Registering ResourceManager for type Compositor
16:48:42: MovableObjectFactory for type 'Entity' registered.
16:48:42: MovableObjectFactory for type 'Light' registered.
16:48:42: MovableObjectFactory for type 'BillboardSet' registered.
16:48:42: MovableObjectFactory for type 'ManualObject' registered.
16:48:42: MovableObjectFactory for type 'BillboardChain' registered.
16:48:42: MovableObjectFactory for type 'RibbonTrail' registered.
16:48:42: Loading library /usr/local/lib/RenderSystem_GL
16:48:42: Installing plugin: GL RenderSystem
16:48:42: OpenGL Rendering Subsystem created.
16:48:42: Plugin successfully installed
16:48:42: Loading library /usr/local/lib/Plugin_ParticleFX
16:48:42: Installing plugin: ParticleFX
16:48:42: Particle Emitter Type 'Point' registered
16:48:42: Particle Emitter Type 'Box' registered
16:48:42: Particle Emitter Type 'Ellipsoid' registered
16:48:42: Particle Emitter Type 'Cylinder' registered
16:48:42: Particle Emitter Type 'Ring' registered
16:48:42: Particle Emitter Type 'HollowEllipsoid' registered
16:48:42: Particle Affector Type 'LinearForce' registered
16:48:42: Particle Affector Type 'ColourFader' registered
16:48:42: Particle Affector Type 'ColourFader2' registered
16:48:42: Particle Affector Type 'ColourImage' registered
16:48:42: Particle Affector Type 'ColourInterpolator' registered
16:48:42: Particle Affector Type 'Scaler' registered
16:48:42: Particle Affector Type 'Rotator' registered
16:48:42: Particle Affector Type 'DirectionRandomiser' registered
16:48:42: Particle Affector Type 'DeflectorPlane' registered
16:48:42: Plugin successfully installed
16:48:42: Loading library /usr/local/lib/Plugin_CgProgramManager
16:48:43: Installing plugin: Cg Program Manager
16:48:43: Plugin successfully installed
16:48:43: Loading library /usr/local/lib/libParticleUniverse
16:48:43: Installing plugin: ParticleUniverse
16:48:43: MovableObjectFactory for type 'PUParticleSystem' registered.
16:48:43: MovableObjectFactory for type 'BoxSet' registered.
16:48:43: MovableObjectFactory for type 'SphereSet' registered.
16:48:43: ParticleUniverse: Particle Renderer Type 'Beam' registered
16:48:43: ParticleUniverse: Particle Renderer Type 'Billboard' registered
16:48:43: ParticleUniverse: Particle Renderer Type 'Box' registered
16:48:43: ParticleUniverse: Particle Renderer Type 'Sphere' registered
16:48:43: ParticleUniverse: Particle Renderer Type 'Entity' registered
16:48:43: ParticleUniverse: Particle Renderer Type 'RibbonTrail' registered
16:48:43: ParticleUniverse: Particle Renderer Type 'Light' registered
16:48:43: ParticleUniverse: Particle Emitter Type 'Point' registered
16:48:43: ParticleUniverse: Particle Emitter Type 'Line' registered
16:48:43: ParticleUniverse: Particle Emitter Type 'Box' registered
16:48:43: ParticleUniverse: Particle Emitter Type 'Circle' registered
16:48:43: ParticleUniverse: Particle Emitter Type 'SphereSurface' registered
16:48:43: ParticleUniverse: Particle Emitter Type 'Vertex' registered
16:48:43: ParticleUniverse: Particle Emitter Type 'MeshSurface' registered
16:48:43: ParticleUniverse: Particle Emitter Type 'Position' registered
16:48:43: ParticleUniverse: Particle Emitter Type 'Slave' registered
16:48:43: ParticleUniverse: Particle Affector Type 'Dummy01' registered
16:48:43: ParticleUniverse: Particle Affector Type 'LinearForce' registered
16:48:43: ParticleUniverse: Particle Affector Type 'Gravity' registered
16:48:43: ParticleUniverse: Particle Affector Type 'ParticleFollower' registered
16:48:43: ParticleUniverse: Particle Affector Type 'Vortex' registered
16:48:43: ParticleUniverse: Particle Affector Type 'Randomiser' registered
16:48:43: ParticleUniverse: Particle Affector Type 'Line' registered
16:48:43: ParticleUniverse: Particle Affector Type 'Scale' registered
16:48:43: ParticleUniverse: Particle Affector Type 'ScaleVelocity' registered
16:48:43: ParticleUniverse: Particle Affector Type 'GeometryRotator' registered
16:48:43: ParticleUniverse: Particle Affector Type 'TextureRotator' registered
16:48:43: ParticleUniverse: Particle Affector Type 'TextureAnimator' registered
16:48:43: ParticleUniverse: Particle Affector Type 'Jet' registered
16:48:43: ParticleUniverse: Particle Affector Type 'Align' registered
16:48:43: ParticleUniverse: Particle Affector Type 'FlockCentering' registered
16:48:43: ParticleUniverse: Particle Affector Type 'CollisionAvoidance' registered
16:48:43: ParticleUniverse: Particle Affector Type 'VelocityMatching' registered
16:48:43: ParticleUniverse: Particle Affector Type 'Colour' registered
16:48:43: ParticleUniverse: Particle Affector Type 'SineForce' registered
16:48:43: ParticleUniverse: Particle Affector Type 'Dummy02' registered
16:48:43: ParticleUniverse: Particle Affector Type 'SphereCollider' registered
16:48:43: ParticleUniverse: Particle Affector Type 'PlaneCollider' registered
16:48:43: ParticleUniverse: Particle Affector Type 'BoxCollider' registered
16:48:43: ParticleUniverse: Particle Affector Type 'InterParticleCollider' registered
16:48:43: ParticleUniverse: Particle Affector Type 'PathFollower' registered
16:48:43: ParticleUniverse: Particle Affector Type 'ForceField' registered
16:48:43: ParticleUniverse: Particle Observer Type 'OnExpire' registered
16:48:43: ParticleUniverse: Particle Observer Type 'OnEmission' registered
16:48:43: ParticleUniverse: Particle Observer Type 'OnCount' registered
16:48:43: ParticleUniverse: Particle Observer Type 'OnEventFlag' registered
16:48:43: ParticleUniverse: Particle Observer Type 'OnCollision' registered
16:48:43: ParticleUniverse: Particle Observer Type 'OnVelocity' registered
16:48:43: ParticleUniverse: Particle Observer Type 'OnTime' registered
16:48:43: ParticleUniverse: Particle Observer Type 'OnPosition' registered
16:48:43: ParticleUniverse: Particle Observer Type 'OnClear' registered
16:48:43: ParticleUniverse: Particle Observer Type 'OnQuota' registered
16:48:43: ParticleUniverse: Particle Observer Type 'OnRandom' registered
16:48:43: ParticleUniverse: Particle EventHandler Type 'DoExpire' registered
16:48:43: ParticleUniverse: Particle EventHandler Type 'DoFreeze' registered
16:48:43: ParticleUniverse: Particle EventHandler Type 'DoPlacementParticle' registered
16:48:43: ParticleUniverse: Particle EventHandler Type 'DoStopSystem' registered
16:48:43: ParticleUniverse: Particle EventHandler Type 'DoEnableComponent' registered
16:48:43: ParticleUniverse: Particle EventHandler Type 'DoAffector' registered
16:48:43: ParticleUniverse: Particle EventHandler Type 'DoScale' registered
16:48:43: ParticleUniverse: Particle Extern Type 'Gravity' registered
16:48:43: ParticleUniverse: Particle Extern Type 'SphereCollider' registered
16:48:43: ParticleUniverse: Particle Extern Type 'BoxCollider' registered
16:48:43: ParticleUniverse: Particle Extern Type 'Vortex' registered
16:48:43: ParticleUniverse: Particle Extern Type 'SceneDecorator' registered
16:48:43: ParticleUniverse: Particle Behaviour Type 'Slave' registered
16:48:43: Plugin successfully installed
16:48:43: *-*-* OGRE Initialising
16:48:43: *-*-* Version 1.7.2 (Cthugha)
16:48:43: Added resource location '../Media' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res.zip' of type 'Zip' to resource group 'General'
16:48:43: Added resource location '../Media/MyGUI_Media' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Layout' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/loading' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/Start' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/show' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/choose_game' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/choose_game/back' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/choose_game/titleback' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/choose_game/logo' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/choose_game/mesh' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/choose_game/choose' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/choose_game/choose/singleplayer' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/choose_game/choose/multipplayer' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/choose_game/multipplayer' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/choose_game/singleplayer' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/choose_car/icon/0' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/choose_car/icon/1' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/choose_car/icon/2' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/choose_car/icon/3' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/choose_car/icon/4' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/choose_car/icon/5' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/choose_car/view' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/choose_car' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/choose_car/carpros' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/choose_sence/icon/0' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/choose_sence/icon/1' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/choose_sence/icon/2' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/choose_sence/icon/3' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/choose_sence/icon/4' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/choose_sence/icon/5' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/choose_sence/view' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/choose_sence' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/choose_sence/sencepros' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/choose_road/light' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/choose_road/star' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/choose_road' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/choose_road/0' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/choose_road/1' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/end/end_stage' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/end/end_titel' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/end/end_item' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/end' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/gaming' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Res/sceneloading' of type 'FileSystem' to resource group 'General'
16:48:43: Added resource location '../Media/Common/Base' of type 'FileSystem' to resource group 'General'
16:48:43: CPU Identifier & Features
16:48:43: -------------------------
16:48:43:  *   CPU ID: AuthenticAMD: AMD Sempron(tm) 130 Processor
16:48:43:  *      SSE: yes
16:48:43:  *     SSE2: yes
16:48:43:  *     SSE3: yes
16:48:43:  *      MMX: yes
16:48:43:  *   MMXEXT: yes
16:48:43:  *    3DNOW: yes
16:48:43:  * 3DNOWEXT: yes
16:48:43:  *     CMOV: yes
16:48:43:  *      TSC: yes
16:48:43:  *      FPU: yes
16:48:43:  *      PRO: yes
16:48:43:  *       HT: no
16:48:43: -------------------------
16:48:43: ******************************
*** Starting GLX Subsystem ***
******************************
16:48:43: GLRenderSystem::_createRenderWindow "OGRE Render Window", 1280x720 windowed  miscParams: FSAA=0 displayFrequency=60 MHz gamma=No vsync=Yes 
16:48:43: OGRE EXCEPTION(6:FileNotFoundException): Cannot locate resource GLX_icon.png in resource group General or any other group. in ResourceGroupManager::openResource at /PlaneGame/ogre_src_v1-7-2/OgreMain/src/OgreResourceGroupManager.cpp (line 753)
16:48:43: GLXWindow::create used FBConfigID = 225
16:48:43: GL_VERSION = 2.1.2 NVIDIA 304.88
16:48:43: GL_VENDOR = NVIDIA Corporation
16:48:43: GL_RENDERER = GeForce 7025 / nForce 630a/integrated/SSE2/3DNOW!
16:48:43: GL_EXTENSIONS = GL_ARB_color_buffer_float GL_ARB_compressed_texture_pixel_storage GL_ARB_conservative_depth GL_ARB_copy_buffer GL_ARB_depth_clamp GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_ES2_compatibility GL_ARB_explicit_attrib_location GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_framebuffer_object GL_ARB_get_program_binary GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_imaging GL_ARB_internalformat_query GL_ARB_map_buffer_alignment GL_ARB_map_buffer_range GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_occlusion_query2 GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_provoking_vertex GL_ARB_robustness GL_ARB_sampler_objects GL_ARB_separate_shader_objects GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_shading_language_420pack GL_ARB_shading_language_include GL_ARB_shadow GL_ARB_sync GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_texture_storage GL_ARB_texture_swizzle GL_ARB_timer_query GL_ARB_transpose_matrix GL_ARB_vertex_array_bgra GL_ARB_vertex_array_object GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_direct_state_access GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_shader_objects GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_dxt1 GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_format_BGRA8888 GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_texture_sRGB_decode GL_EXT_texture_storage GL_EXT_texture_swizzle GL_EXT_timer_query GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_EXT_x11_sync_object GL_EXT_import_sync_object GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_alpha_test GL_NV_blend_minmax GL_NV_blend_square GL_NV_complex_primitives GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_ES1_1_compatibility GL_NV_fbo_color_attachments GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragdepth GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_framebuffer_multisample_coverage GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_barrier GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_lod_clamp GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_OES_compressed_paletted_texture GL_OES_depth24 GL_OES_depth32 GL_OES_depth_texture GL_OES_element_index_uint GL_OES_fbo_render_mipmap GL_OES_get_program_binary GL_OES_mapbuffer GL_OES_packed_depth_stencil GL_OES_point_size_array GL_OES_point_sprite GL_OES_rgb8_rgba8 GL_OES_read_format GL_OES_standard_derivatives GL_OES_texture_3D GL_OES_texture_float GL_OES_texture_float_linear GL_OES_texture_half_float GL_OES_texture_half_float_linear GL_OES_texture_npot GL_OES_vertex_array_object GL_OES_vertex_half_float GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 
16:48:43: Supported GLX extensions: GLX_EXT_visual_info GLX_EXT_visual_rating GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGI_video_sync GLX_SGI_swap_control GLX_EXT_swap_control GLX_EXT_swap_control_tear GLX_EXT_texture_from_pixmap GLX_ARB_create_context GLX_ARB_create_context_profile GLX_EXT_create_context_es2_profile GLX_ARB_create_context_robustness GLX_ARB_multisample GLX_NV_float_buffer GLX_ARB_fbconfig_float GLX_ARB_get_proc_address 
16:48:43: ***************************
16:48:43: *** GL Renderer Started ***
16:48:43: ***************************
16:48:43: Registering ResourceManager for type GpuProgram
16:48:43: GLSL support detected
16:48:43: GL: Using GL_EXT_framebuffer_object for rendering to textures (best)
16:48:43: FBO PF_UNKNOWN depth/stencil support: D16S0 D24S0 D32S0 Packed-D24S8 
16:48:43: FBO PF_R5G6B5 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
16:48:43: FBO PF_B5G6R5 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
16:48:43: FBO PF_R8G8B8 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
16:48:43: FBO PF_B8G8R8 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
16:48:43: FBO PF_A8R8G8B8 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
16:48:43: FBO PF_B8G8R8A8 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
16:48:43: FBO PF_A2R10G10B10 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
16:48:43: FBO PF_A2B10G10R10 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
16:48:43: FBO PF_FLOAT16_RGB depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
16:48:43: FBO PF_FLOAT16_RGBA depth/stencil support: D0S0 D16S0 
16:48:43: FBO PF_FLOAT32_RGB depth/stencil support: D0S0 D16S0 
16:48:43: FBO PF_FLOAT32_RGBA depth/stencil support: D0S0 D16S0 
16:48:43: FBO PF_X8R8G8B8 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
16:48:43: FBO PF_X8B8G8R8 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
16:48:43: FBO PF_SHORT_RGBA depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
16:48:43: FBO PF_R3G3B2 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
16:48:43: FBO PF_SHORT_RGB depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
16:48:43: [GL] : Valid FBO targets PF_UNKNOWN PF_R5G6B5 PF_B5G6R5 PF_R8G8B8 PF_B8G8R8 PF_A8R8G8B8 PF_B8G8R8A8 PF_A2R10G10B10 PF_A2B10G10R10 PF_FLOAT16_RGB PF_FLOAT16_RGBA PF_FLOAT32_RGB PF_FLOAT32_RGBA PF_X8R8G8B8 PF_X8B8G8R8 PF_SHORT_RGBA PF_R3G3B2 PF_SHORT_RGB 
16:48:43: RenderSystem capabilities
16:48:43: -------------------------
16:48:43: RenderSystem Name: OpenGL Rendering Subsystem
16:48:43: GPU Vendor: nvidia
16:48:43: Device Name: GeForce 7025 / nForce 630a/integrated/SSE2/3DNOW!
16:48:43: Driver Version: 2.1.2.0
16:48:43:  * Fixed function pipeline: yes
16:48:43:  * Hardware generation of mipmaps: yes
16:48:43:  * Texture blending: yes
16:48:43:  * Anisotropic texture filtering: yes
16:48:43:  * Dot product texture operation: yes
16:48:43:  * Cube mapping: yes
16:48:43:  * Hardware stencil buffer: yes
16:48:43:    - Stencil depth: 8
16:48:43:    - Two sided stencil support: yes
16:48:43:    - Wrap stencil values: yes
16:48:43:  * Hardware vertex / index buffers: yes
16:48:43:  * Vertex programs: yes
16:48:43:  * Number of floating-point constants for vertex programs: 256
16:48:43:  * Number of integer constants for vertex programs: 0
16:48:43:  * Number of boolean constants for vertex programs: 0
16:48:43:  * Fragment programs: yes
16:48:43:  * Number of floating-point constants for fragment programs: 512
16:48:43:  * Number of integer constants for fragment programs: 0
16:48:43:  * Number of boolean constants for fragment programs: 0
16:48:43:  * Geometry programs: no
16:48:43:  * Number of floating-point constants for geometry programs: 2425
16:48:43:  * Number of integer constants for geometry programs: 8676
16:48:43:  * Number of boolean constants for geometry programs: 2425
16:48:43:  * Supported Shader Profiles: arbfp1 arbvp1 fp20 fp30 fp40 glsl vp30 vp40
16:48:43:  * Texture Compression: yes
16:48:43:    - DXT: yes
16:48:43:    - VTC: yes
16:48:43:    - PVRTC: no
16:48:43:  * Scissor Rectangle: yes
16:48:43:  * Hardware Occlusion Query: yes
16:48:43:  * User clip planes: yes
16:48:43:  * VET_UBYTE4 vertex element type: yes
16:48:43:  * Infinite far plane projection: yes
16:48:43:  * Hardware render-to-texture: yes
16:48:43:  * Floating point textures: yes
16:48:43:  * Non-power-of-two textures: yes
16:48:43:  * Volume textures: yes
16:48:43:  * Multiple Render Targets: 4
16:48:43:    - With different bit depths: yes
16:48:43:  * Point Sprites: yes
16:48:43:  * Extended point parameters: yes
16:48:43:  * Max Point Size: 63.375
16:48:43:  * Vertex texture fetch: yes
16:48:43:  * Number of world matrices: 0
16:48:43:  * Number of texture units: 16
16:48:43:  * Stencil buffer depth: 8
16:48:43:  * Number of vertex blend matrices: 0
16:48:43:    - Max vertex textures: 4
16:48:43:    - Vertex textures shared: yes
16:48:43:  * Render to Vertex Buffer : no
16:48:43:  * GL 1.5 without VBO workaround: no
16:48:43:  * Frame Buffer objects: yes
16:48:43:  * Frame Buffer objects (ARB extension): no
16:48:43:  * Frame Buffer objects (ATI extension): no
16:48:43:  * PBuffer support: yes
16:48:43:  * GL 1.5 without HW-occlusion workaround: no
16:48:43: Registering ResourceManager for type Texture
16:48:43: DefaultWorkQueue('Root') initialising on thread main.
16:48:43: Particle Renderer Type 'billboard' registered
16:48:43: Parsing scripts for resource group Autodetect
16:48:43: Finished parsing scripts for resource group Autodetect
16:48:43: Parsing scripts for resource group General
16:48:44: Finished parsing scripts for resource group General
16:48:44: Parsing scripts for resource group Internal
16:48:44: Finished parsing scripts for resource group Internal
16:48:44: OGRE EXCEPTION(7:InternalErrorException): Error decoding image in FreeImageCodec::decode at /PlaneGame/ogre_src_v1-7-2/OgreMain/src/OgreFreeImageCodec.cpp (line 439)



help me ,

---

