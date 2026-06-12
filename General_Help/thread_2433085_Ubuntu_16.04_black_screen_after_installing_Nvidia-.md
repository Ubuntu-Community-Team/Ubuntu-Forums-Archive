---
title: "Ubuntu 16.04 black screen after installing Nvidia-430"
date: 2019-12-13
forum: General Help
---

### Post by mtbdrew on 2019-12-13
Nvidia-418 installs and works fine but nvidia-430 always leads to black screen no matter how I try to install it.

 lsmod | grep nvidia
nvidia_uvm            819200  0
nvidia              19046400  169 nvidia_uvm
ipmi_msghandler        53248  2 ipmi_devintf,nvidia
frontend@frontend:~$ dpkg -l | grep -i nvidia
ii  bbswitch-dkms                               0.8-3ubuntu1                                    amd64        Interface for toggling the power on NVIDIA Optimus video cards
ii  libcuda1-430                                430.64-0ubuntu0~gpu16.04.2                      amd64        NVIDIA CUDA runtime library
rc  nvidia-418                                  418.56-0ubuntu0~gpu16.04.1                      amd64        NVIDIA binary driver - version 418.56
ii  nvidia-430                                  430.64-0ubuntu0~gpu16.04.2                      amd64        NVIDIA binary driver - version 430.64
rc  nvidia-opencl-icd-418                       418.56-0ubuntu0~gpu16.04.1                      amd64        NVIDIA OpenCL ICD
ii  nvidia-opencl-icd-430                       430.64-0ubuntu0~gpu16.04.2                      amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                0.8.2                                           amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                             418.56-0ubuntu0~gpu16.04.1                      amd64        Tool for configuring the NVIDIA graphics driver
frontend@frontend:~$ cat /var/log/gpu-manager.log
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-fglrx-was-loaded file
Looking for fglrx modules in /lib/modules/4.15.0-72-generic/updates/dkms
Looking for nvidia modules in /lib/modules/4.15.0-72-generic/updates/dkms
Found nvidia module: nvidia.ko
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
Is nouveau loaded? no
Is nouveau blacklisted? no
Is fglrx kernel module available? no
Is nvidia kernel module available? yes
Vendor/Device Id: 8086:22b1
BusID "PCI:0@0:2:0"
Is boot vga? no
Vendor/Device Id: 10de:1284
BusID "PCI:2@0:0:0"
Is boot vga? yes
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card0", driven by "i915"
Found "/dev/dri/card0", driven by "i915"
Number of connected outputs for /dev/dri/card0: 0
Does it require offloading? no
last cards number = 2
Has amd? no
Has intel? yes
Has nvidia? yes
How many cards? 2
Has the system changed? No
main_arch_path x86_64-linux-gnu, other_arch_path i386-linux-gnu
Current alternative: /usr/lib/nvidia-430/ld.so.conf
Current core alternative: (null)
Current egl alternative: /usr/lib/nvidia-430/ld.so.conf
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
frontend@frontend:~$ sudo dkms status
bbswitch, 0.8, 4.15.0-72-generic, x86_64: installedError! Could not locate dkms.conf file.
File:  does not exist.

frontend@frontend:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-4.15.0-72-generic root=UUID=89ea4739-64a1-4200-9626-c597e9d5a485 ro quiet splash vt.handoff=7
frontend@frontend:~$

---

### Post by mtbdrew on 2019-12-15
Any ideas why this is happening?

---

### Post by Skaperen on 2019-12-15
can you describe the hardware this was run on?  can you try 18.04?

---

