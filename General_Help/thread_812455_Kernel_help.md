---
title: "Kernel help"
date: 2008-05-29
forum: General Help
---

### Post by dansued on 2008-05-29
Currently in the process of installing nvidia drivers from the nvidia site.

As quoted from the readme..

> 
The NVIDIA kernel module has a kernel interface layer that must be compiled specifically for each kernel. NVIDIA distributes the source code to this kernel interface layer, as well as precompiled versions for many of the kernels provided by popular Linux distributions.
 When the installer is run, it will determine if it has a precompiled kernel interface for the kernel you are running. If it does not have one, it will check if there is one on the NVIDIA FTP site (assuming you have an Internet connection), and download it. If one cannot be downloaded, either because the FTP site cannot be reached or because one is not provided, the installer will check your system for the required kernel sources and compile the interface for you. You must have the source code for your kernel installed for compilation to work. On most systems, this means that you will need to locate and install the correct kernel-source, kernel-headers, or kernel-devel package; on some distributions, no additional packages are required (e.g. Fedora Core 3, Red Hat Enterprise Linux 4).
 After the correct kernel interface has been identified (either included in the .run file, downloaded, or compiled from source code), the kernel interface will be linked with the closed-source portion of the NVIDIA kernel module. This requires that you have a linker installed on your system. The linker, usually /usr/bin/ld, is part of the binutils package. You must have a linker installed prior to installing the NVIDIA driver.this would be fine except my ethernet card does not work. I have acess to other windows running boxes that can access the internet. Is there any way I can download the kernel from another computer and transfer it over?



What suggestions do you guys have?

thanks!

---

### Post by RAOF on 2008-05-29
There are a variety of options.  However, first it's probably a better idea to work out whether this is worth the effort :).  *Why* are you installing the nvidia drivers from the nvidia site?  Unless the Ubuntu packaged drivers (169.12, the release before the new 172 drivers released in the last couple of days) don't support your card, it will be *much* less effort to use those.

---

### Post by dansued on 2008-05-30
the X server doesn't start. when I dpkg-reconfigure, I pick nv from the drivers list, and leave everything else on default. when I restart gdm, it doesn't work. The log just says no devices detected and no screens detected.

This is on a feisty fawn installation as that's the only cd I have and the box I'm using doesn't have a working ethernet card

---

