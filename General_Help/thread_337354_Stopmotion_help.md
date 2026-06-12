---
title: "Stopmotion help"
date: 2007-01-12
forum: General Help
---

### Post by namelessone on 2007-01-12
I recently download this great program called stopmotion from the ubuntu repositories. All was going fine...for a while. Suddenly, the program crashed, and now it won't start back up with error > Segmentation Fault (core dumped)

From reading around it seems this is some sort of bug, but this bug has been fixed in the most recent version--which is not available in the ubuntu repositories. On the stopmotion website there was a link for a .deb of the newest version, but when it tried to install I got this error:

> Error: Dependency is not satisfiable: libqt4-core

I have libqt4-core. What is the matter?

Any help would be appreciated.

---

### Post by kperkins on 2007-03-06
The libqt4-core problem is that the wrong version is installed on Edgy.  Newest stopmotion needs 4.2.1, and 4.2.0 is installed on edgy.  Looks like a dependency PIA to get newest version of libqt4-core installed, also.  Probably Feisty has it.

---

