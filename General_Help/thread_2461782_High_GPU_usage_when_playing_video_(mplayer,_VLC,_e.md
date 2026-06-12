---
title: "High GPU usage when playing video (mplayer, VLC, etc)"
date: 2021-05-06
forum: General Help
---

### Post by riverhawk on 2021-05-06
Hello everyone. Recently I've been having a very high GPU load when watching video. This happens with both mplayer and VLC. My computer is fairly old, but I always thought of it as pretty powerful. It is a Dell Latitude E6430. As an example of the GPU load, opening a random video gets a load of around 70-80%. Resizing this video to fill the screen causes the GPU load to jump to 150%. VLC goes up to around 180%.

One note on my computer is the video card is an old Nvidia. I used to be able to use it back when I was running some other distro, but never got it working on Xubuntu. I really don't think this is the problem, since I've been running Xubuntu for years and only recently noticed the high GPU problem.

I did a little research and changed the output driver to "xv", that definitely reduced the load, but then I couldn't resize the video, so that's not a good solution. Right now the output driver is set to "gl (fast)."

Any advice or suggestions would be much appreciated. Thank you!

---

### Post by HermanAB on 2021-05-07
It means that ffmpeg/gstreamer doesn't recognize the graphical processor and therefore uses emulation on the CPU.  You may need to reinstall/recompile the video device driver, ffmpeg and gstreamer.  That will keep you busy and out of trouble for a few days.

---

### Post by Yellow Pasque on 2021-05-07
Please give output of:
```
glxinfo -B
```

---

### Post by riverhawk on 2021-05-07
Thanks for the replies!

@HermanAB I have experience reinstalling the video device driver and know it is not for the faint of heart! I will look into: the video device driver, ffmpeg and gstreamer and see what I can come up with. 

@Yellow Pasque here is the output from [COLOR=#000000][FONT=&amp]glxinfo -B

[/FONT][/COLOR]```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
Extended renderer info (GLX_MESA_query_renderer):
    Vendor: Mesa/X.org (0xffffffff)
    Device: llvmpipe (LLVM 11.0.0, 256 bits) (0xffffffff)
    Version: 20.2.6
    Accelerated: no
    Video memory: 7915MB
    Unified memory: no
    Preferred profile: core (0x1)
    Max core profile version: 4.5
    Max compat profile version: 3.1
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.2
OpenGL vendor string: Mesa/X.org
OpenGL renderer string: llvmpipe (LLVM 11.0.0, 256 bits)
OpenGL core profile version string: 4.5 (Core Profile) Mesa 20.2.6
OpenGL core profile shading language version string: 4.50
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile


OpenGL version string: 3.1 Mesa 20.2.6
OpenGL shading language version string: 1.40
OpenGL context flags: (none)


OpenGL ES profile version string: OpenGL ES 3.2 Mesa 20.2.6
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20

```

---

### Post by TheFu on 2021-05-07
If the CPU is being used, then the GPU hardware decoding is not being used.  That's why a $75 Chromebook plays 1080p youtube videos, but struggles to open a libreoffice document - the built in GPU decoder for video processing.

So, you need a video player that enables your specific GPU video hardware decoding to be used.  That will depend on the GPU driver being used AND the program used to playback the video.  I had an old nvidia GPU that lost driver support, so all the video decoding had to be performed by the CPU, not the GPU.  My solution was to get a 1-gen old GPU for $70, install the nvidia driver (sudo ubuntu-drivers autoinstall), then use mpv as the playback software.  With that combination, the CPU barely does anything. The GPU does the video playback stuff for mpeg2, h.264 and h.265/HEVC videos.

I think mpv has a GUI front-end, but I never use it.  Maybe smplayer works with both? [https://www.smplayer.info/en/mpv](https://www.smplayer.info/en/mpv)  mpv lets us play youtube URLs directly, which is nice.

mpv is a fork of mplayer. There are many things that mpv does better than mplayer, but a few things that mpv doesn't do that only mplayer does, so I use both, depending on the task.

---

### Post by Yellow Pasque on 2021-05-08
Your video driver is broken. Please file a bug with the following command to gather all the relevant logs. Remember to copy the link here.
```
apport-bug xorg
```

> **TheFu said:**
> Stuff

1. The OP has a laptop, so buying a new GPU is not the answer.
2. The laptop probably has Intel HD4000 if google has not failed me, so it should at least be able to play h.264 smoothly/efficiently.
3. The OP's video driver is broken, so worrying about video players is putting the cart ahead of the horse.

---

### Post by mikewhatever on 2021-05-08
It would have been useful to specify the exact hardware in post #1. Perhaps you'd be kind enough to post the output of <lspci -nnk | grep -A3 VGA> sometime soon.

---

### Post by riverhawk on 2021-05-08
Hi everyone, thanks and I really appreciate the time. I'm getting a lot out of reading through the answers.

I filed the following bug report: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1927841](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1927841)

Output from <[COLOR=#000000]<lspci -nnk | grep -A3 VGA> is:[/COLOR]

```
[COLOR=#000000]
[/COLOR]01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF108GLM [NVS 5200M] [10de:0dfc] (rev a1)    Subsystem: Dell GF108GLM [NVS 5200M] [1028:0534]
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
01:00.1 Audio device [0403]: NVIDIA Corporation GF108 High Definition Audio Controller [10de:0bea] (rev a1)
```

I will continue to monitor this thread, although I'm not on the computer every day, and will make replies if needed.

Thanks again!

---

### Post by mikewhatever on 2021-05-09
Let us also see the ouput of <dpkg -l | grep nvidia>. How was the driver installed? Have you tried reinstalling it?

---

### Post by Yellow Pasque on 2021-05-09
I see a few problems there. First off, you have the wrong driver for the Nvidia GPU installed. You need the 390 legacy driver:
```
[   21.262523] NVRM: The NVIDIA NVS 5200M GPU installed in this system is
               NVRM:  supported through the NVIDIA 390.xx Legacy drivers. 
               NVRM:  The 460.73.01 NVIDIA driver will ignore
               NVRM:  this GPU.  Continuing probe...
[   21.262527] NVRM: No NVIDIA GPU found.
```

Second, the integrated Intel GPU is not showing up. Check the "Optimus" setting under the "Video" menu in the BIOS.

Third, you're using an outdated BIOS. I'd recommend updating: [https://www.dell.com/support/home/en-us/drivers/driversdetails?driverid=ng6cn&oscode=w732&productcode=latitude-e6430](https://www.dell.com/support/home/en-us/drivers/driversdetails?driverid=ng6cn&oscode=w732&productcode=latitude-e6430)

---

### Post by riverhawk on 2021-05-09
Hello everyone and thanks for the replies. I'm too scared to update my BIOS...!

Checking "Optimus" settings under "Video" in BIOS really helped a lot. Opening a video and resizing it, the CPU usage is now around 35-40%, and it doesn't change if I resize to the entire screen. Wow!

Here are some updated outputs...

For: [COLOR=#000000]lspci -nnk | grep -A3 VGA

[/COLOR]```
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
    DeviceName:  Onboard IGD
    Subsystem: Dell 3rd Gen Core processor Graphics Controller [1028:0534]
    Kernel driver in use: i915
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF108GLM [NVS 5200M] [10de:0dfc] (rev a1)
    Subsystem: Dell GF108GLM [NVS 5200M] [1028:1534]
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
01:00.1 Audio device [0403]: NVIDIA Corporation GF108 High Definition Audio Controller [10de:0bea] (rev a1)
```

For: dpkg -l | grep nvidia

```
ii  libnvidia-cfg1-460:amd64                      460.73.01-0ubuntu0.20.04.1            amd64        NVIDIA binary OpenGL/GLX configuration libraryii  libnvidia-common-460                          460.73.01-0ubuntu0.20.04.1            all          Shared files used by the NVIDIA libraries
rc  libnvidia-compute-435:amd64                   455.38-0ubuntu0.18.04.1               amd64        Transitional package for libnvidia-compute-455
rc  libnvidia-compute-455:amd64                   460.32.03-0ubuntu0.18.04.1            amd64        Transitional package for libnvidia-compute-460
ii  libnvidia-compute-460:amd64                   460.73.01-0ubuntu0.20.04.1            amd64        NVIDIA libcompute package
ii  libnvidia-compute-460:i386                    460.73.01-0ubuntu0.20.04.1            i386         NVIDIA libcompute package
ii  libnvidia-decode-460:amd64                    460.73.01-0ubuntu0.20.04.1            amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-460:i386                     460.73.01-0ubuntu0.20.04.1            i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-460:amd64                    460.73.01-0ubuntu0.20.04.1            amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-460:i386                     460.73.01-0ubuntu0.20.04.1            i386         NVENC Video Encoding runtime library
ii  libnvidia-extra-460:amd64                     460.73.01-0ubuntu0.20.04.1            amd64        Extra libraries for the NVIDIA driver
ii  libnvidia-fbc1-460:amd64                      460.73.01-0ubuntu0.20.04.1            amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-460:i386                       460.73.01-0ubuntu0.20.04.1            i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-460:amd64                        460.73.01-0ubuntu0.20.04.1            amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-460:i386                         460.73.01-0ubuntu0.20.04.1            i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-460:amd64                      460.73.01-0ubuntu0.20.04.1            amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  libnvidia-ifr1-460:i386                       460.73.01-0ubuntu0.20.04.1            i386         NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  nvidia-compute-utils-460                      460.73.01-0ubuntu0.20.04.1            amd64        NVIDIA compute utilities
ii  nvidia-dkms-460                               460.73.01-0ubuntu0.20.04.1            amd64        NVIDIA DKMS package
ii  nvidia-driver-435                             455.45.01-0ubuntu0.20.04.1            amd64        Transitional package for nvidia-driver-455
ii  nvidia-driver-455                             460.73.01-0ubuntu0.20.04.1            amd64        Transitional package for nvidia-driver-460
ii  nvidia-driver-460                             460.73.01-0ubuntu0.20.04.1            amd64        NVIDIA driver metapackage
ii  nvidia-kernel-common-460                      460.73.01-0ubuntu0.20.04.1            amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-460                      460.73.01-0ubuntu0.20.04.1            amd64        NVIDIA kernel source package
ii  nvidia-prime                                  0.8.15.3~0.20.04.1                    all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                               440.82-0ubuntu0.20.04.1               amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-460                              460.73.01-0ubuntu0.20.04.1            amd64        NVIDIA driver support binaries
ii  screen-resolution-extra                       0.18build1                            all          Extension for the nvidia-settings control panel
ii  xserver-xorg-video-nvidia-460                 460.73.01-0ubuntu0.20.04.1            amd64        NVIDIA binary Xorg driver

```

Honestly I find all this video stuff very mysterious. I will keep checking back on this thread over the next few days. This has been great help, thanks.

---

### Post by TheFu on 2021-05-10
If you don't update the BIOS, you may never find a solution. It is the first place to start when there is a problem that appears related to hardware.

---

### Post by mikewhatever on 2021-05-10
How did you end up with 3 nvidia drivers installed? Uninstall allbut the recommended one, and hopefully, it should work.

---

### Post by TheFu on 2021-05-10
> **mikewhatever said:**
> How did you end up with 3 nvidia drivers installed? Uninstall allbut the recommended one, and hopefully, it should work.

[LIST=1]
[*]Switch to a different console - non-graphical - and login <cntl>-<alt>-F2
[*]Remove all nvidia stuff - **sudo apt remove  'nvidia-*'**
[*]Install the approved nvidia stuff: **sudo ubuntu-drivers autoinstall**
[*]Reboot. **sudo reboot**
[/LIST]

**Two example systems below:**

```
$ inxi -G
Graphics:  Card: NVIDIA GF108 [GeForce GT 430]
```
Currently running 18.04 and it uses the 390.143 nvidia drivers. This is a "legacy" driver. 

```
$ inxi -G
Graphics:  Card: NVIDIA GP108 [GeForce GT 1030]
```
Currently running 18.04, it uses the 460.73 nvidia drivers.

---

### Post by riverhawk on 2021-05-10
@TheFu Thanks, I will look into updating the BIOS. I've been taking notes on this thread and will follow up more when I can put aside the time.

I got a reply after posting a bug report as recommended here: 

> VLC and Mplayer do not enable hardware acceleration by default that I know of. So high CPU is expected. Please try using 'mpv' for the most performant experience.


Changed Multimedia engine in SMPlayer to /usr/bin/mpv and now CPU usage is around 10%. Overall with that change plus some other changes suggested here previously, everything's great. I'm very impressed.

Reinstalled the drivers, as suggested. Here is some output...

For: inxi -G

```

Graphics:  Device-1: Intel 3rd Gen Core processor Graphics driver: i915 v: kernel 
           Device-2: NVIDIA GF108GLM [NVS 5200M] driver: N/A 
           Display: x11 server: X.Org 1.20.9 driver: modesetting unloaded: fbdev,vesa resolution: 1600x900~60Hz 
           OpenGL: renderer: Mesa DRI Intel HD Graphics 4000 (IVB GT2) v: 4.2 Mesa 20.2.6 

```

For: [COLOR=#000000]dpkg -l | grep nvidia

[/COLOR]```
ii  libnvidia-cfg1-435:amd64                      435.21-0ubuntu7                       amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-435                          435.21-0ubuntu7                       all          Shared files used by the NVIDIA libraries
ii  libnvidia-compute-435:amd64                   435.21-0ubuntu7                       amd64        NVIDIA libcompute package
ii  libnvidia-compute-435:i386                    435.21-0ubuntu7                       i386         NVIDIA libcompute package
rc  libnvidia-compute-455:amd64                   460.32.03-0ubuntu0.18.04.1            amd64        Transitional package for libnvidia-compute-460
rc  libnvidia-compute-460:amd64                   460.73.01-0ubuntu0.20.04.1            amd64        NVIDIA libcompute package
ii  libnvidia-decode-435:amd64                    435.21-0ubuntu7                       amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-435:i386                     435.21-0ubuntu7                       i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-435:amd64                    435.21-0ubuntu7                       amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-435:i386                     435.21-0ubuntu7                       i386         NVENC Video Encoding runtime library
ii  libnvidia-fbc1-435:amd64                      435.21-0ubuntu7                       amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-435:i386                       435.21-0ubuntu7                       i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-435:amd64                        435.21-0ubuntu7                       amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-435:i386                         435.21-0ubuntu7                       i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-435:amd64                      435.21-0ubuntu7                       amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  libnvidia-ifr1-435:i386                       435.21-0ubuntu7                       i386         NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  nvidia-compute-utils-435                      435.21-0ubuntu7                       amd64        NVIDIA compute utilities
rc  nvidia-compute-utils-460                      460.73.01-0ubuntu0.20.04.1            amd64        NVIDIA compute utilities
ii  nvidia-dkms-435                               435.21-0ubuntu7                       amd64        NVIDIA DKMS package
rc  nvidia-dkms-460                               460.73.01-0ubuntu0.20.04.1            amd64        NVIDIA DKMS package
ii  nvidia-driver-435                             435.21-0ubuntu7                       amd64        NVIDIA driver metapackage
ii  nvidia-kernel-common-435                      435.21-0ubuntu7                       amd64        Shared files used with the kernel module
rc  nvidia-kernel-common-460                      460.73.01-0ubuntu0.20.04.1            amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-435                      435.21-0ubuntu7                       amd64        NVIDIA kernel source package
ii  nvidia-prime                                  0.8.14                                all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                               440.64-0ubuntu1                       amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-435                              435.21-0ubuntu7                       amd64        NVIDIA driver support binaries
ii  screen-resolution-extra                       0.18build1                            all          Extension for the nvidia-settings control panel
ii  xserver-xorg-video-nvidia-435                 435.21-0ubuntu7                       amd64        NVIDIA binary Xorg driver

```

[COLOR=#000000]Will keep checking back on this thread, or I can mark it solved. I really appreciate everyone's time. Thank you!
[/COLOR]

---

