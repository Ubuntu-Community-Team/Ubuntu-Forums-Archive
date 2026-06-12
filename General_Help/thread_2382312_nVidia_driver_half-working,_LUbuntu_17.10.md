---
title: "nVidia driver half-working, LUbuntu 17.10"
date: 2018-01-11
forum: General Help
---

### Post by zeroth404 on 2018-01-11
This is a laptop with nVidia Geforce GTX 960m.
nvidia drivers 304, 331, and 340 all sort of half-work. The stock driver is slower (presumably noveau or however they spell that). nvidia drivers 361, 375, 346, 352, 384 all seem to just not work whatsoever. So I concluded 340 is the one I should be using.


However, glxgears complains that GLX is missing.


I've also tried this "bumblebee" program that tries to juggle between the integrated Intel HD driver and the nVidia driver, but my system hard-locks when I try to load X with it (even Alt+SysRQ+B won't work at that point).


I just moved over from XUbuntu and things were working fine with one of the nvidia drivers. So I'm not sure what the heck is going on here but I'm at wits end.


I've googled this for a while, but here I am. Any advice is greatly appreciated!


```

antic@antic-Inspiron-7559:~$ glxgears 
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

```


and:
```

antic@antic-Inspiron-7559:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".


Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```


```

root@antic-Inspiron-7559:/home/antic# cat /etc/issue
Ubuntu 17.10 \n \l


root@antic-Inspiron-7559:/home/antic# lspci | grep vid -i
02:00.0 3D controller: NVIDIA Corporation GM107M [GeForce GTX 960M] (rev a2)


root@antic-Inspiron-7559:/home/antic# uname -a
Linux antic-Inspiron-7559 4.13.0-25-generic #29-Ubuntu SMP Mon Jan 8 21:14:41 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux


root@antic-Inspiron-7559:/home/antic# dpkg -l 'nvidia*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
rc  nvidia-304     304.137-0ubu amd64        NVIDIA legacy binary driver - ver
ii  nvidia-340     340.104-0ubu amd64        NVIDIA binary driver - version 34
rc  nvidia-384     384.111-0ubu amd64        NVIDIA binary driver - version 38
un  nvidia-common  <none>       <none>       (no description available)
un  nvidia-driver- <none>       <none>       (no description available)
un  nvidia-libopen <none>       <none>       (no description available)
un  nvidia-libopen <none>       <none>       (no description available)
un  nvidia-libopen <none>       <none>       (no description available)
un  nvidia-libopen <none>       <none>       (no description available)
un  nvidia-opencl- <none>       <none>       (no description available)
rc  nvidia-opencl- 304.137-0ubu amd64        NVIDIA OpenCL ICD
ii  nvidia-opencl- 340.104-0ubu amd64        NVIDIA OpenCL ICD
rc  nvidia-opencl- 384.111-0ubu amd64        NVIDIA OpenCL ICD
un  nvidia-persist <none>       <none>       (no description available)
ii  nvidia-prime   0.8.5        amd64        Tools to enable NVIDIA's Prime
ii  nvidia-setting 384.69-0ubun amd64        Tool for configuring the NVIDIA g
un  nvidia-setting <none>       <none>       (no description available)
un  nvidia-smi     <none>       <none>       (no description available)


cat /var/log/Xorg.0.log | egrep "(EE|EE)"
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    40.318] (EE) [drm] Failed to open DRM device for (null): -22
[    40.318] (EE) open /dev/fb0: No such file or directory
[    40.318] (EE) open /dev/fb0: No such file or directory
[    40.318] (EE) Screen 0 deleted because of no matching config section.
[    40.318] (EE) Screen 0 deleted because of no matching config section.
[    41.967] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)




root@antic-Inspiron-7559:/home/antic# cat /var/log/Xorg.0.log | egrep -i "(video|vidia|glx)"
[    40.307]     X.Org Video Driver: 23.0
[    40.309] (II) "glx" will be loaded by default.
[    40.309] (II) LoadModule: "glx"
[    40.309] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    40.316] (II) Module glx: vendor="NVIDIA Corporation"
[    40.316] (II) NVIDIA GLX Module  340.104  Thu Sep 14 16:40:42 PDT 2017
[    40.316] (==) Matched nvidia as autoconfigured driver 0
[    40.317] (II) LoadModule: "nvidia"
[    40.317] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    40.317] (II) Module nvidia: vendor="NVIDIA Corporation"
[    40.317]     Module class: X.Org Video Driver
[    40.317]     Module class: X.Org Video Driver
[    40.317]     ABI class: X.Org Video Driver, version 23.0
[    40.317]     Module class: X.Org Video Driver
[    40.317]     ABI class: X.Org Video Driver, version 23.0
[    40.317]     Module class: X.Org Video Driver
[    40.317]     ABI class: X.Org Video Driver, version 23.0
[    40.317]     Module class: X.Org Video Driver
[    40.317]     ABI class: X.Org Video Driver, version 23.0
[    40.317] (II) NVIDIA dlloader X Driver  340.104  Thu Sep 14 16:18:31 PDT 2017
[    40.317] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    40.317] (II) NOUVEAU driver for NVIDIA chipset families :
[    40.318]     ABI class: X.Org Video Driver, version 23.0
[    40.318]     ABI class: X.Org Video Driver, version 23.0
[    40.318]     ABI class: X.Org Video Driver, version 23.0
[    40.318]     ABI class: X.Org Video Driver, version 23.0
[    41.781] (II) UnloadModule: "nvidia"
[    41.781] (II) Unloading nvidia
[    41.781]     ABI class: X.Org Video Driver, version 23.0
[    41.967] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)


root@antic-Inspiron-7559:/home/antic# cat /etc/issue
Ubuntu 17.10 \n \l


root@antic-Inspiron-7559:/home/antic# uname -a
Linux antic-Inspiron-7559 4.13.0-25-generic #29-Ubuntu SMP Mon Jan 8 21:14:41 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
root@antic-Inspiron-7559:/home/antic# dpkg -l 'nvidia*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
rc  nvidia-304     304.137-0ubu amd64        NVIDIA legacy binary driver - ver
ii  nvidia-340     340.104-0ubu amd64        NVIDIA binary driver - version 34
rc  nvidia-384     384.111-0ubu amd64        NVIDIA binary driver - version 38
un  nvidia-common  <none>       <none>       (no description available)
un  nvidia-driver- <none>       <none>       (no description available)
un  nvidia-libopen <none>       <none>       (no description available)
un  nvidia-libopen <none>       <none>       (no description available)
un  nvidia-libopen <none>       <none>       (no description available)
un  nvidia-libopen <none>       <none>       (no description available)
un  nvidia-opencl- <none>       <none>       (no description available)
rc  nvidia-opencl- 304.137-0ubu amd64        NVIDIA OpenCL ICD
ii  nvidia-opencl- 340.104-0ubu amd64        NVIDIA OpenCL ICD
rc  nvidia-opencl- 384.111-0ubu amd64        NVIDIA OpenCL ICD
un  nvidia-persist <none>       <none>       (no description available)
ii  nvidia-prime   0.8.5        amd64        Tools to enable NVIDIA's Prime
ii  nvidia-setting 384.69-0ubun amd64        Tool for configuring the NVIDIA g
un  nvidia-setting <none>       <none>       (no description available)
un  nvidia-smi     <none>       <none>       (no description available)


cat /var/log/Xorg.0.log | egrep "(EE|EE)"
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    40.318] (EE) [drm] Failed to open DRM device for (null): -22
[    40.318] (EE) open /dev/fb0: No such file or directory
[    40.318] (EE) open /dev/fb0: No such file or directory
[    40.318] (EE) Screen 0 deleted because of no matching config section.
[    40.318] (EE) Screen 0 deleted because of no matching config section.
[    41.967] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)




root@antic-Inspiron-7559:/home/antic# cat /var/log/Xorg.0.log | egrep -i "(video|vidia|glx)"
[    40.307]     X.Org Video Driver: 23.0
[    40.309] (II) "glx" will be loaded by default.
[    40.309] (II) LoadModule: "glx"
[    40.309] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    40.316] (II) Module glx: vendor="NVIDIA Corporation"
[    40.316] (II) NVIDIA GLX Module  340.104  Thu Sep 14 16:40:42 PDT 2017
[    40.316] (==) Matched nvidia as autoconfigured driver 0
[    40.317] (II) LoadModule: "nvidia"
[    40.317] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    40.317] (II) Module nvidia: vendor="NVIDIA Corporation"
[    40.317]     Module class: X.Org Video Driver
[    40.317]     Module class: X.Org Video Driver
[    40.317]     ABI class: X.Org Video Driver, version 23.0
[    40.317]     Module class: X.Org Video Driver
[    40.317]     ABI class: X.Org Video Driver, version 23.0
[    40.317]     Module class: X.Org Video Driver
[    40.317]     ABI class: X.Org Video Driver, version 23.0
[    40.317]     Module class: X.Org Video Driver
[    40.317]     ABI class: X.Org Video Driver, version 23.0
[    40.317] (II) NVIDIA dlloader X Driver  340.104  Thu Sep 14 16:18:31 PDT 2017
[    40.317] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    40.317] (II) NOUVEAU driver for NVIDIA chipset families :
[    40.318]     ABI class: X.Org Video Driver, version 23.0
[    40.318]     ABI class: X.Org Video Driver, version 23.0
[    40.318]     ABI class: X.Org Video Driver, version 23.0
[    40.318]     ABI class: X.Org Video Driver, version 23.0
[    41.781] (II) UnloadModule: "nvidia"
[    41.781] (II) Unloading nvidia
[    41.781]     ABI class: X.Org Video Driver, version 23.0
[    41.967] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)


root@antic-Inspiron-7559:/home/antic# lsmod | grep vid -i
nvidia_uvm             36864  0
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
videodev              176128  3 uvcvideo,videobuf2_core,videobuf2_v4l2
media                  40960  2 uvcvideo,videodev
nvidia              10571776  1 nvidia_uvm
drm                   356352  4 nvidia,i915,drm_kms_helper
video                  40960  3 dell_wmi,dell_laptop,i915

```

---

### Post by Bashing-om on 2018-01-11
zeroth404; Hello;

The correct driver for your nvidia card is the 384 version:
[http://www.nvidia.com/download/driverResults.aspx/128737/en-us](http://www.nvidia.com/download/driverResults.aspx/128737/en-us)

Let's clean up and have the system install the driver(s).
* Disable secure boot in bios ! *
```

sudo apt purge nvidia
sudo rm /etc/X11/Xorg.conf
sudo apt autoremove
dpkg -l | awk '/^rc/{print $2}' | xargs sudo dpkg -P
sudo apt update
sudo ubuntu-drivers autoinstall

```
reboot to see the effect .

What we do not know is the state of the Intel side - a tale will be told.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by zeroth404 on 2018-01-11
I did as you said, here's the result of the last tool. I'm rebooting now to see what happens, will reply soon.
```

root@antic-Inspiron-7559:/home/antic# ubuntu-drivers autoinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  iucode-tool libcuda1-384 nvidia-opencl-icd-384 nvidia-prime nvidia-settings
The following packages will be REMOVED:
  libcuda1-340
The following NEW packages will be installed:
  intel-microcode iucode-tool libcuda1-384 nvidia-384 nvidia-opencl-icd-384 nvidia-prime nvidia-settings
0 upgraded, 7 newly installed, 1 to remove and 5 not upgraded.
Need to get 1,129 kB/85.7 MB of archives.
After this operation, 336 MB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu artful/restricted amd64 iucode-tool amd64 2.1.2-2 [38.9 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu artful-updates/main amd64 intel-microcode amd64 3.20180108.0~ubuntu17.10.1 [1,090 kB]
Fetched 1,129 kB in 1s (1,009 kB/s)        
(Reading database ... 249308 files and directories currently installed.)
Removing libcuda1-340 (340.104-0ubuntu2) ...
Selecting previously unselected package iucode-tool.
(Reading database ... 249301 files and directories currently installed.)
Preparing to unpack .../0-iucode-tool_2.1.2-2_amd64.deb ...
Unpacking iucode-tool (2.1.2-2) ...
Selecting previously unselected package nvidia-384.
Preparing to unpack .../1-nvidia-384_384.111-0ubuntu0.17.10.1_amd64.deb ...
Unpacking nvidia-384 (384.111-0ubuntu0.17.10.1) ...
Selecting previously unselected package libcuda1-384.
Preparing to unpack .../2-libcuda1-384_384.111-0ubuntu0.17.10.1_amd64.deb ...
Unpacking libcuda1-384 (384.111-0ubuntu0.17.10.1) ...
Selecting previously unselected package nvidia-opencl-icd-384.
Preparing to unpack .../3-nvidia-opencl-icd-384_384.111-0ubuntu0.17.10.1_amd64.deb ...
Unpacking nvidia-opencl-icd-384 (384.111-0ubuntu0.17.10.1) ...
Selecting previously unselected package nvidia-prime.
Preparing to unpack .../4-nvidia-prime_0.8.5_amd64.deb ...
Unpacking nvidia-prime (0.8.5) ...
Selecting previously unselected package nvidia-settings.
Preparing to unpack .../5-nvidia-settings_384.69-0ubuntu1_amd64.deb ...
Unpacking nvidia-settings (384.69-0ubuntu1) ...
Selecting previously unselected package intel-microcode.
Preparing to unpack .../6-intel-microcode_3.20180108.0~ubuntu17.10.1_amd64.deb ...
Unpacking intel-microcode (3.20180108.0~ubuntu17.10.1) ...
Setting up nvidia-prime (0.8.5) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for ureadahead (0.100.0-20) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu3) ...
Setting up nvidia-settings (384.69-0ubuntu1) ...
Processing triggers for libc-bin (2.26-0ubuntu2) ...
Setting up iucode-tool (2.1.2-2) ...
Setting up nvidia-384 (384.111-0ubuntu0.17.10.1) ...
update-alternatives: using /usr/lib/nvidia-384/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-384/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_EGL.conf (x86_64-linux-gnu_egl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-384/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-384/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_EGL.conf (i386-linux-gnu_egl_conf) in auto mode
update-alternatives: using /usr/share/nvidia-384/glamor.conf to provide /usr/share/X11/xorg.conf.d/glamoregl.conf (glamor_conf) in auto mode
dpkg: error: version '-' has bad syntax: revision number is empty
dpkg: error: version '-' has bad syntax: revision number is empty
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-384
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
Adding system user `nvidia-persistenced' (UID 114) ...
Adding new group `nvidia-persistenced' (GID 125) ...
Adding new user `nvidia-persistenced' (UID 114) with group `nvidia-persistenced' ...
Not creating home directory `/'.
Loading new nvidia-384-384.111 DKMS files...
Building for 4.13.0-25-generic
Building for architecture x86_64
Building initial module for 4.13.0-25-generic
Done.


nvidia_384:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.13.0-25-generic/updates/dkms/


nvidia_384_modeset.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.13.0-25-generic/updates/dkms/


nvidia_384_drm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.13.0-25-generic/updates/dkms/


nvidia_384_uvm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.13.0-25-generic/updates/dkms/


depmod...


DKMS: install completed.
Processing triggers for man-db (2.7.6.1-2) ...
Setting up nvidia-opencl-icd-384 (384.111-0ubuntu0.17.10.1) ...
Setting up intel-microcode (3.20180108.0~ubuntu17.10.1) ...
update-initramfs: deferring update (trigger activated)
intel-microcode: microcode will be updated at next boot
Setting up libcuda1-384 (384.111-0ubuntu0.17.10.1) ...
Processing triggers for libc-bin (2.26-0ubuntu2) ...
Processing triggers for initramfs-tools (0.125ubuntu12) ...
update-initramfs: Generating /boot/initrd.img-4.13.0-25-generic
root@antic-Inspiron-7559:/home/antic# 

```

---

### Post by zeroth404 on 2018-01-11
Still no GLX after reboot.

Also, the video refresh rate is sluggish again like when I was using noveau.
```

antic@antic-Inspiron-7559:~$ glxgears 
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
antic@antic-Inspiron-7559:~$ lsmod | grep vid -i
nvidia_uvm            667648  0
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
videodev              176128  3 uvcvideo,videobuf2_core,videobuf2_v4l2
media                  40960  2 uvcvideo,videodev
nvidia_drm             45056  0
nvidia_modeset        860160  1 nvidia_drm
nvidia              13139968  2 nvidia_modeset,nvidia_uvm
drm_kms_helper        167936  2 i915,nvidia_drm
drm                   356352  4 i915,nvidia_drm,drm_kms_helper
video                  40960  3 dell_wmi,dell_laptop,i915
antic@antic-Inspiron-7559:~$ grep EE /var/log/Xorg.0.log
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     3.842] (EE) [drm] Failed to open DRM device for (null): -22
[     3.843] (EE) Screen 0 deleted because of no matching config section.
[     3.850] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
antic@antic-Inspiron-7559:~$ grep WW /var/log/Xorg.0.log
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     3.760] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     3.760] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     3.760] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     3.760] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     3.760] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     3.763] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[     3.842] (WW) Falling back to old probe method for modesetting
[     3.843] (WW) Falling back to old probe method for vesa
antic@antic-Inspiron-7559:~$ grep vidia -i /var/log/Xorg.0.log
[     3.829] (II) Module glx: vendor="NVIDIA Corporation"
[     3.830] (II) NVIDIA GLX Module  384.111  Tue Dec 19 22:51:13 PST 2017
[     3.830] (==) Matched nvidia as autoconfigured driver 0
[     3.830] (II) LoadModule: "nvidia"
[     3.830] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[     3.835] (II) Module nvidia: vendor="NVIDIA Corporation"
[     3.841] (II) NVIDIA dlloader X Driver  384.111  Tue Dec 19 22:25:34 PST 2017
[     3.841] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[     3.842] (II) NOUVEAU driver for NVIDIA chipset families :
[     3.850] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
antic@antic-Inspiron-7559:~$ dpkg -l | grep vidia -i
ii  bbswitch-dkms                                 0.8-4ubuntu1                                               amd64        Interface for toggling the power on NVIDIA Optimus video cards
ii  libcuda1-384                                  384.111-0ubuntu0.17.10.1                                   amd64        NVIDIA CUDA runtime library
ii  nvidia-384                                    384.111-0ubuntu0.17.10.1                                   amd64        NVIDIA binary driver - version 384.111
ii  nvidia-opencl-icd-384                         384.111-0ubuntu0.17.10.1                                   amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                  0.8.5                                                      amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                               384.69-0ubuntu1                                            amd64        Tool for configuring the NVIDIA graphics driver
antic@antic-Inspiron-7559:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".


Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
antic@antic-Inspiron-7559:~$ 

```

---

### Post by Bashing-om on 2018-01-11
zeroth404' Humm ..

All "looks" good .. hummmm ....
what Desktop Environment ? wayland ?
```

ps -efly | grep Xorg
echo $XDG_SESSION_TYPE

```


What says the GPU manager ?
```

cat /var/log/gpu-manager.log

```

[INDENT][INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT][/INDENT]

---

### Post by zeroth404 on 2018-01-11
```

antic@antic-Inspiron-7559:~$ ps -efly | grep Xorg
S root       881   858  0  80   0 57152 87046 -      17:12 tty7     00:00:30 /usr/lib/xorg/Xorg -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
S antic     2782  2767  0  80   0   928  3589 pipe_w 19:46 pts/0    00:00:00 grep --color=auto Xorg
antic@antic-Inspiron-7559:~$ echo $XDG_SESSION_TYPE
x11
antic@antic-Inspiron-7559:~$ 
antic@antic-Inspiron-7559:~$ cat /var/log/gpu-manager.log
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-fglrx-was-loaded file
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for fglrx modules in /lib/modules/4.13.0-25-generic/updates/dkms
Looking for nvidia modules in /lib/modules/4.13.0-25-generic/updates/dkms
Found nvidia module: nvidia_384_uvm.ko
Looking for amdgpu modules in /lib/modules/4.13.0-25-generic/updates/dkms
Is nvidia loaded? yes
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is fglrx loaded? no
Was fglrx unloaded? no
Is fglrx blacklisted? no
Is intel loaded? yes
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is amdgpu versioned? no
Is amdgpu pro stack? no
Is nouveau loaded? no
Is nouveau blacklisted? yes
Is fglrx kernel module available? no
Is nvidia kernel module available? yes
Is amdgpu kernel module available? no
Vendor/Device Id: 8086:191b
BusID "PCI:0@0:2:0"
Is boot vga? yes
Error: can't access /sys/bus/pci/devices/0000:00:02.0/driver
The device is not bound to any driver. Skipping...
Vendor/Device Id: 10de:139b
BusID "PCI:2@0:0:0"
Is boot vga? no
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Does it require offloading? no
last cards number = 1
Has amd? no
Has intel? no
Has nvidia? yes
How many cards? 1
Has the system changed? No
main_arch_path x86_64-linux-gnu, other_arch_path i386-linux-gnu
Current alternative: /usr/lib/nvidia-384/ld.so.conf
Current core alternative: (null)
Current egl alternative: /usr/lib/nvidia-384/ld.so.conf
Is nvidia enabled? yes
Is nvidia egl enabled? yes
Is fglrx enabled? no
Is mesa enabled? no
Is mesa egl enabled? no
Is pxpress enabled? no
Is prime enabled? no
Is prime egl enabled? no
Is nvidia available? yes
Is nvidia egl available? no
Is fglrx available? no
Is fglrx-core available? no
Is mesa available? yes
Is mesa egl available? yes
Is pxpress available? no
Is prime available? yes
Is prime egl available? no
Single card detected
No change - nothing to do
antic@antic-Inspiron-7559:~$ 



```

---

### Post by Bashing-om on 2018-01-11
zeroth404; Ouch !

We have:
> 
Error: can't access /sys/bus/pci/devices/0000:00:02.0/driver
The device is not bound to any driver. Skipping...


I do not have a 17.10 install as a reference to know; but what have we ?
```

ls -al /sys/bus/pci/devices/0000:00:02.0

```
Start down a rabbit hole ??

Be aware in  my 16.04 install I have:
> 
sysop@x1604:~/Desktop$ ls -al /sys/bus/pci/devices/0000:06:00.0
lrwxrwxrwx 1 root root 0 Jan 11 19:22 /sys/bus/pci/devices/0000:06:00.0 -> ../../../devices/pci0000:00/0000:00:0f.0/0000:06:00.0
sysop@x1604:~/Desktop$ 


As to a fix -
[INDENT][INDENT]just do not know, yet
[/INDENT][/INDENT]

---

### Post by zeroth404 on 2018-01-12
```

antic@antic-Inspiron-7559:~$ ls -al /sys/bus/pci/devices/0000:00:02.0
lrwxrwxrwx 1 root root 0 Jan 12 17:02 /sys/bus/pci/devices/0000:00:02.0 -> ../../../devices/pci0000:00/0000:00:02.0
antic@antic-Inspiron-7559:~$ 

```


I appreciate your time.

---

### Post by Bashing-om on 2018-01-12
zeroth404; Yukkie ( on me ) ..


I am chasing down the wrong rabbit hole .
Gimme a bit to regroup.


[INDENT]A know-it-all; I am not
[/INDENT]

---

### Post by Bashing-om on 2018-01-12
zeroth404; OK ..

Let's see where this rabbit hole leads to:
```

ls -al /sys/bus/pci/devices/0000:00:02.0/driver

```

my 16.04 result:
> 
sysop@x1604:~$ ls -al /sys/bus/pci/devices/0000:06:00.0/driver
lrwxrwxrwx 1 root root 0 Jan 12 16:54 /sys/bus/pci/devices/0000:06:00.0/driver -> ../../../../bus/pci/drivers/nvidia


where I get even deeper - let's see how deep you get and where it all ends.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by dorian7 on 2018-01-12
I have the same Nvidia 960m in an MSI laptop and I use 387.26 which works perfectly for me.  This is on 16.04 with the 4.10 kernel.

By the way, kernel 4.13 kills the Nvidia optimus driver completely.  I just ended up fixing it all and reverting my kernel.  I've been tweeting about it @DorianDotSlash

---

### Post by zeroth404 on 2018-01-13
root@antic-Inspiron-7559:/home/antic# ls -al /sys/bus/pci/devices/0000:00:02.0/driver
ls: cannot access '/sys/bus/pci/devices/0000:00:02.0/driver': No such file or directory
root@antic-Inspiron-7559:/home/antic# 


If we reach a dead-end, I'm going to try a previous release of LUbuntu.

---

### Post by Bashing-om on 2018-01-13
zeroth404; Hey ..

As dorian7 advises, there are many issues currently with the latest kernels - patching for the vulnerabilities:
[https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown](https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown)

Note that the nvidia drivers are affected. I worked the same issue on irc #ubuntu, last night, with  resolution by installing the 390 version driver from our trusted PPA .

Let's do the same and see what results in your case:
Make sure secure boot is disabled in bios **
```

sudo apt update
sudo apt full-upgrade

```

reboot the machine so we are booting with any newly installed kernel.

Now we purge the old nvidia driver. activate the PPA  and install the 390 version driver:
```

sudo apt purge nvidia*
sudo rm /etc/X11/xorg.conf
sudo apt autoremove
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo ubuntu-drivers autoinstall

```

reboot once more and tell me
[INDENT][INDENT][INDENT]all looks good now 
[/INDENT][/INDENT][/INDENT]

---

### Post by zeroth404 on 2018-01-13
UEFI is and has been off.

```

root@antic-Inspiron-7559:/home/antic# apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  gir1.2-javascriptcoregtk-4.0 gir1.2-webkit2-4.0 irssi
  libjavascriptcoregtk-4.0-18 libwebkit2gtk-4.0-37
5 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 15.3 MB/16.0 MB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n]   

```

doesn't look like anything important is coming through.

---

### Post by dorian7 on 2018-01-13
> **Bashing-om said:**
> zeroth404; Hey ..

As dorian7 advises, there are many issues currently with the latest kernels - patching for the vulnerabilities:
[https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown](https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown)

Note that the nvidia drivers are affected. I worked the same issue on irc #ubuntu, last night, with resolution by installing the 390 version driver from our trusted PPA .

.....snip.....



Did 390 work for you? Do you have Nvidia optimus graphics? I put in the PPA and went with a newer 387.34 from 387.26 and it didn't fix my issues. I didn't want to touch 390 yet because it's very early in staging, and optimus is very picky.

---

### Post by Bashing-om on 2018-01-13
@dorian7;
Yes, in that instance installing 390 from our PPA did in fact work .. and yes was optimus - make sure there are no driver conflicts and BumbleBee is not a factor.

@zeroth404; UEFI should be active IF you installed the operating system in EFI mode, but secure boot ( different !) should be disabled to allow the installation of additional trusted software ( nvidia) .
continue on to the "autoinstall" and advise of results.

[INDENT][INDENT]maybe Yes !
[/INDENT][/INDENT]

---

### Post by zeroth404 on 2018-01-13
I tried the nvidia PPA and 390 just to see. no solution yet.

```

root@antic-Inspiron-7559:/home/antic# lsmod | grep vidia -i
nvidia_uvm            753664  0
nvidia_drm             40960  0
nvidia_modeset       1089536  1 nvidia_drm
nvidia              14311424  2 nvidia_modeset,nvidia_uvm
drm_kms_helper        167936  2 i915,nvidia_drm
drm                   356352  4 i915,nvidia_drm,drm_kms_helper
ipmi_msghandler        40960  2 nvidia,ipmi_devintf
root@antic-Inspiron-7559:/home/antic# grep EE /var/log/Xorg.0.log
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     3.866] (EE) [drm] Failed to open DRM device for (null): -2
[     3.867] (EE) Screen 0 deleted because of no matching config section.
[     3.874] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
root@antic-Inspiron-7559:/home/antic# grep WW /var/log/Xorg.0.log
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     3.787] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     3.787] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     3.787] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     3.787] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     3.787] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     3.790] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[     3.866] (WW) Falling back to old probe method for modesetting
[     3.867] (WW) Falling back to old probe method for vesa
root@antic-Inspiron-7559:/home/antic# grep vidia -i /var/log/Xorg.0.log
[     3.855] (II) Module glx: vendor="NVIDIA Corporation"
[     3.856] (II) NVIDIA GLX Module  390.12  Wed Dec 20 06:08:47 PST 2017
[     3.856] (==) Matched nvidia as autoconfigured driver 0
[     3.856] (II) LoadModule: "nvidia"
[     3.856] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[     3.860] (II) Module nvidia: vendor="NVIDIA Corporation"
[     3.866] (II) NVIDIA dlloader X Driver  390.12  Wed Dec 20 05:44:24 PST 2017
[     3.866] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[     3.866] (II) NOUVEAU driver for NVIDIA chipset families :
[     3.874] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
root@antic-Inspiron-7559:/home/antic# dpkg -l | grep -i vidia
ii  bbswitch-dkms                                 0.8-4ubuntu1                                               amd64        Interface for toggling the power on NVIDIA Optimus video cards
ii  libcuda1-390                                  390.12-0ubuntu0~gpu17.10.2                                 amd64        NVIDIA CUDA runtime library
rc  nvidia-384                                    384.111-0ubuntu0.17.10.1                                   amd64        NVIDIA binary driver - version 384.111
ii  nvidia-390                                    390.12-0ubuntu0~gpu17.10.2                                 amd64        NVIDIA binary driver - version 390.12
rc  nvidia-opencl-icd-384                         384.111-0ubuntu0.17.10.1                                   amd64        NVIDIA OpenCL ICD
ii  nvidia-opencl-icd-390                         390.12-0ubuntu0~gpu17.10.2                                 amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                  0.8.5                                                      amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                               390.12-0ubuntu0~gpu17.10.1                                 amd64        Tool for configuring the NVIDIA graphics driver
root@antic-Inspiron-7559:/home/antic#

```

I'm gonna try the autoinstall with this version. If that doesn't work I'll purging it, remove the PPA, and reverting to 384 and try the autoinstall again.

I installed without UEFI, so no secure boot.

---

### Post by zeroth404 on 2018-01-13
no difference with autoinstall 390. purged it, removed PPA, and tried autoinstall of 384

```

root@antic-Inspiron-7559:/home/antic# ubuntu-drivers autoinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  libcuda1-384 nvidia-opencl-icd-384 nvidia-prime nvidia-settings
The following NEW packages will be installed:
  libcuda1-384 nvidia-384 nvidia-opencl-icd-384 nvidia-prime nvidia-settings
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/84.6 MB of archives.
After this operation, 362 MB of additional disk space will be used.
Selecting previously unselected package nvidia-384.
(Reading database ... 249384 files and directories currently installed.)
Preparing to unpack .../nvidia-384_384.111-0ubuntu0.17.10.1_amd64.deb ...
Unpacking nvidia-384 (384.111-0ubuntu0.17.10.1) ...
Selecting previously unselected package libcuda1-384.
Preparing to unpack .../libcuda1-384_384.111-0ubuntu0.17.10.1_amd64.deb ...
Unpacking libcuda1-384 (384.111-0ubuntu0.17.10.1) ...
Selecting previously unselected package nvidia-opencl-icd-384.
Preparing to unpack .../nvidia-opencl-icd-384_384.111-0ubuntu0.17.10.1_amd64.deb ...
Unpacking nvidia-opencl-icd-384 (384.111-0ubuntu0.17.10.1) ...
Selecting previously unselected package nvidia-prime.
Preparing to unpack .../nvidia-prime_0.8.5_amd64.deb ...
Unpacking nvidia-prime (0.8.5) ...
Selecting previously unselected package nvidia-settings.
Preparing to unpack .../nvidia-settings_384.69-0ubuntu1_amd64.deb ...
Unpacking nvidia-settings (384.69-0ubuntu1) ...
Setting up nvidia-prime (0.8.5) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for ureadahead (0.100.0-20) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu3) ...
Setting up nvidia-settings (384.69-0ubuntu1) ...
Processing triggers for libc-bin (2.26-0ubuntu2) ...
Setting up nvidia-384 (384.111-0ubuntu0.17.10.1) ...
update-alternatives: using /usr/lib/nvidia-384/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-384/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_EGL.conf (x86_64-linux-gnu_egl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-384/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-384/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_EGL.conf (i386-linux-gnu_egl_conf) in auto mode
update-alternatives: using /usr/share/nvidia-384/glamor.conf to provide /usr/share/X11/xorg.conf.d/glamoregl.conf (glamor_conf) in auto mode
dpkg: error: version '-' has bad syntax: revision number is empty
dpkg: error: version '-' has bad syntax: revision number is empty
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-384
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
Adding system user `nvidia-persistenced' (UID 114) ...
Adding new group `nvidia-persistenced' (GID 125) ...
Adding new user `nvidia-persistenced' (UID 114) with group `nvidia-persistenced' ...
Not creating home directory `/'.
Loading new nvidia-384-384.111 DKMS files...
Building for 4.13.0-25-generic
Building for architecture x86_64
Building initial module for 4.13.0-25-generic
Done.


nvidia_384:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.13.0-25-generic/updates/dkms/


nvidia_384_modeset.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.13.0-25-generic/updates/dkms/


nvidia_384_drm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.13.0-25-generic/updates/dkms/


nvidia_384_uvm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.13.0-25-generic/updates/dkms/


depmod...


DKMS: install completed.
Processing triggers for man-db (2.7.6.1-2) ...
Setting up nvidia-opencl-icd-384 (384.111-0ubuntu0.17.10.1) ...
Setting up libcuda1-384 (384.111-0ubuntu0.17.10.1) ...
Processing triggers for libc-bin (2.26-0ubuntu2) ...
Processing triggers for initramfs-tools (0.125ubuntu12) ...
update-initramfs: Generating /boot/initrd.img-4.13.0-25-generic
root@antic-Inspiron-7559:/home/antic# 

```

rebooted, then this:
```

root@antic-Inspiron-7559:/home/antic# lsmod | grep vidia -i 
nvidia_uvm            753664  0
nvidia_drm             40960  0
nvidia_modeset       1089536  1 nvidia_drm
nvidia              14311424  2 nvidia_modeset,nvidia_uvm
drm_kms_helper        167936  2 i915,nvidia_drm
drm                   356352  4 i915,nvidia_drm,drm_kms_helper
ipmi_msghandler        40960  2 nvidia,ipmi_devintf
root@antic-Inspiron-7559:/home/antic# dpkg -l | grep vidia -i
ii  bbswitch-dkms                                 0.8-4ubuntu1                                               amd64        Interface for toggling the power on NVIDIA Optimus video cards
ii  libcuda1-384                                  384.111-0ubuntu0.17.10.1                                   amd64        NVIDIA CUDA runtime library
ii  nvidia-384                                    384.111-0ubuntu0.17.10.1                                   amd64        NVIDIA binary driver - version 384.111
ii  nvidia-opencl-icd-384                         384.111-0ubuntu0.17.10.1                                   amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                  0.8.5                                                      amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                               384.69-0ubuntu1                                            amd64        Tool for configuring the NVIDIA graphics driver
root@antic-Inspiron-7559:/home/antic# grep EE /var/log/Xorg.0.log
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     3.846] (EE) [drm] Failed to open DRM device for (null): -2
[     3.847] (EE) Screen 0 deleted because of no matching config section.
[     3.854] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
root@antic-Inspiron-7559:/home/antic# grep WW /var/log/Xorg.0.log
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     3.769] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     3.769] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     3.769] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     3.769] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     3.769] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     3.772] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[     3.846] (WW) Falling back to old probe method for modesetting
[     3.847] (WW) Falling back to old probe method for vesa
root@antic-Inspiron-7559:/home/antic# grep nvidia /var/log/Xorg.0.log -i
[     3.835] (II) Module glx: vendor="NVIDIA Corporation"
[     3.835] (II) NVIDIA GLX Module  390.12  Wed Dec 20 06:08:47 PST 2017
[     3.835] (==) Matched nvidia as autoconfigured driver 0
[     3.835] (II) LoadModule: "nvidia"
[     3.836] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[     3.840] (II) Module nvidia: vendor="NVIDIA Corporation"
[     3.846] (II) NVIDIA dlloader X Driver  390.12  Wed Dec 20 05:44:24 PST 2017
[     3.846] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[     3.846] (II) NOUVEAU driver for NVIDIA chipset families :
[     3.854] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
root@antic-Inspiron-7559:/home/antic# 

```

---

### Post by zeroth404 on 2018-01-13
I'm thinking I should just install a kernel that is known to support 384.

---

### Post by dorian7 on 2018-01-13
Not sure if you'll be able to downgrade just the kernel, since 17.10 was released with kernel 4.13.  You may have to install 16.04, and you can then upgrade the kernel up to at least 4.10, which does still work with Nvidia drivers up to nvidia-387.

---

### Post by zeroth404 on 2018-01-13
I installed a 4.12 kernel package. I tried the autoinstall of nvidia 384, still getting the same darn problem.

---

### Post by zeroth404 on 2018-01-13
I have tried kernel 4.10, 4.11, and 4.12 packages from the mainline ubuntu repo. They all boot, but the nvidia 384 driver  doesn't work with any of them.

I also tried nvidia 340 with kernel 4.10 just to see what would happen. lsmod still shows the driver loaded but it still isn't functioning.

---

### Post by dorian7 on 2018-01-13
Are you using the ACPI workaround?  You need to have your boot parameters include:  acpi_osi=! acpi_osi="Windows 2009"
Only then will it boot properly with the drivers installed.

EDIT : If you're on the 4.10 kernel, you can drop the ACPI parameters.  However, I needed to then add pcie_aspm=force to allow the system to conserve power usage and generate less heat.  More of an issue on laptops of course.

---

### Post by zeroth404 on 2018-01-15
I was just about to install a previous version of LUbuntu when I decided to try your last suggestion, dorian7. It was when I went in to grub to add the boot parameters you recommended when I noticed "nomodeset" was listed there. This was something I had to add in order for the LiveCD to not lock up during boot-up, but I didn't realize it saved the darn thing to the system during installation. From what I gather, nomodeset is only supposed to prevent the drivers from loading *before* X starts, but in this case it seems to have prevented the drivers from loading at all.

I removed nomodeset from my boot parameters, and (after `ubuntu-drivers autoinstall`) now I can run glx-gears. NVidia driver 384.111, kernel 4.13.0-250-generic, LUbuntu 17.10.

Thank you all for your support.

---

### Post by Bashing-om on 2018-01-15
zeroth404; Yuk, and great !

I called myself looking for that eventuality of "nomodeset" - do not know how I missed it .

Wonderful that you are up and running ..

Once we have  dorian7's closing remarks:

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]good things can happen
[/INDENT][/INDENT]

---

### Post by dorian7 on 2018-01-17
Sorry for holding up the close :)
Glad it got sorted!  Sometimes it ends up being something so simple lol
Bash on!

---

### Post by noabody2 on 2018-01-26
> **zeroth404 said:**
> It was when I went in to grub to add the boot parameters you recommended when I noticed "nomodeset" was listed there.
Same problem here.  Found "nouveau.runpm=0" let me boot the live CD and caused less trouble before I caught, and removed it, from the installed OS kernel option.

---

