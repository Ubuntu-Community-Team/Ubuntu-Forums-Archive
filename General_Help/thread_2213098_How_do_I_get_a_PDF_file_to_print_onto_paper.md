---
title: "How do I get a PDF file to print onto paper?"
date: 2014-03-24
forum: General Help
---

### Post by secuono on 2014-03-24
I am not wanting a PDF file to print to file, I want it to actually print the pages I am seeing in Adobe document viewer.

---

### Post by pqwoerituytrueiwoq on 2014-03-24
you need to install/setup your printer, if you press ctrl+p in firefox and don't see your printer in the list open you printer settings and add you printer

---

### Post by HermanAB on 2014-03-25
You can just send the file to the printer.  The CUPS system natively handles PDFs and many other file types.

This will print on the default printer:
$ lpr filename.pdf

This will print on a printer connected to another machine:
$ lpr -H ipaddress filename.pdf

---

