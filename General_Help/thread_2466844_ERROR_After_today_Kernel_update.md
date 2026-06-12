---
title: "ERROR After today Kernel update"
date: 2021-09-07
forum: General Help
---

### Post by waffen on 2021-09-07
Hello,

My System:
Ubuntu 20.04 + Nvidia GT710, today I made an update, the normal one from the system (but today with a Kernel update), in the middle the system freeze and I need to reset the PC.

When I try to start using the latest kernel: 5.11.0-34 Im getting the next black screen at the start:

[https://cloud.lacunza.biz/index.php/s/PzRjyERsCBK5Xi6]("https://cloud.lacunza.biz/index.php/s/PzRjyERsCBK5Xi6")

If a try recovery mode Im getting stuck in this step:

[https://cloud.lacunza.biz/index.php/s/rrTrXGFTC4SAosL]("https://cloud.lacunza.biz/index.php/s/rrTrXGFTC4SAosL")

I can start the PC using the 5.11.0-27 previous kernel. Any idea how to fix it? 

Thanks!

---

### Post by Impavidus on 2021-09-08
Use the old kernel until this has been fixed.

Something went wrong during installation of the new kernel. The package is probably not completely installed. Try to fix that:```
sudo apt install -f
```
If that doesn't fix it, show the complete output of that command.

---

### Post by waffen on 2021-09-08
> **Impavidus said:**
> Use the old kernel until this has been fixed.

Something went wrong during installation of the new kernel. The package is probably not completely installed. Try to fix that:```
sudo apt install -f
```
If that doesn't fix it, show the complete output of that command.

The problem is: If a run with the xxx.34 kernel the PC freeze...  so I don't have the option to open a terminal, ctrl+alt+Fx  don't work too... 

Loading the xxx.27 kernel, all is fine, I just run that command no errors reported.

---

### Post by Impavidus on 2021-09-09
So, did it fix the issue?

---

### Post by waffen on 2021-09-09
> **Impavidus said:**
> So, did it fix the issue?

No, loading kernel xxx.34 keep freezing the PC, is there any way to recompile the kernel or another fix?

---

### Post by Impavidus on 2021-09-09
So, let's see what's installed exactly.```
dpkg --list "linux-*"
```
That should tell us if it's properly installed. If it is already, maybe reinstalling works. If that doesn't work, this could very well be a bug.

---

### Post by monkeybrain20122 on 2021-09-09
Boot into the previous kernel, from the old kernel delete the new one and don't upgrade the kernel until there is a fix (or you can temporarily [pin the version]("https://askubuntu.com/questions/999529/pin-kernel-version") and remove the pin when a fix is released) There are multiple reports of it causing problems, for example, [this]("https://ubuntuforums.org/showthread.php?t=2466903").

---

### Post by waffen on 2021-09-09
> **Impavidus said:**
> So, let's see what's installed exactly.```
dpkg --list "linux-*"
```
That should tell us if it's properly installed. If it is already, maybe reinstalling works. If that doesn't work, this could very well be a bug.

Here's the result:

```
Deseado=desconocido(U)/Instalar/eliminaR/Purgar/retener(H)
| Estado=No/Inst/ficheros-Conf/desempaqUetado/medio-conF/medio-inst(H)/espera-disparo(W)/pendienTe-disparo
|/ Err?=(ninguno)/requiere-Reinst (Estado,Err: mayúsc.=malo)
||/ Nombre                                     Versión                Arquitectura Descripción
+++-==========================================-======================-============-=================================================================================
ii  linux-base                                 4.5ubuntu3.6           all          Linux image base package
un  linux-doc                                  <ninguna>              <ninguna>    (no hay ninguna descripción disponible)
ii  linux-firmware                             1.187.16               all          Firmware for Linux kernel drivers
un  linux-firmware-raspi2                      <ninguna>              <ninguna>    (no hay ninguna descripción disponible)
un  linux-firmware-snapdragon                  <ninguna>              <ninguna>    (no hay ninguna descripción disponible)
ii  linux-generic-hwe-20.04                    5.11.0.34.36~20.04.13  amd64        Complete Generic Linux kernel and headers
un  linux-headers                              <ninguna>              <ninguna>    (no hay ninguna descripción disponible)
un  linux-headers-3.0                          <ninguna>              <ninguna>    (no hay ninguna descripción disponible)
un  linux-headers-5.11.0-25-generic            <ninguna>              <ninguna>    (no hay ninguna descripción disponible)
ii  linux-headers-5.11.0-27-generic            5.11.0-27.29~20.04.1   amd64        Linux kernel headers for version 5.11.0 on 64 bit x86 SMP
ii  linux-headers-5.11.0-34-generic            5.11.0-34.36~20.04.1   amd64        Linux kernel headers for version 5.11.0 on 64 bit x86 SMP
un  linux-headers-5.4.0-42-generic             <ninguna>              <ninguna>    (no hay ninguna descripción disponible)
un  linux-headers-5.8.0-59-generic             <ninguna>              <ninguna>    (no hay ninguna descripción disponible)
un  linux-headers-5.8.0-63-generic             <ninguna>              <ninguna>    (no hay ninguna descripción disponible)
un  linux-headers-686-pae                      <ninguna>              <ninguna>    (no hay ninguna descripción disponible)
un  linux-headers-amd64                        <ninguna>              <ninguna>    (no hay ninguna descripción disponible)
un  linux-headers-generic                      <ninguna>              <ninguna>    (no hay ninguna descripción disponible)
ii  linux-headers-generic-hwe-20.04            5.11.0.34.36~20.04.13  amd64        Generic Linux kernel headers
ii  linux-hwe-5.11-headers-5.11.0-27           5.11.0-27.29~20.04.1   all          Header files related to Linux kernel version 5.11.0
ii  linux-hwe-5.11-headers-5.11.0-34           5.11.0-34.36~20.04.1   all          Header files related to Linux kernel version 5.11.0
un  linux-hwe-5.11-source-5.11.0               <ninguna>              <ninguna>    (no hay ninguna descripción disponible)
un  linux-hwe-5.11-tools                       <ninguna>              <ninguna>    (no hay ninguna descripción disponible)
un  linux-hwe-5.8-source-5.8.0                 <ninguna>              <ninguna>    (no hay ninguna descripción disponible)
un  linux-hwe-5.8-tools                        <ninguna>              <ninguna>    (no hay ninguna descripción disponible)
un  linux-image                                <ninguna>              <ninguna>    (no hay ninguna descripción disponible)
rc  linux-image-5.11.0-25-generic              5.11.0-25.27~20.04.1   amd64        Signed kernel image generic
ii  linux-image-5.11.0-27-generic              5.11.0-27.29~20.04.1   amd64        Signed kernel image generic
ii  linux-image-5.11.0-34-generic              5.11.0-34.36~20.04.1   amd64        Signed kernel image generic
rc  linux-image-5.4.0-42-generic               5.4.0-42.46            amd64        Signed kernel image generic
rc  linux-image-5.8.0-59-generic               5.8.0-59.66~20.04.1    amd64        Signed kernel image generic
rc  linux-image-5.8.0-63-generic               5.8.0-63.71~20.04.1    amd64        Signed kernel image generic
ii  linux-image-generic-hwe-20.04              5.11.0.34.36~20.04.13  amd64        Generic Linux kernel image
un  linux-image-unsigned-5.11.0-25-generic     <ninguna>              <ninguna>    (no hay ninguna descripción disponible)
un  linux-image-unsigned-5.11.0-27-generic     <ninguna>              <ninguna>    (no hay ninguna descripción disponible)
un  linux-image-unsigned-5.11.0-34-generic     <ninguna>              <ninguna>    (no hay ninguna descripción disponible)
un  linux-image-unsigned-5.4.0-42-generic      <ninguna>              <ninguna>    (no hay ninguna descripción disponible)
un  linux-image-unsigned-5.8.0-59-generic      <ninguna>              <ninguna>    (no hay ninguna descripción disponible)
un  linux-image-unsigned-5.8.0-63-generic      <ninguna>              <ninguna>    (no hay ninguna descripción disponible)
un  linux-initramfs-tool                       <ninguna>              <ninguna>    (no hay ninguna descripción disponible)
rc  linux-image-5.4.0-42-generic               5.4.0-42.46            amd64        Signed kernel image generic
rc  linux-image-5.8.0-59-generic               5.8.0-59.66~20.04.1    amd64        Signed kernel image generic
rc  linux-image-5.8.0-63-generic               5.8.0-63.71~20.04.1    amd64        Signed kernel image generic
ii  linux-image-generic-hwe-20.04              5.11.0.34.36~20.04.13  amd64        Generic Linux kernel image
un  linux-image-unsigned-5.11.0-25-generic     <ninguna>              <ninguna>    (no hay ninguna descripción disponible)
un  linux-image-unsigned-5.11.0-27-generic     <ninguna>              <ninguna>    (no hay ninguna descripción disponible)
un  linux-image-unsigned-5.11.0-34-generic     <ninguna>              <ninguna>    (no hay ninguna descripción disponible)
un  linux-image-unsigned-5.4.0-42-generic      <ninguna>              <ninguna>    (no hay ninguna descripción disponible)
un  linux-image-unsigned-5.8.0-59-generic      <ninguna>              <ninguna>    (no hay ninguna descripción disponible)
un  linux-image-unsigned-5.8.0-63-generic      <ninguna>              <ninguna>    (no hay ninguna descripción disponible)
un  linux-initramfs-tool                       <ninguna>              <ninguna>    (no hay ninguna descripción disponible)
un  linux-kernel-headers                       <ninguna>              <ninguna>    (no hay ninguna descripción disponible)
un  linux-kernel-log-daemon                    <ninguna>              <ninguna>    (no hay ninguna descripción disponible)
ii  linux-libc-dev:amd64                       5.4.0-84.94            amd64        Linux Kernel Headers for development
rc  linux-modules-5.11.0-25-generic            5.11.0-25.27~20.04.1   amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
ii  linux-modules-5.11.0-27-generic            5.11.0-27.29~20.04.1   amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
ii  linux-modules-5.11.0-34-generic            5.11.0-34.36~20.04.1   amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-42-generic             5.4.0-42.46            amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.8.0-59-generic             5.8.0-59.66~20.04.1    amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
rc  linux-modules-5.8.0-63-generic             5.8.0-63.71~20.04.1    amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.11.0-25-generic      5.11.0-25.27~20.04.1   amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.11.0-27-generic      5.11.0-27.29~20.04.1   amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.11.0-34-generic      5.11.0-34.36~20.04.1   amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-42-generic       5.4.0-42.46            amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.8.0-59-generic       5.8.0-59.66~20.04.1    amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.8.0-63-generic       5.8.0-63.71~20.04.1    amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
rc  linux-modules-nvidia-465-5.8.0-59-generic  5.8.0-59.66~20.04.1    amd64        Linux kernel nvidia modules for version 5.8.0-59
ii  linux-modules-nvidia-465-generic-hwe-20.04 5.11.0-34.36~20.04.1   amd64        Extra drivers for nvidia-465 for the generic flavour (dummy transitional package)
rc  linux-modules-nvidia-470-5.11.0-25-generic 5.11.0-25.27~20.04.1+3 amd64        Linux kernel nvidia modules for version 5.11.0-25
ii  linux-modules-nvidia-470-5.11.0-27-generic 5.11.0-27.29~20.04.1   amd64        Linux kernel nvidia modules for version 5.11.0-27
rc  linux-modules-nvidia-470-5.8.0-63-generic  5.8.0-63.71~20.04.1    amd64        Linux kernel nvidia modules for version 5.8.0-63
ii  linux-modules-nvidia-470-generic-hwe-20.04 5.11.0-27.29~20.04.1   amd64        Extra drivers for nvidia-470 for the generic-hwe-20.04 flavour
rc  linux-objects-nvidia-465-5.8.0-59-generic  5.8.0-59.66~20.04.1    amd64        Linux kernel nvidia modules for version 5.8.0-59 (objects)
rc  linux-objects-nvidia-470-5.11.0-25-generic 5.11.0-25.27~20.04.1+3 amd64        Linux kernel nvidia modules for version 5.11.0-25 (objects)
ii  linux-objects-nvidia-470-5.11.0-27-generic 5.11.0-27.29~20.04.1   amd64        Linux kernel nvidia modules for version 5.11.0-27 (objects)
rc  linux-objects-nvidia-470-5.8.0-63-generic  5.8.0-63.71~20.04.1    amd64        Linux kernel nvidia modules for version 5.8.0-63 (objects)
un  linux-restricted-common                    <ninguna>              <ninguna>    (no hay ninguna descripción disponible)
un  linux-signatures-nvidia-5.11.0-25-generic  <ninguna>              <ninguna>    (no hay ninguna descripción disponible)
ii  linux-signatures-nvidia-5.11.0-27-generic  5.11.0-27.29~20.04.1   amd64        Linux kernel signatures for nvidia modules for version 5.11.0-27-generic
un  linux-signatures-nvidia-5.8.0-59-generic   <ninguna>              <ninguna>    (no hay ninguna descripción disponible)
un  linux-signatures-nvidia-5.8.0-63-generic   <ninguna>              <ninguna>    (no hay ninguna descripción disponible)
ii  linux-sound-base                           1.0.25+dfsg-0ubuntu5   all          base package for ALSA and OSS sound systems
un  linux-source-5.4.0                         <ninguna>              <ninguna>    (no hay ninguna descripción disponible)
un  linux-tools                                <ninguna>              <ninguna>    (no hay ninguna descripción disponible)

```

---

### Post by waffen on 2021-09-09
> **monkeybrain20122 said:**
> Boot into the previous kernel, from the old kernel delete the new one and don't upgrade the kernel until there is a fix (or you can temporarily [pin the version]("https://askubuntu.com/questions/999529/pin-kernel-version") and remove the pin when a fix is released) There are multiple reports of it causing problems, for example, [this]("https://ubuntuforums.org/showthread.php?t=2466903").

I think the error could be the Nvidia drivers.... like in that post. Reading my info posted here in previous message I can see some missing Nvidia files...

---

### Post by monkeybrain20122 on 2021-09-09
> **waffen said:**
> I think the error could be the Nvidia drivers.... like in that post. Reading my info posted here in previous message I can see some missing Nvidia files...

If it works on the old kernel then it is the culprit is the defective new kernel.  The missing Nvidia files are linux-signatures-nvidia *** I don't think they are the cause since I have never installed these packages anyway and have no issue (Nvidia gtx1070) In synaptic it says "you likely don't want to install this package directly" and you already have linux extra modules for 5.11.0-34 installed from your output.

It is your choice, but instead of tearing your hair out the easy way is to just use the old kernel until this is fixed (like I said there are multiple reports that 5.11.0-34 is bugged, and it doesn't affect only Nvidia machines, I lost touchpad function on an Intel machine and there are several similar threads)

---

### Post by waffen on 2021-09-09
> **monkeybrain20122 said:**
> If it works on the old kernel then it is the culprit is the defective new kernel.  The missing Nvidia files are linux-signatures-nvidia *** I don't think they are the cause since I have never installed these packages anyway and have no issue (Nvidia gtx1070) In synaptic it says "you likely don't want to install this package directly" and you already have linux extra modules for 5.11.0-34 installed from your output.

It is your choice, but instead of tearing your hair out the easy way is to just use the old kernel until this is fixed (like I said there are multiple reports that 5.11.0-34 is bugged, and it doesn't affect only Nvidia machines, I lost touchpad function on an Intel machine and there are several similar threads)

I just get a new update, and after force an update where I see 21 nvidia related packages the kernel xxx-34 it's working for me now, hope this helps and thanks to all for your answers!!

---

### Post by Impavidus on 2021-09-10
Indeed, some of the nvidia driver packages were not upgraded as the package manager hadn't seen the available upgrades. They are now in the repositories and your package manager picked them up and installed them.

If everything is OK now, you can mark this thread as solved. Tread tools (near top of page) &#8594; mark as solved.

---

