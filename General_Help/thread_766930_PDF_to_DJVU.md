---
title: "PDF to DJVU?"
date: 2008-04-25
forum: General Help
---

### Post by pelikan555 on 2008-04-25
Hi,
Is there a way I can convert a .pdf file (all scanned images - so preferably compressed a bit) into a .djvu? Whether it be a direct or a round-a-bout method I'm not bothered.

Thanks!

---

### Post by ryanhaigh on 2008-04-27
Not sure if it will work but if you install imagemagick you could try using 
```
convert file.pdf file.djvu
```

---

### Post by pyre on 2008-04-27
iirc, djvu is a proprietary format in the vein of rar.  reading it is free, but you need a license to create software that will actually *make* a djvu file.

---

### Post by battletoad on 2008-06-09
have a look :
[http://djvu.sourceforge.net/gsdjvu.html](http://djvu.sourceforge.net/gsdjvu.html)
[http://code.google.com/p/pdf2djvu/](http://code.google.com/p/pdf2djvu/)

dejavu isn't proprietary.

---

### Post by netyire on 2008-12-04
Hi! I know this is a late reply but I just need to say that the .djvu format has been extensively documented and that it's specifications have been published. Furthermore the developers of .djvu allowed for open sourced encoders and decoders to be built based on the published specifications. **As such, djvu creation is a very easy task on linux. The bottom line is: DJVU is FREE and .djvu file creation is also FREE.**

Here's one way to convert those scanned pictures into .djvu

1. Import the pictures into f-spot or other graphic viewing program capable of printing.
2. Install cups-pdf to get a virtual pdf printer installed, this allows you to create a .pdf of any file that can be printed.
3. Print those photos in f-spot to the virtual cups-pdf printer.
4. Convert the pdf to djvu with the following command:
pdf2djvu mypdf.pdf -o mydjvu.djvu

You'll have to install pdf2djvu from the repos in order for this to work.

---

### Post by TeXtonyx on 2008-12-04
[http://code.google.com/p/pdf2djvu/](http://code.google.com/p/pdf2djvu/)

pdf2djvu_0.4.13.tar.gz  
pdf2djvu_0.4.13_amd64.deb  
pdf2djvu_0.4.13_i386.deb

---

