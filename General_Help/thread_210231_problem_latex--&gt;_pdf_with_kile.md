---
title: "problem latex--&gt; pdf with kile"
date: 2006-07-06
forum: General Help
---

### Post by woot on 2006-07-06
I get the following errormessage:

[PDFLaTeX] thesis.tex => thesis.pdf (pdflatex)
[PDFLaTeX] finished with exit status 1
./thesis.tex:4:File `a4wide.sty' not found. \usepackage
[PDFLaTeX] 1 error, 0 warnings, 0 badboxes

and this one is causing it:
\usepackage{a4wide}

its not a specific kile problem I guess, the a4wide file is simply not on my system I assume. I just sudo apt-get kile...

perhaps I am missing some package?

---

### Post by wylfing on 2006-07-06
I use LaTeX all the time, so I feel foolish not being able to tell you exactly which packages you require, but try installing these:

tetex-base
tetex-bin
tetex-extra
latex-xft-fonts

---

### Post by woot on 2006-07-07
dont feel foolish :D you helped me out :) 

Funny google didnt gave me some solution...

---

### Post by zugvogel on 2006-11-06
Thanks for this information - this was very useful and helpful for me too!

---

