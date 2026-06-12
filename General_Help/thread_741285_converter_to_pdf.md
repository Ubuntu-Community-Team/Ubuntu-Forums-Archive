---
title: "converter to pdf"
date: 2008-03-31
forum: General Help
---

### Post by sayak on 2008-03-31
Is there any command line converter that takes any printable file as its argument and converts it to PDF

remember PDF and not PS

---

### Post by chilinski on 2008-03-31
There are several ways. One is to use convert or mogrify that are part of the Imagemagick suite. I think xpdf has a tool, also. OpenOffice can export to PDF.

I like the Imagemagick stuff because it can convert from almost anything to almost anything else and lets you do whole bunches of sweet things in the process. By the way, convert is a command line tool, so you do:

convert file.txt file.pdf

---

