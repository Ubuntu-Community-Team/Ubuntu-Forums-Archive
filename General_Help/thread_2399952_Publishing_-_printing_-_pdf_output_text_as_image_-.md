---
title: "Publishing - printing - pdf output text as image - block searching of text"
date: 2018-08-31
forum: General Help
---

### Post by nicolasdiogo on 2018-08-31
Hello,


I have to make a submission of a PDF file, but I am trying to create an electronic file that does not support/allow for the text to be searched.

One way would be to physically print once and re-scan as a single file.

As Ubuntu is such a flexible tool - surely, there must be a way of doing this directly.

My document is currently a LibreOffice (massive document) with 600 pages and extensively cross-referenced.


The requirement is for:

- printing this LibreOffice Writer documents as a PDF with 600 pages containing 'images' of the pages instead of the actual 'text' in the pages
- this would block the search facility to find anything
- or, some other PDF that does not lend itself to be searched for the text contained within


Is there a way to achieve this in Ubuntu/Linux?

thanks a Lot !!

---

### Post by ajgreeny on 2018-08-31
You give us no info about the printer you use nor the version of Ubuntu but this problem has been mentioned before.

Perhaps the ideas in these two threads will help you.
[https://ubuntuforums.org/showthread.php?t=2355677](https://ubuntuforums.org/showthread.php?t=2355677)
[https://ubuntuforums.org/showthread.php?t=2220257](https://ubuntuforums.org/showthread.php?t=2220257)

You could also try opening the PDF document with another PDF reader such as qpdfview, xpdf or even okular and printing from that, though that latter app will pull in a lot of kde libs and other dependencies which you may prefer to avoid.

---

### Post by Holger_Gehrke on 2018-08-31
I assume the reason for your question is similar to the situation posted in this [blog at adobe]("https://blogs.adobe.com/acrolaw/2008/04/creating_a_nonsearchable_pdf_fro/") ...
so with the same misgivings as the poster of that blog (image pdf-files are large, ugly and pulling them apart again and running them through OCR to make them searchable is no big thing) here is a solution:


[LIST=1]
[*] Export a normal pdf from LibreOffice and save it as "text.pdf" in a new empty directory 
[*]Open a terminal and change to that directory 
[*]If ImageMagick is not installed on your system, install it with 'sudo apt install imagemagick' 
[*]Break the pdf into pages using 'convert -density 200 text.pdf -quality 75 page-%03d.jpg' (the value 200 after '-density' is the density to render the pages at in pixel per inch, the value 75 after -quality is a compression factor - lower value=higher compression but worse images) 
[*]Rejoin the pages into a new pdf with 'convert *.jpg images.pdf" 
[*]Erase the text.pdf and the pages with 'rm text.pdf *jpg' 
[/LIST]

Holger

---

