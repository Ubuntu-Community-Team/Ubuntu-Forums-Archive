---
title: "kile PDFlatex build problem, after latest kubuntu update"
date: 2012-12-03
forum: General Help
---

### Post by nikosd on 2012-12-03
Running kile 2.1 on kubuntu, kernel 2.6.32-45-generic.
Always viewing pdf output in okular. 
kile was running smoothly for a long time. With last set of updates, kile does not build PDFlatex anymore. 
After trying to compile empty article file 
```

\documentclass[a4paper,10pt]{article}
\usepackage[utf8x]{inputenc}

%opening
\title{}
\author{}

\begin{document}

\maketitle

\begin{abstract}

\end{abstract}

\section{}

\end{document}

```output produces following warning
```

Cannot open log file; did you run latex?

```Log file contents:
```

*****
*****     PDFLaTeX output: 
*****     cd "/home/nikos/Desktop/kile-test"
*****     pdflatex -interaction=nonstopmode 'test-kile-2.tex'--shell-escape
*****
This is pdfTeX, Version 3.1415926-1.40.10 (TeX Live 2009/Debian)
entering extended mode
! I can't find file `test-kile-2.tex--shell-escape'.
&lt;*&gt; test-kile-2.tex--shell-escape
                                 
(Press Enter to retry, or Control-D to exit)
Please type another input file name
! Emergency stop.
&lt;*&gt; test-kile-2.tex--shell-escape
                                 
!  ==&gt; Fatal error occurred, no output PDF file produced!
Transcript written on texput.log.

```Tried removing texlive, tex-common, and kile and reinstalling from command line, to no avail. 
Different build methods work, for example LaTeX+DVItoPDF+ViewPDF produces proper pdf output. 

What is going on?

I also posted this in [http://latex-community.org/forum](http://latex-community.org/forum), hope it's ok

thanks, nd

---

