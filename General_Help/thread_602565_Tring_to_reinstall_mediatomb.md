---
title: "Tring to reinstall mediatomb"
date: 2007-11-04
forum: General Help
---

### Post by takeawaydave on 2007-11-04
I installed mediatomb from deb package as per instructions on mediatomb home site.

I then removed it and now I am trying to reinstall as per the same initial methid but get the following:

```
root@denali:/etc/init.d# apt-get install mediatomb
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libexif12 libid3-3.8.3c2a libmozjs0d libnspr4-0d
The following NEW packages will be installed
  libexif12 libid3-3.8.3c2a libmozjs0d libnspr4-0d mediatomb
0 upgraded, 5 newly installed, 0 to remove and 28 not upgraded.
Need to get 0B/1401kB of archives.
After unpacking 3903kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package libexif12.
(Reading database ... 25250 files and directories currently installed.)
Unpacking libexif12 (from .../libexif12_0.6.13-5ubuntu0.2_i386.deb) ...
Selecting previously deselected package libid3-3.8.3c2a.
Unpacking libid3-3.8.3c2a (from .../libid3-3.8.3c2a_3.8.3-6build1_i386.deb) ...
Selecting previously deselected package libnspr4-0d.
Unpacking libnspr4-0d (from .../libnspr4-0d_1.8.0.10-3ubuntu1_i386.deb) ...
Selecting previously deselected package libmozjs0d.
Unpacking libmozjs0d (from .../libmozjs0d_1.8.0.10-3ubuntu1_i386.deb) ...
Selecting previously deselected package mediatomb.
Unpacking mediatomb (from .../mediatomb_0.10.0-1feisty1_i386.deb) ...
Setting up libexif12 (0.6.13-5ubuntu0.2) ...

Setting up libid3-3.8.3c2a (3.8.3-6build1) ...
Setting up libnspr4-0d (1.8.0.10-3ubuntu1) ...

Setting up libmozjs0d (1.8.0.10-3ubuntu1) ...

Setting up mediatomb (0.10.0-1feisty1) ...
chown: cannot access `/etc/mediatomb/config.xml': No such file or directory
dpkg: error processing mediatomb (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mediatomb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I have runthen ran:

```
apt-get remove mediatomb 

```

followed by

```
apt-get autoclean

```
but I get the same error and the package will not install.

Please help me someone.

---

### Post by takeawaydave on 2007-11-04
ok following fixed it

```
apt-get -f install mediatomb
```

---

### Post by Maestro23 on 2007-11-04
> **takeawaydave said:**
> ok following fixed it

```
apt-get -f install mediatomb
```

Glad you got it fixed.  Please mark this SOLVED using the Thread Tools.

Thanks.:)

---

