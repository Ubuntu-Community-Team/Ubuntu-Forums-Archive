---
title: "printing pdf files fails"
date: 2007-11-05
forum: General Help
---

### Post by barna on 2007-11-05
Hi, I tried to print a pdf file from kpdf, but nothing appears on the printer, and no error message/warning is displayed. Then I tried to convert it to postscript... it complained about missing fonts, so I installed practically all fonts available in the repositories. Then I tried to convert it again:

```

gs -dBATCH -dNOPAUSE -sDEVICE=pswrite -sOutputFile=minitico.ps minitico.pdf                                                        GPL Ghostscript SVN PRE-RELEASE 8.61 (2007-08-02)
Copyright (C) 2007 Artifex Software, Inc.  All rights reserved.
This software comes with NO WARRANTY: see the file PUBLIC for details.
Processing pages 1 through 2.
Page 1
Can't find (or can't open) font file /home/barna/Resource/Font/Arial-BoldMT.
Can't find (or can't open) font file Arial-BoldMT.
Can't find (or can't open) font file /home/barna/Resource/Font/Arial-BoldMT.
Can't find (or can't open) font file Arial-BoldMT.
Querying operating system for font files...
Loading Arial-BoldMT font from /usr/share/fonts/truetype/msttcorefonts/arialbd.ttf... 3138384 1581997 6155428 2614245 3 done.
Loading ArialMT font from /usr/share/fonts/truetype/msttcorefonts/Arial.ttf... 3165184 1613050 6461100 2975572 3 done.
Page 2
Loading Arial-BoldMT font from /usr/share/fonts/truetype/msttcorefonts/arialbd.ttf... 3279432 1620680 4187652 2599298 3 done.
Loading ArialMT font from /usr/share/fonts/truetype/msttcorefonts/Arial.ttf... 3286136 1648132 4165500 2481639 3 done.

   **** Warning: Fonts with Subtype = /TrueType should be embedded.
                 The following fonts were not embedded:
                        Arial
                        Arial,Bold

   **** This file had errors that were repaired or ignored.
   **** The file was produced by:
   **** >>>> PDFXC Library (version 2.5). <<<<
   **** Please notify the author of the software that produced this
   **** file that it does not conform to Adobe's published PDF
   **** specification.


```

Then tried to print the resulting ps file - the printer display showed for a short time 'Processing job', but then went off, and nothing came out from the printer, and the printer queue is also empty.

Well, ok, according to the message of gs, the PDF file is broken. But does it also mean that I will not be able to print it, even though I can see it on my display? Any idea?

Thanks
Daniel

---

### Post by mali2297 on 2007-11-05
You could try to convert the file to postscript with
```

pdftops minitico.pdf

```
or
```

pdf2ps minitico.pdf

```
(Can't remember which tool that is installed by default in Ubuntu.)

---

### Post by barna on 2007-11-05
Those did not help, either. (Same warning during conversion, and no output from the printer when printed)

however, switching off/on the printer seems to have helped. so I think this is finally a printer issue.

---

