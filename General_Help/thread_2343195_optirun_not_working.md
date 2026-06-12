---
title: "optirun not working"
date: 2016-11-14
forum: General Help
---

### Post by aircrack on 2016-11-14
Hi,

i have a msi gp60 2qf with a nvidia gtx 950m and an intel graphics chip.
```
~$ lspci -nnk | grep "VGA\|'Kern'\|3D\|Display" -A2 
00:02.0 VGA compatible controller [0300]: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller [8086:0416] (rev 06)
    DeviceName:  Onboard IGD
    Subsystem: Micro-Star International Co., Ltd. [MSI] 4th Gen Core Processor Integrated Graphics Controller [1462:1113]
--
01:00.0 3D controller [0302]: NVIDIA Corporation GM107M [GeForce GTX 950M] [10de:139a] (rev a2)
    Subsystem: Micro-Star International Co., Ltd. [MSI] GM107M [GeForce GTX 950M] [1462:1113]
    Kernel modules: nvidiafb, nouveau, nvidia_304

```

```

$ cat /etc/bumblebee/xorg.conf.nvidia 
Section "ServerLayout"
    Identifier  "Layout0"
    Option      "AutoAddDevices" "false"
    Option      "AutoAddGPU" "false"
EndSection

Section "Device"
    Identifier  "DiscreteNvidia"
    Driver      "nvidia"
    VendorName  "NVIDIA Corporation"

#   If the X server does not automatically detect your VGA device,
#   you can manually set it here.
#   To get the BusID prop, run `lspci | egrep 'VGA|3D'` and input the data
#   as you see in the commented example.
#   This Setting may be needed in some platforms with more than one
#   nvidia card, which may confuse the proprietary driver (e.g.,
#   trying to take ownership of the wrong device). Also needed on Ubuntu 13.04.
    BusID "PCI:01:00:0"

#   Setting ProbeAllGpus to false prevents the new proprietary driver
#   instance spawned to try to control the integrated graphics card,
#   which is already being managed outside bumblebee.
#   This option doesn't hurt and it is required on platforms running
#   more than one nvidia graphics card with the proprietary driver.
#   (E.g. Macbook Pro pre-2010 with nVidia 9400M + 9600M GT).
#   If this option is not set, the new Xorg may blacken the screen and
#   render it unusable (unless you have some way to run killall Xorg).
    Option "ProbeAllGpus" "false"

    Option "NoLogo" "true"
    Option "UseEDID" "false"
    Option "UseDisplayDevice" "none"
EndSection



```

I am trying to use optirun to start glxgears, but it does not work. 
The output i am getting is:
```
~$ optirun -vvv glxgears
[  101.476159] [DEBUG]Reading file: /etc/bumblebee/bumblebee.conf
[  101.476390] [DEBUG]optirun version 3.2.1 starting...
[  101.476397] [DEBUG]Active configuration:
[  101.476400] [DEBUG] bumblebeed config file: /etc/bumblebee/bumblebee.conf
[  101.476408] [DEBUG] X display: :8
[  101.476412] [DEBUG] LD_LIBRARY_PATH: 
[  101.476416] [DEBUG] Socket path: /var/run/bumblebee.socket
[  101.476420] [DEBUG] Accel/display bridge: auto
[  101.476423] [DEBUG] VGL Compression: proxy
[  101.476426] [DEBUG] VGLrun extra options: 
[  101.476428] [DEBUG] Primus LD Path: /usr/lib/x86_64-linux-gnu/primus:/usr/lib/i386-linux-gnu/primus
[  101.484110] [DEBUG]Using auto-detected bridge primus
[  101.772498] [INFO]Response: No - error: Could not load GPU driver

[  101.772510] [ERROR]Cannot access secondary GPU - error: Could not load GPU driver

[  101.772512] [DEBUG]Socket closed.
[  101.772527] [ERROR]Aborting because fallback start is disabled.
[  101.772530] [DEBUG]Killing all remaining processes.

```

I configured my bumblebee to access the correct directories:
```
~$ cat /etc/bumblebee/bumblebee.conf 
# Configuration file for Bumblebee. Values should **not** be put between quotes

## Server options. Any change made in this section will need a server restart
# to take effect.
[bumblebeed]
# The secondary Xorg server DISPLAY number
VirtualDisplay=:8
# Should the unused Xorg server be kept running? Set this to true if waiting
# for X to be ready is too long and don't need power management at all.
KeepUnusedXServer=false
# The name of the Bumbleblee server group name (GID name)
ServerGroup=bumblebee
# Card power state at exit. Set to false if the card shoud be ON when Bumblebee
# server exits.
TurnCardOffAtExit=false
# The default behavior of '-f' option on optirun. If set to "true", '-f' will
# be ignored.
NoEcoModeOverride=false
# The Driver used by Bumblebee server. If this value is not set (or empty),
# auto-detection is performed. The available drivers are nvidia and nouveau
# (See also the driver-specific sections below)
Driver=
# Directory with a dummy config file to pass as a -configdir to secondary X
XorgConfDir=/etc/bumblebee/xorg.conf.d

## Client options. Will take effect on the next optirun executed.
[optirun]
# Acceleration/ rendering bridge, possible values are auto, virtualgl and
# primus.
Bridge=auto
# The method used for VirtualGL to transport frames between X servers.
# Possible values are proxy, jpeg, rgb, xv and yuv.
VGLTransport=proxy
# List of paths which are searched for the primus libGL.so.1 when using
# the primus bridge
PrimusLibraryPath=/usr/lib/x86_64-linux-gnu/primus:/usr/lib/i386-linux-gnu/primus
# Should the program run under optirun even if Bumblebee server or nvidia card
# is not available?
AllowFallbackToIGC=false


# Driver-specific settings are grouped under [driver-NAME]. The sections are
# parsed if the Driver setting in [bumblebeed] is set to NAME (or if auto-
# detection resolves to NAME).
# PMMethod: method to use for saving power by disabling the nvidia card, valid
# values are: auto - automatically detect which PM method to use
#         bbswitch - new in BB 3, recommended if available
#       switcheroo - vga_switcheroo method, use at your own risk
#             none - disable PM completely
# https://github.com/Bumblebee-Project/Bumblebee/wiki/Comparison-of-PM-methods

## Section with nvidia driver specific options, only parsed if Driver=nvidia
[driver-nvidia]
# Module name to load, defaults to Driver if empty or unset
KernelDriver=nvidia-304
PMMethod=auto
# colon-separated path to the nvidia libraries
LibraryPath=/usr/lib/nvidia-304:/usr/lib32/nvidia-304
# comma-separated path of the directory containing nvidia_drv.so and the
# default Xorg modules path
XorgModulePath=/usr/lib/nvidia-304/xorg,/usr/lib/xorg/modules
XorgConfFile=/etc/bumblebee/xorg.conf.nvidia

## Section with nouveau driver specific options, only parsed if Driver=nouveau
[driver-nouveau]
KernelDriver=nouveau
PMMethod=auto
XorgConfFile=/etc/bumblebee/xorg.conf.nouveau

```

How can i fix this?
Thank you!


Edit: 
The packages i have installed are:
```
~$ dpkg --list | grep nvidia
ii  bumblebee-nvidia                           3.2.1-10                                      amd64        NVIDIA Optimus support using the proprietary NVIDIA driver
ii  nvidia-304                                 304.132-0ubuntu0.16.04.2                      amd64        NVIDIA legacy binary driver - version 304.132
ii  nvidia-current                             304.132-0ubuntu0.16.04.2                      amd64        Transitional package for nvidia-current
ii  nvidia-opencl-icd-304                      304.132-0ubuntu0.16.04.2                      amd64        NVIDIA OpenCL ICD
ii  nvidia-settings                            361.42-0ubuntu1                               amd64        Tool for configuring the NVIDIA graphics driver

```

---

