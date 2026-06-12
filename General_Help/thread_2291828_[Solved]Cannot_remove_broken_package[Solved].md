---
title: "[Solved]Cannot remove broken package[Solved]"
date: 2015-08-23
forum: General Help
---

### Post by Cg_boy on 2015-08-23
Hello.

I have a problem, I tried installing a package(libstdc++6), But something happened,
and now I think its broken. I've tried to remove it, but it doesn't work.
The problem might be because the package was for a more recent Ubuntu version.

If I run sudo apt-get install -f, it wants to remove tons of packages.

This is what I get when I run sudo apt-get remove libstdc++6:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 abiword : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 abiword-plugin-grammar : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 abiword-plugin-mathview : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 acetoneiso : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 adobe-flashplugin : Depends: libstdc++6 (>= 4.3) but it is not going to be installed
                     Recommends: adobe-flash-properties-gtk (= 1:20150512.1-0trusty1) but it is not going to be installed or
                                 adobe-flash-properties-kde (= 1:20150512.1-0trusty1) but it is not going to be installed
 angelscript : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 apt : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 apt-transport-https : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 apt-utils : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 aspell : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 audacity : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 caelum : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 caps : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 cdrdao : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 celestia-gnome : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 cmake : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 crrcsim : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 cups : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 cups-filters : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 cups-filters-core-drivers : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 cups-ppdc : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 dosbox : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 dvd+rw-tools : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 dvgrab : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 firefox : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 frei0r-plugins : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 gdisk : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 geany : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 gnucap : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 groff-base : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 growisofs : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 gstreamer0.10-plugins-good : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 gstreamer1.0-plugins-good : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 katepart : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 kde-runtime : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 kdelibs-bin : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 kdelibs5-plugins : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 kdenlive : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 kdoctools : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 kolourpaint4 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 kstars : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 kubuntu-debug-installer : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 leocad : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
          Recommends: leocad-parts but it is not installable
 libabiword-3.0 : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 libapt-inst1.5 : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 libapt-pkg-perl : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libapt-pkg4.12 : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 libaspell15 : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 libasprintf0c2 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libatkmm-1.6-1 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libattica0.4 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libaudiofile1 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libavifile-0.7c2 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libbaloocore4 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libbaloofiles4 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libbalooxapian4 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libbasicusageenvironment0 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libboost-system1.54.0 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libboost-thread1.46.1 : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 libboost-thread1.54.0 : Depends: libstdc++6 (>= 4.2.1) but it is not going to be installed
 libbulletcollision2.81 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libbulletdynamics2.81 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libbulletsoftbody2.81 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libcaca0 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libcairomm-1.0-1 : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 libcgal10 : Depends: libstdc++6 (>= 4.2.1) but it is not going to be installed
 libchromaprint0 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libclucene-core1 : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 libcrystalhd3 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libcupsppdc1 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libdbusmenu-qt2 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libdirac-encoder0 : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 libdjvulibre21 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libebml4 : Depends: libstdc++6 (>= 4.2.1) but it is not going to be installed
 libegl1-mesa-drivers : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 libenchant1c2a : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libexempi3 : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 libexiv2-12 : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 libflac++6 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libframe6 : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 libfreeimage3 : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 libgdome2-cpp-smart0c2a : Depends: libstdc++6 (>= 4.2.1) but it is not going to be installed
 libgegl-0.2-0 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libgexiv2-2 : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 libgl1-mesa-dri : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 libglibmm-2.4-1c2a : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 libglu1-mesa : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libgnutlsxx27 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libgrail6 : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 libgroupsock1 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libgtkmathview0c2a : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 libgtkmm-3.0-1 : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 libhunspell-1.3-0 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libicu52 : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 libilmbase6 : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 libirrlicht1.8 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libjack-jackd2-0 : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 libjavascriptcoregtk-1.0-0 : Depends: libstdc++6 (>= 4.8.1) but it is not going to be installed
 libjavascriptcoregtk-3.0-0 : Depends: libstdc++6 (>= 4.8.1) but it is not going to be installed
 libkactivities-bin : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libkactivities-models1 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libkactivities6 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libkatepartinterfaces4 : Depends: libstdc++6 (>= 4.2.1) but it is not going to be installed
 libkcmutils4 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libkde3support4 : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 libkdeclarative5 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libkdecore5 : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 libkdesu5 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libkdeui5 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libkdewebkit5 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libkdnssd4 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libkemoticons4 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libkfile4 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libkhtml5 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libkidletime4 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libkio5 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libkjsapi4 : Depends: libstdc++6 (>= 4.2.1) but it is not going to be installed
 libkjsembed4 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libkmediaplayer4 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libknewstuff3-4 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libknotifyconfig4 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libkparts4 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libkprintutils4 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libkpty4 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libkrosscore4 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libktexteditor4 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libkubuntu0 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libkxmlrpcclient4 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libleveldb1 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 liblinearmath2.81 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 liblivemedia23 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libllvm3.4 : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 liblua5.1-0 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libmatroska6 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libmediainfo0 : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 libmirclient7 : Depends: libstdc++6 (>= 4.8.1) but it is not going to be installed
 libmirclientplatform-mesa : Depends: libstdc++6 (>= 4.8) but it is not going to be installed
 libmirprotobuf0 : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 libmlt++3 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libmlt6 : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 libmodplug1 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libmpeg2encpp-2.1-0 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libmplex2-2.1-0 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libmsgpack3 : Depends: libstdc++6 (>= 4.2.1) but it is not going to be installed
 libnepomuk4 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libnepomukcleaner4 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libnepomukcore4abi1 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libnepomukquery4a : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libnepomukutils4 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libntrack-qt4-1 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libode1 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libogre-1.7.4 : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 libogre-1.8.0 : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 libois-1.3.0 : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 libopencv-core2.4 : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 libopencv-highgui2.4 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libopencv-imgproc2.4 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libopencv-objdetect2.4 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libopenexr6 : Depends: libstdc++6 (>= 4.2.1) but it is not going to be installed
 libosmesa6 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libpangomm-1.4-1 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libphonon4 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libplasma3 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libplib1 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libpolkit-qt-1-1 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libpoppler-glib8 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libpoppler-qt4-4 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libpoppler44 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libportsmf0 : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 libprotobuf-lite8 : Depends: libstdc++6 (>= 4.3) but it is not going to be installed
 libprotobuf8 : Depends: libstdc++6 (>= 4.3) but it is not going to be installed
 libproxy1 : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 libqapt2 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libqapt2-runtime : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libqca2 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libqimageblitz4 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libqjson0 : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 libqmobipocket1 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libqpdf13 : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 libqt3-mt : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libqt4-declarative : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libqt4-designer : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libqt4-help : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libqt4-network : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libqt4-opengl : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libqt4-qt3support : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libqt4-script : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libqt4-scripttools : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libqt4-sql : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libqt4-sql-mysql : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libqt4-svg : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libqt4-test : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libqt4-xml : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libqt4-xmlpatterns : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libqtassistantclient4 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libqtcore4 : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 libqtdbus4 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libqtgui4 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libqtwebkit4 : Depends: libstdc++6 (>= 4.2.1) but it is not going to be installed
 libraw9 : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 libresid-builder0c2a : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 librtaudio4 : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 librtmidi1 : Depends: libstdc++6 (>= 4.2.1) but it is not going to be installed
 libsbsms10 : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 libsidplay2 : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 libsigc++-2.0-0c2a : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 libsmpeg0 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libsnappy1 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libsolid4 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libsoprano4 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libsoundtouch0 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libstdc++-4.8-dev : Depends: libstdc++6 (>= 4.8.2-19ubuntu1) but it is not going to be installed
 libstk0c2a : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 libstreamanalyzer0 : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 libstreams0 : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 libtag1-vanilla : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 libtagc0 : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 libtbb2 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libthreadweaver4 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libtinyxml2-0.0.0 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libtxc-dxtn-s2tc0 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libusageenvironment1 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libvamp-hostsdk3 : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 libvisual-0.4-plugins : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libwebkitgtk-1.0-0 : Depends: libstdc++6 (>= 4.8.1) but it is not going to be installed
 libwebkitgtk-3.0-0 : Depends: libstdc++6 (>= 4.8.1) but it is not going to be installed
 libwpd-0.9-9 : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 libwpg-0.2-2 : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 libwps-0.2-2 : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 libwxbase2.8-0 : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 libwxgtk2.8-0 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 libxapian22 : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 libzen0 : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 lmms : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 lshw : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 mediainfo-gui : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 minetestc55 : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 mjpegtools : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 muse : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 nepomuk-core-runtime : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 nload : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 nomnom : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 onboard : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 p7zip : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 p7zip-full : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 panda3d1.9 : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
              Recommends: libstdc++6 (>= 4.6) but it is not going to be installed
              Recommends: python-wxversion but it is not going to be installed
              Recommends: python-profiler (>= 2.7)
 pavucontrol : Depends: libstdc++6 (>= 4.2.1) but it is not going to be installed
 phonon-backend-gstreamer : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 pinentry-qt4 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 plasma-scriptengine-javascript : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 poppler-utils : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 powertop : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 primus-libs : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 printer-driver-hpcups : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 printer-driver-splix : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 python-apt : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 python-qt4 : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 python-xapian : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 python3-apt : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 qapt-batch : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 qastrocam-g2 : Depends: libstdc++6 (>= 4.2.1) but it is not going to be installed
                Recommends: avifile-win32-plugin (>= 1:0.7.47) but it is not installable
                Recommends: nas but it is not going to be installed
 qdbus : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 qpdf : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 qtchooser : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 rigsofrods : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 smtube : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 socketw : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 soprano-daemon : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 stellarium : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 stk : Depends: libstdc++6 (>= 4.2.1) but it is not going to be installed
 stopmotion : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
              Recommends: ffmpeg but it is not installable
 telnet : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 thunderbird : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 toshset : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 unrar : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 vlc : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 vlc-nox : Depends: libstdc++6 (>= 4.6) but it is not going to be installed
           Recommends: libdvdcss2 but it is not installable
 xfce4-whiskermenu-plugin : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 xplanet : Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 zeitgeist-core : Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


```

I'm running Xubuntu 14.04 64 bit. I installed the package with a deb file.

Please help. Thanks.

---

### Post by QIII on 2015-08-23
Hello!

What makes you think it's broken?

Where did you get the .deb?

---

### Post by Cg_boy on 2015-08-23
I got it from packages.ubuntu.com.

Not sure its broken, but I don't think its fully installed.

---

### Post by QIII on 2015-08-23
OK.  What makes you think it's not fully installed?  Did you get errors when you were installing it?

By the way, that package is in the Trusty repo and the following should have installed it:

```
sudo apt-get install libstdc++6

```

---

### Post by Cg_boy on 2015-08-23
I installed it using GDebi. I think there was some error, but I can't remember it. It then told me that I could run sudo apt-get install -f.

---

### Post by QIII on 2015-08-23
OK.  Hold on.  Let me confirm the point version of that package.


Edit:  Looks like the Trusty repo has libstdc++6 4.8.4-2, which is greater than all the complaints in your output.

Since you used Gdebi, you should be able to just try 

```
sudo apt-get install --reinstall libstdc++6
```

Do that from the command line and post back any errors you encounter.

---

### Post by Cg_boy on 2015-08-23
Unfortunately, it didn't work:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of libstdc++6 is not possible, it cannot be downloaded.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libstdc++6 : Breaks: libstdc++6:i386 (!= 5.2.1-15ubuntu1) but 4.8.2-19ubuntu1 is to be installed
 libstdc++6:i386 : Breaks: libstdc++6 (!= 4.8.2-19ubuntu1) but 5.2.1-15ubuntu1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


```

---

### Post by Cg_boy on 2015-08-23
Isn't there any way to fix or remove this package?

Thanks for the help.

---

### Post by CantankRus on 2015-08-23
What is the full name of the deb package you downloaded?

What does this command give you...
```
apt-cache policy libstdc++6
```

Might want to post enabled sources as well...
```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*.list
```

---

### Post by Cg_boy on 2015-08-23
First command gives me this:
```
  Installed: 5.2.1-15ubuntu1
  Candidate: 5.2.1-15ubuntu1
  Version table:
 *** 5.2.1-15ubuntu1 0
        100 /var/lib/dpkg/status
     4.8.2-19ubuntu1 0
        500 http://za.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages

```

Second command gives me this:
```
/etc/apt/sources.list:deb http://za.archive.ubuntu.com/ubuntu/ trusty main restricted
/etc/apt/sources.list:deb-src http://za.archive.ubuntu.com/ubuntu/ trusty main restricted
/etc/apt/sources.list:deb http://za.archive.ubuntu.com/ubuntu/ trusty universe
/etc/apt/sources.list:deb-src http://za.archive.ubuntu.com/ubuntu/ trusty universe
/etc/apt/sources.list:deb http://za.archive.ubuntu.com/ubuntu/ trusty multiverse
/etc/apt/sources.list:deb-src http://za.archive.ubuntu.com/ubuntu/ trusty multiverse
/etc/apt/sources.list:deb http://archive.canonical.com/ubuntu trusty partner
/etc/apt/sources.list:deb http://extras.ubuntu.com/ubuntu trusty main
/etc/apt/sources.list:deb-src http://extras.ubuntu.com/ubuntu trusty main
/etc/apt/sources.list.d/ubuntu-wine-ppa-trusty.list:deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu trusty main

```

---

### Post by CantankRus on 2015-08-23
You need to force the version of libstdc++6 .
eg for you from your **apt-cache policy libstdc++6** output it is...
```
sudo apt-get install libstdc++6=4.8.2-19ubuntu1
```
but I'm not sure how to get back to a position where that command will run without error.

---

### Post by CantankRus on 2015-08-23
Seems that to install **libstdc++6_5.2.1-15ubuntu1** 
you also need to download and install
**gcc-5-base_5.2.1-15ubuntu1** first, which you must have done.
This links the **/usr/share/doc/libstdc++6** folder to **/usr/share/doc/gcc-5-base**

Deleting the **/usr/share/doc/libstdc++6** folder link allows the new link to be created to **/usr/share/doc/gcc-4.8-base**.
```
sudo rm /usr/share/doc/libstdc++6
```

This allows the force version command to now run. You don't appear to have the trusty-updates repo enabled
so your version is different than mine.
> **[COLOR="#006400"]glen@Trusty:~$[/COLOR] apt-cache policy libstdc++6**
libstdc++6:
  Installed: 4.8.4-2ubuntu1~14.04
  Candidate: 4.8.4-2ubuntu1~14.04
  Version table:
 *** 4.8.4-2ubuntu1~14.04 0
        500 [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) trusty-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     4.8.2-19ubuntu1 0
        500 [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) trusty/main amd64 Packages

```
sudo apt-get install libstdc++6=[COLOR="#696969"]4.8.2-19ubuntu1[/COLOR]
```

Check for further errors...
```
sudo apt-get update 
```

Don't know why you were installing debs for this. Try enabling trusty-updates.

---

### Post by Cg_boy on 2015-08-25
THANK YOU!!! It works now!

---

### Post by CantankRus on 2015-08-25
Ok, good.
You may want to also remove gcc-5-base.
Check only removes gcc-5-base.
```
sudo apt-get remove gcc-5-base
```

---

