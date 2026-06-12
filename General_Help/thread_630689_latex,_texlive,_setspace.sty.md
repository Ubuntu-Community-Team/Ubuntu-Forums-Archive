---
title: "latex, texlive, setspace.sty"
date: 2007-12-03
forum: General Help
---

### Post by goodmanbrown on 2007-12-03
I'm having trouble getting LaTeX to see setspace.sty, which I need for doublespacing.  I've installed texlive-latex-recommended, so setspace is installed at /usr/share/texmf-texlive/tex/latex/setspace/setspace.sty.  But if I \usepackage{setspace}, compilation fails as soon as I use \doublespacing.  If I copy setpsace.sty into my working directory, and \usepackage{./setspace}, everything compiles fine.

As an added wrinkle:  another package that comes with texlive-latex-recommended is the memoir class, which I use.  It is installed in /usr/share/texmf-texlive/tex/latex/memoir/ (that is, in the same tree as setspace) and the memoir class works just fine.

Any idea how I can get LaTeX to see all of the packages installed in /usr/share/texmf-texlive/tex/latex/ instead of only some of them?

Thanks!

---

### Post by gaussian on 2007-12-04
This is strange: normally if LaTeX does not see the style, it should fail in the \usepackage -line, not when you use \doublespacing. Is it possible you have a non-working setspace.sty somewhere else in your drive somewhere that gets pick instead of the one at /usr/share/texmf-texlive/tex/latex/setspace/setspace.sty ? What is the output of "locate setspace"?

Second: try texhash and sudo texhash and try again if this cures the problem.

---

### Post by goodmanbrown on 2007-12-04
Thanks for the reply!

Running texhash did not change the strange behavior.

The output of locate setspace is:

```
/var/lib/auctex/emacs22/setspace.elc
/usr/share/texmf-texlive/tex/latex/setspace
/usr/share/texmf-texlive/tex/latex/setspace/setspace.sty
```

Which is as it should be, no?

I'm completely flummoxed.  When setspace.sty is in its installed directory, LaTeX finds it, but can't find the \doublespacing command it specifies.The very same setspace.sty file, when copied to the working directory, works fine.  Mystifying!

Thanks again for the texhash idea.  If you have any others, please do pass them along.

---

### Post by gaussian on 2007-12-05
I am out of ideas too, let's hope someone can help

---

### Post by seepage87 on 2007-12-06
That's really weird.  I'd try two things though, just to troubleshoot.  Try calling \singlespacing or \onehalfspacing instead and see if those error.  then try replacing that version with [this]("http://math.ndsu.nodak.edu/resources/tex/ndsuthesis/setspace.sty") one.  I suppose you could also check the permissions of that file compared to memoir, but that doesn't sound right since it is able to access it in the first place.

---

### Post by elyob on 2008-05-24
Use the command "\DoubleSpacing".  Memoir actually ignores any \usepackage or \RequirePackage related to setspace.  (See TUGBoat, Volume 28, No. 2, p. 245.)

It also does this with
abstract, appendix, array, booktabs, ccaption, 
chngcntr, chngpage, dcolumn, delarray, enumerate, 
epigraph, framed, ifmtarg, ifpdf , index, makeidx, 
moreverb, needspace, new&#64257;le, nextpage, parskip, 
patchcmd, shortvrb, showidx, tabularx, 
titleref , titling, tocbibind, tocloft, verbatim, verse

---

