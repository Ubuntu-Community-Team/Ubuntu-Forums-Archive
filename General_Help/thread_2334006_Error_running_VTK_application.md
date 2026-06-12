---
title: "Error running VTK application"
date: 2016-08-15
forum: General Help
---

### Post by hlustosa on 2016-08-15
Hello Everyone

I am trying to set a up a VTK server on a remote machine at work. I've built VTK 7.0 on ubuntu server 16.04 (without setting up any desktop enviroment for it) without any problems, using the OSMESA flag. I am trying to run VTK applications with offscreen rendering, and save the visualization output in regular png files. In order to build VTK I installed libmesa:

dpkg --get-selections | grep mesa*
```
libegl1-mesa:amd64                install
libgl1-mesa-dev:amd64                install
libgl1-mesa-dri:amd64                install
libgl1-mesa-dri:i386                install
libgl1-mesa-glx:amd64                install
libglapi-mesa:amd64                install
libgles2-mesa:amd64                install
libglu1-mesa:amd64                install
libglu1-mesa-dev:amd64                install
libosmesa6:amd64                install
libosmesa6-dev:amd64                install
libwayland-egl1-mesa:amd64            install
mesa-common-dev:amd64                install
mesa-utils                    install
mesa-utils-extra                install

```

I've written a test application, that creates a VTK primitive and saves the render results to a file. It is running smoothly on a different machine (that has desktop environment), however, ehen I run the application on the server, I get this error:

```
ERROR: In /opt/VTK/Rendering/OpenGL2/vtkOpenGLRenderWindow.cxx, line 609
vtkXOpenGLRenderWindow (0x7f8e5c017940): GL version 2.1 with the gpu_shader4 extension is not supported by your graphics driver but is required for the new OpenGL rendering backend. Please update your OpenGL driver. If you are using Mesa please make sure you have version 10.6.5 or later and make sure your driver in Mesa supports OpenGL 3.2.
```

Is it hardware limitation issue or something that can be fixed with some package installation? 

Some extra info:

inxi -G

```
Graphics:  Card: Matrox Systems G200eR2           Display Server: X.Org 1.15.1 driver: N/A Resolution: 1366x768@60.00hz
           GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 3.8, 256 bits) GLX Version: 3.0 Mesa 11.2.0

```

lshw -c DISPLAY
```

*-display UNCLAIMED            description: VGA compatible controller
       product: G200eR2
       vendor: Matrox Electronics Systems Ltd.
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list
       configuration: latency=64 maxlatency=32 mingnt=16
       resources: memory:90000000-90ffffff memory:91800000-91803fff memory:91000000-917fffff
```

sudo glxinfo | grep OpenGL
```

libGL error: failed to open drm device: No such file or directory
libGL error: failed to load driver: i965
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.8, 256 bits)
OpenGL core profile version string: 3.3 (Core Profile) Mesa 11.2.0
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 11.2.0
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.0 Mesa 11.2.0
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.00
OpenGL ES profile extensions:

```

I haven't found any useful information on this problem except that this could be a hardware limitation problem. I am really lost at this point. Any tips are welcome.

Thanks in advance.

---

### Post by deadflowr on 2016-08-15
> OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.8, 256 bits)
This means your system is running in software rendering mode, and not hardware, because you do not have a functional graphics card driver for your card.

Suppose it's related to this bug:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1316035]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1316035")

But who knows whether or not a functional graphics card driver will help...

the card might not have the capabilities to run the gpu_shader extension requested, anyway.

---

