---
title: "WebGL not working in either Firefox nor Chrome"
date: 2014-01-19
forum: General Help
---

### Post by Sashaafm on 2014-01-19
[COLOR=#333333][FONT=UbuntuRegular]I'm using Ubuntu 13.10 (through Virtualbox in a Windows 8.1 host) and finally managed to install the correct drivers for my nVidia card (using bumblebee) and glxinfo finally shows that I support OpenGL 4.20. So, lastly, for the project I'm working on, I need to get WebGL running in either Chrome or Firefox (I'd rather use in Chrome) to test the program I'm developing. I believe this may be a conflict with my on-board Intel HD5000 maybe?
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]When I try to run the WebGL .html file in Firefox I get this in the terminal:
[/FONT][/COLOR]
(process:8315): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed
    OpenGL Warning: glFlushVertexArrayRangeNV not found in mesa table
    OpenGL Warning: glVertexArrayRangeNV not found in mesa table
    OpenGL Warning: glCombinerInputNV not found in mesa table
    OpenGL Warning: glCombinerOutputNV not found in mesa table
    OpenGL Warning: glCombinerParameterfNV not found in mesa table
    OpenGL Warning: glCombinerParameterfvNV not found in mesa table
    OpenGL Warning: glCombinerParameteriNV not found in mesa table
    OpenGL Warning: glCombinerParameterivNV not found in mesa table
    OpenGL Warning: glFinalCombinerInputNV not found in mesa table
    OpenGL Warning: glGetCombinerInputParameterfvNV not found in mesa table
    OpenGL Warning: glGetCombinerInputParameterivNV not found in mesa table
    OpenGL Warning: glGetCombinerOutputParameterfvNV not found in mesa table
    OpenGL Warning: glGetCombinerOutputParameterivNV not found in mesa table
    OpenGL Warning: glGetFinalCombinerInputParameterfvNV not found in mesa table
    OpenGL Warning: glGetFinalCombinerInputParameterivNV not found in mesa table
    OpenGL Warning: glDeleteFencesNV not found in mesa table
    OpenGL Warning: glFinishFenceNV not found in mesa table
    OpenGL Warning: glGenFencesNV not found in mesa table
    OpenGL Warning: glGetFenceivNV not found in mesa table
    OpenGL Warning: glIsFenceNV not found in mesa table
    OpenGL Warning: glSetFenceNV not found in mesa table
    OpenGL Warning: glTestFenceNV not found in mesa table
    ATTENTION: default value of option force_s3tc_enable overridden by environment.
    OpenGL Warning: Unimplemented glxMakeCurrent call with GLXPixmap passed, unexpected things might happen.
    OpenGL Warning: Failed to get windows geometry for 0x7ff7e0b8d800, try xwininfo
    OpenGL version detected: 210
    OpenGL Warning: Unknown program 0
    OpenGL version detected: 210
    OpenGL Warning: Unknown program 0
    OpenGL version detected: 210
    OpenGL Warning: Unknown program 0
    OpenGL Warning: Unimplemented glxMakeCurrent call with GLXPixmap passed, unexpected things might happen.
    OpenGL Warning: Failed to get windows geometry for 0x7ff7d14b3800, try xwininfo
    OpenGL version detected: 210
    OpenGL Warning: Unknown program 0
    OpenGL Warning: Unimplemented glxMakeCurrent call with GLXPixmap passed, unexpected things might happen.
    OpenGL Warning: Failed to get windows geometry for 0x7ff7d14b3800, try xwininfo
    OpenGL version detected: 210
    OpenGL Warning: Unknown program 0

[COLOR=#333333][FONT=UbuntuRegular]And in Chrome I get the following:
[/FONT][/COLOR]
OpenGL Warning: glFlushVertexArrayRangeNV not found in mesa table
OpenGL Warning: glVertexArrayRangeNV not found in mesa table
OpenGL Warning: glCombinerInputNV not found in mesa table
OpenGL Warning: glCombinerOutputNV not found in mesa table
OpenGL Warning: glCombinerParameterfNV not found in mesa table
OpenGL Warning: glCombinerParameterfvNV not found in mesa table
OpenGL Warning: glCombinerParameteriNV not found in mesa table
OpenGL Warning: glCombinerParameterivNV not found in mesa table
OpenGL Warning: glFinalCombinerInputNV not found in mesa table
OpenGL Warning: glGetCombinerInputParameterfvNV not found in mesa table
OpenGL Warning: glGetCombinerInputParameterivNV not found in mesa table
OpenGL Warning: glGetCombinerOutputParameterfvNV not found in mesa table
OpenGL Warning: glGetCombinerOutputParameterivNV not found in mesa table
OpenGL Warning: glGetFinalCombinerInputParameterfvNV not found in mesa table
OpenGL Warning: glGetFinalCombinerInputParameterivNV not found in mesa table
OpenGL Warning: glDeleteFencesNV not found in mesa table
OpenGL Warning: glFinishFenceNV not found in mesa table
OpenGL Warning: glGenFencesNV not found in mesa table
OpenGL Warning: glGetFenceivNV not found in mesa table
OpenGL Warning: glIsFenceNV not found in mesa table
OpenGL Warning: glSetFenceNV not found in mesa table
OpenGL Warning: glTestFenceNV not found in mesa table
ATTENTION: default value of option force_s3tc_enable overridden by environment.
OpenGL Warning: glXChooseFBConfig returning NULL, due to attrib=0x2, next=0x20
[8501:8501:0119/161214:ERROR:gl_surface_glx.cc(739)] glXChooseFBConfig failed.
[8501:8501:0119/161214:ERROR:gpu_info_collector.cc(27)] gfx::GLContext::CreateOffscreenGLSurface failed
[8501:8501:0119/161214:ERROR:sandbox_linux.cc(142)] InitializeSandbox() called with multiple threads in process gpu-process
OpenGL Warning: glXChooseFBConfig returning NULL, due to attrib=0x2, next=0x20
[8501:8501:0119/161214:ERROR:gl_surface_glx.cc(739)] glXChooseFBConfig failed.
[7:7:0119/161214:ERROR:command_buffer_proxy_impl.cc(164)] Failed to initialize command buffer service.
OpenGL Warning: glXChooseFBConfig returning NULL, due to attrib=0x2, next=0x20
[8501:8501:0119/161214:ERROR:gl_surface_glx.cc(739)] glXChooseFBConfig failed.
[7:7:0119/161214:ERROR:command_buffer_proxy_impl.cc(164)] Failed to initialize command buffer service.

[COLOR=#333333][FONT=UbuntuRegular]My nVidia card is a 765GTXM. When I run the exact same file in Windows everything runs smoothly.[/FONT][/COLOR]

---

