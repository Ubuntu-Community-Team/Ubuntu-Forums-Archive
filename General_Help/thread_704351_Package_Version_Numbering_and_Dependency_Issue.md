---
title: "Package Version Numbering and Dependency Issue"
date: 2008-02-22
forum: General Help
---

### Post by BattlePanic on 2008-02-22
I'm having some trouble understanding the package versioning schemes in the Ubuntu repositories.

Some time ago, I upgraded my installation of Pidgin to 2.3.1-1 by following [this HOWTO]("http://ubuntuforums.org/showthread.php?t=613049"), compiling from source and making a package for my newly compiled version.  I now want to add some plugins for Pidgin, but the plugins' associated pidgin-guifications package is dependent upon Pidgin version 1:2.0 or greater.  It seems that the preceding "1:" in the version number throws everything off and 2.3.1-1 is considered a lower version.  As a result, the package manager won't let me install pidgin-guifications.  I'm assuming that the stock version of Pidgin that I replaced also contained this preceding "1:" in it's version number and thus would have satisfied the dependency.

What does this "1:" in the version number mean?  What would be the reasons for using such a prefix in the version number?  Is there a relatively painless way I can get around this problem?

---

