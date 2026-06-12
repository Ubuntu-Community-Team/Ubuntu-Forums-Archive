---
title: "pdflatex fonts problem"
date: 2005-04-13
forum: General Help
---

### Post by dbolgheroni on 2005-04-13
Hi,

I've installed Ubuntu yesterday, mainly to use LaTeX.

I have a file called rel_03.tex and I want to generate a .pdf file with. "pdflatex" runs OK, but the fonts are ugly and all accents refuse to show. Running "latex", I can generate a .dvi file and it looks fine.

I think I'm missing to install some fonts, because when I try to generate a .pdf file from a .dvi with "dvipdf", I get these messages:

$ dvipdf rel_03.dvi
dvips: Font cmbx12 at 9600 not found; scaling 600 instead.
dvips: Such scaling will generate extremely poor output.
dvips: Font cmr10 at 8000 not found; scaling 600 instead.
dvips: Font cmti10 at 8000 not found; scaling 600 instead.
dvips: Font cmbx12 at 8000 not found; scaling 600 instead.
dvips: Font cmmi10 at 8000 not found; scaling 600 instead.
dvips: Font cmsy7 at 8000 not found; scaling 600 instead.
dvips: Font cmmi7 at 8000 not found; scaling 600 instead.
dvips: Font cmsy10 at 8000 not found; scaling 600 instead.
dvips: Font cmr7 at 8000 not found; scaling 600 instead.

(...)
$

What can I do to solve this? I need to finalize this job today.

Thank you very much.

---

### Post by dbolgheroni on 2005-04-13
I know this question was asked before, but my problem remains the same even doing what was suggested.

[http://www.ubuntuforums.org/showthread.php?t=8093&highlight=pdflatex](http://www.ubuntuforums.org/showthread.php?t=8093&highlight=pdflatex)
[http://www.ubuntuforums.org/showthread.php?t=5448&highlight=pdflatex](http://www.ubuntuforums.org/showthread.php?t=5448&highlight=pdflatex)

I've installed tetex-extra but the fonts of the .pdf file generated with pdflatex are to ugly (Monospace?), with no accents.

What can I do?

---

### Post by dbolgheroni on 2005-04-14
Strangely, I deinstalled and installed again tetex-extra package and it worked well.

---

### Post by pestilence4hr on 2005-04-21
[QUOTE=dbolgheroni]Strangely, I deinstalled and installed again tetex-extra package and it worked well.[/QUOTE]

This is indeed strange.  I had the exact same problem and a

```
apt-get install --reinstall tetex-extra
```

fixed it.  Perhaps a bug report should be filed.

---

### Post by roland on 2005-06-03
It did work with me too, thanks!

---

### Post by shadow on 2005-11-20
I just wanted to bump this thread as I'm using breezy and still had this problem. The reinstallation solution fixed it no bother, though.

---

### Post by alphpt on 2007-04-22
Fixed it over here also! Thanks.

---

