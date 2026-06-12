---
title: "Tex/LaTeX/TexLive/tetex"
date: 2006-11-28
forum: General Help
---

### Post by rosslaird on 2006-11-28
It seems very difficult to find consistent information regarding the decision about whether to switch from tetex to texlive in edgy. There are a number of posts on the forum about the question in general, but many of them are from before edgy was released. So, I am left with various uncertainties:

Given that tetex is no longer supported, but is still installed by default in edgy, and given that texlive seems to be the best replacement, I thought I should make the switch. I have different parts of both on my system (and I have lost track of which of these were installed by default and which were added by me). When I use apt-get to try to install various texlive packages (such as texlive-base), apt wants to remove a bunch of stuff, eg:

```
The following packages were automatically installed and are no longer required:
  whizzytex winefish tetex-extra latex2html libsgmls-perl libaiksaurus-1.2-data texlive-fonts-extra
  latexmk texi2html auctex lyx-qt groff preview-latex-style tetex-base texlive-publishers rubber
  docbook-utils docbook-dsssl libostyle1c2 dblatex linuxdoc-tools texpower advi jadetex
  translate-docformat openjade muttprint pdfjam tetex-bin tetex-doc sgmlspl lyx-common cm-super
  latex-ucs lyx libkpathsea-perl xdg-utils sgmltools-lite libroman-perl debiandoc-sgml
  texlive-latex-extra linuxdoc-tools-latex texlive-pictures libaiksaurus-1.2-0c2a libtiff-tools
  latex2rtf kile pfb2t1c2pfb catdvi texinfo libtext-format-perl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  texlive-base texlive-base-bin
Recommended packages:
  lmodern
The following packages will be REMOVED:
  advi auctex catdvi cm-super dblatex docbook-utils jadetex kile latex-ucs latex2html latex2rtf
  latexmk libkpathsea-perl linuxdoc-tools-latex lyx lyx-common lyx-qt muttprint pdfjam
  preview-latex-style rubber tetex-base tetex-bin tetex-doc tetex-extra texlive-fonts-extra
  texlive-latex-extra texlive-publishers texpower translate-docformat whizzytex winefish
The following NEW packages will be installed:
  texlive-base texlive-base-bin texlive-pdfetex

```

Now, I use certain things in the above list, such as auctex and muttprint. So, am I stuck with tetex for now?

Also, I have installed quite a few opentype fonts into my tetex installation, and I wonder how those might get transferred to the texlive setup.

Also, once texlive is installed, will it use the commands "latex" and "pdflatex"? Or is there some other scheme?

Any insight would be appreciated.

Ross

---

### Post by aleksabl on 2006-12-03
Hi!

I haven't tried to upgrade to texlive yet, but I know that the Smart Package Manager solves many problems similar to yours. You could try installing and using it instead of apt-get/aptitude:

```

sudo apt-get install smartpm
sudo smart update
sudo smart install texlive

```

---

### Post by NunoCorreia on 2006-12-03
Besides texlive being maintained unlike tetex, what other advantages are there in upgrading? I have a bunch of LaTeX documents which compile well, will installing texlive break compatibility with the LaTeX packages?

---

### Post by rosslaird on 2006-12-03
I have upgraded to texlive, using:

apt-get install texlive-full

A few things were removed (though some that I thought might be removed were not, actually, so I still have auctex and muttprint). I have not explored the Smart Package Manager, which I assume is a front-end for apt (which is itself a front-end for dpkg, more or less).

I have experienced no issues of any kind. Texlive is working perfectly on my system (YMMV).

> Besides texlive being maintained unlike tetex, what other advantages are there in upgrading? I have a bunch of LaTeX documents which compile well, will installing texlive break compatibility with the LaTeX packages?

Texlive has many more inbuilt packages than tetex, so it's easier to call on a package and be reasonably sure it's already in the system. My latex documents compiled under tetex work exactly the same as those compiled on texlive. I don't think this part changes at all (though I'm no expert). I think the main changes have to do with packaging, more than anything else. And, of course, texlive is being maintained.

It may be an indication of something (or not), but I recently purchased a copy of the LaTeX Companion. The CD that came with the book is TexLive.

Ross

---

### Post by venik212 on 2007-05-15
I thought that TexLive-Full installs all the languages (Bulgarian, etc.)  as well.  Is that true?

---

### Post by pvdg on 2007-06-26
> I thought that TexLive-Full installs all the languages (Bulgarian, etc.) as well. Is that true?

Yes, venik212, the meta-package texlive-full installs all texlive packages, including all the languages. If you install using synaptic or aptitude, you can manually (de)select the languages and other packages you don't need.

---

### Post by frisket on 2007-06-28
> will installing texlive break compatibility

No, TeX is TeX and LaTeX is LaTeX no matter what distro you use, provided that you have all the packages installed that you need. The only compatibility problems will be if you have used hardware-specific or OS-specific addresses, or you have been using obsolete versions of packages or fonts.

---

### Post by ecmerkle on 2007-07-09
> **pvdg said:**
> If you install using synaptic or aptitude, you can manually (de)select the languages and other packages you don't need.

FWIW, I just switched from tetex to texlive in synaptic using this strategy.  I first selected texlive-full, then deselected the languages I don't need.  Everything worked seamlessly.

I finally switched to texlive because I kept having to manually install style files that were not included with tetex.

---

### Post by venik212 on 2007-07-11
How do you add packages you need to TexLive?

---

### Post by ecmerkle on 2007-07-12
venik, this link may help:

[http://irrepupavel.blogspot.com/2007/02/installing-latex-style-files-sty-on.html](http://irrepupavel.blogspot.com/2007/02/installing-latex-style-files-sty-on.html)

---

### Post by venik212 on 2007-07-13
Thanks, that was helpful.  I typically run sudo texhash after installing a new package.

---

