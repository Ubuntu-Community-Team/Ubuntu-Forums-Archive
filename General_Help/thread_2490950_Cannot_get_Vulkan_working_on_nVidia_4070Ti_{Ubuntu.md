---
title: "Cannot get Vulkan working on nVidia 4070Ti {Ubuntu 22.04}"
date: 2023-09-21
forum: General Help
---

### Post by yoshmaista on 2023-09-21
I've been trying to game on this card in Ubuntu for a while now, but can't seem to find the answer as to why Vulkan only recognizes the CPU, and not the GPU (causing all launched games to never..well...launch).

Here's the vulkan info:

```
(base) yosh@yoshdesk:~$ vulkaninfo --summaryCan't open bumblebee display.
ERROR: [Loader Message] Code 0 : loader_scanned_icd_add: ICD libnv_vulkan_wrapper.so.1 doesn't support interface version compatible with loader, skip this ICD.
==========
VULKANINFO
==========


Vulkan Instance Version: 1.3.204




Instance Extensions: count = 20
-------------------------------
VK_EXT_acquire_drm_display             : extension revision 1
VK_EXT_acquire_xlib_display            : extension revision 1
VK_EXT_debug_report                    : extension revision 10
VK_EXT_debug_utils                     : extension revision 2
VK_EXT_direct_mode_display             : extension revision 1
VK_EXT_display_surface_counter         : extension revision 1
VK_EXT_swapchain_colorspace            : extension revision 4
VK_KHR_device_group_creation           : extension revision 1
VK_KHR_display                         : extension revision 23
VK_KHR_external_fence_capabilities     : extension revision 1
VK_KHR_external_memory_capabilities    : extension revision 1
VK_KHR_external_semaphore_capabilities : extension revision 1
VK_KHR_get_display_properties2         : extension revision 1
VK_KHR_get_physical_device_properties2 : extension revision 2
VK_KHR_get_surface_capabilities2       : extension revision 1
VK_KHR_surface                         : extension revision 25
VK_KHR_surface_protected_capabilities  : extension revision 1
VK_KHR_wayland_surface                 : extension revision 6
VK_KHR_xcb_surface                     : extension revision 6
VK_KHR_xlib_surface                    : extension revision 6


Instance Layers: count = 9
--------------------------
VK_LAYER_INTEL_nullhw             INTEL NULL HW                                        1.1.73   version 1
VK_LAYER_KHRONOS_validation       Khronos Validation Layer                             1.3.204  version 1
VK_LAYER_MESA_device_select       Linux device selection layer                         1.3.211  version 1
VK_LAYER_MESA_overlay             Mesa Overlay layer                                   1.3.211  version 1
VK_LAYER_PRIMUS_PrimusVK          Primus-vk - https://github.com/felixdoerre/primus_vk 1.2.0    version 1
VK_LAYER_VALVE_steam_fossilize_32 Steam Pipeline Caching Layer                         1.3.207  version 1
VK_LAYER_VALVE_steam_fossilize_64 Steam Pipeline Caching Layer                         1.3.207  version 1
VK_LAYER_VALVE_steam_overlay_32   Steam Overlay Layer                                  1.3.207  version 1
VK_LAYER_VALVE_steam_overlay_64   Steam Overlay Layer                                  1.3.207  version 1


Devices:
========
GPU0:
	apiVersion         = 4206830 (1.3.238)
	driverVersion      = 1 (0x0001)
	vendorID           = 0x10005
	deviceID           = 0x0000
	deviceType         = PHYSICAL_DEVICE_TYPE_CPU
	deviceName         = llvmpipe (LLVM 15.0.7, 256 bits)
	driverID           = DRIVER_ID_MESA_LLVMPIPE
	driverName         = llvmpipe
	driverInfo         = Mesa 23.0.4-0ubuntu1~22.04.1 (LLVM 15.0.7)
	conformanceVersion = 1.3.1.1
	deviceUUID         = 6d657361-3233-2e30-2e34-2d3075627500
	driverUUID         = 6c6c766d-7069-7065-5555-494400000000
```

nVidia-SMI:
```

+---------------------------------------------------------------------------------------+
| NVIDIA-SMI 535.104.05             Driver Version: 535.104.05   CUDA Version: 12.2     |
|-----------------------------------------+----------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |         Memory-Usage | GPU-Util  Compute M. |
|                                         |                      |               MIG M. |
|=========================================+======================+======================|
|   0  NVIDIA GeForce RTX 4070 Ti     On  | 00000000:26:00.0  On |                  N/A |
|  0%   43C    P2              34W / 285W |    785MiB / 12282MiB |      7%      Default |
|                                         |                      |                  N/A |
+-----------------------------------------+----------------------+----------------------+
                                                                                         
+---------------------------------------------------------------------------------------+
| Processes:                                                                            |
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory |
|        ID   ID                                                             Usage      |
|=======================================================================================|
|    0   N/A  N/A      4535      G   /usr/lib/xorg/Xorg                          273MiB |
|    0   N/A  N/A      4656    C+G   ...libexec/gnome-remote-desktop-daemon      195MiB |
|    0   N/A  N/A      4696      G   /usr/bin/gnome-shell                        151MiB |
|    0   N/A  N/A      5355      G   .../bridge-v3/updates/3.4.2/bridge-gui       17MiB |
|    0   N/A  N/A      5692      G   ...776964397,334027382103122624,262144      124MiB |
+---------------------------------------------------------------------------------------+




```

---

### Post by #&amp;thj^% on 2023-09-21
What Game /or Games?
```
==========
VULKANINFO
==========

Vulkan Instance Version: 1.3.250


Instance Extensions: count = 23
-------------------------------
VK_EXT_acquire_drm_display             : extension revision 1
VK_EXT_acquire_xlib_display            : extension revision 1
VK_EXT_debug_report                    : extension revision 10
VK_EXT_debug_utils                     : extension revision 2
VK_EXT_direct_mode_display             : extension revision 1
VK_EXT_display_surface_counter         : extension revision 1
VK_EXT_surface_maintenance1            : extension revision 1
VK_EXT_swapchain_colorspace            : extension revision 4
VK_KHR_device_group_creation           : extension revision 1
VK_KHR_display                         : extension revision 23
VK_KHR_external_fence_capabilities     : extension revision 1
VK_KHR_external_memory_capabilities    : extension revision 1
VK_KHR_external_semaphore_capabilities : extension revision 1
VK_KHR_get_display_properties2         : extension revision 1
VK_KHR_get_physical_device_properties2 : extension revision 2
VK_KHR_get_surface_capabilities2       : extension revision 1
VK_KHR_portability_enumeration         : extension revision 1
VK_KHR_surface                         : extension revision 25
VK_KHR_surface_protected_capabilities  : extension revision 1
VK_KHR_wayland_surface                 : extension revision 6
VK_KHR_xcb_surface                     : extension revision 6
VK_KHR_xlib_surface                    : extension revision 6
VK_LUNARG_direct_driver_loading        : extension revision 1

Instance Layers: count = 4
--------------------------
VK_LAYER_INTEL_nullhw       INTEL NULL HW                1.1.73   version 1
VK_LAYER_MESA_device_select Linux device selection layer 1.3.211  version 1
VK_LAYER_MESA_overlay       Mesa Overlay layer           1.3.211  version 1
VK_LAYER_NV_optimus         NVIDIA Optimus layer         1.3.242  version 1

Devices:
========
GPU0:
	apiVersion         = 1.3.246
	driverVersion      = 23.1.7
	vendorID           = 0x1002
	deviceID           = 0x1636
	deviceType         = PHYSICAL_DEVICE_TYPE_INTEGRATED_GPU
	deviceName         = AMD Radeon Graphics (RADV RENOIR)
	driverID           = DRIVER_ID_MESA_RADV
	driverName         = radv
	driverInfo         = Mesa 23.1.7-1ubuntu1
	conformanceVersion = 1.2.7.1
	deviceUUID         = 00000000-0500-0000-0000-000000000000
	driverUUID         = 414d442d-4d45-5341-2d44-525600000000
GPU1:
	apiVersion         = 1.3.242
	driverVersion      = 535.104.5.320
	vendorID           = 0x10de
	deviceID           = 0x1f95
	deviceType         = PHYSICAL_DEVICE_TYPE_DISCRETE_GPU
	deviceName         = NVIDIA GeForce GTX 1650 Ti
	driverID           = DRIVER_ID_NVIDIA_PROPRIETARY
	driverName         = NVIDIA
	driverInfo         = 535.104.05
	conformanceVersion = 1.3.5.0
	deviceUUID         = c6f98d81-557d-7bfd-8af2-b62d3540d330
	driverUUID         = 0415fb4e-e904-5af7-8fad-a705dd68f35e
GPU2:
	apiVersion         = 1.3.246
	driverVersion      = 0.0.1
	vendorID           = 0x10005
	deviceID           = 0x0000
	deviceType         = PHYSICAL_DEVICE_TYPE_CPU
	deviceName         = llvmpipe (LLVM 15.0.7, 256 bits)
	driverID           = DRIVER_ID_MESA_LLVMPIPE
	driverName         = llvmpipe
	driverInfo         = Mesa 23.1.7-1ubuntu1 (LLVM 15.0.7)
	conformanceVersion = 1.3.1.1
	deviceUUID         = 6d657361-3233-2e31-2e37-2d3175627500
	driverUUID         = 6c6c766d-7069-7065-5555-494400000000

```
And 
```
apt policy   vulkan-tools
vulkan-tools:
  Installed: 1.3.250.0+dfsg1-1
  Candidate: 1.3.250.0+dfsg1-1
  Version table:
 *** 1.3.250.0+dfsg1-1 500
        500 http://us.archive.ubuntu.com/ubuntu mantic/universe amd64 Packages
        100 /var/lib/dpkg/status

```
```
nvidia-smi | grep Driver
| NVIDIA-SMI 535.104.05             Driver Version: 535.104.05   CUDA Version: 12.2     |

```

---

### Post by yoshmaista on 2023-09-21
Any game that involves utilizing the GPU.  Only game I can get working is RimWorld, which I'm pretty sure is all CPU.

---

### Post by #&amp;thj^% on 2023-09-21
Please run the "system-info script" in my signature, with the "--details" flag
Post back the Link it gives you in your next post.
Like this:
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/system-info/raw/main/system-info && \
chmod +x system-info && \
./system-info --details
```
That will give us somethings to go on.

---

### Post by yoshmaista on 2023-09-21
[https://termbin.com/ngfw](https://termbin.com/ngfw)

---

### Post by #&amp;thj^% on 2023-09-21
Thank you,  looking at it now, but i need some clarity:
```
cd /etc/apt/sources.list.d/ && ls

```
This I need to see.

---

### Post by yoshmaista on 2023-09-21
(base) yosh@yoshdesk:/mnt/wdblack/ModelAIFinal$ cd /etc/apt/sources.list.d/ && ls
amdgpu.list                                                                                       deadsnakes-ubuntu-ppa-jammy.list
archive_uri-http_developer_download_nvidia_com_compute_cuda_repos_ubuntu2004_x86_64_-jammy.list   graphics-drivers-ubuntu-ppa-jammy.list
archive_uri-https_developer_download_nvidia_com_compute_cuda_repos_ubuntu2204_x86_64_-jammy.list  nvidia-cuda.list
bazel.list                                                                                        nv-tensorrt-local-ubuntu2204-8.6.1-cuda-11.8.list
cappelikan-ubuntu-ppa-jammy.list                                                                  nv-tensorrt-local-ubuntu2204-8.6.1-cuda-12.0.list
cuda.list                                                                                         protonvpn-stable.list
cudnn-local-ubuntu2204-8.9.3.28.list                                                              rocm.list

---

### Post by #&amp;thj^% on 2023-09-21
I'm not going to be able to help you my friend.
No Code Tags so this:
```
 cd /etc/apt/sources.list.d/ && ls
amdgpu.list deadsnakes-ubuntu-ppa-jammy.list
archive_uri-http_developer_download_nvidia_com_compute_cuda_re pos_ubuntu2004_x86_64_-jammy.list graphics-drivers-ubuntu-ppa-jammy.list
archive_uri-https_developer_download_nvidia_com_compute_cuda_r epos_ubuntu2204_x86_64_-jammy.list nvidia-cuda.list
bazel.list nv-tensorrt-local-ubuntu2204-8.6.1-cuda-11.8.list
cappelikan-ubuntu-ppa-jammy.list nv-tensorrt-local-ubuntu2204-8.6.1-cuda-12.0.list
cuda.list protonvpn-stable.list
cudnn-local-ubuntu2204-8.9.3.28.list rocm.list 
```
Those source's are behind your problem though, and perhaps a bad Grub edit as well.

---

### Post by yoshmaista on 2023-09-21
I haven't touched grub in a way that should've affected it.  The sources might be behind my problem but I still don't know how to debug/fix that :/  Tired of having to boot into windows just to enjoy my games ;(

---

### Post by #&amp;thj^% on 2023-09-21
Are the Nvidia PPA and AMD PPA necessary?
My rig is fairly close to yours, and I do not have problems.

---

### Post by yoshmaista on 2023-09-22
The AMD one isn't, the nVidia ones are.  I do some machine learning stuff on this system.

---

### Post by MAFoElffen on 2023-09-23
Sorry for the drop in... I *had* to comment.

Wow... 

I want to be kind, but... What a jumble of things from many different sources, all installed in a way, that I suspect that you have many conflicts.

You say you are doing some "*AI machine learning stuff*". Expand on that explanation please. Keep in mind that I am a programmer, and I also game my main workstation to unwind...

I am a little familiar at reading the output from the 'system-info' report. (LOL)

This is his /etc/apt/sources.list.d from the report:
```

Sources List from SourcesD:
/etc/apt/sources.list.d/archive_uri-https_developer_download_nvidia_com_compute_cuda_repos_ubuntu2204_x86_64_-jammy.list:
deb https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/ /
/etc/apt/sources.list.d/amdgpu.list:
deb [arch=amd64 signed-by=/etc/apt/keyrings/rocm.gpg] https://repo.radeon.com/amdgpu/latest/ubuntu focal main
/etc/apt/sources.list.d/archive_uri-http_developer_download_nvidia_com_compute_cuda_repos_ubuntu2004_x86_64_-jammy.list:
deb http://developer.download.nvidia.com/compute/cuda/repos/ubuntu2004/x86_64/ /
/etc/apt/sources.list.d/cudnn-local-ubuntu2204-8.9.3.28.list:
deb [signed-by=/usr/share/keyrings/cudnn-local-BD12C98D-keyring.gpg] file:///var/cudnn-local-repo-ubuntu2204-8.9.3.28 /
/etc/apt/sources.list.d/deadsnakes-ubuntu-ppa-jammy.list:
deb https://ppa.launchpadcontent.net/deadsnakes/ppa/ubuntu/ jammy main
/etc/apt/sources.list.d/nv-tensorrt-local-ubuntu2204-8.6.1-cuda-12.0.list:
deb [signed-by=/usr/share/keyrings/nv-tensorrt-local-42B2FC56-keyring.gpg] file:///var/nv-tensorrt-local-repo-ubuntu2204-8.6.1-cuda-12.0 /
/etc/apt/sources.list.d/nvidia-cuda.list:
deb https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2004/x86_64 /
/etc/apt/sources.list.d/cuda.list:
deb http://deb.debian.org/debian buster-backports main contrib non-free
/etc/apt/sources.list.d/bazel.list:
deb [arch=amd64] https://storage.googleapis.com/bazel-apt stable jdk1.8
/etc/apt/sources.list.d/nv-tensorrt-local-ubuntu2204-8.6.1-cuda-11.8.list:
deb [signed-by=/usr/share/keyrings/nv-tensorrt-local-0628887B-keyring.gpg] file:///var/nv-tensorrt-local-repo-ubuntu2204-8.6.1-cuda-11.8 /
/etc/apt/sources.list.d/protonvpn-stable.list:
deb [arch="all", signed-by=/usr/share/keyrings/protonvpn-stable-archive-keyring.gpg] https://repo.protonvpn.com/debian stable main
/etc/apt/sources.list.d/graphics-drivers-ubuntu-ppa-jammy.list:
deb https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu/ jammy main
/etc/apt/sources.list.d/cappelikan-ubuntu-ppa-jammy.list:
deb https://ppa.launchpadcontent.net/cappelikan/ppa/ubuntu/ jammy main
/etc/apt/sources.list.d/rocm.list:
deb [arch=amd64 signed-by=/etc/apt/keyrings/rocm.gpg] https://repo.radeon.com/rocm/apt/debian focal main

```
Where you have many duplicate cuda repo's because you have multitple versions installed... Showing in nvidia-smi is
```

NVIDIA-SMI 535.104.05             Driver Version: 535.104.05   CUDA Version: 12.2

```
But I also see 11.8, and 12.0???

Skip down to your user installed packages---
Via Apt:
```

cuda
cuda-toolkit-11-5
cuda-toolkit-12-2
libcudnn8
libcudnn8-dev
libglu1-mesa-dev
libnccl-dev
libnccl2
libnvidia-cfg1-535
libnvidia-common-535
libnvidia-container-dev
libnvidia-container-tools
libnvidia-container1
libnvidia-egl-wayland-dev
libnvidia-extra-535
libnvidia-fbc1-535
libnvidia-gl-535
libnvinfer-bin
libnvinfer-dev
libnvinfer-dispatch-dev
libnvinfer-dispatch8
libnvinfer-headers-dev
libnvinfer-headers-plugin-dev
libnvinfer-lean-dev
libnvinfer-lean8
libnvinfer-plugin-dev
libnvinfer-plugin8
libnvinfer-vc-plugin-dev
libnvinfer8
libnvvm4
libopenblas-dev
libpython3.11
libpython3.11-dev
libsmbclient-dev
libstdc++-9-dev-amd64-cross
libstdc++6-10-dbg-i386-cross
liburcu6
libvulkan-dev
libvulkan-volk-dev
libx11-dev
libx32stdc++-10-dev-amd64-cross
libx32stdc++6
libxi-dev
libxmu-dev
mesa-vulkan-drivers:i386
nv-tensorrt-local-repo-ubuntu2204-8.6.1-cuda-11.8
nv-tensorrt-local-repo-ubuntu2204-8.6.1-cuda-12.0
nvidia-compute-utils-535
nvidia-container-toolkit
nvidia-dkms-535
nvidia-driver-530
nvidia-driver-535
nvidia-kernel-source-535
nvidia-opencl-dev
nvidia-primus-vk-common
nvidia-primus-vk-wrapper
nvidia-settings
nvidia-utils-535
primus-nvidia
pybind11-dev
python-is-python3
python-pytools-doc
python3-aiohttp
python3-asyncssh
python3-bs4
python3-convertdate
python3-dev
python3-flatbuffers
python3-gast
python3-holidays
python3-lxml
python3-nltk
python3-numba
python3-numpy
python3-pandas
python3-pip
python3-praw
python3-prawcore
python3-psutil
python3-pydrive
python3-pypdf2
python3-pytools
python3-retrying
python3-scp
python3-selenium
python3-setuptools
python3-smbus
python3-sshpubkeys
python3-translate
python3-venv
python3.11-dev
python3.8
python3.9
vulkan-tools
vulkan-validationlayers-dev
xserver-xorg-video-nvidia-535

```
Via Snap:
```

gaming-graphics-core22
jupyter
mesa-core20
pyqt5-runtime-core20
pyqt5-runtime-lite
qt5-core20

```
Via FlatPak:
```

Freedesktop
Freedesktop
i386
i386
Mesa
Mesa
Mesa
Mesa
nvidia-535-104-05
Mesa
Mesa
Mesa
nvidia-535-104-05
i386

```
You have Mesa installed from apt, snap and flatpak?

You have been busy...

Now look at my workstation (mostly zero in on the User Installed packages, specifically mesa and vulcan): [https://paste.ubuntu.com/p/9FY5XgWX4d/](https://paste.ubuntu.com/p/9FY5XgWX4d/)
```

mafoelffen@msi-ubuntu:~$ nvidia-smi
Fri Sep 22 20:58:06 2023       
+---------------------------------------------------------------------------------------+
| NVIDIA-SMI 535.86.05              Driver Version: 535.86.05    CUDA Version: 12.2     |
|-----------------------------------------+----------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |         Memory-Usage | GPU-Util  Compute M. |
|                                         |                      |               MIG M. |
|=========================================+======================+======================|
|   0  NVIDIA GeForce GTX 1660 Ti     Off | 00000000:01:00.0  On |                  N/A |
|  0%   34C    P8               7W / 130W |     99MiB /  6144MiB |      2%      Default |
|                                         |                      |                  N/A |
+-----------------------------------------+----------------------+----------------------+
                                                                                         
+---------------------------------------------------------------------------------------+
| Processes:                                                                            |
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory |
|        ID   ID                                                             Usage      |
|=======================================================================================|
|    0   N/A  N/A      5643      G   /usr/lib/xorg/Xorg                           68MiB |
|    0   N/A  N/A      6984      G   /usr/bin/gnome-shell                         29MiB |
+---------------------------------------------------------------------------------------+

```
Then on Vulcan:
```

mafoelffen@msi-ubuntu:~$ vulkaninfo | grep 'Instance Version' && echo '' && vulkaninfo | grep -A 40 -iE 'Device Groups'
Vulkan Instance Version: 1.3.204

Device Groups:
==============
Group 0:
    Properties:
        physicalDevices: count = 1
            llvmpipe (LLVM 15.0.7, 256 bits) (ID: 0)
        subsetAllocation = 0

    Present Capabilities:
        llvmpipe (LLVM 15.0.7, 256 bits) (ID: 0):
            Can present images from the following devices: count = 1
                llvmpipe (LLVM 15.0.7, 256 bits) (ID: 0)
        Present modes: count = 1
            DEVICE_GROUP_PRESENT_MODE_LOCAL_BIT_KHR

Group 1:
    Properties:
        physicalDevices: count = 1
            Intel(R) Graphics (RPL-S) (ID: 0)
        subsetAllocation = 0

    Present Capabilities:
        Intel(R) Graphics (RPL-S) (ID: 0):
            Can present images from the following devices: count = 1
                Intel(R) Graphics (RPL-S) (ID: 0)
        Present modes: count = 1
            DEVICE_GROUP_PRESENT_MODE_LOCAL_BIT_KHR

Group 2:
    Properties:
        physicalDevices: count = 1
            NVIDIA GeForce GTX 1660 Ti (ID: 0)
        subsetAllocation = 0

    Present Capabilities:
        NVIDIA GeForce GTX 1660 Ti (ID: 0):
            Can present images from the following devices: count = 1
                NVIDIA GeForce GTX 1660 Ti (ID: 0)
        Present modes: count = 1
            DEVICE_GROUP_PRESENT_MODE_LOCAL_BIT_KHR

```
Then on mesa:
```

mafoelffen@msi-ubuntu:~$ glxinfo | grep -iE 'display|direct rendering|Version'
name of display: localhost:10.0
display: localhost:10  screen: 0
direct rendering: Yes
server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.4
OpenGL core profile version string: 4.6.0 NVIDIA 535.86.05
OpenGL core profile shading language version string: 4.60 NVIDIA
OpenGL version string: 4.6.0 NVIDIA 535.86.05
OpenGL shading language version string: 4.60 NVIDIA
OpenGL ES profile version string: OpenGL ES 3.2 NVIDIA 535.86.05
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20
    GL_EXT_shader_group_vote, GL_EXT_shader_implicit_conversions, 

```

---

### Post by yoshmaista on 2023-09-24
Sorry if my setup offends you, but I'm still learning linux.  I just started using it as my main OS less than 6 months ago--my last exposure before then was running Gentoo for about 6 hours as a teenager.

At the end of the day though, it's not your setup so why are you upset?

---

### Post by MAFoElffen on 2023-09-24
LOL. Don't take that personally. It does not offend me. No emotions in that at all. I am just trying to figure out what your plan and goal was with that. Please reread my post after reading this post. I think you might have a different perspective of what I wrote.

What are your goals? That will lead me to know what you want to do, and what you really need left there. No sense in recommending that you remove CUDA if that is what you want and need to do. Or to remove two specific Mesa drivers of the 3 Mesa drivers installed, if a version of it would work and fit better to what you are doing. Right? (I am trying to get some clarity and direction from you.)

That would guide us to a path on what needs to be left there, by what is required to get to your goals. 

My goal is to help Users get to their goals.

Sorry you read between the lines and took that wrong.  Does that make sense?

EDIT: For example, having multiple CUDA version repo's defined in your sources is most likely going to cause conflicts, when those repo's go to update, with packages between the versions with the same names. The names that include versions of will not update. They will point to a new package in the newer repo... But if they backport a package in the older repo, then it will try to install that, which will break CUDA from conflicting packages of different versions. NVidia's recommendations in their doc's are to completely uninstall the old version, before installing the new version. Multiple versions of CUDA cannot coexist.

RE from NVidia: [https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html](https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html)
```

 2.9. Handle Conflicting Installation Methods

Before installing CUDA, [COLOR=#ff0000]any previous installations that could conflict should be uninstalled[/COLOR]. This will not affect 
systems which have not had CUDA installed previously, or systems where the installation method has been preserved 
(RPM/Deb vs. Runfile). See the following charts for specifics.
...

```
I have been supporting Users using high-end GPU's with Linux and Unix since 2005... I sincerely and honestly "am" really trying to help you.

EDIT: Note that you might have to uninstall all conflicting packages, just to get a clean install of what will work. Just a pro-active warning about that "that" might be in the recommendation. For example, I recommend to Users that they uninstall and purge all old NVidia Graphics drivers before installing the newer driver... That just resolves a lot of problems for people on what might be left over, and what may cause any further conflicts down the road.

---

### Post by #&amp;thj^% on 2023-09-25
Yes in post #14, would explain some of your issues. 
**Disclaimer:**  MAFoElffen will bend over backwards to help a user, all he is saying there is some improvements you could if willing to change. ;)

But I do wonder how you took any of this personal, lots of times "matter of fact statements" are just that, with NO extra feelings or emotions.
Relax a bit and enjoy your learning journey. For the *most* part this is one of the friendliest forums around.

---

