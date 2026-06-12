---
title: "Compiling Intel video driver"
date: 2013-11-08
forum: General Help
---

### Post by williammanda on 2013-11-08
I need some advice on the proper way to compile Intel video drivers:
libva
intel-video-driver

I found this site:
[https://gitorious.org/gst-plugins-vaapi/pages/Home](https://gitorious.org/gst-plugins-vaapi/pages/Home)

With these two commands:

libva
git clone git://anongit.freedesktop.org/vaapi/libva
./autogen.sh —prefix=/usr && make && sudo make install

backend driver (take Intel GenX graphics driver as example)
git clone git://anongit.freedesktop.org/vaapi/intel-driver
./autogen.sh —prefix=/usr && make && sudo make install

Will these work? If not please advise.
Thanks

---

### Post by fantab on 2013-11-08
I think intel-VAAPI libva drivers are available in the Ubuntu Repositories. Search for them and install them, they should work.

---

### Post by mastablasta on 2013-11-09
if you need newer version it might be easier to use xorg edgers PPA

---

### Post by williammanda on 2013-11-09
Sorry I need to be more specific...I need the latest version from Intel not the current version used by Ubuntu or the version supplied by xorg-edgers. I'm working with Intel on a bug and I need to compile the latest version.
Thanks

---

