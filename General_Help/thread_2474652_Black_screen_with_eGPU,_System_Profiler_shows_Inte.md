---
title: "Black screen with eGPU, System Profiler shows Intel 3000 but installed Nvidia GT 1030"
date: 2022-05-04
forum: General Help
---

### Post by SciGuy1872 on 2022-05-04
Hi. I get a black screen when starting the computer with an eGPU connected--I get around that problem by hot plugging the ExpressCard after logging out.  What's a better way?  I know now how to get the computer to recognize the external graphics card, and so I went to Additional Drivers and installed the 470 it listed.  Before I had the GT 1030, I had a GT 590; I was thinking that maybe having multiple drivers was the cause for the black screen.  I checked, but the 470 was the only installed:

```
anthony@anthony-Latitude-E5420:~$ dpkg -l | grep nvidia
ii  libnvidia-cfg1-470:amd64                      470.103.01-0ubuntu0.20.04.1          amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-470                          470.103.01-0ubuntu0.20.04.1          all          Shared files used by the NVIDIA libraries
ii  libnvidia-compute-470:amd64                   470.103.01-0ubuntu0.20.04.1          amd64        NVIDIA libcompute package
ii  libnvidia-compute-470:i386                    470.103.01-0ubuntu0.20.04.1          i386         NVIDIA libcompute package
ii  libnvidia-decode-470:amd64                    470.103.01-0ubuntu0.20.04.1          amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-470:i386                     470.103.01-0ubuntu0.20.04.1          i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-470:amd64                    470.103.01-0ubuntu0.20.04.1          amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-470:i386                     470.103.01-0ubuntu0.20.04.1          i386         NVENC Video Encoding runtime library
ii  libnvidia-extra-470:amd64                     470.103.01-0ubuntu0.20.04.1          amd64        Extra libraries for the NVIDIA driver
ii  libnvidia-fbc1-470:amd64                      470.103.01-0ubuntu0.20.04.1          amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-470:i386                       470.103.01-0ubuntu0.20.04.1          i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-470:amd64                        470.103.01-0ubuntu0.20.04.1          amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-470:i386                         470.103.01-0ubuntu0.20.04.1          i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-470:amd64                      470.103.01-0ubuntu0.20.04.1          amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  libnvidia-ifr1-470:i386                       470.103.01-0ubuntu0.20.04.1          i386         NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  nvidia-compute-utils-470                      470.103.01-0ubuntu0.20.04.1          amd64        NVIDIA compute utilities
ii  nvidia-dkms-470                               470.103.01-0ubuntu0.20.04.1          amd64        NVIDIA DKMS package
ii  nvidia-driver-470                             470.103.01-0ubuntu0.20.04.1          amd64        NVIDIA driver metapackage
ii  nvidia-kernel-common-470                      470.103.01-0ubuntu0.20.04.1          amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-470                      470.103.01-0ubuntu0.20.04.1          amd64        NVIDIA kernel source package
ii  nvidia-prime                                  0.8.16~0.20.04.2                     all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                               470.57.01-0ubuntu0.20.04.3           amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-470                              470.103.01-0ubuntu0.20.04.1          amd64        NVIDIA driver support binaries
ii  screen-resolution-extra                       0.18build1                           all          Extension for the nvidia-settings control panel
ii  xserver-xorg-video-nvidia-470                 470.103.01-0ubuntu0.20.04.1          amd64        NVIDIA binary Xorg driver

```

Even though this Nvidia driver is installed, when I go to the System Profiler, the graphics are listed as the onboard--Intel 3000.  I have attached a screenshot if you wish to see).  I figure it's just a little mistake keeping me from using the Nvidia, since the card was detected and the driver was installed.

---

