---
title: "reading a CHM file"
date: 2022-03-07
forum: General Help
---

### Post by Skaperen on 2022-03-07
i was given a file in CHM format.  i found a couple CHM readers in a search (*chmsee* and *gnochm*) but neither of these are in the 18.04 LTM repository.  any suggestions?

---

### Post by #&amp;thj^% on 2022-03-07
I found kchmviewer a nice fit for myself.
> KchmViewer is a chm (MS HTML help file format) viewer, written in C++.
 Unlike most existing CHM viewers for Unix, it uses Trolltech Qt widget
 library, and does not depend on KDE or GNOME. However, it may be compiled
 with full KDE support, including KDE widgets and KIO/KHTML.
 .
 The main advantage of KchmViewer is non-English language support. Unlike
 others, KchmViewer in most cases correctly detects help file encoding,
 correctly shows tables of context of Russian, Korean, Chinese and Japanese
 help files, and correctly searches in non-English help files (search for
 MBCS languages - ja/ko/ch is still in progress).
Source: [https://launchpad.net/ubuntu/focal/+package/kchmviewer](https://launchpad.net/ubuntu/focal/+package/kchmviewer)

---

### Post by Skaperen on 2022-03-08
i'm on *Xfce4*, but i will give *kchmviewer* a try.

---

### Post by #&amp;thj^% on 2022-03-08
> **Skaperen said:**
> i'm on *Xfce4*, but i will give *kchmviewer* a try.
I as well on XFCE4
```
/usr/bin/kchmviewer
/usr/share/applications/kchmviewer.desktop
/usr/share/pixmaps/kchmviewer.png
```

Deps= chmlib, libzip. qt5-webengine.
Dang I forgot to add a useful link: [https://submain.com/ghostdoc/samples/PowerCollections/CHM/](https://submain.com/ghostdoc/samples/PowerCollections/CHM/)
I found it helped to have some basic knowledge.

---

### Post by Skaperen on 2022-03-08
the install froze up my system.  reboot and try again,  freeze, again.  it listed 70 packages to install.  looks like about 80 percent did install.  i gave up and autoremoved them.

*edit1*:

it looks like it tried to do an install of a package i already have.  maybe an issue with apt-get?

---

### Post by #&amp;thj^% on 2022-03-08
That's too bad.:( at least you tried.

---

### Post by Holger_Gehrke on 2022-03-08
xchm is in the repositories. Works fine as long as there's no JavaScript in the chm file.

Holger

---

### Post by #&amp;thj^% on 2022-03-08
A look at both. Not bad.

---

### Post by Skaperen on 2022-03-09
> **1fallen said:**
> A look at both. Not bad.

would have been nice to compare same page.

---

