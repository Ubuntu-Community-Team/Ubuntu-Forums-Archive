---
title: "Problems with Latex and latin-1"
date: 2005-09-12
forum: General Help
---

### Post by Midget on 2005-09-12
I am having problems with Latex and the charset latin-1 (norwegian). I can't generate a .dvi without latex giving me lots of errors.

This is the document:
```

\documentclass[12pt, a4paper]{article}
\usepackage[norsk]{babel}
\usepackage[latin1]{inputenc}
\usepackage[T1]{fontenc}

\begin{document}

æøå ÆØÅ

\end{document
``` 

The output of the command *latex <file>* can be found [here](http://temp.nerdinne.net/pus.log) 

Any help will be appreciated :)

---

### Post by Midget on 2005-09-12
[QUOTE=Midget]I am having problems with Latex and the charset latin-1 (norwegian). I can't generate a .dvi without latex giving me lots of errors.[/QUOTE]

I just love to answer my own posts. Latex is now working. I installed the following packages:

tetex-base
tetex-bin 
tetex-doc 
tetex-extra 
texi2html 
texinfo 
vim-latexsuite

I think installing only tetex-extra will be sufficent :)

---

