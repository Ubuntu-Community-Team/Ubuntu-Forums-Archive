---
title: "Ubuntu 12.04 and Nvidia Geoforce 840M Gfx card"
date: 2014-11-05
forum: General Help
---

### Post by Tony Flury on 2014-11-05
I have a laptop with Geforce 840M Gfx chip set, and Intel 4th Gen Core Processor Integrated Graphics Controller, and a clean install of Ubuntu 12.04, with all the recent updates.

glxinfo reported that glx functionality was working fine, but as far as I know the default nouveau drivers don't do 3D graphics acceleration, and s/w like Firestorm won't recognise the Nvidia chip-set, using the intel chips as default.

When I look for additional Drivers (System Settings -> Additional Drivers) no drivers are listed.

As I want to be able to use the capabilities provided by the Nvidia gfx chip-set, I manually install nvidia-319 from the repos (I believe that 319 supports the 840M chip set), and restarted.

I now have the following symptoms :

    glxinfo reports that it can't find GLX extensions on the display.
    firestorm wont start - since GLX does not work

I have noticed in /var/log/Xorg.0.log that the nvidia driver is loaded, and then some time later is unloaded : grep nvidia /var/log/Xorg.0.log

```

[    24.364] (==) Matched nvidia as autoconfigured driver 1
[    24.424] (II) LoadModule: "nvidia"
[    24.424] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    24.495] (II) Module nvidia: vendor="NVIDIA Corporation"
[    24.547] (II) UnloadModule: "nvidia"
[    24.547] (II) Unloading nvidia

```

Between the nvidia module being loaded nouveas, vesa, modeset, fbdev and fbdevhw modules are all loaded (as reported in /var/log/Xorg.0.log)

Any attempt to use the nvidia driver (by using nvidia-xconfig to create /etc/X11/xorg.conf) results in a 600x400 res screen - presumably because the nvidia module is not actually loaded.

I want to get to the situation where the nvidia chipset is use in preference to the intel set - how do i do that ?

The BIOS does not allow the intel set to be disabled

---

### Post by Tony Flury on 2014-11-07
For completeness - the full answer to this is to use nvidia-prime, as detailed on this [Hybrid Graphics Wiki Page][1]

Essentially : Install the nvidia drivers and nvidia prime

     sudo apt-get install  nvidia-319 nvidia-prime

and then restart

  [1]: [https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

---

