---
title: "Uninstalling a program that's not in Synaptic"
date: 2007-08-22
forum: General Help
---

### Post by Zikes on 2007-08-22
Some time ago I downloaded and installed Scribes, compiling it from source.  I've since decided that it's not the right text editor for me, and would like to uninstall it, but it's not listed in Synaptic and I've already deleted the source files so I can't make uninstall it.  The Scribes site only has a newer version of the program posted on their site, so I apparently can't just download the source again.  What options are available to me?

---

### Post by MeneM on 2007-08-22
Ooh you're right, even this page only shows the latest release: [http://sourceforge.net/project/showfiles.php?group_id=143967]("http://sourceforge.net/project/showfiles.php?group_id=143967")

Could you not download the latest version, install (upgrade) the version you have and then uninstall using the newer source?

---

### Post by PentaxFollower on 2007-08-22
To avoid such situations in future consider using 'checkinstall'. It makes deb package from given sources, so you can uninstall it later in Synaptic.
Usage is similar to standard configure/make/make install.
You just type:
```
./configure
make
make checkinstall
```
and then follow simple dialog.

---

