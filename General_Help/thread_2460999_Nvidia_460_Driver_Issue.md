---
title: "Nvidia 460 Driver Issue?"
date: 2021-04-22
forum: General Help
---

### Post by dwarthog on 2021-04-22
First if I have this in the wrong sub forum please move. 

I'm running 20.04 LTS with all of the current updates and everything seems to be ok however I think I may have an issue with the Nvidia 460 driver. 

The concern is that for some time now I have had the following items show up when running 'sudo apt list --upgradable' 

```
libxnvctrl0/focal-updates 460.39-0ubuntu0.20.04.1 amd64 [upgradable from: 440.82-0ubuntu0.20.04.1]
nvidia-prime/focal-updates,focal-updates 0.8.16~0.20.04.1 all [upgradable from: 0.8.15.3~0.20.04.1]
nvidia-settings/focal-updates 460.39-0ubuntu0.20.04.1 amd64 [upgradable from: 440.82-0ubuntu0.20.04.1]
```

When I check through the software updater interface which nvidia driver is in use it shows that I'm using the recommended 460 driver. 

So I guess the question is, why are those updates staying there and not being applied? 

I have done some poking around here but don't find anything that specifically matches this issue. 

Here is the output from dpkg -l | grep nvid

```
ii  libnvidia-cfg1-460:amd64                      460.56-0ubuntu0.20.04.1              amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-460                          460.56-0ubuntu0.20.04.1              all          Shared files used by the NVIDIA libraries
rc  libnvidia-compute-390:amd64                   390.116-0ubuntu0.18.04.1             amd64        NVIDIA libcompute package
rc  libnvidia-compute-390:i386                    390.116-0ubuntu0.18.04.1             i386         NVIDIA libcompute package
rc  libnvidia-compute-430:amd64                   430.50-0ubuntu0.18.04.2              amd64        NVIDIA libcompute package
rc  libnvidia-compute-435:amd64                   435.21-0ubuntu0.18.04.2              amd64        NVIDIA libcompute package
rc  libnvidia-compute-450:amd64                   450.80.02-0ubuntu0.20.04.2           amd64        NVIDIA libcompute package
rc  libnvidia-compute-455:amd64                   460.32.03-0ubuntu0.20.04.1           amd64        Transitional package for libnvidia-compute-460
ii  libnvidia-compute-460:amd64                   460.56-0ubuntu0.20.04.1              amd64        NVIDIA libcompute package
ii  libnvidia-compute-460:i386                    460.56-0ubuntu0.20.04.1              i386         NVIDIA libcompute package
ii  libnvidia-decode-460:amd64                    460.56-0ubuntu0.20.04.1              amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-460:i386                     460.56-0ubuntu0.20.04.1              i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-460:amd64                    460.56-0ubuntu0.20.04.1              amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-460:i386                     460.56-0ubuntu0.20.04.1              i386         NVENC Video Encoding runtime library
ii  libnvidia-extra-460:amd64                     460.56-0ubuntu0.20.04.1              amd64        Extra libraries for the NVIDIA driver
ii  libnvidia-fbc1-460:amd64                      460.56-0ubuntu0.20.04.1              amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-460:i386                       460.56-0ubuntu0.20.04.1              i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-460:amd64                        460.56-0ubuntu0.20.04.1              amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-460:i386                         460.56-0ubuntu0.20.04.1              i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-460:amd64                      460.56-0ubuntu0.20.04.1              amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  libnvidia-ifr1-460:i386                       460.56-0ubuntu0.20.04.1              i386         NVIDIA OpenGL-based Inband Frame Readback runtime library
rc  nvidia-compute-utils-390                      390.116-0ubuntu0.18.04.1             amd64        NVIDIA compute utilities
rc  nvidia-compute-utils-430                      430.50-0ubuntu0.18.04.2              amd64        NVIDIA compute utilities
rc  nvidia-compute-utils-435                      435.21-0ubuntu0.18.04.2              amd64        NVIDIA compute utilities
rc  nvidia-compute-utils-450                      450.80.02-0ubuntu0.20.04.2           amd64        NVIDIA compute utilities
ii  nvidia-compute-utils-460                      460.56-0ubuntu0.20.04.1              amd64        NVIDIA compute utilities
rc  nvidia-dkms-390                               390.116-0ubuntu0.18.04.1             amd64        NVIDIA DKMS package
rc  nvidia-dkms-430                               430.50-0ubuntu0.18.04.2              amd64        NVIDIA DKMS package
rc  nvidia-dkms-435                               435.21-0ubuntu0.18.04.2              amd64        NVIDIA DKMS package
rc  nvidia-dkms-450                               450.80.02-0ubuntu0.20.04.2           amd64        NVIDIA DKMS package
ii  nvidia-dkms-460                               460.56-0ubuntu0.20.04.1              amd64        NVIDIA DKMS package
ii  nvidia-driver-455                             460.56-0ubuntu0.20.04.1              amd64        Transitional package for nvidia-driver-460
ii  nvidia-driver-460                             460.56-0ubuntu0.20.04.1              amd64        NVIDIA driver metapackage
rc  nvidia-kernel-common-390                      390.116-0ubuntu0.18.04.1             amd64        Shared files used with the kernel module
rc  nvidia-kernel-common-430                      430.50-0ubuntu0.18.04.2              amd64        Shared files used with the kernel module
rc  nvidia-kernel-common-435                      435.21-0ubuntu0.18.04.2              amd64        Shared files used with the kernel module
rc  nvidia-kernel-common-450                      450.80.02-0ubuntu0.20.04.2           amd64        Shared files used with the kernel module
ii  nvidia-kernel-common-460                      460.56-0ubuntu0.20.04.1              amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-460                      460.56-0ubuntu0.20.04.1              amd64        NVIDIA kernel source package
**ii  nvidia-prime                                  0.8.15.3~0.20.04.1                   all          Tools to enable NVIDIA's Prime**
**ii  nvidia-settings                               440.82-0ubuntu0.20.04.1              amd64        Tool for configuring the NVIDIA graphics driver**
ii  nvidia-utils-460                              460.56-0ubuntu0.20.04.1              amd64        NVIDIA driver support binaries
ii  screen-resolution-extra                       0.18build1                           all          Extension for the nvidia-settings control panel
ii  xserver-xorg-video-nvidia-460                 460.56-0ubuntu0.20.04.1              amd64        NVIDIA binary Xorg driver

```

dpkg -l | grep libxnvc

```
ii  libxnvctrl0:amd64                             440.82-0ubuntu0.20.04.1              amd64        NV-CONTROL X extension (runtime library)

```

It sure looks like from the above output there is a mix of drivers being used. 

Not being certain if there is indeed an issue I would like to have a far more knowledgable person's opinion on this. 

Is this an issue? 

If so what is my best course of action to clean it up? 

Thanks in advance.

---

### Post by Bashing-om on 2021-04-22
dwarthog - Hey hey :D

Yup - conflict in drivers
> 
ii  nvidia-driver-455


Were me I would purge all nvida and have the system RE-install what it thinks best.
Make sure here that secure boot is disabled in bios and run:
```

sudo apt remove --purge nvidia-*
sudo apt update
sudo apt upgrade
sudo ubuntu-drivers autoinstall

```


Reboot required to see the effect.


The system is smart - and I have yet to know of an erorr on what the driver selection is.

[INDENT][INDENT]All in the process
[/INDENT][/INDENT]

---

### Post by Yellow Pasque on 2021-04-22
Show output of the second command (apt-get install):
```
sudo apt-get update
sudo apt-get install libxnvctrl0 nvidia-prime nvidia-settings
```

> **Bashing-om said:**
> Yup - conflict in drivers

No. nvidia-455 is just a transitional package that points to nvidia-460. It should not be hurting anything, though it can probably be removed.

---

### Post by dwarthog on 2021-04-23
@Yellow Pasque 

Here is the requested output from the second command you provided

It looks like that resolved the concern and upgraded those packages to the currently installed 460 driver. 

Thank you! 

sudo apt-get install libxnvctrl0 nvidia-prime nvidia-settings

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ipset libipset13 xsltproc
Use 'sudo apt autoremove' to remove them.
The following packages will be upgraded:
  libxnvctrl0 nvidia-prime nvidia-settings
3 upgraded, 0 newly installed, 0 to remove and 28 not upgraded.
Need to get 0 B/907 kB of archives.
After this operation, 247 kB disk space will be freed.
(Reading database ... 251111 files and directories currently installed.)
Preparing to unpack .../libxnvctrl0_460.39-0ubuntu0.20.04.1_amd64.deb ...
Unpacking libxnvctrl0:amd64 (460.39-0ubuntu0.20.04.1) over (440.82-0ubuntu0.20.04.1) ...
Preparing to unpack .../nvidia-prime_0.8.16~0.20.04.1_all.deb ...
Unpacking nvidia-prime (0.8.16~0.20.04.1) over (0.8.15.3~0.20.04.1) ...
Preparing to unpack .../nvidia-settings_460.39-0ubuntu0.20.04.1_amd64.deb ...
Unpacking nvidia-settings (460.39-0ubuntu0.20.04.1) over (440.82-0ubuntu0.20.04.1) ...
Setting up nvidia-prime (0.8.16~0.20.04.1) ...
Setting up libxnvctrl0:amd64 (460.39-0ubuntu0.20.04.1) ...
Setting up nvidia-settings (460.39-0ubuntu0.20.04.1) ...
Processing triggers for mime-support (3.64ubuntu1) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu1) ...
Processing triggers for libc-bin (2.31-0ubuntu9.2) ...
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for desktop-file-utils (0.24-1ubuntu3) ...


```


FYI


I noticed this morning that an update to the 460 driver hit the repositories. 

```
libnvidia-cfg1-460/focal-updates 460.73.01-0ubuntu0.20.04.1 amd64 [upgradable from: 460.56-0ubuntu0.20.04.1]
libnvidia-common-460/focal-updates,focal-updates 460.73.01-0ubuntu0.20.04.1 all [upgradable from: 460.56-0ubuntu0.20.04.1]
libnvidia-compute-460/focal-updates 460.73.01-0ubuntu0.20.04.1 amd64 [upgradable from: 460.56-0ubuntu0.20.04.1]
libnvidia-compute-460/focal-updates 460.73.01-0ubuntu0.20.04.1 i386 [upgradable from: 460.56-0ubuntu0.20.04.1]
libnvidia-decode-460/focal-updates 460.73.01-0ubuntu0.20.04.1 amd64 [upgradable from: 460.56-0ubuntu0.20.04.1]
libnvidia-decode-460/focal-updates 460.73.01-0ubuntu0.20.04.1 i386 [upgradable from: 460.56-0ubuntu0.20.04.1]
libnvidia-encode-460/focal-updates 460.73.01-0ubuntu0.20.04.1 amd64 [upgradable from: 460.56-0ubuntu0.20.04.1]
libnvidia-encode-460/focal-updates 460.73.01-0ubuntu0.20.04.1 i386 [upgradable from: 460.56-0ubuntu0.20.04.1]
libnvidia-extra-460/focal-updates 460.73.01-0ubuntu0.20.04.1 amd64 [upgradable from: 460.56-0ubuntu0.20.04.1]
libnvidia-fbc1-460/focal-updates 460.73.01-0ubuntu0.20.04.1 amd64 [upgradable from: 460.56-0ubuntu0.20.04.1]
libnvidia-fbc1-460/focal-updates 460.73.01-0ubuntu0.20.04.1 i386 [upgradable from: 460.56-0ubuntu0.20.04.1]
libnvidia-gl-460/focal-updates 460.73.01-0ubuntu0.20.04.1 amd64 [upgradable from: 460.56-0ubuntu0.20.04.1]
libnvidia-gl-460/focal-updates 460.73.01-0ubuntu0.20.04.1 i386 [upgradable from: 460.56-0ubuntu0.20.04.1]
libnvidia-ifr1-460/focal-updates 460.73.01-0ubuntu0.20.04.1 amd64 [upgradable from: 460.56-0ubuntu0.20.04.1]
libnvidia-ifr1-460/focal-updates 460.73.01-0ubuntu0.20.04.1 i386 [upgradable from: 460.56-0ubuntu0.20.04.1]
nvidia-compute-utils-460/focal-updates 460.73.01-0ubuntu0.20.04.1 amd64 [upgradable from: 460.56-0ubuntu0.20.04.1]
nvidia-dkms-460/focal-updates 460.73.01-0ubuntu0.20.04.1 amd64 [upgradable from: 460.56-0ubuntu0.20.04.1]
nvidia-driver-455/focal-updates 460.73.01-0ubuntu0.20.04.1 amd64 [upgradable from: 460.56-0ubuntu0.20.04.1]
nvidia-driver-460/focal-updates 460.73.01-0ubuntu0.20.04.1 amd64 [upgradable from: 460.56-0ubuntu0.20.04.1]
nvidia-kernel-common-460/focal-updates 460.73.01-0ubuntu0.20.04.1 amd64 [upgradable from: 460.56-0ubuntu0.20.04.1]
nvidia-kernel-source-460/focal-updates 460.73.01-0ubuntu0.20.04.1 amd64 [upgradable from: 460.56-0ubuntu0.20.04.1]
nvidia-utils-460/focal-updates 460.73.01-0ubuntu0.20.04.1 amd64 [upgradable from: 460.56-0ubuntu0.20.04.1]
python3-distupgrade/focal-updates,focal-updates 1:20.04.32 all [upgradable from: 1:20.04.30]
ubuntu-release-upgrader-core/focal-updates,focal-updates 1:20.04.32 all [upgradable from: 1:20.04.30]
ubuntu-release-upgrader-gtk/focal-updates,focal-updates 1:20.04.32 all [upgradable from: 1:20.04.30]
update-notifier-common/focal-updates,focal-updates 3.192.30.6 all [upgradable from: 3.192.30.5]
update-notifier/focal-updates 3.192.30.6 amd64 [upgradable from: 3.192.30.5]
xserver-xorg-video-nvidia-460/focal-updates 460.73.01-0ubuntu0.20.04.1 amd64 [upgradable from: 460.56-0ubuntu0.20.04.1]

```

I believe that all is well here unless there is something I'm missing.  (I did run the previous grep commands everything looks to be in order now.) 

If you want to see something else let me know otherwise I can mark this one as solved.

---

