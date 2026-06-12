---
title: "While installing libqt4-dev"
date: 2015-07-14
forum: General Help
---

### Post by eshant_engineer on 2015-07-14
While installing required library libqt4-dev for building keepassx 2 alpha 6 source code, I am asked following:-

```

sudo apt-get build-dep libqt4-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Picking 'qt4-x11' as source package instead of 'libqt4-dev'
Note, selecting 'libtiff5-dev' instead of 'libtiff-dev'
The following packages will be REMOVED:
  libegl1-mesa-drivers-lts-utopic libegl1-mesa-lts-utopic libgbm1-lts-utopic
  libgl1-mesa-dri-lts-utopic libgl1-mesa-dri-lts-utopic:i386
  libgl1-mesa-glx-lts-utopic libgl1-mesa-glx-lts-utopic:i386
  libglapi-mesa-lts-utopic libglapi-mesa-lts-utopic:i386
  libgles1-mesa-lts-utopic libgles2-mesa-lts-utopic libopenvg1-mesa-lts-utopic
  libwayland-egl1-mesa-lts-utopic libxatracker2-lts-utopic
  xserver-xorg-core-lts-utopic xserver-xorg-input-all-lts-utopic
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
  comerr-dev debhelper dh-apparmor docbook docbook-to-man flex freetds-common
  freetds-dev gir1.2-gst-plugins-base-0.10 gir1.2-gstreamer-0.10
  gir1.2-gtk-2.0 icu-devtools krb5-multidev libasound2-dev libatk1.0-dev
  libaudio-dev libcairo-script-interpreter2 libcairo2-dev libct4 libcups2-dev
  libdbus-1-dev libdrm-dev libegl1-mesa libfl-dev libfontconfig1-dev
  libfreetype6-dev libgdk-pixbuf2.0-dev libgl1-mesa-dev libgl1-mesa-dri
  libgl1-mesa-dri:i386 libgl1-mesa-glx libgl1-mesa-glx:i386 libglapi-mesa
  libglapi-mesa:i386 libgles1-mesa libgles2-mesa libglib2.0-dev
  libglu1-mesa-dev libgnutls-dev libgnutlsxx27 libgssrpc4
  libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev libgtk2.0-dev
  libharfbuzz-dev libharfbuzz-gobject0 libice-dev libicu-dev libjbig-dev
  libjpeg-dev libjpeg-turbo8-dev libjpeg8-dev libkadm5clnt-mit9
  libkadm5srv-mit9 libkdb5-7 libkrb5-dev liblcms2-dev libllvm3.6
  libllvm3.6:i386 libltdl-dev liblzma-dev libmng-dev libmysqlclient-dev
  libodbc1 libp11-kit-dev libpam0g-dev libpango1.0-dev libpcre3-dev
  libpcrecpp0 libpixman-1-dev libpng12-dev libpq-dev libpq5
  libpthread-stubs0-dev libreadline-dev libreadline6-dev libsigsegv2 libsm-dev
  libsp1c2 libsqlite3-dev libssl-dev libsybdb5 libtasn1-6-dev libtiff5-dev
  libtiffxx5 libtinfo-dev libwayland-egl1-mesa libx11-dev libx11-xcb-dev
  libxau-dev libxcb-dri2-0-dev libxcb-dri3-dev libxcb-glx0-dev
  libxcb-present-dev libxcb-randr0-dev libxcb-render0-dev libxcb-shape0-dev
  libxcb-shm0-dev libxcb-sync-dev libxcb-xfixes0-dev libxcb1-dev
  libxcomposite-dev libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev
  libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxml2-dev libxml2-utils
  libxmu-dev libxmu-headers libxrandr-dev libxrender-dev libxshmfence-dev
  libxslt1-dev libxt-dev libxtst-dev libxv-dev libxxf86vm-dev m4
  mesa-common-dev odbcinst odbcinst1debian2 pkg-kde-tools po-debconf sgml-data
  sp unixodbc unixodbc-dev x11proto-composite-dev x11proto-core-dev
  x11proto-damage-dev x11proto-dri2-dev x11proto-fixes-dev x11proto-gl-dev
  x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-record-dev
  x11proto-render-dev x11proto-video-dev x11proto-xext-dev
  x11proto-xf86vidmode-dev x11proto-xinerama-dev xorg-sgml-doctools
  xserver-xorg xserver-xorg-core xserver-xorg-input-evdev xtrans-dev
0 upgraded, 152 newly installed, 42 to remove and 7 not upgraded.
Need to get 64.1 MB of archives.
After this operation, 218 MB of additional disk space will be used.

```

I don't know about the packages, it is about to remove. But since the list is big, I thought of taking suggestion on forum. What shall I do?

---

### Post by steeldriver on 2015-07-14
I'm confused - you shouldn't need to install the build-deps for libqt4-dev unless you're building libqt4-dev itself from source ... and you shouldn't need to build libqt4-dev from source to build KeePassX from source

What exactly are you trying to do?

---

### Post by eshant_engineer on 2015-07-14
> **steeldriver said:**
> I'm confused - you shouldn't need to install the build-deps for libqt4-dev unless you're building libqt4-dev itself from source ... and you shouldn't need to build libqt4-dev from source to build KeePassX from source

What exactly are you trying to do?

I am following the requirements to build keepass as mentioned [here]("https://github.com/keepassx/keepassx#from-source"), for which I have to install libqt4-dev but it is asking to allow to uninstall list of xorg packages


```

root@eshant-N5110:/# **apt-get install libqt4-dev**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libegl1-mesa libgl1-mesa-dri libgl1-mesa-dri:i386 libgl1-mesa-glx
  libgl1-mesa-glx:i386 libglapi-mesa libglapi-mesa:i386 libgles1-mesa
  libgles2-mesa libllvm3.6 libllvm3.6:i386 libqt4-dev-bin libqt4-qt3support
  libqtwebkit-dev libwayland-egl1-mesa qt4-linguist-tools qt4-qmake
  xserver-xorg xserver-xorg-core xserver-xorg-input-evdev
Suggested packages:
  firebird-dev libmysqlclient-dev libpq-dev libsqlite0-dev libsqlite3-dev
  qt4-dev-tools qt4-doc unixodbc-dev xfonts-100dpi xfonts-75dpi
Recommended packages:
  libqt4-opengl-dev
The following packages will be REMOVED:
  libegl1-mesa-drivers-lts-utopic libegl1-mesa-lts-utopic libgbm1-lts-utopic
  libgl1-mesa-dri-lts-utopic libgl1-mesa-dri-lts-utopic:i386
  libgl1-mesa-glx-lts-utopic libgl1-mesa-glx-lts-utopic:i386
  libglapi-mesa-lts-utopic libglapi-mesa-lts-utopic:i386
  libgles1-mesa-lts-utopic libgles2-mesa-lts-utopic libopenvg1-mesa-lts-utopic
  libwayland-egl1-mesa-lts-utopic libxatracker2-lts-utopic
  xserver-xorg-core-lts-utopic xserver-xorg-input-all-lts-utopic
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
  libegl1-mesa libgl1-mesa-dri libgl1-mesa-dri:i386 libgl1-mesa-glx
  libgl1-mesa-glx:i386 libglapi-mesa libglapi-mesa:i386 libgles1-mesa
  libgles2-mesa libllvm3.6 libllvm3.6:i386 libqt4-dev libqt4-dev-bin
  libqt4-qt3support libqtwebkit-dev libwayland-egl1-mesa qt4-linguist-tools
  qt4-qmake xserver-xorg xserver-xorg-core xserver-xorg-input-evdev
0 upgraded, 21 newly installed, 42 to remove and 7 not upgraded.
Need to get 31.1 MB of archives.
After this operation, 74.2 MB of additional disk space will be used.
Do you want to continue? [Y/n] 

```

---

### Post by oldos2er on 2015-07-14
There is a PPA of keepassx alpha daily builds [here]("https://launchpad.net/~keepassx/+archive/ubuntu/daily").

---

### Post by monkeybrain20122 on 2015-07-14
Well first of all why did you log in as root??! For security sakes you should run commands that require root privileges with sudo on a per command basis rather than logging in as root.

Secondly, did you install a 14.04 point release? it seems like you are on the lts-hardware-enabling stack and it is incompatible with qt4-dev in trusty so installing it would remove the -lts packages and replace them with the original ones (e.g libegl1-mesa-lts-utopic --> removed, libegl1-mesa --> installed etc)

---

### Post by eshant_engineer on 2015-07-15
> **monkeybrain20122 said:**
> Well first of all why did you log in as root??! For security sakes you should run commands that require root privileges with sudo on a per command basis rather than logging in as root.

Secondly, did you install a 14.04 point release? it seems like you are on the lts-hardware-enabling stack and it is incompatible with qt4-dev in trusty so installing it would remove the -lts packages and replace them with the original ones (e.g libegl1-mesa-lts-utopic --> removed, libegl1-mesa --> installed etc)

it is also removing display driver xorgs and other important packages, so after it finish, it might not open login screen after I reboot the system. The question is how can we have libqt4-dev(or higher, I guess it is backward compatible) for development on LTS without losing xorgs and important packages?

---

### Post by steeldriver on 2015-07-15
If you leave the libqt-dev install out of the equation for the moment, what does it propose to do if you upgrade e.g.

```

sudo apt-get update

sudo apt-get **--dry-run** upgrade

```

---

