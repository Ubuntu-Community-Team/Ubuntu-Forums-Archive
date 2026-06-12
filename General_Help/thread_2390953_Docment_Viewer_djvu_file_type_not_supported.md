---
title: "Docment Viewer djvu file type not supported"
date: 2018-05-04
forum: General Help
---

### Post by monkeybrain20122 on 2018-05-04
Document Viewer aka Evince used to be able to open djvu files, but in 18.04 I get "File type DjVu image (image/vnd.djvu) is not supported"  The "image" is actually a book. qpdfview can open it without problem, as could Evince in  all previous versions of Ubuntu.

Am I missing something here?

Thanks.

---

### Post by PaulW2U on 2018-05-05
> **monkeybrain20122 said:**
> Document Viewer aka Evince used to be able to open djvu files, but in 18.04 I get "File type DjVu image (image/vnd.djvu) is not supported"  The "image" is actually a book. qpdfview can open it without problem, as could Evince in  all previous versions of Ubuntu.
Hi monkeybrain20122, until I saw your post I'd never heard of the DjVu format but couldn't find a file anywhere to test evince's treatment of such files. So I converted a PDF to DjVu format online, downloaded it and successfully opened it with evince. So no problem here using Ubuntu 18.04.

What happens if you right-click the file in nautilus, select "Open With Other Application" and then search for Document Viewer? 

I see libdjvulibre21 is installed to support the DjVu format. Perhaps reinstall that package?

---

### Post by monkeybrain20122 on 2018-05-05
Hi, thanks for the reply. 

djvu is a common format for books. I have reinstall libdjvulibre2 and evince, still not working.
If you right click that djvu document you created and check for properties, what is the Type?
here it says 
> DjVu image (image/vnd.djvu)

Also unlike in 16.04 there are no preview thumbnails for .djvu files, just a generic icon.

---

### Post by PaulW2U on 2018-05-05
> **monkeybrain20122 said:**
> If you right click that djvu document you created and check for properties, what is the Type?
here it says 


Also unlike in 16.04 there are no preview thumbnails for .djvu files, just a generic icon.
Here I see: ```
DjVu document (image/vnd.djvu+multipage)
```. nautilus shows me a thumbnail of the document. Probably not relevant but this installation was originally Ubuntu 17.10 upgraded during the development period to Ubuntu 18.04..

---

### Post by monkeybrain20122 on 2018-05-05
> **PaulW2U said:**
> Here I see: ```
DjVu document (image/vnd.djvu+multipage)
```. nautilus shows me a thumbnail of the document. Probably not relevant but this installation was originally Ubuntu 17.10 upgraded during the development period to Ubuntu 18.04..

There has been changes upstream [https://bugzilla.gnome.org/show_bug.cgi?id=754467](https://bugzilla.gnome.org/show_bug.cgi?id=754467)

It seems that here it is not picking up the correct type, Since my documents are books they should be image/vnd.djvu+multipage rather than image/vnd.djvu

Can you please see if [this]("https://www.dropbox.com/s/u4ukmvmbly3yl4c/Stewart%20%26%20Golubitsky%20-%20Fearful%20Symmetry.djvu?dl=0") opens on your end? Thanks.

---

### Post by PaulW2U on 2018-05-05
> **monkeybrain20122 said:**
> Can you please see if [this]("https://www.dropbox.com/s/u4ukmvmbly3yl4c/Stewart%20%26%20Golubitsky%20-%20Fearful%20Symmetry.djvu?dl=0") opens on your end? Thanks.
```
Unable to open document “file:///home/paul/Downloads/Stewart & Golubitsky - Fearful Symmetry.djvu”. 
File type Perl script (application/x-perl) is not supported
```
The file properties do show as image/vnd.djvu though.

---

### Post by monkeybrain20122 on 2018-05-05
> **PaulW2U said:**
> ```
Unable to open document “file:///home/paul/Downloads/Stewart & Golubitsky - Fearful Symmetry.djvu”. 
File type Perl script (application/x-perl) is not supported
```
The file properties do show as image/vnd.djvu though.

But it should be image/vnd.djvu+multipage 
So somehow the Type is not detected properly.

---

### Post by Frogs Hair on 2018-05-05
I was able to open the document in 18.04.

 [[img]http://i.imgur.com/qcNsKkWm.png[/img]](https://imgur.com/qcNsKkW)

---

### Post by monkeybrain20122 on 2018-05-05
Hi, 

if you right click the document and go to properties > Type, what does it say?

---

### Post by Frogs Hair on 2018-05-05
Here you are.

---

### Post by monkeybrain20122 on 2018-05-06
Following comment 3 from this [link]("https://bugzilla.redhat.com/show_bug.cgi?id=1513188"), I edited /usr/lib/x86_64-linux-gnu/evince/4/backends/djvudocument.evince-backend to add image/vnd.djvu to the end and now evince opens djvu. 

But I still have no idea why the djvu files are not detected correctly as image/vnd.djvu+multipage. The link doesn't above seems to address this but not quite, there is no djvulibre-mime.xml or similar in my system. So I am not marking this as solved just now. Maybe someone can find a  solution for the system not detecting the correct meme type for these files.

There is still no preview thumbnails for djvu files, may be related.

---

### Post by PaulW2U on 2018-05-06
This morning I managed to open your book by selecting "Open with Document Viewer" when prompted as the download starts.

[ATTACH=CONFIG]279598[/ATTACH]

I then tried the download again but saved the file to my PC. evince successfully opened it. The file type is now shown as "DjVu document (image/vnd.djvu+multipage)" and the correct thumbnail is being displayed in nautilus.

So the only thing that I've done differently today is to first open the file directly from the web rather than from my PC. Does that help?

---

### Post by monkeybrain20122 on 2018-05-06
> **PaulW2U said:**
> 

So the only thing that I've done differently today is to first open the file directly from the web rather than from my PC. Does that help?

Same, still same file type. .

---

### Post by monkeybrain20122 on 2018-05-06
I think I have narrowed it down. I did a fresh install and it was working, the correct type (image/vnd.djvu+multipage) was detected and evince opened these files with no issue. But it stopped working and the file type got changed to image/vnd.djvu after installing these packages from repo

> autoconf (2.69-11)
automake (1:1.15.1-3ubuntu2)
autotools-dev (20180224.1)
bison (2:3.0.4.dfsg-1build1)
cmake (3.10.2-1ubuntu2)
cmake-curses-gui (3.10.2-1ubuntu2)
cmake-data (3.10.2-1ubuntu2)
libbison-dev (2:3.0.4.dfsg-1build1)
libcurl4 (7.58.0-2ubuntu3)
libjsoncpp1 (1.7.4-3)
librhash0 (1.3.6-2)
libsigsegv2 (2.12-1)
libuv1 (1.18.0-3)
m4 (1.4.18-1)
swig (3.0.12-1)
swig3.0 (3.0.12-1)



However, removing these packages one by one does not restore the default behaviour so some configurations appear to have been changed irreversibly.

Anyone has an idea which package might be the culprit? Don't feel like reinstalling again to find out. :(

---

### Post by monkeybrain20122 on 2018-05-14
Three times it is a charm. I reinstalled again and installed the programs above one by one. couldn't reproduce the error. I have been testing this installation for more than a week, installing and removing many things. My .djvu files still keep the correct mime type image/vnd.djvu+multipage and evince opens them with no problem.  I still have no idea what might have caused the change of mime type for the two previous runs while the third time it all worked..  Maybe some software was updated in the official channel between my reinstallations so running apt upgrade after fresh install solved it?

Anyway I will mark this thread as solved even though the mystery remains.

---

### Post by oriel3 on 2018-07-31
After I had uninstalled djvulibre, Evince opened djvu files.

---

### Post by monkeybrain20122 on 2018-08-16
After working for a while, then after some updates, installing something etc etc then out of the blue it happens again all the .djvu files are identified as "image/vnd.djvu" instead of the correct "image/vnd.djvu+multipage"

> After I had uninstalled djvulibre, Evince opened djvu files.                         

Yes some people reported that uninstalling  djvulibre-desktop solves their problems, but I have never had djvulibre-desktop installed, and libdjvulibre is a dependency for evince (removing it would remove evince itself)

---

### Post by monkeybrain20122 on 2018-08-16
The issue is why the memetype of these .djvu files are not identified properly by the OS. This has nothing to do with evince in and of itself.

---

