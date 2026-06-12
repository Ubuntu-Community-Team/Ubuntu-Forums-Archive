---
title: "problems with music files"
date: 2016-03-09
forum: General Help
---

### Post by mringer on 2016-03-09
The site  cpdl.org   has a huge collection of music in public domain.
Unfortunately, far too many of these are only available as  pdf  files.
Many of these look good on screen but awful when printed, due to
general blurring and substituted fonts. Please, any idea why?

Blurring: On screen, the music is black & white. Printed, it is fuzzy grey.
The quality is like an old Epson FX-80 printer (remember these?)
long overdue for a new ribbon.

Fonts: Here is a typical result using  pdffonts;

name                                                    type                   encoding           emb   sub    uni     object    ID
------------------------------------ ----------------- ---------------- --- --- --- ---------
PSJPKV+TimesNewRomanPSMT                 TrueType             MacRoman         yes     yes    no       7         0
PODVVK+TimesNewRomanPS-BoldMT         TrueType             MacRoman         yes     yes    no       8         0
NLBEXL+Chicago                                     TrueType             MacRoman         yes     yes    no       9         0

(I added extra spaces to align the columns) . The substituted font is
very ugly. Also the successive characters collide.  I think this is
because the new font is fatter than the original, but printed at the
original spacing.

I used gimp to convert to a TIFF. This looks much better. But I would really
like to be able to convert these files to a computer-readable format in order
to correct some musical faults. Most music scanning progs are expensive.
the foremost free one seems to be audiveris (AV), but I cannot get it to work.

When I try to run AV  on a PDF, it says  "cannot get an image from   xyz.pdf ".
When I convert to  tiff   and load a tiff  , it reads the file, then tries to digest
it in stages:

load > scale > grid > systems > measures > texts > etc

and it goes up to measures with no visible error. When I try  texts  there is a
wait and then  AV  crashes. There is no error message. The AV window
disappears.

Versions:     
L-ubuntu           14.04     
AV                  4.3.3406
Ghostscript       9.10-dfsg-0ubuntu
tesseract-OCR   3.03-02.3

Please any advice? thank you, Mark

---

### Post by ecaep on 2016-03-10
After some research looks like the is caused by either the font of the PDF or by the PDF reader it self. I would recommend either seeing if the site has a different format for the files or try an alternative PDF reader.

Also as a least practical method you could copy the contents of the PDF to a text editor and try changing the font and printing.

---

