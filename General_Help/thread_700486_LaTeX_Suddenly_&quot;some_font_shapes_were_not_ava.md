---
title: "LaTeX: Suddenly &quot;some font shapes were not available&quot;"
date: 2008-02-18
forum: General Help
---

### Post by Dingbats on 2008-02-18
I'm working on a quite large LaTeX document.  Compiling it with pdflatex makes the font render improperly, so I'm compiling it with a script to the effect of:

```
latex file.tex
dvips -t a4 -Ppdf file.dvi
ps2pdf file.ps
```
It's been working perfectly fine until recently.

As I was zooming in and out on the PDF in Evince, everything started lagging terribly, the mouse pointer barely moved.  After half a minute, Gnome crashed and restarted, and all windows in the other workspaces were closed.  (I don't really care why that happened, that's not the problem.)  The next compile after that crash, the font was different.  It looks like the left picture in 100% zoom, ragged and ugly.  In 200% zoom, the right picture, it looks ok.

I've attached the log file, but I assume the relevant part is this:

```
LaTeX Font Warning: Some font shapes were not available, defaults substituted.
```

EDIT:  A reboot doesn't fix it, nor does commenting out everything I've added to the tex file since the problem first appeared.

I'm running Gutsy, if that's relevant.

---

### Post by cubekid on 2008-02-18
did you install tetex or texlive? i'm not sure if that would make any difference, but tetex isn't managed anymore ([http://www.tug.org/tetex/]("http://www.tug.org/tetex/")), so that could possibly be a problem.

---

### Post by Dingbats on 2008-02-18
It's Texlive, with the Tetex transitional packages too.

---

### Post by Dingbats on 2008-02-19
Bump...

---

### Post by Dingbats on 2008-02-21
One last attempt..?

---

### Post by mostley on 2008-06-05
bump

---

