---
title: "Odd printing problem"
date: 2008-03-24
forum: General Help
---

### Post by TexLogic on 2008-03-24
A friend using Feisty is having an odd printing problem.  She has a Brother 2040 laser printer.  She is able to print PDF documents just fine, and the the Ununtu test page (from the printer setup menu) prints perfectly.  However, if she prints from OpenOffice or Firefox, there is a large piece of whitespace at the top of each printed page.  If she chooses Page Preview before printing, the whitespace does *not* appear in the preview *and* if she saves an OO file or a web page to PDF the PDF file prints normally.  Since the test page is postscript, the problem therefore does not appear to be a difference between PDF and postscript documents.  The printer driver that Ubuntu is finding for this printer seems to be correct.

Any ideas?  This one has me stumped.

TexLogic

---

### Post by cdenley on 2008-03-24
Is it a spreadsheet? I was having the same problem, and it happened in Ubuntu or Windows with Office 2007.

---

### Post by TexLogic on 2008-03-27
> **cdenley said:**
> Is it a spreadsheet? I was having the same problem, and it happened in Ubuntu or Windows with Office 2007.

It might happen with OpenOffice spreadsheets as well, but it in fact happened with an OO word processing document.  It also happens when she tries to print any page from Firefox.

---

### Post by cdenley on 2008-03-27
Sounds like a different problem then. I had a spreadsheet that wouldn't print correctly to any printer from any computer (Windows or Linux) unless it was first saved as a PDF.

You can try editing the .ppd file you have configured for the printer, but that gets a little tricky. Is there an alternative driver you can choose?

---

### Post by fredbird67 on 2008-04-17
TexLogic, I too am having the same problem.  I tried copying and pasting the text from that web page into Abiword and printing it from Abiword, and it looked just fine there, but not on Firefox.  Me thinks something fishy is going on here...

---

