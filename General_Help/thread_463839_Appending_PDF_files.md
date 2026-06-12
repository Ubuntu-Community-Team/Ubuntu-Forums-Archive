---
title: "Appending PDF files"
date: 2007-06-04
forum: General Help
---

### Post by neilrizo on 2007-06-04
Is there a way to add another page to an existing PDF file?

Or, for that matter, combining two formats (e.g. word and dwg files) into one PDF file?

Help!

---

### Post by vanadium on 2007-06-04
pdftk is a command line utility that you can obtain using Synaptic. To join two PDF's, it sounds like

pdftk in1.pdf in2.pdf cat output out1.pdf

From the help: > If PDF is electronic paper, then pdftk is an electronic staple-remover, hole-punch, binder, secret-decoder-ring, and X-Ray-glasses.  Pdftk is a simple tool for doing everyday things with PDF documents.

---

### Post by neilrizo on 2007-06-07
> **vanadium said:**
> pdftk is a command line utility that you can obtain using Synaptic. To join two PDF's, it sounds like

pdftk in1.pdf in2.pdf cat output out1.pdf

From the help:

this is great, thank you for the reply! 

but since this only joins pdf files is there an ubuntu program that joins different file types? something like FinePrint pdfFactory?

[http://www.fineprint.com/products/pdffactory/index.html](http://www.fineprint.com/products/pdffactory/index.html)

---

### Post by ramjet_1953 on 2007-06-08
Here's a link to download the pdfedit package:

[http://www.getdeb.net/](http://www.getdeb.net/)

Regards,
Roger :cool:

---

### Post by neilrizo on 2007-06-08
> **ramjet_1953 said:**
> Here's a link to download the pdfedit package:

[http://www.getdeb.net/](http://www.getdeb.net/)

Regards,
Roger :cool:


i'll try this out right now.

thanks!

---

### Post by Mujaheiden on 2007-06-14
I like pdftk, but why isnt there a gui?

---

