---
title: "Cannot get OpenCl to recognize AMD GPU (RX 480) after installing amdgpu-pro drivers"
date: 2020-12-09
forum: General Help
---

### Post by orangepeeler on 2020-12-09
After installing AMD's GPU drivers [here]("https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-20-20") (specifically "version 20.20 for Ubuntu 20.04"), "lspci" correctly displays the GPU, but "clinfo" doesn't recognize any OpenCl devices.


To install the drivers I unarchived the tarball and ran "./amdgpu-pro-install -y --opencl=pal,legacy --headless" and "sudo usermod -a -G video $LOGNAME".


The command "lspci -nn | grep -E 'VGA|Display'" properly displays the installed GPU:
```
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere [Radeon RX 470/480/570/570X/580/580X/590] [1002:67df] (rev c7)
```


But when I run "clinfo" I get an output of
```

Number of platforms 2  Platform Name                                   AMD Accelerated Parallel Processing
 Platform Vendor                                 Advanced Micro Devices, Inc.
 Platform Version                                OpenCL 2.1 AMD-APP (3110.6)
 Platform Profile                                FULL_PROFILE
 Platform Extensions                             cl_khr_icd cl_amd_event_callback cl_amd_offline_devices 
 Platform Host timer resolution                  1ns
 Platform Extensions function suffix             AMD




 Platform Name                                   Clover
 Platform Vendor                                 Mesa
 Platform Version                                OpenCL 1.1 Mesa 20.0.8
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


It shows no devices and no platform.


After searching around I tried running "sudo apt-get install ocl-icd-opencl-dev," but that package was already installed.
Any help would be very appreciated. Please let me know if there is any information I could add that may be useful.

---

### Post by CelticWarrior on 2020-12-10
Disable Secure Boot in UEFI and check again.

---

### Post by orangepeeler on 2020-12-10
Hello! As far as I can tell this computer (HP Compaq 8000) doesn’t have UEFI.

---

### Post by CelticWarrior on 2020-12-10
My bad, it is old indeed. And because of that you didn't have to install any AMD drivers. Amdgpu does NOT support your graphics card.

---

### Post by orangepeeler on 2020-12-10
Where do you see that it is not supported? In the compatible devices list ([https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-20-20](https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-20-20)) I can see the RX 480 listed. Is it something to do with the old hardware?

---

### Post by QIII on 2020-12-10
@orangepeeler

Please use the default font and color in your posts.  I have modified the first post in this thread.

---

### Post by orangepeeler on 2020-12-10
Sorry about that. I'll do that in the future. Thanks for letting me know!

---

