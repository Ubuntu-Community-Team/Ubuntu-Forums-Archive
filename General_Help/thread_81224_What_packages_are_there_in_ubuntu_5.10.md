---
title: "What packages are there in ubuntu 5.10?"
date: 2005-10-24
forum: General Help
---

### Post by csscll on 2005-10-24
I'm installing ubuntu 5.10 on a machine that's not connected to the net. As I'll be manually downloading additional packages for software I want to install from packages.ubuntu.com I would like to know what packages are already included in ubuntu 5.10 so that if a file I'm downloading is dependent on files already in the distro release then I know that I don't need to download those dependencies. Thanks.

---

### Post by aysiu on 2005-10-24
I'm not sure if this list is comprehensive, but if you scroll to the bottom of this page...

[http://distrowatch.com/table.php?distribution=ubuntu](http://distrowatch.com/table.php?distribution=ubuntu)

---

### Post by Pausanias on 2005-10-24
If that machine has a DVD drive, you can always download the full DVD version of Breezy. Then you don't have to worry about dependencies.

[http://nginyang.uvt.nl/breezy/](http://nginyang.uvt.nl/breezy/)

---

### Post by csscll on 2005-10-24
[QUOTE=Pausanias]If that machine has a DVD drive, you can always download the full DVD version of Breezy. Then you don't have to worry about dependencies.

[http://nginyang.uvt.nl/breezy/](http://nginyang.uvt.nl/breezy/)[/QUOTE]


Hello, thanks all who replied. I found an easy way to make a list of the packages installed on my ubuntu system 

dpkg -l > mypgks.txt 

and I get a list in the file mypgks.txt. 

BTW, what's in the DVD? More software?

---

### Post by Pausanias on 2005-10-24
Apparently, most of the packages on the main, universe, and multiverse repositories (i.e., almost all software you could possibly install with synaptic) are on the DVDs.

You can also download the same DVD images (md5sums match) at the more official location

[http://cdimage.ubuntu.com/releases/breezy/release/](http://cdimage.ubuntu.com/releases/breezy/release/)

---

