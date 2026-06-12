---
title: "Printing PDF documents"
date: 2013-11-06
forum: General Help
---

### Post by arno48 on 2013-11-06
```
                         [COLOR=#000000][FONT=Verdana][SIZE=2]*Hello,*[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana][SIZE=2]*I cannot print PDF documents any longer,*[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana][SIZE=2]*They are opened by DOCUMENT VIEWER which doesn't offer PRINT option.*[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana][SIZE=2]*Thanks *[/SIZE][/FONT][/COLOR] 
  
```

---

### Post by ajgreeny on 2013-11-06
Does Ctrl+P work?  That is the default keyboard print command shortcut for most applications.  Do you have a menubar showing, or is that totally missing as well?

---

### Post by arno48 on 2013-11-06
Yes, Ctrl+P works, Thanks a lot.
Menubar is missing. I noticed it recently, after having downloaded Ubuntu 13.10.

---

### Post by TheFu on 2013-11-06
A quick workaround is opening a terminal and running this:
$ lp filename.pdf
Might need to load that tool.
Plus there are other PDF viewers/editors - xournal and evince ... are just a start. Sadly, they all suck in different ways.

---

### Post by SeijiSensei on 2013-11-06
> **TheFu said:**
> Plus there are other PDF viewers/editors - xournal and evince ... are just a start. Sadly, they all suck in different ways.

I like Okular myself, particularly for its "jocular" settings page, the one that allows you to choose to enforce digital-rights-management features upon yourself for the pure joy of it.

---

### Post by tgalati4 on 2013-11-07
View-->Toolbar

Edit-->Toolbar (add the printer icon to the toolbar)

---

### Post by ajgreeny on 2013-11-07
> **tgalati4 said:**
> View-->Toolbar

Edit-->Toolbar (add the printer icon to the toolbar)

With no menubar visible you will need to hold Alt+V to see the View menu, and there you may also be able to make the menubar visible again, though in my version on 12.04 there is no way to remove or add back the menubar, as far as I can see.

---

### Post by arno48 on 2013-11-08
I installed evince and it's working fine.
Thank you

---

### Post by arno48 on 2013-11-08
View and Edit are  menus of Firefox menubar I suppose.
But when Firefox is not running I cannot use this bar.
Thanks for your help.

---

### Post by TheFu on 2013-11-08
> **SeijiSensei said:**
> I like Okular myself, 

The dependencies stopped me from even trying Okular.
```
$ sudo apt-get install okular
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  docbook-xsl gstreamer0.10-alsa icoutils kate-data katepart kde-runtime
  kde-runtime-data kdelibs-bin kdelibs5-data kdelibs5-plugins kdoctools
  kubuntu-debug-installer libattica0.3 libcanberra-pulse libclucene0ldbl
  libdbusmenu-qt2 libdlrestrictions1 libkatepartinterfaces4 libkcmutils4
  libkde3support4 libkdeclarative5 libkdecore5 libkdesu5 libkdeui5
  libkdewebkit5 libkdnssd4 libkemoticons4 libkfile4 libkhtml5 libkidletime4
  libkio5 libkjsapi4 libkjsembed4 libkmediaplayer4 libknewstuff3-4
  libknotifyconfig4 libkntlm4 libkparts4 libkprintutils4 libkpty4
  libkrosscore4 libktexteditor4 libnepomuk4 libnepomukdatamanagement4
  libnepomukquery4a libnepomuksync4 libnepomukutils4 libnl-route-3-200
  libntrack-qt4-1 libntrack0 libokularcore1abi1 libphonon4 libplasma3
  libpolkit-qt-1-1 libpoppler-qt4-3 libqapt-runtime libqapt1 libqca2
  libqimageblitz4 libqt4-opengl libqt4-qt3support libsolid4 libsoprano4
  libstreamanalyzer0 libstreams0 libthreadweaver4 libupower-glib1 libvirtodbc0
  ntrack-module-libnl-0 odbcinst odbcinst1debian2 oxygen-icon-theme phonon
  phonon-backend-gstreamer plasma-scriptengine-javascript pm-utils qapt-batch
  shared-desktop-ontologies soprano-daemon upower vbetool virtuoso-minimal
  virtuoso-opensource-6.1-bin virtuoso-opensource-6.1-common
Suggested packages:
  docbook-xsl-doc-html docbook-xsl-doc-pdf docbook-xsl-doc-text
  docbook-xsl-doc libsaxon-java libxalan2-java libxslthl-java
  docbook-xsl-saxon fop xalan dbtoepub libterm-readline-gnu-perl
  libterm-readline-perl-perl djvulibre-bin finger hspell
  libqca2-plugin-cyrus-sasl libqca2-plugin-gnupg libqca2-plugin-ossl
  okular-extra-backends texlive-binaries unrar poppler-data jovie
  phonon-backend-vlc phonon-backend-xine phonon-backend-mplayer
  gstreamer0.10-plugins-ugly cpufrequtils wireless-tools ethtool radeontool
The following NEW packages will be installed:
  docbook-xsl gstreamer0.10-alsa icoutils kate-data katepart kde-runtime
  kde-runtime-data kdelibs-bin kdelibs5-data kdelibs5-plugins kdoctools
  kubuntu-debug-installer libattica0.3 libcanberra-pulse libclucene0ldbl
  libdbusmenu-qt2 libdlrestrictions1 libkatepartinterfaces4 libkcmutils4
  libkde3support4 libkdeclarative5 libkdecore5 libkdesu5 libkdeui5
  libkdewebkit5 libkdnssd4 libkemoticons4 libkfile4 libkhtml5 libkidletime4
  libkio5 libkjsapi4 libkjsembed4 libkmediaplayer4 libknewstuff3-4
  libknotifyconfig4 libkntlm4 libkparts4 libkprintutils4 libkpty4
  libkrosscore4 libktexteditor4 libnepomuk4 libnepomukdatamanagement4
  libnepomukquery4a libnepomuksync4 libnepomukutils4 libnl-route-3-200
  libntrack-qt4-1 libntrack0 libokularcore1abi1 libphonon4 libplasma3
  libpolkit-qt-1-1 libpoppler-qt4-3 libqapt-runtime libqapt1 libqca2
  libqimageblitz4 libqt4-opengl libqt4-qt3support libsolid4 libsoprano4
  libstreamanalyzer0 libstreams0 libthreadweaver4 libupower-glib1 libvirtodbc0
  ntrack-module-libnl-0 odbcinst odbcinst1debian2 okular oxygen-icon-theme
  phonon phonon-backend-gstreamer plasma-scriptengine-javascript pm-utils
  qapt-batch shared-desktop-ontologies soprano-daemon upower vbetool
  virtuoso-minimal virtuoso-opensource-6.1-bin virtuoso-opensource-6.1-common
0 upgraded, 85 newly installed, 0 to remove and 17 not upgraded.
Need to get 51.7 MB of archives.
After this operation, 156 MB of additional disk space will be used.
Do you want to continue [Y/n]? n
```

KDE-based apps are a non-starter for me for this reason. I need to be vigilant to avoid the bloat and extra dependencies.
My loss, I'm certain.

---

### Post by arno48 on 2013-11-08
When Firefox is not running I have neither menubar visible nor Alt+V working.
Am I wright?

---

### Post by tgalati4 on 2013-11-08
The print icon can be added to evince by going to Edit-->Toolbar (scroll down until you find the print icon).  In Firefox, you go to Preferences-->Toolbar Layout-->Select print icon.  And you are correct, unless the toolbar is showing, you will not see the icons.

---

### Post by arno48 on 2013-11-08
Print Icon has been installed in Firefox bar.
After having installed  evince, a HELP botton appears under DOCUMENT VIEWER.
Clicking this button Print Command becomes available.
Thanks a lot for your help.

[FONT=Arial, sans-serif][SIZE=3]*[COLOR=#000000][SIZE=2][/SIZE][/COLOR]*[/SIZE][/FONT]

---

### Post by ajgreeny on 2013-11-08
Now I'm confused!  What has any of this got to do with Firefox?

You originally said documents could not be printed from Document Viewer, then said you have now installed evince and everything is now OK.

As far as I'm aware Document Viewer is evince, so did you simply re-install it, or was your original Document Viewer something else, not evince?

---

### Post by arno48 on 2013-11-09
I agree, it's not quite clear.
I started this thread because, after having installed Ubuntu 13.10, when I opened PDF files they were opened with Document Viewer by default.
As Document Viewer does not show any Menubar I was not able to Print PDF files any longer.
Yesterday I noticed  a HELP button appearing , just below DOCUMENT VIEWER wording in the high left corner.
Clicking this button Print Command becomes available.

---

### Post by ajgreeny on 2013-11-09
OK, perhaps this is the silly global menus problem, one of the many things about unity that I could not get on with, hence my move to Xubuntu.

---

