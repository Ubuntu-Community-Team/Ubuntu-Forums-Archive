---
title: "Graphics Card question"
date: 2015-01-06
forum: General Help
---

### Post by michael-piziak on 2015-01-06
I suppose I have a generic Intel graphics card.  This is what I get in terminal
```

michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82Q33 Express Integrated Graphics Controller (rev 02)
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ sudo lshw -C video
[sudo] password for michael: 
  *-display               
       description: VGA compatible controller
       product: 82Q33 Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:f0100000-f017ffff ioport:1240(size=8) memory:e0000000-efffffff memory:f0000000-f00fffff
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$
```

I was trying to figure out if my system is "OpenGL" or "Xvideo" as some emulators have that option.  In PCSX emulator it runs under OpenGL just fine.  However, in Snes9x emualtor OpenGL option makes the game jittery and Xvideo option makes the graphics fuzzy.

---

### Post by papibe on 2015-01-06
Hi michael-piziak.

OpenGL library can be installed regardless of the compatibility. If the hardware supports it, it would do hardware acceleration. If not, it would be emulated by software.

To check if the hardware supports acceleration run this:
```
glxinfo | grep render
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by michael-piziak on 2015-01-06
I typed it into terminal and I get:

michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ glxinfo | grep render
The program 'glxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install mesa-utils
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$


UPDATE:  I installed glxinfo (more specifically I installed mesa-utils from software center) and get this now:

michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ glxinfo | grep render
direct rendering: Yes
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
OpenGL renderer string: Mesa DRI Intel(R) Q33 
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$

Simply by doing this did I enable OpenGL ?  Or does this simply tell me I have OpenGL ?

---

### Post by papibe on 2015-01-06
Good news:

OpenGL is installed, and running properly.

You could run a graphic test to check performance if you want:
```
glxgears
```
Let us run for a few seconds so you can see the frames per seconds (displayed in the terminal).

Bad news:
```
OpenGL renderer string: Mesa DRI Intel(R) Q33 
```
It is not accelerated by hardware, but by software.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by michael-piziak on 2015-01-06
Well it would be nice to have hardware (graphics card) run it, but I guess my system doesn't have any fancy graphic card installed.

Here's the result of the command:

michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
304 frames in 5.0 seconds = 60.754 FPS
301 frames in 5.0 seconds = 60.000 FPS
301 frames in 5.0 seconds = 60.000 FPS
300 frames in 5.0 seconds = 60.000 FPS
301 frames in 5.0 seconds = 60.000 FPS
300 frames in 5.0 seconds = 60.000 FPS
301 frames in 5.0 seconds = 60.000 FPS

---

### Post by papibe on 2015-01-06
Actually, that's pretty good. That's makes me doubt my previous statement.

Let's check a couple of things:

Could you run these too?
```
/usr/lib/nux/unity_support_test -p

glxinfo | grep -i opengl
```
Regards.

---

### Post by michael-piziak on 2015-01-07
ok, I ran those two commands.  

michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Q33 
OpenGL version string:  1.4 Mesa 10.1.3


Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes


Unity 3D supported:       yes
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ glxinfo | grep -i opengl
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Q33 
OpenGL version string: 1.4 Mesa 10.1.3
OpenGL extensions:
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ 

What does that tell us about my system.

---

### Post by DiogoSaraiva on 2015-01-07
Hi everyone...
Hi have a similar issue, can you help me?

Hi have various emulators installed but the PCSX one don't run well...
I think because it's more "heavy" games,, maybe, or A GRAPHICS CARD PROBLEM/QUESTION...
if is a graphical cards problem... can you help me to solve that....

```

[FONT=Menlo][COLOR=#34bd26]**diogosaraiva@Ubuntu**[/COLOR]:[COLOR=#5330e1]**~**[/COLOR]$ lspci | grep VGA[/FONT]
[FONT=Menlo]00:01.0 [COLOR=#c33720]**VGA**[/COLOR] compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler [Radeon HD 6320][/FONT]
[FONT=Menlo][COLOR=#34bd26]**diogosaraiva@Ubuntu**[/COLOR]:[COLOR=#5330e1]**~**[/COLOR]$ sudo lshw -C video[/FONT]
[FONT=Menlo]  *-display               [/FONT]
[FONT=Menlo]       descrição: VGA compatible controller[/FONT]
[FONT=Menlo]       produto: Wrestler [Radeon HD 6320][/FONT]
[FONT=Menlo]       fabricante: Advanced Micro Devices, Inc. [AMD/ATI][/FONT]
[FONT=Menlo]       ID físico: 1[/FONT]
[FONT=Menlo]       informações do barramento: pci@0000:00:01.0[/FONT]
[FONT=Menlo]       versão: 00[/FONT]
[FONT=Menlo]       largura: 32 bits[/FONT]
[FONT=Menlo]       clock: 33MHz[/FONT]
[FONT=Menlo]       capacidades: pm pciexpress msi vga_controller bus_master cap_list rom[/FONT]
[FONT=Menlo]       configuração: driver=radeon latency=0[/FONT]
[FONT=Menlo]       recursos: irq:41 memória:b0000000-bfffffff porta de E/S:f000(tamanho=256) memória:feb00000-feb3ffff[/FONT]

```

```

diogosaraiva@Ubuntu:~$ glxinfo | grep render
direct rendering: Yes
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
OpenGL renderer string: Gallium 0.4 on AMD PALM
    GL_MESA_texture_signed_rgba, GL_NV_conditional_render, GL_NV_depth_clamp, 
    GL_NV_blend_square, GL_NV_conditional_render, GL_NV_depth_clamp, 


```

```

diogosaraiva@Ubuntu:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
302 frames in 5.0 seconds = 60.227 FPS
301 frames in 5.0 seconds = 60.101 FPS
301 frames in 5.0 seconds = 60.094 FPS
301 frames in 5.0 seconds = 60.103 FPS
301 frames in 5.0 seconds = 60.105 FPS
301 frames in 5.0 seconds = 60.096 FPS
301 frames in 5.0 seconds = 60.107 FPS
301 frames in 5.0 seconds = 60.102 FPS
^C


```


```

diogosaraiva@Ubuntu:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   X.Org
OpenGL renderer string: Gallium 0.4 on AMD PALM
OpenGL version string:  3.0 Mesa 10.1.3

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes


```

```

diogosaraiva@Ubuntu:~$ glxinfo | grep -i opengl
OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD PALM
OpenGL core profile version string: 3.3 (Core Profile) Mesa 10.1.3
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 10.1.3
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:


```


sorry to intruding and thank you in advance

PS: to michael-piziak: One suggestion for running emulators in Ubuntu is the EmulationStation.. with libretro/retroarch emulators... is what I have...

Thanks again

---

