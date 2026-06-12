---
title: "pdflatex under v7.10 fails!!!"
date: 2008-01-15
forum: General Help
---

### Post by amaragon on 2008-01-15
Hi everyone, I didn't know where to report this problem so I apologize if this is not the right place.
I migrated to v7.10 and pdflatex stopped working when including files in the mps format. You get an error message like this:

./template-num.tex:429:Package graphics Error: Cannot convert figures/a.mps from MPS toPDF. ...cludegraphics[scale=1.00]{a}

I checked the .log file and I found out that there was a .tex file with macros missing. The needed files are actually compressed under the directory /usr/share/doc/texlive-doc/pdftex/manual/samplepdf/

I decompressed files supp-mis.tex and supp-pdf.tex in my working directory and now I can use pdflatex again. Is this something that can be fixed in the 7.10 distribution?

a²

---

