---
title: "Help installing Floola!  Cannot find correct Libraries"
date: 2007-04-08
forum: General Help
---

### Post by Drunner611 on 2007-04-08
Hey everyone, I cannot install Floola.  It requires certain files that I do not have and cannot find in any online repositories.

ben@C2D:~/Desktop/Floola-linux$ ./Floola
./Floola: error while loading shared libraries: libtasn1.so.2: cannot open shared object file: No such file or directory

There were several other libraries such as this that I found and downloaded, but I cannot find this one. 

Also

ben@C2D:~/Desktop/Floola-linux$ sudo apt-get install libtasn1-2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libtasn1-2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libtasn1-3-bin
E: Package libtasn1-2 has no installation candidate


And I have already installed libtasn 1-3-bin.

Please help, I would like to have a good media player in Gnome such as Amarok is for KDE.

I'm running 64-bit Feisty.

---

### Post by Drunner611 on 2007-04-08
No one's got this library sitting around?  I googled but to no avail.  All help is greatly appreciated

---

### Post by qpwoeiruty on 2007-04-08
Try the edgy package: [http://packages.ubuntu.com/edgy/libs/libtasn1-2](http://packages.ubuntu.com/edgy/libs/libtasn1-2)
then cd to the place you downloaded it and: dpkg -i <filename>

---

