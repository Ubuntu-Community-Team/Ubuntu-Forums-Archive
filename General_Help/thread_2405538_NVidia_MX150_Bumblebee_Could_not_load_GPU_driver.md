---
title: "NVidia MX150 Bumblebee Could not load GPU driver"
date: 2018-11-07
forum: General Help
---

### Post by Visseroth on 2018-11-07
I've been struggling for many hours trying to get bumblebee to work on my Asus ZenBook laptop. I keep getting the error that "error: Could not load GPU driver", "[ERROR]Aborting because fallback start is disabled."

I've gone through these sites trying to figure out how to get things going, maybe someone smarter than myself will see something I'm missing...
[https://wiki.archlinux.org/index.php/bumblebee](https://wiki.archlinux.org/index.php/bumblebee)
[https://github.com/Bumblebee-Project/Bumblebee/issues/822](https://github.com/Bumblebee-Project/Bumblebee/issues/822)
[https://www.pcsuggest.com/nvidia-optimus-ubuntu/](https://www.pcsuggest.com/nvidia-optimus-ubuntu/)
[https://forums.linuxmint.com/viewtopic.php?t=225156](https://forums.linuxmint.com/viewtopic.php?t=225156)
[https://forum.linuxmint.net.tr/index.php?topic=6258.0#post_yapilandirma](https://forum.linuxmint.net.tr/index.php?topic=6258.0#post_yapilandirma) (Translated)

Here is my system information...

inxi -Fxz
```
System:    Host: LMZB Kernel: 4.15.0-38-generic x86_64 (64 bit gcc: 5.4.0)           Desktop: Cinnamon 3.6.7 (Gtk 3.18.9-1ubuntu3.3) Distro: Linux Mint 18.3 Sylvia
Machine:   System: ASUSTeK (portable) product: UX430UNR v: 1.0
           Mobo: ASUSTeK model: UX430UNR v: 1.0 Bios: American Megatrends v: UX430UNR.305 date: 03/19/2018
CPU:       Quad core Intel Core i7-8550U (-HT-MCP-) cache: 8192 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 15936
           clock speeds: max: 2001 MHz 1: 1799 MHz 2: 1795 MHz 3: 1798 MHz 4: 1799 MHz 5: 1799 MHz 6: 1797 MHz
           7: 1792 MHz 8: 1795 MHz
Graphics:  Card-1: Intel Device 5917 bus-ID: 00:02.0
           Card-2: NVIDIA Device 1d10 bus-ID: 01:00.0
           Display Server: X.org 1.18.4 drivers: (unloaded: fbdev,vesa)
           tty size: 117x30 Advanced Data: N/A for root
Audio:     Card Intel Device 9d71 driver: snd_hda_intel bus-ID: 00:1f.3 Sound: ALSA v: k4.15.0-38-generic
Network:   Card: Intel Device 24fd driver: iwlwifi bus-ID: 02:00.0
           IF: wlp2s0 state: down mac: <filter>
Drives:    HDD Total Size: 512.1GB (8.7% used) ID-1: /dev/sda model: SanDisk_SD8SN8U5 size: 512.1GB temp: 42C
Partition: ID-1: / size: 205G used: 27G (14%) fs: ext4 dev: /dev/sda5
           ID-2: swap-1 size: 17.03GB used: 0.00GB (0%) fs: swap dev: /dev/dm-0
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 54.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 269 Uptime: 21 min Memory: 1594.2/15900.9MB Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (sudo) inxi: 2.2.35 
```

optirun -vvv glxgears
```
[ 1794.204259] [DEBUG]Reading file: /etc/bumblebee/bumblebee.conf
[ 1794.204456] [INFO]Configured driver: nvidia
[ 1794.204621] [DEBUG]optirun version 3.2.1 starting...
[ 1794.204633] [DEBUG]Active configuration:
[ 1794.204636] [DEBUG] bumblebeed config file: /etc/bumblebee/bumblebee.conf
[ 1794.204640] [DEBUG] X display: :8
[ 1794.204644] [DEBUG] LD_LIBRARY_PATH: /usr/lib/x86_64-linux-gnu:/usr/lib/i386-linux-gnu
[ 1794.204650] [DEBUG] Socket path: /var/run/bumblebee.socket
[ 1794.204657] [DEBUG] Accel/display bridge: auto
[ 1794.204666] [DEBUG] VGL Compression: proxy
[ 1794.204673] [DEBUG] VGLrun extra options: 
[ 1794.204680] [DEBUG] Primus LD Path: /usr/lib/x86_64-linux-gnu/primus:/usr/lib/i386-linux-gnu/primus
[ 1794.204761] [DEBUG]Using auto-detected bridge primus
[ 1794.218067] [INFO]Response: No - error: Could not load GPU driver


[ 1794.218100] [ERROR]Cannot access secondary GPU - error: Could not load GPU driver


[ 1794.218104] [DEBUG]Socket closed.
[ 1794.218124] [ERROR]Aborting because fallback start is disabled.
[ 1794.218142] [DEBUG]Killing all remaining processes.
```


cat /etc/bumblebee/bumblebee.conf
```
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
Driver=nvidia
# Directory with a dummy config file to pass as a -configdir to secondary X
XorgConfDir=/etc/bumblebee/xorg.conf.d
# Xorg binary to run
XorgBinary=/usr/lib/xorg/Xorg


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
KernelDriver=nvidia-410
PMMethod=auto
# colon-separated path to the nvidia libraries
LibraryPath=/usr/lib/x86_64-linux-gnu:/usr/lib/i386-linux-gnu
# LibraryPath=/usr/lib/nvidia-410:/usr/lib32/nvidia-410
# comma-separated path of the directory containing nvidia_drv.so and the
# default Xorg modules path
XorgModulePath=/usr/lib/nvidia-410/xorg,/usr/lib/xorg/modules,/usr/lib/xorg/modules/input
XorgConfFile=/etc/bumblebee/xorg.conf.nvidia


## Section with nouveau driver specific options, only parsed if Driver=nouveau
[driver-nouveau]
KernelDriver=nouveau
PMMethod=auto
XorgConfFile=/etc/bumblebee/xorg.conf.nouvea
```

cat /etc/bumblebee/xorg.conf.nvidia
```
Section "ServerLayout"    Identifier  "Layout0"
    Option      "AutoAddDevices" "true"
    Option      "AutoAddGPU" "true"
EndSection


Section "Device"
    Identifier  "DiscreteNvidia"
    Driver      "nvidia"
    VendorName  "NVIDIA Corporation"
    BusID "PCI:01:00:0"
    Option "ProbeAllGpus" "true"


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


cat /etc/modprobe.d/bumblebee.conf
```
# This file is installed by bumblebee, do NOT edit!# to be used by kmod / module-init-tools, and installed in /etc/modprobe.d/
# or equivalent


# do not automatically load nouveau as it may prevent nvidia from loading
blacklist nouveau
# do not automatically load nvidia as it's unloaded anyway when bumblebeed
# starts and may fail bumblebeed to disable the card in a race condition.
# Debian
blacklist nvidia
blacklist nvidia-current
blacklist nvidia-legacy-304xx
blacklist nvidia-legacy-340xx
# Ubuntu
blacklist nvidia
blacklist nvidia-current
blacklist nvidia-current-updates
# 304
blacklist nvidia-304
blacklist nvidia-304-updates
blacklist nvidia-experimental-304
# 310
blacklist nvidia-310
blacklist nvidia-310-updates
blacklist nvidia-experimental-310
# 313
blacklist nvidia-313
blacklist nvidia-313-updates
blacklist nvidia-experimental-313
# 319
blacklist nvidia-319
blacklist nvidia-319-updates
blacklist nvidia-experimental-319
# 325
blacklist nvidia-325
blacklist nvidia-325-updates
blacklist nvidia-experimental-325
# 331
blacklist nvidia-331
blacklist nvidia-331-updates
blacklist nvidia-experimental-331
# 334
blacklist nvidia-334
blacklist nvidia-334-updates
blacklist nvidia-experimental-334
# 337
blacklist nvidia-337
blacklist nvidia-337-updates
blacklist nvidia-experimental-337
# 340
blacklist nvidia-340
blacklist nvidia-340-updates
blacklist nvidia-experimental-340
# 343
blacklist nvidia-343
blacklist nvidia-343-updates
blacklist nvidia-experimental-343
# 346
blacklist nvidia-346
blacklist nvidia-346-updates
blacklist nvidia-experimental-346
# 349
blacklist nvidia-349
blacklist nvidia-349-updates
blacklist nvidia-experimental-349
# 352
blacklist nvidia-352
blacklist nvidia-352-updates
blacklist nvidia-experimental-352
# 355
blacklist nvidia-355
blacklist nvidia-355-updates
blacklist nvidia-experimental-355
# 358
blacklist nvidia-358
blacklist nvidia-358-updates
blacklist nvidia-experimental-358
# 361
blacklist nvidia-361
blacklist nvidia-361-updates
blacklist nvidia-experimental-361
# 364
blacklist nvidia-364
blacklist nvidia-364-updates
blacklist nvidia-experimental-364
# 367
blacklist nvidia-367
blacklist nvidia-367-updates
blacklist nvidia-experimental-367
# 375
blacklist nvidia-375
blacklist nvidia-375-updates
blacklist nvidia-experimental-375
# 378
blacklist nvidia-378
blacklist nvidia-378-updates
blacklist nvidia-experimental-378
# 381
blacklist nvidia-381
blacklist nvidia-381-updates
blacklist nvidia-experimental-381
# 384
blacklist nvidia-384
blacklist nvidia-384-updates
blacklist nvidia-experimental-384
# 370
blacklist nvidia-370
blacklist nvidia-370-updates
blacklist nvidia-experimental-370
# 390
blacklist nvidia-390
blacklist nvidia-390-updates
blacklist nvidia-experimental-390
# 396
blacklist nvidia-396
blacklist nvidia-396-updates
```

cat: /etc/X11/xorg.conf: No such file or directory



dpkg -l | egrep 'nvidia|bumblebee|primus|prime|virtualgl
```
ii  bumblebee                                   3.2.1-101~xenialppa1                         amd64        NVIDIA Optimus support for Linuxrc  nvidia-390                                  390.87-0ubuntu0~gpu16.04.1                   amd64        NVIDIA binary driver - version 390.87
rc  nvidia-396                                  396.54-0ubuntu0~gpu16.04.1                   amd64        NVIDIA binary driver - version 396.54
ii  nvidia-410                                  410.73-0ubuntu0~gpu16.04.1                   amd64        NVIDIA binary driver - version 410.73
rc  nvidia-opencl-icd-390                       390.87-0ubuntu0~gpu16.04.1                   amd64        NVIDIA OpenCL ICD
rc  nvidia-opencl-icd-396                       396.54-0ubuntu0~gpu16.04.1                   amd64        NVIDIA OpenCL ICD
ii  nvidia-opencl-icd-410                       410.73-0ubuntu0~gpu16.04.1                   amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                0.8.2linuxmint1                              amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                             410.73-0ubuntu0~gpu16.04.1                   amd64        Tool for configuring the NVIDIA graphics driver
ii  primus                                      20150328-3~xenialppa2                        amd64        client-side GPU offloading for NVIDIA Optimus
ii  primus-libs:amd64                           20150328-3~xenialppa2                        amd64        Shared libraries for primus
ii  primus-libs:i386                            20150328-3~xenialppa2                        i386         Shared libraries for primus
ii  primus-libs-ia32:i386                       20150328-3~xenialppa2                        i386         Shared libraries for primus (32-bit)
```


lspci | egrep 'VGA|3D|Display'
```
00:02.0 VGA compatible controller: Intel Corporation Device 5917 (rev 07)
01:00.0 3D controller: NVIDIA Corporation Device 1d10 (rev a1)
```


cat /proc/cmdline
```
BOOT_IMAGE=/boot/vmlinuz-4.15.0-38-generic root=UUID=c9482c8c-775c-4d0f-a62d-480d7875913a ro iommu=soft nogpumanager elevator=deadline quiet splash nouveau.modeset=0 nvidia.modeset=0 nogpumanager acpi=force acpi_enforce_resources=lax intel_pstate=disable processor.ignore_ppc=1 vt.handoff=7
```


```
cat /proc/acpi/
button/ wakeup
```

---

### Post by 23dornot23d on 2018-11-08
I usually change this line to true ..........
AllowFallbackToIGC=true

in /etc/bumblebee/bumblebee.conf

> 
# the primus bridge
PrimusLibraryPath=/usr/lib/x86_64-linux-gnu/primus:/usr/lib/i386-linux-gnu/primus
# Should the program run under optirun even if Bumblebee server or nvidia card
# is not available?
AllowFallbackToIGC=false


What difference it makes .....

Allows programs to run ........ some I have found find and can use my Nvidia Card ......... 

Why it does is another question and maybe someone else could answer that .... ?

The IGC probably stands for Integrated Graphics Card ............ so on systems that have that setup - I would have thought it should
automatically be set ......... to true ............ but why it is not is another question also. ?

Here is my own output from running the optimus command ... you will see the gt540 nvidia card is shown as being used.

> 
optirun glxspheres
[ 2489.065985] [ERROR]Cannot access secondary GPU, secondary X is not active.

[ 2489.066099] [WARN]The Bumblebee server was not available.
Polygons in scene: 62464 (61 spheres * 1024 polys/spheres)
Visual ID of window: 0x8f
Context is Direct
OpenGL Renderer: GeForce GT 540M/PCIe/SSE2
641.826576 frames/sec - 586.552471 Mpixels/sec
638.933170 frames/sec - 583.908245 Mpixels/sec

Video showing it as the frames per second do not mean a great deal to most people.
[https://youtu.be/ZIJ5Xj2yTXc](https://youtu.be/ZIJ5Xj2yTXc)

and a video showing the same glxspheres when its not using the Nvidia gt540 card in my own machine for comparison.
[https://youtu.be/AY3TmlxR_R8](https://youtu.be/AY3TmlxR_R8)




---

### Post by Visseroth on 2018-11-23
Thanks for the response. I would have replied sooner but I didn't receive a email notification of a reply, plus I've been busy. I'm just now sitting down to mess with this issue again.
Anyhow, I made the changes you suggested and no difference. I still can't seem to get bumblebeed to start. system logs show...

> Nov 22 22:58:35 LMZB bumblebeed[10736]: [ 1635.892824] [ERROR]Module 'bbswitch' not found.Nov 22 22:58:35 LMZB bumblebeed[10736]: [ 1635.892874] [WARN]No switching method available. The dedicated card will always be on.
Nov 22 22:58:35 LMZB bumblebeed[10736]: [ 1635.892998] [ERROR]Module 'nvidia' is not found.
Nov 22 22:58:35 LMZB systemd[1]: bumblebeed.service: Main process exited, code=exited, status=1/FAILURE
Nov 22 22:58:35 LMZB systemd[1]: bumblebeed.service: Unit entered failed state.
Nov 22 22:58:35 LMZB systemd[1]: bumblebeed.service: Failed with result 'exit-code'.

---

