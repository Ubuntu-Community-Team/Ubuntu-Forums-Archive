---
title: "apt-get install is removing a LOT of packages when install libsdl2-dev, 14.04.2 HWE"
date: 2015-03-10
forum: General Help
---

### Post by edenist on 2015-03-10
[FONT=verdana]I have a 14.04.2 x86_64 system with HWE installed.[/FONT]
[FONT=verdana]I am wanting to install the package libsdl2-dev.[/FONT]
[FONT=verdana]Initially I got the following error:

[/FONT]
```
$:~/programming/SMD/dgen/dgen-sdl-1.33$ sudo apt-get install libsdl2-dev 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 empathy : Depends: libclutter-gst-2.0-0 (>= 0.10.0) but it is not going to be installed
           Depends: libclutter-gtk-1.0-0 (>= 1.4) but it is not going to be installed
           Depends: libcogl15 (>= 1.15.8) but it is not going to be installed
           Recommends: telepathy-haze but it is not going to be installed
 gir1.2-clutter-gst-2.0 : Depends: libclutter-gst-2.0-0 (>= 1.6.0) but it is not going to be installed
 gir1.2-cogl-1.0 : Depends: libcogl15 (>= 1.15.8) but it is not going to be installed
 gir1.2-coglpango-1.0 : Depends: libcogl-pango15 (>= 1.15.8) but it is not going to be installed
 libcheese-gtk23 : Depends: libclutter-gtk-1.0-0 (>= 0.91.8) but it is not going to be installed
                   Depends: libcogl15 (>= 1.15.8) but it is not going to be installed
 libcheese7 : Depends: libclutter-gst-2.0-0 (>= 0.10.0) but it is not going to be installed
              Depends: gstreamer1.0-clutter but it is not going to be installed
 libclutter-1.0-0 : Depends: libcogl-pango15 (>= 1.15.8) but it is not going to be installed
                    Depends: libcogl15 (>= 1.15.8) but it is not going to be installed
 libsdl2-dev : Depends: libegl1-mesa-dev
               Depends: libgles2-mesa-dev
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```
[FONT=verdana]
I resolved this by installing libegl1-mesa-dev-lts-utopic and libgles2-mesa-dev-lts-utopic[/FONT]
[FONT=verdana]Now, when trying to install libsdl2-dev I get the following:

[/FONT]
```
The following packages were automatically installed and are no longer required:
  gcc-4.8-base:i386 libdrm-intel1:i386 libdrm-nouveau2:i386
  libdrm-radeon1:i386 libedit2:i386 libelf1:i386 libexpat1:i386 libffi6:i386
  libllvm3.5:i386 libpciaccess-dev libpciaccess0:i386 libpixman-1-dev
  libstdc++6:i386 libtxc-dxtn-s2tc0:i386 libx11-xcb1:i386 libxcb-dri2-0:i386
  libxcb-dri3-0:i386 libxcb-glx0:i386 libxcb-present0:i386 libxcb-sync1:i386
  libxdamage1:i386 libxfixes3:i386 libxkbfile-dev libxshmfence1:i386
  libxxf86vm1:i386 x11proto-dri3-dev x11proto-fonts-dev x11proto-present-dev
  x11proto-resource-dev x11proto-xf86bigfont-dev x11proto-xf86dri-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libegl1-mesa libegl1-mesa-dev libegl1-mesa-drivers libgl1-mesa-dev
  libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libgles2-mesa
  libgles2-mesa-dev libglu1-mesa-dev libmirclient-dev libmirclient7
  libmirclientplatform-mesa libmirprotobuf-dev libmirprotobuf0 libopenvg1-mesa
  libprotobuf-dev libprotobuf-lite8 libts-dev libudev-dev libwayland-egl1-mesa
  libxcursor-dev libxi-dev libxinerama-dev libxkbcommon-dev libxrandr-dev
  libxrender-dev libxss-dev libxv-dev mircommon-dev xserver-xorg-core
  xserver-xorg-input-evdev
Suggested packages:
  libglide3 xfonts-100dpi xfonts-75dpi
The following packages will be REMOVED:
  libegl1-mesa-dev-lts-utopic libegl1-mesa-drivers-lts-utopic
  libegl1-mesa-lts-utopic libgbm1-lts-utopic libgl1-mesa-dri-lts-utopic
  libgl1-mesa-dri-lts-utopic:i386 libgl1-mesa-glx-lts-utopic
  libgl1-mesa-glx-lts-utopic:i386 libglapi-mesa-lts-utopic
  libglapi-mesa-lts-utopic:i386 libgles1-mesa-lts-utopic
  libgles2-mesa-dev-lts-utopic libgles2-mesa-lts-utopic
  libopenvg1-mesa-lts-utopic libwayland-egl1-mesa-lts-utopic
  libxatracker2-lts-utopic xorg xserver-xorg-core-lts-utopic
  xserver-xorg-dev-lts-utopic xserver-xorg-input-all-lts-utopic
  xserver-xorg-input-evdev-lts-utopic xserver-xorg-input-mouse-lts-utopic
  xserver-xorg-input-synaptics-lts-utopic
  xserver-xorg-input-vmmouse-lts-utopic xserver-xorg-input-wacom-lts-utopic
  xserver-xorg-lts-utopic xserver-xorg-video-all-lts-utopic
  xserver-xorg-video-ati-lts-utopic xserver-xorg-video-cirrus-lts-utopic
  xserver-xorg-video-fbdev-lts-utopic xserver-xorg-video-intel-lts-utopic
  xserver-xorg-video-mach64-lts-utopic xserver-xorg-video-mga-lts-utopic
  xserver-xorg-video-modesetting-lts-utopic
  xserver-xorg-video-neomagic-lts-utopic xserver-xorg-video-nouveau-lts-utopic
  xserver-xorg-video-openchrome-lts-utopic xserver-xorg-video-r128-lts-utopic
  xserver-xorg-video-radeon-lts-utopic xserver-xorg-video-savage-lts-utopic
  xserver-xorg-video-siliconmotion-lts-utopic
  xserver-xorg-video-sisusb-lts-utopic xserver-xorg-video-tdfx-lts-utopic
  xserver-xorg-video-trident-lts-utopic xserver-xorg-video-vesa-lts-utopic
  xserver-xorg-video-vmware-lts-utopic
The following NEW packages will be installed:
  libegl1-mesa libegl1-mesa-dev libegl1-mesa-drivers libgl1-mesa-dev
  libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libgles2-mesa
  libgles2-mesa-dev libglu1-mesa-dev libmirclient-dev libmirclient7
  libmirclientplatform-mesa libmirprotobuf-dev libmirprotobuf0 libopenvg1-mesa
  libprotobuf-dev libprotobuf-lite8 libsdl2-dev libts-dev libudev-dev
  libwayland-egl1-mesa libxcursor-dev libxi-dev libxinerama-dev
  libxkbcommon-dev libxrandr-dev libxrender-dev libxss-dev libxv-dev
  mircommon-dev xserver-xorg-core xserver-xorg-input-evdev
0 to upgrade, 33 to newly install, 46 to remove and 7 not to upgrade.
Need to get 10.7 MB of archives.
After this operation, 1,449 kB disk space will be freed.
Do you want to continue? [Y/n] n
Abort.
```


[FONT=verdana]That seems like a LOT of packages to remove, and some of those [xorg, xserver-xorg-core-lts-utupic] sound like a SUPER risky thing to agree to.[/FONT]
[FONT=verdana]Why is it trying to uninstall my HWE packages? Is this broken dependencies with libsdl2-dev?[/FONT]

---

### Post by mc4man on 2015-03-11
The 14.04.2 HWE install is hobbled when it comes to devel packages that have mesa deps. In some cases there are workarounds, others no.
see next post...

---

### Post by mc4man on 2015-03-11
Most of the devel package install issues will be resolved by a mesa update in near future.
(- currently available if you enable the proposed repo & install the dev package(s) while proposed is enabled
[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1424466](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1424466)

---

