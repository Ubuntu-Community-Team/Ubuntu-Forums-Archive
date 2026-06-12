---
title: "avoid pagebreaks at whitespace in LaTeX?"
date: 2007-01-19
forum: General Help
---

### Post by goodmanbrown on 2007-01-19
I'm typesetting text in LaTeX that uses whitespace to mark breaks between sections.  I'm using \bigskip to make the whitespace.  The problem with this is that when a pagebreak happens to fall at the point of the \bigskip, the visual impression of the whitespace is lost, and it looks like a normal paragraph break.

In published work, I typically see whitespace that falls at a pagebreak marked with some sort of symbol at the bottom or top of the page.  (This is super common in fiction.)  Is there anyway to get LaTeX to do this automatically?  That is, is there a way to get LaTeX to notice when a \bigskip falls at a pagebreak, and to mark it with a few asterisks, or something?  Is there a better way to get whitespace than \bigskip?

And, most generally, does anyone know of a good resource for tips and tricks on typesetting fiction (or creative prose in general) in LaTeX?

---

### Post by Gillingham on 2007-01-19
To get the behaviour you want, I think you need to use the \fancyplainbreak command defined in the memoir class, although you may have to redefine the section command to make best use of it.  Having just had a look, the documentation seems to be quite comprehensive.

When I need a new package/class for LATEX I tend to look at the TeX catalogue which can be found at [http://www.tex.ac.uk/tex-archive/help/Catalogue/catalogue.html]("http://www.tex.ac.uk/tex-archive/help/Catalogue/catalogue.html")
this catalogues a lot of useful LATEX packages.

---

### Post by goodmanbrown on 2007-01-20
Thank you!  The memoir class is exactly what I needed.  I might see if I can tweak it's display a bit, but the behavior of \pfbreak macro is, in principle, just what I want.

---

