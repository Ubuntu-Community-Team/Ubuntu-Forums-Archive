---
title: "Ubuntu keeps freezing!"
date: 2014-11-08
forum: General Help
---

### Post by iSystem on 2014-11-08
My Ubuntu OS keeps freezing!


Here are some details:
[LIST]
[*]I just installed Ubuntu yesterday
[*]I have 512MB of RAM
[*]I am using the LXDE desktop
[*]Usually freezes when browsing the web (Chrorium and Firefox)
[*]Freezes in Unity
[*]Freezes in LXDE
[*]Freezes sometimes when installing applications
[/LIST]

I really want to find a way to fix this!

---

### Post by grahammechanical on 2014-11-08
Install more RAM!

512MB is the minimum requirement for Ubuntu. What CPU do you have? What graphic adapter do you have? How much of its own memory does the graphic card have? If the graphic card is using some of system memory (RAM) then there will be even less RAM available for the OS.

You should even consider using Xubuntu or Lubuntu instead of Ubuntu.

Is the graphic adapter able to run Unity? Is it able to do 3D hardware acceleration? Check System Settings>Details. If graphics is listed as llvmpipe, then there is a strong possibility that the graphic adapter is not capable of running Unity 3D. You may get better results with a proprietary video driver but I doubt that. Besides, the manufacturers of proprietary video drivers often drop support from their drivers for what they consider obsolete graphic adapters. The software centre may have an older proprietary video driver that will work. But Ubuntu only installs the latest proprietary video drivers during installation. If it cannot do that then it uses llvmpipe as a fallback.

Which version of Ubuntu did you install? There are three versions currently supported. It helps to know stuff like that. My point is this: If the CPU has to do video rendering of 3D graphics because the graphic adapter cannot do it, then the CPU is going to be over-worked when trying to download and install software. And something will have to give. Hence the apparent freeze.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Regards.

---

### Post by iSystem on 2014-11-08
> **grahammechanical said:**
> Install more RAM!

512MB is the minimum requirement for Ubuntu. What CPU do you have? What graphic adapter do you have? How much of its own memory does the graphic card have? If the graphic card is using some of system memory (RAM) then there will be even less RAM available for the OS.

You should even consider using Xubuntu or Lubuntu instead of Ubuntu.

Is the graphic adapter able to run Unity? Is it able to do 3D hardware acceleration? Check System Settings>Details. If graphics is listed as llvmpipe, then there is a strong possibility that the graphic adapter is not capable of running Unity 3D. You may get better results with a proprietary video driver but I doubt that. Besides, the manufacturers of proprietary video drivers often drop support from their drivers for what they consider obsolete graphic adapters. The software centre may have an older proprietary video driver that will work. But Ubuntu only installs the latest proprietary video drivers during installation. If it cannot do that then it uses llvmpipe as a fallback.

Which version of Ubuntu did you install? There are three versions currently supported. It helps to know stuff like that. My point is this: If the CPU has to do video rendering of 3D graphics because the graphic adapter cannot do it, then the CPU is going to be over-worked when trying to download and install software. And something will have to give. Hence the apparent freeze.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Regards.

I have ran Ubuntu before (with no problems). I recently just swithed back. My CPU is 4GHz. I am using Ubuntu 13.04 (fresh install, haven't had the chance to upgrade yet)

I use the lightweight desktop, LXDE, most of the time

---

