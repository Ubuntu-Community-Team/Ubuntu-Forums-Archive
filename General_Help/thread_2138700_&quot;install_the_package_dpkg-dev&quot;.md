---
title: "&quot;install the package dpkg-dev&quot;???"
date: 2013-04-25
forum: General Help
---

### Post by rhythmiccycle on 2013-04-25
i'm trying to install a program from a tar.gz file. In the provided READ ME file it say the next step :

> 
2.5 When the customization file is modified appropriately, you will execute "./customize.sh archive" which will modify all the .deb package files by inserting the contents of the customization file into the maintainer scripts of each package.


but when i try to do that it says i need to install dpkg-dev. the code is shown below:


```

$./customize.sh 
missing /usr/bin/dpkg-scanpackages
please install the package dpkg-dev before using this script


```


 I also tried:

```

$ ./customize.sh archive
missing /usr/bin/dpkg-scanpackages
please install the package dpkg-dev before using this script


```



How do i install dpkg-dev?

---

### Post by ninjaondemand on 2013-04-25
The Debian package development tools (dpkg-dev) are easily installable from the software center or by apt-get (sudo apt-get dpkg-dev).

---

