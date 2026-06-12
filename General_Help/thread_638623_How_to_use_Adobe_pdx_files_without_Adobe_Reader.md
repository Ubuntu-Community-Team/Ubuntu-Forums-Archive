---
title: "How to use Adobe pdx files without Adobe Reader?"
date: 2007-12-12
forum: General Help
---

### Post by kcy29581 on 2007-12-12
Hi all,

Does anyone know of an alternative application that can open Adobe pdx indexes (pdx files)?

Thanks

---

### Post by jonathan21 on 2007-12-12
don't you mean pdf files and ubuntu comes with a pdf reader its called evince to open ope terminal and type evince

---

### Post by kcy29581 on 2007-12-12
> **jonathan21 said:**
> don't you mean pdf files and ubuntu comes with a pdf reader its called evince to open ope terminal and type evince

No, I put pdx twice,  used the word "indexes", and put it in brackets as well.

Pdx files are indexes that allow you to search content within pdf files that are in that index.

So back to the question:  Does anyone know of an alternative application that can open Adobe pdx indexes (pdx files)?

Thanks

---

### Post by mahiyar on 2007-12-12
I think pdx file extension are too closely linked with microsoft to entertain linux (if it is the same as product data exchange) however i found this for you hope it helps [http://www.guh-software.de/pdxviewer/PDXViewer_1_5_unix_en.sh](http://www.guh-software.de/pdxviewer/PDXViewer_1_5_unix_en.sh)

---

### Post by kcy29581 on 2007-12-12
> **mahiyar said:**
> I think pdx file extension are too closely linked with microsoft to entertain linux (if it is the same as product data exchange) however i found this for you hope it helps [http://www.guh-software.de/pdxviewer/PDXViewer_1_5_unix_en.sh](http://www.guh-software.de/pdxviewer/PDXViewer_1_5_unix_en.sh)

Thanks, but I think this is not the same thing. I'd be very surprised if other enterprise users have not wondered this.

---

### Post by Clopper Almon on 2008-03-10
I also needed to use .pdx files on Ubuntu 7.10, and have managed to do so. What I have is not exactly "without Adobe Reader"; rather it is Adobe Reader working on Ubuntu Linux as if it were born there.  If that is good enough, read on. 

First I googled "Adobe Reader Linux"  and found a Linux version of Adobe Reader on the Adobe website.  I downloaded it to my desktop.  There was a problem, however.  It was a .rpm package for Red Hat, not Ubuntu.  So I first had to convert it to a .deb package.  There is a program called alien which does just that.  There is a good description of how to use alien at 

[http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/](http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/)

I followed the directions there except that on the line 
$sudo alien -k name-of-rpm-file.rpm
I also needed the -scripts option, thus
$sudo alien -k -scripts name-of-rpm-file.rpm

That produced a .deb package which I installed with dpkg.

The installation produced an executable file named acroread at the following location:
/opt/Adobe/Reader8/bin/acroread

I then put a launcher on my desktop pointing to this file, and now can use existing .pdx files from Ubuntu just as well as from Windows.  To make a .pdx file, of course, you need Adobe professional, and that is, I believe, still available only for Windows. 

PDX files are indeed very useful for indexing a large collection of PDF files.  Hope this procedure works for you.
:KS

---

### Post by wanchai on 2008-03-17
First off: you can find a Debian package on the Adobe website. When you are at the download page for the reader, click "Different language or operating system?". That gets you to a page where you can select the installer. Here is a shortcut: [http://www.adobe.com/products/acrobat/readstep2_allversions.html](http://www.adobe.com/products/acrobat/readstep2_allversions.html)

Back to the index files. I have a bunch of documentation CDs from Nortel, they are using PDX files and they are quite essential for finding things. When I open one of the PDF files in Acrobat Reader 7.0.0 or 8.1.2 under W2k, I have no problem. If I open the exact same file with acroread 7.0.8 or 8.1.2 under Ubuntu, I get error messages telling me that the "index is either corrupt or is not compatible with this version."

Do the PDX files work for other people out there?

---

