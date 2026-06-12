---
title: "aptitude, synaptic, package manager conflicts with HughesNet Gen4"
date: 2012-12-03
forum: General Help
---

### Post by illuminaughty50187 on 2012-12-03
Hello.
Please forgive me, i am kind of a n00b, with that said...
I cant update or install anything with my new hughesnet internet setup. I have access to 2 different ISPs at the moment. 1 being at&t dsl, and the other being hughesnet gen4 satellite. 

Ever since i got the new satellite internet I cannot use install things anymore, or update using that isp.

If i use the at&t it works fine. <and I hate at&t

Here is what terminal says when trying to install XBMC using hughesnet.

[PHP]
dycie@dycie-R580-R590:~$ sudo apt-get install xbmc
[sudo] password for dycie: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libass4 libavcodec53 libavfilter2 libavformat53 libavutil51 libcec1 libenca0
  libgsm1 libhal-storage1 libhal1 liblzo2-2 libmad0 libmicrohttpd5 libmikmod2
  libmysqlclient18 libnfs1 libpcrecpp0 libpostproc52 libqt3-mt
  libschroedinger-1.0-0 libsdl-mixer1.2 libshairport1 libswscale2
  libtinyxml2.6.2 libva-glx1 libva-x11-1 libva1 libvdpau1 libvpx1 mesa-utils
  mysql-common oss-compat python-qt3 python-sip python-support xbmc-bin
Suggested packages:
  libqt3-mt-psql libqt3-mt-mysql libqt3-mt-odbc nvidia-vdpau-driver
  vdpau-driver python-qt3-gl python-qt3-doc
The following NEW packages will be installed:
  libass4 libavcodec53 libavfilter2 libavformat53 libavutil51 libcec1 libenca0
  libgsm1 libhal-storage1 libhal1 liblzo2-2 libmad0 libmicrohttpd5 libmikmod2
  libmysqlclient18 libnfs1 libpcrecpp0 libpostproc52 libqt3-mt
  libschroedinger-1.0-0 libsdl-mixer1.2 libshairport1 libswscale2
  libtinyxml2.6.2 libva-glx1 libva-x11-1 libva1 libvdpau1 libvpx1 mesa-utils
  mysql-common oss-compat python-qt3 python-sip python-support xbmc xbmc-bin
0 upgraded, 37 newly installed, 0 to remove and 471 not upgraded.
Need to get 48.6 MB of archives.
After this operation, 103 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libgsm1 libschroedinger-1.0-0 libva1 libvpx1 libcec1 liblzo2-2 libmad0
  oss-compat libmikmod2 libnfs1 libpcrecpp0 libsdl-mixer1.2 libshairport1
  libva-x11-1 libva-glx1 libvdpau1 libenca0 libass4 libhal1 libhal-storage1
  libmicrohttpd5 libqt3-mt libtinyxml2.6.2 python-support python-sip
  python-qt3 xbmc-bin mesa-utils xbmc
Install these packages without verification [y/N]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libavutil51 i386 4:0.8.4-0ubuntu0.12.04.1 [129 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise/main libgsm1 i386 1.0.13-3 [27.6 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise/main libschroedinger-1.0-0 i386 1.0.11-1 [293 kB]
Err http://us.archive.ubuntu.com/ubuntu/ precise/main libschroedinger-1.0-0 i386 1.0.11-1
  Could not connect to us.archive.ubuntu.com:80 (91.189.91.13). - connect (111: Connection refused) [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com/ubuntu/ precise/main libva1 i386 1.0.15-4
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com/ubuntu/ precise/main libvpx1 i386 1.0.0-1
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libavcodec53 i386 4:0.8.4-0ubuntu0.12.04.1
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com/ubuntu/ precise/universe libcec1 i386 1.6.1-2
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com/ubuntu/ precise/main liblzo2-2 i386 2.06-1
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com/ubuntu/ precise/main libmad0 i386 0.15.1b-7ubuntu1
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com/ubuntu/ precise/universe oss-compat all 1
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com/ubuntu/ precise/universe libmikmod2 i386 3.1.12-2
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com/ubuntu/ precise/universe libnfs1 i386 1.2.0-3
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com/ubuntu/ precise/main libpcrecpp0 i386 8.12-4
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com/ubuntu/ precise/universe libsdl-mixer1.2 i386 1.2.11-7
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com/ubuntu/ precise/universe libshairport1 i386 1.2.1~git20120110.aeb4987-1
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com/ubuntu/ precise/main libva-x11-1 i386 1.0.15-4
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com/ubuntu/ precise/main libva-glx1 i386 1.0.15-4
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com/ubuntu/ precise/main libvdpau1 i386 0.4.1-3ubuntu1
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com/ubuntu/ precise/main libenca0 i386 1.13-4
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com/ubuntu/ precise/universe libass4 i386 0.10.0-3
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com/ubuntu/ precise/universe libhal1 i386 0.5.14-8
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com/ubuntu/ precise/universe libhal-storage1 i386 0.5.14-8
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com/ubuntu/ precise/universe libmicrohttpd5 i386 0.4.6-1
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com/ubuntu/ precise/main libqt3-mt i386 3:3.3.8-b-8ubuntu3
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com/ubuntu/ precise/universe libtinyxml2.6.2 i386 2.6.2-1build1
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com/ubuntu/ precise/universe python-support all 1.0.14ubuntu2
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com/ubuntu/ precise/main python-sip i386 4.13.2-1
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com/ubuntu/ precise/universe python-qt3 i386 3.18.1-5
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com/ubuntu/ precise/universe xbmc-bin i386 2:11.0~git20120423.cd20772-1
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com/ubuntu/ precise/universe mesa-utils i386 8.0.1+git20110129+d8f7d6b-0ubuntu2
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com/ubuntu/ precise/universe xbmc all 2:11.0~git20120423.cd20772-1
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libavcodec53 i386 4:0.8.4-0ubuntu0.12.04.1
  Could not connect to security.ubuntu.com:80 (91.189.92.190). - connect (111: Connection refused) [IP: 91.189.92.190 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libavformat53 i386 4:0.8.4-0ubuntu0.12.04.1
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.190 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libswscale2 i386 4:0.8.4-0ubuntu0.12.04.1
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.190 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libavfilter2 i386 4:0.8.4-0ubuntu0.12.04.1
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.190 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main mysql-common all 5.5.28-0ubuntu0.12.04.2
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.190 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libmysqlclient18 i386 5.5.28-0ubuntu0.12.04.2
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.190 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libpostproc52 i386 4:0.8.4-0ubuntu0.12.04.1
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.190 80]
Fetched 157 kB in 1s (87.9 kB/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/schroedinger/libschroedinger-1.0-0_1.0.11-1_i386.deb  Could not connect to us.archive.ubuntu.com:80 (91.189.91.13). - connect (111: Connection refused) [IP: 91.189.91.13 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libv/libva/libva1_1.0.15-4_i386.deb  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libv/libvpx/libvpx1_1.0.0-1_i386.deb  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/liba/libav/libavcodec53_0.8.4-0ubuntu0.12.04.1_i386.deb  Could not connect to security.ubuntu.com:80 (91.189.92.190). - connect (111: Connection refused) [IP: 91.189.92.190 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/liba/libav/libavformat53_0.8.4-0ubuntu0.12.04.1_i386.deb  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.190 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/liba/libav/libswscale2_0.8.4-0ubuntu0.12.04.1_i386.deb  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.190 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/liba/libav/libavfilter2_0.8.4-0ubuntu0.12.04.1_i386.deb  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.190 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/libc/libcec/libcec1_1.6.1-2_i386.deb  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/lzo2/liblzo2-2_2.06-1_i386.deb  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libm/libmad/libmad0_0.15.1b-7ubuntu1_i386.deb  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/o/oss-compat/oss-compat_1_all.deb  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/libm/libmikmod/libmikmod2_3.1.12-2_i386.deb  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/m/mysql-5.5/mysql-common_5.5.28-0ubuntu0.12.04.2_all.deb  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.190 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/m/mysql-5.5/libmysqlclient18_5.5.28-0ubuntu0.12.04.2_i386.deb  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.190 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/libn/libnfs/libnfs1_1.2.0-3_i386.deb  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pcre3/libpcrecpp0_8.12-4_i386.deb  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/liba/libav/libpostproc52_0.8.4-0ubuntu0.12.04.1_i386.deb  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.190 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/s/sdl-mixer1.2/libsdl-mixer1.2_1.2.11-7_i386.deb  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/libs/libshairport/libshairport1_1.2.1~git20120110.aeb4987-1_i386.deb  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libv/libva/libva-x11-1_1.0.15-4_i386.deb  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libv/libva/libva-glx1_1.0.15-4_i386.deb  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libv/libvdpau/libvdpau1_0.4.1-3ubuntu1_i386.deb  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/enca/libenca0_1.13-4_i386.deb  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/liba/libass/libass4_0.10.0-3_i386.deb  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/h/hal/libhal1_0.5.14-8_i386.deb  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/h/hal/libhal-storage1_0.5.14-8_i386.deb  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/libm/libmicrohttpd/libmicrohttpd5_0.4.6-1_i386.deb  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt-x11-free/libqt3-mt_3.3.8-b-8ubuntu3_i386.deb  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/t/tinyxml/libtinyxml2.6.2_2.6.2-1build1_i386.deb  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/p/python-support/python-support_1.0.14ubuntu2_all.deb  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/sip4/python-sip_4.13.2-1_i386.deb  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/p/python-qt3/python-qt3_3.18.1-5_i386.deb  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xbmc/xbmc-bin_11.0~git20120423.cd20772-1_i386.deb  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/m/mesa-demos/mesa-utils_8.0.1+git20110129+d8f7d6b-0ubuntu2_i386.deb  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xbmc/xbmc_11.0~git20120423.cd20772-1_all.deb  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
dycie@dycie-R580-R590:~$ 
[/PHP]Then I use at&t and XBMC installed fine. Here is what terminal says...
[PHP]dycie@dycie-R580-R590:~$ sudo apt-get install xbmc
[sudo] password for dycie: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libass4 libavcodec53 libavfilter2 libavformat53 libavutil51 libcec1 libenca0
  libgsm1 libhal-storage1 libhal1 liblzo2-2 libmad0 libmicrohttpd5 libmikmod2
  libmysqlclient18 libnfs1 libpcrecpp0 libpostproc52 libqt3-mt
  libschroedinger-1.0-0 libsdl-mixer1.2 libshairport1 libswscale2
  libtinyxml2.6.2 libva-glx1 libva-x11-1 libva1 libvdpau1 libvpx1 mesa-utils
  mysql-common oss-compat python-qt3 python-sip python-support xbmc-bin
Suggested packages:
  libqt3-mt-psql libqt3-mt-mysql libqt3-mt-odbc nvidia-vdpau-driver
  vdpau-driver python-qt3-gl python-qt3-doc
The following NEW packages will be installed:
  libass4 libavcodec53 libavfilter2 libavformat53 libavutil51 libcec1 libenca0
  libgsm1 libhal-storage1 libhal1 liblzo2-2 libmad0 libmicrohttpd5 libmikmod2
  libmysqlclient18 libnfs1 libpcrecpp0 libpostproc52 libqt3-mt
  libschroedinger-1.0-0 libsdl-mixer1.2 libshairport1 libswscale2
  libtinyxml2.6.2 libva-glx1 libva-x11-1 libva1 libvdpau1 libvpx1 mesa-utils
  mysql-common oss-compat python-qt3 python-sip python-support xbmc xbmc-bin
0 upgraded, 37 newly installed, 0 to remove and 471 not upgraded.
Need to get 48.4 MB/48.6 MB of archives.
After this operation, 103 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libgsm1 libschroedinger-1.0-0 libva1 libvpx1 libcec1 liblzo2-2 libmad0
  oss-compat libmikmod2 libnfs1 libpcrecpp0 libsdl-mixer1.2 libshairport1
  libva-x11-1 libva-glx1 libvdpau1 libenca0 libass4 libhal1 libhal-storage1
  libmicrohttpd5 libqt3-mt libtinyxml2.6.2 python-support python-sip
  python-qt3 xbmc-bin mesa-utils xbmc
Install these packages without verification [y/N]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/main libschroedinger-1.0-0 i386 1.0.11-1 [293 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise/main libva1 i386 1.0.15-4 [37.6 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise/main libvpx1 i386 1.0.0-1 [263 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libavcodec53 i386 4:0.8.4-0ubuntu0.12.04.1 [5,796 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libavformat53 i386 4:0.8.4-0ubuntu0.12.04.1 [1,032 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libswscale2 i386 4:0.8.4-0ubuntu0.12.04.1 [195 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libavfilter2 i386 4:0.8.4-0ubuntu0.12.04.1 [154 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ precise/universe libcec1 i386 1.6.1-2 [123 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ precise/main liblzo2-2 i386 2.06-1 [60.6 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ precise/main libmad0 i386 0.15.1b-7ubuntu1 [73.8 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ precise/universe oss-compat all 1 [4,498 B]
Get:12 http://us.archive.ubuntu.com/ubuntu/ precise/universe libmikmod2 i386 3.1.12-2 [150 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main mysql-common all 5.5.28-0ubuntu0.12.04.2 [13.5 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libmysqlclient18 i386 5.5.28-0ubuntu0.12.04.2 [922 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu/ precise/universe libnfs1 i386 1.2.0-3 [49.7 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu/ precise/main libpcrecpp0 i386 8.12-4 [16.6 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libpostproc52 i386 4:0.8.4-0ubuntu0.12.04.1 [116 kB]
Get:18 http://us.archive.ubuntu.com/ubuntu/ precise/universe libsdl-mixer1.2 i386 1.2.11-7 [98.9 kB]
Get:19 http://us.archive.ubuntu.com/ubuntu/ precise/universe libshairport1 i386 1.2.1~git20120110.aeb4987-1 [25.3 kB]
Get:20 http://us.archive.ubuntu.com/ubuntu/ precise/main libva-x11-1 i386 1.0.15-4 [16.3 kB]
Get:21 http://us.archive.ubuntu.com/ubuntu/ precise/main libva-glx1 i386 1.0.15-4 [10.8 kB]
Get:22 http://us.archive.ubuntu.com/ubuntu/ precise/main libvdpau1 i386 0.4.1-3ubuntu1 [26.2 kB]
Get:23 http://us.archive.ubuntu.com/ubuntu/ precise/main libenca0 i386 1.13-4 [62.2 kB]
Get:24 http://us.archive.ubuntu.com/ubuntu/ precise/universe libass4 i386 0.10.0-3 [55.5 kB]
Get:25 http://us.archive.ubuntu.com/ubuntu/ precise/universe libhal1 i386 0.5.14-8 [76.8 kB]
Get:26 http://us.archive.ubuntu.com/ubuntu/ precise/universe libhal-storage1 i386 0.5.14-8 [24.0 kB]
Get:27 http://us.archive.ubuntu.com/ubuntu/ precise/universe libmicrohttpd5 i386 0.4.6-1 [29.7 kB]
Get:28 http://us.archive.ubuntu.com/ubuntu/ precise/main libqt3-mt i386 3:3.3.8-b-8ubuntu3 [3,330 kB]
Get:29 http://us.archive.ubuntu.com/ubuntu/ precise/universe libtinyxml2.6.2 i386 2.6.2-1build1 [35.7 kB]
Get:30 http://us.archive.ubuntu.com/ubuntu/ precise/universe python-support all 1.0.14ubuntu2 [26.1 kB]
Get:31 http://us.archive.ubuntu.com/ubuntu/ precise/main python-sip i386 4.13.2-1 [71.1 kB]
Get:32 http://us.archive.ubuntu.com/ubuntu/ precise/universe python-qt3 i386 3.18.1-5 [2,321 kB]
Get:33 http://us.archive.ubuntu.com/ubuntu/ precise/universe xbmc-bin i386 2:11.0~git20120423.cd20772-1 [7,493 kB]
Get:34 http://us.archive.ubuntu.com/ubuntu/ precise/universe mesa-utils i386 8.0.1+git20110129+d8f7d6b-0ubuntu2 [27.6 kB]
Get:35 http://us.archive.ubuntu.com/ubuntu/ precise/universe xbmc all 2:11.0~git20120423.cd20772-1 [25.4 MB]
Fetched 48.4 MB in 5min 4s (159 kB/s)                                          
Extracting templates from packages: 100%
Selecting previously unselected package libavutil51.
(Reading database ... 140586 files and directories currently installed.)
Unpacking libavutil51 (from .../libavutil51_4%3a0.8.4-0ubuntu0.12.04.1_i386.deb) ...
Selecting previously unselected package libgsm1.
Unpacking libgsm1 (from .../libgsm1_1.0.13-3_i386.deb) ...
Selecting previously unselected package libschroedinger-1.0-0.
Unpacking libschroedinger-1.0-0 (from .../libschroedinger-1.0-0_1.0.11-1_i386.deb) ...
Selecting previously unselected package libva1.
Unpacking libva1 (from .../libva1_1.0.15-4_i386.deb) ...
Selecting previously unselected package libvpx1.
Unpacking libvpx1 (from .../libvpx1_1.0.0-1_i386.deb) ...
Selecting previously unselected package libavcodec53.
Unpacking libavcodec53 (from .../libavcodec53_4%3a0.8.4-0ubuntu0.12.04.1_i386.deb) ...
Selecting previously unselected package libavformat53.
Unpacking libavformat53 (from .../libavformat53_4%3a0.8.4-0ubuntu0.12.04.1_i386.deb) ...
Selecting previously unselected package libswscale2.
Unpacking libswscale2 (from .../libswscale2_4%3a0.8.4-0ubuntu0.12.04.1_i386.deb) ...
Selecting previously unselected package libavfilter2.
Unpacking libavfilter2 (from .../libavfilter2_4%3a0.8.4-0ubuntu0.12.04.1_i386.deb) ...
Selecting previously unselected package libcec1.
Unpacking libcec1 (from .../libcec1_1.6.1-2_i386.deb) ...
Selecting previously unselected package liblzo2-2.
Unpacking liblzo2-2 (from .../liblzo2-2_2.06-1_i386.deb) ...
Selecting previously unselected package libmad0.
Unpacking libmad0 (from .../libmad0_0.15.1b-7ubuntu1_i386.deb) ...
Selecting previously unselected package oss-compat.
Unpacking oss-compat (from .../archives/oss-compat_1_all.deb) ...
Selecting previously unselected package libmikmod2.
Unpacking libmikmod2 (from .../libmikmod2_3.1.12-2_i386.deb) ...
Selecting previously unselected package mysql-common.
Unpacking mysql-common (from .../mysql-common_5.5.28-0ubuntu0.12.04.2_all.deb) ...
Selecting previously unselected package libmysqlclient18.
Unpacking libmysqlclient18 (from .../libmysqlclient18_5.5.28-0ubuntu0.12.04.2_i386.deb) ...
Selecting previously unselected package libnfs1.
Unpacking libnfs1 (from .../libnfs1_1.2.0-3_i386.deb) ...
Selecting previously unselected package libpcrecpp0.
Unpacking libpcrecpp0 (from .../libpcrecpp0_8.12-4_i386.deb) ...
Selecting previously unselected package libpostproc52.
Unpacking libpostproc52 (from .../libpostproc52_4%3a0.8.4-0ubuntu0.12.04.1_i386.deb) ...
Selecting previously unselected package libsdl-mixer1.2.
Unpacking libsdl-mixer1.2 (from .../libsdl-mixer1.2_1.2.11-7_i386.deb) ...
Selecting previously unselected package libshairport1.
Unpacking libshairport1 (from .../libshairport1_1.2.1~git20120110.aeb4987-1_i386.deb) ...
Selecting previously unselected package libva-x11-1.
Unpacking libva-x11-1 (from .../libva-x11-1_1.0.15-4_i386.deb) ...
Selecting previously unselected package libva-glx1.
Unpacking libva-glx1 (from .../libva-glx1_1.0.15-4_i386.deb) ...
Selecting previously unselected package libvdpau1.
Unpacking libvdpau1 (from .../libvdpau1_0.4.1-3ubuntu1_i386.deb) ...
Selecting previously unselected package libenca0.
Unpacking libenca0 (from .../libenca0_1.13-4_i386.deb) ...
Selecting previously unselected package libass4.
Unpacking libass4 (from .../libass4_0.10.0-3_i386.deb) ...
Selecting previously unselected package libhal1.
Unpacking libhal1 (from .../libhal1_0.5.14-8_i386.deb) ...
Selecting previously unselected package libhal-storage1.
Unpacking libhal-storage1 (from .../libhal-storage1_0.5.14-8_i386.deb) ...
Selecting previously unselected package libmicrohttpd5.
Unpacking libmicrohttpd5 (from .../libmicrohttpd5_0.4.6-1_i386.deb) ...
Selecting previously unselected package libqt3-mt.
Unpacking libqt3-mt (from .../libqt3-mt_3%3a3.3.8-b-8ubuntu3_i386.deb) ...
Selecting previously unselected package libtinyxml2.6.2.
Unpacking libtinyxml2.6.2 (from .../libtinyxml2.6.2_2.6.2-1build1_i386.deb) ...
Selecting previously unselected package python-support.
Unpacking python-support (from .../python-support_1.0.14ubuntu2_all.deb) ...
Selecting previously unselected package python-sip.
Unpacking python-sip (from .../python-sip_4.13.2-1_i386.deb) ...
Selecting previously unselected package python-qt3.
Unpacking python-qt3 (from .../python-qt3_3.18.1-5_i386.deb) ...
Selecting previously unselected package xbmc-bin.
Unpacking xbmc-bin (from .../xbmc-bin_2%3a11.0~git20120423.cd20772-1_i386.deb) ...
Selecting previously unselected package mesa-utils.
Unpacking mesa-utils (from .../mesa-utils_8.0.1+git20110129+d8f7d6b-0ubuntu2_i386.deb) ...
Selecting previously unselected package xbmc.
Unpacking xbmc (from .../xbmc_2%3a11.0~git20120423.cd20772-1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Setting up libavutil51 (4:0.8.4-0ubuntu0.12.04.1) ...
Setting up libgsm1 (1.0.13-3) ...
Setting up libschroedinger-1.0-0 (1.0.11-1) ...
Setting up libva1 (1.0.15-4) ...
Setting up libvpx1 (1.0.0-1) ...
Setting up libavcodec53 (4:0.8.4-0ubuntu0.12.04.1) ...
Setting up libavformat53 (4:0.8.4-0ubuntu0.12.04.1) ...
Setting up libswscale2 (4:0.8.4-0ubuntu0.12.04.1) ...
Setting up libavfilter2 (4:0.8.4-0ubuntu0.12.04.1) ...
Setting up libcec1 (1.6.1-2) ...
Setting up liblzo2-2 (2.06-1) ...
Setting up libmad0 (0.15.1b-7ubuntu1) ...
Setting up oss-compat (1) ...
Setting up libmikmod2 (3.1.12-2) ...
Setting up mysql-common (5.5.28-0ubuntu0.12.04.2) ...
Setting up libmysqlclient18 (5.5.28-0ubuntu0.12.04.2) ...
Setting up libnfs1 (1.2.0-3) ...
Setting up libpcrecpp0 (8.12-4) ...
Setting up libpostproc52 (4:0.8.4-0ubuntu0.12.04.1) ...
Setting up libsdl-mixer1.2 (1.2.11-7) ...
Setting up libshairport1 (1.2.1~git20120110.aeb4987-1) ...
Setting up libva-x11-1 (1.0.15-4) ...
Setting up libva-glx1 (1.0.15-4) ...
Setting up libvdpau1 (0.4.1-3ubuntu1) ...
Setting up libenca0 (1.13-4) ...
Setting up libass4 (0.10.0-3) ...
Setting up libhal1 (0.5.14-8) ...
Setting up libhal-storage1 (0.5.14-8) ...
Setting up libmicrohttpd5 (0.4.6-1) ...
Setting up libqt3-mt (3:3.3.8-b-8ubuntu3) ...
Setting up libtinyxml2.6.2 (2.6.2-1build1) ...
Setting up python-support (1.0.14ubuntu2) ...
Setting up python-sip (4.13.2-1) ...
Setting up python-qt3 (3.18.1-5) ...
Setting up xbmc-bin (2:11.0~git20120423.cd20772-1) ...
Setting up mesa-utils (8.0.1+git20110129+d8f7d6b-0ubuntu2) ...
Setting up xbmc (2:11.0~git20120423.cd20772-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
dycie@dycie-R580-R590:~$ 
[/PHP]... About what I expected. All software does this. 

And if I use a GUI method (ubuntu software center), i get this...
[IMG]http://s10.postimage.org/tio719113/Screenshot_from_2012_12_03_12_37_48.png[/IMG]

Even Transmission runs like garbage now. Its almost never downloading at ANY rate/speed.

Can someone point me in the right direction. This is ridiculous.
-Thanks

---

### Post by Cheesehead on 2012-12-03
Error 111 is often a server issue. Are you able to duplicate the problem reliably?

> **illuminaughty50187 said:**
> 
  Could not connect to us.archive.ubuntu.com:80 (91.189.91.13). - connect (111: Connection refused) [IP: 91.189.91.13 80]

---

### Post by illuminaughty50187 on 2012-12-03
Well it is happening with any software i have to update or install (using the hughesnet gen4). 
And within 5 minutes I would try using another ISP to download the same software and it works just fine. So it doesn't seem to be a server issue.  I have 3 computers in this house (2 laptops, and 1 very nice gaming rig) and they ALL share the same difficulty when updating or installing software when using the HN gen4 ISP.

Is there specific ports that synaptic or aptitude uses that are blocked maybe? I couldn't imagine that being the case though.

-thanks for the quick help btw

---

### Post by Cheesehead on 2012-12-03
So you seem to have an ISP problem, not a Package Manager or software install problem.

Try pinging archive.ubuntu.com both ways. See if there is a big difference.
Try tracerouting. See if you be blocked on the way.
Try finding another mirror -there are lots of them- that doesn't suffer from the condition.

---

### Post by illuminaughty50187 on 2012-12-03
Right, package manager is not to blame, more of a conflict in my ISP with package manager or something. I'll try your suggestions and let you know...

---

### Post by illuminaughty50187 on 2012-12-03
i pinged with
In terminal "ping -c 10 archive.ubuntu.com"
results...
--- archive.ubuntu.com ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9014ms
rtt min/avg/max/mdev = 709.216/819.569/1121.272/140.082 ms, pipe 2


I installed traceroute then...
In terminal "traceroute archive.ubuntu.com"
Here is what I got...
[PHP]
traceroute to archive.ubuntu.com (91.189.92.177), 30 hops max, 60 byte packets
 1  Cisco70323 (192.168.1.2)  1.125 ms  1.107 ms  1.702 ms
 2  100.64.200.81 (100.64.200.81)  3.745 ms  3.741 ms  3.733 ms
 3  dpc6935168002.direcpc.com (69.35.168.2)  610.598 ms  610.612 ms  610.606 ms
 4  dpc6935172017.direcpc.com (69.35.172.17)  1318.805 ms  1318.816 ms  1318.810 ms
 5  Denver7604-te1-5.pnpt.com (69.2.15.61)  1318.802 ms  1318.793 ms  1318.786 ms
 6  xe-3-3-0.den11.ip4.tinet.net (173.241.130.57)  1318.776 ms  1423.043 ms  1432.975 ms
 7  xe-11-3-2.dal33.ip4.tinet.net (141.136.111.105)  659.240 ms xe-11-2-2.dal33.ip4.tinet.net (141.136.111.101)  759.203 ms  809.015 ms
 8  as3356.ip4.tinet.net (77.67.71.222)  899.107 ms  973.499 ms  1063.432 ms
 9  vlan80.csw3.Dallas1.Level3.net (4.69.145.190)  1065.489 ms vlan90.csw4.Dallas1.Level3.net (4.69.145.254)  1065.447 ms vlan80.csw3.Dallas1.Level3.net (4.69.145.190)  1065.475 ms
10  ae-63-63.ebr3.Dallas1.Level3.net (4.69.151.134)  1065.443 ms ae-83-83.ebr3.Dallas1.Level3.net (4.69.151.158)  1065.449 ms ae-72-72.ebr2.Dallas1.Level3.net (4.69.151.142)  1073.609 ms
11  ae-7-7.ebr3.Atlanta2.Level3.net (4.69.134.22)  1084.097 ms  1084.105 ms ae-3-3.ebr2.NewYork1.Level3.net (4.69.137.122)  1095.511 ms
12  ae-72-72.csw2.NewYork1.Level3.net (4.69.148.38)  1087.046 ms ae-63-63.ebr1.Atlanta2.Level3.net (4.69.148.242)  678.216 ms ae-62-62.csw1.NewYork1.Level3.net (4.69.148.34)  688.574 ms
13  ae-91-91.ebr1.NewYork1.Level3.net (4.69.134.77)  670.178 ms ae-6-6.ebr1.Washington12.Level3.net (4.69.148.106)  678.760 ms  660.031 ms
14  ae-1-100.ebr2.Washington12.Level3.net (4.69.143.214)  710.745 ms ae-41-41.ebr2.London1.Level3.net (4.69.137.65)  716.736 ms ae-1-100.ebr2.Washington12.Level3.net (4.69.143.214)  716.684 ms
15  4.69.148.49 (4.69.148.49)  716.688 ms  757.799 ms ae-57-222.csw2.London1.Level3.net (4.69.153.134)  836.125 ms
16  ae-2-52.edge5.London1.Level3.net (4.69.139.107)  762.434 ms ae-43-43.ebr2.London1.Level3.net (4.69.137.73)  777.648 ms ae-42-42.ebr2.London1.Level3.net (4.69.137.69)  831.241 ms
17  ae-56-221.csw2.London1.Level3.net (4.69.153.130)  841.343 ms SOURCE-MANA.edge5.London1.Level3.net (212.187.138.82)  931.216 ms ae-59-224.csw2.London1.Level3.net (4.69.153.142)  941.452 ms
[/PHP]

How do I find another mirror, then how do i use that other mirror?

Once again thanks for the help!

---

### Post by steeldriver on 2012-12-03
Hmm... I wonder if latency is the problem with the Hughes link?

Both synaptic and Software Center allow you to test for the 'best' mirror iirc

Software Sources --> Download from --> Other... Select Best Server

---

### Post by illuminaughty50187 on 2012-12-03
ALRIGHT!
@steeldriver, That last thing worked :)   Tested that solution on all 3 PCs. And thanks to you sir, all computers are up to date.
Thanks to both of you, and thanks to this nice responsive community.

-Ben

---

