---
title: "etc-update"
date: 2004-10-29
forum: General Help
---

### Post by diebels on 2004-10-29
Is there any tools for merging of new config files in ubuntu, similar to etc-update in gentoo ?[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=3&chap=4#doc_chap1](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=3&chap=4#doc_chap1)

---

### Post by triad169 on 2004-10-29
Quoted From [http://www.linuxforum.com/debian/ch-system.en.html](http://www.linuxforum.com/debian/ch-system.en.html)  :

"2.2.4 Preservation of the local configuration

Preservation of user-configurable files is enabled through Debian's "conffiles" mechanism. User configuration files (usually placed in /etc/) are specified in the conffiles within the Debian package system. The package management system guarantees not to overwrite these files when the package is upgraded.

When it is possible to configure the system without modifying files that belong to various Debian packages, it is usually a good idea not to modify them even if they are "conffiles". This ensures faster and smoother upgrade operations.

To determine exactly which files are preserved during an upgrade, run:

     dpkg --status package

and look under "Conffiles:".

Specifics regarding the contents of a Debian conffiles file are provided in the Debian Policy Manual, section 11.7 (see References, Section 15.1). "


You can look at .conffiles in your /var/lib/dpkg/info directory. 

Triad

---

### Post by jdong on 2004-10-29
yeah, Debian asks about such changes when installing a package with an updated conf file. The options are quite similar to Gentoo's.

---

### Post by diebels on 2004-10-29
Ok, from what I can see in the documents dpkg preserves configuration files and only overwrites files that's not modified by the user and have the correct md5sum, but don't have any functions for merging of a new version from the package maintainer with a file that has been modified by the user. Right?

So when I edit /etc/gdm/gdm.conf for setting a user to autologin, and updates gdm, dpkg detects that the md5sum is incorrect and asks me what to do but I have no merging option.

And some packages have local configuration that is preserved between upgrades, but the gdm maintainer have not bothered to putting any local configuration options in the gdm package.

Debian have no configuration-file merging tools that works indepent of package maintainers decisions.

Right?

---

