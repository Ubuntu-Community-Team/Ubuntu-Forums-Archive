---
title: "Screen Tearing when Scrolling AMD RX480 Ubuntu 16.04LTS"
date: 2016-09-02
forum: General Help
---

### Post by magicman1223 on 2016-09-02
Since I installed my RX480 I have noticed screen tearing when scrolling webpages or doing much of anything. I have loaded the AMD drivers and below is output from lspci and a few other commands. Is there anything else I can do to resolve this? Anyone else noticing this issue?

Thanks!

lsmod |grep amdgpu
amdgpu               1949696  6
i2c_algo_bit           16384  1 amdgpu
ttm                    94208  1 amdgpu
drm_kms_helper        147456  1 amdgpu
drm                   364544  9 ttm,drm_kms_helper,amdgpu



USER@USER:~$ sudo lshw -C display
[sudo] password for USER: 
  *-display               
       description: VGA compatible controller
       product: Advanced Micro Devices, Inc. [AMD/ATI]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: c7
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=amdgpu latency=0
       resources: irq:46 memory:c0000000-cfffffff memory:d0000000-d01fffff ioport:e000(size=256) memory:fea00000-fea3ffff memory:fea40000-fea5ffff


 uname -a
Linux USERPC 4.4.0-36-generic #55-Ubuntu SMP Thu Aug 11 18:01:55 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

lsb_release -r
Release:	16.04

---

### Post by cking-x on 2016-09-17
For me I had to enable the glx backend in compton instead of the default

---

