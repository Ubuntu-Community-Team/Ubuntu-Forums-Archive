---
title: "I screwed up QT5"
date: 2020-01-06
forum: General Help
---

### Post by Dukenukemx on 2020-01-06
I was trying to upgrade QT using [this PPA.](https://launchpad.net/~beineri/+archive/ubuntu/opt-qt-5.12.6-bionic) and now I get this error when running any QT based application like VLC.  I've removed the PPA and anything I installed with it, but this error remains.  Anyone know how I can fix this or reinstall the default version of QT5 that comes with Ubuntu 18.04?  

```

qt.qpa.plugin: Could not load the Qt platform plugin "xcb" in "" even though it was found.
This application failed to start because no Qt platform plugin could be initialized. Reinstalling the application may fix this problem.

Available platform plugins are: linuxfb, minimal, offscreen, vnc, wayland, wayland-xcomposite-glx, xcb, eglfs, minimalegl, wayland-egl, wayland-xcomposite-egl.

Aborted (core dumped)
```

---

### Post by Dukenukemx on 2020-01-06
I tried with QT_DEBUG_PLUGINS=1 and got this error.

```

Got keys from plugin meta data ("xcb")
QFactoryLoader::QFactoryLoader() checking directory path "/usr/bin/platforms" ...
Cannot load library /opt/qt512/plugins/platforms/libqxcb.so: (/opt/qt512/plugins/platforms/../../lib/libQt5XcbQpa.so.5: symbol _ZN11QFontEngine9glyphDataEj6QFixedNS_11GlyphFormatERK10QTransform version Qt_5_PRIVATE_API not defined in file libQt5Gui.so.5 with link time reference)
QLibraryPrivate::loadPlugin failed on "/opt/qt512/plugins/platforms/libqxcb.so" : "Cannot load library /opt/qt512/plugins/platforms/libqxcb.so: (/opt/qt512/plugins/platforms/../../lib/libQt5XcbQpa.so.5: symbol _ZN11QFontEngine9glyphDataEj6QFixedNS_11GlyphFormatERK10QTransform version Qt_5_PRIVATE_API not defined in file libQt5Gui.so.5 with link time reference)"
qt.qpa.plugin: Could not load the Qt platform plugin "xcb" in "" even though it was found.
This application failed to start because no Qt platform plugin could be initialized. Reinstalling the application may fix this problem.

Available platform plugins are: linuxfb, minimal, offscreen, vnc, wayland, wayland-xcomposite-glx, xcb.

Aborted (core dumped)

```

---

### Post by spjackson on 2020-01-07
The link you provide for the PPA indicates that the package installs everything in /opt. It says "Source /opt/qt512/bin/qt512-env.sh to set the correct environment."

My take on that is that the assets installed by the original Qt packages should still be in place (/usr/lib/x86_64-linux-gnu/libQt5*.so* and /usr/lib/x86_64-linux-gnu/qt5/plugins/platforms/* etc.). The fact that it is still looking in /opt/qt512/plugins/platforms indicates that some part of your environment is still pointing at the installation in /opt. What you need to do to access the original assets is to NOT source /opt/qt512/bin/qt512-env.sh. If it's not your environment, maybe there's something in .config or .cache or somewhere pointing at /opt, but I would think it's more likely to be your environment.

---

### Post by Dukenukemx on 2020-01-08
I solved the problem. I realized that I had updated the PPA from QT5.12 to 5.12.3 to 5.12.6. Doing an "apt remove qt512-meta-full" does not remove the /opt/qt512 folder. So it was just overwriting files when I updated QT. I had to do a ppa purge "sudo ppa-purge -d bionic ppa:beineri/opt-qt-5.12.3-bionic" of the PPA and delete /opt/qt512 folder and then reinstall qt512-meta-full and now everything is fine. So now VLC, Dolphin and even Yuzu works without needing to do the export LD_LIBRARY_PATH thing. Figures my desire to keep things up to date had broken it.

---

