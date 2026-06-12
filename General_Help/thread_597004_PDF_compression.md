---
title: "PDF compression"
date: 2007-10-30
forum: General Help
---

### Post by John Deas on 2007-10-30
Hi,

I would like to know if it is possible to compress images inside a pdf, for example using the CUPS pdf printer, or maybe postprocessing an uncompressed pdf. I was used to do it with PDFCreator, but it does not exist on Ubuntu.

Thanks

JD

---

### Post by prankst3r on 2007-11-01
[http://sourceforge.net/projects/gscan2pdf]("http://sourceforge.net/projects/gscan2pdf") is your friend. It is a great replacement for PDFCreator or Paperport. I finally ditched XP and use gscan2pdf w/ Ubuntu exclusively for my paperless office - everything gets scanned to PDF.

The latest build allows you to set the JPG quality before it is packaged into the pdf file.

---

### Post by kevinfishburne on 2008-03-07
I had the same problem (and still do...somewhat) but found something that may be helpful. I searched the net for solutions and found none. I can't find any parameters to pass to pdfwrite (the GhostScript app that creates the PDF), or any sign that the script is capable of doing this.

If however you set the PDF printer's options to grayscale instead of color, the file sizes are *much* smaller. There is no option to do this in the printer admin panel, but when you actually go to print something to the PDF printer you can choose *Properties* for the printer.

---

