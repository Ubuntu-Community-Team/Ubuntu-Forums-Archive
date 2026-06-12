---
title: "Updates fail: libgl1-mesa-dev has broken dependencies but can't be removed."
date: 2013-06-21
forum: General Help
---

### Post by james_mcl on 2013-06-21
I've just tried (and failed) to install eight updates:

libgl1-mesa-glx
libgl1-mesa-glx:i386
libglapi-mesa
libglapi-mesa:i386
libglu1-mesa
libglu1-mesa-dev
libglu1-mesa:i386
libxatracker1

All of these have:
Installed version: 8.0.4-0ubuntu0.5
Available version: 8.0.4-0ubuntu0.6

The update fails with the following error message:
"libgl1-mesa-dev: Depends: mesa-common-dev-lts-raring but it is not installed
                 Depends: libgl1-mesa-glx-lts-raring but it is not installed"

(I don't know why there should be a dependency on packages with Raring in their name, since I'm using Precise)

According to Synaptic, libgl1-mesa-dev does indeed have broken dependencies. However, when I try to remove it, I am told that several other applications will have to be removed - some of these being:

audacity
cantor
gnuplot
gnuplot-x11
gvfs
ia32-libs
ia32-libs-multiarch:i386
kde-runtime
kdebase-runtime
mate-desktop-environment
mate-media-pulse
maxima
scilab
vlc
wine

This is not an exhaustive list of the applications in the "To be removed" list, but should be enough to make it clear that removing libgl1-mesa-dev would lead to disaster. At the moment, however, VLC and MATE both seem to be working OK, as does an application which depends on ia32-libs.

---

### Post by james_mcl on 2013-06-24
Fixed it - going into Synaptic and choosing to reinstall libgl1-mesa-dev instead of removing it allows four of the eight updates to be applied simultaneously. Update Manager can then be used to apply the rest.

---

