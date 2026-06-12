---
title: "Trying to get Epson all in one to scan"
date: 2014-06-08
forum: General Help
---

### Post by john_burns2 on 2014-06-08
I have an Epson Stylus  SX-415 all in one printer scanner (yeah I know Epson support for Linux is pretty poor)  I have managed to get the printer working, but can't scan anything. I have Xsane (0.998) installed. When I tried to use this, a message telling me it needs a backend installing Looking on the internet I have found that it needs backend 1.0.214. I have managed to download this tar.gz file to my desktop. OK what on earth do I do now? Research, suggests I need a degree in computer science. :D:D Opening the terminal fills me with dread, so some extremely simple instructions would be much appreciated. 
Thanks in advance. ;)

---

### Post by MrSteve on 2014-06-08
i have a epson sx435w which prints over wifi but only scans when connected by usb 

i download the required linux drivers from the epson site 
this gives you the scanner drivers for linux place into the search box sx410 ...

[http://download.ebz.epson.net/dsc/search/01/search/searchModuleFromResult](http://download.ebz.epson.net/dsc/search/01/search/searchModuleFromResult)

---

### Post by john_burns2 on 2014-06-08
Thanks Mr Steve, I did try the Epson download page, but it didn't come up with any drivers for my model.. However, I have solved it using the synaptic package manager. Accessed SPM and searched for xsane and sane. Found a package with the same extension  (1.0.2xx) and selected it for installation. Works a treat now and so much easier than trying to use the terminal and the potential to screw my system up. :P:P:P

---

### Post by MrSteve on 2014-06-08
glad you got it fixed ...

---

