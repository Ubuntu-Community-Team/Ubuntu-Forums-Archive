---
title: "how do I completely uninstall all of these with the Terminal?"
date: 2019-07-14
forum: General Help
---

### Post by ardouronerous on 2019-07-14
I've installed OpenShot a few months ago and now I want to completely uninstall it and all it's dependencies, how do I do it on the Terminal?

When uninstalling software with Synaptic, I've noticed there are two  types of uninstall, removal and complete uninstall, I always do a  complete uninstall instead of removal.

> [FONT=courier new]Commandline: apt install openshot
Install: python-webencodings:amd64 (0.5-2, automatic), blender:amd64 (2.79.b+dfsg0-1ubuntu1.18.04.1, automatic), libsocket++1:amd64 (1.12.13-9, automatic), python3-scour:amd64 (0.36-2, automatic), libmagick++-6.q16-7:amd64 (8:6.9.7.4+dfsg-16ubuntu6.7, automatic), libimage-magick-perl:amd64 (8:6.9.7.4+dfsg-16ubuntu6.7, automatic), javascript-common:amd64 (11, automatic), libopencolorio1v5:amd64 (1.1.0~dfsg0-1, automatic), liblog4cplus-1.1-9:amd64 (1.1.2-3.2, automatic), libimage-magick-q16-perl:amd64 (8:6.9.7.4+dfsg-16ubuntu6.7, automatic), libopencv-imgcodecs3.2:amd64 (3.2.0+dfsg-4ubuntu0.1, automatic), fig2dev:amd64 (1:3.2.6a-6ubuntu1, automatic), transfig:amd64 (1:3.2.6a-6ubuntu1, automatic), libopenshot14:amd64 (0.1.9+dfsg1-3build1, automatic), libgdcm2.8:amd64 (2.8.4-1build2, automatic), libpotrace0:amd64 (1.14-2, automatic), libjs-jquery:amd64 (3.2.1-1, automatic), blender-data:amd64 (2.79.b+dfsg0-1ubuntu1.18.04.1, automatic), gawk:amd64 (1:4.1.4+dfsg-1build1, automatic), libopencv-imgproc3.2:amd64 (3.2.0+dfsg-4ubuntu0.1, automatic), python-chardet:amd64 (3.0.4-1, automatic), libopenvdb5.0:amd64 (5.0.0-1, automatic), python-lxml:amd64 (4.2.1-1ubuntu0.1, automatic), python3-pyqt5.qtwebkit:amd64 (5.10.1+dfsg-1ubuntu2, automatic), python3-zmq:amd64 (16.0.2-2build2, automatic), libblosc1:amd64 (1.14.2+ds1-1, automatic), libboost-regex1.65.1:amd64 (1.65.1+dfsg-0ubuntu5, automatic), python-scour:amd64 (0.36-2, automatic), python3-openshot:amd64 (0.1.9+dfsg1-3build1, automatic), python-html5lib:amd64 (0.999999999-1, automatic), libglew2.0:amd64 (2.0.0-5, automatic), inkscape:amd64 (0.92.3-1, automatic), python3-pyqt5.qtsvg:amd64 (5.10.1+dfsg-1ubuntu2, automatic), python-bs4:amd64 (4.6.0-1, automatic), libtbb2:amd64 (2017~U7-8, automatic), scour:amd64 (0.36-2, automatic), libjemalloc1:amd64 (3.6.0-11, automatic), openshot:amd64 (2.4.1-2build2), libopenshot-audio6:amd64 (0.1.5+dfsg1-1, automatic), libopenimageio1.7:amd64 (1.7.17~dfsg0-1ubuntu2, automatic), libgc1c2:amd64 (1:7.4.2-8ubuntu1, automatic), libjsoncpp1:amd64 (1.7.4-3, automatic), libopencv-core3.2:amd64 (3.2.0+dfsg-4ubuntu0.1, automatic), openshot-qt:amd64 (2.4.1-2build2, automatic), libwmf-bin:amd64 (0.2.8.4-12, automatic), libspnav0:amd64 (0.2.3-1, automatic), libyaml-cpp0.5v5:amd64 (0.5.2-4ubuntu1, automatic), python-numpy:amd64 (1:1.13.3-2ubuntu1, automatic), libopencv-videoio3.2:amd64 (3.2.0+dfsg-4ubuntu0.1, automatic), libcharls1:amd64 (1.1.0+dfsg-2, automatic), libsigsegv2:amd64 (2.12-1, automatic)[/FONT]

Thanks.

---

### Post by cellsite60 on 2019-07-14
This might do the trick:
```
sudu apt purge openshot
sudo apt autoremove
```

If you want to go a little more in depth you can take a look **-->** **[here]("https://chrisjean.com/finding-and-purging-unpurged-packages-on-ubuntu/") <--**

---

### Post by kpatz on 2019-07-14
Add --purge to autoremove to completely purge the dependencies:
```
sudo apt purge openshot
sudo apt --purge autoremove
```

---

### Post by ardouronerous on 2019-07-14
Okay, I did:

```
sudo apt purge openshot
sudo apt --purge autoremove
```

While it did purge a lot of the software listed, but not all were removed though, like inkscape for example.

---

### Post by HermanAB on 2019-07-14
Bear in mind that uninstalling things, is bit like trying to unscramble an egg.

One thing I learned, is to never uninstall anything, since the risk of ending up with a screwed up system is just too high.

---

### Post by VMC on 2019-07-14
> **cellsite60 said:**
> This might do the trick:
```
sudu apt purge openshot
sudo apt autoremove
```

If you want to go a little more in depth you can take a look **-->** **[here]("https://chrisjean.com/finding-and-purging-unpurged-packages-on-ubuntu/") <--**
Interesting link you provided. Thanks.

---

