---
title: "pdflatex Uses Wrong Page Size"
date: 2013-08-19
forum: General Help
---

### Post by xanderp123 on 2013-08-19
I have a perplexing problem and I've tried everything that I can think of to fix it. I'm writing a paper for an IEEE conference. I am compiling the IEEEtran testflow document to test my LaTeX setup. When I compile the document using pdflatex, the text is formatted according to letter dimensions, but the page is A4 size. I'm using the texlive distribution from the Ubuntu 13.04 (Raring) repositories.

I've tried everything I can think of to fix it, including completely re-installing texlive from the repositories. I've tried "sudo tl-paper set all letter" but that doesn't work either. I expect that there is a residual config file somewhere from a previous installation of texlive that I just cannot find. Any help is greatly appreciated!

---

### Post by xanderp123 on 2013-08-19
I finally found the problem after a couple hours of searching: removing the ~/.texmf-var/ directory worked.

---

