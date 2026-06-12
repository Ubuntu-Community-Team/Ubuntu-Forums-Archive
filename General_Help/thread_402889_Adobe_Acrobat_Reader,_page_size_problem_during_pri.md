---
title: "Adobe Acrobat Reader, page size problem during printing"
date: 2007-04-06
forum: General Help
---

### Post by patrick1314 on 2007-04-06
Hello!

I have a problem with Adobe Acrobat Reader. I use it as it's the best PDF reader for printing with (at least, I think it is) as I do alot of printing.

I'm in the UK and naturally use A4 paper as opposed to the American 'Letter' size. My installation of Ubuntu is of course localised: language is English UK and the default *system* paper type is set to A4 etc. All other programmes on my installation use A4 as default.

But when I try to print with Adobe Reader every time I must select A4, because it sets letter as the default.

How to fix this, I wonder? There doesn't appear to be any paper options in the preferences...

Anyone else had a similar problem and/or fixed it?

Thank 'ee!

---

### Post by Wollongong on 2007-04-16
I think this is either a bug in Acroread, or a compile time option that we have no control over. It is not a runtime option per: acroread -help

Did you try the download from [www.adobe.com](www.adobe.com), to see if it has the same behaviour?
I notice there is only 1 version, not a US version and a Rest-of-world version.


If the document itself is US letter, and you hover the mouse near the lower left corner, you should see the paper size: 215.9 x 279.4mm

If you then convert the document to A4, e.g. using acroread command line:
$ acroread  -toPostScript -size a4 sourcedoc.pdf sourcedoc.ps
$ ps2pdf sourcedoc.ps newdoc.pdf

and open newdoc.pdf in acroread, the size is now correctly shown as 210 x 297mm

However, printing the document still defaults to US letter. Given that acrobat tries to maintain the original document appearance as far as possible, I would expect that it should choose the paper size to match the document, but it does not. That is why I think it is a bug (or "feature) in acrobat.

One solution is use the ubuntu supplied PDF reader "evince". It is quite good now and doesn't have this problem.

Wollongong, Australia

---

### Post by satbunny on 2007-08-03
I have noticed this problem.
Using evince is not a wholly viable alternative since it doesn't correctly draw all pdfs, especially those with transparent background layers (originated in Adobe InDesign).

---

### Post by sambody on 2007-11-15
I have the same problem: page size being "letter" instead of "A4" every time I print.

Anyone's got a solution ? I've searched the adobe forums, with no result.

---

