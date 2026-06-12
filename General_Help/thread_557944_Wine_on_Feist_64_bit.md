---
title: "Wine on Feist 64 bit?"
date: 2007-09-23
forum: General Help
---

### Post by mikeym on 2007-09-23
Is it possible to get the GIT (CVS or whatever) version of wine on 64 bit Feisty? 

I have tried everything! 

It won't compile because the winehq guide for Ubuntu is awful! It says things like "now download the -dev files you need" - Really? Which ones? Where do I get the 32 bit versions? 

I have searched high and low for a repository that has up-to-date CVS builds in it, but to no avail!

Please help!

---

### Post by mikeym on 2007-09-23
Here is the guide from WineHQ, perhaps someone could help clear it up for me:

> [B][SIZE="5"]Building Wine on Ubuntu / Kubuntu 7.04 (Feisty Fawn)
[/SIZE][/B]
Warning: Wine will not compile if you install libicu34-dev listed at Recommended Packages on 32bit. No bi-directional text support. However, see below for a potential solution.

First one must install the necessary libraries: Finding the correct set may take a few minutes and several tries.

sudo apt-get install libfreetype6-dev fontforge ia32-libs

There are others to be gotten by hand. I did them by installing the various -dev packages in the 32-bit packages build dependency.

Make sure you have the following packages installed:

sudo apt-get install gcc flex bison libc6-i386 libc6-dev-i386 lib32z1-dev

Now add the following links that the library install does not make:

cd /usr/lib32
sudo ln -s libX11.so.6 libX11.so
sudo ln -s libXext.so.6 libXext.so
sudo ln -s libfreetype.so.6 libfreetype.so

Others that may be needed:

sudo ln -s /usr/lib32/libXrender.so.1 /usr/lib32/libXrender.so
sudo ln -s libGL.so.1 libGL.so
sudo ln -s libGLU.so.1 libGLU.so

When you run configure, do it like: ./configure > configoutput.txt Then cat configoutput.txt | grep soname, and you'll find a bunch of sonames of the form *.so rather than, say, *.so.1 -- these are likely libraries linked to the 64 bit version. I don't know what not having a hand-created symlink in /usr/lib32 will do here.

Run configure, build and install with:

CC="gcc-4.1 -m32" LDFLAGS="-L/lib32 -L/usr/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" ./configure
make 
sudo make install

If all needed libraries are present there will be no missing-library warnings or errors anywhere.

Unfortunately, the above method seems to improperly handle libssl. There is no 32 bit libssl or libcrypto in Ubuntu.

So this is the first line to realy get me "First one must install the necessary libraries: Finding the correct set may take a few minutes and several tries."

There is a list of packages to install for 32 bit feisty and a script:

```

#!/bin/sh
# Script showing how to set up a Wine development environment
# on Ubuntu 07.04 (Edgy)
#
# A few Ubuntu tips:
#
# Some packages, like cogito and libjack-dev, are only available 
# in the Universe repository, so you need to uncomment out
# the appropriate line in /etc/apt/sources.list or check the 'universe'
# checkbox in the GUI package manager 'synaptic'.
#
# If you see a prompt to insert the CD when installing software
# with apt-get, comment out the initial reference to the cdrom in /etc/apt/sources.list.
# See https://launchpad.net/distros/ubuntu/+source/apt/+bug/37888
#
# If you see "open /dev/snd/seq failed",
# add snd_seq_oss to /etc/modules
# See http://ubuntuforums.org/archive/index.php/t-1654.html
#
# If you see "cannot create mcop directory"
# when you run winecfg and click on the audio tag,
# do "mkdir -p $HOME/.kde/socket-`hostname`".
# See https://launchpad.net/distros/ubuntu/+source/alsa-lib/+bug/31699
#

# Get basic source management tools
apt-get install cvs git-core cogito

# Get basic C compiler tools
apt-get install gcc libc6-dev flex bison make linux-libc-dev m4

# Get font tools
apt-get install fontforge

# Get libraries needed by Wine
apt-get install \
libaudio-dev \
libcapi20-3 \
libcapi20-dev \
libcupsys2-dev \
libdbus-1-dev \
libesd0-dev \
libexif-dev \
libexpat1-dev \
libfontconfig1-dev \
libfreetype6-dev \
libgcrypt11-dev \
libgl1-mesa-dev \
libglib1.2-dev \
libglib2.0-dev \
libglu1-mesa-dev \
libgnutls-dev \
libgpg-error-dev \
libgphoto2-2-dev \
libhal-dev \
libice-dev \
libicu34-dev \
libieee1284-3-dev \
libjpeg62-dev \
liblcms1-dev \
libldap2-dev \
libltdl3 \
libltdl3-dev \
liblzo-dev \
libmad0 \
libmad0-dev \
libmng-dev \
libncurses5-dev \
libodbcinstq1c2 \
libogg-dev \
libopencdk8-dev \
libpng12-dev \
libpopt-dev \
libqt3-headers \
libqt3-mt \
libqt3-mt-dev \
libsane-dev \
libsm-dev \
libssl-dev \
libtasn1-3-dev \
libtiff4-dev \
libtiffxx0c2 \
libusb-dev \
libvorbis-dev \
libvorbisfile3 \
libx11-dev \
libxau-dev \
libxcursor-dev \
libxdmcp-dev \
libxext-dev \
libxfixes-dev \
libxft-dev \
libxi-dev \
libxinerama-dev \
libxml2-dev \
libxmu-dev \
libxmu-headers \
libxrandr-dev \
libxrender-dev \
libxslt1-dev \
libxt-dev \
libxv-dev \
libxxf86vm-dev \
mesa-common-dev \
odbcinst1debian1 \
qt3-dev-tools \
render-dev \
unixodbc \
unixodbc-dev \
x11proto-core-dev \
x11proto-fixes-dev \
x11proto-input-dev \
x11proto-kb-dev \
x11proto-randr-dev \
x11proto-render-dev \
x11proto-video-dev \
x11proto-xext-dev \
x11proto-xf86vidmode-dev \
x11proto-xinerama-dev \
x-dev \
xtrans-dev \
zlib1g-dev

```

Now surely this is the 64 bit versions of the files? How would you install these as 32 bit versions on a 64 bit system?

**libicu34-dev** doesn't exist in my repos but sould I be worried about **libicu36-dev** that I have installed?
[I]
"When you run configure, do it like: ./configure > configoutput.txt Then cat configoutput.txt | grep soname, and you'll find a bunch of sonames of the form *.so rather than, say, *.so.1 -- these are likely libraries linked to the 64 bit version. I don't know what not having a hand-created symlink in /usr/lib32 will do here."[/I]

What are you supposed to do if you do have .so.1 files like I did when I tried compiling?

---

### Post by mikeym on 2007-09-23
OK so trying it out by doing what it says and installing the -dev files from the script lets me know that the libraries need to be 32 bit. So when I run configure with the --verbose option I get told at the end:

```


configure: Xxf86vm development files not found.
Wine will be built without XF86 Vidmode support. (winex11.drv)

configure: XRender development files not found.
Wine will be built without XRender support. (winex11.drv)

configure: XRandr development files not found.
Wine will be built without XRandr support. (winex11.drv)

configure: Xinerama development files not found.
Wine will be built without Xinerama support. (winex11.drv)

configure: libxml2 development files not found.
Wine will be built without XML support. (msxml.dll)

configure: libxslt development files not found.
Wine will be built without xslt support. (msxml.dll)

configure: libhal development files not found.
Wine will be built without dynamic device support. (explorer.exe)

configure: lib(n)curses development files not found.
Wine will be built without (n)curses support. (wineconsole.exe)

configure: libsane development files not found.
Wine will be built without scanner support. (sane.ds/twain_32.dll)

configure: libgphoto2 development files not found.
Wine will be built without Digital Camera support. (gphoto2.ds/twain_32.dll)

configure: liblcms development files not found.
Wine will be built without Color Management support. (mscms.dll)

configure: libldap (OpenLDAP) development files not found.
Wine will be built without LDAP support. (wldap32.dll)

configure: libcapi20 development files not found.
Wine will be built without ISDN support. (capi2032.dll)

configure: libcups development files not found.
Wine will be built without CUPS support.

configure: fontconfig development files not found.
Wine will be built without fontconfig support.

configure: OpenSSL development files not found.
Wine will be built without SSL support. (wininet.dll)

configure: libjpeg development files not found.
Wine will be built without JPEG support. (oleaut32.dll)

configure: libpng development files not found.
Wine will be built without PNG support. (oleaut32.dll)

Configure finished.  Do 'make depend && make' to compile Wine.

```

Since each of those libraries development files  was installed by the script from winehq it means that they were not what was needed. Looking at the *configure* line from the instructions I would guess that the development files would have to go into the */usr/lib32* folder. 

I've found the following post about installing *chroot* and redirecting the libraries it installs to */usr/lib32*. I've installed *chroot* before and it makes sense as an approach so I'm going to try it.

---

### Post by mikeym on 2007-09-23
O.K,

So I've been doing quite a few things to my system to try and get wine to install. 

First off I created a chroot 32 bit environment by following [this post.]("http://ubuntuforums.org/showpost.php?p=3231948&postcount=219")

Then I followed this post's recomendations to link the 32 bit */chroot/usr/lib* to my* /usr/lib32* and move my old */usr/lib32* to */usr/lib32.local*.

Then I was having problems getting it to confuigure untill I forced config to look in the */usr/lib32.local* folder to.

```

CC="gcc-4.1 -m32" LDFLAGS="-L/lib32 -L/usr/lib32.local -L/usr/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32i -Wl,-rpath,/usr/lib32.local" linux32 ./configure --verbose

```

This gives me the following warning:

```

configure: lib(n)curses development files not found.
Wine will be built without (n)curses support. (wineconsole.exe)

Configure finished.  Do 'make depend && make' to compile Wine.

```

Now I do have the **libncurses5,** **libncurses5-dev,** **libncursesw5** and **libncursesw5-dev** packages installed on the 32 bit *chroot*. I decided to ignore this and run "make depend && make" and I got as for as:

```

../../tools/winegcc/winegcc -B../../tools/winebuild -shared ./acledit.spec    main.o         -o acledit.dll.so  -lkernel32   ../../libs/port/libwine_port.a -L/lib32 -L/usr/lib32.local -L/usr/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32i -Wl,-rpath,/usr/lib32.local 
ld: Relocatable linking with relocations from format elf32-i386 (main.o) to format elf64-x86-64 (acledit.SYSWbp.o) is not supported
winebuild: ld -r failed with status 256
winegcc: ../../tools/winebuild/winebuild failed.
make[2]: *** [acledit.dll.so] Error 2
make[2]: Leaving directory `/home/mikey/packages/wine/dlls/acledit'
make[1]: *** [acledit] Error 2
make[1]: Leaving directory `/home/mikey/packages/wine/dlls'
make: *** [dlls] Error 2

```

I saw on another post that the elf32-i386 was in some way related to *libicu* so I wonder if that is related to the warning in the original winehq guide? 

Does anyone have any ideas how to procede from here?

---

### Post by Maestro23 on 2007-09-23
It appears they have a .deb package for 64-bit.  Have you looked into it?

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Related Forum Thread: [http://ubuntuforums.org/showthread.php?t=431503](http://ubuntuforums.org/showthread.php?t=431503)

Good luck.

---

### Post by mikeym on 2007-09-23
I am awair of this. There also is a repository for stable wine builds, but I'm looking to install the CVS because the one gaem I'm wanting to run (Half Life 2) doesn't work on my system with the stable version and I've been advised to try the CVS builds. 

It would be nice if it was that easy. :)

---

### Post by Maestro23 on 2007-09-23
> **mikeym said:**
> I am awair of this. There also is a repository for stable wine builds, but I'm looking to install the CVS because the one gaem I'm wanting to run (Half Life 2) doesn't work on my system with the stable version and I've been advised to try the CVS builds. 

It would be nice if it was that easy. :)

Ah... I see.  Good luck then man.:guitar:

---

