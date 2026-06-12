---
title: "Problems after 1404_HWE_EOL need to get back to &quot;wily&quot;"
date: 2016-08-31
forum: General Help
---

### Post by fgl27 on 2016-08-31
I click install without read it all on the [**"1404_HWE_EOL"**]("https://wiki.ubuntu.com/1404_HWE_EOL") update then my ubuntu 14.04 update some parts from **wily** to **xenial** then I lost all support of AMD video drivers **fglrx**, and the performance now sucks as my APU depends on AMD driver to get the best performance for CPU/GPU...

Reading the logs I see what was installed and removed, I try to install back wily but I get some errors like this:

```
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
 unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.


```
[COLOR=#ff0000][SIZE=4][B]
The question is... Can I safe do a process to remove the new and re-install the old?[/B][/SIZE][/COLOR]

I know I can just remove the new xenial if I try some will unistall but not all, I can't install the old then if I reboot my system will not boot I have try, so I need to boot to recovery and install the xenial back so my system can properly boot...

[B]I believed must have a correct process on how to do this, if any one know please share...
[/B]
Any help is appreciated, thanks....

below is the result of the install log....
```

install:

xserver-xorg-video-mach64-lts-xenial:amd64
xserver-xorg-video-all-lts-xenial:amd64 
xserver-xorg-video-amdgpu-lts-xenial:amd64
linux-signed-generic-lts-xenial:amd64
xserver-xorg-video-cirrus-lts-xenial:amd64 
xserver-xorg-video-radeon-lts-xenial:amd64 
xserver-xorg-video-mga-lts-xenial:amd64 
xserver-xorg-video-trident-lts-xenial:amd64 
xserver-xorg-video-fbdev-lts-xenial:amd64 
xserver-xorg-video-tdfx-lts-xenial:amd64 
libllvm3.4:amd64 
libllvm3.4:i386 
libglapi-mesa-lts-xenial:amd64 
libglapi-mesa-lts-xenial:i386
xserver-xorg-video-ati-lts-xenial:amd64
libwayland-egl1-mesa-lts-xenial:amd64 
xserver-xorg-input-all-lts-xenial:amd64 
xserver-xorg-video-neomagic-lts-xenial:amd64 
xserver-xorg-video-savage-lts-xenial:amd64 
libegl1-mesa-lts-xenial:amd64 
xserver-xorg-input-vmmouse-lts-xenial:amd64 
xserver-xorg-input-evdev-lts-xenial:amd64 
linux-signed-image-4.4.0-36-generic:amd64 
libgles2-mesa-lts-xenial:amd64 
xserver-xorg-video-vesa-lts-xenial:amd64 
linux-signed-image-generic-lts-xenial:amd64 
xserver-xorg-video-siliconmotion-lts-xenial:amd64 
libxatracker2-lts-xenial:amd64 
xserver-xorg-input-wacom-lts-xenial:amd64 
xserver-xorg-video-nouveau-lts-xenial:amd64 
xserver-xorg-video-openchrome-lts-xenial:amd64 
xserver-xorg-video-qxl-lts-xenial:amd64 
libgbm1-lts-xenial:amd64 
xserver-xorg-video-intel-lts-xenial:amd64
xserver-xorg-video-sisusb-lts-xenial:amd64 
libgl1-mesa-dri-lts-xenial:amd64
libgl1-mesa-dri-lts-xenial:i386 
libgl1-mesa-glx-lts-xenial:amd64 
libgl1-mesa-glx-lts-xenial:i386 
xserver-xorg-video-vmware-lts-xenial:amd64 
xserver-xorg-core-lts-xenial:amd64 
xserver-xorg-video-r128-lts-xenial:amd64 
libgles1-mesa-lts-xenial:amd64 
xserver-xorg-lts-xenial:amd64 
xserver-xorg-input-synaptics-lts-xenial:amd64 
libllvm3.8v4:amd64 
libllvm3.8v4:i386
```

```

Remove: 
xserver-xorg-video-neomagic-lts-wily:amd64 
xserver-xorg-input-wacom-lts-wily:amd64 
xserver-xorg-video-radeon-lts-wily:amd64 
xserver-xorg-video-nouveau-lts-wily:amd64 
xserver-xorg-video-vmware-lts-wily:amd64 
xserver-xorg-core-lts-wily:amd64 
xserver-xorg-lts-wily:amd64 
xserver-xorg-input-vmmouse-lts-wily:amd64 
xserver-xorg-video-openchrome-lts-wily:amd64 
libgbm1-lts-wily:amd64 
libgl1-mesa-glx-lts-wily:amd64 
libgl1-mesa-glx-lts-wily:i386
libglapi-mesa-lts-wily:amd64 
libglapi-mesa-lts-wily:i386 
xserver-xorg-video-savage-lts-wily:amd64 
xserver-xorg-video-sisusb-lts-wily:amd64 
xserver-xorg-video-trident-lts-wily:amd64 
libgl1-mesa-dri-lts-wily:amd64 
libgl1-mesa-dri-lts-wily:i386 
xserver-xorg-video-ati-lts-wily:amd64 
xserver-xorg-video-mach64-lts-wily:amd64 
xserver-xorg-video-tdfx-lts-wily:amd64 
xserver-xorg-video-r128-lts-wily:amd64 
xserver-xorg-input-evdev-lts-wily:amd64
xserver-xorg-input-all-lts-wily:amd64 
xserver-xorg-video-siliconmotion-lts-wily:amd64 
libxatracker2-lts-wily:amd64 
xserver-xorg-input-synaptics-lts-wily:amd64
libegl1-mesa-lts-wily:amd64 
xserver-xorg-video-mga-lts-wily:amd64
xserver-xorg-video-qxl-lts-wily:amd64 
libgles2-mesa-lts-wily:amd64 
xserver-xorg-video-all-lts-wily:amd64 
xserver-xorg-input-mouse-lts-wily:amd64
libwayland-egl1-mesa-lts-wily:amd64 
xserver-xorg-video-cirrus-lts-wily:amd64 
xserver-xorg-video-fbdev-lts-wily:amd64 
xserver-xorg-video-vesa-lts-wily:amd64
```

---

