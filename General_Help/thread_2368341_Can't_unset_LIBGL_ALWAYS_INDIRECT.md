---
title: "Can't unset LIBGL_ALWAYS_INDIRECT"
date: 2017-08-09
forum: General Help
---

### Post by c_xy on 2017-08-09
Hello,

I've run into an issue with our server. It is a Dell R730, running Ubuntu 14.04. We have users connect remotely from Windows/Mac clients using nx.

Here is some background output:

```

%% sudo lshw -C video

 *-display               
       description: 3D controller
       product: GK104GL [Tesla K10]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=nvidia latency=0
       resources: iomemory:33f0-33ef iomemory:33f0-33ef irq:31 memory:92000000-92ffffff memory:33fe0000000-33fefffffff memory:33ff0000000-33ff1ffffff
  *-display
       description: 3D controller
       product: GK104GL [Tesla K10]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=nvidia latency=0
       resources: iomemory:33f0-33ef iomemory:33f0-33ef irq:31 memory:91000000-91ffffff memory:33fc0000000-33fcfffffff memory:33fd0000000-33fd1ffffff
  *-display UNCLAIMED
       description: VGA compatible controller
       product: G200eR2
       vendor: Matrox Electronics Systems Ltd.
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list
       configuration: latency=64 maxlatency=32 mingnt=16
       resources: memory:90000000-90ffffff memory:93800000-93803fff memory:93000000-937fffff




```


The problem is we cannot unset the [COLOR=#333333][FONT=Consolas]LIBGL_ALWAYS_INDIRECT environmental variable.

The output from [/FONT][/COLOR]  

```
 glxinfo | grep "Open"
```

Is:

```


OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL core profile version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL core profile extensions:
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL extensions:


```

We can't change the OpenGL render string from Mesa GLX Indirect. The OpenGL version string remains at 1.2. We can't use software on our system because it requires a version of 1.4 or higher.


We  checked another we have, dell r730 with similar specs, running 16.04 but the same G200eR2 video card. The glixinfo output is:

```

OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 4.0, 256 bits)
OpenGL version string: 3.0 Mesa 17.0.7
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:



```

Then I ran a debugging on both systems:

problem r730:

```

LIBGL_DEBUG=verbose glxinfo | grep -i -A 5 -B 5 direct
name of display: :2000.0
Warning: GL error 0x500 at line 922
display: :2000  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_OML_swap_method, GLX_SGIS_multisample, 
--
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL core profile version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL core profile extensions:
    GL_ARB_depth_texture, GL_ARB_imaging, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 

```

working r730:

```


LIBGL_DEBUG=verbose glxinfo | grep -i -A 5 -B 5 direct
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/swrast_dri.so
libGL: Can't open configuration file /home/mlk/.drirc: No such file or directory.
libGL: Can't open configuration file /home/mlk/.drirc: No such file or directory.
name of display: :50.0
display: :50  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_OML_swap_method, GLX_SGIS_multisample, 



```



One difference to notice is that I cannot get the problem r730 to change to direct rendering: yes. 

Using the command:

```

unset LIBGL_ALWAYS_INDIRECT


```

Doesn't change anything. There is still says direct rendering: No. Another difference we noticed was the following error:

```
Warning: GL error 0x500 at line 922
```

Is this error  preventing direct rendering? Is the reason why the OpenGL version string remains at 1.2 instead of 3.0?

Any help would greatly be appreciated.

Thanks.

c

---

### Post by c_xy on 2017-08-16
Close Thread. Will ask a different question somewhat related to this.

Thanks.

---

### Post by wildmanne39 on 2017-08-16
Closed at OP's request and only because no other members had posted in this thread!

In the future please use the report button if you want us to close or move a thread or you need to report a thread.

You can bump your thread once every 12 hours to keep it on the first page so members can see it.

---

