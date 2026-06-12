---
title: "Xenial 16.04 evince seemingly not honoring custom dpi"
date: 2016-07-09
forum: General Help
---

### Post by Nutria on 2016-07-09
Hi,

System: Xubuntu 16.04 freshly installed on a system that had been running Xubuntu 14.04.

Because my monitor is 304 dpi, a custom dpi of 96 is required.  This has been the case ever since I bought the monitor while using 12.04.

Whatever version of evince that was in 14.04 displayed PDF files correctly, but the same PDF files display **huge** in 16.04.  **xpdf displays them correctly**, so it's not the data.  evince also enlarges .ps files.  (I just noticed that the ancient "gv" also prints them oversized.)

Any thoughts (besides on the content of the pdf)?

```
$ apt-show-versions evince
evince:amd64/xenial 3.18.2-1ubuntu4 uptodate
evince:i386 not installed

$ apt-show-versions ttf-mscorefonts-installer
ttf-mscorefonts-installer:all/xenial 3.4+nmu1ubuntu2 uptodate

$ pdffonts william_craig.pdf
name                                 type              encoding         emb sub uni object ID
------------------------------------ ----------------- ---------------- --- --- --- ---------
XMWNBC+Times-Roman                   TrueType          MacRoman         yes yes no       8  0
RFHWYA+Times-Italic                  TrueType          MacRoman         yes yes no       7  0
```

It happens on all PDF and PS files, even those with embedded fonts.  Here's an example:

[IMG]https://s32.postimg.org/xckn06zth/evince_huge_fonts.png[/IMG]

Thanks.

---

