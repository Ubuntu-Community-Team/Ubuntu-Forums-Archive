---
title: "gpar2 problems- can't remove"
date: 2007-01-03
forum: General Help
---

### Post by dragon76 on 2007-01-03
Installed gpar2 using synaptic. In the terminal I got a gpar2.postinst error. I then tried to completely remove. The following is what aptitude remove gpar2 returns:

Reading package lists... Done
Building dependency tree
Reading state information... Done
Initializing package states... Done
Building tag database... Done
The following packages have been automatically kept back:
  libnspr4 libnss3
The following packages have been kept back:
  firefox w3m
The following packages will be REMOVED:
  gpar2
0 packages upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
Need to get 0B of archives. After unpacking 201kB will be freed.
Writing extended state information... Done
(Reading database ... 125640 files and directories currently installed.)
Removing gpar2 ...
***
* Updating MIME database in /usr/share/mime...
Wrote 478 strings at 20 - 27ac
Wrote aliases at 27ac - 2960
Wrote parents at 2960 - 3310
Wrote literal globs at 3310 - 336c
Wrote suffix globs at 336c - 6674
Wrote full globs at 6674 - 6698
Wrote magic at 6698 - bca8
Wrote namespace list at bca8 - bcb8
***
/var/lib/dpkg/info/gpar2.postrm: 33: update-desktop-database: not found
dpkg: error processing gpar2 (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 gpar2
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:


Now synaptic will not install or update any packages because it always tries to remove gpar2 first and it errors out.

any ideas?

Thanks

---

### Post by dragon76 on 2007-01-03
now I am getting an error that the package needs to be reinstalled. when trying to reinstall I get:

Selecting previously deselected package gpar2.
(Reading database ... 125641 files and directories currently installed.)
Preparing to replace gpar2 0.3-1 (using gpar2_0.3-1_i386.deb) ...
Unpacking replacement gpar2 ...
***
* Updating MIME database in /usr/share/mime...
Wrote 480 strings at 20 - 27dc
Wrote aliases at 27dc - 2990
Wrote parents at 2990 - 3340
Wrote literal globs at 3340 - 339c
Wrote suffix globs at 339c - 66a4
Wrote full globs at 66a4 - 66d0
Wrote magic at 66d0 - bce0
Wrote namespace list at bce0 - bcf0
***
/var/lib/dpkg/info/gpar2.postrm: 33: update-desktop-database: not found
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
***
* Updating MIME database in /usr/share/mime...
Wrote 480 strings at 20 - 27dc
Wrote aliases at 27dc - 2990
Wrote parents at 2990 - 3340
Wrote literal globs at 3340 - 339c
Wrote suffix globs at 339c - 66a4
Wrote full globs at 66a4 - 66d0
Wrote magic at 66d0 - bce0
Wrote namespace list at bce0 - bcf0
***
/var/lib/dpkg/tmp.ci/postrm: 33: update-desktop-database: not found
dpkg: error processing gpar2_0.3-1_i386.deb (--install):
 subprocess new post-removal script returned error exit status 127
***
* Updating MIME database in /usr/share/mime...
Wrote 478 strings at 20 - 27ac
Wrote aliases at 27ac - 2960
Wrote parents at 2960 - 3310
Wrote literal globs at 3310 - 336c
Wrote suffix globs at 336c - 6674
Wrote full globs at 6674 - 6698
Wrote magic at 6698 - bca8
Wrote namespace list at bca8 - bcb8
***
/var/lib/dpkg/tmp.ci/postrm: 33: update-desktop-database: not found
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 gpar2_0.3-1_i386.deb


Please help  :confused:

---

### Post by dragon76 on 2007-01-03
now getting the following with apt-get:

E: The package gpar2 needs to be reinstalled, but I can't find an archive for it.

thanks

---

### Post by dragon76 on 2007-01-04
Bump.

Please help - I can't install or uninstall any packages or security updates....

---

### Post by dragon76 on 2007-01-05
Problem solved by following the thread:

[http://www.ubuntuforums.org/showthread.php?t=308544]("http://www.ubuntuforums.org/showthread.php?t=308544")

See also my other thread:

[http://www.ubuntuforums.org/showthread.php?t=331921]("http://www.ubuntuforums.org/showthread.php?t=331921")

---

