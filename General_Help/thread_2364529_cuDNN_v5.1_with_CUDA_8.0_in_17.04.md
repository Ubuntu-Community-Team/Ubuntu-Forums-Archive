---
title: "cuDNN v5.1 with CUDA 8.0 in 17.04"
date: 2017-06-24
forum: General Help
---

### Post by Tanchistu on 2017-06-24
I have installed cuDNN  and CUDA a handfull of times before and it went smoothly. Now I can't seem to be able to find the right path where to copy the cuDNN files

It looks like CUDA is installed:

```
r@r-desktop:~$ nvcc -V
nvcc: NVIDIA (R) Cuda compiler driver
Copyright (c) 2005-2016 NVIDIA Corporation
Built on Sun_Sep__4_22:14:01_CDT_2016
Cuda compilation tools, release 8.0, V8.0.44
```

These are the instructions on the nVidia page:

> PREREQUISITES

    CUDA 7.0 and a GPU of compute capability 3.0 or higher are required.

ALL PLATFORMS

    Extract the cuDNN archive to a directory of your choice, referred to below as <installpath>.
    Then follow the platform-specific instructions as follows.

LINUX

    cd <installpath>
    export LD_LIBRARY_PATH=`pwd`:$LD_LIBRARY_PATH

    Add <installpath> to your build and link process by adding -I<installpath> to your compile
    line and -L<installpath> -lcudnn to your link line.

I definately don't understand exactly what is the logic behind the commands, and after I blindly follow them I fail to install cuDNN

---

### Post by howefield on 2017-06-24
Moved to the "*General Help*" forum.

---

### Post by case-bowman on 2017-07-02
+1

---

### Post by chris2471 on 2017-08-01
Just a hunch, try dpkg -L nvidia-cuda-toolkit

in most recent ubuntu you can install via apt-get and it puts things in a different organisational structure.

if its the case that it was installed by apt-get just stick the cudnn files in include in /usr/include and the lib64 files in /usr/lib.

---

