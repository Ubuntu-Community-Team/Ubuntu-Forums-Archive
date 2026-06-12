---
title: "screen flickers a misaligned launcher bar"
date: 2023-08-07
forum: General Help
---

### Post by pcdangio on 2023-08-07
I'm running a fresh install of Ubuntu 22.04 with an NVIDIA RTX 3060, using the proprietary NVIDIA driver (535). For some reason, I get periodic screen flickers where the launcher bar briefly appears in the center of my screen. I've attached a screenshot to show the behavior. I've tried using the nouveau driver as well, and the same problem occurs. Any idea what could be causing this? I don't have any xorg.conf files under /etc/X11. Thanks so much!

---

### Post by pcdangio on 2023-08-12
Anybody have any ideas? Thanks!

---

### Post by MAFoElffen on 2023-08-12
Using nvidia-smi, which version of nvidia-driver-535? (Format 535.XX.XX)
```

mafoelffen@msi-ubuntu:~$ nvidia-smi
Sat Aug 12 13:54:39 2023       
+---------------------------------------------------------------------------------------+
| NVIDIA-SMI 535.86.05              Driver Version: 535.86.05    CUDA Version: 12.2     |
|-----------------------------------------+----------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |         Memory-Usage | GPU-Util  Compute M. |
|                                         |                      |               MIG M. |
|=========================================+======================+======================|
|   0  NVIDIA GeForce GTX 1660 Ti     Off | 00000000:01:00.0  On |                  N/A |
|  0%   36C    P8               8W / 130W |     99MiB /  6144MiB |      2%      Default |
|                                         |                      |                  N/A |
+-----------------------------------------+----------------------+----------------------+
                                                                                         
+---------------------------------------------------------------------------------------+
| Processes:                                                                            |
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory |
|        ID   ID                                                             Usage      |
|=======================================================================================|
|    0   N/A  N/A      5571      G   /usr/lib/xorg/Xorg                           66MiB |
|    0   N/A  N/A      7545      G   /usr/bin/gnome-shell                         31MiB |
+---------------------------------------------------------------------------------------+

mafoelffen@msi-ubuntu:~$ sudo systool -vm nvidia_drm
Module = "nvidia_drm"

  Attributes:
    coresize            = "90112"
    initsize            = "0"
    initstate           = "live"
    refcnt              = "4"
    srcversion          = "703E141D70BD62EC6798912"
    taint               = "POE"
    uevent              = <store method only>
    version             = "535.86.05"

  Parameters:
    modeset             = "Y"

  Sections:
    .altinstr_replacement= "0xffffffffc05cf79f"
    .altinstructions    = "0xffffffffc05d0058"
    .bss                = "0xffffffffc05d6800"
    .call_sites         = "0xffffffffc05d2f90"
    .data.once          = "0xffffffffc05d6460"
    .data               = "0xffffffffc05d5580"
    .exit.data          = "0xffffffffc05d6458"
    .exit.text          = "0xffffffffc05cf780"
    .gnu.linkonce.this_module= "0xffffffffc05d6480"
    .init.data          = "0xffffffffc0423000"
    .init.text          = "0xffffffffc0422000"
    .note.Linux         = "0xffffffffc05d0024"
    .note.gnu.build-id  = "0xffffffffc05d0000"
    .retpoline_sites    = "0xffffffffc05d3c28"
    .return_sites       = "0xffffffffc05d2c64"
    .rodata             = "0xffffffffc05d0080"
    .rodata.str1.1      = "0xffffffffc05d0950"
    .rodata.str1.8      = "0xffffffffc05d0be8"
    .smp_locks          = "0xffffffffc05d3bac"
    .static_call_sites  = "0xffffffffc05d644f"
    .strtab             = "0xffffffffc0427450"
    .symtab             = "0xffffffffc0424000"
    .text               = "0xffffffffc05c6000"
    .text.unlikely      = "0xffffffffc05cf2e7"
    __bug_table         = "0xffffffffc05d5000"
    __jump_table        = "0xffffffffc05d4000"
    __mcount_loc        = "0xffffffffc05d283c"
    __param             = "0xffffffffc05d3d38"
    __patchable_function_entries= "0xffffffffc05d5120"


```
For some people, add boot parameter "nvidia_drm.modeset=1" helped them, but with more recent nvidia drivers, that no longer works.

---

