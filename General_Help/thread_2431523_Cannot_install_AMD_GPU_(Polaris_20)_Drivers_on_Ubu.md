---
title: "Cannot install AMD GPU (Polaris 20) Drivers on Ubuntu 18.04.3 with kernel 4.15"
date: 2019-11-17
forum: General Help
---

### Post by addict2 on 2019-11-17
Hi All,

ive been pulling my hair out over the past 48hrs trying to get an RX570 installed on ANY version of Ubuntu, i have tried every version from 18.04.1 to 19.04. i have read a bunch of resources and it looks like 18.04.3 with kernel 4.15 was my best hope ( i have also tried kernel 5.0 and 4.18 but no luck ), I cannot get OpenCL to detect any platforms. i have tried AMD driver version(s) 18.50, 19.10 and 19.30. what you see below is for driver version 19.30, using "./amdgpu-install --opencl=legacy" install command. ANY help would be much appreciate.. im really out of ideas now. this is as far as i can get:

```
user@blah11:~$ clinfoNumber of platforms                               1
  Platform Name                                   AMD Accelerated Parallel Processing
  Platform Vendor                                 Advanced Micro Devices, Inc.
  Platform Version                                OpenCL 2.1 AMD-APP (2906.7)
  Platform Profile                                FULL_PROFILE
  Platform Extensions                             cl_khr_icd cl_amd_event_callback cl_amd_offline_devices
  Platform Host timer resolution                  1ns
  Platform Extensions function suffix             AMD


  Platform Name                                   AMD Accelerated Parallel Processing
Number of devices                                 0


NULL platform behavior
  clGetPlatformInfo(NULL, CL_PLATFORM_NAME, ...)  No platform
  clGetDeviceIDs(NULL, CL_DEVICE_TYPE_ALL, ...)   No platform
  clCreateContext(NULL, ...) [default]            No platform
  clCreateContext(NULL, ...) [other]              <error: no devices in non-default plaforms>
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_DEFAULT)  No devices found in platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_CPU)  No devices found in platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_GPU)  No devices found in platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_ACCELERATOR)  No devices found in platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_CUSTOM)  No devices found in platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_ALL)  No devices found in platform


user@blah11:~$ glxinfo -B
Error: unable to open display


user@blah11:~$ glxinfo | grep -i opengl
Error: unable to open display


user@blah11:~$ uname -r
4.15.0-47-generic


user@blah11:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.3 LTS
Release:        18.04
Codename:       bionic



```

---

### Post by CatKiller on 2019-11-18
I don't use AMD graphics, but I was under the impression that you need the proprietary bits of AMDGPU-PRO, rather than the open source AMDGPU, if you want to use OpenCL. I found some instructions [here](https://linuxconfig.org/install-opencl-for-the-amdgpu-open-source-drivers-on-debian-and-ubuntu) for just installing the OpenCL parts, or you could go with AMDGPU-PRO for the whole stack. I'll readily admit that AMD's drivers confuse me, though.

---

