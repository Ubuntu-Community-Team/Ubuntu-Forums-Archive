---
title: "multiple issues -updates and checkbox"
date: 2013-11-18
forum: General Help
---

### Post by ryandcalvert on 2013-11-18
So I am trying to find the issue with my mahcine. One day my battery monitor just up and disapeared from my top bar using Gnome no-effects. Ubuntu 12.04. I have looked all over and finaly tried removing all my desktops, reverting to Unity and starting over....the problem still persists and now a new one has emerged. The following is from trying to reinstall python.

 sudo apt-get install python
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python is already the newest version.
The following packages were automatically installed and are no longer required:
  ffado-tools gir1.2-muffin-3.0 ubuntuone-control-panel-common libpath-class-perl
  libalgorithm-diff-perl libproc-simple-perl libgnome2-wnck-perl libsort-naturally-perl
  gir1.2-gtkclutter-1.0 liblapack-dev intltool-debian gcj-4.6-jre-lib libcinnamon-desktop0
  libblas-dev libxmmsclient6 libaudclient2 patchutils libpcre3-dev libmuparser0debian1
  libalgorithm-diff-xs-perl cinnamon-desktop-data libopencv-imgproc2.3
  libproc-processtable-perl libportsmf0 libalglib-2.6.0 libgl2ps0 libextutils-pkgconfig-perl
  dh-apparmor audacity-data po-debconf libgnome2-perl python-pypdf muffin-common
  libtamuanova-0.2 libsword-common r-doc-html libopencv-video2.3 caribou kalzium-data
  gir1.2-cinnamondesktop-3.0 libgoo-canvas-perl libgcj12 cinnamon-session libpcrecpp0
  libmail-sendmail-perl libmuffin0 gcj-4.6-base cjs python-tz cinnamon-common
  libgtkimageview0 libopencv-flann2.3 libreadline-dev python-matplotlib-data
  libgnome2-vfs-perl libgcj-common libalgorithm-merge-perl python-psycopg2
  libfile-which-perl libgavl1 gkbd-capplet libnemo-extension1 librarian0 libopencv-core2.3
  xiphos-data libhttp-server-simple-perl python-pysqlite2 libjson-perl
  cinnamon-settings-daemon libxml-simple-perl libtie-ixhash-perl python-pyparsing
  libqtexengine1 libcjs0c libopencv-ml2.3 libreadline6-dev qtiplot-doc libjson-xs-perl
  qt-assistant-compat libncurses5-dev libx11-protocol-perl libextutils-depends-perl
  libgtk2-unique-perl libgnome2-gconf-perl libid3tag0 apport-hooks-medibuntu html2text
  python-pythonmagick libtinfo-dev nemo-data libgtk2-imageview-perl libcommon-sense-perl
  pdftk python-scour libsys-hostname-long-perl cinnamon-translations libgnome2-canvas-perl
  libbz2-dev libfaac0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up checkbox (0.13.10) ...
/var/lib/dpkg/info/checkbox.postinst: 1: /usr/share/checkbox/install/postinst: tempfile: not found
dpkg: error processing checkbox (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of checkbox-qt:
 checkbox-qt depends on checkbox (>= 0.13.10); however:
  Package checkbox is not configured yet.
dpkg: error processing checkbox-qt (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 checkbox
 checkbox-qt
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

