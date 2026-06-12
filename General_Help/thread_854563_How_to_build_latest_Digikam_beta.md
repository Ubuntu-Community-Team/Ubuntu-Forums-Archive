---
title: "How to build latest Digikam beta?"
date: 2008-07-09
forum: General Help
---

### Post by dotancohen on 2008-07-09
On Kubuntu 8.04 in KDE 4.1 beta 2 I am trying to build Digikam 0.10 beta ([http://sourceforge.net/project/downloading.php?group_id=42641&use_mirror=osdn&filename=digikam-0.10.0-beta1.tar.bz2&5352905](http://sourceforge.net/project/downloading.php?group_id=42641&use_mirror=osdn&filename=digikam-0.10.0-beta1.tar.bz2&5352905)). The Install file says that instructions for building can be found at [http://techbase.kde.org/Getting_Started/Build/KDE4](http://techbase.kde.org/Getting_Started/Build/KDE4) however the instructs there are for building from SVN only. I tried running "./configure" but there is no configure script. How does one compile from source if there is no ./configure script?

---

### Post by kuja on 2008-09-29
Ran into this somewhat old thread while googling for something else ... reckon I might as well answer it.

KDE doesn't use autotools, it uses cmake instead. Now, assuming you have all dependencies in place, what you'll need to do will look something like this:

```

mkdir build
cd build
cmake ..
make
sudo make install

```

---

