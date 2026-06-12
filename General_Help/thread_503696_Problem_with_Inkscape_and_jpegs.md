---
title: "Problem with Inkscape and jpegs"
date: 2007-07-18
forum: General Help
---

### Post by oscarsfriend on 2007-07-18
HI,

I'm trying to clip a jpeg in Inkscape .45(.1) inside a curved shape.  It seems to work fine, but when I try to print or export as ps/PDF it unclips the jpeg (displays as a full rectangular image, though it still displays OK in inkscape).  This worked fine when I tried it with .45pre1 on a Windows XP machine.  I upgraded to .45.1 and it still doesn't work.  Anyone have an idea what is going on here?

---

### Post by oscarsfriend on 2007-07-18
I take it back -- it only seems to work on occasions on Windows XP.  I'll have a go at updating to a development version.

EDIT: OK I think I know what's happening now.  There is a bug in Inkscape that messes up clipping images when exporting to ps/PDF.  Since Linux prints using ps files, the printout is messed up.  But since Windows doesn't print that way it works for printing, but not for exporting to ps/PDF.

---

### Post by oscarsfriend on 2007-07-18
Tried the current development version (inkscape-15450).  It still can't produce correct PDFs, though it can produce botched PS files (the image is misplaced inside the curved container).  I guess I'll have to wait until they fix that...

---

### Post by Anzan on 2007-07-18
Thanks for posting that. Though you had no replies, keeping a record of what you found will be helpful to someone.

---

### Post by oscarsfriend on 2007-07-20
Will do, Anzan.

There is an easy way around this for printing. Select print and then print as bitmap, and then a decent resolution (default is 72dpi, I tried 300dpi), and then print as usual.  This works fine on  the Linux version.

---

