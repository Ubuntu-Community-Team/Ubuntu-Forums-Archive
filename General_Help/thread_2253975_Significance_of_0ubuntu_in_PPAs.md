---
title: "Significance of 0ubuntu in PPAs"
date: 2014-11-24
forum: General Help
---

### Post by Ralph L on 2014-11-24
I have seen several PPAs that have 0ubuntux (x will be a number like 1 or 2) in the package list.  What is the significance of the 0 in front of ubuntu in the package name.  Also, I have seen a few occasions where the preceding number is 1, not 0.  What does this mean?

---

### Post by ian-weisser on 2014-11-24
The preceding number refers to the Debian version. It increments when Debian patches and rebuilds the package, and that rebuilt version gets imported to Ubuntu.
The following number refers to the Ubuntu version. It increments when Ubuntu patches and rebuilds the package.
Source: [http://packaging.ubuntu.com/html/packaging-new-software.html](http://packaging.ubuntu.com/html/packaging-new-software.html)

Example: 

An upstream project releases their jewel, Foo 1.3
It gets imported into Debian as foo-1.3.0
It subsequently gets imported into Ubuntu as foo-1.3.0ubuntu1

Then, upstream fooproject releases a security patch, but doesn't release a new upstream version yet.
Debian applies the patch, and replaces foo-1.3.0 with foo-1.3.1
Ubuntu Security Team also applies the patch and replaces foo-1.3.0ubuntu1 with foo-1.3.0ubuntu2

A few months later, during the next Debian import cycle, the patched Debian package gets imported to Ubuntu.
This package, with the Debian patch instead of the Ubuntu patch, will be foo-1.3.1ubuntu1

Finally, a few weeks after that, after internal recriminations about not releasing a new upstream version faster, fooproject releases Foo 1.4.
And the whole cycle starts over again.

---

### Post by Ralph L on 2014-12-07
Thank you very much for the useful info.

---

