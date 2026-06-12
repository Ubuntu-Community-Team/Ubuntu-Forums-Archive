---
title: "Sage the math program install packages?"
date: 2007-12-09
forum: General Help
---

### Post by underwater on 2007-12-09
Hello,

I've noticed that there is no package in the repos for sage, and I was wondering if other people knew of a package or if not, what installation method they chose to use.  Using the tar.gz provided by sage's website seems to contain a lot of redundant stuff that I probably already have installed on my system(Like Java)  


Can anyone offer advice?  

Thanks in advance,
Underwater

---

### Post by niteshifter on 2007-12-09
What's provided in sage-2.8.12-ubuntu-i686-Linux.tar.gz is a pre-built package, so yes there is some duplication. However it allows you to try SAGE without going through a very lengthy and possibly tricky make process. One just unpacks it, cd to sage-2.8.12-ubuntu-i686-Linux (or you can rename it BEFORE you use it to somethong short like sage.d for example), cd to that folder and type ./sage to enter the SAGE environment. 

I placed it in my home folder as I'm the only user of this box, so I didn't really look to see if any problems would arise by placing in /opt and tacking /opt/sage.d to $PATH.

Notice that they do provide a complete sources package, you can always do a traditional build with those. But using the pre-built does give the advantage of not changing any system files and makes removal easy enough - just delete it.

sage-2.8.12-ubuntu-i686-Linux.tar.gz unpacks to 591MB, BTW. Make sure you have room for it.

The Notebook feature is way cool also!

---

