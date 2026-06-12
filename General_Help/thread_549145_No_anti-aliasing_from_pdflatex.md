---
title: "No anti-aliasing from pdflatex"
date: 2007-09-12
forum: General Help
---

### Post by _davidh on 2007-09-12
Hey.

I'm trying to convert some LaTeX to PDF with pdflatex (which I got from installing tetex-bin). This works fine, but the quality of the text is poor. It has _some_ anti-aliasing, but it's mostly visible if you zoom. On 100 % in evince, it looks crap.

I used MiKTeX on Windows before, and the resulting PDFs looks nice in evince, so no problem there.

Does anyone know what the problem may be? Do I need to install some fonts, or tweak some font setting somewhere? Do I need to provide more details?

Thanks in advance for any pointers.

---

### Post by mali2297 on 2007-09-12
You could try to first create a dvi file and then run dvipdf, but I doubt that helps.

Or you could try to reinstall tetex-extra, see here:
[http://ubuntuforums.org/showthread.php?t=26649](http://ubuntuforums.org/showthread.php?t=26649)

---

### Post by _davidh on 2007-09-12
> **mali2297 said:**
> Or you could try to reinstall tetex-extra, see here:
[http://ubuntuforums.org/showthread.php?t=26649](http://ubuntuforums.org/showthread.php?t=26649)
Installing tetex-extra fixed the problem.

Tack så mycket :-)

---

