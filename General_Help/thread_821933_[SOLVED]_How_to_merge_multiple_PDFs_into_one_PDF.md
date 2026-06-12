---
title: "[SOLVED] How to merge multiple PDFs into one PDF?"
date: 2008-06-07
forum: General Help
---

### Post by Th3Professor on 2008-06-07
How do you do that?

I have several PDFs that are 1-pagers and would like to merge them into one large PDF.

Is there a particular app that does this?

Thanks!

---

### Post by y-lee on 2008-06-07
hmm try [Merge multiple PDFs into one file]("http://www.newlinuxuser.com/merge-multiple-pdfs-into-one-file/")

---

### Post by kaibob on 2008-06-07
You can also use PDFtk, which is in the repo's, to do what you want. The commandline syntac is:

```
pdftk [input files] cat output [output file]
```

In the above command, you need to insert the names of the input files and output file. When combining a large number of PDF files, it may be easiest to place them in an empty directory and use *.pdf as the input files. 

BTW, I use Ghostscript to combine PDF files, as explained in the link provided by y-lee.

---

### Post by Th3Professor on 2008-06-07
That did the trick...

I'll copy/paste the info just in case that website ever removes the info...

[quote="http://www.newlinuxuser.com/merge-multiple-pdfs-into-one-file/"]


This process requires you to install two packages: Ghostscript and PDFtk. These packages are widely available in the repositories of your distro of choice. If you are going to install them using apt, use the following commands:
 
**apt-get install gs**
 **apt-get install pdftk**


Now, open a terminal and copy and paste the following command:[INDENT]
** gs -dNOPAUSE -sDEVICE=pdfwrite -sOUTPUTFILE=firstANDsecond.pdf -dBATCH first.pdf second.pdf**
[/INDENT]Change the name of first.pdf and second.pdf to the PDF files that you would like to merge, and change the name of firstANDsecond.pdf to the name you would like to name your merged pdf file. If you haven’t changed directories, the merged document will be created in your home directory.
 This command allows you to merge more than just two documents.  If you would like to merge three or more [[FONT=Verdana][FONT=Verdana]PDF [/FONT][FONT=Verdana]files[/FONT][/FONT]]("http://www.newlinuxuser.com/merge-multiple-pdfs-into-one-file/#"), continue to append the file names to the above command (separated by a space).
[/quote]


On another note... is there a PDF "editor" out there?

I've used Adobe-type apps before, pretty handy, though am not familiar with any open source variations. Thanks! :)

---

### Post by avtolle on 2008-06-07
To edit PDF files, there is pdfedit in the repositories. This may be what you are looking for. Here's a link about using it under Feisty, which gives some additional information:

[http://www.howtoforge.com/editing_pdf_files_pdfedit_ubuntu_feisty](http://www.howtoforge.com/editing_pdf_files_pdfedit_ubuntu_feisty)

---

### Post by Th3Professor on 2008-06-08
lol "pdfedit"... I should've figured that out! :) thx, good to know... it seems to be doing a pretty good job at basic pdf editing, though basics is all I need.

---

### Post by kaibob on 2008-06-08
> For years I never knew how to combine multiple PDFs into one PDF file without the use of Adobe Professional. However, this can be done and can be done in Linux very very easily and of course, for free. This process requires you to install two packages: Ghostscript and PDFtk. 

The above statement is somewhat inaccurate in that PDFtk is not needed to combine multiple PDF files into one PDF file. Ghostscript alone will do the job just fine. This isn't all that important except that PDFtk and needed dependencies can consume about 40 MB of disk space.

---

### Post by Th3Professor on 2008-06-08
> **kaibob said:**
> The above statement is somewhat inaccurate in that PDFtk is not needed to combine multiple PDF files into one PDF file. Ghostscript alone will do the job just fine. This isn't all that important except that PDFtk and needed dependencies can consume about 40 MB of disk space.

ORLY?

How do you merge PDFs with gs?

---

### Post by Th3Professor on 2008-06-08
How would I create a PDF that would consist of some screenshots?

EDIT:
Okay I have somewhat of a progress on that one...
I saved a screenshot (.png) as ghostscripts (.ps) in gimp, then used:
```
[B]gs -dNOPAUSE -sDEVICE=pdfwrite -sOUTPUTFILE=firstANDsecond.pdf -dBATCH first.pdf second.pdf
```
[/B]
However, I'm not sure how to save all the "png" as "ps" in one step. Any ideas?

---

### Post by kaibob on 2008-06-08
> **Th3Professor said:**
> ORLY? How do you merge PDFs with gs?

I'm sorry but I'm not sure I understand your question. You merge PDF's with gs (Ghostscript) by way of the gs commandline contained in your above posting. The point I was trying to make was that PDFtk is not needed to do this. I'm sure that I misunderstand what you are asking, but I can't quite figure this out.

---

### Post by kevdog on 2008-06-08
How about the pdfjoin function as described here:
[http://www2.warwick.ac.uk/fac/sci/statistics/staff/academic/firth/software/pdfjam](http://www2.warwick.ac.uk/fac/sci/statistics/staff/academic/firth/software/pdfjam)

There is even a debian package:
[http://packages.debian.org/unstable/text/pdfjam](http://packages.debian.org/unstable/text/pdfjam)

---

### Post by kaibob on 2008-06-08
> **Th3Professor said:**
> How would I create a PDF that would consist of some screenshots?


There are a number of ways to do what you want. One alternative is to copy all of the PNG screenshots to an empty folder. Then, open a terminal window, change to the folder that contains the screenshots, and run the following command:

```
convert *.png outputfilename.pdf
```

Convert is part of the Imagemagick package, which is available in the repo's. It takes up very little space and is very useful.

---

### Post by Th3Professor on 2008-06-08
> **kaibob said:**
> I'm sorry but I'm not sure I understand your question. You merge PDF's with gs (Ghostscript) by way of the gs commandline contained in your above posting. The point I was trying to make was that PDFtk is not needed to do this. I'm sure that I misunderstand what you are asking, but I can't quite figure this out.

Forget about it... what I said. lol :) I was on another planet.

> **kaibob said:**
> There are a number of ways to do what you want. One alternative is to copy all of the PNG screenshots to an empty folder. Then, open a terminal window, change to the folder that contains the screenshots, and run the following command:

```
convert *.png outputfilename.pdf
```Convert is part of the Imagemagick package, which is available in the repo's. It takes up very little space and is very useful.

Wow... convert... that's it. So easy. thx:)

---

### Post by kleo skywalker on 2010-01-02
The pdftk tip was quick and easy and got me out of a fix, thanks!

---

### Post by sanket_s on 2010-01-09
How do I remove one page from a pdf file w/o using pdf editor.??

Thanks in advance.

---

### Post by kaibob on 2010-01-09
> **sanket_s said:**
> How do I remove one page from a pdf file w/o using pdf editor.??

Thanks in advance.

There are some GUI app's that make deleting a page or pages quite easy. I don't use them, so I can't provide any direct references, but I'm sure another forum member will have information on this. 

If you want to do this with pdftk, you cannot specify a page to delete and instead have to specify the pages to retain. For example, to delete page 5 from a 10-page document, I believe the command with pdftk would be:

```
pdftk in.pdf cat 1-4 6-10 output out.pdf
```

EDIT:

This is the GUI app that I had in mind. It's called pdfshuffler, and it's in the repo's.

[http://sourceforge.net/projects/pdfshuffler/](http://sourceforge.net/projects/pdfshuffler/)

---

### Post by jaezcurra on 2010-01-09
At [http://www.pdfsam.org](http://www.pdfsam.org) there is a product that I have used as well in ubuntu as in Windoows and it always worked.
Once installed it goes to the Office apps.

---

### Post by John_T on 2010-06-22
Just a note which some may find convenient.

A few people have recommended "pdftk". A companion for this, which is also in the repositories is "pdfchain" which is a nice simple GUI for merging and ordering documents.

Once installed you'll find it under "Applications" > "Office"> "PDF Chain"

Screen shot attached.

---

### Post by buzink on 2011-05-31
Try pdf-shuffler, it's graphical, simple, small and efficient. You can find it in Ubuntu software center.

---

### Post by AlexanderDGreat on 2011-07-07
Wow these are all great ideas, specially the PDF-chain and PDF-shuffler with the GUI. How will you survive if it's on Windows?

You download a trial -> it installs a ton of spam, adware -> PC slows down...

You purchase

Ubuntu -> FREE!

---

