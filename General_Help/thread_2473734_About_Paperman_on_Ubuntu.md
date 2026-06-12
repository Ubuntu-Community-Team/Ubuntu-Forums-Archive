---
title: "About Paperman on Ubuntu"
date: 2022-04-12
forum: General Help
---

### Post by satimis on 2022-04-12
Hi all,

Can Paperman be installed on Ubuntu to read PaperPort .max files?

Paperman
[https://github.com/sjg20/paperman](https://github.com/sjg20/paperman)

Regards

---

### Post by ActionParsnip on 2022-04-12
[https://github.com/sjg20/paperman/blob/master/INSTALL](https://github.com/sjg20/paperman/blob/master/INSTALL)

Don't see why not

---

### Post by satimis on 2022-04-12
> **ActionParsnip said:**
> [https://github.com/sjg20/paperman/blob/master/INSTALL](https://github.com/sjg20/paperman/blob/master/INSTALL)

Don't see why not
Hi,

I have read;
paperman/INSTALL 
[https://github.com/sjg20/paperman/blob/master/INSTALL](https://github.com/sjg20/paperman/blob/master/INSTALL)

```

....
In summary, to prepare on Debian / Ubuntu with QT4:

   sudo apt-get install qtcreator g++ qt5-default libsane-dev libtiff5-dev \
           cmake libpodofo-dev imagemagick tesseract-ocr tesseract-ocr-eng \
           libpoppler-qt5-dev
....

```

libqt5-dev or libqt4-dev
not in repo

$ apt policy libpoppler-qt5-dev```

libpoppler-qt5-dev:
  Installed: (none)
  Candidate: 0.86.1-0ubuntu1
  Version table:
     0.86.1-0ubuntu1 500
        500 http://hk.archive.ubuntu.com/ubuntu focal/universe amd64 Packages

```

$ apt policy libpodofo-dev```

libpodofo-dev:
  Installed: (none)
  Candidate: 0.9.6+dfsg-5build1
  Version table:
     0.9.6+dfsg-5build1 500
        500 http://hk.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
```

$ apt policy libsane-dev```

libsane-dev:
  Installed: (none)
  Candidate: 1.0.29-0ubuntu5.2
  Version table:
     1.0.29-0ubuntu5.2 500
        500 http://hk.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages
     1.0.29-0ubuntu5.1 500
        500 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages
     1.0.29-0ubuntu5 500
        500 http://hk.archive.ubuntu.com/ubuntu focal/main amd64 Packages

```

$ apt policy libtiff5-dev```

libtiff5-dev:
  Installed: (none)
  Candidate: 4.1.0+git191117-2ubuntu0.20.04.2
  Version table:
     4.1.0+git191117-2ubuntu0.20.04.2 500
        500 http://hk.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages
     4.1.0+git191117-2build1 500
        500 http://hk.archive.ubuntu.com/ubuntu focal/main amd64 Packages

```

I have to create 'paperman' myself.

What I expect to find is a Linux package which can convert PaperPort .max file to .pdf file

Regards

---

### Post by ActionParsnip on 2022-04-13
Yes and the paperman package you build yourself will be the package that converts the files....

---

### Post by satimis on 2022-04-14
> **ActionParsnip said:**
> Yes and the paperman package you build yourself will be the package that converts the files....
Thanks.

A further question.  I'm going to build "paperman" on an Ubuntu 20.04 VM of Oracle Virtualbox.  Can I copy this package to be used on another Ubuntu VM?  OR I have to rebuild it?

Regards

---

### Post by ActionParsnip on 2022-04-14
If you use  the "checkinstall" command (I think it's that) then you can make a deb file of your efforts and install easily on other systems.

---

### Post by ActionParsnip on 2022-04-14
I assume that the other systems are the same release of Ubuntu and the same architecture (most likely X64)

---

