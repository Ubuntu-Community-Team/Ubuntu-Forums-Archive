---
title: "problems blacklisting nvidia_drm and nvidia_uvm, 16.04 edition"
date: 2016-11-10
forum: General Help
---

### Post by davidv1992 on 2016-11-10
I have an asus N751JK laptop with nvidia optimus hardware, and am currently in the process of upgrading to xubuntu 16.04.

Part of this process is setting up optimus again. For this i currently have installed the packages bumblebee, bumblebee-nvidia and nvidia-367 and all their dependencies. As part of this process, a known issue to me was that the nvidia drivers are usually loaded at boot, and that xorg does not deal well with that. When the drivers are loaded, xorg tries to use the nvidia card as output graphics card, which goes wrong as it doesnt have any screens (those are connected to the intel graphics card).

On 14.04 it was relatively easy to do this, simply blacklisting the modules nvidia-367, nvidia-367-drm and nvidia-367-uvm, as well as stopping the persistence daemon from running.

However, on 16.04, I have done this, and the modules still load. In detail, i have modified the following:
Added blacklist entries for the modules nvidia-367, nvidia-367-drm and nvidia-367-uvm in /etc/modprobe.d/
Ran systemctl mask nvidia-persistenced
Moved /usr/lib/nvidia-367/bin/nvidia-persistenced to a backup location and replaced it with a symlink to /bin/false

Unfortunately, something is still loading the nvidia-367-drm module at some point during boot (for reference, a boot log is here: [http://paste2.org/WLXK6GtJ](http://paste2.org/WLXK6GtJ)).

Does anyone have suggestions as to what more I can try? Or as to what might still be forcing the load of that module?

---

### Post by #&amp;thj^% on 2016-11-10
It's seems there was a bit of discussion on this here: [https://github.com/Bumblebee-Project/Bumblebee/issues/759](https://github.com/Bumblebee-Project/Bumblebee/issues/759)

I use a dedicated card my self so not much help from me..sorry.
And I do not know if this will work you but looks promising. And maybe you have already seen this:
[http://www.webupd8.org/2016/08/how-to-install-and-configure-bumblebee.html](http://www.webupd8.org/2016/08/how-to-install-and-configure-bumblebee.html)

And I have to say for myself that the newer drivers are getting much better in my case use.
```
Graphics:  Card: NVIDIA GF106 [GeForce GTS 450]
           Display Server: X.Org 1.18.4 driver: nvidia
           Resolution: 1920x1080@60.00hz
           GLX Renderer: GeForce GTS 450/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 375.10
```
Hoping this is usefull to you and good luck

---

### Post by davidv1992 on 2016-11-25
Thanks for the advice, it did indeed help.

Specifically, the tutorials suggestion of using nvidia-prime to disable it for X was golden. Unfortunately, I'm still unable to force the GPU to an off state with respect to power management. Something still is binding the module nvidia-drm, but lsmod does not specifiy what. Is there any other way of figuring that out?

---

