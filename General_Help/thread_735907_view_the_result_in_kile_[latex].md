---
title: "view the result in kile [latex]"
date: 2008-03-26
forum: General Help
---

### Post by afeasfaerw23231233 on 2008-03-26
i have another problem again. how can i view the result immediately after i type?
for example, i type tan \theta = \frac{k-tan \alpha }  {1-2} , how do i view the result?
edit : or where can i get a instant tex preview software?

---

### Post by dvase on 2008-03-30
This probably isn't exactly what your looking for, but Kile 2.0 has a quick preview ability.

If you right click within a selection such as an equation there is an option called "QuickPreview Selection".  Selecting this option presents a preview of the equation in the QuickPreview tab window below the text.

Other TeX options that are more WYSIWYG (or more precisely WYSIWYM) are LyX and Texmacs.  They do somewhat obfuscate the underlying Tex code, but give the user more immediate graphical feedback.

---

### Post by afeasfaerw23231233 on 2008-04-08
thanks

---

### Post by frisket on 2008-04-09
> **afeasfaerw23231233 said:**
> i have another problem again. how can i view the result immediately after i type?
for example, i type tan \theta = \frac{k-tan \alpha }  {1-2} , how do i view the result?
edit : or where can i get a instant tex preview software?

AUCTeX has a Preview-LaTeX mode 
[http://www.gnu.org/software/auctex/preview-latex.html](http://www.gnu.org/software/auctex/preview-latex.html)

PyTeX has Instant Preview
[http://www.pytex.org/texd/](http://www.pytex.org/texd/)

But normally you just click the LaTeX button and then the ViewDVI button (the first time).
Keep the viewer window open, and then any time you click the LaTeX button the display will update. 

///Peter

---

