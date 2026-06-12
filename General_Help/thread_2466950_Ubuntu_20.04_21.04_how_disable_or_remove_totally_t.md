---
title: "Ubuntu 20.04 21.04 how disable or remove totally the nvidia nouveau driver ?"
date: 2021-09-11
forum: General Help
---

### Post by aug7744 on 2021-09-11
I want to unninstal the nouveau driver before of install nvidia binary or proprietary driver.

How disable or remove totally (kernel driver and other files) the nouveau driver ?

Thanks for reply.

---

### Post by Autodave on 2021-09-11
I would think that if you could remove the nouveau driver, then you would not have any way (no screen to see) to install a new driver.  And you really want to use the driver from Linux, not from nVidia.

---

### Post by aug7744 on 2021-09-14
Installing the OS using nouveau.modeset=0 look how if nouveau not will be installed in OS instead another driver.
I had installed in 18.04.5 using nouveau.modeset=0 and nouveau not was installed.

---

### Post by yaminb on 2021-09-14
Can I ask why you want to remove the nouveau driver?

I've occasionally had the Nvidia drivers fail on update or fresh install and it's good to have the nouveau drivers to at least have something.
If you're worried about conflicting drivers... I've actually had some problems with the Nvidia provided drivers and those tend to be solve by purging and reinstalling the Nvidia drivers
sudo apt-get remove --purge nvidia-*

---

### Post by monkeybrain20122 on 2021-09-14
Why would you need to do that? If you install the Nvidia driver properly nouveau would be disabled (if you install a .deb). It is only necessary to mess with nouveau if you plan to install the Nvidia driver with the .run file which is not recommended.

---

### Post by monkeybrain20122 on 2021-09-14
> **aug7744 said:**
> Installing the OS using nouveau.modeset=0 look how if nouveau not will be installed in OS instead another driver.
I had installed in 18.04.5 using nouveau.modeset=0 and nouveau not was installed.

So you have no graphic before you install the Nvidia driver. Why?

---

### Post by The Cog on 2021-09-14
I could be wrong, but I suspect that setting modeset=0 does not disable the driver, but simply changes how the OS changes video modes, for instance when switching between TTY and graphical modes.
Using lsmod will show you which modules are loaded - it would be interesting to see if nouveau is listed after that modeset=0 intallation.

Once a good nvidia driver is installed, the it takes priority over the nouveau driver anyway, so I see no need to remove the driver.
If you really want to go ahead anyway, you can add nouveau to modprobe.d/blacklist.conf. But be ready to have no display after reboot.

---

### Post by grahammechanical on 2021-09-14
The Motherboard BIOS/UEFI sets a video mode otherwise we would not see a splash screen or other information or be able to see the BIOS/UEFI settings utility when we load it.

Grub also sets a video mode which is in operation when the Grub boot menu appears on the screen. The same video mode is used as the Linux kernel loads all kinds of modules. At one point in the loading process the video driver, be it open source of proprietary, takes over and the size and style of the Linux messages alters.

It is my guess that this Grub video mode is the mode being used when we load a recovery mode kernel and it continues to be used when we select Resume. It is only on a reboot that the video driver is loaded. It is my guess that it is this video mode we will be running under if we remove Nouveau and do not have a proprietary video driver activated.

Regards

---

