---
title: "The following packages have unmet dependencies:   libc6"
date: 2016-06-05
forum: General Help
---

### Post by Abdullah_Al_Jasir on 2016-06-05
Hi guys. I recently installed a plain copy of GNOME and performed following commands before my problem occured. 
Generally I needed to upgrade my wine1.2 to 1.4:
[COLOR=#ff0000]apt-get update
apt-get upgrade[/COLOR]

Here is the results on: [COLOR=#ff0000]lsb_release -a[/COLOR]
```

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04 LTS
Release:    12.04
Codename:    precise

```

Here is the results on my [COLOR=#ff0000]source.list[/COLOR]
```

deb http://cy.archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse 
deb-src http://cy.archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse 

```

Here is error on: [COLOR=#ff0000]apt-get -f dist-upgrade[/COLOR]
```
E: Could not perform immediate configuration on 'python2.7-minimal'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)
```

Here is error when i perform: [COLOR=#ff0000]apt-get install -o APT::Immediate-Configure=false -f apt python-minimal[/COLOR]
```

The following packages have unmet dependencies:
  apt: Depends: libapt-pkg4.12 (>= 0.8.16~exp12ubuntu10) but it is not going to be installed
       Depends: libc6 (>= 2.15) but 2.11.1-0ubuntu7.10 is to be installed
       Depends: libstdc++6 (>= 4.6) but 4.4.3-4ubuntu5.1 is to be installed
       PreDepends: dpkg (>= 1.15.7.2) but 1.15.5.6ubuntu4.5 is to be installed
  apt-transport-https: Depends: libapt-pkg-libc6.10-6-4.8
  apt-utils: Depends: libapt-pkg-libc6.10-6-4.8
  aptitude: Depends: libapt-pkg-libc6.10-6-4.8
  libc6: Depends: libc-bin (= 2.11.1-0ubuntu7.10) but 2.15-0ubuntu10 is to be installed
         Recommends: libc6-i686
  libept0: Depends: libapt-pkg-libc6.10-6-4.8
  python: Depends: python-minimal (= 2.6.5-0ubuntu1) but 2.7.3-0ubuntu2 is to be installed
  python-apt: Depends: libapt-pkg-libc6.10-6-4.8
  python-minimal: Depends: python2.7-minimal (>= 2.7.3) but it is not going to be installed
                  Breaks: python-support (< 1.0.10ubuntu2) but 1.0.4ubuntu1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Here is error on: [COLOR=#ff0000]apt-get -f install[/COLOR]
```

dpkg: warning: files list file for package `libxau6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkrb5-3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libwrap0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gcc-4.4-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcupsimage2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcap2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxt6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgomp1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgphoto2-port0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mysql-client-5.1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libscope-guard-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpcsclite1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libvisual-0.4-plugins' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libstdc++6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmad0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgsm1-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mysql-server-core-5.1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `reiserfsprogs' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `lame' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsql-translator-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxcursor1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libclass-mop-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxcb-xv0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpixman-1-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpng12-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxxf86vm1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsm6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libc6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtalloc2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libaa1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libselinux1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libnih-dbus1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxcb-shape0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libice6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcdparanoia0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxtst6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libedit2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libavahi-client3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpciaccess0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `zlib1g-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgphoto2-2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libvorbis0a' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtag1c2a' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liblua5.1-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcaca0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmp3lame0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpkcs11-helper1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libvisual-0.4-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openvpn-blacklist' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libbz2-1.0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxp6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libc-ares2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liblcms1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libx11-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsqlite3-ruby1.8' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libyaml-0-2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-pyicu' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsub-uplevel-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `warvox' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libavahi-compat-libdnssd1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxml2-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libncursesw5' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpcre3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ttf-symbol-replacement' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgpm2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libaccess-bridge-java-jni' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnutls26' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libavahi-common3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcroco3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libnih1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libssh-4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libatk1.0-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsigc++-2.0-0c2a' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libjasper1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsensors4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libx11-6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxau-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxft2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libbsd0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libavahi-common-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libss2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdatrie1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libblkid1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libslang2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `portaudio19-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libaudio2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpthread-stubs0-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libacl1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtest-exception-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libiec61883-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsasl2-2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsasl2-modules' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgfortran3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmng1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxaw7' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxdamage1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmpg123-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `wine1.2-gecko' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxmu6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsndfile1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxfixes3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libopenal1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdb4.8' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdb4.6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpst4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openvas' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcomerr2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkrb5support0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openvas-check-setup' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `e2fslibs' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libshout3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpulse0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxcb-render0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `bogl-bterm' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `greenbone-security-desktop' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libatm1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtheora0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libidn11' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libspeexdsp1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `bluez-alsa' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpcap0.8' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libattr1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxi6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcairomm-1.0-1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgdu0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libreadline-ruby' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libportaudio2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `wine' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libexpat1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libltdl7' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `rdate' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libvorbisenc2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkeyutils1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openvas-administrator' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libreadline6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcups2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsqlite3-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libasound2-plugins' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libbluetooth3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsmbclient' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libasound2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libwxbase2.8-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdv4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxv1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxcomposite1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgcc1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxcb1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsvn1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `sqlfairy' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libglu1-mesa' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxrandr2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libiaxclient-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `zlib1g' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libnl1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsdl-image1.2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtdb1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxpm4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-libc-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtag1-vanilla' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liboil0.3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libatasmart4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libthai0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxrender1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liblzo2-2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libts-0.0-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libogg0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libusb-1.0-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libfontconfig1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libudev0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libavahi-glib1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsepol1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpulse-mainloop-glib0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `greenbone-security-assistant' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdigest-sha1-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libk5crypto3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxcb1-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgif4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpthread-stubs0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libasound2-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxdmcp-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxslt1.1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libwavpack1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libssl0.9.8' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libc6-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsamplerate0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxslt1-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openvas-scanner' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgudev-1.0-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxss1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libwbclient0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openvas-manager' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsybdb5' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgssrpc4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgpg-error0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsqlite3-ruby' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libavc1394-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libusb-0.1-4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpci3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpam0g' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpopt0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libspeex1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgssapi-krb5-2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libjpeg62' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libparted0debian1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtasn1-3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libuuid1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxinerama1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgcrypt11' missing, assuming package has no files currently installed.
(Reading database ... 5%
dpkg: warning: files list file for package `libexif12' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgdbm3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcairo2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openvas-cli' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libflac8' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libvorbisfile3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libperl5.10' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdbus-1-3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openssl-blacklist' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxml2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxmuu1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxcb-shm0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libfreetype6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxdmcp6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libraw1394-11' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libltdl-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libelf1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mysql-client-core-5.1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libexempi3' missing, assuming package has no files currently installed.
(Reading database ... 256965 files and directories currently installed.)
Preparing to replace libc6 2.11.1-0ubuntu7.10 (using .../libc6_2.15-0ubuntu10_i386.deb) ...
Checking for services that may need to be restarted...
Checking init scripts...
Checking for services that may need to be restarted...
Checking init scripts...
WARNING: init script for nis not found.
Stopping some services possibly affected by the upgrade (will be restarted later):
  cron: stopping...done.


A copy of the C library was found in an unexpected directory:
  '/lib/i386-linux-gnu/libc-2.15.so'
It is not safe to upgrade the C library in this situation;
please remove that copy of the C library or get it out of
'/lib/i386-linux-gnu' and try again.

dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu10_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.15-0ubuntu10_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

[COLOR=#ff0000]Note:[/COLOR][COLOR=#000000] I've tried removing the C library manually "[/COLOR][COLOR=#ff0000]/lib/i386-linux-gnu/libc-2.15.so[/COLOR][COLOR=#000000]" but my terminal crashes.[/COLOR][COLOR=#0000ff]
[/COLOR][COLOR=#000000]I've tried manually executing [/COLOR][COLOR=#ff0000]./libc6_2.15-0ubuntu10_i386.deb[/COLOR] [COLOR=#000000]in result i get error file corrupted.
I've tried to download it again by removing it from the archives "[/COLOR][COLOR=#ff0000]/var/cache/apt/archives/libc6_2.15-0ubuntu10_i386.deb[/COLOR][COLOR=#000000]".[/COLOR][COLOR=#0000ff]
[/COLOR][COLOR=#000000]It is my second time my Linux copy  breaks using apt-get.
I would like to fix my copy if possible solution instead of reinstalling[COLOR=#0000ff]. 
[/COLOR][/COLOR][COLOR=#000000]Is there anything i could do?

Thanks in advance.
[/COLOR]

---

### Post by mc4man on 2016-06-05
run & post
```
apt-cache policy libc6
```

---

### Post by Abdullah_Al_Jasir on 2016-06-05
[COLOR=#ff0000]apt-cache policy libc6[/COLOR]
```

libc6:
  Installed: 2.11.1-0ubuntu7.10
  Candidate: 2.15-0ubuntu10
  Version table:
     2.15-0ubuntu10 0
        500 http://cy.archive.ubuntu.com/ubuntu/ precise/main Packages
 *** 2.11.1-0ubuntu7.10 0
        100 /var/lib/dpkg/status


```

[COLOR=#ff0000]Note:[/COLOR] I have previously manually edited my "[COLOR=#ff0000]/var/lib/dpkg/status[/COLOR]"
Due to error in version on some packages.
But that was one of the errors i managed to solve after the upgrade.

---

### Post by mc4man on 2016-06-05
Well your current libc6 is from lucid (10.04) When is the last time you updated??

---

### Post by Abdullah_Al_Jasir on 2016-06-05
I always [COLOR=#ff0000]update[/COLOR].
My Linux copy is pretty old.
I noticed the repositories I use are precise.
Should I be looking for new repositories?
Or should I be looking for newer release of Linux?

```

Hit http://cy.archive.ubuntu.com precise Release.gpg
Ign http://cy.archive.ubuntu.com/ubuntu/ precise/main Translation-en_US
Ign http://cy.archive.ubuntu.com/ubuntu/ precise/restricted Translation-en_US
Ign http://cy.archive.ubuntu.com/ubuntu/ precise/universe Translation-en_US
Ign http://cy.archive.ubuntu.com/ubuntu/ precise/multiverse Translation-en_US
Hit http://cy.archive.ubuntu.com precise Release
Hit http://cy.archive.ubuntu.com precise/main Packages
Hit http://cy.archive.ubuntu.com precise/restricted Packages
Hit http://cy.archive.ubuntu.com precise/universe Packages
Hit http://cy.archive.ubuntu.com precise/multiverse Packages
Hit http://cy.archive.ubuntu.com precise/main Sources
Hit http://cy.archive.ubuntu.com precise/restricted Sources
Hit http://cy.archive.ubuntu.com precise/universe Sources
Hit http://cy.archive.ubuntu.com precise/multiverse Sources

```

---

### Post by mörgæs on 2016-06-06
> **Abdullah_Al_Jasir said:**
> 
Or should I be looking for newer release of Linux?


Yes, a fresh install (not upgrade) of 16.04 will solve many problems and give you a more recent Wine.

---

