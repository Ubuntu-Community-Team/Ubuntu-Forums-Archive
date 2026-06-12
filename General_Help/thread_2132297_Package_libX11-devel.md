---
title: "Package libX11-devel"
date: 2013-04-04
forum: General Help
---

### Post by stallm on 2013-04-04
Hi
I am trying to install the cern ROOT software
```

tom@tom-Aspire-5732Z:~/Desktop/root$ ./configure
Configuring for linuxx8664gcc
Checking for GNU Make version >= 3.79.1 ... ok
Checking for libX11 ... no
configure: libX11 (package libX11-devel) MUST be installed

tom@tom-Aspire-5732Z:~/Desktop/root$ sudo apt-get install libX11-devel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libX11-devel

```
I'm a linux novice, so I'm having problems understanding what is needed here. I have the packages libX11-6 and libX11-dev installed, but no help
Thanks

---

### Post by Cheesemill on 2013-04-04
According to the prerequisite instructions the packages name is libx11-dev not libX11-devel.
Is that what you have installed?

[http://root.cern.ch/drupal/content/build-prerequisites](http://root.cern.ch/drupal/content/build-prerequisites)

---

### Post by schragge on 2013-04-04
Hopefully, [post=12578130]this post[/post] about package naming in Debian may be of some help. Basically, Debian (and Debian-based distributions by extension) prefers consistency over authenticity and renames several kinds of packages like libraries.
[highlight]Edit[/highlight]
Just noticed that on the page linked by **Cheesemill** there is a section devoted to Ubuntu, so the point of guessing right package names is moot in this case.

---

### Post by Cheesemill on 2013-04-04
It's compiling fine on my machine, I just used the following commands...
```
sudo apt-get install subversion dpkg-dev make g++ gcc binutils libx11-dev libxpm-dev libxft-dev libxext-dev checkinstall
mkdir ~/build
cd ~/build
svn co http://root.cern.ch/svn/root/trunk root
./configure
make
sudo checkinstall
```

---

### Post by stallm on 2013-04-04
Yes, I have libx11-dev
```

tom@tom-Aspire-5732Z:~/Desktop/root$ sudo apt-get install libx11-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libx11-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by stallm on 2013-04-04
Cheesemill, that worked. Thank you.

---

