---
title: "PDFs print all black"
date: 2016-06-23
forum: General Help
---

### Post by 1clue on 2016-06-23
Hi,

I'm using Ubuntu 15.10. Printer is a networked Canon color laser all-in-one, ImageClass MF8050Cn.

ALL pdfs print a 100% black page.

The same exact PDF scp'd to a mac will print fine.

I see from Google that others have this problem and fix it by using the Adobe print dialog, but that seems to be not available anymore.

I've tried:
[LIST=1]
[*]Default document viewer
[*]Print preview
[*]Libre Office
[*]xpdf
[*]lpr (command-line print)
[*]Adobe Acrobat is no longer available for Linux.
[/LIST]

Does someone have a solution for this?

Thanks.

---

### Post by ajgreeny on 2016-06-23
Do you mean a big black oblong covering the whole page or just that the text prints in b/w only, not colour as you want?

I suspect the former but just checking.

Have you tried printing from another PDF viewer, eg **okular** (yes, I know it's a KDE app, but it is very good) or qpdfview; I sometimes find that evince plays tricks when printing certain pdf files, but does others fine. Occasionally it has refused to print a pdf totally using evince and my printer (HP Deskjet F2180 MFP) just sits unmoved by my instructions, but using qpdfview that pdf prints fine.

---

### Post by 1clue on 2016-06-23
I mean an entire black rectangle covering the entire page. With the exception of what looks like 6 pages maybe 1" by 0.75". The document I'm most interested in has 3 pages.

I'll try okular, but IMO this is not a problem with the viewer.  Diverse apps including lpr <pdf-name> which has no gui issue.

The PDFs look good in any viewer, with the exception of xpdf which is evidently not using good fonts.

Come to think of it I may not try okular.  It looks like it wants to install most of the kde backend. I don't want that kind of bloat.

I tried qpdfview. It has the same issue. Completely black toner out to less than 1/8" on sides and bottom, tiny thumbnails of the document (actually 8 of them) on the very top.

Thanks for your time.

---

### Post by SeijiSensei on 2016-06-23
Can you configure the printer to use Postscript and choose a Postscript driver in CUPS?

---

### Post by 1clue on 2016-06-23
[ATTACH=CONFIG]269746[/ATTACH]

---

### Post by 1clue on 2016-06-23
This printer does not work with a standard postscript driver.  It's Canon, needs their specific software. I fought off and onfor years to get this thing to work on Linux.

---

### Post by raphaeldc on 2016-09-28
Did you find any solution to this problem? I'm having the same issue. Installed Acrobat Reader, but I still have black backgound and white fonts.

---

### Post by 1clue on 2016-09-28
No.

At the moment I need to send it to a mac or pc in order to print a pdf.

---

### Post by norikd on 2017-02-13
I know its a relatively old thread... but in case anyone finds themselves here with the same issue.

Using the printers applet in the Systems Settings, add the printer as a Generic printer instead of Canon and then choose a PCL6 driver. "Generic PCL 6/PCL XL Printer Foomatic/pxlcolor" worked for me with Ubuntu 16.10.

---

### Post by 1clue on 2017-02-13
What do you use for device uri?

Are you using it as a networked printer?

---

### Post by sjponder on 2017-04-23
Hi, I found that I have two pdfs, one will print fine, and the other, black, just as shown earlier in this thread..

I have a canon mf212

The file I included prints fine, using the lpr command. 

I have many others which print black, look below and see if I was allowed to upload it.


Description:	Ubuntu 16.04.2 LTS
Release:	16.04
Codename:	xenial

---

### Post by sjponder on 2017-04-23
I cannot upload the example pdf because of its size. It's about 10 times the size of the pdf previously attached, but is only one more page in length. Also, both are black and white. So, I am guessing this is obliquely related to filesize/resolution/encoding.

---

### Post by ippsatsi on 2017-11-02
Hi i have Canon IR1730, I also printed pages in black, when they were scanned pages,
with  the Canon driver "linux-UFRII-drv-v340.tar.gz", a utility called **cngplp**  is installed, run it in a terminal and check the option within special  options, "Correct print data (including By N" ). With that, solve it.[ATTACH=CONFIG]277384[/ATTACH]

---

### Post by oldos2er on 2017-11-02
Please don't bump old threads.

Closed.

---

