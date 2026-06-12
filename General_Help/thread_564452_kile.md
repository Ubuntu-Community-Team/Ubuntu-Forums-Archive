---
title: "kile"
date: 2007-10-01
forum: General Help
---

### Post by vcadavez on 2007-10-01
Hello

I'm trying to use Kile!
I have this error! somebody can help?
[LaTeX] morfologia.tex => morfologia.dvi (latex)
[LaTeX] finished with exit status 1
/usr/share/texmf-tetex/tex/latex/pdfscreen/pdfscreen.sty:337: Option `pagebackref' has already been used,(hyperref) setting the option has no effect on input line 337. Option `pagebackref' has already been used,(hyperref) setting the option has no effect
/usr/share/texmf-tetex/tex/latex/pdfscreen/pdfscreen.sty:337: Option `backref' has already been used,(hyperref) setting the option has no effect on input line 337. Option `backref' has already been used,(hyperref) setting the option has no effect
/usr/share/texmf-tetex/tex/latex/pdfscreen/pdfscreen.sty:829:File `truncate.sty' not found. \newcounter
[LaTeX] 1 error, 2 warnings, 0 badboxes

[ViewDVI] The file /home/vc/morfologia/morfologia.dvi does not exist; did you compile the source file?

---

### Post by gaussian on 2007-10-01
As pointed out by Adotb in the other thread  (see [http://ubuntuforums.org/showthread.php?t=561362](http://ubuntuforums.org/showthread.php?t=561362)) the hyperref package used by the original .tex file probably works only with pdflatex. You should try to run that instead of regular LaTeX. In Kile I think you should see in the toolbar an alternative to produce a PDF (instead dvi) from your source. Try that. Hope this helps.

---

