---
title: "Can't install Nvidia-glx-new"
date: 2007-10-24
forum: General Help
---

### Post by geovino on 2007-10-24
Since my upgrade to Gutsy I haven't been able to install the nvidia-glx-new drivers. Here's the error message:

E: /var/cache/apt/archives/nvidia-glx-new_100.14.19+2.6.22.4-14.9_i386.deb: subprocess pre-installation script returned error exit status 2

I can't install the nvidia-glx either. What is causing that it not to install?

---

### Post by Nunu on 2007-10-24
I am not a pro, but my question is do you have any Nvidia driver installed at the moment and can you uninstall them?

---

### Post by geovino on 2007-10-24
> **Nunu said:**
> I am not a pro, but my question is do you have any Nvidia driver installed at the moment and can you uninstall them?

No. When I go to Synaptic and search for nvidia-glx and nvidia-glx-new they are listed, but not installed.

---

### Post by steveneddy on 2007-10-24
Why don't you install them from Synaptic?

Just make sure that you uninstall the video driver you are using now at the same time, unless it is the Vesa driver.

If you are using the nv driver, uninstall that while installing the nvidia driver.

Make sure that you do

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

after that or edit the xorg.conf file yourself.

You will need to restart, also.

:popcorn:

---

### Post by geovino on 2007-10-24
I tried to install from Synaptic and that's when I get that error message. when I first did the upgrade to Gutsy it rebooted in a safe mode with a resolution of 600x800, but then I went to Screen and Graphics Preferences and selected the Nvidia Geforce 6 series and that gave me 1280x1024 and the screen looks good.  So what should I do at this point?

---

### Post by geovino on 2007-10-24
> **steveneddy said:**
> Why don't you install them from Synaptic?

Just make sure that you uninstall the video driver you are using now at the same time, unless it is the Vesa driver.

If you are using the nv driver, uninstall that while installing the nvidia driver.

Make sure that you do

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

after that or edit the xorg.conf file yourself.

You will need to restart, also.

:popcorn:

How do I know what video driver I have now?

---

