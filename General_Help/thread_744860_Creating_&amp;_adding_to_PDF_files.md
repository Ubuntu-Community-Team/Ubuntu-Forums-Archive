---
title: "Creating &amp; adding to PDF files"
date: 2008-04-04
forum: General Help
---

### Post by binder74 on 2008-04-04
I'm currently using Adobe Acrobat 5.5 & XP to create PDF files from my incoming email  .  I've tried using the CUPS/PDF to print to file which works fine, but I haven't found a way to add additional pages to the file once it has been created.  Adobe lets me open a file and add or delete pages.  I want to switch to ubuntu if I can solve this problem, otherwise, I'm stuck with XP.

---

### Post by mali2297 on 2008-04-04
You can use [Pdftk]("http://www.accesspdf.com/pdftk/"), it's a simple command line tool. To install, use Synaptic.

If you want to merge Example1.pdf and Example2.pdf into Example3.pdf, type
```

pdftk Example1.pdf Example2.pdf cat output Example3.pdf verbose

```
in the terminal.

If you want to create Example4.pdf from Example3.pdf without pages 2 and 6, type
```

pdftk Example3.pdf cat 1 3-5 7-end output Example4.pdf verbose

```
(The *verbose* part is optional but tells the program to give you more feedback.)

---

### Post by sekinto on 2008-04-04
There are a multitude of tools available for this:
joinPDF, pdfmeld, Ghostscript, et cetera...

---

