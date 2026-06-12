---
title: "Upgrading svn to 1.5"
date: 2008-06-25
forum: General Help
---

### Post by sipickles on 2008-06-25
Hi,

can anyone help me upgrade subversion to 1.5? I need the version number to match with tortoiseSVN on Windoze which uses subversion 1.5.

I downloaded the source, did:

./configure
make
sudo make install

but 'svn --version' still outputs:

svn, version 1.4.6 (r28521)
   compiled Mar 11 2008, 08:53:49

Thanks

Simon


--

Solved - just had to uninstall the deb version

---

### Post by The Rocker on 2008-07-06
I'm needing to do this too.  I found an RPM package and can use Alien to convert it to DEB.  I tried this however and was still getting v. 1.4.  What did you do to get 1.5 to be active?

And does anybody know when Subversion 1.5 will be available as an Ubuntu update?

---

### Post by jsma on 2008-07-07
Have you tried removing the old version, e.g. `sudo apt-get remove subversion`?
I installed from source and so far have not experienced any troubles.

---

### Post by sipickles on 2008-07-07
I just uninstalled the package and used the version I had built from source.

---

