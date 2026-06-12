---
title: "How do you uninstall a source-base installation?"
date: 2012-10-22
forum: General Help
---

### Post by Randy Schilling on 2012-10-22
How do you uninstall a source-based installation?
The problem I guess is that the installation may scatter
files throughout the Linux file system.

Thanks, Randy

---

### Post by mikewhatever on 2012-10-22
Usually, you'd run 'sudo make uninstall' from the source directory.

---

### Post by neo_1in on 2012-10-22
A source based install is no different from a package manager based install in terms of 'scattering' of files. Its just that package managers keep a record of all those files, whilst in case of source based installs you'll have to look for the log of installation and delete individual files manually (i.e. in case mikewhatever's solution doesn't work). Usually I save the install log whenever doing an installation from a source file as i delete the source folder after installation.

---

### Post by Randy Schilling on 2012-10-23
Thanks Thanks Thanks

---

