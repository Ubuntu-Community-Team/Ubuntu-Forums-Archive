---
title: "Incosolata: Using it in LaTeX"
date: 2007-10-09
forum: General Help
---

### Post by drbcladd on 2007-10-09
Okay, I am not a complete idiot. I swear that that is true. I can search and read manuals and all that stuff. That said, I am unable to use the Incosolata font in LaTeX.

Is this an Ubuntu question? No. But I have Googled and searched CTAN and tried all my tricks. Heck, I spent three hours trying to figure out how to install it. Is there a particular LaTeX variant that I should be running? I use Emacs with AucTeX for editing TeX files; should I use something else?

I am really sorry to sound so stupid but my brain is drained and this should not be this hard. I have Inconsolata installed and usable in OOo and the GIMP; I just need to convince LaTeX to find and use it.

Thanks in advance,
-bcl

---

### Post by frisket on 2007-10-09
Do you mean Inconsolata? 

LaTeX handles fonts utterly differently from other packages, and entirely independently of the operating system so comparisons with font installation for OOo and other graphics packages are not going to be useful. Neither will Google. Your first port of call should always be the TeX FAQ at [http://www.tex.ac.uk/faq](http://www.tex.ac.uk/faq) 

Anyway, you need a pfb and an afm file for the font. Looks like he only supplies a pfa (how quaint and old-fashioned :-) so download that, install FontForge, open it, and Save As pfb with afm. Then go to chapter 8 of _Formatting Information_ and see the Postscript font installation instructions for LaTeX ([http://research.silmaril.ie/latex/chapter8.html#psfonts](http://research.silmaril.ie/latex/chapter8.html#psfonts)). It's tedious but it works.

Alternatively, replace the tex binary in your distro with the XeTeX one. This is a new engine which includes automatic recognition of all installed fonts of any type. Still beta, but very good.

///Peter

---

### Post by tacutu on 2007-10-29
you don't need the ps fonts... there are ways to use TTF in latex, but you need to do some work first. Just try googling for "truetype latex", you'll find plenty of tutorials

---

