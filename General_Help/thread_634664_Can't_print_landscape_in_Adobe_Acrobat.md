---
title: "Can't print landscape in Adobe Acrobat"
date: 2007-12-07
forum: General Help
---

### Post by reswob on 2007-12-07
Quick question:  Has anyone else been unable to print landscape in Adobe Reader since upgrading to 7.10?

I checked all the orientation settings.  I've uninstalled Adobe Reader and reinstalled.  I've checked linuxprinting.org to make sure I have the correct print drivers installed (I have a Canon S330).  I've printed portrait in Adobe Reader, and landscape in OpenOffice, gedit and Document Viewer.  To be clear, I've opened a pdf file in Document Viewer and printed it landscape.  

The problem is that any file that requires a landscape print, Adobe Reader ONLY prints it portrait (thus cutting off 1/3 of the page).  

If no one else has this problem, I'll chalk it up to weird.  I just want to put this out there in case there are others and in case it doesn't just affect my particular printer.  

Thanks.

---

### Post by FuturePilot on 2008-01-01
I have the same problem. Only on one printer though. The other two are fine. :confused:
Printing the same file through Evince prints fine in Landscape on that printer though.

---

### Post by bevanjones on 2008-02-18
I've got the same problem.  My printer is a Samsung ML-1610.  I'm using Gutsy.

The problem only occurs when I'm printing a PDF document that is landscape-oriented - and (importantly) auto-rotated in the PDF viewer display.  If I produce a landscape document in a PDF file, but disable auto-rotating (see below), the file prints fine.  This is true not just for Acroread but also for Kpdf.  (Evince seems to handle it fine, which is good to know; but odd, since I've seen it reported that Evince stumbled over landscape printing in Feisty while Acroread worked OK - see [http://ubuntuforums.org/archive/index.php/t-383219.html](http://ubuntuforums.org/archive/index.php/t-383219.html)).

I've come across several threads on the Ubuntu forums which report this problem.  It does seem to be something that needs closer analysis and resolution.  I know of two bug reports that have been raised - [https://bugs.launchpad.net/ubuntu/+source/kdegraphics/+bug/47649](https://bugs.launchpad.net/ubuntu/+source/kdegraphics/+bug/47649) and [https://bugs.launchpad.net/ubuntu/+bug/112391](https://bugs.launchpad.net/ubuntu/+bug/112391).  The first of these is interesting, because it contains a short Perl script called "fix_orient", purported to sort out incorrect orientation in an intermediary Postscript file.  Personally, I didn't find this useful; but it prompted me to carry out investigations of my own on intermediary PS files; and I found that if you use ps2pdf to convert a PS file to PDF, and supply the command-line parameter "-dAutoRotatePages=/None", you will end up with a PDF file that will print correctly in landscape.  The drawback is that the pages are "on their side" in the on-screen PDF display.

Interestingly, according to the ps2pdf documentation ([http://pages.cs.wisc.edu/~ghost/doc/AFPL/6.50/Ps2pdf.htm](http://pages.cs.wisc.edu/~ghost/doc/AFPL/6.50/Ps2pdf.htm)), the default setting for the [Adobe] AutoRotatePages parameter is already "/None".  Either this is incorrect for more recent versions of the Acrobat PDF renderer (and the Kpdf engine?); or the ps2pdf documentation is wrong.

---

### Post by amac777 on 2008-05-24
I was having the same problem and found the solution to printing landscape is to select "Portrait" under the orientation, but then to select "auto rotate and center". So it will look exactly the same as a landscape printout but will be printed using the portrait settings, which seem to work fine.

I found this solution here:

[http://www.adobeforums.com/webx/.3c0617da](http://www.adobeforums.com/webx/.3c0617da)

Hope this helps,
Andrew

---

