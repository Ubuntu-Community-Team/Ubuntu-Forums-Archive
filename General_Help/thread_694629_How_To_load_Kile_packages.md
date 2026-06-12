---
title: "How To load Kile packages"
date: 2008-02-12
forum: General Help
---

### Post by cangg on 2008-02-12
I'm new to ubuntu can someone help me how to load packages to kile?

I downloaded the package I wanted, revtex_3.1.orig.tar.gz what next? Thanks

---

### Post by apetresc on 2008-02-12
You don't load REVTeX into Kile; Kile is just a LaTeX editor, not an actual LaTeX system. If you installed Kile, chances are you have installed either the TeTeX or TeX-Live systems. Both of those are supported by REVTeX, just look at their installation instructions for either at: [http://authors.aps.org/revtex4/revtex4_faq.html#inst1a](http://authors.aps.org/revtex4/revtex4_faq.html#inst1a)

But if you are using tetex, you can get revtex right from the repository:```
sudo apt-get install tetex-extra
```Isn't that much easier? :)

**EDIT:** Oh, and it turns out, if you're using TeX-Live, you just need ```
sudo apt-get install texlive-publishers
``` and it's running! So no need to do a manual installation yourself!

---

### Post by cangg on 2008-02-12
thank you :)

---

### Post by Gepetto on 2008-04-16
Sorry to bring up an old thread, but I can't seem to get this to work. I tried installing the texlive-publishers, and that worked fine, but I still can't use the packages. I've tried Kile and Winefish and neither will let me do anything. What am I doing wrong here?

---

### Post by apetresc on 2008-04-16
> **Gepetto said:**
> Sorry to bring up an old thread, but I can't seem to get this to work. I tried installing the texlive-publishers, and that worked fine, but I still can't use the packages. I've tried Kile and Winefish and neither will let me do anything. What am I doing wrong here?

Hm, how are you trying to 'use' the package, and what error is it giving? Also, are you on Hardy or Gutsy?

---

### Post by Gepetto on 2008-04-16
Sorry, I'm new to this whole Latex thing. I'm in Gutsy. Basically, I need to use some commands or whatever in revtex, so I installed texlive-publishers. I'm not sure now what I need to do in order to be able to use the revtex package.

---

### Post by eljalill on 2008-04-17
well, in the preamble to your document (after \documentclass) you need to call up the package:
\usepackage{revtex} in case that is what it is called. Only after you can use the package related commands.

---

