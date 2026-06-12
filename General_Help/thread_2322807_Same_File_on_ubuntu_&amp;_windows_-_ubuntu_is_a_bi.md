---
title: "Same File on ubuntu &amp; windows - ubuntu is a bigger size"
date: 2016-04-30
forum: General Help
---

### Post by joey_tbf on 2016-04-30
I have 2 desktops on my network.  I use the second desktop as a backup of my hard drives. 

My first desktop has windows, my backup second desktop has ubuntu. 


The problem is when i copy all the files onto my backup desktop. The total file size is bigger then the windows. This is bad because i am unable to see if i missed any files. 

With windows it is easy because i shows the exact files & size.  


I even clicked on 1 mp3 file and on ubuntu the file size is bigger than windows, on the same mp3 file. 


here is the picture of the size
[http://oi66.tinypic.com/dm9ta8.jpg](http://oi66.tinypic.com/dm9ta8.jpg)


Why is this happening?

---

### Post by oldfred on 2016-04-30
Cannot see from screen shots, but is one MB and other MiB?

       MB vs MiB
[http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)
[http://www.osforge.com/news/001337.html](http://www.osforge.com/news/001337.html)

---

### Post by ajgreeny on 2016-04-30
Yes, I think the likely reason is that the 81.2MB is in MiB and 85.2 is MB; allowing for rounding to a single decimal point, as I think is showing, that is exactly what I would expect

---

### Post by joey_tbf on 2016-04-30
They are both MB



Is there anyway to change it so it shows the exact size and not rounding off?

---

### Post by oldfred on 2016-04-30
They may say MB, but is one really MiB?
Not all software is correct in using MiB when it should.

---

### Post by HermanAB on 2016-05-01
Just for information:
If you use rsync to copy a file, then they are guaranteed to be the same.  
You can also compare files by computing a checksum such as with md5sum.

---

### Post by ajgreeny on 2016-05-01
Does a **Right click -> Properties** on the file in windows show you the exact number of bytes as thunar does? That will give you a definite answer.

---

### Post by joey_tbf on 2016-05-01
if i click on 1 single file:

[ATTACH=CONFIG]268752[/ATTACH]
windows: 8.39MB (8,806,537 bytes)
ubuntu: 8.8MB (8,806,537 bytes) 






If i click on the whole album:
[ATTACH=CONFIG]268753[/ATTACH]
windows: 286MB (300,535,655 bytes) |  35 files, 3 folders
ubuntu:  300.5MB (no bytes displayed)| 38 Items







ubuntu is always more,

---

### Post by deadflowr on 2016-05-01
Windows is using MIB.: mebibytes

Run a Google search for mib to mb converter.
Google puts a converter box in the searches for you to try.

You'll see 8.39 mib comes out to 8.797553 mb.

---

