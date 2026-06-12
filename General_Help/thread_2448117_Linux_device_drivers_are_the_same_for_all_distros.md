---
title: "Linux device drivers are the same for all distros ?"
date: 2020-08-02
forum: General Help
---

### Post by aug7744 on 2020-08-02
Linux device drivers are the same for all distros or need to download the version to each distro ?

---

### Post by CelticWarrior on 2020-08-02
Typically the same but different distros can use different drivers or different versions of the same driver.

As you already know, different distros may use different package managers (software installers) and some drivers may come packaged for a specific family of distros and not others, thus requiring different installation methods.

---

### Post by aug7744 on 2020-08-02
I see my video card installed in Lubuntu displaying geforce nouveau driver.
I had started an console emulator (Nestopia) and not was possible change to full screen thus I think nouveau driver not is exactly the driver to use.
I have downloaded the proprietary nvidia driver that I will try to install.

---

### Post by Autodave on 2020-08-02
That is usually not a good idea.  Go into Settings -> Additional Drivers and see what one is recommended.

---

### Post by grahammechanical on 2020-08-02
Nouveau is the open source video driver for Nvidia graphic cards. When we install Ubuntu or one of its flavours the installer will ask us if we want to install non-free or proprietary software at the same time. If we chose to do that the installer will download an appropriate video driver and an assortment of audio and video codecs which are free to download and use but not open source.

If our video card is old or very new the open source driver might be all we get.

Drivers for other devices come with the Linux kernel and are called Linux Firmware. This why it is best to install the latest distributions of Linux if we have the latest hardware. Older distributions may not have the hardware drivers.

My video card is so old that the newest Nvidia drivers do not support it. Which is a reason for only installing video drivers using Software & Updates>Additional Drivers tab. It will search the internet for proprietary video drivers that support your graphic card. Installing the latest driver from the Nvidia website might give you a system with no video capability.

If you wish to experiment you should at least become familiar with the Ubuntu Recovery mode that is accessed under Advanced options for Ubuntu from the Grub menu. You may need to do some command line repair to remove the proprietary video driver.

Regards.

---

### Post by HermanAB on 2020-08-02
Before I futz with a video driver, I always make sure that opensshd is running and that I can log in over the net from another machine.  That way, when the video driver is bad, causing a black screen, I can recover using ssh from the other machine.

---

### Post by SeijiSensei on 2020-08-02
The vast majority of drivers are packaged with the Linux kernel. Different distributions may use different kernel versions, but it's rare for them to have drivers unique to a particular distribution.

---

### Post by TheFu on 2020-08-02
> **aug7744 said:**
> Linux device drivers are the same for all distros or need to download the version to each distro ?

You shouldn't download drivers directly 99.9999% of the time. Use the package management system.
How to property install the video driver you want is answered in another thread.
```
sudo ubuntu-drivers autoinstall
```
should work. There's a GUI for it somewhere ... "Additional Drivers".
Or if those don't work, 
```
sudo apt install  nvidia-driver-390
```

Doing through the package manager will ensure you get updates as suggested.  Doing it manually will ensure you do not get updates.

---

### Post by aug7744 on 2020-08-13
Thanks for all replies.

---

