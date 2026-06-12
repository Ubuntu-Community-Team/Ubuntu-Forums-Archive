---
title: "Hardy make troubles with Opengl Games!"
date: 2008-05-04
forum: General Help
---

### Post by killall-9 on 2008-05-04
Hello Grettings from Vienna!

After updgrade from Feisty 64 bit all my Linux Games startig to bucking when i turn fast around!I try with games like Ut2k4,Doom3 and Quakewars!
The crazy think is,when i play with "wine" "Prey" or "Mafia" there are no problems,works pretty fine!

what can i do?

---

### Post by markharding557 on 2008-05-04
can you explain what you mean by bucking

---

### Post by killall-9 on 2008-05-05
Hello!

Its like the Mouse cant handle fast turns so the mouse jump a little back, like a connection,laggy problem on Onlineserver.
I have try another Mouse ( i have here 2 mx518 from logitech),and i have testing with diffrent Nvidia Driver.Then i try with another Mouse driver,in xorg with lomoco and without it.
I dont know what else can i do :confused:

any ideas?

---

### Post by jtravnick on 2008-05-08
Well at least your able to get into the games. Did a fresh install of hardy and now I cant even get Doom3 to start. Crashes at start so can no longer play. Killer is that game is what made me switch over to ubuntu from fedora.

---

### Post by killall-9 on 2008-05-08
I found the error /fault.
When the resolution setting (dpi) of the  Mouse on Highest Level is,and Mouse movment in Games on low setting is,then the Games start to lagging by fast Turns.
Simple solution,turn down resolution (dpi)by Mouse and go upper in the game with Mouse setting.

Thx for Help

 
@ jtravnick 
what messages gives your terminal ?
what hardware yuo have?

---

### Post by jtravnick on 2008-05-13
killall-9 here is what im getting. I cant even get into the game. The game worked perfect in gutsy wasn't until I put hardy on that I had this problem with ubuntu, though it is the same problem I was having with fedora8 after one of there updates. I'm thinking it has something to do with pulse audio. As that is what cosed the problem in fedora and now ubuntu is running it. As of right now I am thinking about going back to gutsy as not realy all that impressed with hardy yet.


------- Input Initialization -------
XKB extension: compile time 0x1:0x0, runtime 0x1:0x0: OK
XKB extension present on server ( 0x1:0x0 )
------------------------------------
dlopen(libasound.so.2)
asoundlib version: 1.0.15
Alsa is available
------ Alsa Sound Initialization -----
opened Alsa PCM device default for playback
device buffer size: 5461 frames ( 21844 bytes )
allocated a mix buffer of 16384 bytes
--------------------------------------
...using GL_ARB_multitexture
...using GL_ARB_texture_env_combine
...using GL_ARB_texture_cube_map
...using GL_ARB_texture_env_dot3
...using GL_ARB_texture_env_add
X..GL_ARB_texture_non_power_of_two not found
...using GL_ARB_texture_compression
...using GL_EXT_texture_compression_s3tc
...using GL_EXT_texture_filter_anisotropic
   maxTextureAnisotropy: 8.000000
...using GL_1.4_texture_lod_bias
...using GL_EXT_shared_texture_palette
...using GL_EXT_texture3D
...using GL_EXT_stencil_wrap
...using GL_NV_register_combiners
...using GL_EXT_stencil_two_side
X..GL_ATI_fragment_shader not found
X..GL_ATI_text_fragment_shader not found
...using GL_ARB_vertex_buffer_object
...using GL_ARB_vertex_program
...using GL_ARB_fragment_program
X..EXT_depth_bounds_test not found
---------- R_NV20_Init ----------
---------------------------------
----------- R200_Init -----------
Not available.
---------- R_ARB2_Init ----------
Available.
---------------------------------
----- R_ReloadARBPrograms -----
glprogs/test.vfp
glprogs/test.vfp
glprogs/interaction.vfp
glprogs/interaction.vfp
glprogs/bumpyEnvironment.vfp
glprogs/bumpyEnvironment.vfp
glprogs/ambientLight.vfp
glprogs/ambientLight.vfp
glprogs/shadow.vp
glprogs/R200_interaction.vp
glprogs/nv20_bumpAndLight.vp
glprogs/nv20_diffuseColor.vp
glprogs/nv20_specularColor.vp
glprogs/nv20_diffuseAndSpecularColor.vp
glprogs/environment.vfp
glprogs/environment.vfp
glprogs/arbVP_glasswarp.txt: File not found
glprogs/arbFP_glasswarp.txt: File not found
-------------------------------
using ARB_vertex_buffer_object memory
signal caught: Illegal instruction
si_code 2
Trying to exit gracefully..
Shutting down sound hardware
----------- Alsa Shutdown ------------
close pcm
dlclose
--------------------------------------
idRenderSystem::Shutdown()
jim@jim-desktop:~$

---

### Post by Redscare on 2008-05-26
I had a similar problem, i suggest installing the latest 1.1 full version from the old section, i doubt that would change anything and at least the game works for me.

---

