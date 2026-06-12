---
title: "Can't Open PDFs by Left-Clicking"
date: 2006-10-09
forum: General Help
---

### Post by Ubuntist on 2006-10-09
When I click on a PDF file, like "x.pdf", I get an error message

```
Cannot open x.pdf

The filename "x.pdf" indicates that theis file
is of type "pdf document". The contents of the file indicate that
the file is of type "PDF document". If you open this file, it
might present a security risk to your system.

Do not open the file unless you created the file yourself, or
received the file from a trusted source.  To poen the file,
rename the file to the correct extenstion for "PDF document",
then open the file normally. Alternatively, use the Open With
menu to choose a specific application for the file.
```

When I right-click, I can open the file either with Adobe or Document Reader (Evince).

What do I need to change to allow these files to be opened by left-clicking?  I've looked in System|Preferences for something relevant, but couldn't find anything.

---

### Post by yopnono on 2006-10-09
Have a look in you home dir there you have a hidden folder ".local" just rename it and try to open the PDF.

---

### Post by yopnono on 2006-10-09
You can also check the properties of the file by right click and look at the open with tab. You may have multiple applications in there.

In there you can add and remove applications to open the file with

---

### Post by Ubuntist on 2006-10-10
Thanks, yopono.

I've checked, but there's no .local in my home dir.

When I right-click on a PDF file and check properties, the Open With tab gives shows two applications: Adobe Acrobat and Document Viewer.  Regardless of which of the two is selected, left-clicking still generates the error message I posted originally.

Note that the error message that I posted refers at one point to a "pdf" document but to a "PDF" document at another point.  Could it be that I just need to chage "pdf" to "PDF" in some table somewhere?  There must be a table somewhere that tells Ubuntu that a file with a name ending in ".pdf" is a PDF file.

---

### Post by beerorkid on 2006-10-10
this: [http://www.mikesplanet.net/?p=38](http://www.mikesplanet.net/?p=38)
solved all of my adobe problems

---

### Post by Ubuntist on 2006-10-17
> **beerorkid said:**
> this: [http://www.mikesplanet.net/?p=38](http://www.mikesplanet.net/?p=38)
solved all of my adobe problems

Thanks for the link, beerorkid, but it seems to relate to problems opening PDFs from Firefox.  My problem is that I can't click-open PDFs in Nautilus.

---

