---
title: "libqwebview.so missing for ubuntu"
date: 2015-08-17
forum: General Help
---

### Post by ashish-sharma-mw on 2015-08-17
Hi all,

I tried to install pyQt4, qt4-designer, and QtWebKit from synaptic package manager. All installed well. I could work upon pyqt and designer but I could not locate QWebView icon in qt4-designer. 
I looked at /usr/lib/i386-linux-gnu/qt4/plugins/designer but I could not find libqwebview.so there. Even I could not locate it anywhere on my pc.
Can anyone please guide me on how and where to look for this file for ubuntu, as I can see some links showing the file for debian.
Moreover, is there any other method to get this working?

Thanks in advance.

---

### Post by dino99 on 2015-08-17
you might look at libqtwebkit4

---

### Post by ashish-sharma-mw on 2015-08-17
Hi dino99,

I could locate libqtwebkit4 at following locations:

/usr/share/doc/libqtwebkit4
/usr/share/doc/libqtwebkit4/changelog.Debian.gz
/usr/share/doc/libqtwebkit4/copyright
/var/lib/dpkg/info/libqtwebkit4:i386.list
/var/lib/dpkg/info/libqtwebkit4:i386.md5sums
/var/lib/dpkg/info/libqtwebkit4:i386.postinst
/var/lib/dpkg/info/libqtwebkit4:i386.postrm
/var/lib/dpkg/info/libqtwebkit4:i386.shlibs

But  it does not really solved my issue. I wish to have webkit plugin for  qt4-designer so that I can incorporate it in my python based design. I  am using Ubuntu 14.04 LTS.

Please help.
Thanks

---

### Post by steeldriver on 2015-08-18
possible relevant discussion here? --> [https://bugs.launchpad.net/ubuntu/+source/qtwebkit-source/+bug/674367](https://bugs.launchpad.net/ubuntu/+source/qtwebkit-source/+bug/674367)

---

### Post by ashish-sharma-mw on 2015-08-22
steeldriver,

I've already seen that, it seems that this has been reported as a bug which persists in latest releases as well. Any comments?

---

