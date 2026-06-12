---
title: "libgl.so Ubuntu 22.04 Nvidia Drivers 32-bit on 64-bit - Can't get MOHAA to run"
date: 2023-12-06
forum: General Help
---

### Post by own3mall on 2023-12-06
I've installed the latest Nvidia drivers, but when I try to launch mohaa (Medal of Honor Allied Assault) in Ubuntu 22.04, I can't get it to work.

> 
./mohaa_lnx
----------------------
18294 files in pk3 files
execing default.cfg
execing menu.cfg
couldn't exec newconfig.cfg
Config: unnamedsoldier.cfg
STUB: wtf in unix/linux_general_extras.c line 95.
STUB: wtf in unix/linux_general_extras.c line 101.
execing configs/unnamedsoldier.cfg
couldn't exec localized.cfg
execing autoexec.cfg
Unknown command "fov"
couldn't exec custom.cfg
You are now setup for easy mode.
----- Client Initialization -----
Called FadeSound with: 0.000000
----- Initializing Renderer ----
----- R_Init -----
...loading libGL.so: SDL: SDL_GL_LoadLibrary() failed! rc == (-1).
SDL_GetError() reports "Could not load OpenGL library".
failed
...loading libMesaVoodooGL.so.3.1: SDL: SDL_GL_LoadLibrary() failed! rc == (-1).
SDL_GetError() reports "Could not load OpenGL library".
failed
ASSERT: [qcommon/common.c:406] GLimp_Init() - could not load OpenGL subsystem
 (fyi)
----- CL_Shutdown -----
-----------------------
Error: GLimp_Init() - could not load OpenGL subsystem


I have the 32-bit drivers installed along with the 64-bit drivers:

> 
dpkg -l | grep libnvidia
ii  libnvidia-cfg1-535:amd64                   535.129.03-0ubuntu0.22.04.1             amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-535                       535.129.03-0ubuntu0.22.04.1             all          Shared files used by the NVIDIA libraries
ii  libnvidia-compute-535:amd64                535.129.03-0ubuntu0.22.04.1             amd64        NVIDIA libcompute package
ii  libnvidia-decode-535:amd64                 535.129.03-0ubuntu0.22.04.1             amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-535:amd64                 535.129.03-0ubuntu0.22.04.1             amd64        NVENC Video Encoding runtime library
ii  libnvidia-extra-535:amd64                  535.129.03-0ubuntu0.22.04.1             amd64        Extra libraries for the NVIDIA driver
ii  libnvidia-fbc1-535:amd64                   535.129.03-0ubuntu0.22.04.1             amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-535:amd64                     535.129.03-0ubuntu0.22.04.1             amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-535:i386                      535.129.03-0ubuntu0.22.04.1             i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD


nvidia-smi detects my graphics card:

> 
nvidia-smi
Wed Dec  6 14:14:26 2023       
+---------------------------------------------------------------------------------------+
| NVIDIA-SMI 535.129.03             Driver Version: 535.129.03   CUDA Version: 12.2     |
|-----------------------------------------+----------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |         Memory-Usage | GPU-Util  Compute M. |
|                                         |                      |               MIG M. |
|=========================================+======================+======================|
|   0  NVIDIA GeForce RTX 4070 ...    Off | 00000000:01:00.0 Off |                  N/A |
| N/A   53C    P4              10W / 115W |    430MiB /  8188MiB |     11%      Default |
|                                         |                      |                  N/A |
+-----------------------------------------+----------------------+----------------------+
                                                                                         
+---------------------------------------------------------------------------------------+
| Processes:                                                                            |
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory |
|        ID   ID                                                             Usage      |
|=======================================================================================|
|    0   N/A  N/A      1465      G   /usr/lib/xorg/Xorg                          159MiB |
|    0   N/A  N/A      1880      G   /usr/bin/gnome-shell                         91MiB |
|    0   N/A  N/A      2385      G   ...irefox/2987/usr/lib/firefox/firefox      169MiB |
+---------------------------------------------------------------------------------------+


It appears the Nvidia drivers no longer provide their implementations of libgl1?

[https://askubuntu.com/questions/611026/steam-error-missing-libgl-so-1](https://askubuntu.com/questions/611026/steam-error-missing-libgl-so-1)
[https://www.reddit.com/r/Ubuntu/comments/zhhttc/enable_32_bit_drivers/](https://www.reddit.com/r/Ubuntu/comments/zhhttc/enable_32_bit_drivers/)

Anyone know how I can get this old game working on Ubuntu 22.04?

---

### Post by MAFoElffen on 2023-12-06
RE: [https://www.reddit.com/r/wine_gaming/comments/je8gvo/comment/g9q3vx5/?utm_source=share&utm_medium=web3x&utm_name=web3xcss&utm_term=1&utm_content=share_button](https://www.reddit.com/r/wine_gaming/comments/je8gvo/comment/g9q3vx5/?utm_source=share&utm_medium=web3x&utm_name=web3xcss&utm_term=1&utm_content=share_button)

---

### Post by Yellow Pasque on 2023-12-09
Do you have libgl-dev:i386 package installed?

---

