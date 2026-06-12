---
title: "Unmet dependencies &amp; wants to remove a bunch of packages"
date: 2013-03-20
forum: General Help
---

### Post by Cesaar on 2013-03-20
Hi all.
 I decided to use steam and buy a game on my 64bit ubuntu 12.10, so I thought I should free up some disk space by removing some packages. I went ahead and removed some of the many linux-image-3.*.*-*-generic that I had, leaving only the last two that were installed (3.5.0-25 and 3.5.0-26). Removing them proved to be a bad choice, since that caused the automatic removal of a few other packages. From running: ```
cat /var/log/dpkg.log | grep remove
```
I get (the packages that were automatically removed when removing the linux images):
```
2013-03-20 00:05:46 startup packages remove
2013-03-20 00:05:46 remove teamviewer:amd64 8.0.16675 <none>
2013-03-20 00:05:58 remove ia32-libs:amd64 20090808ubuntu36 <none>
2013-03-20 00:05:59 remove ia32-libs-multiarch:i386 20090808ubuntu36 <none>
2013-03-20 00:05:59 remove libgl1-mesa-dri:i386 9.0.2-0ubuntu0.1 <none>
2013-03-20 00:06:00 remove shatter:amd64 1347954459-0ubuntu3 <none>
2013-03-20 00:06:01 remove shatter-bin:i386 1347954459-0ubuntu3 <none>
2013-03-20 00:06:03 remove libqt4-opengl:i386 4:4.8.3+dfsg-0ubuntu3.1 <none>
2013-03-20 00:06:04 remove libvisual-0.4-plugins:i386 0.4.0.dfsg.1-7build1 <none>
2013-03-20 00:06:05 remove libglu1-mesa:i386 9.0.0-0ubuntu1 <none>
2013-03-20 00:06:05 remove libgl1-mesa-glx:i386 9.0.2-0ubuntu0.1 <none>
2013-03-20 00:06:06 remove libosmesa6:i386 9.0.2-0ubuntu0.1 <none>
2013-03-20 00:06:07 remove libglapi-mesa:i386 9.0.2-0ubuntu0.1 <none>
2013-03-20 00:06:09 remove wine1.4:amd64 1.4.1-0ubuntu1 <none>
2013-03-20 00:06:11 remove wine1.4-amd64:amd64 1.4.1-0ubuntu1 <none>
2013-03-20 00:06:12 remove wine1.4-i386:i386 1.4.1-0ubuntu1 <none>
2013-03-20 00:06:12 remove wine1.4-common:all 1.4.1-0ubuntu1  <none>
```

Well, I decided to deal with those removed packages later -- I eyeballed them and they seemed non essential packages -- so I tried to run Steam. But Steam told me that it needed to install 2 packages: libgl1-mesa-dri:i386 and libgl1-mesa-glx:i386. (see above, they were removed).
So I tried to reinstall them: I ran ```
sudo apt-get install libgl1-mesa-dri:i386 libgl1-mesa-glx:i386
``` And.. it went crazy wanting to remove a bunch of packages that I need:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dcraw enfuse exiftran hugin-data kde-baseapps-data kiki-the-nano-bot-data
  libarpack2 libboost-python1.49.0 libboost-thread1.49.0 libccolamd2.7.1
  libcholmod1.7.1 libcolamd2.7.1 libcxsparse2.2.3 libgl2ps0 libglpk0
  libgraphicsmagick++3 libgraphicsmagick3 libhdf5-7 libibverbs1
  libimage-exiftool-perl libmikmod2 libopenmpi1.3 libpano13-2 libpano13-bin
  libparpack2 libplot2c2 libqhull5 libqrupdate1 libsdl-mixer1.2 libsdl-net1.2
  libsdl-sound1.2 libtiff-tools libtorque2 libzthread-2.3-2 octave-common
  octave-htmldoc octave-info phatch-cli python-pyexiv2 python-pyexiv2-doc
  texinfo ttf-thai-tlwg xcftools
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libglapi-mesa:i386
Suggested packages:
  libglide3:i386
The following packages will be REMOVED:
  account-plugin-aim account-plugin-jabber account-plugin-salut
  account-plugin-yahoo apturl asymptote audacity bastion bittriprunner brasero
  cave-story-plus celestia-gnome cheese clementine closure compiz compiz-gnome
  compiz-plugins compiz-plugins-default compiz-plugins-main-default
  compizconfig-backend-gconf dosbox electricsheep empathy enblend eog
  evolution-data-server freeglut3 gimp gir1.2-clutter-1.0
  gir1.2-clutter-gst-2.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-gdata-0.0
  gir1.2-goa-1.0 gir1.2-gtkclutter-1.0 gir1.2-rb-3.0 gir1.2-totem-1.0
  gir1.2-ubuntuoneui-3.0 gir1.2-webkit-3.0 gnome-contacts gnome-control-center
  gnome-control-center-signon gnome-font-viewer gnome-media
  gnome-online-accounts gnome-power-manager gnome-screensaver gnome-session
  gnome-session-bin gnome-settings-daemon gnome-sushi gnome-user-guide
  gnuplot-x11 google-talkplugin gvfs gvfs:i386 gvfs-backends gvfs-daemons
  gvfs-fuse gwibber hugin hugin-tools indicator-datetime indicator-power
  indicator-session jamestown kde-runtime kiki-the-nano-bot kolourpaint4
  kubuntu-debug-installer legend-of-grimrock libcheese-gtk23 libcheese7
  libclutter-1.0-0 libclutter-gst-1.0-0 libclutter-gst-2.0-0
  libclutter-gtk-1.0-0 libcogl-pango0 libcogl9 libedata-book-1.2-15
  libegl1-mesa libegl1-mesa-drivers libfltk1.1 libfolks-eds25 libftgl2 libgbm1
  libgdata13 libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libglee0d1
  libgles1-mesa libgles2-mesa libglew1.8 libglewmx1.8 libglu1-mesa
  libgnome-desktop-3-4 libgoa-1.0-0 libgtkglext1 libkactivities-bin
  libkactivities6 libmx-1.0-2 libnux-3.0-0 liboctave1 libosmesa6 libplasma3
  libprojectm2 libqt4-opengl libreoffice-ogltrans librhythmbox-core6
  libswt-glx-gtk-3-jni libtotem0 libubuntuoneui-3.0-1 libunity-2d-private0
  libunity-core-6.0-5 libvisual-0.4-plugins libwebkitgtk-1.0-0
  libwebkitgtk-3.0-0 libwxgtk2.8-0 libxatracker1 libyelp0
  lightdm-remote-session-freerdp lightdm-remote-session-uccsconfigure lives
  mcp-account-manager-uoa mencoder metacity mplayer nautilus nautilus-sendto
  nautilus-sendto-empathy nautilus-share nux-tools octave phatch phonon
  phonon-backend-gstreamer pia plasma-scriptengine-javascript python-soya
  python-wxgtk2.8 qapt-batch qtoctave rhythmbox rhythmbox-mozilla
  rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune
  rhythmbox-plugin-zeitgeist rhythmbox-plugins rhythmbox-ubuntuone shank2
  shotwell snapshot software-center steam:i386 steam-launcher stellarium totem
  totem-mozilla totem-plugins ubuntu-desktop ubuntu-docs
  ubuntuone-client-gnome unity unity-2d unity-2d-common unity-2d-panel
  unity-2d-shell unity-2d-spread unity-common unity-greeter
  unity-lens-applications unity-lens-photos unity-scope-gdocs vlc vnc4server
  winetricks x11-utils xawtv xbase-clients xorg xserver-xorg-video-all
  xserver-xorg-video-vmware yelp zenity
The following NEW packages will be installed:
  libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 libglapi-mesa:i386
0 upgraded, 3 newly installed, 186 to remove and 2 not upgraded.
Need to get 3,012 kB of archives.
After this operation, 5,526 MB disk space will be freed.
Do you want to continue [Y/n]?
```

I gues that's a consequence of removing the linux images? I was able to reinstal the linux images that I had removed, but I still get the same crazy output when I try to reinstall the other packages. Dishartening at last, trying to reinstall some of the other removed packages (like ia32-libs:amd64) was not possible due to unavailable dependencies:
```
The following packages have unmet dependencies:
 ia32-libs : Depends: ia32-libs-multiarch
```

```
The following packages have unmet dependencies:
 ia32-libs-multiarch:i386 : Depends: gvfs:i386 but it is not going to be installed
```

```
The following packages have unmet dependencies:
 gvfs:i386 : Depends: gvfs-daemons:i386 (>= 1.14.0-0ubuntu6)
             Depends: gvfs-daemons:i386 (< 1.14.0-0ubuntu6.1~)
```

```
The following packages have unmet dependencies:
 gvfs-daemons:i386 : Depends: libsecret-1-0:i386 (>= 0.7) but it is not going to be installed
                     Recommends: policykit-1-gnome:i386 but it is not going to be installed
```

```
The following packages have unmet dependencies:
 libsecret-1-0:i386 : Depends: libsecret-common:i386 but it is not installable
```

```
Package libsecret-common:i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libsecret-common:i386' has no installation candidate
```

What could I do there?

---

### Post by schragge on 2013-03-20
The removed linux kernels are definitely not the problem. I guess additional packages having been removed is more of a coincidence. What exact error message do you get when trying to run Steam?

Also, what does *dpkg --print-foreign-architectures* show? If nothing then try
```
sudo dpkg --add-architecture i386
```
After that, try
```

sudo apt-get -f install
sudo apt-get install ia32-libs-multiarch

```

---

### Post by Cesaar on 2013-03-20
> **schragge said:**
> The removed linux kernels are definitely not the problem. I guess additional packages having been removed is more of a coincidence. What exact error message do you get when trying to run Steam?

Also, what does *dpkg --print-foreign-architectures* show? If nothing then try
```
sudo dpkg --add-architecture i386
```
After that, try
```

sudo apt-get -f install
sudo apt-get install ia32-libs-multiarch

```

Thanks for your answer. Well, it seems like it works now. I had restarted the computer before but to no avail. I restarted just now again and I was able to download the missing packages from before which is odd. Now steam starts up fine. :)

---

