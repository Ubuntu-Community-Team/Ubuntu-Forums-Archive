---
title: "openCL and nVidia"
date: 2022-03-08
forum: General Help
---

### Post by alain.roger on 2022-03-08
Hi,

I have a laptop that uses nvidia-driver-390. I need to make it use openCL and I would like also to be able to make CUDA working on it.
I installed openCL from Mesa but clinfo returns me :
```
[FONT=monospace][COLOR=#000000]Number of platforms                               1 [/COLOR]
  Platform Name                                   Clover 
  Platform Vendor                                 Mesa 
  Platform Version                                OpenCL 1.1 Mesa 21.2.6 
  Platform Profile                                FULL_PROFILE 
  Platform Extensions                             cl_khr_icd 
  Platform Extensions function suffix             MESA 

  Platform Name                                   Clover 
Number of devices                                 0 

NULL platform behavior 
  clGetPlatformInfo(NULL, CL_PLATFORM_NAME, ...)  No platform 
  clGetDeviceIDs(NULL, CL_DEVICE_TYPE_ALL, ...)   No platform 
  clCreateContext(NULL, ...) [default]            No platform 
  clCreateContext(NULL, ...) [other]               
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_DEFAULT)  No platform 
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_CPU)  No platform 
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_GPU)  No platform 
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_ACCELERATOR)  No platform 
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_CUSTOM)  No platform 
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_ALL)  No platform

[/FONT]
```

I understand by "number of devices = 0" that openCL does not work.
Am I wrong ?
I know that my graphic card supports CUDA and OpenCL so how can I be sure that openCL works ?
Is there another version of openCL than MESA ?

thx a lot

---

### Post by #&amp;thj^% on 2022-03-08
> **alain.roger said:**
> Hi,


I know that my graphic card supports CUDA and OpenCL so how can I be sure that openCL works ?
Is there another version of openCL than MESA ?

thx a lot

what dose this show?
```
apt policy ocl-icd-libopencl1
```
One more as well:
```
nvidia-smi
```

---

### Post by alain.roger on 2022-03-10
Hi,

> **1fallen said:**
> what dose this show?
```
apt policy ocl-icd-libopencl1
```
returns:
```
[FONT=monospace][COLOR=#000000]ocl-icd-libopencl1:[/COLOR]
  Installed: 2.2.14-2
  Candidate: 2.2.14-2
  Version table:
 *** 2.2.14-2 500
        500 http://fr.archive.ubuntu.com/ubuntu impish/universe amd64 Packages
        100 /var/lib/dpkg/status

[/FONT]
```
> **1fallen said:**
> One more as well:
```
nvidia-smi
```
returns:
```
[FONT=monospace][COLOR=#000000]Thu Mar 10 06:59:35 2022        [/COLOR]
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 390.144                Driver Version: 390.144                   |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 460M    Off  | 00000000:01:00.0 N/A |                  N/A |
| N/A   55C    P0    N/A /  N/A |    902MiB /  1473MiB |     N/A      Default |
+-------------------------------+----------------------+----------------------+
                                                                                
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|    0                    Not Supported                                       |
+-----------------------------------------------------------------------------+

[/FONT]
```

I know that CUDA 8.1 was working on this laptop as opencl

---

### Post by #&amp;thj^% on 2022-03-10
I don't see cuda at all in your smi output.
Is it installed?
```
apt policy nvidia-cuda-toolkit
```
After a reboot recommended, >>if it wasn't installed beforehand.
It should look like this:
```
nvidia-smi
Thu Mar 10 11:08:37 2022       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 510.54       Driver Version: 510.54       CUDA Version: 11.6     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|

```
And I agree CUDA 8.1 should be the correct version for your older driver.

---

### Post by alain.roger on 2022-03-10
when I install nvidia-cuda-toolkit, it goes to version 470 and remove nvidia-smi (v390). And if I install nvidia-utils-390 after I installed nvidia-cuda-toolkit, the toolkit is removed.
That's weird system does not install nvidia-utils of the same version as toolkit is.

Anyway here is it:
```
[FONT=monospace][COLOR=#000000]sudo apt policy nvidia-cuda-toolkit[/COLOR]
nvidia-cuda-toolkit:
  Installed: 11.3.1-4
  Candidate: 11.3.1-4
  Version table:
 *** 11.3.1-4 500
        500 http://fr.archive.ubuntu.com/ubuntu impish/multiverse amd64 Packages
        100 /var/lib/dpkg/status

[/FONT]
```

and if I want to install nvidia-utils-470 (the same version as the toolkit), typing nvidia-smi does not work as it says it's not the same version

so I'm stuck.. I have the choice to take one of them (toolkit or nvidia-utils)

Is there a way to specify the toolkit version I want ? so it could be for nvidia 390.144

thx

---

### Post by #&amp;thj^% on 2022-03-10
So the driver 470. dose not work for your system? is this correct?
So it looks like I'm incorrect on the CUDA version yours shows the correct version 11.3.1-4
And now it appears at a glance your forced to use driver 470.
I strayed off my usual questions.
Assuming your install was like:
```
ubuntu-drivers devices
WARNING:root:_pkg_get_support nvidia-driver-390: package has invalid Support Legacyheader, cannot determine support level
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd00001290sv000017AAsd0000221Ebc03sc00i00
vendor   : NVIDIA Corporation
model    : GK208M [GeForce GT 730M]
driver   : nvidia-340 - distro non-free
driver   : nvidia-driver-418-server - distro non-free
driver   : nvidia-driver-470 - distro non-free recommended
driver   : nvidia-driver-470-server - distro non-free
**_[COLOR="#FF0000"]driver   : nvidia-driver-390 - distro non-free[/COLOR]_**
driver   : nvidia-driver-450-server - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin

```
and  you selected the high-lighted driver from above, the toolkit should have been included.
I have this card that fell  out of support a few months back.
```
inxi -Gx
Graphics:
  Device-1: Intel 4th Gen Core Processor Integrated Graphics vendor: Lenovo 
  driver: i915 v: kernel bus ID: 00:02.0 
  Device-2: NVIDIA GK208M [GeForce GT 730M] vendor: Lenovo driver: nvidia 
  v: 470.103.01 bus ID: 01:00.0 
  Display: x11 server: X.Org 1.20.13 driver: modesetting,nvidia 
  unloaded: fbdev,nouveau,vesa resolution: 1920x1080~60Hz 
  OpenGL: renderer: Mesa DRI Intel HD Graphics 4600 (HSW GT2) 
  v: 4.5 Mesa 21.2.6 direct render: Yes 

```
Mine:
```
Thu Mar 10 18:11:05 2022       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 470.103.01   Driver Version: 470.103.01   CUDA Version: 11.4     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  NVIDIA GeForce ...  Off  | 00000000:01:00.0 N/A |                  N/A |
| N/A   43C    P8    N/A /  N/A |      3MiB /   983MiB |     N/A      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================|
|  No running processes found                                                 |
+-----------------------------------------------------------------------------+

```
So i wondering now how you installed your driver?
Ad there is this:
```
WARNING:root:_pkg_get_support nvidia-driver-390: package has invalid Support Legacyheader, cannot determine support level
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd00001290sv000017AAsd0000221Ebc03sc00i00

```

---

### Post by alain.roger on 2022-03-11
In fact Ubuntu advise me to install nvidia-driver-390 as it seems it's the latest compatible version for my Nvidia card.

Therefore I installed drivers as usual with sudo apt install nvidia-driver-390
I installed nvidia utils with sudo apt install nvidia-utils-390

But none of these instruction installed cuda driver and as I wrote previously, according to nvidia, the latest compatible cuda driver should be v9.1 and not 11.x
However, I haven't been able to install the cuda 9.1 driver for now (or toolkit)
[FONT=monospace]
[/FONT]```
[FONT=monospace][COLOR=#000000]Fri Mar 11 09:59:10 2022        [/COLOR]
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 390.144                Driver Version: 390.144                   |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 460M    Off  | 00000000:01:00.0 N/A |                  N/A |
| N/A   45C    P8    N/A /  N/A |    202MiB /  1473MiB |     N/A      Default |
+-------------------------------+----------------------+----------------------+
                                                                                
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|    0                    Not Supported                                       |
+-----------------------------------------------------------------------------+

[/FONT]
```

[FONT=monospace]it seems that installing toolkit 11.x, installed also drivers. This step was not available for cuda driver 9.1
[/FONT]

---

### Post by #&amp;thj^% on 2022-03-11
They have crippled 390. [https://forums.developer.nvidia.com/t/cant-install-cuda-on-ubuntu-20-04-with-old-driver-390-144/195399/2](https://forums.developer.nvidia.com/t/cant-install-cuda-on-ubuntu-20-04-with-old-driver-390-144/195399/2)

I wasn't convinced so I first installed the driver
```

nvidia-smi
Fri Mar 11 10:08:09 2022       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 390.144                Driver Version: 390.144                   |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GT 730M     Off  | 00000000:01:00.0 N/A |                  N/A |
| N/A   43C    P8    N/A /  N/A |    129MiB /   983MiB |     N/A      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|    0                    Not Supported                                       |
+-----------------------------------------------------------------------------+
```

Just as you saw it^^^^^^^
Looked here, 
```
 
>> dkms status
nvidia, 390.144, 5.13.0-30-generic, x86_64: installed
nvidia, 390.144, 5.13.0-35-generic, x86_64: installed
```
So now I had to see first hand what is what.
```

sudo apt install nvidia-cuda-toolkit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-cuda-toolkit : Depends: nvidia-profiler (= 10.1.243-3) but it is not going to be installed
                       Depends: nvidia-cuda-dev (= 10.1.243-3) but it is not going to be installed
                       Recommends: nvidia-visual-profiler (= 10.1.243-3) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

Now this "nvidia-visual-profiler" should have pulled in cuda 10.1, and I believe your card has compute capability 3.0 which will work. (So I thought) 
```

dpkg -l | grep nvidia
ii  libnvidia-cfg1-390:amd64                      390.144-0ubuntu0.20.04.1                             amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-390                          390.144-0ubuntu0.20.04.1                             all          Shared files used by the NVIDIA libraries
ii  libnvidia-compute-390:amd64                   390.144-0ubuntu0.20.04.1                             amd64        NVIDIA libcompute package
ii  libnvidia-compute-390:i386                    390.144-0ubuntu0.20.04.1                             i386         NVIDIA libcompute package
rc  libnvidia-compute-470:amd64                   470.103.01-0ubuntu0.20.04.1                          amd64        NVIDIA libcompute package
ii  libnvidia-decode-390:amd64                    390.144-0ubuntu0.20.04.1                             amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-390:i386                     390.144-0ubuntu0.20.04.1                             i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-390:amd64                    390.144-0ubuntu0.20.04.1                             amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-390:i386                     390.144-0ubuntu0.20.04.1                             i386         NVENC Video Encoding runtime library
ii  libnvidia-fbc1-390:amd64                      390.144-0ubuntu0.20.04.1                             amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-390:i386                       390.144-0ubuntu0.20.04.1                             i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-390:amd64                        390.144-0ubuntu0.20.04.1                             amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-390:i386                         390.144-0ubuntu0.20.04.1                             i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-390:amd64                      390.144-0ubuntu0.20.04.1                             amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  libnvidia-ifr1-390:i386                       390.144-0ubuntu0.20.04.1                             i386         NVIDIA OpenGL-based Inband Frame Readback runtime library
rc  linux-modules-nvidia-470-5.11.0-27-generic    5.11.0-27.29~20.04.1                                 amd64        Linux kernel nvidia modules for version 5.11.0-27
rc  linux-modules-nvidia-470-5.11.0-40-generic    5.11.0-40.44~20.04.2+1                               amd64        Linux kernel nvidia modules for version 5.11.0-40
rc  linux-objects-nvidia-470-5.11.0-27-generic    5.11.0-27.29~20.04.1                                 amd64        Linux kernel nvidia modules for version 5.11.0-27 (objects)
rc  linux-objects-nvidia-470-5.11.0-40-generic    5.11.0-40.44~20.04.2+1                               amd64        Linux kernel nvidia modules for version 5.11.0-40 (objects)
rc  linux-objects-nvidia-470-5.13.0-28-generic    5.13.0-28.31~20.04.1+2                               amd64        Linux kernel nvidia modules for version 5.13.0-28 (objects)
ii  linux-objects-nvidia-470-5.13.0-30-generic    5.13.0-30.33~20.04.1                                 amd64        Linux kernel nvidia modules for version 5.13.0-30 (objects)
ii  linux-objects-nvidia-470-5.13.0-35-generic    5.13.0-35.40~20.04.1                                 amd64        Linux kernel nvidia modules for version 5.13.0-35 (objects)
ii  linux-signatures-nvidia-5.13.0-30-generic     5.13.0-30.33~20.04.1                                 amd64        Linux kernel signatures for nvidia modules for version 5.13.0-30-generic
ii  linux-signatures-nvidia-5.13.0-35-generic     5.13.0-35.40~20.04.1                                 amd64        Linux kernel signatures for nvidia modules for version 5.13.0-35-generic
ii  nvidia-compute-utils-390                      390.144-0ubuntu0.20.04.1                             amd64        NVIDIA compute utilities
ii  nvidia-dkms-390                               390.144-0ubuntu0.20.04.1                             amd64        NVIDIA DKMS package
ii  nvidia-driver-390                             390.144-0ubuntu0.20.04.1                             amd64        NVIDIA driver metapackage
ii  nvidia-kernel-common-390                      390.144-0ubuntu0.20.04.1                             amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-390                      390.144-0ubuntu0.20.04.1                             amd64        NVIDIA kernel source package
ii  nvidia-prime                                  0.8.16~0.20.04.1                                     all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                               470.57.01-0ubuntu0.20.04.3                           amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-390                              390.144-0ubuntu0.20.04.1                             amd64        NVIDIA driver support binaries
ii  screen-resolution-extra                       0.18build1                                           all          Extension for the nvidia-settings control panel
ii  xserver-xorg-video-nvidia-390                 390.144-0ubuntu0.20.04.1                             amd64        NVIDIA binary Xorg driver

```
Long Story short, nothing I've tried has worked  and from that link I showed you, so far no one there has as well.
When nvidia is done with support they are done with any support.
Wish I had better news.

---

### Post by #&amp;thj^% on 2022-03-11
Hold the fort< Breaking News.
This thing had me wrapped around the axle, talked to Dev and check this if it will work for you.
```
nvidia-smi
Fri Mar 11 17:33:37 2022       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 390.144                Driver Version: 390.144                   |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GT 730M     Off  | 00000000:01:00.0 N/A |                  N/A |
| N/A   43C    P8    N/A /  N/A |    145MiB /   983MiB |     N/A      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|    0                    Not Supported                                       |
+-----------------------------------------------------------------------------+


me on Fri Mar 11 at 05:33 PM in ~ branch: (HEAD) 
>> nvcc --version
nvcc: NVIDIA (R) Cuda compiler driver
Copyright (c) 2005-2019 NVIDIA Corporation
Built on Sun_Jul_28_19:07:16_PDT_2019
Cuda compilation tools, release 10.1, V10.1.243


```
Let me know and I'll post a step by step.
Took me a half a day.

---

### Post by alain.roger on 2022-03-13
I have the same result:
```
[FONT=monospace][COLOR=#000000]Sun Mar 13 22:48:14 2022        [/COLOR]
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 390.144                Driver Version: 390.144                   |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 460M    Off  | 00000000:01:00.0 N/A |                  N/A |
| N/A   61C    P0    N/A /  N/A |   1183MiB /  1473MiB |     N/A      Default |
+-------------------------------+----------------------+----------------------+
                                                                                
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|    0                    Not Supported                                       |
+-----------------------------------------------------------------------------+
[COLOR=#ffffff]** alain **[/COLOR][COLOR=#0087af]&#57520; [/COLOR][COLOR=#d0d0d0]**~ **[/COLOR]**[COLOR=#585858] [/COLOR]**[COLOR=#000000]nvcc --version[/COLOR]
nvcc: NVIDIA (R) Cuda compiler driver
Copyright (c) 2005-2017 NVIDIA Corporation
Built on Fri_Nov__3_21:07:56_CDT_2017
Cuda compilation tools, release 9.1, V9.1.85

[/FONT]
```

---

### Post by #&amp;thj^% on 2022-03-13
> **alain.roger said:**
> I have the same result:
```
[FONT=monospace][COLOR=#000000]Sun Mar 13 22:48:14 2022        [/COLOR]
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 390.144                Driver Version: 390.144                   |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 460M    Off  | 00000000:01:00.0 N/A |                  N/A |
| N/A   61C    P0    N/A /  N/A |   1183MiB /  1473MiB |     N/A      Default |
+-------------------------------+----------------------+----------------------+
                                                                                
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|    0                    Not Supported                                       |
+-----------------------------------------------------------------------------+
[COLOR=#ffffff]** alain **[/COLOR][COLOR=#0087af]&#57520; [/COLOR][COLOR=#d0d0d0]**~ **[/COLOR]**[COLOR=#585858] [/COLOR]**[COLOR=#000000]nvcc --version[/COLOR]
nvcc: NVIDIA (R) Cuda compiler driver
Copyright (c) 2005-2017 NVIDIA Corporation
Built on Fri_Nov__3_21:07:56_CDT_2017
Cuda compilation tools, release 9.1, V9.1.85

[/FONT]
```
Good Job and you even got the 9.1 version.

---

### Post by alain.roger on 2022-03-20
I still have issue to make CUDA/OpenCL works on my laptop with my Nvidia 460m (supporting CUDA/OpenCL).
I tried to replicate the steps of this article : [https://askubuntu.com/questions/1301528/how-to-use-cuda-toolkit-on-geforce-gtx-460m-in-2020](https://askubuntu.com/questions/1301528/how-to-use-cuda-toolkit-on-geforce-gtx-460m-in-2020)
but without success.

I was not able to install Cuda toolkit 9.1 nor 8.0.

---

### Post by alain.roger on 2022-03-29
After several tests under Ubuntu 21.10, Fedora 35.1.2 and Almalinux 8.5 with my laptop (nvidia 460M) I discovered that nvidia driver 390.144 supplied with ubuntu was buggy and did not allow to use OpenCL and Cuda.
I downloaded nvidia driver 390.147 directly from NVidia website and after purgin all nvidia packages from my laptop, installing nvidia driver 390.147, now everything works as before and I can use OpenCL / Cuda with my 10 years old graphic card 460M.

---

### Post by #&amp;thj^% on 2022-03-29
> **alain.roger said:**
> After several tests under Ubuntu 21.10, Fedora 35.1.2 and Almalinux 8.5 with my laptop (nvidia 460M) I discovered that nvidia driver 390.144 supplied with ubuntu was buggy and did not allow to use OpenCL and Cuda.
I downloaded nvidia driver 390.147 directly from NVidia website and after purgin all nvidia packages from my laptop, installing nvidia driver 390.147, now everything works as before and I can use OpenCL / Cuda with my 10 years old graphic card 460M.

@alain.roger my sincerest apologies, I had thought on your last post from 2weeks ago that was what you had done, manual install.
the only crappy part of that is the reinstall's needed after kernel upgrades. (the price we pay :))
And good work, you won't soon forget.  ;)

---

