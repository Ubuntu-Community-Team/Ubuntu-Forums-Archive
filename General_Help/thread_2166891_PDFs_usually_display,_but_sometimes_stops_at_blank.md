---
title: "PDFs usually display, but sometimes stops at blank screen"
date: 2013-08-11
forum: General Help
---

### Post by RogerDavis on 2013-08-11
Recently, PDFs sometimes will not display content.  Usually, it works ok, but sometimes it will start, but stop short after showing the display screen (blank).  Some will display, some won't.  Some will work one time, then not the second time.

This began in about the last week or two.  At first I thought it was just a bad PDF, but the problem continues.  

I suspect an update caused the problem, but I can't pin down the date or the update.

I've tried Adobe Reader, Evince, and Document Viewer, all give the same results.  Also, I get the same results if I save the file.  It will save, but when I try to open it, I get the blank screen only.

One example is   [http://www.homedepot.com/catalog/pdfImages/23/23def8bf-1757-4ee9-83ec-290f70aef999.pdf](http://www.homedepot.com/catalog/pdfImages/23/23def8bf-1757-4ee9-83ec-290f70aef999.pdf)  .  This is only one of many on different sites.

Ubuntu 12.04, fully updated.

---

### Post by TheFu on 2013-09-01
The source of the PDF file matters as does the complexity of the content. I know that isn't what you want to hear.  All that I can say is to have 5 different viewers and try each.
* evince
* okular
* xpdf
* epdfviewer
* xournal
are all options. I'm certain there are others. Not all are light weight, or handle PDF-forms, and very few actually support editing.  Some had 100+ dependencies - talking about okular. Yuck. I just can't load any tool with that many dependencies on my system. Most were probably KDE stuff, to be fair.

If we think of PDF as a "container" that can hold almost anything (which it is), then when people put strange things into those containers, it becomes hard for programs to understand.  With F/LOSS software, each project team decides to which level of PDF they can support. The PDF file format has changed over the years to add / improve new features. I'm grateful that the F/LOSS versions don&#8217;t just puke and die when a newer, unsupported, PDF file version is encountered.

Last week I noticed that inside the **Software Center,** a PDF viewer was in the top 10 programs claiming to be free, but it wasn't. Lots of complaints about that ... seems the vendor was gaming the top-10 list with a "free to download, but pay to use" package. Further, most of the real reviews complained that it sucked. I did not try it, kept my $50.

Of course, I'm sure that all the active F/LOSS PDF projects will happily accept code fixes. ;)

---

### Post by Impavidus on 2013-09-02
They're all different.

I recently did an experiment with a 337 byte PostScript, converted into a 40,862,342 byte pdf using ps2pdf and compared the loading times in gv, evince and xpdf. In all cases the program ran for a while, in a few cases it concluded by showing a blank screen, indicated as "failed":
[TABLE="width: 500"]
[TR]
[TD][/TD]
[TD].ps
[/TD]
[TD].pdf
[/TD]
[/TR]
[TR]
[TD]gv[/TD]
[TD]26 sec (success)[/TD]
[TD]1 min 20 sec (success)[/TD]
[/TR]
[TR]
[TD]evince[/TD]
[TD]1 min 23 sec (success)[/TD]
[TD]2 min 42 sec (failed)[/TD]
[/TR]
[TR]
[TD]xpdf[/TD]
[TD](not supported)[/TD]
[TD]17 min 30 sec (failed)[/TD]
[/TR]
[/TABLE]
The image was a Sierpinski triangle.

---

