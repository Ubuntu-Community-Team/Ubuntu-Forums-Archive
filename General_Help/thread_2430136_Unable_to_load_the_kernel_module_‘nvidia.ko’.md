---
title: "Unable to load the kernel module ‘nvidia.ko’"
date: 2019-10-28
forum: General Help
---

### Post by cdoublejj on 2019-10-28
LOG: [https://slexy.org/view/s2zkrYhJZh](https://slexy.org/view/s2zkrYhJZh)

Nvidia GRID K1 ; profile set for vm, k160q

Guest OS Lubuntu 18.04 LTS

After fighting the commands given in the instructions and installing some missing headers and packages (looks like geared for something like centos)
Looks like i nearly got it working but, last attempted with the log linked above. if it possible to even install 369 nvidia drivers on *buntu 18.04 based on commands for centos type distros would it even really work with out a ton of work around?


nvidia docs: [https://docs.nvidia.com/grid/latest/grid-vgpu-user-guide/index.html#installing-vgpu-drivers-linux](https://docs.nvidia.com/grid/latest/grid-vgpu-user-guide/index.html#installing-vgpu-drivers-linux)

my prior attempts: [https://forum.level1techs.com/t/unable-to-load-the-kernel-module-nvidia-ko/148983](https://forum.level1techs.com/t/unable-to-load-the-kernel-module-nvidia-ko/148983)

---

### Post by SeijiSensei on 2019-10-28
Are you trying to enable the NVIDIA module from within a virtual machine?  Since the VM doesn't see the actual hardware, this is often difficult if not impossible to do.

---

### Post by cdoublejj on 2019-10-31
> **SeijiSensei said:**
> Are you trying to enable the NVIDIA module from within a virtual machine?  Since the VM doesn't see the actual hardware, this is often difficult if not impossible to do.



all of the instructions i've seen show actually passing through a GPU. As such lspci and hardware profiler do see and list the GPU.

---

