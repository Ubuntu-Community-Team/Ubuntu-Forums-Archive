---
title: "Merge pdf files"
date: 2006-09-21
forum: General Help
---

### Post by rekahsoft on 2006-09-21
Hey i have a bunch of pdf files that i want to merge...how would i go about doing that?

---

### Post by Average Joe on 2006-09-21
Honestly, I don't know. But have you tried [this]("http://ktmatu.com/info/merge-pdf-files/")?

---

### Post by kolesarm on 2007-01-22
try pdftk - [here ]("http://www.accesspdf.com/pdftk/") is an explanation how you use it.

---

### Post by freda on 2007-02-06
Why not try the software called  [[COLOR="Red"]ABC Amber PDF Merger[/COLOR] ]("http://www.qweas.com/download/converters/document_converters/abc_amber_pdf_merger.htm") which allows you to easily split or merge a number of PDFs. All you have to do is selecting required files, choosing format to convert and clicking "Save As" button.
 
Have a try!

more information:
[http://www.qweas.com/download/converters/document_converters/abc_amber_pdf_merger.htm]("http://www.qweas.com/download/converters/document_converters/abc_amber_pdf_merger.htm")


:lolflag: :lolflag: :lolflag:

---

### Post by Rui Pais on 2007-02-06
> **freda said:**
> Why not try the software called  [[COLOR="Red"]ABC Amber PDF Merger[/COLOR] ]("http://www.qweas.com/download/converters/document_converters/abc_amber_pdf_merger.htm") ...

maybe because of this:
> Version:	2.01  	Publisher:	processtext.com
File Size:	1,444 KB 	System:	Windows 98/ME/NT/2000/XP
License:	Free to try ($19.95) 	Limitations:	30-day free trial

looks like a close source application for Windows.

(are you sure you are in the right forum?)

---

### Post by jonnymccullagh on 2007-02-06
It has been a while since I needed to merge PDF files and I think there is a shortfall for PDF tools under Gnu/Linux.
Anyway, in KDE I used the PDF Service Manu Pack which is a service menu which is available when you right click on a PDF file in Konqueror. (If you are using gnome you will need to install konqueror, pdftk and pdfjam using Synaptic)
I found it best to rename each of the PDF files alphabetically (or using numbers) so that they were in the correct order for the merge as the service menu only merges files in alphabetical order.
The PDF Service Menu Pack is availble from:
[http://www.kde-apps.org/content/show.php?content=37321]("http://www.kde-apps.org/content/show.php?content=37321")

Another option might be PDFedit - which I have not yet tried so I don't know how much functionality it has but it looks promising:
[http://www.kde-apps.org/content/show.php?content=51831]("http://www.kde-apps.org/content/show.php?content=51831")

All the Best,
jonny

---

### Post by lobner on 2007-08-02
This is easily done with the following command:
```
gs -q -sPAPERSIZE=letter -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -sOutputFile=out.pdf in1.pdf in2.pdf in3.pdf ...
```

---

### Post by wild_oscar on 2007-08-23
How about this?
[http://linux.softpedia.com/get/Text-Editing-Processing/Others/PDF-Split-and-Merge-10743.shtml]("http://linux.softpedia.com/get/Text-Editing-Processing/Others/PDF-Split-and-Merge-10743.shtml")

---

### Post by kangyu29 on 2008-05-12
> **kolesarm said:**
> try pdftk - [here ]("http://www.accesspdf.com/pdftk/") is an explanation how you use it.

pdftk is very easy to install(apt-get) and use with the help of their "simple example".
Thanks.

---

### Post by Gonkerd on 2008-07-01
I've just used: 

pdftk - pdftoolkit and it worked perfectly and fast!

[examples of how to use pdftk]("http://www.accesspdf.com/article.php/20041129175231241")
same pages as kolesarm mentioned

---

### Post by crokfor on 2008-07-08
how do you combine lots of pdf files with names 01.pdf .... 50.pdf?

putting them manually is not productive

---

