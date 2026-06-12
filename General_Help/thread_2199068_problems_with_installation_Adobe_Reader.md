---
title: "problems with installation Adobe Reader"
date: 2014-01-12
forum: General Help
---

### Post by mrayo on 2014-01-12
Hi everyone,
I have been trying to install Adobe Reader in Ubuntu 12.04 LTS, I have read some posts and how to install it using the terminal. I suceed in having the icon of Adobe but it is not running. One of the lines that shows in terminal when I do the first step for Adobe installation said


----------------------------------------
sudo apt-get update


Get:59 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) precise-backports/universe Translation-en [27.7 kB]
Fetched 4,590 kB in 12s (361 kB/s)                                             
W: Failed to fetch [http://archive.canonical.com/dists/](http://archive.canonical.com/dists/)[distro]/partner/source/Sources  404  Not Found [IP: 91.189.92.191 80]

W: Failed to fetch [http://archive.canonical.com/dists/](http://archive.canonical.com/dists/)[distro]/partner/binary-amd64/Packages  404  Not Found [IP: 91.189.92.191 80]

W: Failed to fetch [http://archive.canonical.com/dists/](http://archive.canonical.com/dists/)[distro]/partner/binary-i386/Packages  404  Not Found [IP: 91.189.92.191 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

-------------
My question is if that could be the explanation for the unsuccessful installation? 
Any help??

Thanks

---

### Post by grier-devon on 2014-01-12
Are we talking about Adobe Reader 9? The on in the repositories? If you do not see that one then make sure to enable the Canonical Partners in the software sources. Adobe Reader 9 was the last compatiable version for Linux, however you could try wine for latest version but I have not had much luck with it working.

---

### Post by mrayo on 2014-01-12
Yes, I am talking about Adobe Reader 9. I did that, I enable the Canonical Parthers via the terminal. I see Adobe Reader but it does not open any document

---

### Post by mrayo on 2014-01-12
I tried to install it again, at the end there are errors

------------------------------------
 Selecting previously unselected package acroread.
Unpacking acroread (from .../acroread_9.5.5-1precise1_amd64.deb) ...
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/acroread-bin_9.5.5-1precise1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
------------------------------------------

Please, help!!

---

### Post by grier-devon on 2014-01-12
Honestly man Adobe Reader 9 is so old now the stock document viewer may be better. I did some searching on the topic and it looks like a lot of people are complaining of it breaking, looks like time retire reader. If I may ask what is the specific feature of Adobe Reader you need that Document Viewer cannot do?

---

### Post by mrayo on 2014-01-22
Hi,
I finally manage to install Adobe Reader but it is giving me troubles now with the ubuntu updates :(
The features that I am looking is to copy images and the Document viewer it can not do this.
Anyway thanks for your help!!

---

### Post by Buntu Bunny on 2014-01-22
I don't believe much support is given for Adobe Reader 9 any more. I just tried to copy an image and paste into LibreOffice, but it pasted a big black square. Unfortunately, there aren't a lot of choices for Ubuntu. However, here are instructions for doing it via the command line - [How to Extract Images from PDF Documents in Ubuntu/Linux]("https://ubuntugenius.wordpress.com/2012/02/04/how-to-extract-images-from-pdf-documents-in-ubuntulinux/")

---

