---
title: "'Locate' gives better result then 'find'"
date: 2017-01-21
forum: General Help
---

### Post by peter1897 on 2017-01-21
I was searching for 'intltool' and 'locate' provided 36 results and 'find' 25:

```
osboxes@osboxes:~$ locate intltool
/home/osboxes/Downloads/xfdashboard-0.6.1/intltool-extract.in
/home/osboxes/Downloads/xfdashboard-0.6.1/intltool-merge.in
/home/osboxes/Downloads/xfdashboard-0.6.1/intltool-update.in
/usr/bin/intltool-extract
/usr/bin/intltool-merge
/usr/bin/intltool-prepare
/usr/bin/intltool-update
/usr/bin/intltoolize
/usr/share/intltool
/usr/share/intltool-debian
/usr/share/aclocal/intltool.m4
/usr/share/doc/intltool
/usr/share/doc/intltool-debian
/usr/share/doc/intltool/AUTHORS
/usr/share/doc/intltool/NEWS.gz
/usr/share/doc/intltool/README.gz
/usr/share/doc/intltool/TODO
/usr/share/doc/intltool/changelog.Debian.gz
/usr/share/doc/intltool/copyright
/usr/share/doc/intltool-debian/AUTHORS
/usr/share/doc/intltool-debian/README.Debian
/usr/share/doc/intltool-debian/changelog.gz
/usr/share/doc/intltool-debian/copyright
/usr/share/intltool/Makefile.in.in
/usr/share/intltool-debian/intltool-extract
/usr/share/intltool-debian/intltool-merge
/usr/share/intltool-debian/intltool-update
/usr/share/man/man8/intltool-extract.8.gz
/usr/share/man/man8/intltool-merge.8.gz
/usr/share/man/man8/intltool-prepare.8.gz
/usr/share/man/man8/intltool-update.8.gz
/usr/share/man/man8/intltoolize.8.gz
/var/lib/dpkg/info/intltool-debian.list
/var/lib/dpkg/info/intltool-debian.md5sums
/var/lib/dpkg/info/intltool.list
/var/lib/dpkg/info/intltool.md5sums
osboxes@osboxes:~$ locate intltool -c
36
```


```
osboxes@osboxes:~$ sudo find / -name *intltool*
/usr/bin/intltool-update
/usr/bin/intltool-merge
/usr/bin/intltool-extract
/usr/bin/intltoolize
/usr/bin/intltool-prepare
/usr/share/aclocal/intltool.m4
/usr/share/doc/intltool-debian
/usr/share/doc/intltool
/usr/share/man/man8/intltool-extract.8.gz
/usr/share/man/man8/intltool-update.8.gz
/usr/share/man/man8/intltool-merge.8.gz
/usr/share/man/man8/intltool-prepare.8.gz
/usr/share/man/man8/intltoolize.8.gz
/usr/share/intltool-debian
/usr/share/intltool-debian/intltool-update
/usr/share/intltool-debian/intltool-merge
/usr/share/intltool-debian/intltool-extract
/usr/share/intltool
/var/lib/dpkg/info/intltool.list
/var/lib/dpkg/info/intltool-debian.md5sums
/var/lib/dpkg/info/intltool.md5sums
/var/lib/dpkg/info/intltool-debian.list
/home/osboxes/Downloads/xfdashboard-0.6.1/intltool-merge.in
/home/osboxes/Downloads/xfdashboard-0.6.1/intltool-update.in
/home/osboxes/Downloads/xfdashboard-0.6.1/intltool-extract.in
osboxes@osboxes:~$ sudo find / -name *intltool* | wc -l
25
```


Why 'find' finds less results than 'locate'?

---

### Post by steeldriver on 2017-01-21
locate is including files whose paths match the keyword

A fairer comparison would be

```

sudo find / **-path** '*intltool*' 2>/dev/null

```

ASIDE: always quote wildcard arguments to `find`, to stop the shell from trying to match them to filenames in the current dir

ASIDE 2: locate can give false positives (files that have been removed since the last updatedb was run); you can add -e to make sure the reported files exist at the time of running

---

### Post by peter1897 on 2017-01-21
Thanks, that explains the different output.

---

