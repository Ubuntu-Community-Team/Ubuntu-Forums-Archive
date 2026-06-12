---
title: "Ubuntu 15.10 nVidia Driver Problem"
date: 2015-10-06
forum: General Help
---

### Post by gfb-gokberk on 2015-10-06
Hello, I installed Ubuntu 15.10 beta 2. When I try to install additional nVidia drivers [[[COLOR=#333333][FONT=Ubuntu]version 355.11 from nvidia-355 (open source) and [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]-version 352.41 from nvidia-352 (proprietary)]], after reboot, i see only black screen. The only thing that i can do, return to [/FONT][/COLOR]nouveau drivers. 

What is the correct configuration?

I have two graphic cards. [COLOR=#333333][FONT=Ubuntu]Intel HD4600 and GeForce 840M

[/FONT][/COLOR]```
[COLOR=#333333][FONT=Ubuntu Mono]lspci | egrep "VGA|3D|Display"[/FONT][/COLOR]
```

```
[COLOR=#333333][FONT=Ubuntu Mono]00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]01:00.0 3D controller: NVIDIA Corporation GM108M [GeForce 840M] (rev a2)[/FONT][/COLOR]
```

[COLOR=#333333][FONT=Ubuntu]Also i installed [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]Bumblebee and when i do this for example;

[/FONT][/COLOR]```
[COLOR=#333333][FONT=Ubuntu Mono]optirun google-chrome[/FONT][/COLOR]
```

i get this:

```
[COLOR=#333333][FONT=Ubuntu Mono][ 2105.171956] [ERROR]Cannot access secondary GPU - error: Could not load GPU driver[/FONT][/COLOR]

[COLOR=#333333][FONT=Ubuntu Mono][ 2105.172126] [ERROR]Aborting because fallback start is disabled.[/FONT][/COLOR]
```



```
[COLOR=#333333][FONT=Ubuntu Mono]dpkg -l | egrep "nvidia|bumblebee|prime"[/FONT][/COLOR]
```

```
[COLOR=#333333][FONT=Ubuntu Mono]ii  bumblebee                                     3.2.1-9                                    amd64        NVIDIA Optimus support for Linux[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]ii  bumblebee-nvidia                              3.2.1-9                                    amd64        NVIDIA Optimus support using the proprietary NVIDIA driver[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]ii  nvidia-304                                    304.128-0ubuntu1                           amd64        NVIDIA legacy binary driver - version 304.128[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]ii  nvidia-current                                304.128-0ubuntu1                           amd64        Transitional package for nvidia-current[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]ii  nvidia-opencl-icd-304                         304.128-0ubuntu1                           amd64        NVIDIA OpenCL ICD[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]ii  nvidia-settings                               355.11-0ubuntu0~gpu15.10.1                 amd64        Tool for configuring the NVIDIA graphics driver[/FONT][/COLOR]
```

```
[COLOR=#333333][FONT=Ubuntu Mono]cat /etc/bumblebee/bumblebee.conf[/FONT][/COLOR]
```

```
[COLOR=#333333][FONT=Ubuntu Mono]# Configuration file for Bumblebee. Values should **not** be put between quotes[/FONT][/COLOR]

[COLOR=#333333][FONT=Ubuntu Mono]## Server options. Any change made in this section will need a server restart[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]# to take effect.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono][bumblebeed][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]# The secondary Xorg server DISPLAY number[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]VirtualDisplay=:8[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]# Should the unused Xorg server be kept running? Set this to true if waiting[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]# for X to be ready is too long and don't need power management at all.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]KeepUnusedXServer=false[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]# The name of the Bumbleblee server group name (GID name)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]ServerGroup=bumblebee[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]# Card power state at exit. Set to false if the card shoud be ON when Bumblebee[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]# server exits.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]TurnCardOffAtExit=false[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]# The default behavior of '-f' option on optirun. If set to "true", '-f' will[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]# be ignored.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]NoEcoModeOverride=false[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]# The Driver used by Bumblebee server. If this value is not set (or empty),[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]# auto-detection is performed. The available drivers are nvidia and nouveau[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]# (See also the driver-specific sections below)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]Driver=[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]# Directory with a dummy config file to pass as a -configdir to secondary X[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]XorgConfDir=/etc/bumblebee/xorg.conf.d[/FONT][/COLOR]

[COLOR=#333333][FONT=Ubuntu Mono]## Client options. Will take effect on the next optirun executed.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono][optirun][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]# Acceleration/ rendering bridge, possible values are auto, virtualgl and[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]# primus.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]Bridge=auto[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]# The method used for VirtualGL to transport frames between X servers.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]# Possible values are proxy, jpeg, rgb, xv and yuv.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]VGLTransport=proxy[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]# List of paths which are searched for the primus libGL.so.1 when using[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]# the primus bridge[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]PrimusLibraryPath=/usr/lib/x86_64-linux-gnu/primus:/usr/lib/i386-linux-gnu/primus[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]# Should the program run under optirun even if Bumblebee server or nvidia card[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]# is not available?[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]AllowFallbackToIGC=false[/FONT][/COLOR]


[COLOR=#333333][FONT=Ubuntu Mono]# Driver-specific settings are grouped under [driver-NAME]. The sections are[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]# parsed if the Driver setting in [bumblebeed] is set to NAME (or if auto-[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]# detection resolves to NAME).[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]# PMMethod: method to use for saving power by disabling the nvidia card, valid[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]# values are: auto - automatically detect which PM method to use[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]#         bbswitch - new in BB 3, recommended if available[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]#       switcheroo - vga_switcheroo method, use at your own risk[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]#             none - disable PM completely[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]# https://github.com/Bumblebee-Project/Bumblebee/wiki/Comparison-of-PM-methods[/FONT][/COLOR]

[COLOR=#333333][FONT=Ubuntu Mono]## Section with nvidia driver specific options, only parsed if Driver=nvidia[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono][driver-nvidia][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]# Module name to load, defaults to Driver if empty or unset[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]KernelDriver=nvidia-current[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]PMMethod=auto[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]# colon-separated path to the nvidia libraries[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]LibraryPath=/usr/lib/nvidia-current:/usr/lib32/nvidia-current[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]# comma-separated path of the directory containing nvidia_drv.so and the[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]# default Xorg modules path[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]XorgModulePath=/usr/lib/nvidia-current/xorg,/usr/lib/xorg/modules[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]XorgConfFile=/etc/bumblebee/xorg.conf.nvidia[/FONT][/COLOR]

[COLOR=#333333][FONT=Ubuntu Mono]## Section with nouveau driver specific options, only parsed if Driver=nouveau[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono][driver-nouveau][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]KernelDriver=nouveau[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]PMMethod=auto[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]XorgConfFile=/etc/bumblebee/xorg.conf.nouveau[/FONT][/COLOR]
```

Thanks. Sory for my English.

[[img]http://i.hizliresim.com/m5rl12.png[/img]](http://hizliresim.com/m5rl12)

[[img]http://i.hizliresim.com/Epzl5D.png[/img]](http://hizliresim.com/Epzl5D)

---

### Post by ventrical on 2015-10-06
Are you trying to use the dual screen option? because I think that there were problems with this and may be dealt with during next development cycle. Otherwise it should jockey with nouveau  but not nvidia.

regards..

---

### Post by dino99 on 2015-10-06
why opting for "do not use the device" ? you might accept the line above (microcode)
open-source is "nouveau", not a nvidia driver

the intel graphic needs xserver-xorg-video-intel driver to be able to work
[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

---

### Post by cariboo on 2015-10-06
There shouldn't be a problem with dual screens, as I can use both monitors with nouveau and the Nvidia proprietary drivers. I'm running a 32" Samsung TV and a Benq 22" with zero problems. I'm running the Nvidia 340.93 version from the repositories.

---

### Post by buzzingrobot on 2015-10-06
If you want to use only the Intel or only the Nvidia and can disable one or the other in BIOS, then Bumblebee is not needed. The appropriate Intel driver will be used automatically if Intel video is detected as active.  Tthe Nouveau driver will be used if the Nvidia is active.  You can then, in that instance, if you wish, use Additional Drivers to install a proprietary driver from Nvidia.

---

### Post by ventrical on 2015-10-06
> **cariboo said:**
> There shouldn't be a problem with dual screens, as I can use both monitors with nouveau and the Nvidia proprietary drivers. I'm running a 32" Samsung TV and a Benq 22" with zero problems. I'm running the Nvidia 340.93 version from the repositories.

But are they two different chipsets? ie: 1 Intel 1 nvidia ?

regards..

---

### Post by mc4man on 2015-10-07
A quick test here on an optimus device shows bumblebee is broken, same errors (never liked or used bumblebee any way.

nvidia-prime can work well though you'll likely black screen at either any lightdm greeter or on session login. 
If that is the case there is  no forthcoming fix but quite easy to work-around in several ways. If you need a workaround then post in this thread, mention whether you login to the greeter screen or auto login to the session.
[http://ubuntuforums.org/showthread.php?t=2293682](http://ubuntuforums.org/showthread.php?t=2293682)

(- I've opted for auto-login & a startup script, that way no black screen & no blind login

As far as nvidia drivers - 304 can't be used with nvidia-prime, 352 is a terrible driver, best option is 355 from the ppa

---

### Post by emil15 on 2015-10-19
Hi.

I installed xubuntu 15.10, on my asus with 650m optimus. Got the login screen, and then a black screen after login. My solution:

After getting the black screen I hit:

   CTRL+ALT+F1, then logged in.

then:

   sudo nano /etc/X11/xorg.conf

In the first section I changed:

```
Section "ServerLayout"
    Identifier "layout"
    Screen 0 "nvidia"
    Inactive "intel"
EndSection


```

to:
```
Section "ServerLayout"
    Identifier "layout"
    Screen 0 "intel"
    Inactive "nvidia"
EndSection


```

Switching the target of "Screen 0" and "Inactive", is the important part here.

After a reboot, I logged in just fine. But when I went to the nvidia-settings, nvidia was set to active, but after setting intel be active, everything behaved just as expected.

Hope it does you some good. 

Cheers.

---

### Post by amias2 on 2015-11-06
if you are using optimus you don't load the nvidia drivers , everything is setup to use the intel ones and the nvidia driver (in my case nvidia_346_updates to run my GeForce GT 750M) just gets enabled automagically when applications do 3d stuff. You need to install nvidia-prime for this to work. 
This breaks some apps that check for nvidia drivers using the filesystem instead of the api

---

### Post by cariboo on 2015-11-06
Moved, as it has nothing to do with Xenial.

---

