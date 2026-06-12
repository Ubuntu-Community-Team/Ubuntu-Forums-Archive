---
title: "Debmirror and Gutsy"
date: 2007-09-06
forum: General Help
---

### Post by piripallo on 2007-09-06
Hi, I'm using the following script to download packages for a local mirror:

debmirror -m --passive --host=archive.ubuntulinux.org --root=ubuntu/ --method=ftp --progress --dist=gutsy,gutsy-updates,gutsy-security,gutsy-backports,gutsy-proposed --section=main,multiverse,universe,restricted --arch=i386 ubuntu/ --ignore-release-gpg

But it doesn't work in gutsy.
It first download Release.gpg files, and packages.gz files, parse them and after instead of starting download .deb packages it say:

Parse Packages and Sources files and add to the file list everything therein.
Download all files that we need to get (49 MiB).
Downloaded 49 MiB in 106s at 467.1 kiB/s
Everything OK. Moving meta files.
Cleanup mirror.
All done.

even if ubuntu directory is empty.

Any idea?
Thank You.

Marco

---

