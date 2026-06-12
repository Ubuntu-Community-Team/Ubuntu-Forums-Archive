---
title: "sudo apt-get install-f error"
date: 2020-12-28
forum: General Help
---

### Post by tel32 on 2020-12-28
It is not possible to install or remove any software. Please first use the "Synaptic" Package Manager to fix this situation, or type and run the "sudo apt-get install-f" command in the terminal window. I get this error when I update the software, and as soon as I write the command "sudo apt-get install-f", i get the following errors

```
omer@gokturk:~ $ sudo apt-get install-f
Reading package lists... It's over
Creating a dependency tree
Reading status... It's over
Fixing dependencies... Completed
The following packages are automatically installed and are no longer required:
apturl-common cabextract gir1. 2-Goa-1.0 glib-networking:i386 gstreamer1.0-plugins-base:i386 i965-va-driver:i386 intel-media-va-driver:i386
libaom0:libapparmor1 i386:i386 libasn1-8-heimdal:i386 libasound2:i386 libasound2-plugins:i386 libasyncns0:i386 libatk-bridge2.0-0:i386
libatk1.0-0:i386 libatspi2 libatopology2.0-0:i386 libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386 libavcodec58:i386
libavutil56:i386 libblkid1:i386 libbrotli1:i386 libbz2-1.0:i386 libcairo-gobject2:i386 libcairo2:i386 libcap2:i386 libcapi20-3 libcapi20-3:i386
libcdparanoia0:i386 libcodec2-0.9:i386 libcolord2:i386 libcom-err2:i386 libcups2:i386 libcurl3-gnutls:i386 libdatrie1:i386 libdb5.3:i386
libdbus-1-3:i386 libepoxy0:i386 libexif12:i386 libfaudio0 libfaudio0:i386 libflac8:i386 libfontconfig1:i386 libfreetype6:i386 libfribidi0:i386
libgcrypt20:i386 libgd3:i386 libgdbm-compat4:libgdbm6 i386:i386 libgdk-pixbuf2.0-0:i386 libgl1-mesa-glx:i386 libglib2.0-0:i386 libglu1-mesa:i386
libgmp10:i386 libgnutls30:i386 libgomp1:i386 libgpg-error0:i386 libgphoto2-6:i386 libgphoto2-port12:i386 libgpm2:i386 libgraphite2-3:i386
libgsm1:i386 libgssapi-krb5-2:i386 libgssapi3-heimdal:i386 libgstreamer-plugins-base1.0-0:i386 libgstreamer1.0-0:i386 libgtk-3-0:i386
libharfbuzz0b:i386 libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386 libhogweed5:i386 libhx509-5-heimdal:i386
libicu66:i386 libieee1284-3:i386 libigdgmm11:i386 libjack-jackd2-0:i386 libjbig0:i386 libjpeg-turbo8:i386 libjpeg8:i386 libjson-glib-1.0-0:i386
libk5crypto3:i386 libkeyutils1:i386 libkrb5-26-heimdal:i386 libkrb5-3:i386 libkrb5support0:i386 liblcms2-2:i386 libldap-2.4-2:i386 libltdl7:i386
liblz4-1:i386 liblzma5:i386 libmount1:i386 libmp3lame0:i386 libmpg123-0: i386 libmspack0 libmysqlclient21:i386 libncurses6:i386 libnettle7:i386
libnghttp2-14:i386 libnuma1:i386 libodbc1 libodbc1:i386 libogg0:i386 libopenal-data libopenal1 libopenal1:i386 libopenjp2-7:i386 libopus0:i386
liborc-0.4-0:i386 libosmesa6 libosmesa6:i386 libp11-kit0:i386 libpango-1.0-0:i386 libpangocairo-1.0-0:i386 libpangoft2-1.0-0:i386 libpcap0.8:i386
libpci3:i386 libpcre2-8-0:i386 libpcre3:i386 libperl5.30:i386 libpixman-1-0:i386 libpng16-16:libproxy1v5 i386:i386 libpsl5:i386 libpulse0:i386
librest-0.7-0:i386 libroken18-heimdal:i386 librsvg2-2:i386 librsvg2-common:i386 librtmp1:i386 libsamplerate0:i386 libsane:i386 libsasl2-2:i386
libsasl2-modules:i386 libsasl2-modules-db:i386 libsbc1 libsdl2-2.0-0 libsdl2-2.0-0:i386 libselinux1:i386 libshine3:libsnappy1v5 i386:i386
libsndfile1:i386 libsndio7.0 libsndio7.0:libsnmp35 i386:i386 libsoup-gnome2.4-1:i386 libsoup2.4-1:libsoxr0 i386:i386 libspeex1:i386
libsqlite3-0:i386 libssh-4:i386 libssl1.1:libstb0 libstb0 i386:i386 libswresample3:i386 libsystemd0:i386 libtasn1-6:i386 libthai0:i386
libtheora0:i386 libtiff5:i386 libtwolame0:i386 libudev1:i386 libusb-1.0-0:i386 libuuid1:i386 libv4l-0:i386 libv4lconvert0:i386 libva-drm2:i386
libva-x11-2:i386 libva2:i386 libvdpau1:i386 libvisual-0.4-0:i386 libvkd3d1 libvkd3d1:i386 libvorbis0a:i386 libvorbisenc2:i386 libvpx6:i386
libwavpack1:i386 libwayland-cursor0:i386 libwayland-egl1:i386 libwebp6:i386 libwebpmux3:i386 libwind0-heimdal:i386 libwrap0:i386 libx264-155:i386
libx265-179:i386 libxcb-render0:i386 libxcb-shm0:i386 libxcb-xfixes0:i386 libxcomposite1:i386 libxcursor1:i386 libxi6:i386 libxinerama1:i386
libxkbcommon0:i386 libxml2:i386 libxpm4:i386 libxrandr2:i386 libxrender1:i386 libxslt1.1:i386 libxss1:i386 libxvidcore4:i386 libzvbi0:i386
mesa-va-drivers: i386 mesa-vdpau-drivers:i386 ocl-icd-libopencl1:i386 python3-click python3-colorama python3-dateutil python3-software-properties
software-properties-common steam:i386 steam-devices unattended-upgrades va-driver-all:i386 vdpau-driver-all:i386 wine-devel-amd64
wine-devel-i386: i386 wine-stable-amd64 wine-stable-i386:i386 wine-staging-amd64 wine-staging-i386:i386
Use the 'sudo apt autoremove' command to remove these packages.
The following packages will be removed:
steam-installer wine-devel wine-stable wine-staging winehq-staging
0 packages will be upgraded, 0 new packages will be installed, 5 packages will be removed, and 0 packages will not be upgraded.
After this process is complete, 36.6 MB of disk space will be free.
Do you want to continue? [E/h] E
E: dpkg --set-selections subsystem sent an error code (100)
E: could not record the approved state changes as dpkg selection states
```

---

### Post by Bashing-om on 2020-12-28
tel32; Hello - Welcome to the forum :D

Let's see what we can do to find out why dpkg is unhappy.

Post back the results of terminal commands:
```

sudo apt update
sudo apt full-upgrade

```

Then we make consideration for "autoremove" and/or a manual intervention.

If the package manager is not happy
[INDENT][INDENT]no one is happy
[/INDENT][/INDENT]

---

### Post by tel32 on 2020-12-29
```
omer@gokturk: ~ $ sudo apt update
[sudo] password for omer:
Same: 1 [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) focal InRelease
Same: 2 [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) focal-updates InRelease
Same: 3 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) focal InRelease
Same: 4 [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) focal-backports InRelease
Download: 5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease [109 kB]
Same: 6 [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) focal InRelease
Same: 7 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) focal InRelease
6 sec.at 109 kB received (19.7 kB / s)
Reading package lists... It's over
Creating a dependency tree
Reading status... It's over
5 pack upgradeable. Run the 'apt list --upgradeable' command to see these packages.
```

```
omer@gokturk:~ $ sudo apt full-upgrade
Reading package lists... It's over
Creating a dependency tree
Reading status... It's over
You may need to run the 'apt --fix-broken install' command to fix these problems.
The following packages have unmet dependencies:
steam-installer: dependencies: steam (=1: 1.0.0.61-2ubuntu3) but not installable
wine-devel : dependencies: wine-devel-i386 (=6.0~rc3~focal) but not installable
wine-stable : dependencies: wine-stable-i386 (= 5.0.3~focal) but not installable
Wine-staging : dependencies: wine-staging-i386 (=6.0 ~ rc3~focal) but not installable
E: unmet dependencies. try the' apt --fix-broken install ' command without giving the package option (or specify a solution).
```


Now what do I write these commands

---

### Post by slickymaster on 2020-12-29
*Thread moved to **General Help**.*

---

### Post by tel32 on 2020-12-29
```
omer@gokturk:~ $ sudo apt-get install - f error
Reading package lists... It's over
Creating a dependency tree
Reading status... It's over
E: error package not found
```

---

### Post by ajgreeny on 2020-12-29
Remove the word **error** from that last command and try again. 
Your system is looking for a package named **error** which, of course, does not exist.

---

### Post by llamakc on 2020-12-29
The correct command it is asking for is 

```
sudo apt --fix-missing install
```

Which may also be entered as

```
sudo apt -f install
```

---

