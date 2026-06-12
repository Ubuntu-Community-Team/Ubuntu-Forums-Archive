---
title: "Combining pdf files from multiple directories in alphabetical order"
date: 2018-12-21
forum: General Help
---

### Post by flucoe2 on 2018-12-21
I have a directory with multiple sub-directories that contain pdf files of job applicants. The files in each subdirectory are Lastname_cv.pdf, Lastname_letter.pdf, and other files that I don't need at this point. I want to combine all the pdfs that refer to applicants' cv and letter, in alphabetical order, with the cv of each applicant first, and the letter second. So, an example would be having two subdirectories A  and B, where in A I have A_cv.pdf and A_letter.pdf; in B I have B_cv.pdf and B_letter.pdf. Is there a way in which I can combine all these files so that I get a single file All_documents.pdf that has the files just mentioned in the order A_cv, A_letter, B_cv, B_letter?

I'm using Ubuntu 18.04.

Thanks

---

### Post by dragonfly41 on 2018-12-21
I can think of two approaches to try ..

(a) install pandoc and then use command line to concatenate files of a given type.

e.g.  [https://gist.github.com/xuanlongma/5564190](https://gist.github.com/xuanlongma/5564190)

(b) PDFshuffler in Software Centre

---

### Post by flucoe2 on 2018-12-21
Thanks for the suggestions. I ended up using pdftk. I first copied all relevant files into a temporal directory (using cp ../Applications/*/*_cv.pdf . and cp ../Applications/*/*_letter.pdf .) and then I combined them using pdftk (pdftk *.pdf cat output all_applicants.pdf)

---

### Post by HermanAB on 2018-12-22
I use pdfshuffler for these kind of jobs.

---

