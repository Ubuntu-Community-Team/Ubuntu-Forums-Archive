---
title: "Screwy colors in OpenArena"
date: 2007-12-21
forum: General Help
---

### Post by Trinexx on 2007-12-21
Well, pretty much self explanatory, but I shall elaborate regardless! Whenever I launch OpenArena, the colors on my system go haywire. Like some newbie screwed with a color palette, if that analogy makes sense. Anyways, the colors are messed in OpenArena, along with everything else, until OpenArena is closed. Not sure if this will help, but here's the terminal output...

```

jacob@soloman:~$ openarena
ioQ3 1.33+oa linux-i386 Jul  5 2007
----- FS_Startup -----
Current search path:
/home/jacob/.openarena/baseoa
/usr/share/games/openarena/baseoa/pak6-misc.pk3 (96 files)
/usr/share/games/openarena/baseoa/pak5-TA.pk3 (7 files)
/usr/share/games/openarena/baseoa/pak4-textures.pk3 (932 files)
/usr/share/games/openarena/baseoa/pak2-players.pk3 (187 files)
/usr/share/games/openarena/baseoa/pak1-maps.pk3 (25 files)
/usr/share/games/openarena/baseoa/pak0.pk3 (748 files)
/usr/share/games/openarena/baseoa
/usr/lib/games/openarena/baseoa

----------------------
1995 files in pk3 files
execing default.cfg
execing q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----

------- Input Initialization -------
Joystick is not active.
------------------------------------
...loading libGL.so.1:
Calling SDL_Init(SDL_INIT_VIDEO)...
SDL_Init(SDL_INIT_VIDEO) passed.
Initializing OpenGL display
...setting mode 3: 640 480
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
Using 4/4/4 Color bits, 16 depth, 0 stencil display.
GL_RENDERER: Mesa DRI i810E 20050821 x86/MMX/SSE
*** IGNORING OPENGL EXTENSIONS ***

GL_VENDOR: Keith Whitwell
GL_RENDERER: Mesa DRI i810E 20050821 x86/MMX/SSE
GL_VERSION: 1.2 Mesa 7.0.1
GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_texture_compression GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_histogram GL_EXT_packed_pixels GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_APPLE_packed_pixels GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_rectangle GL_NV_texgen_reflection GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod
GL_MAX_TEXTURE_SIZE: 512
GL_MAX_ACTIVE_TEXTURES_ARB: 0

PIXELFORMAT: color(16-bits) Z(16-bit) stencil(0-bits)
MODE: 3, 640 x 480 windowed hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: multiple glArrayElement
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 16
multitexture: disabled
compiled vertex arrays: disabled
texenv add: disabled
compressed textures: disabled
Initializing Shaders
...loading 'scripts/player_gargoyle.shader'
...loading 'scripts/player_kyonshi.shader'
...loading 'scripts/player_major.shader'
...loading 'scripts/player_tux.shader'
...loading 'scripts/ammo.shader'
...loading 'scripts/beams.shader'
...loading 'scripts/ctf.shader'
...loading 'scripts/decals.shader'
...loading 'scripts/details.shader'
...loading 'scripts/detailtest.shader'
...loading 'scripts/evil8.shader'
...loading 'scripts/flaretest.shader'
...loading 'scripts/iconsprites.shader'
...loading 'scripts/item_health.shader'
...loading 'scripts/liquid_lavas.shader'
...loading 'scripts/liquid_water.shader'
...loading 'scripts/map_chpwatery2.shader'
...loading 'scripts/newmenu.shader'
...loading 'scripts/oactf.shader'
...loading 'scripts/oaflares.shader'
...loading 'scripts/oagfx.shader'
...loading 'scripts/oalite.shader'
...loading 'scripts/oanew.shader'
...loading 'scripts/oapowerups.shader'
...loading 'scripts/oasky.shader'
...loading 'scripts/oa_fogs.shader'
...loading 'scripts/oquartz.shader'
...loading 'scripts/q3map2_void3.shader'
...loading 'scripts/q3map2_void4.shader'
...loading 'scripts/qtex.shader'
...loading 'scripts/shells.shader'
...loading 'scripts/sky.shader'
...loading 'scripts/temporary.shader'
...loading 'scripts/weaponhits.shader'
...loading 'scripts/weaponry.shader'
...loading 'scripts/weapon_chaingun.shader'
...loading 'scripts/weapon_gauntlet.shader'
...loading 'scripts/weapon_grenadelauncher.shader'
...loading 'scripts/weapon_machinegun.shader'
...loading 'scripts/weapon_muzzles.shader'
...loading 'scripts/weapon_plasma.shader'
...loading 'scripts/weapon_railgun.shader'
...loading 'scripts/weapon_rocketlauncher.shader'
----- finished R_Init -----
------ Initializing Sound ------
Allocated 96 sources.
OpenAL info:
  Vendor:     OpenAL Community
  Version:    1.1
  Renderer:   Software
  Extensions: ALC_EXT_capture AL_EXT_capture AL_EXT_vorbis AL_EXT_MP3 AL_LOKI_quadriphonic AL_LOKI_play_position AL_LOKI_WAVE_format AL_LOKI_IMA_ADPCM_format AL_LOKI_buffer_data_callback ALC_LOKI_audio_channel 
Sound initialization successful.
--------------------------------
Loading vm file vm/ui.qvm...
VM file ui compiled to 585869 bytes of code
ui loaded in 1363392 bytes on the hunk
7 arenas parsed
3 arenas ignored to make count divisible by 4
6 bots parsed
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: soloman.dhcp.embarqhsd.net
Alias: soloman
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
Shutdown tty console
jacob@soloman:~$ 

```

Any ideas? Using an Intel 810e chipset, if that helps.


EDIT: Colors are screwed in Tremulous, too. >_<

---

### Post by Trinexx on 2007-12-21
ok, that's weird... I tried to take a screenshot with scrot, setting a delay of 60 seconds. The colors flashed normal for a fraction of a second, then went back to being corrupted. The screenshot, as I'm sure you figured out, was normal.

>_<

---

### Post by Trinexx on 2007-12-22
I take it that nobody has any solutions in mind. I found a workaround, but it kinda gimps the game. Oh well, a better solution has yet to present itself.

---

