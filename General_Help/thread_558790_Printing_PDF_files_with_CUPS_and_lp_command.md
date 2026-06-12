---
title: "Printing PDF files with CUPS and lp command"
date: 2007-09-24
forum: General Help
---

### Post by mail480697 on 2007-09-24
HI -- I'm new to CUPS and want to print a PDF file.  The PDF is a
large format (12" x 18") and I want to print it on standard "Letter"
size paper (8 12" x 11").  So far, no luck.  Here's what I've tried:

1. lp my.pdf

===> printer asks for 12 x 18 paper, I walk to the printer and tell printer to use standard
letter stock.  Only the top left corner is printer (expected) BUT the
printout is enlarged by a factor of eight or so

2. lp -o media=letter my.pdf

===> same results as above (printer still asks for 12x18" paper)

3. lp -o media=letter -o fitplot my.pdf

===> printer still asks for 12 x 18 paper, I tell printer to use
standard letter stock.  All I get is one blank page


I'm not sure what to try next, but it's a bit frustrating at this
point.  Hope someone can help.

Oh, btw the printer is an HP 9040mfp

---

### Post by quixotic-cynic on 2007-09-25
I can't help with lp but you could try using the xpp package - if you can install it.

Which drivers are you using for the HP printer? It's probably best to use hplip - which you can set up with the command ```
sudo hp-setup
``` after installing the package. In xpp you have to check the option "Fit pdf/plot to page" to achieve what you intend.

Edit: I would have thought your 3rd attempt would have worked too.

---

### Post by astx813 on 2008-01-17
I'm having a similar problem, though completely different.  In my case I'm trying to print address-size labels that have been generated as PDFs with fpdf.php.  See an example at [http://law.wustl.edu/gant/label.pdf]("http://law.wustl.edu/gant/label.pdf").  I can print from Evince (Document Viewer), but first I have to go into page setup and set "Format for:" to my label printer and "Paper size:" to the label size.  If I don't do that first, or if I print with lpr (which is what I need to be able to do in the end), it cuts off the top 1/2 of the first line and bottom of the last line.  Any thoughts what Evince is doing when I tell it to "format for" and how I can pull that off at the command line?

Oh, and I checked, it's not simply scaling the text.  The image and the text that isn't cut off lines up perfectly with a properly printed label.  It's just forcing some narrower margin on it or something.

**Edit: ** Looked into a comprehensive list of options for lp/lpr and found lp -dDymo_Labeler -o media=Address (one of the pagetypes in the ppd) label.pdf  Still no good, prints exactly the same way.  This is driving me nuts.

---

