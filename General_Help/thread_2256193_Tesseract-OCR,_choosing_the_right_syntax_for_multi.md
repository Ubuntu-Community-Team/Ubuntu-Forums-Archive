---
title: "Tesseract-OCR, choosing the right syntax for multiple .jpg"
date: 2014-12-10
forum: General Help
---

### Post by b-12-3838 on 2014-12-10
Hi,

i have 12 jpg in my folder /home/user/Downloads/PDF JPG/
with the name "page_0000.jpg" to "page_0011.jpg".

Now i want to convert them all at once to a OCR-PDF.

```
tesseract -l deu page_0000.jpg finalOCR pdf 
```

works fine for 1 jpg image. But how do i need to choose the syntax that tesseract chooses all pages at once from 0-12 or better from 0 to infinite page numbers?

Thanks in advance!

---

### Post by b-12-3838 on 2014-12-11
It simply means that i need the syntax to tell the terminal to take all JPG's that are in the folder /home/user/Downloads/PDF JPG/  How can i express it that it takes all files named with page_%.... ?

---

