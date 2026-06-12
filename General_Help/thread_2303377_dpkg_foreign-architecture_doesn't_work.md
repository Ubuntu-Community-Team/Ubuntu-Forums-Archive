---
title: "dpkg foreign-architecture doesn't work"
date: 2015-11-18
forum: General Help
---

### Post by necbot on 2015-11-18
This all started because I am trying to install Firefox 32 bit on Ubuntu 12.04.  Circumstances beyond my control force me to use 12.04 and the 32 bit version of Firefox.  As such, answers that involve "switch to 64 bit Firefox" or "upgrade to the latest version of Ubuntu" or "this is fixed in a later version" won't help because my employer won't allow me to upgrade.

So I tried installing 32 bit Firefox but when I run "sudo apt-get install firefox:i386" I get....
```


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 firefox:i386 : Depends: libasound2:i386 (>= 1.0.23) but it is not going to be installed
                Depends: libatk1.0-0:i386 (>= 1.12.4) but it is not going to be installed
                Depends: libcairo2:i386 (>= 1.2.4) but it is not going to be installed
                Depends: libdbus-glib-1-2:i386 (>= 0.78) but it is not going to be installed
                Depends: libfontconfig1:i386 (>= 2.8.0) but it is not going to be installed
                Depends: libgdk-pixbuf2.0-0:i386 (>= 2.22.0) but it is not going to be installed
                Depends: libglib2.0-0:i386 (>= 2.31.8) but it is not going to be installed
                Depends: libgtk2.0-0:i386 (>= 2.24.0) but it is not going to be installed
                Depends: libpango1.0-0:i386 (>= 1.22.0) but it is not going to be installed
                Depends: libxt6:i386 but it is not going to be installed
                Recommends: xul-ext-ubufox:i386 but it is not installable
                Recommends: libcanberra0:i386 but it is not going to be installed
                Recommends: libdbusmenu-glib4:i386 but it is not going to be installed
                Recommends: libdbusmenu-gtk4:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

I'm guessing this occurs because the 12.04 I have installed is 64 bit.  I tried to enable 32 bit packages by running "sudo dpkg --add-architecture i386", but when I run this I get...

```
dpkg: error: unknown option --add-architecture


Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;


Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !

```

I did some more reading and found that 12.04 dpkg version does not support --add-architecture, *ugh* you have to use foreign-architecture so I ran "sudo dpkg --foreign-architecture i386" and I get this...

```
dpkg: error: need an action option


Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;


Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !

```

What does dpkg: error: need an action option mean?  Most of the advice I saw regarding this seems specific to 12.04.  There is a bug report on this here...  [https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/1255073](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/1255073)  but it was simply closed and the users question was not even addressed.  I checked my /etc/dpkg/dpkg.cfg.d/multiarch and the foreign-architecture i386 is in the file.  Is there a command I'm missing?  How do I enable 32 bit packages on 64 bit 12.04 ubuntu?  My dpkg version is 1.16.1.2  Thanks!

---

### Post by matt_symes on 2015-11-18
Hi

Try to install the 32 bit libraries in 12.04

```
sudo apt-get install ia32-libs
```

and then try to install Firefox as you did before.

I think the ia32-libs package was still available in 12.04 but my memory is a bit hazy.

Give it a try though.

Kind regards

---

### Post by necbot on 2015-11-18
Thanks for the help matt_symes.  I ran the command and got this....

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 ia32-libs : Depends: ia32-libs-multiarch
E: Unable to correct problems, you have held broken packages.
```

I tried running...

```
sudo apt-get install ia32-libs-multiarch
```

and I got...

```
Reading package lists...
Building dependency tree...
Reading state information...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 ia32-libs-multiarch:i386 : Depends: bluez-alsa:i386 but it is not going to be installed
                            Depends: libgettextpo0:i386 but it is not going to be installed
                            Depends: gstreamer0.10-plugins-base:i386 but it is not going to be installed
                            Depends: gstreamer0.10-plugins-good:i386 but it is not going to be installed
                            Depends: gstreamer0.10-fluendo-mp3:i386 but it is not going to be installed
                            Depends: gtk2-engines:i386 but it is not going to be installed
                            Depends: gtk2-engines-murrine:i386 but it is not going to be installed
                            Depends: gtk2-engines-pixbuf:i386 but it is not going to be installed
                            Depends: gtk2-engines-oxygen:i386 but it is not going to be installed
                            Depends: gvfs:i386 but it is not going to be installed
                            Depends: ibus-gtk:i386 but it is not going to be installed
                            Depends: libasound2:i386 but it is not going to be installed
                            Depends: libasound2-plugins:i386 but it is not going to be installed
                            Depends: libaudio2:i386 but it is not going to be installed
                            Depends: libcanberra-gtk-module:i386 but it is not going to be installed
                            Depends: libcups2:i386 but it is not going to be installed
                            Depends: libcupsimage2:i386 but it is not going to be installed
                            Depends: libcurl3:i386 but it is not going to be installed
                            Depends: libdbus-glib-1-2:i386 but it is not going to be installed
                            Depends: libesd0:i386 but it is not going to be installed
                            Depends: libfontconfig1:i386 but it is not going to be installed
                            Depends: libgail-common:i386 but it is not going to be installed
                            Depends: libgconf-2-4:i386 but it is not going to be installed
                            Depends: libglapi-mesa:i386
                            Depends: libglu1-mesa:i386 but it is not going to be installed
                            Depends: libgphoto2-2:i386 but it is not going to be installed
                            Depends: libgphoto2-port0:i386 but it is not going to be installed
                            Depends: libgtk2.0-0:i386 but it is not going to be installed
                            Depends: libpulse-mainloop-glib0:i386 but it is not going to be installed
                            Depends: libqt4-dbus:i386 but it is not going to be installed
                            Depends: libqt4-network:i386 but it is not going to be installed
                            Depends: libqt4-opengl:i386 but it is not going to be installed
                            Depends: libqt4-qt3support:i386 but it is not going to be installed
                            Depends: libqt4-script:i386 but it is not going to be installed
                            Depends: libqt4-scripttools:i386 but it is not going to be installed
                            Depends: libqt4-sql:i386 but it is not going to be installed
                            Depends: libqt4-svg:i386 but it is not going to be installed
                            Depends: libqt4-test:i386 but it is not going to be installed
                            Depends: libqt4-xml:i386 but it is not going to be installed
                            Depends: libqt4-xmlpatterns:i386 but it is not going to be installed
                            Depends: libqtcore4:i386 but it is not going to be installed
                            Depends: libqtgui4:i386 but it is not going to be installed
                            Depends: libqtwebkit4:i386 but it is not going to be installed
                            Depends: librsvg2-common:i386 but it is not going to be installed
                            Depends: libsane:i386 but it is not going to be installed
                            Depends: libsdl-mixer1.2:i386 but it is not going to be installed
                            Depends: libsdl-image1.2:i386 but it is not going to be installed
                            Depends: libsdl-net1.2:i386 but it is not going to be installed
                            Depends: libsdl-ttf2.0-0:i386 but it is not going to be installed
                            Depends: libsdl1.2debian:i386 but it is not going to be installed
                            Depends: libxaw7:i386 but it is not going to be installed
                            Depends: libpulsedsp:i386 but it is not going to be installed
                            Depends: xaw3dg:i386 but it is not going to be installed
                            Recommends: libgl1-mesa-glx:i386
                            Recommends: libgl1-mesa-dri:i386
E: Unable to correct problems, you have held broken packages.

```

---

### Post by matt_symes on 2015-11-18
Hi

Hmm. We need to diagnose those error messages.

Can you post the output of these commands please.

This will list all your sourses.
```
grep -n "^[^#]" /etc/apt/sources.list{,.d/*}
```

This will audit for broken packages.

```
sudo dpkg -C
```

That'll be a good start.

I'm going to be afk for until this late afternoon/evening though.

BTW: Have you considered installing 12.04 32 bit in a VM ? It may be quicker to do that and to install Firefox. It'll depend on your use case though.

Kind regards

---

### Post by steeldriver on 2015-11-18
Given that 'apt-get install firefox:i386' doesn't simply tell you that it's unable to locate the package, I suspect that the i386 architecture may already be enabled, and the failure is cause by other dependency problems

What are the outputs of

```

dpkg --print-foreign-architectures

ls /etc/dpkg/dpkg.cfg.d/

cat /etc/dpkg/dpkg.cfg.d/multiarch

apt-cache policy firefox:i386

```

FWIW I confirmed on an old 64-bit 12.04 VM that dpkg doesn't recognize '--foreign-architecture' (even though its manpage says it should)

---

### Post by necbot on 2015-11-18
Thank you both for the replies.  I ran the commands you asked about.  Here is the output...

grep -n "^[^#]" /etc/apt/sources.list{,.d/*} 


```
/etc/apt/sources.list:8:deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
/etc/apt/sources.list:9:deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted
/etc/apt/sources.list:17:deb http://us.archive.ubuntu.com/ubuntu/ precise universe
/etc/apt/sources.list:18:deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
/etc/apt/sources.list:25:deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
/etc/apt/sources.list:26:deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
/etc/apt/sources.list:34:deb http://security.ubuntu.com/ubuntu precise-security main restricted
/etc/apt/sources.list:35:deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
/etc/apt/sources.list:36:deb http://security.ubuntu.com/ubuntu precise-security universe
/etc/apt/sources.list:37:deb-src http://security.ubuntu.com/ubuntu precise-security universe
/etc/apt/sources.list:38:deb http://security.ubuntu.com/ubuntu precise-security multiverse
/etc/apt/sources.list:39:deb-src http://security.ubuntu.com/ubuntu precise-security multiverse
/etc/apt/sources.list:50:deb http://extras.ubuntu.com/ubuntu precise main
/etc/apt/sources.list:51:deb-src http://extras.ubuntu.com/ubuntu precise main
/etc/apt/sources.list:55:deb http://ppa.launchpad.net/nginx/stable/ubuntu precise main
/etc/apt/sources.list:56:deb-src http://ppa.launchpad.net/nginx/stable/ubuntu precise main
/etc/apt/sources.list.d/skunk-pepper-flash-precise.list:1:deb http://ppa.launchpad.net/skunk/pepper-flash/ubuntu precise main
/etc/apt/sources.list.d/skunk-pepper-flash-precise.list:2:deb-src http://ppa.launchpad.net/skunk/pepper-flash/ubuntu precise main
/etc/apt/sources.list.d/webupd8team-java-precise.list:1:deb http://ppa.launchpad.net/webupd8team/java/ubuntu precise main
/etc/apt/sources.list.d/webupd8team-java-precise.list:2:deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu precise main
/etc/apt/sources.list.d/webupd8team-java-precise.list.save:1:deb http://ppa.launchpad.net/webupd8team/java/ubuntu precise main
/etc/apt/sources.list.d/webupd8team-java-precise.list.save:2:deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu precise main

```



sudo dpkg -C outputs nothing




dpkg --print-foreign-architectures


```
i386

```

ls /etc/dpkg/dpkg.cfg.d/


```
multiarch

```

cat /etc/dpkg/dpkg.cfg.d/multiarch


```
foreign-architecture i386

```

apt-cache policy firefox:i386


```
firefox:i386:
  Installed: (none)
  Candidate: 42.0+build2-0ubuntu0.12.04.1
  Version table:
     42.0+build2-0ubuntu0.12.04.1 0
        500 http://security.ubuntu.com/ubuntu/ precise-security/main i386 Packages
     11.0+build1-0ubuntu4 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main i386 Packages

```

---

### Post by mc4man on 2015-11-18
Putting aside your particular install & Ubuntu release version I'm not too sure that anyone can install firefox:i386 on a 64 bit install, at least in Ubuntu.
For one your current FF (amd64) should be removed before trying but there are some other packages that FF deps on that will conflict between i386 & amd64 versions. These packages are also deps of several other key packages so that *may* create an impossible situation.

To see a little more clearly install aptitude & try to install with it..

---

### Post by vasa1 on 2015-11-19
> **mc4man said:**
> Putting aside your particular install & Ubuntu release version I'm not too sure that anyone can install firefox:i386 on a 64 bit install, at least in Ubuntu. ...
Is this only for 12.04? Here's a link to someone installing 32-bit Seamonkey on 64-bit _**14.04**_: [http://askubuntu.com/questions/698185/is-there-a-way-to-make-32-bit-mozilla-seamonkey-work-in-a-64-bit-xubuntu-14-04](http://askubuntu.com/questions/698185/is-there-a-way-to-make-32-bit-mozilla-seamonkey-work-in-a-64-bit-xubuntu-14-04)

---

### Post by necbot on 2015-11-19
> **mc4man said:**
> Putting aside your particular install & Ubuntu release version I'm not too sure that anyone can install firefox:i386 on a 64 bit install, at least in Ubuntu.
For one your current FF (amd64) should be removed before trying but there are some other packages that FF deps on that will conflict between i386 & amd64 versions. These packages are also deps of several other key packages so that *may* create an impossible situation.

To see a little more clearly install aptitude & try to install with it..


I think you may be correct.  I installed aptitude and this is the output....

```
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
The following NEW packages will be installed:
  firefox:i386 libasound2:i386{ab} libatk1.0-0:i386{a} 
  libavahi-client3:i386{ab} libavahi-common-data:i386{ab} 
  libavahi-common3:i386{ab} libcairo2:i386{ab} libcanberra0:i386{a} 
  libcomerr2:i386{ab} libcups2:i386{a} libdatrie1:i386{a} 
  libdbus-1-3:i386{a} libdbus-glib-1-2:i386{a} libdbusmenu-glib4:i386{ab} 
  libdbusmenu-gtk4:i386{ab} libelf1:i386{a} libexpat1:i386{a} 
  libffi6:i386{a} libfontconfig1:i386{ab} libfreetype6:i386{a} 
  libgcrypt11:i386{a} libgdk-pixbuf2.0-0:i386{a} libglib2.0-0:i386{ab} 
  libgnutls26:i386{a} libgpg-error0:i386{a} libgssapi-krb5-2:i386{a} 
  libgtk2.0-0:i386{ab} libice6:i386{a} libjasper1:i386{a} 
  libjpeg-turbo8:i386{ab} libjpeg8:i386{a} libk5crypto3:i386{a} 
  libkeyutils1:i386{a} libkrb5-3:i386{a} libkrb5support0:i386{a} 
  libltdl7:i386{a} libogg0:i386{a} libp11-kit0:i386{a} 
  libpango1.0-0:i386{ab} libpcre3:i386{a} libpixman-1-0:i386{a} 
  libpng12-0:i386{a} libselinux1:i386{a} libsm6:i386{a} 
  libstartup-notification0:i386{a} libtasn1-3:i386{a} libtdb1:i386{a} 
  libthai0:i386{a} libtiff4:i386{a} libuuid1:i386{ab} libvorbis0a:i386{a} 
  libvorbisfile3:i386{a} libx11-6:i386{a} libx11-xcb1:i386{a} 
  libxau6:i386{a} libxcb-render0:i386{a} libxcb-shm0:i386{a} 
  libxcb-util0:i386{a} libxcb1:i386{a} libxcomposite1:i386{a} 
  libxcursor1:i386{a} libxdamage1:i386{a} libxdmcp6:i386{a} 
  libxext6:i386{a} libxfixes3:i386{a} libxft2:i386{a} libxi6:i386{a} 
  libxinerama1:i386{a} libxrandr2:i386{a} libxrender1:i386{a} 
  libxt6:i386{a} zlib1g:i386{a} 
0 packages upgraded, 72 newly installed, 0 to remove and 0 not upgraded.
Need to get 60.9 MB of archives. After unpacking 128 MB will be used.
The following packages have unmet dependencies:
 libcomerr2 : Breaks: libcomerr2:i386 (!= 1.42-1ubuntu2.3) but 1.42-1ubuntu2.2 is to be installed.
 libcomerr2:i386 : Breaks: libcomerr2 (!= 1.42-1ubuntu2.2) but 1.42-1ubuntu2.3 is installed.
 libjpeg-turbo8 : Breaks: libjpeg-turbo8:i386 (!= 1.1.90+svn733-0ubuntu4.4) but 1.1.90+svn733-0ubuntu4.3 is to be installed.
 libjpeg-turbo8:i386 : Breaks: libjpeg-turbo8 (!= 1.1.90+svn733-0ubuntu4.3) but 1.1.90+svn733-0ubuntu4.4 is installed.
 libcairo2 : Breaks: libcairo2:i386 (!= 1.10.2-6.1ubuntu3) but 1.10.2-6.1ubuntu2 is to be installed.
 libcairo2:i386 : Breaks: libcairo2 (!= 1.10.2-6.1ubuntu2) but 1.10.2-6.1ubuntu3 is installed.
 libglib2.0-0 : Breaks: libglib2.0-0:i386 (!= 2.32.4-0ubuntu1) but 2.32.1-0ubuntu2 is to be installed.
 libglib2.0-0:i386 : Breaks: libglib2.0-0 (!= 2.32.1-0ubuntu2) but 2.32.4-0ubuntu1 is installed.
 libavahi-common-data : Breaks: libavahi-common-data:i386 (!= 0.6.30-5ubuntu2.1) but 0.6.30-5ubuntu2 is to be installed.
 libavahi-common-data:i386 : Breaks: libavahi-common-data (!= 0.6.30-5ubuntu2) but 0.6.30-5ubuntu2.1 is installed.
 libdbusmenu-glib4 : Breaks: libdbusmenu-glib4:i386 (!= 0.6.2-0ubuntu0.2) but 0.6.1-0ubuntu3 is to be installed.
 libdbusmenu-glib4:i386 : Breaks: libdbusmenu-glib4 (!= 0.6.1-0ubuntu3) but 0.6.2-0ubuntu0.2 is installed.
 libdbusmenu-gtk4 : Breaks: libdbusmenu-gtk4:i386 (!= 0.6.2-0ubuntu0.2) but 0.6.1-0ubuntu3 is to be installed.
 libdbusmenu-gtk4:i386 : Breaks: libdbusmenu-gtk4 (!= 0.6.1-0ubuntu3) but 0.6.2-0ubuntu0.2 is installed.
 libasound2 : Breaks: libasound2:i386 (!= 1.0.25-1ubuntu10.2) but 1.0.25-1ubuntu10 is to be installed.
 libasound2:i386 : Breaks: libasound2 (!= 1.0.25-1ubuntu10) but 1.0.25-1ubuntu10.2 is installed.
 libuuid1 : Breaks: libuuid1:i386 (!= 2.20.1-1ubuntu3.1) but 2.20.1-1ubuntu3 is to be installed.
 libuuid1:i386 : Breaks: libuuid1 (!= 2.20.1-1ubuntu3) but 2.20.1-1ubuntu3.1 is installed.
 libavahi-client3 : Breaks: libavahi-client3:i386 (!= 0.6.30-5ubuntu2.1) but 0.6.30-5ubuntu2 is to be installed.
 libavahi-client3:i386 : Breaks: libavahi-client3 (!= 0.6.30-5ubuntu2) but 0.6.30-5ubuntu2.1 is installed.
 libfontconfig1 : Breaks: libfontconfig1:i386 (!= 2.8.0-3ubuntu9.1) but 2.8.0-3ubuntu9 is to be installed.
 libfontconfig1:i386 : Depends: fontconfig-config:i386 (= 2.8.0-3ubuntu9) which is a virtual package.
                       Breaks: libfontconfig1 (!= 2.8.0-3ubuntu9) but 2.8.0-3ubuntu9.1 is installed.
 libpango1.0-0 : Breaks: libpango1.0-0:i386 (!= 1.30.0-0ubuntu3.1) but 1.30.0-0ubuntu2 is to be installed.
 libpango1.0-0:i386 : Breaks: libpango1.0-0 (!= 1.30.0-0ubuntu2) but 1.30.0-0ubuntu3.1 is installed.
 libavahi-common3 : Breaks: libavahi-common3:i386 (!= 0.6.30-5ubuntu2.1) but 0.6.30-5ubuntu2 is to be installed.
 libavahi-common3:i386 : Breaks: libavahi-common3 (!= 0.6.30-5ubuntu2) but 0.6.30-5ubuntu2.1 is installed.
 libgtk2.0-0 : Breaks: libgtk2.0-0:i386 (!= 2.24.10-0ubuntu6.2) but 2.24.10-0ubuntu6 is to be installed.
 libgtk2.0-0:i386 : Breaks: libgtk2.0-0 (!= 2.24.10-0ubuntu6) but 2.24.10-0ubuntu6.2 is installed.
Internal error: the solver Install(fontconfig-config:amd64 2.8.0-3ubuntu9 <libfontconfig1:i386 2.8.0-3ubuntu9 -> {fontconfig-config:amd64 2.8.0-3ubuntu9}>) of a supposedly unresolved dependency is already installed in step 8
Internal error: the solver Install(espeak:i386 1.46.02-0ubuntu1 <espeak-data:amd64 1.46.02-0ubuntu1 -S> {espeak:amd64 1.46.02-0ubuntu1 espeak:i386 1.46.02-0ubuntu1}>) of a supposedly unresolved dependency is already installed in step 108
Internal error: the solver Install(ghostscript:i386 9.05~dfsg-0ubuntu4 <gs-cjk-resource:amd64 1.20100103-3 -> {ghostscript:amd64 9.05~dfsg-0ubuntu4 ghostscript:amd64 9.05~dfsg-0ubuntu4.3 ghostscript:i386 9.05~dfsg-0ubuntu4 ghostscript:i386 9.05~dfsg-0ubuntu4.3}>) of a supposedly unresolved dependency is already installed in step 1606
Internal error: the solver Install(ghostscript:i386 9.05~dfsg-0ubuntu4.3 <ghostscript-x:amd64 9.05~dfsg-0ubuntu4.3 -> {ghostscript:amd64 9.05~dfsg-0ubuntu4.3 ghostscript:i386 9.05~dfsg-0ubuntu4.3}>) of a supposedly unresolved dependency is already installed in step 1607
Internal error: the solver Install(ghostscript:i386 9.05~dfsg-0ubuntu4.3 <gs-cjk-resource:amd64 1.20100103-3 -> {ghostscript:amd64 9.05~dfsg-0ubuntu4 ghostscript:amd64 9.05~dfsg-0ubuntu4.3 ghostscript:i386 9.05~dfsg-0ubuntu4 ghostscript:i386 9.05~dfsg-0ubuntu4.3}>) of a supposedly unresolved dependency is already installed in step 1607
Internal error: the solver Install(avahi-daemon:i386 0.6.30-5ubuntu2 <libnss-mdns:amd64 0.10-3.2 -> {avahi-daemon:amd64 0.6.30-5ubuntu2 avahi-daemon:amd64 0.6.30-5ubuntu2.1 avahi-daemon:i386 0.6.30-5ubuntu2}>) of a supposedly unresolved dependency is already installed in step 1695
Internal error: the solver Install(gconf2:i386 3.2.5-0ubuntu2 <gstreamer0.10-gconf:amd64 0.10.31-1ubuntu1.2 -> {gconf2:amd64 3.2.5-0ubuntu2 gconf2:i386 3.2.5-0ubuntu2}>) of a supposedly unresolved dependency is already installed in step 2958
Internal error: the solver Install(gconf2:i386 3.2.5-0ubuntu2 <gnome-panel-data:amd64 1:3.4.1-0ubuntu1.2 -> {gconf2:amd64 3.2.5-0ubuntu2 gconf2:i386 3.2.5-0ubuntu2}>) of a supposedly unresolved dependency is already installed in step 2958
Internal error: the solver Install(gconf2:i386 3.2.5-0ubuntu2 <libgnome2-common:amd64 2.32.1-2ubuntu1.1 -> {gconf2:amd64 3.2.5-0ubuntu2 gconf2:i386 3.2.5-0ubuntu2}>) of a supposedly unresolved dependency is already installed in step 2958
Internal error: the solver Install(gconf2:i386 3.2.5-0ubuntu2 <unity-common:amd64 5.20.0-0ubuntu3 -> {gconf2:amd64 3.2.5-0ubuntu2 gconf2:i386 3.2.5-0ubuntu2}>) of a supposedly unresolved dependency is already installed in step 2958
Internal error: the solver Install(gconf2:i386 3.2.5-0ubuntu2 <gnome-themes-standard:amd64 3.4.1-0ubuntu1.2 -> {gconf2:amd64 3.2.5-0ubuntu2 gconf2:i386 3.2.5-0ubuntu2}>) of a supposedly unresolved dependency is already installed in step 2958
Internal error: the solver Install(gconf2:i386 3.2.5-0ubuntu2 <compiz-plugins-main-default:amd64 1:0.9.7.0~bzr19-0ubuntu10.1 -> {gconf2:amd64 3.2.5-0ubuntu2 gconf2:i386 3.2.5-0ubuntu2}>) of a supposedly unresolved dependency is already installed in step 2958
Internal error: the solver Install(gconf2:i386 3.2.5-0ubuntu2 <mutter-common:amd64 3.4.1-0ubuntu1 -> {gconf2:amd64 3.2.5-0ubuntu2 gconf2:i386 3.2.5-0ubuntu2}>) of a supposedly unresolved dependency is already installed in step 2958
Internal error: the solver Install(gconf2:i386 3.2.5-0ubuntu2 <gnome-applets-data:amd64 3.4.1-0ubuntu1 -> {gconf2:amd64 3.2.5-0ubuntu2 gconf2:i386 3.2.5-0ubuntu2}>) of a supposedly unresolved dependency is already installed in step 2958
Internal error: the solver Install(gconf2:i386 3.2.5-0ubuntu2 <metacity-common:amd64 1:2.34.1-1ubuntu11 -> {gconf2:amd64 3.2.5-0ubuntu2 gconf2:i386 3.2.5-0ubuntu2}>) of a supposedly unresolved dependency is already installed in step 2958
Internal error: the solver Install(gconf2:i386 3.2.5-0ubuntu2 <libgweather-common:amd64 3.4.1-0ubuntu1 -> {gconf2:amd64 3.2.5-0ubuntu2 gconf2:i386 3.2.5-0ubuntu2}>) of a supposedly unresolved dependency is already installed in step 2958
Internal error: the solver Install(gconf2:i386 3.2.5-0ubuntu2 <libcompizconfig0:amd64 0.9.7.0~bzr428-0ubuntu6 -> {gconf2:amd64 3.2.5-0ubuntu2 gconf2:i386 3.2.5-0ubuntu2}>) of a supposedly unresolved dependency is already installed in step 2958
Internal error: the solver Install(gconf2:i386 3.2.5-0ubuntu2 <gnome-terminal-data:amd64 3.4.1.1-0ubuntu1 -> {gconf2:amd64 3.2.5-0ubuntu2 gconf2:i386 3.2.5-0ubuntu2}>) of a supposedly unresolved dependency is already installed in step 2958
Internal error: the solver Install(gconf2:i386 3.2.5-0ubuntu2 <gstreamer0.10-gconf:amd64 0.10.31-1ubuntu1.2 -> {gconf2:amd64 3.2.5-0ubuntu2 gconf2:i386 3.2.5-0ubuntu2}>) of a supposedly unresolved dependency is already installed in step 3165
Internal error: the solver Install(gconf2:i386 3.2.5-0ubuntu2 <gnome-panel-data:amd64 1:3.4.1-0ubuntu1.2 -> {gconf2:amd64 3.2.5-0ubuntu2 gconf2:i386 3.2.5-0ubuntu2}>) of a supposedly unresolved dependency is already installed in step 3165
Internal error: the solver Install(gconf2:i386 3.2.5-0ubuntu2 <libgnome2-common:amd64 2.32.1-2ubuntu1.1 -> {gconf2:amd64 3.2.5-0ubuntu2 gconf2:i386 3.2.5-0ubuntu2}>) of a supposedly unresolved dependency is already installed in step 3165
Internal error: the solver Install(gconf2:i386 3.2.5-0ubuntu2 <unity-common:amd64 5.20.0-0ubuntu3 -> {gconf2:amd64 3.2.5-0ubuntu2 gconf2:i386 3.2.5-0ubuntu2}>) of a supposedly unresolved dependency is already installed in step 3165
Internal error: the solver Install(gconf2:i386 3.2.5-0ubuntu2 <compiz-plugins-main-default:amd64 1:0.9.7.0~bzr19-0ubuntu10.1 -> {gconf2:amd64 3.2.5-0ubuntu2 gconf2:i386 3.2.5-0ubuntu2}>) of a supposedly unresolved dependency is already installed in step 3165
Internal error: the solver Install(gconf2:i386 3.2.5-0ubuntu2 <mutter-common:amd64 3.4.1-0ubuntu1 -> {gconf2:amd64 3.2.5-0ubuntu2 gconf2:i386 3.2.5-0ubuntu2}>) of a supposedly unresolved dependency is already installed in step 3165
Internal error: the solver Install(gconf2:i386 3.2.5-0ubuntu2 <gnome-applets-data:amd64 3.4.1-0ubuntu1 -> {gconf2:amd64 3.2.5-0ubuntu2 gconf2:i386 3.2.5-0ubuntu2}>) of a supposedly unresolved dependency is already installed in step 3165
Internal error: the solver Install(gconf2:i386 3.2.5-0ubuntu2 <metacity-common:amd64 1:2.34.1-1ubuntu11 -> {gconf2:amd64 3.2.5-0ubuntu2 gconf2:i386 3.2.5-0ubuntu2}>) of a supposedly unresolved dependency is already installed in step 3165
Internal error: the solver Install(gconf2:i386 3.2.5-0ubuntu2 <libgweather-common:amd64 3.4.1-0ubuntu1 -> {gconf2:amd64 3.2.5-0ubuntu2 gconf2:i386 3.2.5-0ubuntu2}>) of a supposedly unresolved dependency is already installed in step 3165
Internal error: the solver Install(gconf2:i386 3.2.5-0ubuntu2 <libcompizconfig0:amd64 0.9.7.0~bzr428-0ubuntu6 -> {gconf2:amd64 3.2.5-0ubuntu2 gconf2:i386 3.2.5-0ubuntu2}>) of a supposedly unresolved dependency is already installed in step 3165
Internal error: the solver Install(gconf2:i386 3.2.5-0ubuntu2 <gnome-terminal-data:amd64 3.4.1.1-0ubuntu1 -> {gconf2:amd64 3.2.5-0ubuntu2 gconf2:i386 3.2.5-0ubuntu2}>) of a supposedly unresolved dependency is already installed in step 3165
Internal error: the solver Install(pkg-config:i386 0.26-1ubuntu1 <libglib2.0-dev:amd64 2.32.4-0ubuntu1 -> {pkg-config:amd64 0.26-1ubuntu1 pkg-config:i386 0.26-1ubuntu1}>) of a supposedly unresolved dependency is already installed in step 3178
Internal error: the solver Install(pkg-config:i386 0.26-1ubuntu1 <libglib2.0-dev:amd64 2.32.4-0ubuntu1 -> {pkg-config:amd64 0.26-1ubuntu1 pkg-config:i386 0.26-1ubuntu1}>) of a supposedly unresolved dependency is already installed in step 3181
The following actions will resolve these dependencies:


       Remove the following packages:                                           
1)       aisleriot                                                              
2)       alacarte                                                               
3)       appmenu-gtk                                                            
4)       appmenu-gtk3                                                           
5)       apport-gtk                                                             
6)       apturl                                                                 
7)       avahi-daemon                                                           
8)       avahi-utils                                                            
9)       bamfdaemon                                                             
10)      baobab                                                                 
11)      bluez-cups                                                             
12)      brasero                                                                
13)      brasero-cdrkit                                                         
14)      chromium-browser                                                       
15)      chromium-browser-l10n                                                  
16)      chromium-codecs-ffmpeg-extra                                           
17)      colord                                                                 
18)      compiz                                                                 
19)      compiz-gnome                                                           
20)      compizconfig-settings-manager                                          
21)      cups                                                                   
22)      cups-bsd                                                               
23)      cups-client                                                            
24)      cups-filters                                                           
25)      cups-pk-helper                                                         
26)      cups-ppdc                                                              
27)      default-jre                                                            
28)      default-jre-headless                                                   
29)      deja-dup                                                               
30)      empathy                                                                
31)      eog                                                                    
32)      evince                                                                 
33)      evolution-data-server                                                  
34)      exo-utils                                                              
35)      file-roller                                                            
36)      flashplugin-installer                                                  
37)      gcalctool                                                              
38)      gconf-editor                                                           
39)      gedit                                                                  
40)      ghostscript                                                            
41)      ghostscript-cups                                                       
42)      ghostscript-x                                                          
43)      gimp                                                                   
44)      ginn                                                                   
45)      gir1.2-appindicator3-0.1                                               
46)      gir1.2-caribou-1.0                                                     
47)      gir1.2-clutter-1.0                                                     
48)      gir1.2-dbusmenu-glib-0.4                                               
49)      gir1.2-dbusmenu-gtk-0.4                                                
50)      gir1.2-gkbd-3.0                                                        
51)      gir1.2-gnomebluetooth-1.0                                              
52)      gir1.2-gtk-2.0                                                         
53)      gir1.2-gtk-3.0                                                         
54)      gir1.2-gtksource-3.0                                                   
55)      gir1.2-indicate-0.7                                                    
56)      gir1.2-launchpad-integration-3.0                                       
57)      gir1.2-mutter-3.0                                                      
58)      gir1.2-panelapplet-4.0                                                 
59)      gir1.2-peas-1.0                                                        
60)      gir1.2-rb-3.0                                                          
61)      gir1.2-totem-1.0                                                       
62)      gir1.2-unity-5.0                                                       
63)      gir1.2-vte-2.90                                                        
64)      gir1.2-webkit-3.0                                                      
65)      gir1.2-wnck-3.0                                                        
66)      gksu                                                                   
67)      gnome-applets                                                          
68)      gnome-bluetooth                                                        
69)      gnome-contacts                                                         
70)      gnome-control-center                                                   
71)      gnome-disk-utility                                                     
72)      gnome-font-viewer                                                      
73)      gnome-games-data                                                       
74)      gnome-icon-theme                                                       
75)      gnome-icon-theme-full                                                  
76)      gnome-icon-theme-symbolic                                              
77)      gnome-keyring                                                          
78)      gnome-media                                                            
79)      gnome-nettool                                                          
80)      gnome-online-accounts                                                  
81)      gnome-orca                                                             
82)      gnome-panel                                                            
83)      gnome-power-manager                                                    
84)      gnome-screensaver                                                      
85)      gnome-screenshot                                                       
86)      gnome-session                                                          
87)      gnome-session-bin                                                      
88)      gnome-session-canberra                                                 
89)      gnome-session-fallback                                                 
90)      gnome-settings-daemon                                                  
91)      gnome-shell                                                            
92)      gnome-sudoku                                                           
93)      gnome-system-log                                                       
94)      gnome-system-monitor                                                   
95)      gnome-terminal                                                         
96)      gnome-themes-standard                                                  
97)      gnome-tweak-tool                                                       
98)      gnome-user-guide                                                       
99)      gnome-user-share                                                       
100)     gnomine                                                                
101)     gparted                                                                
102)     gs-cjk-resource                                                        
103)     gtk2-engines                                                           
104)     gtk2-engines-murrine                                                   
105)     gtk3-engines-unico                                                     
106)     gucharmap                                                              
107)     gvfs-backends                                                          
108)     gwibber                                                                
109)     gwibber-service                                                        
110)     gwibber-service-facebook                                               
111)     gwibber-service-identica                                               
112)     gwibber-service-twitter                                                
113)     hplip                                                                  
114)     humanity-icon-theme                                                    
115)     ibus                                                                   
116)     ibus-gtk                                                               
117)     ibus-gtk3                                                              
118)     ibus-pinyin                                                            
119)     ibus-table                                                             
120)     icedtea-6-jre-cacao                                                    
121)     icedtea-6-jre-jamvm                                                    
122)     indicator-applet-complete                                              
123)     indicator-application                                                  
124)     indicator-appmenu                                                      
125)     indicator-datetime                                                     
126)     indicator-messages                                                     
127)     indicator-power                                                        
128)     indicator-printers                                                     
129)     indicator-session                                                      
130)     indicator-sound                                                        
131)     indicator-status-provider-mc5                                          
132)     jockey-gtk                                                             
133)     landscape-client-ui-install                                            
134)     language-selector-gnome                                                
135)     libappindicator1                                                       
136)     libappindicator3-1                                                     
137)     libatk-wrapper-java-jni                                                
138)     libavahi-client3                                                       
139)     libavahi-common-data                                                   
140)     libavahi-common3                                                       
141)     libavahi-core7                                                         
142)     libavahi-glib1                                                         
143)     libavahi-gobject0                                                      
144)     libavahi-ui-gtk3-0                                                     
145)     libbamf0                                                               
146)     libbamf3-0                                                             
147)     libbrasero-media3-1                                                    
148)     libc6:i386                                                             
149)     libcanberra-gtk-module                                                 
150)     libcanberra-gtk0                                                       
151)     libcanberra-gtk3-0                                                     
152)     libcanberra-gtk3-module                                                
153)     libcaribou0                                                            
154)     libclutter-1.0-0                                                       
155)     libcups2                                                               
156)     libcupscgi1                                                            
157)     libcupsdriver1                                                         
158)     libcupsfilters1                                                        
159)     libcupsimage2                                                          
160)     libcupsmime1                                                           
161)     libcupsppdc1                                                           
162)     libdbusmenu-glib4                                                      
163)     libdbusmenu-gtk3-4                                                     
164)     libdbusmenu-gtk4                                                       
165)     libdmapsharing-3.0-2                                                   
166)     libedataserverui-3.0-1                                                 
167)     libevince3-3                                                           
168)     libexo-1-0                                                             
169)     libfm-gtk-data                                                         
170)     libfm-gtk1                                                             
171)     libfolks-eds25                                                         
172)     libfreerdp-plugins-standard                                            
173)     libgail-3-0                                                            
174)     libgail-common                                                         
175)     libgail18                                                              
176)     libgcc1:i386                                                           
177)     libgcr-3-1                                                             
178)     libgdu-gtk0                                                            
179)     libgimp2.0                                                             
180)     libgksu2-0                                                             
181)     libglade2-0                                                            
182)     libgnome-bluetooth8                                                    
183)     libgnome-control-center1                                               
184)     libgnome-desktop-3-2                                                   
185)     libgnome-media-profiles-3.0-0                                          
186)     libgnomekbd7                                                           
187)     libgoa-1.0-0                                                           
188)     libgpm2:i386                                                           
189)     libgrip0                                                               
190)     libgs9                                                                 
191)     libgtk-3-0                                                             
192)     libgtk-3-bin                                                           
193)     libgtk2-perl                                                           
194)     libgtk2.0-0                                                            
195)     libgtk2.0-bin                                                          
196)     libgtk2.0-dev                                                          
197)     libgtkmm-2.4-1c2a                                                      
198)     libgtkmm-3.0-1                                                         
199)     libgtksourceview-3.0-0                                                 
200)     libgtkspell-3-0                                                        
201)     libgucharmap-2-90-7                                                    
202)     libgweather-3-0                                                        
203)     libgwibber-gtk2                                                        
204)     libgwibber2                                                            
205)     libido3-0.1-0                                                          
206)     libindicator3-7                                                        
207)     libindicator7                                                          
208)     liblaunchpad-integration-3.0-1                                         
209)     libmetacity-private0                                                   
210)     libmutter0                                                             
211)     libnautilus-extension1a                                                
212)     libncurses5:i386                                                       
213)     libnm-gtk0                                                             
214)     libnss-mdns                                                            
215)     libopencv-calib3d-dev                                                  
216)     libopencv-calib3d2.3                                                   
217)     libopencv-contrib-dev                                                  
218)     libopencv-contrib2.3                                                   
219)     libopencv-core-dev                                                     
220)     libopencv-dev                                                          
221)     libopencv-features2d-dev                                               
222)     libopencv-features2d2.3                                                
223)     libopencv-flann-dev                                                    
224)     libopencv-gpu-dev                                                      
225)     libopencv-highgui-dev                                                  
226)     libopencv-highgui2.3                                                   
227)     libopencv-imgproc-dev                                                  
228)     libopencv-legacy-dev                                                   
229)     libopencv-legacy2.3                                                    
230)     libopencv-ml-dev                                                       
231)     libopencv-objdetect-dev                                                
232)     libopencv-objdetect2.3                                                 
233)     libopencv-video-dev                                                    
234)     liboverlay-scrollbar-0.2-0                                             
235)     liboverlay-scrollbar3-0.2-0                                            
236)     libpanel-applet-4-0                                                    
237)     libpeas-1.0-0                                                          
238)     libpurple0                                                             
239)     libqtbamf1                                                             
240)     libreoffice-gnome                                                      
241)     libreoffice-gtk                                                        
242)     librhythmbox-core5                                                     
243)     librsvg2-common                                                        
244)     libsane                                                                
245)     libsane-hpaio                                                          
246)     libspectre1                                                            
247)     libstdc++6:i386                                                        
248)     libsyncdaemon-1.0-1                                                    
249)     libtimezonemap1                                                        
250)     libtinfo5:i386                                                         
251)     libtotem0                                                              
252)     libunique-3.0-0                                                        
253)     libunity-2d-private0                                                   
254)     libunity-core-5.0-5                                                    
255)     libunity-misc4                                                         
256)     libunity9                                                              
257)     libvte-2.90-9                                                          
258)     libvte9                                                                
259)     libwebkitgtk-1.0-0                                                     
260)     libwebkitgtk-3.0-0                                                     
261)     libwnck-3-0                                                            
262)     libwnck22                                                              
263)     libwxgtk2.8-0                                                          
264)     libyelp0                                                               
265)     light-themes                                                           
266)     lxshortcut                                                             
267)     mahjongg                                                               
268)     metacity                                                               
269)     mousetweaks                                                            
270)     nautilus                                                               
271)     nautilus-open-terminal                                                 
272)     nautilus-sendto                                                        
273)     nautilus-sendto-empathy                                                
274)     nautilus-share                                                         
275)     network-manager-gnome                                                  
276)     network-manager-pptp-gnome                                             
277)     notify-osd                                                             
278)     onboard                                                                
279)     oneconf                                                                
280)     openjdk-6-jre                                                          
281)     openjdk-6-jre-headless                                                 
282)     openjdk-6-jre-lib                                                      
283)     openjdk-7-jre-headless                                                 
284)     overlay-scrollbar                                                      
285)     pcmanfm                                                                
286)     policykit-1-gnome                                                      
287)     printer-driver-c2esp                                                   
288)     printer-driver-foo2zjs                                                 
289)     printer-driver-gutenprint                                              
290)     printer-driver-hpcups                                                  
291)     printer-driver-pnm2ppa                                                 
292)     printer-driver-ptouch                                                  
293)     printer-driver-sag-gdi                                                 
294)     printer-driver-splix                                                   
295)     prosper                                                                
296)     ps2eps                                                                 
297)     python-appindicator                                                    
298)     python-aptdaemon.gtk3widgets                                           
299)     python-cups                                                            
300)     python-glade2                                                          
301)     python-gmenu                                                           
302)     python-gnomekeyring                                                    
303)     python-gtk2                                                            
304)     python-ibus                                                            
305)     python-matplotlib                                                      
306)     python-notify                                                          
307)     python-opencv                                                          
308)     python-ubuntu-sso-client                                               
309)     python-ubuntuone-control-panel                                         
310)     python-virtkey                                                         
311)     python-wxgtk2.8                                                        
312)     remmina                                                                
313)     remmina-plugin-rdp                                                     
314)     remmina-plugin-vnc                                                     
315)     rhythmbox                                                              
316)     rhythmbox-mozilla                                                      
317)     rhythmbox-plugin-cdrecorder                                            
318)     rhythmbox-plugin-magnatune                                             
319)     rhythmbox-plugins                                                      
320)     rhythmbox-ubuntuone                                                    
321)     sane-utils                                                             
322)     seahorse                                                               
323)     sessioninstaller                                                       
324)     shotwell                                                               
325)     simple-scan                                                            
326)     software-center                                                        
327)     software-properties-gtk                                                
328)     ssh-askpass-gnome                                                      
329)     synaptic                                                               
330)     system-config-printer-common                                           
331)     system-config-printer-gnome                                            
332)     system-config-printer-udev                                             
333)     telepathy-haze                                                         
334)     telepathy-indicator                                                    
335)     telepathy-salut                                                        
336)     thunderbird                                                            
337)     thunderbird-gnome-support                                              
338)     thunderbird-locale-en                                                  
339)     thunderbird-locale-en-us                                               
340)     totem                                                                  
341)     totem-mozilla                                                          
342)     totem-plugins                                                          
343)     transmission-gtk                                                       
344)     ubuntu-artwork                                                         
345)     ubuntu-desktop                                                         
346)     ubuntu-docs                                                            
347)     ubuntu-mono                                                            
348)     ubuntu-sso-client                                                      
349)     ubuntu-sso-client-gtk                                                  
350)     ubuntuone-client                                                       
351)     ubuntuone-client-gnome                                                 
352)     ubuntuone-control-panel                                                
353)     ubuntuone-installer                                                    
354)     unity                                                                  
355)     unity-2d                                                               
356)     unity-2d-panel                                                         
357)     unity-2d-shell                                                         
358)     unity-2d-spread                                                        
359)     unity-asset-pool                                                       
360)     unity-greeter                                                          
361)     unity-lens-applications                                                
362)     unity-lens-files                                                       
363)     unity-lens-music                                                       
364)     unity-lens-video                                                       
365)     unity-scope-musicstores                                                
366)     unity-scope-video-remote                                               
367)     unity-services                                                         
368)     update-manager                                                         
369)     update-notifier                                                        
370)     usb-creator-gtk                                                        
371)     vino                                                                   
372)     xdg-user-dirs-gtk                                                      
373)     xdiagnose                                                              
374)     yelp                                                                   
375)     zenity                                                                 


       Keep the following packages at their current version:                    
376)     firefox:i386 [Not Installed]                                           
377)     libasound2:i386 [Not Installed]                                        
378)     libatk1.0-0:i386 [Not Installed]                                       
379)     libavahi-client3:i386 [Not Installed]                                  
380)     libavahi-common3:i386 [Not Installed]                                  
381)     libcairo2:i386 [Not Installed]                                         
382)     libcanberra0:i386 [Not Installed]                                      
383)     libcomerr2:i386 [Not Installed]                                        
384)     libcups2:i386 [Not Installed]                                          
385)     libdatrie1:i386 [Not Installed]                                        
386)     libdbus-1-3:i386 [Not Installed]                                       
387)     libdbus-glib-1-2:i386 [Not Installed]                                  
388)     libdbusmenu-glib4:i386 [Not Installed]                                 
389)     libdbusmenu-gtk4:i386 [Not Installed]                                  
390)     libelf1:i386 [Not Installed]                                           
391)     libexpat1:i386 [Not Installed]                                         
392)     libffi6:i386 [Not Installed]                                           
393)     libfontconfig1:i386 [Not Installed]                                    
394)     libfreetype6:i386 [Not Installed]                                      
395)     libgcrypt11:i386 [Not Installed]                                       
396)     libgdk-pixbuf2.0-0:i386 [Not Installed]                                
397)     libglib2.0-0:i386 [Not Installed]                                      
398)     libgnutls26:i386 [Not Installed]                                       
399)     libgpg-error0:i386 [Not Installed]                                     
400)     libgssapi-krb5-2:i386 [Not Installed]                                  
401)     libgtk2.0-0:i386 [Not Installed]                                       
402)     libice6:i386 [Not Installed]                                           
403)     libjasper1:i386 [Not Installed]                                        
404)     libjpeg-turbo8:i386 [Not Installed]                                    
405)     libjpeg8:i386 [Not Installed]                                          
406)     libk5crypto3:i386 [Not Installed]                                      
407)     libkeyutils1:i386 [Not Installed]                                      
408)     libkrb5-3:i386 [Not Installed]                                         
409)     libkrb5support0:i386 [Not Installed]                                   
410)     libltdl7:i386 [Not Installed]                                          
411)     libogg0:i386 [Not Installed]                                           
412)     libp11-kit0:i386 [Not Installed]                                       
413)     libpango1.0-0:i386 [Not Installed]                                     
414)     libpcre3:i386 [Not Installed]                                          
415)     libpixman-1-0:i386 [Not Installed]                                     
416)     libpng12-0:i386 [Not Installed]                                        
417)     libselinux1:i386 [Not Installed]                                       
418)     libsm6:i386 [Not Installed]                                            
419)     libstartup-notification0:i386 [Not Installed]                          
420)     libtasn1-3:i386 [Not Installed]                                        
421)     libtdb1:i386 [Not Installed]                                           
422)     libthai0:i386 [Not Installed]                                          
423)     libtiff4:i386 [Not Installed]                                          
424)     libuuid1:i386 [Not Installed]                                          
425)     libvorbis0a:i386 [Not Installed]                                       
426)     libvorbisfile3:i386 [Not Installed]                                    
427)     libx11-6:i386 [Not Installed]                                          
428)     libx11-xcb1:i386 [Not Installed]                                       
429)     libxau6:i386 [Not Installed]                                           
430)     libxcb-render0:i386 [Not Installed]                                    
431)     libxcb-shm0:i386 [Not Installed]                                       
432)     libxcb-util0:i386 [Not Installed]                                      
433)     libxcb1:i386 [Not Installed]                                           
434)     libxcomposite1:i386 [Not Installed]                                    
435)     libxcursor1:i386 [Not Installed]                                       
436)     libxdamage1:i386 [Not Installed]                                       
437)     libxdmcp6:i386 [Not Installed]                                         
438)     libxext6:i386 [Not Installed]                                          
439)     libxfixes3:i386 [Not Installed]                                        
440)     libxft2:i386 [Not Installed]                                           
441)     libxi6:i386 [Not Installed]                                            
442)     libxinerama1:i386 [Not Installed]                                      
443)     libxrandr2:i386 [Not Installed]                                        
444)     libxrender1:i386 [Not Installed]                                       
445)     libxt6:i386 [Not Installed]                                            
446)     zlib1g:i386 [Not Installed]                                            


       Leave the following dependencies unresolved:                             
447)     foomatic-db-compressed-ppds recommends ghostscript                     
448)     foomatic-db-compressed-ppds recommends cups                            
449)     foomatic-db-compressed-ppds recommends cups-client                     
450)     foomatic-db-compressed-ppds recommends printer-driver-pnm2ppa          
451)     foomatic-db-engine recommends cups                                     
452)     foomatic-db-engine recommends cups-client                              
453)     gedit-common recommends gedit                                          
454)     gnome-terminal-data recommends gnome-terminal                          
455)     ibus recommends ibus-gtk3 | ibus-qt4 | ibus-clutter                    
456)     libatk-wrapper-java recommends libatk-wrapper-java-jni                 
457)     libcanberra-gtk0 recommends libcanberra-gtk-module                     
458)     libfolks25 recommends libfolks-eds25                                   
459)     libgtk2.0-common recommends libgtk2.0-0                                
460)     libnotify4 recommends notification-daemon                              
461)     metacity recommends gnome-session | x-session-manager                  
462)     netpbm recommends ghostscript                                          
463)     network-manager-pptp recommends network-manager-pptp-gnome | plasma-wid
464)     openprinting-ppds recommends cups                                      
465)     openprinting-ppds recommends cups-client                               
466)     printer-driver-foo2zjs recommends cups                                 
467)     printer-driver-min12xxw recommends cups                                
468)     printer-driver-min12xxw recommends ghostscript                         
469)     texlive-extra-utils recommends ghostscript                             
470)     texlive-font-utils recommends ghostscript                              
471)     texlive-latex-recommended recommends prosper (>= 1.00.4+cvs.2006.10.22-
472)     texlive-pstricks recommends ps2eps                                     
473)     gnome-applets recommends gnome-system-monitor                          
474)     gnome-shell recommends gnome-contacts                                  
475)     gnome-shell recommends gnome-session-fallback                          
476)     gnome-shell recommends gnome-user-guide                                
477)     indicator-applet-complete recommends indicator-session                 
478)     indicator-applet-complete recommends indicator-application             
479)     pcmanfm recommends gvfs-backends                                       
480)     pcmanfm recommends lxshortcut                                          
481)     python-matplotlib recommends python-glade2                             
482)     python-pandas recommends python-matplotlib                             
483)     python-scikits.statsmodels recommends python-matplotlib                
484)     ubuntu-restricted-addons recommends flashplugin-installer              
485)     libncurses5:i386 recommends libgpm2:i386                               
486)     ghostscript-cups recommends cups                                       
487)     gimp recommends ghostscript                                            
488)     gimp-data recommends gimp                                              
489)     gnome-online-accounts recommends gnome-control-center                  
490)     hplip recommends sane-utils                                            
491)     imagemagick recommends ghostscript                                     
492)     libgtk-3-common recommends libgtk-3-0                                  
493)     libmagickcore4 recommends ghostscript                                  
494)     libqtgui4 recommends libcups2                                          
495)     libsane-hpaio recommends sane-utils                                    
496)     libsane-hpaio recommends hplip (= 3.12.2-1ubuntu3.5)                   
497)     poppler-utils recommends ghostscript                                   
498)     printer-driver-hpijs recommends ghostscript                            
499)     printer-driver-hpijs recommends cups (>= 1.4.0) | cupsddk | hpijs-ppds 
500)     ubuntuone-client recommends ubuntuone-installer (>= 2.99.5-0ubuntu3)   
501)     firefox:i386 recommends libdbusmenu-gtk4:i386                          
502)     pepflashplugin-installer recommends chromium-browser (>= 23.0)         
503)     empathy-common recommends yelp                                         
504)     unity-greeter recommends indicator-datetime                            
505)     unity-greeter recommends indicator-power                               
506)     unity-greeter recommends indicator-session                             
507)     empathy recommends telepathy-salut                                     
508)     empathy recommends telepathy-indicator                                 
509)     unity-2d-shell recommends unity-lens-files                             
510)     unity-2d-shell recommends unity-lens-applications                      
511)     unity-2d-shell recommends unity-lens-music                             
512)     unity recommends indicator-appmenu                                     
513)     unity recommends indicator-application                                 
514)     unity recommends indicator-datetime                                    
515)     unity recommends indicator-printers                                    
516)     unity recommends indicator-power                                       
517)     unity recommends indicator-session                                     
518)     gnome-panel recommends gnome-applets                                   
519)     gnome-panel recommends gnome-session (>= 2.26)                         
520)     gnome-panel recommends gnome-session-fallback                          
521)     gnome-panel recommends gnome-control-center                            
522)     gnome-panel recommends evolution-data-server                           
523)     gnome-panel recommends gnome-settings-daemon                           
524)     gnome-panel recommends indicator-applet-complete                       
525)     rhythmbox-plugins recommends nautilus-sendto                           
526)     gnome-accessibility-themes recommends gtk2-engines                     
527)     gnome-control-center-data recommends gnome-control-center (>= 1:3.4.2-0
528)     rhythmbox recommends yelp                                              
529)     rhythmbox recommends avahi-daemon                                      
530)     rhythmbox recommends notification-daemon                               
531)     rhythmbox recommends gvfs-backends                                     
532)     rhythmbox recommends rhythmbox-plugins                                 
533)     totem-mozilla recommends firefox | epiphany-browser | www-browser      
534)     ubuntu-sso-client recommends ubuntu-sso-client-gtk | ubuntu-sso-client-
535)     remmina recommends remmina-plugin-vnc                                  
536)     libappindicator1 recommends indicator-application (>= 0.2.93)          
537)     unity-2d-panel recommends indicator-application                        
538)     unity-2d-panel recommends indicator-appmenu                            
539)     unity-2d-panel recommends indicator-datetime                           
540)     unity-2d-panel recommends indicator-messages                           
541)     unity-2d-panel recommends indicator-session                            
542)     unity-2d-panel recommends indicator-sound                              
543)     gnome-media recommends gnome-control-center                            
544)     remmina-common recommends remmina                                      
545)     libpam-gnome-keyring recommends gnome-keyring                          
546)     gnome-control-center recommends gnome-session-bin                      
547)     gnome-control-center recommends mousetweaks                            
548)     gnome-control-center recommends indicator-power (>= 1.90)              
549)     gcalctool recommends yelp                                              
550)     synaptic recommends libgtk2-perl (>= 1:1.130)                          
551)     nautilus-sendto-empathy recommends nautilus-sendto (>= 2.28.2-2)       
552)     update-notifier recommends apport-gtk                                  
553)     update-notifier recommends python-aptdaemon.gtk3widgets | synaptic     
554)     libappindicator3-1 recommends indicator-application (>= 0.2.93)        
555)     foomatic-filters recommends cups-client | lpr | lprng | rlpr           
556)     foomatic-filters recommends ghostscript                                
557)     foomatic-filters recommends cups | enscript | a2ps | mpage             
558)     foomatic-filters recommends colord                                     
559)     nautilus recommends brasero (>= 2.26)                                  
560)     nautilus recommends librsvg2-common                                    
561)     nautilus recommends gvfs-backends                                      
562)     ubuntu-desktop recommends aisleriot                                    
563)     ubuntu-desktop recommends bluez-cups                                   
564)     ubuntu-desktop recommends brasero                                      
565)     ubuntu-desktop recommends cups                                         
566)     ubuntu-desktop recommends cups-bsd                                     
567)     ubuntu-desktop recommends cups-client                                  
568)     ubuntu-desktop recommends empathy                                      
569)     ubuntu-desktop recommends gnome-bluetooth                              
570)     ubuntu-desktop recommends gnome-disk-utility                           
571)     ubuntu-desktop recommends gnome-screensaver                            
572)     ubuntu-desktop recommends hplip                                        
573)     ubuntu-desktop recommends ibus-gtk3                                    
574)     ubuntu-desktop recommends mousetweaks                                  
575)     ubuntu-desktop recommends nautilus-share                               
576)     ubuntu-desktop recommends network-manager-pptp-gnome                   
577)     ubuntu-desktop recommends printer-driver-c2esp                         
578)     ubuntu-desktop recommends printer-driver-foo2zjs                       
579)     ubuntu-desktop recommends printer-driver-splix                         
580)     ubuntu-desktop recommends ubuntuone-client-gnome                       
581)     rhythmbox-mozilla recommends firefox | epiphany-browser | www-browser  
582)     deja-dup recommends gvfs-backends                                      
583)     oneconf recommends software-center (>= 4.1.21)                         
584)     oneconf recommends update-notifier (>= 0.103)                          
585)     totem-plugins recommends gnome-settings-daemon                         
586)     lightdm recommends unity-greeter | lightdm-greeter                     
587)     rhythmbox-data recommends rhythmbox                                    
588)     gnome-panel-data recommends gnome-panel                                
589)     system-config-printer-common recommends system-config-printer-udev     
590)     system-config-printer-common recommends avahi-utils                    
591)     network-manager recommends network-manager-gnome | network-manager-kde 
592)     python-debtagshw recommends sane-utils                                 
593)     python-debtagshw recommends python-cups                                
594)     onboard recommends gir1.2-appindicator3-0.1                            
595)     gvfs-daemons recommends policykit-1-gnome                              
596)     libcolord1 recommends colord                                           
597)     update-manager recommends gir1.2-dbusmenu-gtk-0.4                      
598)     update-manager recommends gir1.2-unity-5.0                             
599)     update-manager recommends gir1.2-webkit-3.0                            
600)     unity-lens-music recommends unity-scope-musicstores                    




Accept this solution? [Y/n/q/?] Abandoning all efforts to resolve these dependencies.
Abort.

```

It looks like on 12.04 it is impossible for me to install the 32 bit version of firefox without removing a bunch of packages and replacing them with 32 bit versions.  How is 14.04 able to do this?

---

### Post by vasa1 on 2015-11-19
So are you currently without any version of Firefox at all?

And could you share why you need 32-bit Firefox?

---

### Post by necbot on 2015-11-19
> **vasa1 said:**
> So are you currently without any version of Firefox at all?

And could you share why you need 32-bit Firefox?

Yes, I'm currently without any version of firefox.  I need 32 bit firefox because my employer's vpn uses a 32 bit java plugin for authentication and this plugin will only work with 32 bit firefox.  Attempting to use this plugin with any other browser has failed and I've long since given up on that.

---

### Post by mc4man on 2015-11-19
> **mc4man said:**
> Putting aside your particular install & Ubuntu release version I'm not too sure that anyone can install firefox:i386 on a 64 bit install, at least in Ubuntu.
 
It's seems that in 14.04 you can install the 32 bit FF, I'd been trying on 16.04 & there it wasn't going to happen. It likely was from a couple of packages I updated from propsed that were causing the issue.
Trying the same in 14.04 the install of 32 bit FF went thru without issue, only the existing 64 bit FF had to be removed.
I think you may be seeing something similar as for example - 
libcomerr2 : Breaks: libcomerr2:i386 (!= 1.42-1ubuntu2.3) but 1.42-1ubuntu2.2 is to be installed.
This means that 1.42-1ubuntu2.2 is installed but the i386 version is the new updates version 1.42-1ubuntu2.3

So I think you can do this in 12.04.
First open software sources & on the 'Updates' tab make sure the top 2 are enabled (security & updates, likely both are.
Then update (reload) your sources if need be  & go 
```
sudo apt-get upgrade
```
When that completes then try again to install firefox - 
sudo aptitude install firefox:i386

---

