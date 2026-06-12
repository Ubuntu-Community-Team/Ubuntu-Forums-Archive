---
title: "FTP via File Manager"
date: 2007-06-01
forum: General Help
---

### Post by x1a4 on 2007-06-01
Hi,

Is there a way to configure my Xubuntu Feisty to access directories on a remote ftp server the same as I access my local drives?

Thank you.

---

### Post by pbw on 2007-06-02
thunar (default xfce file manager) doesnt support this. But konqueror, nautilus and krusader all do out of the box.. Least i'm fairly sure nautilus does, I don't use it however.

You could also just install fuse, that allows you to mount remote filesystems and access them locally. It's easy and probably the best idea if you're happy with thunar.

-- pbw

---

### Post by x1a4 on 2007-06-02
Thank you.  

Nautilus does the trick but I prefer to use Thunar.  I can't use FUSE because the repositories only have a FUSE module for the 2.6.17 kernel and I'm using 2.6.20.  Is it still possible to use it and if so how?  

I have the following FUSE packages installed: 

afuse
fuse-module-2.6.17-10-generic
fuse-source
fuse-utils
fuseiso
libconfuse0
libfuse2

Thank you

EDIT: This is to access a Linux ftp server

---

### Post by pbw on 2007-06-02
curlftpfs is my preference and what i use. It's in universe, give that a shot it's easy to use. The homepage shows you a couple examples [http://curlftpfs.sourceforge.net/](http://curlftpfs.sourceforge.net/)

-- pbw

---

### Post by x1a4 on 2007-06-02
> **pbw said:**
> curlftpfs is my preference and what i use. It's in universe, give that a shot it's easy to use. The homepage shows you a couple examples [http://curlftpfs.sourceforge.net/](http://curlftpfs.sourceforge.net/)

-- pbw

Worked like a charm.  Thank you.   Linux rocks!

---

### Post by pbw on 2007-06-02
not a prob

---

