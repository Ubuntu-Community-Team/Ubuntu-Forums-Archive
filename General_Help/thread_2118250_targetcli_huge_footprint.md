---
title: "targetcli huge footprint"
date: 2013-02-20
forum: General Help
---

### Post by DiAx on 2013-02-20
I have a small home Ubuntu server with 12.04.2 LTS installed.
I wanted to try default iSCSI target based on LIO and typed
```
apt-get install targetcli
```
Proposed dependencies list was way too impressive:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  blt cmap-adobe-japan1 doc-base docutils-common docutils-doc fonts-liberation gettext ghostscript graphviz gs-cjk-resource gsfonts
  intltool-debian lacheck latex-beamer latex-xcolor libcdt4 libcgraph5 libcroco3 libcupsimage2 libfontenc1 libgd2-noxpm libgettextpo0
  libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libgraph4 libgs9 libgs9-common libgvc5 libgvpr1 libice6 libijs-0.35 libjasper1 libjbig2dec0
  libjpeg-turbo8 libjpeg8 libkpathsea5 liblcms1 liblcms2-2 libllvm3.0 libmail-sendmail-perl libpaper-utils libpaper1 libpathplan4
  libpoppler19 libsm6 libsys-hostname-long-perl libtiff4 libunistring0 libutempter0 libuuid-perl libx11-xcb1 libxaw7 libxcb-glx0
  libxcb-shape0 libxcomposite1 libxdamage1 libxfixes3 libxfont1 libxi6 libxinerama1 libxmu6 libxpm4 libxslt1.1 libxss1 libxt6 libxtst6 libxv1
  libxxf86dga1 libxxf86vm1 libyaml-tiny-perl lio-utils lmodern luatex pgf po-debconf preview-latex-style prosper ps2eps python-configobj
  python-configshell python-docutils python-epydoc python-imaging python-ipaddr python-lxml python-netifaces python-pkg-resources
  python-pygments python-roman python-rtslib python-simpleparse python-simpleparse-mxtexttools python-support python-tk tcl8.5 tex-common
  texlive-base texlive-binaries texlive-common texlive-doc-base texlive-extra-utils texlive-font-utils texlive-fonts-recommended
  texlive-fonts-recommended-doc texlive-generic-recommended texlive-latex-base texlive-latex-base-doc texlive-latex-extra
  texlive-latex-extra-doc texlive-latex-recommended texlive-latex-recommended-doc texlive-luatex texlive-pictures texlive-pictures-doc
  texlive-pstricks texlive-pstricks-doc tipa tk8.5 ttf-liberation x11-common x11-utils xbitmaps xfonts-encodings xfonts-utils xterm
Suggested packages:
  blt-demo dhelp dwww doc-central yelp khelpcenter4 rarian-compat gettext-doc ghostscript-cups ghostscript-x hpijs graphviz-doc
  fonts-ipafont-mincho fonts-ipafont-gothic ttf-arphic-ukai ttf-arphic-uming fonts-unfonts-core auctex libgd-tools libglide3
  libjasper-runtime liblcms-utils liblcms2-utils poppler-data libmail-box-perl pdf-viewer postscript-viewer texlive-lang-french
  ttf-linux-libertine epydoc-doc python-imaging-doc python-imaging-dbg python-lxml-dbg python-distribute python-distribute-doc
  ttf-bitstream-vera python-simpleparse-doc tix python-tk-dbg tclreadline debhelper perl-tk dvidvi fragmaster latexmk purifyeps xindy psutils
  t1utils texpower dot2tex mesa-utils xfonts-cyrillic
The following NEW packages will be installed:
  blt cmap-adobe-japan1 doc-base docutils-common docutils-doc fonts-liberation gettext ghostscript graphviz gs-cjk-resource gsfonts
  intltool-debian lacheck latex-beamer latex-xcolor libcdt4 libcgraph5 libcroco3 libcupsimage2 libfontenc1 libgd2-noxpm libgettextpo0
  libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libgraph4 libgs9 libgs9-common libgvc5 libgvpr1 libice6 libijs-0.35 libjasper1 libjbig2dec0
  libjpeg-turbo8 libjpeg8 libkpathsea5 liblcms1 liblcms2-2 libllvm3.0 libmail-sendmail-perl libpaper-utils libpaper1 libpathplan4
  libpoppler19 libsm6 libsys-hostname-long-perl libtiff4 libunistring0 libutempter0 libuuid-perl libx11-xcb1 libxaw7 libxcb-glx0
  libxcb-shape0 libxcomposite1 libxdamage1 libxfixes3 libxfont1 libxi6 libxinerama1 libxmu6 libxpm4 libxslt1.1 libxss1 libxt6 libxtst6 libxv1
  libxxf86dga1 libxxf86vm1 libyaml-tiny-perl lio-utils lmodern luatex pgf po-debconf preview-latex-style prosper ps2eps python-configobj
  python-configshell python-docutils python-epydoc python-imaging python-ipaddr python-lxml python-netifaces python-pkg-resources
  python-pygments python-roman python-rtslib python-simpleparse python-simpleparse-mxtexttools python-support python-tk targetcli tcl8.5
  tex-common texlive-base texlive-binaries texlive-common texlive-doc-base texlive-extra-utils texlive-font-utils texlive-fonts-recommended
  texlive-fonts-recommended-doc texlive-generic-recommended texlive-latex-base texlive-latex-base-doc texlive-latex-extra
  texlive-latex-extra-doc texlive-latex-recommended texlive-latex-recommended-doc texlive-luatex texlive-pictures texlive-pictures-doc
  texlive-pstricks texlive-pstricks-doc tipa tk8.5 ttf-liberation x11-common x11-utils xbitmaps xfonts-encodings xfonts-utils xterm
0 upgraded, 127 newly installed, 0 to remove and 21 not upgraded.
Need to get 468 MB/468 MB of archives.
After this operation, 800 MB of additional disk space will be used.

```
Installing 800MB of "stuff" including Tex, OpenGL just way too much for simple graphic-less server.

Any hints how to get iSCSI CLI without all above collateral damage?

---

### Post by Cheesemill on 2013-02-20
What does this give you...
```
sudo apt-get install --no-install-recommends targetcli
```

Although looking at the details of [targetcli]("http://packages.ubuntu.com/precise/targetcli") I'm not sure where these dependencies are coming from.

---

### Post by DiAx on 2013-02-20
Thanks a bunch, Cheesemill! Now it looks much more reasonable:
```

apt-get install --no-install-recommends targetcli
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following extra packages will be installed:
  lio-utils python-configobj python-configshell python-epydoc python-ipaddr python-netifaces python-rtslib python-simpleparse
  python-simpleparse-mxtexttools python-support
Suggested packages:
  epydoc-doc python-simpleparse-doc
Recommended packages:
  ghostscript python-tk python-docutils texlive-latex-base texlive-latex-extra texlive-latex-recommended texlive-fonts-recommended graphviz
The following NEW packages will be installed:
  lio-utils python-configobj python-configshell python-epydoc python-ipaddr python-netifaces python-rtslib python-simpleparse
  python-simpleparse-mxtexttools python-support targetcli
0 upgraded, 11 newly installed, 0 to remove and 21 not upgraded.
Need to get 1,362 kB/1,464 kB of archives.
After this operation, 6,552 kB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

And targetcli seems to work without OpenGL now :)

Lisati, thanks for make up... Lesson learnt.

---

