---
title: "[SOLVED] How to Combine multiple PDFs into One"
date: 2008-04-18
forum: General Help
---

### Post by Anthony M on 2008-04-18
I have installed pdfedit but cannot figure how how to combine multiple PDF files into one large file. Is there any other way to do this?

Thanks!

---

### Post by mali2297 on 2008-04-18
You can use [Pdftk]("http://www.accesspdf.com/pdftk/"), it's a simple command line tool. To install, use Synaptic.

If you want to merge Example1.pdf and Example2.pdf into Example3.pdf, type
```

pdftk Example1.pdf Example2.pdf cat output Example3.pdf verbose

```
in the terminal. (The *verbose* part is optional but tells the program to give you more feedback.)

---

### Post by Anthony M on 2008-04-18
Worked perfect!

---

### Post by skoalman88 on 2008-05-10
Works very well. Thanks

---

