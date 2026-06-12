---
title: "dpkg --get-selections &gt; ~/my-packages  options"
date: 2013-03-25
forum: General Help
---

### Post by Redalien0304 on 2013-03-25
Used "dpkg --get-selections > ~/my-packages" on my Laptop 32 bit to get copy of my packages to put on my Desktop 64 bit. dpkg also included my linux kernel 3.2.0-39 generic which installed on my Desktop 64 bit. is there way to exclude a kernel?? What other options are there besides dpkg??
did everything from here
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
[http://ubuntuforums.org/showthread.php?t=1139264&p=7157175#post7157175](http://ubuntuforums.org/showthread.php?t=1139264&p=7157175#post7157175)

---

### Post by schragge on 2013-03-26
To exclude specific kernel package:
```
dpkg --get-selections|sed '/^linux-image-3\.2\.0-39-/d' >my-packages
```
To exclude all installed kernel packages:
```
dpkg --get-selections|sed '/^linux-image-[0-9]/d' >my-packages
```
To exclude all kernel-related packages:
```
dpkg --get-selections|sed /^linux-/d >my-packages
```

---

### Post by oldfred on 2013-03-26
The list is just a text file. 
I go in and edit out kernels and a few old packages I know I do not want to reinstall or should have housecleaned before. 

If upgrading from an older version you may run into old version ran OpenOffice and new installs LibreOffice & you do not need both. Again just edit out of text file.

---

### Post by Redalien0304 on 2013-03-26
ok thanks. one more question will this work From Ubuntu to Linux mint?? from one Distribution to a Different Distribution? 32 or 64 bit

---

### Post by oldfred on 2013-03-27
It depends on repository and available programs by name, so I do not know about different distributions. Non-Debian based systems do not use apt, so they definitely will not work.

But I used it to convert from 32bit to 64bit. The list is just the program names, not versions. Again with 32bit there may be some things you do not need to install in the 64 bit version. But if you have a lot of installed programs it greatly simplifies reinstalling them. It will not reinstall something already installed.

The dpkg also includes depends, so list is very long. You can generate top level only lists, but they will not work easily as a list to reinstall.
 Top level only - no depends
sudo apt-get install aptitude
aptitude --disable-columns -F '%p' search '~i!~M!~R(~i)' > toplevel 
or
aptitude search '?installed ?not(?reverse-depends(?installed))'

You can also look at your server for the repositories and download the list of default apps.

 Look for manifests for version:
[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

---

