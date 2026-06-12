---
title: "What package"
date: 2004-12-09
forum: General Help
---

### Post by oddabe19 on 2004-12-09
What package will fix this error
```
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for GTK+ - version >= 2.0.3... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.

Cannot find GTK! Not building GTK FrontEnd.

checking for perl... /usr/bin/perl
checking for Perl compile flags... ok

```

I was building a package, and I got that error, it makes no sense to me, since i thought I had GTK installed and apt-cache search showed a million packages that have GTK+ in it, and gtk-dev i cant find...

any help?

---

### Post by randy on 2004-12-09
The gtk+ dev package will fix that error.

---

### Post by WW on 2004-12-09
Try installing **libgtk2.0-dev** (but that's just a guess).

---

