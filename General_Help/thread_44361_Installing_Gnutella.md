---
title: "Installing Gnutella"
date: 2005-06-25
forum: General Help
---

### Post by scott9027 on 2005-06-25
scott@ubuntu:~$ sudo apt-get install gtk-gnutella
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gtk-gnutella
scott@ubuntu:~$

This is what I get when I try to install Gnutella client.  I downloaded it from sourceforge.net.  How can I tell it where to get the file that I downloaded?

---

### Post by tonym on 2005-06-26
I assume you have downloaded a .deb file.  Its not clear from the sourceforge site what versions of Debian / Ubuntu / etc these are compatible with but to install you need to do

dpkg -i filename.deb

Alternatively,  gtk-gnutella is in the Ubuntu universe repository.  You could enable that repository and then install with apt-get.

Regards

Tony

---

