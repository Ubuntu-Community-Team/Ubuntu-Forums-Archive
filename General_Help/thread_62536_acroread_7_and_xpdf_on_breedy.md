---
title: "acroread 7 and xpdf on breedy"
date: 2005-09-05
forum: General Help
---

### Post by lizhao on 2005-09-05
1. My acoread always crash after the splash screen popups, without any error reported
My config:
Ubuntu 5.10 colony 3
acroread 7.0-0.9 or 7.0-0.9~5.04ubp2 or tar.gz downloaded from acrobat

how to resolve it? ](*,) 

thanks in advance


2. When starting xpdf, a warning is reported:
Warning: Cannot convert string "-*-times-medium-r-normal--16-*-*-*-*-*-iso8859-1" to type FontStruct

What's it, and how to amend?

My xpdf can NOT display bookmark panel, no idea about why

---

### Post by Manny C on 2005-09-05
[QUOTE=lizhao]1. My acoread always crash after the splash screen popups, without any error reported
My config:
Ubuntu 5.10 colony 3
acroread 7.0-0.9 or 7.0-0.9~5.04ubp2 or tar.gz downloaded from acrobat

how to resolve it? ](*,) [/QUOTE]

Post this in the Breezy Badger Mailing List not in the Hoary List. Colony 3 is a Breezy Badger pre-release.

> 2. When starting xpdf, a warning is reported:
Warning: Cannot convert string "-*-times-medium-r-normal--16-*-*-*-*-*-iso8859-1" to type FontStruct

What's it, and how to amend?

My xpdf can NOT display bookmark panel, no idea about why

Xpdf does display bookmarks. Simply click on the little box on the lower left hand corner (above the toolbar) and move across. Regarding the warning, you should do the following:

1) Install the gsfonts-x11 package. 

2) Open you favourite text editor and then create a .xpdfrc file in ~/ directory. The contents should be as follows:
```

displayFontT1 Times-Roman           /usr/X11R6/lib/X11/fonts/Type1/n021003l.pfb
displayFontT1 Times-Italic          /usr/X11R6/lib/X11/fonts/Type1/n021023l.pfb
displayFontT1 Times-Bold            /usr/X11R6/lib/X11/fonts/Type1/n021004l.pfb
displayFontT1 Times-BoldItalic      /usr/X11R6/lib/X11/fonts/Type1/n021024l.pfb
displayFontT1 Helvetica             /usr/X11R6/lib/X11/fonts/Type1/n019003l.pfb
displayFontT1 Helvetica-Oblique     /usr/X11R6/lib/X11/fonts/Type1/n019023l.pfb
displayFontT1 Helvetica-Bold        /usr/X11R6/lib/X11/fonts/Type1/n019004l.pfb
displayFontT1 Helvetica-BoldOblique /usr/X11R6/lib/X11/fonts/Type1/n019024l.pfb
displayFontT1 Courier               /usr/X11R6/lib/X11/fonts/Type1/n022003l.pfb
displayFontT1 Courier-Oblique       /usr/X11R6/lib/X11/fonts/Type1/n022023l.pfb
displayFontT1 Courier-Bold          /usr/X11R6/lib/X11/fonts/Type1/n022004l.pfb
displayFontT1 Courier-BoldOblique   /usr/X11R6/lib/X11/fonts/Type1/n022024l.pfb
displayFontT1 Symbol                /usr/X11R6/lib/X11/fonts/Type1/s050000l.pfb
displayFontT1 ZapfDingbats          /usr/X11R6/lib/X11/fonts/Type1/d050000l.pfb

``` 

3) Then at a bash shell:
```
xrdb -merge .xpdfrc
``` 

That should fix it. If it doesn't you should be asking this question in the Breezy Development mailing list.

---

