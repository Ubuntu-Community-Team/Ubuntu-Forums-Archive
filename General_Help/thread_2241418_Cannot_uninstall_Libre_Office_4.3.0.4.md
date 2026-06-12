---
title: "Cannot uninstall Libre Office 4.3.0.4"
date: 2014-08-26
forum: General Help
---

### Post by Gordonbp531 on 2014-08-26
I uninstalled the version of LO supplied in 14.04 and replaced it with the latest version (4.3.0.4) using downloaded deb packages.
I now need to revert to the supplied version.
However, when I try to uninstall using
[TABLE="class: outer_border, width: 500, align: left"]
[TR]
[TD]sudo dpkg -P libreoffice
[/TD]
[/TR]
[/TABLE]

 
I get this error message:

dpkg: warning: ignoring request to remove libreoffice which isn't installed

How can I uninstall?

---

### Post by varunendra on 2014-08-26
libreoffice is just a metapackage that installs all the required components. Removing it, even if it were installed, wouldn't remove those other packages that it would have installed.

You'll need to purge those individual packages that you installed manually. Perhaps cumbersome, but the only way. And be VERY CAREFUL about NOT removing anything that may break the system (some critical dependency that may get purged along with any of the packages).

---

