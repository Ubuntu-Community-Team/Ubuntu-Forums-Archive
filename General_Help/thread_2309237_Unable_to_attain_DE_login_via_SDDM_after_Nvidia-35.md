---
title: "Unable to attain DE login via SDDM after Nvidia-355 install on DellXPS 15"
date: 2016-01-08
forum: General Help
---

### Post by Hodevah on 2016-01-08
This is for Kubuntu 15.10 _Wily Werewolf_ - Alpha amd64

I am not able to login to DE. I am however able to login with my credentials to a basic command terminal. 
Some information about my laptop:
```

dmidecode | grep -A3 '^System Information'
System Information
    Manufacturer: Dell Inc.
    Product Name: XPS 15 9530
    Version: A06

```


Post install of Nvidia 355 I believe I may tried to switch to Nvidia drivers via the Nvidia settings rather via the Drivers through the General Settings. 
Probably should not have done that. 
If you are interested in knowing how and what I did to install nvidia on this Linux Box, I am able to do so with the following output described below after having purged all nvidia and bumbleee related configs, libs, drivers, etc 
(because for some reason, "autoremove" removed the prior install of nvidia-358 and related kernel(s) after recent upgrade to the latest kernel and after informing me that it would remove some of those older kernels, it also removed nvidia-358, leaving me with no nvidia. Nice!!!):



```



sudo apt-get purge -y nvidia* bumblebee bumblebee-nvidia bbswitch-dkms primus
sudo apt-get purge nvidia* '^bumblebee.*'
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update


sudo apt-get install nvidia-355 nvidia-prime  


sudo add-apt-repository ppa:bumblebee/stable
sudo apt-get update
sudo apt-get install bumblebee primus


#sudo gedit /etc/modprobe.d/bumblebee.conf
#and made sure that the following line was existing/input
#  blacklist nvidia-355


#sudo gedit /etc/bumblebee/bumblebee.conf
#  changed line 22 "Driver=" to "Driver=nvidia"
#  changed all nvidia-current to nvidia-355


#sudo gedit /etc/bumblebee/xorg.conf.nvidia
#  uncommented the BusID line if it was commented and made sure it corresponded to the correct BusID. See below output for this information. 


#disabled the gpu-manager as it changed/changes the i386-linux-gnu_gl_conf and x86_64-linux-gnu_gl_conf
sudo systemctl mask gpu-manager.service



```
some related information:


```

02:00.0 3D controller: NVIDIA Corporation GK107M [GeForce GT 750M] (rev a1)
``````
        Subsystem: Dell Device 05fe
        Flags: bus master, fast devsel, latency 0, IRQ 34
        Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Memory at f0000000 (64-bit, prefetchable) [size=32M]
        I/O ports at e000 
        Expansion ROM at f7000000 [disabled] [size=512K]
        Capabilities: <access denied>
        Kernel driver in use: nouveau
        Kernel modules: nouveau





```
and 
```

00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06) (prog-if 00 [VGA controller])
``````
        Subsystem: Dell Device 05fe
        Flags: bus master, fast devsel, latency 0, IRQ 33
        Memory at f7400000 (64-bit, non-prefetchable) [size=4M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at f000 
        Expansion ROM at <unassigned> [disabled]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: i915





```


Some config file information:




```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
i915
bbswitch

```


```

cat /etc/bumblebee/bumblebee.conf
``````

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
KernelDriver=nvidia-355
PMMethod=auto
# colon-separated path to the nvidia libraries
LibraryPath=/usr/lib/nvidia-355:/usr/lib32/nvidia-355
# comma-separated path of the directory containing nvidia_drv.so and the
# default Xorg modules path
XorgModulePath=/usr/lib/nvidia-355/xorg,/usr/lib/xorg/modules
XorgConfFile=/etc/bumblebee/xorg.conf.nvidia




## Section with nouveau driver specific options, only parsed if Driver=nouveau
[driver-nouveau]
KernelDriver=nouveau
PMMethod=auto
XorgConfFile=/etc/bumblebee/xorg.conf.nouveau

```


I have no idea why I am getting two (2) different Xorg.conf files. One is the regular "Xorg.conf" and the second one is "xorg.conf.01082016"


Both have identical information output below:


```

cat /etc/X11/xorg.conf


Section "ServerLayout"
    Identifier "layout"
    Screen 0 "nvidia"
    Inactive "intel"
EndSection




Section "Device"
    Identifier "intel"
    Driver "modesetting"
    BusID "PCI:0@0:2:0"
    Option "AccelMethod" "None"
EndSection




Section "Screen"
    Identifier "intel"
    Device "intel"
EndSection

```


When I tried 
```

startx

```
in the basic terminal to see what if any output and perhaps navigate back to a GUI/Desktop Environment, I got this output:


```

X.Org X Server 1.17.2
Release Date: 2015-06-16
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.13.0-68-generic x86_64 Ubuntu
Current Operating System: Linux DellXPS-15-9530 4.2.0-23-generic #28-Ubuntu SMP Sun Dec 27 17:47:31 UTC 2015 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-23-generic root=UUID=f211db28-021e-4475-baa2-db2d92d862dc ro quiet splash
Build Date: 12 November 2015  05:33:29PM
xorg-server 2:1.17.2-1ubuntu9.1 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.32.6
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jan  7 23:09:43 2016
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
Data incomplete in file /etc/X11/xorg.conf
    Undefined Screen "nvidia" referenced by ServerLayout "layout".
(EE) 
Fatal server error:
(EE) no screens found(EE) 
(EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
(EE)** Please also check the log file at "/var/log/Xorg.0.log" for additional information.**
(EE) 
(EE) Server terminated with error (1). Closing log file.
xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error
root@DellXPS-15-9530:/home/frankenstein# systemctl status sddm.service
[1;32m&#9679;[0m sddm.service - Simple Desktop Display Manager
   Loaded: loaded (/lib/systemd/system/sddm.service; enabled; vendor preset: enabled)
   Active: [1;32mactive (running)[0m since Thu 2016-01-07 23:00:13 MST; 9min ago
     Docs: man:sddm(1)
           man:sddm.conf(5)
 Main PID: 1685 (sddm)
   CGroup: /system.slice/sddm.service
           &#9492;&#9472;1685 /usr/bin/sddm

```


Here is the /var/log/Xorg.0.log output:

```
[    19.794] X.Org X Server 1.17.2
Release Date: 2015-06-16
[    19.794] X Protocol Version 11, Revision 0
[    19.794] Build Operating System: Linux 3.13.0-68-generic x86_64 Ubuntu
[    19.794] Current Operating System: Linux DellXPS-15-9530 4.2.0-23-generic #28-Ubuntu SMP Sun Dec 27 17:47:31 UTC 2015 x86_64
[    19.794] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-23-generic root=UUID=f211db28-021e-4475-baa2-db2d92d862dc ro quiet splash
[    19.794] Build Date: 12 November 2015  05:33:29PM
[    19.794] xorg-server 2:1.17.2-1ubuntu9.1 (For technical support please see http://www.ubuntu.com/support) 
[    19.794] Current version of pixman: 0.32.6
[    19.794]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    19.794] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    19.794] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jan  8 10:59:10 2016
[    19.829] (==) Using config file: "/etc/X11/xorg.conf"
[    19.829] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    19.850] [B]Data incomplete in file /etc/X11/xorg.conf
    Undefined Screen "nvidia" referenced by ServerLayout "layout"[/B].
[    19.850] (EE) Problem parsing the config file
[    19.850] (EE) Error parsing the config file
[    19.850] (EE) 
Fatal server error:
[    19.850] (EE) no screens found(EE) 
[    19.850] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    19.850] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    19.850] (EE) 
[    19.850] (EE) Server terminated with error (1). Closing log file.
```

The Xorg.0.log file is/was already posted. Please see the output for it already posted in this thread (above). 


As you can see from the last output above, SDDM, which apparently is the new Greeter for Kubuntu 15.10 is active. Yet not loading. 

Also, within
```

cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.


# evbug is a debug tool that should be loaded explicitly
blacklist evbug


# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd


# replaced by e100
blacklist eepro100


# replaced by tulip
blacklist de4x5


# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394


# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m


# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2


# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801


# replaced by p54pci
blacklist prism54


# replaced by b43 and ssb.
blacklist bcm43xx


# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps


# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi


# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp


# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr


# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

```

I do believe that the above output for all the relevant config files are correct. I have used a number of resources to install that version of nvidia. Again, I think that perhaps one of my mistakes was to switch to nvidia driver rather than the Driver listing. **I also believe that bumblebee was made active via "systemctl". I think I did though, but I am not 100 percent sure.** 

If there is any other information you require, please let me know right away. Looking for some assistance, please.

---

### Post by Hodevah on 2016-01-08
I have tried to remove the offending** xorg.conf.01082016** file. 

```
sudo rm xorg.conf.01082016
``` file from** /etc/X11**/ and then to edit via nano the** xorg.conf **file to read

```
Section "ServerLayout"    Identifier "layout"
    Screen 0 "nvidia-355"
    Inactive "intel"
EndSection



```
[B]
rather than[/B]:

```
Section "ServerLayout"    Identifier "layout"
    Screen 0 "nvidia"
    Inactive "intel"
EndSection



```

and then to ```
sudo systemctl start sddm.service
```

No go. What happens is that the a **new xorg.conf** file seems to be regenerated and the old xorg.conf file is renamed (after been deleted) to **xorg.conf.01082016** again.

still looking for some help please.

---

### Post by Hodevah on 2016-01-09
I am just wondering if I should "nouveau.modeset=0" to the kernel command line. Not sure if it would work.  Again, still looking for help from someone here on the board.  :)

---

### Post by Hodevah on 2016-01-10
Bump.
Again, looking for help here please.

---

