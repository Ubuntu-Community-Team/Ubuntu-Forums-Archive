---
title: "Keyboard, mice doesn't work, boot animation keeps blinking after installing UbuntuSDK"
date: 2015-06-07
forum: General Help
---

### Post by Ankush_Menat on 2015-06-07
>I installed Ubuntu SDK using ppa as mentioned here - [https://developer.ubuntu.com/en/start/ubuntu-sdk/installing-the-sdk/](https://developer.ubuntu.com/en/start/ubuntu-sdk/installing-the-sdk/)

> I didn't use it, some work came up so I turned off laptop and when I started laptop again, its UNUSABLE! Boot animation blinks constantly, after like one minute login screen appears but keyboard and mouse(or touchpad) doesn't work.

> So I thought lets boot into upstart mode - Voila everything works (visually no errors). So I went ahead and removed ubuntu sdk package and did sudo apt-get autoremove (for removing lots of dependencies came with it)

Here is list of all packages installed with sdk...

```
Start-Date: 2015-06-07  19:39:50Commandline: apt-get install ubuntu-sdk
Install: accountsservice-ubuntu-schemas:amd64 (0.0.4+15.04.20150211-0ubuntu1, automatic), libqt5script5:amd64 (5.4.1+dfsg-3, automatic), pay-service:amd64 (2.0.0+14.10.20140916-0ubuntu1, automatic), qtdeclarative5-folderlistmodel-plugin:amd64 (5.4.1-1ubuntu5, automatic), python3-autopilot:amd64 (1.5.0+15.04.20150408-0ubuntu1, automatic), python-contextlib2:amd64 (0.4.0-2, automatic), python-distro-info:amd64 (0.14, automatic), python3-scope-harness:amd64 (0.5.4+15.04.20150410.2-0ubuntu1, automatic), libproperties-cpp-doc:amd64 (0.0.1+14.10.20140730-0ubuntu1, automatic), libqt5xmlpatterns5-dev:amd64 (5.4.1-1, automatic), qtdeclarative5-ubuntu-telephony-phonenumber0.1:amd64 (0.1+15.04.20150414-0ubuntu1, automatic), google-mock:amd64 (1.7.0-18092013-1, automatic), libubuntu-download-manager-common0:amd64 (0.9+15.04.20150203-0ubuntu1, automatic), ubuntuone-credentials-common:amd64 (14.04+15.04.20150401, automatic), libqt5concurrent5:amd64 (5.4.1+dfsg-2ubuntu4.1, automatic), kpartx:amd64 (0.4.9-3ubuntu12, automatic), qt5-qmake:amd64 (5.4.1+dfsg-2ubuntu4.1, automatic), libedit2:i386 (3.1-20140620-2, automatic), bzr:amd64 (2.6.0+bzr6595-6ubuntu1, automatic), libubuntu-platform-hardware-api2:amd64 (2.9.0+15.04.20150326-0ubuntu1, automatic), ubuntu-sdk-libs:amd64 (1.221), python3-apparmor:amd64 (2.9.1-0ubuntu9, automatic), libqdjango-db0:amd64 (0.5.0-1ubuntu1, automatic), libtinfo5:i386 (5.9+20140712-2ubuntu2, automatic), apparmor-easyprof:amd64 (2.9.1-0ubuntu9, automatic), qml-module-qtpositioning:amd64 (5.4.1-1ubuntu1, automatic), qtdeclarative5-dev-tools:amd64 (5.4.1-1ubuntu5, automatic), qtscript5-dev:amd64 (5.4.1+dfsg-3, automatic), libusermetricsinput1:amd64 (1.1.1+15.04.20150219-0ubuntu1, automatic), python-support:amd64 (1.0.15, automatic), libxcb-dri2-0:i386 (1.10-2ubuntu1, automatic), debootstrap:amd64 (1.0.67ubuntu0.1, automatic), libgflags2:amd64 (2.0-2.1build1, automatic), libqmenumodel0:amd64 (0.2.9+15.04.20150108-0ubuntu1, automatic), python3-dateutil:amd64 (2.2-2, automatic), libxfixes3:i386 (5.0.1-2, automatic), liblttng-ust-ctl2:amd64 (2.5.1-1ubuntu2, automatic), python-autopilot-trace:amd64 (1.4.1+14.10.20140822-0ubuntu1, automatic), python3-evdev:amd64 (0.4.1-0ubuntu3, automatic), libqt5declarative5:amd64 (5.4.1-1, automatic), libxau6:i386 (1.0.8-1, automatic), libautopilot-gtk:amd64 (1.4+15.04.20141218-0ubuntu1, automatic), qtcreator-plugin-ubuntu-common:amd64 (3.1.1+15.10.20150521-0ubuntu2~0vivid1, automatic), qttools5-dev:amd64 (5.4.1-1, automatic), python-keyring:amd64 (4.0-1ubuntu1, automatic), qt5-default:amd64 (5.4.1+dfsg-2ubuntu4.1, automatic), qml-module-qtqml-models2:amd64 (5.4.1-1ubuntu5, automatic), libpciaccess0:i386 (0.13.2-3build1, automatic), libpay2:amd64 (2.0.0+14.10.20140916-0ubuntu1, automatic), python-ubuntutools:amd64 (0.155~ubuntu2, automatic), python-evdev:amd64 (0.4.1-0ubuntu3, automatic), qtdeclarative5-ubuntu-syncmonitor0.1:amd64 (0.1+15.04.20150327-0ubuntu1, automatic), qtcreator:amd64 (3.1.1-0ubuntu9, automatic), python-subunit:amd64 (0.0.18-4, automatic), ubuntu-html5-ui-toolkit-examples:amd64 (0.1.2+15.04.20150410-0ubuntu1, automatic), pristine-tar:amd64 (1.33, automatic), click:amd64 (0.4.38.5, automatic), libxext6:i386 (1.3.3-1, automatic), qtcreator-plugin-cmake:amd64 (3.1.1+14.10.20140908-0ubuntu1, automatic), ubuntu-sdk-qmake-extras:amd64 (3.1.1+15.10.20150521-0ubuntu2~0vivid1, automatic), python-defusedxml:amd64 (0.4.1-2, automatic), qtbase5-doc:amd64 (5.4.1-1, automatic), qemu-user-static:amd64 (2.2+dfsg-5expubuntu9.1, automatic), python-lzma:amd64 (0.5.3-2build1, automatic), gir1.2-click-0.4:amd64 (0.4.38.5, automatic), ubuntu-html5-theme-examples:amd64 (0.1.2+15.04.20150410-0ubuntu1, automatic), libx11-xcb1:i386 (1.6.2-2ubuntu2, automatic), python3-psutil:amd64 (2.1.1-1, automatic), libio-stringy-perl:amd64 (2.110-5, automatic), qtdeclarative5-ubuntu-content1:amd64 (0.0+15.04.20150331-0ubuntu1.0, automatic), mediascanner2.0:amd64 (0.105+15.04.20150128-0ubuntu1, automatic), qtdeclarative5-qtorganizer-plugin:amd64 (5.0~git20140515~29475884-0ubuntu9, automatic), qtsvg5-doc:amd64 (5.4.1-1, automatic), python-oauth:amd64 (1.0.1-4, automatic), python3-fixtures:amd64 (1.0.0-01ubuntu1, automatic), libegl1-mesa-dev:amd64 (10.5.2-0ubuntu1, automatic), libunity-api-dev:amd64 (7.96+15.04.20150410.2-0ubuntu1, automatic), schroot-common:amd64 (1.6.10-1ubuntu1, automatic), qtsystems5-examples:amd64 (5.0~git20141206~44f70d99-0ubuntu2, automatic), libbotan-1.10-0:amd64 (1.10.8-2, automatic), libunity-api0:amd64 (7.96+15.04.20150410.2-0ubuntu1, automatic), qtdeclarative5-ubuntu-push-plugin:amd64 (0.1+15.04.20150312-0ubuntu1, automatic), libdrm-intel1:i386 (2.4.60-2, automatic), gir1.2-ubuntu-app-launch-2:amd64 (0.4+15.04.20150410-0ubuntu1, automatic), libdbus-cpp4:amd64 (4.3.0+15.04.20150415-0ubuntu1, automatic), qtscript5-doc:amd64 (5.4.1-1, automatic), libcontent-hub0:amd64 (0.0+15.04.20150331-0ubuntu1.0, automatic), python-testscenarios:amd64 (0.4-3, automatic), python-wadllib:amd64 (1.3.2-3, automatic), automake:amd64 (1.14.1-3ubuntu1, automatic), qtbase5-dev-tools:amd64 (5.4.1+dfsg-2ubuntu4.1, automatic), gcc-5-base:i386 (5.1~rc1-0ubuntu1, automatic), libxmltok1:amd64 (1.2-3build3, automatic), libubuntuoneauth-2.0-0:amd64 (14.04+15.04.20150401, automatic), qtdeclarative5-usermetrics0.1:amd64 (1.1.1+15.04.20150219-0ubuntu1, automatic), libllvm3.6:i386 (3.6-2ubuntu1, automatic), libgl1-mesa-dri:i386 (10.5.2-0ubuntu1, automatic), qtdeclarative5-dev:amd64 (5.4.1-1ubuntu5, automatic), python-autopilot-vis:amd64 (1.4.1+14.10.20140822-0ubuntu1, automatic), gir1.2-gee-0.8:amd64 (0.16.1-1, automatic), librbd1:amd64 (0.94.1-0ubuntu1, automatic), python3-pyqt4:amd64 (4.11.3+dfsg-1, automatic), schroot:amd64 (1.6.10-1ubuntu1, automatic), python3-junitxml:amd64 (0.6-1.1build1, automatic), liburcu2:amd64 (0.8.5-1ubuntu1, automatic), qttools5-doc:amd64 (5.4.1-1, automatic), libtrust-store1:amd64 (1.1.0+15.04.20150213-0ubuntu1, automatic), ubuntu-snappy-cli:amd64 (1.0.1-0ubuntu1, automatic), qml-module-qtorganizer:amd64 (5.0~git20140515~29475884-0ubuntu9, automatic), liblttng-ust0:amd64 (2.5.1-1ubuntu2, automatic), debsig-verify:amd64 (0.13, automatic), libmediascanner-2.0-3:amd64 (0.105+15.04.20150128-0ubuntu1, automatic), libdrm-radeon1:i386 (2.4.60-2, automatic), qtscript5-examples:amd64 (5.4.1+dfsg-3, automatic), libcontent-hub-dev:amd64 (0.0+15.04.20150331-0ubuntu1.0, automatic), libqt5svg5-dev:amd64 (5.4.1-1, automatic), devscripts:amd64 (2.15.1, automatic), libxcb1:i386 (1.10-2ubuntu1, automatic), qt3d5-dev:amd64 (5.0~git20130731-0ubuntu10, automatic), ubuntu-sdk-libs-dev:amd64 (1.221), qtcreator-doc:amd64 (3.1.1-0ubuntu9, automatic), qtquick1-5-examples:amd64 (5.4.1-1, automatic), ubuntu-sdk:amd64 (1.221), libqt5versit5:amd64 (5.0~git20140515~29475884-0ubuntu9, automatic), libubuntu-app-launch2:amd64 (0.4+15.04.20150410-0ubuntu1, automatic), qtlocation5-dev:amd64 (5.4.1-1ubuntu1, automatic), libudm-common0:amd64 (0.9+15.04.20150203-0ubuntu1, automatic), libgcc1:i386 (5.1~rc1-0ubuntu1, automatic), python-wstools:amd64 (0.4.3-3, automatic), qtcreator-plugin-ubuntu:amd64 (3.1.1+15.10.20150521-0ubuntu2~0vivid1, automatic), librados2:amd64 (0.94.1-0ubuntu1, automatic), python3-xlib:amd64 (0.14+20091101-1ubuntu3, automatic), libc6:i386 (2.21-0ubuntu4, automatic), libqt5bluetooth5-bin:amd64 (5.4.1-1ubuntu1, automatic), libqt5quicktest5:amd64 (5.4.1-1ubuntu5, automatic), python3-magic:amd64 (5.20-1ubuntu2, automatic), dput:amd64 (0.9.6.4ubuntu3, automatic), qtlocation5-examples:amd64 (5.4.1-1ubuntu1, automatic), libglapi-mesa:i386 (10.5.2-0ubuntu1, automatic), python-secretstorage:amd64 (2.1.1-1ubuntu1, automatic), ubuntu-html5-container:amd64 (0.1.2+15.04.20150410-0ubuntu1, automatic), qt3d5-examples:amd64 (5.0~git20130731-0ubuntu10, automatic), dctrl-tools:amd64 (2.23ubuntu1, automatic), libqt5positioning5-plugins:amd64 (5.4.1-1ubuntu1, automatic), libpoppler-qt5-1:amd64 (0.30.0-0ubuntu1, automatic), qtbase5-examples:amd64 (5.4.1+dfsg-2ubuntu4.1, automatic), python3-dbus.mainloop.qt:amd64 (4.11.3+dfsg-1, automatic), python3-extras:amd64 (0.0.3-3, automatic), libboost-dev:amd64 (1.55.0.2, automatic), libtxc-dxtn-s2tc0:i386 (0~git20131104-1.1, automatic), ubuntu-emulator:amd64 (0.20-0ubuntu1, automatic), libboost1.55-dev:amd64 (1.55.0+dfsg-3ubuntu2, automatic), libthumbnailer0:amd64 (1.3+15.04.20150312-0ubuntu1, automatic), python-debianbts:amd64 (1.12, automatic), usermetricsservice:amd64 (1.1.1+15.04.20150219-0ubuntu1, automatic), libqt5websockets5:amd64 (5.4.1-1, automatic), unity8-private:amd64 (8.02+15.04.20150409.1-0ubuntu1, automatic), libboost-program-options1.55.0:amd64 (1.55.0+dfsg-3ubuntu2, automatic), ubuntu-ui-toolkit-autopilot:amd64 (1.2.1458+15.04.20150422-0ubuntu1, automatic), qtgraphicaleffects5-doc:amd64 (5.4.1-1ubuntu1, automatic), qml-module-qttest:amd64 (5.4.1-1ubuntu5, automatic), qtdeclarative5-unity-notifications-plugin:amd64 (0.1.2+15.04.20141104-0ubuntu1, automatic), python-psutil:amd64 (2.1.1-1, automatic), qtdeclarative5-ubuntu-mediascanner0.1:amd64 (0.105+15.04.20150128-0ubuntu1, automatic), sqlite3:amd64 (3.8.7.4-1, automatic), libboost-serialization1.55.0:amd64 (1.55.0+dfsg-3ubuntu2, automatic), thumbnailer-common:amd64 (1.3+15.04.20150312-0ubuntu1, automatic), xdelta:amd64 (1.1.3-9.1ubuntu1, automatic), libonline-accounts-client1:amd64 (0.6+15.04.20150409-0ubuntu1, automatic), libqt5designercomponents5:amd64 (5.4.1-1, automatic), libcapnp-0.4.0:amd64 (0.4.0-1ubuntu2, automatic), qtscript5-doc-html:amd64 (5.4.1+dfsg-3, automatic), python3-autopilot-vis:amd64 (1.5.0+15.04.20150408-0ubuntu1, automatic), python-simplejson:amd64 (3.6.5-1ubuntu1, automatic), libqt5xmlpatterns5:amd64 (5.4.1-1, automatic), libcontent-hub-doc:amd64 (0.0+15.04.20150331-0ubuntu1.0, automatic), wdiff:amd64 (1.2.2-1, automatic), qml-module-qt-websockets:amd64 (5.4.1-1, automatic), cmake-extras:amd64 (0.3+15.04.20141204-0ubuntu1, automatic), libprocess-cpp2:amd64 (2.0.0+14.10.20140718-0ubuntu3, automatic), dh-make:amd64 (1.20140617, automatic), libunity-scopes-dev:amd64 (0.6.16+15.04.20150410.3-0ubuntu1, automatic), python-mimeparse:amd64 (0.1.4-1build1, automatic), libunity-scopes3:amd64 (0.6.16+15.04.20150410.3-0ubuntu1, automatic), pbuilder:amd64 (0.215ubuntu11, automatic), libxcb-glx0:i386 (1.10-2ubuntu1, automatic), qtdeclarative5-xmllistmodel-plugin:amd64 (5.4.1-1ubuntu5, automatic), qtsvg5-examples:amd64 (5.4.1-1, automatic), libudev1:i386 (219-7ubuntu5, automatic), libnet-cpp1:amd64 (1.1.0+15.04.20150305-0ubuntu1, automatic), libqt5designer5:amd64 (5.4.1-1, automatic), qtdeclarative5-examples:amd64 (5.4.1-1ubuntu5, automatic), click-reviewers-tools:amd64 (0.27-0~455~ubuntu15.04.1, automatic), libgl1-mesa-glx:i386 (10.5.2-0ubuntu1, automatic), libxdmcp6:i386 (1.1.1-1build1, automatic), qtdeclarative5-window-plugin:amd64 (5.4.1-1ubuntu5, automatic), libprocess-cpp-dev:amd64 (2.0.0+14.10.20140718-0ubuntu3, automatic), qml-module-qtquick-particles2:amd64 (5.4.1-1ubuntu5, automatic), libqt5versitorganizer5:amd64 (5.0~git20140515~29475884-0ubuntu9, automatic), python-fixtures:amd64 (1.0.0-01ubuntu1, automatic), libgoogle-glog0:amd64 (0.3.3-2build1, automatic), libqt5scripttools5:amd64 (5.4.1+dfsg-3, automatic), libexporter-lite-perl:amd64 (0.06-1, automatic), libxcb-sync1:i386 (1.10-2ubuntu1, automatic), libubuntu-location-service2:amd64 (2.1+15.04.20150226-0ubuntu1, automatic), libqt5quickwidgets5:amd64 (5.4.1-1ubuntu5, automatic), libgtest-dev:amd64 (1.7.0-3, automatic), python3-subunit:amd64 (0.0.18-4, automatic), qtxmlpatterns5-examples:amd64 (5.4.1-1, automatic), qml-module-qtmultimedia:amd64 (5.4.1-1ubuntu1, automatic), quilt:amd64 (0.63-3, automatic), ubuntu-device-flash:amd64 (0.20-0ubuntu1, automatic), python-lazr.uri:amd64 (1.0.3-2, automatic), libqt5multimediawidgets5:amd64 (5.4.1-1ubuntu1, automatic), python3-mimeparse:amd64 (0.1.4-1build1, automatic), qtcreator-plugin-go:amd64 (3.1.1+14.10.20140616-0ubuntu1, automatic), libqt5clucene5:amd64 (5.4.1-1, automatic), ubuntu-ui-toolkit-examples:amd64 (1.2.1458+15.04.20150422-0ubuntu1, automatic), bzr-builddeb:amd64 (2.8.9, automatic), libqt5x11extras5:amd64 (5.4.1-1, automatic), qtcreator-plugin-remotelinux:amd64 (3.1.1+14.10.20140616-0ubuntu4, automatic), libqt5multimediaquick-p5:amd64 (5.4.1-1ubuntu1, automatic), python-junitxml:amd64 (0.6-1.1build1, automatic), qtmultimedia5-dev:amd64 (5.4.1-1ubuntu1, automatic), qml-module-qtquick-controls:amd64 (5.4.1-0ubuntu1, automatic), qtcreator-plugin-valgrind:amd64 (3.1.1+14.10.20140616-0ubuntu4, automatic), libdrm-nouveau2:i386 (2.4.60-2, automatic), phablet-tools:amd64 (1.1+15.04.20150330-0ubuntu1, automatic), libxdelta2:amd64 (1.1.3-9.1ubuntu1, automatic), qml-module-ubuntu-onlineaccounts-client:amd64 (0.6+15.04.20150409-0ubuntu1, automatic), intltool:amd64 (0.51.0-1, automatic), qmlscene:amd64 (5.4.1-1ubuntu5, automatic), debian-keyring:amd64 (2015.03.04, automatic), libclick-0.4-0:amd64 (0.4.38.5, automatic), python-dns:amd64 (2.3.6-3, automatic), qtmultimedia5-examples:amd64 (5.4.1-1ubuntu1, automatic), libqt5opengl5-dev:amd64 (5.4.1+dfsg-2ubuntu4.1, automatic), click-ubuntu-policy:amd64 (0.1, automatic), python-extras:amd64 (0.0.3-3, automatic), qtdeclarative5-particles-plugin:amd64 (5.4.1-1ubuntu5, automatic), qtpositioning5-dev:amd64 (5.4.1-1ubuntu1, automatic), libu1db-qt5-examples:amd64 (0.1.5+15.04.20150327-0ubuntu1, automatic), autoconf:amd64 (2.69-8, automatic), python-gpgme:amd64 (0.3-1, automatic), autopilot-desktop-legacy:amd64 (1.4.1+14.10.20140822-0ubuntu1), gir1.2-gconf-2.0:amd64 (3.2.6-3ubuntu1, automatic), libnet-cpp-dev:amd64 (1.1.0+15.04.20150305-0ubuntu1, automatic), libu1db-qt5-3:amd64 (0.1.5+15.04.20150327-0ubuntu1, automatic), qtsvg5-doc-html:amd64 (5.4.1-1, automatic), qtdeclarative5-doc-html:amd64 (5.4.1-1ubuntu5, automatic), qtsensors5-examples:amd64 (5.4.1+dfsg-1ubuntu1, automatic), qml-module-qtquick-xmllistmodel:amd64 (5.4.1-1ubuntu5, automatic), qtdeclarative5-ubuntu-settings-components:amd64 (0.6+15.04.20150409.1-0ubuntu1, automatic), libqt5keychain0:amd64 (0.4.0-1, automatic), libprocess-cpp-doc:amd64 (2.0.0+14.10.20140718-0ubuntu3, automatic), qtdeclarative5-u1db1.0:amd64 (0.1.5+15.04.20150327-0ubuntu1, automatic), libjsoncpp-dev:amd64 (0.6.0~rc2-3.1ubuntu1, automatic), libqt5bluetooth5:amd64 (5.4.1-1ubuntu1, automatic), click-apparmor:amd64 (0.3.8, automatic), libxpathselect1.4:amd64 (1.4+14.04.20140303-0ubuntu1, automatic), apparmor-easyprof-ubuntu:amd64 (1.3.10, automatic), pybootchartgui:amd64 (0+r141-0ubuntu5, automatic), libqt5sensors5-dev:amd64 (5.4.1+dfsg-1ubuntu1, automatic), python-requests:amd64 (2.4.3-6, automatic), libusermetricsoutput1:amd64 (1.1.1+15.04.20150219-0ubuntu1, automatic), qttools5-examples:amd64 (5.4.1-1, automatic), libscope-harness1:amd64 (0.5.4+15.04.20150410.2-0ubuntu1, automatic), libqt53d5:amd64 (5.0~git20130731-0ubuntu10, automatic), ubuntu-app-launch:amd64 (0.4+15.04.20150410-0ubuntu1, automatic), click-dev:amd64 (0.4.38.5, automatic), python3-simplejson:amd64 (3.6.5-1ubuntu1, automatic), python-testtools:amd64 (0.9.39-1, automatic), libparse-debcontrol-perl:amd64 (2.005-4, automatic), python-soappy:amd64 (0.12.22-1, automatic), qtdeclarative5-online-accounts-client0.1:amd64 (0.6+15.04.20150409-0ubuntu1, automatic), qemu-utils:amd64 (2.2+dfsg-5expubuntu9.1, automatic), libqt5websockets5-dev:amd64 (5.4.1-1, automatic), python3-decorator:amd64 (3.4.0-2build1, automatic), account-plugin-tools:amd64 (0.12+15.04.20150415.1-0ubuntu2, automatic), qttestability-autopilot:amd64 (1.4+14.10.20140820-0ubuntu1, automatic), python-configobj:amd64 (5.0.6-1, automatic), qml-module-qtsensors:amd64 (5.4.1+dfsg-1ubuntu1, automatic), libproperties-cpp-dev:amd64 (0.0.1+14.10.20140730-0ubuntu1, automatic), python3-testscenarios:amd64 (0.4-3, automatic), zlib1g:i386 (1.2.8.dfsg-2ubuntu1, automatic), libzmqpp3:amd64 (3.2.0-0ubuntu3, automatic), qtpim5-dev:amd64 (5.0~git20140515~29475884-0ubuntu9, automatic), libqt5help5:amd64 (5.4.1-1, automatic), libxdamage1:i386 (1.1.4-2, automatic), libxxf86vm1:i386 (1.1.3-1, automatic), qtmultimedia5-doc:amd64 (5.4.1-1ubuntu1, automatic), ubuntu-html5-ui-toolkit:amd64 (0.1.2+15.04.20150410-0ubuntu1, automatic), libexpat1:i386 (2.1.0-6ubuntu1, automatic), libdistro-info-perl:amd64 (0.14, automatic), ubuntu-dev-tools:amd64 (0.155~ubuntu2, automatic), libelf1:i386 (0.160-0ubuntu3, automatic), python-reportbug:amd64 (6.6.3ubuntu1, automatic), debian-archive-keyring:amd64 (2014.3, automatic), libxcb-dri3-0:i386 (1.10-2ubuntu1, automatic), thumbnailer-service:amd64 (1.3+15.04.20150312-0ubuntu1, automatic), ubuntu-emulator-runtime:i386 (20141117-0039-0ubuntu11, automatic), libgles2-mesa-dev:amd64 (10.5.2-0ubuntu1, automatic), libqt5multimedia5-plugins:amd64 (5.4.1-1ubuntu1, automatic), reportbug:amd64 (6.6.3ubuntu1, automatic), libqt5contacts5:amd64 (5.0~git20140515~29475884-0ubuntu9, automatic), distro-info:amd64 (0.14, automatic), qtmultimedia5-doc-html:amd64 (5.4.1-1ubuntu1, automatic), libjsoncpp0:amd64 (0.6.0~rc2-3.1ubuntu1, automatic), qtdeclarative5-ubuntu-download-manager0.1:amd64 (0.9+15.04.20150203-0ubuntu1, automatic), qtdeclarative5-controls-plugin:amd64 (5.4.1-0ubuntu1, automatic), python3-testtools:amd64 (0.9.39-1, automatic), libxcb-present0:i386 (1.10-2ubuntu1, automatic), libubuntu-download-manager-client0:amd64 (0.9+15.04.20150203-0ubuntu1, automatic), fbset:amd64 (2.1-28, automatic), qtdeclarative5-poppler1.0:amd64 (0.1.1+13.10.20130819.3-0ubuntu3, automatic), autotools-dev:amd64 (20140911.1, automatic), python3-autopilot-trace:amd64 (1.5.0+15.04.20150408-0ubuntu1, automatic), python3-click:amd64 (0.4.38.5, automatic), libqt5quickparticles5:amd64 (5.4.1-1ubuntu5, automatic), python3-libapparmor:amd64 (2.9.1-0ubuntu9, automatic), libboost-log1.55.0:amd64 (1.55.0+dfsg-3ubuntu2, automatic), libqgsttools-p1:amd64 (5.4.1-1ubuntu1, automatic), python-bzrlib:amd64 (2.6.0+bzr6595-6ubuntu1, automatic), qtcreator-plugin-qnx:amd64 (3.1.1+14.10.20140616-0ubuntu4, automatic), libautopilot-qt:amd64 (1.4+14.10.20140820-0ubuntu1, automatic), libqt5nfc5:amd64 (5.4.1-1ubuntu1, automatic), python-autopilot:amd64 (1.4.1+14.10.20140822-0ubuntu1, automatic), unity-scope-tool:amd64 (8.02+15.04.20150409.1-0ubuntu1, automatic), python3-sip:amd64 (4.16.6+dfsg-1, automatic), pbzip2:amd64 (1.1.9-1, automatic), python3-apparmor-click:amd64 (0.3.8, automatic), libstdc++6:i386 (4.9.2-10ubuntu13, automatic), qtwebkit5-doc-html:amd64 (5.4.1+dfsg-2ubuntu1, automatic), qml-module-qtlocation:amd64 (5.4.1-1ubuntu1, automatic), libdrm2:i386 (2.4.60-2, automatic), autopilot-qt4:amd64 (1.4+14.10.20140820-0ubuntu1, automatic), autopilot-qt5:amd64 (1.4+14.10.20140820-0ubuntu1, automatic), libqt5location5:amd64 (5.4.1-1ubuntu1, automatic), libphonenumber6:amd64 (6.0+r655-0ubuntu6, automatic), libx11-6:i386 (1.6.2-2ubuntu2, automatic), python-launchpadlib:amd64 (1.10.3-1, automatic), unity-plugin-scopes:amd64 (0.5.4+15.04.20150410.2-0ubuntu1, automatic), at:amd64 (3.1.16-1ubuntu1, automatic), unity8-fake-env:amd64 (8.02+15.04.20150409.1-0ubuntu1, automatic), qtconnectivity5-examples:amd64 (5.4.1-1ubuntu1, automatic), libqt5location5-plugins:amd64 (5.4.1-1ubuntu1, automatic), libqt5sensors5:amd64 (5.4.1+dfsg-1ubuntu1, automatic), distro-info-data:amd64 (0.26ubuntu0.1, automatic), qtdeclarative5-ubuntu-thumbnailer0.1:amd64 (1.3+15.04.20150312-0ubuntu1, automatic), autopilot-desktop:amd64 (1.5.0+15.04.20150408-0ubuntu1), gcc-4.9-base:i386 (4.9.2-10ubuntu13, automatic), unity-action-doc:amd64 (1.1.0+14.04.20140304-0ubuntu1, automatic), click-doc:amd64 (0.4.38.5, automatic), qtbase5-dev:amd64 (5.4.1+dfsg-2ubuntu4.1, automatic), libxshmfence1:i386 (1.1-4, automatic), unity8-common:amd64 (8.02+15.04.20150409.1-0ubuntu1, automatic), libffi6:i386 (3.2.1-2, automatic), python-lazr.restfulclient:amd64 (0.13.4-4, automatic), gdb-multiarch:amd64 (7.9-1ubuntu1, automatic), ubuntu-ui-toolkit-doc:amd64 (1.2.1458+15.04.20150422-0ubuntu1, automatic)
End-Date: 2015-06-07  19:49:15



```

> So I decided to make upstart default using - [https://wiki.ubuntu.com/SystemdForUpstartUsers#Permanent_switch_back_to_upstart](https://wiki.ubuntu.com/SystemdForUpstartUsers#Permanent_switch_back_to_upstart)

> Rebooted... Blinking and flickering started in upstart mode too. So I selected advance>systemd mode. Everything works properly (I am typing using my laptop currently.)

Now I am forced to press ECS on everyboot and select advanced mode :( What can I do to fix all this mess?


Edit: default boot mode is highly unpredictable now. I rebooted once more to see what happens - NOTHING HAPPENS, plain black screen for 4-5 minutes -_-

Edit2 : Here is grub.conf if it helps
```
## DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#


### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi


if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi


export menuentry_id_option


if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi


function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}
function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}
function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}


if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_gpt
insmod ext2
set root='hd0,gpt2'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  75e53bf4-9d4b-47dc-9c07-1cbada4801b0
else
  search --no-floppy --fs-uuid --set=root 75e53bf4-9d4b-47dc-9c07-1cbada4801b0
fi
    font="/usr/share/grub/unicode.pf2"
fi


if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_IN
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=0
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 0 ; then
    set timeout=0
  fi
fi
### END /etc/grub.d/00_header ###


### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30,0; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###


### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-75e53bf4-9d4b-47dc-9c07-1cbada4801b0' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  75e53bf4-9d4b-47dc-9c07-1cbada4801b0
    else
      search --no-floppy --fs-uuid --set=root 75e53bf4-9d4b-47dc-9c07-1cbada4801b0
    fi
    linux    /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=75e53bf4-9d4b-47dc-9c07-1cbada4801b0 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.19.0-18-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-75e53bf4-9d4b-47dc-9c07-1cbada4801b0' {
    menuentry 'Ubuntu, with Linux 3.19.0-18-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-18-generic-advanced-75e53bf4-9d4b-47dc-9c07-1cbada4801b0' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  75e53bf4-9d4b-47dc-9c07-1cbada4801b0
        else
          search --no-floppy --fs-uuid --set=root 75e53bf4-9d4b-47dc-9c07-1cbada4801b0
        fi
        echo    'Loading Linux 3.19.0-18-generic ...'
        linux    /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=75e53bf4-9d4b-47dc-9c07-1cbada4801b0 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-18-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-18-generic (systemd)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-18-generic-init-systemd-75e53bf4-9d4b-47dc-9c07-1cbada4801b0' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  75e53bf4-9d4b-47dc-9c07-1cbada4801b0
        else
          search --no-floppy --fs-uuid --set=root 75e53bf4-9d4b-47dc-9c07-1cbada4801b0
        fi
        echo    'Loading Linux 3.19.0-18-generic ...'
        linux    /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=75e53bf4-9d4b-47dc-9c07-1cbada4801b0 ro  quiet splash $vt_handoff init=/lib/systemd/systemd
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-18-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-18-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-18-generic-recovery-75e53bf4-9d4b-47dc-9c07-1cbada4801b0' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  75e53bf4-9d4b-47dc-9c07-1cbada4801b0
        else
          search --no-floppy --fs-uuid --set=root 75e53bf4-9d4b-47dc-9c07-1cbada4801b0
        fi
        echo    'Loading Linux 3.19.0-18-generic ...'
        linux    /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=75e53bf4-9d4b-47dc-9c07-1cbada4801b0 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-18-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-16-generic-advanced-75e53bf4-9d4b-47dc-9c07-1cbada4801b0' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  75e53bf4-9d4b-47dc-9c07-1cbada4801b0
        else
          search --no-floppy --fs-uuid --set=root 75e53bf4-9d4b-47dc-9c07-1cbada4801b0
        fi
        echo    'Loading Linux 3.19.0-16-generic ...'
        linux    /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=75e53bf4-9d4b-47dc-9c07-1cbada4801b0 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-16-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-16-generic (systemd)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-16-generic-init-systemd-75e53bf4-9d4b-47dc-9c07-1cbada4801b0' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  75e53bf4-9d4b-47dc-9c07-1cbada4801b0
        else
          search --no-floppy --fs-uuid --set=root 75e53bf4-9d4b-47dc-9c07-1cbada4801b0
        fi
        echo    'Loading Linux 3.19.0-16-generic ...'
        linux    /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=75e53bf4-9d4b-47dc-9c07-1cbada4801b0 ro  quiet splash $vt_handoff init=/lib/systemd/systemd
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-16-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-16-generic-recovery-75e53bf4-9d4b-47dc-9c07-1cbada4801b0' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  75e53bf4-9d4b-47dc-9c07-1cbada4801b0
        else
          search --no-floppy --fs-uuid --set=root 75e53bf4-9d4b-47dc-9c07-1cbada4801b0
        fi
        echo    'Loading Linux 3.19.0-16-generic ...'
        linux    /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=75e53bf4-9d4b-47dc-9c07-1cbada4801b0 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-16-generic
    }
}


### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/20_linux_xen ###


### END /etc/grub.d/20_linux_xen ###


### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###


### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###


### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###


### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###


### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###



```

---

### Post by Ankush_Menat on 2015-06-07
Bump?

---

### Post by Ankush_Menat on 2015-06-08
Another bump...!

---

