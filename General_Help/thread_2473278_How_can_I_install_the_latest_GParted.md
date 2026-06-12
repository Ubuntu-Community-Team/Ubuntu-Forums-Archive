---
title: "How can I install the latest GParted?"
date: 2022-03-30
forum: General Help
---

### Post by Paddy Landau on 2022-03-30
Gparted has released version 1.4.0, which has both improved and new features.

I'm on Ubuntu 20.04, which currently holds version 1.0.0.

I'd like to install the latest version of GParted, but I can't figure out how. The [GParted website]("https://gparted.org/") allows me to download the Live ISO, but that's not what I'm after. I can't work out from the website how to install it on my system.

There's also no snap, flatpak, or appimage that I could use instead.

Do you know how I can install the latest GParted on my machine, please?

(If I can't, I'll settle for using the Live ISO.)

Thank you

---

### Post by &amp;KyT$0P# on 2022-03-30
Can you compile it from source?  That website has a link to GParted source code, where you can find 1.4.0 source code tarball.

---

### Post by Paddy Landau on 2022-03-30
> **halogen2 said:**
> Can you compile it from source?
Thank you; that hadn't occurred to me, as I don't know how to do that!

I downloaded and extracted the tar. It has instructions! The instructions say to begin with [FONT=courier new]./configure[/FONT], which I did. But, it returns an error:
```
configure: error: *** libuuid not found.
```
As [FONT=courier new]libuuid1[/FONT] is already installed, I suspect that this can only be solved with a rather complex process, which is more than I'm willing to do.

Oh, well. I'll just have to wait.

---

### Post by &amp;KyT$0P# on 2022-03-30
Does running
```
sudo apt-get build-dep gparted
```
install the missing build dependencies?

---

### Post by Paddy Landau on 2022-03-30
> **halogen2 said:**
> Does running
```
sudo apt-get build-dep gparted
```
install the missing build dependencies?
It returns the error:
```
E: Unable to find a source package for gparted
```
However, I already have gparted installed from the standard repository (version 1.0.0, though), so would it have made a difference?It returns the error:
```
E: Unable to find a source package for gparted
```
However, I already have gparted installed from the standard repository (version 1.0.0, though), so would it have made a difference?

**EDIT: I figured out how to fix the error&#8230; See my next post**

---

### Post by Paddy Landau on 2022-03-30
I added the source code repository, and your command is ready to install a whole bunch of packages.

Will this potentially mess up my system?

```
The following NEW packages will be installed:
  autopoint debhelper dh-autoreconf dh-strip-nondeterminism dwz gir1.2-harfbuzz-0.0 icu-devtools intltool intltool-debian itstool libatk-bridge2.0-dev libatk1.0-dev
  libatkmm-1.6-dev libatspi2.0-dev libblkid-dev libcairo-script-interpreter2 libcairo2-dev libcairomm-1.0-dev libdatrie-dev libdbus-1-dev libdebhelper-perl
  libdevmapper-dev libegl-dev libegl1-mesa-dev libepoxy-dev libexpat1-dev libffi-dev libfile-stripnondeterminism-perl libfontconfig1-dev libfreetype-dev
  libfreetype6-dev libfribidi-dev libgdk-pixbuf2.0-dev libgl-dev libgl1-mesa-dev libgles-dev libgles1 libglib2.0-dev libglib2.0-dev-bin libglibmm-2.4-dev libglvnd-dev
  libglx-dev libgraphite2-dev libgtk-3-dev libgtkmm-3.0-dev libharfbuzz-dev libharfbuzz-gobject0 libice-dev libicu-dev libmount-dev libopengl-dev libpango1.0-dev
  libpangomm-1.4-dev libparted-dev libpcre16-3 libpcre2-dev libpcre2-posix2 libpcre3-dev libpcre32-3 libpcrecpp0v5 libpixman-1-dev libpng-dev libpthread-stubs0-dev
  libselinux1-dev libsepol1-dev libsigc++-2.0-dev libsm-dev libsub-override-perl libthai-dev libtool libudev-dev libwayland-bin libwayland-dev libx11-dev libxau-dev
  libxcb-render0-dev libxcb-shm0-dev libxcb1-dev libxcomposite-dev libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev libxi-dev
  libxinerama-dev libxkbcommon-dev libxml2-utils libxrandr-dev libxrender-dev libxtst-dev pango1.0-tools po-debconf python3-libxml2 uuid-dev wayland-protocols
  x11proto-core-dev x11proto-dev x11proto-input-dev x11proto-randr-dev x11proto-record-dev x11proto-xext-dev x11proto-xinerama-dev xorg-sgml-doctools xtrans-dev
  yelp-tools zlib1g-dev
0 upgraded, 108 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by ActionParsnip on 2022-03-30
You may want to check deps. If it needs a tonne of the new GTK stuff you'll need to build that as well....

---

### Post by &amp;KyT$0P# on 2022-03-30
> **Paddy Landau said:**
> I added the source code repository, and your command is ready to install a whole bunch of packages.

Will this potentially mess up my system?

I don't see any problem with what it wants to install, if it were my system I would go ahead with it.

---

### Post by Paddy Landau on 2022-03-30
> **ActionParsnip said:**
> You may want to check deps. If it needs a tonne of the new GTK stuff you'll need to build that as well....
> **halogen2 said:**
> I don't see any problem with what it wants to install, if it were my system I would go ahead with it.
Now I'm nervous, ha ha!

I'll test it on a virtual machine instead &#128578;

---

### Post by dragonfly41 on 2022-03-30
Build it in a Ubuntu VM perhaps as an experiment.

ah. You wrote that at end!

---

### Post by Paddy Landau on 2022-03-30
**Result**

I followed all the instructions on a virtual machine with Lubuntu 20.04.

I had to uninstall the default GParted, and then everything worked!

Thank you :)

---

