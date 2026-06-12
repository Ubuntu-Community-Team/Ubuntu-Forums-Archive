---
title: "[SOLVED] Pidgin LaTeX problems"
date: 2007-10-30
forum: General Help
---

### Post by Can+~ on 2007-10-30
Using ubuntu Gutsy, it came with Pidgin and the LaTeX plugin preinstalled. So I downloaded the LaTeX necessary files, imageMagick, and now when I do a $$anything$$ I get a blank image. Then I executed pidgin via terminal and it created the following output (bold is the important thing).

> This is pdfTeXk, Version 3.141592-1.40.3 (Web2C 7.5.6)
 %&-line parsing enabled.
entering extended mode
(/tmp/purpleQD4R0T.tex
LaTeX2e <2005/12/01>
Babel <v3.8h> and hyphenation patterns for english, usenglishmax, dumylang, noh
yphenation, loaded.
(/usr/share/texmf-texlive/tex/latex/base/article.cls
Document Class: article 2005/09/16 v1.4f Standard LaTeX document class
(/usr/share/texmf-texlive/tex/latex/base/size12.clo))
(/usr/share/texmf-texlive/tex/latex/graphics/graphicx.sty
(/usr/share/texmf-texlive/tex/latex/graphics/keyval.sty)
(/usr/share/texmf-texlive/tex/latex/graphics/graphics.sty
(/usr/share/texmf-texlive/tex/latex/graphics/trig.sty)
(/etc/texmf/tex/latex/config/graphics.cfg)
(/usr/share/texmf-texlive/tex/latex/graphics/dvips.def)))
(/usr/share/texmf-texlive/tex/latex/amsmath/amsmath.sty
For additional information on amsmath, use the `?' option.
(/usr/share/texmf-texlive/tex/latex/amsmath/amstext.sty
(/usr/share/texmf-texlive/tex/latex/amsmath/amsgen.sty))
(/usr/share/texmf-texlive/tex/latex/amsmath/amsbsy.sty)
(/usr/share/texmf-texlive/tex/latex/amsmath/amsopn.sty))
(/usr/share/texmf-texlive/tex/latex/amsfonts/amssymb.sty
(/usr/share/texmf-texlive/tex/latex/amsfonts/amsfonts.sty))
**No file purpleQD4R0T.aux.**
(/usr/share/texmf-texlive/tex/latex/amsfonts/umsa.fd)
(/usr/share/texmf-texlive/tex/latex/amsfonts/umsb.fd) [1] (./purpleQD4R0T.aux) 
)
**Output written on purpleQD4R0T.dvi (1 page, 224 bytes).**
Transcript written on purpleQD4R0T.log.
This is dvips(k) 5.96.1 Copyright 2007 Radical Eye Software ([www.radicaleye.com](www.radicaleye.com))
' TeX output 2007.10.30:2351' -> /tmp/purpleQD4R0T.ps
</usr/share/texmf-texlive/dvips/base/tex.pro>
</usr/share/texmf-texlive/dvips/base/texps.pro>. 
</usr/share/texmf-texlive/fonts/type1/bluesky/cm/cmmi12.pfb>[1] 

---

### Post by teckan on 2007-12-12
Have you managed to solve this problem? I am experiencing it at this moment, and I don't have any clue on how to solve it. Thanks in advance for positive response(s).

---

### Post by xubis on 2007-12-13
I have this exact same problem too

---

### Post by peabody on 2007-12-15
It came with the LaTeX plugin pre-installed?  odd, I didn't see it installed under my plugin list, nor did I see it in the repositories.  I installed it via checkinstall from the source.  Seems to work fine, I've posted the deb, let me know if it works for you guys.

---

### Post by Can+~ on 2007-12-15
> **peabody said:**
> It came with the LaTeX plugin pre-installed?  odd, I didn't see it installed under my plugin list, nor did I see it in the repositories.  I installed it via checkinstall from the source.  Seems to work fine, I've posted the deb, let me know if it works for you guys.

IT WORKED!

:guitar: Marking as solved, and please, anyone else having this problem, do this.

Also, notice that you must restart pidgin, go to the plugins sections, and now I have two "LaTeX plugin" installed, mark the first one.

---

### Post by xubis on 2007-12-18
I've done as you said, but now when I type $$anything$$ pidgin just closes completely! argh!

---

### Post by Can+~ on 2007-12-29
> **xubis said:**
> I've done as you said, but now when I type $$anything$$ pidgin just closes completely! argh!

Make sure you have image-magick installed, and LaTeX, LaTeX-live I think?

Also run pidgin through console to receive some output.

---

### Post by xubis on 2008-01-18
I had all this installed, so I purged it all and purged gaim then redid it all and is now working :D Thanks guys

---

