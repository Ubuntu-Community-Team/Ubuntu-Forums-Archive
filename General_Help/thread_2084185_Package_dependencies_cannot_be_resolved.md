---
title: "Package dependencies cannot be resolved"
date: 2012-11-14
forum: General Help
---

### Post by eslavko on 2012-11-14
Hello....

Seems that I'm managed to mess package's
When I tried (many) version of avidemux now I can't install any more as Package dependencies cannot be resolved
Here are the details:

```
The following packages have unmet dependencies:

avidemux-plugins-qt: Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
                     Depends: libqtcore4 (>= 4:4.7.0~beta1) but 4:4.8.1-0ubuntu4.3 is to be installed
                     Depends: libqtgui4 (>= 4:4.5.3) but 4:4.8.1-0ubuntu4.3 is to be installed

```How to solve that problem?!?

When I check i have libgcc1 and libgcc1:i386 installed, and same for libqtcore4 and libqtgui.  If I try to remove that I got a bunch of application to be deleted, so I didnt remove that.

help!

Slavko.

Ubuntu 12.04 64 bit.

---

### Post by ibjsb4 on 2012-11-14
I do not see anything wrong with what you posted.

>=  Greater than or equal to and that's the way all three read to me.

Where did the 386 reference come from?

---

### Post by eslavko on 2012-11-15
I don't know when I got i386 versions...
But if I try to remove it I got just the scarry list what will goes wrong too...

```
slavko@ePodstresnik:~$ sudo apt-get remove libgcc1:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libpthread-stubs0:i386 libaio1:i386 transcode-doc liblzo2-2 transcode
  libavidemux0 libpthread-stubs0-dev:i386
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bluez-alsa:i386 devede glib-networking:i386 gstreamer0.10-plugins-base:i386
  gstreamer0.10-plugins-good:i386 gstreamer0.10-x:i386 gtk2-engines:i386
  gtk2-engines-murrine:i386 gtk2-engines-oxygen:i386 gtk2-engines-pixbuf:i386
  gvfs:i386 gvfs-libs:i386 harbour:i386 ia32-libs ia32-libs-multiarch:i386
  ibus-gtk:i386 inkscape libaa1:i386 libacl1:i386 libao4:i386
  libasn1-8-heimdal:i386 libasound2:i386 libasound2-plugins:i386
  libasyncns0:i386 libatk1.0-0:i386 libattr1:i386 libaudio2:i386
  libaudiofile1:i386 libavahi-client3:i386 libavahi-common3:i386
  libavc1394-0:i386 libbz2-1.0:i386 libc6:i386 libcaca0:i386
  libcairo-gobject2:i386 libcairo2:i386 libcanberra-gtk-module:i386
  libcanberra-gtk0:i386 libcanberra0:i386 libcap2:i386 libcapi20-3:i386
  libcdparanoia0:i386 libcomerr2:i386 libcroco3:i386 libcups2:i386
  libcupsimage2:i386 libcurl3:i386 libdatrie1:i386 libdb5.1:i386
  libdbus-1-3:i386 libdbus-glib-1-2:i386 libdbusmenu-qt2:i386 libdrm-dev:i386
  libdrm-intel1:i386 libdrm-nouveau1a:i386 libdrm-radeon1:i386 libdrm2:i386
  libdv4:i386 libesd0:i386 libexif12:i386 libexpat1:i386 libffi6:i386
  libflac8:i386 libfontconfig1:i386 libfreetype6:i386 libgail-common:i386
  libgail18:i386 libgcc1:i386 libgconf-2-4:i386 libgcrypt11:i386
  libgd2-xpm:i386 libgdbm3:i386 libgdk-pixbuf2.0-0:i386 libgettextpo0:i386
  libgif4:i386 libgl1-mesa-dev:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:i386
  libglapi-mesa:i386 libglib2.0-0:i386 libglu1-mesa:i386 libglu1-mesa-dev:i386
  libgnome-keyring0:i386 libgnutls26:i386 libgomp1:i386 libgpg-error0:i386
  libgphoto2-2:i386 libgphoto2-port0:i386 libgpm2:i386 libgssapi-krb5-2:i386
  libgssapi3-heimdal:i386 libgstreamer-plugins-base0.10-0:i386
  libgstreamer0.10-0:i386 libgtk2.0-0:i386 libgudev-1.0-0:i386
  libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386
  libhx509-5-heimdal:i386 libibus-1.0-0:i386 libice6:i386 libidn11:i386
  libiec61883-0:i386 libieee1284-3:i386 libjack-jackd2-0:i386 libjasper1:i386
  libjpeg-turbo8:i386 libjpeg8:i386 libjson0:i386 libk5crypto3:i386
  libkeyutils1:i386 libkms1:i386 libkrb5-26-heimdal:i386 libkrb5-3:i386
  libkrb5support0:i386 liblcms1:i386 libldap-2.4-2:i386 libllvm3.0:i386
  libltdl7:i386 libmad0:i386 libmikmod2:i386 libmng1:i386 libmpg123-0:i386
  libmysqlclient18:i386 libncurses5:i386 libncursesw5:i386 libnspr4:i386
  libnss3:i386 libodbc1:i386 libogg0:i386 libopenal1:i386 liborc-0.4-0:i386
  libosmesa6:i386 libp11-kit0:i386 libpango1.0-0:i386 libpciaccess0:i386
  libpcre3:i386 libpixman-1-0:i386 libpng12-0:i386 libproxy1:i386
  libpulse-mainloop-glib0:i386 libpulse0:i386 libpulsedsp:i386
  libqt4-dbus:i386 libqt4-declarative:i386 libqt4-designer:i386
  libqt4-network:i386 libqt4-opengl:i386 libqt4-qt3support:i386
  libqt4-script:i386 libqt4-scripttools:i386 libqt4-sql:i386
  libqt4-sql-mysql:i386 libqt4-svg:i386 libqt4-test:i386 libqt4-xml:i386
  libqt4-xmlpatterns:i386 libqtcore4:i386 libqtgui4:i386 libqtwebkit4:i386
  libraw1394-11:i386 libroken18-heimdal:i386 librsvg2-2:i386
  librsvg2-common:i386 librtmp0:i386 libsamplerate0:i386 libsane:i386
  libsasl2-2:i386 libsasl2-modules:i386 libsdl-image1.2:i386
  libsdl-mixer1.2:i386 libsdl-net1.2:i386 libsdl-ttf2.0-0:i386
  libsdl1.2debian:i386 libselinux1:i386 libshout3:i386 libslang2:i386
  libsm6:i386 libsndfile1:i386 libsoup-gnome2.4-1:i386 libsoup2.4-1:i386
  libspeex1:i386 libspeexdsp1:i386 libsqlite3-0:i386 libssl0.9.8:i386
  libssl1.0.0:i386 libstdc++5:i386 libstdc++6:i386 libtag1-vanilla:i386
  libtag1c2a:i386 libtasn1-3:i386 libtdb1:i386 libthai0:i386 libtheora0:i386
  libtiff4:i386 libtinfo5:i386 libudev0:i386 libunistring0:i386
  libusb-0.1-4:i386 libuuid1:i386 libv4l-0:i386 libv4lconvert0:i386
  libvisual-0.4-0:i386 libvisual-0.4-plugins:i386 libvorbis0a:i386
  libvorbisenc2:i386 libvorbisfile3:i386 libwavpack1:i386
  libwind0-heimdal:i386 libwrap0:i386 libx11-6:i386 libx11-dev:i386
  libx11-xcb1:i386 libxau-dev:i386 libxau6:i386 libxaw7:i386 libxcb-glx0:i386
  libxcb-render0:i386 libxcb-shm0:i386 libxcb1:i386 libxcb1-dev:i386
  libxcomposite1:i386 libxcursor1:i386 libxdamage1:i386 libxdmcp-dev:i386
  libxdmcp6:i386 libxext-dev:i386 libxext6:i386 libxfixes3:i386 libxft2:i386
  libxi6:i386 libxinerama1:i386 libxml2:i386 libxmu6:i386 libxp6:i386
  libxpm-dev:i386 libxpm4:i386 libxrandr-dev:i386 libxrandr2:i386
  libxrender-dev:i386 libxrender1:i386 libxslt1.1:i386 libxss1:i386
  libxt6:i386 libxtst6:i386 libxv1:i386 libxxf86vm1:i386 mencoder
  mesa-common-dev:i386 odbcinst1debian2:i386 skype skype-bin:i386 sni-qt:i386
  tovid w32codecs:i386 wine1.5 wine1.5-amd64 wine1.5-i386:i386 xaw3dg:i386
  zlib1g:i386
0 upgraded, 0 newly installed, 260 to remove and 2 not upgraded.
After this operation, 709 MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

```


how to fix that mess.

---

### Post by varunendra on 2012-11-16
Wow!! Huge list there ! :)

Actually that seems normal to me. Almost all of them come altogether when you install "ia32-libs" package, which is a 32-bit library for applications that depend on 32-bit packages. For example wine. In your case, it may be skype, if not wine or anything else, that I can see in that list.

I don't think it should cause any conflicts with the regular packages though. What happens if you just do -
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install avidemux
```

If it still returns errors, please post the output of -
```
ls -1 /etc/apt/sources.list.d/
grep -hR ^deb /etc/apt/sources.list.d/
```

---

### Post by eslavko on 2012-11-16
Yes I have wine installed.

The problem seems to came when I install nightly build of avidemux and have wrong reprosity. 

I don't really know how I managed to do (and undo) that. So system now behave as healthy. 

Thanks for support.

---

### Post by eslavko on 2012-11-16
> **stanfidavid said:**
> I do not see anything wrong with what you posted.[IMG]<snip>[/IMG]

seems nothing wrong, but installer refuse to install !

---

