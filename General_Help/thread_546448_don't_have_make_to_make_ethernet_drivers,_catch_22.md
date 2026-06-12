---
title: "don't have make to make ethernet drivers, catch 22"
date: 2007-09-08
forum: General Help
---

### Post by REXz on 2007-09-08
Hi. I need to compile ethernet drivers for linux but my ubuntu install doesn't have "make" installed.  I can't download it because I don't have an internet connection. :( 

Can I download the make program(not the ubuntu package) to a flash drive or something and install it and make my ethernet drivers or is there a better way?  Thanks.

---

### Post by fragos on 2007-09-08
The packages you want is called build-essential, linux-headers-2.6.20-16-generic and perhaps linux-source-2.6.20.  These deb packages can be downloaded.

---

### Post by REXz on 2007-09-08
Can I install the deb packages from the file system as opposed to having apt or whatever fetch and install them from the web?

---

### Post by REXz on 2007-09-08
Think I found the answer here:

[http://www.newlinuxuser.com/howto-install-deb-rpm-and-source-code-files/](http://www.newlinuxuser.com/howto-install-deb-rpm-and-source-code-files/)


> 

Quick Ref:
if you’ve already downloaded the deb file and have it on your hard drive run this…
#: sudo dpkg -i /path/to/deb/file.deb


---

### Post by flloyd on 2007-09-08
You can download the needed .deb packages from: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

