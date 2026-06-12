---
title: "Problems with Procps"
date: 2014-01-22
forum: General Help
---

### Post by Keith_Capel on 2014-01-22
After some time not upgrading my system I have come across this little bug.

k@ukscifi ~ $ sudo apt-get install -f
[sudo] password for k: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  aften awn-applet-animal-farm awn-applet-common-folder
  awn-applet-media-icon-applet awn-applet-related awn-applet-showdesktop
  awn-applet-thinkhdaps awn-applets-common bzr chromium-codecs-ffmpeg-extra
  cinnamon-bluetooth cinnamon-session cjs emacs23-bin-common emacs23-common
  emacs23-common-non-dfsg faac flam3 gir1.2-unique-3.0
  gnome-control-center-unity gnome-system-monitor gnucash-docs gpac
  gpac-modules-base guile-1.8 libappindicator0.1-cil libaqbanking-data
  libaqbanking-plugins-libgwenhywfar60 libaqbanking34 libaqbanking34-plugins
  libaqhbci20 libaqofxconnect7 libart2.0-cil libart2.0-cil-dev libawn1
  libcjs0c libdbi1 libdesktop-agnostic-cfg-keyfile libdesktop-agnostic-data
  libdesktop-agnostic-vfs-gio libdesktop-agnostic0 libextutils-depends-perl
  libextutils-pkgconfig-perl libfinance-quote-perl libglade2.0-cil
  libgnome-menu2 libgnome2-canvas-perl libgnome2-wnck-perl
  libgoffice-0.8-8-common libgoo-canvas-perl libgoocanvas-common libgoocanvas3
  libgpac2 libgtk2-imageview-perl libgtk2-unique-perl libgtkimageview0
  libgtksourceview2-2.0-cil libgtksourceview2-cil-dev libgwengui-gtk2-0
  libgwenhywfar-data libgwenhywfar60 libhsqldb1.8.0-java libjs-mootools
  libktoblzcheck1c2a libm17n-0 libofx4 liboggz2 libopencv-calib3d2.4
  libopencv-contrib2.4 libopencv-features2d2.4 libopencv-flann2.4
  libopencv-legacy2.4 libopencv-ml2.4 libopencv-objdetect2.4
  libopencv-photo2.4 libopencv-video2.4 liborcus-0.6-0 libosp5 libotf0
  libpath-class-perl libproc-processtable-perl libproc-simple-perl
  librsvg2-2.0-cil-dev librsvg2-2.18-cil libssl0.9.8 libvte0.16-cil
  libvte0.16-cil-dev libxine2-bin m17n-contrib m17n-db miro-data mkvtoolnix
  oggz-tools ogmrip-doc ogmtools perlmagick pulseaudio-module-zeroconf
  python-apsw python-awn python-awn-extras python-desktop-agnostic
  python-gmenu python-m2crypto python-opencv python-wnck python3-feedparser
  slib telepathy-indicator tidy tofrodos tribler-swift unity-scope-audacious
  unity-scope-calculator unity-scope-chromiumbookmarks unity-scope-clementine
  unity-scope-colourlovers unity-scope-devhelp unity-scope-firefoxbookmarks
  unity-scope-gmusicbrowser unity-scope-gourmet unity-scope-guayadeque
  unity-scope-home unity-scope-manpages unity-scope-musique
  unity-scope-openclipart unity-scope-texdoc unity-scope-tomboy
  unity-scope-virtualbox unity-scope-yelp unity-scope-zotero
  unity-scopes-master-default vim-gui-common vim-runtime
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 24 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up procps (1:3.3.4-2) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: Service mountkernfs has to be enabled to start service procps
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing procps (--configure):
 subprocess installed post-installation script returned error exit status 1
configured to not write apport reports
                                      Errors were encountered while processing:
 procps
E: Sub-process /usr/bin/dpkg returned an error code (1)

When trying to remove procps - I'm asked to remove 2.432Gbs of files.

That is almost everything installed on the system.

---

