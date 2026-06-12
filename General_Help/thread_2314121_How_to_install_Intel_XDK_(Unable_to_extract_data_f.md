---
title: "How to install Intel XDK (Unable to extract data from RPM package)"
date: 2016-02-18
forum: General Help
---

### Post by shartazh on 2016-02-18
Hello!
I'm using Lubuntu from Live USB (a few days ago my HDD was broken). I tried to install Intel XDK, but I had a problem - Error message:
 ```
Setup failed!
Installing Intel(R) XDK for Linux* - Core files: ERROR: Unable to extract data from RPM package. Please check that temporary directory is not full.
Please see "/tmp/intel.pset.root.lubuntu_02.18.16.41.42.2016.log" for details. 
```

[ATTACH=CONFIG]267375[/ATTACH]

Can anybody help me?

---

### Post by grahammechanical on 2016-02-18
rpm = Redhat Package Management.

Lubuntu is based upon Ubuntu which is based on Debian and so they all use the Debian package management system. In other words, we install packages with the .deb extension and not the .rpm extension.

So, you are starting this from the wrong place.

Regards.

---

### Post by buzzingrobot on 2016-02-18
It can't be installed on an Ubuntu system, but RPM's, like deb's, are archives that can be extracted.  Try right clicking on the RPM in the file manager to see if the "Extract..." option is offered. (That requires the right archiving tool to be installed; I don't know if it is on Lubuntu.)   At least then  you can see what's in it. Meanwhile, look for a.deb version at the Intel site.

Other things that could cause this failure in a live session is lack of RAM and/or lack of permission to access the right directories. The entire file system is in RAM, along with everything else, so if you try to install or unarchive something that needs more space than is available, it will fail.

---

### Post by QIII on 2016-02-18
Hello, shartazh!

When inserting images, please do not simply paste the image.  Some of our users have slow internet connections and some have data transfer quotas.  For the latter, large images may cause them to go over their quota and cost them actual money.

Please use the attachment functionality provided by clicking the "paper clip" icon above the text input box and uploading the image.  That will cause it to appear as a thumbnail.  Other users can then decide if they want to view the larger image.

Thanks.

---

### Post by shartazh on 2016-02-19
I have 2GB of RAM, Lubuntu getting 250MB :)
When I tried to install XDK, the installer write that Intel XDK was been tested on Ubuntu 10.04+
I don't know how it been tested if install packeg haven't .deb
You can download Intel XDK here [https://software.intel.com/en-us/intel-xdk](https://software.intel.com/en-us/intel-xdk)

---

### Post by shartazh on 2016-02-19
I not faund .deb packages

---

### Post by shartazh on 2016-02-19
It's strange, but on Ubuntu 15.10 XDK was been installed successful!

---

