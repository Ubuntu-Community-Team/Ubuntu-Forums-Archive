---
title: "Integrated Intel graphics seem to cause random crashes"
date: 2018-12-27
forum: General Help
---

### Post by Superdude_123 on 2018-12-27
After plenty of digging around the forms and some trial and error, it seems that when I allow the kernel drivers for my integrated video card to load(the motherboard is a MSI Z170-A Pro with Intel Z170 Express Chipset - lshw -c display reports the HD Graphics 530 and currently unclaimed), my system becomes randomly unstable and will hang/crash/become unresponsive after finishing a boot.

To place a band aid on my solution, I've modified GRUB to be GRUB_CMDLINE_LINUX_DEFAULT="nomodeset acpi=force" as to disable the kernel video drivers, which by default, reverts Ubuntu 18.04 LTS (recently upgraded from 16 LTS with 4.4.0-21-generic which worked and didn't suffer these problems if I didn't upgrade the kernel) to use llvmpipe (LLVM 7.0, 256 bits) for the graphics driver.

While this band aid is a solution, is there a way to have stability and my Intel graphics at the same time? I was looking last night at the idea of installing and loading the Intel graphics in the OS instead of at the kernel, however, this doesn't seem to be the new norm with 18.04/17.10.

---

