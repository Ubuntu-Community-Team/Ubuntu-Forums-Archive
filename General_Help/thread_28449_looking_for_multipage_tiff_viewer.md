---
title: "looking for multipage tiff viewer"
date: 2005-04-20
forum: General Help
---

### Post by burlap on 2005-04-20
Is there a good multipage tiff viewer? Gnome tools can only display the first page, gimp can do better but it is too big to be a viewer only.

I can convert tiff to pdf, but the solution I'm lookin for is an application to do it for me. 

Preferably gtk2 and in Ubuntu repositories...

---

### Post by Burgundavia on 2005-04-20
You might want to try evince, it is in hoary universe.

Corey

---

### Post by burlap on 2005-04-20
I have tried - evince also opens signle page (0.1.9 from Hoary repositories)...

---

### Post by joe_williams on 2005-04-20
try ghfaxviewer  ....It's in the universe repository

here's the discription:

The GNU HaliFAX Viewer
This is the GNU HaliFAX Viewer, a component of GNU HaliFAX which will
help you look at the TIFF g3/g4 fax files produced by HylaFAX

The GNU HaliFAX will be a complete free client package for HylaFAX
and maybe for other fax systems in the future.
It is intended to run on both the Win32 platform and the GNU system.

 - joe

---

### Post by Franko30 on 2005-08-23
Hi,

**ghfaxviewer**  worked great for me!

And together with Cups-PDF (and gtklp if you want a print options dialogue) it can convert multi page TIFFs to nice PDFs.

Or it can export the multipage TIFFs to a PS (postscript) file that Ghostview can handle. :-)

---

### Post by burlap on 2005-08-23
Halifax is ok, but evince 0.3.2 (not in Ubuntu Hoary, need to compile it yourself, but it's worth it) now supports multipage tiff documents.

---

### Post by amastronardi on 2005-08-23
[QUOTE=Franko30]Hi,

**ghfaxviewer**  worked great for me!

And together with Cups-PDF (and gtklp if you want a print options dialogue) it can convert multi page TIFFs to nice PDFs.

Or it can export the multipage TIFFs to a PS (postscript) file that Ghostview can handle. :-)[/QUOTE]

Do you know if it can export to png?

Cheers, Adrian.

---

### Post by lonetree on 2005-10-26
Installed the ghfaxviewer, but it did not create the launcher by itself. How to go about it?

---

