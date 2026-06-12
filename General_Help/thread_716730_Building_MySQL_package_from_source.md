---
title: "Building MySQL package from source"
date: 2008-03-06
forum: General Help
---

### Post by eriklee on 2008-03-06
I'm trying to install the sphinx full text search engine with the sphinx_se plug-in for mysql, and I keep running into seemingly silly problems.  Here's the list of things I've tried:

Info:
Linux www 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64 GNU/Linux

The following fails saying that Makefile.in and a couple of other files in the debian directory are missing:
```
apt-get source mysql-server-5.0
<apply sphinx patches>
dpkg-buildpackage -b
```

This fails in the same way as above:
```
apt-build source mysql-server-5.0
<change to /var/cache/apt-build/build/mysql... and apply patches>
dpkg-buildpackage -b
```

Same story if I use 
```
 fakeroot debian/rules binary 
```
to build it.

So I downloaded the source distribution (5.0.51a) from mysql site and attempted to build a deb package from there:

Using all the same techniques from above, I end up with unexpanded text in the final stage of package creation that bombs out saying:
```

dpkg-gencontrol: error: source package name `@MYSQL_BRANDED_BASE_VERSION@' contains illegal character `@'
```
I'm not an autotools expert, but it seems like these files need to be processed into workable versions as a step before being usable by the rules makefile.

Does anyone have some advice about how to *successfully* build a package from mysql-server-5.0 from source?  I have built several other packages from source following these steps, but I'm missing something with mysql...

As a footnote, I tested all of the above with unmodified sources as well (i.e., I didn't apply the sphinx patches and ended up with the same results, so it appears that it isn't sphinx's fault).

Thanks!
Erik

---

### Post by tmth on 2008-05-31
After 5 hours of struggling i figured it out: guys over at mysql made a few mistakes in variable declarations so the sed script that is in debian/rules replaces the placeholders with wrong stuff.

You will have to edit your rules files by replacing all instances of the empty variables with correct data.  Just do a replace command in text editor (replace my version numbers with yours):

$(MYSQL_BASE_VERSION)  to  5.0
$(MYSQL_BRANDED_BASE_VERSION) to 5.0
$(MYSQL_PREVIOUS_BASE_VERSION) to 4.1
$(MYSQL_BRANDED_PREVIOUS_BASE_VERSION) to 4.1
$(MYSQL_SOURCE_BASE_VERSION) to
$(SHARED_LIB_MAJOR_VERSION) to 15
$(NDB_SHARED_LIB_MAJOR_VERSION) to 2

Although i still can't figure out how to get the version numbers in sink with ubuntu standards

---

