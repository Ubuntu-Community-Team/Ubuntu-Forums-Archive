---
title: "How to install DEB?"
date: 2012-11-23
forum: General Help
---

### Post by thomo2710 on 2012-11-23
Hi all,

I need to install MegaRaid Software Manager to monitor my raid.

The official LSI instructions say i need to bodge it to install it on Ubuntu!!!!

But im stuck at step 1

1. check for the existence of /bin/csh. If it is not present, then install the Linux software component DEB that provides /bin/csh.This is available as part of Debian OS DVD.
It doesnt exist.

Help........... :)

---

### Post by Lars Noodén on 2012-11-23
Look in the Software Center for the package 'csh'. Or use Synaptic or apt-get.  However, that sounds strange.  Scripts generally use a plain 'sh' or occasionally 'bash'.  The shell 'csh' almost never, ever enters the picture.

What is the link you got your .deb file from?  A closer look at that might provide some insight in how to install it.

---

### Post by philinux on 2012-11-23
```
apt-cache policy csh
csh:
  Installed: (none)
  Candidate: 20110502-2ubuntu1
  Version table:
     20110502-2ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages

```

```
sudo apt-get install csh
```

csh = Shell with C-like syntax


Have you got the link to the tutorial you're following?

---

### Post by thomo2710 on 2012-11-23
Yes - here is the link

[http://kb.lsi.com/Attachment782.aspx](http://kb.lsi.com/Attachment782.aspx)

---

