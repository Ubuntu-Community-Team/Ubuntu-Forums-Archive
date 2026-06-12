---
title: "how do I install the dependencies kdenlive needs to be installed"
date: 2013-01-19
forum: General Help
---

### Post by Bushcraft Bill on 2013-01-19
great did an update and it deleted kdenlive and this is what I get when I now try and re-install how do I get these unmet dependencies files back ?


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 kdenlive : Depends: libqjson0 (>= 0.7.1) but it is not installable
            Depends: kdenlive-data (= 0.9.3+git20130109.e070d4a4-0ubuntu0~sunab~precise1) but 0.9.3+git20130117.91ea0353-0ubuntu0~sunab~precise1 is to be installed
            Depends: dvgrab but it is not installable
            Depends: recordmydesktop but it is not installable
E: Unable to correct problems, you have held broken packages.

---

### Post by tgalati4 on 2013-01-19
tgalati4@Dell600m-mint14 ~ $ apt-cache depends kdenlive
kdenlive
  Depends: kde-runtime
  Depends: libc6
  Depends: libgcc1
 |Depends: libgl1-mesa-glx
  Depends: <libgl1>
    libgl1-mesa-glx
 |Depends: libglu1-mesa
  Depends: <libglu1>
    libglu1-mesa
  Depends: libkdecore5
  Depends: libkdeui5
  Depends: libkio5
  Depends: libknewstuff3-4
  Depends: libknotifyconfig4
  Depends: libmlt++3
  Depends: libmlt5
  Depends: libnepomuk4
  Depends: libqjson0
  Depends: libqt4-dbus
  Depends: libqt4-opengl
  Depends: libqt4-script
  Depends: libqt4-svg
  Depends: libqt4-xml
  Depends: libqtcore4
  Depends: libqtgui4
  Depends: libsolid4
  Depends: libstdc++6
  Depends: libx11-6
  Depends: kdenlive-data
  Depends: melt
  Depends: ffmpeg
  Recommends: swh-plugins
  Recommends: dvgrab
  Recommends: frei0r-plugins
  Recommends: recordmydesktop
  Recommends: dvdauthor
  Recommends: genisoimage

Did you manually install any *.debs or added a ppa?  It looks like an update was performed, but the original package wants the original kdenlive-data package.  Perhaps it is a packaging error?

---

### Post by tgalati4 on 2013-01-19
Open a terminal:

```
sudo apt-get install --fix-broken kdenlive
```

Post any error messages.

---

