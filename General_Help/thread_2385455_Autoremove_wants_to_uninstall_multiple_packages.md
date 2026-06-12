---
title: "Autoremove wants to uninstall multiple packages"
date: 2018-02-20
forum: General Help
---

### Post by michael337 on 2018-02-20
After removing wine1.6, and installing wine-stable, autoremove wants to remove:

```
The following packages were automatically installed and are no longer required:
  glib-networking:i386 i965-va-driver:i386 libatk-bridge2.0-0:i386 libatspi2.0-0:i386
  libboost-filesystem1.58.0:i386 libboost-system1.58.0:i386 libcairo-gobject2:i386
  libcapnp-0.5.3:i386 libcolord2:i386 libegl1-mesa:i386 libepoxy0:i386 libgbm1:i386
  libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0:i386 libgtk-3-0:i386
  libjson-glib-1.0-0:i386 libmirclient9:i386 libmircommon7:i386 libmircore1:i386
  libmirprotobuf3:i386 libprotobuf-lite9v5:i386 libproxy1v5:i386 libqmi-glib1
  librest-0.7-0:i386 libsoup-gnome2.4-1:i386 libsoup2.4-1:i386 libva-drm1:i386
  libva-x11-1:i386 libva1:i386 libvdpau1:i386 libwayland-client0:i386 libwayland-cursor0:i386
  libwayland-egl1-mesa:i386 libwayland-server0:i386 libxcb-xfixes0:i386 libxkbcommon0:i386
  mesa-vdpau-drivers:i386 ocl-icd-libopencl1:i386 va-driver-all:i386 vdpau-driver-all:i386
  vdpau-va-driver:i386
Use 'sudo apt autoremove' to remove them.
```
Should I be concerned, or are these depreciated packages that wine1.6 installed?
If this helps, I'm using Ubuntu 16.04 (64 bit version).

---

### Post by tinylagarto on 2018-02-20
You should be able to remove them all without problem as I only see i386 packages and you are on 64 bit. I guess it has something to do with 32 bit compatibility. I am not sure. 

Though use autoremove carefully and most of the time you could just ignore the autoremove option if unsure.

---

### Post by kerry_s on 2018-02-20
your good to go those were installed for wine, shouldn't affect anything.

---

### Post by vanadium on 2018-02-23
autoremove is your package manager observing that automatically installed dependencies, i.e.e, dependencies from a program you once installed, are no longer used. It should be very safe to use autoremove. Keeps your system neat and tidy. That is also how old kernels are removed - only a few recent kernels are preserved.

---

