---
title: "Combining PDF files [Resolved]"
date: 2007-04-16
forum: General Help
---

### Post by freebeer on 2007-04-16
Hi folks!

Is there any way to combine multiple PDF files into a single file?  I can successfully import the PDF files into Kword, but when I do, it wants to create a second instance/window in Kword of the file, rather than combining them into a single document.

I don't need to use Kword, per se - I just know that it can import PDFs.  I'm looking for any means to combine them such that in the end I have all the PDF files into one document (eventually in PDF format) so that I can email it, archive it, etc.  Kinda like a .zip or .rar file, but in PDF format.

Thanks in advance for any ideas or shots-in-the-dark.  :D

---

### Post by jdong on 2007-04-16
Try using pdftk (in Universe)

IIRC the command is something like **pdftk input-1.pdf input-2.pdf cat output combined.pdf** but don't quote me on that :D

---

### Post by freebeer on 2007-04-16
Thanks!  I'll give that a try!


minutes later.....


That worked just fine!  Thanks!

---

### Post by noynac on 2007-04-16
> **jdong said:**
> Try using pdftk (in Universe)....

Thanks! I've been looking for a way to combine individual PDF's, and PDFtk works great. Also, it supports wild cards for the input files, which makes it easy to combine all PDF files in a directory.

---

### Post by ramjet_1953 on 2007-04-17
You can also use a GUI package called pdfEdit.

Check out this link:

[http://ubuntuforums.org/showthread.php?t=366470](http://ubuntuforums.org/showthread.php?t=366470)

Regards,
Roger :)

---

### Post by artesian_spring on 2008-01-01
> Try using pdftk (in Universe)

IIRC the command is something like pdftk input-1.pdf input-2.pdf cat output combined.pdf but don't quote me on that 

Works great. Thanks! I'm sure my email recipients will be happy to have fewer attachments to open, too.

---

