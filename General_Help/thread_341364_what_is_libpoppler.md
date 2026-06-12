---
title: "what is libpoppler??"
date: 2007-01-18
forum: General Help
---

### Post by presbp on 2007-01-18
in the update list 3 libpoppler files showed up and I don't know what libpoppler is or if it is legal.. because I was adding the PLF repositories to the sources list to get the w32 codecs (I own Windows) and the updates popped up around then.  I took those repositories out of the list after the wget win32 failed but they are still there.

---

### Post by hikaricore on 2007-01-18
> **presbp said:**
> in the update list 3 libpoppler files showed up and I don't know what libpoppler is or if it is legal.. because I was adding the PLF repositories to the sources list to get the w32 codecs (I own Windows) and the updates popped up around then.  I took those repositories out of the list after the wget win32 failed but they are still there.

This wasn't that hard:

> [hikaricore@devistate:/media/devistate]$ cat /usr/share/doc/libpoppler1/README
This is poppler, a PDF rendering library.

Poppler is a fork of the xpdf PDF viewer developed by Derek Noonburg
of Glyph and Cog, LLC.  The purpose of forking xpdf is twofold.
First, we want to provide PDF rendering functionality as a shared
library, to centralize the maintenence effort.  Today a number of
applications incorporate the xpdf code base, and whenever a security
issue is discovered, all these applications exchange patches and put
out new releases.  In turn, all distributions must package and release
new version of these xpdf based viewers.  It's safe to say that
there's a lot of duplicated effort with the current situaion.  Even if
poppler in the short term introduces yet another xpdf derived code
base to the world, we hope that over time these applications will
adopt poppler.  After all, we only need one application to use poppler
to break even.

Second, we would like to move libpoppler forward in a number of areas
that doesn't fit within the goals of xpdf.  By design, xpdf depends on
very few libraries and runs a wide range of X based platforms.  This
is a strong feature and reasonable design goal.  However, with poppler
we would like to replace parts of xpdf that are now available as
standard components of modern Unix desktop environments.  One such
example is fontconfig, which solves the problem of matching and
locating fonts on the system, in a standardized and well understood
way.  Another example is cairo, which provides high quality 2D
rendering.  See the file TODO for a list of planned changes.

Please note that xpdf, and thus poppler, is licensed under the GPL,
not the LGPL.  Consequently, any application using poppler must also
be licensed under the GPL.  If you want to incorporate Xpdf based PDF
rendering in a closed source product, please contact Glyph & Cog
([www.glyphandcog.com](www.glyphandcog.com)) for commercial licensing options.

        Kristian Høgsberg, Feb. 27, 2005


See the README-XPDF for the original xpdf-3.00 README.
[hikaricore@devistate:/media/devistate]$ 

---

### Post by MikeDK on 2007-01-19
Hi!
Having troubles with installing lates libpoppler update please someone help me nor, the aptitude wont let it in

Best regards MikeDK

E: /var/cache/apt/archives/libpoppler1-glib_0.5.4-0ubuntu4.1_i386.deb: files list file for package `lsof' is missing final newline

---

### Post by Ramses de Norre on 2007-01-19
> **presbp said:**
> in the update list 3 libpoppler files showed up and I don't know what libpoppler is or if it is legal.. because I was adding the PLF repositories to the sources list to get the w32 codecs (I own Windows) and the updates popped up around then.  I took those repositories out of the list after the wget win32 failed but they are still there.

[Here](http://ubuntuforums.org/forumdisplay.php?f=13) you can find out everything about official updates. (So updates from main, I think edgy/dapper-updates isn't included however...)

@MikeDK: Try deleting the archive and redownloading it.

---

### Post by MikeDK on 2007-01-19
rgr that, just a single Question, should i use the Recommended updates in the update settings

no problems anymore just my lsof.list that was torn apart

Regards MikeDK

---

