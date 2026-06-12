---
title: "How do I find the versions of software on older versions?"
date: 2013-07-31
forum: General Help
---

### Post by ken3 on 2013-07-31
Hi,

I need to set up a couple VMs for support of legacy systems.  I DO NOT WANT UPDATES, so a stale *buntu would be wonderful.

What I would like is to know how to figure out what versions of certain packages are released with each version of *buntu.  I would also like to keep this lightweight, so maybe xubuntu.

Last time I did this I just went to the FTP server and browsed all the package trees.  Things have changed since then.

Thanks.

---

### Post by lah7 on 2013-07-31
I would suggest installing a package manager like **Synaptic Package Manager**; it's not too heavy, only needing 7.8 MB of disk space. It'll be able to tell you every package installed and their version numbers.

---

### Post by oldfred on 2013-07-31
You can download the manifests, change to release you want and then within release which version:

 Look for manifests for version:
[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

---

### Post by ken3 on 2013-08-01
@lah7, I'm trying to select the version of *buntu by the versions of the packages installed, for example mysql 5.1.  Synaptic (or more likely aptitude) are well traveled ground for me.  :)

@oldfred, this seems to be exactly what I'm after.  Thanks.

---

