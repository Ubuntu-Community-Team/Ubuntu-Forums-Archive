---
title: "How do I avoid installing &quot;Extra&quot; packages?"
date: 2007-06-17
forum: General Help
---

### Post by navneeth on 2007-06-17
One of the dependencies for a program I'm installing from source is libqt4-dev. When I try to install this from synaptic, I get this message.

```
The following extra packages will be installed:
  comerr-dev libaudio-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev
  libglib2.0-dev libice-dev libjpeg62-dev libkadm55 libkrb5-dev liblcms1-dev
  libmng-dev libpng12-dev libpq-dev libqt4-core libqt4-gui libqt4-qt3support
  libqt4-sql libsm-dev libsqlite0 libsqlite0-dev libssl-dev libxcursor-dev
  libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxmu-dev
  libxmu-headers libxrandr-dev libxrender-dev libxt-dev x11proto-fixes-dev
  x11proto-randr-dev x11proto-render-dev x11proto-xext-dev
  x11proto-xinerama-dev zlib1g-dev
Suggested packages:
  libglib2.0-doc krb5-doc postgresql-doc-8.2 qt4-doc sqlite-doc
Recommended packages:
  qt4-dev-tools qt4-qtconfig
The following NEW packages will be installed:
  comerr-dev libaudio-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev
  libglib2.0-dev libice-dev libjpeg62-dev libkadm55 libkrb5-dev liblcms1-dev
  libmng-dev libpng12-dev libpq-dev libqt4-core libqt4-dev libqt4-gui
  libqt4-qt3support libqt4-sql libsm-dev libsqlite0 libsqlite0-dev libssl-dev
  libxcursor-dev libxext-dev libxfixes-dev libxft-dev libxi-dev
  libxinerama-dev libxmu-dev libxmu-headers libxrandr-dev libxrender-dev
  libxt-dev x11proto-fixes-dev x11proto-randr-dev x11proto-render-dev
  x11proto-xext-dev x11proto-xinerama-dev zlib1g-dev
0 upgraded, 40 newly installed, 0 to remove and 0 not upgraded.
Need to get 20.0MB of archives.
After unpacking 66.3MB of additional disk space will be used.

```

Well, I really don't want to install all that. Only the libqt4 and other files which are essential for its functioning. How do I do that? Going through apt-get's man page didn't help much. 

Thanks.

---

### Post by navneeth on 2007-06-17
*Bump*

---

### Post by mikewhatever on 2007-06-17
A quick look [here]("http://packages.ubuntu.com/feisty/libdevel/libqt4-dev") shows that the packages it wants to install are required as dependencies. Looks like nothing you can do. Suggested and recommended ones are not to be installed, so that's a good point.

---

### Post by navneeth on 2007-06-17
So do I just install it with the file linked at the bottom of the page? Seems to be 1/5th the download.

---

### Post by zvacet on 2007-06-17
Look at the link **mikewhatever** posted to you and you will see that all of packages (exept two)are dependencies.You have to install them if you want your package to be installed.

---

