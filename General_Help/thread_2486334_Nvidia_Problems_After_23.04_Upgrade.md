---
title: "Nvidia Problems After 23.04 Upgrade"
date: 2023-04-26
forum: General Help
---

### Post by criageek on 2023-04-26
I just upgraded to 23.04.  Initially I couldn't log into the new kernel (6.2.0-20-generic).  I logged into the previous kernel and fiddled around with Nvidia drivers...I did this:  [https://www.youtube.com/watch?v=VP-R7LNSJXA](https://www.youtube.com/watch?v=VP-R7LNSJXA) to install the drivers from the Nvidia site.  Once I did that I was no longer able to log into that kernel, but surprisingly, I can log into the new kernel now.  But the graphics are messed up...some windows/apps (such as a VirtualBox guest) are quite a bit smaller than they should be and the fonts are barely readable they are so small, while others are closer to the right size, but the fonts are not right...they are the wrong font and are slightly larger than they should be.  I'm quite certain this is a problem with the Nvidia drivers but don't know what to do about it.  When I first logged into the older kernel, it was the same situation I am in now with the new kernel...some apps and fonts way too small and some a little too large.  So I'm hesitant to try loading the drivers from the Nvidia website in the new kernel, since that resulted in being unable to log into the older kernel.

I know that's pretty convoluted but I hope it makes sense.  Anyway, last summer I was having some issues and the people helping me wanted me to run some commands and post the results, so I've run those same commands again and here are the results:

nvidia-smi
```
Wed Apr 26 10:35:44 2023       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 525.105.17   Driver Version: 525.105.17   CUDA Version: 12.0     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  NVIDIA GeForce ...  Off  | 00000000:01:00.0  On |                  N/A |
| N/A   40C    P0    N/A /  30W |   1783MiB /  2048MiB |     14%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================|
|    0   N/A  N/A      2099      G   /usr/lib/xorg/Xorg                937MiB |
|    0   N/A  N/A      2208      G   ...mviewer/tv_bin/TeamViewer        0MiB |
|    0   N/A  N/A      2258      G   /usr/bin/gnome-shell              262MiB |
|    0   N/A  N/A      2274      G   ...libexec/mutter-x11-frames      239MiB |
|    0   N/A  N/A      2951      G   ...oud-3.6.1-x86_64.AppImage        0MiB |
|    0   N/A  N/A      4763      G   ...687825567114718178,131072      273MiB |
+-----------------------------------------------------------------------------+

```

inxi -G
```
Graphics:  Device-1: NVIDIA GP108 [GeForce GT 1030] driver: nvidia v: 525.105.17
  Display: x11 server: X.Org v: 1.21.1.7 with: Xwayland v: 22.1.8 driver: X:
    loaded: nvidia unloaded: modesetting gpu: nvidia,nvidia-nvswitch
    resolution: 6144x3456~30Hz
  API: OpenGL v: 4.6.0 NVIDIA 525.105.17 renderer: NVIDIA GeForce GT
    1030/PCIe/SSE2
```

grep "X Driver" /var/log/Xorg.0.log
Nothing found

modinfo /usr/lib/modules/$(uname -r)/kernel/drivers/video/nvidia.ko | grep ^version
```
modinfo: ERROR: Module /usr/lib/modules/6.2.0-20-generic/kernel/drivers/video/nvidia.ko not found.
```


So what's my next step?

Thanks,
Rich

---

### Post by criageek on 2023-04-28
I need to bump this.  My system is quite slow.  And besides the graphics being wonky, now the audio is nasty.  Don't know if that's related or not.

Thanks,
Rich

---

### Post by criageek on 2023-04-29
I decided to change the title of this thread to see if I can attract any interest.  Any help appreciated!

Rich

---

### Post by Bashing-om on 2023-04-29
criageek  - Hey hey

Ouch: Please note what Nvidia says:
> 
Note that many Linux distributions provide their own packages of the NVIDIA Linux Graphics Driver in the distribution's native package management format. This may interact better with the rest of your distribution's framework, and you may want to use this rather than NVIDIA's official package.

[https://www.nvidia.com/Download/driverResults.aspx/204639/en-us/](https://www.nvidia.com/Download/driverResults.aspx/204639/en-us/)

To that end may I suggest that you purge the OEM driver:
```

sudo find / -name "NVIDIA-Linux-*"
sudo <NVIDIA-Linux-x86_64-331.38.run> --uninstall ## where the driver version from the find command is to be substituted and these brackets removed.

```

As Nvidia and Wayland are still having growing pains - may I also suggest that with Nvidia graphics issues that you employ the legacy Xorg compositor - OR run the open source nouveau driver with Wayland ?

Install the repository version driver:
in bios disable secure boot - as the driver is 3rd party
then run in terminal:
```

sudo apt update
sudo apt upgrade
sudo ubuntu-drivers autoinstall

```
where I expect the kernel to choose to install the 525 version driver.

reboot to see the effect.

-hope this helps-

---

### Post by criageek on 2023-04-29
Thanks Bashing-om!  I'm not at that pc right now but I'll give your suggestions a try when I get a chance.

Thanks for your help  :)

Rich

---

### Post by criageek on 2023-04-30
I just ran ```
sudo find / -name "NVIDIA-Linux-*"
``` and it found nothing.  Is it safe to go ahead and install the repository version of the driver?

Thanks,
Rich

---

### Post by criageek on 2023-04-30
I found this website that details how to remove all installed Nvidia packages:  [https://fedingo.com/how-to-uninstall-nvidia-drivers-in-ubuntu/](https://fedingo.com/how-to-uninstall-nvidia-drivers-in-ubuntu/)

Following their suggestion to search for installed Nvidia packages I ran ```
sudo dpkg -l | grep -i nvidia
``` which resulted in this:

```
ii  libnvidia-cfg1-525:amd64                                    525.105.17-0ubuntu1                     amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-525                                        525.105.17-0ubuntu1                     all          Shared files used by the NVIDIA libraries
rc  libnvidia-compute-470:amd64                                 470.129.06-0ubuntu0.22.04.1             amd64        NVIDIA libcompute package
rc  libnvidia-compute-510:amd64                                 510.108.03-0ubuntu2                     amd64        NVIDIA libcompute package
ii  libnvidia-compute-525:amd64                                 525.105.17-0ubuntu1                     amd64        NVIDIA libcompute package
ii  libnvidia-compute-525:i386                                  525.105.17-0ubuntu1                     i386         NVIDIA libcompute package
ii  libnvidia-decode-525:amd64                                  525.105.17-0ubuntu1                     amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-525:i386                                   525.105.17-0ubuntu1                     i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-egl-wayland1:amd64                                1:1.1.10-1                              amd64        Wayland EGL External Platform library -- shared library
ii  libnvidia-encode-525:amd64                                  525.105.17-0ubuntu1                     amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-525:i386                                   525.105.17-0ubuntu1                     i386         NVENC Video Encoding runtime library
ii  libnvidia-extra-525:amd64                                   525.105.17-0ubuntu1                     amd64        Extra libraries for the NVIDIA driver
ii  libnvidia-fbc1-525:amd64                                    525.105.17-0ubuntu1                     amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-525:i386                                     525.105.17-0ubuntu1                     i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-525:amd64                                      525.105.17-0ubuntu1                     amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-525:i386                                       525.105.17-0ubuntu1                     i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
rc  linux-modules-nvidia-470-5.11.0-31-generic                  5.11.0-31.33                            amd64        Linux kernel nvidia modules for version 5.11.0-31
rc  linux-modules-nvidia-470-5.11.0-36-generic                  5.11.0-36.40                            amd64        Linux kernel nvidia modules for version 5.11.0-36
rc  linux-modules-nvidia-470-5.11.0-37-generic                  5.11.0-37.41                            amd64        Linux kernel nvidia modules for version 5.11.0-37
rc  linux-modules-nvidia-470-5.11.0-38-generic                  5.11.0-38.42                            amd64        Linux kernel nvidia modules for version 5.11.0-38
rc  linux-modules-nvidia-470-5.13.0-20-generic                  5.13.0-20.20                            amd64        Linux kernel nvidia modules for version 5.13.0-20
rc  linux-modules-nvidia-470-5.13.0-21-generic                  5.13.0-21.21+1                          amd64        Linux kernel nvidia modules for version 5.13.0-21
rc  linux-modules-nvidia-470-5.13.0-22-generic                  5.13.0-22.22+2                          amd64        Linux kernel nvidia modules for version 5.13.0-22
rc  linux-modules-nvidia-470-5.13.0-23-generic                  5.13.0-23.23+1                          amd64        Linux kernel nvidia modules for version 5.13.0-23
rc  linux-modules-nvidia-470-5.13.0-25-generic                  5.13.0-25.26                            amd64        Linux kernel nvidia modules for version 5.13.0-25
rc  linux-modules-nvidia-470-5.13.0-27-generic                  5.13.0-27.29                            amd64        Linux kernel nvidia modules for version 5.13.0-27
rc  linux-modules-nvidia-470-5.13.0-28-generic                  5.13.0-28.31+1                          amd64        Linux kernel nvidia modules for version 5.13.0-28
rc  linux-modules-nvidia-470-5.13.0-30-generic                  5.13.0-30.33                            amd64        Linux kernel nvidia modules for version 5.13.0-30
rc  linux-modules-nvidia-470-5.13.0-35-generic                  5.13.0-35.40                            amd64        Linux kernel nvidia modules for version 5.13.0-35
rc  linux-modules-nvidia-470-5.13.0-37-generic                  5.13.0-37.42                            amd64        Linux kernel nvidia modules for version 5.13.0-37
rc  linux-modules-nvidia-470-5.13.0-39-generic                  5.13.0-39.44                            amd64        Linux kernel nvidia modules for version 5.13.0-39
rc  linux-modules-nvidia-470-5.13.0-40-generic                  5.13.0-40.45                            amd64        Linux kernel nvidia modules for version 5.13.0-40
rc  linux-modules-nvidia-470-5.15.0-27-generic                  5.15.0-27.28                            amd64        Linux kernel nvidia modules for version 5.15.0-27
rc  linux-modules-nvidia-470-5.15.0-30-generic                  5.15.0-30.31+1                          amd64        Linux kernel nvidia modules for version 5.15.0-30
rc  linux-modules-nvidia-470-5.15.0-33-generic                  5.15.0-33.34                            amd64        Linux kernel nvidia modules for version 5.15.0-33
rc  linux-modules-nvidia-470-5.15.0-35-generic                  5.15.0-35.36+1                          amd64        Linux kernel nvidia modules for version 5.15.0-35
rc  linux-modules-nvidia-470-5.15.0-37-generic                  5.15.0-37.39                            amd64        Linux kernel nvidia modules for version 5.15.0-37
rc  linux-modules-nvidia-470-5.15.0-39-generic                  5.15.0-39.42                            amd64        Linux kernel nvidia modules for version 5.15.0-39
rc  linux-modules-nvidia-510-5.15.0-40-generic                  5.15.0-40.43+1                          amd64        Linux kernel nvidia modules for version 5.15.0-40
rc  linux-modules-nvidia-510-5.15.0-41-generic                  5.15.0-41.44+1                          amd64        Linux kernel nvidia modules for version 5.15.0-41
rc  linux-modules-nvidia-510-5.15.0-52-generic                  5.15.0-52.58+1                          amd64        Linux kernel nvidia modules for version 5.15.0-52
rc  linux-modules-nvidia-510-5.19.0-23-generic                  5.19.0-23.24+1                          amd64        Linux kernel nvidia modules for version 5.19.0-23
rc  linux-modules-nvidia-510-5.19.0-26-generic                  5.19.0-26.27+1                          amd64        Linux kernel nvidia modules for version 5.19.0-26
rc  linux-modules-nvidia-510-5.19.0-28-generic                  5.19.0-28.29                            amd64        Linux kernel nvidia modules for version 5.19.0-28
rc  linux-modules-nvidia-510-5.19.0-29-generic                  5.19.0-29.30+1                          amd64        Linux kernel nvidia modules for version 5.19.0-29
rc  linux-modules-nvidia-510-5.19.0-31-generic                  5.19.0-31.32                            amd64        Linux kernel nvidia modules for version 5.19.0-31
rc  linux-modules-nvidia-510-5.19.0-35-generic                  5.19.0-35.36                            amd64        Linux kernel nvidia modules for version 5.19.0-35
rc  linux-modules-nvidia-510-5.19.0-38-generic                  5.19.0-38.39+1                          amd64        Linux kernel nvidia modules for version 5.19.0-38
rc  linux-modules-nvidia-510-5.19.0-40-generic                  5.19.0-40.41+1                          amd64        Linux kernel nvidia modules for version 5.19.0-40
rc  linux-modules-nvidia-510-6.2.0-20-generic                   6.2.0-20.20                             amd64        Linux kernel nvidia modules for version 6.2.0-20
ii  linux-modules-nvidia-525-6.2.0-20-generic                   6.2.0-20.20                             amd64        Linux kernel nvidia modules for version 6.2.0-20
ii  linux-modules-nvidia-525-generic-hwe-22.04                  6.2.0-20.20                             amd64        Extra drivers for nvidia-525 for the generic-hwe-22.04 flavour
rc  linux-objects-nvidia-470-5.11.0-36-generic                  5.11.0-36.40                            amd64        Linux kernel nvidia modules for version 5.11.0-36 (objects)
rc  linux-objects-nvidia-470-5.11.0-38-generic                  5.11.0-38.42                            amd64        Linux kernel nvidia modules for version 5.11.0-38 (objects)
rc  linux-objects-nvidia-470-5.13.0-20-generic                  5.13.0-20.20                            amd64        Linux kernel nvidia modules for version 5.13.0-20 (objects)
rc  linux-objects-nvidia-470-5.13.0-21-generic                  5.13.0-21.21+1                          amd64        Linux kernel nvidia modules for version 5.13.0-21 (objects)
rc  linux-objects-nvidia-470-5.13.0-22-generic                  5.13.0-22.22+2                          amd64        Linux kernel nvidia modules for version 5.13.0-22 (objects)
rc  linux-objects-nvidia-470-5.13.0-23-generic                  5.13.0-23.23+1                          amd64        Linux kernel nvidia modules for version 5.13.0-23 (objects)
rc  linux-objects-nvidia-470-5.13.0-25-generic                  5.13.0-25.26                            amd64        Linux kernel nvidia modules for version 5.13.0-25 (objects)
rc  linux-objects-nvidia-470-5.13.0-27-generic                  5.13.0-27.29                            amd64        Linux kernel nvidia modules for version 5.13.0-27 (objects)
rc  linux-objects-nvidia-470-5.13.0-28-generic                  5.13.0-28.31+1                          amd64        Linux kernel nvidia modules for version 5.13.0-28 (objects)
rc  linux-objects-nvidia-470-5.13.0-30-generic                  5.13.0-30.33                            amd64        Linux kernel nvidia modules for version 5.13.0-30 (objects)
rc  linux-objects-nvidia-470-5.13.0-35-generic                  5.13.0-35.40                            amd64        Linux kernel nvidia modules for version 5.13.0-35 (objects)
rc  linux-objects-nvidia-470-5.13.0-37-generic                  5.13.0-37.42                            amd64        Linux kernel nvidia modules for version 5.13.0-37 (objects)
rc  linux-objects-nvidia-470-5.13.0-39-generic                  5.13.0-39.44                            amd64        Linux kernel nvidia modules for version 5.13.0-39 (objects)
rc  linux-objects-nvidia-470-5.13.0-40-generic                  5.13.0-40.45                            amd64        Linux kernel nvidia modules for version 5.13.0-40 (objects)
rc  linux-objects-nvidia-470-5.15.0-30-generic                  5.15.0-30.31+1                          amd64        Linux kernel nvidia modules for version 5.15.0-30 (objects)
rc  linux-objects-nvidia-470-5.15.0-33-generic                  5.15.0-33.34                            amd64        Linux kernel nvidia modules for version 5.15.0-33 (objects)
rc  linux-objects-nvidia-470-5.15.0-35-generic                  5.15.0-35.36+1                          amd64        Linux kernel nvidia modules for version 5.15.0-35 (objects)
rc  linux-objects-nvidia-470-5.15.0-37-generic                  5.15.0-37.39                            amd64        Linux kernel nvidia modules for version 5.15.0-37 (objects)
rc  linux-objects-nvidia-510-5.15.0-41-generic                  5.15.0-41.44+1                          amd64        Linux kernel nvidia modules for version 5.15.0-41 (objects)
rc  linux-objects-nvidia-510-5.15.0-52-generic                  5.15.0-52.58+1                          amd64        Linux kernel nvidia modules for version 5.15.0-52 (objects)
rc  linux-objects-nvidia-510-5.19.0-23-generic                  5.19.0-23.24+1                          amd64        Linux kernel nvidia modules for version 5.19.0-23 (objects)
rc  linux-objects-nvidia-510-5.19.0-26-generic                  5.19.0-26.27+1                          amd64        Linux kernel nvidia modules for version 5.19.0-26 (objects)
rc  linux-objects-nvidia-510-5.19.0-28-generic                  5.19.0-28.29                            amd64        Linux kernel nvidia modules for version 5.19.0-28 (objects)
rc  linux-objects-nvidia-510-5.19.0-29-generic                  5.19.0-29.30+1                          amd64        Linux kernel nvidia modules for version 5.19.0-29 (objects)
rc  linux-objects-nvidia-510-5.19.0-31-generic                  5.19.0-31.32                            amd64        Linux kernel nvidia modules for version 5.19.0-31 (objects)
rc  linux-objects-nvidia-510-5.19.0-35-generic                  5.19.0-35.36                            amd64        Linux kernel nvidia modules for version 5.19.0-35 (objects)
rc  linux-objects-nvidia-510-5.19.0-38-generic                  5.19.0-38.39+1                          amd64        Linux kernel nvidia modules for version 5.19.0-38 (objects)
ii  linux-objects-nvidia-510-5.19.0-40-generic                  5.19.0-40.41+1                          amd64        Linux kernel nvidia modules for version 5.19.0-40 (objects)
ii  linux-objects-nvidia-510-6.2.0-20-generic                   6.2.0-20.20                             amd64        Linux kernel nvidia modules for version 6.2.0-20 (objects)
ii  linux-objects-nvidia-525-6.2.0-20-generic                   6.2.0-20.20                             amd64        Linux kernel nvidia modules for version 6.2.0-20 (objects)
ii  linux-signatures-nvidia-5.19.0-40-generic                   5.19.0-40.41+1                          amd64        Linux kernel signatures for nvidia modules for version 5.19.0-40-generic
ii  linux-signatures-nvidia-6.2.0-20-generic                    6.2.0-20.20                             amd64        Linux kernel signatures for nvidia modules for version 6.2.0-20-generic
rc  nvidia-compute-utils-470                                    470.129.06-0ubuntu0.22.04.1             amd64        NVIDIA compute utilities
rc  nvidia-compute-utils-510                                    510.108.03-0ubuntu2                     amd64        NVIDIA compute utilities
ii  nvidia-compute-utils-525                                    525.105.17-0ubuntu1                     amd64        NVIDIA compute utilities
rc  nvidia-dkms-470                                             470.129.06-0ubuntu0.22.04.1             amd64        NVIDIA DKMS package
ii  nvidia-driver-525                                           525.105.17-0ubuntu1                     amd64        NVIDIA driver metapackage
rc  nvidia-kernel-common-470                                    470.129.06-0ubuntu0.22.04.1             amd64        Shared files used with the kernel module
rc  nvidia-kernel-common-510                                    510.108.03-0ubuntu2                     amd64        Shared files used with the kernel module
ii  nvidia-kernel-common-525                                    525.105.17-0ubuntu1                     amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-525                                    525.105.17-0ubuntu1                     amd64        NVIDIA kernel source package
ii  nvidia-prime                                                0.8.17.1                                all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                                             510.47.03-0ubuntu1                      amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-525                                            525.105.17-0ubuntu1                     amd64        NVIDIA driver support binaries
ii  screen-resolution-extra                                     0.18.3                                  all          Extension for the nvidia-settings control panel
ii  xserver-xorg-video-nvidia-525                               525.105.17-0ubuntu1                     amd64        NVIDIA binary Xorg driver

```
Is it safe to remove all of these by running this command as they suggest?
```
sudo apt-get remove --purge '^nvidia-.*'
```

Thanks,
Rich

---

### Post by #&amp;thj^% on 2023-04-30
> **criageek said:**
> 
Is it safe to remove all of these by running this command as they suggest?
```
sudo apt-get remove --purge '^nvidia-.*'
```

Thanks,
Rich

Yes that will work:
```
sudo apt-get remove --purge '^nvidia-.*' -s
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Note, selecting 'nvidia-cuda-toolkit-doc' for regex '^nvidia-.*'
Note, selecting 'nvidia-dkms-450-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-390' for regex '^nvidia-.*'
Note, selecting 'nvidia-cuda-toolkit-gcc' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-418' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-430' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-435' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-440' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-450' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-455' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-460' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-465' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-470' for regex '^nvidia-.*'
Note, selecting 'nvidia-dkms-470-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-495' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-510' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-515' for regex '^nvidia-.*'
Note, selecting 'nvidia-compute-utils-515-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-520' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-525' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-530' for regex '^nvidia-.*'
Note, selecting 'nvidia-driver-440-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-fabricmanager-dev' for regex '^nvidia-.*'
Note, selecting 'nvidia-driver-460-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-primus-vk-common' for regex '^nvidia-.*'
Note, selecting 'nvidia-opencl-dev' for regex '^nvidia-.*'
Note, selecting 'nvidia-open-kernel-dkms-any' for regex '^nvidia-.*'
Note, selecting 'nvidia-cg-toolkit' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-common-525-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-dkms-510-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-libopencl1-dev' for regex '^nvidia-.*'
Note, selecting 'nvidia-texture-tools' for regex '^nvidia-.*'
Note, selecting 'nvidia-driver-525-open' for regex '^nvidia-.*'
Note, selecting 'nvidia-opencl-icd' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-450-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-compute-utils-390' for regex '^nvidia-.*'
Note, selecting 'nvidia-utils' for regex '^nvidia-.*'
Note, selecting 'nvidia-compute-utils-418' for regex '^nvidia-.*'
Note, selecting 'nvidia-compute-utils-430' for regex '^nvidia-.*'
Note, selecting 'nvidia-compute-utils-435' for regex '^nvidia-.*'
Note, selecting 'nvidia-compute-utils-440' for regex '^nvidia-.*'
Note, selecting 'nvidia-compute-utils-450' for regex '^nvidia-.*'
Note, selecting 'nvidia-compute-utils-455' for regex '^nvidia-.*'
Note, selecting 'nvidia-compute-utils-460' for regex '^nvidia-.*'
Note, selecting 'nvidia-compute-utils-465' for regex '^nvidia-.*'
Note, selecting 'nvidia-compute-utils-470' for regex '^nvidia-.*'
Note, selecting 'nvidia-compute-utils-495' for regex '^nvidia-.*'
Note, selecting 'nvidia-dkms-390' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-470-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-compute-utils-510' for regex '^nvidia-.*'
Note, selecting 'nvidia-compute-utils-515' for regex '^nvidia-.*'
Note, selecting 'nvidia-compute-utils-520' for regex '^nvidia-.*'
Note, selecting 'nvidia-compute-utils-525' for regex '^nvidia-.*'
Note, selecting 'nvidia-compute-utils-530' for regex '^nvidia-.*'
Note, selecting 'nvidia-dkms-418' for regex '^nvidia-.*'
Note, selecting 'nvidia-dkms-430' for regex '^nvidia-.*'
Note, selecting 'nvidia-dkms-435' for regex '^nvidia-.*'
Note, selecting 'nvidia-dkms-440' for regex '^nvidia-.*'
Note, selecting 'nvidia-dkms-450' for regex '^nvidia-.*'
Note, selecting 'nvidia-dkms-455' for regex '^nvidia-.*'
Note, selecting 'nvidia-dkms-460' for regex '^nvidia-.*'
Note, selecting 'nvidia-dkms-465' for regex '^nvidia-.*'
Note, selecting 'nvidia-dkms-470' for regex '^nvidia-.*'
Note, selecting 'nvidia-dkms-495' for regex '^nvidia-.*'
Note, selecting 'nvidia-dkms-510' for regex '^nvidia-.*'
Note, selecting 'nvidia-dkms-515' for regex '^nvidia-.*'
Note, selecting 'nvidia-dkms-520' for regex '^nvidia-.*'
Note, selecting 'nvidia-dkms-525' for regex '^nvidia-.*'
Note, selecting 'nvidia-dkms-530' for regex '^nvidia-.*'
Note, selecting 'nvidia-driver-390' for regex '^nvidia-.*'
Note, selecting 'nvidia-driver-418' for regex '^nvidia-.*'
Note, selecting 'nvidia-driver-430' for regex '^nvidia-.*'
Note, selecting 'nvidia-driver-435' for regex '^nvidia-.*'
Note, selecting 'nvidia-driver-440' for regex '^nvidia-.*'
Note, selecting 'nvidia-driver-450' for regex '^nvidia-.*'
Note, selecting 'nvidia-driver-455' for regex '^nvidia-.*'
Note, selecting 'nvidia-driver-460' for regex '^nvidia-.*'
Note, selecting 'nvidia-driver-465' for regex '^nvidia-.*'
Note, selecting 'nvidia-driver-470' for regex '^nvidia-.*'
Note, selecting 'nvidia-driver-495' for regex '^nvidia-.*'
Note, selecting 'nvidia-driver-510' for regex '^nvidia-.*'
Note, selecting 'nvidia-driver-515' for regex '^nvidia-.*'
Note, selecting 'nvidia-driver-520' for regex '^nvidia-.*'
Note, selecting 'nvidia-driver-525' for regex '^nvidia-.*'
Note, selecting 'nvidia-driver-530' for regex '^nvidia-.*'
Note, selecting 'nvidia-dkms-440-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-dkms-460-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-510-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-no-dkms-515-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-dkms-520-open' for regex '^nvidia-.*'
Note, selecting 'nvidia-driver-450-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-driver-470-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-primus-vk-wrapper' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-common-515-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-vaapi-driver' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-440-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-460-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-utils-390' for regex '^nvidia-.*'
Note, selecting 'nvidia-utils-418' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-dkms-any' for regex '^nvidia-.*'
Note, selecting 'nvidia-utils-430' for regex '^nvidia-.*'
Note, selecting 'nvidia-utils-435' for regex '^nvidia-.*'
Note, selecting 'nvidia-utils-440' for regex '^nvidia-.*'
Note, selecting 'nvidia-utils-450' for regex '^nvidia-.*'
Note, selecting 'nvidia-utils-455' for regex '^nvidia-.*'
Note, selecting 'nvidia-utils-460' for regex '^nvidia-.*'
Note, selecting 'nvidia-utils-465' for regex '^nvidia-.*'
Note, selecting 'nvidia-utils-470' for regex '^nvidia-.*'
Note, selecting 'nvidia-utils-495' for regex '^nvidia-.*'
Note, selecting 'nvidia-utils-510' for regex '^nvidia-.*'
Note, selecting 'nvidia-utils-515' for regex '^nvidia-.*'
Note, selecting 'nvidia-utils-520' for regex '^nvidia-.*'
Note, selecting 'nvidia-utils-525' for regex '^nvidia-.*'
Note, selecting 'nvidia-utils-530' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-source-510-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-source-530-open' for regex '^nvidia-.*'
Note, selecting 'nvidia-egl-wayland-common' for regex '^nvidia-.*'
Note, selecting 'nvidia-utils-525-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-515-open' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-no-dkms-525-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-source-440-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-source-460-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-source-515-open' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-no-dkms-530-open' for regex '^nvidia-.*'
Note, selecting 'nvidia-utils-515-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-dkms-525-open' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-no-dkms-515-open' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-530-open' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-source-450-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-legacy-390xx-opencl-icd' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-source-470-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-profiler' for regex '^nvidia-.*'
Note, selecting 'nvidia-current-updates' for regex '^nvidia-.*'
Note, selecting 'nvidia-compute-utils-510-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-visual-profiler' for regex '^nvidia-.*'
Note, selecting 'nvidia-dkms-515-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-common-390' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-common-418' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-common-430' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-common-435' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-common-440' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-common-450' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-common-455' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-common-460' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-common-465' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-common-470' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-common-495' for regex '^nvidia-.*'
Note, selecting 'nvidia-legacy-390xx-smi' for regex '^nvidia-.*'
Note, selecting 'nvidia-prebuilt-kernel' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-common-510' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-common-515' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-common-520' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-common-525' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-common-530' for regex '^nvidia-.*'
Note, selecting 'nvidia-driver-418-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-current' for regex '^nvidia-.*'
Note, selecting 'nvidia-compute-utils' for regex '^nvidia-.*'
Note, selecting 'nvidia-driver-525-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-common' for regex '^nvidia-.*'
Note, selecting 'nvidia-compute-utils-440-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-driver-515-open' for regex '^nvidia-.*'
Note, selecting 'nvidia-compute-utils-460-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-cuda-dev' for regex '^nvidia-.*'
Note, selecting 'nvidia-cuda-doc' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-515-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-fabricmanager' for regex '^nvidia-.*'
Note, selecting 'nvidia-cuda-gdb' for regex '^nvidia-.*'
Note, selecting 'nvidia-340-dev' for regex '^nvidia-.*'
Note, selecting 'nvidia-cuda-toolkit' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-no-dkms-510-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-dkms-525-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-prime' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-common-510-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-driver-515-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-dkms-515-open' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-520-open' for regex '^nvidia-.*'
Note, selecting 'nvidia-opencl-icd-340' for regex '^nvidia-.*'
Note, selecting 'nvidia-opencl-icd-384' for regex '^nvidia-.*'
Note, selecting 'nvidia-compute-utils-450-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-340' for regex '^nvidia-.*'
Note, selecting 'nvidia-384' for regex '^nvidia-.*'
Note, selecting 'nvidia-390' for regex '^nvidia-.*'
Note, selecting 'nvidia-fs-dkms' for regex '^nvidia-.*'
Note, selecting 'nvidia-compute-utils-470-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-common-440-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-340-uvm' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-525-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-common-460-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-driver-530-open' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-source-520-open' for regex '^nvidia-.*'
Note, selecting 'nvidia-settings' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-no-dkms-390' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-no-dkms-418' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-no-dkms-430' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-no-dkms-435' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-no-dkms-440' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-no-dkms-450' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-no-dkms-455' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-no-dkms-460' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-no-dkms-465' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-no-dkms-470' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-no-dkms-495' for regex '^nvidia-.*'
Note, selecting 'nvidia-cudnn' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-no-dkms-510' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-no-dkms-515' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-no-dkms-520' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-no-dkms-525' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-no-dkms-530' for regex '^nvidia-.*'
Note, selecting 'nvidia-libopencl1' for regex '^nvidia-.*'
Note, selecting 'nvidia-fabricmanager-dev-450' for regex '^nvidia-.*'
Note, selecting 'nvidia-fabricmanager-dev-460' for regex '^nvidia-.*'
Note, selecting 'nvidia-fabricmanager-dev-470' for regex '^nvidia-.*'
Note, selecting 'nvidia-fabricmanager-dev-510' for regex '^nvidia-.*'
Note, selecting 'nvidia-fabricmanager-dev-515' for regex '^nvidia-.*'
Note, selecting 'nvidia-fabricmanager-dev-525' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-source-525-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-no-dkms-450-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-dkms-530-open' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-no-dkms-470-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-no-dkms-520-open' for regex '^nvidia-.*'
Note, selecting 'nvidia-cuda-samples' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-common-450-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-common-470-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-utils-510-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-fabricmanager-450' for regex '^nvidia-.*'
Note, selecting 'nvidia-fabricmanager-460' for regex '^nvidia-.*'
Note, selecting 'nvidia-fabricmanager-470' for regex '^nvidia-.*'
Note, selecting 'nvidia-fabricmanager-510' for regex '^nvidia-.*'
Note, selecting 'nvidia-fabricmanager-515' for regex '^nvidia-.*'
Note, selecting 'nvidia-fabricmanager-525' for regex '^nvidia-.*'
Note, selecting 'nvidia-libopencl1-340' for regex '^nvidia-.*'
Note, selecting 'nvidia-libopencl1-384' for regex '^nvidia-.*'
Note, selecting 'nvidia-utils-440-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-source-515-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-source-390' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-no-dkms-440-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-utils-460-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-source-418' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-source-430' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-source-435' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-source-440' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-source-450' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-source-455' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-source-460' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-source-465' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-source-470' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-source-495' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-source-510' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-source-515' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-525-open' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-source-520' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-source-525' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-source-530' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-no-dkms-460-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-driver-520-open' for regex '^nvidia-.*'
Note, selecting 'nvidia-384-dev' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-source-525-open' for regex '^nvidia-.*'
Note, selecting 'nvidia-compute-utils-525-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-utils-450-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-settings-binary' for regex '^nvidia-.*'
Note, selecting 'nvidia-dkms-kernel' for regex '^nvidia-.*'
Note, selecting 'nvidia-modprobe' for regex '^nvidia-.*'
Note, selecting 'nvidia-utils-470-server' for regex '^nvidia-.*'
Note, selecting 'nvidia-cg-dev' for regex '^nvidia-.*'
Note, selecting 'nvidia-cg-doc' for regex '^nvidia-.*'
Note, selecting 'nvidia-kernel-source' for regex '^nvidia-.*'
Note, selecting 'nvidia-common' for regex '^nvidia-.*'
Note, selecting 'nvidia-persistenced' for regex '^nvidia-.*'
Note, selecting 'nvidia-headless-no-dkms-525-open' for regex '^nvidia-.*'
Note, selecting 'nvidia-driver-binary' for regex '^nvidia-.*'
Note, selecting 'nvidia-smi' for regex '^nvidia-.*'
Note, selecting 'nvidia-driver-510-server' for regex '^nvidia-.*'
Package 'nvidia-egl-wayland-common' is not installed, so not removed
Note, selecting 'nvidia-settings' instead of 'nvidia-settings-binary'
Package 'nvidia-390' is not installed, so not removed
Note, selecting 'libnvtt-bin' instead of 'nvidia-texture-tools'
Package 'nvidia-libopencl1-dev' is not installed, so not removed
Package 'nvidia-current' is not installed, so not removed
Package 'nvidia-current-updates' is not installed, so not removed
Package 'nvidia-driver-418-server' is not installed, so not removed
Package 'nvidia-legacy-390xx-opencl-icd' is not installed, so not removed
Package 'nvidia-legacy-390xx-smi' is not installed, so not removed
Package 'nvidia-libopencl1' is not installed, so not removed
Package 'nvidia-cuda-doc' is not installed, so not removed
Package 'nvidia-kernel-dkms-any' is not installed, so not removed
Package 'nvidia-open-kernel-dkms-any' is not installed, so not removed
Package 'nvidia-384' is not installed, so not removed
Package 'nvidia-kernel-common-390' is not installed, so not removed
Package 'nvidia-dkms-390' is not installed, so not removed
Package 'nvidia-kernel-common-450-server' is not installed, so not removed
Package 'nvidia-dkms-450-server' is not installed, so not removed
Package 'nvidia-kernel-common-470' is not installed, so not removed
Package 'nvidia-dkms-470' is not installed, so not removed
Package 'nvidia-kernel-common-470-server' is not installed, so not removed
Package 'nvidia-dkms-470-server' is not installed, so not removed
Package 'nvidia-kernel-common-510' is not installed, so not removed
Package 'nvidia-dkms-510' is not installed, so not removed
Package 'nvidia-kernel-common-515' is not installed, so not removed
Package 'nvidia-dkms-515' is not installed, so not removed
Package 'nvidia-kernel-common-515-server' is not installed, so not removed
Package 'nvidia-dkms-515-server' is not installed, so not removed
Package 'nvidia-kernel-common-525' is not installed, so not removed
Package 'nvidia-dkms-525' is not installed, so not removed
Package 'nvidia-dkms-525-open' is not installed, so not removed
Package 'nvidia-kernel-common-525-server' is not installed, so not removed
Package 'nvidia-dkms-525-server' is not installed, so not removed
Package 'nvidia-340' is not installed, so not removed
Package 'nvidia-340-dev' is not installed, so not removed
Package 'nvidia-340-uvm' is not installed, so not removed
Package 'nvidia-driver-390' is not installed, so not removed
Package 'nvidia-384-dev' is not installed, so not removed
Package 'nvidia-compute-utils-390' is not installed, so not removed
Package 'nvidia-compute-utils-418' is not installed, so not removed
Package 'nvidia-compute-utils-430' is not installed, so not removed
Package 'nvidia-compute-utils-440' is not installed, so not removed
Package 'nvidia-compute-utils-435' is not installed, so not removed
Package 'nvidia-compute-utils-455' is not installed, so not removed
Package 'nvidia-compute-utils-450' is not installed, so not removed
Package 'nvidia-compute-utils-440-server' is not installed, so not removed
Package 'nvidia-compute-utils-450-server' is not installed, so not removed
Package 'nvidia-compute-utils-460' is not installed, so not removed
Package 'nvidia-compute-utils-470' is not installed, so not removed
Package 'nvidia-compute-utils-460-server' is not installed, so not removed
Package 'nvidia-compute-utils-470-server' is not installed, so not removed
Package 'nvidia-compute-utils-465' is not installed, so not removed
Package 'nvidia-compute-utils-495' is not installed, so not removed
Package 'nvidia-compute-utils-510' is not installed, so not removed
Package 'nvidia-compute-utils-510-server' is not installed, so not removed
Package 'nvidia-compute-utils-515-server' is not installed, so not removed
Package 'nvidia-compute-utils-515' is not installed, so not removed
Package 'nvidia-compute-utils-520' is not installed, so not removed
Package 'nvidia-compute-utils-525' is not installed, so not removed
Package 'nvidia-compute-utils-525-server' is not installed, so not removed
Package 'nvidia-kernel-source-390' is not installed, so not removed
Package 'nvidia-dkms-418' is not installed, so not removed
Package 'nvidia-dkms-430' is not installed, so not removed
Package 'nvidia-dkms-440' is not installed, so not removed
Package 'nvidia-dkms-435' is not installed, so not removed
Package 'nvidia-dkms-455' is not installed, so not removed
Package 'nvidia-dkms-450' is not installed, so not removed
Package 'nvidia-dkms-440-server' is not installed, so not removed
Package 'nvidia-dkms-460' is not installed, so not removed
Package 'nvidia-kernel-source-450-server' is not installed, so not removed
Package 'nvidia-dkms-460-server' is not installed, so not removed
Package 'nvidia-dkms-465' is not installed, so not removed
Package 'nvidia-kernel-source-470' is not installed, so not removed
Package 'nvidia-kernel-source-470-server' is not installed, so not removed
Package 'nvidia-dkms-495' is not installed, so not removed
Package 'nvidia-kernel-source-510' is not installed, so not removed
Package 'nvidia-dkms-510-server' is not installed, so not removed
Package 'nvidia-kernel-source-515' is not installed, so not removed
Package 'nvidia-dkms-515-open' is not installed, so not removed
Package 'nvidia-kernel-source-515-open' is not installed, so not removed
Package 'nvidia-kernel-source-515-server' is not installed, so not removed
Package 'nvidia-dkms-520' is not installed, so not removed
Package 'nvidia-dkms-520-open' is not installed, so not removed
Package 'nvidia-kernel-source-525' is not installed, so not removed
Package 'nvidia-kernel-source-525-open' is not installed, so not removed
Package 'nvidia-kernel-source-525-server' is not installed, so not removed
Package 'nvidia-utils-390' is not installed, so not removed
Package 'nvidia-driver-418' is not installed, so not removed
Package 'nvidia-driver-430' is not installed, so not removed
Package 'nvidia-driver-440' is not installed, so not removed
Package 'nvidia-driver-435' is not installed, so not removed
Package 'nvidia-driver-455' is not installed, so not removed
Package 'nvidia-driver-450' is not installed, so not removed
Package 'nvidia-driver-440-server' is not installed, so not removed
Package 'nvidia-driver-450-server' is not installed, so not removed
Package 'nvidia-driver-460' is not installed, so not removed
Package 'nvidia-utils-450-server' is not installed, so not removed
Package 'nvidia-driver-470' is not installed, so not removed
Package 'nvidia-driver-460-server' is not installed, so not removed
Package 'nvidia-driver-470-server' is not installed, so not removed
Package 'nvidia-driver-465' is not installed, so not removed
Package 'nvidia-utils-470' is not installed, so not removed
Package 'nvidia-utils-470-server' is not installed, so not removed
Package 'nvidia-driver-495' is not installed, so not removed
Package 'nvidia-driver-510' is not installed, so not removed
Package 'nvidia-utils-510' is not installed, so not removed
Package 'nvidia-driver-510-server' is not installed, so not removed
Package 'nvidia-driver-515-server' is not installed, so not removed
Package 'nvidia-driver-515' is not installed, so not removed
Package 'nvidia-utils-515' is not installed, so not removed
Package 'nvidia-driver-515-open' is not installed, so not removed
Package 'nvidia-utils-515-server' is not installed, so not removed
Package 'nvidia-driver-520' is not installed, so not removed
Package 'nvidia-driver-525' is not installed, so not removed
Package 'nvidia-driver-520-open' is not installed, so not removed
Package 'nvidia-utils-525' is not installed, so not removed
Package 'nvidia-driver-525-open' is not installed, so not removed
Package 'nvidia-driver-525-server' is not installed, so not removed
Package 'nvidia-utils-525-server' is not installed, so not removed
Package 'nvidia-headless-390' is not installed, so not removed
Package 'nvidia-headless-no-dkms-390' is not installed, so not removed
Package 'nvidia-headless-418' is not installed, so not removed
Package 'nvidia-headless-430' is not installed, so not removed
Package 'nvidia-headless-440' is not installed, so not removed
Package 'nvidia-headless-435' is not installed, so not removed
Package 'nvidia-headless-455' is not installed, so not removed
Package 'nvidia-headless-450' is not installed, so not removed
Package 'nvidia-headless-440-server' is not installed, so not removed
Package 'nvidia-headless-450-server' is not installed, so not removed
Package 'nvidia-headless-460' is not installed, so not removed
Package 'nvidia-headless-no-dkms-450-server' is not installed, so not removed
Package 'nvidia-headless-470' is not installed, so not removed
Package 'nvidia-headless-460-server' is not installed, so not removed
Package 'nvidia-headless-470-server' is not installed, so not removed
Package 'nvidia-headless-465' is not installed, so not removed
Package 'nvidia-headless-no-dkms-470' is not installed, so not removed
Package 'nvidia-headless-no-dkms-470-server' is not installed, so not removed
Package 'nvidia-headless-495' is not installed, so not removed
Package 'nvidia-headless-510' is not installed, so not removed
Package 'nvidia-headless-no-dkms-510' is not installed, so not removed
Package 'nvidia-headless-510-server' is not installed, so not removed
Package 'nvidia-headless-515-server' is not installed, so not removed
Package 'nvidia-headless-515' is not installed, so not removed
Package 'nvidia-headless-no-dkms-515' is not installed, so not removed
Package 'nvidia-headless-515-open' is not installed, so not removed
Package 'nvidia-headless-no-dkms-515-open' is not installed, so not removed
Package 'nvidia-headless-no-dkms-515-server' is not installed, so not removed
Package 'nvidia-headless-520' is not installed, so not removed
Package 'nvidia-headless-525' is not installed, so not removed
Package 'nvidia-headless-520-open' is not installed, so not removed
Package 'nvidia-headless-no-dkms-525' is not installed, so not removed
Package 'nvidia-headless-525-open' is not installed, so not removed
Package 'nvidia-headless-no-dkms-525-open' is not installed, so not removed
Package 'nvidia-headless-525-server' is not installed, so not removed
Package 'nvidia-headless-no-dkms-525-server' is not installed, so not removed
Package 'nvidia-headless-no-dkms-418' is not installed, so not removed
Package 'nvidia-headless-no-dkms-430' is not installed, so not removed
Package 'nvidia-headless-no-dkms-440' is not installed, so not removed
Package 'nvidia-headless-no-dkms-435' is not installed, so not removed
Package 'nvidia-headless-no-dkms-455' is not installed, so not removed
Package 'nvidia-headless-no-dkms-450' is not installed, so not removed
Package 'nvidia-headless-no-dkms-440-server' is not installed, so not removed
Package 'nvidia-headless-no-dkms-460' is not installed, so not removed
Package 'nvidia-headless-no-dkms-460-server' is not installed, so not removed
Package 'nvidia-headless-no-dkms-465' is not installed, so not removed
Package 'nvidia-headless-no-dkms-495' is not installed, so not removed
Package 'nvidia-headless-no-dkms-510-server' is not installed, so not removed
Package 'nvidia-headless-no-dkms-520' is not installed, so not removed
Package 'nvidia-headless-no-dkms-520-open' is not installed, so not removed
Package 'nvidia-kernel-common-418' is not installed, so not removed
Package 'nvidia-kernel-common-430' is not installed, so not removed
Package 'nvidia-kernel-common-440' is not installed, so not removed
Package 'nvidia-kernel-common-435' is not installed, so not removed
Package 'nvidia-kernel-common-455' is not installed, so not removed
Package 'nvidia-kernel-common-450' is not installed, so not removed
Package 'nvidia-kernel-common-440-server' is not installed, so not removed
Package 'nvidia-kernel-common-460' is not installed, so not removed
Package 'nvidia-kernel-common-460-server' is not installed, so not removed
Package 'nvidia-kernel-common-465' is not installed, so not removed
Package 'nvidia-kernel-common-495' is not installed, so not removed
Package 'nvidia-kernel-common-510-server' is not installed, so not removed
Package 'nvidia-kernel-common-520' is not installed, so not removed
Package 'nvidia-kernel-source-418' is not installed, so not removed
Package 'nvidia-kernel-source-430' is not installed, so not removed
Package 'nvidia-kernel-source-440' is not installed, so not removed
Package 'nvidia-kernel-source-435' is not installed, so not removed
Package 'nvidia-kernel-source-455' is not installed, so not removed
Package 'nvidia-kernel-source-450' is not installed, so not removed
Package 'nvidia-kernel-source-440-server' is not installed, so not removed
Package 'nvidia-kernel-source-460' is not installed, so not removed
Package 'nvidia-kernel-source-460-server' is not installed, so not removed
Package 'nvidia-kernel-source-465' is not installed, so not removed
Package 'nvidia-kernel-source-495' is not installed, so not removed
Package 'nvidia-kernel-source-510-server' is not installed, so not removed
Package 'nvidia-kernel-source-520' is not installed, so not removed
Package 'nvidia-kernel-source-520-open' is not installed, so not removed
Package 'nvidia-utils-418' is not installed, so not removed
Package 'nvidia-utils-430' is not installed, so not removed
Package 'nvidia-utils-440' is not installed, so not removed
Package 'nvidia-utils-435' is not installed, so not removed
Package 'nvidia-utils-455' is not installed, so not removed
Package 'nvidia-utils-450' is not installed, so not removed
Package 'nvidia-utils-440-server' is not installed, so not removed
Package 'nvidia-utils-460' is not installed, so not removed
Package 'nvidia-utils-460-server' is not installed, so not removed
Package 'nvidia-utils-465' is not installed, so not removed
Package 'nvidia-utils-495' is not installed, so not removed
Package 'nvidia-utils-510-server' is not installed, so not removed
Package 'nvidia-utils-520' is not installed, so not removed
Package 'nvidia-cuda-toolkit' is not installed, so not removed
Package 'nvidia-cuda-dev' is not installed, so not removed
Package 'nvidia-vaapi-driver' is not installed, so not removed
Package 'nvidia-primus-vk-wrapper' is not installed, so not removed
Package 'nvidia-fabricmanager-450' is not installed, so not removed
Package 'nvidia-fabricmanager-470' is not installed, so not removed
Package 'nvidia-fabricmanager-515' is not installed, so not removed
Package 'nvidia-fabricmanager-525' is not installed, so not removed
Package 'nvidia-cg-toolkit' is not installed, so not removed
Package 'nvidia-opencl-dev' is not installed, so not removed
Package 'nvidia-profiler' is not installed, so not removed
Package 'nvidia-cg-dev' is not installed, so not removed
Package 'nvidia-cg-doc' is not installed, so not removed
Package 'nvidia-cuda-gdb' is not installed, so not removed
Package 'nvidia-cuda-toolkit-doc' is not installed, so not removed
Package 'nvidia-cuda-samples' is not installed, so not removed
Package 'nvidia-visual-profiler' is not installed, so not removed
Package 'nvidia-cuda-toolkit-gcc' is not installed, so not removed
Package 'nvidia-cudnn' is not installed, so not removed
Package 'nvidia-fabricmanager-460' is not installed, so not removed
Package 'nvidia-fabricmanager-510' is not installed, so not removed
Package 'nvidia-fabricmanager-dev-450' is not installed, so not removed
Package 'nvidia-fabricmanager-dev-460' is not installed, so not removed
Package 'nvidia-fabricmanager-dev-470' is not installed, so not removed
Package 'nvidia-fabricmanager-dev-510' is not installed, so not removed
Package 'nvidia-fabricmanager-dev-515' is not installed, so not removed
Package 'nvidia-fabricmanager-dev-525' is not installed, so not removed
Package 'nvidia-fs-dkms' is not installed, so not removed
Package 'nvidia-libopencl1-340' is not installed, so not removed
Package 'nvidia-libopencl1-384' is not installed, so not removed
Package 'nvidia-modprobe' is not installed, so not removed
Package 'nvidia-opencl-icd-340' is not installed, so not removed
Package 'nvidia-opencl-icd-384' is not installed, so not removed
Package 'nvidia-primus-vk-common' is not installed, so not removed
Package 'nvidia-dkms-530-open' is not installed, so not removed
Package 'nvidia-kernel-source-530-open' is not installed, so not removed
Package 'nvidia-driver-530-open' is not installed, so not removed
Package 'nvidia-headless-530' is not installed, so not removed
Package 'nvidia-headless-no-dkms-530' is not installed, so not removed
Package 'nvidia-headless-530-open' is not installed, so not removed
Package 'nvidia-headless-no-dkms-530-open' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libatomic1:i386 libbsd0:i386 libdrm-amdgpu1:i386 libdrm-intel1:i386
  libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386 libedit2:i386
  libelf1:i386 libexpat1:i386 libffi8:i386 libgl1:i386 libgl1-mesa-dri:i386
  libglapi-mesa:i386 libglvnd0:i386 libglx-mesa0:i386 libglx0:i386
  libicu72:i386 libllvm15:i386 libnvidia-cfg1-530 libnvidia-common-530
  libnvidia-compute-530:i386 libnvidia-decode-530 libnvidia-decode-530:i386
  libnvidia-encode-530 libnvidia-encode-530:i386 libnvidia-extra-530
  libnvidia-fbc1-530 libnvidia-fbc1-530:i386 libnvidia-gl-530
  libnvidia-gl-530:i386 libpciaccess0:i386 libsensors5:i386 libx11-6:i386
  libx11-xcb1:i386 libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386
  libxcb-glx0:i386 libxcb-present0:i386 libxcb-randr0:i386 libxcb-shm0:i386
  libxcb-sync1:i386 libxcb-xfixes0:i386 libxcb1:i386 libxdmcp6:i386
  libxext6:i386 libxfixes3:i386 libxml2:i386 libxshmfence1:i386
  libxxf86vm1:i386 screen-resolution-extra xserver-xorg-video-nvidia-530
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  linux-modules-nvidia-530-5.15.0-71-generic*
  linux-modules-nvidia-530-generic* nvidia-common* nvidia-compute-utils-530*
  nvidia-dkms-530* nvidia-driver-530* nvidia-kernel-common-530*
  nvidia-kernel-source-530* nvidia-prime* nvidia-settings* nvidia-utils-530*
0 upgraded, 0 newly installed, 11 to remove and 0 not upgraded.
Purg nvidia-driver-530 [530.41.03-0ubuntu2]
Purg linux-modules-nvidia-530-generic [5.15.0-71.78]
Purg linux-modules-nvidia-530-5.15.0-71-generic [5.15.0-71.78]
Purg nvidia-common [1:0.9.7.1]
Purg nvidia-compute-utils-530 [530.41.03-0ubuntu2]
Purg nvidia-dkms-530 [530.41.03-0ubuntu2]
Purg nvidia-kernel-common-530 [530.41.03-0ubuntu2]
Purg nvidia-kernel-source-530 [530.41.03-0ubuntu2]
Purg nvidia-prime [0.8.17.1]
Purg nvidia-settings [510.47.03-0ubuntu1]
Purg nvidia-utils-530 [530.41.03-0ubuntu2]

```
Do you have any PPA's added for nvidia?
```
apt policy nvidia-driver-530
nvidia-driver-530:
  Installed: 530.41.03-0ubuntu2
  Candidate: 530.41.03-0ubuntu2
  Version table:
 *** 530.41.03-0ubuntu2 500
        **[COLOR="#FF0000"]500 https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu lunar/main amd64 Packages[/COLOR]**
        100 /var/lib/dpkg/status


```

---

### Post by criageek on 2023-04-30
Thanks 1fallen - I do not have any PPA's added.  I determined this in two ways.  First I opened Synaptic and selected 'Origin' and saw no PPA's.  Then I followed your suggestion but used nvidia-driver-* and redirected the output to a text file.  Then I searched that text file for 'ppa' and found nothing.

Rich

---

### Post by #&amp;thj^% on 2023-04-30
PPA's are outside sources or 3rd party.
This one has been very stable on my end for a year or more now: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
Please note, that your mileage may vary from my findings.
Let me know which way you want go now.

---

### Post by criageek on 2023-04-30
Ok, I did the purge

```
sudo apt-get remove --purge '^nvidia-.*'
```
and then did this again

```
sudo dpkg -l | grep -i nvidia

```and that resulted in this
```
ii  libnvidia-cfg1-525:amd64                                    525.105.17-0ubuntu1                     amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-525                                        525.105.17-0ubuntu1                     all          Shared files used by the NVIDIA libraries
rc  libnvidia-compute-470:amd64                                 470.129.06-0ubuntu0.22.04.1             amd64        NVIDIA libcompute package
rc  libnvidia-compute-510:amd64                                 510.108.03-0ubuntu2                     amd64        NVIDIA libcompute package
ii  libnvidia-compute-525:amd64                                 525.105.17-0ubuntu1                     amd64        NVIDIA libcompute package
ii  libnvidia-compute-525:i386                                  525.105.17-0ubuntu1                     i386         NVIDIA libcompute package
ii  libnvidia-decode-525:amd64                                  525.105.17-0ubuntu1                     amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-525:i386                                   525.105.17-0ubuntu1                     i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-egl-wayland1:amd64                                1:1.1.10-1                              amd64        Wayland EGL External Platform library -- shared library
ii  libnvidia-encode-525:amd64                                  525.105.17-0ubuntu1                     amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-525:i386                                   525.105.17-0ubuntu1                     i386         NVENC Video Encoding runtime library
ii  libnvidia-extra-525:amd64                                   525.105.17-0ubuntu1                     amd64        Extra libraries for the NVIDIA driver
ii  libnvidia-fbc1-525:amd64                                    525.105.17-0ubuntu1                     amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-525:i386                                     525.105.17-0ubuntu1                     i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-525:amd64                                      525.105.17-0ubuntu1                     amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-525:i386                                       525.105.17-0ubuntu1                     i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
rc  linux-modules-nvidia-470-5.11.0-31-generic                  5.11.0-31.33                            amd64        Linux kernel nvidia modules for version 5.11.0-31
rc  linux-modules-nvidia-470-5.11.0-36-generic                  5.11.0-36.40                            amd64        Linux kernel nvidia modules for version 5.11.0-36
rc  linux-modules-nvidia-470-5.11.0-37-generic                  5.11.0-37.41                            amd64        Linux kernel nvidia modules for version 5.11.0-37
rc  linux-modules-nvidia-470-5.11.0-38-generic                  5.11.0-38.42                            amd64        Linux kernel nvidia modules for version 5.11.0-38
rc  linux-modules-nvidia-470-5.13.0-20-generic                  5.13.0-20.20                            amd64        Linux kernel nvidia modules for version 5.13.0-20
rc  linux-modules-nvidia-470-5.13.0-21-generic                  5.13.0-21.21+1                          amd64        Linux kernel nvidia modules for version 5.13.0-21
rc  linux-modules-nvidia-470-5.13.0-22-generic                  5.13.0-22.22+2                          amd64        Linux kernel nvidia modules for version 5.13.0-22
rc  linux-modules-nvidia-470-5.13.0-23-generic                  5.13.0-23.23+1                          amd64        Linux kernel nvidia modules for version 5.13.0-23
rc  linux-modules-nvidia-470-5.13.0-25-generic                  5.13.0-25.26                            amd64        Linux kernel nvidia modules for version 5.13.0-25
rc  linux-modules-nvidia-470-5.13.0-27-generic                  5.13.0-27.29                            amd64        Linux kernel nvidia modules for version 5.13.0-27
rc  linux-modules-nvidia-470-5.13.0-28-generic                  5.13.0-28.31+1                          amd64        Linux kernel nvidia modules for version 5.13.0-28
rc  linux-modules-nvidia-470-5.13.0-30-generic                  5.13.0-30.33                            amd64        Linux kernel nvidia modules for version 5.13.0-30
rc  linux-modules-nvidia-470-5.13.0-35-generic                  5.13.0-35.40                            amd64        Linux kernel nvidia modules for version 5.13.0-35
rc  linux-modules-nvidia-470-5.13.0-37-generic                  5.13.0-37.42                            amd64        Linux kernel nvidia modules for version 5.13.0-37
rc  linux-modules-nvidia-470-5.13.0-39-generic                  5.13.0-39.44                            amd64        Linux kernel nvidia modules for version 5.13.0-39
rc  linux-modules-nvidia-470-5.13.0-40-generic                  5.13.0-40.45                            amd64        Linux kernel nvidia modules for version 5.13.0-40
rc  linux-modules-nvidia-470-5.15.0-27-generic                  5.15.0-27.28                            amd64        Linux kernel nvidia modules for version 5.15.0-27
rc  linux-modules-nvidia-470-5.15.0-30-generic                  5.15.0-30.31+1                          amd64        Linux kernel nvidia modules for version 5.15.0-30
rc  linux-modules-nvidia-470-5.15.0-33-generic                  5.15.0-33.34                            amd64        Linux kernel nvidia modules for version 5.15.0-33
rc  linux-modules-nvidia-470-5.15.0-35-generic                  5.15.0-35.36+1                          amd64        Linux kernel nvidia modules for version 5.15.0-35
rc  linux-modules-nvidia-470-5.15.0-37-generic                  5.15.0-37.39                            amd64        Linux kernel nvidia modules for version 5.15.0-37
rc  linux-modules-nvidia-470-5.15.0-39-generic                  5.15.0-39.42                            amd64        Linux kernel nvidia modules for version 5.15.0-39
rc  linux-modules-nvidia-510-5.15.0-40-generic                  5.15.0-40.43+1                          amd64        Linux kernel nvidia modules for version 5.15.0-40
rc  linux-modules-nvidia-510-5.15.0-41-generic                  5.15.0-41.44+1                          amd64        Linux kernel nvidia modules for version 5.15.0-41
rc  linux-modules-nvidia-510-5.15.0-52-generic                  5.15.0-52.58+1                          amd64        Linux kernel nvidia modules for version 5.15.0-52
rc  linux-modules-nvidia-510-5.19.0-23-generic                  5.19.0-23.24+1                          amd64        Linux kernel nvidia modules for version 5.19.0-23
rc  linux-modules-nvidia-510-5.19.0-26-generic                  5.19.0-26.27+1                          amd64        Linux kernel nvidia modules for version 5.19.0-26
rc  linux-modules-nvidia-510-5.19.0-28-generic                  5.19.0-28.29                            amd64        Linux kernel nvidia modules for version 5.19.0-28
rc  linux-modules-nvidia-510-5.19.0-29-generic                  5.19.0-29.30+1                          amd64        Linux kernel nvidia modules for version 5.19.0-29
rc  linux-modules-nvidia-510-5.19.0-31-generic                  5.19.0-31.32                            amd64        Linux kernel nvidia modules for version 5.19.0-31
rc  linux-modules-nvidia-510-5.19.0-35-generic                  5.19.0-35.36                            amd64        Linux kernel nvidia modules for version 5.19.0-35
rc  linux-modules-nvidia-510-5.19.0-38-generic                  5.19.0-38.39+1                          amd64        Linux kernel nvidia modules for version 5.19.0-38
rc  linux-modules-nvidia-510-5.19.0-40-generic                  5.19.0-40.41+1                          amd64        Linux kernel nvidia modules for version 5.19.0-40
rc  linux-modules-nvidia-510-6.2.0-20-generic                   6.2.0-20.20                             amd64        Linux kernel nvidia modules for version 6.2.0-20
rc  linux-objects-nvidia-470-5.11.0-36-generic                  5.11.0-36.40                            amd64        Linux kernel nvidia modules for version 5.11.0-36 (objects)
rc  linux-objects-nvidia-470-5.11.0-38-generic                  5.11.0-38.42                            amd64        Linux kernel nvidia modules for version 5.11.0-38 (objects)
rc  linux-objects-nvidia-470-5.13.0-20-generic                  5.13.0-20.20                            amd64        Linux kernel nvidia modules for version 5.13.0-20 (objects)
rc  linux-objects-nvidia-470-5.13.0-21-generic                  5.13.0-21.21+1                          amd64        Linux kernel nvidia modules for version 5.13.0-21 (objects)
rc  linux-objects-nvidia-470-5.13.0-22-generic                  5.13.0-22.22+2                          amd64        Linux kernel nvidia modules for version 5.13.0-22 (objects)
rc  linux-objects-nvidia-470-5.13.0-23-generic                  5.13.0-23.23+1                          amd64        Linux kernel nvidia modules for version 5.13.0-23 (objects)
rc  linux-objects-nvidia-470-5.13.0-25-generic                  5.13.0-25.26                            amd64        Linux kernel nvidia modules for version 5.13.0-25 (objects)
rc  linux-objects-nvidia-470-5.13.0-27-generic                  5.13.0-27.29                            amd64        Linux kernel nvidia modules for version 5.13.0-27 (objects)
rc  linux-objects-nvidia-470-5.13.0-28-generic                  5.13.0-28.31+1                          amd64        Linux kernel nvidia modules for version 5.13.0-28 (objects)
rc  linux-objects-nvidia-470-5.13.0-30-generic                  5.13.0-30.33                            amd64        Linux kernel nvidia modules for version 5.13.0-30 (objects)
rc  linux-objects-nvidia-470-5.13.0-35-generic                  5.13.0-35.40                            amd64        Linux kernel nvidia modules for version 5.13.0-35 (objects)
rc  linux-objects-nvidia-470-5.13.0-37-generic                  5.13.0-37.42                            amd64        Linux kernel nvidia modules for version 5.13.0-37 (objects)
rc  linux-objects-nvidia-470-5.13.0-39-generic                  5.13.0-39.44                            amd64        Linux kernel nvidia modules for version 5.13.0-39 (objects)
rc  linux-objects-nvidia-470-5.13.0-40-generic                  5.13.0-40.45                            amd64        Linux kernel nvidia modules for version 5.13.0-40 (objects)
rc  linux-objects-nvidia-470-5.15.0-30-generic                  5.15.0-30.31+1                          amd64        Linux kernel nvidia modules for version 5.15.0-30 (objects)
rc  linux-objects-nvidia-470-5.15.0-33-generic                  5.15.0-33.34                            amd64        Linux kernel nvidia modules for version 5.15.0-33 (objects)
rc  linux-objects-nvidia-470-5.15.0-35-generic                  5.15.0-35.36+1                          amd64        Linux kernel nvidia modules for version 5.15.0-35 (objects)
rc  linux-objects-nvidia-470-5.15.0-37-generic                  5.15.0-37.39                            amd64        Linux kernel nvidia modules for version 5.15.0-37 (objects)
rc  linux-objects-nvidia-510-5.15.0-41-generic                  5.15.0-41.44+1                          amd64        Linux kernel nvidia modules for version 5.15.0-41 (objects)
rc  linux-objects-nvidia-510-5.15.0-52-generic                  5.15.0-52.58+1                          amd64        Linux kernel nvidia modules for version 5.15.0-52 (objects)
rc  linux-objects-nvidia-510-5.19.0-23-generic                  5.19.0-23.24+1                          amd64        Linux kernel nvidia modules for version 5.19.0-23 (objects)
rc  linux-objects-nvidia-510-5.19.0-26-generic                  5.19.0-26.27+1                          amd64        Linux kernel nvidia modules for version 5.19.0-26 (objects)
rc  linux-objects-nvidia-510-5.19.0-28-generic                  5.19.0-28.29                            amd64        Linux kernel nvidia modules for version 5.19.0-28 (objects)
rc  linux-objects-nvidia-510-5.19.0-29-generic                  5.19.0-29.30+1                          amd64        Linux kernel nvidia modules for version 5.19.0-29 (objects)
rc  linux-objects-nvidia-510-5.19.0-31-generic                  5.19.0-31.32                            amd64        Linux kernel nvidia modules for version 5.19.0-31 (objects)
rc  linux-objects-nvidia-510-5.19.0-35-generic                  5.19.0-35.36                            amd64        Linux kernel nvidia modules for version 5.19.0-35 (objects)
rc  linux-objects-nvidia-510-5.19.0-38-generic                  5.19.0-38.39+1                          amd64        Linux kernel nvidia modules for version 5.19.0-38 (objects)
ii  linux-objects-nvidia-510-5.19.0-40-generic                  5.19.0-40.41+1                          amd64        Linux kernel nvidia modules for version 5.19.0-40 (objects)
ii  linux-objects-nvidia-510-6.2.0-20-generic                   6.2.0-20.20                             amd64        Linux kernel nvidia modules for version 6.2.0-20 (objects)
ii  linux-objects-nvidia-525-6.2.0-20-generic                   6.2.0-20.20                             amd64        Linux kernel nvidia modules for version 6.2.0-20 (objects)
ii  linux-signatures-nvidia-5.19.0-40-generic                   5.19.0-40.41+1                          amd64        Linux kernel signatures for nvidia modules for version 5.19.0-40-generic
ii  linux-signatures-nvidia-6.2.0-20-generic                    6.2.0-20.20                             amd64        Linux kernel signatures for nvidia modules for version 6.2.0-20-generic
ii  screen-resolution-extra                                     0.18.3                                  all          Extension for the nvidia-settings control panel
ii  xserver-xorg-video-nvidia-525                               525.105.17-0ubuntu1                     amd64        NVIDIA binary Xorg driver

```

Is that expected?  I ask because after I did
```
sudo apt update
sudo apt upgrade
sudo ubuntu-drivers autoinstall
```
 and rebooted I had the same issues with some windows being very small.  A virtual box machine is one, and some Windows backup software I run using Wine is another.  Also some text in other apps is way smaller than it should be.  Perhaps I need to follow this advice? > [COLOR=#000000]As Nvidia and Wayland are still having growing pains - may I also suggest that with Nvidia graphics issues that you employ the legacy Xorg compositor - OR run the open source nouveau driver with Wayland ? Can you expand on this?  How I go about doing this?

Thanks guys!

Rich[/COLOR]

---

### Post by #&amp;thj^% on 2023-04-30
OK now I'm here for a short time so lets try again:
```
nvidia-smi
```
> As Nvidia and Wayland are still having growing pains - may I also suggest that with Nvidia graphics issues that you employ the legacy Xorg compositor - OR run the open source nouveau driver with Wayland ?" Can you expand on this? How I go about doing this?

Nvidia and Wayland are not yet ready to play nice with each other, Login with a X11 session with Nvidia.

---

### Post by criageek on 2023-04-30
> **1fallen said:**
> OK now I'm here for a short time so lets try again:
```
nvidia-smi
```

Nvidia and Wayland are not yet ready to play nice with each other, Login with a X11 session with Nvidia.

nvidia-smi is not installed.  I assume I can install it with ```
sudo apt install nvidia-utils-525
```Right?

How do I go about logging in "with a X11 session with Nvidia"?

Thanks!

Rich

---

### Post by #&amp;thj^% on 2023-04-30
> **criageek said:**
> nvidia-smi is not installed.  I assume I can install it with ```
sudo apt install nvidia-utils-525
```Right?
That should come in with the Nvidia driver install, so do nothing yet.
> **criageek said:**
> How do I go about logging in "with a X11 session with Nvidia"?

Thanks!

Rich
See Screenshot

---

### Post by criageek on 2023-04-30
Actually, I probably gave you bad info.  When I tried nvidia-smi, it was after a (second) purge but before a second driver install.  One moment...

Rich

---

### Post by criageek on 2023-04-30
nvidia-smi

```
Sun Apr 30 16:09:58 2023       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 525.105.17   Driver Version: 525.105.17   CUDA Version: 12.0     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  NVIDIA GeForce ...  Off  | 00000000:01:00.0  On |                  N/A |
| N/A   38C    P0    N/A /  30W |   1123MiB /  2048MiB |     11%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================|
|    0   N/A  N/A      2053      G   /usr/lib/xorg/Xorg                576MiB |
|    0   N/A  N/A      2215      G   /usr/bin/gnome-shell              234MiB |
|    0   N/A  N/A      2231      G   ...libexec/mutter-x11-frames        1MiB |
|    0   N/A  N/A      2773      G   ...oud-3.6.1-x86_64.AppImage        0MiB |
|    0   N/A  N/A      3371      G   ...641596061839090226,131072      241MiB |
+-----------------------------------------------------------------------------+
```I'll reboot now and try your login suggestion...

Thanks,
Rich

---

### Post by criageek on 2023-04-30
Hi 1fallen - I don't have an X11 option for login.  All I have is "Ubuntu" and "Ubuntu on Wayland".

Next step?

Thanks!
Rich

---

### Post by #&amp;thj^% on 2023-04-30
Yeppers  All I have is **"Ubuntu"** That the one.
BTW You don't have to reboot to change sessions, just log out.

---

### Post by criageek on 2023-04-30
Yea, I decided that was the case after doing this

```
rich@jru-zt:~$ echo $XDG_SESSION_TYPE
x11
rich@jru-zt:~$
``` 


Any idea why I am still having font size issues in some apps?

Thanks!
Rich

---

### Post by #&amp;thj^% on 2023-04-30
I'm going to have to defer to a Gnome User on this.
Sorry I haven't used Gnome since Gnome 3 came about. (I'm a XFCE4 user)

---

### Post by criageek on 2023-04-30
Ok...thanks 1fallen.  I appreciate you taking the time to help me out.  I'm certainly not married to Gnome...in fact I don't really care for it.  On one of my machines I installed the display manager for Elementary OS (Pantheon?) and like it.  It upgraded to 23.04 fine but when I tried to install Pantheon on a virtual machine that was upgraded to 23.04 it said there was no release candidate for 23.04.

Rich

---

### Post by criageek on 2023-04-30
Just for reference, here is a screenshot showing this thread in a browser on my primary pc (left) and in my virtualbox machine (right).  Prior to upgrading they would have been similar sizes.  It's pretty much unreadable for my 68 year old eyes  lol.

As mentioned previously, this is not the only app with this sort of problem.  Many are ok, but many are way too small.

Rich

---

### Post by #&amp;thj^% on 2023-04-30
> **criageek said:**
> Just for reference, here is a screenshot showing this thread in a browser on my primary pc (left) and in my virtualbox machine (right).  Prior to upgrading they would have been similar sizes.  It's pretty much unreadable for my 68 year old eyes  lol.
Right there with ya..lol
> **criageek said:**
> As mentioned previously, this is not the only app with this sort of problem.  Many are ok, but many are way too small.

Rich
Have you gone to Settings, to view what options are available? (font-size) also DPI settings, but again I'm naive with Gnome. ;)

---

### Post by criageek on 2023-05-01
> **1fallen said:**
> Right there with ya..lol

Have you gone to Settings, to view what options are available? (font-size) also DPI settings, but again I'm naive with Gnome. ;)
It looks like I've found the problem.  Initially I didn't check settings because I didn't know what I'd be looking for, but finally I decided to take your suggestion and look around.  In the 'Displays' section I had 'Fractional Scaling' set on, and had the screen scaled to 125%.  I use a 42" 4k TV for my monitor, and at full resolution it was a little too small, so I had scaled it up.  Once I set it to 100% and rebooted, everything looks ok (so far).

Thanks again!
Rich

---

### Post by #&amp;thj^% on 2023-05-01
Great, very nice you did nicely all on your own, kudos :D
Had I known about the 4K monitor, well you know the old "the one that got away"LOL

---

