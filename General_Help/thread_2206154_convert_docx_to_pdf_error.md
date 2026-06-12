---
title: "convert docx to pdf error"
date: 2014-02-17
forum: General Help
---

### Post by imh on 2014-02-17
Hi, 

I've been using libreoffice on the command line to convert documents to pdf.  On Ubuntu 10.04.4 LTS using LibreOffice 4.0.2.2 I do:

libreoffice --headless -convert-to pdf document.docx

It gives me:

convert /home/ivan/document.docx -> /home/ivan/document.pdf using writer_pdf_ExportError: Please reverify input parameters...

I have a hunch it has something do with there being images in the file as it works for most other documents. It also works fine on another computer using libreoffice 3.5

Any ideas? Thanks!

---

### Post by mindylynn0 on 2014-10-20
Time pass by, have you found a solution for [[COLOR=#333333]pdf file conversion[/COLOR]]("http://www.pqscan.com/pdf-to-image/")? Recently, i met the similar issue. If you still haven't find a solution, maybe i'd better switch to other [[COLOR=#333333]pdf conversion tools[/COLOR]]("http://www.pqscan.com/online-demo/pdf-to-image/").

---

### Post by sudodus on 2014-10-20
Welcome to the Ubuntu Forums :-)

Does it work for you to open the docx file in LibreOffice?

---

### Post by mindylynn0 on 2014-10-21
Thanks for your quick reply. I only met the conversion issue. Maybe i need to have a try again to see the result.

---

### Post by sudodus on 2014-10-21
My experience is that if LibreOffice can open a file and render it correctly, it can also make a good pdf-file from it

- manually by selecting 'File -- Export as PDF'
- automatically with the --headless option

But there are cases, where the formatting is such that LibreOffice does not understand it (it does not manage 100% or Microsoft's formatting options).

---

### Post by coffeecat on 2014-10-21
Unusual topic for the Multimedia sub-forum, so...

*Thread moved to **General Help**.*

---

