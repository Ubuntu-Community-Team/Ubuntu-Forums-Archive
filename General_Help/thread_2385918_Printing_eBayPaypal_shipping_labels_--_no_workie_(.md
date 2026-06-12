---
title: "Printing eBay/Paypal shipping labels -- no workie (from 16.04 LTS desktop &amp; Firefox)"
date: 2018-02-26
forum: General Help
---

### Post by Ronald_F._Guilmett on 2018-02-26
I'm using 16.04 LTS.

Am I the only one who has had problems printing eBay/Paypal shipping labels?

The story is simple:  I log in to eBay, using Firefox (58.0.2) and I request to print a shipping label for am item of mine that sold recently.  A new page opens in a new browser tab, just like normal, and it has an image of my shipping label on it along with a button labeled "Print label".  So I click that... like I've done hundreds of times before... and after a short pause my Brother MFC-7860DW starts to hum, just as it normally does when it is about to print, and then out pops a printed page that just says:

ERROR NAME:
     stackunderflow
COMMAND:
     pop
OPERAND STACK:

and that's it.

Now, obviously, one of the following three things must have gone wrong:

1)  eBay's partner (Pitney Bowes) that generates the shipping labels screwed up somehow when they generated the PDF or postscript for my label (unlikely).

2)  My Brother MFC-7860DW printer screwed up when attempting to interpret the document that was sent to it (also unlikely).

3)  Whatever Ubuntu in-built software was/is responsible for transmogrifying these specific documents (i.e. eBay/Payal shipping labels) into something that will be understood by my printer screwed up the document before it was actually sent to the printer.

Can anyone tell me which of the above three possibilities is actually the one causing the problem, AND (I hope) how to fix this issue?

One more question while we are on the subject... This specific printer, Brother MFC-7860DW is one of these new-fangled "multi personality" printers. It has some default language (I'm not even sure what that is) but it also implements something called "BRScript3" which is apparently Brother's own version of a Postscript interpreter.... one which I am guessing that they built themselves, from scratch, in order to avoid having to pay someone else royalties for a Postscript interpreter.

Anyway, as far as my Windoze 7 system is concerned, this networked printer shows up on the list of printers as ***two ***printers... one just called "Brother MFC-7860DW" and another one named "Brother MFC-7860DW BRScript3".  But with Ubuntu (16.04LTS) this same printer only shows up as the one printer, "Brother MFC-7860DW".  So, the obvious question:  Why?  More to the point, under Ubuntu how can I avail myself of ***either*** of the two personalities/languages of this printer?  (I'd like to try the one that I am ***not*** currently getting, to see if that solves the printing problems described above.)

---

