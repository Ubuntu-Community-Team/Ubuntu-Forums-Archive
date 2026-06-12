---
title: "using latex beamer in Ubuntu Gutsy"
date: 2007-10-01
forum: General Help
---

### Post by yshhq on 2007-10-01
Hi,

I am using ubuntu gutsy, and having trouble to compile beamer tex files. 
For example: [http://heather.cs.ucdavis.edu/~matloff/BeamerTour.tex](http://heather.cs.ucdavis.edu/~matloff/BeamerTour.tex)
After I compile, I got the following error:
Is this because of texlive? I got no problem in my laptop installed gentoo and tetex.

Thank you!

Best,
Peng

[LaTeX] BeamerTour.tex => BeamerTour.dvi (latex)
[LaTeX] finished with exit status 1
/usr/share/texmf-texlive/tex/latex/graphics/graphics.sty:88:Package graphics Error: No driver specified. }
/usr/share/texmf/tex/generic/pgf/systemlayer/pgfsys.code.tex:848:Package pgfsys Error: Driver file ``pgfsys-'' not found.. ...ver file ``\pgfsysdriver'' not found.}{}}
/usr/share/texmf/tex/latex/xcolor/xcolor.sty:218:Package xcolor Error: No driver specified. eg: \protect\ExecuteOptions{dvips}}
/usr/share/texmf/tex/latex/xcolor/xcolor.sty:1422:Undefined control sequence. }{}
/usr/share/texmf/tex/latex/beamer/base/beamer.cls:0: Option `pdfpagelabels' is turned off(hyperref) because \thepage is undefined.
/usr/share/texmf/tex/latex/beamer/base/beamerbasenavigation.sty:211: Your graphic driver pgfsys- does not supported path constructions. This warning is given only once on input line 211. Your graphic driver pgfsys- does not supported path constructions. This warning is given only once
/usr/share/texmf/tex/latex/beamer/base/beamerbasenavigation.sty:0: Your graphic driver pgfsys- does not supported path usage.
/usr/share/texmf/tex/latex/beamer/base/beamerbasenavigation.sty:280: Your graphic driver pgfsys- does not supported setting theline width. This warning is given only once on input line 280. Your graphic driver pgfsys- does not supported setting theline width. This warning is given only once
/usr/share/texmf/tex/latex/beamer/base/beamerbasenavigation.sty:428: Your graphic driver pgfsys- does not supported setting theline cap. This warning is given only once on input line 428. Your graphic driver pgfsys- does not supported setting theline cap. This warning is given only once
/usr/share/texmf/tex/latex/beamer/themes/inner/beamerinnerthemedefault.sty:0: File "beamericonbook" not found when defining image "beamericonbook".
/usr/share/texmf/tex/latex/beamer/themes/inner/beamerinnerthemedefault.sty:0: File "beamericonbook.20" not found when defining image "beamericonbookshaded".
/usr/share/texmf/tex/latex/beamer/themes/inner/beamerinnerthemedefault.sty:0: File "beamericonarticle" not found when defining image "beamericonarticle".
/usr/share/texmf/tex/latex/beamer/themes/inner/beamerinnerthemedefault.sty:0: File "beamericonarticle.20" not found when defining image"beamericonarticleshaded".
BeamerTour.tex:16: Token not allowed in a PDFDocEncoded string,(hyperref) removing `\\' on input line 16. Token not allowed in a PDFDocEncoded string,(hyperref) removing `\\'
BeamerTour.tex:16: Token not allowed in a PDFDocEncoded string,(hyperref) removing `\\' on input line 16. Token not allowed in a PDFDocEncoded string,(hyperref) removing `\\'
BeamerTour.tex:0:No file BeamerTour.aux.
BeamerTour.tex:0:No file BeamerTour.nav.
BeamerTour.tex:36: Your graphic driver pgfsys- does not supported scoping. This warning is given only once on input line 36. Your graphic driver pgfsys- does not supported scoping. This warning is given only once
BeamerTour.tex:36: Your graphic driver pgfsys- does not supported color. Thiswarning is given only once on input line 36. Your graphic driver pgfsys- does not supported color. Thiswarning is given only once
BeamerTour.tex:38: Your graphic driver pgfsys- does not supported transformations. This warning is given only once on input line 38. Your graphic driver pgfsys- does not supported transformations. This warning is given only once
BeamerTour.tex:0:No file BeamerTour.toc.
BeamerTour.tex:0:No file BeamerTour.toc.
BeamerTour.tex:143: File `BeamerTriangle.jpg' not found on input line 143.
BeamerTour.tex:143:Unknown graphics extension: .jpg. \end{frame}
BeamerTour.tex:143: File `BeamerTriangle.jpg' not found on input line 143.
BeamerTour.tex:143:Unknown graphics extension: .jpg. \end{frame}
BeamerTour.tex:0:No file BeamerTour.toc.
[LaTeX] 6 errors, 21 warnings, 0 badboxes

---

### Post by Golyadkin on 2007-10-01
Hmmm, looks like it can't find the images. YOu can set the directory to look for images with a command, and also add .jpg as a valid image extension. Are you sure you refer to the fiel correctly? Without the extension?

Search path for graphics files:
> 
\graphicspath{*directory_list*}


Default extensions can be added:
> 
\DeclareGraphicsExtensions{*ext_list*}


---

### Post by yshhq on 2007-10-01
I think the reason is that the tex somehow is not installed properly on the machine.

I tried the following very simple case.

\documentclass{beamer}

\title{Test}

\begin{document}

\begin{frame}
\titlepage
\end{frame}

\end{document}

still gives me the following message: (It is complaining on /usr/share/texmf-texlive/tex/latex/graphics/graphics.sty)
[LaTeX] BeamerTour.tex => BeamerTour.dvi (latex)
[LaTeX] finished with exit status 1
/usr/share/texmf-texlive/tex/latex/graphics/graphics.sty:88:Package graphics Error: No driver specified. }
/usr/share/texmf/tex/generic/pgf/systemlayer/pgfsys.code.tex:848:Package pgfsys Error: Driver file ``pgfsys-'' not found.. ...ver file ``\pgfsysdriver'' not found.}{}}
/usr/share/texmf/tex/latex/xcolor/xcolor.sty:218:Package xcolor Error: No driver specified. eg: \protect\ExecuteOptions{dvips}}
/usr/share/texmf/tex/latex/xcolor/xcolor.sty:1422:Undefined control sequence. }{}
/usr/share/texmf/tex/latex/beamer/base/beamer.cls:0: Option `pdfpagelabels' is turned off(hyperref) because \thepage is undefined.
/usr/share/texmf/tex/latex/beamer/base/beamerbasenavigation.sty:211: Your graphic driver pgfsys- does not supported path constructions. This warning is given only once on input line 211. Your graphic driver pgfsys- does not supported path constructions. This warning is given only once
/usr/share/texmf/tex/latex/beamer/base/beamerbasenavigation.sty:0: Your graphic driver pgfsys- does not supported path usage.
/usr/share/texmf/tex/latex/beamer/base/beamerbasenavigation.sty:280: Your graphic driver pgfsys- does not supported setting theline width. This warning is given only once on input line 280. Your graphic driver pgfsys- does not supported setting theline width. This warning is given only once
/usr/share/texmf/tex/latex/beamer/base/beamerbasenavigation.sty:428: Your graphic driver pgfsys- does not supported setting theline cap. This warning is given only once on input line 428. Your graphic driver pgfsys- does not supported setting theline cap. This warning is given only once
/usr/share/texmf/tex/latex/beamer/themes/inner/beamerinnerthemedefault.sty:0: File "beamericonbook" not found when defining image "beamericonbook".
/usr/share/texmf/tex/latex/beamer/themes/inner/beamerinnerthemedefault.sty:0: File "beamericonbook.20" not found when defining image "beamericonbookshaded".
/usr/share/texmf/tex/latex/beamer/themes/inner/beamerinnerthemedefault.sty:0: File "beamericonarticle" not found when defining image "beamericonarticle".
/usr/share/texmf/tex/latex/beamer/themes/inner/beamerinnerthemedefault.sty:0: File "beamericonarticle.20" not found when defining image"beamericonarticleshaded".
BeamerTour.tex:9: Font shape `OT1/cmss/m/n' in size not available(Font) size substituted on input line 9. Font shape `OT1/cmss/m/n' in size not available(Font) size substituted
BeamerTour.tex:9: Your graphic driver pgfsys- does not supported scoping. This warning is given only once on input line 9. Your graphic driver pgfsys- does not supported scoping. This warning is given only once
BeamerTour.tex:9: Your graphic driver pgfsys- does not supported color. Thiswarning is given only once on input line 9. Your graphic driver pgfsys- does not supported color. Thiswarning is given only once
BeamerTour.tex:0: Size substitutions with differences(Font) up to 1.0pt have occurred.
[LaTeX] 4 errors, 13 warnings, 0 badboxes

---

### Post by fnielsen on 2007-11-30
For me not even this works:

\documentclass{article}
\usepackage{graphics}

\begin{document}

\end{document}

ERROR: Package graphics Error: No driver specified.

Perhaps the paths have changed?

---

### Post by yshhq on 2007-11-30
I reinstalled every tex related packages, and then it worked. I don't know how it messed up at the first place.

---

### Post by fnielsen on 2007-12-10
It now works for me. I beleive it was the path that was not set up correctly. I have the following paths set:

export BIBINPUTS=.:/home/fn/tex/lyngbydoc/:
export BSTINPUTS=.:/home/fn/fnielsen/sty/:/usr/share/texmf-texlive/bibtex/bst//
export TEXINPUTS=.:/home/fn/fnielsen/sty/:/usr/share/texmf-tetex/source//:

I found out that the colon in the end is crucial!

---

### Post by buntu_hugenewbie11 on 2008-05-07
How do you reinstall and locate all your tex packages?

---

### Post by __kornel on 2008-05-10
I had the same problem and using ```
\documentclass[hyperref={pdfpagelabels=false}]{beamer}
``` at the beginning of the document helped.
(unlike latex reinstallation)

---

