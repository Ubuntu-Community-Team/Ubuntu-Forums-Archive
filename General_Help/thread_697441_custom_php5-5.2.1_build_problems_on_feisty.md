---
title: "custom php5-5.2.1 build problems on feisty"
date: 2008-02-15
forum: General Help
---

### Post by darthraider on 2008-02-15
I've been trying to get a customized php5 apache module getting built on my ubuntu server.
I want --enable-debug instead of --disable-debug in my php5 module.

When doing 'fakeroot debian/rules binary' (after editing debian/rules ofc) I get the following error:

> 
dh_builddeb -s
warning, `debian/php5-common/DEBIAN/control' contains user-defined field `Original-Maintainer'
dpkg-deb: building package `php5-common' in `../php5-common_5.2.1-0ubuntu1.5_amd64.deb'.
dpkg-deb: maintainer script `postrm' has bad permissions 664 (must be >=0555 and <=0775)
dh_builddeb: command returned error code 512
make: *** [binary-arch] Error 1


Now, i do understand this message, yet do not know how to fix it, and after spending some time on Google I seem to be the only one running into this problem with php5 (or no one has ever tried doing this :p)

Is there an easy way to fix this (seemingly) minor problem?

---

### Post by danwood76 on 2008-02-15
How are you building the PHP5 module?
Are you folowing a guide?

---

### Post by darthraider on 2008-02-15
> **danwood76 said:**
> How are you building the PHP5 module?
Are you folowing a guide?

I've looked at this page which describes a very basic way of compiling and building a package with extra 
compile options.
[http://www.cyberciti.biz/faq/rebuilding-ubuntu-debian-linux-binary-package/](http://www.cyberciti.biz/faq/rebuilding-ubuntu-debian-linux-binary-package/)

What i've basicly done is
apt-get build-dep php5
apt-get source php5
changed --disable-debug to --enable-debug in ~/debian/rules
fakeroot debian/rules binary
...and then it bails out on me with that 'bad permissions error' on postrm.

---

### Post by darthraider on 2008-02-18
No one ran into a similar problem?

---

