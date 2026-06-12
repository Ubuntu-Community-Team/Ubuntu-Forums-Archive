---
title: "Can't Print to PDF From Adobe Flash Player"
date: 2013-06-13
forum: General Help
---

### Post by Flash Kid on 2013-06-13
Hello all.  I have an Ubuntu 12.10 64-bit machine running Firefox 21 and Adobe Flash Version 11.2.202... (etc.) and I am having trouble printing a document from an SWF as a PDF.  To recreate this problem, click this link:

viewer.docstoc.com/?doc_id=83664002

This is the direct link to a file which I'm trying to download from DocStoc, but I want a more raw file than the watermarked and compressed PDF that they supply with their membership.  So, I'm trying to print it by right-clicking inside of the Flash player (in the document) and hitting "Print".  Ideally, I would like to print this to a PDF for further storage, however, the PDF option is not being shown here.  Is this an irreversible feature of Flash Player, or is there something I can manually do to get that option to show?

cups-pdf is installed and PDF printing works on every other application except on Flash, it seems.  I have also installed Chromium to see if it is a browser issue, and the same problem occurs.  So I'm starting to think this was Adobe's move, and I'm just wondering if there is something I can do to change it, or if I am just out-of-luck.

Thank you all,
FK

---

### Post by Flash Kid on 2013-06-13
Solved:

After a lot of tinkering, I just decided to default and uninstall cups-pdf and then reinstall it.  After this, a printer called "PDF" displayed in the Flash Player options and I was able to print to PDF.

Flash Kid

---

