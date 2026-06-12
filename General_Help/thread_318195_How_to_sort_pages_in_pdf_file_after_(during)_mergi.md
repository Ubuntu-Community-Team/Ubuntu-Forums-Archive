---
title: "How to sort pages in pdf file after (during) merging them into one file?"
date: 2006-12-13
forum: General Help
---

### Post by amanita on 2006-12-13
When I merge pdf files into one  e.g ```
pdftk *.pdf cat output combined.pdf
``` the pages are mixed. I would like to know a way how is possible to sort them out (e.g. page no. 1 to 127, while 65,92,41 are missing) ?

---

### Post by meng on 2006-12-13
Are the individual files named in alphabetical order?

---

### Post by amanita on 2006-12-14
No, unfortunately they are not

---

### Post by meng on 2006-12-14
If it's possible for you to put these in order, perhaps using leading zeroes, then this might work for you.

---

### Post by kolesarm on 2007-01-22
you can do it with pdftk: [here]("http://www.accesspdf.com/article.php/20041129175231241") is how.

i think this is what you are looking for:
 pdftk A=one.pdf B=two.pdf cat A1-7 B1-5 A8 output combined.pdf

---

