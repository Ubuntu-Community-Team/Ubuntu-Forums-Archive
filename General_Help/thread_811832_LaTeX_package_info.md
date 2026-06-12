---
title: "LaTeX package info"
date: 2008-05-29
forum: General Help
---

### Post by pndragon on 2008-05-29
I am just starting to learn LaTeX. How do I find out what packages have already been installed? The documentation talks about a file called *local.tex* or *local-guide.tex* but I can't find it.

---

### Post by clong83 on 2008-05-29
I've been using LaTeX for a while, but I don't know where those would be either.  Are you using a front end for it?  If you're a beginner I might recommend it until you get used to the commands.  If you haven't tried one yet, try installing kile, which I believe will automatically install a great number of the packages you might need.

```
sudo apt-get install kile
```

---

### Post by pndragon on 2008-05-29
I have already installed kile. I have also installed texmaker and winefish just because not all editors are created equal and I wanted to see what the differences were.

---

### Post by Nepherte on 2008-05-29
A latex distribution in the repositories is 'Texlive'. There exist a lot of extra additional packages for it as well. If you want them all, and in that way save some problems searching for packages if you need them, install 'texlive-full'. Be careful though, it's like 1Gb in total. And kile is imo definitely the gui you want for latex.

---

### Post by mannheim on 2008-05-29
You can get some idea of which latex "packages" are installed by browsing the directory in which these are put. Open up your file browser and navigate to /usr/share/texmf-texlive/tex/latex/. 

In most cases, the subdirectories there will each contain one .sty file, or a group of files related to a particular latex package.

---

