---
title: "RAW thumbnails (photo thumbails)"
date: 2012-11-10
forum: General Help
---

### Post by bach on 2012-11-10
I no longer have RAW (NEF, in my case) thumbnails after upgrading to Ubuntu 12.10. I use both Unity and Gnome 3. In previous versions of Ubuntu I solved this by editing 

/usr/share/thumbnailers/raw.thumbnailer

and adding the following to this file: 

[Thumbnailer Entry]
Exec=/usr/bin/gnome-raw-thumbnailer -s %s %u %o
MimeType=image/x-3fr;image/x-adobe-dng;image/x-arw;image/x-bay;image/x-canon-cr2;image/x-canon-crw;image/x-cap;image/x-cr2;image/x-crw;image/x-dcr;image/x-dcraw;image/x-dcs;image/x-dng;image/x-drf;image/x-eip;image/x-erf;image/x-fff;image/x-fuji-raf;image/x-iiq;image/x-k25;image/x-kdc;image/x-mef;image/x-minolta-mrw;image/x-mos;image/x-mrw;image/x-nef;image/x-nikon-nef;image/x-nrw;image/x-olympus-orf;image/x-orf;image/x-panasonic-raw;image/x-pef;image/x-pentax-pef;image/x-ptx;image/x-pxn;image/x-r3d;image/x-raf;image/x-raw;image/x-rw2;image/x-rwl;image/x-rwz;image/x-sigma-x3f;image/x-sony-arw;image/x-sony-sr2;image/x-sony-srf;image/x-sr2;image/x-srf;image/x-x3f;

This solution, however, no longer works for me. 

Any suggestions?

---

### Post by HiImTye on 2012-11-10
try
```
sudo apt-get install gnome-raw-thumbnailer
```

---

### Post by bach on 2012-11-10
> **HiImTye said:**
> try
```
sudo apt-get install gnome-raw-thumbnailer
```

It is already installed. I have no RAW thumbnails even with the package installed.

---

### Post by HiImTye on 2012-11-10
```
locate raw-thumbnailer
```
might point to its' location

---

### Post by bach on 2012-11-10
> **HiImTye said:**
> ```
locate raw-thumbnailer
```
might point to its' location

Here is what I have. 

cribari@darwin2:~$ locate raw-thumbnailer
/usr/bin/gnome-raw-thumbnailer
/usr/lib/x86_64-linux-gnu/tumbler-1/plugins/tumbler-raw-thumbnailer.so
/usr/share/doc/gnome-raw-thumbnailer
/usr/share/doc/gnome-raw-thumbnailer/AUTHORS
/usr/share/doc/gnome-raw-thumbnailer/README
/usr/share/doc/gnome-raw-thumbnailer/TODO
/usr/share/doc/gnome-raw-thumbnailer/changelog.Debian.gz
/usr/share/doc/gnome-raw-thumbnailer/copyright
/usr/share/gconf/schemas/gnome-raw-thumbnailer.schemas
/usr/share/mime/packages/gnome-raw-thumbnailer.xml
/var/lib/dpkg/info/gnome-raw-thumbnailer.list
/var/lib/dpkg/info/gnome-raw-thumbnailer.md5sums
/var/lib/dpkg/info/gnome-raw-thumbnailer.postinst
/var/lib/dpkg/info/gnome-raw-thumbnailer.postrm
/var/lib/dpkg/info/gnome-raw-thumbnailer.prerm

---

### Post by bach on 2012-11-10
It is working now. Thanks!

---

