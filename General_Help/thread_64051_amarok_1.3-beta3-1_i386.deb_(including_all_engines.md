---
title: "amarok_1.3-beta3-1_i386.deb (including all engines) + libtag1_1.4-0_i386.deb."
date: 2005-09-09
forum: General Help
---

### Post by xbaez on 2005-09-09
I am compiling
amarok_1.3-beta3-1_i386.deb (including all engines) + libtag1_1.4-0_i386.deb.

This post is basically to see if people will be willing to download these utilities from my website [http://downloads.gamingaccess.com](http://downloads.gamingaccess.com) (see the reasons why I can't make it as easy as apt-get below)

This one includes:
==========================
=== amaroK - PLUGINS ================================================== ======
==========================
=
= The following extra functionality will be included:
= + aRts-engine
= + GStreamer-engine
= + MAS-engine
= + Helix-engine
= + MySql support
= + Konqueror Sidebar
=
================================================== =============================

I can upload it to my website
[http://downloads.gamingaccess.com](http://downloads.gamingaccess.com)
but I will first like to see if people will be willing to go to my website and download it

I don't know and I don't have much time in order to make my site a repository for amarok, and the file I made is called:
amarok_1.3-beta3-1_i386.deb , it's version is 1.3-beta3
In order to make it "Ubuntu comptabile" it's version should be 2:1.3-beta3, the file should be called:
amarok_2%3a1.3-beta3-0ubuntu1~5.04ubp2_i386.deb

Anyway, installation is easy and I've used it for over a month now, and it works GREAT

All you have to do is
1) download the libtag and amarok .deb files (I can upload them today)
2) upgrade libtag with a .deb file I've already made
3) remove all the amarok deb files
4) install this one

The main feature that I like of amarok is that
1) You'll have lots of engines to chose and features:
= + MySQL Support apart from SQLite
= + aRts-engine
= + GStreamer-engine
= + MAS-engine
= + Helix-engine
= + MySql support
= + Konqueror Sidebar
2) One .deb file includes all these features, you can select the engine that works best (for me it's gstreamer with autoconf)
3) compatible with Ubuntu Hoary (and possible Breezy)
4) You can install plugins such as lyrics and have fetched lyrics for your songs, and you have a nice WIKI Information

I will open a new thread asking people if they will be willing to go to my site and download these, I haven't seen many .deb for amarok.

I will also like to learn how to make a .deb file with it's version 2:1.3-beta3

---

### Post by xbaez on 2005-09-09
Here are the dependencies of this .deb file:

artsbuilder (>= 4:3.4.0), kdelibs4 (>= 4:3.4.0), konqueror (>= 4:3.4.0), libart-2.0-2 (>= 2.3.16), libarts1 (>= 1.3.2), libasound2 (>> 1.0.8), libaudio2, libaudiofile0 (>= 0.2.3-4), libc6 (>= 2.3.2.ds1-4), libesd0 (>= 0.2.29-1) | libesd-alsa0 (>= 0.2.29-1), libflac6, libfontconfig1 (>= 2.2.1), libfreetype6 (>= 2.1.5-1), libgamin0, libgcc1 (>= 1:4.0.0-7), libglib1.2 (>= 1.2.0), libglib2.0-0 (>= 2.6.0), libgstreamer0.8-0 (>= 0.8.9-1), libgtk1.2 (>= 1.2.10-4), libice6 | xlibs (>> 4.1.0), libidn11 (>= 0.5.2), libjpeg62, libmusicbrainz4 (>= 2.1.1), libmysqlclient14 (>= 4.1.10a),libogg0 (>= 1.1.2), libpcre3 (>= 4.5), libpng12-0 (>= 1.2.8rel), libpopt0 (>= 1.7), libqt3c102-mt (>= 3:3.3.3), libsm6 | xlibs (>> 4.1.0), libstdc++5 (>= 1:3.3.4-1), libtag1 (>= 1.4-0), libtunepimp2 (>= 0.3.0), libvorbis0a (>= 1.0.1), libvorbisenc2 (>= 1.0.1), libvorbisfile3 (>= 1.0.1), libx11-6 | xlibs (>> 4.1.0), libxcursor1 (>> 1.1.2), libxext6 | xlibs (>> 4.1.0), libxft2 (>> 2.1.1), libxi6 | xlibs (>> 4.1.0), libxinerama1, libxml2 (>= 2.6.17), libxrandr2 | xlibs (>> 4.3.0), libxrender1, libxt6 | xlibs (>> 4.1.0), xmms, zlib1g (>= 1:1.2.1)

---

### Post by xbaez on 2005-09-12
[QUOTE=xbaez]Here are the dependencies of this .deb file:

artsbuilder (>= 4:3.4.0), kdelibs4 (>= 4:3.4.0), konqueror (>= 4:3.4.0), libart-2.0-2 (>= 2.3.16), libarts1 (>= 1.3.2), libasound2 (>> 1.0.8), libaudio2, libaudiofile0 (>= 0.2.3-4), libc6 (>= 2.3.2.ds1-4), libesd0 (>= 0.2.29-1) | libesd-alsa0 (>= 0.2.29-1), libflac6, libfontconfig1 (>= 2.2.1), libfreetype6 (>= 2.1.5-1), libgamin0, libgcc1 (>= 1:4.0.0-7), libglib1.2 (>= 1.2.0), libglib2.0-0 (>= 2.6.0), libgstreamer0.8-0 (>= 0.8.9-1), libgtk1.2 (>= 1.2.10-4), libice6 | xlibs (>> 4.1.0), libidn11 (>= 0.5.2), libjpeg62, libmusicbrainz4 (>= 2.1.1), libmysqlclient14 (>= 4.1.10a),libogg0 (>= 1.1.2), libpcre3 (>= 4.5), libpng12-0 (>= 1.2.8rel), libpopt0 (>= 1.7), libqt3c102-mt (>= 3:3.3.3), libsm6 | xlibs (>> 4.1.0), libstdc++5 (>= 1:3.3.4-1), libtag1 (>= 1.4-0), libtunepimp2 (>= 0.3.0), libvorbis0a (>= 1.0.1), libvorbisenc2 (>= 1.0.1), libvorbisfile3 (>= 1.0.1), libx11-6 | xlibs (>> 4.1.0), libxcursor1 (>> 1.1.2), libxext6 | xlibs (>> 4.1.0), libxft2 (>> 2.1.1), libxi6 | xlibs (>> 4.1.0), libxinerama1, libxml2 (>= 2.6.17), libxrandr2 | xlibs (>> 4.3.0), libxrender1, libxt6 | xlibs (>> 4.1.0), xmms, zlib1g (>= 1:1.2.1)[/QUOTE]
 Ok I've uploaded both files to my server, here is the link for you to download:
Here is the link
**[http://downloads.gamingaccess.com/index.php?cat_id=317](http://downloads.gamingaccess.com/index.php?cat_id=317)**

Amarok built by Xavier Baez, totally compatible with Ubuntu/Kubuntu Hoary Hedgegod 5.04 and possibly compatible with Breezy. The latest version of Amarok includes cool features such as WIKI, Lyrics (you can install plugins such as lyrics in order to have fetched lyrics as well)
<br>
This special build includes:
Gstreamer (alsa, oss, gaudioconfig...),Helix, MySQL, MAS... support, ALL the engines that you can get from the ./configure script have been included
<br>
<b>INSTRUCTIONS</b>
1) check that you have all the dependencies:
<i>artsbuilder (>= 4:3.4.0), kdelibs4 (>= 4:3.4.0), konqueror (>= 4:3.4.0), libart-2.0-2 (>= 2.3.16), libarts1 (>= 1.3.2), libasound2 (>> 1.0., libaudio2, libaudiofile0 (>= 0.2.3-4), libc6 (>= 2.3.2.ds1-4), libesd0 (>= 0.2.29-1) | libesd-alsa0 (>= 0.2.29-1), libflac6, libfontconfig1 (>= 2.2.1), libfreetype6 (>= 2.1.5-1), libgamin0, libgcc1 (>= 1:4.0.0-7), libglib1.2 (>= 1.2.0), libglib2.0-0 (>= 2.6.0), libgstreamer0.8-0 (>= 0.8.9-1), libgtk1.2 (>= 1.2.10-4), libice6 | xlibs (>> 4.1.0), libidn11 (>= 0.5.2), libjpeg62, libmusicbrainz4 (>= 2.1.1), libmysqlclient14 (>= 4.1.10a), libogg0 (>= 1.1.2), libpcre3 (>= 4.5), libpng12-0 (>= 1.2.8rel), libpopt0 (>= 1.7), libqt3c102-mt (>= 3:3.3.3), libsm6 | xlibs (>> 4.1.0), libstdc++5 (>= 1:3.3.4-1), libtag1 (>= 1.4-0), libtunepimp2 (>= 0.3.0), libvorbis0a (>= 1.0.1), libvorbisenc2 (>= 1.0.1), libvorbisfile3 (>= 1.0.1), libx11-6 | xlibs (>> 4.1.0), libxcursor1 (>> 1.1.2), libxext6 | xlibs (>> 4.1.0), libxft2 (>> 2.1.1), libxi6 | xlibs (>> 4.1.0), libxinerama1, libxml2 (>= 2.6.17), libxrandr2 | xlibs (>> 4.3.0), libxrender1, libxt6 | xlibs (>> 4.1.0), xmms, zlib1g (>= 1:1.2.1)</i>
2) install libtag version 1.4 #dpkg --install libtag1_1.4-0_i386.deb
2) remove amarok (all engines, I recommend using synaptic and removing everything that starts with amarok)
3) install this new version of amarok #dpkg --install amarok_1.3.1-1_i386.deb
4) you can go to synaptic, search for amarok, and lock the version so that you won't be bugged about updating amarok.


**I recommend you to use Gstreamer Engine and use the output plugin Gconfaudiosink**

I've tried with all the engines:
Helix
Gstreamer
aRTS
MAS

And that one seems to use a reasonable ammount of memory (using aRTS for example makes Arts and amarok use much more VMemory Size)

I really hope some downloads, my first work in Linux

---

