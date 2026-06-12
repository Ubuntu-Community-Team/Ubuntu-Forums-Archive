---
title: "[SOLVED] How to create PDF docs from any office app or a browser"
date: 2008-01-24
forum: General Help
---

### Post by MountainX on 2008-01-24
In MS Windows I was using Adobe Acrobat to create PDF documents. One feature I really liked was the toolbar which allowed me to create a PDF document from almost any app I was working in. For example, I could save any web page as a PDF. I found this much better than the more common browser implementation of saving as a collection of images in a folder matched to an html file, for example. I could also save any email message from Outlook as a PDF using these toolbar buttons from Acrobat. I standardized all my doc storage to the PDF format.

How can I achieve something similar in Ubuntu?

Also, how can I **scan** to PDF files from an HP Officejet Pro L7680 (over ethernet)? In MS WIndows, the HP Solution center has this feature (but the basic HP driver does not fully implement the same thing).

Thanks.

---

### Post by Steveway on 2008-01-24
You can print to PDF. This works with every app that can print to a printer.
How can this be any more easy?

---

### Post by stchman on 2008-01-24
> **MountainX said:**
> In MS Windows I was using Adobe Acrobat to create PDF documents. One feature I really liked was the toolbar which allowed me to create a PDF document from almost any app I was working in. For example, I could save any web page as a PDF. I found this much better than the more common browser implementation of saving as a collection of images in a folder matched to an html file, for example. I could also save any email message from Outlook as a PDF using these toolbar buttons from Acrobat. I standardized all my doc storage to the PDF format.

How can I achieve something similar in Ubuntu?

Also, how can I **scan** to PDF files from an HP Officejet Pro L7680 (over ethernet)? In MS WIndows, the HP Solution center has this feature (but the basic HP driver does not fully implement the same thing).

Thanks.

Openoffice has an export to PDF function built in.  If you want to create PDFs from any application use the cups-pdf package.  It is a print to PDF function.  I have a tutorial detailing it.

[http://www.stchman.com/pdf_cups.html](http://www.stchman.com/pdf_cups.html)

---

### Post by nemilar on 2008-01-24
CUPS, the printing system, has a driver that allows you to print anything to PDF.  Here is a tutorial that shows step-by-step (with screenshots) how to install and configure the Print-to-PDF driver:

[http://www.techthrob.com/tech/print2pdf.php]("http://www.techthrob.com/tech/print2pdf.php")

I hope that helps, and you get everything working!

Cheers!

---

### Post by eidauk on 2008-02-04
For some reason the tutorial didn't work for me. Nothing was showing up in the PDF directory after attempting to print to a PDF. I solved it by purging cups-pdf, then reinstalling. To my surprise it automatically created a printer named "PDF". However, I did have to create a ~/PDF directory.

---

