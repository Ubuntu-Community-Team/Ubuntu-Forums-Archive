---
title: "install tar.gz"
date: 2007-05-24
forum: General Help
---

### Post by atlfalcons866 on 2007-05-24
how  do i install tar.gz?

---

### Post by scampbell on 2007-05-24
tar.gz is a file extension which usually denotes that a set of files/dir tree has been run through the tar program and the gzip program to make an archive.

To open a tar.gz file execute the command:  tar xzvf whatever.tar.gz 
It is often a good idea to do a tar tzvf whatever.tar.gz first to examine the contents of
the "tarball"

Regards,
Sean Campbell

---

### Post by qpieus on 2007-05-24
As scampbell said, the tarball contains the files needed to install whatever program it is you are dealing with. Installing software that comes in a tarball is called installing from source.This link has a good explanation of how to install from source:

[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

You should read that whole webpage BTW, it is helpful in explaining the variuos ways software can be installed in ubuntu. To install from source you need to have the build-essential package installed. You can look for that in synaptic or in a terminal type:```
sudo apt-get install build-essential
```
The link I provided goes on to explain the configure, make , and make install process.

---

### Post by scampbell on 2007-05-24
Thats a very useful link indeed! 
Ive been in fedora/red hat land for the last 6 years
and that link definitely shed some light on things for me,
im learning to love the ease with which debian/ubuntu
handles package management.

---

### Post by rouge568 on 2007-06-04
Thanks for the link - it really helped me out

---

