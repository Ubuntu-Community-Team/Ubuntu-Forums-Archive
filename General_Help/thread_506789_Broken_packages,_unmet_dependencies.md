---
title: "Broken packages, unmet dependencies"
date: 2007-07-22
forum: General Help
---

### Post by Tallman on 2007-07-22
I'm dual booting Ubuntu 7.04 and Kubuntu 7.04. Problem arises in Kubuntu.

Here's my sources.list:

```
marpau@marpau-desktop:~$ cat /etc/apt/sources.list
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://nl.archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse

deb http://nl.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

deb http://nl.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.)
deb http://archive.canonical.com/ubuntu feisty-commercial main

## enlightenment e17 beta, use at your own risk
## E17 is in Beta and may break or break your system
deb http://edevelop.org/pkg-e/ubuntu feisty e17
deb http://e17.dunnewind.net/ubuntu feisty e17
deb-src http://edevelop.org/pkg-e/ubuntu feisty e17
marpau@marpau-desktop:~$
```

Then I do:

```
marpau@marpau-desktop:~$ sudo aptitude update
Get:1 http://nl.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://nl.archive.ubuntu.com feisty/main Translation-en_US
Ign http://nl.archive.ubuntu.com feisty/restricted Translation-en_US
Get:2 http://medibuntu.sos-sts.com feisty Release.gpg [189B]
Ign http://medibuntu.sos-sts.com feisty/free Translation-en_US
Ign http://nl.archive.ubuntu.com feisty/universe Translation-en_US
Ign http://nl.archive.ubuntu.com feisty/multiverse Translation-en_US
Get:3 http://archive.canonical.com feisty-commercial Release.gpg [191B]
Ign http://archive.canonical.com feisty-commercial/main Translation-en_US
Get:4 http://nl.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://nl.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://nl.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Get:5 http://nl.archive.ubuntu.com feisty-backports Release.gpg [191B]
Ign http://nl.archive.ubuntu.com feisty-backports/main Translation-en_US
Get:6 http://e17.dunnewind.net feisty Release.gpg [189B]
Ign http://nl.archive.ubuntu.com feisty-backports/restricted Translation-en_US
Ign http://nl.archive.ubuntu.com feisty-backports/universe Translation-en_US
Ign http://nl.archive.ubuntu.com feisty-backports/multiverse Translation-en_US
Get:7 http://security.ubuntu.com feisty-security Release.gpg [191B]
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://medibuntu.sos-sts.com feisty/non-free Translation-en_US
Hit http://medibuntu.sos-sts.com feisty Release
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Hit http://security.ubuntu.com feisty-security Release
Hit http://archive.canonical.com feisty-commercial Release
Ign http://e17.dunnewind.net feisty/e17 Translation-en_US
Hit http://nl.archive.ubuntu.com feisty Release
Hit http://nl.archive.ubuntu.com feisty-updates Release
Hit http://nl.archive.ubuntu.com feisty-backports Release
Ign http://medibuntu.sos-sts.com feisty/free Packages
Hit http://e17.dunnewind.net feisty Release
Hit http://nl.archive.ubuntu.com feisty/main Packages
Hit http://security.ubuntu.com feisty-security/main Packages
Hit http://archive.canonical.com feisty-commercial/main Packages
Hit http://nl.archive.ubuntu.com feisty/restricted Packages
Hit http://nl.archive.ubuntu.com feisty/universe Packages
Hit http://nl.archive.ubuntu.com feisty/multiverse Packages
Ign http://medibuntu.sos-sts.com feisty/non-free Packages
Ign http://medibuntu.sos-sts.com feisty/free Sources
Hit http://nl.archive.ubuntu.com feisty/main Sources
Hit http://nl.archive.ubuntu.com feisty/restricted Sources
Hit http://nl.archive.ubuntu.com feisty/universe Sources
Hit http://nl.archive.ubuntu.com feisty/multiverse Sources
Hit http://nl.archive.ubuntu.com feisty-updates/main Packages
Hit http://nl.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://nl.archive.ubuntu.com feisty-updates/main Sources
Ign http://medibuntu.sos-sts.com feisty/non-free Sources
Hit http://medibuntu.sos-sts.com feisty/free Packages
Hit http://nl.archive.ubuntu.com feisty-updates/restricted Sources
Hit http://medibuntu.sos-sts.com feisty/non-free Packages
Hit http://nl.archive.ubuntu.com feisty-backports/main Packages
Hit http://nl.archive.ubuntu.com feisty-backports/restricted Packages
Hit http://nl.archive.ubuntu.com feisty-backports/universe Packages
Hit http://nl.archive.ubuntu.com feisty-backports/multiverse Packages
Hit http://nl.archive.ubuntu.com feisty-backports/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Packages
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://nl.archive.ubuntu.com feisty-backports/restricted Sources
Hit http://e17.dunnewind.net feisty/e17 Packages
Hit http://nl.archive.ubuntu.com feisty-backports/universe Sources
Hit http://nl.archive.ubuntu.com feisty-backports/multiverse Sources
Hit http://medibuntu.sos-sts.com feisty/free Sources
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Hit http://medibuntu.sos-sts.com feisty/non-free Sources
Get:8 http://edevelop.org feisty Release.gpg [189B]
Ign http://edevelop.org feisty/e17 Translation-en_US
Hit http://edevelop.org feisty Release
Hit http://edevelop.org feisty/e17 Packages
Hit http://edevelop.org feisty/e17 Sources
Fetched 196B in 1s (114B/s)
Reading package lists... Done
marpau@marpau-desktop:~$
```

And:

```
marpau@marpau-desktop:~$ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
marpau@marpau-desktop:~$
```

Something is wrong, though:

```
marpau@marpau-desktop:~$ sudo aptitude install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are unused and will be REMOVED:
  flashplugin-nonfree gstreamer0.10-plugins-ugly-multiverse libdc1394-13 libdvdcss2 libfame-0.9 libglib1.2 libgtk1.2 libgtk1.2-common libpostproc0d libpvm3 pvm sox
  sun-java6-plugin toolame transcode-doc
The following packages will be automatically REMOVED:
  libavcodec0d mjpegtools transcode ubuntu-restricted-extras
The following packages will be DOWNGRADED:
  k3b
The following packages will be REMOVED:
  gstreamer0.10-alsa gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly liba52-0.7.4
  libaa1 libavc1394-0 libavcodec0d libcaca0 libcairomm-1.0-1 libcdaudio1 libcdio6 libcucul0 libfaad2-0 libfreebob0 libglademm-2.4-1c2a libglibmm-2.4-1c2a libgsm1
  libgtkmm-2.4-1c2a libiec61883-0 libjack0.100.0-0 libmjpegtools0c2a libmms0 libmpeg2-4 liboil0.3 libquicktime0 libshout3 libsidplay1 libsoundtouch1c2 libswfdec0.3
  libwavpack1 mjpegtools subtitleeditor transcode ubuntu-restricted-extras
0 packages upgraded, 0 newly installed, 1 downgraded, 52 to remove and 0 not upgraded.
Need to get 5030kB of archives. After unpacking 43.9MB will be freed.
Do you want to continue? [Y/n/?] 
```

What is the matter here?

---

### Post by happy-and-lost on 2007-07-22
Looks like a conflict between the Medibuntu repo packages and official Ubuntu repo packages. The only suggestion I can make is to wait a couple of days and try again.

---

### Post by Tallman on 2007-07-22
Thanks for your reply.

Being the unpatient guy that I am, I just accepted what aptitude suggested. After that I did a dist-upgrade and everything seems to be valid.

Because the ubuntu-restricted-extras packages was removed, I tried to reinstall that one and it gives me a problem with the flashplugin-nonfree.

```
Setting up flashplugin-nonfree (9.0.31.0.2ubuntu1) ...
Downloading...
--13:18:45--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 84.53.150.70
Connecting to fpdownload.macromedia.com|84.53.150.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,608,602 (2.5M) [application/x-gzip]

    0K .......... .......... .......... .......... ..........  1%  377.54 KB/s
   50K .......... .......... .......... .......... ..........  3%    1.30 MB/s
  100K .......... .......... .......... .......... ..........  5%    1.28 MB/s
  150K .......... .......... .......... .......... ..........  7%    1.70 MB/s
  200K .......... .......... .......... .......... ..........  9%    1.52 MB/s
  250K .......... .......... .......... .......... .......... 11%    1.24 MB/s
  300K .......... .......... .......... .......... .......... 13%    2.12 MB/s
  350K .......... .......... .......... .......... .......... 15%    1.52 MB/s
  400K .......... .......... .......... .......... .......... 17%    1.52 MB/s
  450K .......... .......... .......... .......... .......... 19%    1.55 MB/s
  500K .......... .......... .......... .......... .......... 21%    1.51 MB/s
  550K .......... .......... .......... .......... .......... 23%  674.54 KB/s
  600K .......... .......... .......... .......... .......... 25%   12.71 MB/s
  650K .......... .......... .......... .......... .......... 27%    1.11 MB/s
  700K .......... .......... .......... .......... .......... 29%    1.99 MB/s
  750K .......... .......... .......... .......... .......... 31%    1.52 MB/s
  800K .......... .......... .......... .......... .......... 33%    1.58 MB/s
  850K .......... .......... .......... .......... .......... 35%    1.55 MB/s
  900K .......... .......... .......... .......... .......... 37%    1.52 MB/s
  950K .......... .......... .......... .......... .......... 39%    1.54 MB/s
 1000K .......... .......... .......... .......... .......... 41%    1.55 MB/s
 1050K .......... .......... .......... .......... .......... 43%    1.49 MB/s
 1100K .......... .......... .......... .......... .......... 45%    1.63 MB/s
 1150K .......... .......... .......... .......... .......... 47%    1.51 MB/s
 1200K .......... .......... .......... .......... .......... 49%    1.34 MB/s
 1250K .......... .......... .......... .......... .......... 51%    1.82 MB/s
 1300K .......... .......... .......... .......... .......... 52%    1.54 MB/s
 1350K .......... .......... .......... .......... .......... 54%    1.55 MB/s
 1400K .......... .......... .......... .......... .......... 56%  723.71 KB/s
 1450K .......... .......... .......... .......... .......... 58%    9.48 MB/s
 1500K .......... .......... .......... .......... .......... 60%    1.22 MB/s
 1550K .......... .......... .......... .......... .......... 62%    1.65 MB/s
 1600K .......... .......... .......... .......... .......... 64%    1.53 MB/s
 1650K .......... .......... .......... .......... .......... 66%    1.53 MB/s
 1700K .......... .......... .......... .......... .......... 68%    1.55 MB/s
 1750K .......... .......... .......... .......... .......... 70%    1.55 MB/s
 1800K .......... .......... .......... .......... .......... 72%    1.55 MB/s
 1850K .......... .......... .......... .......... .......... 74%    1.55 MB/s
 1900K .......... .......... .......... .......... .......... 76%    1.50 MB/s
 1950K .......... .......... .......... .......... .......... 78%    1.57 MB/s
 2000K .......... .......... .......... .......... .......... 80%    1.52 MB/s
 2050K .......... .......... .......... .......... .......... 82%    1.58 MB/s
 2100K .......... .......... .......... .......... .......... 84%    1.34 MB/s
 2150K .......... .......... .......... .......... .......... 86%    1.77 MB/s
 2200K .......... .......... .......... .......... .......... 88%    1.55 MB/s
 2250K .......... .......... .......... .......... .......... 90%    1.55 MB/s
 2300K .......... .......... .......... .......... .......... 92%    1.54 MB/s
 2350K .......... .......... .......... .......... .......... 94%    1.52 MB/s
 2400K .......... .......... .......... .......... .......... 96%    1.53 MB/s
 2450K .......... .......... .......... .......... .......... 98%    1.52 MB/s
 2500K .......... .......... .......... .......... .......   100%    1.60 MB/s

13:18:47 (1.41 MB/s) - `./install_flash_player_9_linux.tar.gz' saved [2608602/2608602]

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.
```

I see the tarball in /var/cache/flashplugin-nonfree. Can I just try to install it from there?

---

