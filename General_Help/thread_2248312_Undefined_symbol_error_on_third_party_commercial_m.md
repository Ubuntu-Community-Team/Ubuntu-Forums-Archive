---
title: "Undefined symbol error on third party commercial maya plugin"
date: 2014-10-14
forum: General Help
---

### Post by akimb0 on 2014-10-14
Hello,

im want to try out a commercial third party autodesk maya 2014/2015 plugin from here [http://sigrasoft.com/packages/WaxLab3dv1_Maya2013-2015_Linux-x64_Install.tar.gz](http://sigrasoft.com/packages/WaxLab3dv1_Maya2013-2015_Linux-x64_Install.tar.gz)

We was on a business trip these days and checked out the plugin already on our laptop running ubuntu 14.04, which runs smoothly.
Back at the office we installed this to our workstation which also runs ubuntu 14.04 and the plugin fails to load.
The main differences between the laptop and the workstation is the graphics where we are running on intel HD4000 on the laptop and on a brandnew NVIDIA K6000 on the workstation

We are not able to load the plugin on the workstation because of the following erros messages:
maya 2014
```
undefined symbol: GSS_C_NT_HOSTBASED_SERVICE
```

We menawhile migrated to maya 2015 finally, but the error still remains in a different flavour:
maya 2015
```
undefined symbol: SSLv2_client_method
```

We already compared the libraries with a quick ldd and the differences are the following:

These libs are present on both machines (laptop and workstation) but are only loaded on the laptop:
```

libglapi.so.0 => /usr/lib/x86_64-linux-gnu/libglapi.so.0 (0x00007fa6f8fb9000)
libXdamage.so.1 => /usr/lib/x86_64-linux-gnu/libXdamage.so.1 (0x00007fa6f8ba4000)
libXfixes.so.3 => /usr/lib/x86_64-linux-gnu/libXfixes.so.3 (0x00007fa6f899d000)
libX11-xcb.so.1 => /usr/lib/x86_64-linux-gnu/libX11-xcb.so.1 (0x00007fa6f879b000)
libxcb-glx.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-glx.so.0 (0x00007fa6f824e000)
libxcb-dri2.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-dri2.so.0 (0x00007fa6f8049000)
libxcb-dri3.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-dri3.so.0 (0x00007fa6f7e46000)
libxcb-present.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-present.so.0 (0x00007fa6f7c42000)
libxcb-sync.so.1 => /usr/lib/x86_64-linux-gnu/libxcb-sync.so.1 (0x00007fa6f7a3c000)
libxshmfence.so.1 => /usr/lib/x86_64-linux-gnu/libxshmfence.so.1 (0x00007fa6f761a000)
libXxf86vm.so.1 => /usr/lib/x86_64-linux-gnu/libXxf86vm.so.1 (0x00007fa6f7414000)
libdrm.so.2 => /usr/lib/x86_64-linux-gnu/libdrm.so.2 (0x00007fa6f7208000)
```

These nvidia libs are only loaded on the workstation and not on the laptop:
```
libnvidia-tls.so.340.46 => /usr/lib/nvidia-340/tls/libnvidia-tls.so.340.46 (0x00007fa40c1db000)
libnvidia-glcore.so.340.46 => /usr/lib/nvidia-340/libnvidia-glcore.so.340.46 (0x00007fa4095c7000)
```

Additionally the workstation uses libGL depending to the nvidia version where the laptop uses included libGL:
```
libGL.so.1 => /usr/lib/nvidia-340/libGL.so.1 (0x00007fa411a7a000)
```
```
libGL.so.1 => /usr/lib/x86_64-linux-gnu/libGL.so.1 (0x00007fa6fe87e000)
```

We are totally out of an idea what could cause this issue on the workstation where the laptop runs it smoothly.
Any help would be much appreciated.

---

### Post by akimb0 on 2014-10-17
Noone an idea about this issue?
I tried now several nvidia installation including the official nvidia installers without any luck. We start to going crazy on this, if this would not run on the ubuntu laptop i would say there is a library issue, but it runs very smooth on the laptop and not on the workstation, so there must be a reason why.

---

