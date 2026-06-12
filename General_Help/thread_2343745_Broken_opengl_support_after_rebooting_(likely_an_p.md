---
title: "Broken opengl support after rebooting (likely an package update broke it)"
date: 2016-11-18
forum: General Help
---

### Post by egandt on 2016-11-18
This use to work on this system, as I was using kodi and it ran fine.  Now I can not start anything that requires opengl:

kodi@fileserver:~/Desktop$ glxinfo
name of display: :0.0
[B]libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast[/B]
X Error of failed request:  GLXBadContext
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  6 (X_GLXIsDirect)
  Serial number of failed request:  59
  Current serial number in output stream:  58


```
root@fileserver:~# apt-get install nvidia-367 nvidia-settings
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-settings is already the newest version (361.42-0ubuntu1).
nvidia-settings set to manually installed.
nvidia-367 is already the newest version (367.57-0ubuntu0.16.04.1).
nvidia-367 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.


root@fileserver:/etc/modprobe.d# dpkg-reconfigure nvidia-367
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-367
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
Loading new nvidia-367-367.57 DKMS files...
Building only for 4.4.0-47-generic
Building for architecture x86_64
Building initial module for 4.4.0-47-generic
Done.

nvidia_367:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.4.0-47-generic/updates/dkms/

nvidia_367_modeset.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.4.0-47-generic/updates/dkms/

nvidia_367_drm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.4.0-47-generic/updates/dkms/

nvidia_367_uvm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.4.0-47-generic/updates/dkms/

depmod....

DKMS: install completed.
Processing triggers for initramfs-tools (0.122ubuntu8.5) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-47-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.

root@fileserver:~# lspci | grep NVIDIA 
02:00.0 VGA compatible controller: NVIDIA Corporation GM206 [GeForce GTX 960] (rev a1)
02:00.1 Audio device: NVIDIA Corporation Device 0fba (rev a1)
root@fileserver:~# lsmod | grep nvidia
nvidia_uvm            745472  0
nvidia_drm             45056  3
nvidia_modeset        765952  3 nvidia_drm
drm_kms_helper        155648  2 i915,nvidia_drm
nvidia              11489280  51 nvidia_modeset,nvidia_uvm
drm                   364544  7 i915,drm_kms_helper,nvidia_drm

root@fileserver:/raid6/public/WORKSTATION/btdownloads# find / -name *swrast*
/usr/lib/x86_64-linux-gnu/dri/kms_swrast_dri.so
/usr/lib/x86_64-linux-gnu/dri/swrast_dri.so
/usr/lib/i386-linux-gnu/dri/kms_swrast_dri.so
/usr/lib/i386-linux-gnu/dri/swrast_dri.so

```

So it is safe to say that the Nvidia driver 367-57 is install and is configured (I rebooted after running dpkg-reconfigure).


Next I tried:

```
root@fileserver:/raid6/public/WORKSTATION/btdownloads# export LIBGL_DEBUG=verbose
root@fileserver:/raid6/public/WORKSTATION/btdownloads# glxinfo 
name of display: :0.0
libGL: screen 0 does not appear to be DRI2 capable
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/swrast_dri.so
libGL: Can't open configuration file /root/.drirc: No such file or directory.
libGL: Can't open configuration file /root/.drirc: No such file or directory.
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
libGL: screen 1 does not appear to be DRI2 capable
[B]libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/swrast_dri.so
libGL: Can't open configuration file /root/.drirc: No such file or directory.
libGL: Can't open configuration file /root/.drirc: No such file or directory.
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast[/B]
X Error of failed request:  GLXBadContext
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  6 (X_GLXIsDirect)
  Serial number of failed request:  59
  Current serial number in output stream:  58

root@fileserver:/raid6/public/WORKSTATION/btdownloads# ldd /usr/bin/glxgears
	linux-vdso.so.1 =>  (0x00007ffc541d6000)
	**libGL.so.1 => /usr/lib/x86_64-linux-gnu/mesa/libGL.so.1 (0x00007f2e6a3a1000)**
	libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007f2e6a098000)
	libX11.so.6 => /usr/lib/x86_64-linux-gnu/libX11.so.6 (0x00007f2e69d5d000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f2e69994000)
	libexpat.so.1 => /lib/x86_64-linux-gnu/libexpat.so.1 (0x00007f2e6976b000)
	libxcb-dri3.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-dri3.so.0 (0x00007f2e69567000)
	libxcb-present.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-present.so.0 (0x00007f2e69364000)
	libxcb-sync.so.1 => /usr/lib/x86_64-linux-gnu/libxcb-sync.so.1 (0x00007f2e6915d000)
	libxshmfence.so.1 => /usr/lib/x86_64-linux-gnu/libxshmfence.so.1 (0x00007f2e68f59000)
	libglapi.so.0 => /usr/lib/x86_64-linux-gnu/libglapi.so.0 (0x00007f2e68d2b000)
	libXext.so.6 => /usr/lib/x86_64-linux-gnu/libXext.so.6 (0x00007f2e68b19000)
	libXdamage.so.1 => /usr/lib/x86_64-linux-gnu/libXdamage.so.1 (0x00007f2e68915000)
	libXfixes.so.3 => /usr/lib/x86_64-linux-gnu/libXfixes.so.3 (0x00007f2e6870f000)
	libX11-xcb.so.1 => /usr/lib/x86_64-linux-gnu/libX11-xcb.so.1 (0x00007f2e6850d000)
	libxcb-glx.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-glx.so.0 (0x00007f2e682f3000)
	libxcb-dri2.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-dri2.so.0 (0x00007f2e680ee000)
	libxcb.so.1 => /usr/lib/x86_64-linux-gnu/libxcb.so.1 (0x00007f2e67ecc000)
	libXxf86vm.so.1 => /usr/lib/x86_64-linux-gnu/libXxf86vm.so.1 (0x00007f2e67cc5000)
	libdrm.so.2 => /usr/lib/x86_64-linux-gnu/libdrm.so.2 (0x00007f2e67ab6000)
	libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f2e67899000)
	libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f2e67694000)
	/lib64/ld-linux-x86-64.so.2 (0x0000557ed4a90000)
	libXau.so.6 => /usr/lib/x86_64-linux-gnu/libXau.so.6 (0x00007f2e67490000)
	libXdmcp.so.6 => /usr/lib/x86_64-linux-gnu/libXdmcp.so.6 (0x00007f2e67289000)

root@fileserver:~# ldd /usr/bin/glxinfo
        linux-vdso.so.1 =>  (0x00007ffdcf7d0000)
        **libGL.so.1 => /usr/lib/x86_64-linux-gnu/mesa/libGL.so.1 (0x00007fdaefc91000)**
        libX11.so.6 => /usr/lib/x86_64-linux-gnu/libX11.so.6 (0x00007fdaef957000)
        libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fdaef58d000)
        libexpat.so.1 => /lib/x86_64-linux-gnu/libexpat.so.1 (0x00007fdaef364000)
        libxcb-dri3.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-dri3.so.0 (0x00007fdaef161000)
        libxcb-present.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-present.so.0 (0x00007fdaeef5d000)
        libxcb-sync.so.1 => /usr/lib/x86_64-linux-gnu/libxcb-sync.so.1 (0x00007fdaeed56000)
        libxshmfence.so.1 => /usr/lib/x86_64-linux-gnu/libxshmfence.so.1 (0x00007fdaeeb53000)
        libglapi.so.0 => /usr/lib/x86_64-linux-gnu/libglapi.so.0 (0x00007fdaee924000)
        libXext.so.6 => /usr/lib/x86_64-linux-gnu/libXext.so.6 (0x00007fdaee712000)
        libXdamage.so.1 => /usr/lib/x86_64-linux-gnu/libXdamage.so.1 (0x00007fdaee50f000)
        libXfixes.so.3 => /usr/lib/x86_64-linux-gnu/libXfixes.so.3 (0x00007fdaee308000)
        libX11-xcb.so.1 => /usr/lib/x86_64-linux-gnu/libX11-xcb.so.1 (0x00007fdaee106000)
        libxcb-glx.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-glx.so.0 (0x00007fdaedeed000)
        libxcb-dri2.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-dri2.so.0 (0x00007fdaedce7000)
        libxcb.so.1 => /usr/lib/x86_64-linux-gnu/libxcb.so.1 (0x00007fdaedac5000)
        libXxf86vm.so.1 => /usr/lib/x86_64-linux-gnu/libXxf86vm.so.1 (0x00007fdaed8bf000)
        libdrm.so.2 => /usr/lib/x86_64-linux-gnu/libdrm.so.2 (0x00007fdaed6af000)
        libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007fdaed3a6000)
        libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007fdaed189000)
        libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007fdaecf84000)
        /lib64/ld-linux-x86-64.so.2 (0x000056388326e000)
        libXau.so.6 => /usr/lib/x86_64-linux-gnu/libXau.so.6 (0x00007fdaecd80000)
        libXdmcp.so.6 => /usr/lib/x86_64-linux-gnu/libXdmcp.so.6 (0x00007fdaecb79000)


```


My best guess is that it is the fact that it is trying to use the mesa driver and not the nvidia opengl driver that is the cause:

```
root@fileserver:/etc/modprobe.d# find /usr -iname "*libGL.so*" -exec ls -l {} \; 
-rw-r--r-- 1 root root 439972 Oct  3 22:59 /usr/lib32/nvidia-367/libGL.so.1.0.0
**lrwxrwxrwx 1 root root 10 Oct 25 13:57 /usr/lib32/nvidia-367/libGL.so -> libGL.so.1**
lrwxrwxrwx 1 root root 14 Oct 25 13:57 /usr/lib32/nvidia-367/libGL.so.1 -> libGL.so.1.0.0
-rw-r--r-- 1 root root 459392 Aug 11 18:49 /usr/lib/x86_64-linux-gnu/mesa/libGL.so.1.2.0
lrwxrwxrwx 1 root root 14 Aug 11 18:49 /usr/lib/x86_64-linux-gnu/mesa/libGL.so -> libGL.so.1.2.0
**lrwxrwxrwx 1 root root 14 Aug 11 18:49 /usr/lib/x86_64-linux-gnu/mesa/libGL.so.1 -> libGL.so.1.2.0**
lrwxrwxrwx 1 root root 13 Aug 11 18:49 /usr/lib/x86_64-linux-gnu/libGL.so -> mesa/libGL.so
-rw-r--r-- 1 root root 579760 Oct  3 23:26 /usr/lib/nvidia-367/libGL.so.1.0.0
**lrwxrwxrwx 1 root root 10 Oct 25 13:57 /usr/lib/nvidia-367/libGL.so -> libGL.so.1**
lrwxrwxrwx 1 root root 14 Oct 25 13:57 /usr/lib/nvidia-367/libGL.so.1 -> libGL.so.1.0.0
```


The question is how do I fix this issue correctly and cleanly, as it should be using that from: /usr/lib/nvidia-367/libGL.so.1 and not /usr/lib/x86_64-linux-gnu/mesa/libGL.so.1 if I'm correct.  I'm just not sure why the MESA driver is being used first, or how to select the nvidia driver cleanly in a way that does not break other things.

Thanks,
ERIC

---

### Post by wildmanne39 on 2016-11-18
*Thread moved to **General Help**.*

---

### Post by &amp;KyT$0P# on 2016-11-18
I had the inverse of this same problem with the Nvidia 367 driver.  Solution is to change the update-alternatives for [FONT=Courier New]x86_64-linux-gnu_egl_conf[/FONT] and [FONT=Courier New]x86_64-linux-gnu_gl_conf[/FONT] (and the i386 equivalents, if they exist and the proper option is there).  And then reboot.

Unfortunately, I don't remember exactly how to do this by command-line.  See [FONT=Courier New]man update-alternatives[/FONT], I believe it's the [FONT=Courier New]--config[/FONT] option we want here.

---

### Post by egandt on 2016-11-18
Found and resolved the problem, when the driver was updated from 361 to 367, it did not update:

/etc/ld.so.conf.d/nvidia.conf
/usr/lib/nvidia-36**1**
/usr/lib32/nvidia-36**1**
/usr/lib/x86_64-linux-gnu/mesa
/usr/lib/x86_64-linux-gnu/mesa-egl
/usr/lib/i386-linux-gnu/mesa
/usr/lib/i386-linux-gnu/mesa-egl

I had to manually edit it to read:
/usr/lib/nvidia-36**7**
/usr/lib32/nvidia-36**7**
/usr/lib/x86_64-linux-gnu/mesa
/usr/lib/x86_64-linux-gnu/mesa-egl
/usr/lib/i386-linux-gnu/mesa
/usr/lib/i386-linux-gnu/mesa-egl


Seems like a possible bug in the driver package as this should have been done when changing versions.

---

### Post by oldrocker99 on 2016-11-19
Since your problem is solved, please use the Thread Tools to mark it as [SOLVED].

Nice job fixing your problem, too.

---

