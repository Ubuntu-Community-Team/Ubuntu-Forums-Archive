---
title: "Cannot print PDF files after ugrade to 14.04"
date: 2014-04-20
forum: General Help
---

### Post by oz1cz on 2014-04-20
After upgrading from 13.10 to 14.04, I cannot print PDF files anymore.

My printer is an HP Photosmart C7280 connected through a network. Most printing works fine, but if I try to print a PDF file, nothing happens. The printer queue lists the print job as "Processing", but nothing is printed.

I can cancel the job, but any further attempts to print anything merely causes the following jobs to be "Pending" in the job queue.

In order to print again, I must restart my computer. Then printing works again until I try printing a PDF file.

The problem, apparently, only appears when I print the PDF file using Document Viewer. Acrobat Reader can print PDF files correctly.

What can I do?

---

### Post by QDR06VV9 on 2014-04-20
```
sudo apt-get install cups-pdf
```
This will create a PDF folder in your home directory where your printed doc(s) will be.
Regards
This will also give you a new option in the print window of your browser named PDF.
Will also retain the title of what your printing.

---

### Post by SeijiSensei on 2014-04-20
I use Okular, which is a KDE app, and have no troubles printing.  It's an excellent PDF reader and can be installed on non-KDE systems as well.  Just be prepared to install a reasonable chunk of supporting libraries.

---

### Post by HermanAB on 2014-04-20
Try this:
$ lpr filename.pdf

Read 'man lpr' for details.  This is a good way to get meaningful error messages that you can then investigate.

---

### Post by oz1cz on 2014-04-20
Thank you. I tried "lpr filename.pdf" and it printed just nicely!

I guess the problem lies with Document Viewer. I just have to stop using that program.

---

### Post by llamabr on 2014-04-20
> **oz1cz said:**
> Thank you. I tried "lpr filename.pdf" and it printed just nicely!

I guess the problem lies with Document Viewer. I just have to stop using that program.

evince?  I don't care for that one.  The package maintainers are slow to implement useful fixes, and are uninterested in user feedback.

I like xpdf for a very quick and light viewer.

---

### Post by HermanAB on 2014-04-20
I use xournal for PDF files.  It is a handy PDF markup tool and also a nice and fast viewer.

---

### Post by Merel 469 on 2014-05-28
> **oz1cz said:**
> Thank you. I tried "lpr filename.pdf" and it printed just nicely!

I guess the problem lies with Document Viewer. I just have to stop using that program.
I had the same problem to print using the suggested default application.

However printing seems to be no problem with Ubuntu 14.04 as follows :

1. Navigate to the filename.pdf (using "Files") 

2. Right click the file and from context menu choose the SECOND option** Open with ....Print preview**

3. This opens a new window **GNOME Document Previewer** which does what you expect !!
   (sometimes Linux / Ubuntu does it )

This window shows a printer icon which performs printing without further problems, even on my very old machine. 

I would appreciate to hear that works for you. 
Maybe in the mean time the  updates might have solved your problem as well ?

---

