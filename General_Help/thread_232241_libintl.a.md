---
title: "libintl.a"
date: 2006-08-08
forum: General Help
---

### Post by kernco on 2006-08-08
I'm trying to build something that links to this, but I don't seem to have this file.  Everything online says that it is part of the gettext library.  I have used apt-get to verify that I have the most recent gettext package installed, but still no libintl.a.  Any ideas?

Thanks,
Colin

---

### Post by Rui Pais on 2006-08-08
Hi,
according to [Ubuntu Package Contents Search]("http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=libintl.a&searchmode=searchword&case=insensitive&version=dapper&arch=i386") libintl.a belongs to [libdevel/libuclibc-dev]("http://packages.ubuntu.com/dapper/libdevel/libuclibc-dev").

Hope that helps

---

### Post by sulemankm on 2007-07-11
Hi, the libintl.a in libuclib-dev package did not solve the problem for me.

I'm trying to use the CxxTest framework with eclipse.  When I compile/link the application, the linker gives the message 'cannot find -lintl'.  I installed the libuClib-dev package. It compiled and linked correctly but did not execute correctly and terminated unexpectedly.

To my understanding the libuclib-dev package is for embedded development not for desktop ubuntu linux (i'm using fiesty).  So there has to be a gettext-dev package which contains these file.  As of my knowledge I don't find this package in the repo (including universe).

---

### Post by kernco on 2007-07-12
Yes,  I was also having this problem using the CxxTest Eclipse plugin.  I contacted the developers, and they said it was a known bug that occurred because they needed to update the plugin for Eclipse 3.2.  They said they were releasing an update within a week (this was almost a year ago, mind you).  I never saw the update, but I stopped checking after a few weeks.

---

### Post by sulemankm on 2007-07-12
But the strange thing is, why the Ubuntu people don't have the libintl.a in any of the regular packages in any of their repositories.

---

### Post by Rui Pais on 2007-07-12
> **sulemankm said:**
> But the strange thing is, why the Ubuntu people don't have the libintl.a in any of the regular packages in any of their repositories.

libintl.a is on the package that you installed, so you could compile with errors. 
If it fails at execution that seems to indicate other problem, probably the ones kernco refer and that eclipse developers seems to be ware (but apparently not interested...) 

About gettext-dev. There was one a libgettext-dev (or something like) but now gettext package should install all need. There are some extra dev files related, but seems that they are ruby specifics.

---

