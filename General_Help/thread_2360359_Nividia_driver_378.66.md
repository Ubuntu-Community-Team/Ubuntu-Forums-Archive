---
title: "Nividia driver 378.66"
date: 2017-05-03
forum: General Help
---

### Post by ubuntini2 on 2017-05-03
Was told by support to download and install  Nvidia driver 378.66 since it is the most 'stable'.

Currently have 'latest' version 381.09
But have 'issues' 
Houdini crashes on launch and or certain GPU dependent plugins don't render.

Problem is I don't see v 378.66 in my Software&Updates (Ubuntu Mate 16.04)
Closest version is 378.13
Using this additional PPA for driver downloads
[http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu)

Where can I download 378.66 for Ubuntu?

---

### Post by friedchips2 on 2017-05-03
Maybe someone else can confirm this, but I don't believe 378.66 was released for linux. That's WHQL driver. For windows. Who is support? and do they know you are using Ubuntu?

---

### Post by efflandt on 2017-05-04
What nvidia hardware (card/chip) do you have? 378.13 does appear to be the version in nvidia-378 package from graphics-drivers ppa. I have cuda installed too, and enabled that in blender, but not sure how to get blender to use cuda when it is launched by OpenShot Video Editor because that still appears to be using only my CPU (100%) with my nvidia card not busy.```
$ dpkg-query -l nvidia* | grep ii
ii  nvidia-378                       378.13-0ubuntu0~gpu16.10.3 amd64        NVIDIA binary driver - version 378.13
ii  nvidia-cuda-dev                  8.0.44-0ubuntu1            amd64        NVIDIA CUDA development files
ii  nvidia-cuda-doc                  8.0.44-0ubuntu1            all          NVIDIA CUDA and OpenCL documentation
ii  nvidia-cuda-gdb                  8.0.44-0ubuntu1            amd64        NVIDIA CUDA Debugger (GDB)
ii  nvidia-cuda-toolkit              8.0.44-0ubuntu1            amd64        NVIDIA CUDA development toolkit
ii  nvidia-modprobe                  367.18-1                   amd64        utility to load NVIDIA kernel modules and create device nodes
ii  nvidia-opencl-dev:amd64          8.0.44-0ubuntu1            amd64        NVIDIA OpenCL development files
ii  nvidia-opencl-icd-378            378.13-0ubuntu0~gpu16.10.3 amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                     0.8.4                      amd64        Tools to enable NVIDIA's Prime
ii  nvidia-profiler                  8.0.44-0ubuntu1            amd64        NVIDIA Profiler for CUDA and OpenCL
ii  nvidia-settings                  381.09-0ubuntu0~gpu16.10.2 amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-visual-profiler           8.0.44-0ubuntu1            amd64        NVIDIA Visual Profiler for CUDA and OpenCL
```

---

### Post by mastablasta on 2017-05-04
try 378.13, you can always replace it. furthermore why not simply use the additional drivers application to get the stable driver for your chip?

---

### Post by Bucky Ball on 2017-05-04
> **efflandt said:**
> ... not sure how to get blender to use cuda when it is launched by OpenShot Video Editor because that still appears to be using only my CPU (100%) with my nvidia card not busy.

Not all apps use or are able to use cuda. Have you checked Openshot to see if that's one of them?

---

