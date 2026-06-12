---
title: "OpenOffice.org export to PDF text looks bad"
date: 2007-05-03
forum: General Help
---

### Post by taipoh on 2007-05-03
When I export files in OpenOffice.org Writer and open the PDF the text looks pretty bad.  For instance, letters overlap slightly.  I can still select text in the PDF, though.  This happens for each of the ten or so fonts I've tried, and it looks bad in both feisty and on Windows boxes.

---

### Post by in_flu_ence on 2007-05-03
have you tried using the export pdf function under the file menu rather than the pdf icon?
I actually can produce better pdf there since there are more options?

---

### Post by MacD on 2007-05-14
bump

I'm having the same problem, particularly with the times new roman font.  I have installed the msttcorefonts package.  

workaround #1- I have installed and tried the cups pdf printer- which solves the font problem, but does not seem to offer the option of creating bookmarks for section headings.

workaround #2- Try changing the default fonts in OO.o to the nimbus family. Tools -> options -> OpenOffice.org Writer -> Basic Fonts

I'm not sure how nimbus fonts will work if I save as a .doc to send to someone with MS word.

Anyone have any other ideas??

---

### Post by MacD on 2007-05-23
I take back what I said above about the Nimbus fonts- they are NOT a suitable substitute for Times & Arial.  I am collaborating with a MSWORD user on a grant proposal with strict limitations on # of pages per section.  If my colleague types something up at exactly 1 page long in Times New Roman 12pt single spaced-  it HAS to be exactly 1 page long for me on OO.org.

I have found that installing the package msttcorefonts does NOT install the fonts for openoffice.  You need to actually copy the files from /usr/share/fonts/truetype/msttcorefonts into /usr/share/fonts/truetype/openoffice.  This allows Times New Roman and Arial to render properly on screen in OO.org

I have still not succeeded in creating a .pdf from OO.org with fonts the look good.  ](*,)

Opening the .doc with abiword and saving as .pdf is better, but things like page numbers don't work.  I hate to admit that in the morning I am going to have to go find a windows machine to make a decent pdf.  ????? I

---

### Post by jointstereotype on 2007-05-25
I'm experiencing the same problem here as well (running Ubuntu 7.04). It seems to happen with some fonts while others are unaffected - and changing OpenOffice's kerning setting seems to be ineffective.

As a test, I installed the Windows version of OpenOffice 2.2 using Wine, and my documents exported to PDF beautifully. While this isn't a solution, it seems to be an additional workaround until someone smarter than I can figure out the problem. ;)

---

### Post by Big_Croc7 on 2007-05-25
Not a solution either (sorry!), but I've had similar problems in the past, though not recently.  I think the issue is to do with OpenOffice in general - I tried it on a native windows machine and got similar results (in my case, italics coming out as straight text).  I haven't had any problems using 'native Ubuntu' fonts though (i.e. whatever's installed in a default Ubuntu install), so maybe the fonts packages have something to do with it.

---

### Post by jointstereotype on 2007-05-25
Hmm. I did some more fiddling, and have been unable to produce a nasty-looking PDF using the native Ubuntu fonts. The issue (on my machine, at least) seems to be with TrueType fonts alone, and perhaps how OpenOffice handles them.

This issue is strange because I'd previously used Ubuntu 5.10 / OpenOffice to format and produce several PDF files using TrueType fonts. The files all looked / printed perfectly.

I wonder if something has changed in the way OpenOffice works with Ubuntu's font system? Perhaps the two don't agree on something... ;)

---

