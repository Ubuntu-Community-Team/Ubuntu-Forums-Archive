---
title: "OpenGL problem with Ubuntu 22.04 and x2go"
date: 2024-04-29
forum: General Help
---

### Post by philippejuhel on 2024-04-29
Hi, 

On Ubuntu 22.04, I've installed x2go server and the Coppelia software ([https://www.coppeliarobotics.com/](https://www.coppeliarobotics.com/)). 
When I run this software directly on the server, it works : 

```
[FONT=Arial]phil@DL:/usr/local/[/FONT][FONT=Arial]CoppeliaSim_Edu_V4_6_0_rev18_[/FONT][FONT=Arial]Ubuntu22_04$ ./coppeliaSim[/FONT]
[FONT=Arial][CoppeliaSimClient]   loading the CoppeliaSim library...[/FONT]
[FONT=Arial][CoppeliaSimClient:loadinfo]   done.[/FONT]
[FONT=Arial][CoppeliaSimClient:loadinfo]   launching CoppeliaSim...[/FONT]
[FONT=Arial][CoppeliaSim:loadinfo]   Application directory is /usr/local/CoppeliaSim_Edu_V4_[/FONT][FONT=Arial]6_0_rev18_Ubuntu22_04[/FONT]
[FONT=Arial][CoppeliaSim:loadinfo]   user settings file is /home/phil/.CoppeliaSim/[/FONT][FONT=Arial]usrset.txt[/FONT]
[FONT=Arial][CoppeliaSim:loadinfo]   CoppeliaSim v4.6.0 (rev. 18), flavor: 1, linux[/FONT]
[FONT=Arial][CoppeliaSim:loadinfo]   plugin simIK0: loading...[/FONT]
[FONT=Arial][CoppeliaSim:loadinfo]   plugin simIK0: done.[/FONT]
[FONT=Arial][CoppeliaSim:loadinfo]   primary screen physical dots per inch: 93[/FONT]
[FONT=Arial][CoppeliaSim:loadinfo]   display scaling (guessed): 100[/FONT]
[FONT=Arial][CoppeliaSim:loadinfo]   loaded the video compression library.[/FONT]
[FONT=Arial][CoppeliaSim:loadinfo]   if CoppeliaSim crashes now, try to install libgl1-mesa-dev on your system:[/FONT]
[FONT=Arial]    >sudo apt install libgl1-mesa-dev[/FONT]
[FONT=Arial][CoppeliaSim:loadinfo]   OpenGL: NVIDIA Corporation, Renderer: NVIDIA GeForce RTX 2080 Ti/PCIe/SSE2, Version: 4.6.0 NVIDIA 545.29.06[/FONT]
[FONT=Arial][CoppeliaSim:loadinfo]   simulator launched.[/FONT]
```

On another computer, with x2go client, I want to launch Coppelia and I get this error : 
```
phil@DL:/usr/local/CoppeliaSim_Edu_V4_6_0_rev18_Ubuntu22_04$ ./coppeliaSim[CoppeliaSimClient]   loading the CoppeliaSim library...
[CoppeliaSimClient:loadinfo]   done.
[CoppeliaSimClient:loadinfo]   launching CoppeliaSim...
[CoppeliaSim:loadinfo]   Application directory is /usr/local/CoppeliaSim_Edu_V4_6_0_rev18_Ubuntu22_04
qt.qpa.xcb: X server does not support XInput 2
[CoppeliaSim:loadinfo]   user settings file is /home/phil/.CoppeliaSim/usrset.txt
[CoppeliaSim:loadinfo]   CoppeliaSim v4.6.0 (rev. 18), flavor: 1, linux
[CoppeliaSim:loadinfo]   plugin simIK0: loading...
[CoppeliaSim:loadinfo]   plugin simIK0: done.
[CoppeliaSim:loadinfo]   primary screen physical dots per inch: 141
[CoppeliaSim:loadinfo]   display scaling (guessed): 147
qt.qpa.xcb: X server does not support XInput 2
[CoppeliaSim:loadinfo]   loaded the video compression library.
qt.qpa.xcb: QXcbConnection: XCB error: 1 (BadRequest), sequence: 169, resource id: 649, major code: 130 (Unknown), minor code: 47
qt.glx: qglx_findConfig: Failed to finding matching FBConfig for QSurfaceFormat(version 2.0, options QFlags<QSurfaceFormat::FormatOption>(), depthBufferSize -1, redBufferSize 1, greenBufferSize 1, blueBufferSize 1, alphaBufferSize -1, stencilBufferSize -1, samples -1, swapBehavior QSurfaceFormat::SingleBuffer, swapInterval 1, colorSpace QSurfaceFormat::DefaultColorSpace, profile  QSurfaceFormat::NoProfile)
No XVisualInfo for format QSurfaceFormat(version 2.0, options QFlags<QSurfaceFormat::FormatOption>(), depthBufferSize -1, redBufferSize 1, greenBufferSize 1, blueBufferSize 1, alphaBufferSize -1, stencilBufferSize -1, samples -1, swapBehavior QSurfaceFormat::SingleBuffer, swapInterval 1, colorSpace QSurfaceFormat::DefaultColorSpace, profile  QSurfaceFormat::NoProfile)
Falling back to using screens root_visual.
qt.glx: qglx_findConfig: Failed to finding matching FBConfig for QSurfaceFormat(version 2.0, options QFlags<QSurfaceFormat::FormatOption>(), depthBufferSize 0, redBufferSize 1, greenBufferSize 1, blueBufferSize 1, alphaBufferSize -1, stencilBufferSize 0, samples -1, swapBehavior QSurfaceFormat::SingleBuffer, swapInterval -1, colorSpace QSurfaceFormat::DefaultColorSpace, profile  QSurfaceFormat::NoProfile)
No XVisualInfo for format QSurfaceFormat(version 2.0, options QFlags<QSurfaceFormat::FormatOption>(), depthBufferSize 0, redBufferSize 1, greenBufferSize 1, blueBufferSize 1, alphaBufferSize -1, stencilBufferSize 0, samples -1, swapBehavior QSurfaceFormat::SingleBuffer, swapInterval -1, colorSpace QSurfaceFormat::DefaultColorSpace, profile  QSurfaceFormat::NoProfile)
Falling back to using screens root_visual.
qt.glx: qglx_findConfig: Failed to finding matching FBConfig for QSurfaceFormat(version 2.0, options QFlags<QSurfaceFormat::FormatOption>(), depthBufferSize 0, redBufferSize 1, greenBufferSize 1, blueBufferSize 1, alphaBufferSize -1, stencilBufferSize 0, samples -1, swapBehavior QSurfaceFormat::SingleBuffer, swapInterval -1, colorSpace QSurfaceFormat::DefaultColorSpace, profile  QSurfaceFormat::NoProfile)
qt.glx: qglx_findConfig: Failed to finding matching FBConfig for QSurfaceFormat(version 2.0, options QFlags<QSurfaceFormat::FormatOption>(), depthBufferSize 0, redBufferSize 1, greenBufferSize 1, blueBufferSize 1, alphaBufferSize -1, stencilBufferSize 0, samples -1, swapBehavior QSurfaceFormat::SingleBuffer, swapInterval -1, colorSpace QSurfaceFormat::DefaultColorSpace, profile  QSurfaceFormat::NoProfile)
Could not initialize GLX
Aborted (core dumped)



```

When I run glxinfo, I have this error : 
```
phil@DL:~$ glxinfoname of display: :50.0
Error: couldn't find RGB GLX visual or fbconfig



```

On the remote computer, if I use 
```
ssh -X -t phil@server_ip_address /bin/bash
```

It works : 
```
phil@DL:/usr/local/CoppeliaSim_Edu_V4_6_0_rev18_Ubuntu22_04$ ./coppeliaSim[CoppeliaSimClient]   loading the CoppeliaSim library...
[CoppeliaSimClient:loadinfo]   done.
[CoppeliaSimClient:loadinfo]   launching CoppeliaSim...
[CoppeliaSim:loadinfo]   Application directory is /usr/local/CoppeliaSim_Edu_V4_6_0_rev18_Ubuntu22_04
[CoppeliaSim:loadinfo]   user settings file is /home/phil/.CoppeliaSim/usrset.txt
[CoppeliaSim:loadinfo]   CoppeliaSim v4.6.0 (rev. 18), flavor: 1, linux
[CoppeliaSim:loadinfo]   plugin simIK0: loading...
[CoppeliaSim:loadinfo]   plugin simIK0: done.
[CoppeliaSim:loadinfo]   primary screen physical dots per inch: 142
[CoppeliaSim:loadinfo]   display scaling (guessed): 100
[CoppeliaSim:loadinfo]   loaded the video compression library.
[CoppeliaSim:loadinfo]   if CoppeliaSim crashes now, try to install libgl1-mesa-dev on your system:
    >sudo apt install libgl1-mesa-dev
[CoppeliaSim:loadinfo]   OpenGL: Mesa, Renderer: llvmpipe (LLVM 15.0.7, 256 bits), Version: 4.5 (Compatibility Profile) Mesa 23.2.1-1ubuntu3.1~22.04.2
[CoppeliaSim:loadinfo]   simulator launched.

```

and here is the glxinfo for this connection : 

```

phil@DL:~$ glxinfo | grep "OpenGL version"
OpenGL version string: 4.5 (Compatibility Profile) Mesa 23.2.1-1ubuntu3.1~22.04.2

```

Another experiment : on another server with Ubuntu **20.04**, using an x2go connection to launch Coppelia works.

Another problem with Ubuntu 22.04 and x2go : after a few minutes of inactivity, the x2go screen is freezed and I need to kill the x2goagent application. 

So, what is the problem with Ubuntu 22.04 and x2go? Any idea?

Philippe

---

### Post by c_xy on 2024-07-21
Hello, 

Were you able to solve this problem?

We've run into the same problem with a newly installed Ubuntu 22.04 LTS server and accessing remotely through x2go.

```


% glxinfo
name of display: :50
Error: couldn't find RGB GLX visual or fbconfig


```


```


%glxgears
Error: couldn't get an RGB, Double-buffered visual


```


No issues running x2go and the glx commands on 20.04. It is just with Ubuntu 22.04.

Wondering if it has anything to do with initial installation or the initial  updates after installation. On our device we have two NVIDIA graphic accelerator cards on both the Ubuntu 20.04 and Ubuntu 22.04 dell servers.

Thanks.

c

---

