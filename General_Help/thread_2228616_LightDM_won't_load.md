---
title: "LightDM won't load"
date: 2014-06-08
forum: General Help
---

### Post by larzeb on 2014-06-08
I removed an ATI video card and replaced it with a Nvidia. I cannot get X to start as a result.

The system is Linux ubuntu 3.5.0-51-generic #77~precise1-Ubuntu SMP Thu Jun 5 00:48:28 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

First I did:
```
[COLOR=#333333][FONT=Monaco]sudo apt-get purge nvidia*; sudo apt-get install nvidia-331-updates-dev[/FONT][/COLOR]
```
I downloaded NVIDIA-Linux-x86_64-331.79.run and executed it. I accepted the scripts offer to include DKMS into the kernel and no 32-bit drivers.
Any ideas on how I might try to correct this?
Now I've got the following messages:
```
 
From /var/log/Xorg.0.log
   NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
   NVIDIA(0):     system's kernel log for additional error messages and
   NVIDIA(0):     consult the NVIDIA README for details.
   NVIDIA(0):  *** Aborting ***
   NVIDIA(0): Failing initialization of X screen 0
   UnloadModule: "nvidia"
   UnloadSubModule: "wfb"
   UnloadSubModule: "fb"
   Screen(s) found, but none have a usable configuration.
   no screens found


From /var/log/kern.log:
   NVRM: API mismatch: the client has the version 331.79, but
   NVRM: this kernel module has the version 331.38.  Please
   NVRM: make sure that this kernel module and all NVIDIA driver
   NVRM: components have the same version.
   NVRM: nvidia_frontend_ioctl: minor 255, module->ioctl failed, error -22
   NVRM: API mismatch: the client has the version 331.79, but
   NVRM: this kernel module has the version 331.38.  Please
   NVRM: make sure that this kernel module and all NVIDIA driver
   NVRM: components have the same version.
   NVRM: nvidia_frontend_ioctl: minor 255, module->ioctl failed, error -22


From lshw -C display
  *-display UNCLAIMED
       description: Display controller
       product: Rage XL PCI
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 27
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=32 mingnt=8
       resources: memory:fc000000-fcffffff ioport:ac00(size=256) memory:fdfff000-fdffffff memory:fea00000-fea1ffff
  *-display
       description: VGA compatible controller
       product: GF119 [GeForce GT 520]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:18 memory:fa000000-faffffff memory:c8000000-cfffffff memory:d6000000-d7ffffff ioport:6c00(size=128) memory:d0000000-d007ffff
```

---

