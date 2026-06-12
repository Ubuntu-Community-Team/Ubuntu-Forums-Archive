---
title: "Help with Nvidia drivers"
date: 2018-09-07
forum: General Help
---

### Post by aluk3s89 on 2018-09-07
Hi all, 
Im a new linux user, so im trying to understand everything what linux has to offer. But I have some problems. I have integrated intel gpu and nvidia gpu. I want my pc to use nvidia so ive updated all the drivers but my pc wont switch to nvidia 390 drivers in additional drivers section, when i click apply it just stops... Weird, and i cant open nvidia control program just wont open. If i check what is my active gpu card it say its intel... And also my gpu fan is not working... Can you help me guys pls with some lines of code im struggling with this last 3 days. Thnx

---

### Post by aluk3s89 on 2018-09-07
P.S I have newest version of ubuntu 18.04

---

### Post by Bashing-om on 2018-09-07
aluk3s89; Hello -

18.04 offers the Wayland (D)esktop (E)nvironment that nvidia has compatibility issues with.
To know the DE you are using:
```

echo $XDG_SESSION_TYPE

```
We will also want to know the hardware:
```

sudo lshw -C display

```
and what is installed for nvidia at this time:
```

lsmod | grep nvidia
dpkg -l | grep -i nvidia

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
we see where we go from here .

[INDENT][INDENT]'Tis a process
[/INDENT][/INDENT]

---

### Post by aluk3s89 on 2018-09-08
Sure maybe my message will be noobish dont know ho to make code boxes like you did but here it is 

```
echo $XDG_SESSION_TYPE 

x11
```

```
sudo lshw -C display

 *-display UNCLAIMED       
       description: 3D controller
       product: GM107M [GeForce GTX 860M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:ec000000-ecffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:ed000000-ed07ffff
  *-display
       description: VGA compatible controller
       product: 4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:28 memory:ed400000-ed7fffff memory:80000000-8fffffff ioport:f000(size=64) memory:c0000-dffff
```

And for the last code what is installed nvidia :

```
ii  libnvidia-cfg1-396:amd64                   396.54-0ubuntu0~gpu18.04.1          amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-390                       390.87-0ubuntu0~gpu18.04.1          all          Shared files used by the NVIDIA libraries
ii  libnvidia-common-396                       396.54-0ubuntu0~gpu18.04.1          all          Shared files used by the NVIDIA libraries
rc  libnvidia-compute-390:amd64                390.87-0ubuntu0~gpu18.04.1          amd64        NVIDIA libcompute package
rc  libnvidia-compute-390:i386                 390.87-0ubuntu0~gpu18.04.1          i386         NVIDIA libcompute package
ii  libnvidia-compute-396:amd64                396.54-0ubuntu0~gpu18.04.1          amd64        NVIDIA libcompute package
ii  libnvidia-compute-396:i386                 396.54-0ubuntu0~gpu18.04.1          i386         NVIDIA libcompute package
ii  libnvidia-decode-396:amd64                 396.54-0ubuntu0~gpu18.04.1          amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-396:i386                  396.54-0ubuntu0~gpu18.04.1          i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-396:amd64                 396.54-0ubuntu0~gpu18.04.1          amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-396:i386                  396.54-0ubuntu0~gpu18.04.1          i386         NVENC Video Encoding runtime library
ii  libnvidia-fbc1-396:amd64                   396.54-0ubuntu0~gpu18.04.1          amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-396:i386                    396.54-0ubuntu0~gpu18.04.1          i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
iU  libnvidia-ifr1-396:amd64                   396.54-0ubuntu0~gpu18.04.1          amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
iU  libnvidia-ifr1-396:i386                    396.54-0ubuntu0~gpu18.04.1          i386         NVIDIA OpenGL-based Inband Frame Readback runtime library
rc  nvidia-compute-utils-390                   390.87-0ubuntu0~gpu18.04.1          amd64        NVIDIA compute utilities
ii  nvidia-compute-utils-396                   396.54-0ubuntu0~gpu18.04.1          amd64        NVIDIA compute utilities
rc  nvidia-dkms-390                            390.87-0ubuntu0~gpu18.04.1          amd64        NVIDIA DKMS package
ii  nvidia-dkms-396                            396.54-0ubuntu0~gpu18.04.1          amd64        NVIDIA DKMS package
iU  nvidia-driver-396                          396.54-0ubuntu0~gpu18.04.1          amd64        NVIDIA driver metapackage
rc  nvidia-kernel-common-390                   390.87-0ubuntu0~gpu18.04.1          amd64        Shared files used with the kernel module
ii  nvidia-kernel-common-396                   396.54-0ubuntu0~gpu18.04.1          amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-396                   396.54-0ubuntu0~gpu18.04.1          amd64        NVIDIA kernel source package
rc  nvidia-opencl-icd-340                      340.107-0ubuntu0~gpu18.04.1         amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                               0.8.8                               all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                            396.54-0ubuntu0~gpu18.04.1          amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-396                           396.54-0ubuntu0~gpu18.04.1          amd64        NVIDIA driver support binaries
ii  xserver-xorg-video-nvidia-396              396.54-0ubuntu0~gpu18.04.1          amd64        NVIDIA binary Xorg driver
```

Hope you can help me because i really like linux so far :D

---

### Post by aluk3s89 on 2018-09-08
OK update Ive managed to fix it. I was so stupid. I was downloading nvidia 390 drivers instead of 340 for my gpu card. Thank you for trying to help me... Now when i go to system details in open gl my nvidia is listed so i hope my pc is using nvidia ...

---

### Post by Bashing-om on 2018-09-08
aluk3s89; Welp -

> 
 so i hope my pc is using nvidia ...

the 390 version driver is the correct one to install:
[https://www.nvidia.com/Download/driverResults.aspx/137276/en-us](https://www.nvidia.com/Download/driverResults.aspx/137276/en-us)

in that last 'dpkg -l | grep -i nvidia' showed a driver conflict - the reason why .

What is now installed ? show us a new :
```

dpkg -l | grep -i nvidia

```

[INDENT][INDENT]we make things right
[/INDENT][/INDENT]

---

### Post by aluk3s89 on 2018-09-09
It says that 390 is recommended one thats why Ive installed it. But, it didnt work and it crashed my system. And i stumbled upon a resource on line that explained that i am supposed to use 340 one instead 390 one... And now it works flawlessly ...

Here is the code

```

ii  libcuda1-340                               340.107-0ubuntu0~gpu18.04.1         amd64        NVIDIA CUDA runtime library
ii  libnvidia-common-390                       390.87-0ubuntu0~gpu18.04.1          all          Shared files used by the NVIDIA libraries
ii  libnvidia-common-396                       396.54-0ubuntu0~gpu18.04.1          all          Shared files used by the NVIDIA libraries
rc  libnvidia-compute-390:amd64                390.87-0ubuntu0~gpu18.04.1          amd64        NVIDIA libcompute package
rc  libnvidia-compute-390:i386                 390.87-0ubuntu0~gpu18.04.1          i386         NVIDIA libcompute package
rc  libnvidia-compute-396:amd64                396.54-0ubuntu0~gpu18.04.1          amd64        NVIDIA libcompute package
rc  libnvidia-compute-396:i386                 396.54-0ubuntu0~gpu18.04.1          i386         NVIDIA libcompute package
ii  nvidia-340                                 340.107-0ubuntu0~gpu18.04.1         amd64        NVIDIA binary driver - version 340.107
ii  nvidia-opencl-icd-340                      340.107-0ubuntu0~gpu18.04.1         amd64        NVIDIA OpenCL ICD
ii  nvidia-settings                            396.54-0ubuntu0~gpu18.04.1          amd64        Tool for configuring the NVIDIA graphics driver

```

---

### Post by Bashing-om on 2018-09-10
aluk3s89; Great ...

Pleased you fingered it out :)

340 is in the same family, as it works for you - more power to you .

As this thread is now concluded:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]good things do happen
[/INDENT][/INDENT]

---

