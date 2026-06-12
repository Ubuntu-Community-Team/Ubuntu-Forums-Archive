---
title: "Not booting correctly into kernal 6.2.0.26"
date: 2023-08-06
forum: General Help
---

### Post by caterhamfan on 2023-08-06
Hey all,

So, I managed to get into my system and ran some updates.
Version 6.2.0.26 of the Linux kernel was installed. However, when booting into it, I see missing things like brightness control and no wifi option in the settings. I have to boot into an earlier kernel version.

Being able to boot is an improvement though because I couldn't do so until I turned on the graphics drivers in additional drivers. Could this be the cause? The nvidia-driver-525

Thank you,

---

### Post by MAFoElffen on 2023-08-06
Not having a problem with mine but I am running newer driver:
```

mafoelffen@msi-ubuntu:~$ nvidia-smi
Sun Aug  6 09:29:19 2023       
+---------------------------------------------------------------------------------------+
| NVIDIA-SMI 535.86.05              Driver Version: 535.86.05    CUDA Version: 12.2     |
|-----------------------------------------+----------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |         Memory-Usage | GPU-Util  Compute M. |
|                                         |                      |               MIG M. |
|=========================================+======================+======================|
|   0  NVIDIA GeForce GTX 1660 Ti     Off | 00000000:01:00.0  On |                  N/A |
|  0%   32C    P8               8W / 130W |     98MiB /  6144MiB |      3%      Default |
|                                         |                      |                  N/A |
+-----------------------------------------+----------------------+----------------------+
                                                                                         
+---------------------------------------------------------------------------------------+
| Processes:                                                                            |
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory |
|        ID   ID                                                             Usage      |
|=======================================================================================|
|    0   N/A  N/A      5571      G   /usr/lib/xorg/Xorg                           66MiB |
|    0   N/A  N/A      7545      G   /usr/bin/gnome-shell                         29MiB |
+---------------------------------------------------------------------------------------+

```

---

### Post by #&amp;thj^% on 2023-08-06
> **caterhamfan said:**
> Hey all,

So, I managed to get into my system and ran some updates.
Version 6.2.0.26 of the Linux kernel was installed. However, when booting into it, I see missing things like brightness control and no wifi option in the settings. I have to boot into an earlier kernel version.

Being able to boot is an improvement though because I couldn't do so until I turned on the graphics drivers in additional drivers. Could this be the cause? The nvidia-driver-525

Thank you,
> **MAFoElffen said:**
> Not having a problem with mine but I am running newer driver:
```

mafoelffen@msi-ubuntu:~$ nvidia-smi
Sun Aug  6 09:29:19 2023       
+---------------------------------------------------------------------------------------+
| NVIDIA-SMI 535.86.05              Driver Version: 535.86.05    CUDA Version: 12.2     |
|-----------------------------------------+----------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |         Memory-Usage | GPU-Util  Compute M. |
|                                         |                      |               MIG M. |
|=========================================+======================+======================|
|   0  NVIDIA GeForce GTX 1660 Ti     Off | 00000000:01:00.0  On |                  N/A |
|  0%   32C    P8               8W / 130W |     98MiB /  6144MiB |      3%      Default |
|                                         |                      |                  N/A |
+-----------------------------------------+----------------------+----------------------+
                                                                                         
+---------------------------------------------------------------------------------------+
| Processes:                                                                            |
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory |
|        ID   ID                                                             Usage      |
|=======================================================================================|
|    0   N/A  N/A      5571      G   /usr/lib/xorg/Xorg                           66MiB |
|    0   N/A  N/A      7545      G   /usr/bin/gnome-shell                         29MiB |
+---------------------------------------------------------------------------------------+

```

Same here:
```
Sun Aug  6 13:52:35 2023       
+---------------------------------------------------------------------------------------+
| NVIDIA-SMI 535.86.05              Driver Version: 535.86.05    CUDA Version: 12.2     |
|-----------------------------------------+----------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |         Memory-Usage | GPU-Util  Compute M. |
|                                         |                      |               MIG M. |
|=========================================+======================+======================|
|   0  NVIDIA GeForce GTX 1650 Ti     Off | 00000000:01:00.0  On |                  N/A |
| N/A   37C    P8               1W /  50W |    308MiB /  4096MiB |      5%      Default |
|                                         |                      |                  N/A |
+-----------------------------------------+----------------------+----------------------+
                                                                                         
+---------------------------------------------------------------------------------------+
| Processes:                                                                            |
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory |
|        ID   ID                                                             Usage      |
|=======================================================================================|
|    0   N/A  N/A      3831      G   /usr/lib/xorg/Xorg                          166MiB |
|    0   N/A  N/A      6113      G   xfwm4                                         2MiB |
|    0   N/A  N/A     13363      G   /usr/lib/firefox/firefox                    137MiB |
+---------------------------------------------------------------------------------------+

```
kernel: 
```
uname -r
6.2.0-26-generic

```

Can you show us this:
```
apt policy nvidia-dkms-525
```

---

### Post by caterhamfan on 2023-08-10
I think this could be the problem.

> nvidia-dkms-525:
  Installed: (none)
  Candidate: 525.125.06-0ubuntu0.22.04.1
  Version table:
     525.125.06-0ubuntu0.22.04.1 500
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy-updates/restricted amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security/restricted amd64 Packages
        100 /var/lib/dpkg/status

How can I force an update to the latest driver? 
Thank you

---

### Post by #&amp;thj^% on 2023-08-10
> **caterhamfan said:**
> I think this could be the problem.



How can I force an update to the latest driver? 
Thank you
Let's try a proper install, the whole package:
```
sudo apt install --reinstall nvidia-driver-525 nvidia-dkms-525
```
Now reboot after the drivers installs without any errors.

---

### Post by caterhamfan on 2023-08-10
Still not working after your suggestion, unable to see the wifi option or brightness settings. It's so strange. Can't think of what this could be.
Thanks

---

### Post by sitethief on 2023-08-11
I also had driver problems with NVIDIA and other hardware drivers in 6.2.0-26-generic, the workaround right now for me is to go back to an older kernel, in my case 5.19.0-50-generic.

---

### Post by #&amp;thj^% on 2023-08-11
> **sitethief said:**
> I also had driver problems with NVIDIA and other hardware drivers in 6.2.0-26-generic, the workaround right now for me is to go back to an older kernel, in my case 5.19.0-50-generic.
There was a kernel upgrade today to "6.2.0-27-generic" so it may be worth an update/upgrade
> **caterhamfan said:**
> Still not working after your suggestion, unable to see the wifi option or brightness settings. It's so strange. Can't think of what this could be.
Thanks
Not always but in most cases this caused by a bad first install method. and in your case here, i suggest purging all Nvidia related packages and start fresh:
```
sudo apt autoremove --purge nvidia*
```
Now a reboot for a fresh clean session and after longing in:
You may have some benefits for the 535 driver so in this case we go for that driver.
```
sudo apt install nvidia-driver-535 nvidia-dkms-535
```
And another reboot to see what the new driver brings to you.
FTR I never ever use the auto install method recommended by Canonical.
```
inxi -G | grep API && uname -r
  API: OpenGL v: 4.6.0 NVIDIA 535.86.05 renderer: NVIDIA GeForce GTX 1650
6.2.0-27-generic

```

---

### Post by caterhamfan on 2023-08-12
Still no luck when trying those steps, the trackpad also doesn't work also when booting into 6.2.0.
Thanks

---

### Post by #&amp;thj^% on 2023-08-13
> **caterhamfan said:**
> Still no luck when trying those steps, the trackpad also doesn't work also when booting into 6.2.0.
Thanks
My friend a bug needs to filed or join an already filed bug.
I just can not reproduce your results, even on kernel 6.3, everything goes as i would expect on my end.
```
Preparing to unpack .../linux-headers-linuxlite-6.3.0_0010_amd64.deb ...
Unpacking linux-headers-linuxlite-6.3.0 (0010) ...
Selecting previously unselected package linux-image-linuxlite-6.3.0.
Preparing to unpack .../linux-image-linuxlite-6.3.0_0010_amd64.deb ...
Unpacking linux-image-linuxlite-6.3.0 (0010) ...
Setting up linux-headers-linuxlite-6.3.0 (0010) ...
Setting up linux-image-linuxlite-6.3.0 (0010) ...
 * dkms: running auto installation service for kernel 6.3.0
Sign command: /usr/bin/kmodsign
Signing key: /var/lib/shim-signed/mok/MOK.priv
Public certificate (MOK): /var/lib/shim-signed/mok/MOK.der

Building module:
Cleaning build area...
'make' -j12 KVER=6.3.0 KSRC=/lib/modules/6.3.0/build..........
Signing module /var/lib/dkms/8812au/5.6.4.2_35491.20191025/build/88XXau.ko
Cleaning build area...

88XXau.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/6.3.0/updates/dkms/
depmod...
Sign command: /usr/bin/kmodsign
Signing key: /var/lib/shim-signed/mok/MOK.priv
Public certificate (MOK): /var/lib/shim-signed/mok/MOK.der

Building module:
Cleaning build area...
unset ARCH; [ ! -h /usr/bin/cc ] && export CC=/usr/bin/gcc; env NV_VERBOSE=1 'make' -j12 NV_EXCLUDE_BUILD_MODULES='' KERNEL_UNAME=6.3.0 IGNORE_XEN_PRESENCE=1 IGNORE_CC_MISMATCH=1 SYSSRC=/lib/modules/6.3.0/build LD=/usr/bin/ld.bfd CONFIG_X86_KERNEL_IBT= modules............
Signing module /var/lib/dkms/nvidia/535.86.05/build/nvidia.ko
Signing module /var/lib/dkms/nvidia/535.86.05/build/nvidia-modeset.ko
Signing module /var/lib/dkms/nvidia/535.86.05/build/nvidia-drm.ko
Signing module /var/lib/dkms/nvidia/535.86.05/build/nvidia-uvm.ko
Signing module /var/lib/dkms/nvidia/535.86.05/build/nvidia-peermem.ko
Cleaning build area...

nvidia.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/6.3.0/updates/dkms/

nvidia-modeset.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/6.3.0/updates/dkms/

nvidia-drm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/6.3.0/updates/dkms/

nvidia-uvm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/6.3.0/updates/dkms/

nvidia-peermem.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/6.3.0/updates/dkms/
depmod...
dkms autoinstall on 6.3.0/x86_64 succeeded for 8812au nvidia
   ...done.
update-initramfs: Generating /boot/initrd.img-6.3.0
I: The initramfs will attempt to resume from /dev/dm-2
I: (/dev/mapper/vglinux-swap_1)
I: Set the RESUME variable to override this.
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found background: /boot/grub_linux_lite.png
Found background image: /boot/grub_linux_lite.png
Found linux image: /boot/vmlinuz-6.3.0
Found initrd image: /boot/initrd.img-6.3.0
Found linux image: /boot/vmlinuz-6.2.0-27-generic
Found initrd image: /boot/initrd.img-6.2.0-27-generic
Found linux image: /boot/vmlinuz-6.2.0-26-generic
Found initrd image: /boot/initrd.img-6.2.0-26-generic
Found linux image: vmlinuz-6.3.0 in rpool/ROOT/ubuntu_d1lsb0
Found initrd image: initrd.img-6.3.0 in rpool/ROOT/ubuntu_d1lsb0
Found linux image: vmlinuz-6.2.0-27-generic in rpool/ROOT/ubuntu_d1lsb0
Found initrd image: initrd.img-6.2.0-27-generic in rpool/ROOT/ubuntu_d1lsb0
Found linux image: vmlinuz-6.2.0-26-generic in rpool/ROOT/ubuntu_d1lsb0
Found initrd image: initrd.img-6.2.0-26-generic in rpool/ROOT/ubuntu_d1lsb0
Found memtest86+ 64bit EFI image: /boot/memtest86+x64.efi
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
Adding boot menu entry for UEFI Firmware Settings ...
done
Scanning processes...                                                                   
Scanning processor microcode...                                                         
Scanning linux images...                                                                


```
My DKMS and Driver just works.
```
inxi -G | grep API && uname -a
  API: OpenGL v: 4.6.0 NVIDIA 535.86.05 renderer: NVIDIA GeForce GTX 1650
Linux me-Lenovo-Legion-5-15ARH05**[COLOR="#FF0000"] 6.3.0 #1 SMP PREEMPT_DYNAMIC[/COLOR]** Tue Apr 25 17:25:36 NZST 2023 x86_64 x86_64 x86_64 GNU/Linux

```
I would have to think a bug has already been filed but i have not looked yet.

---

