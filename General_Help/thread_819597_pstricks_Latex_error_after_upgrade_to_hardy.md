---
title: "pstricks Latex error after upgrade to hardy"
date: 2008-06-05
forum: General Help
---

### Post by litmos95 on 2008-06-05
Hi everyone,

i got error message when using the package pstricks. This didn't happen when I still used ubuntu feisty. I used texmaker with quick build command: Latex + dvips + ps2pdf + view PDF.

The error message:
```

File: pstricks.tex 2006/12/22 v1.15 `PSTricks' (tvz)
(/usr/share/texmf/tex/latex/xcolor/xcolor.sty
Package: xcolor 2007/01/21 v2.11 LaTeX color extensions (UK)
Package xcolor Info: Package option `override' ignored on input line 216.
! Package xcolor Error: No driver specified.
See the xcolor package documentation for explanation.
Type H <return> for immediate help.

```

The example document:
```

\documentclass[10pt,a4paper]{book}
\usepackage[latin1]{inputenc}
\usepackage{pstricks}
%\usepackage{xcolor}
\begin{document}
asd asd
\end{document}

```

I have tried to reinstall texmaker, texlive-pstrics, and xcolor but no result. Please help, I need to finish my thesis.

Thanks in advance

---

### Post by litmos95 on 2008-06-05
OK I solved it, someone from CQF.info told me to specify the driver when loading packages. So I load pstricks this way: 

```

\usepackage[dvips]{pstricks}

```

It works now. I didn't encounter this problem when still using feisty. It's strange....

---

### Post by manech on 2009-08-09
I just want to post something I found out, as a pstricks newbie:

If you get an error like: "Undefined control sequence \psline" in Kile, this is problably because you are trying to use pstricks with pdflatex.

You can avoid this messages if you include the package using dvips:
\usepackage[dvips]{pstricks}

But using pdflatex you will not get the desired results. A better solution is to create a ps or dvi instead, and then convert it to pdf for example with ps2pdf.
See [http://tug.org/PSTricks/main.cgi?file=pdf/pdfoutput](http://tug.org/PSTricks/main.cgi?file=pdf/pdfoutput)

---

### Post by TjabbeTjibsma on 2009-08-11
> **manech said:**
> I just want to post something I found out, as a pstricks newbie:

If you get an error like: "Undefined control sequence \psline" in Kile, this is problably because you are trying to use pstricks with pdflatex.

You can avoid this messages if you include the package using dvips:
\usepackage[dvips]{pstricks}

But using pdflatex you will not get the desired results. A better solution is to create a ps or dvi instead, and then convert it to pdf for example with ps2pdf.
See [http://tug.org/PSTricks/main.cgi?file=pdf/pdfoutput](http://tug.org/PSTricks/main.cgi?file=pdf/pdfoutput)

Excellent comment! Exactly the solution to my problem! I was trying to get 'sketch' to work (an excellent tool to go 3D with you LaTeX drawings) and noticed that only when I coded it in TikZ it would work. Your solution got me going again!

---

