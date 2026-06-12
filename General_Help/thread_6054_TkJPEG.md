---
title: "Tk::JPEG"
date: 2004-11-24
forum: General Help
---

### Post by condorloco on 2004-11-24
Hi,

I switched to from Windows to Ubuntu a few days ago. It's great. The only thing I'm missing so far is a good comic book reader. I found 6reader, but it needs Tk:JPEG to compile. How can I install it? I found an instruction that told me to use "perl -MCPAN -e 'install Tk::JPEG'", but it won't install, it tells me it would only do it, if I force it. Can anybody help me? Ist there a package to install it with apt-get? I'm thankful for any help.

---

### Post by p!=f on 2004-11-24
Install libtk-img package
```

 * 19:32:46 * pef @ agonicus *
[~] > wajig show libtk-img
Package: libtk-img
Priority: optional
Section: universe/devel
Installed-Size: 1448
Maintainer: David N. Welton <davidw@debian.org>
Architecture: i386
Version: 1:1.3-11
Depends: libc6 (>= 2.3.2.ds1-4), libjpeg62, libpng12-0 (>= 1.2.5.0-4), libtiff4, libx11-6 | xlibs (>> 4.1.0), tcl8.4 (>= 8.4.5), tk8.4 (>= 8.4.5), zlib1g (>= 1:1.2.1)
Filename: pool/universe/libt/libtk-img/libtk-img_1.3-11_i386.deb
Size: 401854
MD5sum: f326d4bbfd621a36fd5b64556ab2a3a8
Description: Extended image format support for Tcl/Tk
 Img is a package to enhance Tk by providing support for various image
 formats such as XPM, GIF (transparency supported, but not LZW), PNG,
 JPEG, TIFF, and PostScript.
 .
 The libimg library can be loaded dynamically into Tcl/Tk scripts to
 provide the image handling functions.
 .
 Also included is the tkv script, which is basically a functional
 demo/proof-of-concept for Img.
Enhances: tk8.4
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```

---

### Post by condorloco on 2004-11-25
Thanks a lot, but it still doesn't work. It gives me the same error message as before:

$ perl 6reader.pl
Can't locate Tk/JPEG.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.4 /usr/local/share/perl/5.8.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at 6reader.pl line 19.
BEGIN failed--compilation aborted at 6reader.pl line 19.

And it doesn't matter, if I sudo or not.

---

### Post by p!=f on 2004-11-25
[QUOTE=condorloco]Thanks a lot, but it still doesn't work. It gives me the same error message as before:

$ perl 6reader.pl
Can't locate Tk/JPEG.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.4 /usr/local/share/perl/5.8.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at 6reader.pl line 19.
BEGIN failed--compilation aborted at 6reader.pl line 19.

And it doesn't matter, if I sudo or not.[/QUOTE]
You should be safe by installing the following package...
```

 * 16:54:45 * pef @ agonicus *
[~] > wajig show **libimage-info-perl**
Package: libimage-info-perl
Priority: optional
Section: universe/perl
Installed-Size: 196
Maintainer: Don Armstrong <don@donarmstrong.com>
Architecture: all
Version: 1.16-1
Depends: perl (>= 5.6.0-16), libio-string-perl, libimage-base-bundle-perl | libimage-xpm-perl, libimage-base-bundle-perl | libimage-xbm-perl, libxml-simple-perl
Filename: pool/universe/libi/libimage-info-perl/libimage-info-perl_1.16-1_all.deb
Size: 46066
MD5sum: cd2bd4dd6f363cab92814fc98720064b
Description: allows extraction of meta information from image files
 This Perl extension allows you to extract meta information from
 various types of image files.  In this release the following file
 formats are supported:
 .
   JPEG (plain JFIF and Exif)
   PNG
   GIF
   PBM/PGM/PPM
   SVG
   XBM/XPM
   BMP/DIB/RLE
   TIFF
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```

---

### Post by condorloco on 2004-11-25
Hi, I still get the same error message :-(

---

### Post by p!=f on 2004-11-25
Do you have perl-tk package installed?

---

### Post by condorloco on 2004-11-25
yes, and I really don't know what else to do.

---

### Post by condorloco on 2004-12-05
I'm sorry that I bump this, but does anybody have any idea? It still doesn't work. And the only thing I still miss in Ubuntu is a decent comic book viewer.

---

