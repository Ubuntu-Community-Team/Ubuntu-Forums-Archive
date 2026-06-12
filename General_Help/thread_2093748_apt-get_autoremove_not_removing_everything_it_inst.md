---
title: "apt-get autoremove not removing everything it installed"
date: 2012-12-11
forum: General Help
---

### Post by latestversion on 2012-12-11
I installed digikam and got the following output from apt-get. Immediately after, I uninstalled digikam, but when I did it only  uninstalled some of the many dependencies it installed a few moments  earlier (output shown at end of this post). For example, konqueror remains, as do several other packages.  Am I doing something wrong, or am I misunderstanding the use of  'autoremove'?

```
$ sudo apt-get install digikam
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  digikam-data dolphin enblend enfuse freeglut3 gpsd graphicsmagick graphicsmagick-imagemagick-compat hugin hugin-data hugin-tools kde-baseapps-bin kde-baseapps-data kipi-plugins kipi-plugins-common
  konqueror konqueror-nsplugins libaudiofile1 libboost-filesystem1.46.1 libboost-regex1.46.1 libboost-signals1.46.1 libboost-system1.46.1 libboost-thread1.46.1 libesd0 libglew1.5 libgps20
  libgraphicsmagick3 libimage-exiftool-perl libkcalcore4 libkdcraw-data libkdcraw20 libkexiv2-10 libkexiv2-data libkface-data libkface1 libkgeomap-data libkgeomap1 libkipi-data libkipi8 libkonq-common
  libkonq5-templates libkonq5abi1 libkonqsidebarplugin4a libksane-data libksane0 libkvkontakte1 liblensfun-data liblensfun0 liblqr-1-0 libmarblewidget13 libopencv-calib3d2.3 libopencv-features2d2.3
  libopencv-flann2.3 libopencv-legacy2.3 libopencv-objdetect2.3 libopencv-video2.3 libpano13-2 libpano13-bin libplot2c2 libqjson0 libsvga1 libvdpau1 libzthread-2.3-2 marble-data marble-plugins mplayer
  mplayerthumbs
Suggested packages:
  digikam-doc kdesdk-dolphin-plugins kfind ruby konsole kompare gpsd-clients graphicsmagick-dbg python-wxgtk2.8 autopano-sift-c autopano-sift gallery gimp kmail vorbis-tools konq-plugins
  pulseaudio-esound-compat glew-utils1.5 nvidia-vdpau-driver nvidia-vdpau-driver-ia32 vdpau-driver mplayer-doc netselect fping
The following NEW packages will be installed:
  digikam digikam-data dolphin enblend enfuse freeglut3 gpsd graphicsmagick graphicsmagick-imagemagick-compat hugin hugin-data hugin-tools kde-baseapps-bin kde-baseapps-data kipi-plugins
  kipi-plugins-common konqueror konqueror-nsplugins libaudiofile1 libboost-filesystem1.46.1 libboost-regex1.46.1 libboost-signals1.46.1 libboost-system1.46.1 libboost-thread1.46.1 libesd0 libglew1.5
  libgps20 libgraphicsmagick3 libimage-exiftool-perl libkcalcore4 libkdcraw-data libkdcraw20 libkexiv2-10 libkexiv2-data libkface-data libkface1 libkgeomap-data libkgeomap1 libkipi-data libkipi8
  libkonq-common libkonq5-templates libkonq5abi1 libkonqsidebarplugin4a libksane-data libksane0 libkvkontakte1 liblensfun-data liblensfun0 liblqr-1-0 libmarblewidget13 libopencv-calib3d2.3
  libopencv-features2d2.3 libopencv-flann2.3 libopencv-legacy2.3 libopencv-objdetect2.3 libopencv-video2.3 libpano13-2 libpano13-bin libplot2c2 libqjson0 libsvga1 libvdpau1 libzthread-2.3-2 marble-data
  marble-plugins mplayer mplayerthumbs
0 upgraded, 68 newly installed, 0 to remove and 42 not upgraded.
Need to get 68.4 MB of archives.
After this operation, 221 MB of additional disk space will be used.

```This is the output from uninstalling digikam:

```
~$ sudo apt-get remove digikam
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libkface-data kipi-plugins libkvkontakte1 libboost-filesystem1.46.1 libkface1 libksane0 libkcalcore4 kipi-plugins-common libopencv-legacy2.3 enblend libkexiv2-data libkipi8 libkipi-data enfuse libsvga1
  libopencv-objdetect2.3 libopencv-calib3d2.3 libglew1.5 libboost-system1.46.1 libmarblewidget13 libopencv-features2d2.3 libplot2c2 mplayer libboost-signals1.46.1 libgps20 libpano13-bin
  libopencv-video2.3 libkdcraw-data digikam-data liblqr-1-0 marble-plugins libqjson0 hugin-data libopencv-flann2.3 hugin liblensfun-data libboost-thread1.46.1 libpano13-2 liblensfun0 libkexiv2-10
  mplayerthumbs libvdpau1 libksane-data gpsd libkdcraw20 libkgeomap-data marble-data libkgeomap1 libboost-regex1.46.1 freeglut3 libimage-exiftool-perl libzthread-2.3-2 hugin-tools
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  digikam
0 upgraded, 0 newly installed, 1 to remove and 42 not upgraded.
After this operation, 16.0 MB disk space will be freed.

```

---

### Post by debodas on 2012-12-11
try typing ```
sudo apt-get purge digikam
``` into the terminal and running it.

Then use ```
sudo apt-get autoremove
```

If things are still left after this, it will be because something else uses them.

---

### Post by latestversion on 2012-12-11
I ran the autoremove command and it removes the packages that it says it will remove above in the 'sudo apt-get purge digikam' output, but that list of packages is smaller than the packages that it installed while doing 'sudo apt-get install digikam'. That leads to my confusion about how autoremove works.

---

### Post by ibjsb4 on 2012-12-11
This any help

[https://help.ubuntu.com/community/AptGet/Howto#Removal_commands](https://help.ubuntu.com/community/AptGet/Howto#Removal_commands)

---

### Post by vasa1 on 2012-12-11
BTW, I'd also be concerned about:```
0 upgraded, 68 newly installed, 0 to remove and 42 not upgraded.
```and```
0 upgraded, 0 newly installed, 1 to remove and 42 not upgraded.
```
Why are you seeing 42 not upgraded? I would suggest that you do a dist-upgrade **but wait for or ask an expert to guide you on this**.

And I too get the feeling that install is not cleanly reversed by purge or autoremove (leaving files created in the home folder aside). That's why I like the six month "cadence": cleans out the stables ;)

---

