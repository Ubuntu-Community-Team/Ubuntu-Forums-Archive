---
title: "CUPS-PDF creates files not compatible with Acrobat"
date: 2008-05-20
forum: General Help
---

### Post by lsutiger on 2008-05-20
I recently switched over to Ubuntu for my office. I am having a problem with printing to a shared windows printer that [I have posted here]("http://ubuntuforums.org/showthread.php?t=795571").
In the mean time, I decided that I could print to CUPS-PDF printer, send it to the server, and have my coworker print it out...problem:
Adobe acrobat does not recognize the file. I tried it on my VB also, and Adobe did not recognize it. I can open it fine on my Ubuntu box.

For CUPS-PDF I have the Generic PDF file generator selected.

There were only 20 posts returned when I searched for CUPS PDF file generator, none fixed the problem.

Thanx in advance!

---

### Post by EarloftheWest on 2008-05-20
Have you tried viewing the file with different versions of Acrobat Reader? I've noticed that sometimes Adobe Reader has some bugs which create compatibility problems. On Windows, I started using foxit pdf reader without problems.

---

### Post by lsutiger on 2008-05-20
> Have you tried viewing the file with different versions of Acrobat Reader? I've noticed that sometimes Adobe Reader has some bugs which create compatibility problems. On Windows, I started using foxit pdf reader without problems.

I just d/l foxit and got a "format error: not a PDF or corrupted". I also tried with acrobat 6.x and 7.x

thanx for the reply!

---

### Post by EarloftheWest on 2008-05-21
Bummer.

Can you recreate the PDF files? Perhaps they got corrupted somehow?

Are there programs that can extract the data or fix the file? I'm guessing that there would be.

---

### Post by lsutiger on 2008-05-21
> Bummer.

Can you recreate the PDF files? Perhaps they got corrupted somehow?

Are there programs that can extract the data or fix the file? I'm guessing that there would be.

I have tried that (recreating the files). I have tried first from the generic (recommended) drivers and setting to other options.

Thanx for the reply!

---

### Post by lsutiger on 2008-05-29
Any ideas here ppl?

---

### Post by niteshifter on 2008-05-29
Hi,

You said you can open it on your Ubuntu box - this would be the box that you generated the file on and it was evince that opened it? In particular if it was evince that displayed the file correctly then I think I know what the problem is: your generated Postscript output is not being converted to PDF. To fix this:

Do in this order via Synaptic (or command line, if you're comfortable with it):

1. Remove completely cups-pdf.
2. Remove completely ghostscript.
3. Install ghostscript.
4. Install cups-pdf.

Why you may ask? cups-pdf doesn't actually do the pdf, ghostscript does. It takes Postscript (output from a print command) and converts it to PDF (as a file).

---

### Post by noynac on 2008-05-30
---

---

### Post by lsutiger on 2008-05-30
> niteshifter  	
Re: CUPS-PDF creates files not compatible with Acrobat
Hi,

You said you can open it on your Ubuntu box - this would be the box that you generated the file on and it was evince that opened it? In particular if it was evince that displayed the file correctly then I think I know what the problem is: your generated Postscript output is not being converted to PDF. To fix this:

Do in this order via Synaptic (or command line, if you're comfortable with it):

1. Remove completely cups-pdf.
2. Remove completely ghostscript.
3. Install ghostscript.
4. Install cups-pdf.

Why you may ask? cups-pdf doesn't actually do the pdf, ghostscript does. It takes Postscript (output from a print command) and converts it to PDF (as a file). 

Ok I did that. Now I only have the option of creating postscript files. To make matters worse, I only get blank pages.

I did notice that when I went to remove (completely) ghostscript, a lot of packages were removed, but when I re-installed, only the ghostscript package was installed.

---

### Post by lsutiger on 2008-05-30
I did it again and now it works.
Thanx!

---

### Post by lsutiger on 2008-05-30
Craptastical!

I do not know if this has anything to do with this, but I have my suspicions.

I now can generate pdf's. But now I can not print to the windows shared printer. I had problem in the beginning [(you can see at this thread)]("http://ubuntuforums.org/showthread.php?t=795571"). Since I completely removed cups-pdf, could it have effected this?

---

### Post by lsutiger on 2008-06-03
Anybody? Could removing cups-pdf completely effect printing to a printer?

---

