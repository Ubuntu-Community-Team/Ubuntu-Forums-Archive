---
title: "Need help with video card drivers"
date: 2019-04-16
forum: General Help
---

### Post by andreadixon825 on 2019-04-16
Hi, I was installing my video card, everytime I pick a driver it installs but then I have to go to recover mode, when I try to run startx I get a messages sayintg that something went wrong and could not load. so I have to uninstall the drivers and then trying agine. But get the same issue.
I'm using Ubuntu 18.10 64bit my video card is a GT 740. If anyone can help me please thanks

---

### Post by SeijiSensei on 2019-04-16
Did you use the Driver Manager in System Settings to configure the driver?  Where did you "pick" your driver?  The Manager is usually foolproof.

---

### Post by andreadixon825 on 2019-04-16
Hi yes I did use the driver manager, and sitll cant go to desktop

---

### Post by #&amp;thj^% on 2019-04-16
Can you tell us the return of:
```
echo $XDG_SESSION_TYPE
```

---

### Post by andreadixon825 on 2019-04-16
It says x11, but I did not try agine should I go and istall it agin and then tell you what it says

---

### Post by #&amp;thj^% on 2019-04-16
> **andreadixon825 said:**
> It says x11, but I did not try agine should I go and istall it agin and then tell you what it says
Is a PPA used here for the source? 
Like: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

---

### Post by Bashing-om on 2019-04-16
andreadixon825 Hello -

Moreso - be good to know what the hardware is:
```

sudo lshw -C display

```

And also what driver(s) is installed:
```

dpkg -l | grep -i nvidia

```

[INDENT][INDENT]look before the leap
[/INDENT][/INDENT]

---

### Post by andreadixon825 on 2019-04-16
Hi I have done it but still gives me a message that says cant start x

---

### Post by andreadixon825 on 2019-04-16
```
andrew@andrew825pc:~$ dpkg -l | grep -i nvidia
ii  libnvidia-cfg1-410:amd64                                         410.104-0ubuntu0~18.10.1                      amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-410                                             410.104-0ubuntu0~18.10.1                      all          Shared files used by the NVIDIA libraries
rc  libnvidia-compute-390:amd64                                      390.116-0ubuntu0.18.10.1                      amd64        NVIDIA libcompute package
rc  libnvidia-compute-390:i386                                       390.116-0ubuntu0.18.10.1                      i386         NVIDIA libcompute package
rc  libnvidia-compute-396:amd64                                      396.54-0ubuntu0~gpu18.10.1                    amd64        NVIDIA libcompute package
rc  libnvidia-compute-396:i386                                       396.54-0ubuntu0~gpu18.10.1                    i386         NVIDIA libcompute package
ii  libnvidia-compute-410:amd64                                      410.104-0ubuntu0~18.10.1                      amd64        NVIDIA libcompute package
ii  libnvidia-compute-410:i386                                       410.104-0ubuntu0~18.10.1                      i386         NVIDIA libcompute package
rc  libnvidia-compute-418:amd64                                      418.56-0ubuntu0~gpu18.10.1                    amd64        NVIDIA libcompute package
ii  libnvidia-decode-410:amd64                                       410.104-0ubuntu0~18.10.1                      amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-410:i386                                        410.104-0ubuntu0~18.10.1                      i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-410:amd64                                       410.104-0ubuntu0~18.10.1                      amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-410:i386                                        410.104-0ubuntu0~18.10.1                      i386         NVENC Video Encoding runtime library
ii  libnvidia-fbc1-410:amd64                                         410.104-0ubuntu0~18.10.1                      amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-410:i386                                          410.104-0ubuntu0~18.10.1                      i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-410:amd64                                           410.104-0ubuntu0~18.10.1                      amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-410:i386                                            410.104-0ubuntu0~18.10.1                      i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-410:amd64                                         410.104-0ubuntu0~18.10.1                      amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  libnvidia-ifr1-410:i386                                          410.104-0ubuntu0~18.10.1                      i386         NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  xserver-xorg-video-nvidia-410                                    410.104-0ubuntu0~18.10.1                      amd64        NVIDIA binary Xorg driver
andrew@andrew825pc:~$
```

```
andrew@andrew825pc:~$ sudo lshw -C display
  *-display                 
       description: VGA compatible controller
       product: GK107 [GeForce GT 740]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:37 memory:f5000000-f5ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:c0000-dffff
```

---

### Post by Bashing-om on 2019-04-16
andreadixon825; Well !

That reeks as the nvidia driver is installed, but the nouveau driver is loaded.

Post back - Between code tags ! -
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
the output of:
```

cat /var/log/gpu-manager.log

```

As a start to find out where the failure may lie.

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by andreadixon825 on 2019-04-16
andrew@andrew825pc:~$ cat /var/log/gpu-manager.log
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/4.18.0-17-generic/updates/dkms
Looking for amdgpu modules in /lib/modules/4.18.0-17-generic/updates/dkms
Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is intel loaded? no
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is amdgpu versioned? no
Is amdgpu pro stack? no
Is nouveau loaded? yes
Is nouveau blacklisted? no
Is nvidia kernel module available? no
Is amdgpu kernel module available? no
Vendor/Device Id: 10de:fc8
BusID "PCI:1@0:0:0"
Is boot vga? yes
Vendor/Device Id: 10de:dd8
BusID "PCI:2@0:0:0"
Is boot vga? no
Skipping "/dev/dri/card1", driven by "nouveau"
Skipping "/dev/dri/card0", driven by "nouveau"
Skipping "/dev/dri/card1", driven by "nouveau"
Skipping "/dev/dri/card0", driven by "nouveau"
Found "/dev/dri/card1", driven by "nouveau"
Number of connected outputs for /dev/dri/card1: 0
Skipping "/dev/dri/card1", driven by "nouveau"
Skipping "/dev/dri/card0", driven by "nouveau"
Does it require offloading? no
last cards number = 2
Has amd? no
Has intel? no
Has nvidia? yes
How many cards? 2
Has the system changed? No
Unsupported discrete card vendor: 10de
Nothing to do
andrew@andrew825pc:~$

---

### Post by Bashing-om on 2019-04-16
andreadixon825 - code tags ! please

Any idea how many lines we look at ? And how much easier the code tags make this ?

OK, what is driving the kernel nuts ?
as we have:
> 
Is nvidia kernel module available? no
How many cards? 2

We need to see what those 2 cards are. post back BCT! :
```

lspci -k | grep -EA2 'VGA|3D'

```

[INDENT][INDENT]the game is afoot
[/INDENT][/INDENT]

---

### Post by andreadixon825 on 2019-04-16
```
andrew@andrew825pc:~$ lspci -k | grep -EA2 'VGA|3D'
01:00.0 VGA compatible controller: NVIDIA Corporation GK107 [GeForce GT 740] (rev a1)
    Subsystem: Gigabyte Technology Co., Ltd GK107 [GeForce GT 740]
    Kernel driver in use: nouveau
--
02:00.0 VGA compatible controller: NVIDIA Corporation GF106GL [Quadro 2000] (rev a1)
    Subsystem: NVIDIA Corporation Quadro 2000D
    Kernel driver in use: nouveau
```

Thanks for helping me

---

### Post by Bashing-om on 2019-04-16
andreadixon825; Yukkie on me -

Yup - driving the kernel nuts as to what card to use and what driver,

quadro 200 card:
[https://www.nvidia.com/Download/driverResults.aspx/134859/en-us](https://www.nvidia.com/Download/driverResults.aspx/134859/en-us)
takes the 390.67 version driver.

while the GeForce GT 740:
[https://www.nvidia.com/Download/driverResults.aspx/145182/en-us](https://www.nvidia.com/Download/driverResults.aspx/145182/en-us)
takes the 418.56 version driver.

Now my experience ends here. I do not know how to make the kernel support 2 nvidia cards.
Maybe disable one of the cards in Bios ? and get the system booting.

Other's skills here too will be much appreciated.

[INDENT][INDENT]a know-it-all I am not
[/INDENT][/INDENT]

---

