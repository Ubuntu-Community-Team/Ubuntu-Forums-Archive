---
title: "After successful dual Windows/Ubuntu UEFI-- Cannot apt-get install"
date: 2018-05-29
forum: General Help
---

### Post by mrwednezday on 2018-05-29
After successful dual Windows/Ubuntu UEFI-- Cannot apt-get install

For example:

```
Sudo apt-get install gparted


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  reiser4progs gpart
The following NEW packages will be installed:
  gparted
0 upgraded, 1 newly installed, 0 to remove and 9 not upgraded.
1 not fully installed or removed.
Need to get 462 kB of archives.
After this operation, 2,138 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main amd64 gparted amd64 0.30.0-3ubuntu1 [462 kB]
Fetched 462 kB in 1s (576 kB/s)  
Selecting previously unselected package gparted.
(Reading database ... 183890 files and directories currently installed.)
Preparing to unpack .../gparted_0.30.0-3ubuntu1_amd64.deb ...
Unpacking gparted (0.30.0-3ubuntu1) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu3) ...
Setting up grub-efi-amd64-signed (1.93+2.02-2ubuntu8) ...
Installing for x86_64-efi platform.
Could not prepare Boot variable: No space left on device
grub-install: error: efibootmgr failed to register the boot entry: Input/output error.
dpkg: error processing package grub-efi-amd64-signed (--configure):
 installed grub-efi-amd64-signed package post-installation script subprocess returned error exit status 1
Processing triggers for man-db (2.8.3-2) ...
Processing triggers for gnome-menus (3.13.3-11ubuntu1) ...
Setting up gparted (0.30.0-3ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Errors were encountered while processing:
 grub-efi-amd64-signed
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Also, I tried installing Gparted with Ubuntu Software

It said it was already installed so I removed it and installed it again

and this is what happens when i go on terminal and type

 sudo gparted

Unit -.mount does not exist, proceeding anyway.
/usr/sbin/gpartedbin: error while loading shared libraries: libgtkmm-2.4.so.1: cannot open shared object file: No such file or directory

---

### Post by wildmanne39 on 2018-05-29
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by bijayalaxmi1808 on 2018-05-29
I can see the following error from the above log that you have provided:

```
Installing for x86_64-efi platform.
Could not prepare Boot variable: No space left on device
grub-install: error: efibootmgr failed to register the boot entry: Input/output error.
```

I suspect some of the partition is full and cannot be written anymore and that's where the apt command is trying write something.

Can you post the output of the following command:
```
df -h
```

---

### Post by mrwednezday on 2018-05-29
```
Filesystem      Size  Used Avail Use% Mounted onudev            5.9G     0  5.9G   0% /dev
tmpfs           1.2G  1.8M  1.2G   1% /run
/dev/sda1        14G  5.2G  7.9G  40% /
tmpfs           5.9G  4.1M  5.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           5.9G     0  5.9G   0% /sys/fs/cgroup
/dev/loop0       22M   22M     0 100% /snap/gnome-logs/31
/dev/loop1       87M   87M     0 100% /snap/core/4486
/dev/loop3       21M   21M     0 100% /snap/gnome-logs/25
/dev/loop4      3.8M  3.8M     0 100% /snap/gnome-system-monitor/39
/dev/loop5      3.4M  3.4M     0 100% /snap/gnome-system-monitor/36
/dev/loop6      140M  140M     0 100% /snap/gnome-3-26-1604/64
/dev/loop7       13M   13M     0 100% /snap/gnome-characters/86
/dev/loop8       87M   87M     0 100% /snap/core/4650
/dev/loop9      141M  141M     0 100% /snap/gnome-3-26-1604/59
/dev/loop2      1.7M  1.7M     0 100% /snap/gnome-calculator/154
/dev/loop10      13M   13M     0 100% /snap/gnome-characters/69
/dev/loop11     2.4M  2.4M     0 100% /snap/gnome-calculator/167
/dev/sda4       6.9G  5.8M  6.9G   1% /boot/efi
/dev/sda3       183G  4.6G  169G   3% /home
tmpfs           1.2G   28K  1.2G   1% /run/user/1000



```

---

### Post by bijayalaxmi1808 on 2018-05-30
I see the root file system has enough space left.
I don't know what's really happening and why it detects as you don't have any space left.

All the /dev/loop* looks strange to me. I don't know what's that.
Probably someone can help us to interpret the error that shows up.

Going back to your second comment where you have the following:
```
/usr/sbin/gpartedbin: error while loading shared libraries:  libgtkmm-2.4.so.1: cannot open shared object file: No such file or  directory
```

It looks like gparted is looking for the libgtkmm-2.4.so.1 shared library which is not present.

Can you install the libgtkmm-2.4 using below command:
```
sudo apt install libgtkmm-2.4
```

It is possible that you may be stuck for some other library even after installing this. Try to install the relevant dependent library and proceed.

---

### Post by mrwednezday on 2018-05-30
@[[COLOR=#000000]bijayalaxmi1808[/COLOR]]("https://ubuntuforums.org/member.php?u=2098260")[COLOR=#000000]  Thank You for your response. Basically, trying to install Ubuntu in UEFI causes a lot of stress. The Ubuntu 18.04 x64  installation is stressful as it fails to install Grub2.
I had to go to windows to shut off Fast Startup. 

[/COLOR]https://bugs.launchpad.net/ubuntu/+source/gtkmm2.4/+bug/1753120[COLOR=#000000]

```
 s[/COLOR]udo apt install libgtkmm-2.4[sudo] password for ------: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libgtkmm-2.4-1v5' for regex 'libgtkmm-2.4'
Note, selecting 'libgtkmm-2.4-1c2a' for regex 'libgtkmm-2.4'
Note, selecting 'libgtkmm-2.4-dev' for regex 'libgtkmm-2.4'
Note, selecting 'libgtkmm-2.4-doc' for regex 'libgtkmm-2.4'
libgtkmm-2.4-1v5 is already the newest version (1:2.24.5-2).
The following additional packages will be installed:
  autoconf automake autopoint autotools-dev debhelper dh-autoreconf
  dh-strip-nondeterminism doc-base gir1.2-gtk-2.0 gir1.2-harfbuzz-0.0
  gtkmm-documentation icu-devtools libarchive-cpio-perl libatk1.0-dev
  libatkmm-1.6-dev libcairo-script-interpreter2 libcairo2-dev
  libcairomm-1.0-dev libexpat1-dev libfile-stripnondeterminism-perl
  libfontconfig1-dev libfreetype6-dev libgdk-pixbuf2.0-dev libglib2.0-dev
  libglib2.0-dev-bin libglibmm-2.4-dev libglibmm-2.4-doc libgraphite2-dev
  libgtk2.0-dev libgtkmm-3.0-doc libharfbuzz-dev libharfbuzz-gobject0
  libice-dev libicu-dev libicu-le-hb-dev libicu-le-hb0 libiculx60 libltdl-dev
  libmail-sendmail-perl libpango1.0-dev libpangomm-1.4-dev libpcre16-3
  libpcre3-dev libpcre32-3 libpcrecpp0v5 libpixman-1-dev libpng-dev
  libpng-tools libpthread-stubs0-dev libsigc++-2.0-dev libsm-dev
  libsys-hostname-long-perl libtool libuuid-perl libx11-dev libx11-doc
  libxau-dev libxcb-render0-dev libxcb-shm0-dev libxcb1-dev libxcomposite-dev
  libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev
  libxft-dev libxi-dev libxinerama-dev libxml2-utils libxrandr-dev
  libxrender-dev libyaml-tiny-perl m4 pkg-config po-debconf python3-distutils
  python3-lib2to3 x11proto-composite-dev x11proto-core-dev x11proto-damage-dev
  x11proto-dev x11proto-fixes-dev x11proto-input-dev x11proto-randr-dev
  x11proto-xext-dev x11proto-xinerama-dev xorg-sgml-doctools xtrans-dev
  zlib1g-dev
Suggested packages:
  autoconf-archive gnu-standards autoconf-doc dh-make dwz rarian-compat
  libatkmm-1.6-doc libcairo2-doc libcairomm-1.0-doc libglib2.0-doc
  libgtkmm-3.0-dev libgraphite2-utils libgtk2.0-doc libice-doc icu-doc
  libtool-doc libpango1.0-doc libsigc++-2.0-doc libsm-doc gfortran
  | fortran95-compiler gcj-jdk libxcb-doc libxext-doc m4-doc libmail-box-perl
The following NEW packages will be installed:
  autoconf automake autopoint autotools-dev debhelper dh-autoreconf
  dh-strip-nondeterminism doc-base gir1.2-gtk-2.0 gir1.2-harfbuzz-0.0
  gtkmm-documentation icu-devtools libarchive-cpio-perl libatk1.0-dev
  libatkmm-1.6-dev libcairo-script-interpreter2 libcairo2-dev
  libcairomm-1.0-dev libexpat1-dev libfile-stripnondeterminism-perl
  libfontconfig1-dev libfreetype6-dev libgdk-pixbuf2.0-dev libglib2.0-dev
  libglib2.0-dev-bin libglibmm-2.4-dev libglibmm-2.4-doc libgraphite2-dev
  libgtk2.0-dev libgtkmm-2.4-dev libgtkmm-2.4-doc libgtkmm-3.0-doc
  libharfbuzz-dev libharfbuzz-gobject0 libice-dev libicu-dev libicu-le-hb-dev
  libicu-le-hb0 libiculx60 libltdl-dev libmail-sendmail-perl libpango1.0-dev
  libpangomm-1.4-dev libpcre16-3 libpcre3-dev libpcre32-3 libpcrecpp0v5
  libpixman-1-dev libpng-dev libpng-tools libpthread-stubs0-dev
  libsigc++-2.0-dev libsm-dev libsys-hostname-long-perl libtool libuuid-perl
  libx11-dev libx11-doc libxau-dev libxcb-render0-dev libxcb-shm0-dev
  libxcb1-dev libxcomposite-dev libxcursor-dev libxdamage-dev libxdmcp-dev
  libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxml2-utils
  libxrandr-dev libxrender-dev libyaml-tiny-perl m4 pkg-config po-debconf
  python3-distutils python3-lib2to3 x11proto-composite-dev x11proto-core-dev
  x11proto-damage-dev x11proto-dev x11proto-fixes-dev x11proto-input-dev
  x11proto-randr-dev x11proto-xext-dev x11proto-xinerama-dev
  xorg-sgml-doctools xtrans-dev zlib1g-dev
0 upgraded, 92 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 54.1 MB of archives.
After this operation, 478 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 m4 amd64 1.4.18-1 [197 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 autoconf all 2.69-11 [322 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 autotools-dev all 20180224.1 [39.6 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 automake all 1:1.15.1-3ubuntu2 [509 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 autopoint all 0.19.8.1-6 [412 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libtool all 2.4.6-2 [194 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 dh-autoreconf all 17 [15.8 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libfile-stripnondeterminism-perl all 0.040-1.1~build1 [13.8 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 dh-strip-nondeterminism all 0.040-1.1~build1 [5,208 B]
Get:10 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 po-debconf all 1.0.20 [232 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 debhelper all 11.1.6ubuntu2 [902 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libuuid-perl amd64 0.27-1build1 [15.7 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libyaml-tiny-perl all 1.70-1 [25.1 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 doc-base all 0.10.8 [80.3 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 gir1.2-gtk-2.0 amd64 2.24.32-1ubuntu1 [172 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 gir1.2-harfbuzz-0.0 amd64 1.7.2-1ubuntu1 [18.6 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libgtkmm-3.0-doc all 3.22.2-2 [10.7 MB]
Get:18 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 gtkmm-documentation all 3.22.0-2 [1,204 kB]
Get:19 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 icu-devtools amd64 60.2-3ubuntu3 [179 kB]
Get:20 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libarchive-cpio-perl all 0.10-1 [9,644 B]
Get:21 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 pkg-config amd64 0.29.1-0ubuntu2 [45.0 kB]
Get:22 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 python3-lib2to3 all 3.6.5-3 [76.6 kB]
Get:23 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 python3-distutils all 3.6.5-3 [141 kB]
Get:24 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libglib2.0-dev-bin amd64 2.56.1-2ubuntu1 [102 kB]
Get:25 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libpcre16-3 amd64 2:8.39-9 [147 kB]
Get:26 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libpcre32-3 amd64 2:8.39-9 [138 kB]
Get:27 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libpcrecpp0v5 amd64 2:8.39-9 [15.3 kB]
Get:28 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libpcre3-dev amd64 2:8.39-9 [537 kB]
Get:29 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 zlib1g-dev amd64 1:1.2.11.dfsg-0ubuntu2 [176 kB]
Get:30 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libglib2.0-dev amd64 2.56.1-2ubuntu1 [1,382 kB]
Get:31 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libatk1.0-dev amd64 2.28.1-1 [79.9 kB]
Get:32 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libsigc++-2.0-dev amd64 2.10.0-2 [63.7 kB]
Get:33 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libglibmm-2.4-dev amd64 2.56.0-1 [429 kB]
Get:34 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libatkmm-1.6-dev amd64 2.24.2-3 [33.0 kB]
Get:35 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libcairo-script-interpreter2 amd64 1.15.10-2 [53.4 kB]
Get:36 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libexpat1-dev amd64 2.2.5-3 [122 kB]
Get:37 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libpng-dev amd64 1.6.34-1 [177 kB]
Get:38 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libfreetype6-dev amd64 2.8.1-2ubuntu2 [2,539 kB]
Get:39 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libfontconfig1-dev amd64 2.12.6-0ubuntu2 [689 kB]
Get:40 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 xorg-sgml-doctools all 1:1.11-1 [12.9 kB]
Get:41 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 x11proto-dev all 2018.4-4 [251 kB]
Get:42 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 x11proto-core-dev all 2018.4-4 [2,620 B]
Get:43 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libxau-dev amd64 1:1.0.8-1 [11.1 kB]
Get:44 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libxdmcp-dev amd64 1:1.1.2-3 [25.1 kB]
Get:45 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 x11proto-input-dev all 2018.4-4 [2,620 B]
Get:46 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 xtrans-dev all 1.3.5-1 [70.5 kB]
Get:47 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libpthread-stubs0-dev amd64 0.3-4 [4,068 B]
Get:48 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libxcb1-dev amd64 1.13-1 [80.0 kB]
Get:49 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libx11-dev amd64 2:1.6.4-3 [642 kB]
Get:50 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libxrender-dev amd64 1:0.9.10-1 [24.9 kB]
Get:51 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 x11proto-xext-dev all 2018.4-4 [2,620 B]
Get:52 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libxext-dev amd64 2:1.3.3-1 [82.1 kB]
Get:53 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libice-dev amd64 2:1.0.9-2 [46.8 kB]
Get:54 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libsm-dev amd64 2:1.2.2-1 [16.2 kB]
Get:55 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libpixman-1-dev amd64 0.34.0-2 [244 kB]
Get:56 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libxcb-render0-dev amd64 1.13-1 [18.4 kB]
Get:57 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libxcb-shm0-dev amd64 1.13-1 [6,676 B]
Get:58 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libcairo2-dev amd64 1.15.10-2 [626 kB]
Get:59 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libcairomm-1.0-dev amd64 1.12.2-3 [525 kB]
Get:60 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libgdk-pixbuf2.0-dev amd64 2.36.11-2 [46.8 kB]
Get:61 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libglibmm-2.4-doc all 2.56.0-1 [5,168 kB]
Get:62 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libgraphite2-dev amd64 1.3.11-2 [14.5 kB]
Get:63 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libharfbuzz-gobject0 amd64 1.7.2-1ubuntu1 [13.4 kB]
Get:64 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libicu-le-hb0 amd64 1.0.3+git161113-4 [14.3 kB]
Get:65 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libiculx60 amd64 60.2-3ubuntu3 [18.9 kB]
Get:66 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libicu-le-hb-dev amd64 1.0.3+git161113-4 [29.5 kB]
Get:67 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libicu-dev amd64 60.2-3ubuntu3 [8,893 kB]
Get:68 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libharfbuzz-dev amd64 1.7.2-1ubuntu1 [302 kB]
Get:69 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libxft-dev amd64 2.3.2-1 [45.7 kB]
Get:70 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libpango1.0-dev amd64 1.40.14-1 [288 kB]
Get:71 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 x11proto-xinerama-dev all 2018.4-4 [2,628 B]
Get:72 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libxinerama-dev amd64 2:1.1.3-1 [8,404 B]
Get:73 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 x11proto-fixes-dev all 1:2018.4-4 [2,620 B]
Get:74 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libxfixes-dev amd64 1:5.0.3-1 [11.0 kB]
Get:75 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libxi-dev amd64 2:1.7.9-1 [186 kB]
Get:76 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 x11proto-randr-dev all 2018.4-4 [2,620 B]
Get:77 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libxrandr-dev amd64 2:1.5.1-1 [24.0 kB]
Get:78 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libxcursor-dev amd64 1:1.1.15-1 [26.5 kB]
Get:79 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 x11proto-composite-dev all 1:2018.4-4 [2,620 B]
Get:80 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libxcomposite-dev amd64 1:0.4.4-2 [9,136 B]
Get:81 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 x11proto-damage-dev all 1:2018.4-4 [2,620 B]
Get:82 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libxdamage-dev amd64 1:1.1.4-3 [5,028 B]
Get:83 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libxml2-utils amd64 2.9.4+dfsg1-6.1ubuntu1 [35.8 kB]
Get:84 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libgtk2.0-dev amd64 2.24.32-1ubuntu1 [2,652 kB]
Get:85 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libpangomm-1.4-dev amd64 2.40.1-4 [49.1 kB]
Get:86 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libgtkmm-2.4-dev amd64 1:2.24.5-2 [493 kB]
Get:87 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libgtkmm-2.4-doc all 1:2.24.5-2 [8,630 kB]
Get:88 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libltdl-dev amd64 2.4.6-2 [162 kB]
Get:89 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libsys-hostname-long-perl all 1.5-1 [11.7 kB]
Get:90 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libmail-sendmail-perl all 0.80-1 [22.6 kB]
Get:91 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libpng-tools amd64 1.6.34-1 [25.5 kB]
Get:92 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libx11-doc all 2:1.6.4-3 [2,067 kB]
Fetched 54.1 MB in 7s (7,919 kB/s)                                             
Extracting templates from packages: 100%
Selecting previously unselected package m4.
(Reading database ... 184360 files and directories currently installed.)
Preparing to unpack .../00-m4_1.4.18-1_amd64.deb ...
Unpacking m4 (1.4.18-1) ...
Selecting previously unselected package autoconf.
Preparing to unpack .../01-autoconf_2.69-11_all.deb ...
Unpacking autoconf (2.69-11) ...
Selecting previously unselected package autotools-dev.
Preparing to unpack .../02-autotools-dev_20180224.1_all.deb ...
Unpacking autotools-dev (20180224.1) ...
Selecting previously unselected package automake.
Preparing to unpack .../03-automake_1%3a1.15.1-3ubuntu2_all.deb ...
Unpacking automake (1:1.15.1-3ubuntu2) ...
Selecting previously unselected package autopoint.
Preparing to unpack .../04-autopoint_0.19.8.1-6_all.deb ...
Unpacking autopoint (0.19.8.1-6) ...
Selecting previously unselected package libtool.
Preparing to unpack .../05-libtool_2.4.6-2_all.deb ...
Unpacking libtool (2.4.6-2) ...
Selecting previously unselected package dh-autoreconf.
Preparing to unpack .../06-dh-autoreconf_17_all.deb ...
Unpacking dh-autoreconf (17) ...
Selecting previously unselected package libfile-stripnondeterminism-perl.
Preparing to unpack .../07-libfile-stripnondeterminism-perl_0.040-1.1~build1_all.deb ...
Unpacking libfile-stripnondeterminism-perl (0.040-1.1~build1) ...
Selecting previously unselected package dh-strip-nondeterminism.
Preparing to unpack .../08-dh-strip-nondeterminism_0.040-1.1~build1_all.deb ...
Unpacking dh-strip-nondeterminism (0.040-1.1~build1) ...
Selecting previously unselected package po-debconf.
Preparing to unpack .../09-po-debconf_1.0.20_all.deb ...
Unpacking po-debconf (1.0.20) ...
Selecting previously unselected package debhelper.
Preparing to unpack .../10-debhelper_11.1.6ubuntu2_all.deb ...
Unpacking debhelper (11.1.6ubuntu2) ...
Selecting previously unselected package libuuid-perl.
Preparing to unpack .../11-libuuid-perl_0.27-1build1_amd64.deb ...
Unpacking libuuid-perl (0.27-1build1) ...
Selecting previously unselected package libyaml-tiny-perl.
Preparing to unpack .../12-libyaml-tiny-perl_1.70-1_all.deb ...
Unpacking libyaml-tiny-perl (1.70-1) ...
Selecting previously unselected package doc-base.
Preparing to unpack .../13-doc-base_0.10.8_all.deb ...
Unpacking doc-base (0.10.8) ...
Selecting previously unselected package gir1.2-gtk-2.0.
Preparing to unpack .../14-gir1.2-gtk-2.0_2.24.32-1ubuntu1_amd64.deb ...
Unpacking gir1.2-gtk-2.0 (2.24.32-1ubuntu1) ...
Selecting previously unselected package gir1.2-harfbuzz-0.0:amd64.
Preparing to unpack .../15-gir1.2-harfbuzz-0.0_1.7.2-1ubuntu1_amd64.deb ...
Unpacking gir1.2-harfbuzz-0.0:amd64 (1.7.2-1ubuntu1) ...
Selecting previously unselected package libgtkmm-3.0-doc.
Preparing to unpack .../16-libgtkmm-3.0-doc_3.22.2-2_all.deb ...
Unpacking libgtkmm-3.0-doc (3.22.2-2) ...
Selecting previously unselected package gtkmm-documentation.
Preparing to unpack .../17-gtkmm-documentation_3.22.0-2_all.deb ...
Unpacking gtkmm-documentation (3.22.0-2) ...
Selecting previously unselected package icu-devtools.
Preparing to unpack .../18-icu-devtools_60.2-3ubuntu3_amd64.deb ...
Unpacking icu-devtools (60.2-3ubuntu3) ...
Selecting previously unselected package libarchive-cpio-perl.
Preparing to unpack .../19-libarchive-cpio-perl_0.10-1_all.deb ...
Unpacking libarchive-cpio-perl (0.10-1) ...
Selecting previously unselected package pkg-config.
Preparing to unpack .../20-pkg-config_0.29.1-0ubuntu2_amd64.deb ...
Unpacking pkg-config (0.29.1-0ubuntu2) ...
Selecting previously unselected package python3-lib2to3.
Preparing to unpack .../21-python3-lib2to3_3.6.5-3_all.deb ...
Unpacking python3-lib2to3 (3.6.5-3) ...
Selecting previously unselected package python3-distutils.
Preparing to unpack .../22-python3-distutils_3.6.5-3_all.deb ...
Unpacking python3-distutils (3.6.5-3) ...
Selecting previously unselected package libglib2.0-dev-bin.
Preparing to unpack .../23-libglib2.0-dev-bin_2.56.1-2ubuntu1_amd64.deb ...
Unpacking libglib2.0-dev-bin (2.56.1-2ubuntu1) ...
Selecting previously unselected package libpcre16-3:amd64.
Preparing to unpack .../24-libpcre16-3_2%3a8.39-9_amd64.deb ...
Unpacking libpcre16-3:amd64 (2:8.39-9) ...
Selecting previously unselected package libpcre32-3:amd64.
Preparing to unpack .../25-libpcre32-3_2%3a8.39-9_amd64.deb ...
Unpacking libpcre32-3:amd64 (2:8.39-9) ...
Selecting previously unselected package libpcrecpp0v5:amd64.
Preparing to unpack .../26-libpcrecpp0v5_2%3a8.39-9_amd64.deb ...
Unpacking libpcrecpp0v5:amd64 (2:8.39-9) ...
Selecting previously unselected package libpcre3-dev:amd64.
Preparing to unpack .../27-libpcre3-dev_2%3a8.39-9_amd64.deb ...
Unpacking libpcre3-dev:amd64 (2:8.39-9) ...
Selecting previously unselected package zlib1g-dev:amd64.
Preparing to unpack .../28-zlib1g-dev_1%3a1.2.11.dfsg-0ubuntu2_amd64.deb ...
Unpacking zlib1g-dev:amd64 (1:1.2.11.dfsg-0ubuntu2) ...
Selecting previously unselected package libglib2.0-dev:amd64.
Preparing to unpack .../29-libglib2.0-dev_2.56.1-2ubuntu1_amd64.deb ...
Unpacking libglib2.0-dev:amd64 (2.56.1-2ubuntu1) ...
Selecting previously unselected package libatk1.0-dev:amd64.
Preparing to unpack .../30-libatk1.0-dev_2.28.1-1_amd64.deb ...
Unpacking libatk1.0-dev:amd64 (2.28.1-1) ...
Selecting previously unselected package libsigc++-2.0-dev:amd64.
Preparing to unpack .../31-libsigc++-2.0-dev_2.10.0-2_amd64.deb ...
Unpacking libsigc++-2.0-dev:amd64 (2.10.0-2) ...
Selecting previously unselected package libglibmm-2.4-dev:amd64.
Preparing to unpack .../32-libglibmm-2.4-dev_2.56.0-1_amd64.deb ...
Unpacking libglibmm-2.4-dev:amd64 (2.56.0-1) ...
Selecting previously unselected package libatkmm-1.6-dev:amd64.
Preparing to unpack .../33-libatkmm-1.6-dev_2.24.2-3_amd64.deb ...
Unpacking libatkmm-1.6-dev:amd64 (2.24.2-3) ...
Selecting previously unselected package libcairo-script-interpreter2:amd64.
Preparing to unpack .../34-libcairo-script-interpreter2_1.15.10-2_amd64.deb ...
Unpacking libcairo-script-interpreter2:amd64 (1.15.10-2) ...
Selecting previously unselected package libexpat1-dev:amd64.
Preparing to unpack .../35-libexpat1-dev_2.2.5-3_amd64.deb ...
Unpacking libexpat1-dev:amd64 (2.2.5-3) ...
Selecting previously unselected package libpng-dev:amd64.
Preparing to unpack .../36-libpng-dev_1.6.34-1_amd64.deb ...
Unpacking libpng-dev:amd64 (1.6.34-1) ...
Selecting previously unselected package libfreetype6-dev:amd64.
Preparing to unpack .../37-libfreetype6-dev_2.8.1-2ubuntu2_amd64.deb ...
Unpacking libfreetype6-dev:amd64 (2.8.1-2ubuntu2) ...
Selecting previously unselected package libfontconfig1-dev:amd64.
Preparing to unpack .../38-libfontconfig1-dev_2.12.6-0ubuntu2_amd64.deb ...
Unpacking libfontconfig1-dev:amd64 (2.12.6-0ubuntu2) ...
Selecting previously unselected package xorg-sgml-doctools.
Preparing to unpack .../39-xorg-sgml-doctools_1%3a1.11-1_all.deb ...
Unpacking xorg-sgml-doctools (1:1.11-1) ...
Selecting previously unselected package x11proto-dev.
Preparing to unpack .../40-x11proto-dev_2018.4-4_all.deb ...
Unpacking x11proto-dev (2018.4-4) ...
Selecting previously unselected package x11proto-core-dev.
Preparing to unpack .../41-x11proto-core-dev_2018.4-4_all.deb ...
Unpacking x11proto-core-dev (2018.4-4) ...
Selecting previously unselected package libxau-dev:amd64.
Preparing to unpack .../42-libxau-dev_1%3a1.0.8-1_amd64.deb ...
Unpacking libxau-dev:amd64 (1:1.0.8-1) ...
Selecting previously unselected package libxdmcp-dev:amd64.
Preparing to unpack .../43-libxdmcp-dev_1%3a1.1.2-3_amd64.deb ...
Unpacking libxdmcp-dev:amd64 (1:1.1.2-3) ...
Selecting previously unselected package x11proto-input-dev.
Preparing to unpack .../44-x11proto-input-dev_2018.4-4_all.deb ...
Unpacking x11proto-input-dev (2018.4-4) ...
Selecting previously unselected package xtrans-dev.
Preparing to unpack .../45-xtrans-dev_1.3.5-1_all.deb ...
Unpacking xtrans-dev (1.3.5-1) ...
Selecting previously unselected package libpthread-stubs0-dev:amd64.
Preparing to unpack .../46-libpthread-stubs0-dev_0.3-4_amd64.deb ...
Unpacking libpthread-stubs0-dev:amd64 (0.3-4) ...
Selecting previously unselected package libxcb1-dev:amd64.
Preparing to unpack .../47-libxcb1-dev_1.13-1_amd64.deb ...
Unpacking libxcb1-dev:amd64 (1.13-1) ...
Selecting previously unselected package libx11-dev:amd64.
Preparing to unpack .../48-libx11-dev_2%3a1.6.4-3_amd64.deb ...
Unpacking libx11-dev:amd64 (2:1.6.4-3) ...
Selecting previously unselected package libxrender-dev:amd64.
Preparing to unpack .../49-libxrender-dev_1%3a0.9.10-1_amd64.deb ...
Unpacking libxrender-dev:amd64 (1:0.9.10-1) ...
Selecting previously unselected package x11proto-xext-dev.
Preparing to unpack .../50-x11proto-xext-dev_2018.4-4_all.deb ...
Unpacking x11proto-xext-dev (2018.4-4) ...
Selecting previously unselected package libxext-dev:amd64.
Preparing to unpack .../51-libxext-dev_2%3a1.3.3-1_amd64.deb ...
Unpacking libxext-dev:amd64 (2:1.3.3-1) ...
Selecting previously unselected package libice-dev:amd64.
Preparing to unpack .../52-libice-dev_2%3a1.0.9-2_amd64.deb ...
Unpacking libice-dev:amd64 (2:1.0.9-2) ...
Selecting previously unselected package libsm-dev:amd64.
Preparing to unpack .../53-libsm-dev_2%3a1.2.2-1_amd64.deb ...
Unpacking libsm-dev:amd64 (2:1.2.2-1) ...
Selecting previously unselected package libpixman-1-dev:amd64.
Preparing to unpack .../54-libpixman-1-dev_0.34.0-2_amd64.deb ...
Unpacking libpixman-1-dev:amd64 (0.34.0-2) ...
Selecting previously unselected package libxcb-render0-dev:amd64.
Preparing to unpack .../55-libxcb-render0-dev_1.13-1_amd64.deb ...
Unpacking libxcb-render0-dev:amd64 (1.13-1) ...
Selecting previously unselected package libxcb-shm0-dev:amd64.
Preparing to unpack .../56-libxcb-shm0-dev_1.13-1_amd64.deb ...
Unpacking libxcb-shm0-dev:amd64 (1.13-1) ...
Selecting previously unselected package libcairo2-dev:amd64.
Preparing to unpack .../57-libcairo2-dev_1.15.10-2_amd64.deb ...
Unpacking libcairo2-dev:amd64 (1.15.10-2) ...
Selecting previously unselected package libcairomm-1.0-dev:amd64.
Preparing to unpack .../58-libcairomm-1.0-dev_1.12.2-3_amd64.deb ...
Unpacking libcairomm-1.0-dev:amd64 (1.12.2-3) ...
Selecting previously unselected package libgdk-pixbuf2.0-dev.
Preparing to unpack .../59-libgdk-pixbuf2.0-dev_2.36.11-2_amd64.deb ...
Unpacking libgdk-pixbuf2.0-dev (2.36.11-2) ...
Selecting previously unselected package libglibmm-2.4-doc.
Preparing to unpack .../60-libglibmm-2.4-doc_2.56.0-1_all.deb ...
Unpacking libglibmm-2.4-doc (2.56.0-1) ...
Selecting previously unselected package libgraphite2-dev:amd64.
Preparing to unpack .../61-libgraphite2-dev_1.3.11-2_amd64.deb ...
Unpacking libgraphite2-dev:amd64 (1.3.11-2) ...
Selecting previously unselected package libharfbuzz-gobject0:amd64.
Preparing to unpack .../62-libharfbuzz-gobject0_1.7.2-1ubuntu1_amd64.deb ...
Unpacking libharfbuzz-gobject0:amd64 (1.7.2-1ubuntu1) ...
Selecting previously unselected package libicu-le-hb0:amd64.
Preparing to unpack .../63-libicu-le-hb0_1.0.3+git161113-4_amd64.deb ...
Unpacking libicu-le-hb0:amd64 (1.0.3+git161113-4) ...
Selecting previously unselected package libiculx60:amd64.
Preparing to unpack .../64-libiculx60_60.2-3ubuntu3_amd64.deb ...
Unpacking libiculx60:amd64 (60.2-3ubuntu3) ...
Selecting previously unselected package libicu-le-hb-dev:amd64.
Preparing to unpack .../65-libicu-le-hb-dev_1.0.3+git161113-4_amd64.deb ...
Unpacking libicu-le-hb-dev:amd64 (1.0.3+git161113-4) ...
Selecting previously unselected package libicu-dev.
Preparing to unpack .../66-libicu-dev_60.2-3ubuntu3_amd64.deb ...
Unpacking libicu-dev (60.2-3ubuntu3) ...
Selecting previously unselected package libharfbuzz-dev:amd64.
Preparing to unpack .../67-libharfbuzz-dev_1.7.2-1ubuntu1_amd64.deb ...
Unpacking libharfbuzz-dev:amd64 (1.7.2-1ubuntu1) ...
Selecting previously unselected package libxft-dev.
Preparing to unpack .../68-libxft-dev_2.3.2-1_amd64.deb ...
Unpacking libxft-dev (2.3.2-1) ...
Selecting previously unselected package libpango1.0-dev.
Preparing to unpack .../69-libpango1.0-dev_1.40.14-1_amd64.deb ...
Unpacking libpango1.0-dev (1.40.14-1) ...
Selecting previously unselected package x11proto-xinerama-dev.
Preparing to unpack .../70-x11proto-xinerama-dev_2018.4-4_all.deb ...
Unpacking x11proto-xinerama-dev (2018.4-4) ...
Selecting previously unselected package libxinerama-dev:amd64.
Preparing to unpack .../71-libxinerama-dev_2%3a1.1.3-1_amd64.deb ...
Unpacking libxinerama-dev:amd64 (2:1.1.3-1) ...
Selecting previously unselected package x11proto-fixes-dev.
Preparing to unpack .../72-x11proto-fixes-dev_1%3a2018.4-4_all.deb ...
Unpacking x11proto-fixes-dev (1:2018.4-4) ...
Selecting previously unselected package libxfixes-dev:amd64.
Preparing to unpack .../73-libxfixes-dev_1%3a5.0.3-1_amd64.deb ...
Unpacking libxfixes-dev:amd64 (1:5.0.3-1) ...
Selecting previously unselected package libxi-dev:amd64.
Preparing to unpack .../74-libxi-dev_2%3a1.7.9-1_amd64.deb ...
Unpacking libxi-dev:amd64 (2:1.7.9-1) ...
Selecting previously unselected package x11proto-randr-dev.
Preparing to unpack .../75-x11proto-randr-dev_2018.4-4_all.deb ...
Unpacking x11proto-randr-dev (2018.4-4) ...
Selecting previously unselected package libxrandr-dev:amd64.
Preparing to unpack .../76-libxrandr-dev_2%3a1.5.1-1_amd64.deb ...
Unpacking libxrandr-dev:amd64 (2:1.5.1-1) ...
Selecting previously unselected package libxcursor-dev:amd64.
Preparing to unpack .../77-libxcursor-dev_1%3a1.1.15-1_amd64.deb ...
Unpacking libxcursor-dev:amd64 (1:1.1.15-1) ...
Selecting previously unselected package x11proto-composite-dev.
Preparing to unpack .../78-x11proto-composite-dev_1%3a2018.4-4_all.deb ...
Unpacking x11proto-composite-dev (1:2018.4-4) ...
Selecting previously unselected package libxcomposite-dev:amd64.
Preparing to unpack .../79-libxcomposite-dev_1%3a0.4.4-2_amd64.deb ...
Unpacking libxcomposite-dev:amd64 (1:0.4.4-2) ...
Selecting previously unselected package x11proto-damage-dev.
Preparing to unpack .../80-x11proto-damage-dev_1%3a2018.4-4_all.deb ...
Unpacking x11proto-damage-dev (1:2018.4-4) ...
Selecting previously unselected package libxdamage-dev:amd64.
Preparing to unpack .../81-libxdamage-dev_1%3a1.1.4-3_amd64.deb ...
Unpacking libxdamage-dev:amd64 (1:1.1.4-3) ...
Selecting previously unselected package libxml2-utils.
Preparing to unpack .../82-libxml2-utils_2.9.4+dfsg1-6.1ubuntu1_amd64.deb ...
Unpacking libxml2-utils (2.9.4+dfsg1-6.1ubuntu1) ...
Selecting previously unselected package libgtk2.0-dev.
Preparing to unpack .../83-libgtk2.0-dev_2.24.32-1ubuntu1_amd64.deb ...
Unpacking libgtk2.0-dev (2.24.32-1ubuntu1) ...
Selecting previously unselected package libpangomm-1.4-dev:amd64.
Preparing to unpack .../84-libpangomm-1.4-dev_2.40.1-4_amd64.deb ...
Unpacking libpangomm-1.4-dev:amd64 (2.40.1-4) ...
Selecting previously unselected package libgtkmm-2.4-dev:amd64.
Preparing to unpack .../85-libgtkmm-2.4-dev_1%3a2.24.5-2_amd64.deb ...
Unpacking libgtkmm-2.4-dev:amd64 (1:2.24.5-2) ...
Selecting previously unselected package libgtkmm-2.4-doc.
Preparing to unpack .../86-libgtkmm-2.4-doc_1%3a2.24.5-2_all.deb ...
Unpacking libgtkmm-2.4-doc (1:2.24.5-2) ...
dpkg: error processing archive /tmp/apt-dpkg-install-ZlZ1mp/86-libgtkmm-2.4-doc_1%3a2.24.5-2_all.deb (--unpack):
 trying to overwrite '/usr/share/doc/libgtkmm-2.4-dev/examples/README', which is also in package libgtkmm-2.4-dev:amd64 1:2.24.5-2
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Selecting previously unselected package libltdl-dev:amd64.
Preparing to unpack .../87-libltdl-dev_2.4.6-2_amd64.deb ...
Unpacking libltdl-dev:amd64 (2.4.6-2) ...
Selecting previously unselected package libsys-hostname-long-perl.
Preparing to unpack .../88-libsys-hostname-long-perl_1.5-1_all.deb ...
Unpacking libsys-hostname-long-perl (1.5-1) ...
Selecting previously unselected package libmail-sendmail-perl.
Preparing to unpack .../89-libmail-sendmail-perl_0.80-1_all.deb ...
Unpacking libmail-sendmail-perl (0.80-1) ...
Selecting previously unselected package libpng-tools.
Preparing to unpack .../90-libpng-tools_1.6.34-1_amd64.deb ...
Unpacking libpng-tools (1.6.34-1) ...
Selecting previously unselected package libx11-doc.
Preparing to unpack .../91-libx11-doc_2%3a1.6.4-3_all.deb ...
Unpacking libx11-doc (2:1.6.4-3) ...
Errors were encountered while processing:
 /tmp/apt-dpkg-install-ZlZ1mp/86-libgtkmm-2.4-doc_1%3a2.24.5-2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Also here is my fdisk -l output

```
 Disk /dev/loop0: 139.5 MiB, 146276352 bytes, 285696 sectorsUnits: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop1: 21.6 MiB, 22609920 bytes, 44160 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop2: 12.2 MiB, 12804096 bytes, 25008 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop3: 21 MiB, 22003712 bytes, 42976 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop4: 2.3 MiB, 2428928 bytes, 4744 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop5: 13 MiB, 13594624 bytes, 26552 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop6: 86.6 MiB, 90759168 bytes, 177264 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop7: 3.3 MiB, 3411968 bytes, 6664 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 98CF5243-37F2-4442-B1D0-A6017F656BE5


Device         Start        End    Sectors   Size Type
/dev/sda1    9764864   39061503   29296640    14G Linux filesystem
/dev/sda2   39061504   78123007   39061504  18.6G Linux swap
/dev/sda3   78123008  468748287  390625280 186.3G Linux filesystem
/dev/sda4  468748288  483084287   14336000   6.9G EFI System
/dev/sda5  483084288 1953521663 1470437376 701.2G Microsoft basic data








Disk /dev/sdb: 223.6 GiB, 240057409536 bytes, 468862128 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 94D1404F-DA05-4C5B-8461-D9E5370221B2


Device       Start       End   Sectors  Size Type
/dev/sdb1     2048   1023999   1021952  499M Windows recovery environment
/dev/sdb2  1024000   1228799    204800  100M EFI System
/dev/sdb3  1228800   1261567     32768   16M Microsoft reserved
/dev/sdb4  1261568 468860927 467599360  223G Microsoft basic data




Disk /dev/loop8: 140 MiB, 146841600 bytes, 286800 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop9: 86.6 MiB, 90812416 bytes, 177368 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop10: 1.6 MiB, 1691648 bytes, 3304 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop11: 3.7 MiB, 3813376 bytes, 7448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop12: 14.5 MiB, 15196160 bytes, 29680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop13: 13 MiB, 13619200 bytes, 26600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop14: 2.3 MiB, 2428928 bytes, 4744 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop15: 3.7 MiB, 3813376 bytes, 7448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```

---

