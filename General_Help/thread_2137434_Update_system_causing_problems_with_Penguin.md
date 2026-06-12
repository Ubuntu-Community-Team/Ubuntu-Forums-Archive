---
title: "Update system causing problems with Penguin"
date: 2013-04-20
forum: General Help
---

### Post by phantom21 on 2013-04-20
During an update process a problem occurred.  Update didn't complete and now I have a problem.

The system works, but I'm concerned the enduser will come up with something when she comes back from vaca so I'd prefer to fix it now if possible.

the errors are as follows after typing sudo apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libopenal1:i386 bluez-alsa:i386 libsdl-ttf2.0-0:i386 libgconf-2-4:i386
  libstdc++5:i386 ia32-libs-multiarch:i386 libqt4-declarative:i386
  libgail18:i386 libldap-2.4-2:i386 libao-common libv4l-0:i386 liblcms1:i386
  libunity6 libqt4-qt3support:i386 libroken18-heimdal:i386 libunistring0:i386
  libcupsimage2:i386 libgphoto2-port0:i386 libnss3:i386 libwrap0:i386
  libcaca0:i386 gtk2-engines:i386 libgudev-1.0-0:i386 libsamplerate0:i386
  libcdparanoia0:i386 libcairo-gobject2:i386 libavc1394-0:i386 ia32-libs
  libdrm-radeon1:i386 libaio1:i386 libsane:i386 odbcinst1debian2:i386
  libqt4-test:i386 libqt4-script:i386 libqt4-designer:i386
  libsdl-mixer1.2:i386 libqt4-network:i386 libxxf86vm1:i386 libcap2:i386
  libproxy1:i386 ibus-gtk:i386 libdbus-glib-1-2:i386 libgl1-mesa-dri:i386
  libtdb1:i386 libxcb-glx0:i386 libasn1-8-heimdal:i386 libgl1-mesa-glx:i386
  libspeex1:i386 libjack-jackd2-0:i386 libxslt1.1:i386 libgomp1:i386
  libcapi20-3:i386 libibus-1.0-0:i386 libx11-xcb1:i386 libglapi-mesa:i386
  libgssapi3-heimdal:i386 libvisual-0.4-0:i386 libcanberra-gtk-module:i386
  libcanberra0:i386 gtk2-engines-murrine:i386 libwavpack1:i386
  libqt4-opengl:i386 libsoup-gnome2.4-1:i386 libv4lconvert0:i386
  gstreamer0.10-plugins-good:i386 lib32gcc1 libqt4-xmlpatterns:i386
  libiec61883-0:i386 libjson0:i386 libsdl-image1.2:i386 libdrm2:i386
  libwind0-heimdal:i386 libsdl1.2debian:i386 libxaw7:i386 libgdbm3:i386
  libcurl3:i386 libesd0:i386 libmikmod2:i386 acroread-common
  libdrm-nouveau1a:i386 libpulse-mainloop-glib0:i386 libtheora0:i386
  libaa1:i386 libspeexdsp1:i386 libieee1284-3:i386 libdrm-intel1:i386
  libao4:i386 libxmu6:i386 libcanberra-gtk0:i386 libvorbisfile3:i386
  libqt4-sql:i386 esound-common libasound2:i386 libxpm4:i386 libflac8:i386
  libqt4-svg:i386 libusb-0.1-4:i386 libgail-common:i386
  libhcrypto4-heimdal:i386 liborc-0.4-0:i386 libraw1394-11:i386 libnspr4:i386
  libshout3:i386 libdv4:i386 libhx509-5-heimdal:i386 libvorbisenc2:i386
  libasyncns0:i386 gstreamer0.10-x:i386 libgettextpo0:i386 libxss1:i386
  libgd2-xpm:i386 libheimbase1-heimdal:i386 libsdl-net1.2:i386
  libvisual-0.4-plugins:i386 libgstreamer-plugins-base0.10-0:i386
  libgnome-keyring0:i386 libxtst6:i386 gtk2-engines-pixbuf:i386 libqtgui4:i386
  libtag1c2a:i386 libssl0.9.8:i386 libmpg123-0:i386 libmad0:i386
  libsasl2-2:i386 gtk2-engines-oxygen:i386 lib32z1 xaw3dg:i386 libpulse0:i386
  libheimntlm0-heimdal:i386 libpulsedsp:i386 lib32stdc++6 libodbc1:i386
  libexif12:i386 libqt4-scripttools:i386 libglu1-mesa:i386 librtmp0:i386
  libvorbis0a:i386 libqtwebkit4:i386 libgstreamer0.10-0:i386 libxp6:i386
  libaudio2:i386 libxv1:i386 libsasl2-modules:i386
  gstreamer0.10-plugins-base:i386 libsndfile1:i386 libsqlite3-0:i386
  libmng1:i386 libltdl7:i386 libkrb5-26-heimdal:i386 libasound2-plugins:i386
  glib-networking:i386 libllvm3.0:i386 libsoup2.4-1:i386 libgphoto2-2:i386
  libogg0:i386 libtag1-vanilla:i386 libaudiofile1:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-generic
The following packages will be upgraded:
  linux-generic
1 upgraded, 0 newly installed, 0 to remove and 34 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,722 B of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.36.43); however:
  Version of linux-image-generic on system is 3.2.0.40.48.
 linux-generic depends on linux-headers-generic (= 3.2.0.36.43); however:
  Version of linux-headers-generic on system is 3.2.0.40.48.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


and the following after sudp dpkg --configure -a
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.36.43); however:
  Version of linux-image-generic on system is 3.2.0.40.48.
 linux-generic depends on linux-headers-generic (= 3.2.0.36.43); however:
  Version of linux-headers-generic on system is 3.2.0.40.48.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-generic


Want to stay with 12.04 since it's LTS.

Any help apprecidated.

Mark

---

### Post by grahammechanical on 2013-04-20
Do you really mean Penguin or Precise Pangolin? You should have Synaptic Package Manager installed. Open it and search for kernel. Look through the list for anything related to Linux 3.2.0.36.43 or 3.2.0.40.48 you may find that some are marked with a grey icon indicating that they are due to be upgraded. A right click will let you mark them for upgrade.

What is strange is that you are trying to install an older kernel. Linux 3.2.0.36.43 is older than Linux 3.2.0.40.48. That is what is causing the problem. You are missing some of the bits and pieces for Linux 3.2.0.36.43

Can you access the Grub menu? At the menu select the normal line that boots Ubuntu and press E. That will put Grub into Edit mode and you can examine the boot parameters to see what kernel is being booted. Press Esc to back out of Edit mode or F10 to boot.

If you run this ```
[COLOR=#000000]apt-get autoremove[/COLOR]
```[COLOR=#000000]

then all those non-required packages will be removed.


[/COLOR]

---

### Post by phantom21 on 2013-04-21
Yes, Precise Penguin, ubuntu 12.04.  Have already tried sudo apt-get autoremove.

This problem arose through an incomplete update.

I will try the steps you suggest in synaptic.  Will report when I have.  Thanks.

---

### Post by phantom21 on 2013-05-26
Finally got to the machine and try your fix.  Unfortunately it did not help.  And, I'm getting a MaxReport reached message so an error report isn't being generated.

Can you suggest something more?

Tbanks,
Mark

---

### Post by phantom21 on 2013-05-26
Oh, I should say I did an apt-get -f autoremove first, then an apt-get -f install, which got the message I described re MaxReport, then I went to synaptic tried to do the updates.  It said it had some broken packages, which I tried to apply the fix, and it wouldn't .  I also did a sudo dpkg --configure -a and this also returned an error.

---

