---
title: "Kernel Error: i2c i2c-1"
date: 2012-10-21
forum: General Help
---

### Post by cipherboy_loc on 2012-10-21
Could you advise how to fix this error that is spamming dmesg? 

```

**dmesg | grep -i 'i2c'**
[    4.703809] i2c i2c-1: >sendbytes: NAK bailout.
[    4.919393] i2c i2c-1: >sendbytes: NAK bailout.
[   25.648747] i2c i2c-3: >nForce2 SMBus adapter at 0x1c00
[   25.648902] i2c i2c-4: >nForce2 SMBus adapter at 0x1c40
[   28.852021] i2c i2c-1: >sendbytes: NAK bailout.
[   34.763800] i2c i2c-1: >sendbytes: NAK bailout.
[  115.186172] i2c i2c-1: >sendbytes: NAK bailout.
[  155.371620] i2c i2c-1: >sendbytes: NAK bailout.
[  175.467669] i2c i2c-1: >sendbytes: NAK bailout.
[  185.515588] i2c i2c-1: >sendbytes: NAK bailout.
[  266.027506] i2c i2c-1: >sendbytes: NAK bailout.
[  316.395464] i2c i2c-1: >sendbytes: NAK bailout.
[  326.443480] i2c i2c-1: >sendbytes: NAK bailout.
[  356.587449] i2c i2c-1: >sendbytes: NAK bailout.
[  376.683411] i2c i2c-1: >sendbytes: NAK bailout.
[  467.243322] i2c i2c-1: >sendbytes: NAK bailout.
[  477.291291] i2c i2c-1: >sendbytes: NAK bailout.
[  527.563267] i2c i2c-1: >sendbytes: NAK bailout.
[  547.697548] i2c i2c-1: >sendbytes: NAK bailout.
[  587.883196] i2c i2c-1: >sendbytes: NAK bailout.
[  607.979189] i2c i2c-1: >sendbytes: NAK bailout.
[  618.027281] i2c i2c-1: >sendbytes: NAK bailout.
[  688.529339] i2c i2c-1: >sendbytes: NAK bailout.
[  698.571137] i2c i2c-1: >sendbytes: NAK bailout.
[  738.827097] i2c i2c-1: >sendbytes: NAK bailout.
[  748.843090] i2c i2c-1: >sendbytes: NAK bailout.
[  768.971100] i2c i2c-1: >sendbytes: NAK bailout.
[  789.067094] i2c i2c-1: >sendbytes: NAK bailout.
[  869.591344] i2c i2c-1: >sendbytes: NAK bailout.
[  919.935081] i2c i2c-1: >sendbytes: NAK bailout.
[  940.043082] i2c i2c-1: >sendbytes: NAK bailout.
[  970.219085] i2c i2c-1: >sendbytes: NAK bailout.
[  990.315093] i2c i2c-1: >sendbytes: NAK bailout.
[ 1161.451076] i2c i2c-1: >sendbytes: NAK bailout.
[ 1191.595112] i2c i2c-1: >sendbytes: NAK bailout.
[ 1352.747118] i2c i2c-1: >sendbytes: NAK bailout.
[ 1574.091052] i2c i2c-1: >sendbytes: NAK bailout.
[ 1674.737207] i2c i2c-1: >sendbytes: NAK bailout.
[ 1896.138968] i2c i2c-1: >sendbytes: NAK bailout.
[ 1926.257040] i2c i2c-1: >sendbytes: NAK bailout.
[ 1946.359129] i2c i2c-1: >sendbytes: NAK bailout.
[ 2036.848991] i2c i2c-1: >sendbytes: NAK bailout.
[ 2127.338940] i2c i2c-1: >sendbytes: NAK bailout.
[ 2177.610918] i2c i2c-1: >sendbytes: NAK bailout.
[ 2247.933104] i2c i2c-1: >sendbytes: NAK bailout.
[ 2248.802167] i2c i2c-1: >sendbytes: NAK bailout.
[ 2257.962904] i2c i2c-1: >sendbytes: NAK bailout.
[ 2298.154868] i2c i2c-1: >sendbytes: NAK bailout.
[ 2308.170854] i2c i2c-1: >sendbytes: NAK bailout.
[ 2549.418941] i2c i2c-1: >sendbytes: NAK bailout.
[ 2629.834788] i2c i2c-1: >sendbytes: NAK bailout.
[ 2639.888813] i2c i2c-1: >sendbytes: NAK bailout.
[ 2660.011148] i2c i2c-1: >sendbytes: NAK bailout.
[ 2670.058843] i2c i2c-1: >sendbytes: NAK bailout.

``````

**lspci | grep -i 'nvidia'**
00:00.0 RAM memory: NVIDIA Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: NVIDIA Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: NVIDIA Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: NVIDIA Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: NVIDIA Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: NVIDIA Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: NVIDIA Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: NVIDIA Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: NVIDIA Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: NVIDIA Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: NVIDIA Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: NVIDIA Corporation C51 [GeForce 6150 LE] (rev a2)
00:09.0 RAM memory: NVIDIA Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: NVIDIA Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: NVIDIA Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: NVIDIA Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB controller: NVIDIA Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB controller: NVIDIA Corporation MCP51 USB Controller (rev a3)
00:0e.0 IDE interface: NVIDIA Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: NVIDIA Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: NVIDIA Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: NVIDIA Corporation MCP51 High Definition Audio (rev a2)

``````

**lsmod | grep 'i2c'**
i2c_nforce2            12869  0 
i2c_algo_bit           13197  1 nouveau

``````

**lsmod | grep 'nouveau'**
nouveau               823577  2 
ttm                    75534  1 nouveau
drm_kms_helper         45271  1 nouveau
drm                   230463  4 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13197  1 nouveau
mxm_wmi                12859  1 nouveau
video                  18847  1 nouveau
wmi                    18590  2 nouveau,mxm_wmi

``````

**uname -a**
Linux ubuntu-basement 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 i686 athlon i686 GNU/Linux

``````

**lsb_release -a**
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.10
Release:    12.10
Codename:    quantal

``````

**dpkg --list | grep  -i 'nvidia'**
ii  libcg:i386                                                  3.1.0013-1                                 i386         Nvidia Cg core runtime library
ii  libcggl:i386                                                3.1.0013-1                                 i386         Nvidia Cg Opengl runtime library
ii  nvclock                                                     0.8b4+cvs20100914-3                        i386         Overclock an NVIDIA card
ii  nvidia-96-modaliases                                        96.43.19-0ubuntu1                          i386         Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-cg-dev:i386                                          3.1.0013-1                                 i386         Cg Toolkit - GPU Shader Authoring Language (headers)
ii  nvidia-cg-toolkit                                           3.1.0013-1                                 i386         Cg Toolkit - GPU Shader Authoring Language
ii  nvidia-common                                               1:0.2.71                                   i386         transitional package for ubuntu-drivers-common

``````

**dpkg --list | grep  -i 'nouveau'**
ii  libdrm-nouveau1a:i386                                       2.4.39-0ubuntu1                            i386         Userspace interface to nouveau-specific kernel DRM services -- runtime
ii  libdrm-nouveau2:i386                                        2.4.39-0ubuntu1                            i386         Userspace interface to nouveau-specific kernel DRM services -- runtime
ii  xserver-xorg-video-nouveau                                  1:1.0.2-0ubuntu3                           i386         X.Org X server -- Nouveau display driver

```Thanks,
Cipherboy

---

### Post by cipherboy_loc on 2012-10-25
Bump.

---

### Post by dino99 on 2012-10-25
Seems a new bug regression into the kernel about nforce2 (maybe its not included, check the kernel module to know if it exist)

[http://ubuntuforums.org/showthread.php?t=1680530](http://ubuntuforums.org/showthread.php?t=1680530)  :P

---

### Post by cipherboy_loc on 2012-10-25
Lol, I saw that, no ATI hardware here, and stock Ubuntu kernel. The blog that supposedly held the solution for ATI is no longer available. In other words, it appears to be a regression, is there something to fix it?

---

### Post by dino99 on 2012-10-25
already reported but expired

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1015165](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1015165)

and that older one 

[https://bugs.launchpad.net/ubuntu/+source/linux-lts-backport-natty/+bug/852972](https://bugs.launchpad.net/ubuntu/+source/linux-lts-backport-natty/+bug/852972)

---

### Post by cipherboy_loc on 2012-10-25
So the other guy traced it to the nouveau driver, but says that an update resolved it. My system is up to date running 12.10. Wonder what fixed the bug in the earlier version.


Thanks,
Cipherboy

---

### Post by dino99 on 2012-10-25
> **cipherboy_loc said:**
> So the other guy traced it to the nouveau driver, but says that an update resolved it. My system is up to date running 12.10. Wonder what fixed the bug in the earlier version.


Thanks,
Cipherboy

yes but what im seeing with your output is related to nforce2. So the question now is to know if the actual kernel still drive that chip or not (which is called a regression). If its not a kernel issue , then the problem is with the video driver.

you have to check if nforce2 is a known kernel module (modprobe) and loaded. And try with some other kernel(s) and video driver to see the difference for narrowing down that issue.

---

### Post by cipherboy_loc on 2012-10-25
Okay, so I am going to leave this open for a bit more on the off chance it isn't fixed, but thus far, across 4 different boots today, I have not encountered any problems with the spamming, so keep your fingers crossed.

---

### Post by cipherboy_loc on 2012-11-01
Marking as solved. No further issues.

---

### Post by Sme377 on 2012-12-20
Hate to semi-necro a thread, but exactly what was the solution?

---

