---
title: "Package lcms2 was not found in the pkg-config search path"
date: 2019-11-16
forum: General Help
---

### Post by jgw on 2019-11-16
I was trying to make beautify which is a plugin for gimp 2.10.16  I got the error:Package lcms2 was not found in the pkg-config search path

I then did a search of lcms2 and got:
```

greg@gregdown:~$ locate lcms2
/snap/gnome-3-26-1604/97/usr/lib/x86_64-linux-gnu/liblcms2.so.2
/snap/gnome-3-26-1604/97/usr/lib/x86_64-linux-gnu/liblcms2.so.2.0.6
/snap/gnome-3-26-1604/97/usr/share/doc/liblcms2-2
/snap/gnome-3-26-1604/97/usr/share/doc/liblcms2-2/changelog.Debian.gz
/snap/gnome-3-26-1604/97/usr/share/doc/liblcms2-2/copyright
/snap/gnome-3-26-1604/98/usr/lib/x86_64-linux-gnu/liblcms2.so.2
/snap/gnome-3-26-1604/98/usr/lib/x86_64-linux-gnu/liblcms2.so.2.0.6
/snap/gnome-3-26-1604/98/usr/share/doc/liblcms2-2
/snap/gnome-3-26-1604/98/usr/share/doc/liblcms2-2/changelog.Debian.gz
/snap/gnome-3-26-1604/98/usr/share/doc/liblcms2-2/copyright
/snap/gnome-3-28-1804/110/usr/lib/x86_64-linux-gnu/liblcms2.so.2
/snap/gnome-3-28-1804/110/usr/lib/x86_64-linux-gnu/liblcms2.so.2.0.8
/snap/gnome-3-28-1804/110/usr/share/doc/liblcms2-2
/snap/gnome-3-28-1804/110/usr/share/doc/liblcms2-2/changelog.Debian.gz
/snap/gnome-3-28-1804/110/usr/share/doc/liblcms2-2/copyright
/snap/gnome-3-28-1804/91/usr/lib/x86_64-linux-gnu/liblcms2.so.2
/snap/gnome-3-28-1804/91/usr/lib/x86_64-linux-gnu/liblcms2.so.2.0.8
/snap/gnome-3-28-1804/91/usr/share/doc/liblcms2-2
/snap/gnome-3-28-1804/91/usr/share/doc/liblcms2-2/changelog.Debian.gz
/snap/gnome-3-28-1804/91/usr/share/doc/liblcms2-2/copyright
/snap/guvcview/81/usr/lib/x86_64-linux-gnu/liblcms2.so.2
/snap/guvcview/81/usr/lib/x86_64-linux-gnu/liblcms2.so.2.0.8
/snap/guvcview/81/usr/share/doc/liblcms2-2
/snap/guvcview/81/usr/share/doc/liblcms2-2/changelog.Debian.gz
/snap/guvcview/81/usr/share/doc/liblcms2-2/copyright
/usr/lib/x86_64-linux-gnu/liblcms2.so.2
/usr/lib/x86_64-linux-gnu/liblcms2.so.2.0.8
/usr/share/doc/liblcms2-2
/usr/share/doc/liblcms2-utils
/usr/share/doc/liblcms2-2/changelog.Debian.gz
/usr/share/doc/liblcms2-2/copyright
/usr/share/doc/liblcms2-utils/changelog.Debian.gz
/usr/share/doc/liblcms2-utils/copyright
/var/lib/dpkg/info/liblcms2-2:amd64.list
/var/lib/dpkg/info/liblcms2-2:amd64.md5sums
/var/lib/dpkg/info/liblcms2-2:amd64.shlibs
/var/lib/dpkg/info/liblcms2-2:amd64.symbols
/var/lib/dpkg/info/liblcms2-2:amd64.triggers
/var/lib/dpkg/info/liblcms2-utils.list
/var/lib/dpkg/info/liblcms2-utils.md5sums
greg@gregdown:~$ 

```

I am assuming I am going to have to add something to pkg-config search path but figured I had better get some advise instead of charging ahead.

Thank you........................

---

### Post by jgw on 2019-11-17
bump

---

### Post by jgw on 2019-11-23
I solved this one.  Seems that I needed to install the .dev file for lcms2.  I did this with synaptic.  I then tried to make beautify again and, this time, it worked.  I then ran make userinstall (whilst in the beautify folder) and it installed it into gimp (that worked too because it now appears in gimp).  

So, I will mark this one as solved...............

---

