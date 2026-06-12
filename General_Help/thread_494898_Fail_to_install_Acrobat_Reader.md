---
title: "Fail to install Acrobat Reader"
date: 2007-07-07
forum: General Help
---

### Post by satimis on 2007-07-07
Hi folks,

Ubuntu Desktop 7.04

I have  AdobeReader_enu-7.0.9-1.i386.rpm download on Adobe site.

$ which rpm
did not find it.


rpm installation;
$ sudo apt-get install rpm
it went through w/o complaint.

packages installed are;```

libbeecrypt6
librpm4
Suggested packages:
alien

The following NEW packages will be installed:
libbeecrypt6 librpm4 rpm

```


$ which rpm
/usr/bin/rpm


$ sudo rpm -ivh AdobeReader_enu-7.0.9-1.i386.rpm ```

error: Failed dependencies:
        /bin/sh is needed by AdobeReader_enu-7.0.9-1.i386
        gtk2 >= 2.4.0 is needed by AdobeReader_enu-7.0.9-1.i386
        libGL.so.1 is needed by AdobeReader_enu-7.0.9-1.i386
        libGLU.so.1 is needed by AdobeReader_enu-7.0.9-1.i386
        libX11.so.6 is needed by AdobeReader_enu-7.0.9-1.i386
        libXext.so.6 is needed by AdobeReader_enu-7.0.9-1.i386
        libXt.so.6 is needed by AdobeReader_enu-7.0.9-1.i386
        libatk-1.0.so.0 is needed by AdobeReader_enu-7.0.9-1.i386
        libc.so.6 is needed by AdobeReader_enu-7.0.9-1.i386
        libc.so.6(GLIBC_2.0) is needed by AdobeReader_enu-7.0.9-1.i386
        libc.so.6(GLIBC_2.1) is needed by AdobeReader_enu-7.0.9-1.i386
        libc.so.6(GLIBC_2.1.2) is needed by AdobeReader_enu-7.0.9-1.i386
        libc.so.6(GLIBC_2.1.3) is needed by AdobeReader_enu-7.0.9-1.i386
        libc.so.6(GLIBC_2.2) is needed by AdobeReader_enu-7.0.9-1.i386
        libc.so.6(GLIBC_2.2.4) is needed by AdobeReader_enu-7.0.9-1.i386
        libc.so.6(GLIBC_2.3) is needed by AdobeReader_enu-7.0.9-1.i386
        libc.so.6(GLIBC_2.3.2) is needed by AdobeReader_enu-7.0.9-1.i386
        libdl.so.2 is needed by AdobeReader_enu-7.0.9-1.i386
        libdl.so.2(GLIBC_2.0) is needed by AdobeReader_enu-7.0.9-1.i386
        libdl.so.2(GLIBC_2.1) is needed by AdobeReader_enu-7.0.9-1.i386
        libfontconfig.so.1 is needed by AdobeReader_enu-7.0.9-1.i386
        libgdk-x11-2.0.so.0 is needed by AdobeReader_enu-7.0.9-1.i386
        libgdk_pixbuf-2.0.so.0 is needed by AdobeReader_enu-7.0.9-1.i386
        libgdk_pixbuf_xlib-2.0.so.0 is needed by AdobeReader_enu-7.0.9-1.i386
        libglib-2.0.so.0 is needed by AdobeReader_enu-7.0.9-1.i386
        libgmodule-2.0.so.0 is needed by AdobeReader_enu-7.0.9-1.i386
        libgobject-2.0.so.0 is needed by AdobeReader_enu-7.0.9-1.i386
        libgtk-x11-2.0.so.0 is needed by AdobeReader_enu-7.0.9-1.i386
        libm.so.6 is needed by AdobeReader_enu-7.0.9-1.i386
        libm.so.6(GLIBC_2.0) is needed by AdobeReader_enu-7.0.9-1.i386
        libm.so.6(GLIBC_2.1) is needed by AdobeReader_enu-7.0.9-1.i386
        libpango-1.0.so.0 is needed by AdobeReader_enu-7.0.9-1.i386
        libpangox-1.0.so.0 is needed by AdobeReader_enu-7.0.9-1.i386
        libpthread.so.0 is needed by AdobeReader_enu-7.0.9-1.i386
        libpthread.so.0(GLIBC_2.0) is needed by AdobeReader_enu-7.0.9-1.i386
        libpthread.so.0(GLIBC_2.1) is needed by AdobeReader_enu-7.0.9-1.i386
        libpthread.so.0(GLIBC_2.2) is needed by AdobeReader_enu-7.0.9-1.i386
        libpthread.so.0(GLIBC_2.3.2) is needed by AdobeReader_enu-7.0.9-1.i386
        libresolv.so.2 is needed by AdobeReader_enu-7.0.9-1.i386
        libresolv.so.2(GLIBC_2.2) is needed by AdobeReader_enu-7.0.9-1.i386
        librt.so.1 is needed by AdobeReader_enu-7.0.9-1.i386
        libz.so.1 is needed by AdobeReader_enu-7.0.9-1.i386

```

It needs so many dependencies.  What can I do?  To download the tarball?

Tks


B.R.
satimis

---

### Post by cragged6 on 2007-07-07
rpm is for redhat (and others) apt is debian (like ubuntu). someone may have work arounds, but why not enable extra repositories and then

```
sudo apt-get install acroread 
```

---

### Post by satimis on 2007-07-07
> **cragged6 said:**
> rpm is for redhat (and others) apt is debian (like ubuntu). someone may have work arounds, but why not enable extra repositories and then

```
sudo apt-get install acroread 
```
Hi cragged6,

I tried before download AdobeReader_enu-7.0.9-1.i386.rpm

$ sudo apt-get install acroread
Password:```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package acroread

```

Besides acroread differs from AdobeReader.  Which repo provides acroread?  How to get it installed?  Tks


B.R.
satimis

---

### Post by confused57 on 2007-07-07
This thread should help:
[http://ubuntuforums.org/showthread.php?t=485031&highlight=adobe+reader](http://ubuntuforums.org/showthread.php?t=485031&highlight=adobe+reader)

I think acroread is in the Mediubuntu repositories or you might have better luck installing with the tar.gz download.  See this website for installing software:
[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

---

### Post by cragged6 on 2007-07-08
Or go here:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories)
for adding repositories and then try the sudo apt-get install acroread  (btw they are the same program).  It installs version 7.0.9.

The instructions at [http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/) that Confused57 mentioned are *excellent*, but you might want to go back to adobe and download the .tar.gz file instead of the .rpm you have.

---

### Post by satimis on 2007-07-09
Hi folks,


Tks for your advice and URL.


Have AdobeReader_enu-7.0.9-1.i386.tar.gz  download and installed as follow;

$ tar zxpf AdobeReader_enu-7.0.9-1.i386.tar.gz 

$ sudo AdobeReader/INSTALL
password

It went through w/o complaint

$ which acroread
/usr/bin/acroread


B.R.
satimis

---

