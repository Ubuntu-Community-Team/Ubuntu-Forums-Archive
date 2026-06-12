---
title: "What is the difference between a package and a software in ubuntu?"
date: 2015-05-30
forum: General Help
---

### Post by wisdom2 on 2015-05-30
It is a very basic question however i cannot find the answer. I wonder the difference between package and software. 

By giving command, sudo apt-get install filezilla, the package named filezilla and other dependent packages are downloaded. OK. This is package.

Then, what is software ? All things are packages in ubuntu, right? Or is there any software? If yes, what exactly is a software?

Bu using ubuntu software center, do i install packages or software?

Thanks in advance.

---

### Post by grahammechanical on 2015-05-30
Software is a computer program that runs on computer hardware. Computer programs are made up of various files that interact with each other as the program is run. Package all those files together in an archive and you have what in Linux is called a package.

Packages are always dependant on other packages (dependencies or depends) which must also be downloaded and installed at the same time. Package software formats are designed to take care of that for us. Ubuntu is built on Debian and so at present Ubuntu uses the Debian software package format.

Ubuntu developers have created a modified version of Debian packaging called Click packaging which is used on the Ubuntu Phone. Click packaging is evolving into Snap packaging and over the next 12 months a version of Ubuntu desktop will be produced that uses the Snap package format instead of Debian packaging.

[http://en.wikipedia.org/wiki/Software](http://en.wikipedia.org/wiki/Software)

[http://en.wikipedia.org/wiki/Package_format](http://en.wikipedia.org/wiki/Package_format)

[http://en.wikipedia.org/wiki/Deb_%28file_format%29](http://en.wikipedia.org/wiki/Deb_%28file_format%29)

Regards.

---

### Post by ian-weisser on 2015-05-30
Software can be distributed in many ways: Packages, tarballs, source code, etc.

Packages are a standardized way of safely distributing and installing software. Packages are not the only way to distribute and install software.

In Debian-based systems, packages were developed in response to the shortcomings of tarballs and compiling-from-source and other older methods. If you have installed software the other ways, you can appreciate how convenient packages are.

Apt (including apt-get) is the Debian tool for packages only. You use different tools for unpacking tarballs and compiling.

---

### Post by tgalati4 on 2015-05-30
All packages are software, but not all software are packages.  You have Red Hat packages (*.rpm) and Debian packages (*.deb) as two different software pools.  The Software Center makes it easy to install packages.  You can use *synaptic*, *aptitude*, *apt-get*, *dpkg*, or manually insert the binary files into the correct system folders.  Try them all and you will see the differences.

---

