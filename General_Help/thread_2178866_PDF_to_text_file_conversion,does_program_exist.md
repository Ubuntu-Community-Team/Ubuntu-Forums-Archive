---
title: "PDF to text file conversion,does program exist?"
date: 2013-10-05
forum: General Help
---

### Post by gnostlos on 2013-10-05
Is there a program that converts PDF files to text files? Emacs seems to be able to do it.

---

### Post by Vaphell on 2013-10-05
check out *pdftotext*

---

### Post by slickymaster on 2013-10-05
> **Vaphell said:**
> check out *pdftotext*

+1

Besides pdftotext, there is also a command line converter in unoconv```
sudo apt-get install unoconv
```It will convert any document from and to any OpenOffice supported format.

---

### Post by gnostlos on 2013-10-07
VapHell and slickymaster, thanks. Neither works yet. Pdftotext was right under my nose, but I did not know it existed. Its output was just "^L^L^L......". I installed unoconv, but the form of the command was not clear to me. I just typed "unoconv something.pdf" and got:

/q/z$ unoconv robco-20130930.pdf 
Warning: -headless is deprecated.  Use --headless instead.
Warning: -invisible is deprecated.  Use --invisible instead.
Warning: -nodefault is deprecated.  Use --nodefault instead.
Warning: -nofirststartwizard is deprecated.  Use --nofirststartwizard instead.
Warning: -nologo is deprecated.  Use --nologo instead.
Warning: -norestore is deprecated.  Use --norestore instead.
Warning: -accept=socket,host=localhost,port=2002;urp;StarOffice.ComponentContext is deprecated.  Use --accept=socket,host=localhost,port=2002;urp;StarOffice.ComponentContext instead.
^Z
[1]+  Stopped                 unoconv robco-20130930.pdf
/q/z$ 


If you can think of any other angles, please let me know.

---

### Post by bootedguy on 2013-10-07
If it is a true PDF (not a PDF of an image), then copy and paste should work as well.

---

### Post by gnostlos on 2013-10-10
Bootedguy, this is a little too sophisticated for me. Now that you mention it, I think it may be an image of a copy, since it is crooked on the page. That means, then, that it is not really a PDF file with text in some form, I suppose, but just a picture of the dots. In that case, I suppose there is no translation.

---

### Post by gnostlos on 2013-10-12
The people sending me PDF's had sent the earlier ones as PDF and the later ones as copies of printouts which they named "....pdf". And pdftotext did print the text in the real PDF's, though my downloaded unoconv did not. But I do not mark the problem as solved, because the quality of pdftotext is poor. It simply puts any text string it finds on a separate line. My PDFs were financial statements, so a column of descriptions followed by a column of numbers is not helpful. Is there any alignment capability in any programs?

---

### Post by Lars Noodén on 2013-10-12
PDF is an end-stage format.  It holds a representation of data on its way to either the bitbucket or the recycle bin (via the printer).   By the time material hits PDF all the pieces necessary for automated data processsing are gone and you are only left with a visual layout.  Again, PDF is for displaying or erasing.  

All information about the document's structure is gone.  If you want that structure, you'll have to go upstream and get the original files in XML, SGML, CSV or whatever they may have been.

---

### Post by gnostlos on 2013-10-24
Thank you, Lars. I see your point. I wish there were some structure conveyance but accept that there is not. I would like to declare this thread SOLVED to get it out of the way of all the others, but do not find a button for that.

---

### Post by Iowan on 2013-10-24
> **gnostlos said:**
>  I would like to declare this thread SOLVED to get it out of the way of all the others, but do not find a button for that.[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

