---
title: "Printing"
date: 2007-06-19
forum: General Help
---

### Post by Howard Kaikow on 2007-06-19
In gedit, there are 3 options for printing:

Create a PDF document
Generic Postscript
Optra-E312

No trouble printing either a PDF file, or to the Optra-E312 printer.

However, I can only pringtGeneric Postscript to a file.
When I try printing Generic Postscript to lpr, nothing appears to happen.
The printer will automatically detect Postscript, so I should be able to print Postscript directly to the printer.

Is this a Linux driver problem?

---

### Post by rbmorse on 2007-06-19
For me, woking in Gedit:

print > Generic Postscript 

results in a printed page from my HP 2605DN. Everything appears to be working normally.

---

### Post by Howard Kaikow on 2007-06-19
> **rbmorse said:**
> For me, woking in Gedit:

print > Generic Postscript 

results in a printed page from my HP 2605DN. Everything appears to be working normally.

OK, then it's a problem with the drivers for the Lexmark Optra-312.

How can I tell whether I have the latest drivers?
I ran an update about 2 daze ago.

---

### Post by Howard Kaikow on 2007-06-20
Should I install [Lexmark Debian GNU drivers]("http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:140:0:0&emeaframe=&fileID=9315&searchLang=en&os_group=Debian%20GNU")?

Do I have to redefine the printer after installing such drivers?

---

### Post by Howard Kaikow on 2007-06-20
What version of linux is Feisty (7.04)?

The Lexmark Debian drivers are for versions 3.0 and 3.1.

---

### Post by blackspyder on 2007-06-20
the Open printing database says to use the Postscript Driver. Feisty is version 7.04. 

I think this is the page for your printer. [http://openprinting.org/show_printer.cgi?recnum=Lexmark-Optra_E312](http://openprinting.org/show_printer.cgi?recnum=Lexmark-Optra_E312)

---

### Post by Howard Kaikow on 2007-06-20
> **blackspyder said:**
> the Open printing database says to use the Postscript Driver. Feisty is version 7.04. 

I think this is the page for your printer. [http://openprinting.org/show_printer.cgi?recnum=Lexmark-Optra_E312](http://openprinting.org/show_printer.cgi?recnum=Lexmark-Optra_E312)

Thanx.

As I understand it, I would click the Install Driver button and locate the file..

---

### Post by Howard Kaikow on 2007-06-20
Is there a directory in which I should put the PPD, in case linux wants to to later locate the file?

---

### Post by rbmorse on 2007-06-21
/usr/share/ppd   

should work. You need  root to write there. 

RBM

---

### Post by Howard Kaikow on 2007-06-21
> **rbmorse said:**
> /usr/share/ppd   

should work. You need  root to write there. 

RBM
Thanx.

Here's what I found out and did.

1. Inspecting the printer properties.linux used an Optra E driver and I saw no driver for the Optra E312.

2. I installed the driver from Adobe.

This resulted in the PPD being added in /var/share/ppd/custom.
Seems that linux should include more lexmark stuff for th installed PPDs.

Result was that the lpr printer choice was elimated and replaced by a POstscript printer, tho linux still does not allow me to send Postscript directly to lpr.

In Firefox, and Thunderbird, the printer choices are now:

CUPS/Opera-312
Postscript/Default

Both produce Postscript output.

In Gedit, the choices are now:

Create a PDF Document
Generic Postscript
Optra-E312

So, there are three questions:

1. How do I get the "Create a PDF Document" option in Firefox and Thunderbird?
2. How can I copy raw Postscript to the printer?

3. Am I better off now than I was before installing the Adobe PPD?

---

### Post by Howard Kaikow on 2007-06-21
> 
So, there are three questions:

1. How do I get the "Create a PDF Document" option in Firefox and Thunderbird?
2. How can I copy raw Postscript to the printer?

3. Am I better off now than I was before installing the Adobe PPD?

I guess that I can solve item 1 by installing CUPS-PDF.

---

