---
title: "gocr command line. What's wrong with this?"
date: 2014-04-05
forum: General Help
---

### Post by MadMax2 on 2014-04-05
I  want to convert pdf to text.
I open in libre office draw and *Save As* .pbm

gocr -i a.pbm -o a.txt
Thanks

---

### Post by sudodus on 2014-04-05
The program ***pdftotext*** is probably installed with your Ubuntu. If not, it can be installed easily.

See ```
man pdftotext
``` or

[http://linux.die.net/man/1/pdftotext](http://linux.die.net/man/1/pdftotext)

---

### Post by MadMax2 on 2014-04-05
Thanks for that
Example:
cd Documents
cd A
ls
pdftotext b.pdf b.text

---

### Post by sudodus on 2014-04-06
If you are happy with the solution, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED.

---

