---
title: "Problems with printing. Document viewer don't print pdf. 18.04"
date: 2019-01-11
forum: General Help
---

### Post by _zax_ on 2019-01-11
I have a freshly installed ubuntu 18.04, i also use a samsung M2026w printer (wireless). Diver is Samsung M2020 series.
Problem with printing. Document Viewer don't print pdf. I tried Firefox and it printed once normally, then it gave me an awkward page with little squares having 4 small letters inside each one ,instead of normal letters and symbols, then the next day it printed the same page normally again. I am a math professor and i need to print pdfs every other day. Note that the pdfs contain math and greek language since I am Greek, but i don't think that this is the problem.

---

### Post by cmcanulty on 2019-01-11
Try installing qpdfview it has more features and opens really fast. mupdf is another option

---

### Post by _zax_ on 2019-01-11
> **cmcanulty said:**
> Try installing qpdfview it has more features and opens really fast. mupdf is another option

Tried. it does not do the job neither . 

By the way message "printing complete" comes up with both apps.

---

### Post by ajgreeny on 2019-01-11
Have you tried **ocular**, the KDE pdf reader?
It will pull in a lot of qt/kde libs, etc etc, when installed but it often thought (by others, not necessarily by me) one of the best pdf readers in the repos.

Do you know which version pdf files have your problem, as that could possibly be the reason behind the printing difficulty.

---

### Post by CatKiller on 2019-01-11
> **ajgreeny said:**
> Have you tried **ocular**, the KDE pdf reader?

It's okular, with a K, because KDE.

This doesn't sound at all like a PDF viewer problem, it sounds like a printer problem.

---

### Post by HermanAB on 2019-01-11
Well, technically, a PDF file is ready for printing.  You don't need special software and can just send it straight to the printer.

For example to print to the default printer on your machine:
$ lpr -P localhost file.pdf

More information here:
[https://www.aeronetworks.ca/2014/10/printers.html](https://www.aeronetworks.ca/2014/10/printers.html)

---

### Post by Impavidus on 2019-01-11
In mathematics you get quite some Greek letters even if you're not Greek, although maybe not as many as in physics.

The little boxes with a few symbols inside indicate this is a font problem. Whenever a character is undefined in the current font, you may get a small box with the hexadecimal code of that character (Can you check those codes? Do they make sense? But maybe not, as it may use some funny encoding.). Normally all fonts should be built into the pdf files using them, except a small set of standard fonts (Helvetica, Times, Symbol, Courier and some later additions) that are supposed to be built into every pdf printer, printer driver or pdf viewer. In the default pdf viewer (Document Viewer a.k.a. evince), there is, somewhat hidden, a menu to view the properties of the file, with a tab to see the fonts. That should tell whether all fonts are indeed included.

How to solve this problem I don't know. For some reason, it seems that the pdf viewer can access the fonts, but the printer driver can't and in Firefox the problem even seems intermittent. Maybe this helps you further.

---

### Post by _zax_ on 2019-01-11
> **ajgreeny said:**
> Have you tried **ocular**, the KDE pdf reader?
It will pull in a lot of qt/kde libs, etc etc, when installed but it often thought (by others, not necessarily by me) one of the best pdf readers in the repos.

Do you know which version pdf files have your problem, as that could possibly be the reason behind the printing difficulty.

Sorry I am late, I've been out for work.
Okular not printing as well.
I don't know what do you mean by pdf version. I made the pdf my own using LaTeX.

---

### Post by _zax_ on 2019-01-12
Evince started printing and hopefully everything comes out of the printer normal!
Yesterday I was determined to make it work! So I did a series of things
First i searched on the manufacturer's site for the right driver. There is a Linux driver for that printer here:[http://www.samsungdrivers.net/samsung-m2026w-driver/]("http://www.samsungdrivers.net/samsung-m2026w-driver/"). The tar.gz that I downloaded contains a bunch of .sh not any PPD file, I install it using "sudo sh install.sh" some y later it was done, I checked on the printers and their drivers and nothing seemed new to me:mad: , tried to print and nothing again. 
Then I added a new printer at settings>devices>printers, click on the Additional Printer Settings then right click on printer and go to properties. I hit "change" on "Make and Model" then change driver. I chose "Model M2020 (recommended)" and "Drivers Samsung M2020 Series, driverless, cups-filters 1.20.2[en]". Forward and then when asked: 
Use the new PPD as is OR Try to copy the option settings over from the old PPD, I chose the all new thing. Then I hit the "print test page" button and the printer started printing. I opened a pdf using Document reader and boom printer started printing and everything went back to normal. 
I don't know what was wrong before, and i am almost sure that the installation of the .sh that i did earlier was not the only thing that i had to do to use those drivers in the tar.gz. Probably the drivers in the tar.gz would be a better thing to use, but after all I can print again!;)

---

