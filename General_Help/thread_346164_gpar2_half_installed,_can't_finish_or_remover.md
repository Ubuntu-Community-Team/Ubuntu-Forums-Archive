---
title: "gpar2 half installed, can't finish or remover"
date: 2007-01-25
forum: General Help
---

### Post by Drooling_Sheep on 2007-01-25
On kubuntu edgy, I tried to install a gpar2 .deb from that project's sourceforge.  It will not install because I don't have the program update-desktop-database.  It won't let me remove it without finishing the install, and I can't finish the install.  It won't let me install anything else until I resolve the issue with this package.  I don't want to break things any further, so I'm going to the experts.  
```
kopec@kopec-laptop:~$ sudo dpkg -i temp/gpar2_0.3-1_i386.deb
(Reading database ... 181428 files and directories currently installed.)
Preparing to replace gpar2 0.3-1 (using temp/gpar2_0.3-1_i386.deb) ...
Unpacking replacement gpar2 ...
***
* Updating MIME database in /usr/share/mime...
Wrote 480 strings at 20 - 27dc
Wrote aliases at 27dc - 2990
Wrote parents at 2990 - 3340
Wrote literal globs at 3340 - 339c
Wrote suffix globs at 339c - 66f4
Wrote full globs at 66f4 - 6720
Wrote magic at 6720 - bd30
Wrote namespace list at bd30 - bd40
***
/var/lib/dpkg/info/gpar2.postrm: line 25: update-desktop-database: command not found
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
***
* Updating MIME database in /usr/share/mime...
Wrote 480 strings at 20 - 27dc
Wrote aliases at 27dc - 2990
Wrote parents at 2990 - 3340
Wrote literal globs at 3340 - 339c
Wrote suffix globs at 339c - 66f4
Wrote full globs at 66f4 - 6720
Wrote magic at 6720 - bd30
Wrote namespace list at bd30 - bd40
***
/var/lib/dpkg/tmp.ci/postrm: line 25: update-desktop-database: command not found
dpkg: error processing temp/gpar2_0.3-1_i386.deb (--install):
 subprocess new post-removal script returned error exit status 127
***
* Updating MIME database in /usr/share/mime...
Wrote 480 strings at 20 - 27dc
Wrote aliases at 27dc - 2990
Wrote parents at 2990 - 3340
Wrote literal globs at 3340 - 339c
Wrote suffix globs at 339c - 66f4
Wrote full globs at 66f4 - 6720
Wrote magic at 6720 - bd30
Wrote namespace list at bd30 - bd40
***
/var/lib/dpkg/tmp.ci/postrm: line 25: update-desktop-database: command not found
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 temp/gpar2_0.3-1_i386.deb

```

Trying to install the package that contains update-desktop-database gives

```
kopec@kopec-laptop:~$ sudo apt-get install desktop-file-utils
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package gpar2 needs to be reinstalled, but I can't find an archive for it.

```

---

### Post by taurus on 2007-01-25
Try something like

```
sudo dpkg -r gpar2
```

---

### Post by Drooling_Sheep on 2007-01-25
```
kopec@kopec-laptop:~$ sudo dpkg -r gpar2
Password:
dpkg: error processing gpar2 (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 gpar2

```

Reinstalling doesn't work as I mentioned above.

---

### Post by Billquinn1 on 2007-01-25
First look in /var/lib/dpkg/status and remove all gpar2 entries

Then do   dpkg --purge gpar2

That should get rid of it. I'm not sure about getting it installed.

---

### Post by Drooling_Sheep on 2007-01-25
Thanks, that allows me to install other software.  I'm not too worried about getting it installed.

---

