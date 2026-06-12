---
title: "opencl: &quot;No devices found in platform&quot; when PuTTy/SSH into ubuntu 20.04"
date: 2020-05-27
forum: General Help
---

### Post by myzis on 2020-05-27
Hi all,

TL;DR
I have an AMD gpu installed on my Ubuntu 20.04 and everything works when I'm locally connected to a monitor and all and clinfo shows opencl working. When I unplug screen, mouse, keyboard and try to SSH with a PuTTY from my windows machine, clinfo shows "No devices found in platform" for OpenCL.

New to the Ubuntu community. Searched a while the forum and couldn't find an answer.. What could be the root cause and is there a fix? Would appreciate some pointers so that I can figure this out.

Note: I did a little hack to install AMD PRO GPU on 20.04 by following this: [https://www.reddit.com/r/Kubuntu/comments/g79lp8/ive_got_the_amd_pro_gpu_driver_working_in_2004_if/](https://www.reddit.com/r/Kubuntu/comments/g79lp8/ive_got_the_amd_pro_gpu_driver_working_in_2004_if/)

Here's what I'm getting from clinfo: 
```
Number of platforms                               2  Platform Name                                   AMD Accelerated Parallel Processing
  Platform Vendor                                 Advanced Micro Devices, Inc.
  Platform Version                                OpenCL 2.1 AMD-APP (3075.10)
  Platform Profile                                FULL_PROFILE
  Platform Extensions                             cl_khr_icd cl_amd_event_callback cl_amd_offline_devices
  Platform Host timer resolution                  1ns
  Platform Extensions function suffix             AMD


  Platform Name                                   Clover
  Platform Vendor                                 Mesa
  Platform Version                                OpenCL 1.1 Mesa 20.0.4
  Platform Profile                                FULL_PROFILE
  Platform Extensions                             cl_khr_icd
  Platform Extensions function suffix             MESA


  Platform Name                                   AMD Accelerated Parallel Processing
Number of devices                                 0


  Platform Name                                   Clover
Number of devices                                 0


NULL platform behavior
  clGetPlatformInfo(NULL, CL_PLATFORM_NAME, ...)  No platform
  clGetDeviceIDs(NULL, CL_DEVICE_TYPE_ALL, ...)   No platform
  clCreateContext(NULL, ...) [default]            No platform
  clCreateContext(NULL, ...) [other]              No platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_DEFAULT)  No devices found in platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_CPU)  No devices found in platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_GPU)  No devices found in platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_ACCELERATOR)  No devices found in platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_CUSTOM)  No devices found in platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_ALL)  No devices found in platform



```

Thanks.

---

### Post by CatKiller on 2020-05-27
I've never needed to use one, but apparently things like [this](https://www.amazon.co.uk/Headless-Display-Emulator-Headless-1920x1080-generation/dp/B06XT1Z9TF) can help with needing a display for things like remote desktop and GPGPU. You can get DisplayPort ones as well. They just plug in and say, "yes, I'm totally a display" for those things that don't auto-configure themselves when there's not a physical display present. That might be the easiest option.

---

### Post by myzis on 2020-05-28
Thank you! ok.. let me throw my money at the problem first ($8 for the headless displayport). Haven't thought about that!

Will revert back to this thread with a [SOLVED] tag, if it works. ETA EOW.

---

### Post by myzis on 2020-05-30
Still getting  "clCreateContextFromType(NULL, CL_DEVICE_TYPE_GPU)  No devices found in platform".. But another thing that I changed since is I plugged another GPU, so perhaps need to set it up more.. Will keep digging

---

