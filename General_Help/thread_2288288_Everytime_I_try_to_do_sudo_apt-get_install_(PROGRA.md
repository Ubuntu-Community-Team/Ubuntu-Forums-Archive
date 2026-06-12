---
title: "Everytime I try to do sudo apt-get install (PROGRAM NAME) I get this message"
date: 2015-07-25
forum: General Help
---

### Post by rafael_vicuna on 2015-07-25
Even If I do sudo apt-get update, this will happen as well, same with ANYTHING I install, like lets say sudo apt-get install sl or sudo apt-get install any other programs, i get this message. Today I tried to install gqrx

```
rafael@rafael-Latitude-E6230:~$ sudo apt-get install gqrx
[sudo] password for rafael: 
rafael@rafael-Latitude-E6230:~$ gqrx
The program 'gqrx' is currently not installed. You can install it by typing:
sudo apt-get install gqrx-sdr
rafael@rafael-Latitude-E6230:~$ sudo apt-get install gqrx-sdr
[sudo] password for rafael: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.19.0-22 linux-headers-3.19.0-22-generic
  linux-image-3.19.0-22-generic linux-image-extra-3.19.0-22-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  blt fonts-lyx freeglut3 gnuradio gr-fcdproplus gr-iqbal gr-osmosdr
  libairspy0 libbladerf0 libboost-serialization1.55.0 libboost-test1.55.0
  libcomedi0 libdrm-dev libexpat1-dev libgl1-mesa-dev libglu1-mesa-dev
  libgnuradio-analog3.7.5 libgnuradio-atsc3.7.5 libgnuradio-audio3.7.5
  libgnuradio-blocks3.7.5 libgnuradio-channels3.7.5 libgnuradio-comedi3.7.5
  libgnuradio-digital3.7.5 libgnuradio-dtv3.7.5 libgnuradio-fcd3.7.5
  libgnuradio-fcdproplus0 libgnuradio-fec3.7.5 libgnuradio-fft3.7.5
  libgnuradio-filter3.7.5 libgnuradio-iqbalance0 libgnuradio-noaa3.7.5
  libgnuradio-osmosdr0.1.3 libgnuradio-pager3.7.5 libgnuradio-pmt3.7.5
  libgnuradio-qtgui3.7.5 libgnuradio-runtime3.7.5 libgnuradio-trellis3.7.5
  libgnuradio-uhd3.7.5 libgnuradio-video-sdl3.7.5 libgnuradio-vocoder3.7.5
  libgnuradio-wavelet3.7.5 libgnuradio-wxgui3.7.5 libgnuradio-zeromq3.7.5
  libgsl0ldbl libhackrf0 liblog4cpp5 libmirisdr0 libosmosdr0 libpgm-5.1-0
  libpython-dev libpython2.7-dev libqt4-dev libqt4-dev-bin libqt4-opengl-dev
  libqtwebkit-dev libqwt-dev libqwt5-qt4 libqwt6 librtlsdr0 libsodium13
  libuhd003 libvolk-bin libvolk0.0.0 libx11-xcb-dev libxcb-dri2-0-dev
  libxcb-dri3-dev libxcb-glx0-dev libxcb-present-dev libxcb-randr0-dev
  libxcb-render0-dev libxcb-shape0-dev libxcb-sync-dev libxcb-xfixes0-dev
  libxdamage-dev libxext-dev libxfixes-dev libxshmfence-dev libxxf86vm-dev
  libzmq3 mesa-common-dev python-cheetah python-dateutil python-decorator
  python-dev python-matplotlib python-matplotlib-data python-mock
  python-networkx python-nose python-numpy python-opengl python-pyparsing
  python-qwt5-qt4 python-scipy python-tk python-tz python-zmq python2.7-dev
  qt4-linguist-tools qt4-qmake qthid-fcd-controller tk8.6-blt2.5 uhd-host
  x11proto-damage-dev x11proto-dri2-dev x11proto-fixes-dev x11proto-gl-dev
  x11proto-xext-dev x11proto-xf86vidmode-dev
Suggested packages:
  blt-demo gsl-ref-psdoc gsl-doc-pdf gsl-doc-info gsl-ref-html firebird-dev
  libmysqlclient-dev libsqlite0-dev qt4-dev-tools qt4-doc unixodbc-dev
  libxext-doc python-markdown python-pygments python-memcache dvipng inkscape
  ipython python-cairocffi python-configobj python-excelerator
  python-matplotlib-doc python-tornado python-traits texlive-extra-utils
  texlive-latex-extra ttf-staypuft python-mock-doc python-pydot python-yaml
  python-coverage python-nose-doc gfortran python-numpy-dbg python-numpy-doc
  libgle3 python-scipy-doc tix python-tk-dbg
Recommended packages:
  gr-fcd
The following NEW packages will be installed:
  blt fonts-lyx freeglut3 gnuradio gqrx-sdr gr-fcdproplus gr-iqbal gr-osmosdr
  libairspy0 libbladerf0 libboost-serialization1.55.0 libboost-test1.55.0
  libcomedi0 libdrm-dev libexpat1-dev libgl1-mesa-dev libglu1-mesa-dev
  libgnuradio-analog3.7.5 libgnuradio-atsc3.7.5 libgnuradio-audio3.7.5
  libgnuradio-blocks3.7.5 libgnuradio-channels3.7.5 libgnuradio-comedi3.7.5
  libgnuradio-digital3.7.5 libgnuradio-dtv3.7.5 libgnuradio-fcd3.7.5
  libgnuradio-fcdproplus0 libgnuradio-fec3.7.5 libgnuradio-fft3.7.5
  libgnuradio-filter3.7.5 libgnuradio-iqbalance0 libgnuradio-noaa3.7.5
  libgnuradio-osmosdr0.1.3 libgnuradio-pager3.7.5 libgnuradio-pmt3.7.5
  libgnuradio-qtgui3.7.5 libgnuradio-runtime3.7.5 libgnuradio-trellis3.7.5
  libgnuradio-uhd3.7.5 libgnuradio-video-sdl3.7.5 libgnuradio-vocoder3.7.5
  libgnuradio-wavelet3.7.5 libgnuradio-wxgui3.7.5 libgnuradio-zeromq3.7.5
  libgsl0ldbl libhackrf0 liblog4cpp5 libmirisdr0 libosmosdr0 libpgm-5.1-0
  libpython-dev libpython2.7-dev libqt4-dev libqt4-dev-bin libqt4-opengl-dev
  libqtwebkit-dev libqwt-dev libqwt5-qt4 libqwt6 librtlsdr0 libsodium13
  libuhd003 libvolk-bin libvolk0.0.0 libx11-xcb-dev libxcb-dri2-0-dev
  libxcb-dri3-dev libxcb-glx0-dev libxcb-present-dev libxcb-randr0-dev
  libxcb-render0-dev libxcb-shape0-dev libxcb-sync-dev libxcb-xfixes0-dev
  libxdamage-dev libxext-dev libxfixes-dev libxshmfence-dev libxxf86vm-dev
  libzmq3 mesa-common-dev python-cheetah python-dateutil python-decorator
  python-dev python-matplotlib python-matplotlib-data python-mock
  python-networkx python-nose python-numpy python-opengl python-pyparsing
  python-qwt5-qt4 python-scipy python-tk python-tz python-zmq python2.7-dev
  qt4-linguist-tools qt4-qmake qthid-fcd-controller tk8.6-blt2.5 uhd-host
  x11proto-damage-dev x11proto-dri2-dev x11proto-fixes-dev x11proto-gl-dev
  x11proto-xext-dev x11proto-xf86vidmode-dev
0 to upgrade, 110 to newly install, 0 to remove and 0 not to upgrade.
Need to get 59.3 MB/60.1 MB of archives.
After this operation, 260 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
WARNING: The following packages cannot be authenticated!
  freeglut3 libairspy0 libbladerf0 libgnuradio-pmt3.7.5 liblog4cpp5
  libvolk0.0.0 libgnuradio-runtime3.7.5 libgnuradio-blocks3.7.5
  libgnuradio-audio3.7.5 libgnuradio-fcd3.7.5 libgnuradio-fcdproplus0
  libgnuradio-iqbalance0 libboost-serialization1.55.0 libuhd003
  libgnuradio-uhd3.7.5 libhackrf0 libmirisdr0 libosmosdr0 librtlsdr0
  libgnuradio-osmosdr0.1.3 gr-osmosdr libboost-test1.55.0 libgnuradio-fft3.7.5
  libgnuradio-analog3.7.5 libgnuradio-fec3.7.5 libgnuradio-filter3.7.5
  libgnuradio-atsc3.7.5 libgnuradio-channels3.7.5 libgsl0ldbl libcomedi0
  libgnuradio-comedi3.7.5 libgnuradio-digital3.7.5 libgnuradio-dtv3.7.5
  libgnuradio-noaa3.7.5 libgnuradio-pager3.7.5 libqwt5-qt4
  libgnuradio-qtgui3.7.5 libgnuradio-trellis3.7.5 libgnuradio-video-sdl3.7.5
  libgnuradio-vocoder3.7.5 libgnuradio-wavelet3.7.5 libgnuradio-wxgui3.7.5
  libpgm-5.1-0 libsodium13 libgnuradio-zeromq3.7.5 libexpat1-dev
  libpython2.7-dev libqwt6 libvolk-bin gr-iqbal tk8.6-blt2.5 blt fonts-lyx
  python-opengl python-cheetah gnuradio gqrx-sdr gr-fcdproplus libdrm-dev
  mesa-common-dev libx11-xcb-dev libxcb-dri3-dev libxcb-render0-dev
  libxcb-randr0-dev libxcb-shape0-dev libxcb-xfixes0-dev libxcb-sync-dev
  libxcb-present-dev libxshmfence-dev libxcb-dri2-0-dev libxcb-glx0-dev
  x11proto-xext-dev x11proto-fixes-dev libxfixes-dev x11proto-damage-dev
  libxdamage-dev libxext-dev x11proto-xf86vidmode-dev libxxf86vm-dev
  x11proto-dri2-dev x11proto-gl-dev libgl1-mesa-dev libglu1-mesa-dev
  libpython-dev libqtwebkit-dev libqwt-dev python-dateutil python-decorator
  python2.7-dev python-dev python-matplotlib-data python-pyparsing python-tz
  python-numpy python-mock python-nose python-matplotlib python-networkx
  python-qwt5-qt4 python-tk python-zmq qthid-fcd-controller uhd-host
  python-scipy
Install these packages without verification? [y/N] y
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main freeglut3 amd64 2.8.1-2
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libairspy0 amd64 0.2.22.b4c38a7-1
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libbladerf0 amd64 0.2014.09~rc2-5
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libgnuradio-pmt3.7.5 amd64 3.7.5-5
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe liblog4cpp5 amd64 1.0-4
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libvolk0.0.0 amd64 3.7.5-5
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libgnuradio-runtime3.7.5 amd64 3.7.5-5
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libgnuradio-blocks3.7.5 amd64 3.7.5-5
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libgnuradio-audio3.7.5 amd64 3.7.5-5
  503  Service unavailable [IP: 202.158.214.106 80]
Get:1 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) vivid-security/universe libzmq3 amd64 4.0.5+dfsg-2+deb8u1build0.15.04.1 [140 kB]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libgnuradio-fcd3.7.5 amd64 3.7.5-5
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libgnuradio-fcdproplus0 amd64 3.7.11-3
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libgnuradio-iqbalance0 amd64 0.37.2-1
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main libboost-serialization1.55.0 amd64 1.55.0+dfsg-3ubuntu2
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libuhd003 amd64 3.7.3-1
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libgnuradio-uhd3.7.5 amd64 3.7.5-5
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libhackrf0 amd64 2014.08.1-1
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libmirisdr0 amd64 0.0.4.59ba37-2
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libosmosdr0 amd64 0.1.8.effcaa7-1
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe librtlsdr0 amd64 0.5.3-3
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libgnuradio-osmosdr0.1.3 amd64 0.1.3-2
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe gr-osmosdr amd64 0.1.3-2
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main libboost-test1.55.0 amd64 1.55.0+dfsg-3ubuntu2
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libgnuradio-fft3.7.5 amd64 3.7.5-5
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libgnuradio-analog3.7.5 amd64 3.7.5-5
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libgnuradio-fec3.7.5 amd64 3.7.5-5
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libgnuradio-filter3.7.5 amd64 3.7.5-5
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libgnuradio-atsc3.7.5 amd64 3.7.5-5
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libgnuradio-channels3.7.5 amd64 3.7.5-5
  503  Service unavailable [IP: 202.158.214.106 80]
Get:2 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) vivid-security/main libqt4-dev-bin amd64 4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1 [1,631 kB]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main libgsl0ldbl amd64 1.16+dfsg-2build1
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libcomedi0 amd64 0.10.2-2
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libgnuradio-comedi3.7.5 amd64 3.7.5-5
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libgnuradio-digital3.7.5 amd64 3.7.5-5
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libgnuradio-dtv3.7.5 amd64 3.7.5-5
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libgnuradio-noaa3.7.5 amd64 3.7.5-5
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libgnuradio-pager3.7.5 amd64 3.7.5-5
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libqwt5-qt4 amd64 5.2.3-1
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libgnuradio-qtgui3.7.5 amd64 3.7.5-5
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libgnuradio-trellis3.7.5 amd64 3.7.5-5
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libgnuradio-video-sdl3.7.5 amd64 3.7.5-5
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libgnuradio-vocoder3.7.5 amd64 3.7.5-5
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libgnuradio-wavelet3.7.5 amd64 3.7.5-5
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libgnuradio-wxgui3.7.5 amd64 3.7.5-5
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libpgm-5.1-0 amd64 5.1.118-1~dfsg-2ubuntu1
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libsodium13 amd64 1.0.1-1
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libgnuradio-zeromq3.7.5 amd64 3.7.5-5
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main libexpat1-dev amd64 2.1.0-6ubuntu1
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main libpython2.7-dev amd64 2.7.9-2ubuntu3
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libqwt6 amd64 6.1.1-0ubuntu1
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libvolk-bin amd64 3.7.5-5
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe gr-iqbal amd64 0.37.2-1
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe python-opengl all 3.0.2-1
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main python-cheetah amd64 2.4.4-3.fakesyncbuild1
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe gnuradio amd64 3.7.5-5
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe gqrx-sdr amd64 2.3.1-2build1
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe gr-fcdproplus amd64 3.7.11-3
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main libdrm-dev amd64 2.4.60-2
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main mesa-common-dev amd64 10.5.2-0ubuntu1
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main libx11-xcb-dev amd64 2:1.6.2-2ubuntu2
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main libxcb-dri3-dev amd64 1.10-2ubuntu1
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main libxcb-render0-dev amd64 1.10-2ubuntu1
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main libxcb-randr0-dev amd64 1.10-2ubuntu1
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main libxcb-shape0-dev amd64 1.10-2ubuntu1
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main libxcb-xfixes0-dev amd64 1.10-2ubuntu1
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main libxcb-sync-dev amd64 1.10-2ubuntu1
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main libxcb-present-dev amd64 1.10-2ubuntu1
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main libxshmfence-dev amd64 1.1-4
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main libxcb-dri2-0-dev amd64 1.10-2ubuntu1
  503  Service unavailable [IP: 202.158.214.106 80]
Get:3 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) vivid-security/main qt4-linguist-tools amd64 4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1 [841 kB]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main libxcb-glx0-dev amd64 1.10-2ubuntu1
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main x11proto-xext-dev all 7.3.0-1
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main x11proto-fixes-dev all 1:5.0-2ubuntu2
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main libxfixes-dev amd64 1:5.0.1-2
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main x11proto-damage-dev all 1:1.2.1-2
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main libxdamage-dev amd64 1:1.1.4-2
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main libxext-dev amd64 2:1.3.3-1
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main x11proto-xf86vidmode-dev all 2.3.1-2
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main libxxf86vm-dev amd64 1:1.1.3-1                                                             
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main x11proto-dri2-dev all 2.8-2                                                                
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main x11proto-gl-dev all 1.4.17-1                                                               
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main libgl1-mesa-dev amd64 10.5.2-0ubuntu1                                                      
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main libglu1-mesa-dev amd64 9.0.0-2                                                             
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main libpython-dev amd64 2.7.9-1                                                                
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main libqtwebkit-dev amd64 2.3.2-0ubuntu7                                                       
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe libqwt-dev amd64 6.1.1-0ubuntu1                                                        
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main python-dateutil all 2.2-2                                                                  
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main python-decorator all 3.4.0-2build1                                                         
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main python2.7-dev amd64 2.7.9-2ubuntu3                                                         
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main python-dev amd64 2.7.9-1                                                                   
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe python-matplotlib-data all 1.4.2-3.1                                                   
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main python-pyparsing all 2.0.3+dfsg1-1                                                         
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main python-tz all 2014.10~dfsg1-0ubuntu1                                                       
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main python-numpy amd64 1:1.8.2-1ubuntu1                                                        
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main python-mock all 1.0.1-3                                                                    
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main python-nose all 1.3.4-2                                                                    
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe python-matplotlib amd64 1.4.2-3.1                                                      
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main python-networkx all 1.8.1-0ubuntu3                                                         
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe python-qwt5-qt4 amd64 5.2.1~cvs20091107+dfsg-7build1                                   
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/main python-tk amd64 2.7.9-1                                                                    
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe python-zmq amd64 14.4.1-0ubuntu3                                                       
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe qthid-fcd-controller amd64 4.1-3                                                       
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe uhd-host amd64 3.7.3-1                                                                 
  503  Service unavailable [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) vivid/universe python-scipy amd64 0.14.1-1ubuntu1                                                     
  503  Service unavailable [IP: 202.158.214.106 80]
Get:4 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) vivid-security/main qt4-qmake amd64 4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1 [1,267 kB]                
Get:5 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) vivid-security/main libqt4-dev amd64 4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1 [897 kB]                 
Get:6 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) vivid-security/main libqt4-opengl-dev amd64 4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1 [22.9 kB]         
Fetched 4,800 kB in 14s (334 kB/s)                                                                                                             
E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/f/freeglut/freeglut3_2.8.1-2_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/f/freeglut/freeglut3_2.8.1-2_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/a/airspy-host/libairspy0_0.2.22.b4c38a7-1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/a/airspy-host/libairspy0_0.2.22.b4c38a7-1_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/b/bladerf/libbladerf0_0.2014.09~rc2-5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/b/bladerf/libbladerf0_0.2014.09~rc2-5_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-pmt3.7.5_3.7.5-5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-pmt3.7.5_3.7.5-5_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/l/log4cpp/liblog4cpp5_1.0-4_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/l/log4cpp/liblog4cpp5_1.0-4_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libvolk0.0.0_3.7.5-5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libvolk0.0.0_3.7.5-5_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-runtime3.7.5_3.7.5-5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-runtime3.7.5_3.7.5-5_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-blocks3.7.5_3.7.5-5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-blocks3.7.5_3.7.5-5_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-audio3.7.5_3.7.5-5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-audio3.7.5_3.7.5-5_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-fcd3.7.5_3.7.5-5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-fcd3.7.5_3.7.5-5_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gr-fcdproplus/libgnuradio-fcdproplus0_3.7.11-3_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gr-fcdproplus/libgnuradio-fcdproplus0_3.7.11-3_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gr-iqbal/libgnuradio-iqbalance0_0.37.2-1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gr-iqbal/libgnuradio-iqbalance0_0.37.2-1_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/b/boost1.55/libboost-serialization1.55.0_1.55.0+dfsg-3ubuntu2_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/b/boost1.55/libboost-serialization1.55.0_1.55.0+dfsg-3ubuntu2_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/u/uhd/libuhd003_3.7.3-1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/u/uhd/libuhd003_3.7.3-1_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-uhd3.7.5_3.7.5-5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-uhd3.7.5_3.7.5-5_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/h/hackrf/libhackrf0_2014.08.1-1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/h/hackrf/libhackrf0_2014.08.1-1_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/libm/libmirisdr/libmirisdr0_0.0.4.59ba37-2_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/libm/libmirisdr/libmirisdr0_0.0.4.59ba37-2_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/libo/libosmosdr/libosmosdr0_0.1.8.effcaa7-1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/libo/libosmosdr/libosmosdr0_0.1.8.effcaa7-1_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/r/rtl-sdr/librtlsdr0_0.5.3-3_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/r/rtl-sdr/librtlsdr0_0.5.3-3_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gr-osmosdr/libgnuradio-osmosdr0.1.3_0.1.3-2_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gr-osmosdr/libgnuradio-osmosdr0.1.3_0.1.3-2_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gr-osmosdr/gr-osmosdr_0.1.3-2_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gr-osmosdr/gr-osmosdr_0.1.3-2_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/b/boost1.55/libboost-test1.55.0_1.55.0+dfsg-3ubuntu2_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/b/boost1.55/libboost-test1.55.0_1.55.0+dfsg-3ubuntu2_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-fft3.7.5_3.7.5-5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-fft3.7.5_3.7.5-5_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-analog3.7.5_3.7.5-5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-analog3.7.5_3.7.5-5_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-fec3.7.5_3.7.5-5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-fec3.7.5_3.7.5-5_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-filter3.7.5_3.7.5-5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-filter3.7.5_3.7.5-5_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-atsc3.7.5_3.7.5-5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-atsc3.7.5_3.7.5-5_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-channels3.7.5_3.7.5-5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-channels3.7.5_3.7.5-5_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/gsl/libgsl0ldbl_1.16+dfsg-2build1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/gsl/libgsl0ldbl_1.16+dfsg-2build1_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/c/comedilib/libcomedi0_0.10.2-2_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/c/comedilib/libcomedi0_0.10.2-2_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-comedi3.7.5_3.7.5-5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-comedi3.7.5_3.7.5-5_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-digital3.7.5_3.7.5-5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-digital3.7.5_3.7.5-5_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-dtv3.7.5_3.7.5-5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-dtv3.7.5_3.7.5-5_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-noaa3.7.5_3.7.5-5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-noaa3.7.5_3.7.5-5_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-pager3.7.5_3.7.5-5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-pager3.7.5_3.7.5-5_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/q/qwt5/libqwt5-qt4_5.2.3-1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/q/qwt5/libqwt5-qt4_5.2.3-1_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-qtgui3.7.5_3.7.5-5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-qtgui3.7.5_3.7.5-5_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-trellis3.7.5_3.7.5-5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-trellis3.7.5_3.7.5-5_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-video-sdl3.7.5_3.7.5-5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-video-sdl3.7.5_3.7.5-5_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-vocoder3.7.5_3.7.5-5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-vocoder3.7.5_3.7.5-5_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-wavelet3.7.5_3.7.5-5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-wavelet3.7.5_3.7.5-5_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-wxgui3.7.5_3.7.5-5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-wxgui3.7.5_3.7.5-5_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/libp/libpgm/libpgm-5.1-0_5.1.118-1~dfsg-2ubuntu1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/libp/libpgm/libpgm-5.1-0_5.1.118-1~dfsg-2ubuntu1_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/libs/libsodium/libsodium13_1.0.1-1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/libs/libsodium/libsodium13_1.0.1-1_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-zeromq3.7.5_3.7.5-5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libgnuradio-zeromq3.7.5_3.7.5-5_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/e/expat/libexpat1-dev_2.1.0-6ubuntu1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/e/expat/libexpat1-dev_2.1.0-6ubuntu1_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/p/python2.7/libpython2.7-dev_2.7.9-2ubuntu3_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/p/python2.7/libpython2.7-dev_2.7.9-2ubuntu3_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/q/qwt/libqwt6_6.1.1-0ubuntu1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/q/qwt/libqwt6_6.1.1-0ubuntu1_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libvolk-bin_3.7.5-5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/libvolk-bin_3.7.5-5_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gr-iqbal/gr-iqbal_0.37.2-1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gr-iqbal/gr-iqbal_0.37.2-1_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/p/pyopengl/python-opengl_3.0.2-1_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/p/pyopengl/python-opengl_3.0.2-1_all.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/c/cheetah/python-cheetah_2.4.4-3.fakesyncbuild1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/c/cheetah/python-cheetah_2.4.4-3.fakesyncbuild1_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/gnuradio_3.7.5-5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gnuradio/gnuradio_3.7.5-5_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gqrx-sdr/gqrx-sdr_2.3.1-2build1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gqrx-sdr/gqrx-sdr_2.3.1-2build1_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gr-fcdproplus/gr-fcdproplus_3.7.11-3_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gr-fcdproplus/gr-fcdproplus_3.7.11-3_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/libd/libdrm/libdrm-dev_2.4.60-2_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/libd/libdrm/libdrm-dev_2.4.60-2_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/m/mesa/mesa-common-dev_10.5.2-0ubuntu1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/m/mesa/mesa-common-dev_10.5.2-0ubuntu1_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/libx/libx11/libx11-xcb-dev_1.6.2-2ubuntu2_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/libx/libx11/libx11-xcb-dev_1.6.2-2ubuntu2_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-dri3-dev_1.10-2ubuntu1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-dri3-dev_1.10-2ubuntu1_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-render0-dev_1.10-2ubuntu1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-render0-dev_1.10-2ubuntu1_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-randr0-dev_1.10-2ubuntu1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-randr0-dev_1.10-2ubuntu1_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-shape0-dev_1.10-2ubuntu1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-shape0-dev_1.10-2ubuntu1_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-xfixes0-dev_1.10-2ubuntu1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-xfixes0-dev_1.10-2ubuntu1_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-sync-dev_1.10-2ubuntu1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-sync-dev_1.10-2ubuntu1_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-present-dev_1.10-2ubuntu1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-present-dev_1.10-2ubuntu1_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/libx/libxshmfence/libxshmfence-dev_1.1-4_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/libx/libxshmfence/libxshmfence-dev_1.1-4_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-dri2-0-dev_1.10-2ubuntu1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-dri2-0-dev_1.10-2ubuntu1_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-glx0-dev_1.10-2ubuntu1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-glx0-dev_1.10-2ubuntu1_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/x/x11proto-xext/x11proto-xext-dev_7.3.0-1_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/x/x11proto-xext/x11proto-xext-dev_7.3.0-1_all.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/x/x11proto-fixes/x11proto-fixes-dev_5.0-2ubuntu2_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/x/x11proto-fixes/x11proto-fixes-dev_5.0-2ubuntu2_all.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/libx/libxfixes/libxfixes-dev_5.0.1-2_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/libx/libxfixes/libxfixes-dev_5.0.1-2_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/x/x11proto-damage/x11proto-damage-dev_1.2.1-2_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/x/x11proto-damage/x11proto-damage-dev_1.2.1-2_all.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/libx/libxdamage/libxdamage-dev_1.1.4-2_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/libx/libxdamage/libxdamage-dev_1.1.4-2_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/libx/libxext/libxext-dev_1.3.3-1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/libx/libxext/libxext-dev_1.3.3-1_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/x/x11proto-xf86vidmode/x11proto-xf86vidmode-dev_2.3.1-2_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/x/x11proto-xf86vidmode/x11proto-xf86vidmode-dev_2.3.1-2_all.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/libx/libxxf86vm/libxxf86vm-dev_1.1.3-1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/libx/libxxf86vm/libxxf86vm-dev_1.1.3-1_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/x/x11proto-dri2/x11proto-dri2-dev_2.8-2_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/x/x11proto-dri2/x11proto-dri2-dev_2.8-2_all.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/x/x11proto-gl/x11proto-gl-dev_1.4.17-1_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/x/x11proto-gl/x11proto-gl-dev_1.4.17-1_all.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libgl1-mesa-dev_10.5.2-0ubuntu1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libgl1-mesa-dev_10.5.2-0ubuntu1_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/libg/libglu/libglu1-mesa-dev_9.0.0-2_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/libg/libglu/libglu1-mesa-dev_9.0.0-2_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/p/python-defaults/libpython-dev_2.7.9-1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/p/python-defaults/libpython-dev_2.7.9-1_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/q/qtwebkit-source/libqtwebkit-dev_2.3.2-0ubuntu7_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/q/qtwebkit-source/libqtwebkit-dev_2.3.2-0ubuntu7_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/q/qwt/libqwt-dev_6.1.1-0ubuntu1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/q/qwt/libqwt-dev_6.1.1-0ubuntu1_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/p/python-dateutil/python-dateutil_2.2-2_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/p/python-dateutil/python-dateutil_2.2-2_all.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/p/python-decorator/python-decorator_3.4.0-2build1_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/p/python-decorator/python-decorator_3.4.0-2build1_all.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/p/python2.7/python2.7-dev_2.7.9-2ubuntu3_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/p/python2.7/python2.7-dev_2.7.9-2ubuntu3_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/p/python-defaults/python-dev_2.7.9-1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/p/python-defaults/python-dev_2.7.9-1_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/m/matplotlib/python-matplotlib-data_1.4.2-3.1_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/m/matplotlib/python-matplotlib-data_1.4.2-3.1_all.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/p/pyparsing/python-pyparsing_2.0.3+dfsg1-1_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/p/pyparsing/python-pyparsing_2.0.3+dfsg1-1_all.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/p/python-tz/python-tz_2014.10~dfsg1-0ubuntu1_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/p/python-tz/python-tz_2014.10~dfsg1-0ubuntu1_all.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/p/python-numpy/python-numpy_1.8.2-1ubuntu1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/p/python-numpy/python-numpy_1.8.2-1ubuntu1_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/p/python-mock/python-mock_1.0.1-3_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/p/python-mock/python-mock_1.0.1-3_all.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/n/nose/python-nose_1.3.4-2_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/n/nose/python-nose_1.3.4-2_all.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/m/matplotlib/python-matplotlib_1.4.2-3.1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/m/matplotlib/python-matplotlib_1.4.2-3.1_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/p/python-networkx/python-networkx_1.8.1-0ubuntu3_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/p/python-networkx/python-networkx_1.8.1-0ubuntu3_all.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/p/pyqwt5/python-qwt5-qt4_5.2.1~cvs20091107+dfsg-7build1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/p/pyqwt5/python-qwt5-qt4_5.2.1~cvs20091107+dfsg-7build1_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/p/python-stdlib-extensions/python-tk_2.7.9-1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/p/python-stdlib-extensions/python-tk_2.7.9-1_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/p/pyzmq/python-zmq_14.4.1-0ubuntu3_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/p/pyzmq/python-zmq_14.4.1-0ubuntu3_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/q/qthid-fcd-controller/qthid-fcd-controller_4.1-3_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/q/qthid-fcd-controller/qthid-fcd-controller_4.1-3_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/u/uhd/uhd-host_3.7.3-1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/u/uhd/uhd-host_3.7.3-1_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/p/python-scipy/python-scipy_0.14.1-1ubuntu1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/p/python-scipy/python-scipy_0.14.1-1ubuntu1_amd64.deb) 503  Service unavailable [IP: 202.158.214.106 80]

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
rafael@rafael-Latitude-E6230:~$ 
```

WHAT IS HAPPENING?????????

---

### Post by oldos2er on 2015-07-25
Try switching to the main server (in Software Center go to Edit, Software Sources); it appears au.archive.ubuntu.com is temporarily down.

---

### Post by Bucky Ball on 2015-07-25
Try Internode or aarnet rather than the au mirror. The other two are generally faster (and Internode or aarnet may be free upload/download from your ISP so check). 

Try:

```
sudo apt-get update
```

... in a terminal and if that breaks, post the error, but would probably confirm what olddos2er is saying.

---

