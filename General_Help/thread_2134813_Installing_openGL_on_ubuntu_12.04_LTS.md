---
title: "Installing openGL on ubuntu 12.04 LTS"
date: 2013-04-12
forum: General Help
---

### Post by Raafat1991 on 2013-04-12
Hi guys...please how can i install openGL on ubuntu 12.04 LTS ?


thank you .

---

### Post by Impavidus on 2013-04-12
OpenGL should be installed by default. If you need development versions of the libraries with the header files, for compiling your own stuff, install packages like freeglut3-dev, libgl1-mesa-dev or libglfw-dev, depending on what you need exactly. They will pull in some dependencies

---

### Post by Raafat1991 on 2013-04-12
> **Impavidus said:**
> OpenGL should be installed by default. If you need development versions of the libraries with the header files, for compiling your own stuff, install packages like freeglut3-dev, libgl1-mesa-dev or libglfw-dev, depending on what you need exactly. They will pull in some dependencies


So what i can't run stellarium on my ubuntu machine ?

Stellarium told me your system does not support opengl !

---

### Post by 3rdalbum on 2013-04-12
> **Raafat1991 said:**
> So what i can't run stellarium on my ubuntu machine ?

Stellarium told me your system does not support opengl !

What's your graphics card? If it's an ATI Radeon HD 2000-series or higher, or any Nvidia graphics card, you need to install the AMD/ATI driver from the Additional Drivers program.

If it's an ATI Radeon but not a Radeon HD, you're out of luck, sorry. Those cards only work with the default open-source driver, which might not do 3D very well.

If it's Intel graphics, I'd be surprised if you were getting an error message like that, as the open-source drivers for Intel cards support 3D and OpenGL.

If it's anything else, like VIA or SiS graphics, sorry; you've got a lemon. You can't use 3D on Linux with those graphics cards.

---

### Post by Raafat1991 on 2013-04-13
> **3rdalbum said:**
> What's your graphics card?


Look to this :

```
lspci | grep VGA

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF119 [GeForce GT 520MX] (rev a1)


```

---

### Post by Raafat1991 on 2013-04-16
Hi,i'm here...

---

### Post by CatKiller on 2013-04-16
If that's an Optimus setup, you'll need to use Bumblebee.

---

### Post by Raafat1991 on 2013-04-16
> **CatKiller said:**
> If that's an Optimus setup, you'll need to use Bumblebee.

Please more explanation...

---

### Post by papibe on 2013-04-16
Take a look at this wiki: [Bumblebee]("https://wiki.ubuntu.com/Bumblebee").

Regards.

---

### Post by 3rdalbum on 2013-04-16
Bumblebee only helps to switch GPUs. The OP needs to install the Nvidia driver, and optionally Bumblebee.

---

### Post by Raafat1991 on 2013-04-20
> **CatKiller said:**
> If that's an Optimus setup, you'll need to use Bumblebee.


Thank you man your suggestion was helpful...

---

### Post by Raafat1991 on 2013-04-20
> **CatKiller said:**
> If that's an Optimus setup, you'll need to use Bumblebee.

Thank you man your suggestion was helpful...

---

### Post by Raafat1991 on 2013-04-20
Thank you every one posted here any thing for helping me...thank you guys.

---

