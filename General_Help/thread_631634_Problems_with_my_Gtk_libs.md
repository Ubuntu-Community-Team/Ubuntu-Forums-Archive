---
title: "Problems with my Gtk libs"
date: 2007-12-04
forum: General Help
---

### Post by anto91 on 2007-12-04
When i try to start any application using gtk i get the following error
```

/usr/lib/firefox/firefox-bin: symbol lookup error: /usr/lib/libgtk-x11-2.0.so.0: undefined symbol: gdk_threads_add_idle

```

```

anto@anto-desktop:~/Desktop/Programs/monodevelop-version-0.17$ locate libgtk
/usr/lib/libgtkspell.so.0
/usr/lib/libgtk-x11-2.0.so.0
/usr/lib/libgtkhtml-2.so.0.0.0
/usr/lib/mono/gtk-sharp-2.0/libgtksharpglue-2.so
/usr/lib/libgtkhtml-3.8.so.15
/usr/lib/libgtk-x11-2.0.so.0.1200.0
/usr/lib/libgtkspell.so.0.0.0
/usr/lib/libgtksourceview-1.0.so.0
/usr/lib/firefox/libgtkxtbin.so
/usr/lib/firefox/libgtkembedmoz.so
/usr/lib/libgtksourceview-2.0.so.0.0.0
/usr/lib/libgtkhtml-2.so.0
/usr/lib/libgtkhtml-3.8.so.15.3.9
/usr/lib/gtk-2.0/2.10.0/immodule-files.d/libgtk2.0-0.immodules
/usr/lib/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
/usr/lib/libgtk2.0-0
/usr/lib/libgtk2.0-0/update-gdkpixbuf-loaders
/usr/lib/libgtk2.0-0/gtk-query-immodules-2.0
/usr/lib/libgtk2.0-0/gdk-pixbuf-query-loaders
/usr/lib/libgtk2.0-0/update-gtk-immodules
/usr/lib/libgtk2.0-0/gtk-update-icon-cache
/usr/lib/libgtksourceview-1.0.so.0.0.0
/usr/lib/libgtksourceview-2.0.so.0
/usr/share/doc/libgtk2.0-common
/usr/share/doc/libgtk2.0-common/NEWS.gz
/usr/share/doc/libgtk2.0-common/copyright
/usr/share/doc/libgtk2.0-common/NEWS.pre-1-0.gz
/usr/share/doc/libgtk2.0-common/changelog.gz
/usr/share/doc/libgtk2.0-common/README.gz
/usr/share/doc/libgtk2.0-common/changelog.Debian.gz
/usr/share/doc/libgtk2.0-cil
/usr/share/doc/libgtkhtml2-0
/usr/share/doc/libgtkhtml2-0/NEWS.gz
/usr/share/doc/libgtkhtml2-0/copyright
/usr/share/doc/libgtkhtml2-0/AUTHORS
/usr/share/doc/libgtkhtml2-0/changelog.gz
/usr/share/doc/libgtkhtml2-0/changelog.Debian.gz
/usr/share/doc/libgtksourceview2.0-common
/usr/share/doc/libgtksourceview2.0-common/NEWS.gz
/usr/share/doc/libgtksourceview2.0-common/copyright
/usr/share/doc/libgtksourceview2.0-common/AUTHORS
/usr/share/doc/libgtksourceview2.0-common/buildinfo.gz
/usr/share/doc/libgtksourceview2.0-common/changelog.gz
/usr/share/doc/libgtksourceview2.0-common/README
/usr/share/doc/libgtksourceview2.0-common/changelog.Debian.gz
/usr/share/doc/libgtkhtml3.8-15
/usr/share/doc/libgtkhtml3.8-15/NEWS.gz
/usr/share/doc/libgtkhtml3.8-15/copyright
/usr/share/doc/libgtkhtml3.8-15/AUTHORS
/usr/share/doc/libgtkhtml3.8-15/changelog.gz
/usr/share/doc/libgtkhtml3.8-15/README
/usr/share/doc/libgtkhtml3.8-15/BUGS
/usr/share/doc/libgtkhtml3.8-15/changelog.Debian.gz
/usr/share/doc/libgtkhtml3.8-15/TODO
/usr/share/doc/libgtk2.0-bin
/usr/share/doc/libgtkhtml2.0-cil
/usr/share/doc/libgtkhtml2.0-cil/copyright
/usr/share/doc/libgtkhtml2.0-cil/changelog.Debian.gz
/usr/share/doc/libgtkspell0
/usr/share/doc/libgtkspell0/copyright
/usr/share/doc/libgtkspell0/changelog.gz
/usr/share/doc/libgtkspell0/changelog.Debian.gz
/usr/share/doc/libgtksourceview1.0-0
/usr/share/doc/libgtksourceview1.0-0/NEWS.gz
/usr/share/doc/libgtksourceview1.0-0/copyright
/usr/share/doc/libgtksourceview1.0-0/AUTHORS
/usr/share/doc/libgtksourceview1.0-0/changelog.gz
/usr/share/doc/libgtksourceview1.0-0/README
/usr/share/doc/libgtksourceview1.0-0/changelog.Debian.gz
/usr/share/doc/libgtksourceview1.0-0/TODO
/usr/share/doc/libgtksourceview2.0-0
/usr/share/doc/libgtksourceview2.0-0/NEWS.gz
/usr/share/doc/libgtksourceview2.0-0/copyright
/usr/share/doc/libgtksourceview2.0-0/AUTHORS
/usr/share/doc/libgtksourceview2.0-0/changelog.gz
/usr/share/doc/libgtksourceview2.0-0/README
/usr/share/doc/libgtksourceview2.0-0/changelog.Debian.gz
/usr/share/doc/libgtk2.0-0
/usr/share/doc/libgtksourceview-common
/usr/share/doc/libgtksourceview-common/NEWS.gz
/usr/share/doc/libgtksourceview-common/copyright
/usr/share/doc/libgtksourceview-common/AUTHORS
/usr/share/doc/libgtksourceview-common/buildinfo.gz
/usr/share/doc/libgtksourceview-common/changelog.gz
/usr/share/doc/libgtksourceview-common/README
/usr/share/doc/libgtksourceview-common/changelog.Debian.gz
/usr/share/doc/libgtksourceview-common/TODO
/var/cache/apt/archives/libgtksourceview2.0-common_2.0.1-0ubuntu1_all.deb
/var/cache/apt/archives/libgtksourceview2.0-0_2.0.1-0ubuntu1_i386.deb
/var/lib/dpkg/info/libgtkhtml3.8-15.shlibs
/var/lib/dpkg/info/libgtkhtml3.8-15.postinst
/var/lib/dpkg/info/libgtkspell0.postrm
/var/lib/dpkg/info/libgtk2.0-cil.md5sums
/var/lib/dpkg/info/libgtk2.0-cil.list
/var/lib/dpkg/info/libgtk2.0-0.list
/var/lib/dpkg/info/libgtksourceview2.0-0.postrm
/var/lib/dpkg/info/libgtk2.0-cil.clilibs
/var/lib/dpkg/info/libgtkspell0.md5sums
/var/lib/dpkg/info/libgtkspell0.postinst
/var/lib/dpkg/info/libgtksourceview2.0-common.md5sums
/var/lib/dpkg/info/libgtksourceview1.0-0.postrm
/var/lib/dpkg/info/libgtkhtml2-0.shlibs
/var/lib/dpkg/info/libgtkhtml2-0.postinst
/var/lib/dpkg/info/libgtksourceview2.0-0.list
/var/lib/dpkg/info/libgtksourceview2.0-0.shlibs
/var/lib/dpkg/info/libgtk2.0-common.list
/var/lib/dpkg/info/libgtkhtml3.8-15.md5sums
/var/lib/dpkg/info/libgtksourceview-common.md5sums
/var/lib/dpkg/info/libgtk2.0-bin.list
/var/lib/dpkg/info/libgtksourceview2.0-0.md5sums
/var/lib/dpkg/info/libgtk2.0-bin.md5sums
/var/lib/dpkg/info/libgtksourceview1.0-0.shlibs
/var/lib/dpkg/info/libgtk2.0-0.shlibs
/var/lib/dpkg/info/libgtk2.0-cil.preinst
/var/lib/dpkg/info/libgtk2.0-common.preinst
/var/lib/dpkg/info/libgtkhtml2-0.md5sums
/var/lib/dpkg/info/libgtkhtml2-0.list
/var/lib/dpkg/info/libgtk2.0-0.postrm
/var/lib/dpkg/info/libgtk2.0-0.conffiles
/var/lib/dpkg/info/libgtkhtml2.0-cil.md5sums
/var/lib/dpkg/info/libgtk2.0-common.md5sums
/var/lib/dpkg/info/libgtksourceview1.0-0.list
/var/lib/dpkg/info/libgtkhtml3.8-15.postrm
/var/lib/dpkg/info/libgtkhtml2-0.postrm
/var/lib/dpkg/info/libgtksourceview-common.list
/var/lib/dpkg/info/libgtkhtml2.0-cil.list
/var/lib/dpkg/info/libgtksourceview2.0-0.postinst
/var/lib/dpkg/info/libgtksourceview2.0-common.list
/var/lib/dpkg/info/libgtk2.0-0.md5sums
/var/lib/dpkg/info/libgtk2.0-0.postinst
/var/lib/dpkg/info/libgtkspell0.list
/var/lib/dpkg/info/libgtkhtml2.0-cil.clilibs
/var/lib/dpkg/info/libgtksourceview1.0-0.md5sums
/var/lib/dpkg/info/libgtksourceview1.0-0.postinst
/var/lib/dpkg/info/libgtkhtml3.8-15.list
/var/lib/dpkg/info/libgtkspell0.shlibs

```

---

### Post by anto91 on 2007-12-05
Common somone ?

---

