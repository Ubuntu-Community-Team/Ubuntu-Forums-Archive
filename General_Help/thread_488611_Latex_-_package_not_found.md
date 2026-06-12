---
title: "Latex - package not found"
date: 2007-06-30
forum: General Help
---

### Post by Ultra Magnus on 2007-06-30
Hi - I'm a long time user of latex on windows - I used Miktex and whenever I used a new package, it would just automatically download it for me - I've been using Linux for a bit and wanted to update my CV, I decided to use tetex because people said it was a good latex package but when I tried to create a PDF, it said it couldn't find "fullpage.sty" package. I've been having a look but can't seem to find where to get packages from, just wondering did I miss something to download, and is there a way I can get packages to automatically download when I use a new one?

Thanks

Jim

---

### Post by nereid on 2007-06-30
What did you use to create the pdf? pdflatex?

---

### Post by Ultra Magnus on 2007-06-30
> **nereid said:**
> What did you use to create the pdf? pdflatex?

yep - just typed "pdflatex cv.tex"

---

### Post by nickbooker on 2007-06-30
Hi.

fullpage.sty is in the tetex-extra package, so use Synaptic to install it, or install from the terminal:

```
$ sudo apt-get install tetex-extra
```

---

### Post by nickbooker on 2007-06-30
> **Ultra Magnus said:**
> is there a way I can get packages to automatically download when I use a new one?

Sorry just noticed this bit ;)

There isn't as far as I know, but tetex-extra contains a lot of commonly-used packages.

There are some other packages in the universe repositories too, such as latex-beamer, pgf, latex-xcolor et cetera that you can install separately.

If you need anything that isn't in a deb package, you can probably find it on [http://www.ctan.org/](http://www.ctan.org/) (the Comprehensive TeX Archive Network).  Choose search for a file name and put in the .sty (or whatever) file it's looking for and it should be there.  Most packages can be extracted into ~/texmf and 'just work'.

---

### Post by Ultra Magnus on 2007-06-30
Awesome, thanks allot, managed to get it to work.

---

### Post by Muhahahahaz on 2007-12-09
WOW, 249MB??  This is going to take forever... :(

:popcorn:

---

### Post by rhm on 2008-06-16
> **Ultra Magnus said:**
> Awesome, thanks allot, managed to get it to work.

How did you get it to work?

My LaTeX is having the same problem finding the {fullpage} package. I'm using TeXLive through AUCTeX in emacs for the first time, trying to get a feel for it and, as such, have very little idea about what to do.

---

### Post by mali2297 on 2008-06-16
> **rhm said:**
> How did you get it to work?

My LaTeX is having the same problem finding the {fullpage} package. I'm using TeXLive through AUCTeX in emacs for the first time, trying to get a feel for it and, as such, have very little idea about what to do.

If you search for **fullpage.sty** [here]("http://packages.ubuntu.com/"), you will find it in the package **texlive-latex-extra**. Have you installed that package?

---

### Post by rhm on 2008-06-30
> **mali2297 said:**
> If you search for **fullpage.sty** [here]("http://packages.ubuntu.com/"), you will find it in the package **texlive-latex-extra**. Have you installed that package?

I had not installed that package yet. I did so now and it works perfectly. Thanks! Also, thanks for the link; I'm sure it will come in handy in the future.

---

