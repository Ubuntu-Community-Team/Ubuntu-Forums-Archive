---
title: "Switch from amdgpu-pro to amdgpu buildin kernel"
date: 2023-08-04
forum: General Help
---

### Post by habernir on 2023-08-04
hello

recently i installed amdgpu-pro but after i uninstall amdgpu-pro its doesn't go to the buildin amgpu driver because i switch to amd from nvidia card before i install amdgpu-pro
soo 
what packages or configurations do i need to do to make amdgpu kernel driver work?

thanks nir

---

### Post by MAFoElffen on 2023-08-04
Try this: [https://ubuntuforums.org/showthread.php?t=2489555&p=14152990#post14152990](https://ubuntuforums.org/showthread.php?t=2489555&p=14152990#post14152990)

---

### Post by habernir on 2023-08-05
> **MAFoElffen said:**
> Try this: [https://ubuntuforums.org/showthread.php?t=2489555&p=14152990#post14152990](https://ubuntuforums.org/showthread.php?t=2489555&p=14152990#post14152990)

i tried but it doesn't load amgdpu, 
when i run 

lsmod | grep amdgpu

its return nothing.

---

### Post by QIII on 2023-08-05
Have you tried to load the module manually?

```
sudo modprobe amdgpu
```

---

### Post by habernir on 2023-08-05
yes.
do you know if their is a good explanation (or step by step) how to restore amdgpu kernel driver?

---

### Post by habernir on 2023-08-05
> **QIII said:**
> Have you tried to load the module manually?

```
sudo modprobe amdgpu
```

its works its return 

```
amdgpu               9867264  0iommu_v2               24576  1 amdgpu
gpu_sched              45056  1 amdgpu
drm_ttm_helper         16384  1 amdgpu
ttm                    86016  2 amdgpu,drm_ttm_helper
drm_kms_helper        311296  1 amdgpu
drm                   622592  5 gpu_sched,drm_kms_helper,amdgpu,drm_ttm_helper,ttm
i2c_algo_bit           16384  2 igb,amdgpu

```

the problem was that i have 7900 xtx and the kernels 5.19 and 5.15 create problems with this card soo i tried kernel 6.2.0 and everything works 
and i didn't use this line :

GRUB_CMDLINE_LINUX_DEFAULT="--- splash radeon.modeset=0 amdgpu.noretry=0 amdgpu.dc=1 video=uvesafb:1920x1080-32@60,mtrr:3,ywrap,noblank"

do i need to use all the parameters in this line ? 

but now the cursor disappear in xorg but not in wayland

---

### Post by MAFoElffen on 2023-08-06
RE: [https://ubuntuforums.org/showthread.php?t=2489555&p=14153392#post14153392](https://ubuntuforums.org/showthread.php?t=2489555&p=14153392#post14153392)
The "video=" parameter is optional. It helps to set the resolution early, before the amdgpu driver is loaded, so that it doesn't have a problem during console, splash, and the graphical logon (on some machines) The other do help it load.

---

