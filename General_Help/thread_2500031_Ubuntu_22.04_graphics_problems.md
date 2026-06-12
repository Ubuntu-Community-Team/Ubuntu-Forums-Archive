---
title: "Ubuntu 22.04 graphics problems"
date: 2024-08-19
forum: General Help
---

### Post by antonio715 on 2024-08-19
hi there,

three days ago i started my ubuntu 22.04 laptop and got a very awfull message: 
systemd-logind[762]: failed to idle channel 2 [systemd-logind[762]]
after restarting i got to enter but since then i have many graphics problems: the screen blinks, something like interferences, one second, sometimes almost shut down the image
i tried to update the nvidia driver to 550 but the problem continues
it happens many times when the mouse is near the border of the screen (botton or right usually)

does someone know something about this problem?

Thanks  in advance and sorry for my horrible english

Ps: under Windows i have not problems... only Ubuntu

---

### Post by Bashing-om on 2024-08-19
Hello antonio715 -

Supposing this is a graphic's driver issue -
Show us what we are working with; post back the result of terminal command:
```

sudo lshw -C display

```

[INDENT]see where we go from here
[/INDENT]

---

### Post by ReFranz on 2024-08-19
Clicked on wrong thread. My apologies.

---

### Post by antonio715 on 2024-08-20
Hi Bashing-om,
here is the report:
*-display                 
       descripción: VGA compatible controller
       producto: UHD Graphics 620
       fabricante: Intel Corporation
       id físico: 2
       información del bus: pci@0000:00:02.0
       nombre lógico: /dev/fb0
       versión: 07
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pciexpress msi pm vga_controller bus_master cap_list rom fb
       configuración: depth=32 driver=i915 latency=0 resolution=1366,768
       recursos: irq:139 memoria:b2000000-b2ffffff memoria:c0000000-cfffffff ioport:5000(size=64) memoria:c0000-dffff
  *-display NO RECLAMADO
       descripción: 3D controller
       producto: GP108M [GeForce MX150]
       fabricante: NVIDIA Corporation
       id físico: 0
       información del bus: pci@0000:01:00.0
       versión: a1
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress bus_master cap_list
       configuración: latency=0
       recursos: memoria:b3000000-b3ffffff memoria:a0000000-afffffff memoria:b0000000-b1ffffff ioport:4000(size=128)

in spanish sorry
Thanks

Ps: do you think it is a hardware problem?

---

### Post by Bashing-om on 2024-08-20
Well antonio715 -

There is no driver loaded for the Nvidia card -
Before we try to install a driver best see what the current Nvidia driver states are.
Code tags!
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
makes output so much more readable.

Now show us the output of terminal command:
```

dpkg -l | grep -i nvidia

```

Where I can confirm the 550 version driver is recommended - I bet that there is a bit of cleanup to do first.

[INDENT]we can do that
[/INDENT]

---

### Post by antonio715 on 2024-08-21
Hi Bashing-om,

here is the code (i hope it will be shown properly):

```

ii  libnvidia-cfg1-550:amd64                   550.107.02-0ubuntu0~gpu22.04.1                    amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-550                       550.107.02-0ubuntu0~gpu22.04.1                    all          Shared files used by the NVIDIA libraries
rc  libnvidia-compute-535:amd64                535.183.01-0ubuntu0.22.04.1                       amd64        NVIDIA libcompute package
ii  libnvidia-compute-550:amd64                550.107.02-0ubuntu0~gpu22.04.1                    amd64        NVIDIA libcompute package
ii  libnvidia-compute-550:i386                 550.107.02-0ubuntu0~gpu22.04.1                    i386         NVIDIA libcompute package
ii  libnvidia-decode-550:amd64                 550.107.02-0ubuntu0~gpu22.04.1                    amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-550:i386                  550.107.02-0ubuntu0~gpu22.04.1                    i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-egl-wayland1:amd64               1:1.1.9-1.1                                       amd64        Wayland EGL External Platform library -- shared library
ii  libnvidia-egl-wayland1:i386                1:1.1.9-1.1                                       i386         Wayland EGL External Platform library -- shared library
ii  libnvidia-encode-550:amd64                 550.107.02-0ubuntu0~gpu22.04.1                    amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-550:i386                  550.107.02-0ubuntu0~gpu22.04.1                    i386         NVENC Video Encoding runtime library
ii  libnvidia-extra-550:amd64                  550.107.02-0ubuntu0~gpu22.04.1                    amd64        Extra libraries for the NVIDIA driver
ii  libnvidia-fbc1-550:amd64                   550.107.02-0ubuntu0~gpu22.04.1                    amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-550:i386                    550.107.02-0ubuntu0~gpu22.04.1                    i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-550:amd64                     550.107.02-0ubuntu0~gpu22.04.1                    amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-550:i386                      550.107.02-0ubuntu0~gpu22.04.1                    i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
rc  linux-modules-nvidia-535-6.8.0-40-generic  6.8.0-40.40~22.04.3                               amd64        Linux kernel nvidia modules for version 6.8.0-40
ii  linux-modules-nvidia-550-6.8.0-40-generic  6.8.0-40.40~22.04.3                               amd64        Linux kernel nvidia modules for version 6.8.0-40
ii  linux-modules-nvidia-550-generic-hwe-22.04 6.8.0-40.40~22.04.3                               amd64        Extra drivers for nvidia-550 for the generic-hwe-22.04 flavour
ii  linux-objects-nvidia-535-6.8.0-40-generic  6.8.0-40.40~22.04.3                               amd64        Linux kernel nvidia modules for version 6.8.0-40 (objects)
ii  linux-objects-nvidia-550-6.8.0-40-generic  6.8.0-40.40~22.04.3                               amd64        Linux kernel nvidia modules for version 6.8.0-40 (objects)
ii  linux-signatures-nvidia-6.8.0-40-generic   6.8.0-40.40~22.04.3                               amd64        Linux kernel signatures for nvidia modules for version 6.8.0-40-generic
rc  nvidia-compute-utils-535                   535.183.01-0ubuntu0.22.04.1                       amd64        NVIDIA compute utilities
ii  nvidia-compute-utils-550                   550.107.02-0ubuntu0~gpu22.04.1                    amd64        NVIDIA compute utilities
ii  nvidia-dkms-550                            550.107.02-0ubuntu0~gpu22.04.1                    amd64        NVIDIA DKMS package
ii  nvidia-driver-550                          550.107.02-0ubuntu0~gpu22.04.1                    amd64        NVIDIA driver metapackage
ii  nvidia-firmware-550-550.107.02             550.107.02-0ubuntu0~gpu22.04.1                    amd64        Firmware files used by the kernel module
rc  nvidia-kernel-common-535                   535.183.01-0ubuntu0.22.04.1                       amd64        Shared files used with the kernel module
ii  nvidia-kernel-common-550                   550.107.02-0ubuntu0~gpu22.04.1                    amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-550                   550.107.02-0ubuntu0~gpu22.04.1                    amd64        NVIDIA kernel source package
ii  nvidia-prime                               0.8.17.1                                          all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                            510.47.03-0ubuntu1                                amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-550                           550.107.02-0ubuntu0~gpu22.04.1                    amd64        NVIDIA driver support binaries
ii  screen-resolution-extra                    0.18.2                                            all          Extension for the nvidia-settings control panel
ii  xserver-xorg-video-nvidia-550              550.107.02-0ubuntu0~gpu22.04.1                    amd64        NVIDIA binary Xorg driver

```

thanks

---

### Post by Bashing-om on 2024-08-21
antonio715 - looks proper
Can not say why the 550 driver fails to load - however
Let's try again from the top -
as the proprietary driver is 3rd party disable Secure Boot in your Bios
next run terminal commands:
```

sudo apt update
sydo apt upgrade
sudo apt remove --purge nvidia*
sudo ubuntu-drivers autoinstall

```

Reboot to see the effect.

If all good now - you may re-enable Secure Boot.

[INDENT]all good now[/INDENT]

---

### Post by antonio715 on 2024-08-22
hi Bashing-om,

i followed your instructions but the same problem
now it is installed nvidia-driver-555 instead 550 [IMG]https://ibb.co/P48nfMx[/IMG]
before reboot i was request for a password saying after reboot i will need it but i did not


after reboot i had to select [IMG]https://ubuntuforums.org/attachment.php?attachmentid=294112&stc=1[/IMG]
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294111&stc=1[/IMG]
may i did something wrong...
i did not understand "e-enable Secure Boot"...

thanks in advance

---

### Post by nicolasdentremont on 2024-08-22
Normally you make a password before rebooting and at that screen you go to Enroll MOK and enter the password there.

---

### Post by antonio715 on 2024-08-23
hi there,

i removed and reinstalled again such i did before

sudo apt update
sudo apt upgrade
sudo apt remove --purge nvidia*
sudo ubuntu-drivers autoinstall

and after reboot i chose Enroll MOK
but then i had to chose
 
view key 0
continue

choosing view key 0 i got another blue screen with a lot of things i dont understand but anyway i could not continue
back the menu and choosing continue i got another screen that i do not remember and another one and so on... 
in one moment i got a screen where i had to enter a password (aleluya) but my password doesnt match!!!
at the end i had to go back and re-star usually...

what can i do now??

Thanks in advance

---

