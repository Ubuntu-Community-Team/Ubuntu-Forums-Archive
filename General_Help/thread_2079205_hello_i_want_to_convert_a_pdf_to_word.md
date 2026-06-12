---
title: "hello i want to convert a pdf to word"
date: 2012-11-01
forum: General Help
---

### Post by CCgirl6690 on 2012-11-01
Hello everyone 
iv got an pdf file , there is a water mark on each pays saying "this file was eddited with trial version of xsoftware......"  and i dunno how i can remove that water mark , it wont let me read the 5 or 6 first lines of each page , so i thought maybe converting it to word might solve it and remove it , so looking for the free convertor for ubuntu 12
correct me if im wrong please, or are there any other ways for me to remove it . 
thanksssss

---

### Post by drmrgd on 2012-11-01
I'm not sure if it's installed by default, or if I installed it some time ago, but there's a commandline tool called 'pdftotext' that I've used in the past.  I think there's a whole series of these that can covert to html, images, etc.  See if you have pdftotext, and if not install it and give that a shot.

---

### Post by varunendra on 2012-11-01
> **CCgirl6690 said:**
> Hello everyone 
iv got an pdf file , there is a water mark on each pays saying "this file was eddited with trial version of xsoftware......"  and i dunno how i can remove that water mark , it wont let me read the 5 or 6 first lines of each page , so i thought maybe converting it to word might solve it and remove it , so looking for the free convertor for ubuntu 12
correct me if im wrong please, or are there any other ways for me to remove it . 
thanksssss
I haven't done it on Ubuntu yet (did on windows once), but there is an application "PDF Edit" in the Software Center which seems to be able to do it. It can also do what *drmrgd* mentioned above, that is, export the contents to a simple text file (but the formatting may get messed up, as will be the case with any other 'editable' format exported from pdf). Install it with :
```
sudo apt-get install pdfedit
```then see if it meets your requirements. If you need advance editing, then try **inkscape** (something like corel draw in windows) to either edit it or just to export it to a more friendly format which you can easily edit.

---

### Post by Mark Phelps on 2012-11-01
> **CCgirl6690 said:**
> Hello everyone 
iv got an pdf file , there is a water mark on each pays saying "this file was eddited with trial version of xsoftware......"  

Generally speaking, the PDF creator apps embed this watermark into the file they create -- making removing it virtually impossible.

You would need the original content from which the PDF was constructed -- which, obviously, you don't have.

---

### Post by cedric_tux on 2012-12-10
Have you already tried PdfStudio form Qoppa?
I Think they can do that.

---

